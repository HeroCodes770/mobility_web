<template>
  <div>
    <!-- Hero Section - Full Screen -->
    <section class="hero full-screen">
      <video class="hero-video" autoplay muted loop playsinline>
        <source src="/landing-video.mp4" type="video/mp4">
        Your browser does not support the video tag.
      </video>
      <div class="hero-overlay"></div>
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

    <!-- Rent a Bike Section -->
    <section class="py-lg" style="background: linear-gradient(135deg, var(--primary-green), var(--secondary-blue)); color: white;">
      <div class="container">
        <div class="text-center mb-lg fade-in">
          <h2 style="color: white; margin-bottom: var(--spacing-md);">Rent a Bike</h2>
          <p style="color: rgba(255, 255, 255, 0.9); max-width: 600px; margin: 0 auto; font-size: 1.1rem;">
            Experience the freedom of electric mobility with our convenient bike rental service.
          </p>
        </div>

        <div class="rent-features">
          <div class="feature-item fade-in-up" v-for="(feature, index) in rentFeatures" :key="index" :style="{ animationDelay: `${index * 0.2}s` }">
            <div class="feature-icon">
              <i :class="feature.icon"></i>
            </div>
            <h3 style="color: white;">{{ feature.title }}</h3>
            <p style="color: rgba(255, 255, 255, 0.9);">{{ feature.description }}</p>
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
            <div class="card-image" :style="{ backgroundImage: `url(/${feature.image})` }"></div>
            <h3>{{ feature.title }}</h3>
            <p>{{ feature.description }}</p>
            <NuxtLink :to="feature.link" class="btn-secondary">
              Learn More
            </NuxtLink>
          </div>
        </div>
      </div>
    </section>



    <!-- Latest Events Section -->
    <section class="py-lg">
      <div class="container">
        <div class="text-center mb-lg">
          <h2>Our Recent Events</h2>
          <p>Discover the exciting events and partnerships that are driving our mission forward</p>
        </div>
        <div class="card-grid">
          <div class="card fade-in-up" v-for="(event, index) in recentEvents" :key="index" :style="{ animationDelay: `${index * 0.2}s` }">
            <div class="card-image" :style="{ backgroundImage: `url(/${event.image})` }"></div>
            <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: var(--spacing-xs);">
              <small style="color: var(--secondary-blue); font-weight: 600;">{{ event.date }}</small>
              <span style="background-color: var(--primary-gold); color: var(--neutral-gray); padding: 4px 8px; border-radius: 4px; font-size: 0.75rem; font-weight: 600;">{{ event.category }}</span>
            </div>
            <h3>{{ event.title }}</h3>
            <p>{{ event.description }}</p>
            <a v-if="event.video" href="#" class="btn-secondary" style="margin-top: var(--spacing-sm);" @click.prevent="playVideo(`/${event.video}`)">
              <i class="fas fa-play"></i> Watch Video
            </a>
            <a v-else href="#" class="btn-secondary" style="margin-top: var(--spacing-sm);">
              View Photos
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

    <!-- Video Modal -->
    <div v-if="showVideoModal" class="video-modal" @click="closeVideoModal">
      <div class="video-modal-content" @click.stop>
        <button class="video-modal-close" @click="closeVideoModal">
          <i class="fas fa-times"></i>
        </button>
        <video 
          :src="currentVideo" 
          controls 
          autoplay
          style="width: 100%; max-width: 800px; border-radius: 8px;"
        >
          Your browser does not support the video tag.
        </video>
      </div>
    </div>
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
  { number: '4', label: 'Major Events Held' },
  { number: '3', label: 'Embassy Partnerships' }
])

// Featured sections
const features = ref([
  {
    title: 'Our Vision',
    description: 'Building connected, sustainable communities through active transport solutions that benefit everyone in Ghana.',
    image: '2025-09-01-15.09.36.jpg',
    link: '/vision-mission'
  },
  {
    title: 'Our Mission',
    description: 'Promoting active mobility, education, and community empowerment through the Eno Bike initiative and beyond.',
    image: '2025-09-01-15.10.01.jpg',
    link: '/vision-mission'
  },
  {
    title: 'Our Programs',
    description: 'From bike-sharing pilots to trail development, discover how we\'re making active mobility accessible to all.',
    image: '2025-09-01-15.10.07.jpg',
    link: '/programs'
  }
])

