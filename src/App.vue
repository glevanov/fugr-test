<template>
  <div class="container">
    <h1 class="heading">Users</h1>
    <table class="users">
      <tr class="users__headings">
        <th class="users__heading" @click="sortUsers('id')">id</th>
        <th class="users__heading" @click="sortUsers('firstName')">firstName</th>
        <th class="users__heading" @click="sortUsers('lastName')">lastName</th>
        <th class="users__heading" @click="sortUsers('email')">email</th>
        <th class="users__heading" @click="sortUsers('phone')">phone</th>
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
      url: 'http://www.filltext.com/?rows=32&id={number|1000}&firstName={firstName}&lastName={lastName}&email={email}&phone={phone|(xxx)xxx-xx-xx}&address={addressObject}&description={lorem|32}',
      sortedByDescending: {
        id: false,
        firstName: false,
        lastName: false,
        email: false,
        phone: false
      }
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
      sortUsers(key) {
        const resetSortedStatus = () => {
          for (const key of Object.keys(this.sortedByDescending)) {
            this.sortedByDescending[key] = false;
          }
        }

        if (!this.sortedByDescending[key]) {
          this.usersList.sort((a, b) => (a[key] < b[key]) ? -1 : 1);
          resetSortedStatus()
          this.sortedByDescending[key] = true;
        } else {
          this.usersList.sort((a, b) => (a[key] < b[key]) ? 1 : -1);
          resetSortedStatus()
        }
      },
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

<style></style>
