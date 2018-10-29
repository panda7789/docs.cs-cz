---
title: Cílení na více platforem
description: Doporučené osvědčené postupy pro vytváření knihovny pro různé platformy .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 72fa891d5b1054af485a98d89b4efb11d6b0018b
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50202813"
---
# <a name="cross-platform-targeting"></a><span data-ttu-id="530b9-103">Cílení na více platforem</span><span class="sxs-lookup"><span data-stu-id="530b9-103">Cross-platform targeting</span></span>

<span data-ttu-id="530b9-104">Moderní .NET podporuje několik operačních systémů a zařízení.</span><span class="sxs-lookup"><span data-stu-id="530b9-104">Modern .NET supports multiple operating systems and devices.</span></span> <span data-ttu-id="530b9-105">Je důležité pro open source knihovny .NET pro podporu tolik vývojáři co nejvíce, zda že sestavujete Web ASP.NET hostovaný v Azure nebo rozhraní .NET hry v Unity.</span><span class="sxs-lookup"><span data-stu-id="530b9-105">It's important for .NET open-source libraries to support as many developers as possible, whether they're building an ASP.NET website hosted in Azure, or a .NET game in Unity.</span></span>

## <a name="net-standard"></a><span data-ttu-id="530b9-106">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="530b9-106">.NET Standard</span></span>

<span data-ttu-id="530b9-107">.NET standard je nejlepší způsob, jak přidat podporu pro různé platformy do knihovny .NET.</span><span class="sxs-lookup"><span data-stu-id="530b9-107">.NET Standard is the best way to add cross-platform support to a .NET library.</span></span> <span data-ttu-id="530b9-108">[.NET standard](../net-standard.md) je specifikace rozhraní API .NET, která jsou k dispozici na všech implementace .NET.</span><span class="sxs-lookup"><span data-stu-id="530b9-108">[.NET Standard](../net-standard.md) is a specification of .NET APIs that are available on all .NET implementations.</span></span> <span data-ttu-id="530b9-109">Cílení na .NET Standard umožňuje vytvořit knihovny, které jsou omezeny na použití rozhraní API, která jsou v dané verzi rozhraní .NET Standard, což znamená, že je možné ji použít ve všech platformách, které implementují verzi .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="530b9-109">Targeting .NET Standard lets you produce libraries that are constrained to use APIs that are in a given version of .NET Standard, which means it's usable by all platforms that implement that version of the .NET Standard.</span></span>

<span data-ttu-id="530b9-110">![.NET standard](./media/cross-platform-targeting/platforms-netstandard.png ".NET Standard")</span><span class="sxs-lookup"><span data-stu-id="530b9-110">![.NET Standard](./media/cross-platform-targeting/platforms-netstandard.png ".NET Standard")</span></span>

<span data-ttu-id="530b9-111">Cílení na .NET Standard a úspěšně kompilace projektu nezaručuje, že knihovny úspěšně poběží na všech platformách:</span><span class="sxs-lookup"><span data-stu-id="530b9-111">Targeting .NET Standard, and successfully compiling your project, doesn't guarantee the library will run successfully on all platforms:</span></span>

1. <span data-ttu-id="530b9-112">Rozhraní API pro konkrétní platformu selže na jiných platformách.</span><span class="sxs-lookup"><span data-stu-id="530b9-112">Platform-specific APIs will fail on other platforms.</span></span> <span data-ttu-id="530b9-113">Například <xref:Microsoft.Win32.Registry?displayProperty=nameWithType> úspěšná na Windows, který se vyvolat <xref:System.PlatformNotSupportedException> při použití na jiných operačních systémech.</span><span class="sxs-lookup"><span data-stu-id="530b9-113">For example, <xref:Microsoft.Win32.Registry?displayProperty=nameWithType> will succeed on Windows and throw <xref:System.PlatformNotSupportedException> when used on any other OS.</span></span>
2. <span data-ttu-id="530b9-114">Rozhraní API se může chovat jinak.</span><span class="sxs-lookup"><span data-stu-id="530b9-114">APIs can behave differently.</span></span> <span data-ttu-id="530b9-115">Například reflexe rozhraní API mají jiné výkonové charakteristiky když aplikace využívá ahead of time kompilace v Iosu nebo UWP.</span><span class="sxs-lookup"><span data-stu-id="530b9-115">For example, reflection APIs have different performance characteristics when an application uses ahead-of-time compilation on iOS or UWP.</span></span>

