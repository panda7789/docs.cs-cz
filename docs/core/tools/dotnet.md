---
title: příkaz DotNet - .NET Core rozhraní příkazového řádku
description: Další informace o příkazu dotnet (obecný ovladač pro rozhraní .NET Core rozhraní příkazového řádku nástroje) a jeho použití.
author: mairaw
ms.author: mairaw
ms.date: 05/30/2018
ms.openlocfilehash: 4087cbc666bb837e6048695a2ebbd6f4821b528a
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696404"
---
# <a name="dotnet-command"></a><span data-ttu-id="44bfe-103">příkaz DotNet.</span><span class="sxs-lookup"><span data-stu-id="44bfe-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="44bfe-104">Název</span><span class="sxs-lookup"><span data-stu-id="44bfe-104">Name</span></span>

<span data-ttu-id="44bfe-105">`dotnet` -Obecné ovladače pro spouštění příkazy příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="44bfe-105">`dotnet` - General driver for running the command-line commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="44bfe-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="44bfe-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="44bfe-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="44bfe-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="44bfe-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="44bfe-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="44bfe-109">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="44bfe-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [-v|--verbosity] [--version]
```
---

## <a name="description"></a><span data-ttu-id="44bfe-110">Popis</span><span class="sxs-lookup"><span data-stu-id="44bfe-110">Description</span></span>

<span data-ttu-id="44bfe-111">`dotnet` je obecný ovladač pro nástrojů rozhraní příkazového řádku (CLI).</span><span class="sxs-lookup"><span data-stu-id="44bfe-111">`dotnet` is a generic driver for the Command Line Interface (CLI) toolchain.</span></span> <span data-ttu-id="44bfe-112">Vyvolání sama o sobě poskytuje stručný využití pokyny.</span><span class="sxs-lookup"><span data-stu-id="44bfe-112">Invoked on its own, it provides brief usage instructions.</span></span>

<span data-ttu-id="44bfe-113">Každý konkrétní funkce je implementovaná jako příkaz.</span><span class="sxs-lookup"><span data-stu-id="44bfe-113">Each specific feature is implemented as a command.</span></span> <span data-ttu-id="44bfe-114">Pokud chcete používat funkci, je příkaz zadaný po `dotnet`, jako například [ `dotnet build` ](dotnet-build.md).</span><span class="sxs-lookup"><span data-stu-id="44bfe-114">To use the feature, the command is specified after `dotnet`, such as [`dotnet build`](dotnet-build.md).</span></span> <span data-ttu-id="44bfe-115">Všechny argumenty následující příkaz jsou vlastní argumenty.</span><span class="sxs-lookup"><span data-stu-id="44bfe-115">All of the arguments following the command are its own arguments.</span></span>

<span data-ttu-id="44bfe-116">Pouze `dotnet` slouží jako příkaz svoje vlastní je spuštění [framework závislé aplikace](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="44bfe-116">The only time `dotnet` is used as a command on its own is to run [framework-dependent apps](../deploying/index.md).</span></span> <span data-ttu-id="44bfe-117">Zadejte aplikaci DLL po `dotnet` příkaz pro spuštění aplikace (například `dotnet myapp.dll`).</span><span class="sxs-lookup"><span data-stu-id="44bfe-117">Specify an application DLL after the `dotnet` verb to execute the application (for example, `dotnet myapp.dll`).</span></span>

## <a name="options"></a><span data-ttu-id="44bfe-118">Možnosti</span><span class="sxs-lookup"><span data-stu-id="44bfe-118">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="44bfe-119">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="44bfe-119">.NET Core 2.1</span></span>](#tab/netcore21)

`--additional-deps <PATH>`

<span data-ttu-id="44bfe-120">Cesta k další *deps.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="44bfe-120">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="44bfe-121">Cesta obsahující testování zásad a sestavení testovat.</span><span class="sxs-lookup"><span data-stu-id="44bfe-121">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="44bfe-122">Umožňuje výstup diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="44bfe-122">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="44bfe-123">Verze nainstalovaného .NET Core runtime se použije ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="44bfe-123">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="44bfe-124">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="44bfe-124">Prints out a short help for the command.</span></span> <span data-ttu-id="44bfe-125">Pokud pomocí `dotnet`, vytiskne také seznam dostupných příkazů.</span><span class="sxs-lookup"><span data-stu-id="44bfe-125">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="44bfe-126">Vytiskne podrobné informace o nástroji příkazového řádku a prostředí, například v aktuálním operačním systému, potvrzení SHA pro verze a další informace.</span><span class="sxs-lookup"><span data-stu-id="44bfe-126">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`--list-runtimes`

<span data-ttu-id="44bfe-127">Zobrazuje nainstalované moduly runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="44bfe-127">Displays the installed .NET Core runtimes.</span></span>

`--list-sdks`

<span data-ttu-id="44bfe-128">Zobrazuje nainstalované sady Core SDK pro rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="44bfe-128">Displays the installed .NET Core SDKs.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="44bfe-129">Zobrazí souhrn vpřed v žádné sdílené framework candidate.</span><span class="sxs-lookup"><span data-stu-id="44bfe-129">Rolls forward on no candidate shared framework.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="44bfe-130">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="44bfe-130">Sets the verbosity level of the command.</span></span> <span data-ttu-id="44bfe-131">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="44bfe-131">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="44bfe-132">Není podporována v každé příkazu; Zobrazit stránka konkrétní příkaz k určení, pokud tato možnost je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="44bfe-132">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="44bfe-133">Vytiskne verzi rozhraní .NET Core SDK používá.</span><span class="sxs-lookup"><span data-stu-id="44bfe-133">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="44bfe-134">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="44bfe-134">.NET Core 2.0</span></span>](#tab/netcore20)

`--additional-deps <PATH>`

<span data-ttu-id="44bfe-135">Cesta k další *deps.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="44bfe-135">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="44bfe-136">Cesta obsahující testování zásad a sestavení testovat.</span><span class="sxs-lookup"><span data-stu-id="44bfe-136">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="44bfe-137">Umožňuje výstup diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="44bfe-137">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="44bfe-138">Verze nainstalovaného .NET Core runtime se použije ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="44bfe-138">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="44bfe-139">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="44bfe-139">Prints out a short help for the command.</span></span> <span data-ttu-id="44bfe-140">Pokud pomocí `dotnet`, vytiskne také seznam dostupných příkazů.</span><span class="sxs-lookup"><span data-stu-id="44bfe-140">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="44bfe-141">Vytiskne podrobné informace o nástroji příkazového řádku a prostředí, například v aktuálním operačním systému, potvrzení SHA pro verze a další informace.</span><span class="sxs-lookup"><span data-stu-id="44bfe-141">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="44bfe-142">Zobrazí souhrn vpřed v žádné sdílené framework candidate.</span><span class="sxs-lookup"><span data-stu-id="44bfe-142">Rolls forward on no candidate shared framework.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="44bfe-143">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="44bfe-143">Sets the verbosity level of the command.</span></span> <span data-ttu-id="44bfe-144">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="44bfe-144">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="44bfe-145">Není podporována v každé příkazu; Zobrazit stránka konkrétní příkaz k určení, pokud tato možnost je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="44bfe-145">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="44bfe-146">Vytiskne verzi rozhraní .NET Core SDK používá.</span><span class="sxs-lookup"><span data-stu-id="44bfe-146">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="44bfe-147">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="44bfe-147">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="44bfe-148">Cesta obsahující testování zásad a sestavení testovat.</span><span class="sxs-lookup"><span data-stu-id="44bfe-148">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="44bfe-149">Umožňuje výstup diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="44bfe-149">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="44bfe-150">Verze nainstalovaného .NET Core runtime se použije ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="44bfe-150">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="44bfe-151">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="44bfe-151">Prints out a short help for the command.</span></span> <span data-ttu-id="44bfe-152">Pokud pomocí `dotnet`, vytiskne také seznam dostupných příkazů.</span><span class="sxs-lookup"><span data-stu-id="44bfe-152">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="44bfe-153">Vytiskne podrobné informace o nástroji příkazového řádku a prostředí, například v aktuálním operačním systému, potvrzení SHA pro verze a další informace.</span><span class="sxs-lookup"><span data-stu-id="44bfe-153">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="44bfe-154">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="44bfe-154">Sets the verbosity level of the command.</span></span> <span data-ttu-id="44bfe-155">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="44bfe-155">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="44bfe-156">Není podporována v každé příkazu; Zobrazit stránka konkrétní příkaz k určení, pokud tato možnost je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="44bfe-156">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="44bfe-157">Vytiskne verzi rozhraní .NET Core SDK používá.</span><span class="sxs-lookup"><span data-stu-id="44bfe-157">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="44bfe-158">příkazy DotNet.</span><span class="sxs-lookup"><span data-stu-id="44bfe-158">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="44bfe-159">Obecné</span><span class="sxs-lookup"><span data-stu-id="44bfe-159">General</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="44bfe-160">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="44bfe-160">.NET Core 2.1</span></span>](#tab/netcore21)

| <span data-ttu-id="44bfe-161">Příkaz</span><span class="sxs-lookup"><span data-stu-id="44bfe-161">Command</span></span>                                       | <span data-ttu-id="44bfe-162">Funkce</span><span class="sxs-lookup"><span data-stu-id="44bfe-162">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="44bfe-163">dotnet build</span><span class="sxs-lookup"><span data-stu-id="44bfe-163">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="44bfe-164">Sestavení aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="44bfe-164">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="44bfe-165">sestavení serverem DotNet.</span><span class="sxs-lookup"><span data-stu-id="44bfe-165">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="44bfe-166">Komunikuje se servery, které jsou spouštěné sestavení.</span><span class="sxs-lookup"><span data-stu-id="44bfe-166">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="44bfe-167">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="44bfe-167">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="44bfe-168">Čistá sestavení výstupy.</span><span class="sxs-lookup"><span data-stu-id="44bfe-168">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="44bfe-169">dotnet help</span><span class="sxs-lookup"><span data-stu-id="44bfe-169">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="44bfe-170">Zobrazí podrobnější online dokumentaci pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="44bfe-170">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="44bfe-171">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="44bfe-171">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="44bfe-172">Migruje platný Preview 2 projektu na .NET Core SDK 1.0 projekt.</span><span class="sxs-lookup"><span data-stu-id="44bfe-172">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="44bfe-173">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="44bfe-173">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="44bfe-174">Poskytuje přístup k MSBuild příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="44bfe-174">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="44bfe-175">dotnet new</span><span class="sxs-lookup"><span data-stu-id="44bfe-175">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="44bfe-176">Inicializuje jazyka C# nebo projekt F # pro dané šablony.</span><span class="sxs-lookup"><span data-stu-id="44bfe-176">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="44bfe-177">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="44bfe-177">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="44bfe-178">Vytvoří balíček NuGet kódu.</span><span class="sxs-lookup"><span data-stu-id="44bfe-178">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="44bfe-179">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="44bfe-179">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="44bfe-180">Publikuje aplikace rozhraní .NET framework závislé nebo úplný a samostatný.</span><span class="sxs-lookup"><span data-stu-id="44bfe-180">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="44bfe-181">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="44bfe-181">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="44bfe-182">Obnoví závislosti pro dané aplikaci.</span><span class="sxs-lookup"><span data-stu-id="44bfe-182">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="44bfe-183">dotnet run</span><span class="sxs-lookup"><span data-stu-id="44bfe-183">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="44bfe-184">Spustí aplikaci ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="44bfe-184">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="44bfe-185">dotnet run</span><span class="sxs-lookup"><span data-stu-id="44bfe-185">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="44bfe-186">Možnosti pro přidání, odebrání a seznam projekty v řešení souboru.</span><span class="sxs-lookup"><span data-stu-id="44bfe-186">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="44bfe-187">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="44bfe-187">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="44bfe-188">Uchovává sestavení v úložišti balíček modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="44bfe-188">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="44bfe-189">dotnet test</span><span class="sxs-lookup"><span data-stu-id="44bfe-189">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="44bfe-190">Spustí testy použitím nástroje test runner.</span><span class="sxs-lookup"><span data-stu-id="44bfe-190">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="44bfe-191">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="44bfe-191">.NET Core 2.0</span></span>](#tab/netcore20)

| <span data-ttu-id="44bfe-192">Příkaz</span><span class="sxs-lookup"><span data-stu-id="44bfe-192">Command</span></span>                             | <span data-ttu-id="44bfe-193">Funkce</span><span class="sxs-lookup"><span data-stu-id="44bfe-193">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="44bfe-194">dotnet build</span><span class="sxs-lookup"><span data-stu-id="44bfe-194">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="44bfe-195">Sestavení aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="44bfe-195">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="44bfe-196">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="44bfe-196">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="44bfe-197">Čistá sestavení výstupy.</span><span class="sxs-lookup"><span data-stu-id="44bfe-197">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="44bfe-198">dotnet help</span><span class="sxs-lookup"><span data-stu-id="44bfe-198">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="44bfe-199">Zobrazí podrobnější online dokumentaci pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="44bfe-199">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="44bfe-200">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="44bfe-200">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="44bfe-201">Migruje platný Preview 2 projektu na .NET Core SDK 1.0 projekt.</span><span class="sxs-lookup"><span data-stu-id="44bfe-201">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="44bfe-202">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="44bfe-202">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="44bfe-203">Poskytuje přístup k MSBuild příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="44bfe-203">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="44bfe-204">dotnet new</span><span class="sxs-lookup"><span data-stu-id="44bfe-204">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="44bfe-205">Inicializuje jazyka C# nebo projekt F # pro dané šablony.</span><span class="sxs-lookup"><span data-stu-id="44bfe-205">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="44bfe-206">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="44bfe-206">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="44bfe-207">Vytvoří balíček NuGet kódu.</span><span class="sxs-lookup"><span data-stu-id="44bfe-207">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="44bfe-208">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="44bfe-208">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="44bfe-209">Publikuje aplikace rozhraní .NET framework závislé nebo úplný a samostatný.</span><span class="sxs-lookup"><span data-stu-id="44bfe-209">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="44bfe-210">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="44bfe-210">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="44bfe-211">Obnoví závislosti pro dané aplikaci.</span><span class="sxs-lookup"><span data-stu-id="44bfe-211">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="44bfe-212">dotnet run</span><span class="sxs-lookup"><span data-stu-id="44bfe-212">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="44bfe-213">Spustí aplikaci ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="44bfe-213">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="44bfe-214">dotnet run</span><span class="sxs-lookup"><span data-stu-id="44bfe-214">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="44bfe-215">Možnosti pro přidání, odebrání a seznam projekty v řešení souboru.</span><span class="sxs-lookup"><span data-stu-id="44bfe-215">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="44bfe-216">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="44bfe-216">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="44bfe-217">Uchovává sestavení v úložišti balíček modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="44bfe-217">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="44bfe-218">dotnet test</span><span class="sxs-lookup"><span data-stu-id="44bfe-218">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="44bfe-219">Spustí testy použitím nástroje test runner.</span><span class="sxs-lookup"><span data-stu-id="44bfe-219">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="44bfe-220">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="44bfe-220">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="44bfe-221">Příkaz</span><span class="sxs-lookup"><span data-stu-id="44bfe-221">Command</span></span>                             | <span data-ttu-id="44bfe-222">Funkce</span><span class="sxs-lookup"><span data-stu-id="44bfe-222">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="44bfe-223">dotnet build</span><span class="sxs-lookup"><span data-stu-id="44bfe-223">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="44bfe-224">Sestavení aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="44bfe-224">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="44bfe-225">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="44bfe-225">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="44bfe-226">Čistá sestavení výstupy.</span><span class="sxs-lookup"><span data-stu-id="44bfe-226">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="44bfe-227">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="44bfe-227">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="44bfe-228">Migruje platný Preview 2 projektu na .NET Core SDK 1.0 projekt.</span><span class="sxs-lookup"><span data-stu-id="44bfe-228">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="44bfe-229">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="44bfe-229">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="44bfe-230">Poskytuje přístup k MSBuild příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="44bfe-230">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="44bfe-231">dotnet new</span><span class="sxs-lookup"><span data-stu-id="44bfe-231">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="44bfe-232">Inicializuje jazyka C# nebo projekt F # pro dané šablony.</span><span class="sxs-lookup"><span data-stu-id="44bfe-232">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="44bfe-233">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="44bfe-233">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="44bfe-234">Vytvoří balíček NuGet kódu.</span><span class="sxs-lookup"><span data-stu-id="44bfe-234">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="44bfe-235">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="44bfe-235">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="44bfe-236">Publikuje aplikace rozhraní .NET framework závislé nebo úplný a samostatný.</span><span class="sxs-lookup"><span data-stu-id="44bfe-236">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="44bfe-237">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="44bfe-237">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="44bfe-238">Obnoví závislosti pro dané aplikaci.</span><span class="sxs-lookup"><span data-stu-id="44bfe-238">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="44bfe-239">dotnet run</span><span class="sxs-lookup"><span data-stu-id="44bfe-239">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="44bfe-240">Spustí aplikaci ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="44bfe-240">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="44bfe-241">dotnet run</span><span class="sxs-lookup"><span data-stu-id="44bfe-241">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="44bfe-242">Možnosti pro přidání, odebrání a seznam projekty v řešení souboru.</span><span class="sxs-lookup"><span data-stu-id="44bfe-242">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="44bfe-243">dotnet test</span><span class="sxs-lookup"><span data-stu-id="44bfe-243">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="44bfe-244">Spustí testy použitím nástroje test runner.</span><span class="sxs-lookup"><span data-stu-id="44bfe-244">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="44bfe-245">Odkazy na projekt</span><span class="sxs-lookup"><span data-stu-id="44bfe-245">Project references</span></span>

<span data-ttu-id="44bfe-246">Příkaz</span><span class="sxs-lookup"><span data-stu-id="44bfe-246">Command</span></span> | <span data-ttu-id="44bfe-247">Funkce</span><span class="sxs-lookup"><span data-stu-id="44bfe-247">Function</span></span>
--- | ---
[<span data-ttu-id="44bfe-248">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="44bfe-248">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="44bfe-249">Přidá odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="44bfe-249">Adds a project reference.</span></span>
[<span data-ttu-id="44bfe-250">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="44bfe-250">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="44bfe-251">Obsahuje seznam odkazů projektu.</span><span class="sxs-lookup"><span data-stu-id="44bfe-251">Lists project references.</span></span>
[<span data-ttu-id="44bfe-252">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="44bfe-252">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="44bfe-253">Odebere odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="44bfe-253">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="44bfe-254">Balíčky NuGet</span><span class="sxs-lookup"><span data-stu-id="44bfe-254">NuGet packages</span></span>

<span data-ttu-id="44bfe-255">Příkaz</span><span class="sxs-lookup"><span data-stu-id="44bfe-255">Command</span></span> | <span data-ttu-id="44bfe-256">Funkce</span><span class="sxs-lookup"><span data-stu-id="44bfe-256">Function</span></span>
--- | ---
[<span data-ttu-id="44bfe-257">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="44bfe-257">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="44bfe-258">Přidá balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="44bfe-258">Adds a NuGet package.</span></span>
[<span data-ttu-id="44bfe-259">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="44bfe-259">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="44bfe-260">Odebere balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="44bfe-260">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="44bfe-261">Příkazy pro balíčky NuGet</span><span class="sxs-lookup"><span data-stu-id="44bfe-261">NuGet commands</span></span>

<span data-ttu-id="44bfe-262">Příkaz</span><span class="sxs-lookup"><span data-stu-id="44bfe-262">Command</span></span> | <span data-ttu-id="44bfe-263">Funkce</span><span class="sxs-lookup"><span data-stu-id="44bfe-263">Function</span></span>
--- | ---
[<span data-ttu-id="44bfe-264">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="44bfe-264">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="44bfe-265">Odstraní nebo unlists balíčku ze serveru.</span><span class="sxs-lookup"><span data-stu-id="44bfe-265">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="44bfe-266">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="44bfe-266">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="44bfe-267">Vymaže nebo vypíše místní prostředky NuGet například mezipaměti požadavek http, dočasnou vyrovnávací paměť nebo složku globální balíčky celého systému.</span><span class="sxs-lookup"><span data-stu-id="44bfe-267">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="44bfe-268">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="44bfe-268">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="44bfe-269">Nabízených oznámení balíček na server a vydává je.</span><span class="sxs-lookup"><span data-stu-id="44bfe-269">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tools-commands"></a><span data-ttu-id="44bfe-270">Globální příkazy nástroje</span><span class="sxs-lookup"><span data-stu-id="44bfe-270">Global Tools commands</span></span>

<span data-ttu-id="44bfe-271">[.NET core globální nástroje](global-tools.md) jsou k dispozici strating s .NET Core SDK 2.1.300:</span><span class="sxs-lookup"><span data-stu-id="44bfe-271">[.NET Core Global Tools](global-tools.md) are available strating with .NET Core SDK 2.1.300:</span></span>

<span data-ttu-id="44bfe-272">Příkaz</span><span class="sxs-lookup"><span data-stu-id="44bfe-272">Command</span></span> | <span data-ttu-id="44bfe-273">Funkce</span><span class="sxs-lookup"><span data-stu-id="44bfe-273">Function</span></span>
--- | ---
[<span data-ttu-id="44bfe-274">Instalace nástroje pro DotNet.</span><span class="sxs-lookup"><span data-stu-id="44bfe-274">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="44bfe-275">Nainstaluje nástroj globální na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="44bfe-275">Installs a Global Tool on your machine.</span></span>
[<span data-ttu-id="44bfe-276">seznam nástrojů DotNet.</span><span class="sxs-lookup"><span data-stu-id="44bfe-276">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="44bfe-277">Obsahuje seznam všech globálních nástrojů, které jsou nainstalovány v výchozí adresář na počítači nebo v zadané cestě.</span><span class="sxs-lookup"><span data-stu-id="44bfe-277">Lists all Global Tools currently installed in the default directory on your machine or in the specified path.</span></span>
[<span data-ttu-id="44bfe-278">Odinstalace nástroje pro DotNet.</span><span class="sxs-lookup"><span data-stu-id="44bfe-278">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="44bfe-279">Odinstaluje nástroj globální z vašeho počítače.</span><span class="sxs-lookup"><span data-stu-id="44bfe-279">Uninstalls a Global Tool from your machine.</span></span>
[<span data-ttu-id="44bfe-280">aktualizace nástrojů DotNet.</span><span class="sxs-lookup"><span data-stu-id="44bfe-280">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="44bfe-281">Aktualizuje nástroj globální na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="44bfe-281">Updates a Global Tool on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="44bfe-282">Další nástroje</span><span class="sxs-lookup"><span data-stu-id="44bfe-282">Additional tools</span></span>

<span data-ttu-id="44bfe-283">Od verze rozhraní .NET Core SDK 2.1.300, několik nástrojů, které byly k dispozici pouze na jednotlivých projektů za použití `DotnetCliToolReference` jsou nyní k dispozici jako součást .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="44bfe-283">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="44bfe-284">Mezi tyto nástroje patří:</span><span class="sxs-lookup"><span data-stu-id="44bfe-284">These tools include:</span></span>

| <span data-ttu-id="44bfe-285">Nástroj</span><span class="sxs-lookup"><span data-stu-id="44bfe-285">Tool</span></span>                                    | <span data-ttu-id="44bfe-286">Funkce</span><span class="sxs-lookup"><span data-stu-id="44bfe-286">Function</span></span>                                                     |
| --------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="44bfe-287">dev certifikátů</span><span class="sxs-lookup"><span data-stu-id="44bfe-287">dev-certs</span></span>                               | <span data-ttu-id="44bfe-288">Vytváří a spravuje certifikáty vývoj.</span><span class="sxs-lookup"><span data-stu-id="44bfe-288">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="44bfe-289">EF</span><span class="sxs-lookup"><span data-stu-id="44bfe-289">ef</span></span>](/ef/core/miscellaneous/cli/dotnet) | <span data-ttu-id="44bfe-290">Nástroje příkazového řádku Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="44bfe-290">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="44bfe-291">ukládání do mezipaměti SQL</span><span class="sxs-lookup"><span data-stu-id="44bfe-291">sql-cache</span></span>                               | <span data-ttu-id="44bfe-292">Nástroje příkazového řádku systému SQL Server mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="44bfe-292">SQL Server cache command-line tools.</span></span>                         |
| <span data-ttu-id="44bfe-293">uživatel-tajné klíče</span><span class="sxs-lookup"><span data-stu-id="44bfe-293">user-secrets</span></span>                            | <span data-ttu-id="44bfe-294">Spravuje uživatele vývoj tajných klíčů.</span><span class="sxs-lookup"><span data-stu-id="44bfe-294">Manages development user secrets.</span></span>                            |
| <span data-ttu-id="44bfe-295">Sledování</span><span class="sxs-lookup"><span data-stu-id="44bfe-295">watch</span></span>                                   | <span data-ttu-id="44bfe-296">Spustí soubor sledovacího procesu, který spouští příkaz změna souborů.</span><span class="sxs-lookup"><span data-stu-id="44bfe-296">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="44bfe-297">Další informace o nástroji pro každé provedení `dotnet <tool-name> --help`.</span><span class="sxs-lookup"><span data-stu-id="44bfe-297">For more information about each tool, execute `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="44bfe-298">Příklady</span><span class="sxs-lookup"><span data-stu-id="44bfe-298">Examples</span></span>

