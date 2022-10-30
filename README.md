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
        - [600.perlbench_s](#600perlbench_s)
            + [構建](#構建)
            + [執行](#執行)
            + [搬運](#搬運)
        - [602.gcc_s](#602gcc_s)
            + [構建](#構建-1)
            + [執行](#執行-1)
            + [搬運](#搬運-1)
+ [Deprecated](#deprecated)
+ [SPEC CPU®2006](#spec-cpu2006)

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
sudo apt install -y g++-aarch64-linux-gnu
```

## SPEC CPU®2017

### 安裝

```zsh
sudo mount -t iso9660 cpu2017-1.0.5.iso /mnt

/mnt/install.sh -d ${HOME}/speccpu2017

sudo umount /mnt
```

### 配置

```zsh
cd speccpu2017

cp config/Example-gcc-linux-x86.cfg config/test.cfg

which aarch64-linux-gnu-gcc aarch64-linux-gnu-g++
```

-   config/test.cfg

```apacheconf
%ifndef %{gcc_dir}
%   define  gcc_dir        /usr  # EDIT (see above)
%endif

   CC                      = $(SPECLANG)aarch64-linux-gnu-gcc  --static   -std=c99   %{model}
   CXX                     = $(SPECLANG)aarch64-linux-gnu-g++  --static   -std=c++03 %{model}
```

### 600.perlbench_s

#### 構建

```zsh
source shrc

runcpu -D -c test.cfg -i test -n 1 600.perlbench_s
```

#### 執行

```zsh
cd benchspec/CPU/600.perlbench_s/run/run_base_test_mytest-64.0000

specinvoke -n

./perlbench_s -I. -I./lib makerand.pl
./perlbench_s -I. -I./lib test.pl
```

#### 搬運

```zsh
scp -r misakisuna@192.168.30.34:~/speccpu2017/benchspec/CPU/600.perlbench_s ~/Downloads/SpecCpu2017
```

### 602.gcc_s

#### 構建

```zsh
source shrc

runcpu -D -c test.cfg -i test -n 1 602.gcc_s
```

#### 執行

```zsh
cd benchspec/CPU/602.gcc_s/run/run_base_test_mytest-64.0000

specinvoke -n

./sgcc_base.mytest-64 t1.c -O3 -finline-limit=50000 -o t1.opts-O3_-finline-limit_50000.s
```

#### 搬運

```zsh
scp -r misakisuna@192.168.30.34:~/speccpu2017/benchspec/CPU/602.gcc_s ~/Downloads/SpecCpu2017
```

# Deprecated

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

# SPEC CPU®2006

runspec --action run --config ft-rate-s2500-int.cfg --size test --tune base --iterations=1 400.perlbench
