## Автотранспорт компаний:

Получить статистику по типам автотранспорта

**Ограничения по лицензии**: Только в расширенной.

**URL** : `/vehicle/stat/`

**Обязательные параметры** :
- `inn(str) or ogrn(str)` - ИНН или ОГРН контрагента

**Необязательные параметры** :
- `kpp(str)` - КПП контрагента

**Метод** : `GET`

**Формат ответа**

```json
{
  "type": "array",
  "items": [
    {
      "type": "object",
      "properties": {
        "category_id": {
          "type": "int",
          "description": "Идентификатор категории."
        },
        "vehicle_count": {
          "type": "int",
          "description": "Количество автомобилей категории"
        }
      }
    }
  ]
}
```

**Пример запроса**

```text
https://api.sbis.ru/vok/vehicle/stat?inn=7605016030
```

**Пример ответа**

```json
[
  {
    "category_id": 1,
    "vehicle_count": 422
  },
  {
    "category_id": 2,
    "vehicle_count": 349
  },
  {
    "category_id": 3,
    "vehicle_count": 1341
  },
  {
    "category_id": 4,
    "vehicle_count": 2164
  }
]
```

***

Получить список автотранспорта

**Ограничения по лицензии**: Только в расширенной.

**URL** : `/vehicle/`

**Обязательные параметры** :
- `inn(str) or ogrn(str)` - ИНН или ОГРН контрагента

**Необязательные параметры** :
- `kpp(str)` - КПП контрагента
- `limit(int)` - количество записей в запросе. По умолчанию 20, максимум 100.
- `page(int)` - номер страницы запроса. По умолчанию 0.

**Метод** : `GET`

**Формат ответа**

```json
{
  "type": "array",
  "items": [
    {
      "type": "object",
      "properties": {
        "category_id": {
          "type": "int",
          "description": "Идентификатор категории."
        },
        "brand": {
          "type": "string",
          "description": "Брэнд автомобиля"
        },
        "model": {
          "type": "string",
          "description": "Модель автомобиля"
        },
        "year": {
          "type": "int",
          "description": "Год выпуска"
        },
        "vin": {
          "type": "string",
          "description": "VIN номер"
        },
        "vrp": {
          "type": "string",
          "description": "Номер регистрации автомобиля"
        },
        "vrp_region": {
          "type": "string",
          "description": "регион регистрации автомобиля"
        },
        "license_number": {
          "type": "string",
          "description": "Номер лицензии по перевозке"
        },
        "erul_number": {
          "type": "string",
          "description": "Глобальный номер лицензии по перевозке"
        },
        "pledge_number": {
          "type": "string",
          "description": "Номер залога/лизинга"
        }
      }
    }
  ]
}
```

**Пример запроса**

```text
https://api.sbis.ru/vok/vehicle?inn=7605016030
```

**Пример ответа**

```json
[
  {
    "category_id": 4,
    "brand": "IVECO",
    "model": "SFR 160",
    "year": 2020,
    "vin": null,
    "vrp": "",
    "vrp_region": "",
    "license_number": null,
    "erul_number": null,
    "pledge_number": null
  },
  {
    "category_id": 4,
    "brand": "IVECO",
    "model": "SFR 160",
    "year": 2019,
    "vin": null,
    "vrp": "",
    "vrp_region": "",
    "license_number": null,
    "erul_number": null,
    "pledge_number": null
  },
  {
    "category_id": 4,
    "brand": "IVECO",
    "model": "SFR 160",
    "year": 2018,
    "vin": null,
    "vrp": "",
    "vrp_region": "",
    "license_number": null,
    "erul_number": null,
    "pledge_number": null
  }
]
```


**Поле category_id**

    1: 'Легковые',
    2: 'Коммерческие',
    3: 'Грузовые',
    4: 'Автобусы',
    5: 'Спецтехника',
