---
layout: post
title: "Структура backend и модули NestJS"
date: 2025-06-23 00:00:00 +0300
categories: [Backend]
tags: [nestjs, backend, структура, архитектура]
order: 1
---
После запуска проекта я хотел, чтобы backend был не только рабочим, но и читаемым, расширяемым, модульным. В этой статье покажу, как устроена архитектура backend и почему она работает именно так.

## 🧠 Ключевые идеи

- Каждый модуль — это изолированный блок (*счета*, *категории*, *транзакции*)
- Подход **feature-first**, а не type-first
- Всё рядом: `dto`, `.http`, `entity`, `types`, `*.spec.ts`
- Общие вещи вынесены в `shared/`
- Удобные middlewares: `auth` и `mock-user`

## 🗂 Структура проекта (уровень 2)

```bash
tree -L 2 -I "dist|node_modules|.git|coverage"
```

```text
├── Dockerfile
├── package.json
├── src
│   ├── accounts
│   ├── auth
│   ├── balance
│   ├── categories
│   ├── logger
│   ├── modules
│   ├── reports
│   ├── shared
│   ├── transactions
│   ├── users
│   ├── main.ts
│   └── app.module.ts
├── test
└── tsconfig.json
```

> 💡 Вложенные уровни покажу позже, в примере модуля transactions.

## 📦 Пример: модуль transactions

```text
transactions/
├── dto/
├── transaction.entity.ts
├── transactions.controller.ts
├── transactions.service.ts
├── transactions.module.ts
├── transactions.http
└── transactions.controller.spec.ts
```

Такой подход:
- Упрощает навигацию
- Делает тесты очевидными (*.spec.ts рядом)
- Позволяет держать всё, что касается транзакций, в одной папке

## 🔄 Общие модули

- **shared/** — enum'ы, интерфейсы, утилиты
- **logger/** — Pino, middleware и interceptor
- **auth/** — кастомная авторизация по Telegram ID
- **modules/** — собирает все feature-модули в `AppModule`


## 🚀 Почему это работает

- Быстро находишь нужный код, даже если вернулся к проекту через месяц
- Нет каши из controller/service/entity во всех направлениях
- Можно масштабировать: добавить новый модуль — легко, ничего не ломая

Такой подход даёт не только чистую архитектуру, но и удовольствие от работы.
В следующих статьях покажу примеры реальных модулей, middlewares и тестов.

