<template>
  <div>
    <div class="flex justify-center gap-2">
      <router-link
        :to="{ name: 'byLetter', params: { letter } }"
        :key="letter"
        v-for="letter of letters"
      >
        {{ letter }}
      </router-link>
    </div>

    <Meals :meals="meals" />
  </div>
</template>
<script setup>
import { watch } from "vue";
import { computed } from "@vue/reactivity";
import { useRoute } from "vue-router";
import { onMounted } from "vue";
import store from "../store";
import Meals from "../components/Meals.vue";

const route = useRoute();
const letters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ".split("");
const meals = computed(() => store.state.mealsByLetter);

watch(route, () => {
  store.dispatch("searchMealsByLetter", route.params.letter);
});

onMounted(() => {
  store.dispatch("searchMealsByLetter", route.params.letter);
});
</script>
