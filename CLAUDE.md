# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is the MAC Ethiopia (Medicos Art Club) website - a React-based single-page application for a non-profit organization that promotes artistic expression among medical students and doctors.

## Essential Commands

```bash
# Install dependencies (using pnpm - required for Vercel deployment)
pnpm install

# Start development server
pnpm dev

# Build for production
pnpm build

# Preview production build locally
pnpm preview

# Run ESLint
pnpm lint
```

## High-Level Architecture

### Tech Stack
- **React 18.3** with functional components and hooks
- **Vite** for build tooling and dev server
- **Tailwind CSS** for styling with custom theme colors (lightBlue: #49D3FF, darkBlue: #34445E)
- **React Router DOM** for client-side routing
- **Framer Motion & AOS** for animations
- **pnpm** as package manager (required for Vercel deployment)

### Project Structure
```
src/
├── components/     # Reusable UI components organized by feature
│   ├── about/     # About page components
│   ├── blog/      # Blog components (BlogCard, BlogContent, etc.)
│   ├── contact/   # Contact form and related components
│   ├── home/      # Homepage sections (Hero, Testimonials, etc.)
│   └── resources/ # Resource download components
├── screen/        # Page-level components that map to routes
├── constants/     # Static data (team members, blog posts, resources)
├── utilities/     # Shared utility components (Loader, Error, Success)
└── App.jsx        # Main routing configuration
```

### Key Architectural Patterns

1. **Component Organization**: Components are grouped by feature/page rather than type. Each major page has its own folder with related components.

2. **Data Management**: Static content (blog posts, team members, resources) is stored in `constants/` directory as JavaScript objects, not fetched from an API.

3. **Routing Structure**:
   - `/` - Home page
   - `/about` - About page with team members
   - `/blog` - Blog listing
   - `/blog/:id` - Individual blog posts
   - `/resources` - Downloadable resources (PDFs)
   - `/contact` - Contact form
   - `/privacy`, `/terms` - Legal pages

4. **Animation Strategy**: 
   - Framer Motion for complex component animations
   - AOS for simple scroll-triggered animations
   - Both libraries are used extensively throughout

5. **Responsive Design**: Custom Tailwind breakpoint `xs: 410px` added for fine-tuned mobile styling.

### Development Notes

- **Git Workflow**: Development happens on `development` branch, PRs go to `main`
- **Deployment**: Configured for Vercel with pnpm (see vercel.json)
- **SEO**: Comprehensive meta tags in index.html
- **No API Integration**: Currently all data is static
- **Image Assets**: Stored in `src/assets/images/` 
- **PDF Resources**: Stored in `src/assets/resources/`

### Common Tasks

- When adding new pages, create components in `src/screen/` and update routing in `App.jsx`
- Static content updates go in `src/constants/`
- Always use pnpm for package management to maintain Vercel compatibility
- Run `pnpm lint` before committing to catch ESLint errors