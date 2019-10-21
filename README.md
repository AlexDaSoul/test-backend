# Тестовое задание backend

### Стек технологий
* [NestJs](https://nestjs.com/)
* [RxJs](http://reactivex.io/)
* [gRPC](https://grpc.io/)
* [Postgres](https://www.postgresql.org/)
* [TypeOrm](https://typeorm.io/)
* [request](https://github.com/request/request/)

### Задача
Взять данные из https://api.flickr.com/services/feeds/photos_public.gne?format=json и записать их в свою БД Postgres с использованием TypeOrm. Обновлять данные раз в 15 секунд, добавлять в БД новые изображения, если есть. Создать в Entity индексы, использовать их.

Создать grpc-стрим, который должен возвращать массив изображений при подключении и обновлении списка в БД. При создании подключения к стриму должна быть возможность указать параметры limit и tags. Limit который должен регулировать длину списка в первом ответе. Tags должен фильтровать данные, передаваемые в стрим стриме по полю tags.

### Дополнительные условия
* Стрим должен быть организован с использованием Rxjs Observable
* 2 запроса с разными параметрами не должны заменять друг друга (если клиент создает 2 подключения к стриму, одно с параметром, другое без, или в тэгах указано разное, в каждый стрим приходят свои данные)
* Запрещено использовать промисы (async/await), они должы быть превращены в RxJs Observable
