---
title: dotnet – příkaz vstest
description: Příkaz dotnet VSTest vytvoří projekt a všechny jeho závislosti.
ms.date: 02/27/2020
ms.openlocfilehash: 88e5b6a8966d78d0746f9ea5ccbccab142a2e0f6
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156930"
---
# <a name="dotnet-vstest"></a><span data-ttu-id="a9c6d-103">dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="a9c6d-103">dotnet vstest</span></span>

<span data-ttu-id="a9c6d-104">**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="a9c6d-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="a9c6d-105">Název</span><span class="sxs-lookup"><span data-stu-id="a9c6d-105">Name</span></span>

<span data-ttu-id="a9c6d-106">`dotnet-vstest` – spustí testy ze zadaných souborů.</span><span class="sxs-lookup"><span data-stu-id="a9c6d-106">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a9c6d-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="a9c6d-107">Synopsis</span></span>

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings] [--Tests]
    [--TestAdapterPath] [--Platform] [--Framework] [--Parallel]
    [--TestCaseFilter] [--logger] [-lt|--ListTests]
    [--ParentProcessId] [--Port] [--Diag] [--Blame]
    [--InIsolation] [[--] <args>...]] [-?|--Help]
```

## <a name="description"></a><span data-ttu-id="a9c6d-108">Popis</span><span class="sxs-lookup"><span data-stu-id="a9c6d-108">Description</span></span>

<span data-ttu-id="a9c6d-109">Příkaz `dotnet-vstest` spustí aplikaci `VSTest.Console` příkazového řádku, aby se spouštěly automatizované testy jednotek.</span><span class="sxs-lookup"><span data-stu-id="a9c6d-109">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="a9c6d-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="a9c6d-110">Arguments</span></span>

- **`TEST_FILE_NAMES`**

  <span data-ttu-id="a9c6d-111">Spustí testy ze zadaných sestavení.</span><span class="sxs-lookup"><span data-stu-id="a9c6d-111">Run tests from the specified assemblies.</span></span> <span data-ttu-id="a9c6d-112">Rozdělte více názvů testovacích sestavení s mezerami.</span><span class="sxs-lookup"><span data-stu-id="a9c6d-112">Separate multiple test assembly names with spaces.</span></span> <span data-ttu-id="a9c6d-113">Jsou podporovány zástupné znaky.</span><span class="sxs-lookup"><span data-stu-id="a9c6d-113">Wildcards are supported.</span></span>

## <a name="options"></a><span data-ttu-id="a9c6d-114">Možnosti</span><span class="sxs-lookup"><span data-stu-id="a9c6d-114">Options</span></span>

- **`--Settings <Settings File>`**

  <span data-ttu-id="a9c6d-115">Nastavení, které se má použít při spouštění testů.</span><span class="sxs-lookup"><span data-stu-id="a9c6d-115">Settings to use when running tests.</span></span>

- **`--Tests <Test Names>`**

  <span data-ttu-id="a9c6d-116">Spustí testy s názvy, které odpovídají zadaným hodnotám.</span><span class="sxs-lookup"><span data-stu-id="a9c6d-116">Run tests with names that match the provided values.</span></span> <span data-ttu-id="a9c6d-117">Více hodnot oddělte čárkami.</span><span class="sxs-lookup"><span data-stu-id="a9c6d-117">Separate multiple values with commas.</span></span>

- **`--TestAdapterPath`**

  <span data-ttu-id="a9c6d-118">Použijte vlastní testovací adaptéry z dané cesty (pokud existuje) v testovacím běhu.</span><span class="sxs-lookup"><span data-stu-id="a9c6d-118">Use custom test adapters from a given path (if any) in the test run.</span></span>

- **`--Platform <Platform type>`**

  <span data-ttu-id="a9c6d-119">Cílová architektura platformy použitá pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="a9c6d-119">Target platform architecture used for test execution.</span></span> <span data-ttu-id="a9c6d-120">Platné hodnoty jsou `x86`, `x64`a `ARM`.</span><span class="sxs-lookup"><span data-stu-id="a9c6d-120">Valid values are `x86`, `x64`, and `ARM`.</span></span>

- **`--Framework <Framework Version>`**

  <span data-ttu-id="a9c6d-121">Cílová verze .NET Framework používaná pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="a9c6d-121">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="a9c6d-122">Příklady platných hodnot jsou `.NETFramework,Version=v4.6` nebo `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="a9c6d-122">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="a9c6d-123">Další podporované hodnoty jsou `Framework40`, `Framework45`, `FrameworkCore10`a `FrameworkUap10`.</span><span class="sxs-lookup"><span data-stu-id="a9c6d-123">Other supported values are `Framework40`, `Framework45`, `FrameworkCore10`, and `FrameworkUap10`.</span></span>

