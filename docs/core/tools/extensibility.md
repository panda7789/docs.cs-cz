---
title: Model rozšíření rozhraní příkazového řádku .NET core
description: Zjistěte, jak můžete rozšířit nástroje rozhraní příkazového řádku (CLI).
author: blackdwarf
ms.author: mairaw
ms.date: 04/12/2017
ms.openlocfilehash: a9cfebbeddbedc329432c805c5956b382a726a77
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45592059"
---
# <a name="net-core-cli-tools-extensibility-model"></a>Model rozšiřitelnosti nástrojů rozhraní příkazového řádku .NET core

Tento dokument popisuje různé způsoby, můžete rozšířit nástroje .NET Core rozhraní příkazového řádku (CLI) a popisují scénáře, které řídí každém z nich.
Uvidíte jak používat nástroje, jakož i jak vytvářet různé typy nástrojů.

## <a name="how-to-extend-cli-tools"></a>Rozšíření nástrojů rozhraní příkazového řádku
Nástroje rozhraní příkazového řádku je možné rozšířit třemi hlavními způsoby:

1. [Prostřednictvím balíčků NuGet na základě jednotlivých projektů](#per-project-based-extensibility)

   Nástroje na projektu jsou obsaženy v kontextu projektu, ale umožňují snadnou instalaci prostřednictvím obnovení.

2. [Prostřednictvím balíčků NuGet s vlastní cíle](#custom-targets)

   Vlastní cíle vám umožní snadno rozšířit proces sestavení pomocí vlastní úlohy.

3. [Prostřednictvím systémové cesty](#path-based-extensibility)

   Na základě cest nástroje jsou vhodné pro napříč projekty, obecné nástroje, které lze použít na jednom počítači.

Tyto tři mechanismy rozšíření uvedených výše se nevylučují. Můžete použít jednu nebo všechny, nebo jejich kombinaci. Který se má vybrat závisí do značné míry na cíl, který se snažíte dosáhnout pomocí rozšíření.

## <a name="per-project-based-extensibility"></a>Rozšíření na základě jednotlivých projektů
Nástroje na projekt jsou [nasazení závisí na architektuře](../deploying/index.md#framework-dependent-deployments-fdd) , která se distribuují jako balíčky NuGet. Nástroje jsou dostupné jenom v kontextu projektu, který na ně odkazuje, a u kterého se obnoví. Volání mimo kontext projektu (například nachází mimo adresář, který obsahuje projekt) se nezdaří, protože příkaz nebyl nalezen.

Tyto nástroje jsou ideální pro sestavovací servery, protože je potřeba nic mimo rámec souborů projektu. Spuštění procesu sestavení pro projekt ji obnovit sestavení a nástroje budou dostupné. Projekty jazyka, jako je například F #, jsou také v této kategorii, protože každý projekt lze zapsat pouze v jeden konkrétní jazyk.

Nakonec tento model rozšiřitelnosti poskytuje podporu pro vytváření nástrojů, které potřebují přístup k sestavení výstupu projektu. Například různých zobrazení Razor nástroje v [ASP.NET](https://www.asp.net/) do této kategorie patří aplikace MVC.

### <a name="consuming-per-project-tools"></a>Využívání projektů nástroje
Využívání těchto nástrojů je potřeba přidat `<DotNetCliToolReference>` element do souboru projektu pro každý nástroj, který chcete použít. Uvnitř `<DotNetCliToolReference>` elementu, odkazujte na balíček, ve kterém se nástroj nachází a určit verzi budete potřebovat. Po spuštění [ `dotnet restore` ](dotnet-restore.md), budou obnoveny nástroj a jeho závislosti.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Pro nástroje, které je potřeba načíst výstupu sestavení projektu pro spuštění je obvykle další závislosti, která je uvedena pod regulární závislosti v souboru projektu. Jelikož rozhraní příkazového řádku používá jako jeho modul sestavení MSBuild, doporučujeme vám, že tyto části nástroje pro zapsání jako vlastní MSBuild [cíle](/visualstudio/msbuild/msbuild-targets) a [úlohy](/visualstudio/msbuild/msbuild-tasks), protože se pak můžou část v celkovém procesu sestavení. Navíc můžete získat všechny data snadno, který je vytvořen pomocí sestavení, jako je například umístění výstupních souborů, aktuální konfigurace sestavována atd. Tyto informace se změní sadu vlastnosti nástroje MSBuild, které může číst z žádné cíle. Můžete zjistit, jak přidat vlastní cíl pomocí nástroje NuGet dále v tomto dokumentu.

Pojďme se podívat na příklad Přidání jednoduchého nástroje jenom nástroje na jednoduchý projekt. Zadaný příkaz příklad volá `dotnet-api-search` , který umožňuje prohledávat balíčky NuGet pro zadané rozhraní API, tady je soubor projektu konzolové aplikace, který používá nástroje:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>

  <!-- The tools reference -->
  <ItemGroup>
    <DotNetCliToolReference Include="dotnet-api-search" Version="1.0.0" />
  </ItemGroup>
</Project>
```

`<DotNetCliToolReference>` Element strukturovaná podobně jako `<PackageReference>` elementu. Musí být schopni obnovit ID balíčku nástroje balíček, který obsahuje nástroje a její verzi.

### <a name="building-tools"></a>Nástroje pro sestavování
Jak už bylo zmíněno, nástroje jsou pouze přenosných konzolové aplikace. Nástroje sestavení, jako by sestavení jakékoli jiné aplikace konzoly.
Po sestavení, můžete použít [ `dotnet pack` ](dotnet-pack.md) příkaz, který vytvoří balíček NuGet (.nupkg soubor), která obsahuje váš kód, informace o jeho závislosti a tak dále. Můžete přiřadit libovolný název balíčku, ale aplikace, nástroj Skutečná binární, musí odpovídat konvenci `dotnet-<command>` mohl `dotnet` být schopni ho vyvolat.

> [!NOTE]
> V RC3 předběžné verze nástroje příkazového řádku .NET Core `dotnet pack` měl příkaz, který způsobil chybu `runtime.config.json` nesmí být zabalena nástrojem. Chybí tento soubor výsledků chyby za běhu. Pokud narazíte na toto chování, nezapomeňte aktualizovat na nejnovější nástroje a zkuste to `dotnet pack` znovu.

Vzhledem k tomu, že jsou nástroje přenosné aplikace, musí mít uživatele, nástroj verze knihovny .NET Core, které nástroj byla vytvořena Chcete-li spustit nástroj. Všechny další závislosti, využívá nástroj a, která není zahrnutá do knihovny .NET Core není obnoví a je umístěn v mezipaměti NuGet. Celý nástroj, proto se spouští pomocí sestavení z knihoven .NET Core a sestavení z mezipaměti NuGet.

Tyto druhy nástroje mají graf závislostí, který je zcela oddělená od grafu závislostí projektu, který je využívá. Proces obnovení nejprve obnoví závislosti projektu a poté obnoví všechny nástroje a jejich závislosti.

Najdete podrobnější příklady a to v různých kombinacích [úložiště .NET Core CLI](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestProjects).
Můžete zobrazit také [implementace nástroje používané](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestPackages) ve stejném úložišti.

### <a name="custom-targets"></a>Vlastní cíle
NuGet má schopnost [balíček vlastní MSBuild cíle a soubory vlastností](/nuget/create-packages/creating-a-package#including-msbuild-props-and-targets-in-a-package). S přechodem na nástroje rozhraní příkazového řádku .NET Core pro použití nástroje MSBuild stejný mechanismus rozšiřitelnosti teď platí pro projekty .NET Core. Tento typ rozšíření byste použili, když chcete rozšíření procesu sestavení, nebo když chcete získat přístup k žádnému artefaktů v procesu sestavení, jako je například generované soubory, nebo chcete provést kontrolu konfigurace, pod kterým je vyvolán sestavení , atd.

V následujícím příkladu vidíte cílový projekt pomocí souborů `csproj` syntaxe. Tím se nastaví [ `dotnet pack` ](dotnet-pack.md) příkaz co do balíčku, uvedení soubory cíle a také sestavení do *sestavení* složky uvnitř balíčku. Všimněte si, že `<ItemGroup>` element, který má `Label` nastavenou na `dotnet pack instructions`, a cíl definovaný pod ním.

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

Použití vlastní cíle se uvede `<PackageReference>` , která odkazuje na balíček a jeho verzi v projektu, který se rozšiřuje. Na rozdíl od nástroje získat balíček vlastní cíle zahrnut do uzavření závislostí projektu náročné.

Použití vlastní cíle závisí výhradně na tom, jak nakonfigurovat. Protože je cíl nástroje MSBuild, může záviset na daném cíli, spustit po jiném cíli a je také možné ručně vyvolat pomocí `dotnet msbuild /t:<target-name>` příkazu.

Nicméně pokud chcete poskytovat lepší výkon pro vaše uživatele, můžete kombinovat jednotlivých projektů nástroje a vlastní cíle. V tomto scénáři nástroj jednotlivých projektů by v podstatě stačí přijmout cokoli, co potřebné parametry a, která převedla do požadované [ `dotnet msbuild` ](dotnet-msbuild.md) volání, které by se spustit cíl. Můžete zobrazit ukázku, tento druh synergii na [MVP Summit 2016 Hackathon ukázky](https://github.com/dotnet/MVPSummitHackathon2016) úložiště v [ `dotnet-packer` ](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) projektu.

### <a name="path-based-extensibility"></a>Na základě cest rozšiřitelnosti
Na základě cest rozšíření se obvykle používá pro vývoj počítače tam, kde potřebujete nástroj, který koncepčně zahrnuje více než jeden projekt. Tento mechanismus rozšíření Hlavní nevýhodou je, že je spojený s počítači tam, kde existuje nástroj. Pokud je nutné ji na jiném počítači, je třeba ho nasadit.

Tento model rozšiřitelnosti nástrojů rozhraní příkazového řádku je velmi snadné. Jak je popsáno v [přehled rozhraní příkazového řádku .NET Core](index.md), `dotnet` ovladač lze spustit jakýkoli příkaz, který má stejný název `dotnet-<command>` konvence. Výchozí logika řešení nejprve sondy několika míst a nakonec spadne zpět na CESTU systému. Pokud požadovaný příkaz, existuje v systémové CESTĚ a je binární soubor, který může být vyvolána, `dotnet` ovladač vyvolá.

Soubor musí být spustitelný soubor. V systémech Unix, to znamená cokoliv, co má nastavený bit provést prostřednictvím `chmod +x`. Na Windows, můžete použít *cmd* soubory.

Pojďme se podívat na velmi jednoduchá implementace nástroje "Hello World". Použijeme obě `bash` a `cmd` na Windows.
Následující příkaz se ke konzole echo jednoduše "Hello World".

```bash
#!/bin/bash

echo "Hello World!"
```

```cmd
echo "Hello World"
```

V systému macOS, uložíme tento skript jako `dotnet-hello` a nastavte jeho spustitelné bitové s `chmod +x dotnet-hello`. Pak vytvoříme symbolický odkaz k tomu `/usr/local/bin` pomocí příkazu `ln -s <full_path>/dotnet-hello /usr/local/bin/`. To znamená, že je to možné, který má být vyvolán pomocí příkazu `dotnet hello` syntaxe.

Na Windows, uložíme tento skript jako `dotnet-hello.cmd` a vložit ho do umístění, které je v systémové cestě (nebo ji můžete přidat do složky, která je již v cestě). Potom můžete použít jenom `dotnet hello` spuštění tohoto příkladu.
