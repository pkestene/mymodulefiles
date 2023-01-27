Example of yakl build recipe using e.g. CUDA as a target architecture (YAKL_ARCH).

```shell
module load gnu/11
module load cuda/11.8

git clone git@github.com:pkestene/YAKL.git
cd YAKL
# switch to git branch that allows a full make install
git checkout fix/install_target

mkdir -p _build/cuda
cd _build/cuda
cmake -DYAKL_ARCH=CUDA -DYAKL_HAVE_MPI=ON -DYAKL_MANAGED_MEMORY=ON -DCMAKE_INSTALL_PREFIX=$HOME/local/yakl-cuda ../
make
make install
```
