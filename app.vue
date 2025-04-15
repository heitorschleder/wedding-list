<script setup>
import DarkSoulsImage from '@/assets/images/darksouls.png'
import PanelaImage from '@/assets/images/panela.png'
import CobertaImage from '@/assets/images/coberta.png'
// adicionar a fonte que a bruna quis @import url('https://fonts.googleapis.com/css2?family=Pinyon+Script&display=swap');
// .pinyon-script-regular {
//   font-family: "Pinyon Script", cursive;
//   font-weight: 400;
//   font-style: normal;
// }

const gifts = ref([
  {
    id: 1,
    title: 'Edredom para noiva que esta sempre coberta de razão',
    price: 599.90,
    image: CobertaImage,
    pixCode: '00020126670014BR.GOV.BCB.PIX0126heitorschleder33@gmail.com0215cafeteira teste52040000530398654040.015802BR5925Heitor de Oliveira Schled6009SAO PAULO62140510br7dCaacm16304338B'
  },
  {
    id: 2,
    title: 'DarkSouls III pro noivo não se estressar com a noiva',
    price: 299.90,
    image: DarkSoulsImage,
    pixCode: 'FAZOPIXPRABRUNA'
  },
  {
    id: 3,
    title: 'Panela de pressão "inexplodível" pros noivos não se matarem',
    price: 459.90,
    image: PanelaImage,
    pixCode: 'pixcode789'
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
  <div class="min-h-screen bg-gray-50">
    <header class="bg-white shadow">
      <div class="text-center max-w-7xl mx-auto py-6 px-4 sm:px-6 lg:px-8">
        <h1 class="text-3xl font-bold text-gray-900">
          Lista de Presentes de Heitor e Bruna
        </h1>
        <p class="mt-2 text-gray-600">
          Agradecemos seu carinho! Escolha um presente abaixo.
        </p>
      </div>
    </header>

    <main class="max-w-7xl mx-auto py-6 sm:px-6 lg:px-8">
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
        <GiftCard
          v-for="gift in gifts"
          :key="gift.id"
          :gift="gift"
          @click="openGiftModal(gift)"
        />
      </div>

      <GiftModal
        v-if="isModalOpen"
        :is-open="isModalOpen"
        :gift="selectedGift"
        @close="closeGiftModal"
      />
    </main>
  </div>
</template>