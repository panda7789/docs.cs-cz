---
title: příkaz DotNet test
description: Příkaz dotnet test slouží ke spuštění testů jednotek v daném projektu.
ms.date: 05/29/2018
ms.openlocfilehash: 1b2a3917a930db0c0a49ebea41f568aaf4a58ee3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54535279"
---
# <a name="dotnet-test"></a><span data-ttu-id="6d4d4-103">DotNet test</span><span class="sxs-lookup"><span data-stu-id="6d4d4-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="6d4d4-104">Název</span><span class="sxs-lookup"><span data-stu-id="6d4d4-104">Name</span></span>

<span data-ttu-id="6d4d4-105">`dotnet test` -Ovladač test .NET ke spuštění testů jednotek.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="6d4d4-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="6d4d4-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="6d4d4-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="6d4d4-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] 
    [-v|--verbosity] [-- <RunSettings arguments>]

dotnet test [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="6d4d4-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="6d4d4-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]

dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6d4d4-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="6d4d4-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]

dotnet test [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="6d4d4-110">Popis</span><span class="sxs-lookup"><span data-stu-id="6d4d4-110">Description</span></span>

<span data-ttu-id="6d4d4-111">`dotnet test` Příkaz se používá ke spuštění testů jednotek v daném projektu.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-111">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="6d4d4-112">`dotnet test` Příkaz spustí zadaný pro projekt test runner konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-112">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="6d4d4-113">Nástroj test runner sestavy úspěch nebo selhání jednotlivých testovacích a spustí testy, které jsou definovány pro rozhraní testování částí (například MSTest, NUnit nebo xUnit).</span><span class="sxs-lookup"><span data-stu-id="6d4d4-113">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="6d4d4-114">Pokud všechny testy jsou úspěšné, nástroj test runner vrátí hodnotu 0 jako ukončovací kód; jinak pokud nějaký test selže, vrátí se 1.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-114">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="6d4d4-115">Nástroj test runner a knihovnu testu jednotky jsou dodávány jako balíčky NuGet a se obnoví jako běžný závislosti projektu.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-115">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="6d4d4-116">Projekty testů zadat nástroje test runner pomocí běžný `<PackageReference>` elementu, jak je znázorněno v následující ukázkový soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="6d4d4-116">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="6d4d4-117">Arguments</span><span class="sxs-lookup"><span data-stu-id="6d4d4-117">Arguments</span></span>

`PROJECT`

<span data-ttu-id="6d4d4-118">Cesta k projektu testů.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-118">Path to the test project.</span></span> <span data-ttu-id="6d4d4-119">Pokud není zadán, použije se výchozí aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-119">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="6d4d4-120">Možnosti</span><span class="sxs-lookup"><span data-stu-id="6d4d4-120">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="6d4d4-121">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="6d4d4-121">.NET Core 2.1</span></span>](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="6d4d4-122">Používáte vlastní adaptéry testu ze zadané cesty v testovacím běhu.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-122">Use the custom test adapters from the specified path in the test run.</span></span>

`--blame`

<span data-ttu-id="6d4d4-123">Testy se spustí v režimu viny.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-123">Runs the tests in blame mode.</span></span> <span data-ttu-id="6d4d4-124">Tato možnost je užitečná v izolaci problematické testů způsobí hostitele testu při selhání.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-124">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="6d4d4-125">Vytvoří výstupní soubor v aktuálním adresáři jako *Sequence.xml* , který zachycuje pořadí provádění testů před selhání.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-125">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="6d4d4-126">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-126">Defines the build configuration.</span></span> <span data-ttu-id="6d4d4-127">Výchozí hodnota je `Debug`, ale váš projekt konfigurace může přepsat toto výchozí nastavení sady SDK.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-127">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="6d4d4-128">Povolí shromažďování dat pro testovací běh.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-128">Enables data collector for the test run.</span></span> <span data-ttu-id="6d4d4-129">Další informace najdete v tématu [monitorování a analýza testovacího běhu](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="6d4d4-129">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="6d4d4-130">Umožňuje diagnostickém režimu pro testovací platformy a zápis diagnostické zprávy do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-130">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="6d4d4-131">Vyhledá binárních souborů testu pro konkrétní [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="6d4d4-131">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="6d4d4-132">Filtruje testy v aktuálním projektu pomocí daného výrazu.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-132">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="6d4d4-133">Další informace najdete v tématu [možnost podrobnosti filtru](#filter-option-details) oddílu.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-133">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="6d4d4-134">Další informace a příklady o tom, jak použít selektivní jednotky filtrování testů, naleznete v tématu [spouštění selektivních testů jednotek](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="6d4d4-134">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="6d4d4-135">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-135">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="6d4d4-136">Určuje protokolovací nástroj pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-136">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="6d4d4-137">Nepodporuje vytvoření testovacího projektu před jejím spuštěním.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-137">Doesn't build the test project before running it.</span></span> <span data-ttu-id="6d4d4-138">Také implicitní nastaví `--no-restore` příznak.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-138">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="6d4d4-139">Při spuštění příkazu se nebude spouštět implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-139">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="6d4d4-140">Adresář, ve kterém chcete najít binární soubory, které chcete spustit.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-140">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="6d4d4-141">Adresář, kam výsledky testu budou umístěny.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-141">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="6d4d4-142">Pokud zadaný adresář neexistuje, vytvoří se.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-142">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="6d4d4-143">Nastavení se má použít při spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-143">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="6d4d4-144">Seznam všech zjištěných testů v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-144">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="6d4d4-145">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-145">Sets the verbosity level of the command.</span></span> <span data-ttu-id="6d4d4-146">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-146">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`RunSettings arguments`

<span data-ttu-id="6d4d4-147">Argumenty předány jako RunSettings Konfigurace testu.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-147">Arguments passed as RunSettings configurations for the test.</span></span> <span data-ttu-id="6d4d4-148">Argumenty se zadávají jako `[name]=[value]` dvojice po "--" (Poznámka: mezera za--).</span><span class="sxs-lookup"><span data-stu-id="6d4d4-148">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="6d4d4-149">Mezera se používá k oddělení více `[name]=[value]` dvojice.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-149">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

<span data-ttu-id="6d4d4-150">Příklad: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="6d4d4-150">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

<span data-ttu-id="6d4d4-151">Další informace o nastavení běhu, naleznete v tématu [vstest.console.exe: Předávání argumentů RunSettings](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="6d4d4-151">For more information about RunSettings, see [vstest.console.exe: Passing RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="6d4d4-152">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="6d4d4-152">.NET Core 2.0</span></span>](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="6d4d4-153">Používáte vlastní adaptéry testu ze zadané cesty v testovacím běhu.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-153">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="6d4d4-154">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-154">Defines the build configuration.</span></span> <span data-ttu-id="6d4d4-155">Výchozí hodnota je `Debug`, ale váš projekt konfigurace může přepsat toto výchozí nastavení sady SDK.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-155">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="6d4d4-156">Povolí shromažďování dat pro testovací běh.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-156">Enables data collector for the test run.</span></span> <span data-ttu-id="6d4d4-157">Další informace najdete v tématu [monitorování a analýza testovacího běhu](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="6d4d4-157">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="6d4d4-158">Umožňuje diagnostickém režimu pro testovací platformy a zápis diagnostické zprávy do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-158">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="6d4d4-159">Vyhledá binárních souborů testu pro konkrétní [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="6d4d4-159">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="6d4d4-160">Filtruje testy v aktuálním projektu pomocí daného výrazu.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-160">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="6d4d4-161">Další informace najdete v tématu [možnost podrobnosti filtru](#filter-option-details) oddílu.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-161">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="6d4d4-162">Další informace a příklady o tom, jak použít selektivní jednotky filtrování testů, naleznete v tématu [spouštění selektivních testů jednotek](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="6d4d4-162">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="6d4d4-163">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-163">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="6d4d4-164">Určuje protokolovací nástroj pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-164">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="6d4d4-165">Nepodporuje vytvoření testovacího projektu před jejím spuštěním.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-165">Doesn't build the test project before running it.</span></span> <span data-ttu-id="6d4d4-166">Také implicitní nastaví `--no-restore` příznak.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-166">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="6d4d4-167">Při spuštění příkazu se nebude spouštět implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-167">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="6d4d4-168">Adresář, ve kterém chcete najít binární soubory, které chcete spustit.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-168">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="6d4d4-169">Adresář, kam výsledky testu budou umístěny.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-169">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="6d4d4-170">Pokud zadaný adresář neexistuje, vytvoří se.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-170">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="6d4d4-171">Nastavení se má použít při spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-171">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="6d4d4-172">Seznam všech zjištěných testů v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-172">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="6d4d4-173">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-173">Sets the verbosity level of the command.</span></span> <span data-ttu-id="6d4d4-174">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-174">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6d4d4-175">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="6d4d4-175">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="6d4d4-176">Používáte vlastní adaptéry testu ze zadané cesty v testovacím běhu.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-176">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="6d4d4-177">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-177">Defines the build configuration.</span></span> <span data-ttu-id="6d4d4-178">Výchozí hodnota je `Debug`, ale váš projekt konfigurace může přepsat toto výchozí nastavení sady SDK.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-178">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="6d4d4-179">Umožňuje diagnostickém režimu pro testovací platformy a zápis diagnostické zprávy do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-179">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="6d4d4-180">Vyhledá binárních souborů testu pro konkrétní [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="6d4d4-180">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="6d4d4-181">Filtruje testy v aktuálním projektu pomocí daného výrazu.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-181">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="6d4d4-182">Další informace najdete v tématu [možnost podrobnosti filtru](#filter-option-details) oddílu.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-182">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="6d4d4-183">Další informace a příklady o tom, jak použít selektivní jednotky filtrování testů, naleznete v tématu [spouštění selektivních testů jednotek](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="6d4d4-183">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="6d4d4-184">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-184">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="6d4d4-185">Určuje protokolovací nástroj pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-185">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="6d4d4-186">Nepodporuje vytvoření testovacího projektu před jejím spuštěním.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-186">Doesn't build the test project before running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="6d4d4-187">Adresář, ve kterém chcete najít binární soubory, které chcete spustit.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-187">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="6d4d4-188">Nastavení se má použít při spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-188">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="6d4d4-189">Seznam všech zjištěných testů v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-189">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="6d4d4-190">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-190">Sets the verbosity level of the command.</span></span> <span data-ttu-id="6d4d4-191">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-191">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="6d4d4-192">Příklady</span><span class="sxs-lookup"><span data-stu-id="6d4d4-192">Examples</span></span>

<span data-ttu-id="6d4d4-193">Spusťte testy v projektu v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="6d4d4-193">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="6d4d4-194">Spustit testy v `test1` projektu:</span><span class="sxs-lookup"><span data-stu-id="6d4d4-194">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

<span data-ttu-id="6d4d4-195">Spuštění testů v projektu v aktuálním adresáři a vygenerovat soubor s výsledky testu ve formátu trx:</span><span class="sxs-lookup"><span data-stu-id="6d4d4-195">Run the tests in the project in the current directory and generate a test results file in the trx format:</span></span>

`dotnet test --logger:trx`

## <a name="filter-option-details"></a><span data-ttu-id="6d4d4-196">Možnost podrobnosti filtru</span><span class="sxs-lookup"><span data-stu-id="6d4d4-196">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="6d4d4-197">`<Expression>` má formát `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-197">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="6d4d4-198">`<property>` je atribut `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-198">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="6d4d4-199">Toto jsou vlastnosti podporované rozhraní pro testování částí oblíbených:</span><span class="sxs-lookup"><span data-stu-id="6d4d4-199">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="6d4d4-200">Rozhraní pro testování</span><span class="sxs-lookup"><span data-stu-id="6d4d4-200">Test Framework</span></span> | <span data-ttu-id="6d4d4-201">Podporovaných vlastností</span><span class="sxs-lookup"><span data-stu-id="6d4d4-201">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="6d4d4-202">MSTest</span><span class="sxs-lookup"><span data-stu-id="6d4d4-202">MSTest</span></span>         | <ul><li><span data-ttu-id="6d4d4-203">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="6d4d4-203">FullyQualifiedName</span></span></li><li><span data-ttu-id="6d4d4-204">Název</span><span class="sxs-lookup"><span data-stu-id="6d4d4-204">Name</span></span></li><li><span data-ttu-id="6d4d4-205">Název třídy</span><span class="sxs-lookup"><span data-stu-id="6d4d4-205">ClassName</span></span></li><li><span data-ttu-id="6d4d4-206">Priorita</span><span class="sxs-lookup"><span data-stu-id="6d4d4-206">Priority</span></span></li><li><span data-ttu-id="6d4d4-207">TestCategory</span><span class="sxs-lookup"><span data-stu-id="6d4d4-207">TestCategory</span></span></li></ul> |
| <span data-ttu-id="6d4d4-208">xUnit</span><span class="sxs-lookup"><span data-stu-id="6d4d4-208">xUnit</span></span>          | <ul><li><span data-ttu-id="6d4d4-209">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="6d4d4-209">FullyQualifiedName</span></span></li><li><span data-ttu-id="6d4d4-210">displayName</span><span class="sxs-lookup"><span data-stu-id="6d4d4-210">DisplayName</span></span></li><li><span data-ttu-id="6d4d4-211">Osobnostní rysy</span><span class="sxs-lookup"><span data-stu-id="6d4d4-211">Traits</span></span></li></ul>                                   |

<span data-ttu-id="6d4d4-212">`<operator>` Popisuje vztah mezi vlastnosti a hodnotu:</span><span class="sxs-lookup"><span data-stu-id="6d4d4-212">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="6d4d4-213">Operátor</span><span class="sxs-lookup"><span data-stu-id="6d4d4-213">Operator</span></span> | <span data-ttu-id="6d4d4-214">Funkce</span><span class="sxs-lookup"><span data-stu-id="6d4d4-214">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="6d4d4-215">Přesná shoda</span><span class="sxs-lookup"><span data-stu-id="6d4d4-215">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="6d4d4-216">Není přesná shoda</span><span class="sxs-lookup"><span data-stu-id="6d4d4-216">Not exact match</span></span> |
| `~`      | <span data-ttu-id="6d4d4-217">Obsahuje</span><span class="sxs-lookup"><span data-stu-id="6d4d4-217">Contains</span></span>        |

<span data-ttu-id="6d4d4-218">`<value>` je řetězec.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-218">`<value>` is a string.</span></span> <span data-ttu-id="6d4d4-219">Všechna vyhledávání jsou malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="6d4d4-219">All the lookups are case insensitive.</span></span>

<span data-ttu-id="6d4d4-220">Výraz bez `<operator>` je automaticky považováno za `contains` na `FullyQualifiedName` vlastnosti (například `dotnet test --filter xyz` je stejná jako `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="6d4d4-220">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="6d4d4-221">Výrazy jde připojit k podmíněných operátorů:</span><span class="sxs-lookup"><span data-stu-id="6d4d4-221">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="6d4d4-222">Operátor</span><span class="sxs-lookup"><span data-stu-id="6d4d4-222">Operator</span></span>            | <span data-ttu-id="6d4d4-223">Funkce</span><span class="sxs-lookup"><span data-stu-id="6d4d4-223">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="6d4d4-224">NEBO</span><span class="sxs-lookup"><span data-stu-id="6d4d4-224">OR</span></span>       |
| `&`                 | <span data-ttu-id="6d4d4-225">AND</span><span class="sxs-lookup"><span data-stu-id="6d4d4-225">AND</span></span>      |

<span data-ttu-id="6d4d4-226">Je možné uzavřít do uvozovek výrazy v závorkách při použití podmíněných operátorů (například `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="6d4d4-226">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="6d4d4-227">Další informace a příklady o tom, jak použít selektivní jednotky filtrování testů, naleznete v tématu [spouštění selektivních testů jednotek](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="6d4d4-227">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6d4d4-228">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6d4d4-228">See also</span></span>

- [<span data-ttu-id="6d4d4-229">Architektury a cíle</span><span class="sxs-lookup"><span data-stu-id="6d4d4-229">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="6d4d4-230">.NET core Runtime identifikátor (RID) katalogu</span><span class="sxs-lookup"><span data-stu-id="6d4d4-230">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
