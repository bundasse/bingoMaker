<script setup>
import { RouterLink, RouterView } from 'vue-router'
import NavBar from '@/components/NavBar.vue';
</script>

<template>
  <header>
    <div class="wrapper">
      <nav>
        <NavBar />
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/make">빙고 만들기</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}
</style>
