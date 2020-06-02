---
title: dotnet – příkaz testu
description: Příkaz dotnet test se používá ke spouštění testů jednotek v daném projektu.
ms.date: 04/29/2020
ms.openlocfilehash: 1190ecb75e83c9930c60726e7cd83203b11928cb
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84283933"
---
# <a name="dotnet-test"></a><span data-ttu-id="29fa1-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="29fa1-103">dotnet test</span></span>

<span data-ttu-id="29fa1-104">**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="29fa1-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="29fa1-105">Name</span><span class="sxs-lookup"><span data-stu-id="29fa1-105">Name</span></span>

<span data-ttu-id="29fa1-106">`dotnet test`– Testovací ovladač .NET, který se používá ke spouštění testů jednotek.</span><span class="sxs-lookup"><span data-stu-id="29fa1-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="29fa1-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="29fa1-107">Synopsis</span></span>

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION> | <DIRECTORY> | <DLL>]
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

## <a name="description"></a><span data-ttu-id="29fa1-108">Popis</span><span class="sxs-lookup"><span data-stu-id="29fa1-108">Description</span></span>

<span data-ttu-id="29fa1-109">`dotnet test`Příkaz slouží ke spuštění testů jednotek v daném řešení.</span><span class="sxs-lookup"><span data-stu-id="29fa1-109">The `dotnet test` command is used to execute unit tests in a given solution.</span></span> <span data-ttu-id="29fa1-110">Příkaz sestaví `dotnet test` řešení a spustí testovací hostitelskou aplikaci pro každý projekt testů v řešení.</span><span class="sxs-lookup"><span data-stu-id="29fa1-110">The `dotnet test` command builds the solution and runs a test host application for each test project in the solution.</span></span> <span data-ttu-id="29fa1-111">Testovací hostitel provede v daném projektu testy pomocí testovacího rozhraní, například: MSTest, NUnit nebo xUnit, a ohlásí úspěch nebo neúspěch každého testu.</span><span class="sxs-lookup"><span data-stu-id="29fa1-111">The test host executes tests in the given project using a test framework, for example: MSTest, NUnit, or xUnit, and reports the success or failure of each test.</span></span> <span data-ttu-id="29fa1-112">Pokud jsou všechny testy úspěšné, Test Runner vrátí 0 jako ukončovací kód; jinak, pokud nějaký test selže, vrátí 1.</span><span class="sxs-lookup"><span data-stu-id="29fa1-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span>

<span data-ttu-id="29fa1-113">Pro projekty zaměřené na více platforem jsou testy spouštěny pro každou cílovou architekturu.</span><span class="sxs-lookup"><span data-stu-id="29fa1-113">For multi-targeted projects, tests are run for each targeted framework.</span></span> <span data-ttu-id="29fa1-114">Testovací hostitel a testovací rozhraní jednotky jsou zabaleny jako balíčky NuGet a jsou obnoveny jako běžné závislosti pro projekt.</span><span class="sxs-lookup"><span data-stu-id="29fa1-114">The test host and the unit test framework are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="29fa1-115">Projekty testů určují testovací spouštěč pomocí obyčejného `<PackageReference>` prvku, jak je vidět v následujícím ukázkovém souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="29fa1-115">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

<span data-ttu-id="29fa1-116">Kde `Microsoft.NET.Test.Sdk` je testovací hostitel, `xunit` je testovací rozhraní.</span><span class="sxs-lookup"><span data-stu-id="29fa1-116">Where `Microsoft.NET.Test.Sdk` is the test host, `xunit` is the test framework.</span></span> <span data-ttu-id="29fa1-117">A `xunit.runner.visualstudio` je testovací adaptér, který umožňuje, aby architektura xUnit spolupracovala s testovacím hostitelem.</span><span class="sxs-lookup"><span data-stu-id="29fa1-117">And `xunit.runner.visualstudio` is a test adapter, which allows the xUnit framework to work with the test host.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="29fa1-118">Implicitní obnovení</span><span class="sxs-lookup"><span data-stu-id="29fa1-118">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="29fa1-119">Arguments</span><span class="sxs-lookup"><span data-stu-id="29fa1-119">Arguments</span></span>

