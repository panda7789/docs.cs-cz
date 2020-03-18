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
# <a name="cross-platform-targeting"></a><span data-ttu-id="feecc-103">Cílení na více platforem</span><span class="sxs-lookup"><span data-stu-id="feecc-103">Cross-platform targeting</span></span>

<span data-ttu-id="feecc-104">Moderní rozhraní .NET podporuje více operačních systémů a zařízení.</span><span class="sxs-lookup"><span data-stu-id="feecc-104">Modern .NET supports multiple operating systems and devices.</span></span> <span data-ttu-id="feecc-105">Je důležité, aby open source knihovny .NET podporovaly co nejvíce vývojářů, ať už budují ASP.NET web hostovaný v Azure, nebo hru .NET v Unity.</span><span class="sxs-lookup"><span data-stu-id="feecc-105">It's important for .NET open-source libraries to support as many developers as possible, whether they're building an ASP.NET website hosted in Azure, or a .NET game in Unity.</span></span>

## <a name="net-standard"></a><span data-ttu-id="feecc-106">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="feecc-106">.NET Standard</span></span>

<span data-ttu-id="feecc-107">Standard .NET je nejlepší způsob, jak přidat podporu pro různé platformy do knihovny .NET.</span><span class="sxs-lookup"><span data-stu-id="feecc-107">.NET Standard is the best way to add cross-platform support to a .NET library.</span></span> <span data-ttu-id="feecc-108">[.NET Standard](../net-standard.md) je specifikace rozhraní API .NET, která jsou k dispozici ve všech implementacích rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="feecc-108">[.NET Standard](../net-standard.md) is a specification of .NET APIs that are available on all .NET implementations.</span></span> <span data-ttu-id="feecc-109">Cílení .NET Standard umožňuje vytvářet knihovny, které jsou omezeny na použití rozhraní API, které jsou v dané verzi standardu .NET, což znamená, že je použitelné pro všechny platformy, které implementují tuto verzi standardu .NET.</span><span class="sxs-lookup"><span data-stu-id="feecc-109">Targeting .NET Standard lets you produce libraries that are constrained to use APIs that are in a given version of .NET Standard, which means it's usable by all platforms that implement that version of the .NET Standard.</span></span>

<span data-ttu-id="feecc-110">![.NET Standard](./media/cross-platform-targeting/platforms-netstandard.png ".NET Standard")</span><span class="sxs-lookup"><span data-stu-id="feecc-110">![.NET Standard](./media/cross-platform-targeting/platforms-netstandard.png ".NET Standard")</span></span>

<span data-ttu-id="feecc-111">Cílení na standard .NET a úspěšná kompilace projektu nezaručuje, že knihovna bude úspěšně spuštěna na všech platformách:</span><span class="sxs-lookup"><span data-stu-id="feecc-111">Targeting .NET Standard, and successfully compiling your project, doesn't guarantee the library will run successfully on all platforms:</span></span>

1. <span data-ttu-id="feecc-112">Na jiných platformách se nezdaří specifická api pro platformu.</span><span class="sxs-lookup"><span data-stu-id="feecc-112">Platform-specific APIs will fail on other platforms.</span></span> <span data-ttu-id="feecc-113">Například <xref:Microsoft.Win32.Registry?displayProperty=nameWithType> bude úspěšné v <xref:System.PlatformNotSupportedException> systému Windows a hodit při použití na jiném osu.</span><span class="sxs-lookup"><span data-stu-id="feecc-113">For example, <xref:Microsoft.Win32.Registry?displayProperty=nameWithType> will succeed on Windows and throw <xref:System.PlatformNotSupportedException> when used on any other OS.</span></span>
2. <span data-ttu-id="feecc-114">Api se mohou chovat jinak.</span><span class="sxs-lookup"><span data-stu-id="feecc-114">APIs can behave differently.</span></span> <span data-ttu-id="feecc-115">Například reflexe API mají různé charakteristiky výkonu při aplikaci používá předčasovou kompilaci na iOS nebo UPW.</span><span class="sxs-lookup"><span data-stu-id="feecc-115">For example, reflection APIs have different performance characteristics when an application uses ahead-of-time compilation on iOS or UWP.</span></span>

> [!TIP]
> <span data-ttu-id="feecc-116">Tým .NET [nabízí analyzátor Roslyn,](../analyzers/api-analyzer.md) který vám pomůže zjistit možné problémy.</span><span class="sxs-lookup"><span data-stu-id="feecc-116">The .NET team [offers a Roslyn analyzer](../analyzers/api-analyzer.md) to help you discover possible issues.</span></span>

<span data-ttu-id="feecc-117">✔️ do začít `netstandard2.0` s včetně cíle.</span><span class="sxs-lookup"><span data-stu-id="feecc-117">✔️ DO start with including a `netstandard2.0` target.</span></span>

