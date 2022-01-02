# Compiling

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
