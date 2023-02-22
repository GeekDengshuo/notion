# Adapter


## Core

* OpenAdapter

driver入口函数(core.def)

* 1.构造一个gpu_adapter_c 并配置driver settings
* 2.创建一个pil层的adapter
* 3.配置core层adapter的adapterfunc

为什么会调用 close_adapter  ?

## PIL

* open_adapters

[entry.cc](http://entry.cc)  pil 入口函数的实现(需要根据操作系统os创建)

* 1.会完成操作系统对应pil adapter的创建
* 2.loader 相关库(rtsim.dll  or gdi32.dll)
* 3.调用 D3DKMTEnumAdapters 枚举adapter
* 4.调用 D3DKMTQueryAdapterInfo 并完成当前环境adapter的init

## adapter func- create_device

* [1.new](http://1.new) gpu_device_c
* 2.generate_device_functable
* 3.创建shader const buf 的resource，并set shader const到pipeline state 的shader state

## create_device - gpu_device_c

* 1.从core gpu_adapter获取driver settings
* 2.调用pil adapter 创建pil device
* 3.load lib SC.dll 加载compiler的函数地址
* 4.生成chip func table  ,gf_xxxx 在chips层
* 5.gf_create_chip_device，生成 sync及chip cmd相关
* 6.创建pipeline state

## device_c

1.os_create_device(), 调用D3DKMTCreateDevice

2.创建page_queue()

[3.open](http://3.open) sync object
