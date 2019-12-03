<template>
  <!-- iterate through the meals and pass them to the MealItem -->
  <div class="container">
    <MealItem
      v-bind:key="meal.type"
      v-for="meal in meals.food"
      v-show="meal.type"
      v-bind:meal="meal"
    />
  </div>
</template>

<script>
import MealItem from "./MealItem.vue";

export default {
  name: "Meals",
  components: {
    MealItem
  },
  props: ["meals", "filter"]
};
</script>

<style scoped>
.container {
  width: 100%;
  height: auto;
}
</style>
