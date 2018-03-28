---
title: DotNet. příkaz test - .NET Core rozhraní příkazového řádku
description: Příkaz dotnet testu se používá k provedení testů jednotek v daný projekt.
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 6102281c4daf149f31e65ef8360831fe9e0ef4f6
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2018
---
# <a name="dotnet-test"></a><span data-ttu-id="6beca-103">test DotNet.</span><span class="sxs-lookup"><span data-stu-id="6beca-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="6beca-104">Název</span><span class="sxs-lookup"><span data-stu-id="6beca-104">Name</span></span>

<span data-ttu-id="6beca-105">`dotnet test` -Ovladač test .NET použít ke spuštění testů jednotek.</span><span class="sxs-lookup"><span data-stu-id="6beca-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="6beca-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="6beca-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="6beca-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="6beca-107">.NET Core 2.x</span></span>](#tab/netcore2x)


```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6beca-108">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="6beca-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]
dotnet test [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="6beca-109">Popis</span><span class="sxs-lookup"><span data-stu-id="6beca-109">Description</span></span>

<span data-ttu-id="6beca-110">`dotnet test` Příkaz se používá k provedení testů jednotek v daný projekt.</span><span class="sxs-lookup"><span data-stu-id="6beca-110">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="6beca-111">`dotnet test` Příkaz spustí zadaný pro projekt test runner konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="6beca-111">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="6beca-112">Nástroj test runner provede testů definovaných pro systém testování částí (například Mstestu, NUnit nebo xUnit) a oznámí úspěšné nebo neúspěšné každého testu.</span><span class="sxs-lookup"><span data-stu-id="6beca-112">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="6beca-113">Nástroj test runner a knihovně test jednotky spojených jako balíčků NuGet a se obnoví jako obyčejnou závislosti pro projekt.</span><span class="sxs-lookup"><span data-stu-id="6beca-113">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="6beca-114">Nástroj test runner pomocí běžný zadejte projektů testování `<PackageReference>` elementu, jak je vidět v následujícím souboru projektu vzorku:</span><span class="sxs-lookup"><span data-stu-id="6beca-114">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="6beca-115">Arguments</span><span class="sxs-lookup"><span data-stu-id="6beca-115">Arguments</span></span>

`PROJECT`

<span data-ttu-id="6beca-116">Určuje cestu pro projekt test.</span><span class="sxs-lookup"><span data-stu-id="6beca-116">Specifies a path to the test project.</span></span> <span data-ttu-id="6beca-117">Při vynechání je použita k aktuálnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="6beca-117">If omitted, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="6beca-118">Možnosti</span><span class="sxs-lookup"><span data-stu-id="6beca-118">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="6beca-119">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="6beca-119">.NET Core 2.x</span></span>](#tab/netcore2x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="6beca-120">V testovacím běhu použijte vlastní test adaptéry ze zadané cesty.</span><span class="sxs-lookup"><span data-stu-id="6beca-120">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="6beca-121">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="6beca-121">Defines the build configuration.</span></span> <span data-ttu-id="6beca-122">Výchozí hodnota je `Debug`, ale konfigurace vašeho projektu může přepsat toto výchozí nastavení SDK.</span><span class="sxs-lookup"><span data-stu-id="6beca-122">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="6beca-123">Umožňuje kolekce dat pro test spustit.</span><span class="sxs-lookup"><span data-stu-id="6beca-123">Enables data collector for the test run.</span></span> <span data-ttu-id="6beca-124">Další informace najdete v tématu [monitorování a analyzovat testu](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="6beca-124">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="6beca-125">Umožňuje diagnostiky režimu pro testovací platformy a zápis diagnostické zprávy do určeného souboru.</span><span class="sxs-lookup"><span data-stu-id="6beca-125">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="6beca-126">Vyhledá testovací binární soubory pro konkrétní [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="6beca-126">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="6beca-127">Filtruje testy v aktuálním projektu pomocí daného výrazu.</span><span class="sxs-lookup"><span data-stu-id="6beca-127">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="6beca-128">Další informace najdete v tématu [filtrovat možnost Podrobnosti](#filter-option-details) části.</span><span class="sxs-lookup"><span data-stu-id="6beca-128">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="6beca-129">Další příklady a další informace o tom, jak pomocí filtrování testovací selektivní jednotky, najdete v části [spouštění testů jednotek selektivní](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="6beca-129">For additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="6beca-130">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="6beca-130">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="6beca-131">Určuje protokolovacího nástroje pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="6beca-131">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="6beca-132">Nelze sestavit k testovacímu projektu před jejím spuštěním.</span><span class="sxs-lookup"><span data-stu-id="6beca-132">Does not build the test project prior to running it.</span></span>

`--no-restore`

<span data-ttu-id="6beca-133">Neprovede implicitní obnovení, při spuštění příkazu.</span><span class="sxs-lookup"><span data-stu-id="6beca-133">Doesn't perform an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="6beca-134">Adresář, ve kterém chcete najít binární soubory ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="6beca-134">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="6beca-135">Adresář, kde se chystáte výsledky testů umístit.</span><span class="sxs-lookup"><span data-stu-id="6beca-135">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="6beca-136">Zadaný adresář bude vytvořen, pokud neexistuje.</span><span class="sxs-lookup"><span data-stu-id="6beca-136">The specified directory will be created if it doesn't exist.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="6beca-137">Nastavení se má použít při spouštění testů.</span><span class="sxs-lookup"><span data-stu-id="6beca-137">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="6beca-138">Seznam všech zjištěných testů v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="6beca-138">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="6beca-139">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="6beca-139">Sets the verbosity level of the command.</span></span> <span data-ttu-id="6beca-140">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="6beca-140">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6beca-141">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="6beca-141">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="6beca-142">V testovacím běhu použijte vlastní test adaptéry ze zadané cesty.</span><span class="sxs-lookup"><span data-stu-id="6beca-142">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="6beca-143">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="6beca-143">Defines the build configuration.</span></span> <span data-ttu-id="6beca-144">Výchozí hodnota je `Debug`, ale konfigurace vašeho projektu může přepsat toto výchozí nastavení SDK.</span><span class="sxs-lookup"><span data-stu-id="6beca-144">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="6beca-145">Umožňuje diagnostiky režimu pro testovací platformy a zápis diagnostické zprávy do určeného souboru.</span><span class="sxs-lookup"><span data-stu-id="6beca-145">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="6beca-146">Vyhledá testovací binární soubory pro konkrétní [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="6beca-146">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="6beca-147">Filtruje testy v aktuálním projektu pomocí daného výrazu.</span><span class="sxs-lookup"><span data-stu-id="6beca-147">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="6beca-148">Další informace najdete v tématu [filtrovat možnost Podrobnosti](#filter-option-details) části.</span><span class="sxs-lookup"><span data-stu-id="6beca-148">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="6beca-149">Další příklady a další informace o tom, jak pomocí filtrování testovací selektivní jednotky, najdete v části [spouštění testů jednotek selektivní](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="6beca-149">For additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="6beca-150">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="6beca-150">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="6beca-151">Určuje protokolovacího nástroje pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="6beca-151">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="6beca-152">Nelze sestavit k testovacímu projektu před jejím spuštěním.</span><span class="sxs-lookup"><span data-stu-id="6beca-152">Does not build the test project prior to running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="6beca-153">Adresář, ve kterém chcete najít binární soubory ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="6beca-153">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="6beca-154">Nastavení se má použít při spouštění testů.</span><span class="sxs-lookup"><span data-stu-id="6beca-154">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="6beca-155">Seznam všech zjištěných testů v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="6beca-155">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="6beca-156">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="6beca-156">Sets the verbosity level of the command.</span></span> <span data-ttu-id="6beca-157">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="6beca-157">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="6beca-158">Příklady</span><span class="sxs-lookup"><span data-stu-id="6beca-158">Examples</span></span>

<span data-ttu-id="6beca-159">Spouštět testy v projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="6beca-159">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="6beca-160">Spouštět testy v `test1` projektu:</span><span class="sxs-lookup"><span data-stu-id="6beca-160">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

## <a name="filter-option-details"></a><span data-ttu-id="6beca-161">Podrobnosti o možnost filtru</span><span class="sxs-lookup"><span data-stu-id="6beca-161">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="6beca-162">`<Expression>` má formát `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="6beca-162">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="6beca-163">`<property>` je atributem `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="6beca-163">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="6beca-164">Tady jsou vlastnostech podporovaných zprostředkovatelem systémů testů jednotek oblíbených:</span><span class="sxs-lookup"><span data-stu-id="6beca-164">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="6beca-165">Test Framework</span><span class="sxs-lookup"><span data-stu-id="6beca-165">Test Framework</span></span> | <span data-ttu-id="6beca-166">Podporovaných vlastností</span><span class="sxs-lookup"><span data-stu-id="6beca-166">Supported properties</span></span>                                                                                      |
| :------------: | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="6beca-167">MSTest</span><span class="sxs-lookup"><span data-stu-id="6beca-167">MSTest</span></span>         | <ul><li><span data-ttu-id="6beca-168">Položka FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="6beca-168">FullyQualifiedName</span></span></li><li><span data-ttu-id="6beca-169">Název</span><span class="sxs-lookup"><span data-stu-id="6beca-169">Name</span></span></li><li><span data-ttu-id="6beca-170">ClassName</span><span class="sxs-lookup"><span data-stu-id="6beca-170">ClassName</span></span></li><li><span data-ttu-id="6beca-171">Priorita</span><span class="sxs-lookup"><span data-stu-id="6beca-171">Priority</span></span></li><li><span data-ttu-id="6beca-172">TestCategory</span><span class="sxs-lookup"><span data-stu-id="6beca-172">TestCategory</span></span></li></ul> |
| <span data-ttu-id="6beca-173">xunit</span><span class="sxs-lookup"><span data-stu-id="6beca-173">Xunit</span></span>          | <ul><li><span data-ttu-id="6beca-174">Položka FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="6beca-174">FullyQualifiedName</span></span></li><li><span data-ttu-id="6beca-175">DisplayName</span><span class="sxs-lookup"><span data-stu-id="6beca-175">DisplayName</span></span></li><li><span data-ttu-id="6beca-176">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="6beca-176">Traits</span></span></li></ul>                                   |

<span data-ttu-id="6beca-177">`<operator>` Popisuje vztah mezi vlastnosti a hodnotu:</span><span class="sxs-lookup"><span data-stu-id="6beca-177">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="6beca-178">Operátor</span><span class="sxs-lookup"><span data-stu-id="6beca-178">Operator</span></span> | <span data-ttu-id="6beca-179">Funkce</span><span class="sxs-lookup"><span data-stu-id="6beca-179">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="6beca-180">Přesná shoda</span><span class="sxs-lookup"><span data-stu-id="6beca-180">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="6beca-181">Není přesná shoda</span><span class="sxs-lookup"><span data-stu-id="6beca-181">Not exact match</span></span> |
| `~`      | <span data-ttu-id="6beca-182">Obsahuje</span><span class="sxs-lookup"><span data-stu-id="6beca-182">Contains</span></span>        |

<span data-ttu-id="6beca-183">`<value>` obsahuje řetězec.</span><span class="sxs-lookup"><span data-stu-id="6beca-183">`<value>` is a string.</span></span> <span data-ttu-id="6beca-184">Všechny hledání se malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="6beca-184">All the lookups are case insensitive.</span></span>

<span data-ttu-id="6beca-185">Výraz bez `<operator>` je automaticky považováno za `contains` na `FullyQualifiedName` vlastnosti (například `dotnet test --filter xyz` je stejný jako `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="6beca-185">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="6beca-186">Výrazy lze spojit s podmíněné operátory:</span><span class="sxs-lookup"><span data-stu-id="6beca-186">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="6beca-187">Operátor</span><span class="sxs-lookup"><span data-stu-id="6beca-187">Operator</span></span> | <span data-ttu-id="6beca-188">Funkce</span><span class="sxs-lookup"><span data-stu-id="6beca-188">Function</span></span> |
| :------: | :------: |
| <code>&#124;</code>      | <span data-ttu-id="6beca-189">NEBO</span><span class="sxs-lookup"><span data-stu-id="6beca-189">OR</span></span>       |
| `&`      | <span data-ttu-id="6beca-190">AND</span><span class="sxs-lookup"><span data-stu-id="6beca-190">AND</span></span>      |

<span data-ttu-id="6beca-191">Můžete uzavřete výrazy v závorkách, při použití podmíněné operátory (například `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="6beca-191">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="6beca-192">Další příklady a další informace o tom, jak pomocí filtrování testovací selektivní jednotky, najdete v části [spouštění testů jednotek selektivní](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="6beca-192">For additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6beca-193">Viz také</span><span class="sxs-lookup"><span data-stu-id="6beca-193">See also</span></span>

 [<span data-ttu-id="6beca-194">Rozhraní a cíle</span><span class="sxs-lookup"><span data-stu-id="6beca-194">Frameworks and Targets</span></span>](../../standard/frameworks.md)  
 [<span data-ttu-id="6beca-195">Katalog .NET core Runtime identifikátor (RID)</span><span class="sxs-lookup"><span data-stu-id="6beca-195">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