- **`PROJECT | SOLUTION | DIRECTORY | DLL`**

  - <span data-ttu-id="29fa1-120">Cesta k testovacímu projektu.</span><span class="sxs-lookup"><span data-stu-id="29fa1-120">Path to the test project.</span></span>
  - <span data-ttu-id="29fa1-121">Cesta k řešení</span><span class="sxs-lookup"><span data-stu-id="29fa1-121">Path to the solution.</span></span>
  - <span data-ttu-id="29fa1-122">Cesta k adresáři, který obsahuje projekt nebo řešení.</span><span class="sxs-lookup"><span data-stu-id="29fa1-122">Path to a directory that contains a project or a solution.</span></span>
  - <span data-ttu-id="29fa1-123">Cesta k souboru projektu testů *. dll* .</span><span class="sxs-lookup"><span data-stu-id="29fa1-123">Path to a test project *.dll* file.</span></span>

  <span data-ttu-id="29fa1-124">Pokud není zadán, vyhledá projekt nebo řešení v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="29fa1-124">If not specified, it searches for a project or a solution in the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="29fa1-125">Možnosti</span><span class="sxs-lookup"><span data-stu-id="29fa1-125">Options</span></span>

- **`-a|--test-adapter-path <PATH_TO_ADAPTER>`**

  <span data-ttu-id="29fa1-126">Cesta k adresáři, ve kterém se mají hledat další testovací adaptéry</span><span class="sxs-lookup"><span data-stu-id="29fa1-126">Path to a directory to be searched for additional test adapters.</span></span> <span data-ttu-id="29fa1-127">Jsou zkontrolovány pouze soubory *DLL* s příponou `.TestAdapter.dll` .</span><span class="sxs-lookup"><span data-stu-id="29fa1-127">Only *.dll* files with suffix `.TestAdapter.dll` are inspected.</span></span> <span data-ttu-id="29fa1-128">Pokud není zadán, bude prohledán adresář souboru Test *. dll* .</span><span class="sxs-lookup"><span data-stu-id="29fa1-128">If not specified, the directory of the test *.dll* is searched.</span></span>

