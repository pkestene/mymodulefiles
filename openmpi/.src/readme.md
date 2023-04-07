# But why (compile openmpi) ?

Because :
First I noticed that currently (Ubuntu 22.04, OpenMPI 4.1.2), oshrun gives a seg fault when running any oshmem applications:

```shell
oshrun -np 4 ./a.out
[myhost:249799] Error ../../../../../oshmem/mca/memheap/base/memheap_base_static.c:249 - _load_segments() too many segments (max = 32): skip 7f1f6afff000-7f1f6b00c000 rw-p 00000000 00:00 0
[ladygaga:249799] ../../../../../../oshmem/mca/spml/ucx/spml_ucx.c:127  Error: Failed to get new mkey for segment: max number (32) of segment descriptor is exhausted
[ladygaga:249799] ../../../../../../oshmem/mca/spml/ucx/spml_ucx.c:223  Error: mca_spml_ucx_ctx_mkey_new failed
[ladygaga:249799] ../../../../../../oshmem/mca/spml/ucx/spml_ucx.c:736  Error: mca_spml_ucx_ctx_mkey_cache failed
[ladygaga:249799:0:249799] Caught signal 11 (Segmentation fault: address not mapped to object at address 0x49)
```
Second, I want to have cuda support enabled by default.

```shell
module load cuda/12.1
../../configure --disable-silent-rules --disable-wrapper-runpath --enable-mpi-cxx --enable-ipv6 --with-slurm --with-sge --without-tm --enable-mpi-fortran=no --with-cuda --prefix=$HOME/local/openmpi-4.1.4-cuda-12.1
make -j 12
make install
```
