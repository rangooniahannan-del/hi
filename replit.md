# Multi-Agent Web Development Platform

## Overview

This is a full-stack web application for building projects with AI-powered multi-agent collaboration. Users can create conversations with AI agents, describe their project requirements, and receive assistance in building full-stack web applications. The platform features a modern dark-themed UI inspired by developer tools like Linear, Vercel, and GitHub.

The application is built with React on the frontend, Express on the backend, and uses PostgreSQL (via Neon serverless) for data persistence. It follows a monorepo structure with shared TypeScript schemas and implements a conversation-based interface where users interact with AI agents to build and refine their projects.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture

**Framework & Build Tool:**
- React 18+ with TypeScript for type safety
- Vite as the build tool and dev server with HMR support
- Wouter for lightweight client-side routing

**UI Component System:**
- shadcn/ui component library (New York style variant) built on Radix UI primitives
- Tailwind CSS for styling with custom design tokens for dark theme
- Design system based on a dark color palette (#0F0F0F to #1A1A1A backgrounds) with warm gold/amber (#F59E0B to #FBBF24) accents
- Inter font family from Google Fonts for typography

**State Management:**
- TanStack React Query for server state management, data fetching, and caching
- Local React state for UI-specific state (modals, forms)
- Custom query client configured with infinite stale time and disabled automatic refetching

**Key Frontend Patterns:**
- Component-based architecture with reusable UI components in `/client/src/components/ui/`
- Feature components in `/client/src/components/` (AppSidebar, AuthModal, MessageBubble, etc.)
- Page-level components in `/client/src/pages/` (Dashboard, ConversationPage)
- Path aliases configured (`@/` for client src, `@shared/` for shared schemas)

### Backend Architecture

**Server Framework:**
- Express.js with TypeScript running on Node.js
- Custom middleware for request logging with JSON response capture
- RESTful API design pattern with routes organized in `/server/routes.ts`

**Data Layer:**
- Drizzle ORM for type-safe database queries and schema management
- Neon serverless PostgreSQL for cloud-native database hosting
- WebSocket support for database connections
- In-memory storage implementation (MemStorage) as fallback/development option

**Database Schema:**
- `users` table: id (UUID), username (unique), password
- `conversations` table: id (UUID), title, userId, createdAt timestamp
- `messages` table: id (UUID), conversationId, role (system/user/assistant), content, createdAt timestamp
- Zod schemas derived from Drizzle tables for runtime validation

**API Endpoints:**
- `POST /api/conversations` - Create new conversation
- `GET /api/conversations` - List conversations by userId
- `GET /api/conversations/:id` - Get single conversation
- `POST /api/messages` - Create new message
- `GET /api/messages/:conversationId` - Get messages for conversation

**Development Setup:**
- Vite middleware integration in development mode for SSR capabilities
- Custom error overlay plugin for runtime errors
- Cartographer and dev banner plugins in Replit environment

### Data Storage Solutions

**Primary Database:**
- PostgreSQL via Neon serverless (`@neondatabase/serverless`)
- Connection pooling with pg Pool
- Environment variable `DATABASE_URL` required for connection
- Drizzle Kit for schema migrations (output to `/migrations/`)

**Schema Management:**
- TypeScript schema definitions in `/shared/schema.ts`
- Type inference for Insert and Select operations
- Validation schemas using drizzle-zod integration

**Storage Interface Pattern:**
- IStorage interface defines contract for data operations
- Supports multiple implementations (database vs in-memory)
- CRUD methods for users, conversations, and messages

### Authentication and Authorization

**Current Implementation:**
- Username/password schema defined in database
- AuthModal component with login/signup modes
- OAuth provider UI placeholders (GitHub, GitLab, Bitbucket)
- Session state managed in frontend (`isAuthenticated` boolean)
- No active authentication middleware currently implemented (ready for implementation)

**Planned/Placeholder Features:**
- OAuth integration with Git providers
- Session management (connect-pg-simple package included for PostgreSQL session store)
- Protected routes and API endpoint authorization

### External Dependencies

**UI Libraries:**
- Radix UI primitives for accessible component foundation (accordion, alert-dialog, avatar, checkbox, collapsible, context-menu, dialog, dropdown-menu, hover-card, label, menubar, navigation-menu, popover, progress, radio-group, scroll-area, select, separator, slider, switch, tabs, toast, toggle, tooltip)
- React Hook Form with Zod resolver for form validation
- date-fns for date formatting and manipulation
- lucide-react for icon components
- react-icons for additional icon sets (GitLab, Bitbucket logos)
- cmdk for command palette functionality
- class-variance-authority for variant-based component styling
- clsx and tailwind-merge for className utilities

**Development Tools:**
- TypeScript for static typing across the stack
- ESBuild for production server bundling
- Drizzle Kit for database schema management
- Replit-specific plugins (cartographer, dev banner, runtime error modal)

**Database & ORM:**
- @neondatabase/serverless for PostgreSQL connection
- drizzle-orm for type-safe queries
- drizzle-zod for schema-to-Zod conversion
- ws for WebSocket support in database connections

**Build & Bundling:**
- Vite with React plugin
- PostCSS with Tailwind CSS and Autoprefixer
- Path resolution configured for cleaner imports

**Key Third-Party Services:**
- Neon (serverless PostgreSQL hosting)
- Google Fonts (Inter font family)
- Planned: Git provider OAuth (GitHub, GitLab, Bitbucket)