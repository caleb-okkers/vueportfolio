<template>
    <div class="container" id="experience-section">
      <div class="row pt-5">
        <h2 class="exp-heading headings">Experience</h2>
      </div>
      <div class="row">
        <div class="col d-flex justify-content-center">
          <div class="timeline">
            <div v-for="(i, index) in work" :key="index" :class="['timeline-container', index % 2 === 0 ? 'left-container' : 'right-container']">
              <img :src=i.image alt="logo"  loading="lazy">
              <div class="text-box">
                <h2>{{ i.company }}</h2>
                <small>{{ i.position }}</small>
                <small>{{ i.year }}</small>
                <p>{{ i.description }}</p>
                <span :class="[index % 2 === 0 ? 'left-container-arrow' : 'right-container-arrow']"></span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'ExperienceComp',
    computed: { 
      work() {
        return this.$store.state.work
      }
  },
    mounted() {
    this.$store.dispatch('getWork')

    // Intersection Observer setup
    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          document.querySelectorAll('.timeline-container').forEach((el, index) => {
            console.log(`Animating element with index: ${index}`); // Use index here
            el.style.animationPlayState = 'running';
          });
          observer.unobserve(entry.target); // Stop observing once animation has started
        }
      });
    }, { threshold: 0.1 }); // Trigger when 10% of the section is in view
    
    observer.observe(this.$el);
  }
  }
  </script>
  
  <style scoped>
  @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap');

  .exp-heading {
  color: #89ff00;
  text-shadow: 2px 2px 4px #000, 5px 5px 70px #00bcd4;
}
  
  .timeline {
    position: relative;
    max-width: 1200px;
    margin: 100px auto;
    /* animation: movedown 2s linear forwards; */
  
  }
  
  /* .timeline::before {
    content: '';
    position: absolute;
    top: 0;
    bottom: 0;
    width: 2px;
    
    left: 50%;
    margin-left: -1px;
  } */
  
  .timeline::after {
    content: '';
    position: absolute;
    width: 2px;
    height: 100%;
    /* background: linear-gradient(235deg, #B8860B, #010615, #B8860B); */
    background: #fff;
    top: 0;
    left: 50%;
    margin-left: -3px;
    z-index: 1;
    animation: moveline 6s linear forwards;
  }
  
  @keyframes moveline {
    0% { 
      height: 0;
    }
    100% {
      height: 100%;
    }
  }
  
  .timeline-container {
    padding: 10px 40px;
    position: relative;
    width: 50%;
    box-sizing: border-box;
    opacity: 0;
    animation: movedown 1s linear forwards;
    animation-play-state: paused;
    z-index: 5;
    
  }
  
  @keyframes movedown {
    0% {
      opacity: 0;
      transform: translateY(-30px);
    }
    100% {
      opacity: 1;
      transform: translateY(0px);
    }
  }
  .timeline-container:nth-child(1){
    animation-delay: 0s;
  }
  
  .timeline-container:nth-child(2){
    animation-delay: 1.5s;
  }
  
  .timeline-container:nth-child(3){
    animation-delay: 2.5s;
  }
  
  .timeline-container:nth-child(4){
    animation-delay: 3.5s;
  }
  
  .timeline-container.left-container {
    left: -50%;
  }
  
  .timeline-container.right-container {
    left: 50%;
  }
  
  .timeline-container img {
      position: absolute;
      width: 40px;
      border-radius: 50%;
      right: -20px;
      top: 32px;
      z-index: 10;
      border: 2px solid #fff;
    }
  
    .right-container img {
      left: -20px;
    }
  
    .left-container img {
      left: 460px;
    }
  
    .text-box {
    padding: 20px 30px;
    background: #000;
    position: relative;
    border-radius: 6px;
    font-size: 15px;
    color: #fff;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
    font-family: 'Poppins', sans-serif;
    border: 3px solid;
    border-image-slice: 1;
    border-width: 3px;
    border-image-source:  linear-gradient(235deg, #89ff00, #b6b2b2, #89ff00);
    width: 400px;
    box-shadow: 0 0 10px #00bcd4;
  }


  .text-box:hover {

transition: 0.5s;
transform: scale(1.03);
}

  .text-box::before,
.text-box::after {
    content: '';
    position: absolute;
    width: 20px;
    height: 20px;
    background: rgba(0, 0, 0, 0.5);
    filter: blur(40px);
}

.text-box::before {
    left: -10px;
    bottom: -10px;
}

.text-box::after {
    right: -10px;
    top: -10px;
}
  
  
  .text-box h2 {
    font-weight: 600;
    font-size: 22px;
  }
  
  .text-box small {
    display: block;
    margin-bottom: 15px;
  }
  
  .left-container-arrow {
    height: 0;
    width: 0;
    position: absolute;
    top: 28px;
    z-index: 1;
    border-top: 15px solid transparent;
    border-bottom: 15px solid transparent;
    border-left: 15px solid #89ff00;
    right: -15px;
  }
  
  .right-container-arrow {
    height: 0;
    width: 0;
    position: absolute;
    top: 28px;
    z-index: 1;
    border-top: 15px solid transparent;
    border-bottom: 15px solid transparent;
    border-right: 15px solid #89ff00;
    left: -15px;
  }
 
  
  @media screen and (max-width: 600px) {
    .timeline::before {
      left: 31px;
    }
  
    .timeline-container {
      width: 100%;
      padding-left: 70px;
      padding-right: 25px;
    }
  
    .text-box {
      font-size: 13px;
    }
  
    .right-container {
      left: 0%;
    }
  
    .timeline-container img {
      left: 10px;
    }
  
    .left-container-arrow,
    .right-container-arrow {
      border-right: 15px solid #000;
      border-left: 0;
      left: -15px;
    }
  }
  </style>