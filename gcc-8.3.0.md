1. Download gcc from https://ftp.gnu.org/gnu/gcc/
2. Run following commands
```sh
tar xzf gcc-8.3.0.tar.gz
cd gcc-8.3.0
./contrib/download_prerequisites
cd ..
mkdir gcc-build
cd gcc-build
$PWD/../gcc-8.3.0/configure \
  --prefix=/opt/gcc/8.3.0 \
  --enable-languages=c,c++,fortran \
  --disable-bootstrap \
  --disable-libquadmath \
  --disable-libquadmath-support \
  --disable-werror \
  --enable-gold \
  --disable-multilib
make
make install
```
