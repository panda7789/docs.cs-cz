---
title: dotnet vstest, příkaz
description: Dotnet vstest příkaz vytvoří projekt a všechny jeho závislosti.
ms.date: 02/27/2020
ms.openlocfilehash: e8fa94cf12ca2fe5fb99c6e3c1dcdb52185798c0
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463289"
---
# <a name="dotnet-vstest"></a>dotnet vstest

**Tento článek se týká:** ✔️ .NET Core 2.1 SDK a novější verze

## <a name="name"></a>Název

`dotnet-vstest`- Spustí testy ze zadaných souborů.

## <a name="synopsis"></a>Synopse

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Blame] [--Diag <PATH_TO_LOG_FILE>]
    [--Framework <FRAMEWORK>] [--InIsolation] [-lt|--ListTests <FILE_NAME>]
    [--logger <LOGGER_URI/FRIENDLY_NAME>] [--Parallel]
    [--ParentProcessId <PROCESS_ID>] [--Platform] <PLATFORM_TYPE>
    [--Port <PORT>] [--ResultsDirectory<PATH>] [--Settings <SETTINGS_FILE>]
    [--TestAdapterPath <PATH>] [--TestCaseFilter <EXPRESSION>]
    [--Tests <TEST_NAMES>] [[--] <args>...]]

dotnet vstest -?|--Help
```

## <a name="description"></a>Popis

Příkaz `dotnet-vstest` spustí `VSTest.Console` aplikaci příkazového řádku pro spuštění automatizovaných testů částí.

## <a name="arguments"></a>Argumenty

- **`TEST_FILE_NAMES`**

  Spusťte testy ze zadaných sestavení. Oddělte více názvů testovacích sestavení mezerami. Zástupné znaky jsou podporovány.

## <a name="options"></a>Možnosti

- **`--Blame`**

  Spustí testy v režimu obviňování. Tato možnost je užitečná při izolaci problémových testů, které způsobují selhání testovacího hostitele. Vytvoří výstupní soubor v aktuálním adresáři jako *Sequence.xml,* který zachycuje pořadí spuštění testů před selháním.

- **`--Diag <PATH_TO_LOG_FILE>`**

  Povolí podrobné protokoly pro testovací platformu. Protokoly jsou zapsány do dodaný soubor.

- **`--Framework <FRAMEWORK>`**

  Cílová verze rozhraní .NET Framework použitá pro spuštění testu. Příklady platných `.NETFramework,Version=v4.6` hodnot `.NETCoreApp,Version=v1.0`jsou nebo . Další podporované `Framework40`hodnoty `Framework45` `FrameworkCore10`jsou `FrameworkUap10`, , a .

- **`--InIsolation`**

  Spustí testy v izolovaném procesu. Díky *vstest.console.exe* proces méně pravděpodobné, že bude zastaven a na chybu v testech, ale testy mohou běžet pomaleji.

- **`-lt|--ListTests <FILE_NAME>`**

  Zobrazí seznam všech zjištěných testů z daného testovacího kontejneru.

- **`--logger <LOGGER_URI/FRIENDLY_NAME>`**

  Zadejte protokolovací nástroj pro výsledky testů.

  - Chcete-li publikovat výsledky testů na `TfsPublisher` serveru Team Foundation, použijte zprostředkovatele protokolování:

    ```console
    /logger:TfsPublisher;
        Collection=<team project collection url>;
        BuildName=<build name>;
        TeamProject=<team project name>
        [;Platform=<Defaults to "Any CPU">]
        [;Flavor=<Defaults to "Debug">]
        [;RunTitle=<title>]
    ```

  - Chcete-li protokolovat výsledky souboru výsledků testů `trx` sady Visual Studio (TRX), použijte zprostředkovatele protokolování. Tento přepínač vytvoří soubor v adresáři výsledků testu s daným názvem souboru protokolu. Pokud `LogFileName` není k dispozici, jedinečný název souboru je vytvořen pro uložení výsledků testu.

    ```console
    /logger:trx [;LogFileName=<Defaults to unique file name>]
    ```

- **`--Parallel`**

  Spouštět testy paralelně. Ve výchozím nastavení jsou k dispozici všechna dostupná jádra v počítači. Zadejte explicitní počet jader `MaxCpuCount` nastavením `RunConfiguration` vlastnosti pod uzlevě v souboru *runsettings.*

- **`--ParentProcessId <PROCESS_ID>`**

  ID procesu nadřazeného procesu odpovědného za spuštění aktuálního procesu.

- **`--Platform <PLATFORM_TYPE>`**

  Architektura cílové platformy používaná pro spuštění testu. Platné hodnoty `x86` `x64`jsou `ARM`, a .

- **`--Port <PORT>`**

  Určuje port pro připojení soketu a příjem zpráv o událostech.

- **`--ResultsDirectory:<PATH>`**

  Pokud neexistuje, bude adresář výsledků testu vytvořen v zadané cestě.

- **`--Settings <SETTINGS_FILE>`**

  Nastavení, které se má použít při spuštění testů.

- **`--TestAdapterPath <PATH>`**

  Při testovacím běhu použijte vlastní testovací adaptéry z dané cesty (pokud existuje).

- **`--TestCaseFilter <EXPRESSION>`**

  Spusťte testy, které odpovídají danému výrazu. `<EXPRESSION>`je ve `<property>Operator<value>[|&<EXPRESSION>]`formátu , kde `=`Operator `!=`je `~`jedním z , , nebo . Operátor `~` má sémantiku "obsahuje" a `DisplayName`je použitelný pro vlastnosti řetězce, jako je . Závorky `()` se používají k seskupení podvýrazů. Další informace naleznete v tématu [TestCase filtr](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).

- **`--Tests <TEST_NAMES>`**

  Spusťte testy s názvy, které odpovídají zadaným hodnotám. Oddělte více hodnot čárkou.

- **`-?|--Help`**

  Vytiskne krátkou nápovědu pro příkaz.

- **`@<file>`**

  Přečte soubor odpovědí pro další možnosti.

- **`args`**

  Určuje další argumenty, které mají být předávány adaptéru. Argumenty jsou určeny jako dvojice název-hodnota formuláře `<n>=<v>`, kde `<n>` je název argumentu a `<v>` je hodnota argumentu. Použijte mezeru k oddělení více argumentů.

## <a name="examples"></a>Příklady

Spustit testy v *mytestproject.dll*:

```dotnetcli
dotnet vstest mytestproject.dll
```

Spusťte testy v souboru *mytestproject.dll*, exportujte do vlastní složky s vlastním názvem:

```dotnetcli
dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path
```

Spusťte testy v *mytestproject.dll* a *myothertestproject.exe*:

```dotnetcli
dotnet vstest mytestproject.dll myothertestproject.exe
```

Spustit `TestMethod1` testy:

```dotnetcli
dotnet vstest /Tests:TestMethod1
```

Běh `TestMethod1` `TestMethod2` a testy:

```dotnetcli
dotnet vstest /Tests:TestMethod1,TestMethod2
```

## <a name="see-also"></a>Viz také

- [VSTest.Console.exe – možnosti příkazového řádku](/visualstudio/test/vstest-console-options)
