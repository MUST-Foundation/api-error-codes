# prescoring process

## front/init

### Валидация.

Если не заполнены plates и vin - возвращаем ошибку 1102, "plates invalid".

Если заполнено поле plates и не прошло валидацию - возвращаем ошибку 1102, "plates invalid".
Перед валидацией вырезается RU(RUS), заменяются латинские символы на карилические.
Допустимые буквы "авекмнорстух". 
Номер должен начинаться с 1 буквы, затем 3 цифры, затем 2 буквы, затем 2 или 3 цифры.

Если заполнено поле plates и не определился регион - возвращаем ошибку 1103, "plates region invalid".

Если заполнено поле vin и не прошло валидацию - возвращаем ошибку 1406, "incorrect vin".
Длина vin должна быть 17 символов.

### Инициация прескоринга.

Если не заполнено поле vin, определяем по AvtokodVehicleByPlates. Если не удалось определить - ошибка прескоринга 1203, "vin not determined".

### Обогащение.

Если ошибка маппинга данных в lossClassifier - ошибка прескоринга 1202, "loss classifier error".

Если не определили vehicleIndustry - ошибка прескоринга 1201, "invalid vehicle industry".

Если vehicleIndustry "Частный транспорт" - ошибка прескоринга 1204, "individual vehicle".

Если vehicleIndustry не "Коммерческий транспорт" - ошибка прескоринга 1201, "invalid vehicle industry".

## front/calculate

### Валидация.

Если выбран владелец физ. лицо и не указан город - возвращаем ошибку "OwnerRegistrationCity required".

Если выбран владелец юр. лицо и не указан инн или кпп - возвращаем ошибки "Inn required", "Kpp required".

Если прескоринг ранее сломался с ошибкой или еще не завершилось обогащение - возвращаем ошибку 1401, "invalid preScoring state".

Если указанное значение PolicyStartOn меньше текущей даты - возвращаем ошибку 1403, "invalid policy start on".

Если выбран владелец юр. лицо, сначала определяем тип владельца в последнем полисе rsaPolicy, если не получилось определяем по последнему владельцу ownershipPeriod. Если тип не юр. лицо - возвращаем ошибку 1205, "owner not legalEntity".

Если нет поля ФИАС города собственника (или он не определился для юр. лица) - возвращаем ошибку 1404, "empty owner registration city id".

Если поле ФИАС города собственника не прошло проверку - возвращаем ошибку 1405, "malformed owner registration city".

### Расчет стоимости.

Если DrivingLicenseCategory "C" и нет поля VehicleWeightGroupRuIns - ошибка прескоринга 1412, "insufficient data to calculate price".

Если не установлено значение поля HasTrailer - ошибка прескоринга 1412, "insufficient data to calculate price".

Если не установлено значение поля OwnerRegistrationCity - ошибка прескоринга 1412, "insufficient data to calculate price".

Если не удалось получить cbTerritoryRate (КТ - коэффициент территории) - ошибка прескоринга 1413, "cannot get cb territory rate".

Если не удалось получить baseTariffRate (БТ - базовый тариф) - ошибка прескоринга 1408, "cannot get base tariff".