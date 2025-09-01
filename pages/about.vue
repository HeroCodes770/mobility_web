<template>
  <div>
    <!-- Hero Section -->
    <section class="hero" style="min-height: 50vh; background-image: linear-gradient(rgba(0, 0, 0, 0.6), rgba(0, 0, 0, 0.6)), url(/2025-09-01-15.09.36.jpg);">
      <div class="container">
        <div class="hero-content fade-in-up">
          <h1>About Us</h1>
          <p class="subtitle">
            Discover our story, meet our team, and learn how we're transforming Ghana's streets 
            into vibrant spaces for active mobility.
          </p>
        </div>
      </div>
    </section>

    <!-- Main About Section -->
    <section class="py-lg">
      <div class="container">
        <div class="fade-in">
          <h2 class="mb-md">Who We Are</h2>
          <div style="display: grid; grid-template-columns: 1fr 1fr; gap: var(--spacing-lg); align-items: center;" class="about-grid">
            <div>
              <p style="font-size: 1.1rem; line-height: 1.7;">
                We are a vibrant community of individuals, advocates, and partners inspired to promote 
                active mobility options, trails, and greenways to create complete streets across Ghana. 
                Our focus is on transforming urban and rural spaces into safe, accessible, and eco-friendly 
                environments where everyone can walk, bike, or use non-motorized transport with ease.
              </p>
              <p style="font-size: 1.1rem; line-height: 1.7;">
                Founded on the belief that streets should serve people first, we work to address challenges 
                like traffic congestion, pollution, and sedentary lifestyles. By collaborating with local 
                governments, NGOs, and residents, we're building a movement that prioritizes health, equity, 
                and sustainability in Ghana's communities.
              </p>
            </div>
            <div>
              <div 
                class="about-image"
                style="background-image: url(/2025-09-01-15.10.01.jpg); width: 100%; height: 300px; background-size: cover; background-position: center; border-radius: 12px; box-shadow: 0 8px 25px rgba(0, 0, 0, 0.1);"
              ></div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Our Story Section -->
    <section class="py-lg" style="background-color: white;">
      <div class="container">
        <div class="text-center mb-lg fade-in">
          <h2>Our Story</h2>
          <p style="max-width: 800px; margin: 0 auto; font-size: 1.1rem; color: var(--neutral-gray);">
            Every great movement starts with a simple idea and passionate people willing to make it reality.
          </p>
        </div>

        <div class="story-timeline">
          <div class="timeline-item fade-in-up" v-for="(milestone, index) in timeline" :key="index" :style="{ animationDelay: `${index * 0.2}s` }">
            <div class="timeline-marker"></div>
            <div class="timeline-content">
              <h3>{{ milestone.year }}</h3>
              <h4>{{ milestone.title }}</h4>
              <p>{{ milestone.description }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Recent Events Gallery -->
    <section class="py-lg">
      <div class="container">
        <div class="text-center mb-lg fade-in">
          <h2>Our Recent Events</h2>
          <p style="max-width: 600px; margin: 0 auto; font-size: 1.1rem;">
            Take a look at some of our most memorable events and partnerships.
          </p>
        </div>

                 <div class="events-gallery">
           <div class="gallery-item fade-in-up" v-for="(event, index) in eventsGallery" :key="index" :style="{ animationDelay: `${index * 0.1}s` }">
             <div class="gallery-image" :style="{ backgroundImage: `url(/${event.image})` }"></div>
             <div class="gallery-overlay">
               <h4>{{ event.title }}</h4>
               <p>{{ event.description }}</p>
             </div>
           </div>
         </div>
      </div>
    </section>

    <!-- Why Join Us Section -->
    <section class="py-lg" style="background: linear-gradient(135deg, var(--primary-green), var(--secondary-blue)); color: white;">
      <div class="container">
        <div class="text-center mb-lg fade-in">
          <h2 style="color: white;">Why Join Us?</h2>
          <p style="color: rgba(255, 255, 255, 0.9); max-width: 700px; margin: 0 auto; font-size: 1.1rem;">
            Active mobility isn't just about getting from A to B – it's about healthier lives, 
            cleaner air, and thriving economies. By supporting us, you're part of positive change in Ghana.
          </p>
        </div>

        <div class="benefits-grid">
          <div class="benefit-card fade-in-up" v-for="(benefit, index) in benefits" :key="index" :style="{ animationDelay: `${index * 0.2}s` }">
            <div class="benefit-icon">
              <i :class="benefit.icon"></i>
            </div>
            <h3 style="color: white;">{{ benefit.title }}</h3>
            <p style="color: rgba(255, 255, 255, 0.9);">{{ benefit.description }}</p>
          </div>
        </div>

        <div class="text-center mt-lg fade-in">
          <NuxtLink to="/contact" class="btn-primary" style="background-color: var(--primary-gold); color: var(--neutral-gray); font-size: 1.1rem; padding: 15px 30px;">
            Join Our Community Today
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
  title: 'About Us - Active Mobility Ghana',
  meta: [
    {
      name: 'description',
      content: 'Learn about Active Mobility Ghana\'s mission to promote sustainable transport, our team, partners, and how we\'re transforming communities across Ghana.'
    }
  ]
})

