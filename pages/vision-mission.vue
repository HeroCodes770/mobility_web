<template>
  <div>
    <!-- Hero Section -->
    <section class="hero" style="min-height: 60vh; background-image: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)), url(/2025-09-01-15.09.36.jpg);">
      <div class="container">
        <div class="hero-content fade-in-up">
          <h1>Vision & Mission</h1>
          <p class="subtitle">
            Inspiring a sustainable future where active mobility transforms communities, 
            promotes wellness, and creates connected spaces for all Ghanaians.
          </p>
        </div>
      </div>
    </section>

    <!-- Vision Section -->
    <section class="py-lg">
      <div class="container">
        <div class="vision-section fade-in">
          <div class="vision-content">
            <div class="section-header">
              <span class="section-tag">Our Vision</span>
              <h2>A Connected & Sustainable Ghana</h2>
            </div>
            
            <div class="vision-grid">
              <div class="vision-text">
                <p style="font-size: 1.2rem; line-height: 1.7; margin-bottom: var(--spacing-md);">
                  We envision a Ghana where active transport is the norm within connected and sustainable communities. 
                  Our collective efforts are making a positive impact on wellness, the environment, our streets, and the economy.
                </p>
                
                <p style="font-size: 1.1rem; line-height: 1.6;">
                  Imagine cities and towns buzzing with cyclists, walkers, and vibrant green spaces – free from excessive 
                  pollution and traffic hazards. We're committed to fostering a culture of movement that benefits everyone, 
                  from urban dwellers in Accra to rural communities across the nation.
                </p>
                
                <div class="vision-highlights">
                  <div class="highlight-item" v-for="(highlight, index) in visionHighlights" :key="index">
                    <div class="highlight-icon">
                      <i :class="highlight.icon"></i>
                    </div>
                    <div>
                      <h4>{{ highlight.title }}</h4>
                      <p>{{ highlight.description }}</p>
                    </div>
                  </div>
                </div>
              </div>
              
              <div class="vision-visual">
                                 <div class="vision-image-container">
                   <div 
                     class="vision-image"
                     style="background-image: url(/2025-09-01-15.10.01.jpg); width: 100%; height: 400px; background-size: cover; background-position: center;"
                   ></div>
                  <div class="vision-overlay">
                    <div class="vision-stat">
                      <span class="stat-number">2030</span>
                      <span class="stat-label">Vision Target</span>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Mission Section -->
    <section class="py-lg" style="background: linear-gradient(135deg, var(--primary-green), var(--secondary-blue));">
      <div class="container">
        <div class="mission-section fade-in">
          <div class="section-header text-center" style="margin-bottom: var(--spacing-xl);">
            <span class="section-tag" style="background-color: var(--primary-gold); color: var(--neutral-gray);">Our Mission</span>
            <h2 style="color: white; margin-top: var(--spacing-sm);">Empowering Communities Through Action</h2>
          </div>

          <div class="mission-content">
            <div class="mission-intro">
              <p style="font-size: 1.2rem; color: rgba(255, 255, 255, 0.95); text-align: center; max-width: 800px; margin: 0 auto var(--spacing-lg) auto; line-height: 1.7;">
                At the heart of our work is the <strong style="color: var(--primary-gold);">Eno Bike initiative</strong>, 
                which promotes active mobility options like cycling and walking. We connect and empower communities 
                through education, planning, and engagement.
              </p>
            </div>

            <div class="mission-pillars">
              <div class="pillar-card fade-in-up" v-for="(pillar, index) in missionPillars" :key="index" :style="{ animationDelay: `${index * 0.2}s` }">
                <div class="pillar-icon">
                  <i :class="pillar.icon"></i>
                </div>
                <h3>{{ pillar.title }}</h3>
                <p>{{ pillar.description }}</p>
                <ul class="pillar-activities">
                  <li v-for="activity in pillar.activities" :key="activity">{{ activity }}</li>
                </ul>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- How We Achieve This Section -->
    <section class="py-lg">
      <div class="container">
        <div class="text-center mb-lg fade-in">
          <h2>How We Achieve Our Mission</h2>
          <p style="max-width: 700px; margin: 0 auto; font-size: 1.1rem; color: var(--neutral-gray);">
            Through strategic initiatives and community partnerships, we're creating lasting change across Ghana.
          </p>
        </div>

        <div class="achievement-methods">
                     <div class="method-item fade-in-up" v-for="(method, index) in achievementMethods" :key="index" :style="{ animationDelay: `${index * 0.15}s` }">
             <div class="method-visual" :style="{ backgroundImage: `url(/${method.image})` }">
             </div>
            <div class="method-content">
              <h3>{{ method.title }}</h3>
              <p>{{ method.description }}</p>
              <div class="method-metrics">
                <div class="metric" v-for="metric in method.metrics" :key="metric.label">
                  <span class="metric-value">{{ metric.value }}</span>
                  <span class="metric-label">{{ metric.label }}</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Impact Metrics Section -->
    <section class="py-lg" style="background-color: white;">
      <div class="container">
        <div class="text-center mb-lg fade-in">
          <h2>Our Impact So Far</h2>
          <p style="max-width: 600px; margin: 0 auto; font-size: 1.1rem;">
            Tracking our progress toward building sustainable, connected communities across Ghana.
          </p>
        </div>

        <div class="impact-dashboard">
          <div class="impact-category fade-in-up" v-for="(category, index) in impactCategories" :key="index" :style="{ animationDelay: `${index * 0.1}s` }">
            <div class="category-header">
              <i :class="category.icon"></i>
              <h3>{{ category.title }}</h3>
            </div>
            <div class="category-metrics">
              <div class="impact-metric" v-for="metric in category.metrics" :key="metric.label">
                <div class="metric-circle" :style="{ background: `conic-gradient(var(--primary-green) ${metric.percentage}%, #e0e0e0 0%)` }">
                  <div class="metric-inner">
                    <span class="metric-number">{{ metric.value }}</span>
                  </div>
                </div>
                <span class="metric-description">{{ metric.label }}</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Call to Action -->
    <section class="py-lg" style="background: linear-gradient(45deg, var(--primary-gold), var(--accent-orange));">
      <div class="container text-center">
        <div class="fade-in">
          <h2 style="color: white; margin-bottom: var(--spacing-md);">Join Our Vision for Ghana's Future</h2>
          <p style="color: rgba(255, 255, 255, 0.95); font-size: 1.2rem; max-width: 600px; margin: 0 auto var(--spacing-lg) auto;">
            Together, we can create the connected, sustainable communities that Ghana deserves. 
            Your support makes our vision a reality.
          </p>
          <div style="display: flex; gap: var(--spacing-md); justify-content: center; flex-wrap: wrap;">
            <NuxtLink to="/programs" class="btn-primary" style="background-color: white; color: var(--primary-green); font-size: 1.1rem;">
              Explore Our Programs
            </NuxtLink>
            <NuxtLink to="/contact" class="btn-secondary" style="border-color: white; color: white;">
              Get Involved Today
            </NuxtLink>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

