# api-error-codes


## Error Codes
| num  | code description                     | more detail              | RU detail                                                      |
| ---- | -------------------------------------| ------------------------ |----------------------------------------------------------------|
| 10## | **Phone errors**                     |                          | **Ошибки номера телефона**                                     |
| 1001 | empty phone                          |                          | Введите номер телефона                                         |
| 1002 | phone invalid                        |                          | В номере телефона ошибка                                       |
| 1003 | fraud                                | ban 20min ; limit 5/5min | Повторите попытку через 20 минут (бан номера телефона)         |
| 1004 | wait                                 | wait 30sec               | Получить новый код можно через 30 сек                          |
| 1005 | invalid otp                          | 5 max                    | Введите правильный код из СМС                                  |
| 1006 | migrated to another phone            | new phone in response    | Номер телефона был изменен                                     |
| #### | **Email errors**                     |                          | **Ошибки Email**                                               |
| 1101 | email invalid                        |                          | В адресе e-mail ошибка                                         |
| #### | **Plates & VIN errors**              |                          | **Ошибки Гос.номера и VIN**                                    |
| 1102 | plates invalid                       |                          | Некорректный гос.номер                                         |
| 1103 | plates region invalid                |                          | Некорректный регион                                            |
| 1203 | vin not determined                   |                          | Ну удалось определить VIN                                      |
| 1406 | incorrect vin                        |                          | Некорректный VIN                                               |
| 1419 | incorrect vin                        |                          | Введеный VIN не соответствует данным по ГРЗ                    |
| #### | **Industry\Category\Type errors**    |                          | **Ошибки Индустрии\Категории\Типа ТС**                         |
| 1201 | invalid vehicle industry             |                          | Некорректная категория ТС                                      |
| 1204 | individual vehicle                   |                          | Это не грузовик                                                |
| 1208 | empty vehicle industry               |                          | Не удалось определить категорию ТС                             |
| 1415 | invalid vehicle body type group      |                          | Категория ТС отличается от "С"                                 |
| #### | **System errors**                    |                          | **Системные ошибки**                                           |
| 1202 | loss classifier error                |                          | Системная ошибка LossClassifier                                |
| 1301 | invalid prediction                   |                          | Системная ошибка Prediction                                    |
| 1401 | invalid preScoring state             |                          | Системная ошибка PreScoring                                    |
| 1901 | unhandled sales process error        |                          | Системная ошибка SalesProcess                                  |
| #### | **OSAGO issuing errors**             |                          | **Ошибки выпуска полиса**                                      |
| 1205 | legalEntity disabled                 |                          | Сейчас оформление для Юридических лиц недоступно               |
| 1206 | individual disabled                  |                          | Сейчас оформление для Физических лиц недоступно                |
| 1207 | privateEntrepreneur disabled         |                          | Сейчас оформление для ИП недоступно                            |
| 1421 | technical inspection expired         |                          | Диагностическая карта просрочена, введите номер действующей ДК |
| #### | **OSAGO data filling errors**        |                          | **Ошибки заполнения данных полиса**                            |
| 1402 | should be with trailer               |                          | Используется только с прицепом                                 |
| 1403 | invalid policy start on              |                          | Не заполнен населенный пункт                                   |
| 1404 | empty owner registration city id     |                          | Не введен населенный пункт                                     |
| 1405 | malformed owner registration city    |                          | Населенный пункт не существуе                                  |
| 1416 | invalid hasTrailer flag              |                          | Используется только с прицепом                                 |
| 1417 | invalid weightGross                  |                          | Категория ТС отличается от "С"                                 |
| #### | **Data collection errors**           |                          | **Ошибки сбора и получения данных**                            |
| 1407 | cannot get city fias id              |                          | Не возможно определить населенный пункт                        |
| 1408 | cannot get base tariff               |                          | Не возможно определить Базовый Траиф                           |
| 1409 | cannot get ageExperienceRate         |                          | Не возможно определить КВС                                     |
| 1410 | cannot get bonusMalusRate            |                          | Не возможно определить КБМ                                     |
| 1411 | empty weightGross                    |                          | Отсутствует разрешенная масса ТС                               |
| 1412 | insufficient data to calculate price |                          | Не возможно рассчитать стоимость полиса                        |
| 1413 | cannot get cb territory rate         |                          | Не возможно рассчитать КТ                                      |
| 1420 | no data                              |                          | Недостаточно данных для обработки запроса                      |
| #### | **Drivers data errors**              |                          | **Ошибки в данных о Водителях**                                |
| 1414 | invalid vehicle license category     |                          | Категория ТС отличается от "С"                                 |
| 1418 | invalid driver license categories    |                          | Один из водителей на имеет необходимой категории               |
| 15## | **Ingos errors**                     |                          | **Ошибки ИНГОССТРАХ**                                          |
| 1501 | ingos create agreement error         |                          | Ингосстрах ошибка создания договора                            |
| 1502 | ingos create payment link error      |                          | Ингосстрах ошибка создания ссылки на оплату                    |
| 1503 | ingos check is paid error            |                          | Ингосстрах ошибка проверка статуса оплаты                      |
| 1504 | ingos download policy error          |                          | Ингосстрах ошибка загрузки полиса                              |
| 1505 | ingos get tariff error               |                          | Ингосстрах ошибка предварительного расчета                     |
| 16## | **Renis errors**                     |                          | **Ошибки Ренессанс**                                           |
| 1601 | renis create agreement error         |                          | Ренессанс ошибка создания договора                             |
| 1602 | renis create payment link error      |                          | Ренессанс ошибка создания ссылки на оплату                     |
| 1603 | renis check is paid error            |                          | Истек срок оплаты полиса, процесс остановлен                   |
| 1604 | renis download policy error          |                          | Ренессанс ошибка загрузки полиса                               |
