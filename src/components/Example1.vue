<script setup lang="ts">
import {onMounted, ref} from "vue";
import autoAnimate from "@formkit/auto-animate";

let numbers = ref(Array.from({ length: 100 }, (y, i) => i));

function shuffle() {
  numbers.value.sort(() => 0.5 - Math.random());
}

let container = ref();

onMounted(() => {
  autoAnimate(container.value);
})

</script>

<template>
  <section ref="container" class="flex flex-wrap gap-4">
    <div v-for="number in numbers" :key="number" v-text="number"
         class="bg-gray-200 w-12 h-12 flex items-center justify-center text-black"
    />
  </section>

  <div class="fixed bootom-4 right-4">
    <button class="bg-red-500 rounded text-white m-2" @click="shuffle">Shuffle</button>
    <button class="bg-red-500 rounded text-white m-2" @click="numbers.push(100)">Add</button>
    <button class="bg-red-500 rounded text-white m-2" @click="numbers.unshift(100)">Add in begining</button>
  </div>
</template>