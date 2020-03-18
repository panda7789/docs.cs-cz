---
title: Přehled sady SDK základního projektu .NET
description: Další informace o sadách SDK projektu .NET Core.
ms.date: 02/02/2020
ms.topic: conceptual
ms.openlocfilehash: 32e14993326c6f17d6470249fe5a545180348631
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399173"
---
# <a name="net-core-project-sdks"></a>Sady SDK core aplikace .NET

.NET Core projekty jsou spojeny s sadou pro vývoj softwaru (SDK). Každý projekt SDK je sada [cílů](/visualstudio/msbuild/msbuild-targets) MSBuild a přidružené [úkoly,](/visualstudio/msbuild/msbuild-tasks) které jsou zodpovědné za kompilaci, balení a publikování kódu.

## <a name="available-sdks"></a>Dostupné sady SDK

Pro službu .NET Core jsou k dispozici následující sady SDK:

| ID | Popis | Repo|
| - | - | - |
| `Microsoft.NET.Sdk` | Sada SDK jádra .NET | https://github.com/dotnet/sdk |
| `Microsoft.NET.Sdk.Web` | Sada .NET Core [Web SDK](/aspnet/core/razor-pages/web-sdk) | https://github.com/aspnet/websdk |
| `Microsoft.NET.Sdk.Razor` | Sada [SDK .NET](/aspnet/core/razor-pages/sdk) Core Razor |
| `Microsoft.NET.Sdk.Worker` | Sada SDK základní pracovní služby .NET |
| `Microsoft.NET.Sdk.WindowsDesktop` | Základní winforms rozhraní .NET a sada WPF SDK |

Sada .NET Core SDK je základní sadou SDK pro jádro .NET Core. Ostatní sady SDK odkazují na sadu .NET Core SDK a projekty, které jsou přidruženy k ostatním sadám SDK, mají všechny vlastnosti sady .NET Core SDK, které jsou k dispozici. Web SDK, například závisí na .NET Core SDK a Razor SDK.

Můžete také vytvářet vlastní sdk, které mohou být distribuovány prostřednictvím NuGet.

## <a name="project-files"></a>Soubory projektu

Základní projekty .NET jsou založeny na formátu [MSBuild.](/visualstudio/msbuild/msbuild) Soubory projektu, které mají rozšíření jako *.csproj* pro projekty C# a *.fsproj* pro projekty F#, jsou ve formátu XML. Kořenový prvek souboru projektu MSBuild je prvek [Project.](/visualstudio/msbuild/project-element-msbuild) Prvek `Project` má volitelný `Sdk` atribut, který určuje, který SDK (a verze) použít. Chcete-li použít nástroje .NET Core a `Sdk` vytvořit kód, nastavte atribut na jedno z ID v tabulce [Dostupné sady SDK.](#available-sdks)

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

Chcete-li zadat sadu SDK, která pochází z NuGet, zadejte verzi na konci názvu nebo zadejte název a verzi v souboru *global.json.*

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

Dalším způsobem, jak určit sdk je s nejvyšší úrovně [Sdk](/visualstudio/msbuild/sdk-element-msbuild) prvek:

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

Odkazování na sdk jedním z těchto způsobů výrazně zjednodušuje soubory projektu pro .NET Core. Při vyhodnocování projektu MSBuild `Sdk.props` přidá implicitní importy `Sdk.targets` v horní části souboru projektu a v dolní části.

```xml
<Project>
  <!-- Implicit top import -->
  <Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />
  ...
  <!-- Implicit bottom import -->
  <Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />
</Project>
```

> [!TIP]
> V počítači se systémem Windows lze soubory *Sdk.props* a *Sdk.targets* nalézt ve složce *%ProgramFiles%\dotnet\sdk\\[verze]\Sdks\Microsoft.NET.Sdk\Sdk.*

### <a name="preprocess-the-project-file"></a>Předběžné zpracování souboru projektu

Můžete vidět plně rozšířený projekt jako MSBuild vidí po SDK a jeho `dotnet msbuild -preprocess` cíle jsou zahrnuty pomocí příkazu. [Předprocesový](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) přepínač [`dotnet msbuild`](../tools/dotnet-msbuild.md) příkazu zobrazuje, které soubory jsou importovány, jejich zdroje a jejich příspěvky k sestavení, aniž by skutečně stavěly projekt.

Pokud projekt má více cílových architektur, zaměřte výsledky příkazu pouze na jeden rámec zadáním jako vlastnost MSBuild. Například:

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a>Výchozí kompilace zahrnuje

Výchozí zahrnuje a vylučuje pro kompilaci položky a vložené prostředky jsou definovány v sadě SDK. Na rozdíl od projektů, které nejsou sdk.net framework, není nutné zadat tyto položky v souboru projektu, protože výchozí pokrytí většiny běžných případů použití. To vede k menším souborům projektu, které jsou srozumitelnější a v případě potřeby ručně upravovány.

