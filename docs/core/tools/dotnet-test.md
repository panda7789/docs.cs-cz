---
title: dotnet test, příkaz
description: Dotnet test příkaz se používá k provedení testů částí v daném projektu.
ms.date: 02/27/2020
ms.openlocfilehash: 69b8101f9b1052f4726dce8a86234da99f5dc89c
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102737"
---
# <a name="dotnet-test"></a><span data-ttu-id="e76cd-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="e76cd-103">dotnet test</span></span>

<span data-ttu-id="e76cd-104">**Tento článek se týká:** ✔️ .NET Core 2.1 SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="e76cd-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="e76cd-105">Název</span><span class="sxs-lookup"><span data-stu-id="e76cd-105">Name</span></span>

<span data-ttu-id="e76cd-106">`dotnet test`- Testovací ovladač .NET používaný ke spuštění testů částí.</span><span class="sxs-lookup"><span data-stu-id="e76cd-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e76cd-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="e76cd-107">Synopsis</span></span>

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

## <a name="description"></a><span data-ttu-id="e76cd-108">Popis</span><span class="sxs-lookup"><span data-stu-id="e76cd-108">Description</span></span>

<span data-ttu-id="e76cd-109">Příkaz `dotnet test` se používá ke spuštění testů částí v daném projektu.</span><span class="sxs-lookup"><span data-stu-id="e76cd-109">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="e76cd-110">Příkaz `dotnet test` spustí aplikace konzoly pro spuštění testu určená pro projekt.</span><span class="sxs-lookup"><span data-stu-id="e76cd-110">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="e76cd-111">Testovací běžec provede testy definované pro rozhraní testování částí (například MSTest, NUnit nebo xUnit) a hlásí úspěch nebo neúspěch každého testu.</span><span class="sxs-lookup"><span data-stu-id="e76cd-111">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="e76cd-112">Pokud jsou všechny testy úspěšné, testovací běžec vrátí 0 jako ukončovací kód; v opačném případě, pokud některý test selže, vrátí 1.</span><span class="sxs-lookup"><span data-stu-id="e76cd-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="e76cd-113">Testovací běžec a knihovna testování částí jsou zabaleny jako balíčky NuGet a jsou obnoveny jako běžné závislosti pro projekt.</span><span class="sxs-lookup"><span data-stu-id="e76cd-113">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="e76cd-114">Testovací projekty určují testovací `<PackageReference>` běh pomocí běžného prvku, jak je vidět v následujícím ukázkovém souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="e76cd-114">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

### <a name="implicit-restore"></a><span data-ttu-id="e76cd-115">Implicitní obnovení</span><span class="sxs-lookup"><span data-stu-id="e76cd-115">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="e76cd-116">Argumenty</span><span class="sxs-lookup"><span data-stu-id="e76cd-116">Arguments</span></span>

- **`PROJECT | SOLUTION`**

  <span data-ttu-id="e76cd-117">Cesta k testovacímu projektu nebo řešení.</span><span class="sxs-lookup"><span data-stu-id="e76cd-117">Path to the test project or solution.</span></span> <span data-ttu-id="e76cd-118">Pokud není zadán, je výchozí aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="e76cd-118">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="e76cd-119">Možnosti</span><span class="sxs-lookup"><span data-stu-id="e76cd-119">Options</span></span>

- **`-a|--test-adapter-path <PATH_TO_ADAPTER>`**

  <span data-ttu-id="e76cd-120">Použijte vlastní testovací adaptéry ze zadané cesty v testovacím běhu.</span><span class="sxs-lookup"><span data-stu-id="e76cd-120">Use the custom test adapters from the specified path in the test run.</span></span>

