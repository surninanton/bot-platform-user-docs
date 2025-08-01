---
layout: default
title: Главная
description: Telegram Bot Manager - современная SaaS-платформа для создания и управления Telegram ботами
---

# 🤖 Telegram Bot Manager

<div style="text-align: center; margin: 2rem 0;">
  <img src="https://img.shields.io/badge/Laravel-12.x-FF2D20?style=for-the-badge&logo=laravel" alt="Laravel">
  <img src="https://img.shields.io/badge/PHP-8.2+-777BB4?style=for-the-badge&logo=php" alt="PHP">
  <img src="https://img.shields.io/badge/React-18+-61DAFB?style=for-the-badge&logo=react" alt="React">
  <img src="https://img.shields.io/badge/MySQL-8.0+-4479A1?style=for-the-badge&logo=mysql" alt="MySQL">
</div>

**Многофункциональная SaaS-платформа для создания и управления Telegram ботами с визуальным конструктором команд**

---

## 🎯 Что такое Telegram Bot Manager?

Telegram Bot Manager — это современная платформа, которая позволяет создавать, настраивать и управлять Telegram ботами **без необходимости программирования**. 

### 🎨 Визуальный конструктор команд

Создавайте сложные сценарии для вашего бота с помощью интуитивного drag-and-drop интерфейса:

```
🎯 Перетащите блок → 🔗 Соедините с другими → 🚀 Опубликуйте бота
```

### ✨ Основные возможности

<div class="feature-grid">

<div class="feature-card">
<h4>🎨 Canvas Builder</h4>
<ul>
<li><strong>7 типов узлов</strong> для создания любой логики</li>
<li><strong>Визуальные связи</strong> между действиями</li>
<li><strong>Условная логика</strong> и циклы</li>
<li><strong>Переменные</strong> и API интеграции</li>
</ul>
</div>

<div class="feature-card">
<h4>🏢 Multi-tenant</h4>
<ul>
<li><strong>Полная изоляция</strong> данных клиентов</li>
<li><strong>Гибкие планы</strong> использования</li>
<li><strong>Управление пользователями</strong></li>
<li><strong>Масштабируемость</strong></li>
</ul>
</div>

<div class="feature-card">
<h4>🤖 Управление ботами</h4>
<ul>
<li><strong>Безопасное хранение</strong> токенов</li>
<li><strong>Автоматические webhook'и</strong></li>
<li><strong>Логирование</strong> всех событий</li>
<li><strong>Monitoring</strong> в реальном времени</li>
</ul>
</div>

<div class="feature-card">
<h4>📊 Админ-панель</h4>
<ul>
<li><strong>Laravel Filament</strong> интерфейс</li>
<li><strong>Real-time мониторинг</strong></li>
<li><strong>Аналитика</strong> использования</li>
<li><strong>Поиск и фильтры</strong></li>
</ul>
</div>

</div>

---

## 🎭 Типы узлов Canvas

Создавайте сложную логику с помощью различных типов узлов:

| Узел | Описание | Использование |
|------|----------|---------------|
| 💬 **Отправить сообщение** | Отправляет текст, изображения, клавиатуры | Основное взаимодействие с пользователем |
| ⏱️ **Задержка** | Пауза перед следующим действием | Создание естественного диалога |
| ❓ **Условие** | Проверка условий и ветвление | if/else логика |
| 📝 **Запрос ввода** | Ожидание ответа от пользователя | Сбор данных от пользователя |
| 🌐 **API вызов** | Интеграция с внешними сервисами | Получение данных, отправка уведомлений |
| 📦 **Переменная** | Сохранение и использование данных | Хранение состояния диалога |
| 🔄 **Цикл** | Повторение действий | Обработка списков, повторяющиеся задачи |

---

## 🚀 Начать работу

