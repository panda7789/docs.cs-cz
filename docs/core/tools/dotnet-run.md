---
title: příkaz dotnet run
description: Příkaz dotnet Run poskytuje pohodlný způsob, jak spustit aplikaci ze zdrojového kódu.
ms.date: 05/29/2018
ms.openlocfilehash: 0a6c1303bc12c256dd0a8923f9468620835ddabc
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202805"
---
# <a name="dotnet-run"></a>dotnet run

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Name

`dotnet run`-Spustí zdrojový kód bez explicitních příkazů Compile nebo Launch.

## <a name="synopsis"></a>Stručný obsah

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

```console
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2,0](#tab/netcore20)

```console
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```console
dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]]
dotnet run [-h|--help]
```

---

## <a name="description"></a>Popis

`dotnet run` Příkaz nabízí pohodlný způsob, jak spustit aplikaci ze zdrojového kódu pomocí jednoho příkazu. Je vhodný pro rychlý iterativní vývoj z příkazového řádku. Příkaz závisí na [`dotnet build`](dotnet-build.md) příkazu pro sestavení kódu. Všechny požadavky na sestavení, jako je třeba projekt, musí být nejprve obnoveny, platí také `dotnet run` pro něj.

Výstupní soubory jsou zapsány do výchozího umístění, což `bin/<configuration>/<target>`je. Například pokud `netcoreapp2.1` máte aplikaci a spustíte `dotnet run`, výstup je umístěný v `bin/Debug/netcoreapp2.1`. Soubory jsou v případě potřeby přepsány. Dočasné soubory jsou umístěny v `obj` adresáři.

Pokud projekt určuje více rozhraní, spuštění `dotnet run` způsobí chybu, `-f|--framework <FRAMEWORK>` Pokud není použita možnost pro určení rozhraní.

`dotnet run` Příkaz se používá v kontextu projektů, nesestavených sestavení. Pokud se pokoušíte spustit knihovnu DLL aplikace závislou na rozhraní, je nutné použít příkaz [dotnet](dotnet.md) bez příkazu. Pokud například chcete spustit `myapp.dll`, použijte:

```console
dotnet myapp.dll
```

Další informace o `dotnet` ovladači naleznete v tématu [.NET Core Command line Tools (CLI)](index.md) .

Pro spuštění aplikace `dotnet run` příkaz vyřeší závislosti aplikace, které jsou mimo sdílený modul runtime z mezipaměti NuGet. Protože používá závislosti v mezipaměti, nedoporučuje se používat `dotnet run` ke spouštění aplikací v produkčním prostředí. Místo toho [vytvořte nasazení](../deploying/index.md) pomocí [`dotnet publish`](dotnet-publish.md) příkazu a nasaďte publikovaný výstup.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a>Možnosti

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

`--`

Odděluje argumenty `dotnet run` z argumentů pro spouštěnou aplikaci. Všechny argumenty po tomto oddělovači jsou předány spuštění aplikace.

