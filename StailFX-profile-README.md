<!--
  GitHub profile README for github.com/StailFX

  HOW TO USE:
  1. Create a new repository at https://github.com/new
     - Repository name: StailFX  (must exactly match your username)
     - Public, ✅ Add a README file
     - GitHub will show a "You found a special repository!" banner
  2. Replace the auto-generated README.md content with this file.
  3. Commit. Open https://github.com/StailFX — this README appears on top.
-->

### Hi, I'm Nikita · StailFX 👋

**Computational mathematics × ML × crypto microstructure.**
4-курс прикладной математики · КФУ Казань · ищу позицию **Data Scientist / Quant Developer / ML Engineer** (Казань / удалённо).

📫 [systemniki42@gmail.com](mailto:systemniki42@gmail.com) · [@StailFX](https://t.me/StailFX) · [+7 (965) 617-93-81](tel:+79656179381)

---

### 🚀 What I'm building right now

#### NeuCast — production HFT pipeline (private repo · live at [neucast.ru](https://neucast.ru))

End-to-end система минутного directional-прогноза на криптовалютах. Полный production-стек, написанный с нуля и развёрнутый на co-located VPS у Binance.

| | |
|---|---|
| **Что делает** | Binance Spot L2 (depth20 @100ms) → OFI/microprice/depth-imbalance features → CatBoost binary classifier → paper-trading state machine с time-stop, vol-adjusted sizing и risk caps |
| **Latency** | TCP RTT Tokyo VPS ↔ Binance ≈ **19 мс** (vs ~250 мс из EU) |
| **Symbols** | BTCUSDT · ETHUSDT · BNBUSDT параллельно |
| **Tests** | **341/341 passing** — каждая ветка state-machine + endpoint покрыта |
| **Architecture** | 11 ADRs документирующих trade-off'ы (Tokyo placement, WireGuard tunnel Finland↔Tokyo, sim-only contract, calibration gate, vol-adjusted Kelly-free sizing) |
| **Storage** | Hot Postgres 7д · Cold Yandex S3 (Parquet+snappy) с atomic verify-before-delete archival cron |
| **Observability** | Self-hosted Prometheus + Grafana + 5 alert rules → Telegram bot. Daily TSDB snapshots в S3. |
| **UI surface** | Live microprice chart · orderbook density heatmap (Bookmap-style canvas) · paper trader log с cumulative P&L · walk-forward calibration plot с Wilson 95% CI · CatBoost feature importance · vol-regime classifier · operations dashboard |
| **Stack** | Python (asyncio) · CatBoost · FastAPI · PostgreSQL · asyncpg · Prometheus · Grafana · WireGuard · nginx · systemd · Yandex Object Storage (S3-compatible) |

#### GymBro — Telegram Mini App fitness tracker

🌐 Live: **[gymbro.dev](https://gymbro.dev)**

Production fitness-приложение внутри Telegram: персонализированные тренировочные протоколы с progressive overload, gamification, social feed и аналитика прогресса.

- 🏆 Грант **1 000 000 ₽** от ФСИ — конкурс **«Студенческий стартап»** (2025)
- 🏢 Резидент **IT Park Казань** (площадка 52)
- **Роль:** генеральный директор · lead backend · project manager · аналитик

**Stack**

FastAPI (async) · Python 3.12 · SQLAlchemy 2.0 (async) · PostgreSQL 15 · Redis 7 · Celery 5.6 · Alembic · Pydantic v2 · Uvicorn + uvloop

**API surface**

12 REST router-модулей: auth · onboarding · exercises · protocols · workouts · progress · gamification · challenges · feed · profile · notifications · settings

**Domain model**

22 SQLAlchemy-модели в 5 доменах (Users / Training / Social / Gamification / Notifications), 23 Alembic-миграции, каталог 200+ упражнений с health-restriction-aware alternatives

**Training engine**

Protocol → week → day → exercise hierarchy · workout session lifecycle (start / log set / complete / abandon) · progressive overload · personal records · RPE-trend с deload suggestions · volume-by-muscle-group analytics

**Async layer (Celery beat)**

Workout reminders (per-user hour) · streak resets · challenge expiration · auto-moderation отрепорченных постов · weekly progress summary через Telegram-бот · social-event notifications (likes / comments / follows / PRs)

**Auth + rate limit**

Telegram WebApp initData валидация (HMAC-SHA256) · Redis sliding-window rate limiter на всех mutation endpoints

**Social layer**

Feed (recent / popular / following) · posts с likes/comments · user follows · auto-moderation отрепорченного контента

**Observability + CI**

Prometheus metrics · 4-stage GitLab CI (lint → test → build → deploy) · self-hosted runner · auto-migrations after deploy

**i18n**

ru · en · be · kk — полная локализация backend-сообщений

---

### 📦 Public projects

#### [VitaBalance](https://github.com/StailFX/VitaBalance) · TypeScript + FastAPI + PostgreSQL

Веб-сервис оценки витаминно-минерального баланса с персонализированными рекомендациями по питанию. Full-stack:
- **Frontend:** React 19 + TypeScript + Vite — дашборды анализа дефицитов, рекомендации рецептов, meal planner, light/dark theme
- **Backend:** FastAPI + async SQLAlchemy — auth, обработка лабораторных данных, симптомный опросник
- **Database:** PostgreSQL — ~20 витаминов/минералов, 94 продукта, 60 рецептов, 108 symptom mappings
- **Infra:** Docker Compose + nginx, production-ready

#### [PriceSpy](https://github.com/StailFX/PriceSpy) · Python + Docker

Web-приложение для отслеживания цен с CI/CD pipeline (Azure Pipelines), контейнеризацией Docker и шаблонизированным UI. Структура `src/` + `templates/` + `docs/`.

#### [Ozon-Parsing](https://github.com/StailFX/Ozon-Parsing) · Python

Web-scraper для ozon.ru: на вход список товаров (`names.txt`), на выход CSV с собранной информацией. Минимальный, фокус на быстрый сбор данных.

#### [RocketProblem](https://github.com/StailFX/RocketProblem) · Jupyter

Курсовая по численным методам — расчёт траектории 30 кг projectile с учётом drag, оптимизация угла запуска (30°-80°), визуализация trajectories. Применение numerical integration на практике.

---

### 🛠 Tech I work with

**Languages**

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Go](https://img.shields.io/badge/Go-00ADD8?style=flat&logo=go&logoColor=white)
![C++](https://img.shields.io/badge/C++-00599C?style=flat&logo=cplusplus&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat&logo=typescript&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat&logo=postgresql&logoColor=white)

**ML / Data**

![CatBoost](https://img.shields.io/badge/CatBoost-FFCC00?style=flat&logo=catboost&logoColor=black)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat&logo=scikit-learn&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-150458?style=flat&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat&logo=numpy&logoColor=white)
![Keras](https://img.shields.io/badge/Keras-D00000?style=flat&logo=keras&logoColor=white)

**Backend / Infra**

![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat&logo=fastapi&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-336791?style=flat&logo=postgresql&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)
![Nginx](https://img.shields.io/badge/Nginx-009639?style=flat&logo=nginx&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat&logo=linux&logoColor=black)
![Git](https://img.shields.io/badge/Git-F05032?style=flat&logo=git&logoColor=white)

**Monitoring / Cloud**

![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=flat&logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?style=flat&logo=grafana&logoColor=white)
![Yandex Cloud](https://img.shields.io/badge/Yandex_Cloud-5282FF?style=flat&logo=yandexcloud&logoColor=white)

**Дополнительно:** asyncio · WebSocket (Binance L2) · CI/CD (GitLab, Azure Pipelines) · WireGuard · systemd · Jinja2 · React + Vite · async SQLAlchemy · SVG/Canvas data viz

---

### 🏆 Competitive programming & cases

- **ICPC Southern Volga Russia 2026** — 3 командных размещения
- **Cup IT 2024** — диплом (кейс-чемпионат)
- [Codeforces](https://codeforces.com/profile/stailfx) · [ACMP](https://acmp.ru/index.asp?main=user&id=243256) — алгоритмические задачи на C++/Python

Опыт командных кейс-чемпионатов: чаще всего в роли аналитика и организатора командной работы.

---

### 📊 GitHub

![Stats](https://github-readme-stats.vercel.app/api?username=StailFX&theme=tokyonight&hide_border=true&show_icons=true&include_all_commits=true&count_private=true)
![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=StailFX&theme=tokyonight&hide_border=true&layout=compact&langs_count=8)

---

### 🎓 Education

**Казанский (Приволжский) федеральный университет** · Институт вычислительной математики и информационных технологий · Прикладная математика и информатика · 2023 — 2027

---

### 💼 Experience

| Period | Role | Where |
|---|---|---|
| Июнь 2025 — настоящее время | **CEO + Backend Developer + PM + Аналитик** | GymBro (резидент IT Park Казань) |
| Июль 2024 — Декабрь 2024 | **Техник-сборщик** (тестирование, прошивка, OS-конфигурирование) | ICL-КПО ВС, Казань |

---

### 📫 Contact

- 📧 Email: [systemniki42@gmail.com](mailto:systemniki42@gmail.com)
- 💬 Telegram: [@StailFX](https://t.me/StailFX)
- 📱 Phone: +7 (965) 617-93-81
- 📍 Казань, Россия · open to remote
- 📁 [Portfolio (Google Drive)](https://drive.google.com/drive/folders/1NvHgLY66WcYCa5AUpqKOb-kiYmU5XN3E)

<sub>Open to: <b>Data Scientist</b> · <b>Quant Developer</b> · <b>ML Engineer</b> · <b>Backend Developer</b> roles · stack-aligned with Python / Postgres / CatBoost ecosystem · Kazan local или fully remote.</sub>
