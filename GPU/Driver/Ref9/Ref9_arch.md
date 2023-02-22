* Ref9 Contents
  ```bash
  ref
  ├── hw
  └── sw
  ```

## 1.HW

* hw
  ```bash
  hw
  └── chip
      └── cmodel
          ├── D3DReference9C
          │   ├── Backup
          │   ├── D3DReference9C.sln
          │   ├── D3DReference9C.vcproj
          │   ├── D3DReference9C.vcxproj
          │   ├── D3DReference9C.vcxproj.filters
          │   ├── D3DReference9C.vcxproj.user
          │   ├── Debug
          │   ├── RefModelBuild.bat
          │   ├── RefModelBuild_x64.bat
          │   ├── UpgradeLog.htm
          │   ├── clean.bat
          │   ├── clean_x64.bat
          │   ├── readme.txt
          │   └── src
          ├── Utils
          │   └── include
          └── include
              ├── EnvShare.h
              ├── ProfilingDef.h
              └── typeport.h

  9 directories, 14 files
  ```
* chip-model
  ```bash
  cmodel
  ├── D3DReference9C
  │   ├── Backup
  │   ├── D3DReference9C.sln
  │   ├── D3DReference9C.vcproj
  │   ├── D3DReference9C.vcxproj
  │   ├── D3DReference9C.vcxproj.filters
  │   ├── D3DReference9C.vcxproj.user
  │   ├── Debug
  │   │   ├── D3DReference9C.Build.CppClean.log
  │   │   ├── D3DReference9C.log
  │   │   └── D3DReference9C.vcxproj.AssemblyReference.cache
  │   ├── RefModelBuild.bat
  │   ├── RefModelBuild_x64.bat
  │   ├── UpgradeLog.htm
  │   ├── clean.bat
  │   ├── clean_x64.bat
  │   ├── readme.txt
  │   └── src
  │       ├── d3d8
  │       │   └── inc
  │       └── d3dref9
  │           ├── buildchk_wlh_x86.log
  │           ├── buildchk_wlh_x86.wrn
  │           ├── common
  │           ├── dirs
  │           ├── drv
  │           ├── hop
  │           ├── inc
  │           ├── link
  │           ├── ntref.mk
  │           ├── rast
  │           ├── ref.mk
  │           ├── tnl
  │           └── win9xref.mk
  ├── Utils
  │   └── include
  │       └── misc
  │           └── EliteAssert.h
  └── include
      ├── EnvShare.h
      ├── ProfilingDef.h
      └── typeport.h

  18 directories, 24 files
  ```

### 1.1 ***Src***

