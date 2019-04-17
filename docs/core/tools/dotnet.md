---
title: příkaz DotNet
description: Další informace o příkazu dotnet (obecný ovladač pro nástroje .NET Core CLI) a jeho použití.
ms.date: 06/04/2018
ms.openlocfilehash: 5278adf44d12e428cdeacf1d475377ce9155c314
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2019
ms.locfileid: "59613002"
---
# <a name="dotnet-command"></a><span data-ttu-id="cbeda-103">příkaz DotNet</span><span class="sxs-lookup"><span data-stu-id="cbeda-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="cbeda-104">Name</span><span class="sxs-lookup"><span data-stu-id="cbeda-104">Name</span></span>

<span data-ttu-id="cbeda-105">`dotnet` – Nástroj pro správu zdrojového kódu .NET a binární soubory.</span><span class="sxs-lookup"><span data-stu-id="cbeda-105">`dotnet` - A tool for managing .NET source code and binaries.</span></span>

## <a name="synopsis"></a><span data-ttu-id="cbeda-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="cbeda-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="cbeda-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="cbeda-107">.NET Core 2.1</span></span>](#tab/netcore21)

```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="cbeda-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="cbeda-108">.NET Core 2.0</span></span>](#tab/netcore20)

```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="cbeda-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="cbeda-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [-v|--verbosity] [--version]
```

---

## <a name="description"></a><span data-ttu-id="cbeda-110">Popis</span><span class="sxs-lookup"><span data-stu-id="cbeda-110">Description</span></span>

<span data-ttu-id="cbeda-111">`dotnet` je nástroj pro správu zdrojového kódu .NET a binární soubory.</span><span class="sxs-lookup"><span data-stu-id="cbeda-111">`dotnet` is a tool for managing .NET source code and binaries.</span></span> <span data-ttu-id="cbeda-112">Uvádí příkazy, které provádějí konkrétní úlohy, jako například [ `dotnet build` ](dotnet-build.md) a [ `dotnet run` ](dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="cbeda-112">It exposes commands that perform specific tasks, such as [`dotnet build`](dotnet-build.md) and [`dotnet run`](dotnet-run.md).</span></span> <span data-ttu-id="cbeda-113">Každý příkaz definuje vlastní argumenty.</span><span class="sxs-lookup"><span data-stu-id="cbeda-113">Each command defines its own arguments.</span></span> <span data-ttu-id="cbeda-114">Typ `--help` po každém z nich pro přístup k stručný dokumentace nápovědy.</span><span class="sxs-lookup"><span data-stu-id="cbeda-114">Type `--help` after each command to access brief help documentation.</span></span>

<span data-ttu-id="cbeda-115">`dotnet` je možné ke spouštění aplikací, tak, že zadáte aplikaci knihovny DLL, jako například `dotnet myapp.dll`.</span><span class="sxs-lookup"><span data-stu-id="cbeda-115">`dotnet` can be used to run applications, by specifying an application DLL, such as `dotnet myapp.dll`.</span></span> <span data-ttu-id="cbeda-116">Zobrazit [nasazení aplikace .NET Core](../deploying/index.md) pro další informace o možnosti nasazení.</span><span class="sxs-lookup"><span data-stu-id="cbeda-116">See [.NET Core application deployment](../deploying/index.md) for to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="cbeda-117">Možnosti</span><span class="sxs-lookup"><span data-stu-id="cbeda-117">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="cbeda-118">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="cbeda-118">.NET Core 2.1</span></span>](#tab/netcore21)

`--additional-deps <PATH>`

<span data-ttu-id="cbeda-119">Cesta k dalším *deps.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="cbeda-119">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="cbeda-120">Cestu, která obsahuje testování zásad a sestavení testu.</span><span class="sxs-lookup"><span data-stu-id="cbeda-120">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="cbeda-121">Umožňuje diagnostický výstup.</span><span class="sxs-lookup"><span data-stu-id="cbeda-121">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="cbeda-122">Verze modulu runtime .NET Core se použije ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="cbeda-122">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="cbeda-123">Dokumentace pro zadaný příkaz, například vytiskne `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="cbeda-123">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="cbeda-124">`dotnet --help` Vypíše seznam dostupných příkazů.</span><span class="sxs-lookup"><span data-stu-id="cbeda-124">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="cbeda-125">Vytiskne podrobné informace o instalaci .NET Core a prostředí počítače, jako je například aktuální operační systém a verze .NET Core SHA potvrzení.</span><span class="sxs-lookup"><span data-stu-id="cbeda-125">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--list-runtimes`

<span data-ttu-id="cbeda-126">Zobrazuje nainstalované moduly runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cbeda-126">Displays the installed .NET Core runtimes.</span></span>

`--list-sdks`

<span data-ttu-id="cbeda-127">Zobrazí nainstalovaný .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="cbeda-127">Displays the installed .NET Core SDKs.</span></span>

`--roll-forward-on-no-candidate-fx <N>`

<span data-ttu-id="cbeda-128">Definuje chování, pokud není k dispozici požadované sdílené architektuře.</span><span class="sxs-lookup"><span data-stu-id="cbeda-128">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="cbeda-129">`N` může být:</span><span class="sxs-lookup"><span data-stu-id="cbeda-129">`N` can be:</span></span>
* <span data-ttu-id="cbeda-130">`0` – Zakažte dopředné posunutí i podverze.</span><span class="sxs-lookup"><span data-stu-id="cbeda-130">`0` - Disable even minor version roll forward.</span></span>
* <span data-ttu-id="cbeda-131">`1` -Posunout vpřed vedlejší verze aktualizace, ale ne hlavní verze.</span><span class="sxs-lookup"><span data-stu-id="cbeda-131">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="cbeda-132">Toto je výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="cbeda-132">This is the default behavior.</span></span>
* <span data-ttu-id="cbeda-133">`2` -Posunout vpřed na vedlejší a hlavní verze.</span><span class="sxs-lookup"><span data-stu-id="cbeda-133">`2` - Roll forward on minor and major versions.</span></span>

 <span data-ttu-id="cbeda-134">Další informace najdete v tématu [posunout vpřed](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="cbeda-134">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="cbeda-135">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="cbeda-135">Sets the verbosity level of the command.</span></span> <span data-ttu-id="cbeda-136">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="cbeda-136">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="cbeda-137">Nepodporované ve každý příkaz; Zobrazit stránka konkrétní příkaz k určení, zda tato možnost je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="cbeda-137">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="cbeda-138">Vytiskne na verzi .NET Core SDK používá.</span><span class="sxs-lookup"><span data-stu-id="cbeda-138">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="cbeda-139">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="cbeda-139">.NET Core 2.0</span></span>](#tab/netcore20)

`--additional-deps <PATH>`

<span data-ttu-id="cbeda-140">Cesta k dalším *deps.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="cbeda-140">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="cbeda-141">Cestu, která obsahuje testování zásad a sestavení testu.</span><span class="sxs-lookup"><span data-stu-id="cbeda-141">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="cbeda-142">Umožňuje diagnostický výstup.</span><span class="sxs-lookup"><span data-stu-id="cbeda-142">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="cbeda-143">Verze modulu runtime .NET Core se použije ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="cbeda-143">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="cbeda-144">Dokumentace pro zadaný příkaz, například vytiskne `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="cbeda-144">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="cbeda-145">`dotnet --help` Vypíše seznam dostupných příkazů.</span><span class="sxs-lookup"><span data-stu-id="cbeda-145">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="cbeda-146">Vytiskne podrobné informace o instalaci .NET Core a prostředí počítače, jako je například aktuální operační systém a verze .NET Core SHA potvrzení.</span><span class="sxs-lookup"><span data-stu-id="cbeda-146">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="cbeda-147">Zakáže podverze Posunutí vpřed, pokud nastavit `0`.</span><span class="sxs-lookup"><span data-stu-id="cbeda-147">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="cbeda-148">Další informace najdete v tématu [posunout vpřed](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="cbeda-148">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="cbeda-149">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="cbeda-149">Sets the verbosity level of the command.</span></span> <span data-ttu-id="cbeda-150">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="cbeda-150">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="cbeda-151">Nepodporované ve každý příkaz; Zobrazit stránka konkrétní příkaz k určení, zda tato možnost je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="cbeda-151">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="cbeda-152">Vytiskne na verzi .NET Core SDK používá.</span><span class="sxs-lookup"><span data-stu-id="cbeda-152">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="cbeda-153">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="cbeda-153">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="cbeda-154">Cestu, která obsahuje testování zásad a sestavení testu.</span><span class="sxs-lookup"><span data-stu-id="cbeda-154">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="cbeda-155">Umožňuje diagnostický výstup.</span><span class="sxs-lookup"><span data-stu-id="cbeda-155">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="cbeda-156">Verze modulu runtime .NET Core se použije ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="cbeda-156">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="cbeda-157">Dokumentace pro zadaný příkaz, například vytiskne `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="cbeda-157">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="cbeda-158">`dotnet --help` Vypíše seznam dostupných příkazů.</span><span class="sxs-lookup"><span data-stu-id="cbeda-158">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="cbeda-159">Vytiskne podrobné informace o instalaci .NET Core a prostředí počítače, jako je například aktuální operační systém a verze .NET Core SHA potvrzení.</span><span class="sxs-lookup"><span data-stu-id="cbeda-159">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="cbeda-160">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="cbeda-160">Sets the verbosity level of the command.</span></span> <span data-ttu-id="cbeda-161">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="cbeda-161">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="cbeda-162">Nepodporované ve každý příkaz; Zobrazit stránka konkrétní příkaz k určení, zda tato možnost je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="cbeda-162">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="cbeda-163">Vytiskne na verzi .NET Core SDK používá.</span><span class="sxs-lookup"><span data-stu-id="cbeda-163">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="cbeda-164">Příkazy dotnet</span><span class="sxs-lookup"><span data-stu-id="cbeda-164">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="cbeda-165">Obecné</span><span class="sxs-lookup"><span data-stu-id="cbeda-165">General</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="cbeda-166">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="cbeda-166">.NET Core 2.1</span></span>](#tab/netcore21)

| <span data-ttu-id="cbeda-167">Příkaz</span><span class="sxs-lookup"><span data-stu-id="cbeda-167">Command</span></span>                                       | <span data-ttu-id="cbeda-168">Funkce</span><span class="sxs-lookup"><span data-stu-id="cbeda-168">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="cbeda-169">dotnet build</span><span class="sxs-lookup"><span data-stu-id="cbeda-169">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="cbeda-170">Sestavení aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cbeda-170">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="cbeda-171">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="cbeda-171">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="cbeda-172">Komunikuje se servery pro spuštění sestavení.</span><span class="sxs-lookup"><span data-stu-id="cbeda-172">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="cbeda-173">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="cbeda-173">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="cbeda-174">Čištění výstupy sestavení.</span><span class="sxs-lookup"><span data-stu-id="cbeda-174">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="cbeda-175">dotnet help</span><span class="sxs-lookup"><span data-stu-id="cbeda-175">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="cbeda-176">Zobrazí podrobnější online dokumentaci pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="cbeda-176">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="cbeda-177">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="cbeda-177">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="cbeda-178">Migruje platný projekt ve verzi Preview 2 na projekt .NET Core SDK 1.0.</span><span class="sxs-lookup"><span data-stu-id="cbeda-178">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="cbeda-179">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="cbeda-179">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="cbeda-180">Poskytuje přístup k příkazovému řádku nástroje MSBuild.</span><span class="sxs-lookup"><span data-stu-id="cbeda-180">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="cbeda-181">dotnet new</span><span class="sxs-lookup"><span data-stu-id="cbeda-181">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="cbeda-182">Inicializuje C# nebo F# projektu pro danou šablonu.</span><span class="sxs-lookup"><span data-stu-id="cbeda-182">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="cbeda-183">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="cbeda-183">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="cbeda-184">Vytvoří balíček NuGet kódu.</span><span class="sxs-lookup"><span data-stu-id="cbeda-184">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="cbeda-185">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="cbeda-185">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="cbeda-186">Publikuje závisí na architektuře nebo samostatné aplikaci .NET.</span><span class="sxs-lookup"><span data-stu-id="cbeda-186">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="cbeda-187">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="cbeda-187">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="cbeda-188">Obnoví závislosti pro danou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="cbeda-188">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="cbeda-189">dotnet run</span><span class="sxs-lookup"><span data-stu-id="cbeda-189">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="cbeda-190">Spuštění aplikace ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="cbeda-190">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="cbeda-191">dotnet run</span><span class="sxs-lookup"><span data-stu-id="cbeda-191">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="cbeda-192">Možnosti pro přidání, odebrání a výpis projektů v souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="cbeda-192">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="cbeda-193">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="cbeda-193">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="cbeda-194">Sestavení se ukládá do úložiště balíčků modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="cbeda-194">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="cbeda-195">dotnet test</span><span class="sxs-lookup"><span data-stu-id="cbeda-195">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="cbeda-196">Spustí testy pomocí nástroje test runner.</span><span class="sxs-lookup"><span data-stu-id="cbeda-196">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="cbeda-197">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="cbeda-197">.NET Core 2.0</span></span>](#tab/netcore20)

| <span data-ttu-id="cbeda-198">Příkaz</span><span class="sxs-lookup"><span data-stu-id="cbeda-198">Command</span></span>                             | <span data-ttu-id="cbeda-199">Funkce</span><span class="sxs-lookup"><span data-stu-id="cbeda-199">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="cbeda-200">dotnet build</span><span class="sxs-lookup"><span data-stu-id="cbeda-200">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="cbeda-201">Sestavení aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cbeda-201">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="cbeda-202">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="cbeda-202">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="cbeda-203">Čištění výstupy sestavení.</span><span class="sxs-lookup"><span data-stu-id="cbeda-203">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="cbeda-204">dotnet help</span><span class="sxs-lookup"><span data-stu-id="cbeda-204">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="cbeda-205">Zobrazí podrobnější online dokumentaci pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="cbeda-205">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="cbeda-206">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="cbeda-206">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="cbeda-207">Migruje platný projekt ve verzi Preview 2 na projekt .NET Core SDK 1.0.</span><span class="sxs-lookup"><span data-stu-id="cbeda-207">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="cbeda-208">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="cbeda-208">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="cbeda-209">Poskytuje přístup k příkazovému řádku nástroje MSBuild.</span><span class="sxs-lookup"><span data-stu-id="cbeda-209">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="cbeda-210">dotnet new</span><span class="sxs-lookup"><span data-stu-id="cbeda-210">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="cbeda-211">Inicializuje C# nebo F# projektu pro danou šablonu.</span><span class="sxs-lookup"><span data-stu-id="cbeda-211">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="cbeda-212">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="cbeda-212">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="cbeda-213">Vytvoří balíček NuGet kódu.</span><span class="sxs-lookup"><span data-stu-id="cbeda-213">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="cbeda-214">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="cbeda-214">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="cbeda-215">Publikuje závisí na architektuře nebo samostatné aplikaci .NET.</span><span class="sxs-lookup"><span data-stu-id="cbeda-215">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="cbeda-216">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="cbeda-216">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="cbeda-217">Obnoví závislosti pro danou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="cbeda-217">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="cbeda-218">dotnet run</span><span class="sxs-lookup"><span data-stu-id="cbeda-218">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="cbeda-219">Spuštění aplikace ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="cbeda-219">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="cbeda-220">dotnet run</span><span class="sxs-lookup"><span data-stu-id="cbeda-220">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="cbeda-221">Možnosti pro přidání, odebrání a výpis projektů v souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="cbeda-221">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="cbeda-222">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="cbeda-222">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="cbeda-223">Sestavení se ukládá do úložiště balíčků modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="cbeda-223">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="cbeda-224">dotnet test</span><span class="sxs-lookup"><span data-stu-id="cbeda-224">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="cbeda-225">Spustí testy pomocí nástroje test runner.</span><span class="sxs-lookup"><span data-stu-id="cbeda-225">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="cbeda-226">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="cbeda-226">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="cbeda-227">Příkaz</span><span class="sxs-lookup"><span data-stu-id="cbeda-227">Command</span></span>                             | <span data-ttu-id="cbeda-228">Funkce</span><span class="sxs-lookup"><span data-stu-id="cbeda-228">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="cbeda-229">dotnet build</span><span class="sxs-lookup"><span data-stu-id="cbeda-229">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="cbeda-230">Sestavení aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cbeda-230">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="cbeda-231">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="cbeda-231">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="cbeda-232">Čištění výstupy sestavení.</span><span class="sxs-lookup"><span data-stu-id="cbeda-232">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="cbeda-233">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="cbeda-233">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="cbeda-234">Migruje platný projekt ve verzi Preview 2 na projekt .NET Core SDK 1.0.</span><span class="sxs-lookup"><span data-stu-id="cbeda-234">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="cbeda-235">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="cbeda-235">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="cbeda-236">Poskytuje přístup k příkazovému řádku nástroje MSBuild.</span><span class="sxs-lookup"><span data-stu-id="cbeda-236">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="cbeda-237">dotnet new</span><span class="sxs-lookup"><span data-stu-id="cbeda-237">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="cbeda-238">Inicializuje C# nebo F# projektu pro danou šablonu.</span><span class="sxs-lookup"><span data-stu-id="cbeda-238">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="cbeda-239">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="cbeda-239">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="cbeda-240">Vytvoří balíček NuGet kódu.</span><span class="sxs-lookup"><span data-stu-id="cbeda-240">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="cbeda-241">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="cbeda-241">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="cbeda-242">Publikuje závisí na architektuře nebo samostatné aplikaci .NET.</span><span class="sxs-lookup"><span data-stu-id="cbeda-242">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="cbeda-243">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="cbeda-243">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="cbeda-244">Obnoví závislosti pro danou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="cbeda-244">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="cbeda-245">dotnet run</span><span class="sxs-lookup"><span data-stu-id="cbeda-245">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="cbeda-246">Spuštění aplikace ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="cbeda-246">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="cbeda-247">dotnet run</span><span class="sxs-lookup"><span data-stu-id="cbeda-247">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="cbeda-248">Možnosti pro přidání, odebrání a výpis projektů v souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="cbeda-248">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="cbeda-249">dotnet test</span><span class="sxs-lookup"><span data-stu-id="cbeda-249">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="cbeda-250">Spustí testy pomocí nástroje test runner.</span><span class="sxs-lookup"><span data-stu-id="cbeda-250">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="cbeda-251">Odkazy na projekt</span><span class="sxs-lookup"><span data-stu-id="cbeda-251">Project references</span></span>

<span data-ttu-id="cbeda-252">Příkaz</span><span class="sxs-lookup"><span data-stu-id="cbeda-252">Command</span></span> | <span data-ttu-id="cbeda-253">Funkce</span><span class="sxs-lookup"><span data-stu-id="cbeda-253">Function</span></span>
--- | ---
[<span data-ttu-id="cbeda-254">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="cbeda-254">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="cbeda-255">Přidá odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="cbeda-255">Adds a project reference.</span></span>
[<span data-ttu-id="cbeda-256">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="cbeda-256">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="cbeda-257">Obsahuje odkazy na projekt.</span><span class="sxs-lookup"><span data-stu-id="cbeda-257">Lists project references.</span></span>
[<span data-ttu-id="cbeda-258">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="cbeda-258">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="cbeda-259">Odebere odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="cbeda-259">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="cbeda-260">Balíčky NuGet</span><span class="sxs-lookup"><span data-stu-id="cbeda-260">NuGet packages</span></span>

<span data-ttu-id="cbeda-261">Příkaz</span><span class="sxs-lookup"><span data-stu-id="cbeda-261">Command</span></span> | <span data-ttu-id="cbeda-262">Funkce</span><span class="sxs-lookup"><span data-stu-id="cbeda-262">Function</span></span>
--- | ---
[<span data-ttu-id="cbeda-263">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="cbeda-263">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="cbeda-264">Přidá balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="cbeda-264">Adds a NuGet package.</span></span>
[<span data-ttu-id="cbeda-265">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="cbeda-265">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="cbeda-266">Odebere balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="cbeda-266">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="cbeda-267">Příkazy pro balíčky NuGet</span><span class="sxs-lookup"><span data-stu-id="cbeda-267">NuGet commands</span></span>

<span data-ttu-id="cbeda-268">Příkaz</span><span class="sxs-lookup"><span data-stu-id="cbeda-268">Command</span></span> | <span data-ttu-id="cbeda-269">Funkce</span><span class="sxs-lookup"><span data-stu-id="cbeda-269">Function</span></span>
--- | ---
[<span data-ttu-id="cbeda-270">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="cbeda-270">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="cbeda-271">Odstraní nebo unlists balíčku ze serveru.</span><span class="sxs-lookup"><span data-stu-id="cbeda-271">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="cbeda-272">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="cbeda-272">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="cbeda-273">Vymaže nebo vypíše místní prostředky NuGet, třeba mezipaměť požadavku http, dočasná mezipaměť nebo celý počítač globální složku balíčků.</span><span class="sxs-lookup"><span data-stu-id="cbeda-273">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="cbeda-274">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="cbeda-274">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="cbeda-275">Odešle balíček na server a publikuje ji.</span><span class="sxs-lookup"><span data-stu-id="cbeda-275">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tools-commands"></a><span data-ttu-id="cbeda-276">Globální příkazy nástroje</span><span class="sxs-lookup"><span data-stu-id="cbeda-276">Global Tools commands</span></span>

<span data-ttu-id="cbeda-277">[Globální nástroje .NET core](global-tools.md) jsou k dispozici od verze rozhraní .NET Core SDK 2.1.300:</span><span class="sxs-lookup"><span data-stu-id="cbeda-277">[.NET Core Global Tools](global-tools.md) are available starting with .NET Core SDK 2.1.300:</span></span>

<span data-ttu-id="cbeda-278">Příkaz</span><span class="sxs-lookup"><span data-stu-id="cbeda-278">Command</span></span> | <span data-ttu-id="cbeda-279">Funkce</span><span class="sxs-lookup"><span data-stu-id="cbeda-279">Function</span></span>
--- | ---
[<span data-ttu-id="cbeda-280">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="cbeda-280">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="cbeda-281">Globální nástroj nainstaluje na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="cbeda-281">Installs a Global Tool on your machine.</span></span>
[<span data-ttu-id="cbeda-282">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="cbeda-282">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="cbeda-283">Vypíše všechny globální nástroje aktuálně nainstalované ve výchozím adresáři na svém počítači nebo v zadané cestě.</span><span class="sxs-lookup"><span data-stu-id="cbeda-283">Lists all Global Tools currently installed in the default directory on your machine or in the specified path.</span></span>
[<span data-ttu-id="cbeda-284">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="cbeda-284">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="cbeda-285">Odinstaluje nástroj globální z vašeho počítače.</span><span class="sxs-lookup"><span data-stu-id="cbeda-285">Uninstalls a Global Tool from your machine.</span></span>
[<span data-ttu-id="cbeda-286">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="cbeda-286">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="cbeda-287">Aktualizuje nástroj globální na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="cbeda-287">Updates a Global Tool on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="cbeda-288">Další nástroje</span><span class="sxs-lookup"><span data-stu-id="cbeda-288">Additional tools</span></span>

<span data-ttu-id="cbeda-289">Počínaje řadou nástrojů, které byly k dispozici pouze v jednotlivých projektů pomocí sady .NET Core SDK 2.1.300, `DotnetCliToolReference` jsou teď k dispozici jako součást sady .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="cbeda-289">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="cbeda-290">Tyto nástroje jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="cbeda-290">These tools are listed in the following table:</span></span>

| <span data-ttu-id="cbeda-291">Nástroj</span><span class="sxs-lookup"><span data-stu-id="cbeda-291">Tool</span></span>                                              | <span data-ttu-id="cbeda-292">Funkce</span><span class="sxs-lookup"><span data-stu-id="cbeda-292">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="cbeda-293">dev-certs</span><span class="sxs-lookup"><span data-stu-id="cbeda-293">dev-certs</span></span>                                         | <span data-ttu-id="cbeda-294">Vytváří a spravuje certifikáty vývoje.</span><span class="sxs-lookup"><span data-stu-id="cbeda-294">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="cbeda-295">EF</span><span class="sxs-lookup"><span data-stu-id="cbeda-295">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="cbeda-296">Nástroje příkazového řádku Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="cbeda-296">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="cbeda-297">sql-cache</span><span class="sxs-lookup"><span data-stu-id="cbeda-297">sql-cache</span></span>                                         | <span data-ttu-id="cbeda-298">Nástroje příkazového řádku systému SQL Server mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="cbeda-298">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="cbeda-299">user-secrets</span><span class="sxs-lookup"><span data-stu-id="cbeda-299">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="cbeda-300">Slouží ke správě tajných kódů uživatelů vývoje.</span><span class="sxs-lookup"><span data-stu-id="cbeda-300">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="cbeda-301">Sledování</span><span class="sxs-lookup"><span data-stu-id="cbeda-301">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="cbeda-302">Spustí se soubor sledování, které se spustí příkaz, když se změní soubory.</span><span class="sxs-lookup"><span data-stu-id="cbeda-302">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="cbeda-303">Další informace o jednotlivých nástrojích, zadejte `dotnet <tool-name> --help`.</span><span class="sxs-lookup"><span data-stu-id="cbeda-303">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="cbeda-304">Příklady</span><span class="sxs-lookup"><span data-stu-id="cbeda-304">Examples</span></span>

<span data-ttu-id="cbeda-305">Vytvoří novou konzolovou aplikaci .NET Core:</span><span class="sxs-lookup"><span data-stu-id="cbeda-305">Creates a new .NET Core console application:</span></span>

`dotnet new console`

<span data-ttu-id="cbeda-306">Obnovte závislosti pro dané aplikace:</span><span class="sxs-lookup"><span data-stu-id="cbeda-306">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="cbeda-307">Sestavení projektu a jeho závislosti v daném adresáři:</span><span class="sxs-lookup"><span data-stu-id="cbeda-307">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="cbeda-308">Spustit aplikaci knihovny DLL, jako například `myapp.dll`:</span><span class="sxs-lookup"><span data-stu-id="cbeda-308">Run an application DLL, such as `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="cbeda-309">Proměnné prostředí</span><span class="sxs-lookup"><span data-stu-id="cbeda-309">Environment variables</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="cbeda-310">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="cbeda-310">.NET Core 2.1</span></span>](#tab/netcore21)

`DOTNET_PACKAGES`

<span data-ttu-id="cbeda-311">Primární balíček mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="cbeda-311">The primary package cache.</span></span> <span data-ttu-id="cbeda-312">Pokud není nastavená, použije se výchozí `$HOME/.nuget/packages` v systému Unix nebo `%HOME%\NuGet\Packages` na Windows.</span><span class="sxs-lookup"><span data-stu-id="cbeda-312">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="cbeda-313">Určuje umístění index údržby pro použití sdílené hostitele při načítání modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="cbeda-313">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="cbeda-314">Určuje, zda data o využití nástroje .NET Core je shromažďovat a odesílat do Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="cbeda-314">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="cbeda-315">Nastavte na `true` odhlásit funkce telemetrie (hodnoty `true`, `1`, nebo `yes` přijetí).</span><span class="sxs-lookup"><span data-stu-id="cbeda-315">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="cbeda-316">V opačném případě nastavte na `false` do funkce telemetrie (hodnoty `false`, `0`, nebo `no` přijetí).</span><span class="sxs-lookup"><span data-stu-id="cbeda-316">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="cbeda-317">Pokud není nastavený, výchozí hodnota je `false` a funkce telemetrie je aktivní.</span><span class="sxs-lookup"><span data-stu-id="cbeda-317">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="cbeda-318">Určuje, zda modul runtime .NET Core, sdílené architektuře nebo sady SDK jsou vyřešené z globálního místa.</span><span class="sxs-lookup"><span data-stu-id="cbeda-318">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="cbeda-319">Pokud není nastavená, použije se výchozí `true`.</span><span class="sxs-lookup"><span data-stu-id="cbeda-319">If not set, it defaults to `true`.</span></span> <span data-ttu-id="cbeda-320">Nastavte na `false` se vyřešit z globálního místa a mají izolované instalace .NET Core (hodnoty `0` nebo `false` jsou přijímány).</span><span class="sxs-lookup"><span data-stu-id="cbeda-320">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="cbeda-321">Další informace o víceúrovňových vyhledávání najdete v tématu [víceúrovňovými SharedFX vyhledávání](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="cbeda-321">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

<span data-ttu-id="cbeda-322">Zakáže podverze Posunutí vpřed, pokud nastavit `0`.</span><span class="sxs-lookup"><span data-stu-id="cbeda-322">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="cbeda-323">Další informace najdete v tématu [posunout vpřed](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="cbeda-323">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="cbeda-324">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="cbeda-324">.NET Core 2.0</span></span>](#tab/netcore20)

`DOTNET_PACKAGES`

<span data-ttu-id="cbeda-325">Primární balíček mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="cbeda-325">The primary package cache.</span></span> <span data-ttu-id="cbeda-326">Pokud není nastavená, použije se výchozí `$HOME/.nuget/packages` v systému Unix nebo `%HOME%\NuGet\Packages` na Windows.</span><span class="sxs-lookup"><span data-stu-id="cbeda-326">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="cbeda-327">Určuje umístění index údržby pro použití sdílené hostitele při načítání modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="cbeda-327">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="cbeda-328">Určuje, zda data o využití nástroje .NET Core je shromažďovat a odesílat do Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="cbeda-328">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="cbeda-329">Nastavte na `true` odhlásit funkce telemetrie (hodnoty `true`, `1`, nebo `yes` přijetí).</span><span class="sxs-lookup"><span data-stu-id="cbeda-329">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="cbeda-330">V opačném případě nastavte na `false` do funkce telemetrie (hodnoty `false`, `0`, nebo `no` přijetí).</span><span class="sxs-lookup"><span data-stu-id="cbeda-330">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="cbeda-331">Pokud není nastavený, výchozí hodnota je `false` a funkce telemetrie je aktivní.</span><span class="sxs-lookup"><span data-stu-id="cbeda-331">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="cbeda-332">Určuje, zda modul runtime .NET Core, sdílené architektuře nebo sady SDK jsou vyřešené z globálního místa.</span><span class="sxs-lookup"><span data-stu-id="cbeda-332">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="cbeda-333">Pokud není nastavená, použije se výchozí `true`.</span><span class="sxs-lookup"><span data-stu-id="cbeda-333">If not set, it defaults to `true`.</span></span> <span data-ttu-id="cbeda-334">Nastavte na `false` se vyřešit z globálního místa a mají izolované instalace .NET Core (hodnoty `0` nebo `false` jsou přijímány).</span><span class="sxs-lookup"><span data-stu-id="cbeda-334">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="cbeda-335">Další informace o víceúrovňových vyhledávání najdete v tématu [víceúrovňovými SharedFX vyhledávání](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="cbeda-335">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="cbeda-336">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="cbeda-336">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="cbeda-337">Primární balíček mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="cbeda-337">The primary package cache.</span></span> <span data-ttu-id="cbeda-338">Pokud není nastavená, použije se výchozí `$HOME/.nuget/packages` v systému Unix nebo `%HOME%\NuGet\Packages` na Windows.</span><span class="sxs-lookup"><span data-stu-id="cbeda-338">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="cbeda-339">Určuje umístění index údržby pro použití sdílené hostitele při načítání modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="cbeda-339">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="cbeda-340">Určuje, zda data o využití nástroje .NET Core je shromažďovat a odesílat do Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="cbeda-340">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="cbeda-341">Nastavte na `true` odhlásit funkce telemetrie (hodnoty `true`, `1`, nebo `yes` přijetí).</span><span class="sxs-lookup"><span data-stu-id="cbeda-341">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="cbeda-342">V opačném případě nastavte na `false` do funkce telemetrie (hodnoty `false`, `0`, nebo `no` přijetí).</span><span class="sxs-lookup"><span data-stu-id="cbeda-342">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="cbeda-343">Pokud není nastavený, výchozí hodnota je `false` a funkce telemetrie je aktivní.</span><span class="sxs-lookup"><span data-stu-id="cbeda-343">If not set, the default is `false` and the telemetry feature is active.</span></span>

---
