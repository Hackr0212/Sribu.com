<template>
  <div id="app">
    <!-- Header -->
    <header class="header">
      <div class="container">
        <div class="header-content">
          <div class="logo">
            <h2 class="logo-text">Sribu</h2>
            <p class="tagline">Creative Design Solutions</p>
          </div>
          <nav class="nav">
            <a href="#portfolio" class="nav-link">Portfolio</a>
            <a href="#testimonials" class="nav-link">Reviews</a>
            <a href="#cta" class="nav-link cta-button">Get Started</a>
          </nav>
        </div>
      </div>
    </header>

    <!-- Hero Section -->
    <section class="hero">
      <div class="container">
        <div class="hero-content">
          <h1 class="hero-title">Work with Talented Graphic Designers Online</h1>
          <p class="hero-subtitle">Get more quality design ideas and say good bye to time consuming offline meetings.</p>
          <div class="hero-actions">
            <button class="btn btn-primary" @click="scrollToSection('cta')">Start Your Project</button>
            <button class="btn btn-secondary" @click="scrollToSection('portfolio')">View Portfolio</button>
          </div>
        </div>
        <div class="hero-visual">
          <div class="design-cards">
            <div class="design-card card-1">
              <div class="card-placeholder">Logo Design</div>
            </div>
            <div class="design-card card-2">
              <div class="card-placeholder">Web Design</div>
            </div>
            <div class="design-card card-3">
              <div class="card-placeholder">Branding</div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Problem Section -->
    <section class="problem-section">
      <div class="container">
        <div class="section-header">
          <h2 class="section-title">The Design Challenge</h2>
          <p class="section-subtitle">Difficult finding the best design through freelancers, studios/agencies, or in-house designers.</p>
        </div>
        <div class="problem-grid">
          <div class="problem-item">
            <div class="problem-icon">💡</div>
            <h3>Limited Creative Ideas</h3>
            <p>Restricted pool of creative concepts and design approaches</p>
          </div>
          <div class="problem-item">
            <div class="problem-icon">💰</div>
            <h3>High Costs</h3>
            <p>Expensive retainer fees and project costs that strain budgets</p>
          </div>
          <div class="problem-item">
            <div class="problem-icon">⏰</div>
            <h3>Time Consuming</h3>
            <p>Lengthy processes with multiple revisions and meetings</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Comparison Chart -->
    <section class="comparison-section">
      <div class="container">
        <div class="section-header">
          <h2 class="section-title">Why Choose Sribu?</h2>
          <p class="section-subtitle">Compare different design service options and see the Sribu advantage</p>
        </div>
        <div class="comparison-table">
          <div class="comparison-header">
            <div class="feature-column">Features</div>
            <div class="service-column">Freelancer</div>
            <div class="service-column">In-house</div>
            <div class="service-column">Agency</div>
            <div class="service-column sribu-column">Sribu</div>
          </div>
          <div class="comparison-row" v-for="feature in comparisonFeatures" :key="feature.name">
            <div class="feature-cell">{{ feature.name }}</div>
            <div class="service-cell">{{ feature.freelancer }}</div>
            <div class="service-cell">{{ feature.inhouse }}</div>
            <div class="service-cell">{{ feature.agency }}</div>
            <div class="service-cell sribu-cell">{{ feature.sribu }}</div>
          </div>
        </div>
      </div>
    </section>

    <!-- Portfolio Section -->
    <section id="portfolio" class="portfolio-section">
      <div class="container">
        <div class="section-header">
          <h2 class="section-title">You will get designs like these</h2>
          <p class="section-subtitle">while working with talented designers online.</p>
        </div>
        <div class="portfolio-grid">
          <div class="portfolio-item" v-for="item in portfolioItems" :key="item.id">
            <div class="portfolio-image">
              <img :src="item.image" :alt="item.title" />
              <div class="portfolio-overlay">
                <h4>{{ item.title }}</h4>
                <p>{{ item.category }}</p>
              </div>
            </div>
          </div>
        </div>
        <div class="portfolio-cta">
          <a href="https://www.sribu.com/en/portfolio" target="_blank" class="btn btn-outline">View Full Portfolio</a>
        </div>
      </div>
    </section>

    <!-- Testimonials Section -->
    <section id="testimonials" class="testimonials-section">
      <div class="container">
        <div class="section-header">
          <h2 class="section-title">What Our Clients Say</h2>
          <p class="section-subtitle">Real feedback from businesses who transformed their brand with Sribu</p>
        </div>
        <div class="testimonials-grid">
          <div class="testimonial-card" v-for="testimonial in testimonials" :key="testimonial.id">
            <div class="testimonial-content">
              <div class="stars">★★★★★</div>
              <p class="testimonial-text">"{{ testimonial.text }}"</p>
              <div class="testimonial-author">
                <strong>{{ testimonial.author }}</strong>
                <span>{{ testimonial.company }}</span>
              </div>
            </div>
          </div>
        </div>
        <div class="testimonials-cta">
          <a href="https://www.sribu.com/en/testimonials" target="_blank" class="btn btn-outline">Read More Reviews</a>
        </div>
      </div>
    </section>

    <!-- Call to Action Section -->
    <section id="cta" class="cta-section">
      <div class="container">
        <div class="cta-content">
          <h2 class="cta-title">Ready to Transform Your Brand?</h2>
          <p class="cta-subtitle">Drop your email and we will send you a complete guide on how to work with talented designers online. (PS: We won't spam you).</p>
          )
          <form class="cta-form" @submit.prevent="handleSubmit">
            <div class="form-group">
              <input 
                type="email"
                v-model="email"
                placeholder="Enter your email address"
                class="form-input"
                required
              />
              <button type="submit" class="btn btn-primary" :disabled="isSubmitting">
                {{ isSubmitting ? 'Sending...' : 'Get Free Guide' }}
              </button>
            </div>
          </form>
          <p class="cta-note">Join 10,000+ entrepreneurs who've successfully launched their brands with Sribu</p>
        </div>
      </div>
    </section>

    <!-- About Section -->
    <section class="about-section">
      <div class="container">
        <div class="about-content">
          <h2 class="section-title">About Sribu</h2>
          <p class="about-text">
            Sribu.com is a website that connects clients in need of design services with a community of designers from around the world. 
            Sribu.com offers 20 types of design categories ranging from logos, websites, mascots, posters, and more. 
            The concept applied at Sribu.com is contest-based, ensuring you get multiple creative options to choose from.
          </p>
          <div class="stats-grid">
            <div class="stat-item">
              <div class="stat-number">10,000+</div>
              <div class="stat-label">Happy Clients</div>
            </div>
            <div class="stat-item">
              <div class="stat-number">20+</div>
              <div class="stat-label">Design Categories</div>
            </div>
            <div class="stat-item">
              <div class="stat-number">50,000+</div>
              <div class="stat-label">Designs Created</div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Footer -->
    <footer class="footer">
      <div class="container">
        <div class="footer-content">
          <div class="footer-section">
            <h3>Sribu</h3>
            <p>Connecting businesses with talented designers worldwide</p>
          </div>
          <div class="footer-section">
            <h4>Services</h4>
            <ul>
              <li><a href="#">Logo Design</a></li>
              <li><a href="#">Web Design</a></li>
              <li><a href="#">Branding</a></li>
              <li><a href="#">Print Design</a></li>
            </ul>
          </div>
          <div class="footer-section">
            <h4>Company</h4>
            <ul>
              <li><a href="#">About Us</a></li>
              <li><a href="#">How It Works</a></li>
              <li><a href="#">Pricing</a></li>
              <li><a href="#">Contact</a></li>
            </ul>
          </div>
        </div>
        <div class="footer-bottom">
          <p>&copy; 2025 Sribu. All rights reserved.</p>
        </div>
      </div>
    </footer>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const email = ref('')
