---
title: Operační systém, na který mají cílit kontejnery .NET
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Jaký operační systém pro cílení na kontejnery .NET
ms.date: 01/30/2020
ms.openlocfilehash: a09e3981ece478a9795c0f27acc98d604864cdd5
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77501866"
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

| Image | Komentáře |
|-------|----------|
| mcr.microsoft.com/dotnet/core/runtime:3.1 | .NET Core 3,1 s více architekturami: podporuje systémy Linux a Windows nano Server v závislosti na hostiteli Docker. |
| mcr.microsoft.com/dotnet/core/aspnet:3.1 | ASP.NET Core 3,1 s více architekturami: podporuje systémy Linux a Windows nano Server v závislosti na hostiteli Docker. <br/> Obrázek aspnetcore má několik optimalizací pro ASP.NET Core. |
| mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim | .NET Core 3,1 runtime – pouze v systémech Linux Debian distribuce |
| mcr.microsoft.com/dotnet/core/aspnet:3.1-nanoserver-1809 | .NET Core 3,1 runtime – jenom na Windows nano serveru (Windows Server verze 1809) |

## <a name="additional-resources"></a>Další zdroje

- **BitmapDecoder se nezdařila z důvodu chybějícího souboru WindowsCodecsExt. dll (problém GitHubu).**  
  <https://github.com/microsoft/dotnet-framework-docker/issues/299>

> [!div class="step-by-step"]
> [Předchozí](container-framework-choice-factors.md)
> [Další](official-net-docker-images.md)
