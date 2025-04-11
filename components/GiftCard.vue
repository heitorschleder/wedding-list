<template>
  <div 
    @click="$emit('click')"
    class="bg-white rounded-lg shadow-md overflow-hidden cursor-pointer transform transition hover:scale-105"
  >
    <img :src="gift.image" :alt="gift.title" class="w-full h-48 object-cover">
    <div class="p-4">
      <h3 class="text-lg font-semibold text-gray-800">{{ gift.title }}</h3>
      <p class="text-gray-600 mt-2">R$ {{ gift.price.toFixed(2) }}</p>
    </div>
  </div>
</template>

<script setup>
defineProps({
  gift: {
    type: Object,
    required: true
  }
})
</script>