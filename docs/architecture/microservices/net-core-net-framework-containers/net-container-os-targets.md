---
title: Operační systém, na který mají cílit kontejnery .NET
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Jaký operační systém pro cílení na kontejnery .NET
ms.date: 01/07/2019
ms.openlocfilehash: 7380889374e69ca4d3c981a401af703c19263de5
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039693"
---
# <a name="what-os-to-target-with-net-containers"></a>Operační systém, na který mají cílit kontejnery .NET

Vzhledem k rozmanitosti operačních systémů, které podporuje Docker, a rozdílů mezi .NET Framework a .NET Core, byste měli cílit na konkrétní operační systém a konkrétní verze v závislosti na používaném rozhraní.

Pro Windows můžete použít jádro Windows serveru nebo Windows nano Server. Tyto verze systému Windows poskytují různé charakteristiky (IIS v jádru Windows serveru a webový server v místním prostředí, jako je Kestrel na nano serveru), které může být potřeba .NET Framework nebo .NET Core v uvedeném pořadí.

Pro Linux je k dispozici několik distribuce a podporují se v oficiálních bitových kopiích .NET Docker (jako Debian).

Na obrázku 3-1 můžete zobrazit možnou verzi operačního systému v závislosti na použitém rozhraní .NET Framework.

![Při nasazování starších aplikací .NET Framework, které je třeba cílit na jádro Windows serveru, je kompatibilní se staršími aplikacemi a službou IIS má větší obrázek. Při nasazování aplikací .NET Core můžete cílit na Windows nano Server, což je cloudově optimalizované, používá Kestrel a je menší a spouští se rychleji. Můžete také cílit na Linux, podporu Debian, Alpine a další. Používá také Kestrel a je menší a spouští se rychleji.](./media/image1.png)

**Obrázek 3-1.** Operační systémy určené pro cílení v závislosti na verzích rozhraní .NET Framework

Můžete také vytvořit vlastní image Docker v případech, kdy chcete použít jiný distribuce pro Linux nebo kde chcete image s verzemi, které Microsoft neposkytuje. Můžete například vytvořit bitovou kopii s ASP.NET Core spuštěnou v tradičním .NET Framework a jádro Windows serveru, což je neobvyklý scénář pro Docker.

Když přidáte název Image do souboru souboru Dockerfile, můžete vybrat operační systém a verzi v závislosti na používané značce, jako v následujících příkladech:

| Image | Komentáře |
|-------|----------|
| mcr.microsoft.com/dotnet/core/runtime:2.2 | .NET Core 2,2 s více architekturami: Podporuje systémy Linux a Windows nano Server v závislosti na hostiteli Docker. |
| mcr.microsoft.com/dotnet/core/aspnet:2.2 | ASP.NET Core 2,2 s více architekturami: Podporuje systémy Linux a Windows nano Server v závislosti na hostiteli Docker. <br/> Obrázek aspnetcore má několik optimalizací pro ASP.NET Core. |
| mcr.microsoft.com/dotnet/core/aspnet:2.2-alpine | .NET Core 2,2 runtime – jenom pro Linux Alpine distribuce |
| mcr.microsoft.com/dotnet/core/aspnet:2.2-nanoserver-1803 | .NET Core 2,2 runtime – jenom na Windows nano serveru (Windows Server verze 1803) |

> [!div class="step-by-step"]
> [Předchozí](container-framework-choice-factors.md)Další
> [](official-net-docker-images.md)
