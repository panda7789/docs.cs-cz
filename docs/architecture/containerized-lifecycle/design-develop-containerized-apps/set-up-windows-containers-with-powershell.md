---
title: Použití příkazů prostředí Windows PowerShell v souboru Dockerfile k nastavení kontejnerů Windows (na bázi Docker Standard)
description: Naučte se používat PowerShell při práci s Docker v kontejnerech Windows.
ms.date: 02/15/2019
ms.openlocfilehash: e91d278aef1365a111e8d67ff04092dfc6a44185
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295704"
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a>Použití příkazů prostředí Windows PowerShell v souboru Dockerfile k nastavení kontejnerů Windows (na bázi Docker Standard)

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
>[Předchozí](visual-studio-tools-for-docker.md)Další
>[](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)
