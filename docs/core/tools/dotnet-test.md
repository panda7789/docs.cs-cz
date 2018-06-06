---
title: DotNet. příkaz test - .NET Core rozhraní příkazového řádku
description: Příkaz dotnet testu se používá k provedení testů jednotek v daný projekt.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 8a10ac9175ee5fcf8649efbb07d8d382ac3afdc7
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696267"
---
# <a name="dotnet-test"></a>test DotNet.

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet test` -Ovladač test .NET použít ke spuštění testů jednotek.

## <a name="synopsis"></a>Stručný obsah

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)
```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)
```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)
```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]
dotnet test [-h|--help]
```
---

## <a name="description"></a>Popis

`dotnet test` Příkaz se používá k provedení testů jednotek v daný projekt. `dotnet test` Příkaz spustí zadaný pro projekt test runner konzolové aplikace. Nástroj test runner provede testů definovaných pro systém testování částí (například Mstestu, NUnit nebo xUnit) a oznámí úspěšné nebo neúspěšné každého testu. Nástroj test runner a knihovně test jednotky spojených jako balíčků NuGet a se obnoví jako obyčejnou závislosti pro projekt.

Nástroj test runner pomocí běžný zadejte projektů testování `<PackageReference>` elementu, jak je vidět v následujícím souboru projektu vzorku:

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a>Arguments

`PROJECT`

Cesta pro projekt test. Pokud není zadáno, bude výchozí aktuální adresář.

## <a name="options"></a>Možnosti

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

V testovacím běhu použijte vlastní test adaptéry ze zadané cesty.

`--blame`

Testy se spustí v režimu viny. Tato možnost je užitečná v izolace problematické testy způsobuje testovacího hostitele k chybě. Vytvoří výstupní soubor v aktuálním adresáři jako *Sequence.xml* který zachycuje pořadí provádění testů před havárii.

`-c|--configuration {Debug|Release}`

Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`, ale konfigurace vašeho projektu může přepsat toto výchozí nastavení SDK.

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

