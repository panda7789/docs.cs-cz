---
title: příkaz DotNet test – rozhraní příkazového řádku .NET Core
description: Příkaz dotnet test slouží ke spuštění testů jednotek v daném projektu.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 7946196b27489870da1c16b15cbf5f078ae89c61
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46479179"
---
# <a name="dotnet-test"></a><span data-ttu-id="0918e-103">DotNet test</span><span class="sxs-lookup"><span data-stu-id="0918e-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="0918e-104">Název</span><span class="sxs-lookup"><span data-stu-id="0918e-104">Name</span></span>

<span data-ttu-id="0918e-105">`dotnet test` -Ovladač test .NET ke spuštění testů jednotek.</span><span class="sxs-lookup"><span data-stu-id="0918e-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0918e-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="0918e-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="0918e-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="0918e-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="0918e-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="0918e-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0918e-109">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="0918e-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]
dotnet test [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="0918e-110">Popis</span><span class="sxs-lookup"><span data-stu-id="0918e-110">Description</span></span>

<span data-ttu-id="0918e-111">`dotnet test` Příkaz se používá ke spuštění testů jednotek v daném projektu.</span><span class="sxs-lookup"><span data-stu-id="0918e-111">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="0918e-112">`dotnet test` Příkaz spustí zadaný pro projekt test runner konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0918e-112">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="0918e-113">Nástroj test runner sestavy úspěch nebo selhání jednotlivých testovacích a spustí testy, které jsou definovány pro rozhraní testování částí (například MSTest, NUnit nebo xUnit).</span><span class="sxs-lookup"><span data-stu-id="0918e-113">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="0918e-114">Nástroj test runner a knihovnu testu jednotky jsou dodávány jako balíčky NuGet a se obnoví jako běžný závislosti projektu.</span><span class="sxs-lookup"><span data-stu-id="0918e-114">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="0918e-115">Projekty testů zadat nástroje test runner pomocí běžný `<PackageReference>` elementu, jak je znázorněno v následující ukázkový soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="0918e-115">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="0918e-116">Arguments</span><span class="sxs-lookup"><span data-stu-id="0918e-116">Arguments</span></span>

`PROJECT`

<span data-ttu-id="0918e-117">Cesta k projektu testů.</span><span class="sxs-lookup"><span data-stu-id="0918e-117">Path to the test project.</span></span> <span data-ttu-id="0918e-118">Pokud není zadán, použije se výchozí aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="0918e-118">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="0918e-119">Možnosti</span><span class="sxs-lookup"><span data-stu-id="0918e-119">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="0918e-120">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="0918e-120">.NET Core 2.1</span></span>](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="0918e-121">Používáte vlastní adaptéry testu ze zadané cesty v testovacím běhu.</span><span class="sxs-lookup"><span data-stu-id="0918e-121">Use the custom test adapters from the specified path in the test run.</span></span>

`--blame`

<span data-ttu-id="0918e-122">Testy se spustí v režimu viny.</span><span class="sxs-lookup"><span data-stu-id="0918e-122">Runs the tests in blame mode.</span></span> <span data-ttu-id="0918e-123">Tato možnost je užitečná v izolaci problematické testů způsobí hostitele testu při selhání.</span><span class="sxs-lookup"><span data-stu-id="0918e-123">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="0918e-124">Vytvoří výstupní soubor v aktuálním adresáři jako *Sequence.xml* , který zachycuje pořadí provádění testů před selhání.</span><span class="sxs-lookup"><span data-stu-id="0918e-124">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="0918e-125">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="0918e-125">Defines the build configuration.</span></span> <span data-ttu-id="0918e-126">Výchozí hodnota je `Debug`, ale váš projekt konfigurace může přepsat toto výchozí nastavení sady SDK.</span><span class="sxs-lookup"><span data-stu-id="0918e-126">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="0918e-127">Povolí shromažďování dat pro testovací běh.</span><span class="sxs-lookup"><span data-stu-id="0918e-127">Enables data collector for the test run.</span></span> <span data-ttu-id="0918e-128">Další informace najdete v tématu [monitorování a analýza testovacího běhu](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="0918e-128">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="0918e-129">Umožňuje diagnostickém režimu pro testovací platformy a zápis diagnostické zprávy do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="0918e-129">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="0918e-130">Vyhledá binárních souborů testu pro konkrétní [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="0918e-130">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="0918e-131">Filtruje testy v aktuálním projektu pomocí daného výrazu.</span><span class="sxs-lookup"><span data-stu-id="0918e-131">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="0918e-132">Další informace najdete v tématu [možnost podrobnosti filtru](#filter-option-details) oddílu.</span><span class="sxs-lookup"><span data-stu-id="0918e-132">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="0918e-133">Další informace a příklady o tom, jak použít selektivní jednotky filtrování testů, naleznete v tématu [spouštění selektivních testů jednotek](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="0918e-133">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="0918e-134">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="0918e-134">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="0918e-135">Určuje protokolovací nástroj pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="0918e-135">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="0918e-136">Nepodporuje vytvoření testovacího projektu před jejím spuštěním.</span><span class="sxs-lookup"><span data-stu-id="0918e-136">Doesn't build the test project before running it.</span></span> <span data-ttu-id="0918e-137">Také implicitní nastaví `--no-restore` příznak.</span><span class="sxs-lookup"><span data-stu-id="0918e-137">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="0918e-138">Při spuštění příkazu se nebude spouštět implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="0918e-138">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="0918e-139">Adresář, ve kterém chcete najít binární soubory, které chcete spustit.</span><span class="sxs-lookup"><span data-stu-id="0918e-139">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="0918e-140">Adresář, kam výsledky testu budou umístěny.</span><span class="sxs-lookup"><span data-stu-id="0918e-140">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="0918e-141">Pokud zadaný adresář neexistuje, vytvoří se.</span><span class="sxs-lookup"><span data-stu-id="0918e-141">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="0918e-142">Nastavení se má použít při spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="0918e-142">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="0918e-143">Seznam všech zjištěných testů v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="0918e-143">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="0918e-144">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="0918e-144">Sets the verbosity level of the command.</span></span> <span data-ttu-id="0918e-145">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="0918e-145">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="0918e-146">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="0918e-146">.NET Core 2.0</span></span>](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="0918e-147">Používáte vlastní adaptéry testu ze zadané cesty v testovacím běhu.</span><span class="sxs-lookup"><span data-stu-id="0918e-147">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="0918e-148">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="0918e-148">Defines the build configuration.</span></span> <span data-ttu-id="0918e-149">Výchozí hodnota je `Debug`, ale váš projekt konfigurace může přepsat toto výchozí nastavení sady SDK.</span><span class="sxs-lookup"><span data-stu-id="0918e-149">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="0918e-150">Povolí shromažďování dat pro testovací běh.</span><span class="sxs-lookup"><span data-stu-id="0918e-150">Enables data collector for the test run.</span></span> <span data-ttu-id="0918e-151">Další informace najdete v tématu [monitorování a analýza testovacího běhu](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="0918e-151">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="0918e-152">Umožňuje diagnostickém režimu pro testovací platformy a zápis diagnostické zprávy do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="0918e-152">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="0918e-153">Vyhledá binárních souborů testu pro konkrétní [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="0918e-153">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="0918e-154">Filtruje testy v aktuálním projektu pomocí daného výrazu.</span><span class="sxs-lookup"><span data-stu-id="0918e-154">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="0918e-155">Další informace najdete v tématu [možnost podrobnosti filtru](#filter-option-details) oddílu.</span><span class="sxs-lookup"><span data-stu-id="0918e-155">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="0918e-156">Další informace a příklady o tom, jak použít selektivní jednotky filtrování testů, naleznete v tématu [spouštění selektivních testů jednotek](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="0918e-156">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="0918e-157">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="0918e-157">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="0918e-158">Určuje protokolovací nástroj pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="0918e-158">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="0918e-159">Nepodporuje vytvoření testovacího projektu před jejím spuštěním.</span><span class="sxs-lookup"><span data-stu-id="0918e-159">Doesn't build the test project before running it.</span></span> <span data-ttu-id="0918e-160">Také implicitní nastaví `--no-restore` příznak.</span><span class="sxs-lookup"><span data-stu-id="0918e-160">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="0918e-161">Při spuštění příkazu se nebude spouštět implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="0918e-161">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="0918e-162">Adresář, ve kterém chcete najít binární soubory, které chcete spustit.</span><span class="sxs-lookup"><span data-stu-id="0918e-162">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="0918e-163">Adresář, kam výsledky testu budou umístěny.</span><span class="sxs-lookup"><span data-stu-id="0918e-163">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="0918e-164">Pokud zadaný adresář neexistuje, vytvoří se.</span><span class="sxs-lookup"><span data-stu-id="0918e-164">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="0918e-165">Nastavení se má použít při spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="0918e-165">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="0918e-166">Seznam všech zjištěných testů v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="0918e-166">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="0918e-167">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="0918e-167">Sets the verbosity level of the command.</span></span> <span data-ttu-id="0918e-168">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="0918e-168">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0918e-169">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="0918e-169">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="0918e-170">Používáte vlastní adaptéry testu ze zadané cesty v testovacím běhu.</span><span class="sxs-lookup"><span data-stu-id="0918e-170">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="0918e-171">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="0918e-171">Defines the build configuration.</span></span> <span data-ttu-id="0918e-172">Výchozí hodnota je `Debug`, ale váš projekt konfigurace může přepsat toto výchozí nastavení sady SDK.</span><span class="sxs-lookup"><span data-stu-id="0918e-172">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="0918e-173">Umožňuje diagnostickém režimu pro testovací platformy a zápis diagnostické zprávy do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="0918e-173">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="0918e-174">Vyhledá binárních souborů testu pro konkrétní [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="0918e-174">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="0918e-175">Filtruje testy v aktuálním projektu pomocí daného výrazu.</span><span class="sxs-lookup"><span data-stu-id="0918e-175">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="0918e-176">Další informace najdete v tématu [možnost podrobnosti filtru](#filter-option-details) oddílu.</span><span class="sxs-lookup"><span data-stu-id="0918e-176">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="0918e-177">Další informace a příklady o tom, jak použít selektivní jednotky filtrování testů, naleznete v tématu [spouštění selektivních testů jednotek](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="0918e-177">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="0918e-178">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="0918e-178">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="0918e-179">Určuje protokolovací nástroj pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="0918e-179">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="0918e-180">Nepodporuje vytvoření testovacího projektu před jejím spuštěním.</span><span class="sxs-lookup"><span data-stu-id="0918e-180">Doesn't build the test project before running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="0918e-181">Adresář, ve kterém chcete najít binární soubory, které chcete spustit.</span><span class="sxs-lookup"><span data-stu-id="0918e-181">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="0918e-182">Nastavení se má použít při spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="0918e-182">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="0918e-183">Seznam všech zjištěných testů v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="0918e-183">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="0918e-184">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="0918e-184">Sets the verbosity level of the command.</span></span> <span data-ttu-id="0918e-185">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="0918e-185">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="0918e-186">Příklady</span><span class="sxs-lookup"><span data-stu-id="0918e-186">Examples</span></span>

<span data-ttu-id="0918e-187">Spusťte testy v projektu v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="0918e-187">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="0918e-188">Spustit testy v `test1` projektu:</span><span class="sxs-lookup"><span data-stu-id="0918e-188">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

<span data-ttu-id="0918e-189">Spuštění testů v projektu v aktuálním adresáři a vygenerovat soubor s výsledky testu ve formátu trx:</span><span class="sxs-lookup"><span data-stu-id="0918e-189">Run the tests in the project in the current directory and generate a test results file in the trx format:</span></span>

`dotnet test --logger:trx`

## <a name="filter-option-details"></a><span data-ttu-id="0918e-190">Možnost podrobnosti filtru</span><span class="sxs-lookup"><span data-stu-id="0918e-190">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="0918e-191">`<Expression>` má formát `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="0918e-191">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="0918e-192">`<property>` je atribut `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="0918e-192">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="0918e-193">Toto jsou vlastnosti podporované rozhraní pro testování částí oblíbených:</span><span class="sxs-lookup"><span data-stu-id="0918e-193">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="0918e-194">Rozhraní pro testování</span><span class="sxs-lookup"><span data-stu-id="0918e-194">Test Framework</span></span> | <span data-ttu-id="0918e-195">Podporovaných vlastností</span><span class="sxs-lookup"><span data-stu-id="0918e-195">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="0918e-196">MSTest</span><span class="sxs-lookup"><span data-stu-id="0918e-196">MSTest</span></span>         | <ul><li><span data-ttu-id="0918e-197">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="0918e-197">FullyQualifiedName</span></span></li><li><span data-ttu-id="0918e-198">Název</span><span class="sxs-lookup"><span data-stu-id="0918e-198">Name</span></span></li><li><span data-ttu-id="0918e-199">Název třídy</span><span class="sxs-lookup"><span data-stu-id="0918e-199">ClassName</span></span></li><li><span data-ttu-id="0918e-200">Priorita</span><span class="sxs-lookup"><span data-stu-id="0918e-200">Priority</span></span></li><li><span data-ttu-id="0918e-201">TestCategory</span><span class="sxs-lookup"><span data-stu-id="0918e-201">TestCategory</span></span></li></ul> |
| <span data-ttu-id="0918e-202">xUnit</span><span class="sxs-lookup"><span data-stu-id="0918e-202">xUnit</span></span>          | <ul><li><span data-ttu-id="0918e-203">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="0918e-203">FullyQualifiedName</span></span></li><li><span data-ttu-id="0918e-204">displayName</span><span class="sxs-lookup"><span data-stu-id="0918e-204">DisplayName</span></span></li><li><span data-ttu-id="0918e-205">Osobnostní rysy</span><span class="sxs-lookup"><span data-stu-id="0918e-205">Traits</span></span></li></ul>                                   |

<span data-ttu-id="0918e-206">`<operator>` Popisuje vztah mezi vlastnosti a hodnotu:</span><span class="sxs-lookup"><span data-stu-id="0918e-206">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="0918e-207">Operátor</span><span class="sxs-lookup"><span data-stu-id="0918e-207">Operator</span></span> | <span data-ttu-id="0918e-208">Funkce</span><span class="sxs-lookup"><span data-stu-id="0918e-208">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="0918e-209">Přesná shoda</span><span class="sxs-lookup"><span data-stu-id="0918e-209">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="0918e-210">Není přesná shoda</span><span class="sxs-lookup"><span data-stu-id="0918e-210">Not exact match</span></span> |
| `~`      | <span data-ttu-id="0918e-211">Obsahuje</span><span class="sxs-lookup"><span data-stu-id="0918e-211">Contains</span></span>        |

<span data-ttu-id="0918e-212">`<value>` je řetězec.</span><span class="sxs-lookup"><span data-stu-id="0918e-212">`<value>` is a string.</span></span> <span data-ttu-id="0918e-213">Všechna vyhledávání jsou malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="0918e-213">All the lookups are case insensitive.</span></span>

<span data-ttu-id="0918e-214">Výraz bez `<operator>` je automaticky považováno za `contains` na `FullyQualifiedName` vlastnosti (například `dotnet test --filter xyz` je stejná jako `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="0918e-214">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="0918e-215">Výrazy jde připojit k podmíněných operátorů:</span><span class="sxs-lookup"><span data-stu-id="0918e-215">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="0918e-216">Operátor</span><span class="sxs-lookup"><span data-stu-id="0918e-216">Operator</span></span>            | <span data-ttu-id="0918e-217">Funkce</span><span class="sxs-lookup"><span data-stu-id="0918e-217">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="0918e-218">NEBO</span><span class="sxs-lookup"><span data-stu-id="0918e-218">OR</span></span>       |
| `&`                 | <span data-ttu-id="0918e-219">AND</span><span class="sxs-lookup"><span data-stu-id="0918e-219">AND</span></span>      |

<span data-ttu-id="0918e-220">Je možné uzavřít do uvozovek výrazy v závorkách při použití podmíněných operátorů (například `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="0918e-220">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="0918e-221">Další informace a příklady o tom, jak použít selektivní jednotky filtrování testů, naleznete v tématu [spouštění selektivních testů jednotek](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="0918e-221">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0918e-222">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0918e-222">See also</span></span>

* [<span data-ttu-id="0918e-223">Architektury a cíle</span><span class="sxs-lookup"><span data-stu-id="0918e-223">Frameworks and Targets</span></span>](../../standard/frameworks.md)  
* [<span data-ttu-id="0918e-224">.NET core Runtime identifikátor (RID) katalogu</span><span class="sxs-lookup"><span data-stu-id="0918e-224">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
