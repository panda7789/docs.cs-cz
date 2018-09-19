---
title: Dodatky k formátu csproj pro .NET Core
description: Další informace o rozdílech mezi stávající a soubory csproj .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 09/22/2017
ms.openlocfilehash: d868eb689af1d87ea2adb1f0069345cbb8195af7
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46004374"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a><span data-ttu-id="65e93-103">Dodatky k formátu csproj pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="65e93-103">Additions to the csproj format for .NET Core</span></span>

<span data-ttu-id="65e93-104">Tento dokument popisuje změny, které byly přidány do souborů projektu jako součást přesunu z *project.json* k *csproj* a [MSBuild](https://github.com/Microsoft/MSBuild).</span><span class="sxs-lookup"><span data-stu-id="65e93-104">This document outlines the changes that were added to the project files as part of the move from *project.json* to *csproj* and [MSBuild](https://github.com/Microsoft/MSBuild).</span></span> <span data-ttu-id="65e93-105">Další informace o syntaxi souboru obecné projektu a odkaz, naleznete v tématu [souboru projektu MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="65e93-105">For more information about general project file syntax and reference, see [the MSBuild project file](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation.</span></span>  

## <a name="implicit-package-references"></a><span data-ttu-id="65e93-106">Odkazy na implicitní balíček</span><span class="sxs-lookup"><span data-stu-id="65e93-106">Implicit package references</span></span>
<span data-ttu-id="65e93-107">Metabalíčky jsou implicitně odkazovat podle cílové architekturu podle `<TargetFramework>` nebo `<TargetFrameworks>` vlastnost souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="65e93-107">Metapackages are implicitly referenced based on the target framework(s) specified in the `<TargetFramework>` or `<TargetFrameworks>` property of your project file.</span></span> <span data-ttu-id="65e93-108">`<TargetFrameworks>` se ignoruje, pokud `<TargetFramework>` je zadaný, nezávisle na pořadí.</span><span class="sxs-lookup"><span data-stu-id="65e93-108">`<TargetFrameworks>` is ignored if `<TargetFramework>` is specified, independent of order.</span></span>

```xml
 <PropertyGroup>
   <TargetFramework>netcoreapp2.1</TargetFramework>
 </PropertyGroup>
 ```
 
 ```xml
 <PropertyGroup>
   <TargetFrameworks>netcoreapp2.1;net462</TargetFrameworks>
 </PropertyGroup>
 ```

### <a name="recommendations"></a><span data-ttu-id="65e93-109">Doporučení</span><span class="sxs-lookup"><span data-stu-id="65e93-109">Recommendations</span></span>
<span data-ttu-id="65e93-110">Protože `Microsoft.NETCore.App` nebo `NetStandard.Library` metabalíčky jsou implicitně odkazovat, naše doporučené osvědčené postupy jsou následující:</span><span class="sxs-lookup"><span data-stu-id="65e93-110">Since `Microsoft.NETCore.App` or `NetStandard.Library` metapackages are implicitly referenced, the following are our recommended best practices:</span></span>

* <span data-ttu-id="65e93-111">Při cílení na .NET Core nebo .NET Standard, nikdy nemůžete mít explicitní odkaz na `Microsoft.NETCore.App` nebo `NetStandard.Library` metabalíčky prostřednictvím `<PackageReference>` položky v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="65e93-111">When targeting .NET Core or .NET Standard, never have an explicit reference to the `Microsoft.NETCore.App` or `NetStandard.Library` metapackages via a `<PackageReference>` item in your project file.</span></span>
* <span data-ttu-id="65e93-112">Pokud potřebujete konkrétní verzi modulu runtime při cílení na .NET Core, měli byste použít `<RuntimeFrameworkVersion>` vlastnost v projektu (například `1.0.4`) namísto odkazování Microsoft.aspnetcore.all.</span><span class="sxs-lookup"><span data-stu-id="65e93-112">If you need a specific version of the runtime when targeting .NET Core, you should use the `<RuntimeFrameworkVersion>` property in your project (for example, `1.0.4`) instead of referencing the metapackage.</span></span>
    * <span data-ttu-id="65e93-113">K tomu může dojít, pokud používáte [samostatná nasazení](../deploying/index.md#self-contained-deployments-scd) a potřebujete oprav konkrétní verze 1.0.0 LTS běhu.</span><span class="sxs-lookup"><span data-stu-id="65e93-113">This might happen if you are using [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) and you need a specific patch version of 1.0.0 LTS runtime, for example.</span></span>
* <span data-ttu-id="65e93-114">Pokud potřebujete konkrétní verzi `NetStandard.Library` Microsoft.aspnetcore.all při cílení na .NET Standard, můžete použít `<NetStandardImplicitPackageVersion>` vlastnost a nastavte verzi budete potřebovat.</span><span class="sxs-lookup"><span data-stu-id="65e93-114">If you need a specific version of the `NetStandard.Library` metapackage when targeting .NET Standard, you can use the `<NetStandardImplicitPackageVersion>` property and set the version you need.</span></span>
* <span data-ttu-id="65e93-115">Není explicitně přidat nebo aktualizovat odkazy na buď `Microsoft.NETCore.App` nebo `NetStandard.Library` Microsoft.aspnetcore.all v projektech .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="65e93-115">Don't explicitly add or update references to either the `Microsoft.NETCore.App` or `NetStandard.Library` metapackage in .NET Framework projects.</span></span> <span data-ttu-id="65e93-116">Pokud všechny verze `NetStandard.Library` je potřeba při použití balíčku NuGet pro .NET Standard na základě, NuGet automaticky instaluje tuto verzi.</span><span class="sxs-lookup"><span data-stu-id="65e93-116">If any version of `NetStandard.Library` is needed when using a .NET Standard-based NuGet package, NuGet automatically installs that version.</span></span>

## <a name="default-compilation-includes-in-net-core-projects"></a><span data-ttu-id="65e93-117">Obsahuje výchozí kompilace v projektech .NET Core</span><span class="sxs-lookup"><span data-stu-id="65e93-117">Default compilation includes in .NET Core projects</span></span>
<span data-ttu-id="65e93-118">S přechodem na *csproj* formátu v nejnovější verze sady SDK, přešli jsme výchozí zahrnuje a nezahrnuje pro položky kompilace a vložené prostředky, které vlastnosti soubory sady SDK.</span><span class="sxs-lookup"><span data-stu-id="65e93-118">With the move to the *csproj* format in the latest SDK versions, we've moved the default includes and excludes for compile items and embedded resources to the SDK properties files.</span></span> <span data-ttu-id="65e93-119">To znamená, že už nemusíte určit tyto položky v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="65e93-119">This means that you no longer need to specify these items in your project file.</span></span> 

<span data-ttu-id="65e93-120">Hlavním důvodem pro to je přehlednost v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="65e93-120">The main reason for doing this is to reduce the clutter in your project file.</span></span> <span data-ttu-id="65e93-121">Výchozí hodnoty, které jsou k dispozici v sadě SDK by měly pokrývat nejběžnější případy použití, takže není nutné opakovat v každém projektu, který vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="65e93-121">The defaults that are present in the SDK should cover most common use cases, so there is no need to repeat them in every project that you create.</span></span> <span data-ttu-id="65e93-122">To vede k menší soubory projektu, které jsou mnohem snazší porozumět, stejně jako upravit ručně, v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="65e93-122">This leads to smaller project files that are much easier to understand as well as edit by hand, if needed.</span></span> 

<span data-ttu-id="65e93-123">V následující tabulce jsou uvedeny které elementy a které [globy](https://en.wikipedia.org/wiki/Glob_(programming)) jsou zahrnuté i vyloučené v sadě SDK:</span><span class="sxs-lookup"><span data-stu-id="65e93-123">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are both included and excluded in the SDK:</span></span> 

| <span data-ttu-id="65e93-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="65e93-124">Element</span></span>           | <span data-ttu-id="65e93-125">Zahrnout glob</span><span class="sxs-lookup"><span data-stu-id="65e93-125">Include glob</span></span>                              | <span data-ttu-id="65e93-126">Vyloučit glob</span><span class="sxs-lookup"><span data-stu-id="65e93-126">Exclude glob</span></span>                                                  | <span data-ttu-id="65e93-127">Odebrat glob</span><span class="sxs-lookup"><span data-stu-id="65e93-127">Remove glob</span></span>                |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| <span data-ttu-id="65e93-128">Kompilace</span><span class="sxs-lookup"><span data-stu-id="65e93-128">Compile</span></span>           | <span data-ttu-id="65e93-129">\*\*/\*.cs (nebo jiných jazykových rozšíření)</span><span class="sxs-lookup"><span data-stu-id="65e93-129">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="65e93-130">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="65e93-130">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="65e93-131">Není k dispozici</span><span class="sxs-lookup"><span data-stu-id="65e93-131">N/A</span></span>                        |
| <span data-ttu-id="65e93-132">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="65e93-132">EmbeddedResource</span></span>  | <span data-ttu-id="65e93-133">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="65e93-133">\*\*/\*.resx</span></span>                              | <span data-ttu-id="65e93-134">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="65e93-134">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="65e93-135">Není k dispozici</span><span class="sxs-lookup"><span data-stu-id="65e93-135">N/A</span></span>                        |
| <span data-ttu-id="65e93-136">Žádné</span><span class="sxs-lookup"><span data-stu-id="65e93-136">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="65e93-137">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="65e93-137">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="65e93-138">- \*\*/\*.cs; \*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="65e93-138">- \*\*/\*.cs; \*\*/\*.resx</span></span> |

<span data-ttu-id="65e93-139">Pokud máte globy ve vašem projektu a zkusíte sestavit pomocí nejnovější SDK, zobrazí se vám chybová zpráva:</span><span class="sxs-lookup"><span data-stu-id="65e93-139">If you have globs in your project and you try to build it using the newest SDK, you'll get the following error:</span></span>

> <span data-ttu-id="65e93-140">Duplicitní položky kompilace byly zahrnuty.</span><span class="sxs-lookup"><span data-stu-id="65e93-140">Duplicate Compile items were included.</span></span> <span data-ttu-id="65e93-141">Sady .NET SDK obsahuje ve výchozím nastavení kompilace položky z adresáře projektu.</span><span class="sxs-lookup"><span data-stu-id="65e93-141">The .NET SDK includes Compile items from your project directory by default.</span></span> <span data-ttu-id="65e93-142">Můžete tyto položky odebrat ze svého souboru projektu, nebo nastavte vlastnost 'EnableDefaultCompileItems' na hodnotu false' Pokud chcete explicitně zahrnout je do souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="65e93-142">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span> 

<span data-ttu-id="65e93-143">Aby bylo možné tuto chybu vyřešit, buď odstraněním explicitní `Compile` položky, které odpovídají těm, které jsou uvedené v předchozí tabulce, nebo můžete nastavit `<EnableDefaultCompileItems>` vlastnost `false`, tímto způsobem:</span><span class="sxs-lookup"><span data-stu-id="65e93-143">In order to get around this error, you can either remove the explicit `Compile` items that match the ones listed on the previous table, or you can set the `<EnableDefaultCompileItems>` property to `false`, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```
<span data-ttu-id="65e93-144">Nastavení této vlastnosti na `false` přepíše implicitního zahrnutí a chování se vrátí zpět na předchozí sady SDK, které jste museli zadat výchozí globy ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="65e93-144">Setting this property to `false` will override implicit inclusion and the behavior will revert back to the previous SDKs where you had to specify the default globs in your project.</span></span> 

<span data-ttu-id="65e93-145">Tato změna neprovede žádné změny v hlavním obsahuje jiné mechanismy.</span><span class="sxs-lookup"><span data-stu-id="65e93-145">This change does not modify the main mechanics of other includes.</span></span> <span data-ttu-id="65e93-146">Ale pokud chcete zadat, například některé soubory se publikovat s vaší aplikací, můžete stále použít známé mechanismy ve *csproj* pro daný (například `<Content>` element).</span><span class="sxs-lookup"><span data-stu-id="65e93-146">However, if you wish to specify, for example, some files to get published with your app, you can still use the known mechanisms in *csproj* for that (for example, the `<Content>` element).</span></span>

<span data-ttu-id="65e93-147">`<EnableDefaultCompileItems>` pouze zakáže `Compile` globy, ale nemá vliv na ostatní globy, jako jsou implicitní `None` glob, která se také vztahuje na \*.cs položky.</span><span class="sxs-lookup"><span data-stu-id="65e93-147">`<EnableDefaultCompileItems>` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob, which also applies to \*.cs items.</span></span> <span data-ttu-id="65e93-148">Proto **Průzkumníka řešení** bude dál zobrazovat \*.cs položky jako součást projektu, jako `None` položky.</span><span class="sxs-lookup"><span data-stu-id="65e93-148">Because of that, **Solution Explorer** will continue show \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="65e93-149">Podobným způsobem, můžete použít `<EnableDefaultNoneItems>` zakázat implicitní `None` glob.</span><span class="sxs-lookup"><span data-stu-id="65e93-149">In a similar way, you can use `<EnableDefaultNoneItems>` to disable the implicit `None` glob.</span></span>

<span data-ttu-id="65e93-150">Chcete-li zakázat **všechny implicitní globy**, můžete nastavit `<EnableDefaultItems>` vlastnost `false` jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="65e93-150">To disable **all implicit globs**, you can set the `<EnableDefaultItems>` property to `false` as in the following example:</span></span>
```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

### <a name="recommendation"></a><span data-ttu-id="65e93-151">Doporučení</span><span class="sxs-lookup"><span data-stu-id="65e93-151">Recommendation</span></span>
<span data-ttu-id="65e93-152">S csproj doporučujeme, abyste výchozí globy odeberte z projektu a přidat jenom cesty k souborům s globy pro tyto artefakty, které vaše aplikace/knihovna potřebuje pro různé scénáře (například modul runtime a zabalení NuGet).</span><span class="sxs-lookup"><span data-stu-id="65e93-152">With csproj, we recommend that you remove the default globs from your project and only add file paths with globs for those artifacts that your app/library needs for various scenarios (for example, runtime and NuGet packaging).</span></span>

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a><span data-ttu-id="65e93-153">Zobrazení celého projektu, jak ho uvidí MSBuild</span><span class="sxs-lookup"><span data-stu-id="65e93-153">How to see the whole project as MSBuild sees it</span></span>

<span data-ttu-id="65e93-154">Zatímco tyto změny csproj výrazně zjednodušit soubory projektu, můžete chtít zobrazit plně rozšířené projektu jako MSBuild ji vidí, jakmile jsou zahrnuty v sadě SDK a cíle.</span><span class="sxs-lookup"><span data-stu-id="65e93-154">While those csproj changes greatly simplify project files, you might want to see the fully expanded project as MSBuild sees it once the SDK and its targets are included.</span></span> <span data-ttu-id="65e93-155">Předběžné zpracování projektu s [ `/pp` přepnout](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) z [ `dotnet msbuild` ](dotnet-msbuild.md) příkaz, který ukazuje, které soubory se importují, jejich zdroje a svoje příspěvky k sestavení bez ve skutečnosti sestavení projektu:</span><span class="sxs-lookup"><span data-stu-id="65e93-155">Preprocess the project with [the `/pp` switch](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) of the [`dotnet msbuild`](dotnet-msbuild.md) command, which shows which files are imported, their sources, and their contributions to the build without actually building the project:</span></span>

`dotnet msbuild /pp:fullproject.xml`

<span data-ttu-id="65e93-156">Pokud projekt obsahuje více cílových platforem, by měl výsledky příkazu, zaměřuje na pouze jeden z nich tak, že zadáte jako vlastnost MSBuild:</span><span class="sxs-lookup"><span data-stu-id="65e93-156">If the project has multiple target frameworks, the results of the command should be focused on only one of them by specifying it as an MSBuild property:</span></span>

`dotnet msbuild /p:TargetFramework=netcoreapp2.0 /pp:fullproject.xml`

## <a name="additions"></a><span data-ttu-id="65e93-157">Přidání</span><span class="sxs-lookup"><span data-stu-id="65e93-157">Additions</span></span>

### <a name="sdk-attribute"></a><span data-ttu-id="65e93-158">Atribut SDK</span><span class="sxs-lookup"><span data-stu-id="65e93-158">Sdk attribute</span></span> 
<span data-ttu-id="65e93-159">`<Project>` Elementu *.csproj* soubor obsahuje nový atribut volá `Sdk`.</span><span class="sxs-lookup"><span data-stu-id="65e93-159">The `<Project>` element of the *.csproj* file has a new attribute called `Sdk`.</span></span> <span data-ttu-id="65e93-160">`Sdk` Určuje, které sada SDK se používá v projektu.</span><span class="sxs-lookup"><span data-stu-id="65e93-160">`Sdk` specifies which SDK will be used by the project.</span></span> <span data-ttu-id="65e93-161">Sady SDK, jako [rozvržení dokumentu](cli-msbuild-architecture.md) popisuje, je sada MSBuild [úlohy](/visualstudio/msbuild/msbuild-tasks) a [cíle](/visualstudio/msbuild/msbuild-targets) , které můžete vytvářet kód .NET Core.</span><span class="sxs-lookup"><span data-stu-id="65e93-161">The SDK, as the [layering document](cli-msbuild-architecture.md) describes, is a set of MSBuild [tasks](/visualstudio/msbuild/msbuild-tasks) and [targets](/visualstudio/msbuild/msbuild-targets) that can build .NET Core code.</span></span> <span data-ttu-id="65e93-162">Dodáváme dvě hlavní sady SDK s nástroji .NET Core:</span><span class="sxs-lookup"><span data-stu-id="65e93-162">We ship two main SDKs with the .NET Core tools:</span></span>

1. <span data-ttu-id="65e93-163">.NET Core SDK s ID `Microsoft.NET.Sdk`</span><span class="sxs-lookup"><span data-stu-id="65e93-163">The .NET Core SDK with the ID of `Microsoft.NET.Sdk`</span></span>
2. <span data-ttu-id="65e93-164">.NET Core web SDK s ID `Microsoft.NET.Sdk.Web`</span><span class="sxs-lookup"><span data-stu-id="65e93-164">The .NET Core web SDK with the ID of `Microsoft.NET.Sdk.Web`</span></span>

<span data-ttu-id="65e93-165">Je potřeba mít `Sdk` nastavený atribut na jednu z těchto ID na `<Project>` prvku abyste mohli použít nástroje pro .NET Core a vytváření kódu.</span><span class="sxs-lookup"><span data-stu-id="65e93-165">You need to have the `Sdk` attribute set to one of those IDs on the `<Project>` element in order to use the .NET Core tools and build your code.</span></span> 

### <a name="packagereference"></a><span data-ttu-id="65e93-166">PackageReference</span><span class="sxs-lookup"><span data-stu-id="65e93-166">PackageReference</span></span>
<span data-ttu-id="65e93-167">Položka, která určuje závislostí NuGet v projektu.</span><span class="sxs-lookup"><span data-stu-id="65e93-167">Item that specifies a NuGet dependency in the project.</span></span> <span data-ttu-id="65e93-168">`Include` Atribut určuje ID balíčku.</span><span class="sxs-lookup"><span data-stu-id="65e93-168">The `Include` attribute specifies the package ID.</span></span> 

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a><span data-ttu-id="65e93-169">Version</span><span class="sxs-lookup"><span data-stu-id="65e93-169">Version</span></span>
<span data-ttu-id="65e93-170">`Version` Určuje verzi balíčku, který se obnovit.</span><span class="sxs-lookup"><span data-stu-id="65e93-170">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="65e93-171">Atribut respektuje pravidla [správy verzí NuGet](/nuget/create-packages/dependency-versions#version-ranges) schéma.</span><span class="sxs-lookup"><span data-stu-id="65e93-171">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="65e93-172">Výchozí chování je shoda přesnou verzi.</span><span class="sxs-lookup"><span data-stu-id="65e93-172">The default behavior is an exact version match.</span></span> <span data-ttu-id="65e93-173">Například zadání `Version="1.2.3"` je ekvivalentní zápisu NuGet `[1.2.3]` pro přesné 1.2.3 verzi balíčku.</span><span class="sxs-lookup"><span data-stu-id="65e93-173">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

#### <a name="includeassets-excludeassets-and-privateassets"></a><span data-ttu-id="65e93-174">IncludeAssets, ExcludeAssets a PrivateAssets</span><span class="sxs-lookup"><span data-stu-id="65e93-174">IncludeAssets, ExcludeAssets and PrivateAssets</span></span>
<span data-ttu-id="65e93-175">`IncludeAssets` atribut určuje, jaké prostředky, které patří do balíčku určeného `<PackageReference>` by měl používat.</span><span class="sxs-lookup"><span data-stu-id="65e93-175">`IncludeAssets` attribute specifies what assets belonging to the package specified by `<PackageReference>` should be consumed.</span></span> 

<span data-ttu-id="65e93-176">`ExcludeAssets` atribut určuje, jaké prostředky, které patří do balíčku určeného `<PackageReference>` by neměla využívat.</span><span class="sxs-lookup"><span data-stu-id="65e93-176">`ExcludeAssets` attribute specifies what assets belonging to the package specified by `<PackageReference>` should not be consumed.</span></span>

<span data-ttu-id="65e93-177">`PrivateAssets` atribut určuje, jaké prostředky, které patří do balíčku určeného `<PackageReference>` by měl používat, ale, že by neměla posílat do příští projekt.</span><span class="sxs-lookup"><span data-stu-id="65e93-177">`PrivateAssets` attribute specifies what assets belonging to the package specified by `<PackageReference>` should be consumed but that they should not flow to the next project.</span></span> 

> [!NOTE]
> <span data-ttu-id="65e93-178">`PrivateAssets` je ekvivalentní *project.json*/*xproj* `SuppressParent` elementu.</span><span class="sxs-lookup"><span data-stu-id="65e93-178">`PrivateAssets` is equivalent to the *project.json*/*xproj* `SuppressParent` element.</span></span>

<span data-ttu-id="65e93-179">Tyto atributy mohou obsahovat jednu nebo více z následujících položek:</span><span class="sxs-lookup"><span data-stu-id="65e93-179">These attributes can contain one or more of the following items:</span></span>

* <span data-ttu-id="65e93-180">`Compile` – je možné kompilovat proti obsah složky lib.</span><span class="sxs-lookup"><span data-stu-id="65e93-180">`Compile` – the contents of the lib folder are available to compile against.</span></span>
* <span data-ttu-id="65e93-181">`Runtime` – obsah složky modulu runtime jsou distribuovány.</span><span class="sxs-lookup"><span data-stu-id="65e93-181">`Runtime` – the contents of the runtime folder are distributed.</span></span>
* <span data-ttu-id="65e93-182">`ContentFiles` – obsah *contentfiles* složky se používají.</span><span class="sxs-lookup"><span data-stu-id="65e93-182">`ContentFiles` – the contents of the *contentfiles* folder are used.</span></span>
* <span data-ttu-id="65e93-183">`Build` – vlastnosti a cíle ve složce sestavení se používají.</span><span class="sxs-lookup"><span data-stu-id="65e93-183">`Build` – the props/targets in the build folder are used.</span></span>
* <span data-ttu-id="65e93-184">`Native` – obsah z nativní prostředky se zkopíruje do výstupní složky pro modul runtime.</span><span class="sxs-lookup"><span data-stu-id="65e93-184">`Native` – the contents from native assets are copied to the output folder for runtime.</span></span>
* <span data-ttu-id="65e93-185">`Analyzers` – Analyzátory se používají.</span><span class="sxs-lookup"><span data-stu-id="65e93-185">`Analyzers` – the analyzers are used.</span></span>

<span data-ttu-id="65e93-186">Alternativně může obsahovat atribut:</span><span class="sxs-lookup"><span data-stu-id="65e93-186">Alternatively, the attribute can contain:</span></span>

* <span data-ttu-id="65e93-187">`None` – žádné prostředky se používají.</span><span class="sxs-lookup"><span data-stu-id="65e93-187">`None` – none of the assets are used.</span></span>
* <span data-ttu-id="65e93-188">`All` – všechny prostředky se používají.</span><span class="sxs-lookup"><span data-stu-id="65e93-188">`All` – all assets are used.</span></span>

### <a name="dotnetclitoolreference"></a><span data-ttu-id="65e93-189">DotNetCliToolReference</span><span class="sxs-lookup"><span data-stu-id="65e93-189">DotNetCliToolReference</span></span>
<span data-ttu-id="65e93-190">`<DotNetCliToolReference>` prvek položky určuje nástroj rozhraní příkazového řádku, který uživatel chce obnovit v kontextu projektu.</span><span class="sxs-lookup"><span data-stu-id="65e93-190">`<DotNetCliToolReference>` item element specifies the CLI tool that the user wants to restore in the context of the project.</span></span> <span data-ttu-id="65e93-191">Je náhradou za `tools` uzel v *project.json*.</span><span class="sxs-lookup"><span data-stu-id="65e93-191">It's a replacement for the `tools` node in *project.json*.</span></span> 

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

#### <a name="version"></a><span data-ttu-id="65e93-192">Version</span><span class="sxs-lookup"><span data-stu-id="65e93-192">Version</span></span>
<span data-ttu-id="65e93-193">`Version` Určuje verzi balíčku, který se obnovit.</span><span class="sxs-lookup"><span data-stu-id="65e93-193">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="65e93-194">Atribut respektuje pravidla [správy verzí NuGet](/nuget/create-packages/dependency-versions#version-ranges) schéma.</span><span class="sxs-lookup"><span data-stu-id="65e93-194">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="65e93-195">Výchozí chování je shoda přesnou verzi.</span><span class="sxs-lookup"><span data-stu-id="65e93-195">The default behavior is an exact version match.</span></span> <span data-ttu-id="65e93-196">Například zadání `Version="1.2.3"` je ekvivalentní zápisu NuGet `[1.2.3]` pro přesné 1.2.3 verzi balíčku.</span><span class="sxs-lookup"><span data-stu-id="65e93-196">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

### <a name="runtimeidentifiers"></a><span data-ttu-id="65e93-197">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="65e93-197">RuntimeIdentifiers</span></span>
<span data-ttu-id="65e93-198">`<RuntimeIdentifiers>` Element umožňuje určit seznam oddělený středníkem [Runtime identifikátorů (RID)](../rid-catalog.md) pro projekt.</span><span class="sxs-lookup"><span data-stu-id="65e93-198">The `<RuntimeIdentifiers>` element lets you specify a semicolon-delimited list of [Runtime Identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="65e93-199">Identifikátory RID povolit publikování samostatná nasazení.</span><span class="sxs-lookup"><span data-stu-id="65e93-199">RIDs enable publishing a self-contained deployments.</span></span> 

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a><span data-ttu-id="65e93-200">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="65e93-200">RuntimeIdentifier</span></span>
<span data-ttu-id="65e93-201">`<RuntimeIdentifier>` Element umožňuje určit pouze jeden [identifikátor modulu Runtime (RID)](../rid-catalog.md) pro projekt.</span><span class="sxs-lookup"><span data-stu-id="65e93-201">The `<RuntimeIdentifier>` element allows you to specify only one [Runtime Identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="65e93-202">Identifikátory RID povolit publikování samostatná nasazení.</span><span class="sxs-lookup"><span data-stu-id="65e93-202">RIDs enable publishing a self-contained deployment.</span></span> 

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

### <a name="packagetargetfallback"></a><span data-ttu-id="65e93-203">PackageTargetFallback</span><span class="sxs-lookup"><span data-stu-id="65e93-203">PackageTargetFallback</span></span> 
<span data-ttu-id="65e93-204">`<PackageTargetFallback>` Element slouží k určení sady cílů kompatibilní se použije při obnovování balíčků.</span><span class="sxs-lookup"><span data-stu-id="65e93-204">The `<PackageTargetFallback>` element allows you to specify a set of compatible targets to be used when restoring packages.</span></span> <span data-ttu-id="65e93-205">Je navržen tak, aby balíčky, které používají dotnet [TxM (Moniker cílového x)](/nuget/schema/target-frameworks) pracovat s balíčky, které není deklarovat dotnet TxM.</span><span class="sxs-lookup"><span data-stu-id="65e93-205">It's designed to allow packages that use the dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) to operate with packages that don't declare a dotnet TxM.</span></span> <span data-ttu-id="65e93-206">Pokud váš projekt používá dotnet TxM, pak všechny balíčky, které závisí na musí také mít dotnet TxM, pokud přidáte `<PackageTargetFallback>` do vašeho projektu, aby bylo možné povolit bez dotnet platformy se kvůli kompatibilitě s dotnet.</span><span class="sxs-lookup"><span data-stu-id="65e93-206">If your project uses the dotnet TxM, then all the packages it depends on must also have a dotnet TxM, unless you add the `<PackageTargetFallback>` to your project in order to allow non-dotnet platforms to be compatible with dotnet.</span></span> 

<span data-ttu-id="65e93-207">Následující příklad uvádí náhrad pro všechny cíle v projektu:</span><span class="sxs-lookup"><span data-stu-id="65e93-207">The following example provides the fallbacks for all targets in your project:</span></span> 

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

<span data-ttu-id="65e93-208">Následující příklad určuje náhrad pouze `netcoreapp2.1` cíl:</span><span class="sxs-lookup"><span data-stu-id="65e93-208">The following example specifies the fallbacks only for the `netcoreapp2.1` target:</span></span>

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp2.1'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="nuget-metadata-properties"></a><span data-ttu-id="65e93-209">Vlastnosti metadat NuGet</span><span class="sxs-lookup"><span data-stu-id="65e93-209">NuGet metadata properties</span></span>
<span data-ttu-id="65e93-210">S přechodem na MSbuild, přesunuli jsme vstupní metadata, která se používá při balení balíček NuGet *project.json* k *.csproj* soubory.</span><span class="sxs-lookup"><span data-stu-id="65e93-210">With the move to MSbuild, we have moved the input metadata that is used when packing a NuGet package from *project.json* to *.csproj* files.</span></span> <span data-ttu-id="65e93-211">Vstupy jsou vlastnosti nástroje MSBuild, takže budou muset přejít v rámci `<PropertyGroup>` skupiny.</span><span class="sxs-lookup"><span data-stu-id="65e93-211">The inputs are MSBuild properties so they have to go within a `<PropertyGroup>` group.</span></span> <span data-ttu-id="65e93-212">Tady je seznam vlastností, které se používají jako vstupy do procesu zabalení, při použití `dotnet pack` příkazu nebo `Pack` MSBuild cíl, který je součástí sady SDK.</span><span class="sxs-lookup"><span data-stu-id="65e93-212">The following is the list of properties that are used as inputs to the packing process when using the `dotnet pack` command or the `Pack` MSBuild target that is part of the SDK.</span></span> 

### <a name="ispackable"></a><span data-ttu-id="65e93-213">IsPackable</span><span class="sxs-lookup"><span data-stu-id="65e93-213">IsPackable</span></span>
<span data-ttu-id="65e93-214">Logická hodnota určující, zda lze zabalit projekt.</span><span class="sxs-lookup"><span data-stu-id="65e93-214">A Boolean value that specifies whether the project can be packed.</span></span> <span data-ttu-id="65e93-215">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="65e93-215">The default value is `true`.</span></span> 

### <a name="packageversion"></a><span data-ttu-id="65e93-216">PackageVersion</span><span class="sxs-lookup"><span data-stu-id="65e93-216">PackageVersion</span></span>
<span data-ttu-id="65e93-217">Určuje verzi, bude výsledný balíček.</span><span class="sxs-lookup"><span data-stu-id="65e93-217">Specifies the version that the resulting package will have.</span></span> <span data-ttu-id="65e93-218">Přijímá všechny formy řetězec verze NuGet.</span><span class="sxs-lookup"><span data-stu-id="65e93-218">Accepts all forms of NuGet version string.</span></span> <span data-ttu-id="65e93-219">Výchozí hodnota je hodnota `$(Version)`, to znamená, vlastnosti `Version` v projektu.</span><span class="sxs-lookup"><span data-stu-id="65e93-219">Default is the value of `$(Version)`, that is, of the property `Version` in the project.</span></span> 

### <a name="packageid"></a><span data-ttu-id="65e93-220">ID balíčku</span><span class="sxs-lookup"><span data-stu-id="65e93-220">PackageId</span></span>
<span data-ttu-id="65e93-221">Určuje název pro výsledný balíček.</span><span class="sxs-lookup"><span data-stu-id="65e93-221">Specifies the name for the resulting package.</span></span> <span data-ttu-id="65e93-222">Pokud není zadán, `pack` operace budou ve výchozím nastavení použití `AssemblyName` nebo název adresáře jako název balíčku.</span><span class="sxs-lookup"><span data-stu-id="65e93-222">If not specified, the `pack` operation will default to using the `AssemblyName` or directory name as the name of the package.</span></span> 

### <a name="title"></a><span data-ttu-id="65e93-223">Název</span><span class="sxs-lookup"><span data-stu-id="65e93-223">Title</span></span>
<span data-ttu-id="65e93-224">Lidské popisný název balíčku, obvykle používaných v uživatelském rozhraní na webech nuget.org a Správce balíčků v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="65e93-224">A human-friendly title of the package, typically used in UI displays as on nuget.org and the Package Manager in Visual Studio.</span></span> <span data-ttu-id="65e93-225">Pokud se nezadá, ID balíčku, který se používá místo toho.</span><span class="sxs-lookup"><span data-stu-id="65e93-225">If not specified, the package ID is used instead.</span></span>

### <a name="authors"></a><span data-ttu-id="65e93-226">Autoři</span><span class="sxs-lookup"><span data-stu-id="65e93-226">Authors</span></span>
<span data-ttu-id="65e93-227">Středníkem oddělený seznam autorů balíčků, odpovídající názvy profilů na nuget.org. Tyto jsou zobrazeny v galerii NuGet na nuget.org a slouží k křížový odkaz balíčky stejné autory.</span><span class="sxs-lookup"><span data-stu-id="65e93-227">A semicolon-separated list of packages authors, matching the profile names on nuget.org. These are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span>

### <a name="description"></a><span data-ttu-id="65e93-228">Popis</span><span class="sxs-lookup"><span data-stu-id="65e93-228">Description</span></span>
<span data-ttu-id="65e93-229">Dlouhý popis balíčku zobrazí v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="65e93-229">A long description of the package for UI display.</span></span>

### <a name="copyright"></a><span data-ttu-id="65e93-230">Copyright</span><span class="sxs-lookup"><span data-stu-id="65e93-230">Copyright</span></span>
<span data-ttu-id="65e93-231">Podrobnosti o autorských právech pro balíček.</span><span class="sxs-lookup"><span data-stu-id="65e93-231">Copyright details for the package.</span></span>

### <a name="packagerequirelicenseacceptance"></a><span data-ttu-id="65e93-232">PackageRequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="65e93-232">PackageRequireLicenseAcceptance</span></span>
<span data-ttu-id="65e93-233">Logická hodnota určující, zda klient musí požádat spotřebitele o přijetí licence balíčku před instalací balíčku.</span><span class="sxs-lookup"><span data-stu-id="65e93-233">A Boolean value that specifies whether the client must prompt the consumer to accept the package license before installing the package.</span></span> <span data-ttu-id="65e93-234">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="65e93-234">The default is `false`.</span></span>

### <a name="packagelicenseurl"></a><span data-ttu-id="65e93-235">PackageLicenseUrl</span><span class="sxs-lookup"><span data-stu-id="65e93-235">PackageLicenseUrl</span></span>
<span data-ttu-id="65e93-236">Adresu URL licence, která se vztahuje na balíček.</span><span class="sxs-lookup"><span data-stu-id="65e93-236">An URL to the license that is applicable to the package.</span></span>

### <a name="packageprojecturl"></a><span data-ttu-id="65e93-237">PackageProjectUrl</span><span class="sxs-lookup"><span data-stu-id="65e93-237">PackageProjectUrl</span></span>
<span data-ttu-id="65e93-238">Adresa URL domovské stránky balíčku, často zobrazuje v uživatelském rozhraní nuget.org.</span><span class="sxs-lookup"><span data-stu-id="65e93-238">A URL for the package's home page, often shown in UI displays as well as nuget.org.</span></span>

### <a name="packageiconurl"></a><span data-ttu-id="65e93-239">PackageIconUrl</span><span class="sxs-lookup"><span data-stu-id="65e93-239">PackageIconUrl</span></span>
<span data-ttu-id="65e93-240">Adresa URL pro bitovou kopii 64 x 64 s průhledným pozadím použít jako ikona pro balíček zobrazená v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="65e93-240">A URL for a 64x64 image with transparent background to use as the icon for the package in UI display.</span></span>

### <a name="packagereleasenotes"></a><span data-ttu-id="65e93-241">PackageReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="65e93-241">PackageReleaseNotes</span></span>
<span data-ttu-id="65e93-242">Zpráva k vydání verze pro balíček.</span><span class="sxs-lookup"><span data-stu-id="65e93-242">Release notes for the package.</span></span>

### <a name="packagetags"></a><span data-ttu-id="65e93-243">PackageTags</span><span class="sxs-lookup"><span data-stu-id="65e93-243">PackageTags</span></span>
<span data-ttu-id="65e93-244">Středníkem oddělený seznam značek, který určuje balíček.</span><span class="sxs-lookup"><span data-stu-id="65e93-244">A semicolon-delimited list of tags that designates the package.</span></span>

### <a name="packageoutputpath"></a><span data-ttu-id="65e93-245">PackageOutputPath</span><span class="sxs-lookup"><span data-stu-id="65e93-245">PackageOutputPath</span></span>
<span data-ttu-id="65e93-246">Určuje výstupní cesta, ve kterém se zahodí komprimovaný balíček.</span><span class="sxs-lookup"><span data-stu-id="65e93-246">Determines the output path in which the packed package will be dropped.</span></span> <span data-ttu-id="65e93-247">Výchozí hodnota je `$(OutputPath)`.</span><span class="sxs-lookup"><span data-stu-id="65e93-247">Default is `$(OutputPath)`.</span></span> 

### <a name="includesymbols"></a><span data-ttu-id="65e93-248">IncludeSymbols</span><span class="sxs-lookup"><span data-stu-id="65e93-248">IncludeSymbols</span></span>
<span data-ttu-id="65e93-249">Tato logická hodnota označuje, zda by měl balíček tehdy, když je zabalit projekt vytvořit balíček dalších symbolů.</span><span class="sxs-lookup"><span data-stu-id="65e93-249">This Boolean value indicates whether the package should create an additional symbols package when the project is packed.</span></span> <span data-ttu-id="65e93-250">Tento balíček bude mít *. symbols.nupkg* rozšíření a bude kopírovat soubory PDB spolu s knihovny DLL a ostatních výstupních souborů.</span><span class="sxs-lookup"><span data-stu-id="65e93-250">This package will have a *.symbols.nupkg* extension and will copy the PDB files along with the DLL and other output files.</span></span>

### <a name="includesource"></a><span data-ttu-id="65e93-251">IncludeSource</span><span class="sxs-lookup"><span data-stu-id="65e93-251">IncludeSource</span></span>
<span data-ttu-id="65e93-252">Tato logická hodnota značí, zda proces pack by měl vytvářet zdrojového balíčku.</span><span class="sxs-lookup"><span data-stu-id="65e93-252">This Boolean value indicates whether the pack process should create a source package.</span></span> <span data-ttu-id="65e93-253">Zdrojový balíček obsahuje knihovny zdrojový kód a soubory PDB.</span><span class="sxs-lookup"><span data-stu-id="65e93-253">The source package contains the library's source code as well as PDB files.</span></span> <span data-ttu-id="65e93-254">Zdrojové soubory jsou umístěny na `src/ProjectName` adresáře ve výsledném souboru balíčku.</span><span class="sxs-lookup"><span data-stu-id="65e93-254">Source files are put under the `src/ProjectName` directory in the resulting package file.</span></span> 

### <a name="istool"></a><span data-ttu-id="65e93-255">IsTool</span><span class="sxs-lookup"><span data-stu-id="65e93-255">IsTool</span></span>
<span data-ttu-id="65e93-256">Určuje, zda jsou všechny výstupní soubory zkopírovány do *nástroje* složky namísto *lib* složky.</span><span class="sxs-lookup"><span data-stu-id="65e93-256">Specifies whether all output files are copied to the *tools* folder instead of the *lib* folder.</span></span> <span data-ttu-id="65e93-257">Všimněte si, že se liší od `DotNetCliTool` který je určený nastavením `PackageType` v *.csproj* souboru.</span><span class="sxs-lookup"><span data-stu-id="65e93-257">Note that this is different from a `DotNetCliTool` which is specified by setting the `PackageType` in the *.csproj* file.</span></span>

### <a name="repositoryurl"></a><span data-ttu-id="65e93-258">RepositoryUrl</span><span class="sxs-lookup"><span data-stu-id="65e93-258">RepositoryUrl</span></span>
<span data-ttu-id="65e93-259">Určuje adresu URL úložiště, kde se nachází zdrojový kód pro balíček a/nebo z kterého se má být sestaven.</span><span class="sxs-lookup"><span data-stu-id="65e93-259">Specifies the URL for the repository where the source code for the package resides and/or from which it's being built.</span></span> 

### <a name="repositorytype"></a><span data-ttu-id="65e93-260">RepositoryType</span><span class="sxs-lookup"><span data-stu-id="65e93-260">RepositoryType</span></span>
<span data-ttu-id="65e93-261">Určuje typ úložiště.</span><span class="sxs-lookup"><span data-stu-id="65e93-261">Specifies the type of the repository.</span></span> <span data-ttu-id="65e93-262">Výchozí hodnota je "git".</span><span class="sxs-lookup"><span data-stu-id="65e93-262">Default is "git".</span></span> 

### <a name="nopackageanalysis"></a><span data-ttu-id="65e93-263">NoPackageAnalysis</span><span class="sxs-lookup"><span data-stu-id="65e93-263">NoPackageAnalysis</span></span>
<span data-ttu-id="65e93-264">Určuje, že balíček by neměl balíčku spustit jeho analýzu po sestavení.</span><span class="sxs-lookup"><span data-stu-id="65e93-264">Specifies that pack should not run package analysis after building the package.</span></span>

### <a name="minclientversion"></a><span data-ttu-id="65e93-265">MinClientVersion</span><span class="sxs-lookup"><span data-stu-id="65e93-265">MinClientVersion</span></span>
<span data-ttu-id="65e93-266">Určuje minimální verzi klienta NuGet, který můžete nainstalovat tento balíček, vynucuje nuget.exe a Správce balíčků sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="65e93-266">Specifies the minimum version of the NuGet client that can install this package, enforced by nuget.exe and the Visual Studio Package Manager.</span></span>

### <a name="includebuildoutput"></a><span data-ttu-id="65e93-267">IncludeBuildOutput</span><span class="sxs-lookup"><span data-stu-id="65e93-267">IncludeBuildOutput</span></span>
<span data-ttu-id="65e93-268">Tato logické hodnoty Určuje, zda sestavení výstupu sestavení by měl být zabaleny do *.nupkg* souboru nebo ne.</span><span class="sxs-lookup"><span data-stu-id="65e93-268">This Boolean values specifies whether the build output assemblies should be packed into the *.nupkg* file or not.</span></span>

### <a name="includecontentinpack"></a><span data-ttu-id="65e93-269">IncludeContentInPack</span><span class="sxs-lookup"><span data-stu-id="65e93-269">IncludeContentInPack</span></span>
<span data-ttu-id="65e93-270">Tato logická hodnota určuje, zda všechny položky, které mají typ `Content` výsledný balíček bude obsahovat automaticky.</span><span class="sxs-lookup"><span data-stu-id="65e93-270">This Boolean value specifies whether any items that have a type of `Content` will be included in the resulting package automatically.</span></span> <span data-ttu-id="65e93-271">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="65e93-271">The default is `true`.</span></span> 

### <a name="buildoutputtargetfolder"></a><span data-ttu-id="65e93-272">BuildOutputTargetFolder</span><span class="sxs-lookup"><span data-stu-id="65e93-272">BuildOutputTargetFolder</span></span>
<span data-ttu-id="65e93-273">Určuje složku, kam chcete umístit výstup sestavení.</span><span class="sxs-lookup"><span data-stu-id="65e93-273">Specifies the folder where to place the output assemblies.</span></span> <span data-ttu-id="65e93-274">Výstup sestavení (a ostatních výstupních souborů) jsou zkopírovány do složky jejich příslušných rozhraní framework.</span><span class="sxs-lookup"><span data-stu-id="65e93-274">The output assemblies (and other output files) are copied into their respective framework folders.</span></span>

### <a name="contenttargetfolders"></a><span data-ttu-id="65e93-275">ContentTargetFolders</span><span class="sxs-lookup"><span data-stu-id="65e93-275">ContentTargetFolders</span></span>
<span data-ttu-id="65e93-276">Tato vlastnost určuje výchozí umístění, kde by měl přejděte všechny soubory obsahu, pokud `PackagePath` není zadaný pro ně.</span><span class="sxs-lookup"><span data-stu-id="65e93-276">This property specifies the default location of where all the content files should go if `PackagePath` is not specified for them.</span></span> <span data-ttu-id="65e93-277">Výchozí hodnota je "obsah; contentFiles".</span><span class="sxs-lookup"><span data-stu-id="65e93-277">The default value is "content;contentFiles".</span></span>

### <a name="nuspecfile"></a><span data-ttu-id="65e93-278">NuspecFile</span><span class="sxs-lookup"><span data-stu-id="65e93-278">NuspecFile</span></span>
<span data-ttu-id="65e93-279">Relativní nebo absolutní cesta k *souboru .nuspec* souboru se používají pro balení.</span><span class="sxs-lookup"><span data-stu-id="65e93-279">Relative or absolute path to the *.nuspec* file being used for packing.</span></span> 

> [!NOTE]
> <span data-ttu-id="65e93-280">Pokud *souboru .nuspec* soubor zadán, použije se **výhradně** pro balení informace a informace v projektech se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="65e93-280">If the *.nuspec* file is specified, it's used **exclusively** for packaging information and any information in the projects is not used.</span></span> 

### <a name="nuspecbasepath"></a><span data-ttu-id="65e93-281">NuspecBasePath</span><span class="sxs-lookup"><span data-stu-id="65e93-281">NuspecBasePath</span></span>
<span data-ttu-id="65e93-282">Základní cesta pro *souboru .nuspec* souboru.</span><span class="sxs-lookup"><span data-stu-id="65e93-282">Base path for the *.nuspec* file.</span></span>

### <a name="nuspecproperties"></a><span data-ttu-id="65e93-283">NuspecProperties</span><span class="sxs-lookup"><span data-stu-id="65e93-283">NuspecProperties</span></span>
<span data-ttu-id="65e93-284">Středníkem oddělený seznam klíč = dvojice hodnot.</span><span class="sxs-lookup"><span data-stu-id="65e93-284">Semicolon separated list of key=value pairs.</span></span>
