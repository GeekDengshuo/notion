# 17.Output Merger Stage

## 1.States

blend state 和 depth/stencil state 的对象，创建以后就不能编辑

如果允许编辑对象，那必须跟踪或者刷新管道(track and flush pipeline)

### 1.1Blend State

4096 blend objects can be created per context

### 1.2Depth/Stencil State

4096 depth/stencil objects can be created per context
