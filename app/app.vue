<script setup lang="ts">
import Header from './components/Header.vue';
import Discover from './components/Discover.vue'; 
import Parallax from './components/Parallax.vue';
import Services from './components/Services.vue';
import Banner from './components/Banner.vue';
import Avis from './components/Avis.vue';   
import Faq from './components/Faq.vue';
import Banner2 from './components/Banner2.vue';
import Footer from './components/Footer.vue';
</script>

<template>
  <div id="app">
    <Header />
    <Discover />
    <Services />
    <Parallax />
    <Banner />
    <Avis />
    <Faq />
    <Banner2 />
    <Footer />
  </div>
</template>

<style scoped>
#app {
	position: relative;
	min-height: 100vh;
}

*, *::before, *::after {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}

html, body {
    overflow-x: hidden;
    width: 100%;
}
</style>
