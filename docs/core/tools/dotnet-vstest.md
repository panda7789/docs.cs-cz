---
title: dotnet vstest, příkaz
description: Dotnet vstest příkaz vytvoří projekt a všechny jeho závislosti.
ms.date: 02/27/2020
ms.openlocfilehash: e8fa94cf12ca2fe5fb99c6e3c1dcdb52185798c0
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463289"
---
# <a name="dotnet-vstest"></a><span data-ttu-id="d5a43-103">dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="d5a43-103">dotnet vstest</span></span>

<span data-ttu-id="d5a43-104">**Tento článek se týká:** ✔️ .NET Core 2.1 SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="d5a43-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="d5a43-105">Název</span><span class="sxs-lookup"><span data-stu-id="d5a43-105">Name</span></span>

<span data-ttu-id="d5a43-106">`dotnet-vstest`- Spustí testy ze zadaných souborů.</span><span class="sxs-lookup"><span data-stu-id="d5a43-106">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d5a43-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="d5a43-107">Synopsis</span></span>

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Blame] [--Diag <PATH_TO_LOG_FILE>]
    [--Framework <FRAMEWORK>] [--InIsolation] [-lt|--ListTests <FILE_NAME>]
    [--logger <LOGGER_URI/FRIENDLY_NAME>] [--Parallel]
    [--ParentProcessId <PROCESS_ID>] [--Platform] <PLATFORM_TYPE>
    [--Port <PORT>] [--ResultsDirectory<PATH>] [--Settings <SETTINGS_FILE>]
    [--TestAdapterPath <PATH>] [--TestCaseFilter <EXPRESSION>]
    [--Tests <TEST_NAMES>] [[--] <args>...]]

