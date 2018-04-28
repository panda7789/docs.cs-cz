---
title: porovnání Project.JSON a csproj - .NET Core
description: V tématu mapování mezi elementy project.json a csproj.
author: natemcmaster
ms.author: mairaw
ms.date: 03/13/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: c5753d73f062aa107d7afbec6146ea3452901fb1
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="a-mapping-between-projectjson-and-csproj-properties"></a>Mapování mezi project.json a csproj vlastnosti

Podle [McMaster Jan](https://github.com/natemcmaster)

Během vývoje nástrojů .NET Core, návrhu důležité změně již nepodporují *project.json* soubory a místo toho přesunout do formátu nástroje MSBuild/csproj projekty .NET Core.

Tento článek ukazuje, jak nastavení v *project.json* jsou reprezentované ve formátu MSBuild/csproj, takže můžete naučit používat nový formát a pochopit změny provedené pomocí nástrojů pro migraci, když provádíte upgrade projektu pro nejnovější verzi nástrojů. 
 
## <a name="the-csproj-format"></a>Formát csproj

Nový formát \*.csproj, je ve formátu formátu XML. Následující příklad ukazuje na kořenový uzel .NET Core projekt pomocí `Microsoft.NET.Sdk`. Pro webové projekty, je sada SDK používá `Microsoft.NET.Sdk.Web`.

```xml
<Project Sdk="Microsoft.NET.Sdk">
...
</Project>
```

## <a name="common-top-level-properties"></a>Běžné vlastnosti nejvyšší úrovně

### <a name="name"></a>name
```json
{
  "name": "MyProjectName"
}
```

Již není podporována. V csproj ten je daný název souboru projektu, který je definovaný název adresáře. Například `MyProjectName.csproj`.

Ve výchozím nastavení, určuje název souboru projektu také hodnotu `<AssemblyName>` a `<PackageId>` vlastnosti. 

```xml
<PropertyGroup>
  <AssemblyName>MyProjectName</AssemblyName>
  <PackageId>MyProjectName</PackageId>
</PropertyGroup>
```

`<AssemblyName>` Bude mít jinou hodnotu než `<PackageId>` Pokud `buildOptions\outputName` vlastnost byla definována v souboru project.json. Další informace najdete v tématu [další běžné možnosti sestavení](#other-common-build-options).

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

Můžete také `Version` vlastnost, ale může přepsat nastavení verze během balení:

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

## <a name="frameworks"></a>rozhraní

### <a name="one-target-framework"></a>Jeden cíl framework
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

### <a name="multiple-target-frameworks"></a>Více cílové rozhraní

```json
{
  "frameworks": {
    "netcoreapp1.0": {},
    "net451": {}
  }
}
```

Použití `TargetFrameworks` vlastnost můžete definovat seznam cílové architektury. K oddělení více hodnot framework použijte oddělte středníkem. 

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp1.0;net451</TargetFrameworks>
</PropertyGroup>
```

## <a name="dependencies"></a>závislosti

> [!IMPORTANT]
> Pokud je závislost **projektu** a nejedná se o balíček, formát se liší. Další informace najdete v tématu [typ závislosti](#dependency-type) části.

### <a name="netstandardlibrary-metapackage"></a>NETStandard.Library metapackage

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

### <a name="microsoftnetcoreapp-metapackage"></a>Microsoft.NETCore.App metapackage

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

Všimněte si, že `<RuntimeFrameworkVersion>` hodnota v migrovaných projektu je dáno verzi sady SDK, které jste nainstalovali.

### <a name="top-level-dependencies"></a>Nejvyšší úrovně závislosti
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

### <a name="per-framework-dependencies"></a>Závislosti za architektury
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

#### <a name="type-project"></a>Typ: projektu
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
> Tím by došlo k přerušení způsob který `dotnet pack --version-suffix $suffix` Určuje verzi závislostí odkaz na projekt.


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

V csproj není žádný ekvivalent. 

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
V souboru project.json definování `runtimes` části znamená byla aplikace samostatné během sestavení a publikování.
V nástroji MSBuild, jsou všechny projekty *přenosné* během vytváření sestavení, ale mohou být uvedeny jako samostatné.

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
> `imports` nástroje, nejsou podporovány v csproj. Nástroje, které je třeba importy nebude fungovat s novým `Microsoft.NET.Sdk`.

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

Pokud `emitEntryPoint` byla `false`, hodnota `OutputType` jsou převedeny na `Library`, což je výchozí hodnota:

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

`keyFile` Element zasahuje do tří vlastnosti v nástroji MSBuild:

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

Není k dispozici žádný ekvivalent `owners` element v nástroji MSBuild. Pro `summary`, můžete použít MSBuild `<Description>` vlastnost, i když hodnota `summary` není automaticky migrovat na tuto vlastnost, protože tuto vlastnost je namapována na [ `description` ](#-other-common-root-level-options) element.

## <a name="scripts"></a>skripty

```json
{
  "scripts": {
    "precompile": "generateCode.cmd",
    "postpublish": [ "obfuscate.cmd", "removeTempFiles.cmd" ]
  }
}
```

Jsou jejich ekvivalent v nástroji MSBuild [cíle](/visualstudio/msbuild/msbuild-targets):

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

Všechna nastavení v této skupině s výjimkou vlastnost "System.GC.Server" se umístí do souboru s názvem *runtimeconfig.template.json* ve složce projektu s možnostmi nahoru, aby se kořenový objekt během procesu migrace:

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

Vlastnost "System.GC.Server" je do souboru csproj migrovat:
```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

V csproj a také vlastnosti nástroje MSBuild však můžete nastavit tyto hodnoty:
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

Nepodporované ve csproj. Místo toho musíte vytvořit zahrnout soubory obsahu v vaše *příponou .nuspec* souboru. Další informace najdete v tématu [včetně soubory obsahu](/nuget/schema/nuspec#including-content-files).

## <a name="files"></a>soubory 

V *project.json*, sestavení a aktualizací Service pack může rozšířit na zkompilování a vložit z jiné složky.
V nástroji MSBuild, to se provádí pomocí [položky](/visualstudio/msbuild/common-msbuild-project-items). V následujícím příkladu je běžné převod:

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
> Mnoho výchozí [expanze názvů vzory](https://en.wikipedia.org/wiki/Glob_(programming)) automaticky přidá .NET Core SDK.
> Další informace najdete v tématu [výchozí hodnoty položky zkompilovat](https://aka.ms/sdkimplicititems).

Všechny nástroje MSBuild `ItemGroup` podporují elementy `Include`, `Exclude`, a `Remove`.

Můžete změnit rozložení balíček uvnitř .nupkg `PackagePath="path"`.

S výjimkou `Content`, většina skupiny položek vyžadují explicitně přidání `Pack="true"` mají být zahrnuty v balíčku. `Content` budou umístěny do *obsah* složky v balíčku od MSBuild `<IncludeContentInPack>` je nastavena na `true` ve výchozím nastavení. Další informace najdete v tématu [včetně obsahu v balíčku](/nuget/schema/msbuild-targets#including-content-in-a-package).

`PackagePath="%(Identity)"` je krátký způsob nastavení na cestu k souboru projektu relativní cestu k balíčku.

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

[Souhrnné informace o změnách v rozhraní příkazového řádku](../tools/cli-msbuild-architecture.md)
