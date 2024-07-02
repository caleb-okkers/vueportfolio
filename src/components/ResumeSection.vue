<template>
    <div class="timeline">
      <div v-for="(item, index) in education" :key="index" :class="['timeline-container', index % 2 === 0 ? 'left' : 'right']">
          

                <div class="content">
                  <h2>{{ item.institution }}</h2>
                  <p>{{ item.qualification }}</p>
                  <p>{{ item.year }}</p>
              
            </div>
        </div>
    </div>
  </template>
  
  <script>
  
  export default {
    name: 'ResumeSection',
    props: {
      education: {
        type: Array,
        required: true
      }
    }
  }
  </script>
  
  <style scoped>
  
  .timeline {
  position: relative;
  max-width: 1200px;
  margin: 0 auto;
  padding: 40px 0;
  color: #B8860B;
}

.timeline::after {
  content: '';
  position: absolute;
  width: 1px;
  background-color: #B8860B; /* Set the line background color */
  top: 0;
  bottom: 0;
  left: 50%;
  margin-left: -0.5px;
  z-index: 2; /* Ensure the line is above other elements */
}

.timeline::before {
  content: '';
  position: absolute;
  width: 10px; /* Adjust the width to accommodate the border */
  top: 0;
  bottom: 0;
  left: 50%;
  margin-left: -5px; /* Half the width to center the border */
  background: #B8860B;
  border-radius: 3px;
  z-index: 1;
}

.timeline-container {
  padding: 10px 40px;
  position: relative;
  background-color: inherit;
  width: 50%;
  z-index: 3; /* Ensure containers are above the timeline */
}

.timeline-container.left {
  left: -50%;
}

.timeline-container.right {
  left: 50%;
}

.timeline-container::before {
  content: '';
  position: absolute;
  top: 0;
  left: 15%;
  right: 0;
  bottom: 0;
  border-radius: 6px;
  padding: 2px; /* Adjust the padding to set the border width */
  background: linear-gradient(235deg, #B8860B, #050505, #B8860B);
  -webkit-mask: 
    linear-gradient(#fff 0 0) content-box, 
    linear-gradient(#fff 0 0);
  -webkit-mask-composite: xor; 
          mask-composite: exclude; 
  z-index: 1;
  min-width: 400px;
}

.timeline-container::after {
  content: ' ';
  position: absolute;
  width: 25px;
  height: 25px;
  right: -17px;
  background-color: #B8860B;
  border: 4px solid #B8860B;
  top: 15px;
  border-radius: 50%;
  z-index: 4; /* Ensure the circle is above everything else */
}

.timeline-container.right::after {
  left: -16px;
}

.content {
  padding: 20px 30px;
  background-color: #000;
  position: relative;
  border-radius: 6px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.1);
  z-index: 5; /* Ensure content is above the timeline container */
  min-width: 390px
}

.timeline-container.left .content {
  left: 0;
}

.timeline-container.right .content {
  left: 0;
}

.content h2 {
  font-family: Poppins;
  font-size: 22px;
}

.content p {
  font-family: Poppins;
  font-size: 16px;
}

  </style>