const isSubmitting = ref(false)

const comparisonFeatures = [
  {
    name: 'Multiple Design Options',
    freelancer: '1-2 options',
    inhouse: '1 option',
    agency: '2-3 options',
    sribu: '10+ options'
  },
  {
    name: 'Cost',
    freelancer: 'Variable',
    inhouse: 'High',
    agency: 'Very High',
    sribu: 'Affordable'
  },
  {
    name: 'Timeline',
    freelancer: '1-2 weeks',
    inhouse: '2-4 weeks',
    agency: '3-6 weeks',
    sribu: '3-7 days'
  },
  {
    name: 'Revisions',
    freelancer: 'Limited',
    inhouse: 'Limited',
    agency: 'Limited',
    sribu: 'Unlimited'
  },
  {
    name: 'Quality Guarantee',
    freelancer: 'No',
    inhouse: 'Maybe',
    agency: 'Yes',
    sribu: 'Yes'
  }
]

const portfolioItems = [
  {
    id: 1,
    title: 'Modern Tech Logo',
    category: 'Logo Design',
    image: 'https://images.pexels.com/photos/196644/pexels-photo-196644.jpeg?auto=compress&cs=tinysrgb&w=400'
  },
  {
    id: 2,
    title: 'Restaurant Branding',
    category: 'Brand Identity',
    image: 'https://images.pexels.com/photos/1640774/pexels-photo-1640774.jpeg?auto=compress&cs=tinysrgb&w=400'
  },
  {
    id: 3,
    title: 'E-commerce Website',
    category: 'Web Design',
    image: 'https://images.pexels.com/photos/196644/pexels-photo-196644.jpeg?auto=compress&cs=tinysrgb&w=400'
  },
  {
    id: 4,
    title: 'Marketing Poster',
    category: 'Print Design',
    image: 'https://images.pexels.com/photos/1640774/pexels-photo-1640774.jpeg?auto=compress&cs=tinysrgb&w=400'
  },
  {
    id: 5,
    title: 'Mobile App UI',
    category: 'App Design',
    image: 'https://images.pexels.com/photos/196644/pexels-photo-196644.jpeg?auto=compress&cs=tinysrgb&w=400'
  },
  {
    id: 6,
    title: 'Corporate Identity',
    category: 'Branding',
    image: 'https://images.pexels.com/photos/1640774/pexels-photo-1640774.jpeg?auto=compress&cs=tinysrgb&w=400'
  }
]

