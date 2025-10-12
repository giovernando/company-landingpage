<template>
  <section id="hero" class="hero">
    <div class="container">
      <div class="hero-content">
        <h2>Welcome to Our Company</h2>
        <p>We provide innovative solutions for your business needs.</p>
        <a href="#contact" class="btn-primary">Get Free Consultation</a>
        <a href="#portfolio" class="btn-secondary">View Our Work</a>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero {
  background: linear-gradient(135deg, rgba(102, 126, 234, 0.8) 0%, rgba(118, 75, 162, 0.8) 100%), url('https://images.unsplash.com/photo-1552664730-d307ca884978?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1170&q=80');
  background-size: cover;
  background-position: center;
  color: white;
  padding: 120px 0 100px;
  text-align: center;
  position: relative;
}

.hero::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.3);
  z-index: 1;
}

.hero-content {
  position: relative;
  z-index: 2;
}

.hero-content h2 {
  font-size: 48px;
  margin-bottom: 20px;
  font-weight: 700;
}

.hero-content p {
  font-size: 20px;
  margin-bottom: 40px;
  opacity: 0.9;
}

.cta-button {
  display: inline-block;
  background-color: #fff;
  color: #667eea;
  padding: 15px 30px;
  text-decoration: none;
  border-radius: 5px;
  font-weight: 600;
  transition: all 0.3s;
}

.cta-button:hover {
  background-color: #f8f9fa;
  transform: translateY(-2px);
}
</style>
