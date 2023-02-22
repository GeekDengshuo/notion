### EMITF

### EMITC

o means ***osharp***. imm4_rt can be 0~7, since we support 8 RTs at most.

```llvm
{@{!}p} EMITC{.rte}        o[imm4_rt], src0{.chsel}{.chnum}
```


## Move

- syntax

```cpp
{@{!}p} MOVE{.fp}{qex} dst ,src0
```