<script setup>
const scrollToSection = (id) => {
  const element = document.getElementById(id)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
}
</script>

<template>
  <section id="hero" class="hero-section">
    <div class="container">
      <div class="hero-content">
        <div class="hero-text">
          <p class="hero-eyebrow">FRONTEND ENGINEER · NIGERIA</p>
          <h1 class="hero-headline">Building thoughtful digital experiences that solve real problems.</h1>
          <p class="hero-description">
            I'm Munir Abubakar, a Frontend Engineer focused on building reliable, intuitive web applications. I work primarily with Vue.js and JavaScript, turning complex product requirements and APIs into clear, maintainable user experiences.
          </p>

          <div class="hero-ctas">
            <button class="btn btn-primary btn-large" @click="scrollToSection('projects')">
              Explore My Work
            </button>
            <button class="btn btn-secondary btn-large" @click="scrollToSection('contact')">
              Get in Touch
            </button>
          </div>

          <div class="hero-links">
            <a href="#" @click.prevent="scrollToSection('contact')" class="hero-text-link">
              Download CV →
            </a>
          </div>
        </div>

        <div class="hero-visual">
          <div class="visual-placeholder">
            <svg width="100%" height="100%" viewBox="0 0 400 300" preserveAspectRatio="xMidYMid meet" xmlns="http://www.w3.org/2000/svg">
              <!-- Browser window mockup -->
              <rect x="20" y="20" width="360" height="260" rx="12" fill="none" stroke="var(--color-border)" stroke-width="1" />
              <rect x="20" y="20" width="360" height="40" rx="12" fill="var(--color-bg-secondary)" />
              
              <!-- Browser chrome -->
              <circle cx="35" cy="35" r="4" fill="var(--color-primary-500)" opacity="0.5" />
              <circle cx="50" cy="35" r="4" fill="var(--color-warning)" opacity="0.5" />
              <circle cx="65" cy="35" r="4" fill="var(--color-success)" opacity="0.5" />
              
              <!-- Content placeholder bars (representing interface elements) -->
              <rect x="40" y="75" width="320" height="12" rx="6" fill="var(--color-primary-500)" opacity="0.1" />
              <rect x="40" y="100" width="240" height="8" rx="4" fill="var(--color-primary-500)" opacity="0.15" />
              <rect x="40" y="120" width="280" height="8" rx="4" fill="var(--color-primary-500)" opacity="0.1" />
              
              <rect x="40" y="160" width="140" height="30" rx="6" fill="var(--color-primary-500)" opacity="0.2" />
              <rect x="200" y="160" width="140" height="30" rx="6" fill="var(--color-primary-500)" opacity="0.1" />
              
              <rect x="40" y="210" width="100" height="6" rx="3" fill="var(--color-primary-500)" opacity="0.15" />
              <rect x="160" y="210" width="100" height="6" rx="3" fill="var(--color-primary-500)" opacity="0.1" />
              <rect x="280" y="210" width="80" height="6" rx="3" fill="var(--color-primary-500)" opacity="0.12" />
            </svg>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero-section {
  padding: var(--spacing-24) 0;
  overflow: hidden;
}

@media (max-width: 640px) {
  .hero-section {
    padding: var(--spacing-16) 0;
  }
}

.hero-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: var(--spacing-16);
  align-items: center;
}

@media (max-width: 1023px) {
  .hero-content {
    grid-template-columns: 1fr;
    gap: var(--spacing-12);
  }
}

.hero-eyebrow {
  font-size: var(--font-size-sm);
  font-weight: var(--font-weight-semibold);
  letter-spacing: 0.15em;
  text-transform: uppercase;
  color: var(--color-primary-500);
  margin-bottom: var(--spacing-4);
}

.hero-headline {
  font-size: var(--font-size-5xl);
  line-height: var(--line-height-tight);
  margin-bottom: var(--spacing-6);
  color: var(--color-text-primary);
}

@media (max-width: 1023px) {
  .hero-headline {
    font-size: var(--font-size-4xl);
  }
}

@media (max-width: 640px) {
  .hero-headline {
    font-size: var(--font-size-3xl);
  }
}

.hero-description {
  font-size: var(--font-size-lg);
  line-height: var(--line-height-relaxed);
  margin-bottom: var(--spacing-8);
  color: var(--color-text-secondary);
  max-width: 500px;
}

.hero-ctas {
  display: flex;
  gap: var(--spacing-4);
  margin-bottom: var(--spacing-6);
  flex-wrap: wrap;
}

@media (max-width: 640px) {
  .hero-ctas {
    flex-direction: column;
  }

  .hero-ctas .btn {
    width: 100%;
  }
}

.hero-links {
  display: flex;
  gap: var(--spacing-6);
  align-items: center;
}

.hero-text-link {
  font-size: var(--font-size-base);
  font-weight: var(--font-weight-medium);
  color: var(--color-primary-500);
  transition: color var(--transition-fast);
}

.hero-text-link:hover {
  color: var(--color-primary-600);
}

.hero-visual {
  display: flex;
  align-items: center;
  justify-content: center;
}

.visual-placeholder {
  width: 100%;
  max-width: 400px;
  aspect-ratio: 4 / 3;
  background: linear-gradient(135deg, var(--color-bg-secondary) 0%, var(--color-bg-tertiary) 100%);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-xl);
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  animation: fadeInScale 0.6s ease-out;
}

@keyframes fadeInScale {
  from {
    opacity: 0;
    transform: scale(0.95);
  }
  to {
    opacity: 1;
    transform: scale(1);
  }
}
</style>
