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
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a><span data-ttu-id="ea6f2-103">Pomocí příkazů prostředí Windows PowerShell v souboru DockerFile k nastavení kontejnery Windows (založeno na standardu Dockeru)</span><span class="sxs-lookup"><span data-stu-id="ea6f2-103">Using Windows PowerShell commands in a DockerFile to set up Windows Containers (Docker standard based)</span></span>

<span data-ttu-id="ea6f2-104">S [kontejnery Windows](/virtualization/windowscontainers/about/index), můžete převést existující aplikace Windows do Image Dockeru a nasadit je pomocí stejných nástrojů jako ostatní ekosystému Dockeru.</span><span class="sxs-lookup"><span data-stu-id="ea6f2-104">With [Windows Containers](/virtualization/windowscontainers/about/index), you can convert your existing Windows applications to Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span>

<span data-ttu-id="ea6f2-105">Pokud chcete používat kontejnery Windows, stačí k zápisu příkazů prostředí Windows PowerShell v souboru DockerFile, jak je ukázáno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ea6f2-105">To use Windows Containers, you just need to write Windows PowerShell commands in the DockerFile, as demonstrated in the following example:</span></span>

```Dockerfile
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="ea6f2-106">V tomto případě používáme prostředí Windows PowerShell k instalaci základní image jádra Windows serveru, jakož i služby IIS.</span><span class="sxs-lookup"><span data-stu-id="ea6f2-106">In this case, we're using Windows PowerShell to install a Windows Server Core base image as well as IIS.</span></span>

<span data-ttu-id="ea6f2-107">Podobným způsobem můžete také použít příkazy prostředí Windows PowerShell nastavit další komponenty, jako jsou tradiční ASP.NET 4.x a .NET 4.6 nebo jakýkoli jiný Windows software, jak je znázorněno zde:</span><span class="sxs-lookup"><span data-stu-id="ea6f2-107">In a similar way, you also could use Windows PowerShell commands to set up additional components like the traditional ASP.NET 4.x and .NET 4.6 or any other Windows software, as shown here:</span></span>

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
><span data-ttu-id="ea6f2-108">[Předchozí](visual-studio-tools-for-docker.md)
>[další](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="ea6f2-108">[Previous](visual-studio-tools-for-docker.md)
[Next](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)</span></span>
