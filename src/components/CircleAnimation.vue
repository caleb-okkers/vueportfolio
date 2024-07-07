<template>
    <div class="animation-container">
      <div v-for="index in 20" :key="index" class="circle"></div>
    </div>
  </template>
  
  <script>
  import { nextTick } from 'vue';
  
  export default {
    name: 'CircleAnimation',
    mounted() {
      nextTick(() => {
        const coords = { x: 0, y: 0 };
        const circles = this.$el.querySelectorAll(".circle");
  
        const colors = [
  "#00FFFF", // cyan
  "#00F0FF",
  
  "#00C5CD", // turquoise
  "#00B8B8",
  "#00ACAC",
  "#009B9B",
  "#008B8B",
  "#007A7A",
  "#006A6A",
  "#005959",
  "#004848",
  "#003838",
  "#002727",
  "#001616",
  "#000505",
  "#000000", //black
  "#000000", 
  "#000000", 
  "#000000", 
  "#000000", 
  "#000000", 
        ];
  
        circles.forEach((circle, index) => {
          circle.x = 0;
          circle.y = 0;
          circle.style.backgroundColor = colors[index % colors.length];
        });
  
        window.addEventListener("mousemove", (e) => {
          coords.x = e.clientX;
          coords.y = e.clientY;
        });
  
        const animateCircles = () => {
          let x = coords.x;
          let y = coords.y;
  
          circles.forEach((circle, index) => {
            circle.style.left = `${x - 12}px`;
            circle.style.top = `${y - 12}px`;
            circle.style.transform = `scale(${(circles.length - index) / circles.length})`;
  
            circle.x = x;
            circle.y = y;
  
            const nextCircle = circles[index + 1] || circles[0];
            x += (nextCircle.x - x) * 0.3;
            y += (nextCircle.y - y) * 0.3;
          });
  
          requestAnimationFrame(animateCircles);
        };
  
        animateCircles();
      });
    }
  };
  </script>
  
  <style scoped>
  .animation-container {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    pointer-events: none;
    z-index: 99999999;
  }
  
  .circle {
    position: absolute;
    height: 24px;
    width: 24px;
    border-radius: 50%;
    background-color: black;
    pointer-events: none;
  }
  </style>