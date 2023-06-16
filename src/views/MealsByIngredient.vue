<template>
  <div class="grid grid-cols-1 md:grid-cols-3 gap-5 p-8">
    <MealItem v-for="meal of meals" :key="meal.idMeal" :meal="meal" />
  </div>
  <div v-if="!meals" class="flex justify-center text-gray-600">
    There are no meals
  </div>
</template>
<script setup>
import { computed, onMounted } from "vue";
import { useRoute } from "vue-router";
import MealItem from "../components/MealItem.vue";
import store from "../store/store";

const route = useRoute();
const meals = computed(() => store.state.mealsByIngredient);

onMounted(() => {
  store.dispatch("searchMealsByIngredient", route.params.ingredient);
});
</script>
