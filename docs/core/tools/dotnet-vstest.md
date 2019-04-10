---
title: příkaz DotNet vstest
description: Příkaz dotnet vstest sestavení projektu a všechny jeho závislosti.
author: guardrex
ms.date: 05/30/2018
ms.openlocfilehash: 25d1b2d65b3e91bce894c59959a58537fa8ca113
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59204013"
---
# <a name="dotnet-vstest"></a><span data-ttu-id="da243-103">DotNet test</span><span class="sxs-lookup"><span data-stu-id="da243-103">dotnet vstest</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="da243-104">Name</span><span class="sxs-lookup"><span data-stu-id="da243-104">Name</span></span>

`dotnet-vstest` <span data-ttu-id="da243-105">-Spustí testy ze zadaných souborů.</span><span class="sxs-lookup"><span data-stu-id="da243-105">- Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="da243-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="da243-106">Synopsis</span></span>

# [<a name="net-core-21"></a><span data-ttu-id="da243-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="da243-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [--Blame|/Blame] [--InIsolation|/InIsolation]
    [[--] <args>...]] [-?|--Help|/?|/Help]
```
# [<a name="net-core-20"></a><span data-ttu-id="da243-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="da243-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] 
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```
# [<a name="net-core-1x"></a><span data-ttu-id="da243-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="da243-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] 
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```
---

## <a name="description"></a><span data-ttu-id="da243-110">Popis</span><span class="sxs-lookup"><span data-stu-id="da243-110">Description</span></span>

<span data-ttu-id="da243-111">`dotnet-vstest` Příkaz spustí `VSTest.Console` aplikace příkazového řádku, chcete-li spustit automatizované testy jednotky.</span><span class="sxs-lookup"><span data-stu-id="da243-111">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="da243-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="da243-112">Arguments</span></span>

`TEST_FILE_NAMES`

<span data-ttu-id="da243-113">Spusťte testy ze zadaných sestaveních.</span><span class="sxs-lookup"><span data-stu-id="da243-113">Run tests from the specified assemblies.</span></span> <span data-ttu-id="da243-114">Více názvů sestavení testu oddělte mezerou.</span><span class="sxs-lookup"><span data-stu-id="da243-114">Separate multiple test assembly names with spaces.</span></span>

## <a name="options"></a><span data-ttu-id="da243-115">Možnosti</span><span class="sxs-lookup"><span data-stu-id="da243-115">Options</span></span>

# [<a name="net-core-21"></a><span data-ttu-id="da243-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="da243-116">.NET Core 2.1</span></span>](#tab/netcore21)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="da243-117">Nastavení se má použít při spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="da243-117">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="da243-118">Spusťte testy s názvy, které odpovídají zadaným hodnotám.</span><span class="sxs-lookup"><span data-stu-id="da243-118">Run tests with names that match the provided values.</span></span> <span data-ttu-id="da243-119">Více hodnot oddělujte čárkami.</span><span class="sxs-lookup"><span data-stu-id="da243-119">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="da243-120">Používáte vlastní adaptéry testu ze zadané cesty (pokud existuje) v testovacím běhu.</span><span class="sxs-lookup"><span data-stu-id="da243-120">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="da243-121">Cílová architektura platformy, použít pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="da243-121">Target platform architecture used for test execution.</span></span> <span data-ttu-id="da243-122">Platné hodnoty jsou `x86`, `x64`, a `ARM`.</span><span class="sxs-lookup"><span data-stu-id="da243-122">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="da243-123">Cílová verze rozhraní .NET Framework používá pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="da243-123">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="da243-124">Příklady platných hodnot `.NETFramework,Version=v4.6` nebo `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="da243-124">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="da243-125">Další podporované hodnoty jsou `Framework40`, `Framework45`, `FrameworkCore10`, a `FrameworkUap10`.</span><span class="sxs-lookup"><span data-stu-id="da243-125">Other supported values are `Framework40`, `Framework45`, `FrameworkCore10`, and `FrameworkUap10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="da243-126">Spusťte testy paralelně.</span><span class="sxs-lookup"><span data-stu-id="da243-126">Execute tests in parallel.</span></span> <span data-ttu-id="da243-127">Ve výchozím nastavení se dají používat všechna dostupná jádra počítače.</span><span class="sxs-lookup"><span data-stu-id="da243-127">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="da243-128">Zadejte explicitní počet jader pomocí nastavení MaxCpuCount vlastnosti uzlu RunConfiguration v souboru runsettings.</span><span class="sxs-lookup"><span data-stu-id="da243-128">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="da243-129">Spusťte testy, které odpovídají danému výrazu.</span><span class="sxs-lookup"><span data-stu-id="da243-129">Run tests that match the given expression.</span></span> `<Expression>` <span data-ttu-id="da243-130">je ve formátu `<property>Operator<value>[|&<Expression>]`, kde operátor představuje jeden z `=`, `!=`, nebo `~`.</span><span class="sxs-lookup"><span data-stu-id="da243-130">is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="da243-131">Operátor `~` má 'obsahuje' sémantiku a je použitelný pro vlastnosti řetězce jako `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="da243-131">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="da243-132">Závorky `()` se používají k dílčí výrazy skupiny.</span><span class="sxs-lookup"><span data-stu-id="da243-132">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="da243-133">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="da243-133">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="da243-134">Zadejte protokolovací nástroj pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="da243-134">Specify a logger for test results.</span></span>

