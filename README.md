# Next.js Project Structures by Scale

This document presents different project structures for Next.js applications, organized from small to large-scale projects.

---

## 🟢 Small Project Structure (< 10 features)

Ideal for MVPs, prototypes, or simple applications with limited functionality.

```
src/
├── app/                          # Next.js App Router directory (routing & pages)
│   ├── (app)/                    # Route group for authenticated app pages
│   │   ├── dashboard/            # Dashboard page route
│   │   │   └── page.tsx          # Dashboard page component
│   │   ├── settings/             # Settings page route
│   │   │   └── page.tsx          # Settings page component
│   │   └── layout.tsx            # Layout wrapper for authenticated routes
│   ├── (auth)/                   # Route group for authentication pages
│   │   ├── login/                # Login page route
│   │   │   └── page.tsx          # Login page component
│   │   ├── sign-up/              # Sign up page route
│   │   │   └── page.tsx          # Sign up page component
│   │   └── layout.tsx            # Layout wrapper for auth routes
│   ├── api/                      # API routes directory
│   │   └── auth/                 # Authentication API endpoints
│   │       └── [...all]/         # Catch-all route for auth handlers
│   │           └── route.ts       # Auth API route handler
│   ├── layout.tsx                # Root layout component
│   └── globals.css               # Global CSS styles
│
├── components/                   # React components directory
│   ├── features/                 # Feature-specific components
│   │   ├── auth/                 # Authentication-related components
│   │   │   ├── login-form.tsx    # Login form component
│   │   │   └── signup-form.tsx   # Sign up form component
│   │   └── dashboard/            # Dashboard-related components
│   │       └── stats-card.tsx    # Statistics card component
│   └── ui/                       # Reusable UI components
│       ├── button.tsx            # Button component
│       ├── input.tsx             # Input component
│       └── card.tsx              # Card component
│
├── lib/                          # Utility libraries and helpers
│   ├── auth.ts                   # Server-side auth utilities
│   ├── auth-client.ts            # Client-side auth utilities
│   ├── utils.ts                  # General utility functions
│   └── db.ts                     # Database connection and utilities
│
└── db/                           # Database configuration
    ├── index.ts                  # Database client initialization
    └── schema.ts                 # Database schema definitions
```

**Characteristics:**

- Minimal folder structure
- Components organized by feature
- Utilities in a single `lib/` folder
- No separate services layer
- Direct database access from components/pages

---

## 🟡 Medium Project Structure (10-30 features)

Suitable for growing applications with multiple features and moderate complexity.

