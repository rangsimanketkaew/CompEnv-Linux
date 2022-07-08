## Compile and install GCC

I tested with gcc 12.1.0.

1. Download a tarball of the gcc release from https://github.com/gcc-mirror/gcc/tags

2. Run the following commands
```
tar -xzvf TARBALL.tar.gz
cd gcc-*
sudo apt install flex
mkdir build
cd build
# if you want to install in /usr/, you need root!
../configure -v --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu --prefix=/usr/local/gcc-11.1.0 --enable-checking=release --enable-languages=c,c++,fortran --disable-multilib
make -j 16
sudo make install-strip
```

3. Setup environment in `~/.bashrc`
```
export PATH=/usr/local/gcc-12.1.0/bin:$PATH
export LD_LIBRARY_PATH=/usr/local/gcc-12.1.0/lib64:$LD_LIBRARY_PATH

# To let CMake know
export CC=/usr/local/gcc-11.1.0/bin/gcc
export CXX=/usr/local/gcc-11.1.0/bin/g++
export FC=/usr/local/gcc-11.1.0/bin/gfortran
```
and then `source` it

4. Usage
```
gcc --version
```
