---
title: dotnet – příkaz vstest
description: Příkaz dotnet VSTest vytvoří projekt a všechny jeho závislosti.
ms.date: 02/27/2020
ms.openlocfilehash: f7db58f4aab59354b8c69ce0371324c23482dafe
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975391"
---
# <a name="dotnet-vstest"></a><span data-ttu-id="447a2-103">dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="447a2-103">dotnet vstest</span></span>

<span data-ttu-id="447a2-104">**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="447a2-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

> [!IMPORTANT]
> <span data-ttu-id="447a2-105">`dotnet vstest` Příkaz je nahrazen nástrojem `dotnet test`, který lze nyní použít ke spuštění sestavení.</span><span class="sxs-lookup"><span data-stu-id="447a2-105">The `dotnet vstest` command is superseded by `dotnet test`, which can now be used to run assemblies.</span></span> <span data-ttu-id="447a2-106">Viz [`dotnet test`](dotnet-test.md).</span><span class="sxs-lookup"><span data-stu-id="447a2-106">See [`dotnet test`](dotnet-test.md).</span></span>

## <a name="name"></a><span data-ttu-id="447a2-107">Name</span><span class="sxs-lookup"><span data-stu-id="447a2-107">Name</span></span>

<span data-ttu-id="447a2-108">`dotnet-vstest`-Spustí testy ze zadaných sestavení.</span><span class="sxs-lookup"><span data-stu-id="447a2-108">`dotnet-vstest` - Runs tests from the specified assemblies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="447a2-109">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="447a2-109">Synopsis</span></span>

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

## <a name="description"></a><span data-ttu-id="447a2-110">Popis</span><span class="sxs-lookup"><span data-stu-id="447a2-110">Description</span></span>

<span data-ttu-id="447a2-111">`dotnet-vstest` Příkaz spustí aplikaci `VSTest.Console` příkazového řádku pro spuštění automatizovaných testů jednotek.</span><span class="sxs-lookup"><span data-stu-id="447a2-111">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="447a2-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="447a2-112">Arguments</span></span>

- **`TEST_FILE_NAMES`**

  <span data-ttu-id="447a2-113">Spustí testy ze zadaných sestavení.</span><span class="sxs-lookup"><span data-stu-id="447a2-113">Run tests from the specified assemblies.</span></span> <span data-ttu-id="447a2-114">Rozdělte více názvů testovacích sestavení s mezerami.</span><span class="sxs-lookup"><span data-stu-id="447a2-114">Separate multiple test assembly names with spaces.</span></span> <span data-ttu-id="447a2-115">Jsou podporovány zástupné znaky.</span><span class="sxs-lookup"><span data-stu-id="447a2-115">Wildcards are supported.</span></span>

## <a name="options"></a><span data-ttu-id="447a2-116">Možnosti</span><span class="sxs-lookup"><span data-stu-id="447a2-116">Options</span></span>

- **`--Blame`**

  <span data-ttu-id="447a2-117">Spustí testy v režimu viny.</span><span class="sxs-lookup"><span data-stu-id="447a2-117">Runs the tests in blame mode.</span></span> <span data-ttu-id="447a2-118">Tato možnost je užitečná při izolaci problematických testů, které způsobují selhání hostitele testu.</span><span class="sxs-lookup"><span data-stu-id="447a2-118">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="447a2-119">Vytvoří výstupní soubor v aktuálním adresáři jako *Sequence. XML* , který zachycuje pořadí spuštění testů před selháním.</span><span class="sxs-lookup"><span data-stu-id="447a2-119">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`--Diag <PATH_TO_LOG_FILE>`**

  <span data-ttu-id="447a2-120">Povolí podrobné protokoly pro testovací platformu.</span><span class="sxs-lookup"><span data-stu-id="447a2-120">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="447a2-121">Protokoly se zapisují do poskytnutého souboru.</span><span class="sxs-lookup"><span data-stu-id="447a2-121">Logs are written to the provided file.</span></span>

- **`--Framework <FRAMEWORK>`**

  <span data-ttu-id="447a2-122">Cílová verze .NET Framework používaná pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="447a2-122">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="447a2-123">Příklady platných hodnot jsou `.NETFramework,Version=v4.6` nebo. `.NETCoreApp,Version=v1.0`</span><span class="sxs-lookup"><span data-stu-id="447a2-123">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="447a2-124">Další podporované hodnoty jsou `Framework40`, `Framework45`, `FrameworkCore10`a `FrameworkUap10`.</span><span class="sxs-lookup"><span data-stu-id="447a2-124">Other supported values are `Framework40`, `Framework45`, `FrameworkCore10`, and `FrameworkUap10`.</span></span>

