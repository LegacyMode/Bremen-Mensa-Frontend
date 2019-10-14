<template>
  <div id="app">
    <div class="header">
      <h1>Mensa Speiseplan</h1>
    </div>
    <NavBar
      v-bind:meals="meals"
      v-bind:dayIndex ="dayIndex"
      v-on:dayClicked="dayIndex = $event"
    />
    <transition :name="`slide-${transition}`" mode="out-in">
      <Meals
        :key="dayIndex"
        v-bind:meals="meals[dayIndex]"
        v-touch:swipe="swipeHandler"
        v-bind:filter="filter"
      />
    </transition>
    <Footer></Footer>
  </div>
</template>

<script>
import Meals from "./components/Meals.vue";
import MealFilter from "./components/MealFilter.vue";
import NavBar from "./components/NavBar.vue";
import Footer from "./components/Footer.vue";

import Vue from 'vue'
import axios from 'axios'
import Vue2TouchEvents from 'vue2-touch-events'

Vue.use(Vue2TouchEvents,{
  tapTolerance: 10,
  swipeTolerance: 30,
})

export default {
  name: "app",
  components: {
    NavBar,
    Meals,
    MealFilter,
    Footer
  },
  data() {
    return {
      // fill with dummy data to avoid loading errors during async get request
      meals: [0,1,2,3,4],
      showFilter: false,
      filter: [],
      dayIndex: 0,
      transition: ""
    }
  },
  methods :{
    swipeHandler(direction) {
      if(direction === "right" && this.dayIndex !== 0) this.dayIndex--;
      if(direction === "left" && this.dayIndex !== 4) this.dayIndex++;
    },
    toggleFilter(type) {
      if(this.filter.includes(type)) {
        this.filter = this.filter.filter( (element) => element !== type);
      } else this.filter = this.filter.concat(type);
    }
  },
  watch: {
    dayIndex(newValue, oldValue) {
      this.transition = oldValue < newValue ? "right" : "left";
    }
  },
  // when created fetch the meals from the API
  created() {
      axios.get('https://legacymo.de/v2/api/')
          .then(data => this.meals = data.data)
          .catch(err => console.log(err))
  }
};
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=IBM+Plex+Mono:300,400,500,600,700&display=swap');
@import url('./style/slide.css');

body {
  overflow-x: hidden;
}

#app {
  font-family: 'IBM Plex Mono', monospace;
  font-size: 12px;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  padding: 0rem 1rem;
  background: rgb(255, 255, 255);
  max-width: 768px;
  height: 100%;
  margin: 0 auto;
}

@media (max-width: 768px) { 
  #app {
    overflow-x: hidden;
  }
}

.header {
  display: grid;
  font-size: 1rem;
  font-weight: 700;
}

.h1 {
  margin: 0;
}

.header img {
  width: 30%;
  height: auto;
}
</style>
