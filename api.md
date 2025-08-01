---
layout: default
title: API Документация
description: REST API справочник для Telegram Bot Manager
permalink: /api/
---

# 🔌 API Документация

REST API для интеграции с Telegram Bot Manager. Все API эндпоинты используют JSON для обмена данными и поддерживают стандартные HTTP методы.

---

## 🔐 Аутентификация

### Способы аутентификации

API поддерживает несколько способов аутентификации:

| Способ | Описание | Использование |
|--------|----------|---------------|
| **Laravel Sanctum** | Token-based аутентификация | Веб-приложения, SPA |
| **Session Auth** | Сессионная аутентификация | Встроенные формы |
| **Webhook Signature** | Подпись для webhook'ов | Telegram webhook'и |

### Получение токена

```bash
# Создание токена через Artisan
php artisan sanctum:token --user=1 --name="API Token"

# Или через API
POST /api/auth/login
Content-Type: application/json

{
  "email": "user@example.com",
  "password": "password"
}
```

**Ответ:**
```json
{
  "success": true,
  "data": {
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9...",
    "user": {
      "id": 1,
      "name": "John Doe",
      "email": "user@example.com"
    }
  }
}
```

### Использование токена

```bash
# В заголовке Authorization
curl -H "Authorization: Bearer YOUR_TOKEN" \
     -H "Content-Type: application/json" \
     https://your-domain.com/api/endpoint
```

---

## 📊 Базовая информация

### Базовый URL

```
https://your-domain.com/api
```

### Формат ответов

Все API ответы следуют единому формату:

```json
{
  "success": true,
  "data": { /* данные ответа */ },
  "message": "Успешно",
  "errors": null,
  "meta": {
    "timestamp": "2025-08-01T12:00:00Z",
    "version": "1.0"
  }
}
```

### HTTP статус коды

| Код | Описание |
|-----|----------|
| `200` | Успешный запрос |
| `201` | Ресурс создан |
| `400` | Неверный запрос |
| `401` | Не авторизован |
| `403` | Доступ запрещен |
| `404` | Ресурс не найден |
| `422` | Ошибка валидации |
| `500` | Внутренняя ошибка сервера |

---

## 🤖 Webhook API

### Обработка Telegram webhook

```
POST /api/webhook/telegram
```

**Заголовки:**
```
Content-Type: application/json
X-Telegram-Bot-Api-Secret-Token: SECRET_TOKEN
```

**Тело запроса:**
```json
{
  "update_id": 123456789,
  "message": {
    "message_id": 456,
    "from": {
      "id": 123456789,
      "is_bot": false,
      "first_name": "John",
      "username": "johndoe"
    },
    "chat": {
      "id": 123456789,
      "first_name": "John",
      "username": "johndoe",
      "type": "private"
    },
    "date": 1627804800,
    "text": "/start"
  }
}
```

**Ответ:**
```json
{
  "success": true,
  "data": {
    "processed": true,
    "conversation_id": "conv_123",
    "actions_executed": 3
  }
}
```

### Установка webhook

```
POST /api/webhook/set
```

**Параметры:**
```json
{
  "bot_token": "1234567890:AABBCCDDEEFFGGHHIIJJKKLLMMNNOOPPq",
  "webhook_url": "https://your-domain.com/api/webhook/telegram",
  "secret_token": "your_secret_token"
}
```

---

## 🎨 Canvas API

### Загрузка Canvas данных

```
GET /api/command-templates/{id}/canvas
```

**Ответ:**
```json
{
  "success": true,
  "data": {
    "nodes": [
      {
        "id": "node_1",
        "type": "send_message",
        "position": { "x": 100, "y": 100 },
        "data": {
          "message_text": "Привет! Как дела?",
          "message_type": "text",
          "keyboard_template_id": null
        }
      }
    ],
    "edges": [
      {
        "id": "edge_1", 
        "source": "node_1",
        "target": "node_2",
        "type": "default"
      }
    ]
  }
}
```

### Сохранение Canvas данных

```
PUT /api/command-templates/{id}/canvas
```

