# 777 Garage — AI-Assisted Automotive Service Platform

&gt; A production-ready single-page business website built with AI collaboration tools, 
&gt; demonstrating modern frontend architecture, automated deployment, and conversion-focused UX.

🔗 **Live:** [777garage.com](https://777garage.com)

---

## Project Overview

777 Garage is a landing page for an automotive repair and detailing studio. 
The project was scoped, designed, and developed using AI-assisted workflows — 
from initial prompt engineering to production deployment.

**Key Business Goals:**
- Lead generation via WhatsApp-integrated contact form
- Service showcase with pricing transparency
- Mobile-first experience for on-the-go customers
- Cookie consent & analytics compliance (EU market)

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| **Framework** | React 18 + Vite |
| **Styling** | Tailwind CSS |
| **Animations** | Framer Motion |
| **Deployment** | cPanel (shared hosting) via SFTP |
| **Analytics** | Google Analytics 4 + Cookie Consent |
| **Forms** | WhatsApp API integration (direct chat routing) |

---

## AI Collaboration Workflow

This project demonstrates practical AI project management:

| Stage | AI Tool | My Role |
|-------|---------|---------|
| **Architecture** | ChatGPT / Claude | Prompt engineering, tech stack validation |
| **Design** | Midjourney / DALL-E | Art direction, brand consistency checks |
| **Code** | Cursor IDE + Copilot | Code review, customization, edge-case handling |
| **Copy** | GPT-4 | SEO optimization, multilingual adaptation |
| **QA** | AI-generated test cases | Manual validation, cross-browser testing |

**Result:** 70% faster delivery vs. traditional workflow while maintaining production code quality.

---

## Key Features

- **Responsive Design** — Optimized for 320px to 4K displays
- **Performance** — Lighthouse 95+ (Performance, Accessibility, SEO)
- **Lead Capture** — One-click WhatsApp contact with pre-filled service request
- **Legal Compliance** — GDPR-ready cookie banner with granular consent
- **Analytics** — Event tracking for form submissions and CTA clicks

777garage/
├── public/              # Static assets, favicon, OG images
├── src/
│   ├── components/      # Reusable UI (Button, Card, Section)
│   ├── sections/        # Page blocks (Hero, Services, Pricing, Contact)
│   ├── hooks/           # Custom React hooks (useAnalytics, useConsent)
│   ├── utils/           # Helpers (WhatsApp link generator, formatters)
│   └── App.jsx          # Main composition
├── .github/             # Deployment workflows (optional CI/CD)
└── vite.config.js       # Build optimization
