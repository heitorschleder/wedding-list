<template>
  <div @click="$emit('click')"
    class="bg-gray-50 rounded-lg shadow-md overflow-hidden cursor-pointer transform transition hover:scale-105">
    <img :src="gift.image" :alt="gift.title" class="w-full h-48 object-cover">
    <div class="p-4 text-[#53682F]">
      <h3 class="text-lg font-semibold ">{{ gift.title }}</h3>
      <div class="flex justify-between items-center">
        <p class=" mt-2">R$ {{ gift.price.toFixed(2) }}</p>
        <button class="mt-4 px-4 py-2 bg-[#A6C34C] text-white rounded hover:bg-[#8AA03B] transition"
          @click.stop="$emit('click')">
          Comprar agora!
        </button>
      </div>
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