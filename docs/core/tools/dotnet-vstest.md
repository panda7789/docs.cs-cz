---
title: dotnet – příkaz vstest
description: Příkaz dotnet VSTest vytvoří projekt a všechny jeho závislosti.
ms.date: 02/27/2020
ms.openlocfilehash: f7db58f4aab59354b8c69ce0371324c23482dafe
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975391"
---
# <a name="dotnet-vstest"></a>dotnet vstest

**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí

> [!IMPORTANT]
> `dotnet vstest` Příkaz je nahrazen nástrojem `dotnet test`, který lze nyní použít ke spuštění sestavení. Viz [`dotnet test`](dotnet-test.md).

## <a name="name"></a>Name

`dotnet-vstest`-Spustí testy ze zadaných sestavení.

## <a name="synopsis"></a>Stručný obsah

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

`dotnet-vstest` Příkaz spustí aplikaci `VSTest.Console` příkazového řádku pro spuštění automatizovaných testů jednotek.

## <a name="arguments"></a>Arguments

- **`TEST_FILE_NAMES`**

  Spustí testy ze zadaných sestavení. Rozdělte více názvů testovacích sestavení s mezerami. Jsou podporovány zástupné znaky.

## <a name="options"></a>Možnosti

- **`--Blame`**

  Spustí testy v režimu viny. Tato možnost je užitečná při izolaci problematických testů, které způsobují selhání hostitele testu. Vytvoří výstupní soubor v aktuálním adresáři jako *Sequence. XML* , který zachycuje pořadí spuštění testů před selháním.

- **`--Diag <PATH_TO_LOG_FILE>`**

  Povolí podrobné protokoly pro testovací platformu. Protokoly se zapisují do poskytnutého souboru.

- **`--Framework <FRAMEWORK>`**

  Cílová verze .NET Framework používaná pro spuštění testu. Příklady platných hodnot jsou `.NETFramework,Version=v4.6` nebo. `.NETCoreApp,Version=v1.0` Další podporované hodnoty jsou `Framework40`, `Framework45`, `FrameworkCore10`a `FrameworkUap10`.

- **`--InIsolation`**

  Spustí testy v izolovaném procesu. Díky tomu je proces *VSTest. Console. exe* méně pravděpodobný při chybě v testech zastavit, ale testy mohou běžet pomaleji.

- **`-lt|--ListTests <FILE_NAME>`**

  Zobrazí všechny zjištěné testy z daného kontejneru testů.

- **`--logger <LOGGER_URI/FRIENDLY_NAME>`**

  Zadejte protokolovací nástroj pro výsledky testů.

  - K publikování výsledků testů do Team Foundation Server použijte zprostředkovatele `TfsPublisher` protokolovacího nástroje:

    ```console
    /logger:TfsPublisher;
        Collection=<team project collection url>;
        BuildName=<build name>;
        TeamProject=<team project name>
        [;Platform=<Defaults to "Any CPU">]
        [;Flavor=<Defaults to "Debug">]
        [;RunTitle=<title>]
    ```

  - K protokolování výsledků do souboru sady Visual Studio Výsledky testů (TRX) použijte poskytovatele `trx` protokolovacího nástroje. Tento přepínač vytvoří soubor v adresáři výsledků testu s daným názvem souboru protokolu. Pokud `LogFileName` není zadaný, vytvoří se jedinečný název souboru, který bude obsahovat výsledky testu.

    ```console
    /logger:trx [;LogFileName=<Defaults to unique file name>]
    ```

- **`--Parallel`**

  Paralelně spouštějte testy. Ve výchozím nastavení jsou všechny dostupné jádra počítače k dispozici pro použití. Určete explicitní počet jader nastavením `MaxCpuCount` vlastnosti pod `RunConfiguration` uzlem v souboru *runsettings* .

- **`--ParentProcessId <PROCESS_ID>`**

  ID procesu nadřazeného procesu zodpovědného za spuštění aktuálního procesu.

- **`--Platform <PLATFORM_TYPE>`**

  Cílová architektura platformy použitá pro spuštění testu. Platné hodnoty jsou `x86`, `x64`a `ARM`.

- **`--Port <PORT>`**

  Určuje port pro připojení soketu a příjem zpráv událostí.

- **`--ResultsDirectory:<PATH>`**

  Adresář výsledků testů bude vytvořen v zadané cestě, pokud neexistuje.

- **`--Settings <SETTINGS_FILE>`**

  Nastavení, které se má použít při spouštění testů.

- **`--TestAdapterPath <PATH>`**

  Použijte vlastní testovací adaptéry z dané cesty (pokud existuje) v testovacím běhu.

- **`--TestCaseFilter <EXPRESSION>`**

  Spustí testy, které odpovídají danému výrazu. `<EXPRESSION>`má formát `<property>Operator<value>[|&<EXPRESSION>]`, kde operátor je jedna z `=`, `!=`nebo. `~` Operátor `~` obsahuje sémantiku Contains a je použitelný pro řetězcové vlastnosti, jako `DisplayName`je. K seskupení `()` podvýrazů se používají kulaté závorky. Další informace najdete v tématu [testovací případ Filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).

- **`--Tests <TEST_NAMES>`**

  Spustí testy s názvy, které odpovídají zadaným hodnotám. Více hodnot oddělte čárkami.

- **`-?|--Help`**

  Vypíše krátkou nápovědu k příkazu.

- **`@<file>`**

  Přečte soubor odpovědí pro další možnosti.

- **`args`**

  Určuje nadbytečné argumenty, které se mají předat adaptéru. Argumenty jsou zadány jako páry název-hodnota ve formátu `<n>=<v>`, kde `<n>` je název argumentu a `<v>` je hodnota argumentu. K oddělení více argumentů použijte mezeru.

## <a name="examples"></a>Příklady

Spustit testy v *knihovně mytestproject. dll*:

```dotnetcli
dotnet vstest mytestproject.dll
```

Spusťte testy v souboru *mytestproject. dll*a exportujte je do vlastní složky s vlastním názvem:

```dotnetcli
dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path
```

Spustit testy v *mytestproject. dll* a *myothertestproject. exe*:

```dotnetcli
dotnet vstest mytestproject.dll myothertestproject.exe
```

Spustit `TestMethod1` testy:

```dotnetcli
dotnet vstest /Tests:TestMethod1
```

Běh `TestMethod1` a `TestMethod2` testy:

```dotnetcli
dotnet vstest /Tests:TestMethod1,TestMethod2
```

## <a name="see-also"></a>Viz také

- [VSTest.Console.exe – možnosti příkazového řádku](/visualstudio/test/vstest-console-options)
