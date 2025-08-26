<template>
  <nav class="navbar" :class="{ scrolled: isScrolled }">
    <div class="container">
      <div class="navbar-content">
        <NuxtLink to="/" class="navbar-brand">
          Active Mobility Ghana
        </NuxtLink>
        
        <ul class="navbar-nav" :class="{ active: mobileMenuOpen }">
          <li><NuxtLink to="/" @click="closeMobileMenu">Home</NuxtLink></li>
          <li><NuxtLink to="/about" @click="closeMobileMenu">About Us</NuxtLink></li>
          <li><NuxtLink to="/vision-mission" @click="closeMobileMenu">Vision & Mission</NuxtLink></li>
          <li><NuxtLink to="/programs" @click="closeMobileMenu">Programs</NuxtLink></li>
          <li><NuxtLink to="/contact" @click="closeMobileMenu">Contact</NuxtLink></li>
        </ul>

        <button 
          class="mobile-menu-toggle"
          @click="toggleMobileMenu"
          :aria-expanded="mobileMenuOpen"
          aria-label="Toggle navigation menu"
        >
          <div class="hamburger" :class="{ active: mobileMenuOpen }">
            <span></span>
            <span></span>
            <span></span>
          </div>
        </button>
      </div>
    </div>
  </nav>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const isScrolled = ref(false)
const mobileMenuOpen = ref(false)

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50
}

const toggleMobileMenu = () => {
  mobileMenuOpen.value = !mobileMenuOpen.value
}

const closeMobileMenu = () => {
  mobileMenuOpen.value = false
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<style scoped>
.hamburger.active span:nth-child(1) {
  transform: rotate(45deg) translate(5px, 5px);
}

.hamburger.active span:nth-child(2) {
  opacity: 0;
}

.hamburger.active span:nth-child(3) {
  transform: rotate(-45deg) translate(7px, -6px);
}

.router-link-active {
  color: var(--primary-green) !important;
}

.router-link-active::after {
  width: 100% !important;
}
</style>
