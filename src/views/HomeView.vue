<template>
  <div class="container-fluid">
    <!-- <NavBar/> -->
    
      <section class="row" id="home">
        <HomeSection/>
      </section>
      <section class="row" id="about">
        <div class="container pt-5">
          <AboutSection :about="about" :hobbies="hobbies"/>
        </div>
      </section>
      <section class="row" id="resume">
        <resume-section/>
      </section>
      <section class="row" id="skills"></section>
      <section class="row" id="projects"></section>
      <section class="row" id="testimonials"></section>
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

export default {
  
  components: {
    HomeSection,
    AboutSection,
    ResumeSection
  }
}
</script>

<style>
</style>