```
src/
├── app/                          # Next.js App Router directory
│   ├── (app)/                    # Route group for authenticated app pages
│   │   ├── dashboard/            # Dashboard page route
│   │   ├── goals/                # Goals feature routes
│   │   │   ├── page.tsx          # Goals list page
│   │   │   └── [id]/            # Dynamic route for individual goal
│   │   │       └── page.tsx      # Goal detail page
│   │   ├── settings/             # Settings page route
│   │   └── layout.tsx            # Layout for authenticated routes
│   ├── (auth)/                   # Route group for authentication pages
│   │   ├── login/                # Login page route
│   │   ├── sign-up/              # Sign up page route
│   │   ├── forgot-password/      # Password recovery page route
│   │   └── layout.tsx            # Layout for auth routes
│   ├── (marketing)/              # Route group for public marketing pages
│   │   ├── page.tsx              # Home/landing page
│   │   └── layout.tsx            # Layout for marketing pages
│   ├── api/                      # API routes directory
│   │   ├── auth/                 # Authentication API endpoints
│   │   ├── goals/                # Goals API endpoints
│   │   │   ├── route.ts          # Goals CRUD operations
│   │   │   └── [id]/            # Dynamic route for goal operations
│   │   │       └── route.ts      # Individual goal API handler
│   │   └── users/                # Users API endpoints
│   │       └── route.ts          # Users API handler
│   ├── layout.tsx                # Root layout component
│   └── globals.css               # Global CSS styles
│
├── components/                   # React components directory
│   ├── features/                 # Feature-specific components
│   │   ├── auth/                 # Authentication components
│   │   │   ├── login-form.tsx    # Login form component
│   │   │   ├── signup-form.tsx   # Sign up form component
│   │   │   └── forgot-password-form.tsx  # Password recovery form
│   │   ├── goals/                # Goals feature components
│   │   │   ├── goal-card.tsx     # Goal card display component
│   │   │   ├── goal-list.tsx     # Goals list component
│   │   │   └── goal-form.tsx     # Goal create/edit form
│   │   └── dashboard/            # Dashboard components
│   │       ├── stats-card.tsx    # Statistics card component
│   │       └── recent-activity.tsx  # Recent activity feed
│   ├── layout/                   # Layout components
│   │   ├── app/                  # App layout components
│   │   │   ├── sidebar.tsx       # Sidebar navigation
│   │   │   └── header.tsx        # App header
│   │   ├── auth/                 # Auth layout components
│   │   │   └── auth-container.tsx  # Auth page container
│   │   └── marketing/            # Marketing layout components
│   │       ├── navbar.tsx        # Marketing navbar
│   │       └── footer.tsx        # Marketing footer
│   ├── shared/                   # Shared/common components
│   │   ├── loading.tsx           # Loading spinner component
│   │   ├── error-boundary.tsx    # Error boundary component
│   │   └── toast.tsx             # Toast notification component
│   └── ui/                       # Reusable UI primitives
│       ├── button.tsx            # Button component
│       ├── input.tsx             # Input component
│       ├── card.tsx              # Card component
│       └── dialog.tsx            # Dialog/modal component
│
├── lib/                          # Utility libraries and helpers
│   ├── auth.ts                   # Server-side auth utilities
│   ├── auth-client.ts            # Client-side auth utilities
│   ├── utils.ts                  # General utility functions
│   ├── constants.ts              # Application constants
│   ├── validations/              # Validation schemas (Zod)
│   │   ├── auth.ts               # Auth validation schemas
│   │   ├── goals.ts              # Goals validation schemas
│   │   └── user.ts               # User validation schemas
│   └── hooks/                    # Custom React hooks
│       ├── use-auth.ts           # Authentication hook
│       ├── use-goals.ts          # Goals data hook
│       └── use-local-storage.ts  # Local storage hook
│
├── services/                     # Business logic services layer
│   ├── auth.service.ts          # Authentication service
│   ├── goals.service.ts         # Goals business logic
│   └── api.service.ts           # API client service
│
├── db/                           # Database configuration
│   ├── index.ts                 # Database client initialization
│   ├── schema.ts                # Database schema definitions
│   └── migrations/              # Database migration files
│
├── types/                        # TypeScript type definitions
│   ├── index.ts                 # Main type exports
│   ├── auth.ts                  # Authentication types
│   ├── goals.ts                 # Goals types
│   └── api.ts                   # API response types
│
└── config/                       # Configuration files
    ├── env.ts                   # Environment variables config
    └── site.ts                  # Site configuration
```

**Characteristics:**

- Feature-based component organization
- Separate services layer for business logic
- Validation schemas with Zod
- Custom hooks for reusable logic
- Type definitions centralized
- Environment configuration

---

## 🟠 Large Project Structure (30-100 features)

Designed for complex applications with multiple domains and teams.

