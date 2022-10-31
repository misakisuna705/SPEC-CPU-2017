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

cp -f config/Example-gcc-linux-aarch64.cfg config/test.cfg
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

touch ./600.perlbench_s.sh && chmod u+x ./600.perlbench_s.sh
specinvoke -n *.cmd | grep ../ | cut -f1 -d">" >> ./600.perlbench_s.sh

./600.perlbench_s.sh
```

### 602.gcc_s（Deprecated）

#### 構建

```zsh
source shrc

runcpu -D -c test.cfg -i test -n 1 602.gcc_s
```

#### 執行

```zsh
cd benchspec/CPU/602.gcc_s/run/run_base_test_mytest-64.0000

touch ./602.gcc_s.sh && chmod u+x ./602.gcc_s.sh
specinvoke -n *.cmd | grep ../ | cut -f1 -d">" >> ./602.gcc_s.sh

./602.gcc_s.sh
```

### 605.mcf_s

#### 構建

```zsh
source shrc

runcpu -D -c test.cfg -i test -n 1 605.mcf_s
```

#### 執行

```zsh
cd benchspec/CPU/605.mcf_s/run/run_base_test_mytest-64.0000

touch ./605.mcf_s.sh && chmod u+x ./605.mcf_s.sh
specinvoke -n *.cmd | grep ../ | cut -f1 -d">" >> ./605.mcf_s.sh

./605.mcf_s.sh
```

### 619.lbm_s

#### 構建

```zsh
source shrc

runcpu -D -c test.cfg -i test -n 1 619.lbm_s
```

#### 執行

```zsh
cd benchspec/CPU/619.lbm_s/run/run_base_test_mytest-64.0000

touch ./619.lbm_s.sh && chmod u+x ./619.lbm_s.sh
specinvoke -n *.cmd | grep ../ | cut -f1 -d">" >> ./619.lbm_s.sh

./619.lbm_s.sh
```

### 620.omnetpp_s

#### 構建

```zsh
source shrc

runcpu -D -c test.cfg -i test -n 1 620.omnetpp_s
```

#### 執行

```zsh
cd benchspec/CPU/620.omnetpp_s/run/run_base_test_mytest-64.0000

touch ./620.omnetpp_s.sh && chmod u+x ./620.omnetpp_s.sh
specinvoke -n *.cmd | grep ../ | cut -f1 -d">" >> ./620.omnetpp_s.sh

./620.omnetpp_s.sh
```

### 623.xalancbmk_s

#### 構建

```zsh
source shrc

runcpu -D -c test.cfg -i test -n 1 623.xalancbmk_s
```

#### 執行

```zsh
cd benchspec/CPU/623.xalancbmk_s/run/run_base_test_mytest-64.0000

touch ./623.xalancbmk_s.sh && chmod u+x ./623.xalancbmk_s.sh
specinvoke -n *.cmd | grep ../ | cut -f1 -d">" >> ./623.xalancbmk_s.sh

./623.xalancbmk_s.sh
```

### 625.x264_s

#### 構建

```zsh
source shrc

runcpu -D -c test.cfg -i test -n 1 625.x264_s
```

#### 執行

```zsh
cd benchspec/CPU/625.x264_s/run/run_base_test_mytest-64.0000

touch ./625.x264_s.sh && chmod u+x ./625.x264_s.sh
specinvoke -n *.cmd | grep ../ | cut -f1 -d">" >> ./625.x264_s.sh

./625.x264_s.sh
```

### 631.deepsjeng_s

#### 構建

```zsh
source shrc

runcpu -D -c test.cfg -i test -n 1 631.deepsjeng_s
```

#### 執行

```zsh
cd benchspec/CPU/631.deepsjeng_s/run/run_base_test_mytest-64.0000

touch ./631.deepsjeng_s.sh && chmod u+x ./631.deepsjeng_s.sh
specinvoke -n *.cmd | grep ../ | cut -f1 -d">" >> ./631.deepsjeng_s.sh

./631.deepsjeng_s.sh
```

### 638.imagick_s

#### 構建

```zsh
source shrc

runcpu -D -c test.cfg -i test -n 1 638.imagick_s
```

#### 執行

```zsh
cd benchspec/CPU/638.imagick_s/run/run_base_test_mytest-64.0000

touch ./638.imagick_s.sh && chmod u+x ./638.imagick_s.sh
specinvoke -n *.cmd | grep ../ | cut -f1 -d">" >> ./638.imagick_s.sh

./638.imagick_s.sh
```

### 641.leela_s

#### 構建

```zsh
source shrc

runcpu -D -c test.cfg -i test -n 1 641.leela_s
```

#### 執行

```zsh
cd benchspec/CPU/641.leela_s/run/run_base_test_mytest-64.0000

touch ./641.leela_s.sh && chmod u+x ./641.leela_s.sh
specinvoke -n *.cmd | grep ../ | cut -f1 -d">" >> ./641.leela_s.sh

./641.leela_s.sh
```

### 644.nab_s

#### 構建

```zsh
source shrc

runcpu -D -c test.cfg -i test -n 1 644.nab_s
```

#### 執行

```zsh
cd benchspec/CPU/644.nab_s/run/run_base_test_mytest-64.0000

touch ./644.nab_s.sh && chmod u+x ./644.nab_s.sh
specinvoke -n *.cmd | grep ../ | cut -f1 -d">" >> ./644.nab_s.sh

./644.nab_s.sh
```

### 657.xz_s

#### 構建

```zsh
source shrc

runcpu -D -c test.cfg -i test -n 1 657.xz_s
```

#### 執行

```zsh
cd benchspec/CPU/657.xz_s/run/run_base_test_mytest-64.0000

touch ./657.xz_s.sh && chmod u+x ./657.xz_s.sh
specinvoke -n *.cmd | grep ../ | cut -f1 -d">" >> ./657.xz_s.sh

./657.xz_s.sh
```