- **`--Parallel`**

  <span data-ttu-id="a9c6d-124">Paralelně spouštějte testy.</span><span class="sxs-lookup"><span data-stu-id="a9c6d-124">Run tests in parallel.</span></span> <span data-ttu-id="a9c6d-125">Ve výchozím nastavení jsou všechny dostupné jádra počítače k dispozici pro použití.</span><span class="sxs-lookup"><span data-stu-id="a9c6d-125">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="a9c6d-126">Určete explicitní počet jader nastavením vlastnosti `MaxCpuCount` pod uzlem `RunConfiguration` v souboru *runsettings* .</span><span class="sxs-lookup"><span data-stu-id="a9c6d-126">Specify an explicit number of cores by setting the `MaxCpuCount` property under the `RunConfiguration` node in the *runsettings* file.</span></span>

- **`--TestCaseFilter <Expression>`**

  <span data-ttu-id="a9c6d-127">Spustí testy, které odpovídají danému výrazu.</span><span class="sxs-lookup"><span data-stu-id="a9c6d-127">Run tests that match the given expression.</span></span> <span data-ttu-id="a9c6d-128">`<Expression>` je `<property>Operator<value>[|&<Expression>]`formátu, kde operátor je jedním z `=`, `!=`nebo `~`.</span><span class="sxs-lookup"><span data-stu-id="a9c6d-128">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="a9c6d-129">Operátor `~` obsahuje sémantiku Contains a je použitelný pro řetězcové vlastnosti, jako je `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="a9c6d-129">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="a9c6d-130">`()` závorky se používají k seskupení podvýrazů.</span><span class="sxs-lookup"><span data-stu-id="a9c6d-130">Parenthesis `()` are used to group subexpressions.</span></span>

- **`-?|--Help`**

  <span data-ttu-id="a9c6d-131">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="a9c6d-131">Prints out a short help for the command.</span></span>

- **`--logger <Logger Uri/FriendlyName>`**

  <span data-ttu-id="a9c6d-132">Zadejte protokolovací nástroj pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="a9c6d-132">Specify a logger for test results.</span></span>

  - <span data-ttu-id="a9c6d-133">K publikování výsledků testů do Team Foundation Server použijte poskytovatele protokolovacího nástroje `TfsPublisher`:</span><span class="sxs-lookup"><span data-stu-id="a9c6d-133">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

    ```console
    /logger:TfsPublisher;
        Collection=<team project collection url>;
        BuildName=<build name>;
        TeamProject=<team project name>
        [;Platform=<Defaults to "Any CPU">]
        [;Flavor=<Defaults to "Debug">]
        [;RunTitle=<title>]
    ```

  - <span data-ttu-id="a9c6d-134">Chcete-li protokolovat výsledky do souboru sady Visual Studio Výsledky testů (TRX), použijte poskytovatele protokolovacího nástroje `trx`.</span><span class="sxs-lookup"><span data-stu-id="a9c6d-134">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="a9c6d-135">Tento přepínač vytvoří soubor v adresáři výsledků testu s daným názvem souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="a9c6d-135">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="a9c6d-136">Pokud `LogFileName` není k dispozici, vytvoří se jedinečný název souboru, který bude obsahovat výsledky testu.</span><span class="sxs-lookup"><span data-stu-id="a9c6d-136">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

    ```console
    /logger:trx [;LogFileName=<Defaults to unique file name>]
    ```

- **`-lt|--ListTests <File Name>`**

  <span data-ttu-id="a9c6d-137">Zobrazí všechny zjištěné testy z daného kontejneru testů.</span><span class="sxs-lookup"><span data-stu-id="a9c6d-137">Lists all discovered tests from the given test container.</span></span>

- **`--ParentProcessId <ParentProcessId>`**

  <span data-ttu-id="a9c6d-138">ID procesu nadřazeného procesu zodpovědného za spuštění aktuálního procesu.</span><span class="sxs-lookup"><span data-stu-id="a9c6d-138">Process ID of the parent process responsible for launching the current process.</span></span>

- **`--Port <Port>`**

  <span data-ttu-id="a9c6d-139">Určuje port pro připojení soketu a příjem zpráv událostí.</span><span class="sxs-lookup"><span data-stu-id="a9c6d-139">Specifies the port for the socket connection and receiving the event messages.</span></span>

- **`--Diag <Path to log file>`**

  <span data-ttu-id="a9c6d-140">Povolí podrobné protokoly pro testovací platformu.</span><span class="sxs-lookup"><span data-stu-id="a9c6d-140">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="a9c6d-141">Protokoly se zapisují do poskytnutého souboru.</span><span class="sxs-lookup"><span data-stu-id="a9c6d-141">Logs are written to the provided file.</span></span>

- **`--Blame`**

  <span data-ttu-id="a9c6d-142">Spustí testy v režimu viny.</span><span class="sxs-lookup"><span data-stu-id="a9c6d-142">Runs the tests in blame mode.</span></span> <span data-ttu-id="a9c6d-143">Tato možnost je užitečná při izolaci problematických testů, které způsobují selhání hostitele testu.</span><span class="sxs-lookup"><span data-stu-id="a9c6d-143">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="a9c6d-144">Vytvoří výstupní soubor v aktuálním adresáři jako *Sequence. XML* , který zachycuje pořadí spuštění testů před selháním.</span><span class="sxs-lookup"><span data-stu-id="a9c6d-144">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`--InIsolation`**

  <span data-ttu-id="a9c6d-145">Spustí testy v izolovaném procesu.</span><span class="sxs-lookup"><span data-stu-id="a9c6d-145">Runs the tests in an isolated process.</span></span> <span data-ttu-id="a9c6d-146">Díky tomu je proces *VSTest. Console. exe* méně pravděpodobný při chybě v testech zastavit, ale testy mohou běžet pomaleji.</span><span class="sxs-lookup"><span data-stu-id="a9c6d-146">This makes *vstest.console.exe* process less likely to be stopped on an error in the tests, but tests may run slower.</span></span>

- **`@<file>`**

  <span data-ttu-id="a9c6d-147">Přečte soubor odpovědí pro další možnosti.</span><span class="sxs-lookup"><span data-stu-id="a9c6d-147">Reads response file for more options.</span></span>

- **`args`**

  <span data-ttu-id="a9c6d-148">Určuje nadbytečné argumenty, které se mají předat adaptéru.</span><span class="sxs-lookup"><span data-stu-id="a9c6d-148">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="a9c6d-149">Argumenty jsou zadány jako páry název-hodnota `<n>=<v>`formuláře, kde `<n>` je název argumentu a `<v>` je hodnota argumentu.</span><span class="sxs-lookup"><span data-stu-id="a9c6d-149">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="a9c6d-150">K oddělení více argumentů použijte mezeru.</span><span class="sxs-lookup"><span data-stu-id="a9c6d-150">Use a space to separate multiple arguments.</span></span>

## <a name="examples"></a><span data-ttu-id="a9c6d-151">Příklady</span><span class="sxs-lookup"><span data-stu-id="a9c6d-151">Examples</span></span>

<span data-ttu-id="a9c6d-152">Spustit testy v *knihovně mytestproject. dll*:</span><span class="sxs-lookup"><span data-stu-id="a9c6d-152">Run tests in *mytestproject.dll*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll
```

<span data-ttu-id="a9c6d-153">Spusťte testy v souboru *mytestproject. dll*a exportujte je do vlastní složky s vlastním názvem:</span><span class="sxs-lookup"><span data-stu-id="a9c6d-153">Run tests in *mytestproject.dll*, exporting to custom folder with custom name:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path
```

<span data-ttu-id="a9c6d-154">Spustit testy v *mytestproject. dll* a *myothertestproject. exe*:</span><span class="sxs-lookup"><span data-stu-id="a9c6d-154">Run tests in *mytestproject.dll* and *myothertestproject.exe*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll myothertestproject.exe
```

<span data-ttu-id="a9c6d-155">Spustit `TestMethod1` testy:</span><span class="sxs-lookup"><span data-stu-id="a9c6d-155">Run `TestMethod1` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1
```

<span data-ttu-id="a9c6d-156">Spustit `TestMethod1` a `TestMethod2` testy:</span><span class="sxs-lookup"><span data-stu-id="a9c6d-156">Run `TestMethod1` and `TestMethod2` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1,TestMethod2
```
