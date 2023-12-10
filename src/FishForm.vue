<script setup>
import { ref } from "vue";

const emit = defineEmits(["add"]);

const fishes = [
  "golden-purple-fish.png",
  "goldfish.png",
  "guppie.png",
  "tropical-fish.png",
  "tuna.png",
];

const selectedFish = ref(fishes[0]);
const name = ref("");
</script>

<template>
  <div>
    <form
      @submit.prevent="$emit('add', { name, src: selectedFish })"
      class="flex flex-col gap-y-5 p-5"
    >
      <div class="grid grid-cols-2 gap-5">
        <img
          v-for="(fish, index) in fishes"
          :key="index"
          :src="`/${fish}`"
          alt="fish"
          width="120"
          class="cursor-pointer"
          :class="{
            'drop-shadow-[0_1px_5px_#fff]': selectedFish === fish,
          }"
          @click="selectedFish = fish"
        />
      </div>

      <input
        type="text"
        class="rounded outline-none bg-transparent border px-4 py-2 text-white"
        v-model="name"
        required
      />

      <button
        type="submit"
        class="text-white font-bold border rounded w-1/2 p-2"
      >
        Add
      </button>
    </form>
  </div>
</template>
