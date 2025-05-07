<script setup>
import DarkSoulsImage from '@/assets/images/darksouls.png'
import PanelaImage from '@/assets/images/panela.png'
import CobertaImage from '@/assets/images/coberta.png'
import ChimaImage from '@/assets/images/chimarrao.png'
import GymImage from '@/assets/images/gym.png'
import TravelImage from '@/assets/images/travel.png'

const gifts = ref([
  {
    id: 1,
    title: 'Edredom para noiva que esta sempre coberta de razão',
    price: 291.12,
    image: CobertaImage,
    pixCode: '00020126670014BR.GOV.BCB.PIX0126heitorschleder33@gmail.com0215cafeteira teste52040000530398654040.015802BR5925Heitor de Oliveira Schled6009SAO PAULO62140510br7dCaacm16304338B'
  },
  {
    id: 2,
    title: 'DarkSouls III pro noivo não se estressar com a noiva',
    price: 171.00,
    image: DarkSoulsImage,
    pixCode: 'FAZOPIXPRABRUNA'
  },
  {
    id: 3,
    title: 'Panela de pressão "inexplodível" pros noivos não se matarem',
    price: 242.23,
    image: PanelaImage,
    pixCode: 'pixcode789'
  },
  {
    id: 4,
    title: 'Kit Chimarrão para o casal',
    price: 159.36,
    image: ChimaImage,
    pixCode: 'pixcode789'
  },
  {
    id: 5,
    title: '3 Meses de academia para gastar todas as calorias do casamento',
    price: 423.71,
    image: GymImage,
    pixCode: 'pixcode789'
  },
  {
    id: 6,
    title: 'Auxilio viagem',
    price: 203.40,
    image: TravelImage,
    pixCode: 'queroviajar'
  }
])

const isModalOpen = ref(false)
const selectedGift = ref(null)

const openGiftModal = (gift) => {
  selectedGift.value = gift
  isModalOpen.value = true
}

const closeGiftModal = () => {
  isModalOpen.value = false
  selectedGift.value = null
}
</script>

<template>
  <div class="min-h-screen bg-[#E7E2CC]">
    <header class="text-white">
      <div class="text-center text-[#873f2B] max-w-7xl mx-auto py-6 px-4 sm:px-6 lg:px-8">
        <h1 class="text-5xl font-bold">
          Lista de Presentes de Heitor e Bruna
        </h1>
        <p class="mt-2">
          Agradecemos seu carinho! Escolha um presente abaixo.
        </p>
      </div>
    </header>
    <div class="flex justify-center items-center my-4">
      <img src="@/assets/images/flor2.webp" alt="Flor decorativa" class="w-84 h-24 mt-0 mb-0" />
    </div>
    <main class="max-w-7xl mx-auto py-6 sm:px-6 lg:px-8">
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
        <GiftCard v-for="gift in gifts" :key="gift.id" :gift="gift" @click="openGiftModal(gift)" />
      </div>

      <GiftModal v-if="isModalOpen" :is-open="isModalOpen" :gift="selectedGift" @close="closeGiftModal" />
      <div class="flex justify-center items-center my-4">
      <img src="@/assets/images/flor2.webp" alt="Flor decorativa" class="w-84 h-24 mt-0 mb-0" />
    </div>
    </main>
   
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Pinyon+Script&display=swap');

h1 {
  font-family: 'Pinyon Script', cursive;
  font-weight: 400;
  font-style: normal;
}
</style>