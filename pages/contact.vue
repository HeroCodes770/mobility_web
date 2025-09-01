<template>
  <div>
    <!-- Hero Section -->
    <section class="hero" style="min-height: 50vh; background-image: linear-gradient(rgba(0, 0, 0, 0.6), rgba(0, 0, 0, 0.6)), url(/2025-09-01-15.10.27.jpg);">
      <div class="container">
        <div class="hero-content fade-in-up">
          <h1>Get in Touch</h1>
          <p class="subtitle">
            Ready to join our movement? We'd love to hear from you.
          </p>
        </div>
      </div>
    </section>

    <!-- Contact Form Section -->
    <section class="py-lg" style="background: linear-gradient(135deg, var(--primary-green), var(--secondary-blue));">
      <div class="container">
        <div class="contact-form-section">
          <div class="form-intro fade-in">
            <h2 style="color: white; text-align: center; margin-bottom: var(--spacing-md);">Send Us a Message</h2>
            <p style="color: rgba(255, 255, 255, 0.9); text-align: center; max-width: 600px; margin: 0 auto var(--spacing-lg) auto; font-size: 1.1rem;">
              Fill out the form below and we'll get back to you within 24 hours.
            </p>
          </div>

          <div class="form-container fade-in-up">
            <form @submit.prevent="submitForm" class="contact-form">
              <div class="form-row">
                <div class="form-group">
                  <label for="firstName" class="form-label">First Name *</label>
                  <input 
                    type="text" 
                    id="firstName" 
                    v-model="form.firstName" 
                    required 
                  >
                </div>
                <div class="form-group">
                  <label for="lastName" class="form-label">Last Name *</label>
                  <input 
                    type="text" 
                    id="lastName" 
                    v-model="form.lastName" 
                    required 
                  >
                </div>
              </div>

              <div class="form-group">
                <label for="email" class="form-label">Email Address *</label>
                <input 
                  type="email" 
                  id="email" 
                  v-model="form.email" 
                  required 
                >
              </div>

              <div class="form-group">
                <label for="message" class="form-label">Message *</label>
                <textarea 
                  id="message" 
                  v-model="form.message" 
                  rows="5" 
                  required 
                  placeholder="Tell us how you'd like to get involved..."
                ></textarea>
              </div>

              <div class="form-actions">
                <button 
                  type="submit" 
                  class="btn-primary" 
                  :disabled="isSubmitting"
                  style="width: 100%; background-color: var(--primary-gold); color: var(--neutral-gray); font-size: 1.1rem; padding: 15px;"
                >
                  <span v-if="!isSubmitting">Send Message</span>
                  <span v-else>
                    <i class="fas fa-spinner fa-spin"></i>
                    Sending...
                  </span>
                </button>
              </div>
            </form>

            <!-- Success Message -->
            <div v-if="showSuccess" class="success-message">
              <i class="fas fa-check-circle"></i>
              <h3>Message Sent Successfully!</h3>
              <p>Thank you for reaching out. We'll get back to you within 24 hours.</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact Info -->
    <section class="py-lg">
      <div class="container">
        <div class="text-center mb-lg fade-in">
          <h2>Contact Information</h2>
          <p style="max-width: 600px; margin: 0 auto; font-size: 1.1rem;">
            Get in touch with us through any of these channels.
          </p>
        </div>

        <div class="contact-info-grid">
          <div class="contact-info-card fade-in-up" v-for="(info, index) in contactInfo" :key="index">
            <div class="info-icon">
              <i :class="info.icon"></i>
            </div>
            <h3>{{ info.title }}</h3>
            <p>{{ info.details }}</p>
            <a v-if="info.link" :href="info.link" class="btn-secondary">
              {{ info.buttonText }}
            </a>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref, reactive, onMounted } from 'vue'

// SEO Meta
useHead({
  title: 'Contact Us - Active Mobility Ghana',
  meta: [
    {
      name: 'description',
      content: 'Get in touch with Active Mobility Ghana. Join our community, volunteer, partner with us, or learn more about sustainable transport initiatives across Ghana.'
    }
  ]
})

