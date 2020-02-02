---
title: Model rozšiřitelnosti .NET Core CLI
description: Přečtěte si, jak můžete .NET Core CLI rozšiřuje.
ms.date: 04/12/2017
ms.openlocfilehash: 74da895fb3a3f6c77640a2b9a64acdb2894a954b
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920518"
---
# <a name="net-core-cli-extensibility-model"></a>Model rozšiřitelnosti .NET Core CLI

Tento článek popisuje různé způsoby, jak .NET Core CLI můžete roztáhnout a vysvětlit scénáře, které jednotlivé jednotky na nich zabírají.
Uvidíte, jak tyto nástroje používat a jak vytvořit různé typy nástrojů.

## <a name="how-to-extend-the-cli"></a>Postup rozšiřování rozhraní příkazového řádku
Rozhraní příkazového řádku lze rozšířit třemi hlavními způsoby:

1. [Přes balíčky NuGet na jednotlivých projektech](#per-project-based-extensibility)

   Nástroje pro projekty jsou obsaženy v kontextu projektu, ale umožňují snadnou instalaci prostřednictvím obnovení.

2. [Přes balíčky NuGet s vlastními cíli](#custom-targets)

   Vlastní cíle vám umožňují snadno roztáhnout proces sestavení s vlastními úkoly.

3. [Přes cestu systému](#path-based-extensibility)

   Nástroje založené na cestách jsou vhodné pro obecné nástroje pro více projektů, které jsou použitelné na jednom počítači.

Tři výše popsané mechanismy rozšíření nejsou exkluzivní. Můžete použít jeden nebo všechny nebo jejich kombinaci. Který z jednoho výběru závisí hlavně na cíli, který se snažíte dosáhnout s vaším rozšířením.

## <a name="per-project-based-extensibility"></a>Rozšiřitelnost na základě projektu
Nástroje pro jednotlivé projekty jsou [nasazení závislá na rozhraní](../deploying/index.md#framework-dependent-deployments-fdd) , která jsou distribuována jako balíčky NuGet. Nástroje jsou k dispozici pouze v kontextu projektu, který je odkazuje na ně a pro které jsou obnoveny. Volání mimo kontext projektu (například mimo adresář, který obsahuje projekt) selže, protože příkaz nelze nalézt.

Tyto nástroje jsou ideální pro servery sestavení, protože není potřeba nic mimo soubor projektu. Proces sestavení spustí obnovení pro sestavení projektu, které bude k dispozici. Jazykové projekty, například F#, jsou také v této kategorii, protože každý projekt lze zapsat pouze do jednoho konkrétního jazyka.

Nakonec tento model rozšiřitelnosti poskytuje podporu pro vytváření nástrojů, které potřebují přístup k sestavenému výstupu projektu. Do této kategorie patří například různé nástroje pro zobrazení Razor v aplikacích [ASP.NET](https://www.asp.net/) MVC.

### <a name="consuming-per-project-tools"></a>Zpracování nástrojů pro jednotlivé projekty
Spotřeba těchto nástrojů vyžaduje, abyste přidali `<DotNetCliToolReference>` element do souboru projektu pro každý nástroj, který chcete použít. Uvnitř elementu `<DotNetCliToolReference>` odkazujete na balíček, ve kterém se nástroj nachází, a zadejte požadovanou verzi. Po spuštění [`dotnet restore`](dotnet-restore.md)se nástroj a jeho závislosti obnoví.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Pro nástroje, které potřebují načíst výstup sestavení projektu ke spuštění, je obvykle jiná závislost, která je uvedena v rámci normální závislosti v souboru projektu. Vzhledem k tomu, že rozhraní příkazového řádku používá jako modul sestavení MSBuild, doporučujeme, aby tyto části nástroje byly zapsány jako vlastní [cíle](/visualstudio/msbuild/msbuild-targets) a [úkoly](/visualstudio/msbuild/msbuild-tasks)MSBuild, protože mohou být součástí celého procesu sestavení. Také mohou získat jakákoli a všechna data, která jsou vytvářena prostřednictvím sestavení, například umístění výstupních souborů, aktuální konfigurace, která je vytvořena a tak dále. Všechny tyto informace se stávají sadou vlastností nástroje MSBuild, které lze číst z libovolného cíle. Můžete vidět, jak přidat vlastní cíl pomocí NuGetu dále v tomto dokumentu.

Pojďme se podívat na příklad přidání jednoduchého nástroje pouze pro nástroje do jednoduchého projektu. V případě ukázkového příkazu s názvem `dotnet-api-search`, který umožňuje vyhledat balíčky NuGet pro zadané rozhraní API, je zde soubor projektu aplikace konzoly, který používá tento nástroj:

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

Element `<DotNetCliToolReference>` je strukturován podobným způsobem jako `<PackageReference>` prvek. Potřebuje ID balíčku balíčku, který obsahuje nástroj a jeho verzi, aby se mohl obnovit.

### <a name="building-tools"></a>Vytváření nástrojů
Jak už bylo zmíněno, nástroje jsou jenom přenosné konzolové aplikace. Nástroje sestavíte stejně, jako byste vytvořili jinou konzolovou aplikaci.
Po sestavení můžete pomocí příkazu [`dotnet pack`](dotnet-pack.md) vytvořit balíček NuGet (soubor. nupkg), který obsahuje váš kód, informace o jeho závislostech atd. Do balíčku můžete dát libovolný název, ale aplikace uvnitř, skutečný binární soubor nástroje, musí odpovídat konvenci `dotnet-<command>`, aby `dotnet` mohl vyvolat.

> [!NOTE]
> V RC3 verzích nástrojů příkazového řádku .NET Core měla příkaz `dotnet pack` chybu, která způsobila, že *runtimeconfig. JSON* není zabalený pomocí nástroje. Při nedostatku tohoto souboru dojde k chybám za běhu. Pokud narazíte na toto chování, nezapomeňte aktualizovat na nejnovější nástroje a zkuste `dotnet pack` znovu.

Vzhledem k tomu, že nástroje jsou přenosné aplikace, uživatel, který nástroj spotřebovává, musí mít verzi knihoven .NET Core, pro kterou byl nástroj vytvořen, aby mohl nástroj spustit. Všechny ostatní závislosti, které nástroj používá a které nejsou obsaženy v knihovnách .NET Core, se obnoví a umístí do mezipaměti NuGet. Celý nástroj je proto spouštěn pomocí sestavení z knihoven .NET Core i sestavení z mezipaměti NuGet.

Tyto druhy nástrojů mají graf závislosti, který je zcela oddělený od grafu závislostí projektu, který je používá. Proces obnovení nejprve obnoví závislosti projektu a pak obnoví všechny nástroje a jejich závislosti.

V [úložišti .NET Core CLI](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestProjects)můžete najít bohatší příklady a různé kombinace.
Můžete také zobrazit [implementaci nástrojů používaných](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestPackages) ve stejném úložišti.

## <a name="custom-targets"></a>Vlastní cíle

Balíčky NuGet mají možnost [zabalit vlastní cíle a soubory props nástroje MSBuild](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package). Když přesunete .NET Core pro použití nástroje MSBuild, stejný mechanismus rozšíření teď platí pro projekty .NET Core. Tento typ rozšiřitelnosti byste měli použít, pokud chcete rozšíření procesu sestavení, nebo když chcete získat přístup k jakémukoli artefaktům v procesu sestavení, jako jsou například generované soubory nebo chcete zkontrolovat konfiguraci, pod kterou je vyvoláno sestavení. a tak dále.

V následujícím příkladu se můžete podívat na soubor projektu cíle pomocí syntaxe `csproj`. Tím se dá pokyn [`dotnet pack`](dotnet-pack.md) příkazu, který se má zabalit, umístit soubory cílů i sestavení do složky *sestavení* uvnitř balíčku. Všimněte si `<ItemGroup>` elementu, který má vlastnost `Label` nastavenou na `dotnet pack instructions`a cíl definovaný pod ním.

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

Používání vlastních cílů se provádí poskytnutím `<PackageReference>`, které odkazuje na balíček a jeho verzi v projektu, který se rozšiřuje. Na rozdíl od nástrojů balíček vlastní cíle zahrnuje do uzavření závislosti projektu.

Použití vlastního cíle závisí výhradně na tom, jak ho nakonfigurujete. Vzhledem k tomu, že se jedná o cíl nástroje MSBuild, může záviset na daném cíli, běžet po jiném cíli a lze jej také ručně vyvolat pomocí příkazu `dotnet msbuild -t:<target-name>`.

Pokud však chcete uživatelům poskytnout lepší uživatelské prostředí, můžete kombinovat nástroje pro jednotlivé projekty a vlastní cíle. V tomto scénáři by nástroj na projekt v podstatě přijal libovolné potřebné parametry a převedl to na požadované [`dotnet msbuild`](dotnet-msbuild.md) vyvolání, které by způsobilo provedení cíle. Ukázku tohoto druhu součinnosti si můžete prohlédnout na úložišti [ukázek MVP 2016 Hackathon](https://github.com/dotnet/MVPSummitHackathon2016) v projektu [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) .

## <a name="path-based-extensibility"></a>Rozšiřitelnost na základě cesty
Rozšíření na základě cesty se obvykle používá ve vývojových počítačích, kde potřebujete nástroj, který koncepčně pokrývá více než jeden projekt. Hlavní nevýhodou tohoto mechanismu rozšíření je to, že je vázaný na počítač, na kterém nástroj existuje. Pokud ho potřebujete na jiném počítači, budete ho muset nasadit.

Tento model rozšiřitelnosti sady nástrojů rozhraní příkazového řádku je velmi jednoduchý. Jak je popsáno v [přehledu .NET Core CLI](index.md), `dotnet` ovladač může spustit jakýkoli příkaz, který se jmenuje po `dotnet-<command>` konvenci. Výchozí logika rozlišení nejprve vyhledá několik umístění a nakonec se vrátí k systémové cestě. Pokud v systémové cestě existuje požadovaný příkaz a je to binární soubor, který lze vyvolat, `dotnet` ovladač ho vyvolá.

Soubor musí být spustitelný. V systémech UNIX to znamená cokoli, co má nastaven bit spouštění prostřednictvím `chmod +x`. Ve Windows můžete použít soubory *cmd* .

Pojďme se podívat na velmi jednoduchou implementaci nástroje "Hello World". Ve Windows budeme používat jak `bash`, tak `cmd`.
Následující příkaz jednoduše vrátí "Hello World" do konzoly.

```bash
#!/bin/bash

echo "Hello World!"
```

```cmd
echo "Hello World"
```

V macOS můžete tento skript Uložit jako `dotnet-hello` a nastavit jeho spustitelný bit pomocí `chmod +x dotnet-hello`. V `/usr/local/bin` pak můžeme vytvořit symbolický odkaz pomocí příkazového `ln -s <full_path>/dotnet-hello /usr/local/bin/`. Díky tomu bude možné vyvolat příkaz pomocí syntaxe `dotnet hello`.

Ve Windows můžeme tento skript Uložit jako `dotnet-hello.cmd` a umístit ho do umístění, které je v systémové cestě (nebo ho můžete přidat do složky, která je už v cestě). Za tímto účelem můžete spustit tento příklad jenom pomocí `dotnet hello`.
