---
title: dotnet – příkaz vstest
description: Příkaz dotnet VSTest vytvoří projekt a všechny jeho závislosti.
author: mairaw
ms.date: 05/30/2018
ms.openlocfilehash: ffe3807be2c35fb4d6b46b83ed84200433f551d8
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117515"
---
# <a name="dotnet-vstest"></a>dotnet vstest

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Name

`dotnet-vstest`– Spustí testy ze zadaných souborů.

## <a name="synopsis"></a>Stručný obsah

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [--Blame|/Blame] [--InIsolation|/InIsolation]
    [[--] <args>...]] [-?|--Help|/?|/Help]
```

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2,0](#tab/netcore20)

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] 
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] 
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```

---

## <a name="description"></a>Popis

`dotnet-vstest` Příkaz`VSTest.Console` spustí aplikaci příkazového řádku pro spuštění automatizovaných testů jednotek.

## <a name="arguments"></a>Arguments

`TEST_FILE_NAMES`

Spustí testy ze zadaných sestavení. Rozdělte více názvů testovacích sestavení s mezerami.

## <a name="options"></a>Možnosti

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

`--Settings|/Settings:<Settings File>`

Nastavení, které se má použít při spouštění testů.

`--Tests|/Tests:<Test Names>`

Spustí testy s názvy, které odpovídají zadaným hodnotám. Více hodnot oddělte čárkami.

`--TestAdapterPath|/TestAdapterPath`

Použijte vlastní testovací adaptéry z dané cesty (pokud existuje) v testovacím běhu.

`--Platform|/Platform:<Platform type>`

Cílová architektura platformy použitá pro spuštění testu. Platné hodnoty jsou `x86`, `x64`, a `ARM`.

`--Framework|/Framework:<Framework Version>`

Cílová verze .NET Framework používaná pro spuštění testu. Příklady platných hodnot jsou `.NETFramework,Version=v4.6` nebo. `.NETCoreApp,Version=v1.0` Další podporované hodnoty jsou `Framework40`, `Framework45`, `FrameworkCore10`a `FrameworkUap10`.

`--Parallel|/Parallel`

Paralelní provádění testů. Ve výchozím nastavení jsou všechny dostupné jádra počítače k dispozici pro použití. Určete explicitní počet jader nastavením vlastnosti MaxCpuCount v uzlu RunConfiguration v souboru runsettings.

`--TestCaseFilter|/TestCaseFilter:<Expression>`

Spustí testy, které odpovídají danému výrazu. `<Expression>`má formát `<property>Operator<value>[|&<Expression>]`, kde operátor je jedna z `=`, `!=`nebo `~`. Operátor `~` obsahuje sémantiku Contains a je použitelný pro řetězcové vlastnosti, jako `DisplayName`je. K seskupení dílčích výrazů sepoužívajízávorky.`()`

`-?|--Help|/?|/Help`

Vypíše krátkou nápovědu k příkazu.

`--logger|/logger:<Logger Uri/FriendlyName>`

Zadejte protokolovací nástroj pro výsledky testů.

