# SALT MUN Conference Website

## Overview

This is a Model United Nations (MUN) conference website for "SALT MUN" with the theme "Voice of Heritage". The application provides conference information, committee listings, delegate registration, and contact functionality. It's built as a full-stack TypeScript application with a React frontend and Express backend, using PostgreSQL for data persistence.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Routing**: Wouter (lightweight React router)
- **State Management**: TanStack React Query for server state
- **Styling**: Tailwind CSS with custom design system (deep royal blue primary, metallic gold accent)
- **UI Components**: shadcn/ui component library built on Radix UI primitives
- **Animations**: Framer Motion for page transitions and scroll animations
- **Forms**: React Hook Form with Zod validation via @hookform/resolvers
- **Typography**: Playfair Display (serif) and Plus Jakarta Sans (sans-serif) fonts

### Backend Architecture
- **Runtime**: Node.js with Express
- **Language**: TypeScript with ESM modules
- **API Pattern**: RESTful endpoints defined in shared routes file
- **Build Tool**: esbuild for server bundling, Vite for client

### Data Storage
- **Database**: PostgreSQL
- **ORM**: Drizzle ORM with drizzle-zod for schema validation
- **Schema Location**: `shared/schema.ts` contains all database tables
- **Migrations**: Drizzle Kit manages migrations in `./migrations` folder

### Key Design Patterns
- **Shared Code**: The `shared/` directory contains schema definitions and API route contracts used by both frontend and backend
- **Type Safety**: Zod schemas generated from Drizzle tables ensure consistent validation across the stack
- **Storage Abstraction**: `server/storage.ts` provides a clean interface for database operations through the `IStorage` interface

### Database Schema
Two main tables:
1. **registrations**: Stores delegate registration data (name, email, school, committee preference, message)
2. **committees**: Stores committee information (name, description, topic, imageUrl)

### API Endpoints
- `POST /api/registrations` - Submit delegate registration
- `GET /api/committees` - List all available committees

## External Dependencies

### Database
- PostgreSQL database (connection via `DATABASE_URL` environment variable)
- `connect-pg-simple` for session storage (if sessions are used)

### Third-Party Services
- Google Fonts API for typography (Playfair Display, Plus Jakarta Sans, DM Sans, Fira Code, Geist Mono)
- Unsplash for stock committee images

### Key NPM Packages
- **UI**: Full shadcn/ui component suite (@radix-ui/*)
- **Data Fetching**: @tanstack/react-query
- **Database**: drizzle-orm, pg, drizzle-zod
- **Validation**: zod, zod-validation-error
- **Build**: Vite, esbuild, tsx

### Replit-Specific Integrations
- `@replit/vite-plugin-runtime-error-modal` for development error display
- `@replit/vite-plugin-cartographer` and `@replit/vite-plugin-dev-banner` for development tooling