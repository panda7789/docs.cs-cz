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
# <a name="dotnet-vstest"></a><span data-ttu-id="c8b64-103">dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="c8b64-103">dotnet vstest</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="c8b64-104">Název</span><span class="sxs-lookup"><span data-stu-id="c8b64-104">Name</span></span>

<span data-ttu-id="c8b64-105">`dotnet-vstest` – spustí testy ze zadaných souborů.</span><span class="sxs-lookup"><span data-stu-id="c8b64-105">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c8b64-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="c8b64-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21"></a>[<span data-ttu-id="c8b64-107">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="c8b64-107">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [--Blame|/Blame] [--InIsolation|/InIsolation]
    [[--] <args>...]] [-?|--Help|/?|/Help]
```

# <a name="net-core-20"></a>[<span data-ttu-id="c8b64-108">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="c8b64-108">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] 
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```

# <a name="net-core-1x"></a>[<span data-ttu-id="c8b64-109">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="c8b64-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] 
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```

---

## <a name="description"></a><span data-ttu-id="c8b64-110">Popis</span><span class="sxs-lookup"><span data-stu-id="c8b64-110">Description</span></span>

<span data-ttu-id="c8b64-111">Příkaz `dotnet-vstest` spustí aplikaci `VSTest.Console` příkazového řádku, aby se spouštěly automatizované testy jednotek.</span><span class="sxs-lookup"><span data-stu-id="c8b64-111">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="c8b64-112">Argumenty</span><span class="sxs-lookup"><span data-stu-id="c8b64-112">Arguments</span></span>

`TEST_FILE_NAMES`

<span data-ttu-id="c8b64-113">Spustí testy ze zadaných sestavení.</span><span class="sxs-lookup"><span data-stu-id="c8b64-113">Run tests from the specified assemblies.</span></span> <span data-ttu-id="c8b64-114">Rozdělte více názvů testovacích sestavení s mezerami.</span><span class="sxs-lookup"><span data-stu-id="c8b64-114">Separate multiple test assembly names with spaces.</span></span>

## <a name="options"></a><span data-ttu-id="c8b64-115">Možnosti</span><span class="sxs-lookup"><span data-stu-id="c8b64-115">Options</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="c8b64-116">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="c8b64-116">.NET Core 2.1</span></span>](#tab/netcore21)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="c8b64-117">Nastavení, které se má použít při spouštění testů.</span><span class="sxs-lookup"><span data-stu-id="c8b64-117">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="c8b64-118">Spustí testy s názvy, které odpovídají zadaným hodnotám.</span><span class="sxs-lookup"><span data-stu-id="c8b64-118">Run tests with names that match the provided values.</span></span> <span data-ttu-id="c8b64-119">Více hodnot oddělte čárkami.</span><span class="sxs-lookup"><span data-stu-id="c8b64-119">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="c8b64-120">Použijte vlastní testovací adaptéry z dané cesty (pokud existuje) v testovacím běhu.</span><span class="sxs-lookup"><span data-stu-id="c8b64-120">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="c8b64-121">Cílová architektura platformy použitá pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="c8b64-121">Target platform architecture used for test execution.</span></span> <span data-ttu-id="c8b64-122">Platné hodnoty jsou `x86`, `x64`a `ARM`.</span><span class="sxs-lookup"><span data-stu-id="c8b64-122">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="c8b64-123">Cílová verze .NET Framework používaná pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="c8b64-123">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="c8b64-124">Příklady platných hodnot jsou `.NETFramework,Version=v4.6` nebo `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="c8b64-124">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="c8b64-125">Další podporované hodnoty jsou `Framework40`, `Framework45`, `FrameworkCore10`a `FrameworkUap10`.</span><span class="sxs-lookup"><span data-stu-id="c8b64-125">Other supported values are `Framework40`, `Framework45`, `FrameworkCore10`, and `FrameworkUap10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="c8b64-126">Paralelní provádění testů.</span><span class="sxs-lookup"><span data-stu-id="c8b64-126">Execute tests in parallel.</span></span> <span data-ttu-id="c8b64-127">Ve výchozím nastavení jsou všechny dostupné jádra počítače k dispozici pro použití.</span><span class="sxs-lookup"><span data-stu-id="c8b64-127">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="c8b64-128">Určete explicitní počet jader nastavením vlastnosti MaxCpuCount v uzlu RunConfiguration v souboru runsettings.</span><span class="sxs-lookup"><span data-stu-id="c8b64-128">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="c8b64-129">Spustí testy, které odpovídají danému výrazu.</span><span class="sxs-lookup"><span data-stu-id="c8b64-129">Run tests that match the given expression.</span></span> <span data-ttu-id="c8b64-130">`<Expression>` je `<property>Operator<value>[|&<Expression>]`formátu, kde operátor je jedním z `=`, `!=`nebo `~`.</span><span class="sxs-lookup"><span data-stu-id="c8b64-130">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="c8b64-131">Operátor `~` obsahuje sémantiku Contains a je použitelný pro řetězcové vlastnosti, jako je `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="c8b64-131">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="c8b64-132">`()` závorky se používají k seskupení podvýrazů.</span><span class="sxs-lookup"><span data-stu-id="c8b64-132">Parenthesis `()` are used to group subexpressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="c8b64-133">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="c8b64-133">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="c8b64-134">Zadejte protokolovací nástroj pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="c8b64-134">Specify a logger for test results.</span></span>

