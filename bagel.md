# Bagel

## Requirement

Boost (v.1.70.0 rc2 works for me) [install](./boost.md)

## Compile bagel with Intel MPI & MKL

1. Download latest stable release, e.g. v1.2.2 on the day of this writing: https://github.com/qsimulate-open/bagel/releases/tag/v1.2.2
2. Uncompress tarball
3. Load Intel module and activate MKL and MPI environment
    ```sh
    module load iparastudio-2019.1
    source /home/modules/i-para-studio/xe/2019.1/impi/2019.0.117/intel64/bin/mpivars.sh intel64
    source /home/modules/i-para-studio/xe/2019.1/mkl/bin/mklvars.sh intel64
    ```
    
4. Automake
    ```sh
    cd bagel
    glibtoolize (or, libtoolize)
    aclocal
    autoconf
    autoheader
    automake -a
    ```

5. Configure
    ```sh
    mkdir obj
    cd obj
    
    export BOOST_ROOT=/path/to/boost
    export LD_LIBRARY_PATH=$BOOST_ROOT/lib:$LD_LIBRARY_PATH

    ../configure CXXFLAGS="-DNDEBUG -O3 -mavx" \
        --enable-mkl --with-boost=$BOOST_ROOT \
        --with-mpi=intel --prefix=path/to/install/bagel-1.2.2/    
    ```

6. Compile bagel
    ```sh
    make -j8
    make -j8 install
    ```

7. Test bagel
    ```sh
    mpirun -np 2 path/to/install/bagel-1.2.2/bin/BAGEL test/ch2_sto3g_meci_opt.json
    ```
    Output example:
    ```sh
        * process grid (2, 1) will be used
      lub-c05                         
      lub-c05                         

    * using 16 threads per process

    ===============================================================
      BAGEL - Freshly leavened quantum chemistry                   
    ===============================================================

    *** Geometry ***

    { "atom" : "C", "xyz" : [     -7.866971,      5.313377,     -0.592330 ] },
    { "atom" : "H", "xyz" : [     -8.357249,      3.395294,     -0.361773 ] },
    { "atom" : "H", "xyz" : [     -7.821773,      7.081184,     -1.494701 ] },

    Number of auxiliary basis functions:      111
    ...
    ...
    ```

## Compile Bagel on Piz Daint

1. Load module
    ```sh
    module load daint-gpu
    module load Boost/1.70.0-CrayGNU-20.11
    module load gcc/10.3.0
    ```
    
2. Activate Intel MPI & MKL
    ```sh
    source /project/s1001/intel/mpi/2021.5.0/env/vars.sh intel64
    source /project/s1001/intel/mkl/2022.0.1/env/vars.sh intel64
    ```
    
3. Configure
    ```sh
    cd basel-1.2.2/obj
    
    ../configure CXXFLAGS="-DNDEBUG -O3" \
        --with-boost=/apps/daint/UES/jenkins/7.0.UP02-20.11/gpu/easybuild/software/Boost/1.70.0-CrayGNU-20.11/ \
        --with-mpi=intel --disable-scalapack \
        --with-include="-I/opt/cray/pe/libsci/20.09.1/GNU/8.1/x86_64/include/" \
        --prefix=path/to/install/bagel-1.2.2/
    ```
    
    Note:
    - I disable MKL & Scalapack.
    - If it fails, adding `--enable-static --disable-shared` might help.
    
4. Compile & install
    ```sh
    make -j12  # can take up to 1 hr.
    make install
    ```
