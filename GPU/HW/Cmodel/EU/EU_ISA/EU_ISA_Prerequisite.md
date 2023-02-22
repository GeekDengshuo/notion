### The grammer of Syntax

> One Instruction may 0/1/2/3 source operand, 0/1/2 destination operand. Typical has following grammar.
> 

```llvm
{@{!}p} MajorOpName{.rp}{.dly}{.sat}{.ov}{.s}{.cc}  dst, {src2,} src1, src0
```

- **{}** means optional field which can be omitted.
- **@p** is an instruction prefix source predicate register which is used as lane mask register for SIMD machines.
- **! p** is to get the opposite of p.
- **MajorOpName** is the operation name like FADD/FMUL.
- **rp** is repeat number for this instruction. “rp0” mean no repeat. “rp1”, “rp2” , “rp3”  means source/destination are vector registers.
- **dly** is for delayed cycles before executing this ISA due to data dependencies. ISA need read data which may not be ready. So, this ISA may be delayed for certain cycles before data dependencies is removed.
    
    Any ISA has source register operand, field “dly” is appliable.  Otherwise, “dly” is not used.
    
- **sat** is short for stature. It indicates ISA to return statured result if “out of range” case occurs.
- **ov** is short for overflow.  It indicates ISA to follow IEEE rules to treat overflow.
- **cc**  is short for condition code. If using .cc in instructions, P10(overflow), P11(Carry) will be updated accordingly
- **[]** is used as addressing operator or indexing operator

### PDC

PDC_0,          240~249 are for PDC

---

PDC_0125F, float 0.125f

---

PDC_025F,   float 0.25f

---

PDC_050F,   float 0.5f

---

PDC_1F,       float 1.0f

---

PDC_2F,       float 2.0f

---

PDC_4F,       float:4.0f

---

PDC_8F,       float:8.0f

---

PDC_1I,        Integer 1

---

PDC_1IN,      Integer -1

### CRF,PRF,SRF,CB

CRF: common register file

PRF: predicate register file

```powershell
The predicate register is used as lane mask register for SIMD machines.
For each thread, we have 12 PRF registers, P0~P11.
```

PRF can't be repeated

SRF: scaler register file

CB: constant buffer

```powershell
Each PB has 2048 dword CB entries from CB0 to CB2047
```

### fwd

fwd 代表组合指令，获取上一个指令运行的结果  ？