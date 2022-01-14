# Boost C++ Library

Boost is a set of libraries for the C++ programming language that provides support for tasks and structures such as 
linear algebra, pseudorandom number generation, multithreading, image processing, regular expressions, and unit testing.

It contains more than 100 individual libraries.

## Compile from the source (system's default compiler)

1. Download the tarball to your machine and uncompress it
2. `cd` to the boost folder
3. `./bootstrap.sh --prefix=path/to/installation/prefix`
4. `./b2 install`
5. Both static (`*.a`) and dynamic (`*.so`) libraries will be built and stored in `lib` folder

Reference: Boost 1.70.0
https://www.boost.org/doc/libs/1_70_0/more/getting_started/unix-variants.html
