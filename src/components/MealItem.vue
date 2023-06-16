<template>
  <div class="bg-white shadow rounded-xl">
    <router-link :to="{ name: 'mealDetails', params: { id: meal.idMeal } }">
      <img
        :src="meal.strMealThumb"
        :alt="meal.strMeal"
        class="rounded-t-xl w-full h-60 object-cover"
      />
    </router-link>
    <div class="p-3">
      <h3 class="font-bold">{{ meal.strMeal }}</h3>
      <p class="m-4">
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Recusandae
        dignissimos tempora sequi architecto, eaque accusamus reiciendis
      </p>
      <div class="flex items-center justify-between">
        <YouTubeBtn :href="meal.strYoutube">YouTube</YouTubeBtn>
      </div>
    </div>
  </div>
</template>
<script setup>
import YouTubeBtn from "../components/YouTubeBtn.vue";
const { meal } = defineProps({
  meal: {
    required: true,
    type: Object,
  },
});
</script>
