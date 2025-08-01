---
layout: default
title: Быстрый старт
description: Пошаговое руководство по установке и настройке Telegram Bot Manager
permalink: /quick-start/
---

# 🚀 Быстрый старт

Это руководство поможет вам развернуть Telegram Bot Manager и создать вашего первого бота за 15 минут.

---

## 📋 Требования

Перед началом убедитесь, что у вас установлено:

| Компонент | Минимальная версия | Рекомендуемая |
|-----------|-------------------|---------------|
| **PHP** | 8.2 | 8.3+ |
| **Composer** | 2.0 | 2.6+ |
| **Node.js** | 18 | 20+ |
| **MySQL** | 8.0 | 8.0+ |
| **Redis** | 6.0 | 7.0+ |
| **Git** | 2.0 | 2.40+ |

---

## 🐳 Способ 1: Docker (Рекомендуется)

Самый простой способ запустить проект — использовать Docker.

### Шаг 1: Клонирование репозитория

```bash
git clone https://github.com/surnin/telegram-bot-manager.git
cd telegram-bot-manager
```

### Шаг 2: Настройка окружения

```bash
# Копируем файл настроек
cp .env.example .env

# Редактируем настройки
nano .env
```

**Основные настройки в .env:**

```env
# Основные настройки приложения
APP_NAME="Telegram Bot Manager"
APP_ENV=local
APP_DEBUG=true
APP_URL=http://localhost:8000

# База данных
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=telegram_bot_manager
DB_USERNAME=root
DB_PASSWORD=password

# Redis
REDIS_HOST=127.0.0.1
REDIS_PASSWORD=null
REDIS_PORT=6379

# Telegram (заполните после создания бота)
TELEGRAM_BOT_TOKEN=your_bot_token_here
TELEGRAM_WEBHOOK_URL=https://yourdomain.com/webhook
```

### Шаг 3: Запуск через Docker

```bash
# Запуск всех сервисов
docker-compose up -d

# Проверка статуса
docker-compose ps
```

### Шаг 4: Настройка приложения

```bash
# Установка зависимостей и миграции
docker-compose exec app composer install
docker-compose exec app php artisan key:generate
docker-compose exec app php artisan migrate
docker-compose exec app php artisan storage:link

# Создание администратора
docker-compose exec app php artisan make:filament-user
```

### Шаг 5: Сборка фронтенда

```bash
# Установка Node.js зависимостей
docker-compose exec app npm install

# Сборка для разработки
docker-compose exec app npm run dev

# Или для продакшена
docker-compose exec app npm run build
```

---

## 📦 Способ 2: Стандартная установка

### Шаг 1: Подготовка системы

**Ubuntu/Debian:**
```bash
sudo apt update
sudo apt install php8.2 php8.2-fpm php8.2-mysql php8.2-xml php8.2-curl php8.2-mbstring php8.2-zip
sudo apt install mysql-server redis-server nodejs npm
```

**macOS (Homebrew):**
```bash
brew install php@8.2 mysql redis node
brew services start mysql
brew services start redis
```

### Шаг 2: Клонирование и настройка

```bash
# Клонирование
git clone https://github.com/surnin/telegram-bot-manager.git
cd telegram-bot-manager

# Настройка окружения
cp .env.example .env
```

### Шаг 3: Установка зависимостей

```bash
# PHP зависимости
composer install

# Node.js зависимости
npm install
```

### Шаг 4: Настройка приложения

```bash
# Генерация ключа
php artisan key:generate

# Миграции БД
php artisan migrate

# Создание симлинка для файлов
php artisan storage:link

# Создание администратора
php artisan make:filament-user
```

### Шаг 5: Сборка фронтенда и запуск

```bash
# Сборка фронтенда
npm run build

# Запуск всех сервисов разработки
composer dev
```

---

## 🤖 Создание первого Telegram бота

### Шаг 1: Регистрация бота в Telegram