const testimonials = [
  {
    id: 1,
    text: 'Sribu helped us create an amazing logo that perfectly represents our brand. The contest format gave us so many great options to choose from!',
    author: 'Sarah Johnson',
    company: 'TechStart Inc.'
  },
  {
    id: 2,
    text: 'The quality of designs we received was outstanding. Working with multiple designers through Sribu was much better than hiring just one freelancer.',
    author: 'Michael Chen',
    company: 'GreenLeaf Organic'
  },
  {
    id: 3,
    text: 'Fast, affordable, and high-quality designs. Sribu made our rebranding project smooth and successful.',
    author: 'Emma Rodriguez',
    company: 'Bright Future Consulting'
  }
]

const scrollToSection = (sectionId: string) => {
  const element = document.getElementById(sectionId)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
}

const handleSubmit = async () => {
  isSubmitting.value = true
  
  // Simulate API call
  setTimeout(() => {
    alert('Thank you for your interest! We\'ll send you the complete guide shortly.')
    email.value = ''
    isSubmitting.value = false
  }, 1000)
}
</script>

<style scoped>
/* Global Styles */
* {
  box-sizing: border-box;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 24px;
}

/* Header */
.header {
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(10px);
  position: fixed;
  top: 0;
  width: 100%;
  z-index: 1000;
  border-bottom: 1px solid #f1f5f9;
}

.header-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 16px 0;
}

.logo-text {
  font-size: 28px;
  font-weight: 700;
  color: #dc2626;
  margin: 0;
}

.tagline {
  font-size: 12px;
  color: #64748b;
  margin: 0;
}

.nav {
  display: flex;
  gap: 32px;
  align-items: center;
}

.nav-link {
  color: #334155;
  text-decoration: none;
  font-weight: 500;
  transition: color 0.3s ease;
}

.nav-link:hover {
  color: #dc2626;
}

.cta-button {
  background: #dc2626;
  color: white;
  padding: 12px 24px;
  border-radius: 8px;
  transition: all 0.3s ease;
}

.cta-button:hover {
  background: #b91c1c;
  color: white;
}

