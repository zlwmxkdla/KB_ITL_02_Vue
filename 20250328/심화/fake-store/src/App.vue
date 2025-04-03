<script setup>
import { RouterLink, RouterView } from 'vue-router'
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'
import NavBar from './components/NavBar.vue'

</script>

<template>
  <header>
    <Header />
    <NavBar />
   
  </header>
  <RouterView />
    <Footer />
  
</template>
