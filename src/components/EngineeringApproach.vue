<script setup>
const principles = [
  {
    id: 'understand',
    title: 'Understand the Problem',
    description: 'I first try to understand the user, business requirements, and expected behaviour before deciding how to implement a feature.',
    icon: 'search'
  },
  {
    id: 'maintainability',
    title: 'Build for Maintainability',
    description: 'I value clear component boundaries, reusable patterns, consistent naming, and code that other developers can understand.'
  },
  {
    id: 'real-world',
    title: 'Handle Real-World States',
    description: 'I pay attention to API responses, loading indicators, validation, empty states, errors, and permissions instead of focusing only on the ideal successful flow.'
  },
  {
    id: 'improve',
    title: 'Keep Improving',
    description: 'I learn continuously, review existing implementations, and look for opportunities to improve the quality and consistency of my work.'
  }
]
</script>

<template>
  <section id="approach" class="approach-section">
    <div class="container">
      <div class="section-header">
        <h2>How I Approach Engineering</h2>
        <p>Four principles that guide my work on every project.</p>
      </div>

      <div class="principles-grid">
        <div v-for="principle in principles" :key="principle.id" class="principle-card">
          <div class="principle-icon">
            <svg width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
              <template v-if="principle.id === 'understand'">
                <!-- Search icon -->
                <circle cx="11" cy="11" r="8"></circle>
                <path d="m21 21-4.35-4.35"></path>
              </template>
              <template v-else-if="principle.id === 'maintainability'">
                <!-- Layers icon -->
                <path d="M12 2L2 7l10 5 10-5-10-5z"></path>
                <path d="M2 17l10 5 10-5"></path>
                <path d="M2 12l10 5 10-5"></path>
              </template>
              <template v-else-if="principle.id === 'real-world'">
                <!-- Alert icon -->
                <path d="M10.29 3.86L1.82 18a2 2 0 0 0 1.71 3.05h16.94a2 2 0 0 0 1.71-3.05L13.71 3.86a2 2 0 0 0-3.42 0z"></path>
                <line x1="12" y1="9" x2="12" y2="13"></line>
                <line x1="12" y1="17" x2="12.01" y2="17"></line>
              </template>
              <template v-else-if="principle.id === 'improve'">
                <!-- Trending up icon -->
                <polyline points="23 6 13.46 15.54 8 10.09 1 17"></polyline>
                <polyline points="17 6 23 6 23 12"></polyline>
              </template>
            </svg>
          </div>
          <h3>{{ principle.title }}</h3>
          <p>{{ principle.description }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.approach-section {
  padding: var(--spacing-24) 0;
}

@media (max-width: 640px) {
  .approach-section {
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

.principles-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: var(--spacing-8);
}

@media (max-width: 1023px) {
  .principles-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 640px) {
  .principles-grid {
    grid-template-columns: 1fr;
    gap: var(--spacing-6);
  }
}

.principle-card {
  padding: var(--spacing-8);
  text-align: center;
  transition: all var(--transition-base);
}

.principle-card:hover {
  transform: translateY(-4px);
}

.principle-icon {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 64px;
  height: 64px;
  margin: 0 auto var(--spacing-6);
  color: var(--color-primary-500);
  background-color: var(--color-primary-50);
  border-radius: var(--radius-lg);
  transition: all var(--transition-base);
}

.principle-card:hover .principle-icon {
  background-color: var(--color-primary-100);
  color: var(--color-primary-600);
  transform: scale(1.1);
}

.principle-card h3 {
  font-size: var(--font-size-lg);
  margin-bottom: var(--spacing-3);
  color: var(--color-text-primary);
}

.principle-card p {
  font-size: var(--font-size-base);
  line-height: var(--line-height-relaxed);
  color: var(--color-text-secondary);
}

@media (max-width: 640px) {
  .principle-card {
    padding: var(--spacing-6);
    text-align: left;
  }

  .principle-icon {
    margin-left: 0;
    margin-bottom: var(--spacing-4);
  }

  .principle-card h3 {
    font-size: var(--font-size-base);
  }

  .principle-card p {
    font-size: var(--font-size-sm);
  }
}
</style>
