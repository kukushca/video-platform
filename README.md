# Документация API платформы YADRO

В данном документе описано REST API для взаимодействия фронтенда с бэкендом (Flask).

* Ссылка на сайт: https://clinquant-klepon-a44054.netlify.app/
* Базовый URL API: https://video-platform-kqvw.onrender.com
---

## 1. Авторизация и пользователи

### Регистрация нового пользователя
* URL: /register
* Метод: POST
* Тело запроса (JSON):
{
  "email": "user@example.com",
  "password": "secretpassword",
  "first_name": "Иван",
  "last_name": "Иванов"
}
* Успешный ответ (201): {"message": "Регистрация прошла успешно!"}

### Вход в систему (Авторизация)
* URL: /login
* Метод: POST
* Тело запроса (JSON):
{
  "email": "user@example.com",
  "password": "secretpassword"
}
* Успешный ответ (200): Возвращает JWT-токен и данные пользователя.

---

## 2. Работа с видео

### Получение ленты видео
* URL: /videos
* Метод: GET
* Успешный ответ (200): Возвращает массив со списком всех видео.

### Загрузка нового видео
* URL: /videos/upload
* Метод: POST
* Заголовки: Authorization: Bearer <JWT-токен>
* Тело запроса (FormData): title (строка), video (файл).

### Потоковое воспроизведение видео (Стриминг)
* URL: /videos/stream/<filename>
* Метод: GET
* Описание: Отдает видеофайл частями для поддержки перемотки в плеере.

---

## 3. Чат «Вопрос / ответ»

### Получение сообщений чата
* URL: /chat
* Метод: GET

### Отправка сообщения
* URL: /chat
* Метод: POST
* Заголовки: Authorization: Bearer <JWT-токен>
* Тело запроса (JSON): {"text": "Текст сообщения"}