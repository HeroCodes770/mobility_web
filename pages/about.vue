<template>
  <div>
    <section class="hero" style="min-height: 50vh; background-image: linear-gradient(rgba(0, 0, 0, 0.6), rgba(0, 0, 0, 0.6)), url('https://images.unsplash.com/photo-1544620347-c4fd4a3d5957?ixlib=rb-4.0.3&auto=format&fit=crop&w=2000&q=80');">
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

    <section class="py-lg">
      <div class="container">
        <div class="fade-in">
          <h2 class="mb-md">Who We Are</h2>
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
      </div>
    </section>
  </div>
</template>

<script setup>
useHead({
  title: 'About Us - Active Mobility Ghana',
  meta: [
    {
      name: 'description',
      content: 'Learn about Active Mobility Ghana\'s mission to promote sustainable transport, our team, partners, and how we\'re transforming communities across Ghana.'
    }
  ]
})
</script>
