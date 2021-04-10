<template>
  <div style="padding-left: 75px; padding-right: 75px; padding-top: 20px; padding-bottom: 20px;">
    <v-card color="basil">
      <v-card-title class="text-center justify-center py-6">
        <NuxtLink to="/">
          <v-icon
            large
            color="green darken-2"
            style="margin-right: 10px;"
            @click="this.$router.push('index')"
          >
            mdi-domain
          </v-icon></NuxtLink>
        <h1 class="font-weight-bold display-3 basil--text">
          About Ride Share App
        </h1>
      </v-card-title>

      <v-tabs
        v-model="tab"
        background-color="basil"
        color="basil"
        grow
        centered
      >
        <v-tab
          v-for="item in items"
          :key="item"
        >
          {{ item.name }}
        </v-tab>
      </v-tabs>

      <v-tabs-items v-model="tab">
        <v-tab-item
          v-for="item in items"
          :key="item"
        >
          <v-card
            color="basil"
            flat
          >
            <v-card-text>{{ item.des }}</v-card-text>
            <v-row style="padding-left: 35px; padding-bottom: 25px;">
              <v-col md="6">
                <v-img
                  align="center"
                  justify="center"
                  :aspect-ratio="16/9"
                  :src="item.img"
                ></v-img>
              </v-col>
            </v-row>
          </v-card>
        </v-tab-item>
      </v-tabs-items>
    </v-card>
  </div>
</template>

<script>
export default {
  name: "index",
  data () {
    return {
      tab: null,
      items: [
        {
          img: 'https://cdn.ndtv.com/tech/images/ola_share.jpg?output-quality=80&output-format=webp',
          name: 'Driver',
          des: 'The app always has available drivers for your service. You can enter your co-ordinates and a driver will be there for you',
        },
        {
          img: 'https://d540vms5r2s2d.cloudfront.net/mad/uploads/mad_blog_5c138c8f9f90f1544785039.png',
          name: 'Rider',
          des: 'As a rider you can always search for drivers five them rating and get you calculted fare as well',
        },
        {
          img: 'https://echoinnovateit.com/wp-content/uploads/2020/01/Car-Pooling-And-Ride-Sharing-Apps-e1579598886486.jpg',
          name: 'Rating',
          des: 'The rating system will help you to give us feed back about the rider and also a chance to improve our self',
        },
        {
          img: 'https://res.cloudinary.com/practicaldev/image/fetch/s--PhhDXlXd--/c_imagga_scale,f_auto,fl_progressive,h_420,q_auto,w_1000/https://thepracticaldev.s3.amazonaws.com/i/9ojzqyykyzjtavwjr9pu.jpg',
          name: 'Moto',
          des: 'Our main moto is to implement a micro service system but you can also get a few riders and drivers as well'
        },
      ],
    }
  },
}
</script>

<style scoped>
.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 50px;
  color: #35495e;
  letter-spacing: 1px;
  justify-content: center;
}
.basil {
  background-color: #FFFBE6 !important;
}
.basil--text {
  color: #356859 !important;
}
</style>
