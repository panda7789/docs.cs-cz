---
title: dotnet – příkaz testu
description: Příkaz dotnet test se používá ke spouštění testů jednotek v daném projektu.
ms.date: 05/29/2018
ms.openlocfilehash: c3115d546efb1f076ae9f9731f83a12183aa4154
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182512"
---
# <a name="dotnet-test"></a><span data-ttu-id="f77f4-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="f77f4-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="f77f4-104">Name</span><span class="sxs-lookup"><span data-stu-id="f77f4-104">Name</span></span>

<span data-ttu-id="f77f4-105">`dotnet test`– Testovací ovladač .NET, který se používá ke spouštění testů jednotek.</span><span class="sxs-lookup"><span data-stu-id="f77f4-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f77f4-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="f77f4-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="f77f4-107">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="f77f4-107">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] 
    [-v|--verbosity] [-- <RunSettings arguments>]

dotnet test [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="f77f4-108">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="f77f4-108">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]

dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="f77f4-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="f77f4-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]

dotnet test [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="f77f4-110">Popis</span><span class="sxs-lookup"><span data-stu-id="f77f4-110">Description</span></span>

<span data-ttu-id="f77f4-111">`dotnet test` Příkaz slouží ke spuštění testů jednotek v daném projektu.</span><span class="sxs-lookup"><span data-stu-id="f77f4-111">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="f77f4-112">`dotnet test` Příkaz spustí konzolovou aplikaci Test Runner určenou pro projekt.</span><span class="sxs-lookup"><span data-stu-id="f77f4-112">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="f77f4-113">Test Runner spustí testy definované pro systém testů jednotek (například MSTest, NUnit nebo xUnit) a ohlásí úspěch nebo neúspěch každého testu.</span><span class="sxs-lookup"><span data-stu-id="f77f4-113">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="f77f4-114">Pokud jsou všechny testy úspěšné, Test Runner vrátí 0 jako ukončovací kód; jinak, pokud nějaký test selže, vrátí 1.</span><span class="sxs-lookup"><span data-stu-id="f77f4-114">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="f77f4-115">Test Runner a knihovna testů jednotek jsou zabaleny jako balíčky NuGet a jsou obnoveny jako běžné závislosti pro projekt.</span><span class="sxs-lookup"><span data-stu-id="f77f4-115">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="f77f4-116">Projekty testů určují testovací spouštěč pomocí obyčejného `<PackageReference>` prvku, jak je vidět v následujícím ukázkovém souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="f77f4-116">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="f77f4-117">Arguments</span><span class="sxs-lookup"><span data-stu-id="f77f4-117">Arguments</span></span>

`PROJECT`

<span data-ttu-id="f77f4-118">Cesta k testovacímu projektu.</span><span class="sxs-lookup"><span data-stu-id="f77f4-118">Path to the test project.</span></span> <span data-ttu-id="f77f4-119">Pokud není zadaný, použije se ve výchozím nastavení aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="f77f4-119">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="f77f4-120">Možnosti</span><span class="sxs-lookup"><span data-stu-id="f77f4-120">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="f77f4-121">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="f77f4-121">.NET Core 2.1</span></span>](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="f77f4-122">Použijte vlastní testovací adaptéry ze zadané cesty v testovacím běhu.</span><span class="sxs-lookup"><span data-stu-id="f77f4-122">Use the custom test adapters from the specified path in the test run.</span></span>

`--blame`

<span data-ttu-id="f77f4-123">Spustí testy v režimu viny.</span><span class="sxs-lookup"><span data-stu-id="f77f4-123">Runs the tests in blame mode.</span></span> <span data-ttu-id="f77f4-124">Tato možnost je užitečná při izolaci problematických testů, které způsobují selhání hostitele testu.</span><span class="sxs-lookup"><span data-stu-id="f77f4-124">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="f77f4-125">Vytvoří výstupní soubor v aktuálním adresáři jako *Sequence. XML* , který zachycuje pořadí spuštění testů před selháním.</span><span class="sxs-lookup"><span data-stu-id="f77f4-125">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="f77f4-126">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="f77f4-126">Defines the build configuration.</span></span> <span data-ttu-id="f77f4-127">Výchozí hodnota je `Debug`, ale konfigurace vašeho projektu může přepsat toto výchozí nastavení sady SDK.</span><span class="sxs-lookup"><span data-stu-id="f77f4-127">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="f77f4-128">Povolí shromažďování dat pro testovací běh.</span><span class="sxs-lookup"><span data-stu-id="f77f4-128">Enables data collector for the test run.</span></span> <span data-ttu-id="f77f4-129">Další informace najdete v tématu [monitorování a analýza testovacího běhu](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="f77f4-129">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="f77f4-130">Povolí diagnostický režim pro testovací platformu a zapíše diagnostické zprávy do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="f77f4-130">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="f77f4-131">Vyhledá testovací binární soubory pro konkrétní [rozhraní](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="f77f4-131">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="f77f4-132">Odfiltruje testy v aktuálním projektu pomocí daného výrazu.</span><span class="sxs-lookup"><span data-stu-id="f77f4-132">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="f77f4-133">Další informace najdete v části [Podrobnosti o možnosti filtru](#filter-option-details) .</span><span class="sxs-lookup"><span data-stu-id="f77f4-133">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="f77f4-134">Další informace a příklady použití selektivního filtrování testů jednotek naleznete v tématu [spuštění selektivních testů jednotek](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="f77f4-134">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="f77f4-135">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="f77f4-135">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="f77f4-136">Určuje protokolovací nástroj pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="f77f4-136">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="f77f4-137">Před spuštěním nevytvoří testovací projekt.</span><span class="sxs-lookup"><span data-stu-id="f77f4-137">Doesn't build the test project before running it.</span></span> <span data-ttu-id="f77f4-138">Také implicitně nastaví `--no-restore` příznak.</span><span class="sxs-lookup"><span data-stu-id="f77f4-138">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="f77f4-139">Při spuštění příkazu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="f77f4-139">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="f77f4-140">Adresář, ve kterém se mají najít binární soubory, které se mají spustit.</span><span class="sxs-lookup"><span data-stu-id="f77f4-140">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="f77f4-141">Adresář, do kterého budou umístěny výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="f77f4-141">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="f77f4-142">Pokud zadaný adresář neexistuje, vytvoří se.</span><span class="sxs-lookup"><span data-stu-id="f77f4-142">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="f77f4-143">`.runsettings` Soubor, který se má použít pro spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="f77f4-143">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="f77f4-144">Nakonfigurujte testy jednotek pomocí `.runsettings` souboru.</span><span class="sxs-lookup"><span data-stu-id="f77f4-144">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

`-t|--list-tests`

<span data-ttu-id="f77f4-145">Vypíše všechny zjištěné testy v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="f77f4-145">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="f77f4-146">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="f77f4-146">Sets the verbosity level of the command.</span></span> <span data-ttu-id="f77f4-147">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]` `d[etailed]`, a .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="f77f4-147">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`RunSettings arguments`

<span data-ttu-id="f77f4-148">Argumenty byly předány jako konfigurace RunSettings pro test.</span><span class="sxs-lookup"><span data-stu-id="f77f4-148">Arguments passed as RunSettings configurations for the test.</span></span> <span data-ttu-id="f77f4-149">Argumenty jsou zadány `[name]=[value]` jako páry po "--" (Všimněte si mezer za-).</span><span class="sxs-lookup"><span data-stu-id="f77f4-149">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="f77f4-150">K oddělení více `[name]=[value]` párů se používá mezera.</span><span class="sxs-lookup"><span data-stu-id="f77f4-150">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

<span data-ttu-id="f77f4-151">Příklad: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="f77f4-151">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

<span data-ttu-id="f77f4-152">Další informace o runsettings najdete v tématu [VSTest. Console. exe: Předávání argumentů](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)runsettings</span><span class="sxs-lookup"><span data-stu-id="f77f4-152">For more information about RunSettings, see [vstest.console.exe: Passing RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="f77f4-153">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="f77f4-153">.NET Core 2.0</span></span>](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="f77f4-154">Použijte vlastní testovací adaptéry ze zadané cesty v testovacím běhu.</span><span class="sxs-lookup"><span data-stu-id="f77f4-154">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="f77f4-155">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="f77f4-155">Defines the build configuration.</span></span> <span data-ttu-id="f77f4-156">Výchozí hodnota je `Debug`, ale konfigurace vašeho projektu může přepsat toto výchozí nastavení sady SDK.</span><span class="sxs-lookup"><span data-stu-id="f77f4-156">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="f77f4-157">Povolí shromažďování dat pro testovací běh.</span><span class="sxs-lookup"><span data-stu-id="f77f4-157">Enables data collector for the test run.</span></span> <span data-ttu-id="f77f4-158">Další informace najdete v tématu [monitorování a analýza testovacího běhu](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="f77f4-158">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="f77f4-159">Povolí diagnostický režim pro testovací platformu a zapíše diagnostické zprávy do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="f77f4-159">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="f77f4-160">Vyhledá testovací binární soubory pro konkrétní [rozhraní](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="f77f4-160">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="f77f4-161">Odfiltruje testy v aktuálním projektu pomocí daného výrazu.</span><span class="sxs-lookup"><span data-stu-id="f77f4-161">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="f77f4-162">Další informace najdete v části [Podrobnosti o možnosti filtru](#filter-option-details) .</span><span class="sxs-lookup"><span data-stu-id="f77f4-162">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="f77f4-163">Další informace a příklady použití selektivního filtrování testů jednotek naleznete v tématu [spuštění selektivních testů jednotek](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="f77f4-163">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="f77f4-164">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="f77f4-164">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="f77f4-165">Určuje protokolovací nástroj pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="f77f4-165">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="f77f4-166">Před spuštěním nevytvoří testovací projekt.</span><span class="sxs-lookup"><span data-stu-id="f77f4-166">Doesn't build the test project before running it.</span></span> <span data-ttu-id="f77f4-167">Také implicitně nastaví `--no-restore` příznak.</span><span class="sxs-lookup"><span data-stu-id="f77f4-167">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="f77f4-168">Při spuštění příkazu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="f77f4-168">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="f77f4-169">Adresář, ve kterém se mají najít binární soubory, které se mají spustit.</span><span class="sxs-lookup"><span data-stu-id="f77f4-169">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="f77f4-170">Adresář, do kterého budou umístěny výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="f77f4-170">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="f77f4-171">Pokud zadaný adresář neexistuje, vytvoří se.</span><span class="sxs-lookup"><span data-stu-id="f77f4-171">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="f77f4-172">`.runsettings` Soubor, který se má použít pro spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="f77f4-172">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="f77f4-173">Nakonfigurujte testy jednotek pomocí `.runsettings` souboru.</span><span class="sxs-lookup"><span data-stu-id="f77f4-173">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

`-t|--list-tests`

<span data-ttu-id="f77f4-174">Vypíše všechny zjištěné testy v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="f77f4-174">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="f77f4-175">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="f77f4-175">Sets the verbosity level of the command.</span></span> <span data-ttu-id="f77f4-176">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]` `d[etailed]`, a .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="f77f4-176">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="f77f4-177">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="f77f4-177">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="f77f4-178">Použijte vlastní testovací adaptéry ze zadané cesty v testovacím běhu.</span><span class="sxs-lookup"><span data-stu-id="f77f4-178">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="f77f4-179">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="f77f4-179">Defines the build configuration.</span></span> <span data-ttu-id="f77f4-180">Výchozí hodnota je `Debug`, ale konfigurace vašeho projektu může přepsat toto výchozí nastavení sady SDK.</span><span class="sxs-lookup"><span data-stu-id="f77f4-180">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="f77f4-181">Povolí diagnostický režim pro testovací platformu a zapíše diagnostické zprávy do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="f77f4-181">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="f77f4-182">Vyhledá testovací binární soubory pro konkrétní [rozhraní](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="f77f4-182">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="f77f4-183">Odfiltruje testy v aktuálním projektu pomocí daného výrazu.</span><span class="sxs-lookup"><span data-stu-id="f77f4-183">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="f77f4-184">Další informace najdete v části [Podrobnosti o možnosti filtru](#filter-option-details) .</span><span class="sxs-lookup"><span data-stu-id="f77f4-184">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="f77f4-185">Další informace a příklady použití selektivního filtrování testů jednotek naleznete v tématu [spuštění selektivních testů jednotek](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="f77f4-185">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="f77f4-186">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="f77f4-186">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="f77f4-187">Určuje protokolovací nástroj pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="f77f4-187">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="f77f4-188">Před spuštěním nevytvoří testovací projekt.</span><span class="sxs-lookup"><span data-stu-id="f77f4-188">Doesn't build the test project before running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="f77f4-189">Adresář, ve kterém se mají najít binární soubory, které se mají spustit.</span><span class="sxs-lookup"><span data-stu-id="f77f4-189">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="f77f4-190">`.runsettings` Soubor, který se má použít pro spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="f77f4-190">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="f77f4-191">Nakonfigurujte testy jednotek pomocí `.runsettings` souboru.</span><span class="sxs-lookup"><span data-stu-id="f77f4-191">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

`-t|--list-tests`

<span data-ttu-id="f77f4-192">Vypíše všechny zjištěné testy v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="f77f4-192">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="f77f4-193">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="f77f4-193">Sets the verbosity level of the command.</span></span> <span data-ttu-id="f77f4-194">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]` `d[etailed]`, a .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="f77f4-194">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="f77f4-195">Příklady</span><span class="sxs-lookup"><span data-stu-id="f77f4-195">Examples</span></span>

<span data-ttu-id="f77f4-196">Spustit testy v projektu v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="f77f4-196">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="f77f4-197">Spustit testy v `test1` projektu:</span><span class="sxs-lookup"><span data-stu-id="f77f4-197">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

<span data-ttu-id="f77f4-198">Spusťte testy v projektu v aktuálním adresáři a vygenerujte soubor výsledků testů ve formátu TRX:</span><span class="sxs-lookup"><span data-stu-id="f77f4-198">Run the tests in the project in the current directory and generate a test results file in the trx format:</span></span>

`dotnet test --logger trx`

## <a name="filter-option-details"></a><span data-ttu-id="f77f4-199">Podrobnosti možnosti filtru</span><span class="sxs-lookup"><span data-stu-id="f77f4-199">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="f77f4-200">`<Expression>`má formát `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="f77f4-200">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="f77f4-201">`<property>`je atributem `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="f77f4-201">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="f77f4-202">Níže jsou uvedené vlastnosti podporované oblíbenými rozhraními pro testování částí:</span><span class="sxs-lookup"><span data-stu-id="f77f4-202">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="f77f4-203">Rozhraní pro testování</span><span class="sxs-lookup"><span data-stu-id="f77f4-203">Test Framework</span></span> | <span data-ttu-id="f77f4-204">Podporované vlastnosti</span><span class="sxs-lookup"><span data-stu-id="f77f4-204">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="f77f4-205">MSTest</span><span class="sxs-lookup"><span data-stu-id="f77f4-205">MSTest</span></span>         | <ul><li><span data-ttu-id="f77f4-206">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="f77f4-206">FullyQualifiedName</span></span></li><li><span data-ttu-id="f77f4-207">Name</span><span class="sxs-lookup"><span data-stu-id="f77f4-207">Name</span></span></li><li><span data-ttu-id="f77f4-208">NázevTřídy</span><span class="sxs-lookup"><span data-stu-id="f77f4-208">ClassName</span></span></li><li><span data-ttu-id="f77f4-209">Priorita</span><span class="sxs-lookup"><span data-stu-id="f77f4-209">Priority</span></span></li><li><span data-ttu-id="f77f4-210">TestCategory</span><span class="sxs-lookup"><span data-stu-id="f77f4-210">TestCategory</span></span></li></ul> |
| <span data-ttu-id="f77f4-211">xUnit</span><span class="sxs-lookup"><span data-stu-id="f77f4-211">xUnit</span></span>          | <ul><li><span data-ttu-id="f77f4-212">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="f77f4-212">FullyQualifiedName</span></span></li><li><span data-ttu-id="f77f4-213">DisplayName</span><span class="sxs-lookup"><span data-stu-id="f77f4-213">DisplayName</span></span></li><li><span data-ttu-id="f77f4-214">Traits</span><span class="sxs-lookup"><span data-stu-id="f77f4-214">Traits</span></span></li></ul>                                   |

<span data-ttu-id="f77f4-215">`<operator>` Popisuje vztah mezi vlastností a hodnotou:</span><span class="sxs-lookup"><span data-stu-id="f77f4-215">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="f77f4-216">Operátor</span><span class="sxs-lookup"><span data-stu-id="f77f4-216">Operator</span></span> | <span data-ttu-id="f77f4-217">Funkce</span><span class="sxs-lookup"><span data-stu-id="f77f4-217">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="f77f4-218">Přesná shoda</span><span class="sxs-lookup"><span data-stu-id="f77f4-218">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="f77f4-219">Nepřesná shoda</span><span class="sxs-lookup"><span data-stu-id="f77f4-219">Not exact match</span></span> |
| `~`      | <span data-ttu-id="f77f4-220">Obsahuje</span><span class="sxs-lookup"><span data-stu-id="f77f4-220">Contains</span></span>        |

<span data-ttu-id="f77f4-221">`<value>`je řetězec.</span><span class="sxs-lookup"><span data-stu-id="f77f4-221">`<value>` is a string.</span></span> <span data-ttu-id="f77f4-222">U všech hledání se nerozlišují malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="f77f4-222">All the lookups are case insensitive.</span></span>

<span data-ttu-id="f77f4-223">Výraz `<operator>` bez objektu je automaticky považován za `FullyQualifiedName` `contains` vlastnost on (například `dotnet test --filter xyz` je stejný jako `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="f77f4-223">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="f77f4-224">Výrazy se dají spojit s podmíněnými operátory:</span><span class="sxs-lookup"><span data-stu-id="f77f4-224">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="f77f4-225">Operátor</span><span class="sxs-lookup"><span data-stu-id="f77f4-225">Operator</span></span>            | <span data-ttu-id="f77f4-226">Funkce</span><span class="sxs-lookup"><span data-stu-id="f77f4-226">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="f77f4-227">NEBO</span><span class="sxs-lookup"><span data-stu-id="f77f4-227">OR</span></span>       |
| `&`                 | <span data-ttu-id="f77f4-228">AND</span><span class="sxs-lookup"><span data-stu-id="f77f4-228">AND</span></span>      |

<span data-ttu-id="f77f4-229">Výrazy můžete uzavřít do závorek při použití podmíněných operátorů (například `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="f77f4-229">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="f77f4-230">Další informace a příklady použití selektivního filtrování testů jednotek naleznete v tématu [spuštění selektivních testů jednotek](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="f77f4-230">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f77f4-231">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f77f4-231">See also</span></span>

- [<span data-ttu-id="f77f4-232">Architektury a cíle</span><span class="sxs-lookup"><span data-stu-id="f77f4-232">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="f77f4-233">Katalog identifikátorů runtime .NET Core (RID)</span><span class="sxs-lookup"><span data-stu-id="f77f4-233">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
