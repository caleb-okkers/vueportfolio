<template>
    <div class="container">
        <h2 class="text">Skills</h2>
        <div class="row d-flex justify-content-center pt-5">
            <div class="col d-flex justify-content-center">
                <div class="tech">
                    <h4 class="pb-4">Development Arsenal</h4>
                    <p v-for="tech in skills" :key="tech.name"><span><i :class="['fa-brands', tech.icon]"></i></span> {{ tech.name }}</p>
                </div>
            </div>
            <div class="col d-flex justify-content-center">
                <div class="design">
                    <h4 class="pb-4">Design Tools</h4>
                    <p v-for="tool in designSkills" :key="tool.name"><span><img :src=tool.icon alt=""></span> {{ tool.name }}</p>
                </div>
            </div>
            <div class="col d-flex justify-content-center">
                <div class="soft">
                    <h4 class="pb-4">Soft Skills</h4>
                    <p v-for="skill in softSkills" :key="skill.name">{{ skill.name }}</p>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: "SkillsSection",
    computed: {
        skills() {
            return this.$store.state.skills
        },
        designSkills() {
            return this.$store.state.designSkills
        },
        softSkills() {
            return this.$store.state.softSkills
        }
    },
    mounted() {
        this.$store.dispatch('getSkills'),
        this.$store.dispatch('getDesignSkills')
        this.$store.dispatch('getSoftSkills')
    }
}
</script>
<style scoped>

    .row {
        width: 60%;
        margin: 0 auto;
    }
    
    img {
      width: 40px;
      border-radius: 50%;
      border: 2px solid #fff;
    }

     i {
  margin-right: 10px;
  font-size: 40px;
}

    p, h4 {
        text-align: left;
    }

    h4 {
    color: #fff;
    font-family: "JetBrains Mono", monospace;
    font-optical-sizing: auto;
    font-weight: 500;
    font-style: normal;
    font-size: 1.5rem;
    /* text-shadow: 2px 2px 5px #DAA520, 5px 5px 70px rgba(255, 255, 255, 0.3); */
    }
</style>