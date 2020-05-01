---
title: dotnet – příkaz testu
description: Příkaz dotnet test se používá ke spouštění testů jednotek v daném projektu.
ms.date: 04/29/2020
ms.openlocfilehash: a8218b6596601069b89a60ad018adf89a1f47cf6
ms.sourcegitcommit: e09dbff13f0b21b569a101f3b3c5efa174aec204
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/01/2020
ms.locfileid: "82624888"
---
# <a name="dotnet-test"></a><span data-ttu-id="71bc2-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="71bc2-103">dotnet test</span></span>

<span data-ttu-id="71bc2-104">**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="71bc2-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="71bc2-105">Název</span><span class="sxs-lookup"><span data-stu-id="71bc2-105">Name</span></span>

<span data-ttu-id="71bc2-106">`dotnet test`– Testovací ovladač .NET, který se používá ke spouštění testů jednotek.</span><span class="sxs-lookup"><span data-stu-id="71bc2-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="71bc2-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="71bc2-107">Synopsis</span></span>

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION>]
    [-a|--test-adapter-path <PATH_TO_ADAPTER>] [--blame]
    [-c|--configuration <CONFIGURATION>]
    [--collect <DATA_COLLECTOR_FRIENDLY_NAME>]
    [-d|--diag <PATH_TO_DIAGNOSTICS_FILE>] [-f|--framework <FRAMEWORK>]
    [--filter <EXPRESSION>] [--interactive]
    [-l|--logger <LOGGER_URI/FRIENDLY_NAME>] [--no-build]
    [--nologo] [--no-restore] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--results-directory <PATH>] [--runtime <RUNTIME_IDENTIFIER>]
    [-s|--settings <SETTINGS_FILE>] [-t|--list-tests]
    [-v|--verbosity <LEVEL>] [[--] <RunSettings arguments>]

