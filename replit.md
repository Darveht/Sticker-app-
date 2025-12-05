# Zambik - Creador de Stickers

## Overview

Zambik is a web-based sticker creation application built as a single-page application (SPA). The project is designed to provide users with an interactive interface for creating, customizing, and managing stickers with a cartoon network-inspired visual theme. The application uses a static site architecture with client-side rendering and Firebase for authentication services.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture

**Technology Stack**
- Pure HTML/CSS/JavaScript (no build tools or framework)
- Tailwind CSS via CDN for utility-first styling
- Lucide icons for UI elements
- Custom fonts: Bangers (comic-style) and Rubik (UI elements)

**Design System**
The application implements a cartoon network-inspired design language with:
- Custom color palette (cyan, magenta, yellow, black, white)
- Hard shadow effects for a bold, comic-book aesthetic
- Responsive design with mobile-first considerations (viewport meta tags prevent scaling)
- Custom font families for different UI contexts

**Rationale**: A static, CDN-based approach was chosen to minimize build complexity and deployment overhead. This makes the application extremely portable and easy to deploy on any static hosting platform without requiring Node.js build processes at runtime.

### Authentication Architecture

**Firebase Authentication**
- Uses Firebase Compat SDK (v10.7.1) for authentication
- Client-side authentication flow
- No custom backend authentication layer

**Rationale**: Firebase Authentication provides a managed authentication solution without requiring backend infrastructure. The compat SDK was chosen for broader browser compatibility and simpler migration paths.

### Deployment Architecture

**Static Site Hosting**
- Configured for Vercel deployment with SPA routing
- All routes rewrite to `/index.html` for client-side routing
- Local development via `serve` package

**SPA Routing Strategy**: The vercel.json configuration implements a catch-all rewrite rule, ensuring all URL paths are handled by the main index.html file. This enables client-side routing without server-side route handling.

**Pros**:
- Zero server-side infrastructure required
- Instant deployment and CDN distribution
- Simple development workflow

**Cons**:
- Limited SEO capabilities without SSR
- All routing logic must be client-side

### Build and Development

**Development Server**
- Uses `serve` package for local static file serving
- No build process or bundler required

**Rationale**: The serverless, build-free approach reduces complexity and allows developers to iterate quickly without compilation steps. Files are served directly as written.

## External Dependencies

### CDN-Based Dependencies

**Tailwind CSS** (via CDN)
- Purpose: Utility-first CSS framework for rapid UI development
- Integration: Configured with custom theme extending default Tailwind
- Custom configuration includes brand colors, fonts, and shadow utilities

**Lucide Icons** (via unpkg CDN)
- Purpose: Icon library for UI elements
- Integration: Loaded as script, icons likely used throughout the interface

**Google Fonts**
- Fonts: Bangers (display/comic) and Rubik (UI/interface)
- Purpose: Custom typography matching cartoon aesthetic

### Firebase Services

**Firebase Authentication** (v10.7.1 Compat SDK)
- Purpose: User authentication and session management
- Components: firebase-app-compat, firebase-auth-compat
- Integration: Client-side initialization and authentication flows
- Note: Firebase project configuration (API keys, project ID) must be configured in the application code

### Deployment Platform

**Vercel**
- Purpose: Static site hosting and deployment
- Configuration: Custom routing rules in vercel.json for SPA behavior
- Features utilized: Automatic deployments, CDN distribution

### Package Dependencies

**serve** (v14.2.5)
- Purpose: Local development static file server
- Usage: Enables local testing without deployment
- Note: Development-only dependency, not required for production