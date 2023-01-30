# dispatcher-service (ITBooks)
Сервис для упаковки и отправки заказов из интернет магазина ITBooks

**Стек: Java 17, Spring WebFlux, Spring Cloud Functions, Spring Cloud Stream, RabbitMQ, Gradle, Docker.**
## Описание
Проект представляет собой микросервис для упаковки и отправки заказов из интернет магазина ITBooks. 
Сервис взаимодействует с микросервисом [order-service](https://github.com/ArtJDev/order-service), с помощью брокера сообщений RabbitMQ получает от него уведомления о принятых заказах, 
после этого условно упаковывает их и отправляет заказчику. После уведомляет [order-service](https://github.com/ArtJDev/order-service) о том, что заказ отправлен.
Брокер сообщений RabbitMQ настроен по модели pub/sub.

## Запуск
Для полноценной работы сервиса необходимы работающие сервисы [product-service](https://github.com/ArtJDev/product-service) и [order-service](https://github.com/ArtJDev/order-service).

Запуск приложения осуществляется командой `./gradlew bootRun`.
