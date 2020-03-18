---
title: dotnet vstest, příkaz
description: Dotnet vstest příkaz vytvoří projekt a všechny jeho závislosti.
ms.date: 02/27/2020
ms.openlocfilehash: 88e5b6a8966d78d0746f9ea5ccbccab142a2e0f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156930"
---
# <a name="dotnet-vstest"></a>dotnet vstest

**Tento článek se týká:** ✔️ .NET Core 2.1 SDK a novější verze

## <a name="name"></a>Name (Název)

`dotnet-vstest`- Spustí testy ze zadaných souborů.

## <a name="synopsis"></a>Synopse

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings] [--Tests]
    [--TestAdapterPath] [--Platform] [--Framework] [--Parallel]
    [--TestCaseFilter] [--logger] [-lt|--ListTests]
    [--ParentProcessId] [--Port] [--Diag] [--Blame]
    [--InIsolation] [[--] <args>...]] [-?|--Help]
```

## <a name="description"></a>Popis

Příkaz `dotnet-vstest` spustí `VSTest.Console` aplikaci příkazového řádku pro spuštění automatizovaných testů částí.

## <a name="arguments"></a>Argumenty

- **`TEST_FILE_NAMES`**

  Spusťte testy ze zadaných sestavení. Oddělte více názvů testovacích sestavení mezerami. Zástupné znaky jsou podporovány.

## <a name="options"></a>Možnosti

- **`--Settings <Settings File>`**

  Nastavení, které se má použít při spuštění testů.

- **`--Tests <Test Names>`**

  Spusťte testy s názvy, které odpovídají zadaným hodnotám. Oddělte více hodnot čárkou.

- **`--TestAdapterPath`**

  Při testovacím běhu použijte vlastní testovací adaptéry z dané cesty (pokud existuje).

- **`--Platform <Platform type>`**

  Architektura cílové platformy používaná pro spuštění testu. Platné hodnoty `x86` `x64`jsou `ARM`, a .

- **`--Framework <Framework Version>`**

  Cílová verze rozhraní .NET Framework použitá pro spuštění testu. Příklady platných `.NETFramework,Version=v4.6` hodnot `.NETCoreApp,Version=v1.0`jsou nebo . Další podporované `Framework40`hodnoty `Framework45` `FrameworkCore10`jsou `FrameworkUap10`, , a .

- **`--Parallel`**

  Spouštět testy paralelně. Ve výchozím nastavení jsou k dispozici všechna dostupná jádra v počítači. Zadejte explicitní počet jader `MaxCpuCount` nastavením `RunConfiguration` vlastnosti pod uzlevě v souboru *runsettings.*

- **`--TestCaseFilter <Expression>`**

  Spusťte testy, které odpovídají danému výrazu. `<Expression>`je ve `<property>Operator<value>[|&<Expression>]`formátu , kde `=`Operator `!=`je `~`jedním z , , nebo . Operátor `~` má sémantiku "obsahuje" a `DisplayName`je použitelný pro vlastnosti řetězce, jako je . Závorky `()` se používají k seskupení podvýrazů.

- **`-?|--Help`**

  Vytiskne krátkou nápovědu pro příkaz.

- **`--logger <Logger Uri/FriendlyName>`**

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

- **`-lt|--ListTests <File Name>`**

  Zobrazí seznam všech zjištěných testů z daného testovacího kontejneru.

- **`--ParentProcessId <ParentProcessId>`**

  ID procesu nadřazeného procesu odpovědného za spuštění aktuálního procesu.

- **`--Port <Port>`**

  Určuje port pro připojení soketu a příjem zpráv o událostech.

- **`--Diag <Path to log file>`**

  Povolí podrobné protokoly pro testovací platformu. Protokoly jsou zapsány do dodaný soubor.

- **`--Blame`**

  Spustí testy v režimu obviňování. Tato možnost je užitečná při izolaci problémových testů, které způsobují selhání testovacího hostitele. Vytvoří výstupní soubor v aktuálním adresáři jako *Sequence.xml,* který zachycuje pořadí spuštění testů před selháním.

- **`--InIsolation`**

  Spustí testy v izolovaném procesu. Díky *vstest.console.exe* proces méně pravděpodobné, že bude zastaven a na chybu v testech, ale testy mohou běžet pomaleji.

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
