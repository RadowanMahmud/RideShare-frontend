<template>
  <diV>
    <div class="container">
      <h1 class="subtitle" style="margin-right: 35px">Add New Rider</h1>
      <v-form
        ref="form"
        @submit.prevent="saveRider"
      >
        <v-text-field
          id="ridername"
          v-model="rider.name"
          label="Name"
        ></v-text-field>

        <v-text-field
          v-model.number="rider.positionX"
          label="X axis Co-ordinate"
          required
        >
        </v-text-field>

        <v-text-field
          id="riderpox"
          v-model.number="rider.positionY"
          label="Y axis Co-ordinate"
          required
        >
        </v-text-field>

        <v-btn
          id="riderpoy"
          outlined
          class="mr-4"
          color="#177420"
          type="submit"
        >
          Submit
        </v-btn>

        <v-btn
          outlined
          class="mr-4"
          @click="resetForm"
        >
          Reset Form
        </v-btn>

      </v-form>
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
    </v-row>
  </diV>
</template>

<script>
export default {
  name: "index",
  data(){
    return{
      rider:{
        name: '',
        positionX: null,
        positionY: null,
        rating: 0,
      }
    }
  },
  methods:{
    resetForm(){
        this.rider.name = ''
        this.rider.positionX = null
        this.rider.positionY = null
    },
    saveRider(){
      console.log("calling")
      if(this.rider.name === '' || this.rider.positionX===null || this.rider.positionY===null){
          alert('Please Submit All Informations')
      }
      else{
        this.$axios.post('/rider/add', this.rider).then((response)=>{
            this.$router.push('/rider')
        })
      }
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