- **`--InIsolation`**

  <span data-ttu-id="447a2-125">Spustí testy v izolovaném procesu.</span><span class="sxs-lookup"><span data-stu-id="447a2-125">Runs the tests in an isolated process.</span></span> <span data-ttu-id="447a2-126">Díky tomu je proces *VSTest. Console. exe* méně pravděpodobný při chybě v testech zastavit, ale testy mohou běžet pomaleji.</span><span class="sxs-lookup"><span data-stu-id="447a2-126">This makes *vstest.console.exe* process less likely to be stopped on an error in the tests, but tests may run slower.</span></span>

- **`-lt|--ListTests <FILE_NAME>`**

  <span data-ttu-id="447a2-127">Zobrazí všechny zjištěné testy z daného kontejneru testů.</span><span class="sxs-lookup"><span data-stu-id="447a2-127">Lists all discovered tests from the given test container.</span></span>

- **`--logger <LOGGER_URI/FRIENDLY_NAME>`**

  <span data-ttu-id="447a2-128">Zadejte protokolovací nástroj pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="447a2-128">Specify a logger for test results.</span></span>

  - <span data-ttu-id="447a2-129">K publikování výsledků testů do Team Foundation Server použijte zprostředkovatele `TfsPublisher` protokolovacího nástroje:</span><span class="sxs-lookup"><span data-stu-id="447a2-129">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

    ```console
    /logger:TfsPublisher;
        Collection=<team project collection url>;
        BuildName=<build name>;
        TeamProject=<team project name>
        [;Platform=<Defaults to "Any CPU">]
        [;Flavor=<Defaults to "Debug">]
        [;RunTitle=<title>]
    ```

  - <span data-ttu-id="447a2-130">K protokolování výsledků do souboru sady Visual Studio Výsledky testů (TRX) použijte poskytovatele `trx` protokolovacího nástroje.</span><span class="sxs-lookup"><span data-stu-id="447a2-130">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="447a2-131">Tento přepínač vytvoří soubor v adresáři výsledků testu s daným názvem souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="447a2-131">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="447a2-132">Pokud `LogFileName` není zadaný, vytvoří se jedinečný název souboru, který bude obsahovat výsledky testu.</span><span class="sxs-lookup"><span data-stu-id="447a2-132">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

    ```console
    /logger:trx [;LogFileName=<Defaults to unique file name>]
    ```

- **`--Parallel`**

  <span data-ttu-id="447a2-133">Paralelně spouštějte testy.</span><span class="sxs-lookup"><span data-stu-id="447a2-133">Run tests in parallel.</span></span> <span data-ttu-id="447a2-134">Ve výchozím nastavení jsou všechny dostupné jádra počítače k dispozici pro použití.</span><span class="sxs-lookup"><span data-stu-id="447a2-134">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="447a2-135">Určete explicitní počet jader nastavením `MaxCpuCount` vlastnosti pod `RunConfiguration` uzlem v souboru *runsettings* .</span><span class="sxs-lookup"><span data-stu-id="447a2-135">Specify an explicit number of cores by setting the `MaxCpuCount` property under the `RunConfiguration` node in the *runsettings* file.</span></span>

- **`--ParentProcessId <PROCESS_ID>`**

  <span data-ttu-id="447a2-136">ID procesu nadřazeného procesu zodpovědného za spuštění aktuálního procesu.</span><span class="sxs-lookup"><span data-stu-id="447a2-136">Process ID of the parent process responsible for launching the current process.</span></span>

- **`--Platform <PLATFORM_TYPE>`**

  <span data-ttu-id="447a2-137">Cílová architektura platformy použitá pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="447a2-137">Target platform architecture used for test execution.</span></span> <span data-ttu-id="447a2-138">Platné hodnoty jsou `x86`, `x64`a `ARM`.</span><span class="sxs-lookup"><span data-stu-id="447a2-138">Valid values are `x86`, `x64`, and `ARM`.</span></span>

- **`--Port <PORT>`**

  <span data-ttu-id="447a2-139">Určuje port pro připojení soketu a příjem zpráv událostí.</span><span class="sxs-lookup"><span data-stu-id="447a2-139">Specifies the port for the socket connection and receiving the event messages.</span></span>

- **`--ResultsDirectory:<PATH>`**

  <span data-ttu-id="447a2-140">Adresář výsledků testů bude vytvořen v zadané cestě, pokud neexistuje.</span><span class="sxs-lookup"><span data-stu-id="447a2-140">Test results directory will be created in specified path if not exists.</span></span>

- **`--Settings <SETTINGS_FILE>`**

  <span data-ttu-id="447a2-141">Nastavení, které se má použít při spouštění testů.</span><span class="sxs-lookup"><span data-stu-id="447a2-141">Settings to use when running tests.</span></span>

