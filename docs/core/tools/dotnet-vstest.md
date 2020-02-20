---
title: dotnet – příkaz vstest
description: Příkaz dotnet VSTest vytvoří projekt a všechny jeho závislosti.
ms.date: 05/30/2018
ms.openlocfilehash: 3fdb5443d6d0cfbe1e7e88bc824cbb930f211260
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451178"
---
# <a name="dotnet-vstest"></a>dotnet vstest

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet-vstest` – spustí testy ze zadaných souborů.

## <a name="synopsis"></a>Stručný obsah

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21"></a>[.NET Core 2,1](#tab/netcore21)

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [--Blame|/Blame] [--InIsolation|/InIsolation]
    [[--] <args>...]] [-?|--Help|/?|/Help]
```

# <a name="net-core-20"></a>[.NET Core 2,0](#tab/netcore20)

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] 
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```

# <a name="net-core-1x"></a>[.NET Core 1. x](#tab/netcore1x)

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] 
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```

---

## <a name="description"></a>Popis

Příkaz `dotnet-vstest` spustí aplikaci `VSTest.Console` příkazového řádku, aby se spouštěly automatizované testy jednotek.

## <a name="arguments"></a>Argumenty

`TEST_FILE_NAMES`

Spustí testy ze zadaných sestavení. Rozdělte více názvů testovacích sestavení s mezerami.

## <a name="options"></a>Možnosti

# <a name="net-core-21"></a>[.NET Core 2,1](#tab/netcore21)

`--Settings|/Settings:<Settings File>`

Nastavení, které se má použít při spouštění testů.

`--Tests|/Tests:<Test Names>`

Spustí testy s názvy, které odpovídají zadaným hodnotám. Více hodnot oddělte čárkami.

`--TestAdapterPath|/TestAdapterPath`

Použijte vlastní testovací adaptéry z dané cesty (pokud existuje) v testovacím běhu.

`--Platform|/Platform:<Platform type>`

Cílová architektura platformy použitá pro spuštění testu. Platné hodnoty jsou `x86`, `x64`a `ARM`.

`--Framework|/Framework:<Framework Version>`

Cílová verze .NET Framework používaná pro spuštění testu. Příklady platných hodnot jsou `.NETFramework,Version=v4.6` nebo `.NETCoreApp,Version=v1.0`. Další podporované hodnoty jsou `Framework40`, `Framework45`, `FrameworkCore10`a `FrameworkUap10`.

`--Parallel|/Parallel`

Paralelní provádění testů. Ve výchozím nastavení jsou všechny dostupné jádra počítače k dispozici pro použití. Určete explicitní počet jader nastavením vlastnosti MaxCpuCount v uzlu RunConfiguration v souboru runsettings.

`--TestCaseFilter|/TestCaseFilter:<Expression>`

Spustí testy, které odpovídají danému výrazu. `<Expression>` je `<property>Operator<value>[|&<Expression>]`formátu, kde operátor je jedním z `=`, `!=`nebo `~`. Operátor `~` obsahuje sémantiku Contains a je použitelný pro řetězcové vlastnosti, jako je `DisplayName`. `()` závorky se používají k seskupení podvýrazů.

`-?|--Help|/?|/Help`

Vypíše krátkou nápovědu k příkazu.

`--logger|/logger:<Logger Uri/FriendlyName>`

Zadejte protokolovací nástroj pro výsledky testů.

* K publikování výsledků testů do Team Foundation Server použijte poskytovatele protokolovacího nástroje `TfsPublisher`:

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* Chcete-li protokolovat výsledky do souboru sady Visual Studio Výsledky testů (TRX), použijte poskytovatele protokolovacího nástroje `trx`. Tento přepínač vytvoří soubor v adresáři výsledků testu s daným názvem souboru protokolu. Pokud `LogFileName` není k dispozici, vytvoří se jedinečný název souboru, který bude obsahovat výsledky testu.

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

Určuje nadbytečné argumenty, které se mají předat adaptéru. Argumenty jsou zadány jako páry název-hodnota `<n>=<v>`formuláře, kde `<n>` je název argumentu a `<v>` je hodnota argumentu. K oddělení více argumentů použijte mezeru.

# <a name="net-core-20"></a>[.NET Core 2,0](#tab/netcore20)

`--Settings|/Settings:<Settings File>`

Nastavení, které se má použít při spouštění testů.

`--Tests|/Tests:<Test Names>`

Spustí testy s názvy, které odpovídají zadaným hodnotám. Více hodnot oddělte čárkami.

`--TestAdapterPath|/TestAdapterPath`

Použijte vlastní testovací adaptéry z dané cesty (pokud existuje) v testovacím běhu.

`--Platform|/Platform:<Platform type>`

Cílová architektura platformy použitá pro spuštění testu. Platné hodnoty jsou `x86`, `x64`a `ARM`.

`--Framework|/Framework:<Framework Version>`

Cílová verze .NET Framework používaná pro spuštění testu. Příklady platných hodnot jsou `.NETFramework,Version=v4.6` nebo `.NETCoreApp,Version=v1.0`. Další podporované hodnoty jsou `Framework40`, `Framework45`a `FrameworkCore10`.

