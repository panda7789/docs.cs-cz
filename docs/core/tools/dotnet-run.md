---
title: dotnet spustit, příkaz
description: Příkaz dotnet run poskytuje vhodnou možnost spuštění aplikace ze zdrojového kódu.
ms.date: 02/19/2020
ms.openlocfilehash: 28ed13a17c127ae1c61548fed8491315db279c20
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463418"
---
# <a name="dotnet-run"></a>dotnet run

**Tento článek se týká:** ✔️ .NET Core 2.x SDK a novější verze

## <a name="name"></a>Název

`dotnet run`- Spustí zdrojový kód bez explicitních příkazů kompilace nebo spuštění.

## <a name="synopsis"></a>Synopse

```dotnetcli
dotnet run [-c|--configuration <CONFIGURATION>] [-f|--framework <FRAMEWORK>]
    [--force] [--interactive] [--launch-profile <NAME>] [--no-build]
    [--no-dependencies] [--no-launch-profile] [--no-restore]
    [-p|--project <PATH>] [-r|--runtime <RUNTIME_IDENTIFIER>]
    [-v|--verbosity <LEVEL>] [[--] [application arguments]]

dotnet run -h|--help
```

## <a name="description"></a>Popis

Příkaz `dotnet run` poskytuje vhodnou možnost spuštění aplikace ze zdrojového kódu pomocí jednoho příkazu. Je to užitečné pro rychlý iterativní vývoj z příkazového řádku. Příkaz závisí na [`dotnet build`](dotnet-build.md) příkaz u vytvoření kódu. Všechny požadavky na sestavení, například že projekt musí být `dotnet run` obnovena jako první, platí také.

Výstupní soubory jsou zapsány do `bin/<configuration>/<target>`výchozího umístění, což je . Například pokud máte `netcoreapp2.1` aplikaci `dotnet run`a spustit , `bin/Debug/netcoreapp2.1`výstup je umístěn v . Soubory jsou přepsány podle potřeby. Dočasné soubory jsou `obj` umístěny v adresáři.

Pokud projekt určuje více rozhraní, `dotnet run` provádění výsledků v `-f|--framework <FRAMEWORK>` chybě, pokud je použita možnost k určení rozhraní.

Příkaz `dotnet run` se používá v kontextu projektů, nikoli sestavení. Pokud se místo toho pokoušíte spustit dll aplikace závislé na rozhraní, musíte použít [dotnet](dotnet.md) bez příkazu. Chcete-li například spustit `myapp.dll`, použijte:

```dotnetcli
dotnet myapp.dll
```

Další informace o `dotnet` ovladači naleznete v tématu [nástroje CLI (.NET Core Command Line Tools).](index.md)

Chcete-li spustit `dotnet run` aplikaci, příkaz řeší závislosti aplikace, které jsou mimo sdílené hodu runtime z mezipaměti NuGet. Vzhledem k tomu, že používá závislosti uložené `dotnet run` v mezipaměti, nedoporučuje se používat ke spouštění aplikací v produkčním prostředí. Místo toho [vytvořte](../deploying/index.md) [`dotnet publish`](dotnet-publish.md) nasazení pomocí příkazu a nasadit publikovaný výstup.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a>Možnosti

- **`--`**

  Vymezuje `dotnet run` argumenty z argumentů pro spuštěnou aplikaci. Všechny argumenty po tomto oddělovači jsou předány spuštění aplikace.

- **`-c|--configuration <CONFIGURATION>`**

  Definuje konfiguraci sestavení. Výchozí hodnota pro `Debug`většinu projektů je , ale můžete přepsat nastavení konfigurace sestavení v projektu.

- **`-f|--framework <FRAMEWORK>`**

  Vytvoří a spustí aplikaci pomocí zadaného [rozhraní](../../standard/frameworks.md). Rámec musí být zadán v souboru projektu.

- **`--force`**

  Vynutí vyřešení všech závislostí, i když bylo poslední obnovení úspěšné. Zadání tohoto příznaku je stejné jako odstranění souboru *project.assets.json.*

- **`-h|--help`**

  Vytiskne krátkou nápovědu pro příkaz.

- **`--interactive`**

  Umožňuje příkazu zastavit a čekat na vstup nebo akci uživatele (například k dokončení ověřování). K dispozici od .NET Core 3.0 SDK.

- **`--launch-profile <NAME>`**

  Název profilu spuštění (pokud existuje) použít při spuštění aplikace. Profily spuštění jsou definovány v souboru *launchSettings.json* a obvykle se nazývají `Development`, `Staging`, a `Production`. Další informace naleznete v [tématu Práce s více prostředími](/aspnet/core/fundamentals/environments).

- **`--no-build`**

  Nesestavuje projekt před spuštěním. Také implicitní `--no-restore` nastaví příznak.

- **`--no-dependencies`**

  Při obnovení projektu s odkazy projekt-projekt (P2P) obnoví kořenový projekt a nikoli odkazy.

- **`--no-launch-profile`**

  Nepokouší se použít *launchSettings.json* ke konfiguraci aplikace.

- **`--no-restore`**

  Nespustí implicitní obnovení při spuštění příkazu.

- **`-p|--project <PATH>`**

  Určuje cestu ke spuštění souboru projektu (název složky nebo úplná cesta). Pokud není zadán, je výchozí aktuální adresář.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Určuje cílový čas běhu, pro který má být obnoveny balíčky. Seznam identifikátorů modulu Runtime (RID) naleznete v [katalogu RID](../rid-catalog.md). `-r`krátká možnost k dispozici od .NET Core 3.0 SDK.

- **`-v|--verbosity <LEVEL>`**

  Nastaví úroveň podrobností příkazu. Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a . Výchozí hodnota je `m`. K dispozici od .NET Core 2.1 SDK.

## <a name="examples"></a>Příklady

- Spusťte projekt v aktuálním adresáři:

  ```dotnetcli
  dotnet run
  ```

- Spusťte zadaný projekt:

  ```dotnetcli
  dotnet run --project ./projects/proj1/proj1.csproj
  ```

- Spusťte projekt v aktuálním adresáři (argument v tomto příkladu `--help` je předán aplikaci, protože se používá prázdná `--` možnost):

  ```dotnetcli
  dotnet run --configuration Release -- --help
  ```

- Obnovení závislostí a nástrojů pro projekt v aktuálním adresáři zobrazující pouze minimální výstup a potom spustit projekt: (.NET Core SDK 2.0 a novější verze):

  ```dotnetcli
  dotnet run --verbosity m
  ```
