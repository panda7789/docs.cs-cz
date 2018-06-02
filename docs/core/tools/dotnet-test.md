---
title: DotNet. příkaz test - .NET Core rozhraní příkazového řádku
description: Příkaz dotnet testu se používá k provedení testů jednotek v daný projekt.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 8a10ac9175ee5fcf8649efbb07d8d382ac3afdc7
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696267"
---
# <a name="dotnet-test"></a><span data-ttu-id="f08c7-103">test DotNet.</span><span class="sxs-lookup"><span data-stu-id="f08c7-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="f08c7-104">Název</span><span class="sxs-lookup"><span data-stu-id="f08c7-104">Name</span></span>

<span data-ttu-id="f08c7-105">`dotnet test` -Ovladač test .NET použít ke spuštění testů jednotek.</span><span class="sxs-lookup"><span data-stu-id="f08c7-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f08c7-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="f08c7-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="f08c7-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="f08c7-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="f08c7-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="f08c7-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="f08c7-109">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="f08c7-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]
dotnet test [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="f08c7-110">Popis</span><span class="sxs-lookup"><span data-stu-id="f08c7-110">Description</span></span>

<span data-ttu-id="f08c7-111">`dotnet test` Příkaz se používá k provedení testů jednotek v daný projekt.</span><span class="sxs-lookup"><span data-stu-id="f08c7-111">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="f08c7-112">`dotnet test` Příkaz spustí zadaný pro projekt test runner konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="f08c7-112">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="f08c7-113">Nástroj test runner provede testů definovaných pro systém testování částí (například Mstestu, NUnit nebo xUnit) a oznámí úspěšné nebo neúspěšné každého testu.</span><span class="sxs-lookup"><span data-stu-id="f08c7-113">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="f08c7-114">Nástroj test runner a knihovně test jednotky spojených jako balíčků NuGet a se obnoví jako obyčejnou závislosti pro projekt.</span><span class="sxs-lookup"><span data-stu-id="f08c7-114">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="f08c7-115">Nástroj test runner pomocí běžný zadejte projektů testování `<PackageReference>` elementu, jak je vidět v následujícím souboru projektu vzorku:</span><span class="sxs-lookup"><span data-stu-id="f08c7-115">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="f08c7-116">Arguments</span><span class="sxs-lookup"><span data-stu-id="f08c7-116">Arguments</span></span>

`PROJECT`

<span data-ttu-id="f08c7-117">Cesta pro projekt test.</span><span class="sxs-lookup"><span data-stu-id="f08c7-117">Path to the test project.</span></span> <span data-ttu-id="f08c7-118">Pokud není zadáno, bude výchozí aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="f08c7-118">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="f08c7-119">Možnosti</span><span class="sxs-lookup"><span data-stu-id="f08c7-119">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="f08c7-120">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="f08c7-120">.NET Core 2.1</span></span>](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="f08c7-121">V testovacím běhu použijte vlastní test adaptéry ze zadané cesty.</span><span class="sxs-lookup"><span data-stu-id="f08c7-121">Use the custom test adapters from the specified path in the test run.</span></span>

`--blame`

<span data-ttu-id="f08c7-122">Testy se spustí v režimu viny.</span><span class="sxs-lookup"><span data-stu-id="f08c7-122">Runs the tests in blame mode.</span></span> <span data-ttu-id="f08c7-123">Tato možnost je užitečná v izolace problematické testy způsobuje testovacího hostitele k chybě.</span><span class="sxs-lookup"><span data-stu-id="f08c7-123">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="f08c7-124">Vytvoří výstupní soubor v aktuálním adresáři jako *Sequence.xml* který zachycuje pořadí provádění testů před havárii.</span><span class="sxs-lookup"><span data-stu-id="f08c7-124">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="f08c7-125">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="f08c7-125">Defines the build configuration.</span></span> <span data-ttu-id="f08c7-126">Výchozí hodnota je `Debug`, ale konfigurace vašeho projektu může přepsat toto výchozí nastavení SDK.</span><span class="sxs-lookup"><span data-stu-id="f08c7-126">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="f08c7-127">Umožňuje kolekce dat pro test spustit.</span><span class="sxs-lookup"><span data-stu-id="f08c7-127">Enables data collector for the test run.</span></span> <span data-ttu-id="f08c7-128">Další informace najdete v tématu [monitorování a analyzovat testu](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="f08c7-128">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="f08c7-129">Umožňuje diagnostiky režimu pro testovací platformy a zápis diagnostické zprávy do určeného souboru.</span><span class="sxs-lookup"><span data-stu-id="f08c7-129">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="f08c7-130">Vyhledá testovací binární soubory pro konkrétní [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="f08c7-130">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="f08c7-131">Filtruje testy v aktuálním projektu pomocí daného výrazu.</span><span class="sxs-lookup"><span data-stu-id="f08c7-131">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="f08c7-132">Další informace najdete v tématu [filtrovat možnost Podrobnosti](#filter-option-details) části.</span><span class="sxs-lookup"><span data-stu-id="f08c7-132">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="f08c7-133">Další příklady a další informace o tom, jak pomocí filtrování testovací selektivní jednotky, najdete v části [spouštění testů jednotek selektivní](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="f08c7-133">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="f08c7-134">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="f08c7-134">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="f08c7-135">Určuje protokolovacího nástroje pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="f08c7-135">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="f08c7-136">Před spuštěním není sestavte projekt test.</span><span class="sxs-lookup"><span data-stu-id="f08c7-136">Doesn't build the test project before running it.</span></span> <span data-ttu-id="f08c7-137">Také implicitní nastaví `--no-restore` příznak.</span><span class="sxs-lookup"><span data-stu-id="f08c7-137">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="f08c7-138">Implicitní obnovení není spustit, když spustíte příkaz.</span><span class="sxs-lookup"><span data-stu-id="f08c7-138">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="f08c7-139">Adresář, ve kterém chcete najít binární soubory ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="f08c7-139">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="f08c7-140">Adresář, kde se chystáte výsledky testů umístit.</span><span class="sxs-lookup"><span data-stu-id="f08c7-140">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="f08c7-141">Pokud zadaný adresář neexistuje, vytvoří se.</span><span class="sxs-lookup"><span data-stu-id="f08c7-141">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="f08c7-142">Nastavení se má použít při spouštění testů.</span><span class="sxs-lookup"><span data-stu-id="f08c7-142">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="f08c7-143">Seznam všech zjištěných testů v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="f08c7-143">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="f08c7-144">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="f08c7-144">Sets the verbosity level of the command.</span></span> <span data-ttu-id="f08c7-145">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="f08c7-145">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="f08c7-146">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="f08c7-146">.NET Core 2.0</span></span>](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="f08c7-147">V testovacím běhu použijte vlastní test adaptéry ze zadané cesty.</span><span class="sxs-lookup"><span data-stu-id="f08c7-147">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="f08c7-148">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="f08c7-148">Defines the build configuration.</span></span> <span data-ttu-id="f08c7-149">Výchozí hodnota je `Debug`, ale konfigurace vašeho projektu může přepsat toto výchozí nastavení SDK.</span><span class="sxs-lookup"><span data-stu-id="f08c7-149">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="f08c7-150">Umožňuje kolekce dat pro test spustit.</span><span class="sxs-lookup"><span data-stu-id="f08c7-150">Enables data collector for the test run.</span></span> <span data-ttu-id="f08c7-151">Další informace najdete v tématu [monitorování a analyzovat testu](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="f08c7-151">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="f08c7-152">Umožňuje diagnostiky režimu pro testovací platformy a zápis diagnostické zprávy do určeného souboru.</span><span class="sxs-lookup"><span data-stu-id="f08c7-152">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="f08c7-153">Vyhledá testovací binární soubory pro konkrétní [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="f08c7-153">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="f08c7-154">Filtruje testy v aktuálním projektu pomocí daného výrazu.</span><span class="sxs-lookup"><span data-stu-id="f08c7-154">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="f08c7-155">Další informace najdete v tématu [filtrovat možnost Podrobnosti](#filter-option-details) části.</span><span class="sxs-lookup"><span data-stu-id="f08c7-155">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="f08c7-156">Další příklady a další informace o tom, jak pomocí filtrování testovací selektivní jednotky, najdete v části [spouštění testů jednotek selektivní](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="f08c7-156">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="f08c7-157">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="f08c7-157">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="f08c7-158">Určuje protokolovacího nástroje pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="f08c7-158">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="f08c7-159">Před spuštěním není sestavte projekt test.</span><span class="sxs-lookup"><span data-stu-id="f08c7-159">Doesn't build the test project before running it.</span></span> <span data-ttu-id="f08c7-160">Také implicitní nastaví `--no-restore` příznak.</span><span class="sxs-lookup"><span data-stu-id="f08c7-160">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="f08c7-161">Implicitní obnovení není spustit, když spustíte příkaz.</span><span class="sxs-lookup"><span data-stu-id="f08c7-161">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="f08c7-162">Adresář, ve kterém chcete najít binární soubory ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="f08c7-162">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="f08c7-163">Adresář, kde se chystáte výsledky testů umístit.</span><span class="sxs-lookup"><span data-stu-id="f08c7-163">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="f08c7-164">Pokud zadaný adresář neexistuje, vytvoří se.</span><span class="sxs-lookup"><span data-stu-id="f08c7-164">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="f08c7-165">Nastavení se má použít při spouštění testů.</span><span class="sxs-lookup"><span data-stu-id="f08c7-165">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="f08c7-166">Seznam všech zjištěných testů v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="f08c7-166">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="f08c7-167">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="f08c7-167">Sets the verbosity level of the command.</span></span> <span data-ttu-id="f08c7-168">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="f08c7-168">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="f08c7-169">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="f08c7-169">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="f08c7-170">V testovacím běhu použijte vlastní test adaptéry ze zadané cesty.</span><span class="sxs-lookup"><span data-stu-id="f08c7-170">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="f08c7-171">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="f08c7-171">Defines the build configuration.</span></span> <span data-ttu-id="f08c7-172">Výchozí hodnota je `Debug`, ale konfigurace vašeho projektu může přepsat toto výchozí nastavení SDK.</span><span class="sxs-lookup"><span data-stu-id="f08c7-172">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="f08c7-173">Umožňuje diagnostiky režimu pro testovací platformy a zápis diagnostické zprávy do určeného souboru.</span><span class="sxs-lookup"><span data-stu-id="f08c7-173">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="f08c7-174">Vyhledá testovací binární soubory pro konkrétní [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="f08c7-174">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="f08c7-175">Filtruje testy v aktuálním projektu pomocí daného výrazu.</span><span class="sxs-lookup"><span data-stu-id="f08c7-175">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="f08c7-176">Další informace najdete v tématu [filtrovat možnost Podrobnosti](#filter-option-details) části.</span><span class="sxs-lookup"><span data-stu-id="f08c7-176">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="f08c7-177">Další příklady a další informace o tom, jak pomocí filtrování testovací selektivní jednotky, najdete v části [spouštění testů jednotek selektivní](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="f08c7-177">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="f08c7-178">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="f08c7-178">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="f08c7-179">Určuje protokolovacího nástroje pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="f08c7-179">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="f08c7-180">Před spuštěním není sestavte projekt test.</span><span class="sxs-lookup"><span data-stu-id="f08c7-180">Doesn't build the test project before running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="f08c7-181">Adresář, ve kterém chcete najít binární soubory ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="f08c7-181">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="f08c7-182">Nastavení se má použít při spouštění testů.</span><span class="sxs-lookup"><span data-stu-id="f08c7-182">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="f08c7-183">Seznam všech zjištěných testů v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="f08c7-183">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="f08c7-184">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="f08c7-184">Sets the verbosity level of the command.</span></span> <span data-ttu-id="f08c7-185">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="f08c7-185">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="f08c7-186">Příklady</span><span class="sxs-lookup"><span data-stu-id="f08c7-186">Examples</span></span>

<span data-ttu-id="f08c7-187">Spouštět testy v projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="f08c7-187">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="f08c7-188">Spouštět testy v `test1` projektu:</span><span class="sxs-lookup"><span data-stu-id="f08c7-188">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

## <a name="filter-option-details"></a><span data-ttu-id="f08c7-189">Podrobnosti o možnost filtru</span><span class="sxs-lookup"><span data-stu-id="f08c7-189">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="f08c7-190">`<Expression>` má formát `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="f08c7-190">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="f08c7-191">`<property>` je atributem `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="f08c7-191">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="f08c7-192">Tady jsou vlastnostech podporovaných zprostředkovatelem systémů testů jednotek oblíbených:</span><span class="sxs-lookup"><span data-stu-id="f08c7-192">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="f08c7-193">Test Framework</span><span class="sxs-lookup"><span data-stu-id="f08c7-193">Test Framework</span></span> | <span data-ttu-id="f08c7-194">Podporovaných vlastností</span><span class="sxs-lookup"><span data-stu-id="f08c7-194">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="f08c7-195">MSTest</span><span class="sxs-lookup"><span data-stu-id="f08c7-195">MSTest</span></span>         | <ul><li><span data-ttu-id="f08c7-196">Položka FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="f08c7-196">FullyQualifiedName</span></span></li><li><span data-ttu-id="f08c7-197">Název</span><span class="sxs-lookup"><span data-stu-id="f08c7-197">Name</span></span></li><li><span data-ttu-id="f08c7-198">Název třídy</span><span class="sxs-lookup"><span data-stu-id="f08c7-198">ClassName</span></span></li><li><span data-ttu-id="f08c7-199">Priorita</span><span class="sxs-lookup"><span data-stu-id="f08c7-199">Priority</span></span></li><li><span data-ttu-id="f08c7-200">TestCategory</span><span class="sxs-lookup"><span data-stu-id="f08c7-200">TestCategory</span></span></li></ul> |
| <span data-ttu-id="f08c7-201">xUnit</span><span class="sxs-lookup"><span data-stu-id="f08c7-201">xUnit</span></span>          | <ul><li><span data-ttu-id="f08c7-202">Položka FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="f08c7-202">FullyQualifiedName</span></span></li><li><span data-ttu-id="f08c7-203">displayName</span><span class="sxs-lookup"><span data-stu-id="f08c7-203">DisplayName</span></span></li><li><span data-ttu-id="f08c7-204">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="f08c7-204">Traits</span></span></li></ul>                                   |

<span data-ttu-id="f08c7-205">`<operator>` Popisuje vztah mezi vlastnosti a hodnotu:</span><span class="sxs-lookup"><span data-stu-id="f08c7-205">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="f08c7-206">Operátor</span><span class="sxs-lookup"><span data-stu-id="f08c7-206">Operator</span></span> | <span data-ttu-id="f08c7-207">Funkce</span><span class="sxs-lookup"><span data-stu-id="f08c7-207">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="f08c7-208">Přesná shoda</span><span class="sxs-lookup"><span data-stu-id="f08c7-208">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="f08c7-209">Není přesná shoda</span><span class="sxs-lookup"><span data-stu-id="f08c7-209">Not exact match</span></span> |
| `~`      | <span data-ttu-id="f08c7-210">Obsahuje</span><span class="sxs-lookup"><span data-stu-id="f08c7-210">Contains</span></span>        |

<span data-ttu-id="f08c7-211">`<value>` obsahuje řetězec.</span><span class="sxs-lookup"><span data-stu-id="f08c7-211">`<value>` is a string.</span></span> <span data-ttu-id="f08c7-212">Všechny hledání se malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="f08c7-212">All the lookups are case insensitive.</span></span>

<span data-ttu-id="f08c7-213">Výraz bez `<operator>` je automaticky považováno za `contains` na `FullyQualifiedName` vlastnosti (například `dotnet test --filter xyz` je stejný jako `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="f08c7-213">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="f08c7-214">Výrazy lze spojit s podmíněné operátory:</span><span class="sxs-lookup"><span data-stu-id="f08c7-214">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="f08c7-215">Operátor</span><span class="sxs-lookup"><span data-stu-id="f08c7-215">Operator</span></span>            | <span data-ttu-id="f08c7-216">Funkce</span><span class="sxs-lookup"><span data-stu-id="f08c7-216">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="f08c7-217">NEBO</span><span class="sxs-lookup"><span data-stu-id="f08c7-217">OR</span></span>       |
| `&`                 | <span data-ttu-id="f08c7-218">AND</span><span class="sxs-lookup"><span data-stu-id="f08c7-218">AND</span></span>      |

<span data-ttu-id="f08c7-219">Můžete uzavřete výrazy v závorkách, při použití podmíněné operátory (například `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="f08c7-219">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="f08c7-220">Další příklady a další informace o tom, jak pomocí filtrování testovací selektivní jednotky, najdete v části [spouštění testů jednotek selektivní](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="f08c7-220">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f08c7-221">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f08c7-221">See also</span></span>

[<span data-ttu-id="f08c7-222">Rozhraní a cíle</span><span class="sxs-lookup"><span data-stu-id="f08c7-222">Frameworks and Targets</span></span>](../../standard/frameworks.md)  
[<span data-ttu-id="f08c7-223">Katalog .NET core Runtime identifikátor (RID)</span><span class="sxs-lookup"><span data-stu-id="f08c7-223">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
