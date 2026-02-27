## Pydantic
* Pydantic is the most widely used data validation library for Python.

## Why use Pydantic?
* __Powered by type hints__ : with Pydantic, schema validation and serialization are controlled by type annotations; less to learn, less code to write, and integration with your IDE and static analysis tools.
* __Speed__ : Pydantic's core validation logic is written in Rust. As a result, Pydantic is among the fastest data validation libraries for Python
* __JSON Schema__: Pydantic models can emit JSON Schema, allowing for easy integration with other tools. 
* __Strict and Lax mode__: Pydantic can run in either strict mode (where data is not converted) or lax mode where Pydantic tries to coerce data to the correct type where appropriate.
* __Dataclasses, TypedDicts and more__: Pydantic supports validation of many standard library types including dataclass and TypedDict.
* __Customisation__: Pydantic allows custom validators and serializers to alter how data is processed in many powerful ways.

## Do Pydantic models have all dataclass properties?
* ❌ Not all
* ✅ Most of the commonly used ones
* ➕ Many extra features dataclasses don’t have

| Feature                     | `@dataclass` | `pydantic.BaseModel`                  |
| --------------------------- | ------------ | ------------------------------------- |
| Auto `__init__`             | ✅            | ✅                                     |
| Type annotations            | ✅            | ✅ (mandatory)                         |
| Default values              | ✅            | ✅                                     |
| `__repr__`                  | ✅            | ✅                                     |
| Equality (`==`)             | ✅            | ✅                                     |
| Immutability (`frozen`)     | ✅            | ✅ (`model_config = {"frozen": True}`) |
| Field validation            | ❌            | ✅                                     |
| Type coercion               | ❌            | ✅                                     |
| Serialization (`dict/json`) | ❌ (manual)   | ✅                                     |
| Optional fields             | ✅            | ✅                                     |
| Default factories           | ✅            | ✅                                     |
| Inheritance                 | ✅            | ✅                                     |
| Performance (pure Python)   | ✅ Faster     | ❌ Slightly slower                     |
| Stdlib only                 | ✅            | ❌ External lib                        |
