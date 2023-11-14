<script setup>
import Header from './components/Header.vue'
import Hero from './components/Hero.vue'
import About from './components/About.vue'
</script>

<template>
  <div class="wrapper">
    <Header />
    <Hero />
    <About />
  </div>
</template>

<style scoped>
.wrapper {
  width: 100%;
  height: 100%;
}

/* Media Query */
@media screen and (max-width: 1180px) {
  .wrapper {
    max-width: 840px;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    position: relative;
  }
}
</style>
