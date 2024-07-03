<template>
  <div>
    <Education/>
    <Experience/>
  </div>
</template>

<script>
import Experience from './ExperienceComp.vue'
import Education from './EducationComp.vue'

export default {
  name: 'ResumeSection',
  components: {
    Experience,
    Education
  }
}
</script>

<style scoped>

</style>