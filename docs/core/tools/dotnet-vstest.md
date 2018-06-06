---
title: příkaz vstest DotNet - .NET Core rozhraní příkazového řádku
description: Příkaz vstest dotnet sestavení projektu a všechny jeho závislé součásti.
author: guardrex
ms.author: mairaw
ms.date: 05/30/2018
ms.openlocfilehash: 84b9d9eebfbf20fefe8153dd3ae9bec0f34986c8
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696335"
---
# <a name="dotnet-vstest"></a><span data-ttu-id="9590e-103">vstest DotNet.</span><span class="sxs-lookup"><span data-stu-id="9590e-103">dotnet vstest</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="9590e-104">Název</span><span class="sxs-lookup"><span data-stu-id="9590e-104">Name</span></span>

<span data-ttu-id="9590e-105">`dotnet-vstest` -Spustí testy ze zadané soubory.</span><span class="sxs-lookup"><span data-stu-id="9590e-105">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9590e-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="9590e-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="9590e-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="9590e-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [--Blame|/Blame] [--InIsolation|/InIsolation]
    [[--] <args>...]] [-?|--Help|/?|/Help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="9590e-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="9590e-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] 
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="9590e-109">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="9590e-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] 
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```
---

## <a name="description"></a><span data-ttu-id="9590e-110">Popis</span><span class="sxs-lookup"><span data-stu-id="9590e-110">Description</span></span>

<span data-ttu-id="9590e-111">`dotnet-vstest` Příkaz spustí `VSTest.Console` aplikace příkazového řádku spouštět automatizované částí a programové testy uživatelského rozhraní aplikace.</span><span class="sxs-lookup"><span data-stu-id="9590e-111">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit and coded UI application tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="9590e-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="9590e-112">Arguments</span></span>

`TEST_FILE_NAMES`

<span data-ttu-id="9590e-113">Spouštění testů ze zadaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="9590e-113">Run tests from the specified assemblies.</span></span> <span data-ttu-id="9590e-114">Názvy sestavení více testovací oddělte mezerou.</span><span class="sxs-lookup"><span data-stu-id="9590e-114">Separate multiple test assembly names with spaces.</span></span>

## <a name="options"></a><span data-ttu-id="9590e-115">Možnosti</span><span class="sxs-lookup"><span data-stu-id="9590e-115">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="9590e-116">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="9590e-116">.NET Core 2.1</span></span>](#tab/netcore21)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="9590e-117">Nastavení se má použít při spouštění testů.</span><span class="sxs-lookup"><span data-stu-id="9590e-117">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="9590e-118">Spouštění testů pomocí názvy, které odpovídají zadaným hodnotám.</span><span class="sxs-lookup"><span data-stu-id="9590e-118">Run tests with names that match the provided values.</span></span> <span data-ttu-id="9590e-119">Více hodnot oddělujte čárkami.</span><span class="sxs-lookup"><span data-stu-id="9590e-119">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="9590e-120">Použijte vlastní test adaptéry z dané cesty (pokud existuje) v testovacím běhu.</span><span class="sxs-lookup"><span data-stu-id="9590e-120">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="9590e-121">Architektura platformy cíl používá pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="9590e-121">Target platform architecture used for test execution.</span></span> <span data-ttu-id="9590e-122">Platné hodnoty jsou `x86`, `x64`, a `ARM`.</span><span class="sxs-lookup"><span data-stu-id="9590e-122">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="9590e-123">Cílová verze rozhraní .NET Framework používá pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="9590e-123">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="9590e-124">Příklady platných hodnot `.NETFramework,Version=v4.6` nebo `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="9590e-124">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="9590e-125">Jiné podporované hodnoty jsou `Framework35`, `Framework40`, `Framework45`, `FrameworkCore10`, a `FrameworkUap10`.</span><span class="sxs-lookup"><span data-stu-id="9590e-125">Other supported values are `Framework35`, `Framework40`, `Framework45`, `FrameworkCore10`, and `FrameworkUap10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="9590e-126">Spustíte testy paralelně.</span><span class="sxs-lookup"><span data-stu-id="9590e-126">Execute tests in parallel.</span></span> <span data-ttu-id="9590e-127">Standardně jsou všechny dostupné jader na počítači k dispozici pro použití.</span><span class="sxs-lookup"><span data-stu-id="9590e-127">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="9590e-128">Soubor nastavení nastavte explicitní počet jader.</span><span class="sxs-lookup"><span data-stu-id="9590e-128">Set an explicit number of cores with a settings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="9590e-129">Testy, které odpovídají daného výrazu.</span><span class="sxs-lookup"><span data-stu-id="9590e-129">Run tests that match the given expression.</span></span> <span data-ttu-id="9590e-130">`<Expression>` je ve formátu `<property>Operator<value>[|&<Expression>]`, kde operátor je jedním z `=`, `!=`, nebo `~`.</span><span class="sxs-lookup"><span data-stu-id="9590e-130">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="9590e-131">Operátor `~` má "obsahuje" sémantiku a použít u vlastnosti řetězce jako `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="9590e-131">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="9590e-132">Závorky `()` se používají k dílčí výrazy skupiny.</span><span class="sxs-lookup"><span data-stu-id="9590e-132">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="9590e-133">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="9590e-133">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="9590e-134">Zadejte protokolovacího nástroje pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="9590e-134">Specify a logger for test results.</span></span>

