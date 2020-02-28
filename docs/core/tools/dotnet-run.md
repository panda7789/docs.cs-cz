---
title: příkaz dotnet run
description: Příkaz dotnet Run poskytuje pohodlný způsob, jak spustit aplikaci ze zdrojového kódu.
ms.date: 02/19/2020
ms.openlocfilehash: e442ed56d676ffd189ef6d394d840cea671c2dc6
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157073"
---
# <a name="dotnet-run"></a>dotnet run

**Tento článek se týká:** ✔️ .NET Core 2. x SDK a novějších verzí

## <a name="name"></a>Název

`dotnet run` – spustí zdrojový kód bez explicitních příkazů Compile nebo Launch.

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--interactive] [--launch-profile]
    [--no-build] [--no-dependencies] [--no-launch-profile] [--no-restore] [-p|--project]
    [-r|--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

## <a name="description"></a>Popis

Příkaz `dotnet run` poskytuje pohodlný způsob, jak spustit aplikaci ze zdrojového kódu pomocí jednoho příkazu. Je vhodný pro rychlý iterativní vývoj z příkazového řádku. Příkaz závisí na příkazu [`dotnet build`](dotnet-build.md) pro sestavení kódu. Všechny požadavky na sestavení, například, že je nutné nejprve obnovit projekt, platí pro `dotnet run`.

Výstupní soubory jsou zapsány do výchozího umístění, které je `bin/<configuration>/<target>`. Pokud máte například aplikaci `netcoreapp2.1` a spustíte `dotnet run`, výstup je umístěný v `bin/Debug/netcoreapp2.1`. Soubory jsou v případě potřeby přepsány. Dočasné soubory jsou umístěny v adresáři `obj`.

Pokud projekt určuje více rozhraní, spuštění `dotnet run` způsobí chybu, pokud není použita možnost `-f|--framework <FRAMEWORK>` k určení architektury.

Příkaz `dotnet run` se používá v kontextu projektů, nikoli ve vytvořených sestaveních. Pokud se pokoušíte spustit knihovnu DLL aplikace závislou na rozhraní, je nutné použít příkaz [dotnet](dotnet.md) bez příkazu. Pokud například chcete spustit `myapp.dll`, použijte:

```dotnetcli
dotnet myapp.dll
```

Další informace o ovladači `dotnet` naleznete v tématu [.NET Core Command line Tools (CLI)](index.md) .

Chcete-li spustit aplikaci, příkaz `dotnet run` vyřeší závislosti aplikace, které jsou mimo sdílený modul runtime z mezipaměti NuGet. Protože používá závislosti v mezipaměti, nedoporučuje se používat `dotnet run` ke spouštění aplikací v produkčním prostředí. Místo toho [vytvořte nasazení](../deploying/index.md) pomocí příkazu [`dotnet publish`](dotnet-publish.md) a nasaďte publikovaný výstup.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a>Možnosti

- **`--`**

  Odděluje argumenty pro `dotnet run` z argumentů pro spouštěnou aplikaci. Všechny argumenty po tomto oddělovači jsou předány spuštění aplikace.

- **`-c|--configuration <CONFIGURATION>`**

  Definuje konfiguraci sestavení. Výchozí hodnota pro většinu projektů je `Debug`, ale můžete přepsat nastavení konfigurace sestavení v projektu.

- **`-f|--framework <FRAMEWORK>`**

  Vytvoří a spustí aplikaci pomocí zadaného [rozhraní](../../standard/frameworks.md). Rozhraní musí být určeno v souboru projektu.

- **`--force`**

  Vynutí vyřešení všech závislostí i v případě, že bylo poslední obnovení úspěšné. Zadání tohoto příznaku je stejné jako odstranění souboru *Project. assets. JSON* .

- **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

- **`--interactive`**

  Umožňuje příkazu zastavit a počkat na vstup nebo akci uživatele (například k dokončení ověřování). K dispozici od verze .NET Core 3,0 SDK.

- **`--launch-profile <NAME>`**

  Název spouštěcího profilu (pokud existuje), který se má použít při spouštění aplikace Spouštěcí profily jsou definované v souboru *launchSettings. JSON* a obvykle se nazývají `Development`, `Staging`a `Production`. Další informace najdete v tématu [práce s více prostředími](/aspnet/core/fundamentals/environments).

- **`--no-build`**

  Před spuštěním nevytvoří projekt. Také implicitně nastaví příznak `--no-restore`.

- **`--no-dependencies`**

  Při obnovení projektu s odkazy z projektu na projekt (P2P) obnoví kořenový projekt a nikoli odkazy.

- **`--no-launch-profile`**

  Nepokusí se nakonfigurovat aplikaci pomocí *launchSettings. JSON* .

- **`--no-restore`**

  Při spuštění příkazu neprovede implicitní obnovení.

- **`-p|--project <PATH>`**

  Určuje cestu k souboru projektu, který se má spustit (název složky nebo úplná cesta). Pokud není zadaný, použije se ve výchozím nastavení aktuální adresář.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Určuje cílový modul runtime pro obnovení balíčků pro. Seznam identifikátorů modulu runtime (identifikátorů RID) najdete v [katalogu RID](../rid-catalog.md). pro sadu .NET Core 3,0 SDK je `-r` k dispozici krátká možnost.

- **`-v|--verbosity <LEVEL>`**

  Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`. Výchozí hodnota je `m`. K dispozici od verze .NET Core 2,1 SDK.

## <a name="examples"></a>Příklady

- Spustit projekt v aktuálním adresáři:

  ```dotnetcli
  dotnet run
  ```

- Spustit zadaný projekt:

  ```dotnetcli
  dotnet run --project ./projects/proj1/proj1.csproj
  ```

- Spustí projekt v aktuálním adresáři (`--help` argument v tomto příkladu je předán do aplikace, protože je použita možnost prázdné `--`):

  ```dotnetcli
  dotnet run --configuration Release -- --help
  ```

- Obnovte závislosti a nástroje pro projekt v aktuálním adresáři pouze s minimálním výstupem a potom spusťte projekt: (.NET Core SDK 2,0 a novější verze):

  ```dotnetcli
  dotnet run --verbosity m
  ```
