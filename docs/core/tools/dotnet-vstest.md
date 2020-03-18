---
title: dotnet vstest, příkaz
description: Dotnet vstest příkaz vytvoří projekt a všechny jeho závislosti.
ms.date: 02/27/2020
ms.openlocfilehash: 88e5b6a8966d78d0746f9ea5ccbccab142a2e0f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156930"
---
# <a name="dotnet-vstest"></a><span data-ttu-id="71972-103">dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="71972-103">dotnet vstest</span></span>

<span data-ttu-id="71972-104">**Tento článek se týká:** ✔️ .NET Core 2.1 SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="71972-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="71972-105">Name (Název)</span><span class="sxs-lookup"><span data-stu-id="71972-105">Name</span></span>

<span data-ttu-id="71972-106">`dotnet-vstest`- Spustí testy ze zadaných souborů.</span><span class="sxs-lookup"><span data-stu-id="71972-106">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="71972-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="71972-107">Synopsis</span></span>

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings] [--Tests]
    [--TestAdapterPath] [--Platform] [--Framework] [--Parallel]
    [--TestCaseFilter] [--logger] [-lt|--ListTests]
    [--ParentProcessId] [--Port] [--Diag] [--Blame]
    [--InIsolation] [[--] <args>...]] [-?|--Help]
