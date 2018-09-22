---
title: příkaz DotNet test – rozhraní příkazového řádku .NET Core
description: Příkaz dotnet test slouží ke spuštění testů jednotek v daném projektu.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: e80ba874ec8d0fbc49858719dc3b9b6e02254c78
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46696453"
---
# <a name="dotnet-test"></a><span data-ttu-id="ff30a-103">DotNet test</span><span class="sxs-lookup"><span data-stu-id="ff30a-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="ff30a-104">Název</span><span class="sxs-lookup"><span data-stu-id="ff30a-104">Name</span></span>

<span data-ttu-id="ff30a-105">`dotnet test` -Ovladač test .NET ke spuštění testů jednotek.</span><span class="sxs-lookup"><span data-stu-id="ff30a-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ff30a-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="ff30a-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="ff30a-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="ff30a-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="ff30a-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="ff30a-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ff30a-109">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="ff30a-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]
dotnet test [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="ff30a-110">Popis</span><span class="sxs-lookup"><span data-stu-id="ff30a-110">Description</span></span>

<span data-ttu-id="ff30a-111">`dotnet test` Příkaz se používá ke spuštění testů jednotek v daném projektu.</span><span class="sxs-lookup"><span data-stu-id="ff30a-111">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="ff30a-112">`dotnet test` Příkaz spustí zadaný pro projekt test runner konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ff30a-112">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="ff30a-113">Nástroj test runner sestavy úspěch nebo selhání jednotlivých testovacích a spustí testy, které jsou definovány pro rozhraní testování částí (například MSTest, NUnit nebo xUnit).</span><span class="sxs-lookup"><span data-stu-id="ff30a-113">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="ff30a-114">Pokud všechny testy jsou úspěšné, nástroj test runner vrátí hodnotu 0 jako ukončovací kód; jinak pokud nějaký test selže, vrátí se 1.</span><span class="sxs-lookup"><span data-stu-id="ff30a-114">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="ff30a-115">Nástroj test runner a knihovnu testu jednotky jsou dodávány jako balíčky NuGet a se obnoví jako běžný závislosti projektu.</span><span class="sxs-lookup"><span data-stu-id="ff30a-115">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="ff30a-116">Projekty testů zadat nástroje test runner pomocí běžný `<PackageReference>` elementu, jak je znázorněno v následující ukázkový soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="ff30a-116">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="ff30a-117">Arguments</span><span class="sxs-lookup"><span data-stu-id="ff30a-117">Arguments</span></span>

`PROJECT`

<span data-ttu-id="ff30a-118">Cesta k projektu testů.</span><span class="sxs-lookup"><span data-stu-id="ff30a-118">Path to the test project.</span></span> <span data-ttu-id="ff30a-119">Pokud není zadán, použije se výchozí aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="ff30a-119">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="ff30a-120">Možnosti</span><span class="sxs-lookup"><span data-stu-id="ff30a-120">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="ff30a-121">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="ff30a-121">.NET Core 2.1</span></span>](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="ff30a-122">Používáte vlastní adaptéry testu ze zadané cesty v testovacím běhu.</span><span class="sxs-lookup"><span data-stu-id="ff30a-122">Use the custom test adapters from the specified path in the test run.</span></span>

`--blame`

<span data-ttu-id="ff30a-123">Testy se spustí v režimu viny.</span><span class="sxs-lookup"><span data-stu-id="ff30a-123">Runs the tests in blame mode.</span></span> <span data-ttu-id="ff30a-124">Tato možnost je užitečná v izolaci problematické testů způsobí hostitele testu při selhání.</span><span class="sxs-lookup"><span data-stu-id="ff30a-124">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="ff30a-125">Vytvoří výstupní soubor v aktuálním adresáři jako *Sequence.xml* , který zachycuje pořadí provádění testů před selhání.</span><span class="sxs-lookup"><span data-stu-id="ff30a-125">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="ff30a-126">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="ff30a-126">Defines the build configuration.</span></span> <span data-ttu-id="ff30a-127">Výchozí hodnota je `Debug`, ale váš projekt konfigurace může přepsat toto výchozí nastavení sady SDK.</span><span class="sxs-lookup"><span data-stu-id="ff30a-127">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="ff30a-128">Povolí shromažďování dat pro testovací běh.</span><span class="sxs-lookup"><span data-stu-id="ff30a-128">Enables data collector for the test run.</span></span> <span data-ttu-id="ff30a-129">Další informace najdete v tématu [monitorování a analýza testovacího běhu](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="ff30a-129">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="ff30a-130">Umožňuje diagnostickém režimu pro testovací platformy a zápis diagnostické zprávy do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="ff30a-130">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="ff30a-131">Vyhledá binárních souborů testu pro konkrétní [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="ff30a-131">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="ff30a-132">Filtruje testy v aktuálním projektu pomocí daného výrazu.</span><span class="sxs-lookup"><span data-stu-id="ff30a-132">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="ff30a-133">Další informace najdete v tématu [možnost podrobnosti filtru](#filter-option-details) oddílu.</span><span class="sxs-lookup"><span data-stu-id="ff30a-133">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="ff30a-134">Další informace a příklady o tom, jak použít selektivní jednotky filtrování testů, naleznete v tématu [spouštění selektivních testů jednotek](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="ff30a-134">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="ff30a-135">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="ff30a-135">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="ff30a-136">Určuje protokolovací nástroj pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="ff30a-136">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="ff30a-137">Nepodporuje vytvoření testovacího projektu před jejím spuštěním.</span><span class="sxs-lookup"><span data-stu-id="ff30a-137">Doesn't build the test project before running it.</span></span> <span data-ttu-id="ff30a-138">Také implicitní nastaví `--no-restore` příznak.</span><span class="sxs-lookup"><span data-stu-id="ff30a-138">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="ff30a-139">Při spuštění příkazu se nebude spouštět implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="ff30a-139">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="ff30a-140">Adresář, ve kterém chcete najít binární soubory, které chcete spustit.</span><span class="sxs-lookup"><span data-stu-id="ff30a-140">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="ff30a-141">Adresář, kam výsledky testu budou umístěny.</span><span class="sxs-lookup"><span data-stu-id="ff30a-141">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="ff30a-142">Pokud zadaný adresář neexistuje, vytvoří se.</span><span class="sxs-lookup"><span data-stu-id="ff30a-142">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="ff30a-143">Nastavení se má použít při spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="ff30a-143">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="ff30a-144">Seznam všech zjištěných testů v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="ff30a-144">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="ff30a-145">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="ff30a-145">Sets the verbosity level of the command.</span></span> <span data-ttu-id="ff30a-146">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="ff30a-146">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="ff30a-147">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="ff30a-147">.NET Core 2.0</span></span>](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="ff30a-148">Používáte vlastní adaptéry testu ze zadané cesty v testovacím běhu.</span><span class="sxs-lookup"><span data-stu-id="ff30a-148">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="ff30a-149">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="ff30a-149">Defines the build configuration.</span></span> <span data-ttu-id="ff30a-150">Výchozí hodnota je `Debug`, ale váš projekt konfigurace může přepsat toto výchozí nastavení sady SDK.</span><span class="sxs-lookup"><span data-stu-id="ff30a-150">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="ff30a-151">Povolí shromažďování dat pro testovací běh.</span><span class="sxs-lookup"><span data-stu-id="ff30a-151">Enables data collector for the test run.</span></span> <span data-ttu-id="ff30a-152">Další informace najdete v tématu [monitorování a analýza testovacího běhu](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="ff30a-152">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="ff30a-153">Umožňuje diagnostickém režimu pro testovací platformy a zápis diagnostické zprávy do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="ff30a-153">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="ff30a-154">Vyhledá binárních souborů testu pro konkrétní [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="ff30a-154">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="ff30a-155">Filtruje testy v aktuálním projektu pomocí daného výrazu.</span><span class="sxs-lookup"><span data-stu-id="ff30a-155">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="ff30a-156">Další informace najdete v tématu [možnost podrobnosti filtru](#filter-option-details) oddílu.</span><span class="sxs-lookup"><span data-stu-id="ff30a-156">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="ff30a-157">Další informace a příklady o tom, jak použít selektivní jednotky filtrování testů, naleznete v tématu [spouštění selektivních testů jednotek](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="ff30a-157">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="ff30a-158">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="ff30a-158">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="ff30a-159">Určuje protokolovací nástroj pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="ff30a-159">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="ff30a-160">Nepodporuje vytvoření testovacího projektu před jejím spuštěním.</span><span class="sxs-lookup"><span data-stu-id="ff30a-160">Doesn't build the test project before running it.</span></span> <span data-ttu-id="ff30a-161">Také implicitní nastaví `--no-restore` příznak.</span><span class="sxs-lookup"><span data-stu-id="ff30a-161">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="ff30a-162">Při spuštění příkazu se nebude spouštět implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="ff30a-162">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="ff30a-163">Adresář, ve kterém chcete najít binární soubory, které chcete spustit.</span><span class="sxs-lookup"><span data-stu-id="ff30a-163">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="ff30a-164">Adresář, kam výsledky testu budou umístěny.</span><span class="sxs-lookup"><span data-stu-id="ff30a-164">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="ff30a-165">Pokud zadaný adresář neexistuje, vytvoří se.</span><span class="sxs-lookup"><span data-stu-id="ff30a-165">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="ff30a-166">Nastavení se má použít při spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="ff30a-166">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="ff30a-167">Seznam všech zjištěných testů v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="ff30a-167">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="ff30a-168">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="ff30a-168">Sets the verbosity level of the command.</span></span> <span data-ttu-id="ff30a-169">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="ff30a-169">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ff30a-170">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="ff30a-170">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="ff30a-171">Používáte vlastní adaptéry testu ze zadané cesty v testovacím běhu.</span><span class="sxs-lookup"><span data-stu-id="ff30a-171">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="ff30a-172">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="ff30a-172">Defines the build configuration.</span></span> <span data-ttu-id="ff30a-173">Výchozí hodnota je `Debug`, ale váš projekt konfigurace může přepsat toto výchozí nastavení sady SDK.</span><span class="sxs-lookup"><span data-stu-id="ff30a-173">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="ff30a-174">Umožňuje diagnostickém režimu pro testovací platformy a zápis diagnostické zprávy do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="ff30a-174">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="ff30a-175">Vyhledá binárních souborů testu pro konkrétní [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="ff30a-175">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="ff30a-176">Filtruje testy v aktuálním projektu pomocí daného výrazu.</span><span class="sxs-lookup"><span data-stu-id="ff30a-176">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="ff30a-177">Další informace najdete v tématu [možnost podrobnosti filtru](#filter-option-details) oddílu.</span><span class="sxs-lookup"><span data-stu-id="ff30a-177">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="ff30a-178">Další informace a příklady o tom, jak použít selektivní jednotky filtrování testů, naleznete v tématu [spouštění selektivních testů jednotek](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="ff30a-178">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="ff30a-179">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="ff30a-179">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="ff30a-180">Určuje protokolovací nástroj pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="ff30a-180">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="ff30a-181">Nepodporuje vytvoření testovacího projektu před jejím spuštěním.</span><span class="sxs-lookup"><span data-stu-id="ff30a-181">Doesn't build the test project before running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="ff30a-182">Adresář, ve kterém chcete najít binární soubory, které chcete spustit.</span><span class="sxs-lookup"><span data-stu-id="ff30a-182">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="ff30a-183">Nastavení se má použít při spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="ff30a-183">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="ff30a-184">Seznam všech zjištěných testů v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="ff30a-184">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="ff30a-185">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="ff30a-185">Sets the verbosity level of the command.</span></span> <span data-ttu-id="ff30a-186">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="ff30a-186">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="ff30a-187">Příklady</span><span class="sxs-lookup"><span data-stu-id="ff30a-187">Examples</span></span>

<span data-ttu-id="ff30a-188">Spusťte testy v projektu v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="ff30a-188">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="ff30a-189">Spustit testy v `test1` projektu:</span><span class="sxs-lookup"><span data-stu-id="ff30a-189">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

<span data-ttu-id="ff30a-190">Spuštění testů v projektu v aktuálním adresáři a vygenerovat soubor s výsledky testu ve formátu trx:</span><span class="sxs-lookup"><span data-stu-id="ff30a-190">Run the tests in the project in the current directory and generate a test results file in the trx format:</span></span>

`dotnet test --logger:trx`

## <a name="filter-option-details"></a><span data-ttu-id="ff30a-191">Možnost podrobnosti filtru</span><span class="sxs-lookup"><span data-stu-id="ff30a-191">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="ff30a-192">`<Expression>` má formát `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="ff30a-192">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="ff30a-193">`<property>` je atribut `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="ff30a-193">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="ff30a-194">Toto jsou vlastnosti podporované rozhraní pro testování částí oblíbených:</span><span class="sxs-lookup"><span data-stu-id="ff30a-194">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="ff30a-195">Rozhraní pro testování</span><span class="sxs-lookup"><span data-stu-id="ff30a-195">Test Framework</span></span> | <span data-ttu-id="ff30a-196">Podporovaných vlastností</span><span class="sxs-lookup"><span data-stu-id="ff30a-196">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="ff30a-197">MSTest</span><span class="sxs-lookup"><span data-stu-id="ff30a-197">MSTest</span></span>         | <ul><li><span data-ttu-id="ff30a-198">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="ff30a-198">FullyQualifiedName</span></span></li><li><span data-ttu-id="ff30a-199">Název</span><span class="sxs-lookup"><span data-stu-id="ff30a-199">Name</span></span></li><li><span data-ttu-id="ff30a-200">Název třídy</span><span class="sxs-lookup"><span data-stu-id="ff30a-200">ClassName</span></span></li><li><span data-ttu-id="ff30a-201">Priorita</span><span class="sxs-lookup"><span data-stu-id="ff30a-201">Priority</span></span></li><li><span data-ttu-id="ff30a-202">TestCategory</span><span class="sxs-lookup"><span data-stu-id="ff30a-202">TestCategory</span></span></li></ul> |
| <span data-ttu-id="ff30a-203">xUnit</span><span class="sxs-lookup"><span data-stu-id="ff30a-203">xUnit</span></span>          | <ul><li><span data-ttu-id="ff30a-204">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="ff30a-204">FullyQualifiedName</span></span></li><li><span data-ttu-id="ff30a-205">displayName</span><span class="sxs-lookup"><span data-stu-id="ff30a-205">DisplayName</span></span></li><li><span data-ttu-id="ff30a-206">Osobnostní rysy</span><span class="sxs-lookup"><span data-stu-id="ff30a-206">Traits</span></span></li></ul>                                   |

<span data-ttu-id="ff30a-207">`<operator>` Popisuje vztah mezi vlastnosti a hodnotu:</span><span class="sxs-lookup"><span data-stu-id="ff30a-207">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="ff30a-208">Operátor</span><span class="sxs-lookup"><span data-stu-id="ff30a-208">Operator</span></span> | <span data-ttu-id="ff30a-209">Funkce</span><span class="sxs-lookup"><span data-stu-id="ff30a-209">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="ff30a-210">Přesná shoda</span><span class="sxs-lookup"><span data-stu-id="ff30a-210">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="ff30a-211">Není přesná shoda</span><span class="sxs-lookup"><span data-stu-id="ff30a-211">Not exact match</span></span> |
| `~`      | <span data-ttu-id="ff30a-212">Obsahuje</span><span class="sxs-lookup"><span data-stu-id="ff30a-212">Contains</span></span>        |

<span data-ttu-id="ff30a-213">`<value>` je řetězec.</span><span class="sxs-lookup"><span data-stu-id="ff30a-213">`<value>` is a string.</span></span> <span data-ttu-id="ff30a-214">Všechna vyhledávání jsou malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="ff30a-214">All the lookups are case insensitive.</span></span>

<span data-ttu-id="ff30a-215">Výraz bez `<operator>` je automaticky považováno za `contains` na `FullyQualifiedName` vlastnosti (například `dotnet test --filter xyz` je stejná jako `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="ff30a-215">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="ff30a-216">Výrazy jde připojit k podmíněných operátorů:</span><span class="sxs-lookup"><span data-stu-id="ff30a-216">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="ff30a-217">Operátor</span><span class="sxs-lookup"><span data-stu-id="ff30a-217">Operator</span></span>            | <span data-ttu-id="ff30a-218">Funkce</span><span class="sxs-lookup"><span data-stu-id="ff30a-218">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="ff30a-219">NEBO</span><span class="sxs-lookup"><span data-stu-id="ff30a-219">OR</span></span>       |
| `&`                 | <span data-ttu-id="ff30a-220">AND</span><span class="sxs-lookup"><span data-stu-id="ff30a-220">AND</span></span>      |

<span data-ttu-id="ff30a-221">Je možné uzavřít do uvozovek výrazy v závorkách při použití podmíněných operátorů (například `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="ff30a-221">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="ff30a-222">Další informace a příklady o tom, jak použít selektivní jednotky filtrování testů, naleznete v tématu [spouštění selektivních testů jednotek](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="ff30a-222">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ff30a-223">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ff30a-223">See also</span></span>

* [<span data-ttu-id="ff30a-224">Architektury a cíle</span><span class="sxs-lookup"><span data-stu-id="ff30a-224">Frameworks and Targets</span></span>](../../standard/frameworks.md)  
* [<span data-ttu-id="ff30a-225">.NET core Runtime identifikátor (RID) katalogu</span><span class="sxs-lookup"><span data-stu-id="ff30a-225">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
