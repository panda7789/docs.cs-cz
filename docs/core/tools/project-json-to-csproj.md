---
title: Porovnání project.jsa csproj
description: Podívejte se na mapování mezi project.jsa prvky csproj.
author: natemcmaster
ms.date: 03/13/2017
ms.openlocfilehash: c8638bc30ba09d8e8d464159aded60dcde4b8dc0
ms.sourcegitcommit: 32f0d6f4c01ddc6ca78767c3a30e3305f8cd032c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2020
ms.locfileid: "87427018"
---
# <a name="a-mapping-between-projectjson-and-csproj-properties"></a>Mapování mezi project.jsa vlastnostmi csproj

Od [Tomáš McMaster](https://github.com/natemcmaster)

Během vývoje nástrojů .NET Core byly provedeny důležité změny návrhu, aby již nepodporovaly *project.js* se soubory a místo toho byly projekty .NET Core přesunuty do formátu MSBuild/csproj.

Tento článek ukazuje, jak se v *project.js* ve formátu MSBuild/csproj reprezentují nastavení v, abyste se mohli dozvědět, jak používat nový formát a pochopit změny provedené nástroji pro migraci při upgradu projektu na nejnovější verzi nástrojů.

## <a name="the-csproj-format"></a>Formát csproj

Nový formát, \* . csproj, je formát založený na jazyce XML. Následující příklad ukazuje kořenový uzel projektu .NET Core pomocí `Microsoft.NET.Sdk` . Pro webové projekty je použita sada SDK `Microsoft.NET.Sdk.Web` .

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

Již není podporováno. V hodnotě csproj je určena název souboru projektu, který obvykle odpovídá názvu adresáře. Například, `MyProjectName.csproj`.

Ve výchozím nastavení určuje název souboru projektu také hodnotu `<AssemblyName>` `<PackageId>` vlastností a.

```xml
<PropertyGroup>
  <AssemblyName>MyProjectName</AssemblyName>
  <PackageId>MyProjectName</PackageId>
</PropertyGroup>
```

`<AssemblyName>`Bude mít jinou hodnotu, než `<PackageId>` Když `buildOptions\outputName` byla vlastnost definována v project.js.
Další informace najdete v tématu [Další běžné možnosti sestavení](#other-common-build-options).

### <a name="version"></a>verze

```json
{
  "version": "1.0.0-alpha-*"
}
```

Použijte `VersionPrefix` vlastnosti a `VersionSuffix` :

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

### <a name="other-common-root-level-options"></a>Další běžné možnosti na úrovni root

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

## <a name="frameworks"></a>rozhraní

### <a name="one-target-framework"></a>Jedna cílová architektura

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

### <a name="multiple-target-frameworks"></a>Více cílových rozhraní

```json
{
  "frameworks": {
    "netcoreapp1.0": {},
    "net451": {}
  }
}
```

Pomocí `TargetFrameworks` Vlastnosti definujte seznam cílových rozhraní. K oddělení více hodnot rozhraní použijte středník.

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp1.0;net451</TargetFrameworks>
</PropertyGroup>
```

## <a name="dependencies"></a>závislosti

> [!IMPORTANT]
> Pokud se jedná o **projekt** , nikoli o balíček, formát se liší.
> Další informace najdete v části [typ závislosti](#dependency-type) .

### <a name="netstandardlibrary-metapackage"></a>NETStandard. Library Metapackage

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

### <a name="microsoftnetcoreapp-metapackage"></a>Microsoft. NETCore. app Metapackage

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

`<RuntimeFrameworkVersion>`Hodnota v migrovaném projektu je určena verzí sady SDK, která je nainstalována.

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

### <a name="per-framework-dependencies"></a>Závislosti pro rozhraní

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
> Tím dojde k přerušení způsobu, který `dotnet pack --version-suffix $suffix` Určuje verzi závislosti odkazu na projekt.

#### <a name="type-build"></a>Typ: Build

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

V hodnotě csproj není žádný ekvivalent.

## <a name="runtimes"></a>moduly runtime

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

### <a name="standalone-apps-self-contained-deployment"></a>Samostatné aplikace (samostatně zahrnuté nasazení)

V project.jsna, definování `runtimes` oddílu znamená, že aplikace byla při sestavování a publikování samostatná.
V nástroji MSBuild jsou všechny projekty *přenosné* během sestavení, ale mohou být publikovány jako samostatné.

`dotnet publish --framework netcoreapp1.0 --runtime osx.10.11-x64`

Další informace najdete v tématu [samostatná nasazení (SCD)](../deploying/index.md#publish-self-contained).

## <a name="tools"></a>tools

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
> `imports`v nástrojích csproj nejsou podporovány nástroje. Nástroje, které potřebují importy, nebudou s novým nástrojem fungovat `Microsoft.NET.Sdk` .

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

Pokud `emitEntryPoint` byla `false` , hodnota `OutputType` je převedena na `Library` , což je výchozí hodnota:

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

### <a name="keyfile"></a>keyFile

```json
{
  "buildOptions": {
    "keyFile": "MyKey.snk"
  }
}
```

`keyFile`Element se v nástroji MSBuild rozšíří na tři vlastnosti:

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

### <a name="common-pack-options"></a>Možnosti běžných balíčků

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
  <PackageIcon>ico.png</PackageIcon>
  <PackageProjectUrl>http://numl.net</PackageProjectUrl>
  <PackageLicenseUrl>https://raw.githubusercontent.com/sethjuarez/numl/master/LICENSE.md</PackageLicenseUrl>
  <PackageRequireLicenseAcceptance>false</PackageRequireLicenseAcceptance>
  <RepositoryType>git</RepositoryType>
  <RepositoryUrl>https://raw.githubusercontent.com/sethjuarez/numl</RepositoryUrl>
  <!-- owners is not supported in MSBuild -->
</PropertyGroup>
```

Neexistuje žádný ekvivalent pro `owners` element v MSBuild. Pro `summary` můžete použít `<Description>` vlastnost MSBuild. Hodnota `summary` není migrována automaticky do této vlastnosti, protože tato vlastnost je mapována na [`description`](#other-common-root-level-options) element.  [PackageIconUrl je zastaralé](/nuget/reference/msbuild-targets#packageiconurl) namísto PackageIcon.

## <a name="scripts"></a>skripty

```json
{
  "scripts": {
    "precompile": "generateCode.cmd",
    "postpublish": [ "obfuscate.cmd", "removeTempFiles.cmd" ]
  }
}
```

Jejich ekvivalenty v nástroji MSBuild jsou [cíle](/visualstudio/msbuild/msbuild-targets):

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

Všechna nastavení v této skupině, s výjimkou `System.GC.Server` vlastnosti, jsou umístěna do souboru s názvem *runtimeconfig.template.js* ve složce projektu, s možnostmi, které byly během procesu migrace vyvolány na kořenový objekt:

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

`System.GC.Server`Vlastnost je migrována do souboru csproj:

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

Všechny tyto hodnoty však můžete nastavit v souboru csproj a také ve vlastnostech MSBuild:

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

Ve csproj se nepodporuje. Místo toho v souboru *. nuspec* vytvořte zahrnuté soubory obsahu.
Další informace najdete v tématu [zahrnutí souborů obsahu](/nuget/schema/nuspec#including-content-files).

## <a name="files"></a>files

V *project.jsna*je možné sestavení a sadu rozšířit, aby se daly kompilovat a vkládat z různých složek.
V nástroji MSBuild to je prováděno pomocí [položek](/visualstudio/msbuild/common-msbuild-project-items). Následující příklad je běžným převodem:

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
> Mnohé z výchozích [vzorů nástroje pro expanzi názvů](https://en.wikipedia.org/wiki/Glob_(programming)) jsou automaticky přidány .NET Core SDK. Další informace naleznete v tématu [výchozí kompilace zahrnuje](../project-sdk/overview.md#default-compilation-includes).

Všechny `ItemGroup` prvky MSBuild podporují `Include` , `Exclude` a `Remove` .

Rozložení balíčku uvnitř soubor. nupkg lze upravit pomocí `PackagePath="path"` .

S výjimkou `Content` je většina skupin položek, které jsou součástí balíčku, vyžadovat explicitní přidání `Pack="true"` . `Content`bude umístěn do složky *obsahu* v balíčku, protože `<IncludeContentInPack>` vlastnost MSBuild je ve výchozím nastavení nastavena na hodnotu `true` .
Další informace najdete v tématu [zahrnutí obsahu do balíčku](/nuget/schema/msbuild-targets#including-content-in-a-package).

`PackagePath="%(Identity)"`je krátký způsob, jak nastavit cestu balíčku k relativní cestě k souboru projektu.

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

## <a name="see-also"></a>Viz také:

- [Podrobný přehled změn v rozhraní příkazového řádku](cli-msbuild-architecture.md)
