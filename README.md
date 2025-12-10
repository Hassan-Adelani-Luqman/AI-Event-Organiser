# 🎉 Spott - AI Event Organiser

> Delightful Events Start Here

A modern, full-stack event management platform built with Next.js 16, featuring AI-powered event creation, real-time updates, and seamless user experience.

![Next.js](https://img.shields.io/badge/Next.js-16.0-black?style=flat-square&logo=next.js)
![React](https://img.shields.io/badge/React-19.2-blue?style=flat-square&logo=react)
![Convex](https://img.shields.io/badge/Convex-Backend-orange?style=flat-square)
![Clerk](https://img.shields.io/badge/Clerk-Auth-purple?style=flat-square)

## ✨ Features

### For Attendees
- 🔍 **Smart Event Discovery** - Browse and search events with advanced filters
- 📍 **Location-Based Search** - Find events near you
- 🎫 **Easy Registration** - One-click event registration with QR codes
- 📱 **Digital Tickets** - Receive and manage tickets in your account
- 🎯 **Personalized Recommendations** - Get event suggestions based on interests
- 🌓 **Dark/Light Mode** - Comfortable viewing in any lighting

### For Organizers
- 🤖 **AI Event Generator** - Create events using natural language prompts
- 🖼️ **Unsplash Integration** - Professional cover images from millions of photos
- 📊 **Event Dashboard** - Manage all your events in one place
- 📈 **Attendee Management** - Track registrations and check-ins
- 📱 **QR Code Scanner** - Quick check-in with mobile scanner
- 🎟️ **Ticket Management** - Control capacity and ticket types

### Technical Highlights
- ⚡ **Real-time Updates** - Powered by Convex for instant data sync
- 🔐 **Secure Authentication** - Clerk-based auth with JWT tokens
- 🎨 **Modern UI** - Built with Tailwind CSS and shadcn/ui components
- 📱 **Fully Responsive** - Works seamlessly on all devices
- 🚀 **Server Components** - Optimized with Next.js 16 App Router
- 🌐 **SEO Friendly** - Dynamic metadata and slugs

---

## 🚀 Quick Start

### Prerequisites

- Node.js 18+ and npm
- Git
- Accounts on:
  - [Convex](https://convex.dev) (Backend)
  - [Clerk](https://clerk.com) (Authentication)
  - [Google AI Studio](https://aistudio.google.com) (Gemini API)
  - [Unsplash](https://unsplash.com/developers) (Image API)

### Installation

1. **Clone the repository**
   ```bash
   git clone <your-repo-url>
   cd ai-event-organiser
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Set up environment variables**
   
   Create a `.env` file in the root directory:
   ```env
   # Convex Backend
   CONVEX_DEPLOYMENT=
   NEXT_PUBLIC_CONVEX_URL=
   
   # Clerk Authentication
   NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=
   CLERK_SECRET_KEY=
   NEXT_PUBLIC_CLERK_SIGN_IN_URL=/sign-in
   NEXT_PUBLIC_CLERK_SIGN_UP_URL=/sign-up
   CLERK_JWT_ISSUER_DOMAIN=
   
   # Unsplash Images
   NEXT_PUBLIC_UNSPLASH_ACCESS_KEY=
   
   # Google Gemini AI
   GEMINI_API_KEY=
   ```

4. **Initialize Convex**
   ```bash
   npx convex dev
   ```
   This will:
   - Create a new Convex project (if needed)
   - Generate your `CONVEX_DEPLOYMENT` and `NEXT_PUBLIC_CONVEX_URL`
   - Sync your database schema
   - Start the Convex development server

5. **Run the development server**
   ```bash
   npm run dev
   ```

6. **Open your browser**
   
   Navigate to [http://localhost:3000](http://localhost:3000)

---

## 🔑 API Keys Setup

### 1. Convex (Backend Database)

1. Go to [convex.dev](https://convex.dev)
2. Create a new project
3. Run `npx convex dev` - it will automatically:
   - Set up your deployment
   - Provide the deployment URL
   - Update your `.env` with `CONVEX_DEPLOYMENT` and `NEXT_PUBLIC_CONVEX_URL`

### 2. Clerk (Authentication)

1. Go to [clerk.com](https://clerk.com)
2. Create a new application
3. Choose authentication methods (Email, Google, etc.)
4. Copy API keys from the dashboard:
   - **Publishable Key** → `NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY`
   - **Secret Key** → `CLERK_SECRET_KEY`
5. Go to **JWT Templates** → Create "convex" template
6. Copy the Issuer URL → `CLERK_JWT_ISSUER_DOMAIN`
7. **Connect Clerk to Convex:**
   - In Convex dashboard: Settings → Authentication → Add Clerk
   - Paste your `CLERK_JWT_ISSUER_DOMAIN`

### 3. Google Gemini API (AI Generation)

1. Go to [aistudio.google.com/app/apikey](https://aistudio.google.com/app/apikey)
2. Sign in with Google account
3. Create API key in a project
4. Copy API key → `GEMINI_API_KEY`

### 4. Unsplash (Image Search)

1. Go to [unsplash.com/developers](https://unsplash.com/developers)
2. Register as a developer
3. Create a new application
4. Copy Access Key → `NEXT_PUBLIC_UNSPLASH_ACCESS_KEY`

---

## 📁 Project Structure

```
ai-event-organiser/
├── app/                          # Next.js 16 App Router
│   ├── (auth)/                   # Authentication routes
│   │   ├── sign-in/
│   │   └── sign-up/
│   ├── (main)/                   # Protected routes
│   │   ├── create-event/         # AI event creator
│   │   ├── my-events/            # Event management
│   │   └── my-tickets/           # User tickets
│   ├── (public)/                 # Public routes
│   │   ├── events/[slug]/        # Event details
│   │   └── explore/              # Event discovery
│   ├── api/                      # API routes
│   │   └── generate-event/       # Gemini AI endpoint
│   ├── layout.js                 # Root layout
│   └── page.js                   # Landing page
├── components/                   # React components
│   ├── ui/                       # shadcn/ui components
│   ├── event-card.jsx
│   ├── header.jsx
│   ├── footer.jsx
│   └── ...
├── convex/                       # Convex backend
│   ├── schema.js                 # Database schema
│   ├── events.js                 # Event queries/mutations
│   ├── users.js                  # User management
│   ├── registrations.js          # Registration logic
│   ├── auth.config.js            # Auth configuration
│   └── ...
├── hooks/                        # Custom React hooks
├── lib/                          # Utility functions
├── public/                       # Static assets
└── .env                          # Environment variables
```

---

## 🎯 Key Features Explained

### AI Event Generation
Uses Google's Gemini 2.0 Flash model to generate:
- Event titles
- Detailed descriptions
- Category suggestions
- Capacity recommendations
- Ticket type suggestions

### Real-time Database
Convex provides:
- Instant data synchronization
- Optimistic updates
- Automatic caching
- Type-safe queries

### Authentication Flow
Clerk handles:
- Sign-up/Sign-in
- Session management
- JWT token generation
- User profiles
- Protected routes

### Image Selection
Unsplash API offers:
- 12 images per search
- High-quality professional photos
- Search by keywords
- Free usage (with attribution)

---

## 🛠️ Tech Stack

| Technology | Purpose | Version |
|------------|---------|---------|
| **Next.js** | React framework | 16.0.1 |
| **React** | UI library | 19.2.0 |
| **Convex** | Backend & database | 1.28.2 |
| **Clerk** | Authentication | 6.34.1 |
| **Tailwind CSS** | Styling | 4.x |
| **shadcn/ui** | UI components | Latest |
| **Gemini AI** | AI generation | 0.24.1 |
| **Unsplash** | Image API | Latest |
| **Lucide React** | Icons | 0.552.0 |
| **React Hook Form** | Forms | 7.66.0 |
| **Zod** | Validation | 4.1.12 |
| **html5-qrcode** | QR scanner | 2.3.8 |

---

## 🚢 Deployment

### Deploy to Vercel (Recommended)

1. **Push to GitHub:**
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git push origin main
   ```

2. **Deploy Convex to production:**
   ```bash
   npx convex deploy
   ```
   Copy the production URL and deployment name.

3. **Deploy to Vercel:**
   - Go to [vercel.com](https://vercel.com)
   - Import your GitHub repository
   - Add all environment variables
   - Deploy!

4. **Update Clerk:**
   - Add Vercel URL to allowed origins
   - Update redirect URLs if needed

### Environment Variables for Production

Make sure to add all variables from `.env` to your Vercel project settings.

---

## 📝 Available Scripts

```bash
npm run dev          # Start development server
npm run build        # Build for production
npm start            # Start production server
npm run lint         # Run ESLint
npx convex dev       # Start Convex development
npx convex deploy    # Deploy Convex to production
```

---

## 🎨 Customization

### Theme
- Edit `app/globals.css` for global styles
- Modify `components/theme-provider.jsx` for theme settings
- Update Tailwind config in `postcss.config.mjs`

### Branding
- Update `app/layout.js` metadata
- Replace logo in `components/header.jsx`
- Modify colors in Tailwind classes

### Features
- Add new event categories in `convex/schema.js`
- Customize AI prompts in `app/api/generate-event/route.js`
- Extend user onboarding in `components/onboarding-modal.jsx`

---

## 🐛 Troubleshooting

### Hydration Errors
If you see hydration mismatches, ensure `suppressHydrationWarning` is on `<html>` and `<body>` tags.

### Clerk Authentication Issues
- Verify JWT Issuer Domain matches Clerk dashboard
- Check Convex has Clerk configured correctly
- Ensure redirect URLs are set properly

### Convex Connection Issues
- Run `npx convex dev` to sync schema
- Check `NEXT_PUBLIC_CONVEX_URL` is correct
- Verify deployment is running

### AI Generation Failures
- Confirm `GEMINI_API_KEY` is valid
- Check API quota limits
- Review error logs in browser console

### Unsplash Images Not Loading
- Verify `NEXT_PUBLIC_UNSPLASH_ACCESS_KEY`
- Check rate limits (50 requests/hour for demo)
- Apply for production access if needed

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!

1. Fork the project
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📧 Contact

For questions or support, please open an issue in the repository.

---

## 🙏 Acknowledgments

- [Next.js](https://nextjs.org/) - The React Framework
- [Convex](https://convex.dev/) - Backend platform
- [Clerk](https://clerk.com/) - Authentication
- [shadcn/ui](https://ui.shadcn.com/) - UI components
- [Unsplash](https://unsplash.com/) - Beautiful free images
- [Google AI](https://ai.google.dev/) - Gemini AI model

---

Made with ❤️ using Next.js and AI