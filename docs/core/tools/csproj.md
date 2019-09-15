---
title: Přidání do formátu csproj pro .NET Core
description: Přečtěte si o rozdílech mezi existujícími a soubory .NET Core csproj.
ms.date: 04/08/2019
ms.openlocfilehash: 13239b5235138cc6994841bbb81f8f12e661e337
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969844"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a><span data-ttu-id="d2924-103">Přidání do formátu csproj pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="d2924-103">Additions to the csproj format for .NET Core</span></span>

<span data-ttu-id="d2924-104">Tento dokument popisuje změny, které byly přidány do souborů projektu jako součást přesunutí z *Project. JSON* na *csproj* a [MSBuild](https://github.com/Microsoft/MSBuild).</span><span class="sxs-lookup"><span data-stu-id="d2924-104">This document outlines the changes that were added to the project files as part of the move from *project.json* to *csproj* and [MSBuild](https://github.com/Microsoft/MSBuild).</span></span> <span data-ttu-id="d2924-105">Další informace o obecných syntaxech souborů projektu a referenčních informacích naleznete v dokumentaci k [souboru projektu MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) .</span><span class="sxs-lookup"><span data-stu-id="d2924-105">For more information about general project file syntax and reference, see [the MSBuild project file](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation.</span></span>

## <a name="implicit-package-references"></a><span data-ttu-id="d2924-106">Odkazy na implicitní balíčky</span><span class="sxs-lookup"><span data-stu-id="d2924-106">Implicit package references</span></span>

<span data-ttu-id="d2924-107">Na metabalíčky se implicitně odkazuje na základě cílových rozhraní, která jsou určená v `<TargetFramework>` vlastnosti nebo `<TargetFrameworks>` souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="d2924-107">Metapackages are implicitly referenced based on the target framework(s) specified in the `<TargetFramework>` or `<TargetFrameworks>` property of your project file.</span></span> <span data-ttu-id="d2924-108">`<TargetFrameworks>`se ignoruje `<TargetFramework>` , pokud je zadaný, nezávisle na pořadí.</span><span class="sxs-lookup"><span data-stu-id="d2924-108">`<TargetFrameworks>` is ignored if `<TargetFramework>` is specified, independent of order.</span></span> <span data-ttu-id="d2924-109">Další informace najdete v tématu [balíčky, metabalíčky a rozhraní](../packages.md).</span><span class="sxs-lookup"><span data-stu-id="d2924-109">For more information, see [Packages, metapackages and frameworks](../packages.md).</span></span> 

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

### <a name="recommendations"></a><span data-ttu-id="d2924-110">Doporučení</span><span class="sxs-lookup"><span data-stu-id="d2924-110">Recommendations</span></span>

<span data-ttu-id="d2924-111">Vzhledem `Microsoft.NETCore.App` k `NETStandard.Library` tomu, že jsou implicitně odkazovány na nebo metabalíčky, následující doporučené osvědčené postupy:</span><span class="sxs-lookup"><span data-stu-id="d2924-111">Since `Microsoft.NETCore.App` or `NETStandard.Library` metapackages are implicitly referenced, the following are our recommended best practices:</span></span>

* <span data-ttu-id="d2924-112">Pokud cílíte na rozhraní .NET Core nebo .NET Standard, nikdy nepoužívejte explicitní `Microsoft.NETCore.App` odkaz `NETStandard.Library` na nebo metabalíčky `<PackageReference>` prostřednictvím položky v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="d2924-112">When targeting .NET Core or .NET Standard, never have an explicit reference to the `Microsoft.NETCore.App` or `NETStandard.Library` metapackages via a `<PackageReference>` item in your project file.</span></span>
* <span data-ttu-id="d2924-113">Pokud potřebujete specifickou verzi modulu runtime při cílení na .NET Core, měli byste použít `<RuntimeFrameworkVersion>` vlastnost v projektu ( `1.0.4`například) namísto odkazování na Metapackage.</span><span class="sxs-lookup"><span data-stu-id="d2924-113">If you need a specific version of the runtime when targeting .NET Core, you should use the `<RuntimeFrameworkVersion>` property in your project (for example, `1.0.4`) instead of referencing the metapackage.</span></span>
  * <span data-ttu-id="d2924-114">K tomu může dojít, pokud používáte [samostatná nasazení](../deploying/index.md#self-contained-deployments-scd) a potřebujete konkrétní opravu verze 1.0.0 LTS runtime, například.</span><span class="sxs-lookup"><span data-stu-id="d2924-114">This might happen if you are using [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) and you need a specific patch version of 1.0.0 LTS runtime, for example.</span></span>
* <span data-ttu-id="d2924-115">Pokud potřebujete specifickou verzi `NETStandard.Library` Metapackage při cílení na .NET Standard, můžete `<NetStandardImplicitPackageVersion>` použít vlastnost a nastavit verzi, kterou potřebujete.</span><span class="sxs-lookup"><span data-stu-id="d2924-115">If you need a specific version of the `NETStandard.Library` metapackage when targeting .NET Standard, you can use the `<NetStandardImplicitPackageVersion>` property and set the version you need.</span></span>
* <span data-ttu-id="d2924-116">Neprovádějte explicitní přidávání nebo aktualizaci odkazů na `Microsoft.NETCore.App` Metapackage nebo `NETStandard.Library` v projektech .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d2924-116">Don't explicitly add or update references to either the `Microsoft.NETCore.App` or `NETStandard.Library` metapackage in .NET Framework projects.</span></span> <span data-ttu-id="d2924-117">Pokud `NETStandard.Library` je při použití balíčku NuGet založeného na .NET Standard potřebná nějaká verze, NuGet tuto verzi nainstaluje automaticky.</span><span class="sxs-lookup"><span data-stu-id="d2924-117">If any version of `NETStandard.Library` is needed when using a .NET Standard-based NuGet package, NuGet automatically installs that version.</span></span>

## <a name="implicit-version-for-some-package-references"></a><span data-ttu-id="d2924-118">Implicitní verze pro některé odkazy na balíčky</span><span class="sxs-lookup"><span data-stu-id="d2924-118">Implicit version for some package references</span></span>

<span data-ttu-id="d2924-119">Většina použití [`<PackageReference>`](#packagereference) `Version` parametru vyžaduje nastavení atributu k určení verze balíčku NuGet, která se má použít.</span><span class="sxs-lookup"><span data-stu-id="d2924-119">Most usages of [`<PackageReference>`](#packagereference) require setting the `Version` attribute to specify the NuGet package version to be used.</span></span> <span data-ttu-id="d2924-120">Při použití .NET Core 2,1 nebo 2,2 a odkazování na [Microsoft. AspNetCore. app](/aspnet/core/fundamentals/metapackage-app) nebo [Microsoft. AspNetCore. All](/aspnet/core/fundamentals/metapackage)ale atribut není zbytečný.</span><span class="sxs-lookup"><span data-stu-id="d2924-120">When using .NET Core 2.1 or 2.2 and referencing [Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) or [Microsoft.AspNetCore.All](/aspnet/core/fundamentals/metapackage), however, the  attribute is unnecessary.</span></span> <span data-ttu-id="d2924-121">.NET Core SDK může automaticky vybrat verzi těchto balíčků, které by se měly použít.</span><span class="sxs-lookup"><span data-stu-id="d2924-121">The .NET Core SDK can automatically select the version of these packages that should be used.</span></span>

### <a name="recommendation"></a><span data-ttu-id="d2924-122">Doporučení</span><span class="sxs-lookup"><span data-stu-id="d2924-122">Recommendation</span></span>

<span data-ttu-id="d2924-123">Při odkazování na `Microsoft.AspNetCore.App` balíčky `Microsoft.AspNetCore.All` nebo nezadávejte jejich verzi.</span><span class="sxs-lookup"><span data-stu-id="d2924-123">When referencing the `Microsoft.AspNetCore.App` or `Microsoft.AspNetCore.All` packages, do not specify their version.</span></span> <span data-ttu-id="d2924-124">Pokud je zadána verze, sada SDK může vytvořit upozornění NETSDK1071.</span><span class="sxs-lookup"><span data-stu-id="d2924-124">If a version is specified, the SDK may produce warning NETSDK1071.</span></span> <span data-ttu-id="d2924-125">Chcete-li toto upozornění vyřešit, odeberte verzi balíčku, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="d2924-125">To fix this warning, remove the package version like in the following example:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore.App" />
</ItemGroup>
```

> <span data-ttu-id="d2924-126">Známý problém: sada .NET Core 2,1 SDK podporuje pouze tuto syntaxi pouze v případě, že projekt používá také Microsoft. NET. SDK. Web.</span><span class="sxs-lookup"><span data-stu-id="d2924-126">Known issue: the .NET Core 2.1 SDK only supported this syntax when the project also uses Microsoft.NET.Sdk.Web.</span></span> <span data-ttu-id="d2924-127">To je vyřešeno v sadě .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="d2924-127">This is resolved in the .NET Core 2.2 SDK.</span></span>

<span data-ttu-id="d2924-128">Tyto odkazy na ASP.NET Core metabalíčky mají mírně odlišné chování z většiny běžných balíčků NuGet.</span><span class="sxs-lookup"><span data-stu-id="d2924-128">These references to ASP.NET Core metapackages have a slightly different behavior from most normal NuGet packages.</span></span> <span data-ttu-id="d2924-129">[Nasazení aplikací závislých na rozhraních](../deploying/index.md#framework-dependent-deployments-fdd) , která používají tyto metabalíčky, automaticky využívají ASP.NET Core sdílené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d2924-129">[Framework-dependent deployments](../deploying/index.md#framework-dependent-deployments-fdd) of applications that use these metapackages automatically take advantage of the ASP.NET Core shared framework.</span></span> <span data-ttu-id="d2924-130">Při použití metabalíčky se s aplikací nasadí **žádné** prostředky z odkazovaného ASP.NET Core balíčků NuGet – ASP.NET Core sdílené rozhraní obsahuje tyto prostředky.</span><span class="sxs-lookup"><span data-stu-id="d2924-130">When you use the metapackages, **no** assets from the referenced ASP.NET Core NuGet packages are deployed with the application—the ASP.NET Core shared framework contains these assets.</span></span> <span data-ttu-id="d2924-131">Prostředky ve sdíleném rozhraní jsou optimalizované pro cílovou platformu pro zlepšení času spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="d2924-131">The assets in the shared framework are optimized for the target platform to improve application startup time.</span></span> <span data-ttu-id="d2924-132">Další informace o sdílených rozhraních naleznete v tématu [distribuční balíček .NET Core](../build/distribution-packaging.md).</span><span class="sxs-lookup"><span data-stu-id="d2924-132">For more information about shared framework, see [.NET Core distribution packaging](../build/distribution-packaging.md).</span></span>

<span data-ttu-id="d2924-133">*Je* -li zadána verze, je zpracována jako *minimální* verze ASP.NET Core sdílené architektury pro nasazení závislá na rozhraních a jako *Přesná* verze pro samostatně nasazená nasazení.</span><span class="sxs-lookup"><span data-stu-id="d2924-133">If a version *is* specified, it's treated as the *minimum* version of ASP.NET Core shared framework for framework-dependent deployments and as an *exact* version for self-contained deployments.</span></span> <span data-ttu-id="d2924-134">To může mít následující důsledky:</span><span class="sxs-lookup"><span data-stu-id="d2924-134">This can have the following consequences:</span></span>

* <span data-ttu-id="d2924-135">Pokud je verze ASP.NET Core nainstalovaná na serveru menší než verze zadaná na PackageReference, proces .NET Core se nepovede spustit.</span><span class="sxs-lookup"><span data-stu-id="d2924-135">If the version of ASP.NET Core installed on the server is less than the version specified on the PackageReference, the .NET Core process fails to launch.</span></span> <span data-ttu-id="d2924-136">Aktualizace Metapackage jsou často k dispozici v NuGet.org před zpřístupněním aktualizací v hostitelských prostředích, jako je Azure.</span><span class="sxs-lookup"><span data-stu-id="d2924-136">Updates to the metapackage are often available on NuGet.org before updates have been made available in hosting environments such as Azure.</span></span> <span data-ttu-id="d2924-137">Aktualizace verze PackageReference na ASP.NET Core by mohla způsobit selhání nasazené aplikace.</span><span class="sxs-lookup"><span data-stu-id="d2924-137">Updating the version on the PackageReference to ASP.NET Core could cause a deployed application to fail.</span></span>
* <span data-ttu-id="d2924-138">Pokud je aplikace nasazena jako [samostatné nasazení](../deploying/index.md#self-contained-deployments-scd), aplikace nemusí obsahovat nejnovější aktualizace zabezpečení .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d2924-138">If the application is deployed as a [self-contained deployment](../deploying/index.md#self-contained-deployments-scd), the application may not contain the latest security updates to .NET Core.</span></span> <span data-ttu-id="d2924-139">Pokud není určena verze, může sada SDK automaticky zahrnovat nejnovější verzi ASP.NET Core v samostatném nasazení.</span><span class="sxs-lookup"><span data-stu-id="d2924-139">When a version isn't specified, the SDK can automatically include the newest version of ASP.NET Core in the self-contained deployment.</span></span>

## <a name="default-compilation-includes-in-net-core-projects"></a><span data-ttu-id="d2924-140">Výchozí kompilace zahrnuje v projektech .NET Core</span><span class="sxs-lookup"><span data-stu-id="d2924-140">Default compilation includes in .NET Core projects</span></span>

<span data-ttu-id="d2924-141">S přesunem do formátu *csproj* v nejnovějších verzích sady SDK jsme přesunuli výchozí zahrnutí a vyloučení položek kompilace a integrovaných prostředků do souborů vlastností sady SDK.</span><span class="sxs-lookup"><span data-stu-id="d2924-141">With the move to the *csproj* format in the latest SDK versions, we've moved the default includes and excludes for compile items and embedded resources to the SDK properties files.</span></span> <span data-ttu-id="d2924-142">To znamená, že už nemusíte tyto položky v souboru projektu zadávat.</span><span class="sxs-lookup"><span data-stu-id="d2924-142">This means that you no longer need to specify these items in your project file.</span></span>

<span data-ttu-id="d2924-143">Hlavním důvodem pro to, aby to bylo, je omezit zbytečné soubory projektu.</span><span class="sxs-lookup"><span data-stu-id="d2924-143">The main reason for doing this is to reduce the clutter in your project file.</span></span> <span data-ttu-id="d2924-144">Výchozí hodnoty, které jsou obsaženy v sadě SDK, by měly pokrývat většinu běžných případů použití, takže je nemusíte opakovat v každém vytvořeném projektu.</span><span class="sxs-lookup"><span data-stu-id="d2924-144">The defaults that are present in the SDK should cover most common use cases, so there is no need to repeat them in every project that you create.</span></span> <span data-ttu-id="d2924-145">To vede k menšímu množství souborů projektu, které jsou v případě potřeby mnohem snazší a v případě potřeby upravitelné.</span><span class="sxs-lookup"><span data-stu-id="d2924-145">This leads to smaller project files that are much easier to understand as well as edit by hand, if needed.</span></span>

<span data-ttu-id="d2924-146">Následující tabulka ukazuje, který prvek a které [globy](https://en.wikipedia.org/wiki/Glob_(programming)) jsou zahrnuty a vyloučeny v sadě SDK:</span><span class="sxs-lookup"><span data-stu-id="d2924-146">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are both included and excluded in the SDK:</span></span>

| <span data-ttu-id="d2924-147">Prvek</span><span class="sxs-lookup"><span data-stu-id="d2924-147">Element</span></span>           | <span data-ttu-id="d2924-148">Zahrnout glob</span><span class="sxs-lookup"><span data-stu-id="d2924-148">Include glob</span></span>                              | <span data-ttu-id="d2924-149">Vyloučit glob</span><span class="sxs-lookup"><span data-stu-id="d2924-149">Exclude glob</span></span>                                                  | <span data-ttu-id="d2924-150">Odebrat glob</span><span class="sxs-lookup"><span data-stu-id="d2924-150">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| <span data-ttu-id="d2924-151">Kompilace</span><span class="sxs-lookup"><span data-stu-id="d2924-151">Compile</span></span>           | <span data-ttu-id="d2924-152">\*\*/\*cs (nebo jiné jazykové rozšíření)</span><span class="sxs-lookup"><span data-stu-id="d2924-152">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="d2924-153">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="d2924-153">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="d2924-154">Není k dispozici</span><span class="sxs-lookup"><span data-stu-id="d2924-154">N/A</span></span>                      |
| <span data-ttu-id="d2924-155">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="d2924-155">EmbeddedResource</span></span>  | <span data-ttu-id="d2924-156">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="d2924-156">\*\*/\*.resx</span></span>                              | <span data-ttu-id="d2924-157">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="d2924-157">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="d2924-158">Není k dispozici</span><span class="sxs-lookup"><span data-stu-id="d2924-158">N/A</span></span>                      |
| <span data-ttu-id="d2924-159">Žádné</span><span class="sxs-lookup"><span data-stu-id="d2924-159">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="d2924-160">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="d2924-160">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="d2924-161">\*\*/\*cs \* .resx\* / \*</span><span class="sxs-lookup"><span data-stu-id="d2924-161">\*\*/\*.cs; \*\*/\*.resx</span></span>   |

> [!NOTE]
> <span data-ttu-id="d2924-162">**Exclude glob** vždy `./bin` `./obj` vyloučí `$(BaseIntermediateOutputPath)` složky a, které jsou reprezentovány vlastnostmi a,vuvedenémpořadí.`$(BaseOutputPath)`</span><span class="sxs-lookup"><span data-stu-id="d2924-162">**Exclude glob** always excludes the `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, respectively.</span></span> <span data-ttu-id="d2924-163">Všechna vyloučení jsou představována `$(DefaultItemExcludes)`jako celek.</span><span class="sxs-lookup"><span data-stu-id="d2924-163">As a whole, all excludes are represented by `$(DefaultItemExcludes)`.</span></span>

<span data-ttu-id="d2924-164">Pokud jste v projektu globy a pokusíte se ho sestavit pomocí nejnovější sady SDK, zobrazí se následující chyba:</span><span class="sxs-lookup"><span data-stu-id="d2924-164">If you have globs in your project and you try to build it using the newest SDK, you'll get the following error:</span></span>

> <span data-ttu-id="d2924-165">Byly zahrnuty duplicitní položky kompilace.</span><span class="sxs-lookup"><span data-stu-id="d2924-165">Duplicate Compile items were included.</span></span> <span data-ttu-id="d2924-166">Sada .NET SDK obsahuje ve výchozím nastavení položky kompilace z adresáře projektu.</span><span class="sxs-lookup"><span data-stu-id="d2924-166">The .NET SDK includes Compile items from your project directory by default.</span></span> <span data-ttu-id="d2924-167">Můžete buď odebrat tyto položky ze souboru projektu, nebo nastavit vlastnost ' EnableDefaultCompileItems ' na hodnotu ' false ', pokud je chcete explicitně zahrnout do souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="d2924-167">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

<span data-ttu-id="d2924-168">Chcete-li se této chybě vyhnout, můžete buď odebrat explicitní `Compile` položky, které odpovídají těm, které jsou uvedeny v předchozí tabulce, nebo můžete `<EnableDefaultCompileItems>` nastavit vlastnost na `false`následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="d2924-168">In order to get around this error, you can either remove the explicit `Compile` items that match the ones listed on the previous table, or you can set the `<EnableDefaultCompileItems>` property to `false`, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

<span data-ttu-id="d2924-169">Nastavením této vlastnosti na `false` zakážete implicitní zahrnutí a vrátíte se do chování předchozích sad SDK, kde jste museli v projektu zadat výchozí globy.</span><span class="sxs-lookup"><span data-stu-id="d2924-169">Setting this property to `false` will disable implicit inclusion, reverting to the behavior of previous SDKs where you had to specify the default globs in your project.</span></span>

<span data-ttu-id="d2924-170">Tato změna neupravuje hlavní mechanismy ostatních zahrnutí.</span><span class="sxs-lookup"><span data-stu-id="d2924-170">This change does not modify the main mechanics of other includes.</span></span> <span data-ttu-id="d2924-171">Nicméně pokud chcete určit, například některé soubory, které mají být publikovány s vaší aplikací, můžete stále používat známé mechanismy v souboru *csproj* pro tento `<Content>` prvek (například element).</span><span class="sxs-lookup"><span data-stu-id="d2924-171">However, if you wish to specify, for example, some files to get published with your app, you can still use the known mechanisms in *csproj* for that (for example, the `<Content>` element).</span></span>

<span data-ttu-id="d2924-172">`<EnableDefaultCompileItems>`zakáže `Compile` jenom globy, ale neovlivní jiné globy, jako je `None` implicitní glob, které platí i \*pro položky. cs.</span><span class="sxs-lookup"><span data-stu-id="d2924-172">`<EnableDefaultCompileItems>` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob, which also applies to \*.cs items.</span></span> <span data-ttu-id="d2924-173">Z tohoto důvodu **Průzkumník řešení** nadále zobrazovat \*položky cs jako součást projektu zahrnuté jako `None` položky.</span><span class="sxs-lookup"><span data-stu-id="d2924-173">Because of that, **Solution Explorer** will continue show \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="d2924-174">Podobným způsobem můžete nastavit `<EnableDefaultNoneItems>` na hodnotu false, chcete-li zakázat implicitní `None` glob, například:</span><span class="sxs-lookup"><span data-stu-id="d2924-174">In a similar way, you can set `<EnableDefaultNoneItems>` to false to disable the implicit `None` glob, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

<span data-ttu-id="d2924-175">Chcete-li zakázat **všechny implicitní globy**, můžete nastavit `<EnableDefaultItems>` vlastnost na `false` jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="d2924-175">To disable **all implicit globs**, you can set the `<EnableDefaultItems>` property to `false` as in the following example:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a><span data-ttu-id="d2924-176">Jak zobrazit celý projekt, když ho MSBuild uvidí</span><span class="sxs-lookup"><span data-stu-id="d2924-176">How to see the whole project as MSBuild sees it</span></span>

<span data-ttu-id="d2924-177">I když tyto změny csproj značně zjednodušují soubory projektu, je možné, že budete chtít zobrazit plně rozbalený projekt jako nástroj MSBuild, jakmile bude sada SDK a její cíle zahrnuté.</span><span class="sxs-lookup"><span data-stu-id="d2924-177">While those csproj changes greatly simplify project files, you might want to see the fully expanded project as MSBuild sees it once the SDK and its targets are included.</span></span> <span data-ttu-id="d2924-178">Projekt předzpracování pomocí [`dotnet msbuild`](dotnet-msbuild.md) [ `/pp` přepínače](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) příkazu, který ukazuje, které soubory jsou importovány, jejich zdroje a jejich příspěvky na sestavení bez skutečného sestavení projektu:</span><span class="sxs-lookup"><span data-stu-id="d2924-178">Preprocess the project with [the `/pp` switch](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) of the [`dotnet msbuild`](dotnet-msbuild.md) command, which shows which files are imported, their sources, and their contributions to the build without actually building the project:</span></span>

`dotnet msbuild -pp:fullproject.xml`

<span data-ttu-id="d2924-179">Pokud má projekt více cílových rozhraní, výsledky příkazu by měly být zaměřené jenom na jeden z nich zadáním jako vlastnost MSBuild:</span><span class="sxs-lookup"><span data-stu-id="d2924-179">If the project has multiple target frameworks, the results of the command should be focused on only one of them by specifying it as an MSBuild property:</span></span>

`dotnet msbuild -p:TargetFramework=netcoreapp2.0 -pp:fullproject.xml`

## <a name="additions"></a><span data-ttu-id="d2924-180">Rozšíření</span><span class="sxs-lookup"><span data-stu-id="d2924-180">Additions</span></span>

### <a name="sdk-attribute"></a><span data-ttu-id="d2924-181">Atribut sady SDK</span><span class="sxs-lookup"><span data-stu-id="d2924-181">Sdk attribute</span></span>

<span data-ttu-id="d2924-182">Kořenový `<Project>` element souboru *. csproj* má nový atribut s názvem `Sdk`.</span><span class="sxs-lookup"><span data-stu-id="d2924-182">The root `<Project>` element of the *.csproj* file has a new attribute called `Sdk`.</span></span> <span data-ttu-id="d2924-183">`Sdk`Určuje sadu SDK, kterou bude projekt používat.</span><span class="sxs-lookup"><span data-stu-id="d2924-183">`Sdk` specifies which SDK will be used by the project.</span></span> <span data-ttu-id="d2924-184">Sada SDK, jak popisuje [dokument vrstvení](cli-msbuild-architecture.md) , je sada [úloh](/visualstudio/msbuild/msbuild-tasks) a [cílů](/visualstudio/msbuild/msbuild-targets) nástroje MSBuild, které mohou sestavovat kód .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d2924-184">The SDK, as the [layering document](cli-msbuild-architecture.md) describes, is a set of MSBuild [tasks](/visualstudio/msbuild/msbuild-tasks) and [targets](/visualstudio/msbuild/msbuild-targets) that can build .NET Core code.</span></span> <span data-ttu-id="d2924-185">Při použití .NET Core 3,0 Preview dodáváme tři hlavní sady SDK pomocí nástrojů .NET Core a dalších dvou sad SDK:</span><span class="sxs-lookup"><span data-stu-id="d2924-185">We ship three main SDKs with the .NET Core tools and an additional two SDKs when using .NET Core 3.0 Preview:</span></span>

1. <span data-ttu-id="d2924-186">.NET Core SDK s ID`Microsoft.NET.Sdk`</span><span class="sxs-lookup"><span data-stu-id="d2924-186">The .NET Core SDK with the ID of `Microsoft.NET.Sdk`</span></span>
2. <span data-ttu-id="d2924-187">Sada Web SDK .NET Core s ID`Microsoft.NET.Sdk.Web`</span><span class="sxs-lookup"><span data-stu-id="d2924-187">The .NET Core web SDK with the ID of `Microsoft.NET.Sdk.Web`</span></span>
3. <span data-ttu-id="d2924-188">Sada SDK knihovny tříd .NET Core Razor s ID`Microsoft.NET.Sdk.Razor`</span><span class="sxs-lookup"><span data-stu-id="d2924-188">The .NET Core Razor Class Library SDK with the ID of `Microsoft.NET.Sdk.Razor`</span></span>
4. <span data-ttu-id="d2924-189">Služba pracovních procesů .NET Core s ID `Microsoft.NET.Sdk.Worker` (.NET Core 3,0 Preview)</span><span class="sxs-lookup"><span data-stu-id="d2924-189">The .NET Core Worker Service with the ID of `Microsoft.NET.Sdk.Worker` (.NET Core 3.0 Preview)</span></span>
5. <span data-ttu-id="d2924-190">WinForms rozhraní .NET Core a WPF s ID `Microsoft.NET.Sdk.WindowsDesktop` (.NET Core 3,0 Preview)</span><span class="sxs-lookup"><span data-stu-id="d2924-190">The .NET Core WinForms and WPF with the ID of `Microsoft.NET.Sdk.WindowsDesktop` (.NET Core 3.0 Preview)</span></span>

<span data-ttu-id="d2924-191">Aby bylo možné používat nástroje `Sdk` .NET Core a sestavovat kód, je `<Project>` nutné mít atribut nastaven na jedno z těchto identifikátorů v elementu.</span><span class="sxs-lookup"><span data-stu-id="d2924-191">You need to have the `Sdk` attribute set to one of those IDs on the `<Project>` element in order to use the .NET Core tools and build your code.</span></span>

### <a name="packagereference"></a><span data-ttu-id="d2924-192">PackageReference</span><span class="sxs-lookup"><span data-stu-id="d2924-192">PackageReference</span></span>

<span data-ttu-id="d2924-193">Element Item Určuje [závislost NuGet v projektu.](/nuget/consume-packages/package-references-in-project-files) `<PackageReference>`</span><span class="sxs-lookup"><span data-stu-id="d2924-193">A `<PackageReference>` item element specifies a [NuGet dependency in the project](/nuget/consume-packages/package-references-in-project-files).</span></span> <span data-ttu-id="d2924-194">`Include` Atribut určuje ID balíčku.</span><span class="sxs-lookup"><span data-stu-id="d2924-194">The `Include` attribute specifies the package ID.</span></span>

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a><span data-ttu-id="d2924-195">Version</span><span class="sxs-lookup"><span data-stu-id="d2924-195">Version</span></span>

<span data-ttu-id="d2924-196">Požadovaný `Version` atribut určuje verzi balíčku, který má být obnoven.</span><span class="sxs-lookup"><span data-stu-id="d2924-196">The required `Version` attribute specifies the version of the package to restore.</span></span> <span data-ttu-id="d2924-197">Atribut respektuje pravidla schématu [správy verzí NuGet](/nuget/reference/package-versioning#version-ranges-and-wildcards) .</span><span class="sxs-lookup"><span data-stu-id="d2924-197">The attribute respects the rules of the [NuGet versioning](/nuget/reference/package-versioning#version-ranges-and-wildcards) scheme.</span></span> <span data-ttu-id="d2924-198">Výchozí chování je přesné porovnávání verzí.</span><span class="sxs-lookup"><span data-stu-id="d2924-198">The default behavior is an exact version match.</span></span> <span data-ttu-id="d2924-199">Zadání `Version="1.2.3"` je například ekvivalentní zápisu `[1.2.3]` NuGet pro přesný balíček verze 1.2.3 balíčku.</span><span class="sxs-lookup"><span data-stu-id="d2924-199">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

#### <a name="includeassets-excludeassets-and-privateassets"></a><span data-ttu-id="d2924-200">IncludeAssets, ExcludeAssets a PrivateAssets</span><span class="sxs-lookup"><span data-stu-id="d2924-200">IncludeAssets, ExcludeAssets and PrivateAssets</span></span>

<span data-ttu-id="d2924-201">`IncludeAssets`atribut určuje, které prostředky patřící k balíčku určenému `<PackageReference>` parametr by měly být spotřebovány.</span><span class="sxs-lookup"><span data-stu-id="d2924-201">`IncludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed.</span></span> <span data-ttu-id="d2924-202">Ve výchozím nastavení jsou zahrnuty všechny prostředky balíčku.</span><span class="sxs-lookup"><span data-stu-id="d2924-202">By default, all package assets are included.</span></span>

<span data-ttu-id="d2924-203">`ExcludeAssets`atribut určuje, které prostředky patřící do balíčku určeného `<PackageReference>` by neměly být spotřebovány.</span><span class="sxs-lookup"><span data-stu-id="d2924-203">`ExcludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should not be consumed.</span></span>

<span data-ttu-id="d2924-204">`PrivateAssets`atribut určuje, které prostředky patřící do balíčku určeného `<PackageReference>` by měly být spotřebovány, ale nikoli do dalšího projektu.</span><span class="sxs-lookup"><span data-stu-id="d2924-204">`PrivateAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed but not flow to the next project.</span></span> <span data-ttu-id="d2924-205">V `Analyzers`případě `Build` , `ContentFiles` že tento atribut není k dispozici, jsou prostředky a majetky soukromé ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="d2924-205">The `Analyzers`, `Build` and `ContentFiles` assets are private by default when this attribute is not present.</span></span>

> [!NOTE]
> <span data-ttu-id="d2924-206">`PrivateAssets`je ekvivalentní k elementu *Project. JSON*/*xproj* `SuppressParent` .</span><span class="sxs-lookup"><span data-stu-id="d2924-206">`PrivateAssets` is equivalent to the *project.json*/*xproj* `SuppressParent` element.</span></span>

<span data-ttu-id="d2924-207">Tyto atributy mohou obsahovat jednu nebo více z následujících položek oddělených středníkem `;` , pokud je uvedena více než jedna:</span><span class="sxs-lookup"><span data-stu-id="d2924-207">These attributes can contain one or more of the following items, separated by the semicolon `;` character if more than one is listed:</span></span>

* <span data-ttu-id="d2924-208">`Compile`– obsah složky lib je k dispozici pro zkompilování.</span><span class="sxs-lookup"><span data-stu-id="d2924-208">`Compile` – the contents of the lib folder are available to compile against.</span></span>
* <span data-ttu-id="d2924-209">`Runtime`– obsah běhové složky se distribuuje.</span><span class="sxs-lookup"><span data-stu-id="d2924-209">`Runtime` – the contents of the runtime folder are distributed.</span></span>
* <span data-ttu-id="d2924-210">`ContentFiles`– používá se obsah složky *contentFiles* .</span><span class="sxs-lookup"><span data-stu-id="d2924-210">`ContentFiles` – the contents of the *contentfiles* folder are used.</span></span>
* <span data-ttu-id="d2924-211">`Build`– jsou použity props/targets ve složce sestavení.</span><span class="sxs-lookup"><span data-stu-id="d2924-211">`Build` – the props/targets in the build folder are used.</span></span>
* <span data-ttu-id="d2924-212">`Native`– obsah z nativních assetů se zkopíruje do výstupní složky pro modul runtime.</span><span class="sxs-lookup"><span data-stu-id="d2924-212">`Native` – the contents from native assets are copied to the output folder for runtime.</span></span>
* <span data-ttu-id="d2924-213">`Analyzers`– Analyzátory se používají.</span><span class="sxs-lookup"><span data-stu-id="d2924-213">`Analyzers` – the analyzers are used.</span></span>

<span data-ttu-id="d2924-214">Atribut může případně obsahovat:</span><span class="sxs-lookup"><span data-stu-id="d2924-214">Alternatively, the attribute can contain:</span></span>

* <span data-ttu-id="d2924-215">`None`– žádný z prostředků se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="d2924-215">`None` – none of the assets are used.</span></span>
* <span data-ttu-id="d2924-216">`All`– používají se všechny prostředky.</span><span class="sxs-lookup"><span data-stu-id="d2924-216">`All` – all assets are used.</span></span>

### <a name="dotnetclitoolreference"></a><span data-ttu-id="d2924-217">DotNetCliToolReference</span><span class="sxs-lookup"><span data-stu-id="d2924-217">DotNetCliToolReference</span></span>
<span data-ttu-id="d2924-218">Element `<DotNetCliToolReference>` Item Určuje nástroj CLI, který uživatel chce obnovit v kontextu projektu.</span><span class="sxs-lookup"><span data-stu-id="d2924-218">A `<DotNetCliToolReference>` item element specifies the CLI tool that the user wants to restore in the context of the project.</span></span> <span data-ttu-id="d2924-219">Je náhradou za `tools` uzel v *Project. JSON*.</span><span class="sxs-lookup"><span data-stu-id="d2924-219">It's a replacement for the `tools` node in *project.json*.</span></span>

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

#### <a name="version"></a><span data-ttu-id="d2924-220">Version</span><span class="sxs-lookup"><span data-stu-id="d2924-220">Version</span></span>

<span data-ttu-id="d2924-221">`Version`Určuje verzi balíčku, který se má obnovit.</span><span class="sxs-lookup"><span data-stu-id="d2924-221">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="d2924-222">Atribut respektuje pravidla schématu [správy verzí NuGet](/nuget/create-packages/dependency-versions#version-ranges) .</span><span class="sxs-lookup"><span data-stu-id="d2924-222">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="d2924-223">Výchozí chování je přesné porovnávání verzí.</span><span class="sxs-lookup"><span data-stu-id="d2924-223">The default behavior is an exact version match.</span></span> <span data-ttu-id="d2924-224">Zadání `Version="1.2.3"` je například ekvivalentní zápisu `[1.2.3]` NuGet pro přesný balíček verze 1.2.3 balíčku.</span><span class="sxs-lookup"><span data-stu-id="d2924-224">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

### <a name="runtimeidentifiers"></a><span data-ttu-id="d2924-225">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="d2924-225">RuntimeIdentifiers</span></span>

<span data-ttu-id="d2924-226">Element Property umožňuje určit seznam [identifikátorů modulu runtime (identifikátorů RID)](../rid-catalog.md) , které jsou v projektu odděleny středníkem. `<RuntimeIdentifiers>`</span><span class="sxs-lookup"><span data-stu-id="d2924-226">The `<RuntimeIdentifiers>` property element lets you specify a semicolon-delimited list of [Runtime Identifiers (RIDs)](../rid-catalog.md) for the project.</span></span>
<span data-ttu-id="d2924-227">Identifikátorů RID umožňuje publikování samostatně obsažených nasazení.</span><span class="sxs-lookup"><span data-stu-id="d2924-227">RIDs enable publishing self-contained deployments.</span></span>

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a><span data-ttu-id="d2924-228">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="d2924-228">RuntimeIdentifier</span></span>

<span data-ttu-id="d2924-229">Element Property umožňuje zadat pouze jeden [identifikátor modulu runtime (RID)](../rid-catalog.md) pro projekt. `<RuntimeIdentifier>`</span><span class="sxs-lookup"><span data-stu-id="d2924-229">The `<RuntimeIdentifier>` property element allows you to specify only one [Runtime Identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="d2924-230">Identifikátor RID umožňuje publikování samostatně zahrnutého nasazení.</span><span class="sxs-lookup"><span data-stu-id="d2924-230">The RID enables publishing a self-contained deployment.</span></span>

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

<span data-ttu-id="d2924-231">Použijte `<RuntimeIdentifiers>` (plural) místo toho, pokud potřebujete publikovat pro více modulů runtime.</span><span class="sxs-lookup"><span data-stu-id="d2924-231">Use `<RuntimeIdentifiers>` (plural) instead if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="d2924-232">`<RuntimeIdentifier>`může poskytovat rychlejší sestavení, je-li vyžadován pouze jeden modul runtime.</span><span class="sxs-lookup"><span data-stu-id="d2924-232">`<RuntimeIdentifier>` can provide faster builds when only a single runtime is required.</span></span>

### <a name="packagetargetfallback"></a><span data-ttu-id="d2924-233">PackageTargetFallback</span><span class="sxs-lookup"><span data-stu-id="d2924-233">PackageTargetFallback</span></span>

<span data-ttu-id="d2924-234">Element `<PackageTargetFallback>` Property umožňuje zadat sadu kompatibilních cílů, které se mají použít při obnovování balíčků.</span><span class="sxs-lookup"><span data-stu-id="d2924-234">The `<PackageTargetFallback>` property element allows you to specify a set of compatible targets to be used when restoring packages.</span></span> <span data-ttu-id="d2924-235">Je navržena tak, aby povolovala balíčky, které používají dotnet [TxM (Target x moniker)](/nuget/schema/target-frameworks) pro práci s balíčky, které nedeklarují dotnet TxM.</span><span class="sxs-lookup"><span data-stu-id="d2924-235">It's designed to allow packages that use the dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) to operate with packages that don't declare a dotnet TxM.</span></span> <span data-ttu-id="d2924-236">Pokud váš projekt používá TxM dotnet, pak všechny balíčky, na kterých závisí, musí mít také hodnotu dotnet TxM, pokud do projektu nepřidáte `<PackageTargetFallback>` , aby bylo možné, aby platformy, které nejsou dotnet, byly kompatibilní s dotnet.</span><span class="sxs-lookup"><span data-stu-id="d2924-236">If your project uses the dotnet TxM, then all the packages it depends on must also have a dotnet TxM, unless you add the `<PackageTargetFallback>` to your project in order to allow non-dotnet platforms to be compatible with dotnet.</span></span>

<span data-ttu-id="d2924-237">Následující příklad poskytuje záložní hodnoty pro všechny cíle v projektu:</span><span class="sxs-lookup"><span data-stu-id="d2924-237">The following example provides the fallbacks for all targets in your project:</span></span>

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

<span data-ttu-id="d2924-238">Následující příklad určuje pouze zálohy pro `netcoreapp2.1` cíl:</span><span class="sxs-lookup"><span data-stu-id="d2924-238">The following example specifies the fallbacks only for the `netcoreapp2.1` target:</span></span>

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp2.1'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="nuget-metadata-properties"></a><span data-ttu-id="d2924-239">Vlastnosti metadat NuGet</span><span class="sxs-lookup"><span data-stu-id="d2924-239">NuGet metadata properties</span></span>

<span data-ttu-id="d2924-240">Při přechodu na MSBuild jsme přesunuli vstupní metadata, která se používají při balení balíčku NuGet z *Project. JSON* do souborů *. csproj* .</span><span class="sxs-lookup"><span data-stu-id="d2924-240">With the move to MSBuild, we have moved the input metadata that is used when packing a NuGet package from *project.json* to *.csproj* files.</span></span> <span data-ttu-id="d2924-241">Vstupy jsou vlastnosti nástroje MSBuild, takže musí jít v rámci `<PropertyGroup>` skupiny.</span><span class="sxs-lookup"><span data-stu-id="d2924-241">The inputs are MSBuild properties so they have to go within a `<PropertyGroup>` group.</span></span> <span data-ttu-id="d2924-242">Následuje seznam vlastností, které se používají jako vstupy do procesu balení při použití `dotnet pack` příkazu `Pack` nebo cíle MSBuild, který je součástí sady SDK.</span><span class="sxs-lookup"><span data-stu-id="d2924-242">The following is the list of properties that are used as inputs to the packing process when using the `dotnet pack` command or the `Pack` MSBuild target that is part of the SDK.</span></span>

### <a name="ispackable"></a><span data-ttu-id="d2924-243">Ispackable nastavenou</span><span class="sxs-lookup"><span data-stu-id="d2924-243">IsPackable</span></span>

<span data-ttu-id="d2924-244">Logická hodnota, která určuje, zda lze projekt zabalit.</span><span class="sxs-lookup"><span data-stu-id="d2924-244">A Boolean value that specifies whether the project can be packed.</span></span> <span data-ttu-id="d2924-245">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="d2924-245">The default value is `true`.</span></span>

### <a name="packageversion"></a><span data-ttu-id="d2924-246">PackageVersion</span><span class="sxs-lookup"><span data-stu-id="d2924-246">PackageVersion</span></span>

<span data-ttu-id="d2924-247">Určuje verzi, kterou výsledný balíček bude mít.</span><span class="sxs-lookup"><span data-stu-id="d2924-247">Specifies the version that the resulting package will have.</span></span> <span data-ttu-id="d2924-248">Akceptuje všechny formy řetězce verze NuGet.</span><span class="sxs-lookup"><span data-stu-id="d2924-248">Accepts all forms of NuGet version string.</span></span> <span data-ttu-id="d2924-249">Výchozí hodnota je hodnota `$(Version)`, to znamená vlastnost `Version` v projektu.</span><span class="sxs-lookup"><span data-stu-id="d2924-249">Default is the value of `$(Version)`, that is, of the property `Version` in the project.</span></span>

### <a name="packageid"></a><span data-ttu-id="d2924-250">PackageId</span><span class="sxs-lookup"><span data-stu-id="d2924-250">PackageId</span></span>

<span data-ttu-id="d2924-251">Určuje název výsledného balíčku.</span><span class="sxs-lookup"><span data-stu-id="d2924-251">Specifies the name for the resulting package.</span></span> <span data-ttu-id="d2924-252">Pokud tento parametr nezadáte `pack` , použije se ve výchozím nastavení `AssemblyName` jako název balíčku název adresáře nebo.</span><span class="sxs-lookup"><span data-stu-id="d2924-252">If not specified, the `pack` operation will default to using the `AssemblyName` or directory name as the name of the package.</span></span>

### <a name="title"></a><span data-ttu-id="d2924-253">Název</span><span class="sxs-lookup"><span data-stu-id="d2924-253">Title</span></span>

<span data-ttu-id="d2924-254">Popisný název balíčku, který se obvykle používá v uživatelském rozhraní, se zobrazuje jako v nuget.org a správce balíčků v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d2924-254">A human-friendly title of the package, typically used in UI displays as on nuget.org and the Package Manager in Visual Studio.</span></span> <span data-ttu-id="d2924-255">Pokud není zadaný, použije se místo toho ID balíčku.</span><span class="sxs-lookup"><span data-stu-id="d2924-255">If not specified, the package ID is used instead.</span></span>

### <a name="authors"></a><span data-ttu-id="d2924-256">Autoři</span><span class="sxs-lookup"><span data-stu-id="d2924-256">Authors</span></span>

<span data-ttu-id="d2924-257">Středníkem oddělený seznam autorů balíčků, které odpovídají názvům profilů v nuget.org. Ty se zobrazí v galerii NuGet na nuget.org a používají se pro balíčky křížového odkazu stejnými autory.</span><span class="sxs-lookup"><span data-stu-id="d2924-257">A semicolon-separated list of packages authors, matching the profile names on nuget.org. These are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span>

### <a name="packagedescription"></a><span data-ttu-id="d2924-258">PackageDescription</span><span class="sxs-lookup"><span data-stu-id="d2924-258">PackageDescription</span></span>

<span data-ttu-id="d2924-259">Dlouhý popis balíčku pro zobrazení uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d2924-259">A long description of the package for UI display.</span></span>

### <a name="description"></a><span data-ttu-id="d2924-260">Popis</span><span class="sxs-lookup"><span data-stu-id="d2924-260">Description</span></span>

<span data-ttu-id="d2924-261">Dlouhý popis pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="d2924-261">A long description for the assembly.</span></span> <span data-ttu-id="d2924-262">Pokud `PackageDescription` není zadaný, použije se tato vlastnost také jako Popis balíčku.</span><span class="sxs-lookup"><span data-stu-id="d2924-262">If `PackageDescription` is not specified then this property is also used as the description of the package.</span></span>

### <a name="copyright"></a><span data-ttu-id="d2924-263">Úprava</span><span class="sxs-lookup"><span data-stu-id="d2924-263">Copyright</span></span>

<span data-ttu-id="d2924-264">Podrobnosti o autorských právech pro balíček.</span><span class="sxs-lookup"><span data-stu-id="d2924-264">Copyright details for the package.</span></span>

### <a name="packagerequirelicenseacceptance"></a><span data-ttu-id="d2924-265">PackageRequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="d2924-265">PackageRequireLicenseAcceptance</span></span>

<span data-ttu-id="d2924-266">Logická hodnota, která určuje, zda klient musí požádat spotřebitele o přijetí licence k balíčku před instalací balíčku.</span><span class="sxs-lookup"><span data-stu-id="d2924-266">A Boolean value that specifies whether the client must prompt the consumer to accept the package license before installing the package.</span></span> <span data-ttu-id="d2924-267">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="d2924-267">The default is `false`.</span></span>

### <a name="packagelicenseexpression"></a><span data-ttu-id="d2924-268">PackageLicenseExpression</span><span class="sxs-lookup"><span data-stu-id="d2924-268">PackageLicenseExpression</span></span>

<span data-ttu-id="d2924-269">Identifikátor nebo výraz [licence SPDX](https://spdx.org/licenses/)</span><span class="sxs-lookup"><span data-stu-id="d2924-269">An [SPDX license identifier](https://spdx.org/licenses/) or expression.</span></span> <span data-ttu-id="d2924-270">Například, `Apache-2.0`.</span><span class="sxs-lookup"><span data-stu-id="d2924-270">For example, `Apache-2.0`.</span></span>

<span data-ttu-id="d2924-271">Tady je úplný seznam [identifikátorů licencí SPDX](https://spdx.org/licenses/).</span><span class="sxs-lookup"><span data-stu-id="d2924-271">Here is the complete list of [SPDX license identifiers](https://spdx.org/licenses/).</span></span> <span data-ttu-id="d2924-272">NuGet.org přijímá při použití výrazu typu licence pouze licence OSI nebo FSF schválené.</span><span class="sxs-lookup"><span data-stu-id="d2924-272">NuGet.org accepts only OSI or FSF approved licenses when using license type expression.</span></span>

<span data-ttu-id="d2924-273">Přesná Syntaxe výrazů s licencí je popsána níže v tématu [ABNF](https://tools.ietf.org/html/rfc5234).</span><span class="sxs-lookup"><span data-stu-id="d2924-273">The exact syntax of the license expressions is described below in [ABNF](https://tools.ietf.org/html/rfc5234).</span></span>

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
> <span data-ttu-id="d2924-274">V jednom okamžiku `PackageLicenseExpression`může `PackageLicenseFile` být `PackageLicenseUrl` určena pouze jedna z a.</span><span class="sxs-lookup"><span data-stu-id="d2924-274">Only one of `PackageLicenseExpression`, `PackageLicenseFile` and `PackageLicenseUrl` can be specified at a time.</span></span>

### <a name="packagelicensefile"></a><span data-ttu-id="d2924-275">PackageLicenseFile</span><span class="sxs-lookup"><span data-stu-id="d2924-275">PackageLicenseFile</span></span>

<span data-ttu-id="d2924-276">Cesta k souboru s licencí v rámci balíčku Pokud používáte licenci, ke které se nepřiřadil identifikátor SPDX, nebo se jedná o vlastní licenci (jinak `PackageLicenseExpression` se upřednostňuje)</span><span class="sxs-lookup"><span data-stu-id="d2924-276">Path to a license file within the package if you are using a license that hasn’t been assigned an SPDX identifier, or it is a custom license (Otherwise `PackageLicenseExpression` is preferred)</span></span>

<span data-ttu-id="d2924-277">Nahrazuje `PackageLicenseUrl`, nejde kombinovat s `PackageLicenseExpression` a vyžaduje Visual Studio 15.9.4, .NET SDK 2.1.502 nebo 2.2.101 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="d2924-277">Replaces `PackageLicenseUrl`, can't be combined with `PackageLicenseExpression` and requires Visual Studio 15.9.4, .NET SDK 2.1.502 or 2.2.101, or newer.</span></span>

<span data-ttu-id="d2924-278">Je potřeba zajistit, aby byl soubor s licencí zabalený tak, že ho do projektu přidáte explicitně, jako příklad použití:</span><span class="sxs-lookup"><span data-stu-id="d2924-278">You will need to ensure the license file is packed by adding it explicitly to the project, example usage:</span></span>

```xml
<PropertyGroup>
  <PackageLicenseFile>LICENSE.txt</PackageLicenseFile>
</PropertyGroup>
<ItemGroup>
  <None Include="licenses\LICENSE.txt" Pack="true" PackagePath="$(PackageLicenseFile)"/>
</ItemGroup>
```

### <a name="packagelicenseurl"></a><span data-ttu-id="d2924-279">PackageLicenseUrl</span><span class="sxs-lookup"><span data-stu-id="d2924-279">PackageLicenseUrl</span></span>

<span data-ttu-id="d2924-280">Adresa URL licence, která se vztahuje na balíček.</span><span class="sxs-lookup"><span data-stu-id="d2924-280">An URL to the license that is applicable to the package.</span></span> <span data-ttu-id="d2924-281">(_nepoužívá se od verze Visual Studio 15.9.4, .NET SDK 2.1.502 a 2.2.101_)</span><span class="sxs-lookup"><span data-stu-id="d2924-281">(_deprecated since Visual Studio 15.9.4, .NET SDK 2.1.502 and 2.2.101_)</span></span>

### <a name="packageiconurl"></a><span data-ttu-id="d2924-282">PackageIconUrl</span><span class="sxs-lookup"><span data-stu-id="d2924-282">PackageIconUrl</span></span>

<span data-ttu-id="d2924-283">Adresa URL obrázku 64 × 64 s průhledným pozadím, který se má použít jako ikona balíčku v zobrazení uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d2924-283">A URL for a 64x64 image with transparent background to use as the icon for the package in UI display.</span></span>

### <a name="packagereleasenotes"></a><span data-ttu-id="d2924-284">PackageReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="d2924-284">PackageReleaseNotes</span></span>

<span data-ttu-id="d2924-285">Poznámky k verzi balíčku</span><span class="sxs-lookup"><span data-stu-id="d2924-285">Release notes for the package.</span></span>

### <a name="packagetags"></a><span data-ttu-id="d2924-286">PackageTags</span><span class="sxs-lookup"><span data-stu-id="d2924-286">PackageTags</span></span>

<span data-ttu-id="d2924-287">Seznam značek oddělených středníkem, který určuje balíček.</span><span class="sxs-lookup"><span data-stu-id="d2924-287">A semicolon-delimited list of tags that designates the package.</span></span>

### <a name="packageoutputpath"></a><span data-ttu-id="d2924-288">PackageOutputPath</span><span class="sxs-lookup"><span data-stu-id="d2924-288">PackageOutputPath</span></span>

<span data-ttu-id="d2924-289">Určuje výstupní cestu, do které bude zahozen zabalený balíček.</span><span class="sxs-lookup"><span data-stu-id="d2924-289">Determines the output path in which the packed package will be dropped.</span></span> <span data-ttu-id="d2924-290">Výchozí hodnota je `$(OutputPath)`.</span><span class="sxs-lookup"><span data-stu-id="d2924-290">Default is `$(OutputPath)`.</span></span>

### <a name="includesymbols"></a><span data-ttu-id="d2924-291">IncludeSymbols</span><span class="sxs-lookup"><span data-stu-id="d2924-291">IncludeSymbols</span></span>
<span data-ttu-id="d2924-292">Tato logická hodnota označuje, zda má balíček při zabalení projektu vytvořit další balíček symbolů.</span><span class="sxs-lookup"><span data-stu-id="d2924-292">This Boolean value indicates whether the package should create an additional symbols package when the project is packed.</span></span> <span data-ttu-id="d2924-293">Formát balíčku symbolů je řízen `SymbolPackageFormat` vlastností.</span><span class="sxs-lookup"><span data-stu-id="d2924-293">The symbols package's format is controlled by the `SymbolPackageFormat` property.</span></span>

### <a name="symbolpackageformat"></a><span data-ttu-id="d2924-294">SymbolPackageFormat</span><span class="sxs-lookup"><span data-stu-id="d2924-294">SymbolPackageFormat</span></span>
<span data-ttu-id="d2924-295">Určuje formát balíčku symbolů.</span><span class="sxs-lookup"><span data-stu-id="d2924-295">Specifies the format of the symbols package.</span></span> <span data-ttu-id="d2924-296">Pokud "Symbols. nupkg", bude balíček starších symbolů vytvořen s příponou *. Symbols. nupkg* , která obsahuje soubory PDB, knihovny DLL a další výstupní soubory.</span><span class="sxs-lookup"><span data-stu-id="d2924-296">If "symbols.nupkg", a legacy symbols package will be created with a *.symbols.nupkg* extension containing PDBs, DLLs, and other output files.</span></span> <span data-ttu-id="d2924-297">Pokud bude "snupkg", vytvoří se balíček symbolů snupkg obsahující přenosné soubory PDB.</span><span class="sxs-lookup"><span data-stu-id="d2924-297">If "snupkg", a snupkg symbol package will be created containing the portable PDBs.</span></span> <span data-ttu-id="d2924-298">Výchozí hodnota je "Symbols. nupkg".</span><span class="sxs-lookup"><span data-stu-id="d2924-298">Default is "symbols.nupkg".</span></span>

### <a name="includesource"></a><span data-ttu-id="d2924-299">IncludeSource</span><span class="sxs-lookup"><span data-stu-id="d2924-299">IncludeSource</span></span>

<span data-ttu-id="d2924-300">Tato logická hodnota označuje, zda by měl proces balíčku vytvořit zdrojový balíček.</span><span class="sxs-lookup"><span data-stu-id="d2924-300">This Boolean value indicates whether the pack process should create a source package.</span></span> <span data-ttu-id="d2924-301">Zdrojový balíček obsahuje zdrojový kód knihovny i soubory PDB.</span><span class="sxs-lookup"><span data-stu-id="d2924-301">The source package contains the library's source code as well as PDB files.</span></span> <span data-ttu-id="d2924-302">Zdrojové soubory jsou umístěny `src/ProjectName` do adresáře ve výsledném souboru balíčku.</span><span class="sxs-lookup"><span data-stu-id="d2924-302">Source files are put under the `src/ProjectName` directory in the resulting package file.</span></span>

### <a name="istool"></a><span data-ttu-id="d2924-303">Nástroj</span><span class="sxs-lookup"><span data-stu-id="d2924-303">IsTool</span></span>

<span data-ttu-id="d2924-304">Určuje, zda jsou všechny výstupní soubory zkopírovány do složky *Tools* namísto složky *lib* .</span><span class="sxs-lookup"><span data-stu-id="d2924-304">Specifies whether all output files are copied to the *tools* folder instead of the *lib* folder.</span></span> <span data-ttu-id="d2924-305">Všimněte si, že se liší od `DotNetCliTool` a, který je určen `PackageType` nastavením v souboru *. csproj* .</span><span class="sxs-lookup"><span data-stu-id="d2924-305">Note that this is different from a `DotNetCliTool` which is specified by setting the `PackageType` in the *.csproj* file.</span></span>

### <a name="repositoryurl"></a><span data-ttu-id="d2924-306">RepositoryUrl</span><span class="sxs-lookup"><span data-stu-id="d2924-306">RepositoryUrl</span></span>

<span data-ttu-id="d2924-307">Určuje adresu URL úložiště, ve kterém se nachází zdrojový kód balíčku, nebo ze kterého se vytváří.</span><span class="sxs-lookup"><span data-stu-id="d2924-307">Specifies the URL for the repository where the source code for the package resides and/or from which it's being built.</span></span>

### <a name="repositorytype"></a><span data-ttu-id="d2924-308">RepositoryType</span><span class="sxs-lookup"><span data-stu-id="d2924-308">RepositoryType</span></span>

<span data-ttu-id="d2924-309">Určuje typ úložiště.</span><span class="sxs-lookup"><span data-stu-id="d2924-309">Specifies the type of the repository.</span></span> <span data-ttu-id="d2924-310">Výchozí hodnota je "git".</span><span class="sxs-lookup"><span data-stu-id="d2924-310">Default is "git".</span></span>

### <a name="nopackageanalysis"></a><span data-ttu-id="d2924-311">NoPackageAnalysis</span><span class="sxs-lookup"><span data-stu-id="d2924-311">NoPackageAnalysis</span></span>

<span data-ttu-id="d2924-312">Určuje, že sada by neměla po sestavení balíčku spustit analýzu balíčku.</span><span class="sxs-lookup"><span data-stu-id="d2924-312">Specifies that pack should not run package analysis after building the package.</span></span>

### <a name="minclientversion"></a><span data-ttu-id="d2924-313">MinClientVersion</span><span class="sxs-lookup"><span data-stu-id="d2924-313">MinClientVersion</span></span>

<span data-ttu-id="d2924-314">Určuje minimální verzi klienta NuGet, která může nainstalovat tento balíček, který vynutila NuGet. exe a správce balíčků sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d2924-314">Specifies the minimum version of the NuGet client that can install this package, enforced by nuget.exe and the Visual Studio Package Manager.</span></span>

### <a name="includebuildoutput"></a><span data-ttu-id="d2924-315">IncludeBuildOutput</span><span class="sxs-lookup"><span data-stu-id="d2924-315">IncludeBuildOutput</span></span>

<span data-ttu-id="d2924-316">Tato logická hodnota určuje, zda mají být výstupní sestavení sestavení zabalena do souboru *. nupkg* nebo ne.</span><span class="sxs-lookup"><span data-stu-id="d2924-316">This Boolean values specifies whether the build output assemblies should be packed into the *.nupkg* file or not.</span></span>

### <a name="includecontentinpack"></a><span data-ttu-id="d2924-317">IncludeContentInPack</span><span class="sxs-lookup"><span data-stu-id="d2924-317">IncludeContentInPack</span></span>

<span data-ttu-id="d2924-318">Tato logická hodnota určuje, zda `Content` budou do výsledného balíčku automaticky zahrnuty všechny položky, které mají typ.</span><span class="sxs-lookup"><span data-stu-id="d2924-318">This Boolean value specifies whether any items that have a type of `Content` will be included in the resulting package automatically.</span></span> <span data-ttu-id="d2924-319">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="d2924-319">The default is `true`.</span></span>

### <a name="buildoutputtargetfolder"></a><span data-ttu-id="d2924-320">BuildOutputTargetFolder</span><span class="sxs-lookup"><span data-stu-id="d2924-320">BuildOutputTargetFolder</span></span>

<span data-ttu-id="d2924-321">Určuje složku, kam se mají umístit výstupní sestavení.</span><span class="sxs-lookup"><span data-stu-id="d2924-321">Specifies the folder where to place the output assemblies.</span></span> <span data-ttu-id="d2924-322">Výstupní sestavení (a další výstupní soubory) se zkopírují do příslušných složek rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d2924-322">The output assemblies (and other output files) are copied into their respective framework folders.</span></span>

### <a name="contenttargetfolders"></a><span data-ttu-id="d2924-323">ContentTargetFolders</span><span class="sxs-lookup"><span data-stu-id="d2924-323">ContentTargetFolders</span></span>

<span data-ttu-id="d2924-324">Tato vlastnost určuje výchozí umístění, kde mají všechny soubory obsahu jít, pokud `PackagePath` nejsou pro ně zadány.</span><span class="sxs-lookup"><span data-stu-id="d2924-324">This property specifies the default location of where all the content files should go if `PackagePath` is not specified for them.</span></span> <span data-ttu-id="d2924-325">Výchozí hodnota je Content; contentFiles.</span><span class="sxs-lookup"><span data-stu-id="d2924-325">The default value is "content;contentFiles".</span></span>

### <a name="nuspecfile"></a><span data-ttu-id="d2924-326">NuspecFile</span><span class="sxs-lookup"><span data-stu-id="d2924-326">NuspecFile</span></span>

<span data-ttu-id="d2924-327">Relativní nebo absolutní cesta k souboru *. nuspec* , který se používá pro balení.</span><span class="sxs-lookup"><span data-stu-id="d2924-327">Relative or absolute path to the *.nuspec* file being used for packing.</span></span>

> [!NOTE]
> <span data-ttu-id="d2924-328">Je-li zadán soubor *. nuspec* , používá se **výhradně** k balení informací a žádné informace v projektech se nepoužívají.</span><span class="sxs-lookup"><span data-stu-id="d2924-328">If the *.nuspec* file is specified, it's used **exclusively** for packaging information and any information in the projects is not used.</span></span>

### <a name="nuspecbasepath"></a><span data-ttu-id="d2924-329">NuspecBasePath</span><span class="sxs-lookup"><span data-stu-id="d2924-329">NuspecBasePath</span></span>

<span data-ttu-id="d2924-330">Základní cesta pro soubor *. nuspec*</span><span class="sxs-lookup"><span data-stu-id="d2924-330">Base path for the *.nuspec* file.</span></span>

### <a name="nuspecproperties"></a><span data-ttu-id="d2924-331">NuspecProperties</span><span class="sxs-lookup"><span data-stu-id="d2924-331">NuspecProperties</span></span>

<span data-ttu-id="d2924-332">Seznam párů klíč = hodnota oddělený středníkem.</span><span class="sxs-lookup"><span data-stu-id="d2924-332">Semicolon separated list of key=value pairs.</span></span>

## <a name="assemblyinfo-properties"></a><span data-ttu-id="d2924-333">Vlastnosti AssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="d2924-333">AssemblyInfo properties</span></span>

<span data-ttu-id="d2924-334">[Atributy sestavení](../../standard/assembly/set-attributes.md) , které byly obvykle přítomny v souboru *AssemblyInfo* , se nyní automaticky generují z vlastností.</span><span class="sxs-lookup"><span data-stu-id="d2924-334">[Assembly attributes](../../standard/assembly/set-attributes.md) that were typically present in an *AssemblyInfo* file are now automatically generated from properties.</span></span>

### <a name="properties-per-attribute"></a><span data-ttu-id="d2924-335">Vlastnosti na atribut</span><span class="sxs-lookup"><span data-stu-id="d2924-335">Properties per attribute</span></span>

<span data-ttu-id="d2924-336">Každý atribut má vlastnost, která řídí svůj obsah a druhý pro zakázání jeho generování, jak je znázorněno v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="d2924-336">Each attribute has a property that control its content and another to disable its generation as shown in the following table:</span></span>

| <span data-ttu-id="d2924-337">Atribut</span><span class="sxs-lookup"><span data-stu-id="d2924-337">Attribute</span></span>                                                      | <span data-ttu-id="d2924-338">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="d2924-338">Property</span></span>               | <span data-ttu-id="d2924-339">Vlastnost, která se má zakázat</span><span class="sxs-lookup"><span data-stu-id="d2924-339">Property to disable</span></span>                             |
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

<span data-ttu-id="d2924-340">Poznámky:</span><span class="sxs-lookup"><span data-stu-id="d2924-340">Notes:</span></span>

* <span data-ttu-id="d2924-341">`AssemblyVersion`ve výchozím nastavení je to, že se `$(Version)` má přebírat hodnota bez přípony. `FileVersion`</span><span class="sxs-lookup"><span data-stu-id="d2924-341">`AssemblyVersion` and `FileVersion` default is to take the value of `$(Version)` without suffix.</span></span> <span data-ttu-id="d2924-342">Například pokud `$(Version)` je `1.2.3-beta.4`, `1.2.3`pak hodnota by byla.</span><span class="sxs-lookup"><span data-stu-id="d2924-342">For example, if `$(Version)` is `1.2.3-beta.4`, then the value would be `1.2.3`.</span></span>
* <span data-ttu-id="d2924-343">`InformationalVersion`Výchozí hodnota `$(Version)`je.</span><span class="sxs-lookup"><span data-stu-id="d2924-343">`InformationalVersion` defaults to the value of `$(Version)`.</span></span>
* <span data-ttu-id="d2924-344">`InformationalVersion`má `$(SourceRevisionId)` připojení, pokud je vlastnost přítomna.</span><span class="sxs-lookup"><span data-stu-id="d2924-344">`InformationalVersion` has `$(SourceRevisionId)` appended if the property is present.</span></span> <span data-ttu-id="d2924-345">Dá se zakázat pomocí `IncludeSourceRevisionInInformationalVersion`.</span><span class="sxs-lookup"><span data-stu-id="d2924-345">It can be disabled using `IncludeSourceRevisionInInformationalVersion`.</span></span>
* <span data-ttu-id="d2924-346">`Copyright`a `Description` vlastnosti se také používají pro metadata NuGet.</span><span class="sxs-lookup"><span data-stu-id="d2924-346">`Copyright` and `Description` properties are also used for NuGet metadata.</span></span>
* <span data-ttu-id="d2924-347">`Configuration`je sdílen se všemi procesy sestavení a nastavena prostřednictvím `--configuration` `dotnet` parametru příkazů.</span><span class="sxs-lookup"><span data-stu-id="d2924-347">`Configuration` is shared with all the build process and set via the `--configuration` parameter of `dotnet` commands.</span></span>

### <a name="generateassemblyinfo"></a><span data-ttu-id="d2924-348">GenerateAssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="d2924-348">GenerateAssemblyInfo</span></span>

<span data-ttu-id="d2924-349">Logická hodnota, která povolí nebo zakáže všechny generace AssemblyInfo.</span><span class="sxs-lookup"><span data-stu-id="d2924-349">A Boolean that enable or disable all the AssemblyInfo generation.</span></span> <span data-ttu-id="d2924-350">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="d2924-350">The default value is `true`.</span></span>

### <a name="generatedassemblyinfofile"></a><span data-ttu-id="d2924-351">GeneratedAssemblyInfoFile</span><span class="sxs-lookup"><span data-stu-id="d2924-351">GeneratedAssemblyInfoFile</span></span>

<span data-ttu-id="d2924-352">Cesta k vygenerovanému souboru s informacemi o sestavení</span><span class="sxs-lookup"><span data-stu-id="d2924-352">The path of the generated assembly info file.</span></span> <span data-ttu-id="d2924-353">Ve výchozím nastavení se jedná o `$(IntermediateOutputPath)` soubor v adresáři (obj).</span><span class="sxs-lookup"><span data-stu-id="d2924-353">Default to a file in the `$(IntermediateOutputPath)` (obj) directory.</span></span>