```
src/
├── app/                          # Next.js App Router directory
│   ├── (app)/                    # Route group for authenticated app pages
│   │   ├── dashboard/            # Dashboard page route
│   │   ├── goals/                # Goals feature routes
│   │   │   ├── page.tsx          # Goals list page
│   │   │   ├── [id]/            # Dynamic route for individual goal
│   │   │   │   └── page.tsx      # Goal detail page
│   │   │   └── new/              # Create new goal route
│   │   │       └── page.tsx      # New goal form page
│   │   ├── settings/             # Settings routes
│   │   │   ├── profile/          # User profile settings
│   │   │   ├── preferences/      # User preferences
│   │   │   └── security/         # Security settings
│   │   ├── analytics/            # Analytics page route
│   │   └── layout.tsx            # Layout for authenticated routes
│   ├── (auth)/                   # Route group for authentication pages
│   │   ├── login/                # Login page route
│   │   ├── sign-up/              # Sign up page route
│   │   ├── forgot-password/      # Password recovery page
│   │   ├── reset-password/       # Password reset page
│   │   └── layout.tsx            # Layout for auth routes
│   ├── (marketing)/              # Route group for public marketing pages
│   │   ├── page.tsx              # Home/landing page
│   │   ├── about/                # About page
│   │   ├── pricing/              # Pricing page
│   │   └── layout.tsx            # Layout for marketing pages
│   ├── api/                      # API routes directory
│   │   ├── auth/                 # Authentication API endpoints
│   │   ├── goals/                # Goals API endpoints
│   │   │   ├── route.ts          # Goals CRUD operations
│   │   │   └── [id]/            # Dynamic route for goal operations
│   │   │       └── route.ts      # Individual goal API handler
│   │   ├── users/                # Users API endpoints
│   │   │   ├── route.ts          # Users list/create
│   │   │   └── [id]/            # Dynamic route for user operations
│   │   │       └── route.ts      # Individual user API handler
│   │   └── analytics/            # Analytics API endpoints
│   │       └── route.ts          # Analytics data API
│   ├── layout.tsx                # Root layout component
│   └── globals.css               # Global CSS styles
│
├── components/                   # React components directory
│   ├── features/                 # Feature-specific components
│   │   ├── auth/                 # Authentication components
│   │   │   ├── login-form.tsx    # Login form component
│   │   │   ├── signup-form.tsx   # Sign up form component
│   │   │   ├── forgot-password-form.tsx  # Password recovery form
│   │   │   └── reset-password-form.tsx   # Password reset form
│   │   ├── goals/                # Goals feature components
│   │   │   ├── goal-card.tsx     # Goal card display component
│   │   │   ├── goal-list.tsx     # Goals list component
│   │   │   ├── goal-form.tsx     # Goal create/edit form
│   │   │   ├── goal-detail.tsx   # Goal detail view
│   │   │   └── goal-filters.tsx  # Goal filtering component
│   │   ├── dashboard/            # Dashboard components
│   │   │   ├── stats-card.tsx    # Statistics card component
│   │   │   ├── recent-activity.tsx  # Recent activity feed
│   │   │   └── charts/           # Chart components
│   │   │       ├── line-chart.tsx    # Line chart component
│   │   │       └── bar-chart.tsx     # Bar chart component
│   │   └── analytics/            # Analytics components
│   │       ├── analytics-dashboard.tsx  # Analytics dashboard
│   │       └── report-generator.tsx     # Report generation component
│   ├── layout/                   # Layout components
│   │   ├── app/                  # App layout components
│   │   │   ├── sidebar.tsx       # Sidebar navigation
│   │   │   ├── header.tsx        # App header
│   │   │   ├── navigation.tsx   # Main navigation component
│   │   │   └── breadcrumbs.tsx  # Breadcrumb navigation
│   │   ├── auth/                 # Auth layout components
│   │   │   └── auth-container.tsx  # Auth page container
│   │   └── marketing/            # Marketing layout components
│   │       ├── navbar.tsx        # Marketing navbar
│   │       ├── footer.tsx        # Marketing footer
│   │       └── hero-section.tsx  # Hero section component
│   ├── shared/                   # Shared/common components
│   │   ├── loading.tsx           # Loading spinner component
│   │   ├── error-boundary.tsx    # Error boundary component
│   │   ├── toast.tsx             # Toast notification component
│   │   ├── modal.tsx             # Modal component
│   │   ├── confirm-dialog.tsx    # Confirmation dialog
│   │   └── pagination.tsx        # Pagination component
│   └── ui/                       # Reusable UI primitives
│       ├── button.tsx            # Button component
│       ├── input.tsx             # Input component
│       ├── card.tsx              # Card component
│       ├── dialog.tsx            # Dialog/modal component
│       ├── select.tsx            # Select dropdown component
│       ├── table.tsx             # Table component
│       └── tabs.tsx              # Tabs component
│
├── lib/                          # Utility libraries and helpers
│   ├── auth.ts                   # Server-side auth utilities
│   ├── auth-client.ts            # Client-side auth utilities
│   ├── utils.ts                  # General utility functions
│   ├── constants.ts              # Application constants
│   ├── validations/              # Validation schemas (Zod)
│   │   ├── auth.ts               # Auth validation schemas
│   │   ├── goals.ts              # Goals validation schemas
│   │   ├── user.ts               # User validation schemas
│   │   └── analytics.ts          # Analytics validation schemas
│   ├── hooks/                    # Custom React hooks
│   │   ├── use-auth.ts           # Authentication hook
│   │   ├── use-goals.ts          # Goals data hook
│   │   ├── use-local-storage.ts  # Local storage hook
│   │   ├── use-debounce.ts       # Debounce hook
│   │   └── use-media-query.ts    # Media query hook
│   └── helpers/                  # Helper utility functions
│       ├── formatters.ts         # Data formatting utilities
│       ├── validators.ts        # Additional validators
│       └── date-utils.ts         # Date manipulation utilities
│
├── services/                     # Business logic services layer
│   ├── auth.service.ts          # Authentication service
│   ├── goals.service.ts         # Goals business logic
│   ├── users.service.ts         # Users business logic
│   ├── analytics.service.ts     # Analytics business logic
│   ├── api.service.ts           # API client service
│   ├── cache.service.ts         # Caching service
│   └── storage.service.ts       # Storage service
│
├── stores/                       # State management stores (Zustand/Redux)
│   ├── auth-store.ts            # Authentication state store
│   ├── goals-store.ts           # Goals state store
│   ├── ui-store.ts              # UI state store
│   └── analytics-store.ts       # Analytics state store
│
├── db/                           # Database configuration
│   ├── index.ts                 # Database client initialization
│   ├── schema.ts                # Database schema definitions
│   ├── migrations/              # Database migration files
│   └── seeds/                   # Database seed files
│
├── types/                        # TypeScript type definitions
│   ├── index.ts                 # Main type exports
│   ├── auth.ts                  # Authentication types
│   ├── goals.ts                 # Goals types
│   ├── user.ts                  # User types
│   ├── api.ts                   # API response types
│   └── analytics.ts             # Analytics types
│
├── hooks/                        # Top-level custom hooks
│   ├── use-auth.ts              # Authentication hook
│   ├── use-goals.ts             # Goals data hook
│   ├── use-theme.ts             # Theme management hook
│   └── use-analytics.ts         # Analytics hook
│
├── config/                       # Configuration files
│   ├── env.ts                   # Environment variables config
│   ├── site.ts                  # Site configuration
│   └── constants.ts             # Application constants
│
└── styles/                       # Global styles
    ├── globals.css              # Global CSS styles
    └── themes.css               # Theme CSS variables
```

