<template>
  <div class="container" id="education-section">
    <div class="education-section" v-if="education && education.length">
      <h2 class="edu-heading headings">Education</h2>
      <p class="subtext">I believe that knowledge is power ... but wisdom is how to use it.</p>


        <div class="education-list">
          <ul class="education-tabs">
            <li
              v-for="(edu, index) in education"
              :key="edu.institution"
              :class="{ active: selectedEduIndex === index }"
              @click="selectEdu(index)"
            >
              <img :src="edu.image" alt="institution logo" class="institution-logo"> 
              {{ edu.institution }}
            </li>
          </ul>
  
          <div class="education-details justify-content-center align-content-center">
            <h3>
               <span>{{ education[selectedEduIndex].institution }}</span>
            </h3>
            <p class="education-duration">{{ education[selectedEduIndex].year }}</p>
            <!-- <p>{{ education[selectedEduIndex].description }}</p> -->
             <p>{{ education[selectedEduIndex].qualification}}</p>
          </div>
        </div>

    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      selectedEduIndex: 0, // Default selected education item
    };
  },
  computed: {
    education() {
      return this.$store.state.education; // Fetch education data from the Vuex store
    },
  },
  mounted() {
    this.$store.dispatch("getEducation"); // Dispatch action to fetch education data
  },
  methods: {
    selectEdu(index) {
      this.selectedEduIndex = index; // Set the selected education index
    },
  },
};
</script>

<style scoped>
.education-section {
  margin: 0 auto;
  max-width: 1000px;
  padding: 50px 0;
}

.edu-heading {
  color: #89ff00;
  text-shadow: 2px 2px 4px #000, 5px 5px 70px #00bcd4;
  margin-bottom: 3rem;
}

/* .section-heading {
  text-align: center;
  font-size: 2.5rem;
  color: #ff005e;
  margin-bottom: 20px;
} */

.subtext {
  text-align: center;
  margin-bottom: 40px;
}

.education-list {
  position: relative;
  display: flex;
  justify-content: space-between;
}




.education-tabs {
  list-style: none;
  padding: 0;
  width: 30%;
  display: flex;
  flex-direction: column;
}

.education-tabs li {
  padding: 15px;
  cursor: pointer;
  color: #666;
  border-left: 2px solid transparent;
  display: flex;
  align-items: center;
  transition: all 0.3s ease;
  font-weight: 200;
  font-family: "JetBrains Mono", monospace;
}

.education-tabs li.active {
  color: #89ff00;
  border-left: 2px solid #89ff00;
}

.institution-logo {
  width: 30px;
  height: 30px;
  margin-right: 10px;
}

.education-details {
  width: 65%;
}

.education-details h3 {
  font-size: 1.75rem;
  color: #89ff00;
  font-family: "Poppins";
}

.education-details .education-duration {
  font-size: 1rem;
  margin-bottom: 20px;
}

/* .education-details p {
  font-size: 1.1rem;
} */

@media (max-width:475px) {
    .education-tabs {
    width: 50%;
    display: flex;
    flex-direction: column;
  }

  .education-tabs li {
  align-items: left;
  text-align: left;
  font-size: 12px;
}

.education-details  {
    color: #333;
    text-align: left;
    padding-left: 2rem ;
  }

.education-details h3 {
  font-size: 1.2rem;
}
}

.institution-logo {
  width: 30px;
  height: 30px;
  margin-right: 10px;
  filter: grayscale(100%);
  transition: filter 0.3s ease;
}

.education-tabs li.active .institution-logo {
  filter: none;
}
</style>
