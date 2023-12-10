<script setup>
import Fish from "./Fish.vue";
defineProps(["allFish"]);
defineEmits(["remove"]);
</script>

<template>
  <div
    class="w-4/5 bg-aquarium bg-cover bg-center bg-no-repeat relative overflow-hidden"
    id="aquarium"
  >
    <Fish
      v-for="(fish, index) in allFish"
      :key="index"
      :fish="fish"
      @remove="$emit('remove', fish)"
    />
  </div>
</template>

<style scoped></style>
