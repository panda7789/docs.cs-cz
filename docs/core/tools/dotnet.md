---
title: "příkaz DotNet - .NET Core rozhraní příkazového řádku"
description: "Další informace o příkazu dotnet (obecný ovladač pro rozhraní .NET Core rozhraní příkazového řádku nástroje) a jeho použití."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: bba8d77cda7538bf008dc0f510f9279d3c695c3d
ms.sourcegitcommit: a19548e5167cbe7e9e58df4ffd8c3b23f17d5c7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2017
---
# <a name="dotnet-command"></a><span data-ttu-id="73401-103">příkaz DotNet.</span><span class="sxs-lookup"><span data-stu-id="73401-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="73401-104">Název</span><span class="sxs-lookup"><span data-stu-id="73401-104">Name</span></span>

<span data-ttu-id="73401-105">`dotnet`-Obecné ovladače pro spouštění příkazy příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="73401-105">`dotnet` - General driver for running the command-line commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="73401-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="73401-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="73401-107">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="73401-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbose] [--version]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="73401-108">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="73401-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [-v|--verbose] [--version]
```
---

## <a name="description"></a><span data-ttu-id="73401-109">Popis</span><span class="sxs-lookup"><span data-stu-id="73401-109">Description</span></span>

<span data-ttu-id="73401-110">`dotnet`je obecný ovladač pro nástrojů rozhraní příkazového řádku (CLI).</span><span class="sxs-lookup"><span data-stu-id="73401-110">`dotnet` is a generic driver for the Command Line Interface (CLI) toolchain.</span></span> <span data-ttu-id="73401-111">Vyvolání sama o sobě poskytuje stručný využití pokyny.</span><span class="sxs-lookup"><span data-stu-id="73401-111">Invoked on its own, it provides brief usage instructions.</span></span>

<span data-ttu-id="73401-112">Každý konkrétní funkce je implementovaná jako příkaz.</span><span class="sxs-lookup"><span data-stu-id="73401-112">Each specific feature is implemented as a command.</span></span> <span data-ttu-id="73401-113">Chcete-li používat funkci, je příkaz zadaný po `dotnet`, jako například [ `dotnet build` ](dotnet-build.md).</span><span class="sxs-lookup"><span data-stu-id="73401-113">In order to use the feature, the command is specified after `dotnet`, such as [`dotnet build`](dotnet-build.md).</span></span> <span data-ttu-id="73401-114">Všechny argumenty následující příkaz jsou vlastní argumenty.</span><span class="sxs-lookup"><span data-stu-id="73401-114">All of the arguments following the command are its own arguments.</span></span>

<span data-ttu-id="73401-115">Pouze `dotnet` slouží jako příkaz svoje vlastní je spuštění [framework závislé aplikace](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="73401-115">The only time `dotnet` is used as a command on its own is to run [framework-dependent apps](../deploying/index.md).</span></span> <span data-ttu-id="73401-116">Zadejte aplikaci DLL po `dotnet` příkaz pro spuštění aplikace (například `dotnet myapp.dll`).</span><span class="sxs-lookup"><span data-stu-id="73401-116">Specify an application DLL after the `dotnet` verb to execute the application (for example, `dotnet myapp.dll`).</span></span>

## <a name="options"></a><span data-ttu-id="73401-117">Možnosti</span><span class="sxs-lookup"><span data-stu-id="73401-117">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="73401-118">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="73401-118">.NET Core 2.x</span></span>](#tab/netcore2x)

`--additionaldeps <PATH>`

<span data-ttu-id="73401-119">Cesta k další *deps.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="73401-119">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="73401-120">Cesta obsahující testování zásad a sestavení testovat.</span><span class="sxs-lookup"><span data-stu-id="73401-120">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="73401-121">Umožňuje výstup diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="73401-121">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="73401-122">Verze nainstalovaného .NET Core runtime se použije ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="73401-122">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="73401-123">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="73401-123">Prints out a short help for the command.</span></span> <span data-ttu-id="73401-124">Pokud pomocí `dotnet`, vytiskne také seznam dostupných příkazů.</span><span class="sxs-lookup"><span data-stu-id="73401-124">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="73401-125">Vytiskne podrobné informace o nástroji příkazového řádku a prostředí, například v aktuálním operačním systému, potvrzení SHA pro verze a další informace.</span><span class="sxs-lookup"><span data-stu-id="73401-125">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="73401-126">Zobrazí souhrn vpřed v žádné sdílené framework candidate.</span><span class="sxs-lookup"><span data-stu-id="73401-126">Rolls forward on no candidate shared framework.</span></span>

`-v|--verbose`

<span data-ttu-id="73401-127">Umožňuje podrobný výstup.</span><span class="sxs-lookup"><span data-stu-id="73401-127">Enables verbose output.</span></span>

`--version`

<span data-ttu-id="73401-128">Vytiskne verzi rozhraní .NET Core SDK používá.</span><span class="sxs-lookup"><span data-stu-id="73401-128">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="73401-129">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="73401-129">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="73401-130">Cesta obsahující testování zásad a sestavení testovat.</span><span class="sxs-lookup"><span data-stu-id="73401-130">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="73401-131">Umožňuje výstup diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="73401-131">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="73401-132">Verze nainstalovaného .NET Core runtime se použije ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="73401-132">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="73401-133">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="73401-133">Prints out a short help for the command.</span></span> <span data-ttu-id="73401-134">Pokud pomocí `dotnet`, vytiskne také seznam dostupných příkazů.</span><span class="sxs-lookup"><span data-stu-id="73401-134">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="73401-135">Vytiskne podrobné informace o nástroji příkazového řádku a prostředí, například v aktuálním operačním systému, potvrzení SHA pro verze a další informace.</span><span class="sxs-lookup"><span data-stu-id="73401-135">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`-v|--verbose`

<span data-ttu-id="73401-136">Umožňuje podrobný výstup.</span><span class="sxs-lookup"><span data-stu-id="73401-136">Enables verbose output.</span></span>

`--version`

<span data-ttu-id="73401-137">Vytiskne verzi rozhraní .NET Core SDK používá.</span><span class="sxs-lookup"><span data-stu-id="73401-137">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="73401-138">příkazy DotNet.</span><span class="sxs-lookup"><span data-stu-id="73401-138">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="73401-139">Obecné</span><span class="sxs-lookup"><span data-stu-id="73401-139">General</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="73401-140">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="73401-140">.NET Core 2.x</span></span>](#tab/netcore2x)

| <span data-ttu-id="73401-141">Příkaz</span><span class="sxs-lookup"><span data-stu-id="73401-141">Command</span></span>                             | <span data-ttu-id="73401-142">Funkce</span><span class="sxs-lookup"><span data-stu-id="73401-142">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="73401-143">sestavení DotNet.</span><span class="sxs-lookup"><span data-stu-id="73401-143">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="73401-144">Sestavení aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="73401-144">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="73401-145">Vyčištění DotNet.</span><span class="sxs-lookup"><span data-stu-id="73401-145">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="73401-146">Čistá sestavení výstupy.</span><span class="sxs-lookup"><span data-stu-id="73401-146">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="73401-147">Nápověda DotNet.</span><span class="sxs-lookup"><span data-stu-id="73401-147">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="73401-148">Zobrazí podrobnější online dokumentaci pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="73401-148">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="73401-149">migrace DotNet.</span><span class="sxs-lookup"><span data-stu-id="73401-149">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="73401-150">Migruje platný Preview 2 projektu na .NET Core SDK 1.0 projekt.</span><span class="sxs-lookup"><span data-stu-id="73401-150">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="73401-151">msbuild DotNet.</span><span class="sxs-lookup"><span data-stu-id="73401-151">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="73401-152">Poskytuje přístup k MSBuild příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="73401-152">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="73401-153">nové DotNet.</span><span class="sxs-lookup"><span data-stu-id="73401-153">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="73401-154">Inicializuje jazyka C# nebo projekt F # pro dané šablony.</span><span class="sxs-lookup"><span data-stu-id="73401-154">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="73401-155">pack DotNet.</span><span class="sxs-lookup"><span data-stu-id="73401-155">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="73401-156">Vytvoří balíček NuGet kódu.</span><span class="sxs-lookup"><span data-stu-id="73401-156">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="73401-157">publikování DotNet.</span><span class="sxs-lookup"><span data-stu-id="73401-157">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="73401-158">Publikuje aplikace rozhraní .NET framework závislé nebo úplný a samostatný.</span><span class="sxs-lookup"><span data-stu-id="73401-158">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="73401-159">obnovení DotNet.</span><span class="sxs-lookup"><span data-stu-id="73401-159">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="73401-160">Obnoví závislosti pro dané aplikaci.</span><span class="sxs-lookup"><span data-stu-id="73401-160">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="73401-161">Spustit DotNet.</span><span class="sxs-lookup"><span data-stu-id="73401-161">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="73401-162">Spustí aplikaci ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="73401-162">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="73401-163">SLN – DotNet.</span><span class="sxs-lookup"><span data-stu-id="73401-163">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="73401-164">Možnosti pro přidání, odebrání a seznam projekty v řešení souboru.</span><span class="sxs-lookup"><span data-stu-id="73401-164">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="73401-165">úložiště DotNet.</span><span class="sxs-lookup"><span data-stu-id="73401-165">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="73401-166">Uchovává sestavení v úložišti balíček modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="73401-166">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="73401-167">test DotNet.</span><span class="sxs-lookup"><span data-stu-id="73401-167">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="73401-168">Spustí testy použitím nástroje test runner.</span><span class="sxs-lookup"><span data-stu-id="73401-168">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="73401-169">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="73401-169">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="73401-170">Příkaz</span><span class="sxs-lookup"><span data-stu-id="73401-170">Command</span></span>                             | <span data-ttu-id="73401-171">Funkce</span><span class="sxs-lookup"><span data-stu-id="73401-171">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="73401-172">sestavení DotNet.</span><span class="sxs-lookup"><span data-stu-id="73401-172">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="73401-173">Sestavení aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="73401-173">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="73401-174">Vyčištění DotNet.</span><span class="sxs-lookup"><span data-stu-id="73401-174">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="73401-175">Čistá sestavení výstupy.</span><span class="sxs-lookup"><span data-stu-id="73401-175">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="73401-176">migrace DotNet.</span><span class="sxs-lookup"><span data-stu-id="73401-176">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="73401-177">Migruje platný Preview 2 projektu na .NET Core SDK 1.0 projekt.</span><span class="sxs-lookup"><span data-stu-id="73401-177">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="73401-178">msbuild DotNet.</span><span class="sxs-lookup"><span data-stu-id="73401-178">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="73401-179">Poskytuje přístup k MSBuild příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="73401-179">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="73401-180">nové DotNet.</span><span class="sxs-lookup"><span data-stu-id="73401-180">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="73401-181">Inicializuje jazyka C# nebo projekt F # pro dané šablony.</span><span class="sxs-lookup"><span data-stu-id="73401-181">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="73401-182">pack DotNet.</span><span class="sxs-lookup"><span data-stu-id="73401-182">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="73401-183">Vytvoří balíček NuGet kódu.</span><span class="sxs-lookup"><span data-stu-id="73401-183">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="73401-184">publikování DotNet.</span><span class="sxs-lookup"><span data-stu-id="73401-184">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="73401-185">Publikuje aplikace rozhraní .NET framework závislé nebo úplný a samostatný.</span><span class="sxs-lookup"><span data-stu-id="73401-185">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="73401-186">obnovení DotNet.</span><span class="sxs-lookup"><span data-stu-id="73401-186">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="73401-187">Obnoví závislosti pro dané aplikaci.</span><span class="sxs-lookup"><span data-stu-id="73401-187">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="73401-188">Spustit DotNet.</span><span class="sxs-lookup"><span data-stu-id="73401-188">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="73401-189">Spustí aplikaci ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="73401-189">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="73401-190">SLN – DotNet.</span><span class="sxs-lookup"><span data-stu-id="73401-190">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="73401-191">Možnosti pro přidání, odebrání a seznam projekty v řešení souboru.</span><span class="sxs-lookup"><span data-stu-id="73401-191">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="73401-192">test DotNet.</span><span class="sxs-lookup"><span data-stu-id="73401-192">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="73401-193">Spustí testy použitím nástroje test runner.</span><span class="sxs-lookup"><span data-stu-id="73401-193">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="73401-194">Odkazy na projekt</span><span class="sxs-lookup"><span data-stu-id="73401-194">Project references</span></span>

<span data-ttu-id="73401-195">Příkaz</span><span class="sxs-lookup"><span data-stu-id="73401-195">Command</span></span> | <span data-ttu-id="73401-196">Funkce</span><span class="sxs-lookup"><span data-stu-id="73401-196">Function</span></span>
--- | ---
[<span data-ttu-id="73401-197">Přidat odkaz DotNet.</span><span class="sxs-lookup"><span data-stu-id="73401-197">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="73401-198">Přidáte odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="73401-198">Add a project reference.</span></span>
[<span data-ttu-id="73401-199">referenční seznam DotNet.</span><span class="sxs-lookup"><span data-stu-id="73401-199">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="73401-200">Zobrazí seznam odkazů projektu.</span><span class="sxs-lookup"><span data-stu-id="73401-200">List project references.</span></span>
[<span data-ttu-id="73401-201">Odebrat odkaz DotNet.</span><span class="sxs-lookup"><span data-stu-id="73401-201">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="73401-202">Odeberte odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="73401-202">Remove a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="73401-203">Balíčky NuGet</span><span class="sxs-lookup"><span data-stu-id="73401-203">NuGet packages</span></span>

<span data-ttu-id="73401-204">Příkaz</span><span class="sxs-lookup"><span data-stu-id="73401-204">Command</span></span> | <span data-ttu-id="73401-205">Funkce</span><span class="sxs-lookup"><span data-stu-id="73401-205">Function</span></span>
--- | ---
[<span data-ttu-id="73401-206">Přidejte balíček DotNet.</span><span class="sxs-lookup"><span data-stu-id="73401-206">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="73401-207">Přidejte balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="73401-207">Add a NuGet package.</span></span>
[<span data-ttu-id="73401-208">Odebrat balíček DotNet.</span><span class="sxs-lookup"><span data-stu-id="73401-208">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="73401-209">Odebrání balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="73401-209">Remove a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="73401-210">Příkazy pro balíčky NuGet</span><span class="sxs-lookup"><span data-stu-id="73401-210">NuGet commands</span></span>

<span data-ttu-id="73401-211">Příkaz</span><span class="sxs-lookup"><span data-stu-id="73401-211">Command</span></span> | <span data-ttu-id="73401-212">Funkce</span><span class="sxs-lookup"><span data-stu-id="73401-212">Function</span></span>
--- | ---
[<span data-ttu-id="73401-213">odstranění nuget DotNet.</span><span class="sxs-lookup"><span data-stu-id="73401-213">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="73401-214">Odstraní nebo unlists balíčku ze serveru.</span><span class="sxs-lookup"><span data-stu-id="73401-214">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="73401-215">místní hodnoty nuget DotNet.</span><span class="sxs-lookup"><span data-stu-id="73401-215">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="73401-216">Vymaže nebo vypíše místní prostředky NuGet například mezipaměti požadavek http, dočasnou vyrovnávací paměť nebo složku globální balíčky celého systému.</span><span class="sxs-lookup"><span data-stu-id="73401-216">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="73401-217">nabízená nuget DotNet.</span><span class="sxs-lookup"><span data-stu-id="73401-217">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="73401-218">Nabízených oznámení balíček na server a vydává je.</span><span class="sxs-lookup"><span data-stu-id="73401-218">Pushes a package to the server and publishes it.</span></span>

## <a name="examples"></a><span data-ttu-id="73401-219">Příklady</span><span class="sxs-lookup"><span data-stu-id="73401-219">Examples</span></span>

<span data-ttu-id="73401-220">Inicializace ukázkové aplikace konzoly .NET Core, která můžete zkompilovat a spustit:</span><span class="sxs-lookup"><span data-stu-id="73401-220">Initialize a sample .NET Core console application that can be compiled and run:</span></span>

`dotnet new console`

<span data-ttu-id="73401-221">Obnovte závislosti pro danou aplikaci:</span><span class="sxs-lookup"><span data-stu-id="73401-221">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="73401-222">Sestavte projekt a jeho závislosti v daném adresáři:</span><span class="sxs-lookup"><span data-stu-id="73401-222">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="73401-223">Spustit framework závislé aplikace s názvem `myapp.dll`:</span><span class="sxs-lookup"><span data-stu-id="73401-223">Run a framework-dependent app named `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="73401-224">Proměnné prostředí</span><span class="sxs-lookup"><span data-stu-id="73401-224">Environment variables</span></span>

`DOTNET_PACKAGES`

<span data-ttu-id="73401-225">Primární balíček mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="73401-225">The primary package cache.</span></span> <span data-ttu-id="73401-226">Pokud není nastavena, je standardně `$HOME/.nuget/packages` v systému Unix nebo `%HOME%\NuGet\Packages` v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="73401-226">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="73401-227">Určuje umístění údržby indexu má použít pro sdílené hostitele při načítání modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="73401-227">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="73401-228">Určuje, jestli se data o využití nástroje .NET Core shromažďuje a odesílá společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="73401-228">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="73401-229">Nastavte na `true` vyjádřit výslovný nesouhlas funkci telemetrie (hodnoty `true`, `1`, nebo `yes` přijata) nastavena, jinak hodnota `false` k vyslovení souhlasu s funkcí telemetrie (hodnoty `false`, `0`, nebo `no` přijata).</span><span class="sxs-lookup"><span data-stu-id="73401-229">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted); otherwise, set to `false` to opt-in to the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="73401-230">Pokud není nastavená, výchozí hodnoty je `false`, a je aktivní funkce telemetrie.</span><span class="sxs-lookup"><span data-stu-id="73401-230">If not set, the defaults is `false`, and the telemetry feature is active.</span></span>
