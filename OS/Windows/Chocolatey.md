## Chocolatey


chocolatey:  Windows 包管理工具 ,类似于brew

* power shell 安装

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('<https://chocolatey.org/install.ps1>'))
```

* 查看信息

```powershell
choco -v
choco upgrade chocolatey
```

* 常用command指令

```powershell
choco list -li 查看本地安装的软件
choco search nodejs 查找安装包
choco install sublimetext3 下载
choco uninstall sublimetext3 卸载
choco upgrade sublimetext3 更新（update）
```
