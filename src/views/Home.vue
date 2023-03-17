<template>
  
    <div class="w-[100vw] flex flex-col p-8">
      <h1 class="ml-10 font-bold text-2xl text-gray-600">Meal of The Day</h1>
      <Meals :meals="meals" />
    </div>
    
</template>

<script setup>
import { computed, onMounted } from 'vue';
import Meals from '../components/Meals.vue';
import axiosClient from '../axiosClient.js'
import store from '../store';
import { useRoute } from 'vue-router';

const route = useRoute()
const meals = computed(() => store.state.randomMeals)
onMounted(async () => {
  store.dispatch('randomMeals', route.params.meals)
})
onMounted(() => {
    axiosClient.get('random.php')
    .then(({data}) => {
        meals.value = data.meals
    })
  })

</script>