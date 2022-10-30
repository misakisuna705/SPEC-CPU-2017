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
        - [602.gcc_s（Deprecated）](#602gcc_sdeprecated)
            + [構建](#構建-1)
            + [執行](#執行-1)
        - [605.mcf_s](#605mcf_s)
            + [構建](#構建-2)
            + [執行](#執行-2)
        - [619.lbm_s](#619lbm_s)
            + [構建](#構建-3)
            + [執行](#執行-3)
        - [620.omnetpp_s](#620omnetpp_s)
            + [構建](#構建-4)
            + [執行](#執行-4)
        - [623.xalancbmk_s](#623xalancbmk_s)
            + [構建](#構建-5)
            + [執行](#執行-5)
        - [625.x264_s](#625x264_s)
            + [構建](#構建-6)
            + [執行](#執行-6)
        - [631.deepsjeng_s](#631deepsjeng_s)
            + [構建](#構建-7)
            + [執行](#執行-7)
        - [638.imagick_s](#638imagick_s)
            + [構建](#構建-8)
            + [執行](#執行-8)
        - [641.leela_s](#641leela_s)
            + [構建](#構建-9)
            + [執行](#執行-9)
        - [644.nab_s](#644nab_s)
            + [構建](#構建-10)
            + [執行](#執行-10)
        - [657.xz_s](#657xz_s)
            + [構建](#構建-11)
            + [執行](#執行-11)
+ [Deprecated](#deprecated)
+ [Deprecated](#deprecated-1)
+ [Deprecated](#deprecated-2)
+ [Deprecated](#deprecated-3)
+ [Deprecated](#deprecated-4)
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
cd benchspec/CPU/600.perlbench_s/run/run_base_test_mytest-m64.0000

# specinvoke -n
./perlbench_s_base.mytest-m64 -I. -I./lib makerand.pl
./perlbench_s_base.mytest-m64 -I. -I./lib test.pl
```

### 602.gcc_s（Deprecated）

#### 構建

```zsh
source shrc

runcpu -D -c test.cfg -i test -n 1 602.gcc_s
```

#### 執行

```zsh
cd benchspec/CPU/602.gcc_s/run/run_base_test_mytest-m64.0000

# specinvoke -n
./sgcc_base.mytest-m64 t1.c -O3 -finline-limit=50000 -o t1.opts-O3_-finline-limit_50000.s
```

### 605.mcf_s

#### 構建

```zsh
source shrc

runcpu -D -c test.cfg -i test -n 1 605.mcf_s
```

#### 執行

```zsh
cd benchspec/CPU/605.mcf_s/run/run_base_test_mytest-m64.0000

# specinvoke -n
./mcf_s_base.mytest-m64 inp.in
```

### 619.lbm_s

#### 構建

```zsh
source shrc

runcpu -D -c test.cfg -i test -n 1 619.lbm_s
```

#### 執行

```zsh
cd benchspec/CPU/619.lbm_s/run/run_base_test_mytest-m64.0000

# specinvoke -n
./lbm_s_base.mytest-m64 20 reference.dat 0 1 200_200_260_ldc.of
```

### 620.omnetpp_s

#### 構建

```zsh
source shrc

runcpu -D -c test.cfg -i test -n 1 620.omnetpp_s
```

#### 執行

```zsh
cd benchspec/CPU/620.omnetpp_s/run/run_base_test_mytest-m64.0000

# specinvoke -n
./omnetpp_s_base.mytest-m64 -c General -r 0
```

### 623.xalancbmk_s

#### 構建

```zsh
source shrc

runcpu -D -c test.cfg -i test -n 1 623.xalancbmk_s
```

#### 執行

```zsh
cd benchspec/CPU/623.xalancbmk_s/run/run_base_test_mytest-m64.0000

# specinvoke -n
./xalancbmk_s_base.mytest-m64 -v test.xml xalanc.xsl
```

### 625.x264_s

#### 構建

```zsh
source shrc

runcpu -D -c test.cfg -i test -n 1 625.x264_s
```

#### 執行

```zsh
cd benchspec/CPU/625.x264_s/run/run_base_test_mytest-m64.0000

# specinvoke -n
./x264_s_base.mytest-m64 --dumpyuv 50 --frames 156 -o BuckBunny_New.264 BuckBunny.yuv 1280x720
```

### 631.deepsjeng_s

#### 構建

```zsh
source shrc

runcpu -D -c test.cfg -i test -n 1 631.deepsjeng_s
```

#### 執行

```zsh
cd benchspec/CPU/631.deepsjeng_s/run/run_base_test_mytest-m64.0000

# specinvoke -n
./deepsjeng_s_base.mytest-m64 test.txt
```

### 638.imagick_s

#### 構建

```zsh
source shrc

runcpu -D -c test.cfg -i test -n 1 638.imagick_s
```

#### 執行

```zsh
cd benchspec/CPU/638.imagick_s/run/run_base_test_mytest-m64.0000

# specinvoke -n
./imagick_s_base.mytest-m64 -limit disk 0 test_input.tga -shear 25 -resize 640x480 -negate -alpha Off test_output.tga
```

### 641.leela_s

#### 構建

```zsh
source shrc

runcpu -D -c test.cfg -i test -n 1 641.leela_s
```

#### 執行

```zsh
cd benchspec/CPU/641.leela_s/run/run_base_test_mytest-m64.0000

# specinvoke -n
./leela_s_base.mytest-m64 test.sgf
```

### 644.nab_s

#### 構建

```zsh
source shrc

runcpu -D -c test.cfg -i test -n 1 644.nab_s
```

#### 執行

```zsh
cd benchspec/CPU/644.nab_s/run/run_base_test_mytest-m64.0000

# specinvoke -n
./nab_s_base.mytest-m64 hkrdenq 1930344093 1000
```

### 657.xz_s

#### 構建

```zsh
source shrc

runcpu -D -c test.cfg -i test -n 1 657.xz_s
```

#### 執行

```zsh
cd benchspec/CPU/657.xz_s/run/run_base_test_mytest-m64.0000

# specinvoke -n
./xz_s_base.mytest-m64 cpu2006docs.tar.xz 4 055ce243071129412e9dd0b3b69a21654033a9b723d874b2015c774fac1553d9713be561ca86f74e4f16f22e664fc17a79f30caa5ad2c04fbc447549c2810fae 1548636 1555348 0
./xz_s_base.mytest-m64 cpu2006docs.tar.xz 4 055ce243071129412e9dd0b3b69a21654033a9b723d874b2015c774fac1553d9713be561ca86f74e4f16f22e664fc17a79f30caa5ad2c04fbc447549c2810fae 1462248 -1 1
./xz_s_base.mytest-m64 cpu2006docs.tar.xz 4 055ce243071129412e9dd0b3b69a21654033a9b723d874b2015c774fac1553d9713be561ca86f74e4f16f22e664fc17a79f30caa5ad2c04fbc447549c2810fae 1428548 -1 2
./xz_s_base.mytest-m64 cpu2006docs.tar.xz 4 055ce243071129412e9dd0b3b69a21654033a9b723d874b2015c774fac1553d9713be561ca86f74e4f16f22e664fc17a79f30caa5ad2c04fbc447549c2810fae 1034828 -1 3e
./xz_s_base.mytest-m64 cpu2006docs.tar.xz 4 055ce243071129412e9dd0b3b69a21654033a9b723d874b2015c774fac1553d9713be561ca86f74e4f16f22e664fc17a79f30caa5ad2c04fbc447549c2810fae 1061968 -1 4
./xz_s_base.mytest-m64 cpu2006docs.tar.xz 4 055ce243071129412e9dd0b3b69a21654033a9b723d874b2015c774fac1553d9713be561ca86f74e4f16f22e664fc17a79f30caa5ad2c04fbc447549c2810fae 1034588 -1 4e
./xz_s_base.mytest-m64 cpu2006docs.tar.xz 1 055ce243071129412e9dd0b3b69a21654033a9b723d874b2015c774fac1553d9713be561ca86f74e4f16f22e664fc17a79f30caa5ad2c04fbc447549c2810fae 650156 -1 0
./xz_s_base.mytest-m64 cpu2006docs.tar.xz 1 055ce243071129412e9dd0b3b69a21654033a9b723d874b2015c774fac1553d9713be561ca86f74e4f16f22e664fc17a79f30caa5ad2c04fbc447549c2810fae 639996 -1 1
./xz_s_base.mytest-m64 cpu2006docs.tar.xz 1 055ce243071129412e9dd0b3b69a21654033a9b723d874b2015c774fac1553d9713be561ca86f74e4f16f22e664fc17a79f30caa5ad2c04fbc447549c2810fae 637616 -1 2
./xz_s_base.mytest-m64 cpu2006docs.tar.xz 1 055ce243071129412e9dd0b3b69a21654033a9b723d874b2015c774fac1553d9713be561ca86f74e4f16f22e664fc17a79f30caa5ad2c04fbc447549c2810fae 628996 -1 3e
./xz_s_base.mytest-m64 cpu2006docs.tar.xz 1 055ce243071129412e9dd0b3b69a21654033a9b723d874b2015c774fac1553d9713be561ca86f74e4f16f22e664fc17a79f30caa5ad2c04fbc447549c2810fae 631912 -1 4
./xz_s_base.mytest-m64 cpu2006docs.tar.xz 1 055ce243071129412e9dd0b3b69a21654033a9b723d874b2015c774fac1553d9713be561ca86f74e4f16f22e664fc17a79f30caa5ad2c04fbc447549c2810fae 629064 -1 4
```

# Deprecated

# Deprecated

# Deprecated

# Deprecated

# Deprecated

```zsh
runcpu --fake --config test.cfg --size test --tune base --iterations=1 600.perlbench_s

cd benchspec/CPU/600.perlbench_s/build/build_base_mytest-64.0000

runspec --action run --config ft-rate-s2500-int.cfg --size test --tune base --iterations=1 400.perlbench
```

# SPEC CPU®2006

```zsh
scp -r misakisuna@192.168.30.34:~/speccpu2017/benchspec/CPU/602.gcc_s ~/Downloads/SpecCpu2017
```
