---
title: Vlastnosti MSBuild pro sadu Microsoft.NET.Sdk
description: Odkaz na vlastnosti MSBuild, které jsou chápány sadou .NET Core SDK.
ms.date: 02/14/2020
ms.topic: reference
ms.openlocfilehash: d4a204a1e0216313418d278ec3bd333f72db8751
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399180"
---
# <a name="msbuild-properties-for-net-core-sdk-projects"></a><span data-ttu-id="e28af-103">Vlastnosti msbuild pro projekty sady .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="e28af-103">MSBuild properties for .NET Core SDK projects</span></span>

<span data-ttu-id="e28af-104">Tato stránka popisuje vlastnosti MSBuild pro konfiguraci projektů .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e28af-104">This page describes MSBuild properties for configuring .NET Core projects.</span></span>

> [!NOTE]
> <span data-ttu-id="e28af-105">Tato stránka je nedokončená a neuvádí všechny užitečné vlastnosti MSBuild pro sadu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="e28af-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET Core SDK.</span></span> <span data-ttu-id="e28af-106">Seznam běžných vlastností MSBuild naleznete [v tématu Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="e28af-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="e28af-107">Vlastnosti rozhraní Framework</span><span class="sxs-lookup"><span data-stu-id="e28af-107">Framework properties</span></span>

