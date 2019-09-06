---
title: Oficiální image .NET Dockeru
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Oficiální image Docker pro .NET
ms.date: 01/07/2019
ms.openlocfilehash: b184e8f3606da8448a06a1cad90688958ecbce3a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296487"
---
# <a name="official-net-docker-images"></a>Oficiální image .NET Dockeru

Oficiální image rozhraní .NET Docker jsou image Docker vytvořené a optimalizované Microsoftem. Jsou veřejně dostupné v úložištích Microsoftu v [Docker Hub](https://hub.docker.com/u/microsoft/). Každé úložiště může obsahovat několik imagí v závislosti na verzích .NET a v závislosti na operačním systému a verzích (Linux Debian, Linux Alpine, Windows nano Server, Windows Server Core atd.).

Vzhledem k tomu, že je .NET Core 2,1, jsou všechny image .NET Core, včetně pro ASP.NET Core dostupné v Docker Hub v úložišti imagí .NET Core: https://hub.docker.com/_/microsoft-dotnet-core/

Většina úložišť imagí poskytuje rozsáhlé označování, které vám pomůžou vybrat nejen konkrétní verzi architektury, ale také zvolit operační systém (Linux distribuce nebo Windows verze).

## <a name="net-core-and-docker-image-optimizations-for-development-versus-production"></a>Optimalizace imagí .NET Core a Docker pro vývoj a produkci

Při sestavování imagí Docker pro vývojáře se společnost Microsoft zaměřuje na následující hlavní scénáře:

- Obrázky používané k *vývoji* a sestavování aplikací .NET Core

- Image používané ke *spouštění* aplikací .NET Core

Proč více imagí? Při vývoji, sestavování a spouštění kontejnerových aplikací jsou obvykle k dispozici různé priority. Poskytováním různých imagí pro tyto samostatné úlohy pomáhá Microsoft optimalizovat samostatné procesy vývoje, sestavování a nasazování aplikací.

### <a name="during-development-and-build"></a>Během vývoje a sestavení

V průběhu vývoje je důležité, jak rychle iterovat změny a možnost ladit změny. Velikost obrázku není tak důležitá jako schopnost provádět změny kódu a rychle zobrazit změny. Některé nástroje a kontejnery agentů sestavení využívají během vývoje a procesu sestavování bitovou kopii rozhraní .NET Core (*MCR.Microsoft.com/dotnet/Core/SDK:2.2*). Při sestavování uvnitř kontejneru Docker jsou důležité aspekty prvky, které jsou potřeba pro zkompilování vaší aplikace. To zahrnuje kompilátor a všechny další závislosti rozhraní .NET.

Proč je tento typ image sestavení důležitý? Tuto image nebudete nasazovat do produkčního prostředí. Místo toho se jedná o obrázek, který použijete k vytvoření obsahu, který umístíte do produkční image. Tento obrázek se použije v prostředí pro průběžnou integraci (CI) nebo v prostředí sestavení při použití víceprocesorového sestavení Docker.

### <a name="in-production"></a>V produkčním prostředí

Důležité informace o tom, jak rychle můžete nasadit a spustit kontejnery založené na provozní imagi .NET Core, najdete v tématu o produkčním prostředí. Proto je bitová kopie pouze za běhu založená na *MCR.Microsoft.com/dotnet/Core/ASPNET:2.2* malá, aby mohla rychle cestovat přes síť z registru Docker do hostitelů Docker. Obsah je připravený ke spuštění, což umožňuje nejrychlejší čas od spuštění kontejneru až po zpracování výsledků. V modelu Docker není nutné provádět kompilaci z kódu jazyka C\# , protože při použití kontejneru sestavení je k dispozici při spuštění příkazu dotnet Build nebo dotnet Publish.

V této optimalizované imagi vložíte jenom binární soubory a další obsah potřebný ke spuštění aplikace. Například obsah vytvořený pomocí dotnet publish obsahuje pouze kompilované binární soubory .NET, obrázky,. js a. CSS. V průběhu času se zobrazí obrázky, které obsahují zpracovaných kompilátorem JIT (kompilace z IL do nativní, ke které dochází v době běhu) balíčků.

I když existuje více verzí rozhraní .NET Core a ASP.NET Core imagí, všechny sdílejí jednu nebo více vrstev, včetně základní vrstvy. Proto je velikost místa na disku potřebného pro uložení obrázku malá. obsahuje jenom rozdíl mezi vlastní image a její základní imagí. Výsledkem je rychlé načtení obrázku z registru.

Když prozkoumáte úložiště imagí .NET v Docker Hub, zjistíte více verzí imagí klasifikovaných nebo označených pomocí značek. Tyto značky vám pomůžou určit, která z nich se má použít, v závislosti na verzi, kterou potřebujete, třeba v následující tabulce:

| Image                                       | Komentáře                                                                                          |
| ------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| mcr.microsoft.com/dotnet/core/aspnet:**2,2** | ASP.NET Core, pouze s modulem runtime a optimalizace ASP.NET Core v systémech Linux a Windows (více archů) |
| mcr.microsoft.com/dotnet/core/sdk:**2,2**    | Rozhraní .NET Core se zahrnutými sadami SDK v systému Linux a Windows (vícenásobný arch)                                  |

> [!div class="step-by-step"]
> [Předchozí](net-container-os-targets.md)Další
> [](../architect-microservice-container-applications/index.md)