* <span data-ttu-id="da243-135">Chcete-li publikovat výsledky testů do sady Team Foundation Server, použijte `TfsPublisher` protokolovacího nástroje zprostředkovatele:</span><span class="sxs-lookup"><span data-stu-id="da243-135">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="da243-136">Pro protokolování výsledků do Visual Studio Test výsledky souboru (TRX), použijte `trx` poskytovatele protokolovacího nástroje.</span><span class="sxs-lookup"><span data-stu-id="da243-136">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="da243-137">Tento přepínač vytvoří soubor ve výsledcích testu adresáře s zadaný název souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="da243-137">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="da243-138">Pokud `LogFileName` není uvedený, je vytvořen jedinečný název souboru pro uložení výsledků testu.</span><span class="sxs-lookup"><span data-stu-id="da243-138">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="da243-139">Obsahuje seznam všech testů zjištěných daném kontejneru testů.</span><span class="sxs-lookup"><span data-stu-id="da243-139">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="da243-140">Proces ID nadřazeného procesu zodpovědná za spuštění aktuální proces.</span><span class="sxs-lookup"><span data-stu-id="da243-140">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="da243-141">Určuje port pro připojení soketu a přijímání zpráv událostí.</span><span class="sxs-lookup"><span data-stu-id="da243-141">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="da243-142">Umožňuje podrobné protokoly pro testovací platformě sady.</span><span class="sxs-lookup"><span data-stu-id="da243-142">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="da243-143">Protokoly se zapisují do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="da243-143">Logs are written to the provided file.</span></span>

`--Blame|/Blame`

<span data-ttu-id="da243-144">Testy se spustí v režimu viny.</span><span class="sxs-lookup"><span data-stu-id="da243-144">Runs the tests in blame mode.</span></span> <span data-ttu-id="da243-145">Tato možnost je užitečná v izolaci problematické testů způsobí hostitele testu při selhání.</span><span class="sxs-lookup"><span data-stu-id="da243-145">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="da243-146">Vytvoří výstupní soubor v aktuálním adresáři jako *Sequence.xml* , který zachycuje pořadí provádění testů před selhání.</span><span class="sxs-lookup"><span data-stu-id="da243-146">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`--InIsolation|/InIsolation`

<span data-ttu-id="da243-147">Spustí testy v izolovaném procesu.</span><span class="sxs-lookup"><span data-stu-id="da243-147">Runs the tests in an isolated process.</span></span> <span data-ttu-id="da243-148">Díky tomu *vstest.console.exe* méně pravděpodobné, že proces zastavení v případě chyby v testech, ale testy mohou běžet pomaleji.</span><span class="sxs-lookup"><span data-stu-id="da243-148">This makes *vstest.console.exe* process less likely to be stopped on an error in the tests, but tests may run slower.</span></span>

`@<file>`

