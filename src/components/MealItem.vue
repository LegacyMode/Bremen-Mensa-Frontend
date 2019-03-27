<template>
    <div class="meal">
            <p class="type">{{ meal.type }}</p>
            <p class="name">{{ meal.meal[0].name }}</p>
            <p class="costs">{{ meal.meal[0].costs }}</p>
    </div>
</template>

<script>
export default {
    name: "MealItem",
    props: ["meal"],
}
</script>

<style scoped>
.meal {
    background: #efe;
    margin: 1rem 0;
    padding: 0;
    display: grid;
    grid-template-columns: 1fr;
    align-items: center;
    box-shadow: 5px 5px 2.5px grey;
}

.meal p {
    display: inline;
    padding: 0;
    margin: 0.5rem 0;
}

.meal p.name {
    font-weight: bold;
}

.meal p.type {
    background: rgb(255, 194, 103);
    margin: 0;
    padding: 0.5rem 0;
}

</style>
