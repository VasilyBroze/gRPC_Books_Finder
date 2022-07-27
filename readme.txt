Запуск с Docker:
Импортировать Docker file books_db_backup.tar, лежащий на Яндекс Диске по ссылке https://disk.yandex.ru/d/5UtVpGcLY5Kk6Q 
Либо из Docker-репозитория https://hub.docker.com/r/vasyabroze/books_db_backup
в Images Docker'а командой docker load -i books_db_backup.tar
Указать настройки авторизации к серверу БД в файле pkg/finder/grpcserver.go (25 строка) и grpcserver_test.go (11 строка) (Стандартные настройки root:my-secret-pw@tcp(127.0.0.1:3306)/books)
Запустить файл ./gRPC_Books_Test.exe и Image Docker.
Запустить тест из папки ./pkg/finder


Без Docker:
Для запуска сервиса необходимо импортировать Базу Данных books.sql из папки ./db на сервер (В моём случае Open Server 5.4.2)
Указать настройки авторизации к серверу БД в файле pkg/finder/grpcserver.go (25 строка) и grpcserver_test.go (11 строка) (Стандартные настройки root:my-secret-pw@tcp(127.0.0.1:3306)/books)
Запустить файл ./gRPC_Books_Test.exe и сервер БД.
Запустить тест из папки ./pkg/finder

Для использования gRPC клиента (Windows):
В терминале открыть папку проекта и выполнить: 
	evans api/proto/finder.proto -p 8080
	call GetAuthor
	Автор Пушкин
При верной настройке получим список книг автора. Аналогичная команда - Книга Мёртвые души.

