<script setup lang="ts">
import { getDistanceKm, getDistanceMiles } from '@/utils/distance'
import { useGeolocation } from '@vueuse/core'
import { ref, computed } from 'vue'

// hint: coords.latitude + cords.latitude
const { coords, locatedAt } = useGeolocation()

const coordsForDisplay = computed(() => {
  if (unit.value === 'km') {
    return getDistanceKm(coords.value.latitude, coords.value.longitude);
  }
  return getDistanceMiles(coords.value.latitude, coords.value.longitude);
})

const unit = ref<'km' | 'mile'>('mile')

const toggleUnit = () => {
  if (unit.value === 'km') {
    unit.value = 'mile'
  } else {
    unit.value = 'km'
  }
}
</script>

<template>
  <!-- this should only render a slot -->
  <slot :coords="coordsForDisplay" :unit="unit" :toggleUnit="toggleUnit" :isFound="locatedAt" />
</template>