**Тело запроса:**
```json
{
  "nodes": [
    {
      "id": "node_1",
      "type": "send_message",
      "position": { "x": 100, "y": 100 },
      "data": {
        "message_text": "Обновленное сообщение",
        "message_type": "text"
      }
    }
  ],
  "edges": [
    {
      "id": "edge_1",
      "source": "node_1", 
      "target": "node_2",
      "type": "default"
    }
  ]
}
```

### Валидация Canvas workflow

```
POST /api/canvas/validate
```

**Тело запроса:**
```json
{
  "nodes": [...],
  "edges": [...]
}
```

**Ответ:**
```json
{
  "success": true,
  "data": {
    "valid": true,
    "errors": [],
    "warnings": [
      "Узел 'node_3' не соединен с другими узлами"
    ]
  }
}
```

### Получение типов узлов

```
GET /api/canvas/node-types
```

**Ответ:**
```json
{
  "success": true,
  "data": {
    "send_message": {
      "name": "Отправить сообщение",
      "icon": "💬",
      "description": "Отправляет сообщение пользователю",
      "inputs": ["default"],
      "outputs": ["default"],
      "settings": {
        "message_text": {
          "type": "textarea",
          "required": true,
          "label": "Текст сообщения"
        }
      }
    }
  }
}
```

### Дублирование команды

```
POST /api/command-templates/{id}/canvas/duplicate
```

**Тело запроса:**
```json
{
  "name": "Копия команды",
  "description": "Дублированная команда"
}
```

---

## ⌨️ Keyboard Templates API

### Список шаблонов клавиатур

```
GET /api/keyboard-templates
```

**Параметры запроса:**
- `search` — поиск по названию/описанию
- `type` — тип клавиатуры (`reply`, `inline`)
- `page` — номер страницы
- `per_page` — количество на странице

**Пример запроса:**
```
GET /api/keyboard-templates?search=главное&type=reply&per_page=10
```

**Ответ:**
```json
{
  "success": true,
  "data": {
    "data": [
      {
        "id": 1,
        "name": "Главное меню",
        "description": "Основная навигация по боту",
        "keyboard_type": "reply",
        "keyboard_data": {
          "keyboard": [
            ["📋 Каталог", "🛒 Корзина"],
            ["👤 Профиль", "ℹ️ Помощь"]
          ],
          "resize_keyboard": true,
          "one_time_keyboard": false
        },
        "created_at": "2025-08-01T12:00:00Z"
      }
    ],
    "meta": {
      "current_page": 1,
      "total": 25,
      "per_page": 10
    }
  }
}
```

### Создание шаблона клавиатуры

```
POST /api/keyboard-templates
```

**Тело запроса:**
```json
{
  "name": "Новое меню",
  "description": "Описание меню",
  "keyboard_type": "inline",
  "keyboard_data": {
    "inline_keyboard": [
      [
        {
          "text": "✅ Подтвердить",
          "callback_data": "confirm"
        },
        {
          "text": "❌ Отменить",
          "callback_data": "cancel"
        }
      ]
    ]
  }
}
```

**Ответ:**
```json
{
  "success": true,
  "data": {
    "id": 26,
    "name": "Новое меню",
    "keyboard_type": "inline",
    "keyboard_data": { /* данные клавиатуры */ }
  }
}
```

### Получение шаблона клавиатуры

```
GET /api/keyboard-templates/{id}
```

### Обновление шаблона клавиатуры

```
PUT /api/keyboard-templates/{id}
```

### Удаление шаблона клавиатуры

```
DELETE /api/keyboard-templates/{id}
```

### Создание шаблона из кнопок

```
POST /api/keyboard-templates/create-from-buttons
```

**Тело запроса:**
```json
{
  "name": "Быстрое меню",
  "buttons": [
    {"text": "Кнопка 1", "action": "action_1"},
    {"text": "Кнопка 2", "action": "action_2"}
  ],
  "keyboard_type": "reply",
  "layout": "2x1"
}
```

---

## 👤 User API

### Получение текущего пользователя

```
GET /api/user
```

