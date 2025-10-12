<template>
  <section id="contact" class="contact">
    <div class="container">
      <h2>Contact Us</h2>
      <div class="contact-content">
        <div class="contact-info">
          <div class="info-item">
            <h3>Address</h3>
            <p>123 Business Street<br>City, State 12345</p>
          </div>
          <div class="info-item">
            <h3>Phone</h3>
            <p>(555) 123-4567</p>
          </div>
          <div class="info-item">
            <h3>Email</h3>
            <p>info@company.com</p>
          </div>
        </div>
        <form @submit.prevent="handleSubmit" class="contact-form">
          <div class="form-group">
            <input
              v-model="form.name"
              type="text"
              placeholder="Your Name *"
              required
              :class="{ 'error': errors.name }"
            >
            <span v-if="errors.name" class="error-text">{{ errors.name }}</span>
          </div>
          <div class="form-group">
            <input
              v-model="form.email"
              type="email"
              placeholder="Your Email *"
              required
              :class="{ 'error': errors.email }"
            >
            <span v-if="errors.email" class="error-text">{{ errors.email }}</span>
          </div>
          <div class="form-group">
            <input
              v-model="form.subject"
              type="text"
              placeholder="Subject *"
              required
              :class="{ 'error': errors.subject }"
            >
            <span v-if="errors.subject" class="error-text">{{ errors.subject }}</span>
          </div>
          <div class="form-group">
            <textarea
              v-model="form.message"
              placeholder="Your Message *"
              rows="5"
              required
              :class="{ 'error': errors.message }"
            ></textarea>
            <span v-if="errors.message" class="error-text">{{ errors.message }}</span>
          </div>
          <button type="submit" class="submit-button" :disabled="isSubmitting">
            {{ isSubmitting ? 'Sending...' : 'Send Message' }}
          </button>
          <div v-if="successMessage" class="success-message">{{ successMessage }}</div>
        </form>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const form = ref({
  name: '',
  email: '',
  subject: '',
  message: ''
})

const errors = ref({})
const isSubmitting = ref(false)
const successMessage = ref('')

const validateForm = () => {
  errors.value = {}

  if (!form.value.name.trim()) {
    errors.value.name = 'Name is required'
  }

  if (!form.value.email.trim()) {
    errors.value.email = 'Email is required'
  } else if (!/\S+@\S+\.\S+/.test(form.value.email)) {
    errors.value.email = 'Please enter a valid email'
  }

  if (!form.value.subject.trim()) {
    errors.value.subject = 'Subject is required'
  }

  if (!form.value.message.trim()) {
    errors.value.message = 'Message is required'
  }

  return Object.keys(errors.value).length === 0
}

const handleSubmit = async () => {
  if (!validateForm()) return

  isSubmitting.value = true
  successMessage.value = ''

  try {
    // Simulate API call
    await new Promise(resolve => setTimeout(resolve, 2000))
    successMessage.value = 'Thank you for your message! We\'ll get back to you within 24 hours.'
    form.value = { name: '', email: '', subject: '', message: '' }
  } catch (error) {
    errors.value.general = 'Something went wrong. Please try again.'
  } finally {
    isSubmitting.value = false
  }
}
</script>

<style scoped>
.contact {
  padding: 100px 0;
  background-color: #f8f9fa;
}

.contact h2 {
  text-align: center;
  font-size: 36px;
  margin-bottom: 60px;
  color: #333;
}

.contact-content {
  display: flex;
  gap: 60px;
  align-items: flex-start;
}

.contact-info {
  flex: 1;
}

.info-item {
  margin-bottom: 30px;
}

.info-item h3 {
  font-size: 20px;
  margin-bottom: 10px;
  color: #333;
}

.info-item p {
  color: #666;
  line-height: 1.6;
}

.contact-form {
  flex: 1;
}

.form-group {
  margin-bottom: 20px;
}

input, textarea {
  width: 100%;
  padding: 12px;
  border: 1px solid #ddd;
  border-radius: 5px;
  font-size: 16px;
  font-family: inherit;
  transition: border-color 0.3s;
}

input:focus, textarea:focus {
  outline: none;
  border-color: #007bff;
}

input.error, textarea.error {
  border-color: #dc3545;
}

.error-text {
  color: #dc3545;
  font-size: 0.9rem;
  margin-top: 5px;
  display: block;
}

.success-message {
  color: #28a745;
  font-size: 0.9rem;
  margin-top: 15px;
  text-align: center;
}

textarea {
  resize: vertical;
}

.submit-button {
  background-color: #007bff;
  color: white;
  border: none;
  padding: 12px 30px;
  border-radius: 5px;
  font-size: 16px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.submit-button:hover:not(:disabled) {
  background-color: #0056b3;
}

.submit-button:disabled {
  background-color: #6c757d;
  cursor: not-allowed;
}

@media (max-width: 768px) {
  .contact-content {
    flex-direction: column;
  }
}
</style>
