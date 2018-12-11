---
title: příkaz DotNet
description: Další informace o příkazu dotnet (obecný ovladač pro nástroje .NET Core CLI) a jeho použití.
ms.date: 06/04/2018
ms.openlocfilehash: 081f295cc71c3cd46de465efb12f131e7b2d36d9
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170838"
---
# <a name="dotnet-command"></a><span data-ttu-id="17d79-103">příkaz DotNet</span><span class="sxs-lookup"><span data-stu-id="17d79-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="17d79-104">Název</span><span class="sxs-lookup"><span data-stu-id="17d79-104">Name</span></span>

<span data-ttu-id="17d79-105">`dotnet` – Nástroj pro správu zdrojového kódu .NET a binární soubory.</span><span class="sxs-lookup"><span data-stu-id="17d79-105">`dotnet` - A tool for managing .NET source code and binaries.</span></span>

## <a name="synopsis"></a><span data-ttu-id="17d79-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="17d79-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="17d79-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="17d79-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="17d79-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="17d79-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="17d79-109">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="17d79-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [-v|--verbosity] [--version]
```
---

## <a name="description"></a><span data-ttu-id="17d79-110">Popis</span><span class="sxs-lookup"><span data-stu-id="17d79-110">Description</span></span>

<span data-ttu-id="17d79-111">`dotnet` je nástroj pro správu zdrojového kódu .NET a binární soubory.</span><span class="sxs-lookup"><span data-stu-id="17d79-111">`dotnet` is a tool for managing .NET source code and binaries.</span></span> <span data-ttu-id="17d79-112">Uvádí příkazy, které provádějí konkrétní úlohy, jako například [ `dotnet build` ](dotnet-build.md) a [ `dotnet run` ](dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="17d79-112">It exposes commands that perform specific tasks, such as [`dotnet build`](dotnet-build.md) and [`dotnet run`](dotnet-run.md).</span></span> <span data-ttu-id="17d79-113">Každý příkaz definuje vlastní argumenty.</span><span class="sxs-lookup"><span data-stu-id="17d79-113">Each command defines its own arguments.</span></span> <span data-ttu-id="17d79-114">Typ `--help` po každém z nich pro přístup k stručný dokumentace nápovědy.</span><span class="sxs-lookup"><span data-stu-id="17d79-114">Type `--help` after each command to access brief help documentation.</span></span>

<span data-ttu-id="17d79-115">`dotnet` je možné ke spouštění aplikací, tak, že zadáte aplikaci knihovny DLL, jako například `dotnet myapp.dll`.</span><span class="sxs-lookup"><span data-stu-id="17d79-115">`dotnet` can be used to run applications, by specifying an application DLL, such as `dotnet myapp.dll`.</span></span> <span data-ttu-id="17d79-116">Zobrazit [nasazení aplikace .NET Core](../deploying/index.md) pro další informace o možnosti nasazení.</span><span class="sxs-lookup"><span data-stu-id="17d79-116">See [.NET Core application deployment](../deploying/index.md) for to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="17d79-117">Možnosti</span><span class="sxs-lookup"><span data-stu-id="17d79-117">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="17d79-118">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="17d79-118">.NET Core 2.1</span></span>](#tab/netcore21)

`--additional-deps <PATH>`

<span data-ttu-id="17d79-119">Cesta k dalším *deps.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="17d79-119">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="17d79-120">Cestu, která obsahuje testování zásad a sestavení testu.</span><span class="sxs-lookup"><span data-stu-id="17d79-120">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="17d79-121">Umožňuje diagnostický výstup.</span><span class="sxs-lookup"><span data-stu-id="17d79-121">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="17d79-122">Verze modulu runtime .NET Core se použije ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="17d79-122">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="17d79-123">Dokumentace pro zadaný příkaz, například vytiskne `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="17d79-123">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="17d79-124">`dotnet --help` Vypíše seznam dostupných příkazů.</span><span class="sxs-lookup"><span data-stu-id="17d79-124">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="17d79-125">Vytiskne podrobné informace o instalaci .NET Core a prostředí počítače, jako je například aktuální operační systém a verze .NET Core SHA potvrzení.</span><span class="sxs-lookup"><span data-stu-id="17d79-125">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--list-runtimes`

<span data-ttu-id="17d79-126">Zobrazuje nainstalované moduly runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="17d79-126">Displays the installed .NET Core runtimes.</span></span>

`--list-sdks`

<span data-ttu-id="17d79-127">Zobrazí nainstalovaný .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="17d79-127">Displays the installed .NET Core SDKs.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="17d79-128">Zakáže podverze Posunutí vpřed, pokud nastavit `0`.</span><span class="sxs-lookup"><span data-stu-id="17d79-128">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="17d79-129">Další informace najdete v tématu [posunout vpřed](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="17d79-129">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="17d79-130">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="17d79-130">Sets the verbosity level of the command.</span></span> <span data-ttu-id="17d79-131">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="17d79-131">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="17d79-132">Nepodporované ve každý příkaz; Zobrazit stránka konkrétní příkaz k určení, zda tato možnost je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="17d79-132">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="17d79-133">Vytiskne na verzi .NET Core SDK používá.</span><span class="sxs-lookup"><span data-stu-id="17d79-133">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="17d79-134">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="17d79-134">.NET Core 2.0</span></span>](#tab/netcore20)

`--additional-deps <PATH>`

<span data-ttu-id="17d79-135">Cesta k dalším *deps.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="17d79-135">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="17d79-136">Cestu, která obsahuje testování zásad a sestavení testu.</span><span class="sxs-lookup"><span data-stu-id="17d79-136">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="17d79-137">Umožňuje diagnostický výstup.</span><span class="sxs-lookup"><span data-stu-id="17d79-137">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="17d79-138">Verze modulu runtime .NET Core se použije ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="17d79-138">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="17d79-139">Dokumentace pro zadaný příkaz, například vytiskne `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="17d79-139">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="17d79-140">`dotnet --help` Vypíše seznam dostupných příkazů.</span><span class="sxs-lookup"><span data-stu-id="17d79-140">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="17d79-141">Vytiskne podrobné informace o instalaci .NET Core a prostředí počítače, jako je například aktuální operační systém a verze .NET Core SHA potvrzení.</span><span class="sxs-lookup"><span data-stu-id="17d79-141">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="17d79-142">Zakáže podverze Posunutí vpřed, pokud nastavit `0`.</span><span class="sxs-lookup"><span data-stu-id="17d79-142">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="17d79-143">Další informace najdete v tématu [posunout vpřed](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="17d79-143">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="17d79-144">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="17d79-144">Sets the verbosity level of the command.</span></span> <span data-ttu-id="17d79-145">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="17d79-145">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="17d79-146">Nepodporované ve každý příkaz; Zobrazit stránka konkrétní příkaz k určení, zda tato možnost je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="17d79-146">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="17d79-147">Vytiskne na verzi .NET Core SDK používá.</span><span class="sxs-lookup"><span data-stu-id="17d79-147">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="17d79-148">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="17d79-148">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="17d79-149">Cestu, která obsahuje testování zásad a sestavení testu.</span><span class="sxs-lookup"><span data-stu-id="17d79-149">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="17d79-150">Umožňuje diagnostický výstup.</span><span class="sxs-lookup"><span data-stu-id="17d79-150">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="17d79-151">Verze modulu runtime .NET Core se použije ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="17d79-151">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="17d79-152">Dokumentace pro zadaný příkaz, například vytiskne `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="17d79-152">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="17d79-153">`dotnet --help` Vypíše seznam dostupných příkazů.</span><span class="sxs-lookup"><span data-stu-id="17d79-153">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="17d79-154">Vytiskne podrobné informace o instalaci .NET Core a prostředí počítače, jako je například aktuální operační systém a verze .NET Core SHA potvrzení.</span><span class="sxs-lookup"><span data-stu-id="17d79-154">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="17d79-155">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="17d79-155">Sets the verbosity level of the command.</span></span> <span data-ttu-id="17d79-156">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="17d79-156">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="17d79-157">Nepodporované ve každý příkaz; Zobrazit stránka konkrétní příkaz k určení, zda tato možnost je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="17d79-157">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="17d79-158">Vytiskne na verzi .NET Core SDK používá.</span><span class="sxs-lookup"><span data-stu-id="17d79-158">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="17d79-159">příkazy DotNet</span><span class="sxs-lookup"><span data-stu-id="17d79-159">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="17d79-160">Obecné</span><span class="sxs-lookup"><span data-stu-id="17d79-160">General</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="17d79-161">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="17d79-161">.NET Core 2.1</span></span>](#tab/netcore21)

| <span data-ttu-id="17d79-162">Příkaz</span><span class="sxs-lookup"><span data-stu-id="17d79-162">Command</span></span>                                       | <span data-ttu-id="17d79-163">Funkce</span><span class="sxs-lookup"><span data-stu-id="17d79-163">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="17d79-164">dotnet build</span><span class="sxs-lookup"><span data-stu-id="17d79-164">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="17d79-165">Sestavení aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="17d79-165">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="17d79-166">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="17d79-166">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="17d79-167">Komunikuje se servery pro spuštění sestavení.</span><span class="sxs-lookup"><span data-stu-id="17d79-167">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="17d79-168">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="17d79-168">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="17d79-169">Čištění výstupy sestavení.</span><span class="sxs-lookup"><span data-stu-id="17d79-169">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="17d79-170">dotnet help</span><span class="sxs-lookup"><span data-stu-id="17d79-170">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="17d79-171">Zobrazí podrobnější online dokumentaci pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="17d79-171">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="17d79-172">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="17d79-172">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="17d79-173">Migruje platný projekt ve verzi Preview 2 na projekt .NET Core SDK 1.0.</span><span class="sxs-lookup"><span data-stu-id="17d79-173">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="17d79-174">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="17d79-174">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="17d79-175">Poskytuje přístup k příkazovému řádku nástroje MSBuild.</span><span class="sxs-lookup"><span data-stu-id="17d79-175">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="17d79-176">dotnet new</span><span class="sxs-lookup"><span data-stu-id="17d79-176">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="17d79-177">Inicializuje C# nebo F# projektu pro danou šablonu.</span><span class="sxs-lookup"><span data-stu-id="17d79-177">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="17d79-178">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="17d79-178">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="17d79-179">Vytvoří balíček NuGet kódu.</span><span class="sxs-lookup"><span data-stu-id="17d79-179">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="17d79-180">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="17d79-180">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="17d79-181">Publikuje závisí na architektuře nebo samostatné aplikaci .NET.</span><span class="sxs-lookup"><span data-stu-id="17d79-181">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="17d79-182">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="17d79-182">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="17d79-183">Obnoví závislosti pro danou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="17d79-183">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="17d79-184">dotnet run</span><span class="sxs-lookup"><span data-stu-id="17d79-184">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="17d79-185">Spuštění aplikace ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="17d79-185">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="17d79-186">dotnet run</span><span class="sxs-lookup"><span data-stu-id="17d79-186">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="17d79-187">Možnosti pro přidání, odebrání a výpis projektů v souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="17d79-187">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="17d79-188">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="17d79-188">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="17d79-189">Sestavení se ukládá do úložiště balíčků modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="17d79-189">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="17d79-190">dotnet test</span><span class="sxs-lookup"><span data-stu-id="17d79-190">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="17d79-191">Spustí testy pomocí nástroje test runner.</span><span class="sxs-lookup"><span data-stu-id="17d79-191">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="17d79-192">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="17d79-192">.NET Core 2.0</span></span>](#tab/netcore20)

| <span data-ttu-id="17d79-193">Příkaz</span><span class="sxs-lookup"><span data-stu-id="17d79-193">Command</span></span>                             | <span data-ttu-id="17d79-194">Funkce</span><span class="sxs-lookup"><span data-stu-id="17d79-194">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="17d79-195">dotnet build</span><span class="sxs-lookup"><span data-stu-id="17d79-195">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="17d79-196">Sestavení aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="17d79-196">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="17d79-197">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="17d79-197">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="17d79-198">Čištění výstupy sestavení.</span><span class="sxs-lookup"><span data-stu-id="17d79-198">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="17d79-199">dotnet help</span><span class="sxs-lookup"><span data-stu-id="17d79-199">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="17d79-200">Zobrazí podrobnější online dokumentaci pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="17d79-200">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="17d79-201">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="17d79-201">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="17d79-202">Migruje platný projekt ve verzi Preview 2 na projekt .NET Core SDK 1.0.</span><span class="sxs-lookup"><span data-stu-id="17d79-202">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="17d79-203">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="17d79-203">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="17d79-204">Poskytuje přístup k příkazovému řádku nástroje MSBuild.</span><span class="sxs-lookup"><span data-stu-id="17d79-204">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="17d79-205">dotnet new</span><span class="sxs-lookup"><span data-stu-id="17d79-205">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="17d79-206">Inicializuje C# nebo F# projektu pro danou šablonu.</span><span class="sxs-lookup"><span data-stu-id="17d79-206">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="17d79-207">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="17d79-207">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="17d79-208">Vytvoří balíček NuGet kódu.</span><span class="sxs-lookup"><span data-stu-id="17d79-208">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="17d79-209">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="17d79-209">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="17d79-210">Publikuje závisí na architektuře nebo samostatné aplikaci .NET.</span><span class="sxs-lookup"><span data-stu-id="17d79-210">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="17d79-211">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="17d79-211">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="17d79-212">Obnoví závislosti pro danou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="17d79-212">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="17d79-213">dotnet run</span><span class="sxs-lookup"><span data-stu-id="17d79-213">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="17d79-214">Spuštění aplikace ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="17d79-214">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="17d79-215">dotnet run</span><span class="sxs-lookup"><span data-stu-id="17d79-215">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="17d79-216">Možnosti pro přidání, odebrání a výpis projektů v souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="17d79-216">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="17d79-217">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="17d79-217">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="17d79-218">Sestavení se ukládá do úložiště balíčků modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="17d79-218">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="17d79-219">dotnet test</span><span class="sxs-lookup"><span data-stu-id="17d79-219">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="17d79-220">Spustí testy pomocí nástroje test runner.</span><span class="sxs-lookup"><span data-stu-id="17d79-220">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="17d79-221">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="17d79-221">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="17d79-222">Příkaz</span><span class="sxs-lookup"><span data-stu-id="17d79-222">Command</span></span>                             | <span data-ttu-id="17d79-223">Funkce</span><span class="sxs-lookup"><span data-stu-id="17d79-223">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="17d79-224">dotnet build</span><span class="sxs-lookup"><span data-stu-id="17d79-224">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="17d79-225">Sestavení aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="17d79-225">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="17d79-226">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="17d79-226">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="17d79-227">Čištění výstupy sestavení.</span><span class="sxs-lookup"><span data-stu-id="17d79-227">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="17d79-228">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="17d79-228">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="17d79-229">Migruje platný projekt ve verzi Preview 2 na projekt .NET Core SDK 1.0.</span><span class="sxs-lookup"><span data-stu-id="17d79-229">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="17d79-230">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="17d79-230">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="17d79-231">Poskytuje přístup k příkazovému řádku nástroje MSBuild.</span><span class="sxs-lookup"><span data-stu-id="17d79-231">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="17d79-232">dotnet new</span><span class="sxs-lookup"><span data-stu-id="17d79-232">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="17d79-233">Inicializuje C# nebo F# projektu pro danou šablonu.</span><span class="sxs-lookup"><span data-stu-id="17d79-233">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="17d79-234">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="17d79-234">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="17d79-235">Vytvoří balíček NuGet kódu.</span><span class="sxs-lookup"><span data-stu-id="17d79-235">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="17d79-236">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="17d79-236">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="17d79-237">Publikuje závisí na architektuře nebo samostatné aplikaci .NET.</span><span class="sxs-lookup"><span data-stu-id="17d79-237">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="17d79-238">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="17d79-238">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="17d79-239">Obnoví závislosti pro danou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="17d79-239">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="17d79-240">dotnet run</span><span class="sxs-lookup"><span data-stu-id="17d79-240">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="17d79-241">Spuštění aplikace ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="17d79-241">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="17d79-242">dotnet run</span><span class="sxs-lookup"><span data-stu-id="17d79-242">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="17d79-243">Možnosti pro přidání, odebrání a výpis projektů v souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="17d79-243">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="17d79-244">dotnet test</span><span class="sxs-lookup"><span data-stu-id="17d79-244">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="17d79-245">Spustí testy pomocí nástroje test runner.</span><span class="sxs-lookup"><span data-stu-id="17d79-245">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="17d79-246">Odkazy na projekt</span><span class="sxs-lookup"><span data-stu-id="17d79-246">Project references</span></span>

<span data-ttu-id="17d79-247">Příkaz</span><span class="sxs-lookup"><span data-stu-id="17d79-247">Command</span></span> | <span data-ttu-id="17d79-248">Funkce</span><span class="sxs-lookup"><span data-stu-id="17d79-248">Function</span></span>
--- | ---
[<span data-ttu-id="17d79-249">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="17d79-249">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="17d79-250">Přidá odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="17d79-250">Adds a project reference.</span></span>
[<span data-ttu-id="17d79-251">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="17d79-251">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="17d79-252">Obsahuje odkazy na projekt.</span><span class="sxs-lookup"><span data-stu-id="17d79-252">Lists project references.</span></span>
[<span data-ttu-id="17d79-253">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="17d79-253">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="17d79-254">Odebere odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="17d79-254">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="17d79-255">Balíčky NuGet</span><span class="sxs-lookup"><span data-stu-id="17d79-255">NuGet packages</span></span>

<span data-ttu-id="17d79-256">Příkaz</span><span class="sxs-lookup"><span data-stu-id="17d79-256">Command</span></span> | <span data-ttu-id="17d79-257">Funkce</span><span class="sxs-lookup"><span data-stu-id="17d79-257">Function</span></span>
--- | ---
[<span data-ttu-id="17d79-258">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="17d79-258">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="17d79-259">Přidá balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="17d79-259">Adds a NuGet package.</span></span>
[<span data-ttu-id="17d79-260">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="17d79-260">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="17d79-261">Odebere balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="17d79-261">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="17d79-262">Příkazy pro balíčky NuGet</span><span class="sxs-lookup"><span data-stu-id="17d79-262">NuGet commands</span></span>

<span data-ttu-id="17d79-263">Příkaz</span><span class="sxs-lookup"><span data-stu-id="17d79-263">Command</span></span> | <span data-ttu-id="17d79-264">Funkce</span><span class="sxs-lookup"><span data-stu-id="17d79-264">Function</span></span>
--- | ---
[<span data-ttu-id="17d79-265">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="17d79-265">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="17d79-266">Odstraní nebo unlists balíčku ze serveru.</span><span class="sxs-lookup"><span data-stu-id="17d79-266">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="17d79-267">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="17d79-267">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="17d79-268">Vymaže nebo vypíše místní prostředky NuGet, třeba mezipaměť požadavku http, dočasná mezipaměť nebo celý počítač globální složku balíčků.</span><span class="sxs-lookup"><span data-stu-id="17d79-268">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="17d79-269">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="17d79-269">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="17d79-270">Odešle balíček na server a publikuje ji.</span><span class="sxs-lookup"><span data-stu-id="17d79-270">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tools-commands"></a><span data-ttu-id="17d79-271">Globální příkazy nástroje</span><span class="sxs-lookup"><span data-stu-id="17d79-271">Global Tools commands</span></span>

<span data-ttu-id="17d79-272">[Globální nástroje .NET core](global-tools.md) jsou k dispozici od verze rozhraní .NET Core SDK 2.1.300:</span><span class="sxs-lookup"><span data-stu-id="17d79-272">[.NET Core Global Tools](global-tools.md) are available starting with .NET Core SDK 2.1.300:</span></span>

<span data-ttu-id="17d79-273">Příkaz</span><span class="sxs-lookup"><span data-stu-id="17d79-273">Command</span></span> | <span data-ttu-id="17d79-274">Funkce</span><span class="sxs-lookup"><span data-stu-id="17d79-274">Function</span></span>
--- | ---
[<span data-ttu-id="17d79-275">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="17d79-275">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="17d79-276">Globální nástroj nainstaluje na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="17d79-276">Installs a Global Tool on your machine.</span></span>
[<span data-ttu-id="17d79-277">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="17d79-277">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="17d79-278">Vypíše všechny globální nástroje aktuálně nainstalované ve výchozím adresáři na svém počítači nebo v zadané cestě.</span><span class="sxs-lookup"><span data-stu-id="17d79-278">Lists all Global Tools currently installed in the default directory on your machine or in the specified path.</span></span>
[<span data-ttu-id="17d79-279">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="17d79-279">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="17d79-280">Odinstaluje nástroj globální z vašeho počítače.</span><span class="sxs-lookup"><span data-stu-id="17d79-280">Uninstalls a Global Tool from your machine.</span></span>
[<span data-ttu-id="17d79-281">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="17d79-281">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="17d79-282">Aktualizuje nástroj globální na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="17d79-282">Updates a Global Tool on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="17d79-283">Další nástroje</span><span class="sxs-lookup"><span data-stu-id="17d79-283">Additional tools</span></span>

<span data-ttu-id="17d79-284">Počínaje řadou nástrojů, které byly k dispozici pouze v jednotlivých projektů pomocí sady .NET Core SDK 2.1.300, `DotnetCliToolReference` jsou teď k dispozici jako součást sady .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="17d79-284">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="17d79-285">Tyto nástroje jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="17d79-285">These tools are listed in the following table:</span></span>

| <span data-ttu-id="17d79-286">Nástroj</span><span class="sxs-lookup"><span data-stu-id="17d79-286">Tool</span></span>                                              | <span data-ttu-id="17d79-287">Funkce</span><span class="sxs-lookup"><span data-stu-id="17d79-287">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="17d79-288">dev-certs</span><span class="sxs-lookup"><span data-stu-id="17d79-288">dev-certs</span></span>                                         | <span data-ttu-id="17d79-289">Vytváří a spravuje certifikáty vývoje.</span><span class="sxs-lookup"><span data-stu-id="17d79-289">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="17d79-290">EF</span><span class="sxs-lookup"><span data-stu-id="17d79-290">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="17d79-291">Nástroje příkazového řádku Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="17d79-291">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="17d79-292">SQL-cache</span><span class="sxs-lookup"><span data-stu-id="17d79-292">sql-cache</span></span>                                         | <span data-ttu-id="17d79-293">Nástroje příkazového řádku systému SQL Server mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="17d79-293">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="17d79-294">tajné klíče uživatelů</span><span class="sxs-lookup"><span data-stu-id="17d79-294">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="17d79-295">Slouží ke správě tajných kódů uživatelů vývoje.</span><span class="sxs-lookup"><span data-stu-id="17d79-295">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="17d79-296">Sledování</span><span class="sxs-lookup"><span data-stu-id="17d79-296">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="17d79-297">Spustí se soubor sledování, které se spustí příkaz, když se změní soubory.</span><span class="sxs-lookup"><span data-stu-id="17d79-297">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="17d79-298">Další informace o jednotlivých nástrojích, zadejte `dotnet <tool-name> --help`.</span><span class="sxs-lookup"><span data-stu-id="17d79-298">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="17d79-299">Příklady</span><span class="sxs-lookup"><span data-stu-id="17d79-299">Examples</span></span>

<span data-ttu-id="17d79-300">Vytvoří novou konzolovou aplikaci .NET Core:</span><span class="sxs-lookup"><span data-stu-id="17d79-300">Creates a new .NET Core console application:</span></span>

`dotnet new console`

<span data-ttu-id="17d79-301">Obnovte závislosti pro dané aplikace:</span><span class="sxs-lookup"><span data-stu-id="17d79-301">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="17d79-302">Sestavení projektu a jeho závislosti v daném adresáři:</span><span class="sxs-lookup"><span data-stu-id="17d79-302">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="17d79-303">Spustit aplikaci knihovny DLL, jako například `myapp.dll`:</span><span class="sxs-lookup"><span data-stu-id="17d79-303">Run an application DLL, such as `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="17d79-304">Proměnné prostředí</span><span class="sxs-lookup"><span data-stu-id="17d79-304">Environment variables</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="17d79-305">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="17d79-305">.NET Core 2.1</span></span>](#tab/netcore21)

`DOTNET_PACKAGES`

<span data-ttu-id="17d79-306">Primární balíček mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="17d79-306">The primary package cache.</span></span> <span data-ttu-id="17d79-307">Pokud není nastavená, použije se výchozí `$HOME/.nuget/packages` v systému Unix nebo `%HOME%\NuGet\Packages` na Windows.</span><span class="sxs-lookup"><span data-stu-id="17d79-307">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="17d79-308">Určuje umístění index údržby pro použití sdílené hostitele při načítání modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="17d79-308">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="17d79-309">Určuje, zda data o využití nástroje .NET Core je shromažďovat a odesílat do Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="17d79-309">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="17d79-310">Nastavte na `true` odhlásit funkce telemetrie (hodnoty `true`, `1`, nebo `yes` přijetí).</span><span class="sxs-lookup"><span data-stu-id="17d79-310">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="17d79-311">V opačném případě nastavte na `false` do funkce telemetrie (hodnoty `false`, `0`, nebo `no` přijetí).</span><span class="sxs-lookup"><span data-stu-id="17d79-311">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="17d79-312">Pokud není nastavený, výchozí hodnota je `false` a funkce telemetrie je aktivní.</span><span class="sxs-lookup"><span data-stu-id="17d79-312">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="17d79-313">Určuje, zda modul runtime .NET Core, sdílené architektuře nebo sady SDK jsou vyřešené z globálního místa.</span><span class="sxs-lookup"><span data-stu-id="17d79-313">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="17d79-314">Pokud není nastavená, použije se výchozí `true`.</span><span class="sxs-lookup"><span data-stu-id="17d79-314">If not set, it defaults to `true`.</span></span> <span data-ttu-id="17d79-315">Nastavte na `false` se vyřešit z globálního místa a mají izolované instalace .NET Core (hodnoty `0` nebo `false` jsou přijímány).</span><span class="sxs-lookup"><span data-stu-id="17d79-315">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="17d79-316">Další informace o víceúrovňových vyhledávání najdete v tématu [víceúrovňovými SharedFX vyhledávání](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="17d79-316">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

<span data-ttu-id="17d79-317">Zakáže podverze Posunutí vpřed, pokud nastavit `0`.</span><span class="sxs-lookup"><span data-stu-id="17d79-317">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="17d79-318">Další informace najdete v tématu [posunout vpřed](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="17d79-318">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="17d79-319">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="17d79-319">.NET Core 2.0</span></span>](#tab/netcore20)

`DOTNET_PACKAGES`

<span data-ttu-id="17d79-320">Primární balíček mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="17d79-320">The primary package cache.</span></span> <span data-ttu-id="17d79-321">Pokud není nastavená, použije se výchozí `$HOME/.nuget/packages` v systému Unix nebo `%HOME%\NuGet\Packages` na Windows.</span><span class="sxs-lookup"><span data-stu-id="17d79-321">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="17d79-322">Určuje umístění index údržby pro použití sdílené hostitele při načítání modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="17d79-322">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="17d79-323">Určuje, zda data o využití nástroje .NET Core je shromažďovat a odesílat do Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="17d79-323">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="17d79-324">Nastavte na `true` odhlásit funkce telemetrie (hodnoty `true`, `1`, nebo `yes` přijetí).</span><span class="sxs-lookup"><span data-stu-id="17d79-324">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="17d79-325">V opačném případě nastavte na `false` do funkce telemetrie (hodnoty `false`, `0`, nebo `no` přijetí).</span><span class="sxs-lookup"><span data-stu-id="17d79-325">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="17d79-326">Pokud není nastavený, výchozí hodnota je `false` a funkce telemetrie je aktivní.</span><span class="sxs-lookup"><span data-stu-id="17d79-326">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="17d79-327">Určuje, zda modul runtime .NET Core, sdílené architektuře nebo sady SDK jsou vyřešené z globálního místa.</span><span class="sxs-lookup"><span data-stu-id="17d79-327">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="17d79-328">Pokud není nastavená, použije se výchozí `true`.</span><span class="sxs-lookup"><span data-stu-id="17d79-328">If not set, it defaults to `true`.</span></span> <span data-ttu-id="17d79-329">Nastavte na `false` se vyřešit z globálního místa a mají izolované instalace .NET Core (hodnoty `0` nebo `false` jsou přijímány).</span><span class="sxs-lookup"><span data-stu-id="17d79-329">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="17d79-330">Další informace o víceúrovňových vyhledávání najdete v tématu [víceúrovňovými SharedFX vyhledávání](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="17d79-330">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="17d79-331">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="17d79-331">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="17d79-332">Primární balíček mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="17d79-332">The primary package cache.</span></span> <span data-ttu-id="17d79-333">Pokud není nastavená, použije se výchozí `$HOME/.nuget/packages` v systému Unix nebo `%HOME%\NuGet\Packages` na Windows.</span><span class="sxs-lookup"><span data-stu-id="17d79-333">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="17d79-334">Určuje umístění index údržby pro použití sdílené hostitele při načítání modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="17d79-334">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="17d79-335">Určuje, zda data o využití nástroje .NET Core je shromažďovat a odesílat do Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="17d79-335">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="17d79-336">Nastavte na `true` odhlásit funkce telemetrie (hodnoty `true`, `1`, nebo `yes` přijetí).</span><span class="sxs-lookup"><span data-stu-id="17d79-336">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="17d79-337">V opačném případě nastavte na `false` do funkce telemetrie (hodnoty `false`, `0`, nebo `no` přijetí).</span><span class="sxs-lookup"><span data-stu-id="17d79-337">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="17d79-338">Pokud není nastavený, výchozí hodnota je `false` a funkce telemetrie je aktivní.</span><span class="sxs-lookup"><span data-stu-id="17d79-338">If not set, the default is `false` and the telemetry feature is active.</span></span>

---
