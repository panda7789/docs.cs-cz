---
title: dotnet test, příkaz
description: Dotnet test příkaz se používá k provedení testů částí v daném projektu.
ms.date: 02/27/2020
ms.openlocfilehash: a11814f9fdc6326e681a09d7d2654b968014f318
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507305"
---
# <a name="dotnet-test"></a><span data-ttu-id="1b429-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="1b429-103">dotnet test</span></span>

<span data-ttu-id="1b429-104">**Tento článek se týká:** ✔️ .NET Core 2.1 SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="1b429-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="1b429-105">Name (Název)</span><span class="sxs-lookup"><span data-stu-id="1b429-105">Name</span></span>

<span data-ttu-id="1b429-106">`dotnet test`- Testovací ovladač .NET používaný ke spuštění testů částí.</span><span class="sxs-lookup"><span data-stu-id="1b429-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="1b429-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="1b429-107">Synopsis</span></span>

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION>]
    [-a|--test-adapter-path] [--blame] [-c|--configuration]
    [--collect] [-d|--diag] [-f|--framework] [--filter]
    [--interactive] [-l|--logger] [--no-build] [--nologo]
    [--no-restore] [-o|--output] [-r|--results-directory]
    [--runtime] [-s|--settings] [-t|--list-tests]
    [-v|--verbosity] [[--] <RunSettings arguments>]