* K publikování výsledků testů do Team Foundation Server použijte `TfsPublisher` zprostředkovatele protokolovacího nástroje:

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* K protokolování výsledků do souboru sady Visual Studio výsledky testů (TRX) použijte `trx` poskytovatele protokolovacího nástroje. Tento přepínač vytvoří soubor v adresáři výsledků testu s daným názvem souboru protokolu. Pokud `LogFileName` není zadaný, vytvoří se jedinečný název souboru, který bude obsahovat výsledky testu.

  ```console
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

Zobrazí všechny zjištěné testy z daného kontejneru testů.

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

ID procesu nadřazeného procesu zodpovědného za spuštění aktuálního procesu.

`--Port|/Port:<Port>`

Určuje port pro připojení soketu a příjem zpráv událostí.

`--Diag|/Diag:<Path to log file>`

Povolí podrobné protokoly pro testovací platformu. Protokoly se zapisují do poskytnutého souboru.

`--Blame|/Blame`

Spustí testy v režimu viny. Tato možnost je užitečná při izolaci problematických testů, které způsobují selhání hostitele testu. Vytvoří výstupní soubor v aktuálním adresáři jako *Sequence. XML* , který zachycuje pořadí spuštění testů před selháním.

`--InIsolation|/InIsolation`

Spustí testy v izolovaném procesu. Díky tomu je proces *VSTest. Console. exe* méně pravděpodobný při chybě v testech zastavit, ale testy mohou běžet pomaleji.

`@<file>`

Přečte soubor odpovědí pro další možnosti.

`args`

Určuje nadbytečné argumenty, které se mají předat adaptéru. Argumenty jsou zadány jako páry název-hodnota ve formátu `<n>=<v>`, kde `<n>` je název argumentu a `<v>` je hodnota argumentu. K oddělení více argumentů použijte mezeru.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2,0](#tab/netcore20)

`--Settings|/Settings:<Settings File>`

Nastavení, které se má použít při spouštění testů.

`--Tests|/Tests:<Test Names>`

Spustí testy s názvy, které odpovídají zadaným hodnotám. Více hodnot oddělte čárkami.

`--TestAdapterPath|/TestAdapterPath`

Použijte vlastní testovací adaptéry z dané cesty (pokud existuje) v testovacím běhu.

`--Platform|/Platform:<Platform type>`

Cílová architektura platformy použitá pro spuštění testu. Platné hodnoty jsou `x86`, `x64`, a `ARM`.

`--Framework|/Framework:<Framework Version>`

Cílová verze .NET Framework používaná pro spuštění testu. Příklady platných hodnot jsou `.NETFramework,Version=v4.6` nebo. `.NETCoreApp,Version=v1.0` Další podporované hodnoty jsou `Framework40`, `Framework45`a `FrameworkCore10`.

`--Parallel|/Parallel`

Paralelní provádění testů. Ve výchozím nastavení jsou všechny dostupné jádra počítače k dispozici pro použití. Určete explicitní počet jader nastavením vlastnosti MaxCpuCount v uzlu RunConfiguration v souboru runsettings.

`--TestCaseFilter|/TestCaseFilter:<Expression>`

Spustí testy, které odpovídají danému výrazu. `<Expression>`má formát `<property>Operator<value>[|&<Expression>]`, kde operátor je jedna z `=`, `!=`nebo `~`. Operátor `~` obsahuje sémantiku Contains a je použitelný pro řetězcové vlastnosti, jako `DisplayName`je. K seskupení dílčích výrazů sepoužívajízávorky.`()`

`-?|--Help|/?|/Help`

Vypíše krátkou nápovědu k příkazu.

`--logger|/logger:<Logger Uri/FriendlyName>`

Zadejte protokolovací nástroj pro výsledky testů.

* K publikování výsledků testů do Team Foundation Server použijte `TfsPublisher` zprostředkovatele protokolovacího nástroje:

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* K protokolování výsledků do souboru sady Visual Studio výsledky testů (TRX) použijte `trx` poskytovatele protokolovacího nástroje. Tento přepínač vytvoří soubor v adresáři výsledků testu s daným názvem souboru protokolu. Pokud `LogFileName` není zadaný, vytvoří se jedinečný název souboru, který bude obsahovat výsledky testu.

  ```console
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

Zobrazí všechny zjištěné testy z daného kontejneru testů.

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

ID procesu nadřazeného procesu zodpovědného za spuštění aktuálního procesu.

`--Port|/Port:<Port>`

Určuje port pro připojení soketu a příjem zpráv událostí.

`--Diag|/Diag:<Path to log file>`

Povolí podrobné protokoly pro testovací platformu. Protokoly se zapisují do poskytnutého souboru.

`args`

