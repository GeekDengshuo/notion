
## Bin 二进制文件中将空格替换为行

读取二进制文件

```bash
>>> fn = open('C:/derick/test/fb_com_in.bin','rb')
>>> fn_read = fn.read()
>>> fn_read_decode = fn_read.decode()
>>> fn_read_decode = fn_read_decode.replace('  ','\n')
>>> out = open('C:/derick/test/fb_out2.bin','a+')
>>> out = out.write(fn_read_decode)
```

- 需要进行decode()处理

fn_read的内容直接写入到bin文件中

会报error

```bash
AttributeError: 'bytes' object has no attribute 'tostr'
AttributeError: 'bytes' object has no attribute 'write'

TypeError: write() argument must be str, not bytes
```

```bash
>>> fn = open('C:/derick/test/fb_com_in.bin','rb')
>>> fn_read = fn.read()
>>> type(fn_read)
<class 'bytes'>
# bytes is a built-in binary sequence type in Python. 
# It is used for binary data manipulation.
```

```bash
bytes is a built-in binary sequence type in Python. It is used for binary data manipulation.
```

也可以进行二进制文件的replace

```bash
a = b"abc"
b = a.replace(b"a", b"f")
```

write 函数的参数必须是str

```bash
>>> fn = open('C:/derick/test/fb_com_in.bin','rb')
>>> fn_read = fn.read()
>>> type(fn_read)
<class 'bytes'>

# 进行二进制的replace
>>> fn_read_rep  = fn_read.replace(b'  ',b'\n')
>>> out = open('C:/derick/test/fb_out3.bin','a+')
>>> out = out.write(fn_read_rep)

TypeError: write() argument must be str, not bytes

>>> out = out.write(fn_read_rep.decode())
```