# How to build emacs from source

Example build configure for recompiling emacs-29.3 :

```shell
../../configure --prefix=$HOME/local/emacs-29.3 --with-libsystemd --with-pop=yes --without-gconf --with-cairo --with-x=yes --with-x-toolkit=gtk3 --with-toolkit-scroll-bars
make -j 8
make install
```
