<script setup lang="ts">
import Features from './components/sections/Features.vue';
import Hero from './components/sections/Hero.vue';
import Introduction from './components/sections/Introduction.vue';
import LogoTicker from './components/sections/LogoTicker.vue';
import Navbar from './components/sections/Navbar.vue';
import Integrations from './components/sections/Integrations.vue';
import Faqs from './components/sections/Faqs.vue';
import CallToAction from './components/sections/CallToAction.vue';
import Footer from './components/sections/Footer.vue';
</script>

<template>
  <Navbar />
  <Hero />
  <LogoTicker />
  <Introduction />
  <Features />
  <Integrations />
  <Faqs />
  <CallToAction />
  <Footer />
</template>
