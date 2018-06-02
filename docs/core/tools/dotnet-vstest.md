---
title: příkaz vstest DotNet - .NET Core rozhraní příkazového řádku
description: Příkaz vstest dotnet sestavení projektu a všechny jeho závislé součásti.
author: guardrex
ms.author: mairaw
ms.date: 05/30/2018
ms.openlocfilehash: 84b9d9eebfbf20fefe8153dd3ae9bec0f34986c8
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696335"
---
# <a name="dotnet-vstest"></a><span data-ttu-id="ca9e0-103">vstest DotNet.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-103">dotnet vstest</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="ca9e0-104">Název</span><span class="sxs-lookup"><span data-stu-id="ca9e0-104">Name</span></span>

<span data-ttu-id="ca9e0-105">`dotnet-vstest` -Spustí testy ze zadané soubory.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-105">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ca9e0-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="ca9e0-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="ca9e0-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="ca9e0-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [--Blame|/Blame] [--InIsolation|/InIsolation]
    [[--] <args>...]] [-?|--Help|/?|/Help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="ca9e0-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="ca9e0-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] 
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ca9e0-109">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="ca9e0-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] 
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```
---

## <a name="description"></a><span data-ttu-id="ca9e0-110">Popis</span><span class="sxs-lookup"><span data-stu-id="ca9e0-110">Description</span></span>

<span data-ttu-id="ca9e0-111">`dotnet-vstest` Příkaz spustí `VSTest.Console` aplikace příkazového řádku spouštět automatizované částí a programové testy uživatelského rozhraní aplikace.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-111">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit and coded UI application tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="ca9e0-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="ca9e0-112">Arguments</span></span>

`TEST_FILE_NAMES`

<span data-ttu-id="ca9e0-113">Spouštění testů ze zadaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-113">Run tests from the specified assemblies.</span></span> <span data-ttu-id="ca9e0-114">Názvy sestavení více testovací oddělte mezerou.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-114">Separate multiple test assembly names with spaces.</span></span>

## <a name="options"></a><span data-ttu-id="ca9e0-115">Možnosti</span><span class="sxs-lookup"><span data-stu-id="ca9e0-115">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="ca9e0-116">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="ca9e0-116">.NET Core 2.1</span></span>](#tab/netcore21)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="ca9e0-117">Nastavení se má použít při spouštění testů.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-117">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="ca9e0-118">Spouštění testů pomocí názvy, které odpovídají zadaným hodnotám.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-118">Run tests with names that match the provided values.</span></span> <span data-ttu-id="ca9e0-119">Více hodnot oddělujte čárkami.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-119">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="ca9e0-120">Použijte vlastní test adaptéry z dané cesty (pokud existuje) v testovacím běhu.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-120">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="ca9e0-121">Architektura platformy cíl používá pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-121">Target platform architecture used for test execution.</span></span> <span data-ttu-id="ca9e0-122">Platné hodnoty jsou `x86`, `x64`, a `ARM`.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-122">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="ca9e0-123">Cílová verze rozhraní .NET Framework používá pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-123">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="ca9e0-124">Příklady platných hodnot `.NETFramework,Version=v4.6` nebo `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-124">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="ca9e0-125">Jiné podporované hodnoty jsou `Framework35`, `Framework40`, `Framework45`, `FrameworkCore10`, a `FrameworkUap10`.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-125">Other supported values are `Framework35`, `Framework40`, `Framework45`, `FrameworkCore10`, and `FrameworkUap10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="ca9e0-126">Spustíte testy paralelně.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-126">Execute tests in parallel.</span></span> <span data-ttu-id="ca9e0-127">Standardně jsou všechny dostupné jader na počítači k dispozici pro použití.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-127">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="ca9e0-128">Soubor nastavení nastavte explicitní počet jader.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-128">Set an explicit number of cores with a settings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="ca9e0-129">Testy, které odpovídají daného výrazu.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-129">Run tests that match the given expression.</span></span> <span data-ttu-id="ca9e0-130">`<Expression>` je ve formátu `<property>Operator<value>[|&<Expression>]`, kde operátor je jedním z `=`, `!=`, nebo `~`.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-130">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="ca9e0-131">Operátor `~` má "obsahuje" sémantiku a použít u vlastnosti řetězce jako `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-131">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="ca9e0-132">Závorky `()` se používají k dílčí výrazy skupiny.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-132">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="ca9e0-133">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-133">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="ca9e0-134">Zadejte protokolovacího nástroje pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-134">Specify a logger for test results.</span></span>

