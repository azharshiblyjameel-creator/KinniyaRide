# Overview

Kinniya Ride is a comprehensive Uber-style ride-hailing platform designed for Kinniya, Trincomalee, Sri Lanka. The system includes both a responsive web application and native mobile apps (Android/iOS) built with Flutter. The platform serves three user types: passengers for booking rides, drivers for managing ride requests, and administrators for system management. It supports two vehicle types (bikes and 3-wheelers) with both cash and card payment options, featuring real-time GPS tracking, driver ratings, and subscription-based driver monetization.

# User Preferences

Preferred communication style: Simple, everyday language.

# System Architecture

## Frontend Architecture

### Web Application
The client-side is built as a Single Page Application (SPA) using React with TypeScript, utilizing a component-based architecture with Radix UI components and Tailwind CSS for styling. The application implements role-based views through a unified interface that dynamically switches between passenger, driver, and admin modes based on user permissions. State management is handled through React Query for server state, Zustand for client state, and React Hook Form for form management. The routing system uses Wouter for lightweight client-side navigation with protected routes ensuring proper authentication.

### Mobile Applications
The native mobile apps are built with Flutter using Dart, providing separate Android and iOS applications that connect to the same backend API. The mobile architecture uses Provider pattern for state management, GoRouter for navigation, and Dio for HTTP communication. The apps feature role-based theming (green for passengers, blue for drivers, purple for admins) and support GPS-based location services, real-time ride tracking, and native mobile UX patterns. The mobile apps share the same database and authentication system as the web platform.

## Backend Architecture
The server follows an Express.js REST API architecture with TypeScript, implementing a modular structure separating authentication, routing, and data access layers. Authentication is managed through Passport.js with local strategy using session-based authentication with PostgreSQL session storage. The API provides comprehensive endpoints for user management, ride operations, driver management, and administrative functions. The server includes middleware for request logging, error handling, and CORS management.

## Database Design
The system uses PostgreSQL as the primary database with Drizzle ORM for type-safe database operations and schema management. The database schema includes users (passengers, drivers, admins), drivers (vehicle details, status, location), rides (booking details, status tracking), and fare settings (pricing configuration). The schema supports multi-role user types through enums and maintains referential integrity between related entities. Database migrations are handled through Drizzle Kit with support for schema evolution.

## Authentication & Authorization
User authentication is implemented using session-based authentication with encrypted passwords using Node.js crypto scrypt. The system supports role-based access control with three user types: passengers, drivers, and admins. Sessions are stored in PostgreSQL using connect-pg-simple for persistence across server restarts. Protected routes ensure proper access control on both frontend and backend, with middleware validating user authentication status.

## Real-time Features
The application architecture supports real-time features through the existing HTTP infrastructure, with provisions for WebSocket integration for live ride tracking, driver location updates, and instant notifications. The frontend uses React Query for efficient data fetching and caching, providing near real-time updates through polling mechanisms.

# External Dependencies

## Database Services
- **Neon Database**: PostgreSQL hosting service configured through DATABASE_URL environment variable
- **Drizzle ORM**: Type-safe database client with schema management and migrations
- **connect-pg-simple**: PostgreSQL session store for Express sessions

## UI Framework & Styling
- **Radix UI**: Comprehensive component library providing accessible, unstyled UI primitives
- **Tailwind CSS**: Utility-first CSS framework with custom design tokens and responsive design
- **Shadcn/ui**: Pre-built component system built on top of Radix UI with consistent styling

## Development & Build Tools
- **Vite**: Fast build tool and development server with hot module replacement
- **TypeScript**: Static type checking and enhanced developer experience
- **ESBuild**: Fast bundling for production builds
- **PostCSS & Autoprefixer**: CSS processing and vendor prefix management

## Authentication & Security
- **Passport.js**: Authentication middleware with local strategy implementation
- **Express Session**: Session management with PostgreSQL storage backend
- **Node.js Crypto**: Built-in cryptographic functions for password hashing and security

## Form Handling & Validation
- **React Hook Form**: Efficient form state management with minimal re-renders
- **Zod**: TypeScript-first schema validation for form inputs and API data
- **@hookform/resolvers**: Integration between React Hook Form and Zod validation

## State Management & API
- **TanStack React Query**: Server state management with caching, background updates, and error handling
- **Zustand**: Lightweight client-side state management for ride operations and UI state
- **Wouter**: Minimal client-side routing library for single-page application navigation

## Payment Integration
The architecture is prepared for payment gateway integration with support for cash and card payments, though specific payment providers are not yet implemented in the current codebase.

## Maps & Location Services
The system includes coordinate data for Kinniya, Sri Lanka (8.4833°N, 81.2167°E), with Google Maps API integration ready for real-time location tracking, route calculation, and fare estimation based on distance. The mobile apps include native GPS location services with proper permission handling for accurate pickup and drop-off location detection.

## Mobile Development
The Flutter-based mobile applications provide native Android and iOS experiences with the following key features:
- **Cross-platform**: Single codebase for both Android and iOS
- **Native Performance**: Optimized for mobile devices with low internet speeds
- **Offline Capabilities**: Local storage for essential data and graceful offline handling
- **Push Notifications**: Firebase integration for real-time ride updates
- **Location Services**: GPS-based location detection with background location for drivers
- **Role-based UI**: Separate interfaces and theming for passengers, drivers, and administrators
- **Multi-language**: Support for Tamil, Sinhala, and English languages