---
title: Portování do .NET Core - analyzovat závislostmi třetích stran
description: Zjistěte, jak analyzovat závislosti třetích stran k portu z rozhraní .NET Framework projektu na .NET Core.
author: cartermp
ms.author: mairaw
ms.date: 02/15/2018
ms.openlocfilehash: a5affd8f1c493a87b2a4f7cd4096d168d404626a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216827"
---
# <a name="analyze-your-third-party-dependencies"></a><span data-ttu-id="3ac2e-103">Analýza závislostmi třetích stran</span><span class="sxs-lookup"><span data-stu-id="3ac2e-103">Analyze your third-party dependencies</span></span>

<span data-ttu-id="3ac2e-104">Pokud hledáte, můžete k portu kódu .NET Core nebo .NET Standard, je prvním krokem v procesu přenosem pochopit závislostmi třetích stran.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-104">If you're looking to port your code to .NET Core or .NET Standard, the first step in the porting process is to understand your third-party dependencies.</span></span> <span data-ttu-id="3ac2e-105">Třetí strany závislosti jsou buď [balíčky NuGet](#analyze-referenced-nuget-packages-on-your-project) nebo [knihovny DLL](#analyze-dependencies-that-arent-nuget-packages) jste odkazující na ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-105">Third-party dependencies are either [NuGet packages](#analyze-referenced-nuget-packages-on-your-project) or [DLLs](#analyze-dependencies-that-arent-nuget-packages) you're referencing in your project.</span></span> <span data-ttu-id="3ac2e-106">Posuďte každá závislost a vytvořte pohotovostní plán závislosti, které nejsou kompatibilní s .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-106">Evaluate each dependency and develop a contingency plan for the dependencies that aren't compatible with .NET Core.</span></span> <span data-ttu-id="3ac2e-107">Tento článek ukazuje, jak zjistit, jestli závislost kompatibilní s .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-107">This article shows you how to determine if the dependency is compatible with .NET Core.</span></span>

## <a name="analyze-referenced-nuget-packages-in-your-project"></a><span data-ttu-id="3ac2e-108">Analýza odkazované balíčky NuGet ve vašem projektu</span><span class="sxs-lookup"><span data-stu-id="3ac2e-108">Analyze referenced NuGet packages in your project</span></span>

<span data-ttu-id="3ac2e-109">Pokud jste odkazování balíčky NuGet ve vašem projektu, je třeba ověřit, pokud jsou kompatibilní s .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-109">If you're referencing NuGet packages in your project, you need to verify if they're compatible with .NET Core.</span></span>
<span data-ttu-id="3ac2e-110">To provést dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="3ac2e-110">There are two ways to accomplish that:</span></span>

* <span data-ttu-id="3ac2e-111">[Pomocí Průzkumníku balíčků NuGet aplikace](#analyze-nuget-packages-using-nuget-package-explorer) (nejspolehlivější způsob).</span><span class="sxs-lookup"><span data-stu-id="3ac2e-111">[Using the NuGet Package Explorer app](#analyze-nuget-packages-using-nuget-package-explorer) (the most reliable method).</span></span>
* <span data-ttu-id="3ac2e-112">[Pomocí webu nuget.org](#analyze-nuget-packages-using-nugetorg).</span><span class="sxs-lookup"><span data-stu-id="3ac2e-112">[Using the nuget.org site](#analyze-nuget-packages-using-nugetorg).</span></span>

<span data-ttu-id="3ac2e-113">Po analýze balíčků, pokud nejsou kompatibilní s .NET Core a pouze cílové rozhraní .NET Framework, můžete zkontrolovat, pokud [režim kompatibility rozhraní .NET Framework](#net-framework-compatibility-mode) může pomoct s přenosem procesu.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-113">After analyzing the packages, if they're not compatible with .NET Core and only target .NET Framework, you can check if the [.NET Framework compatibility mode](#net-framework-compatibility-mode) can help with your porting process.</span></span>

### <a name="analyze-nuget-packages-using-nuget-package-explorer"></a><span data-ttu-id="3ac2e-114">Analýza balíčků NuGet pomocí Průzkumníku balíčků NuGet</span><span class="sxs-lookup"><span data-stu-id="3ac2e-114">Analyze NuGet packages using NuGet Package Explorer</span></span>

<span data-ttu-id="3ac2e-115">Balíček NuGet je sám sadu složek, které obsahují sestavení specifické pro platformu.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-115">A NuGet package is itself a set of folders that contain platform-specific assemblies.</span></span> <span data-ttu-id="3ac2e-116">Proto je třeba zkontrolovat, zda je složka, která obsahuje kompatibilní sestavení uvnitř balíčku.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-116">So you need to check if there's a folder that contains a compatible assembly inside the package.</span></span>

<span data-ttu-id="3ac2e-117">Nejjednodušší způsob, jak zkontrolovat balíček NuGet složek se má používat [Explorer balíček NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) nástroj.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-117">The easiest way to inspect NuGet Package folders is to use the [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) tool.</span></span> <span data-ttu-id="3ac2e-118">Po instalaci ji, použijte následující postup zobrazíte názvy složek:</span><span class="sxs-lookup"><span data-stu-id="3ac2e-118">After installing it, use the following steps to see the folder names:</span></span>

1. <span data-ttu-id="3ac2e-119">Otevřete Průzkumníka balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-119">Open the NuGet Package Explorer.</span></span>
2. <span data-ttu-id="3ac2e-120">Klikněte na tlačítko **otevřít balíček z online kanálu**.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-120">Click **Open package from online feed**.</span></span>
3. <span data-ttu-id="3ac2e-121">Vyhledejte název balíčku.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-121">Search for the name of the package.</span></span>
4. <span data-ttu-id="3ac2e-122">Ve výsledcích hledání vyberte název balíčku a klikněte na tlačítko **otevřete**.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-122">Select the package name from the search results and click **open**.</span></span>
5. <span data-ttu-id="3ac2e-123">Rozbalte *lib* složky na pravé straně a podívejte se na názvy složek.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-123">Expand the *lib* folder on the right-hand side and look at folder names.</span></span>

<span data-ttu-id="3ac2e-124">Vyhledejte složku s žádným z následujících názvů:</span><span class="sxs-lookup"><span data-stu-id="3ac2e-124">Look for a folder with any of the following names:</span></span>

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
portable-net45-win8
portable-win8-wpa8
portable-net451-win81
portable-net45-win8-wpa8-wpa81
```

<span data-ttu-id="3ac2e-125">Tyto hodnoty jsou [cílový Framework Monikery (TFMs)](../../standard/frameworks.md) , mapování na verzích [.NET Standard](../../standard/net-standard.md), .NET Core a tradiční profily přenosných třída knihovny PCL (), které jsou kompatibilní s .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-125">These values are the [Target Framework Monikers (TFMs)](../../standard/frameworks.md) that map to versions of the [.NET Standard](../../standard/net-standard.md), .NET Core, and traditional Portable Class Library (PCL) profiles that are compatible with .NET Core.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3ac2e-126">Při prohlížení TFMs, které podporuje balíček, Všimněte si, že `netcoreapp*`, při kompatibilní, jenom .NET Core projekty a ne pro rozhraní .NET standardní projekty.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-126">When looking at the TFMs that a package supports, note that `netcoreapp*`, while compatible, is for .NET Core projects only and not for .NET Standard projects.</span></span>
> <span data-ttu-id="3ac2e-127">Knihovny, který se zaměřuje jenom `netcoreapp*` a není `netstandard*` pouze mohou být využívány službou jiných aplikací .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-127">A library that only targets `netcoreapp*` and not `netstandard*` can only be consumed by other .NET Core apps.</span></span>

<span data-ttu-id="3ac2e-128">Existují také některé starší verze TFMs v předběžné verze jádra rozhraní .NET, která je také možné kompatibilní:</span><span class="sxs-lookup"><span data-stu-id="3ac2e-128">There are also some legacy TFMs used in pre-release versions of .NET Core that may also be compatible:</span></span>

```
dnxcore50
dotnet5.0
dotnet5.1
dotnet5.2
dotnet5.3
dotnet5.4
dotnet5.5
```

<span data-ttu-id="3ac2e-129">Při těchto TFMs pravděpodobně pracovat s kódu, neexistuje žádná záruka kompatibility.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-129">While these TFMs likely work with your code, there is no guarantee of compatibility.</span></span> <span data-ttu-id="3ac2e-130">Balíčky s tyto TFMs nebyly vytvořené s balíčky předběžné verze .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-130">Packages with these TFMs were built with pre-release .NET Core packages.</span></span> <span data-ttu-id="3ac2e-131">Poznamenejte si při (nebo pokud) balíčky pomocí těchto TFMs jsou aktualizovány na .NET Standard na základě.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-131">Take note of when (or if) packages using these TFMs are updated to be .NET Standard-based.</span></span>

> [!NOTE]
> <span data-ttu-id="3ac2e-132">Chcete-li použít balíček cílení tradiční PCL nebo předběžné verze .NET Core cíl, je nutné použít `PackageTargetFallback` MSBuild element v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-132">To use a package targeting a traditional PCL or pre-release .NET Core target, you must use the `PackageTargetFallback` MSBuild element in your project file.</span></span>
> <span data-ttu-id="3ac2e-133">Další informace o tomto prvku MSBuild najdete v tématu [ `PackageTargetFallback` ](../tools/csproj.md#packagetargetfallback).</span><span class="sxs-lookup"><span data-stu-id="3ac2e-133">For more information about this MSBuild element, see [`PackageTargetFallback`](../tools/csproj.md#packagetargetfallback).</span></span>

### <a name="analyze-nuget-packages-using-nugetorg"></a><span data-ttu-id="3ac2e-134">Analýza balíčků NuGet pomocí nuget.org</span><span class="sxs-lookup"><span data-stu-id="3ac2e-134">Analyze NuGet packages using nuget.org</span></span>

<span data-ttu-id="3ac2e-135">Alternativně uvidíte TFMs, které podporuje každý balíček na [nuget.org](https://www.nuget.org/) pod **závislosti** části stránky balíčku.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-135">Alternatively, you can see the TFMs that each package supports on [nuget.org](https://www.nuget.org/) under the **Dependencies** section of the package page.</span></span>

<span data-ttu-id="3ac2e-136">I když pomocí webu je jednodušší metodu k ověření kompatibility, **závislosti** informace nejsou k dispozici na webu pro všechny balíčky.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-136">Although using the site is an easier method to verify the compatibility, **Dependencies** information is not available on the site for all packages.</span></span>

### <a name="net-framework-compatibility-mode"></a><span data-ttu-id="3ac2e-137">Režim kompatibility rozhraní .NET framework</span><span class="sxs-lookup"><span data-stu-id="3ac2e-137">.NET Framework compatibility mode</span></span>

<span data-ttu-id="3ac2e-138">Po analýze balíčky NuGet, je možné, že pouze cílové rozhraní .NET Framework, stejně jako většinu balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-138">After analyzing the NuGet packages, you might find that they only target the .NET Framework, as most NuGet packages do.</span></span>

<span data-ttu-id="3ac2e-139">Od verze rozhraní .NET 2.0 standardní, byla zavedena režimu kompatibility rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-139">Starting with .NET Standard 2.0, the .NET Framework compatibility mode was introduced.</span></span> <span data-ttu-id="3ac2e-140">Tento režim kompatibility umožňuje .NET Standard a .NET Core projekty tak, aby odkazovaly knihovny rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-140">This compatibility mode allows .NET Standard and .NET Core projects to reference .NET Framework libraries.</span></span> <span data-ttu-id="3ac2e-141">Odkazování na rozhraní .NET Framework knihovny nefunguje pro všechny projekty, jako třeba když knihovny používá Windows Presentation Foundation (WPF) rozhraní API, ale jeho odblokování mnoho scénářů s přenosem.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-141">Referencing .NET Framework libraries doesn't work for all projects, such as if the library uses Windows Presentation Foundation (WPF) APIs, but it does unblock many porting scenarios.</span></span>

<span data-ttu-id="3ac2e-142">Při odkazu na balíčky NuGet, cílených na rozhraní .NET Framework v projektu, například [Huitian.PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections), se zobrazí upozornění, záložní balíčku ([NU1701](/nuget/reference/errors-and-warnings#nu1701)) podobně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="3ac2e-142">When you reference NuGet packages that target the .NET Framework in your project, such as [Huitian.PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections), you get a package fallback warning ([NU1701](/nuget/reference/errors-and-warnings#nu1701)) similar to the following example:</span></span>

`NU1701: Package ‘Huitian.PowerCollections 1.0.0’ was restored using ‘.NETFramework,Version=v4.6.1’ instead of the project target framework ‘.NETStandard,Version=v2.0’. This package may not be fully compatible with your project.`

<span data-ttu-id="3ac2e-143">Tento upozornění se zobrazí, když přidáte balíček a pokaždé, když vytvoříte a ujistěte se otestování tento balíček v projektu.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-143">That warning is displayed when you add the package and every time you build to make sure you test that package with your project.</span></span> <span data-ttu-id="3ac2e-144">Pokud projekt funguje podle očekávání, můžete tak, že upravíte vlastnosti balíčku v sadě Visual Studio nebo ruční úpravy souboru projektu ve svém oblíbeném kód editoru potlačit tohoto upozornění.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-144">If your project is working as expected, you can suppress that warning by editing the package properties in Visual Studio or by manually editing the project file in your favorite code editor.</span></span>

<span data-ttu-id="3ac2e-145">Potlačit upozornění úpravou souboru projektu, Najít `PackageReference` balíčku pro položku, kterou chcete potlačení upozornění pro a přidat `NoWarn` atribut.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-145">To suppress the warning by editing the project file, find the `PackageReference` entry for the package you want to suppress the warning for and add the `NoWarn` attribute.</span></span> <span data-ttu-id="3ac2e-146">`NoWarn` Atribut přijímá seznam všech upozornění ID oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-146">The `NoWarn` attribute accepts a comma-separated list of all the warning IDs.</span></span> <span data-ttu-id="3ac2e-147">Následující příklad ukazuje, jak můžete potlačit `NU1701` upozornění pro `Huitian.PowerCollections` balíček úpravou souboru projektu ručně:</span><span class="sxs-lookup"><span data-stu-id="3ac2e-147">The following example shows how to suppress the `NU1701` warning for the `Huitian.PowerCollections` package by editing your project file manually:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Huitian.PowerCollections" Version="1.0.0" NoWarn="NU1701" />
</ItemGroup>
```

<span data-ttu-id="3ac2e-148">Další informace o tom, jak potlačení upozornění kompilátoru v sadě Visual Studio najdete v tématu [potlačení upozornění pro balíčky NuGet](/visualstudio/ide/how-to-suppress-compiler-warnings#suppressing-warnings-for-nuget-packages).</span><span class="sxs-lookup"><span data-stu-id="3ac2e-148">For more information on how to suppress compiler warnings in Visual Studio, see [Suppressing warnings for NuGet packages](/visualstudio/ide/how-to-suppress-compiler-warnings#suppressing-warnings-for-nuget-packages).</span></span>

### <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a><span data-ttu-id="3ac2e-149">Co dělat, když vaše závislost balíčku NuGet nefunguje v .NET Core</span><span class="sxs-lookup"><span data-stu-id="3ac2e-149">What to do when your NuGet package dependency doesn't run on .NET Core</span></span>

<span data-ttu-id="3ac2e-150">Existuje několik věcí, které můžete provést, pokud nelze spustit na .NET Core balíčku NuGet, které závisí na:</span><span class="sxs-lookup"><span data-stu-id="3ac2e-150">There are a few things you can do if a NuGet package you depend on doesn't run on .NET Core:</span></span>

1. <span data-ttu-id="3ac2e-151">Pokud projekt je open source a je hostovaná někde jako GitHub, můžete použít vývojáři přímo.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-151">If the project is open source and hosted somewhere like GitHub, you can engage the developers directly.</span></span>
2. <span data-ttu-id="3ac2e-152">Obraťte se na autora přímo na [nuget.org](https://www.nuget.org/). Vyhledejte balíček a klikněte na **kontaktujte vlastníky** na levé straně stránky daného balíčku.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-152">You can contact the author directly on [nuget.org](https://www.nuget.org/). Search for the package and click **Contact Owners** on the left-hand side of the package's page.</span></span>
3. <span data-ttu-id="3ac2e-153">Můžete hledat jiný balíček, který běží na .NET Core, který provede stejnou úlohu jako balíčku, který jste používali.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-153">You can search for another package that runs on .NET Core that accomplishes the same task as the package you were using.</span></span>
4. <span data-ttu-id="3ac2e-154">Můžete se pokusit napsat kód, že balíček dělal sami.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-154">You can attempt to write the code the package was doing yourself.</span></span>
5. <span data-ttu-id="3ac2e-155">Závislost na balíček může eliminovat alespoň změnou funkce aplikace, dokud nebude k dispozici kompatibilní verzi balíčku.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-155">You could eliminate the dependency on the package by changing the functionality of your app, at least until a compatible version of the package becomes available.</span></span>

<span data-ttu-id="3ac2e-156">Mějte na paměti, že údržby programu open source projektu a vydavatelé balíček NuGet jsou často dobrovolníků.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-156">Remember that open-source project maintainers and NuGet package publishers are often volunteers.</span></span> <span data-ttu-id="3ac2e-157">Přispívají, protože zajímají pro danou doménu, provést zdarma a často mají různé denní úlohy.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-157">They contribute because they care about a given domain, do it for free, and often have a different daytime job.</span></span> <span data-ttu-id="3ac2e-158">Proto buďte s vědomím, při kontaktování je požádat o podporu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-158">So be mindful of that when contacting them to ask for .NET Core support.</span></span>

<span data-ttu-id="3ac2e-159">Pokud nelze vyřešit problém s žádným z výše, budete muset port na .NET Core později.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-159">If you can't resolve your issue with any of the above, you may have to port to .NET Core at a later date.</span></span>

<span data-ttu-id="3ac2e-160">Tým služby .NET chcete vědět, které knihovny jsou nejdůležitější pro podporu s .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-160">The .NET Team would like to know which libraries are the most important to support with .NET Core.</span></span> <span data-ttu-id="3ac2e-161">Můžete odeslat e-mail na dotnet@microsoft.com o knihovny, které chcete použít.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-161">You can send an email to dotnet@microsoft.com about the libraries you'd like to use.</span></span>

## <a name="analyze-dependencies-that-arent-nuget-packages"></a><span data-ttu-id="3ac2e-162">Analýza závislosti, které nejsou balíčků NuGet</span><span class="sxs-lookup"><span data-stu-id="3ac2e-162">Analyze dependencies that aren't NuGet packages</span></span>

<span data-ttu-id="3ac2e-163">Můžete mít závislost, která není balíčku NuGet, jako je například knihovny DLL v systému souborů.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-163">You may have a dependency that isn't a NuGet package, such as a DLL in the file system.</span></span> <span data-ttu-id="3ac2e-164">Jediný způsob, jak určit přenositelnost této závislosti se ke spuštění [.NET přenositelnost analyzátor](https://github.com/Microsoft/dotnet-apiport) nástroj.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-164">The only way to determine the portability of that dependency is to run the [.NET Portability Analyzer](https://github.com/Microsoft/dotnet-apiport) tool.</span></span> <span data-ttu-id="3ac2e-165">Nástroj můžete analyzovat sestavení cílených na rozhraní .NET Framework a identifikovat rozhraní API, která nejsou přenosný na jiné platformy .NET jako .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3ac2e-165">The tool can analyze assemblies that target the .NET Framework and identify APIs that aren't portable to other .NET platforms such as .NET Core.</span></span> <span data-ttu-id="3ac2e-166">Nástroj můžete spustit jako konzolové aplikace nebo jako [rozšíření sady Visual Studio](../../standard/analyzers/portability-analyzer.md).</span><span class="sxs-lookup"><span data-stu-id="3ac2e-166">You can run the tool as a console application or as a [Visual Studio extension](../../standard/analyzers/portability-analyzer.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="3ac2e-167">Další kroky</span><span class="sxs-lookup"><span data-stu-id="3ac2e-167">Next steps</span></span>

<span data-ttu-id="3ac2e-168">Pokud jste portování knihovnu, podívejte se na [portování knihovnách](libraries.md).</span><span class="sxs-lookup"><span data-stu-id="3ac2e-168">If you're porting a library, check out [Porting your Libraries](libraries.md).</span></span>
