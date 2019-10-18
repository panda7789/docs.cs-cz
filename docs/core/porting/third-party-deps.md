---
title: Analyzovat závislosti na kód portu pro .NET Core
description: Naučte se analyzovat externí závislosti, abyste mohli přenést projekt z .NET Framework do .NET Core.
author: cartermp
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: 36d1c1d2090a0fb9e6f48fe519d15897579df2d5
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72521469"
---
# <a name="analyze-your-dependencies-to-port-code-to-net-core"></a><span data-ttu-id="9dd35-103">Analyzovat závislosti na kód portu pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="9dd35-103">Analyze your dependencies to port code to .NET Core</span></span>

<span data-ttu-id="9dd35-104">Chcete-li svůj kód přenést do rozhraní .NET Core nebo .NET Standard, je nutné pochopit závislosti.</span><span class="sxs-lookup"><span data-stu-id="9dd35-104">To port your code to .NET Core or .NET Standard, you must understand your dependencies.</span></span> <span data-ttu-id="9dd35-105">Externí závislosti jsou [balíčky NuGet](#analyze-referenced-nuget-packages-in-your-projects) nebo [knihovny DLL](#analyze-dependencies-that-arent-nuget-packages) , na které odkazujete v projektu, ale nebudete je sestavovat.</span><span class="sxs-lookup"><span data-stu-id="9dd35-105">External dependencies are the [NuGet packages](#analyze-referenced-nuget-packages-in-your-projects) or [DLLs](#analyze-dependencies-that-arent-nuget-packages) you reference in your project, but that you don't build.</span></span> <span data-ttu-id="9dd35-106">Vyhodnoťte každou závislost a vytvořte pohotovostní plán pro ty, které nejsou kompatibilní s .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9dd35-106">Evaluate each dependency and develop a contingency plan for the ones that aren't compatible with .NET Core.</span></span> <span data-ttu-id="9dd35-107">Tady je postup, jak zjistit, jestli je závislost kompatibilní s .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9dd35-107">Here's how to determine if a dependency is compatible with .NET Core.</span></span>

## <a name="analyze-referenced-nuget-packages-in-your-projects"></a><span data-ttu-id="9dd35-108">Analyzovat odkazované balíčky NuGet ve vašich projektech</span><span class="sxs-lookup"><span data-stu-id="9dd35-108">Analyze referenced NuGet packages in your projects</span></span>

<span data-ttu-id="9dd35-109">Pokud odkazujete na balíčky NuGet v projektu, musíte ověřit, jestli jsou kompatibilní s .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9dd35-109">If you reference NuGet packages in your project, you need to verify if they're compatible with .NET Core.</span></span>
<span data-ttu-id="9dd35-110">Existují dva způsoby, jak to provést:</span><span class="sxs-lookup"><span data-stu-id="9dd35-110">There are two ways to accomplish that:</span></span>

- [<span data-ttu-id="9dd35-111">Použití aplikace Průzkumník balíčků NuGet</span><span class="sxs-lookup"><span data-stu-id="9dd35-111">Using the NuGet Package Explorer app</span></span>](#analyze-nuget-packages-using-nuget-package-explorer)
- [<span data-ttu-id="9dd35-112">Používání webu nuget.org</span><span class="sxs-lookup"><span data-stu-id="9dd35-112">Using the nuget.org site</span></span>](#analyze-nuget-packages-using-nugetorg)

<span data-ttu-id="9dd35-113">Pokud nejsou po analýze balíčků kompatibilní s .NET Core a pouze cílovými .NET Framework, můžete zjistit, zda [.NET Framework režim kompatibility](#net-framework-compatibility-mode) může pomáhat s vaším procesem přenosu.</span><span class="sxs-lookup"><span data-stu-id="9dd35-113">After analyzing the packages, if they're not compatible with .NET Core and only target .NET Framework, you can check if the [.NET Framework compatibility mode](#net-framework-compatibility-mode) can help with your porting process.</span></span>

### <a name="analyze-nuget-packages-using-nuget-package-explorer"></a><span data-ttu-id="9dd35-114">Analýza balíčků NuGet pomocí Průzkumníka balíčků NuGet</span><span class="sxs-lookup"><span data-stu-id="9dd35-114">Analyze NuGet packages using NuGet Package Explorer</span></span>

<span data-ttu-id="9dd35-115">Balíček NuGet je sada složek, které obsahují sestavení specifická pro konkrétní platformu.</span><span class="sxs-lookup"><span data-stu-id="9dd35-115">A NuGet package is itself a set of folders that contain platform-specific assemblies.</span></span> <span data-ttu-id="9dd35-116">Proto je nutné ověřit, zda existuje složka, která obsahuje kompatibilní sestavení v rámci balíčku.</span><span class="sxs-lookup"><span data-stu-id="9dd35-116">So you need to check if there's a folder that contains a compatible assembly inside the package.</span></span>

<span data-ttu-id="9dd35-117">Nejjednodušší způsob, jak zkontrolovat složky balíčku NuGet, je použít nástroj [Průzkumník balíčků NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) .</span><span class="sxs-lookup"><span data-stu-id="9dd35-117">The easiest way to inspect NuGet Package folders is to use the [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) tool.</span></span> <span data-ttu-id="9dd35-118">Po instalaci použijte následující postup k zobrazení názvů složek:</span><span class="sxs-lookup"><span data-stu-id="9dd35-118">After installing it, use the following steps to see the folder names:</span></span>

1. <span data-ttu-id="9dd35-119">Otevřete Průzkumníka balíčků NuGet.</span><span class="sxs-lookup"><span data-stu-id="9dd35-119">Open the NuGet Package Explorer.</span></span>
2. <span data-ttu-id="9dd35-120">Klikněte na **Otevřít balíček z online informačního kanálu**.</span><span class="sxs-lookup"><span data-stu-id="9dd35-120">Click **Open package from online feed**.</span></span>
3. <span data-ttu-id="9dd35-121">Vyhledejte název balíčku.</span><span class="sxs-lookup"><span data-stu-id="9dd35-121">Search for the name of the package.</span></span>
4. <span data-ttu-id="9dd35-122">Ve výsledcích hledání vyberte název balíčku a klikněte na **otevřít**.</span><span class="sxs-lookup"><span data-stu-id="9dd35-122">Select the package name from the search results and click **open**.</span></span>
5. <span data-ttu-id="9dd35-123">Rozbalte složku *lib* na pravé straně a podívejte se na názvy složek.</span><span class="sxs-lookup"><span data-stu-id="9dd35-123">Expand the *lib* folder on the right-hand side and look at folder names.</span></span>

<span data-ttu-id="9dd35-124">Vyhledejte složku s některým z následujících názvů:</span><span class="sxs-lookup"><span data-stu-id="9dd35-124">Look for a folder with any of the following names:</span></span>

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

<span data-ttu-id="9dd35-125">Tyto hodnoty jsou [cílové monikery rozhraní .NET Framework (TFM)](../../standard/frameworks.md) , které jsou namapovány na verze [.NET Standard](../../standard/net-standard.md), .NET Core a tradiční profily PŘENOSITELNÉ knihovny tříd (PCL), které jsou kompatibilní s .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9dd35-125">These values are the [Target Framework Monikers (TFMs)](../../standard/frameworks.md) that map to versions of the [.NET Standard](../../standard/net-standard.md), .NET Core, and traditional Portable Class Library (PCL) profiles that are compatible with .NET Core.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9dd35-126">Při prohlížení TFM, který balíček podporuje, pamatujte, že `netcoreapp*`, i když je kompatibilní, je jenom pro projekty .NET Core, a ne pro .NET Standard projekty.</span><span class="sxs-lookup"><span data-stu-id="9dd35-126">When looking at the TFMs that a package supports, note that `netcoreapp*`, while compatible, is for .NET Core projects only and not for .NET Standard projects.</span></span>
> <span data-ttu-id="9dd35-127">Knihovna, která cílí jenom na `netcoreapp*` a ne `netstandard*`, může být spotřebovaná jenom jinými aplikacemi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9dd35-127">A library that only targets `netcoreapp*` and not `netstandard*` can only be consumed by other .NET Core apps.</span></span>

### <a name="analyze-nuget-packages-using-nugetorg"></a><span data-ttu-id="9dd35-128">Analýza balíčků NuGet pomocí nuget.org</span><span class="sxs-lookup"><span data-stu-id="9dd35-128">Analyze NuGet packages using nuget.org</span></span>

<span data-ttu-id="9dd35-129">Případně se můžete podívat na TFM, který každý balíček podporuje v [NuGet.org](https://www.nuget.org/) v části **závislosti** stránky balíčku.</span><span class="sxs-lookup"><span data-stu-id="9dd35-129">Alternatively, you can see the TFMs that each package supports on [nuget.org](https://www.nuget.org/) under the **Dependencies** section of the package page.</span></span>

<span data-ttu-id="9dd35-130">I když použití webu je jednodušší způsob, jak ověřit kompatibilitu, informace o **závislostech** nejsou v lokalitě k dispozici pro všechny balíčky.</span><span class="sxs-lookup"><span data-stu-id="9dd35-130">Although using the site is an easier method to verify the compatibility, **Dependencies** information is not available on the site for all packages.</span></span>

### <a name="net-framework-compatibility-mode"></a><span data-ttu-id="9dd35-131">Režim kompatibility .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9dd35-131">.NET Framework compatibility mode</span></span>

<span data-ttu-id="9dd35-132">Po analýze balíčků NuGet můžete zjistit, že cílí jenom na .NET Framework jako většina balíčků NuGet.</span><span class="sxs-lookup"><span data-stu-id="9dd35-132">After analyzing the NuGet packages, you might find that they only target the .NET Framework, as most NuGet packages do.</span></span>

<span data-ttu-id="9dd35-133">Počínaje .NET Standard 2,0 byl zaveden režim kompatibility .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9dd35-133">Starting with .NET Standard 2.0, the .NET Framework compatibility mode was introduced.</span></span> <span data-ttu-id="9dd35-134">Tento režim kompatibility umožňuje projektům .NET Standard a .NET Core odkazovat na .NET Framework knihovny.</span><span class="sxs-lookup"><span data-stu-id="9dd35-134">This compatibility mode allows .NET Standard and .NET Core projects to reference .NET Framework libraries.</span></span> <span data-ttu-id="9dd35-135">Odkazování na knihovny .NET Framework nefunguje pro všechny projekty, například pokud knihovna používá rozhraní API Windows Presentation Foundation (WPF), ale odblokuje mnoho scénářů přenosu.</span><span class="sxs-lookup"><span data-stu-id="9dd35-135">Referencing .NET Framework libraries doesn't work for all projects, such as if the library uses Windows Presentation Foundation (WPF) APIs, but it does unblock many porting scenarios.</span></span>

<span data-ttu-id="9dd35-136">Při odkazování na balíčky NuGet, které cílí na .NET Framework ve vašem projektu, jako je například [Huitian. PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections), získáte upozornění záložního balíčku ([NU1701](/nuget/reference/errors-and-warnings/nu1701)) podobně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="9dd35-136">When you reference NuGet packages that target the .NET Framework in your project, such as [Huitian.PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections), you get a package fallback warning ([NU1701](/nuget/reference/errors-and-warnings/nu1701)) similar to the following example:</span></span>

`NU1701: Package ‘Huitian.PowerCollections 1.0.0’ was restored using ‘.NETFramework,Version=v4.6.1’ instead of the project target framework ‘.NETStandard,Version=v2.0’. This package may not be fully compatible with your project.`

<span data-ttu-id="9dd35-137">Toto upozornění se zobrazí, když přidáte balíček a pokaždé, když ho sestavíte, abyste se ujistili, že balíček otestujete s vaším projektem.</span><span class="sxs-lookup"><span data-stu-id="9dd35-137">That warning is displayed when you add the package and every time you build to make sure you test that package with your project.</span></span> <span data-ttu-id="9dd35-138">Pokud projekt pracuje podle očekávání, můžete toto upozornění potlačit úpravou vlastností balíčku v aplikaci Visual Studio nebo ruční úpravou souboru projektu ve svém oblíbeném editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="9dd35-138">If your project is working as expected, you can suppress that warning by editing the package properties in Visual Studio or by manually editing the project file in your favorite code editor.</span></span>

<span data-ttu-id="9dd35-139">Chcete-li potlačit upozornění úpravou souboru projektu, vyhledejte položku `PackageReference` balíčku, pro který chcete upozornění potlačit, a přidejte atribut `NoWarn`.</span><span class="sxs-lookup"><span data-stu-id="9dd35-139">To suppress the warning by editing the project file, find the `PackageReference` entry for the package you want to suppress the warning for and add the `NoWarn` attribute.</span></span> <span data-ttu-id="9dd35-140">Atribut `NoWarn` přijímá čárkami oddělený seznam všech ID upozornění.</span><span class="sxs-lookup"><span data-stu-id="9dd35-140">The `NoWarn` attribute accepts a comma-separated list of all the warning IDs.</span></span> <span data-ttu-id="9dd35-141">Následující příklad ukazuje, jak potlačit upozornění `NU1701` pro balíček `Huitian.PowerCollections` úpravou souboru projektu ručně:</span><span class="sxs-lookup"><span data-stu-id="9dd35-141">The following example shows how to suppress the `NU1701` warning for the `Huitian.PowerCollections` package by editing your project file manually:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Huitian.PowerCollections" Version="1.0.0" NoWarn="NU1701" />
</ItemGroup>
```

<span data-ttu-id="9dd35-142">Další informace o potlačení upozornění kompilátoru v aplikaci Visual Studio naleznete v tématu [potlačení upozornění pro balíčky NuGet](/visualstudio/ide/how-to-suppress-compiler-warnings#suppress-warnings-for-nuget-packages).</span><span class="sxs-lookup"><span data-stu-id="9dd35-142">For more information on how to suppress compiler warnings in Visual Studio, see [Suppressing warnings for NuGet packages](/visualstudio/ide/how-to-suppress-compiler-warnings#suppress-warnings-for-nuget-packages).</span></span>

## <a name="port-your-packages-to-packagereference"></a><span data-ttu-id="9dd35-143">Portování balíčků pro `PackageReference`</span><span class="sxs-lookup"><span data-stu-id="9dd35-143">Port your packages to `PackageReference`</span></span>

<span data-ttu-id="9dd35-144">.NET Core používá [PackageReference](/nuget/consume-packages/package-references-in-project-files) k určení závislostí balíčku.</span><span class="sxs-lookup"><span data-stu-id="9dd35-144">.NET Core uses [PackageReference](/nuget/consume-packages/package-references-in-project-files) to specify package dependencies.</span></span> <span data-ttu-id="9dd35-145">Pokud k určení balíčků používáte [Package. config](/nuget/reference/packages-config) , budete muset převést na `PackageReference`.</span><span class="sxs-lookup"><span data-stu-id="9dd35-145">If you are using [packages.config](/nuget/reference/packages-config) to specify your packages, you will need to convert over to `PackageReference`.</span></span>

<span data-ttu-id="9dd35-146">Další informace najdete na adrese [migrace ze souboru Packages. config na PackageReference](/nuget/reference/migrate-packages-config-to-package-reference).</span><span class="sxs-lookup"><span data-stu-id="9dd35-146">You can learn more at [Migrate from packages.config to PackageReference](/nuget/reference/migrate-packages-config-to-package-reference).</span></span>

## <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a><span data-ttu-id="9dd35-147">Co dělat, když se závislost balíčku NuGet nespustí v .NET Core</span><span class="sxs-lookup"><span data-stu-id="9dd35-147">What to do when your NuGet package dependency doesn't run on .NET Core</span></span>

<span data-ttu-id="9dd35-148">Existuje několik věcí, které můžete udělat, pokud balíček NuGet, na kterém závisíte, neběží na .NET Core:</span><span class="sxs-lookup"><span data-stu-id="9dd35-148">There are a few things you can do if a NuGet package you depend on doesn't run on .NET Core:</span></span>

1. <span data-ttu-id="9dd35-149">Pokud je projekt Open Source a hostovaný někde jako GitHub, můžete vývojáře přímo zapojit.</span><span class="sxs-lookup"><span data-stu-id="9dd35-149">If the project is open source and hosted somewhere like GitHub, you can engage the developers directly.</span></span>
2. <span data-ttu-id="9dd35-150">Autora můžete kontaktovat přímo na [NuGet.org](https://www.nuget.org/). Vyhledejte balíček a na levé straně stránky balíčku klikněte na **vlastníci kontaktní** osoby.</span><span class="sxs-lookup"><span data-stu-id="9dd35-150">You can contact the author directly on [nuget.org](https://www.nuget.org/). Search for the package and click **Contact Owners** on the left-hand side of the package's page.</span></span>
3. <span data-ttu-id="9dd35-151">Můžete vyhledat jiný balíček, který běží v .NET Core, který provede stejnou úlohu jako balíček, který jste používali.</span><span class="sxs-lookup"><span data-stu-id="9dd35-151">You can search for another package that runs on .NET Core that accomplishes the same task as the package you were using.</span></span>
4. <span data-ttu-id="9dd35-152">Můžete se pokusit napsat kód, který balíček prováděl sami.</span><span class="sxs-lookup"><span data-stu-id="9dd35-152">You can attempt to write the code the package was doing yourself.</span></span>
5. <span data-ttu-id="9dd35-153">Závislost na balíčku můžete eliminovat tak, že změníte funkčnost vaší aplikace alespoň do chvíle, kdy bude k dispozici kompatibilní verze balíčku.</span><span class="sxs-lookup"><span data-stu-id="9dd35-153">You could eliminate the dependency on the package by changing the functionality of your app, at least until a compatible version of the package becomes available.</span></span>

<span data-ttu-id="9dd35-154">Pamatujte na to, že open source projekty údržba a vydavatelé balíčků NuGet jsou často dobrovolníkem.</span><span class="sxs-lookup"><span data-stu-id="9dd35-154">Remember that open-source project maintainers and NuGet package publishers are often volunteers.</span></span> <span data-ttu-id="9dd35-155">Přispívají vzhledem k tomu, že se na danou doménu zajímá, je to zdarma a často mají jinou denní úlohu.</span><span class="sxs-lookup"><span data-stu-id="9dd35-155">They contribute because they care about a given domain, do it for free, and often have a different daytime job.</span></span> <span data-ttu-id="9dd35-156">Nezapomeňte to mít na vědomí, že při kontaktování s žádostí o podporu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9dd35-156">So be mindful of that when contacting them to ask for .NET Core support.</span></span>

<span data-ttu-id="9dd35-157">Pokud nemůžete problém vyřešit pomocí některé z výše uvedených verzí, možná budete muset přenést na rozhraní .NET Core později.</span><span class="sxs-lookup"><span data-stu-id="9dd35-157">If you can't resolve your issue with any of the above, you may have to port to .NET Core at a later date.</span></span>

<span data-ttu-id="9dd35-158">Tým .NET by chtěl zjistit, které knihovny jsou pro podporu rozhraní .NET Core nejdůležitější.</span><span class="sxs-lookup"><span data-stu-id="9dd35-158">The .NET Team would like to know which libraries are the most important to support with .NET Core.</span></span> <span data-ttu-id="9dd35-159">Můžete odeslat e-mail dotnet@microsoft.com o knihovnách, které chcete použít.</span><span class="sxs-lookup"><span data-stu-id="9dd35-159">You can send an email to dotnet@microsoft.com about the libraries you'd like to use.</span></span>

## <a name="analyze-dependencies-that-arent-nuget-packages"></a><span data-ttu-id="9dd35-160">Analyzovat závislosti, které nejsou balíčky NuGet</span><span class="sxs-lookup"><span data-stu-id="9dd35-160">Analyze dependencies that aren't NuGet packages</span></span>

<span data-ttu-id="9dd35-161">Může se jednat o závislost, která není balíčkem NuGet, jako je například knihovna DLL v systému souborů.</span><span class="sxs-lookup"><span data-stu-id="9dd35-161">You may have a dependency that isn't a NuGet package, such as a DLL in the file system.</span></span> <span data-ttu-id="9dd35-162">Jediným způsobem, jak určit přenositelnost této závislosti, je spustit nástroj [analyzátor přenositelnosti .NET](https://github.com/Microsoft/dotnet-apiport) .</span><span class="sxs-lookup"><span data-stu-id="9dd35-162">The only way to determine the portability of that dependency is to run the [.NET Portability Analyzer](https://github.com/Microsoft/dotnet-apiport) tool.</span></span> <span data-ttu-id="9dd35-163">Nástroj může analyzovat sestavení, která cílí na .NET Framework, a identifikovat rozhraní API, která nejsou přenosné na jiné platformy .NET, jako je .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9dd35-163">The tool can analyze assemblies that target the .NET Framework and identify APIs that aren't portable to other .NET platforms such as .NET Core.</span></span> <span data-ttu-id="9dd35-164">Nástroj můžete spustit jako konzolovou aplikaci nebo jako [rozšíření sady Visual Studio](../../standard/analyzers/portability-analyzer.md).</span><span class="sxs-lookup"><span data-stu-id="9dd35-164">You can run the tool as a console application or as a [Visual Studio extension](../../standard/analyzers/portability-analyzer.md).</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="9dd35-165">Next</span><span class="sxs-lookup"><span data-stu-id="9dd35-165">Next</span></span>](libraries.md)
