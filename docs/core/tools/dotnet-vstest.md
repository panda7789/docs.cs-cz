---
title: příkaz DotNet vstest
description: Příkaz dotnet vstest sestavení projektu a všechny jeho závislosti.
author: guardrex
ms.date: 05/30/2018
ms.openlocfilehash: d41e901f70b4a3d0647c693fdd8076f771466073
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2019
ms.locfileid: "56747726"
---
# <a name="dotnet-vstest"></a>DotNet test

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet-vstest` -Spustí testy ze zadaných souborů.

## <a name="synopsis"></a>Souhrn

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)
```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [--Blame|/Blame] [--InIsolation|/InIsolation]
    [[--] <args>...]] [-?|--Help|/?|/Help]
```
# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)
```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] 
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)
```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] 
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```
---

## <a name="description"></a>Popis

`dotnet-vstest` Příkaz spustí `VSTest.Console` aplikace příkazového řádku, chcete-li spustit automatizované testy jednotky.

## <a name="arguments"></a>Arguments

`TEST_FILE_NAMES`

Spusťte testy ze zadaných sestaveních. Více názvů sestavení testu oddělte mezerou.

## <a name="options"></a>Možnosti

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

`--Settings|/Settings:<Settings File>`

Nastavení se má použít při spuštění testů.

`--Tests|/Tests:<Test Names>`

Spusťte testy s názvy, které odpovídají zadaným hodnotám. Více hodnot oddělujte čárkami.

`--TestAdapterPath|/TestAdapterPath`

Používáte vlastní adaptéry testu ze zadané cesty (pokud existuje) v testovacím běhu.

`--Platform|/Platform:<Platform type>`

Cílová architektura platformy, použít pro spuštění testu. Platné hodnoty jsou `x86`, `x64`, a `ARM`.

`--Framework|/Framework:<Framework Version>`

Cílová verze rozhraní .NET Framework používá pro spuštění testu. Příklady platných hodnot `.NETFramework,Version=v4.6` nebo `.NETCoreApp,Version=v1.0`. Další podporované hodnoty jsou `Framework40`, `Framework45`, `FrameworkCore10`, a `FrameworkUap10`.

`--Parallel|/Parallel`

Spusťte testy paralelně. Ve výchozím nastavení se dají používat všechna dostupná jádra počítače. Zadejte explicitní počet jader pomocí nastavení MaxCpuCount vlastnosti uzlu RunConfiguration v souboru runsettings.

`--TestCaseFilter|/TestCaseFilter:<Expression>`

Spusťte testy, které odpovídají danému výrazu. `<Expression>` je ve formátu `<property>Operator<value>[|&<Expression>]`, kde operátor představuje jeden z `=`, `!=`, nebo `~`. Operátor `~` má 'obsahuje' sémantiku a je použitelný pro vlastnosti řetězce jako `DisplayName`. Závorky `()` se používají k dílčí výrazy skupiny.

`-?|--Help|/?|/Help`

Vytiskne krátký nápovědy pro příkaz.

`--logger|/logger:<Logger Uri/FriendlyName>`

Zadejte protokolovací nástroj pro výsledky testů.

* Chcete-li publikovat výsledky testů do sady Team Foundation Server, použijte `TfsPublisher` protokolovacího nástroje zprostředkovatele:

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* Pro protokolování výsledků do Visual Studio Test výsledky souboru (TRX), použijte `trx` poskytovatele protokolovacího nástroje. Tento přepínač vytvoří soubor ve výsledcích testu adresáře s zadaný název souboru protokolu. Pokud `LogFileName` není uvedený, je vytvořen jedinečný název souboru pro uložení výsledků testu.

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

Obsahuje seznam všech testů zjištěných daném kontejneru testů.

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

Proces ID nadřazeného procesu zodpovědná za spuštění aktuální proces.

`--Port|/Port:<Port>`

Určuje port pro připojení soketu a přijímání zpráv událostí.

