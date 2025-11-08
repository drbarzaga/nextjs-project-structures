# Next.js Project Structures by Scale

> A comprehensive guide to organizing Next.js projects from small MVPs to enterprise-scale applications.

<div align="center">

![GitHub stars](https://img.shields.io/github/stars/dayan/nextjs-project-structures?style=for-the-badge&logo=github&color=yellow)
![GitHub forks](https://img.shields.io/github/forks/dayan/nextjs-project-structures?style=for-the-badge&logo=github&color=blue)
![GitHub issues](https://img.shields.io/github/issues/dayan/nextjs-project-structures?style=for-the-badge&logo=github&color=red)

[![Next.js](https://img.shields.io/badge/Next.js-13+-black?style=for-the-badge&logo=next.js)](https://nextjs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.0+-blue?style=for-the-badge&logo=typescript)](https://www.typescriptlang.org/)
[![React](https://img.shields.io/badge/React-18+-61dafb?style=for-the-badge&logo=react)](https://reactjs.org/)

</div>

---

This document presents different project structures for Next.js applications, organized from small to large-scale projects. Each structure includes detailed explanations, use cases, and best practices to help you choose the right organization for your project.

---

## 🟢 Small Project Structure (< 10 features)

Ideal for MVPs, prototypes, or simple applications with limited functionality.

### 📋 Use Cases

**Perfect for:**

- **MVP Development**: Quick prototypes to validate business ideas
- **Personal Projects**: Portfolio sites, personal blogs, or hobby projects
- **Landing Pages**: Simple marketing pages with minimal functionality
- **Proof of Concept**: Technical demonstrations or feasibility studies
- **Startup MVPs**: Early-stage products with 1-2 core features
- **Hackathons**: Time-constrained projects requiring rapid development
- **Learning Projects**: Educational projects to understand Next.js fundamentals

**Example Projects:**

- Personal portfolio website
- Simple blog with authentication
- Todo app with user accounts
- Basic e-commerce landing page
- Company website with contact form
- Event registration system

<pre>
<code style="color: #e1e4e8;">src/
├── <span style="color: #79b8ff;">app</span>/                          # Next.js App Router directory (routing & pages)
│   ├── <span style="color: #85e89d;">(app)</span>/                    # Route group for authenticated app pages
│   │   ├── <span style="color: #85e89d;">dashboard</span>/            # Dashboard page route
│   │   │   └── <span style="color: #9ecbff;">page.tsx</span>          # Dashboard page component
│   │   ├── <span style="color: #85e89d;">settings</span>/             # Settings page route
│   │   │   └── <span style="color: #9ecbff;">page.tsx</span>          # Settings page component
│   │   └── <span style="color: #9ecbff;">layout.tsx</span>            # Layout wrapper for authenticated routes
│   ├── <span style="color: #85e89d;">(auth)</span>/                   # Route group for authentication pages
│   │   ├── <span style="color: #85e89d;">login</span>/                # Login page route
│   │   │   └── <span style="color: #9ecbff;">page.tsx</span>          # Login page component
│   │   ├── <span style="color: #85e89d;">sign-up</span>/              # Sign up page route
│   │   │   └── <span style="color: #9ecbff;">page.tsx</span>          # Sign up page component
│   │   └── <span style="color: #9ecbff;">layout.tsx</span>            # Layout wrapper for auth routes
│   ├── <span style="color: #ffab70;">api</span>/                      # API routes directory
│   │   └── <span style="color: #85e89d;">auth</span>/                 # Authentication API endpoints
│   │       └── <span style="color: #85e89d;">[...all]</span>/         # Catch-all route for auth handlers
│   │           └── <span style="color: #79b8ff;">route.ts</span>       # Auth API route handler
│   ├── <span style="color: #9ecbff;">layout.tsx</span>                # Root layout component
│   └── <span style="color: #b392f0;">globals.css</span>               # Global CSS styles
│
├── <span style="color: #79b8ff;">components</span>/                   # React components directory
│   ├── <span style="color: #85e89d;">features</span>/                 # Feature-specific components
│   │   ├── <span style="color: #85e89d;">auth</span>/                 # Authentication-related components
│   │   │   ├── <span style="color: #9ecbff;">login-form.tsx</span>    # Login form component
│   │   │   └── <span style="color: #9ecbff;">signup-form.tsx</span>   # Sign up form component
│   │   └── <span style="color: #85e89d;">dashboard</span>/            # Dashboard-related components
│   │       └── <span style="color: #9ecbff;">stats-card.tsx</span>    # Statistics card component
│   └── <span style="color: #85e89d;">ui</span>/                       # Reusable UI components
│       ├── <span style="color: #9ecbff;">button.tsx</span>            # Button component
│       ├── <span style="color: #9ecbff;">input.tsx</span>             # Input component
│       └── <span style="color: #9ecbff;">card.tsx</span>              # Card component
│
├── <span style="color: #79b8ff;">lib</span>/                          # Utility libraries and helpers
│   ├── <span style="color: #79b8ff;">auth.ts</span>                   # Server-side auth utilities
│   ├── <span style="color: #79b8ff;">auth-client.ts</span>            # Client-side auth utilities
│   ├── <span style="color: #79b8ff;">utils.ts</span>                  # General utility functions
│   └── <span style="color: #79b8ff;">db.ts</span>                     # Database connection and utilities
│
└── <span style="color: #79b8ff;">db</span>/                           # Database configuration
    ├── <span style="color: #79b8ff;">index.ts</span>                  # Database client initialization
    └── <span style="color: #79b8ff;">schema.ts</span>                 # Database schema definitions
</code>
</pre>

**Characteristics:**

- Minimal folder structure
- Components organized by feature
- Utilities in a single `lib/` folder
- No separate services layer
- Direct database access from components/pages

**When to Use:**

- Team size: 1-2 developers
- Timeline: 1-3 months
- Features: < 10 distinct features
- Complexity: Low to medium
- Maintenance: Minimal ongoing maintenance expected

---

## 🟡 Medium Project Structure (10-30 features)

Suitable for growing applications with multiple features and moderate complexity.

### 📋 Use Cases

**Perfect for:**

- **SaaS Applications**: Subscription-based services with multiple modules
- **E-commerce Platforms**: Online stores with product management, cart, and checkout
- **Content Management Systems**: CMS with user roles, content creation, and publishing
- **Social Platforms**: Community apps with posts, comments, and user interactions
- **Project Management Tools**: Task tracking, team collaboration, and reporting
- **Educational Platforms**: Learning management systems with courses and assessments
- **Healthcare Apps**: Patient portals, appointment scheduling, and medical records

**Example Projects:**

- Task management SaaS (Trello-like)
- E-commerce store with admin panel
- Social media platform
- Learning management system
- Project collaboration tool
- Restaurant ordering system
- Real estate listing platform

**Real-World Examples:**

- Small to medium SaaS products
- Regional e-commerce platforms
- Niche community platforms
- B2B productivity tools

<pre>
<code style="color: #e1e4e8;">src/
├── <span style="color: #79b8ff;">app</span>/                          # Next.js App Router directory
│   ├── <span style="color: #85e89d;">(app)</span>/                    # Route group for authenticated app pages
│   │   ├── <span style="color: #85e89d;">dashboard</span>/            # Dashboard page route
│   │   ├── <span style="color: #85e89d;">goals</span>/                # Goals feature routes
│   │   │   ├── <span style="color: #9ecbff;">page.tsx</span>          # Goals list page
│   │   │   └── <span style="color: #85e89d;">[id]</span>/            # Dynamic route for individual goal
│   │   │       └── <span style="color: #9ecbff;">page.tsx</span>      # Goal detail page
│   │   ├── <span style="color: #85e89d;">settings</span>/             # Settings page route
│   │   └── <span style="color: #9ecbff;">layout.tsx</span>            # Layout for authenticated routes
│   ├── <span style="color: #85e89d;">(auth)</span>/                   # Route group for authentication pages
│   │   ├── <span style="color: #85e89d;">login</span>/                # Login page route
│   │   ├── <span style="color: #85e89d;">sign-up</span>/              # Sign up page route
│   │   ├── <span style="color: #85e89d;">forgot-password</span>/      # Password recovery page route
│   │   └── <span style="color: #9ecbff;">layout.tsx</span>            # Layout for auth routes
│   ├── <span style="color: #85e89d;">(marketing)</span>/              # Route group for public marketing pages
│   │   ├── <span style="color: #9ecbff;">page.tsx</span>              # <span style="color: #85e89d;">Home</span>/landing page
│   │   └── <span style="color: #9ecbff;">layout.tsx</span>            # Layout for marketing pages
│   ├── <span style="color: #ffab70;">api</span>/                      # API routes directory
│   │   ├── <span style="color: #85e89d;">auth</span>/                 # Authentication API endpoints
│   │   ├── <span style="color: #85e89d;">goals</span>/                # Goals API endpoints
│   │   │   ├── <span style="color: #79b8ff;">route.ts</span>          # Goals CRUD operations
│   │   │   └── <span style="color: #85e89d;">[id]</span>/            # Dynamic route for goal operations
│   │   │       └── <span style="color: #79b8ff;">route.ts</span>      # Individual goal API handler
│   │   └── <span style="color: #85e89d;">users</span>/                # Users API endpoints
│   │       └── <span style="color: #79b8ff;">route.ts</span>          # Users API handler
│   ├── <span style="color: #9ecbff;">layout.tsx</span>                # Root layout component
│   └── <span style="color: #b392f0;">globals.css</span>               # Global CSS styles
│
├── <span style="color: #79b8ff;">components</span>/                   # React components directory
│   ├── <span style="color: #85e89d;">features</span>/                 # Feature-specific components
│   │   ├── <span style="color: #85e89d;">auth</span>/                 # Authentication components
│   │   │   ├── <span style="color: #9ecbff;">login-form.tsx</span>    # Login form component
│   │   │   ├── <span style="color: #9ecbff;">signup-form.tsx</span>   # Sign up form component
│   │   │   └── <span style="color: #9ecbff;">forgot-password-form.tsx</span>  # Password recovery form
│   │   ├── <span style="color: #85e89d;">goals</span>/                # Goals feature components
│   │   │   ├── <span style="color: #9ecbff;">goal-card.tsx</span>     # Goal card display component
│   │   │   ├── <span style="color: #9ecbff;">goal-list.tsx</span>     # Goals list component
│   │   │   └── <span style="color: #9ecbff;">goal-form.tsx</span>     # Goal <span style="color: #85e89d;">create</span>/edit form
│   │   └── <span style="color: #85e89d;">dashboard</span>/            # Dashboard components
│   │       ├── <span style="color: #9ecbff;">stats-card.tsx</span>    # Statistics card component
│   │       └── <span style="color: #9ecbff;">recent-activity.tsx</span>  # Recent activity feed
│   ├── <span style="color: #f97583;">layout</span>/                   # Layout components
│   │   ├── <span style="color: #79b8ff;">app</span>/                  # App layout components
│   │   │   ├── <span style="color: #9ecbff;">sidebar.tsx</span>       # Sidebar navigation
│   │   │   └── <span style="color: #9ecbff;">header.tsx</span>        # App header
│   │   ├── <span style="color: #85e89d;">auth</span>/                 # Auth layout components
│   │   │   └── <span style="color: #9ecbff;">auth-container.tsx</span>  # Auth page container
│   │   └── <span style="color: #85e89d;">marketing</span>/            # Marketing layout components
│   │       ├── <span style="color: #9ecbff;">navbar.tsx</span>        # Marketing navbar
│   │       └── <span style="color: #9ecbff;">footer.tsx</span>        # Marketing footer
│   ├── <span style="color: #85e89d;">shared</span>/                   # <span style="color: #85e89d;">Shared</span>/common components
│   │   ├── <span style="color: #9ecbff;">loading.tsx</span>           # Loading spinner component
│   │   ├── <span style="color: #9ecbff;">error-boundary.tsx</span>    # Error boundary component
│   │   └── <span style="color: #9ecbff;">toast.tsx</span>             # Toast notification component
│   └── <span style="color: #85e89d;">ui</span>/                       # Reusable UI primitives
│       ├── <span style="color: #9ecbff;">button.tsx</span>            # Button component
│       ├── <span style="color: #9ecbff;">input.tsx</span>             # Input component
│       ├── <span style="color: #9ecbff;">card.tsx</span>              # Card component
│       └── <span style="color: #9ecbff;">dialog.tsx</span>            # <span style="color: #85e89d;">Dialog</span>/modal component
│
├── <span style="color: #79b8ff;">lib</span>/                          # Utility libraries and helpers
│   ├── <span style="color: #79b8ff;">auth.ts</span>                   # Server-side auth utilities
│   ├── <span style="color: #79b8ff;">auth-client.ts</span>            # Client-side auth utilities
│   ├── <span style="color: #79b8ff;">utils.ts</span>                  # General utility functions
│   ├── <span style="color: #79b8ff;">constants.ts</span>              # Application constants
│   ├── <span style="color: #ffea7f;">validations</span>/              # Validation schemas (Zod)
│   │   ├── <span style="color: #79b8ff;">auth.ts</span>               # Auth validation schemas
│   │   ├── <span style="color: #79b8ff;">goals.ts</span>              # Goals validation schemas
│   │   └── <span style="color: #79b8ff;">user.ts</span>               # User validation schemas
│   └── <span style="color: #79b8ff;">hooks</span>/                    # Custom React hooks
│       ├── <span style="color: #79b8ff;">use-auth.ts</span>           # Authentication hook
│       ├── <span style="color: #79b8ff;">use-goals.ts</span>          # Goals data hook
│       └── <span style="color: #79b8ff;">use-local-storage.ts</span>  # Local storage hook
│
├── <span style="color: #79b8ff;">services</span>/                     # Business logic services layer
│   ├── auth.service.ts          # Authentication service
│   ├── goals.service.ts         # Goals business logic
│   └── api.service.ts           # API client service
│
├── <span style="color: #79b8ff;">db</span>/                           # Database configuration
│   ├── <span style="color: #79b8ff;">index.ts</span>                 # Database client initialization
│   ├── <span style="color: #79b8ff;">schema.ts</span>                # Database schema definitions
│   └── <span style="color: #ffea7f;">migrations</span>/              # Database migration files
│
├── <span style="color: #79b8ff;">types</span>/                        # TypeScript type definitions
│   ├── <span style="color: #79b8ff;">index.ts</span>                 # Main type exports
│   ├── <span style="color: #79b8ff;">auth.ts</span>                  # Authentication types
│   ├── <span style="color: #79b8ff;">goals.ts</span>                 # Goals types
│   └── <span style="color: #79b8ff;">api.ts</span>                   # API response types
│
└── <span style="color: #79b8ff;">config</span>/                       # Configuration files
    ├── <span style="color: #79b8ff;">env.ts</span>                   # Environment variables config
    └── <span style="color: #79b8ff;">site.ts</span>                  # Site configuration
</code>
</pre>

**Characteristics:**

- Feature-based component organization
- Separate services layer for business logic
- Validation schemas with Zod
- Custom hooks for reusable logic
- Type definitions centralized
- Environment configuration

**When to Use:**

- Team size: 2-5 developers
- Timeline: 3-6 months initial development
- Features: 10-30 distinct features
- Complexity: Medium
- Maintenance: Regular updates and feature additions expected
- Scalability: Planning for growth but not yet at enterprise scale

---

## 🟠 Large Project Structure (30-100 features)

Designed for complex applications with multiple domains and teams.

### 📋 Use Cases

**Perfect for:**

- **Enterprise SaaS**: Multi-tenant platforms with complex business logic
- **Marketplace Platforms**: Multi-sided marketplaces connecting buyers and sellers
- **Financial Applications**: Banking apps, payment processors, or fintech platforms
- **Healthcare Systems**: Electronic health records, telemedicine platforms
- **Enterprise Resource Planning (ERP)**: Complex business management systems
- **Customer Relationship Management (CRM)**: Sales, marketing, and customer service platforms
- **Analytics Platforms**: Business intelligence and data analytics tools
- **Collaboration Suites**: Comprehensive team collaboration with multiple integrated tools

**Example Projects:**

- Multi-tenant SaaS platform
- Marketplace with vendor management
- Banking or fintech application
- Healthcare patient management system
- Enterprise CRM platform
- Business intelligence dashboard
- Integrated collaboration suite
- Supply chain management system

**Real-World Examples:**

- Mid-market SaaS companies
- Growing fintech companies
- Healthcare technology platforms
- B2B enterprise software
- Multi-regional e-commerce platforms

<pre>
<code style="color: #e1e4e8;">src/
├── <span style="color: #79b8ff;">app</span>/                          # Next.js App Router directory
│   ├── <span style="color: #85e89d;">(app)</span>/                    # Route group for authenticated app pages
│   │   ├── <span style="color: #85e89d;">dashboard</span>/            # Dashboard page route
│   │   ├── <span style="color: #85e89d;">goals</span>/                # Goals feature routes
│   │   │   ├── <span style="color: #9ecbff;">page.tsx</span>          # Goals list page
│   │   │   ├── <span style="color: #85e89d;">[id]</span>/            # Dynamic route for individual goal
│   │   │   │   └── <span style="color: #9ecbff;">page.tsx</span>      # Goal detail page
│   │   │   └── <span style="color: #85e89d;">new</span>/              # Create new goal route
│   │   │       └── <span style="color: #9ecbff;">page.tsx</span>      # New goal form page
│   │   ├── <span style="color: #85e89d;">settings</span>/             # Settings routes
│   │   │   ├── <span style="color: #85e89d;">profile</span>/          # User profile settings
│   │   │   ├── <span style="color: #85e89d;">preferences</span>/      # User preferences
│   │   │   └── <span style="color: #85e89d;">security</span>/         # Security settings
│   │   ├── <span style="color: #85e89d;">analytics</span>/            # Analytics page route
│   │   └── <span style="color: #9ecbff;">layout.tsx</span>            # Layout for authenticated routes
│   ├── <span style="color: #85e89d;">(auth)</span>/                   # Route group for authentication pages
│   │   ├── <span style="color: #85e89d;">login</span>/                # Login page route
│   │   ├── <span style="color: #85e89d;">sign-up</span>/              # Sign up page route
│   │   ├── <span style="color: #85e89d;">forgot-password</span>/      # Password recovery page
│   │   ├── <span style="color: #85e89d;">reset-password</span>/       # Password reset page
│   │   └── <span style="color: #9ecbff;">layout.tsx</span>            # Layout for auth routes
│   ├── <span style="color: #85e89d;">(marketing)</span>/              # Route group for public marketing pages
│   │   ├── <span style="color: #9ecbff;">page.tsx</span>              # <span style="color: #85e89d;">Home</span>/landing page
│   │   ├── <span style="color: #85e89d;">about</span>/                # About page
│   │   ├── <span style="color: #85e89d;">pricing</span>/              # Pricing page
│   │   └── <span style="color: #9ecbff;">layout.tsx</span>            # Layout for marketing pages
│   ├── <span style="color: #ffab70;">api</span>/                      # API routes directory
│   │   ├── <span style="color: #85e89d;">auth</span>/                 # Authentication API endpoints
│   │   ├── <span style="color: #85e89d;">goals</span>/                # Goals API endpoints
│   │   │   ├── <span style="color: #79b8ff;">route.ts</span>          # Goals CRUD operations
│   │   │   └── <span style="color: #85e89d;">[id]</span>/            # Dynamic route for goal operations
│   │   │       └── <span style="color: #79b8ff;">route.ts</span>      # Individual goal API handler
│   │   ├── <span style="color: #85e89d;">users</span>/                # Users API endpoints
│   │   │   ├── <span style="color: #79b8ff;">route.ts</span>          # Users <span style="color: #85e89d;">list</span>/create
│   │   │   └── <span style="color: #85e89d;">[id]</span>/            # Dynamic route for user operations
│   │   │       └── <span style="color: #79b8ff;">route.ts</span>      # Individual user API handler
│   │   └── <span style="color: #85e89d;">analytics</span>/            # Analytics API endpoints
│   │       └── <span style="color: #79b8ff;">route.ts</span>          # Analytics data API
│   ├── <span style="color: #9ecbff;">layout.tsx</span>                # Root layout component
│   └── <span style="color: #b392f0;">globals.css</span>               # Global CSS styles
│
├── <span style="color: #79b8ff;">components</span>/                   # React components directory
│   ├── <span style="color: #85e89d;">features</span>/                 # Feature-specific components
│   │   ├── <span style="color: #85e89d;">auth</span>/                 # Authentication components
│   │   │   ├── <span style="color: #9ecbff;">login-form.tsx</span>    # Login form component
│   │   │   ├── <span style="color: #9ecbff;">signup-form.tsx</span>   # Sign up form component
│   │   │   ├── <span style="color: #9ecbff;">forgot-password-form.tsx</span>  # Password recovery form
│   │   │   └── <span style="color: #9ecbff;">reset-password-form.tsx</span>   # Password reset form
│   │   ├── <span style="color: #85e89d;">goals</span>/                # Goals feature components
│   │   │   ├── <span style="color: #9ecbff;">goal-card.tsx</span>     # Goal card display component
│   │   │   ├── <span style="color: #9ecbff;">goal-list.tsx</span>     # Goals list component
│   │   │   ├── <span style="color: #9ecbff;">goal-form.tsx</span>     # Goal <span style="color: #85e89d;">create</span>/edit form
│   │   │   ├── <span style="color: #9ecbff;">goal-detail.tsx</span>   # Goal detail view
│   │   │   └── <span style="color: #9ecbff;">goal-filters.tsx</span>  # Goal filtering component
│   │   ├── <span style="color: #85e89d;">dashboard</span>/            # Dashboard components
│   │   │   ├── <span style="color: #9ecbff;">stats-card.tsx</span>    # Statistics card component
│   │   │   ├── <span style="color: #9ecbff;">recent-activity.tsx</span>  # Recent activity feed
│   │   │   └── <span style="color: #85e89d;">charts</span>/           # Chart components
│   │   │       ├── <span style="color: #9ecbff;">line-chart.tsx</span>    # Line chart component
│   │   │       └── <span style="color: #9ecbff;">bar-chart.tsx</span>     # Bar chart component
│   │   └── <span style="color: #85e89d;">analytics</span>/            # Analytics components
│   │       ├── <span style="color: #9ecbff;">analytics-dashboard.tsx</span>  # Analytics dashboard
│   │       └── <span style="color: #9ecbff;">report-generator.tsx</span>     # Report generation component
│   ├── <span style="color: #f97583;">layout</span>/                   # Layout components
│   │   ├── <span style="color: #79b8ff;">app</span>/                  # App layout components
│   │   │   ├── <span style="color: #9ecbff;">sidebar.tsx</span>       # Sidebar navigation
│   │   │   ├── <span style="color: #9ecbff;">header.tsx</span>        # App header
│   │   │   ├── <span style="color: #9ecbff;">navigation.tsx</span>   # Main navigation component
│   │   │   └── <span style="color: #9ecbff;">breadcrumbs.tsx</span>  # Breadcrumb navigation
│   │   ├── <span style="color: #85e89d;">auth</span>/                 # Auth layout components
│   │   │   └── <span style="color: #9ecbff;">auth-container.tsx</span>  # Auth page container
│   │   └── <span style="color: #85e89d;">marketing</span>/            # Marketing layout components
│   │       ├── <span style="color: #9ecbff;">navbar.tsx</span>        # Marketing navbar
│   │       ├── <span style="color: #9ecbff;">footer.tsx</span>        # Marketing footer
│   │       └── <span style="color: #9ecbff;">hero-section.tsx</span>  # Hero section component
│   ├── <span style="color: #85e89d;">shared</span>/                   # <span style="color: #85e89d;">Shared</span>/common components
│   │   ├── <span style="color: #9ecbff;">loading.tsx</span>           # Loading spinner component
│   │   ├── <span style="color: #9ecbff;">error-boundary.tsx</span>    # Error boundary component
│   │   ├── <span style="color: #9ecbff;">toast.tsx</span>             # Toast notification component
│   │   ├── <span style="color: #9ecbff;">modal.tsx</span>             # Modal component
│   │   ├── <span style="color: #9ecbff;">confirm-dialog.tsx</span>    # Confirmation dialog
│   │   └── <span style="color: #9ecbff;">pagination.tsx</span>        # Pagination component
│   └── <span style="color: #85e89d;">ui</span>/                       # Reusable UI primitives
│       ├── <span style="color: #9ecbff;">button.tsx</span>            # Button component
│       ├── <span style="color: #9ecbff;">input.tsx</span>             # Input component
│       ├── <span style="color: #9ecbff;">card.tsx</span>              # Card component
│       ├── <span style="color: #9ecbff;">dialog.tsx</span>            # <span style="color: #85e89d;">Dialog</span>/modal component
│       ├── <span style="color: #9ecbff;">select.tsx</span>            # Select dropdown component
│       ├── <span style="color: #9ecbff;">table.tsx</span>             # Table component
│       └── <span style="color: #9ecbff;">tabs.tsx</span>              # Tabs component
│
├── <span style="color: #79b8ff;">lib</span>/                          # Utility libraries and helpers
│   ├── <span style="color: #79b8ff;">auth.ts</span>                   # Server-side auth utilities
│   ├── <span style="color: #79b8ff;">auth-client.ts</span>            # Client-side auth utilities
│   ├── <span style="color: #79b8ff;">utils.ts</span>                  # General utility functions
│   ├── <span style="color: #79b8ff;">constants.ts</span>              # Application constants
│   ├── <span style="color: #ffea7f;">validations</span>/              # Validation schemas (Zod)
│   │   ├── <span style="color: #79b8ff;">auth.ts</span>               # Auth validation schemas
│   │   ├── <span style="color: #79b8ff;">goals.ts</span>              # Goals validation schemas
│   │   ├── <span style="color: #79b8ff;">user.ts</span>               # User validation schemas
│   │   └── <span style="color: #79b8ff;">analytics.ts</span>          # Analytics validation schemas
│   ├── <span style="color: #79b8ff;">hooks</span>/                    # Custom React hooks
│   │   ├── <span style="color: #79b8ff;">use-auth.ts</span>           # Authentication hook
│   │   ├── <span style="color: #79b8ff;">use-goals.ts</span>          # Goals data hook
│   │   ├── <span style="color: #79b8ff;">use-local-storage.ts</span>  # Local storage hook
│   │   ├── <span style="color: #79b8ff;">use-debounce.ts</span>       # Debounce hook
│   │   └── <span style="color: #79b8ff;">use-media-query.ts</span>    # Media query hook
│   └── <span style="color: #ffea7f;">helpers</span>/                  # Helper utility functions
│       ├── <span style="color: #79b8ff;">formatters.ts</span>         # Data formatting utilities
│       ├── <span style="color: #79b8ff;">validators.ts</span>        # Additional validators
│       └── <span style="color: #79b8ff;">date-utils.ts</span>         # Date manipulation utilities
│
├── <span style="color: #79b8ff;">services</span>/                     # Business logic services layer
│   ├── auth.service.ts          # Authentication service
│   ├── goals.service.ts         # Goals business logic
│   ├── users.service.ts         # Users business logic
│   ├── analytics.service.ts     # Analytics business logic
│   ├── api.service.ts           # API client service
│   ├── cache.service.ts         # Caching service
│   └── storage.service.ts       # Storage service
│
├── <span style="color: #79b8ff;">stores</span>/                       # State management stores <span style="color: #85e89d;">(Zustand</span>/Redux)
│   ├── <span style="color: #79b8ff;">auth-store.ts</span>            # Authentication state store
│   ├── <span style="color: #79b8ff;">goals-store.ts</span>           # Goals state store
│   ├── <span style="color: #79b8ff;">ui-store.ts</span>              # UI state store
│   └── <span style="color: #79b8ff;">analytics-store.ts</span>       # Analytics state store
│
├── <span style="color: #79b8ff;">db</span>/                           # Database configuration
│   ├── <span style="color: #79b8ff;">index.ts</span>                 # Database client initialization
│   ├── <span style="color: #79b8ff;">schema.ts</span>                # Database schema definitions
│   ├── <span style="color: #ffea7f;">migrations</span>/              # Database migration files
│   └── <span style="color: #ffea7f;">seeds</span>/                   # Database seed files
│
├── <span style="color: #79b8ff;">types</span>/                        # TypeScript type definitions
│   ├── <span style="color: #79b8ff;">index.ts</span>                 # Main type exports
│   ├── <span style="color: #79b8ff;">auth.ts</span>                  # Authentication types
│   ├── <span style="color: #79b8ff;">goals.ts</span>                 # Goals types
│   ├── <span style="color: #79b8ff;">user.ts</span>                  # User types
│   ├── <span style="color: #79b8ff;">api.ts</span>                   # API response types
│   └── <span style="color: #79b8ff;">analytics.ts</span>             # Analytics types
│
├── <span style="color: #79b8ff;">hooks</span>/                        # Top-level custom hooks
│   ├── <span style="color: #79b8ff;">use-auth.ts</span>              # Authentication hook
│   ├── <span style="color: #79b8ff;">use-goals.ts</span>             # Goals data hook
│   ├── <span style="color: #79b8ff;">use-theme.ts</span>             # Theme management hook
│   └── <span style="color: #79b8ff;">use-analytics.ts</span>         # Analytics hook
│
├── <span style="color: #79b8ff;">config</span>/                       # Configuration files
│   ├── <span style="color: #79b8ff;">env.ts</span>                   # Environment variables config
│   ├── <span style="color: #79b8ff;">site.ts</span>                  # Site configuration
│   └── <span style="color: #79b8ff;">constants.ts</span>             # Application constants
│
└── <span style="color: #79b8ff;">styles</span>/                       # Global styles
    ├── <span style="color: #b392f0;">globals.css</span>              # Global CSS styles
    └── <span style="color: #b392f0;">themes.css</span>               # Theme CSS variables
</code>
</pre>

**Characteristics:**

- State management with stores
- Advanced caching strategies
- Helper utilities separated
- Multiple custom hooks
- Comprehensive type system
- Theming support

**When to Use:**

- Team size: 5-15 developers
- Timeline: 6-12+ months development
- Features: 30-100 distinct features
- Complexity: High
- Maintenance: Active development with multiple releases
- Scalability: Must handle significant user base and data volume
- Multi-team: Multiple development teams working on different domains

---

## 🔴 Enterprise Project Structure (100+ features)

For large-scale applications with multiple teams, domains, and complex business logic.

### 📋 Use Cases

**Perfect for:**

- **Global SaaS Platforms**: Large-scale multi-regional platforms serving millions of users
- **Enterprise Software**: Complex business applications for Fortune 500 companies
- **Financial Institutions**: Banking systems, trading platforms, or insurance platforms
- **Healthcare Systems**: Hospital management systems, medical device platforms
- **Government Platforms**: Public sector applications with high security requirements
- **Telecommunications**: Network management, customer portals, billing systems
- **Manufacturing Systems**: Production management, quality control, supply chain
- **Media & Entertainment**: Content platforms, streaming services, publishing systems

**Example Projects:**

- Global e-commerce platform (Amazon-scale)
- Enterprise banking application
- Hospital information system
- Government service portal
- Telecommunications billing system
- Manufacturing ERP system
- Large-scale content platform
- Multi-regional SaaS platform

**Real-World Examples:**

- Fortune 500 internal tools
- Global financial platforms
- Healthcare enterprise systems
- Government digital services
- Large-scale marketplaces
- Enterprise cloud platforms

<pre>
<code style="color: #e1e4e8;">src/
├── <span style="color: #79b8ff;">app</span>/                          # Next.js App Router directory
│   ├── <span style="color: #85e89d;">(app)</span>/                    # Route group for authenticated app pages
│   │   ├── <span style="color: #85e89d;">dashboard</span>/            # Dashboard page route
│   │   ├── <span style="color: #85e89d;">goals</span>/                # Goals feature routes
│   │   │   ├── <span style="color: #9ecbff;">page.tsx</span>          # Goals list page
│   │   │   ├── <span style="color: #85e89d;">[id]</span>/            # Dynamic route for individual goal
│   │   │   │   └── <span style="color: #9ecbff;">page.tsx</span>      # Goal detail page
│   │   │   ├── <span style="color: #85e89d;">new</span>/              # Create new goal route
│   │   │   │   └── <span style="color: #9ecbff;">page.tsx</span>      # New goal form page
│   │   │   └── <span style="color: #85e89d;">templates</span>/        # Goal templates route
│   │   │       └── <span style="color: #9ecbff;">page.tsx</span>      # Goal templates page
│   │   ├── <span style="color: #85e89d;">settings</span>/             # Settings routes
│   │   │   ├── <span style="color: #85e89d;">profile</span>/          # User profile settings
│   │   │   ├── <span style="color: #85e89d;">preferences</span>/      # User preferences
│   │   │   ├── <span style="color: #85e89d;">security</span>/         # Security settings
│   │   │   └── <span style="color: #85e89d;">integrations</span>/     # Third-party integrations
│   │   ├── <span style="color: #85e89d;">analytics</span>/            # Analytics routes
│   │   │   ├── <span style="color: #85e89d;">overview</span>/         # Analytics overview page
│   │   │   ├── <span style="color: #85e89d;">reports</span>/          # Reports page
│   │   │   └── <span style="color: #85e89d;">exports</span>/          # Data exports page
│   │   ├── <span style="color: #85e89d;">teams</span>/                # Teams feature routes
│   │   │   ├── <span style="color: #9ecbff;">page.tsx</span>          # Teams list page
│   │   │   └── <span style="color: #85e89d;">[id]</span>/            # Dynamic route for team
│   │   │       └── <span style="color: #9ecbff;">page.tsx</span>      # Team detail page
│   │   └── <span style="color: #9ecbff;">layout.tsx</span>            # Layout for authenticated routes
│   ├── <span style="color: #85e89d;">(auth)</span>/                   # Route group for authentication pages
│   │   ├── <span style="color: #85e89d;">login</span>/                # Login page route
│   │   ├── <span style="color: #85e89d;">sign-up</span>/              # Sign up page route
│   │   ├── <span style="color: #85e89d;">forgot-password</span>/      # Password recovery page
│   │   ├── <span style="color: #85e89d;">reset-password</span>/       # Password reset page
│   │   ├── <span style="color: #85e89d;">verify-email</span>/         # Email verification page
│   │   └── <span style="color: #9ecbff;">layout.tsx</span>            # Layout for auth routes
│   ├── <span style="color: #85e89d;">(marketing)</span>/              # Route group for public marketing pages
│   │   ├── <span style="color: #9ecbff;">page.tsx</span>              # <span style="color: #85e89d;">Home</span>/landing page
│   │   ├── <span style="color: #85e89d;">about</span>/                # About page
│   │   ├── <span style="color: #85e89d;">pricing</span>/              # Pricing page
│   │   ├── <span style="color: #85e89d;">blog</span>/                 # Blog routes
│   │   │   ├── <span style="color: #9ecbff;">page.tsx</span>          # Blog list page
│   │   │   └── <span style="color: #85e89d;">[slug]</span>/          # Dynamic route for blog post
│   │   │       └── <span style="color: #9ecbff;">page.tsx</span>      # Blog post detail page
│   │   └── <span style="color: #9ecbff;">layout.tsx</span>            # Layout for marketing pages
│   ├── <span style="color: #ffab70;">api</span>/                      # API routes directory
│   │   ├── <span style="color: #85e89d;">auth</span>/                 # Authentication API endpoints
│   │   ├── <span style="color: #85e89d;">goals</span>/                # Goals API endpoints
│   │   │   ├── <span style="color: #79b8ff;">route.ts</span>          # Goals CRUD operations
│   │   │   ├── <span style="color: #85e89d;">[id]</span>/            # Dynamic route for goal operations
│   │   │   │   └── <span style="color: #79b8ff;">route.ts</span>      # Individual goal API handler
│   │   │   └── <span style="color: #85e89d;">templates</span>/        # Goal templates API
│   │   │       └── <span style="color: #79b8ff;">route.ts</span>      # Templates API handler
│   │   ├── <span style="color: #85e89d;">users</span>/                # Users API endpoints
│   │   │   ├── <span style="color: #79b8ff;">route.ts</span>          # Users <span style="color: #85e89d;">list</span>/create
│   │   │   └── <span style="color: #85e89d;">[id]</span>/            # Dynamic route for user operations
│   │   │       └── <span style="color: #79b8ff;">route.ts</span>      # Individual user API handler
│   │   ├── <span style="color: #85e89d;">teams</span>/                # Teams API endpoints
│   │   │   ├── <span style="color: #79b8ff;">route.ts</span>          # Teams <span style="color: #85e89d;">list</span>/create
│   │   │   └── <span style="color: #85e89d;">[id]</span>/            # Dynamic route for team operations
│   │   │       └── <span style="color: #79b8ff;">route.ts</span>      # Individual team API handler
│   │   ├── <span style="color: #85e89d;">analytics</span>/            # Analytics API endpoints
│   │   │   ├── <span style="color: #79b8ff;">route.ts</span>          # Analytics data API
│   │   │   └── <span style="color: #85e89d;">export</span>/           # Analytics export API
│   │   │       └── <span style="color: #79b8ff;">route.ts</span>      # Export data handler
│   │   └── <span style="color: #85e89d;">webhooks</span>/             # Webhook endpoints
│   │       └── <span style="color: #79b8ff;">route.ts</span>          # Webhook handler
│   ├── <span style="color: #9ecbff;">layout.tsx</span>                # Root layout component
│   └── <span style="color: #b392f0;">globals.css</span>               # Global CSS styles
│
├── <span style="color: #79b8ff;">components</span>/                   # React components directory
│   ├── <span style="color: #85e89d;">features</span>/                 # Feature-specific components
│   │   ├── <span style="color: #85e89d;">auth</span>/                 # Authentication components
│   │   │   ├── <span style="color: #9ecbff;">login-form.tsx</span>    # Login form component
│   │   │   ├── <span style="color: #9ecbff;">signup-form.tsx</span>   # Sign up form component
│   │   │   ├── <span style="color: #9ecbff;">forgot-password-form.tsx</span>  # Password recovery form
│   │   │   ├── <span style="color: #9ecbff;">reset-password-form.tsx</span>   # Password reset form
│   │   │   └── <span style="color: #9ecbff;">verify-email-form.tsx</span>     # Email verification form
│   │   ├── <span style="color: #85e89d;">goals</span>/                # Goals feature components
│   │   │   ├── <span style="color: #9ecbff;">goal-card.tsx</span>     # Goal card display component
│   │   │   ├── <span style="color: #9ecbff;">goal-list.tsx</span>     # Goals list component
│   │   │   ├── <span style="color: #9ecbff;">goal-form.tsx</span>     # Goal <span style="color: #85e89d;">create</span>/edit form
│   │   │   ├── <span style="color: #9ecbff;">goal-detail.tsx</span>   # Goal detail view
│   │   │   ├── <span style="color: #9ecbff;">goal-filters.tsx</span>  # Goal filtering component
│   │   │   ├── <span style="color: #85e89d;">goal-templates</span>/    # Goal template components
│   │   │   │   ├── <span style="color: #9ecbff;">template-card.tsx</span>      # Template card
│   │   │   │   └── <span style="color: #9ecbff;">template-selector.tsx</span>   # Template selector
│   │   │   └── <span style="color: #85e89d;">goal-analytics</span>/    # Goal analytics components
│   │   │       └── <span style="color: #9ecbff;">goal-progress.tsx</span>      # Goal progress tracker
│   │   ├── <span style="color: #85e89d;">dashboard</span>/            # Dashboard components
│   │   │   ├── <span style="color: #9ecbff;">stats-card.tsx</span>    # Statistics card component
│   │   │   ├── <span style="color: #9ecbff;">recent-activity.tsx</span>  # Recent activity feed
│   │   │   ├── <span style="color: #85e89d;">charts</span>/           # Chart components
│   │   │   │   ├── <span style="color: #9ecbff;">line-chart.tsx</span>    # Line chart component
│   │   │   │   ├── <span style="color: #9ecbff;">bar-chart.tsx</span>     # Bar chart component
│   │   │   │   └── <span style="color: #9ecbff;">pie-chart.tsx</span>     # Pie chart component
│   │   │   └── <span style="color: #85e89d;">widgets</span>/          # Dashboard widgets
│   │   │       ├── <span style="color: #9ecbff;">quick-actions.tsx</span>    # Quick actions widget
│   │   │       └── <span style="color: #9ecbff;">notifications.tsx</span>     # Notifications widget
│   │   ├── <span style="color: #85e89d;">analytics</span>/            # Analytics components
│   │   │   ├── <span style="color: #9ecbff;">analytics-dashboard.tsx</span>  # Analytics dashboard
│   │   │   ├── <span style="color: #9ecbff;">report-generator.tsx</span>     # Report generation component
│   │   │   ├── <span style="color: #9ecbff;">data-export.tsx</span>          # Data export component
│   │   │   └── <span style="color: #85e89d;">filters</span>/                 # Analytics filter components
│   │   │       ├── <span style="color: #9ecbff;">date-range-picker.tsx</span> # Date range picker
│   │   │       └── <span style="color: #9ecbff;">metric-selector.tsx</span>   # Metric selector
│   │   └── <span style="color: #85e89d;">teams</span>/                # Teams feature components
│   │       ├── <span style="color: #9ecbff;">team-card.tsx</span>     # Team card component
│   │       ├── <span style="color: #9ecbff;">team-list.tsx</span>     # Teams list component
│   │       ├── <span style="color: #9ecbff;">team-form.tsx</span>    # Team <span style="color: #85e89d;">create</span>/edit form
│   │       └── <span style="color: #85e89d;">team-members</span>/     # Team member components
│   │           ├── <span style="color: #9ecbff;">member-list.tsx</span>    # Member list
│   │           └── <span style="color: #9ecbff;">member-invite.tsx</span>  # Member invitation
│   ├── <span style="color: #f97583;">layout</span>/                   # Layout components
│   │   ├── <span style="color: #79b8ff;">app</span>/                  # App layout components
│   │   │   ├── <span style="color: #85e89d;">sidebar</span>/          # Sidebar components
│   │   │   │   ├── <span style="color: #9ecbff;">sidebar.tsx</span>       # Main sidebar
│   │   │   │   ├── <span style="color: #9ecbff;">sidebar-nav.tsx</span>   # Sidebar navigation
│   │   │   │   └── <span style="color: #9ecbff;">sidebar-footer.tsx</span> # Sidebar footer
│   │   │   ├── <span style="color: #85e89d;">header</span>/            # Header components
│   │   │   │   ├── <span style="color: #9ecbff;">header.tsx</span>         # Main header
│   │   │   │   ├── <span style="color: #9ecbff;">user-menu.tsx</span>     # User menu dropdown
│   │   │   │   └── <span style="color: #9ecbff;">notifications.tsx</span>  # Notifications component
│   │   │   ├── <span style="color: #85e89d;">navigation</span>/       # Navigation components
│   │   │   │   └── <span style="color: #9ecbff;">main-nav.tsx</span>      # Main navigation
│   │   │   └── <span style="color: #9ecbff;">breadcrumbs.tsx</span>   # Breadcrumb navigation
│   │   ├── <span style="color: #85e89d;">auth</span>/                 # Auth layout components
│   │   │   └── <span style="color: #9ecbff;">auth-container.tsx</span>  # Auth page container
│   │   └── <span style="color: #85e89d;">marketing</span>/            # Marketing layout components
│   │       ├── <span style="color: #9ecbff;">navbar.tsx</span>        # Marketing navbar
│   │       ├── <span style="color: #9ecbff;">footer.tsx</span>        # Marketing footer
│   │       └── <span style="color: #9ecbff;">hero-section.tsx</span>  # Hero section component
│   ├── <span style="color: #85e89d;">shared</span>/                   # <span style="color: #85e89d;">Shared</span>/common components
│   │   ├── <span style="color: #85e89d;">loading</span>/              # Loading components
│   │   │   ├── <span style="color: #9ecbff;">loading.tsx</span>       # Loading spinner
│   │   │   └── <span style="color: #9ecbff;">skeleton.tsx</span>     # Skeleton loader
│   │   ├── <span style="color: #9ecbff;">error-boundary.tsx</span>    # Error boundary component
│   │   ├── <span style="color: #85e89d;">toast</span>/                # Toast notification components
│   │   │   ├── <span style="color: #9ecbff;">toast.tsx</span>         # Toast component
│   │   │   └── <span style="color: #9ecbff;">toast-provider.tsx</span> # Toast provider
│   │   ├── <span style="color: #85e89d;">modal</span>/                # Modal components
│   │   │   ├── <span style="color: #9ecbff;">modal.tsx</span>         # Modal component
│   │   │   └── <span style="color: #9ecbff;">confirm-dialog.tsx</span> # Confirmation dialog
│   │   ├── <span style="color: #9ecbff;">pagination.tsx</span>        # Pagination component
│   │   └── <span style="color: #9ecbff;">empty-state.tsx</span>       # Empty state component
│   └── <span style="color: #85e89d;">ui</span>/                       # Reusable UI primitives
│       ├── <span style="color: #9ecbff;">button.tsx</span>            # Button component
│       ├── <span style="color: #9ecbff;">input.tsx</span>             # Input component
│       ├── <span style="color: #9ecbff;">card.tsx</span>              # Card component
│       ├── <span style="color: #9ecbff;">dialog.tsx</span>            # <span style="color: #85e89d;">Dialog</span>/modal component
│       ├── <span style="color: #9ecbff;">select.tsx</span>            # Select dropdown component
│       ├── <span style="color: #9ecbff;">table.tsx</span>             # Table component
│       ├── <span style="color: #9ecbff;">tabs.tsx</span>              # Tabs component
│       ├── <span style="color: #9ecbff;">dropdown-menu.tsx</span>     # Dropdown menu component
│       ├── <span style="color: #9ecbff;">tooltip.tsx</span>           # Tooltip component
│       └── <span style="color: #9ecbff;">popover.tsx</span>           # Popover component
│
├── <span style="color: #79b8ff;">lib</span>/                          # Utility libraries and helpers
│   ├── <span style="color: #79b8ff;">auth.ts</span>                   # Server-side auth utilities
│   ├── <span style="color: #79b8ff;">auth-client.ts</span>            # Client-side auth utilities
│   ├── <span style="color: #79b8ff;">utils.ts</span>                  # General utility functions
│   ├── <span style="color: #79b8ff;">constants.ts</span>              # Application constants
│   ├── <span style="color: #ffea7f;">validations</span>/              # Validation schemas (Zod)
│   │   ├── <span style="color: #79b8ff;">auth.ts</span>               # Auth validation schemas
│   │   ├── <span style="color: #79b8ff;">goals.ts</span>              # Goals validation schemas
│   │   ├── <span style="color: #79b8ff;">user.ts</span>               # User validation schemas
│   │   ├── <span style="color: #79b8ff;">teams.ts</span>              # Teams validation schemas
│   │   └── <span style="color: #79b8ff;">analytics.ts</span>          # Analytics validation schemas
│   ├── <span style="color: #79b8ff;">hooks</span>/                    # Custom React hooks
│   │   ├── <span style="color: #79b8ff;">use-auth.ts</span>           # Authentication hook
│   │   ├── <span style="color: #79b8ff;">use-goals.ts</span>          # Goals data hook
│   │   ├── <span style="color: #79b8ff;">use-local-storage.ts</span>  # Local storage hook
│   │   ├── <span style="color: #79b8ff;">use-debounce.ts</span>       # Debounce hook
│   │   ├── <span style="color: #79b8ff;">use-media-query.ts</span>    # Media query hook
│   │   ├── <span style="color: #79b8ff;">use-intersection.ts</span>  # Intersection observer hook
│   │   └── <span style="color: #79b8ff;">use-keyboard-shortcut.ts</span> # Keyboard shortcut hook
│   ├── <span style="color: #ffea7f;">helpers</span>/                  # Helper utility functions
│   │   ├── <span style="color: #79b8ff;">formatters.ts</span>         # Data formatting utilities
│   │   ├── <span style="color: #79b8ff;">validators.ts</span>         # Additional validators
│   │   ├── <span style="color: #79b8ff;">date-utils.ts</span>         # Date manipulation utilities
│   │   └── <span style="color: #79b8ff;">string-utils.ts</span>       # String manipulation utilities
│   └── <span style="color: #79b8ff;">middleware</span>/               # Request middleware utilities
│       ├── <span style="color: #79b8ff;">rate-limiter.ts</span>       # Rate limiting middleware
│       └── <span style="color: #79b8ff;">request-validator.ts</span>  # Request validation middleware
│
├── <span style="color: #79b8ff;">services</span>/                     # Business logic services layer (domain-organized)
│   ├── <span style="color: #85e89d;">auth</span>/                     # Authentication services
│   │   ├── auth.service.ts      # Authentication service
│   │   └── session.service.ts   # Session management service
│   ├── <span style="color: #85e89d;">goals</span>/                    # Goals services
│   │   ├── goals.service.ts     # Goals business logic
│   │   └── templates.service.ts # Goal templates service
│   ├── <span style="color: #85e89d;">users</span>/                    # Users services
│   │   └── users.service.ts     # Users business logic
│   ├── <span style="color: #85e89d;">teams</span>/                    # Teams services
│   │   └── teams.service.ts     # Teams business logic
│   ├── <span style="color: #85e89d;">analytics</span>/                # Analytics services
│   │   ├── analytics.service.ts # Analytics business logic
│   │   └── reports.service.ts   # Reports generation service
│   ├── <span style="color: #ffab70;">api</span>/                      # API services
│   │   ├── api.service.ts       # Main API client
│   │   ├── <span style="color: #79b8ff;">http-client.ts</span>       # HTTP client wrapper
│   │   └── <span style="color: #79b8ff;">error-handler.ts</span>     # Error handling service
│   ├── <span style="color: #85e89d;">cache</span>/                    # Caching services
│   │   ├── cache.service.ts     # Cache service
│   │   └── <span style="color: #79b8ff;">cache-strategies.ts</span>  # Cache strategy implementations
│   ├── <span style="color: #85e89d;">storage</span>/                  # Storage services
│   │   ├── storage.service.ts   # Storage service
│   │   └── file-upload.service.ts # File upload service
│   └── <span style="color: #85e89d;">notifications</span>/            # Notification services
│       └── notification.service.ts # Notification service
│
├── <span style="color: #79b8ff;">stores</span>/                       # State management stores (domain-organized)
│   ├── <span style="color: #85e89d;">auth</span>/                     # Authentication stores
│   │   ├── <span style="color: #79b8ff;">auth-store.ts</span>        # Authentication state store
│   │   └── <span style="color: #79b8ff;">session-store.ts</span>     # Session state store
│   ├── <span style="color: #85e89d;">goals</span>/                    # Goals stores
│   │   ├── <span style="color: #79b8ff;">goals-store.ts</span>       # Goals state store
│   │   └── <span style="color: #79b8ff;">templates-store.ts</span>   # Templates state store
│   ├── <span style="color: #85e89d;">ui</span>/                       # UI stores
│   │   ├── <span style="color: #79b8ff;">ui-store.ts</span>          # General UI state
│   │   ├── <span style="color: #79b8ff;">theme-store.ts</span>       # Theme state store
│   │   └── <span style="color: #79b8ff;">sidebar-store.ts</span>     # Sidebar state store
│   └── <span style="color: #85e89d;">analytics</span>/                # Analytics stores
│       └── <span style="color: #79b8ff;">analytics-store.ts</span>   # Analytics state store
│
├── <span style="color: #79b8ff;">db</span>/                           # Database configuration
│   ├── <span style="color: #79b8ff;">index.ts</span>                 # Database client initialization
│   ├── <span style="color: #ffea7f;">schema</span>/                   # Modular schema definitions
│   │   ├── <span style="color: #79b8ff;">auth.ts</span>              # Authentication schema
│   │   ├── <span style="color: #79b8ff;">goals.ts</span>             # Goals schema
│   │   ├── <span style="color: #79b8ff;">users.ts</span>             # Users schema
│   │   ├── <span style="color: #79b8ff;">teams.ts</span>             # Teams schema
│   │   └── <span style="color: #79b8ff;">analytics.ts</span>         # Analytics schema
│   ├── <span style="color: #ffea7f;">migrations</span>/              # Database migration files
│   ├── <span style="color: #ffea7f;">seeds</span>/                   # Database seed files
│   └── <span style="color: #ffea7f;">queries</span>/                 # Database query functions
│       ├── goals.queries.ts     # Goals queries
│       └── users.queries.ts     # Users queries
│
├── <span style="color: #79b8ff;">types</span>/                        # TypeScript type definitions
│   ├── <span style="color: #79b8ff;">index.ts</span>                 # Main type exports
│   ├── <span style="color: #79b8ff;">auth.ts</span>                  # Authentication types
│   ├── <span style="color: #79b8ff;">goals.ts</span>                 # Goals types
│   ├── <span style="color: #79b8ff;">user.ts</span>                  # User types
│   ├── <span style="color: #79b8ff;">teams.ts</span>                 # Teams types
│   ├── <span style="color: #79b8ff;">api.ts</span>                   # API response types
│   ├── <span style="color: #79b8ff;">analytics.ts</span>             # Analytics types
│   └── <span style="color: #79b8ff;">common.ts</span>                # <span style="color: #85e89d;">Common</span>/shared types
│
├── <span style="color: #79b8ff;">hooks</span>/                        # Top-level custom hooks
│   ├── <span style="color: #79b8ff;">use-auth.ts</span>              # Authentication hook
│   ├── <span style="color: #79b8ff;">use-goals.ts</span>             # Goals data hook
│   ├── <span style="color: #79b8ff;">use-theme.ts</span>             # Theme management hook
│   ├── <span style="color: #79b8ff;">use-analytics.ts</span>         # Analytics hook
│   └── <span style="color: #79b8ff;">use-teams.ts</span>             # Teams hook
│
├── <span style="color: #79b8ff;">config</span>/                       # Configuration files
│   ├── <span style="color: #79b8ff;">env.ts</span>                   # Environment variables config
│   ├── <span style="color: #79b8ff;">site.ts</span>                  # Site configuration
│   ├── <span style="color: #79b8ff;">constants.ts</span>             # Application constants
│   └── <span style="color: #79b8ff;">feature-flags.ts</span>         # Feature flags configuration
│
├── <span style="color: #79b8ff;">middleware</span>/                   # Next.js middleware
│   ├── auth.middleware.ts       # Authentication middleware
│   ├── rate-limit.middleware.ts # Rate limiting middleware
│   └── logging.middleware.ts    # Logging middleware
│
├── <span style="color: #79b8ff;">styles</span>/                       # Global styles
│   ├── <span style="color: #b392f0;">globals.css</span>              # Global CSS styles
│   ├── <span style="color: #85e89d;">themes</span>/                  # Theme styles
│   │   ├── <span style="color: #b392f0;">light.css</span>            # Light theme
│   │   └── <span style="color: #b392f0;">dark.css</span>             # Dark theme
│   └── <span style="color: #79b8ff;">components</span>/              # Component-specific styles
│       └── <span style="color: #b392f0;">custom-components.css</span> # Custom component styles
│
└── <span style="color: #79b8ff;">tests</span>/                        # Test files
    ├── <span style="color: #85e89d;">unit</span>/                     # Unit tests
    ├── <span style="color: #85e89d;">integration</span>/              # Integration tests
    └── <span style="color: #85e89d;">e2e</span>/                      # End-to-end tests
</code>
</pre>

**Characteristics:**

- Domain-driven organization
- Service layer organized by domain
- Separate query layer for database
- Middleware for cross-cutting concerns
- Feature flags for gradual rollouts
- Comprehensive testing structure
- Advanced caching strategies
- Modular schema organization

**When to Use:**

- Team size: 15+ developers across multiple teams
- Timeline: 12+ months with continuous development
- Features: 100+ distinct features across multiple domains
- Complexity: Very high
- Maintenance: Continuous deployment with multiple releases per day
- Scalability: Must handle millions of users and petabytes of data
- Multi-team: Multiple autonomous teams with clear domain boundaries
- Compliance: Must meet strict regulatory requirements (HIPAA, SOC2, GDPR, etc.)
- Reliability: 99.9%+ uptime requirements with disaster recovery

---

## 🎯 Choosing the Right Structure

### Quick Decision Matrix

| Factor          | Small      | Medium     | Large        | Enterprise |
| --------------- | ---------- | ---------- | ------------ | ---------- |
| **Team Size**   | 1-2        | 2-5        | 5-15         | 15+        |
| **Features**    | < 10       | 10-30      | 30-100       | 100+       |
| **Timeline**    | 1-3 months | 3-6 months | 6-12+ months | 12+ months |
| **Complexity**  | Low        | Medium     | High         | Very High  |
| **Users**       | < 1K       | 1K-100K    | 100K-1M      | 1M+        |
| **Data Volume** | Small      | Medium     | Large        | Very Large |
| **Compliance**  | Basic      | Standard   | Advanced     | Enterprise |

### Decision Guidelines

- **🟢 Small**: Start here for new projects. Easy to refactor as you grow. Perfect for MVPs and learning.
- **🟡 Medium**: Use when you have 10+ features and need better organization. Ideal for growing SaaS products.
- **🟠 Large**: Adopt when working with multiple teams or complex domains. Suitable for established businesses.
- **🔴 Enterprise**: For applications with 100+ features, multiple teams, and complex business requirements. Global scale platforms.

### Migration Path

**Recommended Evolution:**

1. **Start Small**: Begin with the small structure for rapid development
2. **Grow to Medium**: Add services layer and better organization as features increase
3. **Scale to Large**: Introduce state management and advanced patterns with team growth
4. **Enterprise**: Adopt domain-driven design when multiple teams and complex domains emerge

**Key Principles:**

- ✅ Start simple, refactor when needed
- ✅ Don't over-engineer early
- ✅ Add structure as complexity grows
- ✅ Maintain consistency within each structure
- ✅ Plan for migration paths between structures

---

## 📚 Additional Resources

- [Next.js Documentation](https://nextjs.org/docs)
- [TypeScript Best Practices](https://www.typescriptlang.org/docs/handbook/declaration-files/do-s-and-don-ts.html)
- [React Patterns](https://reactpatterns.com/)
- [Domain-Driven Design](https://martinfowler.com/bliki/DomainDrivenDesign.html)

---

## 🤝 Contributing

Contributions are welcome! If you have suggestions for improving these structures or want to add more use cases, please feel free to open an issue or submit a pull request.
