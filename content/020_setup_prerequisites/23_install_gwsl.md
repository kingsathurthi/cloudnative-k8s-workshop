---
title: "4. Install GWSL"
chapter: true
weight: 13
---

## Install GWSL
GWSL is an XServer that lets you easily run graphical Linux apps on Windows 10. GWSL stands for Graphical WSL.

:arrow_right: Download and Install [GWSL](https://github.com/Opticos/GWSL-Source/releases/download/v1.4.0/GWSL.Traditional.140.release.x64.exe)

[Github Source](https://github.com/Opticos/GWSL-Source/releases/)

> Allow any firewall alert popups to allow the traffic between host and WSL

:arrow_right: Configure Remote Display (Auto)

Open GWSL -> GWSL Distro Tools -> Configure Ubuntu 20.02 -> Auto-Export Display/Audio

![GWSL Config](../images/gwslconfig.png "GWSLConfig")

{{% notice note %}}
Skip below section, if GWSL has been already configured using previous method.
{{% /notice %}}

:arrow_right: Setup Remote Display (Manual)
``` 
export DISPLAY=$(ip -4 route | awk '{ if ($1~/default/)  print $3 }'):0.0 
export PULSE_SERVER=tcp:$(ip -4 route | awk '{ if ($1~/default/)  print $3 }') 
```
 
:arrow_right: Update profile to persist the configuration (Manual)
```
echo "export DISPLAY=\$(ip -4 route | awk '{ if (\$1~/default/)  print \$3 }'):0.0 
export PULSE_SERVER=tcp:\$(ip -4 route | awk '{ if (\$1~/default/)  print \$3 }')" >> ~/.bashrc
```
