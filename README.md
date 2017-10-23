cbrf.py [![Unlicensed work](https://raw.githubusercontent.com/unlicense/unlicense.org/master/static/favicon.png)](https://unlicense.org/)
===============
[![PyPi Status](https://img.shields.io/pypi/v/cbrf.py.svg)](https://pypi.python.org/pypi/cbrf)
[![TravisCI Build Status](https://travis-ci.org/KOLANICH/cbrf.py.svg?branch=master)](https://travis-ci.org/KOLANICH/cbrf.py)
[![Coveralls Coverage](https://img.shields.io/coveralls/KOLANICH/cbrf.py.svg)](https://coveralls.io/r/KOLANICH/cbrf.py)
[![Libraries.io Status](https://img.shields.io/librariesio/github/KOLANICH/cbrf.py.svg)](https://libraries.io/github/KOLANICH/cbrf.py)

Gets currency exchange rates from [the official API](https://www.cbr.ru/scripts/root.asp) of [CentroBank of the Russian Federation](https://www.cbr.ru/) .

Disclaimer
----------
I AM NOT AFFILIATED WITH CENTROBANK.
POSTING THE LIBRARY HERE MUSTN'T BE UNDERSTOOD AS PROMOTING THE BANK, ITS EXCHANGE RATES OR ITS POSITION OR ANY FINANCIAL ADVISE.
THE LIBRARY IS POSTED HERE ONLY FOR CONVENIENCE FOR THE PEOPLE WHO HAVE TO USE THE EXCHANGE RATES BY CB RF.
I HOLD NO LIABILITY FOR ITS ACTIONS, CORRECTNESS OF DATA, EXCHANGE RATES, OR ANY OTHER LOSSES, LOST OR IMPLIED OR ASSUMED PROFIT, OR ANYTHING ELSE. PLEASE, SEE THE [(UN)LICENSE FILE](./UNLICENSE) FOR MORE INFO ABOUT THE LICENSE.


Getting the rates
----------
```python
from cbrf import CentroBank
cb=CentroBank()
print(cb.byISO["USD"])
```


```money``` integration
------------------
```python
import money
from cbrf import MoneyBackend
money.xrates.install(MoneyBackend())
money.Money(1, "USD").to("RUB")
```

```pint``` integration
------------------
!!! WARNING: FOR NOW IT DOESN'T USE ```Decimal``` type. Precision loss is likely to occur !!!
```python
import pint
from cbrf import populatePintUnitRegistry
ureg = pint.UnitRegistry(None)
populatePintUnitRegistry(ureg, cb.byISO.values())
ureg("1 USD").to(ureg.RUB)
```
