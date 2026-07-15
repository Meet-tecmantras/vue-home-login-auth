<template>
  <nav class="top-nav">
    <div class="brand">
      <router-link to="/">AuthBase</router-link>
    </div>
    <div class="nav-links">
      <router-link to="/" class="nav-link" :class="{ active: isActive('/') }">Home</router-link>
      <router-link to="/login" class="nav-link" :class="{ active: isActive('/login') }">Login</router-link>
      <router-link to="/register" class="nav-link" :class="{ active: isActive('/register') }">Register</router-link>
    </div>
  </nav>
</template>

<script setup>
import { useRoute } from 'vue-router';

const route = useRoute();

const isActive = (path) => route.path === path;
</script>

<style scoped>
.top-nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem 1.5rem;
  background: rgba(19, 57, 106, 0.95);
  color: #fff;
  position: sticky;
  top: 0;
  z-index: 10;
  box-shadow: 0 10px 25px rgba(12, 21, 45, 0.25);
}

.brand a {
  font-weight: 700;
  letter-spacing: 0.08em;
  color: #fff;
  font-size: 1.1rem;
}

.nav-links {
  display: flex;
  gap: 1rem;
}

.nav-link {
  color: rgba(255, 255, 255, 0.8);
  text-decoration: none;
  font-weight: 500;
  padding-bottom: 0.25rem;
  border-bottom: 2px solid transparent;
  transition: color 0.2s ease, border-color 0.2s ease;
}

.nav-link.active,
.nav-link:hover {
  border-color: #f9ca24;
  color: #fff;
}

@media (max-width: 640px) {
  .nav-links {
    gap: 0.5rem;
  }
}
</style>