// SEO Meta
useHead({
  title: 'Vision & Mission - Active Mobility Ghana',
  meta: [
    {
      name: 'description',
      content: 'Discover Active Mobility Ghana\'s vision for sustainable transport and our mission to empower communities through the Eno Bike initiative and active mobility programs.'
    }
  ]
})

// Vision highlights
const visionHighlights = ref([
  {
    title: 'Connected Communities',
    description: 'Safe, accessible pathways linking neighborhoods and economic centers',
    icon: 'fas fa-network-wired'
  },
  {
    title: 'Sustainable Transport',
    description: 'Eco-friendly mobility options that reduce emissions and promote health',
    icon: 'fas fa-leaf'
  },
  {
    title: 'Economic Growth',
    description: 'Thriving local economies supported by sustainable tourism and reduced transport costs',
    icon: 'fas fa-chart-line'
  },
  {
    title: 'Cultural Movement',
    description: 'A nationwide shift toward active, healthy lifestyles for all Ghanaians',
    icon: 'fas fa-users'
  }
])

// Mission pillars
const missionPillars = ref([
  {
    title: 'Education',
    description: 'Building awareness and skills for safe, sustainable transport',
    icon: 'fas fa-graduation-cap',
    activities: [
      'Hosting community workshops and training sessions',
      'School programs teaching cycling safety',
      'Public awareness campaigns on active mobility benefits'
    ]
  },
  {
    title: 'Planning',
    description: 'Collaborative design for inclusive, accessible infrastructure',
    icon: 'fas fa-drafting-compass',
    activities: [
      'Urban planning for bike lanes and pedestrian paths',
      'Complete streets design consultations',
      'Community input sessions for infrastructure projects'
    ]
  },
  {
    title: 'Engagement',
    description: 'Building networks and advocating for policy change',
    icon: 'fas fa-handshake',
    activities: [
      'Organizing community rides and events',
      'Advocacy for bike-friendly policies',
      'Partnership building with local organizations'
    ]
  }
])