- [<span data-ttu-id="e28af-108">Targetframework</span><span class="sxs-lookup"><span data-stu-id="e28af-108">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="e28af-109">Cílové rámce</span><span class="sxs-lookup"><span data-stu-id="e28af-109">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="e28af-110">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="e28af-110">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="e28af-111">Targetframework</span><span class="sxs-lookup"><span data-stu-id="e28af-111">TargetFramework</span></span>

<span data-ttu-id="e28af-112">Vlastnost `TargetFramework` určuje verzi cílového rozhraní pro aplikaci, která implicitně odkazuje na [metabalíček](../packages.md#metapackages).</span><span class="sxs-lookup"><span data-stu-id="e28af-112">The `TargetFramework` property specifies the target framework version for the app, which implicitly references a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="e28af-113">Seznam platných zástupných názvů cílové architektury naleznete v tématu [Cílové architektury v projektech ve stylu sady SDK](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="e28af-113">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="e28af-114">Další informace naleznete v tématu [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="e28af-114">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="e28af-115">Cílové rámce</span><span class="sxs-lookup"><span data-stu-id="e28af-115">TargetFrameworks</span></span>

<span data-ttu-id="e28af-116">Vlastnost `TargetFrameworks` použijte, když chcete, aby vaše aplikace cílila na více platforem.</span><span class="sxs-lookup"><span data-stu-id="e28af-116">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="e28af-117">Seznam platných zástupných názvů cílové architektury naleznete v tématu [Cílové architektury v projektech ve stylu sady SDK](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="e28af-117">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

> [!NOTE]
> <span data-ttu-id="e28af-118">Tato vlastnost je `TargetFramework` ignorována, pokud je zadán (singulární) .</span><span class="sxs-lookup"><span data-stu-id="e28af-118">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="e28af-119">Další informace naleznete v tématu [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="e28af-119">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="e28af-120">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="e28af-120">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="e28af-121">Tato vlastnost se vztahuje `netstandard1.x`pouze na projekty pomocí .</span><span class="sxs-lookup"><span data-stu-id="e28af-121">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="e28af-122">Nevztahuje se na projekty, které používají `netstandard2.x`.</span><span class="sxs-lookup"><span data-stu-id="e28af-122">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="e28af-123">`NetStandardImplicitPackageVersion` Vlastnost použijte, pokud chcete zadat verzi architektury, která je nižší než verze [metabalíčku.](../packages.md#metapackages)</span><span class="sxs-lookup"><span data-stu-id="e28af-123">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the [metapackage](../packages.md#metapackages) version.</span></span> <span data-ttu-id="e28af-124">Soubor projektu v následujícím `netstandard1.3` příkladu cíle, ale používá `NETStandard.Library`verzi 1.6.0 .</span><span class="sxs-lookup"><span data-stu-id="e28af-124">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

## <a name="publish-properties"></a><span data-ttu-id="e28af-125">Publikovat vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e28af-125">Publish properties</span></span>

- [<span data-ttu-id="e28af-126">Identifikátor runtime</span><span class="sxs-lookup"><span data-stu-id="e28af-126">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="e28af-127">Identifikátory runtime</span><span class="sxs-lookup"><span data-stu-id="e28af-127">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="e28af-128">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="e28af-128">UseAppHost</span></span>](#useapphost)

### <a name="runtimeidentifier"></a><span data-ttu-id="e28af-129">Identifikátor runtime</span><span class="sxs-lookup"><span data-stu-id="e28af-129">RuntimeIdentifier</span></span>

<span data-ttu-id="e28af-130">Vlastnost `RuntimeIdentifier` umožňuje zadat jeden [identifikátor runtime (RID)](../rid-catalog.md) pro projekt.</span><span class="sxs-lookup"><span data-stu-id="e28af-130">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="e28af-131">Rid umožňuje publikování samostatné nasazení.</span><span class="sxs-lookup"><span data-stu-id="e28af-131">The RID enables publishing a self-contained deployment.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
  </PropertyGroup>
</Project>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="e28af-132">Identifikátory runtime</span><span class="sxs-lookup"><span data-stu-id="e28af-132">RuntimeIdentifiers</span></span>

<span data-ttu-id="e28af-133">Vlastnost `RuntimeIdentifiers` umožňuje zadat seznam [identifikátorů runtime (RID)](../rid-catalog.md) pro projekt oddělený středníkem.</span><span class="sxs-lookup"><span data-stu-id="e28af-133">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="e28af-134">Tuto vlastnost použijte, pokud potřebujete publikovat pro více runtimes.</span><span class="sxs-lookup"><span data-stu-id="e28af-134">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="e28af-135">`RuntimeIdentifiers`se používá v době obnovení, aby bylo zajištěno, že správné prostředky jsou v grafu.</span><span class="sxs-lookup"><span data-stu-id="e28af-135">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="e28af-136">`RuntimeIdentifier`(singulární) může poskytnout rychlejší sestavení, když je vyžadován pouze jeden runtime.</span><span class="sxs-lookup"><span data-stu-id="e28af-136">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

### <a name="useapphost"></a><span data-ttu-id="e28af-137">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="e28af-137">UseAppHost</span></span>

<span data-ttu-id="e28af-138">Vlastnost `UseAppHost` byla zavedena ve verzi 2.1.400 sady .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="e28af-138">The `UseAppHost` property was introduced in the 2.1.400 version of the .NET Core SDK.</span></span> <span data-ttu-id="e28af-139">Určuje, zda je pro nasazení vytvořen nativní spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="e28af-139">It controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="e28af-140">Nativní spustitelný soubor je vyžadován pro samostatná nasazení.</span><span class="sxs-lookup"><span data-stu-id="e28af-140">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="e28af-141">V rozhraní .NET Core 3.0 a novějších verzích je ve výchozím nastavení vytvořen spustitelný soubor závislý na rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e28af-141">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="e28af-142">Nastavte `UseAppHost` vlastnost `false` zakázat generování spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="e28af-142">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <UseAppHost>false</UseAppHost>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="e28af-143">Další informace o nasazení naleznete v tématu [.NET Core application deployment](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="e28af-143">For more information about deployment, see [.NET Core application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="e28af-144">Kompilovat vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e28af-144">Compile properties</span></span>

### <a name="langversion"></a><span data-ttu-id="e28af-145">LangVersion</span><span class="sxs-lookup"><span data-stu-id="e28af-145">LangVersion</span></span>

<span data-ttu-id="e28af-146">Vlastnost `LangVersion` umožňuje určit konkrétní verzi programovacího jazyka.</span><span class="sxs-lookup"><span data-stu-id="e28af-146">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="e28af-147">Například pokud chcete přístup k c# `LangVersion` náhled `preview`funkce, nastavte na .</span><span class="sxs-lookup"><span data-stu-id="e28af-147">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <LangVersion>preview</LangVersion>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="e28af-148">Další informace naleznete v [tématu C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span><span class="sxs-lookup"><span data-stu-id="e28af-148">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="nuget-packages"></a><span data-ttu-id="e28af-149">Balíčky NuGet</span><span class="sxs-lookup"><span data-stu-id="e28af-149">NuGet packages</span></span>

- [<span data-ttu-id="e28af-150">Odkaz na balíček</span><span class="sxs-lookup"><span data-stu-id="e28af-150">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="e28af-151">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="e28af-151">AssetTargetFallback</span></span>](#assettargetfallback)

### <a name="packagereference"></a><span data-ttu-id="e28af-152">Odkaz na balíček</span><span class="sxs-lookup"><span data-stu-id="e28af-152">PackageReference</span></span>

<span data-ttu-id="e28af-153">Položka `PackageReference` umožňuje zadat závislost NuGet.</span><span class="sxs-lookup"><span data-stu-id="e28af-153">The `PackageReference` item lets you specify a NuGet dependency.</span></span> <span data-ttu-id="e28af-154">Můžete například odkazovat na jeden balíček namísto [metabalíčku](../packages.md#metapackages).</span><span class="sxs-lookup"><span data-stu-id="e28af-154">For example, you may want to reference a single package instead of a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="e28af-155">Atribut `Include` určuje ID balíčku.</span><span class="sxs-lookup"><span data-stu-id="e28af-155">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="e28af-156">Fragment souboru projektu v následujícím příkladu odkazuje na balíček [System.Runtime.](https://www.nuget.org/packages/System.Runtime/)</span><span class="sxs-lookup"><span data-stu-id="e28af-156">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="e28af-157">Další informace naleznete [v tématu Odkazy na balíčky v souborech projektu](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="e28af-157">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="assettargetfallback"></a><span data-ttu-id="e28af-158">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="e28af-158">AssetTargetFallback</span></span>

<span data-ttu-id="e28af-159">Vlastnost `AssetTargetFallback` umožňuje zadat další verze architektury kompatibilní pro projekty, které odkazuje na váš projekt a Balíčky NuGet, které váš projekt spotřebovává.</span><span class="sxs-lookup"><span data-stu-id="e28af-159">The `AssetTargetFallback` property lets you specify additional compatible framework versions for projects that your project references and NuGet packages that your project consumes.</span></span> <span data-ttu-id="e28af-160">Například pokud zadáte závislost balíčku `PackageReference` pomocí, ale tento balíček neobsahuje prostředky, `TargetFramework`které `AssetTargetFallback` jsou kompatibilní s projekty , vlastnost vstoupí do hry.</span><span class="sxs-lookup"><span data-stu-id="e28af-160">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="e28af-161">Kompatibilita odkazovaného balíčku je znovu kontrolována pomocí každého `AssetTargetFallback`cílového rozhraní, které je zadáno v aplikaci .</span><span class="sxs-lookup"><span data-stu-id="e28af-161">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span>

<span data-ttu-id="e28af-162">Vlastnost můžete `AssetTargetFallback` nastavit na jednu nebo více [verzí cílové architektury](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="e28af-162">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <PropertyGroup>
    <AssetTargetFallback>net461</AssetTargetFallback>
  </PropertyGroup>
</Project>
```

### <a name="pack-and-restore-targets"></a><span data-ttu-id="e28af-163">Sbalit a obnovit cíle</span><span class="sxs-lookup"><span data-stu-id="e28af-163">Pack and restore targets</span></span>

<span data-ttu-id="e28af-164">MSBuild 15.1 `pack` zavedena a `restore` cíle pro vytváření a obnovení nuget balíčky jako součást sestavení.</span><span class="sxs-lookup"><span data-stu-id="e28af-164">MSBuild 15.1 introduced `pack` and `restore` targets for creating and restoring NuGet packages as part of a build.</span></span> <span data-ttu-id="e28af-165">Informace o vlastnostech MSBuild pro `PackageTargetFallback`tyto cíle, včetně naleznete v [tématu NuGet pack a restore as MSBuild targets](/nuget/reference/msbuild-targets).</span><span class="sxs-lookup"><span data-stu-id="e28af-165">For information about the MSBuild properties for these targets, including `PackageTargetFallback`, see [NuGet pack and restore as MSBuild targets](/nuget/reference/msbuild-targets).</span></span>

## <a name="see-also"></a><span data-ttu-id="e28af-166">Viz také</span><span class="sxs-lookup"><span data-stu-id="e28af-166">See also</span></span>

- [<span data-ttu-id="e28af-167">Odkaz na schéma msbuild</span><span class="sxs-lookup"><span data-stu-id="e28af-167">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="e28af-168">Běžné vlastnosti MSBuild</span><span class="sxs-lookup"><span data-stu-id="e28af-168">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="e28af-169">Vlastnosti MSBuild pro balíček NuGet</span><span class="sxs-lookup"><span data-stu-id="e28af-169">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="e28af-170">Vlastnosti MSBuild pro obnovení NuGet</span><span class="sxs-lookup"><span data-stu-id="e28af-170">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="e28af-171">Přizpůsobení sestavení</span><span class="sxs-lookup"><span data-stu-id="e28af-171">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