// Timeline data
const timeline = ref([
  {
    year: '2023',
    title: 'The Beginning',
    description: 'A group of passionate Ghanaians came together with a vision of car-free, people-centered streets and sustainable transport solutions.'
  },
  {
    year: '2024',
    title: 'First Embassy Partnership',
    description: 'Established our first diplomatic partnership with the French Embassy for the "Ride with Team Europe" event.'
  },
  {
    year: '2024',
    title: 'Community Weekly Rides',
    description: 'Launched our regular community cycling events that bring together cyclists of all levels for weekly tours.'
  },
  {
    year: '2024',
    title: 'Adomi Bridge Adventure',
    description: 'Organized our first major cycling tour to the iconic Adomi Bridge, showcasing Ghana\'s beautiful landscapes.'
  },
  {
    year: '2024',
    title: 'Israel Embassy Partnership',
    description: 'Partnered with the Israel Embassy for a solidarity ride to raise awareness about important global issues.'
  }
])

// Events gallery - using more of your images
const eventsGallery = ref([
  {
    title: 'Community Gathering',
    description: 'Pre-ride community meetup',
    image: '2025-09-01-15.09.17.jpg'
  },
  {
    title: 'Team Formation',
    description: 'Organizing cycling groups',
    image: '2025-09-01-15.09.36.jpg'
  },
  {
    title: 'Israel Embassy Partnership',
    description: 'Solidarity cycling event',
    image: '2025-09-01-15.09.43.jpg'
  },
  {
    title: 'Weekly Community Rides',
    description: 'Regular cycling activities',
    image: '2025-09-01-15.09.51.jpg'
  },
  {
    title: 'Group Preparation',
    description: 'Getting ready for events',
    image: '2025-09-01-15.09.56.jpg'
  },
  {
    title: 'Adomi Bridge Adventure',
    description: 'Long-distance cycling tour',
    image: '2025-09-01-15.10.01.jpg'
  },
  {
    title: 'Cycling Education',
    description: 'Teaching cycling skills',
    image: '2025-09-01-15.10.07.jpg'
  },
  {
    title: 'French Embassy Event',
    description: 'International partnership',
    image: '2025-09-01-15.10.17.jpg'
  },
  {
    title: 'Community Outreach',
    description: 'Expanding our reach',
    image: '2025-09-01-15.10.22.jpg'
  },
  {
    title: 'Bridge Tour Participants',
    description: 'Successful completion',
    image: '2025-09-01-15.10.27.jpg'
  },
  {
    title: 'Safety Training',
    description: 'Cycling safety workshops',
    image: '2025-09-01-15.10.31.jpg'
  },
  {
    title: 'Team Building Activities',
    description: 'Strengthening community bonds',
    image: '2025-09-01-15.10.36.jpg'
  },
  {
    title: 'Skill Development',
    description: 'Advanced cycling techniques',
    image: '2025-09-01-15.10.39.jpg'
  },
  {
    title: 'Group Dynamics',
    description: 'Working together effectively',
    image: '2025-09-01-15.10.44.jpg'
  },
  {
    title: 'Event Coordination',
    description: 'Organizing successful rides',
    image: '2025-09-01-15.10.47.jpg'
  }
])

