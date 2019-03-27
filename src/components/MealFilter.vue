<template>
    <div class="filter">
        <p 
            @click="showFilter = !showFilter" 
            class="toggle" 
            :class="{highlight:showFilter}"><i class="fas fa-filter fa-2x"></i></p>
        <transition name="fade">
          <div class="filterList" v-if="showFilter">
              <p 
                  v-bind:key="meal.type" 
                  v-for="meal in meals.food"
                  v-on:click="$emit('typeClicked', meal.type)"
                  :class="{highlight:!filter.includes(meal.type)}" >
                  {{ meal.type }}
              </p>
          </div>
        </transition>
    </div>
</template>

<script>
export default {
    name: "MealFilter",
    props: ["filter", "meals"],
    data() {
        return{
            showFilter: false
        }
    }
}
</script>

<style scoped>
/* toggle */

.toggle {
  display:inline-block;
  font-size: 14px;
  padding: 1rem;
  width: 30px;
  height: 30px;
  border-radius: 50%;
  background: #efe;
  cursor: pointer;
}

.toggle.highlight {
  background: #95C11F;
  color: white;
}

/* filter list */

.filterList {
  display: grid;
  grid-template-columns: 1fr 1fr;
  justify-items: center; 
  margin: 1rem 0;
  overflow: hidden;
}

.filterList p {
  width: 70%;
  margin: 0.5rem;
  padding: 0.3rem;
  min-height: 2rem;
  background: #efe;
}

.filterList p.highlight{
  background: #95C11F;
  color: white;
}

/* transitions */

.fade-enter-active, .fade-leave-active {
  transition: all .5s ease;
}

.fade-leave, .fade-enter-to {
  opacity: 1;
}

.fade-enter, .fade-leave-to {
  opacity: 0;
  /* transform: translateY(-20px); */
}

</style>
