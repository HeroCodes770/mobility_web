<template>
  <div>
    <!-- Hero Section -->
    <section class="hero">
      <div class="container">
        <div class="hero-content fade-in-up">
          <h1>Empowering Ghana's Streets: Join the Movement for Active Mobility</h1>
          <p class="subtitle">
            We're a passionate community promoting trails, greenways, and complete streets 
            to build healthier, greener, and more connected communities.
          </p>
          <NuxtLink to="/programs" class="btn-primary">
            Get Involved
          </NuxtLink>
        </div>
      </div>
    </section>

    <!-- Quick Overview Section -->
    <section class="py-lg">
      <div class="container">
        <div class="text-center mb-lg fade-in">
          <h2>Welcome to Our Community!</h2>
          <p class="subtitle" style="color: var(--neutral-gray); font-size: 1.1rem; max-width: 800px; margin: 0 auto;">
            Inspired by the need for sustainable transport in Ghana, we advocate for active mobility options 
            like walking, cycling, and green trails. Our efforts create safer streets, boost wellness, 
            protect the environment, and strengthen local economies.
          </p>
        </div>

        <!-- Key Stats/Highlights -->
        <div class="stats-grid">
          <div class="stat-item fade-in" v-for="(stat, index) in stats" :key="index" :style="{ animationDelay: `${index * 0.2}s` }">
            <div class="stat-number">{{ stat.number }}</div>
            <div class="stat-label">{{ stat.label }}</div>
          </div>
        </div>
      </div>
    </section>

    <!-- Featured Sections Teaser -->
    <section class="py-lg" style="background-color: white;">
      <div class="container">
        <h2 class="text-center mb-lg">Our Impact Areas</h2>
        <div class="card-grid">
          <div class="card fade-in-up" v-for="(feature, index) in features" :key="index" :style="{ animationDelay: `${index * 0.3}s` }">
            <img :src="feature.image" :alt="feature.title" loading="lazy">
            <h3>{{ feature.title }}</h3>
            <p>{{ feature.description }}</p>
            <NuxtLink :to="feature.link" class="btn-secondary">
              Learn More
            </NuxtLink>
          </div>
        </div>
      </div>
    </section>

    <!-- Mission Preview -->
    <section class="py-lg" style="background: linear-gradient(135deg, var(--primary-green), var(--secondary-blue)); color: white;">
      <div class="container">
        <div class="text-center">
          <h2 style="color: white; margin-bottom: var(--spacing-md);">Our Mission in Action</h2>
          <p style="font-size: 1.2rem; max-width: 600px; margin: 0 auto var(--spacing-lg) auto; opacity: 0.95;">
            Through our Eno Bike initiative, we're connecting communities, promoting education, 
            and creating sustainable transport solutions that benefit all Ghanaians.
          </p>
          <div style="display: flex; gap: var(--spacing-md); justify-content: center; flex-wrap: wrap;">
            <NuxtLink to="/vision-mission" class="btn-primary" style="background-color: var(--primary-gold); color: var(--neutral-gray);">
              Our Vision
            </NuxtLink>
            <NuxtLink to="/programs" class="btn-secondary" style="border-color: white; color: white;">
              View Programs
            </NuxtLink>
          </div>
        </div>
      </div>
    </section>

    <!-- Latest News/Blog Preview -->
    <section class="py-lg">
      <div class="container">
        <div class="text-center mb-lg">
          <h2>Latest Updates</h2>
          <p>Stay informed about our recent activities and upcoming events</p>
        </div>
        <div class="card-grid">
          <div class="card fade-in-up" v-for="(news, index) in latestNews" :key="index" :style="{ animationDelay: `${index * 0.2}s` }">
            <img :src="news.image" :alt="news.title" loading="lazy">
            <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: var(--spacing-xs);">
              <small style="color: var(--secondary-blue); font-weight: 600;">{{ news.date }}</small>
              <span style="background-color: var(--primary-gold); color: var(--neutral-gray); padding: 4px 8px; border-radius: 4px; font-size: 0.75rem; font-weight: 600;">{{ news.category }}</span>
            </div>
            <h3>{{ news.title }}</h3>
            <p>{{ news.excerpt }}</p>
            <a href="#" class="btn-secondary" style="margin-top: var(--spacing-sm);">
              Read More
            </a>
          </div>
        </div>
      </div>
    </section>

    <!-- Call to Action -->
    <section class="py-lg" style="background-color: var(--neutral-white); border-top: 3px solid var(--primary-gold);">
      <div class="container text-center">
        <h2 style="color: var(--primary-green);">Ready to Make a Difference?</h2>
        <p style="font-size: 1.1rem; margin-bottom: var(--spacing-lg); max-width: 600px; margin-left: auto; margin-right: auto;">
          Join our growing community of advocates working to transform Ghana's streets 
          into safe, sustainable, and vibrant spaces for everyone.
        </p>
        <div style="display: flex; gap: var(--spacing-md); justify-content: center; flex-wrap: wrap;">
          <NuxtLink to="/contact" class="btn-primary">
            Join Our Community
          </NuxtLink>
          <NuxtLink to="/about" class="btn-secondary">
            Learn About Us
          </NuxtLink>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

