### FMA

FMA does the FP arithmetic work for dst = src0*src1 + src2

- only round once

It returns the higher precision result of fused **multiply-addition operation**. It achieves it by keeping all mantissa of src0*src1 result instead of rounding it. After addition with src2, the final result is normalized

最后计算完，赋值之前进行 normalized

```llvm
{@{!}p} FMA{.rp}{.sat}    dst,    src2,    src1,    src0
```

### MAD

MAD does the FP arithmetic work for dst = src0*src1 + src2

MAD will normalize and round src0*src1 to a standard FP32 value, then do add with src2. The final result is normalized and rounded

```llvm
{@{!}p} MAD{.rp}{.sat}    dst,    src2,    src1,    src0

//equal

FMUL temp, src1, src0
FADD dst,  src2, temp
```


### FCLAMP

example

```llvm
FCLAMP.rp3 r0, PDC_1F, r1
```