# Backend Architecture — Geo Attendance Startup

## Основной Backend Stack

| Категория | Технология |
|---|---|
| Backend Framework | NestJS |
| Язык | TypeScript |
| Database | PostgreSQL |
| Geo Database | PostGIS |
| ORM | Prisma ORM |
| Cache | Redis |
| Queue System | BullMQ |
| Telegram Integration | Telegraf.js |
| Realtime | Socket.IO |
| Validation | class-validator |
| Documentation | Swagger |
| Deployment | Docker |

---

# Почему NestJS

NestJS идеально подходит для:

- SaaS платформ
- HR систем
- Attendance систем
- Realtime приложений
- Enterprise backend архитектуры

---

# Преимущества NestJS

✅ Чистая архитектура  
✅ TypeScript-first  
✅ Модульная система  
✅ Хороший scalability  
✅ Подходит для больших проектов  
✅ Отлично работает с PostgreSQL и Redis  

---

# Почему НЕ Express

| Express | NestJS |
|---|---|
| Хаос на больших проектах | Структурированный backend |
| Нет архитектуры | Enterprise-ready |
| Много boilerplate | Clean modules |
| Сложно масштабировать | Легко масштабируется |

---

# Основная Архитектура

```text
Telegram Bot
      ↓
Telegram Mini App
      ↓
NGINX
      ↓
NestJS API
      ↓
Redis
      ↓
BullMQ Workers
      ↓
PostgreSQL + PostGIS