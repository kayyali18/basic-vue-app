<template>
  <div id="app">
    <h1> Welcome to my First Vue App </h1>
    <figcaption>Click on the NASA Logo to see the pictures of the month</figcaption>
    <img alt="Nasa logo" src="./assets/nasa-logo.svg" v-on:click="show = !show">

    <PicList class="piclist" v-bind:show="show" msg="I am your PICLIST Components" v-for="pic in picArray" v-bind:pic="pic" v-bind:key="pic.name" />
    <a class="stick-btn" href="#top"><span>Go</span> Top</a>
    <!-- <Search msg="Search"></Search> -->

  </div>
</template>

<script>
import PicList from './components/PicList.vue'
import { data } from './utils/mockData.js'

export default {
  name: 'app',
  data: function() {
    return {
      picArray: [],
      other: { msg: 'hello' },
      show: false,
    }
  },
  components: {
    PicList,
  },
  created() {
    this.fetchNasa()
  },
  methods: {
    fetchNasa: async function() {
      // const response = await fetch(nasaURL)
      this.picArray = data
    },
  },
}
</script>

<style>
body {
  margin: 0;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: grid;
  grid-template-areas:
    'h1 h1 h1'
    'figcaption figcaption figcaption'
    'logo logo logo';
}

h1 {
  grid-area: h1;
}

figcaption {
  grid-area: figcaption;
}

img {
  grid-area: logo;
  margin: auto;
}

.stick-btn {
  border-radius: 15px;
  position: relative;
  left: -60px;
  height: 100px;
  width: 100px;
  display: flex;
  padding-right: 1rem;
  flex-direction: column;
  align-items: flex-end;
  justify-content: center;
  position: fixed;
  bottom: 10px;
  background-color: #171717;
  transition: 0.4s;
}

.stick-btn:hover {
  left: -30px;
}

a {
  text-decoration: none;
}

a:visited {
  color: white;
}
</style>
