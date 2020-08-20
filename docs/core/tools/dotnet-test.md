---
title: dotnet – příkaz testu
description: Příkaz dotnet test se používá ke spouštění testů jednotek v daném projektu.
ms.date: 04/29/2020
ms.openlocfilehash: d67521084330b206afca89baf59228b99ca799a1
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656752"
---
# <a name="dotnet-test"></a><span data-ttu-id="0efa3-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="0efa3-103">dotnet test</span></span>

<span data-ttu-id="0efa3-104">**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="0efa3-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="0efa3-105">Název</span><span class="sxs-lookup"><span data-stu-id="0efa3-105">Name</span></span>

<span data-ttu-id="0efa3-106">`dotnet test` – Testovací ovladač .NET, který se používá ke spouštění testů jednotek.</span><span class="sxs-lookup"><span data-stu-id="0efa3-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0efa3-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="0efa3-107">Synopsis</span></span>

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION> | <DIRECTORY> | <DLL>]
    [-a|--test-adapter-path <ADAPTER_PATH>] [--blame] [--blame-crash]
    [--blame-crash-dump-type <DUMP_TYPE>] [--blame-crash-collect-always]
    [--blame-hang] [--blame-hang-dump-type <DUMP_TYPE>]
    [--blame-hang-timeout <TIMESPAN>]
    [-c|--configuration <CONFIGURATION>]
    [--collect <DATA_COLLECTOR_NAME>]
    [-d|--diag <LOG_FILE>] [-f|--framework <FRAMEWORK>]
    [--filter <EXPRESSION>] [--interactive]
    [-l|--logger <LOGGER>] [--no-build]
    [--nologo] [--no-restore] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--results-directory <RESULTS_DIR>] [--runtime <RUNTIME_IDENTIFIER>]
    [-s|--settings <SETTINGS_FILE>] [-t|--list-tests]
    [-v|--verbosity <LEVEL>] [[--] <RunSettings arguments>]

