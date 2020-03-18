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
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a><span data-ttu-id="9592c-103">Použití příkazů prostředí Windows PowerShell v souboru DockerFile k nastavení kontejneru Windows (založeno na standardu Dockeru)</span><span class="sxs-lookup"><span data-stu-id="9592c-103">Using Windows PowerShell commands in a DockerFile to set up Windows Containers (Docker standard based)</span></span>

<span data-ttu-id="9592c-104">S [Windows Containers](/virtualization/windowscontainers/about/index)můžete převést existující aplikace Windows na image Dockeru a nasadit je pomocí stejných nástrojů jako zbytek ekosystému Dockeru.</span><span class="sxs-lookup"><span data-stu-id="9592c-104">With [Windows Containers](/virtualization/windowscontainers/about/index), you can convert your existing Windows applications to Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span>

<span data-ttu-id="9592c-105">Chcete-li použít kontejnery systému Windows, stačí napsat příkazy prostředí Windows PowerShell v souboru DockerFile, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="9592c-105">To use Windows Containers, you just need to write Windows PowerShell commands in the DockerFile, as demonstrated in the following example:</span></span>

```Dockerfile
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="9592c-106">V takovém případě používáme prostředí Windows PowerShell k instalaci základní bitové kopie jádra systému Windows Server core i služby IIS.</span><span class="sxs-lookup"><span data-stu-id="9592c-106">In this case, we're using Windows PowerShell to install a Windows Server Core base image as well as IIS.</span></span>

<span data-ttu-id="9592c-107">Podobným způsobem můžete také použít příkazy prostředí Windows PowerShell k nastavení dalších součástí, jako je tradiční ASP.NET 4.x a .NET 4.6 nebo jakýkoli jiný software windows, jak je znázorněno zde:</span><span class="sxs-lookup"><span data-stu-id="9592c-107">In a similar way, you also could use Windows PowerShell commands to set up additional components like the traditional ASP.NET 4.x and .NET 4.6 or any other Windows software, as shown here:</span></span>

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
><span data-ttu-id="9592c-108">[Předchozí](visual-studio-tools-for-docker.md)
>[další](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="9592c-108">[Previous](visual-studio-tools-for-docker.md)
[Next](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)</span></span>