// Achievement methods
const achievementMethods = ref([
  {
    title: 'Community Programs',
    description: 'From weekly cycling tours to embassy partnerships, we create hands-on opportunities for community involvement.',
    image: '2025-09-01-15.09.51.jpg',
    metrics: [
      { value: '6', label: 'Major Events' },
      { value: '200+', label: 'Participants' }
    ]
  },
  {
    title: 'International Partnerships',
    description: 'Building relationships with embassies and international organizations to promote cycling culture and diplomatic connections.',
    image: '2025-09-01-15.10.17.jpg',
    metrics: [
      { value: '3', label: 'Embassy Partners' },
      { value: '5', label: 'Countries Engaged' }
    ]
  },
  {
    title: 'Community Impact',
    description: 'Creating lasting change through education, training, and community engagement across Ghana.',
    image: '2025-09-01-15.10.36.jpg',
    metrics: [
      { value: '17', label: 'Photo Moments' },
      { value: '100%', label: 'Event Success' }
    ]
  }
])

// Impact categories
const impactCategories = ref([
  {
    title: 'Community',
    icon: 'fas fa-users',
    metrics: [
      { value: '150+', label: 'Active Members', percentage: 75 },
      { value: '4', label: 'Major Events', percentage: 80 }
    ]
  },
  {
    title: 'Partnerships',
    icon: 'fas fa-handshake',
    metrics: [
      { value: '3', label: 'Embassy Partners', percentage: 70 },
      { value: '2', label: 'Cities Reached', percentage: 60 }
    ]
  },
  {
    title: 'Advocacy',
    icon: 'fas fa-megaphone',
    metrics: [
      { value: '100%', label: 'Event Success Rate', percentage: 90 },
      { value: '50+', label: 'Media Mentions', percentage: 65 }
    ]
  }
])

// Add intersection observer for animations
onMounted(() => {
  const observerOptions = {
    threshold: 0.1,
    rootMargin: '0px 0px -50px 0px'
  }

  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.style.opacity = '1'
        entry.target.style.transform = 'translateY(0)'
      }
    })
  }, observerOptions)

  // Observe all fade-in elements
  document.querySelectorAll('.fade-in, .fade-in-up').forEach(el => {
    el.style.opacity = '0'
    el.style.transform = 'translateY(30px)'
    el.style.transition = 'all 0.8s ease-out'
    observer.observe(el)
  })
})
</script>

<style scoped>
/* Section tags */
.section-tag {
  display: inline-block;
  background-color: var(--primary-gold);
  color: var(--neutral-gray);
  padding: 8px 16px;
  border-radius: 20px;
  font-size: 0.9rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

/* Vision section */
.vision-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: var(--spacing-xl);
  align-items: center;
  margin-top: var(--spacing-lg);
}

.vision-highlights {
  margin-top: var(--spacing-lg);
}

.highlight-item {
  display: flex;
  align-items: flex-start;
  gap: var(--spacing-md);
  margin-bottom: var(--spacing-md);
  padding: var(--spacing-sm);
  background: rgba(46, 125, 50, 0.05);
  border-radius: 8px;
  transition: all 0.3s ease;
}

.highlight-item:hover {
  background: rgba(46, 125, 50, 0.1);
  transform: translateX(5px);
}

.highlight-icon {
  width: 50px;
  height: 50px;
  background: linear-gradient(135deg, var(--primary-green), var(--secondary-blue));
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  font-size: 1.2rem;
  flex-shrink: 0;
}

.highlight-item h4 {
  color: var(--primary-green);
  margin-bottom: var(--spacing-xs);
  font-size: 1.1rem;
}

.vision-image-container {
  position: relative;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 12px 30px rgba(0, 0, 0, 0.15);
}

.vision-image-container img {
  width: 100%;
  height: 400px;
  object-fit: cover;
}

.vision-overlay {
  position: absolute;
  bottom: 20px;
  right: 20px;
  background: rgba(255, 255, 255, 0.95);
  padding: var(--spacing-md);
  border-radius: 12px;
  text-align: center;
}

.vision-stat .stat-number {
  display: block;
  font-size: 2rem;
  font-weight: 700;
  color: var(--primary-green);
  font-family: 'Poppins', sans-serif;
}

.vision-stat .stat-label {
  font-size: 0.9rem;
  color: var(--neutral-gray);
  font-weight: 600;
}

