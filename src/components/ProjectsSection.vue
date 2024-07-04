<template>
    <div class="container">
        <div class="row">
            <h2 class="text">Projects</h2>
            <p class="subtext">Have a look at some of my projects...</p>
        </div>
        <div class="row">
            <div class="col col-md-6 col-sm-12">
                <Card v-for="project in projects " :key="project.name">
                    <template #img>
                        <img :src= project.image alt="">
                    </template>
                    <template #content>
                        <h5>{{ project.name }}</h5>
                        <p>{{ project.description }}</p>
                        <span>
                            <i class="fa-brands fa-github"></i>
                            <img src="" alt="">
                        </span>
                    </template>
        
                </Card>
            </div>
        </div>
    </div>
</template>
<script>
import Card from './Card.vue'

export default {
    name: "ProjectsSection",
    components: {
        Card
    }
}
</script>
<style lang="">
    
</style>