<script setup>
import {ref} from 'vue'

const images = ref([
  // List of image urls
  'https://cdn.pixabay.com/photo/2023/06/27/10/51/man-8091933_1280.jpg',
  'https://cdn.pixabay.com/photo/2023/04/10/06/32/tulip-7912886_1280.jpg',
  'https://cdn.pixabay.com/photo/2023/07/03/08/05/turkey-8103602_1280.jpg',
])

let currentImage = ref(0)

const nextImage = () => {
  currentImage.value = (currentImage.value + 1) % images.value.length
}

const previousImage = () => {
  currentImage.value = (currentImage.value - 1 + images.value.length) % images.value.length
}
</script>

<template>
  <div class="max-w-3xl mx-auto flex flex-col justify-center h-screen">
    <div id="controls-carousel" class="relative flex items-center justify-center min-h-screen">
      <div v-for="(image, index) in images" :key="index" class="absolute w-full transition-opacity duration-700 ease-in-out" :class="{'opacity-0': currentImage !== index, 'opacity-100': currentImage === index}">
        <img :src="image" class="w-full h-96 rounded-lg" alt="...">
      </div>
    <!-- Slider controls -->
    <button  @click="previousImage" type="button" class="absolute top-0 left-0 z-30 flex items-center justify-center h-full px-4 cursor-pointer group focus:outline-none">
        <span class="inline-flex items-center justify-center w-10 h-10 rounded-full bg-white/30 bg-white-800/30 group-hover:bg-white/50 group-hover:bg-white-800/60 group-focus:ring-4 group-focus:ring-white group-focus:ring-white-800/70 group-focus:outline-none">
            <svg class="w-4 h-4 text-white" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 6 10">
                <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 1 1 5l4 4"/>
            </svg>
            <span class="sr-only">Previous</span>
        </span>
    </button>
    <button @click="nextImage" type="button" class="absolute top-0 right-0 z-30 flex items-center justify-center h-full px-4 cursor-pointer group focus:outline-none">
        <span class="inline-flex items-center justify-center w-10 h-10 rounded-full bg-white/30 bg-white-800/30 group-hover:bg-white/50 group-hover:bg-white-800/60 group-focus:ring-4 group-focus:ring-white group-focus:ring-white-800/70 group-focus:outline-none">
            <svg class="w-4 h-4 text-white" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 6 10">
                <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="m1 9 4-4-4-4"/>
            </svg>
            <span class="sr-only">Next</span>
        </span>
    </button>
  </div>
</div>
</template>

<style scoped>
</style>