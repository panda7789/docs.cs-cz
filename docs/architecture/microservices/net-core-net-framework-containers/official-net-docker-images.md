---
title: Oficiální image .NET Dockeru
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Oficiální obrázky .NET Docker
ms.date: 01/30/2020
ms.openlocfilehash: 50a50587b35f811859841c4e049f40cb99479372
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77501867"
---
# <a name="official-net-docker-images"></a>Oficiální image .NET Dockeru

Oficiální bitové kopie .NET Docker jsou image Dockeru vytvořené a optimalizované společností Microsoft. Jsou veřejně dostupné v repozitářích Microsoftu v [Docker Hubu](https://hub.docker.com/u/microsoft/). Každé úložiště může obsahovat více obrázků v závislosti na verzích .NET a v závislosti na operačním systému a verzích (Linux Debian, Linux Alpine, Windows Nano Server, Windows Server Core atd.).

Vzhledem k tomu, že .NET Core 2.1, všechny image .NET Core, včetně ASP.NET <https://hub.docker.com/_/microsoft-dotnet-core/>Core jsou k dispozici v Docker Hub u .NET Core image repozitáře: .

Od května 2018 jsou bitové kopie společnosti Microsoft [syndikovány v registru microsoft kontejnerů](https://azure.microsoft.com/blog/microsoft-syndicates-container-catalog/). Oficiální katalog je stále k dispozici pouze v Docker Hubu a tam najdete aktualizovanou adresu pro vytažení obrázku.

Většina úložišť obrázků poskytuje rozsáhlé značkování, které vám pomůže vybrat nejen konkrétní verzi architektury, ale také zvolit operační systém (linuxová distribuce nebo verze systému Windows).

## <a name="net-core-and-docker-image-optimizations-for-development-versus-production"></a>Optimalizace bitových obrázků .NET Core a Docker pro vývoj versus produkční

Při vytváření imitek Dockeru pro vývojáře se Microsoft zaměřil na následující hlavní scénáře:

- Obrázky používané k *vývoji* a vytváření aplikací .NET Core.

- Obrázky používané ke *spuštění* aplikací .NET Core.

Proč více obrázků? Při vývoji, vytváření a spouštění kontejnerizovaných aplikací máte obvykle různé priority. Poskytováním různých iobrazek pro tyto samostatné úkoly pomáhá společnost Microsoft optimalizovat samostatné procesy vývoje, vytváření a nasazování aplikací.

### <a name="during-development-and-build"></a>Během vývoje a budování

Během vývoje je důležité, jak rychle můžete iterate změny a schopnost ladit změny. Velikost obrázku není tak důležitá jako možnost provádět změny v kódu a rychle zobrazit změny. Některé nástroje a "build agent kontejnery", použijte vývoj .NET Image Jádra (*mcr.microsoft.com/dotnet/core/sdk:3.1*) během procesu vývoje a sestavení. Při vytváření uvnitř kontejneru Dockeru jsou důležité aspekty prvky, které jsou potřeba ke kompilaci vaší aplikace. To zahrnuje kompilátor a všechny ostatní .NET závislosti.

Proč je tento typ image sestavení důležitý? Tuto bitové kopii nelze nasadit do produkčního prostředí. Místo toho se jedná o bitovou kopii, kterou použijete k vytvoření obsahu, který umístíte do produkční bitové kopie. Tato bitová kopie by se použila v prostředí průběžné integrace (CI) nebo při použití vícefázových sestavení Dockeru.

### <a name="in-production"></a>Ve výrobě

Co je důležité v produkčním prostředí je, jak rychle můžete nasadit a spustit kontejnery na základě produkční bitové kopie .NET Core. Proto bitová kopie pouze za běhu založená na *mcr.microsoft.com/dotnet/core/aspnet:3.1* je malá, takže může rychle cestovat po síti z registru Dockeru k hostitelům Dockeru. Obsah je připraven ke spuštění, což umožňuje nejrychlejší čas od spuštění kontejneru ke zpracování výsledků. V modelu Dockeru není potřeba kompilace\# z kódu C, jako je při spuštění dotnet sestavení nebo dotnet publikovat při použití kontejneru sestavení.

V této optimalizované bitové kopii vložíte pouze binární soubory a další obsah potřebný ke spuštění aplikace. Například obsah vytvořený `dotnet publish` obsahuje pouze zkompilované binární soubory .NET, obrázky, soubory JS a CSS. V průběhu času se zobrazí obrázky, které obsahují předem jitted (kompilace z IL nanativní, ke kterému dochází za běhu) balíčky.

Přestože existuje více verzí obrazů .NET Core a ASP.NET Core, všechny sdílejí jednu nebo více vrstev, včetně základní vrstvy. Proto je velikost místa na disku potřebné k uložení bitové kopie malá; skládá se pouze z rozdílu mezi vlastní bitovou kopii a její základní bitovou kopii. Výsledkem je, že je rychlé vytáhnout obrázek z registru.

Když prozkoumáte úložiště bitových bitových údajů .NET v Docker Hubu, najdete více verzí bitových obrázků klasifikovaných nebo označených značkami. Tyto značky pomáhají rozhodnout, který z nich použít, v závislosti na verzi, kterou potřebujete, jako jsou ty v následující tabulce:

| Image | Komentáře |
|-------|----------|
| mcr.microsoft.com/dotnet/core/aspnet:**3.1** | ASP.NET Core, s pouze runtime a optimalizací ASP.NET Core, na Linuxu a Windows (multi-arch) |
| mcr.microsoft.com/dotnet/core/sdk:**3.1** | .NET Core, včetně sad SDK, na Linuxu a Windows (multi-arch) |

> [!div class="step-by-step"]
> [Předchozí](net-container-os-targets.md)
> [další](../architect-microservice-container-applications/index.md)
