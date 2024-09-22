<template>
    <div class="container">
        <div class="row pt-5">
            <h2 class="skills-heading headings">Skills</h2>
            <p class="subtext pt-5">"What I do have are a very particular set of skills..."</p>
        </div>
        <div class="row d-flex justify-content-center pt-5">
            <div class="col-md-4 col-sm-12 mb-4 d-flex justify-content-center">
                <div class="tech skill-divs">
                    <div class="skill-intro">

                        <h5 class="pb-4">Development Arsenal</h5>
                        <p>These are the technologies I am proficient in. With these in my locker, I'm able to build pixel-perfect functional websites.</p>
                    </div>
                    <div class="skills-grid tech-grid">
                        <div v-for="tech in skills" :key="tech.name" class="skill-item">
                            <img :src="tech.icon" alt="logo" loading="lazy" class="stack"> {{ tech.name }}
                        </div>
                    </div>
                </div>
            </div>
            <div class="col-md-4 col-sm-12 mb-4 d-flex justify-content-center">
                <div class="design skill-divs">
                    <div class="skill-intro">

                        <h5 class="pb-4">Design Tools</h5>
                        <p>I use these platforms to plan beautiful designs or create exciting content leading to satisfying, unique user experiences.</p>
                    </div>
                    <div class="skills-grid design-grid">
                        <div v-for="tool in designSkills" :key="tool.name" class="skill-item">
                            <img :src="tool.icon" alt="logo" loading="lazy"> {{ tool.name }}
                        </div>
                    </div>
                </div>
            </div>
            <div class="col-md-4 col-sm-12 mb-4 d-flex justify-content-center">
                <div class="soft skill-divs">
                    <div class="skill-intro">

                        <h5 class="pb-4">Soft Skills</h5>
                        <p>The underrated "soft" skills. Without these, my technical expertise would only take me so far.</p>
                    </div>
                    <div class="skills-grid soft-grid">
                        <div v-for="skill in softSkills" :key="skill.name" class="skill-item">
                            {{ skill.name }}
                        </div>
                    </div>
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
            return this.$store.state.skills;
        },
        designSkills() {
            return this.$store.state.designSkills;
        },
        softSkills() {
            return this.$store.state.softSkills;
        }
    },
    mounted() {
        this.$store.dispatch("getSkills");
        this.$store.dispatch("getDesignSkills");
        this.$store.dispatch("getSoftSkills");
    }
};
</script>

<style scoped>
.subtext {
    text-align: center;
}

.stack {
    width: 40px;
    border: none;
    border-radius: 0;
}

.container {
    flex-wrap: wrap;
}

.skills-heading {
    color: #ff005e;
    text-shadow: 2px 2px 4px #000, 5px 5px 70px rgba(251, 255, 0);
}

.row {
    width: 85%;
    margin: 0 auto;
}

.skill-divs {
    position: relative;
    padding: 20px;
    background-color: #000;
    /* border-radius: 8px; */
    width: 100%;
    height: 100%;
    display: flex;
    color: #fff;
    flex-direction: column;
}

/* .box {

    width: 300px;
    height: 300px;
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 40px;
    background: #000;
    transition: 0.5s;
} */

.skill-divs::before {
    content: '';
    position: absolute;
    top: -2px;
    left: -2px;
    right: -2px;
    bottom: -2px;
    /* background: #fff; */
    z-index: -1;
    
}

.skill-divs::after {
    content: '';
    position: absolute;
    top: -2px;
    left: -2px;
    right: -2px;
    bottom: -2px;
    /* background: #fff; */
    z-index: -2;
    filter: blur(20px);
    
}

.skill-divs::before,
.skill-divs::after {
    background: linear-gradient(235deg, #ff005e, #010615, #fbff00) !important;
    
}

.skill-intro {
    height: 13rem;
}

.skills-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr); 
    gap: 10px; 
    text-align: left;
    margin: 0 10px;
    padding-bottom: 0 !important;
    
}

.skill-item {
    display: flex;
    align-items: center;
}

img {
    width: 40px;
    border-radius: 50%;
    margin-right: 10px;
}



@media (max-width: 1365px) {

    .skills-grid{
        margin-top: 5.5rem;
    }

    .soft-grid{
        grid-template-columns: repeat(1, 1fr); 
    }

    .skill-item {
        flex-direction: column;
        text-align: center;
    }

    .skill-item img {
        margin-bottom: 10px;
    }

    .skill-intro {
    height: 10rem;
}
}

@media (max-width: 1065px) {

    .col-md-4 {
        flex: 0 0 100%; /* Make each skill section take up the full width */
        max-width: 80%;
    }

    .skills-grid{
        margin-top: 3.5rem;
    }

    .soft-grid{
        grid-template-columns: repeat(1, 1fr); 
    }

    /* .skill-item {
        flex-direction: column;
        text-align: center;
    } */

    /* .skill-item img {
        margin-bottom: 10px;
    } */

    .skill-intro {
    height: 10rem;
}


}

@media (min-width: 765px) and (max-width: 990px) {
    .col-md-4 {
        flex: 0 0 100%; /* Make each skill section take up the full width */
        max-width: 100%;
    }

    .skill-divs {
        margin-bottom: 2rem;
    }

    .skills-grid {
        grid-template-columns: repeat(2, 1fr); /* Ensure the skills are still in 2 columns */
        margin-top: 3rem;
        margin-left: 7rem;
    }

    .skill-item {
        flex-direction: row;
        text-align: left;
    }

    .skill-item img {
        margin-bottom: 0;
        margin-right: 10px;
    }

    .skill-intro {
        height: 10rem;
    }
}





@media (max-width: 765px) {


    .soft-grid{
        grid-template-columns: repeat(1, 1fr); 
        margin-left: 0 !important;
    }

    .skill-item {
        flex-direction: column;
        text-align: center;
    }

    .skill-item img {
        margin-bottom: 10px;
    }

    .skill-intro {
    height: 10rem;
}
}


@media (max-width: 475px) {

    .row {
    width: 100%;
    margin: 0 auto;
}

    .soft-grid{
        grid-template-columns: repeat(1, 1fr); 
    }

    .skill-item {
        flex-direction: column;
        text-align: center;
        scale: 0.8;
    }

    .skill-item img {
        margin-bottom: 10px;
    }

    .skill-intro {
    height: 10rem;
    }

    .skills-grid{
        margin-top: 2.5rem;
    }

    /* .skills-grid{
        grid-template-columns: repeat(1, 1fr); 
        margin-top: 3.5rem;
    } */


}

/* @media (max-width: 365px) {

} */

@media (max-width: 365px) {
    .row {
    width: 100%;
    margin: 0 auto;
}
    /* .skills-grid{
        grid-template-columns: repeat(1, 1fr); 
        margin-top: 5.8rem;
    } */

    .soft-grid{
        margin-top: 3.5rem !important;
    }
}

@media (max-width: 355px) {
    .row {
    width: 100%;
    margin: 0 auto;
}
    .skills-grid{
        grid-template-columns: repeat(1, 1fr); 
        margin-top: 5.8rem;
    }
}

@media (max-width: 330px) {
    .row {
    width: 100%;
    margin: 0 auto;
}
    .soft-grid{
        margin-top: 3.5rem !important;
        margin-right: 3rem !important;
        margin-left: -1rem !important;
    }

    .skill-item {
        flex-direction: column;
        text-align: center;
        scale: 0.8;
        width: 100%;
    }

    .skill-intro h5 {
        width: 100%;
        word-wrap: break-word;
    }
}



</style>
