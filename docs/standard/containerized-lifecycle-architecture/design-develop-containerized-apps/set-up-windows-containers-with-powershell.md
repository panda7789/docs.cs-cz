---
title: Pomocí příkazů prostředí Windows PowerShell v souboru DockerFile k nastavení kontejnery Windows (založeno na standardu Dockeru)
description: Zjistěte, jak pomocí prostředí PowerShell při práci s Dockerem v kontejnerech Windows
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: d9c0bc28f62d44eb7471b99c63055ef43da12a69
ms.sourcegitcommit: 2b986afe4ce9e13bbeec929c9737757eb61de60e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/22/2019
ms.locfileid: "56664702"
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a>Pomocí příkazů prostředí Windows PowerShell v souboru DockerFile k nastavení kontejnery Windows (založeno na standardu Dockeru)

S [kontejnery Windows](/virtualization/windowscontainers/about/index), můžete převést existující aplikace Windows do Image Dockeru a nasadit je pomocí stejných nástrojů jako ostatní ekosystému Dockeru.

Pokud chcete používat kontejnery Windows, stačí k zápisu příkazů prostředí Windows PowerShell v souboru DockerFile, jak je ukázáno v následujícím příkladu:

```Dockerfile
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

V tomto případě používáme prostředí Windows PowerShell k instalaci základní image jádra Windows serveru, jakož i služby IIS.

Podobným způsobem můžete také použít příkazy prostředí Windows PowerShell nastavit další komponenty, jako jsou tradiční ASP.NET 4.x a .NET 4.6 nebo jakýkoli jiný Windows software, jak je znázorněno zde:

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
>[Předchozí](visual-studio-tools-for-docker.md)
>[další](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)
