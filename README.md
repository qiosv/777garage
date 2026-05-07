# 777 Garage Website

Сайт на React + TypeScript + Vite.

## 1) Локальный запуск (localhost)

Требования:
- Node.js 20 LTS
- npm (устанавливается вместе с Node.js)

Команды:

```bash
npm install
npm run dev
```

После запуска открой:
- `http://localhost:5173`

## 2) Сборка production

```bash
npm install
npm run build
npm run preview
```

Production preview откроется на:
- `http://localhost:4173`

## 3) Постоянная работа на сервере (рекомендуется Docker)

В проекте уже добавлены:
- `Dockerfile`
- `docker-compose.yml`
- `nginx/default.conf`

Запуск на сервере:

```bash
docker compose up -d --build
```

Сайт будет доступен на:
- `http://<IP_сервера>`

Автоподнятие после перезагрузки сервера уже включено:
- `restart: unless-stopped`

Обновление после изменений:

```bash
docker compose down
docker compose up -d --build
```

## 4) Что уже подготовлено в проекте

- Все нужные скрипты запуска в `package.json`
- Базовые docker-файлы для деплоя
- Конфиг nginx для SPA
- Заполнена папка `public/images` (чтобы не было битых изображений)

## 5) Если на компьютере не запускается npm

Проверь:
- установлен ли Node.js: `node -v`
- установлен ли npm: `npm -v`

Если команд нет, установи Node.js 20 LTS и снова выполни:

```bash
npm install
npm run dev
```

## 6) Как постоянно добавлять фото и посты

Теперь `Gallery` и `Blog` читают данные из файлов в `public/content`:

- `public/content/gallery.json` — контент галереи
- `public/content/blog-posts.json` — посты блога

### Добавить фото в галерею

1. Скопируй картинку в `public/images` (например `public/images/gallery-777/`)  
2. Добавь объект в массив `portfolio` внутри `public/content/gallery.json` (для каждого языка `en` / `pl` / `es` / `ru`, если нужны переводы):

```json
{
  "image": "/images/your-photo.jpg",
  "title": "Название",
  "description": "Короткое описание"
}
```

### Добавить пост в блог

1. Скопируй обложку в `public/images`  
2. Добавь объект в массив `en` внутри `public/content/blog-posts.json`:

```json
{
  "id": 10,
  "title": "Заголовок поста",
  "excerpt": "Короткое описание для карточки",
  "content": "<p>Текст поста...</p><h2>Подзаголовок</h2><p>Еще текст...</p>",
  "image": "/images/blog-new-cover.jpg",
  "category": "Supercars",
  "author": "777 Garage Team",
  "date": "March 21, 2026",
  "slug": "unique-post-slug"
}
```

Важно:
- `id` должен быть уникальным
- `slug` должен быть уникальным (используется в URL)
- `content` поддерживает HTML (`<p>`, `<h2>`, и т.д.)

## 7) Cloudflare Pages: автодеплой при каждом push в Git

Сайт уже собирается командой `npm run build`, результат в папке `dist`. Чтобы **777garage.com** обновлялся сам после `git push`, свяжи этот репозиторий с тем же проектом Pages **777-garage**.

### 7.1 Установи Git (если команда `git` не находится)

1. Скачай и установи [Git for Windows](https://git-scm.com/download/win).
2. Закрой и снова открой терминал (или Cursor).
3. Проверь: `git --version`.

### 7.2 Создай репозиторий на GitHub

1. Зайди на [github.com](https://github.com) → **New repository** (например имя `777-garage-web`).
2. **Без** README / .gitignore / license (они уже есть локально).
3. Скопируй URL репозитория (HTTPS или SSH).

### 7.3 Первый push с твоего ПК

В PowerShell из папки проекта (`C:\Users\23\Desktop\app`):

```powershell
cd C:\Users\23\Desktop\app
git init
git add .
git commit -m "Initial commit: 777 Garage site"
git branch -M main
git remote add origin https://github.com/ТВОЙ_ЛОГИН/777-garage-web.git
git push -u origin main
```

Подставь свой URL вместо примера. При запросе логина GitHub лучше использовать **Personal Access Token** вместо пароля ([инструкция](https://docs.github.com/en/authentication)).

**Не коммить секреты:** файлы `.env`, `.env.local` уже в `.gitignore`. Шаблон переменных — `.env.example`.

### 7.4 Подключи Git к существующему проекту Pages

1. [Cloudflare Dashboard](https://dash.cloudflare.com) → **Workers & Pages** → проект **777-garage**.
2. **Settings** → раздел про сборки / **Connect to Git** (или при создании связи с Git следуй мастеру).
3. Разреши доступ Cloudflare к GitHub и выбери репозиторий.
4. Настройки сборки:
   - **Framework preset:** Vite (или None)
   - **Build command:** `npm run build`
   - **Build output directory:** `dist`
   - **Root directory:** `/` (если репозиторий — корень этого проекта)
   - **Production branch:** `main`
5. В **Settings → Environment variables** добавь (если нужна аналитика), для **Production** и при желании **Preview**:
   - `NODE_VERSION` = `22`
   - `VITE_GA_MEASUREMENT_ID` = твоё значение `G-...`
   - `VITE_GOOGLE_ADS_ID` = если используешь
6. Сохрани и дождись первого деплоя. Кастомный домен **777garage.com** останется привязанным к этому же проекту.

### 7.5 Как жить дальше

После настройки цикл такой:

1. Правки в Cursor → сохранить.
2. `git add` → `git commit` → `git push` в `main`.
3. Cloudflare сам соберёт проект и обновит сайт (обычно 1–3 минуты). Статус смотри во вкладке **Deployments** у проекта Pages.

Ручной деплой с ПК по-прежнему доступен: `npm.cmd run pages:deploy` (нужен `CLOUDFLARE_API_TOKEN`).
