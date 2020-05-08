---
title: dotnet – příkaz testu
description: Příkaz dotnet test se používá ke spouštění testů jednotek v daném projektu.
ms.date: 04/29/2020
ms.openlocfilehash: ef71e48daa7c4a6f33961d05a2f3def122087b0e
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975430"
---
# <a name="dotnet-test"></a><span data-ttu-id="41d7b-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="41d7b-103">dotnet test</span></span>

<span data-ttu-id="41d7b-104">**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="41d7b-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="41d7b-105">Name</span><span class="sxs-lookup"><span data-stu-id="41d7b-105">Name</span></span>

<span data-ttu-id="41d7b-106">`dotnet test`– Testovací ovladač .NET, který se používá ke spouštění testů jednotek.</span><span class="sxs-lookup"><span data-stu-id="41d7b-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="41d7b-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="41d7b-107">Synopsis</span></span>

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

## <a name="description"></a><span data-ttu-id="41d7b-108">Popis</span><span class="sxs-lookup"><span data-stu-id="41d7b-108">Description</span></span>

<span data-ttu-id="41d7b-109">`dotnet test` Příkaz slouží ke spuštění testů jednotek v daném řešení.</span><span class="sxs-lookup"><span data-stu-id="41d7b-109">The `dotnet test` command is used to execute unit tests in a given solution.</span></span> <span data-ttu-id="41d7b-110">`dotnet test` Příkaz sestaví řešení a spustí testovací hostitelskou aplikaci pro každý projekt testů v řešení.</span><span class="sxs-lookup"><span data-stu-id="41d7b-110">The `dotnet test` command builds the solution and runs a test host application for each test project in the solution.</span></span> <span data-ttu-id="41d7b-111">Testovací hostitel provede v daném projektu testy pomocí testovacího rozhraní, například: MSTest, NUnit nebo xUnit, a ohlásí úspěch nebo neúspěch každého testu.</span><span class="sxs-lookup"><span data-stu-id="41d7b-111">The test host executes tests in the given project using a test framework, for example: MSTest, NUnit, or xUnit, and reports the success or failure of each test.</span></span> <span data-ttu-id="41d7b-112">Pokud jsou všechny testy úspěšné, Test Runner vrátí 0 jako ukončovací kód; jinak, pokud nějaký test selže, vrátí 1.</span><span class="sxs-lookup"><span data-stu-id="41d7b-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span>

<span data-ttu-id="41d7b-113">Pro projekty zaměřené na více platforem jsou testy spouštěny pro každou cílovou architekturu.</span><span class="sxs-lookup"><span data-stu-id="41d7b-113">For multi-targeted projects, tests are run for each targeted framework.</span></span> <span data-ttu-id="41d7b-114">Testovací hostitel a testovací rozhraní jednotky jsou zabaleny jako balíčky NuGet a jsou obnoveny jako běžné závislosti pro projekt.</span><span class="sxs-lookup"><span data-stu-id="41d7b-114">The test host and the unit test framework are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="41d7b-115">Projekty testů určují testovací spouštěč pomocí obyčejného `<PackageReference>` prvku, jak je vidět v následujícím ukázkovém souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="41d7b-115">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

<span data-ttu-id="41d7b-116">Kde `Microsoft.NET.Test.Sdk` je testovací hostitel, `xunit` je testovací rozhraní.</span><span class="sxs-lookup"><span data-stu-id="41d7b-116">Where `Microsoft.NET.Test.Sdk` is the test host, `xunit` is the test framework.</span></span> <span data-ttu-id="41d7b-117">A `xunit.runner.visualstudio` je testovací adaptér, který umožňuje, aby architektura xUnit spolupracovala s testovacím hostitelem.</span><span class="sxs-lookup"><span data-stu-id="41d7b-117">And `xunit.runner.visualstudio` is a test adapter, which allows the xUnit framework to work with the test host.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="41d7b-118">Implicitní obnovení</span><span class="sxs-lookup"><span data-stu-id="41d7b-118">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="41d7b-119">Arguments</span><span class="sxs-lookup"><span data-stu-id="41d7b-119">Arguments</span></span>

