# IndividualsApi

4. Проверка через Keycloak Admin Console
   Откройте http://localhost:9091/admin

Войдите под admin/admin

Проверьте:

Существует ли реалм individuals-realm

Существует ли клиент individuals-api

В настройках клиента:

Access Type: confidential

Service Accounts Enabled: ON

Direct Access Grants Enabled: ON

Во вкладке Credentials - секрет клиента (должен совпадать с your-client-secret)

1. Регистрация пользователя
   bash
   curl -X POST http://localhost:9090/v1/auth/registration \
   -H "Content-Type: application/json" \
   -d '{
   "email": "user1@example.com",
   "password": "Password123",
   "confirm_password": "Password123",
2. "first_name":"Artem",
3. "last_name":"Guschin",
4. "role":"admin"
   }'
2. Логин пользователя
   bash
   curl -X POST http://localhost:9090/v1/auth/login \
   -H "Content-Type: application/json" \
   -d '{
   "email": "user1@example.com",
   "password": "Password123"
   }'
3. Обновление токена
   bash
   curl -X POST http://localhost:9090/v1/auth/refresh-token \
   -H "Content-Type: application/json" \
   -d '{
   "refresh_token": "ВАШ_REFRESH_TOKEN"
   }'
4. Получение данных пользователя
   bash
   curl -X GET http://localhost:9090/v1/auth/me \
   -H "Authorization: Bearer ВАШ_ACCESS_TOKEN"
5. Тест ошибки (неверный пароль)
   bash
   curl -X POST http://localhost:9090/v1/auth/login \
   -H "Content-Type: application/json" \
   -d '{
   "email": "user1@example.com",
   "password": "WrongPassword"
   }'