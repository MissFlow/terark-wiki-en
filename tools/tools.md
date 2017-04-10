# Terark Command Line Tools

[Home](../README.md)

## Terark Command Line Tools

[Download Terark Command Line Tools](https://www.terark.com/download/tools/latest), from this download page, the package names are:

- terark-fsa_all-Linux-x86_64-g++-**VERSION**-bmi2-0.tgz : Works on older CPU which doesn't support `BMI2`
- terark-fsa_all-Linux-x86_64-g++-**VERSION**-bmi2-1.tgz : Works on newer CPU (e.g. `intel-haswell` or better) which supports `BMI2`

Please check your gcc version and CPU for downloading the corresponding package.

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
[nlt_build.exe](bin/nlt_build.exe.md)| Build Terark Nested Succinct Trie (for keys), the output file can be loaded via Terark's API and execute queries on it.<br/> [terark-zip-rocksdb](https://github.com/Terark/terark-zip-rocksdb)'s index (key) is using this algorithm.<br/> This algorithm is a practical realization of Terark's **CO-Index** (**C**ompressed **O**rdered **Index**) concept|
[zbs_build.exe](bin/zbs_build.exe.md)| Terark global compressin (for values), the compressed data file could be loaded via Terark's API and could extract record by record ID, randomly.<br/>[terark-zip-rocksdb](https://github.com/Terark/terark-zip-rocksdb)'s value compression is using this algorithm.<br/>This algorithm is a practical realization of Terark's **PA-Zip** (**P**oint **A**ccessible **Zip**) concept|
[zbs_unzip.exe](bin/zbs_unzip.exe.md)| Decompress (or point access) from the file which compressed by [zbs_build.exe](bin/zbs_build.exe.md). And can be used for benchmarking|
[fplcat.exe](bin/fplcat.exe.md)| Pack multiple files together in order to be used for [zbs_build.exe](bin/zbs_build.exe.md) to compress them. The `-B` param should be present when using [zbs_build.exe](bin/zbs_build.exe.md) to compress the **fplcat's** output file|
|[adfa_build.exe](bin/adfa_build.exe.md)| Build a ADFA(Acyclic DFA) from input keys. Each line in the input text file is a single key. <br/> The generated DFA can be used for key matching (full match or prefix match)|
[ac_build.exe](bin/ac_build.exe.md)| Build an AC automata from patterns, Each line of the input pattern text file is a pattern. The generated AC automata file could be loaded via Terark's API and used for pattern matching.<br/> The speed of the exact matching can be up to hundreds of MB (sometimes over 1GB/s) per thread.|
[regex_build.exe](bin/regex_build.exe.md)|Build a multiple regex matching automata from a set of regex. The generated automata can be loaded via Terark's API and used for multi regex matching(which regex**s** are matched at which position). <br/> Since it is multi-regex matching, it is more powerful(feature rich) than AC automata but is slower than AC automata.|

More detail on each of the tools can be found by their `command line help`.
