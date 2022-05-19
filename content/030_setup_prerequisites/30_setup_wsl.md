---
title: "1. Install WSL and Linux"
chapter: true
weight: 10
---

## Windows Subsystem for Linux (WSL)

{{% children %}}

{{% notice warning %}}
You must be running Windows 10 version 2004 and higher (Build 19041 and higher) or Windows 11. We highly recommend you to go to the [WSL Installation](https://docs.microsoft.com/en-us/windows/wsl/install) to get started with WSL environment.
{{% /notice %}}

The Windows Subsystem for Linux lets developers run a GNU/Linux environment directly on Windows, unmodified, without the overhead of a traditional virtual machine or dualboot setup.

#### Install Windows Subsytem for Linux (WSL)

:arrow_right: Powershell/CMD
```
wsl --install
```

#### Install Linux environment (Ubuntu 20.04)

:arrow_right: Powershell/CMD
```
wsl --install -d Ubuntu-20.04
```

