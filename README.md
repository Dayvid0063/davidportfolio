# 🌟 David Orji - Portfolio Website

A modern, multilingual portfolio website built with Nuxt 4, showcasing my work as a Full Stack Software Engineer. Features a stunning UI with smooth animations, dark mode aesthetics, and support for English, French, and Arabic languages.

[![Nuxt 4](https://img.shields.io/badge/Nuxt-4.3.0-00DC82?style=flat&logo=nuxt.js&logoColor=white)](https://nuxt.com/)
[![Vue 3](https://img.shields.io/badge/Vue-3.5.27-4FC08D?style=flat&logo=vue.js&logoColor=white)](https://vuejs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.x-3178C6?style=flat&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind-3.x-38B2AC?style=flat&logo=tailwind-css&logoColor=white)](https://tailwindcss.com/)

## ✨ Features

### 🌍 Internationalization (i18n)
- **Multi-language support**: English, French (Français), and Arabic (العربية)
- **RTL support** for Arabic language
- **Language switcher** in header (desktop & mobile)
- **Cookie-based persistence** - remembers user's language preference
- **Browser language detection** - automatically detects and sets user's preferred language
- **60+ translation keys** across all components

### 🎨 Design & UI
- **Modern dark theme** with vibrant emerald and teal accents
- **Glassmorphism effects** with backdrop blur
- **Smooth animations** and transitions
- **Floating particles** background effect
- **Responsive design** - mobile, tablet, and desktop optimized
- **Compact header** with backdrop blur for better visibility

### 📱 Sections
- **Hero Section**: Eye-catching introduction with animated background
- **About Section**: 
  - Professional bio with profile image
  - Animated skill bars (16+ technologies)
  - Certifications modal with 6+ certificates
- **Projects Section**: 
  - 14+ featured projects
  - Filter by category (All, Web App, Mobile, E-commerce)
  - View More/Less functionality
- **Contact Section**: 
  - Contact information cards
  - Working contact form with Formspree integration
  - Success/error message handling
- **Footer**: 
  - Social media links (GitHub, LinkedIn, Twitter)
  - Blog links (Medium, Hashnode)
  - Tech stack showcase
  - Quick navigation links

### 🛠️ Technical Features
- **Nuxt 4** with Vue 3 Composition API
- **TypeScript** for type safety
- **Tailwind CSS** for styling
- **@nuxtjs/i18n** for internationalization
- **Formspree** for contact form handling
- **Font Awesome** icons
- **Google Fonts** (DM Sans)
- **SEO optimized** with proper meta tags

## 🚀 Getting Started

### Prerequisites
- Node.js 18+ 
- npm or yarn

### Installation

1. Clone the repository:
```bash
git clone https://github.com/Dayvid0063/davidportfolio.git
cd davidportfolio
```

2. Install dependencies:
```bash
npm install
```

3. Create a `.env` file in the root directory:
```env
NUXT_PUBLIC_FORMSPREE_KEY=your_formspree_key_here
```

4. Start the development server:
```bash
npm run dev
```

5. Open your browser and navigate to `http://localhost:3000`

## 🌐 Language Support

The portfolio supports three languages:

| Language | Code | URL | Direction |
|----------|------|-----|-----------|
| English | `en` | `/` | LTR |
| French | `fr` | `/fr` | LTR |
| Arabic | `ar` | `/ar` | RTL |

### Adding a New Language

1. Create a new JSON file in `i18n/locales/` (e.g., `es.json`)
2. Add the locale configuration in `nuxt.config.ts`:
```typescript
{ code: 'es', iso: 'es-ES', file: 'es.json', name: 'Español', dir: 'ltr' }
```
3. Translate all keys from `en.json` to your new language
4. The language switcher will automatically include the new language

## 📁 Project Structure

```
davidportfolio/
├── components/
│   ├── AboutSection.vue       # About me section with skills
│   ├── ContactSection.vue     # Contact form and info
│   ├── FloatingParticles.vue  # Animated background particles
│   ├── Footer.vue             # Footer with links
│   ├── Header.vue             # Navigation header with i18n switcher
│   ├── HeroSection.vue        # Landing section
│   ├── ProjectCard.vue        # Individual project card
│   └── ProjectsSection.vue    # Projects showcase
├── i18n/
│   └── locales/
│       ├── en.json            # English translations
│       ├── fr.json            # French translations
│       └── ar.json            # Arabic translations
├── pages/
│   └── index.vue              # Main page
├── public/
│   └── assets/
│       └── images/            # Project images and profile
├── nuxt.config.ts             # Nuxt configuration
├── tailwind.config.js         # Tailwind configuration
└── package.json               # Dependencies
```

## 🎨 Customization

### Updating Text Content

To update any text on the website:

1. Open the appropriate translation file in `i18n/locales/`
2. Update the value for the key you want to change
3. **Important**: Update the same key in all three language files (en.json, fr.json, ar.json)

Example:
```json
// en.json
"footer": {
  "brandDescription": "Your new description here"
}

// fr.json
"footer": {
  "brandDescription": "Votre nouvelle description ici"
}

// ar.json
"footer": {
  "brandDescription": "وصفك الجديد هنا"
}
```

### Updating Projects

Edit the `allProjects` array in `components/ProjectsSection.vue`:
```typescript
{
  id: 1,
  title: 'Project Name',
  description: 'Project description',
  image: '/assets/images/project.png',
  technologies: ['Tech1', 'Tech2'],
  github: 'https://github.com/...',
  demo: 'https://demo-url.com',
  category: 'Web App' // or 'Mobile', 'E-commerce'
}
```

### Updating Skills

Edit the `skills` array in `components/AboutSection.vue`:
```typescript
{ name: 'Skill Name', level: 80, icon: 'fab fa-icon', category: 'Category' }
```

## 🔧 Configuration

### Environment Variables

| Variable | Description | Required |
|----------|-------------|----------|
| `NUXT_PUBLIC_FORMSPREE_KEY` | Formspree API key for contact form | Yes |

### Tailwind Colors

Custom colors are defined in `tailwind.config.js`:
- `navy-900`, `navy-800`, `navy-950` - Dark backgrounds
- `emerald-400`, `emerald-500` - Primary accent
- `teal-400`, `teal-500` - Secondary accent

## 📦 Build for Production

```bash
# Build the application
npm run build

# Preview the production build
npm run preview
```

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! Feel free to check the [issues page](https://github.com/Dayvid0063/davidportfolio/issues).

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 👨‍💻 Author

**David Orji**
- GitHub: [@Dayvid0063](https://github.com/Dayvid0063)
- LinkedIn: [David Orji](https://www.linkedin.com/in/david-orji-/)
- Twitter: [@sir_dayvido](https://x.com/sir_dayvido)
- Email: orjidavid0063@gmail.com

## 🙏 Acknowledgments

- Built with [Nuxt 4](https://nuxt.com/)
- Styled with [Tailwind CSS](https://tailwindcss.com/)
- Icons from [Font Awesome](https://fontawesome.com/)
- Fonts from [Google Fonts](https://fonts.google.com/)
- Form handling by [Formspree](https://formspree.io/)

---

⭐ If you like this project, please give it a star on GitHub!
