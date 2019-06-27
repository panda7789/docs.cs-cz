---
title: příkaz DotNet test
description: Příkaz dotnet test slouží ke spuštění testů jednotek v daném projektu.
ms.date: 05/29/2018
ms.openlocfilehash: 6b67273f549edd7712237756a5aba13d5cb59a61
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410356"
---
# <a name="dotnet-test"></a><span data-ttu-id="90c40-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="90c40-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="90c40-104">Name</span><span class="sxs-lookup"><span data-stu-id="90c40-104">Name</span></span>

<span data-ttu-id="90c40-105">`dotnet test` -Ovladač test .NET ke spuštění testů jednotek.</span><span class="sxs-lookup"><span data-stu-id="90c40-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="90c40-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="90c40-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="90c40-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="90c40-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] 
    [-v|--verbosity] [-- <RunSettings arguments>]

dotnet test [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="90c40-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="90c40-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]

dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="90c40-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="90c40-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]

dotnet test [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="90c40-110">Popis</span><span class="sxs-lookup"><span data-stu-id="90c40-110">Description</span></span>

<span data-ttu-id="90c40-111">`dotnet test` Příkaz se používá ke spuštění testů jednotek v daném projektu.</span><span class="sxs-lookup"><span data-stu-id="90c40-111">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="90c40-112">`dotnet test` Příkaz spustí zadaný pro projekt test runner konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="90c40-112">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="90c40-113">Nástroj test runner sestavy úspěch nebo selhání jednotlivých testovacích a spustí testy, které jsou definovány pro rozhraní testování částí (například MSTest, NUnit nebo xUnit).</span><span class="sxs-lookup"><span data-stu-id="90c40-113">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="90c40-114">Pokud všechny testy jsou úspěšné, nástroj test runner vrátí hodnotu 0 jako ukončovací kód; jinak pokud nějaký test selže, vrátí se 1.</span><span class="sxs-lookup"><span data-stu-id="90c40-114">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="90c40-115">Nástroj test runner a knihovnu testu jednotky jsou dodávány jako balíčky NuGet a se obnoví jako běžný závislosti projektu.</span><span class="sxs-lookup"><span data-stu-id="90c40-115">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="90c40-116">Projekty testů zadat nástroje test runner pomocí běžný `<PackageReference>` elementu, jak je znázorněno v následující ukázkový soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="90c40-116">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="90c40-117">Arguments</span><span class="sxs-lookup"><span data-stu-id="90c40-117">Arguments</span></span>

`PROJECT`

<span data-ttu-id="90c40-118">Cesta k projektu testů.</span><span class="sxs-lookup"><span data-stu-id="90c40-118">Path to the test project.</span></span> <span data-ttu-id="90c40-119">Pokud není zadán, použije se výchozí aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="90c40-119">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="90c40-120">Možnosti</span><span class="sxs-lookup"><span data-stu-id="90c40-120">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="90c40-121">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="90c40-121">.NET Core 2.1</span></span>](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="90c40-122">Používáte vlastní adaptéry testu ze zadané cesty v testovacím běhu.</span><span class="sxs-lookup"><span data-stu-id="90c40-122">Use the custom test adapters from the specified path in the test run.</span></span>

`--blame`

<span data-ttu-id="90c40-123">Testy se spustí v režimu viny.</span><span class="sxs-lookup"><span data-stu-id="90c40-123">Runs the tests in blame mode.</span></span> <span data-ttu-id="90c40-124">Tato možnost je užitečná v izolaci problematické testů způsobí hostitele testu při selhání.</span><span class="sxs-lookup"><span data-stu-id="90c40-124">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="90c40-125">Vytvoří výstupní soubor v aktuálním adresáři jako *Sequence.xml* , který zachycuje pořadí provádění testů před selhání.</span><span class="sxs-lookup"><span data-stu-id="90c40-125">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="90c40-126">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="90c40-126">Defines the build configuration.</span></span> <span data-ttu-id="90c40-127">Výchozí hodnota je `Debug`, ale váš projekt konfigurace může přepsat toto výchozí nastavení sady SDK.</span><span class="sxs-lookup"><span data-stu-id="90c40-127">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="90c40-128">Povolí shromažďování dat pro testovací běh.</span><span class="sxs-lookup"><span data-stu-id="90c40-128">Enables data collector for the test run.</span></span> <span data-ttu-id="90c40-129">Další informace najdete v tématu [monitorování a analýza testovacího běhu](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="90c40-129">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="90c40-130">Umožňuje diagnostickém režimu pro testovací platformy a zápis diagnostické zprávy do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="90c40-130">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="90c40-131">Vyhledá binárních souborů testu pro konkrétní [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="90c40-131">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="90c40-132">Filtruje testy v aktuálním projektu pomocí daného výrazu.</span><span class="sxs-lookup"><span data-stu-id="90c40-132">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="90c40-133">Další informace najdete v tématu [možnost podrobnosti filtru](#filter-option-details) oddílu.</span><span class="sxs-lookup"><span data-stu-id="90c40-133">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="90c40-134">Další informace a příklady o tom, jak použít selektivní jednotky filtrování testů, naleznete v tématu [spouštění selektivních testů jednotek](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="90c40-134">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="90c40-135">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="90c40-135">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="90c40-136">Určuje protokolovací nástroj pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="90c40-136">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="90c40-137">Nepodporuje vytvoření testovacího projektu před jejím spuštěním.</span><span class="sxs-lookup"><span data-stu-id="90c40-137">Doesn't build the test project before running it.</span></span> <span data-ttu-id="90c40-138">Také implicitní nastaví `--no-restore` příznak.</span><span class="sxs-lookup"><span data-stu-id="90c40-138">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="90c40-139">Při spuštění příkazu se nebude spouštět implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="90c40-139">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="90c40-140">Adresář, ve kterém chcete najít binární soubory, které chcete spustit.</span><span class="sxs-lookup"><span data-stu-id="90c40-140">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="90c40-141">Adresář, kam výsledky testu budou umístěny.</span><span class="sxs-lookup"><span data-stu-id="90c40-141">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="90c40-142">Pokud zadaný adresář neexistuje, vytvoří se.</span><span class="sxs-lookup"><span data-stu-id="90c40-142">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="90c40-143">`.runsettings` Soubor se má použít pro spouštění testů.</span><span class="sxs-lookup"><span data-stu-id="90c40-143">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="90c40-144">Konfigurace testů jednotek s použitím `.runsettings` souboru.</span><span class="sxs-lookup"><span data-stu-id="90c40-144">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file?view=vs-2019)

`-t|--list-tests`

<span data-ttu-id="90c40-145">Seznam všech zjištěných testů v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="90c40-145">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="90c40-146">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="90c40-146">Sets the verbosity level of the command.</span></span> <span data-ttu-id="90c40-147">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="90c40-147">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`RunSettings arguments`

<span data-ttu-id="90c40-148">Argumenty předány jako RunSettings Konfigurace testu.</span><span class="sxs-lookup"><span data-stu-id="90c40-148">Arguments passed as RunSettings configurations for the test.</span></span> <span data-ttu-id="90c40-149">Argumenty se zadávají jako `[name]=[value]` dvojice po "--" (Poznámka: mezera za--).</span><span class="sxs-lookup"><span data-stu-id="90c40-149">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="90c40-150">Mezera se používá k oddělení více `[name]=[value]` dvojice.</span><span class="sxs-lookup"><span data-stu-id="90c40-150">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

<span data-ttu-id="90c40-151">Příklad: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="90c40-151">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

<span data-ttu-id="90c40-152">Další informace o nastavení běhu, naleznete v tématu [vstest.console.exe: Předávání argumentů RunSettings](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="90c40-152">For more information about RunSettings, see [vstest.console.exe: Passing RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="90c40-153">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="90c40-153">.NET Core 2.0</span></span>](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="90c40-154">Používáte vlastní adaptéry testu ze zadané cesty v testovacím běhu.</span><span class="sxs-lookup"><span data-stu-id="90c40-154">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="90c40-155">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="90c40-155">Defines the build configuration.</span></span> <span data-ttu-id="90c40-156">Výchozí hodnota je `Debug`, ale váš projekt konfigurace může přepsat toto výchozí nastavení sady SDK.</span><span class="sxs-lookup"><span data-stu-id="90c40-156">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="90c40-157">Povolí shromažďování dat pro testovací běh.</span><span class="sxs-lookup"><span data-stu-id="90c40-157">Enables data collector for the test run.</span></span> <span data-ttu-id="90c40-158">Další informace najdete v tématu [monitorování a analýza testovacího běhu](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="90c40-158">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="90c40-159">Umožňuje diagnostickém režimu pro testovací platformy a zápis diagnostické zprávy do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="90c40-159">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="90c40-160">Vyhledá binárních souborů testu pro konkrétní [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="90c40-160">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="90c40-161">Filtruje testy v aktuálním projektu pomocí daného výrazu.</span><span class="sxs-lookup"><span data-stu-id="90c40-161">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="90c40-162">Další informace najdete v tématu [možnost podrobnosti filtru](#filter-option-details) oddílu.</span><span class="sxs-lookup"><span data-stu-id="90c40-162">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="90c40-163">Další informace a příklady o tom, jak použít selektivní jednotky filtrování testů, naleznete v tématu [spouštění selektivních testů jednotek](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="90c40-163">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="90c40-164">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="90c40-164">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="90c40-165">Určuje protokolovací nástroj pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="90c40-165">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="90c40-166">Nepodporuje vytvoření testovacího projektu před jejím spuštěním.</span><span class="sxs-lookup"><span data-stu-id="90c40-166">Doesn't build the test project before running it.</span></span> <span data-ttu-id="90c40-167">Také implicitní nastaví `--no-restore` příznak.</span><span class="sxs-lookup"><span data-stu-id="90c40-167">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="90c40-168">Při spuštění příkazu se nebude spouštět implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="90c40-168">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="90c40-169">Adresář, ve kterém chcete najít binární soubory, které chcete spustit.</span><span class="sxs-lookup"><span data-stu-id="90c40-169">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="90c40-170">Adresář, kam výsledky testu budou umístěny.</span><span class="sxs-lookup"><span data-stu-id="90c40-170">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="90c40-171">Pokud zadaný adresář neexistuje, vytvoří se.</span><span class="sxs-lookup"><span data-stu-id="90c40-171">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="90c40-172">`.runsettings` Soubor se má použít pro spouštění testů.</span><span class="sxs-lookup"><span data-stu-id="90c40-172">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="90c40-173">Konfigurace testů jednotek s použitím `.runsettings` souboru.</span><span class="sxs-lookup"><span data-stu-id="90c40-173">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file?view=vs-2019)

`-t|--list-tests`

<span data-ttu-id="90c40-174">Seznam všech zjištěných testů v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="90c40-174">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="90c40-175">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="90c40-175">Sets the verbosity level of the command.</span></span> <span data-ttu-id="90c40-176">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="90c40-176">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="90c40-177">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="90c40-177">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="90c40-178">Používáte vlastní adaptéry testu ze zadané cesty v testovacím běhu.</span><span class="sxs-lookup"><span data-stu-id="90c40-178">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="90c40-179">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="90c40-179">Defines the build configuration.</span></span> <span data-ttu-id="90c40-180">Výchozí hodnota je `Debug`, ale váš projekt konfigurace může přepsat toto výchozí nastavení sady SDK.</span><span class="sxs-lookup"><span data-stu-id="90c40-180">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="90c40-181">Umožňuje diagnostickém režimu pro testovací platformy a zápis diagnostické zprávy do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="90c40-181">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="90c40-182">Vyhledá binárních souborů testu pro konkrétní [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="90c40-182">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="90c40-183">Filtruje testy v aktuálním projektu pomocí daného výrazu.</span><span class="sxs-lookup"><span data-stu-id="90c40-183">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="90c40-184">Další informace najdete v tématu [možnost podrobnosti filtru](#filter-option-details) oddílu.</span><span class="sxs-lookup"><span data-stu-id="90c40-184">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="90c40-185">Další informace a příklady o tom, jak použít selektivní jednotky filtrování testů, naleznete v tématu [spouštění selektivních testů jednotek](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="90c40-185">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="90c40-186">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="90c40-186">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="90c40-187">Určuje protokolovací nástroj pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="90c40-187">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="90c40-188">Nepodporuje vytvoření testovacího projektu před jejím spuštěním.</span><span class="sxs-lookup"><span data-stu-id="90c40-188">Doesn't build the test project before running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="90c40-189">Adresář, ve kterém chcete najít binární soubory, které chcete spustit.</span><span class="sxs-lookup"><span data-stu-id="90c40-189">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="90c40-190">`.runsettings` Soubor se má použít pro spouštění testů.</span><span class="sxs-lookup"><span data-stu-id="90c40-190">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="90c40-191">Konfigurace testů jednotek s použitím `.runsettings` souboru.</span><span class="sxs-lookup"><span data-stu-id="90c40-191">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file?view=vs-2019)

`-t|--list-tests`

<span data-ttu-id="90c40-192">Seznam všech zjištěných testů v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="90c40-192">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="90c40-193">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="90c40-193">Sets the verbosity level of the command.</span></span> <span data-ttu-id="90c40-194">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="90c40-194">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="90c40-195">Příklady</span><span class="sxs-lookup"><span data-stu-id="90c40-195">Examples</span></span>

<span data-ttu-id="90c40-196">Spusťte testy v projektu v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="90c40-196">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="90c40-197">Spustit testy v `test1` projektu:</span><span class="sxs-lookup"><span data-stu-id="90c40-197">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

<span data-ttu-id="90c40-198">Spuštění testů v projektu v aktuálním adresáři a vygenerovat soubor s výsledky testu ve formátu trx:</span><span class="sxs-lookup"><span data-stu-id="90c40-198">Run the tests in the project in the current directory and generate a test results file in the trx format:</span></span>

`dotnet test --logger:trx`

## <a name="filter-option-details"></a><span data-ttu-id="90c40-199">Možnost podrobnosti filtru</span><span class="sxs-lookup"><span data-stu-id="90c40-199">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="90c40-200">`<Expression>` má formát `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="90c40-200">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="90c40-201">`<property>` je atribut `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="90c40-201">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="90c40-202">Toto jsou vlastnosti podporované rozhraní pro testování částí oblíbených:</span><span class="sxs-lookup"><span data-stu-id="90c40-202">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="90c40-203">Rozhraní pro testování</span><span class="sxs-lookup"><span data-stu-id="90c40-203">Test Framework</span></span> | <span data-ttu-id="90c40-204">Podporovaných vlastností</span><span class="sxs-lookup"><span data-stu-id="90c40-204">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="90c40-205">MSTest</span><span class="sxs-lookup"><span data-stu-id="90c40-205">MSTest</span></span>         | <ul><li><span data-ttu-id="90c40-206">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="90c40-206">FullyQualifiedName</span></span></li><li><span data-ttu-id="90c40-207">Name</span><span class="sxs-lookup"><span data-stu-id="90c40-207">Name</span></span></li><li><span data-ttu-id="90c40-208">Název třídy</span><span class="sxs-lookup"><span data-stu-id="90c40-208">ClassName</span></span></li><li><span data-ttu-id="90c40-209">Priorita</span><span class="sxs-lookup"><span data-stu-id="90c40-209">Priority</span></span></li><li><span data-ttu-id="90c40-210">TestCategory</span><span class="sxs-lookup"><span data-stu-id="90c40-210">TestCategory</span></span></li></ul> |
| <span data-ttu-id="90c40-211">xUnit</span><span class="sxs-lookup"><span data-stu-id="90c40-211">xUnit</span></span>          | <ul><li><span data-ttu-id="90c40-212">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="90c40-212">FullyQualifiedName</span></span></li><li><span data-ttu-id="90c40-213">displayName</span><span class="sxs-lookup"><span data-stu-id="90c40-213">DisplayName</span></span></li><li><span data-ttu-id="90c40-214">Osobnostní rysy</span><span class="sxs-lookup"><span data-stu-id="90c40-214">Traits</span></span></li></ul>                                   |

<span data-ttu-id="90c40-215">`<operator>` Popisuje vztah mezi vlastnosti a hodnotu:</span><span class="sxs-lookup"><span data-stu-id="90c40-215">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="90c40-216">Operátor</span><span class="sxs-lookup"><span data-stu-id="90c40-216">Operator</span></span> | <span data-ttu-id="90c40-217">Funkce</span><span class="sxs-lookup"><span data-stu-id="90c40-217">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="90c40-218">Přesná shoda</span><span class="sxs-lookup"><span data-stu-id="90c40-218">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="90c40-219">Není přesná shoda</span><span class="sxs-lookup"><span data-stu-id="90c40-219">Not exact match</span></span> |
| `~`      | <span data-ttu-id="90c40-220">Obsahuje</span><span class="sxs-lookup"><span data-stu-id="90c40-220">Contains</span></span>        |

<span data-ttu-id="90c40-221">`<value>` je řetězec.</span><span class="sxs-lookup"><span data-stu-id="90c40-221">`<value>` is a string.</span></span> <span data-ttu-id="90c40-222">Všechna vyhledávání jsou malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="90c40-222">All the lookups are case insensitive.</span></span>

<span data-ttu-id="90c40-223">Výraz bez `<operator>` je automaticky považováno za `contains` na `FullyQualifiedName` vlastnosti (například `dotnet test --filter xyz` je stejná jako `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="90c40-223">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="90c40-224">Výrazy jde připojit k podmíněných operátorů:</span><span class="sxs-lookup"><span data-stu-id="90c40-224">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="90c40-225">Operátor</span><span class="sxs-lookup"><span data-stu-id="90c40-225">Operator</span></span>            | <span data-ttu-id="90c40-226">Funkce</span><span class="sxs-lookup"><span data-stu-id="90c40-226">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="90c40-227">NEBO</span><span class="sxs-lookup"><span data-stu-id="90c40-227">OR</span></span>       |
| `&`                 | <span data-ttu-id="90c40-228">AND</span><span class="sxs-lookup"><span data-stu-id="90c40-228">AND</span></span>      |

<span data-ttu-id="90c40-229">Je možné uzavřít do uvozovek výrazy v závorkách při použití podmíněných operátorů (například `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="90c40-229">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="90c40-230">Další informace a příklady o tom, jak použít selektivní jednotky filtrování testů, naleznete v tématu [spouštění selektivních testů jednotek](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="90c40-230">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="90c40-231">Viz také:</span><span class="sxs-lookup"><span data-stu-id="90c40-231">See also</span></span>

- [<span data-ttu-id="90c40-232">Architektury a cíle</span><span class="sxs-lookup"><span data-stu-id="90c40-232">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="90c40-233">.NET core Runtime identifikátor (RID) katalogu</span><span class="sxs-lookup"><span data-stu-id="90c40-233">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
