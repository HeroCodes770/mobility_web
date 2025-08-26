<template>
  <footer class="footer">
    <div class="container">
      <div class="footer-content">
        <div class="footer-section">
          <h4>Active Mobility Ghana</h4>
          <p>Empowering communities through sustainable transport, trails, and greenways across Ghana.</p>
        </div>
        
        <div class="footer-section">
          <h4>Quick Links</h4>
          <ul style="list-style: none;">
            <li><NuxtLink to="/about">About Us</NuxtLink></li>
            <li><NuxtLink to="/vision-mission">Vision & Mission</NuxtLink></li>
            <li><NuxtLink to="/programs">Programs</NuxtLink></li>
            <li><NuxtLink to="/contact">Contact</NuxtLink></li>
          </ul>
        </div>
        
        <div class="footer-section">
          <h4>Connect With Us</h4>
          <div class="social-links">
            <a href="#" aria-label="Facebook" target="_blank">
              <i class="fab fa-facebook-f"></i>
            </a>
            <a href="#" aria-label="Twitter" target="_blank">
              <i class="fab fa-twitter"></i>
            </a>
            <a href="#" aria-label="Instagram" target="_blank">
              <i class="fab fa-instagram"></i>
            </a>
            <a href="#" aria-label="LinkedIn" target="_blank">
              <i class="fab fa-linkedin-in"></i>
            </a>
          </div>
        </div>
        
        <div class="footer-section">
          <h4>Contact Info</h4>
          <p>📧 info@activemobilityghana.org</p>
          <p>📞 +233 XX XXX XXXX</p>
          <p>📍 Accra, Ghana</p>
        </div>
      </div>
      
      <div class="footer-bottom">
        <small>&copy; 2025 Active Mobility Ghana. All rights reserved.</small>
      </div>
    </div>
  </footer>
</template>

<script setup>
</script>

<style scoped>
.footer-section ul {
  padding: 0;
}

.footer-section ul li {
  margin-bottom: 8px;
}

.social-links {
  display: flex;
  gap: 16px;
  justify-content: center;
}

.social-links a {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 40px;
  height: 40px;
  background-color: var(--primary-gold);
  color: var(--primary-green);
  border-radius: 50%;
  transition: all 0.3s ease;
}

.social-links a:hover {
  background-color: var(--neutral-white);
  transform: translateY(-3px);
}

@media (max-width: 768px) {
  .social-links {
    justify-content: center;
  }
}
</style>
