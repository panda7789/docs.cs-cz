---
title: dotnet – příkaz vstest
description: Příkaz dotnet VSTest vytvoří projekt a všechny jeho závislosti.
ms.date: 02/27/2020
ms.openlocfilehash: 88e5b6a8966d78d0746f9ea5ccbccab142a2e0f6
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156930"
---
# <a name="dotnet-vstest"></a>dotnet vstest

**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí

## <a name="name"></a>Název

`dotnet-vstest` – spustí testy ze zadaných souborů.

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings] [--Tests]
    [--TestAdapterPath] [--Platform] [--Framework] [--Parallel]
    [--TestCaseFilter] [--logger] [-lt|--ListTests]
    [--ParentProcessId] [--Port] [--Diag] [--Blame]
    [--InIsolation] [[--] <args>...]] [-?|--Help]
```

## <a name="description"></a>Popis

Příkaz `dotnet-vstest` spustí aplikaci `VSTest.Console` příkazového řádku, aby se spouštěly automatizované testy jednotek.

## <a name="arguments"></a>Argumenty

- **`TEST_FILE_NAMES`**

  Spustí testy ze zadaných sestavení. Rozdělte více názvů testovacích sestavení s mezerami. Jsou podporovány zástupné znaky.

## <a name="options"></a>Možnosti

- **`--Settings <Settings File>`**

  Nastavení, které se má použít při spouštění testů.

- **`--Tests <Test Names>`**

  Spustí testy s názvy, které odpovídají zadaným hodnotám. Více hodnot oddělte čárkami.

- **`--TestAdapterPath`**

  Použijte vlastní testovací adaptéry z dané cesty (pokud existuje) v testovacím běhu.

- **`--Platform <Platform type>`**

  Cílová architektura platformy použitá pro spuštění testu. Platné hodnoty jsou `x86`, `x64`a `ARM`.

- **`--Framework <Framework Version>`**

  Cílová verze .NET Framework používaná pro spuštění testu. Příklady platných hodnot jsou `.NETFramework,Version=v4.6` nebo `.NETCoreApp,Version=v1.0`. Další podporované hodnoty jsou `Framework40`, `Framework45`, `FrameworkCore10`a `FrameworkUap10`.

- **`--Parallel`**

  Paralelně spouštějte testy. Ve výchozím nastavení jsou všechny dostupné jádra počítače k dispozici pro použití. Určete explicitní počet jader nastavením vlastnosti `MaxCpuCount` pod uzlem `RunConfiguration` v souboru *runsettings* .

- **`--TestCaseFilter <Expression>`**

  Spustí testy, které odpovídají danému výrazu. `<Expression>` je `<property>Operator<value>[|&<Expression>]`formátu, kde operátor je jedním z `=`, `!=`nebo `~`. Operátor `~` obsahuje sémantiku Contains a je použitelný pro řetězcové vlastnosti, jako je `DisplayName`. `()` závorky se používají k seskupení podvýrazů.

- **`-?|--Help`**

  Vypíše krátkou nápovědu k příkazu.

- **`--logger <Logger Uri/FriendlyName>`**

  Zadejte protokolovací nástroj pro výsledky testů.

  - K publikování výsledků testů do Team Foundation Server použijte poskytovatele protokolovacího nástroje `TfsPublisher`:

    ```console
    /logger:TfsPublisher;
        Collection=<team project collection url>;
        BuildName=<build name>;
        TeamProject=<team project name>
        [;Platform=<Defaults to "Any CPU">]
        [;Flavor=<Defaults to "Debug">]
        [;RunTitle=<title>]
    ```

  - Chcete-li protokolovat výsledky do souboru sady Visual Studio Výsledky testů (TRX), použijte poskytovatele protokolovacího nástroje `trx`. Tento přepínač vytvoří soubor v adresáři výsledků testu s daným názvem souboru protokolu. Pokud `LogFileName` není k dispozici, vytvoří se jedinečný název souboru, který bude obsahovat výsledky testu.

    ```console
    /logger:trx [;LogFileName=<Defaults to unique file name>]
    ```

- **`-lt|--ListTests <File Name>`**

  Zobrazí všechny zjištěné testy z daného kontejneru testů.

- **`--ParentProcessId <ParentProcessId>`**

  ID procesu nadřazeného procesu zodpovědného za spuštění aktuálního procesu.

- **`--Port <Port>`**

  Určuje port pro připojení soketu a příjem zpráv událostí.

- **`--Diag <Path to log file>`**

  Povolí podrobné protokoly pro testovací platformu. Protokoly se zapisují do poskytnutého souboru.

- **`--Blame`**

  Spustí testy v režimu viny. Tato možnost je užitečná při izolaci problematických testů, které způsobují selhání hostitele testu. Vytvoří výstupní soubor v aktuálním adresáři jako *Sequence. XML* , který zachycuje pořadí spuštění testů před selháním.

- **`--InIsolation`**

  Spustí testy v izolovaném procesu. Díky tomu je proces *VSTest. Console. exe* méně pravděpodobný při chybě v testech zastavit, ale testy mohou běžet pomaleji.

- **`@<file>`**

  Přečte soubor odpovědí pro další možnosti.

- **`args`**

  Určuje nadbytečné argumenty, které se mají předat adaptéru. Argumenty jsou zadány jako páry název-hodnota `<n>=<v>`formuláře, kde `<n>` je název argumentu a `<v>` je hodnota argumentu. K oddělení více argumentů použijte mezeru.

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

Spustit `TestMethod1` a `TestMethod2` testy:

```dotnetcli
dotnet vstest /Tests:TestMethod1,TestMethod2
```