```

## <a name="description"></a><span data-ttu-id="71972-108">Popis</span><span class="sxs-lookup"><span data-stu-id="71972-108">Description</span></span>

<span data-ttu-id="71972-109">Příkaz `dotnet-vstest` spustí `VSTest.Console` aplikaci příkazového řádku pro spuštění automatizovaných testů částí.</span><span class="sxs-lookup"><span data-stu-id="71972-109">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="71972-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="71972-110">Arguments</span></span>

- **`TEST_FILE_NAMES`**

  <span data-ttu-id="71972-111">Spusťte testy ze zadaných sestavení.</span><span class="sxs-lookup"><span data-stu-id="71972-111">Run tests from the specified assemblies.</span></span> <span data-ttu-id="71972-112">Oddělte více názvů testovacích sestavení mezerami.</span><span class="sxs-lookup"><span data-stu-id="71972-112">Separate multiple test assembly names with spaces.</span></span> <span data-ttu-id="71972-113">Zástupné znaky jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="71972-113">Wildcards are supported.</span></span>

## <a name="options"></a><span data-ttu-id="71972-114">Možnosti</span><span class="sxs-lookup"><span data-stu-id="71972-114">Options</span></span>

- **`--Settings <Settings File>`**

  <span data-ttu-id="71972-115">Nastavení, které se má použít při spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="71972-115">Settings to use when running tests.</span></span>

- **`--Tests <Test Names>`**

  <span data-ttu-id="71972-116">Spusťte testy s názvy, které odpovídají zadaným hodnotám.</span><span class="sxs-lookup"><span data-stu-id="71972-116">Run tests with names that match the provided values.</span></span> <span data-ttu-id="71972-117">Oddělte více hodnot čárkou.</span><span class="sxs-lookup"><span data-stu-id="71972-117">Separate multiple values with commas.</span></span>

- **`--TestAdapterPath`**

  <span data-ttu-id="71972-118">Při testovacím běhu použijte vlastní testovací adaptéry z dané cesty (pokud existuje).</span><span class="sxs-lookup"><span data-stu-id="71972-118">Use custom test adapters from a given path (if any) in the test run.</span></span>

- **`--Platform <Platform type>`**

  <span data-ttu-id="71972-119">Architektura cílové platformy používaná pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="71972-119">Target platform architecture used for test execution.</span></span> <span data-ttu-id="71972-120">Platné hodnoty `x86` `x64`jsou `ARM`, a .</span><span class="sxs-lookup"><span data-stu-id="71972-120">Valid values are `x86`, `x64`, and `ARM`.</span></span>

- **`--Framework <Framework Version>`**

  <span data-ttu-id="71972-121">Cílová verze rozhraní .NET Framework použitá pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="71972-121">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="71972-122">Příklady platných `.NETFramework,Version=v4.6` hodnot `.NETCoreApp,Version=v1.0`jsou nebo .</span><span class="sxs-lookup"><span data-stu-id="71972-122">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="71972-123">Další podporované `Framework40`hodnoty `Framework45` `FrameworkCore10`jsou `FrameworkUap10`, , a .</span><span class="sxs-lookup"><span data-stu-id="71972-123">Other supported values are `Framework40`, `Framework45`, `FrameworkCore10`, and `FrameworkUap10`.</span></span>

- **`--Parallel`**

  <span data-ttu-id="71972-124">Spouštět testy paralelně.</span><span class="sxs-lookup"><span data-stu-id="71972-124">Run tests in parallel.</span></span> <span data-ttu-id="71972-125">Ve výchozím nastavení jsou k dispozici všechna dostupná jádra v počítači.</span><span class="sxs-lookup"><span data-stu-id="71972-125">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="71972-126">Zadejte explicitní počet jader `MaxCpuCount` nastavením `RunConfiguration` vlastnosti pod uzlevě v souboru *runsettings.*</span><span class="sxs-lookup"><span data-stu-id="71972-126">Specify an explicit number of cores by setting the `MaxCpuCount` property under the `RunConfiguration` node in the *runsettings* file.</span></span>

- **`--TestCaseFilter <Expression>`**

  <span data-ttu-id="71972-127">Spusťte testy, které odpovídají danému výrazu.</span><span class="sxs-lookup"><span data-stu-id="71972-127">Run tests that match the given expression.</span></span> <span data-ttu-id="71972-128">`<Expression>`je ve `<property>Operator<value>[|&<Expression>]`formátu , kde `=`Operator `!=`je `~`jedním z , , nebo .</span><span class="sxs-lookup"><span data-stu-id="71972-128">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="71972-129">Operátor `~` má sémantiku "obsahuje" a `DisplayName`je použitelný pro vlastnosti řetězce, jako je .</span><span class="sxs-lookup"><span data-stu-id="71972-129">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="71972-130">Závorky `()` se používají k seskupení podvýrazů.</span><span class="sxs-lookup"><span data-stu-id="71972-130">Parenthesis `()` are used to group subexpressions.</span></span>

- **`-?|--Help`**

  <span data-ttu-id="71972-131">Vytiskne krátkou nápovědu pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="71972-131">Prints out a short help for the command.</span></span>

- **`--logger <Logger Uri/FriendlyName>`**

  <span data-ttu-id="71972-132">Zadejte protokolovací nástroj pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="71972-132">Specify a logger for test results.</span></span>

  - <span data-ttu-id="71972-133">Chcete-li publikovat výsledky testů na `TfsPublisher` serveru Team Foundation, použijte zprostředkovatele protokolování:</span><span class="sxs-lookup"><span data-stu-id="71972-133">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

    ```console
    /logger:TfsPublisher;
        Collection=<team project collection url>;
        BuildName=<build name>;
        TeamProject=<team project name>
        [;Platform=<Defaults to "Any CPU">]
        [;Flavor=<Defaults to "Debug">]
        [;RunTitle=<title>]
    ```

  - <span data-ttu-id="71972-134">Chcete-li protokolovat výsledky souboru výsledků testů `trx` sady Visual Studio (TRX), použijte zprostředkovatele protokolování.</span><span class="sxs-lookup"><span data-stu-id="71972-134">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="71972-135">Tento přepínač vytvoří soubor v adresáři výsledků testu s daným názvem souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="71972-135">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="71972-136">Pokud `LogFileName` není k dispozici, jedinečný název souboru je vytvořen pro uložení výsledků testu.</span><span class="sxs-lookup"><span data-stu-id="71972-136">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

    ```console
    /logger:trx [;LogFileName=<Defaults to unique file name>]
    ```

- **`-lt|--ListTests <File Name>`**

  <span data-ttu-id="71972-137">Zobrazí seznam všech zjištěných testů z daného testovacího kontejneru.</span><span class="sxs-lookup"><span data-stu-id="71972-137">Lists all discovered tests from the given test container.</span></span>

- **`--ParentProcessId <ParentProcessId>`**

  <span data-ttu-id="71972-138">ID procesu nadřazeného procesu odpovědného za spuštění aktuálního procesu.</span><span class="sxs-lookup"><span data-stu-id="71972-138">Process ID of the parent process responsible for launching the current process.</span></span>

- **`--Port <Port>`**

  <span data-ttu-id="71972-139">Určuje port pro připojení soketu a příjem zpráv o událostech.</span><span class="sxs-lookup"><span data-stu-id="71972-139">Specifies the port for the socket connection and receiving the event messages.</span></span>

- **`--Diag <Path to log file>`**

  <span data-ttu-id="71972-140">Povolí podrobné protokoly pro testovací platformu.</span><span class="sxs-lookup"><span data-stu-id="71972-140">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="71972-141">Protokoly jsou zapsány do dodaný soubor.</span><span class="sxs-lookup"><span data-stu-id="71972-141">Logs are written to the provided file.</span></span>

- **`--Blame`**

  <span data-ttu-id="71972-142">Spustí testy v režimu obviňování.</span><span class="sxs-lookup"><span data-stu-id="71972-142">Runs the tests in blame mode.</span></span> <span data-ttu-id="71972-143">Tato možnost je užitečná při izolaci problémových testů, které způsobují selhání testovacího hostitele.</span><span class="sxs-lookup"><span data-stu-id="71972-143">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="71972-144">Vytvoří výstupní soubor v aktuálním adresáři jako *Sequence.xml,* který zachycuje pořadí spuštění testů před selháním.</span><span class="sxs-lookup"><span data-stu-id="71972-144">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`--InIsolation`**

  <span data-ttu-id="71972-145">Spustí testy v izolovaném procesu.</span><span class="sxs-lookup"><span data-stu-id="71972-145">Runs the tests in an isolated process.</span></span> <span data-ttu-id="71972-146">Díky *vstest.console.exe* proces méně pravděpodobné, že bude zastaven a na chybu v testech, ale testy mohou běžet pomaleji.</span><span class="sxs-lookup"><span data-stu-id="71972-146">This makes *vstest.console.exe* process less likely to be stopped on an error in the tests, but tests may run slower.</span></span>

- **`@<file>`**

  <span data-ttu-id="71972-147">Přečte soubor odpovědí pro další možnosti.</span><span class="sxs-lookup"><span data-stu-id="71972-147">Reads response file for more options.</span></span>

- **`args`**

  <span data-ttu-id="71972-148">Určuje další argumenty, které mají být předávány adaptéru.</span><span class="sxs-lookup"><span data-stu-id="71972-148">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="71972-149">Argumenty jsou určeny jako dvojice název-hodnota formuláře `<n>=<v>`, kde `<n>` je název argumentu a `<v>` je hodnota argumentu.</span><span class="sxs-lookup"><span data-stu-id="71972-149">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="71972-150">Použijte mezeru k oddělení více argumentů.</span><span class="sxs-lookup"><span data-stu-id="71972-150">Use a space to separate multiple arguments.</span></span>

## <a name="examples"></a><span data-ttu-id="71972-151">Příklady</span><span class="sxs-lookup"><span data-stu-id="71972-151">Examples</span></span>

<span data-ttu-id="71972-152">Spustit testy v *mytestproject.dll*:</span><span class="sxs-lookup"><span data-stu-id="71972-152">Run tests in *mytestproject.dll*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll
```

<span data-ttu-id="71972-153">Spusťte testy v souboru *mytestproject.dll*, exportujte do vlastní složky s vlastním názvem:</span><span class="sxs-lookup"><span data-stu-id="71972-153">Run tests in *mytestproject.dll*, exporting to custom folder with custom name:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path
```

<span data-ttu-id="71972-154">Spusťte testy v *mytestproject.dll* a *myothertestproject.exe*:</span><span class="sxs-lookup"><span data-stu-id="71972-154">Run tests in *mytestproject.dll* and *myothertestproject.exe*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll myothertestproject.exe
```

<span data-ttu-id="71972-155">Spustit `TestMethod1` testy:</span><span class="sxs-lookup"><span data-stu-id="71972-155">Run `TestMethod1` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1
```

<span data-ttu-id="71972-156">Běh `TestMethod1` `TestMethod2` a testy:</span><span class="sxs-lookup"><span data-stu-id="71972-156">Run `TestMethod1` and `TestMethod2` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1,TestMethod2
```
