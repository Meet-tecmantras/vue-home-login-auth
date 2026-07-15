<template>
  <section class="form-section">
    <div class="form-card">
      <div class="form-heading">
        <h2>Create your account</h2>
        <p>Start with a secure, validated registration flow.</p>
      </div>
      <form @submit.prevent="handleSubmit">
        <label class="form-group">
          <span>Email</span>
          <input v-model="form.email" type="email" placeholder="you@example.com" />
          <span v-if="errors.email" class="error-message">{{ errors.email }}</span>
        </label>
        <label class="form-group">
          <span>Password</span>
          <input v-model="form.password" type="password" placeholder="Choose a strong password" />
          <span v-if="errors.password" class="error-message">{{ errors.password }}</span>
        </label>
        <label class="form-group">
          <span>Confirm Password</span>
          <input v-model="form.confirmPassword" type="password" placeholder="Repeat password" />
          <span v-if="errors.confirmPassword" class="error-message">{{ errors.confirmPassword }}</span>
        </label>
        <button class="primary-btn" type="submit" :disabled="submitting">{{ submitting ? 'Creating account…' : 'Register' }}</button>
        <p v-if="message" class="success-message">{{ message }}</p>
      </form>
      <p class="helper-text">
        Already registered?
        <router-link to="/login" class="link">Log in instead</router-link>
      </p>
    </div>
  </section>
</template>

<script setup>
import { reactive, ref } from 'vue';
import { useRouter } from 'vue-router';

const form = reactive({
  email: '',
  password: '',
  confirmPassword: ''
});

const errors = reactive({
  email: '',
  password: '',
  confirmPassword: ''
});

const submitting = ref(false);
const message = ref('');
const router = useRouter();

const resetErrors = () => {
  errors.email = '';
  errors.password = '';
  errors.confirmPassword = '';
  message.value = '';
};

const validate = () => {
  resetErrors();
  if (!form.email) {
    errors.email = 'Email is required.';
  } else if (!form.email.includes('@')) {
    errors.email = 'Please enter a valid email address.';
  }

  if (!form.password) {
    errors.password = 'Password is required.';
  } else if (form.password.length < 6) {
    errors.password = 'Password must be at least 6 characters.';
  }

  if (!form.confirmPassword) {
    errors.confirmPassword = 'Please confirm your password.';
  } else if (form.confirmPassword !== form.password) {
    errors.confirmPassword = 'Passwords do not match.';
  }

  return !errors.email && !errors.password && !errors.confirmPassword;
};

const handleSubmit = () => {
  if (!validate()) {
    return;
  }
  submitting.value = true;
  message.value = '';

  setTimeout(() => {
    submitting.value = false;
    message.value = 'Account created successfully!';
    form.email = '';
    form.password = '';
    form.confirmPassword = '';
    router.push('/');
  }, 900);
};
</script>

<style scoped>
.form-section {
  display: flex;
  justify-content: center;
  align-items: center;
}

.form-card {
  width: min(500px, 100%);
  background: rgba(255, 255, 255, 0.95);
  border-radius: 1.25rem;
  padding: 2rem;
  box-shadow: 0 18px 30px rgba(7, 12, 20, 0.18);
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 0.35rem;
  margin-top: 1rem;
}

.form-group input {
  border: 1px solid rgba(9, 30, 70, 0.2);
  border-radius: 0.65rem;
  padding: 0.85rem 1rem;
  font-size: 1rem;
}

.error-message {
  color: #c62828;
  font-size: 0.85rem;
}

.helper-text {
  margin-top: 1rem;
  font-size: 0.95rem;
}

.link {
  color: #283593;
  text-decoration: underline;
}

.success-message {
  margin-top: 1rem;
  color: #1b5e20;
}

button.primary-btn {
  width: 100%;
  margin-top: 1.5rem;
}
</style>
