<template>
  <section class="home-hero">
    <div class="hero-content">
      <p class="eyebrow">Welcome to AuthBase</p>
      <h1>Securely connect with confidence</h1>
      <p class="lead">
        A simple, beautifully crafted landing page that introduces visitors to the experience, and funnels them
        straight into the login or registration forms.
      </p>
      <div class="hero-actions">
        <button class="primary-btn" @click="navigate('/login')">Go to Login</button>
        <button class="secondary-btn" @click="navigate('/register')">Create an Account</button>
      </div>
    </div>
    <div class="hero-card">
      <p class="card-label">Why choose this flow?</p>
      <ul>
        <li>Seamless navigation powered by Vue Router.</li>
        <li>Accessible components and responsive layout.</li>
        <li>Form validation that keeps users informed in real time.</li>
      </ul>
    </div>
  </section>
</template>

<script setup>
import { useRouter } from 'vue-router';

const router = useRouter();
const navigate = (path) => router.push(path);
</script>

<style scoped>
.home-hero {
  display: grid;
  gap: 2rem;
  align-items: center;
}

.hero-content h1 {
  font-size: clamp(2.3rem, 4vw, 3.25rem);
  margin-bottom: 1rem;
}

.hero-actions {
  display: flex;
  flex-wrap: wrap;
  gap: 0.75rem;
  margin-top: 1.75rem;
}

.hero-card {
  background: rgba(255, 255, 255, 0.95);
  border-radius: 1rem;
  padding: 1.75rem;
  box-shadow: 0 15px 30px rgba(5, 10, 20, 0.15);
}

.hero-card ul {
  margin: 0.75rem 0 0;
  padding-left: 1.2rem;
  line-height: 1.7;
}

.card-label {
  text-transform: uppercase;
  font-size: 0.75rem;
  letter-spacing: 0.25em;
  color: #283593;
}

@media (min-width: 900px) {
  .home-hero {
    grid-template-columns: 2fr 1fr;
  }
}
</style>
