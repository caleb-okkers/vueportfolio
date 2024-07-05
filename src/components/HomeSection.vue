<template>
  <div class="container">
    <video autoplay loop muted playsinline class="video-background" id="bgVideo">
      <source src="https://videos.pexels.com/video-files/3129671/3129671-uhd_2560_1440_30fps.mp4" type="video/mp4">
      Your browser does not support the video tag.
      
    </video>
    <div class="row d-flex justify-content-center">
      <div class="content">
        <h1 class="text pt-3">Caleb Okkers</h1>
        <h3 v-if="title" class="title">
          <span>{{ title }}</span>
        </h3>
        <Spinner v-else />
        <div class="home-image">
          <img src="https://github.com/caleb-okkers/coolCards/blob/master/images/IMG_2711onetooneratio.jpg?raw=true" alt="Caleb Okkers" loading="lazy">
        </div>
      </div>

    </div>

  </div>

</template>

<script>
import Spinner from '@/components/Spinner.vue'
import { computed, onMounted, ref } from 'vue'
import { useStore } from 'vuex'

export default {
  name: 'HomeSection',
  components: {
    Spinner
  },
  setup() {
    const store = useStore()
    const jobTitle = computed(() => store.state.jobTitle)
    const title = ref('')
    const cnt = ref(0)

    function repeat() {
      try {
        if (cnt.value == jobTitle.value?.length) cnt.value = 0
        title.value = jobTitle.value?.at(cnt.value)?.title
        setTimeout(repeat, 2000)
        cnt.value++
      } catch (e) {
        // Handle error
      }
    }

    onMounted(() => {
      store.dispatch('getJobTitle')
      repeat()
    })

    return {
      title
    }
  }
}

// const video = document.getElementById('bgVideo');
//         video.addEventListener('ended', () => {
//             video.currentTime = 0;
//             video.play();
//         });
</script>

<style scoped>

.video-background {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100vh;
    object-fit: cover;
    /* z-index: -1; */
    transform: translateZ(-1px) scale(2);
}

#home {
    position: relative;
    
    min-height: 100vh;
    transform-style: preserve-3d;
    
}

#home::before {
    width: 100%;
    height: 100%;
    background-size: cover;
    
}

#home .content {
    position: absolute;
    text-align: center;
    color: #000;
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 50vw;
}


#home .text {
    font-family: "Orbitron", monospace;
    font-optical-sizing: auto;
    font-style: normal;
    font-size: 4rem;
    /* text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.3), 5px 5px 70px rgba(255, 255, 255, 0.5); */
    text-shadow: 2px 2px 4px cyan, 5px 5px 70px rgba(255, 255, 255, 0.5);
    
}

#home .title {
    font-family: "JetBrains Mono", monospace;
    font-optical-sizing: auto;
    font-style: normal;
    font-size: 1.8rem;
    text-shadow: 2px 2px 4px cyan, 5px 5px 70px rgba(255, 255, 255, 0.5);
}

#home .home-image img {
    width: 400px;
    height: auto;
    /* margin-top: 20px; */
    /* border-radius: 10%; */
    padding: 10px;
    opacity: 0.85;
}

.home-image {
    position: relative;
    width: 400px;
    height: 400px;
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 10px;
    transition: 0.5s;
    background: #000;
    box-sizing: border-box;
}

.home-image::before {
    content: '';
    position: absolute;
    top: -2px;
    left: -2px;
    right: -2px;
    bottom: -2px;
    background: #fff;
    z-index: -1;

}

.home-image::after {
    content: '';
    position: absolute;
    top: -2px;
    left: -2px;
    right: -2px;
    bottom: -2px;
    background: #fff;
    z-index: -2;
    filter: blur(40px);

}

.home-image .profile {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    padding: 10px;
    box-sizing: border-box;
    overflow: hidden;
}

.home-image .profile img {
    max-width: 100%;
    /* opacity: 0.4; */
    transition: 0.5s;
    overflow: hidden;
}

.home-image::before,
.home-image::after {
    background: linear-gradient(235deg, cyan, #050505, cyan);
}


</style>

