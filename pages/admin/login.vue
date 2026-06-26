<template>
  <div class="login-container">
    <div class="login-card">
      <h2>Admin Portal Login</h2>
      <p class="subtitle">Secure Staff Authentication Only</p>
      
      <form @submit.prevent="handleEmailLogin" class="login-form">
        <div class="form-group">
          <label for="email">Username or Email</label>
          <input 
            type="email" 
            id="email" 
            v-model="email" 
            placeholder="admin@example.com" 
            required 
            @blur="emailTouched = true"
            :class="{ 'input-error': emailError }"
            aria-describedby="email-error"
          />
          <p v-if="emailError" id="email-error" class="field-error">{{ emailError }}</p>
        </div>
        <div class="form-group">
          <label for="password">Password</label>
          <input 
            type="password" 
            id="password" 
            v-model="password" 
            placeholder="••••••••" 
            required 
            @blur="passwordTouched = true"
            :class="{ 'input-error': passwordError }"
            aria-describedby="password-error"
          />
          <p v-if="passwordError" id="password-error" class="field-error">{{ passwordError }}</p>
        </div>
        <button type="submit" class="btn-primary" :disabled="loading">
          <span v-if="loading" class="spinner"></span>
          {{ loading ? 'Signing In...' : 'Sign In with Credentials' }}
        </button>
      </form>

      <div class="divider">
        <span>OR</span>
      </div>

      <button @click="handleGoogleLogin" class="btn-google" :disabled="loading">
        <span v-if="loading" class="spinner"></span>
        <template v-else>
          <svg class="google-icon" viewBox="0 0 24 24" width="18" height="18">
            <path fill="#4285F4" d="M22.56 12.25c0-.78-.07-1.53-.2-2.25H12v4.26h5.92c-.26 1.37-1.04 2.53-2.21 3.31v2.77h3.57c2.08-1.92 3.28-4.74 3.28-8.09z"/>
            <path fill="#34A853" d="M12 23c2.97 0 5.46-.98 7.28-2.66l-3.57-2.77c-.98.66-2.23 1.06-3.71 1.06-2.86 0-5.29-1.93-6.16-4.53H2.18v2.84C3.99 20.53 7.7 23 12 23z"/>
            <path fill="#FBBC05" d="M5.84 14.09c-.22-.66-.35-1.36-.35-2.09s.13-1.43.35-2.09V7.06H2.18C1.43 8.55 1 10.22 1 12s.43 3.45 1.18 4.94l3.66-2.85z"/>
            <path fill="#EA4335" d="M12 5.38c1.62 0 3.06.56 4.21 1.64l3.15-3.15C17.45 2.09 14.97 1 12 1 7.7 1 3.99 3.47 2.18 7.06l3.66 2.85c.87-2.6 3.3-4.53 6.16-4.53z"/>
          </svg>
        </template>
        {{ loading ? 'Signing In...' : 'Sign In with Google Auth' }}
      </button>

      <p v-if="errorMessage" class="error-msg">{{ errorMessage }}</p>
      <p v-if="successMessage" class="success-msg">{{ successMessage }}</p>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const email = ref('')
const password = ref('')
const errorMessage = ref('')
const successMessage = ref('')
const loading = ref(false)
const emailTouched = ref(false)
const passwordTouched = ref(false)

const emailError = computed(() => {
  if (!emailTouched.value) return ''
  if (!email.value) return 'Email is required'
  const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/
  if (!emailRegex.test(email.value)) return 'Please enter a valid email address'
  return ''
})

const passwordError = computed(() => {
  if (!passwordTouched.value) return ''
  if (!password.value) return 'Password is required'
  if (password.value.length < 6) return 'Password must be at least 6 characters'
  return ''
})

const isFormValid = computed(() => {
  return email.value && password.value && !emailError.value && !passwordError.value
})

const handleEmailLogin = async () => {
  emailTouched.value = true
  passwordTouched.value = true
  
  if (!isFormValid.value) {
    errorMessage.value = 'Please fix the errors above'
    return
  }
  
  errorMessage.value = ''
  successMessage.value = ''
  loading.value = true
  
  try {
    // Mock authentication logic
    await new Promise(resolve => setTimeout(resolve, 1000))
    
    if (email.value === 'admin@example.com' && password.value === 'password') {
      successMessage.value = 'Login successful! Redirecting...'
      setTimeout(() => {
        navigateTo('/admin/dashboard')
      }, 1000)
    } else {
      errorMessage.value = 'Access denied. Standard member logins are blocked through this portal.'
    }
  } catch (error) {
    errorMessage.value = 'An error occurred. Please try again.'
  } finally {
    loading.value = false
  }
}