**Characteristics:**

- State management with stores
- Advanced caching strategies
- Helper utilities separated
- Multiple custom hooks
- Comprehensive type system
- Theming support

---

## 🔴 Enterprise Project Structure (100+ features)

For large-scale applications with multiple teams, domains, and complex business logic.

```
src/
├── app/                          # Next.js App Router directory
│   ├── (app)/                    # Route group for authenticated app pages
│   │   ├── dashboard/            # Dashboard page route
│   │   ├── goals/                # Goals feature routes
│   │   │   ├── page.tsx          # Goals list page
│   │   │   ├── [id]/            # Dynamic route for individual goal
│   │   │   │   └── page.tsx      # Goal detail page
│   │   │   ├── new/              # Create new goal route
│   │   │   │   └── page.tsx      # New goal form page
│   │   │   └── templates/        # Goal templates route
│   │   │       └── page.tsx      # Goal templates page
│   │   ├── settings/             # Settings routes
│   │   │   ├── profile/          # User profile settings
│   │   │   ├── preferences/      # User preferences
│   │   │   ├── security/         # Security settings
│   │   │   └── integrations/     # Third-party integrations
│   │   ├── analytics/            # Analytics routes
│   │   │   ├── overview/         # Analytics overview page
│   │   │   ├── reports/          # Reports page
│   │   │   └── exports/          # Data exports page
│   │   ├── teams/                # Teams feature routes
│   │   │   ├── page.tsx          # Teams list page
│   │   │   └── [id]/            # Dynamic route for team
│   │   │       └── page.tsx      # Team detail page
│   │   └── layout.tsx            # Layout for authenticated routes
│   ├── (auth)/                   # Route group for authentication pages
│   │   ├── login/                # Login page route
│   │   ├── sign-up/              # Sign up page route
│   │   ├── forgot-password/      # Password recovery page
│   │   ├── reset-password/       # Password reset page
│   │   ├── verify-email/         # Email verification page
│   │   └── layout.tsx            # Layout for auth routes
│   ├── (marketing)/              # Route group for public marketing pages
│   │   ├── page.tsx              # Home/landing page
│   │   ├── about/                # About page
│   │   ├── pricing/              # Pricing page
│   │   ├── blog/                 # Blog routes
│   │   │   ├── page.tsx          # Blog list page
│   │   │   └── [slug]/          # Dynamic route for blog post
│   │   │       └── page.tsx      # Blog post detail page
│   │   └── layout.tsx            # Layout for marketing pages
│   ├── api/                      # API routes directory
│   │   ├── auth/                 # Authentication API endpoints
│   │   ├── goals/                # Goals API endpoints
│   │   │   ├── route.ts          # Goals CRUD operations
│   │   │   ├── [id]/            # Dynamic route for goal operations
│   │   │   │   └── route.ts      # Individual goal API handler
│   │   │   └── templates/        # Goal templates API
│   │   │       └── route.ts      # Templates API handler
│   │   ├── users/                # Users API endpoints
│   │   │   ├── route.ts          # Users list/create
│   │   │   └── [id]/            # Dynamic route for user operations
│   │   │       └── route.ts      # Individual user API handler
│   │   ├── teams/                # Teams API endpoints
│   │   │   ├── route.ts          # Teams list/create
│   │   │   └── [id]/            # Dynamic route for team operations
│   │   │       └── route.ts      # Individual team API handler
│   │   ├── analytics/            # Analytics API endpoints
│   │   │   ├── route.ts          # Analytics data API
│   │   │   └── export/           # Analytics export API
│   │   │       └── route.ts      # Export data handler
│   │   └── webhooks/             # Webhook endpoints
│   │       └── route.ts          # Webhook handler
│   ├── layout.tsx                # Root layout component
│   └── globals.css               # Global CSS styles
│
├── components/                   # React components directory
│   ├── features/                 # Feature-specific components
│   │   ├── auth/                 # Authentication components
│   │   │   ├── login-form.tsx    # Login form component
│   │   │   ├── signup-form.tsx   # Sign up form component
│   │   │   ├── forgot-password-form.tsx  # Password recovery form
│   │   │   ├── reset-password-form.tsx   # Password reset form
│   │   │   └── verify-email-form.tsx     # Email verification form
│   │   ├── goals/                # Goals feature components
│   │   │   ├── goal-card.tsx     # Goal card display component
│   │   │   ├── goal-list.tsx     # Goals list component
│   │   │   ├── goal-form.tsx     # Goal create/edit form
│   │   │   ├── goal-detail.tsx   # Goal detail view
│   │   │   ├── goal-filters.tsx  # Goal filtering component
│   │   │   ├── goal-templates/    # Goal template components
│   │   │   │   ├── template-card.tsx      # Template card
│   │   │   │   └── template-selector.tsx   # Template selector
│   │   │   └── goal-analytics/    # Goal analytics components
│   │   │       └── goal-progress.tsx      # Goal progress tracker
│   │   ├── dashboard/            # Dashboard components
│   │   │   ├── stats-card.tsx    # Statistics card component
│   │   │   ├── recent-activity.tsx  # Recent activity feed
│   │   │   ├── charts/           # Chart components
│   │   │   │   ├── line-chart.tsx    # Line chart component
│   │   │   │   ├── bar-chart.tsx     # Bar chart component
│   │   │   │   └── pie-chart.tsx     # Pie chart component
│   │   │   └── widgets/          # Dashboard widgets
│   │   │       ├── quick-actions.tsx    # Quick actions widget
│   │   │       └── notifications.tsx     # Notifications widget
│   │   ├── analytics/            # Analytics components
│   │   │   ├── analytics-dashboard.tsx  # Analytics dashboard
│   │   │   ├── report-generator.tsx     # Report generation component
│   │   │   ├── data-export.tsx          # Data export component
│   │   │   └── filters/                 # Analytics filter components
│   │   │       ├── date-range-picker.tsx # Date range picker
│   │   │       └── metric-selector.tsx   # Metric selector
│   │   └── teams/                # Teams feature components
│   │       ├── team-card.tsx     # Team card component
│   │       ├── team-list.tsx     # Teams list component
│   │       ├── team-form.tsx    # Team create/edit form
│   │       └── team-members/     # Team member components
│   │           ├── member-list.tsx    # Member list
│   │           └── member-invite.tsx  # Member invitation
│   ├── layout/                   # Layout components
│   │   ├── app/                  # App layout components
│   │   │   ├── sidebar/          # Sidebar components
│   │   │   │   ├── sidebar.tsx       # Main sidebar
│   │   │   │   ├── sidebar-nav.tsx   # Sidebar navigation
│   │   │   │   └── sidebar-footer.tsx # Sidebar footer
│   │   │   ├── header/            # Header components
│   │   │   │   ├── header.tsx         # Main header
│   │   │   │   ├── user-menu.tsx     # User menu dropdown
│   │   │   │   └── notifications.tsx  # Notifications component
│   │   │   ├── navigation/       # Navigation components
│   │   │   │   └── main-nav.tsx      # Main navigation
│   │   │   └── breadcrumbs.tsx   # Breadcrumb navigation
│   │   ├── auth/                 # Auth layout components
│   │   │   └── auth-container.tsx  # Auth page container
│   │   └── marketing/            # Marketing layout components
│   │       ├── navbar.tsx        # Marketing navbar
│   │       ├── footer.tsx        # Marketing footer
│   │       └── hero-section.tsx  # Hero section component
│   ├── shared/                   # Shared/common components
│   │   ├── loading/              # Loading components
│   │   │   ├── loading.tsx       # Loading spinner
│   │   │   └── skeleton.tsx     # Skeleton loader
│   │   ├── error-boundary.tsx    # Error boundary component
│   │   ├── toast/                # Toast notification components
│   │   │   ├── toast.tsx         # Toast component
│   │   │   └── toast-provider.tsx # Toast provider
│   │   ├── modal/                # Modal components
│   │   │   ├── modal.tsx         # Modal component
│   │   │   └── confirm-dialog.tsx # Confirmation dialog
│   │   ├── pagination.tsx        # Pagination component
│   │   └── empty-state.tsx       # Empty state component
│   └── ui/                       # Reusable UI primitives
│       ├── button.tsx            # Button component
│       ├── input.tsx             # Input component
│       ├── card.tsx              # Card component
│       ├── dialog.tsx            # Dialog/modal component
│       ├── select.tsx            # Select dropdown component
│       ├── table.tsx             # Table component
│       ├── tabs.tsx              # Tabs component
│       ├── dropdown-menu.tsx     # Dropdown menu component
│       ├── tooltip.tsx           # Tooltip component
│       └── popover.tsx           # Popover component
│
├── lib/                          # Utility libraries and helpers
│   ├── auth.ts                   # Server-side auth utilities
│   ├── auth-client.ts            # Client-side auth utilities
│   ├── utils.ts                  # General utility functions
│   ├── constants.ts              # Application constants
│   ├── validations/              # Validation schemas (Zod)
│   │   ├── auth.ts               # Auth validation schemas
│   │   ├── goals.ts              # Goals validation schemas
│   │   ├── user.ts               # User validation schemas
│   │   ├── teams.ts              # Teams validation schemas
│   │   └── analytics.ts          # Analytics validation schemas
│   ├── hooks/                    # Custom React hooks
│   │   ├── use-auth.ts           # Authentication hook
│   │   ├── use-goals.ts          # Goals data hook
│   │   ├── use-local-storage.ts  # Local storage hook
│   │   ├── use-debounce.ts       # Debounce hook
│   │   ├── use-media-query.ts    # Media query hook
│   │   ├── use-intersection.ts  # Intersection observer hook
│   │   └── use-keyboard-shortcut.ts # Keyboard shortcut hook
│   ├── helpers/                  # Helper utility functions
│   │   ├── formatters.ts         # Data formatting utilities
│   │   ├── validators.ts         # Additional validators
│   │   ├── date-utils.ts         # Date manipulation utilities
│   │   └── string-utils.ts       # String manipulation utilities
│   └── middleware/               # Request middleware utilities
│       ├── rate-limiter.ts       # Rate limiting middleware
│       └── request-validator.ts  # Request validation middleware
│
├── services/                     # Business logic services layer (domain-organized)
│   ├── auth/                     # Authentication services
│   │   ├── auth.service.ts      # Authentication service
│   │   └── session.service.ts   # Session management service
│   ├── goals/                    # Goals services
│   │   ├── goals.service.ts     # Goals business logic
│   │   └── templates.service.ts # Goal templates service
│   ├── users/                    # Users services
│   │   └── users.service.ts     # Users business logic
│   ├── teams/                    # Teams services
│   │   └── teams.service.ts     # Teams business logic
│   ├── analytics/                # Analytics services
│   │   ├── analytics.service.ts # Analytics business logic
│   │   └── reports.service.ts   # Reports generation service
│   ├── api/                      # API services
│   │   ├── api.service.ts       # Main API client
│   │   ├── http-client.ts       # HTTP client wrapper
│   │   └── error-handler.ts     # Error handling service
│   ├── cache/                    # Caching services
│   │   ├── cache.service.ts     # Cache service
│   │   └── cache-strategies.ts  # Cache strategy implementations
│   ├── storage/                  # Storage services
│   │   ├── storage.service.ts   # Storage service
│   │   └── file-upload.service.ts # File upload service
│   └── notifications/            # Notification services
│       └── notification.service.ts # Notification service
│
├── stores/                       # State management stores (domain-organized)
│   ├── auth/                     # Authentication stores
│   │   ├── auth-store.ts        # Authentication state store
│   │   └── session-store.ts     # Session state store
│   ├── goals/                    # Goals stores
│   │   ├── goals-store.ts       # Goals state store
│   │   └── templates-store.ts   # Templates state store
│   ├── ui/                       # UI stores
│   │   ├── ui-store.ts          # General UI state
│   │   ├── theme-store.ts       # Theme state store
│   │   └── sidebar-store.ts     # Sidebar state store
│   └── analytics/                # Analytics stores
│       └── analytics-store.ts   # Analytics state store
│
├── db/                           # Database configuration
│   ├── index.ts                 # Database client initialization
│   ├── schema/                   # Modular schema definitions
│   │   ├── auth.ts              # Authentication schema
│   │   ├── goals.ts             # Goals schema
│   │   ├── users.ts             # Users schema
│   │   ├── teams.ts             # Teams schema
│   │   └── analytics.ts         # Analytics schema
│   ├── migrations/              # Database migration files
│   ├── seeds/                   # Database seed files
│   └── queries/                 # Database query functions
│       ├── goals.queries.ts     # Goals queries
│       └── users.queries.ts     # Users queries
│
├── types/                        # TypeScript type definitions
│   ├── index.ts                 # Main type exports
│   ├── auth.ts                  # Authentication types
│   ├── goals.ts                 # Goals types
│   ├── user.ts                  # User types
│   ├── teams.ts                 # Teams types
│   ├── api.ts                   # API response types
│   ├── analytics.ts             # Analytics types
│   └── common.ts                # Common/shared types
│
├── hooks/                        # Top-level custom hooks
│   ├── use-auth.ts              # Authentication hook
│   ├── use-goals.ts             # Goals data hook
│   ├── use-theme.ts             # Theme management hook
│   ├── use-analytics.ts         # Analytics hook
│   └── use-teams.ts             # Teams hook
│
├── config/                       # Configuration files
│   ├── env.ts                   # Environment variables config
│   ├── site.ts                  # Site configuration
│   ├── constants.ts             # Application constants
│   └── feature-flags.ts         # Feature flags configuration
│
├── middleware/                   # Next.js middleware
│   ├── auth.middleware.ts       # Authentication middleware
│   ├── rate-limit.middleware.ts # Rate limiting middleware
│   └── logging.middleware.ts    # Logging middleware
│
├── styles/                       # Global styles
│   ├── globals.css              # Global CSS styles
│   ├── themes/                  # Theme styles
│   │   ├── light.css            # Light theme
│   │   └── dark.css             # Dark theme
│   └── components/              # Component-specific styles
│       └── custom-components.css # Custom component styles
│
└── tests/                        # Test files
    ├── unit/                     # Unit tests
    ├── integration/              # Integration tests
    └── e2e/                      # End-to-end tests
```

**Characteristics:**

- Domain-driven organization
- Service layer organized by domain
- Separate query layer for database
- Middleware for cross-cutting concerns
- Feature flags for gradual rollouts
- Comprehensive testing structure
- Advanced caching strategies
- Modular schema organization

---

## Choosing the Right Structure

- **Small**: Start here for new projects. Easy to refactor as you grow.
- **Medium**: Use when you have 10+ features and need better organization.
- **Large**: Adopt when working with multiple teams or complex domains.
- **Enterprise**: For applications with 100+ features, multiple teams, and complex business requirements.

**Migration Path**: You can start with a smaller structure and gradually evolve to a larger one as your project grows.
