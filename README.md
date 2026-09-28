# Restoran (курсовая)

Веб-приложение для ресторана: вход и регистрация, меню, заказы, бронирование столиков, профиль. Есть роль администратора. 

## Из чего состоит

Проект разбит на две папки:

- `restoran-master/` — бэкенд. Spring Boot 3, Java 17, Maven, PostgreSQL, JWT-авторизация.
- `restoran-front-master/` — фронтенд. Angular 19, страницы login, register, home, profile.


## Запуск

Сначала нужно, чтобы крутился PostgreSQL. Подключение настроено в `restoran-master/src/main/resources/application.properties`: база `postgres`, пользователь `postgres`, пароль `postgres`. Если у тебя другие креды — меняй прямо там.

Бэкенд:

```bash
cd restoran-master
mvn spring-boot:run
```

Запустится на http://localhost:8080.

Фронтенд в режиме разработки:

```bash
cd restoran-front-master
npm install
ng serve
```

И открыть http://localhost:4200. Адрес API лежит в `src/environments/environment.ts`.

## Что внутри

- Регистрация и вход по логину/паролю. После входа бэкенд отдаёт JWT-токен, фронт подставляет его через интерцептор.
- Меню и карточки блюд.
- Заказы: оформить и посмотреть свои.
- Бронирование столиков (дата, количество гостей).
- Профиль пользователя.
- Админка: видит все брони и может их редактировать.

По бэкенду: `AuthController` (`/auth-api`), `RegistrationController` (`/reg-api`), дальше `MenuController`, `OrderController`, `BookingController`, `ProductController`, `AdminController`, `UserController`. Работа с базой через JPA-репозитории.

