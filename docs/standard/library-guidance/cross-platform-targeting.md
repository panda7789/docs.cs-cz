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
# <a name="cross-platform-targeting"></a><span data-ttu-id="85582-103">Cílení na více platforem</span><span class="sxs-lookup"><span data-stu-id="85582-103">Cross-platform targeting</span></span>

<span data-ttu-id="85582-104">Moderní rozhraní .NET podporuje několik operačních systémů a zařízení.</span><span class="sxs-lookup"><span data-stu-id="85582-104">Modern .NET supports multiple operating systems and devices.</span></span> <span data-ttu-id="85582-105">Je důležité, aby open source knihovny pro .NET podporovaly co nejvíce vývojářů, ať už vytváří web ASP.NET hostovaný v Azure, nebo hry .NET v Unity.</span><span class="sxs-lookup"><span data-stu-id="85582-105">It's important for .NET open-source libraries to support as many developers as possible, whether they're building an ASP.NET website hosted in Azure, or a .NET game in Unity.</span></span>

## <a name="net-standard"></a><span data-ttu-id="85582-106">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="85582-106">.NET Standard</span></span>

<span data-ttu-id="85582-107">.NET Standard je nejlepším způsobem, jak přidat podporu pro více platforem do knihovny .NET.</span><span class="sxs-lookup"><span data-stu-id="85582-107">.NET Standard is the best way to add cross-platform support to a .NET library.</span></span> <span data-ttu-id="85582-108">[.NET Standard](../net-standard.md) je specifikace rozhraní API .NET, která jsou k dispozici ve všech implementacích rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="85582-108">[.NET Standard](../net-standard.md) is a specification of .NET APIs that are available on all .NET implementations.</span></span> <span data-ttu-id="85582-109">Cílení na .NET Standard umožňuje vytvořit knihovny, které jsou omezené na používání rozhraní API, která jsou v dané verzi .NET Standard, což znamená, že je použitelná pro všechny platformy, které implementují tuto verzi .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="85582-109">Targeting .NET Standard lets you produce libraries that are constrained to use APIs that are in a given version of .NET Standard, which means it's usable by all platforms that implement that version of the .NET Standard.</span></span>

<span data-ttu-id="85582-110">![.NET Standard](./media/cross-platform-targeting/platforms-netstandard.png ".NET Standard")</span><span class="sxs-lookup"><span data-stu-id="85582-110">![.NET Standard](./media/cross-platform-targeting/platforms-netstandard.png ".NET Standard")</span></span>

<span data-ttu-id="85582-111">Při cílení .NET Standard a úspěšném kompilování projektu nezaručujeme, že se knihovna na všech platformách úspěšně spustí:</span><span class="sxs-lookup"><span data-stu-id="85582-111">Targeting .NET Standard, and successfully compiling your project, doesn't guarantee the library will run successfully on all platforms:</span></span>

1. <span data-ttu-id="85582-112">Rozhraní API specifická pro platformu se na jiných platformách nezdaří.</span><span class="sxs-lookup"><span data-stu-id="85582-112">Platform-specific APIs will fail on other platforms.</span></span> <span data-ttu-id="85582-113">Například <xref:Microsoft.Win32.Registry?displayProperty=nameWithType> bude ve Windows úspěšné a vyvolat <xref:System.PlatformNotSupportedException> při použití v jakémkoli jiném operačním systému.</span><span class="sxs-lookup"><span data-stu-id="85582-113">For example, <xref:Microsoft.Win32.Registry?displayProperty=nameWithType> will succeed on Windows and throw <xref:System.PlatformNotSupportedException> when used on any other OS.</span></span>
2. <span data-ttu-id="85582-114">Rozhraní API se můžou chovat jinak.</span><span class="sxs-lookup"><span data-stu-id="85582-114">APIs can behave differently.</span></span> <span data-ttu-id="85582-115">Například rozhraní API pro reflexi mají různé charakteristiky výkonu, když aplikace používá předdobu kompilace v systému iOS nebo UWP.</span><span class="sxs-lookup"><span data-stu-id="85582-115">For example, reflection APIs have different performance characteristics when an application uses ahead-of-time compilation on iOS or UWP.</span></span>

> [!TIP]
> <span data-ttu-id="85582-116">Tým .NET [nabízí nástroj Roslyn Analyzer](../analyzers/api-analyzer.md) , který vám umožní zjistit možné problémy.</span><span class="sxs-lookup"><span data-stu-id="85582-116">The .NET team [offers a Roslyn analyzer](../analyzers/api-analyzer.md) to help you discover possible issues.</span></span>

