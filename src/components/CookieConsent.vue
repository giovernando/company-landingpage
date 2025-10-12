<template>
  <div v-if="!accepted" class="cookie-consent" role="dialog" aria-labelledby="cookie-title" aria-describedby="cookie-description">
    <div class="cookie-content">
      <h4 id="cookie-title">Cookie Preferences</h4>
      <p id="cookie-description">
        We use cookies to enhance your browsing experience, serve personalized content, and analyze our traffic.
        By clicking "Accept All", you consent to our use of cookies.
      </p>
      <div class="cookie-buttons">
        <button @click="acceptAll" class="btn-primary">Accept All</button>
        <button @click="acceptEssential" class="btn-secondary">Essential Only</button>
        <button @click="customize" class="btn-link">Customize</button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const accepted = ref(localStorage.getItem('cookie-consent') === 'accepted')

const acceptAll = () => {
  localStorage.setItem('cookie-consent', 'accepted')
  accepted.value = true
  // Initialize Google Analytics or other tracking
  initializeTracking()
}

const acceptEssential = () => {
  localStorage.setItem('cookie-consent', 'essential')
  accepted.value = true
}

const customize = () => {
  // Open detailed cookie preferences modal
  alert('Cookie customization coming soon!')
}

const initializeTracking = () => {
  // Google Analytics initialization
  if (typeof gtag !== 'undefined') {
    gtag('consent', 'update', {
      'analytics_storage': 'granted'
    })
  }
}
</script>

<style scoped>
.cookie-consent {
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
  background: white;
  border-top: 1px solid #e0e0e0;
  box-shadow: 0 -2px 10px rgba(0, 0, 0, 0.1);
  z-index: 10000;
  padding: 20px;
}

.cookie-content {
  max-width: 1200px;
  margin: 0 auto;
}

.cookie-content h4 {
  margin: 0 0 10px 0;
  color: #333;
  font-size: 1.2rem;
}

.cookie-content p {
  margin: 0 0 20px 0;
  color: #666;
  line-height: 1.5;
}

.cookie-buttons {
  display: flex;
  gap: 15px;
  flex-wrap: wrap;
}

.btn-primary {
  background: #007bff;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 5px;
  cursor: pointer;
  font-weight: 500;
  transition: background 0.3s;
}

.btn-primary:hover {
  background: #0056b3;
}

.btn-secondary {
  background: #6c757d;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 5px;
  cursor: pointer;
  font-weight: 500;
  transition: background 0.3s;
}

.btn-secondary:hover {
  background: #545b62;
}

.btn-link {
  background: transparent;
  color: #007bff;
  border: none;
  padding: 10px 20px;
  cursor: pointer;
  text-decoration: underline;
  font-weight: 500;
}

@media (max-width: 768px) {
  .cookie-buttons {
    flex-direction: column;
  }

  .cookie-consent {
    padding: 15px;
  }
}
</style>
