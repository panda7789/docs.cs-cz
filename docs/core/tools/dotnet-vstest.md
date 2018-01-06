---
title: "příkaz vstest DotNet - .NET Core rozhraní příkazového řádku"
description: "Příkaz vstest dotnet sestavení projektu a všechny jeho závislé součásti."
author: guardrex
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: f2ad875430b2dc7f0ffbadfb9a39dd83854557cb
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/05/2018
---
# <a name="dotnet-vstest"></a>vstest DotNet.

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet-vstest`-Spustí testy ze zadané soubory.

## <a name="synopsis"></a>Stručný obsah

`dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]`

## <a name="description"></a>Popis

`dotnet-vstest` Příkaz spustí `VSTest.Console` aplikace příkazového řádku spouštět automatizované částí a programové testy uživatelského rozhraní aplikace.

## <a name="arguments"></a>Arguments

`TEST_FILE_NAMES`

Spouštění testů ze zadaného sestavení. Názvy sestavení více testovací oddělte mezerou.

## <a name="options"></a>Možnosti

`--Settings|/Settings:<Settings File>`

Nastavení se má použít při spouštění testů.

`--Tests|/Tests:<Test Names>`

Spouštění testů pomocí názvy, které odpovídají zadaným hodnotám. Více hodnot oddělujte čárkami.

`--TestAdapterPath|/TestAdapterPath`

Použijte vlastní test adaptéry z dané cesty (pokud existuje) v testovacím běhu.

`--Platform|/Platform:<Platform type>`

Architektura platformy cíl používá pro spuštění testu. Platné hodnoty jsou `x86`, `x64`, a `ARM`.

`--Framework|/Framework:<Framework Version>`

Cílová verze rozhraní .NET Framework používá pro spuštění testu. Příklady platných hodnot `.NETFramework,Version=v4.6`, `.NETCoreApp,Version=v1.0`atd. Jiné podporované hodnoty jsou `Framework35`, `Framework40`, `Framework45`, a `FrameworkCore10`.

`--Parallel|/Parallel`

Spustíte testy paralelně. Standardně jsou všechny dostupné jader na počítači k dispozici pro použití. Soubor nastavení nastavte explicitní počet jader.

`--TestCaseFilter|/TestCaseFilter:<Expression>`

Testy, které odpovídají daného výrazu. `<Expression>`je ve formátu `<property>Operator<value>[|&<Expression>]`, kde operátor je jedním z `=`, `!=`, nebo `~`.  Operátor `~` má "obsahuje" sémantiku a použít u vlastnosti řetězce jako `DisplayName`. Závorky `()` se používají k dílčí výrazy skupiny.

`-?|--Help|/?|/Help`

Vytiskne krátké nápovědy pro příkaz.

`--logger|/logger:<Logger Uri/FriendlyName>`

Zadejte protokolovacího nástroje pro výsledky testů.  

* K publikování výsledků testů pro Team Foundation Server, použijte `TfsPublisher` protokolovač zprostředkovatele:

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* Do protokolu výsledky do Visual Studio Test výsledky souboru (TRX), použijte `trx` zprostředkovatele protokolovacího nástroje. Tento přepínač vytvoří soubor ve výsledcích testu adresáři s zadaný název souboru protokolu. Pokud `LogFileName` není zadaný jedinečný název souboru je vytvořen za účelem uchovávání výsledků testů.

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

Seznamy zjistit testů z daného testovacího kontejneru.

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

Id procesu nadřazené zodpovědná za spuštění aktuálním procesu.

`--Port|/Port:<Port>`

Určuje port pro připojení soketu a přijímat zprávy o událostech.

`--Diag|/Diag:<Path to log file>`

Umožňuje podrobné protokoly pro platformu testu. Protokoly se zapisují do zadaného souboru.

`args`

Určuje další argumenty pro adaptér. Argumenty nejsou zadány jako dvojice název hodnota ve formátu `<n>=<v>`, kde `<n>` je název argument a `<v>` je hodnota argumentu. Prostor používejte k oddělení více argumentů.

## <a name="examples"></a>Příklady

Spuštění testů `mytestproject.dll`:

`dotnet vstest mytestproject.dll`

Spuštění testů `mytestproject.dll`, export do vlastní složky s vlastní název:

`dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path`

Spuštění testů `mytestproject.dll` a `myothertestproject.exe`:

`dotnet vstest mytestproject.dll myothertestproject.exe`

Spustit `TestMethod1` testů:

`dotnet vstest /Tests:TestMethod1`

Spustit `TestMethod1` a `TestMethod2` testů:

`dotnet vstest /Tests:TestMethod1,TestMethod2`

