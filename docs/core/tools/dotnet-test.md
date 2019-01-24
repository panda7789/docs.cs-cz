---
title: příkaz DotNet test
description: Příkaz dotnet test slouží ke spuštění testů jednotek v daném projektu.
ms.date: 05/29/2018
ms.openlocfilehash: 1b2a3917a930db0c0a49ebea41f568aaf4a58ee3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54535279"
---
# <a name="dotnet-test"></a>DotNet test

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet test` -Ovladač test .NET ke spuštění testů jednotek.

## <a name="synopsis"></a>Souhrn

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] 
    [-v|--verbosity] [-- <RunSettings arguments>]

dotnet test [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]

dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]

dotnet test [-h|--help]
```

---

## <a name="description"></a>Popis

`dotnet test` Příkaz se používá ke spuštění testů jednotek v daném projektu. `dotnet test` Příkaz spustí zadaný pro projekt test runner konzolovou aplikaci. Nástroj test runner sestavy úspěch nebo selhání jednotlivých testovacích a spustí testy, které jsou definovány pro rozhraní testování částí (například MSTest, NUnit nebo xUnit). Pokud všechny testy jsou úspěšné, nástroj test runner vrátí hodnotu 0 jako ukončovací kód; jinak pokud nějaký test selže, vrátí se 1. Nástroj test runner a knihovnu testu jednotky jsou dodávány jako balíčky NuGet a se obnoví jako běžný závislosti projektu.

Projekty testů zadat nástroje test runner pomocí běžný `<PackageReference>` elementu, jak je znázorněno v následující ukázkový soubor projektu:

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a>Arguments

`PROJECT`

Cesta k projektu testů. Pokud není zadán, použije se výchozí aktuální adresář.

## <a name="options"></a>Možnosti

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

Používáte vlastní adaptéry testu ze zadané cesty v testovacím běhu.

`--blame`

Testy se spustí v režimu viny. Tato možnost je užitečná v izolaci problematické testů způsobí hostitele testu při selhání. Vytvoří výstupní soubor v aktuálním adresáři jako *Sequence.xml* , který zachycuje pořadí provádění testů před selhání.

`-c|--configuration {Debug|Release}`

Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`, ale váš projekt konfigurace může přepsat toto výchozí nastavení sady SDK.

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

Povolí shromažďování dat pro testovací běh. Další informace najdete v tématu [monitorování a analýza testovacího běhu](https://aka.ms/vstest-collect).

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

Umožňuje diagnostickém režimu pro testovací platformy a zápis diagnostické zprávy do zadaného souboru.

`-f|--framework <FRAMEWORK>`

Vyhledá binárních souborů testu pro konkrétní [framework](../../standard/frameworks.md).

`--filter <EXPRESSION>`

Filtruje testy v aktuálním projektu pomocí daného výrazu. Další informace najdete v tématu [možnost podrobnosti filtru](#filter-option-details) oddílu. Další informace a příklady o tom, jak použít selektivní jednotky filtrování testů, naleznete v tématu [spouštění selektivních testů jednotek](../testing/selective-unit-tests.md).

`-h|--help`

Vytiskne krátký nápovědy pro příkaz.

`-l|--logger <LoggerUri/FriendlyName>`

Určuje protokolovací nástroj pro výsledky testů.

`--no-build`

Nepodporuje vytvoření testovacího projektu před jejím spuštěním. Také implicitní nastaví `--no-restore` příznak.

`--no-restore`

Při spuštění příkazu se nebude spouštět implicitní obnovení.

`-o|--output <OUTPUT_DIRECTORY>`

Adresář, ve kterém chcete najít binární soubory, které chcete spustit.

`-r|--results-directory <PATH>`

Adresář, kam výsledky testu budou umístěny. Pokud zadaný adresář neexistuje, vytvoří se.

`-s|--settings <SETTINGS_FILE>`

Nastavení se má použít při spuštění testů.

`-t|--list-tests`

Seznam všech zjištěných testů v aktuálním projektu.

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.

`RunSettings arguments`

Argumenty předány jako RunSettings Konfigurace testu. Argumenty se zadávají jako `[name]=[value]` dvojice po "--" (Poznámka: mezera za--). Mezera se používá k oddělení více `[name]=[value]` dvojice.

Příklad: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`

