---
title: dotnet test, příkaz
description: Dotnet test příkaz se používá k provedení testů částí v daném projektu.
ms.date: 02/27/2020
ms.openlocfilehash: 359e4522b26e2b59092d55eea3fca575d2afaf1f
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121039"
---
# <a name="dotnet-test"></a>dotnet test

**Tento článek se týká:** ✔️ .NET Core 2.1 SDK a novější verze

## <a name="name"></a>Name (Název)

`dotnet test`- Testovací ovladač .NET používaný ke spuštění testů částí.

## <a name="synopsis"></a>Synopse

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION>]
    [-a|--test-adapter-path] [--blame] [-c|--configuration]
    [--collect] [-d|--diag] [-f|--framework] [--filter]
    [--interactive] [-l|--logger] [--no-build] [--nologo]
    [--no-restore] [-o|--output] [-r|--results-directory]
    [--runtime] [-s|--settings] [-t|--list-tests]
    [-v|--verbosity] [[--] <RunSettings arguments>]

dotnet test [-h|--help]
```

## <a name="description"></a>Popis

Příkaz `dotnet test` se používá ke spuštění testů částí v daném projektu. Příkaz `dotnet test` spustí aplikace konzoly pro spuštění testu určená pro projekt. Testovací běžec provede testy definované pro rozhraní testování částí (například MSTest, NUnit nebo xUnit) a hlásí úspěch nebo neúspěch každého testu. Pokud jsou všechny testy úspěšné, testovací běžec vrátí 0 jako ukončovací kód; v opačném případě, pokud některý test selže, vrátí 1. Testovací běžec a knihovna testování částí jsou zabaleny jako balíčky NuGet a jsou obnoveny jako běžné závislosti pro projekt.

Testovací projekty určují testovací `<PackageReference>` běh pomocí běžného prvku, jak je vidět v následujícím ukázkovém souboru projektu:

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a>Argumenty

- **`PROJECT | SOLUTION`**

  Cesta k testovacímu projektu nebo řešení. Pokud není zadán, je výchozí aktuální adresář.

## <a name="options"></a>Možnosti

- **`a|--test-adapter-path <PATH_TO_ADAPTER>`**

  Použijte vlastní testovací adaptéry ze zadané cesty v testovacím běhu.

- **`--blame`**

  Spustí testy v režimu obviňování. Tato možnost je užitečná při izolování problémových testů, které způsobují selhání testovacího hostitele. Vytvoří výstupní soubor v aktuálním adresáři jako *Sequence.xml,* který zachycuje pořadí spuštění testů před selháním.

- **`c|--configuration <CONFIGURATION>`**

  Definuje konfiguraci sestavení. Výchozí hodnota `Debug`je , ale konfigurace projektu může přepsat toto výchozí nastavení sady SDK.

- **`-collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  Povolí sběr dat pro spuštění testu. Další informace naleznete v [tématu Sledování a analýza testovacího běhu](https://aka.ms/vstest-collect).

- **`d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  Povolí diagnostický režim pro testovací platformu a zapisuje diagnostické zprávy do zadaného souboru.

- **`f|--framework <FRAMEWORK>`**

  Vyhledá testovací binární soubory pro konkrétní [rámec](../../standard/frameworks.md).

- **`--filter <EXPRESSION>`**

  Odfiltruje testy v aktuálním projektu pomocí daného výrazu. Další informace naleznete v části [Podrobnosti o možnosti filtr.](#filter-option-details) Další informace a příklady použití filtrace testů selektivních testů částí naleznete v [tématu Spuštění testů selektivních částí](../testing/selective-unit-tests.md).

- **`h|--help`**

  Vytiskne krátkou nápovědu pro příkaz.

- **`--interactive`**

  Umožňuje příkazu zastavit a čekat na vstup uživatele nebo akci. Například k dokončení ověřování. K dispozici od .NET Core 3.0 SDK.

- **`l|--logger <LoggerUri/FriendlyName>`**

  Určuje protokolovací nástroj pro výsledky testů. Na rozdíl od MSBuild, dotnet test nepřijímá zkratky: `-l "console;v=d"` `-l "console;verbosity=detailed"`místo použití .

- **`--no-build`**

  Nesestaví testovací projekt před jeho spuštěním. Také implicitně nastaví `--no-restore` - příznak.

- **`--nologo`**

  Spusťte testy bez zobrazení hlavičky Microsoft TestPlatform. K dispozici od .NET Core 3.0 SDK.

- **`--no-restore`**

  Nespustí implicitní obnovení při spuštění příkazu.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Adresář, ve kterém chcete najít binární soubory ke spuštění.

- **`-r|--results-directory <PATH>`**

  Adresář, kde budou umístěny výsledky testů. Pokud zadaný adresář neexistuje, je vytvořen.

- **`--runtime <RUNTIME_IDENTIFIER>`**

  Cílový runtime, pro který chcete testovat.

- **`-s|--settings <SETTINGS_FILE>`**

  Soubor, `.runsettings` který chcete použít pro spuštění testů. [Nakonfigurujte `.runsettings` testy částí pomocí souboru.](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

- **`-t|--list-tests`**

  Seznam všech zjištěných testů v aktuálním projektu.

- **`-v|--verbosity <LEVEL>`**

  Nastaví úroveň podrobností příkazu. Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a . Výchozí formát je `minimal`. Další informace naleznete v tématu <xref:Microsoft.Build.Framework.LoggerVerbosity>.

- `RunSettings`Argumenty

  Argumenty jsou `RunSettings` předány jako konfigurace pro test. Argumenty jsou `[name]=[value]` určeny jako páry po "-- " (všimněte si mezery po --). Mezera se používá `[name]=[value]` k oddělení více párů.

  Příklad: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`

  Další informace naleznete [v vstest.console.exe: Předávání RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).

## <a name="examples"></a>Příklady

- Spusťte testy v projektu v aktuálním adresáři:

  ```dotnetcli
  dotnet test
  ```

- Spusťte testy `test1` v projektu:

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- Spusťte testy v projektu v aktuálním adresáři a vygenerujte soubor výsledků testu ve formátu trx:

  ```dotnetcli
  dotnet test --logger trx
  ```

- Spusťte testy v projektu v aktuálním adresáři a protokolujte s podrobnou podrobností do konzoly:

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```

## <a name="filter-option-details"></a>Podrobnosti o možnosti filtru

`--filter <EXPRESSION>`

`<Expression>`má formát `<property><operator><value>[|&<Expression>]`.

`<property>`je atributem `Test Case`. Následují vlastnosti podporované populární rozhraní testování částí:

| Testovací rámec | Podporované vlastnosti                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| MSTest         | <ul><li>Plně kvalifikovaný název</li><li>Name (Název)</li><li>Classname</li><li>Priorita</li><li>Kategorie testů</li></ul> |
| xJednotka          | <ul><li>Plně kvalifikovaný název</li><li>DisplayName</li><li>Vlastnosti</li></ul>                                   |

Popisuje `<operator>` vztah mezi vlastností a hodnotou:

| Operátor | Funkce        |
| :------: | --------------- |
| `=`      | Přesná shoda     |
| `!=`     | Není přesná shoda |
| `~`      | Contains        |
| `!~`     | Neobsahuje    |

`<value>`je řetězec. Všechna vyhledávání jsou malá a velká písmena.

Výraz bez `<operator>` je automaticky považován `contains` `FullyQualifiedName` za vlastnost on `dotnet test --filter xyz` (například je stejný jako `dotnet test --filter FullyQualifiedName~xyz`).

Výrazy lze spojit s podmíněnými operátory:

| Operátor            | Funkce |
| ------------------- | -------- |
| <code>&#124;</code> | NEBO       |
| `&`                 | AND      |

Výrazy můžete uzavřít do závorek při použití podmíněných operátorů `(Name~TestMethod1) | (Name~TestMethod2)`(například).

Další informace a příklady použití filtrace testů selektivních testů částí naleznete v [tématu Spuštění testů selektivních částí](../testing/selective-unit-tests.md).

## <a name="see-also"></a>Viz také

- [Rámce a cíle](../../standard/frameworks.md)
- [Katalog IDentifier (RID) modulu .NET Core Runtime](../rid-catalog.md)
- [Předávání argumentů runsettings prostřednictvím příkazového řádku](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
