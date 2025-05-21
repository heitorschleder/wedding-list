<script setup>
import DarkSoulsImage from '@/assets/images/darksouls.png'
import PanelaImage from '@/assets/images/panela.png'
import CobertaImage from '@/assets/images/coberta.png'
import ChimaImage from '@/assets/images/chimarrao.png'
import GymImage from '@/assets/images/gym.png'
import TravelImage from '@/assets/images/travel.png'
import Especial from '@/assets/images/especial.png'
import Helmet from '@/assets/images/helmet.png'
import Kitchen from '@/assets/images/kitchen.png'
import Lingerie from '@/assets/images/lingerie.png'
import Stick from '@/assets/images/stick.png'



const gifts = ref([
  {
    id: 1,
    title: 'Edredom para noiva que esta sempre coberta de razão',
    price: 291.12,
    image: CobertaImage,
    pixCode: '00020126480014BR.GOV.BCB.PIX0126heitorschleder33@gmail.com5204000053039865406291.125802BR5925Heitor de Oliveira Schled6009SAO PAULO62140510GCvuqp1X2b630470CF'
  },
  {
    id: 2,
    title: 'DarkSouls III pro noivo não se estressar com a noiva',
    price: 171.00,
    image: DarkSoulsImage,
    pixCode: '00020126480014BR.GOV.BCB.PIX0126heitorschleder33@gmail.com5204000053039865406171.005802BR5925Heitor de Oliveira Schled6009SAO PAULO62140510xbw0D71mbk63049DD5'
  },
  {
    id: 3,
    title: 'Panela de pressão "inexplodível" pros noivos não se matarem',
    price: 242.23,
    image: PanelaImage,
    pixCode: '00020126480014BR.GOV.BCB.PIX0126heitorschleder33@gmail.com5204000053039865406242.235802BR5925Heitor de Oliveira Schled6009SAO PAULO62140510AC64AV700M630426DF'
  },
  {
    id: 4,
    title: 'Kit Chimarrão para o casal',
    price: 159.36,
    image: ChimaImage,
    pixCode: '00020126480014BR.GOV.BCB.PIX0126heitorschleder33@gmail.com5204000053039865406159.365802BR5925Heitor de Oliveira Schled6009SAO PAULO62140510BLj7vCPEWQ630445B4'
  },
  {
    id: 5,
    title: '3 Meses de academia para gastar todas as calorias do casamento',
    price: 423.71,
    image: GymImage,
    pixCode: '00020126480014BR.GOV.BCB.PIX0126heitorschleder33@gmail.com5204000053039865406423.715802BR5925Heitor de Oliveira Schled6009SAO PAULO62140510QNPtVphJwP6304F412'
  },
  {
    id: 6,
    title: 'Auxilio viagem',
    price: 203.40,
    image: TravelImage,
    pixCode: '00020126480014BR.GOV.BCB.PIX0126heitorschleder33@gmail.com5204000053039865406203.405802BR5925Heitor de Oliveira Schled6009SAO PAULO62140510Jun0ok0McB6304C689'
  },
  {
    id: 7,
    title: 'Renovação do estoque de conchinhas para venda de artes na praia',
    price: 89.62,
    image: Especial,
    pixCode: '00020126580014BR.GOV.BCB.PIX0136e0ec7723-68aa-44d4-bb26-7102480094fe520400005303986540589.625802BR5918Bruna Cansian Knop6009SAO PAULO61080540900062110507conchas6304D9E7'
  },
  {
    id: 8,
    title: 'Curso de Culinária para Noiva',
    price: 245.50,
    image: Kitchen,
    pixCode: '00020126580014BR.GOV.BCB.PIX0136e0ec7723-68aa-44d4-bb26-7102480094fe5204000053039865406245.505802BR5918Bruna Cansian Knop6009SAO PAULO61080540900062090505curso63040132'
  },
  {
    id: 9,
    title: 'Lingerie para noiva usar na Lua de Mel',
    price: 119.80,
    image: Lingerie,
    pixCode: '00020126580014BR.GOV.BCB.PIX0136e0ec7723-68aa-44d4-bb26-7102480094fe5204000053039865406119.805802BR5918Bruna Cansian Knop6009SAO PAULO61080540900062120508lingerie6304E534'
  },
  {
    id: 10,
    title: 'Rolo de Massa para Noiva "educar" o Noivo',
    price: 77.43,
    image: Stick,
    pixCode: '00020126580014BR.GOV.BCB.PIX0136e0ec7723-68aa-44d4-bb26-7102480094fe520400005303986540577.435802BR5918Bruna Cansian Knop6009SAO PAULO61080540900062150511rolodemassa63042A3D'
  },
  {
    id: 11,
    title: 'Capacete a prova de rolo de massa',
    price: 100.00,
    image: Helmet,
    pixCode: '00020126580014BR.GOV.BCB.PIX0136e0ec7723-68aa-44d4-bb26-7102480094fe5204000053039865406100.005802BR5918Bruna Cansian Knop6009SAO PAULO61080540900062120508capacete630475FC'
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
      <div class="text-center text-[#C45824] max-w-7xl mx-auto py-6 px-4 sm:px-6 lg:px-8">
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
    <main class="max-w-7xl p-2 mx-auto py-6 sm:px-6 lg:px-8">
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