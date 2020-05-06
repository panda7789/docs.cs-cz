---
title: Vlastnosti nástroje MSBuild pro Microsoft. NET. SDK
description: Referenční informace o vlastnostech MSBuild, které jsou srozumitelné pro .NET Core SDK.
ms.date: 02/14/2020
ms.topic: reference
ms.openlocfilehash: 800ff59310d8437d7f770bf20a5bdf37714f8515
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795570"
---
# <a name="msbuild-properties-for-net-core-sdk-projects"></a><span data-ttu-id="5402e-103">Vlastnosti nástroje MSBuild pro projekty .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="5402e-103">MSBuild properties for .NET Core SDK projects</span></span>

<span data-ttu-id="5402e-104">Tato stránka popisuje vlastnosti nástroje MSBuild pro konfiguraci projektů .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5402e-104">This page describes MSBuild properties for configuring .NET Core projects.</span></span> <span data-ttu-id="5402e-105">Můžete zadat *metadata* pro každou vlastnost jako podřízené prvky vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5402e-105">You can specify *metadata* for each property as child elements of the property.</span></span>

> [!NOTE]
> <span data-ttu-id="5402e-106">Tato stránka je Nedokončená práce a neobsahuje seznam všech užitečných vlastností MSBuild pro .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="5402e-106">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET Core SDK.</span></span> <span data-ttu-id="5402e-107">Seznam běžných vlastností MSBuild najdete v tématu [běžné vlastnosti MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="5402e-107">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="5402e-108">Vlastnosti architektury</span><span class="sxs-lookup"><span data-stu-id="5402e-108">Framework properties</span></span>

- [<span data-ttu-id="5402e-109">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="5402e-109">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="5402e-110">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="5402e-110">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="5402e-111">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="5402e-111">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="5402e-112">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="5402e-112">TargetFramework</span></span>

<span data-ttu-id="5402e-113">`TargetFramework` Vlastnost určuje cílovou verzi rozhraní .NET Framework pro aplikaci, která implicitně odkazuje na [Metapackage](../packages.md#metapackages).</span><span class="sxs-lookup"><span data-stu-id="5402e-113">The `TargetFramework` property specifies the target framework version for the app, which implicitly references a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="5402e-114">Seznam platných monikerů cílového rozhraní Framework naleznete v tématu [cílové architektury v projektech ve stylu sady SDK](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="5402e-114">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

<span data-ttu-id="5402e-115">Další informace naleznete v tématu [cílová rozhraní v projektech ve stylu sady SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="5402e-115">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="5402e-116">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="5402e-116">TargetFrameworks</span></span>

<span data-ttu-id="5402e-117">Vlastnost použijte `TargetFrameworks` , pokud chcete, aby aplikace byla cílena na více platforem.</span><span class="sxs-lookup"><span data-stu-id="5402e-117">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="5402e-118">Seznam platných monikerů cílového rozhraní Framework naleznete v tématu [cílové architektury v projektech ve stylu sady SDK](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="5402e-118">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

> [!NOTE]
> <span data-ttu-id="5402e-119">Tato vlastnost je ignorována `TargetFramework` , pokud je zadáno (jednotné).</span><span class="sxs-lookup"><span data-stu-id="5402e-119">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
</PropertyGroup>
```

<span data-ttu-id="5402e-120">Další informace naleznete v tématu [cílová rozhraní v projektech ve stylu sady SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="5402e-120">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="5402e-121">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="5402e-121">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="5402e-122">Tato vlastnost se vztahuje pouze na projekty `netstandard1.x`používající.</span><span class="sxs-lookup"><span data-stu-id="5402e-122">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="5402e-123">Neplatí pro projekty, které používají `netstandard2.x`.</span><span class="sxs-lookup"><span data-stu-id="5402e-123">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="5402e-124">`NetStandardImplicitPackageVersion` Vlastnost použijte, pokud chcete zadat verzi rozhraní, která je nižší než verze [Metapackage](../packages.md#metapackages) .</span><span class="sxs-lookup"><span data-stu-id="5402e-124">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the [metapackage](../packages.md#metapackages) version.</span></span> <span data-ttu-id="5402e-125">Soubor projektu v následujícím příkladu cílí `netstandard1.3` , ale používá 1.6.0 verzi. `NETStandard.Library`</span><span class="sxs-lookup"><span data-stu-id="5402e-125">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netstandard1.3</TargetFramework>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

## <a name="package-properties"></a><span data-ttu-id="5402e-126">Vlastnosti balíčku</span><span class="sxs-lookup"><span data-stu-id="5402e-126">Package properties</span></span>

<span data-ttu-id="5402e-127">Můžete `PackageId`zadat vlastnosti, `PackageVersion`například,, `PackageIcon`, `Title`a `Description` pro popis balíčku, který je vytvořen z projektu.</span><span class="sxs-lookup"><span data-stu-id="5402e-127">You can specify properties such as `PackageId`, `PackageVersion`, `PackageIcon`, `Title`, and `Description` to describe the package that gets created from your project.</span></span> <span data-ttu-id="5402e-128">Informace o těchto a dalších vlastnostech naleznete v tématu [targeting pack](/nuget/reference/msbuild-targets#pack-target).</span><span class="sxs-lookup"><span data-stu-id="5402e-128">For information about these and other properties, see [pack target](/nuget/reference/msbuild-targets#pack-target).</span></span>

```xml
<PropertyGroup>
  ...
  <PackageId>ClassLibDotNetStandard</PackageId>
  <Version>1.0.0</Version>
  <Authors>John Doe</Authors>
  <Company>Contoso</Company>
</PropertyGroup>
```

## <a name="publish-properties"></a><span data-ttu-id="5402e-129">Vlastnosti publikování</span><span class="sxs-lookup"><span data-stu-id="5402e-129">Publish properties</span></span>

- [<span data-ttu-id="5402e-130">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="5402e-130">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="5402e-131">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="5402e-131">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="5402e-132">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="5402e-132">TrimmerRootAssembly</span></span>](#trimmerrootassembly)
- [<span data-ttu-id="5402e-133">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="5402e-133">UseAppHost</span></span>](#useapphost)

### <a name="runtimeidentifier"></a><span data-ttu-id="5402e-134">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="5402e-134">RuntimeIdentifier</span></span>

<span data-ttu-id="5402e-135">`RuntimeIdentifier` Vlastnost umožňuje zadat jeden [identifikátor modulu runtime (RID)](../rid-catalog.md) pro projekt.</span><span class="sxs-lookup"><span data-stu-id="5402e-135">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="5402e-136">Identifikátor RID umožňuje publikování samostatně zahrnutého nasazení.</span><span class="sxs-lookup"><span data-stu-id="5402e-136">The RID enables publishing a self-contained deployment.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
</PropertyGroup>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="5402e-137">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="5402e-137">RuntimeIdentifiers</span></span>

<span data-ttu-id="5402e-138">`RuntimeIdentifiers` Vlastnost umožňuje určit seznam [identifikátorů modulu runtime (identifikátorů RID)](../rid-catalog.md) oddělených středníky pro projekt.</span><span class="sxs-lookup"><span data-stu-id="5402e-138">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="5402e-139">Tuto vlastnost použijte v případě, že potřebujete publikovat více modulů runtime.</span><span class="sxs-lookup"><span data-stu-id="5402e-139">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="5402e-140">`RuntimeIdentifiers`se používá v čase obnovení, aby se zajistilo, že jsou správné prostředky v grafu.</span><span class="sxs-lookup"><span data-stu-id="5402e-140">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="5402e-141">`RuntimeIdentifier`(jednotné) může poskytovat rychlejší sestavení, pokud je potřeba jenom jeden modul runtime.</span><span class="sxs-lookup"><span data-stu-id="5402e-141">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="trimmerrootassembly"></a><span data-ttu-id="5402e-142">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="5402e-142">TrimmerRootAssembly</span></span>

<span data-ttu-id="5402e-143">`TrimmerRootAssembly` Položka umožňuje vyloučit sestavení z [*ořezávání*](../deploying/trim-self-contained.md).</span><span class="sxs-lookup"><span data-stu-id="5402e-143">The `TrimmerRootAssembly` item lets you exclude an assembly from [*trimming*](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="5402e-144">Oříznutí je proces odebrání nepoužívaných částí modulu runtime ze zabalené aplikace.</span><span class="sxs-lookup"><span data-stu-id="5402e-144">Trimming is the process of removing unused parts of the runtime from a packaged application.</span></span> <span data-ttu-id="5402e-145">V některých případech může oříznutí nesprávně odebrat požadované odkazy.</span><span class="sxs-lookup"><span data-stu-id="5402e-145">In some cases, trimming might incorrectly remove required references.</span></span>

<span data-ttu-id="5402e-146">Následující kód XML vylučuje `System.Security` sestavení z ořezávání.</span><span class="sxs-lookup"><span data-stu-id="5402e-146">The following XML excludes the `System.Security` assembly from trimming.</span></span>

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

### <a name="useapphost"></a><span data-ttu-id="5402e-147">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="5402e-147">UseAppHost</span></span>

<span data-ttu-id="5402e-148">`UseAppHost` Vlastnost byla představena ve verzi 2.1.400 .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="5402e-148">The `UseAppHost` property was introduced in the 2.1.400 version of the .NET Core SDK.</span></span> <span data-ttu-id="5402e-149">Určuje, zda je pro nasazení vytvořen nativní spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="5402e-149">It controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="5402e-150">Pro samostatně obsažená nasazení je vyžadován nativní spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="5402e-150">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="5402e-151">V rozhraní .NET Core 3,0 a novějších verzích je ve výchozím nastavení vytvořen spustitelný soubor závislý na rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5402e-151">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="5402e-152">Nastavte `UseAppHost` vlastnost na `false` hodnotu pro zakázání generování spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="5402e-152">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<PropertyGroup>
  <UseAppHost>false</UseAppHost>
</PropertyGroup>
```

<span data-ttu-id="5402e-153">Další informace o nasazení naleznete v tématu [nasazení aplikace .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="5402e-153">For more information about deployment, see [.NET Core application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="5402e-154">Vlastnosti kompilace</span><span class="sxs-lookup"><span data-stu-id="5402e-154">Compile properties</span></span>

- [<span data-ttu-id="5402e-155">Langversion –</span><span class="sxs-lookup"><span data-stu-id="5402e-155">LangVersion</span></span>](#langversion)

### <a name="langversion"></a><span data-ttu-id="5402e-156">Langversion –</span><span class="sxs-lookup"><span data-stu-id="5402e-156">LangVersion</span></span>

<span data-ttu-id="5402e-157">`LangVersion` Vlastnost umožňuje zadat konkrétní verzi programovacího jazyka.</span><span class="sxs-lookup"><span data-stu-id="5402e-157">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="5402e-158">Například pokud chcete mít přístup k funkcím verze Preview jazyka C#, `LangVersion` nastavte `preview`na.</span><span class="sxs-lookup"><span data-stu-id="5402e-158">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<PropertyGroup>
  <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="5402e-159">Další informace najdete v tématu [Správa verzí jazyka C#](../../csharp/language-reference/configure-language-version.md#override-a-default).</span><span class="sxs-lookup"><span data-stu-id="5402e-159">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="run-time-configuration-properties"></a><span data-ttu-id="5402e-160">Vlastnosti konfigurace runtime</span><span class="sxs-lookup"><span data-stu-id="5402e-160">Run-time configuration properties</span></span>

<span data-ttu-id="5402e-161">Můžete nakonfigurovat některé chování za běhu zadáním vlastností MSBuild v souboru projektu aplikace.</span><span class="sxs-lookup"><span data-stu-id="5402e-161">You can configure some run-time behaviors by specifying MSBuild properties in the project file of the app.</span></span> <span data-ttu-id="5402e-162">Informace o jiných způsobech konfigurace chování za běhu najdete v tématu [nastavení konfigurace prostředí .NET Core](../run-time-config/index.md)runtime.</span><span class="sxs-lookup"><span data-stu-id="5402e-162">For information about other ways of configuring run-time behavior, see [.NET Core run-time configuration settings](../run-time-config/index.md).</span></span>

- [<span data-ttu-id="5402e-163">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="5402e-163">ConcurrentGarbageCollection</span></span>](#concurrentgarbagecollection)
- [<span data-ttu-id="5402e-164">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="5402e-164">InvariantGlobalization</span></span>](#invariantglobalization)
- [<span data-ttu-id="5402e-165">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="5402e-165">RetainVMGarbageCollection</span></span>](#retainvmgarbagecollection)
- [<span data-ttu-id="5402e-166">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="5402e-166">ServerGarbageCollection</span></span>](#servergarbagecollection)
- [<span data-ttu-id="5402e-167">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="5402e-167">ThreadPoolMaxThreads</span></span>](#threadpoolmaxthreads)
- [<span data-ttu-id="5402e-168">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="5402e-168">ThreadPoolMinThreads</span></span>](#threadpoolminthreads)
- [<span data-ttu-id="5402e-169">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="5402e-169">TieredCompilation</span></span>](#tieredcompilation)
- [<span data-ttu-id="5402e-170">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="5402e-170">TieredCompilationQuickJit</span></span>](#tieredcompilationquickjit)
- [<span data-ttu-id="5402e-171">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="5402e-171">TieredCompilationQuickJitForLoops</span></span>](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a><span data-ttu-id="5402e-172">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="5402e-172">ConcurrentGarbageCollection</span></span>

<span data-ttu-id="5402e-173">`ConcurrentGarbageCollection` Vlastnost konfiguruje, zda je povoleno [uvolňování paměti na pozadí (souběžně)](../../standard/garbage-collection/background-gc.md) .</span><span class="sxs-lookup"><span data-stu-id="5402e-173">The `ConcurrentGarbageCollection` property configures whether [background (concurrent) garbage collection](../../standard/garbage-collection/background-gc.md) is enabled.</span></span> <span data-ttu-id="5402e-174">Nastavte hodnotu na zakázat `false` uvolňování paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="5402e-174">Set the value to `false` to disable background garbage collection.</span></span> <span data-ttu-id="5402e-175">Další informace najdete v tématu [System. GC. souběžné/COMPlus_gcConcurrent](../run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent).</span><span class="sxs-lookup"><span data-stu-id="5402e-175">For more information, see [System.GC.Concurrent/COMPlus_gcConcurrent](../run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent).</span></span>

```xml
<PropertyGroup>
  <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
</PropertyGroup>
```

### <a name="invariantglobalization"></a><span data-ttu-id="5402e-176">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="5402e-176">InvariantGlobalization</span></span>

<span data-ttu-id="5402e-177">`InvariantGlobalization` Vlastnost nakonfiguruje, jestli aplikace běží v režimu *invariantní globalizace* , což znamená, že nemá přístup k datům specifickým pro jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="5402e-177">The `InvariantGlobalization` property configures whether the app runs in *globalization-invariant* mode, which means it doesn't have access to culture-specific data.</span></span> <span data-ttu-id="5402e-178">Nastavte hodnotu `true` pro spuštění v režimu invariantní globalizace.</span><span class="sxs-lookup"><span data-stu-id="5402e-178">Set the value to `true` to run in globalization-invariant mode.</span></span> <span data-ttu-id="5402e-179">Další informace naleznete v tématu [invariantní režim](../run-time-config/globalization.md#invariant-mode).</span><span class="sxs-lookup"><span data-stu-id="5402e-179">For more information, see [Invariant mode](../run-time-config/globalization.md#invariant-mode).</span></span>

```xml
<PropertyGroup>
  <InvariantGlobalization>true</InvariantGlobalization>
</PropertyGroup>
```

### <a name="retainvmgarbagecollection"></a><span data-ttu-id="5402e-180">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="5402e-180">RetainVMGarbageCollection</span></span>

<span data-ttu-id="5402e-181">`RetainVMGarbageCollection` Vlastnost konfiguruje systém uvolňování paměti pro vložení odstraněných segmentů paměti v pohotovostním seznamu pro budoucí použití nebo uvolnění.</span><span class="sxs-lookup"><span data-stu-id="5402e-181">The `RetainVMGarbageCollection` property configures the garbage collector to put deleted memory segments on a standby list for future use or release them.</span></span> <span data-ttu-id="5402e-182">Nastavením hodnoty určíte `true` , aby systém uvolňování paměti umístil segmenty do seznamu pohotovostních hodnot.</span><span class="sxs-lookup"><span data-stu-id="5402e-182">Setting the value to `true` tells the garbage collector to put the segments on a standby list.</span></span> <span data-ttu-id="5402e-183">Další informace najdete v tématu [System. GC. RetainVM/COMPlus_GCRetainVM](../run-time-config/garbage-collector.md#systemgcretainvmcomplus_gcretainvm).</span><span class="sxs-lookup"><span data-stu-id="5402e-183">For more information, see [System.GC.RetainVM/COMPlus_GCRetainVM](../run-time-config/garbage-collector.md#systemgcretainvmcomplus_gcretainvm).</span></span>

```xml
<PropertyGroup>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
</PropertyGroup>
```

### <a name="servergarbagecollection"></a><span data-ttu-id="5402e-184">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="5402e-184">ServerGarbageCollection</span></span>

<span data-ttu-id="5402e-185">`ServerGarbageCollection` Vlastnost konfiguruje, zda aplikace používá [uvolňování paměti pracovní stanice nebo uvolňování paměti serveru](../../standard/garbage-collection/workstation-server-gc.md).</span><span class="sxs-lookup"><span data-stu-id="5402e-185">The `ServerGarbageCollection` property configures whether the application uses [workstation garbage collection or server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span> <span data-ttu-id="5402e-186">Nastavte hodnotu `true` na použít uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="5402e-186">Set the value to `true` to use server garbage collection.</span></span> <span data-ttu-id="5402e-187">Další informace najdete v tématu [System. GC. Server/COMPlus_gcServer](../run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).</span><span class="sxs-lookup"><span data-stu-id="5402e-187">For more information, see [System.GC.Server/COMPlus_gcServer](../run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

### <a name="threadpoolmaxthreads"></a><span data-ttu-id="5402e-188">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="5402e-188">ThreadPoolMaxThreads</span></span>

<span data-ttu-id="5402e-189">`ThreadPoolMaxThreads` Vlastnost konfiguruje maximální počet vláken pro fond pracovních vláken.</span><span class="sxs-lookup"><span data-stu-id="5402e-189">The `ThreadPoolMaxThreads` property configures the maximum number of threads for the worker thread pool.</span></span> <span data-ttu-id="5402e-190">Další informace najdete v tématu [maximální počet vláken](../run-time-config/threading.md#maximum-threads).</span><span class="sxs-lookup"><span data-stu-id="5402e-190">For more information, see [Maximum threads](../run-time-config/threading.md#maximum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
</PropertyGroup>
```

### <a name="threadpoolminthreads"></a><span data-ttu-id="5402e-191">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="5402e-191">ThreadPoolMinThreads</span></span>

<span data-ttu-id="5402e-192">`ThreadPoolMinThreads` Vlastnost konfiguruje minimální počet vláken pro fond pracovních vláken.</span><span class="sxs-lookup"><span data-stu-id="5402e-192">The `ThreadPoolMinThreads` property configures the minimum number of threads for the worker thread pool.</span></span> <span data-ttu-id="5402e-193">Další informace najdete v tématu [minimální počet vláken](../run-time-config/threading.md#minimum-threads).</span><span class="sxs-lookup"><span data-stu-id="5402e-193">For more information, see [Minimum threads](../run-time-config/threading.md#minimum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
</PropertyGroup>
```

### <a name="tieredcompilation"></a><span data-ttu-id="5402e-194">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="5402e-194">TieredCompilation</span></span>

<span data-ttu-id="5402e-195">`TieredCompilation` Vlastnost určuje, zda kompilátor JIT (just-in-time) používá [vrstvenou kompilaci](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="5402e-195">The `TieredCompilation` property configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="5402e-196">Nastavte hodnotu `false` na zakázat vrstvenou kompilaci.</span><span class="sxs-lookup"><span data-stu-id="5402e-196">Set the value to `false` to disable tiered compilation.</span></span> <span data-ttu-id="5402e-197">Další informace najdete v tématu [vrstvená kompilace](../run-time-config/compilation.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="5402e-197">For more information, see [Tiered compilation](../run-time-config/compilation.md#tiered-compilation).</span></span>

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

### <a name="tieredcompilationquickjit"></a><span data-ttu-id="5402e-198">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="5402e-198">TieredCompilationQuickJit</span></span>

<span data-ttu-id="5402e-199">`TieredCompilationQuickJit` Vlastnost konfiguruje, zda kompilátor JIT používá rychlou JIT.</span><span class="sxs-lookup"><span data-stu-id="5402e-199">The `TieredCompilationQuickJit` property configures whether the JIT compiler uses quick JIT.</span></span> <span data-ttu-id="5402e-200">Nastavením hodnoty `false` na zakážete rychlou JIT.</span><span class="sxs-lookup"><span data-stu-id="5402e-200">Set the value to `false` to disable quick JIT.</span></span> <span data-ttu-id="5402e-201">Další informace najdete v tématu [rychlá JIT](../run-time-config/compilation.md#quick-jit).</span><span class="sxs-lookup"><span data-stu-id="5402e-201">For more information, see [Quick JIT](../run-time-config/compilation.md#quick-jit).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

### <a name="tieredcompilationquickjitforloops"></a><span data-ttu-id="5402e-202">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="5402e-202">TieredCompilationQuickJitForLoops</span></span>

<span data-ttu-id="5402e-203">`TieredCompilationQuickJitForLoops` Vlastnost konfiguruje, zda kompilátor JIT používá rychlou JIT v metodách, které obsahují smyčky.</span><span class="sxs-lookup"><span data-stu-id="5402e-203">The `TieredCompilationQuickJitForLoops` property configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span> <span data-ttu-id="5402e-204">Nastavte hodnotu na, `true` Chcete-li povolit rychlou JIT v metodách, které obsahují smyčky.</span><span class="sxs-lookup"><span data-stu-id="5402e-204">Set the value to `true` to enable quick JIT on methods that contain loops.</span></span> <span data-ttu-id="5402e-205">Další informace najdete v tématu [rychlá JIT pro smyčky](../run-time-config/compilation.md#quick-jit-for-loops).</span><span class="sxs-lookup"><span data-stu-id="5402e-205">For more information, see [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
</PropertyGroup>
```

## <a name="reference-properties"></a><span data-ttu-id="5402e-206">Vlastnosti odkazu</span><span class="sxs-lookup"><span data-stu-id="5402e-206">Reference properties</span></span>

- [<span data-ttu-id="5402e-207">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="5402e-207">AssetTargetFallback</span></span>](#assettargetfallback)
- [<span data-ttu-id="5402e-208">PackageReference</span><span class="sxs-lookup"><span data-stu-id="5402e-208">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="5402e-209">ProjectReference</span><span class="sxs-lookup"><span data-stu-id="5402e-209">ProjectReference</span></span>](#projectreference)
- [<span data-ttu-id="5402e-210">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="5402e-210">Reference</span></span>](#reference)
- [<span data-ttu-id="5402e-211">Obnovit vlastnosti</span><span class="sxs-lookup"><span data-stu-id="5402e-211">Restore properties</span></span>](#restore-properties)

### <a name="assettargetfallback"></a><span data-ttu-id="5402e-212">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="5402e-212">AssetTargetFallback</span></span>

<span data-ttu-id="5402e-213">`AssetTargetFallback` Vlastnost umožňuje zadat další kompatibilní verze rozhraní pro odkazy na projekt a balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="5402e-213">The `AssetTargetFallback` property lets you specify additional compatible framework versions for project references and NuGet packages.</span></span> <span data-ttu-id="5402e-214">Pokud například zadáte závislost balíčku pomocí `PackageReference` , ale tento balíček neobsahuje prostředky, které jsou kompatibilní s vašimi projekty `TargetFramework`, vlastnost se `AssetTargetFallback` dostane do hry.</span><span class="sxs-lookup"><span data-stu-id="5402e-214">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="5402e-215">Kompatibilita odkazovaného balíčku je znovu zkontrolována pomocí každé cílové architektury, která je určena v `AssetTargetFallback`.</span><span class="sxs-lookup"><span data-stu-id="5402e-215">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span>

<span data-ttu-id="5402e-216">Můžete nastavit `AssetTargetFallback` vlastnost na jednu nebo více [cílových verzí rozhraní .NET Framework](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="5402e-216">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<PropertyGroup>
  <AssetTargetFallback>net461</AssetTargetFallback>
</PropertyGroup>
```

### <a name="packagereference"></a><span data-ttu-id="5402e-217">PackageReference</span><span class="sxs-lookup"><span data-stu-id="5402e-217">PackageReference</span></span>

<span data-ttu-id="5402e-218">`PackageReference` Definuje odkaz na balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="5402e-218">The `PackageReference` defines a reference to a NuGet package.</span></span> <span data-ttu-id="5402e-219">Například můžete chtít odkazovat na jeden balíček místo [Metapackage](../packages.md#metapackages).</span><span class="sxs-lookup"><span data-stu-id="5402e-219">For example, you may want to reference a single package instead of a [metapackage](../packages.md#metapackages).</span></span>

<span data-ttu-id="5402e-220">`Include` Atribut určuje ID balíčku.</span><span class="sxs-lookup"><span data-stu-id="5402e-220">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="5402e-221">`Version` Atribut určuje verzi nebo rozsah verzí.</span><span class="sxs-lookup"><span data-stu-id="5402e-221">The `Version` attribute specifies the version or version range.</span></span> <span data-ttu-id="5402e-222">Informace o tom, jak zadat minimální verzi, maximální verzi, rozsah nebo přesnou shodu, najdete v tématu [rozsahy verzí](/nuget/concepts/package-versioning#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="5402e-222">For information about how to specify a minimum version, maximum version, range, or exact match, see [Version ranges](/nuget/concepts/package-versioning#version-ranges).</span></span> <span data-ttu-id="5402e-223">Do odkazu na projekt můžete také přidat následující metadata: `IncludeAssets`, `ExcludeAssets`a. `PrivateAssets`</span><span class="sxs-lookup"><span data-stu-id="5402e-223">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="5402e-224">Fragment souboru projektu v následujícím příkladu odkazuje na balíček [System. Runtime](https://www.nuget.org/packages/System.Runtime/) .</span><span class="sxs-lookup"><span data-stu-id="5402e-224">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="System.Runtime" Version="4.3.0" />
</ItemGroup>
```

<span data-ttu-id="5402e-225">Další informace naleznete v tématu [odkazy na balíčky v souborech projektu](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="5402e-225">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="projectreference"></a><span data-ttu-id="5402e-226">ProjectReference</span><span class="sxs-lookup"><span data-stu-id="5402e-226">ProjectReference</span></span>

<span data-ttu-id="5402e-227">`ProjectReference` Položka definuje odkaz na jiný projekt.</span><span class="sxs-lookup"><span data-stu-id="5402e-227">The `ProjectReference` item defines a reference to another project.</span></span> <span data-ttu-id="5402e-228">Odkazovaný projekt je přidán jako závislost balíčku NuGet, to znamená, že je zpracována jako `PackageReference`.</span><span class="sxs-lookup"><span data-stu-id="5402e-228">The referenced project is added as a NuGet package dependency, that is, it's treated the same as a `PackageReference`.</span></span>

<span data-ttu-id="5402e-229">`Include` Atribut určuje cestu k projektu.</span><span class="sxs-lookup"><span data-stu-id="5402e-229">The `Include` attribute specifies the path to the project.</span></span> <span data-ttu-id="5402e-230">Do odkazu na projekt můžete také přidat následující metadata: `IncludeAssets`, `ExcludeAssets`a. `PrivateAssets`</span><span class="sxs-lookup"><span data-stu-id="5402e-230">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="5402e-231">Fragment souboru projektu v následujícím příkladu odkazuje na projekt s názvem `Project2`.</span><span class="sxs-lookup"><span data-stu-id="5402e-231">The project file snippet in the following example references a project named `Project2`.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\Project2.csproj" />
</ItemGroup>
```

### <a name="reference"></a><span data-ttu-id="5402e-232">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="5402e-232">Reference</span></span>

<span data-ttu-id="5402e-233">`Reference` Položka definuje odkaz na soubor sestavení.</span><span class="sxs-lookup"><span data-stu-id="5402e-233">The `Reference` item defines a reference to an assembly file.</span></span>

<span data-ttu-id="5402e-234">`Include` Atribut určuje název souboru a `HintPath` podřízený element určuje cestu k sestavení.</span><span class="sxs-lookup"><span data-stu-id="5402e-234">The `Include` attribute specifies the name of the file, and the `HintPath` child element specifies the path to the assembly.</span></span>

```xml
<ItemGroup>
  <Reference Include="MyAssembly">
    <HintPath>..\..\Assemblies\MyAssembly.dll</HintPath>
  </Reference>
</ItemGroup>
```

### <a name="restore-properties"></a><span data-ttu-id="5402e-235">Obnovit vlastnosti</span><span class="sxs-lookup"><span data-stu-id="5402e-235">Restore properties</span></span>

<span data-ttu-id="5402e-236">Při obnovení odkazovaného balíčku se nainstaluje všechny jeho přímé závislosti a všechny závislosti těchto závislostí.</span><span class="sxs-lookup"><span data-stu-id="5402e-236">Restoring a referenced package installs all of its direct dependencies and all the dependencies of those dependencies.</span></span> <span data-ttu-id="5402e-237">Obnovení balíčku můžete přizpůsobit zadáním vlastností, jako jsou `RestorePackagesPath` a `RestoreIgnoreFailedSources`.</span><span class="sxs-lookup"><span data-stu-id="5402e-237">You can customize package restoration by specifying properties such as `RestorePackagesPath` and `RestoreIgnoreFailedSources`.</span></span> <span data-ttu-id="5402e-238">Další informace o těchto a dalších vlastnostech naleznete v tématu [Restore Target](/nuget/reference/msbuild-targets#restore-target).</span><span class="sxs-lookup"><span data-stu-id="5402e-238">For more information about these and other properties, see [restore target](/nuget/reference/msbuild-targets#restore-target).</span></span>

```xml
<PropertyGroup>
  <RestoreIgnoreFailedSource>true</RestoreIgnoreFailedSource>
</PropertyGroup>
```

## <a name="see-also"></a><span data-ttu-id="5402e-239">Viz také</span><span class="sxs-lookup"><span data-stu-id="5402e-239">See also</span></span>

- [<span data-ttu-id="5402e-240">Referenční dokumentace schématu MSBuild</span><span class="sxs-lookup"><span data-stu-id="5402e-240">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="5402e-241">Běžné vlastnosti nástroje MSBuild</span><span class="sxs-lookup"><span data-stu-id="5402e-241">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="5402e-242">Vlastnosti nástroje MSBuild pro balíček NuGet</span><span class="sxs-lookup"><span data-stu-id="5402e-242">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="5402e-243">Vlastnosti nástroje MSBuild pro obnovení NuGet</span><span class="sxs-lookup"><span data-stu-id="5402e-243">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="5402e-244">Přizpůsobení sestavení</span><span class="sxs-lookup"><span data-stu-id="5402e-244">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
