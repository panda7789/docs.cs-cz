---
title: Jaké operačního systému k cíli s kontejnery rozhraní .NET
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Jaké operačního systému k cíli s kontejnery rozhraní .NET
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: 53b279a3325ae0fb662cd91a6f7f454b765196ff
ms.sourcegitcommit: 6c480773ae896f45af4671fb3e26611a50e4dd81
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2018
ms.locfileid: "35251009"
---
# <a name="what-os-to-target-with-net-containers"></a>Jaké operačního systému k cíli s kontejnery rozhraní .NET

Zadané různorodost operační systémy podporované nástrojem Docker a rozdíly mezi rozhraní .NET Framework a .NET Core, by měl cílové konkrétní operační systém a konkrétní verze v závislosti na rozhraní framework, který používáte. 

Pro systém Windows můžete použít Windows Server Core nebo Nano Server systému Windows. Tyto verze systému Windows zadejte různými charakteristikami (služba IIS v systému Windows Server Core a vlastním hostováním webového serveru jako Kestrel v Nano Server), které mohou být potřebné rozhraní .NET Framework nebo .NET Core, v uvedeném pořadí. 

Pro systémy Linux více distribucích jsou dostupné a podporované v oficiální imagí Dockeru .NET (například Debian).

Obrázek 3-1 se zobrazí možné verze operačního systému v závislosti na rozhraní .NET framework, který používá.

![](./media/image1.png)

**Obrázek 3-1.** Operační systémy do cíle v závislosti na verze rozhraní .NET framework

Můžete také vytvořit vlastní image Docker v případech, kde chcete použít jiný distro Linux nebo místo bitovou kopii s verzemi není poskytovaný společností Microsoft. Například může vytvořit bitovou kopii pomocí ASP.NET Core systémem tradiční rozhraní .NET Framework a Windows Server Core, což není tak běžné scénáře pro Docker.

Když přidáte název bitové kopie do souboru soubor Docker, můžete vybrat operační systém a verze v závislosti na značku, kterou používáte, jako v následujících příkladech:

-   Microsoft /**dotnet:2.1 – modul runtime**

        .NET Core 2.1 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.

-   Microsoft /**dotnet:2.1-aspnetcore – modul runtime**
    
        ASP.NET Core 2.1 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.
        The aspnetcore image has a few optimizations for ASP.NET Core. 

-   Microsoft /**dotnet:2.1-aspnetcore-runtime-alpine** 

        .NET Core 2.1 runtime-only on Linux Alpine distro

-   Microsoft /**dotnet:2.1-aspnetcore-runtime-nanoserver-1803** 

        .NET Core 2.1 runtime-only on Windows Nano Server (Windows Server version 1803)




>[!div class="step-by-step"]
[Předchozí] (kontejner framework – volba factors.md) [Další] (oficiální net-docker-images.md)
