# Перенос Rocket Agency в GitHub

## 1. Создайте репозиторий

На GitHub нажмите **New repository**, задайте название (например, `rocket-agency`) и создайте пустой репозиторий без автоматически добавленных README, лицензии и `.gitignore`.

## 2. Загрузите проект через Git

В распакованной папке проекта выполните:

```bash
git init
git add .
git commit -m "Initial Rocket Agency website"
git branch -M main
git remote add origin https://github.com/USERNAME/rocket-agency.git
git push -u origin main
```

Замените `USERNAME` на имя аккаунта GitHub. Если папка уже является Git-репозиторием, не выполняйте `git init`; достаточно заменить или добавить внешний remote.

## 3. Проверьте содержимое репозитория

В GitHub должны быть видны `app`, `components`, `data`, `public`, `scripts`, `worker`, `package.json`, `package-lock.json` и документация. Папки `node_modules`, `.next`, `dist`, `.sites-runtime` и файлы `.env` загружаться не должны — они исключены через `.gitignore`.

## 4. Автоматические проверки

Файл `.github/workflows/quality.yml` запускает ESLint, TypeScript и production-сборку при каждом push и pull request в ветку `main`.

## 5. Публикация

GitHub хранит исходный код, но обычный GitHub Pages предназначен для статических файлов и не запускает Cloudflare Worker этого проекта. Возможные варианты:

1. продолжить публиковать сайт через ChatGPT Sites;
2. подключить GitHub-репозиторий к Cloudflare Workers и использовать `npm run build`;
3. подготовить отдельную статическую экспортную версию для GitHub Pages.

Текущий рабочий сайт: <https://alina-github-site.valeevaalina214.chatgpt.site/>

## Проверка на другом компьютере

```bash
git clone https://github.com/USERNAME/rocket-agency.git
cd rocket-agency
npm ci
npm run lint
npm run typecheck
npm run build
npm run dev
```

Для текущей версии сайта переменные окружения и секреты не требуются.
