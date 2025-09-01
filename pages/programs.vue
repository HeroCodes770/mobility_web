<template>
  <div>
    <!-- Hero Section -->
    <section class="hero" style="min-height: 60vh; background-image: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)), url(/2025-09-01-15.10.01.jpg);">
      <div class="container">
        <div class="hero-content fade-in-up">
          <h1>Our Programs & Events</h1>
          <p class="subtitle">
            Discover the exciting events and partnerships that are driving our mission forward 
            and building a stronger cycling community in Ghana.
          </p>
        </div>
      </div>
    </section>

    <!-- Main Events Section -->
    <section class="py-lg">
      <div class="container">
        <div class="text-center mb-lg fade-in">
          <h2>Our Signature Events</h2>
          <p style="max-width: 700px; margin: 0 auto; font-size: 1.1rem;">
            From diplomatic partnerships to community rides, these events showcase our commitment 
            to promoting active mobility and building international connections.
          </p>
        </div>

        <div class="events-showcase">
          <div class="event-card fade-in-up" v-for="(event, index) in mainEvents" :key="index" :style="{ animationDelay: `${index * 0.2}s` }">
            <div class="event-image" :style="{ backgroundImage: `url(/${event.image})` }">
              <div class="event-category">{{ event.category }}</div>
              <div v-if="event.video" class="video-indicator">
                <i class="fas fa-play"></i>
              </div>
            </div>
            
            <div class="event-content">
              <h3>{{ event.title }}</h3>
              <p>{{ event.description }}</p>
              
              <div class="event-details">
                <div class="detail-item">
                  <i class="fas fa-calendar"></i>
                  <span>{{ event.date }}</span>
                </div>
                <div class="detail-item">
                  <i class="fas fa-map-marker-alt"></i>
                  <span>{{ event.location }}</span>
                </div>
                <div class="detail-item">
                  <i class="fas fa-users"></i>
                  <span>{{ event.participants }}</span>
                </div>
              </div>
              
              <div class="event-actions">
                <button v-if="event.video" class="btn-primary" @click="playVideo(event.video)">
                  <i class="fas fa-play"></i> Watch Video
                </button>
                <button class="btn-secondary">
                  View Gallery
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Community Programs Section -->
    <section class="py-lg" style="background: linear-gradient(135deg, var(--primary-green), var(--secondary-blue));">
      <div class="container">
        <div class="text-center mb-lg fade-in">
          <h2 style="color: white;">Community Programs</h2>
          <p style="color: rgba(255, 255, 255, 0.9); max-width: 600px; margin: 0 auto; font-size: 1.1rem;">
            Our ongoing initiatives that bring the cycling community together and promote active mobility.
          </p>
        </div>

        <div class="community-programs">
          <div class="program-card fade-in-up" v-for="(program, index) in communityPrograms" :key="index" :style="{ animationDelay: `${index * 0.15}s` }">
            <div class="program-icon">
              <i :class="program.icon"></i>
            </div>
            <h3 style="color: white;">{{ program.title }}</h3>
            <p style="color: rgba(255, 255, 255, 0.9);">{{ program.description }}</p>
            <div class="program-features">
              <span v-for="feature in program.features" :key="feature" class="feature-tag">
                {{ feature }}
              </span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Photo Gallery Section -->
    <section class="py-lg">
      <div class="container">
        <div class="text-center mb-lg fade-in">
          <h2>Event Gallery</h2>
          <p style="max-width: 600px; margin: 0 auto; font-size: 1.1rem;">
            Take a visual journey through our most memorable moments and events.
          </p>
        </div>

                 <div class="photo-gallery">
           <div class="gallery-item fade-in-up" v-for="(photo, index) in photoGallery" :key="index" :style="{ animationDelay: `${index * 0.1}s` }">
             <div class="gallery-image" :style="{ backgroundImage: `url(/${photo.image})` }"></div>
             <div class="photo-overlay">
               <p>{{ photo.caption }}</p>
             </div>
           </div>
         </div>
      </div>
    </section>

    <!-- Get Involved Section -->
    <section class="py-lg" style="background-color: var(--neutral-white);">
      <div class="container">
        <div class="get-involved-section fade-in">
          <div class="involvement-content">
            <h2>Join Our Next Event</h2>
            <p style="font-size: 1.2rem; margin-bottom: var(--spacing-lg);">
              Ready to be part of our next cycling adventure? Join our community and stay updated 
              on upcoming events and activities.
            </p>
            
            <div class="involvement-options">
              <div class="involvement-card" v-for="option in involvementOptions" :key="option.title">
                <div class="involvement-icon">
                  <i :class="option.icon"></i>
                </div>
                <h3>{{ option.title }}</h3>
                <p>{{ option.description }}</p>
                <NuxtLink :to="option.link" class="btn-secondary">
                  {{ option.buttonText }}
                </NuxtLink>
              </div>
            </div>
          </div>
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
  title: 'Programs & Events - Active Mobility Ghana',
  meta: [
    {
      name: 'description',
      content: 'Explore Active Mobility Ghana\'s programs including embassy partnerships, community rides, and cycling events across Ghana.'
    }
  ]
})