// SEO Meta
useHead({
  title: 'Home - Active Mobility Ghana',
  meta: [
    {
      name: 'description',
      content: 'Join Ghana\'s movement for active mobility, sustainable transport, and complete streets. Building healthier, greener communities through trails and greenways.'
    }
  ]
})

// Stats data
const stats = ref([
  { number: '500+', label: 'Community Members' },
  { number: '25km', label: 'Trails Promoted' },
  { number: '12', label: 'Active Programs' },
  { number: '8', label: 'Partner Organizations' }
])

// Featured sections
const features = ref([
  {
    title: 'Our Vision',
    description: 'Building connected, sustainable communities through active transport solutions that benefit everyone in Ghana.',
    image: 'https://images.unsplash.com/photo-1544620347-c4fd4a3d5957?ixlib=rb-4.0.3&auto=format&fit=crop&w=500&q=80',
    link: '/vision-mission'
  },
  {
    title: 'Our Mission',
    description: 'Promoting active mobility, education, and community empowerment through the Eno Bike initiative and beyond.',
    image: 'https://images.unsplash.com/photo-1571068316344-75bc76f77890?ixlib=rb-4.0.3&auto=format&fit=crop&w=500&q=80',
    link: '/vision-mission'
  },
  {
    title: 'Our Programs',
    description: 'From bike-sharing pilots to trail development, discover how we\'re making active mobility accessible to all.',
    image: 'https://images.unsplash.com/photo-1558618666-fcd25c85cd64?ixlib=rb-4.0.3&auto=format&fit=crop&w=500&q=80',
    link: '/programs'
  }
])

// Latest news
const latestNews = ref([
  {
    title: 'Successful Bike Safety Workshop in Kumasi',
    excerpt: 'Over 100 participants learned essential cycling safety skills and advocacy techniques in our recent community workshop.',
    image: 'https://images.unsplash.com/photo-1544191696-15693072b5d5?ixlib=rb-4.0.3&auto=format&fit=crop&w=500&q=80',
    date: 'January 15, 2025',
    category: 'Workshop'
  },
  {
    title: 'New Greenway Project Launched in Accra',
    excerpt: 'We\'re excited to announce our partnership with local authorities to develop a 5km greenway connecting three communities.',
    image: 'https://images.unsplash.com/photo-1449824913935-59a10b8d2000?ixlib=rb-4.0.3&auto=format&fit=crop&w=500&q=80',
    date: 'January 10, 2025',
    category: 'Project'
  },
  {
    title: 'Eno Bike Initiative Reaches 1000 Users',
    excerpt: 'Our flagship program has successfully engaged over 1000 community members in sustainable transport advocacy.',
    image: 'https://images.unsplash.com/photo-1558437268-a2fbdcf06b6e?ixlib=rb-4.0.3&auto=format&fit=crop&w=500&q=80',
    date: 'January 5, 2025',
    category: 'Milestone'
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
.subtitle {
  font-size: 1.2rem;
  line-height: 1.6;
}

/* Hover effects for cards */
.card:hover h3 {
  color: var(--accent-orange);
  transition: color 0.3s ease;
}

/* Stats animation */
.stat-item:hover .stat-number {
  transform: scale(1.1);
  transition: transform 0.3s ease;
}
</style>
