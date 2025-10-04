# Pa' que Pinto #2 - Vehicle Dealership Platform

## Overview

A premium automotive e-commerce platform for browsing and exploring a curated catalog of 86+ vehicles. The application provides an immersive, Tesla/Carvana-inspired browsing experience with VIP discount tiers, advanced filtering, and Spanish-language interface. Built as a full-stack TypeScript application with React frontend and Express backend.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture

**Framework & Build System**
- React 18+ with TypeScript for type-safe component development
- Vite as the build tool and development server for fast HMR and optimized production builds
- Wouter for lightweight client-side routing
- Single-page application (SPA) architecture

**UI Component Strategy**
- shadcn/ui component library (New York style variant) built on Radix UI primitives
- Tailwind CSS for utility-first styling with custom design system
- CSS variables for theming with dark mode as default
- Custom color palette inspired by premium automotive brands (Tesla, Mercedes-Benz)

**Design System**
- Typography: Inter (primary) and Rajdhani (technical specs) from Google Fonts
- Dark mode primary with electric blue accent color (210 100% 55%)
- Price range color coding: Gold (Alto), Blue (Medio), Green (Bajo)
- Responsive design with mobile-first approach

**State Management**
- React hooks (useState, useMemo, useRef) for local component state
- TanStack Query (React Query) for server state management and caching
- No global state management library - deliberately kept simple with component-level state

**Key Features**
- VIP discount system with three tiers (Platino, Oro, Diamante) applying dynamic discounts based on price range
- Multi-criteria filtering (search, category, price range) with real-time results
- Smooth scroll navigation and category-based browsing
- Vehicle cards with specifications (speed, fuel capacity, trunk space)

### Backend Architecture

**Server Framework**
- Express.js for HTTP server and API routing
- Node.js runtime with ES modules (type: "module")
- Development and production modes with environment-based configuration

**Data Storage**
- In-memory storage implementation (MemStorage class) as current data layer
- Designed with IStorage interface for future database integration
- Static vehicle data imported from shared schema

**API Design**
- RESTful API structure with `/api` prefix for all application routes
- Request/response logging middleware for debugging
- JSON-based communication
- Error handling middleware for consistent error responses

**Development Tools**
- TSX for running TypeScript directly in development
- esbuild for production server bundling
- Hot module replacement via Vite middleware in development

### Data Schema & Models

**Core Entities**
- Users: Basic authentication schema with username/password (prepared for future auth implementation)
- Vehicles: Comprehensive model with category, price range, specifications (speed, tank capacity, trunk capacity)

**Type System**
- Shared TypeScript types between client and server via `@shared` alias
- Zod schemas with drizzle-zod integration for runtime validation
- Type inference for Insert and Select operations

**Vehicle Categories**
- AUTOS (54 vehicles) - Sports cars and luxury sedans
- CAMIONETAS (17 vehicles) - SUVs and pickup trucks
- MOTOS (9 vehicles) - High-end motorcycles
- OTROS (6 vehicles) - Specialized vehicles

**Price Ranges**
- Alto (High tier) - Premium vehicles with 12-20% VIP discounts
- Medio (Mid tier) - Mid-range vehicles with 13-17.5% VIP discounts
- Bajo (Low tier) - Entry-level vehicles with 10-15% VIP discounts

### External Dependencies

**Database**
- Drizzle ORM configured for PostgreSQL via @neondatabase/serverless
- Connection pooling through Neon serverless driver
- Schema migrations managed by drizzle-kit
- Database currently not active - using in-memory storage as placeholder

**UI Component Library**
- Radix UI primitives (20+ components) for accessible, unstyled components
- Full suite: dialogs, dropdowns, popovers, tooltips, accordions, tabs, etc.
- Custom styling applied via Tailwind and CVA (class-variance-authority)

**Form Management**
- React Hook Form with @hookform/resolvers for validation
- Zod schema integration for type-safe form validation

**Utility Libraries**
- clsx + tailwind-merge (via cn utility) for conditional className handling
- date-fns for date manipulation
- nanoid for generating unique IDs
- cmdk for command palette functionality

**Development Dependencies**
- Replit-specific plugins for runtime error overlay, cartographer, and dev banner
- TypeScript with strict mode enabled
- PostCSS with Tailwind and Autoprefixer

**Assets Management**
- Stock images stored in `attached_assets/stock_images/` directory
- Vite alias `@assets` for asset imports
- Images for categories and hero section (luxury cars, trucks, motorcycles)

**Session Management**
- connect-pg-simple configured for PostgreSQL session storage (prepared for future use)
- Express session middleware ready for authentication implementation