- **`--blame`**

  <span data-ttu-id="29fa1-129">Spustí testy v režimu viny.</span><span class="sxs-lookup"><span data-stu-id="29fa1-129">Runs the tests in blame mode.</span></span> <span data-ttu-id="29fa1-130">Tato možnost je užitečná při izolaci problematických testů, které způsobují selhání hostitele testu.</span><span class="sxs-lookup"><span data-stu-id="29fa1-130">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="29fa1-131">Při zjištění chyby vytvoří soubor sekvence v `TestResults/<Guid>/<Guid>_Sequence.xml` , který zachytí pořadí testů, které byly spuštěny před selháním.</span><span class="sxs-lookup"><span data-stu-id="29fa1-131">When a crash is detected, it creates a sequence file in `TestResults/<Guid>/<Guid>_Sequence.xml` that captures the order of tests that were run before the crash.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="29fa1-132">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="29fa1-132">Defines the build configuration.</span></span> <span data-ttu-id="29fa1-133">Výchozí hodnota je `Debug` , ale konfigurace vašeho projektu může přepsat toto výchozí nastavení sady SDK.</span><span class="sxs-lookup"><span data-stu-id="29fa1-133">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  <span data-ttu-id="29fa1-134">Povolí shromažďování dat pro testovací běh.</span><span class="sxs-lookup"><span data-stu-id="29fa1-134">Enables data collector for the test run.</span></span> <span data-ttu-id="29fa1-135">Další informace najdete v tématu [monitorování a analýza testovacího běhu](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="29fa1-135">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>
  
  <span data-ttu-id="29fa1-136">Chcete-li shromáždit pokrytí kódu na jakékoli platformě, která je podporována rozhraním .NET Core, nainstalujte [Coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/README.md) a použijte `--collect:"XPlat Code Coverage"` možnost.</span><span class="sxs-lookup"><span data-stu-id="29fa1-136">To collect code coverage on any platform that is supported by .NET Core, install [Coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/README.md) and use the `--collect:"XPlat Code Coverage"` option.</span></span>

  <span data-ttu-id="29fa1-137">Ve Windows můžete pokrytí kódu shromažďovat pomocí `--collect "Code Coverage"` Možnosti.</span><span class="sxs-lookup"><span data-stu-id="29fa1-137">On Windows, you can collect code coverage by using the `--collect "Code Coverage"` option.</span></span> <span data-ttu-id="29fa1-138">Tato možnost vygeneruje soubor *. pokrytí* , který lze otevřít v aplikaci Visual Studio 2019 Enterprise.</span><span class="sxs-lookup"><span data-stu-id="29fa1-138">This option generates a *.coverage* file, which can be opened in Visual Studio 2019 Enterprise.</span></span> <span data-ttu-id="29fa1-139">Další informace najdete v tématu [Použití pokrytí kódu](/visualstudio/test/using-code-coverage-to-determine-how-much-code-is-being-tested) a [přizpůsobení analýzy pokrytí kódu](/visualstudio/test/customizing-code-coverage-analysis).</span><span class="sxs-lookup"><span data-stu-id="29fa1-139">For more information, see [Use code coverage](/visualstudio/test/using-code-coverage-to-determine-how-much-code-is-being-tested) and [Customize code coverage analysis](/visualstudio/test/customizing-code-coverage-analysis).</span></span>

- **`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  <span data-ttu-id="29fa1-140">Povolí diagnostický režim pro testovací platformu a zapisuje diagnostické zprávy do zadaného souboru a do souborů vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="29fa1-140">Enables diagnostic mode for the test platform and writes diagnostic messages to the specified file and to files next to it.</span></span> <span data-ttu-id="29fa1-141">Proces, který zaznamenává zprávy, určuje, které soubory jsou vytvořeny, například `*.host_<date>.txt` pro protokol testu hostitele a `*.datacollector_<date>.txt` protokol sběru dat.</span><span class="sxs-lookup"><span data-stu-id="29fa1-141">The process that is logging the messages determines which files are created, such as `*.host_<date>.txt` for test host log, and `*.datacollector_<date>.txt` for data collector log.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="29fa1-142">Vynutí použití `dotnet` nebo .NET Framework testovacího hostitele pro binární soubory testu.</span><span class="sxs-lookup"><span data-stu-id="29fa1-142">Forces the use of `dotnet` or .NET Framework test host for the test binaries.</span></span> <span data-ttu-id="29fa1-143">Tato možnost určuje pouze typ hostitele, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="29fa1-143">This option only determines which type of host to use.</span></span> <span data-ttu-id="29fa1-144">Skutečná verze rozhraní, která se má použít, se určuje pomocí *runtimeconfig. JSON* testovacího projektu.</span><span class="sxs-lookup"><span data-stu-id="29fa1-144">The actual framework version to be used is determined by the *runtimeconfig.json* of the test project.</span></span> <span data-ttu-id="29fa1-145">Pokud není zadaný, použije se k určení typu hostitele [atribut pro sestavení targetFramework](/dotnet/api/system.runtime.versioning.targetframeworkattribute) .</span><span class="sxs-lookup"><span data-stu-id="29fa1-145">When not specified, the [TargetFramework assembly attribute](/dotnet/api/system.runtime.versioning.targetframeworkattribute) is used to determine the type of host.</span></span> <span data-ttu-id="29fa1-146">Když je tento atribut ze souboru *. dll*odstraněn, je použit hostitel .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="29fa1-146">When that attribute is stripped from the *.dll*, the .NET Framework host is used.</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="29fa1-147">Odfiltruje testy v aktuálním projektu pomocí daného výrazu.</span><span class="sxs-lookup"><span data-stu-id="29fa1-147">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="29fa1-148">Další informace najdete v části [Podrobnosti o možnosti filtru](#filter-option-details) .</span><span class="sxs-lookup"><span data-stu-id="29fa1-148">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="29fa1-149">Další informace a příklady použití selektivního filtrování testů jednotek naleznete v tématu [spuštění selektivních testů jednotek](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="29fa1-149">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="29fa1-150">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="29fa1-150">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="29fa1-151">Umožňuje zastavení příkazu zastavit a počkat na vstup nebo akci uživatele.</span><span class="sxs-lookup"><span data-stu-id="29fa1-151">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="29fa1-152">Například k dokončení ověřování.</span><span class="sxs-lookup"><span data-stu-id="29fa1-152">For example, to complete authentication.</span></span> <span data-ttu-id="29fa1-153">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="29fa1-153">Available since .NET Core 3.0 SDK.</span></span>

- **`-l|--logger <LOGGER_URI/FRIENDLY_NAME>`**

  <span data-ttu-id="29fa1-154">Určuje protokolovací nástroj pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="29fa1-154">Specifies a logger for test results.</span></span> <span data-ttu-id="29fa1-155">Na rozdíl od MSBuild test dotnet nepřijímá zkratky: místo `-l "console;v=d"` použití `-l "console;verbosity=detailed"` .</span><span class="sxs-lookup"><span data-stu-id="29fa1-155">Unlike MSBuild, dotnet test doesn't accept abbreviations: instead of `-l "console;v=d"` use `-l "console;verbosity=detailed"`.</span></span>

- **`--no-build`**

  <span data-ttu-id="29fa1-156">Před spuštěním nevytvoří testovací projekt.</span><span class="sxs-lookup"><span data-stu-id="29fa1-156">Doesn't build the test project before running it.</span></span> <span data-ttu-id="29fa1-157">Také implicitně nastaví `--no-restore` příznak-.</span><span class="sxs-lookup"><span data-stu-id="29fa1-157">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="29fa1-158">Spusťte testy bez zobrazení banneru Microsoft TestPlatform.</span><span class="sxs-lookup"><span data-stu-id="29fa1-158">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="29fa1-159">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="29fa1-159">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="29fa1-160">Při spuštění příkazu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="29fa1-160">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="29fa1-161">Adresář, ve kterém se mají najít binární soubory, které se mají spustit.</span><span class="sxs-lookup"><span data-stu-id="29fa1-161">Directory in which to find the binaries to run.</span></span> <span data-ttu-id="29fa1-162">Pokud není zadaný, použije se výchozí cesta `./bin/<configuration>/<framework>/` .</span><span class="sxs-lookup"><span data-stu-id="29fa1-162">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="29fa1-163">Pro projekty s více cílovými rozhraními (prostřednictvím `TargetFrameworks` Vlastnosti) musíte definovat i `--framework` při zadání této možnosti.</span><span class="sxs-lookup"><span data-stu-id="29fa1-163">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span> <span data-ttu-id="29fa1-164">`dotnet test`vždy spouští testy z výstupního adresáře.</span><span class="sxs-lookup"><span data-stu-id="29fa1-164">`dotnet test` always runs tests from the output directory.</span></span> <span data-ttu-id="29fa1-165">Můžete použít <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> pro využívání testovacích prostředků ve výstupním adresáři.</span><span class="sxs-lookup"><span data-stu-id="29fa1-165">You can use <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> to consume test assets in the output directory.</span></span>

- **`-r|--results-directory <PATH>`**

  <span data-ttu-id="29fa1-166">Adresář, do kterého budou umístěny výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="29fa1-166">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="29fa1-167">Pokud zadaný adresář neexistuje, vytvoří se.</span><span class="sxs-lookup"><span data-stu-id="29fa1-167">If the specified directory doesn't exist, it's created.</span></span> <span data-ttu-id="29fa1-168">Výchozí hodnota je `TestResults` v adresáři, který obsahuje soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="29fa1-168">The default is `TestResults` in the directory that contains the project file.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="29fa1-169">Cílový modul runtime, pro který se má testovat.</span><span class="sxs-lookup"><span data-stu-id="29fa1-169">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="29fa1-170">`.runsettings`Soubor, který se má použít pro spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="29fa1-170">The `.runsettings` file to use for running the tests.</span></span> <span data-ttu-id="29fa1-171">`TargetPlatform`Element (x86 | x64) nemá žádný vliv na `dotnet test` .</span><span class="sxs-lookup"><span data-stu-id="29fa1-171">The `TargetPlatform` element (x86|x64) has no effect for `dotnet test`.</span></span> <span data-ttu-id="29fa1-172">Chcete-li spustit testy, které cílí na x86, nainstalujte verzi x86 rozhraní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="29fa1-172">To run tests that target x86, install the x86 version of .NET Core.</span></span> <span data-ttu-id="29fa1-173">Bitová verze příkazu *dotnet. exe* , který je na cestě, bude použit pro spouštění testů.</span><span class="sxs-lookup"><span data-stu-id="29fa1-173">The bitness of the *dotnet.exe* that is on the path is what will be used for running tests.</span></span> <span data-ttu-id="29fa1-174">Další informace najdete v následujících materiálech:</span><span class="sxs-lookup"><span data-stu-id="29fa1-174">For more information, see the following resources:</span></span>

  - [<span data-ttu-id="29fa1-175">Nakonfigurujte testy jednotek pomocí `.runsettings` souboru.</span><span class="sxs-lookup"><span data-stu-id="29fa1-175">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)
  - [<span data-ttu-id="29fa1-176">Konfigurace testovacího běhu</span><span class="sxs-lookup"><span data-stu-id="29fa1-176">Configure a test run</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/configure.md)

- **`-t|--list-tests`**

  <span data-ttu-id="29fa1-177">Vypíše všechny zjištěné testy v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="29fa1-177">List all of the discovered tests in the current project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="29fa1-178">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="29fa1-178">Sets the verbosity level of the command.</span></span> <span data-ttu-id="29fa1-179">Povolené hodnoty jsou `q[uiet]` , `m[inimal]` ,, a `n[ormal]` `d[etailed]` `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="29fa1-179">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="29fa1-180">Výchozí formát je `minimal`.</span><span class="sxs-lookup"><span data-stu-id="29fa1-180">The default is `minimal`.</span></span> <span data-ttu-id="29fa1-181">Další informace naleznete v tématu <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span><span class="sxs-lookup"><span data-stu-id="29fa1-181">For more information, see <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span></span>

- <span data-ttu-id="29fa1-182">**`RunSettings`** náhodné</span><span class="sxs-lookup"><span data-stu-id="29fa1-182">**`RunSettings`** arguments</span></span>

 <span data-ttu-id="29fa1-183">Inline `RunSettings` se předávají jako poslední argumenty příkazového řádku za znakem "--" (Všimněte si místa za-).</span><span class="sxs-lookup"><span data-stu-id="29fa1-183">Inline `RunSettings` are passed as the last arguments on the command line after "-- " (note the space after --).</span></span> <span data-ttu-id="29fa1-184">`RunSettings`Jako páry jsou zadány vložené `[name]=[value]` .</span><span class="sxs-lookup"><span data-stu-id="29fa1-184">Inline `RunSettings` are specified as `[name]=[value]` pairs.</span></span> <span data-ttu-id="29fa1-185">K oddělení více párů se používá mezera `[name]=[value]` .</span><span class="sxs-lookup"><span data-stu-id="29fa1-185">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="29fa1-186">Příklad: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="29fa1-186">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="29fa1-187">Další informace najdete v tématu [předávání argumentů runsettings pomocí příkazového řádku](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="29fa1-187">For more information, see [Passing RunSettings arguments through command line](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="29fa1-188">Příklady</span><span class="sxs-lookup"><span data-stu-id="29fa1-188">Examples</span></span>

- <span data-ttu-id="29fa1-189">Spustit testy v projektu v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="29fa1-189">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="29fa1-190">Spustit testy v `test1` projektu:</span><span class="sxs-lookup"><span data-stu-id="29fa1-190">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="29fa1-191">Spusťte testy v projektu v aktuálním adresáři a vygenerujte soubor výsledků testů ve formátu TRX:</span><span class="sxs-lookup"><span data-stu-id="29fa1-191">Run the tests in the project in the current directory, and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

- <span data-ttu-id="29fa1-192">Spusťte testy v projektu v aktuálním adresáři a vygenerujte soubor pokrytí kódu (po instalaci [Coverlet](https://github.com/tonerdo/coverlet/blob/master/README.md)):</span><span class="sxs-lookup"><span data-stu-id="29fa1-192">Run the tests in the project in the current directory, and generate a code coverage file (after installing [Coverlet](https://github.com/tonerdo/coverlet/blob/master/README.md)):</span></span>

  ```dotnetcli
  dotnet test --collect:"XPlat Code Coverage"
  ```

- <span data-ttu-id="29fa1-193">Spusťte testy v projektu v aktuálním adresáři a vygenerujte soubor pokrytí kódu (pouze Windows):</span><span class="sxs-lookup"><span data-stu-id="29fa1-193">Run the tests in the project in the current directory, and generate a code coverage file (Windows only):</span></span>

  ```dotnetcli
  dotnet test --collect "Code Coverage"
  ```

- <span data-ttu-id="29fa1-194">Spusťte testy v projektu v aktuálním adresáři a log s detailní podrobností do konzoly:</span><span class="sxs-lookup"><span data-stu-id="29fa1-194">Run the tests in the project in the current directory, and log with detailed verbosity to the console:</span></span>

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```
  
  - <span data-ttu-id="29fa1-195">Spusťte testy v projektu v aktuálním adresáři a Nahlášením testů, které probíhaly při selhání hostitele testu:</span><span class="sxs-lookup"><span data-stu-id="29fa1-195">Run the tests in the project in the current directory, and report tests that were in progress when the test host crashed:</span></span>

  ```dotnetcli
  dotnet test --blame
  ```

## <a name="filter-option-details"></a><span data-ttu-id="29fa1-196">Podrobnosti možnosti filtru</span><span class="sxs-lookup"><span data-stu-id="29fa1-196">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="29fa1-197">`<Expression>`má formát `<property><operator><value>[|&<Expression>]` .</span><span class="sxs-lookup"><span data-stu-id="29fa1-197">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="29fa1-198">`<property>`je atributem `Test Case` .</span><span class="sxs-lookup"><span data-stu-id="29fa1-198">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="29fa1-199">Níže jsou uvedené vlastnosti podporované oblíbenými rozhraními pro testování částí:</span><span class="sxs-lookup"><span data-stu-id="29fa1-199">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="29fa1-200">Testovací rozhraní</span><span class="sxs-lookup"><span data-stu-id="29fa1-200">Test Framework</span></span> | <span data-ttu-id="29fa1-201">Podporované vlastnosti</span><span class="sxs-lookup"><span data-stu-id="29fa1-201">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="29fa1-202">MSTest</span><span class="sxs-lookup"><span data-stu-id="29fa1-202">MSTest</span></span>         | <ul><li><span data-ttu-id="29fa1-203">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="29fa1-203">FullyQualifiedName</span></span></li><li><span data-ttu-id="29fa1-204">Name</span><span class="sxs-lookup"><span data-stu-id="29fa1-204">Name</span></span></li><li><span data-ttu-id="29fa1-205">NázevTřídy</span><span class="sxs-lookup"><span data-stu-id="29fa1-205">ClassName</span></span></li><li><span data-ttu-id="29fa1-206">Priorita</span><span class="sxs-lookup"><span data-stu-id="29fa1-206">Priority</span></span></li><li><span data-ttu-id="29fa1-207">TestCategory</span><span class="sxs-lookup"><span data-stu-id="29fa1-207">TestCategory</span></span></li></ul> |
| <span data-ttu-id="29fa1-208">xUnit</span><span class="sxs-lookup"><span data-stu-id="29fa1-208">xUnit</span></span>          | <ul><li><span data-ttu-id="29fa1-209">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="29fa1-209">FullyQualifiedName</span></span></li><li><span data-ttu-id="29fa1-210">DisplayName</span><span class="sxs-lookup"><span data-stu-id="29fa1-210">DisplayName</span></span></li><li><span data-ttu-id="29fa1-211">Traits</span><span class="sxs-lookup"><span data-stu-id="29fa1-211">Traits</span></span></li></ul>                                   |
| <span data-ttu-id="29fa1-212">NUnit</span><span class="sxs-lookup"><span data-stu-id="29fa1-212">NUnit</span></span>          | <ul><li><span data-ttu-id="29fa1-213">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="29fa1-213">FullyQualifiedName</span></span></li><li><span data-ttu-id="29fa1-214">Name</span><span class="sxs-lookup"><span data-stu-id="29fa1-214">Name</span></span></li><li><span data-ttu-id="29fa1-215">TestCategory</span><span class="sxs-lookup"><span data-stu-id="29fa1-215">TestCategory</span></span></li><li><span data-ttu-id="29fa1-216">Priorita</span><span class="sxs-lookup"><span data-stu-id="29fa1-216">Priority</span></span></li></ul>                                   |

<span data-ttu-id="29fa1-217">`<operator>`Popisuje vztah mezi vlastností a hodnotou:</span><span class="sxs-lookup"><span data-stu-id="29fa1-217">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="29fa1-218">Operátor</span><span class="sxs-lookup"><span data-stu-id="29fa1-218">Operator</span></span> | <span data-ttu-id="29fa1-219">Funkce</span><span class="sxs-lookup"><span data-stu-id="29fa1-219">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="29fa1-220">Přesná shoda</span><span class="sxs-lookup"><span data-stu-id="29fa1-220">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="29fa1-221">Nepřesná shoda</span><span class="sxs-lookup"><span data-stu-id="29fa1-221">Not exact match</span></span> |
| `~`      | <span data-ttu-id="29fa1-222">Contains</span><span class="sxs-lookup"><span data-stu-id="29fa1-222">Contains</span></span>        |
| `!~`     | <span data-ttu-id="29fa1-223">Neobsahuje</span><span class="sxs-lookup"><span data-stu-id="29fa1-223">Not contains</span></span>    |

<span data-ttu-id="29fa1-224">`<value>`je řetězec.</span><span class="sxs-lookup"><span data-stu-id="29fa1-224">`<value>` is a string.</span></span> <span data-ttu-id="29fa1-225">U všech hledání se nerozlišují malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="29fa1-225">All the lookups are case insensitive.</span></span>

<span data-ttu-id="29fa1-226">Výraz bez objektu `<operator>` je automaticky považován za `contains` `FullyQualifiedName` vlastnost on (například `dotnet test --filter xyz` je stejný jako `dotnet test --filter FullyQualifiedName~xyz` ).</span><span class="sxs-lookup"><span data-stu-id="29fa1-226">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="29fa1-227">Výrazy se dají spojit s podmíněnými operátory:</span><span class="sxs-lookup"><span data-stu-id="29fa1-227">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="29fa1-228">Operátor</span><span class="sxs-lookup"><span data-stu-id="29fa1-228">Operator</span></span>            | <span data-ttu-id="29fa1-229">Funkce</span><span class="sxs-lookup"><span data-stu-id="29fa1-229">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="29fa1-230">OR</span><span class="sxs-lookup"><span data-stu-id="29fa1-230">OR</span></span>       |
| `&`                 | <span data-ttu-id="29fa1-231">AND</span><span class="sxs-lookup"><span data-stu-id="29fa1-231">AND</span></span>      |

<span data-ttu-id="29fa1-232">Výrazy můžete uzavřít do závorek při použití podmíněných operátorů (například `(Name~TestMethod1) | (Name~TestMethod2)` ).</span><span class="sxs-lookup"><span data-stu-id="29fa1-232">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="29fa1-233">Další informace a příklady použití selektivního filtrování testů jednotek naleznete v tématu [spuštění selektivních testů jednotek](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="29fa1-233">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="29fa1-234">Viz také</span><span class="sxs-lookup"><span data-stu-id="29fa1-234">See also</span></span>

- [<span data-ttu-id="29fa1-235">Architektury a cíle</span><span class="sxs-lookup"><span data-stu-id="29fa1-235">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="29fa1-236">Katalog identifikátorů runtime .NET Core (RID)</span><span class="sxs-lookup"><span data-stu-id="29fa1-236">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="29fa1-237">Předávání argumentů runsettings prostřednictvím příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="29fa1-237">Passing runsettings arguments through commandline</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
