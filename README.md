# Computational environment on Linux

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
