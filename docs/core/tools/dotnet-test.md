---
title: dotnet – příkaz testu
description: Příkaz dotnet test se používá ke spouštění testů jednotek v daném projektu.
ms.date: 02/27/2020
ms.openlocfilehash: 6e906ab396a788905c99f50e73390b765b240efc
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157008"
---
# <a name="dotnet-test"></a><span data-ttu-id="120fd-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="120fd-103">dotnet test</span></span>

<span data-ttu-id="120fd-104">**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="120fd-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="120fd-105">Název</span><span class="sxs-lookup"><span data-stu-id="120fd-105">Name</span></span>

<span data-ttu-id="120fd-106">ovladač testu `dotnet test`-.NET použitý ke spuštění testů jednotek</span><span class="sxs-lookup"><span data-stu-id="120fd-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="120fd-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="120fd-107">Synopsis</span></span>

```dotnetcli
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame]
    [-c|--configuration] [--collect] [-d|--diag] [-f|--framework]
    [--filter] [-l|--logger] [--no-build] [--no-restore]
    [-o|--output] [-r|--results-directory] [-s|--settings]
    [-t|--list-tests] [-v|--verbosity] [-- <RunSettings arguments>]

dotnet test [-h|--help]
```

## <a name="description"></a><span data-ttu-id="120fd-108">Popis</span><span class="sxs-lookup"><span data-stu-id="120fd-108">Description</span></span>

<span data-ttu-id="120fd-109">Příkaz `dotnet test` slouží ke spuštění testů jednotek v daném projektu.</span><span class="sxs-lookup"><span data-stu-id="120fd-109">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="120fd-110">Příkaz `dotnet test` spustí konzolovou aplikaci Test Runner určenou pro projekt.</span><span class="sxs-lookup"><span data-stu-id="120fd-110">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="120fd-111">Test Runner spustí testy definované pro systém testů jednotek (například MSTest, NUnit nebo xUnit) a ohlásí úspěch nebo neúspěch každého testu.</span><span class="sxs-lookup"><span data-stu-id="120fd-111">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="120fd-112">Pokud jsou všechny testy úspěšné, Test Runner vrátí 0 jako ukončovací kód; jinak, pokud nějaký test selže, vrátí 1.</span><span class="sxs-lookup"><span data-stu-id="120fd-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="120fd-113">Test Runner a knihovna testů jednotek jsou zabaleny jako balíčky NuGet a jsou obnoveny jako běžné závislosti pro projekt.</span><span class="sxs-lookup"><span data-stu-id="120fd-113">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="120fd-114">Projekty testů určují Test Runner pomocí obyčejného prvku `<PackageReference>`, jak je vidět v následujícím ukázkovém souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="120fd-114">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="120fd-115">Argumenty</span><span class="sxs-lookup"><span data-stu-id="120fd-115">Arguments</span></span>

- **`PROJECT`**

  <span data-ttu-id="120fd-116">Cesta k testovacímu projektu.</span><span class="sxs-lookup"><span data-stu-id="120fd-116">Path to the test project.</span></span> <span data-ttu-id="120fd-117">Pokud není zadaný, použije se ve výchozím nastavení aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="120fd-117">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="120fd-118">Možnosti</span><span class="sxs-lookup"><span data-stu-id="120fd-118">Options</span></span>

- **`a|--test-adapter-path <PATH_TO_ADAPTER>`**

  <span data-ttu-id="120fd-119">Použijte vlastní testovací adaptéry ze zadané cesty v testovacím běhu.</span><span class="sxs-lookup"><span data-stu-id="120fd-119">Use the custom test adapters from the specified path in the test run.</span></span>

- **`-blame`**

  <span data-ttu-id="120fd-120">Spustí testy v režimu viny.</span><span class="sxs-lookup"><span data-stu-id="120fd-120">Runs the tests in blame mode.</span></span> <span data-ttu-id="120fd-121">Tato možnost je užitečná při izolaci problematických testů, které způsobují selhání hostitele testu.</span><span class="sxs-lookup"><span data-stu-id="120fd-121">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="120fd-122">Vytvoří výstupní soubor v aktuálním adresáři jako *Sequence. XML* , který zachycuje pořadí spuštění testů před selháním.</span><span class="sxs-lookup"><span data-stu-id="120fd-122">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`c|--configuration {Debug|Release}`**

  <span data-ttu-id="120fd-123">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="120fd-123">Defines the build configuration.</span></span> <span data-ttu-id="120fd-124">Výchozí hodnota je `Debug`, ale konfigurace vašeho projektu může přepsat toto výchozí nastavení sady SDK.</span><span class="sxs-lookup"><span data-stu-id="120fd-124">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`-collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  <span data-ttu-id="120fd-125">Povolí shromažďování dat pro testovací běh.</span><span class="sxs-lookup"><span data-stu-id="120fd-125">Enables data collector for the test run.</span></span> <span data-ttu-id="120fd-126">Další informace najdete v tématu [monitorování a analýza testovacího běhu](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="120fd-126">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

- **`d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  <span data-ttu-id="120fd-127">Povolí diagnostický režim pro testovací platformu a zapíše diagnostické zprávy do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="120fd-127">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