// Main events
const mainEvents = ref([
  {
    title: 'Ride with the Israel Embassy - Bring the Hostages Home',
    description: 'A powerful solidarity ride with the Israel Embassy to raise awareness and bring attention to the hostages situation. This event demonstrated our commitment to using cycling as a platform for important global causes.',
    image: '2025-09-01-15.09.43.jpg',
    date: 'December 2024',
    location: 'Accra, Ghana',
    participants: '50+ cyclists',
    category: 'Diplomatic Partnership',
    video: null
  },
  {
    title: 'Community Weekly Cycling Tour',
    description: 'Our regular community cycling events that bring together cyclists of all levels for weekly tours around Accra. These rides promote fitness, community building, and sustainable transport awareness.',
    image: '2025-09-01-15.09.51.jpg',
    date: 'Every Week',
    location: 'Various locations in Accra',
    participants: '20-30 cyclists',
    category: 'Community Event',
    video: null
  },
  {
    title: 'Partnership with French Embassy - Ride with Team Europe',
    description: 'An exciting partnership event with the French Embassy featuring Team Europe for a special cycling event. This collaboration strengthened our international connections and promoted European-Ghanaian cycling culture.',
    image: '2025-09-01-15.10.17.jpg',
    date: 'November 2024',
    location: 'Accra, Ghana',
    participants: '75+ cyclists',
    category: 'International Partnership',
    video: '/Partnership-with-French-Embassy.mp4'
  },
  {
    title: 'Cycling Tour to the Adomi Bridge',
    description: 'An adventurous cycling tour to the iconic Adomi Bridge, showcasing Ghana\'s beautiful landscapes and infrastructure. This long-distance ride demonstrated the potential for cycling tourism in Ghana.',
    image: '2025-09-01-15.10.27.jpg',
    date: 'October 2024',
    location: 'Adomi Bridge, Eastern Region',
    participants: '40+ cyclists',
    category: 'Adventure Tour',
    video: null
  }
])

// Community programs
const communityPrograms = ref([
  {
    title: 'Weekly Community Rides',
    description: 'Regular cycling events that bring together cyclists of all skill levels for enjoyable rides around Accra.',
    icon: 'fas fa-bicycle',
    features: ['All skill levels welcome', 'Safety training provided', 'Community building']
  },
  {
    title: 'Cycling Advocacy',
    description: 'Working with local authorities to promote cycling infrastructure and policies in Ghana.',
    icon: 'fas fa-megaphone',
    features: ['Policy engagement', 'Infrastructure advocacy', 'Public awareness']
  },
  {
    title: 'International Partnerships',
    description: 'Building relationships with embassies and international organizations to promote cycling culture.',
    icon: 'fas fa-handshake',
    features: ['Diplomatic relations', 'Cultural exchange', 'Global networking']
  }
])

