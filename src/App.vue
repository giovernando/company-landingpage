<script setup>
import { onMounted } from 'vue'
import Header from './components/Header.vue'
import Hero from './components/Hero.vue'
import About from './components/About.vue'
import Services from './components/Services.vue'
import Portfolio from './components/Portfolio.vue'
import Testimonials from './components/Testimonials.vue'
import Stats from './components/Stats.vue'
import FAQ from './components/FAQ.vue'
import Newsletter from './components/Newsletter.vue'
import Contact from './components/Contact.vue'
import Footer from './components/Footer.vue'
import TrustBadges from './components/TrustBadges.vue'
import CookieConsent from './components/CookieConsent.vue'
import Blog from './components/Blog.vue'

onMounted(() => {
  // Intersection Observer for fade-in animations
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('fade-in')
      }
    })
  }, { threshold: 0.1 })

  // Observe all sections
  document.querySelectorAll('section').forEach(section => {
    observer.observe(section)
  })

  // Lazy loading for images
  const imageObserver = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        const img = entry.target
        img.src = img.dataset.src
        img.classList.remove('lazy')
        imageObserver.unobserve(img)
      }
    })
  })

  // Observe lazy images
  document.querySelectorAll('img[data-src]').forEach(img => {
    imageObserver.observe(img)
  })
})
</script>

<template>
  <Header />
  <Hero />
  <TrustBadges />
  <About />
  <Services />
  <Portfolio />
  <Testimonials />
  <Stats />
  <Blog />
  <FAQ />
  <Newsletter />
  <Contact />
  <Footer />
  <CookieConsent />
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html {
  scroll-behavior: smooth;
}

body {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  line-height: 1.6;
  color: #333;
  overflow-x: hidden;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

a {
  color: #007bff;
  text-decoration: none;
}

a:hover {
  text-decoration: underline;
}

section {
  padding: 80px 0;
  opacity: 0;
  transform: translateY(30px);
  transition: opacity 0.6s ease, transform 0.6s ease;
}

section.fade-in {
  opacity: 1;
  transform: translateY(0);
}

h2 {
  font-size: 2.5rem;
  margin-bottom: 1rem;
}

h3 {
  font-size: 1.5rem;
  margin-bottom: 0.5rem;
}

p {
  margin-bottom: 1rem;
}

.btn-primary {
  background: #007bff;
  color: white;
  padding: 12px 24px;
  border: none;
  border-radius: 5px;
  font-size: 1rem;
  font-weight: 500;
  cursor: pointer;
  text-decoration: none;
  display: inline-block;
  transition: all 0.3s;
}

.btn-primary:hover {
  background: #0056b3;
  transform: translateY(-2px);
  box-shadow: 0 5px 15px rgba(0, 123, 255, 0.3);
}

.btn-secondary {
  background: transparent;
  color: #007bff;
  padding: 12px 24px;
  border: 2px solid #007bff;
  border-radius: 5px;
  font-size: 1rem;
  font-weight: 500;
  cursor: pointer;
  text-decoration: none;
  display: inline-block;
  transition: all 0.3s;
}

.btn-secondary:hover {
  background: #007bff;
  color: white;
  transform: translateY(-2px);
}

@media (max-width: 768px) {
  .container {
    padding: 0 15px;
  }

  section {
    padding: 60px 0;
  }

  h2 {
    font-size: 2rem;
  }

  .btn-primary,
  .btn-secondary {
    width: 100%;
    text-align: center;
  }
}
</style>
