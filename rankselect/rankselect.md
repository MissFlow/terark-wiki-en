# Rank Select

[Home](../README.md)

## Rank Select Performance Comparison

Our core products are using Succinct Data Structures, and the fundamental of Succinct Data Structure is `Rank-Select`. So the performance of `Rank-Select` is  of greatest importance.

The ensure the performance of the Succinct Data Structure, we implemented our own Rank-Select. Comparing to existing open source implementation([sdsl-lite](https://github.com/simongog/sdsl-lite)), we have tremendous performance advantage.

Here's the benchmark report:

### Hardware

|CPU | |
|------|------|
|CPU Num. | 2
|CPU Model | Xeon E5-2630 v3
|CPU Freq. |2.4 GHz
|CPU Actual Freq. |2.6 GHz
|CPU Cores/Threads (each CPU)|8 cores, 16 threads
|CPU Cores/Threads（in total）|16 cores 32 threads
|CPU Buffer Size |20M
|CPU bogomips<br>（represent the real speeed of CPU）|4793

|Memory | |
|------|------|
|Memory Size|64GB
|Memory Freq.|DDR4 1866 MHz

### Test Result
The y-axis represents the time cost of each operation and the x-axis represents
different implementation of `rank-select`.

`sdsl_v_mcl` is the fastest `rank-select` implementation in [sdsl-lite](https://github.com/simongog/sdsl-lite). THe rest of them are our own different implementations. The ones include `_fast` suffix means it have extra optimize inline functions.

![rank_select](https://cdn.rawgit.com/terark/terark-wiki-zh_cn/master/rankselect/rank_select.svg)
