## 5.2 Resource Views

> There are also distinctions in how a Resource is bound to the graphics pipeline. The binding location can also be thought of as accepting either Buffers directly or accepting Views of Resources

> In order to indirectly bind a Resource to certain stages of the graphics pipeline, Resource Views must be used

resource绑定到pipeline上，必须创建相应的view，buffer除外

```cpp
pDev9Ex_1->CreateTexture(128, 128, 1, D3DUSAGE_RENDERTARGET, D3DFMT_A8R8G8B8, D3DPOOL_DEFAULT, pTex_1, NULL);
```

**这个resource既是Texture，也是renderTarget**


## **5.3 Resource Types And Pipeline Bindings**

### 5.3.2 Performant Readback

Any Resource that is used as an **output** for the **graphics pipeline** cannot be mapped/ locked

任何作为图形管线输出的资源都不能被mapped/locked

* Performant manner

如果application想要查看resources中的内容，可以使用高性能方式

将resource copied 到一个cpu 可以进行 mapped/locked  读访问的 resource中

这个resource创建的时候不会bind标记到任何管道绑定的标志

如果不是application，**有bindflag也是可以进行locked**的
