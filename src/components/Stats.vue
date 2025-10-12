<template>
  <section class="stats">
    <div class="container">
      <div class="stats-grid">
        <div class="stat-item">
          <div class="stat-number" data-target="500">0</div>
          <div class="stat-label">Projects Completed</div>
        </div>
        <div class="stat-item">
          <div class="stat-number" data-target="98">0</div>
          <div class="stat-label">Client Satisfaction</div>
        </div>
        <div class="stat-item">
          <div class="stat-number" data-target="50">0</div>
          <div class="stat-label">Team Members</div>
        </div>
        <div class="stat-item">
          <div class="stat-number" data-target="24">0</div>
          <div class="stat-label">Hours Support</div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { onMounted } from 'vue'

onMounted(() => {
  const observerOptions = {
    threshold: 0.5,
    rootMargin: '0px 0px -50px 0px'
  }

  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        animateCounter(entry.target)
        observer.unobserve(entry.target)
      }
    })
  }, observerOptions)

  const statNumbers = document.querySelectorAll('.stat-number')
  statNumbers.forEach(number => observer.observe(number))

  function animateCounter(element) {
    const target = parseInt(element.getAttribute('data-target'))
    const duration = 2000 // 2 seconds
    const step = target / (duration / 16) // 60fps
    let current = 0

    const timer = setInterval(() => {
      current += step
      if (current >= target) {
        element.textContent = target + (element.nextElementSibling.textContent.includes('%') ? '%' : '+')
        clearInterval(timer)
      } else {
        element.textContent = Math.floor(current) + (element.nextElementSibling.textContent.includes('%') ? '%' : '+')
      }
    }, 16)
  }
})
</script>

<style scoped>
.stats {
  background-color: #007bff;
  color: white;
  padding: 80px 0;
}

.stats-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 40px;
  text-align: center;
}

.stat-item {
  padding: 20px;
}

.stat-number {
  font-size: 3rem;
  font-weight: bold;
  margin-bottom: 10px;
  color: white;
}

.stat-label {
  font-size: 1.1rem;
  opacity: 0.9;
}

@media (max-width: 768px) {
  .stats-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 30px;
  }

  .stat-number {
    font-size: 2.5rem;
  }
}
</style>
