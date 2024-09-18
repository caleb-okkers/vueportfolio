<template>
    <div class="container" id="experience-section">
      <div class="experience-section" v-if="work && work.length">
    <h2 class="section-heading headings">Work Experience</h2>
    <p class="subtext">It's not about the destination ... it's about the experience.</p>
    
    <div class="job-list">
      <ul class="job-tabs">
        <li
          v-for="(job, index) in work"
          :key="job.company"
          :class="{ active: selectedJobIndex === index }"
          @click="selectJob(index)"
        >
          <img :src="job.image" alt="company logo" class="company-logo"> {{ job.company }}
        </li>
      </ul>

      <div class="job-details justify-content-center align-content-center">
        <h3>
          {{ work[selectedJobIndex].position }} <span>@ {{ work[selectedJobIndex].company }}</span>
        </h3>
        <p class="job-duration">{{ work[selectedJobIndex].year }}</p>
        <p>{{ work[selectedJobIndex].description }}</p>
      </div>
    </div>
  </div>
  </div>


  </template>
  <script>
  export default {
    data() {
      return {
        selectedJobIndex: 0
      };
    },
    computed: {
      work() {
        return this.$store.state.work;
      }
    },
    mounted() {
      this.$store.dispatch("getWork");
    },
    methods: {
      selectJob(index) {
        this.selectedJobIndex = index;
      }
    }
  };
  </script>
  
  <style scoped>
  .experience-section {
    margin: 0 auto;
    max-width: 1000px;
    padding: 50px 0;
  }
  
  .section-heading {
    margin-bottom: 3rem;
    color: #89ff00;
    text-shadow: 2px 2px 4px #000, 5px 5px 70px #00bcd4;
    margin-bottom: 3rem;
  }
  
  .subtext {
    text-align: center;
    font-size: 1.2rem;
    margin-bottom: 40px;
    color: #666;
  }
  
  .job-list {
    display: flex;
    justify-content: space-between;
  }
  
  .job-tabs {
    list-style: none;
    padding: 0;
    width: 30%;
    display: flex;
    flex-direction: column;
  }
  
  .job-tabs li {
    padding: 15px;
    cursor: pointer;
    font-size: 1.1rem;
    color: #666;
    border-left: 2px solid transparent;
    display: flex;
    align-items: center;
    transition: all 0.3s ease;
  }
  
  .job-tabs li.active {
    color: #89ff00;
    border-left: 2px solid #89ff00;
  }
  

  .company-logo {
    width: 30px;
    height: 30px;
    margin-right: 10px;
  }
  

  .job-details {
    width: 65%;
  }
  
  .job-details h3 {
    font-size: 1.75rem;
    color: #89ff00;
  }
  
  .job-details .job-duration {
    font-size: 1rem;
    color: #666;
    margin-bottom: 20px;
  }
  
  .job-details p {
    font-size: 1.1rem;
    color: #333;
  }

  @media (max-width:475px) {
    .job-tabs {
    width: 50%;
    display: flex;
    flex-direction: column;
  }

  .job-tabs li {
  align-items: left;
  text-align: left;
  font-size: 12px;
}

.job-details  {
    color: #333;
    text-align: left;
    padding-left: 2rem ;
  }

  .job-details h3  {
    font-size: 1.2rem;
  }

}

.company-logo {
  width: 30px;
  height: 30px;
  margin-right: 10px;
  filter: grayscale(100%);
  transition: filter 0.3s ease;
}

.job-tabs li.active .company-logo {
  filter: none;
}
  </style>
