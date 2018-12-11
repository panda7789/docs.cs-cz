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
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a><span data-ttu-id="4e3e2-103">Pomocí příkazů prostředí Windows PowerShell v souboru DockerFile k nastavení kontejnery Windows (založeno na standardu Dockeru)</span><span class="sxs-lookup"><span data-stu-id="4e3e2-103">Using Windows PowerShell commands in a DockerFile to set up Windows Containers (Docker standard based)</span></span>

<span data-ttu-id="4e3e2-104">S [kontejnery Windows](/virtualization/windowscontainers/about/index), můžete převést existující aplikace Windows do Image Dockeru a nasadit je pomocí stejných nástrojů jako ostatní ekosystému Dockeru.</span><span class="sxs-lookup"><span data-stu-id="4e3e2-104">With [Windows Containers](/virtualization/windowscontainers/about/index), you can convert your existing Windows applications to Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span>

<span data-ttu-id="4e3e2-105">Pokud chcete používat kontejnery Windows, stačí k zápisu příkazů prostředí Windows PowerShell v souboru DockerFile, jak je ukázáno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="4e3e2-105">To use Windows Containers, you just need to write Windows PowerShell commands in the DockerFile, as demonstrated in the following example:</span></span>

```
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="4e3e2-106">V tomto případě používáme prostředí Windows PowerShell k instalaci základní image jádra Windows serveru, jakož i služby IIS.</span><span class="sxs-lookup"><span data-stu-id="4e3e2-106">In this case, we're using Windows PowerShell to install a Windows Server Core base image as well as IIS.</span></span>

<span data-ttu-id="4e3e2-107">Podobným způsobem můžete také použít příkazy prostředí Windows PowerShell nastavit další komponenty, jako jsou tradiční ASP.NET 4.x a .NET 4.6 nebo jakýkoli jiný Windows software, jak je znázorněno zde:</span><span class="sxs-lookup"><span data-stu-id="4e3e2-107">In a similar way, you also could use Windows PowerShell commands to set up additional components like the traditional ASP.NET 4.x and .NET 4.6 or any other Windows software, as shown here:</span></span>

```
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
><span data-ttu-id="4e3e2-108">[Předchozí](visual-studio-tools-for-docker.md)
>[další](../docker-devops-workflow/index.md)</span><span class="sxs-lookup"><span data-stu-id="4e3e2-108">[Previous](visual-studio-tools-for-docker.md)
[Next](../docker-devops-workflow/index.md)</span></span>