<span data-ttu-id="da243-149">Přečte soubor odpovědí pro další možnosti.</span><span class="sxs-lookup"><span data-stu-id="da243-149">Reads response file for more options.</span></span>

`args`

<span data-ttu-id="da243-150">Určuje další argumenty pro adaptér.</span><span class="sxs-lookup"><span data-stu-id="da243-150">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="da243-151">Argumenty se zadávají jako dvojice název hodnota ve formátu `<n>=<v>`, kde `<n>` je název argumentu a `<v>` je hodnota argumentu.</span><span class="sxs-lookup"><span data-stu-id="da243-151">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="da243-152">Prostor použijte k oddělení víc argumentů.</span><span class="sxs-lookup"><span data-stu-id="da243-152">Use a space to separate multiple arguments.</span></span>

# [<a name="net-core-20"></a><span data-ttu-id="da243-153">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="da243-153">.NET Core 2.0</span></span>](#tab/netcore20)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="da243-154">Nastavení se má použít při spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="da243-154">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="da243-155">Spusťte testy s názvy, které odpovídají zadaným hodnotám.</span><span class="sxs-lookup"><span data-stu-id="da243-155">Run tests with names that match the provided values.</span></span> <span data-ttu-id="da243-156">Více hodnot oddělujte čárkami.</span><span class="sxs-lookup"><span data-stu-id="da243-156">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="da243-157">Používáte vlastní adaptéry testu ze zadané cesty (pokud existuje) v testovacím běhu.</span><span class="sxs-lookup"><span data-stu-id="da243-157">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="da243-158">Cílová architektura platformy, použít pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="da243-158">Target platform architecture used for test execution.</span></span> <span data-ttu-id="da243-159">Platné hodnoty jsou `x86`, `x64`, a `ARM`.</span><span class="sxs-lookup"><span data-stu-id="da243-159">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="da243-160">Cílová verze rozhraní .NET Framework používá pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="da243-160">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="da243-161">Příklady platných hodnot `.NETFramework,Version=v4.6` nebo `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="da243-161">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="da243-162">Další podporované hodnoty jsou `Framework40`, `Framework45`, a `FrameworkCore10`.</span><span class="sxs-lookup"><span data-stu-id="da243-162">Other supported values are `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="da243-163">Spusťte testy paralelně.</span><span class="sxs-lookup"><span data-stu-id="da243-163">Execute tests in parallel.</span></span> <span data-ttu-id="da243-164">Ve výchozím nastavení se dají používat všechna dostupná jádra počítače.</span><span class="sxs-lookup"><span data-stu-id="da243-164">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="da243-165">Zadejte explicitní počet jader pomocí nastavení MaxCpuCount vlastnosti uzlu RunConfiguration v souboru runsettings.</span><span class="sxs-lookup"><span data-stu-id="da243-165">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="da243-166">Spusťte testy, které odpovídají danému výrazu.</span><span class="sxs-lookup"><span data-stu-id="da243-166">Run tests that match the given expression.</span></span> `<Expression>` <span data-ttu-id="da243-167">je ve formátu `<property>Operator<value>[|&<Expression>]`, kde operátor představuje jeden z `=`, `!=`, nebo `~`.</span><span class="sxs-lookup"><span data-stu-id="da243-167">is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="da243-168">Operátor `~` má 'obsahuje' sémantiku a je použitelný pro vlastnosti řetězce jako `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="da243-168">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="da243-169">Závorky `()` se používají k dílčí výrazy skupiny.</span><span class="sxs-lookup"><span data-stu-id="da243-169">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="da243-170">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="da243-170">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="da243-171">Zadejte protokolovací nástroj pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="da243-171">Specify a logger for test results.</span></span>

