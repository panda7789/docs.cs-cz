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
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a>Použití příkazů prostředí Windows PowerShell v souboru DockerFile k nastavení kontejneru Windows (založeno na standardu Dockeru)

Pomocí [kontejnerů Windows](/virtualization/windowscontainers/about/index)můžete převést stávající aplikace pro Windows na Image Docker a nasadit je pomocí stejných nástrojů jako zbytek ekosystému Docker.

Chcete-li používat kontejnery Windows, stačí v souboru Dockerfile psát příkazy prostředí Windows PowerShell, jak je znázorněno v následujícím příkladu:

```Dockerfile
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

V tomto případě používáme Windows PowerShell k instalaci základní image jádra Windows serveru i služby IIS.

Podobným způsobem můžete také použít příkazy prostředí Windows PowerShell k nastavení dalších komponent, jako jsou tradiční ASP.NET 4. x a .NET 4,6 nebo jakýkoli jiný software pro Windows, jak je znázorněno zde:

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
>[Předchozí](visual-studio-tools-for-docker.md) 
> [Další](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)
