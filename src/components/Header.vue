<template>
  <header class="header">
    <div class="container">
      <div class="logo">
        <h1>NexusForge</h1>
      </div>
      <nav class="nav">
        <div class="hamburger" @click="toggleMenu" :class="{ 'active': isMenuOpen }">
          <span></span>
          <span></span>
          <span></span>
        </div>
        <ul :class="{ 'active': isMenuOpen }">
          <li><a href="#hero" @click="closeMenu">Home</a></li>
          <li><a href="#about" @click="closeMenu">About</a></li>
          <li><a href="#services" @click="closeMenu">Services</a></li>
          <li><a href="#portfolio" @click="closeMenu">Portfolio</a></li>
          <li><a href="#testimonials" @click="closeMenu">Testimonials</a></li>
          <li><a href="#faq" @click="closeMenu">FAQ</a></li>
          <li><a href="#contact" @click="closeMenu">Contact</a></li>
        </ul>
      </nav>
    </div>
  </header>
</template>

<script setup>
import { ref } from 'vue'

const isMenuOpen = ref(false)

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
}

const closeMenu = () => {
  isMenuOpen.value = false
}
</script>

<style scoped>
.header {
  background-color: #fff;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  position: fixed;
  top: 0;
  width: 100%;
  z-index: 1000;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 80px;
}

.logo h1 {
  margin: 0;
  color: #333;
  font-size: 24px;
}

.hamburger {
  display: none;
  flex-direction: column;
  cursor: pointer;
  padding: 5px;
}

.hamburger span {
  width: 25px;
  height: 3px;
  background: #333;
  margin: 3px 0;
  transition: 0.3s;
  border-radius: 2px;
}

.hamburger.active span:nth-child(1) {
  transform: rotate(-45deg) translate(-5px, 6px);
}

.hamburger.active span:nth-child(2) {
  opacity: 0;
}

.hamburger.active span:nth-child(3) {
  transform: rotate(45deg) translate(-5px, -6px);
}

.nav ul {
  list-style: none;
  margin: 0;
  padding: 0;
  display: flex;
}

.nav li {
  margin-left: 30px;
}

.nav a {
  text-decoration: none;
  color: #333;
  font-weight: 500;
  transition: color 0.3s;
}

.nav a:hover {
  color: #007bff;
}

@media (max-width: 768px) {
  .hamburger {
    display: flex;
  }

  .nav ul {
    position: fixed;
    top: 80px;
    left: -100%;
    width: 100%;
    height: calc(100vh - 80px);
    background: #fff;
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
    padding-top: 50px;
    transition: left 0.3s;
    box-shadow: 0 5px 10px rgba(0, 0, 0, 0.1);
  }

  .nav ul.active {
    left: 0;
  }

  .nav li {
    margin: 20px 0;
    margin-left: 0;
  }

  .nav a {
    font-size: 1.2rem;
  }
}
</style>
