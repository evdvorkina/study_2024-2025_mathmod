---
## Front matter
lang: ru-RU
title: Лабораторная работа №1
subtitle: Работа с git
author:
  - Дворкина Е. В.
institute:
  - Российский университет дружбы народов, Москва, Россия
date: 22 февраля 2025

## i18n babel
babel-lang: russian
babel-otherlangs: english

## Formatting pdf
toc: false
toc-title: Содержание
slide_level: 2
aspectratio: 169
section-titles: true
theme: metropolis
header-includes:
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
---

## Докладчик

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

  * Дворкина Ева Владимировна
  * студентка
  * группа НФИбд-01-22
  * Российский университет дружбы народов
  * [1132226447@rudn.ru](mailto:1132226447@rudn.ru)
  * <https://github.com/evdvorkina>

:::
::: {.column width="30%"}

![](./image/я.jpg)

:::
::::::::::::::


## Цель работы

Цель данной лабораторной работы - приобретение практических навыков работы с системой управления версиями Git.

# Теоретическое введение

Git — распределённая система управления версиями. Проект был создан Линусом Торвальдсом для управления разработкой ядра Linux, первая версия выпущена 7 апреля 2005 года; координатор — Дзюн Хамано. 

# Выполнение лабораторной работы

## Подготовка

