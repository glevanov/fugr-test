<template>
  <div class="container">
    <h1 class="heading">Users</h1>
    <table class="users">
      <tr class="users__headings">
        <th class="users__heading">id</th>
        <th class="users__heading">firstName</th>
        <th class="users__heading">lastName</th>
        <th class="users__heading">email</th>
        <th class="users__heading">phone</th>
      </tr>
      <tr
        class="users__row"
        v-for="item in paginatedData">
        <td class="users__cell">{{ item.id }}</td>
        <td class="users__cell">{{ item.firstName }}</td>
        <td class="users__cell">{{ item.lastName }}</td>
        <td class="users__cell">{{ item.email }}</td>
        <td class="users__cell">{{ item.phone }}</td>
      </tr>
    </table>
    <div class="pagination">
      <button class="pagination__button pagination__button--previous"
              @click="prevPage"
              :disabled="pageNumber===0"
      >Previous
      </button>
      <p class="pagination__counter">Page {{ pageNumber + 1 }} out of {{ pageCount }}</p>
      <button class="pagination__button pagination__button--next"
              @click="nextPage"
              :disabled="pageNumber >= pageCount - 1"
      >Next
      </button>
    </div>
  </div>
</template>

<script>
  export default {
    data: () => ({
      pageNumber: 0,
      maxPages: 10,
      usersList: [],
      url: 'http://www.filltext.com/?rows=32&id={number|1000}&firstName={firstName}&lastName={lastName}&email={email}&phone={phone|(xxx)xxx-xx-xx}&address={addressObject}&description={lorem|32}'
    }),
    computed: {
      pageCount () {
        const length = this.usersList.length
        const size = this.maxPages
        return Math.ceil(length / size)
      },
      paginatedData () {
        const start = this.pageNumber * this.maxPages
        const end = start + this.maxPages
        return this.usersList.slice(start, end)
      }
    },
    methods: {
      getList () {
        const xhr = new XMLHttpRequest();
        xhr.open('GET', this.url, false);
        xhr.send();
        if (xhr.status !== 200) {
          console.log(`${xhr.status}: ${xhr.statusText}`)
        } else {
          this.usersList = JSON.parse(xhr.response);
        }
      },
      nextPage () {
        this.pageNumber++
      },
      prevPage () {
        this.pageNumber--
      }
    },
    created () {
      this.getList();
    }
  }
</script>

<style scoped>
  .container {
    background-color: #ffffff;
    box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.1);
    border: 1px solid rgba(0, 0, 0, 0.5);
    border-radius: 6px;
    display: inline-block;
    margin: 20px;
    padding: 20px;
    text-align: left;
  }

  .heading {
    color: #0260ee;
    margin: 0;
    margin-top: 10px;
    margin-bottom: 10px;
    margin-left: 9px;
  }

  .users {
    background-color: #ffffff;
    border-collapse: collapse;
  }

  .users__headings {
    font-size: 24px;
    line-height: normal;
  }

  .users__row {
    font-size: 18px;
    line-height: normal;
  }

  .users__heading {
    padding: 10px;
    text-align: left;
  }

  .users__cell {
    padding: 10px;
    border-top: 1px solid rgba(0, 0, 0, 0.5);
  }

  .pagination {
    align-items: center;
    display: flex;
    margin-top: 10px;
    margin-bottom: 10px;
  }

  .pagination__button {
    background-color: #0260ee;
    border: 0;
    border-radius: 5px;
    color: #ffffff;
    letter-spacing: 1px;
    padding: 10px;
    text-transform: uppercase;
  }

  .pagination__button:disabled {
    background-color: rgba(0, 0, 0, 0.5);
  }

  .pagination__counter {
    margin: 0;
    margin-right: 10px;
    margin-left: 10px;
  }
</style>