dotnet test -h|--help
```

## <a name="description"></a><span data-ttu-id="71bc2-108">Popis</span><span class="sxs-lookup"><span data-stu-id="71bc2-108">Description</span></span>

<span data-ttu-id="71bc2-109">`dotnet test` Příkaz slouží ke spuštění testů jednotek v daném projektu.</span><span class="sxs-lookup"><span data-stu-id="71bc2-109">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="71bc2-110">`dotnet test` Příkaz spustí konzolovou aplikaci Test Runner určenou pro projekt.</span><span class="sxs-lookup"><span data-stu-id="71bc2-110">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="71bc2-111">Test Runner spustí testy definované pro systém testů jednotek (například MSTest, NUnit nebo xUnit) a ohlásí úspěch nebo neúspěch každého testu.</span><span class="sxs-lookup"><span data-stu-id="71bc2-111">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="71bc2-112">Pokud jsou všechny testy úspěšné, Test Runner vrátí 0 jako ukončovací kód; jinak, pokud nějaký test selže, vrátí 1.</span><span class="sxs-lookup"><span data-stu-id="71bc2-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="71bc2-113">Pro projekty zaměřené na více platforem jsou testy spouštěny pro každou cílovou architekturu.</span><span class="sxs-lookup"><span data-stu-id="71bc2-113">For multi-targeted projects, tests are run for each targeted framework.</span></span> <span data-ttu-id="71bc2-114">Test Runner a knihovna testů jednotek jsou zabaleny jako balíčky NuGet a jsou obnoveny jako běžné závislosti pro projekt.</span><span class="sxs-lookup"><span data-stu-id="71bc2-114">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="71bc2-115">Projekty testů určují testovací spouštěč pomocí obyčejného `<PackageReference>` prvku, jak je vidět v následujícím ukázkovém souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="71bc2-115">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

### <a name="implicit-restore"></a><span data-ttu-id="71bc2-116">Implicitní obnovení</span><span class="sxs-lookup"><span data-stu-id="71bc2-116">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="71bc2-117">Argumenty</span><span class="sxs-lookup"><span data-stu-id="71bc2-117">Arguments</span></span>

- **`PROJECT | SOLUTION`**

  <span data-ttu-id="71bc2-118">Cesta k testovacímu projektu nebo řešení.</span><span class="sxs-lookup"><span data-stu-id="71bc2-118">Path to the test project or solution.</span></span> <span data-ttu-id="71bc2-119">Pokud není zadaný, použije se ve výchozím nastavení aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="71bc2-119">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="71bc2-120">Možnosti</span><span class="sxs-lookup"><span data-stu-id="71bc2-120">Options</span></span>

- **`-a|--test-adapter-path <PATH_TO_ADAPTER>`**

  <span data-ttu-id="71bc2-121">Použijte vlastní testovací adaptéry ze zadané cesty v testovacím běhu.</span><span class="sxs-lookup"><span data-stu-id="71bc2-121">Use the custom test adapters from the specified path in the test run.</span></span>

- **`--blame`**

  <span data-ttu-id="71bc2-122">Spustí testy v režimu viny.</span><span class="sxs-lookup"><span data-stu-id="71bc2-122">Runs the tests in blame mode.</span></span> <span data-ttu-id="71bc2-123">Tato možnost je užitečná při izolaci problematických testů, které způsobují selhání hostitele testu.</span><span class="sxs-lookup"><span data-stu-id="71bc2-123">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="71bc2-124">Vytvoří výstupní soubor v aktuálním adresáři jako *Sequence. XML* , který zachycuje pořadí spuštění testů před selháním.</span><span class="sxs-lookup"><span data-stu-id="71bc2-124">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="71bc2-125">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="71bc2-125">Defines the build configuration.</span></span> <span data-ttu-id="71bc2-126">Výchozí hodnota je `Debug`, ale konfigurace vašeho projektu může přepsat toto výchozí nastavení sady SDK.</span><span class="sxs-lookup"><span data-stu-id="71bc2-126">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  <span data-ttu-id="71bc2-127">Povolí shromažďování dat pro testovací běh.</span><span class="sxs-lookup"><span data-stu-id="71bc2-127">Enables data collector for the test run.</span></span> <span data-ttu-id="71bc2-128">Další informace najdete v tématu [monitorování a analýza testovacího běhu](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="71bc2-128">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

- **`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  <span data-ttu-id="71bc2-129">Povolí diagnostický režim pro testovací platformu a zapíše diagnostické zprávy do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="71bc2-129">Enables diagnostic mode for the test platform and writes diagnostic messages to the specified file.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="71bc2-130">Vyhledá testovací binární soubory pro konkrétní [rozhraní](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="71bc2-130">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="71bc2-131">Odfiltruje testy v aktuálním projektu pomocí daného výrazu.</span><span class="sxs-lookup"><span data-stu-id="71bc2-131">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="71bc2-132">Další informace najdete v části [Podrobnosti o možnosti filtru](#filter-option-details) .</span><span class="sxs-lookup"><span data-stu-id="71bc2-132">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="71bc2-133">Další informace a příklady použití selektivního filtrování testů jednotek naleznete v tématu [spuštění selektivních testů jednotek](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="71bc2-133">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="71bc2-134">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="71bc2-134">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="71bc2-135">Umožňuje zastavení příkazu zastavit a počkat na vstup nebo akci uživatele.</span><span class="sxs-lookup"><span data-stu-id="71bc2-135">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="71bc2-136">Například k dokončení ověřování.</span><span class="sxs-lookup"><span data-stu-id="71bc2-136">For example, to complete authentication.</span></span> <span data-ttu-id="71bc2-137">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="71bc2-137">Available since .NET Core 3.0 SDK.</span></span>

- **`-l|--logger <LOGGER_URI/FRIENDLY_NAME>`**

  <span data-ttu-id="71bc2-138">Určuje protokolovací nástroj pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="71bc2-138">Specifies a logger for test results.</span></span> <span data-ttu-id="71bc2-139">Na rozdíl od MSBuild test dotnet nepřijímá zkratky: místo `-l "console;v=d"` použití. `-l "console;verbosity=detailed"`</span><span class="sxs-lookup"><span data-stu-id="71bc2-139">Unlike MSBuild, dotnet test doesn't accept abbreviations: instead of `-l "console;v=d"` use `-l "console;verbosity=detailed"`.</span></span>

- **`--no-build`**

  <span data-ttu-id="71bc2-140">Před spuštěním nevytvoří testovací projekt.</span><span class="sxs-lookup"><span data-stu-id="71bc2-140">Doesn't build the test project before running it.</span></span> <span data-ttu-id="71bc2-141">Také implicitně nastaví příznak- `--no-restore` .</span><span class="sxs-lookup"><span data-stu-id="71bc2-141">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="71bc2-142">Spusťte testy bez zobrazení banneru Microsoft TestPlatform.</span><span class="sxs-lookup"><span data-stu-id="71bc2-142">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="71bc2-143">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="71bc2-143">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="71bc2-144">Při spuštění příkazu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="71bc2-144">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="71bc2-145">Adresář, ve kterém se mají najít binární soubory, které se mají spustit.</span><span class="sxs-lookup"><span data-stu-id="71bc2-145">Directory in which to find the binaries to run.</span></span> <span data-ttu-id="71bc2-146">Pokud není zadaný, použije se výchozí cesta `./bin/<configuration>/<framework>/`.</span><span class="sxs-lookup"><span data-stu-id="71bc2-146">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="71bc2-147">Pro projekty s více cílovými rozhraními (prostřednictvím `TargetFrameworks` vlastnosti) musíte definovat `--framework` i při zadání této možnosti.</span><span class="sxs-lookup"><span data-stu-id="71bc2-147">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span> <span data-ttu-id="71bc2-148">`dotnet test`vždy spouštějte testy z výstupního adresáře.</span><span class="sxs-lookup"><span data-stu-id="71bc2-148">`dotnet test` always run tests from the output directory.</span></span> <span data-ttu-id="71bc2-149">Můžete použít <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> pro využívání testovacích prostředků ve výstupním adresáři.</span><span class="sxs-lookup"><span data-stu-id="71bc2-149">You can use <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> to consume test assets in the output directory.</span></span>

- **`-r|--results-directory <PATH>`**

  <span data-ttu-id="71bc2-150">Adresář, do kterého budou umístěny výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="71bc2-150">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="71bc2-151">Pokud zadaný adresář neexistuje, vytvoří se.</span><span class="sxs-lookup"><span data-stu-id="71bc2-151">If the specified directory doesn't exist, it's created.</span></span> <span data-ttu-id="71bc2-152">Výchozí hodnota je `TestResults` v adresáři, který obsahuje soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="71bc2-152">The default is `TestResults` in the directory that contains the project file.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="71bc2-153">Cílový modul runtime, pro který se má testovat.</span><span class="sxs-lookup"><span data-stu-id="71bc2-153">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="71bc2-154">`.runsettings` Soubor, který se má použít pro spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="71bc2-154">The `.runsettings` file to use for running the tests.</span></span> <span data-ttu-id="71bc2-155">Všimněte si, `TargetPlatform` že element (x86 | x64) nemá žádný vliv `dotnet test`na.</span><span class="sxs-lookup"><span data-stu-id="71bc2-155">Note that the `TargetPlatform` element (x86|x64) has no effect for `dotnet test`.</span></span> <span data-ttu-id="71bc2-156">Chcete-li spustit testy, které cílí na x86, nainstalujte verzi x86 rozhraní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="71bc2-156">To run tests that target x86, install the x86 version of .NET Core.</span></span> <span data-ttu-id="71bc2-157">Bitová verze příkazu *dotnet. exe* , který je na cestě, bude použit pro spouštění testů.</span><span class="sxs-lookup"><span data-stu-id="71bc2-157">The bitness of the *dotnet.exe* that is on the path is what will be used for running tests.</span></span> <span data-ttu-id="71bc2-158">Další informace najdete v následujících zdrojích informací:</span><span class="sxs-lookup"><span data-stu-id="71bc2-158">for more information, see the following resources:</span></span>

  - [<span data-ttu-id="71bc2-159">Nakonfigurujte testy jednotek pomocí `.runsettings` souboru.</span><span class="sxs-lookup"><span data-stu-id="71bc2-159">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)
  - [<span data-ttu-id="71bc2-160">Konfigurace testovacího běhu</span><span class="sxs-lookup"><span data-stu-id="71bc2-160">Configure a test run</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/configure.md)

- **`-t|--list-tests`**

  <span data-ttu-id="71bc2-161">Vypíše všechny zjištěné testy v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="71bc2-161">List all of the discovered tests in the current project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="71bc2-162">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="71bc2-162">Sets the verbosity level of the command.</span></span> <span data-ttu-id="71bc2-163">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]` `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="71bc2-163">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="71bc2-164">Výchozí formát je `minimal`.</span><span class="sxs-lookup"><span data-stu-id="71bc2-164">The default is `minimal`.</span></span> <span data-ttu-id="71bc2-165">Další informace naleznete v tématu <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span><span class="sxs-lookup"><span data-stu-id="71bc2-165">For more information, see <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span></span>

- <span data-ttu-id="71bc2-166">**`RunSettings`** náhodné</span><span class="sxs-lookup"><span data-stu-id="71bc2-166">**`RunSettings`** arguments</span></span>

  <span data-ttu-id="71bc2-167">Argumenty jsou předány `RunSettings` jako konfigurace pro test.</span><span class="sxs-lookup"><span data-stu-id="71bc2-167">Arguments are passed as `RunSettings` configurations for the test.</span></span> <span data-ttu-id="71bc2-168">Argumenty jsou zadány `[name]=[value]` jako páry po "--" (Všimněte si mezer za-).</span><span class="sxs-lookup"><span data-stu-id="71bc2-168">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="71bc2-169">K oddělení více `[name]=[value]` párů se používá mezera.</span><span class="sxs-lookup"><span data-stu-id="71bc2-169">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="71bc2-170">Příklad: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="71bc2-170">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="71bc2-171">Další informace najdete v tématu [předávání argumentů runsettings pomocí příkazového řádku](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="71bc2-171">For more information, see [Passing RunSettings arguments through command line](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="71bc2-172">Příklady</span><span class="sxs-lookup"><span data-stu-id="71bc2-172">Examples</span></span>

- <span data-ttu-id="71bc2-173">Spustit testy v projektu v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="71bc2-173">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="71bc2-174">Spustit testy v `test1` projektu:</span><span class="sxs-lookup"><span data-stu-id="71bc2-174">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="71bc2-175">Spusťte testy v projektu v aktuálním adresáři a vygenerujte soubor výsledků testů ve formátu TRX:</span><span class="sxs-lookup"><span data-stu-id="71bc2-175">Run the tests in the project in the current directory, and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

- <span data-ttu-id="71bc2-176">Spusťte testy v projektu v aktuálním adresáři a log s detailní podrobností do konzoly:</span><span class="sxs-lookup"><span data-stu-id="71bc2-176">Run the tests in the project in the current directory, and log with detailed verbosity to the console:</span></span>

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```

## <a name="filter-option-details"></a><span data-ttu-id="71bc2-177">Podrobnosti možnosti filtru</span><span class="sxs-lookup"><span data-stu-id="71bc2-177">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="71bc2-178">`<Expression>`má formát `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="71bc2-178">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="71bc2-179">`<property>`je atributem `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="71bc2-179">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="71bc2-180">Níže jsou uvedené vlastnosti podporované oblíbenými rozhraními pro testování částí:</span><span class="sxs-lookup"><span data-stu-id="71bc2-180">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="71bc2-181">Testovací rozhraní</span><span class="sxs-lookup"><span data-stu-id="71bc2-181">Test Framework</span></span> | <span data-ttu-id="71bc2-182">Podporované vlastnosti</span><span class="sxs-lookup"><span data-stu-id="71bc2-182">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="71bc2-183">MSTest</span><span class="sxs-lookup"><span data-stu-id="71bc2-183">MSTest</span></span>         | <ul><li><span data-ttu-id="71bc2-184">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="71bc2-184">FullyQualifiedName</span></span></li><li><span data-ttu-id="71bc2-185">Název</span><span class="sxs-lookup"><span data-stu-id="71bc2-185">Name</span></span></li><li><span data-ttu-id="71bc2-186">NázevTřídy</span><span class="sxs-lookup"><span data-stu-id="71bc2-186">ClassName</span></span></li><li><span data-ttu-id="71bc2-187">Priorita</span><span class="sxs-lookup"><span data-stu-id="71bc2-187">Priority</span></span></li><li><span data-ttu-id="71bc2-188">TestCategory</span><span class="sxs-lookup"><span data-stu-id="71bc2-188">TestCategory</span></span></li></ul> |
| <span data-ttu-id="71bc2-189">xUnit</span><span class="sxs-lookup"><span data-stu-id="71bc2-189">xUnit</span></span>          | <ul><li><span data-ttu-id="71bc2-190">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="71bc2-190">FullyQualifiedName</span></span></li><li><span data-ttu-id="71bc2-191">DisplayName</span><span class="sxs-lookup"><span data-stu-id="71bc2-191">DisplayName</span></span></li><li><span data-ttu-id="71bc2-192">Traits</span><span class="sxs-lookup"><span data-stu-id="71bc2-192">Traits</span></span></li></ul>                                   |

<span data-ttu-id="71bc2-193">`<operator>` Popisuje vztah mezi vlastností a hodnotou:</span><span class="sxs-lookup"><span data-stu-id="71bc2-193">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="71bc2-194">Operátor</span><span class="sxs-lookup"><span data-stu-id="71bc2-194">Operator</span></span> | <span data-ttu-id="71bc2-195">Funkce</span><span class="sxs-lookup"><span data-stu-id="71bc2-195">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="71bc2-196">Přesná shoda</span><span class="sxs-lookup"><span data-stu-id="71bc2-196">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="71bc2-197">Nepřesná shoda</span><span class="sxs-lookup"><span data-stu-id="71bc2-197">Not exact match</span></span> |
| `~`      | <span data-ttu-id="71bc2-198">Contains</span><span class="sxs-lookup"><span data-stu-id="71bc2-198">Contains</span></span>        |
| `!~`     | <span data-ttu-id="71bc2-199">Neobsahuje</span><span class="sxs-lookup"><span data-stu-id="71bc2-199">Not contains</span></span>    |

<span data-ttu-id="71bc2-200">`<value>`je řetězec.</span><span class="sxs-lookup"><span data-stu-id="71bc2-200">`<value>` is a string.</span></span> <span data-ttu-id="71bc2-201">U všech hledání se nerozlišují malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="71bc2-201">All the lookups are case insensitive.</span></span>

<span data-ttu-id="71bc2-202">Výraz bez objektu `<operator>` je automaticky považován za vlastnost `contains` on `FullyQualifiedName` (například `dotnet test --filter xyz` je stejný jako `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="71bc2-202">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="71bc2-203">Výrazy se dají spojit s podmíněnými operátory:</span><span class="sxs-lookup"><span data-stu-id="71bc2-203">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="71bc2-204">Operátor</span><span class="sxs-lookup"><span data-stu-id="71bc2-204">Operator</span></span>            | <span data-ttu-id="71bc2-205">Funkce</span><span class="sxs-lookup"><span data-stu-id="71bc2-205">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="71bc2-206">NEBO</span><span class="sxs-lookup"><span data-stu-id="71bc2-206">OR</span></span>       |
| `&`                 | <span data-ttu-id="71bc2-207">AND</span><span class="sxs-lookup"><span data-stu-id="71bc2-207">AND</span></span>      |

<span data-ttu-id="71bc2-208">Výrazy můžete uzavřít do závorek při použití podmíněných operátorů (například `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="71bc2-208">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="71bc2-209">Další informace a příklady použití selektivního filtrování testů jednotek naleznete v tématu [spuštění selektivních testů jednotek](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="71bc2-209">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="71bc2-210">Viz také</span><span class="sxs-lookup"><span data-stu-id="71bc2-210">See also</span></span>

- [<span data-ttu-id="71bc2-211">Architektury a cíle</span><span class="sxs-lookup"><span data-stu-id="71bc2-211">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="71bc2-212">Katalog identifikátorů runtime .NET Core (RID)</span><span class="sxs-lookup"><span data-stu-id="71bc2-212">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="71bc2-213">Předávání argumentů runsettings prostřednictvím příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="71bc2-213">Passing runsettings arguments through commandline</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
