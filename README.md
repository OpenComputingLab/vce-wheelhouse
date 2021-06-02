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
%pip wheel --wheel-dir=./wheelhouse yarl tornado pyzmq
%pip wheel --wheel-dir=./wheelhouse PyICU Pillow PyYAML SQLAlchemy aiohttp regex
%pip wheel --wheel-dir=./wheelhouse multidict lxml kiwisolver matplotlib
%pip wheel --wheel-dir=./wheelhouse pandas
%pip wheel --wheel-dir=./wheelhouse scipy
%pip wheel --wheel-dir=./wheelhouse h5py
%pip wheel --wheel-dir=./wheelhouse scikit_learn
%pip wheel --wheel-dir=./wheelhouse psycopg2-binary
%pip wheel --wheel-dir=./wheelhouse numexpr tables statsmodels
%pip wheel --wheel-dir=./wheelhouse pymongo psycopg2 psutil
%pip wheel --wheel-dir=./wheelhouse Fiona Shapely pyproj
%pip wheel --wheel-dir=./wheelhouse Fiona Shapely pynacl geopandas
```

Requirements for VCE wheels:

```
apt-get update && \
    apt-get install -y --no-install-recommends ffmpeg dvipng cm-super && \
    # Pillow support? libblis2-serial <-> libblis3-serial
    apt-get install -y libopenblas-dev libblis3-serial libjpeg-dev zlib1g-dev libfreetype6-dev libopenjp2-7 libtiff5
    
apt-get install -y --no-install-recommends ffmpeg dvipng cm-super && \
    apt-get install --upgrade -y libhdf5-dev gfortran libatlas-base-dev libopenblas-dev liblapack-dev

apt-get update && apt-get install -y libproj-dev \
  gdal-bin \
  libgdal-dev
```

To create a wheelhouse index file based on the wheels in a directory, there's a function in the `index_builder.ipynb` notebook. The wheelhouse itself can be published via Github Pages.

To enter a container to update Linux packages, eg:

```
docker exec -it -u 0  wheelbuild /bin/bash

apt-get update && apt-get install -y PACKAGE
```
