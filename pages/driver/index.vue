<template>
  <div v-if="driver.length > 0">
    <div class="container">
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
        <template v-slot:item.action="{ item }">
              <tr>
                <td>
                  <v-btn class="mx-2" fab dark small color="#9F2610" style="padding: 2px" @click="deleteDriver(item._id)">
                    <v-icon dark>mdi-delete</v-icon>
                  </v-btn>
                </td>
              </tr>
        </template>
      </v-data-table>
    </div>
    <v-row
      style="
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 35px;
        ">
      <v-btn
        outlined
        color="indigo"
        style="margin-right: 20px;"
        large
      >
        <NuxtLink to="/">
          Home
        </NuxtLink>
      </v-btn>
      <v-btn
        outlined
        color="indigo"
        style="margin-right: 20px;"
        large
      >
        <NuxtLink to="/about">
          About us
        </NuxtLink>
      </v-btn>
      <NuxtLink to="/driver/create">
        <v-btn
          class="mx-2"
          fab
          dark
          color="cyan"
          small
        >
          <v-icon dark>
            mdi-plus
          </v-icon>
        </v-btn>
      </NuxtLink>
    </v-row>
  </div>
</template>

<script>
export default {
  name: "index",
  data(){
    return{
      driver: [],
      deletedriverForm: {
        id: '',
      },
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
        { text: 'Action', value: 'action' },
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
      })
    },
    deleteDriver(id){
        this.deletedriverForm.id = id
        this.$axios.post('/driver/delete', this.deletedriverForm ).then((response)=>{
          this.fetchDriver()
        })
    },
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
  min-height: 70vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
</style>
