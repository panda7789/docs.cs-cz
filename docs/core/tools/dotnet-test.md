---
title: příkaz DotNet test – rozhraní příkazového řádku .NET Core
description: Příkaz dotnet test slouží ke spuštění testů jednotek v daném projektu.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 73b1d832b855798dd053187bbb24e8fb989fedf1
ms.sourcegitcommit: 3b1cb8467bd73dee854b604e306c0e7e3882d91a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2018
ms.locfileid: "46696453"
---
# <a name="dotnet-test"></a><span data-ttu-id="73003-103">DotNet test</span><span class="sxs-lookup"><span data-stu-id="73003-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="73003-104">Název</span><span class="sxs-lookup"><span data-stu-id="73003-104">Name</span></span>

<span data-ttu-id="73003-105">`dotnet test` -Ovladač test .NET ke spuštění testů jednotek.</span><span class="sxs-lookup"><span data-stu-id="73003-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="73003-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="73003-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="73003-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="73003-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] 
    [-v|--verbosity] [-- <RunSettings arguments>]

dotnet test [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="73003-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="73003-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]

dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="73003-109">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="73003-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]

dotnet test [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="73003-110">Popis</span><span class="sxs-lookup"><span data-stu-id="73003-110">Description</span></span>

<span data-ttu-id="73003-111">`dotnet test` Příkaz se používá ke spuštění testů jednotek v daném projektu.</span><span class="sxs-lookup"><span data-stu-id="73003-111">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="73003-112">`dotnet test` Příkaz spustí zadaný pro projekt test runner konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="73003-112">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="73003-113">Nástroj test runner sestavy úspěch nebo selhání jednotlivých testovacích a spustí testy, které jsou definovány pro rozhraní testování částí (například MSTest, NUnit nebo xUnit).</span><span class="sxs-lookup"><span data-stu-id="73003-113">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="73003-114">Pokud všechny testy jsou úspěšné, nástroj test runner vrátí hodnotu 0 jako ukončovací kód; jinak pokud nějaký test selže, vrátí se 1.</span><span class="sxs-lookup"><span data-stu-id="73003-114">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="73003-115">Nástroj test runner a knihovnu testu jednotky jsou dodávány jako balíčky NuGet a se obnoví jako běžný závislosti projektu.</span><span class="sxs-lookup"><span data-stu-id="73003-115">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="73003-116">Projekty testů zadat nástroje test runner pomocí běžný `<PackageReference>` elementu, jak je znázorněno v následující ukázkový soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="73003-116">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="73003-117">Arguments</span><span class="sxs-lookup"><span data-stu-id="73003-117">Arguments</span></span>

`PROJECT`

<span data-ttu-id="73003-118">Cesta k projektu testů.</span><span class="sxs-lookup"><span data-stu-id="73003-118">Path to the test project.</span></span> <span data-ttu-id="73003-119">Pokud není zadán, použije se výchozí aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="73003-119">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="73003-120">Možnosti</span><span class="sxs-lookup"><span data-stu-id="73003-120">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="73003-121">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="73003-121">.NET Core 2.1</span></span>](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="73003-122">Používáte vlastní adaptéry testu ze zadané cesty v testovacím běhu.</span><span class="sxs-lookup"><span data-stu-id="73003-122">Use the custom test adapters from the specified path in the test run.</span></span>

`--blame`

<span data-ttu-id="73003-123">Testy se spustí v režimu viny.</span><span class="sxs-lookup"><span data-stu-id="73003-123">Runs the tests in blame mode.</span></span> <span data-ttu-id="73003-124">Tato možnost je užitečná v izolaci problematické testů způsobí hostitele testu při selhání.</span><span class="sxs-lookup"><span data-stu-id="73003-124">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="73003-125">Vytvoří výstupní soubor v aktuálním adresáři jako *Sequence.xml* , který zachycuje pořadí provádění testů před selhání.</span><span class="sxs-lookup"><span data-stu-id="73003-125">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="73003-126">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="73003-126">Defines the build configuration.</span></span> <span data-ttu-id="73003-127">Výchozí hodnota je `Debug`, ale váš projekt konfigurace může přepsat toto výchozí nastavení sady SDK.</span><span class="sxs-lookup"><span data-stu-id="73003-127">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="73003-128">Povolí shromažďování dat pro testovací běh.</span><span class="sxs-lookup"><span data-stu-id="73003-128">Enables data collector for the test run.</span></span> <span data-ttu-id="73003-129">Další informace najdete v tématu [monitorování a analýza testovacího běhu](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="73003-129">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="73003-130">Umožňuje diagnostickém režimu pro testovací platformy a zápis diagnostické zprávy do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="73003-130">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="73003-131">Vyhledá binárních souborů testu pro konkrétní [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="73003-131">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="73003-132">Filtruje testy v aktuálním projektu pomocí daného výrazu.</span><span class="sxs-lookup"><span data-stu-id="73003-132">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="73003-133">Další informace najdete v tématu [možnost podrobnosti filtru](#filter-option-details) oddílu.</span><span class="sxs-lookup"><span data-stu-id="73003-133">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="73003-134">Další informace a příklady o tom, jak použít selektivní jednotky filtrování testů, naleznete v tématu [spouštění selektivních testů jednotek](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="73003-134">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="73003-135">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="73003-135">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="73003-136">Určuje protokolovací nástroj pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="73003-136">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="73003-137">Nepodporuje vytvoření testovacího projektu před jejím spuštěním.</span><span class="sxs-lookup"><span data-stu-id="73003-137">Doesn't build the test project before running it.</span></span> <span data-ttu-id="73003-138">Také implicitní nastaví `--no-restore` příznak.</span><span class="sxs-lookup"><span data-stu-id="73003-138">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="73003-139">Při spuštění příkazu se nebude spouštět implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="73003-139">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="73003-140">Adresář, ve kterém chcete najít binární soubory, které chcete spustit.</span><span class="sxs-lookup"><span data-stu-id="73003-140">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="73003-141">Adresář, kam výsledky testu budou umístěny.</span><span class="sxs-lookup"><span data-stu-id="73003-141">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="73003-142">Pokud zadaný adresář neexistuje, vytvoří se.</span><span class="sxs-lookup"><span data-stu-id="73003-142">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="73003-143">Nastavení se má použít při spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="73003-143">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="73003-144">Seznam všech zjištěných testů v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="73003-144">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="73003-145">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="73003-145">Sets the verbosity level of the command.</span></span> <span data-ttu-id="73003-146">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="73003-146">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`RunSettings arguments`

<span data-ttu-id="73003-147">Argumenty předány jako RunSettings Konfigurace testu.</span><span class="sxs-lookup"><span data-stu-id="73003-147">Arguments passed as RunSettings configurations for the test.</span></span> <span data-ttu-id="73003-148">Argumenty se zadávají jako `[name]=[value]` dvojice po "--" (Poznámka: mezera za--).</span><span class="sxs-lookup"><span data-stu-id="73003-148">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="73003-149">Mezera se používá k oddělení více `[name]=[value]` dvojice.</span><span class="sxs-lookup"><span data-stu-id="73003-149">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

<span data-ttu-id="73003-150">Příklad: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="73003-150">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

<span data-ttu-id="73003-151">Další informace o nastavení běhu, naleznete v tématu [vstest.console.exe: předání RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="73003-151">For more information about RunSettings, see [vstest.console.exe: Passing RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="73003-152">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="73003-152">.NET Core 2.0</span></span>](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="73003-153">Používáte vlastní adaptéry testu ze zadané cesty v testovacím běhu.</span><span class="sxs-lookup"><span data-stu-id="73003-153">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="73003-154">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="73003-154">Defines the build configuration.</span></span> <span data-ttu-id="73003-155">Výchozí hodnota je `Debug`, ale váš projekt konfigurace může přepsat toto výchozí nastavení sady SDK.</span><span class="sxs-lookup"><span data-stu-id="73003-155">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="73003-156">Povolí shromažďování dat pro testovací běh.</span><span class="sxs-lookup"><span data-stu-id="73003-156">Enables data collector for the test run.</span></span> <span data-ttu-id="73003-157">Další informace najdete v tématu [monitorování a analýza testovacího běhu](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="73003-157">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="73003-158">Umožňuje diagnostickém režimu pro testovací platformy a zápis diagnostické zprávy do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="73003-158">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="73003-159">Vyhledá binárních souborů testu pro konkrétní [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="73003-159">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="73003-160">Filtruje testy v aktuálním projektu pomocí daného výrazu.</span><span class="sxs-lookup"><span data-stu-id="73003-160">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="73003-161">Další informace najdete v tématu [možnost podrobnosti filtru](#filter-option-details) oddílu.</span><span class="sxs-lookup"><span data-stu-id="73003-161">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="73003-162">Další informace a příklady o tom, jak použít selektivní jednotky filtrování testů, naleznete v tématu [spouštění selektivních testů jednotek](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="73003-162">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="73003-163">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="73003-163">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="73003-164">Určuje protokolovací nástroj pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="73003-164">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="73003-165">Nepodporuje vytvoření testovacího projektu před jejím spuštěním.</span><span class="sxs-lookup"><span data-stu-id="73003-165">Doesn't build the test project before running it.</span></span> <span data-ttu-id="73003-166">Také implicitní nastaví `--no-restore` příznak.</span><span class="sxs-lookup"><span data-stu-id="73003-166">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="73003-167">Při spuštění příkazu se nebude spouštět implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="73003-167">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="73003-168">Adresář, ve kterém chcete najít binární soubory, které chcete spustit.</span><span class="sxs-lookup"><span data-stu-id="73003-168">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="73003-169">Adresář, kam výsledky testu budou umístěny.</span><span class="sxs-lookup"><span data-stu-id="73003-169">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="73003-170">Pokud zadaný adresář neexistuje, vytvoří se.</span><span class="sxs-lookup"><span data-stu-id="73003-170">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="73003-171">Nastavení se má použít při spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="73003-171">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="73003-172">Seznam všech zjištěných testů v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="73003-172">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="73003-173">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="73003-173">Sets the verbosity level of the command.</span></span> <span data-ttu-id="73003-174">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="73003-174">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="73003-175">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="73003-175">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="73003-176">Používáte vlastní adaptéry testu ze zadané cesty v testovacím běhu.</span><span class="sxs-lookup"><span data-stu-id="73003-176">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="73003-177">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="73003-177">Defines the build configuration.</span></span> <span data-ttu-id="73003-178">Výchozí hodnota je `Debug`, ale váš projekt konfigurace může přepsat toto výchozí nastavení sady SDK.</span><span class="sxs-lookup"><span data-stu-id="73003-178">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="73003-179">Umožňuje diagnostickém režimu pro testovací platformy a zápis diagnostické zprávy do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="73003-179">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="73003-180">Vyhledá binárních souborů testu pro konkrétní [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="73003-180">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="73003-181">Filtruje testy v aktuálním projektu pomocí daného výrazu.</span><span class="sxs-lookup"><span data-stu-id="73003-181">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="73003-182">Další informace najdete v tématu [možnost podrobnosti filtru](#filter-option-details) oddílu.</span><span class="sxs-lookup"><span data-stu-id="73003-182">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="73003-183">Další informace a příklady o tom, jak použít selektivní jednotky filtrování testů, naleznete v tématu [spouštění selektivních testů jednotek](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="73003-183">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="73003-184">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="73003-184">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="73003-185">Určuje protokolovací nástroj pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="73003-185">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="73003-186">Nepodporuje vytvoření testovacího projektu před jejím spuštěním.</span><span class="sxs-lookup"><span data-stu-id="73003-186">Doesn't build the test project before running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="73003-187">Adresář, ve kterém chcete najít binární soubory, které chcete spustit.</span><span class="sxs-lookup"><span data-stu-id="73003-187">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="73003-188">Nastavení se má použít při spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="73003-188">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="73003-189">Seznam všech zjištěných testů v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="73003-189">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="73003-190">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="73003-190">Sets the verbosity level of the command.</span></span> <span data-ttu-id="73003-191">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="73003-191">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="73003-192">Příklady</span><span class="sxs-lookup"><span data-stu-id="73003-192">Examples</span></span>

<span data-ttu-id="73003-193">Spusťte testy v projektu v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="73003-193">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="73003-194">Spustit testy v `test1` projektu:</span><span class="sxs-lookup"><span data-stu-id="73003-194">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

<span data-ttu-id="73003-195">Spuštění testů v projektu v aktuálním adresáři a vygenerovat soubor s výsledky testu ve formátu trx:</span><span class="sxs-lookup"><span data-stu-id="73003-195">Run the tests in the project in the current directory and generate a test results file in the trx format:</span></span>

`dotnet test --logger:trx`

## <a name="filter-option-details"></a><span data-ttu-id="73003-196">Možnost podrobnosti filtru</span><span class="sxs-lookup"><span data-stu-id="73003-196">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="73003-197">`<Expression>` má formát `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="73003-197">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="73003-198">`<property>` je atribut `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="73003-198">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="73003-199">Toto jsou vlastnosti podporované rozhraní pro testování částí oblíbených:</span><span class="sxs-lookup"><span data-stu-id="73003-199">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="73003-200">Rozhraní pro testování</span><span class="sxs-lookup"><span data-stu-id="73003-200">Test Framework</span></span> | <span data-ttu-id="73003-201">Podporovaných vlastností</span><span class="sxs-lookup"><span data-stu-id="73003-201">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="73003-202">MSTest</span><span class="sxs-lookup"><span data-stu-id="73003-202">MSTest</span></span>         | <ul><li><span data-ttu-id="73003-203">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="73003-203">FullyQualifiedName</span></span></li><li><span data-ttu-id="73003-204">Název</span><span class="sxs-lookup"><span data-stu-id="73003-204">Name</span></span></li><li><span data-ttu-id="73003-205">Název třídy</span><span class="sxs-lookup"><span data-stu-id="73003-205">ClassName</span></span></li><li><span data-ttu-id="73003-206">Priorita</span><span class="sxs-lookup"><span data-stu-id="73003-206">Priority</span></span></li><li><span data-ttu-id="73003-207">TestCategory</span><span class="sxs-lookup"><span data-stu-id="73003-207">TestCategory</span></span></li></ul> |
| <span data-ttu-id="73003-208">xUnit</span><span class="sxs-lookup"><span data-stu-id="73003-208">xUnit</span></span>          | <ul><li><span data-ttu-id="73003-209">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="73003-209">FullyQualifiedName</span></span></li><li><span data-ttu-id="73003-210">displayName</span><span class="sxs-lookup"><span data-stu-id="73003-210">DisplayName</span></span></li><li><span data-ttu-id="73003-211">Osobnostní rysy</span><span class="sxs-lookup"><span data-stu-id="73003-211">Traits</span></span></li></ul>                                   |

<span data-ttu-id="73003-212">`<operator>` Popisuje vztah mezi vlastnosti a hodnotu:</span><span class="sxs-lookup"><span data-stu-id="73003-212">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="73003-213">Operátor</span><span class="sxs-lookup"><span data-stu-id="73003-213">Operator</span></span> | <span data-ttu-id="73003-214">Funkce</span><span class="sxs-lookup"><span data-stu-id="73003-214">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="73003-215">Přesná shoda</span><span class="sxs-lookup"><span data-stu-id="73003-215">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="73003-216">Není přesná shoda</span><span class="sxs-lookup"><span data-stu-id="73003-216">Not exact match</span></span> |
| `~`      | <span data-ttu-id="73003-217">Obsahuje</span><span class="sxs-lookup"><span data-stu-id="73003-217">Contains</span></span>        |

<span data-ttu-id="73003-218">`<value>` je řetězec.</span><span class="sxs-lookup"><span data-stu-id="73003-218">`<value>` is a string.</span></span> <span data-ttu-id="73003-219">Všechna vyhledávání jsou malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="73003-219">All the lookups are case insensitive.</span></span>

<span data-ttu-id="73003-220">Výraz bez `<operator>` je automaticky považováno za `contains` na `FullyQualifiedName` vlastnosti (například `dotnet test --filter xyz` je stejná jako `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="73003-220">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="73003-221">Výrazy jde připojit k podmíněných operátorů:</span><span class="sxs-lookup"><span data-stu-id="73003-221">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="73003-222">Operátor</span><span class="sxs-lookup"><span data-stu-id="73003-222">Operator</span></span>            | <span data-ttu-id="73003-223">Funkce</span><span class="sxs-lookup"><span data-stu-id="73003-223">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="73003-224">NEBO</span><span class="sxs-lookup"><span data-stu-id="73003-224">OR</span></span>       |
| `&`                 | <span data-ttu-id="73003-225">AND</span><span class="sxs-lookup"><span data-stu-id="73003-225">AND</span></span>      |

<span data-ttu-id="73003-226">Je možné uzavřít do uvozovek výrazy v závorkách při použití podmíněných operátorů (například `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="73003-226">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="73003-227">Další informace a příklady o tom, jak použít selektivní jednotky filtrování testů, naleznete v tématu [spouštění selektivních testů jednotek](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="73003-227">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="73003-228">Viz také:</span><span class="sxs-lookup"><span data-stu-id="73003-228">See also</span></span>

* [<span data-ttu-id="73003-229">Architektury a cíle</span><span class="sxs-lookup"><span data-stu-id="73003-229">Frameworks and Targets</span></span>](../../standard/frameworks.md)  
* [<span data-ttu-id="73003-230">.NET core Runtime identifikátor (RID) katalogu</span><span class="sxs-lookup"><span data-stu-id="73003-230">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
