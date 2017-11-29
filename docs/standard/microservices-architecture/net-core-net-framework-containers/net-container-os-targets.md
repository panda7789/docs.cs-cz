---
title: "Jaké operačního systému k cíli s kontejnery rozhraní .NET"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Jaké operačního systému k cíli s kontejnery rozhraní .NET"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 828ccb5e7a76f9419e80793b6cb3a6ba24f358cf
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
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

-   Microsoft /**dotnet:2.0.0-runtime-Klára**

        .NET Core 2.0 runtime-only on Linux

-   Microsoft /**dotnet:2.0.0-runtime-nanoserver-. 1709** 

        .NET Core 2.0 runtime-only on Windows Nano Server (Windows Server 2016 Fall Creators Update version 1709)

-   Microsoft /**aspnetcore:2.0**
    
        .NET Core 2.0 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.
        The aspnetcore image has a few optimizations for ASP.NET Core. 





>[!div class="step-by-step"]
[Předchozí] (kontejner framework – volba factors.md) [Další] (oficiální net-docker-images.md)