dotnet test -h|--help
```

## <a name="description"></a><span data-ttu-id="0efa3-108">Popis</span><span class="sxs-lookup"><span data-stu-id="0efa3-108">Description</span></span>

<span data-ttu-id="0efa3-109">`dotnet test`Příkaz slouží ke spuštění testů jednotek v daném řešení.</span><span class="sxs-lookup"><span data-stu-id="0efa3-109">The `dotnet test` command is used to execute unit tests in a given solution.</span></span> <span data-ttu-id="0efa3-110">Příkaz sestaví `dotnet test` řešení a spustí testovací hostitelskou aplikaci pro každý projekt testů v řešení.</span><span class="sxs-lookup"><span data-stu-id="0efa3-110">The `dotnet test` command builds the solution and runs a test host application for each test project in the solution.</span></span> <span data-ttu-id="0efa3-111">Testovací hostitel provede v daném projektu testy pomocí testovacího rozhraní, například: MSTest, NUnit nebo xUnit, a ohlásí úspěch nebo neúspěch každého testu.</span><span class="sxs-lookup"><span data-stu-id="0efa3-111">The test host executes tests in the given project using a test framework, for example: MSTest, NUnit, or xUnit, and reports the success or failure of each test.</span></span> <span data-ttu-id="0efa3-112">Pokud jsou všechny testy úspěšné, Test Runner vrátí 0 jako ukončovací kód; jinak, pokud nějaký test selže, vrátí 1.</span><span class="sxs-lookup"><span data-stu-id="0efa3-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span>

<span data-ttu-id="0efa3-113">Pro projekty zaměřené na více platforem jsou testy spouštěny pro každou cílovou architekturu.</span><span class="sxs-lookup"><span data-stu-id="0efa3-113">For multi-targeted projects, tests are run for each targeted framework.</span></span> <span data-ttu-id="0efa3-114">Testovací hostitel a testovací rozhraní jednotky jsou zabaleny jako balíčky NuGet a jsou obnoveny jako běžné závislosti pro projekt.</span><span class="sxs-lookup"><span data-stu-id="0efa3-114">The test host and the unit test framework are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="0efa3-115">Projekty testů určují testovací spouštěč pomocí obyčejného `<PackageReference>` prvku, jak je vidět v následujícím ukázkovém souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="0efa3-115">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

<span data-ttu-id="0efa3-116">Kde `Microsoft.NET.Test.Sdk` je testovací hostitel, `xunit` je testovací rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0efa3-116">Where `Microsoft.NET.Test.Sdk` is the test host, `xunit` is the test framework.</span></span> <span data-ttu-id="0efa3-117">A `xunit.runner.visualstudio` je testovací adaptér, který umožňuje, aby architektura xUnit spolupracovala s testovacím hostitelem.</span><span class="sxs-lookup"><span data-stu-id="0efa3-117">And `xunit.runner.visualstudio` is a test adapter, which allows the xUnit framework to work with the test host.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="0efa3-118">Implicitní obnovení</span><span class="sxs-lookup"><span data-stu-id="0efa3-118">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="0efa3-119">Arguments</span><span class="sxs-lookup"><span data-stu-id="0efa3-119">Arguments</span></span>

- **`PROJECT | SOLUTION | DIRECTORY | DLL`**

  - <span data-ttu-id="0efa3-120">Cesta k testovacímu projektu.</span><span class="sxs-lookup"><span data-stu-id="0efa3-120">Path to the test project.</span></span>
  - <span data-ttu-id="0efa3-121">Cesta k řešení</span><span class="sxs-lookup"><span data-stu-id="0efa3-121">Path to the solution.</span></span>
  - <span data-ttu-id="0efa3-122">Cesta k adresáři, který obsahuje projekt nebo řešení.</span><span class="sxs-lookup"><span data-stu-id="0efa3-122">Path to a directory that contains a project or a solution.</span></span>
  - <span data-ttu-id="0efa3-123">Cesta k souboru projektu testů *. dll* .</span><span class="sxs-lookup"><span data-stu-id="0efa3-123">Path to a test project *.dll* file.</span></span>

  <span data-ttu-id="0efa3-124">Pokud není zadán, vyhledá projekt nebo řešení v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="0efa3-124">If not specified, it searches for a project or a solution in the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="0efa3-125">Možnosti</span><span class="sxs-lookup"><span data-stu-id="0efa3-125">Options</span></span>

- **`-a|--test-adapter-path <ADAPTER_PATH>`**

  <span data-ttu-id="0efa3-126">Cesta k adresáři, ve kterém se mají hledat další testovací adaptéry</span><span class="sxs-lookup"><span data-stu-id="0efa3-126">Path to a directory to be searched for additional test adapters.</span></span> <span data-ttu-id="0efa3-127">Jsou zkontrolovány pouze soubory *DLL* s příponou `.TestAdapter.dll` .</span><span class="sxs-lookup"><span data-stu-id="0efa3-127">Only *.dll* files with suffix `.TestAdapter.dll` are inspected.</span></span> <span data-ttu-id="0efa3-128">Pokud není zadán, bude prohledán adresář souboru Test *. dll* .</span><span class="sxs-lookup"><span data-stu-id="0efa3-128">If not specified, the directory of the test *.dll* is searched.</span></span>

- **`--blame`**

  <span data-ttu-id="0efa3-129">Spustí testy v režimu viny.</span><span class="sxs-lookup"><span data-stu-id="0efa3-129">Runs the tests in blame mode.</span></span> <span data-ttu-id="0efa3-130">Tato možnost je užitečná při izolaci problematických testů, které způsobují selhání hostitele testu.</span><span class="sxs-lookup"><span data-stu-id="0efa3-130">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="0efa3-131">Při zjištění chyby vytvoří soubor sekvence v `TestResults/<Guid>/<Guid>_Sequence.xml` , který zachytí pořadí testů, které byly spuštěny před selháním.</span><span class="sxs-lookup"><span data-stu-id="0efa3-131">When a crash is detected, it creates a sequence file in `TestResults/<Guid>/<Guid>_Sequence.xml` that captures the order of tests that were run before the crash.</span></span>

- <span data-ttu-id="0efa3-132">**`--blame-crash`** (K dispozici od verze .NET 5,0 Preview SDK)</span><span class="sxs-lookup"><span data-stu-id="0efa3-132">**`--blame-crash`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="0efa3-133">Spustí testy v režimu viny a shromažďuje stav systému, když se testovací hostitel neočekávaně ukončí.</span><span class="sxs-lookup"><span data-stu-id="0efa3-133">Runs the tests in blame mode and collects a crash dump when the test host exits unexpectedly.</span></span> <span data-ttu-id="0efa3-134">Tato možnost je podporována pouze v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="0efa3-134">This option is only supported on Windows.</span></span> <span data-ttu-id="0efa3-135">Adresář, který obsahuje *procdump.exe* a *procdump64.exe* musí být v cestě nebo v proměnné prostředí PROCDUMP_PATH.</span><span class="sxs-lookup"><span data-stu-id="0efa3-135">A directory that contains *procdump.exe* and *procdump64.exe* must be in the PATH or PROCDUMP_PATH environment variable.</span></span> <span data-ttu-id="0efa3-136">[Stáhněte si nástroje](https://docs.microsoft.com/sysinternals/downloads/procdump).</span><span class="sxs-lookup"><span data-stu-id="0efa3-136">[Download the tools](https://docs.microsoft.com/sysinternals/downloads/procdump).</span></span> <span data-ttu-id="0efa3-137">Implikuje `--blame` .</span><span class="sxs-lookup"><span data-stu-id="0efa3-137">Implies `--blame`.</span></span>

- <span data-ttu-id="0efa3-138">**`--blame-crash-dump-type <DUMP_TYPE>`** (K dispozici od verze .NET 5,0 Preview SDK)</span><span class="sxs-lookup"><span data-stu-id="0efa3-138">**`--blame-crash-dump-type <DUMP_TYPE>`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="0efa3-139">Typ výpisu stavu systému, který se má shromáždit.</span><span class="sxs-lookup"><span data-stu-id="0efa3-139">The type of crash dump to be collected.</span></span> <span data-ttu-id="0efa3-140">Implikuje `--blame-crash` .</span><span class="sxs-lookup"><span data-stu-id="0efa3-140">Implies `--blame-crash`.</span></span>

- <span data-ttu-id="0efa3-141">**`--blame-crash-collect-always`** (K dispozici od verze .NET 5,0 Preview SDK)</span><span class="sxs-lookup"><span data-stu-id="0efa3-141">**`--blame-crash-collect-always`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="0efa3-142">Shromažďuje výpis stavu systému podle očekávání a také neočekávaný konec testovacího hostitele.</span><span class="sxs-lookup"><span data-stu-id="0efa3-142">Collects a crash dump on expected as well as unexpected test host exit.</span></span>

- <span data-ttu-id="0efa3-143">**`--blame-hang`** (K dispozici od verze .NET 5,0 Preview SDK)</span><span class="sxs-lookup"><span data-stu-id="0efa3-143">**`--blame-hang`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="0efa3-144">Spusťte testy v režimu viny a shromáždí výpis stavu zablokování, když test překročí daný časový limit.</span><span class="sxs-lookup"><span data-stu-id="0efa3-144">Run the tests in blame mode and collects a hang dump when a test exceeds the given timeout.</span></span>

- <span data-ttu-id="0efa3-145">**`--blame-hang-dump-type <DUMP_TYPE>`** (K dispozici od verze .NET 5,0 Preview SDK)</span><span class="sxs-lookup"><span data-stu-id="0efa3-145">**`--blame-hang-dump-type <DUMP_TYPE>`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="0efa3-146">Typ výpisu stavu systému, který se má shromáždit.</span><span class="sxs-lookup"><span data-stu-id="0efa3-146">The type of crash dump to be collected.</span></span> <span data-ttu-id="0efa3-147">Mělo by to být `full` , `mini` , nebo `none` .</span><span class="sxs-lookup"><span data-stu-id="0efa3-147">It should be `full`, `mini`, or `none`.</span></span> <span data-ttu-id="0efa3-148">Je `none` -li parametr zadán, je test hostitele ukončen po vypršení časového limitu, ale není shromažďován žádný výpis.</span><span class="sxs-lookup"><span data-stu-id="0efa3-148">When `none` is specified, test host is terminated on timeout, but no dump is collected.</span></span> <span data-ttu-id="0efa3-149">Implikuje `--blame-hang` .</span><span class="sxs-lookup"><span data-stu-id="0efa3-149">Implies `--blame-hang`.</span></span>

- <span data-ttu-id="0efa3-150">**`--blame-hang-timeout <TIMESPAN>`** (K dispozici od verze .NET 5,0 Preview SDK)</span><span class="sxs-lookup"><span data-stu-id="0efa3-150">**`--blame-hang-timeout <TIMESPAN>`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="0efa3-151">Časový limit pro testování, po kterém se aktivuje výpis stavu zablokování a proces testovacího hostitele se ukončí.</span><span class="sxs-lookup"><span data-stu-id="0efa3-151">Per-test timeout, after which a hang dump is triggered and the test host process is terminated.</span></span> <span data-ttu-id="0efa3-152">Hodnota časového limitu je zadána v jednom z následujících formátů:</span><span class="sxs-lookup"><span data-stu-id="0efa3-152">The timeout value is specified in one of the following formats:</span></span>
  
  - <span data-ttu-id="0efa3-153">1,5 h</span><span class="sxs-lookup"><span data-stu-id="0efa3-153">1.5h</span></span>
  - <span data-ttu-id="0efa3-154">90 miliónů</span><span class="sxs-lookup"><span data-stu-id="0efa3-154">90m</span></span>
  - <span data-ttu-id="0efa3-155">5400</span><span class="sxs-lookup"><span data-stu-id="0efa3-155">5400s</span></span>
  - <span data-ttu-id="0efa3-156">5400000ms</span><span class="sxs-lookup"><span data-stu-id="0efa3-156">5400000ms</span></span>

  <span data-ttu-id="0efa3-157">Pokud se nepoužívá žádná jednotka (například 5400000), předpokládá se, že hodnota je v milisekundách.</span><span class="sxs-lookup"><span data-stu-id="0efa3-157">When no unit is used (for example, 5400000), the value is assumed to be in milliseconds.</span></span> <span data-ttu-id="0efa3-158">Při použití společně s testy řízenými daty závisí časový limit na použitém testovacím adaptéru.</span><span class="sxs-lookup"><span data-stu-id="0efa3-158">When used together with data driven tests, the timeout behavior depends on the test adapter used.</span></span> <span data-ttu-id="0efa3-159">Pro xUnit a NUnit se po každém testovacím případu obnoví časový limit.</span><span class="sxs-lookup"><span data-stu-id="0efa3-159">For xUnit and NUnit the timeout is renewed after every test case.</span></span> <span data-ttu-id="0efa3-160">Pro MSTest se používá časový limit pro všechny testovací případy.</span><span class="sxs-lookup"><span data-stu-id="0efa3-160">For MSTest, the timeout is used for all test cases.</span></span> <span data-ttu-id="0efa3-161">Tato možnost je podporovaná ve Windows s netcoreapp 2.1 a novějším a v systému Linux s netcoreapp 3.1 a novějším.</span><span class="sxs-lookup"><span data-stu-id="0efa3-161">This option is supported on Windows with netcoreapp2.1 and later, and on Linux with netcoreapp3.1 and later.</span></span> <span data-ttu-id="0efa3-162">macOS se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="0efa3-162">macOS is not supported.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="0efa3-163">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="0efa3-163">Defines the build configuration.</span></span> <span data-ttu-id="0efa3-164">Výchozí hodnota je `Debug` , ale konfigurace vašeho projektu může přepsat toto výchozí nastavení sady SDK.</span><span class="sxs-lookup"><span data-stu-id="0efa3-164">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`--collect <DATA_COLLECTOR_NAME>`**

  <span data-ttu-id="0efa3-165">Povolí shromažďování dat pro testovací běh.</span><span class="sxs-lookup"><span data-stu-id="0efa3-165">Enables data collector for the test run.</span></span> <span data-ttu-id="0efa3-166">Další informace najdete v tématu [monitorování a analýza testovacího běhu](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="0efa3-166">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>
  
  <span data-ttu-id="0efa3-167">Chcete-li shromáždit pokrytí kódu na jakékoli platformě, která je podporována rozhraním .NET Core, nainstalujte [Coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/README.md) a použijte `--collect:"XPlat Code Coverage"` možnost.</span><span class="sxs-lookup"><span data-stu-id="0efa3-167">To collect code coverage on any platform that is supported by .NET Core, install [Coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/README.md) and use the `--collect:"XPlat Code Coverage"` option.</span></span>

  <span data-ttu-id="0efa3-168">Ve Windows můžete pokrytí kódu shromažďovat pomocí `--collect "Code Coverage"` Možnosti.</span><span class="sxs-lookup"><span data-stu-id="0efa3-168">On Windows, you can collect code coverage by using the `--collect "Code Coverage"` option.</span></span> <span data-ttu-id="0efa3-169">Tato možnost vygeneruje soubor *. pokrytí* , který lze otevřít v aplikaci Visual Studio 2019 Enterprise.</span><span class="sxs-lookup"><span data-stu-id="0efa3-169">This option generates a *.coverage* file, which can be opened in Visual Studio 2019 Enterprise.</span></span> <span data-ttu-id="0efa3-170">Další informace najdete v tématu [Použití pokrytí kódu](/visualstudio/test/using-code-coverage-to-determine-how-much-code-is-being-tested) a [přizpůsobení analýzy pokrytí kódu](/visualstudio/test/customizing-code-coverage-analysis).</span><span class="sxs-lookup"><span data-stu-id="0efa3-170">For more information, see [Use code coverage](/visualstudio/test/using-code-coverage-to-determine-how-much-code-is-being-tested) and [Customize code coverage analysis](/visualstudio/test/customizing-code-coverage-analysis).</span></span>

- **`-d|--diag <LOG_FILE>`**

  <span data-ttu-id="0efa3-171">Povolí diagnostický režim pro testovací platformu a zapisuje diagnostické zprávy do zadaného souboru a do souborů vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="0efa3-171">Enables diagnostic mode for the test platform and writes diagnostic messages to the specified file and to files next to it.</span></span> <span data-ttu-id="0efa3-172">Proces, který zaznamenává zprávy, určuje, které soubory jsou vytvořeny, například `*.host_<date>.txt` pro protokol testu hostitele a `*.datacollector_<date>.txt` protokol sběru dat.</span><span class="sxs-lookup"><span data-stu-id="0efa3-172">The process that is logging the messages determines which files are created, such as `*.host_<date>.txt` for test host log, and `*.datacollector_<date>.txt` for data collector log.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="0efa3-173">Vynutí použití `dotnet` nebo .NET Framework testovacího hostitele pro binární soubory testu.</span><span class="sxs-lookup"><span data-stu-id="0efa3-173">Forces the use of `dotnet` or .NET Framework test host for the test binaries.</span></span> <span data-ttu-id="0efa3-174">Tato možnost určuje pouze typ hostitele, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="0efa3-174">This option only determines which type of host to use.</span></span> <span data-ttu-id="0efa3-175">Skutečná verze rozhraní, která se má použít, je určená *runtimeconfig.jsna* testovacím projektu.</span><span class="sxs-lookup"><span data-stu-id="0efa3-175">The actual framework version to be used is determined by the *runtimeconfig.json* of the test project.</span></span> <span data-ttu-id="0efa3-176">Pokud není zadaný, použije se k určení typu hostitele [atribut pro sestavení targetFramework](/dotnet/api/system.runtime.versioning.targetframeworkattribute) .</span><span class="sxs-lookup"><span data-stu-id="0efa3-176">When not specified, the [TargetFramework assembly attribute](/dotnet/api/system.runtime.versioning.targetframeworkattribute) is used to determine the type of host.</span></span> <span data-ttu-id="0efa3-177">Když je tento atribut ze souboru *. dll*odstraněn, je použit hostitel .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0efa3-177">When that attribute is stripped from the *.dll*, the .NET Framework host is used.</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="0efa3-178">Odfiltruje testy v aktuálním projektu pomocí daného výrazu.</span><span class="sxs-lookup"><span data-stu-id="0efa3-178">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="0efa3-179">Další informace najdete v části [Podrobnosti o možnosti filtru](#filter-option-details) .</span><span class="sxs-lookup"><span data-stu-id="0efa3-179">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="0efa3-180">Další informace a příklady použití selektivního filtrování testů jednotek naleznete v tématu [spuštění selektivních testů jednotek](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="0efa3-180">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="0efa3-181">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="0efa3-181">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="0efa3-182">Umožňuje zastavení příkazu zastavit a počkat na vstup nebo akci uživatele.</span><span class="sxs-lookup"><span data-stu-id="0efa3-182">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="0efa3-183">Například k dokončení ověřování.</span><span class="sxs-lookup"><span data-stu-id="0efa3-183">For example, to complete authentication.</span></span> <span data-ttu-id="0efa3-184">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="0efa3-184">Available since .NET Core 3.0 SDK.</span></span>

- **`-l|--logger <LOGGER>`**

  <span data-ttu-id="0efa3-185">Určuje protokolovací nástroj pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="0efa3-185">Specifies a logger for test results.</span></span> <span data-ttu-id="0efa3-186">Na rozdíl od MSBuild test dotnet nepřijímá zkratky: místo `-l "console;v=d"` použití `-l "console;verbosity=detailed"` .</span><span class="sxs-lookup"><span data-stu-id="0efa3-186">Unlike MSBuild, dotnet test doesn't accept abbreviations: instead of `-l "console;v=d"` use `-l "console;verbosity=detailed"`.</span></span>

- **`--no-build`**

  <span data-ttu-id="0efa3-187">Před spuštěním nevytvoří testovací projekt.</span><span class="sxs-lookup"><span data-stu-id="0efa3-187">Doesn't build the test project before running it.</span></span> <span data-ttu-id="0efa3-188">Také implicitně nastaví `--no-restore` příznak-.</span><span class="sxs-lookup"><span data-stu-id="0efa3-188">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="0efa3-189">Spusťte testy bez zobrazení banneru Microsoft TestPlatform.</span><span class="sxs-lookup"><span data-stu-id="0efa3-189">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="0efa3-190">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="0efa3-190">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="0efa3-191">Při spuštění příkazu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="0efa3-191">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="0efa3-192">Adresář, ve kterém se mají najít binární soubory, které se mají spustit.</span><span class="sxs-lookup"><span data-stu-id="0efa3-192">Directory in which to find the binaries to run.</span></span> <span data-ttu-id="0efa3-193">Pokud není zadaný, použije se výchozí cesta `./bin/<configuration>/<framework>/` .</span><span class="sxs-lookup"><span data-stu-id="0efa3-193">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="0efa3-194">Pro projekty s více cílovými rozhraními (prostřednictvím `TargetFrameworks` Vlastnosti) musíte definovat i `--framework` při zadání této možnosti.</span><span class="sxs-lookup"><span data-stu-id="0efa3-194">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span> <span data-ttu-id="0efa3-195">`dotnet test` vždy spouští testy z výstupního adresáře.</span><span class="sxs-lookup"><span data-stu-id="0efa3-195">`dotnet test` always runs tests from the output directory.</span></span> <span data-ttu-id="0efa3-196">Můžete použít <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> pro využívání testovacích prostředků ve výstupním adresáři.</span><span class="sxs-lookup"><span data-stu-id="0efa3-196">You can use <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> to consume test assets in the output directory.</span></span>

- **`-r|--results-directory <RESULTS_DIR>`**

  <span data-ttu-id="0efa3-197">Adresář, do kterého budou umístěny výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="0efa3-197">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="0efa3-198">Pokud zadaný adresář neexistuje, vytvoří se.</span><span class="sxs-lookup"><span data-stu-id="0efa3-198">If the specified directory doesn't exist, it's created.</span></span> <span data-ttu-id="0efa3-199">Výchozí hodnota je `TestResults` v adresáři, který obsahuje soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="0efa3-199">The default is `TestResults` in the directory that contains the project file.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="0efa3-200">Cílový modul runtime, pro který se má testovat.</span><span class="sxs-lookup"><span data-stu-id="0efa3-200">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="0efa3-201">`.runsettings`Soubor, který se má použít pro spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="0efa3-201">The `.runsettings` file to use for running the tests.</span></span> <span data-ttu-id="0efa3-202">`TargetPlatform`Element (x86 | x64) nemá žádný vliv na `dotnet test` .</span><span class="sxs-lookup"><span data-stu-id="0efa3-202">The `TargetPlatform` element (x86|x64) has no effect for `dotnet test`.</span></span> <span data-ttu-id="0efa3-203">Chcete-li spustit testy, které cílí na x86, nainstalujte verzi x86 rozhraní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0efa3-203">To run tests that target x86, install the x86 version of .NET Core.</span></span> <span data-ttu-id="0efa3-204">Bitová verze *dotnet.exe* , která se nachází na cestě, je to, co se použije ke spouštění testů.</span><span class="sxs-lookup"><span data-stu-id="0efa3-204">The bitness of the *dotnet.exe* that is on the path is what will be used for running tests.</span></span> <span data-ttu-id="0efa3-205">Další informace naleznete v následujících zdrojích:</span><span class="sxs-lookup"><span data-stu-id="0efa3-205">For more information, see the following resources:</span></span>

  - [<span data-ttu-id="0efa3-206">Nakonfigurujte testy jednotek pomocí `.runsettings` souboru.</span><span class="sxs-lookup"><span data-stu-id="0efa3-206">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)
  - [<span data-ttu-id="0efa3-207">Konfigurace testovacího běhu</span><span class="sxs-lookup"><span data-stu-id="0efa3-207">Configure a test run</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/configure.md)

- **`-t|--list-tests`**

  <span data-ttu-id="0efa3-208">Vypíše zjištěné testy místo spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="0efa3-208">List the discovered tests instead of running the tests.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="0efa3-209">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="0efa3-209">Sets the verbosity level of the command.</span></span> <span data-ttu-id="0efa3-210">Povolené hodnoty jsou `q[uiet]` , `m[inimal]` ,, a `n[ormal]` `d[etailed]` `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="0efa3-210">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="0efa3-211">Výchozí formát je `minimal`.</span><span class="sxs-lookup"><span data-stu-id="0efa3-211">The default is `minimal`.</span></span> <span data-ttu-id="0efa3-212">Další informace naleznete v tématu <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span><span class="sxs-lookup"><span data-stu-id="0efa3-212">For more information, see <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span></span>

