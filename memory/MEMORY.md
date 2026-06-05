# Индекс памяти проектов

> Сквозная память по всем проектам владельца репо (Маркетинг директор).
> Любая сессия Claude должна начинать работу с этого файла.

## Как пользоваться

1. Читаешь этот файл → видишь список проектов, статусы, где код.
2. Открываешь нужный `project_<slug>.md` → получаешь стек, хронологию, принципы.
3. Если код в отдельном GitHub-репо — карточка содержит URL для `git clone`.

## Активные проекты

| Проект | Статус | Послед. касание | Карточка | Где код | GitHub |
|---|---|---|---|---|---|
| **KomekAI** — голос+текст AI-ассистент для МСБ KZ | 🟢 active | 2026-06-05 | [project_komekai.md](project_komekai.md) | `KomekAI/` | в этом репо |
| **Immune Up** — SMM + поиск дистрибьюторов | 🟢 active | 2026-05-13 | [project_immune_up.md](project_immune_up.md) | `Immune_Up/` | в этом репо |
| **Dishandi SPA** — стратегия + 90-дн. план | 🟢 active | 2026-05-04 | [project_dishandi.md](project_dishandi.md) | корень: `strategy_dishandi_v1.3.html`, `ACTION_PLAN.md`, `PROJECT.md`, `INVITATION_NIGHT_PLAN.md` | в этом репо |
| **T.S** — сеть АЗС: маркетинг + приложение | 🟢 active | 2026-06-03 | [project_ts_app.md](project_ts_app.md) | `ТС приложение/`, планы `plan_ts_*.html`, `plan_zurai_30d.html` | в этом репо |
| **Receipts Bot** — Telegram-бот сбора чеков | 🟢 active | 2026-05-04 | [project_receipts_bot.md](project_receipts_bot.md) | **отдельный репо**, локально `receipts_bot/` (в `.gitignore`) | [Evimiz-KZ/cheki-bot](https://github.com/Evimiz-KZ/cheki-bot) |

Легенда статусов: 🟢 active · 🟡 paused · ⚪ archive · 🔵 spec/research

## Как продолжить на другом устройстве

### Шаг 0 — клонировать всё, что нужно

```bash
git clone git@github.com:madikabdulovrec-cpu/Marketing-Director.git
cd Marketing-Director

# Если нужен бот — клонируется отдельно:
git clone https://github.com/Evimiz-KZ/cheki-bot.git receipts_bot
```

### Шаг 1 — выбрать проект и дать Claude правильный «вход»

Скопируй один из готовых промптов ниже первым сообщением в новую сессию Claude Code:

**KomekAI:**
> Работаем над KomekAI. Прочитай `memory/project_komekai.md`, затем `KomekAI/KOMEKAI_PLATFORM.md` (описание продукта) и `KomekAI/KomekAI_Strategy_v1.docx` (стратегия по Котлеру). Жду задачу.

**Immune Up:**
> Работаем над Immune Up. Прочитай `memory/project_immune_up.md`, затем список файлов в `Immune_Up/`. Текущая стратегия — `Immune_Up/Immune_Up_Strategy_v2.docx`. Жду задачу.

**Dishandi SPA:**
> Работаем над Dishandi. Прочитай `memory/project_dishandi.md`. Актуальная стратегия — `strategy_dishandi_v1.3.html`, операционный план — `ACTION_PLAN.md`. Жду задачу.

**T.S — приложение АЗС:**
> Работаем над T.S app. Прочитай `memory/project_ts_app.md`. Прототипы в `ТС приложение/TS_app_design_v*.html` и `TS_app_prototype*.html`. Жду задачу.

**Receipts Bot:**
> Работаем над Receipts Bot. Прочитай `memory/project_receipts_bot.md`. Сам код — в отдельном репо `github.com/Evimiz-KZ/cheki-bot`, локально в `receipts_bot/`. Жду задачу.

## Что НЕ в git (нужно перенести вручную, если важно)

| Что | Где локально | Почему не в git |
|---|---|---|
| `dishandi_brief.md` | корень | Бриф клиента, чувствительно |
| `PROJECT_STATE.md` | корень | Внутренние заметки |
| `Бухгалтерия/` | корень | Финансовые данные |
| Все `*.xlsx`, `*.pdf`, исходные `*.docx` | разное | Бинарники / клиентские документы |
| `Immune_Up/inputs/` | `Immune_Up/inputs/` | КП и стратегия от заказчика (~20 MB PDF) |
| `Immune_Up_встреча_и_стратегия.docx`, `Immune_Up_B2B_SMM_стратегия.docx` | корень | Старые версии, заменены `Strategy_v2` |
| `KomekAI/inputs/` | `KomekAI/inputs/` | Зарезервировано под конфиденциальные входящие (брифы, договоры) |
| `receipts_bot/.env` | `receipts_bot/` | Токен Telegram-бота |
| `T.S Brandbook.pdf`, `ТЗ для приложения T.S` | `ТС приложение/` | Брендбук и ТЗ заказчика T.S |
| `ТС приложение/_extracted/brandbook/` | там же | 78 MB PNG-извлечений брендбука |

**Если на новом устройстве чего-то из этого не хватает** — скопируй через флешку / облако из старого устройства. Не пытайся восстановить из git.

## Правила обновления этого файла

- Любой новый проект → строка в таблице + готовый промпт в «Как продолжить на другом устройстве» + создать `project_<slug>.md`.
- При изменении статуса проекта — обновляй колонку «Статус».
- При работе с проектом — обновляй «Послед. касание» (формат YYYY-MM-DD).
