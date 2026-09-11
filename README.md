# Zoomie — прототип приложения для кота

Статический сайт: один `index.html` и папка `assets` (видео, шрифты, звуки).
Ничего собирать не нужно — файл открывается напрямую.

## Посмотреть локально

Двойной клик по `index.html`. Или, если хочется «как на сервере»:

    cd ~/Documents/zoomie
    python3 -m http.server 8000

и открыть http://localhost:8000

## Опубликовать

Один раз — авторизация:

    gh auth login          # GitHub.com → HTTPS → Login with a web browser

Связать папку с репозиторием (если репозиторий уже создан на github.com):

    cd ~/Documents/zoomie
    git init
    git remote add origin https://github.com/ТВОЙ-НИК/ТВОЙ-РЕПО.git
    git branch -M main

Дальше — обычный цикл, повторяется при каждом изменении:

    git add .
    git commit -m "что изменилось"
    git push -u origin main    # в первый раз, потом просто git push

Публикация:

- **GitHub Pages** — в репозитории Settings → Pages → Source: «Deploy from a branch»,
  ветка `main`, папка `/ (root)`. Адрес будет `ТВОЙ-НИК.github.io/ТВОЙ-РЕПО`.
- **Vercel** — vercel.com → Add New Project → выбрать репозиторий →
  Framework Preset: **Other** → Deploy.

Оба варианта публичные: ссылку сможет открыть любой.

## Что внутри

- `index.html` — весь прототип: все экраны, стили и скрипты в одном файле
- `assets/` — видео котика (webm с прозрачностью), шрифты, звуки мяуканья
- `.nojekyll` — просит GitHub Pages отдавать файлы как есть

## Главный экран

Свайп по котику переключает состояние: спокойствие → агрессия → испуг и по кругу,
в обе стороны бесконечно. Стрелки влево-вправо на клавиатуре проходят по экранам:
splash → activation → scan → home.
