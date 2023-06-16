<template>
  <div class="flex flex-col p-8">
    <input
      type="text"
      class="w-full rounded border-2 border-gray-200"
      placeholder="Search For Meals"
    />
  </div>
</template>
<script setup>
import { computed, onMounted, ref } from "vue";
import store from "../store/store";
import axiosClient from "../axiosClient";

const ingredients = ref([]);

onMounted(async () => {
  const response = await axiosClient.get("/list.php?i=list");
  console.log(response.data);
  ingredients.value = response.data;
});
</script>
