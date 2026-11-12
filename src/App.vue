<script setup>
import AppHeader from './components/AppHeader.vue'
import HeroSection from './components/HeroSection.vue'
import AboutSection from './components/AboutSection.vue'
import ProjectsShowcase from './components/ProjectsShowcase.vue'
import EngineeringApproach from './components/EngineeringApproach.vue'
import SkillsSection from './components/SkillsSection.vue'
import ContactSection from './components/ContactSection.vue'
import AppFooter from './components/AppFooter.vue'
</script>

<template>
  <AppHeader />
  <main id="main-content">
    <HeroSection />
    <AboutSection />
    <ProjectsShowcase />
    <EngineeringApproach />
    <SkillsSection />
    <ContactSection />
  </main>
  <AppFooter />
</template>

<style scoped>
#main-content {
  min-height: calc(100vh - 64px);
}
</style>