`--Diag|/Diag:<Path to log file>`

Umožňuje podrobné protokoly pro testovací platformě sady. Protokoly se zapisují do zadaného souboru.

`--Blame|/Blame`

Testy se spustí v režimu viny. Tato možnost je užitečná v izolaci problematické testů způsobí hostitele testu při selhání. Vytvoří výstupní soubor v aktuálním adresáři jako *Sequence.xml* , který zachycuje pořadí provádění testů před selhání.

`--InIsolation|/InIsolation`

Spustí testy v izolovaném procesu. Díky tomu *vstest.console.exe* méně pravděpodobné, že proces zastavení v případě chyby v testech, ale testy mohou běžet pomaleji.

`@<file>`

Přečte soubor odpovědí pro další možnosti.


`args`

Určuje další argumenty pro adaptér. Argumenty se zadávají jako dvojice název hodnota ve formátu `<n>=<v>`, kde `<n>` je název argumentu a `<v>` je hodnota argumentu. Prostor použijte k oddělení víc argumentů.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`--Settings|/Settings:<Settings File>`

Nastavení se má použít při spuštění testů.

`--Tests|/Tests:<Test Names>`

Spusťte testy s názvy, které odpovídají zadaným hodnotám. Více hodnot oddělujte čárkami.

`--TestAdapterPath|/TestAdapterPath`

Používáte vlastní adaptéry testu ze zadané cesty (pokud existuje) v testovacím běhu.

`--Platform|/Platform:<Platform type>`

Cílová architektura platformy, použít pro spuštění testu. Platné hodnoty jsou `x86`, `x64`, a `ARM`.

`--Framework|/Framework:<Framework Version>`

Cílová verze rozhraní .NET Framework používá pro spuštění testu. Příklady platných hodnot `.NETFramework,Version=v4.6` nebo `.NETCoreApp,Version=v1.0`. Další podporované hodnoty jsou `Framework40`, `Framework45`, a `FrameworkCore10`.

`--Parallel|/Parallel`

Spusťte testy paralelně. Ve výchozím nastavení se dají používat všechna dostupná jádra počítače. Zadejte explicitní počet jader pomocí nastavení MaxCpuCount vlastnosti uzlu RunConfiguration v souboru runsettings.

`--TestCaseFilter|/TestCaseFilter:<Expression>`

Spusťte testy, které odpovídají danému výrazu. `<Expression>` je ve formátu `<property>Operator<value>[|&<Expression>]`, kde operátor představuje jeden z `=`, `!=`, nebo `~`. Operátor `~` má 'obsahuje' sémantiku a je použitelný pro vlastnosti řetězce jako `DisplayName`. Závorky `()` se používají k dílčí výrazy skupiny.

`-?|--Help|/?|/Help`

Vytiskne krátký nápovědy pro příkaz.

`--logger|/logger:<Logger Uri/FriendlyName>`

Zadejte protokolovací nástroj pro výsledky testů.

* Chcete-li publikovat výsledky testů do sady Team Foundation Server, použijte `TfsPublisher` protokolovacího nástroje zprostředkovatele:

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* Pro protokolování výsledků do Visual Studio Test výsledky souboru (TRX), použijte `trx` poskytovatele protokolovacího nástroje. Tento přepínač vytvoří soubor ve výsledcích testu adresáře s zadaný název souboru protokolu. Pokud `LogFileName` není uvedený, je vytvořen jedinečný název souboru pro uložení výsledků testu.

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

Obsahuje seznam všech testů zjištěných daném kontejneru testů.

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

Proces ID nadřazeného procesu zodpovědná za spuštění aktuální proces.

`--Port|/Port:<Port>`

Určuje port pro připojení soketu a přijímání zpráv událostí.

`--Diag|/Diag:<Path to log file>`

Umožňuje podrobné protokoly pro testovací platformě sady. Protokoly se zapisují do zadaného souboru.

`args`

