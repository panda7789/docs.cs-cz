---
title: příkaz dotnet Pack
description: Příkaz dotnet Pack vytvoří balíčky NuGet pro projekt .NET Core.
ms.date: 08/08/2019
ms.openlocfilehash: 057d1029e5c933912c43c178b6db8a8498f2ed57
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734122"
---
# <a name="dotnet-pack"></a>dotnet pack

**Tento článek se týká:** ✔️ .NET Core 1. x SDK a novějších verzí

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Název

`dotnet pack` – zabalí kód do balíčku NuGet.

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet pack [<PROJECT>|<SOLUTION>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--interactive]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo] [-o|--output] [--runtime] [-s|--serviceable]
    [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

## <a name="description"></a>Popis

Příkaz `dotnet pack` vytvoří projekt a vytvoří balíčky NuGet. Výsledek tohoto příkazu je balíček NuGet (to znamená soubor *. nupkg* ).

Pokud chcete vygenerovat balíček, který obsahuje symboly ladění, máte k dispozici dvě možnosti:

- `--include-symbols` – vytvoří balíček symbolů.
- `--include-source` – vytvoří balíček symbolů se složkou `src` uvnitř obsahující zdrojové soubory.

Do souboru *. nuspec* jsou přidány závislosti NuGet zkomprimovaného projektu, aby byly po instalaci balíčku správně vyřešeny. Odkazy z projektu na projekt nejsou zabaleny do projektu. V současné době je nutné mít balíček na projekt, pokud máte závislosti typu projekt-projekt.

Ve výchozím nastavení `dotnet pack` sestavit projekt jako první. Pokud se chcete tomuto chování vyhnout, předejte možnost `--no-build`. Tato možnost je často užitečná ve scénářích průběžné integrace (CI), kde víte, že kód byl dříve sestaven.

Vlastnosti nástroje MSBuild můžete zadat pro příkaz `dotnet pack` pro proces balení. Další informace najdete v tématu [vlastnosti metadat NuGet](csproj.md#nuget-metadata-properties) a [Reference k příkazovému řádku MSBuild](/visualstudio/msbuild/msbuild-command-line-reference). V části s [Příklady](#examples) se dozvíte, jak použít přepínač MSBuild-p pro několik různých scénářů.

Webové projekty nejsou ve výchozím nastavení nabaleny. Chcete-li přepsat výchozí chování, přidejte do souboru *. csproj* následující vlastnost:

```xml
<PropertyGroup>
   <IsPackable>true</IsPackable>
</PropertyGroup>
```

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a>Argumenty

`PROJECT | SOLUTION`

  Projekt nebo řešení, které se má zabalit Jedná se buď o cestu k [souboru csproj](csproj.md), k souboru řešení nebo k adresáři. Pokud není zadán, příkaz vyhledá v aktuálním adresáři soubor projektu nebo řešení.

## <a name="options"></a>Možnosti

- **`-c|--configuration {Debug|Release}`**

  Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`.

- **`--force`**

  Vynutí vyřešení všech závislostí i v případě, že bylo poslední obnovení úspěšné. Zadání tohoto příznaku je stejné jako odstranění souboru *Project. assets. JSON* . Možnost je k dispozici od verze .NET Core 2,0 SDK.

- **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

- **`--include-source`**

  Obsahuje kromě běžných balíčků NuGet ve výstupním adresáři také balíčky NuGet pro ladicí symboly. Zdrojové soubory jsou obsaženy ve složce `src` v rámci balíčku symbolů.

- **`--include-symbols`**

  Obsahuje kromě běžných balíčků NuGet ve výstupním adresáři také balíčky NuGet pro ladicí symboly.

- **`--interactive`**

  Umožňuje příkazu zastavit a počkat na vstup nebo akci uživatele (například k dokončení ověřování). K dispozici od verze .NET Core 3,0 SDK.

- **`--no-build`**

  Nevytvoří projekt před balením. Také implicitně nastaví příznak `--no-restore`.

- **`--no-dependencies`**

  Ignoruje odkazy z projektu na projekt a obnoví pouze kořenový projekt. Možnost je k dispozici od verze .NET Core 2,0 SDK.

- **`--no-restore`**

  Při spuštění příkazu neprovede implicitní obnovení. Možnost je k dispozici od verze .NET Core 2,0 SDK.

- **`--nologo`**

  Nezobrazuje úvodní nápis nebo zprávu o autorských právech. K dispozici od verze .NET Core 3,0 SDK.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Umístí sestavené balíčky do zadaného adresáře.

- **`--runtime <RUNTIME_IDENTIFIER>`**

  Určuje cílový modul runtime pro obnovení balíčků pro. Seznam identifikátorů modulu runtime (identifikátorů RID) najdete v [katalogu RID](../rid-catalog.md). Možnost je k dispozici od verze .NET Core 2,0 SDK.

- **`-s|--serviceable`**

  Nastaví v balíčku příznak služby. Další informace najdete na [blogu .NET: rozhraní .NET 4.5.1 podporuje aktualizace zabezpečení Microsoftu pro knihovny NuGet pro .NET](https://aka.ms/nupkgservicing).

- **`--version-suffix <VERSION_SUFFIX>`**

  Definuje hodnotu vlastnosti `$(VersionSuffix)` MSBuild v projektu.

- **`-v|--verbosity <LEVEL>`**

  Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`.

## <a name="examples"></a>Příklady

- Sbalit projekt v aktuálním adresáři:

  ```dotnetcli
  dotnet pack
  ```

- Sbalení `app1` projektu:

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj
  ```

- Sbalení projektu v aktuálním adresáři a umístění výsledných balíčků do složky `nupkgs`:

  ```dotnetcli
  dotnet pack --output nupkgs
  ```

- Sbalení projektu v aktuálním adresáři do složky `nupkgs` a přeskočení kroku sestavení:

  ```dotnetcli
  dotnet pack --no-build --output nupkgs
  ```

- S příponou verze projektu nakonfigurovanou jako `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` v souboru *. csproj* rozbalte aktuální projekt a aktualizujte výslednou verzi balíčku s danou příponou:

  ```dotnetcli
  dotnet pack --version-suffix "ci-1234"
  ```

- Nastavte verzi balíčku na `2.1.0` s vlastností `PackageVersion` MSBuild:

  ```dotnetcli
  dotnet pack -p:PackageVersion=2.1.0
  ```

- Sbalení projektu pro konkrétní [cílové rozhraní](../../standard/frameworks.md):

  ```dotnetcli
  dotnet pack -p:TargetFrameworks=net45
  ```

- Sbalení projektu a použití konkrétního modulu runtime (Windows 10) pro operaci obnovení (.NET Core SDK 2,0 a novější verze):

  ```dotnetcli
  dotnet pack --runtime win10-x64
  ```

- Sbalení projektu pomocí [souboru. nuspec](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec):

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj -p:NuspecFile=~/projects/app1/project.nuspec -p:NuspecBasePath=~/projects/app1/nuget
  ```
