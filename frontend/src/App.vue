<template>
  <div class="app-shell">
    <NavBar />
    <main class="view-wrapper">
      <router-view />
    </main>
  </div>
</template>

<script setup>
import NavBar from './components/NavBar.vue';
</script>

<style scoped>
.app-shell {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

.view-wrapper {
  flex: 1;
  padding: 2rem 1.25rem 3rem;
}

@media (min-width: 1024px) {
  .view-wrapper {
    padding: 3rem 4rem 4rem;
  }
}
</style>
