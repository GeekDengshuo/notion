## 1.Set Shader Const

These constants are loaded every time [SetVertexShader](https://learn.microsoft.com/en-us/windows/desktop/api/d3d9helper/nf-d3d9helper-idirect3ddevice9-setvertexshader)   [SetPixelShader](https://learn.microsoft.com/en-us/windows/win32/api/d3d9/nf-d3d9-idirect3ddevice9-setpixelshader) is called.



## 2.Shader Code

[d3d-shader-code](https://learn.microsoft.com/en-us/windows-hardware/drivers/display/direct3d-shader-codes)

command stream:

D3DHAL_DP2CREATEPIXELSHADER structrue + pixel shader code

```
## shader code format

the format of tokens within each shader code determines its uniquenss

shader code:

general token layout

version token + instruction tokens(comment tokens) + label，destination，source parameter tokens + end token

## shader code tokens

each shader token is actually a DWORD with a specific format

都在shader_9.h中实现

- comment token
- destination parameter token
- end token
- instruction token
- label token
- source parameter token
- version token

### instruction token 

operation code : D3DSIO_*   

D3DSHADER_INSTRUCTION_OPCODE_TYPE

对应shader_9.h 中的  INSTR_TOKEN

https://learn.microsoft.com/en-us/windows-hardware/drivers/ddi/d3d9types/ne-d3d9types-_d3dshader_instruction_opcode_type

#### shader register type

https://learn.microsoft.com/en-us/windows-hardware/drivers/ddi/d3d9types/ne-d3d9types-_d3dshader_param_register_type


D3DSHADER_PARAM_REGISTER_TYPE

对应shader_9.h 中 DX9_REGS_TYPE


### version token
 a version token desc the version number of the shader code

informs the driver whether the shader code is for pixel or vertex shader (gemtory shader)

For a pixel shader, the value is 0xFFFF. For a vertex shader, the value is 0xFFFE.

```