> <span data-ttu-id="feecc-118">Většina knihoven pro obecné účely by neměla potřebovat rozhraní API mimo rozhraní .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="feecc-118">Most general-purpose libraries should not need APIs outside of .NET Standard 2.0.</span></span> <span data-ttu-id="feecc-119">.NET Standard 2.0 je podporován všemi moderními platformami a je doporučeným způsobem, jak podporovat více platforem s jedním cílem.</span><span class="sxs-lookup"><span data-stu-id="feecc-119">.NET Standard 2.0 is supported by all modern platforms and is the recommended way to support multiple platforms with one target.</span></span>

<span data-ttu-id="feecc-120">❌Vyhněte `netstandard1.x` se včetně cíle.</span><span class="sxs-lookup"><span data-stu-id="feecc-120">❌ AVOID including a `netstandard1.x` target.</span></span>

> <span data-ttu-id="feecc-121">.NET Standard 1.x je distribuován jako podrobná sada balíčků NuGet, která vytvoří velký graf závislostí balíčků a výsledkem je, že vývojáři při vytváření stahují velké množství balíčků.</span><span class="sxs-lookup"><span data-stu-id="feecc-121">.NET Standard 1.x is distributed as a granular set of NuGet packages, which creates a large package dependency graph and results in developers downloading a lot of packages when building.</span></span> <span data-ttu-id="feecc-122">Moderní platformy .NET, včetně rozhraní .NET Framework 4.6.1, UWP a Xamarin, všechny podporují standard .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="feecc-122">Modern .NET platforms, including .NET Framework 4.6.1, UWP and Xamarin, all support .NET Standard 2.0.</span></span> <span data-ttu-id="feecc-123">Měli byste cílit pouze na rozhraní .NET Standard 1.x pouze v případě, že konkrétně potřebujete cílit na starší platformu.</span><span class="sxs-lookup"><span data-stu-id="feecc-123">You should only target .NET Standard 1.x if you specifically need to target an older platform.</span></span>

<span data-ttu-id="feecc-124">✔️ do `netstandard2.0` zahrnout cíl, `netstandard1.x` pokud budete potřebovat cíl.</span><span class="sxs-lookup"><span data-stu-id="feecc-124">✔️ DO include a `netstandard2.0` target if you require a `netstandard1.x` target.</span></span>

> <span data-ttu-id="feecc-125">Všechny platformy podporující rozhraní .NET Standard `netstandard2.0` 2.0 budou používat cíl a těžit z toho, že `netstandard1.x` mají menší graf balíčků, zatímco starší platformy budou stále fungovat a vrátí se k použití cíle.</span><span class="sxs-lookup"><span data-stu-id="feecc-125">All platforms supporting .NET Standard 2.0 will use the `netstandard2.0` target and benefit from having a smaller package graph while older platforms will still work and fall back to using the `netstandard1.x` target.</span></span>

<span data-ttu-id="feecc-126">❌NEZAHRNUJTE cíl .NET Standard, pokud knihovna závisí na modelu aplikace specifické pro platformu.</span><span class="sxs-lookup"><span data-stu-id="feecc-126">❌ DO NOT include a .NET Standard target if the library relies on a platform-specific app model.</span></span>

> <span data-ttu-id="feecc-127">Například knihovna nástrojů ovládacího prvku UPW závisí na modelu aplikace, který je k dispozici pouze na UPW.</span><span class="sxs-lookup"><span data-stu-id="feecc-127">For example, a UWP control toolkit library depends on an app model that is only available on UWP.</span></span> <span data-ttu-id="feecc-128">Rozhraní API specifická pro model aplikace nebudou k dispozici ve standardu .NET.</span><span class="sxs-lookup"><span data-stu-id="feecc-128">App model specific APIs will not be available in .NET Standard.</span></span>

## <a name="multi-targeting"></a><span data-ttu-id="feecc-129">Vícenásobné cílení</span><span class="sxs-lookup"><span data-stu-id="feecc-129">Multi-targeting</span></span>

<span data-ttu-id="feecc-130">Někdy potřebujete přístup k rozhraní API specifické pro architekturu z knihoven.</span><span class="sxs-lookup"><span data-stu-id="feecc-130">Sometimes you need to access framework-specific APIs from your libraries.</span></span> <span data-ttu-id="feecc-131">Nejlepší způsob, jak volat rozhraní API specifické pro architekturu je pomocí více cílení, který vytváří váš projekt pro mnoho [rozhraní .NET cíl rámce,](../frameworks.md) nikoli pouze pro jeden.</span><span class="sxs-lookup"><span data-stu-id="feecc-131">The best way to call framework-specific APIs is using multi-targeting, which builds your project for many [.NET target frameworks](../frameworks.md) rather than for just one.</span></span>

