<template>
  <section id="portfolio" class="portfolio">
    <div class="container">
      <h2>Our Portfolio</h2>
      <div class="filter-buttons">
        <button
          v-for="category in categories"
          :key="category"
          @click="setActiveCategory(category)"
          :class="{ 'active': activeCategory === category }"
          class="filter-btn"
        >
          {{ category }}
        </button>
      </div>
      <div class="portfolio-grid">
        <div
          v-for="project in filteredProjects"
          :key="project.id"
          class="portfolio-item"
          @click="openModal(project)"
        >
          <div class="portfolio-image">
            <img :src="project.image" :alt="project.title" />
            <div class="portfolio-overlay">
              <div class="overlay-content">
                <h3>{{ project.title }}</h3>
                <p>{{ project.category }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Modal -->
      <div v-if="selectedProject" class="modal" @click="closeModal">
        <div class="modal-content" @click.stop>
          <span class="close" @click="closeModal">&times;</span>
          <div class="modal-body">
            <img :src="selectedProject.image" :alt="selectedProject.title" class="modal-image" />
            <div class="modal-details">
              <h3>{{ selectedProject.title }}</h3>
              <p class="project-category">{{ selectedProject.category }}</p>
              <p class="project-description">{{ selectedProject.description }}</p>
              <div class="project-tech">
                <strong>Technologies:</strong> {{ selectedProject.technologies.join(', ') }}
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from 'vue'

const activeCategory = ref('All')
const selectedProject = ref(null)

const categories = ['All', 'Web Development', 'Mobile Apps', 'E-commerce', 'Cloud Solutions']

const projects = ref([
  {
    id: 1,
    title: 'E-commerce Platform',
    category: 'E-commerce',
    image: 'https://images.unsplash.com/photo-1563013544-824ae1b704d3?w=400&h=300&fit=crop',
    description: 'A comprehensive e-commerce solution with advanced inventory management, payment processing, and analytics dashboard.',
    technologies: ['Vue.js', 'Node.js', 'MongoDB', 'Stripe API']
  },
  {
    id: 2,
    title: 'Healthcare Management System',
    category: 'Web Development',
    image: 'https://images.unsplash.com/photo-1559757148-5c350d0d3c56?w=400&h=300&fit=crop',
    description: 'Complete healthcare management platform for clinics with patient records, appointment scheduling, and telemedicine features.',
    technologies: ['React', 'Python', 'PostgreSQL', 'WebRTC']
  },
  {
    id: 3,
    title: 'Fitness Tracking App',
    category: 'Mobile Apps',
    image: 'https://images.unsplash.com/photo-1571019613454-1cb2f99b2d8b?w=400&h=300&fit=crop',
    description: 'Cross-platform mobile app for fitness tracking with workout plans, progress monitoring, and social features.',
    technologies: ['React Native', 'Firebase', 'Node.js', 'MongoDB']
  },
  {
    id: 4,
    title: 'Financial Dashboard',
    category: 'Web Development',
    image: 'https://images.unsplash.com/photo-1611974789855-9c2a0a7236a3?w=400&h=300&fit=crop',
    description: 'Real-time financial dashboard with market data, portfolio tracking, and automated reporting features.',
    technologies: ['Vue.js', 'D3.js', 'Python', 'Redis']
  },
  {
    id: 5,
    title: 'Cloud Migration Service',
    category: 'Cloud Solutions',
    image: 'https://images.unsplash.com/photo-1451187580459-43490279c0fa?w=400&h=300&fit=crop',
    description: 'Complete cloud migration solution with automated deployment, monitoring, and optimization services.',
    technologies: ['AWS', 'Docker', 'Kubernetes', 'Terraform']
  },
  {
    id: 6,
    title: 'Restaurant Ordering System',
    category: 'Mobile Apps',
    image: 'https://images.unsplash.com/photo-1517248135467-4c7edcad34c4?w=400&h=300&fit=crop',
    description: 'Mobile ordering system for restaurants with table reservations, menu management, and payment integration.',
    technologies: ['Flutter', 'Firebase', 'Stripe', 'Google Maps API']
  }
])

const filteredProjects = computed(() => {
  if (activeCategory.value === 'All') {
    return projects.value
  }
  return projects.value.filter(project => project.category === activeCategory.value)
})

const setActiveCategory = (category) => {
  activeCategory.value = category
}

const openModal = (project) => {
  selectedProject.value = project
}

const closeModal = () => {
  selectedProject.value = null
}
</script>

<style scoped>
.portfolio {
  padding: 80px 0;
  background-color: #fff;
}

.portfolio h2 {
  text-align: center;
  margin-bottom: 40px;
  color: #333;
}

.filter-buttons {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 10px;
  margin-bottom: 50px;
}

.filter-btn {
  padding: 10px 20px;
  border: 2px solid #007bff;
  background: transparent;
  color: #007bff;
  border-radius: 25px;
  cursor: pointer;
  transition: all 0.3s;
  font-weight: 500;
}

.filter-btn:hover,
.filter-btn.active {
  background: #007bff;
  color: white;
}

.portfolio-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 30px;
}

.portfolio-item {
  cursor: pointer;
  border-radius: 10px;
  overflow: hidden;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s, box-shadow 0.3s;
}

.portfolio-item:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.15);
}

.portfolio-image {
  position: relative;
  height: 250px;
  overflow: hidden;
}

.portfolio-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.3s;
}

.portfolio-item:hover .portfolio-image img {
  transform: scale(1.1);
}

.portfolio-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 123, 255, 0.9);
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: opacity 0.3s;
}

.portfolio-item:hover .portfolio-overlay {
  opacity: 1;
}

.overlay-content {
  text-align: center;
  color: white;
}

.overlay-content h3 {
  margin: 0 0 10px 0;
  font-size: 1.2rem;
}

.overlay-content p {
  margin: 0;
  opacity: 0.9;
}

/* Modal Styles */
.modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.8);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1000;
}

.modal-content {
  background: white;
  border-radius: 10px;
  max-width: 800px;
  width: 90%;
  max-height: 90vh;
  overflow-y: auto;
  position: relative;
}

.close {
  position: absolute;
  top: 15px;
  right: 20px;
  font-size: 28px;
  cursor: pointer;
  color: #333;
  z-index: 1001;
}

.modal-body {
  display: flex;
  flex-direction: column;
}

.modal-image {
  width: 100%;
  height: 300px;
  object-fit: cover;
  border-radius: 10px 10px 0 0;
}

.modal-details {
  padding: 30px;
}

.modal-details h3 {
  margin: 0 0 10px 0;
  color: #333;
}

.project-category {
  color: #007bff;
  font-weight: 500;
  margin-bottom: 15px;
}

.project-description {
  color: #666;
  line-height: 1.6;
  margin-bottom: 15px;
}

.project-tech {
  color: #333;
  font-size: 0.9rem;
}

@media (max-width: 768px) {
  .portfolio-grid {
    grid-template-columns: 1fr;
  }

  .filter-buttons {
    justify-content: center;
  }

  .modal-body {
    flex-direction: column;
  }

  .modal-details {
    padding: 20px;
  }
}
</style>
