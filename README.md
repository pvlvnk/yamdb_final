[![Django-app workflow](https://github.com/pvlvnk/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)](https://github.com/pvlvnk/yamdb_final/actions/workflows/yamdb_workflow.yml)

# Проект YaMDb
## Описание

Проект YaMDb собирает отзывы пользователей на произведения. Произведения делятся на категории: «Книги», «Фильмы», «Музыка».
Сами произведения в YaMDb не хранятся, здесь нельзя посмотреть фильм или послушать музыку.
В каждой категории есть произведения: книги, фильмы или музыка.
Произведению может быть присвоен жанр (Genre) из списка предустановленных. Новые жанры может создавать только администратор.
Благодарные или возмущённые пользователи оставляют к произведениям текстовые отзывы (Review) и ставят произведению оценку в диапазоне от одного до десяти (целое число); из пользовательских оценок формируется усреднённая оценка произведения — рейтинг (целое число). На одно произведение пользователь может оставить только один отзыв.

## Пользовательские роли

- Аноним — может просматривать описания произведений, читать отзывы и комментарии.
- Аутентифицированный пользователь (user) — может, как и Аноним, читать всё, дополнительно он может публиковать отзывы и ставить оценку произведениям (фильмам/книгам/песенкам), может комментировать чужие отзывы; может редактировать и удалять свои отзывы и комментарии. Эта роль присваивается по умолчанию каждому новому пользователю.
- Модератор (moderator) — те же права, что и у Аутентифицированного пользователя плюс право удалять любые отзывы и комментарии.
- Администратор (admin) — полные права на управление всем контентом проекта. Может создавать и удалять произведения, категории и жанры. Может назначать роли пользователям.
- Суперюзер Django — обладет правами администратора (admin).

## Ресурсы API YaMDb

- Ресурс auth: аутентификация.
- Ресурс users: пользователи.
- Ресурс titles: произведения, к которым пишут отзывы (определённый фильм, книга или песенка).
- Ресурс categories: категории (типы) произведений («Фильмы», «Книги», «Музыка»).
- Ресурс genres: жанры произведений. Одно произведение может быть привязано к нескольким жанрам.
- Ресурс reviews: отзывы на произведения. Отзыв привязан к определённому произведению.
- Ресурс comments: комментарии к отзывам. Комментарий привязан к определённому отзыву.

 ## Установка

- Клонируйте новый репозиторий себе на компьютер.
- зайдите в папку infra командой: cd infra
- запустите приложения в контейнерах командой docker-compose up
- Выполните миграции в контейнерах командами:
docker-compose exec web python manage.py makemigrations
docker-compose exec web python manage.py migrate

## Примеры

Примеры запросов по API:
```
- [GET] /api/v1//titles/{title_id}/reviews/ - Получить список всех отзывов.
```
```
- [POST]  /api/v1//titles/{title_id}/reviews/ - Добавить новый отзыв. Пользователь может оставить только один отзыв на произведение.
```
```
- [GET] /api/v1/titles/{title_id}/reviews/{review_id}/ - Получить отзыв по id для указанного произведения.
```
```
- [PATCH] /api/v1/titles/{title_id}/reviews/{review_id}/ - Частично обновить отзыв по id.
```
```
- [DELETE] /api/v1/titles/{title_id}/reviews/{review_id}/ - Удалить отзыв по id.
```