const handleGoogleLogin = async () => {
  errorMessage.value = ''
  successMessage.value = ''
  loading.value = true
  
  try {
    // Mock Google auth
    await new Promise(resolve => setTimeout(resolve, 1000))
    successMessage.value = 'Google Auth authorization successful! Redirecting...'
    setTimeout(() => {
      navigateTo('/admin/dashboard')
    }, 1000)
  } catch (error) {
    errorMessage.value = 'Google authentication failed. Please try again.'
  } finally {
    loading.value = false
  }
}

useHead({
  title: 'Admin Portal Login',
  meta: [
    { name: 'description', content: 'Secure staff-specific backend portal login.' }
  ]
})
</script>

<style scoped>
.login-container {
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  background-color: #f3f4f6;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  padding: 1rem;
}

.login-card {
  background: white;
  padding: 2.5rem;
  border-radius: 12px;
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
  width: 100%;
  max-width: 400px;
  text-align: center;
}

h2 {
  margin: 0 0 0.5rem 0;
  color: #111827;
  font-size: 1.5rem;
  font-weight: 700;
}

.subtitle {
  color: #6b7280;
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
  color: #374151;
  margin-bottom: 0.5rem;
}

input {
  width: 100%;
  padding: 0.75rem;
  border: 1px solid #d1d5db;
  border-radius: 6px;
  font-size: 0.875rem;
  box-sizing: border-box;
  transition: border-color 0.15s ease-in-out;
}

input:focus {
  outline: none;
  border-color: #2563eb;
  box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.15);
}

.btn-primary {
  width: 100%;
  padding: 0.75rem;
  background-color: #2563eb;
  color: white;
  border: none;
  border-radius: 6px;
  font-weight: 600;
  cursor: pointer;
  transition: background-color 0.15s ease-in-out;
  margin-top: 0.5rem;
}

.btn-primary:hover {
  background-color: #1d4ed8;
}

.divider {
  display: flex;
  align-items: center;
  text-align: center;
  color: #9ca3af;
  margin: 1.5rem 0;
  font-size: 0.75rem;
}

.divider::before,
.divider::after {
  content: '';
  flex: 1;
  border-bottom: 1px solid #e5e7eb;
}

.divider:not(:empty)::before {
  margin-right: .5em;
}

.divider:not(:empty)::after {
  margin-left: .5em;
}

.btn-google {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  padding: 0.75rem;
  background-color: white;
  color: #374151;
  border: 1px solid #d1d5db;
  border-radius: 6px;
  font-weight: 600;
  cursor: pointer;
  transition: background-color 0.15s ease-in-out;
}

.btn-google:hover {
  background-color: #f9fafb;
}

.google-icon {
  margin-right: 0.75rem;
}

.error-msg {
  color: #dc2626;
  font-size: 0.875rem;
  margin-top: 1.25rem;
  font-weight: 500;
}

.success-msg {
  color: #16a34a;
  font-size: 0.875rem;
  margin-top: 1.25rem;
  font-weight: 500;
}

.field-error {
  color: #dc2626;
  font-size: 0.75rem;
  margin-top: 0.25rem;
  font-weight: 500;
}

.input-error {
  border-color: #dc2626;
}

.input-error:focus {
  border-color: #dc2626;
  box-shadow: 0 0 0 3px rgba(220, 38, 38, 0.15);
}

.btn-primary:disabled,
.btn-google:disabled {
  opacity: 0.7;
  cursor: not-allowed;
}

.spinner {
  display: inline-block;
  width: 16px;
  height: 16px;
  border: 2px solid rgba(255, 255, 255, 0.3);
  border-radius: 50%;
  border-top-color: #fff;
  animation: spin 1s ease-in-out infinite;
  margin-right: 0.5rem;
}

.btn-google .spinner {
  border-color: rgba(55, 53, 47, 0.3);
  border-top-color: #374151;
}

@keyframes spin {
  to {
    transform: rotate(360deg);
  }
}
</style>
