<template>
  <div class="p-8 pb-0">
    <h1 class="text-4xl font-bold mb-4 text-orange-500">
      Search Meals by Name
    </h1>
  </div>
  <div class="px-8 pb-0">
    <input
      v-model="keyWord"
      type="text"
      class="rounded border-2 bg-white border-gray-200 focus:ring-orange-500 focus:border-orange-500 w-full"
      placeholder="Search for meals"
      @change="searchMeals"
    />
  </div>
  <div class="mt-4">
    <Meals :meals="meals" />
  </div>
</template>
<script setup>
import { computed } from "@vue/reactivity";
import { onMounted, ref } from "vue";
import { useRoute } from "vue-router";
import store from "../store/store";
import Meals from "../components/Meals.vue";

const route = useRoute();
const keyWord = ref("");
const meals = computed(() => store.state.searchedMeals);

function searchMeals() {
  if (keyWord.value) {
    store.dispatch("searchMeals", keyWord.value);
  } else {
    store.commit("setSearchedMeals", []);
  }
}
onMounted(() => {
  keyWord.value = route.params.name;
  if (keyWord.value) {
    searchMeals();
  }
});
</script>
