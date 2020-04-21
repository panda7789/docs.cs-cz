---
title: dotnet test, příkaz
description: Dotnet test příkaz se používá k provedení testů částí v daném projektu.
ms.date: 02/27/2020
ms.openlocfilehash: 2eebcbe2e4a1660da4ffa4ea9a68190c8443463a
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739106"
---
# <a name="dotnet-test"></a><span data-ttu-id="2a33a-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="2a33a-103">dotnet test</span></span>

<span data-ttu-id="2a33a-104">**Tento článek se týká:** ✔️ .NET Core 2.1 SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="2a33a-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="2a33a-105">Název</span><span class="sxs-lookup"><span data-stu-id="2a33a-105">Name</span></span>

<span data-ttu-id="2a33a-106">`dotnet test`- Testovací ovladač .NET používaný ke spuštění testů částí.</span><span class="sxs-lookup"><span data-stu-id="2a33a-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2a33a-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="2a33a-107">Synopsis</span></span>

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

## <a name="description"></a><span data-ttu-id="2a33a-108">Popis</span><span class="sxs-lookup"><span data-stu-id="2a33a-108">Description</span></span>

<span data-ttu-id="2a33a-109">Příkaz `dotnet test` se používá ke spuštění testů částí v daném projektu.</span><span class="sxs-lookup"><span data-stu-id="2a33a-109">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="2a33a-110">Příkaz `dotnet test` spustí aplikace konzoly pro spuštění testu určená pro projekt.</span><span class="sxs-lookup"><span data-stu-id="2a33a-110">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="2a33a-111">Testovací běžec provede testy definované pro rozhraní testování částí (například MSTest, NUnit nebo xUnit) a hlásí úspěch nebo neúspěch každého testu.</span><span class="sxs-lookup"><span data-stu-id="2a33a-111">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="2a33a-112">Pokud jsou všechny testy úspěšné, testovací běžec vrátí 0 jako ukončovací kód; v opačném případě, pokud některý test selže, vrátí 1.</span><span class="sxs-lookup"><span data-stu-id="2a33a-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="2a33a-113">Testovací běžec a knihovna testování částí jsou zabaleny jako balíčky NuGet a jsou obnoveny jako běžné závislosti pro projekt.</span><span class="sxs-lookup"><span data-stu-id="2a33a-113">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="2a33a-114">Testovací projekty určují testovací `<PackageReference>` běh pomocí běžného prvku, jak je vidět v následujícím ukázkovém souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="2a33a-114">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="2a33a-115">Argumenty</span><span class="sxs-lookup"><span data-stu-id="2a33a-115">Arguments</span></span>

- **`PROJECT | SOLUTION`**

  <span data-ttu-id="2a33a-116">Cesta k testovacímu projektu nebo řešení.</span><span class="sxs-lookup"><span data-stu-id="2a33a-116">Path to the test project or solution.</span></span> <span data-ttu-id="2a33a-117">Pokud není zadán, je výchozí aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="2a33a-117">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="2a33a-118">Možnosti</span><span class="sxs-lookup"><span data-stu-id="2a33a-118">Options</span></span>

- **`-a|--test-adapter-path <PATH_TO_ADAPTER>`**

  <span data-ttu-id="2a33a-119">Použijte vlastní testovací adaptéry ze zadané cesty v testovacím běhu.</span><span class="sxs-lookup"><span data-stu-id="2a33a-119">Use the custom test adapters from the specified path in the test run.</span></span>

