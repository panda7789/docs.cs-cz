---
title: dotnet pack, příkaz
description: Příkaz dotnet pack vytvoří balíčky NuGet pro váš projekt .NET Core.
ms.date: 02/14/2020
ms.openlocfilehash: 3b9c46ecd5d67519728896b0018e27fb41ebd861
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463500"
---
# <a name="dotnet-pack"></a>dotnet pack

**Tento článek se týká:** ✔️ .NET Core 2.x SDK a novější verze

## <a name="name"></a>Název

`dotnet pack`- Zabalí kód do balíčku NuGet.

## <a name="synopsis"></a>Synopse

```dotnetcli
dotnet pack [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [--force] [--include-source] [--include-symbols] [--interactive]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo]
    [-o|--output <OUTPUT_DIRECTORY>] [--runtime <RUNTIME_IDENTIFIER>]
    [-s|--serviceable] [-v|--verbosity <LEVEL>]
    [--version-suffix <VERSION_SUFFIX>]

dotnet pack -h|--help
```

## <a name="description"></a>Popis

Příkaz `dotnet pack` vytvoří projekt a vytvoří balíčky NuGet. Výsledkem tohoto příkazu je balíček NuGet (to znamená soubor *.nupkg).*

Pokud chcete vygenerovat balíček, který obsahuje symboly ladění, máte k dispozici dvě možnosti:

- `--include-symbols`- vytváří balíček symbolů.
- `--include-source`- vytváří balíček symbolů se `src` složkou uvnitř obsahující zdrojové soubory.

NuGet závislosti zabalené projektu jsou přidány do souboru *.nuspec,* takže jsou správně vyřešeny při instalaci balíčku. Odkazy na projekt nejsou zabaleny uvnitř projektu. V současné době musíte mít balíček na projekt, pokud máte závislosti mezi projekty.

Ve výchozím `dotnet pack` nastavení nejprve vytvoří projekt. Pokud se chcete tomuto chování `--no-build` vyhnout, předejte tuto možnost. Tato možnost je často užitečné ve scénářích sestavení průběžné integrace (CI), kde víte, že kód byl dříve sestaven.

> [!NOTE]
> V některých případech nelze provést implicitní sestavení. K tomu `GeneratePackageOnBuild` může dojít, když je nastavena, aby se zabránilo cyklické závislosti mezi sestavení a pack cíle. Sestavení může také selhat, pokud je uzamčen soubor nebo jiný problém.

Můžete zadat MSBuild vlastnosti příkazu `dotnet pack` pro proces balení. Další informace naleznete [v tématu Vlastnosti metadat NuGet](csproj.md#nuget-metadata-properties) a [odkaz na příkazový řádek msbuildu](/visualstudio/msbuild/msbuild-command-line-reference). [Příklady](#examples) část ukazuje, jak používat přepínač MSBuild -p pro několik různých scénářů.

Webové projekty nejsou ve výchozím nastavení sbalitelné. Chcete-li přepsat výchozí chování, přidejte do souboru *.csproj* následující vlastnost:

```xml
<PropertyGroup>
   <IsPackable>true</IsPackable>
</PropertyGroup>
```

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a>Argumenty

`PROJECT | SOLUTION`

  Projekt nebo řešení pro balení. Je to buď cesta k [souboru csproj](csproj.md), soubor řešení, nebo do adresáře. Pokud není zadán, příkaz prohledá aktuální adresář pro soubor projektu nebo řešení.

## <a name="options"></a>Možnosti

- **`-c|--configuration <CONFIGURATION>`**

  Definuje konfiguraci sestavení. Výchozí hodnota pro `Debug`většinu projektů je , ale můžete přepsat nastavení konfigurace sestavení v projektu.

- **`--force`**

  Vynutí vyřešení všech závislostí, i když bylo poslední obnovení úspěšné. Zadání tohoto příznaku je stejné jako odstranění souboru *project.assets.json.*

- **`-h|--help`**

  Vytiskne krátkou nápovědu pro příkaz.

- **`--include-source`**

  Obsahuje ladicí symboly NuGet balíčky kromě běžné NuGet balíčky ve výstupním adresáři. Soubory zdrojů jsou zahrnuty ve `src` složce v balíčku symbolů.

- **`--include-symbols`**

  Obsahuje ladicí symboly NuGet balíčky kromě běžné NuGet balíčky ve výstupním adresáři.

- **`--interactive`**

  Umožňuje příkazu zastavit a čekat na vstup nebo akci uživatele (například k dokončení ověřování). K dispozici od .NET Core 3.0 SDK.

- **`--no-build`**

  Nestaví projekt před balením. Také implicitně nastaví příznak. `--no-restore`

- **`--no-dependencies`**

  Ignoruje odkazy projektu na projekt a obnoví pouze kořenový projekt.

- **`--no-restore`**

  Nespustí implicitní obnovení při spuštění příkazu.

- **`--nologo`**

  Nezobrazuje spouštěcí banner ani zprávu o autorských právech. K dispozici od .NET Core 3.0 SDK.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Umístí vytvořené balíčky do zadaného adresáře.

- **`--runtime <RUNTIME_IDENTIFIER>`**

  Určuje cílový čas běhu, pro který má být obnoveny balíčky. Seznam identifikátorů modulu Runtime (RID) naleznete v [katalogu RID](../rid-catalog.md).

- **`-s|--serviceable`**

  Nastaví příznak opravitelný v balíčku. Další informace naleznete [v tématu .NET Blog: .NET 4.5.1 Podporuje aktualizace zabezpečení společnosti Microsoft pro knihovny .NET NuGet](https://aka.ms/nupkgservicing).

- **`--version-suffix <VERSION_SUFFIX>`**

  Definuje hodnotu vlastnosti `$(VersionSuffix)` MSBuild v projektu.

- **`-v|--verbosity <LEVEL>`**

  Nastaví úroveň podrobností příkazu. Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a .

## <a name="examples"></a>Příklady

- Zabalte projekt do aktuálního adresáře:

  ```dotnetcli
  dotnet pack
  ```

- Sbalte `app1` si projekt:

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj
  ```

- Zabalte projekt do aktuálního adresáře a `nupkgs` umístěte výsledné balíčky do složky:

  ```dotnetcli
  dotnet pack --output nupkgs
  ```

- Zabalte projekt do aktuálního `nupkgs` adresáře do složky a přeskočte krok sestavení:

  ```dotnetcli
  dotnet pack --no-build --output nupkgs
  ```

- S příponou verze projektu nakonfigurované jako `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` v souboru *.csproj* zabalte aktuální projekt a aktualizujte výslednou verzi balíčku s danou příponou:

  ```dotnetcli
  dotnet pack --version-suffix "ci-1234"
  ```

- Nastavte verzi balíčku `2.1.0` na `PackageVersion` vlastnost MSBuild:

  ```dotnetcli
  dotnet pack -p:PackageVersion=2.1.0
  ```

- Zabalte projekt pro konkrétní [cílový rámec](../../standard/frameworks.md):

  ```dotnetcli
  dotnet pack -p:TargetFrameworks=net45
  ```

- Zabalte projekt a použijte konkrétní runtime (Windows 10) pro operaci obnovení:

  ```dotnetcli
  dotnet pack --runtime win10-x64
  ```

- Zabalte projekt pomocí [souboru .nuspec](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec):

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj -p:NuspecFile=~/projects/app1/project.nuspec -p:NuspecBasePath=~/projects/app1/nuget
  ```
