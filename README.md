# Setup G6K with NTRU (Tested on Ubuntu 20.04)

> ⚠️ Note: These instructions are tested on Ubuntu 20.04. Compatibility with later versions is not guaranteed.

---

## 1. System Update and Dependencies

```bash
sudo apt-get update  
sudo apt-get upgrade  
sudo apt-get install build-essential --install-suggests  
```

---

## 2. Install QD Library

You can either:
- Use the link below to download, or  
- Use the file already provided in this repository.

```bash
wget https://www.davidhbailey.com/dhbsoftware/qd-2.3.24.tar.gz  
tar -xf qd-2.3.24.tar.gz  
cd qd-2.3.24  
./configure --enable-shared=yes  
sudo make install  
```

---

## 3. Install SageMath

Reference: [Sage Manifolds Guide](https://sagemanifolds.obspm.fr/install_ubuntu.html)

### Step 1: Install Prerequisite Packages

```bash
sudo apt install automake bc binutils bzip2 ca-certificates cliquer cmake curl ecl eclib-tools fflas-ffpack flintqs g++ gengetopt gfan gfortran git glpk-utils gmp-ecm lcalc libatomic-ops-dev libboost-dev libbraiding-dev libbz2-dev libcdd-dev libcdd-tools libcliquer-dev libcurl4-openssl-dev libec-dev libecm-dev libffi-dev libflint-dev libfreetype-dev libgc-dev libgd-dev libgf2x-dev libgiac-dev libgivaro-dev libglpk-dev libgmp-dev libgsl-dev libhomfly-dev libiml-dev liblfunction-dev liblrcalc-dev liblzma-dev libm4rie-dev libmpc-dev libmpfi-dev libmpfr-dev libncurses-dev libntl-dev libopenblas-dev libpari-dev libpcre3-dev libplanarity-dev libppl-dev libprimesieve-dev libpython3-dev libqhull-dev libreadline-dev librw-dev libsingular4-dev libsqlite3-dev libssl-dev libsuitesparse-dev libsymmetrica2-dev zlib1g-dev libzmq3-dev libzn-poly-dev m4 make nauty openssl palp pari-doc pari-elldata pari-galdata pari-galpol pari-gp2c pari-seadata patch perl pkg-config planarity ppl-dev python3-setuptools python3-venv r-base-dev r-cran-lattice singular sqlite3 sympow tachyon tar tox xcas xz-utils
```

### Step 2: Clone and Build Sage

```bash
git clone --branch master https://github.com/sagemath/sage.git  
cd sage  
make configure  
./configure  
MAKE="make -j8" make     # Replace 8 with number of CPU threads  
```

### Step 3: Create a Symlink

```bash
sudo ln -sf $(pwd)/sage /usr/local/bin/sage
```

---

## 4. Clone G6K

```bash
git clone https://github.com/fplll/g6k  
cd g6k
```

---

## 5. Set Up `fplll` with QD Support

Modify `./bootstrap.sh` in the G6K directory to include the following:

```bash
git clone https://github.com/fplll/fplll  
cd fplll  
./configure --with-qd  
sudo make install  
cd ..  
```

---

## 6. Build G6K Environment

After modifying the script, run:

```bash
./bootstrap.sh [-j #]   # Replace # with number of threads, e.g., 8
```

This will build `fpylll` and install dependencies.

---

## 7. Additional Dependencies (Optional)

You may need to install GMP and MPFR manually:

```bash
sudo apt-get install libgmp3-dev  
sudo apt-get install libmpfr-dev libmpfr-doc libmpfr4 libmpfr4-dbg
```

Then rerun:

```bash
./bootstrap.sh [-j #]
```

---

## 8. Install `mod` and `sympy` (for solving LWE instances)

Inside the G6K environment, run:

```bash
pip install mod sympy
```

---

## 9. Clone and Integrate NTRU with Sieving

```bash
git clone https://github.com/ElenaKirshanova/ntru_with_sieving
```

Copy the contents of `ntru_with_sieving` into the `g6k` directory.

You can now run NTRU instances using G6K. Refer to `run-lwe-ntru-instances` for command examples.

---

## 10. Optional: CUDA Toolkit for G6K-GPU

Follow the official NVIDIA installation instructions:  
[NVIDIA CUDA Downloads](https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&Distribution=Ubuntu&target_version=20.04&target_type=deb_local)

---

## ✅ Summary

- You now have SageMath, QD, fplll, fpylll, and G6K set up.
- NTRU instances can be tested using the provided scripts.
- Ensure you're in the right environment when installing Python packages or running experiments.

