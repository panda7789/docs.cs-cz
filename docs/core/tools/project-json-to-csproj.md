---
title: porovnání Project.JSON a csproj – .NET Core
description: Zobrazit mapování mezi project.json a csproj prvky.
author: natemcmaster
ms.author: mairaw
ms.date: 03/13/2017
ms.openlocfilehash: 369075f91c0d5ea6c7eb5d09ac2535c4e60f28f6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43419412"
---
# <a name="a-mapping-between-projectjson-and-csproj-properties"></a><span data-ttu-id="bd086-103">Mapování mezi project.json a csproj vlastnosti</span><span class="sxs-lookup"><span data-stu-id="bd086-103">A mapping between project.json and csproj properties</span></span>

<span data-ttu-id="bd086-104">Podle [Tomáš McMaster](https://github.com/natemcmaster)</span><span class="sxs-lookup"><span data-stu-id="bd086-104">By [Nate McMaster](https://github.com/natemcmaster)</span></span>

<span data-ttu-id="bd086-105">Během vývojové nástroje .NET Core, důležité změny už nebude podporovat *project.json* soubory a místo toho přesuňte projekty .NET Core do formátu nástroje MSBuild/csproj.</span><span class="sxs-lookup"><span data-stu-id="bd086-105">During the development of the .NET Core tooling, an important design change was made to no longer support *project.json* files and instead move the .NET Core projects to the MSBuild/csproj format.</span></span>

<span data-ttu-id="bd086-106">Tento článek popisuje, jak nastavení v *project.json* jsou reprezentovány ve formátu MSBuild/csproj, zjistěte, jak používají nový formát a pochopit změny provedené pomocí nástrojů pro migraci, když upgradujete projekt tak, aby nejnovější verzi nástrojů.</span><span class="sxs-lookup"><span data-stu-id="bd086-106">This article shows how the settings in *project.json* are represented in the MSBuild/csproj format so you can learn how to use the new format and understand the changes made by the migration tools when you're upgrading your project to the latest version of the tooling.</span></span>

## <a name="the-csproj-format"></a><span data-ttu-id="bd086-107">Formát csproj</span><span class="sxs-lookup"><span data-stu-id="bd086-107">The csproj format</span></span>

<span data-ttu-id="bd086-108">Nový formát \*.csproj, je ve formátu založený na formátu XML.</span><span class="sxs-lookup"><span data-stu-id="bd086-108">The new format, \*.csproj, is an XML-based format.</span></span> <span data-ttu-id="bd086-109">Následující příklad ukazuje v kořenovém uzlu projektu .NET Core pomocí `Microsoft.NET.Sdk`.</span><span class="sxs-lookup"><span data-stu-id="bd086-109">The following example shows the root node of a .NET Core project using the `Microsoft.NET.Sdk`.</span></span> <span data-ttu-id="bd086-110">Pro webové projekty, sada SDK používá je `Microsoft.NET.Sdk.Web`.</span><span class="sxs-lookup"><span data-stu-id="bd086-110">For web projects, the SDK used is `Microsoft.NET.Sdk.Web`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
...
</Project>
```

## <a name="common-top-level-properties"></a><span data-ttu-id="bd086-111">Společné vlastnosti nejvyšší úrovně</span><span class="sxs-lookup"><span data-stu-id="bd086-111">Common top-level properties</span></span>

### <a name="name"></a><span data-ttu-id="bd086-112">name</span><span class="sxs-lookup"><span data-stu-id="bd086-112">name</span></span>

```json
{
  "name": "MyProjectName"
}
```

<span data-ttu-id="bd086-113">Již nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="bd086-113">No longer supported.</span></span> <span data-ttu-id="bd086-114">V souboru csproj se určuje podle názvu souboru projektu, který je definovaný název adresáře.</span><span class="sxs-lookup"><span data-stu-id="bd086-114">In csproj, this is determined by the project filename, which is defined by the directory name.</span></span> <span data-ttu-id="bd086-115">Například `MyProjectName.csproj`.</span><span class="sxs-lookup"><span data-stu-id="bd086-115">For example, `MyProjectName.csproj`.</span></span>

<span data-ttu-id="bd086-116">Ve výchozím souboru projektu také určuje hodnotu `<AssemblyName>` a `<PackageId>` vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="bd086-116">By default, the project filename also specifies the value of the `<AssemblyName>` and `<PackageId>` properties.</span></span>

```xml
<PropertyGroup>
  <AssemblyName>MyProjectName</AssemblyName>
  <PackageId>MyProjectName</PackageId>
</PropertyGroup>
```

<span data-ttu-id="bd086-117">`<AssemblyName>` Bude mít jinou hodnotu než `<PackageId>` Pokud `buildOptions\outputName` vlastnost byla definována v souboru project.json.</span><span class="sxs-lookup"><span data-stu-id="bd086-117">The `<AssemblyName>` will have a different value than `<PackageId>` if `buildOptions\outputName` property was defined in project.json.</span></span>
<span data-ttu-id="bd086-118">Další informace najdete v tématu [další běžné možnosti sestavení](#other-common-build-options).</span><span class="sxs-lookup"><span data-stu-id="bd086-118">For more information, see [Other common build options](#other-common-build-options).</span></span>

### <a name="version"></a><span data-ttu-id="bd086-119">verze</span><span class="sxs-lookup"><span data-stu-id="bd086-119">version</span></span>

```json
{
  "version": "1.0.0-alpha-*"
}
```

<span data-ttu-id="bd086-120">Použití `VersionPrefix` a `VersionSuffix` vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="bd086-120">Use the `VersionPrefix` and `VersionSuffix` properties:</span></span>

```xml
<PropertyGroup>
  <VersionPrefix>1.0.0</VersionPrefix>
  <VersionSuffix>alpha</VersionSuffix>
</PropertyGroup>
```

<span data-ttu-id="bd086-121">Můžete také použít `Version` vlastnost, ale můžou přepsat nastavení verzí při vytváření balíčku:</span><span class="sxs-lookup"><span data-stu-id="bd086-121">You can also use the `Version` property, but this may override version settings during packaging:</span></span>

```xml
<PropertyGroup>
  <Version>1.0.0-alpha</Version>
</PropertyGroup>
```

### <a name="other-common-root-level-options"></a><span data-ttu-id="bd086-122">Další běžné možnosti na úrovni kořenového adresáře</span><span class="sxs-lookup"><span data-stu-id="bd086-122">Other common root-level options</span></span>

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

## <a name="frameworks"></a><span data-ttu-id="bd086-123">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="bd086-123">frameworks</span></span>

### <a name="one-target-framework"></a><span data-ttu-id="bd086-124">Jednu cílovou architekturu</span><span class="sxs-lookup"><span data-stu-id="bd086-124">One target framework</span></span>

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

### <a name="multiple-target-frameworks"></a><span data-ttu-id="bd086-125">Více cílových platforem</span><span class="sxs-lookup"><span data-stu-id="bd086-125">Multiple target frameworks</span></span>

```json
{
  "frameworks": {
    "netcoreapp1.0": {},
    "net451": {}
  }
}
```

<span data-ttu-id="bd086-126">Použití `TargetFrameworks` vlastnost pro definování seznamu cílových platforem.</span><span class="sxs-lookup"><span data-stu-id="bd086-126">Use the `TargetFrameworks` property to define your list of target frameworks.</span></span> <span data-ttu-id="bd086-127">Používejte středníky oddělit více hodnot rozhraní framework.</span><span class="sxs-lookup"><span data-stu-id="bd086-127">Use semi-colon to separate multiple framework values.</span></span>

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp1.0;net451</TargetFrameworks>
</PropertyGroup>
```

## <a name="dependencies"></a><span data-ttu-id="bd086-128">závislosti</span><span class="sxs-lookup"><span data-stu-id="bd086-128">dependencies</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bd086-129">Pokud je závislost **projektu** a nejedná se o balíček, formát se liší.</span><span class="sxs-lookup"><span data-stu-id="bd086-129">If the dependency is a **project** and not a package, the format is different.</span></span>
> <span data-ttu-id="bd086-130">Další informace najdete v tématu [typ závislosti](#dependency-type) oddílu.</span><span class="sxs-lookup"><span data-stu-id="bd086-130">For more information, see the [dependency type](#dependency-type) section.</span></span>

### <a name="netstandardlibrary-metapackage"></a><span data-ttu-id="bd086-131">NETStandard.Library Microsoft.aspnetcore.all</span><span class="sxs-lookup"><span data-stu-id="bd086-131">NETStandard.Library metapackage</span></span>

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

### <a name="microsoftnetcoreapp-metapackage"></a><span data-ttu-id="bd086-132">Balíčky Microsoft.NETCore.App Microsoft.aspnetcore.all</span><span class="sxs-lookup"><span data-stu-id="bd086-132">Microsoft.NETCore.App metapackage</span></span>

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

<span data-ttu-id="bd086-133">Všimněte si, že `<RuntimeFrameworkVersion>` hodnotu v migrovaného projektu určuje verzi sady SDK, které jste nainstalovali.</span><span class="sxs-lookup"><span data-stu-id="bd086-133">Note that the `<RuntimeFrameworkVersion>` value in the migrated project is determined by the version of the SDK you have installed.</span></span>

### <a name="top-level-dependencies"></a><span data-ttu-id="bd086-134">Závislosti nejvyšší úrovně</span><span class="sxs-lookup"><span data-stu-id="bd086-134">Top-level dependencies</span></span>

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

### <a name="per-framework-dependencies"></a><span data-ttu-id="bd086-135">Závislosti na rozhraní</span><span class="sxs-lookup"><span data-stu-id="bd086-135">Per-framework dependencies</span></span>

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

### <a name="imports"></a><span data-ttu-id="bd086-136">importy</span><span class="sxs-lookup"><span data-stu-id="bd086-136">imports</span></span>

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

### <a name="dependency-type"></a><span data-ttu-id="bd086-137">Typ závislosti</span><span class="sxs-lookup"><span data-stu-id="bd086-137">dependency type</span></span>

#### <a name="type-project"></a><span data-ttu-id="bd086-138">Typ: projekt</span><span class="sxs-lookup"><span data-stu-id="bd086-138">type: project</span></span>

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
> <span data-ttu-id="bd086-139">Tímto přerušíte způsobem, který `dotnet pack --version-suffix $suffix` Určuje verzi závislosti odkazu na projekt.</span><span class="sxs-lookup"><span data-stu-id="bd086-139">This will break the way that `dotnet pack --version-suffix $suffix` determines the dependency version of a project reference.</span></span>

#### <a name="type-build"></a><span data-ttu-id="bd086-140">Typ: sestavení</span><span class="sxs-lookup"><span data-stu-id="bd086-140">type: build</span></span>

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

#### <a name="type-platform"></a><span data-ttu-id="bd086-141">Typ: platforma</span><span class="sxs-lookup"><span data-stu-id="bd086-141">type: platform</span></span>

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

<span data-ttu-id="bd086-142">V souboru csproj neexistuje žádný ekvivalent.</span><span class="sxs-lookup"><span data-stu-id="bd086-142">There is no equivalent in csproj.</span></span>

## <a name="runtimes"></a><span data-ttu-id="bd086-143">Moduly runtime</span><span class="sxs-lookup"><span data-stu-id="bd086-143">runtimes</span></span>

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

### <a name="standalone-apps-self-contained-deployment"></a><span data-ttu-id="bd086-144">Samostatné aplikace (samostatná nasazení)</span><span class="sxs-lookup"><span data-stu-id="bd086-144">Standalone apps (self-contained deployment)</span></span>

<span data-ttu-id="bd086-145">V souboru project.json definování `runtimes` části znamená, že byla aplikace samostatné během sestavení a publikování.</span><span class="sxs-lookup"><span data-stu-id="bd086-145">In project.json, defining a `runtimes` section means the app was standalone during build and publish.</span></span>
<span data-ttu-id="bd086-146">V nástroji MSBuild, jsou všechny projekty *přenosné* během sestavení, ale mohou být publikovány jako samostatné.</span><span class="sxs-lookup"><span data-stu-id="bd086-146">In MSBuild, all projects are *portable* during build, but can be published as standalone.</span></span>

`dotnet publish --framework netcoreapp1.0 --runtime osx.10.11-x64`

<span data-ttu-id="bd086-147">Další informace najdete v tématu [samostatná nasazení (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="bd086-147">For more information, see [Self-contained deployments (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span>

## <a name="tools"></a><span data-ttu-id="bd086-148">nástroje</span><span class="sxs-lookup"><span data-stu-id="bd086-148">tools</span></span>

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
> <span data-ttu-id="bd086-149">`imports` v nabídce Nástroje, které nejsou podporovány v souboru csproj.</span><span class="sxs-lookup"><span data-stu-id="bd086-149">`imports` on tools are not supported in csproj.</span></span> <span data-ttu-id="bd086-150">Nástroje, které je třeba importy nebude fungovat s novými `Microsoft.NET.Sdk`.</span><span class="sxs-lookup"><span data-stu-id="bd086-150">Tools that need imports will not work with the new `Microsoft.NET.Sdk`.</span></span>

## <a name="buildoptions"></a><span data-ttu-id="bd086-151">buildOptions</span><span class="sxs-lookup"><span data-stu-id="bd086-151">buildOptions</span></span>

<span data-ttu-id="bd086-152">Viz také [soubory](#files).</span><span class="sxs-lookup"><span data-stu-id="bd086-152">See also [Files](#files).</span></span>

### <a name="emitentrypoint"></a><span data-ttu-id="bd086-153">emitEntryPoint</span><span class="sxs-lookup"><span data-stu-id="bd086-153">emitEntryPoint</span></span>

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

<span data-ttu-id="bd086-154">Pokud `emitEntryPoint` byl `false`, hodnota `OutputType` je převedena na `Library`, což je výchozí hodnota:</span><span class="sxs-lookup"><span data-stu-id="bd086-154">If `emitEntryPoint` was `false`, the value of `OutputType` is converted to `Library`, which is the default value:</span></span>

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

### <a name="keyfile"></a><span data-ttu-id="bd086-155">KeyFile</span><span class="sxs-lookup"><span data-stu-id="bd086-155">keyFile</span></span>

```json
{
  "buildOptions": {
    "keyFile": "MyKey.snk"
  }
}
```

<span data-ttu-id="bd086-156">`keyFile` Rozšíří element třem vlastnostem v nástroji MSBuild:</span><span class="sxs-lookup"><span data-stu-id="bd086-156">The `keyFile` element expands to three properties in MSBuild:</span></span>

```xml
<PropertyGroup>
  <AssemblyOriginatorKeyFile>MyKey.snk</AssemblyOriginatorKeyFile>
  <SignAssembly>true</SignAssembly>
  <PublicSign Condition="'$(OS)' != 'Windows_NT'">true</PublicSign>
</PropertyGroup>
```

### <a name="other-common-build-options"></a><span data-ttu-id="bd086-157">Další běžné možnosti sestavení</span><span class="sxs-lookup"><span data-stu-id="bd086-157">Other common build options</span></span>

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

## <a name="packoptions"></a><span data-ttu-id="bd086-158">packOptions</span><span class="sxs-lookup"><span data-stu-id="bd086-158">packOptions</span></span>

<span data-ttu-id="bd086-159">Viz také [soubory](#files).</span><span class="sxs-lookup"><span data-stu-id="bd086-159">See also [Files](#files).</span></span>

### <a name="common-pack-options"></a><span data-ttu-id="bd086-160">Běžné možnosti pack</span><span class="sxs-lookup"><span data-stu-id="bd086-160">Common pack options</span></span>

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

<span data-ttu-id="bd086-161">Neexistuje žádný ekvivalent pro `owners` element v nástroji MSBuild.</span><span class="sxs-lookup"><span data-stu-id="bd086-161">There is no equivalent for the `owners` element in MSBuild.</span></span>
<span data-ttu-id="bd086-162">Pro `summary`, můžete použít MSBuild `<Description>` vlastnost, i v případě, hodnota `summary` není automaticky migrovat na tuto vlastnost, protože tato vlastnost je namapována na [ `description` ](#-other-common-root-level-options) elementu.</span><span class="sxs-lookup"><span data-stu-id="bd086-162">For `summary`, you can use the MSBuild `<Description>` property, even though the value of `summary` is not migrated automatically to that property, since that property is mapped to the [`description`](#-other-common-root-level-options) element.</span></span>

## <a name="scripts"></a><span data-ttu-id="bd086-163">skripty</span><span class="sxs-lookup"><span data-stu-id="bd086-163">scripts</span></span>

```json
{
  "scripts": {
    "precompile": "generateCode.cmd",
    "postpublish": [ "obfuscate.cmd", "removeTempFiles.cmd" ]
  }
}
```

<span data-ttu-id="bd086-164">Jejich ekvivalenty v MSBuild jsou [cíle](/visualstudio/msbuild/msbuild-targets):</span><span class="sxs-lookup"><span data-stu-id="bd086-164">Their equivalent in MSBuild are [targets](/visualstudio/msbuild/msbuild-targets):</span></span>

```xml
<Target Name="MyPreCompileTarget" BeforeTargets="Build">
  <Exec Command="generateCode.cmd" />
</Target>

<Target Name="MyPostCompileTarget" AfterTargets="Publish">
  <Exec Command="obfuscate.cmd" />
  <Exec Command="removeTempFiles.cmd" />
</Target>
```

## <a name="runtimeoptions"></a><span data-ttu-id="bd086-165">runtimeOptions</span><span class="sxs-lookup"><span data-stu-id="bd086-165">runtimeOptions</span></span>

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

<span data-ttu-id="bd086-166">Všechna nastavení v této skupině, s výjimkou vlastnost "System.GC.Server", se umístí do souboru s názvem *runtimeconfig.template.json* ve složce projektu s možnostmi pro kořenový objekt zrušeno během procesu migrace:</span><span class="sxs-lookup"><span data-stu-id="bd086-166">All settings in this group, except for the "System.GC.Server" property, are placed into a file called *runtimeconfig.template.json* in the project folder, with options lifted to the root object during the migration process:</span></span>

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

<span data-ttu-id="bd086-167">Vlastnost "System.GC.Server" je migrovat do souboru csproj:</span><span class="sxs-lookup"><span data-stu-id="bd086-167">The "System.GC.Server" property is migrated into the csproj file:</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

<span data-ttu-id="bd086-168">Všechny tyto hodnoty však můžete nastavit v souboru csproj, stejně jako vlastnosti MSBuild:</span><span class="sxs-lookup"><span data-stu-id="bd086-168">However, you can set all those values in the csproj as well as MSBuild properties:</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
  <ConcurrentGarbageCollection>true</ConcurrentGarbageCollection>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  <ThreadPoolMaxThreads>25</ThreadPoolMaxThreads>
</PropertyGroup>
```

## <a name="shared"></a><span data-ttu-id="bd086-169">shared</span><span class="sxs-lookup"><span data-stu-id="bd086-169">shared</span></span>

```json
{
  "shared": "shared/**/*.cs"
}
```

<span data-ttu-id="bd086-170">Nepodporuje se v souboru csproj.</span><span class="sxs-lookup"><span data-stu-id="bd086-170">Not supported in csproj.</span></span> <span data-ttu-id="bd086-171">Místo toho musíte vytvořit zahrnout soubory obsahu ve vaší *souboru .nuspec* souboru.</span><span class="sxs-lookup"><span data-stu-id="bd086-171">You must instead create include content files in your *.nuspec* file.</span></span>
<span data-ttu-id="bd086-172">Další informace najdete v tématu [včetně soubory obsahu](/nuget/schema/nuspec#including-content-files).</span><span class="sxs-lookup"><span data-stu-id="bd086-172">For more information, see [Including content files](/nuget/schema/nuspec#including-content-files).</span></span>

## <a name="files"></a><span data-ttu-id="bd086-173">soubory </span><span class="sxs-lookup"><span data-stu-id="bd086-173">files</span></span>

<span data-ttu-id="bd086-174">V *project.json*, sestavení a aktualizací Service pack může rozšířit ke kompilaci a vložení z různých složek.</span><span class="sxs-lookup"><span data-stu-id="bd086-174">In *project.json*, build and pack could be extended to compile and embed from different folders.</span></span>
<span data-ttu-id="bd086-175">V nástroji MSBuild, to se provádí pomocí [položky](/visualstudio/msbuild/common-msbuild-project-items).</span><span class="sxs-lookup"><span data-stu-id="bd086-175">In MSBuild, this is done using [items](/visualstudio/msbuild/common-msbuild-project-items).</span></span> <span data-ttu-id="bd086-176">V následujícím příkladu je běžné převodu:</span><span class="sxs-lookup"><span data-stu-id="bd086-176">The following example is a common conversion:</span></span>

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
> <span data-ttu-id="bd086-177">Mnoho výchozí [vzorů podpory zástupných znaků](https://en.wikipedia.org/wiki/Glob_(programming)) automaticky přidá .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="bd086-177">Many of the default [globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are added automatically by the .NET Core SDK.</span></span>
> <span data-ttu-id="bd086-178">Další informace najdete v tématu [výchozí hodnoty položek kompilaci](https://aka.ms/sdkimplicititems).</span><span class="sxs-lookup"><span data-stu-id="bd086-178">For more information, see [Default Compile Item Values](https://aka.ms/sdkimplicititems).</span></span>

<span data-ttu-id="bd086-179">Všechny nástroje MSBuild `ItemGroup` podporují prvky `Include`, `Exclude`, a `Remove`.</span><span class="sxs-lookup"><span data-stu-id="bd086-179">All MSBuild `ItemGroup` elements support `Include`, `Exclude`, and `Remove`.</span></span>

<span data-ttu-id="bd086-180">Rozložení balíčku uvnitř .nupkg se dají upravovat pomocí `PackagePath="path"`.</span><span class="sxs-lookup"><span data-stu-id="bd086-180">Package layout inside the .nupkg can be modified with `PackagePath="path"`.</span></span>

<span data-ttu-id="bd086-181">S výjimkou `Content`, většina skupin položek vyžadují explicitním přidáním `Pack="true"` mají být zahrnuty do balíčku.</span><span class="sxs-lookup"><span data-stu-id="bd086-181">Except for `Content`, most item groups require explicitly adding `Pack="true"` to be included in the package.</span></span> <span data-ttu-id="bd086-182">`Content` zařadí *obsah* složky v balíčku od MSBuild `<IncludeContentInPack>` je nastavena na `true` ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="bd086-182">`Content` will be put in the *content* folder in a package since the MSBuild `<IncludeContentInPack>` property is set to `true` by default.</span></span>
<span data-ttu-id="bd086-183">Další informace najdete v tématu [včetně obsahu v balíčku](/nuget/schema/msbuild-targets#including-content-in-a-package).</span><span class="sxs-lookup"><span data-stu-id="bd086-183">For more information, see [Including content in a package](/nuget/schema/msbuild-targets#including-content-in-a-package).</span></span>

<span data-ttu-id="bd086-184">`PackagePath="%(Identity)"` představuje krátký způsob nastavení cestu k souboru projektu relativní cesta k balíčku.</span><span class="sxs-lookup"><span data-stu-id="bd086-184">`PackagePath="%(Identity)"` is a short way of setting package path to the project-relative file path.</span></span>

## <a name="testrunner"></a><span data-ttu-id="bd086-185">testRunner</span><span class="sxs-lookup"><span data-stu-id="bd086-185">testRunner</span></span>

### <a name="xunit"></a><span data-ttu-id="bd086-186">xUnit</span><span class="sxs-lookup"><span data-stu-id="bd086-186">xUnit</span></span>

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

### <a name="mstest"></a><span data-ttu-id="bd086-187">MSTest</span><span class="sxs-lookup"><span data-stu-id="bd086-187">MSTest</span></span>

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

## <a name="see-also"></a><span data-ttu-id="bd086-188">Viz také</span><span class="sxs-lookup"><span data-stu-id="bd086-188">See Also</span></span>

* [<span data-ttu-id="bd086-189">Podrobný přehled změn v rozhraní příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="bd086-189">High-level overview of changes in CLI</span></span>](../tools/cli-msbuild-architecture.md)
