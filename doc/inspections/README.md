## Проверки

Получить статистику по контрагенту.

**URL** : `/inspections/stat`

**Обязательные параметры** :
- `inn(str) or ogrn(str)` - ИНН или ОГРН контрагента

**Необязательные параметры** :
- `kpp(str)` - КПП контрагента
- `limit(int)` - количество записей, дефолтно 10, максимум 20
- `page(int)` - страница, дефолтно 0
- `year_begin(int)` - год начала проверок, по умолчанию текущий
- `year_begin(int)` - год окончания проверок, по умолчанию текущий, максимальная разница с year_begin - 10 лет

**Метод** : `GET`

**Формат ответа**

```json
{
  "type": "array",
  "items": [
    {
      "type": "object",
      "properties": {
        "control_authority_name": {
          "description": "Название контролирующего органа",
          "type": "string"
        },
        "year_data": {
          "description": "годовая информация",
          "type": "object",
          "properties": {
            "year": {
              "description": "Запрашиваемый год, количество проверок",
              "type": "integer"
            }
          }
        }
      }
    }
  ]
}
```

**Пример ответа**

```json
[
  {
    "control_authority_name": "Ростехнадзор",
    "year_data": {
      "2021": 2
    }
  },
  {
    "control_authority_name": "Ространснадзор",
    "year_data": {
      "2021": 1
    }
  }
]
```

Получить данные по проверкам.

**URL** : `/inspections/stat`

**Обязательные параметры** :
- `inn(str) or ogrn(str)` - ИНН или ОГРН контрагента

**Необязательные параметры** :
- `kpp(str)` - КПП контрагента
- `limit(int)` - количество записей, дефолтно 5, максимум 10
- `page(int)` - страница
- `control_authorities(list of str)` - Названия контролирующих органов, по умолчанию все. Значения из статистики, поле control_authority_name
- `is_completed(bool)` - признак завершенности проверки, по умолчанию все

**Метод** : `GET`

**Формат ответа**

```json
{
  "type": "array",
  "items": [
    {
      "type": "object",
      "properties": {
        "region": {
          "description": "Регион",
          "type": "string"
        },
        "activity_category": {
          "description": "категория деятельности",
          "type": "string"
        },
        "activity_code": {
          "description": "код деятельности",
          "type": "string"
        },
        "inspection_body_main": {
          "description": "Проверяющий орган",
          "type": "string"
        },
        "inspection_body_additional": {
          "description": "Список проверяющих органов с которыми проверка проводится совместно",
          "type": "string"
        },
        "inspection_objective": {
          "description": "цель проведения проверки",
          "type": "string"
        },
        "inspection_objective_other": {
          "description": "Иные основания проведения проверки",
          "type": "string"
        },
        "type": {
          "description": "Тип проверки",
          "type": "string"
        },
        "form": {
          "description": "форма проверки",
          "type": "string"
        },
        "date_check": {
          "description": "дата проверки",
          "type": "string"
        },
        "duration": {
          "description": "Длительность проверки",
          "type": "string"
        },
        "status": {
          "description": "статус",
          "type": "string"
        },
        "inspection_address": {
          "description": "адрес инспекции",
          "type": "string"
        },
        "last_inspection_date": {
          "description": "дата проведения последней проверки",
          "type": "string"
        },
        "number": {
          "description": "номер проверки",
          "type": "string"
        },
        "act_number": {
          "description": "номер приказа о проведении проверки",
          "type": "string"
        },
        "act_date": {
          "description": "дата приказа о проведении проверки",
          "type": "string"
        },
        "is_scheduled": {
          "description": "является ли проверка плановой",
          "type": "bool"
        },
        "is_field_audit": {
          "description": "является ли проверка выездной",
          "type": "bool"
        },
        "is_documentary_audit": {
          "description": "Является ли проверка документарной",
          "type": "bool"
        },
        "url": {
          "description": "ссылка на источник",
          "type": "string"
        },
        "inspection_result.act_datetime": {
          "description": "Дата, время составления акта",
          "type": "string"
        },
        "inspection_result.act_place": {
          "description": "Место составления акта",
          "type": "string"
        },
        "inspection_result.inspectors": {
          "description": "ФИО, должность проверяющих",
          "type": "string"
        },
        "inspection_result.authorised_representative": {
          "description": "ФИО, должность уполномоченного представителя проверяемой компании",
          "type": "string"
        },
        "inspection_result.has_violation": {
          "description": "Флаг о наличии нарушений по итогам проверки",
          "type": "bool"
        },
        "inspection_result.is_canceled": {
          "description": "Флаг указывающий на что проверка отменена, из-за невозможности проведения",
          "type": "bool"
        },
        "inspection_result.cancel_reason": {
          "description": "Информация об отмене проверки",
          "type": "string"
        },
        "inspection_result.injunctions_total": {
          "description": "Всего предписаний",
          "type": "integer"
        },
        "inspection_result.injunctions_current": {
          "description": "Неустраненных предписаний",
          "type": "integer"
        },
        "inspection_result.injunctions_executed": {
          "description": "судебные запреты выполнены",
          "type": "string"
        },
        "inspection_result.result_published": {
          "description": "результаты опубликованы",
          "type": "string"
        },
        "violations_data": {
          "description": "данные о нарушениях",
          "type": "object",
          "properties": {
            "violation_desc": {
              "description": "Характер нарушения",
              "type": "string"
            },
            "violation_act": {
              "description": "Обоснование нарушения. Ссылка на правовой акт",
              "type": "string"
            },
            "violation_responsible": {
              "description": "Лица ответственные за нарушение",
              "type": "string"
            },
            "injunction_details": {
              "description": "Реквизиты предписания",
              "type": "string"
            },
            "injunction_content": {
              "description": "Содержание предписания",
              "type": "string"
            },
            "injunction_date": {
              "description": "Дата предписания",
              "type": "string"
            },
            "injunction_deadline": {
              "description": "Дата до которой должно быть исполнено предписание",
              "type": "string"
            },
            "injunction_execution_date": {
              "description": "Срок исполнения предписания",
              "type": "string"
            },
            "injunction_executed": {
              "description": "флаг исполнения предписания",
              "type": "string"
            }
          }
        }
      }
    }
  ]
}
```