Určuje nadbytečné argumenty, které se mají předat adaptéru. Argumenty jsou zadány jako páry název-hodnota ve formátu `<n>=<v>`, kde `<n>` je název argumentu a `<v>` je hodnota argumentu. K oddělení více argumentů použijte mezeru.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`--Settings|/Settings:<Settings File>`

Nastavení, které se má použít při spouštění testů.

`--Tests|/Tests:<Test Names>`

Spustí testy s názvy, které odpovídají zadaným hodnotám. Více hodnot oddělte čárkami.

`--TestAdapterPath|/TestAdapterPath`

Použijte vlastní testovací adaptéry z dané cesty (pokud existuje) v testovacím běhu.

`--Platform|/Platform:<Platform type>`

Cílová architektura platformy použitá pro spuštění testu. Platné hodnoty jsou `x86`, `x64`, a `ARM`.

`--Framework|/Framework:<Framework Version>`

Cílová verze .NET Framework používaná pro spuštění testu. Příklady platných hodnot jsou `.NETFramework,Version=v4.6` nebo. `.NETCoreApp,Version=v1.0` Další podporované hodnoty jsou `Framework40`, `Framework45`a `FrameworkCore10`.

`--Parallel|/Parallel`

Paralelní provádění testů. Ve výchozím nastavení jsou všechny dostupné jádra počítače k dispozici pro použití. Určete explicitní počet jader nastavením vlastnosti MaxCpuCount v uzlu RunConfiguration v souboru runsettings.

`--TestCaseFilter|/TestCaseFilter:<Expression>`

Spustí testy, které odpovídají danému výrazu. `<Expression>`má formát `<property>Operator<value>[|&<Expression>]`, kde operátor je jedna z `=`, `!=`nebo `~`. Operátor `~` obsahuje sémantiku Contains a je použitelný pro řetězcové vlastnosti, jako `DisplayName`je. K seskupení dílčích výrazů sepoužívajízávorky.`()`

`-?|--Help|/?|/Help`

Vypíše krátkou nápovědu k příkazu.

`--logger|/logger:<Logger Uri/FriendlyName>`

Zadejte protokolovací nástroj pro výsledky testů.

* K publikování výsledků testů do Team Foundation Server použijte `TfsPublisher` zprostředkovatele protokolovacího nástroje:

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* K protokolování výsledků do souboru sady Visual Studio výsledky testů (TRX) použijte `trx` poskytovatele protokolovacího nástroje. Tento přepínač vytvoří soubor v adresáři výsledků testu s daným názvem souboru protokolu. Pokud `LogFileName` není zadaný, vytvoří se jedinečný název souboru, který bude obsahovat výsledky testu.

  ```console
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

Zobrazí všechny zjištěné testy z daného kontejneru testů.

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

ID procesu nadřazeného procesu zodpovědného za spuštění aktuálního procesu.

`--Port|/Port:<Port>`

Určuje port pro připojení soketu a příjem zpráv událostí.

`--Diag|/Diag:<Path to log file>`

Povolí podrobné protokoly pro testovací platformu. Protokoly se zapisují do poskytnutého souboru.

`args`

Určuje nadbytečné argumenty, které se mají předat adaptéru. Argumenty jsou zadány jako páry název-hodnota ve formátu `<n>=<v>`, kde `<n>` je název argumentu a `<v>` je hodnota argumentu. K oddělení více argumentů použijte mezeru.

---

## <a name="examples"></a>Příklady

Spustit testy v `mytestproject.dll`:

`dotnet vstest mytestproject.dll`

Spustit testy v `mytestproject.dll`nástroji, exportovat do vlastní složky s vlastním názvem:

`dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path`

Spustit testy v `mytestproject.dll` a `myothertestproject.exe`:

`dotnet vstest mytestproject.dll myothertestproject.exe`

Spustit `TestMethod1` testy:

`dotnet vstest /Tests:TestMethod1`

Běh `TestMethod1` a`TestMethod2` testy:

`dotnet vstest /Tests:TestMethod1,TestMethod2`