**Ответ:**
```json
{
  "success": true,
  "data": {
    "id": 1,
    "name": "John Doe",
    "email": "john@example.com",
    "tenant_id": 1,
    "created_at": "2025-01-01T00:00:00Z",
    "permissions": ["canvas.create", "bots.manage"]
  }
}
```

---

## 🤖 Bots API

### Список ботов

```
GET /api/bots
```

**Ответ:**
```json
{
  "success": true,
  "data": [
    {
      "id": 1,
      "name": "Мой бот",
      "username": "my_test_bot",
      "token": "1234...***", // замаскированный токен
      "webhook_url": "https://your-domain.com/api/webhook/telegram",
      "webhook_status": "active",
      "is_active": true,
      "commands_count": 5,
      "created_at": "2025-08-01T12:00:00Z"
    }
  ]
}
```

### Создание бота

```
POST /api/bots
```

**Тело запроса:**
```json
{
  "name": "Новый бот",
  "token": "1234567890:AABBCCDDEEFFGGHHIIJJKKLLMMNNOOPPq",
  "description": "Описание бота"
}
```

### Обновление бота

```
PUT /api/bots/{id}
```

### Удаление бота

```
DELETE /api/bots/{id}
```

---

## 📊 Analytics API

### Статистика бота

```
GET /api/bots/{id}/stats
```

**Параметры:**
- `period` — период (`day`, `week`, `month`)
- `from` — дата начала (ISO 8601)
- `to` — дата окончания (ISO 8601)

**Ответ:**
```json
{
  "success": true,
  "data": {
    "messages_sent": 1250,
    "messages_received": 890,
    "active_users": 145,
    "commands_executed": 2340,
    "popular_commands": [
      {"command": "/start", "count": 450},
      {"command": "/help", "count": 123}
    ],
    "chart_data": {
      "labels": ["01.08", "02.08", "03.08"],
      "datasets": [
        {
          "label": "Сообщения",
          "data": [120, 145, 98]
        }
      ]
    }
  }
}
```

### Логи разговоров

```
GET /api/conversations
```

**Параметры:**
- `bot_id` — ID бота
- `user_id` — ID пользователя
- `status` — статус разговора
- `page` — страница
- `per_page` — записей на странице

**Ответ:**
```json
{
  "success": true,
  "data": {
    "data": [
      {
        "id": "conv_123",
        "bot_id": 1,
        "user_id": 123456789,
        "status": "completed",
        "started_at": "2025-08-01T10:30:00Z",
        "completed_at": "2025-08-01T10:35:00Z",
        "steps_count": 8,
        "last_step": "order_confirmation"
      }
    ]
  }
}
```

---

## 🔍 Health Check API

### Проверка состояния системы

```
GET /api/health
```

**Ответ:**
```json
{
  "success": true,
  "data": {
    "status": "healthy",
    "services": {
      "database": "ok",
      "redis": "ok",
      "queue": "ok",
      "storage": "ok"
    },
    "metrics": {
      "uptime": 3600,
      "memory_usage": "45%",
      "disk_usage": "23%"
    },
    "version": "1.2.0",
    "environment": "production"
  }
}
```

### Проверка отладки

```
GET /debug
```

**Ответ:**
```json
{
  "status": "ok",
  "app_url": "https://your-domain.com",
  "environment": "production",
  "timestamp": "2025-08-01T12:00:00Z",
  "routes_count": 45
}
```

---

## 📝 Коды ошибок

### Стандартные ошибки

```json
{
  "success": false,
  "message": "Ошибка валидации",
  "errors": {
    "name": ["Поле обязательно для заполнения"],
    "email": ["Некорректный формат email"]
  },
  "error_code": "VALIDATION_ERROR"
}
```

### Специфичные коды ошибок

| Код | Описание |
|-----|----------|
| `VALIDATION_ERROR` | Ошибка валидации данных |
| `AUTHENTICATION_FAILED` | Неудачная аутентификация |
| `AUTHORIZATION_DENIED` | Недостаточно прав |
| `RESOURCE_NOT_FOUND` | Ресурс не найден |
| `RATE_LIMIT_EXCEEDED` | Превышен лимит запросов |
| `WEBHOOK_SIGNATURE_INVALID` | Неверная подпись webhook |
| `BOT_TOKEN_INVALID` | Неверный токен бота |
| `CANVAS_VALIDATION_FAILED` | Ошибка валидации Canvas |
| `INTERNAL_SERVER_ERROR` | Внутренняя ошибка сервера |