* <span data-ttu-id="c8b64-135">K publikování výsledků testů do Team Foundation Server použijte poskytovatele protokolovacího nástroje `TfsPublisher`:</span><span class="sxs-lookup"><span data-stu-id="c8b64-135">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="c8b64-136">Chcete-li protokolovat výsledky do souboru sady Visual Studio Výsledky testů (TRX), použijte poskytovatele protokolovacího nástroje `trx`.</span><span class="sxs-lookup"><span data-stu-id="c8b64-136">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="c8b64-137">Tento přepínač vytvoří soubor v adresáři výsledků testu s daným názvem souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="c8b64-137">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="c8b64-138">Pokud `LogFileName` není k dispozici, vytvoří se jedinečný název souboru, který bude obsahovat výsledky testu.</span><span class="sxs-lookup"><span data-stu-id="c8b64-138">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```console
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="c8b64-139">Zobrazí všechny zjištěné testy z daného kontejneru testů.</span><span class="sxs-lookup"><span data-stu-id="c8b64-139">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="c8b64-140">ID procesu nadřazeného procesu zodpovědného za spuštění aktuálního procesu.</span><span class="sxs-lookup"><span data-stu-id="c8b64-140">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="c8b64-141">Určuje port pro připojení soketu a příjem zpráv událostí.</span><span class="sxs-lookup"><span data-stu-id="c8b64-141">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="c8b64-142">Povolí podrobné protokoly pro testovací platformu.</span><span class="sxs-lookup"><span data-stu-id="c8b64-142">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="c8b64-143">Protokoly se zapisují do poskytnutého souboru.</span><span class="sxs-lookup"><span data-stu-id="c8b64-143">Logs are written to the provided file.</span></span>

`--Blame|/Blame`

<span data-ttu-id="c8b64-144">Spustí testy v režimu viny.</span><span class="sxs-lookup"><span data-stu-id="c8b64-144">Runs the tests in blame mode.</span></span> <span data-ttu-id="c8b64-145">Tato možnost je užitečná při izolaci problematických testů, které způsobují selhání hostitele testu.</span><span class="sxs-lookup"><span data-stu-id="c8b64-145">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="c8b64-146">Vytvoří výstupní soubor v aktuálním adresáři jako *Sequence. XML* , který zachycuje pořadí spuštění testů před selháním.</span><span class="sxs-lookup"><span data-stu-id="c8b64-146">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`--InIsolation|/InIsolation`

<span data-ttu-id="c8b64-147">Spustí testy v izolovaném procesu.</span><span class="sxs-lookup"><span data-stu-id="c8b64-147">Runs the tests in an isolated process.</span></span> <span data-ttu-id="c8b64-148">Díky tomu je proces *VSTest. Console. exe* méně pravděpodobný při chybě v testech zastavit, ale testy mohou běžet pomaleji.</span><span class="sxs-lookup"><span data-stu-id="c8b64-148">This makes *vstest.console.exe* process less likely to be stopped on an error in the tests, but tests may run slower.</span></span>

`@<file>`

<span data-ttu-id="c8b64-149">Přečte soubor odpovědí pro další možnosti.</span><span class="sxs-lookup"><span data-stu-id="c8b64-149">Reads response file for more options.</span></span>

`args`

<span data-ttu-id="c8b64-150">Určuje nadbytečné argumenty, které se mají předat adaptéru.</span><span class="sxs-lookup"><span data-stu-id="c8b64-150">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="c8b64-151">Argumenty jsou zadány jako páry název-hodnota `<n>=<v>`formuláře, kde `<n>` je název argumentu a `<v>` je hodnota argumentu.</span><span class="sxs-lookup"><span data-stu-id="c8b64-151">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="c8b64-152">K oddělení více argumentů použijte mezeru.</span><span class="sxs-lookup"><span data-stu-id="c8b64-152">Use a space to separate multiple arguments.</span></span>

# <a name="net-core-20"></a>[<span data-ttu-id="c8b64-153">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="c8b64-153">.NET Core 2.0</span></span>](#tab/netcore20)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="c8b64-154">Nastavení, které se má použít při spouštění testů.</span><span class="sxs-lookup"><span data-stu-id="c8b64-154">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="c8b64-155">Spustí testy s názvy, které odpovídají zadaným hodnotám.</span><span class="sxs-lookup"><span data-stu-id="c8b64-155">Run tests with names that match the provided values.</span></span> <span data-ttu-id="c8b64-156">Více hodnot oddělte čárkami.</span><span class="sxs-lookup"><span data-stu-id="c8b64-156">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="c8b64-157">Použijte vlastní testovací adaptéry z dané cesty (pokud existuje) v testovacím běhu.</span><span class="sxs-lookup"><span data-stu-id="c8b64-157">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="c8b64-158">Cílová architektura platformy použitá pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="c8b64-158">Target platform architecture used for test execution.</span></span> <span data-ttu-id="c8b64-159">Platné hodnoty jsou `x86`, `x64`a `ARM`.</span><span class="sxs-lookup"><span data-stu-id="c8b64-159">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="c8b64-160">Cílová verze .NET Framework používaná pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="c8b64-160">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="c8b64-161">Příklady platných hodnot jsou `.NETFramework,Version=v4.6` nebo `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="c8b64-161">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="c8b64-162">Další podporované hodnoty jsou `Framework40`, `Framework45`a `FrameworkCore10`.</span><span class="sxs-lookup"><span data-stu-id="c8b64-162">Other supported values are `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="c8b64-163">Paralelní provádění testů.</span><span class="sxs-lookup"><span data-stu-id="c8b64-163">Execute tests in parallel.</span></span> <span data-ttu-id="c8b64-164">Ve výchozím nastavení jsou všechny dostupné jádra počítače k dispozici pro použití.</span><span class="sxs-lookup"><span data-stu-id="c8b64-164">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="c8b64-165">Určete explicitní počet jader nastavením vlastnosti MaxCpuCount v uzlu RunConfiguration v souboru runsettings.</span><span class="sxs-lookup"><span data-stu-id="c8b64-165">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="c8b64-166">Spustí testy, které odpovídají danému výrazu.</span><span class="sxs-lookup"><span data-stu-id="c8b64-166">Run tests that match the given expression.</span></span> <span data-ttu-id="c8b64-167">`<Expression>` je `<property>Operator<value>[|&<Expression>]`formátu, kde operátor je jedním z `=`, `!=`nebo `~`.</span><span class="sxs-lookup"><span data-stu-id="c8b64-167">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="c8b64-168">Operátor `~` obsahuje sémantiku Contains a je použitelný pro řetězcové vlastnosti, jako je `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="c8b64-168">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="c8b64-169">`()` závorky se používají k seskupení podvýrazů.</span><span class="sxs-lookup"><span data-stu-id="c8b64-169">Parenthesis `()` are used to group subexpressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="c8b64-170">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="c8b64-170">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="c8b64-171">Zadejte protokolovací nástroj pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="c8b64-171">Specify a logger for test results.</span></span>