<span data-ttu-id="feecc-132">Chcete-li chránit vaše spotřebitele před nutností vytvářet pro jednotlivé architektury, měli byste se snažit mít výstup .NET Standard plus jeden nebo více výstupů specifických pro architekturu.</span><span class="sxs-lookup"><span data-stu-id="feecc-132">To shield your consumers from having to build for individual frameworks, you should strive to have a .NET Standard output plus one or more framework-specific outputs.</span></span> <span data-ttu-id="feecc-133">S více cílení, všechny sestavení jsou zabaleny uvnitř jednoho balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="feecc-133">With multi-targeting, all assemblies are packaged inside a single NuGet package.</span></span> <span data-ttu-id="feecc-134">Spotřebitelé pak můžete odkazovat na stejný balíček a NuGet vybere příslušnou implementaci.</span><span class="sxs-lookup"><span data-stu-id="feecc-134">Consumers can then reference the same package and NuGet will pick the appropriate implementation.</span></span> <span data-ttu-id="feecc-135">Vaše knihovna .NET Standard slouží jako záložní knihovna, která se používá všude, s výjimkou případů, kdy váš balíček NuGet nabízí implementaci specifické pro architekturu.</span><span class="sxs-lookup"><span data-stu-id="feecc-135">Your .NET Standard library serves as the fallback library that is used everywhere, except for the cases where your NuGet package offers a framework-specific implementation.</span></span> <span data-ttu-id="feecc-136">Vícenásobné cílení umožňuje používat podmíněnou kompilaci ve vašem kódu a volat rozhraní API specifická pro architekturu.</span><span class="sxs-lookup"><span data-stu-id="feecc-136">Multi-targeting allows you to use conditional compilation in your code and call framework-specific APIs.</span></span>

<span data-ttu-id="feecc-137">![Balíček NuGet s více sestaveními](./media/cross-platform-targeting/nuget-package-multiple-assemblies.png "Balíček NuGet s více sestaveními")</span><span class="sxs-lookup"><span data-stu-id="feecc-137">![NuGet package with multiple assemblies](./media/cross-platform-targeting/nuget-package-multiple-assemblies.png "NuGet package with multiple assemblies")</span></span>

<span data-ttu-id="feecc-138">✔️ ZVÁŽIT cílení na implementací rozhraní .NET kromě standardu .NET.</span><span class="sxs-lookup"><span data-stu-id="feecc-138">✔️ CONSIDER targeting .NET implementations in addition to .NET Standard.</span></span>

> <span data-ttu-id="feecc-139">Cílení na implementace rozhraní .NET umožňuje volat rozhraní API specifická pro platformu, která jsou mimo standard .NET.</span><span class="sxs-lookup"><span data-stu-id="feecc-139">Targeting .NET implementations allows you to call platform-specific APIs that are outside of .NET Standard.</span></span>
>
> <span data-ttu-id="feecc-140">Při této práci nepřepírejte podporu pro standard .NET.</span><span class="sxs-lookup"><span data-stu-id="feecc-140">Do not drop support for .NET Standard when you do this.</span></span> <span data-ttu-id="feecc-141">Místo toho vyvolání z implementace a nabídnout možnosti API.</span><span class="sxs-lookup"><span data-stu-id="feecc-141">Instead, throw from the implementation and offer capability APIs.</span></span> <span data-ttu-id="feecc-142">Tímto způsobem lze knihovnu používat kdekoli a podporuje runtime light-up funkcí.</span><span class="sxs-lookup"><span data-stu-id="feecc-142">This way, your library can be used anywhere and supports runtime light-up of features.</span></span>

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

<span data-ttu-id="feecc-143">❌Vyhněte se více cílení, stejně jako cílení .NET Standard, pokud zdrojový kód je stejný pro všechny cíle.</span><span class="sxs-lookup"><span data-stu-id="feecc-143">❌ AVOID multi-targeting as well as targeting .NET Standard, if your source code is the same for all targets.</span></span>

> <span data-ttu-id="feecc-144">Sestavení .NET Standard bude automaticky použito společností NuGet.</span><span class="sxs-lookup"><span data-stu-id="feecc-144">The .NET Standard assembly will automatically be used by NuGet.</span></span> <span data-ttu-id="feecc-145">Cílení na jednotlivé implementace `*.nupkg` rozhraní .NET zvyšuje velikost bez výhody.</span><span class="sxs-lookup"><span data-stu-id="feecc-145">Targeting individual .NET implementations increases the `*.nupkg` size for no benefit.</span></span>

<span data-ttu-id="feecc-146">✔️ ZVAŽTe přidání `net461` cíle, když `netstandard2.0` nabízíte cíl.</span><span class="sxs-lookup"><span data-stu-id="feecc-146">✔️ CONSIDER adding a target for `net461` when you're offering a `netstandard2.0` target.</span></span>

