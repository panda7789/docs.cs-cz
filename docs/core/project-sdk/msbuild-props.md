---
title: Vlastnosti nástroje MSBuild pro Microsoft. NET. SDK
description: Referenční informace o vlastnostech MSBuild, které jsou srozumitelné pro .NET Core SDK.
ms.date: 02/14/2020
ms.topic: reference
ms.openlocfilehash: 00d9152d864ac0727a511f4c3c15abba82aab904
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503811"
---
# <a name="msbuild-properties-for-net-core-sdk-projects"></a><span data-ttu-id="11d48-103">Vlastnosti nástroje MSBuild pro projekty .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="11d48-103">MSBuild properties for .NET Core SDK projects</span></span>

<span data-ttu-id="11d48-104">Tato stránka popisuje vlastnosti nástroje MSBuild pro konfiguraci projektů .NET Core.</span><span class="sxs-lookup"><span data-stu-id="11d48-104">This page describes MSBuild properties for configuring .NET Core projects.</span></span>

> [!NOTE]
> <span data-ttu-id="11d48-105">Tato stránka je Nedokončená práce a neobsahuje seznam všech užitečných vlastností MSBuild pro .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="11d48-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET Core SDK.</span></span> <span data-ttu-id="11d48-106">Seznam běžných vlastností MSBuild najdete v tématu [běžné vlastnosti MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="11d48-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="11d48-107">Vlastnosti architektury</span><span class="sxs-lookup"><span data-stu-id="11d48-107">Framework properties</span></span>

