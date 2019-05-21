<template>
    <div class="nav" >
      <p v-on:click="$emit('dayClicked', 0)" :class="{highlight:dayIndex == 0}">{{ meals[0].day | capitalize}}</p>
      <p v-on:click="$emit('dayClicked', 1)" :class="{highlight:dayIndex == 1}">{{ meals[1].day | capitalize}}</p>
      <p v-on:click="$emit('dayClicked', 2)" :class="{highlight:dayIndex == 2}">{{ meals[2].day | capitalize}}</p>
      <p v-on:click="$emit('dayClicked', 3)" :class="{highlight:dayIndex == 3}">{{ meals[3].day | capitalize}}</p>
      <p v-on:click="$emit('dayClicked', 4)" :class="{highlight:dayIndex == 4}">{{ meals[4].day | capitalize}}</p>
    </div>
</template>

<script>
export default {
    name: "NavBar",
    props: ["meals", "dayIndex"],

    filters: {
      capitalize: function (value) {
      if (!value) return ''
      value = value.toString()
      return value.substring(0,2 ).toUpperCase()
    }
  }
}
</script>

<style scoped>
.nav {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  grid-gap: 0 0rem;
  max-width: 500px;
  margin: 0 auto;
}

.nav p{
  font-size: 0.8rem;
  padding: 0rem 1rem;
  cursor: pointer;
}

.nav p.highlight {
  font-weight: 700;
}
</style>
