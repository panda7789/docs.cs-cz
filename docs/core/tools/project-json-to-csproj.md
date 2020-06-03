---
title: porovnání Project. JSON a csproj
description: Viz mapování mezi elementy Project. JSON a csproj.
author: natemcmaster
ms.date: 03/13/2017
ms.openlocfilehash: a997b48f645ed58d15610a68aee7c67411f9763f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205835"
---
# <a name="a-mapping-between-projectjson-and-csproj-properties"></a><span data-ttu-id="77947-103">Mapování mezi vlastnostmi Project. JSON a csproj</span><span class="sxs-lookup"><span data-stu-id="77947-103">A mapping between project.json and csproj properties</span></span>

<span data-ttu-id="77947-104">Od [Tomáš McMaster](https://github.com/natemcmaster)</span><span class="sxs-lookup"><span data-stu-id="77947-104">By [Nate McMaster](https://github.com/natemcmaster)</span></span>

<span data-ttu-id="77947-105">Během vývoje nástrojů .NET Core byly provedeny důležité změny návrhu, aby už nepodporovaly soubory *Project. JSON* , a místo toho můžete přesunout projekty .NET Core do formátu MSBuild/csproj.</span><span class="sxs-lookup"><span data-stu-id="77947-105">During the development of the .NET Core tooling, an important design change was made to no longer support *project.json* files and instead move the .NET Core projects to the MSBuild/csproj format.</span></span>

<span data-ttu-id="77947-106">Tento článek ukazuje, jak jsou nastavení v *Project. JSON* zastoupena ve formátu MSBuild/csproj, abyste se mohli naučit používat nový formát a pochopit změny provedené nástroji pro migraci při upgradu projektu na nejnovější verzi nástroje.</span><span class="sxs-lookup"><span data-stu-id="77947-106">This article shows how the settings in *project.json* are represented in the MSBuild/csproj format so you can learn how to use the new format and understand the changes made by the migration tools when you're upgrading your project to the latest version of the tooling.</span></span>

## <a name="the-csproj-format"></a><span data-ttu-id="77947-107">Formát csproj</span><span class="sxs-lookup"><span data-stu-id="77947-107">The csproj format</span></span>

<span data-ttu-id="77947-108">Nový formát, \* . csproj, je formát založený na jazyce XML.</span><span class="sxs-lookup"><span data-stu-id="77947-108">The new format, \*.csproj, is an XML-based format.</span></span> <span data-ttu-id="77947-109">Následující příklad ukazuje kořenový uzel projektu .NET Core pomocí `Microsoft.NET.Sdk` .</span><span class="sxs-lookup"><span data-stu-id="77947-109">The following example shows the root node of a .NET Core project using the `Microsoft.NET.Sdk`.</span></span> <span data-ttu-id="77947-110">Pro webové projekty je použita sada SDK `Microsoft.NET.Sdk.Web` .</span><span class="sxs-lookup"><span data-stu-id="77947-110">For web projects, the SDK used is `Microsoft.NET.Sdk.Web`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
...
</Project>
```

## <a name="common-top-level-properties"></a><span data-ttu-id="77947-111">Společné vlastnosti nejvyšší úrovně</span><span class="sxs-lookup"><span data-stu-id="77947-111">Common top-level properties</span></span>

### <a name="name"></a><span data-ttu-id="77947-112">name</span><span class="sxs-lookup"><span data-stu-id="77947-112">name</span></span>

```json
{
  "name": "MyProjectName"
}
```

<span data-ttu-id="77947-113">Již není podporováno.</span><span class="sxs-lookup"><span data-stu-id="77947-113">No longer supported.</span></span> <span data-ttu-id="77947-114">V hodnotě csproj je určena název souboru projektu, který obvykle odpovídá názvu adresáře.</span><span class="sxs-lookup"><span data-stu-id="77947-114">In csproj, this is determined by the project filename, which usually matches the directory name.</span></span> <span data-ttu-id="77947-115">Například, `MyProjectName.csproj`.</span><span class="sxs-lookup"><span data-stu-id="77947-115">For example, `MyProjectName.csproj`.</span></span>

<span data-ttu-id="77947-116">Ve výchozím nastavení určuje název souboru projektu také hodnotu `<AssemblyName>` `<PackageId>` vlastností a.</span><span class="sxs-lookup"><span data-stu-id="77947-116">By default, the project filename also specifies the value of the `<AssemblyName>` and `<PackageId>` properties.</span></span>

```xml
<PropertyGroup>
  <AssemblyName>MyProjectName</AssemblyName>
  <PackageId>MyProjectName</PackageId>
</PropertyGroup>
```

<span data-ttu-id="77947-117">`<AssemblyName>`Bude mít jinou hodnotu, než `<PackageId>` kdyby `buildOptions\outputName` byla vlastnost definována v Project. JSON.</span><span class="sxs-lookup"><span data-stu-id="77947-117">The `<AssemblyName>` will have a different value than `<PackageId>` if `buildOptions\outputName` property was defined in project.json.</span></span>
<span data-ttu-id="77947-118">Další informace najdete v tématu [Další běžné možnosti sestavení](#other-common-build-options).</span><span class="sxs-lookup"><span data-stu-id="77947-118">For more information, see [Other common build options](#other-common-build-options).</span></span>

### <a name="version"></a><span data-ttu-id="77947-119">verze</span><span class="sxs-lookup"><span data-stu-id="77947-119">version</span></span>

```json
{
  "version": "1.0.0-alpha-*"
}
```

<span data-ttu-id="77947-120">Použijte `VersionPrefix` vlastnosti a `VersionSuffix` :</span><span class="sxs-lookup"><span data-stu-id="77947-120">Use the `VersionPrefix` and `VersionSuffix` properties:</span></span>

```xml
<PropertyGroup>
  <VersionPrefix>1.0.0</VersionPrefix>
  <VersionSuffix>alpha</VersionSuffix>
</PropertyGroup>
```

<span data-ttu-id="77947-121">Můžete také použít `Version` vlastnost, ale to může přepsat nastavení verze během balení:</span><span class="sxs-lookup"><span data-stu-id="77947-121">You can also use the `Version` property, but this may override version settings during packaging:</span></span>

```xml
<PropertyGroup>
  <Version>1.0.0-alpha</Version>
</PropertyGroup>
```

### <a name="other-common-root-level-options"></a><span data-ttu-id="77947-122">Další běžné možnosti na úrovni root</span><span class="sxs-lookup"><span data-stu-id="77947-122">Other common root-level options</span></span>

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

## <a name="frameworks"></a><span data-ttu-id="77947-123">rozhraní</span><span class="sxs-lookup"><span data-stu-id="77947-123">frameworks</span></span>

### <a name="one-target-framework"></a><span data-ttu-id="77947-124">Jedna cílová architektura</span><span class="sxs-lookup"><span data-stu-id="77947-124">One target framework</span></span>

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

### <a name="multiple-target-frameworks"></a><span data-ttu-id="77947-125">Více cílových rozhraní</span><span class="sxs-lookup"><span data-stu-id="77947-125">Multiple target frameworks</span></span>

```json
{
  "frameworks": {
    "netcoreapp1.0": {},
    "net451": {}
  }
}
```

<span data-ttu-id="77947-126">Pomocí `TargetFrameworks` Vlastnosti definujte seznam cílových rozhraní.</span><span class="sxs-lookup"><span data-stu-id="77947-126">Use the `TargetFrameworks` property to define your list of target frameworks.</span></span> <span data-ttu-id="77947-127">K oddělení více hodnot rozhraní použijte středník.</span><span class="sxs-lookup"><span data-stu-id="77947-127">Use semi-colon to separate multiple framework values.</span></span>

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp1.0;net451</TargetFrameworks>
</PropertyGroup>
```

## <a name="dependencies"></a><span data-ttu-id="77947-128">závislosti</span><span class="sxs-lookup"><span data-stu-id="77947-128">dependencies</span></span>

> [!IMPORTANT]
> <span data-ttu-id="77947-129">Pokud se jedná o **projekt** , nikoli o balíček, formát se liší.</span><span class="sxs-lookup"><span data-stu-id="77947-129">If the dependency is a **project** and not a package, the format is different.</span></span>
> <span data-ttu-id="77947-130">Další informace najdete v části [typ závislosti](#dependency-type) .</span><span class="sxs-lookup"><span data-stu-id="77947-130">For more information, see the [dependency type](#dependency-type) section.</span></span>

### <a name="netstandardlibrary-metapackage"></a><span data-ttu-id="77947-131">NETStandard. Library Metapackage</span><span class="sxs-lookup"><span data-stu-id="77947-131">NETStandard.Library metapackage</span></span>

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

### <a name="microsoftnetcoreapp-metapackage"></a><span data-ttu-id="77947-132">Microsoft. NETCore. app Metapackage</span><span class="sxs-lookup"><span data-stu-id="77947-132">Microsoft.NETCore.App metapackage</span></span>

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

<span data-ttu-id="77947-133">`<RuntimeFrameworkVersion>`Hodnota v migrovaném projektu je určena verzí sady SDK, která je nainstalována.</span><span class="sxs-lookup"><span data-stu-id="77947-133">The `<RuntimeFrameworkVersion>` value in the migrated project is determined by the version of SDK that's installed.</span></span>

### <a name="top-level-dependencies"></a><span data-ttu-id="77947-134">Závislosti nejvyšší úrovně</span><span class="sxs-lookup"><span data-stu-id="77947-134">Top-level dependencies</span></span>

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

### <a name="per-framework-dependencies"></a><span data-ttu-id="77947-135">Závislosti pro rozhraní</span><span class="sxs-lookup"><span data-stu-id="77947-135">Per-framework dependencies</span></span>

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

### <a name="imports"></a><span data-ttu-id="77947-136">importy</span><span class="sxs-lookup"><span data-stu-id="77947-136">imports</span></span>

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

### <a name="dependency-type"></a><span data-ttu-id="77947-137">typ závislosti</span><span class="sxs-lookup"><span data-stu-id="77947-137">dependency type</span></span>

#### <a name="type-project"></a><span data-ttu-id="77947-138">Typ: projekt</span><span class="sxs-lookup"><span data-stu-id="77947-138">type: project</span></span>

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
> <span data-ttu-id="77947-139">Tím dojde k přerušení způsobu, který `dotnet pack --version-suffix $suffix` Určuje verzi závislosti odkazu na projekt.</span><span class="sxs-lookup"><span data-stu-id="77947-139">This will break the way that `dotnet pack --version-suffix $suffix` determines the dependency version of a project reference.</span></span>

#### <a name="type-build"></a><span data-ttu-id="77947-140">Typ: Build</span><span class="sxs-lookup"><span data-stu-id="77947-140">type: build</span></span>

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

#### <a name="type-platform"></a><span data-ttu-id="77947-141">Typ: platforma</span><span class="sxs-lookup"><span data-stu-id="77947-141">type: platform</span></span>

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

<span data-ttu-id="77947-142">V hodnotě csproj není žádný ekvivalent.</span><span class="sxs-lookup"><span data-stu-id="77947-142">There is no equivalent in csproj.</span></span>

## <a name="runtimes"></a><span data-ttu-id="77947-143">moduly runtime</span><span class="sxs-lookup"><span data-stu-id="77947-143">runtimes</span></span>

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

### <a name="standalone-apps-self-contained-deployment"></a><span data-ttu-id="77947-144">Samostatné aplikace (samostatně zahrnuté nasazení)</span><span class="sxs-lookup"><span data-stu-id="77947-144">Standalone apps (self-contained deployment)</span></span>

<span data-ttu-id="77947-145">V aplikaci Project. JSON definování `runtimes` oddílu znamená, že aplikace byla při sestavování a publikování samostatná.</span><span class="sxs-lookup"><span data-stu-id="77947-145">In project.json, defining a `runtimes` section means the app was standalone during build and publish.</span></span>
<span data-ttu-id="77947-146">V nástroji MSBuild jsou všechny projekty *přenosné* během sestavení, ale mohou být publikovány jako samostatné.</span><span class="sxs-lookup"><span data-stu-id="77947-146">In MSBuild, all projects are *portable* during build, but can be published as standalone.</span></span>

`dotnet publish --framework netcoreapp1.0 --runtime osx.10.11-x64`

<span data-ttu-id="77947-147">Další informace najdete v tématu [samostatná nasazení (SCD)](../deploying/index.md#publish-self-contained).</span><span class="sxs-lookup"><span data-stu-id="77947-147">For more information, see [Self-contained deployments (SCD)](../deploying/index.md#publish-self-contained).</span></span>

## <a name="tools"></a><span data-ttu-id="77947-148">tools</span><span class="sxs-lookup"><span data-stu-id="77947-148">tools</span></span>

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
> <span data-ttu-id="77947-149">`imports`v nástrojích csproj nejsou podporovány nástroje.</span><span class="sxs-lookup"><span data-stu-id="77947-149">`imports` on tools are not supported in csproj.</span></span> <span data-ttu-id="77947-150">Nástroje, které potřebují importy, nebudou s novým nástrojem fungovat `Microsoft.NET.Sdk` .</span><span class="sxs-lookup"><span data-stu-id="77947-150">Tools that need imports will not work with the new `Microsoft.NET.Sdk`.</span></span>

## <a name="buildoptions"></a><span data-ttu-id="77947-151">buildOptions</span><span class="sxs-lookup"><span data-stu-id="77947-151">buildOptions</span></span>

<span data-ttu-id="77947-152">Viz také [soubory](#files).</span><span class="sxs-lookup"><span data-stu-id="77947-152">See also [Files](#files).</span></span>

### <a name="emitentrypoint"></a><span data-ttu-id="77947-153">emitEntryPoint</span><span class="sxs-lookup"><span data-stu-id="77947-153">emitEntryPoint</span></span>

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

<span data-ttu-id="77947-154">Pokud `emitEntryPoint` byla `false` , hodnota `OutputType` je převedena na `Library` , což je výchozí hodnota:</span><span class="sxs-lookup"><span data-stu-id="77947-154">If `emitEntryPoint` was `false`, the value of `OutputType` is converted to `Library`, which is the default value:</span></span>

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

### <a name="keyfile"></a><span data-ttu-id="77947-155">keyFile</span><span class="sxs-lookup"><span data-stu-id="77947-155">keyFile</span></span>

```json
{
  "buildOptions": {
    "keyFile": "MyKey.snk"
  }
}
```

<span data-ttu-id="77947-156">`keyFile`Element se v nástroji MSBuild rozšíří na tři vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="77947-156">The `keyFile` element expands to three properties in MSBuild:</span></span>

```xml
<PropertyGroup>
  <AssemblyOriginatorKeyFile>MyKey.snk</AssemblyOriginatorKeyFile>
  <SignAssembly>true</SignAssembly>
  <PublicSign Condition="'$(OS)' != 'Windows_NT'">true</PublicSign>
</PropertyGroup>
```

### <a name="other-common-build-options"></a><span data-ttu-id="77947-157">Další běžné možnosti sestavení</span><span class="sxs-lookup"><span data-stu-id="77947-157">Other common build options</span></span>

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

## <a name="packoptions"></a><span data-ttu-id="77947-158">packOptions</span><span class="sxs-lookup"><span data-stu-id="77947-158">packOptions</span></span>

<span data-ttu-id="77947-159">Viz také [soubory](#files).</span><span class="sxs-lookup"><span data-stu-id="77947-159">See also [Files](#files).</span></span>

### <a name="common-pack-options"></a><span data-ttu-id="77947-160">Možnosti běžných balíčků</span><span class="sxs-lookup"><span data-stu-id="77947-160">Common pack options</span></span>

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

<span data-ttu-id="77947-161">Neexistuje žádný ekvivalent pro `owners` element v MSBuild.</span><span class="sxs-lookup"><span data-stu-id="77947-161">There is no equivalent for the `owners` element in MSBuild.</span></span> <span data-ttu-id="77947-162">Pro `summary` můžete použít `<Description>` vlastnost MSBuild.</span><span class="sxs-lookup"><span data-stu-id="77947-162">For `summary`, you can use the MSBuild `<Description>` property.</span></span> <span data-ttu-id="77947-163">Hodnota `summary` není migrována automaticky do této vlastnosti, protože tato vlastnost je mapována na [`description`](#other-common-root-level-options) element.</span><span class="sxs-lookup"><span data-stu-id="77947-163">The value of `summary` is not migrated automatically to that property, since that property is mapped to the [`description`](#other-common-root-level-options) element.</span></span>

## <a name="scripts"></a><span data-ttu-id="77947-164">skripty</span><span class="sxs-lookup"><span data-stu-id="77947-164">scripts</span></span>

```json
{
  "scripts": {
    "precompile": "generateCode.cmd",
    "postpublish": [ "obfuscate.cmd", "removeTempFiles.cmd" ]
  }
}
```

<span data-ttu-id="77947-165">Jejich ekvivalenty v nástroji MSBuild jsou [cíle](/visualstudio/msbuild/msbuild-targets):</span><span class="sxs-lookup"><span data-stu-id="77947-165">Their equivalents in MSBuild are [targets](/visualstudio/msbuild/msbuild-targets):</span></span>

```xml
<Target Name="MyPreCompileTarget" BeforeTargets="Build">
  <Exec Command="generateCode.cmd" />
</Target>

<Target Name="MyPostCompileTarget" AfterTargets="Publish">
  <Exec Command="obfuscate.cmd" />
  <Exec Command="removeTempFiles.cmd" />
</Target>
```

## <a name="runtimeoptions"></a><span data-ttu-id="77947-166">runtimeOptions</span><span class="sxs-lookup"><span data-stu-id="77947-166">runtimeOptions</span></span>

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

<span data-ttu-id="77947-167">Všechna nastavení v této skupině, s výjimkou `System.GC.Server` vlastnosti, jsou umístěna do souboru s názvem *runtimeconfig. template. JSON* ve složce projektu s možnostmi, které byly během procesu migrace vyvolány na kořenový objekt:</span><span class="sxs-lookup"><span data-stu-id="77947-167">All settings in this group, except for the `System.GC.Server` property, are placed into a file called *runtimeconfig.template.json* in the project folder, with options lifted to the root object during the migration process:</span></span>

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

<span data-ttu-id="77947-168">`System.GC.Server`Vlastnost je migrována do souboru csproj:</span><span class="sxs-lookup"><span data-stu-id="77947-168">The `System.GC.Server` property is migrated into the csproj file:</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

<span data-ttu-id="77947-169">Všechny tyto hodnoty však můžete nastavit v souboru csproj a také ve vlastnostech MSBuild:</span><span class="sxs-lookup"><span data-stu-id="77947-169">However, you can set all those values in the csproj as well as MSBuild properties:</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
  <ConcurrentGarbageCollection>true</ConcurrentGarbageCollection>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  <ThreadPoolMaxThreads>25</ThreadPoolMaxThreads>
</PropertyGroup>
```

## <a name="shared"></a><span data-ttu-id="77947-170">shared</span><span class="sxs-lookup"><span data-stu-id="77947-170">shared</span></span>

```json
{
  "shared": "shared/**/*.cs"
}
```

<span data-ttu-id="77947-171">Ve csproj se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="77947-171">Not supported in csproj.</span></span> <span data-ttu-id="77947-172">Místo toho v souboru *. nuspec* vytvořte zahrnuté soubory obsahu.</span><span class="sxs-lookup"><span data-stu-id="77947-172">Instead, create include content files in your *.nuspec* file.</span></span>
<span data-ttu-id="77947-173">Další informace najdete v tématu [zahrnutí souborů obsahu](/nuget/schema/nuspec#including-content-files).</span><span class="sxs-lookup"><span data-stu-id="77947-173">For more information, see [Including content files](/nuget/schema/nuspec#including-content-files).</span></span>

## <a name="files"></a><span data-ttu-id="77947-174">files</span><span class="sxs-lookup"><span data-stu-id="77947-174">files</span></span>

<span data-ttu-id="77947-175">V *aplikaci Project. JSON*bylo možné sestavení a sadu rozšířit, aby se daly kompilovat a vkládat z různých složek.</span><span class="sxs-lookup"><span data-stu-id="77947-175">In *project.json*, build and pack could be extended to compile and embed from different folders.</span></span>
<span data-ttu-id="77947-176">V nástroji MSBuild to je prováděno pomocí [položek](/visualstudio/msbuild/common-msbuild-project-items).</span><span class="sxs-lookup"><span data-stu-id="77947-176">In MSBuild, this is done using [items](/visualstudio/msbuild/common-msbuild-project-items).</span></span> <span data-ttu-id="77947-177">Následující příklad je běžným převodem:</span><span class="sxs-lookup"><span data-stu-id="77947-177">The following example is a common conversion:</span></span>

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
> <span data-ttu-id="77947-178">Mnohé z výchozích [vzorů nástroje pro expanzi názvů](https://en.wikipedia.org/wiki/Glob_(programming)) jsou automaticky přidány .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="77947-178">Many of the default [globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are added automatically by the .NET Core SDK.</span></span> <span data-ttu-id="77947-179">Další informace naleznete v tématu [výchozí kompilace zahrnuje](../project-sdk/overview.md#default-compilation-includes).</span><span class="sxs-lookup"><span data-stu-id="77947-179">For more information, see [Default compilation includes](../project-sdk/overview.md#default-compilation-includes).</span></span>

<span data-ttu-id="77947-180">Všechny `ItemGroup` prvky MSBuild podporují `Include` , `Exclude` a `Remove` .</span><span class="sxs-lookup"><span data-stu-id="77947-180">All MSBuild `ItemGroup` elements support `Include`, `Exclude`, and `Remove`.</span></span>

<span data-ttu-id="77947-181">Rozložení balíčku uvnitř soubor. nupkg lze upravit pomocí `PackagePath="path"` .</span><span class="sxs-lookup"><span data-stu-id="77947-181">Package layout inside the .nupkg can be modified with `PackagePath="path"`.</span></span>

<span data-ttu-id="77947-182">S výjimkou `Content` je většina skupin položek, které jsou součástí balíčku, vyžadovat explicitní přidání `Pack="true"` .</span><span class="sxs-lookup"><span data-stu-id="77947-182">Except for `Content`, most item groups require explicitly adding `Pack="true"` to be included in the package.</span></span> <span data-ttu-id="77947-183">`Content`bude umístěn do složky *obsahu* v balíčku, protože `<IncludeContentInPack>` vlastnost MSBuild je ve výchozím nastavení nastavena na hodnotu `true` .</span><span class="sxs-lookup"><span data-stu-id="77947-183">`Content` will be put in the *content* folder in a package since the MSBuild `<IncludeContentInPack>` property is set to `true` by default.</span></span>
<span data-ttu-id="77947-184">Další informace najdete v tématu [zahrnutí obsahu do balíčku](/nuget/schema/msbuild-targets#including-content-in-a-package).</span><span class="sxs-lookup"><span data-stu-id="77947-184">For more information, see [Including content in a package](/nuget/schema/msbuild-targets#including-content-in-a-package).</span></span>

<span data-ttu-id="77947-185">`PackagePath="%(Identity)"`je krátký způsob, jak nastavit cestu balíčku k relativní cestě k souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="77947-185">`PackagePath="%(Identity)"` is a short way of setting package path to the project-relative file path.</span></span>

## <a name="testrunner"></a><span data-ttu-id="77947-186">testRunner</span><span class="sxs-lookup"><span data-stu-id="77947-186">testRunner</span></span>

### <a name="xunit"></a><span data-ttu-id="77947-187">xUnit</span><span class="sxs-lookup"><span data-stu-id="77947-187">xUnit</span></span>

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

### <a name="mstest"></a><span data-ttu-id="77947-188">MSTest</span><span class="sxs-lookup"><span data-stu-id="77947-188">MSTest</span></span>

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

## <a name="see-also"></a><span data-ttu-id="77947-189">Viz také</span><span class="sxs-lookup"><span data-stu-id="77947-189">See also</span></span>

- [<span data-ttu-id="77947-190">Podrobný přehled změn v rozhraní příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="77947-190">High-level overview of changes in CLI</span></span>](cli-msbuild-architecture.md)
