---
title: Použití příkazů prostředí Windows PowerShell v souboru DockerFile k nastavení kontejneru Windows (založeno na standardu Dockeru)
description: Přečtěte si, jak používat PowerShell při práci s Dockerem v kontejnerech Windows
ms.date: 02/15/2019
ms.openlocfilehash: e91d278aef1365a111e8d67ff04092dfc6a44185
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295704"
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a>Použití příkazů prostředí Windows PowerShell v souboru DockerFile k nastavení kontejneru Windows (založeno na standardu Dockeru)

S [Windows Containers](/virtualization/windowscontainers/about/index)můžete převést existující aplikace Windows na image Dockeru a nasadit je pomocí stejných nástrojů jako zbytek ekosystému Dockeru.

Chcete-li použít kontejnery systému Windows, stačí napsat příkazy prostředí Windows PowerShell v souboru DockerFile, jak je znázorněno v následujícím příkladu:

```Dockerfile
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

V takovém případě používáme prostředí Windows PowerShell k instalaci základní bitové kopie jádra systému Windows Server core i služby IIS.

Podobným způsobem můžete také použít příkazy prostředí Windows PowerShell k nastavení dalších součástí, jako je tradiční ASP.NET 4.x a .NET 4.6 nebo jakýkoli jiný software windows, jak je znázorněno zde:

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
>[Předchozí](visual-studio-tools-for-docker.md)
>[další](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)