* 主要实现部分
  ```bash
  src
  ├── d3d8
  │   └── inc
  │       └── d3d8ddi.h
  └── d3dref9
      ├── buildchk_wlh_x86.log
      ├── buildchk_wlh_x86.wrn
      ├── common
      │   ├── ctexfilt.cpp
      │   ├── daytona
      │   │   ├── makefile
      │   │   ├── objchk_wlh_x86
      │   │   └── sources
      │   ├── dirs
      │   ├── dxtn.cpp
      │   ├── dxtncommon.cpp
      │   ├── maplegcy.cpp
      │   ├── msaachange.cpp
      │   ├── pch.cpp
      │   ├── rddmon.cpp
      │   ├── rdsurf.cpp
      │   ├── rdutil.cpp
      │   ├── refdev.cpp
      │   ├── refdevi.cpp
      │   ├── rtarget.cpp
      │   ├── sources.inc
      │   ├── texsampler.cpp
      │   ├── translator.cpp
      │   └── win9x
      │       ├── makefile
      │       └── sources
      ├── dirs
      ├── drv
      │   ├── daytona
      │   │   ├── makefile
      │   │   ├── objchk_wlh_x86
      │   │   └── sources
      │   ├── dirs
      │   ├── dprim2.cpp
      │   ├── drawprim.cpp
      │   ├── init.c
      │   ├── pch.cpp
      │   ├── primfns.cpp
      │   ├── query.cpp
      │   ├── query.hpp
      │   ├── refif.cpp
      │   ├── refif.hpp
      │   ├── refprov.hpp
      │   ├── refumode.cpp
      │   ├── rralloc.cpp
      │   ├── sources.inc
      │   ├── surfman.cpp
      │   └── win9x
      │       ├── makefile
      │       └── sources
      ├── hop
      │   ├── bezier.cpp
      │   ├── bezier.hpp
      │   ├── bspline.cpp
      │   ├── bspline.hpp
      │   ├── catrom.cpp
      │   ├── catrom.hpp
      │   ├── daytona
      │   │   ├── makefile
      │   │   ├── objchk_wlh_x86
      │   │   └── sources
      │   ├── dirs
      │   ├── drawgrid.cpp
      │   ├── npatch.cpp
      │   ├── npatch.hpp
      │   ├── pch.cpp
      │   ├── sources.inc
      │   └── win9x
      │       ├── makefile
      │       └── sources
      ├── inc
      │   ├── d3d8sddi.h
      │   ├── d3d9ddi.h
      │   ├── dxfloat.h
      │   ├── dxva2.h
      │   ├── dxva2api.h
      │   ├── dxva2swdev.h
      │   ├── dxvadriver.h
      │   ├── halprov.h
      │   ├── pshader.h
      │   ├── pstrans.hpp
      │   ├── rdcomm.hpp
      │   ├── rddmon.hpp
      │   ├── refcommon.h
      │   ├── refdev.hpp
      │   ├── refrast.hpp
      │   ├── reftnl.hpp
      │   ├── templarr.hpp
      │   ├── texsampler.h
      │   ├── translator.h
      │   ├── umfilter.h
      │   ├── verinfo.h
      │   ├── vshader.h
      │   └── vstream.h
      ├── link
      │   ├── d3dref.def
      │   ├── d3dref.rc
      │   ├── daytona
      │   │   ├── makefile
      │   │   ├── objchk_wlh_x86
      │   │   └── sources
      │   ├── dirs
      │   ├── sources.inc
      │   └── win9x
      │       ├── makefile
      │       └── sources
      ├── ntref.mk
      ├── rast
      │   ├── ctexflt.cpp
      │   ├── daytona
      │   │   ├── makefile
      │   │   ├── objchk_wlh_x86
      │   │   └── sources
      │   ├── dirs
      │   ├── pch.cpp
      │   ├── pixproc.cpp
      │   ├── psexec.cpp
      │   ├── pshader.cpp
      │   ├── pstrans.cpp
      │   ├── psutil.cpp
      │   ├── rastattr.cpp
      │   ├── rastedge.cpp
      │   ├── rastprim.cpp
      │   ├── refrast.cpp
      │   ├── refrasti.hpp
      │   ├── scancnv.cpp
      │   ├── setup.cpp
      │   ├── sources.inc
      │   ├── texfilt.cpp
      │   ├── texsmplr.cpp
      │   ├── texstage.cpp
      │   └── win9x
      │       ├── makefile
      │       └── sources
      ├── ref.mk
      ├── tnl
      │   ├── clip.h
      │   ├── clipping.cpp
      │   ├── clipping.hpp
      │   ├── daytona
      │   │   ├── makefile
      │   │   ├── objchk_wlh_x86
      │   │   └── sources
      │   ├── dirs
      │   ├── drawprim.cpp
      │   ├── lighting.cpp
      │   ├── pch.cpp
      │   ├── procprim.cpp
      │   ├── reftnl.cpp
      │   ├── sources.inc
      │   ├── vshader.cpp
      │   ├── vstream.cpp
      │   ├── win9x
      │   │   ├── makefile
      │   │   └── sources
      │   └── xform.cpp
      └── win9xref.mk

  28 directories, 133 files
  ```

入口函数

* d3dref.def

```bash
EXPORTS
    D3D9GetSWInfo
    D3D9GetSWInfoEx
```

## 2.SW

* sw contents
  ```bash
  sw
  └── tools
      └── WDK_6001
          ├── bin
          │   ├── BlockDir
          │   ├── SelfSign
          │   ├── amd64
          │   ├── amd64mk.inc
          │   ├── catalog
          │   ├── coffbase.txt
          │   ├── generic.mac
          │   ├── i386mk.inc
          │   ├── ia64
          │   ├── ia64mk.inc
          │   ├── makefile.def
          │   ├── makefile.new
          │   ├── makefile.plt
          │   ├── projects.inc
          │   ├── setenv.bat
          │   ├── setwdf.bat
          │   ├── verify.src
          │   ├── w2k
          │   ├── wppconfig
          │   └── x86
          ├── build.dat
          ├── inc
          │   ├── api
          │   ├── atl21
          │   ├── atl30
          │   ├── crt
          │   ├── ddk
          │   ├── mfc42
          │   └── wdf
          ├── lib
          │   ├── atl
          │   ├── crt
          │   ├── mfc
          │   ├── w2k
          │   ├── wdf
          │   ├── wlh
          │   ├── wnet
          │   └── wxp
          └── tools
              ├── WDTF
              ├── acpi
              ├── avstream
              ├── chkinf
              ├── coinstallers
              ├── dc2
              ├── devcon
              ├── nxdemo
              ├── other
              ├── pfd
              ├── pnpcpu
              ├── pnpdtest
              ├── print
              ├── procalc
              ├── sdv
              ├── tracing
              ├── wdf
              ├── wia
              ├── wpd
              └── wsdapi

  48 directories, 14 files
  ```