* <span data-ttu-id="ca9e0-135">K publikování výsledků testů pro Team Foundation Server, použijte `TfsPublisher` protokolovač zprostředkovatele:</span><span class="sxs-lookup"><span data-stu-id="ca9e0-135">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="ca9e0-136">Do protokolu výsledky do Visual Studio Test výsledky souboru (TRX), použijte `trx` zprostředkovatele protokolovacího nástroje.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-136">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="ca9e0-137">Tento přepínač vytvoří soubor ve výsledcích testu adresáři s zadaný název souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-137">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="ca9e0-138">Pokud `LogFileName` není zadaný jedinečný název souboru je vytvořen za účelem uchovávání výsledků testů.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-138">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="ca9e0-139">Zobrazí seznam všech zjištěných testů z daného testovacího kontejneru.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-139">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="ca9e0-140">ID procesu nadřazené zodpovědná za spuštění aktuálním procesu.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-140">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="ca9e0-141">Určuje port pro připojení soketu a přijímat zprávy o událostech.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-141">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="ca9e0-142">Umožňuje podrobné protokoly pro platformu testu.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-142">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="ca9e0-143">Protokoly se zapisují do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-143">Logs are written to the provided file.</span></span>

`--Blame|/Blame`

<span data-ttu-id="ca9e0-144">Testy se spustí v režimu viny.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-144">Runs the tests in blame mode.</span></span> <span data-ttu-id="ca9e0-145">Tato možnost je užitečná v izolace problematické testy způsobuje testovacího hostitele k chybě.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-145">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="ca9e0-146">Vytvoří výstupní soubor v aktuálním adresáři jako *Sequence.xml* který zachycuje pořadí provádění testů před havárii.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-146">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`--InIsolation|/InIsolation`

<span data-ttu-id="ca9e0-147">Spouští testy v izolovaném procesu.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-147">Runs the tests in an isolated process.</span></span> <span data-ttu-id="ca9e0-148">Díky tomu *vstest.console.exe* zpracování méně pravděpodobně na chybu v testech zastavit, ale testy může pracovat pomaleji.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-148">This makes *vstest.console.exe* process less likely to be stopped on an error in the tests, but tests may run slower.</span></span>

`@<file>`

<span data-ttu-id="ca9e0-149">Přečte soubor odpovědí pro další možnosti.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-149">Reads response file for more options.</span></span>


`args`

<span data-ttu-id="ca9e0-150">Určuje další argumenty pro adaptér.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-150">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="ca9e0-151">Argumenty nejsou zadány jako dvojice název hodnota ve formátu `<n>=<v>`, kde `<n>` je název argument a `<v>` je hodnota argumentu.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-151">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="ca9e0-152">Prostor používejte k oddělení více argumentů.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-152">Use a space to separate multiple arguments.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="ca9e0-153">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="ca9e0-153">.NET Core 2.0</span></span>](#tab/netcore20)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="ca9e0-154">Nastavení se má použít při spouštění testů.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-154">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="ca9e0-155">Spouštění testů pomocí názvy, které odpovídají zadaným hodnotám.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-155">Run tests with names that match the provided values.</span></span> <span data-ttu-id="ca9e0-156">Více hodnot oddělujte čárkami.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-156">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="ca9e0-157">Použijte vlastní test adaptéry z dané cesty (pokud existuje) v testovacím běhu.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-157">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="ca9e0-158">Architektura platformy cíl používá pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-158">Target platform architecture used for test execution.</span></span> <span data-ttu-id="ca9e0-159">Platné hodnoty jsou `x86`, `x64`, a `ARM`.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-159">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="ca9e0-160">Cílová verze rozhraní .NET Framework používá pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-160">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="ca9e0-161">Příklady platných hodnot `.NETFramework,Version=v4.6` nebo `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-161">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="ca9e0-162">Jiné podporované hodnoty jsou `Framework35`, `Framework40`, `Framework45`, a `FrameworkCore10`.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-162">Other supported values are `Framework35`, `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="ca9e0-163">Spustíte testy paralelně.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-163">Execute tests in parallel.</span></span> <span data-ttu-id="ca9e0-164">Standardně jsou všechny dostupné jader na počítači k dispozici pro použití.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-164">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="ca9e0-165">Soubor nastavení nastavte explicitní počet jader.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-165">Set an explicit number of cores with a settings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="ca9e0-166">Testy, které odpovídají daného výrazu.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-166">Run tests that match the given expression.</span></span> <span data-ttu-id="ca9e0-167">`<Expression>` je ve formátu `<property>Operator<value>[|&<Expression>]`, kde operátor je jedním z `=`, `!=`, nebo `~`.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-167">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="ca9e0-168">Operátor `~` má "obsahuje" sémantiku a použít u vlastnosti řetězce jako `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-168">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="ca9e0-169">Závorky `()` se používají k dílčí výrazy skupiny.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-169">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="ca9e0-170">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-170">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="ca9e0-171">Zadejte protokolovacího nástroje pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-171">Specify a logger for test results.</span></span>

