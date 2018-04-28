---
title: příkaz DotNet - .NET Core rozhraní příkazového řádku
description: Další informace o příkazu dotnet (obecný ovladač pro rozhraní .NET Core rozhraní příkazového řádku nástroje) a jeho použití.
author: mairaw
ms.author: mairaw
ms.date: 03/20/2018
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: bf69be7eb8dfe454823236012113fa53ed39f2f4
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-command"></a><span data-ttu-id="45c56-103">příkaz DotNet.</span><span class="sxs-lookup"><span data-stu-id="45c56-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="45c56-104">Název</span><span class="sxs-lookup"><span data-stu-id="45c56-104">Name</span></span>

<span data-ttu-id="45c56-105">`dotnet` -Obecné ovladače pro spouštění příkazy příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="45c56-105">`dotnet` - General driver for running the command-line commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="45c56-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="45c56-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="45c56-107">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="45c56-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="45c56-108">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="45c56-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [-v|--verbosity] [--version]
```
---

## <a name="description"></a><span data-ttu-id="45c56-109">Popis</span><span class="sxs-lookup"><span data-stu-id="45c56-109">Description</span></span>

<span data-ttu-id="45c56-110">`dotnet` je obecný ovladač pro nástrojů rozhraní příkazového řádku (CLI).</span><span class="sxs-lookup"><span data-stu-id="45c56-110">`dotnet` is a generic driver for the Command Line Interface (CLI) toolchain.</span></span> <span data-ttu-id="45c56-111">Vyvolání sama o sobě poskytuje stručný využití pokyny.</span><span class="sxs-lookup"><span data-stu-id="45c56-111">Invoked on its own, it provides brief usage instructions.</span></span>

<span data-ttu-id="45c56-112">Každý konkrétní funkce je implementovaná jako příkaz.</span><span class="sxs-lookup"><span data-stu-id="45c56-112">Each specific feature is implemented as a command.</span></span> <span data-ttu-id="45c56-113">Chcete-li používat funkci, je příkaz zadaný po `dotnet`, jako například [ `dotnet build` ](dotnet-build.md).</span><span class="sxs-lookup"><span data-stu-id="45c56-113">In order to use the feature, the command is specified after `dotnet`, such as [`dotnet build`](dotnet-build.md).</span></span> <span data-ttu-id="45c56-114">Všechny argumenty následující příkaz jsou vlastní argumenty.</span><span class="sxs-lookup"><span data-stu-id="45c56-114">All of the arguments following the command are its own arguments.</span></span>

<span data-ttu-id="45c56-115">Pouze `dotnet` slouží jako příkaz svoje vlastní je spuštění [framework závislé aplikace](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="45c56-115">The only time `dotnet` is used as a command on its own is to run [framework-dependent apps](../deploying/index.md).</span></span> <span data-ttu-id="45c56-116">Zadejte aplikaci DLL po `dotnet` příkaz pro spuštění aplikace (například `dotnet myapp.dll`).</span><span class="sxs-lookup"><span data-stu-id="45c56-116">Specify an application DLL after the `dotnet` verb to execute the application (for example, `dotnet myapp.dll`).</span></span>

## <a name="options"></a><span data-ttu-id="45c56-117">Možnosti</span><span class="sxs-lookup"><span data-stu-id="45c56-117">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="45c56-118">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="45c56-118">.NET Core 2.x</span></span>](#tab/netcore2x)

`--additional-deps <PATH>`

<span data-ttu-id="45c56-119">Cesta k další *deps.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="45c56-119">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="45c56-120">Cesta obsahující testování zásad a sestavení testovat.</span><span class="sxs-lookup"><span data-stu-id="45c56-120">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="45c56-121">Umožňuje výstup diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="45c56-121">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="45c56-122">Verze nainstalovaného .NET Core runtime se použije ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="45c56-122">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="45c56-123">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="45c56-123">Prints out a short help for the command.</span></span> <span data-ttu-id="45c56-124">Pokud pomocí `dotnet`, vytiskne také seznam dostupných příkazů.</span><span class="sxs-lookup"><span data-stu-id="45c56-124">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="45c56-125">Vytiskne podrobné informace o nástroji příkazového řádku a prostředí, například v aktuálním operačním systému, potvrzení SHA pro verze a další informace.</span><span class="sxs-lookup"><span data-stu-id="45c56-125">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="45c56-126">Zobrazí souhrn vpřed v žádné sdílené framework candidate.</span><span class="sxs-lookup"><span data-stu-id="45c56-126">Rolls forward on no candidate shared framework.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="45c56-127">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="45c56-127">Sets the verbosity level of the command.</span></span> <span data-ttu-id="45c56-128">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="45c56-128">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="45c56-129">Není podporována v každé příkazu; Zobrazit stránka konkrétní příkaz k určení, pokud tato možnost je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="45c56-129">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="45c56-130">Vytiskne verzi rozhraní .NET Core SDK používá.</span><span class="sxs-lookup"><span data-stu-id="45c56-130">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="45c56-131">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="45c56-131">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="45c56-132">Cesta obsahující testování zásad a sestavení testovat.</span><span class="sxs-lookup"><span data-stu-id="45c56-132">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="45c56-133">Umožňuje výstup diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="45c56-133">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="45c56-134">Verze nainstalovaného .NET Core runtime se použije ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="45c56-134">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="45c56-135">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="45c56-135">Prints out a short help for the command.</span></span> <span data-ttu-id="45c56-136">Pokud pomocí `dotnet`, vytiskne také seznam dostupných příkazů.</span><span class="sxs-lookup"><span data-stu-id="45c56-136">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="45c56-137">Vytiskne podrobné informace o nástroji příkazového řádku a prostředí, například v aktuálním operačním systému, potvrzení SHA pro verze a další informace.</span><span class="sxs-lookup"><span data-stu-id="45c56-137">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="45c56-138">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="45c56-138">Sets the verbosity level of the command.</span></span> <span data-ttu-id="45c56-139">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="45c56-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="45c56-140">Není podporována v každé příkazu; Zobrazit stránka konkrétní příkaz k určení, pokud tato možnost je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="45c56-140">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="45c56-141">Vytiskne verzi rozhraní .NET Core SDK používá.</span><span class="sxs-lookup"><span data-stu-id="45c56-141">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="45c56-142">příkazy DotNet.</span><span class="sxs-lookup"><span data-stu-id="45c56-142">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="45c56-143">Obecné</span><span class="sxs-lookup"><span data-stu-id="45c56-143">General</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="45c56-144">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="45c56-144">.NET Core 2.x</span></span>](#tab/netcore2x)

| <span data-ttu-id="45c56-145">Příkaz</span><span class="sxs-lookup"><span data-stu-id="45c56-145">Command</span></span>                             | <span data-ttu-id="45c56-146">Funkce</span><span class="sxs-lookup"><span data-stu-id="45c56-146">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="45c56-147">dotnet build</span><span class="sxs-lookup"><span data-stu-id="45c56-147">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="45c56-148">Sestavení aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="45c56-148">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="45c56-149">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="45c56-149">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="45c56-150">Čistá sestavení výstupy.</span><span class="sxs-lookup"><span data-stu-id="45c56-150">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="45c56-151">dotnet help</span><span class="sxs-lookup"><span data-stu-id="45c56-151">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="45c56-152">Zobrazí podrobnější online dokumentaci pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="45c56-152">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="45c56-153">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="45c56-153">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="45c56-154">Migruje platný Preview 2 projektu na .NET Core SDK 1.0 projekt.</span><span class="sxs-lookup"><span data-stu-id="45c56-154">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="45c56-155">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="45c56-155">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="45c56-156">Poskytuje přístup k MSBuild příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="45c56-156">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="45c56-157">dotnet new</span><span class="sxs-lookup"><span data-stu-id="45c56-157">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="45c56-158">Inicializuje jazyka C# nebo projekt F # pro dané šablony.</span><span class="sxs-lookup"><span data-stu-id="45c56-158">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="45c56-159">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="45c56-159">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="45c56-160">Vytvoří balíček NuGet kódu.</span><span class="sxs-lookup"><span data-stu-id="45c56-160">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="45c56-161">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="45c56-161">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="45c56-162">Publikuje aplikace rozhraní .NET framework závislé nebo úplný a samostatný.</span><span class="sxs-lookup"><span data-stu-id="45c56-162">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="45c56-163">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="45c56-163">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="45c56-164">Obnoví závislosti pro dané aplikaci.</span><span class="sxs-lookup"><span data-stu-id="45c56-164">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="45c56-165">dotnet run</span><span class="sxs-lookup"><span data-stu-id="45c56-165">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="45c56-166">Spustí aplikaci ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="45c56-166">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="45c56-167">dotnet run</span><span class="sxs-lookup"><span data-stu-id="45c56-167">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="45c56-168">Možnosti pro přidání, odebrání a seznam projekty v řešení souboru.</span><span class="sxs-lookup"><span data-stu-id="45c56-168">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="45c56-169">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="45c56-169">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="45c56-170">Uchovává sestavení v úložišti balíček modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="45c56-170">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="45c56-171">dotnet test</span><span class="sxs-lookup"><span data-stu-id="45c56-171">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="45c56-172">Spustí testy použitím nástroje test runner.</span><span class="sxs-lookup"><span data-stu-id="45c56-172">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="45c56-173">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="45c56-173">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="45c56-174">Příkaz</span><span class="sxs-lookup"><span data-stu-id="45c56-174">Command</span></span>                             | <span data-ttu-id="45c56-175">Funkce</span><span class="sxs-lookup"><span data-stu-id="45c56-175">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="45c56-176">dotnet build</span><span class="sxs-lookup"><span data-stu-id="45c56-176">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="45c56-177">Sestavení aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="45c56-177">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="45c56-178">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="45c56-178">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="45c56-179">Čistá sestavení výstupy.</span><span class="sxs-lookup"><span data-stu-id="45c56-179">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="45c56-180">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="45c56-180">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="45c56-181">Migruje platný Preview 2 projektu na .NET Core SDK 1.0 projekt.</span><span class="sxs-lookup"><span data-stu-id="45c56-181">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="45c56-182">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="45c56-182">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="45c56-183">Poskytuje přístup k MSBuild příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="45c56-183">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="45c56-184">dotnet new</span><span class="sxs-lookup"><span data-stu-id="45c56-184">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="45c56-185">Inicializuje jazyka C# nebo projekt F # pro dané šablony.</span><span class="sxs-lookup"><span data-stu-id="45c56-185">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="45c56-186">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="45c56-186">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="45c56-187">Vytvoří balíček NuGet kódu.</span><span class="sxs-lookup"><span data-stu-id="45c56-187">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="45c56-188">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="45c56-188">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="45c56-189">Publikuje aplikace rozhraní .NET framework závislé nebo úplný a samostatný.</span><span class="sxs-lookup"><span data-stu-id="45c56-189">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="45c56-190">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="45c56-190">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="45c56-191">Obnoví závislosti pro dané aplikaci.</span><span class="sxs-lookup"><span data-stu-id="45c56-191">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="45c56-192">dotnet run</span><span class="sxs-lookup"><span data-stu-id="45c56-192">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="45c56-193">Spustí aplikaci ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="45c56-193">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="45c56-194">dotnet run</span><span class="sxs-lookup"><span data-stu-id="45c56-194">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="45c56-195">Možnosti pro přidání, odebrání a seznam projekty v řešení souboru.</span><span class="sxs-lookup"><span data-stu-id="45c56-195">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="45c56-196">dotnet test</span><span class="sxs-lookup"><span data-stu-id="45c56-196">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="45c56-197">Spustí testy použitím nástroje test runner.</span><span class="sxs-lookup"><span data-stu-id="45c56-197">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="45c56-198">Odkazy na projekt</span><span class="sxs-lookup"><span data-stu-id="45c56-198">Project references</span></span>

<span data-ttu-id="45c56-199">Příkaz</span><span class="sxs-lookup"><span data-stu-id="45c56-199">Command</span></span> | <span data-ttu-id="45c56-200">Funkce</span><span class="sxs-lookup"><span data-stu-id="45c56-200">Function</span></span>
--- | ---
[<span data-ttu-id="45c56-201">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="45c56-201">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="45c56-202">Přidáte odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="45c56-202">Add a project reference.</span></span>
[<span data-ttu-id="45c56-203">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="45c56-203">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="45c56-204">Zobrazí seznam odkazů projektu.</span><span class="sxs-lookup"><span data-stu-id="45c56-204">List project references.</span></span>
[<span data-ttu-id="45c56-205">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="45c56-205">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="45c56-206">Odeberte odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="45c56-206">Remove a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="45c56-207">Balíčky NuGet</span><span class="sxs-lookup"><span data-stu-id="45c56-207">NuGet packages</span></span>

<span data-ttu-id="45c56-208">Příkaz</span><span class="sxs-lookup"><span data-stu-id="45c56-208">Command</span></span> | <span data-ttu-id="45c56-209">Funkce</span><span class="sxs-lookup"><span data-stu-id="45c56-209">Function</span></span>
--- | ---
[<span data-ttu-id="45c56-210">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="45c56-210">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="45c56-211">Přidejte balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="45c56-211">Add a NuGet package.</span></span>
[<span data-ttu-id="45c56-212">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="45c56-212">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="45c56-213">Odebrání balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="45c56-213">Remove a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="45c56-214">Příkazy pro balíčky NuGet</span><span class="sxs-lookup"><span data-stu-id="45c56-214">NuGet commands</span></span>

<span data-ttu-id="45c56-215">Příkaz</span><span class="sxs-lookup"><span data-stu-id="45c56-215">Command</span></span> | <span data-ttu-id="45c56-216">Funkce</span><span class="sxs-lookup"><span data-stu-id="45c56-216">Function</span></span>
--- | ---
[<span data-ttu-id="45c56-217">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="45c56-217">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="45c56-218">Odstraní nebo unlists balíčku ze serveru.</span><span class="sxs-lookup"><span data-stu-id="45c56-218">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="45c56-219">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="45c56-219">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="45c56-220">Vymaže nebo vypíše místní prostředky NuGet například mezipaměti požadavek http, dočasnou vyrovnávací paměť nebo složku globální balíčky celého systému.</span><span class="sxs-lookup"><span data-stu-id="45c56-220">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="45c56-221">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="45c56-221">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="45c56-222">Nabízených oznámení balíček na server a vydává je.</span><span class="sxs-lookup"><span data-stu-id="45c56-222">Pushes a package to the server and publishes it.</span></span>

## <a name="examples"></a><span data-ttu-id="45c56-223">Příklady</span><span class="sxs-lookup"><span data-stu-id="45c56-223">Examples</span></span>

<span data-ttu-id="45c56-224">Inicializace ukázkové aplikace konzoly .NET Core, která můžete zkompilovat a spustit:</span><span class="sxs-lookup"><span data-stu-id="45c56-224">Initialize a sample .NET Core console application that can be compiled and run:</span></span>

`dotnet new console`

<span data-ttu-id="45c56-225">Obnovte závislosti pro danou aplikaci:</span><span class="sxs-lookup"><span data-stu-id="45c56-225">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="45c56-226">Sestavte projekt a jeho závislosti v daném adresáři:</span><span class="sxs-lookup"><span data-stu-id="45c56-226">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="45c56-227">Spustit framework závislé aplikace s názvem `myapp.dll`:</span><span class="sxs-lookup"><span data-stu-id="45c56-227">Run a framework-dependent app named `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="45c56-228">Proměnné prostředí</span><span class="sxs-lookup"><span data-stu-id="45c56-228">Environment variables</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="45c56-229">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="45c56-229">.NET Core 2.x</span></span>](#tab/netcore2x)

`DOTNET_PACKAGES`

<span data-ttu-id="45c56-230">Primární balíček mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="45c56-230">The primary package cache.</span></span> <span data-ttu-id="45c56-231">Pokud není nastavena, je standardně `$HOME/.nuget/packages` v systému Unix nebo `%HOME%\NuGet\Packages` v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="45c56-231">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="45c56-232">Určuje umístění údržby indexu má použít pro sdílené hostitele při načítání modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="45c56-232">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="45c56-233">Určuje, jestli se data o využití nástroje .NET Core shromažďuje a odesílá společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="45c56-233">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="45c56-234">Nastavte na `true` vyjádřit výslovný nesouhlas funkci telemetrie (hodnoty `true`, `1`, nebo `yes` přijata) nastavena, jinak hodnota `false` k vyslovení souhlasu s funkcí telemetrie (hodnoty `false`, `0`, nebo `no` přijata).</span><span class="sxs-lookup"><span data-stu-id="45c56-234">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted); otherwise, set to `false` to opt-in to the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="45c56-235">Pokud není nastavená, výchozí hodnoty je `false`, a je aktivní funkce telemetrie.</span><span class="sxs-lookup"><span data-stu-id="45c56-235">If not set, the defaults is `false`, and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="45c56-236">Určuje, zda .NET Core runtime, sdílený framework nebo sady SDK jsou vyřešit z globální umístění.</span><span class="sxs-lookup"><span data-stu-id="45c56-236">Specifies whether .NET Core runtime, shared framework or SDK are resolved from the global location.</span></span> <span data-ttu-id="45c56-237">Pokud není nastavena, je standardně `true`.</span><span class="sxs-lookup"><span data-stu-id="45c56-237">If not set, it defaults to `true`.</span></span> <span data-ttu-id="45c56-238">Nastavte na `false` není vyřešit z globální umístění a mají izolované instalace .NET Core (hodnoty `0` nebo `false` přijímají).</span><span class="sxs-lookup"><span data-stu-id="45c56-238">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="45c56-239">Další informace o víceúrovňovou vyhledávání najdete v tématu [více úroveň SharedFX vyhledávání](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="45c56-239">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="45c56-240">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="45c56-240">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="45c56-241">Primární balíček mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="45c56-241">The primary package cache.</span></span> <span data-ttu-id="45c56-242">Pokud není nastavena, je standardně `$HOME/.nuget/packages` v systému Unix nebo `%HOME%\NuGet\Packages` v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="45c56-242">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="45c56-243">Určuje umístění údržby indexu má použít pro sdílené hostitele při načítání modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="45c56-243">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="45c56-244">Určuje, jestli se data o využití nástroje .NET Core shromažďuje a odesílá společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="45c56-244">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="45c56-245">Nastavte na `true` vyjádřit výslovný nesouhlas funkci telemetrie (hodnoty `true`, `1`, nebo `yes` přijata) nastavena, jinak hodnota `false` k vyslovení souhlasu s funkcí telemetrie (hodnoty `false`, `0`, nebo `no` přijata).</span><span class="sxs-lookup"><span data-stu-id="45c56-245">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted); otherwise, set to `false` to opt-in to the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="45c56-246">Pokud není nastavená, výchozí hodnoty je `false`, a je aktivní funkce telemetrie.</span><span class="sxs-lookup"><span data-stu-id="45c56-246">If not set, the defaults is `false`, and the telemetry feature is active.</span></span>

---
