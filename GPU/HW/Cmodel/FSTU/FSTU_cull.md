默认是指backface culling

### 1.为什么需要背面剔除 ？

背面是看不见的，无需浪费资源去处理顶点及各种信息
saves rendering time because a back-face is not visible

### 2.front-face/back-face

face and vertex normal vectors, 面及顶点法向量

[d3d9-spec:face and vertex normal vectors](https://learn.microsoft.com/en-us/windows/win32/direct3d9/face-and-vertex-normal-vectors)

法向量的方向由以下因素决定：

- 顶点顺序的定义(CW,CCW)
- 坐标系(Coordinate System)

![nrmlvect.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/cdec506f-a3eb-4003-b2fb-abb86be978b3/nrmlvect.png)

The face normal points away from the front side of the face. In Direct3D, only the front of a face is visible. A front face is one in which vertices are defined in clockwise order.

The side the normal vector emanates from is the Front Side and other side is the back side

front face:  就是normal vector 放射出的方向

back face：不是front face ，就是back face

### 3.如何进行culling

By default, D3D treats triangles with a clockwise winding order(with respect to the viewer) as front -facing
Triangles with a counterclockwise winding order as back-facing.

默认情况下，D3D认为  CW winding 就是 front face，CCW就是back face

***d3dtypes.h***

```cpp
typedef enum _D3DCULL {
    D3DCULL_NONE               = 1,
    D3DCULL_CW                 = 2,
    D3DCULL_CCW                = 3,
#if(DIRECT3D_VERSION >= 0x0500)
    D3DCULL_FORCE_DWORD        = 0x7fffffff, /* force 32-bit size enum */
#endif /* DIRECT3D_VERSION >= 0x0500 */
} D3DCULL;
```

***d3d10umddi.h***

```cpp
// Keep CULL_MODE values in sync with earlier DX versions (HW consumes values directly).
typedef enum D3D10_DDI_CULL_MODE
{
    D3D10_DDI_CULL_NONE = 1,
    D3D10_DDI_CULL_FRONT = 2,
    D3D10_DDI_CULL_BACK = 3
} D3D10_DDI_CULL_MODE;
```

A value that specifies how back-facing triangles are culled, if at all. This member must be
set to one of the following values from the D3D10_DDI_CULL_MODE enumeration.

| Value | Meaning |
| --- | --- |
| D3D10_DDI_CULL_NONE(1) | Do  not cull any triangles. |
| D3D10_DDI_CULL_FRONT(2) | Cull front faces. |
| D3D10_DDI_CULL_BACK(3) | Cull back faces. |

[in] FrontCounterClockwise

A Boolean value that specifies whether vertices that
are provided in a counter-clockwise order (with respect to the rasterizer) are
front facing. TRUE indicates they are; FALSE indicates that
counter-clockwise vertices indicate back facing.

### 4.如何render backface

如果需要绘制backface，可以设置renderstate实现

You can change the culling mode to render back faces 。

SetRenderState(D3DRS_CULLMODE, D3DCULL_CW);

```cpp
SetRenderState(D3DRS_CULLMODE, D3DCULL_CCW);

//This example will remove any primitive whose back face is facing forward (given a counter-clockwise winding order)
```

### 5.如何实现ref&cmodel_fstu

[PerTriangleSetup](https://www.notion.so/PerTriangleSetup-736521bbb916453fb34becc4145ad927)

[Cull](https://www.notion.so/Cull-bf2e8f307df24e3a8db7e59fe9e13350)

> [14:29] Henry Ni
> 

> Face = DET_SIGN ^ WINDING ^ (NEGW0^ NEGW1^ NEGW2)
> 

> NEGW0^ NEGW1^ NEGW2，这就是看三个顶点的w的正负值
> 

> DET_SIGN，这个是看三角形的面积,
> 

DET_SIGN  , determinant 向量行列式的值