---
title: Финализация проекта
permalink: /project-finalizing/
eleventyNavigation:
   parent: ug
   key: project-finalizing
   order: 110
   title: Финализация проекта
---


## Общая информация

В процессе выполнения заключительных операций для топологии изделия в ней могут создаваться следующие структуры:

- **Угловые метки "L"** - L-образные структуры, прорисовываемые во всех слоях, за исключением слоя пассивации (нитрида). Угловые метки используются для измерения значений перекрытий фотошаблонов.
- **Метки логотипа, авторских прав и даты** - алфавитно-цифровая структура, созданная в верхнем слое металлизации и содержащая логотип производителя, текущий год и знак авторских прав ©.
- **Метка проекта** - алфавитно-цифровая структура, созданная в верхнем слое металлизации, позволяющая визуально идентифицировать пластину с изделием.
- **Фиктивные области** - фигуры, создаваемые в слоях активной области, поликремния, слоях металлизации и др., необходимые для соблюдения правил плотности заполнения топологии с целью улучшения контроля процессов травления, шлифовки, уменьшения повреждений, индуцированных плазмой.

Для прорисовки перечисленных выше топологических структур используются специальные слои и атрибуты, позволяющие корректно осуществить их обработку на последующих этапах, а также провести физическую верификацию конечной топологии изделия:

- Атрибут `nosizing` - используется в совокупности с соответствующими слоями для прорисовки фигур, которые не должны подвергаться технологической коррекции;
- Атрибут `fsizing` - используется в совокупности с соответствующими слоями для прорисовки меток "F", которые с одной стороны должны подвергаться технологической коррекции, а с другой не вызывать ложных ошибок при верификации.
- Специальные структуры прорисованные в слоях с атрибутом `fsizing` или `nosizing` должны находится внутри слоя `mfgpp drawing`.

Дополнительная информация по правилам прорисовки данных специальных структур, используемым слоям и т.д. приведена в соответствующих разделах DRM.

## Процедура размещения фиктивных областей (ФО)

Если необходимо, то добавьте зоны исключения в топологическое представление. Зоны исключения - это области схемы, где фиктивные области не будут размещены. Для этого, разработчик должен прорисовать полигоны в специальном слое. Таким образом, процедура `calibre` не будет вставлять фиктивные области в места, где прорисованы данные полигоны.
Для запрета генерации ФО в каких-либо областях топологии используются следующие слои:

| Название |    Атрибут   | GDS#  |     Тип    |                         Описание                          |\
|   слоя   | (назначение) |       | (datatype) |                                                           |
| :------: | :----------: | :---: | :--------: | :-------------------------------------------------------: |
| mexclude |   drawing    |  62   |     4      |     Запрещает генерацию dummy элементов во всех слоях     |
| mexclude |     poly     |  62   |     5      |      Запрещает генерацию dummy элементов в слое poly      |
| mexclude |      m1      |  62   |     6      |     Запрещает генерацию dummy элементов в слое metal1     |
| mexclude |      m2      |  62   |     7      |     Запрещает генерацию dummy элементов в слое metal2     |
| mexclude |      m3      |  62   |     8      |     Запрещает генерацию dummy элементов в слое metal3     |
| mexclude |      m4      |  62   |     9      |     Запрещает генерацию dummy элементов в слое metal4     |
| mexclude |      m5      |  62   |     10     |     Запрещает генерацию dummy элементов в слое metal5     |
| mexclude |      m6      |  62   |     11     |     Запрещает генерацию dummy элементов в слое metal6     |
| mexclude |    active    |  62   |     13     | Запрещает генерацию dummy элементов в слоях active и poly |

### Генерирование фиктивных областей c помощью САПР Metnor Graphics Calibre

1. В меню `Virtuoso Layout Editor` выбрать `Calibre -> Run DRC`. Загрузить файл для `Dummy Generation`.

   ![Изображение](/content/images/ug/11_1.png)

2. В окне конфигурирования задать необходимые установки для запуска DRC-процедуры.
   ![Изображение](/content/images/ug/11_2.png)

   Описание ключей, используемых при генерации dummy:

   - `Tiles Distance to Metal >=` - это минимальное расстояние от ФО до металла для первой итерации заполнения;
   - `Dedicated Tiles Distance to Metal >=` - минимальное расстояние от ФО до металла для второй итерации заполнения;
   - `Metal Density second step (use 1.0 for maximum filling) >=` - минимальная плотность заполнения ФО для второй итерации, используйте значение 1.0 для максимального заполнения;
   - `Metal 1 direction of the routing` - направление формирования ФО для 1-го металла. Возможные значения `VERTICAL` - вертикальное и `HORIZONTAL` - горизонтальное;
   - `Metal 2 direction of the routing` - направление формирования ФО для 2-го металла. Возможные значения `VERTICAL` - вертикальное и `HORIZONTAL` - горизонтальное;
   - `Metal 3 direction of the routing` - направление формирования ФО для 3-го металла. Возможные значения `VERTICAL` - вертикальное и `HORIZONTAL` - горизонтальное;
   - `Metal 4 direction of the routing` - направление формирования ФО для 4-го металла. Возможные значения `VERTICAL` - вертикальное и `HORIZONTAL` - горизонтальное.

3. Далее в окне `Calibre Interactive - nmDRC` во вкладке `Rules`  в поле `DRC Rules File` - должен быть указан путь к файлу `hcmos8d_5v_tilingGen.rul`, а в поле `DRC Run Directory` - рабочий каталог.

   ![Изображение](/content/images/ug/11_3.png)

4. Далее нажмите `Setup -> Preferences` и во вкладке `Trigger` проверьте, правильно ли прописаны пути и ключи скриптов постобработки.
5. Нажмите кнопку `Run DRC`.
6. После завершения DRC-процедуры проверьте, корректно ли отработал скрипт постобработки.

   ![Изображение](/content/images/ug/11_4.png)

   ![Изображение](/content/images/ug/11_5.png)

7. В результате данной DRC-процедуры в рабочем каталоге `Calibre`, указанном в п.3, будет создан файл `<имя_проекта>.calibre_with_fill.gds`, который содержит в себе топологию вашего проекта с фиктивными областями. В ячейке под названием `TOP` находится топология вашего проекта с фиктивными областями, в ячейке `<имя_проекта>_DUMMIES` находится топология только фиктивных областей.

## Создание и размещение метки проекта

Создание метки для идентификации проекта осуществляется с помощью ячейки pgtext из библиотеки devices_symbols, входящей в состав PDK по технологии HCMOS8D.
Для создания метки проекта необходимо:

1. В основном меню `Virtuoso Layout Editor` выбрать пункт `Create -> Instance`, указать имя библиотеки `devices_symbols`, имя ячейки `pgtext`, представление `layout`.
2. Задать необходимые параметры, выбрав пункт меню `Edit -> Properties` и вкладку `Parameter`. Данная ячейка позволяет создавать текстовые и цифровые метки в слоях `metal1-metal6` с атрибутом `drawing`. Разрешены только буквы английского алфавита, символ подчеркивания и цифры. Строчные и прописные буквы не различаются. Минимальная высота текста 10 мкм.
3. Привязать ее в необходимое место исходной топологии изделия.

   ![Изображение](/content/images/ug/11_8.png)

4. При размещении метки проекта необходимо соблюдать следующие требования:

|                                       Правило                                        | Норма |
|:------------------------------------------------------------------------------------:|:-----:|
| Минимальное расстояние от метки проекта до активных областей приборов внутри изделия | 3 мкм |
