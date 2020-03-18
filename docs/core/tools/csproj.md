---
title: Dodatky k formátu csproj pro .NET Core
description: Informace o rozdílech mezi existujícími a .NET Core csproj soubory
ms.date: 04/08/2019
ms.openlocfilehash: 2fb00e830380c5c4cbf7b6dcd2c8a585e1617b4b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398991"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a><span data-ttu-id="f25f2-103">Dodatky k formátu csproj pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="f25f2-103">Additions to the csproj format for .NET Core</span></span>

<span data-ttu-id="f25f2-104">Tento dokument popisuje změny, které byly přidány do souborů projektu jako součást přechodu z *project.json* na *csproj* a [MSBuild](https://github.com/Microsoft/MSBuild).</span><span class="sxs-lookup"><span data-stu-id="f25f2-104">This document outlines the changes that were added to the project files as part of the move from *project.json* to *csproj* and [MSBuild](https://github.com/Microsoft/MSBuild).</span></span> <span data-ttu-id="f25f2-105">Další informace o obecné syntaxi souboru projektu a odkaz naleznete v dokumentaci [k souboru projektu MSBuild.](/visualstudio/msbuild/msbuild-project-file-schema-reference)</span><span class="sxs-lookup"><span data-stu-id="f25f2-105">For more information about general project file syntax and reference, see [the MSBuild project file](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation.</span></span>

## <a name="implicit-package-references"></a><span data-ttu-id="f25f2-106">Implicitní odkazy na balíky</span><span class="sxs-lookup"><span data-stu-id="f25f2-106">Implicit package references</span></span>

<span data-ttu-id="f25f2-107">Metabalíčky jsou implicitně odkazovány na základě cílové `<TargetFramework>` architektury `<TargetFrameworks>` zadané v nebo vlastnost souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="f25f2-107">Metapackages are implicitly referenced based on the target framework(s) specified in the `<TargetFramework>` or `<TargetFrameworks>` property of your project file.</span></span> <span data-ttu-id="f25f2-108">`<TargetFrameworks>`je ignorována, pokud `<TargetFramework>` je zadána, nezávisle na pořadí.</span><span class="sxs-lookup"><span data-stu-id="f25f2-108">`<TargetFrameworks>` is ignored if `<TargetFramework>` is specified, independent of order.</span></span> <span data-ttu-id="f25f2-109">Další informace naleznete [v tématu Balíčky, metabalíčky a architektury](../packages.md).</span><span class="sxs-lookup"><span data-stu-id="f25f2-109">For more information, see [Packages, metapackages, and frameworks](../packages.md).</span></span>

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

### <a name="recommendations"></a><span data-ttu-id="f25f2-110">Doporučení</span><span class="sxs-lookup"><span data-stu-id="f25f2-110">Recommendations</span></span>

<span data-ttu-id="f25f2-111">Vzhledem k tomu, `Microsoft.NETCore.App` nebo `NETStandard.Library` metapackages jsou implicitně odkazuje, následující jsou naše doporučené doporučené postupy:</span><span class="sxs-lookup"><span data-stu-id="f25f2-111">Since `Microsoft.NETCore.App` or `NETStandard.Library` metapackages are implicitly referenced, the following are our recommended best practices:</span></span>

- <span data-ttu-id="f25f2-112">Při cílení na rozhraní .NET Core nebo .NET `Microsoft.NETCore.App` `NETStandard.Library` Standard nikdy `<PackageReference>` nemají explicitní odkaz na nebo metapackages prostřednictvím položky v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="f25f2-112">When targeting .NET Core or .NET Standard, never have an explicit reference to the `Microsoft.NETCore.App` or `NETStandard.Library` metapackages via a `<PackageReference>` item in your project file.</span></span>
- <span data-ttu-id="f25f2-113">Pokud potřebujete konkrétní verzi runtime při cílení .NET Core, `<RuntimeFrameworkVersion>` měli byste použít vlastnost `1.0.4`v projektu (například) namísto odkazování na metabalíček.</span><span class="sxs-lookup"><span data-stu-id="f25f2-113">If you need a specific version of the runtime when targeting .NET Core, you should use the `<RuntimeFrameworkVersion>` property in your project (for example, `1.0.4`) instead of referencing the metapackage.</span></span>
  - <span data-ttu-id="f25f2-114">K tomu může dojít, pokud používáte [samostatná nasazení](../deploying/index.md#publish-self-contained) a potřebujete například konkrétní verzi opravy runtime 1.0.0 LTS.</span><span class="sxs-lookup"><span data-stu-id="f25f2-114">This might happen if you are using [self-contained deployments](../deploying/index.md#publish-self-contained) and you need a specific patch version of 1.0.0 LTS runtime, for example.</span></span>
- <span data-ttu-id="f25f2-115">Pokud potřebujete konkrétní verzi `NETStandard.Library` metabalíčku při cílení na standard .NET, můžete použít `<NetStandardImplicitPackageVersion>` vlastnost a nastavit verzi, kterou potřebujete.</span><span class="sxs-lookup"><span data-stu-id="f25f2-115">If you need a specific version of the `NETStandard.Library` metapackage when targeting .NET Standard, you can use the `<NetStandardImplicitPackageVersion>` property and set the version you need.</span></span>
- <span data-ttu-id="f25f2-116">Nepřidávejte explicitně ani neaktualizujte `Microsoft.NETCore.App` `NETStandard.Library` odkazy na metabalíček nebo metabalíček v projektech rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f25f2-116">Don't explicitly add or update references to either the `Microsoft.NETCore.App` or `NETStandard.Library` metapackage in .NET Framework projects.</span></span> <span data-ttu-id="f25f2-117">Pokud je `NETStandard.Library` při použití balíčku NuGet založeného na standardu .NET standard potřeba libovolná verze programu NuGet, nuget tuto verzi automaticky nainstaluje.</span><span class="sxs-lookup"><span data-stu-id="f25f2-117">If any version of `NETStandard.Library` is needed when using a .NET Standard-based NuGet package, NuGet automatically installs that version.</span></span>

## <a name="implicit-version-for-some-package-references"></a><span data-ttu-id="f25f2-118">Implicitní verze pro některé odkazy na balíčky</span><span class="sxs-lookup"><span data-stu-id="f25f2-118">Implicit version for some package references</span></span>

<span data-ttu-id="f25f2-119">Většina použití [`<PackageReference>`](#packagereference) vyžadují `Version` nastavení atributu k určení verze balíčku NuGet, který má být použit.</span><span class="sxs-lookup"><span data-stu-id="f25f2-119">Most usages of [`<PackageReference>`](#packagereference) require setting the `Version` attribute to specify the NuGet package version to be used.</span></span> <span data-ttu-id="f25f2-120">Při použití rozhraní .NET Core 2.1 nebo 2.2 a odkazování [na Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) nebo [Microsoft.AspNetCore.All](/aspnet/core/fundamentals/metapackage), ale atribut je zbytečné.</span><span class="sxs-lookup"><span data-stu-id="f25f2-120">When using .NET Core 2.1 or 2.2 and referencing [Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) or [Microsoft.AspNetCore.All](/aspnet/core/fundamentals/metapackage), however, the  attribute is unnecessary.</span></span> <span data-ttu-id="f25f2-121">Sada .NET Core SDK může automaticky vybrat verzi těchto balíčků, které by měly být použity.</span><span class="sxs-lookup"><span data-stu-id="f25f2-121">The .NET Core SDK can automatically select the version of these packages that should be used.</span></span>

### <a name="recommendation"></a><span data-ttu-id="f25f2-122">Doporučení</span><span class="sxs-lookup"><span data-stu-id="f25f2-122">Recommendation</span></span>

<span data-ttu-id="f25f2-123">Při odkazování `Microsoft.AspNetCore.App` `Microsoft.AspNetCore.All` na nebo balíčky, nezadávejte jejich verzi.</span><span class="sxs-lookup"><span data-stu-id="f25f2-123">When referencing the `Microsoft.AspNetCore.App` or `Microsoft.AspNetCore.All` packages, do not specify their version.</span></span> <span data-ttu-id="f25f2-124">Pokud je zadána verze, sada SDK může způsobit upozornění NETSDK1071.</span><span class="sxs-lookup"><span data-stu-id="f25f2-124">If a version is specified, the SDK may produce warning NETSDK1071.</span></span> <span data-ttu-id="f25f2-125">Chcete-li toto upozornění opravit, odeberte verzi balíčku jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f25f2-125">To fix this warning, remove the package version like in the following example:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore.App" />
</ItemGroup>
```

> <span data-ttu-id="f25f2-126">Známý problém: Sada .NET Core 2.1 SDK tuto syntaxi pouze podporovala, když projekt také používá microsoft.NET.Sdk.Web.</span><span class="sxs-lookup"><span data-stu-id="f25f2-126">Known issue: the .NET Core 2.1 SDK only supported this syntax when the project also uses Microsoft.NET.Sdk.Web.</span></span> <span data-ttu-id="f25f2-127">To je vyřešen v .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="f25f2-127">This is resolved in the .NET Core 2.2 SDK.</span></span>

<span data-ttu-id="f25f2-128">Tyto odkazy na ASP.NET Metapackages Core mají mírně odlišné chování od většiny běžných nuget ových balíčků.</span><span class="sxs-lookup"><span data-stu-id="f25f2-128">These references to ASP.NET Core metapackages have a slightly different behavior from most normal NuGet packages.</span></span> <span data-ttu-id="f25f2-129">[Nasazení aplikací,](../deploying/index.md#publish-runtime-dependent) které používají tyto metabalíčky, jsou závislá na rámci sítě automaticky využívat ASP.NET sdíleného rozhraní Core.</span><span class="sxs-lookup"><span data-stu-id="f25f2-129">[Framework-dependent deployments](../deploying/index.md#publish-runtime-dependent) of applications that use these metapackages automatically take advantage of the ASP.NET Core shared framework.</span></span> <span data-ttu-id="f25f2-130">Při použití metapackages **žádné** prostředky z odkazované ASP.NET balíčky Core NuGet jsou nasazeny s aplikací – ASP.NET základní sdílené rozhraní obsahuje tyto prostředky.</span><span class="sxs-lookup"><span data-stu-id="f25f2-130">When you use the metapackages, **no** assets from the referenced ASP.NET Core NuGet packages are deployed with the application—the ASP.NET Core shared framework contains these assets.</span></span> <span data-ttu-id="f25f2-131">Prostředky ve sdíleném rámci jsou optimalizovány pro cílovou platformu pro zlepšení doby spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="f25f2-131">The assets in the shared framework are optimized for the target platform to improve application startup time.</span></span> <span data-ttu-id="f25f2-132">Další informace o sdíleném rozhraní naleznete v [tématu .NET Core distribution packaging](../distribution-packaging.md).</span><span class="sxs-lookup"><span data-stu-id="f25f2-132">For more information about shared framework, see [.NET Core distribution packaging](../distribution-packaging.md).</span></span>

<span data-ttu-id="f25f2-133">Pokud *je* zadána verze, je považována za *minimální* verzi sdíleného rozhraní ASP.NET Core pro nasazení závislá na rámci a jako *přesná* verze pro samostatná nasazení.</span><span class="sxs-lookup"><span data-stu-id="f25f2-133">If a version *is* specified, it's treated as the *minimum* version of ASP.NET Core shared framework for framework-dependent deployments and as an *exact* version for self-contained deployments.</span></span> <span data-ttu-id="f25f2-134">To může mít následující důsledky:</span><span class="sxs-lookup"><span data-stu-id="f25f2-134">This can have the following consequences:</span></span>

- <span data-ttu-id="f25f2-135">Pokud je verze ASP.NET Core nainstalovaná na serveru menší než verze zadaná v packagereference, proces .NET Core se nespustí.</span><span class="sxs-lookup"><span data-stu-id="f25f2-135">If the version of ASP.NET Core installed on the server is less than the version specified on the PackageReference, the .NET Core process fails to launch.</span></span> <span data-ttu-id="f25f2-136">Aktualizace metabalíčku jsou často k dispozici na NuGet.org před aktualizace byly zpřístupněny v hostitelských prostředích, jako je Azure.</span><span class="sxs-lookup"><span data-stu-id="f25f2-136">Updates to the metapackage are often available on NuGet.org before updates have been made available in hosting environments such as Azure.</span></span> <span data-ttu-id="f25f2-137">Aktualizace verze na PackageReference to ASP.NET Core může způsobit selhání nasazené aplikace.</span><span class="sxs-lookup"><span data-stu-id="f25f2-137">Updating the version on the PackageReference to ASP.NET Core could cause a deployed application to fail.</span></span>
- <span data-ttu-id="f25f2-138">Pokud je aplikace nasazena jako [samostatné nasazení](../deploying/index.md#publish-self-contained), nemusí aplikace obsahovat nejnovější aktualizace zabezpečení pro .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f25f2-138">If the application is deployed as a [self-contained deployment](../deploying/index.md#publish-self-contained), the application may not contain the latest security updates to .NET Core.</span></span> <span data-ttu-id="f25f2-139">Pokud není zadána verze, sada SDK může automaticky zahrnout nejnovější verzi ASP.NET jádra do samostatného nasazení.</span><span class="sxs-lookup"><span data-stu-id="f25f2-139">When a version isn't specified, the SDK can automatically include the newest version of ASP.NET Core in the self-contained deployment.</span></span>

## <a name="default-compilation-includes-in-net-core-projects"></a><span data-ttu-id="f25f2-140">Výchozí kompilace zahrnuje v projektech .NET Core</span><span class="sxs-lookup"><span data-stu-id="f25f2-140">Default compilation includes in .NET Core projects</span></span>

<span data-ttu-id="f25f2-141">S přechodem do formátu *csproj* v nejnovějších verzích sady SDK jsme přesunuli výchozí zahrnutí a vyloučení pro kompilaci položek a vložených prostředků do souborů vlastností sady SDK.</span><span class="sxs-lookup"><span data-stu-id="f25f2-141">With the move to the *csproj* format in the latest SDK versions, we've moved the default includes and excludes for compile items and embedded resources to the SDK properties files.</span></span> <span data-ttu-id="f25f2-142">To znamená, že již není nutné zadávat tyto položky v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="f25f2-142">This means that you no longer need to specify these items in your project file.</span></span>

<span data-ttu-id="f25f2-143">Hlavním důvodem je snížení nepořádku v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="f25f2-143">The main reason for doing this is to reduce the clutter in your project file.</span></span> <span data-ttu-id="f25f2-144">Výchozí hodnoty, které jsou k dispozici v sadě SDK by měla zahrnovat většinu běžných případů použití, takže není nutné opakovat v každém projektu, který vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="f25f2-144">The defaults that are present in the SDK should cover most common use cases, so there is no need to repeat them in every project that you create.</span></span> <span data-ttu-id="f25f2-145">To vede k menším souborům projektu, které jsou mnohem srozumitelnější a v případě potřeby ručně upravovány.</span><span class="sxs-lookup"><span data-stu-id="f25f2-145">This leads to smaller project files that are much easier to understand as well as edit by hand, if needed.</span></span>

<span data-ttu-id="f25f2-146">V následující tabulce je uvedeno, který prvek a které globs jsou [zahrnuty](https://en.wikipedia.org/wiki/Glob_(programming)) i vyloučeny do sady SDK:</span><span class="sxs-lookup"><span data-stu-id="f25f2-146">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are both included and excluded in the SDK:</span></span>

| <span data-ttu-id="f25f2-147">Element</span><span class="sxs-lookup"><span data-stu-id="f25f2-147">Element</span></span>           | <span data-ttu-id="f25f2-148">Zahrnout glob</span><span class="sxs-lookup"><span data-stu-id="f25f2-148">Include glob</span></span>                              | <span data-ttu-id="f25f2-149">Vyloučit glob</span><span class="sxs-lookup"><span data-stu-id="f25f2-149">Exclude glob</span></span>                                                  | <span data-ttu-id="f25f2-150">Odstranit glob</span><span class="sxs-lookup"><span data-stu-id="f25f2-150">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| <span data-ttu-id="f25f2-151">Kompilaci</span><span class="sxs-lookup"><span data-stu-id="f25f2-151">Compile</span></span>           | <span data-ttu-id="f25f2-152">\*\*/\*.cs (nebo jiná jazyková rozšíření)</span><span class="sxs-lookup"><span data-stu-id="f25f2-152">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="f25f2-153">\*\*/\*.user;  \*\*/\*. \*proj;  \* \* /.sln; \*  \* \* / \*.vssscc</span><span class="sxs-lookup"><span data-stu-id="f25f2-153">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="f25f2-154">Není dostupné.</span><span class="sxs-lookup"><span data-stu-id="f25f2-154">N/A</span></span>                      |
| <span data-ttu-id="f25f2-155">Vložený prostředek</span><span class="sxs-lookup"><span data-stu-id="f25f2-155">EmbeddedResource</span></span>  | <span data-ttu-id="f25f2-156">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="f25f2-156">\*\*/\*.resx</span></span>                              | <span data-ttu-id="f25f2-157">\*\*/\*.user; \*\*/\*. \*proj; \* \* /.sln; \* \* \* / \*.vssscc</span><span class="sxs-lookup"><span data-stu-id="f25f2-157">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="f25f2-158">Není dostupné.</span><span class="sxs-lookup"><span data-stu-id="f25f2-158">N/A</span></span>                      |
| <span data-ttu-id="f25f2-159">Žádný</span><span class="sxs-lookup"><span data-stu-id="f25f2-159">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="f25f2-160">\*\*/\*.user; \*\*/\*. \*proj; \* \* /.sln; \* \* \* / \*.vssscc</span><span class="sxs-lookup"><span data-stu-id="f25f2-160">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="f25f2-161">\*\*/\*.cs; \* \* /.resx \*</span><span class="sxs-lookup"><span data-stu-id="f25f2-161">\*\*/\*.cs; \*\*/\*.resx</span></span>   |

> [!NOTE]
> <span data-ttu-id="f25f2-162">**Vyloučit glob** vždy `./bin` vylučuje `./obj` a složky, `$(BaseOutputPath)` které `$(BaseIntermediateOutputPath)` jsou reprezentovány vlastnostmi MSBuild.</span><span class="sxs-lookup"><span data-stu-id="f25f2-162">**Exclude glob** always excludes the `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, respectively.</span></span> <span data-ttu-id="f25f2-163">Jako celek jsou všechna vyloučení `$(DefaultItemExcludes)`reprezentována .</span><span class="sxs-lookup"><span data-stu-id="f25f2-163">As a whole, all excludes are represented by `$(DefaultItemExcludes)`.</span></span>

<span data-ttu-id="f25f2-164">Pokud máte globs v projektu a pokusíte se jej vytvořit pomocí nejnovější sady SDK, zobrazí se následující chyba:</span><span class="sxs-lookup"><span data-stu-id="f25f2-164">If you have globs in your project and you try to build it using the newest SDK, you'll get the following error:</span></span>

> <span data-ttu-id="f25f2-165">Byly zahrnuty duplicitní položky kompilace.</span><span class="sxs-lookup"><span data-stu-id="f25f2-165">Duplicate Compile items were included.</span></span> <span data-ttu-id="f25f2-166">Sada .NET SDK ve výchozím nastavení obsahuje položky kompilace z adresáře projektu.</span><span class="sxs-lookup"><span data-stu-id="f25f2-166">The .NET SDK includes Compile items from your project directory by default.</span></span> <span data-ttu-id="f25f2-167">Tyto položky můžete odebrat ze souboru projektu nebo nastavit vlastnost EnableDefaultCompileItems na hodnotu false, pokud je chcete explicitně zahrnout do souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="f25f2-167">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

<span data-ttu-id="f25f2-168">Chcete-li tuto chybu obejít, můžete `Compile` buď odebrat explicitní položky, které odpovídají položkám uvedeným v předchozí tabulce, nebo můžete vlastnost nastavit `<EnableDefaultCompileItems>` na `false`, například takto:</span><span class="sxs-lookup"><span data-stu-id="f25f2-168">In order to get around this error, you can either remove the explicit `Compile` items that match the ones listed on the previous table, or you can set the `<EnableDefaultCompileItems>` property to `false`, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

<span data-ttu-id="f25f2-169">Nastavení této `false` vlastnosti zakáže implicitní zahrnutí, návrat k chování předchozích sad SDK, kde jste museli zadat výchozí globs v projektu.</span><span class="sxs-lookup"><span data-stu-id="f25f2-169">Setting this property to `false` will disable implicit inclusion, reverting to the behavior of previous SDKs where you had to specify the default globs in your project.</span></span>

<span data-ttu-id="f25f2-170">Tato změna nemění hlavní mechaniky jiných zahrnuje.</span><span class="sxs-lookup"><span data-stu-id="f25f2-170">This change does not modify the main mechanics of other includes.</span></span> <span data-ttu-id="f25f2-171">Pokud však chcete například zadat některé soubory, které chcete publikovat s vaší aplikací, můžete pro to stále používat `<Content>` známé mechanismy v *csproj* (například prvek).</span><span class="sxs-lookup"><span data-stu-id="f25f2-171">However, if you wish to specify, for example, some files to get published with your app, you can still use the known mechanisms in *csproj* for that (for example, the `<Content>` element).</span></span>

<span data-ttu-id="f25f2-172">`<EnableDefaultCompileItems>`pouze zakáže `Compile` globs, ale nemá vliv na `None` jiné globs, \*jako je implicitní glob, který se vztahuje i na .cs položky.</span><span class="sxs-lookup"><span data-stu-id="f25f2-172">`<EnableDefaultCompileItems>` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob, which also applies to \*.cs items.</span></span> <span data-ttu-id="f25f2-173">Z tohoto důvodu bude **Průzkumník řešení** pokračovat v zobrazení \*položek `None` .cs jako součást projektu, zahrnutých jako položky.</span><span class="sxs-lookup"><span data-stu-id="f25f2-173">Because of that, **Solution Explorer** will continue show \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="f25f2-174">Podobným způsobem můžete nastavit `<EnableDefaultNoneItems>` na hodnotu false, chcete-li zakázat implicitní `None` glob, takto:</span><span class="sxs-lookup"><span data-stu-id="f25f2-174">In a similar way, you can set `<EnableDefaultNoneItems>` to false to disable the implicit `None` glob, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

<span data-ttu-id="f25f2-175">Chcete-li zakázat **všechny implicitní globs**, můžete nastavit `<EnableDefaultItems>` vlastnost jako `false` v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f25f2-175">To disable **all implicit globs**, you can set the `<EnableDefaultItems>` property to `false` as in the following example:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a><span data-ttu-id="f25f2-176">Jak zobrazit celý projekt tak, jak jej vidí MSBuild</span><span class="sxs-lookup"><span data-stu-id="f25f2-176">How to see the whole project as MSBuild sees it</span></span>

<span data-ttu-id="f25f2-177">Zatímco tyto změny csproj výrazně zjednodušit soubory projektu, můžete chtít vidět plně rozšířený projekt jako MSBuild vidí, jakmile SDK a jeho cíle jsou zahrnuty.</span><span class="sxs-lookup"><span data-stu-id="f25f2-177">While those csproj changes greatly simplify project files, you might want to see the fully expanded project as MSBuild sees it once the SDK and its targets are included.</span></span> <span data-ttu-id="f25f2-178">Předběžně zpracujte projekt [`dotnet msbuild`](dotnet-msbuild.md) [ `/pp` pomocí přepínače](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) příkazu, který zobrazuje, které soubory jsou importovány, jejich zdroje a jejich příspěvky k sestavení, aniž by bylo skutečně budováno projektu:</span><span class="sxs-lookup"><span data-stu-id="f25f2-178">Preprocess the project with [the `/pp` switch](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) of the [`dotnet msbuild`](dotnet-msbuild.md) command, which shows which files are imported, their sources, and their contributions to the build without actually building the project:</span></span>

`dotnet msbuild -pp:fullproject.xml`

<span data-ttu-id="f25f2-179">Pokud projekt má více cílových architektur, výsledky příkazu by měly být zaměřeny pouze na jeden z nich zadáním jako msbuild vlastnost:</span><span class="sxs-lookup"><span data-stu-id="f25f2-179">If the project has multiple target frameworks, the results of the command should be focused on only one of them by specifying it as an MSBuild property:</span></span>

`dotnet msbuild -p:TargetFramework=netcoreapp2.0 -pp:fullproject.xml`

## <a name="additions"></a><span data-ttu-id="f25f2-180">Dodatky</span><span class="sxs-lookup"><span data-stu-id="f25f2-180">Additions</span></span>

### <a name="sdk-attribute"></a><span data-ttu-id="f25f2-181">Atribut Sdk</span><span class="sxs-lookup"><span data-stu-id="f25f2-181">Sdk attribute</span></span>

<span data-ttu-id="f25f2-182">Kořenový `<Project>` prvek souboru *.csproj* má `Sdk`nový atribut s názvem .</span><span class="sxs-lookup"><span data-stu-id="f25f2-182">The root `<Project>` element of the *.csproj* file has a new attribute called `Sdk`.</span></span> <span data-ttu-id="f25f2-183">`Sdk`určuje, která sada SDK bude projektem používán.</span><span class="sxs-lookup"><span data-stu-id="f25f2-183">`Sdk` specifies which SDK will be used by the project.</span></span> <span data-ttu-id="f25f2-184">Sada SDK, jak popisuje [dokument vrstvení,](cli-msbuild-architecture.md) je sada [úloh](/visualstudio/msbuild/msbuild-tasks) a [cílů](/visualstudio/msbuild/msbuild-targets) MSBuild, které mohou vytvářet základní kód .NET.</span><span class="sxs-lookup"><span data-stu-id="f25f2-184">The SDK, as the [layering document](cli-msbuild-architecture.md) describes, is a set of MSBuild [tasks](/visualstudio/msbuild/msbuild-tasks) and [targets](/visualstudio/msbuild/msbuild-targets) that can build .NET Core code.</span></span> <span data-ttu-id="f25f2-185">Pro službu .NET Core jsou k dispozici následující sady SDK:</span><span class="sxs-lookup"><span data-stu-id="f25f2-185">The following SDKs are available for .NET Core:</span></span>

1. <span data-ttu-id="f25f2-186">Sada .NET Core SDK s ID`Microsoft.NET.Sdk`</span><span class="sxs-lookup"><span data-stu-id="f25f2-186">The .NET Core SDK with the ID of `Microsoft.NET.Sdk`</span></span>
2. <span data-ttu-id="f25f2-187">Sada .NET Core web SDK s ID`Microsoft.NET.Sdk.Web`</span><span class="sxs-lookup"><span data-stu-id="f25f2-187">The .NET Core web SDK with the ID of `Microsoft.NET.Sdk.Web`</span></span>
3. <span data-ttu-id="f25f2-188">Knihovna třídy .NET Core Razor SDK s ID`Microsoft.NET.Sdk.Razor`</span><span class="sxs-lookup"><span data-stu-id="f25f2-188">The .NET Core Razor Class Library SDK with the ID of `Microsoft.NET.Sdk.Razor`</span></span>
4. <span data-ttu-id="f25f2-189">Služba .NET Core Worker Service `Microsoft.NET.Sdk.Worker` s ID (od .NET Core 3.0)</span><span class="sxs-lookup"><span data-stu-id="f25f2-189">The .NET Core Worker Service with the ID of `Microsoft.NET.Sdk.Worker` (since .NET Core 3.0)</span></span>
5. <span data-ttu-id="f25f2-190">Rozhraní .NET Core WinForms a WPF `Microsoft.NET.Sdk.WindowsDesktop` s ID (od .NET Core 3.0)</span><span class="sxs-lookup"><span data-stu-id="f25f2-190">The .NET Core WinForms and WPF with the ID of `Microsoft.NET.Sdk.WindowsDesktop` (since .NET Core 3.0)</span></span>

<span data-ttu-id="f25f2-191">Musíte mít `Sdk` atribut nastaven na jeden z těchto `<Project>` ID na prvek, aby bylo možné použít nástroje .NET Core a vytvořit kód.</span><span class="sxs-lookup"><span data-stu-id="f25f2-191">You need to have the `Sdk` attribute set to one of those IDs on the `<Project>` element in order to use the .NET Core tools and build your code.</span></span>

### <a name="packagereference"></a><span data-ttu-id="f25f2-192">Odkaz na balíček</span><span class="sxs-lookup"><span data-stu-id="f25f2-192">PackageReference</span></span>

<span data-ttu-id="f25f2-193">Prvek `<PackageReference>` položky určuje [závislost NuGet v projektu](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="f25f2-193">A `<PackageReference>` item element specifies a [NuGet dependency in the project](/nuget/consume-packages/package-references-in-project-files).</span></span> <span data-ttu-id="f25f2-194">Atribut `Include` určuje ID balíčku.</span><span class="sxs-lookup"><span data-stu-id="f25f2-194">The `Include` attribute specifies the package ID.</span></span>

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a><span data-ttu-id="f25f2-195">Version</span><span class="sxs-lookup"><span data-stu-id="f25f2-195">Version</span></span>

<span data-ttu-id="f25f2-196">Požadovaný `Version` atribut určuje verzi balíčku, který má být obnoven.</span><span class="sxs-lookup"><span data-stu-id="f25f2-196">The required `Version` attribute specifies the version of the package to restore.</span></span> <span data-ttu-id="f25f2-197">Atribut respektuje pravidla [nuget verze schématu.](/nuget/reference/package-versioning#version-ranges-and-wildcards)</span><span class="sxs-lookup"><span data-stu-id="f25f2-197">The attribute respects the rules of the [NuGet versioning](/nuget/reference/package-versioning#version-ranges-and-wildcards) scheme.</span></span> <span data-ttu-id="f25f2-198">Výchozí chování je minimální verze, včetně shoda.</span><span class="sxs-lookup"><span data-stu-id="f25f2-198">The default behavior is a minimum version, inclusive match.</span></span> <span data-ttu-id="f25f2-199">Například zadání `Version="1.2.3"` je ekvivalentní NuGet `[1.2.3, )` zápisu a znamená, že vyřešený balíček bude mít verzi 1.2.3, pokud je k dispozici nebo větší jinak.</span><span class="sxs-lookup"><span data-stu-id="f25f2-199">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3, )` and means the resolved package will have the version 1.2.3 if available or greater otherwise.</span></span>

#### <a name="includeassets-excludeassets-and-privateassets"></a><span data-ttu-id="f25f2-200">Zahrnout majetek, vyloučit majetek a privateassets</span><span class="sxs-lookup"><span data-stu-id="f25f2-200">IncludeAssets, ExcludeAssets, and PrivateAssets</span></span>

<span data-ttu-id="f25f2-201">`IncludeAssets`atribut určuje, které prostředky patřící `<PackageReference>` do balíčku určeného by měly být spotřebovány.</span><span class="sxs-lookup"><span data-stu-id="f25f2-201">`IncludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed.</span></span> <span data-ttu-id="f25f2-202">Ve výchozím nastavení jsou zahrnuty všechny datové zdroje balíčku.</span><span class="sxs-lookup"><span data-stu-id="f25f2-202">By default, all package assets are included.</span></span>

<span data-ttu-id="f25f2-203">`ExcludeAssets`atribut určuje, které prostředky patřící `<PackageReference>` do balíčku určeného by neměly být spotřebovány.</span><span class="sxs-lookup"><span data-stu-id="f25f2-203">`ExcludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should not be consumed.</span></span>

<span data-ttu-id="f25f2-204">`PrivateAssets`atribut určuje, které prostředky patřící `<PackageReference>` do balíčku určeného by měly být spotřebovány, ale ne tok do dalšího projektu.</span><span class="sxs-lookup"><span data-stu-id="f25f2-204">`PrivateAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed but not flow to the next project.</span></span> <span data-ttu-id="f25f2-205">A `Analyzers` `Build` prostředky `ContentFiles` jsou ve výchozím nastavení soukromé, pokud tento atribut není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="f25f2-205">The `Analyzers`, `Build` and `ContentFiles` assets are private by default when this attribute is not present.</span></span>

> [!NOTE]
> <span data-ttu-id="f25f2-206">`PrivateAssets`je ekvivalentní prvku *project.json*/*xproj.* `SuppressParent`</span><span class="sxs-lookup"><span data-stu-id="f25f2-206">`PrivateAssets` is equivalent to the *project.json*/*xproj* `SuppressParent` element.</span></span>

<span data-ttu-id="f25f2-207">Tyto atributy mohou obsahovat jednu nebo více následujících položek oddělených středníkem, `;` pokud je uvedeno více než jeden:</span><span class="sxs-lookup"><span data-stu-id="f25f2-207">These attributes can contain one or more of the following items, separated by the semicolon `;` character if more than one is listed:</span></span>

- <span data-ttu-id="f25f2-208">`Compile`– obsah složky *lib* jsou k dispozici pro kompilaci.</span><span class="sxs-lookup"><span data-stu-id="f25f2-208">`Compile` – the contents of the *lib* folder are available to compile against.</span></span>
- <span data-ttu-id="f25f2-209">`Runtime`– obsah *složky runtime* jsou distribuovány.</span><span class="sxs-lookup"><span data-stu-id="f25f2-209">`Runtime` – the contents of the *runtime* folder are distributed.</span></span>
- <span data-ttu-id="f25f2-210">`ContentFiles`– obsah složky *contentfiles* se používá.</span><span class="sxs-lookup"><span data-stu-id="f25f2-210">`ContentFiles` – the contents of the *contentfiles* folder are used.</span></span>
- <span data-ttu-id="f25f2-211">`Build`– používají se rekvizity/cíle ve složce *sestavení.*</span><span class="sxs-lookup"><span data-stu-id="f25f2-211">`Build` – the props/targets in the *build* folder are used.</span></span>
- <span data-ttu-id="f25f2-212">`Native`– obsah z nativních datových zdrojů se zkopíruje do *výstupní* složky pro běh.</span><span class="sxs-lookup"><span data-stu-id="f25f2-212">`Native` – the contents from native assets are copied to the *output* folder for runtime.</span></span>
- <span data-ttu-id="f25f2-213">`Analyzers`– analyzátory.</span><span class="sxs-lookup"><span data-stu-id="f25f2-213">`Analyzers` – the analyzers are used.</span></span>

<span data-ttu-id="f25f2-214">Alternativně atribut může obsahovat:</span><span class="sxs-lookup"><span data-stu-id="f25f2-214">Alternatively, the attribute can contain:</span></span>

- <span data-ttu-id="f25f2-215">`None`– žádný z aktiv není použit.</span><span class="sxs-lookup"><span data-stu-id="f25f2-215">`None` – none of the assets are used.</span></span>
- <span data-ttu-id="f25f2-216">`All`– používají se všechna aktiva.</span><span class="sxs-lookup"><span data-stu-id="f25f2-216">`All` – all assets are used.</span></span>

### <a name="dotnetclitoolreference"></a><span data-ttu-id="f25f2-217">DotNetCliToolReference</span><span class="sxs-lookup"><span data-stu-id="f25f2-217">DotNetCliToolReference</span></span>

<span data-ttu-id="f25f2-218">Prvek `<DotNetCliToolReference>` položky určuje nástroj rozhraní se klis, který chce uživatel obnovit v kontextu projektu.</span><span class="sxs-lookup"><span data-stu-id="f25f2-218">A `<DotNetCliToolReference>` item element specifies the CLI tool that the user wants to restore in the context of the project.</span></span> <span data-ttu-id="f25f2-219">Je to náhrada `tools` za uzel v *project.json*.</span><span class="sxs-lookup"><span data-stu-id="f25f2-219">It's a replacement for the `tools` node in *project.json*.</span></span>

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

<span data-ttu-id="f25f2-220">Všimněte `DotNetCliToolReference` si, že je [nyní zastaralé](https://github.com/dotnet/announcements/issues/107) ve prospěch [.NET Core místní nástroje](https://aka.ms/local-tools).</span><span class="sxs-lookup"><span data-stu-id="f25f2-220">Note that `DotNetCliToolReference` is [now deprecated](https://github.com/dotnet/announcements/issues/107) in favor of [.NET Core Local Tools](https://aka.ms/local-tools).</span></span>

#### <a name="version"></a><span data-ttu-id="f25f2-221">Version</span><span class="sxs-lookup"><span data-stu-id="f25f2-221">Version</span></span>

<span data-ttu-id="f25f2-222">`Version`určuje verzi balíčku, který chcete obnovit.</span><span class="sxs-lookup"><span data-stu-id="f25f2-222">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="f25f2-223">Atribut respektuje pravidla [nuget verze schématu.](/nuget/create-packages/dependency-versions#version-ranges)</span><span class="sxs-lookup"><span data-stu-id="f25f2-223">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="f25f2-224">Výchozí chování je minimální verze, včetně shoda.</span><span class="sxs-lookup"><span data-stu-id="f25f2-224">The default behavior is a minimum version, inclusive match.</span></span> <span data-ttu-id="f25f2-225">Například zadání `Version="1.2.3"` je ekvivalentní NuGet `[1.2.3, )` zápisu a znamená, že vyřešený balíček bude mít verzi 1.2.3, pokud je k dispozici nebo větší jinak.</span><span class="sxs-lookup"><span data-stu-id="f25f2-225">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3, )` and means the resolved package will have the version 1.2.3 if available or greater otherwise.</span></span>

### <a name="runtimeidentifiers"></a><span data-ttu-id="f25f2-226">Identifikátory runtime</span><span class="sxs-lookup"><span data-stu-id="f25f2-226">RuntimeIdentifiers</span></span>

<span data-ttu-id="f25f2-227">Element `<RuntimeIdentifiers>` vlastnosti umožňuje zadat seznam [identifikátorů runtime (RID)](../rid-catalog.md) pro projekt oddělený středníkem.</span><span class="sxs-lookup"><span data-stu-id="f25f2-227">The `<RuntimeIdentifiers>` property element lets you specify a semicolon-delimited list of [Runtime Identifiers (RIDs)](../rid-catalog.md) for the project.</span></span>
<span data-ttu-id="f25f2-228">Ridy umožňují publikování samostatných nasazení.</span><span class="sxs-lookup"><span data-stu-id="f25f2-228">RIDs enable publishing self-contained deployments.</span></span>

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a><span data-ttu-id="f25f2-229">Identifikátor runtime</span><span class="sxs-lookup"><span data-stu-id="f25f2-229">RuntimeIdentifier</span></span>

<span data-ttu-id="f25f2-230">Element `<RuntimeIdentifier>` vlastnosti umožňuje zadat pouze jeden [identifikátor runtime (RID)](../rid-catalog.md) pro projekt.</span><span class="sxs-lookup"><span data-stu-id="f25f2-230">The `<RuntimeIdentifier>` property element allows you to specify only one [Runtime Identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="f25f2-231">Rid umožňuje publikování samostatné nasazení.</span><span class="sxs-lookup"><span data-stu-id="f25f2-231">The RID enables publishing a self-contained deployment.</span></span>

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

<span data-ttu-id="f25f2-232">Místo `<RuntimeIdentifiers>` toho použijte (množné číslo), pokud potřebujete publikovat pro více runtimes.</span><span class="sxs-lookup"><span data-stu-id="f25f2-232">Use `<RuntimeIdentifiers>` (plural) instead if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="f25f2-233">`<RuntimeIdentifier>`může poskytovat rychlejší sestavení, pokud je vyžadován pouze jeden runtime.</span><span class="sxs-lookup"><span data-stu-id="f25f2-233">`<RuntimeIdentifier>` can provide faster builds when only a single runtime is required.</span></span>

### <a name="packagetargetfallback"></a><span data-ttu-id="f25f2-234">BalíčekTargetFallback</span><span class="sxs-lookup"><span data-stu-id="f25f2-234">PackageTargetFallback</span></span>

<span data-ttu-id="f25f2-235">Element `<PackageTargetFallback>` vlastnosti umožňuje zadat sadu kompatibilních cílů, které mají být použity při obnovení balíčků.</span><span class="sxs-lookup"><span data-stu-id="f25f2-235">The `<PackageTargetFallback>` property element allows you to specify a set of compatible targets to be used when restoring packages.</span></span> <span data-ttu-id="f25f2-236">Je navržen tak, aby balíčky, které používají dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) pracovat s balíčky, které nedeklarují dotnet TxM.</span><span class="sxs-lookup"><span data-stu-id="f25f2-236">It's designed to allow packages that use the dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) to operate with packages that don't declare a dotnet TxM.</span></span> <span data-ttu-id="f25f2-237">Pokud váš projekt používá dotnet TxM, pak všechny balíčky, na kterých závisí, musí `<PackageTargetFallback>` mít také dotnet TxM, pokud nepřidáte do projektu, aby byly platformy bez dotnetu kompatibilní s dotnet.</span><span class="sxs-lookup"><span data-stu-id="f25f2-237">If your project uses the dotnet TxM, then all the packages it depends on must also have a dotnet TxM, unless you add the `<PackageTargetFallback>` to your project in order to allow non-dotnet platforms to be compatible with dotnet.</span></span>

<span data-ttu-id="f25f2-238">Následující příklad poskytuje záložní informace o všech cílech v projektu:</span><span class="sxs-lookup"><span data-stu-id="f25f2-238">The following example provides the fallbacks for all targets in your project:</span></span>

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

<span data-ttu-id="f25f2-239">Následující příklad určuje záložní pouze pro `netcoreapp2.1` cíl:</span><span class="sxs-lookup"><span data-stu-id="f25f2-239">The following example specifies the fallbacks only for the `netcoreapp2.1` target:</span></span>

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp2.1'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="build-events"></a><span data-ttu-id="f25f2-240">Vytváření událostí</span><span class="sxs-lookup"><span data-stu-id="f25f2-240">Build events</span></span>

<span data-ttu-id="f25f2-241">Způsob, jakým jsou v souboru projektu zadány události před sestavením a po sestavení, se změnil.</span><span class="sxs-lookup"><span data-stu-id="f25f2-241">The way that pre-build and post-build events are specified in the project file has changed.</span></span> <span data-ttu-id="f25f2-242">Vlastnosti PreBuildEvent a PostBuildEvent se ve formátu projektu ve stylu sady SDK nedoporučují, protože makra jako $(ProjectDir) nejsou vyřešena.</span><span class="sxs-lookup"><span data-stu-id="f25f2-242">The properties PreBuildEvent and PostBuildEvent are not recommended in the SDK-style project format, because macros such as $(ProjectDir) are not resolved.</span></span> <span data-ttu-id="f25f2-243">Například následující kód již není podporován:</span><span class="sxs-lookup"><span data-stu-id="f25f2-243">For example, the following code is no longer supported:</span></span>

```xml
<PropertyGroup>
    <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)" />
</PropertyGroup>
```

<span data-ttu-id="f25f2-244">V projektech ve stylu sady SDK `PreBuild` použijte `PostBuild` cíl `BeforeTargets` MSBuild `AfterTargets` s `PostBuild`názvem nebo a nastavte vlastnost pro `PreBuild` nebo vlastnost pro .</span><span class="sxs-lookup"><span data-stu-id="f25f2-244">In SDK-style projects, use an MSBuild target named `PreBuild` or `PostBuild` and set the `BeforeTargets` property for `PreBuild` or the `AfterTargets` property for `PostBuild`.</span></span> <span data-ttu-id="f25f2-245">Pro předchozí příklad použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="f25f2-245">For the preceding example, use the following code:</span></span>

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>

<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
><span data-ttu-id="f25f2-246">Pro cíle MSBuild můžete použít libovolný název, ale ide `PostBuild` sady Visual Studio rozpozná a cílí, `PreBuild` takže doporučujeme tyto názvy používat, abyste mohli upravovat příkazy v ide sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f25f2-246">You can use any name for the MSBuild targets, but the Visual Studio IDE recognizes `PreBuild` and `PostBuild` targets, so we recommend using those names so that you can edit the commands in the Visual Studio IDE.</span></span>

## <a name="nuget-metadata-properties"></a><span data-ttu-id="f25f2-247">Vlastnosti metadat NuGet</span><span class="sxs-lookup"><span data-stu-id="f25f2-247">NuGet metadata properties</span></span>

<span data-ttu-id="f25f2-248">S přechodem na MSBuild jsme přesunuli vstupní metadata, která se používá při balení balíčku NuGet z *project.json* na *soubory .csproj.*</span><span class="sxs-lookup"><span data-stu-id="f25f2-248">With the move to MSBuild, we have moved the input metadata that is used when packing a NuGet package from *project.json* to *.csproj* files.</span></span> <span data-ttu-id="f25f2-249">Vstupy jsou MSBuild vlastnosti, takže `<PropertyGroup>` musí jít do skupiny.</span><span class="sxs-lookup"><span data-stu-id="f25f2-249">The inputs are MSBuild properties so they have to go within a `<PropertyGroup>` group.</span></span> <span data-ttu-id="f25f2-250">Následuje seznam vlastností, které se používají jako vstupy do `dotnet pack` procesu `Pack` balení při použití příkazu nebo cíle MSBuild, který je součástí sady SDK:</span><span class="sxs-lookup"><span data-stu-id="f25f2-250">The following is the list of properties that are used as inputs to the packing process when using the `dotnet pack` command or the `Pack` MSBuild target that is part of the SDK:</span></span>

### <a name="ispackable"></a><span data-ttu-id="f25f2-251">Jestelná</span><span class="sxs-lookup"><span data-stu-id="f25f2-251">IsPackable</span></span>

<span data-ttu-id="f25f2-252">Logická hodnota, která určuje, zda může být projekt zabalen.</span><span class="sxs-lookup"><span data-stu-id="f25f2-252">A Boolean value that specifies whether the project can be packed.</span></span> <span data-ttu-id="f25f2-253">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="f25f2-253">The default value is `true`.</span></span>

### <a name="packageversion"></a><span data-ttu-id="f25f2-254">PackageVersion</span><span class="sxs-lookup"><span data-stu-id="f25f2-254">PackageVersion</span></span>

<span data-ttu-id="f25f2-255">Určuje verzi, kterou bude mít výsledný balíček.</span><span class="sxs-lookup"><span data-stu-id="f25f2-255">Specifies the version that the resulting package will have.</span></span> <span data-ttu-id="f25f2-256">Přijímá všechny formy řetězce verze NuGet.</span><span class="sxs-lookup"><span data-stu-id="f25f2-256">Accepts all forms of NuGet version string.</span></span> <span data-ttu-id="f25f2-257">Výchozí hodnota je `$(Version)`hodnota , to `Version` znamená vlastnost v projektu.</span><span class="sxs-lookup"><span data-stu-id="f25f2-257">Default is the value of `$(Version)`, that is, of the property `Version` in the project.</span></span>

### <a name="packageid"></a><span data-ttu-id="f25f2-258">Id balení</span><span class="sxs-lookup"><span data-stu-id="f25f2-258">PackageId</span></span>

<span data-ttu-id="f25f2-259">Určuje název výsledného balíčku.</span><span class="sxs-lookup"><span data-stu-id="f25f2-259">Specifies the name for the resulting package.</span></span> <span data-ttu-id="f25f2-260">Pokud není zadán, `pack` bude operace `AssemblyName` ve výchozím nastavení používat název nebo jako název balíčku.</span><span class="sxs-lookup"><span data-stu-id="f25f2-260">If not specified, the `pack` operation will default to using the `AssemblyName` or directory name as the name of the package.</span></span>

### <a name="title"></a><span data-ttu-id="f25f2-261">Nadpis</span><span class="sxs-lookup"><span data-stu-id="f25f2-261">Title</span></span>

<span data-ttu-id="f25f2-262">Lidský název balíčku, obvykle používaný v ui se zobrazí jako na nuget.org a Správce balíčků v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f25f2-262">A human-friendly title of the package, typically used in UI displays as on nuget.org and the Package Manager in Visual Studio.</span></span> <span data-ttu-id="f25f2-263">Pokud není zadán, použije se místo toho ID balíčku.</span><span class="sxs-lookup"><span data-stu-id="f25f2-263">If not specified, the package ID is used instead.</span></span>

### <a name="authors"></a><span data-ttu-id="f25f2-264">Autoři</span><span class="sxs-lookup"><span data-stu-id="f25f2-264">Authors</span></span>

<span data-ttu-id="f25f2-265">Středník-oddělený seznam autorů balíčků, odpovídající názvy profilů na nuget.org. Ty jsou zobrazeny v Galerii NuGet na nuget.org a slouží ke křížovým odkazům balíčky stejnými autory.</span><span class="sxs-lookup"><span data-stu-id="f25f2-265">A semicolon-separated list of packages authors, matching the profile names on nuget.org. These are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span>

### <a name="packagedescription"></a><span data-ttu-id="f25f2-266">Popis balíčku</span><span class="sxs-lookup"><span data-stu-id="f25f2-266">PackageDescription</span></span>

<span data-ttu-id="f25f2-267">Dlouhý popis balíčku pro zobrazení ui.</span><span class="sxs-lookup"><span data-stu-id="f25f2-267">A long description of the package for UI display.</span></span>

### <a name="description"></a><span data-ttu-id="f25f2-268">Popis</span><span class="sxs-lookup"><span data-stu-id="f25f2-268">Description</span></span>

<span data-ttu-id="f25f2-269">Dlouhý popis sestavení.</span><span class="sxs-lookup"><span data-stu-id="f25f2-269">A long description for the assembly.</span></span> <span data-ttu-id="f25f2-270">Pokud `PackageDescription` není zadán, pak tato vlastnost se také používá jako popis balíčku.</span><span class="sxs-lookup"><span data-stu-id="f25f2-270">If `PackageDescription` is not specified, then this property is also used as the description of the package.</span></span>

### <a name="copyright"></a><span data-ttu-id="f25f2-271">Copyright</span><span class="sxs-lookup"><span data-stu-id="f25f2-271">Copyright</span></span>

<span data-ttu-id="f25f2-272">Podrobnosti o autorských právech k balíčku.</span><span class="sxs-lookup"><span data-stu-id="f25f2-272">Copyright details for the package.</span></span>

### <a name="packagerequirelicenseacceptance"></a><span data-ttu-id="f25f2-273">PackageRequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="f25f2-273">PackageRequireLicenseAcceptance</span></span>

<span data-ttu-id="f25f2-274">Logická hodnota, která určuje, zda musí klient vyzvat spotřebitele k přijetí licence balíčku před instalací balíčku.</span><span class="sxs-lookup"><span data-stu-id="f25f2-274">A Boolean value that specifies whether the client must prompt the consumer to accept the package license before installing the package.</span></span> <span data-ttu-id="f25f2-275">Výchozí formát je `false`.</span><span class="sxs-lookup"><span data-stu-id="f25f2-275">The default is `false`.</span></span>

### <a name="developmentdependency"></a><span data-ttu-id="f25f2-276">DevelopmentDependency</span><span class="sxs-lookup"><span data-stu-id="f25f2-276">DevelopmentDependency</span></span>

<span data-ttu-id="f25f2-277">Logická hodnota, která určuje, zda je balíček označen jako závislost pouze pro vývoj, což zabraňuje zahrnutí balíčku jako závislosti do jiných balíčků.</span><span class="sxs-lookup"><span data-stu-id="f25f2-277">A Boolean value that specifies whether the package is marked as a development-only dependency, which prevents the package from being included as a dependency in other packages.</span></span> <span data-ttu-id="f25f2-278">S PackageReference (NuGet 4.8+) tento příznak také znamená, že prostředky v době kompilace jsou vyloučeny z kompilace.</span><span class="sxs-lookup"><span data-stu-id="f25f2-278">With PackageReference (NuGet 4.8+), this flag also means that compile-time assets are excluded from compilation.</span></span> <span data-ttu-id="f25f2-279">Další informace naleznete v [tématu DevelopmentDependency support for PackageReference](https://github.com/NuGet/Home/wiki/DevelopmentDependency-support-for-PackageReference).</span><span class="sxs-lookup"><span data-stu-id="f25f2-279">For more information, see [DevelopmentDependency support for PackageReference](https://github.com/NuGet/Home/wiki/DevelopmentDependency-support-for-PackageReference).</span></span>

### <a name="packagelicenseexpression"></a><span data-ttu-id="f25f2-280">PackageLicenseExpression</span><span class="sxs-lookup"><span data-stu-id="f25f2-280">PackageLicenseExpression</span></span>

<span data-ttu-id="f25f2-281">Identifikátor nebo výraz [licence SPDX.](https://spdx.org/licenses/)</span><span class="sxs-lookup"><span data-stu-id="f25f2-281">An [SPDX license identifier](https://spdx.org/licenses/) or expression.</span></span> <span data-ttu-id="f25f2-282">Například, `Apache-2.0`.</span><span class="sxs-lookup"><span data-stu-id="f25f2-282">For example, `Apache-2.0`.</span></span>

<span data-ttu-id="f25f2-283">Zde je úplný seznam [identifikátorů licencí SPDX](https://spdx.org/licenses/).</span><span class="sxs-lookup"><span data-stu-id="f25f2-283">Here is the complete list of [SPDX license identifiers](https://spdx.org/licenses/).</span></span> <span data-ttu-id="f25f2-284">NuGet.org přijímá pouze licence schválené OSI nebo FSF při použití výrazu typu licence.</span><span class="sxs-lookup"><span data-stu-id="f25f2-284">NuGet.org accepts only OSI or FSF approved licenses when using license type expression.</span></span>

<span data-ttu-id="f25f2-285">Přesná syntaxe licenčních výrazů je popsána níže v [ABNF](https://tools.ietf.org/html/rfc5234).</span><span class="sxs-lookup"><span data-stu-id="f25f2-285">The exact syntax of the license expressions is described below in [ABNF](https://tools.ietf.org/html/rfc5234).</span></span>

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
> <span data-ttu-id="f25f2-286">Pouze jeden `PackageLicenseExpression` `PackageLicenseFile` z `PackageLicenseUrl` , a lze zadat současně.</span><span class="sxs-lookup"><span data-stu-id="f25f2-286">Only one of `PackageLicenseExpression`, `PackageLicenseFile` and `PackageLicenseUrl` can be specified at a time.</span></span>

### <a name="packagelicensefile"></a><span data-ttu-id="f25f2-287">Soubor PackageLicenseFile</span><span class="sxs-lookup"><span data-stu-id="f25f2-287">PackageLicenseFile</span></span>

<span data-ttu-id="f25f2-288">Cesta k licenčnímu souboru v rámci balíčku, pokud používáte licenci, které nebyl přiřazen identifikátor `PackageLicenseExpression` SPDX, nebo se jedná o vlastní licenci (v opačném případě je upřednostňována)</span><span class="sxs-lookup"><span data-stu-id="f25f2-288">Path to a license file within the package if you are using a license that hasn’t been assigned an SPDX identifier, or it is a custom license (Otherwise `PackageLicenseExpression` is preferred)</span></span>

<span data-ttu-id="f25f2-289">Nahrazuje `PackageLicenseUrl`, nelze kombinovat s `PackageLicenseExpression`aplikacemi a vyžaduje sady Visual Studio verze 15.9.4 a .NET SDK 2.1.502 nebo 2.2.101 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="f25f2-289">Replaces `PackageLicenseUrl`, can't be combined with `PackageLicenseExpression`, and requires Visual Studio version 15.9.4 and .NET SDK 2.1.502 or 2.2.101 or newer.</span></span>

<span data-ttu-id="f25f2-290">Budete muset zajistit, že licenční soubor je zabalen přidáním explicitně do projektu, například použití:</span><span class="sxs-lookup"><span data-stu-id="f25f2-290">You will need to ensure the license file is packed by adding it explicitly to the project, example usage:</span></span>

```xml
<PropertyGroup>
  <PackageLicenseFile>LICENSE.txt</PackageLicenseFile>
</PropertyGroup>
<ItemGroup>
  <None Include="licenses\LICENSE.txt" Pack="true" PackagePath="$(PackageLicenseFile)"/>
</ItemGroup>
```

### <a name="packagelicenseurl"></a><span data-ttu-id="f25f2-291">Adresa PackageLicenseUrl</span><span class="sxs-lookup"><span data-stu-id="f25f2-291">PackageLicenseUrl</span></span>

<span data-ttu-id="f25f2-292">Adresa URL licence, která se vztahuje na balíček.</span><span class="sxs-lookup"><span data-stu-id="f25f2-292">A URL to the license that is applicable to the package.</span></span> <span data-ttu-id="f25f2-293">(_zastaralé od Visual Studio 15.9.4, .NET SDK 2.1.502 a 2.2.101_)</span><span class="sxs-lookup"><span data-stu-id="f25f2-293">(_deprecated since Visual Studio 15.9.4, .NET SDK 2.1.502 and 2.2.101_)</span></span>

### <a name="packageiconurl"></a><span data-ttu-id="f25f2-294">Adresa PackageIconUrl</span><span class="sxs-lookup"><span data-stu-id="f25f2-294">PackageIconUrl</span></span>

<span data-ttu-id="f25f2-295">Adresa URL obrázku 64 x 64 s průhledným pozadím, která se má použít jako ikona balíčku v zobrazení uživatelského prostředí.</span><span class="sxs-lookup"><span data-stu-id="f25f2-295">A URL for a 64x64 image with transparent background to use as the icon for the package in UI display.</span></span>

### <a name="packagereleasenotes"></a><span data-ttu-id="f25f2-296">Poznámky k vydání balíčku</span><span class="sxs-lookup"><span data-stu-id="f25f2-296">PackageReleaseNotes</span></span>

<span data-ttu-id="f25f2-297">Poznámky k uvolnění balíčku.</span><span class="sxs-lookup"><span data-stu-id="f25f2-297">Release notes for the package.</span></span>

### <a name="packagetags"></a><span data-ttu-id="f25f2-298">Tagy balíčků</span><span class="sxs-lookup"><span data-stu-id="f25f2-298">PackageTags</span></span>

<span data-ttu-id="f25f2-299">Středník-oddělený seznam značek, který označuje balíček.</span><span class="sxs-lookup"><span data-stu-id="f25f2-299">A semicolon-delimited list of tags that designates the package.</span></span>

### <a name="packageoutputpath"></a><span data-ttu-id="f25f2-300">PackageOutputPath</span><span class="sxs-lookup"><span data-stu-id="f25f2-300">PackageOutputPath</span></span>

<span data-ttu-id="f25f2-301">Určuje výstupní cestu, ve které bude vynechán balíček.</span><span class="sxs-lookup"><span data-stu-id="f25f2-301">Determines the output path in which the packed package will be dropped.</span></span> <span data-ttu-id="f25f2-302">Výchozí je `$(OutputPath)`.</span><span class="sxs-lookup"><span data-stu-id="f25f2-302">Default is `$(OutputPath)`.</span></span>

### <a name="includesymbols"></a><span data-ttu-id="f25f2-303">Zahrnout symboly</span><span class="sxs-lookup"><span data-stu-id="f25f2-303">IncludeSymbols</span></span>
<span data-ttu-id="f25f2-304">Tato logická hodnota označuje, zda balíček by měl vytvořit další symboly balíček při projektu je zabalen.</span><span class="sxs-lookup"><span data-stu-id="f25f2-304">This Boolean value indicates whether the package should create an additional symbols package when the project is packed.</span></span> <span data-ttu-id="f25f2-305">Formát balíčku symbolů je řízen `SymbolPackageFormat` vlastností.</span><span class="sxs-lookup"><span data-stu-id="f25f2-305">The symbols package's format is controlled by the `SymbolPackageFormat` property.</span></span>

### <a name="symbolpackageformat"></a><span data-ttu-id="f25f2-306">SymbolPackageFormat</span><span class="sxs-lookup"><span data-stu-id="f25f2-306">SymbolPackageFormat</span></span>
<span data-ttu-id="f25f2-307">Určuje formát balíčku symbolů.</span><span class="sxs-lookup"><span data-stu-id="f25f2-307">Specifies the format of the symbols package.</span></span> <span data-ttu-id="f25f2-308">Pokud "symbols.nupkg", balíček starších symbolů bude vytvořen s příponou *.symbols.nupkg* obsahující pdbs, dll a další výstupní soubory.</span><span class="sxs-lookup"><span data-stu-id="f25f2-308">If "symbols.nupkg", a legacy symbols package will be created with a *.symbols.nupkg* extension containing PDBs, DLLs, and other output files.</span></span> <span data-ttu-id="f25f2-309">Pokud "snupkg", bude vytvořen balíček symbolů snupkg obsahující přenosné PD.</span><span class="sxs-lookup"><span data-stu-id="f25f2-309">If "snupkg", a snupkg symbol package will be created containing the portable PDBs.</span></span> <span data-ttu-id="f25f2-310">Výchozí hodnota je "symbols.nupkg".</span><span class="sxs-lookup"><span data-stu-id="f25f2-310">Default is "symbols.nupkg".</span></span>

### <a name="includesource"></a><span data-ttu-id="f25f2-311">IncludeSource</span><span class="sxs-lookup"><span data-stu-id="f25f2-311">IncludeSource</span></span>

<span data-ttu-id="f25f2-312">Tato logická hodnota označuje, zda by měl proces balení vytvořit zdrojový balíček.</span><span class="sxs-lookup"><span data-stu-id="f25f2-312">This Boolean value indicates whether the pack process should create a source package.</span></span> <span data-ttu-id="f25f2-313">Zdrojový balíček obsahuje zdrojový kód knihovny, stejně jako soubory PDB.</span><span class="sxs-lookup"><span data-stu-id="f25f2-313">The source package contains the library's source code as well as PDB files.</span></span> <span data-ttu-id="f25f2-314">Zdrojové soubory jsou `src/ProjectName` umístěny pod adresářem ve výsledném souboru balíčku.</span><span class="sxs-lookup"><span data-stu-id="f25f2-314">Source files are put under the `src/ProjectName` directory in the resulting package file.</span></span>

### <a name="istool"></a><span data-ttu-id="f25f2-315">Istool</span><span class="sxs-lookup"><span data-stu-id="f25f2-315">IsTool</span></span>

<span data-ttu-id="f25f2-316">Určuje, zda budou všechny výstupní soubory zkopírovány do složky *nástrojů* namísto složky *lib.*</span><span class="sxs-lookup"><span data-stu-id="f25f2-316">Specifies whether all output files are copied to the *tools* folder instead of the *lib* folder.</span></span> <span data-ttu-id="f25f2-317">To se liší `DotNetCliTool`od , který `PackageType` je určen nastavením v souboru *.csproj.*</span><span class="sxs-lookup"><span data-stu-id="f25f2-317">This is different from a `DotNetCliTool`, which is specified by setting the `PackageType` in the *.csproj* file.</span></span>

### <a name="repositoryurl"></a><span data-ttu-id="f25f2-318">Adresa úložiště</span><span class="sxs-lookup"><span data-stu-id="f25f2-318">RepositoryUrl</span></span>

<span data-ttu-id="f25f2-319">Určuje adresu URL úložiště, kde se nachází zdrojový kód pro balíček nebo ze kterého je právě setožován.</span><span class="sxs-lookup"><span data-stu-id="f25f2-319">Specifies the URL for the repository where the source code for the package resides and/or from which it's being built.</span></span>

### <a name="repositorytype"></a><span data-ttu-id="f25f2-320">Typ úložiště</span><span class="sxs-lookup"><span data-stu-id="f25f2-320">RepositoryType</span></span>

<span data-ttu-id="f25f2-321">Určuje typ úložiště.</span><span class="sxs-lookup"><span data-stu-id="f25f2-321">Specifies the type of the repository.</span></span> <span data-ttu-id="f25f2-322">Výchozí hodnota je "git".</span><span class="sxs-lookup"><span data-stu-id="f25f2-322">Default is "git".</span></span>

### <a name="repositorybranch"></a><span data-ttu-id="f25f2-323">Pobočka úložiště</span><span class="sxs-lookup"><span data-stu-id="f25f2-323">RepositoryBranch</span></span>
<span data-ttu-id="f25f2-324">Určuje název zdrojové větve v úložišti.</span><span class="sxs-lookup"><span data-stu-id="f25f2-324">Specifies the name of the source branch in the repository.</span></span> <span data-ttu-id="f25f2-325">Když je projekt zabalen v balíčku NuGet, je přidán do metadat balíčku.</span><span class="sxs-lookup"><span data-stu-id="f25f2-325">When the project is packaged in a NuGet package, it's added to the package metadata.</span></span>

### <a name="repositorycommit"></a><span data-ttu-id="f25f2-326">Potvrzení úložiště</span><span class="sxs-lookup"><span data-stu-id="f25f2-326">RepositoryCommit</span></span>
<span data-ttu-id="f25f2-327">Volitelné potvrzení úložiště nebo sada změn k označení zdroje, proti kterému byl balíček vytvořen.</span><span class="sxs-lookup"><span data-stu-id="f25f2-327">Optional repository commit or changeset to indicate which source the package was built against.</span></span> <span data-ttu-id="f25f2-328">`RepositoryUrl`musí být také určeny pro tuto vlastnost, které mají být zahrnuty.</span><span class="sxs-lookup"><span data-stu-id="f25f2-328">`RepositoryUrl` must also be specified for this property to be included.</span></span> <span data-ttu-id="f25f2-329">Když je projekt zabalen v balíčku NuGet, toto potvrzení nebo sada změn je přidán do metadat balíčku.</span><span class="sxs-lookup"><span data-stu-id="f25f2-329">When the project is packaged in a NuGet package, this commit or changeset is added to the package metadata.</span></span>

### <a name="nopackageanalysis"></a><span data-ttu-id="f25f2-330">NoPackageAnalysis</span><span class="sxs-lookup"><span data-stu-id="f25f2-330">NoPackageAnalysis</span></span>

<span data-ttu-id="f25f2-331">Určuje, že balíček by neměl spustit analýzu balíčku po sestavení balíčku.</span><span class="sxs-lookup"><span data-stu-id="f25f2-331">Specifies that pack should not run package analysis after building the package.</span></span>

### <a name="minclientversion"></a><span data-ttu-id="f25f2-332">MinClientVersion</span><span class="sxs-lookup"><span data-stu-id="f25f2-332">MinClientVersion</span></span>

<span data-ttu-id="f25f2-333">Určuje minimální verzi klienta NuGet, který může nainstalovat tento balíček vynucený nuget.exe a Správce balíčků sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f25f2-333">Specifies the minimum version of the NuGet client that can install this package, enforced by nuget.exe and the Visual Studio Package Manager.</span></span>

### <a name="includebuildoutput"></a><span data-ttu-id="f25f2-334">IncludeBuildOutput</span><span class="sxs-lookup"><span data-stu-id="f25f2-334">IncludeBuildOutput</span></span>

<span data-ttu-id="f25f2-335">Tato logická hodnota určuje, zda mají být výstupní sestavení zabalena do souboru *.nupkg* nebo ne.</span><span class="sxs-lookup"><span data-stu-id="f25f2-335">This Boolean value specifies whether the build output assemblies should be packed into the *.nupkg* file or not.</span></span>

### <a name="includecontentinpack"></a><span data-ttu-id="f25f2-336">IncludeContentInPack</span><span class="sxs-lookup"><span data-stu-id="f25f2-336">IncludeContentInPack</span></span>

<span data-ttu-id="f25f2-337">Tato logická hodnota určuje, zda budou `Content` všechny položky, které mají typ, automaticky zahrnuty do výsledného balíčku.</span><span class="sxs-lookup"><span data-stu-id="f25f2-337">This Boolean value specifies whether any items that have a type of `Content` will be included in the resulting package automatically.</span></span> <span data-ttu-id="f25f2-338">Výchozí formát je `true`.</span><span class="sxs-lookup"><span data-stu-id="f25f2-338">The default is `true`.</span></span>

### <a name="buildoutputtargetfolder"></a><span data-ttu-id="f25f2-339">Složka BuildOutputTargetFolder</span><span class="sxs-lookup"><span data-stu-id="f25f2-339">BuildOutputTargetFolder</span></span>

<span data-ttu-id="f25f2-340">Určuje složku, kam mají být umístěna výstupní sestavení.</span><span class="sxs-lookup"><span data-stu-id="f25f2-340">Specifies the folder where to place the output assemblies.</span></span> <span data-ttu-id="f25f2-341">Výstupní sestavení (a další výstupní soubory) jsou zkopírovány do příslušných složek architektury.</span><span class="sxs-lookup"><span data-stu-id="f25f2-341">The output assemblies (and other output files) are copied into their respective framework folders.</span></span>

### <a name="contenttargetfolders"></a><span data-ttu-id="f25f2-342">ContentTargetFolders</span><span class="sxs-lookup"><span data-stu-id="f25f2-342">ContentTargetFolders</span></span>

<span data-ttu-id="f25f2-343">Tato vlastnost určuje výchozí umístění, kam by měly být všechny soubory obsahu zadány, pokud `PackagePath` pro ně nejsou zadány.</span><span class="sxs-lookup"><span data-stu-id="f25f2-343">This property specifies the default location of where all the content files should go if `PackagePath` is not specified for them.</span></span> <span data-ttu-id="f25f2-344">Výchozí hodnota je "content;contentFiles".</span><span class="sxs-lookup"><span data-stu-id="f25f2-344">The default value is "content;contentFiles".</span></span>

### <a name="nuspecfile"></a><span data-ttu-id="f25f2-345">Soubor NuspecFile</span><span class="sxs-lookup"><span data-stu-id="f25f2-345">NuspecFile</span></span>

<span data-ttu-id="f25f2-346">Relativní nebo absolutní cesta k souboru *.nuspec,* který se používá pro balení.</span><span class="sxs-lookup"><span data-stu-id="f25f2-346">Relative or absolute path to the *.nuspec* file being used for packing.</span></span>

> [!NOTE]
> <span data-ttu-id="f25f2-347">Pokud je zadán soubor *.nuspec,* používá se **výhradně** pro informace o balení a žádné informace v projektech se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="f25f2-347">If the *.nuspec* file is specified, it's used **exclusively** for packaging information and any information in the projects is not used.</span></span>

### <a name="nuspecbasepath"></a><span data-ttu-id="f25f2-348">Aplikace NuspecBasePath</span><span class="sxs-lookup"><span data-stu-id="f25f2-348">NuspecBasePath</span></span>

<span data-ttu-id="f25f2-349">Základní cesta pro soubor *Nuspec.*</span><span class="sxs-lookup"><span data-stu-id="f25f2-349">Base path for the *.nuspec* file.</span></span>

### <a name="nuspecproperties"></a><span data-ttu-id="f25f2-350">NuspecProperties</span><span class="sxs-lookup"><span data-stu-id="f25f2-350">NuspecProperties</span></span>

<span data-ttu-id="f25f2-351">Středník oddělený seznam key=value pairs.</span><span class="sxs-lookup"><span data-stu-id="f25f2-351">Semicolon separated list of key=value pairs.</span></span>

## <a name="assemblyinfo-properties"></a><span data-ttu-id="f25f2-352">AssemblyInfo, vlastnosti</span><span class="sxs-lookup"><span data-stu-id="f25f2-352">AssemblyInfo properties</span></span>

<span data-ttu-id="f25f2-353">[Atributy sestavení,](../../standard/assembly/set-attributes.md) které byly obvykle přítomny v souboru *AssemblyInfo,* jsou nyní automaticky generovány z vlastností.</span><span class="sxs-lookup"><span data-stu-id="f25f2-353">[Assembly attributes](../../standard/assembly/set-attributes.md) that were typically present in an *AssemblyInfo* file are now automatically generated from properties.</span></span>

### <a name="properties-per-attribute"></a><span data-ttu-id="f25f2-354">Vlastnosti podle atributu</span><span class="sxs-lookup"><span data-stu-id="f25f2-354">Properties per attribute</span></span>

<span data-ttu-id="f25f2-355">Jak je znázorněno v následující tabulce, každý atribut má vlastnost, která řídí jeho obsah a jiný, který zakáže jeho generování:</span><span class="sxs-lookup"><span data-stu-id="f25f2-355">As shown in the following table, each attribute has a property that controls its content and another that disables its generation:</span></span>

| <span data-ttu-id="f25f2-356">Atribut</span><span class="sxs-lookup"><span data-stu-id="f25f2-356">Attribute</span></span>                                                      | <span data-ttu-id="f25f2-357">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="f25f2-357">Property</span></span>               | <span data-ttu-id="f25f2-358">Vlastnost zakázat</span><span class="sxs-lookup"><span data-stu-id="f25f2-358">Property to disable</span></span>                             |
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

<span data-ttu-id="f25f2-359">Poznámky:</span><span class="sxs-lookup"><span data-stu-id="f25f2-359">Notes:</span></span>

- <span data-ttu-id="f25f2-360">`AssemblyVersion`a `FileVersion` výchozí je vzít `$(Version)` hodnotu bez přípony.</span><span class="sxs-lookup"><span data-stu-id="f25f2-360">`AssemblyVersion` and `FileVersion` default is to take the value of `$(Version)` without suffix.</span></span> <span data-ttu-id="f25f2-361">Například pokud `$(Version)` `1.2.3-beta.4`je , pak `1.2.3`hodnota bude .</span><span class="sxs-lookup"><span data-stu-id="f25f2-361">For example, if `$(Version)` is `1.2.3-beta.4`, then the value would be `1.2.3`.</span></span>
- <span data-ttu-id="f25f2-362">`InformationalVersion`výchozí hodnota aplikace `$(Version)`.</span><span class="sxs-lookup"><span data-stu-id="f25f2-362">`InformationalVersion` defaults to the value of `$(Version)`.</span></span>
- <span data-ttu-id="f25f2-363">`InformationalVersion``$(SourceRevisionId)` pokud je vlastnost přítomna.</span><span class="sxs-lookup"><span data-stu-id="f25f2-363">`InformationalVersion` has `$(SourceRevisionId)` appended if the property is present.</span></span> <span data-ttu-id="f25f2-364">To může být `IncludeSourceRevisionInInformationalVersion`zakázáno pomocí .</span><span class="sxs-lookup"><span data-stu-id="f25f2-364">It can be disabled using `IncludeSourceRevisionInInformationalVersion`.</span></span>
- <span data-ttu-id="f25f2-365">`Copyright`a `Description` vlastnosti se také používají pro metadata NuGet.</span><span class="sxs-lookup"><span data-stu-id="f25f2-365">`Copyright` and `Description` properties are also used for NuGet metadata.</span></span>
- <span data-ttu-id="f25f2-366">`Configuration`je sdílena se všemi procesy sestavení a nastavena `--configuration` pomocí parametru `dotnet` příkazů.</span><span class="sxs-lookup"><span data-stu-id="f25f2-366">`Configuration` is shared with all the build process and set via the `--configuration` parameter of `dotnet` commands.</span></span>

### <a name="generateassemblyinfo"></a><span data-ttu-id="f25f2-367">Generovat informace o sestavení</span><span class="sxs-lookup"><span data-stu-id="f25f2-367">GenerateAssemblyInfo</span></span>

<span data-ttu-id="f25f2-368">Logická hodnota, která povoluje nebo zakazuje všechny generování AssemblyInfo.</span><span class="sxs-lookup"><span data-stu-id="f25f2-368">A Boolean that enable or disable all the AssemblyInfo generation.</span></span> <span data-ttu-id="f25f2-369">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="f25f2-369">The default value is `true`.</span></span>

### <a name="generatedassemblyinfofile"></a><span data-ttu-id="f25f2-370">Generovanou žádost ParlamentníHo Hromada</span><span class="sxs-lookup"><span data-stu-id="f25f2-370">GeneratedAssemblyInfoFile</span></span>

<span data-ttu-id="f25f2-371">Cesta generovaného souboru informací o sestavení.</span><span class="sxs-lookup"><span data-stu-id="f25f2-371">The path of the generated assembly info file.</span></span> <span data-ttu-id="f25f2-372">Výchozí soubor v `$(IntermediateOutputPath)` adresáři (obj).</span><span class="sxs-lookup"><span data-stu-id="f25f2-372">Default to a file in the `$(IntermediateOutputPath)` (obj) directory.</span></span>