* <span data-ttu-id="9590e-135">K publikování výsledků testů pro Team Foundation Server, použijte `TfsPublisher` protokolovač zprostředkovatele:</span><span class="sxs-lookup"><span data-stu-id="9590e-135">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="9590e-136">Do protokolu výsledky do Visual Studio Test výsledky souboru (TRX), použijte `trx` zprostředkovatele protokolovacího nástroje.</span><span class="sxs-lookup"><span data-stu-id="9590e-136">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="9590e-137">Tento přepínač vytvoří soubor ve výsledcích testu adresáři s zadaný název souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="9590e-137">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="9590e-138">Pokud `LogFileName` není zadaný jedinečný název souboru je vytvořen za účelem uchovávání výsledků testů.</span><span class="sxs-lookup"><span data-stu-id="9590e-138">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="9590e-139">Zobrazí seznam všech zjištěných testů z daného testovacího kontejneru.</span><span class="sxs-lookup"><span data-stu-id="9590e-139">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="9590e-140">ID procesu nadřazené zodpovědná za spuštění aktuálním procesu.</span><span class="sxs-lookup"><span data-stu-id="9590e-140">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="9590e-141">Určuje port pro připojení soketu a přijímat zprávy o událostech.</span><span class="sxs-lookup"><span data-stu-id="9590e-141">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="9590e-142">Umožňuje podrobné protokoly pro platformu testu.</span><span class="sxs-lookup"><span data-stu-id="9590e-142">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="9590e-143">Protokoly se zapisují do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="9590e-143">Logs are written to the provided file.</span></span>

`--Blame|/Blame`

<span data-ttu-id="9590e-144">Testy se spustí v režimu viny.</span><span class="sxs-lookup"><span data-stu-id="9590e-144">Runs the tests in blame mode.</span></span> <span data-ttu-id="9590e-145">Tato možnost je užitečná v izolace problematické testy způsobuje testovacího hostitele k chybě.</span><span class="sxs-lookup"><span data-stu-id="9590e-145">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="9590e-146">Vytvoří výstupní soubor v aktuálním adresáři jako *Sequence.xml* který zachycuje pořadí provádění testů před havárii.</span><span class="sxs-lookup"><span data-stu-id="9590e-146">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`--InIsolation|/InIsolation`

<span data-ttu-id="9590e-147">Spouští testy v izolovaném procesu.</span><span class="sxs-lookup"><span data-stu-id="9590e-147">Runs the tests in an isolated process.</span></span> <span data-ttu-id="9590e-148">Díky tomu *vstest.console.exe* zpracování méně pravděpodobně na chybu v testech zastavit, ale testy může pracovat pomaleji.</span><span class="sxs-lookup"><span data-stu-id="9590e-148">This makes *vstest.console.exe* process less likely to be stopped on an error in the tests, but tests may run slower.</span></span>

`@<file>`