Určuje další argumenty pro adaptér. Argumenty se zadávají jako dvojice název hodnota ve formátu `<n>=<v>`, kde `<n>` je název argumentu a `<v>` je hodnota argumentu. Prostor použijte k oddělení víc argumentů.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`--Settings|/Settings:<Settings File>`

Nastavení se má použít při spuštění testů.

`--Tests|/Tests:<Test Names>`

Spusťte testy s názvy, které odpovídají zadaným hodnotám. Více hodnot oddělujte čárkami.

`--TestAdapterPath|/TestAdapterPath`

Používáte vlastní adaptéry testu ze zadané cesty (pokud existuje) v testovacím běhu.

`--Platform|/Platform:<Platform type>`

Cílová architektura platformy, použít pro spuštění testu. Platné hodnoty jsou `x86`, `x64`, a `ARM`.

`--Framework|/Framework:<Framework Version>`

Cílová verze rozhraní .NET Framework používá pro spuštění testu. Příklady platných hodnot `.NETFramework,Version=v4.6` nebo `.NETCoreApp,Version=v1.0`. Další podporované hodnoty jsou `Framework40`, `Framework45`, a `FrameworkCore10`.

`--Parallel|/Parallel`

Spusťte testy paralelně. Ve výchozím nastavení se dají používat všechna dostupná jádra počítače. Zadejte explicitní počet jader pomocí nastavení MaxCpuCount vlastnosti uzlu RunConfiguration v souboru runsettings.

`--TestCaseFilter|/TestCaseFilter:<Expression>`

Spusťte testy, které odpovídají danému výrazu. `<Expression>` je ve formátu `<property>Operator<value>[|&<Expression>]`, kde operátor představuje jeden z `=`, `!=`, nebo `~`. Operátor `~` má 'obsahuje' sémantiku a je použitelný pro vlastnosti řetězce jako `DisplayName`. Závorky `()` se používají k dílčí výrazy skupiny.

`-?|--Help|/?|/Help`

Vytiskne krátký nápovědy pro příkaz.

`--logger|/logger:<Logger Uri/FriendlyName>`

Zadejte protokolovací nástroj pro výsledky testů.

* Chcete-li publikovat výsledky testů do sady Team Foundation Server, použijte `TfsPublisher` protokolovacího nástroje zprostředkovatele:

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* Pro protokolování výsledků do Visual Studio Test výsledky souboru (TRX), použijte `trx` poskytovatele protokolovacího nástroje. Tento přepínač vytvoří soubor ve výsledcích testu adresáře s zadaný název souboru protokolu. Pokud `LogFileName` není uvedený, je vytvořen jedinečný název souboru pro uložení výsledků testu.

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

Obsahuje seznam všech testů zjištěných daném kontejneru testů.

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

Proces ID nadřazeného procesu zodpovědná za spuštění aktuální proces.

`--Port|/Port:<Port>`

Určuje port pro připojení soketu a přijímání zpráv událostí.

`--Diag|/Diag:<Path to log file>`

Umožňuje podrobné protokoly pro testovací platformě sady. Protokoly se zapisují do zadaného souboru.

`args`

Určuje další argumenty pro adaptér. Argumenty se zadávají jako dvojice název hodnota ve formátu `<n>=<v>`, kde `<n>` je název argumentu a `<v>` je hodnota argumentu. Prostor použijte k oddělení víc argumentů.

---

## <a name="examples"></a>Příklady

Spustit testy v rámci `mytestproject.dll`:

`dotnet vstest mytestproject.dll`

Spustit testy v rámci `mytestproject.dll`, export do vlastní složky s vlastním názvem:

`dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path`

Spustit testy v rámci `mytestproject.dll` a `myothertestproject.exe`:

`dotnet vstest mytestproject.dll myothertestproject.exe`

Spustit `TestMethod1` testy:

`dotnet vstest /Tests:TestMethod1`

Spustit `TestMethod1` a `TestMethod2` testy:

`dotnet vstest /Tests:TestMethod1,TestMethod2`
