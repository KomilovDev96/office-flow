# Frontend Monorepo Architecture — Geo Attendance SaaS

# Основная идея архитектуры

Frontend должен быть разделён на:

```text
apps/
 ├── admin-dashboard/
 └── employee-mini-app/
```

---

# Почему нужно разделять приложения

## Admin Dashboard

Используется для:

- HR management
- analytics
- attendance tables
- reports
- office settings

---

## Employee Mini App

Используется для:

- GPS tracking
- check-in
- attendance status
- employee profile
- Telegram integration

---

# Почему НЕ делать всё в одном приложении

Если сделать:

```text
/admin
/employee
```

в одном Next.js app:

---

# Проблемы

❌ огромный проект  
❌ сложная структура  
❌ смешивание UI логики  
❌ разные UX в одном app  
❌ сложнее deployment  
❌ сложнее поддержка  

---

# Самый правильный подход

## Separate Apps + Shared Packages

---

# Recommended Architecture

```text
geo-attendance/

 ├── apps/
 │
 │   ├── admin-dashboard/
 │   └── employee-mini-app/
 │
 ├── packages/
 │
 │   ├── shared-api/
 │   ├── shared-types/
 │   ├── shared-utils/
 │   ├── shared-config/
 │   └── shared-ui/
 │
 ├── backend/
 │
 │   ├── api/
 │   └── workers/
 │
 ├── docker/
 │
 └── docs/
```

---

# Apps Folder

# admin-dashboard

```text
apps/admin-dashboard
```

---

# Technologies

```text
Next.js
TypeScript
Ant Design
Tailwind CSS
React Query
Zustand
Socket.IO
```

---

# Назначение

- HR dashboard
- employee management
- attendance monitoring
- analytics
- reports
- office settings

---

# employee-mini-app

```text
apps/employee-mini-app
```

---

# Technologies

```text
Next.js
TypeScript
shadcn/ui
Tailwind CSS
Telegram SDK
React Query
Zustand
```

---

# Назначение

- GPS attendance
- check-in
- check-out
- employee status
- Telegram integration

---

# Packages Folder

Очень важная часть architecture.

---

# shared-types

```text
packages/shared-types
```

---

# Что хранить

```ts
Employee types
Attendance types
Office types
Enums
Interfaces
DTOs
```

---

# Пример

```ts
Employee
Attendance
Office
Role
AttendanceStatus
```

---

# shared-api

```text
packages/shared-api
```

---

# Что хранить

```ts
axios instance
API services
auth requests
attendance requests
employee requests
```

---

# Пример

```ts
authApi
attendanceApi
employeeApi
officeApi
```

---

# shared-utils

```text
packages/shared-utils
```

---

# Что хранить

```ts
date formatters
distance calculations
validators
helpers
constants
```

---

# shared-config

```text
packages/shared-config
```

---

# Что хранить

```ts
env variables
routes
permissions
theme config
app constants
```

---

# shared-ui

```text
packages/shared-ui
```

---

# Что хранить

Общие UI элементы:

- loaders
- typography
- buttons
- modals
- empty states

---

# Важно

## НЕ смешивать:

```text
Ant Design
+
shadcn/ui
```

в одном UI layer.

---

# Почему

Потому что:

- admin UI
- mini app UI

имеют разные design systems.

---

# Backend Architecture

```text
backend/
 ├── api/
 └── workers/
```

---

# backend/api

Основной NestJS backend.

---

# backend/workers

BullMQ workers.

---

# Workers выполняют

- attendance processing
- GPS validation
- notifications
- reports
- analytics

---

# Deployment Architecture

## Admin Dashboard

```text
admin.company.com
```

---

# Employee Mini App

```text
mini.company.com
```

---

# Backend API

```text
api.company.com
```

---

# Почему subdomains лучше

✅ cleaner architecture  
✅ easier scaling  
✅ independent deployments  
✅ better security  
✅ easier CI/CD  

---

# Telegram Integration

## Telegram Bot открывает:

```text
mini.company.com
```

---

# Authentication Flow

## Employee

```text
Telegram
   ↓
Mini App
   ↓
Telegram SDK
   ↓
JWT Token
```

---

# Admin

```text
Email/Password
or
Telegram Login
```

---

# Recommended Monorepo Tools

# pnpm

Очень рекомендую.

---

# Почему pnpm

✅ быстрый  
✅ меньше disk usage  
✅ идеально для monorepo  
✅ хороший workspace support  

---

# Turborepo

Использовать для:

- builds
- caching
- shared packages
- CI/CD optimization

---

# Почему Turborepo

✅ fast builds  
✅ scalable monorepo  
✅ build caching  
✅ production-ready  

---

# Final Frontend Stack

# Admin Dashboard

```text
Next.js
TypeScript
Ant Design
Tailwind CSS
React Query
Zustand
Socket.IO
```

---

# Employee Mini App

```text
Next.js
TypeScript
shadcn/ui
Tailwind CSS
Telegram SDK
React Query
Zustand
```

---

# Final Frontend Structure

```text
apps/
 ├── admin-dashboard/
 └── employee-mini-app/

packages/
 ├── shared-api/
 ├── shared-types/
 ├── shared-utils/
 ├── shared-config/
 └── shared-ui/
```

---

# Что получится

✅ scalable architecture  
✅ enterprise SaaS structure  
✅ clean separation  
✅ easy maintenance  
✅ independent deployments  
✅ reusable packages  
✅ production-ready monorepo  

---

# Итог

Это enterprise-level frontend architecture для:

- HR systems
- SaaS platforms
- Telegram Mini Apps
- Realtime attendance systems

Самый правильный подход:

✅ Admin отдельно  
✅ Mini App отдельно  
✅ Shared packages  
✅ Monorepo architecture  
✅ Turborepo + pnpm  