<span data-ttu-id="9590e-149">Přečte soubor odpovědí pro další možnosti.</span><span class="sxs-lookup"><span data-stu-id="9590e-149">Reads response file for more options.</span></span>


`args`

<span data-ttu-id="9590e-150">Určuje další argumenty pro adaptér.</span><span class="sxs-lookup"><span data-stu-id="9590e-150">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="9590e-151">Argumenty nejsou zadány jako dvojice název hodnota ve formátu `<n>=<v>`, kde `<n>` je název argument a `<v>` je hodnota argumentu.</span><span class="sxs-lookup"><span data-stu-id="9590e-151">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="9590e-152">Prostor používejte k oddělení více argumentů.</span><span class="sxs-lookup"><span data-stu-id="9590e-152">Use a space to separate multiple arguments.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="9590e-153">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="9590e-153">.NET Core 2.0</span></span>](#tab/netcore20)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="9590e-154">Nastavení se má použít při spouštění testů.</span><span class="sxs-lookup"><span data-stu-id="9590e-154">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="9590e-155">Spouštění testů pomocí názvy, které odpovídají zadaným hodnotám.</span><span class="sxs-lookup"><span data-stu-id="9590e-155">Run tests with names that match the provided values.</span></span> <span data-ttu-id="9590e-156">Více hodnot oddělujte čárkami.</span><span class="sxs-lookup"><span data-stu-id="9590e-156">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="9590e-157">Použijte vlastní test adaptéry z dané cesty (pokud existuje) v testovacím běhu.</span><span class="sxs-lookup"><span data-stu-id="9590e-157">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="9590e-158">Architektura platformy cíl používá pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="9590e-158">Target platform architecture used for test execution.</span></span> <span data-ttu-id="9590e-159">Platné hodnoty jsou `x86`, `x64`, a `ARM`.</span><span class="sxs-lookup"><span data-stu-id="9590e-159">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="9590e-160">Cílová verze rozhraní .NET Framework používá pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="9590e-160">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="9590e-161">Příklady platných hodnot `.NETFramework,Version=v4.6` nebo `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="9590e-161">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="9590e-162">Jiné podporované hodnoty jsou `Framework35`, `Framework40`, `Framework45`, a `FrameworkCore10`.</span><span class="sxs-lookup"><span data-stu-id="9590e-162">Other supported values are `Framework35`, `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="9590e-163">Spustíte testy paralelně.</span><span class="sxs-lookup"><span data-stu-id="9590e-163">Execute tests in parallel.</span></span> <span data-ttu-id="9590e-164">Standardně jsou všechny dostupné jader na počítači k dispozici pro použití.</span><span class="sxs-lookup"><span data-stu-id="9590e-164">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="9590e-165">Soubor nastavení nastavte explicitní počet jader.</span><span class="sxs-lookup"><span data-stu-id="9590e-165">Set an explicit number of cores with a settings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="9590e-166">Testy, které odpovídají daného výrazu.</span><span class="sxs-lookup"><span data-stu-id="9590e-166">Run tests that match the given expression.</span></span> <span data-ttu-id="9590e-167">`<Expression>` je ve formátu `<property>Operator<value>[|&<Expression>]`, kde operátor je jedním z `=`, `!=`, nebo `~`.</span><span class="sxs-lookup"><span data-stu-id="9590e-167">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="9590e-168">Operátor `~` má "obsahuje" sémantiku a použít u vlastnosti řetězce jako `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="9590e-168">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="9590e-169">Závorky `()` se používají k dílčí výrazy skupiny.</span><span class="sxs-lookup"><span data-stu-id="9590e-169">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="9590e-170">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="9590e-170">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="9590e-171">Zadejte protokolovacího nástroje pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="9590e-171">Specify a logger for test results.</span></span>

* <span data-ttu-id="9590e-172">K publikování výsledků testů pro Team Foundation Server, použijte `TfsPublisher` protokolovač zprostředkovatele:</span><span class="sxs-lookup"><span data-stu-id="9590e-172">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="9590e-173">Do protokolu výsledky do Visual Studio Test výsledky souboru (TRX), použijte `trx` zprostředkovatele protokolovacího nástroje.</span><span class="sxs-lookup"><span data-stu-id="9590e-173">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="9590e-174">Tento přepínač vytvoří soubor ve výsledcích testu adresáři s zadaný název souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="9590e-174">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="9590e-175">Pokud `LogFileName` není zadaný jedinečný název souboru je vytvořen za účelem uchovávání výsledků testů.</span><span class="sxs-lookup"><span data-stu-id="9590e-175">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="9590e-176">Zobrazí seznam všech zjištěných testů z daného testovacího kontejneru.</span><span class="sxs-lookup"><span data-stu-id="9590e-176">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="9590e-177">ID procesu nadřazené zodpovědná za spuštění aktuálním procesu.</span><span class="sxs-lookup"><span data-stu-id="9590e-177">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="9590e-178">Určuje port pro připojení soketu a přijímat zprávy o událostech.</span><span class="sxs-lookup"><span data-stu-id="9590e-178">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="9590e-179">Umožňuje podrobné protokoly pro platformu testu.</span><span class="sxs-lookup"><span data-stu-id="9590e-179">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="9590e-180">Protokoly se zapisují do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="9590e-180">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="9590e-181">Určuje další argumenty pro adaptér.</span><span class="sxs-lookup"><span data-stu-id="9590e-181">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="9590e-182">Argumenty nejsou zadány jako dvojice název hodnota ve formátu `<n>=<v>`, kde `<n>` je název argument a `<v>` je hodnota argumentu.</span><span class="sxs-lookup"><span data-stu-id="9590e-182">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="9590e-183">Prostor používejte k oddělení více argumentů.</span><span class="sxs-lookup"><span data-stu-id="9590e-183">Use a space to separate multiple arguments.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="9590e-184">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="9590e-184">.NET Core 1.x</span></span>](#tab/netcore1x)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="9590e-185">Nastavení se má použít při spouštění testů.</span><span class="sxs-lookup"><span data-stu-id="9590e-185">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="9590e-186">Spouštění testů pomocí názvy, které odpovídají zadaným hodnotám.</span><span class="sxs-lookup"><span data-stu-id="9590e-186">Run tests with names that match the provided values.</span></span> <span data-ttu-id="9590e-187">Více hodnot oddělujte čárkami.</span><span class="sxs-lookup"><span data-stu-id="9590e-187">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="9590e-188">Použijte vlastní test adaptéry z dané cesty (pokud existuje) v testovacím běhu.</span><span class="sxs-lookup"><span data-stu-id="9590e-188">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="9590e-189">Architektura platformy cíl používá pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="9590e-189">Target platform architecture used for test execution.</span></span> <span data-ttu-id="9590e-190">Platné hodnoty jsou `x86`, `x64`, a `ARM`.</span><span class="sxs-lookup"><span data-stu-id="9590e-190">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="9590e-191">Cílová verze rozhraní .NET Framework používá pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="9590e-191">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="9590e-192">Příklady platných hodnot `.NETFramework,Version=v4.6` nebo `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="9590e-192">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="9590e-193">Jiné podporované hodnoty jsou `Framework35`, `Framework40`, `Framework45`, a `FrameworkCore10`.</span><span class="sxs-lookup"><span data-stu-id="9590e-193">Other supported values are `Framework35`, `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="9590e-194">Spustíte testy paralelně.</span><span class="sxs-lookup"><span data-stu-id="9590e-194">Execute tests in parallel.</span></span> <span data-ttu-id="9590e-195">Standardně jsou všechny dostupné jader na počítači k dispozici pro použití.</span><span class="sxs-lookup"><span data-stu-id="9590e-195">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="9590e-196">Soubor nastavení nastavte explicitní počet jader.</span><span class="sxs-lookup"><span data-stu-id="9590e-196">Set an explicit number of cores with a settings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="9590e-197">Testy, které odpovídají daného výrazu.</span><span class="sxs-lookup"><span data-stu-id="9590e-197">Run tests that match the given expression.</span></span> <span data-ttu-id="9590e-198">`<Expression>` je ve formátu `<property>Operator<value>[|&<Expression>]`, kde operátor je jedním z `=`, `!=`, nebo `~`.</span><span class="sxs-lookup"><span data-stu-id="9590e-198">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="9590e-199">Operátor `~` má "obsahuje" sémantiku a použít u vlastnosti řetězce jako `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="9590e-199">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="9590e-200">Závorky `()` se používají k dílčí výrazy skupiny.</span><span class="sxs-lookup"><span data-stu-id="9590e-200">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="9590e-201">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="9590e-201">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="9590e-202">Zadejte protokolovacího nástroje pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="9590e-202">Specify a logger for test results.</span></span>

* <span data-ttu-id="9590e-203">K publikování výsledků testů pro Team Foundation Server, použijte `TfsPublisher` protokolovač zprostředkovatele:</span><span class="sxs-lookup"><span data-stu-id="9590e-203">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="9590e-204">Do protokolu výsledky do Visual Studio Test výsledky souboru (TRX), použijte `trx` zprostředkovatele protokolovacího nástroje.</span><span class="sxs-lookup"><span data-stu-id="9590e-204">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="9590e-205">Tento přepínač vytvoří soubor ve výsledcích testu adresáři s zadaný název souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="9590e-205">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="9590e-206">Pokud `LogFileName` není zadaný jedinečný název souboru je vytvořen za účelem uchovávání výsledků testů.</span><span class="sxs-lookup"><span data-stu-id="9590e-206">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="9590e-207">Zobrazí seznam všech zjištěných testů z daného testovacího kontejneru.</span><span class="sxs-lookup"><span data-stu-id="9590e-207">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="9590e-208">ID procesu nadřazené zodpovědná za spuštění aktuálním procesu.</span><span class="sxs-lookup"><span data-stu-id="9590e-208">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="9590e-209">Určuje port pro připojení soketu a přijímat zprávy o událostech.</span><span class="sxs-lookup"><span data-stu-id="9590e-209">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="9590e-210">Umožňuje podrobné protokoly pro platformu testu.</span><span class="sxs-lookup"><span data-stu-id="9590e-210">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="9590e-211">Protokoly se zapisují do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="9590e-211">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="9590e-212">Určuje další argumenty pro adaptér.</span><span class="sxs-lookup"><span data-stu-id="9590e-212">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="9590e-213">Argumenty nejsou zadány jako dvojice název hodnota ve formátu `<n>=<v>`, kde `<n>` je název argument a `<v>` je hodnota argumentu.</span><span class="sxs-lookup"><span data-stu-id="9590e-213">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="9590e-214">Prostor používejte k oddělení více argumentů.</span><span class="sxs-lookup"><span data-stu-id="9590e-214">Use a space to separate multiple arguments.</span></span>

---

## <a name="examples"></a><span data-ttu-id="9590e-215">Příklady</span><span class="sxs-lookup"><span data-stu-id="9590e-215">Examples</span></span>

<span data-ttu-id="9590e-216">Spuštění testů `mytestproject.dll`:</span><span class="sxs-lookup"><span data-stu-id="9590e-216">Run tests in `mytestproject.dll`:</span></span>

`dotnet vstest mytestproject.dll`

<span data-ttu-id="9590e-217">Spuštění testů `mytestproject.dll`, export do vlastní složky s vlastní název:</span><span class="sxs-lookup"><span data-stu-id="9590e-217">Run tests in `mytestproject.dll`, exporting to custom folder with custom name:</span></span>

`dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path`

<span data-ttu-id="9590e-218">Spuštění testů `mytestproject.dll` a `myothertestproject.exe`:</span><span class="sxs-lookup"><span data-stu-id="9590e-218">Run tests in `mytestproject.dll` and `myothertestproject.exe`:</span></span>

`dotnet vstest mytestproject.dll myothertestproject.exe`

<span data-ttu-id="9590e-219">Spustit `TestMethod1` testů:</span><span class="sxs-lookup"><span data-stu-id="9590e-219">Run `TestMethod1` tests:</span></span>

`dotnet vstest /Tests:TestMethod1`

<span data-ttu-id="9590e-220">Spustit `TestMethod1` a `TestMethod2` testů:</span><span class="sxs-lookup"><span data-stu-id="9590e-220">Run `TestMethod1` and `TestMethod2` tests:</span></span>

`dotnet vstest /Tests:TestMethod1,TestMethod2`