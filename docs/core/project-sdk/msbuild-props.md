---
title: Vlastnosti nástroje MSBuild pro Microsoft. NET. SDK
description: Referenční informace o vlastnostech a položkách MSBuild, které jsou srozumitelné pro .NET Core SDK.
ms.date: 02/14/2020
ms.topic: reference
ms.custom: updateeachrelease
ms.openlocfilehash: 39cbd18121d2b8659b2f5270f39624798f4ebbdc
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88810519"
---
# <a name="msbuild-reference-for-net-core-sdk-projects"></a><span data-ttu-id="09337-103">Referenční dokumentace nástroje MSBuild pro projekty .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="09337-103">MSBuild reference for .NET Core SDK projects</span></span>

<span data-ttu-id="09337-104">Tato stránka je odkazem na vlastnosti a položky nástroje MSBuild, které lze použít ke konfiguraci projektů .NET Core.</span><span class="sxs-lookup"><span data-stu-id="09337-104">This page is a reference for the MSBuild properties and items that you can use to configure .NET Core projects.</span></span>

> [!NOTE]
> <span data-ttu-id="09337-105">Tato stránka je Nedokončená práce a neobsahuje seznam všech užitečných vlastností MSBuild pro .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="09337-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET Core SDK.</span></span> <span data-ttu-id="09337-106">Seznam běžných vlastností MSBuild najdete v tématu [běžné vlastnosti MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="09337-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="09337-107">Vlastnosti architektury</span><span class="sxs-lookup"><span data-stu-id="09337-107">Framework properties</span></span>

