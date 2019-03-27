<template>
  <div id="app">
    <div class="header">
      <img src="./assets/UniBremen.png" >
      <h1>Mensa Speiseplan</h1>
    </div>
    <NavBar
      v-bind:meals="meals"
      v-bind:dayIndex ="dayIndex"
      v-on:dayClicked="dayIndex = $event"
    />
    <MealFilter
      v-bind:meals="meals[dayIndex]"
      v-bind:filter="filter"
      v-on:typeClicked="toggleFilter"
    />
    <Meals 
      v-bind:meals="meals[dayIndex]" 
      v-touch:swipe="swipeHandler"
      v-bind:filter="filter" 
    />
  </div>
</template>

<script>
import Meals from "./components/Meals.vue";
import MealFilter from "./components/MealFilter.vue";
import NavBar from "./components/NavBar.vue";

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
    MealFilter
  },
  data() {
    return {
      // fill with dummy data to avoid loading errors during async get request
      meals: [0,1,2,3,4],
      showFilter: false,
      filter: [],
      dayIndex: 0
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
  
  // when created fetch the meals from the API
  created() {  
      axios.get('https://legacymo.de/v2/api/')
          .then(data => this.meals = data.data)
          .catch(err => console.log(err))
          /* dummy data
          this.meals = [
            {
            "day": "Mittwoch",
            "date": "20. März",
            "food": 
              [
                {
                  "type" : "Essen 1",
                  "meal" : [{"name" : "mega schnitzel", "costs" : "2,35€"}]
                },
                {
                  "type" : "Essen 2",
                  "meal" : [{"name" : "mega brot", "costs" : "1,35€"}]
                },
                {
                  "type" : "Vegetarische Theke",
                  "meal" : [{"name" : "mega falafel", "costs" : "3,10€"}]
                }
              ]
            }, 1,2,3,4
          ]*/
          
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  font-size: 12px;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 20px;
  padding: 2rem 2rem;
  background: rgb(186, 226, 186);
}

.header {
  display: grid;
}

.header img {
  width: 30%;
  height: auto;
}

@media screen and (max-width: 719px) {
  .nav p {
    display: none;
  }
  
  .nav p.highlight {
    display: block;
    background:#efe;
    color: #2c3e50;
    font-size: 1.2rem;
  }

  .nav {
    grid-template-columns: 1fr;
  }
}
</style>
