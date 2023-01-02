<script setup>
import NorthPoleDistance from './components/NorthPoleDistance.vue'
</script>

<template>
  <div class="container mx-auto px-4">
    <h2>Example 1</h2>
    <NorthPoleDistance v-slot="{ coords, unit, toggleUnit, isFound }">
      <span v-if="!isFound">Searching ... </span>
      <div v-else>
        <p>You are currently: {{  coords  }} {{ unit }} away from the North Pole.</p>
        <button class="bg-green text-white py-2 px-4 rounded" @click="toggleUnit">Toggle Unit</button>
      </div>
    </NorthPoleDistance>

    <h2 class="mt-16">Example 2</h2>
    <NorthPoleDistance v-slot="{ coords, unit, toggleUnit, isFound }">
      <span v-if="!isFound">Searching ... </span>
      <div v-else class="rounded border-2 border-gray-300 p-10 flex flex-col justify-center items-center gap-6">
        <p>Current distance from the North Pole</p>
        <span class="text-2xl">{{  coords  }} {{ unit }}</span>
        <button class="bg-red-400 py-2 px-4 rounded text-white" @click="toggleUnit">Switch to {{ unit === 'km' ? 'mile' : 'km' }}</button>
      </div>
    </NorthPoleDistance>
  </div>
</template>
