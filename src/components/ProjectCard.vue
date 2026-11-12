<script setup>
import { ref } from 'vue'

defineProps({
  project: {
    type: Object,
    required: true,
    validator: (obj) => {
      return obj.id && obj.name && obj.category && obj.description
    }
  },
  featured: {
    type: Boolean,
    default: false
  }
})

const emit = defineEmits(['select'])

const isExpanded = ref(false)

const toggleExpand = () => {
  isExpanded.value = !isExpanded.value
  emit('select', isExpanded.value)
}
</script>

<template>
  <article :class="['project-card', { featured, expanded: isExpanded }]">
    <div class="card-header" @click="toggleExpand">
      <div class="card-title-section">
        <p class="card-category">{{ project.category }}</p>
        <h3 class="card-title">{{ project.name }}</h3>
      </div>
      <button class="expand-toggle" :aria-label="`${isExpanded ? 'Collapse' : 'Expand'} ${project.name} details`">
        <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <polyline points="6 9 12 15 18 9"></polyline>
        </svg>
      </button>
    </div>

    <div class="card-content">
      <p class="card-description">{{ project.description }}</p>

      <div class="card-tags">
        <span v-for="tech in project.technologies" :key="tech" class="tag">
          {{ tech }}
        </span>
      </div>

      <div v-if="isExpanded && project.caseStudy" class="case-study">
        <div v-if="project.caseStudy.problem" class="case-section">
          <h4>Problem</h4>
          <p>{{ project.caseStudy.problem }}</p>
        </div>

        <div v-if="project.caseStudy.role" class="case-section">
          <h4>My Role</h4>
          <p>{{ project.caseStudy.role }}</p>
        </div>

        <div v-if="project.caseStudy.approach" class="case-section">
          <h4>Technical Approach</h4>
          <p>{{ project.caseStudy.approach }}</p>
        </div>

        <div v-if="project.caseStudy.challenges" class="case-section">
          <h4>Challenges & Solutions</h4>
          <p>{{ project.caseStudy.challenges }}</p>
        </div>

        <div v-if="project.caseStudy.outcomes" class="case-section">
          <h4>Outcomes</h4>
          <p>{{ project.caseStudy.outcomes }}</p>
        </div>
      </div>

      <div class="card-actions">
        <a v-if="project.liveUrl" :href="project.liveUrl" target="_blank" rel="noopener noreferrer" class="btn btn-secondary btn-small">
          {{ project.ctaText || 'View Project' }} →
        </a>
        <button class="btn btn-tertiary btn-small" @click.stop="toggleExpand">
          {{ isExpanded ? 'Hide Details' : 'View Details' }}
        </button>
      </div>
    </div>
  </article>
</template>

<style scoped>
.project-card {
  border: 1px solid var(--color-border);
  border-radius: var(--radius-xl);
  overflow: hidden;
  transition: all var(--transition-base);
  background-color: var(--color-bg-secondary);
}

.project-card:hover {
  border-color: var(--color-primary-500);
  box-shadow: var(--shadow-lg);
}

.project-card.featured {
  grid-column: 1 / -1;
}

@media (max-width: 767px) {
  .project-card.featured {
    grid-column: 1;
  }
}

.card-header {
  padding: var(--spacing-6);
  cursor: pointer;
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  gap: var(--spacing-4);
  border-bottom: 1px solid var(--color-border);
  transition: background-color var(--transition-fast);
}

.card-header:hover {
  background-color: var(--color-bg-tertiary);
}

.card-title-section {
  flex: 1;
}

.card-category {
  font-size: var(--font-size-sm);
  font-weight: var(--font-weight-semibold);
  color: var(--color-primary-500);
  text-transform: uppercase;
  letter-spacing: 0.05em;
  margin-bottom: var(--spacing-2);
}

.card-title {
  font-size: var(--font-size-2xl);
  color: var(--color-text-primary);
  margin: 0;
}

.expand-toggle {
  background: none;
  border: none;
  padding: var(--spacing-2);
  cursor: pointer;
  color: var(--color-text-secondary);
  display: flex;
  align-items: center;
  justify-content: center;
  transition: transform var(--transition-base), color var(--transition-base);
  flex-shrink: 0;
}

.expand-toggle:hover {
  color: var(--color-primary-500);
}

.project-card.expanded .expand-toggle {
  transform: rotate(180deg);
}

.card-content {
  padding: var(--spacing-6);
}

.card-description {
  font-size: var(--font-size-base);
  line-height: var(--line-height-relaxed);
  color: var(--color-text-secondary);
  margin-bottom: var(--spacing-6);
}

.card-tags {
  display: flex;
  flex-wrap: wrap;
  gap: var(--spacing-2);
  margin-bottom: var(--spacing-6);
}

.tag {
  display: inline-block;
  padding: var(--spacing-2) var(--spacing-3);
  background-color: var(--color-primary-50);
  color: var(--color-primary-600);
  border-radius: var(--radius-md);
  font-size: var(--font-size-sm);
  font-weight: var(--font-weight-medium);
}

.case-study {
  margin-bottom: var(--spacing-6);
  padding-top: var(--spacing-6);
  border-top: 1px solid var(--color-border);
}

.case-section {
  margin-bottom: var(--spacing-6);
}

.case-section:last-child {
  margin-bottom: 0;
}

.case-section h4 {
  font-size: var(--font-size-lg);
  font-weight: var(--font-weight-semibold);
  color: var(--color-text-primary);
  margin-bottom: var(--spacing-2);
}

.case-section p {
  font-size: var(--font-size-base);
  line-height: var(--line-height-relaxed);
  color: var(--color-text-secondary);
}

.card-actions {
  display: flex;
  gap: var(--spacing-3);
  flex-wrap: wrap;
  margin-top: var(--spacing-4);
}

.card-actions .btn {
  flex: 1;
  min-width: 140px;
}

@media (max-width: 640px) {
  .card-header {
    padding: var(--spacing-4);
  }

  .card-content {
    padding: var(--spacing-4);
  }

  .card-title {
    font-size: var(--font-size-xl);
  }

  .card-actions {
    flex-direction: column;
  }

  .card-actions .btn {
    width: 100%;
  }
}
</style>
