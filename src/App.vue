<script setup>
import { ref } from "vue";
import FishForm from "./FishForm.vue";
import Aquarium from "./Aquarium.vue";

const allFish = ref([]);

const remove = (fish) => {
  allFish.value = allFish.value.filter((f) => f.id !== fish.id);
};
</script>

<template>
  <div class="flex h-screen w-screen">
    <FishForm class="w-1/5 bg-[#1f3d7c]" @add="allFish.push($event)" />
    <Aquarium @remove="remove" :all-fish="allFish" />
  </div>
</template>