* <span data-ttu-id="c8b64-172">K publikování výsledků testů do Team Foundation Server použijte poskytovatele protokolovacího nástroje `TfsPublisher`:</span><span class="sxs-lookup"><span data-stu-id="c8b64-172">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="c8b64-173">Chcete-li protokolovat výsledky do souboru sady Visual Studio Výsledky testů (TRX), použijte poskytovatele protokolovacího nástroje `trx`.</span><span class="sxs-lookup"><span data-stu-id="c8b64-173">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="c8b64-174">Tento přepínač vytvoří soubor v adresáři výsledků testu s daným názvem souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="c8b64-174">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="c8b64-175">Pokud `LogFileName` není k dispozici, vytvoří se jedinečný název souboru, který bude obsahovat výsledky testu.</span><span class="sxs-lookup"><span data-stu-id="c8b64-175">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```console
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="c8b64-176">Zobrazí všechny zjištěné testy z daného kontejneru testů.</span><span class="sxs-lookup"><span data-stu-id="c8b64-176">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="c8b64-177">ID procesu nadřazeného procesu zodpovědného za spuštění aktuálního procesu.</span><span class="sxs-lookup"><span data-stu-id="c8b64-177">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="c8b64-178">Určuje port pro připojení soketu a příjem zpráv událostí.</span><span class="sxs-lookup"><span data-stu-id="c8b64-178">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="c8b64-179">Povolí podrobné protokoly pro testovací platformu.</span><span class="sxs-lookup"><span data-stu-id="c8b64-179">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="c8b64-180">Protokoly se zapisují do poskytnutého souboru.</span><span class="sxs-lookup"><span data-stu-id="c8b64-180">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="c8b64-181">Určuje nadbytečné argumenty, které se mají předat adaptéru.</span><span class="sxs-lookup"><span data-stu-id="c8b64-181">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="c8b64-182">Argumenty jsou zadány jako páry název-hodnota `<n>=<v>`formuláře, kde `<n>` je název argumentu a `<v>` je hodnota argumentu.</span><span class="sxs-lookup"><span data-stu-id="c8b64-182">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="c8b64-183">K oddělení více argumentů použijte mezeru.</span><span class="sxs-lookup"><span data-stu-id="c8b64-183">Use a space to separate multiple arguments.</span></span>

# <a name="net-core-1x"></a>[<span data-ttu-id="c8b64-184">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="c8b64-184">.NET Core 1.x</span></span>](#tab/netcore1x)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="c8b64-185">Nastavení, které se má použít při spouštění testů.</span><span class="sxs-lookup"><span data-stu-id="c8b64-185">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="c8b64-186">Spustí testy s názvy, které odpovídají zadaným hodnotám.</span><span class="sxs-lookup"><span data-stu-id="c8b64-186">Run tests with names that match the provided values.</span></span> <span data-ttu-id="c8b64-187">Více hodnot oddělte čárkami.</span><span class="sxs-lookup"><span data-stu-id="c8b64-187">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="c8b64-188">Použijte vlastní testovací adaptéry z dané cesty (pokud existuje) v testovacím běhu.</span><span class="sxs-lookup"><span data-stu-id="c8b64-188">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="c8b64-189">Cílová architektura platformy použitá pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="c8b64-189">Target platform architecture used for test execution.</span></span> <span data-ttu-id="c8b64-190">Platné hodnoty jsou `x86`, `x64`a `ARM`.</span><span class="sxs-lookup"><span data-stu-id="c8b64-190">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="c8b64-191">Cílová verze .NET Framework používaná pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="c8b64-191">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="c8b64-192">Příklady platných hodnot jsou `.NETFramework,Version=v4.6` nebo `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="c8b64-192">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="c8b64-193">Další podporované hodnoty jsou `Framework40`, `Framework45`a `FrameworkCore10`.</span><span class="sxs-lookup"><span data-stu-id="c8b64-193">Other supported values are `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="c8b64-194">Paralelní provádění testů.</span><span class="sxs-lookup"><span data-stu-id="c8b64-194">Execute tests in parallel.</span></span> <span data-ttu-id="c8b64-195">Ve výchozím nastavení jsou všechny dostupné jádra počítače k dispozici pro použití.</span><span class="sxs-lookup"><span data-stu-id="c8b64-195">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="c8b64-196">Určete explicitní počet jader nastavením vlastnosti MaxCpuCount v uzlu RunConfiguration v souboru runsettings.</span><span class="sxs-lookup"><span data-stu-id="c8b64-196">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="c8b64-197">Spustí testy, které odpovídají danému výrazu.</span><span class="sxs-lookup"><span data-stu-id="c8b64-197">Run tests that match the given expression.</span></span> <span data-ttu-id="c8b64-198">`<Expression>` je `<property>Operator<value>[|&<Expression>]`formátu, kde operátor je jedním z `=`, `!=`nebo `~`.</span><span class="sxs-lookup"><span data-stu-id="c8b64-198">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="c8b64-199">Operátor `~` obsahuje sémantiku Contains a je použitelný pro řetězcové vlastnosti, jako je `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="c8b64-199">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="c8b64-200">`()` závorky se používají k seskupení podvýrazů.</span><span class="sxs-lookup"><span data-stu-id="c8b64-200">Parenthesis `()` are used to group subexpressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="c8b64-201">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="c8b64-201">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="c8b64-202">Zadejte protokolovací nástroj pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="c8b64-202">Specify a logger for test results.</span></span>

