<script setup>
import { ref, watch } from 'vue'
import { Dialog, DialogPanel, DialogTitle, TransitionRoot, TransitionChild } from '@headlessui/vue'
import QRCodeVue3 from 'qrcode.vue'

const props = defineProps({
  isOpen: Boolean,
  gift: {
    type: Object,
    required: true
  }
})

const emit = defineEmits(['close'])

const copied = ref(false)

const copyPixCode = () => {
  if (props.gift) {
    navigator.clipboard.writeText(props.gift.pixCode)
    copied.value = true
    setTimeout(() => {
      copied.value = false
    }, 2000) // volta ao normal depois de 2 segundos
  }
}

// Resetar o botão sempre que abrir um novo modal
watch(() => props.gift, () => {
  copied.value = false
})
</script>

<template>
  <TransitionRoot appear :show="isOpen" as="template">
    <Dialog as="div" @close="emit('close')" class="relative z-10">
      <TransitionChild
        as="template"
        enter="duration-300 ease-out"
        enter-from="opacity-0"
        enter-to="opacity-100"
        leave="duration-200 ease-in"
        leave-from="opacity-100"
        leave-to="opacity-0"
      >
        <div class="fixed inset-0 bg-black bg-opacity-25" />
      </TransitionChild>

      <div class="fixed inset-0 overflow-y-auto">
        <div class="flex min-h-full items-center justify-center p-4">
          <TransitionChild
            as="template"
            enter="duration-300 ease-out"
            enter-from="opacity-0 scale-95"
            enter-to="opacity-100 scale-100"
            leave="duration-200 ease-in"
            leave-from="opacity-100 scale-100"
            leave-to="opacity-0 scale-95"
          >
            <DialogPanel class="w-full max-w-md transform overflow-hidden rounded-2xl bg-white p-6 text-left align-middle shadow-xl transition-all">
              <div v-if="gift">
                <DialogTitle as="h3" class="text-lg font-medium leading-6 text-gray-900">
                  {{ gift.title }}
                </DialogTitle>
                
                <div class="mt-4">
                  <div class="flex justify-center mb-4">
                    <QRCodeVue3
                      :value="gift.pixCode"
                      :size="200"
                      level="H"
                    />
                  </div>
                  
                  <div class="mt-4">
                    <p class="text-sm text-gray-500 mb-2">Valor: R$ {{ gift.price.toFixed(2) }}</p>
                    <div class="flex items-center gap-2">
                      <input
                        type="text"
                        :value="gift.pixCode"
                        readonly
                        class="flex-1 p-2 border rounded"
                      />
                      <button
                        @click="copyPixCode"
                        :class="[
                          'px-4 py-2 rounded',
                          copied ? 'bg-blue-300 text-white cursor-default' : 'bg-blue-600 text-white hover:bg-blue-700'
                        ]"
                        :disabled="copied"
                      >
                        {{ copied ? 'Copiado' : 'Copiar' }}
                      </button>
                    </div>
                  </div>

                  <p class="mt-4 text-sm text-gray-500">
                    Obrigado por contribuir com nosso sonho!
                  </p>
                </div>
              </div>

              <div class="mt-4 flex justify-end">
                <button
                  type="button"
                  class="inline-flex justify-center rounded-md border border-transparent bg-gray-100 px-4 py-2 text-sm font-medium text-gray-900 hover:bg-gray-200"
                  @click="emit('close')"
                >
                  Fechar
                </button>
              </div>
            </DialogPanel>
          </TransitionChild>
        </div>
      </div>
    </Dialog>
  </TransitionRoot>
</template>