Umožňuje kolekce dat pro test spustit. Další informace najdete v tématu [monitorování a analyzovat testu](https://aka.ms/vstest-collect).

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

Umožňuje diagnostiky režimu pro testovací platformy a zápis diagnostické zprávy do určeného souboru.

`-f|--framework <FRAMEWORK>`

Vyhledá testovací binární soubory pro konkrétní [framework](../../standard/frameworks.md).

`--filter <EXPRESSION>`

Filtruje testy v aktuálním projektu pomocí daného výrazu. Další informace najdete v tématu [filtrovat možnost Podrobnosti](#filter-option-details) části. Další příklady a další informace o tom, jak pomocí filtrování testovací selektivní jednotky, najdete v části [spouštění testů jednotek selektivní](../testing/selective-unit-tests.md).

`-h|--help`

Vytiskne krátké nápovědy pro příkaz.

`-l|--logger <LoggerUri/FriendlyName>`

Určuje protokolovacího nástroje pro výsledky testů.

`--no-build`

Před spuštěním není sestavte projekt test. Také implicitní nastaví `--no-restore` příznak.

`--no-restore`

Implicitní obnovení není spustit, když spustíte příkaz.

`-o|--output <OUTPUT_DIRECTORY>`

Adresář, ve kterém chcete najít binární soubory ke spuštění.

`-r|--results-directory <PATH>`

Adresář, kde se chystáte výsledky testů umístit. Pokud zadaný adresář neexistuje, vytvoří se.

`-s|--settings <SETTINGS_FILE>`

Nastavení se má použít při spouštění testů.

`-t|--list-tests`

Seznam všech zjištěných testů v aktuálním projektu.

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.

# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

V testovacím běhu použijte vlastní test adaptéry ze zadané cesty.

`-c|--configuration {Debug|Release}`

Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`, ale konfigurace vašeho projektu může přepsat toto výchozí nastavení SDK.

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

Umožňuje kolekce dat pro test spustit. Další informace najdete v tématu [monitorování a analyzovat testu](https://aka.ms/vstest-collect).

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

Umožňuje diagnostiky režimu pro testovací platformy a zápis diagnostické zprávy do určeného souboru.

`-f|--framework <FRAMEWORK>`

Vyhledá testovací binární soubory pro konkrétní [framework](../../standard/frameworks.md).

`--filter <EXPRESSION>`

Filtruje testy v aktuálním projektu pomocí daného výrazu. Další informace najdete v tématu [filtrovat možnost Podrobnosti](#filter-option-details) části. Další příklady a další informace o tom, jak pomocí filtrování testovací selektivní jednotky, najdete v části [spouštění testů jednotek selektivní](../testing/selective-unit-tests.md).

`-h|--help`

Vytiskne krátké nápovědy pro příkaz.

`-l|--logger <LoggerUri/FriendlyName>`

Určuje protokolovacího nástroje pro výsledky testů.

`--no-build`

Před spuštěním není sestavte projekt test. Také implicitní nastaví `--no-restore` příznak.

`--no-restore`

Implicitní obnovení není spustit, když spustíte příkaz.

`-o|--output <OUTPUT_DIRECTORY>`

Adresář, ve kterém chcete najít binární soubory ke spuštění.

`-r|--results-directory <PATH>`

Adresář, kde se chystáte výsledky testů umístit. Pokud zadaný adresář neexistuje, vytvoří se.

`-s|--settings <SETTINGS_FILE>`

Nastavení se má použít při spouštění testů.

`-t|--list-tests`

Seznam všech zjištěných testů v aktuálním projektu.

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.

# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

V testovacím běhu použijte vlastní test adaptéry ze zadané cesty.

`-c|--configuration {Debug|Release}`

Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`, ale konfigurace vašeho projektu může přepsat toto výchozí nastavení SDK.

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

Umožňuje diagnostiky režimu pro testovací platformy a zápis diagnostické zprávy do určeného souboru.

`-f|--framework <FRAMEWORK>`

Vyhledá testovací binární soubory pro konkrétní [framework](../../standard/frameworks.md).

`--filter <EXPRESSION>`

Filtruje testy v aktuálním projektu pomocí daného výrazu. Další informace najdete v tématu [filtrovat možnost Podrobnosti](#filter-option-details) části. Další příklady a další informace o tom, jak pomocí filtrování testovací selektivní jednotky, najdete v části [spouštění testů jednotek selektivní](../testing/selective-unit-tests.md).

`-h|--help`

Vytiskne krátké nápovědy pro příkaz.

`-l|--logger <LoggerUri/FriendlyName>`

Určuje protokolovacího nástroje pro výsledky testů.

`--no-build`

Před spuštěním není sestavte projekt test.

`-o|--output <OUTPUT_DIRECTORY>`

Adresář, ve kterém chcete najít binární soubory ke spuštění.

`-s|--settings <SETTINGS_FILE>`

Nastavení se má použít při spouštění testů.

`-t|--list-tests`

Seznam všech zjištěných testů v aktuálním projektu.

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.

---

## <a name="examples"></a>Příklady

Spouštět testy v projekt v aktuálním adresáři:

`dotnet test`

Spouštět testy v `test1` projektu:

`dotnet test ~/projects/test1/test1.csproj`

## <a name="filter-option-details"></a>Podrobnosti o možnost filtru

`--filter <EXPRESSION>`

`<Expression>` má formát `<property><operator><value>[|&<Expression>]`.

`<property>` je atributem `Test Case`. Tady jsou vlastnostech podporovaných zprostředkovatelem systémů testů jednotek oblíbených:

| Test Framework | Podporovaných vlastností                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| MSTest         | <ul><li>Položka FullyQualifiedName</li><li>Název</li><li>Název třídy</li><li>Priorita</li><li>TestCategory</li></ul> |
| xUnit          | <ul><li>Položka FullyQualifiedName</li><li>displayName</li><li>Vlastnosti</li></ul>                                   |

`<operator>` Popisuje vztah mezi vlastnosti a hodnotu:

| Operátor | Funkce        |
| :------: | --------------- |
| `=`      | Přesná shoda     |
| `!=`     | Není přesná shoda |
| `~`      | Obsahuje        |

`<value>` obsahuje řetězec. Všechny hledání se malá a velká písmena.

Výraz bez `<operator>` je automaticky považováno za `contains` na `FullyQualifiedName` vlastnosti (například `dotnet test --filter xyz` je stejný jako `dotnet test --filter FullyQualifiedName~xyz`).

Výrazy lze spojit s podmíněné operátory:

| Operátor            | Funkce |
| ------------------- | -------- |
| <code>&#124;</code> | NEBO       |
| `&`                 | AND      |

Můžete uzavřete výrazy v závorkách, při použití podmíněné operátory (například `(Name~TestMethod1) | (Name~TestMethod2)`).

Další příklady a další informace o tom, jak pomocí filtrování testovací selektivní jednotky, najdete v části [spouštění testů jednotek selektivní](../testing/selective-unit-tests.md).

## <a name="see-also"></a>Viz také:

[Rozhraní a cíle](../../standard/frameworks.md)  
[Katalog .NET core Runtime identifikátor (RID)](../rid-catalog.md)
