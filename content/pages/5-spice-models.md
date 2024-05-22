---
title: Описание Spice-моделей
permalink: /spice-models/
eleventyNavigation:
   parent: ug
   key: spice-models
   order: 50
   title: Описание Spice-моделей
---


Для МОП транзисторов доступны два типа моделей:

- BSIM3 (рекомендованы для аналоговых приложений)
- MM9 (рекомендованы для цифровых характеристик)
Кроме того, в именах моделей используются следующие расширения:
- JU – используется JUNCAP модель диода для областей стока/истока;
- JURG – используется JUNCAP модель диода для областей стока/истока и учитывается сопротивление затвора;
- JULEAK – используется JUNCAP модель диода для областей стока и истока и подсхема для JUNCAP500 и GIDL (только для моделей BSIM3);
- M1 – простая модель, отсутствуют паразитные резисторы для конденсаторов, простая схема PI-типа для резисторов;
- M2 – более сложная модель, включает паразитные резисторы для конденсаторов, 5 ячеек PI-типа для резисторов.

Более подробная информация по моделям элементов содержится в текстовом представлении ячейки `simulation_models_info` (категория `INFO` библиотеки **devices_symbols**).

Все модели элементов библиотеки сгруппированы по типам устройств в соответствующих модельных файлах (<тип_устройства>.scs для Cadence Spectre), внутри которых они разбиты на секции по углам (corners) моделирования.
Все доступные углы для каждого элемента библиотеки приведены ниже в таблице ниже.

| Тип элемента              |                      Имя элемента                      |   Имя модели   |                 Углы (corners)                  |
| :------------------------ | :----------------------------------------------------: | :------------: | :---------------------------------------------: |
| МОП-транзисторы           |             nhs / nhsb / nhsmos / nhsmos4              |   ENHSMM9JU    | typ / fast2s / fast3s / slow2s / slow3s / stat* | \
| (mosfet.scs)              |                                                        |  ENHSMM9JURG   |                                                 | \
|                           |                                                        |   ENHS_BS3JU   |                                                 | \
|                           |                                                        | ENHS_BS3JULEAK |                                                 |
| ^^                        |             phs / phsb / phsmos / phsmos4              |   EPHSMM9JU    | typ / fast2s / fast3s / slow2s / slow3s / stat  | \
|                           |                                                        |  EPHSMM9JURG   |                                                 | \
|                           |                                                        |   EPHS_BS3JU   |                                                 | \
|                           |                                                        | EPHS_BS3JULEAK |                                                 |
| ^^                        | nll / nllb / nllmos / nllmos4 / IOnmos4 / IOnmos4nplus |   ENLLMM9JU    | typ / fast2s / fast3s / slow2s / slow3s / stat  | \
|                           |                                                        |  ENLLMM9JURG   |                                                 | \
|                           |                                                        |   ENLL_BS3JU   |                                                 | \
|                           |                                                        | ENLL_BS3JULEAK |                                                 |
| ^^                        |        pll / pllb / pllmos / pllmos4 / IOpmos4         |   EPLLMM9JU    | typ / fast2s / fast3s / slow2s / slow3s / stat  | \
|                           |                                                        |  EPLLMM9JURG   |                                                 | \
|                           |                                                        |   EPLL_BS3JU   |                                                 | \
|                           |                                                        | EPLL_BS3JULEAK |                                                 |
| ^^                        |          ndomos / IOndomos / ESDndomos4nplus           |   EN33MM9JU    |          typ / fast3s / slow3s / stat           | \
|                           |                                                        |  EN33MM9JURG   |                                                 | \
|                           |                                                        |   EN33_BS3JU   |                                                 | \
|                           |                                                        | EN33_BS3JULEAK |                                                 |
| ^^                        |                         pdomos                         |   EP33MM9JU    |          typ / fast3s / slow3s / stat           | \
|                           |                                                        |  EP33MM9JURG   |                                                 | \
|                           |                                                        |   EP33_BS3JU   |                                                 |
|                           |                                                        | EP33_BS3JULEAK | typ / fast2s / fast3s / slow2s / slow3s / stat  |
| ^^                        |                 n / nb / nmos / nmos4                  |    ENMM9JU     | typ / fast2s / fast3s / slow2s / slow3s / stat  |
| ^^                        |                 p / pb / pmos / pmos4                  |    EPMM9JU     |                typ / slow / fast                |
| Дрейфовые МОП-транзисторы |                        ndrmoshv                        |   NDRMOSL70A   |                typ / slow / fast                | \
| (driftmos.scs)            |                                                        |                |                                                 |
| ^^                        |                        pdrmoshv                        |   PDRMOSL70A   |                typ / bmax / bmin                |
| Биполярные транзисторы    |                          pnpw                          |   PNPBG25UM1   |                                                 | \
| (bipolar.scs)             |                                                        |                |                typ / slow / fast                |
| Диоды                     |                           dn                           |     DNPPS      |                                                 | \
| (diode.scs)               |                                                        |                |                typ / slow / fast                |
| ^^                        |                           dp                           |     DPPNW      |                typ / slow / fast                |
| ^^                        |                         dnsub                          |     DNWPS      |                typ / slow / fast                |
| ^^                        |                        diodeiso                        |    DPWNISO     |                                                 |
| Конденсаторы              |                        cdonwpo1                        |   CDONWPO1M1   |                typ / cmax / cmin                | \
| (capacitor.scs)           |                                                        |   CDONWPO1M2   |                                                 | \
|                           |                                                        |                |                                                 |
| ^^                        |                         cnwpo1                         |    CNWPO1M1    |            typ / cmax / cmin / stat             | \
|                           |                                                        |    CNWPO1M2    |                                                 |
| ^^                        |                          cmet                          |      CMET      |                typ / cmax / cmin                |
| ^^                        |                     cmim5 / cmim5b                     |    CMM55BM1    |            typ / cmax / cmin / stat             | \
|                           |                                                        |    CMM55BM2    |                                                 |
| ^^                        |                   chkmim5 / chkmim5b                   |   CHKMM55BM1   |            typ / cmax / cmin / stat             | \
|                           |                                                        |   CHKMM55BM2   |                                                 |
| Резисторы                 |                         rhipob                         |     RPO1HM     |            typ / rmax / rmin / stat             | \
| (resistor.scs)            |                                                        |                |                                                 |
| ^^                        |                   rpo1nat / rpo1natb                   |   RPO1NATM1    |            typ / rmax / rmin / stat             | \
|                           |                                                        |   RPO1NATM2    |                                                 |
| ^^                        |                    rpo1sa / rpo1sab                    |    RPO1SAM1    |            typ / rmax / rmin / stat             | \
|                           |                                                        |    RPO1SAM2    |                                                 |
| ^^                        |                    rndiff / rndiffb                    |    RNDIFFM1    |            typ / rmax / rmin / stat             | \
|                           |                                                        |    RNDIFFM2    |                                                 |
| ^^                        |                       rnw / rnwb                       |    RNWELLM1    |            typ / rmax / rmin / stat             | \
|                           |                                                        |    RNWELLM2    |                                                 |
| ^^                        |                     rpo1p / rpo1pb                     |    RPO1PM1     |            typ / rmax / rmin / stat             | \
|                           |                                                        |    RPO1PM2     |                                                 |
| ^^                        |                    rpdiff / rpdiffb                    |     RPDIFF     |                       typ                       | \
|                           |                                                        |    RSHIDEAL    |                                                 |

