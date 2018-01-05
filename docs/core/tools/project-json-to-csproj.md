---
title: "porovnání Project.JSON a csproj - .NET Core"
description: "V tématu mapování mezi elementy project.json a csproj."
keywords: "Project.JSON, csproj .NET Core, nástroje MSBuild"
author: natemcmaster
ms.author: mairaw
ms.date: 03/13/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 79c50621-a24a-4e64-bbb9-b953113e841c
ms.workload: dotnetcore
ms.openlocfilehash: 655f74def4d6163959d7dbbe605f7322fb0573c8
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="a-mapping-between-projectjson-and-csproj-properties"></a><span data-ttu-id="21e41-104">Mapování mezi project.json a csproj vlastnosti</span><span class="sxs-lookup"><span data-stu-id="21e41-104">A mapping between project.json and csproj properties</span></span>

<span data-ttu-id="21e41-105">Podle [McMaster Jan](https://github.com/natemcmaster)</span><span class="sxs-lookup"><span data-stu-id="21e41-105">By [Nate McMaster](https://github.com/natemcmaster)</span></span>

<span data-ttu-id="21e41-106">Během vývoje nástrojů .NET Core, návrhu důležité změně již nepodporují *project.json* soubory a místo toho přesunout do formátu nástroje MSBuild/csproj projekty .NET Core.</span><span class="sxs-lookup"><span data-stu-id="21e41-106">During the development of the .NET Core tooling, an important design change was made to no longer support *project.json* files and instead move the .NET Core projects to the MSBuild/csproj format.</span></span>

<span data-ttu-id="21e41-107">Tento článek ukazuje, jak nastavení v *project.json* jsou reprezentované ve formátu MSBuild/csproj, takže můžete naučit používat nový formát a pochopit změny provedené pomocí nástrojů pro migraci, když provádíte upgrade projektu pro nejnovější verzi nástrojů.</span><span class="sxs-lookup"><span data-stu-id="21e41-107">This article shows how the settings in *project.json* are represented in the MSBuild/csproj format so you can learn how to use the new format and understand the changes made by the migration tools when you're upgrading your project to the latest version of the tooling.</span></span> 
 
## <a name="the-csproj-format"></a><span data-ttu-id="21e41-108">Formát csproj</span><span class="sxs-lookup"><span data-stu-id="21e41-108">The csproj format</span></span>

<span data-ttu-id="21e41-109">Nový formát \*.csproj, je ve formátu formátu XML.</span><span class="sxs-lookup"><span data-stu-id="21e41-109">The new format, \*.csproj, is an XML-based format.</span></span> <span data-ttu-id="21e41-110">Následující příklad ukazuje na kořenový uzel .NET Core projekt pomocí `Microsoft.NET.Sdk`.</span><span class="sxs-lookup"><span data-stu-id="21e41-110">The following example shows the root node of a .NET Core project using the `Microsoft.NET.Sdk`.</span></span> <span data-ttu-id="21e41-111">Pro webové projekty, je sada SDK používá `Microsoft.NET.Sdk.Web`.</span><span class="sxs-lookup"><span data-stu-id="21e41-111">For web projects, the SDK used is `Microsoft.NET.Sdk.Web`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
...
</Project>
```

## <a name="common-top-level-properties"></a><span data-ttu-id="21e41-112">Běžné vlastnosti nejvyšší úrovně</span><span class="sxs-lookup"><span data-stu-id="21e41-112">Common top-level properties</span></span>

### <a name="name"></a><span data-ttu-id="21e41-113">name</span><span class="sxs-lookup"><span data-stu-id="21e41-113">name</span></span>
```json
{
  "name": "MyProjectName"
}
```

<span data-ttu-id="21e41-114">Již není podporována.</span><span class="sxs-lookup"><span data-stu-id="21e41-114">No longer supported.</span></span> <span data-ttu-id="21e41-115">V csproj ten je daný název souboru projektu, který je definovaný název adresáře.</span><span class="sxs-lookup"><span data-stu-id="21e41-115">In csproj, this is determined by the project filename, which is defined by the directory name.</span></span> <span data-ttu-id="21e41-116">Například `MyProjectName.csproj`.</span><span class="sxs-lookup"><span data-stu-id="21e41-116">For example, `MyProjectName.csproj`.</span></span>

<span data-ttu-id="21e41-117">Ve výchozím nastavení, určuje název souboru projektu také hodnotu `<AssemblyName>` a `<PackageId>` vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="21e41-117">By default, the project filename also specifies the value of the `<AssemblyName>` and `<PackageId>` properties.</span></span> 

```xml
<PropertyGroup>
  <AssemblyName>MyProjectName</AssemblyName>
  <PackageId>MyProjectName</PackageId>
</PropertyGroup>
```

<span data-ttu-id="21e41-118">`<AssemblyName>` Bude mít jinou hodnotu než `<PackageId>` Pokud `buildOptions\outputName` vlastnost byla definována v souboru project.json.</span><span class="sxs-lookup"><span data-stu-id="21e41-118">The `<AssemblyName>` will have a different value than `<PackageId>` if `buildOptions\outputName` property was defined in project.json.</span></span> <span data-ttu-id="21e41-119">Další informace najdete v tématu [další běžné možnosti sestavení](#other-common-build-options).</span><span class="sxs-lookup"><span data-stu-id="21e41-119">For more information, see [Other common build options](#other-common-build-options).</span></span>

### <a name="version"></a><span data-ttu-id="21e41-120">verze</span><span class="sxs-lookup"><span data-stu-id="21e41-120">version</span></span>

```json
{
  "version": "1.0.0-alpha-*"
}
```
<span data-ttu-id="21e41-121">Použití `VersionPrefix` a `VersionSuffix` vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="21e41-121">Use the `VersionPrefix` and `VersionSuffix` properties:</span></span>

```xml
<PropertyGroup>
  <VersionPrefix>1.0.0</VersionPrefix>
  <VersionSuffix>alpha</VersionSuffix>
</PropertyGroup>
```

<span data-ttu-id="21e41-122">Můžete také `Version` vlastnost, ale může přepsat nastavení verze během balení:</span><span class="sxs-lookup"><span data-stu-id="21e41-122">You can also use the `Version` property, but this may override version settings during packaging:</span></span>

```xml
<PropertyGroup>
  <Version>1.0.0-alpha</Version>
</PropertyGroup>
```

### <a name="other-common-root-level-options"></a><span data-ttu-id="21e41-123">Další běžné možnosti kořenové úrovně</span><span class="sxs-lookup"><span data-stu-id="21e41-123">Other common root-level options</span></span>

```json
{
  "authors": [ "Anne", "Bob" ],
  "company": "Contoso",
  "language": "en-US",
  "title": "My library",
  "description": "This is my library.\r\nAnd it's really great!",
  "copyright": "Nugetizer 3000",
  "userSecretsId": "xyz123"
}
```

```xml
<PropertyGroup>
  <Authors>Anne;Bob</Authors>
  <Company>Contoso</Company>
  <NeutralLanguage>en-US</NeutralLanguage>
  <AssemblyTitle>My library</AssemblyTitle>
  <Description>This is my library.
And it's really great!</Description>
  <Copyright>Nugetizer 3000</Copyright>
  <UserSecretsId>xyz123</UserSecretsId>
</PropertyGroup>
```

## <a name="frameworks"></a><span data-ttu-id="21e41-124">rozhraní</span><span class="sxs-lookup"><span data-stu-id="21e41-124">frameworks</span></span>

### <a name="one-target-framework"></a><span data-ttu-id="21e41-125">Jeden cíl framework</span><span class="sxs-lookup"><span data-stu-id="21e41-125">One target framework</span></span>
```json
{
  "frameworks": {
    "netcoreapp1.0": {}
  }
}
```

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp1.0</TargetFramework>
</PropertyGroup>
```

### <a name="multiple-target-frameworks"></a><span data-ttu-id="21e41-126">Více cílové rozhraní</span><span class="sxs-lookup"><span data-stu-id="21e41-126">Multiple target frameworks</span></span>

```json
{
  "frameworks": {
    "netcoreapp1.0": {},
    "net451": {}
  }
}
```

<span data-ttu-id="21e41-127">Použití `TargetFrameworks` vlastnost můžete definovat seznam cílové architektury.</span><span class="sxs-lookup"><span data-stu-id="21e41-127">Use the `TargetFrameworks` property to define your list of target frameworks.</span></span> <span data-ttu-id="21e41-128">K oddělení více hodnot framework použijte oddělte středníkem.</span><span class="sxs-lookup"><span data-stu-id="21e41-128">Use semi-colon to separate multiple framework values.</span></span> 

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp1.0;net451</TargetFrameworks>
</PropertyGroup>
```

## <a name="dependencies"></a><span data-ttu-id="21e41-129">závislosti</span><span class="sxs-lookup"><span data-stu-id="21e41-129">dependencies</span></span>

> [!IMPORTANT]
> <span data-ttu-id="21e41-130">Pokud je závislost **projektu** a nejedná se o balíček, formát se liší.</span><span class="sxs-lookup"><span data-stu-id="21e41-130">If the dependency is a **project** and not a package, the format is different.</span></span> <span data-ttu-id="21e41-131">Další informace najdete v tématu [typ závislosti](#dependency-type) části.</span><span class="sxs-lookup"><span data-stu-id="21e41-131">For more information, see the [dependency type](#dependency-type) section.</span></span>

### <a name="netstandardlibrary-metapackage"></a><span data-ttu-id="21e41-132">NETStandard.Library metapackage</span><span class="sxs-lookup"><span data-stu-id="21e41-132">NETStandard.Library metapackage</span></span>

```json
{
  "dependencies": {
    "NETStandard.Library": "1.6.0"
  }
}
```

```xml
<PropertyGroup>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

### <a name="microsoftnetcoreapp-metapackage"></a><span data-ttu-id="21e41-133">Microsoft.NETCore.App metapackage</span><span class="sxs-lookup"><span data-stu-id="21e41-133">Microsoft.NETCore.App metapackage</span></span>

```json
{
  "dependencies": {
    "Microsoft.NETCore.App": "1.0.0"
  }
}
```

```xml
<PropertyGroup>
  <RuntimeFrameworkVersion>1.0.3</RuntimeFrameworkVersion>
</PropertyGroup>
```

<span data-ttu-id="21e41-134">Všimněte si, že `<RuntimeFrameworkVersion>` hodnota v migrovaných projektu je dáno verzi sady SDK, které jste nainstalovali.</span><span class="sxs-lookup"><span data-stu-id="21e41-134">Note that the `<RuntimeFrameworkVersion>` value in the migrated project is determined by the version of the SDK you have installed.</span></span>

### <a name="top-level-dependencies"></a><span data-ttu-id="21e41-135">Nejvyšší úrovně závislosti</span><span class="sxs-lookup"><span data-stu-id="21e41-135">Top-level dependencies</span></span>
```json
{
  "dependencies": {
    "Microsoft.AspNetCore": "1.1.0"
  }
}
```

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore" Version="1.1.0" />
</ItemGroup>
```

### <a name="per-framework-dependencies"></a><span data-ttu-id="21e41-136">Závislosti za architektury</span><span class="sxs-lookup"><span data-stu-id="21e41-136">Per-framework dependencies</span></span>
```json
{
  "framework": {
    "net451": {
      "dependencies": {
        "System.Collections.Immutable": "1.3.1"
      }
    },
    "netstandard1.5": {
      "dependencies": {
        "Newtonsoft.Json": "9.0.1"
      }
    }
  }
}
```

```xml
<ItemGroup Condition="'$(TargetFramework)'=='net451'">
  <PackageReference Include="System.Collections.Immutable" Version="1.3.1" />
</ItemGroup>

<ItemGroup Condition="'$(TargetFramework)'=='netstandard1.5'">
  <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
</ItemGroup>
```

### <a name="imports"></a><span data-ttu-id="21e41-137">importy</span><span class="sxs-lookup"><span data-stu-id="21e41-137">imports</span></span>

```json
{
  "dependencies": {
    "YamlDotNet": "4.0.1-pre309"
  },
  "frameworks": {
    "netcoreapp1.0": {
      "imports": [
        "dnxcore50",
        "dotnet"
      ]
    }
  }
}
```

```xml
<PropertyGroup>
  <PackageTargetFallback>dnxcore50;dotnet</PackageTargetFallback>
</PropertyGroup>
<ItemGroup>
  <PackageReference Include="YamlDotNet" Version="4.0.1-pre309" />
</ItemGroup>
```

### <a name="dependency-type"></a><span data-ttu-id="21e41-138">Typ závislosti</span><span class="sxs-lookup"><span data-stu-id="21e41-138">dependency type</span></span>

#### <a name="type-project"></a><span data-ttu-id="21e41-139">Typ: projektu</span><span class="sxs-lookup"><span data-stu-id="21e41-139">type: project</span></span>
```json
{
  "dependencies": {
    "MyOtherProject": "1.0.0-*",
    "AnotherProject": {
      "type": "project"
    }
  }
}
```

```xml
<ItemGroup>
  <ProjectReference Include="..\MyOtherProject\MyOtherProject.csproj" />
  <ProjectReference Include="..\AnotherProject\AnotherProject.csproj" />
</ItemGroup>
```

> [!NOTE]
> <span data-ttu-id="21e41-140">Tím by došlo k přerušení způsob který `dotnet pack --version-suffix $suffix` Určuje verzi závislostí odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="21e41-140">This will break the way that `dotnet pack --version-suffix $suffix` determines the dependency version of a project reference.</span></span>


#### <a name="type-build"></a><span data-ttu-id="21e41-141">Typ: sestavení</span><span class="sxs-lookup"><span data-stu-id="21e41-141">type: build</span></span>
```json
{
  "dependencies": {
    "Microsoft.EntityFrameworkCore.Design": {
      "version": "1.1.0",
      "type": "build"
    }
  }
}
```

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.EntityFrameworkCore.Design" Version="1.1.0" PrivateAssets="All" />
</ItemGroup>
```

#### <a name="type-platform"></a><span data-ttu-id="21e41-142">Typ: platforma</span><span class="sxs-lookup"><span data-stu-id="21e41-142">type: platform</span></span>
```json
{
  "dependencies": {
    "Microsoft.NETCore.App": {
      "version": "1.1.0",
      "type": "platform"
    }
  }
}
```

<span data-ttu-id="21e41-143">V csproj není žádný ekvivalent.</span><span class="sxs-lookup"><span data-stu-id="21e41-143">There is no equivalent in csproj.</span></span> 

## <a name="runtimes"></a><span data-ttu-id="21e41-144">Moduly runtime</span><span class="sxs-lookup"><span data-stu-id="21e41-144">runtimes</span></span>
```json
{
  "runtimes": {
    "win7-x64": {},
    "osx.10.11-x64": {},
    "ubuntu.16.04-x64": {}
  }
}
```

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win7-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="standalone-apps-self-contained-deployment"></a><span data-ttu-id="21e41-145">Samostatné aplikace (samostatná nasazení)</span><span class="sxs-lookup"><span data-stu-id="21e41-145">Standalone apps (self-contained deployment)</span></span>
<span data-ttu-id="21e41-146">V souboru project.json definování `runtimes` části znamená byla aplikace samostatné během sestavení a publikování.</span><span class="sxs-lookup"><span data-stu-id="21e41-146">In project.json, defining a `runtimes` section means the app was standalone during build and publish.</span></span>
<span data-ttu-id="21e41-147">V nástroji MSBuild, jsou všechny projekty *přenosné* během vytváření sestavení, ale mohou být uvedeny jako samostatné.</span><span class="sxs-lookup"><span data-stu-id="21e41-147">In MSBuild, all projects are *portable* during build, but can be published as standalone.</span></span>

`dotnet publish --framework netcoreapp1.0 --runtime osx.10.11-x64`

<span data-ttu-id="21e41-148">Další informace najdete v tématu [samostatná nasazení (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="21e41-148">For more information, see [Self-contained deployments (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span>

## <a name="tools"></a><span data-ttu-id="21e41-149">nástroje</span><span class="sxs-lookup"><span data-stu-id="21e41-149">tools</span></span>
```json
{
  "tools": {
    "Microsoft.EntityFrameworkCore.Tools.DotNet": "1.0.0-*"
  }
}
```

```xml
<ItemGroup>
  <DotNetCliToolReference Include="Microsoft.EntityFrameworkCore.Tools.DotNet" Version="1.0.0" />
</ItemGroup>
```

> [!NOTE]
> <span data-ttu-id="21e41-150">`imports`nástroje, nejsou podporovány v csproj.</span><span class="sxs-lookup"><span data-stu-id="21e41-150">`imports` on tools are not supported in csproj.</span></span> <span data-ttu-id="21e41-151">Nástroje, které je třeba importy nebude fungovat s novým `Microsoft.NET.Sdk`.</span><span class="sxs-lookup"><span data-stu-id="21e41-151">Tools that need imports will not work with the new `Microsoft.NET.Sdk`.</span></span>

## <a name="buildoptions"></a><span data-ttu-id="21e41-152">buildOptions</span><span class="sxs-lookup"><span data-stu-id="21e41-152">buildOptions</span></span>

<span data-ttu-id="21e41-153">Viz také [soubory](#files).</span><span class="sxs-lookup"><span data-stu-id="21e41-153">See also [Files](#files).</span></span>

### <a name="emitentrypoint"></a><span data-ttu-id="21e41-154">emitEntryPoint</span><span class="sxs-lookup"><span data-stu-id="21e41-154">emitEntryPoint</span></span>

```json
{
  "buildOptions": {
    "emitEntryPoint": true
  }
}
```

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="21e41-155">Pokud `emitEntryPoint` byla `false`, hodnota `OutputType` jsou převedeny na `Library`, což je výchozí hodnota:</span><span class="sxs-lookup"><span data-stu-id="21e41-155">If `emitEntryPoint` was `false`, the value of `OutputType` is converted to `Library`, which is the default value:</span></span>

```json
{
  "buildOptions": {
    "emitEntryPoint": false
  }
}
```

```xml
<PropertyGroup>
  <OutputType>Library</OutputType>
  <!-- or, omit altogether. It defaults to 'Library' -->
</PropertyGroup>
```

### <a name="keyfile"></a><span data-ttu-id="21e41-156">keyFile</span><span class="sxs-lookup"><span data-stu-id="21e41-156">keyFile</span></span>

```json
{
  "buildOptions": {
    "keyFile": "MyKey.snk"
  }
}
```

<span data-ttu-id="21e41-157">`keyFile` Element zasahuje do tří vlastnosti v nástroji MSBuild:</span><span class="sxs-lookup"><span data-stu-id="21e41-157">The `keyFile` element expands to three properties in MSBuild:</span></span>

```xml
<PropertyGroup>
  <AssemblyOriginatorKeyFile>MyKey.snk</AssemblyOriginatorKeyFile>
  <SignAssembly>true</SignAssembly>
  <PublicSign Condition="'$(OS)' != 'Windows_NT'">true</PublicSign>
</PropertyGroup>
```

### <a name="other-common-build-options"></a><span data-ttu-id="21e41-158">Další běžné možnosti sestavení</span><span class="sxs-lookup"><span data-stu-id="21e41-158">Other common build options</span></span>

```json
{
  "buildOptions": {
    "warningsAsErrors": true,
    "nowarn": ["CS0168", "CS0219"],
    "xmlDoc": true,
    "preserveCompilationContext": true,
    "outputName": "Different.AssemblyName",
    "debugType": "portable",
    "allowUnsafe": true,
    "define": ["TEST", "OTHERCONDITION"]
  }
}
```

```xml
<PropertyGroup>
  <TreatWarningsAsErrors>true</TreatWarningsAsErrors>
  <NoWarn>$(NoWarn);CS0168;CS0219</NoWarn>
  <GenerateDocumentationFile>true</GenerateDocumentationFile>
  <PreserveCompilationContext>true</PreserveCompilationContext>
  <AssemblyName>Different.AssemblyName</AssemblyName>
  <DebugType>portable</DebugType>
  <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  <DefineConstants>$(DefineConstants);TEST;OTHERCONDITION</DefineConstants>
</PropertyGroup>
```

## <a name="packoptions"></a><span data-ttu-id="21e41-159">packOptions</span><span class="sxs-lookup"><span data-stu-id="21e41-159">packOptions</span></span>

<span data-ttu-id="21e41-160">Viz také [soubory](#files).</span><span class="sxs-lookup"><span data-stu-id="21e41-160">See also [Files](#files).</span></span>

### <a name="common-pack-options"></a><span data-ttu-id="21e41-161">Běžné možnosti pack</span><span class="sxs-lookup"><span data-stu-id="21e41-161">Common pack options</span></span>

```json
{
  "packOptions": {    
    "summary": "numl is a machine learning library intended to ease the use of using standard modeling techniques for both prediction and clustering.",
    "tags": ["machine learning", "framework"],
    "releaseNotes": "Version 0.9.12-beta",
    "iconUrl": "http://numl.net/images/ico.png",
    "projectUrl": "http://numl.net",
    "licenseUrl": "https://raw.githubusercontent.com/sethjuarez/numl/master/LICENSE.md",
    "requireLicenseAcceptance": false,
    "repository": {
      "type": "git",
      "url": "https://raw.githubusercontent.com/sethjuarez/numl"
    },
    "owners": ["Seth Juarez"]
  }
}
```

```xml
<PropertyGroup>
  <!-- summary is not migrated from project.json, but you can use the <Description> property for that if needed. -->
  <PackageTags>machine learning;framework</PackageTags>
  <PackageReleaseNotes>Version 0.9.12-beta</PackageReleaseNotes>
  <PackageIconUrl>http://numl.net/images/ico.png</PackageIconUrl>
  <PackageProjectUrl>http://numl.net</PackageProjectUrl>
  <PackageLicenseUrl>https://raw.githubusercontent.com/sethjuarez/numl/master/LICENSE.md</PackageLicenseUrl>
  <PackageRequireLicenseAcceptance>false</PackageRequireLicenseAcceptance>
  <RepositoryType>git</RepositoryType>
  <RepositoryUrl>https://raw.githubusercontent.com/sethjuarez/numl</RepositoryUrl>
  <!-- owners is not supported in MSBuild -->
</PropertyGroup>
```

<span data-ttu-id="21e41-162">Není k dispozici žádný ekvivalent `owners` element v nástroji MSBuild.</span><span class="sxs-lookup"><span data-stu-id="21e41-162">There is no equivalent for the `owners` element in MSBuild.</span></span> <span data-ttu-id="21e41-163">Pro `summary`, můžete použít MSBuild `<Description>` vlastnost, i když hodnota `summary` není automaticky migrovat na tuto vlastnost, protože tuto vlastnost je namapována na [ `description` ](#-other-common-root-level-options) element.</span><span class="sxs-lookup"><span data-stu-id="21e41-163">For `summary`, you can use the MSBuild `<Description>` property, even though the value of `summary` is not migrated automatically to that property, since that property is mapped to the [`description`](#-other-common-root-level-options) element.</span></span>

## <a name="scripts"></a><span data-ttu-id="21e41-164">skripty</span><span class="sxs-lookup"><span data-stu-id="21e41-164">scripts</span></span>

```json
{
  "scripts": {
    "precompile": "generateCode.cmd",
    "postpublish": [ "obfuscate.cmd", "removeTempFiles.cmd" ]
  }
}
```

<span data-ttu-id="21e41-165">Jsou jejich ekvivalent v nástroji MSBuild [cíle](/visualstudio/msbuild/msbuild-targets):</span><span class="sxs-lookup"><span data-stu-id="21e41-165">Their equivalent in MSBuild are [targets](/visualstudio/msbuild/msbuild-targets):</span></span>

```xml
<Target Name="MyPreCompileTarget" BeforeTargets="Build">
  <Exec Command="generateCode.cmd" />
</Target>

<Target Name="MyPostCompileTarget" AfterTargets="Publish">
  <Exec Command="obfuscate.cmd" />
  <Exec Command="removeTempFiles.cmd" />
</Target>
```


## <a name="runtimeoptions"></a><span data-ttu-id="21e41-166">runtimeOptions</span><span class="sxs-lookup"><span data-stu-id="21e41-166">runtimeOptions</span></span>

```json
{
  "runtimeOptions": {
    "configProperties": {
      "System.GC.Server": true,
      "System.GC.Concurrent": true,
      "System.GC.RetainVM": true,
      "System.Threading.ThreadPool.MinThreads": 4,
      "System.Threading.ThreadPool.MaxThreads": 25
    }
  }
}
```

<span data-ttu-id="21e41-167">Všechna nastavení v této skupině s výjimkou vlastnost "System.GC.Server" se umístí do souboru s názvem *runtimeconfig.template.json* ve složce projektu s možnostmi nahoru, aby se kořenový objekt během procesu migrace:</span><span class="sxs-lookup"><span data-stu-id="21e41-167">All settings in this group, except for the "System.GC.Server" property, are placed into a file called *runtimeconfig.template.json* in the project folder, with options lifted to the root object during the migration process:</span></span>

```json
{
  "configProperties": {
    "System.GC.Concurrent": true,
    "System.GC.RetainVM": true,
    "System.Threading.ThreadPool.MinThreads": 4,
    "System.Threading.ThreadPool.MaxThreads": 25
  }
}
```

<span data-ttu-id="21e41-168">Vlastnost "System.GC.Server" je do souboru csproj migrovat:</span><span class="sxs-lookup"><span data-stu-id="21e41-168">The "System.GC.Server" property is migrated into the csproj file:</span></span>
```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

<span data-ttu-id="21e41-169">V csproj a také vlastnosti nástroje MSBuild však můžete nastavit tyto hodnoty:</span><span class="sxs-lookup"><span data-stu-id="21e41-169">However, you can set all those values in the csproj as well as MSBuild properties:</span></span>
```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
  <ConcurrentGarbageCollection>true</ConcurrentGarbageCollection>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  <ThreadPoolMaxThreads>25</ThreadPoolMaxThreads>
</PropertyGroup>
```

## <a name="shared"></a><span data-ttu-id="21e41-170">shared</span><span class="sxs-lookup"><span data-stu-id="21e41-170">shared</span></span>
```json
{
  "shared": "shared/**/*.cs"
}
```

<span data-ttu-id="21e41-171">Nepodporované ve csproj.</span><span class="sxs-lookup"><span data-stu-id="21e41-171">Not supported in csproj.</span></span> <span data-ttu-id="21e41-172">Místo toho musíte vytvořit zahrnout soubory obsahu v vaše *příponou .nuspec* souboru.</span><span class="sxs-lookup"><span data-stu-id="21e41-172">You must instead create include content files in your *.nuspec* file.</span></span> <span data-ttu-id="21e41-173">Další informace najdete v tématu [včetně soubory obsahu](/nuget/schema/nuspec#including-content-files).</span><span class="sxs-lookup"><span data-stu-id="21e41-173">For more information, see [Including content files](/nuget/schema/nuspec#including-content-files).</span></span>

## <a name="files"></a><span data-ttu-id="21e41-174">soubory </span><span class="sxs-lookup"><span data-stu-id="21e41-174">files</span></span>

<span data-ttu-id="21e41-175">V *project.json*, sestavení a aktualizací Service pack může rozšířit na zkompilování a vložit z jiné složky.</span><span class="sxs-lookup"><span data-stu-id="21e41-175">In *project.json*, build and pack could be extended to compile and embed from different folders.</span></span>
<span data-ttu-id="21e41-176">V nástroji MSBuild, to se provádí pomocí [položky](/visualstudio/msbuild/common-msbuild-project-items).</span><span class="sxs-lookup"><span data-stu-id="21e41-176">In MSBuild, this is done using [items](/visualstudio/msbuild/common-msbuild-project-items).</span></span> <span data-ttu-id="21e41-177">V následujícím příkladu je běžné převod:</span><span class="sxs-lookup"><span data-stu-id="21e41-177">The following example is a common conversion:</span></span>

```json
{
  "buildOptions": {
    "compile": {
      "copyToOutput": "notes.txt",
      "include": "../Shared/*.cs",
      "exclude": "../Shared/Not/*.cs"
    },
    "embed": {
      "include": "../Shared/*.resx"
    }
  },
  "packOptions": {
    "include": "Views/",
    "mappings": {
      "some/path/in/project.txt": "in/package.txt"
    }
  },
  "publishOptions": {
    "include": [
      "files/",
      "publishnotes.txt"
    ]
  }
}
```

```xml
<ItemGroup>
  <Compile Include="..\Shared\*.cs" Exclude="..\Shared\Not\*.cs" />
  <EmbeddedResource Include="..\Shared\*.resx" />
  <Content Include="Views\**\*" PackagePath="%(Identity)" />
  <None Include="some/path/in/project.txt" Pack="true" PackagePath="in/package.txt" />
  
  <None Include="notes.txt" CopyToOutputDirectory="Always" />
  <!-- CopyToOutputDirectory = { Always, PreserveNewest, Never } -->

  <Content Include="files\**\*" CopyToPublishDirectory="PreserveNewest" />
  <None Include="publishnotes.txt" CopyToPublishDirectory="Always" />
  <!-- CopyToPublishDirectory = { Always, PreserveNewest, Never } -->
</ItemGroup>
```

> [!NOTE]
> <span data-ttu-id="21e41-178">Mnoho výchozí [expanze názvů vzory](https://en.wikipedia.org/wiki/Glob_(programming)) automaticky přidá .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="21e41-178">Many of the default [globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are added automatically by the .NET Core SDK.</span></span>
> <span data-ttu-id="21e41-179">Další informace najdete v tématu [výchozí hodnoty položky zkompilovat](https://aka.ms/sdkimplicititems).</span><span class="sxs-lookup"><span data-stu-id="21e41-179">For more information, see [Default Compile Item Values](https://aka.ms/sdkimplicititems).</span></span>

<span data-ttu-id="21e41-180">Všechny nástroje MSBuild `ItemGroup` podporují elementy `Include`, `Exclude`, a `Remove`.</span><span class="sxs-lookup"><span data-stu-id="21e41-180">All MSBuild `ItemGroup` elements support `Include`, `Exclude`, and `Remove`.</span></span>

<span data-ttu-id="21e41-181">Můžete změnit rozložení balíček uvnitř .nupkg `PackagePath="path"`.</span><span class="sxs-lookup"><span data-stu-id="21e41-181">Package layout inside the .nupkg can be modified with `PackagePath="path"`.</span></span>

<span data-ttu-id="21e41-182">S výjimkou `Content`, většina skupiny položek vyžadují explicitně přidání `Pack="true"` mají být zahrnuty v balíčku.</span><span class="sxs-lookup"><span data-stu-id="21e41-182">Except for `Content`, most item groups require explicitly adding `Pack="true"` to be included in the package.</span></span> <span data-ttu-id="21e41-183">`Content`budou umístěny do *obsah* složky v balíčku od MSBuild `<IncludeContentInPack>` je nastavena na `true` ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="21e41-183">`Content` will be put in the *content* folder in a package since the MSBuild `<IncludeContentInPack>` property is set to `true` by default.</span></span> <span data-ttu-id="21e41-184">Další informace najdete v tématu [včetně obsahu v balíčku](/nuget/schema/msbuild-targets#including-content-in-a-package).</span><span class="sxs-lookup"><span data-stu-id="21e41-184">For more information, see [Including content in a package](/nuget/schema/msbuild-targets#including-content-in-a-package).</span></span>

<span data-ttu-id="21e41-185">`PackagePath="%(Identity)"`je krátký způsob nastavení na cestu k souboru projektu relativní cestu k balíčku.</span><span class="sxs-lookup"><span data-stu-id="21e41-185">`PackagePath="%(Identity)"` is a short way of setting package path to the project-relative file path.</span></span>

## <a name="testrunner"></a><span data-ttu-id="21e41-186">testRunner</span><span class="sxs-lookup"><span data-stu-id="21e41-186">testRunner</span></span>

### <a name="xunit"></a><span data-ttu-id="21e41-187">xUnit</span><span class="sxs-lookup"><span data-stu-id="21e41-187">xUnit</span></span>

```json
{
  "testRunner": "xunit",
  "dependencies": {
    "dotnet-test-xunit": "<any>"
  }
}
```

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.0.0-*" />
  <PackageReference Include="xunit" Version="2.2.0-*" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0-*" />
</ItemGroup>
```

### <a name="mstest"></a><span data-ttu-id="21e41-188">MSTest</span><span class="sxs-lookup"><span data-stu-id="21e41-188">MSTest</span></span>

```json
{
  "testRunner": "mstest",
  "dependencies": {
    "dotnet-test-mstest": "<any>"
  }
}
```

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.0.0-*" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.12-*" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.11-*" />
</ItemGroup>
```

## <a name="see-also"></a><span data-ttu-id="21e41-189">Viz také</span><span class="sxs-lookup"><span data-stu-id="21e41-189">See Also</span></span>

[<span data-ttu-id="21e41-190">Souhrnné informace o změnách v rozhraní příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="21e41-190">High-level overview of changes in CLI</span></span>](../tools/cli-msbuild-architecture.md)
