# Location

```shell
cd ~/install/fftw/fftw-3.3.10
```

# Prepare autotools

```shell
autoreconf --verbose --install --symlink --force
```

# GNU 11.2 (Ubuntu 22.04)

```shell
mkdir build/autotools-gnu-11.2
cd build/autotools-gnu-11.2
../../configure --prefix=$HOME/local/fftw-3.3.10-gnu-11.2 CC=gcc-11 FC=gfortran-11 CXX=g++-11
../../configure --prefix=$HOME/local/fftw-3.3.10-gnu-11.2 --enable-float CC=gcc-11 FC=gfortran-11 CXX=g++-11

make -j 6
make install
```

# nvhpc

```shell
mkdir build/cmake-nvhpc-22.7
cd build/cmake-nvhpc-22.7

cmake -DCMAKE_INSTALL_PREFIX=$HOME/local/fftw-3.3.10-nvhpc-22.7 ../..
cmake -DCMAKE_INSTALL_PREFIX=$HOME/local/fftw-3.3.10-nvhpc-22.7 -DENABLE_FLOAT=ON ../..
make -j 6
make install
```
