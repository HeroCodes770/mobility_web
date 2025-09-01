<template>
  <img 
    :src="imageSrc" 
    :alt="alt" 
    :loading="loading"
    :style="style"
    @error="onImageError"
  />
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
  src: {
    type: String,
    required: true
  },
  alt: {
    type: String,
    default: ''
  },
  loading: {
    type: String,
    default: 'lazy'
  },
  style: {
    type: [String, Object],
    default: ''
  }
})

// Convert the src to the correct public path
const imageSrc = computed(() => {
  if (props.src.startsWith('/media/')) {
    return props.src
  }
  return `/media/${props.src}`
})

const onImageError = (event) => {
  console.warn('Image failed to load:', event.target.src)
  // Optionally set a fallback image
  // event.target.src = '/media/fallback.jpg'
}
</script>
