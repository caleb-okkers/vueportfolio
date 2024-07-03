<template>
    <div class="container">
      <div class="row pt-5" v-for="info in about" :key="info.name">
        <div class="col">
          <div class="info">
            <h2 class="text">{{ info.name }}</h2>
            <p class="par">{{ info.text }}</p>
          </div>
        </div>
      </div>
      <div class="hobbies pt-5">
        <Card v-for="hobby in hobbies" :key="hobby.name">
        <template #img>
           <img :src= hobby.image alt="">
        </template>
        <template #content>
          <h5>{{ hobby.name }}</h5>
          <p>{{ hobby.text }}</p>
        </template>
      </Card>
  
      </div>
    </div>
  </template>
  
  <script>
  import Card from '@/components/Card.vue'
  
  export default {
    name: "AboutSection",
    components: {
      Card
    },
    computed: { 
      about() {
        return this.$store.state.aboutMe
      },
      hobbies() {
        return this.$store.state.hobbies
    }
  },
    mounted() {
    this.$store.dispatch('getAboutMe'),
    this.$store.dispatch('getHobbies')
  }

    }

  
  </script>
  
  <style>
  </style>