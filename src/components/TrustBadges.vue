<template>
  <section class="trust-badges">
    <div class="container">
      <h3>Trusted by Industry Leaders</h3>
      <div class="badges-grid">
        <div class="badge-item">
          <img src="https://images.unsplash.com/photo-1560472354-b33ff0c44a43?w=150&h=80&fit=crop" alt="TechCorp Logo" />
        </div>
        <div class="badge-item">
          <img src="https://images.unsplash.com/photo-1551288049-bebda4e38f71?w=150&h=80&fit=crop" alt="InnovateLab Logo" />
        </div>
        <div class="badge-item">
          <img src="https://images.unsplash.com/photo-1551288049-bebda4e38f71?w=150&h=80&fit=crop" alt="DataFlow Logo" />
        </div>
        <div class="badge-item">
          <img src="https://images.unsplash.com/photo-1560472354-b33ff0c44a43?w=150&h=80&fit=crop" alt="CloudTech Logo" />
        </div>
        <div class="badge-item">
          <img src="https://images.unsplash.com/photo-1551288049-bebda4e38f71?w=150&h=80&fit=crop" alt="SecureNet Logo" />
        </div>
        <div class="badge-item">
          <img src="https://images.unsplash.com/photo-1560472354-b33ff0c44a43?w=150&h=80&fit=crop" alt="FutureSys Logo" />
        </div>
      </div>
      <div class="certifications">
        <div class="cert-item">
          <i class="fas fa-shield-alt"></i>
          <span>ISO 27001 Certified</span>
        </div>
        <div class="cert-item">
          <i class="fas fa-lock"></i>
          <span>SOC 2 Compliant</span>
        </div>
        <div class="cert-item">
          <i class="fas fa-check-circle"></i>
          <span>GDPR Compliant</span>
        </div>
        <div class="cert-item">
          <i class="fas fa-award"></i>
          <span>AWS Advanced Partner</span>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.trust-badges {
  padding: 60px 0;
  background-color: #f8f9fa;
  text-align: center;
}

.trust-badges h3 {
  margin-bottom: 40px;
  color: #333;
  font-size: 1.5rem;
}

.badges-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  gap: 30px;
  margin-bottom: 50px;
  align-items: center;
}

.badge-item {
  padding: 20px;
  background: white;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s;
}

.badge-item:hover {
  transform: translateY(-5px);
}

.badge-item img {
  width: 100%;
  height: 60px;
  object-fit: contain;
  filter: grayscale(100%);
  transition: filter 0.3s;
}

.badge-item:hover img {
  filter: grayscale(0%);
}

.certifications {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 30px;
}

.cert-item {
  display: flex;
  align-items: center;
  gap: 10px;
  color: #666;
  font-weight: 500;
}

.cert-item i {
  color: #007bff;
  font-size: 1.2rem;
}

@media (max-width: 768px) {
  .badges-grid {
    grid-template-columns: repeat(2, 1fr);
  }

  .certifications {
    flex-direction: column;
    align-items: center;
  }
}
</style>
