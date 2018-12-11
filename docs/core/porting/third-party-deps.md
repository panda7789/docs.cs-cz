---
title: Analýza závislosti port kódu až po .NET Core
description: Zjistěte, jak analyzovat externích závislostí k portu projektu z rozhraní .NET Framework do .NET Core.
author: cartermp
ms.date: 12/04/2018
ms.custom: seodec18
ms.openlocfilehash: dce8e6cd4986b15cf926154b378964db4beef398
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170314"
---
# <a name="analyze-your-dependencies-to-port-code-to-net-core"></a><span data-ttu-id="74fba-103">Analýza závislostí do portu kódu až po .NET Core</span><span class="sxs-lookup"><span data-stu-id="74fba-103">Analyze your dependencies to port code to .NET Core</span></span>

<span data-ttu-id="74fba-104">K portu kódu .NET Core nebo .NET Standard, je třeba porozumět závislostí.</span><span class="sxs-lookup"><span data-stu-id="74fba-104">To port your code to .NET Core or .NET Standard, you must understand your dependencies.</span></span> <span data-ttu-id="74fba-105">Externí závislosti jsou [balíčky NuGet](#analyze-referenced-nuget-packages-on-your-project) nebo [knihovny DLL](#analyze-dependencies-that-arent-nuget-packages) odkazovat ve vašem projektu, ale není sestavení.</span><span class="sxs-lookup"><span data-stu-id="74fba-105">External dependencies are the [NuGet packages](#analyze-referenced-nuget-packages-on-your-project) or [DLLs](#analyze-dependencies-that-arent-nuget-packages) you reference in your project, but that you don't build.</span></span> <span data-ttu-id="74fba-106">Vyhodnotit každý závislosti a vytvořte plán řešení nepředvídaných událostí pro ty, které nejsou kompatibilní s .NET Core.</span><span class="sxs-lookup"><span data-stu-id="74fba-106">Evaluate each dependency and develop a contingency plan for the ones that aren't compatible with .NET Core.</span></span> <span data-ttu-id="74fba-107">Tady je postup, chcete-li zjistit, zda závislost je kompatibilní s .NET Core.</span><span class="sxs-lookup"><span data-stu-id="74fba-107">Here's how to determine if a dependency is compatible with .NET Core.</span></span>

## <a name="analyze-referenced-nuget-packages-in-your-projects"></a><span data-ttu-id="74fba-108">Analýza odkazované balíčky NuGet ve vašich projektech</span><span class="sxs-lookup"><span data-stu-id="74fba-108">Analyze referenced NuGet packages in your projects</span></span>

<span data-ttu-id="74fba-109">Pokud odkazujete na balíčky NuGet ve vašem projektu, musíte ověřit, pokud jsou kompatibilní s .NET Core.</span><span class="sxs-lookup"><span data-stu-id="74fba-109">If you reference NuGet packages in your project, you need to verify if they're compatible with .NET Core.</span></span>
<span data-ttu-id="74fba-110">Existují dva způsoby, jak to udělat:</span><span class="sxs-lookup"><span data-stu-id="74fba-110">There are two ways to accomplish that:</span></span>

* [<span data-ttu-id="74fba-111">Pomocí balíčku NuGet aplikaci Průzkumník balení</span><span class="sxs-lookup"><span data-stu-id="74fba-111">Using the NuGet Package Explorer app</span></span>](#analyze-nuget-packages-using-nuget-package-explorer)
* [<span data-ttu-id="74fba-112">Použití webu nuget.org</span><span class="sxs-lookup"><span data-stu-id="74fba-112">Using the nuget.org site</span></span>](#analyze-nuget-packages-using-nugetorg)

<span data-ttu-id="74fba-113">Po analýze balíčků, pokud nejsou kompatibilní s .NET Core a pouze cílové rozhraní .NET Framework, můžete zkontrolovat Pokud [režim kompatibility rozhraní .NET Framework](#net-framework-compatibility-mode) pomáhá s přenosem procesem.</span><span class="sxs-lookup"><span data-stu-id="74fba-113">After analyzing the packages, if they're not compatible with .NET Core and only target .NET Framework, you can check if the [.NET Framework compatibility mode](#net-framework-compatibility-mode) can help with your porting process.</span></span>

### <a name="analyze-nuget-packages-using-nuget-package-explorer"></a><span data-ttu-id="74fba-114">Analýza balíčků NuGet pomocí Průzkumníku balíčků NuGet</span><span class="sxs-lookup"><span data-stu-id="74fba-114">Analyze NuGet packages using NuGet Package Explorer</span></span>

<span data-ttu-id="74fba-115">Balíček NuGet je sám sadu složek, které obsahují specifické pro platformu sestavení.</span><span class="sxs-lookup"><span data-stu-id="74fba-115">A NuGet package is itself a set of folders that contain platform-specific assemblies.</span></span> <span data-ttu-id="74fba-116">Proto je potřeba zkontrolovat, zda je složka, která obsahuje sestavení s kompatibilní uvnitř balíčku.</span><span class="sxs-lookup"><span data-stu-id="74fba-116">So you need to check if there's a folder that contains a compatible assembly inside the package.</span></span>

<span data-ttu-id="74fba-117">Nejjednodušší způsob, jak kontrolovat složky balíčku NuGet je použít [NuGet – Průzkumník balíčků](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) nástroj.</span><span class="sxs-lookup"><span data-stu-id="74fba-117">The easiest way to inspect NuGet Package folders is to use the [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) tool.</span></span> <span data-ttu-id="74fba-118">Po instalaci, postupujte následovně Chcete-li zobrazit názvy složek:</span><span class="sxs-lookup"><span data-stu-id="74fba-118">After installing it, use the following steps to see the folder names:</span></span>

1. <span data-ttu-id="74fba-119">Otevřete v Průzkumníku balíčků NuGet.</span><span class="sxs-lookup"><span data-stu-id="74fba-119">Open the NuGet Package Explorer.</span></span>
2. <span data-ttu-id="74fba-120">Klikněte na tlačítko **otevřít balíček z online datového kanálu**.</span><span class="sxs-lookup"><span data-stu-id="74fba-120">Click **Open package from online feed**.</span></span>
3. <span data-ttu-id="74fba-121">Vyhledejte název balíčku.</span><span class="sxs-lookup"><span data-stu-id="74fba-121">Search for the name of the package.</span></span>
4. <span data-ttu-id="74fba-122">Ve výsledcích hledání vyberte název balíčku a klikněte na tlačítko **otevřete**.</span><span class="sxs-lookup"><span data-stu-id="74fba-122">Select the package name from the search results and click **open**.</span></span>
5. <span data-ttu-id="74fba-123">Rozbalte *lib* složky na pravé straně a podívejte se na názvy složek.</span><span class="sxs-lookup"><span data-stu-id="74fba-123">Expand the *lib* folder on the right-hand side and look at folder names.</span></span>

<span data-ttu-id="74fba-124">Vyhledejte složku s žádným z následujících názvů:</span><span class="sxs-lookup"><span data-stu-id="74fba-124">Look for a folder with any of the following names:</span></span>

```
netstandard1.0
netstandard1.1
netstandard1.2
netstandard1.3
netstandard1.4
netstandard1.5
netstandard1.6
netstandard2.0
netcoreapp1.0
netcoreapp1.1
netcoreapp2.0
netcoreapp2.1
netcoreapp2.2
portable-net45-win8
portable-win8-wpa8
portable-net451-win81
portable-net45-win8-wpa8-wpa81
```

<span data-ttu-id="74fba-125">Tyto hodnoty jsou [Monikery cílového rozhraní (Tfm)](../../standard/frameworks.md) , která mapují na verzích [.NET Standard](../../standard/net-standard.md), .NET Core a tradiční profily Přenosná knihovna tříd (PCL), které jsou kompatibilní s .NET Core.</span><span class="sxs-lookup"><span data-stu-id="74fba-125">These values are the [Target Framework Monikers (TFMs)](../../standard/frameworks.md) that map to versions of the [.NET Standard](../../standard/net-standard.md), .NET Core, and traditional Portable Class Library (PCL) profiles that are compatible with .NET Core.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="74fba-126">Při prohlížení Tfm, které podporuje balíčku, Všimněte si, že `netcoreapp*`, zatímco kompatibilní, je pro projekty .NET Core pouze a ne pro projekty .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="74fba-126">When looking at the TFMs that a package supports, note that `netcoreapp*`, while compatible, is for .NET Core projects only and not for .NET Standard projects.</span></span>
> <span data-ttu-id="74fba-127">Knihovnu, která se zaměřuje pouze `netcoreapp*` a ne `netstandard*` může používat jenom jiné aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="74fba-127">A library that only targets `netcoreapp*` and not `netstandard*` can only be consumed by other .NET Core apps.</span></span>

### <a name="analyze-nuget-packages-using-nugetorg"></a><span data-ttu-id="74fba-128">Analýza balíčků NuGet pomocí nuget.org</span><span class="sxs-lookup"><span data-stu-id="74fba-128">Analyze NuGet packages using nuget.org</span></span>

<span data-ttu-id="74fba-129">Alternativně můžete zobrazit Tfm, které podporuje každý balíček na [nuget.org](https://www.nuget.org/) pod **závislosti** na stránce balíček.</span><span class="sxs-lookup"><span data-stu-id="74fba-129">Alternatively, you can see the TFMs that each package supports on [nuget.org](https://www.nuget.org/) under the **Dependencies** section of the package page.</span></span>

<span data-ttu-id="74fba-130">Ačkoli použití webu je jednodušší způsob ověření kompatibility, **závislosti** informace nejsou k dispozici na webu pro všechny balíčky.</span><span class="sxs-lookup"><span data-stu-id="74fba-130">Although using the site is an easier method to verify the compatibility, **Dependencies** information is not available on the site for all packages.</span></span>

### <a name="net-framework-compatibility-mode"></a><span data-ttu-id="74fba-131">Režim kompatibility rozhraní .NET framework</span><span class="sxs-lookup"><span data-stu-id="74fba-131">.NET Framework compatibility mode</span></span>

<span data-ttu-id="74fba-132">Po analýze balíčky NuGet, můžete zjistit, že pouze cílí na rozhraní .NET Framework, stejně jako většinu balíčků NuGet.</span><span class="sxs-lookup"><span data-stu-id="74fba-132">After analyzing the NuGet packages, you might find that they only target the .NET Framework, as most NuGet packages do.</span></span>

<span data-ttu-id="74fba-133">Počínaje rozhraním .NET Standard 2.0, byla zavedena režimu kompatibility rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="74fba-133">Starting with .NET Standard 2.0, the .NET Framework compatibility mode was introduced.</span></span> <span data-ttu-id="74fba-134">Tento režim kompatibility umožňuje odkazovat na knihovny rozhraní .NET Framework projekty .NET Standard a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="74fba-134">This compatibility mode allows .NET Standard and .NET Core projects to reference .NET Framework libraries.</span></span> <span data-ttu-id="74fba-135">Odkazování na knihovny rozhraní .NET Framework nefunguje pro všechny projekty, třeba když knihovny používá Windows Presentation Foundation (WPF) rozhraní API, ale jeho odblokovat mnoho scénářů přenosem.</span><span class="sxs-lookup"><span data-stu-id="74fba-135">Referencing .NET Framework libraries doesn't work for all projects, such as if the library uses Windows Presentation Foundation (WPF) APIs, but it does unblock many porting scenarios.</span></span>

<span data-ttu-id="74fba-136">Při odkazu na balíčky NuGet, které se zaměřují rozhraní .NET Framework ve vašem projektu, například [Huitian.PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections), zobrazí upozornění záložní balíčku ([NU1701](/nuget/reference/errors-and-warnings#nu1701)) podobně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="74fba-136">When you reference NuGet packages that target the .NET Framework in your project, such as [Huitian.PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections), you get a package fallback warning ([NU1701](/nuget/reference/errors-and-warnings#nu1701)) similar to the following example:</span></span>

`NU1701: Package ‘Huitian.PowerCollections 1.0.0’ was restored using ‘.NETFramework,Version=v4.6.1’ instead of the project target framework ‘.NETStandard,Version=v2.0’. This package may not be fully compatible with your project.`

<span data-ttu-id="74fba-137">Že upozornění se zobrazí, když přidáte balíček a pokaždé, když vytváříte Ujistěte se, že při testování s využitím projektu daného balíčku.</span><span class="sxs-lookup"><span data-stu-id="74fba-137">That warning is displayed when you add the package and every time you build to make sure you test that package with your project.</span></span> <span data-ttu-id="74fba-138">Pokud váš projekt pracuje podle očekávání, můžete potlačit tohoto upozornění úpravou vlastnosti balíčku v sadě Visual Studio nebo ruční úpravou souboru projektu v váš oblíbený editor kódu.</span><span class="sxs-lookup"><span data-stu-id="74fba-138">If your project is working as expected, you can suppress that warning by editing the package properties in Visual Studio or by manually editing the project file in your favorite code editor.</span></span>

<span data-ttu-id="74fba-139">Chcete-li potlačit upozornění úpravou souboru projektu, vyhledejte `PackageReference` položky balíčku, kterou chcete potlačit upozornění pro a přidat `NoWarn` atribut.</span><span class="sxs-lookup"><span data-stu-id="74fba-139">To suppress the warning by editing the project file, find the `PackageReference` entry for the package you want to suppress the warning for and add the `NoWarn` attribute.</span></span> <span data-ttu-id="74fba-140">`NoWarn` Atribut přijímá čárkami oddělený seznam všech upozornění ID.</span><span class="sxs-lookup"><span data-stu-id="74fba-140">The `NoWarn` attribute accepts a comma-separated list of all the warning IDs.</span></span> <span data-ttu-id="74fba-141">Následující příklad ukazuje, jak můžete potlačit `NU1701` pro upozornění `Huitian.PowerCollections` balíčku tak, že ručně upravíte soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="74fba-141">The following example shows how to suppress the `NU1701` warning for the `Huitian.PowerCollections` package by editing your project file manually:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Huitian.PowerCollections" Version="1.0.0" NoWarn="NU1701" />
</ItemGroup>
```

<span data-ttu-id="74fba-142">Další informace o tom, jak potlačení upozornění kompilátoru v sadě Visual Studio najdete v tématu [potlačení upozornění pro balíčky NuGet](/visualstudio/ide/how-to-suppress-compiler-warnings#suppressing-warnings-for-nuget-packages).</span><span class="sxs-lookup"><span data-stu-id="74fba-142">For more information on how to suppress compiler warnings in Visual Studio, see [Suppressing warnings for NuGet packages](/visualstudio/ide/how-to-suppress-compiler-warnings#suppressing-warnings-for-nuget-packages).</span></span>

### <a name="port-your-packages-to-packagereference"></a><span data-ttu-id="74fba-143">Přenést své balíčky do `PackageReference`</span><span class="sxs-lookup"><span data-stu-id="74fba-143">Port your packages to `PackageReference`</span></span>

<span data-ttu-id="74fba-144">.NET core používá [PackageReference](/nuget/consume-packages/package-references-in-project-files) postup určení závislostí balíčku.</span><span class="sxs-lookup"><span data-stu-id="74fba-144">.NET Core uses [PackageReference](/nuget/consume-packages/package-references-in-project-files) to specify package dependencies.</span></span> <span data-ttu-id="74fba-145">Pokud používáte [souboru packages.config](/nuget/reference/packages-config) k určení balíčků, budete muset převést přes `PackageReference`.</span><span class="sxs-lookup"><span data-stu-id="74fba-145">If you are using [packages.config](/nuget/reference/packages-config) to specify your packages, you will need to convert over to `PackageReference`.</span></span>

<span data-ttu-id="74fba-146">Další informace na [migrace ze souboru packages.config na PackageReference](/nuget/reference/migrate-packages-config-to-package-reference).</span><span class="sxs-lookup"><span data-stu-id="74fba-146">You can learn more at [Migrate from packages.config to PackageReference](/nuget/reference/migrate-packages-config-to-package-reference).</span></span>

### <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a><span data-ttu-id="74fba-147">Co dělat, když vaše závislost balíčku NuGet není spuštěna v rozhraní .NET Core</span><span class="sxs-lookup"><span data-stu-id="74fba-147">What to do when your NuGet package dependency doesn't run on .NET Core</span></span>

<span data-ttu-id="74fba-148">Existuje několik věcí, které můžete provést, pokud závisí na balíčku NuGet není spuštěna v rozhraní .NET Core:</span><span class="sxs-lookup"><span data-stu-id="74fba-148">There are a few things you can do if a NuGet package you depend on doesn't run on .NET Core:</span></span>

1. <span data-ttu-id="74fba-149">Pokud je projekt open source a hostovaná někde, např. GitHub, můžete zapojit vývojáře přímo.</span><span class="sxs-lookup"><span data-stu-id="74fba-149">If the project is open source and hosted somewhere like GitHub, you can engage the developers directly.</span></span>
2. <span data-ttu-id="74fba-150">Můžete kontaktovat přímo na autora [nuget.org](https://www.nuget.org/). Vyhledejte balíček a klikněte na tlačítko **kontakt vlastníky** na levé straně stránky daného balíčku.</span><span class="sxs-lookup"><span data-stu-id="74fba-150">You can contact the author directly on [nuget.org](https://www.nuget.org/). Search for the package and click **Contact Owners** on the left-hand side of the package's page.</span></span>
3. <span data-ttu-id="74fba-151">Můžete vyhledat jinému balíčku, který běží na .NET Core, který provede stejné úkoly, jako balíček, který jste používali.</span><span class="sxs-lookup"><span data-stu-id="74fba-151">You can search for another package that runs on .NET Core that accomplishes the same task as the package you were using.</span></span>
4. <span data-ttu-id="74fba-152">Pokuste se, že balíček dělal sami psát kód.</span><span class="sxs-lookup"><span data-stu-id="74fba-152">You can attempt to write the code the package was doing yourself.</span></span>
5. <span data-ttu-id="74fba-153">Závislost na balíčku byste mohli eliminovat alespoň změnou funkci vaší aplikace, dokud nebude k dispozici kompatibilní verzi balíčku.</span><span class="sxs-lookup"><span data-stu-id="74fba-153">You could eliminate the dependency on the package by changing the functionality of your app, at least until a compatible version of the package becomes available.</span></span>

<span data-ttu-id="74fba-154">Mějte na paměti, že programu open source projektu a Vydavatel balíčku NuGet se často dobrovolníků.</span><span class="sxs-lookup"><span data-stu-id="74fba-154">Remember that open-source project maintainers and NuGet package publishers are often volunteers.</span></span> <span data-ttu-id="74fba-155">Přispívají, protože záleží danou doménu, dělat zdarma a často mají různé denní úlohy.</span><span class="sxs-lookup"><span data-stu-id="74fba-155">They contribute because they care about a given domain, do it for free, and often have a different daytime job.</span></span> <span data-ttu-id="74fba-156">Proto buďte s vědomím, která při kontaktování moct požádat o podporu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="74fba-156">So be mindful of that when contacting them to ask for .NET Core support.</span></span>

<span data-ttu-id="74fba-157">Pokud váš problém s žádným z výše uvedených nelze vyřešit, budete muset port až po .NET Core později.</span><span class="sxs-lookup"><span data-stu-id="74fba-157">If you can't resolve your issue with any of the above, you may have to port to .NET Core at a later date.</span></span>

<span data-ttu-id="74fba-158">Tým .NET chcete zjistit, které knihovny jsou nejdůležitější pro podporu s .NET Core.</span><span class="sxs-lookup"><span data-stu-id="74fba-158">The .NET Team would like to know which libraries are the most important to support with .NET Core.</span></span> <span data-ttu-id="74fba-159">Můžete poslat e-mailu dotnet@microsoft.com knihovny, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="74fba-159">You can send an email to dotnet@microsoft.com about the libraries you'd like to use.</span></span>

## <a name="analyze-dependencies-that-arent-nuget-packages"></a><span data-ttu-id="74fba-160">Analýza závislosti, které nejsou balíčky NuGet</span><span class="sxs-lookup"><span data-stu-id="74fba-160">Analyze dependencies that aren't NuGet packages</span></span>

<span data-ttu-id="74fba-161">Může mít závislost, která není balíček NuGet, jako je například knihovny DLL v systému souborů.</span><span class="sxs-lookup"><span data-stu-id="74fba-161">You may have a dependency that isn't a NuGet package, such as a DLL in the file system.</span></span> <span data-ttu-id="74fba-162">Jediný způsob, jak určit přenositelnost dané závislosti je spustit [.NET Portability Analyzeru](https://github.com/Microsoft/dotnet-apiport) nástroj.</span><span class="sxs-lookup"><span data-stu-id="74fba-162">The only way to determine the portability of that dependency is to run the [.NET Portability Analyzer](https://github.com/Microsoft/dotnet-apiport) tool.</span></span> <span data-ttu-id="74fba-163">Nástroj můžete analyzovat sestavení, které jsou cíleny rozhraní .NET Framework a identifikovat rozhraní API, která nejsou přenositelnost na jiné platformy .NET, jako je .NET Core.</span><span class="sxs-lookup"><span data-stu-id="74fba-163">The tool can analyze assemblies that target the .NET Framework and identify APIs that aren't portable to other .NET platforms such as .NET Core.</span></span> <span data-ttu-id="74fba-164">Nástroj můžete spustit jako konzolové aplikace v jazyce nebo [rozšíření sady Visual Studio](../../standard/analyzers/portability-analyzer.md).</span><span class="sxs-lookup"><span data-stu-id="74fba-164">You can run the tool as a console application or as a [Visual Studio extension](../../standard/analyzers/portability-analyzer.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="74fba-165">Další kroky</span><span class="sxs-lookup"><span data-stu-id="74fba-165">Next steps</span></span>

<span data-ttu-id="74fba-166">Pokud jste přenesení do knihovny, přečtěte si [přenos knihoven](libraries.md).</span><span class="sxs-lookup"><span data-stu-id="74fba-166">If you're porting a library, check out [Porting your Libraries](libraries.md).</span></span>