1. Откройте Telegram и найдите [@BotFather](https://t.me/botfather)
2. Отправьте команду `/newbot`
3. Введите имя бота (например: "My Test Bot")
4. Введите username бота (например: "my_test_bot")
5. Скопируйте полученный токен

### Шаг 2: Настройка токена

Добавьте токен в файл `.env`:

```env
TELEGRAM_BOT_TOKEN=1234567890:AABBCCDDEEFFGGHHIIJJKKLLMMNNOOPPq
```

### Шаг 3: Создание бота в системе

1. Откройте админ-панель: [http://localhost:8000/admin](http://localhost:8000/admin)
2. Войдите с созданными ранее учетными данными
3. Перейдите в раздел **"Боты"**
4. Нажмите **"Создать"**
5. Заполните форму:
   - **Название**: "Мой первый бот"
   - **Токен**: вставьте токен от BotFather
   - **Описание**: краткое описание

### Шаг 4: Настройка webhook

```bash
# Установка webhook для бота
php artisan set:webhook
```

---

## 🎨 Создание первой команды в Canvas

### Шаг 1: Открытие Canvas Builder

1. В админ-панели перейдите в **"Canvas Builder"**
2. Нажмите **"Создать"**
3. Введите название команды (например: "Приветствие")

### Шаг 2: Создание простого сценария

Создадим простой сценарий приветствия:

1. **Добавьте узел "Отправить сообщение"**:
   - Перетащите из панели слева
   - Введите текст: "Привет! Как дела?"

2. **Добавьте узел "Запрос ввода"**:
   - Соедините с предыдущим узлом
   - Настройте ожидание ответа

3. **Добавьте узел "Условие"**:
   - Проверьте ответ пользователя
   - Условие: `{{user_input}} содержит "хорошо"`

4. **Добавьте два узла "Отправить сообщение"**:
   - **Если ДА**: "Отлично! Рад это слышать!"
   - **Если НЕТ**: "Надеюсь, всё наладится!"

### Шаг 3: Сохранение и тестирование

1. Нажмите **"Сохранить"**
2. Настройте команду как `/start`
3. Найдите вашего бота в Telegram
4. Отправьте `/start`

---

## ✅ Проверка установки

### Доступность сервисов

Убедитесь, что все работает правильно:

| Сервис | URL | Ожидаемый результат |
|--------|-----|-------------------|
| **Веб-приложение** | http://localhost:8000 | Приветственная страница |
| **Админ-панель** | http://localhost:8000/admin | Форма входа Filament |
| **API** | http://localhost:8000/api/health | JSON с информацией о статусе |

### Команды для диагностики

```bash
# Проверка статуса очередей
php artisan queue:work --once

# Проверка подключения к БД
php artisan migrate:status

# Проверка Redis
php artisan tinker
>>> Redis::ping()

# Проверка конфигурации
php artisan config:cache
php artisan route:cache
```

---

## 🚨 Решение проблем

### Проблема: "Class not found"

```bash
# Обновите автозагрузку
composer dump-autoload

# Очистите кэш
php artisan cache:clear
php artisan config:clear
php artisan view:clear
```

### Проблема: "Permission denied"

```bash
# Установите права доступа
sudo chown -R www-data:www-data storage bootstrap/cache
chmod -R 775 storage bootstrap/cache
```

### Проблема: "npm EACCES"

```bash
# Исправьте права для npm
sudo chown -R $(whoami) ~/.npm
```

### Проблема: Webhook не работает

1. Убедитесь, что URL доступен извне
2. Проверьте SSL сертификат
3. Посмотрите логи:

```bash
# Логи webhook'ов
php artisan pail --filter="webhook"

# Общие логи
tail -f storage/logs/laravel.log
```

---

## 🔧 Разработка

### Полезные команды

```bash
# Запуск всех сервисов разработки
composer dev

# Только веб-сервер
php artisan serve

# Только обработка очередей
php artisan queue:listen

# Только логи в реальном времени
php artisan pail

# Только фронтенд (hot reload)
npm run dev
```

### Структура проекта

```
telegram-bot-manager/
├── app/                    # Код приложения
│   ├── Domain/            # DDD домены
│   ├── Application/       # Use Cases
│   ├── Infrastructure/    # Реализации репозиториев
│   └── Http/             # Контроллеры и middleware
├── resources/
│   ├── js/               # React компоненты Canvas
│   └── views/            # Blade шаблоны
├── database/
│   ├── migrations/       # Миграции БД
│   └── seeders/         # Начальные данные
└── github-pages/        # Документация для GitHub Pages
```

---

## 🎯 Что дальше?

Теперь, когда система работает, рекомендуем:

1. **[📖 Изучить Canvas Guide](/canvas-guide/)** — подробное руководство по созданию сложных сценариев
2. **[🔌 Изучить API](/api/)** — для интеграции с внешними системами
3. **[🤝 Присоединиться к разработке](https://github.com/surnin/telegram-bot-manager)** — помочь развитию проекта

---

## 📞 Поддержка

Если у вас возникли проблемы:

- 🐛 **Сообщить о баге**: [GitHub Issues](https://github.com/surnin/telegram-bot-manager/issues)
- 💬 **Обсуждения**: [GitHub Discussions](https://github.com/surnin/telegram-bot-manager/discussions)
- 📧 **Email**: support@telegram-bot-manager.com

---

<div style="text-align: center; margin: 2rem 0;">
  <strong>🎉 Поздравляем! Ваш первый Telegram бот готов к работе!</strong>
</div>