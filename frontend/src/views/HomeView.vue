<template>
  <div class="carousel">
    <div class="image-wrapper" :style="{ transform: 'translateX(' + (-currentImage * 100) + '%)' }">
      <img v-for="(image, index) in images" :key="index" :src="image" :alt="'Slide ' + (index + 1)">
    </div>
    <div class="controls">
      <button @click="prevImage">Prev</button>
      <button @click="nextImage">Next</button>
    </div>
    <div class="position-indicator">
      {{ currentImage + 1 }} / {{ images.length }}
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      images: [
        'https://i.postimg.cc/y60yxcq1/1320x600-Asrock-sale-min-1320x600.jpg',
        'https://i.postimg.cc/1XyBs33c/1320x600-g-ALAX-new-min-1320x600.jpg',
        'https://i.postimg.cc/KztbCJ13/1320x600-AMD-Last-Of-Us-min-1320x600-1.jpg'
      ],
      currentImage: 0,
      interval: null,
      transitionDuration: 1000
    };
  },
  mounted() {
    this.interval = setInterval(() => {
      this.nextImage();
    }, 5000);
  },
  beforeUnmount() {
    clearInterval(this.interval);
  },
  methods: {
    prevImage() {
      this.currentImage = (this.currentImage === 0) ? (this.images.length - 1) : (this.currentImage - 1);
    },
    nextImage() {
      this.currentImage = (this.currentImage + 1) % this.images.length;
    }
  }
};
</script>

<style>
.carousel {
  position: relative;
  width: 100%;
  height: 500px;
  overflow: hidden;
}
.image-wrapper {
  display: flex;
  transition: transform 1s ease-in-out;
}
.image-wrapper img {
  flex-shrink: 0;
  max-width: 100%;
  max-height: 100%;
  object-fit: cover;
}
.controls {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  display: flex;
  justify-content: space-between;
  width: 100%;
  padding: 0 20px;
  box-sizing: border-box;
}
.controls button {
  padding: 10px;
  font-size: 16px;
  background: none;
  border: 1px solid #ccc;
  border-radius: 5px;
  cursor: pointer;
}
.position-indicator {
  position: absolute;
  bottom: 20px;
  left: 50%;
  transform: translateX(-50%);
  font-size: 14px;
}
</style>





