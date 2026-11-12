# Munir Abubakar — Personal Portfolio

A modern, responsive personal portfolio website showcasing professional frontend engineering experience, fintech projects, and technical skills. Built with Vue 3, Vite, and a thoughtfully designed component system.

## Features

- **Responsive Design**: Optimized for mobile (320px+), tablet (640px+), and desktop (1024px+) viewports
- **Light & Dark Theme**: Automatic theme detection with manual toggle and localStorage persistence
- **Accessible**: Semantic HTML, ARIA labels, keyboard navigation, focus management, and reduced-motion support
- **Performance**: Optimized builds, lazy-loaded assets, and clean production output
- **SEO Ready**: Complete metadata, Open Graph tags, canonical URLs, and semantic structure
- **Interactive**: Smooth animations, expandable project case studies, and functional contact form

## Project Structure

```
munir-portfolio/
├── public/                 # Static assets
│   ├── favicon.svg        # Brand favicon
│   └── icons.svg          # Icon library
├── src/
│   ├── components/        # Reusable Vue components
│   │   ├── AppHeader.vue              # Navigation & theme toggle
│   │   ├── HeroSection.vue            # Hero with CTAs
│   │   ├── AboutSection.vue           # Bio and career timeline
│   │   ├── ProjectsShowcase.vue       # Featured projects grid
│   │   ├── ProjectCard.vue            # Individual project card
│   │   ├── EngineeringApproach.vue    # Engineering principles
│   │   ├── SkillsSection.vue          # Organized skill categories
│   │   ├── ContactSection.vue         # Contact form & links
│   │   └── AppFooter.vue              # Footer with links
│   ├── App.vue            # Root component
│   ├── main.js            # Vue app entry
│   └── style.css          # Global styles & design system
├── index.html             # HTML entry point with SEO
├── vite.config.js         # Vite build configuration
├── package.json           # Dependencies and scripts
└── README.md              # This file
```

## Design System

The portfolio uses a comprehensive design system with CSS custom properties:

