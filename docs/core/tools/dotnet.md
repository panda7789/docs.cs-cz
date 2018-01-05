---
title: "příkaz DotNet - .NET Core rozhraní příkazového řádku"
description: "Další informace o příkazu dotnet (obecný ovladač pro rozhraní .NET Core rozhraní příkazového řádku nástroje) a jeho použití."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 6db2bb6003e630aab900222eb20e33af287cf9c5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-command"></a><span data-ttu-id="5ae72-103">příkaz DotNet.</span><span class="sxs-lookup"><span data-stu-id="5ae72-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="5ae72-104">Název</span><span class="sxs-lookup"><span data-stu-id="5ae72-104">Name</span></span>

<span data-ttu-id="5ae72-105">`dotnet`-Obecné ovladače pro spouštění příkazy příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="5ae72-105">`dotnet` - General driver for running the command-line commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5ae72-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="5ae72-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="5ae72-107">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="5ae72-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbose] [--version]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5ae72-108">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="5ae72-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [-v|--verbose] [--version]
```
---

## <a name="description"></a><span data-ttu-id="5ae72-109">Popis</span><span class="sxs-lookup"><span data-stu-id="5ae72-109">Description</span></span>

<span data-ttu-id="5ae72-110">`dotnet`je obecný ovladač pro nástrojů rozhraní příkazového řádku (CLI).</span><span class="sxs-lookup"><span data-stu-id="5ae72-110">`dotnet` is a generic driver for the Command Line Interface (CLI) toolchain.</span></span> <span data-ttu-id="5ae72-111">Vyvolání sama o sobě poskytuje stručný využití pokyny.</span><span class="sxs-lookup"><span data-stu-id="5ae72-111">Invoked on its own, it provides brief usage instructions.</span></span>

<span data-ttu-id="5ae72-112">Každý konkrétní funkce je implementovaná jako příkaz.</span><span class="sxs-lookup"><span data-stu-id="5ae72-112">Each specific feature is implemented as a command.</span></span> <span data-ttu-id="5ae72-113">Chcete-li používat funkci, je příkaz zadaný po `dotnet`, jako například [ `dotnet build` ](dotnet-build.md).</span><span class="sxs-lookup"><span data-stu-id="5ae72-113">In order to use the feature, the command is specified after `dotnet`, such as [`dotnet build`](dotnet-build.md).</span></span> <span data-ttu-id="5ae72-114">Všechny argumenty následující příkaz jsou vlastní argumenty.</span><span class="sxs-lookup"><span data-stu-id="5ae72-114">All of the arguments following the command are its own arguments.</span></span>

<span data-ttu-id="5ae72-115">Pouze `dotnet` slouží jako příkaz svoje vlastní je spuštění [framework závislé aplikace](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="5ae72-115">The only time `dotnet` is used as a command on its own is to run [framework-dependent apps](../deploying/index.md).</span></span> <span data-ttu-id="5ae72-116">Zadejte aplikaci DLL po `dotnet` příkaz pro spuštění aplikace (například `dotnet myapp.dll`).</span><span class="sxs-lookup"><span data-stu-id="5ae72-116">Specify an application DLL after the `dotnet` verb to execute the application (for example, `dotnet myapp.dll`).</span></span>

## <a name="options"></a><span data-ttu-id="5ae72-117">Možnosti</span><span class="sxs-lookup"><span data-stu-id="5ae72-117">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="5ae72-118">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="5ae72-118">.NET Core 2.x</span></span>](#tab/netcore2x)

`--additionaldeps <PATH>`

<span data-ttu-id="5ae72-119">Cesta k další *deps.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="5ae72-119">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="5ae72-120">Cesta obsahující testování zásad a sestavení testovat.</span><span class="sxs-lookup"><span data-stu-id="5ae72-120">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="5ae72-121">Umožňuje výstup diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="5ae72-121">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="5ae72-122">Verze nainstalovaného .NET Core runtime se použije ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="5ae72-122">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="5ae72-123">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="5ae72-123">Prints out a short help for the command.</span></span> <span data-ttu-id="5ae72-124">Pokud pomocí `dotnet`, vytiskne také seznam dostupných příkazů.</span><span class="sxs-lookup"><span data-stu-id="5ae72-124">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="5ae72-125">Vytiskne podrobné informace o nástroji příkazového řádku a prostředí, například v aktuálním operačním systému, potvrzení SHA pro verze a další informace.</span><span class="sxs-lookup"><span data-stu-id="5ae72-125">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="5ae72-126">Zobrazí souhrn vpřed v žádné sdílené framework candidate.</span><span class="sxs-lookup"><span data-stu-id="5ae72-126">Rolls forward on no candidate shared framework.</span></span>

`-v|--verbose`

<span data-ttu-id="5ae72-127">Umožňuje podrobný výstup.</span><span class="sxs-lookup"><span data-stu-id="5ae72-127">Enables verbose output.</span></span>

`--version`

<span data-ttu-id="5ae72-128">Vytiskne verzi rozhraní .NET Core SDK používá.</span><span class="sxs-lookup"><span data-stu-id="5ae72-128">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5ae72-129">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="5ae72-129">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="5ae72-130">Cesta obsahující testování zásad a sestavení testovat.</span><span class="sxs-lookup"><span data-stu-id="5ae72-130">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="5ae72-131">Umožňuje výstup diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="5ae72-131">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="5ae72-132">Verze nainstalovaného .NET Core runtime se použije ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="5ae72-132">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="5ae72-133">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="5ae72-133">Prints out a short help for the command.</span></span> <span data-ttu-id="5ae72-134">Pokud pomocí `dotnet`, vytiskne také seznam dostupných příkazů.</span><span class="sxs-lookup"><span data-stu-id="5ae72-134">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="5ae72-135">Vytiskne podrobné informace o nástroji příkazového řádku a prostředí, například v aktuálním operačním systému, potvrzení SHA pro verze a další informace.</span><span class="sxs-lookup"><span data-stu-id="5ae72-135">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`-v|--verbose`

<span data-ttu-id="5ae72-136">Umožňuje podrobný výstup.</span><span class="sxs-lookup"><span data-stu-id="5ae72-136">Enables verbose output.</span></span>

`--version`

<span data-ttu-id="5ae72-137">Vytiskne verzi rozhraní .NET Core SDK používá.</span><span class="sxs-lookup"><span data-stu-id="5ae72-137">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="5ae72-138">příkazy DotNet.</span><span class="sxs-lookup"><span data-stu-id="5ae72-138">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="5ae72-139">Obecné</span><span class="sxs-lookup"><span data-stu-id="5ae72-139">General</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="5ae72-140">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="5ae72-140">.NET Core 2.x</span></span>](#tab/netcore2x)

| <span data-ttu-id="5ae72-141">Příkaz</span><span class="sxs-lookup"><span data-stu-id="5ae72-141">Command</span></span>                             | <span data-ttu-id="5ae72-142">Funkce</span><span class="sxs-lookup"><span data-stu-id="5ae72-142">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="5ae72-143">dotnet build</span><span class="sxs-lookup"><span data-stu-id="5ae72-143">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="5ae72-144">Sestavení aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5ae72-144">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="5ae72-145">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="5ae72-145">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="5ae72-146">Čistá sestavení výstupy.</span><span class="sxs-lookup"><span data-stu-id="5ae72-146">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="5ae72-147">dotnet help</span><span class="sxs-lookup"><span data-stu-id="5ae72-147">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="5ae72-148">Zobrazí podrobnější online dokumentaci pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="5ae72-148">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="5ae72-149">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="5ae72-149">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="5ae72-150">Migruje platný Preview 2 projektu na .NET Core SDK 1.0 projekt.</span><span class="sxs-lookup"><span data-stu-id="5ae72-150">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="5ae72-151">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="5ae72-151">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="5ae72-152">Poskytuje přístup k MSBuild příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="5ae72-152">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="5ae72-153">dotnet new</span><span class="sxs-lookup"><span data-stu-id="5ae72-153">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="5ae72-154">Inicializuje jazyka C# nebo projekt F # pro dané šablony.</span><span class="sxs-lookup"><span data-stu-id="5ae72-154">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="5ae72-155">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="5ae72-155">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="5ae72-156">Vytvoří balíček NuGet kódu.</span><span class="sxs-lookup"><span data-stu-id="5ae72-156">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="5ae72-157">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="5ae72-157">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="5ae72-158">Publikuje aplikace rozhraní .NET framework závislé nebo úplný a samostatný.</span><span class="sxs-lookup"><span data-stu-id="5ae72-158">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="5ae72-159">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="5ae72-159">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="5ae72-160">Obnoví závislosti pro dané aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5ae72-160">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="5ae72-161">dotnet run</span><span class="sxs-lookup"><span data-stu-id="5ae72-161">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="5ae72-162">Spustí aplikaci ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="5ae72-162">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="5ae72-163">dotnet run</span><span class="sxs-lookup"><span data-stu-id="5ae72-163">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="5ae72-164">Možnosti pro přidání, odebrání a seznam projekty v řešení souboru.</span><span class="sxs-lookup"><span data-stu-id="5ae72-164">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="5ae72-165">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="5ae72-165">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="5ae72-166">Uchovává sestavení v úložišti balíček modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="5ae72-166">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="5ae72-167">dotnet test</span><span class="sxs-lookup"><span data-stu-id="5ae72-167">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="5ae72-168">Spustí testy použitím nástroje test runner.</span><span class="sxs-lookup"><span data-stu-id="5ae72-168">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5ae72-169">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="5ae72-169">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="5ae72-170">Příkaz</span><span class="sxs-lookup"><span data-stu-id="5ae72-170">Command</span></span>                             | <span data-ttu-id="5ae72-171">Funkce</span><span class="sxs-lookup"><span data-stu-id="5ae72-171">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="5ae72-172">dotnet build</span><span class="sxs-lookup"><span data-stu-id="5ae72-172">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="5ae72-173">Sestavení aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5ae72-173">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="5ae72-174">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="5ae72-174">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="5ae72-175">Čistá sestavení výstupy.</span><span class="sxs-lookup"><span data-stu-id="5ae72-175">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="5ae72-176">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="5ae72-176">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="5ae72-177">Migruje platný Preview 2 projektu na .NET Core SDK 1.0 projekt.</span><span class="sxs-lookup"><span data-stu-id="5ae72-177">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="5ae72-178">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="5ae72-178">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="5ae72-179">Poskytuje přístup k MSBuild příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="5ae72-179">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="5ae72-180">dotnet new</span><span class="sxs-lookup"><span data-stu-id="5ae72-180">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="5ae72-181">Inicializuje jazyka C# nebo projekt F # pro dané šablony.</span><span class="sxs-lookup"><span data-stu-id="5ae72-181">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="5ae72-182">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="5ae72-182">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="5ae72-183">Vytvoří balíček NuGet kódu.</span><span class="sxs-lookup"><span data-stu-id="5ae72-183">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="5ae72-184">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="5ae72-184">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="5ae72-185">Publikuje aplikace rozhraní .NET framework závislé nebo úplný a samostatný.</span><span class="sxs-lookup"><span data-stu-id="5ae72-185">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="5ae72-186">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="5ae72-186">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="5ae72-187">Obnoví závislosti pro dané aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5ae72-187">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="5ae72-188">dotnet run</span><span class="sxs-lookup"><span data-stu-id="5ae72-188">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="5ae72-189">Spustí aplikaci ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="5ae72-189">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="5ae72-190">dotnet run</span><span class="sxs-lookup"><span data-stu-id="5ae72-190">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="5ae72-191">Možnosti pro přidání, odebrání a seznam projekty v řešení souboru.</span><span class="sxs-lookup"><span data-stu-id="5ae72-191">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="5ae72-192">dotnet test</span><span class="sxs-lookup"><span data-stu-id="5ae72-192">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="5ae72-193">Spustí testy použitím nástroje test runner.</span><span class="sxs-lookup"><span data-stu-id="5ae72-193">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="5ae72-194">Odkazy na projekt</span><span class="sxs-lookup"><span data-stu-id="5ae72-194">Project references</span></span>

<span data-ttu-id="5ae72-195">Příkaz</span><span class="sxs-lookup"><span data-stu-id="5ae72-195">Command</span></span> | <span data-ttu-id="5ae72-196">Funkce</span><span class="sxs-lookup"><span data-stu-id="5ae72-196">Function</span></span>
--- | ---
[<span data-ttu-id="5ae72-197">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="5ae72-197">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="5ae72-198">Přidáte odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="5ae72-198">Add a project reference.</span></span>
[<span data-ttu-id="5ae72-199">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="5ae72-199">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="5ae72-200">Zobrazí seznam odkazů projektu.</span><span class="sxs-lookup"><span data-stu-id="5ae72-200">List project references.</span></span>
[<span data-ttu-id="5ae72-201">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="5ae72-201">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="5ae72-202">Odeberte odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="5ae72-202">Remove a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="5ae72-203">Balíčky NuGet</span><span class="sxs-lookup"><span data-stu-id="5ae72-203">NuGet packages</span></span>

<span data-ttu-id="5ae72-204">Příkaz</span><span class="sxs-lookup"><span data-stu-id="5ae72-204">Command</span></span> | <span data-ttu-id="5ae72-205">Funkce</span><span class="sxs-lookup"><span data-stu-id="5ae72-205">Function</span></span>
--- | ---
[<span data-ttu-id="5ae72-206">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="5ae72-206">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="5ae72-207">Přidejte balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="5ae72-207">Add a NuGet package.</span></span>
[<span data-ttu-id="5ae72-208">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="5ae72-208">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="5ae72-209">Odebrání balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="5ae72-209">Remove a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="5ae72-210">Příkazy pro balíčky NuGet</span><span class="sxs-lookup"><span data-stu-id="5ae72-210">NuGet commands</span></span>

<span data-ttu-id="5ae72-211">Příkaz</span><span class="sxs-lookup"><span data-stu-id="5ae72-211">Command</span></span> | <span data-ttu-id="5ae72-212">Funkce</span><span class="sxs-lookup"><span data-stu-id="5ae72-212">Function</span></span>
--- | ---
[<span data-ttu-id="5ae72-213">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="5ae72-213">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="5ae72-214">Odstraní nebo unlists balíčku ze serveru.</span><span class="sxs-lookup"><span data-stu-id="5ae72-214">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="5ae72-215">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="5ae72-215">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="5ae72-216">Vymaže nebo vypíše místní prostředky NuGet například mezipaměti požadavek http, dočasnou vyrovnávací paměť nebo složku globální balíčky celého systému.</span><span class="sxs-lookup"><span data-stu-id="5ae72-216">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="5ae72-217">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="5ae72-217">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="5ae72-218">Nabízených oznámení balíček na server a vydává je.</span><span class="sxs-lookup"><span data-stu-id="5ae72-218">Pushes a package to the server and publishes it.</span></span>

## <a name="examples"></a><span data-ttu-id="5ae72-219">Příklady</span><span class="sxs-lookup"><span data-stu-id="5ae72-219">Examples</span></span>

<span data-ttu-id="5ae72-220">Inicializace ukázkové aplikace konzoly .NET Core, která můžete zkompilovat a spustit:</span><span class="sxs-lookup"><span data-stu-id="5ae72-220">Initialize a sample .NET Core console application that can be compiled and run:</span></span>

`dotnet new console`

<span data-ttu-id="5ae72-221">Obnovte závislosti pro danou aplikaci:</span><span class="sxs-lookup"><span data-stu-id="5ae72-221">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="5ae72-222">Sestavte projekt a jeho závislosti v daném adresáři:</span><span class="sxs-lookup"><span data-stu-id="5ae72-222">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="5ae72-223">Spustit framework závislé aplikace s názvem `myapp.dll`:</span><span class="sxs-lookup"><span data-stu-id="5ae72-223">Run a framework-dependent app named `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="5ae72-224">Proměnné prostředí</span><span class="sxs-lookup"><span data-stu-id="5ae72-224">Environment variables</span></span>

