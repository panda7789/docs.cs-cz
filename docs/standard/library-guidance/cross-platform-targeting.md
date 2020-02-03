---
title: Cílení na různé platformy pro knihovny .NET
description: Doporučení osvědčených postupů pro vytváření knihoven .NET pro různé platformy
ms.date: 08/12/2019
ms.openlocfilehash: 61adff3759984554bb83531b4f9d8a49e29c929c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731458"
---
# <a name="cross-platform-targeting"></a>Cílení na více platforem

Moderní rozhraní .NET podporuje několik operačních systémů a zařízení. Je důležité, aby open source knihovny pro .NET podporovaly co nejvíce vývojářů, ať už vytváří web ASP.NET hostovaný v Azure, nebo hry .NET v Unity.

## <a name="net-standard"></a>.NET Standard

.NET Standard je nejlepším způsobem, jak přidat podporu pro více platforem do knihovny .NET. [.NET Standard](../net-standard.md) je specifikace rozhraní API .NET, která jsou k dispozici ve všech implementacích rozhraní .NET. Cílení na .NET Standard umožňuje vytvořit knihovny, které jsou omezené na používání rozhraní API, která jsou v dané verzi .NET Standard, což znamená, že je použitelná pro všechny platformy, které implementují tuto verzi .NET Standard.

![.NET Standard](./media/cross-platform-targeting/platforms-netstandard.png ".NET Standard")

Při cílení .NET Standard a úspěšném kompilování projektu nezaručujeme, že se knihovna na všech platformách úspěšně spustí:

1. Rozhraní API specifická pro platformu se na jiných platformách nezdaří. Například <xref:Microsoft.Win32.Registry?displayProperty=nameWithType> bude ve Windows úspěšné a vyvolat <xref:System.PlatformNotSupportedException> při použití v jakémkoli jiném operačním systému.
2. Rozhraní API se můžou chovat jinak. Například rozhraní API pro reflexi mají různé charakteristiky výkonu, když aplikace používá předdobu kompilace v systému iOS nebo UWP.

> [!TIP]
> Tým .NET [nabízí nástroj Roslyn Analyzer](../analyzers/api-analyzer.md) , který vám umožní zjistit možné problémy.

✔️ začínat zahrnutím cíle `netstandard2.0`.

> Většina knihoven pro obecné použití by neměla vyžadovat rozhraní API mimo .NET Standard 2,0. .NET Standard 2,0 podporuje všechny moderní platformy a je doporučeným způsobem, jak podporovat více platforem s jedním cílem.

❌ se vyhnout zahrnutí cíle `netstandard1.x`.

> .NET Standard 1. x se distribuuje jako podrobná sada balíčků NuGet, která vytvoří graf závislostí balíčku a výsledkem je, že vývojáři stahují spoustu balíčků při sestavování. Moderní platformy .NET, včetně .NET Framework 4.6.1, UWP a Xamarin, jsou všechny podpory .NET Standard 2,0. Pokud výslovně potřebujete cílit na starší platformu, měli byste cílit pouze na .NET Standard 1. x.

✔️ zahrnout cíl `netstandard2.0`, pokud požadujete cíl `netstandard1.x`.

> Na všech platformách, které podporují .NET Standard 2,0, se použije `netstandard2.0` cíl a bude výhodná mít menší graf balíčků, zatímco starší platformy budou pořád fungovat a budou se vracet k používání `netstandard1.x`ho cíle.

❌ neobsahují .NET Standard cíl, pokud knihovna spoléhá na model aplikace specifický pro platformu.

> Například knihovna Control Toolkit pro UWP závisí na modelu aplikace, který je k dispozici pouze pro UWP. Rozhraní API specifická pro model aplikace nebudou k dispozici v .NET Standard.

## <a name="multi-targeting"></a>Cílení na více platforem

Někdy potřebujete přístup k rozhraním API pro konkrétní rozhraní z vašich knihoven. Nejlepším způsobem, jak volat rozhraní API specifická pro rozhraní, je použití cílení na více verzí, který sestaví projekt pro mnoho [cílových rozhraní .NET](../frameworks.md) , nikoli jenom pro jeden.

