---
title: Oficiální imagí Dockeru rozhraní .NET
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Oficiální imagí Dockeru rozhraní .NET
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/06/2018
ms.openlocfilehash: bb2190a4fae6f8a26b220fd12ecb9f65ea6f4b96
ms.sourcegitcommit: 6c480773ae896f45af4671fb3e26611a50e4dd81
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2018
ms.locfileid: "35251113"
---
# <a name="official-net-docker-images"></a>Oficiální imagí Dockeru rozhraní .NET

Oficiální Docker .NET Image jsou imagí Dockeru vytvořené a optimalizované společností Microsoft. Jsou veřejně dostupné v Microsoft úložiště na [úložiště Docker Hub](https://hub.docker.com/u/microsoft/). Každý úložiště může obsahovat více bitových kopií, v závislosti na rozhraní .NET verze a v závislosti na operační systém a verze (Linux Debian, Linux Alpine, Windows Nano Server, jádro systému Windows Server, atd.).

Od verze rozhraní .NET Core 2.1, které jsou k dispozici na úložiště Docker Hub v všechny .NET Core bitové kopie, včetně pro ASP.NET Core [úložišti bitové kopie .NET Core](https://hub.docker.com/r/microsoft/dotnet/).

Většina úložiště image poskytují rozsáhlé označování, můžete vybrat nejen verzi konkrétní framework, ale taky vybrat operační systém (verze Windows nebo Linux distro).


## <a name="net-core-and-docker-image-optimizations-for-development-versus-production"></a>.NET core a Docker optimalizace image pro vývoj a výroby

Při vytváření imagí Dockeru pro vývojáře, Microsoft se zaměřuje na následující hlavní scénáře:

-   Obrázků použitých k *vyvíjet* a vytvářet aplikace .NET Core.

-   Obrázků použitých k *spustit* aplikace .NET Core.

Proč více bitových kopií? Při vývoji, vytváření a spouštění kontejnerizované aplikací, obvykle mají různých priorit. Zadáním jiné bitové kopie pro tyto jednotlivé úlohy Microsoft umožňuje optimalizovat samostatné procesy vývoje, vytváření a nasazování aplikací.

### <a name="during-development-and-build"></a>Během vývoje a sestavení

Během vývoje důležité je, jak rychle iterovat změny a možnost ladění změny. Velikost bitové kopie není důležité jako možnost provádět změny kódu a rychle zobrazit změny. Některé nástroje a "agenta sestavení kontejnery", použijte vývoj image ASP.NET Core (**microsoft / dotnet:2.1-sdk**) během procesu vývoje a sestavení. Při sestavování uvnitř kontejner Docker, jsou důležité aspekty prvky, které jsou nutné k kompilace aplikace. Tato hodnota zahrnuje kompilátor a všechny další závislosti rozhraní .NET, a webové vývoj závislosti.

Tento typ sestavení bitové kopie je důležité Nenasazujte tuto bitovou kopii do produkčního prostředí. Místo toho je obrázek, který použijete k sestavení obsahu, které umístíte do bitové kopie produkční. Tento image se použije ve vašem prostředí průběžnou integraci (CI) nebo prostředí sestavení, při použití více fáze Docker sestavení.

### <a name="in-production"></a>V produkčním prostředí

Co je důležité v produkčním prostředí je, jak rychle nasadit a spustit kontejnerů na základě bitové kopie produkční .NET Core. Proto na základě bitové kopie jen runtime **microsoft / dotnet:2.1-aspnetcore – modul runtime** je malá, aby ho mohou projít rychle přes síť z registru Docker do hostitelů Docker. Obsah je připraven ke spuštění, povolení nejrychlejší čas spuštění kontejner, aby zpracování výsledků. V modelu Docker, není nutné pro kompilaci z C\# kódu, protože došlo při spuštění dotnet sestavení nebo dotnet publikovat při používá kontejneru sestavení.

Na tomto obrázku optimalizované uveďte pouze binární soubory a jiný obsah potřebné ke spuštění aplikace. Například publikovat obsah vytvořený dotnet. obsahuje jenom binární soubory kompilované .NET, bitové kopie, .js a .css soubory. V čase uvidíte bitové kopie, které obsahují balíčky předběžné jitted.

I když existují několik verzí .NET Core a ASP.NET Core bitové kopie, budou všechny sdílet jednu nebo více vrstev, včetně základní vrstvy. Proto je malá; množství místa na disku pro uložení obrázku obsahuje jenom rozdíl mezi vlastní bitovou kopii a jeho základní image. Výsledkem je, že se jedná o rychle bitovou kopii pro vyžádání obsahu z registru.

Při prozkoumávání úložiště bitové kopie .NET v nástroji Docker Hub najdete několik verzí bitovou kopii klasifikované nebo označené jako značky. Tyto značky pomůže se rozhodnout, které z nich chcete použít, v závislosti na verzi, kterou budete potřebovat, stejně jako v následující tabulce:

-   Microsoft/dotnet:**2.1-aspnetcore – modul runtime**

        ASP.NET Core, with runtime only and ASP.NET Core optimizations, on Linux and Windows (multi-arch)

-   Microsoft /**dotnet:2.1-sdk**

        .NET Core, with SDKs included, on Linux and Windows (multi-arch)


>[!div class="step-by-step"]
[Předchozí] (net kontejneru os-targets.md) [Další] (.. /Architect-microservice-Container-Applications/index.MD)