> [!TIP]
> <span data-ttu-id="530b9-116">Tým .NET [nabízí Roslyn analyzátor](../analyzers/api-analyzer.md) vám pomůžou zjistit informace o možných problémech.</span><span class="sxs-lookup"><span data-stu-id="530b9-116">The .NET team [offers a Roslyn analyzer](../analyzers/api-analyzer.md) to help you discover possible issues.</span></span>

<span data-ttu-id="530b9-117">**PROVEĎTE ✔️** začínat včetně `netstandard2.0` cíl.</span><span class="sxs-lookup"><span data-stu-id="530b9-117">**✔️ DO** start with including a `netstandard2.0` target.</span></span>

> <span data-ttu-id="530b9-118">Většina pro obecné účely knihovny by neměl musí rozhraní API mimo rozhraní .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="530b9-118">Most general-purpose libraries should not need APIs outside of .NET Standard 2.0.</span></span> <span data-ttu-id="530b9-119">Rozhraní .NET standard 2.0 podporuje všechny moderní platformy a je doporučován k podporování více platforem s jedním cílem.</span><span class="sxs-lookup"><span data-stu-id="530b9-119">.NET Standard 2.0 is supported by all modern platforms and is the recommended way to support multiple platforms with one target.</span></span>

<span data-ttu-id="530b9-120">**❌ Nepoužívejte** včetně `netstandard1.x` cíl.</span><span class="sxs-lookup"><span data-stu-id="530b9-120">**❌ AVOID** including a `netstandard1.x` target.</span></span>

> <span data-ttu-id="530b9-121">.NET standard 1.x je distribuován jako podrobné sadu balíčků NuGet, které vytvoří graf závislosti velký balíček, jejichž výsledkem vývojáři stahuje velké balíčky se při sestavování.</span><span class="sxs-lookup"><span data-stu-id="530b9-121">.NET Standard 1.x is distributed as a granular set of NuGet packages, which creates a large package dependency graph and results in developers downloading a lot of packages when building.</span></span> <span data-ttu-id="530b9-122">Moderní platformy .NET, včetně rozhraní .NET Framework 4.6.1, UPW a Xamarin, všechny podporují .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="530b9-122">Modern .NET platforms, including .NET Framework 4.6.1, UWP and Xamarin, all support .NET Standard 2.0.</span></span> <span data-ttu-id="530b9-123">By měla pouze cílíte .NET Standard 1.x, pokud je výslovně potřeba cílit na starší platformy.</span><span class="sxs-lookup"><span data-stu-id="530b9-123">You should only target .NET Standard 1.x if you specifically need to target an older platform.</span></span>

<span data-ttu-id="530b9-124">**✔️ PROVEĎTE** zahrnout `netstandard2.0` cílit, pokud budete potřebovat `netstandard1.x` cíl.</span><span class="sxs-lookup"><span data-stu-id="530b9-124">**✔️ DO** include a `netstandard2.0` target if you require a `netstandard1.x` target.</span></span>

> <span data-ttu-id="530b9-125">Budou používat všechny platformy podporuje .NET Standard 2.0 `netstandard2.0` cíl a těžit z s menší graf balíčku, zatímco starší platformy i nadále fungovat a vrátí k používání `netstandard1.x` cíl.</span><span class="sxs-lookup"><span data-stu-id="530b9-125">All platforms supporting .NET Standard 2.0 will use the `netstandard2.0` target and benefit from having a smaller package graph while older platforms will still work and fall back to using the `netstandard1.x` target.</span></span>

