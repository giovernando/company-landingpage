<template>
  <section id="about" class="about">
    <div class="container">
      <h2>About Us</h2>
      <div class="about-content">
        <div class="about-text">
          <p>We are a leading company dedicated to delivering high-quality solutions to our clients. With years of experience in the industry, we have built a reputation for excellence and innovation.</p>
          <p>Our team consists of skilled professionals who are passionate about what they do. We believe in continuous learning and staying ahead of the latest trends to provide the best services possible.</p>
        </div>
        <div class="about-image">
          <img src="https://images.unsplash.com/photo-1522071820081-009f0129c71c?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1170&q=80" alt="Professional team working together" class="about-img">
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.about {
  padding: 100px 0;
  background-color: #f8f9fa;
}

.about h2 {
  text-align: center;
  font-size: 36px;
  margin-bottom: 60px;
  color: #333;
}

.about-content {
  display: flex;
  align-items: center;
  gap: 60px;
}

.about-text p {
  font-size: 18px;
  line-height: 1.6;
  color: #666;
  margin-bottom: 20px;
}

.about-img {
  width: 100%;
  max-width: 400px;
  height: auto;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

@media (max-width: 768px) {
  .about-content {
    flex-direction: column;
  }

  .about-img {
    max-width: 100%;
  }
}
</style>
