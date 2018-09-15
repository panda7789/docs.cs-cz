---
title: porovnání Project.JSON a csproj – .NET Core
description: Zobrazit mapování mezi project.json a csproj prvky.
author: natemcmaster
ms.author: mairaw
ms.date: 03/13/2017
ms.openlocfilehash: 0079164470f87df665be6f9de62bc98d3fb51696
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/15/2018
ms.locfileid: "45647366"
---
# <a name="a-mapping-between-projectjson-and-csproj-properties"></a>Mapování mezi project.json a csproj vlastnosti

Podle [Tomáš McMaster](https://github.com/natemcmaster)

Během vývojové nástroje .NET Core, důležité změny už nebude podporovat *project.json* soubory a místo toho přesuňte projekty .NET Core do formátu nástroje MSBuild/csproj.

Tento článek popisuje, jak nastavení v *project.json* jsou reprezentovány ve formátu MSBuild/csproj, zjistěte, jak používají nový formát a pochopit změny provedené pomocí nástrojů pro migraci, když upgradujete projekt tak, aby nejnovější verzi nástrojů.

## <a name="the-csproj-format"></a>Formát csproj

Nový formát \*.csproj, je ve formátu založený na formátu XML. Následující příklad ukazuje v kořenovém uzlu projektu .NET Core pomocí `Microsoft.NET.Sdk`. Pro webové projekty, sada SDK používá je `Microsoft.NET.Sdk.Web`.

```xml
<Project Sdk="Microsoft.NET.Sdk">
...
</Project>
```

## <a name="common-top-level-properties"></a>Společné vlastnosti nejvyšší úrovně

### <a name="name"></a>name

```json
{
  "name": "MyProjectName"
}
```

Již nejsou podporovány. V souboru csproj se určuje podle názvu souboru projektu, který je definovaný název adresáře. Například `MyProjectName.csproj`.

Ve výchozím souboru projektu také určuje hodnotu `<AssemblyName>` a `<PackageId>` vlastnosti.

```xml
<PropertyGroup>
  <AssemblyName>MyProjectName</AssemblyName>
  <PackageId>MyProjectName</PackageId>
</PropertyGroup>
```

`<AssemblyName>` Bude mít jinou hodnotu než `<PackageId>` Pokud `buildOptions\outputName` vlastnost byla definována v souboru project.json.
Další informace najdete v tématu [další běžné možnosti sestavení](#other-common-build-options).

### <a name="version"></a>verze

```json
{
  "version": "1.0.0-alpha-*"
}
```

Použití `VersionPrefix` a `VersionSuffix` vlastnosti:

```xml
<PropertyGroup>
  <VersionPrefix>1.0.0</VersionPrefix>
  <VersionSuffix>alpha</VersionSuffix>
</PropertyGroup>
```

Můžete také použít `Version` vlastnost, ale můžou přepsat nastavení verzí při vytváření balíčku:

```xml
<PropertyGroup>
  <Version>1.0.0-alpha</Version>
</PropertyGroup>
```

### <a name="other-common-root-level-options"></a>Další běžné možnosti na úrovni kořenového adresáře

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

## <a name="frameworks"></a>Rozhraní

### <a name="one-target-framework"></a>Jednu cílovou architekturu

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

### <a name="multiple-target-frameworks"></a>Více cílových platforem

```json
{
  "frameworks": {
    "netcoreapp1.0": {},
    "net451": {}
  }
}
```

Použití `TargetFrameworks` vlastnost pro definování seznamu cílových platforem. Používejte středníky oddělit více hodnot rozhraní framework.

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp1.0;net451</TargetFrameworks>
</PropertyGroup>
```

## <a name="dependencies"></a>závislosti

> [!IMPORTANT]
> Pokud je závislost **projektu** a nejedná se o balíček, formát se liší.
> Další informace najdete v tématu [typ závislosti](#dependency-type) oddílu.

### <a name="netstandardlibrary-metapackage"></a>NETStandard.Library Microsoft.aspnetcore.all

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

### <a name="microsoftnetcoreapp-metapackage"></a>Balíčky Microsoft.NETCore.App Microsoft.aspnetcore.all

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

Všimněte si, že `<RuntimeFrameworkVersion>` hodnotu v migrovaného projektu určuje verzi sady SDK, které jste nainstalovali.

### <a name="top-level-dependencies"></a>Závislosti nejvyšší úrovně

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

### <a name="per-framework-dependencies"></a>Závislosti na rozhraní

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

### <a name="imports"></a>importy

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

### <a name="dependency-type"></a>Typ závislosti

#### <a name="type-project"></a>Typ: projekt

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
> Tímto přerušíte způsobem, který `dotnet pack --version-suffix $suffix` Určuje verzi závislosti odkazu na projekt.

#### <a name="type-build"></a>Typ: sestavení

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

#### <a name="type-platform"></a>Typ: platforma

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

V souboru csproj neexistuje žádný ekvivalent.

## <a name="runtimes"></a>Moduly runtime

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

### <a name="standalone-apps-self-contained-deployment"></a>Samostatné aplikace (samostatná nasazení)

V souboru project.json definování `runtimes` části znamená, že byla aplikace samostatné během sestavení a publikování.
V nástroji MSBuild, jsou všechny projekty *přenosné* během sestavení, ale mohou být publikovány jako samostatné.

`dotnet publish --framework netcoreapp1.0 --runtime osx.10.11-x64`

Další informace najdete v tématu [samostatná nasazení (SCD)](../deploying/index.md#self-contained-deployments-scd).

## <a name="tools"></a>nástroje

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
> `imports` v nabídce Nástroje, které nejsou podporovány v souboru csproj. Nástroje, které je třeba importy nebude fungovat s novými `Microsoft.NET.Sdk`.

## <a name="buildoptions"></a>buildOptions

Viz také [soubory](#files).

### <a name="emitentrypoint"></a>emitEntryPoint

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

Pokud `emitEntryPoint` byl `false`, hodnota `OutputType` je převedena na `Library`, což je výchozí hodnota:

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

### <a name="keyfile"></a>KeyFile

```json
{
  "buildOptions": {
    "keyFile": "MyKey.snk"
  }
}
```

`keyFile` Rozšíří element třem vlastnostem v nástroji MSBuild:

```xml
<PropertyGroup>
  <AssemblyOriginatorKeyFile>MyKey.snk</AssemblyOriginatorKeyFile>
  <SignAssembly>true</SignAssembly>
  <PublicSign Condition="'$(OS)' != 'Windows_NT'">true</PublicSign>
</PropertyGroup>
```

### <a name="other-common-build-options"></a>Další běžné možnosti sestavení

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

## <a name="packoptions"></a>packOptions

Viz také [soubory](#files).

### <a name="common-pack-options"></a>Běžné možnosti pack

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

Neexistuje žádný ekvivalent pro `owners` element v nástroji MSBuild.
Pro `summary`, můžete použít MSBuild `<Description>` vlastnost, i v případě, hodnota `summary` není automaticky migrovat na tuto vlastnost, protože tato vlastnost je namapována na [ `description` ](#other-common-root-level-options) elementu.

## <a name="scripts"></a>skripty

```json
{
  "scripts": {
    "precompile": "generateCode.cmd",
    "postpublish": [ "obfuscate.cmd", "removeTempFiles.cmd" ]
  }
}
```

Jejich ekvivalenty v MSBuild jsou [cíle](/visualstudio/msbuild/msbuild-targets):

```xml
<Target Name="MyPreCompileTarget" BeforeTargets="Build">
  <Exec Command="generateCode.cmd" />
</Target>

<Target Name="MyPostCompileTarget" AfterTargets="Publish">
  <Exec Command="obfuscate.cmd" />
  <Exec Command="removeTempFiles.cmd" />
</Target>
```

## <a name="runtimeoptions"></a>runtimeOptions

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

Všechna nastavení v této skupině, s výjimkou vlastnost "System.GC.Server", se umístí do souboru s názvem *runtimeconfig.template.json* ve složce projektu s možnostmi pro kořenový objekt zrušeno během procesu migrace:

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

Vlastnost "System.GC.Server" je migrovat do souboru csproj:

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

Všechny tyto hodnoty však můžete nastavit v souboru csproj, stejně jako vlastnosti MSBuild:

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
  <ConcurrentGarbageCollection>true</ConcurrentGarbageCollection>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  <ThreadPoolMaxThreads>25</ThreadPoolMaxThreads>
</PropertyGroup>
```

## <a name="shared"></a>shared

```json
{
  "shared": "shared/**/*.cs"
}
```

Nepodporuje se v souboru csproj. Místo toho musíte vytvořit zahrnout soubory obsahu ve vaší *souboru .nuspec* souboru.
Další informace najdete v tématu [včetně soubory obsahu](/nuget/schema/nuspec#including-content-files).

## <a name="files"></a>soubory 

V *project.json*, sestavení a aktualizací Service pack může rozšířit ke kompilaci a vložení z různých složek.
V nástroji MSBuild, to se provádí pomocí [položky](/visualstudio/msbuild/common-msbuild-project-items). V následujícím příkladu je běžné převodu:

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
> Mnoho výchozí [vzorů podpory zástupných znaků](https://en.wikipedia.org/wiki/Glob_(programming)) automaticky přidá .NET Core SDK.
> Další informace najdete v tématu [výchozí hodnoty položek kompilaci](https://aka.ms/sdkimplicititems).

Všechny nástroje MSBuild `ItemGroup` podporují prvky `Include`, `Exclude`, a `Remove`.

Rozložení balíčku uvnitř .nupkg se dají upravovat pomocí `PackagePath="path"`.

S výjimkou `Content`, většina skupin položek vyžadují explicitním přidáním `Pack="true"` mají být zahrnuty do balíčku. `Content` zařadí *obsah* složky v balíčku od MSBuild `<IncludeContentInPack>` je nastavena na `true` ve výchozím nastavení.
Další informace najdete v tématu [včetně obsahu v balíčku](/nuget/schema/msbuild-targets#including-content-in-a-package).

`PackagePath="%(Identity)"` představuje krátký způsob nastavení cestu k souboru projektu relativní cesta k balíčku.

## <a name="testrunner"></a>testRunner

### <a name="xunit"></a>xUnit

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

### <a name="mstest"></a>MSTest

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

## <a name="see-also"></a>Viz také

* [Podrobný přehled změn v rozhraní příkazového řádku](../tools/cli-msbuild-architecture.md)