* <span data-ttu-id="da243-172">Chcete-li publikovat výsledky testů do sady Team Foundation Server, použijte `TfsPublisher` protokolovacího nástroje zprostředkovatele:</span><span class="sxs-lookup"><span data-stu-id="da243-172">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="da243-173">Pro protokolování výsledků do Visual Studio Test výsledky souboru (TRX), použijte `trx` poskytovatele protokolovacího nástroje.</span><span class="sxs-lookup"><span data-stu-id="da243-173">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="da243-174">Tento přepínač vytvoří soubor ve výsledcích testu adresáře s zadaný název souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="da243-174">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="da243-175">Pokud `LogFileName` není uvedený, je vytvořen jedinečný název souboru pro uložení výsledků testu.</span><span class="sxs-lookup"><span data-stu-id="da243-175">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="da243-176">Obsahuje seznam všech testů zjištěných daném kontejneru testů.</span><span class="sxs-lookup"><span data-stu-id="da243-176">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="da243-177">Proces ID nadřazeného procesu zodpovědná za spuštění aktuální proces.</span><span class="sxs-lookup"><span data-stu-id="da243-177">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="da243-178">Určuje port pro připojení soketu a přijímání zpráv událostí.</span><span class="sxs-lookup"><span data-stu-id="da243-178">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="da243-179">Umožňuje podrobné protokoly pro testovací platformě sady.</span><span class="sxs-lookup"><span data-stu-id="da243-179">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="da243-180">Protokoly se zapisují do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="da243-180">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="da243-181">Určuje další argumenty pro adaptér.</span><span class="sxs-lookup"><span data-stu-id="da243-181">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="da243-182">Argumenty se zadávají jako dvojice název hodnota ve formátu `<n>=<v>`, kde `<n>` je název argumentu a `<v>` je hodnota argumentu.</span><span class="sxs-lookup"><span data-stu-id="da243-182">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="da243-183">Prostor použijte k oddělení víc argumentů.</span><span class="sxs-lookup"><span data-stu-id="da243-183">Use a space to separate multiple arguments.</span></span>

# [<a name="net-core-1x"></a><span data-ttu-id="da243-184">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="da243-184">.NET Core 1.x</span></span>](#tab/netcore1x)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="da243-185">Nastavení se má použít při spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="da243-185">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="da243-186">Spusťte testy s názvy, které odpovídají zadaným hodnotám.</span><span class="sxs-lookup"><span data-stu-id="da243-186">Run tests with names that match the provided values.</span></span> <span data-ttu-id="da243-187">Více hodnot oddělujte čárkami.</span><span class="sxs-lookup"><span data-stu-id="da243-187">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="da243-188">Používáte vlastní adaptéry testu ze zadané cesty (pokud existuje) v testovacím běhu.</span><span class="sxs-lookup"><span data-stu-id="da243-188">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="da243-189">Cílová architektura platformy, použít pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="da243-189">Target platform architecture used for test execution.</span></span> <span data-ttu-id="da243-190">Platné hodnoty jsou `x86`, `x64`, a `ARM`.</span><span class="sxs-lookup"><span data-stu-id="da243-190">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="da243-191">Cílová verze rozhraní .NET Framework používá pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="da243-191">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="da243-192">Příklady platných hodnot `.NETFramework,Version=v4.6` nebo `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="da243-192">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="da243-193">Další podporované hodnoty jsou `Framework40`, `Framework45`, a `FrameworkCore10`.</span><span class="sxs-lookup"><span data-stu-id="da243-193">Other supported values are `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="da243-194">Spusťte testy paralelně.</span><span class="sxs-lookup"><span data-stu-id="da243-194">Execute tests in parallel.</span></span> <span data-ttu-id="da243-195">Ve výchozím nastavení se dají používat všechna dostupná jádra počítače.</span><span class="sxs-lookup"><span data-stu-id="da243-195">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="da243-196">Zadejte explicitní počet jader pomocí nastavení MaxCpuCount vlastnosti uzlu RunConfiguration v souboru runsettings.</span><span class="sxs-lookup"><span data-stu-id="da243-196">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="da243-197">Spusťte testy, které odpovídají danému výrazu.</span><span class="sxs-lookup"><span data-stu-id="da243-197">Run tests that match the given expression.</span></span> `<Expression>` <span data-ttu-id="da243-198">je ve formátu `<property>Operator<value>[|&<Expression>]`, kde operátor představuje jeden z `=`, `!=`, nebo `~`.</span><span class="sxs-lookup"><span data-stu-id="da243-198">is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="da243-199">Operátor `~` má 'obsahuje' sémantiku a je použitelný pro vlastnosti řetězce jako `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="da243-199">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="da243-200">Závorky `()` se používají k dílčí výrazy skupiny.</span><span class="sxs-lookup"><span data-stu-id="da243-200">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="da243-201">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="da243-201">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="da243-202">Zadejte protokolovací nástroj pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="da243-202">Specify a logger for test results.</span></span>

