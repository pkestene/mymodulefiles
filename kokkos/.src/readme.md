# Kokkos sources

```shell
git clone git@github.com:kokkos/kokkos.git
cd kokkos
git checkout 3.6.01
```

# Build Kokkos for OpenMP with gnu tool toolchain

```shell
export GNU_VERSION=11
export KOKKOS_VERSION=3.6.01
module load gnu/$GNU_VERSION
cd kokkos
BUILD_DIR=build/$KOKKOS_VERSION/openmp-gnu-$GNU_VERSION
mkdir -p $BUILD_DIR
cd $BUILD_DIR
cmake -DKokkos_ENABLE_OPENMP=ON -DKokkos_ENABLE_HWLOC=ON -DCMAKE_INSTALL_PREFIX=$HOME/local/kokkos-$KOKKOS_VERSION-openmp-gnu-$GNU_VERSION ../../..
make -j 6
make install
```

# Build Kokkos for OpenMP and CUDA with gnu tool toolchain

```shell
export GNU_VERSION=11
export KOKKOS_VERSION=3.6.01
export CUDA_VERSION=11.7
module load gnu/$GNU_VERSION
module load cuda/$CUDA_VERSION
cd kokkos
# UVM OFF
BUILD_DIR=build/$KOKKOS_VERSION/cuda-$CUDA_VERSION-gnu-$GNU_VERSION
mkdir -p $BUILD_DIR
cd $BUILD_DIR
cmake -DKokkos_ENABLE_OPENMP=ON -DKokkos_ENABLE_HWLOC=ON -DKokkos_ENABLE_CUDA=ON -DKokkos_ENABLE_CUDA_LAMBDA=ON -DKokkos_ENABLE_CUDA_CONSTEXPR=ON -DKokkos_ENABLE_CUDA_UVM=OFF -DCMAKE_INSTALL_PREFIX=$HOME/local/kokkos-$KOKKOS_VERSION-cuda-$CUDA_VERSION-gnu-$GNU_VERSION ../../..
make -j 6
make install

# UVM ON
BUILD_DIR=build/$KOKKOS_VERSION/cuda-$CUDA_VERSION-uvm-gnu-$GNU_VERSION
mkdir -p $BUILD_DIR
cd $BUILD_DIR
cmake -DKokkos_ENABLE_OPENMP=ON -DKokkos_ENABLE_HWLOC=ON -DKokkos_ENABLE_CUDA=ON -DKokkos_ENABLE_CUDA_LAMBDA=ON -DKokkos_ENABLE_CUDA_CONSTEXPR=ON -DKokkos_ENABLE_CUDA_UVM=ON -DCMAKE_INSTALL_PREFIX=$HOME/local/kokkos-$KOKKOS_VERSION-cuda-$CUDA_VERSION-uvm-gnu-$GNU_VERSION ../../..
make -j 6
make install
```
