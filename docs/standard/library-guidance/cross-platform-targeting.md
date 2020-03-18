---
title: Cílení napříč platformami pro knihovny .NET
description: Doporučení osvědčených postupů pro vytváření knihoven .NET pro různé platformy.
ms.date: 08/12/2019
ms.openlocfilehash: 61adff3759984554bb83531b4f9d8a49e29c929c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "76731458"
---
# <a name="cross-platform-targeting"></a>Cílení na více platforem

Moderní rozhraní .NET podporuje více operačních systémů a zařízení. Je důležité, aby open source knihovny .NET podporovaly co nejvíce vývojářů, ať už budují ASP.NET web hostovaný v Azure, nebo hru .NET v Unity.

## <a name="net-standard"></a>.NET Standard

Standard .NET je nejlepší způsob, jak přidat podporu pro různé platformy do knihovny .NET. [.NET Standard](../net-standard.md) je specifikace rozhraní API .NET, která jsou k dispozici ve všech implementacích rozhraní .NET. Cílení .NET Standard umožňuje vytvářet knihovny, které jsou omezeny na použití rozhraní API, které jsou v dané verzi standardu .NET, což znamená, že je použitelné pro všechny platformy, které implementují tuto verzi standardu .NET.

![.NET Standard](./media/cross-platform-targeting/platforms-netstandard.png ".NET Standard")

Cílení na standard .NET a úspěšná kompilace projektu nezaručuje, že knihovna bude úspěšně spuštěna na všech platformách:

1. Na jiných platformách se nezdaří specifická api pro platformu. Například <xref:Microsoft.Win32.Registry?displayProperty=nameWithType> bude úspěšné v <xref:System.PlatformNotSupportedException> systému Windows a hodit při použití na jiném osu.
2. Api se mohou chovat jinak. Například reflexe API mají různé charakteristiky výkonu při aplikaci používá předčasovou kompilaci na iOS nebo UPW.

> [!TIP]
> Tým .NET [nabízí analyzátor Roslyn,](../analyzers/api-analyzer.md) který vám pomůže zjistit možné problémy.

✔️ do začít `netstandard2.0` s včetně cíle.

> Většina knihoven pro obecné účely by neměla potřebovat rozhraní API mimo rozhraní .NET Standard 2.0. .NET Standard 2.0 je podporován všemi moderními platformami a je doporučeným způsobem, jak podporovat více platforem s jedním cílem.

❌Vyhněte `netstandard1.x` se včetně cíle.

> .NET Standard 1.x je distribuován jako podrobná sada balíčků NuGet, která vytvoří velký graf závislostí balíčků a výsledkem je, že vývojáři při vytváření stahují velké množství balíčků. Moderní platformy .NET, včetně rozhraní .NET Framework 4.6.1, UWP a Xamarin, všechny podporují standard .NET Standard 2.0. Měli byste cílit pouze na rozhraní .NET Standard 1.x pouze v případě, že konkrétně potřebujete cílit na starší platformu.

✔️ do `netstandard2.0` zahrnout cíl, `netstandard1.x` pokud budete potřebovat cíl.

> Všechny platformy podporující rozhraní .NET Standard `netstandard2.0` 2.0 budou používat cíl a těžit z toho, že `netstandard1.x` mají menší graf balíčků, zatímco starší platformy budou stále fungovat a vrátí se k použití cíle.

❌NEZAHRNUJTE cíl .NET Standard, pokud knihovna závisí na modelu aplikace specifické pro platformu.

> Například knihovna nástrojů ovládacího prvku UPW závisí na modelu aplikace, který je k dispozici pouze na UPW. Rozhraní API specifická pro model aplikace nebudou k dispozici ve standardu .NET.

## <a name="multi-targeting"></a>Vícenásobné cílení

Někdy potřebujete přístup k rozhraní API specifické pro architekturu z knihoven. Nejlepší způsob, jak volat rozhraní API specifické pro architekturu je pomocí více cílení, který vytváří váš projekt pro mnoho [rozhraní .NET cíl rámce,](../frameworks.md) nikoli pouze pro jeden.

