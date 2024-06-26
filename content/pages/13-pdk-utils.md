---
title: Описание утилит, встроенных в КСП
permalink: /pdk-utils/
eleventyNavigation:
   parent: ug
   key: pdk-utils
   order: 130
   title: Описание утилит, встроенных в КСП
---


## Скрипт для подсчета центров координат контактных площадок PAD Coords Database

Данный скрипт предназначен для вычисления координат центров контактных площадок кристалла и упорядоченного вывода этих координат в файл, с указанием первой площадки. Описание работы скрипта содержится в отдельном документе `PAD_Coords_Database_Script_manual.pdf`.

## Утилита для поиска топологических слоев LSW Finder

LSW Finder - программа, позволяющая найти любой слой в списке топологических слоев. Она находится в меню `*<Имя технологии> - LSW Finder`.

![Изображение](/content/images/ug/13_1.png)

Основное окно программы выглядит так:

![Изображение](/content/images/ug/13_2.png)

Для запуска программы необходимо вручную набрать название нужного слоя и purpose к нему. В случае, если такой слой в технологическом файле существует, он появится и станет активным в окне LSW, даже если перед этим он был скрыт. Если же такого слоя нет, программа выдаст следующее предупреждение:

![Изображение](/content/images/ug/13_3.png)

## Исключение элементов схемы из моделирования

При необходимости элементы электрической схемы можно "выключать" при проведении моделирования. Для этого необходимо выделить элемент и выбрать пункт `Deactivate/Activate` меню `HCMOS8D`. Так же данный пункт доступен в ниспадающем меню `Instance` вызываемом средней кнопкой мыши. Отмеченный элемент не будет участвовать в нетлистовании при моделировании схемы. Данная функциональность доступна только из окна `Virtuoso Schematic Editor`.

![Изображение](/content/images/ug/13_4.png)
![Изображение](/content/images/ug/13_4_1.png)
