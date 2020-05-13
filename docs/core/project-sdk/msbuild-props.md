---
title: Vlastnosti nástroje MSBuild pro Microsoft. NET. SDK
description: Referenční informace o vlastnostech a položkách MSBuild, které jsou srozumitelné pro .NET Core SDK.
ms.date: 02/14/2020
ms.topic: reference
ms.openlocfilehash: cda56b3e23592a341d9fe672fc1f1530adcdab49
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206113"
---
# <a name="msbuild-reference-for-net-core-sdk-projects"></a><span data-ttu-id="404cd-103">Referenční dokumentace nástroje MSBuild pro projekty .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="404cd-103">MSBuild reference for .NET Core SDK projects</span></span>

<span data-ttu-id="404cd-104">Tato stránka je odkazem na vlastnosti a položky nástroje MSBuild, které lze použít ke konfiguraci projektů .NET Core.</span><span class="sxs-lookup"><span data-stu-id="404cd-104">This page is a reference for the MSBuild properties and items that you can use to configure .NET Core projects.</span></span>

> [!NOTE]
> <span data-ttu-id="404cd-105">Tato stránka je Nedokončená práce a neobsahuje seznam všech užitečných vlastností MSBuild pro .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="404cd-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET Core SDK.</span></span> <span data-ttu-id="404cd-106">Seznam běžných vlastností MSBuild najdete v tématu [běžné vlastnosti MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="404cd-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="404cd-107">Vlastnosti architektury</span><span class="sxs-lookup"><span data-stu-id="404cd-107">Framework properties</span></span>

