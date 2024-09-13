<template>
  <div id="app">
    <!-- Click Counter -->
    <div>
      <button @click="incrementCounter">Click me!</button>
      <p>Count: {{ counter }}</p>
    </div>

    <!-- Box Color Change -->
    <div>
      <button @click="changeColor">Change Box Color</button>
      <div :style="{ backgroundColor: boxColor }" class="box"></div>
    </div>

    <!-- Image Carousel -->
    <div class="carousel-section">
      <div class="carousel">
        <img :src="imagess[currentImageIndex]" alt="carousel image" class="carousel-image" />
        <div class="carousel-buttons">
          <button @click="prevImage">Previous</button>
          <button @click="nextImage">Next</button>
        </div>
      </div>
    </div>

  </div> 
</template>
<script>
// Import foto dari assets
import photo1 from '@/assets/3x4 1 N.jpg';
import photo2 from '@/assets/logo.png';
import photo3 from '@/assets/tom.jpg';

export default {
  data() {
    return {
      counter: 0,
      boxColor: 'lightblue',
      colors: ['lightblue', 'lightgreen', 'lightcoral', 'lightyellow'],
      currentIndex: 0,
      images: [
        'https://via.placeholder.com/600x300?text=Image+1',
        'https://via.placeholder.com/600x300?text=Image+2',
        'https://via.placeholder.com/600x300?text=Image+3',
      ],
      // Image Carousel state
      imagess: [photo1, photo2, photo3], // gunakan foto yang diimpor
      currentImageIndex: 0,
    };
  },
  methods: {
    incrementCounter() {
      this.counter++;
    },
    changeColor() {
      const randomIndex = Math.floor(Math.random() * this.colors.length);
      this.boxColor = this.colors[randomIndex];
    },
    // Carousel functions
    prevImage() {
      this.currentImageIndex =
        (this.currentImageIndex - 1 + this.imagess.length) % this.imagess.length;
    },
    nextImage() {
      this.currentImageIndex = (this.currentImageIndex + 1) % this.imagess.length;
    },
  }
};
</script>

<style scoped>
.box {
  width: 100px;
  height: 100px;
  margin: 10px;
  border: 1px solid #000;
}
.carousel {
  width: 100%;
  overflow: hidden;
  position: relative;
}
.carousel-images {
  display: flex;
  transition: transform 0.5s ease-in-out;
}
.carousel-images img {
  width: 100%;
  height: auto;
}
</style>