<template>
  <section id="faq" class="faq">
    <div class="container">
      <h2>Frequently Asked Questions</h2>
      <div class="faq-list">
        <div class="faq-item" v-for="(faq, index) in faqs" :key="index">
          <div class="faq-question" @click="toggleFAQ(index)">
            <h3>{{ faq.question }}</h3>
            <span class="faq-icon" :class="{ 'active': activeIndex === index }">+</span>
          </div>
          <div class="faq-answer" :class="{ 'active': activeIndex === index }">
            <p>{{ faq.answer }}</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const activeIndex = ref(null)

const faqs = ref([
  {
    question: "What services does NexusForge offer?",
    answer: "We offer comprehensive digital solutions including web development, mobile app development, cloud services, digital marketing, and IT consulting. Our team specializes in creating innovative solutions tailored to your business needs."
  },
  {
    question: "How long does a typical project take?",
    answer: "Project timelines vary depending on complexity and scope. A simple website might take 2-4 weeks, while a complex web application could take 3-6 months. We'll provide a detailed timeline during our initial consultation."
  },
  {
    question: "Do you provide ongoing support after project completion?",
    answer: "Yes, we offer 24/7 technical support and maintenance packages. Our team ensures your solutions remain secure, up-to-date, and performing optimally long after the initial development phase."
  },
  {
    question: "What is your development process?",
    answer: "We follow an agile development methodology with clear milestones: Discovery & Planning, Design, Development, Testing, Deployment, and Ongoing Support. We maintain transparent communication throughout the entire process."
  },
  {
    question: "How do you ensure project quality?",
    answer: "Quality is our top priority. We implement rigorous testing protocols, code reviews, and follow industry best practices. Each project undergoes multiple quality assurance phases before delivery."
  },
  {
    question: "Can you work with our existing systems?",
    answer: "Absolutely. We specialize in system integration and can work with your existing infrastructure, databases, and third-party services. Our solutions are designed to complement and enhance your current technology stack."
  }
])

const toggleFAQ = (index) => {
  activeIndex.value = activeIndex.value === index ? null : index
}
</script>

<style scoped>
.faq {
  background-color: #f8f9fa;
  padding: 80px 0;
}

.faq h2 {
  text-align: center;
  margin-bottom: 60px;
  color: #333;
}

.faq-list {
  max-width: 800px;
  margin: 0 auto;
}

.faq-item {
  background: white;
  margin-bottom: 15px;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  overflow: hidden;
}

.faq-question {
  padding: 25px 30px;
  cursor: pointer;
  display: flex;
  justify-content: space-between;
  align-items: center;
  transition: background-color 0.3s;
}

.faq-question:hover {
  background-color: #f8f9fa;
}

.faq-question h3 {
  margin: 0;
  font-size: 1.1rem;
  color: #333;
}

.faq-icon {
  font-size: 1.5rem;
  font-weight: bold;
  color: #007bff;
  transition: transform 0.3s;
}

.faq-icon.active {
  transform: rotate(45deg);
}

.faq-answer {
  max-height: 0;
  overflow: hidden;
  transition: max-height 0.3s ease;
  background-color: #f8f9fa;
}

.faq-answer.active {
  max-height: 200px;
}

.faq-answer p {
  margin: 0;
  padding: 0 30px 25px 30px;
  color: #666;
  line-height: 1.6;
}

@media (max-width: 768px) {
  .faq-question {
    padding: 20px;
  }

  .faq-answer p {
    padding: 0 20px 20px 20px;
  }
}
</style>
