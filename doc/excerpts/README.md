## Список выписок ЕГРЮЛ

Получение списка выписок из ЕГРЮЛ для контрагента

**URL** : `/excerpt/list/`

**Обязательные параметры**

- `inn(str) or ogrn(str)` - ИНН или ОГРН контрагента.
- `limit (int)` - количество запрашиваемых записей
- `page (int)` - номер страницы
  Пример работы limit и page: номер страницы указывает интервал который нужно получить, кратный ограничению. Если limit=10, а page=0 будут получены записи с 0-ой по 9 (всего 10 штук).

Правая граница интервала ограничена 1000-ой записью.

**Метод** : `GET`

**Формат ответа:**
```
    'excerpt_hash' (str): хеш выписки с помощью которого можно ее получить
    'date_receive' (date): дата получения выписки,
    'type_of_excerpt' (str): источник(ЕГРЮЛ),
```

## Последняя выписка ЕГРЮЛ

Получение последней выписки из ЕГРЮЛ для контрагента

**URL** : `/excerpt/last`

**Обязательные параметры**

- `inn(str) or ogrn(str)` - ИНН или ОГРН контрагента.

**Метод** : `GET`

**Формат ответа:**
```
    'excerpt_hash' (str): хеш выписки с помощью которого можно ее получить
    'date_receive' (date): дата получения выписки,
```

## Получение выписке по хешу

Получение выписке в виде .xml файла по хешу

**URL** : `/excerpt/file`

**Обязательные параметры**

- `hash(str)` - хеш выписки

**Метод** : `GET`

**Формат ответа:** `#hash#.xml файл`