V následující tabulce je uvedeno, který prvek a které globs jsou [zahrnuty](https://en.wikipedia.org/wiki/Glob_(programming)) a vyloučeny do sady .NET Core SDK:

| Element           | Zahrnout glob                              | Vyloučit glob                                                  | Odstranit glob              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| Kompilaci           | \*\*/\*.cs (nebo jiná jazyková rozšíření) | \*\*/\*.user;  \*\*/\*. \*proj;  \* \* /.sln; \*  \* \* / \*.vssscc  | Není dostupné.                      |
| Vložený prostředek  | \*\*/\*.resx                              | \*\*/\*.user; \*\*/\*. \*proj; \* \* /.sln; \* \* \* / \*.vssscc     | Není dostupné.                      |
| Žádný              | \*\*/\*                                   | \*\*/\*.user; \*\*/\*. \*proj; \* \* /.sln; \* \* \* / \*.vssscc     | \*\*/\*.cs; \* \* /.resx \* |

> [!NOTE]
> A `./bin` `./obj` složky, které jsou `$(BaseOutputPath)` `$(BaseIntermediateOutputPath)` reprezentovány vlastnostmi a MSBuild, jsou ve výchozím nastavení vyloučeny z globs. Nezahrnuje jsou reprezentovány `$(DefaultItemExcludes)`vlastností .

Pokud explicitně definujete tyto položky v souboru projektu, pravděpodobně se zobrazí následující chyba:

**Byly zahrnuty duplicitní položky kompilace. Sada .NET SDK ve výchozím nastavení obsahuje položky kompilace z adresáře projektu. Tyto položky můžete odebrat ze souboru projektu nebo nastavit vlastnost EnableDefaultCompileItems na hodnotu false, pokud je chcete explicitně zahrnout do souboru projektu.**

Chcete-li chybu vyřešit, `Compile` odeberte explicitní položky, které odpovídají implicitním položkám uvedeným v předchozí tabulce, nebo nastavte `EnableDefaultCompileItems` vlastnost na `false`, která zakáže implicitní zahrnutí:

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

Pokud chcete zadat, například některé soubory, které mají být publikovány s vaší aplikací, můžete stále použít `Content` známé mechanismy MSBuild pro tento prvek.

`EnableDefaultCompileItems`pouze zakáže `Compile` globs, ale nemá vliv na `None` jiné globs, \*jako implicitní glob, který se vztahuje i na .cs položky. Z tohoto důvodu Průzkumník řešení \*v sadě Visual Studio zobrazuje položky .cs jako součást projektu, zahrnuté jako `None` položky. Chcete-li `None` implicitní `EnableDefaultNoneItems` glob `false`zakázat, nastavte na :

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

Chcete-li zakázat *všechny* `EnableDefaultItems` implicitní `false`globs, nastavte vlastnost na :

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="customize-the-build"></a>Přizpůsobení sestavení

Existují různé způsoby [přizpůsobení sestavení](/visualstudio/msbuild/customize-your-build). Vlastnost můžete přepsat předáním jako argument příkazu [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) nebo [dotnet.](../tools/index.md) Vlastnost můžete také přidat do souboru projektu nebo do souboru *Directory.Build.props.* Seznam užitečných vlastností pro projekty .NET Core naleznete v [tématu Vlastnosti msbuild pro projekty sady .NET Core SDK](msbuild-props.md).

### <a name="custom-targets"></a>Vlastní cíle

.NET Core projekty můžete balíček vlastní MSBuild cíle a vlastnosti pro použití projekty, které spotřebovávají balíček. Tento typ rozšiřitelnosti použijte, pokud chcete:

- Rozšiřte proces sestavení.
- Přístup artefakty procesu sestavení, jako jsou generované soubory.
- Zkontrolujte konfiguraci, pod kterou je vyvoláno sestavení.

Vlastní cíle sestavení nebo vlastnosti přidáte `<package_id>.targets` umístěním souborů do formuláře nebo `<package_id>.props` `Contoso.Utility.UsefulStuff.targets`(například) do složky *sestavení* projektu.

Následující kód XML je výstřižek ze souboru *.csproj,* který příkaz udává, [`dotnet pack`](../tools/dotnet-pack.md) co má sbalit. Prvek `<ItemGroup Label="dotnet pack instructions">` umístí soubory cílů do složky *sestavení* uvnitř balíčku. Prvek `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` umístí sestavení a *soubory JSON* do složky *sestavení.*

```xml
<Project Sdk="Microsoft.NET.Sdk">

  ...
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
  ...
  
</Project>
```

Chcete-li spotřebovat vlastní cíl `PackageReference` v projektu, přidejte prvek, který odkazuje na balíček a jeho verzi. Na rozdíl od nástrojů je balíček vlastních cílů součástí uzavření závislosti náročného projektu.

Můžete nakonfigurovat, jak používat vlastní cíl. Vzhledem k tomu, že je cíl MSBuild, může záviset na daný cíl, spustit `dotnet msbuild -t:<target-name>` za jiným cílem nebo ručně vyvolat pomocí příkazu. Chcete-li však poskytnout lepší uživatelské prostředí, můžete kombinovat nástroje pro jednotlivé projekty a vlastní cíle. V tomto scénáři nástroj pro jednotlivé projekty přijímá všechny parametry, [`dotnet msbuild`](../tools/dotnet-msbuild.md) které jsou potřeba, a překládá, že do požadované vyvolání, který provede cíl. Ukázku tohoto druhu synergie si můžete prohlédnout na [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) příkladech vzorků [Hackathon summitu MVP summitu 2016](https://github.com/dotnet/MVPSummitHackathon2016) v projektu.

## <a name="see-also"></a>Viz také

- [Instalace .NET Core](../install/index.md)
- [Použití sad SDK projektu MSBuild](/visualstudio/msbuild/how-to-use-project-sdk)
- [Balíček vlastních cílů msbuild a rekvizit y nuget](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package)