dotnet test [-h|--help]
```

## <a name="description"></a><span data-ttu-id="1b429-108">Popis</span><span class="sxs-lookup"><span data-stu-id="1b429-108">Description</span></span>

<span data-ttu-id="1b429-109">Příkaz `dotnet test` se používá ke spuštění testů částí v daném projektu.</span><span class="sxs-lookup"><span data-stu-id="1b429-109">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="1b429-110">Příkaz `dotnet test` spustí aplikace konzoly pro spuštění testu určená pro projekt.</span><span class="sxs-lookup"><span data-stu-id="1b429-110">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="1b429-111">Testovací běžec provede testy definované pro rozhraní testování částí (například MSTest, NUnit nebo xUnit) a hlásí úspěch nebo neúspěch každého testu.</span><span class="sxs-lookup"><span data-stu-id="1b429-111">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="1b429-112">Pokud jsou všechny testy úspěšné, testovací běžec vrátí 0 jako ukončovací kód; v opačném případě, pokud některý test selže, vrátí 1.</span><span class="sxs-lookup"><span data-stu-id="1b429-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="1b429-113">Testovací běžec a knihovna testování částí jsou zabaleny jako balíčky NuGet a jsou obnoveny jako běžné závislosti pro projekt.</span><span class="sxs-lookup"><span data-stu-id="1b429-113">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="1b429-114">Testovací projekty určují testovací `<PackageReference>` běh pomocí běžného prvku, jak je vidět v následujícím ukázkovém souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="1b429-114">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="1b429-115">Argumenty</span><span class="sxs-lookup"><span data-stu-id="1b429-115">Arguments</span></span>

- **`PROJECT | SOLUTION`**

  <span data-ttu-id="1b429-116">Cesta k testovacímu projektu nebo řešení.</span><span class="sxs-lookup"><span data-stu-id="1b429-116">Path to the test project or solution.</span></span> <span data-ttu-id="1b429-117">Pokud není zadán, je výchozí aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="1b429-117">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="1b429-118">Možnosti</span><span class="sxs-lookup"><span data-stu-id="1b429-118">Options</span></span>

- **`a|--test-adapter-path <PATH_TO_ADAPTER>`**

  <span data-ttu-id="1b429-119">Použijte vlastní testovací adaptéry ze zadané cesty v testovacím běhu.</span><span class="sxs-lookup"><span data-stu-id="1b429-119">Use the custom test adapters from the specified path in the test run.</span></span>

- **`--blame`**

  <span data-ttu-id="1b429-120">Spustí testy v režimu obviňování.</span><span class="sxs-lookup"><span data-stu-id="1b429-120">Runs the tests in blame mode.</span></span> <span data-ttu-id="1b429-121">Tato možnost je užitečná při izolování problémových testů, které způsobují selhání testovacího hostitele.</span><span class="sxs-lookup"><span data-stu-id="1b429-121">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="1b429-122">Vytvoří výstupní soubor v aktuálním adresáři jako *Sequence.xml,* který zachycuje pořadí spuštění testů před selháním.</span><span class="sxs-lookup"><span data-stu-id="1b429-122">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="1b429-123">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="1b429-123">Defines the build configuration.</span></span> <span data-ttu-id="1b429-124">Výchozí hodnota `Debug`je , ale konfigurace projektu může přepsat toto výchozí nastavení sady SDK.</span><span class="sxs-lookup"><span data-stu-id="1b429-124">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`-collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  <span data-ttu-id="1b429-125">Povolí sběr dat pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="1b429-125">Enables data collector for the test run.</span></span> <span data-ttu-id="1b429-126">Další informace naleznete v [tématu Sledování a analýza testovacího běhu](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="1b429-126">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

- **`d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  <span data-ttu-id="1b429-127">Povolí diagnostický režim pro testovací platformu a zapisuje diagnostické zprávy do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="1b429-127">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

- **`f|--framework <FRAMEWORK>`**

  <span data-ttu-id="1b429-128">Vyhledá testovací binární soubory pro konkrétní [rámec](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="1b429-128">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="1b429-129">Odfiltruje testy v aktuálním projektu pomocí daného výrazu.</span><span class="sxs-lookup"><span data-stu-id="1b429-129">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="1b429-130">Další informace naleznete v části [Podrobnosti o možnosti filtr.](#filter-option-details)</span><span class="sxs-lookup"><span data-stu-id="1b429-130">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="1b429-131">Další informace a příklady použití filtrace testů selektivních testů částí naleznete v [tématu Spuštění testů selektivních částí](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="1b429-131">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`h|--help`**

  <span data-ttu-id="1b429-132">Vytiskne krátkou nápovědu pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="1b429-132">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="1b429-133">Umožňuje příkazu zastavit a čekat na vstup uživatele nebo akci.</span><span class="sxs-lookup"><span data-stu-id="1b429-133">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="1b429-134">Například k dokončení ověřování.</span><span class="sxs-lookup"><span data-stu-id="1b429-134">For example, to complete authentication.</span></span> <span data-ttu-id="1b429-135">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="1b429-135">Available since .NET Core 3.0 SDK.</span></span>

- **`l|--logger <LoggerUri/FriendlyName>`**

  <span data-ttu-id="1b429-136">Určuje protokolovací nástroj pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="1b429-136">Specifies a logger for test results.</span></span>

- **`--no-build`**

  <span data-ttu-id="1b429-137">Nesestaví testovací projekt před jeho spuštěním.</span><span class="sxs-lookup"><span data-stu-id="1b429-137">Doesn't build the test project before running it.</span></span> <span data-ttu-id="1b429-138">Také implicitně nastaví `--no-restore` - příznak.</span><span class="sxs-lookup"><span data-stu-id="1b429-138">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="1b429-139">Spusťte testy bez zobrazení hlavičky Microsoft TestPlatform.</span><span class="sxs-lookup"><span data-stu-id="1b429-139">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="1b429-140">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="1b429-140">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="1b429-141">Nespustí implicitní obnovení při spuštění příkazu.</span><span class="sxs-lookup"><span data-stu-id="1b429-141">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="1b429-142">Adresář, ve kterém chcete najít binární soubory ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="1b429-142">Directory in which to find the binaries to run.</span></span>

- **`-r|--results-directory <PATH>`**

  <span data-ttu-id="1b429-143">Adresář, kde budou umístěny výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="1b429-143">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="1b429-144">Pokud zadaný adresář neexistuje, je vytvořen.</span><span class="sxs-lookup"><span data-stu-id="1b429-144">If the specified directory doesn't exist, it's created.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="1b429-145">Cílový runtime, pro který chcete testovat.</span><span class="sxs-lookup"><span data-stu-id="1b429-145">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="1b429-146">Soubor, `.runsettings` který chcete použít pro spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="1b429-146">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="1b429-147">Nakonfigurujte `.runsettings` testy částí pomocí souboru.</span><span class="sxs-lookup"><span data-stu-id="1b429-147">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

- **`-t|--list-tests`**

  <span data-ttu-id="1b429-148">Seznam všech zjištěných testů v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="1b429-148">List all of the discovered tests in the current project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="1b429-149">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="1b429-149">Sets the verbosity level of the command.</span></span> <span data-ttu-id="1b429-150">Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a .</span><span class="sxs-lookup"><span data-stu-id="1b429-150">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- <span data-ttu-id="1b429-151">`RunSettings`Argumenty</span><span class="sxs-lookup"><span data-stu-id="1b429-151">`RunSettings` arguments</span></span>

  <span data-ttu-id="1b429-152">Argumenty jsou `RunSettings` předány jako konfigurace pro test.</span><span class="sxs-lookup"><span data-stu-id="1b429-152">Arguments are passed as `RunSettings` configurations for the test.</span></span> <span data-ttu-id="1b429-153">Argumenty jsou `[name]=[value]` určeny jako páry po "-- " (všimněte si mezery po --).</span><span class="sxs-lookup"><span data-stu-id="1b429-153">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="1b429-154">Mezera se používá `[name]=[value]` k oddělení více párů.</span><span class="sxs-lookup"><span data-stu-id="1b429-154">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="1b429-155">Příklad: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="1b429-155">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="1b429-156">Další informace naleznete [v vstest.console.exe: Předávání RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="1b429-156">For more information, see [vstest.console.exe: Passing RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="1b429-157">Příklady</span><span class="sxs-lookup"><span data-stu-id="1b429-157">Examples</span></span>

- <span data-ttu-id="1b429-158">Spusťte testy v projektu v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="1b429-158">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="1b429-159">Spusťte testy `test1` v projektu:</span><span class="sxs-lookup"><span data-stu-id="1b429-159">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="1b429-160">Spusťte testy v projektu v aktuálním adresáři a vygenerujte soubor výsledků testů ve formátu trx:</span><span class="sxs-lookup"><span data-stu-id="1b429-160">Run the tests in the project in the current directory and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

## <a name="filter-option-details"></a><span data-ttu-id="1b429-161">Podrobnosti o možnosti filtru</span><span class="sxs-lookup"><span data-stu-id="1b429-161">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="1b429-162">`<Expression>`má formát `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="1b429-162">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="1b429-163">`<property>`je atributem `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="1b429-163">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="1b429-164">Následují vlastnosti podporované populární rozhraní testování částí:</span><span class="sxs-lookup"><span data-stu-id="1b429-164">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="1b429-165">Testovací rámec</span><span class="sxs-lookup"><span data-stu-id="1b429-165">Test Framework</span></span> | <span data-ttu-id="1b429-166">Podporované vlastnosti</span><span class="sxs-lookup"><span data-stu-id="1b429-166">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="1b429-167">MSTest</span><span class="sxs-lookup"><span data-stu-id="1b429-167">MSTest</span></span>         | <ul><li><span data-ttu-id="1b429-168">Plně kvalifikovaný název</span><span class="sxs-lookup"><span data-stu-id="1b429-168">FullyQualifiedName</span></span></li><li><span data-ttu-id="1b429-169">Name (Název)</span><span class="sxs-lookup"><span data-stu-id="1b429-169">Name</span></span></li><li><span data-ttu-id="1b429-170">Classname</span><span class="sxs-lookup"><span data-stu-id="1b429-170">ClassName</span></span></li><li><span data-ttu-id="1b429-171">Priorita</span><span class="sxs-lookup"><span data-stu-id="1b429-171">Priority</span></span></li><li><span data-ttu-id="1b429-172">Kategorie testů</span><span class="sxs-lookup"><span data-stu-id="1b429-172">TestCategory</span></span></li></ul> |
| <span data-ttu-id="1b429-173">xJednotka</span><span class="sxs-lookup"><span data-stu-id="1b429-173">xUnit</span></span>          | <ul><li><span data-ttu-id="1b429-174">Plně kvalifikovaný název</span><span class="sxs-lookup"><span data-stu-id="1b429-174">FullyQualifiedName</span></span></li><li><span data-ttu-id="1b429-175">DisplayName</span><span class="sxs-lookup"><span data-stu-id="1b429-175">DisplayName</span></span></li><li><span data-ttu-id="1b429-176">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="1b429-176">Traits</span></span></li></ul>                                   |

<span data-ttu-id="1b429-177">Popisuje `<operator>` vztah mezi vlastností a hodnotou:</span><span class="sxs-lookup"><span data-stu-id="1b429-177">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="1b429-178">Operátor</span><span class="sxs-lookup"><span data-stu-id="1b429-178">Operator</span></span> | <span data-ttu-id="1b429-179">Funkce</span><span class="sxs-lookup"><span data-stu-id="1b429-179">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="1b429-180">Přesná shoda</span><span class="sxs-lookup"><span data-stu-id="1b429-180">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="1b429-181">Není přesná shoda</span><span class="sxs-lookup"><span data-stu-id="1b429-181">Not exact match</span></span> |
| `~`      | <span data-ttu-id="1b429-182">Contains</span><span class="sxs-lookup"><span data-stu-id="1b429-182">Contains</span></span>        |
| `!~`     | <span data-ttu-id="1b429-183">Neobsahuje</span><span class="sxs-lookup"><span data-stu-id="1b429-183">Not contains</span></span>    |

<span data-ttu-id="1b429-184">`<value>`je řetězec.</span><span class="sxs-lookup"><span data-stu-id="1b429-184">`<value>` is a string.</span></span> <span data-ttu-id="1b429-185">Všechna vyhledávání jsou malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="1b429-185">All the lookups are case insensitive.</span></span>

<span data-ttu-id="1b429-186">Výraz bez `<operator>` je automaticky považován `contains` `FullyQualifiedName` za vlastnost on `dotnet test --filter xyz` (například je stejný jako `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="1b429-186">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="1b429-187">Výrazy lze spojit s podmíněnými operátory:</span><span class="sxs-lookup"><span data-stu-id="1b429-187">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="1b429-188">Operátor</span><span class="sxs-lookup"><span data-stu-id="1b429-188">Operator</span></span>            | <span data-ttu-id="1b429-189">Funkce</span><span class="sxs-lookup"><span data-stu-id="1b429-189">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="1b429-190">NEBO</span><span class="sxs-lookup"><span data-stu-id="1b429-190">OR</span></span>       |
| `&`                 | <span data-ttu-id="1b429-191">AND</span><span class="sxs-lookup"><span data-stu-id="1b429-191">AND</span></span>      |

<span data-ttu-id="1b429-192">Výrazy můžete uzavřít do závorek při použití podmíněných operátorů `(Name~TestMethod1) | (Name~TestMethod2)`(například).</span><span class="sxs-lookup"><span data-stu-id="1b429-192">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="1b429-193">Další informace a příklady použití filtrace testů selektivních testů částí naleznete v [tématu Spuštění testů selektivních částí](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="1b429-193">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1b429-194">Viz také</span><span class="sxs-lookup"><span data-stu-id="1b429-194">See also</span></span>

- [<span data-ttu-id="1b429-195">Rámce a cíle</span><span class="sxs-lookup"><span data-stu-id="1b429-195">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="1b429-196">Katalog IDentifier (RID) modulu .NET Core Runtime</span><span class="sxs-lookup"><span data-stu-id="1b429-196">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