// Recent events - only your 3 actual events
const recentEvents = ref([
  {
    title: 'Ride with the Israel Embassy - Bring the Hostages Home',
    description: 'A powerful solidarity ride with the Israel Embassy to raise awareness and bring attention to the hostages situation.',
    image: '2025-09-01-15.09.43.jpg',
    date: 'December 2024',
    category: 'Diplomatic',
    video: null
  },
  {
    title: 'Partnership with French Embassy - Ride with Team Europe',
    description: 'An exciting partnership event with the French Embassy featuring Team Europe for a special cycling event.',
    image: '2025-09-01-15.10.17.jpg',
    date: 'November 2024',
    category: 'Partnership',
    video: 'Partnership-with-French-Embassy.mp4'
  },
  {
    title: 'Cycling Tour to the Adomi Bridge',
    description: 'An adventurous cycling tour to the iconic Adomi Bridge, showcasing Ghana\'s beautiful landscapes and infrastructure.',
    image: '2025-09-01-15.10.27.jpg',
    date: 'October 2024',
    category: 'Adventure',
    video: null
  }
])

// Rent a bike features
const rentFeatures = ref([
  {
    title: 'Your Electric Bike at Home',
    description: 'Your electric bike, that you keep at your home, and ride when you want to.',
    icon: 'fas fa-bicycle'
  },
  {
    title: 'Flexible Payment Options',
    description: 'Pay monthly - or weekly, where available - for your e-bike. Theft Protection included, too.',
    icon: 'fas fa-coins'
  },
  {
    title: 'Best Way to Move Around',
    description: 'You\'re going to love riding an awesome Zygg e-bike, the best way to move around the city - and super fun, too!',
    icon: 'fas fa-map-marker-alt'
  },
  {
    title: 'Expert Maintenance Service',
    description: 'If you need a fix, our expert technicians will get you back riding quickly. A small fee for At-Home service applies.',
    icon: 'fas fa-tools'
  }
])

// Video modal state
const showVideoModal = ref(false)
const currentVideo = ref('')

const playVideo = (videoSrc) => {
  currentVideo.value = videoSrc
  showVideoModal.value = true
}

const closeVideoModal = () => {
  showVideoModal.value = false
  currentVideo.value = ''
}

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

/* Card image styling */
.card-image {
  width: 100%;
  height: 200px;
  background-size: cover;
  background-position: center;
  border-radius: 8px;
  margin-bottom: var(--spacing-sm);
  transition: transform 0.3s ease;
}

.card:hover .card-image {
  transform: scale(1.05);
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

/* Hero video background */
.hero-video {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  z-index: 1;
}

.hero-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5));
  z-index: 2;
}

.hero-content {
  position: relative;
  z-index: 3;
}

/* Full screen hero */
.hero.full-screen {
  min-height: 100vh;
}

/* Rent features */
.rent-features {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: var(--spacing-lg);
  margin-top: var(--spacing-lg);
}

.feature-item {
  text-align: center;
  padding: var(--spacing-lg);
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  border-radius: 16px;
  border: 1px solid rgba(255, 255, 255, 0.2);
  transition: all 0.3s ease;
}

.feature-item:hover {
  background: rgba(255, 255, 255, 0.2);
  transform: translateY(-5px);
}

.feature-icon {
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

.feature-item h3 {
  margin-bottom: var(--spacing-sm);
  font-size: 1.3rem;
}

.feature-item p {
  font-size: 1rem;
  line-height: 1.6;
}



/* Video modal styles */
.video-modal {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.9);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 2000;
  padding: var(--spacing-md);
}

.video-modal-content {
  position: relative;
  max-width: 90vw;
  max-height: 90vh;
}

.video-modal-close {
  position: absolute;
  top: -40px;
  right: 0;
  background: none;
  border: none;
  color: white;
  font-size: 1.5rem;
  cursor: pointer;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.3s ease;
}

.video-modal-close:hover {
  background: rgba(255, 255, 255, 0.2);
  color: var(--primary-gold);
}
</style>
