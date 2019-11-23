---
title: Operační systém, na který mají cílit kontejnery .NET
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Jaký operační systém pro cílení na kontejnery .NET
ms.date: 01/07/2019
ms.openlocfilehash: dcf91f5ab808a8704201979f6bab1140c3343bce
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736924"
---
# <a name="what-os-to-target-with-net-containers"></a>Operační systém, na který mají cílit kontejnery .NET

Vzhledem k rozmanitosti operačních systémů, které podporuje Docker, a rozdílů mezi .NET Framework a .NET Core, byste měli cílit na konkrétní operační systém a konkrétní verze v závislosti na používaném rozhraní.

Pro Windows můžete použít jádro Windows serveru nebo Windows nano Server. Tyto verze systému Windows poskytují různé charakteristiky (IIS v jádru Windows serveru a webový server v místním prostředí, jako je Kestrel na nano serveru), které může být potřeba .NET Framework nebo .NET Core v uvedeném pořadí.

Pro Linux je k dispozici několik distribuce a podporují se v oficiálních bitových kopiích .NET Docker (jako Debian).

Na obrázku 3-1 můžete zobrazit možnou verzi operačního systému v závislosti na použitém rozhraní .NET Framework.

![Diagram znázorňující, jaký operační systém se má použít, se kterými kontejnery .NET.](./media/net-container-os-targets/targeting-operating-systems.png)

**Obrázek 3-1.** Operační systémy určené pro cílení v závislosti na verzích rozhraní .NET Framework

Při nasazování starších .NET Framework aplikací musíte cílit na Windows Server Core kompatibilní se staršími aplikacemi a IIS, ale má větší obrázek. Při nasazování aplikací .NET Core můžete cílit na Windows nano Server, což je cloudově optimalizované, používá Kestrel a je menší a spouští se rychleji. Můžete také cílit na Linux, podporu Debian, Alpine a další. Také používá Kestrel, je menší a začíná rychleji.

Můžete také vytvořit vlastní image Docker v případech, kdy chcete použít jiný distribuce pro Linux nebo kde chcete image s verzemi, které Microsoft neposkytuje. Můžete například vytvořit bitovou kopii s ASP.NET Core spuštěnou v tradičním .NET Framework a jádro Windows serveru, což je neobvyklý scénář pro Docker.

> [!IMPORTANT]
> Při použití základních imagí Windows serveru se můžete setkat s tím, že v porovnání s úplnými bitovými kopiemi systému Windows chybí některé knihovny DLL. Tento problém může být možné vyřešit vytvořením vlastní image jádra serveru, přidáním chybějících souborů v době sestavení obrázku, jak je uvedeno v tomto [komentáři k GitHubu](https://github.com/microsoft/dotnet-framework-docker/issues/299#issuecomment-511537448).

Když přidáte název Image do souboru souboru Dockerfile, můžete vybrat operační systém a verzi v závislosti na používané značce, jako v následujících příkladech:

| Obrázek | Komentáře |
|-------|----------|
| mcr.microsoft.com/dotnet/core/runtime:2.2 | .NET Core 2,2 s více architekturami: podporuje systémy Linux a Windows nano Server v závislosti na hostiteli Docker. |
| mcr.microsoft.com/dotnet/core/aspnet:2.2 | ASP.NET Core 2,2 s více architekturami: podporuje systémy Linux a Windows nano Server v závislosti na hostiteli Docker. <br/> Obrázek aspnetcore má několik optimalizací pro ASP.NET Core. |
| mcr.microsoft.com/dotnet/core/aspnet:2.2-alpine | .NET Core 2,2 runtime – jenom pro Linux Alpine distribuce |
| mcr.microsoft.com/dotnet/core/aspnet:2.2-nanoserver-1803 | .NET Core 2,2 runtime – jenom na Windows nano serveru (Windows Server verze 1803) |

## <a name="additional-resources"></a>Další materiály a zdroje informací

- **BitmapDecoder se nezdařila z důvodu chybějícího souboru WindowsCodecsExt. dll (problém GitHubu).**  
  <https://github.com/microsoft/dotnet-framework-docker/issues/299>

> [!div class="step-by-step"]
> [Předchozí](container-framework-choice-factors.md)
> [Další](official-net-docker-images.md)