/* Hero Section */
.hero {
  background: linear-gradient(135deg, #f8fafc 0%, #f1f5f9 100%);
  padding: 120px 0 80px;
  min-height: 100vh;
  display: flex;
  align-items: center;
}

.hero-content {
  max-width: 600px;
}

.hero-title {
  font-size: 56px;
  font-weight: 700;
  color: #1e293b;
  line-height: 1.1;
  margin-bottom: 24px;
}

.hero-subtitle {
  font-size: 20px;
  color: #64748b;
  line-height: 1.6;
  margin-bottom: 40px;
}

.hero-actions {
  display: flex;
  gap: 16px;
  margin-bottom: 40px;
}

.btn {
  padding: 16px 32px;
  border-radius: 8px;
  font-weight: 600;
  font-size: 16px;
  cursor: pointer;
  transition: all 0.3s ease;
  border: none;
  text-decoration: none;
  display: inline-block;
  text-align: center;
}

.btn-primary {
  background: #dc2626;
  color: white;
}

.btn-primary:hover {
  background: #b91c1c;
  transform: translateY(-2px);
}

.btn-secondary {
  background: transparent;
  color: #dc2626;
  border: 2px solid #dc2626;
}

.btn-secondary:hover {
  background: #dc2626;
  color: white;
}

.btn-outline {
  background: transparent;
  color: #64748b;
  border: 2px solid #e2e8f0;
}

.btn-outline:hover {
  border-color: #dc2626;
  color: #dc2626;
}

.hero-visual {
  flex: 1;
  display: flex;
  justify-content: center;
  align-items: center;
}

.design-cards {
  position: relative;
  width: 300px;
  height: 300px;
}

.design-card {
  position: absolute;
  width: 120px;
  height: 120px;
  background: white;
  border-radius: 12px;
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 600;
  color: #334155;
  transition: transform 0.3s ease;
}

.design-card:hover {
  transform: translateY(-8px);
}

.card-1 {
  top: 0;
  left: 0;
  background: linear-gradient(135deg, #dc2626, #ef4444);
  color: white;
}

.card-2 {
  top: 50px;
  right: 0;
  background: linear-gradient(135deg, #1e293b, #334155);
  color: white;
}

.card-3 {
  bottom: 0;
  left: 50px;
  background: linear-gradient(135deg, #f8fafc, #e2e8f0);
}

/* Section Styles */
section {
  padding: 80px 0;
}

.section-header {
  text-align: center;
  margin-bottom: 64px;
}

.section-title {
  font-size: 40px;
  font-weight: 700;
  color: #1e293b;
  margin-bottom: 16px;
}

.section-subtitle {
  font-size: 18px;
  color: #64748b;
  max-width: 600px;
  margin: 0 auto;
}

/* Problem Section */
.problem-section {
  background: #f8fafc;
}

.problem-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 40px;
}

.problem-item {
  text-align: center;
  padding: 40px 24px;
  background: white;
  border-radius: 16px;
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.05);
  transition: transform 0.3s ease;
}

.problem-item:hover {
  transform: translateY(-4px);
}

.problem-icon {
  font-size: 48px;
  margin-bottom: 24px;
}

.problem-item h3 {
  font-size: 24px;
  font-weight: 600;
  color: #1e293b;
  margin-bottom: 16px;
}

.problem-item p {
  color: #64748b;
  line-height: 1.6;
}

/* Comparison Table */
.comparison-section {
  background: white;
}

.comparison-table {
  background: white;
  border-radius: 16px;
  overflow: hidden;
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
}

.comparison-header {
  display: grid;
  grid-template-columns: 2fr 1fr 1fr 1fr 1fr;
  background: #f8fafc;
  font-weight: 600;
  color: #1e293b;
}

.comparison-header > div {
  padding: 20px;
  border-right: 1px solid #e2e8f0;
}

.sribu-column {
  background: #dc2626;
  color: white;
}

.comparison-row {
  display: grid;
  grid-template-columns: 2fr 1fr 1fr 1fr 1fr;
  border-bottom: 1px solid #e2e8f0;
}

.comparison-row > div {
  padding: 20px;
  border-right: 1px solid #e2e8f0;
}

.feature-cell {
  font-weight: 600;
  color: #1e293b;
}

.service-cell {
  color: #64748b;
  text-align: center;
}

.sribu-cell {
  background: #fef2f2;
  color: #dc2626;
  font-weight: 600;
  text-align: center;
}

/* Portfolio Section */
.portfolio-section {
  background: #f8fafc;
}

.portfolio-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 32px;
  margin-bottom: 64px;
}

.portfolio-item {
  background: white;
  border-radius: 16px;
  overflow: hidden;
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.05);
  transition: transform 0.3s ease;
}

.portfolio-item:hover {
  transform: translateY(-8px);
}

.portfolio-image {
  position: relative;
  overflow: hidden;
}

.portfolio-image img {
  width: 100%;
  height: 200px;
  object-fit: cover;
  transition: transform 0.3s ease;
}

.portfolio-item:hover .portfolio-image img {
  transform: scale(1.05);
}

