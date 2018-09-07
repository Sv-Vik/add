﻿<a id="markdown-vanessa-add--add-" name="vanessa-add--add-"></a>
# Vanessa-ADD ( ADD )

[![Открытый чат проекта https://gitter.im/silverbulleters/vanessa-behavoir](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/silverbulleters/vanessa-behavoir?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
[![Build Status](http://ci.silverbulleters.org/buildStatus/icon?job=ADD%20test/develop)](http://ci.silverbulleters.org/job/ADD%20test/job/develop/)
[![Crowdin](https://d322cqt584bo4o.cloudfront.net/vanessa-services/localized.svg)](https://crowdin.com/project/vanessa-services)

<!-- TOC insertAnchor:true -->

- [Vanessa-ADD ( ADD )](#vanessa-add--add-)
    - [Введение](#введение)
    - [Установка](#установка)
    - [Описание использования](#описание-использования)
    - [Подготовка автодокументации](#подготовка-автодокументации)
    - [Описание использования в режиме BDD](#описание-использования-в-режиме-bdd)
        - [Классический вариант использования (без интерактивного режима)](#классический-вариант-использования-без-интерактивного-режима)
        - [Использования в режиме проверки поведения пользовательского интерфейса ("кнопко-нажималки")](#использования-в-режиме-проверки-поведения-пользовательского-интерфейса-кнопко-нажималки)
        - [Кто пишет feature-файлы ?](#кто-пишет-feature-файлы-)
    - [Файлы настройки/профиля запуска обработки](#файлы-настройкипрофиля-запуска-обработки)
    - [Создается при финансовой поддержке](#создается-при-финансовой-поддержке)
    - [Замечания:](#замечания)
    - [Известные публикации](#известные-публикации)
    - [Вдохновение черпается](#вдохновение-черпается)
    - [Заметки для желающих поучаствовать в доработке](#заметки-для-желающих-поучаствовать-в-доработке)
    - [Лицензии](#лицензии)
    - [Поддержка OpenSource команды](#поддержка-opensource-команды)
    - [Простой FAQ по использованию](#простой-faq-по-использованию)
    - [Enterprise Support](#enterprise-support)

<!-- /TOC -->

<a id="markdown-введение" name="введение"></a>
## Введение 

Продукт Vanessa-ADD (Automation Driven Development) есть набор инструментов для проверки качества решений на платформе 1С:Предприятие.

Vanessa-ADD is a set of testing tools for [1C:Enterprise 8 platform](http://v8.1c.ru) - Tests/behavior (TDD & BDD) for 1С:Enterprise.

Миссия продукта - повышение качества разработки.

Продукт позволяет проверять поведение различных систем на базе 1С и проверяет/гарантирует качество функциональности системы и ее составных частей.

Возможности:

+ различные виды тестирования (модульного/юнит, приемочного, сценарного для 1С 8.3, интеграционного, TDD)
+ проверка поведения (BDD/Gherkin)
+ формирование автодокументации в формате Markdown и видео.

Vanessa-ADD является наследником 2-х продуктов - [xUnitFor1C](https://github.com/xDrivenDevelopment/xUnitFor1C) и [Vanessa-Behavior](https://github.com/silverbulleters/vanessa-behavior). Совместимость с VB 1.Х и xUnitFor1C 4.Х гарантирована.

<a id="markdown-установка" name="установка"></a>
## Установка

Порядок установки ADD:

Автоматическая установка (через установщик пакетов OneScript ):

+ Выполнить `opm install add`
+ После выполнения пакет будет установлен в каталог <УстановленныйOneScript>/lib/add

Автоматическая установка (при установке пакета vanessa-runner через установщик пакетов OneScript ):

+ Выполнить `opm install vanessa-runner`
+ После выполнения пакет будет установлен в каталог <УстановленныйOneScript>/lib/add

Ручная установка:

+ Перейти в [раздел релизы](https://github.com/silverbulleters/add/releases)
+ Скачать архив `add-x.x.x.zip` с последним стабильным релизом - прямая ссылка [Releases](https://github.com/silverbulleters/add/releases/latest)
+ Распаковать указанный архив в нужную папку.

Обязательно ознакомьтесь с:

+ **справкой по продукту** [doc/README.md](./doc/README.md)

+ часто задаваемыми вопросами [FAQ.md](./F.A.Q.md)
+ руководством контрибьютора [CONTRIBUTING.md](./.github/CONTRIBUTING.md)
+ моделью спонсорства [DONATIONS.md](./DONATIONS.md)
+ известные проблемы [KNOWN-PROBLEMS.md](./doc/KNOWN-PROBLEMS.md)


Ночная сборка ветки **develop**:

1. [7z](http://ci.silverbulleters.org/job/ADD%20test/job/develop/lastSuccessfulBuild/artifact/add.7z) - `unzip -o ./add.7z`
2. [tar.gz](http://ci.silverbulleters.org/job/ADD%20test/job/develop/lastSuccessfulBuild/artifact/add.tar.gz) - `tar xfv ./add.tar.gz`

<a id="markdown-описание-использования" name="описание-использования"></a>
## Описание использования

После установки через `opm install` файл продукта расположены по адресу КаталогУстановкиОСкрипт/lib/add

Как правило, в Windows это `C:\Program Files (x86)\OneScript\lib\add`.

Возможно тестирование 2-х видов:

+ тестирование через фичи, применяя методику BDD (ниже)
+ тестирование через код - например, применяя методику TDD

Для каждого из видов тестирования существуют свои браузеры-запускатели тестирования.

+ BDD-тестирование - `bddTestRunner.epf` (в корне продукта)
  + аналогично более раннему проекту `vanessa-behavior`
+ тестирование через код - `xddTestRunner.epf` (в корне продукта)
  + аналогично более раннему проекту `xUnitFor1C`

Возможен как ручной интерактивный запуск тестирования в режиме 1С:Предприятие,
так и автоматический прогон тестирования через командную строку с помощью json-файлов настройки. См. ниже раздел `Файлы настройки/профиля запуска обработки`.

Примеры простого и удобного автоматического запуска через [Vanessa-Runner](https://github.com/silverbulleters/vanessa-runner)

+ `vrunner vanessa --settings tools\vrunner.json` - BDD
+ `vrunner xunit --settings tools\vrunner.json` - TDD

<a id="markdown-подготовка-автодокументации" name="подготовка-автодокументации"></a>
## Подготовка автодокументации

Проект использует принцип формирования автодокументации в формате Markdown и видео.

+ Видео инструкции лежат [здесь](https://www.youtube.com/channel/UC2mJ4LlMG-FF4qkc_kqN_iQ)
+ Прочие инструкции сгруппированы [в этом плейлисте YouTube](https://www.youtube.com/playlist?list=PL2zlgf113YhFG_uRARjDtP1_Obj55UmY4)
+ Также рекомендуется посмотреть вот [этот вебинар](http://infostart.ru/webinars/537546/)
+ Возможно, вам поможет [этот FAQ](https://github.com/silverbulleters/add/blob/develop/F.A.Q.MD)

Чтобы у вас работало создание автовидеоинструкций, необходимо установить дополнительный софт.

Инструкция по настройке окружения для формирования автовидеоинструкций [здесь](https://github.com/silverbulleters/add/blob/develop/MakeAutoVideo.md).
Также по автовидеоинструкциям есть вот это замечательное [видео](https://www.youtube.com/watch?v=BfXowJH5uP0)

<a id="markdown-описание-использования-в-режиме-bdd" name="описание-использования-в-режиме-bdd"></a>
## Описание использования в режиме BDD

+ пишем feature-файлы в формате Gherkin
  + обычно используется редактор Visual Studio Code с расширением для Gherkin-файлов
  + или связанный проект **vanessa-bdd-editor**

```Gherkin
# language: ru

Функционал: Запуск и получение результатов запуска сценариев

Как любой разработчик продукта
Я хочу иметь возможность запустить проверку сценариев поведения на конфигурации 1С:Предприятие

# Контекст сценария выполняется всегда перед каждым сценарием

Контекст:
  Когда существует разрабатываемая мною конфигурация 1С
  И существуют требования заказчика к ожидаемому поведения в каталоге ".\features"

# Каждый сценарий состоит из последовательных связанных шагов

Сценарий: Запуск в консольном режиме
  Дано Пусть существует файл ".\vb-execute-profile.json"
  И в переменную окружения V83PATH установлено значение "C:\Program Files (x86)\1cv8\8.3.6.2151\bin\1cv8.exe"
  Когда я запускаю командную строку '%V83PATH% /Execute .\bddRunner.epf /C"StartFeaturePlayer;VBParams=.\vb-execute-profile.json'
  Тогда появляется файл с результатами '.\BuildStatus.log'
  И в каталоге ".\allurereport" существует HTML отчет о результатах проверки сценариев

Сценарий: Запуск в интерактивном режиме
  Дано Пусть я открыл обработку "bddRunner.epf"
  Когда Я нажал кнопку "Загрузить фичи из каталога"
  И указал каталог ".\features" с требованиями заказчика
  И затем нажал кнопку "Сгенерировать шаблоны обработок"
  Также в каталоге ".\features" возникли epf-файлы, идентичные имени feature файла
  И при нажатии кнопки "Запустить сценарии" я вижу автоматизированный запуск обработок с признаком "pending" (ожидает реализации)
```

<a id="markdown-классический-вариант-использования-без-интерактивного-режима" name="классический-вариант-использования-без-интерактивного-режима"></a>
### Классический вариант использования (без интерактивного режима)

Фактически классический вариант использования представляет собой следующий рутинный порядок

+ зафиксировали требования к информационной системе
+ создали автоматизированные сценарии проверки в виде feature-файлов
+ наполнили шаги сценариев (сниппеты в виде epf-файлов) кодом проверки поведения
+ запустили сценарии проверки поведения и убедились, что они НЕ работают
+ разработали функционал
+ запустили сценарии проверки поведения
+ убедились, что сценарии проверки работают, и отчет о проверки показывает "Зелёный" статус

<a id="markdown-использования-в-режиме-проверки-поведения-пользовательского-интерфейса-кнопко-нажималки" name="использования-в-режиме-проверки-поведения-пользовательского-интерфейса-кнопко-нажималки"></a>
### Использования в режиме проверки поведения пользовательского интерфейса ("кнопко-нажималки")

для команд, уже имеющих функционал или производящих доработку типовых конфигураций в режиме Taxi, действует упрощенный порядок использования

+ зафиксировали требования к информационной системе
+ создали автоматизированные сценарии проверки в виде feature-файлов
+ разработали управляемые формы или рабочие столы конфигурации в режиме прототипирования
+ запустили запись интерактивных действий пользователя в режиме **менеджера тестирования**
+ получившимся кодом наполнили обработки проверки поведения в виде epf-файлов
+ дополнили код проверки кодом проверки данных, если это необходимо
+ разработали основной функционал
+ запустили сценарии проверки поведения
+ убедились, что сценарии проверки работают и отчет о проверки показывает "Зелёный" статус

<a id="markdown-кто-пишет-feature-файлы-" name="кто-пишет-feature-файлы-"></a>
### Кто пишет feature-файлы ?

Обратите внимание, что фактически feature-файлы могут писать все участники команды:

+ менеджер проекта - если обнаружил, что заказчику необходимо новое поведение
+ бизнес или системный аналитик - на основе собранных требований и технических заданий
+ ведущий разработки - если обнаружил, что требования недостаточно структурированы
+ архитектор или эксперт 1С - если текущие сценарии некорректно спроектированы с точки зрения метаданных

Для редактирования feature-файлов используется

+ либо Visual Studio Code с расширением для Gherkin-файлов
+ либо проект [По автоматизации сбора требований](https://github.com/silverbulleters/vanessa-bdd-editor)
  - на текущий момент имеет статус *beta*

Если вы не уверены в правильности ожидаемого поведения, используйте для этого системы тэгов, например:

+ "@Draft"  - черновик требования
+ "@Предварительно" - начальные заметки

и подобные им обозначения

<a id="markdown-файлы-настройкипрофиля-запуска-обработки" name="файлы-настройкипрофиля-запуска-обработки"></a>
## Файлы настройки/профиля запуска обработки

Для запуска в консольном режиме используется понятие *профиль консольного запуска*. Профиль консольного запуска предназначен для удобной передачи параметров. Профиль запуска представляет собой текстовый файл в формате JSON.

Профиль запуска предназначен для простого консольного запуска
Пример подобной командной строки выглядит так:

+ `vrunner vanessa --settings tools\vrunner.json` - BDD
+ `vrunner xunit --settings tools\vrunner.json` - TDD

Расширенные примеры запуска можно увидеть в соседнем репозитории [Vanessa-Runner](https://github.com/silverbulleters/vanessa-runner)

или
```cmd
%V83PATH% /Execute C:\add\bddRunner.epf /C"StartFeaturePlayer;VBParams=C:\VBParams.json"
```

Текущие параметры настройки для json-файлов:

+ **Каталог фич** - каталог, где собраны требования заказчика описанные на языке Gherkin
+ **ВыполнитьСценарии** - признак того, что необходимо запустить выполнение сценариев
+ **ДелатьОтчетВФорматеАллюр** - признак того, что необходимо формировать HTML отчёт о результатах проверки
+ **КаталогOutputAllureБазовый** - адрес каталога, для где будет формироваться HTML отчёт
+ **ЗавершитьРаботуСистемы** - признак того, что окончанию работы необходимо завершить работу 1С предприятия
+ **ВыгружатьСтатусВыполненияСценариевВФайл** - признак, что необходимо формировать файл с финальным статусом проверки
+ **ПутьКФайлуДляВыгрузкиСтатуасВыполненияСценариев** - по данному пути будет сформирован файл со статусом проверки (обычно используется на серверах сборки для автоматизированного указания статуса сборки)
+ **СписокТеговИсключение** - массив текстовых тэгов для исключения из проверки (например, используется для черновиков сценариев и требований)
+ **СписокТеговОтбор** - массив текстовых тэгов для запуска проверки поведения по сценариям, содержащим любой из указанных тэгов

Пример подобного JSON файла профиля:

```json
{
"КаталогФич": "C:\\add\features",
"ВыполнитьСценарии": "Истина",
"ДелатьОтчетВФорматеАллюр": "Истина",
"КаталогOutputAllureБазовый": "C:\\allurereport",
"ЗавершитьРаботуСистемы": "Истина",
"ВыгружатьСтатусВыполненияСценариевВФайл": "Истина",
"ПутьКФайлуДляВыгрузкиСтатусаВыполненияСценариев": "C:\\BuildStatus.log",
"СписокТеговИсключение":[
  "IgnoreOnCIMainBuild",
  "Draft"
]
}
```

Много примеров json-файлов есть в каталоге `tools` проекта.

<a id="markdown-создается-при-финансовой-поддержке" name="создается-при-финансовой-поддержке"></a>
## Создается при финансовой поддержке

как попасть в этот раздел ? смотри [DONATIONS.md](./DONATIONS.md)

<a id="markdown-замечания" name="замечания"></a>
## Замечания:

+ пожелания к использованию можно фиксировать в виде Github Issues
+ структура каталогов проекта соответствует [шаблону bootstrap]( https://github.com/silverbulleters/vanessa-bootstrap)

<a id="markdown-известные-публикации" name="известные-публикации"></a>
## Известные публикации

+ [Первичная публикация](http://habrahabr.ru/post/252473/)
+ [Пример отчета Allure на основе тестов](http://youtu.be/982gF1wY8sM)

<a id="markdown-вдохновение-черпается" name="вдохновение-черпается"></a>
## Вдохновение черпается

+ [Огурец](https://cukes.info/)
+ [Автоматизированное тестирование 1С](http://v8.1c.ru/overview/Term_000000816.htm)
+ [Yandex Allure](http://allure.qatools.ru/)
+ [Silenium](http://docs.seleniumhq.org/)
+ [ТРИЗ](https://ru.wikipedia.org/wiki/Теория_решения_изобретательских_задач)
+ [Дэн Норт](http://en.wikipedia.org/wiki/Acceptance_test-driven_development)

<a id="markdown-заметки-для-желающих-поучаствовать-в-доработке" name="заметки-для-желающих-поучаствовать-в-доработке"></a>
## Заметки для желающих поучаствовать в доработке

+ мы используем подход git-flow для реализации функциональности
+ мы используем принцип самопроверки через feature файлы, поэтому перед разработкой новой функциональности мы также - разрабатываем feature файлы, генерируем шаблоны сценариев и наполняем их кодом для проверки. Поэтому к доработкам без feature файлов мы относимся "холодно".

более подробно в файле [CONTRIBUTING.md](./.github/CONTRIBUTING.md)

<a id="markdown-лицензии" name="лицензии"></a>
## Лицензии

+ основная лицензия продукта - BSD v3
+ лицензии стороннего кода - Apache License, GitHub CLA, Freeware, etc

<a id="markdown-поддержка-opensource-команды" name="поддержка-opensource-команды"></a>
## Поддержка OpenSource команды

+ мы используем https://salt.bountysource.com/checkout/amount?team=silverbulleters

<a id="markdown-простой-faq-по-использованию" name="простой-faq-по-использованию"></a>
## Простой FAQ по использованию

+ **Q: много ли команд используют такой подход ?**
+ **A:** из известных нам - 63 команды

+ **Q: можно ли тестировать производительность с помощью BDD ?**
+ **A:** для этого существует другой закрытый инструментарий, который использует vanessa-add как клиента тестирования - используется в Enterprise проектах.

+ **Q: Что вы думаете о сценарном тестировании ?**
+ **A:** сценарное тестирование слишком дорого по савокупной стоимости владения, поэтому пусть живет своей жизнью вместе с СППР, обратите внимание, что учебный центр №1 думает провести подготовку слушателей [по функционалу тестирования в 1С:Предприятии (ссылка на Facebook](https://www.facebook.com/1631718833760014/posts/1715544585377438/) - если Вас интересует функционал сценарного тестирования, возможно стоит записаться именно на этот курс, а не ходить по GitHub ссылкам.

+ **Q: А где более подробный FAQ**
+ **A: Полный FAQ находится [в файле F.A.Q.MD](F.A.Q.MD).

<a id="markdown-enterprise-support" name="enterprise-support"></a>
## Enterprise Support

платная подддержка содержит в себе

+ обучение навыкам работы с BDD при разработке на 1С
+ обучение навыкам написания на языке Gherkin
+ обучение навыкам написания сценариев проверки поведения

для заказа платной поддержки необходимо отравить заявку на адрес education@silverbulleters.org
или
по телефону +7-(499)-346-70-19.

[![ZenHub](https://raw.githubusercontent.com/ZenHubIO/support/master/zenhub-badge.png)](https://zenhub.io)

Контура сборки предоставлены

[![DOcean](https://www.digitalocean.com/assets/media/logos-badges/png/DO_Logo_Horizontal_Blue-3db19536.png)](https://m.do.co/c/2a3a0769ac84)
