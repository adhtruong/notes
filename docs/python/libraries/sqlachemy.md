# SQLAlchemy

- [Docs](https://www.sqlalchemy.org/)

## Usage

```txt title='requirements.txt'
SQLAlchemy==1.4.36
```

```python title='sqlalchemy_example.py'
from typing import Optional
from sqlalchemy import Column, Integer, String, create_engine, select
from sqlalchemy.orm import declarative_base, Session, DeclarativeMeta

Base: DeclarativeMeta = declarative_base()


class Author(Base):
    __tablename__ = "authors"

    id: int = Column(Integer, primary_key=True)
    name: str = Column(String, nullable=False)
    age: Optional[int] = Column(Integer, nullable=True)

    def __str__(self) -> str:
        return f"Author(id={self.id}, name={self.name}, age={self.age})"


def main() -> None:
    engine = create_engine("sqlite:///:memory:", future=True, echo=True)
    Base.metadata.create_all(bind=engine)

    with Session(bind=engine) as session:
        session.add(Author(id=1, name="John", age=None))
        session.add(Author(id=2, name="Paul", age=22))

        select_statement = select(Author)
        for author in session.execute(select_statement).scalars():
            print(author)


if __name__ == "__main__":
    main()
```