- [<span data-ttu-id="11d48-108">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="11d48-108">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="11d48-109">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="11d48-109">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="11d48-110">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="11d48-110">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="11d48-111">targetFramework</span><span class="sxs-lookup"><span data-stu-id="11d48-111">TargetFramework</span></span>

<span data-ttu-id="11d48-112">Vlastnost `TargetFramework` určuje cílovou verzi rozhraní .NET Framework pro aplikaci, která implicitně odkazuje na [Metapackage](../packages.md#metapackages).</span><span class="sxs-lookup"><span data-stu-id="11d48-112">The `TargetFramework` property specifies the target framework version for the app, which implicitly references a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="11d48-113">Seznam platných monikerů cílového rozhraní Framework naleznete v tématu [cílové architektury v projektech ve stylu sady SDK](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="11d48-113">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="11d48-114">Další informace naleznete v tématu [cílová rozhraní v projektech ve stylu sady SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="11d48-114">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="11d48-115">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="11d48-115">TargetFrameworks</span></span>

<span data-ttu-id="11d48-116">Vlastnost `TargetFrameworks` použijte v případě, že chcete, aby aplikace byla cílena na více platforem.</span><span class="sxs-lookup"><span data-stu-id="11d48-116">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="11d48-117">Seznam platných monikerů cílového rozhraní Framework naleznete v tématu [cílové architektury v projektech ve stylu sady SDK](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="11d48-117">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

> [!NOTE]
> <span data-ttu-id="11d48-118">Tato vlastnost je ignorována, pokud je zadána `TargetFramework` (v jednotném čísle).</span><span class="sxs-lookup"><span data-stu-id="11d48-118">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="11d48-119">Další informace naleznete v tématu [cílová rozhraní v projektech ve stylu sady SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="11d48-119">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="11d48-120">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="11d48-120">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="11d48-121">Tato vlastnost se vztahuje pouze na projekty používající `netstandard1.x`.</span><span class="sxs-lookup"><span data-stu-id="11d48-121">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="11d48-122">Neplatí pro projekty, které používají `netstandard2.x`.</span><span class="sxs-lookup"><span data-stu-id="11d48-122">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="11d48-123">Vlastnost `NetStandardImplicitPackageVersion` použijte, pokud chcete zadat verzi rozhraní, která je nižší než verze [Metapackage](../packages.md#metapackages) .</span><span class="sxs-lookup"><span data-stu-id="11d48-123">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the [metapackage](../packages.md#metapackages) version.</span></span> <span data-ttu-id="11d48-124">Soubor projektu v následujícím příkladu cílí na `netstandard1.3`, ale používá verzi 1.6.0 `NETStandard.Library`.</span><span class="sxs-lookup"><span data-stu-id="11d48-124">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

## <a name="publish-properties"></a><span data-ttu-id="11d48-125">Vlastnosti publikování</span><span class="sxs-lookup"><span data-stu-id="11d48-125">Publish properties</span></span>

- [<span data-ttu-id="11d48-126">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="11d48-126">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="11d48-127">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="11d48-127">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="11d48-128">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="11d48-128">UseAppHost</span></span>](#useapphost)

### <a name="runtimeidentifier"></a><span data-ttu-id="11d48-129">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="11d48-129">RuntimeIdentifier</span></span>

<span data-ttu-id="11d48-130">Vlastnost `RuntimeIdentifier` umožňuje zadat jeden [identifikátor modulu runtime (RID)](../rid-catalog.md) pro projekt.</span><span class="sxs-lookup"><span data-stu-id="11d48-130">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="11d48-131">Identifikátor RID umožňuje publikování samostatně zahrnutého nasazení.</span><span class="sxs-lookup"><span data-stu-id="11d48-131">The RID enables publishing a self-contained deployment.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
  </PropertyGroup>
</Project>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="11d48-132">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="11d48-132">RuntimeIdentifiers</span></span>

<span data-ttu-id="11d48-133">Vlastnost `RuntimeIdentifiers` umožňuje zadat seznam [identifikátorů modulu runtime (identifikátorů RID)](../rid-catalog.md) pro daný projekt oddělený středníkem.</span><span class="sxs-lookup"><span data-stu-id="11d48-133">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="11d48-134">Tuto vlastnost použijte v případě, že potřebujete publikovat více modulů runtime.</span><span class="sxs-lookup"><span data-stu-id="11d48-134">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="11d48-135">`RuntimeIdentifiers` se používá v době obnovení, aby se zajistilo, že jsou správné prostředky v grafu.</span><span class="sxs-lookup"><span data-stu-id="11d48-135">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="11d48-136">`RuntimeIdentifier` (jednotné) může poskytovat rychlejší sestavení, je-li vyžadován pouze jeden modul runtime.</span><span class="sxs-lookup"><span data-stu-id="11d48-136">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

### <a name="useapphost"></a><span data-ttu-id="11d48-137">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="11d48-137">UseAppHost</span></span>

<span data-ttu-id="11d48-138">Vlastnost `UseAppHost` byla představena ve verzi 2.1.400 .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="11d48-138">The `UseAppHost` property was introduced in the 2.1.400 version of the .NET Core SDK.</span></span> <span data-ttu-id="11d48-139">Určuje, zda je pro nasazení vytvořen nativní spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="11d48-139">It controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="11d48-140">Pro samostatně obsažená nasazení je vyžadován nativní spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="11d48-140">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="11d48-141">V rozhraní .NET Core 3,0 a novějších verzích je ve výchozím nastavení vytvořen spustitelný soubor závislý na rozhraní.</span><span class="sxs-lookup"><span data-stu-id="11d48-141">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="11d48-142">Nastavte vlastnost `UseAppHost` na `false`, aby se zakázalo generování spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="11d48-142">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <UseAppHost>false</UseAppHost>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="11d48-143">Další informace o nasazení naleznete v tématu [nasazení aplikace .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="11d48-143">For more information about deployment, see [.NET Core application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="11d48-144">Vlastnosti kompilace</span><span class="sxs-lookup"><span data-stu-id="11d48-144">Compile properties</span></span>

### <a name="langversion"></a><span data-ttu-id="11d48-145">Langversion –</span><span class="sxs-lookup"><span data-stu-id="11d48-145">LangVersion</span></span>

<span data-ttu-id="11d48-146">Vlastnost `LangVersion` umožňuje zadat konkrétní verzi programovacího jazyka.</span><span class="sxs-lookup"><span data-stu-id="11d48-146">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="11d48-147">Pokud například chcete získat přístup k C# funkcím verze Preview, nastavte `LangVersion` na `preview`.</span><span class="sxs-lookup"><span data-stu-id="11d48-147">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <LangVersion>preview</LangVersion>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="11d48-148">Další informace najdete v tématu [ C# jazyková verze](../../csharp/language-reference/configure-language-version.md#override-a-default).</span><span class="sxs-lookup"><span data-stu-id="11d48-148">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="nuget-packages"></a><span data-ttu-id="11d48-149">Balíčky NuGet</span><span class="sxs-lookup"><span data-stu-id="11d48-149">NuGet packages</span></span>

- [<span data-ttu-id="11d48-150">PackageReference</span><span class="sxs-lookup"><span data-stu-id="11d48-150">PackageReference</span></span>](#packagereference)

### <a name="packagereference"></a><span data-ttu-id="11d48-151">PackageReference</span><span class="sxs-lookup"><span data-stu-id="11d48-151">PackageReference</span></span>

<span data-ttu-id="11d48-152">Položka `PackageReference` umožňuje zadat závislost NuGet.</span><span class="sxs-lookup"><span data-stu-id="11d48-152">The `PackageReference` item lets you specify a NuGet dependency.</span></span> <span data-ttu-id="11d48-153">Například můžete chtít odkazovat na jeden balíček místo [Metapackage](../packages.md#metapackages).</span><span class="sxs-lookup"><span data-stu-id="11d48-153">For example, you may want to reference a single package instead of a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="11d48-154">Atribut `Include` Určuje ID balíčku.</span><span class="sxs-lookup"><span data-stu-id="11d48-154">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="11d48-155">Fragment souboru projektu v následujícím příkladu odkazuje na balíček [System. Runtime](https://www.nuget.org/packages/System.Runtime/) .</span><span class="sxs-lookup"><span data-stu-id="11d48-155">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="11d48-156">Další informace naleznete v tématu [odkazy na balíčky v souborech projektu](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="11d48-156">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="pack-and-restore-targets"></a><span data-ttu-id="11d48-157">Cíle sad a obnovení</span><span class="sxs-lookup"><span data-stu-id="11d48-157">Pack and restore targets</span></span>

<span data-ttu-id="11d48-158">MSBuild 15,1 představil `pack` a `restore` cíle pro vytváření a obnovování balíčků NuGet v rámci sestavení.</span><span class="sxs-lookup"><span data-stu-id="11d48-158">MSBuild 15.1 introduced `pack` and `restore` targets for creating and restoring NuGet packages as part of a build.</span></span> <span data-ttu-id="11d48-159">Informace o vlastnostech MSBuild pro tyto cíle, včetně `PackageTargetFallback`, najdete v tématu [sada NuGet Pack a obnovení jako cíle MSBuild](/nuget/reference/msbuild-targets).</span><span class="sxs-lookup"><span data-stu-id="11d48-159">For information about the MSBuild properties for these targets, including `PackageTargetFallback`, see [NuGet pack and restore as MSBuild targets](/nuget/reference/msbuild-targets).</span></span>

## <a name="see-also"></a><span data-ttu-id="11d48-160">Viz také</span><span class="sxs-lookup"><span data-stu-id="11d48-160">See also</span></span>

- [<span data-ttu-id="11d48-161">Referenční dokumentace schématu MSBuild</span><span class="sxs-lookup"><span data-stu-id="11d48-161">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="11d48-162">Běžné vlastnosti nástroje MSBuild</span><span class="sxs-lookup"><span data-stu-id="11d48-162">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="11d48-163">Vlastnosti nástroje MSBuild pro balíček NuGet</span><span class="sxs-lookup"><span data-stu-id="11d48-163">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="11d48-164">Vlastnosti nástroje MSBuild pro obnovení NuGet</span><span class="sxs-lookup"><span data-stu-id="11d48-164">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="11d48-165">Přizpůsobení sestavení</span><span class="sxs-lookup"><span data-stu-id="11d48-165">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
