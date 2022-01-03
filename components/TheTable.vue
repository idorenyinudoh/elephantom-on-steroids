<template>
  <table>
    <caption>
      All Elephants
    </caption>
    <thead>
      <tr>
        <th>S/N</th>
        <th>Name</th>
        <th>Species</th>
        <th>Sex</th>
        <th>Affiliation</th>
        <th>Dob</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="elephant in tableData" :key="elephant._id">
        <td> {{ elephant.index }} </td>
        <td> {{ elephant.name }} </td>
        <td> {{ elephant.species }} </td>
        <td> {{ elephant.sex }} </td>
        <td> {{ elephant.affiliation }} </td>
        <td> {{ elephant.dob }} </td>
      </tr>
    </tbody>
    <tfoot>
      <tr>
        <td>
          <p>
            PAGE {{ displayedPage }} OF {{ totalPages }}
          </p>
          <button :disabled="displayedPage === 1" @click="displayPrevious">
            <svg width="9" height="12" viewBox="0 0 9 12" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M8.16 1.41L3.58 6L8.16 10.59L6.75 12L0.750004 6L6.75 0L8.16 1.41Z" fill="#C4CDD5"/>
            </svg>
          </button>
          <button class="active"> {{ displayedPage }} </button>
          <button :disabled="displayedPage === totalPages" @click="displayNext"> {{ displayedPage + 1 }} </button>
          <button :disabled="displayedPage === totalPages" @click="displayNext">
            <svg width="9" height="12" viewBox="0 0 9 12" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M0.839996 1.41L5.42 6L0.839996 10.59L2.25 12L8.25 6L2.25 0L0.839996 1.41Z" fill="#C4CDD5"/>
            </svg>
          </button>
        </td>
      </tr>
    </tfoot>
  </table>
</template>

<script>
export default {
  data() {
    return {
      tableData: [],
      dataLength: 0,
      displayedPage: 1,
      totalPages: 0
    }
  },
  mounted() {
    this.getElephants(0)
  },
  methods: {
    async getElephants(from) {
      const elephants = await fetch('https://acumen-elephantom.herokuapp.com/elephants/asian')
      
      await elephants.json()
      .then((response) => {
        const arrayOfElephants = response.data
        this.dataLength = arrayOfElephants.length
        this.totalPages = Math.round(arrayOfElephants.length / 8)

        this.tableData = []
        arrayOfElephants.forEach((elephant, index) => {
          if (index >= from && index <= from + 7) {
            this.tableData.push({
              _id: elephant._id,
              index: index + 1,
              name: elephant.name,
              species: elephant.species,
              sex: elephant.sex,
              affiliation: elephant.affiliation,
              dob: elephant.dob
            })
          }
        });
      })
    },
    displayNext() {
      const from = this.displayedPage * 8

      this.getElephants(from)
      ++this.displayedPage
    },
    displayPrevious() {
      const from = (this.displayedPage - 2) * 8

      this.getElephants(from)
      --this.displayedPage
    }
  }
}
</script>

<style scoped>
table {
  margin: 60px 35px;
  width: calc(100% - 70px);
  max-width: 1009px;
  display: grid;
  overflow-x: auto;
}

caption {
  padding: 27px;
  font-size: 18px;
  font-weight: 700;
  line-height: 28px;
  text-align: left;
  color: #30425A;
  background-color: #FFF;
}

tr {
  padding: 25px 31px;
  display: grid;
  grid-template-columns: 35px repeat(5, max-content);
  justify-content: space-around;
  column-gap: 25px;
  text-align: center;
}

thead tr {
  font-size: 18px;
  line-height: 28px;
  color: #000;
  background-color: #E5E5E5;
}

th {
  font-weight: 400;
}

tbody tr {
  font-size: 16px;
  line-height: 25px;
  color: #848383;
}

tfoot tr {
  grid-template-columns: 1fr;
  justify-items: center;
  background-color: #FFF;
}

tbody tr:nth-child(even) {
  background-color: #F5F5F5;
}

tbody tr:nth-child(odd) {
  background-color: #FFF;
}

tfoot td {
  display: grid;
  grid-template-columns: repeat(5, max-content);
  align-items: center;
  column-gap: 8px;
}

tfoot p {
  margin: 0 12px 0 0;
  font-size: 14px;
  line-height: 15px;
  color: #30425AE6;
}

tfoot button {
  width: 32px;
  height: 32px;
  padding: 0;
  border: 1px solid #DFE3E8;
  border-radius: 4px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #FFF;
  cursor: pointer;
}

tfoot button:disabled {
  background-color: #919EAB;
  opacity: 0.5;
  cursor: not-allowed;
}

.active {
  border-color: #0546E0;
  color: #0546E0;
}
</style>