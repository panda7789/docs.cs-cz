---
title: Vlastnosti nástroje MSBuild pro Microsoft. NET. SDK
description: Referenční informace o vlastnostech MSBuild, které jsou srozumitelné pro .NET Core SDK.
ms.date: 02/14/2020
ms.topic: reference
ms.openlocfilehash: 105b7d67ea24515ea88481cb4a4fe42d2a03cfd0
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2020
ms.locfileid: "82506783"
---
# <a name="msbuild-properties-for-net-core-sdk-projects"></a><span data-ttu-id="d4edd-103">Vlastnosti nástroje MSBuild pro projekty .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="d4edd-103">MSBuild properties for .NET Core SDK projects</span></span>

<span data-ttu-id="d4edd-104">Tato stránka popisuje vlastnosti nástroje MSBuild pro konfiguraci projektů .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d4edd-104">This page describes MSBuild properties for configuring .NET Core projects.</span></span>

> [!NOTE]
> <span data-ttu-id="d4edd-105">Tato stránka je Nedokončená práce a neobsahuje seznam všech užitečných vlastností MSBuild pro .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="d4edd-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET Core SDK.</span></span> <span data-ttu-id="d4edd-106">Seznam běžných vlastností MSBuild najdete v tématu [běžné vlastnosti MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="d4edd-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="d4edd-107">Vlastnosti architektury</span><span class="sxs-lookup"><span data-stu-id="d4edd-107">Framework properties</span></span>

