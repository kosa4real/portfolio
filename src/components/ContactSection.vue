<script setup>
import { ref } from 'vue'

const formData = ref({
  name: '',
  email: '',
  message: ''
})

const submitted = ref(false)
const error = ref(null)

const submitForm = () => {
  // Validate
  if (!formData.value.name || !formData.value.email || !formData.value.message) {
    error.value = 'Please fill in all fields'
    return
  }

  // Simple email validation
  const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/
  if (!emailRegex.test(formData.value.email)) {
    error.value = 'Please enter a valid email'
    return
  }

  // Since we don't have a backend, open email client
  const subject = `Portfolio Contact: ${formData.value.name}`
  const body = `Name: ${formData.value.name}\nEmail: ${formData.value.email}\n\nMessage:\n${formData.value.message}`
  const mailtoLink = `mailto:your-email@example.com?subject=${encodeURIComponent(subject)}&body=${encodeURIComponent(body)}`
  
  window.location.href = mailtoLink
  submitted.value = true
  error.value = null

  // Reset form after 2 seconds
  setTimeout(() => {
    formData.value = { name: '', email: '', message: '' }
    submitted.value = false
  }, 2000)
}
</script>

<template>
  <section id="contact" class="contact-section">
    <div class="container">
      <div class="contact-header">
        <h2>Have a product to build or a problem to solve?</h2>
        <p>I'm interested in connecting with teams building useful products, solving meaningful problems, and caring about the quality of their software.</p>
      </div>

      <div class="contact-content">
        <div class="contact-info">
          <div class="info-item">
            <h3>Email</h3>
            <a href="mailto:your-email@example.com" class="contact-link">your-email@example.com</a>
            <p class="info-note">Replace with your verified professional email</p>
          </div>

          <div class="info-item">
            <h3>Location</h3>
            <p>Kano, Nigeria</p>
          </div>

          <div class="info-item">
            <h3>Connect</h3>
            <div class="social-links">
              <a href="https://www.linkedin.com/in/munir-abubakar-babb1a111/" target="_blank" rel="noopener noreferrer" class="social-link" aria-label="LinkedIn">
                LinkedIn
              </a>
              <a href="https://github.com/kosa4real" target="_blank" rel="noopener noreferrer" class="social-link" aria-label="GitHub">
                GitHub
              </a>
            </div>
          </div>

          <div class="info-item">
            <h3>Resume / CV</h3>
            <a href="#" class="btn btn-secondary btn-small">
              Download CV
            </a>
            <p class="info-note">Configure when CV file is ready</p>
          </div>
        </div>

        <form class="contact-form" @submit.prevent="submitForm">
          <div class="form-group">
            <label for="name">Name</label>
            <input
              id="name"
              v-model="formData.name"
              type="text"
              placeholder="Your name"
              required
            />
          </div>

          <div class="form-group">
            <label for="email">Email</label>
            <input
              id="email"
              v-model="formData.email"
              type="email"
              placeholder="your@email.com"
              required
            />
          </div>

          <div class="form-group">
            <label for="message">Message</label>
            <textarea
              id="message"
              v-model="formData.message"
              placeholder="Tell me about your project or opportunity..."
              rows="6"
              required
            ></textarea>
          </div>

          <div v-if="error" class="error-message">
            {{ error }}
          </div>

          <div v-if="submitted" class="success-message">
            Thank you! Redirecting to email...
          </div>

          <button type="submit" class="btn btn-primary btn-large">
            Send Message
          </button>
        </form>
      </div>
    </div>
  </section>
</template>

<style scoped>
.contact-section {
  padding: var(--spacing-24) 0;
  background-color: var(--color-bg-secondary);
}

@media (max-width: 640px) {
  .contact-section {
    padding: var(--spacing-16) 0;
  }
}

.contact-header {
  text-align: center;
  margin-bottom: var(--spacing-16);
  max-width: 600px;
  margin-left: auto;
  margin-right: auto;
}

.contact-header h2 {
  margin-bottom: var(--spacing-4);
}

.contact-header p {
  font-size: var(--font-size-lg);
  color: var(--color-text-secondary);
}

.contact-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: var(--spacing-12);
  align-items: start;
}

@media (max-width: 1023px) {
  .contact-content {
    grid-template-columns: 1fr;
    gap: var(--spacing-12);
  }
}

.contact-info {
  display: flex;
  flex-direction: column;
  gap: var(--spacing-8);
}

.info-item h3 {
  font-size: var(--font-size-base);
  font-weight: var(--font-weight-semibold);
  color: var(--color-text-primary);
  margin-bottom: var(--spacing-2);
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

.info-item p {
  font-size: var(--font-size-base);
  color: var(--color-text-secondary);
}

.contact-link {
  font-size: var(--font-size-base);
  font-weight: var(--font-weight-medium);
  display: inline-block;
  margin-bottom: var(--spacing-2);
}

.info-note {
  font-size: var(--font-size-sm);
  color: var(--color-text-tertiary);
  margin-top: var(--spacing-2);
}

.social-links {
  display: flex;
  gap: var(--spacing-4);
  margin-bottom: var(--spacing-2);
}

.social-link {
  font-size: var(--font-size-base);
  color: var(--color-primary-500);
  text-decoration: none;
  transition: color var(--transition-fast);
}

.social-link:hover {
  color: var(--color-primary-600);
}

.contact-form {
  background-color: var(--color-bg-primary);
  padding: var(--spacing-8);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-xl);
}

.form-group {
  margin-bottom: var(--spacing-6);
}

.form-group:last-of-type {
  margin-bottom: var(--spacing-8);
}

.form-group label {
  display: block;
  margin-bottom: var(--spacing-2);
  font-weight: var(--font-weight-medium);
  font-size: var(--font-size-base);
  color: var(--color-text-primary);
}

.form-group input,
.form-group textarea {
  width: 100%;
  font-family: var(--font-family-base);
  font-size: var(--font-size-base);
  padding: var(--spacing-3) var(--spacing-4);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-lg);
  background-color: var(--color-bg-secondary);
  color: var(--color-text-primary);
  transition: border-color var(--transition-fast), box-shadow var(--transition-fast);
}

.form-group input:focus,
.form-group textarea:focus {
  outline: none;
  border-color: var(--color-primary-500);
  box-shadow: 0 0 0 3px var(--color-primary-50);
  background-color: var(--color-bg-primary);
}

.form-group input::placeholder,
.form-group textarea::placeholder {
  color: var(--color-text-tertiary);
}

.error-message {
  padding: var(--spacing-4);
  background-color: #fee2e2;
  color: #dc2626;
  border-radius: var(--radius-lg);
  font-size: var(--font-size-sm);
  margin-bottom: var(--spacing-4);
  border-left: 4px solid #dc2626;
}

.success-message {
  padding: var(--spacing-4);
  background-color: #dcfce7;
  color: #16a34a;
  border-radius: var(--radius-lg);
  font-size: var(--font-size-sm);
  margin-bottom: var(--spacing-4);
  border-left: 4px solid #16a34a;
}

.contact-form .btn {
  width: 100%;
}

@media (max-width: 640px) {
  .contact-form {
    padding: var(--spacing-6);
  }

  .contact-info {
    gap: var(--spacing-6);
  }

  .info-item h3 {
    font-size: var(--font-size-sm);
  }
}
</style>
