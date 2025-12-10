<script setup lang="ts">
import Header from './components/Header.vue';
import Discover from './components/Discover.vue'; 
import Services from './components/Services.vue';
import Parallax from './components/Parallax.vue';
import Card from './components/Card.vue';
import Footer from './components/Footer.vue';
</script>

<template>
  <div id="app">
    <Header />
    <Discover />
    <Services />
    <Parallax />
    <Card />
    <Footer />
  </div>
</template>

<style scoped>
#app {
	position: relative;
	min-height: 100vh;
    overflow-x: hidden;
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
