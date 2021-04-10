<template>
  <div class="container">
    <div>
      <h1 class="title">
        Welcome To Ride Share App
      </h1>
      <div class="links">
        <a
          href="about"
          class="button--green"
        >
          About us
        </a>
        <a
          href="about"
          class="button--green"
        >
          Driver
        </a>
        <a
          href="about"
          class="button--green"
        >
          Rider
        </a>
        <v-row class="subtitle" style="margin-top: 20px; margin-left: 10px;">
          Code Base Link for the projects
        </v-row>
        <v-row
          style="
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 35px;
        ">
          <a
            href="https://github.com/RadowanMahmud/RideShare-Backend.git"
            target="_blank"
            rel="noopener noreferrer"
            class="button--grey"
          >
            Back End
          </a>
          <a
            href="https://github.com/RadowanMahmud/RideShare-frontend.git"
            target="_blank"
            rel="noopener noreferrer"
            class="button--grey"
          >
            Front End
          </a>
        </v-row>
      </div>
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

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
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
