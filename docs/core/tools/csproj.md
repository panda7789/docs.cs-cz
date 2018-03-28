---
title: Přidání do formátu csproj pro .NET Core
description: Další informace o rozdílech mezi existující a .NET Core csproj soubory
keywords: odkaz, csproj, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 09/22/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: bdc29497-64f2-4d11-a21b-4097e0bdf5c9
ms.workload:
- dotnetcore
ms.openlocfilehash: fdf91bdb24819c2d92b708e5937980ac2fb0d5fc
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2018
---
# <a name="additions-to-the-csproj-format-for-net-core"></a><span data-ttu-id="cc0e5-104">Přidání do formátu csproj pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="cc0e5-104">Additions to the csproj format for .NET Core</span></span>

<span data-ttu-id="cc0e5-105">Tento dokument popisuje změny, které byly přidány do souborů projektu jako součást přesunutí ze *project.json* k *csproj* a [MSBuild](https://github.com/Microsoft/MSBuild).</span><span class="sxs-lookup"><span data-stu-id="cc0e5-105">This document outlines the changes that were added to the project files as part of the move from *project.json* to *csproj* and [MSBuild](https://github.com/Microsoft/MSBuild).</span></span> <span data-ttu-id="cc0e5-106">Další informace o syntaxi souboru obecné projektu a referenční informace najdete v tématu [soubor projektu nástroje MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-106">For more information about general project file syntax and reference, see [the MSBuild project file](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation.</span></span>  

## <a name="implicit-package-references"></a><span data-ttu-id="cc0e5-107">Implicitní balíček odkazuje</span><span class="sxs-lookup"><span data-stu-id="cc0e5-107">Implicit package references</span></span>
<span data-ttu-id="cc0e5-108">Metapackages odkazují implicitně podle framework(s) cíl zadaný v `<TargetFramework>` nebo `<TargetFrameworks>` vlastnost souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-108">Metapackages are implicitly referenced based on the target framework(s) specified in the `<TargetFramework>` or `<TargetFrameworks>` property of your project file.</span></span> <span data-ttu-id="cc0e5-109">`<TargetFrameworks>` je ignorována, pokud `<TargetFramework>` je zadaný, nezávisle na pořadí.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-109">`<TargetFrameworks>` is ignored if `<TargetFramework>` is specified, independent of order.</span></span>

```xml
 <PropertyGroup>
   <TargetFramework>netcoreapp1.1</TargetFramework>
 </PropertyGroup>
 ```
 
 ```xml
 <PropertyGroup>
   <TargetFrameworks>netcoreapp1.1;net462</TargetFrameworks>
 </PropertyGroup>
 ```

### <a name="recommendations"></a><span data-ttu-id="cc0e5-110">Doporučení</span><span class="sxs-lookup"><span data-stu-id="cc0e5-110">Recommendations</span></span>
<span data-ttu-id="cc0e5-111">Vzhledem k tomu `Microsoft.NETCore.App` nebo `NetStandard.Library` metapackages implicitně odkazují, naše doporučené osvědčené postupy jsou následující:</span><span class="sxs-lookup"><span data-stu-id="cc0e5-111">Since `Microsoft.NETCore.App` or `NetStandard.Library` metapackages are implicitly referenced, the following are our recommended best practices:</span></span>

* <span data-ttu-id="cc0e5-112">Pokud je cílem .NET Core nebo .NET Standard, nemusí explicitní odkaz na `Microsoft.NETCore.App` nebo `NetStandard.Library` metapackages prostřednictvím `<PackageReference>` položku v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-112">When targeting .NET Core or .NET Standard, never have an explicit reference to the `Microsoft.NETCore.App` or `NetStandard.Library` metapackages via a `<PackageReference>` item in your project file.</span></span>
* <span data-ttu-id="cc0e5-113">Pokud budete potřebovat na konkrétní verzi modulu runtime, pokud je cílem .NET Core, měli byste použít `<RuntimeFrameworkVersion>` vlastnost ve vašem projektu (například `1.0.4`) namísto odkazující metapackage.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-113">If you need a specific version of the runtime when targeting .NET Core, you should use the `<RuntimeFrameworkVersion>` property in your project (for example, `1.0.4`) instead of referencing the metapackage.</span></span>
    * <span data-ttu-id="cc0e5-114">K tomu může dojít, pokud používáte [samostatná nasazení](../deploying/index.md#self-contained-deployments-scd) a je třeba daná oprava verzi 1.0.0 modul runtime LTS, např.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-114">This might happen if you are using [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) and you need a specific patch version of 1.0.0 LTS runtime, for example.</span></span>
* <span data-ttu-id="cc0e5-115">Pokud potřebujete konkrétní verzi nástroje `NetStandard.Library` metapackage, pokud je cílem .NET Standard, můžete použít `<NetStandardImplicitPackageVersion>` vlastnost a sadu verze potřebujete.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-115">If you need a specific version of the `NetStandard.Library` metapackage when targeting .NET Standard, you can use the `<NetStandardImplicitPackageVersion>` property and set the version you need.</span></span>
* <span data-ttu-id="cc0e5-116">Není explicitně přidat nebo aktualizovat odkazy na buď `Microsoft.NETCore.App` nebo `NetStandard.Library` metapackage v projektech pro rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-116">Don't explicitly add or update references to either the `Microsoft.NETCore.App` or `NetStandard.Library` metapackage in .NET Framework projects.</span></span> <span data-ttu-id="cc0e5-117">Pokud všechny verze `NetStandard.Library` je potřeba, když pomocí balíčku NuGet .NET Standard na základě, NuGet automaticky instaluje tuto verzi.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-117">If any version of `NetStandard.Library` is needed when using a .NET Standard-based NuGet package, NuGet automatically installs that version.</span></span>

## <a name="default-compilation-includes-in-net-core-projects"></a><span data-ttu-id="cc0e5-118">Výchozí kompilace zahrnuje v projektech .NET Core</span><span class="sxs-lookup"><span data-stu-id="cc0e5-118">Default compilation includes in .NET Core projects</span></span>
<span data-ttu-id="cc0e5-119">S přechodem na *csproj* formátu v nejnovější verze sady SDK sídla výchozí zahrnuje a vyloučí pro kompilaci položky a vložené prostředky k souborům vlastnosti SDK.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-119">With the move to the *csproj* format in the latest SDK versions, we've moved the default includes and excludes for compile items and embedded resources to the SDK properties files.</span></span> <span data-ttu-id="cc0e5-120">To znamená, že už muset zadat tyto položky v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-120">This means that you no longer need to specify these items in your project file.</span></span> 

<span data-ttu-id="cc0e5-121">Hlavním důvodem tohoto postupu je přehlednost v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-121">The main reason for doing this is to reduce the clutter in your project file.</span></span> <span data-ttu-id="cc0e5-122">Výchozí hodnoty, které se nacházejí v sadě SDK by měly zahrnovat nejběžnější případy použití, takže není nutné je opakovat v každém projektu, který vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-122">The defaults that are present in the SDK should cover most common use cases, so there is no need to repeat them in every project that you create.</span></span> <span data-ttu-id="cc0e5-123">To vede k menší soubory projektu, které je mnohem snazší pochopit a také upravit ručně, v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-123">This leads to smaller project files that are much easier to understand as well as edit by hand, if needed.</span></span> 

<span data-ttu-id="cc0e5-124">Následující tabulka uvádí, které elementy a které [globs](https://en.wikipedia.org/wiki/Glob_(programming)) jsou zahrnuté i vyloučené v sadě SDK:</span><span class="sxs-lookup"><span data-stu-id="cc0e5-124">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are both included and excluded in the SDK:</span></span> 

| <span data-ttu-id="cc0e5-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="cc0e5-125">Element</span></span>           | <span data-ttu-id="cc0e5-126">Zahrnout glob</span><span class="sxs-lookup"><span data-stu-id="cc0e5-126">Include glob</span></span>                              | <span data-ttu-id="cc0e5-127">Vyloučit glob</span><span class="sxs-lookup"><span data-stu-id="cc0e5-127">Exclude glob</span></span>                                                  | <span data-ttu-id="cc0e5-128">Odebrat glob</span><span class="sxs-lookup"><span data-stu-id="cc0e5-128">Remove glob</span></span>                |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| <span data-ttu-id="cc0e5-129">Kompilace</span><span class="sxs-lookup"><span data-stu-id="cc0e5-129">Compile</span></span>           | <span data-ttu-id="cc0e5-130">\*\*/\*.cs (nebo jiné jazyková rozšíření)</span><span class="sxs-lookup"><span data-stu-id="cc0e5-130">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="cc0e5-131">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="cc0e5-131">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="cc0e5-132">Není k dispozici</span><span class="sxs-lookup"><span data-stu-id="cc0e5-132">N/A</span></span>                        |
| <span data-ttu-id="cc0e5-133">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="cc0e5-133">EmbeddedResource</span></span>  | <span data-ttu-id="cc0e5-134">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="cc0e5-134">\*\*/\*.resx</span></span>                              | <span data-ttu-id="cc0e5-135">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="cc0e5-135">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="cc0e5-136">Není k dispozici</span><span class="sxs-lookup"><span data-stu-id="cc0e5-136">N/A</span></span>                        |
| <span data-ttu-id="cc0e5-137">Žádné</span><span class="sxs-lookup"><span data-stu-id="cc0e5-137">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="cc0e5-138">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="cc0e5-138">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="cc0e5-139">- \*\*/\*.cs; \*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="cc0e5-139">- \*\*/\*.cs; \*\*/\*.resx</span></span> |

<span data-ttu-id="cc0e5-140">Pokud máte globs ve vašem projektu a pokusíte se sestavení pomocí nejnovější SDK, získáte následující chybě:</span><span class="sxs-lookup"><span data-stu-id="cc0e5-140">If you have globs in your project and you try to build it using the newest SDK, you'll get the following error:</span></span>

> <span data-ttu-id="cc0e5-141">Duplicitní položky kompilace byly zahrnuty.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-141">Duplicate Compile items were included.</span></span> <span data-ttu-id="cc0e5-142">.NET SDK zahrnuje kompilace položky z adresáře projektu ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-142">The .NET SDK includes Compile items from your project directory by default.</span></span> <span data-ttu-id="cc0e5-143">Můžete tyto položky odebrat ze souboru projektu, nebo nastavte vlastnost 'EnableDefaultCompileItems' na hodnotu "false", pokud chcete výslovně nezahrnete v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-143">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span> 

<span data-ttu-id="cc0e5-144">Chcete-li získat vyřešit tuto chybu, můžete odebrat explicitní `Compile` položky, které odpovídají těm, které jsou uvedené v předchozí tabulce, nebo můžete nastavit `<EnableDefaultCompileItems>` vlastnost, která má `false`, podobné výjimky:</span><span class="sxs-lookup"><span data-stu-id="cc0e5-144">In order to get around this error, you can either remove the explicit `Compile` items that match the ones listed on the previous table, or you can set the `<EnableDefaultCompileItems>` property to `false`, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```
<span data-ttu-id="cc0e5-145">Nastavení této vlastnosti na `false` přepíší implicitní zahrnutí a chování se vrátí zpět na předchozí sady SDK, které jste museli zadat výchozí globs ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-145">Setting this property to `false` will override implicit inclusion and the behavior will revert back to the previous SDKs where you had to specify the default globs in your project.</span></span> 

<span data-ttu-id="cc0e5-146">Tato změna nedojde ke změně hlavní zahrnuje jiné mechanismy.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-146">This change does not modify the main mechanics of other includes.</span></span> <span data-ttu-id="cc0e5-147">Ale pokud chcete určit, například některé soubory získat publikována s vaší aplikací, můžete pořád použít známé mechanismy v *csproj* pro tento (například `<Content>` element).</span><span class="sxs-lookup"><span data-stu-id="cc0e5-147">However, if you wish to specify, for example, some files to get published with your app, you can still use the known mechanisms in *csproj* for that (for example, the `<Content>` element).</span></span>

<span data-ttu-id="cc0e5-148">`<EnableDefaultCompileItems>` pouze zakáže `Compile` globs, ale nemá žádný vliv na ostatní globs, jako implicitní `None` glob, která se vztahuje také na \*.cs položky.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-148">`<EnableDefaultCompileItems>` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob, which also applies to \*.cs items.</span></span> <span data-ttu-id="cc0e5-149">Z tohoto důvodu **Průzkumníku řešení** bude pokračovat zobrazit \*.cs položky v rámci projektu, které jsou zahrnuty jako `None` položky.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-149">Because of that, **Solution Explorer** will continue show \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="cc0e5-150">Podobným způsobem, můžete použít `<EnableDefaultNoneItems>` zakázat implicitní `None` glob.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-150">In a similar way, you can use `<EnableDefaultNoneItems>` to disable the implicit `None` glob.</span></span>

<span data-ttu-id="cc0e5-151">Chcete-li zakázat **všechny implicitní globs**, můžete nastavit `<EnableDefaultItems>` vlastnost `false` jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="cc0e5-151">To disable **all implicit globs**, you can set the `<EnableDefaultItems>` property to `false` as in the following example:</span></span>
```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

### <a name="recommendation"></a><span data-ttu-id="cc0e5-152">Doporučení</span><span class="sxs-lookup"><span data-stu-id="cc0e5-152">Recommendation</span></span>
<span data-ttu-id="cc0e5-153">S csproj doporučujeme odebrat globs výchozí z projektu a přidávat jenom cesty k souborům s globs pro tyto artefakty, které vaše aplikace nebo knihovna potřebuje pro různé scénáře (například za běhu a vytváření balíčků NuGet).</span><span class="sxs-lookup"><span data-stu-id="cc0e5-153">With csproj, we recommend that you remove the default globs from your project and only add file paths with globs for those artifacts that your app/library needs for various scenarios (for example, runtime and NuGet packaging).</span></span>

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a><span data-ttu-id="cc0e5-154">Jak zjistit celý projekt jako MSBuild uvidí ho</span><span class="sxs-lookup"><span data-stu-id="cc0e5-154">How to see the whole project as MSBuild sees it</span></span>

<span data-ttu-id="cc0e5-155">Když tyto změny csproj výrazně zjednodušit soubory projektu, můžete chtít najdete v části plně rozšířené projektu jako MSBuild uvidí ho, jakmile jsou součástí sady SDK a jeho cíle.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-155">While those csproj changes greatly simplify project files, you might want to see the fully expanded project as MSBuild sees it once the SDK and its targets are included.</span></span> <span data-ttu-id="cc0e5-156">Předběžné zpracování projektu s [ `/pp` přepínač](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) z [ `dotnet msbuild` ](dotnet-msbuild.md) příkaz, který ukazuje soubory, které jsou importovány, jejich zdroje a jejich příspěvky k sestavení bez ve skutečnosti sestavení projektu:</span><span class="sxs-lookup"><span data-stu-id="cc0e5-156">Preprocess the project with [the `/pp` switch](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) of the [`dotnet msbuild`](dotnet-msbuild.md) command, which shows which files are imported, their sources, and their contributions to the build without actually building the project:</span></span>

`dotnet msbuild /pp:fullproject.xml`

<span data-ttu-id="cc0e5-157">Pokud projekt má více cílové rozhraní, se musí výsledky příkazu zaměřit na pouze jeden z nich tak, že zadáte jako ve vlastnosti nástroje MSBuild:</span><span class="sxs-lookup"><span data-stu-id="cc0e5-157">If the project has multiple target frameworks, the results of the command should be focused on only one of them by specifying it as an MSBuild property:</span></span>

`dotnet msbuild /p:TargetFramework=netcoreapp2.0 /pp:fullproject.xml`

## <a name="additions"></a><span data-ttu-id="cc0e5-158">Přidání</span><span class="sxs-lookup"><span data-stu-id="cc0e5-158">Additions</span></span>

### <a name="sdk-attribute"></a><span data-ttu-id="cc0e5-159">Atribut SDK</span><span class="sxs-lookup"><span data-stu-id="cc0e5-159">Sdk attribute</span></span> 
<span data-ttu-id="cc0e5-160">`<Project>` Element *.csproj* soubor má nový atribut názvem `Sdk`.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-160">The `<Project>` element of the *.csproj* file has a new attribute called `Sdk`.</span></span> <span data-ttu-id="cc0e5-161">`Sdk` Určuje, které SDK bude používán v projektu.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-161">`Sdk` specifies which SDK will be used by the project.</span></span> <span data-ttu-id="cc0e5-162">Sadu SDK, jako [rozvrstvení dokumentu](cli-msbuild-architecture.md) popisuje, je sada MSBuild [úlohy](/visualstudio/msbuild/msbuild-tasks) a [cíle](/visualstudio/msbuild/msbuild-targets) , můžete vytvořit kódu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-162">The SDK, as the [layering document](cli-msbuild-architecture.md) describes, is a set of MSBuild [tasks](/visualstudio/msbuild/msbuild-tasks) and [targets](/visualstudio/msbuild/msbuild-targets) that can build .NET Core code.</span></span> <span data-ttu-id="cc0e5-163">Jsme dodávat dvě hlavní sady SDK nástroje .NET Core:</span><span class="sxs-lookup"><span data-stu-id="cc0e5-163">We ship two main SDKs with the .NET Core tools:</span></span>

1. <span data-ttu-id="cc0e5-164">.NET Core SDK s ID `Microsoft.NET.Sdk`</span><span class="sxs-lookup"><span data-stu-id="cc0e5-164">The .NET Core SDK with the ID of `Microsoft.NET.Sdk`</span></span>
2. <span data-ttu-id="cc0e5-165">.NET Core web SDK s ID `Microsoft.NET.Sdk.Web`</span><span class="sxs-lookup"><span data-stu-id="cc0e5-165">The .NET Core web SDK with the ID of `Microsoft.NET.Sdk.Web`</span></span>

<span data-ttu-id="cc0e5-166">Je potřeba mít `Sdk` nastaven atribut na jednu z těchto ID na `<Project>` element Chcete-li použít nástroje .NET Core a sestavení kódu.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-166">You need to have the `Sdk` attribute set to one of those IDs on the `<Project>` element in order to use the .NET Core tools and build your code.</span></span> 

### <a name="packagereference"></a><span data-ttu-id="cc0e5-167">PackageReference</span><span class="sxs-lookup"><span data-stu-id="cc0e5-167">PackageReference</span></span>
<span data-ttu-id="cc0e5-168">Položka, která určuje závislostí NuGet v projektu.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-168">Item that specifies a NuGet dependency in the project.</span></span> <span data-ttu-id="cc0e5-169">`Include` Atribut určuje ID balíčku.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-169">The `Include` attribute specifies the package ID.</span></span> 

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a><span data-ttu-id="cc0e5-170">Version</span><span class="sxs-lookup"><span data-stu-id="cc0e5-170">Version</span></span>
<span data-ttu-id="cc0e5-171">`Version` Určuje verzi balíčku, který má obnovit.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-171">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="cc0e5-172">Atribut respektuje pravidla [verze NuGet](/nuget/create-packages/dependency-versions#version-ranges) schéma.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-172">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="cc0e5-173">Výchozí chování je v případě shody přesnou verzi.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-173">The default behavior is an exact version match.</span></span> <span data-ttu-id="cc0e5-174">Například zadání `Version="1.2.3"` je ekvivalentní NuGet zápis `[1.2.3]` pro přesnou 1.2.3 verze balíčku.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-174">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

#### <a name="includeassets-excludeassets-and-privateassets"></a><span data-ttu-id="cc0e5-175">IncludeAssets, ExcludeAssets a PrivateAssets</span><span class="sxs-lookup"><span data-stu-id="cc0e5-175">IncludeAssets, ExcludeAssets and PrivateAssets</span></span>
<span data-ttu-id="cc0e5-176">`IncludeAssets` atribut určuje, jaké prostředky, které patří do balíčku určeného `<PackageReference>` by měl být využívány.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-176">`IncludeAssets` attribute specifies what assets belonging to the package specified by `<PackageReference>` should be consumed.</span></span> 

<span data-ttu-id="cc0e5-177">`ExcludeAssets` atribut určuje, jaké prostředky, které patří do balíčku určeného `<PackageReference>` by neměl být využívány.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-177">`ExcludeAssets` attribute specifies what assets belonging to the package specified by `<PackageReference>` should not be consumed.</span></span>

<span data-ttu-id="cc0e5-178">`PrivateAssets` atribut určuje, jaké prostředky, které patří do balíčku určeného `<PackageReference>` by měl být využívány ale, že by neměl toku do další projektu.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-178">`PrivateAssets` attribute specifies what assets belonging to the package specified by `<PackageReference>` should be consumed but that they should not flow to the next project.</span></span> 

> [!NOTE]
> <span data-ttu-id="cc0e5-179">`PrivateAssets` je ekvivalentní *project.json*/*xproj* `SuppressParent` element.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-179">`PrivateAssets` is equivalent to the *project.json*/*xproj* `SuppressParent` element.</span></span>

<span data-ttu-id="cc0e5-180">Tyto atributy mohou obsahovat jednu nebo více z následujících položek:</span><span class="sxs-lookup"><span data-stu-id="cc0e5-180">These attributes can contain one or more of the following items:</span></span>

* <span data-ttu-id="cc0e5-181">`Compile` – jsou k dispozici ke kompilaci proti obsah složky lib.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-181">`Compile` – the contents of the lib folder are available to compile against.</span></span>
* <span data-ttu-id="cc0e5-182">`Runtime` – distribuují obsah složky modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-182">`Runtime` – the contents of the runtime folder are distributed.</span></span>
* <span data-ttu-id="cc0e5-183">`ContentFiles` – obsah *contentfiles* složky se používá.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-183">`ContentFiles` – the contents of the *contentfiles* folder are used.</span></span>
* <span data-ttu-id="cc0e5-184">`Build` – props/cíle ve složce sestavení se používají.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-184">`Build` – the props/targets in the build folder are used.</span></span>
* <span data-ttu-id="cc0e5-185">`Native` – obsah z nativní prostředky se zkopírují do výstupní složky pro modul runtime.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-185">`Native` – the contents from native assets are copied to the output folder for runtime.</span></span>
* <span data-ttu-id="cc0e5-186">`Analyzers` – Analyzátory se používají.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-186">`Analyzers` – the analyzers are used.</span></span>

<span data-ttu-id="cc0e5-187">Alternativně může obsahovat atribut:</span><span class="sxs-lookup"><span data-stu-id="cc0e5-187">Alternatively, the attribute can contain:</span></span>

* <span data-ttu-id="cc0e5-188">`None` – žádné prostředky se používají.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-188">`None` – none of the assets are used.</span></span>
* <span data-ttu-id="cc0e5-189">`All` – všechny prostředky používají.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-189">`All` – all assets are used.</span></span>

### <a name="dotnetclitoolreference"></a><span data-ttu-id="cc0e5-190">DotNetCliToolReference</span><span class="sxs-lookup"><span data-stu-id="cc0e5-190">DotNetCliToolReference</span></span>
<span data-ttu-id="cc0e5-191">`<DotNetCliToolReference>` Item – prvek určuje nástroj příkazového řádku, který chce uživatel obnovit v kontextu projektu.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-191">`<DotNetCliToolReference>` item element specifies the CLI tool that the user wants to restore in the context of the project.</span></span> <span data-ttu-id="cc0e5-192">Je to náhrada za `tools` uzlu v *project.json*.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-192">It's a replacement for the `tools` node in *project.json*.</span></span> 

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

#### <a name="version"></a><span data-ttu-id="cc0e5-193">Version</span><span class="sxs-lookup"><span data-stu-id="cc0e5-193">Version</span></span>
<span data-ttu-id="cc0e5-194">`Version` Určuje verzi balíčku, který má obnovit.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-194">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="cc0e5-195">Atribut respektuje pravidla [verze NuGet](/nuget/create-packages/dependency-versions#version-ranges) schéma.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-195">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="cc0e5-196">Výchozí chování je v případě shody přesnou verzi.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-196">The default behavior is an exact version match.</span></span> <span data-ttu-id="cc0e5-197">Například zadání `Version="1.2.3"` je ekvivalentní NuGet zápis `[1.2.3]` pro přesnou 1.2.3 verze balíčku.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-197">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

### <a name="runtimeidentifiers"></a><span data-ttu-id="cc0e5-198">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="cc0e5-198">RuntimeIdentifiers</span></span>
<span data-ttu-id="cc0e5-199">`<RuntimeIdentifiers>` Vám umožňuje určit seznam oddělený středníkem [Runtime identifikátorů (RID)](../rid-catalog.md) pro projekt.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-199">The `<RuntimeIdentifiers>` element lets you specify a semicolon-delimited list of [Runtime Identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="cc0e5-200">Povolit identifikátorů RID publikování samostatná nasazení.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-200">RIDs enable publishing a self-contained deployments.</span></span> 

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a><span data-ttu-id="cc0e5-201">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="cc0e5-201">RuntimeIdentifier</span></span>
<span data-ttu-id="cc0e5-202">`<RuntimeIdentifier>` Element umožňuje určit pouze jeden [identifikátor Runtime (RID)](../rid-catalog.md) pro projekt.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-202">The `<RuntimeIdentifier>` element allows you to specify only one [Runtime Identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="cc0e5-203">Povolit identifikátorů RID publikování samostatná nasazení.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-203">RIDs enable publishing a self-contained deployment.</span></span> 

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

### <a name="packagetargetfallback"></a><span data-ttu-id="cc0e5-204">PackageTargetFallback</span><span class="sxs-lookup"><span data-stu-id="cc0e5-204">PackageTargetFallback</span></span> 
<span data-ttu-id="cc0e5-205">`<PackageTargetFallback>` Element umožňuje určit sadu kompatibilní cíle, který se má použít při obnovování balíčků.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-205">The `<PackageTargetFallback>` element allows you to specify a set of compatible targets to be used when restoring packages.</span></span> <span data-ttu-id="cc0e5-206">Je navržena k umožnění balíčků, které používají dotnet [TxM (cíl x přezdívka)](/nuget/schema/target-frameworks) pracovat s balíčky, které nejsou deklarovat dotnet TxM.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-206">It's designed to allow packages that use the dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) to operate with packages that don't declare a dotnet TxM.</span></span> <span data-ttu-id="cc0e5-207">Pokud váš projekt používá dotnet TxM, pak všechny balíčky, které závisí na musí také mít dotnet TxM, pokud přidáte `<PackageTargetFallback>` do projektu, aby bylo možné povolit platformy bez dotnet. aby bylo kompatibilní s dotnet.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-207">If your project uses the dotnet TxM, then all the packages it depends on must also have a dotnet TxM, unless you add the `<PackageTargetFallback>` to your project in order to allow non-dotnet platforms to be compatible with dotnet.</span></span> 

<span data-ttu-id="cc0e5-208">Následující příklad uvádí případech přejít pro všechny cíle ve vašem projektu:</span><span class="sxs-lookup"><span data-stu-id="cc0e5-208">The following example provides the fallbacks for all targets in your project:</span></span> 

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

<span data-ttu-id="cc0e5-209">Následující příklad určuje případech přejít jenom pro `netcoreapp1.0` cíl:</span><span class="sxs-lookup"><span data-stu-id="cc0e5-209">The following example specifies the fallbacks only for the `netcoreapp1.0` target:</span></span>

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp1.0'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="nuget-metadata-properties"></a><span data-ttu-id="cc0e5-210">Vlastnosti metadat NuGet</span><span class="sxs-lookup"><span data-stu-id="cc0e5-210">NuGet metadata properties</span></span>
<span data-ttu-id="cc0e5-211">S přechodem na nástroje MSbuild, byl přesunut vstupní metadata, která se používá při balení balíček NuGet z *project.json* k *.csproj* soubory.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-211">With the move to MSbuild, we have moved the input metadata that is used when packing a NuGet package from *project.json* to *.csproj* files.</span></span> <span data-ttu-id="cc0e5-212">Vstupní hodnoty jsou vlastnosti nástroje MSBuild, takže budou muset přejít v rámci `<PropertyGroup>` skupiny.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-212">The inputs are MSBuild properties so they have to go within a `<PropertyGroup>` group.</span></span> <span data-ttu-id="cc0e5-213">Následuje seznam vlastností, které se používají jako vstupy pro proces okolních při použití `dotnet pack` příkaz nebo `Pack` MSBuild cíle, který je součástí sady SDK.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-213">The following is the list of properties that are used as inputs to the packing process when using the `dotnet pack` command or the `Pack` MSBuild target that is part of the SDK.</span></span> 

### <a name="ispackable"></a><span data-ttu-id="cc0e5-214">IsPackable</span><span class="sxs-lookup"><span data-stu-id="cc0e5-214">IsPackable</span></span>
<span data-ttu-id="cc0e5-215">Logická hodnota, která určuje, zda lze zabalit projektu.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-215">A Boolean value that specifies whether the project can be packed.</span></span> <span data-ttu-id="cc0e5-216">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-216">The default value is `true`.</span></span> 

### <a name="packageversion"></a><span data-ttu-id="cc0e5-217">PackageVersion</span><span class="sxs-lookup"><span data-stu-id="cc0e5-217">PackageVersion</span></span>
<span data-ttu-id="cc0e5-218">Určuje verzi, která bude mít výsledný balíčku.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-218">Specifies the version that the resulting package will have.</span></span> <span data-ttu-id="cc0e5-219">Přijme všechny formy řetězec verze NuGet.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-219">Accepts all forms of NuGet version string.</span></span> <span data-ttu-id="cc0e5-220">Výchozí hodnota je hodnota `$(Version)`, která je vlastnosti `Version` v projektu.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-220">Default is the value of `$(Version)`, that is, of the property `Version` in the project.</span></span> 

### <a name="packageid"></a><span data-ttu-id="cc0e5-221">ID balíčku</span><span class="sxs-lookup"><span data-stu-id="cc0e5-221">PackageId</span></span>
<span data-ttu-id="cc0e5-222">Určuje název pro výsledný balíček.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-222">Specifies the name for the resulting package.</span></span> <span data-ttu-id="cc0e5-223">Pokud není zadáno, `pack` operace bude použita výchozí pomocí `AssemblyName` nebo název adresáře jako název balíčku.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-223">If not specified, the `pack` operation will default to using the `AssemblyName` or directory name as the name of the package.</span></span> 

### <a name="title"></a><span data-ttu-id="cc0e5-224">Název</span><span class="sxs-lookup"><span data-stu-id="cc0e5-224">Title</span></span>
<span data-ttu-id="cc0e5-225">Lidské popisný název balíčku, obvykle používaných v zobrazení uživatelského rozhraní na nuget.org a Správce balíčků v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-225">A human-friendly title of the package, typically used in UI displays as on nuget.org and the Package Manager in Visual Studio.</span></span> <span data-ttu-id="cc0e5-226">Pokud není zadáno, bude místo něj použita ID balíčku.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-226">If not specified, the package ID is used instead.</span></span>

### <a name="authors"></a><span data-ttu-id="cc0e5-227">Autoři</span><span class="sxs-lookup"><span data-stu-id="cc0e5-227">Authors</span></span>
<span data-ttu-id="cc0e5-228">Seznam balíčků autoři, odpovídající profil názvy v nuget.org oddělených středníkem. Tyto jsou zobrazeny v galerii NuGet v nuget.org a jsou používané pro křížovou balíčky autory stejné.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-228">A semicolon-separated list of packages authors, matching the profile names on nuget.org. These are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span>

### <a name="description"></a><span data-ttu-id="cc0e5-229">Popis</span><span class="sxs-lookup"><span data-stu-id="cc0e5-229">Description</span></span>
<span data-ttu-id="cc0e5-230">Dlouhý popis balíčku pro zobrazení uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-230">A long description of the package for UI display.</span></span>

### <a name="copyright"></a><span data-ttu-id="cc0e5-231">Copyright</span><span class="sxs-lookup"><span data-stu-id="cc0e5-231">Copyright</span></span>
<span data-ttu-id="cc0e5-232">Údaje o autorských právech pro balíček.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-232">Copyright details for the package.</span></span>

### <a name="packagerequirelicenseacceptance"></a><span data-ttu-id="cc0e5-233">PackageRequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="cc0e5-233">PackageRequireLicenseAcceptance</span></span>
<span data-ttu-id="cc0e5-234">Logická hodnota, která určuje, jestli klient musí zobrazovat výzvu k příjemce tak, aby přijímal licenční balíček před instalací balíčku.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-234">A Boolean value that specifies whether the client must prompt the consumer to accept the package license before installing the package.</span></span> <span data-ttu-id="cc0e5-235">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-235">The default is `false`.</span></span>

### <a name="packagelicenseurl"></a><span data-ttu-id="cc0e5-236">PackageLicenseUrl</span><span class="sxs-lookup"><span data-stu-id="cc0e5-236">PackageLicenseUrl</span></span>
<span data-ttu-id="cc0e5-237">Adresu URL licence, která se vztahuje na balíčku.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-237">An URL to the license that is applicable to the package.</span></span>

### <a name="packageprojecturl"></a><span data-ttu-id="cc0e5-238">PackageProjectUrl</span><span class="sxs-lookup"><span data-stu-id="cc0e5-238">PackageProjectUrl</span></span>
<span data-ttu-id="cc0e5-239">Zobrazí adresu URL pro domovskou stránku balíčku, často se zobrazí v uživatelském rozhraní a také nuget.org.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-239">A URL for the package's home page, often shown in UI displays as well as nuget.org.</span></span>

### <a name="packageiconurl"></a><span data-ttu-id="cc0e5-240">PackageIconUrl</span><span class="sxs-lookup"><span data-stu-id="cc0e5-240">PackageIconUrl</span></span>
<span data-ttu-id="cc0e5-241">Adresu URL pro bitovou kopii 64 x 64 s průhledným pozadím chcete použít jako ikonu balíčku v zobrazení uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-241">A URL for a 64x64 image with transparent background to use as the icon for the package in UI display.</span></span>

### <a name="packagereleasenotes"></a><span data-ttu-id="cc0e5-242">PackageReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="cc0e5-242">PackageReleaseNotes</span></span>
<span data-ttu-id="cc0e5-243">Poznámky k verzi pro balíček.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-243">Release notes for the package.</span></span>

### <a name="packagetags"></a><span data-ttu-id="cc0e5-244">PackageTags</span><span class="sxs-lookup"><span data-stu-id="cc0e5-244">PackageTags</span></span>
<span data-ttu-id="cc0e5-245">Seznam značek oddělených středníkem, který označuje balíčku.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-245">A semicolon-delimited list of tags that designates the package.</span></span>

### <a name="packageoutputpath"></a><span data-ttu-id="cc0e5-246">PackageOutputPath</span><span class="sxs-lookup"><span data-stu-id="cc0e5-246">PackageOutputPath</span></span>
<span data-ttu-id="cc0e5-247">Určuje výstupní cesta, ve kterém se zahodí sbalené balíčku.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-247">Determines the output path in which the packed package will be dropped.</span></span> <span data-ttu-id="cc0e5-248">Výchozí hodnota je `$(OutputPath)`.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-248">Default is `$(OutputPath)`.</span></span> 

### <a name="includesymbols"></a><span data-ttu-id="cc0e5-249">IncludeSymbols</span><span class="sxs-lookup"><span data-stu-id="cc0e5-249">IncludeSymbols</span></span>
<span data-ttu-id="cc0e5-250">Tato logická hodnota určuje, zda by měl balíček tehdy, když je zabalit projektu vytvoření balíčku další symboly.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-250">This Boolean value indicates whether the package should create an additional symbols package when the project is packed.</span></span> <span data-ttu-id="cc0e5-251">Bude mít tento balíček *. symbols.nupkg* rozšíření a bude kopírovat soubory PDB společně s knihovnou DLL a ostatní výstupní soubory.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-251">This package will have a *.symbols.nupkg* extension and will copy the PDB files along with the DLL and other output files.</span></span>

### <a name="includesource"></a><span data-ttu-id="cc0e5-252">IncludeSource</span><span class="sxs-lookup"><span data-stu-id="cc0e5-252">IncludeSource</span></span>
<span data-ttu-id="cc0e5-253">Tato logická hodnota určuje, jestli proces pack by měl vytvořit zdroj balíčku.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-253">This Boolean value indicates whether the pack process should create a source package.</span></span> <span data-ttu-id="cc0e5-254">Zdrojový balíček obsahuje knihovny zdrojového kódu a také soubory PDB.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-254">The source package contains the library's source code as well as PDB files.</span></span> <span data-ttu-id="cc0e5-255">Zdrojové soubory jsou umístěny v části `src/ProjectName` adresář ve výsledném souboru balíčku.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-255">Source files are put under the `src/ProjectName` directory in the resulting package file.</span></span> 

### <a name="istool"></a><span data-ttu-id="cc0e5-256">IsTool</span><span class="sxs-lookup"><span data-stu-id="cc0e5-256">IsTool</span></span>
<span data-ttu-id="cc0e5-257">Určuje, zda všechny výstupní soubory se zkopírují do *nástroje* složky místo *lib* složky.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-257">Specifies whether all output files are copied to the *tools* folder instead of the *lib* folder.</span></span> <span data-ttu-id="cc0e5-258">Všimněte si, že se to neliší od `DotNetCliTool` , která je určena podle nastavení `PackageType` v *.csproj* souboru.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-258">Note that this is different from a `DotNetCliTool` which is specified by setting the `PackageType` in the *.csproj* file.</span></span>

### <a name="repositoryurl"></a><span data-ttu-id="cc0e5-259">RepositoryUrl</span><span class="sxs-lookup"><span data-stu-id="cc0e5-259">RepositoryUrl</span></span>
<span data-ttu-id="cc0e5-260">Určuje adresu URL pro úložiště, kde se nachází zdrojový kód pro balíček nebo ze které je právě vytvořen.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-260">Specifies the URL for the repository where the source code for the package resides and/or from which it's being built.</span></span> 

### <a name="repositorytype"></a><span data-ttu-id="cc0e5-261">RepositoryType</span><span class="sxs-lookup"><span data-stu-id="cc0e5-261">RepositoryType</span></span>
<span data-ttu-id="cc0e5-262">Určuje typ úložiště.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-262">Specifies the type of the repository.</span></span> <span data-ttu-id="cc0e5-263">Výchozí hodnota je "git".</span><span class="sxs-lookup"><span data-stu-id="cc0e5-263">Default is "git".</span></span> 

### <a name="nopackageanalysis"></a><span data-ttu-id="cc0e5-264">NoPackageAnalysis</span><span class="sxs-lookup"><span data-stu-id="cc0e5-264">NoPackageAnalysis</span></span>
<span data-ttu-id="cc0e5-265">Určuje, že sada by neměl spustit analysis balíčku po vytvoření balíčku.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-265">Specifies that pack should not run package analysis after building the package.</span></span>

### <a name="minclientversion"></a><span data-ttu-id="cc0e5-266">MinClientVersion</span><span class="sxs-lookup"><span data-stu-id="cc0e5-266">MinClientVersion</span></span>
<span data-ttu-id="cc0e5-267">Určuje minimální verzi klienta NuGet, který můžete nainstalovat tento balíček vynucováno nuget.exe a Správce balíčků Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-267">Specifies the minimum version of the NuGet client that can install this package, enforced by nuget.exe and the Visual Studio Package Manager.</span></span>

### <a name="includebuildoutput"></a><span data-ttu-id="cc0e5-268">IncludeBuildOutput</span><span class="sxs-lookup"><span data-stu-id="cc0e5-268">IncludeBuildOutput</span></span>
<span data-ttu-id="cc0e5-269">Tato logické hodnoty Určuje, zda by měl sestavení výstupu sestavení do mnoha funkcemi *.nupkg* souboru nebo ne.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-269">This Boolean values specifies whether the build output assemblies should be packed into the *.nupkg* file or not.</span></span>

### <a name="includecontentinpack"></a><span data-ttu-id="cc0e5-270">IncludeContentInPack</span><span class="sxs-lookup"><span data-stu-id="cc0e5-270">IncludeContentInPack</span></span>
<span data-ttu-id="cc0e5-271">Tato logická hodnota určuje, zda všechny položky, které mají typ `Content` budou zahrnuty do výsledného balíček automaticky.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-271">This Boolean value specifies whether any items that have a type of `Content` will be included in the resulting package automatically.</span></span> <span data-ttu-id="cc0e5-272">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-272">The default is `true`.</span></span> 

### <a name="buildoutputtargetfolder"></a><span data-ttu-id="cc0e5-273">BuildOutputTargetFolder</span><span class="sxs-lookup"><span data-stu-id="cc0e5-273">BuildOutputTargetFolder</span></span>
<span data-ttu-id="cc0e5-274">Určuje složku, kam umístit výstupu sestavení.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-274">Specifies the folder where to place the output assemblies.</span></span> <span data-ttu-id="cc0e5-275">Výstup sestavení (a ostatní výstupní soubory) se zkopírují do jejich odpovídajících framework složky.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-275">The output assemblies (and other output files) are copied into their respective framework folders.</span></span>

### <a name="contenttargetfolders"></a><span data-ttu-id="cc0e5-276">ContentTargetFolders</span><span class="sxs-lookup"><span data-stu-id="cc0e5-276">ContentTargetFolders</span></span>
<span data-ttu-id="cc0e5-277">Tato vlastnost určuje, kde se má zobrazit všechny soubory obsahu, pokud výchozí umístění `PackagePath` není zadaný pro ně.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-277">This property specifies the default location of where all the content files should go if `PackagePath` is not specified for them.</span></span> <span data-ttu-id="cc0e5-278">Výchozí hodnota je "obsah; contentFiles".</span><span class="sxs-lookup"><span data-stu-id="cc0e5-278">The default value is "content;contentFiles".</span></span>

### <a name="nuspecfile"></a><span data-ttu-id="cc0e5-279">NuspecFile</span><span class="sxs-lookup"><span data-stu-id="cc0e5-279">NuspecFile</span></span>
<span data-ttu-id="cc0e5-280">Relativní nebo absolutní cesta k *příponou .nuspec* soubor používá pro okolních.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-280">Relative or absolute path to the *.nuspec* file being used for packing.</span></span> 

> [!NOTE]
> <span data-ttu-id="cc0e5-281">Pokud *příponou .nuspec* je zadán, použije se **výhradně** pro balení informace a všechny informace v projektech nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-281">If the *.nuspec* file is specified, it's used **exclusively** for packaging information and any information in the projects is not used.</span></span> 

### <a name="nuspecbasepath"></a><span data-ttu-id="cc0e5-282">NuspecBasePath</span><span class="sxs-lookup"><span data-stu-id="cc0e5-282">NuspecBasePath</span></span>
<span data-ttu-id="cc0e5-283">Základní cesta pro *příponou .nuspec* souboru.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-283">Base path for the *.nuspec* file.</span></span>

### <a name="nuspecproperties"></a><span data-ttu-id="cc0e5-284">NuspecProperties</span><span class="sxs-lookup"><span data-stu-id="cc0e5-284">NuspecProperties</span></span>
<span data-ttu-id="cc0e5-285">Středníky oddělený seznam klíč = hodnota páry.</span><span class="sxs-lookup"><span data-stu-id="cc0e5-285">Semicolon separated list of key=value pairs.</span></span>
