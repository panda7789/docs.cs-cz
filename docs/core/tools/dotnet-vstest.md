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
# <a name="dotnet-vstest"></a><span data-ttu-id="c49fd-103">DotNet test</span><span class="sxs-lookup"><span data-stu-id="c49fd-103">dotnet vstest</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="c49fd-104">Název</span><span class="sxs-lookup"><span data-stu-id="c49fd-104">Name</span></span>

<span data-ttu-id="c49fd-105">`dotnet-vstest` -Spustí testy ze zadaných souborů.</span><span class="sxs-lookup"><span data-stu-id="c49fd-105">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c49fd-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="c49fd-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="c49fd-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="c49fd-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [--Blame|/Blame] [--InIsolation|/InIsolation]
    [[--] <args>...]] [-?|--Help|/?|/Help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="c49fd-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="c49fd-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] 
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c49fd-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="c49fd-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] 
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```
---

## <a name="description"></a><span data-ttu-id="c49fd-110">Popis</span><span class="sxs-lookup"><span data-stu-id="c49fd-110">Description</span></span>

<span data-ttu-id="c49fd-111">`dotnet-vstest` Příkaz spustí `VSTest.Console` aplikace příkazového řádku, chcete-li spustit automatizované testy jednotky.</span><span class="sxs-lookup"><span data-stu-id="c49fd-111">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="c49fd-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="c49fd-112">Arguments</span></span>

`TEST_FILE_NAMES`

<span data-ttu-id="c49fd-113">Spusťte testy ze zadaných sestaveních.</span><span class="sxs-lookup"><span data-stu-id="c49fd-113">Run tests from the specified assemblies.</span></span> <span data-ttu-id="c49fd-114">Více názvů sestavení testu oddělte mezerou.</span><span class="sxs-lookup"><span data-stu-id="c49fd-114">Separate multiple test assembly names with spaces.</span></span>

## <a name="options"></a><span data-ttu-id="c49fd-115">Možnosti</span><span class="sxs-lookup"><span data-stu-id="c49fd-115">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="c49fd-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="c49fd-116">.NET Core 2.1</span></span>](#tab/netcore21)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="c49fd-117">Nastavení se má použít při spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="c49fd-117">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="c49fd-118">Spusťte testy s názvy, které odpovídají zadaným hodnotám.</span><span class="sxs-lookup"><span data-stu-id="c49fd-118">Run tests with names that match the provided values.</span></span> <span data-ttu-id="c49fd-119">Více hodnot oddělujte čárkami.</span><span class="sxs-lookup"><span data-stu-id="c49fd-119">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="c49fd-120">Používáte vlastní adaptéry testu ze zadané cesty (pokud existuje) v testovacím běhu.</span><span class="sxs-lookup"><span data-stu-id="c49fd-120">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="c49fd-121">Cílová architektura platformy, použít pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="c49fd-121">Target platform architecture used for test execution.</span></span> <span data-ttu-id="c49fd-122">Platné hodnoty jsou `x86`, `x64`, a `ARM`.</span><span class="sxs-lookup"><span data-stu-id="c49fd-122">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="c49fd-123">Cílová verze rozhraní .NET Framework používá pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="c49fd-123">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="c49fd-124">Příklady platných hodnot `.NETFramework,Version=v4.6` nebo `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="c49fd-124">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="c49fd-125">Další podporované hodnoty jsou `Framework40`, `Framework45`, `FrameworkCore10`, a `FrameworkUap10`.</span><span class="sxs-lookup"><span data-stu-id="c49fd-125">Other supported values are `Framework40`, `Framework45`, `FrameworkCore10`, and `FrameworkUap10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="c49fd-126">Spusťte testy paralelně.</span><span class="sxs-lookup"><span data-stu-id="c49fd-126">Execute tests in parallel.</span></span> <span data-ttu-id="c49fd-127">Ve výchozím nastavení se dají používat všechna dostupná jádra počítače.</span><span class="sxs-lookup"><span data-stu-id="c49fd-127">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="c49fd-128">Zadejte explicitní počet jader pomocí nastavení MaxCpuCount vlastnosti uzlu RunConfiguration v souboru runsettings.</span><span class="sxs-lookup"><span data-stu-id="c49fd-128">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="c49fd-129">Spusťte testy, které odpovídají danému výrazu.</span><span class="sxs-lookup"><span data-stu-id="c49fd-129">Run tests that match the given expression.</span></span> <span data-ttu-id="c49fd-130">`<Expression>` je ve formátu `<property>Operator<value>[|&<Expression>]`, kde operátor představuje jeden z `=`, `!=`, nebo `~`.</span><span class="sxs-lookup"><span data-stu-id="c49fd-130">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="c49fd-131">Operátor `~` má 'obsahuje' sémantiku a je použitelný pro vlastnosti řetězce jako `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="c49fd-131">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="c49fd-132">Závorky `()` se používají k dílčí výrazy skupiny.</span><span class="sxs-lookup"><span data-stu-id="c49fd-132">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="c49fd-133">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="c49fd-133">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="c49fd-134">Zadejte protokolovací nástroj pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="c49fd-134">Specify a logger for test results.</span></span>

