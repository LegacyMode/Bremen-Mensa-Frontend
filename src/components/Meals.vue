<template>
<!-- iterate through the meals and pass them to the MealItem -->
<div>
    <div class="container">
        <div 
            v-bind:key="meal.type" 
            v-for="meal in meals.food" 
            v-show="!filter.includes(meal.type)">
            <MealItem v-bind:meal="meal" />
        </div>
    </div>
</div>

</template>

<script>
import MealItem from './MealItem.vue'

export default {
    name: "Meals",
    components: {
        MealItem
    },
    props: ["meals", "filter"]
}
</script>

<style scoped>


</style>
