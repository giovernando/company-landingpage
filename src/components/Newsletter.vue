<template>
  <section class="newsletter">
    <div class="container">
      <div class="newsletter-content">
        <div class="newsletter-text">
          <h2>Stay Updated</h2>
          <p>Subscribe to our newsletter for the latest insights, industry trends, and exclusive offers.</p>
          <div class="newsletter-features">
            <div class="feature">
              <span class="check-icon">✓</span>
              <span>Weekly industry insights</span>
            </div>
            <div class="feature">
              <span class="check-icon">✓</span>
              <span>Exclusive offers and discounts</span>
            </div>
            <div class="feature">
              <span class="check-icon">✓</span>
              <span>Early access to new services</span>
            </div>
          </div>
        </div>
        <div class="newsletter-form">
          <form @submit.prevent="handleSubmit" class="subscribe-form">
            <div class="form-group">
              <input
                v-model="email"
                type="email"
                placeholder="Enter your email address"
                required
                class="email-input"
                :class="{ 'error': emailError }"
              />
              <button type="submit" class="subscribe-btn" :disabled="isSubmitting">
                {{ isSubmitting ? 'Subscribing...' : 'Subscribe' }}
              </button>
            </div>
            <div v-if="emailError" class="error-message">{{ emailError }}</div>
            <div v-if="successMessage" class="success-message">{{ successMessage }}</div>
            <p class="privacy-text">
              We respect your privacy. Unsubscribe at any time.
            </p>
          </form>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const email = ref('')
const emailError = ref('')
const successMessage = ref('')
const isSubmitting = ref(false)

const validateEmail = (email) => {
  const re = /^[^\s@]+@[^\s@]+\.[^\s@]+$/
  return re.test(email)
}

const handleSubmit = async () => {
  emailError.value = ''
  successMessage.value = ''

  if (!validateEmail(email.value)) {
    emailError.value = 'Please enter a valid email address'
    return
  }

  isSubmitting.value = true

  // Simulate API call
  try {
    await new Promise(resolve => setTimeout(resolve, 1500))
    successMessage.value = 'Thank you for subscribing! Check your email for confirmation.'
    email.value = ''
  } catch (error) {
    emailError.value = 'Something went wrong. Please try again.'
  } finally {
    isSubmitting.value = false
  }
}
</script>

<style scoped>
.newsletter {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  padding: 80px 0;
}

.newsletter-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 60px;
  align-items: center;
}

.newsletter-text h2 {
  margin: 0 0 20px 0;
  font-size: 2.5rem;
  color: white;
}

.newsletter-text p {
  font-size: 1.1rem;
  margin-bottom: 30px;
  opacity: 0.9;
  line-height: 1.6;
}

.newsletter-features {
  display: flex;
  flex-direction: column;
  gap: 15px;
}

.feature {
  display: flex;
  align-items: center;
  gap: 10px;
}

.check-icon {
  color: #4ade80;
  font-weight: bold;
  font-size: 1.2rem;
}

.subscribe-form {
  background: white;
  padding: 40px;
  border-radius: 15px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
}

.form-group {
  display: flex;
  gap: 0;
  margin-bottom: 15px;
}

.email-input {
  flex: 1;
  padding: 15px 20px;
  border: 2px solid #e1e5e9;
  border-radius: 8px 0 0 8px;
  font-size: 1rem;
  transition: border-color 0.3s;
}

.email-input:focus {
  outline: none;
  border-color: #007bff;
}

.email-input.error {
  border-color: #dc3545;
}

.subscribe-btn {
  padding: 15px 30px;
  background: #007bff;
  color: white;
  border: none;
  border-radius: 0 8px 8px 0;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  transition: background-color 0.3s;
}

.subscribe-btn:hover:not(:disabled) {
  background: #0056b3;
}

.subscribe-btn:disabled {
  background: #6c757d;
  cursor: not-allowed;
}

.error-message {
  color: #dc3545;
  font-size: 0.9rem;
  margin-bottom: 10px;
}

.success-message {
  color: #28a745;
  font-size: 0.9rem;
  margin-bottom: 10px;
}

.privacy-text {
  font-size: 0.8rem;
  color: #6c757d;
  margin: 0;
  text-align: center;
}

@media (max-width: 768px) {
  .newsletter-content {
    grid-template-columns: 1fr;
    gap: 40px;
    text-align: center;
  }

  .newsletter-text h2 {
    font-size: 2rem;
  }

  .subscribe-form {
    padding: 30px 20px;
  }

  .form-group {
    flex-direction: column;
  }

  .email-input {
    border-radius: 8px;
    margin-bottom: 10px;
  }

  .subscribe-btn {
    border-radius: 8px;
  }
}
</style>
