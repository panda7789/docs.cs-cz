---
title: Použití příkazů prostředí Windows PowerShell v souboru DockerFile k nastavení kontejneru Windows (založeno na standardu Dockeru)
description: Naučte se používat PowerShell při práci s Docker v kontejnerech Windows.
ms.date: 08/06/2020
ms.openlocfilehash: 4e7b9e7fedf11b97b3f468aef541bf72a4e88ebc
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2020
ms.locfileid: "87915386"
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a><span data-ttu-id="29cf8-103">Použití příkazů prostředí Windows PowerShell v souboru DockerFile k nastavení kontejneru Windows (založeno na standardu Dockeru)</span><span class="sxs-lookup"><span data-stu-id="29cf8-103">Using Windows PowerShell commands in a DockerFile to set up Windows Containers (Docker standard based)</span></span>

<span data-ttu-id="29cf8-104">Pomocí [kontejnerů Windows](/virtualization/windowscontainers/about/index)můžete převést stávající aplikace pro Windows na Image Docker a nasadit je pomocí stejných nástrojů jako zbytek ekosystému Docker.</span><span class="sxs-lookup"><span data-stu-id="29cf8-104">With [Windows Containers](/virtualization/windowscontainers/about/index), you can convert your existing Windows applications to Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span>

<span data-ttu-id="29cf8-105">Chcete-li používat kontejnery Windows, stačí v souboru Dockerfile psát příkazy prostředí Windows PowerShell, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="29cf8-105">To use Windows Containers, you just need to write Windows PowerShell commands in the DockerFile, as demonstrated in the following example:</span></span>

```Dockerfile
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="29cf8-106">V tomto případě používáme Windows PowerShell k instalaci základní image jádra Windows serveru i služby IIS.</span><span class="sxs-lookup"><span data-stu-id="29cf8-106">In this case, we're using Windows PowerShell to install a Windows Server Core base image as well as IIS.</span></span>

<span data-ttu-id="29cf8-107">Podobným způsobem můžete také použít příkazy prostředí Windows PowerShell k nastavení dalších komponent, jako jsou tradiční ASP.NET 4. x a .NET 4,6 nebo jakýkoli jiný software pro Windows, jak je znázorněno zde:</span><span class="sxs-lookup"><span data-stu-id="29cf8-107">In a similar way, you also could use Windows PowerShell commands to set up additional components like the traditional ASP.NET 4.x and .NET 4.6 or any other Windows software, as shown here:</span></span>

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
><span data-ttu-id="29cf8-108">[Předchozí](visual-studio-tools-for-docker.md) 
> [Další](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="29cf8-108">[Previous](visual-studio-tools-for-docker.md)
[Next](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)</span></span>