* <span data-ttu-id="ca9e0-172">K publikování výsledků testů pro Team Foundation Server, použijte `TfsPublisher` protokolovač zprostředkovatele:</span><span class="sxs-lookup"><span data-stu-id="ca9e0-172">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="ca9e0-173">Do protokolu výsledky do Visual Studio Test výsledky souboru (TRX), použijte `trx` zprostředkovatele protokolovacího nástroje.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-173">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="ca9e0-174">Tento přepínač vytvoří soubor ve výsledcích testu adresáři s zadaný název souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-174">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="ca9e0-175">Pokud `LogFileName` není zadaný jedinečný název souboru je vytvořen za účelem uchovávání výsledků testů.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-175">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="ca9e0-176">Zobrazí seznam všech zjištěných testů z daného testovacího kontejneru.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-176">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="ca9e0-177">ID procesu nadřazené zodpovědná za spuštění aktuálním procesu.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-177">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="ca9e0-178">Určuje port pro připojení soketu a přijímat zprávy o událostech.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-178">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="ca9e0-179">Umožňuje podrobné protokoly pro platformu testu.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-179">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="ca9e0-180">Protokoly se zapisují do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-180">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="ca9e0-181">Určuje další argumenty pro adaptér.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-181">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="ca9e0-182">Argumenty nejsou zadány jako dvojice název hodnota ve formátu `<n>=<v>`, kde `<n>` je název argument a `<v>` je hodnota argumentu.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-182">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="ca9e0-183">Prostor používejte k oddělení více argumentů.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-183">Use a space to separate multiple arguments.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ca9e0-184">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="ca9e0-184">.NET Core 1.x</span></span>](#tab/netcore1x)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="ca9e0-185">Nastavení se má použít při spouštění testů.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-185">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="ca9e0-186">Spouštění testů pomocí názvy, které odpovídají zadaným hodnotám.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-186">Run tests with names that match the provided values.</span></span> <span data-ttu-id="ca9e0-187">Více hodnot oddělujte čárkami.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-187">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="ca9e0-188">Použijte vlastní test adaptéry z dané cesty (pokud existuje) v testovacím běhu.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-188">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="ca9e0-189">Architektura platformy cíl používá pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-189">Target platform architecture used for test execution.</span></span> <span data-ttu-id="ca9e0-190">Platné hodnoty jsou `x86`, `x64`, a `ARM`.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-190">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="ca9e0-191">Cílová verze rozhraní .NET Framework používá pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-191">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="ca9e0-192">Příklady platných hodnot `.NETFramework,Version=v4.6` nebo `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-192">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="ca9e0-193">Jiné podporované hodnoty jsou `Framework35`, `Framework40`, `Framework45`, a `FrameworkCore10`.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-193">Other supported values are `Framework35`, `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="ca9e0-194">Spustíte testy paralelně.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-194">Execute tests in parallel.</span></span> <span data-ttu-id="ca9e0-195">Standardně jsou všechny dostupné jader na počítači k dispozici pro použití.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-195">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="ca9e0-196">Soubor nastavení nastavte explicitní počet jader.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-196">Set an explicit number of cores with a settings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="ca9e0-197">Testy, které odpovídají daného výrazu.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-197">Run tests that match the given expression.</span></span> <span data-ttu-id="ca9e0-198">`<Expression>` je ve formátu `<property>Operator<value>[|&<Expression>]`, kde operátor je jedním z `=`, `!=`, nebo `~`.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-198">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="ca9e0-199">Operátor `~` má "obsahuje" sémantiku a použít u vlastnosti řetězce jako `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-199">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="ca9e0-200">Závorky `()` se používají k dílčí výrazy skupiny.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-200">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="ca9e0-201">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-201">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="ca9e0-202">Zadejte protokolovacího nástroje pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-202">Specify a logger for test results.</span></span>

* <span data-ttu-id="ca9e0-203">K publikování výsledků testů pro Team Foundation Server, použijte `TfsPublisher` protokolovač zprostředkovatele:</span><span class="sxs-lookup"><span data-stu-id="ca9e0-203">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="ca9e0-204">Do protokolu výsledky do Visual Studio Test výsledky souboru (TRX), použijte `trx` zprostředkovatele protokolovacího nástroje.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-204">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="ca9e0-205">Tento přepínač vytvoří soubor ve výsledcích testu adresáři s zadaný název souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-205">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="ca9e0-206">Pokud `LogFileName` není zadaný jedinečný název souboru je vytvořen za účelem uchovávání výsledků testů.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-206">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="ca9e0-207">Zobrazí seznam všech zjištěných testů z daného testovacího kontejneru.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-207">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="ca9e0-208">ID procesu nadřazené zodpovědná za spuštění aktuálním procesu.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-208">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="ca9e0-209">Určuje port pro připojení soketu a přijímat zprávy o událostech.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-209">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="ca9e0-210">Umožňuje podrobné protokoly pro platformu testu.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-210">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="ca9e0-211">Protokoly se zapisují do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-211">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="ca9e0-212">Určuje další argumenty pro adaptér.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-212">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="ca9e0-213">Argumenty nejsou zadány jako dvojice název hodnota ve formátu `<n>=<v>`, kde `<n>` je název argument a `<v>` je hodnota argumentu.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-213">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="ca9e0-214">Prostor používejte k oddělení více argumentů.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-214">Use a space to separate multiple arguments.</span></span>

---

## <a name="examples"></a><span data-ttu-id="ca9e0-215">Příklady</span><span class="sxs-lookup"><span data-stu-id="ca9e0-215">Examples</span></span>

<span data-ttu-id="ca9e0-216">Spuštění testů `mytestproject.dll`:</span><span class="sxs-lookup"><span data-stu-id="ca9e0-216">Run tests in `mytestproject.dll`:</span></span>

`dotnet vstest mytestproject.dll`

<span data-ttu-id="ca9e0-217">Spuštění testů `mytestproject.dll`, export do vlastní složky s vlastní název:</span><span class="sxs-lookup"><span data-stu-id="ca9e0-217">Run tests in `mytestproject.dll`, exporting to custom folder with custom name:</span></span>

`dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path`

<span data-ttu-id="ca9e0-218">Spuštění testů `mytestproject.dll` a `myothertestproject.exe`:</span><span class="sxs-lookup"><span data-stu-id="ca9e0-218">Run tests in `mytestproject.dll` and `myothertestproject.exe`:</span></span>

`dotnet vstest mytestproject.dll myothertestproject.exe`

<span data-ttu-id="ca9e0-219">Spustit `TestMethod1` testů:</span><span class="sxs-lookup"><span data-stu-id="ca9e0-219">Run `TestMethod1` tests:</span></span>

`dotnet vstest /Tests:TestMethod1`

<span data-ttu-id="ca9e0-220">Spustit `TestMethod1` a `TestMethod2` testů:</span><span class="sxs-lookup"><span data-stu-id="ca9e0-220">Run `TestMethod1` and `TestMethod2` tests:</span></span>

`dotnet vstest /Tests:TestMethod1,TestMethod2`