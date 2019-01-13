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
    methods: {
      nextPage () {
        this.pageNumber++
      },
      prevPage () {
        this.pageNumber--
      }
    },
    computed: {
      pageCount () {
        const length = this.small.length
        const size = this.maxPages
        return Math.ceil(length / size)
      },
      paginatedData () {
        const start = this.pageNumber * this.maxPages
        const end = start + this.maxPages
        return this.small.slice(start, end)
      }
    },
    data: () => ({
      pageNumber: 0,
      maxPages: 10,
      small: [{
        'id': 870,
        'firstName': 'Linda',
        'lastName': 'Spataro',
        'email': 'AFlege@convallis.org',
        'phone': '(556)467-4715',
        'address': {'streetAddress': '1933 Libero St', 'city': 'Arcadia', 'state': 'NJ', 'zip': '77108'},
        'description': 'pretium lacus at amet lacus in donec elementum sed egestas lacus et aliquam quis sit odio aliquam libero sed donec eros sagittis elementum amet malesuada mi curabitur tincidunt hendrerit ac mi porta'
      }, {
        'id': 942,
        'firstName': 'Noriess',
        'lastName': 'Franklin',
        'email': 'LStalinski@amet.com',
        'phone': '(446)007-3989',
        'address': {'streetAddress': '4907 Sed Dr', 'city': 'Harrisburg', 'state': 'WI', 'zip': '76373'},
        'description': 'tortor sapien morbi adipiscing lacus donec tincidunt sit dui dui sed sed egestas eget risus lacus hendrerit quis sit turpis ac facilisis nunc nullam lacus libero tellus tortor adipiscing mattis id adipiscing'
      }, {
        'id': 672,
        'firstName': 'Vaibhavi',
        'lastName': 'Marton',
        'email': 'CStrange@ac.net',
        'phone': '(408)992-0048',
        'address': {'streetAddress': '196 Sit Ln', 'city': 'Rancho Cucamonga', 'state': 'VA', 'zip': '46353'},
        'description': 'odio tincidunt odio sed hendrerit tortor convallis mattis ac pulvinar ac et lacus convallis adipiscing elit convallis turpis dolor mattis vestibulum convallis etiam magna egestas sit sit malesuada dolor odio at dolor'
      }, {
        'id': 155,
        'firstName': 'Brien',
        'lastName': 'Reeder',
        'email': 'TSmyth@neque.io',
        'phone': '(165)650-0283',
        'address': {'streetAddress': '5524 Mattis Rd', 'city': 'St Augustine', 'state': 'NC', 'zip': '96881'},
        'description': 'amet ipsum sed egestas ac vitae odio pulvinar eros dolor aliquam at donec elementum dolor fringilla sollicitudin porta nullam aliquam lectus dolor quis morbi aenean lacus magna molestie nec pulvinar turpis amet'
      }, {
        'id': 818,
        'firstName': 'Janelle',
        'lastName': 'Bert',
        'email': 'JDobbins@hendrerit.ly',
        'phone': '(884)292-2732',
        'address': {'streetAddress': '3486 Placerat Dr', 'city': 'Sterling', 'state': 'MA', 'zip': '28083'},
        'description': 'libero tortor molestie adipiscing facilisis sed tellus risus et tellus lectus porta facilisis sit eget lacus curabitur magna pulvinar mattis odio magna et sagittis lorem consequat pretium pretium tincidunt dolor lacus sed'
      }, {
        'id': 250,
        'firstName': 'Rossana',
        'lastName': 'Knost',
        'email': 'ASchramm@sit.io',
        'phone': '(735)212-1685',
        'address': {'streetAddress': '3700 Magna Dr', 'city': 'Ft Lauderdale', 'state': 'AL', 'zip': '20391'},
        'description': 'convallis vestibulum aliquam dolor elementum sed dolor amet nunc sit mattis mi mi vitae rutrum sollicitudin tortor tortor sed augue vestibulum lectus libero nec rutrum molestie nunc risus sagittis morbi tincidunt vestibulum'
      }, {
        'id': 907,
        'firstName': 'Calvin',
        'lastName': 'Heitzman',
        'email': 'CPolovich@eget.gov',
        'phone': '(525)506-8481',
        'address': {'streetAddress': '9616 Pharetra Ln', 'city': 'Spokane', 'state': 'CO', 'zip': '89928'},
        'description': 'rutrum vitae porta sapien porta vel massa et sit non placerat sollicitudin ante consequat libero dui mattis egestas sit magna vel tincidunt pretium consequat neque tortor sollicitudin in elit dui at scelerisque'
      }, {
        'id': 936,
        'firstName': 'Joseph',
        'lastName': 'Ahn',
        'email': 'CPowers@lacus.net',
        'phone': '(666)559-7772',
        'address': {'streetAddress': '890 Sollicitudin Ct', 'city': 'Pacoima', 'state': 'WY', 'zip': '50013'},
        'description': 'at libero magna sollicitudin amet elementum sit suspendisse morbi tortor placerat aenean tortor nunc lectus vitae magna tempor pulvinar etiam fringilla sit curabitur tempor tincidunt sagittis nec sit sapien ac in neque'
      }, {
        'id': 748,
        'firstName': 'Jess',
        'lastName': 'Sherwood',
        'email': 'BLawson@eros.ly',
        'phone': '(560)718-3928',
        'address': {'streetAddress': '4421 Amet St', 'city': 'Stoneham', 'state': 'ID', 'zip': '93326'},
        'description': 'sed et odio quis neque convallis amet velit scelerisque amet convallis mi magna pretium ipsum egestas augue amet rutrum sed dolor et mi placerat sapien mi vestibulum suspendisse vitae aenean consequat donec'
      }, {
        'id': 86,
        'firstName': 'Fredric',
        'lastName': 'Atheya',
        'email': 'ARussell@pulvinar.org',
        'phone': '(524)790-5630',
        'address': {'streetAddress': '5053 Ac St', 'city': 'Pasco', 'state': 'VT', 'zip': '26079'},
        'description': 'tempor sollicitudin mattis et porttitor dui lacus lectus orci pretium elit pulvinar at placerat magna eget libero malesuada velit orci porttitor rutrum sit placerat sapien aliquam tincidunt in lacus amet id mattis'
      }, {
        'id': 24,
        'firstName': 'Zenaida',
        'lastName': 'Cavalier',
        'email': 'KMahan@etiam.net',
        'phone': '(374)701-9431',
        'address': {'streetAddress': '812 Sapien Dr', 'city': 'Carolina Beach', 'state': 'CA', 'zip': '94563'},
        'description': 'at lacus convallis sed sagittis nullam lorem etiam magna sollicitudin ante tortor donec tellus ac porttitor elit non sed dolor ipsum ipsum sollicitudin vitae magna augue in sed aenean vestibulum mattis libero'
      }, {
        'id': 6,
        'firstName': 'Rocelyn',
        'lastName': 'Nesbitt',
        'email': 'NHutchings@dolor.ly',
        'phone': '(239)426-0694',
        'address': {'streetAddress': '6888 Scelerisque Ave', 'city': 'Atlanta', 'state': 'DC', 'zip': '43677'},
        'description': 'pulvinar dui aliquam tempor sed eget tellus vitae tortor sed placerat at mattis tincidunt eros at consequat et nec et etiam eget placerat pulvinar lacus aliquam eros quis hendrerit hendrerit sed id'
      }, {
        'id': 705,
        'firstName': 'Darrell',
        'lastName': 'Diaz',
        'email': 'YFavus@fringilla.org',
        'phone': '(671)762-5547',
        'address': {'streetAddress': '5635 In Rd', 'city': 'Fort Collins', 'state': 'HI', 'zip': '25386'},
        'description': 'sollicitudin aenean pulvinar fringilla aenean vitae et et sapien vel pharetra dui tellus dolor aenean consectetur sit ipsum porttitor donec massa vitae ipsum tortor ipsum neque tortor id tellus sit molestie sapien'
      }, {
        'id': 487,
        'firstName': 'Nicole',
        'lastName': 'Lenz',
        'email': 'AEaton@vitae.gov',
        'phone': '(880)476-1681',
        'address': {'streetAddress': '1045 Sed Rd', 'city': 'Villa Rica', 'state': 'IA', 'zip': '81306'},
        'description': 'dolor placerat dolor sed elit dui magna egestas dolor convallis sed vitae orci amet eget facilisis eros tortor nec eros hendrerit consequat egestas sit aliquam placerat vestibulum hendrerit scelerisque at scelerisque eget'
      }, {
        'id': 513,
        'firstName': 'Corazon',
        'lastName': 'Aviles',
        'email': 'MEkekwe@sed.com',
        'phone': '(489)522-5728',
        'address': {'streetAddress': '8748 Dolor Ln', 'city': 'Armada', 'state': 'WV', 'zip': '55678'},
        'description': 'magna nullam aenean adipiscing at risus sed tortor at pharetra eros vitae velit ac eros tellus etiam lacus sit vitae aenean malesuada magna sit porta tortor placerat amet sit eros magna mattis'
      }, {
        'id': 738,
        'firstName': 'Tracey',
        'lastName': 'Phuan',
        'email': 'LOlson@nunc.io',
        'phone': '(766)127-7563',
        'address': {'streetAddress': '4692 Rutrum Rd', 'city': 'Kingsland', 'state': 'MD', 'zip': '41359'},
        'description': 'nunc morbi donec elit mattis amet tellus sapien odio molestie etiam etiam vitae aenean id amet pulvinar libero sed mi pulvinar malesuada sit magna sit sapien vitae porta amet magna sed etiam'
      }, {
        'id': 827,
        'firstName': 'Paul',
        'lastName': 'Tippit',
        'email': 'SLawson@magna.net',
        'phone': '(510)154-4239',
        'address': {'streetAddress': '1310 Mattis Rd', 'city': 'Orlando', 'state': 'SC', 'zip': '26236'},
        'description': 'et odio consectetur dolor vitae donec odio convallis scelerisque placerat fringilla nunc et tincidunt molestie dui elementum porttitor elit pulvinar pulvinar tortor elit libero sit dolor dolor at lacus sollicitudin odio dolor'
      }, {
        'id': 587,
        'firstName': 'Veena',
        'lastName': 'Westrate',
        'email': 'JMontemer@magna.ly',
        'phone': '(176)598-0087',
        'address': {'streetAddress': '8239 Adipiscing St', 'city': 'Florissant', 'state': 'LA', 'zip': '17659'},
        'description': 'dui vitae ipsum aliquam eros tortor odio tempor nec dolor nec convallis nec nec massa dolor elit rutrum odio suspendisse massa pretium hendrerit mi amet tortor sit at sed lectus massa id'
      }, {
        'id': 760,
        'firstName': 'Vaibhavi',
        'lastName': 'Eckhart',
        'email': 'NBrabant@malesuada.io',
        'phone': '(858)606-3646',
        'address': {'streetAddress': '7236 Dolor Ct', 'city': 'Durham', 'state': 'TX', 'zip': '52858'},
        'description': 'sed lorem sed dolor odio amet ac at non lacus vitae amet at consequat tincidunt malesuada egestas sed vitae egestas turpis nullam dui vitae eget lacus tortor tempor nunc vitae libero consequat'
      }, {
        'id': 362,
        'firstName': 'Imelda',
        'lastName': 'Hunt',
        'email': 'RGuth@massa.org',
        'phone': '(221)979-7665',
        'address': {'streetAddress': '7591 Nunc Dr', 'city': 'Whitehouse', 'state': 'SD', 'zip': '78610'},
        'description': 'placerat sed et lectus magna aliquam consequat sollicitudin morbi orci at sollicitudin magna aliquam massa hendrerit magna hendrerit neque dui morbi sed id ipsum aliquam tortor sed non tincidunt massa sit fringilla'
      }, {
        'id': 917,
        'firstName': 'Blake',
        'lastName': 'Loehfelm',
        'email': 'DYuan@convallis.io',
        'phone': '(847)038-6060',
        'address': {'streetAddress': '2964 Vel Ln', 'city': 'Brownsville', 'state': 'VT', 'zip': '87244'},
        'description': 'pulvinar mattis nec malesuada sit dolor eros non lacus amet aliquam adipiscing sapien dolor vitae massa sed hendrerit aenean turpis aliquam sollicitudin facilisis magna rutrum porttitor vestibulum sit nunc tortor mattis ac'
      }, {
        'id': 43,
        'firstName': 'Bola',
        'lastName': 'Tippetts',
        'email': 'CLarson@magna.ly',
        'phone': '(906)099-5736',
        'address': {'streetAddress': '538 Tortor St', 'city': 'Camden', 'state': 'HI', 'zip': '83103'},
        'description': 'nec curabitur pretium placerat tortor amet porta tortor ipsum placerat aenean porttitor dolor turpis ac vel sit in velit ipsum magna morbi suspendisse tincidunt aliquam sed at id mi dui pulvinar amet'
      }, {
        'id': 239,
        'firstName': 'Amber',
        'lastName': 'Caruso',
        'email': 'VThomad@dui.gov',
        'phone': '(295)054-3327',
        'address': {'streetAddress': '9355 Magna Ln', 'city': 'Alexandria', 'state': 'WI', 'zip': '26412'},
        'description': 'non sed sed et tortor lectus elementum magna morbi libero lacus lectus velit et elit sed mattis vitae nec neque mattis orci facilisis fringilla ac orci amet porttitor pulvinar augue vestibulum consequat'
      }, {
        'id': 104,
        'firstName': 'Alek',
        'lastName': 'Tadeu',
        'email': 'HBodine@magna.gov',
        'phone': '(190)033-7608',
        'address': {'streetAddress': '6056 Morbi Rd', 'city': 'Prince George', 'state': 'SC', 'zip': '35487'},
        'description': 'amet lorem at elit porta massa ante amet pulvinar elementum consequat tortor consectetur pulvinar massa tincidunt at lacus convallis ante fringilla sollicitudin scelerisque eros elementum nec dolor adipiscing sed pulvinar lacus tincidunt'
      }, {
        'id': 861,
        'firstName': 'Napoleon',
        'lastName': 'Brazell',
        'email': 'ARehrig@pretium.ly',
        'phone': '(989)828-1168',
        'address': {'streetAddress': '1744 Vel Dr', 'city': 'Modesto', 'state': 'AR', 'zip': '74852'},
        'description': 'nec malesuada vel hendrerit sit et sagittis tincidunt vestibulum quis et elit elementum fringilla tortor massa sit ac sed odio vitae sit molestie sed at ante mattis id amet morbi libero id'
      }, {
        'id': 66,
        'firstName': 'Kola',
        'lastName': 'Saver',
        'email': 'JGlover@aenean.io',
        'phone': '(895)518-3743',
        'address': {'streetAddress': '815 Ac Rd', 'city': 'Grand Rapids', 'state': 'DC', 'zip': '16982'},
        'description': 'aliquam libero tortor nec mi ipsum donec magna turpis elementum magna sed sollicitudin aliquam lacus curabitur porttitor velit odio orci velit neque in nec dolor tincidunt pulvinar nec amet lorem tincidunt ipsum'
      }, {
        'id': 422,
        'firstName': 'Josephine',
        'lastName': 'Gilby',
        'email': 'NSluka@neque.gov',
        'phone': '(701)944-4688',
        'address': {'streetAddress': '1098 Tortor Ct', 'city': 'Hobbs', 'state': 'ID', 'zip': '15944'},
        'description': 'consequat vestibulum convallis massa eget pulvinar porta sit amet at risus sollicitudin mi malesuada fringilla molestie libero turpis molestie ante rutrum orci elit aenean in pulvinar sagittis sit vestibulum sed augue ante'
      }, {
        'id': 279,
        'firstName': 'Wei',
        'lastName': 'Flanigan',
        'email': 'BGould@mi.gov',
        'phone': '(135)485-7968',
        'address': {'streetAddress': '7552 Dolor St', 'city': 'Aurora', 'state': 'CO', 'zip': '45301'},
        'description': 'vitae nullam sapien curabitur tincidunt sollicitudin amet elementum ac mattis sagittis odio amet lacus et magna odio pulvinar mattis libero sit sapien magna donec vel aliquam molestie tortor suspendisse consequat convallis libero'
      }, {
        'id': 680,
        'firstName': 'Bill',
        'lastName': 'Wantland',
        'email': 'MMcmullin@nec.com',
        'phone': '(844)756-4925',
        'address': {'streetAddress': '2569 Pretium St', 'city': 'Baltimore', 'state': 'AR', 'zip': '85560'},
        'description': 'facilisis facilisis massa tortor dolor sed lacus dolor mattis vestibulum non tellus id lacus sit adipiscing orci sed sed vestibulum sed sollicitudin elit et ac ac placerat magna quis vitae egestas tortor'
      }, {
        'id': 84,
        'firstName': 'Andrew',
        'lastName': 'Braswell',
        'email': 'DBuxton@ac.com',
        'phone': '(927)384-9115',
        'address': {'streetAddress': '8334 Suspendisse Rd', 'city': 'Maricopa', 'state': 'HI', 'zip': '22957'},
        'description': 'vel vel suspendisse odio sit aliquam et lectus at donec amet sit velit tincidunt magna orci mattis risus et facilisis convallis magna et vestibulum tellus risus sagittis aliquam sagittis sollicitudin sed massa'
      }, {
        'id': 712,
        'firstName': 'Henry',
        'lastName': 'Cheng',
        'email': 'XWillett@mattis.net',
        'phone': '(210)254-4873',
        'address': {'streetAddress': '3118 Molestie Ln', 'city': 'Lindale', 'state': 'WA', 'zip': '36259'},
        'description': 'sollicitudin nullam aliquam adipiscing placerat amet adipiscing amet amet sed placerat lacus massa velit consequat vitae augue sagittis orci lacus ipsum pulvinar ac vestibulum amet ipsum fringilla tincidunt mi aenean aliquam dolor'
      }, {
        'id': 768,
        'firstName': 'Colleen',
        'lastName': 'Kailin',
        'email': 'AHist@malesuada.org',
        'phone': '(861)633-7645',
        'address': {'streetAddress': '5633 At Ct', 'city': 'Midlothian', 'state': 'SD', 'zip': '99133'},
        'description': 'tellus lacus neque aenean tincidunt mi lacus id pretium nec malesuada egestas sed pharetra dolor hendrerit consequat id mi vestibulum pulvinar et nec consectetur sed pulvinar et consequat egestas sit eget tincidunt'
      }]
    })
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
