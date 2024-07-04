<template>
  <div class="container-fluid">
    <!-- <NavBar/> -->
    
      <section class="row" id="home">
        <HomeSection/>
      </section>
      <section class="row" id="about">
          <AboutSection :about="about" :hobbies="hobbies"/>
        
      </section>
      <section class="row" id="resume">
        <ResumeSection/>
      </section>
      <section class="row" id="skills">
        <SkillsSection/>
      </section>
      <section class="row" id="projects">
        <ProjectsSection/>
      </section>
      <section class="row" id="testimonials">
        <TestimonialsSection/>
      </section>
      <section class="row" id="contact"></section>
    
    <!-- <Footer/> -->
  </div>
</template>

<script>
// import NavBar from '@/components/NavBar.vue'
// import Footer from '@/components/Footer.vue'
import HomeSection from '@/components/HomeSection.vue'
import AboutSection from '@/components/AboutSection.vue'
import ResumeSection from '@/components/ResumeSection.vue'
import SkillsSection from '@/components/SkillsSection.vue'
import ProjectsSection from '@/components/ProjectsSection.vue'
import TestimonialsSection from '@/components/TestimonialsSection.vue'

export default {
  
  components: {
    HomeSection,
    AboutSection,
    ResumeSection,
    SkillsSection,
    ProjectsSection,
    TestimonialsSection
  }
}
</script>

<style>
</style>

