<template>
  <section id="testimonials" class="testimonials">
    <div class="container">
      <h2>What Our Clients Say</h2>
      <div class="testimonials-grid">
        <div class="testimonial-card">
          <div class="testimonial-content">
            <p>"NexusForge transformed our business operations with their innovative solutions. The team's expertise and dedication are unmatched."</p>
          </div>
          <div class="testimonial-author">
            <img src="https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?w=100&h=100&fit=crop&crop=face" alt="Client" class="author-image">
            <div class="author-info">
              <h4>Sarah Johnson</h4>
              <p>CEO, TechCorp</p>
            </div>
          </div>
        </div>
        <div class="testimonial-card">
          <div class="testimonial-content">
            <p>"Working with NexusForge was a game-changer. Their solutions helped us scale efficiently and improve our customer experience."</p>
          </div>
          <div class="testimonial-author">
            <img src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?w=100&h=100&fit=crop&crop=face" alt="Client" class="author-image">
            <div class="author-info">
              <h4>Michael Chen</h4>
              <p>CTO, InnovateLabs</p>
            </div>
          </div>
        </div>
        <div class="testimonial-card">
          <div class="testimonial-content">
            <p>"The professionalism and quality of work from NexusForge exceeded our expectations. Highly recommended for any business."</p>
          </div>
          <div class="testimonial-author">
            <img src="https://images.unsplash.com/photo-1580489944761-15a19d654956?w=100&h=100&fit=crop&crop=face" alt="Client" class="author-image">
            <div class="author-info">
              <h4>Emily Rodriguez</h4>
              <p>Founder, StartupXYZ</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.testimonials {
  background-color: #f8f9fa;
  padding: 80px 0;
}

.testimonials h2 {
  text-align: center;
  margin-bottom: 60px;
  color: #333;
}

.testimonials-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 30px;
}

.testimonial-card {
  background: white;
  padding: 30px;
  border-radius: 10px;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.testimonial-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.15);
}

.testimonial-content p {
  font-style: italic;
  color: #666;
  margin-bottom: 20px;
  font-size: 1.1rem;
  line-height: 1.6;
}

.testimonial-author {
  display: flex;
  align-items: center;
}

.author-image {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  margin-right: 15px;
  object-fit: cover;
}

.author-info h4 {
  margin: 0;
  color: #333;
  font-size: 1.1rem;
}

.author-info p {
  margin: 0;
  color: #666;
  font-size: 0.9rem;
}

@media (max-width: 768px) {
  .testimonials-grid {
    grid-template-columns: 1fr;
  }

  .testimonial-card {
    padding: 20px;
  }
}
</style>
