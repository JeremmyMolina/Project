# Todo App

Данное приложение - это простая API для управления задачами. Вы можете создавать, читать, обновлять и удалять задачи, используя RESTful архитектуру. В этом проекте используются FastAPI и SQLAlchemy для обработки запросов и взаимодействия с базой данных.

## Содержание

1. [Предпосылки](#предпосылки)
2. [Установка](#установка)
3. [Структура проекта](#структура-проекта)
4. [Использование API](#использование-api)
5. [Примеры запросов](#примеры-запросов)
6. [Запуск приложения](#запуск-приложения)
7. [Дополнительная информация](#дополнительная-информация)
8. [Лицензия](#лицензия)

## Предпосылки

Перед тем как начать, убедитесь, что у вас установлены:

- Python 3.7 или выше
- PostgreSQL или любая другая база данных, поддерживаемая SQLAlchemy
- pip

## Установка

1. Клонируйте репозиторий:
bash
   git clone https://github.com/yourusername/my-fastapi-project.git
   cd my-fastapi-project/todo_app

2. Установите зависимости:
bash
   pip install -r requirements.txt

3. Создайте базу данных и настройте файл `database.py` для подключения к вашей базе данных.

4. Выполните миграции для создания необходимых таблиц в базе данных:
bash
   python -m models

## Структура проекта

todo_app/
│
├── main.py         # Основной файл приложения
├── models.py       # Определение модели базы данных
├── database.py     # Конфигурация подключения к базе данных
├── requirements.txt # Зависимости проекта
└── README.md       # Документация

## Использование API

### Основные маршруты

- `GET /` - Приветственное сообщение.
- `GET /items` - Получить список всех задач.
- `GET /items/{item_id}` - Получить задачу по ID.
- `GET /items_filter` - Фильтрация задач по завершенности.
- `POST /items` - Создать новую задачу.
- `PUT /items/{item_id}` - Обновить существующую задачу по ID.
- `DELETE /items/{item_id}` - Удалить задачу по ID.

## Примеры запросов

### Получение списка задач
bash
GET /items

**Ответ:*
json
[
    {
        "id": 1,
        "title": "Buy groceries",
        "description": "Milk, Cheese, Pizza, Fruit",
        "completed": false
    },
    {
        "id": 2,
        "title": "Wash the car",
        "completed": false
    }
]

### Создание новой задачи
bash
POST /items
Content-Type: application/json
{
    "title": "New Task",
    "description": "Task description",
    "completed": false
}

**Ответ:**
json
{
    "id": 3,
    "title": "New Task",
    "description": "Task description",
    "completed": false
}

### Обновление задачи
bash
PUT /items/1
Content-Type: application/json
{
    "title": "Updated Task",
    "description": "Updated description",
    "completed": true
}

**Ответ:**
json
{
    "id": 1,
    "title": "Updated Task",
    "description": "Updated description",
    "completed": true
}

### Удаление задачи
bash
DELETE /items/1

**Ответ:**
json
{
    "message": "Item deleted"
}

## Запуск приложения

Запустите сервер с помощью Uvicorn:
bash
uvicorn main:app --reload

Теперь приложение будет доступно по адресу `http://localhost:8000`.

## Дополнительная информация

Вы можете использовать Postman или cURL для тестирования вашего API. Обязательно ознакомьтесь с документацией FastAPI для более глубокого понимания возможностей, которые она предлагает.
