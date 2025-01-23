# Setup-g6k-with-ntru
First do,  
``` console
sudo apt-get update  
sudo apt-get upgrade  
sudo apt-get install build-essential --install-suggests  
```

## Then, install qd:  
use the following link or download the file available in repository:  
``` console
wget https://www.davidhbailey.com/dhbsoftware/qd-2.3.24.tar.gz  
tar -xf qd-2.3.24.tar.gz  
cd qd-2.3.24  
./configure --enable-shared=yes  
sudo make install  
```

# To install sage:  
source: https://sagemanifolds.obspm.fr/install_ubuntu.html  
Install following packages:
``` console
sudo apt install automake bc binutils bzip2 ca-certificates cliquer cmake curl ecl eclib-tools fflas-ffpack flintqs g++ gengetopt gfan gfortran git glpk-utils gmp-ecm lcalc libatomic-ops-dev libboost-dev libbraiding-dev libbz2-dev libcdd-dev libcdd-tools libcliquer-dev libcurl4-openssl-dev libec-dev libecm-dev libffi-dev libflint-dev libfreetype-dev libgc-dev libgd-dev libgf2x-dev libgiac-dev libgivaro-dev libglpk-dev libgmp-dev libgsl-dev libhomfly-dev libiml-dev liblfunction-dev liblrcalc-dev liblzma-dev libm4rie-dev libmpc-dev libmpfi-dev libmpfr-dev libncurses-dev libntl-dev libopenblas-dev libpari-dev libpcre3-dev libplanarity-dev libppl-dev libprimesieve-dev libpython3-dev libqhull-dev libreadline-dev librw-dev libsingular4-dev libsqlite3-dev libssl-dev libsuitesparse-dev libsymmetrica2-dev zlib1g-dev libzmq3-dev libzn-poly-dev m4 make nauty openssl palp pari-doc pari-elldata pari-galdata pari-galpol pari-gp2c pari-seadata patch perl pkg-config planarity ppl-dev python3-setuptools python3-venv r-base-dev r-cran-lattice singular sqlite3 sympow tachyon tar tox xcas xz-utils
```

``` console
git clone --branch master https://github.com/sagemath/sage.git  
cd sage
make configure  
./configure  
MAKE="make -j8" make     #“8 is number of threads”  
```

## To create a simulink to access sage run the following command:  
``` console
sudo ln -sf $(pwd)/sage /usr/local/bin  
```

## G6k on github:
``` console
git clone https://github.com/fplll/g6k
```

## To make fplll recognize 'qd':  
In g6k ./bootstrap.sh file: edit ./bootstrap.sh file in g6k  
``` console
git clone https://github.com/fplll/fplll
cd fplll
./configure --with-qd 
sudo make install
cd ..  
```

## You might need to install gmp manually, use the following command:  
``` console
sudo apt-get install libgmp3-dev
```

## You might need to install mpfr manually, use the following command:
### Drop some packages if not available: 
``` console
sudo apt-get install libmpfr-dev libmpfr-doc libmpfr4 libmpfr4-dbg  
```

## NTRU with Sieving on github:
``` console
git clone https://github.com/ElenaKirshanova/ntru_with_sieving
```
