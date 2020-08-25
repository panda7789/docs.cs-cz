---
title: Přidání do formátu csproj pro .NET Core
description: Přečtěte si o rozdílech mezi existujícími a soubory .NET Core csproj.
ms.topic: reference
ms.date: 04/08/2019
ms.openlocfilehash: 7760dc095fa894b1f356c939eb030e675f58a876
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88810882"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a><span data-ttu-id="ece56-103">Přidání do formátu csproj pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="ece56-103">Additions to the csproj format for .NET Core</span></span>

<span data-ttu-id="ece56-104">Tento dokument popisuje změny, které byly přidány do souborů projektu jako součást přesunutí z *project.jsna* do *csproj* a [MSBuild](https://github.com/Microsoft/MSBuild).</span><span class="sxs-lookup"><span data-stu-id="ece56-104">This document outlines the changes that were added to the project files as part of the move from *project.json* to *csproj* and [MSBuild](https://github.com/Microsoft/MSBuild).</span></span> <span data-ttu-id="ece56-105">Další informace o obecných syntaxech souborů projektu a referenčních informacích naleznete v dokumentaci k [souboru projektu MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) .</span><span class="sxs-lookup"><span data-stu-id="ece56-105">For more information about general project file syntax and reference, see [the MSBuild project file](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation.</span></span>

## <a name="implicit-package-references"></a><span data-ttu-id="ece56-106">Odkazy na implicitní balíčky</span><span class="sxs-lookup"><span data-stu-id="ece56-106">Implicit package references</span></span>

<span data-ttu-id="ece56-107">Na metabalíčky se implicitně odkazuje na základě cílových rozhraní, která jsou určená v `<TargetFramework>` vlastnosti nebo `<TargetFrameworks>` souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="ece56-107">Metapackages are implicitly referenced based on the target framework(s) specified in the `<TargetFramework>` or `<TargetFrameworks>` property of your project file.</span></span> <span data-ttu-id="ece56-108">`<TargetFrameworks>` se ignoruje `<TargetFramework>` , pokud je zadaný, nezávisle na pořadí.</span><span class="sxs-lookup"><span data-stu-id="ece56-108">`<TargetFrameworks>` is ignored if `<TargetFramework>` is specified, independent of order.</span></span>

```xml
 <PropertyGroup>
   <TargetFramework>netcoreapp3.1</TargetFramework>
 </PropertyGroup>
 ```

 ```xml
 <PropertyGroup>
   <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
 </PropertyGroup>
 ```

### <a name="recommendations"></a><span data-ttu-id="ece56-109">Doporučení</span><span class="sxs-lookup"><span data-stu-id="ece56-109">Recommendations</span></span>

<span data-ttu-id="ece56-110">Vzhledem `Microsoft.NETCore.App` `NETStandard.Library` k tomu, že jsou implicitně odkazovány na nebo metabalíčky, následující doporučené osvědčené postupy:</span><span class="sxs-lookup"><span data-stu-id="ece56-110">Since `Microsoft.NETCore.App` or `NETStandard.Library` metapackages are implicitly referenced, the following are our recommended best practices:</span></span>

- <span data-ttu-id="ece56-111">Pokud cílíte na rozhraní .NET Core nebo .NET Standard, nikdy nepoužívejte explicitní odkaz na `Microsoft.NETCore.App` nebo `NETStandard.Library` metabalíčky prostřednictvím `<PackageReference>` položky v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="ece56-111">When targeting .NET Core or .NET Standard, never have an explicit reference to the `Microsoft.NETCore.App` or `NETStandard.Library` metapackages via a `<PackageReference>` item in your project file.</span></span>
- <span data-ttu-id="ece56-112">Pokud potřebujete specifickou verzi modulu runtime při cílení na .NET Core, měli byste použít `<RuntimeFrameworkVersion>` vlastnost v projektu (například `1.0.4` ) namísto odkazování na Metapackage.</span><span class="sxs-lookup"><span data-stu-id="ece56-112">If you need a specific version of the runtime when targeting .NET Core, you should use the `<RuntimeFrameworkVersion>` property in your project (for example, `1.0.4`) instead of referencing the metapackage.</span></span>
  - <span data-ttu-id="ece56-113">K tomu může dojít, pokud používáte [samostatná nasazení](../deploying/index.md#publish-self-contained) a potřebujete konkrétní opravu verze 1.0.0 LTS runtime, například.</span><span class="sxs-lookup"><span data-stu-id="ece56-113">This might happen if you are using [self-contained deployments](../deploying/index.md#publish-self-contained) and you need a specific patch version of 1.0.0 LTS runtime, for example.</span></span>
- <span data-ttu-id="ece56-114">Pokud potřebujete specifickou verzi `NETStandard.Library` Metapackage při cílení na .NET Standard, můžete použít `<NetStandardImplicitPackageVersion>` vlastnost a nastavit verzi, kterou potřebujete.</span><span class="sxs-lookup"><span data-stu-id="ece56-114">If you need a specific version of the `NETStandard.Library` metapackage when targeting .NET Standard, you can use the `<NetStandardImplicitPackageVersion>` property and set the version you need.</span></span>
- <span data-ttu-id="ece56-115">Neprovádějte explicitní přidávání nebo aktualizaci odkazů na `Microsoft.NETCore.App` Metapackage nebo `NETStandard.Library` v projektech .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ece56-115">Don't explicitly add or update references to either the `Microsoft.NETCore.App` or `NETStandard.Library` metapackage in .NET Framework projects.</span></span> <span data-ttu-id="ece56-116">Pokud `NETStandard.Library` je při použití balíčku NuGet založeného na .NET Standard potřebná nějaká verze, NuGet tuto verzi nainstaluje automaticky.</span><span class="sxs-lookup"><span data-stu-id="ece56-116">If any version of `NETStandard.Library` is needed when using a .NET Standard-based NuGet package, NuGet automatically installs that version.</span></span>

## <a name="implicit-version-for-some-package-references"></a><span data-ttu-id="ece56-117">Implicitní verze pro některé odkazy na balíčky</span><span class="sxs-lookup"><span data-stu-id="ece56-117">Implicit version for some package references</span></span>

<span data-ttu-id="ece56-118">Většina použití [`<PackageReference>`](#packagereference) parametru vyžaduje nastavení `Version` atributu k určení verze balíčku NuGet, která se má použít.</span><span class="sxs-lookup"><span data-stu-id="ece56-118">Most usages of [`<PackageReference>`](#packagereference) require setting the `Version` attribute to specify the NuGet package version to be used.</span></span> <span data-ttu-id="ece56-119">Při použití .NET Core 2,1 nebo 2,2 a odkazování na [Microsoft. AspNetCore. app](/aspnet/core/fundamentals/metapackage-app) nebo [Microsoft. AspNetCore. All](/aspnet/core/fundamentals/metapackage)ale atribut není zbytečný.</span><span class="sxs-lookup"><span data-stu-id="ece56-119">When using .NET Core 2.1 or 2.2 and referencing [Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) or [Microsoft.AspNetCore.All](/aspnet/core/fundamentals/metapackage), however, the  attribute is unnecessary.</span></span> <span data-ttu-id="ece56-120">.NET Core SDK může automaticky vybrat verzi těchto balíčků, které by se měly použít.</span><span class="sxs-lookup"><span data-stu-id="ece56-120">The .NET Core SDK can automatically select the version of these packages that should be used.</span></span>

### <a name="recommendation"></a><span data-ttu-id="ece56-121">Doporučení</span><span class="sxs-lookup"><span data-stu-id="ece56-121">Recommendation</span></span>

<span data-ttu-id="ece56-122">Při odkazování na `Microsoft.AspNetCore.App` balíčky nebo nezadávejte `Microsoft.AspNetCore.All` jejich verzi.</span><span class="sxs-lookup"><span data-stu-id="ece56-122">When referencing the `Microsoft.AspNetCore.App` or `Microsoft.AspNetCore.All` packages, do not specify their version.</span></span> <span data-ttu-id="ece56-123">Pokud je zadána verze, sada SDK může vytvořit upozornění NETSDK1071.</span><span class="sxs-lookup"><span data-stu-id="ece56-123">If a version is specified, the SDK may produce warning NETSDK1071.</span></span> <span data-ttu-id="ece56-124">Chcete-li toto upozornění vyřešit, odeberte verzi balíčku, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ece56-124">To fix this warning, remove the package version like in the following example:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore.App" />
</ItemGroup>
```

> <span data-ttu-id="ece56-125">Známý problém: sada .NET Core 2,1 SDK podporuje pouze tuto syntaxi pouze v případě, že projekt používá také Microsoft. NET. SDK. Web.</span><span class="sxs-lookup"><span data-stu-id="ece56-125">Known issue: the .NET Core 2.1 SDK only supported this syntax when the project also uses Microsoft.NET.Sdk.Web.</span></span> <span data-ttu-id="ece56-126">To je vyřešeno v sadě .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="ece56-126">This is resolved in the .NET Core 2.2 SDK.</span></span>

<span data-ttu-id="ece56-127">Tyto odkazy na ASP.NET Core metabalíčky mají mírně odlišné chování z většiny běžných balíčků NuGet.</span><span class="sxs-lookup"><span data-stu-id="ece56-127">These references to ASP.NET Core metapackages have a slightly different behavior from most normal NuGet packages.</span></span> <span data-ttu-id="ece56-128">[Nasazení aplikací závislých na rozhraních](../deploying/index.md#publish-framework-dependent) , která používají tyto metabalíčky, automaticky využívají ASP.NET Core sdílené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ece56-128">[Framework-dependent deployments](../deploying/index.md#publish-framework-dependent) of applications that use these metapackages automatically take advantage of the ASP.NET Core shared framework.</span></span> <span data-ttu-id="ece56-129">Při použití metabalíčky se s aplikací nasadí **žádné** prostředky z odkazovaného ASP.NET Core balíčků NuGet – ASP.NET Core sdílené rozhraní obsahuje tyto prostředky.</span><span class="sxs-lookup"><span data-stu-id="ece56-129">When you use the metapackages, **no** assets from the referenced ASP.NET Core NuGet packages are deployed with the application—the ASP.NET Core shared framework contains these assets.</span></span> <span data-ttu-id="ece56-130">Prostředky ve sdíleném rozhraní jsou optimalizované pro cílovou platformu pro zlepšení času spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="ece56-130">The assets in the shared framework are optimized for the target platform to improve application startup time.</span></span> <span data-ttu-id="ece56-131">Další informace o sdílených rozhraních naleznete v tématu [distribuční balíček .NET Core](../distribution-packaging.md).</span><span class="sxs-lookup"><span data-stu-id="ece56-131">For more information about shared framework, see [.NET Core distribution packaging](../distribution-packaging.md).</span></span>

<span data-ttu-id="ece56-132">*Je* -li zadána verze, je zpracována jako *minimální* verze ASP.NET Core sdílené architektury pro nasazení závislá na rozhraních a jako *Přesná* verze pro samostatně nasazená nasazení.</span><span class="sxs-lookup"><span data-stu-id="ece56-132">If a version *is* specified, it's treated as the *minimum* version of ASP.NET Core shared framework for framework-dependent deployments and as an *exact* version for self-contained deployments.</span></span> <span data-ttu-id="ece56-133">To může mít následující důsledky:</span><span class="sxs-lookup"><span data-stu-id="ece56-133">This can have the following consequences:</span></span>

- <span data-ttu-id="ece56-134">Pokud je verze ASP.NET Core nainstalovaná na serveru menší než verze zadaná na PackageReference, proces .NET Core se nepovede spustit.</span><span class="sxs-lookup"><span data-stu-id="ece56-134">If the version of ASP.NET Core installed on the server is less than the version specified on the PackageReference, the .NET Core process fails to launch.</span></span> <span data-ttu-id="ece56-135">Aktualizace Metapackage jsou často k dispozici v NuGet.org před zpřístupněním aktualizací v hostitelských prostředích, jako je Azure.</span><span class="sxs-lookup"><span data-stu-id="ece56-135">Updates to the metapackage are often available on NuGet.org before updates have been made available in hosting environments such as Azure.</span></span> <span data-ttu-id="ece56-136">Aktualizace verze PackageReference na ASP.NET Core by mohla způsobit selhání nasazené aplikace.</span><span class="sxs-lookup"><span data-stu-id="ece56-136">Updating the version on the PackageReference to ASP.NET Core could cause a deployed application to fail.</span></span>
- <span data-ttu-id="ece56-137">Pokud je aplikace nasazena jako [samostatné nasazení](../deploying/index.md#publish-self-contained), aplikace nemusí obsahovat nejnovější aktualizace zabezpečení .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ece56-137">If the application is deployed as a [self-contained deployment](../deploying/index.md#publish-self-contained), the application may not contain the latest security updates to .NET Core.</span></span> <span data-ttu-id="ece56-138">Pokud není určena verze, může sada SDK automaticky zahrnovat nejnovější verzi ASP.NET Core v samostatném nasazení.</span><span class="sxs-lookup"><span data-stu-id="ece56-138">When a version isn't specified, the SDK can automatically include the newest version of ASP.NET Core in the self-contained deployment.</span></span>

## <a name="default-compilation-includes-in-net-core-projects"></a><span data-ttu-id="ece56-139">Výchozí kompilace zahrnuje v projektech .NET Core</span><span class="sxs-lookup"><span data-stu-id="ece56-139">Default compilation includes in .NET Core projects</span></span>

<span data-ttu-id="ece56-140">S přesunem do formátu *csproj* v nejnovějších verzích sady SDK jsme přesunuli výchozí zahrnutí a vyloučení položek kompilace a integrovaných prostředků do souborů vlastností sady SDK.</span><span class="sxs-lookup"><span data-stu-id="ece56-140">With the move to the *csproj* format in the latest SDK versions, we've moved the default includes and excludes for compile items and embedded resources to the SDK properties files.</span></span> <span data-ttu-id="ece56-141">To znamená, že už nemusíte tyto položky v souboru projektu zadávat.</span><span class="sxs-lookup"><span data-stu-id="ece56-141">This means that you no longer need to specify these items in your project file.</span></span>

<span data-ttu-id="ece56-142">Hlavním důvodem pro to, aby to bylo, je omezit zbytečné soubory projektu.</span><span class="sxs-lookup"><span data-stu-id="ece56-142">The main reason for doing this is to reduce the clutter in your project file.</span></span> <span data-ttu-id="ece56-143">Výchozí hodnoty, které jsou obsaženy v sadě SDK, by měly pokrývat většinu běžných případů použití, takže je nemusíte opakovat v každém vytvořeném projektu.</span><span class="sxs-lookup"><span data-stu-id="ece56-143">The defaults that are present in the SDK should cover most common use cases, so there is no need to repeat them in every project that you create.</span></span> <span data-ttu-id="ece56-144">To vede k menšímu množství souborů projektu, které jsou v případě potřeby mnohem snazší a v případě potřeby upravitelné.</span><span class="sxs-lookup"><span data-stu-id="ece56-144">This leads to smaller project files that are much easier to understand as well as edit by hand, if needed.</span></span>

<span data-ttu-id="ece56-145">Následující tabulka ukazuje, který prvek a které [globy](https://en.wikipedia.org/wiki/Glob_(programming)) jsou zahrnuty a vyloučeny v sadě SDK:</span><span class="sxs-lookup"><span data-stu-id="ece56-145">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are both included and excluded in the SDK:</span></span>

| <span data-ttu-id="ece56-146">Prvek</span><span class="sxs-lookup"><span data-stu-id="ece56-146">Element</span></span>           | <span data-ttu-id="ece56-147">Zahrnout glob</span><span class="sxs-lookup"><span data-stu-id="ece56-147">Include glob</span></span>                              | <span data-ttu-id="ece56-148">Vyloučit glob</span><span class="sxs-lookup"><span data-stu-id="ece56-148">Exclude glob</span></span>                                                  | <span data-ttu-id="ece56-149">Odebrat glob</span><span class="sxs-lookup"><span data-stu-id="ece56-149">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| <span data-ttu-id="ece56-150">Sestavení</span><span class="sxs-lookup"><span data-stu-id="ece56-150">Compile</span></span>           | <span data-ttu-id="ece56-151">\*\*/\*cs (nebo jiné jazykové rozšíření)</span><span class="sxs-lookup"><span data-stu-id="ece56-151">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="ece56-152">\*\*/\*uživatelský  \*\*/\*.\* Souhrn  \*\*/\*. SLN  \*\*/\*. vssscc</span><span class="sxs-lookup"><span data-stu-id="ece56-152">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="ece56-153">Není k dispozici</span><span class="sxs-lookup"><span data-stu-id="ece56-153">N/A</span></span>                      |
| <span data-ttu-id="ece56-154">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="ece56-154">EmbeddedResource</span></span>  | <span data-ttu-id="ece56-155">\*\*/\*. resx</span><span class="sxs-lookup"><span data-stu-id="ece56-155">\*\*/\*.resx</span></span>                              | <span data-ttu-id="ece56-156">\*\*/\*uživatelský \*\*/\*.\* Souhrn \*\*/\*. SLN \*\*/\*. vssscc</span><span class="sxs-lookup"><span data-stu-id="ece56-156">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="ece56-157">Není k dispozici</span><span class="sxs-lookup"><span data-stu-id="ece56-157">N/A</span></span>                      |
| <span data-ttu-id="ece56-158">Žádné</span><span class="sxs-lookup"><span data-stu-id="ece56-158">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="ece56-159">\*\*/\*uživatelský \*\*/\*.\* Souhrn \*\*/\*. SLN \*\*/\*. vssscc</span><span class="sxs-lookup"><span data-stu-id="ece56-159">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="ece56-160">\*\*/\*cs \*\*/\*. RESX</span><span class="sxs-lookup"><span data-stu-id="ece56-160">\*\*/\*.cs; \*\*/\*.resx</span></span>   |

> [!NOTE]
> <span data-ttu-id="ece56-161">**Exclude glob** vždy vyloučí `./bin` složky a `./obj` , které jsou reprezentovány `$(BaseOutputPath)` vlastnostmi a `$(BaseIntermediateOutputPath)` , v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="ece56-161">**Exclude glob** always excludes the `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, respectively.</span></span> <span data-ttu-id="ece56-162">Všechna vyloučení jsou představována jako celek `$(DefaultItemExcludes)` .</span><span class="sxs-lookup"><span data-stu-id="ece56-162">As a whole, all excludes are represented by `$(DefaultItemExcludes)`.</span></span>

<span data-ttu-id="ece56-163">Pokud jste v projektu globy a pokusíte se ho sestavit pomocí nejnovější sady SDK, zobrazí se následující chyba:</span><span class="sxs-lookup"><span data-stu-id="ece56-163">If you have globs in your project and you try to build it using the newest SDK, you'll get the following error:</span></span>

> <span data-ttu-id="ece56-164">Byly zahrnuty duplicitní položky kompilace.</span><span class="sxs-lookup"><span data-stu-id="ece56-164">Duplicate Compile items were included.</span></span> <span data-ttu-id="ece56-165">Sada .NET SDK obsahuje ve výchozím nastavení položky kompilace z adresáře projektu.</span><span class="sxs-lookup"><span data-stu-id="ece56-165">The .NET SDK includes Compile items from your project directory by default.</span></span> <span data-ttu-id="ece56-166">Můžete buď odebrat tyto položky ze souboru projektu, nebo nastavit vlastnost ' EnableDefaultCompileItems ' na hodnotu ' false ', pokud je chcete explicitně zahrnout do souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="ece56-166">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

<span data-ttu-id="ece56-167">Chcete-li se této chybě vyhnout, můžete buď odebrat explicitní `Compile` položky, které odpovídají těm, které jsou uvedeny v předchozí tabulce, nebo můžete nastavit `<EnableDefaultCompileItems>` vlastnost na následujícím `false` způsobem:</span><span class="sxs-lookup"><span data-stu-id="ece56-167">In order to get around this error, you can either remove the explicit `Compile` items that match the ones listed on the previous table, or you can set the `<EnableDefaultCompileItems>` property to `false`, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

<span data-ttu-id="ece56-168">Nastavením této vlastnosti na `false` zakážete implicitní zahrnutí a vrátíte se do chování předchozích sad SDK, kde jste museli v projektu zadat výchozí globy.</span><span class="sxs-lookup"><span data-stu-id="ece56-168">Setting this property to `false` will disable implicit inclusion, reverting to the behavior of previous SDKs where you had to specify the default globs in your project.</span></span>

<span data-ttu-id="ece56-169">Tato změna neupravuje hlavní mechanismy ostatních zahrnutí.</span><span class="sxs-lookup"><span data-stu-id="ece56-169">This change does not modify the main mechanics of other includes.</span></span> <span data-ttu-id="ece56-170">Nicméně pokud chcete určit, například některé soubory, které mají být publikovány s vaší aplikací, můžete stále používat známé mechanismy v souboru *csproj* pro tento prvek (například `<Content>` element).</span><span class="sxs-lookup"><span data-stu-id="ece56-170">However, if you wish to specify, for example, some files to get published with your app, you can still use the known mechanisms in *csproj* for that (for example, the `<Content>` element).</span></span>

<span data-ttu-id="ece56-171">`<EnableDefaultCompileItems>` zakáže jenom `Compile` globy, ale neovlivní jiné globy, jako je implicitní `None` glob, které platí i pro \* položky. cs.</span><span class="sxs-lookup"><span data-stu-id="ece56-171">`<EnableDefaultCompileItems>` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob, which also applies to \*.cs items.</span></span> <span data-ttu-id="ece56-172">Z tohoto důvodu **Průzkumník řešení** nadále zobrazovat \* položky cs jako součást projektu zahrnuté jako `None` položky.</span><span class="sxs-lookup"><span data-stu-id="ece56-172">Because of that, **Solution Explorer** will continue show \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="ece56-173">Podobným způsobem můžete nastavit `<EnableDefaultNoneItems>` na hodnotu false, chcete-li zakázat implicitní `None` glob, například:</span><span class="sxs-lookup"><span data-stu-id="ece56-173">In a similar way, you can set `<EnableDefaultNoneItems>` to false to disable the implicit `None` glob, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

<span data-ttu-id="ece56-174">Chcete-li zakázat **všechny implicitní globy**, můžete nastavit `<EnableDefaultItems>` vlastnost na `false` jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ece56-174">To disable **all implicit globs**, you can set the `<EnableDefaultItems>` property to `false` as in the following example:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a><span data-ttu-id="ece56-175">Jak zobrazit celý projekt, když ho MSBuild uvidí</span><span class="sxs-lookup"><span data-stu-id="ece56-175">How to see the whole project as MSBuild sees it</span></span>

<span data-ttu-id="ece56-176">I když tyto změny csproj značně zjednodušují soubory projektu, je možné, že budete chtít zobrazit plně rozbalený projekt jako nástroj MSBuild, jakmile bude sada SDK a její cíle zahrnuté.</span><span class="sxs-lookup"><span data-stu-id="ece56-176">While those csproj changes greatly simplify project files, you might want to see the fully expanded project as MSBuild sees it once the SDK and its targets are included.</span></span> <span data-ttu-id="ece56-177">Projekt předzpracování pomocí [ `/pp` přepínače](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) [`dotnet msbuild`](dotnet-msbuild.md) příkazu, který ukazuje, které soubory jsou importovány, jejich zdroje a jejich příspěvky na sestavení bez skutečného sestavení projektu:</span><span class="sxs-lookup"><span data-stu-id="ece56-177">Preprocess the project with [the `/pp` switch](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) of the [`dotnet msbuild`](dotnet-msbuild.md) command, which shows which files are imported, their sources, and their contributions to the build without actually building the project:</span></span>

```dotnetcli
dotnet msbuild -pp:fullproject.xml
```

<span data-ttu-id="ece56-178">Pokud má projekt více cílových rozhraní, výsledky příkazu by měly být zaměřené jenom na jeden z nich zadáním jako vlastnost MSBuild:</span><span class="sxs-lookup"><span data-stu-id="ece56-178">If the project has multiple target frameworks, the results of the command should be focused on only one of them by specifying it as an MSBuild property:</span></span>

```dotnetcli
dotnet msbuild -p:TargetFramework=netcoreapp3.1 -pp:fullproject.xml
```

## <a name="additions"></a><span data-ttu-id="ece56-179">Rozšíření</span><span class="sxs-lookup"><span data-stu-id="ece56-179">Additions</span></span>

### <a name="sdk-attribute"></a><span data-ttu-id="ece56-180">Atribut sady SDK</span><span class="sxs-lookup"><span data-stu-id="ece56-180">Sdk attribute</span></span>

<span data-ttu-id="ece56-181">Kořenový `<Project>` element souboru *. csproj* má nový atribut s názvem `Sdk` .</span><span class="sxs-lookup"><span data-stu-id="ece56-181">The root `<Project>` element of the *.csproj* file has a new attribute called `Sdk`.</span></span> <span data-ttu-id="ece56-182">`Sdk` Určuje sadu SDK, kterou bude projekt používat.</span><span class="sxs-lookup"><span data-stu-id="ece56-182">`Sdk` specifies which SDK will be used by the project.</span></span> <span data-ttu-id="ece56-183">Sada SDK, jak popisuje [dokument vrstvení](cli-msbuild-architecture.md) , je sada [úloh](/visualstudio/msbuild/msbuild-tasks) a [cílů](/visualstudio/msbuild/msbuild-targets) nástroje MSBuild, které mohou sestavovat kód .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ece56-183">The SDK, as the [layering document](cli-msbuild-architecture.md) describes, is a set of MSBuild [tasks](/visualstudio/msbuild/msbuild-tasks) and [targets](/visualstudio/msbuild/msbuild-targets) that can build .NET Core code.</span></span> <span data-ttu-id="ece56-184">Pro .NET Core jsou k dispozici následující sady SDK:</span><span class="sxs-lookup"><span data-stu-id="ece56-184">The following SDKs are available for .NET Core:</span></span>

1. <span data-ttu-id="ece56-185">.NET Core SDK s ID `Microsoft.NET.Sdk`</span><span class="sxs-lookup"><span data-stu-id="ece56-185">The .NET Core SDK with the ID of `Microsoft.NET.Sdk`</span></span>
2. <span data-ttu-id="ece56-186">Sada Web SDK .NET Core s ID `Microsoft.NET.Sdk.Web`</span><span class="sxs-lookup"><span data-stu-id="ece56-186">The .NET Core web SDK with the ID of `Microsoft.NET.Sdk.Web`</span></span>
3. <span data-ttu-id="ece56-187">Sada SDK knihovny tříd .NET Core Razor s ID `Microsoft.NET.Sdk.Razor`</span><span class="sxs-lookup"><span data-stu-id="ece56-187">The .NET Core Razor Class Library SDK with the ID of `Microsoft.NET.Sdk.Razor`</span></span>
4. <span data-ttu-id="ece56-188">Služba pracovních procesů .NET Core s ID `Microsoft.NET.Sdk.Worker` (od .NET core 3,0)</span><span class="sxs-lookup"><span data-stu-id="ece56-188">The .NET Core Worker Service with the ID of `Microsoft.NET.Sdk.Worker` (since .NET Core 3.0)</span></span>
5. <span data-ttu-id="ece56-189">WinForms rozhraní .NET Core a WPF s ID `Microsoft.NET.Sdk.WindowsDesktop` (od .NET core 3,0)</span><span class="sxs-lookup"><span data-stu-id="ece56-189">The .NET Core WinForms and WPF with the ID of `Microsoft.NET.Sdk.WindowsDesktop` (since .NET Core 3.0)</span></span>

<span data-ttu-id="ece56-190">Aby bylo možné `Sdk` `<Project>` používat nástroje .NET Core a sestavovat kód, je nutné mít atribut nastaven na jedno z těchto identifikátorů v elementu.</span><span class="sxs-lookup"><span data-stu-id="ece56-190">You need to have the `Sdk` attribute set to one of those IDs on the `<Project>` element in order to use the .NET Core tools and build your code.</span></span>

### <a name="packagereference"></a><span data-ttu-id="ece56-191">PackageReference</span><span class="sxs-lookup"><span data-stu-id="ece56-191">PackageReference</span></span>

<span data-ttu-id="ece56-192">`<PackageReference>`Element Item Určuje [závislost NuGet v projektu](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="ece56-192">A `<PackageReference>` item element specifies a [NuGet dependency in the project](/nuget/consume-packages/package-references-in-project-files).</span></span> <span data-ttu-id="ece56-193">`Include`Atribut určuje ID balíčku.</span><span class="sxs-lookup"><span data-stu-id="ece56-193">The `Include` attribute specifies the package ID.</span></span>

```xml
<PackageReference Include="package-id" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a><span data-ttu-id="ece56-194">Verze</span><span class="sxs-lookup"><span data-stu-id="ece56-194">Version</span></span>

<span data-ttu-id="ece56-195">Požadovaný `Version` atribut určuje verzi balíčku, který má být obnoven.</span><span class="sxs-lookup"><span data-stu-id="ece56-195">The required `Version` attribute specifies the version of the package to restore.</span></span> <span data-ttu-id="ece56-196">Atribut respektuje pravidla schématu [rozsahu verzí NuGet](/nuget/concepts/package-versioning#version-ranges) .</span><span class="sxs-lookup"><span data-stu-id="ece56-196">The attribute respects the rules of the [NuGet version range](/nuget/concepts/package-versioning#version-ranges) scheme.</span></span> <span data-ttu-id="ece56-197">Výchozí chování je minimální verze (včetně shody).</span><span class="sxs-lookup"><span data-stu-id="ece56-197">The default behavior is a minimum version, inclusive match.</span></span> <span data-ttu-id="ece56-198">Zadání `Version="1.2.3"` je například ekvivalentní zápisu NuGet `[1.2.3, )` a znamená, že vyřešený balíček bude mít verzi 1.2.3, je-li k dispozici nebo více než jinak.</span><span class="sxs-lookup"><span data-stu-id="ece56-198">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3, )` and means the resolved package will have the version 1.2.3 if available or greater otherwise.</span></span>

#### <a name="includeassets-excludeassets-and-privateassets"></a><span data-ttu-id="ece56-199">IncludeAssets, ExcludeAssets a PrivateAssets</span><span class="sxs-lookup"><span data-stu-id="ece56-199">IncludeAssets, ExcludeAssets, and PrivateAssets</span></span>

<span data-ttu-id="ece56-200">`IncludeAssets` atribut určuje, které prostředky patřící k balíčku určenému parametr `<PackageReference>` by měly být spotřebovány.</span><span class="sxs-lookup"><span data-stu-id="ece56-200">`IncludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed.</span></span> <span data-ttu-id="ece56-201">Ve výchozím nastavení jsou zahrnuty všechny prostředky balíčku.</span><span class="sxs-lookup"><span data-stu-id="ece56-201">By default, all package assets are included.</span></span>

<span data-ttu-id="ece56-202">`ExcludeAssets` atribut určuje, které prostředky patřící do balíčku určeného `<PackageReference>` by neměly být spotřebovány.</span><span class="sxs-lookup"><span data-stu-id="ece56-202">`ExcludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should not be consumed.</span></span>

<span data-ttu-id="ece56-203">`PrivateAssets` atribut určuje, které prostředky patřící do balíčku určeného `<PackageReference>` by měly být spotřebovány, ale nikoli do dalšího projektu.</span><span class="sxs-lookup"><span data-stu-id="ece56-203">`PrivateAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed but not flow to the next project.</span></span> <span data-ttu-id="ece56-204">V `Analyzers` případě, že `Build` `ContentFiles` Tento atribut není k dispozici, jsou prostředky a majetky soukromé ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="ece56-204">The `Analyzers`, `Build` and `ContentFiles` assets are private by default when this attribute is not present.</span></span>

> [!NOTE]
> <span data-ttu-id="ece56-205">`PrivateAssets`je ekvivalentní *project.js* / elementu*xproj* `SuppressParent` .</span><span class="sxs-lookup"><span data-stu-id="ece56-205">`PrivateAssets` is equivalent to the *project.json*/*xproj* `SuppressParent` element.</span></span>

<span data-ttu-id="ece56-206">Tyto atributy mohou obsahovat jednu nebo více z následujících položek oddělených středníkem, `;` Pokud je uvedena více než jedna:</span><span class="sxs-lookup"><span data-stu-id="ece56-206">These attributes can contain one or more of the following items, separated by the semicolon `;` character if more than one is listed:</span></span>

- <span data-ttu-id="ece56-207">`Compile` – obsah složky *lib* je k dispozici pro zkompilování.</span><span class="sxs-lookup"><span data-stu-id="ece56-207">`Compile` – the contents of the *lib* folder are available to compile against.</span></span>
- <span data-ttu-id="ece56-208">`Runtime` – obsah *běhové* složky se distribuuje.</span><span class="sxs-lookup"><span data-stu-id="ece56-208">`Runtime` – the contents of the *runtime* folder are distributed.</span></span>
- <span data-ttu-id="ece56-209">`ContentFiles` – používá se obsah složky *contentFiles* .</span><span class="sxs-lookup"><span data-stu-id="ece56-209">`ContentFiles` – the contents of the *contentfiles* folder are used.</span></span>
- <span data-ttu-id="ece56-210">`Build` – jsou použity props/targets ve složce *sestavení* .</span><span class="sxs-lookup"><span data-stu-id="ece56-210">`Build` – the props/targets in the *build* folder are used.</span></span>
- <span data-ttu-id="ece56-211">`Native` – obsah z nativních assetů se zkopíruje do *výstupní* složky pro modul runtime.</span><span class="sxs-lookup"><span data-stu-id="ece56-211">`Native` – the contents from native assets are copied to the *output* folder for runtime.</span></span>
- <span data-ttu-id="ece56-212">`Analyzers` – Analyzátory se používají.</span><span class="sxs-lookup"><span data-stu-id="ece56-212">`Analyzers` – the analyzers are used.</span></span>

<span data-ttu-id="ece56-213">Atribut může případně obsahovat:</span><span class="sxs-lookup"><span data-stu-id="ece56-213">Alternatively, the attribute can contain:</span></span>

- <span data-ttu-id="ece56-214">`None` – žádný z prostředků se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="ece56-214">`None` – none of the assets are used.</span></span>
- <span data-ttu-id="ece56-215">`All` – používají se všechny prostředky.</span><span class="sxs-lookup"><span data-stu-id="ece56-215">`All` – all assets are used.</span></span>

### <a name="dotnetclitoolreference"></a><span data-ttu-id="ece56-216">DotNetCliToolReference</span><span class="sxs-lookup"><span data-stu-id="ece56-216">DotNetCliToolReference</span></span>

<span data-ttu-id="ece56-217">`<DotNetCliToolReference>`Element Item Určuje nástroj CLI, který uživatel chce obnovit v kontextu projektu.</span><span class="sxs-lookup"><span data-stu-id="ece56-217">A `<DotNetCliToolReference>` item element specifies the CLI tool that the user wants to restore in the context of the project.</span></span> <span data-ttu-id="ece56-218">Je náhradou za `tools` uzel v *project.js*.</span><span class="sxs-lookup"><span data-stu-id="ece56-218">It's a replacement for the `tools` node in *project.json*.</span></span>

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

<span data-ttu-id="ece56-219">Všimněte si, že `DotNetCliToolReference` se [teď zastaralá](https://github.com/dotnet/announcements/issues/107) s upřednostněním [místních nástrojů .NET Core](./global-tools.md#install-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="ece56-219">Note that `DotNetCliToolReference` is [now deprecated](https://github.com/dotnet/announcements/issues/107) in favor of [.NET Core Local Tools](./global-tools.md#install-a-local-tool).</span></span>

#### <a name="version"></a><span data-ttu-id="ece56-220">Verze</span><span class="sxs-lookup"><span data-stu-id="ece56-220">Version</span></span>

<span data-ttu-id="ece56-221">`Version` Určuje verzi balíčku, který se má obnovit.</span><span class="sxs-lookup"><span data-stu-id="ece56-221">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="ece56-222">Atribut respektuje pravidla schématu [správy verzí NuGet](/nuget/create-packages/dependency-versions#version-ranges) .</span><span class="sxs-lookup"><span data-stu-id="ece56-222">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="ece56-223">Výchozí chování je minimální verze (včetně shody).</span><span class="sxs-lookup"><span data-stu-id="ece56-223">The default behavior is a minimum version, inclusive match.</span></span> <span data-ttu-id="ece56-224">Zadání `Version="1.2.3"` je například ekvivalentní zápisu NuGet `[1.2.3, )` a znamená, že vyřešený balíček bude mít verzi 1.2.3, je-li k dispozici nebo více než jinak.</span><span class="sxs-lookup"><span data-stu-id="ece56-224">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3, )` and means the resolved package will have the version 1.2.3 if available or greater otherwise.</span></span>

### <a name="runtimeidentifiers"></a><span data-ttu-id="ece56-225">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="ece56-225">RuntimeIdentifiers</span></span>

<span data-ttu-id="ece56-226">`<RuntimeIdentifiers>`Element Property umožňuje určit seznam [identifikátorů modulu runtime (identifikátorů RID)](../rid-catalog.md) , které jsou v projektu odděleny středníkem.</span><span class="sxs-lookup"><span data-stu-id="ece56-226">The `<RuntimeIdentifiers>` property element lets you specify a semicolon-delimited list of [Runtime Identifiers (RIDs)](../rid-catalog.md) for the project.</span></span>
<span data-ttu-id="ece56-227">Identifikátorů RID umožňuje publikování samostatně obsažených nasazení.</span><span class="sxs-lookup"><span data-stu-id="ece56-227">RIDs enable publishing self-contained deployments.</span></span>

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a><span data-ttu-id="ece56-228">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="ece56-228">RuntimeIdentifier</span></span>

<span data-ttu-id="ece56-229">`<RuntimeIdentifier>`Element Property umožňuje zadat pouze jeden [identifikátor modulu runtime (RID)](../rid-catalog.md) pro projekt.</span><span class="sxs-lookup"><span data-stu-id="ece56-229">The `<RuntimeIdentifier>` property element allows you to specify only one [Runtime Identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="ece56-230">Identifikátor RID umožňuje publikování samostatně zahrnutého nasazení.</span><span class="sxs-lookup"><span data-stu-id="ece56-230">The RID enables publishing a self-contained deployment.</span></span>

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

<span data-ttu-id="ece56-231">Použijte `<RuntimeIdentifiers>` (plural) místo toho, pokud potřebujete publikovat pro více modulů runtime.</span><span class="sxs-lookup"><span data-stu-id="ece56-231">Use `<RuntimeIdentifiers>` (plural) instead if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="ece56-232">`<RuntimeIdentifier>` může poskytovat rychlejší sestavení, je-li vyžadován pouze jeden modul runtime.</span><span class="sxs-lookup"><span data-stu-id="ece56-232">`<RuntimeIdentifier>` can provide faster builds when only a single runtime is required.</span></span>

### <a name="packagetargetfallback"></a><span data-ttu-id="ece56-233">PackageTargetFallback</span><span class="sxs-lookup"><span data-stu-id="ece56-233">PackageTargetFallback</span></span>

<span data-ttu-id="ece56-234">`<PackageTargetFallback>`Element Property umožňuje zadat sadu kompatibilních cílů, které se mají použít při obnovování balíčků.</span><span class="sxs-lookup"><span data-stu-id="ece56-234">The `<PackageTargetFallback>` property element allows you to specify a set of compatible targets to be used when restoring packages.</span></span> <span data-ttu-id="ece56-235">Je navržena tak, aby povolovala balíčky, které používají dotnet [TxM (Target x moniker)](/nuget/schema/target-frameworks) pro práci s balíčky, které nedeklarují dotnet TxM.</span><span class="sxs-lookup"><span data-stu-id="ece56-235">It's designed to allow packages that use the dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) to operate with packages that don't declare a dotnet TxM.</span></span> <span data-ttu-id="ece56-236">Pokud váš projekt používá TxM dotnet, pak všechny balíčky, na kterých závisí, musí mít také hodnotu dotnet TxM, pokud do projektu nepřidáte, aby bylo možné, aby platformy, které `<PackageTargetFallback>` nejsou dotnet, byly kompatibilní s dotnet.</span><span class="sxs-lookup"><span data-stu-id="ece56-236">If your project uses the dotnet TxM, then all the packages it depends on must also have a dotnet TxM, unless you add the `<PackageTargetFallback>` to your project in order to allow non-dotnet platforms to be compatible with dotnet.</span></span>

<span data-ttu-id="ece56-237">Následující příklad poskytuje záložní hodnoty pro všechny cíle v projektu:</span><span class="sxs-lookup"><span data-stu-id="ece56-237">The following example provides the fallbacks for all targets in your project:</span></span>

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

<span data-ttu-id="ece56-238">Následující příklad určuje pouze zálohy pro `netcoreapp3.1` cíl:</span><span class="sxs-lookup"><span data-stu-id="ece56-238">The following example specifies the fallbacks only for the `netcoreapp3.1` target:</span></span>

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp3.1'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="build-events"></a><span data-ttu-id="ece56-239">Události sestavení</span><span class="sxs-lookup"><span data-stu-id="ece56-239">Build events</span></span>

<span data-ttu-id="ece56-240">Způsob, jakým se změnily události před sestavením a po sestavení, jsou uvedeny v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="ece56-240">The way that pre-build and post-build events are specified in the project file has changed.</span></span> <span data-ttu-id="ece56-241">Vlastnosti PreBuildEvent a PostBuildEvent nejsou doporučovány ve formátu projektu ve stylu sady SDK, protože makra jako $ (ProjectDir) nejsou vyřešena.</span><span class="sxs-lookup"><span data-stu-id="ece56-241">The properties PreBuildEvent and PostBuildEvent are not recommended in the SDK-style project format, because macros such as $(ProjectDir) are not resolved.</span></span> <span data-ttu-id="ece56-242">Například následující kód již není podporován:</span><span class="sxs-lookup"><span data-stu-id="ece56-242">For example, the following code is no longer supported:</span></span>

```xml
<PropertyGroup>
    <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)"</PreBuildEvent>
</PropertyGroup>
```

<span data-ttu-id="ece56-243">V projektech se stylem sady SDK použijte cíl MSBuild s názvem `PreBuild` nebo `PostBuild` a nastavte `BeforeTargets` vlastnost pro `PreBuild` nebo `AfterTargets` vlastnost pro `PostBuild` .</span><span class="sxs-lookup"><span data-stu-id="ece56-243">In SDK-style projects, use an MSBuild target named `PreBuild` or `PostBuild` and set the `BeforeTargets` property for `PreBuild` or the `AfterTargets` property for `PostBuild`.</span></span> <span data-ttu-id="ece56-244">Pro předchozí příklad použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="ece56-244">For the preceding example, use the following code:</span></span>

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>

<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
><span data-ttu-id="ece56-245">Můžete použít libovolný název cílů MSBuild, ale rozhraní IDE sady Visual Studio rozpoznává `PreBuild` a `PostBuild` cílí, takže doporučujeme použít tyto názvy, abyste mohli upravovat příkazy v integrovaném vývojovém prostředí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ece56-245">You can use any name for the MSBuild targets, but the Visual Studio IDE recognizes `PreBuild` and `PostBuild` targets, so we recommend using those names so that you can edit the commands in the Visual Studio IDE.</span></span>

## <a name="nuget-metadata-properties"></a><span data-ttu-id="ece56-246">Vlastnosti metadat NuGet</span><span class="sxs-lookup"><span data-stu-id="ece56-246">NuGet metadata properties</span></span>

<span data-ttu-id="ece56-247">Při přechodu na MSBuild jsme přesunuli vstupní metadata, která se používají při balení balíčku NuGet z *project.js* do souborů *. csproj* .</span><span class="sxs-lookup"><span data-stu-id="ece56-247">With the move to MSBuild, we have moved the input metadata that is used when packing a NuGet package from *project.json* to *.csproj* files.</span></span> <span data-ttu-id="ece56-248">Vstupy jsou vlastnosti nástroje MSBuild, takže musí jít v rámci `<PropertyGroup>` skupiny.</span><span class="sxs-lookup"><span data-stu-id="ece56-248">The inputs are MSBuild properties so they have to go within a `<PropertyGroup>` group.</span></span> <span data-ttu-id="ece56-249">Následuje seznam vlastností, které se používají jako vstupy do procesu balení při použití `dotnet pack` příkazu nebo `Pack` cíle MSBuild, který je součástí sady SDK:</span><span class="sxs-lookup"><span data-stu-id="ece56-249">The following is the list of properties that are used as inputs to the packing process when using the `dotnet pack` command or the `Pack` MSBuild target that is part of the SDK:</span></span>

### <a name="ispackable"></a><span data-ttu-id="ece56-250">Ispackable nastavenou</span><span class="sxs-lookup"><span data-stu-id="ece56-250">IsPackable</span></span>

<span data-ttu-id="ece56-251">Logická hodnota, která určuje, zda lze projekt zabalit.</span><span class="sxs-lookup"><span data-stu-id="ece56-251">A Boolean value that specifies whether the project can be packed.</span></span> <span data-ttu-id="ece56-252">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="ece56-252">The default value is `true`.</span></span>

### <a name="packageversion"></a><span data-ttu-id="ece56-253">PackageVersion</span><span class="sxs-lookup"><span data-stu-id="ece56-253">PackageVersion</span></span>

<span data-ttu-id="ece56-254">Určuje verzi, kterou výsledný balíček bude mít.</span><span class="sxs-lookup"><span data-stu-id="ece56-254">Specifies the version that the resulting package will have.</span></span> <span data-ttu-id="ece56-255">Akceptuje všechny formy řetězce verze NuGet.</span><span class="sxs-lookup"><span data-stu-id="ece56-255">Accepts all forms of NuGet version string.</span></span> <span data-ttu-id="ece56-256">Výchozí hodnota je hodnota `$(Version)` , to znamená vlastnost `Version` v projektu.</span><span class="sxs-lookup"><span data-stu-id="ece56-256">Default is the value of `$(Version)`, that is, of the property `Version` in the project.</span></span>

### <a name="packageid"></a><span data-ttu-id="ece56-257">PackageId</span><span class="sxs-lookup"><span data-stu-id="ece56-257">PackageId</span></span>

<span data-ttu-id="ece56-258">Určuje název výsledného balíčku.</span><span class="sxs-lookup"><span data-stu-id="ece56-258">Specifies the name for the resulting package.</span></span> <span data-ttu-id="ece56-259">Pokud tento parametr nezadáte, použije se ve `pack` výchozím nastavení `AssemblyName` jako název balíčku název adresáře nebo.</span><span class="sxs-lookup"><span data-stu-id="ece56-259">If not specified, the `pack` operation will default to using the `AssemblyName` or directory name as the name of the package.</span></span>

### <a name="title"></a><span data-ttu-id="ece56-260">Nadpis</span><span class="sxs-lookup"><span data-stu-id="ece56-260">Title</span></span>

<span data-ttu-id="ece56-261">Popisný název balíčku, který se obvykle používá v uživatelském rozhraní, se zobrazuje jako v nuget.org a správce balíčků v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ece56-261">A human-friendly title of the package, typically used in UI displays as on nuget.org and the Package Manager in Visual Studio.</span></span> <span data-ttu-id="ece56-262">Pokud není zadaný, použije se místo toho ID balíčku.</span><span class="sxs-lookup"><span data-stu-id="ece56-262">If not specified, the package ID is used instead.</span></span>

### <a name="authors"></a><span data-ttu-id="ece56-263">Autoři</span><span class="sxs-lookup"><span data-stu-id="ece56-263">Authors</span></span>

<span data-ttu-id="ece56-264">Středníkem oddělený seznam autorů balíčků, které odpovídají názvům profilů v nuget.org. Ty se zobrazí v galerii NuGet na nuget.org a používají se pro balíčky křížového odkazu stejnými autory.</span><span class="sxs-lookup"><span data-stu-id="ece56-264">A semicolon-separated list of packages authors, matching the profile names on nuget.org. These are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span>

### <a name="packagedescription"></a><span data-ttu-id="ece56-265">PackageDescription</span><span class="sxs-lookup"><span data-stu-id="ece56-265">PackageDescription</span></span>

<span data-ttu-id="ece56-266">Dlouhý popis balíčku pro zobrazení uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ece56-266">A long description of the package for UI display.</span></span>

### <a name="description"></a><span data-ttu-id="ece56-267">Popis</span><span class="sxs-lookup"><span data-stu-id="ece56-267">Description</span></span>

<span data-ttu-id="ece56-268">Dlouhý popis pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="ece56-268">A long description for the assembly.</span></span> <span data-ttu-id="ece56-269">Pokud `PackageDescription` parametr není zadán, tato vlastnost se používá také jako Popis balíčku.</span><span class="sxs-lookup"><span data-stu-id="ece56-269">If `PackageDescription` is not specified, then this property is also used as the description of the package.</span></span>

### <a name="copyright"></a><span data-ttu-id="ece56-270">Copyright</span><span class="sxs-lookup"><span data-stu-id="ece56-270">Copyright</span></span>

<span data-ttu-id="ece56-271">Podrobnosti o autorských právech pro balíček.</span><span class="sxs-lookup"><span data-stu-id="ece56-271">Copyright details for the package.</span></span>

### <a name="packagerequirelicenseacceptance"></a><span data-ttu-id="ece56-272">PackageRequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="ece56-272">PackageRequireLicenseAcceptance</span></span>

<span data-ttu-id="ece56-273">Logická hodnota, která určuje, zda klient musí požádat spotřebitele o přijetí licence k balíčku před instalací balíčku.</span><span class="sxs-lookup"><span data-stu-id="ece56-273">A Boolean value that specifies whether the client must prompt the consumer to accept the package license before installing the package.</span></span> <span data-ttu-id="ece56-274">Výchozí formát je `false`.</span><span class="sxs-lookup"><span data-stu-id="ece56-274">The default is `false`.</span></span>

### <a name="developmentdependency"></a><span data-ttu-id="ece56-275">DevelopmentDependency</span><span class="sxs-lookup"><span data-stu-id="ece56-275">DevelopmentDependency</span></span>

<span data-ttu-id="ece56-276">Logická hodnota, která určuje, zda je balíček označen jako jen pro vývoj, což zabrání zahrnutí balíčku jako závislosti v jiných balíčcích.</span><span class="sxs-lookup"><span data-stu-id="ece56-276">A Boolean value that specifies whether the package is marked as a development-only dependency, which prevents the package from being included as a dependency in other packages.</span></span> <span data-ttu-id="ece56-277">Pomocí PackageReference (NuGet 4,8 +) Tento příznak také znamená, že prostředky při kompilaci jsou vyloučeny z kompilace.</span><span class="sxs-lookup"><span data-stu-id="ece56-277">With PackageReference (NuGet 4.8+), this flag also means that compile-time assets are excluded from compilation.</span></span> <span data-ttu-id="ece56-278">Další informace najdete v tématu [Podpora DevelopmentDependency pro PackageReference](https://github.com/NuGet/Home/wiki/DevelopmentDependency-support-for-PackageReference).</span><span class="sxs-lookup"><span data-stu-id="ece56-278">For more information, see [DevelopmentDependency support for PackageReference](https://github.com/NuGet/Home/wiki/DevelopmentDependency-support-for-PackageReference).</span></span>

### <a name="packagelicenseexpression"></a><span data-ttu-id="ece56-279">PackageLicenseExpression</span><span class="sxs-lookup"><span data-stu-id="ece56-279">PackageLicenseExpression</span></span>

<span data-ttu-id="ece56-280">Identifikátor nebo výraz [licence SPDX](https://spdx.org/licenses/)</span><span class="sxs-lookup"><span data-stu-id="ece56-280">An [SPDX license identifier](https://spdx.org/licenses/) or expression.</span></span> <span data-ttu-id="ece56-281">Například, `Apache-2.0`.</span><span class="sxs-lookup"><span data-stu-id="ece56-281">For example, `Apache-2.0`.</span></span>

<span data-ttu-id="ece56-282">Tady je úplný seznam [identifikátorů licencí SPDX](https://spdx.org/licenses/).</span><span class="sxs-lookup"><span data-stu-id="ece56-282">Here is the complete list of [SPDX license identifiers](https://spdx.org/licenses/).</span></span> <span data-ttu-id="ece56-283">NuGet.org přijímá při použití výrazu typu licence pouze licence OSI nebo FSF schválené.</span><span class="sxs-lookup"><span data-stu-id="ece56-283">NuGet.org accepts only OSI or FSF approved licenses when using license type expression.</span></span>

<span data-ttu-id="ece56-284">Přesná Syntaxe výrazů s licencí je popsána níže v tématu [ABNF](https://tools.ietf.org/html/rfc5234).</span><span class="sxs-lookup"><span data-stu-id="ece56-284">The exact syntax of the license expressions is described below in [ABNF](https://tools.ietf.org/html/rfc5234).</span></span>

```abnf
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
> <span data-ttu-id="ece56-285">`PackageLicenseExpression` `PackageLicenseFile` `PackageLicenseUrl` V jednom okamžiku může být určena pouze jedna z a.</span><span class="sxs-lookup"><span data-stu-id="ece56-285">Only one of `PackageLicenseExpression`, `PackageLicenseFile` and `PackageLicenseUrl` can be specified at a time.</span></span>

### <a name="packagelicensefile"></a><span data-ttu-id="ece56-286">PackageLicenseFile</span><span class="sxs-lookup"><span data-stu-id="ece56-286">PackageLicenseFile</span></span>

<span data-ttu-id="ece56-287">Cesta k souboru s licencí v rámci balíčku Pokud používáte licenci, ke které se nepřiřadil identifikátor SPDX, nebo se jedná o vlastní licenci (jinak `PackageLicenseExpression` se upřednostňuje)</span><span class="sxs-lookup"><span data-stu-id="ece56-287">Path to a license file within the package if you are using a license that hasn’t been assigned an SPDX identifier, or it is a custom license (Otherwise `PackageLicenseExpression` is preferred)</span></span>

<span data-ttu-id="ece56-288">Nahrazuje `PackageLicenseUrl` , nejde kombinovat s a `PackageLicenseExpression` vyžaduje Visual Studio verze 15.9.4 a .NET SDK 2.1.502 nebo 2.2.101 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="ece56-288">Replaces `PackageLicenseUrl`, can't be combined with `PackageLicenseExpression`, and requires Visual Studio version 15.9.4 and .NET SDK 2.1.502 or 2.2.101 or newer.</span></span>

<span data-ttu-id="ece56-289">Je potřeba zajistit, aby byl soubor s licencí zabalený tak, že ho do projektu přidáte explicitně, jako příklad použití:</span><span class="sxs-lookup"><span data-stu-id="ece56-289">You will need to ensure the license file is packed by adding it explicitly to the project, example usage:</span></span>

```xml
<PropertyGroup>
  <PackageLicenseFile>LICENSE.txt</PackageLicenseFile>
</PropertyGroup>
<ItemGroup>
  <None Include="licenses\LICENSE.txt" Pack="true" PackagePath="$(PackageLicenseFile)"/>
</ItemGroup>
```

### <a name="packagelicenseurl"></a><span data-ttu-id="ece56-290">PackageLicenseUrl</span><span class="sxs-lookup"><span data-stu-id="ece56-290">PackageLicenseUrl</span></span>

<span data-ttu-id="ece56-291">Adresa URL licence, která se vztahuje na balíček.</span><span class="sxs-lookup"><span data-stu-id="ece56-291">A URL to the license that is applicable to the package.</span></span> <span data-ttu-id="ece56-292">(_nepoužívá se od verze Visual Studio 15.9.4, .NET SDK 2.1.502 a 2.2.101_)</span><span class="sxs-lookup"><span data-stu-id="ece56-292">(_deprecated since Visual Studio 15.9.4, .NET SDK 2.1.502 and 2.2.101_)</span></span>

### <a name="packageicon"></a><span data-ttu-id="ece56-293">PackageIcon</span><span class="sxs-lookup"><span data-stu-id="ece56-293">PackageIcon</span></span>

<span data-ttu-id="ece56-294">Cesta k obrázku v balíčku, který se má použít jako ikona balíčku</span><span class="sxs-lookup"><span data-stu-id="ece56-294">A path to an image in the package to use as a package icon.</span></span> <span data-ttu-id="ece56-295">Přečtěte si další informace o [ `icon` metadatech](/nuget/reference/nuspec#icon).</span><span class="sxs-lookup"><span data-stu-id="ece56-295">Read more about [`icon` metadata](/nuget/reference/nuspec#icon).</span></span> <span data-ttu-id="ece56-296">[PackageIconUrl je zastaralé](/nuget/reference/msbuild-targets#packageiconurl) namísto PackageIcon.</span><span class="sxs-lookup"><span data-stu-id="ece56-296">[PackageIconUrl is deprecated](/nuget/reference/msbuild-targets#packageiconurl) in favor of PackageIcon.</span></span>

### <a name="packagereleasenotes"></a><span data-ttu-id="ece56-297">PackageReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="ece56-297">PackageReleaseNotes</span></span>

<span data-ttu-id="ece56-298">Poznámky k verzi balíčku</span><span class="sxs-lookup"><span data-stu-id="ece56-298">Release notes for the package.</span></span>

### <a name="packagetags"></a><span data-ttu-id="ece56-299">PackageTags</span><span class="sxs-lookup"><span data-stu-id="ece56-299">PackageTags</span></span>

<span data-ttu-id="ece56-300">Seznam značek oddělených středníkem, který určuje balíček.</span><span class="sxs-lookup"><span data-stu-id="ece56-300">A semicolon-delimited list of tags that designates the package.</span></span>

### <a name="packageoutputpath"></a><span data-ttu-id="ece56-301">PackageOutputPath</span><span class="sxs-lookup"><span data-stu-id="ece56-301">PackageOutputPath</span></span>

<span data-ttu-id="ece56-302">Určuje výstupní cestu, do které bude zahozen zabalený balíček.</span><span class="sxs-lookup"><span data-stu-id="ece56-302">Determines the output path in which the packed package will be dropped.</span></span> <span data-ttu-id="ece56-303">Výchozí je `$(OutputPath)`.</span><span class="sxs-lookup"><span data-stu-id="ece56-303">Default is `$(OutputPath)`.</span></span>

### <a name="includesymbols"></a><span data-ttu-id="ece56-304">IncludeSymbols</span><span class="sxs-lookup"><span data-stu-id="ece56-304">IncludeSymbols</span></span>
<span data-ttu-id="ece56-305">Tato logická hodnota označuje, zda má balíček při zabalení projektu vytvořit další balíček symbolů.</span><span class="sxs-lookup"><span data-stu-id="ece56-305">This Boolean value indicates whether the package should create an additional symbols package when the project is packed.</span></span> <span data-ttu-id="ece56-306">Formát balíčku symbolů je řízen `SymbolPackageFormat` vlastností.</span><span class="sxs-lookup"><span data-stu-id="ece56-306">The symbols package's format is controlled by the `SymbolPackageFormat` property.</span></span>

### <a name="symbolpackageformat"></a><span data-ttu-id="ece56-307">SymbolPackageFormat</span><span class="sxs-lookup"><span data-stu-id="ece56-307">SymbolPackageFormat</span></span>
<span data-ttu-id="ece56-308">Určuje formát balíčku symbolů.</span><span class="sxs-lookup"><span data-stu-id="ece56-308">Specifies the format of the symbols package.</span></span> <span data-ttu-id="ece56-309">Pokud "Symbols. nupkg", bude balíček starších symbolů vytvořen s příponou *. Symbols. nupkg* , která obsahuje soubory PDB, knihovny DLL a další výstupní soubory.</span><span class="sxs-lookup"><span data-stu-id="ece56-309">If "symbols.nupkg", a legacy symbols package will be created with a *.symbols.nupkg* extension containing PDBs, DLLs, and other output files.</span></span> <span data-ttu-id="ece56-310">Pokud bude "snupkg", vytvoří se balíček symbolů snupkg obsahující přenosné soubory PDB.</span><span class="sxs-lookup"><span data-stu-id="ece56-310">If "snupkg", a snupkg symbol package will be created containing the portable PDBs.</span></span> <span data-ttu-id="ece56-311">Výchozí hodnota je "Symbols. nupkg".</span><span class="sxs-lookup"><span data-stu-id="ece56-311">Default is "symbols.nupkg".</span></span>

### <a name="includesource"></a><span data-ttu-id="ece56-312">IncludeSource</span><span class="sxs-lookup"><span data-stu-id="ece56-312">IncludeSource</span></span>

<span data-ttu-id="ece56-313">Tato logická hodnota označuje, zda by měl proces balíčku vytvořit zdrojový balíček.</span><span class="sxs-lookup"><span data-stu-id="ece56-313">This Boolean value indicates whether the pack process should create a source package.</span></span> <span data-ttu-id="ece56-314">Zdrojový balíček obsahuje zdrojový kód knihovny i soubory PDB.</span><span class="sxs-lookup"><span data-stu-id="ece56-314">The source package contains the library's source code as well as PDB files.</span></span> <span data-ttu-id="ece56-315">Zdrojové soubory jsou umístěny do `src/ProjectName` adresáře ve výsledném souboru balíčku.</span><span class="sxs-lookup"><span data-stu-id="ece56-315">Source files are put under the `src/ProjectName` directory in the resulting package file.</span></span>

### <a name="istool"></a><span data-ttu-id="ece56-316">Nástroj</span><span class="sxs-lookup"><span data-stu-id="ece56-316">IsTool</span></span>

<span data-ttu-id="ece56-317">Určuje, zda jsou všechny výstupní soubory zkopírovány do složky *Tools* namísto složky *lib* .</span><span class="sxs-lookup"><span data-stu-id="ece56-317">Specifies whether all output files are copied to the *tools* folder instead of the *lib* folder.</span></span> <span data-ttu-id="ece56-318">To se liší od a `DotNetCliTool` , která je určena nastavením `PackageType` v souboru *. csproj* .</span><span class="sxs-lookup"><span data-stu-id="ece56-318">This is different from a `DotNetCliTool`, which is specified by setting the `PackageType` in the *.csproj* file.</span></span>

### <a name="repositoryurl"></a><span data-ttu-id="ece56-319">RepositoryUrl</span><span class="sxs-lookup"><span data-stu-id="ece56-319">RepositoryUrl</span></span>

<span data-ttu-id="ece56-320">Určuje adresu URL úložiště, ve kterém se nachází zdrojový kód balíčku, nebo ze kterého se vytváří.</span><span class="sxs-lookup"><span data-stu-id="ece56-320">Specifies the URL for the repository where the source code for the package resides and/or from which it's being built.</span></span>

### <a name="repositorytype"></a><span data-ttu-id="ece56-321">RepositoryType</span><span class="sxs-lookup"><span data-stu-id="ece56-321">RepositoryType</span></span>

<span data-ttu-id="ece56-322">Určuje typ úložiště.</span><span class="sxs-lookup"><span data-stu-id="ece56-322">Specifies the type of the repository.</span></span> <span data-ttu-id="ece56-323">Výchozí hodnota je "git".</span><span class="sxs-lookup"><span data-stu-id="ece56-323">Default is "git".</span></span>

### <a name="repositorybranch"></a><span data-ttu-id="ece56-324">RepositoryBranch</span><span class="sxs-lookup"><span data-stu-id="ece56-324">RepositoryBranch</span></span>
<span data-ttu-id="ece56-325">Určuje název zdrojové větve v úložišti.</span><span class="sxs-lookup"><span data-stu-id="ece56-325">Specifies the name of the source branch in the repository.</span></span> <span data-ttu-id="ece56-326">Když je projekt zabalen do balíčku NuGet, přidá se do metadat balíčku.</span><span class="sxs-lookup"><span data-stu-id="ece56-326">When the project is packaged in a NuGet package, it's added to the package metadata.</span></span>

### <a name="repositorycommit"></a><span data-ttu-id="ece56-327">RepositoryCommit</span><span class="sxs-lookup"><span data-stu-id="ece56-327">RepositoryCommit</span></span>
<span data-ttu-id="ece56-328">Volitelné potvrzení změn úložiště nebo sada změn, které označují, na který zdroj byl balíček vytvořen.</span><span class="sxs-lookup"><span data-stu-id="ece56-328">Optional repository commit or changeset to indicate which source the package was built against.</span></span> <span data-ttu-id="ece56-329">`RepositoryUrl` musí být také zadáno pro zahrnutí této vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ece56-329">`RepositoryUrl` must also be specified for this property to be included.</span></span> <span data-ttu-id="ece56-330">Když je projekt zabalen v balíčku NuGet, toto potvrzení nebo sada změn se přidá do metadat balíčku.</span><span class="sxs-lookup"><span data-stu-id="ece56-330">When the project is packaged in a NuGet package, this commit or changeset is added to the package metadata.</span></span>

### <a name="nopackageanalysis"></a><span data-ttu-id="ece56-331">NoPackageAnalysis</span><span class="sxs-lookup"><span data-stu-id="ece56-331">NoPackageAnalysis</span></span>

<span data-ttu-id="ece56-332">Určuje, že sada by neměla po sestavení balíčku spustit analýzu balíčku.</span><span class="sxs-lookup"><span data-stu-id="ece56-332">Specifies that pack should not run package analysis after building the package.</span></span>

### <a name="minclientversion"></a><span data-ttu-id="ece56-333">MinClientVersion</span><span class="sxs-lookup"><span data-stu-id="ece56-333">MinClientVersion</span></span>

<span data-ttu-id="ece56-334">Určuje minimální verzi klienta NuGet, která může nainstalovat tento balíček vynutila nuget.exe a správcem balíčků sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ece56-334">Specifies the minimum version of the NuGet client that can install this package, enforced by nuget.exe and the Visual Studio Package Manager.</span></span>

### <a name="includebuildoutput"></a><span data-ttu-id="ece56-335">IncludeBuildOutput</span><span class="sxs-lookup"><span data-stu-id="ece56-335">IncludeBuildOutput</span></span>

<span data-ttu-id="ece56-336">Tato logická hodnota určuje, zda mají být výstupní sestavení sestavení zabalena do souboru *. nupkg* nebo ne.</span><span class="sxs-lookup"><span data-stu-id="ece56-336">This Boolean value specifies whether the build output assemblies should be packed into the *.nupkg* file or not.</span></span>

### <a name="includecontentinpack"></a><span data-ttu-id="ece56-337">IncludeContentInPack</span><span class="sxs-lookup"><span data-stu-id="ece56-337">IncludeContentInPack</span></span>

<span data-ttu-id="ece56-338">Tato logická hodnota určuje, zda `Content` budou do výsledného balíčku automaticky zahrnuty všechny položky, které mají typ.</span><span class="sxs-lookup"><span data-stu-id="ece56-338">This Boolean value specifies whether any items that have a type of `Content` will be included in the resulting package automatically.</span></span> <span data-ttu-id="ece56-339">Výchozí formát je `true`.</span><span class="sxs-lookup"><span data-stu-id="ece56-339">The default is `true`.</span></span>

### <a name="buildoutputtargetfolder"></a><span data-ttu-id="ece56-340">BuildOutputTargetFolder</span><span class="sxs-lookup"><span data-stu-id="ece56-340">BuildOutputTargetFolder</span></span>

<span data-ttu-id="ece56-341">Určuje složku, kam se mají umístit výstupní sestavení.</span><span class="sxs-lookup"><span data-stu-id="ece56-341">Specifies the folder where to place the output assemblies.</span></span> <span data-ttu-id="ece56-342">Výstupní sestavení (a další výstupní soubory) se zkopírují do příslušných složek rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ece56-342">The output assemblies (and other output files) are copied into their respective framework folders.</span></span>

### <a name="contenttargetfolders"></a><span data-ttu-id="ece56-343">ContentTargetFolders</span><span class="sxs-lookup"><span data-stu-id="ece56-343">ContentTargetFolders</span></span>

<span data-ttu-id="ece56-344">Tato vlastnost určuje výchozí umístění, kde mají všechny soubory obsahu jít, pokud `PackagePath` nejsou pro ně zadány.</span><span class="sxs-lookup"><span data-stu-id="ece56-344">This property specifies the default location of where all the content files should go if `PackagePath` is not specified for them.</span></span> <span data-ttu-id="ece56-345">Výchozí hodnota je Content; contentFiles.</span><span class="sxs-lookup"><span data-stu-id="ece56-345">The default value is "content;contentFiles".</span></span>

### <a name="nuspecfile"></a><span data-ttu-id="ece56-346">NuspecFile</span><span class="sxs-lookup"><span data-stu-id="ece56-346">NuspecFile</span></span>

<span data-ttu-id="ece56-347">Relativní nebo absolutní cesta k souboru *. nuspec* , který se používá pro balení.</span><span class="sxs-lookup"><span data-stu-id="ece56-347">Relative or absolute path to the *.nuspec* file being used for packing.</span></span>

> [!NOTE]
> <span data-ttu-id="ece56-348">Je-li zadán soubor *. nuspec* , používá se **výhradně** k balení informací a žádné informace v projektech se nepoužívají.</span><span class="sxs-lookup"><span data-stu-id="ece56-348">If the *.nuspec* file is specified, it's used **exclusively** for packaging information and any information in the projects is not used.</span></span>

### <a name="nuspecbasepath"></a><span data-ttu-id="ece56-349">NuspecBasePath</span><span class="sxs-lookup"><span data-stu-id="ece56-349">NuspecBasePath</span></span>

<span data-ttu-id="ece56-350">Základní cesta pro soubor *. nuspec*</span><span class="sxs-lookup"><span data-stu-id="ece56-350">Base path for the *.nuspec* file.</span></span>

### <a name="nuspecproperties"></a><span data-ttu-id="ece56-351">NuspecProperties</span><span class="sxs-lookup"><span data-stu-id="ece56-351">NuspecProperties</span></span>

<span data-ttu-id="ece56-352">Seznam párů klíč = hodnota oddělený středníkem.</span><span class="sxs-lookup"><span data-stu-id="ece56-352">Semicolon separated list of key=value pairs.</span></span>

## <a name="assemblyinfo-properties"></a><span data-ttu-id="ece56-353">Vlastnosti AssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="ece56-353">AssemblyInfo properties</span></span>

<span data-ttu-id="ece56-354">[Atributy sestavení](../../standard/assembly/set-attributes.md) , které byly obvykle přítomny v souboru *AssemblyInfo* , se nyní automaticky generují z vlastností.</span><span class="sxs-lookup"><span data-stu-id="ece56-354">[Assembly attributes](../../standard/assembly/set-attributes.md) that were typically present in an *AssemblyInfo* file are now automatically generated from properties.</span></span>

### <a name="properties-per-attribute"></a><span data-ttu-id="ece56-355">Vlastnosti na atribut</span><span class="sxs-lookup"><span data-stu-id="ece56-355">Properties per attribute</span></span>

<span data-ttu-id="ece56-356">Jak je znázorněno v následující tabulce, každý atribut má vlastnost, která řídí svůj obsah a druhý, který zakazuje jeho generaci:</span><span class="sxs-lookup"><span data-stu-id="ece56-356">As shown in the following table, each attribute has a property that controls its content and another that disables its generation:</span></span>

| <span data-ttu-id="ece56-357">Atribut</span><span class="sxs-lookup"><span data-stu-id="ece56-357">Attribute</span></span>                                                      | <span data-ttu-id="ece56-358">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="ece56-358">Property</span></span>               | <span data-ttu-id="ece56-359">Vlastnost, která se má zakázat</span><span class="sxs-lookup"><span data-stu-id="ece56-359">Property to disable</span></span>                             |
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

<span data-ttu-id="ece56-360">Poznámky:</span><span class="sxs-lookup"><span data-stu-id="ece56-360">Notes:</span></span>

- <span data-ttu-id="ece56-361">`AssemblyVersion``FileVersion`ve výchozím nastavení je to, že se má přebírat hodnota `$(Version)` bez přípony.</span><span class="sxs-lookup"><span data-stu-id="ece56-361">`AssemblyVersion` and `FileVersion` default is to take the value of `$(Version)` without suffix.</span></span> <span data-ttu-id="ece56-362">Například pokud `$(Version)` je `1.2.3-beta.4` , pak hodnota by byla `1.2.3` .</span><span class="sxs-lookup"><span data-stu-id="ece56-362">For example, if `$(Version)` is `1.2.3-beta.4`, then the value would be `1.2.3`.</span></span>
- <span data-ttu-id="ece56-363">`InformationalVersion` Výchozí hodnota je `$(Version)` .</span><span class="sxs-lookup"><span data-stu-id="ece56-363">`InformationalVersion` defaults to the value of `$(Version)`.</span></span>
- <span data-ttu-id="ece56-364">`InformationalVersion` má `$(SourceRevisionId)` připojení, pokud je vlastnost přítomna.</span><span class="sxs-lookup"><span data-stu-id="ece56-364">`InformationalVersion` has `$(SourceRevisionId)` appended if the property is present.</span></span> <span data-ttu-id="ece56-365">Dá se zakázat pomocí `IncludeSourceRevisionInInformationalVersion` .</span><span class="sxs-lookup"><span data-stu-id="ece56-365">It can be disabled using `IncludeSourceRevisionInInformationalVersion`.</span></span>
- <span data-ttu-id="ece56-366">`Copyright` a `Description` vlastnosti se také používají pro metadata NuGet.</span><span class="sxs-lookup"><span data-stu-id="ece56-366">`Copyright` and `Description` properties are also used for NuGet metadata.</span></span>
- <span data-ttu-id="ece56-367">`Configuration` je sdílen se všemi procesy sestavení a nastavena prostřednictvím `--configuration` parametru `dotnet` příkazů.</span><span class="sxs-lookup"><span data-stu-id="ece56-367">`Configuration` is shared with all the build process and set via the `--configuration` parameter of `dotnet` commands.</span></span>

### <a name="generateassemblyinfo"></a><span data-ttu-id="ece56-368">GenerateAssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="ece56-368">GenerateAssemblyInfo</span></span>

<span data-ttu-id="ece56-369">Logická hodnota, která povolí nebo zakáže všechny generace AssemblyInfo.</span><span class="sxs-lookup"><span data-stu-id="ece56-369">A Boolean that enable or disable all the AssemblyInfo generation.</span></span> <span data-ttu-id="ece56-370">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="ece56-370">The default value is `true`.</span></span>

### <a name="generatedassemblyinfofile"></a><span data-ttu-id="ece56-371">GeneratedAssemblyInfoFile</span><span class="sxs-lookup"><span data-stu-id="ece56-371">GeneratedAssemblyInfoFile</span></span>

<span data-ttu-id="ece56-372">Cesta k vygenerovanému souboru s informacemi o sestavení</span><span class="sxs-lookup"><span data-stu-id="ece56-372">The path of the generated assembly info file.</span></span> <span data-ttu-id="ece56-373">Ve výchozím nastavení se jedná o soubor v `$(IntermediateOutputPath)` adresáři (obj).</span><span class="sxs-lookup"><span data-stu-id="ece56-373">Default to a file in the `$(IntermediateOutputPath)` (obj) directory.</span></span>