- [<span data-ttu-id="404cd-108">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="404cd-108">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="404cd-109">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="404cd-109">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="404cd-110">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="404cd-110">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="404cd-111">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="404cd-111">TargetFramework</span></span>

<span data-ttu-id="404cd-112">`TargetFramework`Vlastnost určuje cílovou verzi rozhraní .NET Framework pro aplikaci, která implicitně odkazuje na [Metapackage](../packages.md#metapackages).</span><span class="sxs-lookup"><span data-stu-id="404cd-112">The `TargetFramework` property specifies the target framework version for the app, which implicitly references a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="404cd-113">Seznam platných monikerů cílového rozhraní Framework naleznete v tématu [cílové architektury v projektech ve stylu sady SDK](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="404cd-113">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

<span data-ttu-id="404cd-114">Další informace naleznete v tématu [cílová rozhraní v projektech ve stylu sady SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="404cd-114">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="404cd-115">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="404cd-115">TargetFrameworks</span></span>

<span data-ttu-id="404cd-116">Vlastnost použijte, `TargetFrameworks` Pokud chcete, aby aplikace byla cílena na více platforem.</span><span class="sxs-lookup"><span data-stu-id="404cd-116">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="404cd-117">Seznam platných monikerů cílového rozhraní Framework naleznete v tématu [cílové architektury v projektech ve stylu sady SDK](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="404cd-117">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

> [!NOTE]
> <span data-ttu-id="404cd-118">Tato vlastnost je ignorována `TargetFramework` , pokud je zadáno (jednotné).</span><span class="sxs-lookup"><span data-stu-id="404cd-118">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
</PropertyGroup>
```

<span data-ttu-id="404cd-119">Další informace naleznete v tématu [cílová rozhraní v projektech ve stylu sady SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="404cd-119">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="404cd-120">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="404cd-120">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="404cd-121">Tato vlastnost se vztahuje pouze na projekty používající `netstandard1.x` .</span><span class="sxs-lookup"><span data-stu-id="404cd-121">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="404cd-122">Neplatí pro projekty, které používají `netstandard2.x` .</span><span class="sxs-lookup"><span data-stu-id="404cd-122">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="404cd-123">Vlastnost použijte `NetStandardImplicitPackageVersion` , pokud chcete zadat verzi rozhraní, která je nižší než verze [Metapackage](../packages.md#metapackages) .</span><span class="sxs-lookup"><span data-stu-id="404cd-123">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the [metapackage](../packages.md#metapackages) version.</span></span> <span data-ttu-id="404cd-124">Soubor projektu v následujícím příkladu cílí, `netstandard1.3` ale používá 1.6.0 verzi `NETStandard.Library` .</span><span class="sxs-lookup"><span data-stu-id="404cd-124">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netstandard1.3</TargetFramework>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

## <a name="package-properties"></a><span data-ttu-id="404cd-125">Vlastnosti balíčku</span><span class="sxs-lookup"><span data-stu-id="404cd-125">Package properties</span></span>

<span data-ttu-id="404cd-126">Můžete zadat vlastnosti, například, `PackageId` , `PackageVersion` `PackageIcon` , `Title` a `Description` pro popis balíčku, který je vytvořen z projektu.</span><span class="sxs-lookup"><span data-stu-id="404cd-126">You can specify properties such as `PackageId`, `PackageVersion`, `PackageIcon`, `Title`, and `Description` to describe the package that gets created from your project.</span></span> <span data-ttu-id="404cd-127">Informace o těchto a dalších vlastnostech naleznete v tématu [targeting pack](/nuget/reference/msbuild-targets#pack-target).</span><span class="sxs-lookup"><span data-stu-id="404cd-127">For information about these and other properties, see [pack target](/nuget/reference/msbuild-targets#pack-target).</span></span>

```xml
<PropertyGroup>
  ...
  <PackageId>ClassLibDotNetStandard</PackageId>
  <Version>1.0.0</Version>
  <Authors>John Doe</Authors>
  <Company>Contoso</Company>
</PropertyGroup>
```

## <a name="publish-properties-and-items"></a><span data-ttu-id="404cd-128">Publikování vlastností a položek</span><span class="sxs-lookup"><span data-stu-id="404cd-128">Publish properties and items</span></span>

- [<span data-ttu-id="404cd-129">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="404cd-129">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="404cd-130">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="404cd-130">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="404cd-131">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="404cd-131">TrimmerRootAssembly</span></span>](#trimmerrootassembly)
- [<span data-ttu-id="404cd-132">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="404cd-132">UseAppHost</span></span>](#useapphost)

### <a name="runtimeidentifier"></a><span data-ttu-id="404cd-133">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="404cd-133">RuntimeIdentifier</span></span>

<span data-ttu-id="404cd-134">`RuntimeIdentifier`Vlastnost umožňuje zadat jeden [identifikátor modulu runtime (RID)](../rid-catalog.md) pro projekt.</span><span class="sxs-lookup"><span data-stu-id="404cd-134">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="404cd-135">Identifikátor RID umožňuje publikování samostatně zahrnutého nasazení.</span><span class="sxs-lookup"><span data-stu-id="404cd-135">The RID enables publishing a self-contained deployment.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
</PropertyGroup>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="404cd-136">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="404cd-136">RuntimeIdentifiers</span></span>

<span data-ttu-id="404cd-137">`RuntimeIdentifiers`Vlastnost umožňuje určit seznam [identifikátorů modulu runtime (identifikátorů RID)](../rid-catalog.md) oddělených středníky pro projekt.</span><span class="sxs-lookup"><span data-stu-id="404cd-137">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="404cd-138">Tuto vlastnost použijte v případě, že potřebujete publikovat více modulů runtime.</span><span class="sxs-lookup"><span data-stu-id="404cd-138">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="404cd-139">`RuntimeIdentifiers`se používá v čase obnovení, aby se zajistilo, že jsou správné prostředky v grafu.</span><span class="sxs-lookup"><span data-stu-id="404cd-139">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="404cd-140">`RuntimeIdentifier`(jednotné) může poskytovat rychlejší sestavení, pokud je potřeba jenom jeden modul runtime.</span><span class="sxs-lookup"><span data-stu-id="404cd-140">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="trimmerrootassembly"></a><span data-ttu-id="404cd-141">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="404cd-141">TrimmerRootAssembly</span></span>

<span data-ttu-id="404cd-142">`TrimmerRootAssembly`Položka umožňuje vyloučit sestavení z [*ořezávání*](../deploying/trim-self-contained.md).</span><span class="sxs-lookup"><span data-stu-id="404cd-142">The `TrimmerRootAssembly` item lets you exclude an assembly from [*trimming*](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="404cd-143">Oříznutí je proces odebrání nepoužívaných částí modulu runtime ze zabalené aplikace.</span><span class="sxs-lookup"><span data-stu-id="404cd-143">Trimming is the process of removing unused parts of the runtime from a packaged application.</span></span> <span data-ttu-id="404cd-144">V některých případech může oříznutí nesprávně odebrat požadované odkazy.</span><span class="sxs-lookup"><span data-stu-id="404cd-144">In some cases, trimming might incorrectly remove required references.</span></span>

<span data-ttu-id="404cd-145">Následující kód XML vylučuje `System.Security` sestavení z ořezávání.</span><span class="sxs-lookup"><span data-stu-id="404cd-145">The following XML excludes the `System.Security` assembly from trimming.</span></span>

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

### <a name="useapphost"></a><span data-ttu-id="404cd-146">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="404cd-146">UseAppHost</span></span>

<span data-ttu-id="404cd-147">`UseAppHost`Vlastnost byla představena ve verzi 2.1.400 .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="404cd-147">The `UseAppHost` property was introduced in the 2.1.400 version of the .NET Core SDK.</span></span> <span data-ttu-id="404cd-148">Určuje, zda je pro nasazení vytvořen nativní spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="404cd-148">It controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="404cd-149">Pro samostatně obsažená nasazení je vyžadován nativní spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="404cd-149">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="404cd-150">V rozhraní .NET Core 3,0 a novějších verzích je ve výchozím nastavení vytvořen spustitelný soubor závislý na rozhraní.</span><span class="sxs-lookup"><span data-stu-id="404cd-150">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="404cd-151">Nastavte `UseAppHost` vlastnost na hodnotu `false` pro zakázání generování spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="404cd-151">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<PropertyGroup>
  <UseAppHost>false</UseAppHost>
</PropertyGroup>
```

<span data-ttu-id="404cd-152">Další informace o nasazení naleznete v tématu [nasazení aplikace .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="404cd-152">For more information about deployment, see [.NET Core application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="404cd-153">Vlastnosti kompilace</span><span class="sxs-lookup"><span data-stu-id="404cd-153">Compile properties</span></span>

- [<span data-ttu-id="404cd-154">EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="404cd-154">EmbeddedResourceUseDependentUponConvention</span></span>](#embeddedresourceusedependentuponconvention)
- [<span data-ttu-id="404cd-155">Langversion –</span><span class="sxs-lookup"><span data-stu-id="404cd-155">LangVersion</span></span>](#langversion)

### <a name="embeddedresourceusedependentuponconvention"></a><span data-ttu-id="404cd-156">EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="404cd-156">EmbeddedResourceUseDependentUponConvention</span></span>

<span data-ttu-id="404cd-157">`EmbeddedResourceUseDependentUponConvention`Vlastnost určuje, zda jsou názvy souborů manifestu prostředku generovány z informací o typu ve zdrojových souborech, které jsou umístěny společně se soubory prostředků.</span><span class="sxs-lookup"><span data-stu-id="404cd-157">The `EmbeddedResourceUseDependentUponConvention` property defines whether resource manifest file names are generated from type information in source files that are colocated with resource files.</span></span> <span data-ttu-id="404cd-158">Například pokud je *Form1. resx* ve stejné složce jako *Form1.cs*a `EmbeddedResourceUseDependentUponConvention` je nastavena na `true` , vygenerovaný soubor *. Resources* převezme svůj název od prvního typu, který je definován v *Form1.cs*.</span><span class="sxs-lookup"><span data-stu-id="404cd-158">For example, if *Form1.resx* is in the same folder as *Form1.cs*, and `EmbeddedResourceUseDependentUponConvention` is set to `true`, the generated *.resources* file takes its name from the first type that's defined in *Form1.cs*.</span></span> <span data-ttu-id="404cd-159">Například pokud `MyNamespace.Form1` je první typ definovaný v *Form1.cs*, vygenerovaný název souboru je *MyNamespace. Form1. Resources*.</span><span class="sxs-lookup"><span data-stu-id="404cd-159">For example, if `MyNamespace.Form1` is the first type defined in *Form1.cs*, the generated file name is *MyNamespace.Form1.resources*.</span></span>

> [!NOTE]
> <span data-ttu-id="404cd-160">`LogicalName`V případě, že `ManifestResourceName` `DependentUpon` jsou pro položku zadána metadata, `EmbeddedResource` vygenerovaný název souboru manifestu pro tento soubor prostředků je založen na těchto metadatech.</span><span class="sxs-lookup"><span data-stu-id="404cd-160">If `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for an `EmbeddedResource` item, the generated manifest file name for that resource file is based on that metadata instead.</span></span>

<span data-ttu-id="404cd-161">Ve výchozím nastavení je v novém projektu .NET Core Tato vlastnost nastavena na `true` .</span><span class="sxs-lookup"><span data-stu-id="404cd-161">By default, in a new .NET Core project, this property is set to `true`.</span></span> <span data-ttu-id="404cd-162">Pokud `false` `LogicalName` je pro položku v souboru projektu nastavena na, a ne, nebo, je `ManifestResourceName` `DependentUpon` `EmbeddedResource` název souboru manifestu prostředku založen na kořenovém oboru názvů pro projekt a relativní cestě k souboru souboru *. resx* .</span><span class="sxs-lookup"><span data-stu-id="404cd-162">If set to `false`, and no `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for the `EmbeddedResource` item in the project file, the resource manifest file name is based off the root namespace for the project and the relative file path to the *.resx* file.</span></span> <span data-ttu-id="404cd-163">Další informace naleznete v tématu [jak jsou pojmenovány soubory manifestu prostředků](../resources/manifest-file-names.md).</span><span class="sxs-lookup"><span data-stu-id="404cd-163">For more information, see [How resource manifest files are named](../resources/manifest-file-names.md).</span></span>

```xml
<PropertyGroup>
  <EmbeddedResourceUseDependentUponConvention>true</EmbeddedResourceUseDependentUponConvention>
</PropertyGroup>
```

### <a name="langversion"></a><span data-ttu-id="404cd-164">Langversion –</span><span class="sxs-lookup"><span data-stu-id="404cd-164">LangVersion</span></span>

<span data-ttu-id="404cd-165">`LangVersion`Vlastnost umožňuje zadat konkrétní verzi programovacího jazyka.</span><span class="sxs-lookup"><span data-stu-id="404cd-165">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="404cd-166">Například pokud chcete mít přístup k funkcím verze Preview jazyka C#, nastavte `LangVersion` na `preview` .</span><span class="sxs-lookup"><span data-stu-id="404cd-166">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<PropertyGroup>
  <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="404cd-167">Další informace najdete v tématu [Správa verzí jazyka C#](../../csharp/language-reference/configure-language-version.md#override-a-default).</span><span class="sxs-lookup"><span data-stu-id="404cd-167">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="run-time-configuration-properties"></a><span data-ttu-id="404cd-168">Vlastnosti konfigurace runtime</span><span class="sxs-lookup"><span data-stu-id="404cd-168">Run-time configuration properties</span></span>

<span data-ttu-id="404cd-169">Můžete nakonfigurovat některé chování za běhu zadáním vlastností MSBuild v souboru projektu aplikace.</span><span class="sxs-lookup"><span data-stu-id="404cd-169">You can configure some run-time behaviors by specifying MSBuild properties in the project file of the app.</span></span> <span data-ttu-id="404cd-170">Informace o jiných způsobech konfigurace chování za běhu najdete v tématu [nastavení konfigurace prostředí .NET Core](../run-time-config/index.md)runtime.</span><span class="sxs-lookup"><span data-stu-id="404cd-170">For information about other ways of configuring run-time behavior, see [.NET Core run-time configuration settings](../run-time-config/index.md).</span></span>

- [<span data-ttu-id="404cd-171">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="404cd-171">ConcurrentGarbageCollection</span></span>](#concurrentgarbagecollection)
- [<span data-ttu-id="404cd-172">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="404cd-172">InvariantGlobalization</span></span>](#invariantglobalization)
- [<span data-ttu-id="404cd-173">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="404cd-173">RetainVMGarbageCollection</span></span>](#retainvmgarbagecollection)
- [<span data-ttu-id="404cd-174">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="404cd-174">ServerGarbageCollection</span></span>](#servergarbagecollection)
- [<span data-ttu-id="404cd-175">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="404cd-175">ThreadPoolMaxThreads</span></span>](#threadpoolmaxthreads)
- [<span data-ttu-id="404cd-176">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="404cd-176">ThreadPoolMinThreads</span></span>](#threadpoolminthreads)
- [<span data-ttu-id="404cd-177">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="404cd-177">TieredCompilation</span></span>](#tieredcompilation)
- [<span data-ttu-id="404cd-178">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="404cd-178">TieredCompilationQuickJit</span></span>](#tieredcompilationquickjit)
- [<span data-ttu-id="404cd-179">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="404cd-179">TieredCompilationQuickJitForLoops</span></span>](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a><span data-ttu-id="404cd-180">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="404cd-180">ConcurrentGarbageCollection</span></span>

<span data-ttu-id="404cd-181">`ConcurrentGarbageCollection`Vlastnost konfiguruje, zda je povoleno [uvolňování paměti na pozadí (souběžně)](../../standard/garbage-collection/background-gc.md) .</span><span class="sxs-lookup"><span data-stu-id="404cd-181">The `ConcurrentGarbageCollection` property configures whether [background (concurrent) garbage collection](../../standard/garbage-collection/background-gc.md) is enabled.</span></span> <span data-ttu-id="404cd-182">Nastavte hodnotu na `false` Zakázat uvolňování paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="404cd-182">Set the value to `false` to disable background garbage collection.</span></span> <span data-ttu-id="404cd-183">Další informace najdete v tématu [System. GC. souběžné/COMPlus_gcConcurrent](../run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent).</span><span class="sxs-lookup"><span data-stu-id="404cd-183">For more information, see [System.GC.Concurrent/COMPlus_gcConcurrent](../run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent).</span></span>

```xml
<PropertyGroup>
  <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
</PropertyGroup>
```

### <a name="invariantglobalization"></a><span data-ttu-id="404cd-184">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="404cd-184">InvariantGlobalization</span></span>

<span data-ttu-id="404cd-185">`InvariantGlobalization`Vlastnost nakonfiguruje, jestli aplikace běží v režimu *invariantní globalizace* , což znamená, že nemá přístup k datům specifickým pro jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="404cd-185">The `InvariantGlobalization` property configures whether the app runs in *globalization-invariant* mode, which means it doesn't have access to culture-specific data.</span></span> <span data-ttu-id="404cd-186">Nastavte hodnotu pro `true` spuštění v režimu invariantní globalizace.</span><span class="sxs-lookup"><span data-stu-id="404cd-186">Set the value to `true` to run in globalization-invariant mode.</span></span> <span data-ttu-id="404cd-187">Další informace naleznete v tématu [invariantní režim](../run-time-config/globalization.md#invariant-mode).</span><span class="sxs-lookup"><span data-stu-id="404cd-187">For more information, see [Invariant mode](../run-time-config/globalization.md#invariant-mode).</span></span>

```xml
<PropertyGroup>
  <InvariantGlobalization>true</InvariantGlobalization>
</PropertyGroup>
```

### <a name="retainvmgarbagecollection"></a><span data-ttu-id="404cd-188">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="404cd-188">RetainVMGarbageCollection</span></span>

<span data-ttu-id="404cd-189">`RetainVMGarbageCollection`Vlastnost konfiguruje systém uvolňování paměti pro vložení odstraněných segmentů paměti v pohotovostním seznamu pro budoucí použití nebo uvolnění.</span><span class="sxs-lookup"><span data-stu-id="404cd-189">The `RetainVMGarbageCollection` property configures the garbage collector to put deleted memory segments on a standby list for future use or release them.</span></span> <span data-ttu-id="404cd-190">Nastavením hodnoty určíte `true` , aby systém uvolňování paměti umístil segmenty do seznamu pohotovostních hodnot.</span><span class="sxs-lookup"><span data-stu-id="404cd-190">Setting the value to `true` tells the garbage collector to put the segments on a standby list.</span></span> <span data-ttu-id="404cd-191">Další informace najdete v tématu [System. GC. RetainVM/COMPlus_GCRetainVM](../run-time-config/garbage-collector.md#systemgcretainvmcomplus_gcretainvm).</span><span class="sxs-lookup"><span data-stu-id="404cd-191">For more information, see [System.GC.RetainVM/COMPlus_GCRetainVM](../run-time-config/garbage-collector.md#systemgcretainvmcomplus_gcretainvm).</span></span>

```xml
<PropertyGroup>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
</PropertyGroup>
```

### <a name="servergarbagecollection"></a><span data-ttu-id="404cd-192">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="404cd-192">ServerGarbageCollection</span></span>

<span data-ttu-id="404cd-193">`ServerGarbageCollection`Vlastnost konfiguruje, zda aplikace používá [uvolňování paměti pracovní stanice nebo uvolňování paměti serveru](../../standard/garbage-collection/workstation-server-gc.md).</span><span class="sxs-lookup"><span data-stu-id="404cd-193">The `ServerGarbageCollection` property configures whether the application uses [workstation garbage collection or server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span> <span data-ttu-id="404cd-194">Nastavte hodnotu na `true` použít uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="404cd-194">Set the value to `true` to use server garbage collection.</span></span> <span data-ttu-id="404cd-195">Další informace najdete v tématu [System. GC. Server/COMPlus_gcServer](../run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).</span><span class="sxs-lookup"><span data-stu-id="404cd-195">For more information, see [System.GC.Server/COMPlus_gcServer](../run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

### <a name="threadpoolmaxthreads"></a><span data-ttu-id="404cd-196">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="404cd-196">ThreadPoolMaxThreads</span></span>

<span data-ttu-id="404cd-197">`ThreadPoolMaxThreads`Vlastnost konfiguruje maximální počet vláken pro fond pracovních vláken.</span><span class="sxs-lookup"><span data-stu-id="404cd-197">The `ThreadPoolMaxThreads` property configures the maximum number of threads for the worker thread pool.</span></span> <span data-ttu-id="404cd-198">Další informace najdete v tématu [maximální počet vláken](../run-time-config/threading.md#maximum-threads).</span><span class="sxs-lookup"><span data-stu-id="404cd-198">For more information, see [Maximum threads](../run-time-config/threading.md#maximum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
</PropertyGroup>
```

### <a name="threadpoolminthreads"></a><span data-ttu-id="404cd-199">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="404cd-199">ThreadPoolMinThreads</span></span>

<span data-ttu-id="404cd-200">`ThreadPoolMinThreads`Vlastnost konfiguruje minimální počet vláken pro fond pracovních vláken.</span><span class="sxs-lookup"><span data-stu-id="404cd-200">The `ThreadPoolMinThreads` property configures the minimum number of threads for the worker thread pool.</span></span> <span data-ttu-id="404cd-201">Další informace najdete v tématu [minimální počet vláken](../run-time-config/threading.md#minimum-threads).</span><span class="sxs-lookup"><span data-stu-id="404cd-201">For more information, see [Minimum threads](../run-time-config/threading.md#minimum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
</PropertyGroup>
```

### <a name="tieredcompilation"></a><span data-ttu-id="404cd-202">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="404cd-202">TieredCompilation</span></span>

<span data-ttu-id="404cd-203">`TieredCompilation`Vlastnost určuje, zda kompilátor JIT (just-in-time) používá [vrstvenou kompilaci](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="404cd-203">The `TieredCompilation` property configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="404cd-204">Nastavte hodnotu na `false` Zakázat vrstvenou kompilaci.</span><span class="sxs-lookup"><span data-stu-id="404cd-204">Set the value to `false` to disable tiered compilation.</span></span> <span data-ttu-id="404cd-205">Další informace najdete v tématu [vrstvená kompilace](../run-time-config/compilation.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="404cd-205">For more information, see [Tiered compilation](../run-time-config/compilation.md#tiered-compilation).</span></span>

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

### <a name="tieredcompilationquickjit"></a><span data-ttu-id="404cd-206">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="404cd-206">TieredCompilationQuickJit</span></span>

<span data-ttu-id="404cd-207">`TieredCompilationQuickJit`Vlastnost konfiguruje, zda kompilátor JIT používá rychlou JIT.</span><span class="sxs-lookup"><span data-stu-id="404cd-207">The `TieredCompilationQuickJit` property configures whether the JIT compiler uses quick JIT.</span></span> <span data-ttu-id="404cd-208">Nastavením hodnoty na `false` zakážete rychlou JIT.</span><span class="sxs-lookup"><span data-stu-id="404cd-208">Set the value to `false` to disable quick JIT.</span></span> <span data-ttu-id="404cd-209">Další informace najdete v tématu [rychlá JIT](../run-time-config/compilation.md#quick-jit).</span><span class="sxs-lookup"><span data-stu-id="404cd-209">For more information, see [Quick JIT](../run-time-config/compilation.md#quick-jit).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

### <a name="tieredcompilationquickjitforloops"></a><span data-ttu-id="404cd-210">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="404cd-210">TieredCompilationQuickJitForLoops</span></span>

<span data-ttu-id="404cd-211">`TieredCompilationQuickJitForLoops`Vlastnost konfiguruje, zda kompilátor JIT používá rychlou JIT v metodách, které obsahují smyčky.</span><span class="sxs-lookup"><span data-stu-id="404cd-211">The `TieredCompilationQuickJitForLoops` property configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span> <span data-ttu-id="404cd-212">Nastavte hodnotu na, `true` Chcete-li povolit rychlou JIT v metodách, které obsahují smyčky.</span><span class="sxs-lookup"><span data-stu-id="404cd-212">Set the value to `true` to enable quick JIT on methods that contain loops.</span></span> <span data-ttu-id="404cd-213">Další informace najdete v tématu [rychlá JIT pro smyčky](../run-time-config/compilation.md#quick-jit-for-loops).</span><span class="sxs-lookup"><span data-stu-id="404cd-213">For more information, see [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
</PropertyGroup>
```

## <a name="reference-properties-and-items"></a><span data-ttu-id="404cd-214">Odkazování vlastností a položek</span><span class="sxs-lookup"><span data-stu-id="404cd-214">Reference properties and items</span></span>

- [<span data-ttu-id="404cd-215">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="404cd-215">AssetTargetFallback</span></span>](#assettargetfallback)
- [<span data-ttu-id="404cd-216">PackageReference</span><span class="sxs-lookup"><span data-stu-id="404cd-216">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="404cd-217">ProjectReference</span><span class="sxs-lookup"><span data-stu-id="404cd-217">ProjectReference</span></span>](#projectreference)
- [<span data-ttu-id="404cd-218">Odkaz</span><span class="sxs-lookup"><span data-stu-id="404cd-218">Reference</span></span>](#reference)
- [<span data-ttu-id="404cd-219">Obnovit vlastnosti</span><span class="sxs-lookup"><span data-stu-id="404cd-219">Restore properties</span></span>](#restore-properties)

### <a name="assettargetfallback"></a><span data-ttu-id="404cd-220">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="404cd-220">AssetTargetFallback</span></span>

<span data-ttu-id="404cd-221">`AssetTargetFallback`Vlastnost umožňuje zadat další kompatibilní verze rozhraní pro odkazy na projekt a balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="404cd-221">The `AssetTargetFallback` property lets you specify additional compatible framework versions for project references and NuGet packages.</span></span> <span data-ttu-id="404cd-222">Pokud například zadáte závislost balíčku pomocí, `PackageReference` ale tento balíček neobsahuje prostředky, které jsou kompatibilní s vašimi projekty `TargetFramework` , `AssetTargetFallback` vlastnost se dostane do hry.</span><span class="sxs-lookup"><span data-stu-id="404cd-222">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="404cd-223">Kompatibilita odkazovaného balíčku je znovu zkontrolována pomocí každé cílové architektury, která je určena v `AssetTargetFallback` .</span><span class="sxs-lookup"><span data-stu-id="404cd-223">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span>

<span data-ttu-id="404cd-224">Můžete nastavit `AssetTargetFallback` vlastnost na jednu nebo více [cílových verzí rozhraní .NET Framework](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="404cd-224">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<PropertyGroup>
  <AssetTargetFallback>net461</AssetTargetFallback>
</PropertyGroup>
```

### <a name="packagereference"></a><span data-ttu-id="404cd-225">PackageReference</span><span class="sxs-lookup"><span data-stu-id="404cd-225">PackageReference</span></span>

<span data-ttu-id="404cd-226">`PackageReference`Položka definuje odkaz na balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="404cd-226">The `PackageReference` item defines a reference to a NuGet package.</span></span> <span data-ttu-id="404cd-227">Například můžete chtít odkazovat na jeden balíček místo [Metapackage](../packages.md#metapackages).</span><span class="sxs-lookup"><span data-stu-id="404cd-227">For example, you may want to reference a single package instead of a [metapackage](../packages.md#metapackages).</span></span>

<span data-ttu-id="404cd-228">`Include`Atribut určuje ID balíčku.</span><span class="sxs-lookup"><span data-stu-id="404cd-228">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="404cd-229">`Version`Atribut určuje verzi nebo rozsah verzí.</span><span class="sxs-lookup"><span data-stu-id="404cd-229">The `Version` attribute specifies the version or version range.</span></span> <span data-ttu-id="404cd-230">Informace o tom, jak zadat minimální verzi, maximální verzi, rozsah nebo přesnou shodu, najdete v tématu [rozsahy verzí](/nuget/concepts/package-versioning#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="404cd-230">For information about how to specify a minimum version, maximum version, range, or exact match, see [Version ranges](/nuget/concepts/package-versioning#version-ranges).</span></span> <span data-ttu-id="404cd-231">Do odkazu na projekt můžete také přidat následující metadata: `IncludeAssets` , `ExcludeAssets` a `PrivateAssets` .</span><span class="sxs-lookup"><span data-stu-id="404cd-231">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="404cd-232">Fragment souboru projektu v následujícím příkladu odkazuje na balíček [System. Runtime](https://www.nuget.org/packages/System.Runtime/) .</span><span class="sxs-lookup"><span data-stu-id="404cd-232">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="System.Runtime" Version="4.3.0" />
</ItemGroup>
```

<span data-ttu-id="404cd-233">Další informace naleznete v tématu [odkazy na balíčky v souborech projektu](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="404cd-233">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="projectreference"></a><span data-ttu-id="404cd-234">ProjectReference</span><span class="sxs-lookup"><span data-stu-id="404cd-234">ProjectReference</span></span>

<span data-ttu-id="404cd-235">`ProjectReference`Položka definuje odkaz na jiný projekt.</span><span class="sxs-lookup"><span data-stu-id="404cd-235">The `ProjectReference` item defines a reference to another project.</span></span> <span data-ttu-id="404cd-236">Odkazovaný projekt je přidán jako závislost balíčku NuGet, to znamená, že je zpracována jako `PackageReference` .</span><span class="sxs-lookup"><span data-stu-id="404cd-236">The referenced project is added as a NuGet package dependency, that is, it's treated the same as a `PackageReference`.</span></span>

<span data-ttu-id="404cd-237">`Include`Atribut určuje cestu k projektu.</span><span class="sxs-lookup"><span data-stu-id="404cd-237">The `Include` attribute specifies the path to the project.</span></span> <span data-ttu-id="404cd-238">Do odkazu na projekt můžete také přidat následující metadata: `IncludeAssets` , `ExcludeAssets` a `PrivateAssets` .</span><span class="sxs-lookup"><span data-stu-id="404cd-238">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="404cd-239">Fragment souboru projektu v následujícím příkladu odkazuje na projekt s názvem `Project2` .</span><span class="sxs-lookup"><span data-stu-id="404cd-239">The project file snippet in the following example references a project named `Project2`.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\Project2.csproj" />
</ItemGroup>
```

### <a name="reference"></a><span data-ttu-id="404cd-240">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="404cd-240">Reference</span></span>

<span data-ttu-id="404cd-241">`Reference`Položka definuje odkaz na soubor sestavení.</span><span class="sxs-lookup"><span data-stu-id="404cd-241">The `Reference` item defines a reference to an assembly file.</span></span>

<span data-ttu-id="404cd-242">`Include`Atribut určuje název souboru a `HintPath` metadata určují cestu k sestavení.</span><span class="sxs-lookup"><span data-stu-id="404cd-242">The `Include` attribute specifies the name of the file, and the `HintPath` metadata specifies the path to the assembly.</span></span>

```xml
<ItemGroup>
  <Reference Include="MyAssembly">
    <HintPath>..\..\Assemblies\MyAssembly.dll</HintPath>
  </Reference>
</ItemGroup>
```

### <a name="restore-properties"></a><span data-ttu-id="404cd-243">Obnovit vlastnosti</span><span class="sxs-lookup"><span data-stu-id="404cd-243">Restore properties</span></span>

<span data-ttu-id="404cd-244">Při obnovení odkazovaného balíčku se nainstaluje všechny jeho přímé závislosti a všechny závislosti těchto závislostí.</span><span class="sxs-lookup"><span data-stu-id="404cd-244">Restoring a referenced package installs all of its direct dependencies and all the dependencies of those dependencies.</span></span> <span data-ttu-id="404cd-245">Obnovení balíčku můžete přizpůsobit zadáním vlastností, jako jsou `RestorePackagesPath` a `RestoreIgnoreFailedSources` .</span><span class="sxs-lookup"><span data-stu-id="404cd-245">You can customize package restoration by specifying properties such as `RestorePackagesPath` and `RestoreIgnoreFailedSources`.</span></span> <span data-ttu-id="404cd-246">Další informace o těchto a dalších vlastnostech naleznete v tématu [Restore Target](/nuget/reference/msbuild-targets#restore-target).</span><span class="sxs-lookup"><span data-stu-id="404cd-246">For more information about these and other properties, see [restore target](/nuget/reference/msbuild-targets#restore-target).</span></span>

```xml
<PropertyGroup>
  <RestoreIgnoreFailedSource>true</RestoreIgnoreFailedSource>
</PropertyGroup>
```

## <a name="see-also"></a><span data-ttu-id="404cd-247">Viz také</span><span class="sxs-lookup"><span data-stu-id="404cd-247">See also</span></span>

- [<span data-ttu-id="404cd-248">Referenční dokumentace schématu MSBuild</span><span class="sxs-lookup"><span data-stu-id="404cd-248">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="404cd-249">Běžné vlastnosti nástroje MSBuild</span><span class="sxs-lookup"><span data-stu-id="404cd-249">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="404cd-250">Vlastnosti nástroje MSBuild pro balíček NuGet</span><span class="sxs-lookup"><span data-stu-id="404cd-250">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="404cd-251">Vlastnosti nástroje MSBuild pro obnovení NuGet</span><span class="sxs-lookup"><span data-stu-id="404cd-251">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="404cd-252">Přizpůsobení sestavení</span><span class="sxs-lookup"><span data-stu-id="404cd-252">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
