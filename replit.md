# AniFlix - Anime & Movie Streaming Platform

## Overview

AniFlix is a comprehensive anime and movie streaming platform built with Flask, featuring user authentication, subscription management, content administration, and video streaming capabilities. The platform supports both free and VIP memberships with different access levels and device limitations.

## System Architecture

### Backend Architecture
- **Framework**: Flask (Python web framework)
- **Database**: PostgreSQL with SQLAlchemy ORM
- **Authentication**: Flask-Login for session management
- **Payment Processing**: Stripe integration for subscriptions
- **File Storage**: External video hosting (MP4, YouTube embeds)
- **Deployment**: Gunicorn WSGI server with auto-scaling support

### Frontend Architecture
- **Styling**: Tailwind CSS for responsive design
- **Icons**: Font Awesome for UI elements
- **Fonts**: Google Fonts (Poppins)
- **Video Player**: Video.js for HTML5 video playback
- **Templates**: Jinja2 templating engine

## Key Components

### User Management System
- **Authentication**: Email/password-based login with password hashing
- **User Roles**: Regular users and admin users (identified by email patterns)
- **Session Management**: Flask-Login handles user sessions and login persistence
- **Device Tracking**: Limits concurrent device usage based on subscription tier

### Subscription System
- **Tiers**: Free (limited), VIP Monthly ($3), VIP 3-Month ($8), VIP Yearly ($28)
- **Payment**: Stripe checkout integration for secure payments
- **Access Control**: Episode-based restrictions (free users limited to first 5 episodes)
- **Device Limits**: Free users (1 device), VIP users (2 devices)

### Content Management
- **Content Types**: Anime series and movies
- **Episode Management**: Individual episode tracking with video URLs
- **Metadata**: Title, description, genre, year, rating, thumbnails
- **Media Support**: MP4 video files and YouTube embeds
- **Admin Interface**: Full CRUD operations for content and episodes

### Video Streaming
- **Player**: Video.js-based HTML5 video player
- **Quality**: HD video support with responsive design
- **Access Control**: Time-limited viewing for non-VIP users (10 minutes for episodes 6+)
- **Trailers**: Separate trailer viewing with autoplay capability

## Data Flow

### User Registration/Login Flow
1. User submits credentials via auth form
2. Server validates credentials and creates/authenticates user
3. Flask-Login creates session and redirects to dashboard
4. Subscription status determines content access levels

### Content Viewing Flow
1. User selects content from browse pages
2. System checks subscription status and episode restrictions
3. Video player loads with appropriate access controls
4. Watch history is tracked for progress management
5. VIP status determines full access vs. limited preview

### Admin Content Management Flow
1. Admin user accesses admin panel (email-based authorization)
2. Admin can create/edit content and episodes
3. Content is immediately available to users
4. Analytics track viewing patterns and user engagement

## External Dependencies

### Database
- **Primary**: Supabase PostgreSQL (cloud-hosted) - Currently configured
- **Fallback**: Replit PostgreSQL database
- **Connection**: SSL-required connections with connection pooling

### Payment Processing
- **Stripe**: Complete payment processing for subscriptions
- **Webhooks**: Handles successful payments and subscription updates
- **Security**: Secure API key management via environment variables

### Media Hosting
- **Video Files**: External hosting for MP4 content
- **YouTube**: Embedded YouTube videos for trailers and content
- **Images**: Thumbnail and poster image hosting

### Third-Party Services
- **Email Validation**: Server-side email format validation
- **QR Code Generation**: User account QR codes for mobile access
- **Image Processing**: Pillow for image manipulation

## Deployment Strategy

### Platform Configuration
- **Environment**: Replit with Nix package management
- **Runtime**: Python 3.11 with Node.js 20 support
- **Process Management**: Gunicorn with auto-reload for development

### Database Configuration
- **Connection Pooling**: SQLAlchemy engine with pre-ping and recycling
- **SSL**: Required SSL connections for production database
- **Timeout Handling**: 30-second connection timeout with retry logic

### Security Measures
- **Password Hashing**: Werkzeug password hashing for user credentials
- **Session Security**: Secure session keys with environment-based configuration
- **Admin Access**: Email-pattern-based admin authentication
- **SQL Injection Prevention**: SQLAlchemy ORM parameterized queries

### Scalability Features
- **Auto-scaling**: Replit auto-scale deployment target
- **Connection Pooling**: Database connection efficiency
- **Static Asset Optimization**: CDN-served CSS/JS libraries
- **Responsive Design**: Mobile-first responsive web design

## Changelog

- June 24, 2025: Successfully migrated from Replit Agent to Replit environment
- June 24, 2025: Configured Supabase PostgreSQL database connection
- June 24, 2025: Changed hero carousel from horizontal to vertical orientation
- June 24, 2025: Fixed touch/mouse gesture detection to be consistently vertical on all devices
- June 24, 2025: Changed navigation buttons back to left/right position with vertical slide animation
- June 24, 2025: Fixed carousel navigation buttons and multi-directional gesture support
- June 24, 2025: Unified background color for "Latest Releases" to match "Popular This Week"
- June 24, 2025: Removed auth.html template and redirected auth routes to homepage
- June 24, 2025: Fixed navigation overlap with hero content by adding proper padding and z-index
- June 24, 2025: Redesigned anime detail page with responsive UI/UX - improved button layout, mobile-first design, consistent spacing
- June 24, 2025: Initial setup

## User Preferences

- Database preference: Supabase PostgreSQL (configured)
- Preferred communication style: Simple, everyday language