// Form data
const form = reactive({
  firstName: '',
  lastName: '',
  email: '',
  message: ''
})

// Form state
const isSubmitting = ref(false)
const showSuccess = ref(false)

// Contact info
const contactInfo = ref([
  {
    title: 'Email Us',
    details: 'info@activemobilityghana.org',
    icon: 'fas fa-envelope',
    link: 'mailto:info@activemobilityghana.org',
    buttonText: 'Send Email'
  },
  {
    title: 'Call Us',
    details: '+233 XX XXX XXXX',
    icon: 'fas fa-phone',
    link: 'tel:+233XXXXXXXXX',
    buttonText: 'Call Now'
  },
  {
    title: 'Visit Us',
    details: '123 Liberation Road, Osu, Accra',
    icon: 'fas fa-map-marker-alt',
    link: '#',
    buttonText: 'Get Directions'
  },
  {
    title: 'Follow Us',
    details: 'Stay updated on social media',
    icon: 'fas fa-share-alt',
    link: '#',
    buttonText: 'Follow'
  }
])

// Submit form
const submitForm = async () => {
  isSubmitting.value = true

  try {
    // Simulate API call
    await new Promise(resolve => setTimeout(resolve, 2000))
    
    console.log('Form submitted:', form)
    
    // Show success message
    showSuccess.value = true
    
    // Reset form
    Object.keys(form).forEach(key => {
      form[key] = ''
    })

    // Hide success message after 5 seconds
    setTimeout(() => {
      showSuccess.value = false
    }, 5000)

  } catch (error) {
    console.error('Error submitting form:', error)
  } finally {
    isSubmitting.value = false
  }
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
/* Form container */
.form-container {
  max-width: 700px;
  margin: 0 auto;
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(10px);
  border-radius: 16px;
  padding: var(--spacing-xl);
  box-shadow: 0 12px 35px rgba(0, 0, 0, 0.2);
}

.contact-form {
  display: grid;
  gap: var(--spacing-md);
}

.form-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: var(--spacing-md);
}

.form-group {
  display: flex;
  flex-direction: column;
}

.form-label {
  margin-bottom: var(--spacing-xs);
  font-weight: 600;
  color: var(--neutral-gray);
}

input,
textarea {
  padding: var(--spacing-sm);
  border: 2px solid #e0e0e0;
  border-radius: 8px;
  font-family: 'Open Sans', sans-serif;
  font-size: 1rem;
  transition: all 0.3s ease;
  background: white;
}

input:focus,
textarea:focus {
  border-color: var(--primary-green);
  outline: none;
  box-shadow: 0 0 0 3px rgba(46, 125, 50, 0.1);
}

/* Success message */
.success-message {
  text-align: center;
  padding: var(--spacing-lg);
  background: linear-gradient(135deg, var(--primary-green), var(--secondary-blue));
  color: white;
  border-radius: 12px;
  margin-top: var(--spacing-md);
}

.success-message i {
  font-size: 3rem;
  margin-bottom: var(--spacing-md);
  color: var(--primary-gold);
}

.success-message h3 {
  color: white;
  margin-bottom: var(--spacing-sm);
}

/* Contact info grid */
.contact-info-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: var(--spacing-lg);
  margin-top: var(--spacing-lg);
}

.contact-info-card {
  background: white;
  border-radius: 16px;
  padding: var(--spacing-lg);
  text-align: center;
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease;
}

.contact-info-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 12px 35px rgba(0, 0, 0, 0.15);
}

.info-icon {
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

.contact-info-card h3 {
  color: var(--primary-green);
  margin-bottom: var(--spacing-sm);
}

.contact-info-card p {
  color: var(--neutral-gray);
  margin-bottom: var(--spacing-md);
}

/* Responsive design */
@media (max-width: 768px) {
  .form-row {
    grid-template-columns: 1fr;
  }

  .contact-info-grid {
    grid-template-columns: 1fr;
  }
}
</style>
