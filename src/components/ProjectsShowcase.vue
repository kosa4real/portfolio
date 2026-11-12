<script setup>
import { ref } from 'vue'
import ProjectCard from './ProjectCard.vue'

const expandedProject = ref(null)

const projects = [
  {
    id: 'zainpay',
    name: 'Zainpay',
    category: 'Fintech · Payment Infrastructure',
    description: 'Contributed to the frontend development of a payment platform that helps businesses accept payments and manage payment-related operations.',
    liveUrl: 'https://zainpay.ng/',
    ctaText: 'View Live Project',
    technologies: ['Vue.js', 'JavaScript', 'Vuex', 'Axios', 'REST APIs'],
    featured: true,
    caseStudy: {
      problem: 'Payment platforms require intuitive interfaces that handle complex workflows securely and reliably. Businesses need merchant dashboards that clearly display transaction data, settlement information, and account management tools.',
      role: 'Frontend Engineer — I contributed to building payment-related user interfaces, integrating REST API endpoints, and developing merchant-facing features.',
      approach: 'I focused on creating reusable Vue components for forms, transaction displays, and state management with Vuex. I used Axios for API integration and implemented comprehensive loading, error, and validation states.',
      challenges: 'Challenges included handling asynchronous API responses, ensuring form validation across different payment scenarios, and maintaining consistency across multiple dashboard views. I addressed these by creating a centralized error-handling strategy and reusable validation logic.',
      outcomes: 'Delivered maintainable, responsive interfaces that improved the user experience for merchants managing payments.'
    }
  },
  {
    id: 'zainpos',
    name: 'ZainPOS',
    category: 'Fintech · Point-of-Sale Technology',
    description: 'Worked on frontend experiences for a POS and merchant platform designed to help businesses manage payments and transaction-related activities.',
    liveUrl: 'https://zainpos.ng/',
    ctaText: 'View Live Project',
    technologies: ['Vue.js', 'Vuex', 'JavaScript', 'Axios', 'REST APIs'],
    featured: true,
    caseStudy: {
      problem: 'Point-of-sale systems need to be responsive and reliable for transaction processing. Merchants require clear transaction history, settlement tracking, and operational dashboards that work across various screen sizes.',
      role: 'Frontend Engineer — I developed merchant workflows, transaction management interfaces, and dashboard components.',
      approach: 'I built reusable UI patterns for transaction displays, implemented state management for complex workflows, and ensured responsive design across devices. I prioritized API-driven data handling and real-time state updates.',
      challenges: 'Key challenges included organizing complex merchant workflows into intuitive interfaces and handling real-time transaction data reliably. I solved this through careful component design and efficient state management.',
      outcomes: 'Delivered operational interfaces that merchants rely on daily for transaction processing and business management.'
    }
  },
  {
    id: 'betastack',
    name: 'Betastack',
    category: 'Corporate Website · Fintech Technology',
    description: 'Contributed to the web presence of a technology company building digital financial products and payment infrastructure.',
    liveUrl: 'https://betastack.ng/',
    ctaText: 'Visit Website',
    technologies: ['Vue.js', 'JavaScript', 'Bootstrap', 'REST APIs'],
    featured: false,
    caseStudy: {
      problem: 'A fintech company needed a clear, professional web presence to communicate its products and services to potential clients and partners.',
      role: 'Frontend Engineer — I implemented responsive layouts, reusable UI components, and integrated content management.',
      approach: 'I focused on creating a clean, business-oriented design with responsive components. I ensured cross-browser compatibility and optimized for mobile experiences.',
      challenges: 'Balancing technical depth with accessibility for non-technical visitors while maintaining brand consistency.',
      outcomes: 'Delivered a professional, scalable web presence that effectively presents company products and services.'
    }
  },
  {
    id: 'government',
    name: 'Kano State Government Project',
    category: 'Government · Public-Sector Technology',
    description: 'Contributed to a government-related digital project focused on delivering practical software for public-sector needs.',
    liveUrl: null,
    ctaText: 'Project Details',
    technologies: ['Vue.js', 'JavaScript', 'REST APIs'],
    featured: false,
    caseStudy: {
      problem: '[Project details available upon request]',
      role: '[To be confirmed]',
      approach: '[To be confirmed]',
      challenges: '[To be confirmed]',
      outcomes: '[To be confirmed]'
    }
  },
  {
    id: 'colleges',
    name: 'Colleges Project',
    category: 'Education · Digital Solutions',
    description: 'Worked on a digital project serving a college or education-related use case.',
    liveUrl: null,
    ctaText: 'Project Details',
    technologies: ['Vue.js', 'JavaScript'],
    featured: false,
    caseStudy: {
      problem: '[Project details to be added]',
      role: '[To be confirmed]',
      approach: '[To be confirmed]',
      challenges: '[To be confirmed]',
      outcomes: '[To be confirmed]'
    }
  }
]

const handleProjectSelect = (projectId, isExpanded) => {
  expandedProject.value = isExpanded ? projectId : null
}
</script>

<template>
  <section id="projects" class="projects-section">
    <div class="container">
      <div class="section-header">
        <h2>Featured Work</h2>
        <p>A selection of fintech products, platforms, and business-focused web experiences built with Vue.js and modern web technologies.</p>
      </div>

      <div class="projects-grid">
        <ProjectCard
          v-for="project in projects"
          :key="project.id"
          :project="project"
          :featured="project.featured"
          @select="handleProjectSelect(project.id, $event)"
        />
      </div>
    </div>
  </section>
</template>

<style scoped>
.projects-section {
  padding: var(--spacing-24) 0;
}

@media (max-width: 640px) {
  .projects-section {
    padding: var(--spacing-16) 0;
  }
}

.section-header {
  margin-bottom: var(--spacing-16);
  text-align: center;
  max-width: 600px;
  margin-left: auto;
  margin-right: auto;
}

.section-header h2 {
  margin-bottom: var(--spacing-4);
}

.section-header p {
  font-size: var(--font-size-lg);
  color: var(--color-text-secondary);
}

.projects-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: var(--spacing-8);
}

@media (max-width: 1023px) {
  .projects-grid {
    grid-template-columns: 1fr;
  }
}

@media (max-width: 640px) {
  .projects-grid {
    gap: var(--spacing-6);
  }
}
</style>
