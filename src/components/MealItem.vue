<template>
  <div class="bg-white shadow rounded-xl hover:scale-105 transition-all">
    <router-link :to="{ name: 'mealDetails', params: { id: meal.idMeal } }">
      <img
        :src="meal.strMealThumb"
        :alt="meal.strMeal"
        class="rounded-t-xl w-full h-48 object-cover"
      />
    </router-link>
    <div class="p-3">
      <h3 class="font-bold">{{ meal.strMeal }}</h3>
      <p class="m-4">
        {{ $filters.truncateWords(meal.strInstructions, 20) }}
      </p>
      <div class="flex items-center justify-between">
        <YouTubeBtn :href="meal.strYoutube" />
      </div>
    </div>
  </div>
</template>
<script setup>
import { onMounted } from "vue";
import YouTubeBtn from "../components/YouTubeBtn.vue";
const { meal } = defineProps({
  meal: Object,
});
</script>
