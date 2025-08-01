# VitalTracker Pro - Health Monitoring Platform

## Overview

VitalTracker Pro is a comprehensive health monitoring web application designed for patients, healthcare providers, and fitness enthusiasts. The platform enables users to track vital signs, manage medications, schedule appointments, and generate health reports with data visualization. Built as a full-stack TypeScript application, it features a React frontend with shadcn/ui components and an Express.js backend with PostgreSQL database integration.

## User Preferences

Preferred communication style: Simple, everyday language.

## Local Development Setup

For running the application outside of Replit:

### Prerequisites
- Node.js (v18 or higher)
- PostgreSQL database (local or cloud service like Neon)
- Visual Studio Code or preferred IDE

### Setup Steps
1. Install dependencies: `npm install`
2. Create `.env` file with database connection string
3. Run database setup: `npm run db:push`
4. Start development server: `npm run dev`

### Authentication Note
The current implementation uses Replit Auth (OIDC). For local development, consider:
- Setting up alternative auth providers (Auth0, Firebase)
- Or implementing email/password authentication
- Or running in development mode without auth for testing

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript, using Vite as the build tool
- **UI Library**: shadcn/ui components built on Radix UI primitives
- **Styling**: Tailwind CSS with custom medical/health theme colors and CSS variables
- **Routing**: Wouter for client-side routing with protected routes
- **State Management**: TanStack React Query for server state management
- **Form Handling**: React Hook Form with Zod validation
- **Charts**: Chart.js for data visualization of health metrics

### Backend Architecture
- **Framework**: Express.js with TypeScript
- **Database ORM**: Drizzle ORM with PostgreSQL dialect
- **Authentication**: Replit Auth with OpenID Connect (OIDC) integration
- **Session Management**: Express sessions with PostgreSQL store
- **API Design**: RESTful endpoints with comprehensive error handling
- **Validation**: Zod schemas shared between frontend and backend

### Database Design
- **Primary Database**: PostgreSQL with Neon serverless driver
- **Schema Management**: Drizzle migrations with schema definitions in shared directory
- **Key Tables**: 
  - Users (authentication and profile data)
  - Vital signs (heart rate, blood pressure, temperature, etc.)
  - Medications and dosage tracking
  - Appointments with healthcare providers
  - Health goals and emergency contacts
  - Sessions for authentication state

### Authentication & Authorization
- **Provider**: Replit Auth with OIDC flow
- **Session Storage**: PostgreSQL-backed sessions with configurable TTL
- **Route Protection**: Middleware-based authentication checks
- **User Management**: Automatic user creation/updates on authentication

### Data Architecture
- **Shared Types**: TypeScript interfaces and Zod schemas in shared directory
- **API Layer**: Centralized query client with automatic error handling
- **Caching Strategy**: React Query with optimistic updates and cache invalidation
- **Form Validation**: Client and server-side validation using shared Zod schemas

### UI/UX Design Patterns
- **Design System**: shadcn/ui components with medical theme customization
- **Responsive Design**: Mobile-first approach with Tailwind breakpoints
- **Loading States**: Skeleton components and loading indicators
- **Error Handling**: Toast notifications and error boundaries
- **Accessibility**: Radix UI primitives ensure WCAG compliance

## External Dependencies

### Database Services
- **Neon PostgreSQL**: Serverless PostgreSQL database hosting
- **Connection Pooling**: Neon serverless driver with WebSocket support

### Authentication Services
- **Replit Auth**: OIDC-based authentication provider
- **Session Management**: connect-pg-simple for PostgreSQL session storage

### Frontend Libraries
- **UI Components**: Radix UI primitives (@radix-ui/*) for accessible components
- **Styling**: Tailwind CSS with PostCSS processing
- **Data Visualization**: Chart.js for health metrics charts
- **Form Management**: React Hook Form with Hookform resolvers
- **HTTP Client**: Native fetch API with TanStack React Query

### Backend Libraries
- **Database**: Drizzle ORM with Neon serverless adapter
- **Authentication**: Passport.js with OpenID Connect strategy
- **Security**: Express session middleware with secure cookie configuration
- **Validation**: Zod for runtime type checking and validation

### Development Tools
- **Build Tool**: Vite with React plugin and TypeScript support
- **Code Quality**: TypeScript strict mode with comprehensive type checking
- **Development Server**: Vite dev server with HMR and error overlay
- **Deployment**: ESBuild for production bundling with Node.js target