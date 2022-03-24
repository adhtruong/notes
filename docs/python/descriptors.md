# Descriptors

Sources

- https://realpython.com/python-descriptors/

## SQLAlchemy

SQLAlchemy extensively uses descriptors to give a convient way to construct queries by allowing filtering based on class attributes.

```python

```

## Typing

```python
import typing

_T = typing.TypeVar('_T')

class Mapped(typing,Generic[_T]):
    """Returns type for class attribute and actual value for instance."""

    if typing.TYPE_CHECKING:

        @typing.overload
        def __get__(self, instance: None, owner: Any) -> type[_T]:
            ...

        @typing.overload
        def __get__(self, instance: object, owner: Any) -> _T:
            ...

        def __get__(
            self, instance: object, owner: Any
        ) -> Union[type[_T], _T]:
            ...
```