<span data-ttu-id="85582-117">✔️ začínat zahrnutím cíle `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="85582-117">✔️ DO start with including a `netstandard2.0` target.</span></span>

> <span data-ttu-id="85582-118">Většina knihoven pro obecné použití by neměla vyžadovat rozhraní API mimo .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="85582-118">Most general-purpose libraries should not need APIs outside of .NET Standard 2.0.</span></span> <span data-ttu-id="85582-119">.NET Standard 2,0 podporuje všechny moderní platformy a je doporučeným způsobem, jak podporovat více platforem s jedním cílem.</span><span class="sxs-lookup"><span data-stu-id="85582-119">.NET Standard 2.0 is supported by all modern platforms and is the recommended way to support multiple platforms with one target.</span></span>

<span data-ttu-id="85582-120">❌ se vyhnout zahrnutí cíle `netstandard1.x`.</span><span class="sxs-lookup"><span data-stu-id="85582-120">❌ AVOID including a `netstandard1.x` target.</span></span>

> <span data-ttu-id="85582-121">.NET Standard 1. x se distribuuje jako podrobná sada balíčků NuGet, která vytvoří graf závislostí balíčku a výsledkem je, že vývojáři stahují spoustu balíčků při sestavování.</span><span class="sxs-lookup"><span data-stu-id="85582-121">.NET Standard 1.x is distributed as a granular set of NuGet packages, which creates a large package dependency graph and results in developers downloading a lot of packages when building.</span></span> <span data-ttu-id="85582-122">Moderní platformy .NET, včetně .NET Framework 4.6.1, UWP a Xamarin, jsou všechny podpory .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="85582-122">Modern .NET platforms, including .NET Framework 4.6.1, UWP and Xamarin, all support .NET Standard 2.0.</span></span> <span data-ttu-id="85582-123">Pokud výslovně potřebujete cílit na starší platformu, měli byste cílit pouze na .NET Standard 1. x.</span><span class="sxs-lookup"><span data-stu-id="85582-123">You should only target .NET Standard 1.x if you specifically need to target an older platform.</span></span>

<span data-ttu-id="85582-124">✔️ zahrnout cíl `netstandard2.0`, pokud požadujete cíl `netstandard1.x`.</span><span class="sxs-lookup"><span data-stu-id="85582-124">✔️ DO include a `netstandard2.0` target if you require a `netstandard1.x` target.</span></span>

> <span data-ttu-id="85582-125">Na všech platformách, které podporují .NET Standard 2,0, se použije `netstandard2.0` cíl a bude výhodná mít menší graf balíčků, zatímco starší platformy budou pořád fungovat a budou se vracet k používání `netstandard1.x`ho cíle.</span><span class="sxs-lookup"><span data-stu-id="85582-125">All platforms supporting .NET Standard 2.0 will use the `netstandard2.0` target and benefit from having a smaller package graph while older platforms will still work and fall back to using the `netstandard1.x` target.</span></span>

<span data-ttu-id="85582-126">❌ neobsahují .NET Standard cíl, pokud knihovna spoléhá na model aplikace specifický pro platformu.</span><span class="sxs-lookup"><span data-stu-id="85582-126">❌ DO NOT include a .NET Standard target if the library relies on a platform-specific app model.</span></span>

> <span data-ttu-id="85582-127">Například knihovna Control Toolkit pro UWP závisí na modelu aplikace, který je k dispozici pouze pro UWP.</span><span class="sxs-lookup"><span data-stu-id="85582-127">For example, a UWP control toolkit library depends on an app model that is only available on UWP.</span></span> <span data-ttu-id="85582-128">Rozhraní API specifická pro model aplikace nebudou k dispozici v .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="85582-128">App model specific APIs will not be available in .NET Standard.</span></span>

## <a name="multi-targeting"></a><span data-ttu-id="85582-129">Cílení na více platforem</span><span class="sxs-lookup"><span data-stu-id="85582-129">Multi-targeting</span></span>

<span data-ttu-id="85582-130">Někdy potřebujete přístup k rozhraním API pro konkrétní rozhraní z vašich knihoven.</span><span class="sxs-lookup"><span data-stu-id="85582-130">Sometimes you need to access framework-specific APIs from your libraries.</span></span> <span data-ttu-id="85582-131">Nejlepším způsobem, jak volat rozhraní API specifická pro rozhraní, je použití cílení na více verzí, který sestaví projekt pro mnoho [cílových rozhraní .NET](../frameworks.md) , nikoli jenom pro jeden.</span><span class="sxs-lookup"><span data-stu-id="85582-131">The best way to call framework-specific APIs is using multi-targeting, which builds your project for many [.NET target frameworks](../frameworks.md) rather than for just one.</span></span>

<span data-ttu-id="85582-132">Pokud chcete, aby vaši spotřebitelé mohli sestavovat pro jednotlivé architektury, měli byste se snažit mít výstup .NET Standard a jeden nebo několik výstupů specifických pro rozhraní.</span><span class="sxs-lookup"><span data-stu-id="85582-132">To shield your consumers from having to build for individual frameworks, you should strive to have a .NET Standard output plus one or more framework-specific outputs.</span></span> <span data-ttu-id="85582-133">V případě cílení na více platforem jsou všechna sestavení zabalena do jednoho balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="85582-133">With multi-targeting, all assemblies are packaged inside a single NuGet package.</span></span> <span data-ttu-id="85582-134">Příjemci pak můžou odkazovat na stejný balíček a NuGet vybere příslušnou implementaci.</span><span class="sxs-lookup"><span data-stu-id="85582-134">Consumers can then reference the same package and NuGet will pick the appropriate implementation.</span></span> <span data-ttu-id="85582-135">Vaše knihovna .NET Standard slouží jako záložní knihovna, která se používá všude, s výjimkou případů, kdy váš balíček NuGet nabízí implementaci specifickou pro rozhraní.</span><span class="sxs-lookup"><span data-stu-id="85582-135">Your .NET Standard library serves as the fallback library that is used everywhere, except for the cases where your NuGet package offers a framework-specific implementation.</span></span> <span data-ttu-id="85582-136">Cílení na více platforem umožňuje použít podmíněnou kompilaci v kódu a volat rozhraní API specifická pro rozhraní.</span><span class="sxs-lookup"><span data-stu-id="85582-136">Multi-targeting allows you to use conditional compilation in your code and call framework-specific APIs.</span></span>

<span data-ttu-id="85582-137">![Balíček NuGet s více sestaveními](./media/cross-platform-targeting/nuget-package-multiple-assemblies.png "Balíček NuGet s více sestaveními")</span><span class="sxs-lookup"><span data-stu-id="85582-137">![NuGet package with multiple assemblies](./media/cross-platform-targeting/nuget-package-multiple-assemblies.png "NuGet package with multiple assemblies")</span></span>

<span data-ttu-id="85582-138">✔️ Zvažte kromě .NET Standard také cílení implementace rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="85582-138">✔️ CONSIDER targeting .NET implementations in addition to .NET Standard.</span></span>

> <span data-ttu-id="85582-139">Cílení implementace rozhraní .NET umožňuje volat rozhraní API specifická pro platformu, která jsou mimo .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="85582-139">Targeting .NET implementations allows you to call platform-specific APIs that are outside of .NET Standard.</span></span>
>
> <span data-ttu-id="85582-140">Pokud to uděláte, neprovádějte vyřazení podpory pro .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="85582-140">Do not drop support for .NET Standard when you do this.</span></span> <span data-ttu-id="85582-141">Místo toho vyvolejte z rozhraní API funkce implementace a nabídky.</span><span class="sxs-lookup"><span data-stu-id="85582-141">Instead, throw from the implementation and offer capability APIs.</span></span> <span data-ttu-id="85582-142">Tímto způsobem se vaše knihovna dá použít kdekoli a podporuje modul runtime s lehkými funkcemi.</span><span class="sxs-lookup"><span data-stu-id="85582-142">This way, your library can be used anywhere and supports runtime light-up of features.</span></span>

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

<span data-ttu-id="85582-143">Pokud je váš zdrojový kód pro všechny cíle stejný, ❌ se vyhnout cílení na více platforem a také cílení na .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="85582-143">❌ AVOID multi-targeting as well as targeting .NET Standard, if your source code is the same for all targets.</span></span>

> <span data-ttu-id="85582-144">Sestavení .NET Standard bude automaticky použito NuGet.</span><span class="sxs-lookup"><span data-stu-id="85582-144">The .NET Standard assembly will automatically be used by NuGet.</span></span> <span data-ttu-id="85582-145">Cílení na jednotlivé implementace rozhraní .NET zvyšuje `*.nupkg`ou velikost bez výhod.</span><span class="sxs-lookup"><span data-stu-id="85582-145">Targeting individual .NET implementations increases the `*.nupkg` size for no benefit.</span></span>

<span data-ttu-id="85582-146">✔️ Zvažte přidání cíle pro `net461`, když přidáváte `netstandard2.0` cíl.</span><span class="sxs-lookup"><span data-stu-id="85582-146">✔️ CONSIDER adding a target for `net461` when you're offering a `netstandard2.0` target.</span></span>

> <span data-ttu-id="85582-147">Použití .NET Standard 2,0 z .NET Framework obsahuje některé problémy, které byly vyřešeny v .NET Framework 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="85582-147">Using .NET Standard 2.0 from .NET Framework has some issues that were addressed in .NET Framework 4.7.2.</span></span> <span data-ttu-id="85582-148">Můžete vylepšit prostředí pro vývojáře, kteří jsou pořád na .NET Framework 4.6.1-4.7.1, a nabízet jim binární soubor, který je sestavený pro .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="85582-148">You can improve the experience for developers that are still on .NET Framework 4.6.1 - 4.7.1 by offering them a binary that is built for .NET Framework 4.6.1.</span></span>

<span data-ttu-id="85582-149">✔️ k distribuci knihovny pomocí balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="85582-149">✔️ DO distribute your library using a NuGet package.</span></span>

> <span data-ttu-id="85582-150">NuGet vybere nejlepší cíl pro vývojáře a chrání je před tím, než bude muset vybrat příslušnou implementaci.</span><span class="sxs-lookup"><span data-stu-id="85582-150">NuGet will select the best target for the developer and shield them having to pick the appropriate implementation.</span></span>

<span data-ttu-id="85582-151">✔️ použít vlastnost `TargetFrameworks` souboru projektu při cílení na více platforem.</span><span class="sxs-lookup"><span data-stu-id="85582-151">✔️ DO use a project file's `TargetFrameworks` property when multi-targeting.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <!-- This project will output netstandard2.0 and net461 assemblies -->
    <TargetFrameworks>netstandard2.0;net461</TargetFrameworks>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="85582-152">✔️ Zvažte použití nástroje [MSBuild. SDK. Extras](https://github.com/onovotny/MSBuildSdkExtras) při cílení na více platforem pro UWP a Xamarin, protože značně zjednodušuje váš soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="85582-152">✔️ CONSIDER using [MSBuild.Sdk.Extras](https://github.com/onovotny/MSBuildSdkExtras) when multi-targeting for UWP and Xamarin as it greatly simplifies your project file.</span></span>

## <a name="older-targets"></a><span data-ttu-id="85582-153">Starší cíle</span><span class="sxs-lookup"><span data-stu-id="85582-153">Older targets</span></span>

<span data-ttu-id="85582-154">Rozhraní .NET podporuje cílení na verze .NET Framework, které nejsou podporované, i platformy, které se už běžně nepoužívají.</span><span class="sxs-lookup"><span data-stu-id="85582-154">.NET supports targeting versions of the .NET Framework that are long out of support as well as platforms that are no longer commonly used.</span></span> <span data-ttu-id="85582-155">I když existuje hodnota, aby vaše knihovna fungovala s co možná nejvíce cíli, může dopracovat s chybějícími rozhraními API a zvýšit tak značnou režii.</span><span class="sxs-lookup"><span data-stu-id="85582-155">While there's value in making your library work on as many targets as possible, having to work around missing APIs can add significant overhead.</span></span> <span data-ttu-id="85582-156">Domníváme se, že některá rozhraní už necílí na cílení a berou v úvahách jejich dosah a omezení.</span><span class="sxs-lookup"><span data-stu-id="85582-156">We believe certain frameworks are no longer worth targeting, considering their reach and limitations.</span></span>

<span data-ttu-id="85582-157">❌ neobsahují cíl knihovny přenosných tříd (PCL).</span><span class="sxs-lookup"><span data-stu-id="85582-157">❌ DO NOT include a Portable Class Library (PCL) target.</span></span> <span data-ttu-id="85582-158">například `portable-net45+win8+wpa81+wp8`.</span><span class="sxs-lookup"><span data-stu-id="85582-158">For example, `portable-net45+win8+wpa81+wp8`.</span></span>

> <span data-ttu-id="85582-159">.NET Standard je moderní způsob, jak podporovat knihovny .NET pro různé platformy a nahrazuje PCLs.</span><span class="sxs-lookup"><span data-stu-id="85582-159">.NET Standard is the modern way to support cross-platform .NET libraries and replaces PCLs.</span></span>

<span data-ttu-id="85582-160">❌ nezahrnují cíle pro platformy .NET, které už nejsou podporované.</span><span class="sxs-lookup"><span data-stu-id="85582-160">❌ DO NOT include targets for .NET platforms that are no longer supported.</span></span> <span data-ttu-id="85582-161">Například `SL4``WP`.</span><span class="sxs-lookup"><span data-stu-id="85582-161">For example, `SL4`, `WP`.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="85582-162">[Předchozí](get-started.md)
>[Další](strong-naming.md)</span><span class="sxs-lookup"><span data-stu-id="85582-162">[Previous](get-started.md)
[Next](strong-naming.md)</span></span>
