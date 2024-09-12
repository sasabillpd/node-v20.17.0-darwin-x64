<template>
  <div id="app">
    <div class="content">
      <!-- Click Counter with inline style binding -->
      <h1 :style="{ color: 'black', fontSize: '24px', fontWeight: 'bold' }">Click Counter</h1>
      <button class="btn" @click="incrementCounter">Clicked {{ counter }} times</button>

      <!-- Box Color Changer -->
      <h1 :style="{ color: 'black', fontSize: '24px', fontWeight: 'bold' }">Box Color Changer</h1>
      <div :style="boxStyle" class="color-box"></div>
      <button class="btn" @click="changeColor">Change Box Color</button>

      <!-- Image Carousel -->
      <h1 :style="{ color: 'black', fontSize: '24px', fontWeight: 'bold' }">Image Carousel</h1>
      <div class="carousel">
        <img :src="images[currentImage]" alt="carousel image" class="carousel-image" />
        <div class="carousel-controls">
          <button class="btn" @click="prevImage">Previous</button>
          <button class="btn" @click="nextImage">Next</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

// Click Counter
const counter = ref(0)
const incrementCounter = () => {
  counter.value++
}

// Box Color Changer
const colors = ['#ffc0cb', '#FAD6A5', '#E3D8F1', '#F5F5DC', '#D3D3D3', '#C4E1C1', '#F6C1C1', '#D6B7E3', '#A2C2E8', '#A8D5BA', '#F7E5A3']
const currentColorIndex = ref(0)
const changeColor = () => {
  currentColorIndex.value = (currentColorIndex.value + 1) % colors.length
}
const boxStyle = computed(() => ({
  width: '200px',
  height: '200px',
  backgroundColor: colors[currentColorIndex.value],
  borderRadius: '10px',
  boxShadow: '0 4px 8px rgba(0, 0, 0, 0.1)'
}))

// Image Carousel
const images = [
  'src/assets/image/image1.jpeg',
  'src/assets/image/image2.jpeg',
  'src/assets/image/image3.jpeg',
  'src/assets/image/image4.jpeg',
  'src/assets/image/image5.jpeg',
  'src/assets/image/image6.jpeg',
  'src/assets/image/image7.jpeg',
  'src/assets/image/image8.jpeg'
]
const currentImage = ref(0)
const prevImage = () => {
  currentImage.value = (currentImage.value - 1 + images.length) % images.length
}
const nextImage = () => {
  currentImage.value = (currentImage.value + 1) % images.length
}
</script>

<style src="src/assets/styles.css"></style>
