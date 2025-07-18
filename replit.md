# Funngro - Teen Freelancing Platform

## Overview

Funngro is a modern web application that connects talented teenagers with real companies for project-based work. Built as a full-stack TypeScript application, it features separate landing pages for teens and companies, with a focus on showcasing opportunities, testimonials, and facilitating contact between users and the platform.

## User Preferences

Preferred communication style: Simple, everyday language.
Color theme: Modern purple-cyan-yellow gradient design (updated from original Funngro colors)
Server requirement: Frontend-only application (no backend server needed)

## System Architecture

### Frontend Architecture
The frontend is built using **React 18** with **TypeScript** and follows a modern component-based architecture:

- **Framework**: React with Vite for fast development and building
- **Routing**: Wouter for lightweight client-side routing
- **State Management**: React Query (TanStack Query) for server state management
- **Styling**: Tailwind CSS with shadcn/ui component library
- **Form Handling**: React Hook Form with Zod validation
- **UI Components**: Radix UI primitives with custom styling

### Backend Architecture
The backend is an **Express.js** server with TypeScript:

- **Framework**: Express.js with middleware for JSON parsing and request logging
- **Database ORM**: Drizzle ORM configured for PostgreSQL
- **Session Storage**: PostgreSQL session store (connect-pg-simple)
- **Validation**: Zod schemas for API request validation
- **Development**: Vite integration for seamless development experience

### Database Design
Currently uses **PostgreSQL** with Drizzle ORM:

- **Schema Location**: `shared/schema.ts` for type-safe database definitions
- **Migration Management**: Drizzle Kit for schema migrations
- **Current Tables**: Users table with basic authentication fields
- **Temporary Storage**: In-memory storage implementation for development

## Key Components

### Shared Components
- **Navigation**: Responsive navigation with mobile menu support
- **Hero Sections**: Differentiated hero sections for teen and company pages
- **Contact Forms**: Type-safe contact forms with validation and submission handling
- **Testimonials**: Reusable testimonial components for both user types
- **FAQ Sections**: Expandable FAQ components with custom content
- **SEO Components**: Dynamic meta tag management for improved search visibility

### Page Structure
- **Teen Page** (`/` and `/teen`): Focused on earning opportunities, app downloads, and success stories
- **Company Page** (`/company`): Highlights available services, project ideas, and hiring benefits
- **404 Page**: Custom not-found page with helpful messaging

### UI System
- **Design System**: shadcn/ui components with custom Funngro branding
- **Color Scheme**: Purple (#B794F6), Orange (#FB8C00), Indigo, and Emerald brand colors
- **Typography**: Inter font family for modern, readable text
- **Responsive Design**: Mobile-first approach with breakpoint-based layouts

## Data Flow

### Client-Side Flow
1. **Route Resolution**: Wouter handles client-side routing
2. **Data Fetching**: React Query manages API calls and caching
3. **Form Submission**: React Hook Form + Zod validation → API endpoints
4. **State Updates**: React Query automatically updates UI after successful operations
5. **Error Handling**: Global error boundaries and toast notifications

### Server-Side Flow
1. **Request Processing**: Express middleware handles parsing and logging
2. **Validation**: Zod schemas validate incoming data
3. **Business Logic**: Route handlers process requests (currently contact form)
4. **Response**: JSON responses with appropriate status codes
5. **Error Handling**: Global error middleware with structured error responses

## External Dependencies

### Database & Infrastructure
- **Neon Database**: Serverless PostgreSQL (@neondatabase/serverless)
- **Session Management**: PostgreSQL session store for user sessions

### UI & Styling
- **Radix UI**: Accessible component primitives
- **Tailwind CSS**: Utility-first CSS framework
- **Lucide Icons**: Modern SVG icon library
- **Inter Font**: Google Fonts integration

### Development Tools
- **Vite**: Fast build tool and development server
- **TypeScript**: Type safety across the entire stack
- **ESBuild**: Fast JavaScript bundler for production builds

### Planned Integrations
- **Email Service**: For contact form submissions and notifications
- **File Upload**: For user profiles and project assets
- **Payment Processing**: For project payments and platform fees

## Deployment Strategy

### Development Environment
- **Local Development**: Vite dev server with HMR and Express backend
- **Database**: PostgreSQL connection via environment variables
- **Asset Serving**: Vite handles static assets in development

### Production Build
- **Frontend**: Vite builds optimized React bundle to `dist/public`
- **Backend**: ESBuild compiles TypeScript server to `dist/index.js`
- **Static Serving**: Express serves built frontend assets
- **Database**: PostgreSQL with connection pooling via Neon

### Environment Configuration
- **Database URL**: Required environment variable for PostgreSQL connection
- **Node Environment**: Production/development mode switching
- **Session Secret**: Secure session management (to be implemented)

### Key Architectural Decisions

1. **Monorepo Structure**: Single repository with client, server, and shared code for easier development and type sharing
2. **Drizzle ORM**: Chosen for type safety and modern SQL-first approach over traditional ORMs
3. **Shared Types**: TypeScript definitions in `/shared` folder ensure consistency between frontend and backend
4. **Component Library**: shadcn/ui provides high-quality, customizable components while maintaining design system consistency
5. **File-based Routing**: Simple wouter setup enables easy page management without complex routing configuration

The application is designed for scalability with clear separation of concerns, type safety throughout the stack, and modern development practices.