// Photo gallery - showcasing all your amazing images
const photoGallery = ref([
  {
    image: '2025-09-01-15.09.17.jpg',
    caption: 'Community gathering and preparation'
  },
  {
    image: '2025-09-01-15.09.36.jpg',
    caption: 'Team formation and organization'
  },
  {
    image: '2025-09-01-15.09.43.jpg',
    caption: 'Israel Embassy partnership event'
  },
  {
    image: '2025-09-01-15.09.51.jpg',
    caption: 'Weekly community cycling tour'
  },
  {
    image: '2025-09-01-15.09.56.jpg',
    caption: 'Group preparation activities'
  },
  {
    image: '2025-09-01-15.10.01.jpg',
    caption: 'Adomi Bridge cycling adventure'
  },
  {
    image: '2025-09-01-15.10.07.jpg',
    caption: 'Cycling education and training'
  },
  {
    image: '2025-09-01-15.10.17.jpg',
    caption: 'French Embassy partnership'
  },
  {
    image: '2025-09-01-15.10.22.jpg',
    caption: 'Community outreach programs'
  },
  {
    image: '2025-09-01-15.10.27.jpg',
    caption: 'Adomi Bridge tour participants'
  },
  {
    image: '2025-09-01-15.10.31.jpg',
    caption: 'Safety training workshops'
  },
  {
    image: '2025-09-01-15.10.36.jpg',
    caption: 'Team building activities'
  },
  {
    image: '2025-09-01-15.10.39.jpg',
    caption: 'Advanced cycling techniques'
  },
  {
    image: '2025-09-01-15.10.44.jpg',
    caption: 'Group dynamics and coordination'
  },
  {
    image: '2025-09-01-15.10.47.jpg',
    caption: 'Event organization and planning'
  },
  {
    image: '2025-09-01-15.10.51.jpg',
    caption: 'Community engagement activities'
  },
  {
    image: '2025-09-01-15.10.55.jpg',
    caption: 'Successful event completion'
  }
])