- [<span data-ttu-id="09337-108">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="09337-108">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="09337-109">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="09337-109">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="09337-110">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="09337-110">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="09337-111">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="09337-111">TargetFramework</span></span>

<span data-ttu-id="09337-112">`TargetFramework`Vlastnost určuje cílovou verzi rozhraní .NET Framework pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="09337-112">The `TargetFramework` property specifies the target framework version for the app.</span></span> <span data-ttu-id="09337-113">Seznam platných monikerů cílového rozhraní Framework naleznete v tématu [cílové architektury v projektech ve stylu sady SDK](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="09337-113">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

<span data-ttu-id="09337-114">Další informace naleznete v tématu [cílová rozhraní v projektech ve stylu sady SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="09337-114">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="09337-115">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="09337-115">TargetFrameworks</span></span>

<span data-ttu-id="09337-116">Vlastnost použijte, `TargetFrameworks` Pokud chcete, aby aplikace byla cílena na více platforem.</span><span class="sxs-lookup"><span data-stu-id="09337-116">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="09337-117">Seznam platných monikerů cílového rozhraní Framework naleznete v tématu [cílové architektury v projektech ve stylu sady SDK](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="09337-117">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

> [!NOTE]
> <span data-ttu-id="09337-118">Tato vlastnost je ignorována `TargetFramework` , pokud je zadáno (jednotné).</span><span class="sxs-lookup"><span data-stu-id="09337-118">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
</PropertyGroup>
```

<span data-ttu-id="09337-119">Další informace naleznete v tématu [cílová rozhraní v projektech ve stylu sady SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="09337-119">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="09337-120">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="09337-120">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="09337-121">Tato vlastnost se vztahuje pouze na projekty používající `netstandard1.x` .</span><span class="sxs-lookup"><span data-stu-id="09337-121">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="09337-122">Neplatí pro projekty, které používají `netstandard2.x` .</span><span class="sxs-lookup"><span data-stu-id="09337-122">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="09337-123">Vlastnost použijte `NetStandardImplicitPackageVersion` , pokud chcete zadat verzi rozhraní, která je nižší než verze Metapackage.</span><span class="sxs-lookup"><span data-stu-id="09337-123">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the metapackage version.</span></span> <span data-ttu-id="09337-124">Soubor projektu v následujícím příkladu cílí, `netstandard1.3` ale používá 1.6.0 verzi `NETStandard.Library` .</span><span class="sxs-lookup"><span data-stu-id="09337-124">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netstandard1.3</TargetFramework>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

## <a name="package-properties"></a><span data-ttu-id="09337-125">Vlastnosti balíčku</span><span class="sxs-lookup"><span data-stu-id="09337-125">Package properties</span></span>

<span data-ttu-id="09337-126">Můžete zadat vlastnosti, například, `PackageId` , `PackageVersion` `PackageIcon` , `Title` a `Description` pro popis balíčku, který je vytvořen z projektu.</span><span class="sxs-lookup"><span data-stu-id="09337-126">You can specify properties such as `PackageId`, `PackageVersion`, `PackageIcon`, `Title`, and `Description` to describe the package that gets created from your project.</span></span> <span data-ttu-id="09337-127">Informace o těchto a dalších vlastnostech naleznete v tématu [targeting pack](/nuget/reference/msbuild-targets#pack-target).</span><span class="sxs-lookup"><span data-stu-id="09337-127">For information about these and other properties, see [pack target](/nuget/reference/msbuild-targets#pack-target).</span></span>

```xml
<PropertyGroup>
  ...
  <PackageId>ClassLibDotNetStandard</PackageId>
  <Version>1.0.0</Version>
  <Authors>John Doe</Authors>
  <Company>Contoso</Company>
</PropertyGroup>
```

## <a name="publish-properties-and-items"></a><span data-ttu-id="09337-128">Publikování vlastností a položek</span><span class="sxs-lookup"><span data-stu-id="09337-128">Publish properties and items</span></span>

- [<span data-ttu-id="09337-129">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="09337-129">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="09337-130">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="09337-130">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="09337-131">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="09337-131">TrimmerRootAssembly</span></span>](#trimmerrootassembly)
- [<span data-ttu-id="09337-132">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="09337-132">UseAppHost</span></span>](#useapphost)

### <a name="runtimeidentifier"></a><span data-ttu-id="09337-133">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="09337-133">RuntimeIdentifier</span></span>

<span data-ttu-id="09337-134">`RuntimeIdentifier`Vlastnost umožňuje zadat jeden [identifikátor modulu runtime (RID)](../rid-catalog.md) pro projekt.</span><span class="sxs-lookup"><span data-stu-id="09337-134">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="09337-135">Identifikátor RID umožňuje publikování samostatně zahrnutého nasazení.</span><span class="sxs-lookup"><span data-stu-id="09337-135">The RID enables publishing a self-contained deployment.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
</PropertyGroup>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="09337-136">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="09337-136">RuntimeIdentifiers</span></span>

<span data-ttu-id="09337-137">`RuntimeIdentifiers`Vlastnost umožňuje určit seznam [identifikátorů modulu runtime (identifikátorů RID)](../rid-catalog.md) oddělených středníky pro projekt.</span><span class="sxs-lookup"><span data-stu-id="09337-137">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="09337-138">Tuto vlastnost použijte v případě, že potřebujete publikovat více modulů runtime.</span><span class="sxs-lookup"><span data-stu-id="09337-138">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="09337-139">`RuntimeIdentifiers` se používá v čase obnovení, aby se zajistilo, že jsou správné prostředky v grafu.</span><span class="sxs-lookup"><span data-stu-id="09337-139">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="09337-140">`RuntimeIdentifier` (jednotné) může poskytovat rychlejší sestavení, pokud je potřeba jenom jeden modul runtime.</span><span class="sxs-lookup"><span data-stu-id="09337-140">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="trimmerrootassembly"></a><span data-ttu-id="09337-141">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="09337-141">TrimmerRootAssembly</span></span>

<span data-ttu-id="09337-142">`TrimmerRootAssembly`Položka umožňuje vyloučit sestavení z [*ořezávání*](../deploying/trim-self-contained.md).</span><span class="sxs-lookup"><span data-stu-id="09337-142">The `TrimmerRootAssembly` item lets you exclude an assembly from [*trimming*](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="09337-143">Oříznutí je proces odebrání nepoužívaných částí modulu runtime ze zabalené aplikace.</span><span class="sxs-lookup"><span data-stu-id="09337-143">Trimming is the process of removing unused parts of the runtime from a packaged application.</span></span> <span data-ttu-id="09337-144">V některých případech může oříznutí nesprávně odebrat požadované odkazy.</span><span class="sxs-lookup"><span data-stu-id="09337-144">In some cases, trimming might incorrectly remove required references.</span></span>

<span data-ttu-id="09337-145">Následující kód XML vylučuje `System.Security` sestavení z ořezávání.</span><span class="sxs-lookup"><span data-stu-id="09337-145">The following XML excludes the `System.Security` assembly from trimming.</span></span>

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

### <a name="useapphost"></a><span data-ttu-id="09337-146">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="09337-146">UseAppHost</span></span>

<span data-ttu-id="09337-147">`UseAppHost`Vlastnost byla představena ve verzi 2.1.400 .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="09337-147">The `UseAppHost` property was introduced in the 2.1.400 version of the .NET Core SDK.</span></span> <span data-ttu-id="09337-148">Určuje, zda je pro nasazení vytvořen nativní spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="09337-148">It controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="09337-149">Pro samostatně obsažená nasazení je vyžadován nativní spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="09337-149">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="09337-150">V rozhraní .NET Core 3,0 a novějších verzích je ve výchozím nastavení vytvořen spustitelný soubor závislý na rozhraní.</span><span class="sxs-lookup"><span data-stu-id="09337-150">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="09337-151">Nastavte `UseAppHost` vlastnost na hodnotu `false` pro zakázání generování spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="09337-151">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<PropertyGroup>
  <UseAppHost>false</UseAppHost>
</PropertyGroup>
```

<span data-ttu-id="09337-152">Další informace o nasazení naleznete v tématu [nasazení aplikace .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="09337-152">For more information about deployment, see [.NET Core application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="09337-153">Vlastnosti kompilace</span><span class="sxs-lookup"><span data-stu-id="09337-153">Compile properties</span></span>

- [<span data-ttu-id="09337-154">EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="09337-154">EmbeddedResourceUseDependentUponConvention</span></span>](#embeddedresourceusedependentuponconvention)
- [<span data-ttu-id="09337-155">Langversion –</span><span class="sxs-lookup"><span data-stu-id="09337-155">LangVersion</span></span>](#langversion)

### <a name="embeddedresourceusedependentuponconvention"></a><span data-ttu-id="09337-156">EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="09337-156">EmbeddedResourceUseDependentUponConvention</span></span>

<span data-ttu-id="09337-157">`EmbeddedResourceUseDependentUponConvention`Vlastnost určuje, zda jsou názvy souborů manifestu prostředku generovány z informací o typu ve zdrojových souborech, které jsou umístěny společně se soubory prostředků.</span><span class="sxs-lookup"><span data-stu-id="09337-157">The `EmbeddedResourceUseDependentUponConvention` property defines whether resource manifest file names are generated from type information in source files that are colocated with resource files.</span></span> <span data-ttu-id="09337-158">Například pokud je *Form1. resx* ve stejné složce jako *Form1.cs*a `EmbeddedResourceUseDependentUponConvention` je nastavena na `true` , vygenerovaný soubor *. Resources* převezme svůj název od prvního typu, který je definován v *Form1.cs*.</span><span class="sxs-lookup"><span data-stu-id="09337-158">For example, if *Form1.resx* is in the same folder as *Form1.cs*, and `EmbeddedResourceUseDependentUponConvention` is set to `true`, the generated *.resources* file takes its name from the first type that's defined in *Form1.cs*.</span></span> <span data-ttu-id="09337-159">Například pokud `MyNamespace.Form1` je první typ definovaný v *Form1.cs*, vygenerovaný název souboru je *MyNamespace. Form1. Resources*.</span><span class="sxs-lookup"><span data-stu-id="09337-159">For example, if `MyNamespace.Form1` is the first type defined in *Form1.cs*, the generated file name is *MyNamespace.Form1.resources*.</span></span>

> [!NOTE]
> <span data-ttu-id="09337-160">`LogicalName`V případě, že `ManifestResourceName` `DependentUpon` jsou pro položku zadána metadata, `EmbeddedResource` vygenerovaný název souboru manifestu pro tento soubor prostředků je založen na těchto metadatech.</span><span class="sxs-lookup"><span data-stu-id="09337-160">If `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for an `EmbeddedResource` item, the generated manifest file name for that resource file is based on that metadata instead.</span></span>

<span data-ttu-id="09337-161">Ve výchozím nastavení je v novém projektu .NET Core Tato vlastnost nastavena na `true` .</span><span class="sxs-lookup"><span data-stu-id="09337-161">By default, in a new .NET Core project, this property is set to `true`.</span></span> <span data-ttu-id="09337-162">Pokud `false` `LogicalName` je pro položku v souboru projektu nastavena na, a ne, nebo, je `ManifestResourceName` `DependentUpon` `EmbeddedResource` název souboru manifestu prostředku založen na kořenovém oboru názvů pro projekt a relativní cestě k souboru souboru *. resx* .</span><span class="sxs-lookup"><span data-stu-id="09337-162">If set to `false`, and no `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for the `EmbeddedResource` item in the project file, the resource manifest file name is based off the root namespace for the project and the relative file path to the *.resx* file.</span></span> <span data-ttu-id="09337-163">Další informace naleznete v tématu [jak jsou pojmenovány soubory manifestu prostředků](../resources/manifest-file-names.md).</span><span class="sxs-lookup"><span data-stu-id="09337-163">For more information, see [How resource manifest files are named](../resources/manifest-file-names.md).</span></span>

```xml
<PropertyGroup>
  <EmbeddedResourceUseDependentUponConvention>true</EmbeddedResourceUseDependentUponConvention>
</PropertyGroup>
```

### <a name="langversion"></a><span data-ttu-id="09337-164">Langversion –</span><span class="sxs-lookup"><span data-stu-id="09337-164">LangVersion</span></span>

<span data-ttu-id="09337-165">`LangVersion`Vlastnost umožňuje zadat konkrétní verzi programovacího jazyka.</span><span class="sxs-lookup"><span data-stu-id="09337-165">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="09337-166">Například pokud chcete mít přístup k funkcím verze Preview jazyka C#, nastavte `LangVersion` na `preview` .</span><span class="sxs-lookup"><span data-stu-id="09337-166">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<PropertyGroup>
  <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="09337-167">Další informace najdete v tématu [Správa verzí jazyka C#](../../csharp/language-reference/configure-language-version.md#override-a-default).</span><span class="sxs-lookup"><span data-stu-id="09337-167">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="code-analysis-properties"></a><span data-ttu-id="09337-168">Vlastnosti analýzy kódu</span><span class="sxs-lookup"><span data-stu-id="09337-168">Code analysis properties</span></span>

### <a name="analysislevel"></a><span data-ttu-id="09337-169">AnalysisLevel</span><span class="sxs-lookup"><span data-stu-id="09337-169">AnalysisLevel</span></span>

<span data-ttu-id="09337-170">`AnalysisLevel`Vlastnost umožňuje určit úroveň analýzy kódu.</span><span class="sxs-lookup"><span data-stu-id="09337-170">The `AnalysisLevel` property lets you specify a code analysis level.</span></span> <span data-ttu-id="09337-171">Například pokud chcete mít přístup k analyzátorům kódu ve verzi Preview, nastavte `AnalysisLevel` na `preview` .</span><span class="sxs-lookup"><span data-stu-id="09337-171">For example, if you want access to preview code analyzers, set `AnalysisLevel` to `preview`.</span></span> <span data-ttu-id="09337-172">Výchozí hodnota je `latest`.</span><span class="sxs-lookup"><span data-stu-id="09337-172">The default value is `latest`.</span></span>

```xml
<PropertyGroup>
  <AnalysisLevel>preview</AnalysisLevel>
</PropertyGroup>
```

<span data-ttu-id="09337-173">V následující tabulce jsou uvedeny dostupné možnosti.</span><span class="sxs-lookup"><span data-stu-id="09337-173">The following table shows the available options.</span></span>

| <span data-ttu-id="09337-174">Hodnota</span><span class="sxs-lookup"><span data-stu-id="09337-174">Value</span></span> | <span data-ttu-id="09337-175">Význam</span><span class="sxs-lookup"><span data-stu-id="09337-175">Meaning</span></span> |
|-|-|
| `latest` | <span data-ttu-id="09337-176">Použijí se nejnovější analyzátory kódu, které byly vydány.</span><span class="sxs-lookup"><span data-stu-id="09337-176">The latest code analyzers that have been released are used.</span></span> <span data-ttu-id="09337-177">Tato možnost je výchozí.</span><span class="sxs-lookup"><span data-stu-id="09337-177">This is the default.</span></span> |
| `preview` | <span data-ttu-id="09337-178">Používají se nejnovější analyzátory kódu, a to i v případě, že jsou ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="09337-178">The latest code analyzers are used, even if they are in preview.</span></span> |
| `5.0` | <span data-ttu-id="09337-179">Použije se sada pravidel, která byla povolena pro vydání .NET 5,0, i v případě, že jsou k dispozici novější pravidla.</span><span class="sxs-lookup"><span data-stu-id="09337-179">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |
| `5` | <span data-ttu-id="09337-180">Použije se sada pravidel, která byla povolena pro vydání .NET 5,0, i v případě, že jsou k dispozici novější pravidla.</span><span class="sxs-lookup"><span data-stu-id="09337-180">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |

### <a name="codeanalysistreatwarningsaserrors"></a><span data-ttu-id="09337-181">CodeAnalysisTreatWarningsAsErrors</span><span class="sxs-lookup"><span data-stu-id="09337-181">CodeAnalysisTreatWarningsAsErrors</span></span>

<span data-ttu-id="09337-182">`CodeAnalysisTreatWarningsAsErrors`Vlastnost umožňuje nakonfigurovat, zda by měla být upozornění analýzy kódu zpracována jako upozornění a přerušeno sestavení.</span><span class="sxs-lookup"><span data-stu-id="09337-182">The `CodeAnalysisTreatWarningsAsErrors` property lets you configure whether code analysis warnings should be treated as warnings and break the build.</span></span> <span data-ttu-id="09337-183">Použijete-li `-warnaserror` příznak při sestavování projektů, jsou upozornění [analýzy kódu .NET](../../fundamentals/productivity/code-analysis.md) také považována za chyby.</span><span class="sxs-lookup"><span data-stu-id="09337-183">If you use the `-warnaserror` flag when you build your projects, [.NET code analysis](../../fundamentals/productivity/code-analysis.md) warnings are also treated as errors.</span></span> <span data-ttu-id="09337-184">Pokud chcete, aby upozornění kompilátoru byla považována za chyby, můžete `CodeAnalysisTreatWarningsAsErrors` vlastnost MSBuild nastavit na `false` v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="09337-184">If you only want compiler warnings to be treated as errors, you can set the `CodeAnalysisTreatWarningsAsErrors` MSBuild property to `false` in your project file.</span></span>

```xml
<PropertyGroup>
  <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
</PropertyGroup>
```

### <a name="enablenetanalyzers"></a><span data-ttu-id="09337-185">EnableNETAnalyzers</span><span class="sxs-lookup"><span data-stu-id="09337-185">EnableNETAnalyzers</span></span>

<span data-ttu-id="09337-186">[Analýza kódu .NET](../../fundamentals/productivity/code-analysis.md) je ve výchozím nastavení povolená pro projekty, které cílí na .NET 5,0 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="09337-186">[.NET Code analysis](../../fundamentals/productivity/code-analysis.md) is enabled, by default, for projects that target .NET 5.0 or later.</span></span> <span data-ttu-id="09337-187">Můžete povolit analýzu kódu .NET pro projekty, které jsou cíleny na starší verze rozhraní .NET, nastavením `EnableNETAnalyzers` vlastnosti na hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="09337-187">You can enable .NET code analysis for projects that target earlier versions of .NET by setting the `EnableNETAnalyzers` property to true.</span></span> <span data-ttu-id="09337-188">Chcete-li zakázat analýzu kódu v jakémkoli projektu, nastavte tuto vlastnost na `false` .</span><span class="sxs-lookup"><span data-stu-id="09337-188">To disable code analysis in any project, set this property to `false`.</span></span>

```xml
<PropertyGroup>
  <EnableNETAnalyzers>true</EnableNETAnalyzers>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="09337-189">Další způsob, jak povolit analýzu kódu .NET v projektech, které cílí na verze .NET starší než .NET 5,0, je nastavit vlastnost [AnalysisLevel](#analysislevel) na hodnotu `latest` .</span><span class="sxs-lookup"><span data-stu-id="09337-189">Another way to enable .NET code analysis on projects that target .NET versions prior to .NET 5.0 is to set the [AnalysisLevel](#analysislevel) property to `latest`.</span></span>

## <a name="run-time-configuration-properties"></a><span data-ttu-id="09337-190">Vlastnosti konfigurace runtime</span><span class="sxs-lookup"><span data-stu-id="09337-190">Run-time configuration properties</span></span>

<span data-ttu-id="09337-191">Můžete nakonfigurovat některé chování za běhu zadáním vlastností MSBuild v souboru projektu aplikace.</span><span class="sxs-lookup"><span data-stu-id="09337-191">You can configure some run-time behaviors by specifying MSBuild properties in the project file of the app.</span></span> <span data-ttu-id="09337-192">Informace o jiných způsobech konfigurace chování za běhu najdete v tématu [nastavení konfigurace prostředí .NET Core](../run-time-config/index.md)runtime.</span><span class="sxs-lookup"><span data-stu-id="09337-192">For information about other ways of configuring run-time behavior, see [.NET Core run-time configuration settings](../run-time-config/index.md).</span></span>

- [<span data-ttu-id="09337-193">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="09337-193">ConcurrentGarbageCollection</span></span>](#concurrentgarbagecollection)
- [<span data-ttu-id="09337-194">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="09337-194">InvariantGlobalization</span></span>](#invariantglobalization)
- [<span data-ttu-id="09337-195">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="09337-195">RetainVMGarbageCollection</span></span>](#retainvmgarbagecollection)
- [<span data-ttu-id="09337-196">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="09337-196">ServerGarbageCollection</span></span>](#servergarbagecollection)
- [<span data-ttu-id="09337-197">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="09337-197">ThreadPoolMaxThreads</span></span>](#threadpoolmaxthreads)
- [<span data-ttu-id="09337-198">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="09337-198">ThreadPoolMinThreads</span></span>](#threadpoolminthreads)
- [<span data-ttu-id="09337-199">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="09337-199">TieredCompilation</span></span>](#tieredcompilation)
- [<span data-ttu-id="09337-200">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="09337-200">TieredCompilationQuickJit</span></span>](#tieredcompilationquickjit)
- [<span data-ttu-id="09337-201">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="09337-201">TieredCompilationQuickJitForLoops</span></span>](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a><span data-ttu-id="09337-202">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="09337-202">ConcurrentGarbageCollection</span></span>

<span data-ttu-id="09337-203">`ConcurrentGarbageCollection`Vlastnost konfiguruje, zda je povoleno [uvolňování paměti na pozadí (souběžně)](../../standard/garbage-collection/background-gc.md) .</span><span class="sxs-lookup"><span data-stu-id="09337-203">The `ConcurrentGarbageCollection` property configures whether [background (concurrent) garbage collection](../../standard/garbage-collection/background-gc.md) is enabled.</span></span> <span data-ttu-id="09337-204">Nastavte hodnotu na `false` Zakázat uvolňování paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="09337-204">Set the value to `false` to disable background garbage collection.</span></span> <span data-ttu-id="09337-205">Další informace najdete v tématu [GC na pozadí](../run-time-config/garbage-collector.md#background-gc).</span><span class="sxs-lookup"><span data-stu-id="09337-205">For more information, see [Background GC](../run-time-config/garbage-collector.md#background-gc).</span></span>

```xml
<PropertyGroup>
  <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
</PropertyGroup>
```

### <a name="invariantglobalization"></a><span data-ttu-id="09337-206">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="09337-206">InvariantGlobalization</span></span>

<span data-ttu-id="09337-207">`InvariantGlobalization`Vlastnost nakonfiguruje, jestli aplikace běží v režimu *invariantní globalizace* , což znamená, že nemá přístup k datům specifickým pro jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="09337-207">The `InvariantGlobalization` property configures whether the app runs in *globalization-invariant* mode, which means it doesn't have access to culture-specific data.</span></span> <span data-ttu-id="09337-208">Nastavte hodnotu pro `true` spuštění v režimu invariantní globalizace.</span><span class="sxs-lookup"><span data-stu-id="09337-208">Set the value to `true` to run in globalization-invariant mode.</span></span> <span data-ttu-id="09337-209">Další informace naleznete v tématu [invariantní režim](../run-time-config/globalization.md#invariant-mode).</span><span class="sxs-lookup"><span data-stu-id="09337-209">For more information, see [Invariant mode](../run-time-config/globalization.md#invariant-mode).</span></span>

```xml
<PropertyGroup>
  <InvariantGlobalization>true</InvariantGlobalization>
</PropertyGroup>
```

### <a name="retainvmgarbagecollection"></a><span data-ttu-id="09337-210">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="09337-210">RetainVMGarbageCollection</span></span>

<span data-ttu-id="09337-211">`RetainVMGarbageCollection`Vlastnost konfiguruje systém uvolňování paměti pro vložení odstraněných segmentů paměti v pohotovostním seznamu pro budoucí použití nebo uvolnění.</span><span class="sxs-lookup"><span data-stu-id="09337-211">The `RetainVMGarbageCollection` property configures the garbage collector to put deleted memory segments on a standby list for future use or release them.</span></span> <span data-ttu-id="09337-212">Nastavením hodnoty určíte `true` , aby systém uvolňování paměti umístil segmenty do seznamu pohotovostních hodnot.</span><span class="sxs-lookup"><span data-stu-id="09337-212">Setting the value to `true` tells the garbage collector to put the segments on a standby list.</span></span> <span data-ttu-id="09337-213">Další informace najdete v tématu [uchování virtuálního počítače](../run-time-config/garbage-collector.md#retain-vm).</span><span class="sxs-lookup"><span data-stu-id="09337-213">For more information, see [Retain VM](../run-time-config/garbage-collector.md#retain-vm).</span></span>

```xml
<PropertyGroup>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
</PropertyGroup>
```

### <a name="servergarbagecollection"></a><span data-ttu-id="09337-214">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="09337-214">ServerGarbageCollection</span></span>

<span data-ttu-id="09337-215">`ServerGarbageCollection`Vlastnost konfiguruje, zda aplikace používá [uvolňování paměti pracovní stanice nebo uvolňování paměti serveru](../../standard/garbage-collection/workstation-server-gc.md).</span><span class="sxs-lookup"><span data-stu-id="09337-215">The `ServerGarbageCollection` property configures whether the application uses [workstation garbage collection or server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span> <span data-ttu-id="09337-216">Nastavte hodnotu na `true` použít uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="09337-216">Set the value to `true` to use server garbage collection.</span></span> <span data-ttu-id="09337-217">Další informace najdete v tématu [pracovní stanice vs. Server](../run-time-config/garbage-collector.md#workstation-vs-server).</span><span class="sxs-lookup"><span data-stu-id="09337-217">For more information, see [Workstation vs. server](../run-time-config/garbage-collector.md#workstation-vs-server).</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

### <a name="threadpoolmaxthreads"></a><span data-ttu-id="09337-218">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="09337-218">ThreadPoolMaxThreads</span></span>

<span data-ttu-id="09337-219">`ThreadPoolMaxThreads`Vlastnost konfiguruje maximální počet vláken pro fond pracovních vláken.</span><span class="sxs-lookup"><span data-stu-id="09337-219">The `ThreadPoolMaxThreads` property configures the maximum number of threads for the worker thread pool.</span></span> <span data-ttu-id="09337-220">Další informace najdete v tématu [maximální počet vláken](../run-time-config/threading.md#maximum-threads).</span><span class="sxs-lookup"><span data-stu-id="09337-220">For more information, see [Maximum threads](../run-time-config/threading.md#maximum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
</PropertyGroup>
```

### <a name="threadpoolminthreads"></a><span data-ttu-id="09337-221">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="09337-221">ThreadPoolMinThreads</span></span>

<span data-ttu-id="09337-222">`ThreadPoolMinThreads`Vlastnost konfiguruje minimální počet vláken pro fond pracovních vláken.</span><span class="sxs-lookup"><span data-stu-id="09337-222">The `ThreadPoolMinThreads` property configures the minimum number of threads for the worker thread pool.</span></span> <span data-ttu-id="09337-223">Další informace najdete v tématu [minimální počet vláken](../run-time-config/threading.md#minimum-threads).</span><span class="sxs-lookup"><span data-stu-id="09337-223">For more information, see [Minimum threads](../run-time-config/threading.md#minimum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
</PropertyGroup>
```

### <a name="tieredcompilation"></a><span data-ttu-id="09337-224">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="09337-224">TieredCompilation</span></span>

<span data-ttu-id="09337-225">`TieredCompilation`Vlastnost určuje, zda kompilátor JIT (just-in-time) používá [vrstvenou kompilaci](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="09337-225">The `TieredCompilation` property configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="09337-226">Nastavte hodnotu na `false` Zakázat vrstvenou kompilaci.</span><span class="sxs-lookup"><span data-stu-id="09337-226">Set the value to `false` to disable tiered compilation.</span></span> <span data-ttu-id="09337-227">Další informace najdete v tématu [vrstvená kompilace](../run-time-config/compilation.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="09337-227">For more information, see [Tiered compilation](../run-time-config/compilation.md#tiered-compilation).</span></span>

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

### <a name="tieredcompilationquickjit"></a><span data-ttu-id="09337-228">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="09337-228">TieredCompilationQuickJit</span></span>

<span data-ttu-id="09337-229">`TieredCompilationQuickJit`Vlastnost konfiguruje, zda kompilátor JIT používá rychlou JIT.</span><span class="sxs-lookup"><span data-stu-id="09337-229">The `TieredCompilationQuickJit` property configures whether the JIT compiler uses quick JIT.</span></span> <span data-ttu-id="09337-230">Nastavením hodnoty na `false` zakážete rychlou JIT.</span><span class="sxs-lookup"><span data-stu-id="09337-230">Set the value to `false` to disable quick JIT.</span></span> <span data-ttu-id="09337-231">Další informace najdete v tématu [rychlá JIT](../run-time-config/compilation.md#quick-jit).</span><span class="sxs-lookup"><span data-stu-id="09337-231">For more information, see [Quick JIT](../run-time-config/compilation.md#quick-jit).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

### <a name="tieredcompilationquickjitforloops"></a><span data-ttu-id="09337-232">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="09337-232">TieredCompilationQuickJitForLoops</span></span>

<span data-ttu-id="09337-233">`TieredCompilationQuickJitForLoops`Vlastnost konfiguruje, zda kompilátor JIT používá rychlou JIT v metodách, které obsahují smyčky.</span><span class="sxs-lookup"><span data-stu-id="09337-233">The `TieredCompilationQuickJitForLoops` property configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span> <span data-ttu-id="09337-234">Nastavte hodnotu na, `true` Chcete-li povolit rychlou JIT v metodách, které obsahují smyčky.</span><span class="sxs-lookup"><span data-stu-id="09337-234">Set the value to `true` to enable quick JIT on methods that contain loops.</span></span> <span data-ttu-id="09337-235">Další informace najdete v tématu [rychlá JIT pro smyčky](../run-time-config/compilation.md#quick-jit-for-loops).</span><span class="sxs-lookup"><span data-stu-id="09337-235">For more information, see [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
</PropertyGroup>
```

## <a name="reference-properties-and-items"></a><span data-ttu-id="09337-236">Odkazování vlastností a položek</span><span class="sxs-lookup"><span data-stu-id="09337-236">Reference properties and items</span></span>

- [<span data-ttu-id="09337-237">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="09337-237">AssetTargetFallback</span></span>](#assettargetfallback)
- [<span data-ttu-id="09337-238">PackageReference</span><span class="sxs-lookup"><span data-stu-id="09337-238">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="09337-239">ProjectReference</span><span class="sxs-lookup"><span data-stu-id="09337-239">ProjectReference</span></span>](#projectreference)
- [<span data-ttu-id="09337-240">Odkaz</span><span class="sxs-lookup"><span data-stu-id="09337-240">Reference</span></span>](#reference)
- [<span data-ttu-id="09337-241">Obnovit vlastnosti</span><span class="sxs-lookup"><span data-stu-id="09337-241">Restore properties</span></span>](#restore-properties)

### <a name="assettargetfallback"></a><span data-ttu-id="09337-242">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="09337-242">AssetTargetFallback</span></span>

<span data-ttu-id="09337-243">`AssetTargetFallback`Vlastnost umožňuje zadat další kompatibilní verze rozhraní pro odkazy na projekt a balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="09337-243">The `AssetTargetFallback` property lets you specify additional compatible framework versions for project references and NuGet packages.</span></span> <span data-ttu-id="09337-244">Pokud například zadáte závislost balíčku pomocí, `PackageReference` ale tento balíček neobsahuje prostředky, které jsou kompatibilní s vašimi projekty `TargetFramework` , `AssetTargetFallback` vlastnost se dostane do hry.</span><span class="sxs-lookup"><span data-stu-id="09337-244">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="09337-245">Kompatibilita odkazovaného balíčku je znovu zkontrolována pomocí každé cílové architektury, která je určena v `AssetTargetFallback` .</span><span class="sxs-lookup"><span data-stu-id="09337-245">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span>

<span data-ttu-id="09337-246">Můžete nastavit `AssetTargetFallback` vlastnost na jednu nebo více [cílových verzí rozhraní .NET Framework](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="09337-246">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<PropertyGroup>
  <AssetTargetFallback>net461</AssetTargetFallback>
</PropertyGroup>
```

### <a name="packagereference"></a><span data-ttu-id="09337-247">PackageReference</span><span class="sxs-lookup"><span data-stu-id="09337-247">PackageReference</span></span>

<span data-ttu-id="09337-248">`PackageReference`Položka definuje odkaz na balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="09337-248">The `PackageReference` item defines a reference to a NuGet package.</span></span>

<span data-ttu-id="09337-249">`Include`Atribut určuje ID balíčku.</span><span class="sxs-lookup"><span data-stu-id="09337-249">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="09337-250">`Version`Atribut určuje verzi nebo rozsah verzí.</span><span class="sxs-lookup"><span data-stu-id="09337-250">The `Version` attribute specifies the version or version range.</span></span> <span data-ttu-id="09337-251">Informace o tom, jak zadat minimální verzi, maximální verzi, rozsah nebo přesnou shodu, najdete v tématu [rozsahy verzí](/nuget/concepts/package-versioning#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="09337-251">For information about how to specify a minimum version, maximum version, range, or exact match, see [Version ranges](/nuget/concepts/package-versioning#version-ranges).</span></span> <span data-ttu-id="09337-252">Do odkazu na projekt můžete také přidat následující metadata: `IncludeAssets` , `ExcludeAssets` a `PrivateAssets` .</span><span class="sxs-lookup"><span data-stu-id="09337-252">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="09337-253">Fragment souboru projektu v následujícím příkladu odkazuje na balíček [System. Runtime](https://www.nuget.org/packages/System.Runtime/) .</span><span class="sxs-lookup"><span data-stu-id="09337-253">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="System.Runtime" Version="4.3.0" />
</ItemGroup>
```

<span data-ttu-id="09337-254">Další informace naleznete v tématu [odkazy na balíčky v souborech projektu](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="09337-254">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="projectreference"></a><span data-ttu-id="09337-255">ProjectReference</span><span class="sxs-lookup"><span data-stu-id="09337-255">ProjectReference</span></span>

<span data-ttu-id="09337-256">`ProjectReference`Položka definuje odkaz na jiný projekt.</span><span class="sxs-lookup"><span data-stu-id="09337-256">The `ProjectReference` item defines a reference to another project.</span></span> <span data-ttu-id="09337-257">Odkazovaný projekt je přidán jako závislost balíčku NuGet, to znamená, že je zpracována jako `PackageReference` .</span><span class="sxs-lookup"><span data-stu-id="09337-257">The referenced project is added as a NuGet package dependency, that is, it's treated the same as a `PackageReference`.</span></span>

<span data-ttu-id="09337-258">`Include`Atribut určuje cestu k projektu.</span><span class="sxs-lookup"><span data-stu-id="09337-258">The `Include` attribute specifies the path to the project.</span></span> <span data-ttu-id="09337-259">Do odkazu na projekt můžete také přidat následující metadata: `IncludeAssets` , `ExcludeAssets` a `PrivateAssets` .</span><span class="sxs-lookup"><span data-stu-id="09337-259">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="09337-260">Fragment souboru projektu v následujícím příkladu odkazuje na projekt s názvem `Project2` .</span><span class="sxs-lookup"><span data-stu-id="09337-260">The project file snippet in the following example references a project named `Project2`.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\Project2.csproj" />
</ItemGroup>
```

### <a name="reference"></a><span data-ttu-id="09337-261">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="09337-261">Reference</span></span>

<span data-ttu-id="09337-262">`Reference`Položka definuje odkaz na soubor sestavení.</span><span class="sxs-lookup"><span data-stu-id="09337-262">The `Reference` item defines a reference to an assembly file.</span></span>

<span data-ttu-id="09337-263">`Include`Atribut určuje název souboru a `HintPath` metadata určují cestu k sestavení.</span><span class="sxs-lookup"><span data-stu-id="09337-263">The `Include` attribute specifies the name of the file, and the `HintPath` metadata specifies the path to the assembly.</span></span>

```xml
<ItemGroup>
  <Reference Include="MyAssembly">
    <HintPath>..\..\Assemblies\MyAssembly.dll</HintPath>
  </Reference>
</ItemGroup>
```

### <a name="restore-properties"></a><span data-ttu-id="09337-264">Obnovit vlastnosti</span><span class="sxs-lookup"><span data-stu-id="09337-264">Restore properties</span></span>

<span data-ttu-id="09337-265">Při obnovení odkazovaného balíčku se nainstaluje všechny jeho přímé závislosti a všechny závislosti těchto závislostí.</span><span class="sxs-lookup"><span data-stu-id="09337-265">Restoring a referenced package installs all of its direct dependencies and all the dependencies of those dependencies.</span></span> <span data-ttu-id="09337-266">Obnovení balíčku můžete přizpůsobit zadáním vlastností, jako jsou `RestorePackagesPath` a `RestoreIgnoreFailedSources` .</span><span class="sxs-lookup"><span data-stu-id="09337-266">You can customize package restoration by specifying properties such as `RestorePackagesPath` and `RestoreIgnoreFailedSources`.</span></span> <span data-ttu-id="09337-267">Další informace o těchto a dalších vlastnostech naleznete v tématu [Restore Target](/nuget/reference/msbuild-targets#restore-target).</span><span class="sxs-lookup"><span data-stu-id="09337-267">For more information about these and other properties, see [restore target](/nuget/reference/msbuild-targets#restore-target).</span></span>

```xml
<PropertyGroup>
  <RestoreIgnoreFailedSource>true</RestoreIgnoreFailedSource>
</PropertyGroup>
```

## <a name="see-also"></a><span data-ttu-id="09337-268">Viz také</span><span class="sxs-lookup"><span data-stu-id="09337-268">See also</span></span>

- [<span data-ttu-id="09337-269">Referenční dokumentace schématu MSBuild</span><span class="sxs-lookup"><span data-stu-id="09337-269">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="09337-270">Běžné vlastnosti nástroje MSBuild</span><span class="sxs-lookup"><span data-stu-id="09337-270">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="09337-271">Vlastnosti nástroje MSBuild pro balíček NuGet</span><span class="sxs-lookup"><span data-stu-id="09337-271">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="09337-272">Vlastnosti nástroje MSBuild pro obnovení NuGet</span><span class="sxs-lookup"><span data-stu-id="09337-272">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="09337-273">Přizpůsobení sestavení</span><span class="sxs-lookup"><span data-stu-id="09337-273">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
