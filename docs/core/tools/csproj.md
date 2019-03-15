---
title: Dodatky k formátu csproj pro .NET Core
description: Další informace o rozdílech mezi stávající a soubory csproj .NET Core
ms.date: 09/22/2017
ms.openlocfilehash: c6127d20e71328733eb1fe8a21a7fa7a9735d5a2
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57845479"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a><span data-ttu-id="db222-103">Dodatky k formátu csproj pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="db222-103">Additions to the csproj format for .NET Core</span></span>

<span data-ttu-id="db222-104">Tento dokument popisuje změny, které byly přidány do souborů projektu jako součást přesunu z *project.json* k *csproj* a [MSBuild](https://github.com/Microsoft/MSBuild).</span><span class="sxs-lookup"><span data-stu-id="db222-104">This document outlines the changes that were added to the project files as part of the move from *project.json* to *csproj* and [MSBuild](https://github.com/Microsoft/MSBuild).</span></span> <span data-ttu-id="db222-105">Další informace o syntaxi souboru obecné projektu a odkaz, naleznete v tématu [souboru projektu MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="db222-105">For more information about general project file syntax and reference, see [the MSBuild project file](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation.</span></span>

## <a name="implicit-package-references"></a><span data-ttu-id="db222-106">Odkazy na implicitní balíček</span><span class="sxs-lookup"><span data-stu-id="db222-106">Implicit package references</span></span>

<span data-ttu-id="db222-107">Metabalíčky jsou implicitně odkazovat podle cílové architekturu podle `<TargetFramework>` nebo `<TargetFrameworks>` vlastnost souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="db222-107">Metapackages are implicitly referenced based on the target framework(s) specified in the `<TargetFramework>` or `<TargetFrameworks>` property of your project file.</span></span> <span data-ttu-id="db222-108">`<TargetFrameworks>` se ignoruje, pokud `<TargetFramework>` je zadaný, nezávisle na pořadí.</span><span class="sxs-lookup"><span data-stu-id="db222-108">`<TargetFrameworks>` is ignored if `<TargetFramework>` is specified, independent of order.</span></span>

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

### <a name="recommendations"></a><span data-ttu-id="db222-109">Doporučení</span><span class="sxs-lookup"><span data-stu-id="db222-109">Recommendations</span></span>

<span data-ttu-id="db222-110">Protože `Microsoft.NETCore.App` nebo `NetStandard.Library` metabalíčky jsou implicitně odkazovat, naše doporučené osvědčené postupy jsou následující:</span><span class="sxs-lookup"><span data-stu-id="db222-110">Since `Microsoft.NETCore.App` or `NetStandard.Library` metapackages are implicitly referenced, the following are our recommended best practices:</span></span>

* <span data-ttu-id="db222-111">Při cílení na .NET Core nebo .NET Standard, nikdy nemůžete mít explicitní odkaz na `Microsoft.NETCore.App` nebo `NetStandard.Library` metabalíčky prostřednictvím `<PackageReference>` položky v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="db222-111">When targeting .NET Core or .NET Standard, never have an explicit reference to the `Microsoft.NETCore.App` or `NetStandard.Library` metapackages via a `<PackageReference>` item in your project file.</span></span>
* <span data-ttu-id="db222-112">Pokud potřebujete konkrétní verzi modulu runtime při cílení na .NET Core, měli byste použít `<RuntimeFrameworkVersion>` vlastnost v projektu (například `1.0.4`) namísto odkazování Microsoft.aspnetcore.all.</span><span class="sxs-lookup"><span data-stu-id="db222-112">If you need a specific version of the runtime when targeting .NET Core, you should use the `<RuntimeFrameworkVersion>` property in your project (for example, `1.0.4`) instead of referencing the metapackage.</span></span>
    * <span data-ttu-id="db222-113">K tomu může dojít, pokud používáte [samostatná nasazení](../deploying/index.md#self-contained-deployments-scd) a potřebujete oprav konkrétní verze 1.0.0 LTS běhu.</span><span class="sxs-lookup"><span data-stu-id="db222-113">This might happen if you are using [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) and you need a specific patch version of 1.0.0 LTS runtime, for example.</span></span>
* <span data-ttu-id="db222-114">Pokud potřebujete konkrétní verzi `NetStandard.Library` Microsoft.aspnetcore.all při cílení na .NET Standard, můžete použít `<NetStandardImplicitPackageVersion>` vlastnost a nastavte verzi budete potřebovat.</span><span class="sxs-lookup"><span data-stu-id="db222-114">If you need a specific version of the `NetStandard.Library` metapackage when targeting .NET Standard, you can use the `<NetStandardImplicitPackageVersion>` property and set the version you need.</span></span>
* <span data-ttu-id="db222-115">Není explicitně přidat nebo aktualizovat odkazy na buď `Microsoft.NETCore.App` nebo `NetStandard.Library` Microsoft.aspnetcore.all v projektech .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="db222-115">Don't explicitly add or update references to either the `Microsoft.NETCore.App` or `NetStandard.Library` metapackage in .NET Framework projects.</span></span> <span data-ttu-id="db222-116">Pokud všechny verze `NetStandard.Library` je potřeba při použití balíčku NuGet pro .NET Standard na základě, NuGet automaticky instaluje tuto verzi.</span><span class="sxs-lookup"><span data-stu-id="db222-116">If any version of `NetStandard.Library` is needed when using a .NET Standard-based NuGet package, NuGet automatically installs that version.</span></span>

## <a name="default-compilation-includes-in-net-core-projects"></a><span data-ttu-id="db222-117">Obsahuje výchozí kompilace v projektech .NET Core</span><span class="sxs-lookup"><span data-stu-id="db222-117">Default compilation includes in .NET Core projects</span></span>
<span data-ttu-id="db222-118">S přechodem na *csproj* formátu v nejnovější verze sady SDK, přešli jsme výchozí zahrnuje a nezahrnuje pro položky kompilace a vložené prostředky, které vlastnosti soubory sady SDK.</span><span class="sxs-lookup"><span data-stu-id="db222-118">With the move to the *csproj* format in the latest SDK versions, we've moved the default includes and excludes for compile items and embedded resources to the SDK properties files.</span></span> <span data-ttu-id="db222-119">To znamená, že už nemusíte určit tyto položky v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="db222-119">This means that you no longer need to specify these items in your project file.</span></span>

<span data-ttu-id="db222-120">Hlavním důvodem pro to je přehlednost v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="db222-120">The main reason for doing this is to reduce the clutter in your project file.</span></span> <span data-ttu-id="db222-121">Výchozí hodnoty, které jsou k dispozici v sadě SDK by měly pokrývat nejběžnější případy použití, takže není nutné opakovat v každém projektu, který vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="db222-121">The defaults that are present in the SDK should cover most common use cases, so there is no need to repeat them in every project that you create.</span></span> <span data-ttu-id="db222-122">To vede k menší soubory projektu, které jsou mnohem snazší porozumět, stejně jako upravit ručně, v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="db222-122">This leads to smaller project files that are much easier to understand as well as edit by hand, if needed.</span></span>

<span data-ttu-id="db222-123">V následující tabulce jsou uvedeny které elementy a které [globy](https://en.wikipedia.org/wiki/Glob_(programming)) jsou zahrnuté i vyloučené v sadě SDK:</span><span class="sxs-lookup"><span data-stu-id="db222-123">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are both included and excluded in the SDK:</span></span>

| <span data-ttu-id="db222-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="db222-124">Element</span></span>           | <span data-ttu-id="db222-125">Zahrnout glob</span><span class="sxs-lookup"><span data-stu-id="db222-125">Include glob</span></span>                              | <span data-ttu-id="db222-126">Vyloučit glob</span><span class="sxs-lookup"><span data-stu-id="db222-126">Exclude glob</span></span>                                                  | <span data-ttu-id="db222-127">Odebrat glob</span><span class="sxs-lookup"><span data-stu-id="db222-127">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| <span data-ttu-id="db222-128">Kompilace</span><span class="sxs-lookup"><span data-stu-id="db222-128">Compile</span></span>           | <span data-ttu-id="db222-129">\*\*/\*.cs (nebo jiných jazykových rozšíření)</span><span class="sxs-lookup"><span data-stu-id="db222-129">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="db222-130">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="db222-130">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="db222-131">Není k dispozici</span><span class="sxs-lookup"><span data-stu-id="db222-131">N/A</span></span>                      |
| <span data-ttu-id="db222-132">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="db222-132">EmbeddedResource</span></span>  | <span data-ttu-id="db222-133">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="db222-133">\*\*/\*.resx</span></span>                              | <span data-ttu-id="db222-134">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="db222-134">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="db222-135">Není k dispozici</span><span class="sxs-lookup"><span data-stu-id="db222-135">N/A</span></span>                      |
| <span data-ttu-id="db222-136">Žádná</span><span class="sxs-lookup"><span data-stu-id="db222-136">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="db222-137">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="db222-137">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="db222-138">\*\*/\*.cs; \* \* / \*resx</span><span class="sxs-lookup"><span data-stu-id="db222-138">\*\*/\*.cs; \*\*/\*.resx</span></span>   |

> [!NOTE]
> <span data-ttu-id="db222-139">**Vyloučit glob** vždy vyloučí `./bin` a `./obj` složek, které jsou znázorněny `$(BaseOutputPath)` a `$(BaseIntermediateOutputPath)` vlastnosti nástroje MSBuild, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="db222-139">**Exclude glob** always excludes the `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, respectively.</span></span> <span data-ttu-id="db222-140">Jako celek, vyloučí všechny jsou reprezentovány `$(DefaultItemExcludes)`.</span><span class="sxs-lookup"><span data-stu-id="db222-140">As a whole, all excludes are represented by `$(DefaultItemExcludes)`.</span></span>

<span data-ttu-id="db222-141">Pokud máte globy ve vašem projektu a zkusíte sestavit pomocí nejnovější SDK, zobrazí se vám chybová zpráva:</span><span class="sxs-lookup"><span data-stu-id="db222-141">If you have globs in your project and you try to build it using the newest SDK, you'll get the following error:</span></span>

> <span data-ttu-id="db222-142">Duplicitní položky kompilace byly zahrnuty.</span><span class="sxs-lookup"><span data-stu-id="db222-142">Duplicate Compile items were included.</span></span> <span data-ttu-id="db222-143">Sady .NET SDK obsahuje ve výchozím nastavení kompilace položky z adresáře projektu.</span><span class="sxs-lookup"><span data-stu-id="db222-143">The .NET SDK includes Compile items from your project directory by default.</span></span> <span data-ttu-id="db222-144">Můžete tyto položky odebrat ze svého souboru projektu, nebo nastavte vlastnost 'EnableDefaultCompileItems' na hodnotu false' Pokud chcete explicitně zahrnout je do souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="db222-144">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

<span data-ttu-id="db222-145">Aby bylo možné tuto chybu vyřešit, buď odstraněním explicitní `Compile` položky, které odpovídají těm, které jsou uvedené v předchozí tabulce, nebo můžete nastavit `<EnableDefaultCompileItems>` vlastnost `false`, tímto způsobem:</span><span class="sxs-lookup"><span data-stu-id="db222-145">In order to get around this error, you can either remove the explicit `Compile` items that match the ones listed on the previous table, or you can set the `<EnableDefaultCompileItems>` property to `false`, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

<span data-ttu-id="db222-146">Nastavení této vlastnosti na `false` dojde k zakázání implicitního zahrnutí návrat k chování předchozí sady SDK, které jste museli zadat výchozí globy ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="db222-146">Setting this property to `false` will disable implicit inclusion, reverting to the behavior of previous SDKs where you had to specify the default globs in your project.</span></span>

<span data-ttu-id="db222-147">Tato změna neprovede žádné změny v hlavním obsahuje jiné mechanismy.</span><span class="sxs-lookup"><span data-stu-id="db222-147">This change does not modify the main mechanics of other includes.</span></span> <span data-ttu-id="db222-148">Ale pokud chcete zadat, například některé soubory se publikovat s vaší aplikací, můžete stále použít známé mechanismy ve *csproj* pro daný (například `<Content>` element).</span><span class="sxs-lookup"><span data-stu-id="db222-148">However, if you wish to specify, for example, some files to get published with your app, you can still use the known mechanisms in *csproj* for that (for example, the `<Content>` element).</span></span>

<span data-ttu-id="db222-149">`<EnableDefaultCompileItems>` pouze zakáže `Compile` globy, ale nemá vliv na ostatní globy, jako jsou implicitní `None` glob, která se také vztahuje na \*.cs položky.</span><span class="sxs-lookup"><span data-stu-id="db222-149">`<EnableDefaultCompileItems>` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob, which also applies to \*.cs items.</span></span> <span data-ttu-id="db222-150">Proto **Průzkumníka řešení** bude dál zobrazovat \*.cs položky jako součást projektu, jako `None` položky.</span><span class="sxs-lookup"><span data-stu-id="db222-150">Because of that, **Solution Explorer** will continue show \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="db222-151">Podobným způsobem, můžete použít `<EnableDefaultNoneItems>` zakázat implicitní `None` glob.</span><span class="sxs-lookup"><span data-stu-id="db222-151">In a similar way, you can use `<EnableDefaultNoneItems>` to disable the implicit `None` glob.</span></span>

<span data-ttu-id="db222-152">Chcete-li zakázat **všechny implicitní globy**, můžete nastavit `<EnableDefaultItems>` vlastnost `false` jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="db222-152">To disable **all implicit globs**, you can set the `<EnableDefaultItems>` property to `false` as in the following example:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a><span data-ttu-id="db222-153">Zobrazení celého projektu, jak ho uvidí MSBuild</span><span class="sxs-lookup"><span data-stu-id="db222-153">How to see the whole project as MSBuild sees it</span></span>

<span data-ttu-id="db222-154">Zatímco tyto změny csproj výrazně zjednodušit soubory projektu, můžete chtít zobrazit plně rozšířené projektu jako MSBuild ji vidí, jakmile jsou zahrnuty v sadě SDK a cíle.</span><span class="sxs-lookup"><span data-stu-id="db222-154">While those csproj changes greatly simplify project files, you might want to see the fully expanded project as MSBuild sees it once the SDK and its targets are included.</span></span> <span data-ttu-id="db222-155">Předběžné zpracování projektu s [ `/pp` přepnout](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) z [ `dotnet msbuild` ](dotnet-msbuild.md) příkaz, který ukazuje, které soubory se importují, jejich zdroje a svoje příspěvky k sestavení bez ve skutečnosti sestavení projektu:</span><span class="sxs-lookup"><span data-stu-id="db222-155">Preprocess the project with [the `/pp` switch](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) of the [`dotnet msbuild`](dotnet-msbuild.md) command, which shows which files are imported, their sources, and their contributions to the build without actually building the project:</span></span>

`dotnet msbuild -pp:fullproject.xml`

<span data-ttu-id="db222-156">Pokud projekt obsahuje více cílových platforem, by měl výsledky příkazu, zaměřuje na pouze jeden z nich tak, že zadáte jako vlastnost MSBuild:</span><span class="sxs-lookup"><span data-stu-id="db222-156">If the project has multiple target frameworks, the results of the command should be focused on only one of them by specifying it as an MSBuild property:</span></span>

`dotnet msbuild -p:TargetFramework=netcoreapp2.0 -pp:fullproject.xml`

## <a name="additions"></a><span data-ttu-id="db222-157">Přidání</span><span class="sxs-lookup"><span data-stu-id="db222-157">Additions</span></span>

### <a name="sdk-attribute"></a><span data-ttu-id="db222-158">Atribut SDK</span><span class="sxs-lookup"><span data-stu-id="db222-158">Sdk attribute</span></span>
<span data-ttu-id="db222-159">Kořen `<Project>` elementu *.csproj* soubor obsahuje nový atribut volá `Sdk`.</span><span class="sxs-lookup"><span data-stu-id="db222-159">The root `<Project>` element of the *.csproj* file has a new attribute called `Sdk`.</span></span> <span data-ttu-id="db222-160">`Sdk` Určuje, které sada SDK se používá v projektu.</span><span class="sxs-lookup"><span data-stu-id="db222-160">`Sdk` specifies which SDK will be used by the project.</span></span> <span data-ttu-id="db222-161">Sady SDK, jako [rozvržení dokumentu](cli-msbuild-architecture.md) popisuje, je sada MSBuild [úlohy](/visualstudio/msbuild/msbuild-tasks) a [cíle](/visualstudio/msbuild/msbuild-targets) , které můžete vytvářet kód .NET Core.</span><span class="sxs-lookup"><span data-stu-id="db222-161">The SDK, as the [layering document](cli-msbuild-architecture.md) describes, is a set of MSBuild [tasks](/visualstudio/msbuild/msbuild-tasks) and [targets](/visualstudio/msbuild/msbuild-targets) that can build .NET Core code.</span></span> <span data-ttu-id="db222-162">Dodáváme tři hlavní sady SDK s nástroji .NET Core:</span><span class="sxs-lookup"><span data-stu-id="db222-162">We ship three main SDKs with the .NET Core tools:</span></span>

1. <span data-ttu-id="db222-163">.NET Core SDK s ID `Microsoft.NET.Sdk`</span><span class="sxs-lookup"><span data-stu-id="db222-163">The .NET Core SDK with the ID of `Microsoft.NET.Sdk`</span></span>
2. <span data-ttu-id="db222-164">.NET Core web SDK s ID `Microsoft.NET.Sdk.Web`</span><span class="sxs-lookup"><span data-stu-id="db222-164">The .NET Core web SDK with the ID of `Microsoft.NET.Sdk.Web`</span></span>
3. <span data-ttu-id="db222-165">Knihovny tříd Razor .NET Core SDK s ID nástroje `Microsoft.NET.Sdk.Razor`</span><span class="sxs-lookup"><span data-stu-id="db222-165">The .NET Core Razor Class Library SDK with the ID of `Microsoft.NET.Sdk.Razor`</span></span>

<span data-ttu-id="db222-166">Je potřeba mít `Sdk` nastavený atribut na jednu z těchto ID na `<Project>` prvku abyste mohli použít nástroje pro .NET Core a vytváření kódu.</span><span class="sxs-lookup"><span data-stu-id="db222-166">You need to have the `Sdk` attribute set to one of those IDs on the `<Project>` element in order to use the .NET Core tools and build your code.</span></span>

### <a name="packagereference"></a><span data-ttu-id="db222-167">PackageReference</span><span class="sxs-lookup"><span data-stu-id="db222-167">PackageReference</span></span>

<span data-ttu-id="db222-168">A `<PackageReference>` určuje prvek položky [závislostí NuGet v projektu](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="db222-168">A `<PackageReference>` item element specifies a [NuGet dependency in the project](/nuget/consume-packages/package-references-in-project-files).</span></span> <span data-ttu-id="db222-169">`Include` Atribut určuje ID balíčku.</span><span class="sxs-lookup"><span data-stu-id="db222-169">The `Include` attribute specifies the package ID.</span></span>

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a><span data-ttu-id="db222-170">Version</span><span class="sxs-lookup"><span data-stu-id="db222-170">Version</span></span>

<span data-ttu-id="db222-171">Požadované `Version` atribut určuje verzi balíčku k obnovení.</span><span class="sxs-lookup"><span data-stu-id="db222-171">The required `Version` attribute specifies the version of the package to restore.</span></span> <span data-ttu-id="db222-172">Atribut respektuje pravidla [správy verzí NuGet](/nuget/reference/package-versioning#version-ranges-and-wildcards) schéma.</span><span class="sxs-lookup"><span data-stu-id="db222-172">The attribute respects the rules of the [NuGet versioning](/nuget/reference/package-versioning#version-ranges-and-wildcards) scheme.</span></span> <span data-ttu-id="db222-173">Výchozí chování je shoda přesnou verzi.</span><span class="sxs-lookup"><span data-stu-id="db222-173">The default behavior is an exact version match.</span></span> <span data-ttu-id="db222-174">Například zadání `Version="1.2.3"` je ekvivalentní zápisu NuGet `[1.2.3]` pro přesné 1.2.3 verzi balíčku.</span><span class="sxs-lookup"><span data-stu-id="db222-174">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

#### <a name="includeassets-excludeassets-and-privateassets"></a><span data-ttu-id="db222-175">IncludeAssets, ExcludeAssets a PrivateAssets</span><span class="sxs-lookup"><span data-stu-id="db222-175">IncludeAssets, ExcludeAssets and PrivateAssets</span></span>

<span data-ttu-id="db222-176">`IncludeAssets` atribut určuje, jaké prostředky, které patří do určeného balíčku `<PackageReference>` by měl používat.</span><span class="sxs-lookup"><span data-stu-id="db222-176">`IncludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed.</span></span> <span data-ttu-id="db222-177">Ve výchozím nastavení jsou zahrnuty všechny prostředky balíčku.</span><span class="sxs-lookup"><span data-stu-id="db222-177">By default, all package assets are included.</span></span>

<span data-ttu-id="db222-178">`ExcludeAssets` atribut určuje, jaké prostředky, které patří do určeného balíčku `<PackageReference>` by neměla využívat.</span><span class="sxs-lookup"><span data-stu-id="db222-178">`ExcludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should not be consumed.</span></span>

<span data-ttu-id="db222-179">`PrivateAssets` atribut určuje, jaké prostředky, které patří do určeného balíčku `<PackageReference>` by měl používat, ale ne směrovat do příští projekt.</span><span class="sxs-lookup"><span data-stu-id="db222-179">`PrivateAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed but not flow to the next project.</span></span> <span data-ttu-id="db222-180">`Analyzers`, `Build` a `ContentFiles` prostředky jsou ve výchozím nastavení privátní, když tento atribut není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="db222-180">The `Analyzers`, `Build` and `ContentFiles` assets are private by default when this attribute is not present.</span></span>

> [!NOTE]
> <span data-ttu-id="db222-181">`PrivateAssets` je ekvivalentní *project.json*/*xproj* `SuppressParent` elementu.</span><span class="sxs-lookup"><span data-stu-id="db222-181">`PrivateAssets` is equivalent to the *project.json*/*xproj* `SuppressParent` element.</span></span>

<span data-ttu-id="db222-182">Tyto atributy mohou obsahovat jednu nebo více následující položky oddělené středníkem `;` znaku, pokud je uveden více než jeden:</span><span class="sxs-lookup"><span data-stu-id="db222-182">These attributes can contain one or more of the following items, separated by the semicolon `;` character if more than one is listed:</span></span>

* <span data-ttu-id="db222-183">`Compile` – je možné kompilovat proti obsah složky lib.</span><span class="sxs-lookup"><span data-stu-id="db222-183">`Compile` – the contents of the lib folder are available to compile against.</span></span>
* <span data-ttu-id="db222-184">`Runtime` – obsah složky modulu runtime jsou distribuovány.</span><span class="sxs-lookup"><span data-stu-id="db222-184">`Runtime` – the contents of the runtime folder are distributed.</span></span>
* <span data-ttu-id="db222-185">`ContentFiles` – obsah *contentfiles* složky se používají.</span><span class="sxs-lookup"><span data-stu-id="db222-185">`ContentFiles` – the contents of the *contentfiles* folder are used.</span></span>
* <span data-ttu-id="db222-186">`Build` – vlastnosti a cíle ve složce sestavení se používají.</span><span class="sxs-lookup"><span data-stu-id="db222-186">`Build` – the props/targets in the build folder are used.</span></span>
* <span data-ttu-id="db222-187">`Native` – obsah z nativní prostředky se zkopíruje do výstupní složky pro modul runtime.</span><span class="sxs-lookup"><span data-stu-id="db222-187">`Native` – the contents from native assets are copied to the output folder for runtime.</span></span>
* <span data-ttu-id="db222-188">`Analyzers` – Analyzátory se používají.</span><span class="sxs-lookup"><span data-stu-id="db222-188">`Analyzers` – the analyzers are used.</span></span>

<span data-ttu-id="db222-189">Alternativně může obsahovat atribut:</span><span class="sxs-lookup"><span data-stu-id="db222-189">Alternatively, the attribute can contain:</span></span>

* <span data-ttu-id="db222-190">`None` – žádné prostředky se používají.</span><span class="sxs-lookup"><span data-stu-id="db222-190">`None` – none of the assets are used.</span></span>
* <span data-ttu-id="db222-191">`All` – všechny prostředky se používají.</span><span class="sxs-lookup"><span data-stu-id="db222-191">`All` – all assets are used.</span></span>

### <a name="dotnetclitoolreference"></a><span data-ttu-id="db222-192">DotNetCliToolReference</span><span class="sxs-lookup"><span data-stu-id="db222-192">DotNetCliToolReference</span></span>
<span data-ttu-id="db222-193">A `<DotNetCliToolReference>` prvek položky určuje nástroj rozhraní příkazového řádku, který uživatel chce obnovit v kontextu projektu.</span><span class="sxs-lookup"><span data-stu-id="db222-193">A `<DotNetCliToolReference>` item element specifies the CLI tool that the user wants to restore in the context of the project.</span></span> <span data-ttu-id="db222-194">Je náhradou za `tools` uzel v *project.json*.</span><span class="sxs-lookup"><span data-stu-id="db222-194">It's a replacement for the `tools` node in *project.json*.</span></span>

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

#### <a name="version"></a><span data-ttu-id="db222-195">Version</span><span class="sxs-lookup"><span data-stu-id="db222-195">Version</span></span>

<span data-ttu-id="db222-196">`Version` Určuje verzi balíčku, který se obnovit.</span><span class="sxs-lookup"><span data-stu-id="db222-196">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="db222-197">Atribut respektuje pravidla [správy verzí NuGet](/nuget/create-packages/dependency-versions#version-ranges) schéma.</span><span class="sxs-lookup"><span data-stu-id="db222-197">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="db222-198">Výchozí chování je shoda přesnou verzi.</span><span class="sxs-lookup"><span data-stu-id="db222-198">The default behavior is an exact version match.</span></span> <span data-ttu-id="db222-199">Například zadání `Version="1.2.3"` je ekvivalentní zápisu NuGet `[1.2.3]` pro přesné 1.2.3 verzi balíčku.</span><span class="sxs-lookup"><span data-stu-id="db222-199">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

### <a name="runtimeidentifiers"></a><span data-ttu-id="db222-200">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="db222-200">RuntimeIdentifiers</span></span>

<span data-ttu-id="db222-201">`<RuntimeIdentifiers>` Property – element umožňuje určit seznam oddělený středníkem [Runtime identifikátorů (RID)](../rid-catalog.md) pro projekt.</span><span class="sxs-lookup"><span data-stu-id="db222-201">The `<RuntimeIdentifiers>` property element lets you specify a semicolon-delimited list of [Runtime Identifiers (RIDs)](../rid-catalog.md) for the project.</span></span>
<span data-ttu-id="db222-202">Identifikátory RID povolit publikování samostatná nasazení.</span><span class="sxs-lookup"><span data-stu-id="db222-202">RIDs enable publishing self-contained deployments.</span></span>

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a><span data-ttu-id="db222-203">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="db222-203">RuntimeIdentifier</span></span>

<span data-ttu-id="db222-204">`<RuntimeIdentifier>` Property – element umožňuje určit pouze jeden [identifikátor modulu Runtime (RID)](../rid-catalog.md) pro projekt.</span><span class="sxs-lookup"><span data-stu-id="db222-204">The `<RuntimeIdentifier>` property element allows you to specify only one [Runtime Identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="db222-205">Identifikátor RID umožňuje publikování samostatná nasazení.</span><span class="sxs-lookup"><span data-stu-id="db222-205">The RID enables publishing a self-contained deployment.</span></span>

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

<span data-ttu-id="db222-206">Použití `<RuntimeIdentifiers>` (množném čísle) místo toho pokud je potřeba publikovat pro více modulů – runtime.</span><span class="sxs-lookup"><span data-stu-id="db222-206">Use `<RuntimeIdentifiers>` (plural) instead if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="db222-207">`<RuntimeIdentifier>` rychlejší sestavování a můžete zadat, pokud je nutné použít pouze jeden modul runtime.</span><span class="sxs-lookup"><span data-stu-id="db222-207">`<RuntimeIdentifier>` can provide faster builds when only a single runtime is required.</span></span>

### <a name="packagetargetfallback"></a><span data-ttu-id="db222-208">PackageTargetFallback</span><span class="sxs-lookup"><span data-stu-id="db222-208">PackageTargetFallback</span></span>

<span data-ttu-id="db222-209">`<PackageTargetFallback>` Property – element umožňuje určit sadu kompatibilní cíle se použije při obnovování balíčků.</span><span class="sxs-lookup"><span data-stu-id="db222-209">The `<PackageTargetFallback>` property element allows you to specify a set of compatible targets to be used when restoring packages.</span></span> <span data-ttu-id="db222-210">Je navržen tak, aby balíčky, které používají dotnet [TxM (Moniker cílového x)](/nuget/schema/target-frameworks) pracovat s balíčky, které není deklarovat dotnet TxM.</span><span class="sxs-lookup"><span data-stu-id="db222-210">It's designed to allow packages that use the dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) to operate with packages that don't declare a dotnet TxM.</span></span> <span data-ttu-id="db222-211">Pokud váš projekt používá dotnet TxM, pak všechny balíčky, které závisí na musí také mít dotnet TxM, pokud přidáte `<PackageTargetFallback>` do vašeho projektu, aby bylo možné povolit bez dotnet platformy se kvůli kompatibilitě s dotnet.</span><span class="sxs-lookup"><span data-stu-id="db222-211">If your project uses the dotnet TxM, then all the packages it depends on must also have a dotnet TxM, unless you add the `<PackageTargetFallback>` to your project in order to allow non-dotnet platforms to be compatible with dotnet.</span></span>

<span data-ttu-id="db222-212">Následující příklad uvádí náhrad pro všechny cíle v projektu:</span><span class="sxs-lookup"><span data-stu-id="db222-212">The following example provides the fallbacks for all targets in your project:</span></span>

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

<span data-ttu-id="db222-213">Následující příklad určuje náhrad pouze `netcoreapp2.1` cíl:</span><span class="sxs-lookup"><span data-stu-id="db222-213">The following example specifies the fallbacks only for the `netcoreapp2.1` target:</span></span>

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp2.1'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="nuget-metadata-properties"></a><span data-ttu-id="db222-214">Vlastnosti metadat NuGet</span><span class="sxs-lookup"><span data-stu-id="db222-214">NuGet metadata properties</span></span>

<span data-ttu-id="db222-215">S přechodem na MSBuild, přesunuli jsme vstupní metadata, která se používá při balení balíček NuGet *project.json* k *.csproj* soubory.</span><span class="sxs-lookup"><span data-stu-id="db222-215">With the move to MSBuild, we have moved the input metadata that is used when packing a NuGet package from *project.json* to *.csproj* files.</span></span> <span data-ttu-id="db222-216">Vstupy jsou vlastnosti nástroje MSBuild, takže budou muset přejít v rámci `<PropertyGroup>` skupiny.</span><span class="sxs-lookup"><span data-stu-id="db222-216">The inputs are MSBuild properties so they have to go within a `<PropertyGroup>` group.</span></span> <span data-ttu-id="db222-217">Tady je seznam vlastností, které se používají jako vstupy do procesu zabalení, při použití `dotnet pack` příkazu nebo `Pack` MSBuild cíl, který je součástí sady SDK.</span><span class="sxs-lookup"><span data-stu-id="db222-217">The following is the list of properties that are used as inputs to the packing process when using the `dotnet pack` command or the `Pack` MSBuild target that is part of the SDK.</span></span>

### <a name="ispackable"></a><span data-ttu-id="db222-218">IsPackable</span><span class="sxs-lookup"><span data-stu-id="db222-218">IsPackable</span></span>

<span data-ttu-id="db222-219">Logická hodnota určující, zda lze zabalit projekt.</span><span class="sxs-lookup"><span data-stu-id="db222-219">A Boolean value that specifies whether the project can be packed.</span></span> <span data-ttu-id="db222-220">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="db222-220">The default value is `true`.</span></span>

### <a name="packageversion"></a><span data-ttu-id="db222-221">PackageVersion</span><span class="sxs-lookup"><span data-stu-id="db222-221">PackageVersion</span></span>

<span data-ttu-id="db222-222">Určuje verzi, bude výsledný balíček.</span><span class="sxs-lookup"><span data-stu-id="db222-222">Specifies the version that the resulting package will have.</span></span> <span data-ttu-id="db222-223">Přijímá všechny formy řetězec verze NuGet.</span><span class="sxs-lookup"><span data-stu-id="db222-223">Accepts all forms of NuGet version string.</span></span> <span data-ttu-id="db222-224">Výchozí hodnota je hodnota `$(Version)`, to znamená, vlastnosti `Version` v projektu.</span><span class="sxs-lookup"><span data-stu-id="db222-224">Default is the value of `$(Version)`, that is, of the property `Version` in the project.</span></span>

### <a name="packageid"></a><span data-ttu-id="db222-225">PackageId</span><span class="sxs-lookup"><span data-stu-id="db222-225">PackageId</span></span>

<span data-ttu-id="db222-226">Určuje název pro výsledný balíček.</span><span class="sxs-lookup"><span data-stu-id="db222-226">Specifies the name for the resulting package.</span></span> <span data-ttu-id="db222-227">Pokud není zadán, `pack` operace budou ve výchozím nastavení použití `AssemblyName` nebo název adresáře jako název balíčku.</span><span class="sxs-lookup"><span data-stu-id="db222-227">If not specified, the `pack` operation will default to using the `AssemblyName` or directory name as the name of the package.</span></span>

### <a name="title"></a><span data-ttu-id="db222-228">Název</span><span class="sxs-lookup"><span data-stu-id="db222-228">Title</span></span>

<span data-ttu-id="db222-229">Lidské popisný název balíčku, obvykle používaných v uživatelském rozhraní na webech nuget.org a Správce balíčků v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="db222-229">A human-friendly title of the package, typically used in UI displays as on nuget.org and the Package Manager in Visual Studio.</span></span> <span data-ttu-id="db222-230">Pokud se nezadá, ID balíčku, který se používá místo toho.</span><span class="sxs-lookup"><span data-stu-id="db222-230">If not specified, the package ID is used instead.</span></span>

### <a name="authors"></a><span data-ttu-id="db222-231">Autoři</span><span class="sxs-lookup"><span data-stu-id="db222-231">Authors</span></span>

<span data-ttu-id="db222-232">Středníkem oddělený seznam autorů balíčků, odpovídající názvy profilů na nuget.org. Tyto jsou zobrazeny v galerii NuGet na nuget.org a slouží k křížový odkaz balíčky stejné autory.</span><span class="sxs-lookup"><span data-stu-id="db222-232">A semicolon-separated list of packages authors, matching the profile names on nuget.org. These are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span>

### <a name="packagedescription"></a><span data-ttu-id="db222-233">PackageDescription</span><span class="sxs-lookup"><span data-stu-id="db222-233">PackageDescription</span></span>

<span data-ttu-id="db222-234">Dlouhý popis balíčku zobrazí v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="db222-234">A long description of the package for UI display.</span></span>

### <a name="description"></a><span data-ttu-id="db222-235">Popis</span><span class="sxs-lookup"><span data-stu-id="db222-235">Description</span></span>

<span data-ttu-id="db222-236">Dlouhý popis pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="db222-236">A long description for the assembly.</span></span> <span data-ttu-id="db222-237">Pokud `PackageDescription` není zadán, pak tato vlastnost slouží také jako popis balíčku.</span><span class="sxs-lookup"><span data-stu-id="db222-237">If `PackageDescription` is not specified then this property is also used as the description of the package.</span></span>

### <a name="copyright"></a><span data-ttu-id="db222-238">Copyright</span><span class="sxs-lookup"><span data-stu-id="db222-238">Copyright</span></span>

<span data-ttu-id="db222-239">Podrobnosti o autorských právech pro balíček.</span><span class="sxs-lookup"><span data-stu-id="db222-239">Copyright details for the package.</span></span>

### <a name="packagerequirelicenseacceptance"></a><span data-ttu-id="db222-240">PackageRequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="db222-240">PackageRequireLicenseAcceptance</span></span>

<span data-ttu-id="db222-241">Logická hodnota určující, zda klient musí požádat spotřebitele o přijetí licence balíčku před instalací balíčku.</span><span class="sxs-lookup"><span data-stu-id="db222-241">A Boolean value that specifies whether the client must prompt the consumer to accept the package license before installing the package.</span></span> <span data-ttu-id="db222-242">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="db222-242">The default is `false`.</span></span>

### <a name="packagelicenseexpression"></a><span data-ttu-id="db222-243">PackageLicenseExpression</span><span class="sxs-lookup"><span data-stu-id="db222-243">PackageLicenseExpression</span></span>

<span data-ttu-id="db222-244">[SPDX licence identifikátor](https://spdx.org/licenses/) nebo výraz.</span><span class="sxs-lookup"><span data-stu-id="db222-244">An [SPDX license identifier](https://spdx.org/licenses/) or expression.</span></span> <span data-ttu-id="db222-245">Například, `Apache-2.0`.</span><span class="sxs-lookup"><span data-stu-id="db222-245">For example, `Apache-2.0`.</span></span>

<span data-ttu-id="db222-246">Tady je úplný seznam [SPDX licence identifikátory](https://spdx.org/licenses/).</span><span class="sxs-lookup"><span data-stu-id="db222-246">Here is the complete list of [SPDX license identifiers](https://spdx.org/licenses/).</span></span> <span data-ttu-id="db222-247">NuGet.org přijímá pouze OSI nebo licenci FSF schválení licence při použití výrazu typu.</span><span class="sxs-lookup"><span data-stu-id="db222-247">NuGet.org accepts only OSI or FSF approved licenses when using license type expression.</span></span>

<span data-ttu-id="db222-248">Syntaxe výrazů licence je popsaný dole v [ABNF](https://tools.ietf.org/html/rfc5234).</span><span class="sxs-lookup"><span data-stu-id="db222-248">The exact syntax of the license expressions is described below in [ABNF](https://tools.ietf.org/html/rfc5234).</span></span>

```cli
license-id            = <short form license identifier from https://spdx.org/spdx-specification-21-web-version#h.luq9dgcle9mo>

license-exception-id  = <short form license exception identifier from https://spdx.org/spdx-specification-21-web-version#h.ruv3yl8g6czd>

simple-expression = license-id / license-id”+”

compound-expression =  1*1(simple-expression /
                simple-expression "WITH" license-exception-id /
                compound-expression "AND" compound-expression /
                compound-expression "OR" compound-expression ) /
                "(" compound-expression ")" )

license-expression =  1*1(simple-expression / compound-expression / UNLICENSED)
```

> [!NOTE]
> <span data-ttu-id="db222-249">Pouze jeden z `PackageLicenseExpression`, `PackageLicenseFile` a `PackageLicenseUrl` lze zadat najednou.</span><span class="sxs-lookup"><span data-stu-id="db222-249">Only one of `PackageLicenseExpression`, `PackageLicenseFile` and `PackageLicenseUrl` can be specified at a time.</span></span>

### <a name="packagelicensefile"></a><span data-ttu-id="db222-250">PackageLicenseFile</span><span class="sxs-lookup"><span data-stu-id="db222-250">PackageLicenseFile</span></span>

<span data-ttu-id="db222-251">Cesta k souboru licencí v rámci balíčku, pokud používáte licenci, která ještě není přiřazený identifikátor SPDX, nebo vlastní licenci (jinak `PackageLicenseExpression` je upřednostňované)</span><span class="sxs-lookup"><span data-stu-id="db222-251">Path to a license file within the package if you are using a license that hasn’t been assigned an SPDX identifier, or it is a custom license (Otherwise `PackageLicenseExpression` is prefered)</span></span>

<span data-ttu-id="db222-252">Nahradí `PackageLicenseUrl`, nelze kombinovat s `PackageLicenseExpression` a vyžaduje Visual Studio 15.9.4 2.1.502 nebo 2.2.101, sady .NET SDK nebo novější.</span><span class="sxs-lookup"><span data-stu-id="db222-252">Replaces `PackageLicenseUrl`, can't be combined with `PackageLicenseExpression` and requires Visual Studio 15.9.4, .NET SDK 2.1.502 or 2.2.101, or newer.</span></span>

<span data-ttu-id="db222-253">Budete muset zajistit, že soubor s licencí je zabalena tak, že explicitně přidáte k projektu, příklady použití:</span><span class="sxs-lookup"><span data-stu-id="db222-253">You will need to ensure the license file is packed by adding it explicitly to the project, example usage:</span></span>

```xml
<PropertyGroup>
  <PackageLicenseFile>LICENSE.txt</PackageLicenseFile>
</PropertyGroup>
<ItemGroup>
  <None Include="licenses\LICENSE.txt" Pack="true" PackagePath="$(PackageLicenseFile)"/>
</ItemGroup>
```

### <a name="packagelicenseurl"></a><span data-ttu-id="db222-254">PackageLicenseUrl</span><span class="sxs-lookup"><span data-stu-id="db222-254">PackageLicenseUrl</span></span>

<span data-ttu-id="db222-255">Adresu URL licence, která se vztahuje na balíček.</span><span class="sxs-lookup"><span data-stu-id="db222-255">An URL to the license that is applicable to the package.</span></span> <span data-ttu-id="db222-256">(_zastaralé od verze Visual Studio 15.9.4, sady .NET SDK 2.1.502 a 2.2.101_)</span><span class="sxs-lookup"><span data-stu-id="db222-256">(_deprecated since Visual Studio 15.9.4, .NET SDK 2.1.502 and 2.2.101_)</span></span>


### <a name="packageiconurl"></a><span data-ttu-id="db222-257">PackageIconUrl</span><span class="sxs-lookup"><span data-stu-id="db222-257">PackageIconUrl</span></span>

<span data-ttu-id="db222-258">Adresa URL pro bitovou kopii 64 x 64 s průhledným pozadím použít jako ikona pro balíček zobrazená v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="db222-258">A URL for a 64x64 image with transparent background to use as the icon for the package in UI display.</span></span>

### <a name="packagereleasenotes"></a><span data-ttu-id="db222-259">PackageReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="db222-259">PackageReleaseNotes</span></span>

<span data-ttu-id="db222-260">Zpráva k vydání verze pro balíček.</span><span class="sxs-lookup"><span data-stu-id="db222-260">Release notes for the package.</span></span>

### <a name="packagetags"></a><span data-ttu-id="db222-261">PackageTags</span><span class="sxs-lookup"><span data-stu-id="db222-261">PackageTags</span></span>

<span data-ttu-id="db222-262">Středníkem oddělený seznam značek, který určuje balíček.</span><span class="sxs-lookup"><span data-stu-id="db222-262">A semicolon-delimited list of tags that designates the package.</span></span>

### <a name="packageoutputpath"></a><span data-ttu-id="db222-263">PackageOutputPath</span><span class="sxs-lookup"><span data-stu-id="db222-263">PackageOutputPath</span></span>

<span data-ttu-id="db222-264">Určuje výstupní cesta, ve kterém se zahodí komprimovaný balíček.</span><span class="sxs-lookup"><span data-stu-id="db222-264">Determines the output path in which the packed package will be dropped.</span></span> <span data-ttu-id="db222-265">Výchozí hodnota je `$(OutputPath)`.</span><span class="sxs-lookup"><span data-stu-id="db222-265">Default is `$(OutputPath)`.</span></span>

### <a name="includesymbols"></a><span data-ttu-id="db222-266">IncludeSymbols</span><span class="sxs-lookup"><span data-stu-id="db222-266">IncludeSymbols</span></span>

<span data-ttu-id="db222-267">Tato logická hodnota označuje, zda by měl balíček tehdy, když je zabalit projekt vytvořit balíček dalších symbolů.</span><span class="sxs-lookup"><span data-stu-id="db222-267">This Boolean value indicates whether the package should create an additional symbols package when the project is packed.</span></span> <span data-ttu-id="db222-268">Tento balíček bude mít *. symbols.nupkg* rozšíření a bude kopírovat soubory PDB spolu s knihovny DLL a ostatních výstupních souborů.</span><span class="sxs-lookup"><span data-stu-id="db222-268">This package will have a *.symbols.nupkg* extension and will copy the PDB files along with the DLL and other output files.</span></span>

### <a name="includesource"></a><span data-ttu-id="db222-269">IncludeSource</span><span class="sxs-lookup"><span data-stu-id="db222-269">IncludeSource</span></span>

<span data-ttu-id="db222-270">Tato logická hodnota značí, zda proces pack by měl vytvářet zdrojového balíčku.</span><span class="sxs-lookup"><span data-stu-id="db222-270">This Boolean value indicates whether the pack process should create a source package.</span></span> <span data-ttu-id="db222-271">Zdrojový balíček obsahuje knihovny zdrojový kód a soubory PDB.</span><span class="sxs-lookup"><span data-stu-id="db222-271">The source package contains the library's source code as well as PDB files.</span></span> <span data-ttu-id="db222-272">Zdrojové soubory jsou umístěny na `src/ProjectName` adresáře ve výsledném souboru balíčku.</span><span class="sxs-lookup"><span data-stu-id="db222-272">Source files are put under the `src/ProjectName` directory in the resulting package file.</span></span>

### <a name="istool"></a><span data-ttu-id="db222-273">IsTool</span><span class="sxs-lookup"><span data-stu-id="db222-273">IsTool</span></span>

<span data-ttu-id="db222-274">Určuje, zda jsou všechny výstupní soubory zkopírovány do *nástroje* složky namísto *lib* složky.</span><span class="sxs-lookup"><span data-stu-id="db222-274">Specifies whether all output files are copied to the *tools* folder instead of the *lib* folder.</span></span> <span data-ttu-id="db222-275">Všimněte si, že se liší od `DotNetCliTool` který je určený nastavením `PackageType` v *.csproj* souboru.</span><span class="sxs-lookup"><span data-stu-id="db222-275">Note that this is different from a `DotNetCliTool` which is specified by setting the `PackageType` in the *.csproj* file.</span></span>

### <a name="repositoryurl"></a><span data-ttu-id="db222-276">RepositoryUrl</span><span class="sxs-lookup"><span data-stu-id="db222-276">RepositoryUrl</span></span>

<span data-ttu-id="db222-277">Určuje adresu URL úložiště, kde se nachází zdrojový kód pro balíček a/nebo z kterého se má být sestaven.</span><span class="sxs-lookup"><span data-stu-id="db222-277">Specifies the URL for the repository where the source code for the package resides and/or from which it's being built.</span></span>

### <a name="repositorytype"></a><span data-ttu-id="db222-278">RepositoryType</span><span class="sxs-lookup"><span data-stu-id="db222-278">RepositoryType</span></span>

<span data-ttu-id="db222-279">Určuje typ úložiště.</span><span class="sxs-lookup"><span data-stu-id="db222-279">Specifies the type of the repository.</span></span> <span data-ttu-id="db222-280">Výchozí hodnota je "git".</span><span class="sxs-lookup"><span data-stu-id="db222-280">Default is "git".</span></span>

### <a name="nopackageanalysis"></a><span data-ttu-id="db222-281">NoPackageAnalysis</span><span class="sxs-lookup"><span data-stu-id="db222-281">NoPackageAnalysis</span></span>

<span data-ttu-id="db222-282">Určuje, že balíček by neměl balíčku spustit jeho analýzu po sestavení.</span><span class="sxs-lookup"><span data-stu-id="db222-282">Specifies that pack should not run package analysis after building the package.</span></span>

### <a name="minclientversion"></a><span data-ttu-id="db222-283">MinClientVersion</span><span class="sxs-lookup"><span data-stu-id="db222-283">MinClientVersion</span></span>

<span data-ttu-id="db222-284">Určuje minimální verzi klienta NuGet, který můžete nainstalovat tento balíček, vynucuje nuget.exe a Správce balíčků sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="db222-284">Specifies the minimum version of the NuGet client that can install this package, enforced by nuget.exe and the Visual Studio Package Manager.</span></span>

### <a name="includebuildoutput"></a><span data-ttu-id="db222-285">IncludeBuildOutput</span><span class="sxs-lookup"><span data-stu-id="db222-285">IncludeBuildOutput</span></span>

<span data-ttu-id="db222-286">Tato logické hodnoty Určuje, zda sestavení výstupu sestavení by měl být zabaleny do *.nupkg* souboru nebo ne.</span><span class="sxs-lookup"><span data-stu-id="db222-286">This Boolean values specifies whether the build output assemblies should be packed into the *.nupkg* file or not.</span></span>

### <a name="includecontentinpack"></a><span data-ttu-id="db222-287">IncludeContentInPack</span><span class="sxs-lookup"><span data-stu-id="db222-287">IncludeContentInPack</span></span>

<span data-ttu-id="db222-288">Tato logická hodnota určuje, zda všechny položky, které mají typ `Content` výsledný balíček bude obsahovat automaticky.</span><span class="sxs-lookup"><span data-stu-id="db222-288">This Boolean value specifies whether any items that have a type of `Content` will be included in the resulting package automatically.</span></span> <span data-ttu-id="db222-289">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="db222-289">The default is `true`.</span></span>

### <a name="buildoutputtargetfolder"></a><span data-ttu-id="db222-290">BuildOutputTargetFolder</span><span class="sxs-lookup"><span data-stu-id="db222-290">BuildOutputTargetFolder</span></span>

<span data-ttu-id="db222-291">Určuje složku, kam chcete umístit výstup sestavení.</span><span class="sxs-lookup"><span data-stu-id="db222-291">Specifies the folder where to place the output assemblies.</span></span> <span data-ttu-id="db222-292">Výstup sestavení (a ostatních výstupních souborů) jsou zkopírovány do složky jejich příslušných rozhraní framework.</span><span class="sxs-lookup"><span data-stu-id="db222-292">The output assemblies (and other output files) are copied into their respective framework folders.</span></span>

### <a name="contenttargetfolders"></a><span data-ttu-id="db222-293">ContentTargetFolders</span><span class="sxs-lookup"><span data-stu-id="db222-293">ContentTargetFolders</span></span>

<span data-ttu-id="db222-294">Tato vlastnost určuje výchozí umístění, kde by měl přejděte všechny soubory obsahu, pokud `PackagePath` není zadaný pro ně.</span><span class="sxs-lookup"><span data-stu-id="db222-294">This property specifies the default location of where all the content files should go if `PackagePath` is not specified for them.</span></span> <span data-ttu-id="db222-295">Výchozí hodnota je "obsah; contentFiles".</span><span class="sxs-lookup"><span data-stu-id="db222-295">The default value is "content;contentFiles".</span></span>

### <a name="nuspecfile"></a><span data-ttu-id="db222-296">NuspecFile</span><span class="sxs-lookup"><span data-stu-id="db222-296">NuspecFile</span></span>

<span data-ttu-id="db222-297">Relativní nebo absolutní cesta k *souboru .nuspec* souboru se používají pro balení.</span><span class="sxs-lookup"><span data-stu-id="db222-297">Relative or absolute path to the *.nuspec* file being used for packing.</span></span>

> [!NOTE]
> <span data-ttu-id="db222-298">Pokud *souboru .nuspec* soubor zadán, použije se **výhradně** pro balení informace a informace v projektech se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="db222-298">If the *.nuspec* file is specified, it's used **exclusively** for packaging information and any information in the projects is not used.</span></span>

### <a name="nuspecbasepath"></a><span data-ttu-id="db222-299">NuspecBasePath</span><span class="sxs-lookup"><span data-stu-id="db222-299">NuspecBasePath</span></span>

<span data-ttu-id="db222-300">Základní cesta pro *souboru .nuspec* souboru.</span><span class="sxs-lookup"><span data-stu-id="db222-300">Base path for the *.nuspec* file.</span></span>

### <a name="nuspecproperties"></a><span data-ttu-id="db222-301">NuspecProperties</span><span class="sxs-lookup"><span data-stu-id="db222-301">NuspecProperties</span></span>

<span data-ttu-id="db222-302">Středníkem oddělený seznam klíč = dvojice hodnot.</span><span class="sxs-lookup"><span data-stu-id="db222-302">Semicolon separated list of key=value pairs.</span></span>

## <a name="assemblyinfo-properties"></a><span data-ttu-id="db222-303">Vlastnosti souboru AssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="db222-303">AssemblyInfo properties</span></span>

<span data-ttu-id="db222-304">[Atributy sestavení](../../framework/app-domains/set-assembly-attributes.md) , která se obvykle používají ve *AssemblyInfo* souboru jsou teď automaticky generovány z vlastností.</span><span class="sxs-lookup"><span data-stu-id="db222-304">[Assembly attributes](../../framework/app-domains/set-assembly-attributes.md) that were typically present in an *AssemblyInfo* file are now automatically generated from properties.</span></span>

### <a name="properties-per-attribute"></a><span data-ttu-id="db222-305">Každý atribut vlastnosti</span><span class="sxs-lookup"><span data-stu-id="db222-305">Properties per attribute</span></span>

<span data-ttu-id="db222-306">Každý atribut má vlastnosti, které řídí jeho obsah a druhou pro zakázání jeho generaci, jak je znázorněno v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="db222-306">Each attribute has a property that control its content and another to disable its generation as shown in the following table:</span></span>

| <span data-ttu-id="db222-307">Atribut</span><span class="sxs-lookup"><span data-stu-id="db222-307">Attribute</span></span>                                                      | <span data-ttu-id="db222-308">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="db222-308">Property</span></span>               | <span data-ttu-id="db222-309">Vlastnost pro zákaz</span><span class="sxs-lookup"><span data-stu-id="db222-309">Property to disable</span></span>                             |
|----------------------------------------------------------------|------------------------|-------------------------------------------------|
| <xref:System.Reflection.AssemblyCompanyAttribute>              | `Company`              | `GenerateAssemblyCompanyAttribute`              |
| <xref:System.Reflection.AssemblyConfigurationAttribute>        | `Configuration`        | `GenerateAssemblyConfigurationAttribute`        |
| <xref:System.Reflection.AssemblyCopyrightAttribute>            | `Copyright`            | `GenerateAssemblyCopyrightAttribute`            |
| <xref:System.Reflection.AssemblyDescriptionAttribute>          | `Description`          | `GenerateAssemblyDescriptionAttribute`          |
| <xref:System.Reflection.AssemblyFileVersionAttribute>          | `FileVersion`          | `GenerateAssemblyFileVersionAttribute`          |
| <xref:System.Reflection.AssemblyInformationalVersionAttribute> | `InformationalVersion` | `GenerateAssemblyInformationalVersionAttribute` |
| <xref:System.Reflection.AssemblyProductAttribute>              | `Product`              | `GenerateAssemblyProductAttribute`              |
| <xref:System.Reflection.AssemblyTitleAttribute>                | `AssemblyTitle`        | `GenerateAssemblyTitleAttribute`                |
| <xref:System.Reflection.AssemblyVersionAttribute>              | `AssemblyVersion`      | `GenerateAssemblyVersionAttribute`              |
| <xref:System.Resources.NeutralResourcesLanguageAttribute>      | `NeutralLanguage`      | `GenerateNeutralResourcesLanguageAttribute`     |

<span data-ttu-id="db222-310">Poznámky:</span><span class="sxs-lookup"><span data-stu-id="db222-310">Notes:</span></span>

* <span data-ttu-id="db222-311">`AssemblyVersion` a `FileVersion` výchozí je převést hodnotu `$(Version)` bez přípony.</span><span class="sxs-lookup"><span data-stu-id="db222-311">`AssemblyVersion` and `FileVersion` default is to take the value of `$(Version)` without suffix.</span></span> <span data-ttu-id="db222-312">Například pokud `$(Version)` je `1.2.3-beta.4`, pak bude hodnota `1.2.3`.</span><span class="sxs-lookup"><span data-stu-id="db222-312">For example, if `$(Version)` is `1.2.3-beta.4`, then the value would be `1.2.3`.</span></span>
* <span data-ttu-id="db222-313">`InformationalVersion` Výchozí hodnota je hodnota `$(Version)`.</span><span class="sxs-lookup"><span data-stu-id="db222-313">`InformationalVersion` defaults to the value of `$(Version)`.</span></span>
* <span data-ttu-id="db222-314">`InformationalVersion` má `$(SourceRevisionId)` připojí, pokud vlastnost je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="db222-314">`InformationalVersion` has `$(SourceRevisionId)` appended if the property is present.</span></span> <span data-ttu-id="db222-315">Je možné ho zakázat, pomocí `IncludeSourceRevisionInInformationalVersion`.</span><span class="sxs-lookup"><span data-stu-id="db222-315">It can be disabled using `IncludeSourceRevisionInInformationalVersion`.</span></span>
* <span data-ttu-id="db222-316">`Copyright` a `Description` vlastnosti jsou také používány pro NuGet metadat.</span><span class="sxs-lookup"><span data-stu-id="db222-316">`Copyright` and `Description` properties are also used for NuGet metadata.</span></span>
* <span data-ttu-id="db222-317">`Configuration` je sdílený v procesu sestavení a nastavené přes `--configuration` parametr `dotnet` příkazy.</span><span class="sxs-lookup"><span data-stu-id="db222-317">`Configuration` is shared with all the build process and set via the `--configuration` parameter of `dotnet` commands.</span></span>

### <a name="generateassemblyinfo"></a><span data-ttu-id="db222-318">GenerateAssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="db222-318">GenerateAssemblyInfo</span></span>

<span data-ttu-id="db222-319">Logická hodnota, která povolí nebo zakáže všechny generování souboru AssemblyInfo.</span><span class="sxs-lookup"><span data-stu-id="db222-319">A Boolean that enable or disable all the AssemblyInfo generation.</span></span> <span data-ttu-id="db222-320">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="db222-320">The default value is `true`.</span></span>

### <a name="generatedassemblyinfofile"></a><span data-ttu-id="db222-321">GeneratedAssemblyInfoFile</span><span class="sxs-lookup"><span data-stu-id="db222-321">GeneratedAssemblyInfoFile</span></span>

<span data-ttu-id="db222-322">Cestu k souboru informací o vygenerované sestavení.</span><span class="sxs-lookup"><span data-stu-id="db222-322">The path of the generated assembly info file.</span></span> <span data-ttu-id="db222-323">Ve výchozím nastavení v souboru `$(IntermediateOutputPath)` adresáře (obj).</span><span class="sxs-lookup"><span data-stu-id="db222-323">Default to a file in the `$(IntermediateOutputPath)` (obj) directory.</span></span>
