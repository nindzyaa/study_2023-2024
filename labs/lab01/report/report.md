---
## Front matter
title: "Лабораторная работа №1"
subtitle: "Математические основы защиты информации и информационной безопасности"
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
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

1. Ознакомление с двумя методами шифрования: шифр Цезаря с произвольным ключем k и шифр Атбаш.
2. Их реализация на произвольном языке программирования.

# Задание

1. Реализовать шифр Цезаря с произвольным ключем
2. Реализовать шифр Атбаша.

# Теоретическое введение

Шифр = криптосистема.
Закрытый текст = зашифрованный текст.
Криптоаналитик — человек, который пытается вскрыть зашифрованное сообщение, которое не ему предназначено.
Атака, взлом, вскрытие — попытка узнать исходный текст сообщения без ключа.
Дешифровка — взлом или расшифровка самая обычная и законная.

Шифр простой замены — класс методов шифрования, которые сводятся к созданию таблицы шифрования, в которой для каждой буквы открытого текста существует единственная сопоставленная ей буква шифр-текста. Само шифрование заключается в замене букв согласно таблице. Для расшифровки достаточно иметь ту же таблицу, либо знать алгоритм, по которому она генерируется.


# Выполнение лабораторной работы

## Шифр Цезаря

В соответсвии с заданием, была написана программа для шифра Цезаря. Код представлен ниже.

![Код шифра Цезаря](image/1.PNG){ #fig:1 width=70% }

Результаты выполнения программы прдеставленны ниже.


![Результат шифрования](image/2.PNG){ #fig:2 width=70% }

## Шифр Атбаш

В соответсвии с заданием, была написана программа для шифра Атбаш. Код представлен ниже.

![Код шифра Атбаш](image/3.PNG){ #fig:3 width=70% }

Результаты выполнения программы прдеставленны ниже.

![Результат шифрования](image/4.PNG){ #fig:4 width=70% }

# Выводы

1. Я ознакомилась с помощью питона с двумя методами шифровки: Цезарь и Атбаш.
2. Реализовала эти шифры на питоне.

# Список литературы

1. Википедия. Шифр простой замены. https://ru.wikipedia.org/wiki/%D0%A8%D0%B8%D1%84%D1%80_%D0%BF%D1%80%D0%BE%D1%81%D1%82%D0%BE%D0%B9_%D0%B7%D0%B0%D0%BC%D0%B5%D0%BD%D1%8B#:%7E:text=%D0%A8%D0%B8%D1%84%D1%80%20%D0%BF%D1%80%D0%BE%D1%81%D1%82%D0%BE%D0%B9%20%D0%B7%D0%B0%D0%BC%D0%B5%D0%BD%D1%8B%2C%20%D0%BF%D1%80%D0%BE%D1%81%D1%82%D0%BE%D0%B9%20%D0%BF%D0%BE%D0%B4%D1%81%D1%82%D0%B0%D0%BD%D0%BE%D0%B2%D0%BE%D1%87%D0%BD%D1%8B%D0%B9%2C%D1%81%D0%BE%D0%BF%D0%BE%D1%81%D1%82%D0%B0%D0%B2%D0%BB%D0%B5%D0%BD%D0%BD%D0%B0%D1%8F%20%D0%B5%D0%B9%20%D0%B1%D1%83%D0%BA%D0%B2%D0%B0%20%D1%88%D0%B8%D1%84%D1%80-%D1%82%D0%B5%D0%BA%D1%81%D1%82%D0%B0

2. Википедия. Шифр Цезаря.https://ru.wikipedia.org/wiki/%D0%A8%D0%B8%D1%84%D1%80_%D0%A6%D0%B5%D0%B7%D0%B0%D1%80%D1%8F#:%7E:text=%D0%A8%D0%B8%D1%84%D1%80%20%D0%A6%D0%B5%D0%B7%D0%B0%D1%80%D1%8F%20%E2%80%94%20%D1%8D%D1%82%D0%BE%20%D0%B2%D0%B8%D0%B4%20%D1%88%D0%B8%D1%84%D1%80%D0%B0%2C%D1%81%D1%82%D0%B0%D0%BD%D0%B5%D1%82%20%D0%94%2C%20%D0%B8%20%D1%82%D0%B0%D0%BA%20%D0%B4%D0%B0%D0%BB%D0%B5%D0%B5 

3. Википедия. Шифр Атбаш. https://ru.wikipedia.org/wiki/%D0%90%D1%82%D0%B1%D0%B0%D1%88


::: {#refs}
:::
