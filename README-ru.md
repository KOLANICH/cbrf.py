cbrf.py [![Unlicensed work](https://raw.githubusercontent.com/unlicense/unlicense.org/master/static/favicon.png)](https://unlicense.org/)
===============
[![PyPi Status](https://img.shields.io/pypi/v/cbrf.py.svg)](https://pypi.python.org/pypi/cbrf)
[![TravisCI Build Status](https://travis-ci.org/KOLANICH/cbrf.py.svg?branch=master)](https://travis-ci.org/KOLANICH/cbrf.py)
[![Coveralls Coverage](https://img.shields.io/coveralls/KOLANICH/cbrf.py.svg)](https://coveralls.io/r/KOLANICH/cbrf.py)
[![Libraries.io Status](https://img.shields.io/librariesio/github/KOLANICH/cbrf.py.svg)](https://libraries.io/github/KOLANICH/cbrf.py)

Библиотека получает курсы обмена валют через [официальное API](https://www.cbr.ru/scripts/root.asp) [Центробанка РФ](https://www.cbr.ru/) .

Внимание
----------------
Я НЕ РАБОТАЮ НА ЦЕНТРОБАНК И НЕ СВЯЗАН С НИМ.
ПУБЛИКАЦИЯ ЭТОЙ БИБЛИОТЕКИ НЕ ДОЛЖНА ПОНИМАТЬСЯ КАК ПРОДВИЖЕНИЕ БАНКА, УСТАНОВЛЕННЫХ ИМ ОБМЕННЫХ КУРСОВ ИЛИ ЕГО ПОЗИЦИИ, ИЛИ КАК СОВЕТ.
БИБЛИОТЕКА ОПУБЛИКОВАНА ЗДЕСЬ ИСКЛЮЧИТЕЛЬНО ДЛЯ УДОБСТВА ЛЮДЕЙ, КОТОРЫМ ПРИХОДИТСЯ ИСПОЛЬЗОВАТЬ ОБМЕННЫЕ КУРСЫ ЦЕНТРОБАНКА.
Я НЕ НЕСУ ОТВЕТСТВЕННОСТИ ЗА ЕГО ДЕЙСТВИЯ, ДОСТОВЕРНОСТЬ ДАННЫХ, ОБМЕННЫЕ КУРСЫ, ЛЮБЫЕ ДРУГИЕ ПОТЕРИ ИЛИ УБЫТКИ, ПОТЕРЯННУЮ, ПОДРАЗУМЕВАЕМУЮ ИЛИ ВЫДУМАННУЮ ПРИБЫЛЬ, И ВООБЩЕ ЧТО ЛИБО. ПОЖАЛУЙСТА, ПРОСМОТРИТЕ [ФАЙЛ С (РАЗ)ЛИЦЕНЗИЕЙ](./UNLICENSE) ДЛЯ БОЛЕЕ ПОДРОБНОЙ ИНФОРМАЦИИ О ЛИЦЕНЗИИ.


Получение курсов
-----------------------------
```python
from cbrf import CentroBank
cb=CentroBank()
print(cb.byISO["USD"])
```


использование с ```money```
------------------
```python
import money
from cbrf import MoneyBackend
money.xrates.install(MoneyBackend())
money.Money(1, "USD").to("RUB")
```

использование с pint
------------------
!!! Внимание: на данный момент не используется тип ```Decimal``` . Вероятна потеря точности !!!
```python
import pint
from cbrf import populatePintUnitRegistry
ureg = pint.UnitRegistry(None)
populatePintUnitRegistry(ureg, cb.byISO.values())
ureg("1 USD").to(ureg.RUB)
```
