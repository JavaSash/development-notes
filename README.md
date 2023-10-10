# development-notes
Конспекты по разработке ПО. Java, Kotlin, databases, CI\CD etc.

## Оглавление
* Java
  * Core
  * Stream API
* Kotlin
* Spring
* Hibernate
* DB
  * SQL
  * ACID
  * 
* DevOps
  * Docker
  * Kubernetes
* Message brokers
  * Kafka
* REST
* HTTP
  * WebSocket
  * Firebase Cloud Messaging
* gRPC
* Nginx
* Patterns
  * Strategy
  * Decorator
  * Template method
  * Singleton
  * Special Case
  * Factory
  * Builder
* Tests
  * Test-containers
  * Mockito
  * JUnit


### WebSocket
Веб-сокеты это продвинутая технология, позволяющая открыть постоянное двунаправленное сетевое соединение (поверх TCP) между браузером пользователя и сервером. С помощью его API вы можете отправить сообщение на сервер и получить ответ без выполнения http запроса, причём этот процесс будет событийно-управляемым.
#### Как работают веб-сокеты?
Соединение между клиентом и сервером остается открытым, пока не будет остановлено одной из сторон или будет закрыто по таймауту. Для установления соединения между клиентом и сервером они производят “рукопожатие” (handshake). Установленное соединение остается открытым, а связь осуществляется с использованием одного и того же канала, пока соединение не будет прервано на стороне клиента или сервера.
+ Запросы и ответы приходят без задержек и сетевой нагрузки.
+ Подходит для маркетплейсов, бирж, игровых приложений, чатов, соцсетей, интернета вещей, push-уведомлений.

### Firebase Cloud Messaging
Firebase Cloud Messaging (FCM) — это кроссплатформенное решение для обмена сообщениями, которое позволяет надежно и бесплатно их отправлять (например push-уведомления клиентам через приложение.

Взаимодействие с FCM возможно как напрямую через отправку по REST данных на ендпоинт FCM, так и через библиотеку
com.google.firebase:firebase-admin.
[FCM documentation]


[FCM documentation]: https://firebase.google.com/docs/cloud-messaging?hl=ru
