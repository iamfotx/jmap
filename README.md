# jmap

**jmap** is a lightweight JSON-to-struct mapper for C, using a simple schema system.

It lets you populate C structs from JSON without manually extracting every field — ideal for config files, API responses, or embedded systems.

---

## Features

- Minimal schema-based mapping
- Safe assignment with type checks
- Supports strings, integers, and booleans
- Works with JSON strings or files
- No macros, no runtime reflection

---

## Example

```c
typedef struct {
    char name[64];
    int age;
    bool active;
} Person;

Person p = {0};

JField fields[] = {
    {"name", J_STRING, p.name},
    {"age", J_INT, &p.age},
    {"active", J_BOOL, &p.active}
};

JSchema schema = { fields, 3 };

jmap_parse(json_str, &schema);
```

JSON input:
```json
{ "name": "Jake", "age": 27, "active": true }
```

---

## License

MIT
