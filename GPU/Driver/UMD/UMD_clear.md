
# clear


## clear color


### core layer

- DX9   ARGB

0XFF000000  : A FF R 00 G 00 B 00

0x32        : A 00 R 00 G 00 B 00

DX9 下发到chip层，需要做 ARGB -> AGBR的转换


- DX10  ABGR



### chip layer

  A B G R
0x00FF0000 

memory

00 01 02 03
00 00 FF 00



## clear depth&stencil

