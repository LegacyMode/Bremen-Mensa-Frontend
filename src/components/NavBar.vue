<template>
    <div class="nav" >
      <p v-on:click="$emit('dayClicked', 0)" :class="{highlight:dayIndex == 0}">{{ meals[0].day }} <br> {{ meals[0].date }}</p>
      <p v-on:click="$emit('dayClicked', 1)" :class="{highlight:dayIndex == 1}">{{ meals[1].day }} <br> {{ meals[1].date }}</p>
      <p v-on:click="$emit('dayClicked', 2)" :class="{highlight:dayIndex == 2}">{{ meals[2].day }} <br> {{ meals[2].date }}</p>
      <p v-on:click="$emit('dayClicked', 3)" :class="{highlight:dayIndex == 3}">{{ meals[3].day }} <br> {{ meals[3].date }}</p>
      <p v-on:click="$emit('dayClicked', 4)" :class="{highlight:dayIndex == 4}">{{ meals[4].day }} <br> {{ meals[4].date }}</p>
    </div>
</template>

<script>
export default {
    name: "NavBar",
    props: ["meals", "dayIndex"]
}
</script>

<style scoped>
.nav {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  grid-gap: 0 1rem;
}

.nav p{
  background: #efe;
  padding: 1rem;
  cursor: pointer;
}

.nav p.highlight {
  background: #95C11F;
  color: white;
}
</style>
