<template>
  <div class="p-8 pb-0">
    <input
      v-model="keyWord"
      type="text"
      class="rounded border-2 border-gray-200 w-full"
      placeholder="Search for meals"
      @change="searchMeals"
    />
  </div>
  <div class="grid grid-cols-1 md:grid-cols-3 gap-5 p-8">
    <div
      v-for="meal of meals"
      :key="meal.idMeal"
      class="bg-white shadow rounded-xl"
    >
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
          <a
            :href="meal.strYoutube"
            target="_blank"
            class="px-3 py-2 rounded border-2 border-red-600 text-white bg-red-500 hover:bg-red-600 transition-colors"
            >YouTube</a
          >
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
import { computed } from "@vue/reactivity";
import { onMounted, ref } from "vue";
import { useRoute } from "vue-router";
import store from "../store/store";
const route = useRoute();

const keyWord = ref("");
const meals = computed(() => store.state.searchedMeals);

function searchMeals() {
  store.dispatch("searchMeals", keyWord.value);
}
onMounted(() => {
  keyWord.value = route.params.name;
  if (keyWord.value) {
    searchMeals();
  }
});
</script>
