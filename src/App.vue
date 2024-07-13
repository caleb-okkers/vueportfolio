<template>
  <div class="wrapper">
    <NavBar/>
    <main>
      <router-view/>
    </main>
    <CircleAnimation/>
    <Footer/>
  </div>
  
</template>



<script>
import NavBar from '@/components/NavBar.vue'
import Footer from '@/components/Footer.vue'
import CircleAnimation from './components/CircleAnimation.vue';

export default {
  
  components: {
    NavBar,
    Footer,
    CircleAnimation
  }
}
</script>

<style src="@/assets/css/styles.css">
</style>
