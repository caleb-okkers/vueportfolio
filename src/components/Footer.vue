<!-- <template>
    <footer class="container-fluid">
        <div class="row">
            <p class="lead">Caleb Okkers &copy; <span class="shadow">{{ cYear }}</span></p>
        </div>
    </footer>
</template>
<script>
export default {
    name: "FooterComp",
    data() {
        return {
            cYear: new Date().getUTCFullYear()
        }
    }
}
</script>
<style scoped>
    
</style> -->

<template>
  <footer class="container-fluid">

    <div class="row pt-3">
      <p class="lead text-center w-100">
        Caleb Okkers &copy; <span>{{ cYear }}</span>
      </p>
    </div>
  </footer>
</template>
  
  <script>
export default {
  name: "FooterComp",
  data() {
    return {
      cYear: new Date().getUTCFullYear(),
    };
  },
};
</script>
  
  <style scoped>
footer {
  /* color: var(--primary-light);
    background: var(--primary-dark); */
  /* font-family: "Bona Nova SC", serif;
    font-weight: 500;
    font-style: normal;
    font-size: 1rem; */
  bottom: 0;
  z-index: 1;
}

footer p,
footer a {
  /* color: var(--primary-light); */
  color: #fff;
  text-decoration: none;
}

footer ul {
  list-style: none;
  padding: 0;
}

footer ul li a:hover {
  /* color: var(--primary); */
  color: #fff;
}

footer .row {
  margin: 0;
}

footer .lead {
  padding-top: 1rem;
}

svg {
  width: 2rem;
  padding: 0.3rem;
  margin-left: 1.5rem;
  margin-right: 1.5rem;
}
</style>