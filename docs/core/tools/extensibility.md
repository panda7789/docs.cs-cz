---
title: Model rozšiřitelnosti .NET core rozhraní příkazového řádku
description: Zjistěte, jak můžete rozšířit nástroje rozhraní příkazového řádku (CLI).
author: blackdwarf
ms.author: mairaw
ms.date: 04/12/2017
ms.openlocfilehash: 6cabd3959a29878788916ae26589be408c12e0ca
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2018
---
# <a name="net-core-cli-tools-extensibility-model"></a>Model rozšiřitelnosti nástrojů .NET core rozhraní příkazového řádku

Tento dokument popisuje různé způsoby můžete rozšířit nástroje .NET Core rozhraní příkazového řádku (CLI) a popisují scénáře, které jednotka každém z nich.
Uvidíte, jak používat nástroje a také jak vytvářet různé typy nástroje.

## <a name="how-to-extend-cli-tools"></a>Postup rozšíření nástrojů příkazového řádku
Nástroje příkazového řádku lze rozšířit třemi hlavními způsoby:

1. [Pomocí balíčků NuGet při jednotlivých projektů](#per-project-based-extensibility)

   Nástroje pro projekt jsou obsažené v kontextu projektu, ale umožňují snadno instalace prostřednictvím obnovení.

2. [Pomocí balíčků NuGet s vlastní cíle](#custom-targets)

   Vlastní cíle umožňují snadno rozšířit procesu sestavení vlastní úlohy.

3. [Prostřednictvím systémové cesty](#path-based-extensibility)

   Na základě cesty nástroje jsou vhodné pro obecné, mezi projekty nástroje, které lze použít na jednom počítači.

Tři rozšiřitelnost mechanismy uvedených výše se nevylučují. Můžete použít jednu, nebo všechny, nebo jejich kombinaci. Které z nich vybrat závislá převážně na cíl, který se pokoušíte dosáhnout s rozšíření.

## <a name="per-project-based-extensibility"></a>Rozšiřitelnost na základě za projektů
Projekt nástroje jsou [nasazení závislé na framework](../deploying/index.md#framework-dependent-deployments-fdd) , distribuované jako balíčky NuGet. Nástroje jsou dostupné jenom v kontextu projektu, který odkazuje na jejich a pro které jsou obnoveny. Volání mimo kontext projektu (například mimo adresář, který obsahuje projekt) se nezdaří, protože příkaz nebyl nalezen.

Tyto nástroje jsou ideální pro servery sestavení, protože nic mimo souboru projektu. Spustí proces sestavení obnovit pro projekt sestavení a nástroje bude k dispozici. Jazyk projektech, jako jsou F # jsou také v této kategorii, vzhledem k tomu, že každý projekt lze zapsat pouze v jedné konkrétní jazyk.

Tento model rozšiřitelnosti navíc poskytuje podporu pro vytvoření nástrojů, které potřebují přístup k integrovaný výstup projektu. Pro instanci nástroje pro v různých zobrazení syntaxe Razor [ASP.NET](https://www.asp.net/) do této kategorie patří aplikace MVC.

### <a name="consuming-per-project-tools"></a>Použití nástroje pro projekt
Využívání těchto nástrojů vyžaduje můžete přidat `<DotNetCliToolReference>` element se v souboru projektu pro jednotlivé nástroje, které chcete použít. Uvnitř `<DotNetCliToolReference>` elementu odkazují na balíček, ve které tento nástroj se nachází a zadejte verzi budete potřebovat. Po spuštění [ `dotnet restore` ](dotnet-restore.md), nástroje a jeho závislosti jsou obnoveny.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Nástroje, které je potřeba načíst výstup sestavení projektu pro spuštění je obvykle jiné závislost, která je uvedena pod regulární závislosti v souboru projektu. Vzhledem k tomu, že rozhraní příkazového řádku používá MSBuild jako jeho modul sestavení, doporučujeme, aby tyto části nástroje pro zapsání jako vlastní MSBuild [cíle](/visualstudio/msbuild/msbuild-targets) a [úlohy](/visualstudio/msbuild/msbuild-tasks), protože se pak může trvat část v celkovém procesu sestavení. Také můžete získat všech dat snadno vytvořený prostřednictvím sestavení, jako je například umístění výstupní soubory aktuální konfiguraci sestavuje atd. Všechny tyto informace k sadu vlastnosti nástroje MSBuild, které lze číst z žádné cíle. Uvidíte, jak přidat vlastní cíl pomocí nástroje NuGet později v tomto dokumentu.

Pojďme si příklad jednoduchého nástroje jen nástroje pro přidání na jednoduchý projekt. Zadaný příkaz příklad názvem `dotnet-api-search` , které umožňuje hledat prostřednictvím balíčky NuGet pro rozhraní API zadaná, zde je souboru projektu konzolové aplikace, který používá tohoto nástroje:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
  </PropertyGroup>

  <!-- The tools reference -->
  <ItemGroup>
    <DotNetCliToolReference Include="dotnet-api-search" Version="1.0.0" />
  </ItemGroup>
</Project>
```

`<DotNetCliToolReference>` Element strukturovaná podobně jako `<PackageReference>` elementu. Musí být schopni obnovit ID balíčku balíčku, který obsahuje nástroje a její verzi.

### <a name="building-tools"></a>Nástroje pro sestavení
Jak je uvedeno, nástroje jsou právě přenosné konzolové aplikace. Nástroje sestavení, jako by sestavení jiných konzolové aplikace.
Když ho vytvoříte, můžete použít [ `dotnet pack` ](dotnet-pack.md) příkaz k vytvoření balíčku NuGet (souboru .nupkg), který obsahuje kód, informace o jeho závislé součásti a tak dále. Můžete přiřadit libovolný název balíčku, ale aplikace uvnitř nástroj Skutečná binární, má tak, aby odpovídala konvence `dotnet-<command>` v pořadí pro `dotnet` být schopni ji použít.

> [!NOTE]
> V RC3 předběžné verze nástroje příkazového řádku .NET Core `dotnet pack` příkaz měl chyb, která způsobila, že `runtime.config.json` nesmí být zabalena pomocí nástroje. Postrádá tohoto souboru za následek chyby za běhu. Pokud narazíte na toto chování, nezapomeňte aktualizovat na nejnovější nástroje a potom `dotnet pack` znovu.

Vzhledem k tomu, že jsou nástroje přenosné aplikace, musí mít uživatel využívají nástroj verzi knihovny .NET Core, které nástroj byl sestaven proti, aby bylo možné spustit nástroj. Žádné další závislosti, používá nástroj a že není zahrnutá do knihovny .NET Core je obnovena a uložena v mezipaměti NuGet. Nástroj pro celý se proto spustit pomocí sestavení z knihoven .NET Core a také sestavení z mezipaměti NuGet.

Tyto druhy nástroje mít graf závislostí, který je zcela oddělenou z grafu závislostí projektu, který používá. Proces obnovení nejprve obnoví závislosti projektu a potom obnoví všechny nástroje a jejich závislosti.

Můžete najít bohatší příklady a různé kombinace to [úložišti .NET Core rozhraní příkazového řádku](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestProjects).
Můžete také zjistit [implementace nástroje používané](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestPackages) ve stejném úložišti.

### <a name="custom-targets"></a>Vlastní cíle
NuGet má schopnost [balíček vlastní MSBuild cíle a soubory props](/nuget/create-packages/creating-a-package#including-msbuild-props-and-targets-in-a-package). S přechodem .NET Core rozhraní příkazového řádku nástroje pro použití nástroje MSBuild shodný mechanismus rozšiřitelnosti teď vztahují na projekty .NET Core. Tento typ rozšíření by použijte, pokud chcete rozšířit procesu sestavení nebo pokud chcete získat přístup k žádnému artefaktů v procesu sestavení, jako jsou například generované soubory, nebo chcete prohlédnout konfiguraci, pod kterým je volána sestavení , atd.

V následujícím příkladu se zobrazí cílové složky projektu soubor pomocí `csproj` syntaxe. Tím se nastaví [ `dotnet pack` ](dotnet-pack.md) příkaz co do balíčku, umístění souborů cíle, jakož i sestavení do *sestavení* složky uvnitř balíčku. Upozornění `<ItemGroup>` element, který má `Label` vlastnost nastavena na hodnotu `dotnet pack instructions`, a cíl definován pod ní.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <Description>Sample Packer</Description>
    <VersionPrefix>0.1.0-preview</VersionPrefix>
    <TargetFramework>netstandard1.3</TargetFramework>
    <DebugType>portable</DebugType>
    <AssemblyName>SampleTargets.PackerTarget</AssemblyName>
  </PropertyGroup>
  <ItemGroup>
    <EmbeddedResource Include="Resources\Pkg\dist-template.xml;compiler\resources\**\*" Exclude="bin\**;obj\**;**\*.xproj;packages\**" />
    <None Include="build\SampleTargets.PackerTarget.targets" />
  </ItemGroup>
  <ItemGroup Label="dotnet pack instructions">
    <Content Include="build\*.targets">
      <Pack>true</Pack>
      <PackagePath>build\</PackagePath>
    </Content>
  </ItemGroup>
  <Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">
    <!-- Collect these items inside a target that runs after build but before packaging. -->
    <ItemGroup>
      <Content Include="$(OutputPath)\*.dll;$(OutputPath)\*.json">
        <Pack>true</Pack>
        <PackagePath>build\</PackagePath>
      </Content>
    </ItemGroup>
  </Target>
  <ItemGroup>
    <PackageReference Include="Microsoft.Extensions.DependencyModel" Version="1.0.1-beta-000933"/>
    <PackageReference Include="Microsoft.Build.Framework" Version="0.1.0-preview-00028-160627" />
    <PackageReference Include="Microsoft.Build.Utilities.Core" Version="0.1.0-preview-00028-160627" />
    <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
  </ItemGroup>
  <ItemGroup />
  <PropertyGroup Label="Globals">
    <ProjectGuid>463c66f0-921d-4d34-8bde-7c9d0bffaf7b</ProjectGuid>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(TargetFramework)' == 'netstandard1.3' ">
    <DefineConstants>$(DefineConstants);NETSTANDARD1_3</DefineConstants>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">
    <DefineConstants>$(DefineConstants);RELEASE</DefineConstants>
  </PropertyGroup>
</Project>
```

Použití vlastní cíle se provádí zadáním `<PackageReference>` který odkazuje na balíček a jeho verze uvnitř projekt, který je právě rozšířeno. Na rozdíl od nástroje získat balíček vlastní cíle zahrnut do uzavření závislostí náročné projektu.

Pomocí vlastních cíl závisí výhradně na tom, jak nakonfigurovat. Vzhledem k tomu, že je cíl MSBuild, může záviset na daný cíl, spusťte po jiný cíl a můžete také být vyvolána ručně pomocí `dotnet msbuild /t:<target-name>` příkaz.

Ale pokud chcete zajistit lepší prostředí pro uživatele, můžete kombinovat za projektu nástroje a vlastní cíle. V tomto scénáři nástroj projekt by v podstatě právě přijmout ať parametry nejsou potřebné a který se promítne do požadované [ `dotnet msbuild` ](dotnet-msbuild.md) volání, které by provést cíl. Uvidíte ukázku tento druh součinnosti na [ukázky MVP schůzce na nejvyšší úrovni 2016 Hackathon](https://github.com/dotnet/MVPSummitHackathon2016) v úložišti [ `dotnet-packer` ](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) projektu.

### <a name="path-based-extensibility"></a>Na základě CESTU rozšíření
Na základě cesty rozšíření se obvykle používá pro vývoj počítače kde je nutné nástroj, který koncepčně obsahuje více než jeden projekt. Hlavní nevýhodou tento mechanismus rozšíření je, že jsou spojeny počítač kde nástroj existuje. Pokud budete potřebovat na jiném počítači, museli byste ji nasadit.

Tento vzor rozšiřitelnost rozhraní příkazového řádku sady nástrojů je velmi jednoduchý. Jak je popsané v [.NET Core rozhraní příkazového řádku přehled](index.md), `dotnet` ovladač lze spustit všechny příkaz s názvem po `dotnet-<command>` konvence. Výchozí logiku řešení nejprve sondy několika umístění a nakonec se vrátí do systému CESTU. Pokud požadovaný příkaz v systému cesta existuje a je binární soubor, který lze vyvolat, `dotnet` ovladač vyvolá.

Soubor musí být spustitelný soubor. V systémech Unix, to všechno, co má nastaven bit spustit prostřednictvím znamená `chmod +x`. V systému Windows, můžete použít *cmd* soubory.

Podívejme se na velmi jednoduché provedení nástroj "Hello World". Budeme používat obě `bash` a `cmd` v systému Windows.
Následující příkaz se ke konzole echo jednoduše "Hello World".

```bash
#!/bin/bash

echo "Hello World!"
```

```cmd
echo "Hello World"
```

V systému macOS, můžeme uložit tento skript jako `dotnet-hello` a nastavit jeho spustitelné bitové s `chmod +x dotnet-hello`. Pak můžeme vytvořit symbolický odkaz k němu v `/usr/local/bin` pomocí příkazu `ln -s <full_path>/dotnet-hello /usr/local/bin/`. To bude možné volat pomocí příkazu `dotnet hello` syntaxe.

V systému Windows, můžeme uložit tento skript jako `dotnet-hello.cmd` a umístí jej do umístění, které je v cestě systému (nebo jim ho přidat ke složce, která je již v cestě). Poté můžete jednoduše použít `dotnet hello` pro spuštění tohoto příkladu.
