<template>
  <div class="login-container">
    <div class="login-card">
      <h2>Reception Portal Login</h2>
      <p class="subtitle">Secure Desk Agent Access Only</p>
      
      <form @submit.prevent="handleLogin" class="login-form">
        <div class="form-group">
          <label for="username">Receptionist ID/Email</label>
          <input 
            type="email" 
            id="username" 
            v-model="email" 
            placeholder="reception@gym.com" 
            required 
          />
        </div>
        <div class="form-group">
          <label for="password">Password</label>
          <input 
            type="password" 
            id="password" 
            v-model="password" 
            placeholder="••••••••" 
            required 
          />
        </div>
        <button type="submit" class="btn-primary">Sign In</button>
      </form>

      <p v-if="errorMessage" class="error-msg">{{ errorMessage }}</p>
      <p v-if="successMessage" class="success-msg">{{ successMessage }}</p>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const email = ref('')
const password = ref('')
const errorMessage = ref('')
const successMessage = ref('')

const handleLogin = () => {
  errorMessage.value = ''
  successMessage.value = ''

  if (email.value === 'reception@gym.com' && password.value === 'password') {
    successMessage.value = 'Authorized. Welcome to desk dashboards.'
  } else {
    errorMessage.value = 'Access denied. General members blocked.'
  }
}

useHead({
  title: 'Reception Login',
  meta: [
    { name: 'description', content: 'Secure desk receptionist login portal.' }
  ]
})
</script>

<style scoped>
.login-container {
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  background-color: #f0fdf4;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  padding: 1rem;
}

.login-card {
  background: white;
  padding: 2.5rem;
  border-radius: 12px;
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
  width: 100%;
  max-width: 400px;
  text-align: center;
  border-top: 4px solid #10b981;
}

h2 {
  margin: 0 0 0.5rem 0;
  color: #064e3b;
  font-size: 1.5rem;
  font-weight: 700;
}

.subtitle {
  color: #047857;
  font-size: 0.875rem;
  margin-bottom: 2rem;
}

.login-form {
  text-align: left;
}

.form-group {
  margin-bottom: 1.25rem;
}

label {
  display: block;
  font-size: 0.875rem;
  font-weight: 500;
  color: #065f46;
  margin-bottom: 0.5rem;
}

input {
  width: 100%;
  padding: 0.75rem;
  border: 1px solid #a7f3d0;
  border-radius: 6px;
  font-size: 0.875rem;
  box-sizing: border-box;
}

input:focus {
  outline: none;
  border-color: #10b981;
  box-shadow: 0 0 0 3px rgba(16, 185, 129, 0.15);
}

.btn-primary {
  width: 100%;
  padding: 0.75rem;
  background-color: #10b981;
  color: white;
  border: none;
  border-radius: 6px;
  font-weight: 600;
  cursor: pointer;
  transition: background-color 0.15s ease-in-out;
}

.btn-primary:hover {
  background-color: #059669;
}

.error-msg {
  color: #dc2626;
  font-size: 0.875rem;
  margin-top: 1.25rem;
}

.success-msg {
  color: #059669;
  font-size: 0.875rem;
  margin-top: 1.25rem;
}
</style>