Chcete-li chránit vaše spotřebitele před nutností vytvářet pro jednotlivé architektury, měli byste se snažit mít výstup .NET Standard plus jeden nebo více výstupů specifických pro architekturu. S více cílení, všechny sestavení jsou zabaleny uvnitř jednoho balíčku NuGet. Spotřebitelé pak můžete odkazovat na stejný balíček a NuGet vybere příslušnou implementaci. Vaše knihovna .NET Standard slouží jako záložní knihovna, která se používá všude, s výjimkou případů, kdy váš balíček NuGet nabízí implementaci specifické pro architekturu. Vícenásobné cílení umožňuje používat podmíněnou kompilaci ve vašem kódu a volat rozhraní API specifická pro architekturu.

![Balíček NuGet s více sestaveními](./media/cross-platform-targeting/nuget-package-multiple-assemblies.png "Balíček NuGet s více sestaveními")

✔️ ZVÁŽIT cílení na implementací rozhraní .NET kromě standardu .NET.

> Cílení na implementace rozhraní .NET umožňuje volat rozhraní API specifická pro platformu, která jsou mimo standard .NET.
>
> Při této práci nepřepírejte podporu pro standard .NET. Místo toho vyvolání z implementace a nabídnout možnosti API. Tímto způsobem lze knihovnu používat kdekoli a podporuje runtime light-up funkcí.

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

❌Vyhněte se více cílení, stejně jako cílení .NET Standard, pokud zdrojový kód je stejný pro všechny cíle.

> Sestavení .NET Standard bude automaticky použito společností NuGet. Cílení na jednotlivé implementace `*.nupkg` rozhraní .NET zvyšuje velikost bez výhody.

✔️ ZVAŽTe přidání `net461` cíle, když `netstandard2.0` nabízíte cíl.

> Použití rozhraní .NET Standard 2.0 z rozhraní .NET Framework má některé problémy, které byly vyřešeny v rozhraní .NET Framework 4.7.2. Můžete zlepšit prostředí pro vývojáře, kteří jsou stále na rozhraní .NET Framework 4.6.1 - 4.7.1 tím, že jim nabídne binární soubor, který je vytvořen pro rozhraní .NET Framework 4.6.1.

✔️ do distribuovat knihovnu pomocí balíčku NuGet.

> NuGet vybere nejlepší cíl pro vývojáře a chránit je museli vybrat příslušnou implementaci.

✔️ do použít `TargetFrameworks` vlastnost souboru projektu při vícecílení.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <!-- This project will output netstandard2.0 and net461 assemblies -->
    <TargetFrameworks>netstandard2.0;net461</TargetFrameworks>
  </PropertyGroup>
</Project>
```

✔️ zvažte použití [MSBuild.Sdk.Extras](https://github.com/onovotny/MSBuildSdkExtras) při multi-cílení pro UPW a Xamarin, protože výrazně zjednodušuje soubor projektu.

## <a name="older-targets"></a>Starší cíle

Rozhraní .NET podporuje cílení na verze rozhraní .NET Framework, které jsou dlouho mimo podporu, stejně jako platformy, které se již běžně nepoužívají. I když je hodnota v tom, aby vaše knihovna pracovat na co nejvíce cílů, jak je to možné, museli obejít chybějící api může přidat významné režie. Věříme, že některé rámce již nestojí za cílení, vzhledem k jejich dosahu a omezením.

❌NEZAHRNUJTE cíl knihovny přenosných tříd (PCL). Například, `portable-net45+win8+wpa81+wp8`.

> .NET Standard je moderní způsob, jak podporovat knihovny .NET napříč platformami a nahrazuje pcls.

❌NEZAHRNEJTE cíle pro platformy .NET, které již nejsou podporovány. Například `SL4`, `WP`.

>[!div class="step-by-step"]
>[Předchozí](get-started.md)
>[další](strong-naming.md)
