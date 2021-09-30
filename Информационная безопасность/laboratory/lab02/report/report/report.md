---
# Front matter
lang: ru-RU
title: "Лабораторнаяработа No 2"
subtitle: "Дискреционное разграничение прав в Linux. Основные атрибуты"
author: "Белкина Анастасия Михайловна"

# Formatting
toc-title: "Содержание"
toc: true # Table of contents
toc_depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4paper
documentclass: scrreprt
polyglossia-lang: russian
polyglossia-otherlangs: english
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase
indent: true
pdf-engine: lualatex
header-includes:
  - \linepenalty=10 # the penalty added to the badness of each line within a paragraph (no associated penalty node) Increasing the value makes tex try to have fewer lines in the paragraph.
  - \interlinepenalty=0 # value of the penalty (node) added after each line of a paragraph.
  - \hyphenpenalty=50 # the penalty for line breaking at an automatically inserted hyphen
  - \exhyphenpenalty=50 # the penalty for line breaking at an explicit hyphen
  - \binoppenalty=700 # the penalty for breaking a line at a binary operator
  - \relpenalty=500 # the penalty for breaking a line at a relation
  - \clubpenalty=150 # extra penalty for breaking after first line of a paragraph
  - \widowpenalty=150 # extra penalty for breaking before last line of a paragraph
  - \displaywidowpenalty=50 # extra penalty for breaking before last line before a display math
  - \brokenpenalty=100 # extra penalty for page breaking after a hyphenated line
  - \predisplaypenalty=10000 # penalty for breaking before a display
  - \postdisplaypenalty=0 # penalty for breaking after a display
  - \floatingpenalty = 20000 # penalty for splitting an insertion (can only be split footnote in standard LaTeX)
  - \raggedbottom # or \flushbottom
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

<br/><br/>
<br/><br/>
<br/><br/>
<br/><br/>
<br/><br/>
<br/><br/>
<center><font size="8"> Лабораторная работа No 2</font></center>
<br/><br/>
<center><font size="6">Дискреционное разграничение прав в Linux. Основные атрибуты</font> </center>
<br/><br/>
<br/><br/>
<br/><br/>
<div style="text-align: right"> Выполнила: Белкина Анастасия Михайловна, НБИбд-01-18 </div>
<br/><br/>
<div style="text-align: right"> Преподаватель: Кулябов Дмитрий Сергеевич </div>
<br/><br/>
<br/><br/>
<br/><br/>
<br/><br/>
<br/><br/>
<br/><br/>
<br/><br/>
<br/><br/>

# Цель работы

Получение практических навыков работы в консоли с атрибутами файлов, закрепление теоретических основ дискреционного разграничения доступа в современных системах с открытым кодом на базе ОС Linux1.

# Выполнение лабораторной работы
1. В установленной при выполнении предыдущей лабораторной работы операционной системе создала учётную запись пользователя guest (использую учётную запись администратора): useradd guest

![](images/1.png)

<center>Рис.1 Создался юзер guest</center>

2. Задала пароль для пользователя guest (используя учётную запись администратора): passwd guest

![](images/2.png)

<center>Рис.2 Задала пароль</center>

3. Вошла в систему от имени пользователя guest.

![](images/3.png)

<center>Рис.3 Вход от guest</center>

4. Определила директорию, в которой нахожусь, командой pwd. Сравнила её с приглашением командной строки. Определила, что она является домашней директорией.

![](images/4.png)

<center>Рис.4 Домашняя директория</center>

5. Уточнила имя пользователя командой whoami.

![](images/5.png)

<center>Рис.5 Имя пользователя</center>

6. Уточнила имя пользователя, его группу, а также группы, куда входит пользователь, командой id. Выведенные значения uid, gid и др. зафиксировала: uid=1001(guest), gid=1001(guest) и тд. Сравнила вывод id с выводом команды groups. Вывод groups выводит немного  другую информацию по сравнению с id groups.

![](images/6.png)

<center>Рис.6 Команды id и groups</center>

7. Сравнила полученную информацию об имени пользователя с данными, выводимыми в приглашении командной строки: тут guest и там guest. Имя пользователя одинаковое.

![](images/7.png)

<center>Рис.7 Пункты Приглашение КС и данные id</center>

8. Просмотрела файл /etc/passwd командой cat/etc/passwd. Нашла в нём свою учётную запись. Определила uid пользователя - 1001. Определила gid пользователя - 1001. Сравнила найденные значения с полученными в предыдущих пунктах - совпадают.

![](images/8.png)

<center>Рис.8 Данные из файла etc/passwd</center>

9. Определила существующие в системе директории командой ls -l /home/. Не удалось получить список поддиректорий директории /home. Установлены права rwx------ на директории.

![](images/9.png)

<center>Рис.9 Существующие директории</center>

10. Проверила, какие расширенные атрибуты установлены на поддиректориях, находящихся в директории /home, командой: lsattr /home. Удалось увидеть расширенные атрибуты директории guest? Не удалось увидеть расширенные атрибуты директорий пользователя ambelkina.

![](images/10.png)

<center>Рис.10 Расширенные атрибуты директории</center>

11. Создала в домашней директории поддиректорию dir1 командой mkdir dir1. Определила командами ls -l и lsattr, какие права доступа и расширенные атрибуты были выставлены на директорию dir1: rwxrwxr-x и без расширенных атрибутов.

![](images/11.png)

<center>Рис.11 Права доступа и расширенные атрибуты нового каталога</center>

12. Сняла с директории dir1 все атрибуты командой chmod 000 dir1 и проверила с её помощью правильность выполнения команды ls -l.

![](images/12.png)

<center>Рис.12 Снятие атрибутов</center>

13. Попыталась создать в директории dir1 файл file1 командой echo "test" > /home/guest/dir1/file1. Получила отказ, потому что нет прав доступа и создания файлов. Вообще даже зайти в папку нельзя. Оценила, как сообщение об ошибке отразилось на создании файла - файл не был создан.
Проверила командой ls -l /home/guest/dir1 действительно ли файл file1 не находится внутри директории dir1 - не дает проверить, отказ в доступе, файла там скорее всего нет.

![](images/13.png)

<center>Рис.13 </center>

14. Заполнила таблицу «Установленные права и разрешённые действия», выполняя действия от имени владельца директории (файлов), определив опытным путём, какие операции разрешены, а какие нет.

![](images/t1.png)
![](images/t2.png)

<center>Табл.1 Установленные права и разрешённые действия</center>

15. На основании заполненной таблицы определила минимально необходимые права для выполнения операций внутри директории dir1, заполнила таблицу.

![](images/t3.png)

<center>Табл.3 Минимально необходимые права</center>

# Выводы

Выполняя данную лабораторную работу, я получила практические навыки работы в консоли с атрибутами файлов, закрепила теоретические основы дискреционного разграничения доступа в современных системах с открытым кодом на базе ОС Linux1.
