FASTAPI + DOCKER COMPOSE — ИНСТРУКЦИЯ

1. Установите и запустите Docker Desktop.
2. Откройте терминал в папке проекта.
3. Выполните:
   docker compose up --build

4. Откройте:
   http://localhost:8000
   http://localhost:8000/docs
   http://localhost:8000/health/db

5. Для проверки Celery:
   - В Swagger откройте POST /tasks.
   - Нажмите Try it out, затем Execute.
   - В другом терминале выполните:
     docker compose logs -f celery_worker
   - В логах должна появиться строка "Задача выполнена: Hello from Docker!"

Полезные команды:
   docker compose ps
   docker compose logs app
   docker compose logs celery_worker
   docker compose down

ОСТОРОЖНО:
   docker compose down -v удаляет том PostgreSQL вместе с сохранёнными данными.
   Обычный docker compose down именованный том postgres_data сохраняет.

Переменные:
   .env.docker используется контейнерами. Внутри Docker адреса сервисов —
   db и redis, а не localhost.
   .env предназначен для локального запуска на компьютере.
