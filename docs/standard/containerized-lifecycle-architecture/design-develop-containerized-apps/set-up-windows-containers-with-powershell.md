---
title: Pomocí příkazů prostředí Windows PowerShell v souboru DockerFile k nastavení kontejnery Windows (založeno na standardu Dockeru)
description: Životní cyklus aplikace kontejnerizovaných Dockeru s platformou a nástroji Microsoft
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/19/2017
ms.openlocfilehash: 5e85beea0efbee6a2b6594e3a49d705505a36e1c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149390"
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a>Pomocí příkazů prostředí Windows PowerShell v souboru DockerFile k nastavení kontejnery Windows (založeno na standardu Dockeru)

S [kontejnery Windows](/virtualization/windowscontainers/about/index), můžete převést existující aplikace Windows do Image Dockeru a nasadit je pomocí stejných nástrojů jako ostatní ekosystému Dockeru.

Pokud chcete používat kontejnery Windows, stačí k zápisu příkazů prostředí Windows PowerShell v souboru DockerFile, jak je ukázáno v následujícím příkladu:

```
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

V tomto případě používáme prostředí Windows PowerShell k instalaci základní image jádra Windows serveru, jakož i služby IIS.

Podobným způsobem můžete také použít příkazy prostředí Windows PowerShell nastavit další komponenty, jako jsou tradiční ASP.NET 4.x a .NET 4.6 nebo jakýkoli jiný Windows software, jak je znázorněno zde:

```
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
>[Předchozí](visual-studio-tools-for-docker.md)
>[další](../docker-devops-workflow/index.md)
