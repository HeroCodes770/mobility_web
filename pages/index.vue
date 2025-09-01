<template>
  <div>
    <!-- Hero Section -->
    <section class="hero">
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

    <!-- Image Showcase Gallery -->
    <section class="py-lg" style="background-color: white;">
      <div class="container">
        <div class="text-center mb-lg fade-in">
          <h2>Our Community in Action</h2>
          <p style="max-width: 600px; margin: 0 auto; font-size: 1.1rem;">
            Take a visual journey through our events, partnerships, and community activities.
          </p>
        </div>
        
        <div class="image-showcase">
          <div class="showcase-item fade-in-up" v-for="(photo, index) in imageShowcase" :key="index" :style="{ animationDelay: `${index * 0.1}s` }">
            <div class="showcase-image" :style="{ backgroundImage: `url(/${photo.image})` }"></div>
            <div class="showcase-overlay">
              <h4>{{ photo.title }}</h4>
            </div>
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

// Recent events using actual events
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
    title: 'Community Weekly Cycling Tour',
    description: 'Our regular community cycling events that bring together cyclists of all levels for weekly tours around Accra.',
    image: '2025-09-01-15.09.51.jpg',
    date: 'Ongoing',
    category: 'Community',
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
  },
  {
    title: 'Team Building & Community Rides',
    description: 'Building stronger connections through regular cycling activities and team building exercises.',
    image: '2025-09-01-15.10.36.jpg',
    date: 'September 2024',
    category: 'Community',
    video: null
  },
  {
    title: 'Cycling Safety & Training Programs',
    description: 'Comprehensive safety training and cycling skills development for community members.',
    image: '2025-09-01-15.10.44.jpg',
    date: 'August 2024',
    category: 'Training',
    video: null
  }
])

// Image showcase for home page
const imageShowcase = ref([
  { image: '2025-09-01-15.09.17.jpg', title: 'Community Gathering' },
  { image: '2025-09-01-15.09.36.jpg', title: 'Team Formation' },
  { image: '2025-09-01-15.09.56.jpg', title: 'Event Preparation' },
  { image: '2025-09-01-15.10.31.jpg', title: 'Safety Training' },
  { image: '2025-09-01-15.10.39.jpg', title: 'Skill Development' },
  { image: '2025-09-01-15.10.47.jpg', title: 'Event Coordination' },
  { image: '2025-09-01-15.10.51.jpg', title: 'Community Engagement' },
  { image: '2025-09-01-15.10.55.jpg', title: 'Event Success' }
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

/* Image showcase gallery */
.image-showcase {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: var(--spacing-md);
  margin-top: var(--spacing-lg);
}

.showcase-item {
  position: relative;
  height: 200px;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease;
}

.showcase-item:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.15);
}

.showcase-image {
  width: 100%;
  height: 100%;
  background-size: cover;
  background-position: center;
  transition: transform 0.3s ease;
}

.showcase-item:hover .showcase-image {
  transform: scale(1.1);
}

.showcase-overlay {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  background: linear-gradient(transparent, rgba(0, 0, 0, 0.8));
  color: white;
  padding: var(--spacing-sm);
  text-align: center;
  transform: translateY(100%);
  transition: transform 0.3s ease;
}

.showcase-item:hover .showcase-overlay {
  transform: translateY(0);
}

.showcase-overlay h4 {
  color: white;
  margin: 0;
  font-size: 1rem;
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
