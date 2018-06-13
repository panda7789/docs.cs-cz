---
title: Přidání do formátu csproj pro .NET Core
description: Další informace o rozdílech mezi existující a .NET Core csproj soubory
author: blackdwarf
ms.author: mairaw
ms.date: 09/22/2017
ms.openlocfilehash: 1e356d0123328fe703f672c38cb5ee7799cb574c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218229"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a><span data-ttu-id="f61a5-103">Přidání do formátu csproj pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="f61a5-103">Additions to the csproj format for .NET Core</span></span>

<span data-ttu-id="f61a5-104">Tento dokument popisuje změny, které byly přidány do souborů projektu jako součást přesunutí ze *project.json* k *csproj* a [MSBuild](https://github.com/Microsoft/MSBuild).</span><span class="sxs-lookup"><span data-stu-id="f61a5-104">This document outlines the changes that were added to the project files as part of the move from *project.json* to *csproj* and [MSBuild](https://github.com/Microsoft/MSBuild).</span></span> <span data-ttu-id="f61a5-105">Další informace o syntaxi souboru obecné projektu a referenční informace najdete v tématu [soubor projektu nástroje MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="f61a5-105">For more information about general project file syntax and reference, see [the MSBuild project file](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation.</span></span>  

## <a name="implicit-package-references"></a><span data-ttu-id="f61a5-106">Implicitní balíček odkazuje</span><span class="sxs-lookup"><span data-stu-id="f61a5-106">Implicit package references</span></span>
<span data-ttu-id="f61a5-107">Metapackages odkazují implicitně podle framework(s) cíl zadaný v `<TargetFramework>` nebo `<TargetFrameworks>` vlastnost souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="f61a5-107">Metapackages are implicitly referenced based on the target framework(s) specified in the `<TargetFramework>` or `<TargetFrameworks>` property of your project file.</span></span> <span data-ttu-id="f61a5-108">`<TargetFrameworks>` je ignorována, pokud `<TargetFramework>` je zadaný, nezávisle na pořadí.</span><span class="sxs-lookup"><span data-stu-id="f61a5-108">`<TargetFrameworks>` is ignored if `<TargetFramework>` is specified, independent of order.</span></span>

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

### <a name="recommendations"></a><span data-ttu-id="f61a5-109">Doporučení</span><span class="sxs-lookup"><span data-stu-id="f61a5-109">Recommendations</span></span>
<span data-ttu-id="f61a5-110">Vzhledem k tomu `Microsoft.NETCore.App` nebo `NetStandard.Library` metapackages implicitně odkazují, naše doporučené osvědčené postupy jsou následující:</span><span class="sxs-lookup"><span data-stu-id="f61a5-110">Since `Microsoft.NETCore.App` or `NetStandard.Library` metapackages are implicitly referenced, the following are our recommended best practices:</span></span>

* <span data-ttu-id="f61a5-111">Pokud je cílem .NET Core nebo .NET Standard, nemusí explicitní odkaz na `Microsoft.NETCore.App` nebo `NetStandard.Library` metapackages prostřednictvím `<PackageReference>` položku v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="f61a5-111">When targeting .NET Core or .NET Standard, never have an explicit reference to the `Microsoft.NETCore.App` or `NetStandard.Library` metapackages via a `<PackageReference>` item in your project file.</span></span>
* <span data-ttu-id="f61a5-112">Pokud budete potřebovat na konkrétní verzi modulu runtime, pokud je cílem .NET Core, měli byste použít `<RuntimeFrameworkVersion>` vlastnost ve vašem projektu (například `1.0.4`) namísto odkazující metapackage.</span><span class="sxs-lookup"><span data-stu-id="f61a5-112">If you need a specific version of the runtime when targeting .NET Core, you should use the `<RuntimeFrameworkVersion>` property in your project (for example, `1.0.4`) instead of referencing the metapackage.</span></span>
    * <span data-ttu-id="f61a5-113">K tomu může dojít, pokud používáte [samostatná nasazení](../deploying/index.md#self-contained-deployments-scd) a je třeba daná oprava verzi 1.0.0 modul runtime LTS, např.</span><span class="sxs-lookup"><span data-stu-id="f61a5-113">This might happen if you are using [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) and you need a specific patch version of 1.0.0 LTS runtime, for example.</span></span>
* <span data-ttu-id="f61a5-114">Pokud potřebujete konkrétní verzi nástroje `NetStandard.Library` metapackage, pokud je cílem .NET Standard, můžete použít `<NetStandardImplicitPackageVersion>` vlastnost a sadu verze potřebujete.</span><span class="sxs-lookup"><span data-stu-id="f61a5-114">If you need a specific version of the `NetStandard.Library` metapackage when targeting .NET Standard, you can use the `<NetStandardImplicitPackageVersion>` property and set the version you need.</span></span>
* <span data-ttu-id="f61a5-115">Není explicitně přidat nebo aktualizovat odkazy na buď `Microsoft.NETCore.App` nebo `NetStandard.Library` metapackage v projektech pro rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f61a5-115">Don't explicitly add or update references to either the `Microsoft.NETCore.App` or `NetStandard.Library` metapackage in .NET Framework projects.</span></span> <span data-ttu-id="f61a5-116">Pokud všechny verze `NetStandard.Library` je potřeba, když pomocí balíčku NuGet .NET Standard na základě, NuGet automaticky instaluje tuto verzi.</span><span class="sxs-lookup"><span data-stu-id="f61a5-116">If any version of `NetStandard.Library` is needed when using a .NET Standard-based NuGet package, NuGet automatically installs that version.</span></span>

## <a name="default-compilation-includes-in-net-core-projects"></a><span data-ttu-id="f61a5-117">Výchozí kompilace zahrnuje v projektech .NET Core</span><span class="sxs-lookup"><span data-stu-id="f61a5-117">Default compilation includes in .NET Core projects</span></span>
<span data-ttu-id="f61a5-118">S přechodem na *csproj* formátu v nejnovější verze sady SDK sídla výchozí zahrnuje a vyloučí pro kompilaci položky a vložené prostředky k souborům vlastnosti SDK.</span><span class="sxs-lookup"><span data-stu-id="f61a5-118">With the move to the *csproj* format in the latest SDK versions, we've moved the default includes and excludes for compile items and embedded resources to the SDK properties files.</span></span> <span data-ttu-id="f61a5-119">To znamená, že už muset zadat tyto položky v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="f61a5-119">This means that you no longer need to specify these items in your project file.</span></span> 

<span data-ttu-id="f61a5-120">Hlavním důvodem tohoto postupu je přehlednost v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="f61a5-120">The main reason for doing this is to reduce the clutter in your project file.</span></span> <span data-ttu-id="f61a5-121">Výchozí hodnoty, které se nacházejí v sadě SDK by měly zahrnovat nejběžnější případy použití, takže není nutné je opakovat v každém projektu, který vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="f61a5-121">The defaults that are present in the SDK should cover most common use cases, so there is no need to repeat them in every project that you create.</span></span> <span data-ttu-id="f61a5-122">To vede k menší soubory projektu, které je mnohem snazší pochopit a také upravit ručně, v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="f61a5-122">This leads to smaller project files that are much easier to understand as well as edit by hand, if needed.</span></span> 

<span data-ttu-id="f61a5-123">Následující tabulka uvádí, které elementy a které [globs](https://en.wikipedia.org/wiki/Glob_(programming)) jsou zahrnuté i vyloučené v sadě SDK:</span><span class="sxs-lookup"><span data-stu-id="f61a5-123">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are both included and excluded in the SDK:</span></span> 

| <span data-ttu-id="f61a5-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="f61a5-124">Element</span></span>           | <span data-ttu-id="f61a5-125">Zahrnout glob</span><span class="sxs-lookup"><span data-stu-id="f61a5-125">Include glob</span></span>                              | <span data-ttu-id="f61a5-126">Vyloučit glob</span><span class="sxs-lookup"><span data-stu-id="f61a5-126">Exclude glob</span></span>                                                  | <span data-ttu-id="f61a5-127">Odebrat glob</span><span class="sxs-lookup"><span data-stu-id="f61a5-127">Remove glob</span></span>                |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| <span data-ttu-id="f61a5-128">Kompilace</span><span class="sxs-lookup"><span data-stu-id="f61a5-128">Compile</span></span>           | <span data-ttu-id="f61a5-129">\*\*/\*.cs (nebo jiné jazyková rozšíření)</span><span class="sxs-lookup"><span data-stu-id="f61a5-129">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="f61a5-130">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="f61a5-130">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="f61a5-131">Není k dispozici</span><span class="sxs-lookup"><span data-stu-id="f61a5-131">N/A</span></span>                        |
| <span data-ttu-id="f61a5-132">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="f61a5-132">EmbeddedResource</span></span>  | <span data-ttu-id="f61a5-133">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="f61a5-133">\*\*/\*.resx</span></span>                              | <span data-ttu-id="f61a5-134">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="f61a5-134">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="f61a5-135">Není k dispozici</span><span class="sxs-lookup"><span data-stu-id="f61a5-135">N/A</span></span>                        |
| <span data-ttu-id="f61a5-136">Žádné</span><span class="sxs-lookup"><span data-stu-id="f61a5-136">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="f61a5-137">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="f61a5-137">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="f61a5-138">- \*\*/\*.cs; \*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="f61a5-138">- \*\*/\*.cs; \*\*/\*.resx</span></span> |

<span data-ttu-id="f61a5-139">Pokud máte globs ve vašem projektu a pokusíte se sestavení pomocí nejnovější SDK, získáte následující chybě:</span><span class="sxs-lookup"><span data-stu-id="f61a5-139">If you have globs in your project and you try to build it using the newest SDK, you'll get the following error:</span></span>

> <span data-ttu-id="f61a5-140">Duplicitní položky kompilace byly zahrnuty.</span><span class="sxs-lookup"><span data-stu-id="f61a5-140">Duplicate Compile items were included.</span></span> <span data-ttu-id="f61a5-141">.NET SDK zahrnuje kompilace položky z adresáře projektu ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="f61a5-141">The .NET SDK includes Compile items from your project directory by default.</span></span> <span data-ttu-id="f61a5-142">Můžete tyto položky odebrat ze souboru projektu, nebo nastavte vlastnost 'EnableDefaultCompileItems' na hodnotu "false", pokud chcete výslovně nezahrnete v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="f61a5-142">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span> 

<span data-ttu-id="f61a5-143">Chcete-li získat vyřešit tuto chybu, můžete odebrat explicitní `Compile` položky, které odpovídají těm, které jsou uvedené v předchozí tabulce, nebo můžete nastavit `<EnableDefaultCompileItems>` vlastnost, která má `false`, podobné výjimky:</span><span class="sxs-lookup"><span data-stu-id="f61a5-143">In order to get around this error, you can either remove the explicit `Compile` items that match the ones listed on the previous table, or you can set the `<EnableDefaultCompileItems>` property to `false`, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```
<span data-ttu-id="f61a5-144">Nastavení této vlastnosti na `false` přepíší implicitní zahrnutí a chování se vrátí zpět na předchozí sady SDK, které jste museli zadat výchozí globs ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="f61a5-144">Setting this property to `false` will override implicit inclusion and the behavior will revert back to the previous SDKs where you had to specify the default globs in your project.</span></span> 

<span data-ttu-id="f61a5-145">Tato změna nedojde ke změně hlavní zahrnuje jiné mechanismy.</span><span class="sxs-lookup"><span data-stu-id="f61a5-145">This change does not modify the main mechanics of other includes.</span></span> <span data-ttu-id="f61a5-146">Ale pokud chcete určit, například některé soubory získat publikována s vaší aplikací, můžete pořád použít známé mechanismy v *csproj* pro tento (například `<Content>` element).</span><span class="sxs-lookup"><span data-stu-id="f61a5-146">However, if you wish to specify, for example, some files to get published with your app, you can still use the known mechanisms in *csproj* for that (for example, the `<Content>` element).</span></span>

<span data-ttu-id="f61a5-147">`<EnableDefaultCompileItems>` pouze zakáže `Compile` globs, ale nemá žádný vliv na ostatní globs, jako implicitní `None` glob, která se vztahuje také na \*.cs položky.</span><span class="sxs-lookup"><span data-stu-id="f61a5-147">`<EnableDefaultCompileItems>` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob, which also applies to \*.cs items.</span></span> <span data-ttu-id="f61a5-148">Z tohoto důvodu **Průzkumníku řešení** bude pokračovat zobrazit \*.cs položky v rámci projektu, které jsou zahrnuty jako `None` položky.</span><span class="sxs-lookup"><span data-stu-id="f61a5-148">Because of that, **Solution Explorer** will continue show \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="f61a5-149">Podobným způsobem, můžete použít `<EnableDefaultNoneItems>` zakázat implicitní `None` glob.</span><span class="sxs-lookup"><span data-stu-id="f61a5-149">In a similar way, you can use `<EnableDefaultNoneItems>` to disable the implicit `None` glob.</span></span>

<span data-ttu-id="f61a5-150">Chcete-li zakázat **všechny implicitní globs**, můžete nastavit `<EnableDefaultItems>` vlastnost `false` jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f61a5-150">To disable **all implicit globs**, you can set the `<EnableDefaultItems>` property to `false` as in the following example:</span></span>
```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

### <a name="recommendation"></a><span data-ttu-id="f61a5-151">Doporučení</span><span class="sxs-lookup"><span data-stu-id="f61a5-151">Recommendation</span></span>
<span data-ttu-id="f61a5-152">S csproj doporučujeme odebrat globs výchozí z projektu a přidávat jenom cesty k souborům s globs pro tyto artefakty, které vaše aplikace nebo knihovna potřebuje pro různé scénáře (například za běhu a vytváření balíčků NuGet).</span><span class="sxs-lookup"><span data-stu-id="f61a5-152">With csproj, we recommend that you remove the default globs from your project and only add file paths with globs for those artifacts that your app/library needs for various scenarios (for example, runtime and NuGet packaging).</span></span>

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a><span data-ttu-id="f61a5-153">Jak zjistit celý projekt jako MSBuild uvidí ho</span><span class="sxs-lookup"><span data-stu-id="f61a5-153">How to see the whole project as MSBuild sees it</span></span>

<span data-ttu-id="f61a5-154">Když tyto změny csproj výrazně zjednodušit soubory projektu, můžete chtít najdete v části plně rozšířené projektu jako MSBuild uvidí ho, jakmile jsou součástí sady SDK a jeho cíle.</span><span class="sxs-lookup"><span data-stu-id="f61a5-154">While those csproj changes greatly simplify project files, you might want to see the fully expanded project as MSBuild sees it once the SDK and its targets are included.</span></span> <span data-ttu-id="f61a5-155">Předběžné zpracování projektu s [ `/pp` přepínač](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) z [ `dotnet msbuild` ](dotnet-msbuild.md) příkaz, který ukazuje soubory, které jsou importovány, jejich zdroje a jejich příspěvky k sestavení bez ve skutečnosti sestavení projektu:</span><span class="sxs-lookup"><span data-stu-id="f61a5-155">Preprocess the project with [the `/pp` switch](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) of the [`dotnet msbuild`](dotnet-msbuild.md) command, which shows which files are imported, their sources, and their contributions to the build without actually building the project:</span></span>

`dotnet msbuild /pp:fullproject.xml`

<span data-ttu-id="f61a5-156">Pokud projekt má více cílové rozhraní, se musí výsledky příkazu zaměřit na pouze jeden z nich tak, že zadáte jako ve vlastnosti nástroje MSBuild:</span><span class="sxs-lookup"><span data-stu-id="f61a5-156">If the project has multiple target frameworks, the results of the command should be focused on only one of them by specifying it as an MSBuild property:</span></span>

`dotnet msbuild /p:TargetFramework=netcoreapp2.0 /pp:fullproject.xml`

## <a name="additions"></a><span data-ttu-id="f61a5-157">Přidání</span><span class="sxs-lookup"><span data-stu-id="f61a5-157">Additions</span></span>

### <a name="sdk-attribute"></a><span data-ttu-id="f61a5-158">Atribut SDK</span><span class="sxs-lookup"><span data-stu-id="f61a5-158">Sdk attribute</span></span> 
<span data-ttu-id="f61a5-159">`<Project>` Element *.csproj* soubor má nový atribut názvem `Sdk`.</span><span class="sxs-lookup"><span data-stu-id="f61a5-159">The `<Project>` element of the *.csproj* file has a new attribute called `Sdk`.</span></span> <span data-ttu-id="f61a5-160">`Sdk` Určuje, které SDK bude používán v projektu.</span><span class="sxs-lookup"><span data-stu-id="f61a5-160">`Sdk` specifies which SDK will be used by the project.</span></span> <span data-ttu-id="f61a5-161">Sadu SDK, jako [rozvrstvení dokumentu](cli-msbuild-architecture.md) popisuje, je sada MSBuild [úlohy](/visualstudio/msbuild/msbuild-tasks) a [cíle](/visualstudio/msbuild/msbuild-targets) , můžete vytvořit kódu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f61a5-161">The SDK, as the [layering document](cli-msbuild-architecture.md) describes, is a set of MSBuild [tasks](/visualstudio/msbuild/msbuild-tasks) and [targets](/visualstudio/msbuild/msbuild-targets) that can build .NET Core code.</span></span> <span data-ttu-id="f61a5-162">Jsme dodávat dvě hlavní sady SDK nástroje .NET Core:</span><span class="sxs-lookup"><span data-stu-id="f61a5-162">We ship two main SDKs with the .NET Core tools:</span></span>

1. <span data-ttu-id="f61a5-163">.NET Core SDK s ID `Microsoft.NET.Sdk`</span><span class="sxs-lookup"><span data-stu-id="f61a5-163">The .NET Core SDK with the ID of `Microsoft.NET.Sdk`</span></span>
2. <span data-ttu-id="f61a5-164">.NET Core web SDK s ID `Microsoft.NET.Sdk.Web`</span><span class="sxs-lookup"><span data-stu-id="f61a5-164">The .NET Core web SDK with the ID of `Microsoft.NET.Sdk.Web`</span></span>

<span data-ttu-id="f61a5-165">Je potřeba mít `Sdk` nastaven atribut na jednu z těchto ID na `<Project>` element Chcete-li použít nástroje .NET Core a sestavení kódu.</span><span class="sxs-lookup"><span data-stu-id="f61a5-165">You need to have the `Sdk` attribute set to one of those IDs on the `<Project>` element in order to use the .NET Core tools and build your code.</span></span> 

### <a name="packagereference"></a><span data-ttu-id="f61a5-166">PackageReference</span><span class="sxs-lookup"><span data-stu-id="f61a5-166">PackageReference</span></span>
<span data-ttu-id="f61a5-167">Položka, která určuje závislostí NuGet v projektu.</span><span class="sxs-lookup"><span data-stu-id="f61a5-167">Item that specifies a NuGet dependency in the project.</span></span> <span data-ttu-id="f61a5-168">`Include` Atribut určuje ID balíčku.</span><span class="sxs-lookup"><span data-stu-id="f61a5-168">The `Include` attribute specifies the package ID.</span></span> 

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a><span data-ttu-id="f61a5-169">Version</span><span class="sxs-lookup"><span data-stu-id="f61a5-169">Version</span></span>
<span data-ttu-id="f61a5-170">`Version` Určuje verzi balíčku, který má obnovit.</span><span class="sxs-lookup"><span data-stu-id="f61a5-170">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="f61a5-171">Atribut respektuje pravidla [verze NuGet](/nuget/create-packages/dependency-versions#version-ranges) schéma.</span><span class="sxs-lookup"><span data-stu-id="f61a5-171">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="f61a5-172">Výchozí chování je v případě shody přesnou verzi.</span><span class="sxs-lookup"><span data-stu-id="f61a5-172">The default behavior is an exact version match.</span></span> <span data-ttu-id="f61a5-173">Například zadání `Version="1.2.3"` je ekvivalentní NuGet zápis `[1.2.3]` pro přesnou 1.2.3 verze balíčku.</span><span class="sxs-lookup"><span data-stu-id="f61a5-173">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

#### <a name="includeassets-excludeassets-and-privateassets"></a><span data-ttu-id="f61a5-174">IncludeAssets, ExcludeAssets a PrivateAssets</span><span class="sxs-lookup"><span data-stu-id="f61a5-174">IncludeAssets, ExcludeAssets and PrivateAssets</span></span>
<span data-ttu-id="f61a5-175">`IncludeAssets` atribut určuje, jaké prostředky, které patří do balíčku určeného `<PackageReference>` by měl být využívány.</span><span class="sxs-lookup"><span data-stu-id="f61a5-175">`IncludeAssets` attribute specifies what assets belonging to the package specified by `<PackageReference>` should be consumed.</span></span> 

<span data-ttu-id="f61a5-176">`ExcludeAssets` atribut určuje, jaké prostředky, které patří do balíčku určeného `<PackageReference>` by neměl být využívány.</span><span class="sxs-lookup"><span data-stu-id="f61a5-176">`ExcludeAssets` attribute specifies what assets belonging to the package specified by `<PackageReference>` should not be consumed.</span></span>

<span data-ttu-id="f61a5-177">`PrivateAssets` atribut určuje, jaké prostředky, které patří do balíčku určeného `<PackageReference>` by měl být využívány ale, že by neměl toku do další projektu.</span><span class="sxs-lookup"><span data-stu-id="f61a5-177">`PrivateAssets` attribute specifies what assets belonging to the package specified by `<PackageReference>` should be consumed but that they should not flow to the next project.</span></span> 

> [!NOTE]
> <span data-ttu-id="f61a5-178">`PrivateAssets` je ekvivalentní *project.json*/*xproj* `SuppressParent` element.</span><span class="sxs-lookup"><span data-stu-id="f61a5-178">`PrivateAssets` is equivalent to the *project.json*/*xproj* `SuppressParent` element.</span></span>

<span data-ttu-id="f61a5-179">Tyto atributy mohou obsahovat jednu nebo více z následujících položek:</span><span class="sxs-lookup"><span data-stu-id="f61a5-179">These attributes can contain one or more of the following items:</span></span>

* <span data-ttu-id="f61a5-180">`Compile` – jsou k dispozici ke kompilaci proti obsah složky lib.</span><span class="sxs-lookup"><span data-stu-id="f61a5-180">`Compile` – the contents of the lib folder are available to compile against.</span></span>
* <span data-ttu-id="f61a5-181">`Runtime` – distribuují obsah složky modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="f61a5-181">`Runtime` – the contents of the runtime folder are distributed.</span></span>
* <span data-ttu-id="f61a5-182">`ContentFiles` – obsah *contentfiles* složky se používá.</span><span class="sxs-lookup"><span data-stu-id="f61a5-182">`ContentFiles` – the contents of the *contentfiles* folder are used.</span></span>
* <span data-ttu-id="f61a5-183">`Build` – props/cíle ve složce sestavení se používají.</span><span class="sxs-lookup"><span data-stu-id="f61a5-183">`Build` – the props/targets in the build folder are used.</span></span>
* <span data-ttu-id="f61a5-184">`Native` – obsah z nativní prostředky se zkopírují do výstupní složky pro modul runtime.</span><span class="sxs-lookup"><span data-stu-id="f61a5-184">`Native` – the contents from native assets are copied to the output folder for runtime.</span></span>
* <span data-ttu-id="f61a5-185">`Analyzers` – Analyzátory se používají.</span><span class="sxs-lookup"><span data-stu-id="f61a5-185">`Analyzers` – the analyzers are used.</span></span>

<span data-ttu-id="f61a5-186">Alternativně může obsahovat atribut:</span><span class="sxs-lookup"><span data-stu-id="f61a5-186">Alternatively, the attribute can contain:</span></span>

* <span data-ttu-id="f61a5-187">`None` – žádné prostředky se používají.</span><span class="sxs-lookup"><span data-stu-id="f61a5-187">`None` – none of the assets are used.</span></span>
* <span data-ttu-id="f61a5-188">`All` – všechny prostředky používají.</span><span class="sxs-lookup"><span data-stu-id="f61a5-188">`All` – all assets are used.</span></span>

### <a name="dotnetclitoolreference"></a><span data-ttu-id="f61a5-189">DotNetCliToolReference</span><span class="sxs-lookup"><span data-stu-id="f61a5-189">DotNetCliToolReference</span></span>
<span data-ttu-id="f61a5-190">`<DotNetCliToolReference>` Item – prvek určuje nástroj příkazového řádku, který chce uživatel obnovit v kontextu projektu.</span><span class="sxs-lookup"><span data-stu-id="f61a5-190">`<DotNetCliToolReference>` item element specifies the CLI tool that the user wants to restore in the context of the project.</span></span> <span data-ttu-id="f61a5-191">Je to náhrada za `tools` uzlu v *project.json*.</span><span class="sxs-lookup"><span data-stu-id="f61a5-191">It's a replacement for the `tools` node in *project.json*.</span></span> 

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

#### <a name="version"></a><span data-ttu-id="f61a5-192">Version</span><span class="sxs-lookup"><span data-stu-id="f61a5-192">Version</span></span>
<span data-ttu-id="f61a5-193">`Version` Určuje verzi balíčku, který má obnovit.</span><span class="sxs-lookup"><span data-stu-id="f61a5-193">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="f61a5-194">Atribut respektuje pravidla [verze NuGet](/nuget/create-packages/dependency-versions#version-ranges) schéma.</span><span class="sxs-lookup"><span data-stu-id="f61a5-194">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="f61a5-195">Výchozí chování je v případě shody přesnou verzi.</span><span class="sxs-lookup"><span data-stu-id="f61a5-195">The default behavior is an exact version match.</span></span> <span data-ttu-id="f61a5-196">Například zadání `Version="1.2.3"` je ekvivalentní NuGet zápis `[1.2.3]` pro přesnou 1.2.3 verze balíčku.</span><span class="sxs-lookup"><span data-stu-id="f61a5-196">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

### <a name="runtimeidentifiers"></a><span data-ttu-id="f61a5-197">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="f61a5-197">RuntimeIdentifiers</span></span>
<span data-ttu-id="f61a5-198">`<RuntimeIdentifiers>` Vám umožňuje určit seznam oddělený středníkem [Runtime identifikátorů (RID)](../rid-catalog.md) pro projekt.</span><span class="sxs-lookup"><span data-stu-id="f61a5-198">The `<RuntimeIdentifiers>` element lets you specify a semicolon-delimited list of [Runtime Identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="f61a5-199">Povolit identifikátorů RID publikování samostatná nasazení.</span><span class="sxs-lookup"><span data-stu-id="f61a5-199">RIDs enable publishing a self-contained deployments.</span></span> 

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a><span data-ttu-id="f61a5-200">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="f61a5-200">RuntimeIdentifier</span></span>
<span data-ttu-id="f61a5-201">`<RuntimeIdentifier>` Element umožňuje určit pouze jeden [identifikátor Runtime (RID)](../rid-catalog.md) pro projekt.</span><span class="sxs-lookup"><span data-stu-id="f61a5-201">The `<RuntimeIdentifier>` element allows you to specify only one [Runtime Identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="f61a5-202">Povolit identifikátorů RID publikování samostatná nasazení.</span><span class="sxs-lookup"><span data-stu-id="f61a5-202">RIDs enable publishing a self-contained deployment.</span></span> 

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

### <a name="packagetargetfallback"></a><span data-ttu-id="f61a5-203">PackageTargetFallback</span><span class="sxs-lookup"><span data-stu-id="f61a5-203">PackageTargetFallback</span></span> 
<span data-ttu-id="f61a5-204">`<PackageTargetFallback>` Element umožňuje určit sadu kompatibilní cíle, který se má použít při obnovování balíčků.</span><span class="sxs-lookup"><span data-stu-id="f61a5-204">The `<PackageTargetFallback>` element allows you to specify a set of compatible targets to be used when restoring packages.</span></span> <span data-ttu-id="f61a5-205">Je navržena k umožnění balíčků, které používají dotnet [TxM (cíl x přezdívka)](/nuget/schema/target-frameworks) pracovat s balíčky, které nejsou deklarovat dotnet TxM.</span><span class="sxs-lookup"><span data-stu-id="f61a5-205">It's designed to allow packages that use the dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) to operate with packages that don't declare a dotnet TxM.</span></span> <span data-ttu-id="f61a5-206">Pokud váš projekt používá dotnet TxM, pak všechny balíčky, které závisí na musí také mít dotnet TxM, pokud přidáte `<PackageTargetFallback>` do projektu, aby bylo možné povolit platformy bez dotnet. aby bylo kompatibilní s dotnet.</span><span class="sxs-lookup"><span data-stu-id="f61a5-206">If your project uses the dotnet TxM, then all the packages it depends on must also have a dotnet TxM, unless you add the `<PackageTargetFallback>` to your project in order to allow non-dotnet platforms to be compatible with dotnet.</span></span> 

<span data-ttu-id="f61a5-207">Následující příklad uvádí případech přejít pro všechny cíle ve vašem projektu:</span><span class="sxs-lookup"><span data-stu-id="f61a5-207">The following example provides the fallbacks for all targets in your project:</span></span> 

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

<span data-ttu-id="f61a5-208">Následující příklad určuje případech přejít jenom pro `netcoreapp1.0` cíl:</span><span class="sxs-lookup"><span data-stu-id="f61a5-208">The following example specifies the fallbacks only for the `netcoreapp1.0` target:</span></span>

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp1.0'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="nuget-metadata-properties"></a><span data-ttu-id="f61a5-209">Vlastnosti metadat NuGet</span><span class="sxs-lookup"><span data-stu-id="f61a5-209">NuGet metadata properties</span></span>
<span data-ttu-id="f61a5-210">S přechodem na nástroje MSbuild, byl přesunut vstupní metadata, která se používá při balení balíček NuGet z *project.json* k *.csproj* soubory.</span><span class="sxs-lookup"><span data-stu-id="f61a5-210">With the move to MSbuild, we have moved the input metadata that is used when packing a NuGet package from *project.json* to *.csproj* files.</span></span> <span data-ttu-id="f61a5-211">Vstupní hodnoty jsou vlastnosti nástroje MSBuild, takže budou muset přejít v rámci `<PropertyGroup>` skupiny.</span><span class="sxs-lookup"><span data-stu-id="f61a5-211">The inputs are MSBuild properties so they have to go within a `<PropertyGroup>` group.</span></span> <span data-ttu-id="f61a5-212">Následuje seznam vlastností, které se používají jako vstupy pro proces okolních při použití `dotnet pack` příkaz nebo `Pack` MSBuild cíle, který je součástí sady SDK.</span><span class="sxs-lookup"><span data-stu-id="f61a5-212">The following is the list of properties that are used as inputs to the packing process when using the `dotnet pack` command or the `Pack` MSBuild target that is part of the SDK.</span></span> 

### <a name="ispackable"></a><span data-ttu-id="f61a5-213">IsPackable</span><span class="sxs-lookup"><span data-stu-id="f61a5-213">IsPackable</span></span>
<span data-ttu-id="f61a5-214">Logická hodnota, která určuje, zda lze zabalit projektu.</span><span class="sxs-lookup"><span data-stu-id="f61a5-214">A Boolean value that specifies whether the project can be packed.</span></span> <span data-ttu-id="f61a5-215">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="f61a5-215">The default value is `true`.</span></span> 

### <a name="packageversion"></a><span data-ttu-id="f61a5-216">PackageVersion</span><span class="sxs-lookup"><span data-stu-id="f61a5-216">PackageVersion</span></span>
<span data-ttu-id="f61a5-217">Určuje verzi, která bude mít výsledný balíčku.</span><span class="sxs-lookup"><span data-stu-id="f61a5-217">Specifies the version that the resulting package will have.</span></span> <span data-ttu-id="f61a5-218">Přijme všechny formy řetězec verze NuGet.</span><span class="sxs-lookup"><span data-stu-id="f61a5-218">Accepts all forms of NuGet version string.</span></span> <span data-ttu-id="f61a5-219">Výchozí hodnota je hodnota `$(Version)`, která je vlastnosti `Version` v projektu.</span><span class="sxs-lookup"><span data-stu-id="f61a5-219">Default is the value of `$(Version)`, that is, of the property `Version` in the project.</span></span> 

### <a name="packageid"></a><span data-ttu-id="f61a5-220">ID balíčku</span><span class="sxs-lookup"><span data-stu-id="f61a5-220">PackageId</span></span>
<span data-ttu-id="f61a5-221">Určuje název pro výsledný balíček.</span><span class="sxs-lookup"><span data-stu-id="f61a5-221">Specifies the name for the resulting package.</span></span> <span data-ttu-id="f61a5-222">Pokud není zadáno, `pack` operace bude použita výchozí pomocí `AssemblyName` nebo název adresáře jako název balíčku.</span><span class="sxs-lookup"><span data-stu-id="f61a5-222">If not specified, the `pack` operation will default to using the `AssemblyName` or directory name as the name of the package.</span></span> 

### <a name="title"></a><span data-ttu-id="f61a5-223">Název</span><span class="sxs-lookup"><span data-stu-id="f61a5-223">Title</span></span>
<span data-ttu-id="f61a5-224">Lidské popisný název balíčku, obvykle používaných v zobrazení uživatelského rozhraní na nuget.org a Správce balíčků v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f61a5-224">A human-friendly title of the package, typically used in UI displays as on nuget.org and the Package Manager in Visual Studio.</span></span> <span data-ttu-id="f61a5-225">Pokud není zadáno, bude místo něj použita ID balíčku.</span><span class="sxs-lookup"><span data-stu-id="f61a5-225">If not specified, the package ID is used instead.</span></span>

### <a name="authors"></a><span data-ttu-id="f61a5-226">Autoři</span><span class="sxs-lookup"><span data-stu-id="f61a5-226">Authors</span></span>
<span data-ttu-id="f61a5-227">Seznam balíčků autoři, odpovídající profil názvy v nuget.org oddělených středníkem. Tyto jsou zobrazeny v galerii NuGet v nuget.org a jsou používané pro křížovou balíčky autory stejné.</span><span class="sxs-lookup"><span data-stu-id="f61a5-227">A semicolon-separated list of packages authors, matching the profile names on nuget.org. These are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span>

### <a name="description"></a><span data-ttu-id="f61a5-228">Popis</span><span class="sxs-lookup"><span data-stu-id="f61a5-228">Description</span></span>
<span data-ttu-id="f61a5-229">Dlouhý popis balíčku pro zobrazení uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f61a5-229">A long description of the package for UI display.</span></span>

### <a name="copyright"></a><span data-ttu-id="f61a5-230">Copyright</span><span class="sxs-lookup"><span data-stu-id="f61a5-230">Copyright</span></span>
<span data-ttu-id="f61a5-231">Údaje o autorských právech pro balíček.</span><span class="sxs-lookup"><span data-stu-id="f61a5-231">Copyright details for the package.</span></span>

### <a name="packagerequirelicenseacceptance"></a><span data-ttu-id="f61a5-232">PackageRequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="f61a5-232">PackageRequireLicenseAcceptance</span></span>
<span data-ttu-id="f61a5-233">Logická hodnota, která určuje, jestli klient musí zobrazovat výzvu k příjemce tak, aby přijímal licenční balíček před instalací balíčku.</span><span class="sxs-lookup"><span data-stu-id="f61a5-233">A Boolean value that specifies whether the client must prompt the consumer to accept the package license before installing the package.</span></span> <span data-ttu-id="f61a5-234">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="f61a5-234">The default is `false`.</span></span>

### <a name="packagelicenseurl"></a><span data-ttu-id="f61a5-235">PackageLicenseUrl</span><span class="sxs-lookup"><span data-stu-id="f61a5-235">PackageLicenseUrl</span></span>
<span data-ttu-id="f61a5-236">Adresu URL licence, která se vztahuje na balíčku.</span><span class="sxs-lookup"><span data-stu-id="f61a5-236">An URL to the license that is applicable to the package.</span></span>

### <a name="packageprojecturl"></a><span data-ttu-id="f61a5-237">PackageProjectUrl</span><span class="sxs-lookup"><span data-stu-id="f61a5-237">PackageProjectUrl</span></span>
<span data-ttu-id="f61a5-238">Zobrazí adresu URL pro domovskou stránku balíčku, často se zobrazí v uživatelském rozhraní a také nuget.org.</span><span class="sxs-lookup"><span data-stu-id="f61a5-238">A URL for the package's home page, often shown in UI displays as well as nuget.org.</span></span>

### <a name="packageiconurl"></a><span data-ttu-id="f61a5-239">PackageIconUrl</span><span class="sxs-lookup"><span data-stu-id="f61a5-239">PackageIconUrl</span></span>
<span data-ttu-id="f61a5-240">Adresu URL pro bitovou kopii 64 x 64 s průhledným pozadím chcete použít jako ikonu balíčku v zobrazení uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f61a5-240">A URL for a 64x64 image with transparent background to use as the icon for the package in UI display.</span></span>

### <a name="packagereleasenotes"></a><span data-ttu-id="f61a5-241">PackageReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="f61a5-241">PackageReleaseNotes</span></span>
<span data-ttu-id="f61a5-242">Poznámky k verzi pro balíček.</span><span class="sxs-lookup"><span data-stu-id="f61a5-242">Release notes for the package.</span></span>

### <a name="packagetags"></a><span data-ttu-id="f61a5-243">PackageTags</span><span class="sxs-lookup"><span data-stu-id="f61a5-243">PackageTags</span></span>
<span data-ttu-id="f61a5-244">Seznam značek oddělených středníkem, který označuje balíčku.</span><span class="sxs-lookup"><span data-stu-id="f61a5-244">A semicolon-delimited list of tags that designates the package.</span></span>

### <a name="packageoutputpath"></a><span data-ttu-id="f61a5-245">PackageOutputPath</span><span class="sxs-lookup"><span data-stu-id="f61a5-245">PackageOutputPath</span></span>
<span data-ttu-id="f61a5-246">Určuje výstupní cesta, ve kterém se zahodí sbalené balíčku.</span><span class="sxs-lookup"><span data-stu-id="f61a5-246">Determines the output path in which the packed package will be dropped.</span></span> <span data-ttu-id="f61a5-247">Výchozí hodnota je `$(OutputPath)`.</span><span class="sxs-lookup"><span data-stu-id="f61a5-247">Default is `$(OutputPath)`.</span></span> 

### <a name="includesymbols"></a><span data-ttu-id="f61a5-248">IncludeSymbols</span><span class="sxs-lookup"><span data-stu-id="f61a5-248">IncludeSymbols</span></span>
<span data-ttu-id="f61a5-249">Tato logická hodnota určuje, zda by měl balíček tehdy, když je zabalit projektu vytvoření balíčku další symboly.</span><span class="sxs-lookup"><span data-stu-id="f61a5-249">This Boolean value indicates whether the package should create an additional symbols package when the project is packed.</span></span> <span data-ttu-id="f61a5-250">Bude mít tento balíček *. symbols.nupkg* rozšíření a bude kopírovat soubory PDB společně s knihovnou DLL a ostatní výstupní soubory.</span><span class="sxs-lookup"><span data-stu-id="f61a5-250">This package will have a *.symbols.nupkg* extension and will copy the PDB files along with the DLL and other output files.</span></span>

### <a name="includesource"></a><span data-ttu-id="f61a5-251">IncludeSource</span><span class="sxs-lookup"><span data-stu-id="f61a5-251">IncludeSource</span></span>
<span data-ttu-id="f61a5-252">Tato logická hodnota určuje, jestli proces pack by měl vytvořit zdroj balíčku.</span><span class="sxs-lookup"><span data-stu-id="f61a5-252">This Boolean value indicates whether the pack process should create a source package.</span></span> <span data-ttu-id="f61a5-253">Zdrojový balíček obsahuje knihovny zdrojového kódu a také soubory PDB.</span><span class="sxs-lookup"><span data-stu-id="f61a5-253">The source package contains the library's source code as well as PDB files.</span></span> <span data-ttu-id="f61a5-254">Zdrojové soubory jsou umístěny v části `src/ProjectName` adresář ve výsledném souboru balíčku.</span><span class="sxs-lookup"><span data-stu-id="f61a5-254">Source files are put under the `src/ProjectName` directory in the resulting package file.</span></span> 

### <a name="istool"></a><span data-ttu-id="f61a5-255">IsTool</span><span class="sxs-lookup"><span data-stu-id="f61a5-255">IsTool</span></span>
<span data-ttu-id="f61a5-256">Určuje, zda všechny výstupní soubory se zkopírují do *nástroje* složky místo *lib* složky.</span><span class="sxs-lookup"><span data-stu-id="f61a5-256">Specifies whether all output files are copied to the *tools* folder instead of the *lib* folder.</span></span> <span data-ttu-id="f61a5-257">Všimněte si, že se to neliší od `DotNetCliTool` , která je určena podle nastavení `PackageType` v *.csproj* souboru.</span><span class="sxs-lookup"><span data-stu-id="f61a5-257">Note that this is different from a `DotNetCliTool` which is specified by setting the `PackageType` in the *.csproj* file.</span></span>

### <a name="repositoryurl"></a><span data-ttu-id="f61a5-258">RepositoryUrl</span><span class="sxs-lookup"><span data-stu-id="f61a5-258">RepositoryUrl</span></span>
<span data-ttu-id="f61a5-259">Určuje adresu URL pro úložiště, kde se nachází zdrojový kód pro balíček nebo ze které je právě vytvořen.</span><span class="sxs-lookup"><span data-stu-id="f61a5-259">Specifies the URL for the repository where the source code for the package resides and/or from which it's being built.</span></span> 

### <a name="repositorytype"></a><span data-ttu-id="f61a5-260">RepositoryType</span><span class="sxs-lookup"><span data-stu-id="f61a5-260">RepositoryType</span></span>
<span data-ttu-id="f61a5-261">Určuje typ úložiště.</span><span class="sxs-lookup"><span data-stu-id="f61a5-261">Specifies the type of the repository.</span></span> <span data-ttu-id="f61a5-262">Výchozí hodnota je "git".</span><span class="sxs-lookup"><span data-stu-id="f61a5-262">Default is "git".</span></span> 

### <a name="nopackageanalysis"></a><span data-ttu-id="f61a5-263">NoPackageAnalysis</span><span class="sxs-lookup"><span data-stu-id="f61a5-263">NoPackageAnalysis</span></span>
<span data-ttu-id="f61a5-264">Určuje, že sada by neměl spustit analysis balíčku po vytvoření balíčku.</span><span class="sxs-lookup"><span data-stu-id="f61a5-264">Specifies that pack should not run package analysis after building the package.</span></span>

### <a name="minclientversion"></a><span data-ttu-id="f61a5-265">MinClientVersion</span><span class="sxs-lookup"><span data-stu-id="f61a5-265">MinClientVersion</span></span>
<span data-ttu-id="f61a5-266">Určuje minimální verzi klienta NuGet, který můžete nainstalovat tento balíček vynucováno nuget.exe a Správce balíčků Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f61a5-266">Specifies the minimum version of the NuGet client that can install this package, enforced by nuget.exe and the Visual Studio Package Manager.</span></span>

### <a name="includebuildoutput"></a><span data-ttu-id="f61a5-267">IncludeBuildOutput</span><span class="sxs-lookup"><span data-stu-id="f61a5-267">IncludeBuildOutput</span></span>
<span data-ttu-id="f61a5-268">Tato logické hodnoty Určuje, zda by měl sestavení výstupu sestavení do mnoha funkcemi *.nupkg* souboru nebo ne.</span><span class="sxs-lookup"><span data-stu-id="f61a5-268">This Boolean values specifies whether the build output assemblies should be packed into the *.nupkg* file or not.</span></span>

### <a name="includecontentinpack"></a><span data-ttu-id="f61a5-269">IncludeContentInPack</span><span class="sxs-lookup"><span data-stu-id="f61a5-269">IncludeContentInPack</span></span>
<span data-ttu-id="f61a5-270">Tato logická hodnota určuje, zda všechny položky, které mají typ `Content` budou zahrnuty do výsledného balíček automaticky.</span><span class="sxs-lookup"><span data-stu-id="f61a5-270">This Boolean value specifies whether any items that have a type of `Content` will be included in the resulting package automatically.</span></span> <span data-ttu-id="f61a5-271">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="f61a5-271">The default is `true`.</span></span> 

### <a name="buildoutputtargetfolder"></a><span data-ttu-id="f61a5-272">BuildOutputTargetFolder</span><span class="sxs-lookup"><span data-stu-id="f61a5-272">BuildOutputTargetFolder</span></span>
<span data-ttu-id="f61a5-273">Určuje složku, kam umístit výstupu sestavení.</span><span class="sxs-lookup"><span data-stu-id="f61a5-273">Specifies the folder where to place the output assemblies.</span></span> <span data-ttu-id="f61a5-274">Výstup sestavení (a ostatní výstupní soubory) se zkopírují do jejich odpovídajících framework složky.</span><span class="sxs-lookup"><span data-stu-id="f61a5-274">The output assemblies (and other output files) are copied into their respective framework folders.</span></span>

### <a name="contenttargetfolders"></a><span data-ttu-id="f61a5-275">ContentTargetFolders</span><span class="sxs-lookup"><span data-stu-id="f61a5-275">ContentTargetFolders</span></span>
<span data-ttu-id="f61a5-276">Tato vlastnost určuje, kde se má zobrazit všechny soubory obsahu, pokud výchozí umístění `PackagePath` není zadaný pro ně.</span><span class="sxs-lookup"><span data-stu-id="f61a5-276">This property specifies the default location of where all the content files should go if `PackagePath` is not specified for them.</span></span> <span data-ttu-id="f61a5-277">Výchozí hodnota je "obsah; contentFiles".</span><span class="sxs-lookup"><span data-stu-id="f61a5-277">The default value is "content;contentFiles".</span></span>

### <a name="nuspecfile"></a><span data-ttu-id="f61a5-278">NuspecFile</span><span class="sxs-lookup"><span data-stu-id="f61a5-278">NuspecFile</span></span>
<span data-ttu-id="f61a5-279">Relativní nebo absolutní cesta k *příponou .nuspec* soubor používá pro okolních.</span><span class="sxs-lookup"><span data-stu-id="f61a5-279">Relative or absolute path to the *.nuspec* file being used for packing.</span></span> 

> [!NOTE]
> <span data-ttu-id="f61a5-280">Pokud *příponou .nuspec* je zadán, použije se **výhradně** pro balení informace a všechny informace v projektech nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="f61a5-280">If the *.nuspec* file is specified, it's used **exclusively** for packaging information and any information in the projects is not used.</span></span> 

### <a name="nuspecbasepath"></a><span data-ttu-id="f61a5-281">NuspecBasePath</span><span class="sxs-lookup"><span data-stu-id="f61a5-281">NuspecBasePath</span></span>
<span data-ttu-id="f61a5-282">Základní cesta pro *příponou .nuspec* souboru.</span><span class="sxs-lookup"><span data-stu-id="f61a5-282">Base path for the *.nuspec* file.</span></span>

### <a name="nuspecproperties"></a><span data-ttu-id="f61a5-283">NuspecProperties</span><span class="sxs-lookup"><span data-stu-id="f61a5-283">NuspecProperties</span></span>
<span data-ttu-id="f61a5-284">Středníky oddělený seznam klíč = hodnota páry.</span><span class="sxs-lookup"><span data-stu-id="f61a5-284">Semicolon separated list of key=value pairs.</span></span>
