# 📚 Telegram Bot Manager - Пользовательская документация

Это репозиторий содержит пользовательскую документацию для [Telegram Bot Manager](https://github.com/surnin/telegram-bot-manager) - современной SaaS-платформы для создания и управления Telegram ботами.

## 🌐 Онлайн документация

**🔗 [Перейти к документации](https://surnin.github.io/bot-platform-user-docs/)**

---

## 📖 Содержание

- **[🏠 Главная](https://surnin.github.io/bot-platform-user-docs/)** — обзор платформы и возможностей
- **[🚀 Быстрый старт](https://surnin.github.io/bot-platform-user-docs/quick-start/)** — установка и настройка за 15 минут
- **[🎨 Canvas Guide](https://surnin.github.io/bot-platform-user-docs/canvas-guide/)** — полное руководство по визуальному конструктору
- **[🔌 API Документация](https://surnin.github.io/bot-platform-user-docs/api/)** — REST API справочник

---

## 🎯 О платформе

**Telegram Bot Manager** — это многофункциональная SaaS-платформа, которая позволяет:

### ✨ Основные возможности

- 🎨 **Canvas Builder** — визуальный конструктор команд с drag-and-drop интерфейсом
- 🏢 **Multi-tenant архитектура** — полная изоляция данных между клиентами
- 🤖 **Управление ботами** — безопасное хранение токенов и автоматические webhook'и
- 📊 **Админ-панель** — современный интерфейс на Laravel Filament
- 🔌 **REST API** — полная интеграция с внешними системами

### 🎭 Canvas узлы

| Тип узла | Функция |
|----------|---------|
| 💬 **Send Message** | Отправка сообщений, изображений, клавиатур |
| ⏱️ **Delay** | Паузы для естественного диалога |
| ❓ **Condition** | Условная логика и ветвления |
| 📝 **Input Request** | Запрос данных от пользователя |
| 🌐 **API Call** | Интеграция с внешними сервисами |
| 📦 **Set Variable** | Работа с переменными |
| 🔄 **Loop** | Циклы и повторения |

---

## 🏗️ Архитектура документации

Документация построена с использованием **Jekyll** и **GitHub Pages**:

```
bot-platform-user-docs/
├── _config.yml          # Конфигурация Jekyll
├── index.md             # Главная страница
├── quick-start.md       # Руководство по установке
├── canvas-guide.md      # Canvas документация
├── api.md              # API справочник  
├── assets/             # Стили и ресурсы
├── Gemfile             # Ruby зависимости
└── README.md           # Этот файл
```

---

## 🔧 Локальная разработка

### Требования

- Ruby 3.0+
- Jekyll 4.3+
- Bundler

### Установка и запуск

```bash
# Клонирование репозитория
git clone https://github.com/surnin/bot-platform-user-docs.git
cd bot-platform-user-docs

# Установка зависимостей
bundle install

# Запуск локального сервера
bundle exec jekyll serve

# Открыть http://localhost:4000
```

### Автоматическая пересборка

```bash
# С live reload
bundle exec jekyll serve --livereload

# С черновиками
bundle exec jekyll serve --drafts
```

---

## ✏️ Редактирование документации

### Структура файлов

Каждая страница имеет Front Matter с метаданными:

```yaml
---
layout: default
title: Заголовок страницы
description: Описание для SEO
permalink: /custom-url/
---

# Содержимое страницы
```

### Добавление новой страницы

1. Создайте файл `new-page.md`
2. Добавьте Front Matter
3. Добавьте ссылку в навигацию (`_config.yml`)
4. Создайте Pull Request

### Стилизация

Кастомные стили находятся в `assets/css/style.scss`. Доступные классы:

- `.btn`, `.btn-primary`, `.btn-secondary` — кнопки
- `.feature-grid`, `.feature-card` — сетка возможностей  
- `.alert`, `.alert-info`, `.alert-warning` — уведомления
- `.badge`, `.badge-success` — метки

---

## 🚀 Деплой

Документация автоматически публикуется на GitHub Pages при коммитах в `main` ветку.

### GitHub Actions

Настроена автоматическая сборка через `.github/workflows/pages.yml`:

- ✅ Сборка Jekyll при каждом коммите
- ✅ Деплой на GitHub Pages
- ✅ Проверка ссылок и валидация HTML

### Мануальный деплой

```bash
# Сборка статических файлов
bundle exec jekyll build

# Файлы будут в папке _site/
```

---

## 🔗 Связанные репозитории

- **[🏠 Основной проект](https://github.com/surnin/telegram-bot-manager)** — исходный код платформы
- **[📚 Документация](https://github.com/surnin/bot-platform-user-docs)** — этот репозиторий
- **[🎯 Примеры](https://github.com/surnin/telegram-bot-examples)** — готовые шаблоны ботов

---

## 🤝 Участие в разработке

### Как помочь

1. **📝 Улучшение документации**
   - Исправление опечаток
   - Добавление примеров
   - Переводы на другие языки

2. **🐛 Сообщения об ошибках**
   - Неточности в документации
   - Нерабочие ссылки
   - Проблемы с отображением

3. **💡 Предложения**
   - Новые разделы
   - Улучшения структуры
   - Дополнительные примеры

### Процесс

1. Fork репозитория
2. Создайте ветку: `git checkout -b feature/new-docs`
3. Внесите изменения
4. Протестируйте локально: `bundle exec jekyll serve`
5. Создайте Pull Request

---

## 📊 Статистика

- **📄 Страниц**: 4 основные + дополнительные
- **🎯 Охват**: Начинающие и продвинутые пользователи
- **🌍 Языки**: Русский (основной), English (планируется)
- **📱 Поддержка**: Адаптивный дизайн для всех устройств

---

## 📞 Контакты и поддержка

### Документация

- 🐛 **[Issues](https://github.com/surnin/bot-platform-user-docs/issues)** — баги и предложения
- 💬 **[Discussions](https://github.com/surnin/bot-platform-user-docs/discussions)** — обсуждения
- 📧 **Email**: docs@telegram-bot-manager.com

### Основной проект

- 🐛 **[Main Issues](https://github.com/surnin/telegram-bot-manager/issues)** — баги платформы
- 💬 **[Main Discussions](https://github.com/surnin/telegram-bot-manager/discussions)** — общие обсуждения
- 📧 **Email**: support@telegram-bot-manager.com

---

## 📄 Лицензия

Документация распространяется под лицензией **MIT License**.

Основной проект: **MIT License** - см. [LICENSE](https://github.com/surnin/telegram-bot-manager/blob/main/LICENSE)

---

## 🎯 Roadmap

### v1.1 ✅
- [x] Базовая структура документации
- [x] Руководство по быстрому старту
- [x] Canvas Guide
- [x] API документация

### v1.2 🔄
- [ ] Видео-туториалы
- [ ] Интерактивные примеры
- [ ] FAQ раздел
- [ ] Глоссарий терминов

### v2.0 🎯
- [ ] Многоязычная поддержка
- [ ] Поиск по документации
- [ ] Комментарии и обратная связь
- [ ] Интеграция с основным проектом

---

<div align="center">
  <strong>📚 Сделано с ❤️ командой Telegram Bot Manager</strong>
  <br><br>
  <a href="https://surnin.github.io/bot-platform-user-docs/">
    <img src="https://img.shields.io/badge/Docs-Online-brightgreen?style=for-the-badge" alt="Documentation">
  </a>
  <a href="https://github.com/surnin/telegram-bot-manager">
    <img src="https://img.shields.io/badge/Main-Repository-blue?style=for-the-badge" alt="Main Repository">
  </a>
  <a href="https://github.com/surnin/bot-platform-user-docs/blob/main/LICENSE">
    <img src="https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge" alt="License">
  </a>
</div>