- **`f|--framework <FRAMEWORK>`**

  <span data-ttu-id="120fd-128">Vyhledá testovací binární soubory pro konkrétní [rozhraní](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="120fd-128">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="120fd-129">Odfiltruje testy v aktuálním projektu pomocí daného výrazu.</span><span class="sxs-lookup"><span data-stu-id="120fd-129">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="120fd-130">Další informace najdete v části [Podrobnosti o možnosti filtru](#filter-option-details) .</span><span class="sxs-lookup"><span data-stu-id="120fd-130">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="120fd-131">Další informace a příklady použití selektivního filtrování testů jednotek naleznete v tématu [spuštění selektivních testů jednotek](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="120fd-131">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`h|--help`**

  <span data-ttu-id="120fd-132">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="120fd-132">Prints out a short help for the command.</span></span>

- **`l|--logger <LoggerUri/FriendlyName>`**

  <span data-ttu-id="120fd-133">Určuje protokolovací nástroj pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="120fd-133">Specifies a logger for test results.</span></span>

- **`--no-build`**

  <span data-ttu-id="120fd-134">Před spuštěním nevytvoří testovací projekt.</span><span class="sxs-lookup"><span data-stu-id="120fd-134">Doesn't build the test project before running it.</span></span> <span data-ttu-id="120fd-135">Také implicitně nastaví příznak-`--no-restore`.</span><span class="sxs-lookup"><span data-stu-id="120fd-135">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--no-restore`**

  <span data-ttu-id="120fd-136">Při spuštění příkazu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="120fd-136">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="120fd-137">Adresář, ve kterém se mají najít binární soubory, které se mají spustit.</span><span class="sxs-lookup"><span data-stu-id="120fd-137">Directory in which to find the binaries to run.</span></span>

- **`-r|--results-directory <PATH>`**

  <span data-ttu-id="120fd-138">Adresář, do kterého budou umístěny výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="120fd-138">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="120fd-139">Pokud zadaný adresář neexistuje, vytvoří se.</span><span class="sxs-lookup"><span data-stu-id="120fd-139">If the specified directory doesn't exist, it's created.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="120fd-140">Soubor `.runsettings`, který se má použít pro spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="120fd-140">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="120fd-141">Nakonfigurujte testy jednotek pomocí `.runsettings` souboru.</span><span class="sxs-lookup"><span data-stu-id="120fd-141">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

- **`-t|--list-tests`**

  <span data-ttu-id="120fd-142">Vypíše všechny zjištěné testy v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="120fd-142">List all of the discovered tests in the current project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="120fd-143">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="120fd-143">Sets the verbosity level of the command.</span></span> <span data-ttu-id="120fd-144">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="120fd-144">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- <span data-ttu-id="120fd-145">argumenty `RunSettings`</span><span class="sxs-lookup"><span data-stu-id="120fd-145">`RunSettings` arguments</span></span>

  <span data-ttu-id="120fd-146">Argumenty jsou předány jako `RunSettings` konfigurace testu.</span><span class="sxs-lookup"><span data-stu-id="120fd-146">Arguments are passed as `RunSettings` configurations for the test.</span></span> <span data-ttu-id="120fd-147">Argumenty jsou zadány jako páry `[name]=[value]` po "--" (Všimněte si mezer za-).</span><span class="sxs-lookup"><span data-stu-id="120fd-147">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="120fd-148">K oddělení více párů `[name]=[value]` se používá mezera.</span><span class="sxs-lookup"><span data-stu-id="120fd-148">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="120fd-149">Příklad: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="120fd-149">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="120fd-150">Další informace naleznete v tématu [VSTest. Console. exe: předávání argumentů runsettings](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="120fd-150">For more information, see [vstest.console.exe: Passing RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="120fd-151">Příklady</span><span class="sxs-lookup"><span data-stu-id="120fd-151">Examples</span></span>

- <span data-ttu-id="120fd-152">Spustit testy v projektu v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="120fd-152">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="120fd-153">Spusťte testy v projektu `test1`:</span><span class="sxs-lookup"><span data-stu-id="120fd-153">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="120fd-154">Spusťte testy v projektu v aktuálním adresáři a vygenerujte soubor výsledků testů ve formátu TRX:</span><span class="sxs-lookup"><span data-stu-id="120fd-154">Run the tests in the project in the current directory and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

## <a name="filter-option-details"></a><span data-ttu-id="120fd-155">Podrobnosti možnosti filtru</span><span class="sxs-lookup"><span data-stu-id="120fd-155">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="120fd-156">`<Expression>` má `<property><operator><value>[|&<Expression>]`formátu.</span><span class="sxs-lookup"><span data-stu-id="120fd-156">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="120fd-157">`<property>` je atribut `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="120fd-157">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="120fd-158">Níže jsou uvedené vlastnosti podporované oblíbenými rozhraními pro testování částí:</span><span class="sxs-lookup"><span data-stu-id="120fd-158">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="120fd-159">Rozhraní pro testování</span><span class="sxs-lookup"><span data-stu-id="120fd-159">Test Framework</span></span> | <span data-ttu-id="120fd-160">Podporované vlastnosti</span><span class="sxs-lookup"><span data-stu-id="120fd-160">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="120fd-161">MSTest</span><span class="sxs-lookup"><span data-stu-id="120fd-161">MSTest</span></span>         | <ul><li><span data-ttu-id="120fd-162">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="120fd-162">FullyQualifiedName</span></span></li><li><span data-ttu-id="120fd-163">Název</span><span class="sxs-lookup"><span data-stu-id="120fd-163">Name</span></span></li><li><span data-ttu-id="120fd-164">NázevTřídy</span><span class="sxs-lookup"><span data-stu-id="120fd-164">ClassName</span></span></li><li><span data-ttu-id="120fd-165">Priorita</span><span class="sxs-lookup"><span data-stu-id="120fd-165">Priority</span></span></li><li><span data-ttu-id="120fd-166">TestCategory</span><span class="sxs-lookup"><span data-stu-id="120fd-166">TestCategory</span></span></li></ul> |
| <span data-ttu-id="120fd-167">xUnit</span><span class="sxs-lookup"><span data-stu-id="120fd-167">xUnit</span></span>          | <ul><li><span data-ttu-id="120fd-168">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="120fd-168">FullyQualifiedName</span></span></li><li><span data-ttu-id="120fd-169">DisplayName</span><span class="sxs-lookup"><span data-stu-id="120fd-169">DisplayName</span></span></li><li><span data-ttu-id="120fd-170">Traits</span><span class="sxs-lookup"><span data-stu-id="120fd-170">Traits</span></span></li></ul>                                   |

<span data-ttu-id="120fd-171">`<operator>` popisuje vztah mezi vlastností a hodnotou:</span><span class="sxs-lookup"><span data-stu-id="120fd-171">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="120fd-172">Operátor</span><span class="sxs-lookup"><span data-stu-id="120fd-172">Operator</span></span> | <span data-ttu-id="120fd-173">Funkce</span><span class="sxs-lookup"><span data-stu-id="120fd-173">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="120fd-174">Přesná shoda</span><span class="sxs-lookup"><span data-stu-id="120fd-174">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="120fd-175">Nepřesná shoda</span><span class="sxs-lookup"><span data-stu-id="120fd-175">Not exact match</span></span> |
| `~`      | <span data-ttu-id="120fd-176">Contains</span><span class="sxs-lookup"><span data-stu-id="120fd-176">Contains</span></span>        |
| `!~`     | <span data-ttu-id="120fd-177">Neobsahuje</span><span class="sxs-lookup"><span data-stu-id="120fd-177">Not contains</span></span>    |

<span data-ttu-id="120fd-178">`<value>` je řetězec.</span><span class="sxs-lookup"><span data-stu-id="120fd-178">`<value>` is a string.</span></span> <span data-ttu-id="120fd-179">U všech hledání se nerozlišují malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="120fd-179">All the lookups are case insensitive.</span></span>

<span data-ttu-id="120fd-180">Výraz bez `<operator>` je automaticky považován za `contains` při `FullyQualifiedName` vlastnosti (například `dotnet test --filter xyz` je stejný jako `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="120fd-180">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="120fd-181">Výrazy se dají spojit s podmíněnými operátory:</span><span class="sxs-lookup"><span data-stu-id="120fd-181">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="120fd-182">Operátor</span><span class="sxs-lookup"><span data-stu-id="120fd-182">Operator</span></span>            | <span data-ttu-id="120fd-183">Funkce</span><span class="sxs-lookup"><span data-stu-id="120fd-183">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="120fd-184">NEBO</span><span class="sxs-lookup"><span data-stu-id="120fd-184">OR</span></span>       |
| `&`                 | <span data-ttu-id="120fd-185">A</span><span class="sxs-lookup"><span data-stu-id="120fd-185">AND</span></span>      |

<span data-ttu-id="120fd-186">Výrazy můžete uzavřít do závorek při použití podmíněných operátorů (například `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="120fd-186">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="120fd-187">Další informace a příklady použití selektivního filtrování testů jednotek naleznete v tématu [spuštění selektivních testů jednotek](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="120fd-187">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="120fd-188">Viz také</span><span class="sxs-lookup"><span data-stu-id="120fd-188">See also</span></span>

- [<span data-ttu-id="120fd-189">Architektury a cíle</span><span class="sxs-lookup"><span data-stu-id="120fd-189">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="120fd-190">Katalog identifikátorů runtime .NET Core (RID)</span><span class="sxs-lookup"><span data-stu-id="120fd-190">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
