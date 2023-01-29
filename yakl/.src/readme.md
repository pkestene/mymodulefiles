Example of yakl build recipe using e.g. CUDA as a target architecture (YAKL_ARCH).

```shell
export GNU_VERSION=11
export CUDA_VERSION=11.8

module load gnu/$GNU_VERSION
module load cuda/$CUDA_VERSION

git clone git@github.com:pkestene/YAKL.git
cd YAKL
# switch to git branch that allows a full make install
git checkout fix/install_target

mkdir -p _build/cuda-$CUDA_VERSION
cd _build/cuda-$CUDA_VERSION
cmake -DYAKL_ARCH=CUDA -DYAKL_HAVE_MPI=ON -DYAKL_MANAGED_MEMORY=ON -DCMAKE_INSTALL_PREFIX=$HOME/local/yakl-cuda-$CUDA_VERSION ../..
make
make install
```
