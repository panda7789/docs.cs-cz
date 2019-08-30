---
title: dotnet – příkaz
description: Přečtěte si o příkazu dotnet (obecný ovladač pro .NET Core CLI nástroje) a jeho využití.
ms.date: 06/04/2018
ms.openlocfilehash: 7e1915610732151487353f2d14586597f801ddfb
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2019
ms.locfileid: "70167908"
---
# <a name="dotnet-command"></a><span data-ttu-id="38590-103">dotnet – příkaz</span><span class="sxs-lookup"><span data-stu-id="38590-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="38590-104">Name</span><span class="sxs-lookup"><span data-stu-id="38590-104">Name</span></span>

<span data-ttu-id="38590-105">`dotnet`– Nástroj pro správu zdrojového kódu a binárních souborů .NET.</span><span class="sxs-lookup"><span data-stu-id="38590-105">`dotnet` - A tool for managing .NET source code and binaries.</span></span>

## <a name="synopsis"></a><span data-ttu-id="38590-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="38590-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="38590-107">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="38590-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="38590-108">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="38590-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="38590-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="38590-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [-v|--verbosity] [--version]
```

---

## <a name="description"></a><span data-ttu-id="38590-110">Popis</span><span class="sxs-lookup"><span data-stu-id="38590-110">Description</span></span>

<span data-ttu-id="38590-111">`dotnet`je nástroj pro správu zdrojového kódu a binárních souborů .NET.</span><span class="sxs-lookup"><span data-stu-id="38590-111">`dotnet` is a tool for managing .NET source code and binaries.</span></span> <span data-ttu-id="38590-112">Zpřístupňuje příkazy, které provádějí konkrétní úkoly, [`dotnet build`](dotnet-build.md) jako například a. [`dotnet run`](dotnet-run.md)</span><span class="sxs-lookup"><span data-stu-id="38590-112">It exposes commands that perform specific tasks, such as [`dotnet build`](dotnet-build.md) and [`dotnet run`](dotnet-run.md).</span></span> <span data-ttu-id="38590-113">Každý příkaz definuje své vlastní argumenty.</span><span class="sxs-lookup"><span data-stu-id="38590-113">Each command defines its own arguments.</span></span> <span data-ttu-id="38590-114">Typ `--help` za každým příkazem pro přístup k krátké dokumentaci k nápovědě.</span><span class="sxs-lookup"><span data-stu-id="38590-114">Type `--help` after each command to access brief help documentation.</span></span>

<span data-ttu-id="38590-115">`dotnet`lze použít ke spouštění aplikací zadáním knihovny DLL aplikace, například `dotnet myapp.dll`.</span><span class="sxs-lookup"><span data-stu-id="38590-115">`dotnet` can be used to run applications, by specifying an application DLL, such as `dotnet myapp.dll`.</span></span> <span data-ttu-id="38590-116">Další informace o možnostech nasazení najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md) .</span><span class="sxs-lookup"><span data-stu-id="38590-116">See [.NET Core application deployment](../deploying/index.md) for to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="38590-117">Možnosti</span><span class="sxs-lookup"><span data-stu-id="38590-117">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="38590-118">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="38590-118">.NET Core 2.1</span></span>](#tab/netcore21)

`--additional-deps <PATH>`

<span data-ttu-id="38590-119">Cesta k dalšímu souboru *. DEPS. JSON* .</span><span class="sxs-lookup"><span data-stu-id="38590-119">Path to additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="38590-120">Cesta obsahující zásady a sestavení pro zjišťování k testování</span><span class="sxs-lookup"><span data-stu-id="38590-120">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="38590-121">Povolí výstup diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="38590-121">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="38590-122">Verze modulu runtime .NET Core, která se má použít ke spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="38590-122">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="38590-123">Vytiskne dokumentaci pro daný příkaz, například `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="38590-123">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="38590-124">`dotnet --help`vytiskne seznam dostupných příkazů.</span><span class="sxs-lookup"><span data-stu-id="38590-124">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="38590-125">Vytiskne podrobné informace o instalaci .NET Core a počítačovém prostředí, jako je aktuální operační systém, a potvrzení SHA verze .NET Core.</span><span class="sxs-lookup"><span data-stu-id="38590-125">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--list-runtimes`

<span data-ttu-id="38590-126">Zobrazí nainstalované moduly runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="38590-126">Displays the installed .NET Core runtimes.</span></span>

`--list-sdks`

<span data-ttu-id="38590-127">Zobrazí nainstalované sady SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="38590-127">Displays the installed .NET Core SDKs.</span></span>

`--roll-forward-on-no-candidate-fx <N>`

<span data-ttu-id="38590-128">Definuje chování v případě, že požadovaná sdílená architektura není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="38590-128">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="38590-129">`N` může být:</span><span class="sxs-lookup"><span data-stu-id="38590-129">`N` can be:</span></span>
* <span data-ttu-id="38590-130">`0`– Zakažte u sebe i menší verzi.</span><span class="sxs-lookup"><span data-stu-id="38590-130">`0` - Disable even minor version roll forward.</span></span>
* <span data-ttu-id="38590-131">`1`– Navýšení se dopředá na podverzi, ale ne na hlavní verzi.</span><span class="sxs-lookup"><span data-stu-id="38590-131">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="38590-132">Toto je výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="38590-132">This is the default behavior.</span></span>
* <span data-ttu-id="38590-133">`2`– Posunutí posunu k dílčím a hlavním verzím</span><span class="sxs-lookup"><span data-stu-id="38590-133">`2` - Roll forward on minor and major versions.</span></span>

 <span data-ttu-id="38590-134">Další informace najdete v tématu o tom, jak [Posunout](../whats-new/dotnet-core-2-1.md#roll-forward)nahoru.</span><span class="sxs-lookup"><span data-stu-id="38590-134">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="38590-135">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="38590-135">Sets the verbosity level of the command.</span></span> <span data-ttu-id="38590-136">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]` `d[etailed]`, a .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="38590-136">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="38590-137">Nepodporováno v každém příkazu; Pokud chcete zjistit, zda je tato možnost k dispozici, zobrazte konkrétní příkazová stránka.</span><span class="sxs-lookup"><span data-stu-id="38590-137">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="38590-138">Vytiskne verzi .NET Core SDK, která se používá.</span><span class="sxs-lookup"><span data-stu-id="38590-138">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="38590-139">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="38590-139">.NET Core 2.0</span></span>](#tab/netcore20)

`--additional-deps <PATH>`

<span data-ttu-id="38590-140">Cesta k dalšímu souboru *. DEPS. JSON* .</span><span class="sxs-lookup"><span data-stu-id="38590-140">Path to additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="38590-141">Cesta obsahující zásady a sestavení pro zjišťování k testování</span><span class="sxs-lookup"><span data-stu-id="38590-141">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="38590-142">Povolí výstup diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="38590-142">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="38590-143">Verze modulu runtime .NET Core, která se má použít ke spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="38590-143">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="38590-144">Vytiskne dokumentaci pro daný příkaz, například `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="38590-144">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="38590-145">`dotnet --help`vytiskne seznam dostupných příkazů.</span><span class="sxs-lookup"><span data-stu-id="38590-145">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="38590-146">Vytiskne podrobné informace o instalaci .NET Core a počítačovém prostředí, jako je aktuální operační systém, a potvrzení SHA verze .NET Core.</span><span class="sxs-lookup"><span data-stu-id="38590-146">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="38590-147">Zakáže posunutí dílčí verze, pokud je nastaveno `0`na.</span><span class="sxs-lookup"><span data-stu-id="38590-147">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="38590-148">Další informace najdete v tématu o tom, jak [Posunout](../whats-new/dotnet-core-2-1.md#roll-forward)nahoru.</span><span class="sxs-lookup"><span data-stu-id="38590-148">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="38590-149">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="38590-149">Sets the verbosity level of the command.</span></span> <span data-ttu-id="38590-150">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]` `d[etailed]`, a .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="38590-150">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="38590-151">Nepodporováno v každém příkazu; Pokud chcete zjistit, zda je tato možnost k dispozici, zobrazte konkrétní příkazová stránka.</span><span class="sxs-lookup"><span data-stu-id="38590-151">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="38590-152">Vytiskne verzi .NET Core SDK, která se používá.</span><span class="sxs-lookup"><span data-stu-id="38590-152">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="38590-153">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="38590-153">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="38590-154">Cesta obsahující zásady a sestavení pro zjišťování k testování</span><span class="sxs-lookup"><span data-stu-id="38590-154">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="38590-155">Povolí výstup diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="38590-155">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="38590-156">Verze modulu runtime .NET Core, která se má použít ke spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="38590-156">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="38590-157">Vytiskne dokumentaci pro daný příkaz, například `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="38590-157">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="38590-158">`dotnet --help`vytiskne seznam dostupných příkazů.</span><span class="sxs-lookup"><span data-stu-id="38590-158">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="38590-159">Vytiskne podrobné informace o instalaci .NET Core a počítačovém prostředí, jako je aktuální operační systém, a potvrzení SHA verze .NET Core.</span><span class="sxs-lookup"><span data-stu-id="38590-159">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="38590-160">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="38590-160">Sets the verbosity level of the command.</span></span> <span data-ttu-id="38590-161">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]` `d[etailed]`, a .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="38590-161">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="38590-162">Nepodporováno v každém příkazu; Pokud chcete zjistit, zda je tato možnost k dispozici, zobrazte konkrétní příkazová stránka.</span><span class="sxs-lookup"><span data-stu-id="38590-162">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="38590-163">Vytiskne verzi .NET Core SDK, která se používá.</span><span class="sxs-lookup"><span data-stu-id="38590-163">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="38590-164">Příkazy dotnet</span><span class="sxs-lookup"><span data-stu-id="38590-164">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="38590-165">Obecné</span><span class="sxs-lookup"><span data-stu-id="38590-165">General</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="38590-166">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="38590-166">.NET Core 2.1</span></span>](#tab/netcore21)

| <span data-ttu-id="38590-167">Příkaz</span><span class="sxs-lookup"><span data-stu-id="38590-167">Command</span></span>                                       | <span data-ttu-id="38590-168">Funkce</span><span class="sxs-lookup"><span data-stu-id="38590-168">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="38590-169">dotnet build</span><span class="sxs-lookup"><span data-stu-id="38590-169">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="38590-170">Vytvoří aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="38590-170">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="38590-171">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="38590-171">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="38590-172">Komunikuje se servery spuštěnými sestavením.</span><span class="sxs-lookup"><span data-stu-id="38590-172">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="38590-173">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="38590-173">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="38590-174">Vyčistit výstupy sestavení.</span><span class="sxs-lookup"><span data-stu-id="38590-174">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="38590-175">dotnet help</span><span class="sxs-lookup"><span data-stu-id="38590-175">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="38590-176">Zobrazí podrobnější dokumentaci pro příkaz online.</span><span class="sxs-lookup"><span data-stu-id="38590-176">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="38590-177">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="38590-177">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="38590-178">Migruje platný projekt verze Preview 2 na projekt .NET Core SDK 1,0.</span><span class="sxs-lookup"><span data-stu-id="38590-178">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="38590-179">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="38590-179">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="38590-180">Poskytuje přístup k příkazovému řádku MSBuild.</span><span class="sxs-lookup"><span data-stu-id="38590-180">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="38590-181">dotnet new</span><span class="sxs-lookup"><span data-stu-id="38590-181">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="38590-182">Inicializuje projekt C# nebo F# pro danou šablonu.</span><span class="sxs-lookup"><span data-stu-id="38590-182">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="38590-183">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="38590-183">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="38590-184">Vytvoří balíček NuGet vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="38590-184">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="38590-185">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="38590-185">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="38590-186">Publikuje aplikaci závislou na rozhraní .NET Framework nebo samostatnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="38590-186">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="38590-187">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="38590-187">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="38590-188">Obnoví závislosti pro danou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="38590-188">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="38590-189">dotnet run</span><span class="sxs-lookup"><span data-stu-id="38590-189">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="38590-190">Spustí aplikaci ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="38590-190">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="38590-191">dotnet run</span><span class="sxs-lookup"><span data-stu-id="38590-191">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="38590-192">Možnosti pro přidání, odebrání a výpis projektů v souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="38590-192">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="38590-193">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="38590-193">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="38590-194">Ukládá sestavení do úložiště balíčků modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="38590-194">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="38590-195">dotnet test</span><span class="sxs-lookup"><span data-stu-id="38590-195">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="38590-196">Spustí testy pomocí nástroje Test Runner.</span><span class="sxs-lookup"><span data-stu-id="38590-196">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="38590-197">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="38590-197">.NET Core 2.0</span></span>](#tab/netcore20)

| <span data-ttu-id="38590-198">Příkaz</span><span class="sxs-lookup"><span data-stu-id="38590-198">Command</span></span>                             | <span data-ttu-id="38590-199">Funkce</span><span class="sxs-lookup"><span data-stu-id="38590-199">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="38590-200">dotnet build</span><span class="sxs-lookup"><span data-stu-id="38590-200">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="38590-201">Vytvoří aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="38590-201">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="38590-202">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="38590-202">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="38590-203">Vyčistit výstupy sestavení.</span><span class="sxs-lookup"><span data-stu-id="38590-203">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="38590-204">dotnet help</span><span class="sxs-lookup"><span data-stu-id="38590-204">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="38590-205">Zobrazí podrobnější dokumentaci pro příkaz online.</span><span class="sxs-lookup"><span data-stu-id="38590-205">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="38590-206">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="38590-206">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="38590-207">Migruje platný projekt verze Preview 2 na projekt .NET Core SDK 1,0.</span><span class="sxs-lookup"><span data-stu-id="38590-207">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="38590-208">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="38590-208">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="38590-209">Poskytuje přístup k příkazovému řádku MSBuild.</span><span class="sxs-lookup"><span data-stu-id="38590-209">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="38590-210">dotnet new</span><span class="sxs-lookup"><span data-stu-id="38590-210">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="38590-211">Inicializuje projekt C# nebo F# pro danou šablonu.</span><span class="sxs-lookup"><span data-stu-id="38590-211">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="38590-212">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="38590-212">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="38590-213">Vytvoří balíček NuGet vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="38590-213">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="38590-214">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="38590-214">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="38590-215">Publikuje aplikaci závislou na rozhraní .NET Framework nebo samostatnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="38590-215">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="38590-216">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="38590-216">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="38590-217">Obnoví závislosti pro danou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="38590-217">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="38590-218">dotnet run</span><span class="sxs-lookup"><span data-stu-id="38590-218">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="38590-219">Spustí aplikaci ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="38590-219">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="38590-220">dotnet run</span><span class="sxs-lookup"><span data-stu-id="38590-220">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="38590-221">Možnosti pro přidání, odebrání a výpis projektů v souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="38590-221">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="38590-222">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="38590-222">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="38590-223">Ukládá sestavení do úložiště balíčků modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="38590-223">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="38590-224">dotnet test</span><span class="sxs-lookup"><span data-stu-id="38590-224">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="38590-225">Spustí testy pomocí nástroje Test Runner.</span><span class="sxs-lookup"><span data-stu-id="38590-225">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="38590-226">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="38590-226">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="38590-227">Příkaz</span><span class="sxs-lookup"><span data-stu-id="38590-227">Command</span></span>                             | <span data-ttu-id="38590-228">Funkce</span><span class="sxs-lookup"><span data-stu-id="38590-228">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="38590-229">dotnet build</span><span class="sxs-lookup"><span data-stu-id="38590-229">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="38590-230">Vytvoří aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="38590-230">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="38590-231">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="38590-231">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="38590-232">Vyčistit výstupy sestavení.</span><span class="sxs-lookup"><span data-stu-id="38590-232">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="38590-233">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="38590-233">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="38590-234">Migruje platný projekt verze Preview 2 na projekt .NET Core SDK 1,0.</span><span class="sxs-lookup"><span data-stu-id="38590-234">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="38590-235">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="38590-235">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="38590-236">Poskytuje přístup k příkazovému řádku MSBuild.</span><span class="sxs-lookup"><span data-stu-id="38590-236">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="38590-237">dotnet new</span><span class="sxs-lookup"><span data-stu-id="38590-237">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="38590-238">Inicializuje projekt C# nebo F# pro danou šablonu.</span><span class="sxs-lookup"><span data-stu-id="38590-238">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="38590-239">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="38590-239">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="38590-240">Vytvoří balíček NuGet vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="38590-240">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="38590-241">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="38590-241">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="38590-242">Publikuje aplikaci závislou na rozhraní .NET Framework nebo samostatnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="38590-242">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="38590-243">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="38590-243">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="38590-244">Obnoví závislosti pro danou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="38590-244">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="38590-245">dotnet run</span><span class="sxs-lookup"><span data-stu-id="38590-245">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="38590-246">Spustí aplikaci ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="38590-246">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="38590-247">dotnet run</span><span class="sxs-lookup"><span data-stu-id="38590-247">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="38590-248">Možnosti pro přidání, odebrání a výpis projektů v souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="38590-248">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="38590-249">dotnet test</span><span class="sxs-lookup"><span data-stu-id="38590-249">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="38590-250">Spustí testy pomocí nástroje Test Runner.</span><span class="sxs-lookup"><span data-stu-id="38590-250">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="38590-251">Odkazy na projekty</span><span class="sxs-lookup"><span data-stu-id="38590-251">Project references</span></span>

<span data-ttu-id="38590-252">Příkaz</span><span class="sxs-lookup"><span data-stu-id="38590-252">Command</span></span> | <span data-ttu-id="38590-253">Funkce</span><span class="sxs-lookup"><span data-stu-id="38590-253">Function</span></span>
--- | ---
[<span data-ttu-id="38590-254">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="38590-254">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="38590-255">Přidá odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="38590-255">Adds a project reference.</span></span>
[<span data-ttu-id="38590-256">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="38590-256">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="38590-257">Vypíše odkazy na projekt.</span><span class="sxs-lookup"><span data-stu-id="38590-257">Lists project references.</span></span>
[<span data-ttu-id="38590-258">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="38590-258">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="38590-259">Odebere odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="38590-259">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="38590-260">Balíčky NuGet</span><span class="sxs-lookup"><span data-stu-id="38590-260">NuGet packages</span></span>

<span data-ttu-id="38590-261">Příkaz</span><span class="sxs-lookup"><span data-stu-id="38590-261">Command</span></span> | <span data-ttu-id="38590-262">Funkce</span><span class="sxs-lookup"><span data-stu-id="38590-262">Function</span></span>
--- | ---
[<span data-ttu-id="38590-263">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="38590-263">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="38590-264">Přidá balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="38590-264">Adds a NuGet package.</span></span>
[<span data-ttu-id="38590-265">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="38590-265">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="38590-266">Odebere balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="38590-266">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="38590-267">Příkazy NuGet</span><span class="sxs-lookup"><span data-stu-id="38590-267">NuGet commands</span></span>

<span data-ttu-id="38590-268">Příkaz</span><span class="sxs-lookup"><span data-stu-id="38590-268">Command</span></span> | <span data-ttu-id="38590-269">Funkce</span><span class="sxs-lookup"><span data-stu-id="38590-269">Function</span></span>
--- | ---
[<span data-ttu-id="38590-270">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="38590-270">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="38590-271">Odstraní nebo zruší výpis balíčku ze serveru.</span><span class="sxs-lookup"><span data-stu-id="38590-271">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="38590-272">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="38590-272">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="38590-273">Vymaže nebo vypíše místní prostředky NuGet, jako je mezipaměť požadavků HTTP, dočasná mezipaměť nebo složka globálních balíčků v celém počítači.</span><span class="sxs-lookup"><span data-stu-id="38590-273">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="38590-274">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="38590-274">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="38590-275">Odešle balíček na server a publikuje ho.</span><span class="sxs-lookup"><span data-stu-id="38590-275">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tools-commands"></a><span data-ttu-id="38590-276">Příkazy globálních nástrojů</span><span class="sxs-lookup"><span data-stu-id="38590-276">Global Tools commands</span></span>

<span data-ttu-id="38590-277">K dispozici jsou [globální nástroje .NET Core](global-tools.md) od .NET Core SDK 2.1.300:</span><span class="sxs-lookup"><span data-stu-id="38590-277">[.NET Core Global Tools](global-tools.md) are available starting with .NET Core SDK 2.1.300:</span></span>

<span data-ttu-id="38590-278">Příkaz</span><span class="sxs-lookup"><span data-stu-id="38590-278">Command</span></span> | <span data-ttu-id="38590-279">Funkce</span><span class="sxs-lookup"><span data-stu-id="38590-279">Function</span></span>
--- | ---
[<span data-ttu-id="38590-280">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="38590-280">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="38590-281">Nainstaluje na váš počítač globální nástroj.</span><span class="sxs-lookup"><span data-stu-id="38590-281">Installs a Global Tool on your machine.</span></span>
[<span data-ttu-id="38590-282">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="38590-282">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="38590-283">Zobrazí seznam všech globálních nástrojů, které jsou aktuálně nainstalované ve výchozím adresáři na vašem počítači nebo v zadané cestě.</span><span class="sxs-lookup"><span data-stu-id="38590-283">Lists all Global Tools currently installed in the default directory on your machine or in the specified path.</span></span>
[<span data-ttu-id="38590-284">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="38590-284">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="38590-285">Odinstaluje z počítače globální nástroj.</span><span class="sxs-lookup"><span data-stu-id="38590-285">Uninstalls a Global Tool from your machine.</span></span>
[<span data-ttu-id="38590-286">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="38590-286">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="38590-287">Aktualizuje na svém počítači globální nástroj.</span><span class="sxs-lookup"><span data-stu-id="38590-287">Updates a Global Tool on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="38590-288">Další nástroje</span><span class="sxs-lookup"><span data-stu-id="38590-288">Additional tools</span></span>

<span data-ttu-id="38590-289">Počínaje .NET Core SDK 2.1.300 je teď k dispozici několik nástrojů, které byly k dispozici pouze pro jednotlivé `DotnetCliToolReference` projekty pomocí, jako součást .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="38590-289">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="38590-290">Tyto nástroje jsou uvedené v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="38590-290">These tools are listed in the following table:</span></span>

| <span data-ttu-id="38590-291">Nástroj</span><span class="sxs-lookup"><span data-stu-id="38590-291">Tool</span></span>                                              | <span data-ttu-id="38590-292">Funkce</span><span class="sxs-lookup"><span data-stu-id="38590-292">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="38590-293">vývoj – certifikáty</span><span class="sxs-lookup"><span data-stu-id="38590-293">dev-certs</span></span>                                         | <span data-ttu-id="38590-294">Vytvoří a spravuje vývojové certifikáty.</span><span class="sxs-lookup"><span data-stu-id="38590-294">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="38590-295">EF</span><span class="sxs-lookup"><span data-stu-id="38590-295">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="38590-296">Entity Framework Core nástroje příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="38590-296">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="38590-297">sql-cache</span><span class="sxs-lookup"><span data-stu-id="38590-297">sql-cache</span></span>                                         | <span data-ttu-id="38590-298">Nástroje příkazového řádku pro SQL Server cache</span><span class="sxs-lookup"><span data-stu-id="38590-298">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="38590-299">uživatel – tajné klíče</span><span class="sxs-lookup"><span data-stu-id="38590-299">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="38590-300">Spravuje tajné klíče uživatele.</span><span class="sxs-lookup"><span data-stu-id="38590-300">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="38590-301">sledovací</span><span class="sxs-lookup"><span data-stu-id="38590-301">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="38590-302">Spustí sledovací proces souborů, který spustí příkaz, když se soubory změní.</span><span class="sxs-lookup"><span data-stu-id="38590-302">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="38590-303">Další informace o jednotlivých nástrojích získáte tak `dotnet <tool-name> --help`, že zadáte.</span><span class="sxs-lookup"><span data-stu-id="38590-303">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="38590-304">Příklady</span><span class="sxs-lookup"><span data-stu-id="38590-304">Examples</span></span>

<span data-ttu-id="38590-305">Vytvoří novou konzolovou aplikaci .NET Core:</span><span class="sxs-lookup"><span data-stu-id="38590-305">Creates a new .NET Core console application:</span></span>

`dotnet new console`

<span data-ttu-id="38590-306">Obnovit závislosti pro danou aplikaci:</span><span class="sxs-lookup"><span data-stu-id="38590-306">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="38590-307">Sestavení projektu a jeho závislostí v daném adresáři:</span><span class="sxs-lookup"><span data-stu-id="38590-307">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="38590-308">Spusťte knihovnu DLL aplikace, například `myapp.dll`:</span><span class="sxs-lookup"><span data-stu-id="38590-308">Run an application DLL, such as `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="38590-309">Proměnné prostředí</span><span class="sxs-lookup"><span data-stu-id="38590-309">Environment variables</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="38590-310">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="38590-310">.NET Core 2.1</span></span>](#tab/netcore21)

`DOTNET_PACKAGES`

<span data-ttu-id="38590-311">Složka globálních balíčků.</span><span class="sxs-lookup"><span data-stu-id="38590-311">The global packages folder.</span></span> <span data-ttu-id="38590-312">Pokud není nastavená, použije se `~/.nuget/packages` ve výchozím nastavení `%userprofile%\.nuget\packages` v systému UNIX nebo Windows.</span><span class="sxs-lookup"><span data-stu-id="38590-312">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="38590-313">Určuje umístění indexu údržby používaného sdíleným hostitelem při načítání modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="38590-313">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="38590-314">Určuje, jestli se data o využití nástrojů .NET Core shromažďují a odesílají do Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="38590-314">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="38590-315">Nastavte na `true` výslovný souhlas funkce telemetrie (hodnoty `true`, `1`nebo `yes` přijmout).</span><span class="sxs-lookup"><span data-stu-id="38590-315">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="38590-316">V opačném případě `false` nastavte, aby se přihlásil k funkcím `0`telemetrie ( `no` hodnoty `false`, nebo přijaty).</span><span class="sxs-lookup"><span data-stu-id="38590-316">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="38590-317">Pokud není nastavená, je výchozí `false` nastavení a funkce telemetrie je aktivní.</span><span class="sxs-lookup"><span data-stu-id="38590-317">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="38590-318">Určuje, zda je rozhraní .NET Core Runtime, sdílené rozhraní nebo sada SDK vyřešeno z globálního umístění.</span><span class="sxs-lookup"><span data-stu-id="38590-318">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="38590-319">Pokud není nastaven, použije se výchozí `true`hodnota.</span><span class="sxs-lookup"><span data-stu-id="38590-319">If not set, it defaults to `true`.</span></span> <span data-ttu-id="38590-320">Nastavte na hodnotu neřešitelné z globálního umístění a používejte izolované instalace rozhraní .NET Core ( `0` hodnoty `false` nebo jsou přijatelné). `false`</span><span class="sxs-lookup"><span data-stu-id="38590-320">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="38590-321">Další informace o vyhledávání na více úrovních najdete v tématu [SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="38590-321">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

<span data-ttu-id="38590-322">Zakáže posunutí dílčí verze, pokud je nastaveno `0`na.</span><span class="sxs-lookup"><span data-stu-id="38590-322">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="38590-323">Další informace najdete v tématu o tom, jak [Posunout](../whats-new/dotnet-core-2-1.md#roll-forward)nahoru.</span><span class="sxs-lookup"><span data-stu-id="38590-323">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="38590-324">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="38590-324">.NET Core 2.0</span></span>](#tab/netcore20)

`DOTNET_PACKAGES`

<span data-ttu-id="38590-325">Mezipaměť primárního balíčku.</span><span class="sxs-lookup"><span data-stu-id="38590-325">The primary package cache.</span></span> <span data-ttu-id="38590-326">Pokud není nastavená, použije se `$HOME/.nuget/packages` ve výchozím nastavení `%userprofile%\.nuget\packages` v systému UNIX nebo Windows.</span><span class="sxs-lookup"><span data-stu-id="38590-326">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="38590-327">Určuje umístění indexu údržby používaného sdíleným hostitelem při načítání modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="38590-327">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="38590-328">Určuje, jestli se data o využití nástrojů .NET Core shromažďují a odesílají do Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="38590-328">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="38590-329">Nastavte na `true` výslovný souhlas funkce telemetrie (hodnoty `true`, `1`nebo `yes` přijmout).</span><span class="sxs-lookup"><span data-stu-id="38590-329">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="38590-330">V opačném případě `false` nastavte, aby se přihlásil k funkcím `0`telemetrie ( `no` hodnoty `false`, nebo přijaty).</span><span class="sxs-lookup"><span data-stu-id="38590-330">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="38590-331">Pokud není nastavená, je výchozí `false` nastavení a funkce telemetrie je aktivní.</span><span class="sxs-lookup"><span data-stu-id="38590-331">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="38590-332">Určuje, zda je rozhraní .NET Core Runtime, sdílené rozhraní nebo sada SDK vyřešeno z globálního umístění.</span><span class="sxs-lookup"><span data-stu-id="38590-332">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="38590-333">Pokud není nastaven, použije se výchozí `true`hodnota.</span><span class="sxs-lookup"><span data-stu-id="38590-333">If not set, it defaults to `true`.</span></span> <span data-ttu-id="38590-334">Nastavte na hodnotu neřešitelné z globálního umístění a používejte izolované instalace rozhraní .NET Core ( `0` hodnoty `false` nebo jsou přijatelné). `false`</span><span class="sxs-lookup"><span data-stu-id="38590-334">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="38590-335">Další informace o vyhledávání na více úrovních najdete v tématu [SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="38590-335">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="38590-336">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="38590-336">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="38590-337">Mezipaměť primárního balíčku.</span><span class="sxs-lookup"><span data-stu-id="38590-337">The primary package cache.</span></span> <span data-ttu-id="38590-338">Pokud není nastavená, použije se `$HOME/.nuget/packages` ve výchozím nastavení `%userprofile%\.nuget\packages` v systému UNIX nebo Windows.</span><span class="sxs-lookup"><span data-stu-id="38590-338">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="38590-339">Určuje umístění indexu údržby používaného sdíleným hostitelem při načítání modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="38590-339">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="38590-340">Určuje, jestli se data o využití nástrojů .NET Core shromažďují a odesílají do Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="38590-340">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="38590-341">Nastavte na `true` výslovný souhlas funkce telemetrie (hodnoty `true`, `1`nebo `yes` přijmout).</span><span class="sxs-lookup"><span data-stu-id="38590-341">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="38590-342">V opačném případě `false` nastavte, aby se přihlásil k funkcím `0`telemetrie ( `no` hodnoty `false`, nebo přijaty).</span><span class="sxs-lookup"><span data-stu-id="38590-342">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="38590-343">Pokud není nastavená, je výchozí `false` nastavení a funkce telemetrie je aktivní.</span><span class="sxs-lookup"><span data-stu-id="38590-343">If not set, the default is `false` and the telemetry feature is active.</span></span>

---