---

## 🛡️ Безопасность

### Rate Limiting

API использует rate limiting для защиты от злоупотреблений:

| Endpoint | Лимит |
|----------|-------|
| `/api/webhook/*` | 1000 запросов/минуту |
| `/api/canvas/*` | 60 запросов/минуту |
| `/api/keyboard-templates/*` | 100 запросов/минуту |
| Остальные | 200 запросов/минуту |

### CORS

API поддерживает CORS для интеграции с frontend приложениями:

```
Access-Control-Allow-Origin: *
Access-Control-Allow-Methods: GET, POST, PUT, DELETE, OPTIONS
Access-Control-Allow-Headers: Content-Type, Authorization, X-Requested-With
```

### Webhook Security

Telegram webhook'и защищены подписью:

```php
// Проверка подписи
$secret = hash('sha256', $bot_token, true);
$signature = hash_hmac('sha256', $request_body, $secret);
$expected = 'sha256=' . $signature;
```

---

## 📚 SDK и библиотеки

### PHP SDK

```bash
composer require telegram-bot-manager/php-sdk
```

```php
use TelegramBotManager\SDK\Client;

$client = new Client([
    'base_url' => 'https://your-domain.com/api',
    'token' => 'your-api-token'
]);

// Загрузка Canvas данных
$canvas = $client->canvas()->load($templateId);

// Создание клавиатуры
$keyboard = $client->keyboards()->create([
    'name' => 'Test Keyboard',
    'keyboard_type' => 'reply',
    'keyboard_data' => [...]
]);
```

### JavaScript SDK

```bash
npm install telegram-bot-manager-sdk
```

```javascript
import { TelegramBotManagerClient } from 'telegram-bot-manager-sdk';

const client = new TelegramBotManagerClient({
  baseURL: 'https://your-domain.com/api',
  token: 'your-api-token'
});

// Загрузка Canvas данных
const canvas = await client.canvas.load(templateId);

// Сохранение Canvas
await client.canvas.save(templateId, canvasData);
```

---

## 🧪 Тестирование API

### Postman Collection

Импортируйте коллекцию Postman для тестирования API:

```bash
# Скачать коллекцию
curl -o telegram-bot-manager.postman_collection.json \
     https://your-domain.com/api/postman-collection
```

### Примеры с cURL

**Создание клавиатуры:**
```bash
curl -X POST https://your-domain.com/api/keyboard-templates \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Test Menu",
    "keyboard_type": "reply",
    "keyboard_data": {
      "keyboard": [["Button 1", "Button 2"]],
      "resize_keyboard": true
    }
  }'
```

**Валидация Canvas:**
```bash
curl -X POST https://your-domain.com/api/canvas/validate \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "nodes": [...],
    "edges": [...]
  }'
```

---

## 📞 Поддержка

### Вопросы по API

- 🐛 **Баги**: [GitHub Issues](https://github.com/surnin/telegram-bot-manager/issues)
- 💬 **Обсуждения**: [GitHub Discussions](https://github.com/surnin/telegram-bot-manager/discussions)
- 📧 **Email**: api-support@telegram-bot-manager.com

### Changelog

API следует семантическому версионированию. Актуальные изменения доступны в [CHANGELOG.md](https://github.com/surnin/telegram-bot-manager/blob/main/CHANGELOG.md).

### Миграция версий

При обновлении API мы предоставляем:

- **Руководства по миграции**
- **Период поддержки старых версий** (6 месяцев)
- **Автоматические инструменты миграции**

---

<div style="text-align: center; margin: 3rem 0;">
  <strong>🔌 API готов к интеграции с вашими проектами!</strong>
  <br>
  <sub>Следите за обновлениями в GitHub репозитории</sub>
</div>