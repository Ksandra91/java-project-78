### Hexlet tests and linter status:
[![Actions Status](https://github.com/Ksandra91/java-project-78/actions/workflows/hexlet-check.yml/badge.svg)](https://github.com/Ksandra91/java-project-78/actions)

![Java CI](https://github.com/Ksandra91/java-project-78/actions/workflows/main.yml/badge.svg)

[![Maintainability](https://api.codeclimate.com/v1/badges/060975d606885a91d61b/maintainability)](https://codeclimate.com/github/Ksandra91/java-project-71/maintainability)

[![Test Coverage](https://api.codeclimate.com/v1/badges/060975d606885a91d61b/test_coverage)](https://codeclimate.com/github/Ksandra91/java-project-71/test_coverage)

Валидатор данных – библиотека, с помощью которой можно проверять корректность любых данных.
Пример использования:

```import hexlet.code.Validator;
import hexlet.code.schemas.StringSchema;
import hexlet.code.schemas.NumberSchema;
import hexlet.code.schemas.MapSchema;
import hexlet.code.schemas.BaseSchema;

Validator v = new Validator();

// Строки
StringSchema schema = v.string().required();

schema.isValid("what does the fox say"); // true
schema.isValid(""); // false

// Числа
NumberSchema schema = v.number().required().positive();

schema.isValid(-10); // false
schema.isValid(10); // true

// Объект Map с поддержкой проверки структуры
Map<String, BaseSchema> schemas = new HashMap<>();
schemas.put("name", v.string().required());
schemas.put("age", v.number().positive());

MapSchema schema = v.map().sizeof(2).shape(schemas);

Map<String, Object> human1 = new HashMap<>();
human1.put("name", "Kolya");
human1.put("age", 100);
schema.isValid(human1); // true

Map<String, Object> human2 = new HashMap<>();
human2.put("name", "");
human2.put("age", null);
schema.isValid(human2); // false
```