\* – отличие углов *2s / *3s (2sigma / 3sigma) приводится в разделе [7.7 DRM]().

В данной версии КСП конденсаторы и резисторы имеют два уровня моделирования: стандартный уровень для более быстрого моделирования (модели с расширением "M1") и прецизионный для более точного моделирования (модели с расширением "M2"). По умолчанию используются модели стандартного уровня для обоих типов элементов. Управление точностью моделей резисторов и конденсаторов происходит с помощью Hierarchy Editor.

## Модели элементов для Cadence Spectre

Модели элементов библиотеки для САПР Cadence Spectre находятся в каталоге models / spectre в соответствии с иерархией КСП. Ниже приведена структура данного каталога в составе КСП (жирным шрифтом выделены файлы, непосредственно подключаемые пользователем при моделировании):

| 📁 models                     | &nbsp;                                                |
|:------------------------------|:------------------------------------------------------|
| └───📁 __spectre__/           | &nbsp;                                                |
| &nbsp;   ├───📁 bipolar/      |            Модели биполярных транзисторов             |
| &nbsp;   ├───📁 capacitor/    |                 Модели конденсаторов                  |
| &nbsp;   ├───📁 diode/        |                     Модели диодов                     |
| &nbsp;   ├───📁 driftmos/     |           Модели дрейфовых МОП транзисторов           |
| &nbsp;   ├───📁 mosfet/       |                Модели МОП транзисторов                |
| &nbsp;   ├───📁 resistor/     |                   Модели резисторов                   |
| &nbsp;   ├───📁 stat/         |                 Статистические модели                 |
| &nbsp;   ├───📁 veriloga/     |                   Verilog-A модели                    |
| &nbsp;   ├───📄 bipolar.scs   |      Модельный файл для биполярных транзисторов       |
| &nbsp;   ├───📄 capacitor.scs |           Модельный файл для конденсаторов            |
| &nbsp;   ├───📄 cornergui.scs |        _Файл с настройками для моделирования_         |
| &nbsp;   ├───📄 diode.scs     |               Модельный файл для диодов               |
| &nbsp;   ├───📄 driftmos.scs  |     Модельный файл для дрейфовых МОП транзисторов     |
| &nbsp;   ├───📄 mosfet.scs    |          Модельный файл для МОП транзисторов          |
| &nbsp;   ├───📄 resistor.scs  |             Модельный файл для резисторов             |
| &nbsp;   ├───📄 stat.scs      | Модельный файл для подключения статистических моделей |
| &nbsp;   └───📄 veriloga.scs  |   Модельный файл для подключения Verilog-A моделей    |

{.fs-tree-table}

Кроме модельных файлов для соответствующих типов устройств имеются два дополнительных модельных файла: stat.scs и veriloga.scs. Первый из них предназначен для подключения статистических моделей и является взаимоисключающим по отношению к остальным моделям (т.е. при его использовании все остальные модели должны быть отключены). Модельный файл veriloga.scs содержит единственную секцию "typ" и должен подключаться всегда для успешного запуска моделирования.

## Подключение моделей в Analog Design Environment (ADE)

В данной версии КСП для подключения моделей используется гибкий режим, при котором пользователю необходимо выбрать угол моделирования для каждого типа устройств. Для этого следует выбрать пункт меню `Setup -> Model Libraries…` в главном окне ADE и в появившейся форме `Model Library Setup` задать путь к модельному файлу для соответствующего типа устройств в поле `Model Library File`, имя секции (угла) в поле `Section (opt.)` и нажать кнопку `Add`. По умолчанию при запуске Analog Design Environment будет подключен угол `typ` для всех устройств.

![Изображение](/content/images/ug/5_3.png)
___