`--Parallel|/Parallel`

Paralelní provádění testů. Ve výchozím nastavení jsou všechny dostupné jádra počítače k dispozici pro použití. Určete explicitní počet jader nastavením vlastnosti MaxCpuCount v uzlu RunConfiguration v souboru runsettings.

`--TestCaseFilter|/TestCaseFilter:<Expression>`

Spustí testy, které odpovídají danému výrazu. `<Expression>` je `<property>Operator<value>[|&<Expression>]`formátu, kde operátor je jedním z `=`, `!=`nebo `~`. Operátor `~` obsahuje sémantiku Contains a je použitelný pro řetězcové vlastnosti, jako je `DisplayName`. `()` závorky se používají k seskupení podvýrazů.

`-?|--Help|/?|/Help`

Vypíše krátkou nápovědu k příkazu.

`--logger|/logger:<Logger Uri/FriendlyName>`

Zadejte protokolovací nástroj pro výsledky testů.

* K publikování výsledků testů do Team Foundation Server použijte poskytovatele protokolovacího nástroje `TfsPublisher`:

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* Chcete-li protokolovat výsledky do souboru sady Visual Studio Výsledky testů (TRX), použijte poskytovatele protokolovacího nástroje `trx`. Tento přepínač vytvoří soubor v adresáři výsledků testu s daným názvem souboru protokolu. Pokud `LogFileName` není k dispozici, vytvoří se jedinečný název souboru, který bude obsahovat výsledky testu.

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

Určuje nadbytečné argumenty, které se mají předat adaptéru. Argumenty jsou zadány jako páry název-hodnota `<n>=<v>`formuláře, kde `<n>` je název argumentu a `<v>` je hodnota argumentu. K oddělení více argumentů použijte mezeru.

# <a name="net-core-1x"></a>[.NET Core 1. x](#tab/netcore1x)

`--Settings|/Settings:<Settings File>`

Nastavení, které se má použít při spouštění testů.

`--Tests|/Tests:<Test Names>`

Spustí testy s názvy, které odpovídají zadaným hodnotám. Více hodnot oddělte čárkami.

`--TestAdapterPath|/TestAdapterPath`

Použijte vlastní testovací adaptéry z dané cesty (pokud existuje) v testovacím běhu.

`--Platform|/Platform:<Platform type>`

Cílová architektura platformy použitá pro spuštění testu. Platné hodnoty jsou `x86`, `x64`a `ARM`.

`--Framework|/Framework:<Framework Version>`

Cílová verze .NET Framework používaná pro spuštění testu. Příklady platných hodnot jsou `.NETFramework,Version=v4.6` nebo `.NETCoreApp,Version=v1.0`. Další podporované hodnoty jsou `Framework40`, `Framework45`a `FrameworkCore10`.

`--Parallel|/Parallel`

Paralelní provádění testů. Ve výchozím nastavení jsou všechny dostupné jádra počítače k dispozici pro použití. Určete explicitní počet jader nastavením vlastnosti MaxCpuCount v uzlu RunConfiguration v souboru runsettings.

`--TestCaseFilter|/TestCaseFilter:<Expression>`

Spustí testy, které odpovídají danému výrazu. `<Expression>` je `<property>Operator<value>[|&<Expression>]`formátu, kde operátor je jedním z `=`, `!=`nebo `~`. Operátor `~` obsahuje sémantiku Contains a je použitelný pro řetězcové vlastnosti, jako je `DisplayName`. `()` závorky se používají k seskupení podvýrazů.

`-?|--Help|/?|/Help`

Vypíše krátkou nápovědu k příkazu.

`--logger|/logger:<Logger Uri/FriendlyName>`

Zadejte protokolovací nástroj pro výsledky testů.

* K publikování výsledků testů do Team Foundation Server použijte poskytovatele protokolovacího nástroje `TfsPublisher`:

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* Chcete-li protokolovat výsledky do souboru sady Visual Studio Výsledky testů (TRX), použijte poskytovatele protokolovacího nástroje `trx`. Tento přepínač vytvoří soubor v adresáři výsledků testu s daným názvem souboru protokolu. Pokud `LogFileName` není k dispozici, vytvoří se jedinečný název souboru, který bude obsahovat výsledky testu.

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

Určuje nadbytečné argumenty, které se mají předat adaptéru. Argumenty jsou zadány jako páry název-hodnota `<n>=<v>`formuláře, kde `<n>` je název argumentu a `<v>` je hodnota argumentu. K oddělení více argumentů použijte mezeru.

---

## <a name="examples"></a>Příklady

Spustit testy v `mytestproject.dll`:

`dotnet vstest mytestproject.dll`

Spustit testy v `mytestproject.dll`, exportovat do vlastní složky s vlastním názvem:

`dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path`

Spustit testy v `mytestproject.dll` a `myothertestproject.exe`:

`dotnet vstest mytestproject.dll myothertestproject.exe`

Spustit `TestMethod1` testy:

`dotnet vstest /Tests:TestMethod1`

Spustit `TestMethod1` a `TestMethod2` testy:

`dotnet vstest /Tests:TestMethod1,TestMethod2`
