# dispatcher-service (ITBooks)
Сервис для упаковки и отправки заказов из интернет магазина ITBooks

**Стек: Java 17, Spring WebFlux, Spring Cloud Function, Spring Cloud Stream, RabbitMQ, Gradle, Docker.**
## Описание
Проект представляет собой микросервис для упаковки и отправки заказов из интернет магазина ITBooks. 
Сервис взаимодействует с микросервисом [order-service](https://github.com/ArtJDev/order-service), с помощью брокера сообщений RabbitMQ получает от него уведомления о принятых заказах, 
после этого условно упаковывает их и отправляет заказчику. После уведомляет [order-service](https://github.com/ArtJDev/order-service) о том, что заказ отправлен.
Брокер сообщений RabbitMQ настроен по модели pub/sub.

## Запуск
Для полноценной работы сервиса необходимы работающие сервисы [product-service](https://github.com/ArtJDev/product-service), [order-service](https://github.com/ArtJDev/order-service) и Docker контейнер с запущенным брокером RabbtMQ. 

Для запуска контенера с RabbitMQ в контейнере Docker необходимо из [этого](https://github.com/ArtJDev/itbooks-deployment/tree/main/docker) репозитория скачать в папку себе на компьютер скрипт docker-compose.yml и папку rabbitmq с файлом конфигурации. После чего открыть командную строку, перейти в созданную папку и выполнить команду
`docker-compose up -d itbooks-rabbitmq`. Docker подтянет образ RabbitMQ, настроит его и запустит в контейнере "itbooks-rabbitmq".

Запуск приложения осуществляется командой `./gradlew bootRun`.
