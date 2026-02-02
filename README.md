# Yasir Kopi - Vue 3 Migration

This is the Vue 3 + Vite migration of the original Yasir Kopi HTML/Tailwind project.

## Project Structure

```
src/
├── components/
│   ├── Navbar.vue          # Fixed navigation with mobile menu
│   ├── Hero.vue            # Home section with coffee background
│   ├── ProductSection.vue  # Interactive coffee menu showcase
│   └── AboutSection.vue    # About us section
├── App.vue                 # Main app component
├── main.js                 # App entry point
└── style.css               # Global styles with Tailwind
```

## Features Migrated

✅ **Navbar Component**
- Fixed navigation with scroll effect
- Mobile responsive menu
- Smooth animations

✅ **Hero Component**
- Full-screen hero section
- Coffee background image
- Call-to-action button

✅ **ProductSection Component**
- Interactive coffee menu selection
- Dynamic product details display
- Hover effects and animations
- Embedded Google Maps
- Mobile responsive layout

✅ **AboutSection Component**
- Grid layout with background images
- Contact information
- Newsletter subscription input

## Tech Stack

- Vue 3 (Composition API with `<script setup>`)
- Vite
- Tailwind CSS
- Font Awesome icons

## Getting Started

### Development

```bash
cd yasir-kopi-vue
npm run dev
```

The app will be available at `http://localhost:5173/`

### Build for Production

```bash
npm run build
```

### Preview Production Build

```bash
npm run preview
```

## Design Preservation

All Tailwind classes from the original HTML have been preserved exactly to maintain the same design. Custom CSS animations and effects are maintained in `src/style.css`.

## Key Improvements

- **Component-based architecture**: Easier to maintain and reuse
- **Reactive state management**: Using Vue's Composition API
- **Better performance**: Vite's fast HMR and optimized builds
- **Type-safe**: Ready for TypeScript migration if needed
- **Modern tooling**: ESLint, PostCSS, and more
