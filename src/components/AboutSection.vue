<script setup>
const timeline = [
  {
    period: '2021–Present',
    role: 'Frontend Engineer',
    company: 'Betastack Nigeria Limited',
    description: 'Building and maintaining frontend applications for fintech and payment products. Working with Vue.js, Vue Router, Vuex, and REST APIs to develop merchant interfaces, payment workflows, and transaction management systems. Contributing to component architecture, application state management, and code maintainability.'
  },
  {
    period: '2018–2021',
    role: 'Instructor',
    company: 'Aptech Computer Education',
    description: 'Taught programming and web development fundamentals to students. Developed curriculum materials, mentored learners through practical exercises, and helped students understand core technical concepts. This experience strengthened my communication, collaboration, and ability to explain complex ideas clearly.'
  }
]
</script>

<template>
  <section id="about" class="about-section">
    <div class="container">
      <div class="about-content">
        <div class="about-text">
          <h2>About Me</h2>
          <p>
            I'm Munir, a Frontend Engineer based in Kano, Nigeria. My work focuses on turning product requirements into responsive, maintainable web applications that people can use confidently.
          </p>
          <p>
            Over the years, I've worked on fintech products, merchant platforms, payment-related interfaces, and business websites. I enjoy understanding how a product works, connecting the frontend to backend services, and making complex workflows easier to use.
          </p>
          <p>
            I care about clean component architecture, reusable code, thoughtful user experiences, and continuous learning. I'm strengthening my broader software engineering skills while continuing to build on my experience with Vue.js and JavaScript.
          </p>
        </div>

        <div class="experience-timeline">
          <h3>Professional Experience</h3>
          <div class="timeline">
            <div v-for="(item, index) in timeline" :key="index" class="timeline-item">
              <div class="timeline-marker"></div>
              <div class="timeline-content">
                <p class="timeline-period">{{ item.period }}</p>
                <h4>{{ item.role }}</h4>
                <p class="timeline-company">{{ item.company }}</p>
                <p class="timeline-description">{{ item.description }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.about-section {
  padding: var(--spacing-24) 0;
  background-color: var(--color-bg-secondary);
}

@media (max-width: 640px) {
  .about-section {
    padding: var(--spacing-16) 0;
  }
}

.about-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: var(--spacing-16);
  align-items: start;
}

@media (max-width: 1023px) {
  .about-content {
    grid-template-columns: 1fr;
    gap: var(--spacing-12);
  }
}

.about-text h2 {
  margin-bottom: var(--spacing-6);
}

.about-text p {
  font-size: var(--font-size-base);
  line-height: var(--line-height-relaxed);
  color: var(--color-text-secondary);
  margin-bottom: var(--spacing-6);
}

.about-text p:last-child {
  margin-bottom: 0;
}

.experience-timeline h3 {
  font-size: var(--font-size-lg);
  margin-bottom: var(--spacing-8);
  color: var(--color-text-primary);
}

.timeline {
  position: relative;
}

.timeline::before {
  content: '';
  position: absolute;
  left: 19px;
  top: 24px;
  bottom: 0;
  width: 2px;
  background-color: var(--color-border);
}

.timeline-item {
  display: flex;
  gap: var(--spacing-6);
  margin-bottom: var(--spacing-8);
  position: relative;
}

.timeline-item:last-child {
  margin-bottom: 0;
}

.timeline-marker {
  position: relative;
  width: 40px;
  height: 40px;
  flex-shrink: 0;
  background-color: var(--color-primary-500);
  border-radius: 50%;
  border: 3px solid var(--color-bg-primary);
  top: 0;
}

.timeline-content {
  padding-top: var(--spacing-2);
  flex: 1;
}

.timeline-period {
  font-size: var(--font-size-sm);
  font-weight: var(--font-weight-semibold);
  color: var(--color-primary-500);
  text-transform: uppercase;
  letter-spacing: 0.05em;
  margin-bottom: var(--spacing-2);
}

.timeline-content h4 {
  font-size: var(--font-size-lg);
  font-weight: var(--font-weight-semibold);
  color: var(--color-text-primary);
  margin-bottom: var(--spacing-1);
}

.timeline-company {
  font-size: var(--font-size-base);
  color: var(--color-text-secondary);
  margin-bottom: var(--spacing-3);
  font-weight: var(--font-weight-medium);
}

.timeline-description {
  font-size: var(--font-size-base);
  line-height: var(--line-height-relaxed);
  color: var(--color-text-secondary);
}

@media (max-width: 640px) {
  .about-text p {
    font-size: var(--font-size-sm);
  }

  .timeline::before {
    left: 11px;
  }

  .timeline-marker {
    width: 24px;
    height: 24px;
    min-width: 24px;
  }

  .timeline-gap {
    gap: var(--spacing-4);
  }
}
</style>
