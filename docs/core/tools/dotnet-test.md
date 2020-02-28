---
title: dotnet – příkaz testu
description: Příkaz dotnet test se používá ke spouštění testů jednotek v daném projektu.
ms.date: 02/27/2020
ms.openlocfilehash: 6e906ab396a788905c99f50e73390b765b240efc
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157008"
---
# <a name="dotnet-test"></a>dotnet test

**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí

## <a name="name"></a>Název

ovladač testu `dotnet test`-.NET použitý ke spuštění testů jednotek

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame]
    [-c|--configuration] [--collect] [-d|--diag] [-f|--framework]
    [--filter] [-l|--logger] [--no-build] [--no-restore]
    [-o|--output] [-r|--results-directory] [-s|--settings]
    [-t|--list-tests] [-v|--verbosity] [-- <RunSettings arguments>]

dotnet test [-h|--help]
```

## <a name="description"></a>Popis

Příkaz `dotnet test` slouží ke spuštění testů jednotek v daném projektu. Příkaz `dotnet test` spustí konzolovou aplikaci Test Runner určenou pro projekt. Test Runner spustí testy definované pro systém testů jednotek (například MSTest, NUnit nebo xUnit) a ohlásí úspěch nebo neúspěch každého testu. Pokud jsou všechny testy úspěšné, Test Runner vrátí 0 jako ukončovací kód; jinak, pokud nějaký test selže, vrátí 1. Test Runner a knihovna testů jednotek jsou zabaleny jako balíčky NuGet a jsou obnoveny jako běžné závislosti pro projekt.

Projekty testů určují Test Runner pomocí obyčejného prvku `<PackageReference>`, jak je vidět v následujícím ukázkovém souboru projektu:

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a>Argumenty

- **`PROJECT`**

  Cesta k testovacímu projektu. Pokud není zadaný, použije se ve výchozím nastavení aktuální adresář.

## <a name="options"></a>Možnosti

- **`a|--test-adapter-path <PATH_TO_ADAPTER>`**

  Použijte vlastní testovací adaptéry ze zadané cesty v testovacím běhu.

- **`-blame`**

  Spustí testy v režimu viny. Tato možnost je užitečná při izolaci problematických testů, které způsobují selhání hostitele testu. Vytvoří výstupní soubor v aktuálním adresáři jako *Sequence. XML* , který zachycuje pořadí spuštění testů před selháním.

- **`c|--configuration {Debug|Release}`**

  Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`, ale konfigurace vašeho projektu může přepsat toto výchozí nastavení sady SDK.

- **`-collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  Povolí shromažďování dat pro testovací běh. Další informace najdete v tématu [monitorování a analýza testovacího běhu](https://aka.ms/vstest-collect).

- **`d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  Povolí diagnostický režim pro testovací platformu a zapíše diagnostické zprávy do zadaného souboru.

- **`f|--framework <FRAMEWORK>`**

  Vyhledá testovací binární soubory pro konkrétní [rozhraní](../../standard/frameworks.md).

- **`--filter <EXPRESSION>`**

  Odfiltruje testy v aktuálním projektu pomocí daného výrazu. Další informace najdete v části [Podrobnosti o možnosti filtru](#filter-option-details) . Další informace a příklady použití selektivního filtrování testů jednotek naleznete v tématu [spuštění selektivních testů jednotek](../testing/selective-unit-tests.md).

- **`h|--help`**

  Vypíše krátkou nápovědu k příkazu.

- **`l|--logger <LoggerUri/FriendlyName>`**

  Určuje protokolovací nástroj pro výsledky testů.

- **`--no-build`**

  Před spuštěním nevytvoří testovací projekt. Také implicitně nastaví příznak-`--no-restore`.

- **`--no-restore`**

  Při spuštění příkazu neprovede implicitní obnovení.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Adresář, ve kterém se mají najít binární soubory, které se mají spustit.

- **`-r|--results-directory <PATH>`**

  Adresář, do kterého budou umístěny výsledky testů. Pokud zadaný adresář neexistuje, vytvoří se.

- **`-s|--settings <SETTINGS_FILE>`**

  Soubor `.runsettings`, který se má použít pro spuštění testů. [Nakonfigurujte testy jednotek pomocí `.runsettings` souboru.](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

- **`-t|--list-tests`**

  Vypíše všechny zjištěné testy v aktuálním projektu.

- **`-v|--verbosity <LEVEL>`**

  Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`.

- argumenty `RunSettings`

  Argumenty jsou předány jako `RunSettings` konfigurace testu. Argumenty jsou zadány jako páry `[name]=[value]` po "--" (Všimněte si mezer za-). K oddělení více párů `[name]=[value]` se používá mezera.

  Příklad: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`

  Další informace naleznete v tématu [VSTest. Console. exe: předávání argumentů runsettings](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).

## <a name="examples"></a>Příklady

- Spustit testy v projektu v aktuálním adresáři:

  ```dotnetcli
  dotnet test
  ```

- Spusťte testy v projektu `test1`:

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- Spusťte testy v projektu v aktuálním adresáři a vygenerujte soubor výsledků testů ve formátu TRX:

  ```dotnetcli
  dotnet test --logger trx
  ```

## <a name="filter-option-details"></a>Podrobnosti možnosti filtru

`--filter <EXPRESSION>`

`<Expression>` má `<property><operator><value>[|&<Expression>]`formátu.

`<property>` je atribut `Test Case`. Níže jsou uvedené vlastnosti podporované oblíbenými rozhraními pro testování částí:

| Rozhraní pro testování | Podporované vlastnosti                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| MSTest         | <ul><li>FullyQualifiedName</li><li>Název</li><li>NázevTřídy</li><li>Priorita</li><li>TestCategory</li></ul> |
| xUnit          | <ul><li>FullyQualifiedName</li><li>DisplayName</li><li>Traits</li></ul>                                   |

`<operator>` popisuje vztah mezi vlastností a hodnotou:

| Operátor | Funkce        |
| :------: | --------------- |
| `=`      | Přesná shoda     |
| `!=`     | Nepřesná shoda |
| `~`      | Contains        |
| `!~`     | Neobsahuje    |

`<value>` je řetězec. U všech hledání se nerozlišují malá a velká písmena.

Výraz bez `<operator>` je automaticky považován za `contains` při `FullyQualifiedName` vlastnosti (například `dotnet test --filter xyz` je stejný jako `dotnet test --filter FullyQualifiedName~xyz`).

Výrazy se dají spojit s podmíněnými operátory:

| Operátor            | Funkce |
| ------------------- | -------- |
| <code>&#124;</code> | NEBO       |
| `&`                 | A      |

Výrazy můžete uzavřít do závorek při použití podmíněných operátorů (například `(Name~TestMethod1) | (Name~TestMethod2)`).

Další informace a příklady použití selektivního filtrování testů jednotek naleznete v tématu [spuštění selektivních testů jednotek](../testing/selective-unit-tests.md).

## <a name="see-also"></a>Viz také

- [Architektury a cíle](../../standard/frameworks.md)
- [Katalog identifikátorů runtime .NET Core (RID)](../rid-catalog.md)