<span data-ttu-id="44bfe-299">Vytvoří novou konzolovou aplikaci .NET Core:</span><span class="sxs-lookup"><span data-stu-id="44bfe-299">Creates a new .NET Core console application:</span></span>

`dotnet new console`

<span data-ttu-id="44bfe-300">Obnovte závislosti pro danou aplikaci:</span><span class="sxs-lookup"><span data-stu-id="44bfe-300">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="44bfe-301">Sestavte projekt a jeho závislosti v daném adresáři:</span><span class="sxs-lookup"><span data-stu-id="44bfe-301">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="44bfe-302">Spustit framework závislé aplikace s názvem `myapp.dll`:</span><span class="sxs-lookup"><span data-stu-id="44bfe-302">Run a framework-dependent app named `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="44bfe-303">Proměnné prostředí</span><span class="sxs-lookup"><span data-stu-id="44bfe-303">Environment variables</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="44bfe-304">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="44bfe-304">.NET Core 2.1</span></span>](#tab/netcore21)

`DOTNET_PACKAGES`

<span data-ttu-id="44bfe-305">Primární balíček mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="44bfe-305">The primary package cache.</span></span> <span data-ttu-id="44bfe-306">Pokud není nastavena, je standardně `$HOME/.nuget/packages` v systému Unix nebo `%HOME%\NuGet\Packages` v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="44bfe-306">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="44bfe-307">Určuje umístění údržby indexu má použít pro sdílené hostitele při načítání modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="44bfe-307">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="44bfe-308">Určuje, jestli se data o využití nástroje .NET Core shromažďuje a odesílá společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="44bfe-308">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="44bfe-309">Nastavte na `true` vyjádřit výslovný nesouhlas funkci telemetrie (hodnoty `true`, `1`, nebo `yes` přijata).</span><span class="sxs-lookup"><span data-stu-id="44bfe-309">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="44bfe-310">Jinak hodnota nastavena na `false` který se přidá do funkce telemetrie (hodnoty `false`, `0`, nebo `no` přijata).</span><span class="sxs-lookup"><span data-stu-id="44bfe-310">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="44bfe-311">Pokud není nastavená, výchozí hodnota je `false` a funkci telemetrie je aktivní.</span><span class="sxs-lookup"><span data-stu-id="44bfe-311">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="44bfe-312">Určuje, zda .NET Core runtime, sdílený framework nebo sady SDK jsou vyřešit z globální umístění.</span><span class="sxs-lookup"><span data-stu-id="44bfe-312">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="44bfe-313">Pokud není nastavena, je standardně `true`.</span><span class="sxs-lookup"><span data-stu-id="44bfe-313">If not set, it defaults to `true`.</span></span> <span data-ttu-id="44bfe-314">Nastavte na `false` není vyřešit z globální umístění a mají izolované instalace .NET Core (hodnoty `0` nebo `false` přijímají).</span><span class="sxs-lookup"><span data-stu-id="44bfe-314">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="44bfe-315">Další informace o víceúrovňovou vyhledávání najdete v tématu [více úroveň SharedFX vyhledávání](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="44bfe-315">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

<span data-ttu-id="44bfe-316">Zakáže malé verze dopředné posunutí.</span><span class="sxs-lookup"><span data-stu-id="44bfe-316">Disables minor version roll forward.</span></span> <span data-ttu-id="44bfe-317">Další informace najdete v tématu [Posunutí vpřed](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="44bfe-317">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="44bfe-318">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="44bfe-318">.NET Core 2.0</span></span>](#tab/netcore20)

`DOTNET_PACKAGES`

<span data-ttu-id="44bfe-319">Primární balíček mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="44bfe-319">The primary package cache.</span></span> <span data-ttu-id="44bfe-320">Pokud není nastavena, je standardně `$HOME/.nuget/packages` v systému Unix nebo `%HOME%\NuGet\Packages` v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="44bfe-320">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="44bfe-321">Určuje umístění údržby indexu má použít pro sdílené hostitele při načítání modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="44bfe-321">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="44bfe-322">Určuje, jestli se data o využití nástroje .NET Core shromažďuje a odesílá společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="44bfe-322">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="44bfe-323">Nastavte na `true` vyjádřit výslovný nesouhlas funkci telemetrie (hodnoty `true`, `1`, nebo `yes` přijata).</span><span class="sxs-lookup"><span data-stu-id="44bfe-323">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="44bfe-324">Jinak hodnota nastavena na `false` který se přidá do funkce telemetrie (hodnoty `false`, `0`, nebo `no` přijata).</span><span class="sxs-lookup"><span data-stu-id="44bfe-324">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="44bfe-325">Pokud není nastavená, výchozí hodnota je `false` a funkci telemetrie je aktivní.</span><span class="sxs-lookup"><span data-stu-id="44bfe-325">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="44bfe-326">Určuje, zda .NET Core runtime, sdílený framework nebo sady SDK jsou vyřešit z globální umístění.</span><span class="sxs-lookup"><span data-stu-id="44bfe-326">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="44bfe-327">Pokud není nastavena, je standardně `true`.</span><span class="sxs-lookup"><span data-stu-id="44bfe-327">If not set, it defaults to `true`.</span></span> <span data-ttu-id="44bfe-328">Nastavte na `false` není vyřešit z globální umístění a mají izolované instalace .NET Core (hodnoty `0` nebo `false` přijímají).</span><span class="sxs-lookup"><span data-stu-id="44bfe-328">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="44bfe-329">Další informace o víceúrovňovou vyhledávání najdete v tématu [více úroveň SharedFX vyhledávání](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="44bfe-329">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="44bfe-330">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="44bfe-330">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="44bfe-331">Primární balíček mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="44bfe-331">The primary package cache.</span></span> <span data-ttu-id="44bfe-332">Pokud není nastavena, je standardně `$HOME/.nuget/packages` v systému Unix nebo `%HOME%\NuGet\Packages` v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="44bfe-332">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="44bfe-333">Určuje umístění údržby indexu má použít pro sdílené hostitele při načítání modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="44bfe-333">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="44bfe-334">Určuje, jestli se data o využití nástroje .NET Core shromažďuje a odesílá společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="44bfe-334">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="44bfe-335">Nastavte na `true` vyjádřit výslovný nesouhlas funkci telemetrie (hodnoty `true`, `1`, nebo `yes` přijata).</span><span class="sxs-lookup"><span data-stu-id="44bfe-335">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="44bfe-336">Jinak hodnota nastavena na `false` který se přidá do funkce telemetrie (hodnoty `false`, `0`, nebo `no` přijata).</span><span class="sxs-lookup"><span data-stu-id="44bfe-336">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="44bfe-337">Pokud není nastavená, výchozí hodnota je `false` a funkci telemetrie je aktivní.</span><span class="sxs-lookup"><span data-stu-id="44bfe-337">If not set, the default is `false` and the telemetry feature is active.</span></span>

---
