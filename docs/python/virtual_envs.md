# Environment management

## Virtual Env module

Bundled with python 3.3+

For unix,

```
python -m venv venv
source venv/bin/activate
```

or Windows,

```
python -m venv venv
source venv/Script/activate
```

## Pipenv

```
pip install pipenv
pipenv --python 3.9 shell
```

Default behaviour is to store virtual env remnants in global repo rather than local.

## Poetry