<span data-ttu-id="530b9-126">**❌ NEPODPORUJÍ** zahrnout .NET Standard cíl, pokud knihovny závisí na modelu aplikací pro konkrétní platformu.</span><span class="sxs-lookup"><span data-stu-id="530b9-126">**❌ DO NOT** include a .NET Standard target if the library relies on a platform-specific app model.</span></span>

> <span data-ttu-id="530b9-127">Například sada nástrojů knihovny ovládacích prvků UPW závisí na modelu aplikace, která je dostupná pouze na UPW.</span><span class="sxs-lookup"><span data-stu-id="530b9-127">For example, a UWP control toolkit library depends on an app model that is only available on UWP.</span></span> <span data-ttu-id="530b9-128">Konkrétní aplikace modelu rozhraní API není k dispozici v .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="530b9-128">App model specific APIs will not be available in .NET Standard.</span></span>

## <a name="multi-targeting"></a><span data-ttu-id="530b9-129">Cílení na více platforem</span><span class="sxs-lookup"><span data-stu-id="530b9-129">Multi-targeting</span></span>

<span data-ttu-id="530b9-130">Někdy potřebujete přístup k rozhraním API pro konkrétní rozhraní z knihovny.</span><span class="sxs-lookup"><span data-stu-id="530b9-130">Sometimes you need to access framework-specific APIs from your libraries.</span></span> <span data-ttu-id="530b9-131">Nejlepší způsob, jak volat rozhraní API pro konkrétní rozhraní používá, cílení na více platforem, který sestaví váš projekt pro mnoho [cílové rozhraní .NET](../frameworks.md) , a nikoli pro jen jeden.</span><span class="sxs-lookup"><span data-stu-id="530b9-131">The best way to call framework-specific APIs is using multi-targeting, which builds your project for many [.NET target frameworks](../frameworks.md) rather than for just one.</span></span>

<span data-ttu-id="530b9-132">K ochraně zákazníci nebudou muset sestavení pro jednotlivá rozhraní, je nutné snažit se mít .NET standardní výstup a jeden nebo více výstupů specifické pro architekturu.</span><span class="sxs-lookup"><span data-stu-id="530b9-132">To shield your consumers from having to build for individual frameworks, you should strive to have a .NET Standard output plus one or more framework-specific outputs.</span></span> <span data-ttu-id="530b9-133">Pomocí cílení na více platforem jsou sbaleny všechna sestavení v jediném balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="530b9-133">With multi-targeting, all assemblies are packaged inside a single NuGet package.</span></span> <span data-ttu-id="530b9-134">Uživatele můžete odkázat na stejném balíčku a NuGet, vybere vhodné implementaci.</span><span class="sxs-lookup"><span data-stu-id="530b9-134">Consumers can then reference the same package and NuGet will pick the appropriate implementation.</span></span> <span data-ttu-id="530b9-135">Knihovny .NET Standard slouží jako záložní knihovna, která je použít všude, s výjimkou případů, kdy svůj balíček NuGet nabízí implementace specifické pro architekturu.</span><span class="sxs-lookup"><span data-stu-id="530b9-135">Your .NET Standard library serves as the fallback library that is used everywhere, except for the cases where your NuGet package offers a framework-specific implementation.</span></span> <span data-ttu-id="530b9-136">Cílení na více platforem vám umožňuje používat podmíněnou kompilaci ve vašem kódu a volání rozhraní API pro konkrétní rozhraní.</span><span class="sxs-lookup"><span data-stu-id="530b9-136">Multi-targeting allows you to use conditional compilation in your code and call framework-specific APIs.</span></span>

