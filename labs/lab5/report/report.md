---
## Front matter
title: "Лабораторная работа №5"
subtitle: "Информационная безопасность"
author: "Банникова Екатерина Алексеевна"

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true # Table of contents
toc-depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n polyglossia
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
## I18n babel
babel-lang: russian
babel-otherlangs: english
## Fonts
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.9
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric
## Pandoc-crossref LaTeX customization
figureTitle: "Рис."
tableTitle: "Таблица"
listingTitle: "Листинг"
lofTitle: "Список иллюстраций"
lotTitle: "Список таблиц"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Изучить особенности работы с дополнительными атрибутами SetUID, SetGID и Sticky битами и их влияние на работу с файлами при их наличии и отсутствии.

# Теоретическое введение

SetUID, SetGID и Sticku —- это специальные типы разрешений, которые позволяют задавать расширенные права доступа на файлы и каталоги.

* SetUID —- это бит разрешения, который позволяет пользователю запускать исполняемый файл с правами владельца этого файла. Другими словами, использование этого бита позволят поднять привилегии пользователя в случае, если это необходимо. Наличие SetUID бита выражается в том, что на месте классического бита x выставлен специальный бит s: -rwsr-xr-x

* SetGID —- очень похож на SetUID с отличием, что файл будет запускаться от имени группы, который владеет файлом: -rwxr-sr-x

* Sticky —- в случае, если этот бит установлен для папки, то файлы в этой папке могут быть удалены только их владельцем. Наличие этого бита показывается через букву t в конце всех прав: drwxrwxrwxt

# Выполнение лабораторной работы

## Создание программы

Создадим программу simpleid.c 

![Текст программы simpleid.c](image/1.PNG){ #fig:1 width=70% }

Скомпилируем программу с помощью команды gcc и убеждаемся, что файл действительно создан. Далее запускаем исполняемый файл через ./. Вывод написанной программы совпадает с выводом команды id. 

![Компиляция и запуск simpleid](image/2.PNG){ #fig:2 width=70% }

Усложним программу и назовём её simpleid2.c

![Текст программы simpleid2.c](image/3.PNG){ #fig:3 width=70% }

Скомпилируем и запустим файл simpleid2 

![Компиляция и запуск simpleid2](image/4.PNG){ #fig:4 width=70% }

От имени суперпользователя сменим владельца файла simpleid2 на root и установим SetUID-бит. Далее через команду ls -l видим, что бит установился корректно 

![Смена владельца и установка SetUID](image/5.PNG){ #fig:5 width=70% }

Запускаем программу simpleid2 и комаду id. Теперь видим, что появились отличия в uid строках 

![Запуск simpleid2](image/6.PNG){ #fig:6 width=70% }

Проделываем выше описанные действия для SetGID-бита. Теперь после запуска simpleid2 можем увидеть отличие и в gid строках 

![SetUID-бит](image/7.PNG){ #fig:7 width=70% }

Создадим программу readfile.c 

![Текст программы readlife.c](image/8.PNG){ #fig:8 width=70% }

Откомпилируем эту программу командой gcc. Далее меняем владельца файла readfile.c и отнимаем у пользователя guest право на чтение. При попытке прочитать файл от имени пользователя guest возникает ошибка 

![Компиляция readlife.c](image/9.PNG){ #fig:9 width=70% }

![Компиляция readlife.c](image/10.PNG){ #fig:10 width=70% }

Меняем владельца файла readfile и устанавливаем на него SetUID-бит. Запускаем исполняемый файл и убеждаемся, что программа может прочитать файлы readfile.c и /etc/shadow 

![Запуск readlife](image/11.PNG){ #fig:11 width=70% }

![Запуск readlife](image/12.PNG){ #fig:12 width=70% }

## Исследование Sticky-бита

Исследование Sticky-бита
Выполняя команду ls -l выявняем, что на каталоге /tmp установлен Sticky-бит. Это видно, т.к. в конце написана t. Далее от имени пользователя guest создаём файл /tmp/file01.txt. Потом просматриваем атрибуты только что созданного файла и даём всем пользователям право на чтение и запись 

![Создание файла file01](image/13.PNG){ #fig:13 width=70% }

![Создание файла file01](image/14.PNG){ #fig:14 width=70% }

От имени пользователя guest2 читаем файл file01.txt командой cat. Далее успешно дозаписываем в конец файла строку "test2", а затем успешно перезаписываем содержимое, меняя его на строку "test3". Однако при попытке удалить файл возникла ошибка 

![Действия над file01 от лица guest2](image/15.PNG){ #fig:15 width=70% }

Временно повышаем права до суперпользователя и снимаем с директории /tmp Sticky-бит. Покидаем режим суперпользователя командой exit

![Удаление Sticky-бита](image/16.PNG){ #fig:16 width=70% }

Убеждаемся через команду ls -l, что Sticky-бит действительно отсутствует. Далее повторяем действия от имени пользователя guest2. описанные выше. В этот раз удалось удалить файл file01.txt даже при условии, что guest2 не является его владельцем 

![Повтор действий](image/17.PNG){ #fig:17 width=70% }

Временно повышаем права до суперпользователя и возвращает Sticky-бит на каталог /tmp 

![Возвращение Sticky-бита](image/18.PNG){ #fig:18 width=70% }

# Выводы

Я изучила механизмы изменения идентификаторов и получила практические навыки по работе с SetUID, SetGID и Sticky битами и узнала об их особенностях и влиянии на файлы и директории.

# Список литературы{.unnumbered}

::: {#refs}
:::
