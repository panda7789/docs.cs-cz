---
title: DotNet. příkaz test - .NET Core rozhraní příkazového řádku
description: Příkaz dotnet testu se používá k provedení testů jednotek v daný projekt.
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 6102281c4daf149f31e65ef8360831fe9e0ef4f6
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2018
---
# <a name="dotnet-test"></a>test DotNet.

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet test` -Ovladač test .NET použít ke spuštění testů jednotek.

## <a name="synopsis"></a>Stručný obsah

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)


```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
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

Určuje cestu pro projekt test. Při vynechání je použita k aktuálnímu adresáři.

## <a name="options"></a>Možnosti

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

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

Nelze sestavit k testovacímu projektu před jejím spuštěním.

`--no-restore`

Neprovede implicitní obnovení, při spuštění příkazu.

`-o|--output <OUTPUT_DIRECTORY>`

Adresář, ve kterém chcete najít binární soubory ke spuštění.

`-r|--results-directory <PATH>`

Adresář, kde se chystáte výsledky testů umístit. Zadaný adresář bude vytvořen, pokud neexistuje.

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

Nelze sestavit k testovacímu projektu před jejím spuštěním.

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
| :------------: | --------------------------------------------------------------------------------------------------------- |
| MSTest         | <ul><li>Položka FullyQualifiedName</li><li>Název</li><li>ClassName</li><li>Priorita</li><li>TestCategory</li></ul> |
| xunit          | <ul><li>Položka FullyQualifiedName</li><li>DisplayName</li><li>Vlastnosti</li></ul>                                   |

`<operator>` Popisuje vztah mezi vlastnosti a hodnotu:

| Operátor | Funkce        |
| :------: | --------------- |
| `=`      | Přesná shoda     |
| `!=`     | Není přesná shoda |
| `~`      | Obsahuje        |

`<value>` obsahuje řetězec. Všechny hledání se malá a velká písmena.

Výraz bez `<operator>` je automaticky považováno za `contains` na `FullyQualifiedName` vlastnosti (například `dotnet test --filter xyz` je stejný jako `dotnet test --filter FullyQualifiedName~xyz`).

Výrazy lze spojit s podmíněné operátory:

| Operátor | Funkce |
| :------: | :------: |
| <code>&#124;</code>      | NEBO       |
| `&`      | AND      |

Můžete uzavřete výrazy v závorkách, při použití podmíněné operátory (například `(Name~TestMethod1) | (Name~TestMethod2)`).

Další příklady a další informace o tom, jak pomocí filtrování testovací selektivní jednotky, najdete v části [spouštění testů jednotek selektivní](../testing/selective-unit-tests.md).

## <a name="see-also"></a>Viz také

 [Rozhraní a cíle](../../standard/frameworks.md)  
 [Katalog .NET core Runtime identifikátor (RID)](../rid-catalog.md)
