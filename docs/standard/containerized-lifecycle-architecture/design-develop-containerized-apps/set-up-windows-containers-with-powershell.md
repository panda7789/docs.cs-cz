---
title: Nastavení Windows kontejnery (Docker standardní na základě) pomocí příkazů prostředí Windows PowerShell v soubor Docker
description: Kontejnerizované Docker životního cyklu aplikací s Microsoft platforma a nástroje
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/19/2017
ms.openlocfilehash: d68378a12a16dd4072b381f00241e781b40c3e16
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105547"
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a><span data-ttu-id="08dcf-103">Nastavení Windows kontejnery (Docker standardní na základě) pomocí příkazů prostředí Windows PowerShell v soubor Docker</span><span class="sxs-lookup"><span data-stu-id="08dcf-103">Using Windows PowerShell commands in a DockerFile to set up Windows Containers (Docker standard based)</span></span>

<span data-ttu-id="08dcf-104">S [Windows kontejnery](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview), můžete převést existující aplikace systému Windows tak, aby imagí Dockeru a nasadit je stejné nástroje jako zbytek ekosystému Docker.</span><span class="sxs-lookup"><span data-stu-id="08dcf-104">With [Windows Containers](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview), you can convert your existing Windows applications to Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span>

<span data-ttu-id="08dcf-105">Pokud chcete používat Windows kontejnery, stačí k zápisu příkazů prostředí Windows PowerShell v soubor Docker, jak je ukázáno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="08dcf-105">To use Windows Containers, you just need to write Windows PowerShell commands in the DockerFile, as demonstrated in the following example:</span></span>

```
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="08dcf-106">V tomto případě používáme prostředí Windows PowerShell k instalaci základní bitovou kopii systému Windows Server Core a také služby IIS.</span><span class="sxs-lookup"><span data-stu-id="08dcf-106">In this case, we're using Windows PowerShell to install a Windows Server Core base image as well as IIS.</span></span>

<span data-ttu-id="08dcf-107">Podobným způsobem můžete také použít příkazy prostředí Windows PowerShell nastavit další komponenty, jako jsou tradiční ASP.NET 4.x a .NET 4.6 nebo jiný Windows software, jak je vidět tady:</span><span class="sxs-lookup"><span data-stu-id="08dcf-107">In a similar way, you also could use Windows PowerShell commands to set up additional components like the traditional ASP.NET 4.x and .NET 4.6 or any other Windows software, as shown here:</span></span>

```
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
<span data-ttu-id="08dcf-108">[Předchozí](visual-studio-tools-for-docker.md)
[další](../docker-devops-workflow/index.md)</span><span class="sxs-lookup"><span data-stu-id="08dcf-108">[Previous](visual-studio-tools-for-docker.md)
[Next](../docker-devops-workflow/index.md)</span></span>
