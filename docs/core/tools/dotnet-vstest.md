---
title: "příkaz vstest DotNet - .NET Core rozhraní příkazového řádku"
description: "Příkaz vstest dotnet sestavení projektu a všechny jeho závislé součásti."
author: guardrex
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 40469204906bef16e1604d052471721bad64cd7f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-vstest"></a><span data-ttu-id="a01a7-103">vstest DotNet.</span><span class="sxs-lookup"><span data-stu-id="a01a7-103">dotnet vstest</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="a01a7-104">Název</span><span class="sxs-lookup"><span data-stu-id="a01a7-104">Name</span></span>

<span data-ttu-id="a01a7-105">`dotnet-vstest`-Spustí testy ze zadané soubory.</span><span class="sxs-lookup"><span data-stu-id="a01a7-105">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a01a7-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="a01a7-106">Synopsis</span></span>

`dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]`

## <a name="description"></a><span data-ttu-id="a01a7-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a01a7-107">Description</span></span>

<span data-ttu-id="a01a7-108">`dotnet-vstest` Příkaz spustí `VSTest.Console` aplikace příkazového řádku spouštět automatizované částí a programové testy uživatelského rozhraní aplikace.</span><span class="sxs-lookup"><span data-stu-id="a01a7-108">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit and coded UI application tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="a01a7-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="a01a7-109">Arguments</span></span>

`TEST_FILE_NAMES`

<span data-ttu-id="a01a7-110">Spouštění testů ze zadaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="a01a7-110">Run tests from the specified assemblies.</span></span> <span data-ttu-id="a01a7-111">Názvy sestavení více testovací oddělte mezerou.</span><span class="sxs-lookup"><span data-stu-id="a01a7-111">Separate multiple test assembly names with spaces.</span></span>

## <a name="options"></a><span data-ttu-id="a01a7-112">Možnosti</span><span class="sxs-lookup"><span data-stu-id="a01a7-112">Options</span></span>

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="a01a7-113">Nastavení se má použít při spouštění testů.</span><span class="sxs-lookup"><span data-stu-id="a01a7-113">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="a01a7-114">Spouštění testů pomocí názvy, které odpovídají zadaným hodnotám.</span><span class="sxs-lookup"><span data-stu-id="a01a7-114">Run tests with names that match the provided values.</span></span> <span data-ttu-id="a01a7-115">Více hodnot oddělujte čárkami.</span><span class="sxs-lookup"><span data-stu-id="a01a7-115">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="a01a7-116">Použijte vlastní test adaptéry z dané cesty (pokud existuje) v testovacím běhu.</span><span class="sxs-lookup"><span data-stu-id="a01a7-116">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="a01a7-117">Architektura platformy cíl používá pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="a01a7-117">Target platform architecture used for test execution.</span></span> <span data-ttu-id="a01a7-118">Platné hodnoty jsou `x86`, `x64`, a `ARM`.</span><span class="sxs-lookup"><span data-stu-id="a01a7-118">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="a01a7-119">Cílová verze rozhraní .NET Framework používá pro spuštění testu.</span><span class="sxs-lookup"><span data-stu-id="a01a7-119">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="a01a7-120">Příklady platných hodnot `.NETFramework,Version=v4.6`, `.NETCoreApp,Version=v1.0`atd. Jiné podporované hodnoty jsou `Framework35`, `Framework40`, `Framework45`, a `FrameworkCore10`.</span><span class="sxs-lookup"><span data-stu-id="a01a7-120">Examples of valid values are `.NETFramework,Version=v4.6`, `.NETCoreApp,Version=v1.0`, etc. Other supported values are `Framework35`, `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="a01a7-121">Spustíte testy paralelně.</span><span class="sxs-lookup"><span data-stu-id="a01a7-121">Execute tests in parallel.</span></span> <span data-ttu-id="a01a7-122">Standardně jsou všechny dostupné jader na počítači k dispozici pro použití.</span><span class="sxs-lookup"><span data-stu-id="a01a7-122">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="a01a7-123">Soubor nastavení nastavte explicitní počet jader.</span><span class="sxs-lookup"><span data-stu-id="a01a7-123">Set an explicit number of cores with a settings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="a01a7-124">Testy, které odpovídají daného výrazu.</span><span class="sxs-lookup"><span data-stu-id="a01a7-124">Run tests that match the given expression.</span></span> <span data-ttu-id="a01a7-125">`<Expression>`je ve formátu `<property>Operator<value>[|&<Expression>]`, kde operátor je jedním z `=`, `!=`, nebo `~`.</span><span class="sxs-lookup"><span data-stu-id="a01a7-125">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span>  <span data-ttu-id="a01a7-126">Operátor `~` má "obsahuje" sémantiku a použít u vlastnosti řetězce jako `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="a01a7-126">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="a01a7-127">Závorky `()` se používají k dílčí výrazy skupiny.</span><span class="sxs-lookup"><span data-stu-id="a01a7-127">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="a01a7-128">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="a01a7-128">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="a01a7-129">Zadejte protokolovacího nástroje pro výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="a01a7-129">Specify a logger for test results.</span></span>  

