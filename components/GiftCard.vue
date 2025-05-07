<template>
  <div @click="$emit('click')"
    class="bg-gray-50 rounded-lg shadow-md overflow-hidden cursor-pointer transform transition hover:scale-105">
    <!-- Flor após cada linha de 3 cards (ou 2 em md), adaptável -->
    <img :src="gift.image" :alt="gift.title" class="w-full h-48 object-cover">
    <div class="p-4 text-[#53682F]">
      <h3 class="text-lg font-semibold ">{{ gift.title }}</h3>
      <p class=" mt-2">R$ {{ gift.price.toFixed(2) }}</p>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  gift: {
    type: Object,
    required: true
  }
})
</script>