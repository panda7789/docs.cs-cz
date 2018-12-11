---
title: Cílení na .NET knihoven napříč platformami
description: Doporučené osvědčené postupy pro vytváření knihovny pro různé platformy .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 6bd310f2e4b7a9bd7bb550ed9c7da9ebabdf64ba
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129711"
---
# <a name="cross-platform-targeting"></a>Cílení na více platforem

Moderní .NET podporuje několik operačních systémů a zařízení. Je důležité pro open source knihovny .NET pro podporu tolik vývojáři co nejvíce, zda že sestavujete Web ASP.NET hostovaný v Azure nebo rozhraní .NET hry v Unity.

## <a name="net-standard"></a>.NET Standard

.NET standard je nejlepší způsob, jak přidat podporu pro různé platformy do knihovny .NET. [.NET standard](../net-standard.md) je specifikace rozhraní API .NET, která jsou k dispozici na všech implementace .NET. Cílení na .NET Standard umožňuje vytvořit knihovny, které jsou omezeny na použití rozhraní API, která jsou v dané verzi rozhraní .NET Standard, což znamená, že je možné ji použít ve všech platformách, které implementují verzi .NET Standard.

![.NET standard](./media/cross-platform-targeting/platforms-netstandard.png ".NET Standard")

Cílení na .NET Standard a úspěšně kompilace projektu nezaručuje, že knihovny úspěšně poběží na všech platformách:

1. Rozhraní API pro konkrétní platformu selže na jiných platformách. Například <xref:Microsoft.Win32.Registry?displayProperty=nameWithType> úspěšná na Windows, který se vyvolat <xref:System.PlatformNotSupportedException> při použití na jiných operačních systémech.
2. Rozhraní API se může chovat jinak. Například reflexe rozhraní API mají jiné výkonové charakteristiky když aplikace využívá ahead of time kompilace v Iosu nebo UWP.

> [!TIP]
> Tým .NET [nabízí Roslyn analyzátor](../analyzers/api-analyzer.md) vám pomůžou zjistit informace o možných problémech.

**PROVEĎTE ✔️** začínat včetně `netstandard2.0` cíl.

> Většina pro obecné účely knihovny by neměl musí rozhraní API mimo rozhraní .NET Standard 2.0. Rozhraní .NET standard 2.0 podporuje všechny moderní platformy a je doporučován k podporování více platforem s jedním cílem.

**❌ Nepoužívejte** včetně `netstandard1.x` cíl.

> .NET standard 1.x je distribuován jako podrobné sadu balíčků NuGet, které vytvoří graf závislosti velký balíček, jejichž výsledkem vývojáři stahuje velké balíčky se při sestavování. Moderní platformy .NET, včetně rozhraní .NET Framework 4.6.1, UPW a Xamarin, všechny podporují .NET Standard 2.0. By měla pouze cílíte .NET Standard 1.x, pokud je výslovně potřeba cílit na starší platformy.

**✔️ PROVEĎTE** zahrnout `netstandard2.0` cílit, pokud budete potřebovat `netstandard1.x` cíl.

> Budou používat všechny platformy podporuje .NET Standard 2.0 `netstandard2.0` cíl a těžit z s menší graf balíčku, zatímco starší platformy i nadále fungovat a vrátí k používání `netstandard1.x` cíl.

**❌ NEPODPORUJÍ** zahrnout .NET Standard cíl, pokud knihovny závisí na modelu aplikací pro konkrétní platformu.

> Například sada nástrojů knihovny ovládacích prvků UPW závisí na modelu aplikace, která je dostupná pouze na UPW. Konkrétní aplikace modelu rozhraní API není k dispozici v .NET Standard.

## <a name="multi-targeting"></a>Cílení na více platforem

Někdy potřebujete přístup k rozhraním API pro konkrétní rozhraní z knihovny. Nejlepší způsob, jak volat rozhraní API pro konkrétní rozhraní používá, cílení na více platforem, který sestaví váš projekt pro mnoho [cílové rozhraní .NET](../frameworks.md) , a nikoli pro jen jeden.

