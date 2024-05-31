## Залог/Лизинг

Получить список объектов находящихся в залоге/лизинге

**Ограничения по лицензии** :

В базовой версии лицензии: последние 3 записи исключая files_id. В расширенной
 лицензии доступно всё для всех организаций.

**URL** : `/pledges`

**Обязательные параметры** :
- `inn(str) or ogrn(str)` - ИНН или ОГРН контрагента

**Необязательные параметры** :
- `kpp(str)` - КПП контрагента
- `limit(str)` - количество записей в запросе, по умолчанию 10, максимум 100
- `page(str)` - страница запроса, по умолчанию 0

**Метод** : `GET`

**Формат ответа**

```json
{
  "type": "array",
  "items": [
    {
      "type": "object",
      "properties": {
        "cost": {
          "description": "стоимость",
          "type": "number/null"
        },
        "type": {
          "description": "тип записи",
          "type": "string"
        },
        "status": {
          "description": "статус записи",
          "type": "string"
        },
        "url": {
          "description": "ссылка на источник",
          "type": "string"
        },
        "comment": {
          "description": "комментарии",
          "type": "string"
        },
        "pledgor_name": {
          "description": "название залогодателя",
          "type": "string"
        },
        "pledgee_name": {
          "description": "название залогодержателя",
          "type": "string"
        },
        "lessor_name": {
          "description": "название арендодателя",
          "type": "string"
        },
        "lessee_name": {
          "description": "название арендатора",
          "type": "string"
        },
        "category": {
          "description": "название залогодержателя",
          "type": "array",
          "items": [
            {
              "description": "название категории",
              "type": "string"
            }
          ]
        },
        "files_id": {
          "description": "идентификаторы файлов",
          "type": "array",
          "items": [
            {
              "description": "идентификатор файла",
              "type": "string"
            }
          ]
        },
        "objects": {
          "description": "объекты записи",
          "type": "array",
          "items": [
            {
              "description": "объект записи",
              "type": "object",
              "properties": {
                 "cost": {
                  "description": "стоимость",
                  "type": "number/null"
                },
                 "description": {
                  "description": "описание",
                  "type": "string"
                },
                 "category": {
                  "description": "категория",
                  "type": "string"
                }
              }
            }
          ]
        },
        "agreement": {
          "description": "соглашение",
          "type": "object",
          "properties": {
             "title": {
              "description": "заголовок",
              "type": "string"
            },
             "number": {
              "description": "номер записи",
              "type": "string"
            },
             "publish_date": {
              "description": "дата публикации",
              "type": "string"
            },
             "maturity_date": {
              "description": "дата погашения",
              "type": "string"
            }
          }
        }
      }  
    }
  ]
}
```

**Пример запроса**

```text
https://api.sbis.ru/vok/pledges?inn=7712040126
```

**Пример ответа**

```json
[
  {
    "cost": null,
    "type": "В залоге",
    "status": "Недействующий",
    "agreement": {
      "title": null,
      "number": "77-8638-0060-577-01",
      "publish_date": "2014-10-20",
      "maturity_date": "2015-07-01"
    },
    "category": [
      "прочее"
    ],
    "url": "https://www.reestr-zalogov.ru/search/index",
    "comment": null,
    "pledgor_name": "Тандер, АО",
    "pledgee_name": "Сбербанк, ПАО",
    "objects": [
      {
        "description": "Кран башенный ,195",
        "cost": 0,
        "category": "Прочее"
      },
      {
        "description": "Кран башенный ,189",
        "cost": 0,
        "category": "Прочее"
      }
    ],
    "files_id": []
  },
  {
    "cost": null,
    "type": "В залоге",
    "status": "Недействующий",
    "agreement": {
      "title": null,
      "number": "77-8638-0060-577-02",
      "publish_date": "2014-10-20",
      "maturity_date": "2015-07-01"
    },
    "category": [
      "товары народного потребления"
    ],
    "url": "https://www.reestr-zalogov.ru/search/index",
    "comment": null,
    "sourceId": "2014-000-131455-473",
    "pledgor_name": "Тандер, АО",
    "pledgee_name": "Сбербанк, ПАО",
    "objects": [
      {
        "description": "Товары в обороте",
        "cost": 0,
        "category": "Товары народного потребления"
      },
      {
        "description": "Товары в обороте",
        "cost": 0,
        "category": "Товары народного потребления"
      },
      {
        "description": "Товары в обороте",
        "cost": 0,
        "category": "Товары народного потребления"
      },
      {
        "description": "Товары в обороте",
        "cost": 0,
        "category": "Товары народного потребления"
      },
      {
        "description": "Товары в обороте",
        "cost": 0,
        "category": "Товары народного потребления"
      },
      {
        "description": "Товары в обороте",
        "cost": 0,
        "category": "Товары народного потребления"
      },
      {
        "description": "Товары в обороте",
        "cost": 0,
        "category": "Товары народного потребления"
      },
      {
        "description": "Товары в обороте",
        "cost": 0,
        "category": "Товары народного потребления"
      },
      {
        "description": "Товары в обороте",
        "cost": 0,
        "category": "Товары народного потребления"
      },
      {
        "description": "Товары в обороте",
        "cost": 0,
        "category": "Товары народного потребления"
      },
      {
        "description": "Товары в обороте",
        "cost": 0,
        "category": "Товары народного потребления"
      },
      {
        "description": "Товары в обороте",
        "cost": 0,
        "category": "Товары народного потребления"
      },
      {
        "description": "Товары в обороте",
        "cost": 0,
        "category": "Товары народного потребления"
      },
      {
        "description": "Товары в обороте",
        "cost": 0,
        "category": "Товары народного потребления"
      },
      {
        "description": "Товары в обороте",
        "cost": 0,
        "category": "Товары народного потребления"
      },
      {
        "description": "Товары в обороте",
        "cost": 0,
        "category": "Товары народного потребления"
      },
      {
        "description": "Товары в обороте",
        "cost": 0,
        "category": "Товары народного потребления"
      }
    ],
    "files_id": []
  }
]
```

***

Получить файл

**Ограничения по лицензии** :

Только для расширенной лицензии

**URL** : `/pledges/file`

**Обязательные параметры** :
- `inn(str) or ogrn(str)` - ИНН или ОГРН контрагента
- `file_id` - идентификатор файла

**Необязательные параметры** :
- `kpp(str)` - КПП контрагента

**Метод** : `GET`

**Формат ответа**

```json
file
```

**Пример запроса**

```text
https://api.sbis.ru/vok/pledges/file?inn=7712040126&file_id=100500
```