**Пример ответа**

```json
[
  {
    "region": "47008000396",
    "activity_category": "3802000000",
    "activity_code": "19.20",
    "inspection_body_main": "Северо-Западное управление Федеральной службы по экологическому, технологическому  и атомному надзору",
    "inspection_body_additional": "Управление Генеральной прокуратуры РФ в Северо-Западном ФО",
    "inspection_objective": "с целью: контроля деятельности юридических лиц/индивидуальных предпринимателей по соблюдению требований законодательства о градостроительной деятельности, обязательных норм и правил при реконструкции объекта капитального строительства в соответствии с программой проверок от  02.12.2020 № б/н.\rЗадачами настоящей проверки являются:\r-осуществление контроля за соблюдением юридическими лицами (индивидуальными предпринимателями) требований законодательства о градостроительной деятельности, обязательных норм и правил;\r- предупреждение, выявление и пресечение допущенных нарушений законодательства о градостроительной деятельности, в том числе проектной документации.\r Предметом настоящей проверки является (отметить нужное): \rсоблюдение обязательных требований законодательства о градостроительной деятельности;\rсоответствие выполнения работ и применяемых строительных материалов в процессе строительства, реконструкции объекта капитального строительства, а также результатов таких работ требованиям утвержденной в соответствии с частями 15, 15.2 и 15.3 статьи 48 настоящего Кодекса проектной документации (с учетом изменений, внесенных в проектную документацию в соответствии с частями 3.8 и 3.9 статьи 49 настоящего Кодекса) и (или) информационной модели (в случае, если формирование и ведение информационной модели являются обязательными в соответствии с требованиями настоящего Кодекса), в том числе требованиям энергетической эффективности (за исключением объектов капитального строительства, на которые требования энергетической эффективности не распространяются) и требованиям оснащенности объекта капитального строительства приборами учета используемых энергетических ресурсов;\rналичие разрешения на строительство;\rвыполнение лицами, осуществляющими строительство, требований частей 2,  3 и 3.1  статьи  52 Градостроительного кодекса РФ;",
    "inspection_objective_other": "Иные основания в соответствии с федеральным законом.",
    "type": "Внеплановая",
    "form": null,
    "date": "2021-01-27",
    "duration": "20 раб.дн., 160 раб.ч.",
    "status": "Завершено",
    "inspection_address": "Ленинградская область, Кингисеппский муниципальный район, Вистинское сельское поселение, Морской торговый порт Усть-Луга (Вис) территория, Комплекс по перевалке и фракционированию стабильного газового конденсата и продуктов его переработки территория, уч. 1, уч. 2. Ленинградская область, Кингисеппский муниципальный район, Вистинское сельское поселение, земельный участок расположен в центральной части кадастрового квартала (Морской торговый порт Усть-Луга.",
    "last_inspection_date": null,
    "number": "002105313550",
    "act_number": "16-1387-104/РК",
    "act_date": "2021-01-14",
    "is_scheduled": false,
    "is_field_audit": null,
    "is_documentary_audit": null,
    "rawdata_link": "https://proverki.gov.ru/",
    "inspection_result.act_datetime": "2021-02-24 22:45:00",
    "inspection_result.act_place": "191028, г. Санкт-Петербург, ул. Моховая, д 30, квартира 18",
    "inspection_result.inspectors": "Добровольская Марина Александровна - Проверяющий, Кузьменко Дмитрий Валерьевич - Проверяющий, Петухов Владимир Степанович - Проверяющий, Енаев Тимур Халимович - Проверяющий, Цыганова Светлана Алексеевна - Проверяющий",
    "inspection_result.authorised_representative": null,
    "inspection_result.has_violation": true,
    "inspection_result.is_canceled": false,
    "inspection_result.cancel_reason": null,
    "inspection_result.injunctions_total": 1,
    "inspection_result.injunctions_current": 0,
    "ctid": "(128132,6)",
    "ctid_inspection_result": "(246045,14)",
    "inspection_result.injunctions_executed": true,
    "inspection_result.result_published": true,
    "violations_data": [
      {
        "violation_desc": "нарушение требований проектной документации",
        "violation_act": "раздел 6 «Проект организации строительства»,Проектная документация   раздел 4.1 «Конструктивные и объемно-планировочные решения»  часть 2",
        "violation_responsible": null,
        "injunction_details": "№16-1387-104-337/ПР-19",
        "injunction_content": "устранить нарушения",
        "injunction_date": "2021-02-24",
        "injunction_deadline": "2021-05-24",
        "injunction_execution_date": null,
        "injunction_executed": true,
        "ctid": "(11122,5)"
      }
    ]
  }
]
```