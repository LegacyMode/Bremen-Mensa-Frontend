<template>
  <div class="meal">
    <p class="type">{{ meal.type }}</p>
    <span class="entry" v-bind:key="m.name" v-for="m in meal.meal">
      <p class="name">{{ m.name }}</p>
      <p v-show="m.costs" class="costs">{{ m.costs }}</p>
    </span>
  </div>
</template>

<script>
export default {
  name: "MealItem",
  props: ["meal"]
};
</script>

<style scoped>
.meal {
  margin: 0rem 0rem;
  padding: 1.5rem 0rem;
  display: block;
  grid-template-columns: 1fr;
  align-items: center;
  width: 100%;
  border-bottom: solid black 1px;
}

.meal p {
  padding: 0;
  margin: 0;
  float: left;
  text-align: left;
}

.meal p.name {
  font-size: 1rem;
  width: 80%;
  flex-grow: 1;
}

.meal .entry {
  width: 100%;
  padding: 1rem 0rem;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}

.meal p.type {
  font-size: 1rem;
  font-weight: bold;
  margin: 0;
}

.meal p.costs {
  font-size: 1rem;
  margin-left: 2rem;
  text-align: right;
}
</style>
