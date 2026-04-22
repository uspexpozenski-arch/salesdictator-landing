# salesdictator.ru — Личная страница Андрея Семенюка

Статический лендинг. Директор отделов продаж, разработчик AI-систем.

## Стек

- Чистый HTML5 + CSS3 (без фреймворков и сборщиков)
- WebGL Fluid Simulation — [PavelDoGreat](https://github.com/PavelDoGreat/WebGL-Fluid-Simulation) (MIT), адаптирован: синяя палитра, canvas pointer-events:none
- Шрифты: Inter + JetBrains Mono (Google Fonts)

## Файлы

| Файл | Описание |
|------|----------|
| `index.html` | Вся страница |
| `style.css` | Стили: тёмная тема, синие акценты #3b82f6 |
| `fluid.js` | WebGL-эффект на фоне |
| `*.mp4` | Видео-аватар (Telegram-стиль) |

## Структура страницы

- **Hero** — двухколонный layout: слева имя + текст + статистика, справа аватар + system status terminal
- **// 01 Мой стек** — `$ cat skills.yml`
- **// 02 Мои проекты** — GetCount, Get-Poster, Whisper Pro, AI Global News
- **// 03 Кейсы канала** — кейсы из Telegram-канала @salesdictator
- **// 04 Услуги** — 8 направлений с SVG-иконками
- **// 05 Контакты** — terminal-блок + карточки (TG, WA, YouTube, Email) + hacker-кнопка

## Локальный запуск

```bash
python -m http.server 8765
# открыть http://localhost:8765
```

## Деплой

**Сервер:** `95.128.157.222` (Ubuntu 24.04)  
**Домен:** `salesdictator.ru` (регистратор: Beget)  
**Папка:** `/srv/salesdictator/`  
**Docker-compose:** `/root/n8n-compose/docker-compose.yml`

Инфраструктура: Docker + Traefik (reverse proxy) + Let's Encrypt SSL  
n8n живёт на `n8n.salesdictator.ru` — не трогать.

### Обновить файлы на сервере

```bash
scp index.html style.css fluid.js root@95.128.157.222:/srv/salesdictator/
```

### Перезапустить контейнер сайта

```bash
ssh root@95.128.157.222 "cd /root/n8n-compose && docker compose restart salesdictator"
```

### DNS (Beget — cp.beget.com)

| Тип | Хост | Значение |
|-----|------|----------|
| A | `@` | `95.128.157.222` |
| A | `www` | `95.128.157.222` |

Запись `n8n` уже есть — не трогать.