- <span data-ttu-id="0efa3-213">**`RunSettings`** náhodné</span><span class="sxs-lookup"><span data-stu-id="0efa3-213">**`RunSettings`** arguments</span></span>

 <span data-ttu-id="0efa3-214">Inline `RunSettings` se předávají jako poslední argumenty příkazového řádku za znakem "--" (Všimněte si místa za-).</span><span class="sxs-lookup"><span data-stu-id="0efa3-214">Inline `RunSettings` are passed as the last arguments on the command line after "-- " (note the space after --).</span></span> <span data-ttu-id="0efa3-215">`RunSettings`Jako páry jsou zadány vložené `[name]=[value]` .</span><span class="sxs-lookup"><span data-stu-id="0efa3-215">Inline `RunSettings` are specified as `[name]=[value]` pairs.</span></span> <span data-ttu-id="0efa3-216">K oddělení více párů se používá mezera `[name]=[value]` .</span><span class="sxs-lookup"><span data-stu-id="0efa3-216">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="0efa3-217">Příklad: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="0efa3-217">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="0efa3-218">Další informace najdete v tématu [předávání argumentů runsettings pomocí příkazového řádku](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="0efa3-218">For more information, see [Passing RunSettings arguments through command line](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="0efa3-219">Příklady</span><span class="sxs-lookup"><span data-stu-id="0efa3-219">Examples</span></span>

- <span data-ttu-id="0efa3-220">Spustit testy v projektu v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="0efa3-220">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="0efa3-221">Spustit testy v `test1` projektu:</span><span class="sxs-lookup"><span data-stu-id="0efa3-221">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="0efa3-222">Spusťte testy v projektu v aktuálním adresáři a vygenerujte soubor výsledků testů ve formátu TRX:</span><span class="sxs-lookup"><span data-stu-id="0efa3-222">Run the tests in the project in the current directory, and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

- <span data-ttu-id="0efa3-223">Spusťte testy v projektu v aktuálním adresáři a vygenerujte soubor pokrytí kódu (po instalaci integrace kolektorů [Coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/Documentation/VSTestIntegration.md) ):</span><span class="sxs-lookup"><span data-stu-id="0efa3-223">Run the tests in the project in the current directory, and generate a code coverage file (after installing [Coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/Documentation/VSTestIntegration.md) collectors integration):</span></span>

  ```dotnetcli
  dotnet test --collect:"XPlat Code Coverage"
  ```

- <span data-ttu-id="0efa3-224">Spusťte testy v projektu v aktuálním adresáři a vygenerujte soubor pokrytí kódu (pouze Windows):</span><span class="sxs-lookup"><span data-stu-id="0efa3-224">Run the tests in the project in the current directory, and generate a code coverage file (Windows only):</span></span>

  ```dotnetcli
  dotnet test --collect "Code Coverage"
  ```

- <span data-ttu-id="0efa3-225">Spusťte testy v projektu v aktuálním adresáři a log s detailní podrobností do konzoly:</span><span class="sxs-lookup"><span data-stu-id="0efa3-225">Run the tests in the project in the current directory, and log with detailed verbosity to the console:</span></span>

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```

- <span data-ttu-id="0efa3-226">Spusťte testy v projektu v aktuálním adresáři a Nahlášením testů, které probíhaly při selhání hostitele testu:</span><span class="sxs-lookup"><span data-stu-id="0efa3-226">Run the tests in the project in the current directory, and report tests that were in progress when the test host crashed:</span></span>

  ```dotnetcli
  dotnet test --blame
  ```

## <a name="filter-option-details"></a><span data-ttu-id="0efa3-227">Podrobnosti možnosti filtru</span><span class="sxs-lookup"><span data-stu-id="0efa3-227">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="0efa3-228">`<Expression>` má formát `<property><operator><value>[|&<Expression>]` .</span><span class="sxs-lookup"><span data-stu-id="0efa3-228">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="0efa3-229">`<property>` je atributem `Test Case` .</span><span class="sxs-lookup"><span data-stu-id="0efa3-229">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="0efa3-230">Níže jsou uvedené vlastnosti podporované oblíbenými rozhraními pro testování částí:</span><span class="sxs-lookup"><span data-stu-id="0efa3-230">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="0efa3-231">Testovací rozhraní</span><span class="sxs-lookup"><span data-stu-id="0efa3-231">Test Framework</span></span> | <span data-ttu-id="0efa3-232">Podporované vlastnosti</span><span class="sxs-lookup"><span data-stu-id="0efa3-232">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="0efa3-233">MSTest</span><span class="sxs-lookup"><span data-stu-id="0efa3-233">MSTest</span></span>         | <ul><li><span data-ttu-id="0efa3-234">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="0efa3-234">FullyQualifiedName</span></span></li><li><span data-ttu-id="0efa3-235">Název</span><span class="sxs-lookup"><span data-stu-id="0efa3-235">Name</span></span></li><li><span data-ttu-id="0efa3-236">NázevTřídy</span><span class="sxs-lookup"><span data-stu-id="0efa3-236">ClassName</span></span></li><li><span data-ttu-id="0efa3-237">Priorita</span><span class="sxs-lookup"><span data-stu-id="0efa3-237">Priority</span></span></li><li><span data-ttu-id="0efa3-238">TestCategory</span><span class="sxs-lookup"><span data-stu-id="0efa3-238">TestCategory</span></span></li></ul> |
| <span data-ttu-id="0efa3-239">xUnit</span><span class="sxs-lookup"><span data-stu-id="0efa3-239">xUnit</span></span>          | <ul><li><span data-ttu-id="0efa3-240">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="0efa3-240">FullyQualifiedName</span></span></li><li><span data-ttu-id="0efa3-241">DisplayName</span><span class="sxs-lookup"><span data-stu-id="0efa3-241">DisplayName</span></span></li><li><span data-ttu-id="0efa3-242">Traits</span><span class="sxs-lookup"><span data-stu-id="0efa3-242">Traits</span></span></li></ul>                                   |
| <span data-ttu-id="0efa3-243">NUnit</span><span class="sxs-lookup"><span data-stu-id="0efa3-243">NUnit</span></span>          | <ul><li><span data-ttu-id="0efa3-244">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="0efa3-244">FullyQualifiedName</span></span></li><li><span data-ttu-id="0efa3-245">Název</span><span class="sxs-lookup"><span data-stu-id="0efa3-245">Name</span></span></li><li><span data-ttu-id="0efa3-246">TestCategory</span><span class="sxs-lookup"><span data-stu-id="0efa3-246">TestCategory</span></span></li><li><span data-ttu-id="0efa3-247">Priorita</span><span class="sxs-lookup"><span data-stu-id="0efa3-247">Priority</span></span></li></ul>                                   |

<span data-ttu-id="0efa3-248">`<operator>`Popisuje vztah mezi vlastností a hodnotou:</span><span class="sxs-lookup"><span data-stu-id="0efa3-248">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="0efa3-249">Operátor</span><span class="sxs-lookup"><span data-stu-id="0efa3-249">Operator</span></span> | <span data-ttu-id="0efa3-250">Funkce</span><span class="sxs-lookup"><span data-stu-id="0efa3-250">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="0efa3-251">Přesná shoda</span><span class="sxs-lookup"><span data-stu-id="0efa3-251">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="0efa3-252">Nepřesná shoda</span><span class="sxs-lookup"><span data-stu-id="0efa3-252">Not exact match</span></span> |
| `~`      | <span data-ttu-id="0efa3-253">Contains</span><span class="sxs-lookup"><span data-stu-id="0efa3-253">Contains</span></span>        |
| `!~`     | <span data-ttu-id="0efa3-254">Neobsahuje</span><span class="sxs-lookup"><span data-stu-id="0efa3-254">Not contains</span></span>    |

<span data-ttu-id="0efa3-255">`<value>` je řetězec.</span><span class="sxs-lookup"><span data-stu-id="0efa3-255">`<value>` is a string.</span></span> <span data-ttu-id="0efa3-256">U všech hledání se nerozlišují malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="0efa3-256">All the lookups are case insensitive.</span></span>

<span data-ttu-id="0efa3-257">Výraz bez objektu `<operator>` je automaticky považován za `contains` `FullyQualifiedName` vlastnost on (například `dotnet test --filter xyz` je stejný jako `dotnet test --filter FullyQualifiedName~xyz` ).</span><span class="sxs-lookup"><span data-stu-id="0efa3-257">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="0efa3-258">Výrazy se dají spojit s podmíněnými operátory:</span><span class="sxs-lookup"><span data-stu-id="0efa3-258">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="0efa3-259">Operátor</span><span class="sxs-lookup"><span data-stu-id="0efa3-259">Operator</span></span>            | <span data-ttu-id="0efa3-260">Funkce</span><span class="sxs-lookup"><span data-stu-id="0efa3-260">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="0efa3-261">NEBO</span><span class="sxs-lookup"><span data-stu-id="0efa3-261">OR</span></span>       |
| `&`                 | <span data-ttu-id="0efa3-262">AND</span><span class="sxs-lookup"><span data-stu-id="0efa3-262">AND</span></span>      |

<span data-ttu-id="0efa3-263">Výrazy můžete uzavřít do závorek při použití podmíněných operátorů (například `(Name~TestMethod1) | (Name~TestMethod2)` ).</span><span class="sxs-lookup"><span data-stu-id="0efa3-263">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="0efa3-264">Další informace a příklady použití selektivního filtrování testů jednotek naleznete v tématu [spuštění selektivních testů jednotek](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="0efa3-264">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0efa3-265">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0efa3-265">See also</span></span>

- [<span data-ttu-id="0efa3-266">Architektury a cíle</span><span class="sxs-lookup"><span data-stu-id="0efa3-266">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="0efa3-267">Katalog identifikátorů runtime .NET Core (RID)</span><span class="sxs-lookup"><span data-stu-id="0efa3-267">.NET Core Runtime Identifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="0efa3-268">Předávání argumentů runsettings prostřednictvím příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="0efa3-268">Passing runsettings arguments through commandline</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