- **`--TestAdapterPath <PATH>`**

  <span data-ttu-id="447a2-142">Použijte vlastní testovací adaptéry z dané cesty (pokud existuje) v testovacím běhu.</span><span class="sxs-lookup"><span data-stu-id="447a2-142">Use custom test adapters from a given path (if any) in the test run.</span></span>

- **`--TestCaseFilter <EXPRESSION>`**

  <span data-ttu-id="447a2-143">Spustí testy, které odpovídají danému výrazu.</span><span class="sxs-lookup"><span data-stu-id="447a2-143">Run tests that match the given expression.</span></span> <span data-ttu-id="447a2-144">`<EXPRESSION>`má formát `<property>Operator<value>[|&<EXPRESSION>]`, kde operátor je jedna z `=`, `!=`nebo. `~`</span><span class="sxs-lookup"><span data-stu-id="447a2-144">`<EXPRESSION>` is of the format `<property>Operator<value>[|&<EXPRESSION>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="447a2-145">Operátor `~` obsahuje sémantiku Contains a je použitelný pro řetězcové vlastnosti, jako `DisplayName`je.</span><span class="sxs-lookup"><span data-stu-id="447a2-145">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="447a2-146">K seskupení `()` podvýrazů se používají kulaté závorky.</span><span class="sxs-lookup"><span data-stu-id="447a2-146">Parentheses `()` are used to group subexpressions.</span></span> <span data-ttu-id="447a2-147">Další informace najdete v tématu [testovací případ Filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span><span class="sxs-lookup"><span data-stu-id="447a2-147">For more information, see [TestCase filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span></span>

- **`--Tests <TEST_NAMES>`**

  <span data-ttu-id="447a2-148">Spustí testy s názvy, které odpovídají zadaným hodnotám.</span><span class="sxs-lookup"><span data-stu-id="447a2-148">Run tests with names that match the provided values.</span></span> <span data-ttu-id="447a2-149">Více hodnot oddělte čárkami.</span><span class="sxs-lookup"><span data-stu-id="447a2-149">Separate multiple values with commas.</span></span>

- **`-?|--Help`**

  <span data-ttu-id="447a2-150">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="447a2-150">Prints out a short help for the command.</span></span>

- **`@<file>`**

  <span data-ttu-id="447a2-151">Přečte soubor odpovědí pro další možnosti.</span><span class="sxs-lookup"><span data-stu-id="447a2-151">Reads response file for more options.</span></span>

- **`args`**

  <span data-ttu-id="447a2-152">Určuje nadbytečné argumenty, které se mají předat adaptéru.</span><span class="sxs-lookup"><span data-stu-id="447a2-152">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="447a2-153">Argumenty jsou zadány jako páry název-hodnota ve formátu `<n>=<v>`, kde `<n>` je název argumentu a `<v>` je hodnota argumentu.</span><span class="sxs-lookup"><span data-stu-id="447a2-153">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="447a2-154">K oddělení více argumentů použijte mezeru.</span><span class="sxs-lookup"><span data-stu-id="447a2-154">Use a space to separate multiple arguments.</span></span>

## <a name="examples"></a><span data-ttu-id="447a2-155">Příklady</span><span class="sxs-lookup"><span data-stu-id="447a2-155">Examples</span></span>

<span data-ttu-id="447a2-156">Spustit testy v *knihovně mytestproject. dll*:</span><span class="sxs-lookup"><span data-stu-id="447a2-156">Run tests in *mytestproject.dll*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll
```

<span data-ttu-id="447a2-157">Spusťte testy v souboru *mytestproject. dll*a exportujte je do vlastní složky s vlastním názvem:</span><span class="sxs-lookup"><span data-stu-id="447a2-157">Run tests in *mytestproject.dll*, exporting to custom folder with custom name:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path
```

<span data-ttu-id="447a2-158">Spustit testy v *mytestproject. dll* a *myothertestproject. exe*:</span><span class="sxs-lookup"><span data-stu-id="447a2-158">Run tests in *mytestproject.dll* and *myothertestproject.exe*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll myothertestproject.exe
```

<span data-ttu-id="447a2-159">Spustit `TestMethod1` testy:</span><span class="sxs-lookup"><span data-stu-id="447a2-159">Run `TestMethod1` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1
```

<span data-ttu-id="447a2-160">Běh `TestMethod1` a `TestMethod2` testy:</span><span class="sxs-lookup"><span data-stu-id="447a2-160">Run `TestMethod1` and `TestMethod2` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1,TestMethod2
```

## <a name="see-also"></a><span data-ttu-id="447a2-161">Viz také</span><span class="sxs-lookup"><span data-stu-id="447a2-161">See also</span></span>

- [<span data-ttu-id="447a2-162">VSTest.Console.exe – možnosti příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="447a2-162">VSTest.Console.exe command-line options</span></span>](/visualstudio/test/vstest-console-options)
