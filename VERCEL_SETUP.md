# Настройка Vercel для MovieBot Web App

## Проблема: Web App не открывается и нет логов

## Решение:

### 1. Обновите настройки проекта в Vercel

1. Зайдите на [vercel.com](https://vercel.com)
2. Откройте проект `moviebot-webapp`
3. Перейдите в **Settings** → **Git**
4. Убедитесь, что репозиторий: `zapnikita95/moviebot-webapp`
5. Убедитесь, что ветка: `main`
6. **Root Directory**: оставьте пустым (или `/`)

### 2. Проверьте настройки Build & Development Settings

1. В **Settings** → **General**
2. **Framework Preset**: выберите "Other" или "Static"
3. **Build Command**: оставьте пустым
4. **Output Directory**: оставьте пустым (или `/`)
5. **Install Command**: оставьте пустым

### 3. Пересоберите проект

1. Перейдите в **Deployments**
2. Найдите последний деплой
3. Нажмите **Redeploy** (три точки → Redeploy)
4. Или сделайте новый коммит в GitHub — Vercel автоматически пересоберет проект

### 4. Проверьте логи

1. В **Deployments** выберите последний деплой
2. Откройте вкладку **Logs**
3. Там должны быть логи сборки и деплоя

### 5. Проверьте домен

1. В **Settings** → **Domains**
2. Убедитесь, что домен `moviebot-webapp.vercel.app` активен
3. Если нет — добавьте его

### 6. Если проблема сохраняется

Проверьте:
- Правильный ли URL в BotFather: `https://moviebot-webapp.vercel.app/`
- Открывается ли сайт напрямую в браузере (не через Telegram)
- Есть ли ошибки в консоли браузера при открытии Web App

## Текущая структура проекта:

```
moviebot-webapp/
├── index.html      # Главный файл Web App
├── README.md       # Документация
├── vercel.json     # Конфигурация Vercel
└── .gitignore      # Игнорируемые файлы
```

## Конфигурация Vercel (vercel.json):

```json
{
  "version": 2,
  "builds": [
    {
      "src": "index.html",
      "use": "@vercel/static"
    }
  ],
  "routes": [
    {
      "src": "/(.*)",
      "dest": "/$1"
    }
  ]
}
```

Эта конфигурация говорит Vercel, что это статический сайт, и все запросы должны возвращать файлы из корня проекта.

