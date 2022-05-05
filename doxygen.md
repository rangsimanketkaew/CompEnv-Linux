# Doxygen

```
sudo apt-get install cmake
sudo apt-get install flex
sudo apt-get install bison

git clone https://github.com/doxygen/doxygen.git
cd doxygen
mkdir build
cd build
cmake -G "Unix Makefiles" ..
make -j 8
sudo make -j # to install doxygen in /usr/local/bin/
```
