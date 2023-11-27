# Get the sources

```shell
git clone git@github.com:kokkos/kokkos-fortran-interop.git
```

# Build for openmp

```shell
cd kokkos-fortran-interop

GNU_VERSION=11
KOKKOS_VERSION=4.1.00

module load gnu/$GNU_VERSION
module load kokkos/$KOKKOS_VERSION-openmp-gnu-$GNU_VERSION

CMAKE_BUILD_TYPE=RelWithDebInfo

BUILD_DIR=_build/$KOKKOS_VERSION/openmp-gnu-$GNU_VERSION-$CMAKE_BUILD_TYPE
mkdir -p $BUILD_DIR
cd $BUILD_DIR

INSTALL_DIR=$HOME/local/kokkos-flcl-$KOKKOS_VERSION-openmp-gnu-$GNU_VERSION-$CMAKE_BUILD_TYPE

cmake -DCMAKE_BUILD_TYPE=$CMAKE_BUILD_TYPE -DFLCL_BUILD_EXAMPLES=ON -DCMAKE_INSTALL_PREFIX=$INSTALL_DIR ../../..
make -j 6
make install
```

# Build for cuda

```shell
cd kokkos-fortran-interop

GNU_VERSION=11
CUDA_VERSION=12.3
KOKKOS_VERSION=4.1.00

CMAKE_BUILD_TYPE=RelWithDebInfo

module load gnu/$GNU_VERSION
module load cuda/$CUDA_VERSION
module load kokkos/$KOKKOS_VERSION-cuda-$CUDA_VERSION-gnu-$GNU_VERSION-$CMAKE_BUILD_TYPE

BUILD_DIR=_build/$KOKKOS_VERSION/cuda-$CUDA_VERSION-gnu-$GNU_VERSION-$CMAKE_BUILD_TYPE
mkdir -p $BUILD_DIR
cd $BUILD_DIR

INSTALL_DIR=$HOME/local/kokkos-flcl-$KOKKOS_VERSION-cuda-$CUDA_VERSION-gnu-$GNU_VERSION-$CMAKE_BUILD_TYPE

cmake -DCMAKE_BUILD_TYPE=$CMAKE_BUILD_TYPE -DFLCL_BUILD_EXAMPLES=ON -DCMAKE_INSTALL_PREFIX=$INSTALL_DIR ../../..
make -j 6
make install
```