![Настройка git](image/1.PNG){#fig:001 width=70%}

## Создание проекта

![Создание репозитория](image/2.PNG){#fig:002 width=70%}

## Создание проекта

![Добавление файла в репозиторий](image/3.PNG){#fig:003 width=70%}

## Внесение изменений

Изменим содержимое файла hello.html на:

```
<h1>Hello, World!</h1>
```

## Внесение изменений

![Внесение изменений в содержимое репозитория](image/4.PNG){#fig:004 width=70%}

## Внесение изменений

Изменим страницу «Hello, World», чтобы она содержала стандартные теги <html> и <body> 

```
<html>
  <body>
    <h1>Hello, World!</h1>
  </body>
</html>
```

## Внесение изменений

Добавим это изменение в индекс git и добавим заголовки HTML (секцию <head>) к странице «Hello, World».

![Изменение файла hello.html](image/4б.PNG){#fig:0042 width=70%}

## Внесение изменений

Проверив текущий статус, увидим, что hello.html указан дважды в состоянии. Первое изменение (добавление стандартных тегов) проиндексировано и готово к коммиту. Второе изменение (добавление заголовков HTML) не проиндексированно.

![Внесение нескольких изменений в содержимое репозитория](image/5.PNG){#fig:005 width=70%}

## Внесение изменений

Произведем коммит проиндексированного изменения. Проиндексируем оставшееся изменение, посмотрим статус и прокоммитим его тоже 

![Внесение нескольких изменений в содержимое репозитория](image/6.PNG){#fig:006 width=70%}

## История

Получим список произведенных изменений в стандартном виде `git log`, затем в однострочном `git log --pretty=oneline` и далее с указанием времени и количества 

```
git log --pretty=oneline --max-count=2
git log --pretty=oneline --since='5 minutes ago'
git log --pretty=oneline --until='5 minutes ago'
```

![Просмотр истории](image/7.PNG){#fig:007 width=70%}

## Получение старых версий

Изучим данные лога и найдем там хэш первого коммита, используя его, вернемся к первой верссии репозитория и просмотрим файл hello.html, действительно, увидим первую версию. Затем вернемся к последней версии в ветке master и посмотрим на тот же файл 

![Просмотр разных версий репозитория](image/8.PNG){#fig:008 width=70%}

## Создание тегов версий

Назовем текущую версию страницы hello первой (v1). Создадим тег первой версии `git tag v1` и используем его для того, чтобы вернуться к предыдущей версии, которой также присвоим тег v1-beta 

![Создание тегов версий](image/9.PNG){#fig:009 width=70%}

## Создание тегов версий

Переключимся по тегам между двумя отмеченными версиями. Просмотрим все доступные теги (их два) и посмотрим теги в логе 

![Переключение по имени тега и просмотр доступных тегов](image/10.PNG){#fig:010 width=70%}

## Отмена локальных изменений (до индексации)

Убдеимся, что мы находимся на последнем коммите ветки master и внесем изменение в файл hello.html в виде нежелательного комментария 

![Внесение нежелательного комментария в hello.html (до индексации)](image/11а.PNG){#fig:0111 width=70%}

## Отмена локальных изменений (до индексации)

![Отмена локальных изменений (до индексации)](image/11.PNG){#fig:011 width=70%}

## Отмена проиндексированных изменений (перед коммитом)

![Отмена проиндексированных изменений (перед коммитом)](image/12.PNG){#fig:012 width=70%}

## Отмена коммитов

Изменим файл hello.html на следующий.

```
<html>
  <head>
  </head>
  <body>
    <h1>Hello, World!</h1>
    <!-- This is an unwanted but committed change -->
  </body>
</html>
```

## Отмена коммитов

![Отмена коммитов](image/13.PNG){#fig:013 width=70%}

## Удаление коммиттов из ветки

Удалим последние два коммита с помощью сброса, сначала отметим последний коммит тегом, чтобы его можно было потом найти. Используем команду`git reser --hard v1`, чтобы вернуться к версии до этих коммитов.

![Удаление коммиттов из ветки](image/14.PNG){#fig:014 width=70%}

## Удаление коммиттов из ветки

Теперь в логе их нет, но если посмотреть логи с опцией  `--all` можно их увидеть.

![Ничего никогда не теряется](image/15.PNG){#fig:015 width=70%}

## Удаление тега oops

Удалим тег oops и коммиты, на которые он ссылался, сборщиком мусора. Теперь этот тег не отображается в репозитории

![Удаление тега oops](image/16.PNG){#fig:016 width=70%}

## Изменение предыдущего коммита

Добавим в страницу комментарий автора

![Изменение файла hello.html](image/17.PNG){#fig:017 width=70%}

## Изменение предыдущего коммита

![Изменение предыдущего коммита](image/18.PNG){#fig:018 width=70%}

## Перемещение файлов

Переместим наш файл в каталог lib. Для этого создадим его и используем команду `git mv`, сделаем коммит этого перемещения

![Создание структуры репозитория](image/18а.PNG){#fig:0181 width=70%}

## Подробнее о структуре

Добавим файл index.html в наш репозиторий, заполним файл:

```
<html>
  <body>
    <iframe src="lib/hello.html" width="200" height="200" />
  </body>
</html>
```

## Подробнее о структуре

Проиндексируем файл и сделаем коммит 

![Создание, индексация, коммит нового файла](image/18б.PNG){#fig:0182 width=70%}

## Подробнее о структуре

Теперь при открытии index.html увидим кусок страницы hello в маленьком окошке 

![Результат открытия index.html](image/19.PNG){#fig:019 width=70%}

## Git внутри: Каталог .git

Просмотрим каталог, в котором хранится вся информация git. `ls -C .git/`

Затем посмотрим набор каталогов, имена которых состоят из 2 символов `ls -C .git/objects`

![Каталог .git](image/20.PNG){#fig:020 width=70%}

## Работа непосредственно с объектами git

Найдем последний коммит через `log` и выедем его, используя SHA1 хэш.

![Работа непосредственно с объектами git](image/21.PNG){#fig:021 width=70%}

Исследуем  git репозиторий вручную самостоятельно. Используя хэш родительского коммита последовательно дойдем до первой версии файла hello.html и посмотрим его

![Самостоятельная работа непосредственно с объектами git](image/21а.PNG){#fig:0211 width=70%}

## Создание ветки

Создадим новую ветку «style» и перейдем в неё. Добавим туда файл стилей style.css и добавим его в репозиторий (

![Создание ветки](image/22.PNG){#fig:022 width=70%}

## Создание ветки

Обновим файл hello.html, чтобы использовать стили style.css и index.html 

![Редактирование файла hwllo.html](image/24.PNG){#fig:024 width=70%}

## Создание ветки

Обновиv файл index.html

![Редактирование файла index.html](image/25.PNG){#fig:025 width=70%}

## Создание ветки

Также обновим их в репозиторий

![Создание ветки](image/23.PNG){#fig:023 width=70%}

## Навигация по веткам

Посмотрим все логи 

![Просмотр логов новой ветки](image/26.PNG){#fig:026 width=70%}

Переключимся обратно на основную ветку и просмотрим содержимое файла `lib/hello.html`, заметим, что он не использует стили, не изменился, также просмотрим содержимое этого файла в новой ветке `style`, файл в ней уже использует стили

![Сравнение изменений файла hello.html](image/27.PNG)

## Изменения в ветке master

Вернемся в основную ветку и добавим файл  README.md 

![Изменения в ветке master](image/28.PNG){#fig:028 width=70%}

## Изменения в ветке master

 Просмотрим ветки и их различия `git log --graph --all` 
 
![Изменения в ветке master](image/29.PNG){#fig:029 width=70%}

## Слияние

Слияние переносит изменения из двух веток в одну. Вернемся к ветке style и сольем master с style 

![Слияние веток](image/30.PNG){#fig:030 width=70%}

## Создание конфликта

Вернемся в ветку master и создадим конфликт, внеся изменения в файл hello.html 

![Создание конфликта](image/30а.PNG){#fig:0301 width=70%}

## Создание конфликта

![Создание конфликта](image/31.PNG){#fig:031 width=70%}

## Разрешение конфликтов

Вернемся к ветке style и попытаемся объединить ее с новой веткой
master. В файле lib/hello.html можно увидеть записи с обеих версий этого файла. Первый раздел — версия текущей ветки (style). Второй раздел — версия ветки master.  Внесем изменения в lib/hello.html, оставив только необходимую нам запись и добавим этот файл в репозиторий, чтобы вручную разрешить конфликт

## Разрешение конфликтов

![Конфликт](image/32.PNG){#fig:032 width=70%}

## Разрешение конфликтов

![Разрешение конфликта](image/33.PNG){#fig:033 width=70%}

## Разрешение конфликтов

![Коммит разрешения конфликта](image/34.PNG){#fig:034 width=70%}

## Сброс ветки style

Вернемся на ветку style к точке перед тем, как мы слили ее с веткой master. Мы хотим вернуться в ветке style в точку перед слиянием с master. Нам необходимо найти последний коммит перед слиянием .

![Поиск коммита перед слиянием](image/35.PNG){#fig:035 width=70%}

## Сброс ветки style

Мы видим, что коммит «Updated index.html» был последним на ветке style перед слиянием. Сбросим ветку style к этому коммиту.

![Сброс ветки style](image/36.PNG){#fig:036 width=70%}

## Сброс ветки master

Добавив интерактивный режим в ветку master, мы внесли изменения, конфликтующие с изменениями в ветке style. 

![Поиск коммита перед конфликтом](image/37.PNG){#fig:037 width=70%}

## Сброс ветки master

Коммит «Added README» идет непосредственно перед коммитом конфликтующего интерактивного режима. Мы сбросим ветку master к коммиту «Added README»

![Сброс ветки master](image/38.PNG){#fig:038 width=70%}

## Перебазирование

Используем команду rebase вместо команды merge. Мы вернулись в точку до первого слияния и хотим перенести изменения из ветки master в нашу ветку style. На этот раз для переноса изменений из ветки master мы будем использовать команду git rebase вместо слияния 

![Перебазирование](image/39.PNG){#fig:039 width=70%}

## Слияние в ветку master
 
Вернемся в ветку master и сольем ветку style в неё с помощью команды git merge(рис. 

![Слияние style в master](image/40.PNG){#fig:040 width=70%}

## Клонирование репозиториев

Перейдем в наш рабочий каталог и сделаем клон репозитория hello. Просмотрев его, увидим список всех файлов на верхнем уровне оригинального репозитория README.md, index.html и lib

![Клонирование репозиториев](image/41.PNG){#fig:041 width=70%}

## Клонирование репозиториев

Затем просмотрим историю репозитория и увидим список всех коммитов в новый репозиторий, и он совпадает с историей коммитов в оригинальном репозитории.

![Клонирование репозиторв](image/42.PNG){#fig:042 width=70%}

## Что такое origin?

Клонированный репозиторий знает об имени по умолчанию удаленного репозитория. Посмотрим, подробную информацию об имени по умолчанию. .


![Просмотр имени по умолчанию удаленного репозитория](image/43.PNG){#fig:043 width=70%}

## Удаленные ветки

Посмотрим на ветки, доступные в нашем клонированном репозитории. Можно увидеть, что в списке только ветка master. Для того, чтобы увидеть все ветки используем опцию -a 

![Просмотр веток](image/44.PNG){#fig:044 width=70%}


## Изменение оригинального репозитория

Перейдем в репозиторий hello. Внесем изменения в файл README.md. Затем добавим их в репозиторий

![Изменение оригинального репозитория](image/45.PNG){#fig:045 width=70%}

## Изменение оригинального репозитория

Перейдём в клон репозитория и используем команду `git fetch`, которая будет извлекать новые коммиты из удаленного репозитория, но не будет сливать их с наработками в локальных ветках

![Извлечение изменений](image/46.PNG){#fig:046 width=70%}

## Слияние извлеченных изменений

Сольем внесённые изменения в главную ветку с помощью `git pull`, которая является объединением `fetch` и `merge` в одну команду

![Слияние извлеченных изменений](image/47.PNG){#fig:047 width=70%}

## Добавление ветки наблюдения

![Добавление ветки наблюдения](image/48.PNG){#fig:048 width=70%}

## Создание чистого репозитория

![Создание чистого репозитория](image/49.PNG){#fig:049 width=70%}

## Отправка и извлечение изменений 

![Отправка изменений](image/50.PNG){#fig:050 width=70%}

## Отправка и извлечение изменений 

![Извлечение изменений](image/51.PNG){#fig:051 width=70%}

## Выводы

В процессе выполнения данной лабораторной работы я приобрела практические навыки работы с Git.

# Cпасибо за внимание
