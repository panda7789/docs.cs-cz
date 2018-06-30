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
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a>Nastavení Windows kontejnery (Docker standardní na základě) pomocí příkazů prostředí Windows PowerShell v soubor Docker

S [Windows kontejnery](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview), můžete převést existující aplikace systému Windows tak, aby imagí Dockeru a nasadit je stejné nástroje jako zbytek ekosystému Docker.

Pokud chcete používat Windows kontejnery, stačí k zápisu příkazů prostředí Windows PowerShell v soubor Docker, jak je ukázáno v následujícím příkladu:

```
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

V tomto případě používáme prostředí Windows PowerShell k instalaci základní bitovou kopii systému Windows Server Core a také služby IIS.

Podobným způsobem můžete také použít příkazy prostředí Windows PowerShell nastavit další komponenty, jako jsou tradiční ASP.NET 4.x a .NET 4.6 nebo jiný Windows software, jak je vidět tady:

```
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
[Předchozí](visual-studio-tools-for-docker.md)
[další](../docker-devops-workflow/index.md)
