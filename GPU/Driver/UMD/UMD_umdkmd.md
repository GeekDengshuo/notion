## D3DDDI_POOL

* SYSTEMMEM      系统内存
* VIDEOMEMORY  显卡内存
* LOCALVIDMEM   资源在 cpuvisible_local_segment
* NONLOCALVIDMEM    资源在pcie上

nonlocal display memory(AGP memory,PCIe memory)

AGP:Accelerated Graphics Port，图形加速接口

**D3DPOOL_DEFAULT :  D3DDDIPOOL_VIDEOMEMORY ?**

```cpp
D3DDDI_POOL ：Memory pool types

typedef enum _D3DDDI_POOL 
{ 
  D3DDDIPOOL_SYSTEMMEM, 
	D3DDDIPOOL_VIDEOMEMORY,
	D3DDDIPOOL_LOCALVIDMEM, 
	D3DDDIPOOL_NONLOCALVIDMEM,
	D3DDDIPOOL_STAGINGMEM 

} D3DDDI_POOL;

D3DPOOL_DEFAULT :  D3DDDIPOOL_VIDEOMEMORY
```

```cpp
typedef enum _gpu_pool_type
{
    GPU_POOL_UNKNOWN            = 0,
    GPU_POOL_SYSTEMMEM          = 1,
    GPU_POOL_LOCALVIDMEM        = 2,
    GPU_POOL_NONLOCALVIDMEM     = 4,
    GPU_POOL_VIDEOMEMORY        = 6, //(GPU_POOL_LOCALVIDMEM | GPU_POOL_NONLOCALVIDMEM)
    GPU_POOL_MASK               = 0x00000007,
} gpu_pool_type;
```

### **D3DPOOL_SYSTEMMEM**

资源放置在通常不能由 Direct3D 设备访问的内存中。 此内存分配使用系统 RAM，但不会减少可分页 RAM。 设备丢失时，无需重新创建这些资源。 此池中的资源可以锁定，并且可以用作 **[IDirect3DDevice9：：UpdateSurface](https://learn.microsoft.com/zh-cn/windows/desktop/api)** 或 **[IDirect3DDevice9：：UpdateTexture](https://learn.microsoft.com/zh-cn/windows/win32/api/d3d9helper/nf-d3d9helper-idirect3ddevice9-updatetexture)** 操作的源，以使用 D3DPOOL_DEFAULT 创建的内存资源

### D3DPOOL_DEFAULT

资源放置在最适合为给定资源请求的使用情况集的内存池中。 这通常是视频内存，包括本地视频内存和 AGP 内存
