# development-notes
Конспекты по разработке ПО. Java, Kotlin, databases, CI\CD etc.

# Оглавление
* [Парадигмы программирования](#Парадигмы-программирования)
* Java
  * [ООП](#ооп)
    * Преимущества/отличие ООП от функционального программирования
    * [Отношения между классами](#отношения-между-классами)
  * Core
    * [Какой класс в Java не наследуется от Object](#Какой-класс-в-Java-не-наследуется-от-Object)
    * как так может случится, что нельзя будет пробросить чекед ошибку наверх?
    * [Что такое литерал](#что-такое-литерал)
    * [Области памяти](#области-памяти)
    * Boxing, unboxing
    * equals, hashcode
    * [Immutable класс](#immutable-класс)
    * [Абстрактные классы vs интерфейсы](#абстрактные-классы-vs-интерфейсы)
    * [Зачем нужен private конструктор](#зачем-нужен-private-конструктор)
    * [Рефлексия](#рефлексия)
    * Garbage collector
      * 3 типа прохода сборщика мусора, чем отличаются. (minor, major, full)
      * как работает GC
      * алгоритм сборки G1
      * алгоритм поиска мусора
  * [Stream API](#stream-api)
  * [Многопоточность](#многопоточность)
    * разница между синхронайзд в сигнатуре метода и синхронайзд для блока кода?
    * Как реализован дефолтный пул потоков? (BlokingQueue)
    * В чем заключается проблема ключевого слова synchronized?
    * локи
    * коллекции
    * синхронизаторы
    * атомики
    * volatile
    * тредпулы
  * Collections
    * как делается ГЕТ из хэшмапы? https://habr.com/ru/articles/421179/ 
    * как сделать чтобы мы могли положить в хэшмапу но НЕ могли достать?
    * [Arraylist](#arraylist)
    * [LinkedList](#linkedlist)
    * [HashMap](#hashmap)
  * как распределяются потоки в джаве и ос - кто чем владеет? реальные? логические?
  * Загрузчики классов, какие бывают? Наши кастомные классы какими загрузчиками загружаются?
  * Пространства памяти в Java (метаспейс, хип, стек)
  * В каком соотношении разделяется память на хип и остальное? (80%/20%)
  * [Интерфейсы](#интерфейсы)
  * Что появилось в 8 джаве - стримы, лямбды, функциональные интрефейсы.
  * Из каких частей состоит JVM Generations?
  * В чем заключается преимущество сборки приложения в виде исполняемого jar-файла?
  * Какие принципы лежат в основе реактивного программирования? 
* Kotlin
  * Когда используется Nothing
  * lazy vs lateinit 
* Spring
  * как работает спринг стартер?
  * как написать свой спринг-стартер?
  * @Conditional
  * Цикл жизни бина
  * Dependency injection
  * Способы заинжектить бин (конструктор, сеттер и тп). Когда применимы
  * SpringBoot
    * (автоконфигурация, как написать стартер, как работает)
  * Скоупы бинов
  * @PostConsruct, @Predestroy
  * Spring MVC
  * Spring Security
  * Spring Data Jpa
  * Spring AOP
  * Spring Cloud
  * В чем ключевое различие между Spring MVC и Spring Webflux? 
  * Для чего используются профили в спринге (Для конфигурирования (например для дев и тестового стенда))
  * В чём отличие спринга от спринг бут?
  * работа аннотаций
  * bean post processor
  * CGLib, dynamic proxy
    * [Можно ли запроксировать класс если он final](#Можно-ли-запроксировать-класс-если-он-final)
* DSL
* Hibernate
  * проблема N+1, решение
  * @Transactional
  * ORM identity - сначала сохраняется в БД ентити и там на уровне БД присваивается id
  * ORM sequentity - перед сохранением сущности идёт запрос в БД для запроса следующего id
  * Требования к Entity классу
* Database
  * Реляционные БД
    * [SQL](#sql)
    * Каким образом измерить производительность SQL-запросов?
    * ACID
    * primary и unique - в чём разница?
    * как сделать cross join - не используя join ?
    * почему могут не отработать индексы, если установлены
    * нужен составной индекс на фамилию, дату рождения, пол - какой будем создавать (какое первое поле и какое дальше). Какой тип у этого индекса выбрать - hash, btree и тп
    * есть индекс составной (а,b) a и b колонки. Кидаем запросы с поиском по колонкам [b,a] , [b,c], [a,c] - где отработает индекс а где нет
    * в бд случается deadlock - как избежать
    * разница между explain и explain analyze. Откуда берутся цифры в explain
    * SQL-инъекции
    * уровни изоляции транзакций
    * отличие MySQL, Posgtres, Oracle
    * Каким образом сохраняются данные в бд если вылезла проблема с железом (свет погас, сервак взорвался).
  * Нереляционные БД
  * примеры NoSQL БД
  * реляц и нереляц БД - в чём разница, плюсы/минусы?
  * SQL vs noSQL
  * способы масштабирования бд
  * 
* Security
  * [JWT](#jwt)
  * Отличие кодирования от шифрования
  * Алгоритмы шифрования
    * AES 256
    * RSA
    * DSS
    * hashing algorithm (salt)
  * Разница между авторизацей и аутентификацией
  * [Уязвимости](#уязвимости)
    * [Использование алгоритма хеширования NONE](#использование-алгоритма-хеширования-none)
    * [Использование украденного токена с действительным сроком действия](#использование-украденного-токена-с-действительным-сроком-действия)
    * Bruteforce
    * DDoS
* DevOps
  * Docker
    * виртуалки vs докер - плюсы, минусы?
    * как зайти в докер контейнер и что-то исполнить?
    * Как устроен Докер образ внутри? Слоями, начиная с верхнеуровневых и заканчивая твоим приложением.
    * Почему слои идут в таком порядке? Потому что при обновлении образа твоего приложения нужно будет обновить только его дельту. Если бы образы шли в обратном порядке - при изменении в образе нижнего порядка (jar-ника) приходилось бы изменять и образы верхних порядков (ОС и тп)
    * разница между RUN и CMD (RUN -  команды выполняющиеся на этапе сборки имеджа, CMD - что запустим на этапе старта контейнера)
    * разница между arg и env?   arg - параметры при билде имеджа (например чтобы кастомизировать версию джавы), env - параметры при запуске уже контейнера
    * [Через что общаются контейнеры между собой](#Через-что-общаются-контейнеры-между-собой)
    * Docker сети и зачем они. Host, bridge, overlay и тп
    * Как написать DockerFile
    * устройство контейнера
  * Kubernetes
    * почему k8s отказалось от поддержки докера?
    * разница между pod и deployment
* Message brokers
  * Kafka
    * партиционирование
    * топик
    * брокер
    * Если положили в 3 разных партиции 3 ивента, можно ли вычитать их в таком порядке, в котором положили? (вроде партиции друг с другом не согласуются в этом плане.)
    * Как обеспечить чтобы несколько событий упали в 1 партицию? (использовать 1 идентификатор для них, например ид клиента. Тогда ивенты со сквозным идентификатором равным ид клиента пойдут в 1 партицию.)
  * RabbitMQ
  * Разница между ними
* REST
* HTTP
  * [WebSocket](#websocket)
  * [Firebase Cloud Messaging](#firebase-cloud-messaging)
  * синхронный и асинхронный http. Как работает
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
  * MVC
  * Facade
  * Adapter
  * основная транзакция закончила работу, надо кинуть выписку счета, но сервис может быть недоступен. Че делать (outbox pattern)
  * Какую задачу решает шаблон проектирования Memento?
* Tests
  * Test-containers
  * Mockito
  * JUnit
* [Problem solving](#problem-solving)
* Алгоритмы
  * как вычисляется высота кр чёрн дерева? (log n, где n это кол-во узлов )
  * Подробнее про алгоритмы сортировки, которые используются в java в Arrays.sort. Как работает, как меняется в зависимости от чего.
  * [Сложность алгоритмов](#сложность-алгоритмов)
* Архитектура
  * Микросервисы
     * +\-
     * есть сервис 1, отправляет запросы в сервис 2 и тот не отвечает. Что делать. Если сделали circuit breaker, то как потом пускать трафик на сервис 2 - все сразу или по частям
     * переполняется пул коннектов к сервису. Что делать.
     * метрики, как появляются, че будешь добавлять в свой новый сервисы
     * сильно дофига коннектов к сервису, че делать. Виды стратегий распределения запросов в load balancerдавать (какое первое поле и какое дальше). Какой тип у этого индекса выбрать - hash, btree и тп 
  * Монолит
    * +\-
* Что такое Pub/Sub парадигма? Приведите примеры реализации
* Linux основные команды
* Как отвечать на вопросы, которые не знаешь? https://www.youtube.com/watch?v=Beoh3tfgPEk
* Вопросы интервьюеру на собеседовании
  * Норма покрытия кода тестами?
  * Есть ли документация к написанному коду?
  * Локальное поднятие сервисов
  * Конвейер фичи от бизнеса до клиента


## Парадигмы программирования
Совокупность идей и понятий, определяющих подход к программированию.
1. **Императивная** - характерные последовательные команды (инструкции). Говорит КАК решать задачу (язык ассемблера)
   1. **Структурная.** Программа выступает в виде иерархической структуры блоков. Разработка ведётся пошагово, сверху вниз. Основные управляющие конструкции: последовательность, цикл, ветвление.
   2. [Объектно-ориентированная](#ооп)
   3. **Аспектно-ориентированная** предлагает разделять программу на модули по функциональности.
2. **Декларативная** - указывает ожидаемый результат, а не способ его получения (HTML, SQL)

### ООП
Представляет программу, как совокупность взаимодействующих объектов.
у ООП есть всего три базовых принципа:
1. **Полиморфизм** простыми словами, это когда у одного и того же интерфейса может быть много разных реализаций. Пример - любая ORM, которая может работать с разными базами (в том числе, существуют комбинации SQL и noSQL), но ты как разработчик используешь только интерфейс
2. **Наследование** - это возможность переопределять поля и методы классов в рамках дерева иерархии
3. **Инкапсуляция** - это способ защиты внутреннего АПИ, суть ее в том, что публичные методы - это внешнее АПИ, а непубличные - внутреннее. Она используется для того, чтобы скрыть от разработчика или пользователя детали реализации. Кроме того, ты можешь менять внутреннее апи как угодно, не трогая внешнее.
Пример:
метод getDatabaseRecords - непубличный, получает данные из базы некоторые записи
метод GetUsers  - публичный метод, возвращает список юзеров.
Публичный метод внутри себя обращается к непубличному, и это и есть инкапсуляция
мы можем поменять базу, не меняя интерфейс GetUsers, можем менять реализацию обоих методов и т.д.
при этом, если кто-то захочет отнаследоваться от нашего класса, ему придется пилить getDatabaseRecords самостоятельно

[вверх](#оглавление)
### Отношения между классами
**Композиция** - неоъемлемая часть (напр. цельная отвёртка - металлическая часть и ручка её неотъемлемые части, квартира в доме). Это связь имеет\принадлежит. Если уничтожить объект владелец, то его составные части тоже будут уничтожены.

**Агрегация** - связь часть-целое между равноправными объектами (напр. автомобиль и колёса). 

**Ассоциация** - независимое взаимодействие (напр. разработчик и компьютер). HAS-A-отношения. 

[вверх](#оглавление)
### Что такое литерал
литерал - это константа, известная на этапе компиляции. 
нарпимер, print("Hello"),  hello - это литерал, потому что он не связан ни с какой переменной

[вверх](#оглавление)
### Области памяти
**Metaspace** (до Java 8 PermGen) - хранит метаданные. PermGen был частью кучи до Java 8, metaspace вынесен из кучи. Metaspace позволил оптимизировать процесс очистки памяти. Теперь сборщик мусора автоматически удаляет из памяти ненужные классы, когда емкость, выделенная для хранения метаданных, достигает максимального значения.
Static сущности (классы, методы, блоки инициализации) хранятся в метаспейсе. Static блок инициализации выполняется во вемя загрузки классов в JVM. Поэтому к статическим методам и переменным можно обращаться до их объявления.

**Heap (куча)** - хранит объекты, JRE-классы. Объем кучи гораздо больше, чем стека, но доступ к ней дольше и память освобождается не сразу, а после работы Garbage collector-a. В куче сущности делятся на объекты нового и старого поколения. Объектами старого поколения считаются те, которые пережили хотя бы 1 проход GC.

**Stack (стек)** - хранит ссылки на объекты в куче, примитивы, локальные переменные (переменные запущенного метода). Работает по принципу LIFO (last in, first out). В стеке могут храниться локальные переменные нескольких методов, если они вызывают друг друга по цепочке. После выхода из метода блок этого метода с его локальными переменными удаляется. Стек - самая маленькая область памяти, но самая быстрая, т.к. стек локализован в памяти и данные из него могут быть загружены в кэш процессора для быстрого доступа.

[вверх](#оглавление)
## Immutable класс
 * final class
 * все поля final private
 * из методов доступа есть только геттеры
 * геттеры возвращают копию объекта\поля

[вверх](#оглавление)
## Абстрактные классы vs интерфейсы
Абстрактный класс - описывает абстрактный объект, не только его поведение. Если класс содержит хотя бы 1 абстрактный метод - класс должен быть абстрактным. Но абстрактным может быть и класс без абстрактных методов. Абстрактный класс - концептуальный объект.

Интерфейс определяет только поведение. 

[вверх](#оглавление)
## Зачем нужен private конструктор
* Для создания утилитных классов со статическими методами, чтобы нельзя было создать инстанс такого класса.
* Для реализации паттерна Singleton. Чтобы гарантировать, что инстанс данного класса будет создан только 1 раз.

[вверх](#оглавление)
## Рефлексия
**Reflection** - механизм манипуляции объектами в обход стандартных механизмов в runtime (во время выполнения программы). С помощью рефлексии можно получить информацю о классах, интерфейсах, полях, методах в runtime, не зная их имён.
Рефлексия нарушает инкапсуляцию и работает немного дольше. 
Spring framework строится на рефлексии.

[вверх](#оглавление)
### Какой класс в Java не наследуется от Object
Все классы в Java наследуются от Object. Можно сказать, что сам Object не наследуется.

[вверх](#оглавление)
### Можно ли запроксировать класс если он final
Да, если через интерфейсы (JDK dynamic proxy), нет, если через классы-наследники (CGLib) https://habr.com/ru/post/347752/ А можно ли запроксировать final метод? Нет, так как его же надо будет оверрайднуть

[вверх](#оглавление)
### SQL
**Structured Query Language** — это декларативный язык программирования (язык запросов), который используют для создания, 
обработки и хранения данных в реляционных базах данных.

[вверх](#оглавление)
### Через что общаются контейнеры между собой
технически - через бридж - это специальное сетевое устройство канального уровня, в линуксе оно эмулируется на уровне ядра, т.е. все докер контейнеры общаются друг с другом через виртуальную локальную сеть. Также, можно при старте контейнера передать флат --net=host, тогда контейнер будет использовать сеть хост системы вместо бриджа

[вверх](#оглавление)
### WebSocket
**Веб-сокеты** это продвинутая технология, позволяющая открыть постоянное двунаправленное сетевое соединение (поверх TCP) между браузером пользователя и сервером. С помощью его API вы можете отправить сообщение на сервер и получить ответ без выполнения http запроса, причём этот процесс будет событийно-управляемым.
#### Как работают веб-сокеты?
Соединение между клиентом и сервером остается открытым, пока не будет остановлено одной из сторон или будет закрыто по таймауту. Для установления соединения между клиентом и сервером они производят “рукопожатие” (handshake). Установленное соединение остается открытым, а связь осуществляется с использованием одного и того же канала, пока соединение не будет прервано на стороне клиента или сервера.
+ Запросы и ответы приходят без задержек и сетевой нагрузки.
+ Подходит для маркетплейсов, бирж, игровых приложений, чатов, соцсетей, интернета вещей, push-уведомлений.
[Как работают WebSocket](https://habr.com/ru/companies/qiwi/articles/747604/)

[вверх](#оглавление)
### Firebase Cloud Messaging
**Firebase Cloud Messaging (FCM)** — это кроссплатформенное решение для обмена сообщениями, которое позволяет надежно и бесплатно их отправлять (например push-уведомления клиентам через приложение.

Взаимодействие с FCM возможно как напрямую через отправку по REST данных на ендпоинт FCM, так и через библиотеку
com.google.firebase:firebase-admin.
[FCM documentation](https://firebase.google.com/docs/cloud-messaging?hl=ru)

[вверх](#оглавление)
### Arraylist
Capacity по умолчанию = 10. При превышении лимита создаётся новый массив по формуле:
новый массив = старый массив * 1,5 + 1
+ Быстрый перебор, быстрый поиск по индексу
+ Элементы упорядочены по индексу
+ Медленное добавление в середину

[вверх](#оглавление)

### LinkedList
* Двусвязный список
* Общая скорость  меньше, чем у ArrayList
* Лучше для вставок в середину и  удалений из середины
* Реализует интерфейсы Queue и Dequeu

[вверх](#оглавление)
### HashMap
Хеш-таблица. Структура данных ключ-значение.

Содержит в себе:
* table = Entry[] со ссылками на списки значений
* loadFactor (дефолтно 0,75)
* size
* treshold - порог при достижении которого capacity мапы увеличивается в 2 раза. treshold = capacity*loadFactor
* capacity (дефолтно 16)

Содержит bucket (корзины) с элементами. Бакет хранит nodes (узлы). Дефолтно бакетов 16. Если в бакете > 2 узлов, то бакет = LinkedList.

Как происходит добавление элемента в hashMap:
* Вычисляется хеш-код ключа элемента
* По хеш-коду ключа определяется бакет, в который будет добавлен элемент. Номер определяется по остатку от деления хэшкода на количество ячеек. В более новых версиях Java с помощью бинарного сдвига
* Если бакет пустой - элемент просто добавляется
* Если бакет не пустой – элемент добавляется в LinkedList внутри бакета
  * Ключ добавляемого элемента сравнивается с ключами в LinkedList по хэшкодам
  * Если хэшкоды не равны – переход к следующему элементу
  * Если хэшкоды равны – ключи дополнительно сравниваются по equals()
  * Если ключи равны по equals() – перезаписывается value найденного ключа
  * Если ключи не равны по equals() – переход к следующему элементу
* Если ключ не найден в LinkedList – элемент добавляется в конец списка

HashMap:
* Не отсортирован, не уорядочен
* Поддерживает null ключ
* Объекты с null ключами всегда записываются в нулевую ячейку массива
* Ключ в хешмапе должен быть иммутабельным и уникальным
* Нет trimToSize как у ArrayList, то есть нет возможности уменьшить размер после его увеличения
* Ключи отсортированы по значению их хеш-кодов
* Быстрая вставка и поиск элементов

В лучшем случае (правильно реализован hashCode()) время доступа к элементу O(1), константное. При плохой реализации hashCode() могут возникать коллизии, когда все элементы например попадают в один бакет. Тогда получаем время доступа к элементу за линейное время, O(n). Для оптимизации, при достижении внутреннего LinkedList размера 8 (8 элементов попали в один бакет), он преобразовывается в красно-чёрное дерево с логарифмическим временем доступа O(log(n)).

[источник](https://habr.com/ru/articles/696184/#HashMap)

[вверх](#оглавление)
#### Отличие HashMap от IdentityHashMap
Класс IdentityHashMap является реализацией абстрактного класса AbstractMap. Его отличие от HashMap состоит в том, что 
при сравнении элементов используется сравнение ссылок, а не значений.

#### В HashMap 16 элементов, добавляем ещё один. Что произойдёт?
мапа увеличится в 2 раза, элементы перераспределятся по новым бакетам. Потому что бакет для элемента выбирается на 
основе хешкода элемента и капасити мапы. Капасити соответственно изменилась.

#### Когда HashMap начинает использовать красно-черное дерево?

[вверх](#оглавление)

### Интерфейсы
#### Что будет если мы имплементим 2 интерфейса с дефолтными методами с одинаковой сигнатурой?
Будет конфликт. - Как решить конфликт? переопределить метод и в нём явно указать ИмяИнтерф.super.defaultMethod() либо переопределить своей реализацией.

[вверх](#оглавление)
### Stream API
Создание стрима:
 * из коллекции
```
List<String> strings = List.of("a", "b", "c");
Stream<String> stream = strings.stream();
```
 * через генератор (нужно задать Supplier)
```
// сгенерирует 3 случайных числа с плавающей точкой 
    Stream.generate(new Random()::nextFloat)
        .limit(3);
```
 * из примитивов
```
    IntStream.range(0, 3);           // 0, 1, 2
    LongStream.rangeClosed(0L, 3L);  // 0L, 1L, 2L, 3L
```
 * через билдер
```
Stream<Integer> builtStream = Stream.<Integer>builder()
        .add(1)
        .add(2)
        .add(3)
        .build();
```
Тут если не указать тип данных, то получим стрим Object и не будет осуществляться проверка типов элементов.

#### почему внешняя переменная в стримах должна быть эффективли файнал?
#### Как быстрее просуммировать числа от 1 до 100 - через стрим или через паралел стрим (паралел стрим требует больше ресурсов и для малых объемов данных дорого получается)
#### Дефолтные методы в интерфейсах это костыль или фича? - костыль, это рушит всё ООП. Но других вариантов для введения стримов не было. 

[вверх](#оглавление)
### Многопоточность
**Многопоточность** - свойство платформы\приложения, которое позволяет процессу состоять из нескольких параллельных потоков. 

[вверх](#оглавление)
## Problem solving
### ExceptionHandler для @Scheduled методов
Проблема: @ExceptionHandler не работает для @Scheduled из-за многопоточности.
Решение: Spring AOP
```
@Aspect
@Component
class ExceptionHandlerForScheduledTasks {
    companion object : KLogging()

    @Pointcut("execution(* com.foo.services.ScheduledService.*(..))")
    fun scheduled() {
    }

    @Around("scheduled()")
    fun handleNoDataFoundException(joinPoint: ProceedingJoinPoint) =
        runCatching { joinPoint.proceed() }
            .onFailure { logger.error { "NoDataFoundException exception, cause: ${it.message}" } }
}
```
Альтернативное решение: реализовать свой ErrorHandler. Минус в том, что кастомный ErrorHandler будет использоваться как для @Scheduled методов, так и для остальных. Но для всех задач кроме @Scheduled должен использоваться дефолтный ErrorHandler, поэтому это решение не подходит.

[вверх](#оглавление)
### Сложность алгоритмов
**Сложность алгоритма или O(n)** - как влияет объём входных данных на время работы или расходуемую память. 

[вверх](#оглавление)
## JWT
Предназначение JWT - проверка подлинности источника данных. При этом стоит понимать, что токен кодируется и подписывается, но не шифруется. Поэтому передавать в нём конфиденциальную информацию не стоит.
Создание JSON Web-Token:
1. Заголовок
```
{
  "typ": "JWT", \\ тип токена
  "alg": "HS256" \\ алгоритм хеширования. None - если токен не подписан
}
```
2. Полезная нагрузка (payload) - хранится информация о пользователе, которую сервер аутентификации передает серверу приложения.
Стандартные необязательные поля:
 * exp – срок окончания действия токена;
 * nbf – время начала действия токена;
 * sub – уникальный идентификатор пользователя.
Помимо стандартных ключей, можно передавать любые данные в виде пар key-value
Большой размер JWT может сказаться на производительности сервиса.
3. Подпись - вычисляется на основе его заголовка и полезной нагрузки по следующей схеме
```
data = base64urlEncode(header) + "." + base64urlEncode(payload) \\ Заголовок и полезная нагрузка по отдельности кодируются с помощью алгоритма Base64URL, а затем соединяются через точку
hashedData = hash(data, secret) \\ затем закодированные данные хешируется с использованием секретного ключа (secret)
signature = base64urlEncode(hashedData) \\ Хешированные данные снова пропускаются через Base64URL для получения подписи
```
4. Cборка JWT. На основании данных из п1-3 собираем веб-токен по схеме
```
header.payload.signature
```
Заголовок и полезная нагрузка предварительно кодируются в Base64URL, а подпись уже в правильном формате.

5. Верификация JWT. В примере выше использовалось хеширование с секретным ключом по алгоритму HS256. Изначально этот ключ известен только серверу аутентификации. Сервер приложения получает его при настройке процесса проверки подлинности.

Когда пользователь отправляет запрос с прикрепленным к нему JWT, приложение может самостоятельно произвести хеширование данных и сравнить результат с полученной подписью. Если строки совпадают, значит вызов поступил из подтвержденного источника и может быть выполнен безопасно.

![Схема авторизации через JWT](/jwt.png)

[Первоистичник](https://proglib.io/p/jwt-for-dummies)

[вверх](#оглавление)

## Уязвимости
### Использование алгоритма хеширования NONE
Подобная атака происходит, когда злоумышленник изменяет JWT, а также меняет алгоритм хеширования (поле “alg”), чтобы указать через ключевое слово none, что целостность токена уже проверена. Некоторые библиотеки рассматривали токены, подписанные с помощью алгоритма none, как действительный токен с проверенной подписью, поэтому злоумышленник мог изменить полезную нагрузку (payload) токена, и приложение доверяло бы токену.

Для предотвращения атаки необходимо использовать библиотеку JWT, которая не подвержена данной уязвимости. Также во время проверки валидности токена необходимо явно запросить использование ожидаемого алгоритма.

### Использование украденного токена с действительным сроком действия
Поскольку токен становится недействительным только после истечения срока его действия, у пользователя нет встроенной функции, позволяющей явно отменить действие токена. Таким образом, в случае кражи пользователь не может сам отозвать токен и затем заблокировать атакующего.

Одним из способов защиты является внедрение черного списка токенов, который будет пригоден для имитации функции «выход из системы», существующей в традиционной системе сеансов.

В черном списке будет храниться сборник (в кодировке SHA-256 в HEX) токена с датой аннулирования, которая должна превышать срок действия выданного токена.

Когда пользователь хочет «выйти», он вызывает специальную службу, которая добавляет предоставленный токен пользователя в черный список, что приводит к немедленному аннулированию токена для дальнейшего использования в приложении.

[вверх](#оглавление)
