# replit.md

## Overview

This is a full-stack web application built with a modern tech stack featuring React frontend, Express.js backend, and PostgreSQL database. The application appears to be a business landing page for "FN Development Applied Solutions" - a consultancy focused on data solutions, automation, and applied AI. The site includes sections for services, examples, methodology, and a contact form.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

The application follows a monorepo structure with clear separation between client and server code:

- **Frontend**: React with TypeScript, using Vite as the build tool
- **Backend**: Express.js server with TypeScript
- **Database**: PostgreSQL with Drizzle ORM
- **UI Framework**: Tailwind CSS with shadcn/ui components
- **Styling**: Modern design system with CSS variables for theming

### Directory Structure
```
├── client/          # React frontend application
├── server/          # Express.js backend
├── shared/          # Shared types and schemas
├── migrations/      # Database migrations
└── dist/           # Built application output
```

## Key Components

### Frontend Architecture
- **React Router**: Uses wouter for client-side routing
- **State Management**: TanStack Query for server state management
- **UI Components**: shadcn/ui component library built on Radix UI primitives
- **Styling**: Tailwind CSS with custom design tokens
- **Forms**: React Hook Form with Zod validation
- **Responsive Design**: Mobile-first approach with Tailwind breakpoints

### Backend Architecture
- **Express.js**: REST API server with TypeScript
- **Database Layer**: Drizzle ORM with PostgreSQL
- **Validation**: Zod schemas for request/response validation
- **Storage**: Abstracted storage interface with in-memory implementation (likely for development)
- **Logging**: Custom request logging middleware

### Database Schema
- **Users Table**: Basic user management with username/password
- **Contact Submissions**: Stores contact form submissions with name, email, company, and message

## Data Flow

1. **Client Requests**: React components make API calls using TanStack Query
2. **API Layer**: Express routes handle requests and validate data using Zod schemas
3. **Storage Layer**: Abstracted storage interface allows for different implementations
4. **Database**: Drizzle ORM manages PostgreSQL interactions
5. **Response**: JSON responses sent back to client with proper error handling

### Contact Form Flow
- Form submission → Validation → Database storage → Success/error response
- Admin endpoint available to retrieve all contact submissions

## External Dependencies

### Frontend Dependencies
- **React Ecosystem**: React 18 with TypeScript support
- **UI Library**: Comprehensive shadcn/ui component set
- **Icons**: Lucide React icons
- **Date Handling**: date-fns library
- **Animations**: Built-in CSS animations via Tailwind

### Backend Dependencies
- **Database**: Neon serverless PostgreSQL
- **ORM**: Drizzle with full TypeScript support
- **Validation**: Zod for runtime type checking
- **Session Storage**: PostgreSQL-based sessions (connect-pg-simple)

### Development Tools
- **Build System**: Vite for frontend, esbuild for backend
- **Database Tools**: Drizzle Kit for migrations and schema management
- **Development**: tsx for TypeScript execution in development

## Deployment Strategy

### Build Process
- **Frontend**: Vite builds to `dist/public/` directory
- **Backend**: esbuild bundles server code to `dist/` directory
- **Database**: Drizzle migrations handle schema updates

### Environment Configuration
- **Development**: Uses tsx for hot reloading and Vite dev server
- **Production**: Serves static files from Express with built client assets
- **Database**: Configured via `DATABASE_URL` environment variable

### Production Considerations
- Static file serving integrated into Express server
- Database connection via Neon serverless PostgreSQL
- Environment-based configuration for development vs production
- Error handling middleware for production safety

The application is designed to be deployed as a single Node.js service that serves both the API and static frontend assets, making it suitable for platforms like Railway, Vercel, or traditional VPS hosting.