Další informace o nastavení běhu, naleznete v tématu [vstest.console.exe: Předávání argumentů RunSettings](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

Používáte vlastní adaptéry testu ze zadané cesty v testovacím běhu.

`-c|--configuration {Debug|Release}`

Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`, ale váš projekt konfigurace může přepsat toto výchozí nastavení sady SDK.

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

Povolí shromažďování dat pro testovací běh. Další informace najdete v tématu [monitorování a analýza testovacího běhu](https://aka.ms/vstest-collect).

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

Umožňuje diagnostickém režimu pro testovací platformy a zápis diagnostické zprávy do zadaného souboru.

`-f|--framework <FRAMEWORK>`

Vyhledá binárních souborů testu pro konkrétní [framework](../../standard/frameworks.md).

`--filter <EXPRESSION>`

Filtruje testy v aktuálním projektu pomocí daného výrazu. Další informace najdete v tématu [možnost podrobnosti filtru](#filter-option-details) oddílu. Další informace a příklady o tom, jak použít selektivní jednotky filtrování testů, naleznete v tématu [spouštění selektivních testů jednotek](../testing/selective-unit-tests.md).

`-h|--help`

Vytiskne krátký nápovědy pro příkaz.

`-l|--logger <LoggerUri/FriendlyName>`

Určuje protokolovací nástroj pro výsledky testů.

`--no-build`

Nepodporuje vytvoření testovacího projektu před jejím spuštěním. Také implicitní nastaví `--no-restore` příznak.

`--no-restore`

Při spuštění příkazu se nebude spouštět implicitní obnovení.

`-o|--output <OUTPUT_DIRECTORY>`

Adresář, ve kterém chcete najít binární soubory, které chcete spustit.

`-r|--results-directory <PATH>`

Adresář, kam výsledky testu budou umístěny. Pokud zadaný adresář neexistuje, vytvoří se.

`-s|--settings <SETTINGS_FILE>`

Nastavení se má použít při spuštění testů.

`-t|--list-tests`

Seznam všech zjištěných testů v aktuálním projektu.

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

Používáte vlastní adaptéry testu ze zadané cesty v testovacím běhu.

`-c|--configuration {Debug|Release}`

Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`, ale váš projekt konfigurace může přepsat toto výchozí nastavení sady SDK.

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

Umožňuje diagnostickém režimu pro testovací platformy a zápis diagnostické zprávy do zadaného souboru.

`-f|--framework <FRAMEWORK>`

Vyhledá binárních souborů testu pro konkrétní [framework](../../standard/frameworks.md).

`--filter <EXPRESSION>`

Filtruje testy v aktuálním projektu pomocí daného výrazu. Další informace najdete v tématu [možnost podrobnosti filtru](#filter-option-details) oddílu. Další informace a příklady o tom, jak použít selektivní jednotky filtrování testů, naleznete v tématu [spouštění selektivních testů jednotek](../testing/selective-unit-tests.md).

`-h|--help`

Vytiskne krátký nápovědy pro příkaz.

`-l|--logger <LoggerUri/FriendlyName>`

Určuje protokolovací nástroj pro výsledky testů.

`--no-build`

Nepodporuje vytvoření testovacího projektu před jejím spuštěním.

`-o|--output <OUTPUT_DIRECTORY>`

Adresář, ve kterém chcete najít binární soubory, které chcete spustit.

`-s|--settings <SETTINGS_FILE>`

Nastavení se má použít při spuštění testů.

`-t|--list-tests`

Seznam všech zjištěných testů v aktuálním projektu.

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.

---

## <a name="examples"></a>Příklady

Spusťte testy v projektu v aktuálním adresáři:

`dotnet test`

Spustit testy v `test1` projektu:

`dotnet test ~/projects/test1/test1.csproj`

Spuštění testů v projektu v aktuálním adresáři a vygenerovat soubor s výsledky testu ve formátu trx:

`dotnet test --logger:trx`

## <a name="filter-option-details"></a>Možnost podrobnosti filtru

`--filter <EXPRESSION>`

`<Expression>` má formát `<property><operator><value>[|&<Expression>]`.

`<property>` je atribut `Test Case`. Toto jsou vlastnosti podporované rozhraní pro testování částí oblíbených:

| Rozhraní pro testování | Podporovaných vlastností                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| MSTest         | <ul><li>FullyQualifiedName</li><li>Název</li><li>Název třídy</li><li>Priorita</li><li>TestCategory</li></ul> |
| xUnit          | <ul><li>FullyQualifiedName</li><li>displayName</li><li>Osobnostní rysy</li></ul>                                   |

`<operator>` Popisuje vztah mezi vlastnosti a hodnotu:

| Operátor | Funkce        |
| :------: | --------------- |
| `=`      | Přesná shoda     |
| `!=`     | Není přesná shoda |
| `~`      | Obsahuje        |

`<value>` je řetězec. Všechna vyhledávání jsou malá a velká písmena.

Výraz bez `<operator>` je automaticky považováno za `contains` na `FullyQualifiedName` vlastnosti (například `dotnet test --filter xyz` je stejná jako `dotnet test --filter FullyQualifiedName~xyz`).

Výrazy jde připojit k podmíněných operátorů:

| Operátor            | Funkce |
| ------------------- | -------- |
| <code>&#124;</code> | NEBO       |
| `&`                 | AND      |

Je možné uzavřít do uvozovek výrazy v závorkách při použití podmíněných operátorů (například `(Name~TestMethod1) | (Name~TestMethod2)`).

Další informace a příklady o tom, jak použít selektivní jednotky filtrování testů, naleznete v tématu [spouštění selektivních testů jednotek](../testing/selective-unit-tests.md).

## <a name="see-also"></a>Viz také:

- [Architektury a cíle](../../standard/frameworks.md)
- [.NET core Runtime identifikátor (RID) katalogu](../rid-catalog.md)