* <span data-ttu-id="c49fd-135">Chcete-li publikovat výsledky testů do sady Team Foundation Server, použijte `TfsPublisher` protokolovacího nástroje zprostředkovatele:</span><span class="sxs-lookup"><span data-stu-id="c49fd-135">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="c49fd-136">Pro protokolování výsledků do Visual Studio Test výsledky souboru (TRX), použijte `trx` poskytovatele protokolovacího nástroje.</span><span class="sxs-lookup"><span data-stu-id="c49fd-136">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="c49fd-137">Tento přepínač vytvoří soubor ve výsledcích testu adresáře s zadaný název souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="c49fd-137">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="c49fd-138">Pokud `LogFileName` není uvedený, je vytvořen jedinečný název souboru pro uložení výsledků testu.</span><span class="sxs-lookup"><span data-stu-id="c49fd-138">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="c49fd-139">Obsahuje seznam všech testů zjištěných daném kontejneru testů.</span><span class="sxs-lookup"><span data-stu-id="c49fd-139">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="c49fd-140">Proces ID nadřazeného procesu zodpovědná za spuštění aktuální proces.</span><span class="sxs-lookup"><span data-stu-id="c49fd-140">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="c49fd-141">Určuje port pro připojení soketu a přijímání zpráv událostí.</span><span class="sxs-lookup"><span data-stu-id="c49fd-141">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="c49fd-142">Umožňuje podrobné protokoly pro testovací platformě sady.</span><span class="sxs-lookup"><span data-stu-id="c49fd-142">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="c49fd-143">Protokoly se zapisují do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="c49fd-143">Logs are written to the provided file.</span></span>

`--Blame|/Blame`

<span data-ttu-id="c49fd-144">Testy se spustí v režimu viny.</span><span class="sxs-lookup"><span data-stu-id="c49fd-144">Runs the tests in blame mode.</span></span> <span data-ttu-id="c49fd-145">Tato možnost je užitečná v izolaci problematické testů způsobí hostitele testu při selhání.</span><span class="sxs-lookup"><span data-stu-id="c49fd-145">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="c49fd-146">Vytvoří výstupní soubor v aktuálním adresáři jako *Sequence.xml* , který zachycuje pořadí provádění testů před selhání.</span><span class="sxs-lookup"><span data-stu-id="c49fd-146">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`--InIsolation|/InIsolation`

<span data-ttu-id="c49fd-147">Spustí testy v izolovaném procesu.</span><span class="sxs-lookup"><span data-stu-id="c49fd-147">Runs the tests in an isolated process.</span></span> <span data-ttu-id="c49fd-148">Díky tomu *vstest.console.exe* méně pravděpodobné, že proces zastavení v případě chyby v testech, ale testy mohou běžet pomaleji.</span><span class="sxs-lookup"><span data-stu-id="c49fd-148">This makes *vstest.console.exe* process less likely to be stopped on an error in the tests, but tests may run slower.</span></span>

`@<file>`

<span data-ttu-id="c49fd-149">Přečte soubor odpovědí pro další možnosti.</span><span class="sxs-lookup"><span data-stu-id="c49fd-149">Reads response file for more options.</span></span>


`args`

