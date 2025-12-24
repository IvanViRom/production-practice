# REST API для системы управления задачами

## Установка
1. Установите Node.js (если его у вас нет)
2. В терминале проекта напишите команду:
npm install
## Запуск проекта
1. Скомпилируйте TypeScripts:
npm run build
2. запустите сервер;
npm start
Сервер будет доступен по адресу: http://localhost:3000

## Примеры запросов к API
Используйте curl для тестирования

1. Получить список всех задач (GET /api/tasks)
curl http://localhost:3000/api/tasks
"(Invoke-WebRequest -Method GET -Uri "http://localhost:3000/api/tasks").Content"

2. Получить задачу по её идентификатору (GET /api/tasks/:id)
curl http://localhost:3000/api/tasks1
"(Invoke-WebRequest -Method GET -Uri "http://localhost:3000/api/tasks/1").Content"

3. Создать новую задачу (POST /api/tasks)
curl -X POST http://localhost:3000/api/tasks 
-H "Content-Type: application/json" 
-d '{"title": "Новая задача", "description": "Описание задачи"}'
"(Invoke-WebRequest -Method POST -Uri "http://localhost:3000/api/tasks" -Headers @{ "Content-Type" = "application/json" } -Body '{ "title": "New task", "description": "Description of the task" }').Content"

4. Обновить существующую задачу (PUT /api/tasks/:id)
curl -X PUT http://localhost:3000/api/tasks/1 
-H "Content-Type: application/json" 
-d '{"title": "Обновленная задача", "completed": true}'
"(Invoke-WebRequest -Method PUT -Uri "http://localhost:3000/api/tasks/1" -Headers @{ "Content-Type" = "application/json" } -Body '{ "title": "Updated task", "completed": true }').Content"

5. Удалить задачу (DELETE /api/tasks/:id)
curl -X DELETE http://localhost:3000/api/tasks/1
"(Invoke-WebRequest -Method DELETE -Uri "http://localhost:3000/api/tasks/1").Content"

Обработка ошибок: Возвращаются коды 400 (некорректные данные), 404 (не найдено), 500 (ошибка сервера)
