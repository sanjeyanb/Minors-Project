# Student Attendance Management System

## Overview

A full-stack web application for educational institutions to manage student attendance efficiently. The system enables teachers to mark attendance, track student presence patterns, generate reports, and automatically notify parents when attendance falls below configured thresholds. Built with a modern React frontend using shadcn/ui components and a Node.js/Express backend with PostgreSQL database.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture

**Framework & Build System:**
- React 18 with TypeScript for type-safe component development
- Vite as the build tool and development server
- Wouter for client-side routing (lightweight alternative to React Router)

**UI Component Strategy:**
- shadcn/ui component library (Radix UI primitives with Tailwind CSS)
- "New York" style variant with custom Material Design-inspired theme
- Design system follows educational productivity tool patterns with emphasis on data density and quick interactions

**State Management:**
- TanStack Query (React Query) for server state management
- Local component state with React hooks
- No global state management library - queries handle data synchronization

**Styling Approach:**
- Tailwind CSS with custom design tokens
- CSS variables for theming (light/dark mode support)
- Inter font family for consistent typography
- Standardized spacing scale (2, 4, 6, 8, 12, 16 units)

### Backend Architecture

**Server Framework:**
- Express.js with TypeScript
- ESM module system throughout
- Custom logging middleware for API request tracking

**API Design:**
- RESTful endpoints organized by resource (classes, students, attendance, alerts, settings)
- JSON request/response format
- Centralized error handling with Zod schema validation

**Storage Layer:**
- Abstracted storage interface (IStorage) allowing multiple implementations
- In-memory storage implementation for development (MemStorage class)
- Drizzle ORM configured for PostgreSQL production use
- Schema-first approach with TypeScript types generated from database schema

**Database Schema:**
- `classes` - Academic classes with grade, section, and academic year
- `students` - Student records linked to classes with parent contact information
- `attendance_records` - Daily attendance entries with status (present/absent/late)
- `alert_settings` - Configurable thresholds for low attendance notifications
- `alert_history` - Audit log of sent notifications

### Email Service Integration

**Notification System:**
- Nodemailer for SMTP email delivery
- Template-based HTML emails with inline styling
- Triggered automatically when student attendance drops below threshold
- Configurable check period (default: 30 days) and threshold percentage (default: 75%)

**Configuration:**
- Environment variables for SMTP credentials (host, port, user, password)
- Sender email address configuration
- Alert settings persisted in database with admin UI controls

### Authentication & Session Management

**Current State:**
- No authentication system implemented
- Session management infrastructure present (connect-pg-simple for PostgreSQL-backed sessions)
- Ready for future implementation of teacher/admin authentication

### Form Handling & Validation

**Strategy:**
- React Hook Form for form state management and validation
- Zod schemas shared between client and server for consistent validation
- shadcn/ui Form components with integrated error display
- Schema generation using drizzle-zod for database-model alignment

### Development Tools

**Developer Experience:**
- Replit integration plugins (cartographer, dev banner, runtime error overlay)
- Hot module replacement via Vite
- TypeScript strict mode with path aliases (@/, @shared/, @assets/)
- Drizzle Kit for database migrations

### Deployment Considerations

**Build Process:**
- Vite bundles frontend to dist/public
- esbuild bundles backend to dist/index.js with external packages
- Single production command starts Express server serving static frontend

**Environment Requirements:**
- DATABASE_URL for PostgreSQL connection (Neon serverless driver)
- SMTP configuration for email alerts
- NODE_ENV flag for development/production behavior

## External Dependencies

### Database
- **PostgreSQL** via Neon serverless driver (@neondatabase/serverless)
- **Drizzle ORM** for type-safe database queries and migrations
- Connection pooling and serverless-optimized queries

### Email Service
- **SMTP Server** (configured via environment variables)
- **Nodemailer** for email composition and delivery
- HTML email templates with responsive design

### UI Component Libraries
- **Radix UI** primitives for accessible, unstyled components
- **shadcn/ui** as the component system built on Radix
- **Lucide React** for consistent iconography
- **Tailwind CSS** for utility-first styling

### Data Management
- **TanStack Query** for async state, caching, and server synchronization
- **date-fns** for date manipulation and formatting
- **Zod** for runtime schema validation

### Development Dependencies
- **Vite** with React plugin for fast development
- **TypeScript** compiler with strict type checking
- **Replit plugins** for enhanced development experience in Replit environment