---
title: "DotNet. příkaz test - .NET Core rozhraní příkazového řádku"
description: "Příkaz dotnet testu se používá k provedení testů jednotek v daný projekt."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 9eb5be38549711717c11767332bfc84920ea927a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="dotnet-test"></a><span data-ttu-id="f93c2-103">test DotNet.</span><span class="sxs-lookup"><span data-stu-id="f93c2-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="f93c2-104">Název</span><span class="sxs-lookup"><span data-stu-id="f93c2-104">Name</span></span>

<span data-ttu-id="f93c2-105">`dotnet test`-Ovladač test .NET použít ke spuštění testů jednotek.</span><span class="sxs-lookup"><span data-stu-id="f93c2-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f93c2-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="f93c2-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="f93c2-107">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="f93c2-107">.NET Core 2.x</span></span>](#tab/netcore2x)


```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="f93c2-108">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="f93c2-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]
dotnet test [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="f93c2-109">Popis</span><span class="sxs-lookup"><span data-stu-id="f93c2-109">Description</span></span>

<span data-ttu-id="f93c2-110">`dotnet test` Příkaz se používá k provedení testů jednotek v daný projekt.</span><span class="sxs-lookup"><span data-stu-id="f93c2-110">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="f93c2-111">Testy jednotek jsou projekty konzoly aplikace, které mají závislosti na jednotce test framework (například Mstestu, NUnit nebo xUnit) a nástroj test runner dotnet pro testování framework částí.</span><span class="sxs-lookup"><span data-stu-id="f93c2-111">Unit tests are console application projects that have dependencies on the unit test framework (for example, MSTest, NUnit, or xUnit) and the dotnet test runner for the unit testing framework.</span></span> <span data-ttu-id="f93c2-112">Tyto jsou zabaleny jako balíčky NuGet a se obnoví jako obyčejnou závislosti pro projekt.</span><span class="sxs-lookup"><span data-stu-id="f93c2-112">These are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="f93c2-113">Projektů testování musíte zadat také nástroj test runner.</span><span class="sxs-lookup"><span data-stu-id="f93c2-113">Test projects also must specify the test runner.</span></span> <span data-ttu-id="f93c2-114">Je to určeno, používá běžný `<PackageReference>` elementu, jak je vidět v následujícím souboru projektu vzorku:</span><span class="sxs-lookup"><span data-stu-id="f93c2-114">This is specified using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="f93c2-115">Arguments</span><span class="sxs-lookup"><span data-stu-id="f93c2-115">Arguments</span></span>

`PROJECT`

<span data-ttu-id="f93c2-116">Určuje cestu pro projekt test.</span><span class="sxs-lookup"><span data-stu-id="f93c2-116">Specifies a path to the test project.</span></span> <span data-ttu-id="f93c2-117">Při vynechání je použita k aktuálnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="f93c2-117">If omitted, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="f93c2-118">Možnosti</span><span class="sxs-lookup"><span data-stu-id="f93c2-118">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="f93c2-119">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="f93c2-119">.NET Core 2.x</span></span>](#tab/netcore2x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="f93c2-120">V testovacím běhu použijte vlastní test adaptéry ze zadané cesty.</span><span class="sxs-lookup"><span data-stu-id="f93c2-120">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="f93c2-121">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="f93c2-121">Defines the build configuration.</span></span> <span data-ttu-id="f93c2-122">Výchozí hodnota je `Debug`, ale konfigurace vašeho projektu může přepsat toto výchozí nastavení SDK.</span><span class="sxs-lookup"><span data-stu-id="f93c2-122">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="f93c2-123">Umožňuje kolekce dat pro test spustit.</span><span class="sxs-lookup"><span data-stu-id="f93c2-123">Enables data collector for the test run.</span></span> <span data-ttu-id="f93c2-124">Další informace najdete v tématu [monitorování a analyzovat testu](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="f93c2-124">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="f93c2-125">Umožňuje diagnostiky režimu pro testovací platformy a zápis diagnostické zprávy do určeného souboru.</span><span class="sxs-lookup"><span data-stu-id="f93c2-125">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="f93c2-126">Vyhledá testovací binární soubory pro konkrétní [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="f93c2-126">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="f93c2-127">Filtruje testy v aktuálním projektu pomocí daného výrazu.</span><span class="sxs-lookup"><span data-stu-id="f93c2-127">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="f93c2-128">Další informace najdete v tématu [filtrovat možnost Podrobnosti](#filter-option-details) části.</span><span class="sxs-lookup"><span data-stu-id="f93c2-128">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="f93c2-129">Další příklady a další informace o tom, jak pomocí filtrování testovací selektivní jednotky, najdete v části [spouštění testů jednotek selektivní](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="f93c2-129">For additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="f93c2-130">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="f93c2-130">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="f93c2-131">Určuje protokolovacího nástroje pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="f93c2-131">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="f93c2-132">Nelze sestavit k testovacímu projektu před jejím spuštěním.</span><span class="sxs-lookup"><span data-stu-id="f93c2-132">Does not build the test project prior to running it.</span></span>

`--no-restore`

<span data-ttu-id="f93c2-133">Neprovede implicitní obnovení, při spuštění příkazu.</span><span class="sxs-lookup"><span data-stu-id="f93c2-133">Doesn't perform an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="f93c2-134">Adresář, ve kterém chcete najít binární soubory ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="f93c2-134">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="f93c2-135">Adresář, kde se chystáte výsledky testů umístit.</span><span class="sxs-lookup"><span data-stu-id="f93c2-135">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="f93c2-136">Zadaný adresář bude vytvořen, pokud neexistuje.</span><span class="sxs-lookup"><span data-stu-id="f93c2-136">The specified directory will be created if it doesn't exist.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="f93c2-137">Nastavení se má použít při spouštění testů.</span><span class="sxs-lookup"><span data-stu-id="f93c2-137">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="f93c2-138">Seznam všech zjištěných testů v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="f93c2-138">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="f93c2-139">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="f93c2-139">Sets the verbosity level of the command.</span></span> <span data-ttu-id="f93c2-140">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="f93c2-140">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="f93c2-141">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="f93c2-141">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="f93c2-142">V testovacím běhu použijte vlastní test adaptéry ze zadané cesty.</span><span class="sxs-lookup"><span data-stu-id="f93c2-142">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="f93c2-143">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="f93c2-143">Defines the build configuration.</span></span> <span data-ttu-id="f93c2-144">Výchozí hodnota je `Debug`, ale konfigurace vašeho projektu může přepsat toto výchozí nastavení SDK.</span><span class="sxs-lookup"><span data-stu-id="f93c2-144">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="f93c2-145">Umožňuje diagnostiky režimu pro testovací platformy a zápis diagnostické zprávy do určeného souboru.</span><span class="sxs-lookup"><span data-stu-id="f93c2-145">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="f93c2-146">Vyhledá testovací binární soubory pro konkrétní [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="f93c2-146">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="f93c2-147">Filtruje testy v aktuálním projektu pomocí daného výrazu.</span><span class="sxs-lookup"><span data-stu-id="f93c2-147">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="f93c2-148">Další informace najdete v tématu [filtrovat možnost Podrobnosti](#filter-option-details) části.</span><span class="sxs-lookup"><span data-stu-id="f93c2-148">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="f93c2-149">Další příklady a další informace o tom, jak pomocí filtrování testovací selektivní jednotky, najdete v části [spouštění testů jednotek selektivní](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="f93c2-149">For additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="f93c2-150">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="f93c2-150">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="f93c2-151">Určuje protokolovacího nástroje pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="f93c2-151">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="f93c2-152">Nelze sestavit k testovacímu projektu před jejím spuštěním.</span><span class="sxs-lookup"><span data-stu-id="f93c2-152">Does not build the test project prior to running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="f93c2-153">Adresář, ve kterém chcete najít binární soubory ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="f93c2-153">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="f93c2-154">Nastavení se má použít při spouštění testů.</span><span class="sxs-lookup"><span data-stu-id="f93c2-154">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="f93c2-155">Seznam všech zjištěných testů v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="f93c2-155">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="f93c2-156">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="f93c2-156">Sets the verbosity level of the command.</span></span> <span data-ttu-id="f93c2-157">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="f93c2-157">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="f93c2-158">Příklady</span><span class="sxs-lookup"><span data-stu-id="f93c2-158">Examples</span></span>

<span data-ttu-id="f93c2-159">Spouštět testy v projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="f93c2-159">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="f93c2-160">Spouštět testy v `test1` projektu:</span><span class="sxs-lookup"><span data-stu-id="f93c2-160">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

## <a name="filter-option-details"></a><span data-ttu-id="f93c2-161">Podrobnosti o možnost filtru</span><span class="sxs-lookup"><span data-stu-id="f93c2-161">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="f93c2-162">`<Expression>`má formát `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="f93c2-162">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="f93c2-163">`<property>`je atributem `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="f93c2-163">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="f93c2-164">Tady jsou vlastnostech podporovaných zprostředkovatelem systémů testů jednotek oblíbených:</span><span class="sxs-lookup"><span data-stu-id="f93c2-164">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="f93c2-165">Test Framework</span><span class="sxs-lookup"><span data-stu-id="f93c2-165">Test Framework</span></span> | <span data-ttu-id="f93c2-166">Podporovaných vlastností</span><span class="sxs-lookup"><span data-stu-id="f93c2-166">Supported properties</span></span>                                                                                      |
| :------------: | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="f93c2-167">MSTest</span><span class="sxs-lookup"><span data-stu-id="f93c2-167">MSTest</span></span>         | <ul><li><span data-ttu-id="f93c2-168">Položka FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="f93c2-168">FullyQualifiedName</span></span></li><li><span data-ttu-id="f93c2-169">Název</span><span class="sxs-lookup"><span data-stu-id="f93c2-169">Name</span></span></li><li><span data-ttu-id="f93c2-170">Název třídy</span><span class="sxs-lookup"><span data-stu-id="f93c2-170">ClassName</span></span></li><li><span data-ttu-id="f93c2-171">Priorita</span><span class="sxs-lookup"><span data-stu-id="f93c2-171">Priority</span></span></li><li><span data-ttu-id="f93c2-172">TestCategory</span><span class="sxs-lookup"><span data-stu-id="f93c2-172">TestCategory</span></span></li></ul> |
| <span data-ttu-id="f93c2-173">xunit</span><span class="sxs-lookup"><span data-stu-id="f93c2-173">Xunit</span></span>          | <ul><li><span data-ttu-id="f93c2-174">Položka FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="f93c2-174">FullyQualifiedName</span></span></li><li><span data-ttu-id="f93c2-175">displayName</span><span class="sxs-lookup"><span data-stu-id="f93c2-175">DisplayName</span></span></li><li><span data-ttu-id="f93c2-176">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="f93c2-176">Traits</span></span></li></ul>                                   |

<span data-ttu-id="f93c2-177">`<operator>` Popisuje vztah mezi vlastnosti a hodnotu:</span><span class="sxs-lookup"><span data-stu-id="f93c2-177">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="f93c2-178">Operátor</span><span class="sxs-lookup"><span data-stu-id="f93c2-178">Operator</span></span> | <span data-ttu-id="f93c2-179">Funkce</span><span class="sxs-lookup"><span data-stu-id="f93c2-179">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="f93c2-180">Přesná shoda</span><span class="sxs-lookup"><span data-stu-id="f93c2-180">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="f93c2-181">Není přesná shoda</span><span class="sxs-lookup"><span data-stu-id="f93c2-181">Not exact match</span></span> |
| `~`      | <span data-ttu-id="f93c2-182">Obsahuje</span><span class="sxs-lookup"><span data-stu-id="f93c2-182">Contains</span></span>        |

<span data-ttu-id="f93c2-183">`<value>`obsahuje řetězec.</span><span class="sxs-lookup"><span data-stu-id="f93c2-183">`<value>` is a string.</span></span> <span data-ttu-id="f93c2-184">Všechny hledání se malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="f93c2-184">All the lookups are case insensitive.</span></span>

<span data-ttu-id="f93c2-185">Výraz bez `<operator>` je automaticky považováno za `contains` na `FullyQualifiedName` vlastnosti (například `dotnet test --filter xyz` je stejný jako `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="f93c2-185">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="f93c2-186">Výrazy lze spojit s podmíněné operátory:</span><span class="sxs-lookup"><span data-stu-id="f93c2-186">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="f93c2-187">Operátor</span><span class="sxs-lookup"><span data-stu-id="f93c2-187">Operator</span></span> | <span data-ttu-id="f93c2-188">Funkce</span><span class="sxs-lookup"><span data-stu-id="f93c2-188">Function</span></span> |
| :------: | :------: |
| <code>&#124;</code>      | <span data-ttu-id="f93c2-189">NEBO</span><span class="sxs-lookup"><span data-stu-id="f93c2-189">OR</span></span>       |
| `&`      | <span data-ttu-id="f93c2-190">AND</span><span class="sxs-lookup"><span data-stu-id="f93c2-190">AND</span></span>      |

<span data-ttu-id="f93c2-191">Můžete uzavřete výrazy v závorkách, při použití podmíněné operátory (například `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="f93c2-191">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="f93c2-192">Další příklady a další informace o tom, jak pomocí filtrování testovací selektivní jednotky, najdete v části [spouštění testů jednotek selektivní](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="f93c2-192">For additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f93c2-193">Viz také</span><span class="sxs-lookup"><span data-stu-id="f93c2-193">See also</span></span>

 [<span data-ttu-id="f93c2-194">Rozhraní a cíle</span><span class="sxs-lookup"><span data-stu-id="f93c2-194">Frameworks and Targets</span></span>](../../standard/frameworks.md)  
 [<span data-ttu-id="f93c2-195">Katalog .NET core Runtime identifikátor (RID)</span><span class="sxs-lookup"><span data-stu-id="f93c2-195">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
