# Quick Start Guide

Get the portfolio up and running in minutes.

## 1. Development Setup (2 minutes)

```bash
# Install dependencies (one time)
npm install

# Start dev server
npm run dev

# Open http://localhost:5173 in your browser
# Dev server includes hot module replacement (HMR) — changes update instantly
```

## 2. Customize Your Information (10 minutes)

### Update Email
**File**: `src/components/ContactSection.vue` (line ~45)
```vue
<a href="mailto:your-email@example.com" class="contact-link">
  your-email@example.com
</a>
```

### Update LinkedIn & GitHub
**File**: `src/components/ContactSection.vue` (lines ~71–77)
```vue
<a href="https://linkedin.com/in/your-profile" target="_blank" rel="noopener noreferrer" class="social-link">
  LinkedIn
</a>
<a href="https://github.com/your-username" target="_blank" rel="noopener noreferrer" class="social-link">
  GitHub
</a>
```

### Update CV Download
**File**: `src/components/ContactSection.vue` (line ~84)
```vue
<a href="/your-cv.pdf" class="btn btn-secondary btn-small">
  Download CV
</a>
```

Also update in **`src/components/AppFooter.vue`** if needed.

### Update Project Information
**File**: `src/components/ProjectsShowcase.vue` (lines ~10–80)

Each project has this structure:
```javascript
{
  id: 'project-id',
  name: 'Project Name',
  category: 'Category · Subcategory',
  description: 'Short description...',
  liveUrl: 'https://project-url.com/',
  ctaText: 'View Live Project',
  technologies: ['Vue.js', 'JavaScript', 'Axios'],
  featured: true, // or false
  caseStudy: {
    problem: 'What problem did it solve?',
    role: 'Your specific role',
    approach: 'How did you approach it?',
    challenges: 'What challenges did you face?',
    outcomes: 'What were the results?'
  }
}
```

## 3. Build for Production (1 minute)

```bash
# Create optimized production build
npm run build

# Output goes to dist/ folder
# Ready to deploy!
```

## 4. Deploy (Choose One)

### Vercel (Easiest)
```bash
npm install -g vercel
vercel login
npm run build
vercel --prod
```

### Netlify
```bash
npm install -g netlify-cli
netlify login
npm run build
netlify deploy --prod --dir=dist
```

### GitHub Pages
Push to GitHub, enable Actions, automatic deploy.

### Manual Upload
Upload `dist/` folder contents to your web server.

## 5. Verify Deployment

- [ ] Site loads at your domain
- [ ] All links work
- [ ] Theme toggle works
- [ ] Mobile menu works
- [ ] Contact form works
- [ ] No console errors
- [ ] Favicon displays

## Useful Commands

```bash
# Development server (with HMR)
npm run dev

# Production build
npm run build

# Preview production build locally
npm run preview

# Check for outdated packages
npm outdated
```

## Common Customizations

### Change Accent Color
**File**: `src/style.css` (line ~20)
```css
--color-primary-500: #1e5aa8; /* Change this to your color */
```

### Change Background
**File**: `src/style.css` (line ~32)
```css
--color-bg-primary: #fafaf8; /* Light background */
```

### Update Page Title
**File**: `index.html` (line ~5)
```html
<title>Your Name — Your Title | Your Specialty</title>
```

### Update Meta Description
**File**: `index.html` (line ~6)
```html
<meta name="description" content="Your professional summary here." />
```

## Troubleshooting

### Dev server won't start
```bash
# Clear cache and reinstall
rm -rf node_modules package-lock.json
npm install
npm run dev
```

### Build fails
```bash
# Check Node version
node --version  # Should be 16+

# Clear cache
rm -rf dist
npm run build
```

### Theme not persisting
- Check browser localStorage is enabled
- Disable extensions blocking storage
- Try incognito window to test

### Contact form not working
- Ensure email client is installed (for mailto fallback)
- For custom backend, see `ContactSection.vue` for integration

## File Organization

```
src/
├── components/     ← Edit these for content
│   ├── AppHeader.vue (navigation, theme)
│   ├── HeroSection.vue (main headline, CTAs)
│   ├── AboutSection.vue (bio, timeline)
│   ├── ProjectsShowcase.vue (projects, case studies)
│   ├── SkillsSection.vue (skills list)
│   ├── EngineeringApproach.vue (principles)
│   ├── ContactSection.vue (contact form)
│   └── AppFooter.vue (footer)
├── style.css       ← Edit for colors, fonts, spacing
└── App.vue         ← Main app (usually no changes needed)

index.html         ← Edit for page title, meta tags
```

## Design System Variables

All customizable via `src/style.css`:

```css
:root {
  /* Colors */
  --color-primary-500: #1e5aa8;  /* Main accent */
  --color-text-primary: #1a1815; /* Main text */
  --color-bg-primary: #fafaf8;   /* Background */
  
  /* Typography */
  --font-size-base: 1rem;     /* Base size */
  --font-size-3xl: 1.875rem;  /* Large headings */
  
  /* Spacing */
  --spacing-4: 1rem;   /* 16px */
  --spacing-8: 2rem;   /* 32px */
  
  /* Border Radius */
  --radius-lg: 0.75rem; /* 12px */
  
  /* Shadows */
  --shadow-lg: 0 10px 15px ...;
  
  /* Transitions */
  --transition-base: 200ms cubic-bezier(...);
}
```

Change any variable and it updates throughout the site automatically.

## Documentation

- **README.md**: Full setup and customization guide
- **DEPLOYMENT.md**: Detailed deployment instructions
- **IMPLEMENTATION_SUMMARY.md**: Technical overview
- **QUICK_START.md**: This file (quick reference)

## Next Steps

1. ✅ Install dependencies: `npm install`
2. ✅ Start dev server: `npm run dev`
3. ✅ Customize personal information (email, links, projects)
4. ✅ Build: `npm run build`
5. ✅ Deploy: Choose platform and follow deployment guide
6. ✅ Test: Verify all functionality at production URL

## Questions?

Refer to the full documentation:
- Vue 3: https://vuejs.org
- Vite: https://vitejs.dev
- HTML/CSS: https://developer.mozilla.org

---

**Ready?** Run `npm install && npm run dev` and get started!
