---
title: dotnet sestavení, příkaz
description: Příkaz sestavení dotnet vytvoří projekt a všechny jeho závislosti.
ms.date: 02/14/2020
ms.openlocfilehash: 9f9a78ec0a6a25c54c8a727c05081ce6835514ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503760"
---
# <a name="dotnet-build"></a>dotnet build

**Tento článek se týká:** ✔️ .NET Core 2.x SDK a novější verze

## <a name="name"></a>Name (Název)

`dotnet build`- Vytvoří projekt a všechny jeho závislosti.

## <a name="synopsis"></a>Synopse

```dotnetcli
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--force]
    [--interactive] [--no-dependencies] [--no-incremental] [--no-restore] [--nologo]
    [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```

## <a name="description"></a>Popis

Příkaz `dotnet build` vytvoří projekt a jeho závislosti do sady binárních souborů. Binární soubory zahrnují kód projektu v souborech zprostředkujícíjazyk (IL) s příponou *DLL.*  V závislosti na typu a nastavení projektu mohou být zahrnuty další soubory, například:

- Spustitelný soubor, který lze použít ke spuštění aplikace, pokud je typ projektu spustitelným cílením .NET Core 3.0 nebo novějším.
- Soubory symbolů používané pro ladění s příponou *PDB.*
- Soubor *.deps.json,* který obsahuje seznam závislostí aplikace nebo knihovny.
- Soubor *.runtimeconfig.json,* který určuje sdílený čas runtime a jeho verzi pro aplikaci.
- Další knihovny, na kterých projekt závisí (prostřednictvím odkazů na projekt nebo odkazů na balíček NuGet).

U spustitelných projektů zaměřených na verze starší než .NET Core 3.0 se závislosti knihovny z NuGet obvykle nezkopírují do výstupní složky.  Jsou vyřešeny ze složky globálních balíčků NuGet za běhu. S ohledem na to `dotnet build` není produkt připraven k přenosu do jiného stroje ke spuštění. Chcete-li vytvořit verzi aplikace, kterou lze nasadit, musíte ji publikovat (například pomocí příkazu [dotnet publish).](dotnet-publish.md) Další informace naleznete v tématu [.NET Core Application Deployment](../deploying/index.md).

U spustitelných projektů zaměřených na rozhraní .NET Core 3.0 a novější jsou závislosti knihovny zkopírovány do výstupní složky. To znamená, že pokud neexistuje žádná jiná logika specifická pro publikování (například webové projekty mají), výstup sestavení by měl být nasaditelný.

Sestavení vyžaduje soubor *project.assets.json,* který obsahuje seznam závislostí vaší aplikace. Soubor je vytvořen [`dotnet restore`](dotnet-restore.md) při spuštění. Bez souboru datových zdrojů na místě nástroje nelze vyřešit referenční sestavení, což má za následek chyby. Pomocí sady .NET Core 1.x SDK `dotnet restore` bylo `dotnet build`nutné před spuštěním explicitně spustit . Počínaje sadou .NET Core 2.0 `dotnet restore` SDK, `dotnet build`běží implicitně při spuštění . Pokud chcete zakázat implicitní obnovení při spuštění příkazu sestavení, můžete předat `--no-restore` možnost.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

Zda je projekt spustitelný nebo není, je určena `<OutputType>` vlastností v souboru projektu. Následující příklad ukazuje projekt, který vytváří spustitelný kód:

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

Chcete-li vytvořit knihovnu, `<OutputType>` vynechte `Library`vlastnost nebo změňte její hodnotu na . Knihovna IL DLL pro knihovnu neobsahuje vstupní body a nelze ji spustit.

### <a name="msbuild"></a>MSBuild

`dotnet build`používá MSBuild k sestavení projektu, takže podporuje paralelní i přírůstkové sestavení. Další informace naleznete [v tématu Přírůstková sestavení](/visualstudio/msbuild/incremental-builds).

Kromě jeho možnosti `dotnet build` příkaz přijímá MSBuild možnosti, `-p` například `-l` pro nastavení vlastností nebo definovat protokolování. Další informace o těchto možnostech naleznete v [odkazu na příkazový řádek msbuildu](/visualstudio/msbuild/msbuild-command-line-reference). Nebo můžete také použít příkaz [dotnet msbuild.](dotnet-msbuild.md)

