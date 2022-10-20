---
# Front matter
title: "Лабораторная работа №8"
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

Освоить на практике применение однократного гаммирования при работе с различными текстами на дном ключе

# Теоретическое введение



# Выполнение лабораторной работы

Создаем функцию, которая осуществляет однократное гаммирование посредством побитового XOR

![Функция шифрования](image/1.PNG){ #fig:1 width=70% }

Задаем две равные по длине текстовые строки и создаем случайный символьный ключ такой же длины

![Исходные данные](image/2.PNG){ #fig:2 width=70% }

Осуществляем шифрование двух текстов по ключу с помощью написанной функции

![Шифрование данных](image/3.PNG){ #fig:3 width=70% }

Создаем переменную, которая, прогнав два шифрованных текста через побитый XOR, поможет злоумышлинику получить один текс, зная другой, без ключа

![Получение данных без ключа](image/4.PNG){ #fig:4 width=70% }

Таким же способом можно получить часть данных

![Получение части данных](image/5.PNG){ #fig:5 width=70% }


# Выводы

Я освоила на практике применение режима однократного гаммирования при работе с несколькими текстами.


