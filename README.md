Актуальная документация в более читаемом виде находится на http://docs-ke.rtfd.io 

# extern-api-docs: документация API Контур.Экстерна.
У Контур.Экстерна есть удобный и понятный веб-интерфейс, но иногда требуется решать задачи, для которых веб-интерфейс не подходит.   Например, необходимо отправить тысячи документов в ответ на требование ФНС: через веб-интерфейс на это потребуется большое количество человеко-часов, а через API это быстро сделает код.  

Данный API предназначен для обеспечения электронного документооборота между хозяйствующими субъектами и контролирующими органами. API скрывает большую часть рутинной работы и предоставляет простые и понятные методы.


# Функциональность

Работа в API состоит из четырех основных блоков.

![Схема](https://github.com/skbkontur/extern-api-docs/blob/master/images/Общая%20краткая.jpg)

## I. Аутентификация, авторизация [→](https://github.com/skbkontur/extern-api-docs/blob/master/Аутентификация.md)

Методы этого блока позволяют получить доступ к своим организациям следующими защищенными способами:
* предъявить свой сертификат квалифицированной электронной подписи
* предъявить аутентификацию пользователя в своей информационной системе - доверительная аутентификация

## II. Работа с учетными записями организаций и пользователей [→](https://github.com/skbkontur/extern-api-docs/blob/master/Работа%20с%20УЗ.md)

В API есть возможность:
* выбрать для работы организацию авторизованного пользователя, которая уже заведена в Контур.Экстерне;
* добавить для работы новую организацию.

## III. Работа с черновиками документооборотов [→](https://github.com/skbkontur/extern-api-docs/blob/master/Черновик%20ДО.md)

С этого блока начинается работа основной функциональности API Контур.Экстерна — обмен электронными юридически-значимыми документами с контролирующими органами.  
С помощью методов этого блока можно:
* создать черновик документооборота и наполнять его необходимыми к передаче в контролирующий орган документами и файлами;
* создать файл деклараций по контракту: на входе API получает минимально необходимые для заполнения декларации цифры, на выходе получается готовый файл декларации утвержденного формата;
* проверить формализованные документы на соответствие утвержденным форматам;
* получить удобные и соответствующие форматам печатные формы формализованных документов;
* отправить подготовленные в черновиках документы в контролирующие органы.

## IV. Работа с документооборотами [→](https://github.com/skbkontur/extern-api-docs/blob/master/Работа%20с%20ДО.md)

В этом блоке собраны методы для работы с документооборотами (созданными как в рамках работы с данным API, так и с любыми другими документооборотами, созданными в Контур.Экстерне). 
С документооборотами можно делать следующее:
* узнать статус отправленного документооборота (дошел ли он до контролирующего органа, принят или отклонен и прочее);
* получить ответные документы от контролирующих органов на ранее отправленные документообороты, и распечатать их;
* получить входящие документообороты от контролирующих органов (требования, письма), и отправить ответные документов на них;
* получать сводную ленту событий по доступным документооборотам для реализации, например, смс-информирования пользователей.

# Кому может быть интересен API?
### [Абонент Контур.Экстерна](https://github.com/skbkontur/extern-api-docs/blob/master/scenarios/Абонент%20Контур.Экстерна.md)
Организация, которая купила Контур.Экстерн, но не хочет работать в его веб.интерфейса. Например, она хочет автоматизировать процессы внутри компании, предоставить возможность бухгалтерам работа в привычных интерфейсах информационных систем организации.
### [Компания-партнер Контура](https://github.com/skbkontur/extern-api-docs/blob/master/scenarios/Компания-партнер%20Контура.md)
Компания, которая разрабатывает или предоставляет своим клиентам различные информационные системы, и хочет встроить в них электронный документооборот с контролирующими органами.
### [Компания-партнер Удостоверяющего центра Контура](https://github.com/skbkontur/extern-api-docs/blob/master/scenarios/Компания-партнер%20Удостоверяющего%20центра%20Контура.md)
Компании-партнеры Контура дополнительно имеющие у себя аккредитованное рабочее место нашего Удостоверяющего центра. Оно позволяет Партнеру выдавать облачные квалифицированные сертификаты электронной подписи от своего имени, но на мощностях Удостоверяющего центра Контура.

# Адреса
**Тестовая площадка**: https://extern-api.testkontur.ru/  
**Рабочая площадка**: https://extern-api.kontur.ru/
