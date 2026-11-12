<script setup>
const currentYear = new Date().getFullYear()
</script>

<template>
  <footer class="app-footer">
    <div class="container">
      <div class="footer-content">
        <div class="footer-section">
          <h4>Munir Abubakar</h4>
          <p>Frontend Engineer focused on building reliable web applications.</p>
        </div>

        <div class="footer-section">
          <h4>Quick Links</h4>
          <nav class="footer-nav">
            <a href="#about">About</a>
            <a href="#projects">Work</a>
            <a href="#skills">Skills</a>
            <a href="#experience">Experience</a>
            <a href="#contact">Contact</a>
          </nav>
        </div>

        <div class="footer-section">
          <h4>Connect</h4>
          <div class="footer-links">
            <a href="https://www.linkedin.com/in/munir-abubakar-babb1a111/" target="_blank" rel="noopener noreferrer">LinkedIn</a>
            <a href="https://github.com/kosa4real" target="_blank" rel="noopener noreferrer">GitHub</a>
          </div>
        </div>
      </div>

      <div class="footer-bottom">
        <p>&copy; {{ currentYear }} Munir Abubakar. All rights reserved.</p>
        <p class="footer-credit">
          Designed and built with Vue 3 and Vite.
        </p>
      </div>
    </div>
  </footer>
</template>

<style scoped>
.app-footer {
  background-color: var(--color-bg-secondary);
  border-top: 1px solid var(--color-border);
  padding: var(--spacing-16) 0 var(--spacing-12) 0;
  margin-top: var(--spacing-24);
}

@media (max-width: 640px) {
  .app-footer {
    margin-top: var(--spacing-16);
    padding: var(--spacing-12) 0 var(--spacing-8) 0;
  }
}

.footer-content {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: var(--spacing-12);
  margin-bottom: var(--spacing-12);
  padding-bottom: var(--spacing-12);
  border-bottom: 1px solid var(--color-border);
}

@media (max-width: 1023px) {
  .footer-content {
    grid-template-columns: 1fr;
    gap: var(--spacing-8);
  }
}

.footer-section h4 {
  font-size: var(--font-size-base);
  font-weight: var(--font-weight-semibold);
  color: var(--color-text-primary);
  margin-bottom: var(--spacing-3);
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

.footer-section p {
  font-size: var(--font-size-sm);
  color: var(--color-text-secondary);
  line-height: var(--line-height-relaxed);
}

.footer-nav {
  display: flex;
  flex-direction: column;
  gap: var(--spacing-2);
}

.footer-nav a,
.footer-links a {
  font-size: var(--font-size-sm);
  color: var(--color-text-secondary);
  transition: color var(--transition-fast);
}

.footer-nav a:hover,
.footer-links a:hover {
  color: var(--color-primary-500);
}

.footer-links {
  display: flex;
  gap: var(--spacing-4);
}

.footer-bottom {
  text-align: center;
  padding-top: var(--spacing-8);
}

.footer-bottom p {
  font-size: var(--font-size-sm);
  color: var(--color-text-tertiary);
  margin-bottom: var(--spacing-2);
}

.footer-bottom p:last-child {
  margin-bottom: 0;
}

.footer-credit {
  margin-top: var(--spacing-3);
}

@media (max-width: 640px) {
  .footer-section h4 {
    font-size: var(--font-size-sm);
  }

  .footer-bottom p {
    font-size: var(--font-size-xs);
  }
}
</style>