> <span data-ttu-id="feecc-147">Použití rozhraní .NET Standard 2.0 z rozhraní .NET Framework má některé problémy, které byly vyřešeny v rozhraní .NET Framework 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="feecc-147">Using .NET Standard 2.0 from .NET Framework has some issues that were addressed in .NET Framework 4.7.2.</span></span> <span data-ttu-id="feecc-148">Můžete zlepšit prostředí pro vývojáře, kteří jsou stále na rozhraní .NET Framework 4.6.1 - 4.7.1 tím, že jim nabídne binární soubor, který je vytvořen pro rozhraní .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="feecc-148">You can improve the experience for developers that are still on .NET Framework 4.6.1 - 4.7.1 by offering them a binary that is built for .NET Framework 4.6.1.</span></span>

<span data-ttu-id="feecc-149">✔️ do distribuovat knihovnu pomocí balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="feecc-149">✔️ DO distribute your library using a NuGet package.</span></span>

> <span data-ttu-id="feecc-150">NuGet vybere nejlepší cíl pro vývojáře a chránit je museli vybrat příslušnou implementaci.</span><span class="sxs-lookup"><span data-stu-id="feecc-150">NuGet will select the best target for the developer and shield them having to pick the appropriate implementation.</span></span>

<span data-ttu-id="feecc-151">✔️ do použít `TargetFrameworks` vlastnost souboru projektu při vícecílení.</span><span class="sxs-lookup"><span data-stu-id="feecc-151">✔️ DO use a project file's `TargetFrameworks` property when multi-targeting.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <!-- This project will output netstandard2.0 and net461 assemblies -->
    <TargetFrameworks>netstandard2.0;net461</TargetFrameworks>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="feecc-152">✔️ zvažte použití [MSBuild.Sdk.Extras](https://github.com/onovotny/MSBuildSdkExtras) při multi-cílení pro UPW a Xamarin, protože výrazně zjednodušuje soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="feecc-152">✔️ CONSIDER using [MSBuild.Sdk.Extras](https://github.com/onovotny/MSBuildSdkExtras) when multi-targeting for UWP and Xamarin as it greatly simplifies your project file.</span></span>

## <a name="older-targets"></a><span data-ttu-id="feecc-153">Starší cíle</span><span class="sxs-lookup"><span data-stu-id="feecc-153">Older targets</span></span>

<span data-ttu-id="feecc-154">Rozhraní .NET podporuje cílení na verze rozhraní .NET Framework, které jsou dlouho mimo podporu, stejně jako platformy, které se již běžně nepoužívají.</span><span class="sxs-lookup"><span data-stu-id="feecc-154">.NET supports targeting versions of the .NET Framework that are long out of support as well as platforms that are no longer commonly used.</span></span> <span data-ttu-id="feecc-155">I když je hodnota v tom, aby vaše knihovna pracovat na co nejvíce cílů, jak je to možné, museli obejít chybějící api může přidat významné režie.</span><span class="sxs-lookup"><span data-stu-id="feecc-155">While there's value in making your library work on as many targets as possible, having to work around missing APIs can add significant overhead.</span></span> <span data-ttu-id="feecc-156">Věříme, že některé rámce již nestojí za cílení, vzhledem k jejich dosahu a omezením.</span><span class="sxs-lookup"><span data-stu-id="feecc-156">We believe certain frameworks are no longer worth targeting, considering their reach and limitations.</span></span>

<span data-ttu-id="feecc-157">❌NEZAHRNUJTE cíl knihovny přenosných tříd (PCL).</span><span class="sxs-lookup"><span data-stu-id="feecc-157">❌ DO NOT include a Portable Class Library (PCL) target.</span></span> <span data-ttu-id="feecc-158">Například, `portable-net45+win8+wpa81+wp8`.</span><span class="sxs-lookup"><span data-stu-id="feecc-158">For example, `portable-net45+win8+wpa81+wp8`.</span></span>

> <span data-ttu-id="feecc-159">.NET Standard je moderní způsob, jak podporovat knihovny .NET napříč platformami a nahrazuje pcls.</span><span class="sxs-lookup"><span data-stu-id="feecc-159">.NET Standard is the modern way to support cross-platform .NET libraries and replaces PCLs.</span></span>

<span data-ttu-id="feecc-160">❌NEZAHRNEJTE cíle pro platformy .NET, které již nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="feecc-160">❌ DO NOT include targets for .NET platforms that are no longer supported.</span></span> <span data-ttu-id="feecc-161">Například `SL4`, `WP`.</span><span class="sxs-lookup"><span data-stu-id="feecc-161">For example, `SL4`, `WP`.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="feecc-162">[Předchozí](get-started.md)
>[další](strong-naming.md)</span><span class="sxs-lookup"><span data-stu-id="feecc-162">[Previous](get-started.md)
[Next](strong-naming.md)</span></span>