* <span data-ttu-id="c8b64-203">K publikování výsledků testů do Team Foundation Server použijte poskytovatele protokolovacího nástroje `TfsPublisher`:</span><span class="sxs-lookup"><span data-stu-id="c8b64-203">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="c8b64-204">Chcete-li protokolovat výsledky do souboru sady Visual Studio Výsledky testů (TRX), použijte poskytovatele protokolovacího nástroje `trx`.</span><span class="sxs-lookup"><span data-stu-id="c8b64-204">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="c8b64-205">Tento přepínač vytvoří soubor v adresáři výsledků testu s daným názvem souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="c8b64-205">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="c8b64-206">Pokud `LogFileName` není k dispozici, vytvoří se jedinečný název souboru, který bude obsahovat výsledky testu.</span><span class="sxs-lookup"><span data-stu-id="c8b64-206">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```console
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="c8b64-207">Zobrazí všechny zjištěné testy z daného kontejneru testů.</span><span class="sxs-lookup"><span data-stu-id="c8b64-207">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="c8b64-208">ID procesu nadřazeného procesu zodpovědného za spuštění aktuálního procesu.</span><span class="sxs-lookup"><span data-stu-id="c8b64-208">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="c8b64-209">Určuje port pro připojení soketu a příjem zpráv událostí.</span><span class="sxs-lookup"><span data-stu-id="c8b64-209">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="c8b64-210">Povolí podrobné protokoly pro testovací platformu.</span><span class="sxs-lookup"><span data-stu-id="c8b64-210">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="c8b64-211">Protokoly se zapisují do poskytnutého souboru.</span><span class="sxs-lookup"><span data-stu-id="c8b64-211">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="c8b64-212">Určuje nadbytečné argumenty, které se mají předat adaptéru.</span><span class="sxs-lookup"><span data-stu-id="c8b64-212">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="c8b64-213">Argumenty jsou zadány jako páry název-hodnota `<n>=<v>`formuláře, kde `<n>` je název argumentu a `<v>` je hodnota argumentu.</span><span class="sxs-lookup"><span data-stu-id="c8b64-213">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="c8b64-214">K oddělení více argumentů použijte mezeru.</span><span class="sxs-lookup"><span data-stu-id="c8b64-214">Use a space to separate multiple arguments.</span></span>

---

## <a name="examples"></a><span data-ttu-id="c8b64-215">Příklady</span><span class="sxs-lookup"><span data-stu-id="c8b64-215">Examples</span></span>

<span data-ttu-id="c8b64-216">Spustit testy v `mytestproject.dll`:</span><span class="sxs-lookup"><span data-stu-id="c8b64-216">Run tests in `mytestproject.dll`:</span></span>

`dotnet vstest mytestproject.dll`

<span data-ttu-id="c8b64-217">Spustit testy v `mytestproject.dll`, exportovat do vlastní složky s vlastním názvem:</span><span class="sxs-lookup"><span data-stu-id="c8b64-217">Run tests in `mytestproject.dll`, exporting to custom folder with custom name:</span></span>

`dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path`

<span data-ttu-id="c8b64-218">Spustit testy v `mytestproject.dll` a `myothertestproject.exe`:</span><span class="sxs-lookup"><span data-stu-id="c8b64-218">Run tests in `mytestproject.dll` and `myothertestproject.exe`:</span></span>

`dotnet vstest mytestproject.dll myothertestproject.exe`

<span data-ttu-id="c8b64-219">Spustit `TestMethod1` testy:</span><span class="sxs-lookup"><span data-stu-id="c8b64-219">Run `TestMethod1` tests:</span></span>

`dotnet vstest /Tests:TestMethod1`

<span data-ttu-id="c8b64-220">Spustit `TestMethod1` a `TestMethod2` testy:</span><span class="sxs-lookup"><span data-stu-id="c8b64-220">Run `TestMethod1` and `TestMethod2` tests:</span></span>

`dotnet vstest /Tests:TestMethod1,TestMethod2`