- **Colors**: Warm off-white background (#fafaf8), deep charcoal text (#1a1815), cobalt blue accent (#1e5aa8)
- **Typography**: System fonts, 6 heading levels, 10 font sizes, 4 font weights
- **Spacing**: 12-point scale (4px, 8px, 12px, 16px... 128px)
- **Shadows**: 5 carefully calibrated shadow levels
- **Transitions**: Fast (150ms), base (200ms), slow (300ms) with easing curves
- **Radius**: 4 border radius options (6px, 8px, 12px, 16px, 24px)

All design tokens are customizable via CSS variables in `src/style.css`.

## Getting Started

### Prerequisites

- Node.js 16+ and npm 7+

### Installation

```bash
# Clone or navigate to the project
cd munir-portfolio

# Install dependencies
npm install
```

### Development

```bash
# Start the development server
npm run dev

# The site will be available at http://localhost:5173
```

The dev server includes hot module replacement (HMR) for instant feedback on changes.

### Building for Production

```bash
# Create an optimized production build
npm run build

# Preview the production build locally
npm run preview
```

The production build output is in the `dist/` directory.

## Configuration

### Customize Portfolio Content

Edit component files to customize content:

- **Hero Section**: `src/components/HeroSection.vue`
- **About Section**: `src/components/AboutSection.vue`
- **Projects**: `src/components/ProjectsShowcase.vue` (project data defined inline)
- **Skills**: `src/components/SkillsSection.vue`
- **Contact**: `src/components/ContactSection.vue`

### Contact Form

The contact form currently opens the user's email client with a mailto link. To add a backend:

1. Replace the `submitForm` method in `src/components/ContactSection.vue`
2. Point to your backend API endpoint
3. Handle form submission server-side

### Update Metadata

Edit `index.html` to customize:

- Page title and description
- Open Graph tags for social sharing
- Twitter card metadata
- Theme color
- Canonical URL

### Personal Details Placeholders

The following placeholders should be updated with real information:

- **Email**: In `ContactSection.vue` and `index.html` meta tags
- **LinkedIn & GitHub**: In `ContactSection.vue` and `AppFooter.vue`
- **CV Download**: In `ContactSection.vue`
- **Canonical URL**: In `index.html`
- **OG Image**: Provide `/og-image.jpg` in the public folder

## Responsive Breakpoints

The portfolio uses mobile-first design with these breakpoints:

- **Mobile**: 320px – 639px
- **Tablet**: 640px – 1023px
- **Desktop**: 1024px+

All components adapt gracefully across breakpoints with no horizontal overflow.

## Accessibility

- ✓ Semantic HTML5 structure
- ✓ ARIA labels and roles where needed
- ✓ Keyboard navigation throughout
- ✓ Visible focus states on all interactive elements
- ✓ Proper heading hierarchy (h1 → h6)
- ✓ Descriptive alt text on images (for future image content)
- ✓ Color contrast meets WCAG AA standards
- ✓ `prefers-reduced-motion` support for animations

## Performance

The production build includes:

- CSS minification
- JavaScript minification and tree-shaking
- Gzip compression ready
- Optimized bundle size (~33KB gzipped JavaScript)
- No unused dependencies
- Lazy-loaded assets
- Semantic HTML for fast rendering

Current build metrics:
- HTML: ~2.18 KB (0.81 KB gzipped)
- CSS: ~31.64 KB (5.40 KB gzipped)
- JS: ~91.37 KB (33.80 KB gzipped)

## Deployment

### Deploy to Vercel (Recommended)

```bash
# Install Vercel CLI
npm install -g vercel

# Deploy
vercel
```

Vercel automatically optimizes and deploys the built site.

### Deploy to Netlify

```bash
# Install Netlify CLI
npm install -g netlify-cli

# Deploy
netlify deploy --prod --dir=dist
```

### Deploy to GitHub Pages

```bash
# Build the project
npm run build

# Deploy dist/ folder to your gh-pages branch
# Manual: Copy dist/ contents to gh-pages branch
# Or use: npx gh-pages -d dist
```

### Manual Deployment

1. Run `npm run build`
2. Upload the `dist/` folder contents to your web server
3. Ensure your server serves `index.html` for all routes (SPA routing)

## Environment Variables

Create a `.env` file if needed for build-time variables:

```
VITE_CONTACT_EMAIL=your-email@example.com
VITE_API_ENDPOINT=https://api.example.com
```

Reference in components: `import.meta.env.VITE_*`

## Browser Support

- Chrome/Edge 90+
- Firefox 88+
- Safari 14+
- Mobile browsers (iOS Safari, Chrome Mobile)

The portfolio uses modern CSS and JavaScript features; polyfills are not included.

## Customization Guide

### Changing Colors

Edit CSS variables in `src/style.css` `:root` selector:

```css
:root {
  --color-primary-500: #1e5aa8; /* Change accent color */
  --color-text-primary: #1a1815; /* Change main text */
  --color-bg-primary: #fafaf8; /* Change background */
}
```

### Adding Sections

1. Create a new component in `src/components/YourSection.vue`
2. Import in `src/App.vue`
3. Add to the template in the `<main>` element

### Modifying Typography

Edit font sizes, weights, and line heights in `src/style.css`:

```css
:root {
  --font-size-base: 1rem; /* Default size */
  --font-weight-bold: 700; /* Heading weight */
}
```

## Testing

To test the site:

1. **Desktop**: Use Chrome DevTools or browser DevTools
2. **Mobile**: Use responsive design mode or test on actual devices
3. **Accessibility**: Use axe DevTools browser extension
4. **Performance**: Use Lighthouse in Chrome DevTools

### Key Testing Areas

- [ ] All navigation links scroll to correct sections
- [ ] Theme toggle switches between light/dark modes
- [ ] Mobile menu opens/closes properly
- [ ] Contact form validates and submits
- [ ] Project cards expand/collapse smoothly
- [ ] No console errors
- [ ] All images load without errors
- [ ] Responsive layout at 320px, 768px, 1024px widths
- [ ] Keyboard navigation works throughout
- [ ] Focus states visible on all buttons/links

## Troubleshooting

### Site won't build

```bash
# Clear node_modules and reinstall
rm -rf node_modules package-lock.json
npm install
npm run build
```

### Dev server won't start

```bash
# Check port 5173 isn't in use
lsof -i :5173

# Try alternate port
npm run dev -- --port 3000
```

### Theme not persisting

Check that localStorage is enabled in browser and not blocked by extensions.

### Slow build times

- Close other applications
- Check disk space
- Update Node.js to latest LTS version

## License

© 2024 Munir Abubakar. All rights reserved.

## Support

For issues or questions, review the code comments or consult the Vue 3 and Vite documentation:

- [Vue 3 Docs](https://vuejs.org)
- [Vite Docs](https://vitejs.dev)
- [MDN Web Docs](https://developer.mozilla.org)

---

**Last Updated**: November 2024
**Built with**: Vue 3, Vite, modern CSS, vanilla JavaScript