- **`PROJECT | SOLUTION | DIRECTORY | DLL`**

  - <span data-ttu-id="41d7b-120">Cesta k testovacímu projektu.</span><span class="sxs-lookup"><span data-stu-id="41d7b-120">Path to the test project.</span></span>
  - <span data-ttu-id="41d7b-121">Cesta k řešení</span><span class="sxs-lookup"><span data-stu-id="41d7b-121">Path to the solution.</span></span>
  - <span data-ttu-id="41d7b-122">Cesta k adresáři, který obsahuje projekt nebo řešení.</span><span class="sxs-lookup"><span data-stu-id="41d7b-122">Path to a directory that contains a project or a solution.</span></span>
  - <span data-ttu-id="41d7b-123">Cesta k souboru projektu testů *. dll* .</span><span class="sxs-lookup"><span data-stu-id="41d7b-123">Path to a test project *.dll* file.</span></span>

  <span data-ttu-id="41d7b-124">Pokud není zadán, vyhledá projekt nebo řešení v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="41d7b-124">If not specified, it searches for a project or a solution in the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="41d7b-125">Možnosti</span><span class="sxs-lookup"><span data-stu-id="41d7b-125">Options</span></span>

- **`-a|--test-adapter-path <PATH_TO_ADAPTER>`**

  <span data-ttu-id="41d7b-126">Cesta k adresáři, ve kterém se mají hledat další testovací adaptéry</span><span class="sxs-lookup"><span data-stu-id="41d7b-126">Path to a directory to be searched for additional test adapters.</span></span> <span data-ttu-id="41d7b-127">Jsou *.dll* zkontrolovány pouze soubory DLL `.TestAdapter.dll` s příponou.</span><span class="sxs-lookup"><span data-stu-id="41d7b-127">Only *.dll* files with suffix `.TestAdapter.dll` are inspected.</span></span> <span data-ttu-id="41d7b-128">Pokud není zadán, bude prohledán adresář souboru Test *. dll* .</span><span class="sxs-lookup"><span data-stu-id="41d7b-128">If not specified, the directory of the test *.dll* is searched.</span></span>