Běh `dotnet build` je ekvivalentní `dotnet msbuild -restore`běhu ; výchozí podrobnost výstupu se však liší.

## <a name="arguments"></a>Argumenty

`PROJECT | SOLUTION`

Soubor projektu nebo řešení k sestavení. Pokud není zadán soubor projektu nebo řešení, MSBuild vyhledá aktuální pracovní adresář pro soubor, který má příponu souboru, který končí *buď proj* nebo *sln* a používá tento soubor.

## <a name="options"></a>Možnosti

- **`-c|--configuration <CONFIGURATION>`**

  Definuje konfiguraci sestavení. Výchozí hodnota pro `Debug`většinu projektů je , ale můžete přepsat nastavení konfigurace sestavení v projektu.

- **`-f|--framework <FRAMEWORK>`**

  Zkompiluje pro konkrétní [rámec](../../standard/frameworks.md). Rámec musí být definován v [souboru projektu](csproj.md).

- **`--force`**

  Vynutí vyřešení všech závislostí, i když bylo poslední obnovení úspěšné. Zadání tohoto příznaku je stejné jako odstranění souboru *project.assets.json.*

- **`-h|--help`**

  Vytiskne krátkou nápovědu pro příkaz.

- **`--interactive`**

  Umožňuje příkazu zastavit a čekat na vstup uživatele nebo akci. Například k dokončení ověřování. K dispozici od .NET Core 3.0 SDK.

- **`--no-dependencies`**

  Ignoruje odkazy projekt-projekt (P2P) a pouze vytvoří zadaný kořenový projekt.

- **`--no-incremental`**

  Označí sestavení jako nebezpečné pro přírůstkové sestavení. Tento příznak vypne přírůstkovou kompilaci a vynutí čisté opětovné sestavení grafu závislostí projektu.

- **`--no-restore`**

  Neprovede implicitní obnovení během sestavení.

- **`--nologo`**

  Nezobrazuje spouštěcí banner ani zprávu o autorských právech. K dispozici od .NET Core 3.0 SDK.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Adresář, do kterého chcete umístit vytvořené binární soubory. Pokud není zadán, výchozí `./bin/<configuration>/<framework>/`cesta je .  Pro projekty s více cílových rozhraní (prostřednictvím vlastnosti) `TargetFrameworks` je také nutné definovat, `--framework` když zadáte tuto možnost.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Určuje cílový čas běhu. Seznam identifikátorů modulu Runtime (RID) naleznete v [katalogu RID](../rid-catalog.md).

- **`-v|--verbosity <LEVEL>`**

  Nastaví úroveň podrobností MSBuild. Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a . Výchozí formát je `minimal`.

- **`--version-suffix <VERSION_SUFFIX>`**

  Nastaví hodnotu `$(VersionSuffix)` vlastnosti, která má být používána při vytváření projektu. To funguje pouze `$(Version)` v případě, že vlastnost není nastavena. Potom `$(Version)` je nastavena `$(VersionPrefix)` na kombinaci `$(VersionSuffix)`s , oddělenou pomlčkou.

## <a name="examples"></a>Příklady

- Sestavení projektu a jeho závislostí:

  ```dotnetcli
  dotnet build
  ```

- Sestavení projektu a jeho závislostí pomocí konfigurace verze:

  ```dotnetcli
  dotnet build --configuration Release
  ```

- Sestavení projektu a jeho závislostí pro konkrétní běhový čas (v tomto příkladu Ubuntu 18.04):

  ```dotnetcli
  dotnet build --runtime ubuntu.18.04-x64
  ```

- Vytvořte projekt a použijte zadaný zdroj balíčku NuGet během operace obnovení (sada SDK.NET Core 2.0 a novější verze):

  ```dotnetcli
  dotnet build --source c:\packages\mypackages
  ```

- Vytvořte projekt a nastavte verzi 1.2.3.4 `-p` jako parametr sestavení pomocí [možnosti MSBuild](#msbuild):

  ```dotnetcli
  dotnet build -p:Version=1.2.3.4
  ```
