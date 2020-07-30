# GS PY Config

Configuration class

![Python package](https://github.com/guionardo/py-config/workflows/Python%20package/badge.svg)
[![codecov](https://codecov.io/gh/guionardo/py-config/branch/develop/graph/badge.svg)](https://codecov.io/gh/guionardo/py-config)


## USAGE

``` python
from config_guiosoft import ConfigClass, ConfigType
from datetime import datetime, date


class Config(ConfigClass):
    STRING_CONF = ""
    INT_CONF = 0
    FLOAT_CONF = 0.0
    BOOL_CONF = False
    DEFAULT_CONF = None
    DATE = date.today()
    DATETIME = datetime.now()


class SpecialConfig(ConfigClass):
    STRING_CONF = ConfigType(
        'STRING_CONF', str, 'DEFAULT_STRING', lambda value: len(value) > 1)
    INT_CONF = ConfigType(
        'INT_CONF', int, 100, range(1000))
    FLOAT_CONF = ConfigType(
        "FLOAT_CONF", float, 0.5, [0, 0.1, 0.5, 3.14])
    BOOL_CONF = ConfigType(
        "BOOL_CONF", bool, False)
    DEFAULT_CONF = ConfigType("DEFAULT_CONF")
    DATE = ConfigType(
        "DATE", date, date.today(), lambda value: value <= date.today())
    DATETIME = ConfigType(
        "DATETIME", datetime, datetime.now(),
        lambda value: value <= datetime.now())
```