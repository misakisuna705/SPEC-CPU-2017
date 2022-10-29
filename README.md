# SPEC CPU®2017

<!-- vim-markdown-toc GFM -->

* [參數](#參數)
    - [系統](#系統)
    - [目標](#目標)
* [環境](#環境)
    - [cross compiler](#cross-compiler)
* [SPEC CPU®2017](#spec-cpu2017)
    - [安裝](#安裝)
    - [配置](#配置)
    - [構建](#構建)
    - [執行](#執行)

<!-- vim-markdown-toc -->

---

## 參數

### 系統

-   Ubuntu 18.04（WSL）

### 目標

-   arm64

## 環境

### cross compiler

```zsh
sudo apt install -y gcc-aarch64-linux-gnu
```

## SPEC CPU®2017

### 安裝

```zsh
sudo mount -t iso9660 cpu2017-1.0.5.iso /mnt

/mnt/install.sh -d ${HOME}/speccpu2017

umount /mnt
```

### 配置

```zsh
cd speccpu2017
source shrc

cp config/Example-gcc-linux-aarch64.cfg config/test.cfg

which gcc g++ gfortrain
/usr/bin/gcc
/usr/bin/g++
```

-   config/test.cfg

```apacheconf
define gcc_dir /usr
```

### 構建

```zsh
runcpu --fake --config test.cfg --size test --tune base --iterations=1 600.perlbench_s

cd benchspec/CPU/600.perlbench_s/build/build_base_mytest-64.0000
```

-   Makefile.spec

```make
CC               = $(SPECLANG)gcc     -std=c99   -mabi=lp64   --static
CXX              = $(SPECLANG)g++     -std=c++03 -mabi=lp64   --static
```

```zsh
specmake clean

specmake
```

```zsh
cp benchspec/CPU/600.perlbench_s/build/build_base_mytest-64.0000/perlbench_s benchspec/CPU/600.perlbench_s/run/run_base_test_mytest-64.0000
```

### 執行

```zsh
cd benchspec/CPU/600.perlbench_s/run/run_base_test_mytest-64.0000

specinvoke -n

./perlbench_s -I. -I./lib makerand.pl
./perlbench_s -I. -I./lib test.pl
```
