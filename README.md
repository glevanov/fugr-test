# Тестовое задание
Создание компонента для вывода табличной информации о пользователях. Подробное описанание задания доступно [по ссылке](task.md).

При выполнении использованы Vue, нативный CSS и JS, а также сборка на Parcel.

## Запуск
Для запуска необходимо клонировать репозиторий, установить зависимости  и выполнить команду start.
```
git clone https://github.com/glevanov/fugr-test.git
npm install
npm run start
```

## Статус выполнения
* **Сортировка по столбцам**: сортировка работает, не реализован индикатор направления сортировки :interrobang:
* **Пагинация**: реализовано :heavy_check_mark:
* **Фильтрация**: не реализовано :x:
* **Вывод данных в отдельное поле по клику на запись**: не реализовано :x:
* **Загрузка данных с сервера**: реализовано, но без возможности пользовательского выбора :interrobang:

## Что ещё стоило бы доработать
* Разбить код на несколько компонентов — сейчас весь код в одном компоненте.
* Сделать деплой живого демо куда-то, где можно настроить CORS — GitHub Pages не разрешает подгружать данные из внешнего источника.
* Подумать о тестах и обработке ошибок.
