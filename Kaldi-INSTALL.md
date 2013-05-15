hInstallation TIPS for KALDI and installation INSTRUCTIONS for my additional repositories
=================================================================================
Intro
-----
Kaldi has very good instructions and tutorial
for building it from source. It is easy and straightforward.
However, I needed also to build shared libraries
and maybe you will face some of my problems too.
So this is the reasons for writing my building procedure down.

Installing external dependencies
================================
See `kaldi-trunk/tools/INSTALL` for info.
Basically it telss you to use `kaldi-trunk/tools/Makefile`, which I used also.

How I installed Atlas
--------------------
First of all I decided to try OpenBlas. 
It is open source and it allows me to compile both shared and static libraries at one run.
Nevertheless:
 * I installed version atlas3.10.1.tar.bz2 (available at sourceforge)
 * I unpackaged it under `kaldi-trunk/tools` which created `kaldi-trunk/tools/ATLAS`
 * The main problem with building ATLAS was for me disabling CPU throtling.
    * I solved it by 
```bash
# running following command under root in my Ubuntu 12.10
# It does not turn off CPU throttling in fact, but I do not need the things optimaze on my local machine
# I ran it for all of my 4 cores
# for n in 0 1 2 3 ; do echo 'performance' > /sys/devices/system/cpu/cpu${n}/cpufreq/scaling_governor ; done

 * Then I needed to install Fortran compiler (The error from configure was little bit covered by consequent errors) by 
     ```bash
     sudo apt-get install gfortran
     ```
 * On Ubuntu 12.04 I had issue with 
    ```bash
    /usr/include/features.h:323:26: fatal error: bits/predefs.h
    ```
    Which I solved by
    ```bash
    sudo apt-get install --reinstall libc6-dev
    ```
 * Finally, in `kaldi-trunk/tools/ATLAS` I run:
 ```bash
 mkdir build 
 mkdir ../atlas_install
 cd build
../configure --shared --incdir=`pwd`/../../atlas_install
make 
make install
 ```

How I install OpenBlas
----------------------
Simple enough:
```bash
make openblas
```

How I installed Openfst
----------------------
In order to install also shared libraries
I changed the line 37 in 
`kaldi-trunk/tools/Makefile`

```sh
*** Makefile 
************
*** 34,38 ****

openfst-1.3.2/Makefile: openfst-1.3.2/.patched
		cd openfst-1.3.2/; \
!		./configure --prefix=`pwd` --enable-static --disable-shared --enable-far --enable-ngram-fsts

--- 34,38 ----

openfst-1.3.2/Makefile: openfst-1.3.2/.patched
		cd openfst-1.3.2/; \
!		./configure --prefix=`pwd` --enable-static --enable-shared --enable-far --enable-ngram-fsts

```
Than I ran
```bash
make openfst_tgt
```


Which tool for building a Language Model (LM) have I used?
---------------------------------------------------------
None. I got build LM in Arpa format.

NOTE: Probably, I should build my own LM. 


How I build Kaldi?
------------------
```bash
./configure --openblas-root=/home/ondra/school/diplomka/kaldi-trunk/tools/OpenBLAS/install --fst-root=`pwd`/../tools/openfst --static-math=no
```
```bash
EXTRA_CXXFLAGS=-fPIC make
```




How I update Kaldi src code?
----------------------------
I checkout the kaldi-trunk version.

[Kaldi install instructions](http://kaldi.sourceforge.net/install.html)

Note: If you checkout Kaldi before March 2013 you need to relocate svn. See the instructions in the link above!