<span data-ttu-id="530b9-137">![Balíček NuGet s více sestavení](./media/cross-platform-targeting/nuget-package-multiple-assemblies.png "balíček NuGet s více sestavení")</span><span class="sxs-lookup"><span data-stu-id="530b9-137">![NuGet package with multiple assemblies](./media/cross-platform-targeting/nuget-package-multiple-assemblies.png "NuGet package with multiple assemblies")</span></span>

<span data-ttu-id="530b9-138">**✔️ ZVAŽTE** cílí na .NET implementace kromě .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="530b9-138">**✔️ CONSIDER** targeting .NET implementations in addition to .NET Standard.</span></span>

> <span data-ttu-id="530b9-139">Cílení na implementace .NET umožňuje volat rozhraní API pro konkrétní platformu, která se nachází mimo .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="530b9-139">Targeting .NET implementations allows you to call platform-specific APIs that are outside of .NET Standard.</span></span>
>
> <span data-ttu-id="530b9-140">Když toto provedete, neuvolňují podpora pro .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="530b9-140">Do not drop support for .NET Standard when you do this.</span></span> <span data-ttu-id="530b9-141">Místo toho vyvolat od implementace rozhraní a nabízejí funkce rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="530b9-141">Instead, throw from the implementation and offer capability APIs.</span></span> <span data-ttu-id="530b9-142">Tímto způsobem své knihovny lze je použít kdekoli a podporuje runtime světla shrnutí těchto funkcí.</span><span class="sxs-lookup"><span data-stu-id="530b9-142">This way, your library can be used anywhere and supports runtime light-up of features.</span></span>

<span data-ttu-id="530b9-143">**❌ Nepoužívejte** pomocí cílení na více platforem pomocí .NET Standard, pokud se zdrojový kód je stejný pro všechny cíle.</span><span class="sxs-lookup"><span data-stu-id="530b9-143">**❌ AVOID** using multi-targeting with .NET Standard if your source code is the same for all targets.</span></span>

> <span data-ttu-id="530b9-144">.NET Standard sestavení se automaticky použije balíčkem NuGet.</span><span class="sxs-lookup"><span data-stu-id="530b9-144">The .NET Standard assembly will automatically be used by NuGet.</span></span> <span data-ttu-id="530b9-145">Cílení na jednotlivé implementace .NET zvýší `*.nupkg` velikost bez jakékoli výhody.</span><span class="sxs-lookup"><span data-stu-id="530b9-145">Targeting individual .NET implementations increases the `*.nupkg` size for no benefit.</span></span>

<span data-ttu-id="530b9-146">**✔️ ZVAŽTE** přidání cíle `net461` Pokud nabízíte `netstandard2.0` cíl.</span><span class="sxs-lookup"><span data-stu-id="530b9-146">**✔️ CONSIDER** adding a target for `net461` when you're offering a `netstandard2.0` target.</span></span> 

> <span data-ttu-id="530b9-147">Použití .NET Standard 2.0 z rozhraní .NET Framework má některé problémy, které se zákazníky a vyřešené v rozhraní .NET Framework 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="530b9-147">Using .NET Standard 2.0 from .NET Framework has some issues that were addressed in .NET Framework 4.7.2.</span></span> <span data-ttu-id="530b9-148">Můžete vylepšit prostředí pro vývojáře, které jsou stále v rozhraní .NET Framework 4.6.1 – 4.7.1 nabídkou binární soubor, který je sestaven pro rozhraní .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="530b9-148">You can improve the experience for developers that are still on .NET Framework 4.6.1 - 4.7.1 by offering them a binary that is built for .NET Framework 4.6.1.</span></span>

<span data-ttu-id="530b9-149">**PROVEĎTE ✔️** distribuovat knihovny pomocí balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="530b9-149">**✔️ DO** distribute your library using a NuGet package.</span></span>

