<script setup>
import { RouterView } from 'vue-router'
import NavBar from '@/components/NavBar.vue';
</script>

<template>
  <div class="bg">
    <div class="wrapper">
      <nav>
        <NavBar />
      </nav>
      <div class="contents">
        <RouterView />
      </div>
    </div>
  </div>
</template>

<style scoped>
</style>
