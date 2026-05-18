---
name: Receipts Telegram Bot
description: Telegram-бот для сбора фото чеков от кассиров на 16 АЗС с генерацией HTML-отчётов
type: project
status: active
last_touched: 2026-05-04
github: https://github.com/Evimiz-KZ/cheki-bot
local_path: receipts_bot/
---

# Receipts Telegram Bot (cheki-bot)

Telegram-бот для сбора чеков от кассиров на 16 АЗС.

**GitHub:** [Evimiz-KZ/cheki-bot](https://github.com/Evimiz-KZ/cheki-bot) — **отдельный** репозиторий, не зеркалится в Marketing-Director (см. `.gitignore`).

## Запуск сессии по этому проекту

> Работаем над Receipts Bot. Прочитай `memory/project_receipts_bot.md`. Сам код — в отдельном репо `github.com/Evimiz-KZ/cheki-bot`, локально в `receipts_bot/`. Жду задачу.

## На новом устройстве

```bash
# Из корня Marketing-Director:
git clone https://github.com/Evimiz-KZ/cheki-bot.git receipts_bot
cd receipts_bot
cp .env.example .env
# Заполнить .env вручную (BOT_TOKEN, ADMIN_ID) — лежит ТОЛЬКО локально на старом устройстве
```

## Функционал

- Регистрация кассира: Фамилия → Имя → № АЗС (1-16)
- Кассир после регистрации просто шлёт фото чека → бот сохраняет
- Админ (владелец) команды `/report` за период до 6 месяцев
- Отчёт — HTML с фото в base64, группировка: АЗС → кассир → время
- Админ может указать другой Telegram ID, чтобы отчёт ушёл туда

## Стек

Python + aiogram 3 + SQLite. Деплой на Linux-хостинг (есть `Dockerfile`, `k8s/`, `install.sh`, `update.sh`, systemd-юнит).

**Деплой:** k8s-ready, `/data` PVC, `healthz` endpoint, логи в stdout. См. `receipts_bot/HANDOFF.md`.

## Что НЕ в git (бота) — только локально

| Файл | Почему |
|---|---|
| `receipts_bot/.env` | Токен Telegram-бота и админский Telegram ID |
| `receipts_bot/receipts/*` | Сами фото чеков от кассиров |
| `receipts_bot/reports/*`, `logs/*` | Генерируется на лету |

## Принципы

- Кассирам нужен максимально простой UX — только загрузка фото.
- Вся аналитика и отчётность — на стороне бота и владельца.
- Все новые функции добавлять как **админские** команды, кассирский флоу не трогать.

## Не делай

- Не задавай кассиру дополнительных вопросов после регистрации — только фото.
- Не коммить изменения по боту в Marketing-Director — только в свой репо `cheki-bot`.
- Не публикуй `.env` или содержимое `receipts/`.

## TODO / открытые вопросы

(заполнять по итогам сессий — крупные TODO держать в `receipts_bot/HANDOFF.md`)