- **`--blame`**

  <span data-ttu-id="41d7b-129">Spustí testy v režimu viny.</span><span class="sxs-lookup"><span data-stu-id="41d7b-129">Runs the tests in blame mode.</span></span> <span data-ttu-id="41d7b-130">Tato možnost je užitečná při izolaci problematických testů, které způsobují selhání hostitele testu.</span><span class="sxs-lookup"><span data-stu-id="41d7b-130">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="41d7b-131">Při zjištění chyby vytvoří soubor sekvence v `TestResults/<Guid>/<Guid>_Sequence.xml` , který zachytí pořadí testů, které byly spuštěny před selháním.</span><span class="sxs-lookup"><span data-stu-id="41d7b-131">When a crash is detected, it creates an sequence file in `TestResults/<Guid>/<Guid>_Sequence.xml` that captures the order of tests that were run before the crash.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="41d7b-132">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="41d7b-132">Defines the build configuration.</span></span> <span data-ttu-id="41d7b-133">Výchozí hodnota je `Debug`, ale konfigurace vašeho projektu může přepsat toto výchozí nastavení sady SDK.</span><span class="sxs-lookup"><span data-stu-id="41d7b-133">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  <span data-ttu-id="41d7b-134">Povolí shromažďování dat pro testovací běh.</span><span class="sxs-lookup"><span data-stu-id="41d7b-134">Enables data collector for the test run.</span></span> <span data-ttu-id="41d7b-135">Další informace najdete v tématu [monitorování a analýza testovacího běhu](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="41d7b-135">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

- **`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  <span data-ttu-id="41d7b-136">Povolí diagnostický režim pro testovací platformu a zapisuje diagnostické zprávy do zadaného souboru a do souborů vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="41d7b-136">Enables diagnostic mode for the test platform and writes diagnostic messages to the specified file and to files next to it.</span></span> <span data-ttu-id="41d7b-137">Proces, který zaznamenává zprávy, určuje, které soubory jsou vytvořeny, například `*.host_<date>.txt` pro protokol testu hostitele a `*.datacollector_<date>.txt` protokol sběru dat.</span><span class="sxs-lookup"><span data-stu-id="41d7b-137">The process that is logging the messages determines which files are created, such as `*.host_<date>.txt` for test host log, and `*.datacollector_<date>.txt` for data collector log.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="41d7b-138">Vynutí použití `dotnet` nebo .NET Framework testovacího hostitele pro binární soubory testu.</span><span class="sxs-lookup"><span data-stu-id="41d7b-138">Forces the use of `dotnet` or .NET Framework test host for the test binaries.</span></span> <span data-ttu-id="41d7b-139">Tato možnost určuje pouze typ hostitele, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="41d7b-139">This option only determines which type of host to use.</span></span> <span data-ttu-id="41d7b-140">Skutečná verze rozhraní, která se má použít, se určuje pomocí *runtimeconfig. JSON* testovacího projektu.</span><span class="sxs-lookup"><span data-stu-id="41d7b-140">The actual framework version to be used is determined by the *runtimeconfig.json* of the test project.</span></span> <span data-ttu-id="41d7b-141">Pokud není zadaný, použije se k určení typu hostitele [atribut pro sestavení targetFramework](/dotnet/api/system.runtime.versioning.targetframeworkattribute) .</span><span class="sxs-lookup"><span data-stu-id="41d7b-141">When not specified, the [TargetFramework assembly attribute](/dotnet/api/system.runtime.versioning.targetframeworkattribute) is used to determine the type of host.</span></span> <span data-ttu-id="41d7b-142">Když je tento atribut ze souboru *. dll*odstraněn, je použit hostitel .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="41d7b-142">When that attribute is stripped from the *.dll*, the .NET Framework host is used.</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="41d7b-143">Odfiltruje testy v aktuálním projektu pomocí daného výrazu.</span><span class="sxs-lookup"><span data-stu-id="41d7b-143">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="41d7b-144">Další informace najdete v části [Podrobnosti o možnosti filtru](#filter-option-details) .</span><span class="sxs-lookup"><span data-stu-id="41d7b-144">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="41d7b-145">Další informace a příklady použití selektivního filtrování testů jednotek naleznete v tématu [spuštění selektivních testů jednotek](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="41d7b-145">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="41d7b-146">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="41d7b-146">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="41d7b-147">Umožňuje zastavení příkazu zastavit a počkat na vstup nebo akci uživatele.</span><span class="sxs-lookup"><span data-stu-id="41d7b-147">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="41d7b-148">Například k dokončení ověřování.</span><span class="sxs-lookup"><span data-stu-id="41d7b-148">For example, to complete authentication.</span></span> <span data-ttu-id="41d7b-149">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="41d7b-149">Available since .NET Core 3.0 SDK.</span></span>

- **`-l|--logger <LOGGER_URI/FRIENDLY_NAME>`**

  <span data-ttu-id="41d7b-150">Určuje protokolovací nástroj pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="41d7b-150">Specifies a logger for test results.</span></span> <span data-ttu-id="41d7b-151">Na rozdíl od MSBuild test dotnet nepřijímá zkratky: místo `-l "console;v=d"` použití. `-l "console;verbosity=detailed"`</span><span class="sxs-lookup"><span data-stu-id="41d7b-151">Unlike MSBuild, dotnet test doesn't accept abbreviations: instead of `-l "console;v=d"` use `-l "console;verbosity=detailed"`.</span></span>

- **`--no-build`**

  <span data-ttu-id="41d7b-152">Před spuštěním nevytvoří testovací projekt.</span><span class="sxs-lookup"><span data-stu-id="41d7b-152">Doesn't build the test project before running it.</span></span> <span data-ttu-id="41d7b-153">Také implicitně nastaví příznak- `--no-restore` .</span><span class="sxs-lookup"><span data-stu-id="41d7b-153">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="41d7b-154">Spusťte testy bez zobrazení banneru Microsoft TestPlatform.</span><span class="sxs-lookup"><span data-stu-id="41d7b-154">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="41d7b-155">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="41d7b-155">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="41d7b-156">Při spuštění příkazu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="41d7b-156">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="41d7b-157">Adresář, ve kterém se mají najít binární soubory, které se mají spustit.</span><span class="sxs-lookup"><span data-stu-id="41d7b-157">Directory in which to find the binaries to run.</span></span> <span data-ttu-id="41d7b-158">Pokud není zadaný, použije se výchozí cesta `./bin/<configuration>/<framework>/`.</span><span class="sxs-lookup"><span data-stu-id="41d7b-158">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="41d7b-159">Pro projekty s více cílovými rozhraními (prostřednictvím `TargetFrameworks` vlastnosti) musíte definovat `--framework` i při zadání této možnosti.</span><span class="sxs-lookup"><span data-stu-id="41d7b-159">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span> <span data-ttu-id="41d7b-160">`dotnet test`vždy spouštějte testy z výstupního adresáře.</span><span class="sxs-lookup"><span data-stu-id="41d7b-160">`dotnet test` always run tests from the output directory.</span></span> <span data-ttu-id="41d7b-161">Můžete použít <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> pro využívání testovacích prostředků ve výstupním adresáři.</span><span class="sxs-lookup"><span data-stu-id="41d7b-161">You can use <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> to consume test assets in the output directory.</span></span>

- **`-r|--results-directory <PATH>`**

  <span data-ttu-id="41d7b-162">Adresář, do kterého budou umístěny výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="41d7b-162">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="41d7b-163">Pokud zadaný adresář neexistuje, vytvoří se.</span><span class="sxs-lookup"><span data-stu-id="41d7b-163">If the specified directory doesn't exist, it's created.</span></span> <span data-ttu-id="41d7b-164">Výchozí hodnota je `TestResults` v adresáři, který obsahuje soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="41d7b-164">The default is `TestResults` in the directory that contains the project file.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="41d7b-165">Cílový modul runtime, pro který se má testovat.</span><span class="sxs-lookup"><span data-stu-id="41d7b-165">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="41d7b-166">`.runsettings` Soubor, který se má použít pro spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="41d7b-166">The `.runsettings` file to use for running the tests.</span></span> <span data-ttu-id="41d7b-167">Všimněte si, `TargetPlatform` že element (x86 | x64) nemá žádný vliv `dotnet test`na.</span><span class="sxs-lookup"><span data-stu-id="41d7b-167">Note that the `TargetPlatform` element (x86|x64) has no effect for `dotnet test`.</span></span> <span data-ttu-id="41d7b-168">Chcete-li spustit testy, které cílí na x86, nainstalujte verzi x86 rozhraní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="41d7b-168">To run tests that target x86, install the x86 version of .NET Core.</span></span> <span data-ttu-id="41d7b-169">Bitová verze příkazu *dotnet. exe* , který je na cestě, bude použit pro spouštění testů.</span><span class="sxs-lookup"><span data-stu-id="41d7b-169">The bitness of the *dotnet.exe* that is on the path is what will be used for running tests.</span></span> <span data-ttu-id="41d7b-170">Další informace najdete v následujících materiálech:</span><span class="sxs-lookup"><span data-stu-id="41d7b-170">For more information, see the following resources:</span></span>

  - [<span data-ttu-id="41d7b-171">Nakonfigurujte testy jednotek pomocí `.runsettings` souboru.</span><span class="sxs-lookup"><span data-stu-id="41d7b-171">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)
  - [<span data-ttu-id="41d7b-172">Konfigurace testovacího běhu</span><span class="sxs-lookup"><span data-stu-id="41d7b-172">Configure a test run</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/configure.md)

- **`-t|--list-tests`**

  <span data-ttu-id="41d7b-173">Vypíše všechny zjištěné testy v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="41d7b-173">List all of the discovered tests in the current project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="41d7b-174">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="41d7b-174">Sets the verbosity level of the command.</span></span> <span data-ttu-id="41d7b-175">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]` `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="41d7b-175">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="41d7b-176">Výchozí formát je `minimal`.</span><span class="sxs-lookup"><span data-stu-id="41d7b-176">The default is `minimal`.</span></span> <span data-ttu-id="41d7b-177">Další informace naleznete v tématu <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span><span class="sxs-lookup"><span data-stu-id="41d7b-177">For more information, see <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span></span>

- <span data-ttu-id="41d7b-178">**`RunSettings`** náhodné</span><span class="sxs-lookup"><span data-stu-id="41d7b-178">**`RunSettings`** arguments</span></span>

 <span data-ttu-id="41d7b-179">Inline `RunSettings` se předávají jako poslední argumenty příkazového řádku za znakem "--" (Všimněte si místa za-).</span><span class="sxs-lookup"><span data-stu-id="41d7b-179">Inline `RunSettings` are passed as the last arguments on the command line after "-- " (note the space after --).</span></span> <span data-ttu-id="41d7b-180">Jako `RunSettings` `[name]=[value]` páry jsou zadány vložené.</span><span class="sxs-lookup"><span data-stu-id="41d7b-180">Inline `RunSettings` are specified as `[name]=[value]` pairs.</span></span> <span data-ttu-id="41d7b-181">K oddělení více `[name]=[value]` párů se používá mezera.</span><span class="sxs-lookup"><span data-stu-id="41d7b-181">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="41d7b-182">Příklad: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="41d7b-182">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="41d7b-183">Další informace najdete v tématu [předávání argumentů runsettings pomocí příkazového řádku](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="41d7b-183">For more information, see [Passing RunSettings arguments through command line](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="41d7b-184">Příklady</span><span class="sxs-lookup"><span data-stu-id="41d7b-184">Examples</span></span>

- <span data-ttu-id="41d7b-185">Spustit testy v projektu v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="41d7b-185">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="41d7b-186">Spustit testy v `test1` projektu:</span><span class="sxs-lookup"><span data-stu-id="41d7b-186">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="41d7b-187">Spusťte testy v projektu v aktuálním adresáři a vygenerujte soubor výsledků testů ve formátu TRX:</span><span class="sxs-lookup"><span data-stu-id="41d7b-187">Run the tests in the project in the current directory, and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

- <span data-ttu-id="41d7b-188">Spusťte testy v projektu v aktuálním adresáři a log s detailní podrobností do konzoly:</span><span class="sxs-lookup"><span data-stu-id="41d7b-188">Run the tests in the project in the current directory, and log with detailed verbosity to the console:</span></span>

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```
  
  - <span data-ttu-id="41d7b-189">Spusťte testy v projektu v aktuálním adresáři a Nahlášením testů, které probíhaly při selhání hostitele testu:</span><span class="sxs-lookup"><span data-stu-id="41d7b-189">Run the tests in the project in the current directory, and report tests that were in progress when the test host crashed:</span></span>

  ```dotnetcli
  dotnet test --blame
  ```

## <a name="filter-option-details"></a><span data-ttu-id="41d7b-190">Podrobnosti možnosti filtru</span><span class="sxs-lookup"><span data-stu-id="41d7b-190">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="41d7b-191">`<Expression>`má formát `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="41d7b-191">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="41d7b-192">`<property>`je atributem `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="41d7b-192">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="41d7b-193">Níže jsou uvedené vlastnosti podporované oblíbenými rozhraními pro testování částí:</span><span class="sxs-lookup"><span data-stu-id="41d7b-193">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="41d7b-194">Testovací rozhraní</span><span class="sxs-lookup"><span data-stu-id="41d7b-194">Test Framework</span></span> | <span data-ttu-id="41d7b-195">Podporované vlastnosti</span><span class="sxs-lookup"><span data-stu-id="41d7b-195">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="41d7b-196">MSTest</span><span class="sxs-lookup"><span data-stu-id="41d7b-196">MSTest</span></span>         | <ul><li><span data-ttu-id="41d7b-197">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="41d7b-197">FullyQualifiedName</span></span></li><li><span data-ttu-id="41d7b-198">Name</span><span class="sxs-lookup"><span data-stu-id="41d7b-198">Name</span></span></li><li><span data-ttu-id="41d7b-199">NázevTřídy</span><span class="sxs-lookup"><span data-stu-id="41d7b-199">ClassName</span></span></li><li><span data-ttu-id="41d7b-200">Priorita</span><span class="sxs-lookup"><span data-stu-id="41d7b-200">Priority</span></span></li><li><span data-ttu-id="41d7b-201">TestCategory</span><span class="sxs-lookup"><span data-stu-id="41d7b-201">TestCategory</span></span></li></ul> |
| <span data-ttu-id="41d7b-202">xUnit</span><span class="sxs-lookup"><span data-stu-id="41d7b-202">xUnit</span></span>          | <ul><li><span data-ttu-id="41d7b-203">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="41d7b-203">FullyQualifiedName</span></span></li><li><span data-ttu-id="41d7b-204">DisplayName</span><span class="sxs-lookup"><span data-stu-id="41d7b-204">DisplayName</span></span></li><li><span data-ttu-id="41d7b-205">Traits</span><span class="sxs-lookup"><span data-stu-id="41d7b-205">Traits</span></span></li></ul>                                   |

<span data-ttu-id="41d7b-206">`<operator>` Popisuje vztah mezi vlastností a hodnotou:</span><span class="sxs-lookup"><span data-stu-id="41d7b-206">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="41d7b-207">Operátor</span><span class="sxs-lookup"><span data-stu-id="41d7b-207">Operator</span></span> | <span data-ttu-id="41d7b-208">Funkce</span><span class="sxs-lookup"><span data-stu-id="41d7b-208">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="41d7b-209">Přesná shoda</span><span class="sxs-lookup"><span data-stu-id="41d7b-209">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="41d7b-210">Nepřesná shoda</span><span class="sxs-lookup"><span data-stu-id="41d7b-210">Not exact match</span></span> |
| `~`      | <span data-ttu-id="41d7b-211">Contains</span><span class="sxs-lookup"><span data-stu-id="41d7b-211">Contains</span></span>        |
| `!~`     | <span data-ttu-id="41d7b-212">Neobsahuje</span><span class="sxs-lookup"><span data-stu-id="41d7b-212">Not contains</span></span>    |

<span data-ttu-id="41d7b-213">`<value>`je řetězec.</span><span class="sxs-lookup"><span data-stu-id="41d7b-213">`<value>` is a string.</span></span> <span data-ttu-id="41d7b-214">U všech hledání se nerozlišují malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="41d7b-214">All the lookups are case insensitive.</span></span>

<span data-ttu-id="41d7b-215">Výraz bez objektu `<operator>` je automaticky považován za vlastnost `contains` on `FullyQualifiedName` (například `dotnet test --filter xyz` je stejný jako `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="41d7b-215">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="41d7b-216">Výrazy se dají spojit s podmíněnými operátory:</span><span class="sxs-lookup"><span data-stu-id="41d7b-216">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="41d7b-217">Operátor</span><span class="sxs-lookup"><span data-stu-id="41d7b-217">Operator</span></span>            | <span data-ttu-id="41d7b-218">Funkce</span><span class="sxs-lookup"><span data-stu-id="41d7b-218">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="41d7b-219">NEBO</span><span class="sxs-lookup"><span data-stu-id="41d7b-219">OR</span></span>       |
| `&`                 | <span data-ttu-id="41d7b-220">AND</span><span class="sxs-lookup"><span data-stu-id="41d7b-220">AND</span></span>      |

<span data-ttu-id="41d7b-221">Výrazy můžete uzavřít do závorek při použití podmíněných operátorů (například `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="41d7b-221">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="41d7b-222">Další informace a příklady použití selektivního filtrování testů jednotek naleznete v tématu [spuštění selektivních testů jednotek](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="41d7b-222">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="41d7b-223">Viz také</span><span class="sxs-lookup"><span data-stu-id="41d7b-223">See also</span></span>

- [<span data-ttu-id="41d7b-224">Architektury a cíle</span><span class="sxs-lookup"><span data-stu-id="41d7b-224">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="41d7b-225">Katalog identifikátorů runtime .NET Core (RID)</span><span class="sxs-lookup"><span data-stu-id="41d7b-225">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="41d7b-226">Předávání argumentů runsettings prostřednictvím příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="41d7b-226">Passing runsettings arguments through commandline</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