> <span data-ttu-id="530b9-150">NuGet vybere nejlepší cíl pro vývojáře a stínit museli výběr vhodné implementaci.</span><span class="sxs-lookup"><span data-stu-id="530b9-150">NuGet will select the best target for the developer and shield them having to pick the appropriate implementation.</span></span>

<span data-ttu-id="530b9-151">**PROVEĎTE ✔️** pomocí souboru projektu `TargetFrameworks` při cílení na více platforem.</span><span class="sxs-lookup"><span data-stu-id="530b9-151">**✔️ DO** use a project file's `TargetFrameworks` property when multi-targeting.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <!-- This project will output netstandard2.0 and net461 assemblies -->
    <TargetFrameworks>netstandard2.0;net461</TargetFrameworks>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="530b9-152">**✔️ ZVAŽTE** pomocí [MSBuild.Sdk.Extras](https://github.com/onovotny/MSBuildSdkExtras) při cílení na více platforem pro UPW a Xamarin jako výrazně zjednodušuje váš soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="530b9-152">**✔️ CONSIDER** using [MSBuild.Sdk.Extras](https://github.com/onovotny/MSBuildSdkExtras) when multi-targeting for UWP and Xamarin as it greatly simplifies your project file.</span></span>

## <a name="older-targets"></a><span data-ttu-id="530b9-153">Starší cíle</span><span class="sxs-lookup"><span data-stu-id="530b9-153">Older targets</span></span>

<span data-ttu-id="530b9-154">.NET podporuje cílení verze rozhraní .NET Framework, které jsou dlouhé mimo podporu, jakož i platformy, které se už běžně používají.</span><span class="sxs-lookup"><span data-stu-id="530b9-154">.NET supports targeting versions of the .NET Framework that are long out of support as well as platforms that are no longer commonly used.</span></span> <span data-ttu-id="530b9-155">Pokud hodnota při vytvoření knihovny práce na mnoho cíle jako je to možné, museli obejít chybí rozhraní API můžete přidávat významné režie.</span><span class="sxs-lookup"><span data-stu-id="530b9-155">While there's value in making your library work on as many targets as possible, having to work around missing APIs can add significant overhead.</span></span> <span data-ttu-id="530b9-156">Jsme přesvědčeni jisti, že rozhraní stojí za to už cílení, zvažujete jeho dosah a omezení.</span><span class="sxs-lookup"><span data-stu-id="530b9-156">We believe certain frameworks are no longer worth targeting, considering their reach and limitations.</span></span>

<span data-ttu-id="530b9-157">**❌ NEPODPORUJÍ** zahrnout cíl Přenosná knihovna tříd (PCL).</span><span class="sxs-lookup"><span data-stu-id="530b9-157">**❌ DO NOT** include a Portable Class Library (PCL) target.</span></span> <span data-ttu-id="530b9-158">Například `portable-net45+win8+wpa81+wp8`.</span><span class="sxs-lookup"><span data-stu-id="530b9-158">For example, `portable-net45+win8+wpa81+wp8`.</span></span>

> <span data-ttu-id="530b9-159">.NET standard je moderní způsob, jak podpora knihovny pro různé platformy .NET a nahradí PCLs.</span><span class="sxs-lookup"><span data-stu-id="530b9-159">.NET Standard is the modern way to support cross-platform .NET libraries and replaces PCLs.</span></span>

<span data-ttu-id="530b9-160">**❌ NEPODPORUJÍ** obsahovat cílové hodnoty pro platformy .NET, které již nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="530b9-160">**❌ DO NOT** include targets for .NET platforms that are no longer supported.</span></span> <span data-ttu-id="530b9-161">Například `SL4`, `WP`.</span><span class="sxs-lookup"><span data-stu-id="530b9-161">For example, `SL4`, `WP`.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="530b9-162">[Předchozí](./get-started.md)
[další](./strong-naming.md)</span><span class="sxs-lookup"><span data-stu-id="530b9-162">[Previous](./get-started.md)
[Next](./strong-naming.md)</span></span>