* <span data-ttu-id="da243-203">Chcete-li publikovat výsledky testů do sady Team Foundation Server, použijte `TfsPublisher` protokolovacího nástroje zprostředkovatele:</span><span class="sxs-lookup"><span data-stu-id="da243-203">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="da243-204">Pro protokolování výsledků do Visual Studio Test výsledky souboru (TRX), použijte `trx` poskytovatele protokolovacího nástroje.</span><span class="sxs-lookup"><span data-stu-id="da243-204">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="da243-205">Tento přepínač vytvoří soubor ve výsledcích testu adresáře s zadaný název souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="da243-205">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="da243-206">Pokud `LogFileName` není uvedený, je vytvořen jedinečný název souboru pro uložení výsledků testu.</span><span class="sxs-lookup"><span data-stu-id="da243-206">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="da243-207">Obsahuje seznam všech testů zjištěných daném kontejneru testů.</span><span class="sxs-lookup"><span data-stu-id="da243-207">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="da243-208">Proces ID nadřazeného procesu zodpovědná za spuštění aktuální proces.</span><span class="sxs-lookup"><span data-stu-id="da243-208">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="da243-209">Určuje port pro připojení soketu a přijímání zpráv událostí.</span><span class="sxs-lookup"><span data-stu-id="da243-209">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="da243-210">Umožňuje podrobné protokoly pro testovací platformě sady.</span><span class="sxs-lookup"><span data-stu-id="da243-210">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="da243-211">Protokoly se zapisují do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="da243-211">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="da243-212">Určuje další argumenty pro adaptér.</span><span class="sxs-lookup"><span data-stu-id="da243-212">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="da243-213">Argumenty se zadávají jako dvojice název hodnota ve formátu `<n>=<v>`, kde `<n>` je název argumentu a `<v>` je hodnota argumentu.</span><span class="sxs-lookup"><span data-stu-id="da243-213">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="da243-214">Prostor použijte k oddělení víc argumentů.</span><span class="sxs-lookup"><span data-stu-id="da243-214">Use a space to separate multiple arguments.</span></span>

---

## <a name="examples"></a><span data-ttu-id="da243-215">Příklady</span><span class="sxs-lookup"><span data-stu-id="da243-215">Examples</span></span>

<span data-ttu-id="da243-216">Spustit testy v rámci `mytestproject.dll`:</span><span class="sxs-lookup"><span data-stu-id="da243-216">Run tests in `mytestproject.dll`:</span></span>

`dotnet vstest mytestproject.dll`

<span data-ttu-id="da243-217">Spustit testy v rámci `mytestproject.dll`, export do vlastní složky s vlastním názvem:</span><span class="sxs-lookup"><span data-stu-id="da243-217">Run tests in `mytestproject.dll`, exporting to custom folder with custom name:</span></span>

`dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path`

<span data-ttu-id="da243-218">Spustit testy v rámci `mytestproject.dll` a `myothertestproject.exe`:</span><span class="sxs-lookup"><span data-stu-id="da243-218">Run tests in `mytestproject.dll` and `myothertestproject.exe`:</span></span>

`dotnet vstest mytestproject.dll myothertestproject.exe`

<span data-ttu-id="da243-219">Spustit `TestMethod1` testy:</span><span class="sxs-lookup"><span data-stu-id="da243-219">Run `TestMethod1` tests:</span></span>

`dotnet vstest /Tests:TestMethod1`

<span data-ttu-id="da243-220">Spustit `TestMethod1` a `TestMethod2` testy:</span><span class="sxs-lookup"><span data-stu-id="da243-220">Run `TestMethod1` and `TestMethod2` tests:</span></span>

`dotnet vstest /Tests:TestMethod1,TestMethod2`