`DOTNET_PACKAGES`

<span data-ttu-id="5ae72-225">Primární balíček mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="5ae72-225">The primary package cache.</span></span> <span data-ttu-id="5ae72-226">Pokud není nastavena, je standardně `$HOME/.nuget/packages` v systému Unix nebo `%HOME%\NuGet\Packages` v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5ae72-226">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="5ae72-227">Určuje umístění údržby indexu má použít pro sdílené hostitele při načítání modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="5ae72-227">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="5ae72-228">Určuje, jestli se data o využití nástroje .NET Core shromažďuje a odesílá společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5ae72-228">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="5ae72-229">Nastavte na `true` vyjádřit výslovný nesouhlas funkci telemetrie (hodnoty `true`, `1`, nebo `yes` přijata) nastavena, jinak hodnota `false` k vyslovení souhlasu s funkcí telemetrie (hodnoty `false`, `0`, nebo `no` přijata).</span><span class="sxs-lookup"><span data-stu-id="5ae72-229">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted); otherwise, set to `false` to opt-in to the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="5ae72-230">Pokud není nastavená, výchozí hodnoty je `false`, a je aktivní funkce telemetrie.</span><span class="sxs-lookup"><span data-stu-id="5ae72-230">If not set, the defaults is `false`, and the telemetry feature is active.</span></span>
