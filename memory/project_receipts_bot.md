---
name: Receipts Telegram Bot
description: Telegram-бот для сбора фото чеков от кассиров на 16 АЗС с генерацией HTML-отчётов
type: project
github: https://github.com/Evimiz-KZ/cheki-bot
local_path: receipts_bot/
---

Telegram-бот для сбора чеков от кассиров на 16 АЗС.

**GitHub:** [Evimiz-KZ/cheki-bot](https://github.com/Evimiz-KZ/cheki-bot) — отдельный репозиторий, **не** зеркалится в Marketing-Director (см. `.gitignore`).

**Где код локально:** `receipts_bot/` (свой `.git`, свои коммиты).

**Функционал:**
- Регистрация кассира: Фамилия → Имя → № АЗС (1-16)
- Кассир после регистрации просто шлёт фото чека → бот сохраняет
- Админ (владелец) команды `/report` за период до 6 месяцев
- Отчёт — HTML с фото в base64, группировка: АЗС → кассир → время
- Админ может указать другой Telegram ID, чтобы отчёт ушёл туда

**Стек:** Python + aiogram 3 + SQLite. Деплой на Linux-хостинг (есть `Dockerfile`, `k8s/`, `install.sh`, `update.sh`, systemd-юнит).

**Деплой:** k8s-ready, `/data` PVC, `healthz` endpoint, логи в stdout. См. `receipts_bot/HANDOFF.md`.

**Why:** Кассирам нужен максимально простой UX — только загрузка фото. Вся аналитика и отчётность — на стороне бота и владельца.

**How to apply:** При доработках — сохранять простоту для кассира (никаких дополнительных вопросов после регистрации). Все новые функции добавлять как админские команды.

**Если работаешь в новой сессии:**
- Код смотри в `receipts_bot/` (если нет локально — `git clone https://github.com/Evimiz-KZ/cheki-bot.git receipts_bot`).
- Коммиты по боту делаются в **его собственном** репо `cheki-bot`, не в Marketing-Director.
- `.env` с токеном бота лежит локально, **не** в git (см. `receipts_bot/.env.example`).
