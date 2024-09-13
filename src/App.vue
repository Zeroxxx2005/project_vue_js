<template>
  <div id="app">
    <!-- Main Title -->
    <header class="main-title">
      <h1>Travel B</h1>
    </header>

    <!-- Click Counter Section -->
    <div class="section click-counter">
      <h2>Destination Click Counter</h2>
      <button @click="incrementCounter" class="btn">Explore More!</button>
      <p class="count-text">You've visited {{ clickCount }} amazing places.</p>
    </div>

    <!-- Box Color Changer Section -->
    <div class="section color-changer">
      <h2>Travel Theme Color Changer</h2>
      <button @click="changeColor" class="btn">Change Theme Color</button>
      <div :style="{ backgroundColor: boxColor }" class="color-box"></div>
    </div>

    <!-- Image Carousel Section -->
    <div class="section carousel">
      <h2>Popular Destinations</h2>
      <div class="carousel-controls">
        <button @click="prevImage" class="btn">Previous</button>
      </div>
      <div class="carousel-image-container">
        <img :src="images[currentImageIndex]" alt="Travel destination" class="carousel-image">
      </div>
      <div class="carousel-controls">
        <button @click="nextImage" class="btn">Next</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      // Data for Click Counter
      clickCount: 0,
      
      // Data for Box Color Changer
      boxColor: 'skyblue',
      colors: ['skyblue', 'lightseagreen', 'tomato', 'goldenrod'],
      
      // Data for Image Carousel
      currentImageIndex: 0,
      images: [
        'https://i.pinimg.com/originals/31/78/a3/3178a32f9b8a48a770eddba7bafcc28c.jpg',  
        'https://i.pinimg.com/originals/97/06/ba/9706bab1a46ad6db7fa8a3a953c356d3.png', 
        'https://i.pinimg.com/originals/a4/3a/0f/a43a0f38ec32974e41e7eda36d1467e1.jpg'    
      ]
    }
  },
  methods: {
    // Method to increment click counter
    incrementCounter() {
      this.clickCount++;
    },
    // Method to change the box color
    changeColor() {
      const randomIndex = Math.floor(Math.random() * this.colors.length);
      this.boxColor = this.colors[randomIndex];
    },
    // Method to show previous image in carousel
    prevImage() {
      this.currentImageIndex = (this.currentImageIndex - 1 + this.images.length) % this.images.length;
    },
    // Method to show next image in carousel
    nextImage() {
      this.currentImageIndex = (this.currentImageIndex + 1) % this.images.length;
    }
  }
}
</script>

<style>
/* Global Styles */
#app {
  font-family: 'Roboto', sans-serif; /* Modern font for a clean look */
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #fff; /* Text color to contrast with background */
  margin: 0;
  padding: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  background: #00bfae; /* Beachy teal background color */
}

/* Section Styles */
.section {
  background: #fff;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  padding: 20px;
  margin: 20px;
  width: 90%;
  max-width: 600px;
}

/* Headings */
h2 {
  margin-bottom: 20px;
  font-size: 26px;
  color: #333; /* Dark gray color for headings */
}

/* Button Styles */
button {
  margin: 10px;
  padding: 10px 20px;
  font-size: 18px;
  cursor: pointer;
  background-color: #00bfae; /* Teal for buttons */
  color: #fff;
  border: none;
  border-radius: 4px;
  transition: background-color 0.3s, transform 0.2s;
}

button:hover {
  background-color: #008e8f; /* Darker teal for hover */
  transform: scale(1.05);
}

/* Click Counter Text */
.count-text {
  font-size: 20px;
  color: #555; /* Medium gray for text */
}

/* Box Color Styles */
.color-box {
  width: 120px;
  height: 120px;
  margin: 20px auto;
  border-radius: 8px;
  transition: background-color 0.5s ease;
}

/* Carousel Styles */
.carousel {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.carousel-controls {
  display: flex;
  justify-content: center;
  margin: 10px;
}

.carousel-image-container {
  margin: 20px;
}

.carousel-image {
  width: 350px;
  height: 250px;
  border-radius: 8px;
  object-fit: cover;
}
</style>