Pokud chcete, aby vaši spotřebitelé mohli sestavovat pro jednotlivé architektury, měli byste se snažit mít výstup .NET Standard a jeden nebo několik výstupů specifických pro rozhraní. V případě cílení na více platforem jsou všechna sestavení zabalena do jednoho balíčku NuGet. Příjemci pak můžou odkazovat na stejný balíček a NuGet vybere příslušnou implementaci. Vaše knihovna .NET Standard slouží jako záložní knihovna, která se používá všude, s výjimkou případů, kdy váš balíček NuGet nabízí implementaci specifickou pro rozhraní. Cílení na více platforem umožňuje použít podmíněnou kompilaci v kódu a volat rozhraní API specifická pro rozhraní.

![Balíček NuGet s více sestaveními](./media/cross-platform-targeting/nuget-package-multiple-assemblies.png "Balíček NuGet s více sestaveními")

✔️ Zvažte kromě .NET Standard také cílení implementace rozhraní .NET.

> Cílení implementace rozhraní .NET umožňuje volat rozhraní API specifická pro platformu, která jsou mimo .NET Standard.
>
> Pokud to uděláte, neprovádějte vyřazení podpory pro .NET Standard. Místo toho vyvolejte z rozhraní API funkce implementace a nabídky. Tímto způsobem se vaše knihovna dá použít kdekoli a podporuje modul runtime s lehkými funkcemi.

```csharp
public static class GpsLocation
{
    // This project uses multi-targeting to expose device-specific APIs to .NET Standard.
    public static async Task<(double latitude, double longitude)> GetCoordinatesAsync()
    {
#if NET461
        return CallDotNetFramworkApi();
#elif WINDOWS_UWP
        return CallUwpApi();
#else
        throw new PlatformNotSupportedException();
#endif
    }

    // Allows callers to check without having to catch PlatformNotSupportedException
    // or replicating the OS check.
    public static bool IsSupported
    {
        get
        {
#if NET461 || WINDOWS_UWP
            return true;
#else
            return false;
#endif
        }
    }
}
```

Pokud je váš zdrojový kód pro všechny cíle stejný, ❌ se vyhnout cílení na více platforem a také cílení na .NET Standard.

> Sestavení .NET Standard bude automaticky použito NuGet. Cílení na jednotlivé implementace rozhraní .NET zvyšuje `*.nupkg`ou velikost bez výhod.

✔️ Zvažte přidání cíle pro `net461`, když přidáváte `netstandard2.0` cíl.

> Použití .NET Standard 2,0 z .NET Framework obsahuje některé problémy, které byly vyřešeny v .NET Framework 4.7.2. Můžete vylepšit prostředí pro vývojáře, kteří jsou pořád na .NET Framework 4.6.1-4.7.1, a nabízet jim binární soubor, který je sestavený pro .NET Framework 4.6.1.

✔️ k distribuci knihovny pomocí balíčku NuGet.

> NuGet vybere nejlepší cíl pro vývojáře a chrání je před tím, než bude muset vybrat příslušnou implementaci.

✔️ použít vlastnost `TargetFrameworks` souboru projektu při cílení na více platforem.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <!-- This project will output netstandard2.0 and net461 assemblies -->
    <TargetFrameworks>netstandard2.0;net461</TargetFrameworks>
  </PropertyGroup>
</Project>
```

✔️ Zvažte použití nástroje [MSBuild. SDK. Extras](https://github.com/onovotny/MSBuildSdkExtras) při cílení na více platforem pro UWP a Xamarin, protože značně zjednodušuje váš soubor projektu.

## <a name="older-targets"></a>Starší cíle

Rozhraní .NET podporuje cílení na verze .NET Framework, které nejsou podporované, i platformy, které se už běžně nepoužívají. I když existuje hodnota, aby vaše knihovna fungovala s co možná nejvíce cíli, může dopracovat s chybějícími rozhraními API a zvýšit tak značnou režii. Domníváme se, že některá rozhraní už necílí na cílení a berou v úvahách jejich dosah a omezení.

❌ neobsahují cíl knihovny přenosných tříd (PCL). například `portable-net45+win8+wpa81+wp8`.

> .NET Standard je moderní způsob, jak podporovat knihovny .NET pro různé platformy a nahrazuje PCLs.

❌ nezahrnují cíle pro platformy .NET, které už nejsou podporované. Například `SL4``WP`.

>[!div class="step-by-step"]
>[Předchozí](get-started.md)
>[Další](strong-naming.md)
