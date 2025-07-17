[🇨🇳 中文说明](./README.zh-CN.md) | [🇺🇸 English README](./README.md)

# RevBank

该工具可用于对测试系统的 DRAM 映射函数 进行逆向工程分析。
它主要执行如下任务：

- 恢复 BANK 冲突函数（bank conflict functions）



## 使用方法

```
./test [-h] [-s sets] [-r rounds] [-t threshold] [-o o_file] [-v] [--mem mem_size]

    -h                     = 显示帮助信息
    -s sets                = 预期的集合数量                  （默认值: 16）
    -r rounds              = 每组测试的迭代轮数                （默认值: 1000）
    -t threshold           = 判断是否冲突的时间阈值            （默认值: 325）
    -o o_file              = 输出内存访问时间的结果文件         
    --mem mem_size         = 分配内存的大小（单位：字节）       （默认: 5368709120，即5GB）
    -v                     = 输出详细信息（verbose 模式）
```

## 📌 关于参数说明：

**集合数量:**

预期的集合数量取决于实际的内存配置。例如，在常见的双 rank 单通道配置中，总共有 16 个 bank（即 16 个 set）。
你可以自行设定该值，如果不确定，设为 16 通常是一个安全的选择。

**时间阈值:**

可以先运行一次程序并使用 -o 参数输出访问时间数据，然后使用仓库中提供的 histogram.py 脚本绘制直方图。
根据图像判断合适的冲突时间阈值后，再将该阈值作为参数传给程序进行精确测试。