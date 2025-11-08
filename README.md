# Next.js Project Structures by Scale

This document presents different project structures for Next.js applications, organized from small to large-scale projects.

---

## 🟢 Small Project Structure (< 10 features)

Ideal for MVPs, prototypes, or simple applications with limited functionality.

```
src/
├── app/
│   ├── (app)/
│   │   ├── dashboard/
│   │   │   └── page.tsx
│   │   ├── settings/
│   │   │   └── page.tsx
│   │   └── layout.tsx
│   ├── (auth)/
│   │   ├── login/
│   │   │   └── page.tsx
│   │   ├── sign-up/
│   │   │   └── page.tsx
│   │   └── layout.tsx
│   ├── api/
│   │   └── auth/
│   │       └── [...all]/
│   │           └── route.ts
│   ├── layout.tsx
│   └── globals.css
│
├── components/
│   ├── features/
│   │   ├── auth/
│   │   │   ├── login-form.tsx
│   │   │   └── signup-form.tsx
│   │   └── dashboard/
│   │       └── stats-card.tsx
│   └── ui/
│       ├── button.tsx
│       ├── input.tsx
│       └── card.tsx
│
├── lib/
│   ├── auth.ts
│   ├── auth-client.ts
│   ├── utils.ts
│   └── db.ts
│
└── db/
    ├── index.ts
    └── schema.ts
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
├── app/
│   ├── (app)/
│   │   ├── dashboard/
│   │   ├── goals/
│   │   │   ├── page.tsx
│   │   │   └── [id]/
│   │   │       └── page.tsx
│   │   ├── settings/
│   │   └── layout.tsx
│   ├── (auth)/
│   │   ├── login/
│   │   ├── sign-up/
│   │   ├── forgot-password/
│   │   └── layout.tsx
│   ├── (marketing)/
│   │   ├── page.tsx
│   │   └── layout.tsx
│   ├── api/
│   │   ├── auth/
│   │   ├── goals/
│   │   │   ├── route.ts
│   │   │   └── [id]/
│   │   │       └── route.ts
│   │   └── users/
│   │       └── route.ts
│   ├── layout.tsx
│   └── globals.css
│
├── components/
│   ├── features/
│   │   ├── auth/
│   │   │   ├── login-form.tsx
│   │   │   ├── signup-form.tsx
│   │   │   └── forgot-password-form.tsx
│   │   ├── goals/
│   │   │   ├── goal-card.tsx
│   │   │   ├── goal-list.tsx
│   │   │   └── goal-form.tsx
│   │   └── dashboard/
│   │       ├── stats-card.tsx
│   │       └── recent-activity.tsx
│   ├── layout/
│   │   ├── app/
│   │   │   ├── sidebar.tsx
│   │   │   └── header.tsx
│   │   ├── auth/
│   │   │   └── auth-container.tsx
│   │   └── marketing/
│   │       ├── navbar.tsx
│   │       └── footer.tsx
│   ├── shared/
│   │   ├── loading.tsx
│   │   ├── error-boundary.tsx
│   │   └── toast.tsx
│   └── ui/
│       ├── button.tsx
│       ├── input.tsx
│       ├── card.tsx
│       └── dialog.tsx
│
├── lib/
│   ├── auth.ts
│   ├── auth-client.ts
│   ├── utils.ts
│   ├── constants.ts
│   ├── validations/
│   │   ├── auth.ts
│   │   ├── goals.ts
│   │   └── user.ts
│   └── hooks/
│       ├── use-auth.ts
│       ├── use-goals.ts
│       └── use-local-storage.ts
│
├── services/
│   ├── auth.service.ts
│   ├── goals.service.ts
│   └── api.service.ts
│
├── db/
│   ├── index.ts
│   ├── schema.ts
│   └── migrations/
│
├── types/
│   ├── index.ts
│   ├── auth.ts
│   ├── goals.ts
│   └── api.ts
│
└── config/
    ├── env.ts
    └── site.ts
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
├── app/
│   ├── (app)/
│   │   ├── dashboard/
│   │   ├── goals/
│   │   │   ├── page.tsx
│   │   │   ├── [id]/
│   │   │   │   └── page.tsx
│   │   │   └── new/
│   │   │       └── page.tsx
│   │   ├── settings/
│   │   │   ├── profile/
│   │   │   ├── preferences/
│   │   │   └── security/
│   │   ├── analytics/
│   │   └── layout.tsx
│   ├── (auth)/
│   │   ├── login/
│   │   ├── sign-up/
│   │   ├── forgot-password/
│   │   ├── reset-password/
│   │   └── layout.tsx
│   ├── (marketing)/
│   │   ├── page.tsx
│   │   ├── about/
│   │   ├── pricing/
│   │   └── layout.tsx
│   ├── api/
│   │   ├── auth/
│   │   ├── goals/
│   │   │   ├── route.ts
│   │   │   └── [id]/
│   │   │       └── route.ts
│   │   ├── users/
│   │   │   ├── route.ts
│   │   │   └── [id]/
│   │   │       └── route.ts
│   │   └── analytics/
│   │       └── route.ts
│   ├── layout.tsx
│   └── globals.css
│
├── components/
│   ├── features/
│   │   ├── auth/
│   │   │   ├── login-form.tsx
│   │   │   ├── signup-form.tsx
│   │   │   ├── forgot-password-form.tsx
│   │   │   └── reset-password-form.tsx
│   │   ├── goals/
│   │   │   ├── goal-card.tsx
│   │   │   ├── goal-list.tsx
│   │   │   ├── goal-form.tsx
│   │   │   ├── goal-detail.tsx
│   │   │   └── goal-filters.tsx
│   │   ├── dashboard/
│   │   │   ├── stats-card.tsx
│   │   │   ├── recent-activity.tsx
│   │   │   └── charts/
│   │   │       ├── line-chart.tsx
│   │   │       └── bar-chart.tsx
│   │   └── analytics/
│   │       ├── analytics-dashboard.tsx
│   │       └── report-generator.tsx
│   ├── layout/
│   │   ├── app/
│   │   │   ├── sidebar.tsx
│   │   │   ├── header.tsx
│   │   │   ├── navigation.tsx
│   │   │   └── breadcrumbs.tsx
│   │   ├── auth/
│   │   │   └── auth-container.tsx
│   │   └── marketing/
│   │       ├── navbar.tsx
│   │       ├── footer.tsx
│   │       └── hero-section.tsx
│   ├── shared/
│   │   ├── loading.tsx
│   │   ├── error-boundary.tsx
│   │   ├── toast.tsx
│   │   ├── modal.tsx
│   │   ├── confirm-dialog.tsx
│   │   └── pagination.tsx
│   └── ui/
│       ├── button.tsx
│       ├── input.tsx
│       ├── card.tsx
│       ├── dialog.tsx
│       ├── select.tsx
│       ├── table.tsx
│       └── tabs.tsx
│
├── lib/
│   ├── auth.ts
│   ├── auth-client.ts
│   ├── utils.ts
│   ├── constants.ts
│   ├── validations/
│   │   ├── auth.ts
│   │   ├── goals.ts
│   │   ├── user.ts
│   │   └── analytics.ts
│   ├── hooks/
│   │   ├── use-auth.ts
│   │   ├── use-goals.ts
│   │   ├── use-local-storage.ts
│   │   ├── use-debounce.ts
│   │   └── use-media-query.ts
│   └── helpers/
│       ├── formatters.ts
│       ├── validators.ts
│       └── date-utils.ts
│
├── services/
│   ├── auth.service.ts
│   ├── goals.service.ts
│   ├── users.service.ts
│   ├── analytics.service.ts
│   ├── api.service.ts
│   ├── cache.service.ts
│   └── storage.service.ts
│
├── stores/
│   ├── auth-store.ts
│   ├── goals-store.ts
│   ├── ui-store.ts
│   └── analytics-store.ts
│
├── db/
│   ├── index.ts
│   ├── schema.ts
│   ├── migrations/
│   └── seeds/
│
├── types/
│   ├── index.ts
│   ├── auth.ts
│   ├── goals.ts
│   ├── user.ts
│   ├── api.ts
│   └── analytics.ts
│
├── hooks/
│   ├── use-auth.ts
│   ├── use-goals.ts
│   ├── use-theme.ts
│   └── use-analytics.ts
│
├── config/
│   ├── env.ts
│   ├── site.ts
│   └── constants.ts
│
└── styles/
    ├── globals.css
    └── themes.css
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
├── app/
│   ├── (app)/
│   │   ├── dashboard/
│   │   ├── goals/
│   │   │   ├── page.tsx
│   │   │   ├── [id]/
│   │   │   │   └── page.tsx
│   │   │   ├── new/
│   │   │   │   └── page.tsx
│   │   │   └── templates/
│   │   │       └── page.tsx
│   │   ├── settings/
│   │   │   ├── profile/
│   │   │   ├── preferences/
│   │   │   ├── security/
│   │   │   └── integrations/
│   │   ├── analytics/
│   │   │   ├── overview/
│   │   │   ├── reports/
│   │   │   └── exports/
│   │   ├── teams/
│   │   │   ├── page.tsx
│   │   │   └── [id]/
│   │   │       └── page.tsx
│   │   └── layout.tsx
│   ├── (auth)/
│   │   ├── login/
│   │   ├── sign-up/
│   │   ├── forgot-password/
│   │   ├── reset-password/
│   │   ├── verify-email/
│   │   └── layout.tsx
│   ├── (marketing)/
│   │   ├── page.tsx
│   │   ├── about/
│   │   ├── pricing/
│   │   ├── blog/
│   │   │   ├── page.tsx
│   │   │   └── [slug]/
│   │   │       └── page.tsx
│   │   └── layout.tsx
│   ├── api/
│   │   ├── auth/
│   │   ├── goals/
│   │   │   ├── route.ts
│   │   │   ├── [id]/
│   │   │   │   └── route.ts
│   │   │   └── templates/
│   │   │       └── route.ts
│   │   ├── users/
│   │   │   ├── route.ts
│   │   │   └── [id]/
│   │   │       └── route.ts
│   │   ├── teams/
│   │   │   ├── route.ts
│   │   │   └── [id]/
│   │   │       └── route.ts
│   │   ├── analytics/
│   │   │   ├── route.ts
│   │   │   └── export/
│   │   │       └── route.ts
│   │   └── webhooks/
│   │       └── route.ts
│   ├── layout.tsx
│   └── globals.css
│
├── components/
│   ├── features/
│   │   ├── auth/
│   │   │   ├── login-form.tsx
│   │   │   ├── signup-form.tsx
│   │   │   ├── forgot-password-form.tsx
│   │   │   ├── reset-password-form.tsx
│   │   │   └── verify-email-form.tsx
│   │   ├── goals/
│   │   │   ├── goal-card.tsx
│   │   │   ├── goal-list.tsx
│   │   │   ├── goal-form.tsx
│   │   │   ├── goal-detail.tsx
│   │   │   ├── goal-filters.tsx
│   │   │   ├── goal-templates/
│   │   │   │   ├── template-card.tsx
│   │   │   │   └── template-selector.tsx
│   │   │   └── goal-analytics/
│   │   │       └── goal-progress.tsx
│   │   ├── dashboard/
│   │   │   ├── stats-card.tsx
│   │   │   ├── recent-activity.tsx
│   │   │   ├── charts/
│   │   │   │   ├── line-chart.tsx
│   │   │   │   ├── bar-chart.tsx
│   │   │   │   └── pie-chart.tsx
│   │   │   └── widgets/
│   │   │       ├── quick-actions.tsx
│   │   │       └── notifications.tsx
│   │   ├── analytics/
│   │   │   ├── analytics-dashboard.tsx
│   │   │   ├── report-generator.tsx
│   │   │   ├── data-export.tsx
│   │   │   └── filters/
│   │   │       ├── date-range-picker.tsx
│   │   │       └── metric-selector.tsx
│   │   └── teams/
│   │       ├── team-card.tsx
│   │       ├── team-list.tsx
│   │       ├── team-form.tsx
│   │       └── team-members/
│   │           ├── member-list.tsx
│   │           └── member-invite.tsx
│   ├── layout/
│   │   ├── app/
│   │   │   ├── sidebar/
│   │   │   │   ├── sidebar.tsx
│   │   │   │   ├── sidebar-nav.tsx
│   │   │   │   └── sidebar-footer.tsx
│   │   │   ├── header/
│   │   │   │   ├── header.tsx
│   │   │   │   ├── user-menu.tsx
│   │   │   │   └── notifications.tsx
│   │   │   ├── navigation/
│   │   │   │   └── main-nav.tsx
│   │   │   └── breadcrumbs.tsx
│   │   ├── auth/
│   │   │   └── auth-container.tsx
│   │   └── marketing/
│   │       ├── navbar.tsx
│   │       ├── footer.tsx
│   │       └── hero-section.tsx
│   ├── shared/
│   │   ├── loading/
│   │   │   ├── loading.tsx
│   │   │   └── skeleton.tsx
│   │   ├── error-boundary.tsx
│   │   ├── toast/
│   │   │   ├── toast.tsx
│   │   │   └── toast-provider.tsx
│   │   ├── modal/
│   │   │   ├── modal.tsx
│   │   │   └── confirm-dialog.tsx
│   │   ├── pagination.tsx
│   │   └── empty-state.tsx
│   └── ui/
│       ├── button.tsx
│       ├── input.tsx
│       ├── card.tsx
│       ├── dialog.tsx
│       ├── select.tsx
│       ├── table.tsx
│       ├── tabs.tsx
│       ├── dropdown-menu.tsx
│       ├── tooltip.tsx
│       └── popover.tsx
│
├── lib/
│   ├── auth.ts
│   ├── auth-client.ts
│   ├── utils.ts
│   ├── constants.ts
│   ├── validations/
│   │   ├── auth.ts
│   │   ├── goals.ts
│   │   ├── user.ts
│   │   ├── teams.ts
│   │   └── analytics.ts
│   ├── hooks/
│   │   ├── use-auth.ts
│   │   ├── use-goals.ts
│   │   ├── use-local-storage.ts
│   │   ├── use-debounce.ts
│   │   ├── use-media-query.ts
│   │   ├── use-intersection.ts
│   │   └── use-keyboard-shortcut.ts
│   ├── helpers/
│   │   ├── formatters.ts
│   │   ├── validators.ts
│   │   ├── date-utils.ts
│   │   └── string-utils.ts
│   └── middleware/
│       ├── rate-limiter.ts
│       └── request-validator.ts
│
├── services/
│   ├── auth/
│   │   ├── auth.service.ts
│   │   └── session.service.ts
│   ├── goals/
│   │   ├── goals.service.ts
│   │   └── templates.service.ts
│   ├── users/
│   │   └── users.service.ts
│   ├── teams/
│   │   └── teams.service.ts
│   ├── analytics/
│   │   ├── analytics.service.ts
│   │   └── reports.service.ts
│   ├── api/
│   │   ├── api.service.ts
│   │   ├── http-client.ts
│   │   └── error-handler.ts
│   ├── cache/
│   │   ├── cache.service.ts
│   │   └── cache-strategies.ts
│   ├── storage/
│   │   ├── storage.service.ts
│   │   └── file-upload.service.ts
│   └── notifications/
│       └── notification.service.ts
│
├── stores/
│   ├── auth/
│   │   ├── auth-store.ts
│   │   └── session-store.ts
│   ├── goals/
│   │   ├── goals-store.ts
│   │   └── templates-store.ts
│   ├── ui/
│   │   ├── ui-store.ts
│   │   ├── theme-store.ts
│   │   └── sidebar-store.ts
│   └── analytics/
│       └── analytics-store.ts
│
├── db/
│   ├── index.ts
│   ├── schema/
│   │   ├── auth.ts
│   │   ├── goals.ts
│   │   ├── users.ts
│   │   ├── teams.ts
│   │   └── analytics.ts
│   ├── migrations/
│   ├── seeds/
│   └── queries/
│       ├── goals.queries.ts
│       └── users.queries.ts
│
├── types/
│   ├── index.ts
│   ├── auth.ts
│   ├── goals.ts
│   ├── user.ts
│   ├── teams.ts
│   ├── api.ts
│   ├── analytics.ts
│   └── common.ts
│
├── hooks/
│   ├── use-auth.ts
│   ├── use-goals.ts
│   ├── use-theme.ts
│   ├── use-analytics.ts
│   └── use-teams.ts
│
├── config/
│   ├── env.ts
│   ├── site.ts
│   ├── constants.ts
│   └── feature-flags.ts
│
├── middleware/
│   ├── auth.middleware.ts
│   ├── rate-limit.middleware.ts
│   └── logging.middleware.ts
│
├── styles/
│   ├── globals.css
│   ├── themes/
│   │   ├── light.css
│   │   └── dark.css
│   └── components/
│       └── custom-components.css
│
└── tests/
    ├── unit/
    ├── integration/
    └── e2e/
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