K ochraně zákazníci nebudou muset sestavení pro jednotlivá rozhraní, je nutné snažit se mít .NET standardní výstup a jeden nebo více výstupů specifické pro architekturu. Pomocí cílení na více platforem jsou sbaleny všechna sestavení v jediném balíčku NuGet. Uživatele můžete odkázat na stejném balíčku a NuGet, vybere vhodné implementaci. Knihovny .NET Standard slouží jako záložní knihovna, která je použít všude, s výjimkou případů, kdy svůj balíček NuGet nabízí implementace specifické pro architekturu. Cílení na více platforem vám umožňuje používat podmíněnou kompilaci ve vašem kódu a volání rozhraní API pro konkrétní rozhraní.

![Balíček NuGet s více sestavení](./media/cross-platform-targeting/nuget-package-multiple-assemblies.png "balíček NuGet s více sestavení")

**✔️ ZVAŽTE** cílí na .NET implementace kromě .NET Standard.

> Cílení na implementace .NET umožňuje volat rozhraní API pro konkrétní platformu, která se nachází mimo .NET Standard.
>
> Když toto provedete, neuvolňují podpora pro .NET Standard. Místo toho vyvolat od implementace rozhraní a nabízejí funkce rozhraní API. Tímto způsobem své knihovny lze je použít kdekoli a podporuje runtime světla shrnutí těchto funkcí.

**❌ Nepoužívejte** cílení na více platforem a také cílí na .NET Standard, pokud váš zdrojový kód je stejný pro všechny cíle.

> .NET Standard sestavení se automaticky použije balíčkem NuGet. Cílení na jednotlivé implementace .NET zvýší `*.nupkg` velikost bez jakékoli výhody.

**✔️ ZVAŽTE** přidání cíle `net461` Pokud nabízíte `netstandard2.0` cíl. 

> Použití .NET Standard 2.0 z rozhraní .NET Framework má některé problémy, které se zákazníky a vyřešené v rozhraní .NET Framework 4.7.2. Můžete vylepšit prostředí pro vývojáře, které jsou stále v rozhraní .NET Framework 4.6.1 – 4.7.1 nabídkou binární soubor, který je sestaven pro rozhraní .NET Framework 4.6.1.

**PROVEĎTE ✔️** distribuovat knihovny pomocí balíčku NuGet.

> NuGet vybere nejlepší cíl pro vývojáře a stínit museli výběr vhodné implementaci.

**PROVEĎTE ✔️** pomocí souboru projektu `TargetFrameworks` při cílení na více platforem.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <!-- This project will output netstandard2.0 and net461 assemblies -->
    <TargetFrameworks>netstandard2.0;net461</TargetFrameworks>
  </PropertyGroup>
</Project>
```

**✔️ ZVAŽTE** pomocí [MSBuild.Sdk.Extras](https://github.com/onovotny/MSBuildSdkExtras) při cílení na více platforem pro UPW a Xamarin jako výrazně zjednodušuje váš soubor projektu.

## <a name="older-targets"></a>Starší cíle

.NET podporuje cílení verze rozhraní .NET Framework, které jsou dlouhé mimo podporu, jakož i platformy, které se už běžně používají. Pokud hodnota při vytvoření knihovny práce na mnoho cíle jako je to možné, museli obejít chybí rozhraní API můžete přidávat významné režie. Jsme přesvědčeni jisti, že rozhraní stojí za to už cílení, zvažujete jeho dosah a omezení.

**❌ NEPODPORUJÍ** zahrnout cíl Přenosná knihovna tříd (PCL). Například, `portable-net45+win8+wpa81+wp8`.

> .NET standard je moderní způsob, jak podpora knihovny pro různé platformy .NET a nahradí PCLs.

**❌ NEPODPORUJÍ** obsahovat cílové hodnoty pro platformy .NET, které již nejsou podporovány. Například `SL4`, `WP`.

>[!div class="step-by-step"]
>[Předchozí](get-started.md)
>[další](strong-naming.md)
