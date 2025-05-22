# Campus Bites Food Ordering System

## Overview
This project is a full-stack food ordering application called "Campus Bites" built with React on the frontend and Express.js on the backend. It allows users to browse menu items, filter by categories, add items to a cart, and place orders. The application uses Drizzle ORM for database operations and follows a modern component-based architecture with a clean separation between client and server code.

## User Preferences
Preferred communication style: Simple, everyday language.

## System Architecture

### Client-Side Architecture
- **UI Framework**: React with functional components and hooks
- **State Management**: React Context API for managing cart and order state
- **Routing**: Wouter for lightweight client-side routing
- **Styling**: Tailwind CSS with the shadcn/ui component library
- **Data Fetching**: TanStack Query (React Query) for API requests

### Server-Side Architecture
- **Framework**: Express.js running on Node.js
- **API Structure**: RESTful API design with `/api` prefix for all endpoints
- **Database Access**: Drizzle ORM to interact with PostgreSQL
- **Authentication**: Basic authentication system with username/password

### Data Flow
1. Client makes requests to the Express server's REST API endpoints
2. Server processes requests using route handlers
3. Server uses the storage layer to interact with the database
4. Database responses are processed and returned to the client
5. Client updates UI based on received data

## Key Components

### Frontend Components
1. **Core Layout Components**: 
   - Header: App navigation and cart icon
   - CategoryNav: Menu category filtering
   - FilterBar: Search and filtering options
   - MobileNav: Bottom navigation for mobile view

2. **Cart System**:
   - CartContext: Manages cart state across the application
   - CartSection: Desktop cart display
   - MobileCartModal: Mobile-optimized cart display
   - CartItem: Individual item in the cart

3. **Menu Components**:
   - MenuSection: Displays menu items grouped by category
   - MenuItem: Individual food item card

4. **Order System**:
   - OrderContext: Manages order state across the application
   - OrderPlacedModal: Confirmation dialog after placing an order
   - MyOrders: Order history page

### Backend Components
1. **API Routes**: Defined in server/routes.ts, handles API requests
2. **Storage Layer**: Abstract interface for data persistence
   - In-memory implementation for development
   - Drizzle ORM for PostgreSQL in production

3. **Database Schema**: 
   - Users table defined in shared/schema.ts
   - Extendable for additional entities (menu items, orders, etc.)

## Data Structure

### Database Schema
The application currently has a users table defined with:
- id (primary key)
- username (unique)
- password

The schema can be expanded to include:
- Menu items
- Categories
- Orders
- Order items

### Client-Side Data
1. **Cart State**:
   - List of items with quantity, price, and details
   - Subtotal, tax, and total calculations

2. **Order State**:
   - Order history
   - Order status (Preparing, Ready for Pickup, Completed)
   - Order details (items, quantities, total amounts)

3. **Menu Data**:
   - Currently mocked in client/src/data/menuItems.ts
   - Categories include breakfast, lunch, snacks, and beverages

## External Dependencies

### Frontend
- **UI Components**: Radix UI primitives with shadcn/ui component system
- **Styling**: Tailwind CSS for utility-first styling
- **Routing**: Wouter for lightweight routing
- **Data Fetching**: TanStack Query

### Backend
- **Database**: PostgreSQL via Drizzle ORM
- **Database Connectivity**: @neondatabase/serverless for Neon Postgres
- **Authentication**: Basic username/password, with potential for session-based auth

## Deployment Strategy
The application is configured for deployment on Replit with:

1. **Build Process**:
   - Frontend: Vite builds the React application
   - Backend: esbuild bundles the server code

2. **Production Setup**:
   - Static assets served by Express
   - API endpoints handled by Express routes
   - Connection to PostgreSQL database via Drizzle ORM

3. **Environment Variables**:
   - DATABASE_URL: Connection string for PostgreSQL database

## Development Workflow
1. **Local Development**:
   - `npm run dev` starts the development server
   - Both frontend and backend hot-reload during development

2. **Database Management**:
   - Schema defined in shared/schema.ts
   - `npm run db:push` to update the database schema

3. **Build & Deployment**:
   - `npm run build` builds both client and server
   - `npm run start` runs the production server

## Next Steps and Improvements
1. **Authentication System**:
   - Complete user registration and login functionality
   - Implement session management

2. **Menu Management**:
   - Move menu items from client-side mock to database
   - Add admin interface for menu management

3. **Order Processing**:
   - Implement server-side order storage and processing
   - Add real-time order status updates

4. **Payment Integration**:
   - Integrate payment processing system
   - Implement checkout flow