# CRM-система для строительной организации

## Техническое задание на разработку серверной части web-приложения (backend).

**Описание задачи:** необходимо разработать бэкенд для web-приложения, выполняющего функции CRM-системы.
**Взаимодействие с интерфейсом пользователя:** взаимодействие осуществляется через API. Фронтенд реализован на React JS.
**Хранение данных:** в процессе разработки для целей тестирования взаимодействия с фронтом можно использовать любую СУБД. 
По завершении реализации данного ТЗ необходимо осуществить интеграцию с существующей БД, выполненной на MySQL. 

### Предварительная структура БД

| Таблица             | Поле            | Тип данных | Внешняя таблица |
| ------------------- | --------------- | ---------- | --------------- |
| **Users**           | id              |            |                 |
|                     | role_id         | FK         | Roles           |
|                     | name            | text       |                 |
|                     | email           | text       |                 |
|                     | password        | text       |                 |
|                     | last_active     | date       |                 |
| **AuthTokens**      | id              |            |                 |
|                     | key             | text       |                 |
|                     | user_id         |            |                 |
| **Roles**           | id              |            |                 |
|                     | name            | text       |                 |
|                     | permissions     | JSON       |                 |
| **CashboxIncomes**  | id              |            |                 |
|                     | user_id         | FK         | Users           |
|                     | date            | date       |                 |
|                     | description     | text       |                 |
|                     | bank_value      | number     |                 |
|                     | cash_value      | number     |                 |
|                     | project_id      | FK         | Projects        |
|                     | category        | ENUM       |                 |
|                     | comments        | text       |                 |
|                     | status          | ENUM       |                 |
| **CashboxExpenses** | id              |            |                 |
|                     | user_id         | FK         | Users           |
|                     | date            | date       |                 |
|                     | description     | text       |                 |
|                     | cash_value      | number     |                 |
|                     | project_id      | FK         | Projects        |
|                     | category        | ENUM       |                 |
|                     | team            | text       |                 |
|                     | comments        | text       |                 |
|                     | status          | ENUM       |                 |
| **Projects**        | id              |            |                 |
|                     | name            | text       |                 |
|                     | customer        | FK         | Contractors     |
|                     | organization    | FK         | Organizations   |
|                     | cost            | number     |                 |
|                     | project_manager | FK         | Managers        |
|                     | sales_manager   | FK         | Managers        |
|                     | start_plan      | date       |                 |
|                     | start_fact      | date       |                 |
|                     | finish_plan     | date       |                 |
|                     | finish_fact     | date       |                 |
|                     | budget_bank     | number     |                 |
|                     | budget_cash     | number     |                 |
|                     | comments        | text       |                 |
|                     | warranty_start  | date       |                 |
|                     | warranty_finish | date       |                 |
|                     | status          | ENUM       |                 |


### Необходимые API:
getUserProfile – запрос профиля пользователя по токену авторизации
getCashboxIncomes – запрос списка доходов
getCashboxIncomes - запрос списка расходов
getProjectsNames – запрос перечня наименований проектов
postAuthToken – создание токена авторизации
postCashboxIncome – создание записи в таблице доходов
postCashboxExpense - создание записи в таблице расходов
patchCashboxIncome – внесение изменений в запись таблицы доходов
patchCashboxExpense – внесение изменений в запись таблицы расходов
patchCashboxIncomesStatus – изменение статуса записи таблицы доходов
patchCashboxExpensesStatus - – изменение статуса записи таблицы расходов
deleteToken – удаление токена авторизации
deleteCashboxIncomes – удаление записи таблицы доходов
deleteCashboxExpenses – удаление записи таблицы расходов

### Роли и права пользователей


### Дополнительные требования
Действия пользователей должны быть ограничены в соответствии с заданной ролью.
Все запросы и входные параметры должны валидироваться.
Сервер должен писать логи действий пользователей.

