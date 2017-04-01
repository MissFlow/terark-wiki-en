# Terark Command Line Tools

[Home](../README.md)

## Terark Command Line Tools

[Download Terark Command Line Tools](https://www.terark.com/download/tools/latest), from this download page, the package names are:

- terark-fsa_all-Linux-x86_64-g++-**VERSION**-bmi2-0.tgz : Works on older CPU which doesn't support `BMI2`
- terark-fsa_all-Linux-x86_64-g++-**VERSION**-bmi2-1.tgz : Works on newer CPU (e.g. `intel-haswell` or better) which supports `BMI2`

Please check your gcc version and CPU and download the suitable package.

After you un-packed the package, the directory woule looks like:

    root = pkg/terark-fsa_all-Linux-x86_64-g++-**VERSION**-bmi2-**X**

|Dir|Description|
--------|---------|
root/bin| **Command Line Tools** |
root/lib| Dynamic Libraries |
root/include| |
root/samples| |
root/samples/bin| Benchmark Tools|
root/samples/src| Sample Code |

### Command Line Tools Introduction

For the convinient of compiling, we use `.exe` as file extension even at `Linux/Mac OS`

|Tool Name | Description  |
-----|-----|
[nlt_build.exe](bin/nlt_build.exe.md)| Build Terark Nested Succinct Trie (for keys), the compressed data file could be load via Terark's API and execute queries on it.<br/> [terark-zip-rocksdb](https://github.com/Terark/terark-zip-rocksdb)'s index (key) is using this algorithm.<br/> This algorithm is a practical using of Terark's **CO-Index** (**C**ompressed **O**rdered **Index**) |
[zbs_build.exe](bin/zbs_build.exe.md)| Terark global compressin (for values), the compressed data file could be loaded via Terark's API and could extract record by record ID, randomly.<br/>[terark-zip-rocksdb](https://github.com/Terark/terark-zip-rocksdb)'s value compression is using this algorithm.<br/>This algorithm is a practical using of Terark's **PA-Zip** (**P**oint **A**ccessible **Zip**)|
[zbs_unzip.exe](bin/zbs_unzip.exe.md)| Decompress (or point search) from the data file which compressed by [zbs_build.exe](bin/zbs_build.exe.md). And can used for benchmarking|
[fplcat.exe](bin/fplcat.exe.md)| Pack multiple files together in order to let  [zbs_build.exe](bin/zbs_build.exe.md) compress them. The `-B` param should be used when using [zbs_build.exe](bin/zbs_build.exe.md) compressing them|
|[adfa_build.exe](bin/adfa_build.exe.md)| Build a ADFA(Acyclic DFA) from input keys. Each lien in the input text file is single key. <br/> The generated DFA could be used for key matching (full match or prefix match)|
[ac_build.exe](bin/ac_build.exe.md)| Build a AC automata from text-based patterns. The generated AC automata file could be loaded via Terark's API and use its flexiable matching functions.<br/> Each lien of the input pattern text file is a pattern. The speed of the eaxt search could be hundreds of MB (sometimes over 1GB/s) per thread.|
[regex_build.exe](bin/regex_build.exe.md)|Build a multiple regex matching automata from a set of regex expressions. The generated automata could be loaded via Terark's API and execute a set of searching functions on it. <br/> Since it is multi-regex matching, its more powerful than AC automata but the performance is not as good.|

More detail on each of the tools can be found by their `command line help`.