- **`--blame`**

  <span data-ttu-id="e76cd-121">Spustí testy v režimu obviňování.</span><span class="sxs-lookup"><span data-stu-id="e76cd-121">Runs the tests in blame mode.</span></span> <span data-ttu-id="e76cd-122">Tato možnost je užitečná při izolování problémových testů, které způsobují selhání testovacího hostitele.</span><span class="sxs-lookup"><span data-stu-id="e76cd-122">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="e76cd-123">Vytvoří výstupní soubor v aktuálním adresáři jako *Sequence.xml,* který zachycuje pořadí spuštění testů před selháním.</span><span class="sxs-lookup"><span data-stu-id="e76cd-123">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="e76cd-124">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="e76cd-124">Defines the build configuration.</span></span> <span data-ttu-id="e76cd-125">Výchozí hodnota `Debug`je , ale konfigurace projektu může přepsat toto výchozí nastavení sady SDK.</span><span class="sxs-lookup"><span data-stu-id="e76cd-125">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  <span data-ttu-id="e76cd-126">Povolí sběr dat pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="e76cd-126">Enables data collector for the test run.</span></span> <span data-ttu-id="e76cd-127">Další informace naleznete v [tématu Sledování a analýza testovacího běhu](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="e76cd-127">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

- **`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  <span data-ttu-id="e76cd-128">Povolí diagnostický režim pro testovací platformu a zapíše diagnostické zprávy do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="e76cd-128">Enables diagnostic mode for the test platform and writes diagnostic messages to the specified file.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e76cd-129">Vyhledá testovací binární soubory pro konkrétní [rámec](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="e76cd-129">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="e76cd-130">Odfiltruje testy v aktuálním projektu pomocí daného výrazu.</span><span class="sxs-lookup"><span data-stu-id="e76cd-130">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="e76cd-131">Další informace naleznete v části [Podrobnosti o možnosti filtr.](#filter-option-details)</span><span class="sxs-lookup"><span data-stu-id="e76cd-131">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="e76cd-132">Další informace a příklady použití filtrace testů selektivních testů částí naleznete v [tématu Spuštění testů selektivních částí](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="e76cd-132">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="e76cd-133">Vytiskne krátkou nápovědu pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="e76cd-133">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="e76cd-134">Umožňuje příkazu zastavit a čekat na vstup uživatele nebo akci.</span><span class="sxs-lookup"><span data-stu-id="e76cd-134">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="e76cd-135">Například k dokončení ověřování.</span><span class="sxs-lookup"><span data-stu-id="e76cd-135">For example, to complete authentication.</span></span> <span data-ttu-id="e76cd-136">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="e76cd-136">Available since .NET Core 3.0 SDK.</span></span>

- **`-l|--logger <LOGGER_URI/FRIENDLY_NAME>`**

  <span data-ttu-id="e76cd-137">Určuje protokolovací nástroj pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="e76cd-137">Specifies a logger for test results.</span></span> <span data-ttu-id="e76cd-138">Na rozdíl od MSBuild, dotnet test nepřijímá zkratky: `-l "console;v=d"` `-l "console;verbosity=detailed"`místo použití .</span><span class="sxs-lookup"><span data-stu-id="e76cd-138">Unlike MSBuild, dotnet test doesn't accept abbreviations: instead of `-l "console;v=d"` use `-l "console;verbosity=detailed"`.</span></span>

- **`--no-build`**

  <span data-ttu-id="e76cd-139">Nesestaví testovací projekt před jeho spuštěním.</span><span class="sxs-lookup"><span data-stu-id="e76cd-139">Doesn't build the test project before running it.</span></span> <span data-ttu-id="e76cd-140">Také implicitně nastaví `--no-restore` - příznak.</span><span class="sxs-lookup"><span data-stu-id="e76cd-140">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="e76cd-141">Spusťte testy bez zobrazení hlavičky Microsoft TestPlatform.</span><span class="sxs-lookup"><span data-stu-id="e76cd-141">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="e76cd-142">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="e76cd-142">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="e76cd-143">Nespustí implicitní obnovení při spuštění příkazu.</span><span class="sxs-lookup"><span data-stu-id="e76cd-143">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="e76cd-144">Adresář, ve kterém chcete najít binární soubory ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="e76cd-144">Directory in which to find the binaries to run.</span></span> <span data-ttu-id="e76cd-145">Pokud není zadán, výchozí `./bin/<configuration>/<framework>/`cesta je .</span><span class="sxs-lookup"><span data-stu-id="e76cd-145">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="e76cd-146">Pro projekty s více cílových rozhraní (prostřednictvím vlastnosti) `TargetFrameworks` je také nutné definovat, `--framework` když zadáte tuto možnost.</span><span class="sxs-lookup"><span data-stu-id="e76cd-146">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span>

- **`-r|--results-directory <PATH>`**

  <span data-ttu-id="e76cd-147">Adresář, kde budou umístěny výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="e76cd-147">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="e76cd-148">Pokud zadaný adresář neexistuje, je vytvořen.</span><span class="sxs-lookup"><span data-stu-id="e76cd-148">If the specified directory doesn't exist, it's created.</span></span> <span data-ttu-id="e76cd-149">Výchozí hodnota `TestResults` je v adresáři, který obsahuje soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="e76cd-149">The default is `TestResults` in the directory that contains the project file.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="e76cd-150">Cílový runtime, pro který chcete testovat.</span><span class="sxs-lookup"><span data-stu-id="e76cd-150">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="e76cd-151">Soubor, `.runsettings` který chcete použít pro spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="e76cd-151">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="e76cd-152">Nakonfigurujte `.runsettings` testy částí pomocí souboru.</span><span class="sxs-lookup"><span data-stu-id="e76cd-152">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

- **`-t|--list-tests`**

  <span data-ttu-id="e76cd-153">Seznam všech zjištěných testů v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="e76cd-153">List all of the discovered tests in the current project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="e76cd-154">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="e76cd-154">Sets the verbosity level of the command.</span></span> <span data-ttu-id="e76cd-155">Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a .</span><span class="sxs-lookup"><span data-stu-id="e76cd-155">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="e76cd-156">Výchozí formát je `minimal`.</span><span class="sxs-lookup"><span data-stu-id="e76cd-156">The default is `minimal`.</span></span> <span data-ttu-id="e76cd-157">Další informace naleznete v tématu <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span><span class="sxs-lookup"><span data-stu-id="e76cd-157">For more information, see <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span></span>

- <span data-ttu-id="e76cd-158">**`RunSettings`** Argumenty</span><span class="sxs-lookup"><span data-stu-id="e76cd-158">**`RunSettings`** arguments</span></span>

  <span data-ttu-id="e76cd-159">Argumenty jsou `RunSettings` předány jako konfigurace pro test.</span><span class="sxs-lookup"><span data-stu-id="e76cd-159">Arguments are passed as `RunSettings` configurations for the test.</span></span> <span data-ttu-id="e76cd-160">Argumenty jsou `[name]=[value]` určeny jako páry po "-- " (všimněte si mezery po --).</span><span class="sxs-lookup"><span data-stu-id="e76cd-160">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="e76cd-161">Mezera se používá `[name]=[value]` k oddělení více párů.</span><span class="sxs-lookup"><span data-stu-id="e76cd-161">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="e76cd-162">Příklad: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="e76cd-162">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="e76cd-163">Další informace naleznete [v tématu Předávání argumentů RunSettings prostřednictvím příkazového řádku](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="e76cd-163">For more information, see [Passing RunSettings arguments through command line](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="e76cd-164">Příklady</span><span class="sxs-lookup"><span data-stu-id="e76cd-164">Examples</span></span>

- <span data-ttu-id="e76cd-165">Spusťte testy v projektu v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="e76cd-165">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="e76cd-166">Spusťte testy `test1` v projektu:</span><span class="sxs-lookup"><span data-stu-id="e76cd-166">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="e76cd-167">Spusťte testy v projektu v aktuálním adresáři a vygenerujte soubor výsledků testu ve formátu trx:</span><span class="sxs-lookup"><span data-stu-id="e76cd-167">Run the tests in the project in the current directory, and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

- <span data-ttu-id="e76cd-168">Spusťte testy v projektu v aktuálním adresáři a protokolujte s podrobnou podrobností do konzoly:</span><span class="sxs-lookup"><span data-stu-id="e76cd-168">Run the tests in the project in the current directory, and log with detailed verbosity to the console:</span></span>

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```

## <a name="filter-option-details"></a><span data-ttu-id="e76cd-169">Podrobnosti o možnosti filtru</span><span class="sxs-lookup"><span data-stu-id="e76cd-169">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="e76cd-170">`<Expression>`má formát `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="e76cd-170">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="e76cd-171">`<property>`je atributem `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="e76cd-171">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="e76cd-172">Následují vlastnosti podporované populární rozhraní testování částí:</span><span class="sxs-lookup"><span data-stu-id="e76cd-172">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="e76cd-173">Testovací rámec</span><span class="sxs-lookup"><span data-stu-id="e76cd-173">Test Framework</span></span> | <span data-ttu-id="e76cd-174">Podporované vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e76cd-174">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="e76cd-175">MSTest</span><span class="sxs-lookup"><span data-stu-id="e76cd-175">MSTest</span></span>         | <ul><li><span data-ttu-id="e76cd-176">Plně kvalifikovaný název</span><span class="sxs-lookup"><span data-stu-id="e76cd-176">FullyQualifiedName</span></span></li><li><span data-ttu-id="e76cd-177">Název</span><span class="sxs-lookup"><span data-stu-id="e76cd-177">Name</span></span></li><li><span data-ttu-id="e76cd-178">Classname</span><span class="sxs-lookup"><span data-stu-id="e76cd-178">ClassName</span></span></li><li><span data-ttu-id="e76cd-179">Priorita</span><span class="sxs-lookup"><span data-stu-id="e76cd-179">Priority</span></span></li><li><span data-ttu-id="e76cd-180">Kategorie testů</span><span class="sxs-lookup"><span data-stu-id="e76cd-180">TestCategory</span></span></li></ul> |
| <span data-ttu-id="e76cd-181">xJednotka</span><span class="sxs-lookup"><span data-stu-id="e76cd-181">xUnit</span></span>          | <ul><li><span data-ttu-id="e76cd-182">Plně kvalifikovaný název</span><span class="sxs-lookup"><span data-stu-id="e76cd-182">FullyQualifiedName</span></span></li><li><span data-ttu-id="e76cd-183">DisplayName</span><span class="sxs-lookup"><span data-stu-id="e76cd-183">DisplayName</span></span></li><li><span data-ttu-id="e76cd-184">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e76cd-184">Traits</span></span></li></ul>                                   |

<span data-ttu-id="e76cd-185">Popisuje `<operator>` vztah mezi vlastností a hodnotou:</span><span class="sxs-lookup"><span data-stu-id="e76cd-185">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="e76cd-186">Operátor</span><span class="sxs-lookup"><span data-stu-id="e76cd-186">Operator</span></span> | <span data-ttu-id="e76cd-187">Funkce</span><span class="sxs-lookup"><span data-stu-id="e76cd-187">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="e76cd-188">Přesná shoda</span><span class="sxs-lookup"><span data-stu-id="e76cd-188">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="e76cd-189">Není přesná shoda</span><span class="sxs-lookup"><span data-stu-id="e76cd-189">Not exact match</span></span> |
| `~`      | <span data-ttu-id="e76cd-190">Contains</span><span class="sxs-lookup"><span data-stu-id="e76cd-190">Contains</span></span>        |
| `!~`     | <span data-ttu-id="e76cd-191">Neobsahuje</span><span class="sxs-lookup"><span data-stu-id="e76cd-191">Not contains</span></span>    |

<span data-ttu-id="e76cd-192">`<value>`je řetězec.</span><span class="sxs-lookup"><span data-stu-id="e76cd-192">`<value>` is a string.</span></span> <span data-ttu-id="e76cd-193">Všechna vyhledávání jsou malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="e76cd-193">All the lookups are case insensitive.</span></span>

<span data-ttu-id="e76cd-194">Výraz bez `<operator>` je automaticky považován `contains` `FullyQualifiedName` za vlastnost on `dotnet test --filter xyz` (například je stejný jako `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="e76cd-194">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="e76cd-195">Výrazy lze spojit s podmíněnými operátory:</span><span class="sxs-lookup"><span data-stu-id="e76cd-195">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="e76cd-196">Operátor</span><span class="sxs-lookup"><span data-stu-id="e76cd-196">Operator</span></span>            | <span data-ttu-id="e76cd-197">Funkce</span><span class="sxs-lookup"><span data-stu-id="e76cd-197">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="e76cd-198">NEBO</span><span class="sxs-lookup"><span data-stu-id="e76cd-198">OR</span></span>       |
| `&`                 | <span data-ttu-id="e76cd-199">AND</span><span class="sxs-lookup"><span data-stu-id="e76cd-199">AND</span></span>      |

<span data-ttu-id="e76cd-200">Výrazy můžete uzavřít do závorek při použití podmíněných operátorů `(Name~TestMethod1) | (Name~TestMethod2)`(například).</span><span class="sxs-lookup"><span data-stu-id="e76cd-200">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="e76cd-201">Další informace a příklady použití filtrace testů selektivních testů částí naleznete v [tématu Spuštění testů selektivních částí](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="e76cd-201">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e76cd-202">Viz také</span><span class="sxs-lookup"><span data-stu-id="e76cd-202">See also</span></span>

- [<span data-ttu-id="e76cd-203">Rámce a cíle</span><span class="sxs-lookup"><span data-stu-id="e76cd-203">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="e76cd-204">Katalog IDentifier (RID) modulu .NET Core Runtime</span><span class="sxs-lookup"><span data-stu-id="e76cd-204">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="e76cd-205">Předávání argumentů runsettings prostřednictvím příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="e76cd-205">Passing runsettings arguments through commandline</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
