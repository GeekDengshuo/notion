

# Instruction modifiers

Instruction modifiers affect the result of the instruction before it is written to the register

## Source Operand Modifiers

* absolute value

```cpp
_abs

example:
move_abs
```

* negate

```cpp
-

example:
-r0
add r5.xyz, c109, -r0
```

## Instruction Result Modifiers

* Saturate

> min(1.0f, max(0.0f, value))

```cpp
_sat

example:
mov_sat_pp r0, v0
# Clamps the result of a single or double precision floating point arithmetic operation 
# to [0.0f...1.0f] range.
```

* Centroid

```cpp
_centroid

example:
dcl_texcoord0_centroid v0
```

* ****Partial Precision****

```cpp
_pp

examples:

mov_pp
dcl_texcoord0_pp t1
cmp_pp r0, r1, r2, r3
```

reference:

[](https://learn.microsoft.com/en-us/windows/win32/direct3dhlsl/dx9-graphics-reference-asm-ps-instructions-modifiers-ps-2-0)[https://learn.microsoft.com/en-us/windows/win32/direct3dhlsl/dx9-graphics-reference-asm-ps-instructions-modifiers-ps-2-0](https://learn.microsoft.com/en-us/windows/win32/direct3dhlsl/dx9-graphics-reference-asm-ps-instructions-modifiers-ps-2-0)
