# Get the sources

```shell
git clone git@github.com:kokkos/kokkos-fortran-interop.git
```

# Build for openmp

```shell
cd kokkos-fortran-interop
GNU_VERSION=11
KOKKOS_VERSION=3.7.00

module load gnu/$GNU_VERSION
module load kokkos/$KOKKOS_VERSION-openmp-gnu-$GNU_VERSION

BUILD_DIR=build/$KOKKOS_VERSION-openmp-gnu-$GNU_VERSION
mkdir -p $BUILD_DIR
cd $BUILD_DIR
cmake -DCMAKE_BUILD_TYPE=Release -DBUILD_EXAMPLES=ON -DCMAKE_INSTALL_PREFIX=$HOME/local/kokkos-flcl-$KOKKOS_VERSION-openmp-gnu-$GNU_VERSION ../..
make -j 6
make install
```

# Build for cuda

```shell
cd kokkos-fortran-interop
GNU_VERSION=11
CUDA_VERSION=11.8
KOKKOS_VERSION=3.7.00

module load gnu/$GNU_VERSION
module load cuda/$CUDA_VERSION
module load kokkos/$KOKKOS_VERSION-cuda-$CUDA_VERSION-gnu-$GNU_VERSION

BUILD_DIR=build/$KOKKOS_VERSION-cuda-$CUDA_VERSION-gnu-$GNU_VERSION
mkdir -p $BUILD_DIR
cd $BUILD_DIR
cmake -DCMAKE_BUILD_TYPE=Release -DBUILD_EXAMPLES=ON -DCMAKE_INSTALL_PREFIX=$HOME/local/kokkos-flcl-$KOKKOS_VERSION-cuda-$CUDA_VERSION-gnu-$GNU_VERSION ../..

make -j 6
make install
```