<span data-ttu-id="c49fd-150">Určuje další argumenty pro adaptér.</span><span class="sxs-lookup"><span data-stu-id="c49fd-150">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="c49fd-151">Argumenty se zadávají jako dvojice název hodnota ve formátu `<n>=<v>`, kde `<n>` je název argumentu a `<v>` je hodnota argumentu.</span><span class="sxs-lookup"><span data-stu-id="c49fd-151">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="c49fd-152">Prostor použijte k oddělení víc argumentů.</span><span class="sxs-lookup"><span data-stu-id="c49fd-152">Use a space to separate multiple arguments.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="c49fd-153">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="c49fd-153">.NET Core 2.0</span></span>](#tab/netcore20)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="c49fd-154">Nastavení se má použít při spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="c49fd-154">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="c49fd-155">Spusťte testy s názvy, které odpovídají zadaným hodnotám.</span><span class="sxs-lookup"><span data-stu-id="c49fd-155">Run tests with names that match the provided values.</span></span> <span data-ttu-id="c49fd-156">Více hodnot oddělujte čárkami.</span><span class="sxs-lookup"><span data-stu-id="c49fd-156">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="c49fd-157">Používáte vlastní adaptéry testu ze zadané cesty (pokud existuje) v testovacím běhu.</span><span class="sxs-lookup"><span data-stu-id="c49fd-157">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="c49fd-158">Cílová architektura platformy, použít pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="c49fd-158">Target platform architecture used for test execution.</span></span> <span data-ttu-id="c49fd-159">Platné hodnoty jsou `x86`, `x64`, a `ARM`.</span><span class="sxs-lookup"><span data-stu-id="c49fd-159">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="c49fd-160">Cílová verze rozhraní .NET Framework používá pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="c49fd-160">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="c49fd-161">Příklady platných hodnot `.NETFramework,Version=v4.6` nebo `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="c49fd-161">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="c49fd-162">Další podporované hodnoty jsou `Framework40`, `Framework45`, a `FrameworkCore10`.</span><span class="sxs-lookup"><span data-stu-id="c49fd-162">Other supported values are `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="c49fd-163">Spusťte testy paralelně.</span><span class="sxs-lookup"><span data-stu-id="c49fd-163">Execute tests in parallel.</span></span> <span data-ttu-id="c49fd-164">Ve výchozím nastavení se dají používat všechna dostupná jádra počítače.</span><span class="sxs-lookup"><span data-stu-id="c49fd-164">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="c49fd-165">Zadejte explicitní počet jader pomocí nastavení MaxCpuCount vlastnosti uzlu RunConfiguration v souboru runsettings.</span><span class="sxs-lookup"><span data-stu-id="c49fd-165">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="c49fd-166">Spusťte testy, které odpovídají danému výrazu.</span><span class="sxs-lookup"><span data-stu-id="c49fd-166">Run tests that match the given expression.</span></span> <span data-ttu-id="c49fd-167">`<Expression>` je ve formátu `<property>Operator<value>[|&<Expression>]`, kde operátor představuje jeden z `=`, `!=`, nebo `~`.</span><span class="sxs-lookup"><span data-stu-id="c49fd-167">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="c49fd-168">Operátor `~` má 'obsahuje' sémantiku a je použitelný pro vlastnosti řetězce jako `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="c49fd-168">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="c49fd-169">Závorky `()` se používají k dílčí výrazy skupiny.</span><span class="sxs-lookup"><span data-stu-id="c49fd-169">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="c49fd-170">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="c49fd-170">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="c49fd-171">Zadejte protokolovací nástroj pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="c49fd-171">Specify a logger for test results.</span></span>

* <span data-ttu-id="c49fd-172">Chcete-li publikovat výsledky testů do sady Team Foundation Server, použijte `TfsPublisher` protokolovacího nástroje zprostředkovatele:</span><span class="sxs-lookup"><span data-stu-id="c49fd-172">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="c49fd-173">Pro protokolování výsledků do Visual Studio Test výsledky souboru (TRX), použijte `trx` poskytovatele protokolovacího nástroje.</span><span class="sxs-lookup"><span data-stu-id="c49fd-173">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="c49fd-174">Tento přepínač vytvoří soubor ve výsledcích testu adresáře s zadaný název souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="c49fd-174">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="c49fd-175">Pokud `LogFileName` není uvedený, je vytvořen jedinečný název souboru pro uložení výsledků testu.</span><span class="sxs-lookup"><span data-stu-id="c49fd-175">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="c49fd-176">Obsahuje seznam všech testů zjištěných daném kontejneru testů.</span><span class="sxs-lookup"><span data-stu-id="c49fd-176">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="c49fd-177">Proces ID nadřazeného procesu zodpovědná za spuštění aktuální proces.</span><span class="sxs-lookup"><span data-stu-id="c49fd-177">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="c49fd-178">Určuje port pro připojení soketu a přijímání zpráv událostí.</span><span class="sxs-lookup"><span data-stu-id="c49fd-178">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="c49fd-179">Umožňuje podrobné protokoly pro testovací platformě sady.</span><span class="sxs-lookup"><span data-stu-id="c49fd-179">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="c49fd-180">Protokoly se zapisují do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="c49fd-180">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="c49fd-181">Určuje další argumenty pro adaptér.</span><span class="sxs-lookup"><span data-stu-id="c49fd-181">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="c49fd-182">Argumenty se zadávají jako dvojice název hodnota ve formátu `<n>=<v>`, kde `<n>` je název argumentu a `<v>` je hodnota argumentu.</span><span class="sxs-lookup"><span data-stu-id="c49fd-182">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="c49fd-183">Prostor použijte k oddělení víc argumentů.</span><span class="sxs-lookup"><span data-stu-id="c49fd-183">Use a space to separate multiple arguments.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c49fd-184">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="c49fd-184">.NET Core 1.x</span></span>](#tab/netcore1x)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="c49fd-185">Nastavení se má použít při spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="c49fd-185">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="c49fd-186">Spusťte testy s názvy, které odpovídají zadaným hodnotám.</span><span class="sxs-lookup"><span data-stu-id="c49fd-186">Run tests with names that match the provided values.</span></span> <span data-ttu-id="c49fd-187">Více hodnot oddělujte čárkami.</span><span class="sxs-lookup"><span data-stu-id="c49fd-187">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="c49fd-188">Používáte vlastní adaptéry testu ze zadané cesty (pokud existuje) v testovacím běhu.</span><span class="sxs-lookup"><span data-stu-id="c49fd-188">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="c49fd-189">Cílová architektura platformy, použít pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="c49fd-189">Target platform architecture used for test execution.</span></span> <span data-ttu-id="c49fd-190">Platné hodnoty jsou `x86`, `x64`, a `ARM`.</span><span class="sxs-lookup"><span data-stu-id="c49fd-190">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="c49fd-191">Cílová verze rozhraní .NET Framework používá pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="c49fd-191">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="c49fd-192">Příklady platných hodnot `.NETFramework,Version=v4.6` nebo `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="c49fd-192">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="c49fd-193">Další podporované hodnoty jsou `Framework40`, `Framework45`, a `FrameworkCore10`.</span><span class="sxs-lookup"><span data-stu-id="c49fd-193">Other supported values are `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="c49fd-194">Spusťte testy paralelně.</span><span class="sxs-lookup"><span data-stu-id="c49fd-194">Execute tests in parallel.</span></span> <span data-ttu-id="c49fd-195">Ve výchozím nastavení se dají používat všechna dostupná jádra počítače.</span><span class="sxs-lookup"><span data-stu-id="c49fd-195">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="c49fd-196">Zadejte explicitní počet jader pomocí nastavení MaxCpuCount vlastnosti uzlu RunConfiguration v souboru runsettings.</span><span class="sxs-lookup"><span data-stu-id="c49fd-196">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="c49fd-197">Spusťte testy, které odpovídají danému výrazu.</span><span class="sxs-lookup"><span data-stu-id="c49fd-197">Run tests that match the given expression.</span></span> <span data-ttu-id="c49fd-198">`<Expression>` je ve formátu `<property>Operator<value>[|&<Expression>]`, kde operátor představuje jeden z `=`, `!=`, nebo `~`.</span><span class="sxs-lookup"><span data-stu-id="c49fd-198">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="c49fd-199">Operátor `~` má 'obsahuje' sémantiku a je použitelný pro vlastnosti řetězce jako `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="c49fd-199">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="c49fd-200">Závorky `()` se používají k dílčí výrazy skupiny.</span><span class="sxs-lookup"><span data-stu-id="c49fd-200">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="c49fd-201">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="c49fd-201">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="c49fd-202">Zadejte protokolovací nástroj pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="c49fd-202">Specify a logger for test results.</span></span>

* <span data-ttu-id="c49fd-203">Chcete-li publikovat výsledky testů do sady Team Foundation Server, použijte `TfsPublisher` protokolovacího nástroje zprostředkovatele:</span><span class="sxs-lookup"><span data-stu-id="c49fd-203">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="c49fd-204">Pro protokolování výsledků do Visual Studio Test výsledky souboru (TRX), použijte `trx` poskytovatele protokolovacího nástroje.</span><span class="sxs-lookup"><span data-stu-id="c49fd-204">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="c49fd-205">Tento přepínač vytvoří soubor ve výsledcích testu adresáře s zadaný název souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="c49fd-205">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="c49fd-206">Pokud `LogFileName` není uvedený, je vytvořen jedinečný název souboru pro uložení výsledků testu.</span><span class="sxs-lookup"><span data-stu-id="c49fd-206">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="c49fd-207">Obsahuje seznam všech testů zjištěných daném kontejneru testů.</span><span class="sxs-lookup"><span data-stu-id="c49fd-207">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="c49fd-208">Proces ID nadřazeného procesu zodpovědná za spuštění aktuální proces.</span><span class="sxs-lookup"><span data-stu-id="c49fd-208">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="c49fd-209">Určuje port pro připojení soketu a přijímání zpráv událostí.</span><span class="sxs-lookup"><span data-stu-id="c49fd-209">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="c49fd-210">Umožňuje podrobné protokoly pro testovací platformě sady.</span><span class="sxs-lookup"><span data-stu-id="c49fd-210">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="c49fd-211">Protokoly se zapisují do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="c49fd-211">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="c49fd-212">Určuje další argumenty pro adaptér.</span><span class="sxs-lookup"><span data-stu-id="c49fd-212">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="c49fd-213">Argumenty se zadávají jako dvojice název hodnota ve formátu `<n>=<v>`, kde `<n>` je název argumentu a `<v>` je hodnota argumentu.</span><span class="sxs-lookup"><span data-stu-id="c49fd-213">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="c49fd-214">Prostor použijte k oddělení víc argumentů.</span><span class="sxs-lookup"><span data-stu-id="c49fd-214">Use a space to separate multiple arguments.</span></span>

---

## <a name="examples"></a><span data-ttu-id="c49fd-215">Příklady</span><span class="sxs-lookup"><span data-stu-id="c49fd-215">Examples</span></span>

<span data-ttu-id="c49fd-216">Spustit testy v rámci `mytestproject.dll`:</span><span class="sxs-lookup"><span data-stu-id="c49fd-216">Run tests in `mytestproject.dll`:</span></span>

`dotnet vstest mytestproject.dll`

<span data-ttu-id="c49fd-217">Spustit testy v rámci `mytestproject.dll`, export do vlastní složky s vlastním názvem:</span><span class="sxs-lookup"><span data-stu-id="c49fd-217">Run tests in `mytestproject.dll`, exporting to custom folder with custom name:</span></span>

`dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path`

<span data-ttu-id="c49fd-218">Spustit testy v rámci `mytestproject.dll` a `myothertestproject.exe`:</span><span class="sxs-lookup"><span data-stu-id="c49fd-218">Run tests in `mytestproject.dll` and `myothertestproject.exe`:</span></span>

`dotnet vstest mytestproject.dll myothertestproject.exe`

<span data-ttu-id="c49fd-219">Spustit `TestMethod1` testy:</span><span class="sxs-lookup"><span data-stu-id="c49fd-219">Run `TestMethod1` tests:</span></span>

`dotnet vstest /Tests:TestMethod1`

<span data-ttu-id="c49fd-220">Spustit `TestMethod1` a `TestMethod2` testy:</span><span class="sxs-lookup"><span data-stu-id="c49fd-220">Run `TestMethod1` and `TestMethod2` tests:</span></span>

`dotnet vstest /Tests:TestMethod1,TestMethod2`
