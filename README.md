# Limitless - MVP0

<div align="center">
  <h3>🚀 Next-Generation Subscription Platform</h3>
  <p>Built with Next.js, Supabase, Stripe & AI-powered features</p>
  
  ![Next.js](https://img.shields.io/badge/Next.js-15.5-black?style=flat-square&logo=next.js)
  ![TypeScript](https://img.shields.io/badge/TypeScript-5.0-blue?style=flat-square&logo=typescript)
  ![Supabase](https://img.shields.io/badge/Supabase-2.0-green?style=flat-square&logo=supabase)
  ![Stripe](https://img.shields.io/badge/Stripe-18.5-purple?style=flat-square&logo=stripe)
  ![License](https://img.shields.io/badge/License-Private-red?style=flat-square)
</div>

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Getting Started](#getting-started)
- [Project Structure](#project-structure)
- [Environment Variables](#environment-variables)
- [Development](#development)
- [Deployment](#deployment)
- [Testing](#testing)
- [Documentation](#documentation)
- [Contributing](#contributing)

## 🎯 Overview

Limitless is a modern subscription management platform offering three tiers of service (ONE, EVOLVE, ULTIMATE) with seamless payment processing, multi-language support, and enterprise-grade security. Built for the European market with GDPR compliance at its core.

### MVP0 Goals
- ✅ Multi-tier subscription system
- ✅ Stripe Checkout integration with automatic VAT handling
- ✅ Multi-language support (FR, NL, EN)
- ✅ GDPR-compliant data handling
- ✅ Automated invoicing via Odoo
- ✅ Email automation with Brevo
- ✅ Real-time analytics and monitoring

## ✨ Features

### Core Functionality
- **🔐 Authentication**: Secure auth flow with Supabase Auth
- **💳 Payments**: Stripe Checkout with automatic tax calculation
- **🌍 Internationalization**: Full support for French, Dutch, and English
- **📧 Email Automation**: Transactional emails via Brevo
- **📊 Analytics**: GTM/GA4 integration with Hotjar for insights
- **💬 Support**: Integrated Intercom chat
- **🧾 Invoicing**: Automated invoice generation with Odoo

### Subscription Tiers
| Plan | Features | Price |
|------|----------|-------|
| **ONE** | Basic features, Email support | €X/month |
| **EVOLVE** | Advanced features, Priority support | €X/month |
| **ULTIMATE** | All features, Dedicated support | €X/month |

## 🛠 Tech Stack

### Frontend
- **Framework**: [Next.js 15.5](https://nextjs.org/) (App Router)
- **Styling**: [Tailwind CSS](https://tailwindcss.com/) + [shadcn/ui](https://ui.shadcn.com/)
- **Language**: TypeScript (strict mode)
- **Icons**: [Lucide React](https://lucide.dev/)

### Backend
- **Database**: [Supabase](https://supabase.com/) (PostgreSQL with RLS)
- **Payments**: [Stripe](https://stripe.com/) (Checkout mode)
- **Authentication**: Supabase Auth
- **API Routes**: Next.js API Routes (server-only)

### Infrastructure
- **Hosting**: [Vercel](https://vercel.com/) (EU region)
- **CDN**: Vercel Edge Network
- **Monitoring**: Vercel Analytics + Custom dashboard
- **CI/CD**: GitHub Actions

### Third-party Services
- **Email**: [Brevo](https://www.brevo.com/)
- **ERP**: [Odoo](https://www.odoo.com/)
- **Analytics**: Google Analytics 4 + Hotjar
- **Chat**: [Intercom](https://www.intercom.com/)

## 🚀 Getting Started

### Prerequisites
- Node.js 20+ 
- npm/yarn/pnpm
- Git
- Supabase account
- Stripe account
- Vercel account (for deployment)

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/jdvot570/limitless-app.git
cd limitless-app
```

2. **Install dependencies**
```bash
npm install
```

3. **Set up environment variables**
```bash
cp .env.example .env.local
# Edit .env.local with your credentials
```

4. **Run database migrations**
```bash
npm run db:migrate
```

5. **Start development server**
```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) to view the application.

## 📁 Project Structure

```
limitless-app/
├── src/
│   ├── app/                 # Next.js app router pages
│   │   ├── [locale]/        # Internationalized routes
│   │   ├── api/            # API routes
│   │   └── globals.css     # Global styles
│   ├── components/         # React components
│   │   ├── ui/            # shadcn/ui components
│   │   └── features/      # Feature-specific components
│   ├── lib/               # Utility functions and configs
│   │   ├── supabase/      # Database client
│   │   ├── stripe/        # Payment utilities
│   │   └── utils.ts       # Helper functions
│   ├── hooks/             # Custom React hooks
│   ├── types/             # TypeScript type definitions
│   └── i18n/              # Internationalization files
├── public/                # Static assets
├── agents/                # AI agent configurations
├── .github/               # GitHub Actions workflows
├── CLAUDE.md             # AI assistant instructions
├── MVP0_PLAN.md          # Implementation roadmap
└── BRANCH_STRATEGY.md    # Git workflow documentation
```

## 🔐 Environment Variables

Create a `.env.local` file with the following variables:

```env
# Supabase
NEXT_PUBLIC_SUPABASE_URL=your_supabase_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key
SUPABASE_SERVICE_ROLE_KEY=your_service_role_key

# Stripe
NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY=your_stripe_publishable_key
STRIPE_SECRET_KEY=your_stripe_secret_key
STRIPE_WEBHOOK_SECRET=your_webhook_secret

# Odoo
ODOO_URL=your_odoo_url
ODOO_DB=your_odoo_db
ODOO_USERNAME=your_odoo_username
ODOO_API_KEY=your_odoo_api_key

# Brevo
BREVO_API_KEY=your_brevo_api_key

# Analytics
NEXT_PUBLIC_GTM_ID=your_gtm_id
NEXT_PUBLIC_GA_ID=your_ga_id
NEXT_PUBLIC_HOTJAR_ID=your_hotjar_id

# Intercom
NEXT_PUBLIC_INTERCOM_APP_ID=your_intercom_app_id
```

## 💻 Development

### Available Scripts

```bash
# Development
npm run dev          # Start development server
npm run build        # Build for production
npm run start        # Start production server

# Code Quality
npm run lint         # Run ESLint
npm run typecheck    # Run TypeScript checks
npm run format       # Format with Prettier

# Database
npm run db:migrate   # Run migrations
npm run db:seed      # Seed database
npm run db:reset     # Reset database

# Testing
npm run test         # Run tests
npm run test:watch   # Run tests in watch mode
npm run test:e2e     # Run E2E tests
```

### Git Workflow

We follow a simplified Git Flow:
- `main` - Production branch
- `develop` - Development branch
- `feature/*` - Feature branches

See [BRANCH_STRATEGY.md](./BRANCH_STRATEGY.md) for detailed guidelines.

### Code Style

- **TypeScript**: Strict mode enabled
- **ESLint**: Enforced code quality
- **Prettier**: Consistent formatting
- **Commits**: Conventional commits format

## 🚢 Deployment

### Vercel Deployment

1. **Connect GitHub repository to Vercel**
2. **Configure environment variables** in Vercel dashboard
3. **Set up deployment settings**:
   - Production: `main` branch
   - Preview: All pull requests
   - Region: EU (Frankfurt)

### Production Checklist

- [ ] All environment variables configured
- [ ] Database migrations applied
- [ ] Stripe webhooks configured
- [ ] Email templates created in Brevo
- [ ] Odoo integration tested
- [ ] Analytics tracking verified
- [ ] SSL certificates active
- [ ] Monitoring alerts configured

## 🧪 Testing

### Unit Tests
```bash
npm run test
```

### E2E Tests
```bash
npm run test:e2e
```

### Manual Testing Checklist
- [ ] Payment flow (all 3 plans)
- [ ] VAT calculation (EU countries)
- [ ] Coupon codes
- [ ] Authentication flow
- [ ] Email delivery
- [ ] Invoice generation
- [ ] Multi-language switching

## 📚 Documentation

- [API Documentation](./docs/api.md)
- [Database Schema](./docs/database.md)
- [Deployment Guide](./docs/deployment.md)
- [Security Guidelines](./docs/security.md)
- [Claude AI Instructions](./CLAUDE.md)
- [MVP0 Plan](./MVP0_PLAN.md)
- [Branch Strategy](./BRANCH_STRATEGY.md)

## 🤝 Contributing

### Development Process

1. Create feature branch from `develop`
2. Make changes following our code style
3. Write/update tests
4. Create pull request to `develop`
5. Code review by team member
6. Merge after approval

### PR Requirements

- [ ] Passes all CI checks
- [ ] Includes tests for new features
- [ ] Updates documentation if needed
- [ ] Follows conventional commits
- [ ] Reviewed by at least 1 team member

## 📄 License

This project is proprietary and confidential. All rights reserved.

## 🆘 Support

- **Technical Issues**: Create an issue on GitHub
- **Business Inquiries**: contact@limitless.app
- **Emergency**: Check [runbook](./docs/runbook.md)

## 🙏 Acknowledgments

Built with ❤️ using:
- [Next.js](https://nextjs.org/)
- [Supabase](https://supabase.com/)
- [Stripe](https://stripe.com/)
- [Vercel](https://vercel.com/)
- [shadcn/ui](https://ui.shadcn.com/)

---

<div align="center">
  <p>© 2025 Limitless. All rights reserved.</p>
  <p>Made with 🤖 assistance from Claude Code</p>
</div>