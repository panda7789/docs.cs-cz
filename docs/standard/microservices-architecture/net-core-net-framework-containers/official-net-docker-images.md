---
title: Oficiální image .NET Dockeru
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Oficiální Image .NET Dockeru
ms.date: 01/07/2019
ms.openlocfilehash: b184e8f3606da8448a06a1cad90688958ecbce3a
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644354"
---
# <a name="official-net-docker-images"></a>Oficiální image .NET Dockeru

Oficiální .NET Dockeru Image jsou Image Dockeru vytvořené a optimalizované od Microsoftu. Jsou veřejně dostupné v úložištích Microsoft ve [Docker Hubu](https://hub.docker.com/u/microsoft/). Každé úložiště může obsahovat více bitových kopií, v závislosti na verze rozhraní .NET a v závislosti na operačním systému a verze (Linux, Debian, Alpine Linuxu, Windows Nano Server, Windows Server Core atd.).

Od verze rozhraní .NET Core 2.1 všechny .NET Core Image, jako je ASP.NET Core najdete na adrese Docker Hubu v úložišti .NET Core bitové kopie: https://hub.docker.com/_/microsoft-dotnet-core/

Většina úložišť image poskytují rozsáhlé označování pomoct při výběru ne jenom verze konkrétní verzi rozhraní framework, ale také zvolit operační systém (distribuce Linuxu nebo verze Windows).

## <a name="net-core-and-docker-image-optimizations-for-development-versus-production"></a>.NET core a Docker optimalizace image pro vývoj a produkčního prostředí

Při vytváření imagí Dockeru pro vývojáře, zaměřuje Microsoft na následující hlavní scénáře:

- Imagí používaných k *vývoj* a sestavení aplikace .NET Core.

- Imagí používaných k *spustit* aplikace .NET Core.

Proč více bitových kopií? Při vývoji, vytváření a spouštění kontejnerizovaných aplikací, obvykle mají různé priority. Zadáním různých imagí pro tyto jednotlivé úlohy Microsoft pomáhá optimalizovat samostatné procesy vývoje, sestavování a nasazování aplikací.

### <a name="during-development-and-build"></a>Během vývoje a sestavení

Během vývoje co je důležité je můžete jak rychle iterovat změny a možnost ladit změny. Velikost bitové kopie není důležité jako možnost provádět změny kódu a rychle se změny projevily. Některé nástroje a "agent sestavení kontejnery", použít obraz vývoj pro .NET Core (*mcr.microsoft.com/dotnet/core/sdk:2.2*) během procesu vývoje a sestavení. Při vytváření uvnitř kontejneru Dockeru, důležité aspekty jsou prvky, které jsou potřeba, aby bylo možné zkompilovat vaši aplikaci. To zahrnuje kompilátoru a další závislosti rozhraní .NET.

Proč je důležité tento typ bitové kopie sestavení? Tento obrázek nezvolíte nasazení do produkčního prostředí. Místo toho je obrázek, který používáte k sestavení obsahu, který umístíte do produkce image. Tato image se použije ve vašem prostředí kontinuální integrace (CI) nebo prostředí pro sestavení při použití Dockeru vícefázových sestavení.

### <a name="in-production"></a>V produkčním prostředí

Co je důležité v produkčním prostředí je, jak rychle nasadit a spustit vaše kontejnery založené na bitovou kopii produkčního prostředí .NET Core. Proto pouze modul runtime image na základě *mcr.microsoft.com/dotnet/core/aspnet:2.2* je malá, takže ho můžete projít rychle přes síť z registru Dockeru do hostitelů Docker. Obsah je připraven ke spuštění, povolení nejrychlejší doba spuštění kontejneru na zpracování výsledků. V modelu Dockeru, není nutné pro kompilaci from C\# kódu, protože došlo při spuštění sestavení dotnet nebo dotnet publikovat, kdy používá sestavení kontejneru.

V tomto optimalizované bitové kopie vložíte pouze binární soubory a jiný obsah potřebných ke spuštění aplikace. Například publikování obsahu vytvořeného v dotnet obsahuje pouze kompilované binární soubory rozhraní .NET, obrázků, JS a CSS souborů. V průběhu času se zobrazí imagí, které obsahují zpracované kompilátorem JIT předem (kompilace z IL na nativní, ke které dochází za běhu) balíčky.

I když existuje více verzí rozhraní .NET Core a ASP.NET Core imagí, ale všechny sdílet jednu nebo více vrstev, včetně základní vrstvě. Proto je malé množství místa na disku potřebné k uložení obrázku se skládá pouze rozdílů mezi vlastní image a jeho základní image. Výsledkem je, že je rychlé načíst image z registru.

Při prozkoumávání úložiště .NET image v Docker Hubu najdete několik verzí bitové kopie klasifikované nebo označené značkami. Tyto značky pomoct rozhodnout, který se má použít, v závislosti na verzi, které potřebujete, stejně jako v následující tabulce:

| Image                                       | Komentáře                                                                                          |
| ------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| MCR.microsoft.com/DotNet/Core/ASPNET:**2.2** | ASP.NET Core s pouze modul runtime a optimalizace ASP.NET Core v Linuxu a Windows (více arch) |
| MCR.microsoft.com/DotNet/Core/SDK:**2.2**    | .NET core, s zahrnutých sad SDK, na Linuxu a Windows (více arch)                                  |

> [!div class="step-by-step"]
> [Předchozí](net-container-os-targets.md)
> [další](../architect-microservice-container-applications/index.md)