`-c|--configuration {Debug|Release}`

Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`.

`-f|--framework <FRAMEWORK>`

Vytvoří a spustí aplikaci pomocí zadaného [rozhraní](../../standard/frameworks.md). Rozhraní musí být určeno v souboru projektu.

`--force`

Vynutí vyřešení všech závislostí i v případě, že bylo poslední obnovení úspěšné. Zadání tohoto příznaku je stejné jako odstranění souboru *Project. assets. JSON* .

`-h|--help`

Vypíše krátkou nápovědu k příkazu.

`--launch-profile <NAME>`

Název spouštěcího profilu (pokud existuje), který se má použít při spouštění aplikace Spouštěcí profily jsou definované v souboru *launchSettings. JSON* a obvykle se nazývají `Development`, `Staging`a `Production`. Další informace najdete v tématu [práce s více prostředími](/aspnet/core/fundamentals/environments).

`--no-build`

Před spuštěním nevytvoří projekt. Také implicitně nastaví `--no-restore` příznak.

`--no-dependencies`

Při obnovení projektu s odkazy z projektu na projekt (P2P) obnoví kořenový projekt a nikoli odkazy.

`--no-launch-profile`

Nepokusí se nakonfigurovat aplikaci pomocí *launchSettings. JSON* .

`--no-restore`

Při spuštění příkazu neprovede implicitní obnovení.

`-p|--project <PATH>`

Určuje cestu k souboru projektu, který se má spustit (název složky nebo úplná cesta). Pokud není zadaný, použije se ve výchozím nastavení aktuální adresář.

`--runtime <RUNTIME_IDENTIFIER>`

Určuje cílový modul runtime pro obnovení balíčků pro. Seznam identifikátorů modulu runtime (identifikátorů RID) najdete v [katalogu RID](../rid-catalog.md).

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]` `d[etailed]`, a .`diag[nostic]`

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2,0](#tab/netcore20)

`--`

Odděluje argumenty `dotnet run` z argumentů pro spouštěnou aplikaci. Všechny argumenty po tomto oddělovači jsou předány spuštění aplikace.

`-c|--configuration {Debug|Release}`

Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`.

`-f|--framework <FRAMEWORK>`

Vytvoří a spustí aplikaci pomocí zadaného [rozhraní](../../standard/frameworks.md). Rozhraní musí být určeno v souboru projektu.

`--force`

Vynutí vyřešení všech závislostí i v případě, že bylo poslední obnovení úspěšné. Zadání tohoto příznaku je stejné jako odstranění souboru *Project. assets. JSON* .

`-h|--help`

Vypíše krátkou nápovědu k příkazu.

`--launch-profile <NAME>`

Název spouštěcího profilu (pokud existuje), který se má použít při spouštění aplikace Spouštěcí profily jsou definované v souboru *launchSettings. JSON* a obvykle se nazývají `Development`, `Staging`a `Production`. Další informace najdete v tématu [práce s více prostředími](/aspnet/core/fundamentals/environments).

`--no-build`

Před spuštěním nevytvoří projekt. Také implicitně nastaví `--no-restore` příznak.

`--no-dependencies`

Při obnovení projektu s odkazy z projektu na projekt (P2P) obnoví kořenový projekt a nikoli odkazy.

`--no-launch-profile`

Nepokusí se nakonfigurovat aplikaci pomocí *launchSettings. JSON* .

`--no-restore`

Při spuštění příkazu neprovede implicitní obnovení.

`-p|--project <PATH>`

Určuje cestu k souboru projektu, který se má spustit (název složky nebo úplná cesta). Pokud není zadaný, použije se ve výchozím nastavení aktuální adresář.

`--runtime <RUNTIME_IDENTIFIER>`

Určuje cílový modul runtime pro obnovení balíčků pro. Seznam identifikátorů modulu runtime (identifikátorů RID) najdete v [katalogu RID](../rid-catalog.md).

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`--`

Odděluje argumenty `dotnet run` z argumentů pro spouštěnou aplikaci. Všechny argumenty po tomto oddělovači jsou předány spuštění aplikace.

`-c|--configuration {Debug|Release}`

Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`.

`-f|--framework <FRAMEWORK>`

Vytvoří a spustí aplikaci pomocí zadaného [rozhraní](../../standard/frameworks.md). Rozhraní musí být určeno v souboru projektu.

`-h|--help`

Vypíše krátkou nápovědu k příkazu.

`-p|--project <PATH/PROJECT.csproj>`

Určuje cestu a název souboru projektu. (Podívejte se na poznámku.) Pokud není zadaný, použije se ve výchozím nastavení aktuální adresář.

> [!NOTE]
> Použijte cestu a název souboru projektu s `-p|--project` možností. Regrese v rozhraní příkazového řádku zabraňuje tomu, aby poskytovala cestu ke složce .NET Core SDK 1. x. Další informace o tomto problému naleznete v tématu [dotnet Run-p. nelze spustit projekt (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).

---

## <a name="examples"></a>Příklady

Spustit projekt v aktuálním adresáři:

`dotnet run`

Spustit zadaný projekt:

`dotnet run --project ./projects/proj1/proj1.csproj`

Spustí projekt v aktuálním adresáři ( `--help` argument v tomto příkladu je předán do aplikace, protože je použita prázdná `--` možnost):

`dotnet run --configuration Release -- --help`

Obnovte závislosti a nástroje pro projekt v aktuálním adresáři pouze s minimálním výstupem a potom spusťte projekt: (.NET Core SDK 2,0 a novější verze):

`dotnet run --verbosity m`