<div style="display: flex; gap: 1rem; margin: 2rem 0; flex-wrap: wrap;">
  <a href="/quick-start/" class="btn btn-primary">
    📖 Быстрый старт
  </a>
  <a href="/canvas-guide/" class="btn btn-secondary">
    🎨 Руководство по Canvas
  </a>
  <a href="{{ site.main_repo }}" class="btn btn-purple">
    💻 GitHub
  </a>
</div>

---

## 🏗️ Архитектура

Платформа построена с использованием современных архитектурных паттернов:

### 📐 Domain-Driven Design (DDD)

```
📱 Presentation Layer
    ↓
📋 Application Layer  
    ↓
🏢 Domain Layer
    ↓
🗄️ Infrastructure Layer
```

### 🎯 Основные домены

- **🤖 Bot Management** — управление ботами и webhook'ами
- **⚡ Command Execution** — выполнение команд
- **🎨 Conversation** — Canvas система и диалоги
- **👥 User Management** — пользователи и права доступа

---

## 📊 Технологический стек

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 1rem; margin: 2rem 0;">

<div>
<h4>Backend</h4>
<ul>
<li>Laravel 12.19.3</li>
<li>PHP 8.2+</li>
<li>Laravel Filament 3.3</li>
<li>MySQL 8.0</li>
<li>Redis 6.0</li>
</ul>
</div>

<div>
<h4>Frontend</h4>
<ul>
<li>React 18</li>
<li>React Flow</li>
<li>Tailwind CSS</li>
<li>Alpine.js</li>
<li>Vite</li>
</ul>
</div>

</div>

---

## 📚 Документация

| Раздел | Описание |
|--------|----------|
| [📖 Быстрый старт](/quick-start/) | Установка и первые шаги |
| [🎨 Canvas Guide](/canvas-guide/) | Подробное руководство по визуальному конструктору |
| [🔌 API Документация](/api/) | REST API справочник |
| [🏗️ Архитектура]({{ site.main_repo }}#архитектура) | Техническая архитектура проекта |
| [🤝 Contributing]({{ site.main_repo }}#contributing) | Как участвовать в разработке |

---

## 🎪 Команда

Проект разрабатывается командой из 9 специалистов:

- **👨‍💼 Тимлид** — стратегия и планирование
- **🧱 Артурио** — архитектура и DDD
- **🧑‍💻 Тотоний** — Laravel/PHP разработка
- **🔍 Тим** — code review и тестирование
- **🚀 Гамэр** — DevOps и CI/CD
- **🛡 Данил** — безопасность
- **📚 Марина** — документация
- **🗄️ Даниил** — база данных
- **📋 Катя** — Scrum мастер

---

## 📈 Статус проекта

### ✅ Готово (v{{ site.version }})
- Multi-tenant инфраструктура
- Canvas Builder с 7 типами узлов  
- Полная система управления ботами
- Laravel Filament админ-панель
- DDD архитектура

### 🔄 В разработке (v1.3)
- Расширенные Canvas возможности
- Улучшенная система тестирования
- Дополнительные API интеграции

### 🎯 Планы (v2.0)
- Marketplace шаблонов команд
- Мобильное приложение
- Многоязычная поддержка
- Расширенная аналитика

---

## 📄 Лицензия

Проект распространяется под лицензией **MIT License**.

---

## 🔗 Полезные ссылки

- 💻 **[Основной репозиторий]({{ site.main_repo }})**
- 🐛 **[Сообщить о баге]({{ site.main_repo }}/issues/new?template=bug_report.md)**
- 💡 **[Предложить функцию]({{ site.main_repo }}/issues/new?template=feature_request.md)**
- 💬 **[Discussions]({{ site.main_repo }}/discussions)**
- 📧 **[Поддержка](mailto:{{ site.social.email }})**

---

<div style="text-align: center; margin: 3rem 0;">
  <strong>Сделано с ❤️ командой Telegram Bot Manager</strong>
  <br>
  <sub>⭐ Поставьте звезду на GitHub, если проект вам полезен!</sub>
</div>