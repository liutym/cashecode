# 编译运行模拟器

ChampSim采用JSON配置脚本。检查完全指定的示例。此文件中描述的所有选项都是可选的，如果未指定，将替换为默认值。配置脚本也可以在没有输入的情况下运行，在这种情况下，假定文件为空，需要更改策略可以编辑champsim_config.json文件


```python
$ ./config.sh <configuration file>
$ make
```

# DPC-3 跟踪

跟踪文件已经下载，文件名为600.perlbench_s-210B.champsimtrace.xz

# 添加您自己的分支预测器、数据预取程序和替换策略


```python
$ mkdir prefetcher/mypref
$ cp prefetcher/no_l2c/no.cc prefetcher/mypref/mypref.cc
```

编译和测试将预取程序添加到配置文件，Mockingjay源代码已经下载放在prefetcher/Mockingjay文件夹下


```python
{
    "LLC": {
        "prefetcher": "mypref"
    }
}
```

运行二进制文件


```python
$ bin/champsim --warmup_instructions 200000000 --simulation_instructions 500000000 ./600.perlbench_s-210B.champsimtrace.xz
```