- **`--blame`**

  <span data-ttu-id="2a33a-120">Spustí testy v režimu obviňování.</span><span class="sxs-lookup"><span data-stu-id="2a33a-120">Runs the tests in blame mode.</span></span> <span data-ttu-id="2a33a-121">Tato možnost je užitečná při izolování problémových testů, které způsobují selhání testovacího hostitele.</span><span class="sxs-lookup"><span data-stu-id="2a33a-121">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="2a33a-122">Vytvoří výstupní soubor v aktuálním adresáři jako *Sequence.xml,* který zachycuje pořadí spuštění testů před selháním.</span><span class="sxs-lookup"><span data-stu-id="2a33a-122">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="2a33a-123">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="2a33a-123">Defines the build configuration.</span></span> <span data-ttu-id="2a33a-124">Výchozí hodnota `Debug`je , ale konfigurace projektu může přepsat toto výchozí nastavení sady SDK.</span><span class="sxs-lookup"><span data-stu-id="2a33a-124">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  <span data-ttu-id="2a33a-125">Povolí sběr dat pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="2a33a-125">Enables data collector for the test run.</span></span> <span data-ttu-id="2a33a-126">Další informace naleznete v [tématu Sledování a analýza testovacího běhu](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="2a33a-126">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

- **`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  <span data-ttu-id="2a33a-127">Povolí diagnostický režim pro testovací platformu a zapisuje diagnostické zprávy do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="2a33a-127">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="2a33a-128">Vyhledá testovací binární soubory pro konkrétní [rámec](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="2a33a-128">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="2a33a-129">Odfiltruje testy v aktuálním projektu pomocí daného výrazu.</span><span class="sxs-lookup"><span data-stu-id="2a33a-129">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="2a33a-130">Další informace naleznete v části [Podrobnosti o možnosti filtr.](#filter-option-details)</span><span class="sxs-lookup"><span data-stu-id="2a33a-130">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="2a33a-131">Další informace a příklady použití filtrace testů selektivních testů částí naleznete v [tématu Spuštění testů selektivních částí](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="2a33a-131">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="2a33a-132">Vytiskne krátkou nápovědu pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="2a33a-132">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="2a33a-133">Umožňuje příkazu zastavit a čekat na vstup uživatele nebo akci.</span><span class="sxs-lookup"><span data-stu-id="2a33a-133">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="2a33a-134">Například k dokončení ověřování.</span><span class="sxs-lookup"><span data-stu-id="2a33a-134">For example, to complete authentication.</span></span> <span data-ttu-id="2a33a-135">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="2a33a-135">Available since .NET Core 3.0 SDK.</span></span>

- **`-l|--logger <LOGGER_URI/FRIENDLY_NAME>`**

  <span data-ttu-id="2a33a-136">Určuje protokolovací nástroj pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="2a33a-136">Specifies a logger for test results.</span></span> <span data-ttu-id="2a33a-137">Na rozdíl od MSBuild, dotnet test nepřijímá zkratky: `-l "console;v=d"` `-l "console;verbosity=detailed"`místo použití .</span><span class="sxs-lookup"><span data-stu-id="2a33a-137">Unlike MSBuild, dotnet test doesn't accept abbreviations: instead of `-l "console;v=d"` use `-l "console;verbosity=detailed"`.</span></span>

- **`--no-build`**

  <span data-ttu-id="2a33a-138">Nesestaví testovací projekt před jeho spuštěním.</span><span class="sxs-lookup"><span data-stu-id="2a33a-138">Doesn't build the test project before running it.</span></span> <span data-ttu-id="2a33a-139">Také implicitně nastaví `--no-restore` - příznak.</span><span class="sxs-lookup"><span data-stu-id="2a33a-139">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="2a33a-140">Spusťte testy bez zobrazení hlavičky Microsoft TestPlatform.</span><span class="sxs-lookup"><span data-stu-id="2a33a-140">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="2a33a-141">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="2a33a-141">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="2a33a-142">Nespustí implicitní obnovení při spuštění příkazu.</span><span class="sxs-lookup"><span data-stu-id="2a33a-142">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="2a33a-143">Adresář, ve kterém chcete najít binární soubory ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="2a33a-143">Directory in which to find the binaries to run.</span></span>

- **`-r|--results-directory <PATH>`**

  <span data-ttu-id="2a33a-144">Adresář, kde budou umístěny výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="2a33a-144">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="2a33a-145">Pokud zadaný adresář neexistuje, je vytvořen.</span><span class="sxs-lookup"><span data-stu-id="2a33a-145">If the specified directory doesn't exist, it's created.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="2a33a-146">Cílový runtime, pro který chcete testovat.</span><span class="sxs-lookup"><span data-stu-id="2a33a-146">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="2a33a-147">Soubor, `.runsettings` který chcete použít pro spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="2a33a-147">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="2a33a-148">Nakonfigurujte `.runsettings` testy částí pomocí souboru.</span><span class="sxs-lookup"><span data-stu-id="2a33a-148">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

- **`-t|--list-tests`**

  <span data-ttu-id="2a33a-149">Seznam všech zjištěných testů v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="2a33a-149">List all of the discovered tests in the current project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="2a33a-150">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="2a33a-150">Sets the verbosity level of the command.</span></span> <span data-ttu-id="2a33a-151">Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a .</span><span class="sxs-lookup"><span data-stu-id="2a33a-151">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="2a33a-152">Výchozí formát je `minimal`.</span><span class="sxs-lookup"><span data-stu-id="2a33a-152">The default is `minimal`.</span></span> <span data-ttu-id="2a33a-153">Další informace naleznete v tématu <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span><span class="sxs-lookup"><span data-stu-id="2a33a-153">For more information, see <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span></span>

- <span data-ttu-id="2a33a-154">`RunSettings`Argumenty</span><span class="sxs-lookup"><span data-stu-id="2a33a-154">`RunSettings` arguments</span></span>

  <span data-ttu-id="2a33a-155">Argumenty jsou `RunSettings` předány jako konfigurace pro test.</span><span class="sxs-lookup"><span data-stu-id="2a33a-155">Arguments are passed as `RunSettings` configurations for the test.</span></span> <span data-ttu-id="2a33a-156">Argumenty jsou `[name]=[value]` určeny jako páry po "-- " (všimněte si mezery po --).</span><span class="sxs-lookup"><span data-stu-id="2a33a-156">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="2a33a-157">Mezera se používá `[name]=[value]` k oddělení více párů.</span><span class="sxs-lookup"><span data-stu-id="2a33a-157">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="2a33a-158">Příklad: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="2a33a-158">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="2a33a-159">Další informace naleznete [v vstest.console.exe: Předávání RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="2a33a-159">For more information, see [vstest.console.exe: Passing RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="2a33a-160">Příklady</span><span class="sxs-lookup"><span data-stu-id="2a33a-160">Examples</span></span>

- <span data-ttu-id="2a33a-161">Spusťte testy v projektu v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="2a33a-161">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="2a33a-162">Spusťte testy `test1` v projektu:</span><span class="sxs-lookup"><span data-stu-id="2a33a-162">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="2a33a-163">Spusťte testy v projektu v aktuálním adresáři a vygenerujte soubor výsledků testu ve formátu trx:</span><span class="sxs-lookup"><span data-stu-id="2a33a-163">Run the tests in the project in the current directory, and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

- <span data-ttu-id="2a33a-164">Spusťte testy v projektu v aktuálním adresáři a protokolujte s podrobnou podrobností do konzoly:</span><span class="sxs-lookup"><span data-stu-id="2a33a-164">Run the tests in the project in the current directory, and log with detailed verbosity to the console:</span></span>

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```

## <a name="filter-option-details"></a><span data-ttu-id="2a33a-165">Podrobnosti o možnosti filtru</span><span class="sxs-lookup"><span data-stu-id="2a33a-165">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="2a33a-166">`<Expression>`má formát `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="2a33a-166">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="2a33a-167">`<property>`je atributem `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="2a33a-167">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="2a33a-168">Následují vlastnosti podporované populární rozhraní testování částí:</span><span class="sxs-lookup"><span data-stu-id="2a33a-168">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="2a33a-169">Testovací rámec</span><span class="sxs-lookup"><span data-stu-id="2a33a-169">Test Framework</span></span> | <span data-ttu-id="2a33a-170">Podporované vlastnosti</span><span class="sxs-lookup"><span data-stu-id="2a33a-170">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="2a33a-171">MSTest</span><span class="sxs-lookup"><span data-stu-id="2a33a-171">MSTest</span></span>         | <ul><li><span data-ttu-id="2a33a-172">Plně kvalifikovaný název</span><span class="sxs-lookup"><span data-stu-id="2a33a-172">FullyQualifiedName</span></span></li><li><span data-ttu-id="2a33a-173">Název</span><span class="sxs-lookup"><span data-stu-id="2a33a-173">Name</span></span></li><li><span data-ttu-id="2a33a-174">Classname</span><span class="sxs-lookup"><span data-stu-id="2a33a-174">ClassName</span></span></li><li><span data-ttu-id="2a33a-175">Priorita</span><span class="sxs-lookup"><span data-stu-id="2a33a-175">Priority</span></span></li><li><span data-ttu-id="2a33a-176">Kategorie testů</span><span class="sxs-lookup"><span data-stu-id="2a33a-176">TestCategory</span></span></li></ul> |
| <span data-ttu-id="2a33a-177">xJednotka</span><span class="sxs-lookup"><span data-stu-id="2a33a-177">xUnit</span></span>          | <ul><li><span data-ttu-id="2a33a-178">Plně kvalifikovaný název</span><span class="sxs-lookup"><span data-stu-id="2a33a-178">FullyQualifiedName</span></span></li><li><span data-ttu-id="2a33a-179">DisplayName</span><span class="sxs-lookup"><span data-stu-id="2a33a-179">DisplayName</span></span></li><li><span data-ttu-id="2a33a-180">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="2a33a-180">Traits</span></span></li></ul>                                   |

<span data-ttu-id="2a33a-181">Popisuje `<operator>` vztah mezi vlastností a hodnotou:</span><span class="sxs-lookup"><span data-stu-id="2a33a-181">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="2a33a-182">Operátor</span><span class="sxs-lookup"><span data-stu-id="2a33a-182">Operator</span></span> | <span data-ttu-id="2a33a-183">Funkce</span><span class="sxs-lookup"><span data-stu-id="2a33a-183">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="2a33a-184">Přesná shoda</span><span class="sxs-lookup"><span data-stu-id="2a33a-184">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="2a33a-185">Není přesná shoda</span><span class="sxs-lookup"><span data-stu-id="2a33a-185">Not exact match</span></span> |
| `~`      | <span data-ttu-id="2a33a-186">Contains</span><span class="sxs-lookup"><span data-stu-id="2a33a-186">Contains</span></span>        |
| `!~`     | <span data-ttu-id="2a33a-187">Neobsahuje</span><span class="sxs-lookup"><span data-stu-id="2a33a-187">Not contains</span></span>    |

<span data-ttu-id="2a33a-188">`<value>`je řetězec.</span><span class="sxs-lookup"><span data-stu-id="2a33a-188">`<value>` is a string.</span></span> <span data-ttu-id="2a33a-189">Všechna vyhledávání jsou malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="2a33a-189">All the lookups are case insensitive.</span></span>

<span data-ttu-id="2a33a-190">Výraz bez `<operator>` je automaticky považován `contains` `FullyQualifiedName` za vlastnost on `dotnet test --filter xyz` (například je stejný jako `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="2a33a-190">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="2a33a-191">Výrazy lze spojit s podmíněnými operátory:</span><span class="sxs-lookup"><span data-stu-id="2a33a-191">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="2a33a-192">Operátor</span><span class="sxs-lookup"><span data-stu-id="2a33a-192">Operator</span></span>            | <span data-ttu-id="2a33a-193">Funkce</span><span class="sxs-lookup"><span data-stu-id="2a33a-193">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="2a33a-194">NEBO</span><span class="sxs-lookup"><span data-stu-id="2a33a-194">OR</span></span>       |
| `&`                 | <span data-ttu-id="2a33a-195">AND</span><span class="sxs-lookup"><span data-stu-id="2a33a-195">AND</span></span>      |

<span data-ttu-id="2a33a-196">Výrazy můžete uzavřít do závorek při použití podmíněných operátorů `(Name~TestMethod1) | (Name~TestMethod2)`(například).</span><span class="sxs-lookup"><span data-stu-id="2a33a-196">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="2a33a-197">Další informace a příklady použití filtrace testů selektivních testů částí naleznete v [tématu Spuštění testů selektivních částí](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="2a33a-197">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2a33a-198">Viz také</span><span class="sxs-lookup"><span data-stu-id="2a33a-198">See also</span></span>

- [<span data-ttu-id="2a33a-199">Rámce a cíle</span><span class="sxs-lookup"><span data-stu-id="2a33a-199">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="2a33a-200">Katalog IDentifier (RID) modulu .NET Core Runtime</span><span class="sxs-lookup"><span data-stu-id="2a33a-200">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="2a33a-201">Předávání argumentů runsettings prostřednictvím příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="2a33a-201">Passing runsettings arguments through commandline</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