/* Mission pillars */
.mission-pillars {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: var(--spacing-lg);
  margin-top: var(--spacing-lg);
}

.pillar-card {
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  border-radius: 16px;
  padding: var(--spacing-lg);
  text-align: center;
  border: 1px solid rgba(255, 255, 255, 0.2);
  transition: all 0.3s ease;
}

.pillar-card:hover {
  background: rgba(255, 255, 255, 0.2);
  transform: translateY(-5px);
}

.pillar-icon {
  width: 80px;
  height: 80px;
  background: var(--primary-gold);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto var(--spacing-md) auto;
  font-size: 2rem;
  color: var(--neutral-gray);
}

.pillar-card h3 {
  color: white;
  margin-bottom: var(--spacing-sm);
  font-size: 1.5rem;
}

.pillar-card p {
  color: rgba(255, 255, 255, 0.9);
  margin-bottom: var(--spacing-md);
  font-size: 1.1rem;
}

.pillar-activities {
  list-style: none;
  padding: 0;
  text-align: left;
}

.pillar-activities li {
  color: rgba(255, 255, 255, 0.8);
  padding: var(--spacing-xs) 0;
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
  position: relative;
  padding-left: 20px;
}

.pillar-activities li::before {
  content: '✓';
  position: absolute;
  left: 0;
  color: var(--primary-gold);
  font-weight: bold;
}

/* Achievement methods */
.achievement-methods {
  display: flex;
  flex-direction: column;
  gap: var(--spacing-xl);
  margin-top: var(--spacing-lg);
}

.method-item {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: var(--spacing-lg);
  align-items: center;
  background: white;
  border-radius: 16px;
  padding: var(--spacing-lg);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease;
}

.method-item:hover {
  transform: translateY(-3px);
  box-shadow: 0 12px 35px rgba(0, 0, 0, 0.15);
}

.method-item:nth-child(even) {
  grid-template-columns: 1fr 1fr;
}

.method-item:nth-child(even) .method-visual {
  order: 2;
}

.method-visual {
  width: 100%;
  height: 250px;
  background-size: cover;
  background-position: center;
  border-radius: 12px;
}

.method-content h3 {
  color: var(--primary-green);
  margin-bottom: var(--spacing-sm);
  font-size: 1.5rem;
}

.method-metrics {
  display: flex;
  gap: var(--spacing-md);
  margin-top: var(--spacing-md);
}

.metric {
  text-align: center;
  padding: var(--spacing-sm);
  background: rgba(46, 125, 50, 0.1);
  border-radius: 8px;
}

.metric-value {
  display: block;
  font-size: 1.5rem;
  font-weight: 700;
  color: var(--primary-green);
  font-family: 'Poppins', sans-serif;
}

.metric-label {
  font-size: 0.9rem;
  color: var(--neutral-gray);
}

/* Impact dashboard */
.impact-dashboard {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: var(--spacing-lg);
  margin-top: var(--spacing-lg);
}

.impact-category {
  background: white;
  border-radius: 16px;
  padding: var(--spacing-lg);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.1);
  text-align: center;
  transition: all 0.3s ease;
}

.impact-category:hover {
  transform: translateY(-5px);
  box-shadow: 0 12px 35px rgba(0, 0, 0, 0.15);
}

.category-header {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: var(--spacing-sm);
  margin-bottom: var(--spacing-lg);
}

.category-header i {
  font-size: 2rem;
  color: var(--primary-green);
}

.category-header h3 {
  color: var(--primary-green);
  margin: 0;
}

.category-metrics {
  display: flex;
  justify-content: space-around;
  gap: var(--spacing-md);
}

.impact-metric {
  text-align: center;
}

.metric-circle {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto var(--spacing-sm) auto;
  position: relative;
}

.metric-inner {
  width: 70px;
  height: 70px;
  background: white;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.metric-number {
  font-size: 1.2rem;
  font-weight: 700;
  color: var(--primary-green);
  font-family: 'Poppins', sans-serif;
}

.metric-description {
  font-size: 0.9rem;
  color: var(--neutral-gray);
  font-weight: 600;
}

/* Responsive design */
@media (max-width: 768px) {
  .vision-grid,
  .method-item {
    grid-template-columns: 1fr;
    gap: var(--spacing-md);
  }

  .method-item:nth-child(even) .method-visual {
    order: 0;
  }

  .mission-pillars {
    grid-template-columns: 1fr;
  }

  .category-metrics {
    flex-direction: column;
    align-items: center;
  }

  .method-metrics {
    justify-content: center;
  }
}
</style>
