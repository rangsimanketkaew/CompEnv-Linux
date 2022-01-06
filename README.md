# Compiling

## Compilers

| Language | Developer | Command | MPI  | OpenMP |
|----------|-----------|---------|------|--------|
| Fortran 77 | GNU | gfortran | mpif77 | gfortran -fopenmp |
| Fortran 90/95/03 | GNU | gfortran | mpif90 | gfortran -fopenmp |
| C | GNU | gcc (cc) | mpicc | gcc -fopenmp |
| C++ | GNU | g++ (c++) | mpicxx (mpic++, mpiCC) | g++ -fopenmp |
| Fortran 77 | PGI | pgfortran (pgf77) | mpif77 | pgfortran -mp |
| Fortran 90/95/03 | PGI | pgfortran (pgf90, pgf95) | mpif90 | pgfortran -mp |
| C | PGI | pgcc | mpicc | pgcc -mp |
| C++ | PGI | pgc++ | mpicxx (mpic++, mpiCC) | pgc++ -mp |
| Fortran 77/90/95/03 | Intel | ifort | mpifort (mpif90, mpif77) | ifort -openmp |
| C | Intel | icc | mpicc | icc -openmp |
| C++ | Intel | icpc | mpicxx (mpic++, mpiCC) | icpc -openmp |

## General compiler flags (GCC/Clang)

- `-g` - turn on debugging (so GDB gives more friendly output)
- `-Wall` - turns on most warnings
- `-std=c++11` - specify C++ version 11
- `-fPIC` - Position Independent Code to avoid error when building shared libraries for dynamic linking
- `-O0` - no optimization, faster compilation, better for debugging builds
- `-O1` - turn on optimizations - minimize code size
- `-O2` - turn on optimizations - maximize speed
- `-O3` - turn on higher level of optimizations, slow compiling-time, better for production builds
- `-OFast` - higher level of optimizations than `-O3`
- `-o <name>` - name of the output file
- `-c` - output an object file (.o)
- `-D_GLIBCXX_USE_CXX11_ABI=0` - if you use GCC 5 or higher
- `-I<include path>` - specify an include directory
- `-L<library path>` - specify a lib directory
- `-l<library>` - link with library lib<library>.a

## Tricks for C++ compilation

1. Parallelism: `-J N`, where `N` is number of jobs
2. Build on local disk instead of a network file system like NFS. SSD is better than HDD.
3. Upgrade to a newer version of gcc
4. The more RAM your machine has, the faster compilation
5. Guard condition for header

```cpp
#ifndef SOME_NAME_h
#define SOME_NAME_h

...

#endif
```

6. Forward declaration
```cpp
int sum(int, int);

int sum(int a, int b)
{
    return a+b;
}
```

7. unnamed or anonymous namespaces
```cpp
namespace {
...
}
```
