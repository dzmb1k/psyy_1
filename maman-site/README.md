# Сайт психолога Анны Ветровой

Готовый одностраничный сайт — всё в одном файле `index.html`.

## Быстрый старт

Просто откройте `index.html` в браузере — никаких зависимостей, никакой сборки.

## Структура файла

```
index.html
├── <head>         — шрифты Google Fonts, все CSS-стили
├── <body>         — HTML-разметка всех секций
└── <script>       — весь JavaScript (курсор, анимации, форма, Three.js)
```

## Как редактировать

### Изменить текст / данные
Откройте `index.html` и найдите нужную секцию по комментарию:

| Секция       | Комментарий в коде          |
|--------------|-----------------------------|
| Шапка        | `<!-- NAVBAR -->`           |
| Герой        | `<!-- HERO -->`             |
| Обо мне      | `<!-- ABOUT -->`            |
| Услуги       | `<!-- SERVICES -->`         |
| Отзывы       | `<!-- TESTIMONIALS -->`     |
| Блог         | `<!-- BLOG -->`             |
| FAQ          | `<!-- FAQ -->`              |
| Форма записи | `<!-- BOOKING -->`          |
| Подвал       | `<!-- FOOTER -->`           |

### Изменить цвета
В начале `<style>` найдите блок `:root { ... }` и поменяйте переменные:

```css
:root {
  --terracotta: #C97B55;   /* Основной акцентный цвет */
  --sage: #8B9E7C;         /* Зелёный / вторичный */
  --cream: #F5F0E8;        /* Светлый фон */
  --deep: #2C2416;         /* Тёмный текст */
}
```

### Изменить цены
Найдите в секции `<!-- SERVICES -->` теги с классом `.service-price` и `.service-duration`.

### Подключить реальную форму (EmailJS)
1. Зарегистрируйтесь на https://emailjs.com (бесплатно до 200 писем/мес)
2. Создайте сервис и шаблон письма
3. В конце `index.html` найдите функцию `submitForm` и замените `setTimeout` на:

```js
emailjs.send('YOUR_SERVICE_ID', 'YOUR_TEMPLATE_ID', {
  name: document.getElementById('fname').value,
  email: document.getElementById('email').value,
  phone: document.getElementById('phone').value,
  service: document.getElementById('service').value,
  message: document.getElementById('message').value,
}).then(() => { /* показать toast */ });
```

4. Добавьте в `<head>`:
```html
<script src="https://cdn.jsdelivr.net/npm/@emailjs/browser@3/dist/email.min.js"></script>
<script>emailjs.init('YOUR_PUBLIC_KEY');</script>
```

### Заменить фотографии
Найдите теги `<img>` с ссылками на Unsplash и замените `src` на путь к своим фото:
```html
<img src="./images/anna-photo.jpg" alt="Анна Ветрова">
```

### Изменить дышащий цветок
Найдите `<!-- BREATHING WIDGET -->` и отредактируйте SVG-фигуру или параметры анимации в функции `initBreath()` в конце скрипта. Настройте длительность фаз (мс):
```js
{ name: 'вдох',    duration: 4000, ... },
{ name: 'держите', duration: 1400, ... },
{ name: 'выдох',   duration: 4000, ... },
{ name: 'пауза',   duration: 1400, ... },
```

## Деплой

### Netlify (проще всего — бесплатно)
1. Зайдите на https://netlify.com
2. Перетащите папку проекта в браузер на странице деплоя
3. Готово — сайт онлайн за 30 секунд

### GitHub Pages (бесплатно)
1. Создайте репозиторий на GitHub
2. Загрузите `index.html`
3. Settings → Pages → Branch: main → Save

### Своё хостинг
Загрузите `index.html` в корень сервера через FTP/SFTP.

## Зависимости (загружаются автоматически из CDN)
- Three.js r128 — 3D-сцена на hero
- Google Fonts — Cormorant Garamond + DM Sans

Всё остальное написано на чистом JS — никаких npm, никакой сборки.