* <span data-ttu-id="a01a7-130">K publikování výsledků testů pro Team Foundation Server, použijte `TfsPublisher` protokolovač zprostředkovatele:</span><span class="sxs-lookup"><span data-stu-id="a01a7-130">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="a01a7-131">Do protokolu výsledky do Visual Studio Test výsledky souboru (TRX), použijte `trx` zprostředkovatele protokolovacího nástroje.</span><span class="sxs-lookup"><span data-stu-id="a01a7-131">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="a01a7-132">Tento přepínač vytvoří soubor ve výsledcích testu adresáři s zadaný název souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="a01a7-132">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="a01a7-133">Pokud `LogFileName` není zadaný jedinečný název souboru je vytvořen za účelem uchovávání výsledků testů.</span><span class="sxs-lookup"><span data-stu-id="a01a7-133">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="a01a7-134">Seznamy zjistit testů z daného testovacího kontejneru.</span><span class="sxs-lookup"><span data-stu-id="a01a7-134">Lists discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="a01a7-135">Id procesu nadřazené zodpovědná za spuštění aktuálním procesu.</span><span class="sxs-lookup"><span data-stu-id="a01a7-135">Process Id of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="a01a7-136">Určuje port pro připojení soketu a přijímat zprávy o událostech.</span><span class="sxs-lookup"><span data-stu-id="a01a7-136">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="a01a7-137">Umožňuje podrobné protokoly pro platformu testu.</span><span class="sxs-lookup"><span data-stu-id="a01a7-137">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="a01a7-138">Protokoly se zapisují do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="a01a7-138">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="a01a7-139">Určuje další argumenty pro adaptér.</span><span class="sxs-lookup"><span data-stu-id="a01a7-139">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="a01a7-140">Argumenty nejsou zadány jako dvojice název hodnota ve formátu `<n>=<v>`, kde `<n>` je název argument a `<v>` je hodnota argumentu.</span><span class="sxs-lookup"><span data-stu-id="a01a7-140">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="a01a7-141">Prostor používejte k oddělení více argumentů.</span><span class="sxs-lookup"><span data-stu-id="a01a7-141">Use a space to separate multiple arguments.</span></span>

## <a name="examples"></a><span data-ttu-id="a01a7-142">Příklady</span><span class="sxs-lookup"><span data-stu-id="a01a7-142">Examples</span></span>

<span data-ttu-id="a01a7-143">Spuštění testů `mytestproject.dll`:</span><span class="sxs-lookup"><span data-stu-id="a01a7-143">Run tests in `mytestproject.dll`:</span></span>

`dotnet vstest mytestproject.dll`

<span data-ttu-id="a01a7-144">Spuštění testů `mytestproject.dll` a `myothertestproject.exe`:</span><span class="sxs-lookup"><span data-stu-id="a01a7-144">Run tests in `mytestproject.dll` and `myothertestproject.exe`:</span></span>

`dotnet vstest mytestproject.dll myothertestproject.exe`

<span data-ttu-id="a01a7-145">Spustit `TestMethod1` testů:</span><span class="sxs-lookup"><span data-stu-id="a01a7-145">Run `TestMethod1` tests:</span></span>

`dotnet vstest /Tests:TestMethod1`

<span data-ttu-id="a01a7-146">Spustit `TestMethod1` a `TestMethod2` testů:</span><span class="sxs-lookup"><span data-stu-id="a01a7-146">Run `TestMethod1` and `TestMethod2` tests:</span></span>

`dotnet vstest /Tests:TestMethod1,TestMethod2`
