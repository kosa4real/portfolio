<script setup>
const skillCategories = [
  {
    title: 'Primary Frontend',
    skills: [
      'JavaScript',
      'Vue.js',
      'Vue 3',
      'Vue Router',
      'Vuex',
      'HTML5',
      'CSS3',
      'Responsive Web Design'
    ]
  },
  {
    title: 'Frontend Development Practices',
    skills: [
      'Component-based Architecture',
      'Reusable UI Components',
      'State Management',
      'Form Validation',
      'API Integration',
      'Loading & Error States',
      'Performance-conscious Rendering',
      'Accessibility Fundamentals'
    ]
  },
  {
    title: 'APIs & Backend Exposure',
    skills: [
      'REST APIs',
      'Axios',
      'JSON',
      'Node.js',
      'Express.js',
      'Authentication Workflows'
    ]
  },
  {
    title: 'Tools & Additional Technologies',
    skills: [
      'Git',
      'Figma',
      'Bootstrap',
      'Tailwind CSS',
      'React',
      'Next.js',
      'TypeScript',
      'Pinia',
      'Firebase',
      'Chart.js'
    ]
  }
]
</script>

<template>
  <section id="skills" class="skills-section">
    <div class="container">
      <div class="section-header">
        <h2>Technical Skills</h2>
        <p>A focused skill set built on professional experience with Vue.js, JavaScript, and modern web development practices.</p>
      </div>

      <div class="skills-grid">
        <div v-for="category in skillCategories" :key="category.title" class="skill-category">
          <h3>{{ category.title }}</h3>
          <ul class="skill-list">
            <li v-for="skill in category.skills" :key="skill" class="skill-item">
              {{ skill }}
            </li>
          </ul>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.skills-section {
  padding: var(--spacing-24) 0;
  background-color: var(--color-bg-secondary);
}

@media (max-width: 640px) {
  .skills-section {
    padding: var(--spacing-16) 0;
  }
}

.section-header {
  margin-bottom: var(--spacing-16);
  text-align: center;
  max-width: 500px;
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

.skills-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: var(--spacing-12);
}

@media (max-width: 1023px) {
  .skills-grid {
    grid-template-columns: 1fr;
    gap: var(--spacing-10);
  }
}

.skill-category {
  padding: var(--spacing-8);
  background-color: var(--color-bg-primary);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-xl);
  transition: all var(--transition-base);
}

.skill-category:hover {
  border-color: var(--color-primary-500);
  box-shadow: var(--shadow-md);
}

.skill-category h3 {
  font-size: var(--font-size-lg);
  margin-bottom: var(--spacing-6);
  color: var(--color-text-primary);
}

.skill-list {
  list-style: none;
  padding: 0;
  display: grid;
  grid-template-columns: 1fr;
  gap: var(--spacing-3);
}

.skill-item {
  font-size: var(--font-size-base);
  color: var(--color-text-secondary);
  padding-left: var(--spacing-4);
  position: relative;
  margin: 0;
}

.skill-item::before {
  content: '▸';
  position: absolute;
  left: 0;
  color: var(--color-primary-500);
  font-size: var(--font-size-lg);
}

@media (max-width: 640px) {
  .skill-category {
    padding: var(--spacing-6);
  }

  .skill-category h3 {
    font-size: var(--font-size-base);
    margin-bottom: var(--spacing-4);
  }

  .skill-item {
    font-size: var(--font-size-sm);
  }
}
</style>
