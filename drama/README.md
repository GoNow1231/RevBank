[🇨🇳 中文说明](./README.zh-CN.md) | [🇺🇸 English README](./README.md)

# RevBank

This tool can be used to reverse engineer the DRAM mapping functions of the test system.
It carries out  tasks: 

- Recovering the bank conflicts functions 


## Usage

```
./test [-h] [-s sets] [-r rounds] [-t threshold] [-o o_file] [-v] [--mem mem_size]
          -h                     = this help message
          -s sets                = number of expected sets            (default: 16)
          -r rounds              = number of rounds per tuple         (default: 1000)
          -t threshold           = time threshold for conflicts       (default: 325)
          -o o_file              = output file for mem profiling      
          --mem mem_size         = allocation size                    (default: 5368709120)
          -v                     = verbose
```
 
**Number of sets:**

- The number of expected sets is defined by the memory configuration. For instance in a common dual-rank, single-channel configuration you would expect 16 banks (i.e., sets) in total.  You can pass any value you want to the script. If this value is unknown 16 is usually a safe bet.  

**Time threshold:**

- You can identify the time threshold by running the tool the first time with `-o` and plotting the results with the histogram.py script available in the repo. Once you know the threshold you can dinamycally pass it to the binary. 
