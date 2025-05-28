<script setup>
import { useHead } from '#imports'

const props = defineProps({
  title: {
    type: String,
    default: 'Lista de Presentes'
  },
  description: {
    type: String,
    default: 'Essa é a nossa lista de presentes de casamento — fique à vontade pra escolher com carinho!'
  },
  image: {
    type: String,
    default: '~/public/logohb.jpg'
  },
  url: {
    type:String,
    default: 'https://wedding-list-phi.vercel.app'
  }
})

useHead({
  title: props.title,
  meta: [
    { name: 'description', content: props.description },
    { property: 'og:title', content: props.title },
    { property: 'og:description', content: props.description },
    { property: 'og:image', content: props.image },
    { property: 'og:url', content: props.url },
    { name: 'twitter:card', content: 'summary_large_image' },
    { name: 'viewport', content: 'width=device-width, initial-scale=1' },
  ],
})
</script>
