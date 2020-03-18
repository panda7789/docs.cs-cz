---
title: srovnání project.json a csproj
description: Podívejte se na mapování mezi elementy project.json a csproj.
author: natemcmaster
ms.date: 03/13/2017
ms.openlocfilehash: abe515007b47b415ac33e3350a29edced1784d68
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77451102"
---
# <a name="a-mapping-between-projectjson-and-csproj-properties"></a>Mapování mezi vlastnostmi project.json a csproj

Podle [Nate McMaster](https://github.com/natemcmaster)

Během vývoje nástrojů .NET Core byla provedena důležitá změna návrhu, která již nepodporuje soubory *project.json* a místo toho přesune projekty .NET Core do formátu MSBuild/csproj.

Tento článek ukazuje, jak jsou nastavení v *aplikaci project.json* reprezentována ve formátu MSBuild/csproj, takže se můžete dozvědět, jak používat nový formát a pochopit změny provedené nástroji pro migraci při upgradu projektu na nejnovější verzi nástroje.

## <a name="the-csproj-format"></a>Formát csproj

Nový formát \*.csproj je formát založený na jazyce XML. Následující příklad ukazuje kořenový uzel projektu .NET `Microsoft.NET.Sdk`Core pomocí . Pro webové projekty je `Microsoft.NET.Sdk.Web`použitá sada SDK .

```xml
<Project Sdk="Microsoft.NET.Sdk">
...
</Project>
```

## <a name="common-top-level-properties"></a>Běžné vlastnosti nejvyšší úrovně

### <a name="name"></a>jméno

```json
{
  "name": "MyProjectName"
}
```

Již není podporováno. V csproj je to určeno názvem souboru projektu, který obvykle odpovídá názvu adresáře. Například, `MyProjectName.csproj`.

Ve výchozím nastavení název souboru projektu také `<AssemblyName>` `<PackageId>` určuje hodnotu vlastností a.

```xml
<PropertyGroup>
  <AssemblyName>MyProjectName</AssemblyName>
  <PackageId>MyProjectName</PackageId>
</PropertyGroup>
```

Bude `<AssemblyName>` mít jinou `<PackageId>` hodnotu, než kdyby `buildOptions\outputName` vlastnost byla definována v project.json.
Další informace naleznete v [tématu Další běžné možnosti sestavení](#other-common-build-options).

### <a name="version"></a>version

```json
{
  "version": "1.0.0-alpha-*"
}
```

Použijte `VersionPrefix` vlastnosti a: `VersionSuffix`

```xml
<PropertyGroup>
  <VersionPrefix>1.0.0</VersionPrefix>
  <VersionSuffix>alpha</VersionSuffix>
</PropertyGroup>
```

Můžete také použít `Version` vlastnost, ale to může přepsat nastavení verze během balení:

```xml
<PropertyGroup>
  <Version>1.0.0-alpha</Version>
</PropertyGroup>
```

### <a name="other-common-root-level-options"></a>Další běžné možnosti kořenové úrovně

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

## <a name="frameworks"></a>Rámců

### <a name="one-target-framework"></a>Jeden cílový rámec

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

### <a name="multiple-target-frameworks"></a>Více cílových architektur

```json
{
  "frameworks": {
    "netcoreapp1.0": {},
    "net451": {}
  }
}
```

Pomocí `TargetFrameworks` této vlastnosti můžete definovat seznam cílových architektur. Pomocí středníku oddělte více hodnot architektury.

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp1.0;net451</TargetFrameworks>
</PropertyGroup>
```

## <a name="dependencies"></a>závislosti

> [!IMPORTANT]
> Pokud je závislost **projekt** a nikoli balíček, formát se liší.
> Další informace naleznete v části [typ závislosti.](#dependency-type)

### <a name="netstandardlibrary-metapackage"></a>Metabalíček NETStandard.Library

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

### <a name="microsoftnetcoreapp-metapackage"></a>Metabalíček Microsoft.NETCore.App

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

Všimněte `<RuntimeFrameworkVersion>` si, že hodnota v projektu migrované je určena verzí sady SDK, kterou jste nainstalovali.

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

### <a name="per-framework-dependencies"></a>Závislosti podle rámců

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

### <a name="dependency-type"></a>typ závislosti

#### <a name="type-project"></a>typ: projekt

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
> Tím dojde k `dotnet pack --version-suffix $suffix` přerušení způsobu, jakým určuje verzi závislosti odkazu na projekt.

#### <a name="type-build"></a>typ: sestavení

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

#### <a name="type-platform"></a>typ: platforma

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

Neexistuje žádný ekvivalent v csproj.

## <a name="runtimes"></a>Runtime

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

### <a name="standalone-apps-self-contained-deployment"></a>Samostatné aplikace (samostatné nasazení)

V souboru project.json `runtimes` definování oddílu znamená, že aplikace byla během vytváření a publikování samostatná.
V MSBuild všechny projekty jsou *přenosné* během sestavení, ale mohou být publikovány jako samostatné.

`dotnet publish --framework netcoreapp1.0 --runtime osx.10.11-x64`

Další informace naleznete [v tématu Samostatné nasazení (SCD)](../deploying/index.md#publish-self-contained).

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
> `imports`na nástroje nejsou podporovány v csproj. Nástroje, které potřebují import, nebudou `Microsoft.NET.Sdk`fungovat s novým .

## <a name="buildoptions"></a>buildOptions

Viz také [Soubory](#files).

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

Pokud `emitEntryPoint` `false`byla , `OutputType` hodnota je `Library`převedena na , což je výchozí hodnota:

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

### <a name="keyfile"></a>Keyfile

```json
{
  "buildOptions": {
    "keyFile": "MyKey.snk"
  }
}
```

Prvek `keyFile` se rozbalí na tři vlastnosti v MSBuild:

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

Viz také [Soubory](#files).

### <a name="common-pack-options"></a>Běžné možnosti balení

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

Neexistuje žádný ekvivalent `owners` pro prvek v MSBuild.
Pro `summary`, můžete použít MSBuild `<Description>` vlastnost, i `summary` když hodnota není migrována automaticky do této [`description`](#other-common-root-level-options) vlastnosti, protože tato vlastnost je mapována na prvek.

## <a name="scripts"></a>skripty

```json
{
  "scripts": {
    "precompile": "generateCode.cmd",
    "postpublish": [ "obfuscate.cmd", "removeTempFiles.cmd" ]
  }
}
```

Jejich ekvivalent v MSBuild jsou [cíle](/visualstudio/msbuild/msbuild-targets):

```xml
<Target Name="MyPreCompileTarget" BeforeTargets="Build">
  <Exec Command="generateCode.cmd" />
</Target>

<Target Name="MyPostCompileTarget" AfterTargets="Publish">
  <Exec Command="obfuscate.cmd" />
  <Exec Command="removeTempFiles.cmd" />
</Target>
```

## <a name="runtimeoptions"></a>možnosti běhu

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

Všechna nastavení v této skupině, s výjimkou vlastnosti System.GC.Server, jsou umístěna do souboru nazvaného *runtimeconfig.template.json* ve složce projektu s možnostmi, které jsou během procesu migrace přeneseny na kořenový objekt:

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

Vlastnost "System.GC.Server" je migrována do souboru csproj:

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

Můžete však nastavit všechny tyto hodnoty ve vlastnostech csproj i MSBuild:

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

Není podporováno v csproj. Místo toho je nutné vytvořit soubory obsahu zahrnout do souboru *.nuspec.*
Další informace naleznete [v tématu Including content files](/nuget/schema/nuspec#including-content-files).

## <a name="files"></a>files

V *souboru project.json*lze sestavení a balíček rozšířit tak, aby se zkompilovaly a vkládalo z různých složek.
V MSBuild se to provádí pomocí [položek](/visualstudio/msbuild/common-msbuild-project-items). Následující příklad je běžný převod:

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
> Mnoho výchozích [vzorů globbing](https://en.wikipedia.org/wiki/Glob_(programming)) udávají automaticky sada .NET Core SDK.
> Další informace naleznete [v tématu Default Compile Item Values](https://aka.ms/sdkimplicititems).

Podporují všechny `ItemGroup` prvky `Include` `Exclude`MSBuild , a `Remove`.

Rozložení balíčku uvnitř .nupkg lze `PackagePath="path"`upravit pomocí .

S `Content`výjimkou , většina `Pack="true"` skupin položek vyžadují explicitně přidání, které mají být zahrnuty do balíčku. `Content`bude umístěn ve složce *obsahu* v balíčku, `<IncludeContentInPack>` protože vlastnost `true` MSBuild je ve výchozím nastavení nastavena na.
Další informace naleznete [v tématu Včetně obsahu v balíčku](/nuget/schema/msbuild-targets#including-content-in-a-package).

`PackagePath="%(Identity)"`je krátký způsob nastavení cesty balíčku k cestě k souboru relativnímu k projektu.

## <a name="testrunner"></a>testRunner

### <a name="xunit"></a>xJednotka

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

- [Přehled změn v zastřihovaném zastřihění/](../tools/cli-msbuild-architecture.md)