dotnet vstest -?|--Help
```

## <a name="description"></a><span data-ttu-id="d5a43-108">Popis</span><span class="sxs-lookup"><span data-stu-id="d5a43-108">Description</span></span>

<span data-ttu-id="d5a43-109">Příkaz `dotnet-vstest` spustí `VSTest.Console` aplikaci příkazového řádku pro spuštění automatizovaných testů částí.</span><span class="sxs-lookup"><span data-stu-id="d5a43-109">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="d5a43-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d5a43-110">Arguments</span></span>

- **`TEST_FILE_NAMES`**

  <span data-ttu-id="d5a43-111">Spusťte testy ze zadaných sestavení.</span><span class="sxs-lookup"><span data-stu-id="d5a43-111">Run tests from the specified assemblies.</span></span> <span data-ttu-id="d5a43-112">Oddělte více názvů testovacích sestavení mezerami.</span><span class="sxs-lookup"><span data-stu-id="d5a43-112">Separate multiple test assembly names with spaces.</span></span> <span data-ttu-id="d5a43-113">Zástupné znaky jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="d5a43-113">Wildcards are supported.</span></span>

## <a name="options"></a><span data-ttu-id="d5a43-114">Možnosti</span><span class="sxs-lookup"><span data-stu-id="d5a43-114">Options</span></span>

- **`--Blame`**

  <span data-ttu-id="d5a43-115">Spustí testy v režimu obviňování.</span><span class="sxs-lookup"><span data-stu-id="d5a43-115">Runs the tests in blame mode.</span></span> <span data-ttu-id="d5a43-116">Tato možnost je užitečná při izolaci problémových testů, které způsobují selhání testovacího hostitele.</span><span class="sxs-lookup"><span data-stu-id="d5a43-116">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="d5a43-117">Vytvoří výstupní soubor v aktuálním adresáři jako *Sequence.xml,* který zachycuje pořadí spuštění testů před selháním.</span><span class="sxs-lookup"><span data-stu-id="d5a43-117">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`--Diag <PATH_TO_LOG_FILE>`**

  <span data-ttu-id="d5a43-118">Povolí podrobné protokoly pro testovací platformu.</span><span class="sxs-lookup"><span data-stu-id="d5a43-118">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="d5a43-119">Protokoly jsou zapsány do dodaný soubor.</span><span class="sxs-lookup"><span data-stu-id="d5a43-119">Logs are written to the provided file.</span></span>

- **`--Framework <FRAMEWORK>`**

  <span data-ttu-id="d5a43-120">Cílová verze rozhraní .NET Framework použitá pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="d5a43-120">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="d5a43-121">Příklady platných `.NETFramework,Version=v4.6` hodnot `.NETCoreApp,Version=v1.0`jsou nebo .</span><span class="sxs-lookup"><span data-stu-id="d5a43-121">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="d5a43-122">Další podporované `Framework40`hodnoty `Framework45` `FrameworkCore10`jsou `FrameworkUap10`, , a .</span><span class="sxs-lookup"><span data-stu-id="d5a43-122">Other supported values are `Framework40`, `Framework45`, `FrameworkCore10`, and `FrameworkUap10`.</span></span>

- **`--InIsolation`**

  <span data-ttu-id="d5a43-123">Spustí testy v izolovaném procesu.</span><span class="sxs-lookup"><span data-stu-id="d5a43-123">Runs the tests in an isolated process.</span></span> <span data-ttu-id="d5a43-124">Díky *vstest.console.exe* proces méně pravděpodobné, že bude zastaven a na chybu v testech, ale testy mohou běžet pomaleji.</span><span class="sxs-lookup"><span data-stu-id="d5a43-124">This makes *vstest.console.exe* process less likely to be stopped on an error in the tests, but tests may run slower.</span></span>

- **`-lt|--ListTests <FILE_NAME>`**

  <span data-ttu-id="d5a43-125">Zobrazí seznam všech zjištěných testů z daného testovacího kontejneru.</span><span class="sxs-lookup"><span data-stu-id="d5a43-125">Lists all discovered tests from the given test container.</span></span>

- **`--logger <LOGGER_URI/FRIENDLY_NAME>`**

  <span data-ttu-id="d5a43-126">Zadejte protokolovací nástroj pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="d5a43-126">Specify a logger for test results.</span></span>

  - <span data-ttu-id="d5a43-127">Chcete-li publikovat výsledky testů na `TfsPublisher` serveru Team Foundation, použijte zprostředkovatele protokolování:</span><span class="sxs-lookup"><span data-stu-id="d5a43-127">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

    ```console
    /logger:TfsPublisher;
        Collection=<team project collection url>;
        BuildName=<build name>;
        TeamProject=<team project name>
        [;Platform=<Defaults to "Any CPU">]
        [;Flavor=<Defaults to "Debug">]
        [;RunTitle=<title>]
    ```

  - <span data-ttu-id="d5a43-128">Chcete-li protokolovat výsledky souboru výsledků testů `trx` sady Visual Studio (TRX), použijte zprostředkovatele protokolování.</span><span class="sxs-lookup"><span data-stu-id="d5a43-128">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="d5a43-129">Tento přepínač vytvoří soubor v adresáři výsledků testu s daným názvem souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="d5a43-129">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="d5a43-130">Pokud `LogFileName` není k dispozici, jedinečný název souboru je vytvořen pro uložení výsledků testu.</span><span class="sxs-lookup"><span data-stu-id="d5a43-130">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

    ```console
    /logger:trx [;LogFileName=<Defaults to unique file name>]
    ```

- **`--Parallel`**

  <span data-ttu-id="d5a43-131">Spouštět testy paralelně.</span><span class="sxs-lookup"><span data-stu-id="d5a43-131">Run tests in parallel.</span></span> <span data-ttu-id="d5a43-132">Ve výchozím nastavení jsou k dispozici všechna dostupná jádra v počítači.</span><span class="sxs-lookup"><span data-stu-id="d5a43-132">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="d5a43-133">Zadejte explicitní počet jader `MaxCpuCount` nastavením `RunConfiguration` vlastnosti pod uzlevě v souboru *runsettings.*</span><span class="sxs-lookup"><span data-stu-id="d5a43-133">Specify an explicit number of cores by setting the `MaxCpuCount` property under the `RunConfiguration` node in the *runsettings* file.</span></span>

- **`--ParentProcessId <PROCESS_ID>`**

  <span data-ttu-id="d5a43-134">ID procesu nadřazeného procesu odpovědného za spuštění aktuálního procesu.</span><span class="sxs-lookup"><span data-stu-id="d5a43-134">Process ID of the parent process responsible for launching the current process.</span></span>

- **`--Platform <PLATFORM_TYPE>`**

  <span data-ttu-id="d5a43-135">Architektura cílové platformy používaná pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="d5a43-135">Target platform architecture used for test execution.</span></span> <span data-ttu-id="d5a43-136">Platné hodnoty `x86` `x64`jsou `ARM`, a .</span><span class="sxs-lookup"><span data-stu-id="d5a43-136">Valid values are `x86`, `x64`, and `ARM`.</span></span>

- **`--Port <PORT>`**

  <span data-ttu-id="d5a43-137">Určuje port pro připojení soketu a příjem zpráv o událostech.</span><span class="sxs-lookup"><span data-stu-id="d5a43-137">Specifies the port for the socket connection and receiving the event messages.</span></span>

- **`--ResultsDirectory:<PATH>`**

  <span data-ttu-id="d5a43-138">Pokud neexistuje, bude adresář výsledků testu vytvořen v zadané cestě.</span><span class="sxs-lookup"><span data-stu-id="d5a43-138">Test results directory will be created in specified path if not exists.</span></span>

- **`--Settings <SETTINGS_FILE>`**

  <span data-ttu-id="d5a43-139">Nastavení, které se má použít při spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="d5a43-139">Settings to use when running tests.</span></span>

- **`--TestAdapterPath <PATH>`**

  <span data-ttu-id="d5a43-140">Při testovacím běhu použijte vlastní testovací adaptéry z dané cesty (pokud existuje).</span><span class="sxs-lookup"><span data-stu-id="d5a43-140">Use custom test adapters from a given path (if any) in the test run.</span></span>

- **`--TestCaseFilter <EXPRESSION>`**

  <span data-ttu-id="d5a43-141">Spusťte testy, které odpovídají danému výrazu.</span><span class="sxs-lookup"><span data-stu-id="d5a43-141">Run tests that match the given expression.</span></span> <span data-ttu-id="d5a43-142">`<EXPRESSION>`je ve `<property>Operator<value>[|&<EXPRESSION>]`formátu , kde `=`Operator `!=`je `~`jedním z , , nebo .</span><span class="sxs-lookup"><span data-stu-id="d5a43-142">`<EXPRESSION>` is of the format `<property>Operator<value>[|&<EXPRESSION>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="d5a43-143">Operátor `~` má sémantiku "obsahuje" a `DisplayName`je použitelný pro vlastnosti řetězce, jako je .</span><span class="sxs-lookup"><span data-stu-id="d5a43-143">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="d5a43-144">Závorky `()` se používají k seskupení podvýrazů.</span><span class="sxs-lookup"><span data-stu-id="d5a43-144">Parentheses `()` are used to group subexpressions.</span></span> <span data-ttu-id="d5a43-145">Další informace naleznete v tématu [TestCase filtr](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span><span class="sxs-lookup"><span data-stu-id="d5a43-145">For more information, see [TestCase filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span></span>

- **`--Tests <TEST_NAMES>`**

  <span data-ttu-id="d5a43-146">Spusťte testy s názvy, které odpovídají zadaným hodnotám.</span><span class="sxs-lookup"><span data-stu-id="d5a43-146">Run tests with names that match the provided values.</span></span> <span data-ttu-id="d5a43-147">Oddělte více hodnot čárkou.</span><span class="sxs-lookup"><span data-stu-id="d5a43-147">Separate multiple values with commas.</span></span>

- **`-?|--Help`**

  <span data-ttu-id="d5a43-148">Vytiskne krátkou nápovědu pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="d5a43-148">Prints out a short help for the command.</span></span>

- **`@<file>`**

  <span data-ttu-id="d5a43-149">Přečte soubor odpovědí pro další možnosti.</span><span class="sxs-lookup"><span data-stu-id="d5a43-149">Reads response file for more options.</span></span>

- **`args`**

  <span data-ttu-id="d5a43-150">Určuje další argumenty, které mají být předávány adaptéru.</span><span class="sxs-lookup"><span data-stu-id="d5a43-150">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="d5a43-151">Argumenty jsou určeny jako dvojice název-hodnota formuláře `<n>=<v>`, kde `<n>` je název argumentu a `<v>` je hodnota argumentu.</span><span class="sxs-lookup"><span data-stu-id="d5a43-151">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="d5a43-152">Použijte mezeru k oddělení více argumentů.</span><span class="sxs-lookup"><span data-stu-id="d5a43-152">Use a space to separate multiple arguments.</span></span>

## <a name="examples"></a><span data-ttu-id="d5a43-153">Příklady</span><span class="sxs-lookup"><span data-stu-id="d5a43-153">Examples</span></span>

<span data-ttu-id="d5a43-154">Spustit testy v *mytestproject.dll*:</span><span class="sxs-lookup"><span data-stu-id="d5a43-154">Run tests in *mytestproject.dll*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll
```

<span data-ttu-id="d5a43-155">Spusťte testy v souboru *mytestproject.dll*, exportujte do vlastní složky s vlastním názvem:</span><span class="sxs-lookup"><span data-stu-id="d5a43-155">Run tests in *mytestproject.dll*, exporting to custom folder with custom name:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path
```

<span data-ttu-id="d5a43-156">Spusťte testy v *mytestproject.dll* a *myothertestproject.exe*:</span><span class="sxs-lookup"><span data-stu-id="d5a43-156">Run tests in *mytestproject.dll* and *myothertestproject.exe*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll myothertestproject.exe
```

<span data-ttu-id="d5a43-157">Spustit `TestMethod1` testy:</span><span class="sxs-lookup"><span data-stu-id="d5a43-157">Run `TestMethod1` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1
```

<span data-ttu-id="d5a43-158">Běh `TestMethod1` `TestMethod2` a testy:</span><span class="sxs-lookup"><span data-stu-id="d5a43-158">Run `TestMethod1` and `TestMethod2` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1,TestMethod2
```

## <a name="see-also"></a><span data-ttu-id="d5a43-159">Viz také</span><span class="sxs-lookup"><span data-stu-id="d5a43-159">See also</span></span>

- [<span data-ttu-id="d5a43-160">VSTest.Console.exe – možnosti příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="d5a43-160">VSTest.Console.exe command-line options</span></span>](/visualstudio/test/vstest-console-options)
