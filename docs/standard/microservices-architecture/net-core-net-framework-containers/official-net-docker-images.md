---
title: Oficiální imagí Dockeru rozhraní .NET
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Oficiální imagí Dockeru rozhraní .NET
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: d2105603fe1fcbacd995710c9b365ec406bad255
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="official-net-docker-images"></a>Oficiální imagí Dockeru rozhraní .NET

Oficiální Docker .NET Image jsou imagí Dockeru vytvořené a optimalizované společností Microsoft. Jsou veřejně dostupné v Microsoft úložiště na [úložiště Docker Hub](https://hub.docker.com/u/microsoft/). Každý úložiště může obsahovat více bitových kopií, v závislosti na rozhraní .NET verze a v závislosti na operační systém a verze (Linux Debian, Linux Alpine, Windows Nano Server, jádro systému Windows Server, atd.).

Vize Microsoftu pro .NET úložiště je tak, aby měl granulární a zaměřují se úložiště, kde úložišti představuje konkrétní scénář nebo zatížení. Například [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) bitové kopie by měl být použit při pomocí ASP.NET Core na Docker, protože tyto Image ASP.NET Core poskytují další optimalizace Ano kontejnery můžete spustit rychlejší.

Na druhé straně Image .NET Core (microsoft/dotnet) jsou určeny k konzole aplikace založené na .NET Core. Například procesy batch, Azure WebJobs a scénáře konzoly by měl použít .NET Core. Tyto bitové kopie nezahrnují zásobník ASP.NET Core, výsledkem je menší obrázek kontejneru.

Většina úložiště image poskytují rozsáhlé označování, můžete vybrat nejen verzi konkrétní framework, ale taky vybrat operační systém (verze Windows nebo Linux distro).

Další informace o oficiální bitových kopiích .NET Docker od společnosti Microsoft najdete v tématu [Imagí Dockeru .NET souhrn](https://aka.ms/dotnetdockerimages).

## <a name="net-core-and-docker-image-optimizations-for-development-versus-production"></a>.NET core a Docker optimalizace image pro vývoj a výroby

Při vytváření imagí Dockeru pro vývojáře, Microsoft se zaměřuje na následující hlavní scénáře:

-   Obrázků použitých k *vyvíjet* a vytvářet aplikace .NET Core.

-   Obrázků použitých k *spustit* aplikace .NET Core.

Proč více bitových kopií? Při vývoji, vytváření a spouštění kontejnerizované aplikací, obvykle mají různých priorit. Zadáním jiné bitové kopie pro tyto jednotlivé úlohy Microsoft umožňuje optimalizovat samostatné procesy vývoje, vytváření a nasazování aplikací.

### <a name="during-development-and-build"></a>Během vývoje a sestavení

Během vývoje důležité je, jak rychle iterovat změny a možnost ladění změny. Velikost bitové kopie není důležité jako možnost provádět změny kódu a rychle zobrazit změny. Některé nástroje a "agenta sestavení kontejnery", použijte vývoj image ASP.NET Core (microsoft/aspnetcore sestavení) během vývoje a proces sestavení. Při sestavování uvnitř kontejner Docker, jsou důležité aspekty prvky, které jsou nutné k kompilace aplikace. To zahrnuje kompilátor a všechny další závislosti rozhraní .NET, plus webové vývoj závislosti jako npm, Gulp a Bower.

Tento typ sestavení bitové kopie je důležité Nenasazujte tuto bitovou kopii do produkčního prostředí. Místo toho je obrázek, který použijete k sestavení obsahu, které umístíte do bitové kopie produkční. Tento image se použije ve vašem prostředí průběžnou integraci (CI) nebo prostředí pro sestavení. Například místo ruční instalaci všechny závislosti aplikací přímo na agentovi sestavení hostitele (virtuální počítač, např.), agent sestavení by doložit bitové kopie sestavení .NET Core s všechny závislosti, které jsou požadované pro sestavení aplikace. Agenta sestavení pouze musí vědět, jak spustit tento Docker image. To usnadňuje prostředí položek konfigurace a udělá z něj mnohem předvídatelnější.

### <a name="in-production"></a>V produkčním prostředí

Co je důležité v produkčním prostředí je, jak rychle nasadit a spustit kontejnerů na základě bitové kopie produkční .NET Core. Proto na základě bitové kopie jen runtime [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) je malá, aby ho mohou projít rychle přes síť z registru Docker do hostitelů Docker. Obsah je připraven ke spuštění, povolení nejrychlejší čas spuštění kontejner, aby zpracování výsledků. V modelu Docker, není nutné pro kompilaci z C\# kódu, protože došlo při spuštění dotnet sestavení nebo dotnet publikovat při používá kontejneru sestavení.

Na tomto obrázku optimalizované uveďte pouze binární soubory a jiný obsah potřebné ke spuštění aplikace. Například publikovat obsah vytvořený dotnet. obsahuje jenom binární soubory kompilované .NET, bitové kopie, .js a .css soubory. V čase uvidíte bitové kopie, které obsahují balíčky předběžné jitted.

I když existují několik verzí .NET Core a ASP.NET Core bitové kopie, budou všechny sdílet jednu nebo více vrstev, včetně základní vrstvy. Proto je malá; množství místa na disku pro uložení obrázku obsahuje jenom rozdíl mezi vlastní bitovou kopii a jeho základní image. Výsledkem je, že se jedná o rychle bitovou kopii pro vyžádání obsahu z registru.

Při prozkoumávání úložiště bitové kopie .NET v nástroji Docker Hub najdete několik verzí bitovou kopii klasifikované nebo označené jako značky. Tyto značky pomůže se rozhodnout, které z nich chcete použít, v závislosti na verzi, kterou budete potřebovat, stejně jako v následující tabulce:

-   Microsoft /**aspnetcore:2.0**

        ASP.NET Core, with runtime only and ASP.NET Core optimizations, on Linux and Windows (multi-arch)

-   Microsoft /**aspnetcore-sestavení: 2.0**

        ASP.NET Core, with SDKs included, on Linux and Windows (multi-arch)


>[!div class="step-by-step"]
[Předchozí] (net kontejneru os-targets.md) [Další] (.. /Architect-microservice-Container-Applications/index.MD)