.portfolio-overlay {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  background: linear-gradient(transparent, rgba(0, 0, 0, 0.8));
  color: white;
  padding: 24px;
}

.portfolio-overlay h4 {
  margin: 0 0 8px 0;
  font-size: 18px;
  font-weight: 600;
}

.portfolio-overlay p {
  margin: 0;
  color: #e2e8f0;
}

.portfolio-cta {
  text-align: center;
}

/* Testimonials */
.testimonials-section {
  background: white;
}

.testimonials-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 32px;
  margin-bottom: 64px;
}

.testimonial-card {
  background: #f8fafc;
  padding: 32px;
  border-radius: 16px;
  border-left: 4px solid #dc2626;
}

.stars {
  color: #fbbf24;
  font-size: 20px;
  margin-bottom: 16px;
}

.testimonial-text {
  font-size: 16px;
  line-height: 1.6;
  color: #334155;
  margin-bottom: 24px;
}

.testimonial-author strong {
  color: #1e293b;
  display: block;
  margin-bottom: 4px;
}

.testimonial-author span {
  color: #64748b;
  font-size: 14px;
}

.testimonials-cta {
  text-align: center;
}

/* CTA Section */
.cta-section {
  background: linear-gradient(135deg, #dc2626, #b91c1c);
  color: white;
  text-align: center;
}

.cta-title {
  font-size: 40px;
  font-weight: 700;
  margin-bottom: 16px;
}

.cta-subtitle {
  font-size: 18px;
  margin-bottom: 40px;
  opacity: 0.9;
}

.cta-form {
  max-width: 500px;
  margin: 0 auto 24px;
}

.form-group {
  display: flex;
  gap: 16px;
}

.form-input {
  flex: 1;
  padding: 16px 20px;
  border: none;
  border-radius: 8px;
  font-size: 16px;
  background: rgba(255, 255, 255, 0.95);
}

.form-input:focus {
  outline: none;
  background: white;
}

.cta-note {
  opacity: 0.8;
  font-size: 14px;
}

/* About Section */
.about-section {
  background: #f8fafc;
}

.about-text {
  font-size: 18px;
  line-height: 1.7;
  color: #334155;
  max-width: 800px;
  margin: 0 auto 64px;
  text-align: center;
}

.stats-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 40px;
}

.stat-item {
  text-align: center;
}

.stat-number {
  font-size: 48px;
  font-weight: 700;
  color: #dc2626;
  margin-bottom: 8px;
}

.stat-label {
  color: #64748b;
  font-weight: 600;
}

/* Footer */
.footer {
  background: #1e293b;
  color: #e2e8f0;
  padding: 64px 0 24px;
}

.footer-content {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 40px;
  margin-bottom: 40px;
}

.footer-section h3,
.footer-section h4 {
  color: white;
  margin-bottom: 16px;
}

.footer-section h3 {
  font-size: 24px;
  color: #dc2626;
}

.footer-section ul {
  list-style: none;
  padding: 0;
}

.footer-section ul li {
  margin-bottom: 8px;
}

.footer-section ul li a {
  color: #94a3b8;
  text-decoration: none;
  transition: color 0.3s ease;
}

.footer-section ul li a:hover {
  color: #dc2626;
}

.footer-bottom {
  border-top: 1px solid #334155;
  padding-top: 24px;
  text-align: center;
  color: #94a3b8;
}

/* Responsive Design */
@media (max-width: 768px) {
  .hero {
    flex-direction: column;
    text-align: center;
    padding: 100px 0 60px;
  }
  
  .hero-title {
    font-size: 40px;
  }
  
  .hero-actions {
    flex-direction: column;
    align-items: center;
  }
  
  .btn {
    width: 100%;
    max-width: 300px;
  }
  
  .comparison-header,
  .comparison-row {
    grid-template-columns: 1fr;
  }
  
  .comparison-header > div,
  .comparison-row > div {
    border-right: none;
    border-bottom: 1px solid #e2e8f0;
  }
  
  .form-group {
    flex-direction: column;
  }
  
  .nav {
    display: none;
  }
  
  .section-title {
    font-size: 32px;
  }
}

@media (max-width: 480px) {
  .container {
    padding: 0 16px;
  }
  
  .hero-title {
    font-size: 32px;
  }
  
  .section-title {
    font-size: 28px;
  }
  
  .cta-title {
    font-size: 32px;
  }
}
</style>