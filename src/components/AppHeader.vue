<script setup>
import { ref, computed } from 'vue'

const isMenuOpen = ref(false)
const isDarkMode = ref(localStorage.getItem('theme') === 'dark')

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
}

const toggleTheme = () => {
  isDarkMode.value = !isDarkMode.value
  localStorage.setItem('theme', isDarkMode.value ? 'dark' : 'light')
  updateTheme()
}

const updateTheme = () => {
  if (isDarkMode.value) {
    document.documentElement.style.colorScheme = 'dark'
  } else {
    document.documentElement.style.colorScheme = 'light'
  }
}

const closeMenu = () => {
  isMenuOpen.value = false
}

const scrollToSection = (id) => {
  const element = document.getElementById(id)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
    closeMenu()
  }
}

// Initialize theme on mount
if (localStorage.getItem('theme') === 'dark') {
  document.documentElement.style.colorScheme = 'dark'
} else {
  document.documentElement.style.colorScheme = 'light'
}
</script>

<template>
  <header class="app-header">
    <div class="container">
      <div class="header-content">
        <div class="logo">
          <a href="#" @click.prevent="scrollToSection('hero')" class="logo-text">
            Munir
          </a>
        </div>

        <nav class="nav-desktop hidden-mobile">
          <a href="#about" @click.prevent="scrollToSection('about')" class="nav-link">About</a>
          <a href="#projects" @click.prevent="scrollToSection('projects')" class="nav-link">Work</a>
          <a href="#skills" @click.prevent="scrollToSection('skills')" class="nav-link">Skills</a>
          <a href="#experience" @click.prevent="scrollToSection('experience')" class="nav-link">Experience</a>
          <a href="#contact" @click.prevent="scrollToSection('contact')" class="nav-link">Contact</a>
        </nav>

        <div class="header-actions">
          <button
            class="theme-toggle"
            @click="toggleTheme"
            :aria-label="isDarkMode ? 'Switch to light theme' : 'Switch to dark theme'"
            :title="isDarkMode ? 'Light mode' : 'Dark mode'"
          >
            <svg v-if="isDarkMode" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <circle cx="12" cy="12" r="5"></circle>
              <line x1="12" y1="1" x2="12" y2="3"></line>
              <line x1="12" y1="21" x2="12" y2="23"></line>
              <line x1="4.22" y1="4.22" x2="5.64" y2="5.64"></line>
              <line x1="18.36" y1="18.36" x2="19.78" y2="19.78"></line>
              <line x1="1" y1="12" x2="3" y2="12"></line>
              <line x1="21" y1="12" x2="23" y2="12"></line>
              <line x1="4.22" y1="19.78" x2="5.64" y2="18.36"></line>
              <line x1="18.36" y1="5.64" x2="19.78" y2="4.22"></line>
            </svg>
            <svg v-else width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"></path>
            </svg>
          </button>

          <button
            class="menu-toggle hidden-desktop"
            @click="toggleMenu"
            :aria-label="isMenuOpen ? 'Close menu' : 'Open menu'"
          >
            <span v-if="!isMenuOpen" class="hamburger">
              <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                <line x1="3" y1="6" x2="21" y2="6"></line>
                <line x1="3" y1="12" x2="21" y2="12"></line>
                <line x1="3" y1="18" x2="21" y2="18"></line>
              </svg>
            </span>
            <span v-else class="close-icon">
              <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                <line x1="18" y1="6" x2="6" y2="18"></line>
                <line x1="6" y1="6" x2="18" y2="18"></line>
              </svg>
            </span>
          </button>
        </div>
      </div>
    </div>

    <!-- Mobile Navigation Menu -->
    <nav v-if="isMenuOpen" class="nav-mobile hidden-desktop">
      <a href="#about" @click.prevent="scrollToSection('about')" class="nav-link-mobile">About</a>
      <a href="#projects" @click.prevent="scrollToSection('projects')" class="nav-link-mobile">Work</a>
      <a href="#skills" @click.prevent="scrollToSection('skills')" class="nav-link-mobile">Skills</a>
      <a href="#experience" @click.prevent="scrollToSection('experience')" class="nav-link-mobile">Experience</a>
      <a href="#contact" @click.prevent="scrollToSection('contact')" class="nav-link-mobile">Contact</a>
    </nav>
  </header>
</template>

<style scoped>
.app-header {
  position: sticky;
  top: 0;
  background-color: var(--color-bg-primary);
  border-bottom: 1px solid var(--color-border);
  z-index: var(--z-sticky);
  transition: border-color var(--transition-base), background-color var(--transition-base);
}

.header-content {
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 4rem;
  padding: 0 var(--spacing-6);
}

@media (max-width: 640px) {
  .header-content {
    padding: 0 var(--spacing-4);
  }
}

.logo {
  flex-shrink: 0;
}

.logo-text {
  font-size: var(--font-size-lg);
  font-weight: var(--font-weight-bold);
  color: var(--color-text-primary);
  cursor: pointer;
  transition: color var(--transition-fast);
}

.logo-text:hover {
  color: var(--color-primary-500);
}

.nav-desktop {
  display: flex;
  gap: var(--spacing-8);
  margin: 0 auto;
}

.nav-link {
  font-size: var(--font-size-base);
  color: var(--color-text-secondary);
  transition: color var(--transition-fast);
  position: relative;
}

.nav-link:hover {
  color: var(--color-primary-500);
}

.nav-link::after {
  content: '';
  position: absolute;
  bottom: -4px;
  left: 0;
  width: 0;
  height: 2px;
  background-color: var(--color-primary-500);
  transition: width var(--transition-fast);
}

.nav-link:hover::after {
  width: 100%;
}

.header-actions {
  display: flex;
  gap: var(--spacing-4);
  align-items: center;
  flex-shrink: 0;
}

.theme-toggle {
  background: none;
  border: none;
  padding: var(--spacing-2);
  cursor: pointer;
  color: var(--color-text-secondary);
  display: flex;
  align-items: center;
  justify-content: center;
  transition: color var(--transition-fast);
}

.theme-toggle:hover {
  color: var(--color-primary-500);
}

.theme-toggle:focus-visible {
  outline: 2px solid var(--color-primary-500);
  outline-offset: 2px;
  border-radius: var(--radius-md);
}

.menu-toggle {
  background: none;
  border: none;
  padding: var(--spacing-2);
  cursor: pointer;
  color: var(--color-text-primary);
  display: flex;
  align-items: center;
  justify-content: center;
  transition: color var(--transition-fast);
}

.menu-toggle:hover {
  color: var(--color-primary-500);
}

.menu-toggle:focus-visible {
  outline: 2px solid var(--color-primary-500);
  outline-offset: 2px;
  border-radius: var(--radius-md);
}

.nav-mobile {
  display: flex;
  flex-direction: column;
  gap: var(--spacing-2);
  padding: var(--spacing-4);
  border-top: 1px solid var(--color-border);
  animation: slideDown var(--transition-base);
}

@keyframes slideDown {
  from {
    opacity: 0;
    transform: translateY(-10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.nav-link-mobile {
  font-size: var(--font-size-base);
  color: var(--color-text-secondary);
  padding: var(--spacing-3) var(--spacing-4);
  border-radius: var(--radius-md);
  transition: background-color var(--transition-fast), color var(--transition-fast);
}

.nav-link-mobile:hover {
  background-color: var(--color-bg-secondary);
  color: var(--color-primary-500);
}

.nav-link-mobile:focus-visible {
  outline: 2px solid var(--color-primary-500);
  outline-offset: 2px;
}
</style>
