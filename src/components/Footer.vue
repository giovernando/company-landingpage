<template>
  <footer class="footer">
    <div class="container">
      <div class="footer-content">
        <div class="footer-section">
          <h3>NexusForge</h3>
          <p>Providing innovative solutions for your business needs.</p>
        </div>
        <div class="footer-section">
          <h3>Quick Links</h3>
          <ul>
            <li><a href="#hero">Home</a></li>
            <li><a href="#about">About</a></li>
            <li><a href="#services">Services</a></li>
            <li><a href="#testimonials">Testimonials</a></li>
            <li><a href="#contact">Contact</a></li>
          </ul>
        </div>
        <div class="footer-section">
          <h3>Follow Us</h3>
          <div class="social-links">
            <a href="#" class="social-link">Facebook</a>
            <a href="#" class="social-link">Twitter</a>
            <a href="#" class="social-link">LinkedIn</a>
          </div>
        </div>
      </div>
      <div class="footer-bottom">
        <p>&copy; 2024 NexusForge. All rights reserved.</p>
      </div>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  background-color: #333;
  color: white;
  padding: 60px 0 20px;
}

.footer-content {
  display: flex;
  justify-content: space-between;
  margin-bottom: 40px;
}

.footer-section {
  flex: 1;
  margin-right: 30px;
}

.footer-section h3 {
  font-size: 20px;
  margin-bottom: 20px;
}

.footer-section p {
  color: #ccc;
  line-height: 1.6;
}

.footer-section ul {
  list-style: none;
  padding: 0;
}

.footer-section li {
  margin-bottom: 10px;
}

.footer-section a {
  color: #ccc;
  text-decoration: none;
  transition: color 0.3s;
}

.footer-section a:hover {
  color: white;
}

.social-links {
  display: flex;
  gap: 15px;
}

.social-link {
  color: #ccc;
  text-decoration: none;
  transition: color 0.3s;
}

.social-link:hover {
  color: white;
}

.footer-bottom {
  border-top: 1px solid #555;
  padding-top: 20px;
  text-align: center;
}

.footer-bottom p {
  margin: 0;
  color: #ccc;
}

@media (max-width: 768px) {
  .footer-content {
    flex-direction: column;
  }

  .footer-section {
    margin-right: 0;
    margin-bottom: 30px;
  }
}
</style>
