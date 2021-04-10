<template>
  <div v-if="driver.length > 0" class="container">
    <h1 class="subtitle">List Of Drivers</h1>
    <v-data-table
      style="padding: 50px"
      :headers="headers"
      :items="driver"
      class="elevation-1"
      align="center"
    >
      <template v-slot:item.status="{ item }">
        <v-chip
          :color="getColor(item.status)"
          dark
        >
          {{ item.status }}
        </v-chip>
      </template>
      <template v-slot:item.rating="{ item }">
        <v-rating
          v-model="item.rating"
          background-color="purple lighten-3"
          color="purple"
          half-increments
        ></v-rating>
      </template>
    </v-data-table>
  </div>
</template>

<script>
export default {
  name: "index",
  data(){
    return{
     driver: [],
      headers: [
        {
          text: 'Name',
          align: 'start',
          sortable: true,
          value: 'name',
        },
        { text: 'Car', value: 'car' },
        { text: 'X co-ordinate', value: 'positionX' },
        { text: 'Y co-ordinate', value: 'positionY' },
        { text: 'Status', value: 'status' },
        { text: 'Rating', value: 'rating' },
      ],
    }
  },
  mounted() {
    this.fetchDriver()
  },
  methods: {
    getColor (status) {
      if (status ===  true) return '#177420'
      else return '#ED5824'
    },
    fetchDriver(){
      console.log('fetiching')
      this.$axios.get('/driver/fetch').then((response)=>{
        this.driver = response.data
        console.log(this.driver)
      })
    }
  },
}
</script>

<style scoped>
.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
</style>
