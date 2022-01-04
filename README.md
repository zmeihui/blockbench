# BlockBench

BlockBench is the first benchmarking framework for private blockchain systems.
It serves as a fair means of comparison for different platforms and enables deeper understanding
of different system design choices.

BlockBench comes with both [macro benchmark workloads](src/macro) for evaluating the overall performance and
[micro benchmark workloads](src/micro) for evaluating performance of individual layers. 

## Workloads 

### Macro-benchmark

* YCSB (KVStore).
* SmallBank (OLTP).

### Micro-benchmark

* DoNothing (consensus layer).
* IOHeavy (data model layer, read/write oriented).
* Analytics (data model layer, analytical query oriented).
* CPUHeavy (execution layer).

## Source file structure

+ Smart contract sources are in [benchmark/contracts](benchmark/contracts) directory.
+ Instructions and scripts to run benchmarks for Ethereum, Hyperledger Fabric v0.6, v1.4 and v2.2, Parity and Quorum are in [ethereum](benchmark/ethereum),
[hyperledger fabric v0.6](benchmark/hyperledger) , [hyperledger fabric v1.4](benchmark/fabric-v1.4), [hyperledger fabric v2.2](benchmark/fabric-v2.2), [parity](benchmark/parity) , [quorum_raft](benchmark/quorum_raft) and [quorum_vote](benchmark/quorum_vote) directories respectively.
+ Drivers for benchmark workloads are in [src](src) directory.

## Dependency

### C++ libraries
* [restclient-cpp](https://github.com/mrtazz/restclient-cpp)

  Note: we patched this library to include the "Expect: " header in POST requests, which considerably improves the speed for
  processing RPC request at Parity. 

    + The patch file is include in [benchmark/parity](benchmark/parity) folder.
    + To patch: go to top-level directory of restclient-cpp, then:

        `patch -p4 < $BLOCK_BENCH_HOME/benchmark/parity/patch_restclient`

    + The installation can then proceed as normal. 

* [libcurl](https://curl.haxx.se/libcurl/)

### Node.js libraries
Go to [micro](src/micro) directory and use `npm install` to install the dependency libraries
* [Web3.js](https://github.com/ethereum/web3.js/)
* [zipfian](https://www.npmjs.com/package/zipfian)
* [bignumber.js](https://www.npmjs.com/package/bignumber.js)
* [fabric-v1.4 SDK](https://github.com/hyperledger/fabric-sdk-node/tree/release-1.4)
* [fabric-v2.2 SDK](https://github.com/hyperledger/fabric-sdk-node/tree/release-2.2)

## Blockchain Systems 
* [geth(ethereum)](https://github.com/ethereum/go-ethereum/wiki/Installation-Instructions-for-Ubuntu)
* [geth(parity)](https://github.com/paritytech/parity/wiki/Setup)
* [geth(quorum)](https://github.com/jpmorganchase/quorum/wiki/Getting-Set-Up)
* [hyperledger fabric v0.6](https://github.com/hyperledger/fabric/tree/v0.6)
* [hyperledger fabric  v1.4](https://github.com/hyperledger/fabric/tree/release-1.4)
* [hyperledger fabric  v2.2](https://github.com/hyperledger/fabric/tree/release-2.2)

## References
* [1] A. Dinh, J. Wang, G. Chen, R. Liu, B. C. Ooi, K.-L. Tan: [BLOCKBENCH: A Framework for Analysing Private Blockchains](https://www.comp.nus.edu.sg/~ooibc/blockbench.pdf). ACM SIGMOD 2017.
* [2] [The Morning Paper Review](https://blog.acolyer.org/2017/07/05/blockbench-a-framework-for-analyzing-private-blockchains/) 2017
* [3] A. Dinh, R. Liu, M. Zhang, G. Chen, B.C. Ooi, J. Wang: [Untangling Blockchain: A Data Processing View of Blockchain Systems](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=8246573). IEEE Transactions on Knowledge and Data Engineering, July 2018.
* [4] [FabricSharp](https://www.comp.nus.edu.sg/~dbsystem/fabricsharp/#/) -- an faster Fabric blockchain system.
* [5] M. Zhang, Z. Xie, C. Yue, Z. Zhong: [Spitz: A Verifiable Database System](http://www.vldb.org/pvldb/vol13/p3449-zhang.pdf). Proc. VLDB Endow. 13(12): 3449-3460 (2020).
