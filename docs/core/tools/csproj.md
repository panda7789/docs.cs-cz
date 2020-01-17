---
title: Přidání do formátu csproj pro .NET Core
description: Přečtěte si o rozdílech mezi existujícími a soubory .NET Core csproj.
ms.date: 04/08/2019
ms.openlocfilehash: da066625b445eca9186acedf06a941564921a6dd
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115849"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a><span data-ttu-id="91d63-103">Přidání do formátu csproj pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="91d63-103">Additions to the csproj format for .NET Core</span></span>

<span data-ttu-id="91d63-104">Tento dokument popisuje změny, které byly přidány do souborů projektu jako součást přesunutí z *Project. JSON* na *csproj* a [MSBuild](https://github.com/Microsoft/MSBuild).</span><span class="sxs-lookup"><span data-stu-id="91d63-104">This document outlines the changes that were added to the project files as part of the move from *project.json* to *csproj* and [MSBuild](https://github.com/Microsoft/MSBuild).</span></span> <span data-ttu-id="91d63-105">Další informace o obecných syntaxech souborů projektu a referenčních informacích naleznete v dokumentaci k [souboru projektu MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) .</span><span class="sxs-lookup"><span data-stu-id="91d63-105">For more information about general project file syntax and reference, see [the MSBuild project file](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation.</span></span>

## <a name="implicit-package-references"></a><span data-ttu-id="91d63-106">Odkazy na implicitní balíčky</span><span class="sxs-lookup"><span data-stu-id="91d63-106">Implicit package references</span></span>

<span data-ttu-id="91d63-107">Na metabalíčky se implicitně odkazuje na základě cílových rozhraní .NET Framework určených ve vlastnosti `<TargetFramework>` nebo `<TargetFrameworks>` souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="91d63-107">Metapackages are implicitly referenced based on the target framework(s) specified in the `<TargetFramework>` or `<TargetFrameworks>` property of your project file.</span></span> <span data-ttu-id="91d63-108">`<TargetFrameworks>` se ignoruje, pokud je zadána `<TargetFramework>`, nezávisle na pořadí.</span><span class="sxs-lookup"><span data-stu-id="91d63-108">`<TargetFrameworks>` is ignored if `<TargetFramework>` is specified, independent of order.</span></span> <span data-ttu-id="91d63-109">Další informace najdete v tématech [balíčky, metabalíčky a rozhraní](../packages.md).</span><span class="sxs-lookup"><span data-stu-id="91d63-109">For more information, see [Packages, metapackages, and frameworks](../packages.md).</span></span> 

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

### <a name="recommendations"></a><span data-ttu-id="91d63-110">Doporučení</span><span class="sxs-lookup"><span data-stu-id="91d63-110">Recommendations</span></span>

<span data-ttu-id="91d63-111">Vzhledem k tomu, že se na `Microsoft.NETCore.App` nebo `NETStandard.Library` metabalíčky implicitně odkazují, následující doporučené osvědčené postupy:</span><span class="sxs-lookup"><span data-stu-id="91d63-111">Since `Microsoft.NETCore.App` or `NETStandard.Library` metapackages are implicitly referenced, the following are our recommended best practices:</span></span>

- <span data-ttu-id="91d63-112">Pokud cílíte na rozhraní .NET Core nebo .NET Standard, nikdy nemusíte mít explicitní odkaz na `Microsoft.NETCore.App` nebo `NETStandard.Library` metabalíčky prostřednictvím položky `<PackageReference>` v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="91d63-112">When targeting .NET Core or .NET Standard, never have an explicit reference to the `Microsoft.NETCore.App` or `NETStandard.Library` metapackages via a `<PackageReference>` item in your project file.</span></span>
- <span data-ttu-id="91d63-113">Pokud potřebujete specifickou verzi modulu runtime při cílení na .NET Core, měli byste použít vlastnost `<RuntimeFrameworkVersion>` v projektu (například `1.0.4`) namísto odkazování na Metapackage.</span><span class="sxs-lookup"><span data-stu-id="91d63-113">If you need a specific version of the runtime when targeting .NET Core, you should use the `<RuntimeFrameworkVersion>` property in your project (for example, `1.0.4`) instead of referencing the metapackage.</span></span>
  - <span data-ttu-id="91d63-114">K tomu může dojít, pokud používáte [samostatná nasazení](../deploying/index.md#self-contained-deployments-scd) a potřebujete konkrétní opravu verze 1.0.0 LTS runtime, například.</span><span class="sxs-lookup"><span data-stu-id="91d63-114">This might happen if you are using [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) and you need a specific patch version of 1.0.0 LTS runtime, for example.</span></span>
- <span data-ttu-id="91d63-115">Pokud potřebujete specifickou verzi `NETStandard.Library` Metapackage při cílení na .NET Standard, můžete použít vlastnost `<NetStandardImplicitPackageVersion>` a nastavit požadovanou verzi.</span><span class="sxs-lookup"><span data-stu-id="91d63-115">If you need a specific version of the `NETStandard.Library` metapackage when targeting .NET Standard, you can use the `<NetStandardImplicitPackageVersion>` property and set the version you need.</span></span>
- <span data-ttu-id="91d63-116">Nedávejte explicitně odkazy ani neaktualizujte `Microsoft.NETCore.App` ani `NETStandard.Library` Metapackage v projektech .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="91d63-116">Don't explicitly add or update references to either the `Microsoft.NETCore.App` or `NETStandard.Library` metapackage in .NET Framework projects.</span></span> <span data-ttu-id="91d63-117">Pokud je při použití balíčku NuGet založeného na .NET Standard potřeba libovolná verze `NETStandard.Library`, NuGet tuto verzi nainstaluje automaticky.</span><span class="sxs-lookup"><span data-stu-id="91d63-117">If any version of `NETStandard.Library` is needed when using a .NET Standard-based NuGet package, NuGet automatically installs that version.</span></span>

## <a name="implicit-version-for-some-package-references"></a><span data-ttu-id="91d63-118">Implicitní verze pro některé odkazy na balíčky</span><span class="sxs-lookup"><span data-stu-id="91d63-118">Implicit version for some package references</span></span>

<span data-ttu-id="91d63-119">Většina použití [`<PackageReference>`](#packagereference) vyžaduje nastavení atributu `Version` k určení verze balíčku NuGet, která se má použít.</span><span class="sxs-lookup"><span data-stu-id="91d63-119">Most usages of [`<PackageReference>`](#packagereference) require setting the `Version` attribute to specify the NuGet package version to be used.</span></span> <span data-ttu-id="91d63-120">Při použití .NET Core 2,1 nebo 2,2 a odkazování na [Microsoft. AspNetCore. app](/aspnet/core/fundamentals/metapackage-app) nebo [Microsoft. AspNetCore. All](/aspnet/core/fundamentals/metapackage)ale atribut není zbytečný.</span><span class="sxs-lookup"><span data-stu-id="91d63-120">When using .NET Core 2.1 or 2.2 and referencing [Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) or [Microsoft.AspNetCore.All](/aspnet/core/fundamentals/metapackage), however, the  attribute is unnecessary.</span></span> <span data-ttu-id="91d63-121">.NET Core SDK může automaticky vybrat verzi těchto balíčků, které by se měly použít.</span><span class="sxs-lookup"><span data-stu-id="91d63-121">The .NET Core SDK can automatically select the version of these packages that should be used.</span></span>

### <a name="recommendation"></a><span data-ttu-id="91d63-122">Doporučení</span><span class="sxs-lookup"><span data-stu-id="91d63-122">Recommendation</span></span>

<span data-ttu-id="91d63-123">Při odkazování na balíčky `Microsoft.AspNetCore.App` nebo `Microsoft.AspNetCore.All` nezadávejte jejich verzi.</span><span class="sxs-lookup"><span data-stu-id="91d63-123">When referencing the `Microsoft.AspNetCore.App` or `Microsoft.AspNetCore.All` packages, do not specify their version.</span></span> <span data-ttu-id="91d63-124">Pokud je zadána verze, sada SDK může vytvořit upozornění NETSDK1071.</span><span class="sxs-lookup"><span data-stu-id="91d63-124">If a version is specified, the SDK may produce warning NETSDK1071.</span></span> <span data-ttu-id="91d63-125">Chcete-li toto upozornění vyřešit, odeberte verzi balíčku, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="91d63-125">To fix this warning, remove the package version like in the following example:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore.App" />
</ItemGroup>
```

> <span data-ttu-id="91d63-126">Známý problém: sada .NET Core 2,1 SDK podporuje pouze tuto syntaxi pouze v případě, že projekt používá také Microsoft. NET. SDK. Web.</span><span class="sxs-lookup"><span data-stu-id="91d63-126">Known issue: the .NET Core 2.1 SDK only supported this syntax when the project also uses Microsoft.NET.Sdk.Web.</span></span> <span data-ttu-id="91d63-127">To je vyřešeno v sadě .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="91d63-127">This is resolved in the .NET Core 2.2 SDK.</span></span>

<span data-ttu-id="91d63-128">Tyto odkazy na ASP.NET Core metabalíčky mají mírně odlišné chování z většiny běžných balíčků NuGet.</span><span class="sxs-lookup"><span data-stu-id="91d63-128">These references to ASP.NET Core metapackages have a slightly different behavior from most normal NuGet packages.</span></span> <span data-ttu-id="91d63-129">[Nasazení aplikací závislých na rozhraních](../deploying/index.md#framework-dependent-deployments-fdd) , která používají tyto metabalíčky, automaticky využívají ASP.NET Core sdílené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="91d63-129">[Framework-dependent deployments](../deploying/index.md#framework-dependent-deployments-fdd) of applications that use these metapackages automatically take advantage of the ASP.NET Core shared framework.</span></span> <span data-ttu-id="91d63-130">Při použití metabalíčky se s aplikací nasadí **žádné** prostředky z odkazovaného ASP.NET Core balíčků NuGet – ASP.NET Core sdílené rozhraní obsahuje tyto prostředky.</span><span class="sxs-lookup"><span data-stu-id="91d63-130">When you use the metapackages, **no** assets from the referenced ASP.NET Core NuGet packages are deployed with the application—the ASP.NET Core shared framework contains these assets.</span></span> <span data-ttu-id="91d63-131">Prostředky ve sdíleném rozhraní jsou optimalizované pro cílovou platformu pro zlepšení času spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="91d63-131">The assets in the shared framework are optimized for the target platform to improve application startup time.</span></span> <span data-ttu-id="91d63-132">Další informace o sdílených rozhraních naleznete v tématu [distribuční balíček .NET Core](../build/distribution-packaging.md).</span><span class="sxs-lookup"><span data-stu-id="91d63-132">For more information about shared framework, see [.NET Core distribution packaging](../build/distribution-packaging.md).</span></span>

<span data-ttu-id="91d63-133">*Je* -li zadána verze, je zpracována jako *minimální* verze ASP.NET Core sdílené architektury pro nasazení závislá na rozhraních a jako *Přesná* verze pro samostatně nasazená nasazení.</span><span class="sxs-lookup"><span data-stu-id="91d63-133">If a version *is* specified, it's treated as the *minimum* version of ASP.NET Core shared framework for framework-dependent deployments and as an *exact* version for self-contained deployments.</span></span> <span data-ttu-id="91d63-134">To může mít následující důsledky:</span><span class="sxs-lookup"><span data-stu-id="91d63-134">This can have the following consequences:</span></span>

- <span data-ttu-id="91d63-135">Pokud je verze ASP.NET Core nainstalovaná na serveru menší než verze zadaná na PackageReference, proces .NET Core se nepovede spustit.</span><span class="sxs-lookup"><span data-stu-id="91d63-135">If the version of ASP.NET Core installed on the server is less than the version specified on the PackageReference, the .NET Core process fails to launch.</span></span> <span data-ttu-id="91d63-136">Aktualizace Metapackage jsou často k dispozici v NuGet.org před zpřístupněním aktualizací v hostitelských prostředích, jako je Azure.</span><span class="sxs-lookup"><span data-stu-id="91d63-136">Updates to the metapackage are often available on NuGet.org before updates have been made available in hosting environments such as Azure.</span></span> <span data-ttu-id="91d63-137">Aktualizace verze PackageReference na ASP.NET Core by mohla způsobit selhání nasazené aplikace.</span><span class="sxs-lookup"><span data-stu-id="91d63-137">Updating the version on the PackageReference to ASP.NET Core could cause a deployed application to fail.</span></span>
- <span data-ttu-id="91d63-138">Pokud je aplikace nasazena jako [samostatné nasazení](../deploying/index.md#self-contained-deployments-scd), aplikace nemusí obsahovat nejnovější aktualizace zabezpečení .NET Core.</span><span class="sxs-lookup"><span data-stu-id="91d63-138">If the application is deployed as a [self-contained deployment](../deploying/index.md#self-contained-deployments-scd), the application may not contain the latest security updates to .NET Core.</span></span> <span data-ttu-id="91d63-139">Pokud není určena verze, může sada SDK automaticky zahrnovat nejnovější verzi ASP.NET Core v samostatném nasazení.</span><span class="sxs-lookup"><span data-stu-id="91d63-139">When a version isn't specified, the SDK can automatically include the newest version of ASP.NET Core in the self-contained deployment.</span></span>

## <a name="default-compilation-includes-in-net-core-projects"></a><span data-ttu-id="91d63-140">Výchozí kompilace zahrnuje v projektech .NET Core</span><span class="sxs-lookup"><span data-stu-id="91d63-140">Default compilation includes in .NET Core projects</span></span>

<span data-ttu-id="91d63-141">S přesunem do formátu *csproj* v nejnovějších verzích sady SDK jsme přesunuli výchozí zahrnutí a vyloučení položek kompilace a integrovaných prostředků do souborů vlastností sady SDK.</span><span class="sxs-lookup"><span data-stu-id="91d63-141">With the move to the *csproj* format in the latest SDK versions, we've moved the default includes and excludes for compile items and embedded resources to the SDK properties files.</span></span> <span data-ttu-id="91d63-142">To znamená, že už nemusíte tyto položky v souboru projektu zadávat.</span><span class="sxs-lookup"><span data-stu-id="91d63-142">This means that you no longer need to specify these items in your project file.</span></span>

<span data-ttu-id="91d63-143">Hlavním důvodem pro to, aby to bylo, je omezit zbytečné soubory projektu.</span><span class="sxs-lookup"><span data-stu-id="91d63-143">The main reason for doing this is to reduce the clutter in your project file.</span></span> <span data-ttu-id="91d63-144">Výchozí hodnoty, které jsou obsaženy v sadě SDK, by měly pokrývat většinu běžných případů použití, takže je nemusíte opakovat v každém vytvořeném projektu.</span><span class="sxs-lookup"><span data-stu-id="91d63-144">The defaults that are present in the SDK should cover most common use cases, so there is no need to repeat them in every project that you create.</span></span> <span data-ttu-id="91d63-145">To vede k menšímu množství souborů projektu, které jsou v případě potřeby mnohem snazší a v případě potřeby upravitelné.</span><span class="sxs-lookup"><span data-stu-id="91d63-145">This leads to smaller project files that are much easier to understand as well as edit by hand, if needed.</span></span>

<span data-ttu-id="91d63-146">Následující tabulka ukazuje, který prvek a které [globy](https://en.wikipedia.org/wiki/Glob_(programming)) jsou zahrnuty a vyloučeny v sadě SDK:</span><span class="sxs-lookup"><span data-stu-id="91d63-146">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are both included and excluded in the SDK:</span></span>

| <span data-ttu-id="91d63-147">Prvek</span><span class="sxs-lookup"><span data-stu-id="91d63-147">Element</span></span>           | <span data-ttu-id="91d63-148">Zahrnout glob</span><span class="sxs-lookup"><span data-stu-id="91d63-148">Include glob</span></span>                              | <span data-ttu-id="91d63-149">Vyloučit glob</span><span class="sxs-lookup"><span data-stu-id="91d63-149">Exclude glob</span></span>                                                  | <span data-ttu-id="91d63-150">Odebrat glob</span><span class="sxs-lookup"><span data-stu-id="91d63-150">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| <span data-ttu-id="91d63-151">Kompilace</span><span class="sxs-lookup"><span data-stu-id="91d63-151">Compile</span></span>           | <span data-ttu-id="91d63-152">\*\*/\*. cs (nebo jiné jazykové rozšíření)</span><span class="sxs-lookup"><span data-stu-id="91d63-152">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="91d63-153">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="91d63-153">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="91d63-154">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="91d63-154">N/A</span></span>                      |
| <span data-ttu-id="91d63-155">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="91d63-155">EmbeddedResource</span></span>  | <span data-ttu-id="91d63-156">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="91d63-156">\*\*/\*.resx</span></span>                              | <span data-ttu-id="91d63-157">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="91d63-157">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="91d63-158">NEUŽÍVÁ SE.</span><span class="sxs-lookup"><span data-stu-id="91d63-158">N/A</span></span>                      |
| <span data-ttu-id="91d63-159">Žádné</span><span class="sxs-lookup"><span data-stu-id="91d63-159">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="91d63-160">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="91d63-160">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="91d63-161">\*\*/\*. cs; \*\*/\*. resx</span><span class="sxs-lookup"><span data-stu-id="91d63-161">\*\*/\*.cs; \*\*/\*.resx</span></span>   |

> [!NOTE]
> <span data-ttu-id="91d63-162">**Vyloučit glob** vždy vylučuje `./bin` a `./obj` složky, které jsou reprezentovány `$(BaseOutputPath)` a `$(BaseIntermediateOutputPath)` vlastnostech nástroje MSBuild v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="91d63-162">**Exclude glob** always excludes the `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, respectively.</span></span> <span data-ttu-id="91d63-163">Všechna vyloučení jsou představována `$(DefaultItemExcludes)`.</span><span class="sxs-lookup"><span data-stu-id="91d63-163">As a whole, all excludes are represented by `$(DefaultItemExcludes)`.</span></span>

<span data-ttu-id="91d63-164">Pokud jste v projektu globy a pokusíte se ho sestavit pomocí nejnovější sady SDK, zobrazí se následující chyba:</span><span class="sxs-lookup"><span data-stu-id="91d63-164">If you have globs in your project and you try to build it using the newest SDK, you'll get the following error:</span></span>

> <span data-ttu-id="91d63-165">Byly zahrnuty duplicitní položky kompilace.</span><span class="sxs-lookup"><span data-stu-id="91d63-165">Duplicate Compile items were included.</span></span> <span data-ttu-id="91d63-166">Sada .NET SDK obsahuje ve výchozím nastavení položky kompilace z adresáře projektu.</span><span class="sxs-lookup"><span data-stu-id="91d63-166">The .NET SDK includes Compile items from your project directory by default.</span></span> <span data-ttu-id="91d63-167">Můžete buď odebrat tyto položky ze souboru projektu, nebo nastavit vlastnost ' EnableDefaultCompileItems ' na hodnotu ' false ', pokud je chcete explicitně zahrnout do souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="91d63-167">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

<span data-ttu-id="91d63-168">Chcete-li se této chybě vyhnout, můžete buď odebrat explicitní `Compile` položky, které odpovídají těm, které jsou uvedeny v předchozí tabulce, nebo můžete nastavit vlastnost `<EnableDefaultCompileItems>` na `false`, například takto:</span><span class="sxs-lookup"><span data-stu-id="91d63-168">In order to get around this error, you can either remove the explicit `Compile` items that match the ones listed on the previous table, or you can set the `<EnableDefaultCompileItems>` property to `false`, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

<span data-ttu-id="91d63-169">Nastavením této vlastnosti na `false` zakážete implicitní zahrnutí, vrátíte se do chování předchozích sad SDK, kde jste museli zadat výchozí globy v projektu.</span><span class="sxs-lookup"><span data-stu-id="91d63-169">Setting this property to `false` will disable implicit inclusion, reverting to the behavior of previous SDKs where you had to specify the default globs in your project.</span></span>

<span data-ttu-id="91d63-170">Tato změna neupravuje hlavní mechanismy ostatních zahrnutí.</span><span class="sxs-lookup"><span data-stu-id="91d63-170">This change does not modify the main mechanics of other includes.</span></span> <span data-ttu-id="91d63-171">Nicméně pokud chcete určit, například některé soubory, které mají být publikovány s vaší aplikací, můžete i nadále používat známé mechanismy v souboru *csproj* pro to (například `<Content>` element).</span><span class="sxs-lookup"><span data-stu-id="91d63-171">However, if you wish to specify, for example, some files to get published with your app, you can still use the known mechanisms in *csproj* for that (for example, the `<Content>` element).</span></span>

<span data-ttu-id="91d63-172">`<EnableDefaultCompileItems>` zakáže pouze `Compile` globy, ale nemá vliv na jiné globy, jako je například implicitní `None` glob, které platí i pro \*položky. cs.</span><span class="sxs-lookup"><span data-stu-id="91d63-172">`<EnableDefaultCompileItems>` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob, which also applies to \*.cs items.</span></span> <span data-ttu-id="91d63-173">Z tohoto důvodu **Průzkumník řešení** nadále zobrazovat \*. cs položky jako součást projektu, včetně položek `None`.</span><span class="sxs-lookup"><span data-stu-id="91d63-173">Because of that, **Solution Explorer** will continue show \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="91d63-174">Podobným způsobem můžete nastavit `<EnableDefaultNoneItems>` na hodnotu false, chcete-li zakázat implicitní `None` glob, například:</span><span class="sxs-lookup"><span data-stu-id="91d63-174">In a similar way, you can set `<EnableDefaultNoneItems>` to false to disable the implicit `None` glob, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

<span data-ttu-id="91d63-175">Chcete-li zakázat **všechny implicitní globy**, můžete nastavit vlastnost `<EnableDefaultItems>` tak, aby `false` jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="91d63-175">To disable **all implicit globs**, you can set the `<EnableDefaultItems>` property to `false` as in the following example:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a><span data-ttu-id="91d63-176">Jak zobrazit celý projekt, když ho MSBuild uvidí</span><span class="sxs-lookup"><span data-stu-id="91d63-176">How to see the whole project as MSBuild sees it</span></span>

<span data-ttu-id="91d63-177">I když tyto změny csproj značně zjednodušují soubory projektu, je možné, že budete chtít zobrazit plně rozbalený projekt jako nástroj MSBuild, jakmile bude sada SDK a její cíle zahrnuté.</span><span class="sxs-lookup"><span data-stu-id="91d63-177">While those csproj changes greatly simplify project files, you might want to see the fully expanded project as MSBuild sees it once the SDK and its targets are included.</span></span> <span data-ttu-id="91d63-178">Projekt předzpracování pomocí [`/pp`ového přepínače](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) příkazu [`dotnet msbuild`](dotnet-msbuild.md) , který ukazuje, které soubory jsou importovány, jejich zdroje a jejich příspěvky na sestavení bez skutečného sestavení projektu:</span><span class="sxs-lookup"><span data-stu-id="91d63-178">Preprocess the project with [the `/pp` switch](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) of the [`dotnet msbuild`](dotnet-msbuild.md) command, which shows which files are imported, their sources, and their contributions to the build without actually building the project:</span></span>

`dotnet msbuild -pp:fullproject.xml`

<span data-ttu-id="91d63-179">Pokud má projekt více cílových rozhraní, výsledky příkazu by měly být zaměřené jenom na jeden z nich zadáním jako vlastnost MSBuild:</span><span class="sxs-lookup"><span data-stu-id="91d63-179">If the project has multiple target frameworks, the results of the command should be focused on only one of them by specifying it as an MSBuild property:</span></span>

`dotnet msbuild -p:TargetFramework=netcoreapp2.0 -pp:fullproject.xml`

## <a name="additions"></a><span data-ttu-id="91d63-180">Rozšíření</span><span class="sxs-lookup"><span data-stu-id="91d63-180">Additions</span></span>

### <a name="sdk-attribute"></a><span data-ttu-id="91d63-181">Atribut sady SDK</span><span class="sxs-lookup"><span data-stu-id="91d63-181">Sdk attribute</span></span>

<span data-ttu-id="91d63-182">Kořenový `<Project>` element souboru *. csproj* má nový atribut nazvaný `Sdk`.</span><span class="sxs-lookup"><span data-stu-id="91d63-182">The root `<Project>` element of the *.csproj* file has a new attribute called `Sdk`.</span></span> <span data-ttu-id="91d63-183">`Sdk` určuje, kterou sadu SDK bude projekt používat.</span><span class="sxs-lookup"><span data-stu-id="91d63-183">`Sdk` specifies which SDK will be used by the project.</span></span> <span data-ttu-id="91d63-184">Sada SDK, jak popisuje [dokument vrstvení](cli-msbuild-architecture.md) , je sada [úloh](/visualstudio/msbuild/msbuild-tasks) a [cílů](/visualstudio/msbuild/msbuild-targets) nástroje MSBuild, které mohou sestavovat kód .NET Core.</span><span class="sxs-lookup"><span data-stu-id="91d63-184">The SDK, as the [layering document](cli-msbuild-architecture.md) describes, is a set of MSBuild [tasks](/visualstudio/msbuild/msbuild-tasks) and [targets](/visualstudio/msbuild/msbuild-targets) that can build .NET Core code.</span></span> <span data-ttu-id="91d63-185">Pro .NET Core jsou k dispozici následující sady SDK:</span><span class="sxs-lookup"><span data-stu-id="91d63-185">The following SDKs are available for .NET Core:</span></span>

1. <span data-ttu-id="91d63-186">.NET Core SDK s ID `Microsoft.NET.Sdk`</span><span class="sxs-lookup"><span data-stu-id="91d63-186">The .NET Core SDK with the ID of `Microsoft.NET.Sdk`</span></span>
2. <span data-ttu-id="91d63-187">Sada Web SDK .NET Core s ID `Microsoft.NET.Sdk.Web`</span><span class="sxs-lookup"><span data-stu-id="91d63-187">The .NET Core web SDK with the ID of `Microsoft.NET.Sdk.Web`</span></span>
3. <span data-ttu-id="91d63-188">Sada SDK knihovny tříd .NET Core Razor s ID `Microsoft.NET.Sdk.Razor`</span><span class="sxs-lookup"><span data-stu-id="91d63-188">The .NET Core Razor Class Library SDK with the ID of `Microsoft.NET.Sdk.Razor`</span></span>
4. <span data-ttu-id="91d63-189">Služba pracovních procesů .NET Core s ID `Microsoft.NET.Sdk.Worker` (od .NET Core 3,0)</span><span class="sxs-lookup"><span data-stu-id="91d63-189">The .NET Core Worker Service with the ID of `Microsoft.NET.Sdk.Worker` (since .NET Core 3.0)</span></span>
5. <span data-ttu-id="91d63-190">WinForms rozhraní .NET Core a WPF s ID `Microsoft.NET.Sdk.WindowsDesktop` (od .NET Core 3,0)</span><span class="sxs-lookup"><span data-stu-id="91d63-190">The .NET Core WinForms and WPF with the ID of `Microsoft.NET.Sdk.WindowsDesktop` (since .NET Core 3.0)</span></span>

<span data-ttu-id="91d63-191">Aby bylo možné používat nástroje .NET Core a sestavovat kód, je nutné mít atribut `Sdk` nastaven na jedno z těchto identifikátorů `<Project>` elementu.</span><span class="sxs-lookup"><span data-stu-id="91d63-191">You need to have the `Sdk` attribute set to one of those IDs on the `<Project>` element in order to use the .NET Core tools and build your code.</span></span>

### <a name="packagereference"></a><span data-ttu-id="91d63-192">PackageReference</span><span class="sxs-lookup"><span data-stu-id="91d63-192">PackageReference</span></span>

<span data-ttu-id="91d63-193">Element `<PackageReference>` Item Určuje [závislost NuGet v projektu](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="91d63-193">A `<PackageReference>` item element specifies a [NuGet dependency in the project](/nuget/consume-packages/package-references-in-project-files).</span></span> <span data-ttu-id="91d63-194">Atribut `Include` Určuje ID balíčku.</span><span class="sxs-lookup"><span data-stu-id="91d63-194">The `Include` attribute specifies the package ID.</span></span>

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a><span data-ttu-id="91d63-195">Version</span><span class="sxs-lookup"><span data-stu-id="91d63-195">Version</span></span>

<span data-ttu-id="91d63-196">Atribut Required `Version` určuje verzi balíčku, který má být obnoven.</span><span class="sxs-lookup"><span data-stu-id="91d63-196">The required `Version` attribute specifies the version of the package to restore.</span></span> <span data-ttu-id="91d63-197">Atribut respektuje pravidla schématu [správy verzí NuGet](/nuget/reference/package-versioning#version-ranges-and-wildcards) .</span><span class="sxs-lookup"><span data-stu-id="91d63-197">The attribute respects the rules of the [NuGet versioning](/nuget/reference/package-versioning#version-ranges-and-wildcards) scheme.</span></span> <span data-ttu-id="91d63-198">Výchozí chování je přesné porovnávání verzí.</span><span class="sxs-lookup"><span data-stu-id="91d63-198">The default behavior is an exact version match.</span></span> <span data-ttu-id="91d63-199">Například zadání `Version="1.2.3"` je ekvivalentní `[1.2.3]` notace NuGet pro přesný balíček verze balíčku.</span><span class="sxs-lookup"><span data-stu-id="91d63-199">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

#### <a name="includeassets-excludeassets-and-privateassets"></a><span data-ttu-id="91d63-200">IncludeAssets, ExcludeAssets a PrivateAssets</span><span class="sxs-lookup"><span data-stu-id="91d63-200">IncludeAssets, ExcludeAssets, and PrivateAssets</span></span>

<span data-ttu-id="91d63-201">`IncludeAssets` atribut určuje, které prostředky patřící k balíčku určenému `<PackageReference>` by měly být spotřebovány.</span><span class="sxs-lookup"><span data-stu-id="91d63-201">`IncludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed.</span></span> <span data-ttu-id="91d63-202">Ve výchozím nastavení jsou zahrnuty všechny prostředky balíčku.</span><span class="sxs-lookup"><span data-stu-id="91d63-202">By default, all package assets are included.</span></span>

<span data-ttu-id="91d63-203">atribut `ExcludeAssets` určuje, které prostředky patřící k balíčku určenému `<PackageReference>` by neměly být spotřebovány.</span><span class="sxs-lookup"><span data-stu-id="91d63-203">`ExcludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should not be consumed.</span></span>

<span data-ttu-id="91d63-204">atribut `PrivateAssets` určuje, které prostředky patřící k balíčku určenému `<PackageReference>` by měly být spotřebovány, ale nikoli do dalšího projektu.</span><span class="sxs-lookup"><span data-stu-id="91d63-204">`PrivateAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed but not flow to the next project.</span></span> <span data-ttu-id="91d63-205">`Analyzers`, `Build` a `ContentFiles` assety jsou ve výchozím nastavení privátní, pokud tento atribut není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="91d63-205">The `Analyzers`, `Build` and `ContentFiles` assets are private by default when this attribute is not present.</span></span>

> [!NOTE]
> <span data-ttu-id="91d63-206">`PrivateAssets` je ekvivalentem elementu *Project. json*/*xproj* `SuppressParent`.</span><span class="sxs-lookup"><span data-stu-id="91d63-206">`PrivateAssets` is equivalent to the *project.json*/*xproj* `SuppressParent` element.</span></span>

<span data-ttu-id="91d63-207">Tyto atributy mohou obsahovat jednu nebo více následujících položek oddělených středníkem `;` znak, pokud je uvedena více než jedna z těchto hodnot:</span><span class="sxs-lookup"><span data-stu-id="91d63-207">These attributes can contain one or more of the following items, separated by the semicolon `;` character if more than one is listed:</span></span>

- <span data-ttu-id="91d63-208">`Compile` – obsah složky *lib* je k dispozici pro zkompilování.</span><span class="sxs-lookup"><span data-stu-id="91d63-208">`Compile` – the contents of the *lib* folder are available to compile against.</span></span>
- <span data-ttu-id="91d63-209">`Runtime` – obsah *běhové* složky se distribuuje.</span><span class="sxs-lookup"><span data-stu-id="91d63-209">`Runtime` – the contents of the *runtime* folder are distributed.</span></span>
- <span data-ttu-id="91d63-210">`ContentFiles` – používá se obsah složky *contentFiles* .</span><span class="sxs-lookup"><span data-stu-id="91d63-210">`ContentFiles` – the contents of the *contentfiles* folder are used.</span></span>
- <span data-ttu-id="91d63-211">`Build` – používají se props/targets ve složce *Build* .</span><span class="sxs-lookup"><span data-stu-id="91d63-211">`Build` – the props/targets in the *build* folder are used.</span></span>
- <span data-ttu-id="91d63-212">`Native` – obsah z nativních assetů se zkopíruje do *výstupní* složky pro modul runtime.</span><span class="sxs-lookup"><span data-stu-id="91d63-212">`Native` – the contents from native assets are copied to the *output* folder for runtime.</span></span>
- <span data-ttu-id="91d63-213">`Analyzers` – používají se analyzátory.</span><span class="sxs-lookup"><span data-stu-id="91d63-213">`Analyzers` – the analyzers are used.</span></span>

<span data-ttu-id="91d63-214">Atribut může případně obsahovat:</span><span class="sxs-lookup"><span data-stu-id="91d63-214">Alternatively, the attribute can contain:</span></span>

- <span data-ttu-id="91d63-215">`None` – žádný z prostředků se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="91d63-215">`None` – none of the assets are used.</span></span>
- <span data-ttu-id="91d63-216">`All` – používají se všechny prostředky.</span><span class="sxs-lookup"><span data-stu-id="91d63-216">`All` – all assets are used.</span></span>

### <a name="dotnetclitoolreference"></a><span data-ttu-id="91d63-217">DotNetCliToolReference</span><span class="sxs-lookup"><span data-stu-id="91d63-217">DotNetCliToolReference</span></span>

<span data-ttu-id="91d63-218">Element `<DotNetCliToolReference>` Item Určuje nástroj CLI, který uživatel chce obnovit v kontextu projektu.</span><span class="sxs-lookup"><span data-stu-id="91d63-218">A `<DotNetCliToolReference>` item element specifies the CLI tool that the user wants to restore in the context of the project.</span></span> <span data-ttu-id="91d63-219">Je náhradou pro `tools` uzel v *Project. JSON*.</span><span class="sxs-lookup"><span data-stu-id="91d63-219">It's a replacement for the `tools` node in *project.json*.</span></span>

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

<span data-ttu-id="91d63-220">Všimněte si, že `DotNetCliToolReference` se [teď už nepoužívá](https://github.com/dotnet/announcements/issues/107) , a to ve prospěch [místních nástrojů .NET Core](https://aka.ms/local-tools).</span><span class="sxs-lookup"><span data-stu-id="91d63-220">Note that `DotNetCliToolReference` is [now deprecated](https://github.com/dotnet/announcements/issues/107) in favor of [.NET Core Local Tools](https://aka.ms/local-tools).</span></span>

#### <a name="version"></a><span data-ttu-id="91d63-221">Version</span><span class="sxs-lookup"><span data-stu-id="91d63-221">Version</span></span>

<span data-ttu-id="91d63-222">`Version` určuje verzi balíčku, který má být obnoven.</span><span class="sxs-lookup"><span data-stu-id="91d63-222">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="91d63-223">Atribut respektuje pravidla schématu [správy verzí NuGet](/nuget/create-packages/dependency-versions#version-ranges) .</span><span class="sxs-lookup"><span data-stu-id="91d63-223">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="91d63-224">Výchozí chování je přesné porovnávání verzí.</span><span class="sxs-lookup"><span data-stu-id="91d63-224">The default behavior is an exact version match.</span></span> <span data-ttu-id="91d63-225">Například zadání `Version="1.2.3"` je ekvivalentní `[1.2.3]` notace NuGet pro přesný balíček verze balíčku.</span><span class="sxs-lookup"><span data-stu-id="91d63-225">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

### <a name="runtimeidentifiers"></a><span data-ttu-id="91d63-226">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="91d63-226">RuntimeIdentifiers</span></span>

<span data-ttu-id="91d63-227">Element vlastnosti `<RuntimeIdentifiers>` umožňuje zadat seznam [identifikátorů modulu runtime (identifikátorů RID)](../rid-catalog.md) pro daný projekt oddělený středníkem.</span><span class="sxs-lookup"><span data-stu-id="91d63-227">The `<RuntimeIdentifiers>` property element lets you specify a semicolon-delimited list of [Runtime Identifiers (RIDs)](../rid-catalog.md) for the project.</span></span>
<span data-ttu-id="91d63-228">Identifikátorů RID umožňuje publikování samostatně obsažených nasazení.</span><span class="sxs-lookup"><span data-stu-id="91d63-228">RIDs enable publishing self-contained deployments.</span></span>

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a><span data-ttu-id="91d63-229">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="91d63-229">RuntimeIdentifier</span></span>

<span data-ttu-id="91d63-230">Prvek vlastnosti `<RuntimeIdentifier>` umožňuje zadat pouze jeden [identifikátor modulu runtime (RID)](../rid-catalog.md) pro projekt.</span><span class="sxs-lookup"><span data-stu-id="91d63-230">The `<RuntimeIdentifier>` property element allows you to specify only one [Runtime Identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="91d63-231">Identifikátor RID umožňuje publikování samostatně zahrnutého nasazení.</span><span class="sxs-lookup"><span data-stu-id="91d63-231">The RID enables publishing a self-contained deployment.</span></span>

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

<span data-ttu-id="91d63-232">Pokud potřebujete publikovat více modulů runtime, použijte místo toho `<RuntimeIdentifiers>` (plural).</span><span class="sxs-lookup"><span data-stu-id="91d63-232">Use `<RuntimeIdentifiers>` (plural) instead if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="91d63-233">`<RuntimeIdentifier>` můžou poskytovat rychlejší buildy, když je potřeba jenom jeden modul runtime.</span><span class="sxs-lookup"><span data-stu-id="91d63-233">`<RuntimeIdentifier>` can provide faster builds when only a single runtime is required.</span></span>

### <a name="packagetargetfallback"></a><span data-ttu-id="91d63-234">PackageTargetFallback</span><span class="sxs-lookup"><span data-stu-id="91d63-234">PackageTargetFallback</span></span>

<span data-ttu-id="91d63-235">Prvek vlastnosti `<PackageTargetFallback>` umožňuje zadat sadu kompatibilních cílů, které se mají použít při obnovování balíčků.</span><span class="sxs-lookup"><span data-stu-id="91d63-235">The `<PackageTargetFallback>` property element allows you to specify a set of compatible targets to be used when restoring packages.</span></span> <span data-ttu-id="91d63-236">Je navržena tak, aby povolovala balíčky, které používají dotnet [TxM (Target x moniker)](/nuget/schema/target-frameworks) pro práci s balíčky, které nedeklarují dotnet TxM.</span><span class="sxs-lookup"><span data-stu-id="91d63-236">It's designed to allow packages that use the dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) to operate with packages that don't declare a dotnet TxM.</span></span> <span data-ttu-id="91d63-237">Pokud váš projekt používá TxM dotnet, pak všechny balíčky, na kterých závisí, musí mít také hodnotu dotnet TxM, pokud nepřidáte `<PackageTargetFallback>` do projektu, aby bylo umožněno kompatibilitu platforem mimo dotnet s dotnet.</span><span class="sxs-lookup"><span data-stu-id="91d63-237">If your project uses the dotnet TxM, then all the packages it depends on must also have a dotnet TxM, unless you add the `<PackageTargetFallback>` to your project in order to allow non-dotnet platforms to be compatible with dotnet.</span></span>

<span data-ttu-id="91d63-238">Následující příklad poskytuje záložní hodnoty pro všechny cíle v projektu:</span><span class="sxs-lookup"><span data-stu-id="91d63-238">The following example provides the fallbacks for all targets in your project:</span></span>

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

<span data-ttu-id="91d63-239">Následující příklad určuje pouze zálohy pro cíl `netcoreapp2.1`:</span><span class="sxs-lookup"><span data-stu-id="91d63-239">The following example specifies the fallbacks only for the `netcoreapp2.1` target:</span></span>

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp2.1'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="build-events"></a><span data-ttu-id="91d63-240">Události sestavení</span><span class="sxs-lookup"><span data-stu-id="91d63-240">Build events</span></span>

<span data-ttu-id="91d63-241">Způsob, jakým se změnily události před sestavením a po sestavení, jsou uvedeny v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="91d63-241">The way that pre-build and post-build events are specified in the project file has changed.</span></span> <span data-ttu-id="91d63-242">Vlastnosti PreBuildEvent a PostBuildEvent nejsou doporučovány ve formátu projektu ve stylu sady SDK, protože makra jako $ (ProjectDir) nejsou vyřešena.</span><span class="sxs-lookup"><span data-stu-id="91d63-242">The properties PreBuildEvent and PostBuildEvent are not recommended in the SDK-style project format, because macros such as $(ProjectDir) are not resolved.</span></span> <span data-ttu-id="91d63-243">Například následující kód již není podporován:</span><span class="sxs-lookup"><span data-stu-id="91d63-243">For example, the following code is no longer supported:</span></span>

```xml
<PropertyGroup>
    <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)" />
</PropertyGroup>
```

<span data-ttu-id="91d63-244">V projektech se styly sady SDK použijte cíl MSBuild s názvem `PreBuild` nebo `PostBuild` a nastavte vlastnost `BeforeTargets` pro `PreBuild` nebo vlastnost `AfterTargets` pro `PostBuild`.</span><span class="sxs-lookup"><span data-stu-id="91d63-244">In SDK-style projects, use an MSBuild target named `PreBuild` or `PostBuild` and set the `BeforeTargets` property for `PreBuild` or the `AfterTargets` property for `PostBuild`.</span></span> <span data-ttu-id="91d63-245">Pro předchozí příklad použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="91d63-245">For the preceding example, use the following code:</span></span>

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>

<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
><span data-ttu-id="91d63-246">Můžete použít libovolný název pro cíle nástroje MSBuild, ale rozhraní IDE sady Visual Studio rozpozná `PreBuild` a `PostBuild` cíle, proto doporučujeme použít tyto názvy, abyste mohli upravovat příkazy v integrovaném vývojovém prostředí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="91d63-246">You can use any name for the MSBuild targets, but the Visual Studio IDE recognizes `PreBuild` and `PostBuild` targets, so we recommend using those names so that you can edit the commands in the Visual Studio IDE.</span></span> 

## <a name="nuget-metadata-properties"></a><span data-ttu-id="91d63-247">Vlastnosti metadat NuGet</span><span class="sxs-lookup"><span data-stu-id="91d63-247">NuGet metadata properties</span></span>

<span data-ttu-id="91d63-248">Při přechodu na MSBuild jsme přesunuli vstupní metadata, která se používají při balení balíčku NuGet z *Project. JSON* do souborů *. csproj* .</span><span class="sxs-lookup"><span data-stu-id="91d63-248">With the move to MSBuild, we have moved the input metadata that is used when packing a NuGet package from *project.json* to *.csproj* files.</span></span> <span data-ttu-id="91d63-249">Vstupy jsou vlastnosti nástroje MSBuild, takže musí jít do skupiny `<PropertyGroup>`.</span><span class="sxs-lookup"><span data-stu-id="91d63-249">The inputs are MSBuild properties so they have to go within a `<PropertyGroup>` group.</span></span> <span data-ttu-id="91d63-250">Následuje seznam vlastností, které se používají jako vstupy do procesu balení při použití příkazu `dotnet pack` nebo `Pack`ho cíle MSBuild, který je součástí sady SDK:</span><span class="sxs-lookup"><span data-stu-id="91d63-250">The following is the list of properties that are used as inputs to the packing process when using the `dotnet pack` command or the `Pack` MSBuild target that is part of the SDK:</span></span>

### <a name="ispackable"></a><span data-ttu-id="91d63-251">Ispackable nastavenou</span><span class="sxs-lookup"><span data-stu-id="91d63-251">IsPackable</span></span>

<span data-ttu-id="91d63-252">Logická hodnota, která určuje, zda lze projekt zabalit.</span><span class="sxs-lookup"><span data-stu-id="91d63-252">A Boolean value that specifies whether the project can be packed.</span></span> <span data-ttu-id="91d63-253">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="91d63-253">The default value is `true`.</span></span>

### <a name="packageversion"></a><span data-ttu-id="91d63-254">PackageVersion</span><span class="sxs-lookup"><span data-stu-id="91d63-254">PackageVersion</span></span>

<span data-ttu-id="91d63-255">Určuje verzi, kterou výsledný balíček bude mít.</span><span class="sxs-lookup"><span data-stu-id="91d63-255">Specifies the version that the resulting package will have.</span></span> <span data-ttu-id="91d63-256">Akceptuje všechny formy řetězce verze NuGet.</span><span class="sxs-lookup"><span data-stu-id="91d63-256">Accepts all forms of NuGet version string.</span></span> <span data-ttu-id="91d63-257">Výchozí hodnota je hodnota `$(Version)`, to znamená vlastnost `Version` v projektu.</span><span class="sxs-lookup"><span data-stu-id="91d63-257">Default is the value of `$(Version)`, that is, of the property `Version` in the project.</span></span>

### <a name="packageid"></a><span data-ttu-id="91d63-258">PackageId</span><span class="sxs-lookup"><span data-stu-id="91d63-258">PackageId</span></span>

<span data-ttu-id="91d63-259">Určuje název výsledného balíčku.</span><span class="sxs-lookup"><span data-stu-id="91d63-259">Specifies the name for the resulting package.</span></span> <span data-ttu-id="91d63-260">Pokud tento parametr nezadáte, použije operace `pack` ve výchozím nastavení jako název balíčku název `AssemblyName` nebo adresáře.</span><span class="sxs-lookup"><span data-stu-id="91d63-260">If not specified, the `pack` operation will default to using the `AssemblyName` or directory name as the name of the package.</span></span>

### <a name="title"></a><span data-ttu-id="91d63-261">Název</span><span class="sxs-lookup"><span data-stu-id="91d63-261">Title</span></span>

<span data-ttu-id="91d63-262">Popisný název balíčku, který se obvykle používá v uživatelském rozhraní, se zobrazuje jako v nuget.org a správce balíčků v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="91d63-262">A human-friendly title of the package, typically used in UI displays as on nuget.org and the Package Manager in Visual Studio.</span></span> <span data-ttu-id="91d63-263">Pokud není zadaný, použije se místo toho ID balíčku.</span><span class="sxs-lookup"><span data-stu-id="91d63-263">If not specified, the package ID is used instead.</span></span>

### <a name="authors"></a><span data-ttu-id="91d63-264">Autoři</span><span class="sxs-lookup"><span data-stu-id="91d63-264">Authors</span></span>

<span data-ttu-id="91d63-265">Středníkem oddělený seznam autorů balíčků, které odpovídají názvům profilů v nuget.org. Ty se zobrazí v galerii NuGet na nuget.org a používají se pro balíčky křížového odkazu stejnými autory.</span><span class="sxs-lookup"><span data-stu-id="91d63-265">A semicolon-separated list of packages authors, matching the profile names on nuget.org. These are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span>

### <a name="packagedescription"></a><span data-ttu-id="91d63-266">PackageDescription</span><span class="sxs-lookup"><span data-stu-id="91d63-266">PackageDescription</span></span>

<span data-ttu-id="91d63-267">Dlouhý popis balíčku pro zobrazení uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="91d63-267">A long description of the package for UI display.</span></span>

### <a name="description"></a><span data-ttu-id="91d63-268">Popis</span><span class="sxs-lookup"><span data-stu-id="91d63-268">Description</span></span>

<span data-ttu-id="91d63-269">Dlouhý popis pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="91d63-269">A long description for the assembly.</span></span> <span data-ttu-id="91d63-270">Pokud není zadán `PackageDescription`, tato vlastnost se používá také jako Popis balíčku.</span><span class="sxs-lookup"><span data-stu-id="91d63-270">If `PackageDescription` is not specified, then this property is also used as the description of the package.</span></span>

### <a name="copyright"></a><span data-ttu-id="91d63-271">Copyright</span><span class="sxs-lookup"><span data-stu-id="91d63-271">Copyright</span></span>

<span data-ttu-id="91d63-272">Podrobnosti o autorských právech pro balíček.</span><span class="sxs-lookup"><span data-stu-id="91d63-272">Copyright details for the package.</span></span>

### <a name="packagerequirelicenseacceptance"></a><span data-ttu-id="91d63-273">PackageRequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="91d63-273">PackageRequireLicenseAcceptance</span></span>

<span data-ttu-id="91d63-274">Logická hodnota, která určuje, zda klient musí požádat spotřebitele o přijetí licence k balíčku před instalací balíčku.</span><span class="sxs-lookup"><span data-stu-id="91d63-274">A Boolean value that specifies whether the client must prompt the consumer to accept the package license before installing the package.</span></span> <span data-ttu-id="91d63-275">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="91d63-275">The default is `false`.</span></span>

### <a name="packagelicenseexpression"></a><span data-ttu-id="91d63-276">PackageLicenseExpression</span><span class="sxs-lookup"><span data-stu-id="91d63-276">PackageLicenseExpression</span></span>

<span data-ttu-id="91d63-277">Identifikátor nebo výraz [licence SPDX](https://spdx.org/licenses/)</span><span class="sxs-lookup"><span data-stu-id="91d63-277">An [SPDX license identifier](https://spdx.org/licenses/) or expression.</span></span> <span data-ttu-id="91d63-278">Například `Apache-2.0`.</span><span class="sxs-lookup"><span data-stu-id="91d63-278">For example, `Apache-2.0`.</span></span>

<span data-ttu-id="91d63-279">Tady je úplný seznam [identifikátorů licencí SPDX](https://spdx.org/licenses/).</span><span class="sxs-lookup"><span data-stu-id="91d63-279">Here is the complete list of [SPDX license identifiers](https://spdx.org/licenses/).</span></span> <span data-ttu-id="91d63-280">NuGet.org přijímá při použití výrazu typu licence pouze licence OSI nebo FSF schválené.</span><span class="sxs-lookup"><span data-stu-id="91d63-280">NuGet.org accepts only OSI or FSF approved licenses when using license type expression.</span></span>

<span data-ttu-id="91d63-281">Přesná Syntaxe výrazů s licencí je popsána níže v tématu [ABNF](https://tools.ietf.org/html/rfc5234).</span><span class="sxs-lookup"><span data-stu-id="91d63-281">The exact syntax of the license expressions is described below in [ABNF](https://tools.ietf.org/html/rfc5234).</span></span>

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
> <span data-ttu-id="91d63-282">V jednom okamžiku může být zadána pouze jedna z `PackageLicenseExpression`, `PackageLicenseFile` a `PackageLicenseUrl`.</span><span class="sxs-lookup"><span data-stu-id="91d63-282">Only one of `PackageLicenseExpression`, `PackageLicenseFile` and `PackageLicenseUrl` can be specified at a time.</span></span>

### <a name="packagelicensefile"></a><span data-ttu-id="91d63-283">PackageLicenseFile</span><span class="sxs-lookup"><span data-stu-id="91d63-283">PackageLicenseFile</span></span>

<span data-ttu-id="91d63-284">Cesta k souboru s licencí v rámci balíčku, pokud používáte licenci, ke které se nepřiřadil identifikátor SPDX, nebo se jedná o vlastní licenci (jinak `PackageLicenseExpression` upřednostňovaná)</span><span class="sxs-lookup"><span data-stu-id="91d63-284">Path to a license file within the package if you are using a license that hasn’t been assigned an SPDX identifier, or it is a custom license (Otherwise `PackageLicenseExpression` is preferred)</span></span>

<span data-ttu-id="91d63-285">Nahrazuje `PackageLicenseUrl`, nejde kombinovat s `PackageLicenseExpression` a vyžaduje Visual Studio 15.9.4, .NET SDK 2.1.502 nebo 2.2.101 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="91d63-285">Replaces `PackageLicenseUrl`, can't be combined with `PackageLicenseExpression` and requires Visual Studio 15.9.4, .NET SDK 2.1.502 or 2.2.101, or newer.</span></span>

<span data-ttu-id="91d63-286">Je potřeba zajistit, aby byl soubor s licencí zabalený tak, že ho do projektu přidáte explicitně, jako příklad použití:</span><span class="sxs-lookup"><span data-stu-id="91d63-286">You will need to ensure the license file is packed by adding it explicitly to the project, example usage:</span></span>

```xml
<PropertyGroup>
  <PackageLicenseFile>LICENSE.txt</PackageLicenseFile>
</PropertyGroup>
<ItemGroup>
  <None Include="licenses\LICENSE.txt" Pack="true" PackagePath="$(PackageLicenseFile)"/>
</ItemGroup>
```

### <a name="packagelicenseurl"></a><span data-ttu-id="91d63-287">PackageLicenseUrl</span><span class="sxs-lookup"><span data-stu-id="91d63-287">PackageLicenseUrl</span></span>

<span data-ttu-id="91d63-288">Adresa URL licence, která se vztahuje na balíček.</span><span class="sxs-lookup"><span data-stu-id="91d63-288">A URL to the license that is applicable to the package.</span></span> <span data-ttu-id="91d63-289">(_nepoužívá se od verze Visual Studio 15.9.4, .NET SDK 2.1.502 a 2.2.101_)</span><span class="sxs-lookup"><span data-stu-id="91d63-289">(_deprecated since Visual Studio 15.9.4, .NET SDK 2.1.502 and 2.2.101_)</span></span>

### <a name="packageiconurl"></a><span data-ttu-id="91d63-290">PackageIconUrl</span><span class="sxs-lookup"><span data-stu-id="91d63-290">PackageIconUrl</span></span>

<span data-ttu-id="91d63-291">Adresa URL obrázku 64 × 64 s průhledným pozadím, který se má použít jako ikona balíčku v zobrazení uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="91d63-291">A URL for a 64x64 image with transparent background to use as the icon for the package in UI display.</span></span>

### <a name="packagereleasenotes"></a><span data-ttu-id="91d63-292">PackageReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="91d63-292">PackageReleaseNotes</span></span>

<span data-ttu-id="91d63-293">Poznámky k verzi balíčku</span><span class="sxs-lookup"><span data-stu-id="91d63-293">Release notes for the package.</span></span>

### <a name="packagetags"></a><span data-ttu-id="91d63-294">PackageTags</span><span class="sxs-lookup"><span data-stu-id="91d63-294">PackageTags</span></span>

<span data-ttu-id="91d63-295">Seznam značek oddělených středníkem, který určuje balíček.</span><span class="sxs-lookup"><span data-stu-id="91d63-295">A semicolon-delimited list of tags that designates the package.</span></span>

### <a name="packageoutputpath"></a><span data-ttu-id="91d63-296">PackageOutputPath</span><span class="sxs-lookup"><span data-stu-id="91d63-296">PackageOutputPath</span></span>

<span data-ttu-id="91d63-297">Určuje výstupní cestu, do které bude zahozen zabalený balíček.</span><span class="sxs-lookup"><span data-stu-id="91d63-297">Determines the output path in which the packed package will be dropped.</span></span> <span data-ttu-id="91d63-298">Výchozí hodnota je `$(OutputPath)`.</span><span class="sxs-lookup"><span data-stu-id="91d63-298">Default is `$(OutputPath)`.</span></span>

### <a name="includesymbols"></a><span data-ttu-id="91d63-299">IncludeSymbols</span><span class="sxs-lookup"><span data-stu-id="91d63-299">IncludeSymbols</span></span>
<span data-ttu-id="91d63-300">Tato logická hodnota označuje, zda má balíček při zabalení projektu vytvořit další balíček symbolů.</span><span class="sxs-lookup"><span data-stu-id="91d63-300">This Boolean value indicates whether the package should create an additional symbols package when the project is packed.</span></span> <span data-ttu-id="91d63-301">Formát balíčku symbolů je řízen vlastností `SymbolPackageFormat`.</span><span class="sxs-lookup"><span data-stu-id="91d63-301">The symbols package's format is controlled by the `SymbolPackageFormat` property.</span></span>

### <a name="symbolpackageformat"></a><span data-ttu-id="91d63-302">SymbolPackageFormat</span><span class="sxs-lookup"><span data-stu-id="91d63-302">SymbolPackageFormat</span></span>
<span data-ttu-id="91d63-303">Určuje formát balíčku symbolů.</span><span class="sxs-lookup"><span data-stu-id="91d63-303">Specifies the format of the symbols package.</span></span> <span data-ttu-id="91d63-304">Pokud "Symbols. nupkg", bude balíček starších symbolů vytvořen s příponou *. Symbols. nupkg* , která obsahuje soubory PDB, knihovny DLL a další výstupní soubory.</span><span class="sxs-lookup"><span data-stu-id="91d63-304">If "symbols.nupkg", a legacy symbols package will be created with a *.symbols.nupkg* extension containing PDBs, DLLs, and other output files.</span></span> <span data-ttu-id="91d63-305">Pokud bude "snupkg", vytvoří se balíček symbolů snupkg obsahující přenosné soubory PDB.</span><span class="sxs-lookup"><span data-stu-id="91d63-305">If "snupkg", a snupkg symbol package will be created containing the portable PDBs.</span></span> <span data-ttu-id="91d63-306">Výchozí hodnota je "Symbols. nupkg".</span><span class="sxs-lookup"><span data-stu-id="91d63-306">Default is "symbols.nupkg".</span></span>

### <a name="includesource"></a><span data-ttu-id="91d63-307">IncludeSource</span><span class="sxs-lookup"><span data-stu-id="91d63-307">IncludeSource</span></span>

<span data-ttu-id="91d63-308">Tato logická hodnota označuje, zda by měl proces balíčku vytvořit zdrojový balíček.</span><span class="sxs-lookup"><span data-stu-id="91d63-308">This Boolean value indicates whether the pack process should create a source package.</span></span> <span data-ttu-id="91d63-309">Zdrojový balíček obsahuje zdrojový kód knihovny i soubory PDB.</span><span class="sxs-lookup"><span data-stu-id="91d63-309">The source package contains the library's source code as well as PDB files.</span></span> <span data-ttu-id="91d63-310">Zdrojové soubory jsou umístěny pod `src/ProjectName` adresář ve výsledném souboru balíčku.</span><span class="sxs-lookup"><span data-stu-id="91d63-310">Source files are put under the `src/ProjectName` directory in the resulting package file.</span></span>

### <a name="istool"></a><span data-ttu-id="91d63-311">Nástroj</span><span class="sxs-lookup"><span data-stu-id="91d63-311">IsTool</span></span>

<span data-ttu-id="91d63-312">Určuje, zda jsou všechny výstupní soubory zkopírovány do složky *Tools* namísto složky *lib* .</span><span class="sxs-lookup"><span data-stu-id="91d63-312">Specifies whether all output files are copied to the *tools* folder instead of the *lib* folder.</span></span> <span data-ttu-id="91d63-313">To se liší od `DotNetCliTool`, která je určena nastavením `PackageType` v souboru *. csproj* .</span><span class="sxs-lookup"><span data-stu-id="91d63-313">This is different from a `DotNetCliTool`, which is specified by setting the `PackageType` in the *.csproj* file.</span></span>

### <a name="repositoryurl"></a><span data-ttu-id="91d63-314">RepositoryUrl</span><span class="sxs-lookup"><span data-stu-id="91d63-314">RepositoryUrl</span></span>

<span data-ttu-id="91d63-315">Určuje adresu URL úložiště, ve kterém se nachází zdrojový kód balíčku, nebo ze kterého se vytváří.</span><span class="sxs-lookup"><span data-stu-id="91d63-315">Specifies the URL for the repository where the source code for the package resides and/or from which it's being built.</span></span>

### <a name="repositorytype"></a><span data-ttu-id="91d63-316">RepositoryType</span><span class="sxs-lookup"><span data-stu-id="91d63-316">RepositoryType</span></span>

<span data-ttu-id="91d63-317">Určuje typ úložiště.</span><span class="sxs-lookup"><span data-stu-id="91d63-317">Specifies the type of the repository.</span></span> <span data-ttu-id="91d63-318">Výchozí hodnota je "git".</span><span class="sxs-lookup"><span data-stu-id="91d63-318">Default is "git".</span></span>

### <a name="repositorybranch"></a><span data-ttu-id="91d63-319">RepositoryBranch</span><span class="sxs-lookup"><span data-stu-id="91d63-319">RepositoryBranch</span></span>
<span data-ttu-id="91d63-320">Určuje název zdrojové větve v úložišti.</span><span class="sxs-lookup"><span data-stu-id="91d63-320">Specifies the name of the source branch in the repository.</span></span> <span data-ttu-id="91d63-321">Když je projekt zabalen do balíčku NuGet, přidá se do metadat balíčku.</span><span class="sxs-lookup"><span data-stu-id="91d63-321">When the project is packaged in a NuGet package, it's added to the package metadata.</span></span>

### <a name="repositorycommit"></a><span data-ttu-id="91d63-322">RepositoryCommit</span><span class="sxs-lookup"><span data-stu-id="91d63-322">RepositoryCommit</span></span>
<span data-ttu-id="91d63-323">Volitelné potvrzení změn úložiště nebo sada změn, které označují, na který zdroj byl balíček vytvořen.</span><span class="sxs-lookup"><span data-stu-id="91d63-323">Optional repository commit or changeset to indicate which source the package was built against.</span></span> <span data-ttu-id="91d63-324">pro zahrnutí této vlastnosti je také nutné zadat `RepositoryUrl`.</span><span class="sxs-lookup"><span data-stu-id="91d63-324">`RepositoryUrl` must also be specified for this property to be included.</span></span> <span data-ttu-id="91d63-325">Když je projekt zabalen v balíčku NuGet, toto potvrzení nebo sada změn se přidá do metadat balíčku.</span><span class="sxs-lookup"><span data-stu-id="91d63-325">When the project is packaged in a NuGet package, this commit or changeset is added to the package metadata.</span></span>

### <a name="nopackageanalysis"></a><span data-ttu-id="91d63-326">NoPackageAnalysis</span><span class="sxs-lookup"><span data-stu-id="91d63-326">NoPackageAnalysis</span></span>

<span data-ttu-id="91d63-327">Určuje, že sada by neměla po sestavení balíčku spustit analýzu balíčku.</span><span class="sxs-lookup"><span data-stu-id="91d63-327">Specifies that pack should not run package analysis after building the package.</span></span>

### <a name="minclientversion"></a><span data-ttu-id="91d63-328">MinClientVersion</span><span class="sxs-lookup"><span data-stu-id="91d63-328">MinClientVersion</span></span>

<span data-ttu-id="91d63-329">Určuje minimální verzi klienta NuGet, která může nainstalovat tento balíček, který vynutila NuGet. exe a správce balíčků sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="91d63-329">Specifies the minimum version of the NuGet client that can install this package, enforced by nuget.exe and the Visual Studio Package Manager.</span></span>

### <a name="includebuildoutput"></a><span data-ttu-id="91d63-330">IncludeBuildOutput</span><span class="sxs-lookup"><span data-stu-id="91d63-330">IncludeBuildOutput</span></span>

<span data-ttu-id="91d63-331">Tato logická hodnota určuje, zda mají být výstupní sestavení sestavení zabalena do souboru *. nupkg* nebo ne.</span><span class="sxs-lookup"><span data-stu-id="91d63-331">This Boolean value specifies whether the build output assemblies should be packed into the *.nupkg* file or not.</span></span>

### <a name="includecontentinpack"></a><span data-ttu-id="91d63-332">IncludeContentInPack</span><span class="sxs-lookup"><span data-stu-id="91d63-332">IncludeContentInPack</span></span>

<span data-ttu-id="91d63-333">Tato logická hodnota určuje, zda budou všechny položky, které mají typ `Content`, zahrnuty do výsledného balíčku automaticky.</span><span class="sxs-lookup"><span data-stu-id="91d63-333">This Boolean value specifies whether any items that have a type of `Content` will be included in the resulting package automatically.</span></span> <span data-ttu-id="91d63-334">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="91d63-334">The default is `true`.</span></span>

### <a name="buildoutputtargetfolder"></a><span data-ttu-id="91d63-335">BuildOutputTargetFolder</span><span class="sxs-lookup"><span data-stu-id="91d63-335">BuildOutputTargetFolder</span></span>

<span data-ttu-id="91d63-336">Určuje složku, kam se mají umístit výstupní sestavení.</span><span class="sxs-lookup"><span data-stu-id="91d63-336">Specifies the folder where to place the output assemblies.</span></span> <span data-ttu-id="91d63-337">Výstupní sestavení (a další výstupní soubory) se zkopírují do příslušných složek rozhraní.</span><span class="sxs-lookup"><span data-stu-id="91d63-337">The output assemblies (and other output files) are copied into their respective framework folders.</span></span>

### <a name="contenttargetfolders"></a><span data-ttu-id="91d63-338">ContentTargetFolders</span><span class="sxs-lookup"><span data-stu-id="91d63-338">ContentTargetFolders</span></span>

<span data-ttu-id="91d63-339">Tato vlastnost určuje výchozí umístění, ve kterém mají všechny soubory obsahu jít, pokud pro ně není `PackagePath` určena.</span><span class="sxs-lookup"><span data-stu-id="91d63-339">This property specifies the default location of where all the content files should go if `PackagePath` is not specified for them.</span></span> <span data-ttu-id="91d63-340">Výchozí hodnota je Content; contentFiles.</span><span class="sxs-lookup"><span data-stu-id="91d63-340">The default value is "content;contentFiles".</span></span>

### <a name="nuspecfile"></a><span data-ttu-id="91d63-341">NuspecFile</span><span class="sxs-lookup"><span data-stu-id="91d63-341">NuspecFile</span></span>

<span data-ttu-id="91d63-342">Relativní nebo absolutní cesta k souboru *. nuspec* , který se používá pro balení.</span><span class="sxs-lookup"><span data-stu-id="91d63-342">Relative or absolute path to the *.nuspec* file being used for packing.</span></span>

> [!NOTE]
> <span data-ttu-id="91d63-343">Je-li zadán soubor *. nuspec* , používá se **výhradně** k balení informací a žádné informace v projektech se nepoužívají.</span><span class="sxs-lookup"><span data-stu-id="91d63-343">If the *.nuspec* file is specified, it's used **exclusively** for packaging information and any information in the projects is not used.</span></span>

### <a name="nuspecbasepath"></a><span data-ttu-id="91d63-344">NuspecBasePath</span><span class="sxs-lookup"><span data-stu-id="91d63-344">NuspecBasePath</span></span>

<span data-ttu-id="91d63-345">Základní cesta pro soubor *. nuspec*</span><span class="sxs-lookup"><span data-stu-id="91d63-345">Base path for the *.nuspec* file.</span></span>

### <a name="nuspecproperties"></a><span data-ttu-id="91d63-346">NuspecProperties</span><span class="sxs-lookup"><span data-stu-id="91d63-346">NuspecProperties</span></span>

<span data-ttu-id="91d63-347">Seznam párů klíč = hodnota oddělený středníkem.</span><span class="sxs-lookup"><span data-stu-id="91d63-347">Semicolon separated list of key=value pairs.</span></span>

## <a name="assemblyinfo-properties"></a><span data-ttu-id="91d63-348">Vlastnosti AssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="91d63-348">AssemblyInfo properties</span></span>

<span data-ttu-id="91d63-349">[Atributy sestavení](../../standard/assembly/set-attributes.md) , které byly obvykle přítomny v souboru *AssemblyInfo* , se nyní automaticky generují z vlastností.</span><span class="sxs-lookup"><span data-stu-id="91d63-349">[Assembly attributes](../../standard/assembly/set-attributes.md) that were typically present in an *AssemblyInfo* file are now automatically generated from properties.</span></span>

### <a name="properties-per-attribute"></a><span data-ttu-id="91d63-350">Vlastnosti na atribut</span><span class="sxs-lookup"><span data-stu-id="91d63-350">Properties per attribute</span></span>

<span data-ttu-id="91d63-351">Každý atribut má vlastnost, která řídí svůj obsah a druhý pro zakázání jeho generování, jak je znázorněno v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="91d63-351">Each attribute has a property that control its content and another to disable its generation as shown in the following table:</span></span>

| <span data-ttu-id="91d63-352">Atribut</span><span class="sxs-lookup"><span data-stu-id="91d63-352">Attribute</span></span>                                                      | <span data-ttu-id="91d63-353">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="91d63-353">Property</span></span>               | <span data-ttu-id="91d63-354">Vlastnost, která se má zakázat</span><span class="sxs-lookup"><span data-stu-id="91d63-354">Property to disable</span></span>                             |
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

<span data-ttu-id="91d63-355">Poznámky:</span><span class="sxs-lookup"><span data-stu-id="91d63-355">Notes:</span></span>

- <span data-ttu-id="91d63-356">`AssemblyVersion` a `FileVersion` výchozím nastavení je přebírat hodnotu `$(Version)` bez přípony.</span><span class="sxs-lookup"><span data-stu-id="91d63-356">`AssemblyVersion` and `FileVersion` default is to take the value of `$(Version)` without suffix.</span></span> <span data-ttu-id="91d63-357">Například pokud je `$(Version)` `1.2.3-beta.4`, hodnota by byla `1.2.3`.</span><span class="sxs-lookup"><span data-stu-id="91d63-357">For example, if `$(Version)` is `1.2.3-beta.4`, then the value would be `1.2.3`.</span></span>
- <span data-ttu-id="91d63-358">`InformationalVersion` výchozí hodnotu `$(Version)`.</span><span class="sxs-lookup"><span data-stu-id="91d63-358">`InformationalVersion` defaults to the value of `$(Version)`.</span></span>
- <span data-ttu-id="91d63-359">`InformationalVersion` má `$(SourceRevisionId)` připojen, pokud je vlastnost přítomna.</span><span class="sxs-lookup"><span data-stu-id="91d63-359">`InformationalVersion` has `$(SourceRevisionId)` appended if the property is present.</span></span> <span data-ttu-id="91d63-360">Dá se zakázat pomocí `IncludeSourceRevisionInInformationalVersion`.</span><span class="sxs-lookup"><span data-stu-id="91d63-360">It can be disabled using `IncludeSourceRevisionInInformationalVersion`.</span></span>
- <span data-ttu-id="91d63-361">vlastnosti `Copyright` a `Description` se také používají pro metadata NuGet.</span><span class="sxs-lookup"><span data-stu-id="91d63-361">`Copyright` and `Description` properties are also used for NuGet metadata.</span></span>
- <span data-ttu-id="91d63-362">`Configuration` se sdílí se všemi procesy sestavení a nastavuje se prostřednictvím parametru `--configuration` `dotnet` příkazů.</span><span class="sxs-lookup"><span data-stu-id="91d63-362">`Configuration` is shared with all the build process and set via the `--configuration` parameter of `dotnet` commands.</span></span>

### <a name="generateassemblyinfo"></a><span data-ttu-id="91d63-363">GenerateAssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="91d63-363">GenerateAssemblyInfo</span></span>

<span data-ttu-id="91d63-364">Logická hodnota, která povolí nebo zakáže všechny generace AssemblyInfo.</span><span class="sxs-lookup"><span data-stu-id="91d63-364">A Boolean that enable or disable all the AssemblyInfo generation.</span></span> <span data-ttu-id="91d63-365">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="91d63-365">The default value is `true`.</span></span>

### <a name="generatedassemblyinfofile"></a><span data-ttu-id="91d63-366">GeneratedAssemblyInfoFile</span><span class="sxs-lookup"><span data-stu-id="91d63-366">GeneratedAssemblyInfoFile</span></span>

<span data-ttu-id="91d63-367">Cesta k vygenerovanému souboru s informacemi o sestavení</span><span class="sxs-lookup"><span data-stu-id="91d63-367">The path of the generated assembly info file.</span></span> <span data-ttu-id="91d63-368">Ve výchozím nastavení se jedná o soubor v adresáři `$(IntermediateOutputPath)` (obj).</span><span class="sxs-lookup"><span data-stu-id="91d63-368">Default to a file in the `$(IntermediateOutputPath)` (obj) directory.</span></span>
