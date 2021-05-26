# vce-wheelhouse
Wheelhouse for cross-platform pip wheels.

Wheels natively built on Raspberry Pi 32 (`linux/arm/v7` / `armv7l`) and 64 bit (`linux/arm64` / `arm64`) operating systems for use in VCE cross-builds.

Index page from: https://opencomputinglab.github.io/vce-wheelhouse/

Usage: 

```
 echo regex lxml | xargs -n 1 pip install --no-cache --find-links= https://opencomputinglab.github.io/vce-wheelhouse
 ```

*Github Pages published wheelhouse structure based by on `https://github.com/parkin/python-wheelhouse`.*


Wheel creation — for example:

```
!mkdir -p wheelhouse
%pip wheel --wheel-dir=./wheelhouse scipy
```
