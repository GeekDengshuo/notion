## 1.Build

### build:

sln:

sw_driver_ref\ref\hw\chip\cmodel\D3DReference9C\D3DReference9C.sln

build with x64

### target:

d3dref9.dll

sw_driver_ref\ref\hw\chip\cmodel\D3DReference9C\src\d3dref9\link\daytona\objchk_wlh_amd64\amd64

### run:

reference dll放在app同目录，可以使用vs跟代码

### debug:

debug flag in hpp head

\ref\hw\chip\cmodel\D3DReference9C\src\d3dref9\inc\refdev.hpp

```cpp
// \\ref\\hw\\chip\\cmodel\\D3DReference9C\\src\\d3dref9\\inc\\refdev.hpp
const bool g_dump_for_cmodel_debug = false;
```

## 2.Attach

### CreateDeviceEX

脚本行为决定

```cpp
HRESULT CreateDeviceEx(
  [in]          UINT                  Adapter,
  [in]          D3DDEVTYPE            DeviceType,
  [in]          HWND                  hFocusWindow,
  [in]          DWORD                 BehaviorFlags,
  [in, out]     D3DPRESENT_PARAMETERS *pPresentationParameters,
  [in, out]     D3DDISPLAYMODEEX      *pFullscreenDisplayMode,
  [out, retval] IDirect3DDevice9Ex    **ppReturnedDeviceInterface
);
```

* BehaviorFlags

> 这个很重要，决定了Ref对Vertex的处理方式(SWVP,HWVP)

脚本行为

```bash
pD3D9_0->CreateDeviceEx(0, D3DDEVTYPE_REF, win_2, 0x40000022, presParam_2, NULL, pDev9Ex_2);

# 0x400000022  D3DCREATE_SOFTWARE_VERTEXPROCESSING | D3DCREATE_FPU_PRESERV

#0x4000000050  D3DCREATE_HARDWARE_VERTEXPROCESSING | D3DCREATE_PUREDEVICE
```

```cpp
/****************************************************************************
 *
 * Flags for IDirect3D9::CreateDevice's BehaviorFlags
 *
 ****************************************************************************/

#define D3DCREATE_FPU_PRESERVE                  0x00000002L
#define D3DCREATE_MULTITHREADED                 0x00000004L

#define D3DCREATE_PUREDEVICE                    0x00000010L
#define D3DCREATE_SOFTWARE_VERTEXPROCESSING     0x00000020L
#define D3DCREATE_HARDWARE_VERTEXPROCESSING     0x00000040L
#define D3DCREATE_MIXED_VERTEXPROCESSING        0x00000080L

#define D3DCREATE_DISABLE_DRIVER_MANAGEMENT     0x00000100L
#define D3DCREATE_ADAPTERGROUP_DEVICE           0x00000200L
#define D3DCREATE_DISABLE_DRIVER_MANAGEMENT_EX  0x00000400L

// This flag causes the D3D runtime not to alter the focus 
// window in any way. Use with caution- the burden of supporting
// focus management events (alt-tab, etc.) falls on the 
// application, and appropriate responses (switching display
// mode, etc.) should be coded.
#define D3DCREATE_NOWINDOWCHANGES               0x00000800L

// Disable multithreading for software vertex processing
#define D3DCREATE_DISABLE_PSGP_THREADING        0x00002000L
// This flag enables present statistics on device.
#define D3DCREATE_ENABLE_PRESENTSTATS           0x00004000L
// This flag disables printscreen support in the runtime for this device
#define D3DCREATE_DISABLE_PRINTSCREEN           0x00008000L

#define D3DCREATE_SCREENSAVER                   0x10000000L
```

* D3DCREATE_FPU_PRESERVE

Set the precision for Direct3D floating-point calculations to the precision used by the calling thread. If you do not specify this flag, Direct3D defaults to single-precision round-to-nearest mode for two reasons:

* Double-precision mode will reduce Direct3D performance.
* Portions of Direct3D assume floating-point unit exceptions are masked; unmasking these exceptions may result in undefined behavior
* D3DCREATE_SOFTWARE_VERTEXPROCESSING

---

### Entry

d3dref.def

```cpp
EXPORTS
	D3D9GetSWInfo
	D3D9GetSWInfoEx
```

RefRastDrawPrimitives2

---

### FuncTbl

RefRastDrawPrimitives2

* **RefDev::DrawPrimitives2**
  * pStateSetFuncTbl->pfnDp2SetViewport(this, pCmd)
    * --> WrapDp2SetViewport --> pRefDev->Dp2SetViewport(pCmd);
    * -->WrapDp2SetRenderStates ---> RefDev::Dp2SetRenderStates

### Core Object

RefDev::RefDev

```cpp
RefDev::RefDev( LPDDRAWI_DIRECTDRAW_LCL pDDLcl, DWORD dwInterfaceType,
RDDDITYPE dwDDIType, D3DCAPS9* pCaps )
: m_RefVP(), m_RefVM(), m_Clipper(),
m_FVFShader(), m_FVFDecl(), m_pNPatch(NULL), m_dwOcclusionCounter( 0 )
{};
```