- [<span data-ttu-id="d4edd-108">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="d4edd-108">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="d4edd-109">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="d4edd-109">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="d4edd-110">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="d4edd-110">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="d4edd-111">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="d4edd-111">TargetFramework</span></span>

<span data-ttu-id="d4edd-112">`TargetFramework` Vlastnost určuje cílovou verzi rozhraní .NET Framework pro aplikaci, která implicitně odkazuje na [Metapackage](../packages.md#metapackages).</span><span class="sxs-lookup"><span data-stu-id="d4edd-112">The `TargetFramework` property specifies the target framework version for the app, which implicitly references a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="d4edd-113">Seznam platných monikerů cílového rozhraní Framework naleznete v tématu [cílové architektury v projektech ve stylu sady SDK](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="d4edd-113">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="d4edd-114">Další informace naleznete v tématu [cílová rozhraní v projektech ve stylu sady SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="d4edd-114">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="d4edd-115">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="d4edd-115">TargetFrameworks</span></span>

<span data-ttu-id="d4edd-116">Vlastnost použijte `TargetFrameworks` , pokud chcete, aby aplikace byla cílena na více platforem.</span><span class="sxs-lookup"><span data-stu-id="d4edd-116">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="d4edd-117">Seznam platných monikerů cílového rozhraní Framework naleznete v tématu [cílové architektury v projektech ve stylu sady SDK](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="d4edd-117">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

> [!NOTE]
> <span data-ttu-id="d4edd-118">Tato vlastnost je ignorována `TargetFramework` , pokud je zadáno (jednotné).</span><span class="sxs-lookup"><span data-stu-id="d4edd-118">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="d4edd-119">Další informace naleznete v tématu [cílová rozhraní v projektech ve stylu sady SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="d4edd-119">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="d4edd-120">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="d4edd-120">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="d4edd-121">Tato vlastnost se vztahuje pouze na projekty `netstandard1.x`používající.</span><span class="sxs-lookup"><span data-stu-id="d4edd-121">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="d4edd-122">Neplatí pro projekty, které používají `netstandard2.x`.</span><span class="sxs-lookup"><span data-stu-id="d4edd-122">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="d4edd-123">`NetStandardImplicitPackageVersion` Vlastnost použijte, pokud chcete zadat verzi rozhraní, která je nižší než verze [Metapackage](../packages.md#metapackages) .</span><span class="sxs-lookup"><span data-stu-id="d4edd-123">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the [metapackage](../packages.md#metapackages) version.</span></span> <span data-ttu-id="d4edd-124">Soubor projektu v následujícím příkladu cílí `netstandard1.3` , ale používá 1.6.0 verzi. `NETStandard.Library`</span><span class="sxs-lookup"><span data-stu-id="d4edd-124">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

## <a name="publish-properties"></a><span data-ttu-id="d4edd-125">Vlastnosti publikování</span><span class="sxs-lookup"><span data-stu-id="d4edd-125">Publish properties</span></span>

- [<span data-ttu-id="d4edd-126">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="d4edd-126">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="d4edd-127">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="d4edd-127">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="d4edd-128">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="d4edd-128">TrimmerRootAssembly</span></span>](#trimmerrootassembly)
- [<span data-ttu-id="d4edd-129">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="d4edd-129">UseAppHost</span></span>](#useapphost)

### <a name="runtimeidentifier"></a><span data-ttu-id="d4edd-130">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="d4edd-130">RuntimeIdentifier</span></span>

<span data-ttu-id="d4edd-131">`RuntimeIdentifier` Vlastnost umožňuje zadat jeden [identifikátor modulu runtime (RID)](../rid-catalog.md) pro projekt.</span><span class="sxs-lookup"><span data-stu-id="d4edd-131">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="d4edd-132">Identifikátor RID umožňuje publikování samostatně zahrnutého nasazení.</span><span class="sxs-lookup"><span data-stu-id="d4edd-132">The RID enables publishing a self-contained deployment.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
  </PropertyGroup>
</Project>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="d4edd-133">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="d4edd-133">RuntimeIdentifiers</span></span>

<span data-ttu-id="d4edd-134">`RuntimeIdentifiers` Vlastnost umožňuje určit seznam [identifikátorů modulu runtime (identifikátorů RID)](../rid-catalog.md) oddělených středníky pro projekt.</span><span class="sxs-lookup"><span data-stu-id="d4edd-134">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="d4edd-135">Tuto vlastnost použijte v případě, že potřebujete publikovat více modulů runtime.</span><span class="sxs-lookup"><span data-stu-id="d4edd-135">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="d4edd-136">`RuntimeIdentifiers`se používá v čase obnovení, aby se zajistilo, že jsou správné prostředky v grafu.</span><span class="sxs-lookup"><span data-stu-id="d4edd-136">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="d4edd-137">`RuntimeIdentifier`(jednotné) může poskytovat rychlejší sestavení, pokud je potřeba jenom jeden modul runtime.</span><span class="sxs-lookup"><span data-stu-id="d4edd-137">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

### <a name="trimmerrootassembly"></a><span data-ttu-id="d4edd-138">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="d4edd-138">TrimmerRootAssembly</span></span>

<span data-ttu-id="d4edd-139">`TrimmerRootAssembly` Položka umožňuje vyloučit sestavení z [*ořezávání*](../deploying/trim-self-contained.md).</span><span class="sxs-lookup"><span data-stu-id="d4edd-139">The `TrimmerRootAssembly` item lets you exclude an assembly from [*trimming*](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="d4edd-140">Oříznutí je proces odebrání nepoužívaných částí modulu runtime ze zabalené aplikace.</span><span class="sxs-lookup"><span data-stu-id="d4edd-140">Trimming is the process of removing unused parts of the runtime from a packaged application.</span></span> <span data-ttu-id="d4edd-141">V některých případech může oříznutí nesprávně odebrat požadované odkazy.</span><span class="sxs-lookup"><span data-stu-id="d4edd-141">In some cases, trimming might incorrectly remove required references.</span></span>

<span data-ttu-id="d4edd-142">Následující kód XML vylučuje `System.Security` sestavení z ořezávání.</span><span class="sxs-lookup"><span data-stu-id="d4edd-142">The following XML excludes the `System.Security` assembly from trimming.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
  </ItemGroup>
</Project>
```

### <a name="useapphost"></a><span data-ttu-id="d4edd-143">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="d4edd-143">UseAppHost</span></span>

<span data-ttu-id="d4edd-144">`UseAppHost` Vlastnost byla představena ve verzi 2.1.400 .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="d4edd-144">The `UseAppHost` property was introduced in the 2.1.400 version of the .NET Core SDK.</span></span> <span data-ttu-id="d4edd-145">Určuje, zda je pro nasazení vytvořen nativní spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="d4edd-145">It controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="d4edd-146">Pro samostatně obsažená nasazení je vyžadován nativní spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="d4edd-146">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="d4edd-147">V rozhraní .NET Core 3,0 a novějších verzích je ve výchozím nastavení vytvořen spustitelný soubor závislý na rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d4edd-147">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="d4edd-148">Nastavte `UseAppHost` vlastnost na `false` hodnotu pro zakázání generování spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="d4edd-148">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <UseAppHost>false</UseAppHost>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="d4edd-149">Další informace o nasazení naleznete v tématu [nasazení aplikace .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="d4edd-149">For more information about deployment, see [.NET Core application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="d4edd-150">Vlastnosti kompilace</span><span class="sxs-lookup"><span data-stu-id="d4edd-150">Compile properties</span></span>

- [<span data-ttu-id="d4edd-151">Langversion –</span><span class="sxs-lookup"><span data-stu-id="d4edd-151">LangVersion</span></span>](#langversion)

### <a name="langversion"></a><span data-ttu-id="d4edd-152">Langversion –</span><span class="sxs-lookup"><span data-stu-id="d4edd-152">LangVersion</span></span>

<span data-ttu-id="d4edd-153">`LangVersion` Vlastnost umožňuje zadat konkrétní verzi programovacího jazyka.</span><span class="sxs-lookup"><span data-stu-id="d4edd-153">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="d4edd-154">Například pokud chcete mít přístup k funkcím verze Preview jazyka C#, `LangVersion` nastavte `preview`na.</span><span class="sxs-lookup"><span data-stu-id="d4edd-154">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <LangVersion>preview</LangVersion>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="d4edd-155">Další informace najdete v tématu [Správa verzí jazyka C#](../../csharp/language-reference/configure-language-version.md#override-a-default).</span><span class="sxs-lookup"><span data-stu-id="d4edd-155">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="run-time-configuration-properties"></a><span data-ttu-id="d4edd-156">Vlastnosti konfigurace runtime</span><span class="sxs-lookup"><span data-stu-id="d4edd-156">Run-time configuration properties</span></span>

<span data-ttu-id="d4edd-157">Můžete nakonfigurovat některé chování za běhu zadáním vlastností MSBuild v souboru projektu aplikace.</span><span class="sxs-lookup"><span data-stu-id="d4edd-157">You can configure some run-time behaviors by specifying MSBuild properties in the project file of the app.</span></span> <span data-ttu-id="d4edd-158">Informace o jiných způsobech konfigurace chování za běhu najdete v tématu [nastavení konfigurace prostředí .NET Core](../run-time-config/index.md)runtime.</span><span class="sxs-lookup"><span data-stu-id="d4edd-158">For information about other ways of configuring run-time behavior, see [.NET Core run-time configuration settings](../run-time-config/index.md).</span></span>

- [<span data-ttu-id="d4edd-159">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="d4edd-159">ConcurrentGarbageCollection</span></span>](#concurrentgarbagecollection)
- [<span data-ttu-id="d4edd-160">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="d4edd-160">InvariantGlobalization</span></span>](#invariantglobalization)
- [<span data-ttu-id="d4edd-161">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="d4edd-161">RetainVMGarbageCollection</span></span>](#retainvmgarbagecollection)
- [<span data-ttu-id="d4edd-162">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="d4edd-162">ServerGarbageCollection</span></span>](#servergarbagecollection)
- [<span data-ttu-id="d4edd-163">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="d4edd-163">ThreadPoolMaxThreads</span></span>](#threadpoolmaxthreads)
- [<span data-ttu-id="d4edd-164">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="d4edd-164">ThreadPoolMinThreads</span></span>](#threadpoolminthreads)
- [<span data-ttu-id="d4edd-165">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="d4edd-165">TieredCompilation</span></span>](#tieredcompilation)
- [<span data-ttu-id="d4edd-166">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="d4edd-166">TieredCompilationQuickJit</span></span>](#tieredcompilationquickjit)
- [<span data-ttu-id="d4edd-167">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="d4edd-167">TieredCompilationQuickJitForLoops</span></span>](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a><span data-ttu-id="d4edd-168">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="d4edd-168">ConcurrentGarbageCollection</span></span>

<span data-ttu-id="d4edd-169">`ConcurrentGarbageCollection` Vlastnost konfiguruje, zda je povoleno [uvolňování paměti na pozadí (souběžně)](../../standard/garbage-collection/background-gc.md) .</span><span class="sxs-lookup"><span data-stu-id="d4edd-169">The `ConcurrentGarbageCollection` property configures whether [background (concurrent) garbage collection](../../standard/garbage-collection/background-gc.md) is enabled.</span></span> <span data-ttu-id="d4edd-170">Nastavte hodnotu na zakázat `false` uvolňování paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="d4edd-170">Set the value to `false` to disable background garbage collection.</span></span> <span data-ttu-id="d4edd-171">Další informace najdete v tématu [System. GC. souběžné/COMPlus_gcConcurrent](../run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent).</span><span class="sxs-lookup"><span data-stu-id="d4edd-171">For more information, see [System.GC.Concurrent/COMPlus_gcConcurrent](../run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>
</Project>
```

### <a name="invariantglobalization"></a><span data-ttu-id="d4edd-172">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="d4edd-172">InvariantGlobalization</span></span>

<span data-ttu-id="d4edd-173">`InvariantGlobalization` Vlastnost nakonfiguruje, jestli aplikace běží v režimu *invariantní globalizace* , což znamená, že nemá přístup k datům specifickým pro jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="d4edd-173">The `InvariantGlobalization` property configures whether the app runs in *globalization-invariant* mode, which means it doesn't have access to culture-specific data.</span></span> <span data-ttu-id="d4edd-174">Nastavte hodnotu `true` pro spuštění v režimu invariantní globalizace.</span><span class="sxs-lookup"><span data-stu-id="d4edd-174">Set the value to `true` to run in globalization-invariant mode.</span></span> <span data-ttu-id="d4edd-175">Další informace naleznete v tématu [invariantní režim](../run-time-config/globalization.md#invariant-mode).</span><span class="sxs-lookup"><span data-stu-id="d4edd-175">For more information, see [Invariant mode](../run-time-config/globalization.md#invariant-mode).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>
</Project>
```

### <a name="retainvmgarbagecollection"></a><span data-ttu-id="d4edd-176">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="d4edd-176">RetainVMGarbageCollection</span></span>

<span data-ttu-id="d4edd-177">`RetainVMGarbageCollection` Vlastnost konfiguruje systém uvolňování paměti pro vložení odstraněných segmentů paměti v pohotovostním seznamu pro budoucí použití nebo uvolnění.</span><span class="sxs-lookup"><span data-stu-id="d4edd-177">The `RetainVMGarbageCollection` property configures the garbage collector to put deleted memory segments on a standby list for future use or release them.</span></span> <span data-ttu-id="d4edd-178">Nastavením hodnoty určíte `true` , aby systém uvolňování paměti umístil segmenty do seznamu pohotovostních hodnot.</span><span class="sxs-lookup"><span data-stu-id="d4edd-178">Setting the value to `true` tells the garbage collector to put the segments on a standby list.</span></span> <span data-ttu-id="d4edd-179">Další informace najdete v tématu [System. GC. RetainVM/COMPlus_GCRetainVM](../run-time-config/garbage-collector.md#systemgcretainvmcomplus_gcretainvm).</span><span class="sxs-lookup"><span data-stu-id="d4edd-179">For more information, see [System.GC.RetainVM/COMPlus_GCRetainVM](../run-time-config/garbage-collector.md#systemgcretainvmcomplus_gcretainvm).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>
</Project>
```

### <a name="servergarbagecollection"></a><span data-ttu-id="d4edd-180">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="d4edd-180">ServerGarbageCollection</span></span>

<span data-ttu-id="d4edd-181">`ServerGarbageCollection` Vlastnost konfiguruje, zda aplikace používá [uvolňování paměti pracovní stanice nebo uvolňování paměti serveru](../../standard/garbage-collection/workstation-server-gc.md).</span><span class="sxs-lookup"><span data-stu-id="d4edd-181">The `ServerGarbageCollection` property configures whether the application uses [workstation garbage collection or server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span> <span data-ttu-id="d4edd-182">Nastavte hodnotu `true` na použít uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="d4edd-182">Set the value to `true` to use server garbage collection.</span></span> <span data-ttu-id="d4edd-183">Další informace najdete v tématu [System. GC. Server/COMPlus_gcServer](../run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).</span><span class="sxs-lookup"><span data-stu-id="d4edd-183">For more information, see [System.GC.Server/COMPlus_gcServer](../run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>
</Project>
```

### <a name="threadpoolmaxthreads"></a><span data-ttu-id="d4edd-184">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="d4edd-184">ThreadPoolMaxThreads</span></span>

<span data-ttu-id="d4edd-185">`ThreadPoolMaxThreads` Vlastnost konfiguruje maximální počet vláken pro fond pracovních vláken.</span><span class="sxs-lookup"><span data-stu-id="d4edd-185">The `ThreadPoolMaxThreads` property configures the maximum number of threads for the worker thread pool.</span></span> <span data-ttu-id="d4edd-186">Další informace najdete v tématu [maximální počet vláken](../run-time-config/threading.md#maximum-threads).</span><span class="sxs-lookup"><span data-stu-id="d4edd-186">For more information, see [Maximum threads](../run-time-config/threading.md#maximum-threads).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
  </PropertyGroup>
</Project>
```

### <a name="threadpoolminthreads"></a><span data-ttu-id="d4edd-187">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="d4edd-187">ThreadPoolMinThreads</span></span>

<span data-ttu-id="d4edd-188">`ThreadPoolMinThreads` Vlastnost konfiguruje minimální počet vláken pro fond pracovních vláken.</span><span class="sxs-lookup"><span data-stu-id="d4edd-188">The `ThreadPoolMinThreads` property configures the minimum number of threads for the worker thread pool.</span></span> <span data-ttu-id="d4edd-189">Další informace najdete v tématu [minimální počet vláken](../run-time-config/threading.md#minimum-threads).</span><span class="sxs-lookup"><span data-stu-id="d4edd-189">For more information, see [Minimum threads](../run-time-config/threading.md#minimum-threads).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  </PropertyGroup>
</Project>
```

### <a name="tieredcompilation"></a><span data-ttu-id="d4edd-190">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="d4edd-190">TieredCompilation</span></span>

<span data-ttu-id="d4edd-191">`TieredCompilation` Vlastnost určuje, zda kompilátor JIT (just-in-time) používá [vrstvenou kompilaci](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="d4edd-191">The `TieredCompilation` property configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="d4edd-192">Nastavte hodnotu `false` na zakázat vrstvenou kompilaci.</span><span class="sxs-lookup"><span data-stu-id="d4edd-192">Set the value to `false` to disable tiered compilation.</span></span> <span data-ttu-id="d4edd-193">Další informace najdete v tématu [vrstvená kompilace](../run-time-config/compilation.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="d4edd-193">For more information, see [Tiered compilation](../run-time-config/compilation.md#tiered-compilation).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TieredCompilation>false</TieredCompilation>
  </PropertyGroup>
</Project>
```

### <a name="tieredcompilationquickjit"></a><span data-ttu-id="d4edd-194">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="d4edd-194">TieredCompilationQuickJit</span></span>

<span data-ttu-id="d4edd-195">`TieredCompilationQuickJit` Vlastnost konfiguruje, zda kompilátor JIT používá rychlou JIT.</span><span class="sxs-lookup"><span data-stu-id="d4edd-195">The `TieredCompilationQuickJit` property configures whether the JIT compiler uses quick JIT.</span></span> <span data-ttu-id="d4edd-196">Nastavením hodnoty `false` na zakážete rychlou JIT.</span><span class="sxs-lookup"><span data-stu-id="d4edd-196">Set the value to `false` to disable quick JIT.</span></span> <span data-ttu-id="d4edd-197">Další informace najdete v tématu [rychlá JIT](../run-time-config/compilation.md#quick-jit).</span><span class="sxs-lookup"><span data-stu-id="d4edd-197">For more information, see [Quick JIT](../run-time-config/compilation.md#quick-jit).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
  </PropertyGroup>
</Project>
```

### <a name="tieredcompilationquickjitforloops"></a><span data-ttu-id="d4edd-198">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="d4edd-198">TieredCompilationQuickJitForLoops</span></span>

<span data-ttu-id="d4edd-199">`TieredCompilationQuickJitForLoops` Vlastnost konfiguruje, zda kompilátor JIT používá rychlou JIT v metodách, které obsahují smyčky.</span><span class="sxs-lookup"><span data-stu-id="d4edd-199">The `TieredCompilationQuickJitForLoops` property configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span> <span data-ttu-id="d4edd-200">Nastavte hodnotu na, `true` Chcete-li povolit rychlou JIT v metodách, které obsahují smyčky.</span><span class="sxs-lookup"><span data-stu-id="d4edd-200">Set the value to `true` to enable quick JIT on methods that contain loops.</span></span> <span data-ttu-id="d4edd-201">Další informace najdete v tématu [rychlá JIT pro smyčky](../run-time-config/compilation.md#quick-jit-for-loops).</span><span class="sxs-lookup"><span data-stu-id="d4edd-201">For more information, see [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
  </PropertyGroup>
</Project>
```

## <a name="nuget-packages"></a><span data-ttu-id="d4edd-202">Balíčky NuGet</span><span class="sxs-lookup"><span data-stu-id="d4edd-202">NuGet packages</span></span>

- [<span data-ttu-id="d4edd-203">PackageReference</span><span class="sxs-lookup"><span data-stu-id="d4edd-203">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="d4edd-204">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="d4edd-204">AssetTargetFallback</span></span>](#assettargetfallback)

### <a name="packagereference"></a><span data-ttu-id="d4edd-205">PackageReference</span><span class="sxs-lookup"><span data-stu-id="d4edd-205">PackageReference</span></span>

<span data-ttu-id="d4edd-206">`PackageReference` Položka umožňuje zadat závislost NuGet.</span><span class="sxs-lookup"><span data-stu-id="d4edd-206">The `PackageReference` item lets you specify a NuGet dependency.</span></span> <span data-ttu-id="d4edd-207">Například můžete chtít odkazovat na jeden balíček místo [Metapackage](../packages.md#metapackages).</span><span class="sxs-lookup"><span data-stu-id="d4edd-207">For example, you may want to reference a single package instead of a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="d4edd-208">`Include` Atribut určuje ID balíčku.</span><span class="sxs-lookup"><span data-stu-id="d4edd-208">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="d4edd-209">Fragment souboru projektu v následujícím příkladu odkazuje na balíček [System. Runtime](https://www.nuget.org/packages/System.Runtime/) .</span><span class="sxs-lookup"><span data-stu-id="d4edd-209">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="d4edd-210">Další informace naleznete v tématu [odkazy na balíčky v souborech projektu](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="d4edd-210">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="assettargetfallback"></a><span data-ttu-id="d4edd-211">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="d4edd-211">AssetTargetFallback</span></span>

<span data-ttu-id="d4edd-212">`AssetTargetFallback` Vlastnost umožňuje určit další kompatibilní verze rozhraní pro projekty, na které projekt odkazuje, a balíčky NuGet, které váš projekt spotřebovává.</span><span class="sxs-lookup"><span data-stu-id="d4edd-212">The `AssetTargetFallback` property lets you specify additional compatible framework versions for projects that your project references and NuGet packages that your project consumes.</span></span> <span data-ttu-id="d4edd-213">Pokud například zadáte závislost balíčku pomocí `PackageReference` , ale tento balíček neobsahuje prostředky, které jsou kompatibilní s vašimi projekty `TargetFramework`, vlastnost se `AssetTargetFallback` dostane do hry.</span><span class="sxs-lookup"><span data-stu-id="d4edd-213">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="d4edd-214">Kompatibilita odkazovaného balíčku je znovu zkontrolována pomocí každé cílové architektury, která je určena v `AssetTargetFallback`.</span><span class="sxs-lookup"><span data-stu-id="d4edd-214">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span>

<span data-ttu-id="d4edd-215">Můžete nastavit `AssetTargetFallback` vlastnost na jednu nebo více [cílových verzí rozhraní .NET Framework](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="d4edd-215">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <PropertyGroup>
    <AssetTargetFallback>net461</AssetTargetFallback>
  </PropertyGroup>
</Project>
```

### <a name="pack-and-restore-targets"></a><span data-ttu-id="d4edd-216">Cíle sad a obnovení</span><span class="sxs-lookup"><span data-stu-id="d4edd-216">Pack and restore targets</span></span>

<span data-ttu-id="d4edd-217">Byl zaveden `pack` MSBuild 15,1 `restore` a cílený pro vytváření a obnovování balíčků NuGet v rámci sestavení.</span><span class="sxs-lookup"><span data-stu-id="d4edd-217">MSBuild 15.1 introduced `pack` and `restore` targets for creating and restoring NuGet packages as part of a build.</span></span> <span data-ttu-id="d4edd-218">Informace o vlastnostech MSBuild pro tyto cíle, včetně `PackageTargetFallback`, najdete v tématu [sada NuGet Pack a obnovení jako cíle MSBuild](/nuget/reference/msbuild-targets).</span><span class="sxs-lookup"><span data-stu-id="d4edd-218">For information about the MSBuild properties for these targets, including `PackageTargetFallback`, see [NuGet pack and restore as MSBuild targets](/nuget/reference/msbuild-targets).</span></span>

## <a name="see-also"></a><span data-ttu-id="d4edd-219">Viz také</span><span class="sxs-lookup"><span data-stu-id="d4edd-219">See also</span></span>

- [<span data-ttu-id="d4edd-220">Referenční dokumentace schématu MSBuild</span><span class="sxs-lookup"><span data-stu-id="d4edd-220">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="d4edd-221">Běžné vlastnosti nástroje MSBuild</span><span class="sxs-lookup"><span data-stu-id="d4edd-221">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="d4edd-222">Vlastnosti nástroje MSBuild pro balíček NuGet</span><span class="sxs-lookup"><span data-stu-id="d4edd-222">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="d4edd-223">Vlastnosti nástroje MSBuild pro obnovení NuGet</span><span class="sxs-lookup"><span data-stu-id="d4edd-223">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="d4edd-224">Přizpůsobení sestavení</span><span class="sxs-lookup"><span data-stu-id="d4edd-224">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