// Benefits data
const benefits = ref([
  {
    title: 'Health & Wellness',
    description: 'Promote physical activity and mental wellbeing through active transport options.',
    icon: 'fas fa-heartbeat'
  },
  {
    title: 'Environmental Impact',
    description: 'Reduce carbon emissions and air pollution while protecting Ghana\'s natural environment.',
    icon: 'fas fa-leaf'
  },
  {
    title: 'Economic Growth',
    description: 'Boost local economies through sustainable tourism and reduced transport costs.',
    icon: 'fas fa-chart-line'
  },
  {
    title: 'Community Building',
    description: 'Strengthen social connections and create inclusive spaces for all community members.',
    icon: 'fas fa-users'
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
/* About grid responsive */
.about-grid {
  grid-template-columns: 1fr 1fr;
  gap: var(--spacing-lg);
  align-items: center;
}

@media (max-width: 768px) {
  .about-grid {
    grid-template-columns: 1fr;
    gap: var(--spacing-md);
  }
}

/* Timeline styles */
.story-timeline {
  position: relative;
  max-width: 800px;
  margin: 0 auto;
}

.story-timeline::before {
  content: '';
  position: absolute;
  left: 50%;
  top: 0;
  bottom: 0;
  width: 3px;
  background: linear-gradient(to bottom, var(--primary-green), var(--secondary-blue));
  transform: translateX(-50%);
}

.timeline-item {
  display: flex;
  align-items: center;
  margin-bottom: var(--spacing-lg);
  position: relative;
}

.timeline-item:nth-child(odd) {
  flex-direction: row;
}

.timeline-item:nth-child(even) {
  flex-direction: row-reverse;
}

.timeline-marker {
  width: 20px;
  height: 20px;
  background-color: var(--primary-gold);
  border-radius: 50%;
  border: 3px solid var(--primary-green);
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  z-index: 2;
}

.timeline-content {
  background: white;
  padding: var(--spacing-md);
  border-radius: 12px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  width: calc(50% - 40px);
  margin: 0 20px;
}

.timeline-content h3 {
  color: var(--primary-green);
  font-size: 1.5rem;
  margin-bottom: var(--spacing-xs);
}

.timeline-content h4 {
  color: var(--neutral-gray);
  font-size: 1.1rem;
  margin-bottom: var(--spacing-xs);
}

@media (max-width: 768px) {
  .story-timeline::before {
    left: 20px;
  }
  
  .timeline-item {
    flex-direction: row !important;
  }
  
  .timeline-marker {
    left: 20px;
  }
  
  .timeline-content {
    width: calc(100% - 60px);
    margin-left: 40px;
    margin-right: 0;
  }
}

/* Events gallery */
.events-gallery {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: var(--spacing-md);
  margin-top: var(--spacing-lg);
}

.gallery-item {
  position: relative;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease;
  height: 250px;
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

.gallery-overlay {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  background: linear-gradient(transparent, rgba(0, 0, 0, 0.8));
  color: white;
  padding: var(--spacing-md);
  transform: translateY(100%);
  transition: transform 0.3s ease;
}

.gallery-item:hover .gallery-overlay {
  transform: translateY(0);
}

.gallery-overlay h4 {
  color: white;
  margin-bottom: var(--spacing-xs);
  font-size: 1.1rem;
}

.gallery-overlay p {
  color: rgba(255, 255, 255, 0.9);
  font-size: 0.9rem;
  margin: 0;
}

/* Benefits grid */
.benefits-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: var(--spacing-lg);
  margin-top: var(--spacing-lg);
}

.benefit-card {
  text-align: center;
  padding: var(--spacing-lg);
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  border-radius: 12px;
  border: 1px solid rgba(255, 255, 255, 0.2);
  transition: all 0.3s ease;
}

.benefit-card:hover {
  background: rgba(255, 255, 255, 0.2);
  transform: translateY(-5px);
}

.benefit-icon {
  width: 80px;
  height: 80px;
  margin: 0 auto var(--spacing-md) auto;
  background: var(--primary-gold);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 2rem;
  color: var(--neutral-gray);
}

.benefit-card h3 {
  margin-bottom: var(--spacing-sm);
}
</style>