// Involvement options
const involvementOptions = ref([
  {
    title: 'Join Weekly Rides',
    description: 'Participate in our regular community cycling events and meet fellow cycling enthusiasts.',
    icon: 'fas fa-bicycle',
    buttonText: 'Join Next Ride',
    link: '/contact'
  },
  {
    title: 'Volunteer',
    description: 'Help organize events, lead rides, or support our advocacy efforts.',
    icon: 'fas fa-hands-helping',
    buttonText: 'Volunteer Today',
    link: '/contact'
  },
  {
    title: 'Stay Updated',
    description: 'Subscribe to our newsletter for event updates and cycling news.',
    icon: 'fas fa-envelope',
    buttonText: 'Subscribe',
    link: '/contact'
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
/* Events showcase */
.events-showcase {
  display: flex;
  flex-direction: column;
  gap: var(--spacing-xl);
  margin-top: var(--spacing-lg);
}

.event-card {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: var(--spacing-lg);
  background: white;
  border-radius: 16px;
  overflow: hidden;
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease;
}

.event-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 12px 35px rgba(0, 0, 0, 0.15);
}

.event-card:nth-child(even) {
  grid-template-columns: 1fr 1fr;
}

.event-card:nth-child(even) .event-image {
  order: 2;
}

.event-image {
  position: relative;
  height: 300px;
  overflow: hidden;
}

.event-image {
  background-size: cover;
  background-position: center;
  transition: transform 0.3s ease;
}

.event-card:hover .event-image {
  transform: scale(1.05);
}

.event-category {
  position: absolute;
  top: var(--spacing-sm);
  left: var(--spacing-sm);
  background: var(--primary-gold);
  color: var(--neutral-gray);
  padding: 4px 12px;
  border-radius: 12px;
  font-size: 0.8rem;
  font-weight: 600;
}

.video-indicator {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 60px;
  height: 60px;
  background: rgba(0, 0, 0, 0.7);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  font-size: 1.5rem;
  transition: all 0.3s ease;
}

.event-card:hover .video-indicator {
  background: var(--primary-gold);
  color: var(--neutral-gray);
  transform: translate(-50%, -50%) scale(1.1);
}

.event-content {
  padding: var(--spacing-lg);
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.event-content h3 {
  color: var(--primary-green);
  margin-bottom: var(--spacing-sm);
  font-size: 1.5rem;
}

.event-details {
  margin: var(--spacing-md) 0;
}

.detail-item {
  display: flex;
  align-items: center;
  gap: var(--spacing-sm);
  margin-bottom: var(--spacing-xs);
  font-size: 0.9rem;
  color: var(--neutral-gray);
}

.detail-item i {
  color: var(--primary-green);
  width: 16px;
}

.event-actions {
  display: flex;
  gap: var(--spacing-sm);
  margin-top: var(--spacing-md);
}

.event-actions .btn-primary,
.event-actions .btn-secondary {
  flex: 1;
  text-align: center;
  font-size: 0.9rem;
  padding: 10px 16px;
}

/* Community programs */
.community-programs {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: var(--spacing-lg);
  margin-top: var(--spacing-lg);
}

.program-card {
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  border-radius: 16px;
  padding: var(--spacing-lg);
  text-align: center;
  border: 1px solid rgba(255, 255, 255, 0.2);
  transition: all 0.3s ease;
}

.program-card:hover {
  background: rgba(255, 255, 255, 0.2);
  transform: translateY(-5px);
}

.program-icon {
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

.program-card h3 {
  margin-bottom: var(--spacing-sm);
}

.program-features {
  display: flex;
  flex-wrap: wrap;
  gap: var(--spacing-xs);
  margin-top: var(--spacing-md);
  justify-content: center;
}

.feature-tag {
  background: rgba(255, 255, 255, 0.2);
  color: white;
  padding: 4px 12px;
  border-radius: 12px;
  font-size: 0.8rem;
  font-weight: 600;
}

/* Photo gallery */
.photo-gallery {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: var(--spacing-md);
  margin-top: var(--spacing-lg);
}

.gallery-item {
  position: relative;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease;
  height: 200px;
}

.gallery-item:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.15);
}

.gallery-image {
  width: 100%;
  height: 100%;
  background-size: cover;
  background-position: center;
  transition: transform 0.3s ease;
}

.gallery-item:hover .gallery-image {
  transform: scale(1.05);
}

.photo-overlay {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  background: linear-gradient(transparent, rgba(0, 0, 0, 0.8));
  color: white;
  padding: var(--spacing-sm);
  transform: translateY(100%);
  transition: transform 0.3s ease;
}

.gallery-item:hover .photo-overlay {
  transform: translateY(0);
}

.photo-overlay p {
  margin: 0;
  font-size: 0.9rem;
  text-align: center;
}

/* Get involved section */
.involvement-options {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: var(--spacing-lg);
  margin-top: var(--spacing-lg);
}

.involvement-card {
  text-align: center;
  padding: var(--spacing-lg);
  background: white;
  border-radius: 16px;
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease;
}

.involvement-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 12px 35px rgba(0, 0, 0, 0.15);
}

.involvement-icon {
  width: 80px;
  height: 80px;
  margin: 0 auto var(--spacing-md) auto;
  background: linear-gradient(135deg, var(--primary-green), var(--secondary-blue));
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 2rem;
  color: white;
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

/* Responsive design */
@media (max-width: 768px) {
  .event-card,
  .event-card:nth-child(even) {
    grid-template-columns: 1fr;
  }

  .event-card:nth-child(even) .event-image {
    order: 0;
  }

  .event-image {
    height: 200px;
  }

  .community-programs {
    grid-template-columns: 1fr;
  }

  .photo-gallery {
    grid-template-columns: repeat(2, 1fr);
  }

  .involvement-options {
    grid-template-columns: 1fr;
  }
}

@media (max-width: 480px) {
  .photo-gallery {
    grid-template-columns: 1fr;
  }

  .event-actions {
    flex-direction: column;
  }
}
</style>
