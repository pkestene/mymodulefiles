# Kokkos sources

Retrieve the latest available release of kokkos : 4.3.01

```shell
git clone git@github.com:kokkos/kokkos.git
cd kokkos
git checkout 4.3.01
```

# Build Kokkos for OpenMP with gnu tool toolchain

```shell
cd kokkos

export GNU_VERSION=11
export KOKKOS_VERSION=4.3.01

module load gnu/$GNU_VERSION

CMAKE_BUILD_TYPE=RelWithDebInfo

BUILD_DIR=_build/$KOKKOS_VERSION/openmp-gnu-$GNU_VERSION-$CMAKE_BUILD_TYPE
mkdir -p $BUILD_DIR
cd $BUILD_DIR

INSTALL_DIR=$HOME/local/kokkos-$KOKKOS_VERSION-openmp-gnu-$GNU_VERSION-$CMAKE_BUILD_TYPE

cmake -DKokkos_ENABLE_OPENMP=ON -DKokkos_ENABLE_HWLOC=ON -DCMAKE_CXX_STANDARD=17 -DCMAKE_INSTALL_PREFIX=$INSTALL_DIR -DCMAKE_BUILD_TYPE=$CMAKE_BUILD_TYPE ../../..
make -j 6
make install
```

# Build Kokkos for OpenMP and CUDA with gnu tool toolchain

Note that cmake option `Kokkos_ENABLE_CUDA_LAMBDA` is deprecated since kokkos 4.3.01. Support for lambda function is required unconditionnally.

```shell
cd kokkos

export GNU_VERSION=11
export KOKKOS_VERSION=4.3.01
export CUDA_VERSION=12.3

module load gnu/$GNU_VERSION
module load cuda/$CUDA_VERSION

CMAKE_BUILD_TYPE=RelWithDebInfo

BUILD_DIR=_build/$KOKKOS_VERSION/cuda-$CUDA_VERSION-gnu-$GNU_VERSION-$CMAKE_BUILD_TYPE
mkdir -p $BUILD_DIR
cd $BUILD_DIR

INSTALL_DIR=$HOME/local/kokkos-$KOKKOS_VERSION-cuda-$CUDA_VERSION-gnu-$GNU_VERSION-$CMAKE_BUILD_TYPE

cmake -DKokkos_ENABLE_OPENMP=ON -DKokkos_ENABLE_HWLOC=ON -DCMAKE_CXX_STANDARD=17 -DKokkos_ENABLE_CUDA=ON -DKokkos_ENABLE_CUDA_CONSTEXPR=ON -DCMAKE_INSTALL_PREFIX=$INSTALL_DIR -DCMAKE_BUILD_TYPE=$CMAKE_BUILD_TYPE ../../..
make -j 6
make install
```
