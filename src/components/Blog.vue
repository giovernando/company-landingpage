<template>
  <section id="blog" class="blog">
    <div class="container">
      <h2>Latest Insights & Case Studies</h2>
      <div class="blog-grid">
        <article class="blog-card" v-for="post in blogPosts" :key="post.id">
          <div class="blog-image">
            <img :src="post.image" :alt="post.title" loading="lazy" />
            <div class="blog-category">{{ post.category }}</div>
          </div>
          <div class="blog-content">
            <h3>{{ post.title }}</h3>
            <p class="blog-excerpt">{{ post.excerpt }}</p>
            <div class="blog-meta">
              <span class="date">{{ post.date }}</span>
              <span class="read-time">{{ post.readTime }} min read</span>
            </div>
            <a :href="post.link" class="read-more">Read More <i class="fas fa-arrow-right"></i></a>
          </div>
        </article>
      </div>
      <div class="blog-cta">
        <a href="#contact" class="btn-primary">Get Your Free Consultation</a>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const blogPosts = ref([
  {
    id: 1,
    title: 'The Future of Cloud Computing: Trends to Watch in 2024',
    category: 'Technology',
    image: 'https://images.unsplash.com/photo-1451187580459-43490279c0fa?w=400&h=250&fit=crop',
    excerpt: 'Explore the latest trends shaping cloud computing, from serverless architecture to edge computing and AI integration.',
    date: 'Dec 15, 2024',
    readTime: 5,
    link: '#'
  },
  {
    id: 2,
    title: 'How We Helped TechCorp Scale to 1M Users',
    category: 'Case Study',
    image: 'https://images.unsplash.com/photo-1551288049-bebda4e38f71?w=400&h=250&fit=crop',
    excerpt: 'A detailed case study on how our cloud migration and optimization strategies helped TechCorp achieve massive growth.',
    date: 'Dec 10, 2024',
    readTime: 8,
    link: '#'
  },
  {
    id: 3,
    title: 'Cybersecurity Best Practices for Modern Businesses',
    category: 'Security',
    image: 'https://images.unsplash.com/photo-1563013544-824ae1b704d3?w=400&h=250&fit=crop',
    excerpt: 'Essential cybersecurity measures every business should implement to protect against modern threats.',
    date: 'Dec 5, 2024',
    readTime: 6,
    link: '#'
  },
  {
    id: 4,
    title: 'Mobile App Development: Native vs Cross-Platform',
    category: 'Development',
    image: 'https://images.unsplash.com/photo-1512941937669-90a1b58e7e9c?w=400&h=250&fit=crop',
    excerpt: 'Comparing native and cross-platform development approaches to help you choose the right strategy for your project.',
    date: 'Nov 28, 2024',
    readTime: 7,
    link: '#'
  },
  {
    id: 5,
    title: 'Digital Transformation Success Stories',
    category: 'Case Study',
    image: 'https://images.unsplash.com/photo-1551288049-bebda4e38f71?w=400&h=250&fit=crop',
    excerpt: 'Real-world examples of how digital transformation has revolutionized businesses across different industries.',
    date: 'Nov 20, 2024',
    readTime: 9,
    link: '#'
  },
  {
    id: 6,
    title: 'The ROI of Investing in Quality Software Development',
    category: 'Business',
    image: 'https://images.unsplash.com/photo-1460925895917-afdab827c52f?w=400&h=250&fit=crop',
    excerpt: 'Understanding the long-term benefits and return on investment when choosing quality over quick solutions.',
    date: 'Nov 15, 2024',
    readTime: 6,
    link: '#'
  }
])
</script>

<style scoped>
.blog {
  padding: 80px 0;
  background-color: #fff;
}

.blog h2 {
  text-align: center;
  margin-bottom: 60px;
  color: #333;
}

.blog-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 30px;
  margin-bottom: 50px;
}

.blog-card {
  background: white;
  border-radius: 10px;
  overflow: hidden;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s, box-shadow 0.3s;
}

.blog-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.15);
}

.blog-image {
  position: relative;
  height: 200px;
  overflow: hidden;
}

.blog-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.3s;
}

.blog-card:hover .blog-image img {
  transform: scale(1.05);
}

.blog-category {
  position: absolute;
  top: 15px;
  left: 15px;
  background: #007bff;
  color: white;
  padding: 5px 10px;
  border-radius: 15px;
  font-size: 0.8rem;
  font-weight: 500;
}

.blog-content {
  padding: 25px;
}

.blog-content h3 {
  margin: 0 0 15px 0;
  color: #333;
  font-size: 1.2rem;
  line-height: 1.4;
}

.blog-excerpt {
  color: #666;
  line-height: 1.6;
  margin-bottom: 15px;
}

.blog-meta {
  display: flex;
  justify-content: space-between;
  font-size: 0.9rem;
  color: #999;
  margin-bottom: 15px;
}

.read-more {
  color: #007bff;
  text-decoration: none;
  font-weight: 500;
  display: inline-flex;
  align-items: center;
  gap: 5px;
  transition: color 0.3s;
}

.read-more:hover {
  color: #0056b3;
}

.blog-cta {
  text-align: center;
}

.btn-primary {
  background: #007bff;
  color: white;
  padding: 15px 30px;
  border: none;
  border-radius: 5px;
  font-size: 1.1rem;
  font-weight: 500;
  cursor: pointer;
  text-decoration: none;
  display: inline-block;
  transition: background 0.3s;
}

.btn-primary:hover {
  background: #0056b3;
}

@media (max-width: 768px) {
  .blog-grid {
    grid-template-columns: 1fr;
  }

  .blog-content {
    padding: 20px;
  }
}
</style>
