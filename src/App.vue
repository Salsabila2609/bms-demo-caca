<script setup>
import { RouterLink, RouterView } from 'vue-router'
import Navbar from './components/Navbar.vue';
</script>

<template>
  <header>
      <Navbar />
  </header>
  <RouterView />
</template>

<style>
.router-link-active {
  @apply bg-gray-900 text-white hover:text-white hover:bg-gray-900
}
</style>