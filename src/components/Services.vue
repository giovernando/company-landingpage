<template>
  <section id="services" class="services">
    <div class="container">
      <h2>Our Services</h2>
      <div class="services-grid">
        <div class="service-card">
          <h3>Web Development</h3>
          <p>We create responsive and modern websites tailored to your business needs.</p>
        </div>
        <div class="service-card">
          <h3>Mobile Apps</h3>
          <p>Develop native and cross-platform mobile applications for iOS and Android.</p>
        </div>
        <div class="service-card">
          <h3>Consulting</h3>
          <p>Get expert advice on technology strategy and digital transformation.</p>
        </div>
        <div class="service-card">
          <h3>Support</h3>
          <p>24/7 technical support to keep your systems running smoothly.</p>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.services {
  padding: 100px 0;
  background-color: #fff;
}

.services h2 {
  text-align: center;
  font-size: 36px;
  margin-bottom: 60px;
  color: #333;
}

.services-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 30px;
}

.service-card {
  background-color: #f8f9fa;
  padding: 30px;
  border-radius: 10px;
  text-align: center;
  transition: transform 0.3s, box-shadow 0.3s;
}

.service-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
}

.service-card h3 {
  font-size: 24px;
  margin-bottom: 15px;
  color: #333;
}

.service-card p {
  color: #666;
  line-height: 1.6;
}
</style>
