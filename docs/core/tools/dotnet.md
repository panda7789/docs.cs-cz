---
title: dotnet, příkaz
description: Další informace o příkazu dotnet (obecný ovladač pro rozhraní příkazu .NET Core CLI) a jeho použití.
ms.date: 02/13/2020
ms.openlocfilehash: 8692d419afd528bf49e1dc7dc1a7a5fd698b363b
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134077"
---
# <a name="dotnet-command"></a><span data-ttu-id="bbeec-103">dotnet, příkaz</span><span class="sxs-lookup"><span data-stu-id="bbeec-103">dotnet command</span></span>

<span data-ttu-id="bbeec-104">**Tento článek se týká:** ✔️ .NET Core 2.1 SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="bbeec-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="bbeec-105">Name (Název)</span><span class="sxs-lookup"><span data-stu-id="bbeec-105">Name</span></span>

<span data-ttu-id="bbeec-106">`dotnet`- Obecný ovladač pro rozhraní CLI jádra .NET.</span><span class="sxs-lookup"><span data-stu-id="bbeec-106">`dotnet` - The generic driver for the .NET Core CLI.</span></span>

## <a name="synopsis"></a><span data-ttu-id="bbeec-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="bbeec-107">Synopsis</span></span>

<span data-ttu-id="bbeec-108">Získání informací o dostupných příkazech a prostředí:</span><span class="sxs-lookup"><span data-stu-id="bbeec-108">To get information about the available commands and the environment:</span></span>

```dotnetcli
dotnet [-h|--help] [--version] [--info]
    [--list-runtimes] [--list-sdks]
```

<span data-ttu-id="bbeec-109">Spuštění příkazu (vyžaduje instalaci sady SDK):</span><span class="sxs-lookup"><span data-stu-id="bbeec-109">To run a command (requires SDK installation):</span></span>

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity]
    [command-options] [arguments]
```

<span data-ttu-id="bbeec-110">Spuštění aplikace:</span><span class="sxs-lookup"><span data-stu-id="bbeec-110">To run an application:</span></span>

```dotnetcli
dotnet [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]
```

<span data-ttu-id="bbeec-111">`--roll-forward`je k dispozici od rozhraní .NET Core 3.x.</span><span class="sxs-lookup"><span data-stu-id="bbeec-111">`--roll-forward` is available since .NET Core 3.x.</span></span> <span data-ttu-id="bbeec-112">Slouží `--roll-forward-on-no-candidate-fx` pro rozhraní .NET Core 2.x.</span><span class="sxs-lookup"><span data-stu-id="bbeec-112">Use `--roll-forward-on-no-candidate-fx` for .NET Core 2.x.</span></span>

## <a name="description"></a><span data-ttu-id="bbeec-113">Popis</span><span class="sxs-lookup"><span data-stu-id="bbeec-113">Description</span></span>

<span data-ttu-id="bbeec-114">Příkaz `dotnet` má dvě funkce:</span><span class="sxs-lookup"><span data-stu-id="bbeec-114">The `dotnet` command has two functions:</span></span>

- <span data-ttu-id="bbeec-115">Poskytuje příkazy pro práci s projekty .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bbeec-115">It provides commands for working with .NET Core projects.</span></span>

  <span data-ttu-id="bbeec-116">Například [`dotnet build`](dotnet-build.md) vytvoří projekt.</span><span class="sxs-lookup"><span data-stu-id="bbeec-116">For example, [`dotnet build`](dotnet-build.md) builds a project.</span></span> <span data-ttu-id="bbeec-117">Každý příkaz definuje své vlastní možnosti a argumenty.</span><span class="sxs-lookup"><span data-stu-id="bbeec-117">Each command defines its own options and arguments.</span></span> <span data-ttu-id="bbeec-118">Všechny příkazy `--help` podporují možnost tisku stručné dokumentace o použití příkazu.</span><span class="sxs-lookup"><span data-stu-id="bbeec-118">All commands support the `--help` option for printing out brief documentation about how to use the command.</span></span>

- <span data-ttu-id="bbeec-119">Spouští aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bbeec-119">It runs .NET Core applications.</span></span>

  <span data-ttu-id="bbeec-120">Určíte cestu k `.dll` souboru aplikace pro spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="bbeec-120">You specify the path to an application `.dll` file to run the application.</span></span> <span data-ttu-id="bbeec-121">Například `dotnet myapp.dll` spustí `myapp` aplikaci.</span><span class="sxs-lookup"><span data-stu-id="bbeec-121">For example, `dotnet myapp.dll` runs the `myapp` application.</span></span> <span data-ttu-id="bbeec-122">Informace o možnostech nasazení najdete v tématu [Nasazení aplikace .NET Core.](../deploying/index.md)</span><span class="sxs-lookup"><span data-stu-id="bbeec-122">See [.NET Core application deployment](../deploying/index.md) to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="bbeec-123">Možnosti</span><span class="sxs-lookup"><span data-stu-id="bbeec-123">Options</span></span>

<span data-ttu-id="bbeec-124">Různé možnosti `dotnet` jsou k dispozici samostatně, pro spuštění příkazu a pro spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="bbeec-124">Different options are available for `dotnet` by itself, for running a command, and for running an application.</span></span>

### <a name="options-for-dotnet-by-itself"></a><span data-ttu-id="bbeec-125">Možnosti pro dotnet sám o sobě</span><span class="sxs-lookup"><span data-stu-id="bbeec-125">Options for dotnet by itself</span></span>

<span data-ttu-id="bbeec-126">Následující možnosti `dotnet` jsou samy o sobě.</span><span class="sxs-lookup"><span data-stu-id="bbeec-126">The following options are for `dotnet` by itself.</span></span> <span data-ttu-id="bbeec-127">Například, `dotnet --info`.</span><span class="sxs-lookup"><span data-stu-id="bbeec-127">For example, `dotnet --info`.</span></span> <span data-ttu-id="bbeec-128">Tisknou informace o životním prostředí.</span><span class="sxs-lookup"><span data-stu-id="bbeec-128">They print out information about the environment.</span></span>

- **`--info`**

  <span data-ttu-id="bbeec-129">Vytiskne podrobné informace o instalaci jádra .NET a prostředí počítače, jako je například aktuální operační systém, a potvrdí sha verze .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bbeec-129">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

- **`--version`**

  <span data-ttu-id="bbeec-130">Vytiskne verzi sady .NET Core SDK, která se používá.</span><span class="sxs-lookup"><span data-stu-id="bbeec-130">Prints out the version of the .NET Core SDK in use.</span></span>

- **`--list-runtimes`**

  <span data-ttu-id="bbeec-131">Vytiskne seznam nainstalovaných runčasů jádra .NET.</span><span class="sxs-lookup"><span data-stu-id="bbeec-131">Prints out a list of the installed .NET Core runtimes.</span></span>

- **`--list-sdks`**

  <span data-ttu-id="bbeec-132">Vytiskne seznam nainstalovaných sad SDK jádra .NET.</span><span class="sxs-lookup"><span data-stu-id="bbeec-132">Prints out a list of the installed .NET Core SDKs.</span></span>

- **`-h|--help`**

  <span data-ttu-id="bbeec-133">Vytiskne seznam dostupných příkazů.</span><span class="sxs-lookup"><span data-stu-id="bbeec-133">Prints out a list of available commands.</span></span>

### <a name="sdk-options-for-running-a-command"></a><span data-ttu-id="bbeec-134">Možnosti sady SDK pro spuštění příkazu</span><span class="sxs-lookup"><span data-stu-id="bbeec-134">SDK options for running a command</span></span>

<span data-ttu-id="bbeec-135">Následující možnosti `dotnet` jsou pro s příkazem.</span><span class="sxs-lookup"><span data-stu-id="bbeec-135">The following options are for `dotnet` with a command.</span></span> <span data-ttu-id="bbeec-136">Například, `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="bbeec-136">For example, `dotnet build --help`.</span></span>

- **`-d|--diagnostics`**

  <span data-ttu-id="bbeec-137">Umožňuje diagnostický výstup.</span><span class="sxs-lookup"><span data-stu-id="bbeec-137">Enables diagnostic output.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="bbeec-138">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="bbeec-138">Sets the verbosity level of the command.</span></span> <span data-ttu-id="bbeec-139">Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a .</span><span class="sxs-lookup"><span data-stu-id="bbeec-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="bbeec-140">Není podporováno v každém příkazu.</span><span class="sxs-lookup"><span data-stu-id="bbeec-140">Not supported in every command.</span></span> <span data-ttu-id="bbeec-141">Chcete-li zjistit, zda je tato možnost k dispozici, podívejte se na konkrétní příkazovou stránku.</span><span class="sxs-lookup"><span data-stu-id="bbeec-141">See specific command page to determine if this option is available.</span></span>

- **`-h|--help`**

  <span data-ttu-id="bbeec-142">Vytiskne dokumentaci pro daný `dotnet build --help`příkaz, například .</span><span class="sxs-lookup"><span data-stu-id="bbeec-142">Prints out documentation for a given command, such as `dotnet build --help`.</span></span>

- **`command options`**

  <span data-ttu-id="bbeec-143">Každý příkaz definuje možnosti specifické pro tento příkaz.</span><span class="sxs-lookup"><span data-stu-id="bbeec-143">Each command defines options specific to that command.</span></span> <span data-ttu-id="bbeec-144">Seznam dostupných možností naleznete na konkrétní stránce příkazů.</span><span class="sxs-lookup"><span data-stu-id="bbeec-144">See specific command page for a list of available options.</span></span>

### <a name="runtime-options"></a><span data-ttu-id="bbeec-145">Možnosti běhu</span><span class="sxs-lookup"><span data-stu-id="bbeec-145">Runtime options</span></span>

<span data-ttu-id="bbeec-146">Následující možnosti jsou `dotnet` k dispozici při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="bbeec-146">The following options are available when `dotnet` runs an application.</span></span> <span data-ttu-id="bbeec-147">Například, `dotnet myapp.dll --fx-version 3.1.1`.</span><span class="sxs-lookup"><span data-stu-id="bbeec-147">For example, `dotnet myapp.dll --fx-version 3.1.1`.</span></span>

- **`--additionalprobingpath <PATH>`**

  <span data-ttu-id="bbeec-148">Cesta obsahující sondování zásady a sestavení pro sondu.</span><span class="sxs-lookup"><span data-stu-id="bbeec-148">Path containing probing policy and assemblies to probe.</span></span>

- **`--additional-deps <PATH>`**

  <span data-ttu-id="bbeec-149">Cesta k dalšímu souboru *.deps.json.*</span><span class="sxs-lookup"><span data-stu-id="bbeec-149">Path to an additional *.deps.json* file.</span></span> <span data-ttu-id="bbeec-150">Soubor *deps.json* obsahuje seznam závislostí, závislostí kompilace a informací o verzi, které se používají k řešení konfliktů sestavení.</span><span class="sxs-lookup"><span data-stu-id="bbeec-150">A *deps.json* file contains a list of dependencies, compilation dependencies, and version information used to address assembly conflicts.</span></span> <span data-ttu-id="bbeec-151">Další informace najdete [v tématu Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="bbeec-151">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

- **`--fx-version <VERSION>`**

  <span data-ttu-id="bbeec-152">Verze runtime .NET Core, která se má použít ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="bbeec-152">Version of the .NET Core runtime to use to run the application.</span></span>

- **`--runtimeconfig`**

  <span data-ttu-id="bbeec-153">Cesta k souboru *runtimeconfig.json.*</span><span class="sxs-lookup"><span data-stu-id="bbeec-153">Path to a *runtimeconfig.json* file.</span></span> <span data-ttu-id="bbeec-154">Soubor *runtimeconfig.json* je konfigurační soubor, který obsahuje nastavení běhu.</span><span class="sxs-lookup"><span data-stu-id="bbeec-154">A *runtimeconfig.json* file is a configuration file that contains run-time settings.</span></span> <span data-ttu-id="bbeec-155">Další informace naleznete v [tématu Nastavení konfigurace rozhraní .NET Core run-time](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="bbeec-155">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

- <span data-ttu-id="bbeec-156">**`--roll-forward-on-no-candidate-fx <N>`\*\*\*\*K dispozici v sdk .NET Core 2.x.**</span><span class="sxs-lookup"><span data-stu-id="bbeec-156">**`--roll-forward-on-no-candidate-fx <N>`** **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="bbeec-157">Definuje chování, když není k dispozici požadovaná sdílená architektura.</span><span class="sxs-lookup"><span data-stu-id="bbeec-157">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="bbeec-158">`N`může být:</span><span class="sxs-lookup"><span data-stu-id="bbeec-158">`N` can be:</span></span>

  - <span data-ttu-id="bbeec-159">`0`- Zakázat i menší verze roll vpřed.</span><span class="sxs-lookup"><span data-stu-id="bbeec-159">`0` - Disable even minor version roll forward.</span></span>
  - <span data-ttu-id="bbeec-160">`1`- Roll vpřed na dílčí verzi, ale ne na hlavní verzi.</span><span class="sxs-lookup"><span data-stu-id="bbeec-160">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="bbeec-161">Toto je výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="bbeec-161">This is the default behavior.</span></span>
  - <span data-ttu-id="bbeec-162">`2`- Roll vpřed na menší a hlavní verze.</span><span class="sxs-lookup"><span data-stu-id="bbeec-162">`2` - Roll forward on minor and major versions.</span></span>

   <span data-ttu-id="bbeec-163">Další informace naleznete v [tématu Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="bbeec-163">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

- <span data-ttu-id="bbeec-164">**`--roll-forward <SETTING>`\*\*\*\*K dispozici počínaje sadou .NET Core SDK 3.0.**</span><span class="sxs-lookup"><span data-stu-id="bbeec-164">**`--roll-forward <SETTING>`** **Available starting with .NET Core SDK 3.0.**</span></span>

  <span data-ttu-id="bbeec-165">Určuje, jak se v aplikaci použije posun vpřed.</span><span class="sxs-lookup"><span data-stu-id="bbeec-165">Controls how roll forward is applied to the app.</span></span> <span data-ttu-id="bbeec-166">Může `SETTING` být jedna z následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="bbeec-166">The `SETTING` can be one of the following values.</span></span> <span data-ttu-id="bbeec-167">Pokud není `Minor` zadán, je výchozí.</span><span class="sxs-lookup"><span data-stu-id="bbeec-167">If not specified, `Minor` is the default.</span></span>

  - <span data-ttu-id="bbeec-168">`LatestPatch`- Přetočte se dopředu na nejvyšší verzi opravy.</span><span class="sxs-lookup"><span data-stu-id="bbeec-168">`LatestPatch` - Roll forward to the highest patch version.</span></span> <span data-ttu-id="bbeec-169">Tím se zakáže dílčí verze posunout vpřed.</span><span class="sxs-lookup"><span data-stu-id="bbeec-169">This disables minor version roll forward.</span></span>
  - <span data-ttu-id="bbeec-170">`Minor`- Převrátit na nejnižší vyšší dílčí verze, pokud je požadována dílčí verze chybí.</span><span class="sxs-lookup"><span data-stu-id="bbeec-170">`Minor` - Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="bbeec-171">Pokud je k dispozici požadovaná dílčí verze, použije se zásada LatestPatch.</span><span class="sxs-lookup"><span data-stu-id="bbeec-171">If the requested minor version is present, then the LatestPatch policy is used.</span></span>
  - <span data-ttu-id="bbeec-172">`Major`- Roll vpřed na nejnižší vyšší hlavní verze, a nejnižší dílčí verze, pokud požadované hlavní verze chybí.</span><span class="sxs-lookup"><span data-stu-id="bbeec-172">`Major` - Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="bbeec-173">Pokud je k dispozici požadovaná hlavní verze, použije se zásada Vedlejší.</span><span class="sxs-lookup"><span data-stu-id="bbeec-173">If the requested major version is present, then the Minor policy is used.</span></span>
  - <span data-ttu-id="bbeec-174">`LatestMinor`- Převrátit na nejvyšší dílčí verzi, a to i v případě, že je požadována dílčí verze je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="bbeec-174">`LatestMinor` - Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="bbeec-175">Určeno pro scénáře hostování komponent.</span><span class="sxs-lookup"><span data-stu-id="bbeec-175">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="bbeec-176">`LatestMajor`- Převrátit na nejvyšší hlavní a nejvyšší dílčí verze, i když požadované hlavní je přítomen.</span><span class="sxs-lookup"><span data-stu-id="bbeec-176">`LatestMajor` - Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="bbeec-177">Určeno pro scénáře hostování komponent.</span><span class="sxs-lookup"><span data-stu-id="bbeec-177">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="bbeec-178">`Disable`- Neotáčejte se dopředu.</span><span class="sxs-lookup"><span data-stu-id="bbeec-178">`Disable` - Don't roll forward.</span></span> <span data-ttu-id="bbeec-179">Spojte se pouze se zadanou verzí.</span><span class="sxs-lookup"><span data-stu-id="bbeec-179">Only bind to specified version.</span></span> <span data-ttu-id="bbeec-180">Tato zásada se nedoporučuje pro obecné použití, protože zakáže možnost převést na nejnovější opravy.</span><span class="sxs-lookup"><span data-stu-id="bbeec-180">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="bbeec-181">Tato hodnota je doporučena pouze pro testování.</span><span class="sxs-lookup"><span data-stu-id="bbeec-181">This value is only recommended for testing.</span></span>

<span data-ttu-id="bbeec-182">S výjimkou `Disable`aplikace budou všechna nastavení používat nejvyšší dostupnou verzi opravy.</span><span class="sxs-lookup"><span data-stu-id="bbeec-182">With the exception of `Disable`, all settings will use the highest available patch version.</span></span>

<span data-ttu-id="bbeec-183">Chování posunout vpřed lze také nakonfigurovat ve vlastnosti souboru projektu, vlastnosti konfiguračního souboru za běhu a proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="bbeec-183">Roll forward behavior can also be configured in a project file property, a run-time configuration file property, and an environment variable.</span></span> <span data-ttu-id="bbeec-184">Další informace naleznete v [tématu Hlavní verze runtime posun vpřed](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span><span class="sxs-lookup"><span data-stu-id="bbeec-184">For more information, see [Major-version runtime roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span></span>

## <a name="dotnet-commands"></a><span data-ttu-id="bbeec-185">Příkazy dotnet</span><span class="sxs-lookup"><span data-stu-id="bbeec-185">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="bbeec-186">Obecné</span><span class="sxs-lookup"><span data-stu-id="bbeec-186">General</span></span>

| <span data-ttu-id="bbeec-187">Příkaz</span><span class="sxs-lookup"><span data-stu-id="bbeec-187">Command</span></span>                                       | <span data-ttu-id="bbeec-188">Funkce</span><span class="sxs-lookup"><span data-stu-id="bbeec-188">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="bbeec-189">dotnet build</span><span class="sxs-lookup"><span data-stu-id="bbeec-189">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="bbeec-190">Vytvoří aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bbeec-190">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="bbeec-191">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="bbeec-191">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="bbeec-192">Spolupracuje se servery spuštěnými sestavením.</span><span class="sxs-lookup"><span data-stu-id="bbeec-192">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="bbeec-193">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="bbeec-193">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="bbeec-194">Čisté výstupy sestavení.</span><span class="sxs-lookup"><span data-stu-id="bbeec-194">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="bbeec-195">dotnet help</span><span class="sxs-lookup"><span data-stu-id="bbeec-195">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="bbeec-196">Zobrazuje podrobnější dokumentaci online pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="bbeec-196">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="bbeec-197">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="bbeec-197">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="bbeec-198">Přenese platný projekt Preview 2 do projektu .NET Core SDK 1.0.</span><span class="sxs-lookup"><span data-stu-id="bbeec-198">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="bbeec-199">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="bbeec-199">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="bbeec-200">Poskytuje přístup k příkazovému řádku MSBuild.</span><span class="sxs-lookup"><span data-stu-id="bbeec-200">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="bbeec-201">dotnet new</span><span class="sxs-lookup"><span data-stu-id="bbeec-201">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="bbeec-202">Inicializuje projekt C# nebo F# pro danou šablonu.</span><span class="sxs-lookup"><span data-stu-id="bbeec-202">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="bbeec-203">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="bbeec-203">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="bbeec-204">Vytvoří balíček NuGet vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="bbeec-204">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="bbeec-205">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="bbeec-205">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="bbeec-206">Publikuje aplikaci závislou na rozhraní .NET nebo samostatnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="bbeec-206">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="bbeec-207">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="bbeec-207">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="bbeec-208">Obnoví závislosti pro danou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="bbeec-208">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="bbeec-209">dotnet run</span><span class="sxs-lookup"><span data-stu-id="bbeec-209">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="bbeec-210">Spustí aplikaci ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="bbeec-210">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="bbeec-211">dotnet run</span><span class="sxs-lookup"><span data-stu-id="bbeec-211">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="bbeec-212">Možnosti pro přidání, odebrání a seznam projektů v souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="bbeec-212">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="bbeec-213">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="bbeec-213">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="bbeec-214">Ukládá sestavení v runtime balíček úložiště.</span><span class="sxs-lookup"><span data-stu-id="bbeec-214">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="bbeec-215">dotnet test</span><span class="sxs-lookup"><span data-stu-id="bbeec-215">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="bbeec-216">Spustí testy pomocí testovacího běhu.</span><span class="sxs-lookup"><span data-stu-id="bbeec-216">Runs tests using a test runner.</span></span>                                     |

### <a name="project-references"></a><span data-ttu-id="bbeec-217">Odkazy na projekty</span><span class="sxs-lookup"><span data-stu-id="bbeec-217">Project references</span></span>

<span data-ttu-id="bbeec-218">Příkaz</span><span class="sxs-lookup"><span data-stu-id="bbeec-218">Command</span></span> | <span data-ttu-id="bbeec-219">Funkce</span><span class="sxs-lookup"><span data-stu-id="bbeec-219">Function</span></span>
--- | ---
[<span data-ttu-id="bbeec-220">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="bbeec-220">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="bbeec-221">Přidá odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="bbeec-221">Adds a project reference.</span></span>
[<span data-ttu-id="bbeec-222">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="bbeec-222">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="bbeec-223">Zobrazí seznam odkazů na projekt.</span><span class="sxs-lookup"><span data-stu-id="bbeec-223">Lists project references.</span></span>
[<span data-ttu-id="bbeec-224">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="bbeec-224">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="bbeec-225">Odebere odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="bbeec-225">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="bbeec-226">Balíčky NuGet</span><span class="sxs-lookup"><span data-stu-id="bbeec-226">NuGet packages</span></span>

<span data-ttu-id="bbeec-227">Příkaz</span><span class="sxs-lookup"><span data-stu-id="bbeec-227">Command</span></span> | <span data-ttu-id="bbeec-228">Funkce</span><span class="sxs-lookup"><span data-stu-id="bbeec-228">Function</span></span>
--- | ---
[<span data-ttu-id="bbeec-229">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="bbeec-229">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="bbeec-230">Přidá balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="bbeec-230">Adds a NuGet package.</span></span>
[<span data-ttu-id="bbeec-231">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="bbeec-231">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="bbeec-232">Odebere balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="bbeec-232">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="bbeec-233">Příkazy NuGet</span><span class="sxs-lookup"><span data-stu-id="bbeec-233">NuGet commands</span></span>

<span data-ttu-id="bbeec-234">Příkaz</span><span class="sxs-lookup"><span data-stu-id="bbeec-234">Command</span></span> | <span data-ttu-id="bbeec-235">Funkce</span><span class="sxs-lookup"><span data-stu-id="bbeec-235">Function</span></span>
--- | ---
[<span data-ttu-id="bbeec-236">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="bbeec-236">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="bbeec-237">Odstraní nebo odřadí seznam balíčku ze serveru.</span><span class="sxs-lookup"><span data-stu-id="bbeec-237">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="bbeec-238">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="bbeec-238">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="bbeec-239">Odešle balíček na server a publikuje jej.</span><span class="sxs-lookup"><span data-stu-id="bbeec-239">Pushes a package to the server and publishes it.</span></span>
[<span data-ttu-id="bbeec-240">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="bbeec-240">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="bbeec-241">Vymaže nebo zobrazí seznam místních prostředků NuGet, jako je například mezipaměť http-request, dočasná mezipaměť nebo globální balíček pro celý počítač.</span><span class="sxs-lookup"><span data-stu-id="bbeec-241">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="bbeec-242">dotnet nuget přidat zdroj</span><span class="sxs-lookup"><span data-stu-id="bbeec-242">dotnet nuget add source</span></span>](dotnet-nuget-add-source.md) | <span data-ttu-id="bbeec-243">Přidá zdroj NuGet.</span><span class="sxs-lookup"><span data-stu-id="bbeec-243">Adds a NuGet source.</span></span>
[<span data-ttu-id="bbeec-244">dotnet nuget zakázat zdroj</span><span class="sxs-lookup"><span data-stu-id="bbeec-244">dotnet nuget disable source</span></span>](dotnet-nuget-disable-source.md) | <span data-ttu-id="bbeec-245">Zakáže zdroj NuGet.</span><span class="sxs-lookup"><span data-stu-id="bbeec-245">Disables a NuGet source.</span></span>
[<span data-ttu-id="bbeec-246">dotnet nuget povolit zdroj</span><span class="sxs-lookup"><span data-stu-id="bbeec-246">dotnet nuget enable source</span></span>](dotnet-nuget-enable-source.md) | <span data-ttu-id="bbeec-247">Povolí zdroj NuGet.</span><span class="sxs-lookup"><span data-stu-id="bbeec-247">Enables a NuGet source.</span></span>
[<span data-ttu-id="bbeec-248">Zdroj seznamu nugetu dotnet</span><span class="sxs-lookup"><span data-stu-id="bbeec-248">dotnet nuget list source</span></span>](dotnet-nuget-list-source.md) | <span data-ttu-id="bbeec-249">Zobrazí seznam všech nakonfigurovaných zdrojů NuGet.</span><span class="sxs-lookup"><span data-stu-id="bbeec-249">Lists all configured NuGet sources.</span></span>
[<span data-ttu-id="bbeec-250">dotnet nuget odebrat zdroj</span><span class="sxs-lookup"><span data-stu-id="bbeec-250">dotnet nuget remove source</span></span>](dotnet-nuget-remove-source.md) | <span data-ttu-id="bbeec-251">Odebere zdroj NuGet.</span><span class="sxs-lookup"><span data-stu-id="bbeec-251">Removes a NuGet source.</span></span>
[<span data-ttu-id="bbeec-252">Zdroj aktualizace dotnet nuget</span><span class="sxs-lookup"><span data-stu-id="bbeec-252">dotnet nuget update source</span></span>](dotnet-nuget-update-source.md) | <span data-ttu-id="bbeec-253">Aktualizuje zdroj NuGet.</span><span class="sxs-lookup"><span data-stu-id="bbeec-253">Updates a NuGet source.</span></span>

### <a name="global-tool-path-and-local-tools-commands"></a><span data-ttu-id="bbeec-254">Příkazy globálních nástrojů, cest nástrojů a místních nástrojů</span><span class="sxs-lookup"><span data-stu-id="bbeec-254">Global, tool-path, and local tools commands</span></span>

<span data-ttu-id="bbeec-255">Nástroje jsou konzolové aplikace, které jsou nainstalovány z balíčků NuGet a jsou vyvolány z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="bbeec-255">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="bbeec-256">Můžete psát nástroje sami nebo instalovat nástroje napsané třetími stranami.</span><span class="sxs-lookup"><span data-stu-id="bbeec-256">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="bbeec-257">Nástroje jsou také známé jako globální nástroje, nástroje pro cestu nástrojů a místní nástroje.</span><span class="sxs-lookup"><span data-stu-id="bbeec-257">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="bbeec-258">Další informace naleznete v tématu [Přehled nástrojů .NET Core](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="bbeec-258">For more information, see [.NET Core tools overview](global-tools.md).</span></span> <span data-ttu-id="bbeec-259">Globální nástroje a nástroje cesta jsou k dispozici počínaje .NET Core SDK 2.1.</span><span class="sxs-lookup"><span data-stu-id="bbeec-259">Global and tool-path tools are available starting with .NET Core SDK 2.1.</span></span> <span data-ttu-id="bbeec-260">Místní nástroje jsou k dispozici počínaje .NET Core SDK 3.0.</span><span class="sxs-lookup"><span data-stu-id="bbeec-260">Local tools are available starting with .NET Core SDK 3.0.</span></span>

<span data-ttu-id="bbeec-261">Příkaz</span><span class="sxs-lookup"><span data-stu-id="bbeec-261">Command</span></span> | <span data-ttu-id="bbeec-262">Funkce</span><span class="sxs-lookup"><span data-stu-id="bbeec-262">Function</span></span>
--- | ---
[<span data-ttu-id="bbeec-263">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="bbeec-263">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="bbeec-264">Nainstaluje do počítače nástroj.</span><span class="sxs-lookup"><span data-stu-id="bbeec-264">Installs a tool on your machine.</span></span>
[<span data-ttu-id="bbeec-265">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="bbeec-265">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="bbeec-266">Zobrazí seznam všech globálních, nástrojových cest nebo místních nástrojů, které jsou v počítači aktuálně nainstalovány.</span><span class="sxs-lookup"><span data-stu-id="bbeec-266">Lists all global, tool-path, or local tools currently installed on your machine.</span></span>
[<span data-ttu-id="bbeec-267">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="bbeec-267">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="bbeec-268">Odinstaluje nástroj ze zařízení.</span><span class="sxs-lookup"><span data-stu-id="bbeec-268">Uninstalls a tool from your machine.</span></span>
[<span data-ttu-id="bbeec-269">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="bbeec-269">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="bbeec-270">Aktualizuje nástroj, který je nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="bbeec-270">Updates a tool that is installed on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="bbeec-271">Další nástroje</span><span class="sxs-lookup"><span data-stu-id="bbeec-271">Additional tools</span></span>

<span data-ttu-id="bbeec-272">Počínaje .NET Core SDK 2.1.300, počet nástrojů, které byly k `DotnetCliToolReference` dispozici pouze na základě projektu pomocí jsou nyní k dispozici jako součást .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="bbeec-272">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="bbeec-273">Tyto nástroje jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="bbeec-273">These tools are listed in the following table:</span></span>

| <span data-ttu-id="bbeec-274">Nástroj</span><span class="sxs-lookup"><span data-stu-id="bbeec-274">Tool</span></span>                                              | <span data-ttu-id="bbeec-275">Funkce</span><span class="sxs-lookup"><span data-stu-id="bbeec-275">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="bbeec-276">dev-certs</span><span class="sxs-lookup"><span data-stu-id="bbeec-276">dev-certs</span></span>                                         | <span data-ttu-id="bbeec-277">Vytváří a spravuje vývojové certifikáty.</span><span class="sxs-lookup"><span data-stu-id="bbeec-277">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="bbeec-278">Ef</span><span class="sxs-lookup"><span data-stu-id="bbeec-278">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="bbeec-279">Nástroje příkazového řádku Core entity Framework.</span><span class="sxs-lookup"><span data-stu-id="bbeec-279">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="bbeec-280">sql-cache</span><span class="sxs-lookup"><span data-stu-id="bbeec-280">sql-cache</span></span>                                         | <span data-ttu-id="bbeec-281">Nástroje příkazového řádku mezipaměti serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="bbeec-281">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="bbeec-282">uživatelské tajemství</span><span class="sxs-lookup"><span data-stu-id="bbeec-282">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="bbeec-283">Spravuje tajné kódy uživatelů vývoje.</span><span class="sxs-lookup"><span data-stu-id="bbeec-283">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="bbeec-284">Sledovat</span><span class="sxs-lookup"><span data-stu-id="bbeec-284">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="bbeec-285">Spustí sledovací proces souboru, který spustí příkaz při změně souborů.</span><span class="sxs-lookup"><span data-stu-id="bbeec-285">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="bbeec-286">Další informace o jednotlivých `dotnet <tool-name> --help`nástrojích získáte zadáním příkazu .</span><span class="sxs-lookup"><span data-stu-id="bbeec-286">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="bbeec-287">Příklady</span><span class="sxs-lookup"><span data-stu-id="bbeec-287">Examples</span></span>

<span data-ttu-id="bbeec-288">Vytvořte novou aplikaci konzoly .NET Core:</span><span class="sxs-lookup"><span data-stu-id="bbeec-288">Create a new .NET Core console application:</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="bbeec-289">Sestavení projektu a jeho závislostí v daném adresáři:</span><span class="sxs-lookup"><span data-stu-id="bbeec-289">Build a project and its dependencies in a given directory:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="bbeec-290">Spuštění aplikace:</span><span class="sxs-lookup"><span data-stu-id="bbeec-290">Run an application:</span></span>

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a><span data-ttu-id="bbeec-291">Proměnné prostředí</span><span class="sxs-lookup"><span data-stu-id="bbeec-291">Environment variables</span></span>

- <span data-ttu-id="bbeec-292">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span><span class="sxs-lookup"><span data-stu-id="bbeec-292">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span></span>

  <span data-ttu-id="bbeec-293">Určuje umístění runčasů jádra .NET, pokud nejsou nainstalovány ve výchozím umístění.</span><span class="sxs-lookup"><span data-stu-id="bbeec-293">Specifies the location of the .NET Core runtimes, if they are not installed in the default location.</span></span> <span data-ttu-id="bbeec-294">Výchozí umístění v `C:\Program Files\dotnet`systému Windows je .</span><span class="sxs-lookup"><span data-stu-id="bbeec-294">The default location on Windows is `C:\Program Files\dotnet`.</span></span> <span data-ttu-id="bbeec-295">Výchozí umístění na Linuxu a `/usr/share/dotnet`macOS je .</span><span class="sxs-lookup"><span data-stu-id="bbeec-295">The default location on Linux and macOS is `/usr/share/dotnet`.</span></span> <span data-ttu-id="bbeec-296">Tato proměnná prostředí se používá pouze při spouštění aplikací prostřednictvím generovaných spustitelných souborů (apphosts).</span><span class="sxs-lookup"><span data-stu-id="bbeec-296">This environment variable is used only when running apps via generated executables (apphosts).</span></span> <span data-ttu-id="bbeec-297">`DOTNET_ROOT(x86)`se používá místo toho při spuštění 32bitového spustitelného souboru v 64bitovém osu.</span><span class="sxs-lookup"><span data-stu-id="bbeec-297">`DOTNET_ROOT(x86)` is used instead when running a 32-bit executable on a 64-bit OS.</span></span>

- `DOTNET_PACKAGES`

  <span data-ttu-id="bbeec-298">Složka globálních balíčků.</span><span class="sxs-lookup"><span data-stu-id="bbeec-298">The global packages folder.</span></span> <span data-ttu-id="bbeec-299">Pokud není nastavena, `~/.nuget/packages` je výchozí `%userprofile%\.nuget\packages` na Unix nebo na Windows.</span><span class="sxs-lookup"><span data-stu-id="bbeec-299">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

- `DOTNET_SERVICING`

  <span data-ttu-id="bbeec-300">Určuje umístění indexu obsluhy, který má sdílený hostitel použít při načítání za běhu.</span><span class="sxs-lookup"><span data-stu-id="bbeec-300">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

- `DOTNET_NOLOGO`

  <span data-ttu-id="bbeec-301">Určuje, zda se při prvním spuštění zobrazí uvítání a telemetrické zprávy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bbeec-301">Specifies whether .NET Core welcome and telemetry messages are displayed on first run.</span></span> <span data-ttu-id="bbeec-302">Nastaví `true` ztlumení těchto zpráv `true` `1`(hodnoty `yes` , nebo `false` přijaté) nebo `false` `0`na `no` povolit (hodnoty , nebo přijaté).</span><span class="sxs-lookup"><span data-stu-id="bbeec-302">Set to `true` to mute these messages (values `true`, `1`, or `yes` accepted) or set to `false` to allow (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="bbeec-303">Pokud není nastavena, `false` výchozí je a zprávy se zobrazí při prvním spuštění.</span><span class="sxs-lookup"><span data-stu-id="bbeec-303">If not set, the default is `false` and the messages will be displayed on first run.</span></span> <span data-ttu-id="bbeec-304">Všimněte si, že tento příznak `DOTNET_CLI_TELEMETRY_OPTOUT` nemá žádný vliv na telemetrii (viz pro odhlášení odesílání telemetrie).</span><span class="sxs-lookup"><span data-stu-id="bbeec-304">Note that this flag has no effect on telemetry (see `DOTNET_CLI_TELEMETRY_OPTOUT` for opting out of sending telemetry).</span></span>

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  <span data-ttu-id="bbeec-305">Určuje, zda jsou data o použití nástrojů .NET Core shromažďována a odesílána společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bbeec-305">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="bbeec-306">Nastavte `true` na odhlášení z funkce telemetrie (hodnoty `true`, `1`nebo `yes` přijaté).</span><span class="sxs-lookup"><span data-stu-id="bbeec-306">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="bbeec-307">V opačném `false` případě nastavte na opt-li `false` `0`do `no` funkce telemetrie (hodnoty , nebo přijat).</span><span class="sxs-lookup"><span data-stu-id="bbeec-307">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="bbeec-308">Pokud není nastavena, `false` výchozí je a funkce telemetrie je aktivní.</span><span class="sxs-lookup"><span data-stu-id="bbeec-308">If not set, the default is `false` and the telemetry feature is active.</span></span>

- `DOTNET_MULTILEVEL_LOOKUP`

  <span data-ttu-id="bbeec-309">Určuje, zda jsou z globálního umístění vyřešeny zaběhu .NET Core, sdílené ho frameworku nebo sdk.</span><span class="sxs-lookup"><span data-stu-id="bbeec-309">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="bbeec-310">Pokud není nastavena, je výchozí `true`hodnota 1 (logické).</span><span class="sxs-lookup"><span data-stu-id="bbeec-310">If not set, it defaults to 1 (logical `true`).</span></span> <span data-ttu-id="bbeec-311">Nastavte 0 (logické) `false`není vyřešit z globálního umístění a mají izolované instalace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bbeec-311">Set to 0 (logical `false`) to not resolve from the global location and have isolated .NET Core installations.</span></span> <span data-ttu-id="bbeec-312">Další informace o víceúrovňovém vyhledávání naleznete v [tématu Vyhledávání SharedFX na více úrovních](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="bbeec-312">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

- <span data-ttu-id="bbeec-313">`DOTNET_ROLL_FORWARD`**K dispozici počínaje sadou .NET Core 3.x SDK.**</span><span class="sxs-lookup"><span data-stu-id="bbeec-313">`DOTNET_ROLL_FORWARD` **Available starting with .NET Core 3.x SDK.**</span></span>

  <span data-ttu-id="bbeec-314">Určuje chování posunout vpřed.</span><span class="sxs-lookup"><span data-stu-id="bbeec-314">Determines roll forward behavior.</span></span> <span data-ttu-id="bbeec-315">Další informace naleznete `--roll-forward` v této možnosti dříve v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="bbeec-315">For more information, see the `--roll-forward` option earlier in this article.</span></span>

- <span data-ttu-id="bbeec-316">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`**K dispozici v sdk .NET Core 2.x.**</span><span class="sxs-lookup"><span data-stu-id="bbeec-316">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="bbeec-317">Zakáže dílčí verze posunout `0`vpřed, pokud je nastavena na .</span><span class="sxs-lookup"><span data-stu-id="bbeec-317">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="bbeec-318">Další informace naleznete v [tématu Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="bbeec-318">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

- `DOTNET_CLI_UI_LANGUAGE`

  <span data-ttu-id="bbeec-319">Nastaví jazyk rozhraní rozhraní rozhraní SEkatelu `en-us`pomocí hodnoty národního prostředí, například .</span><span class="sxs-lookup"><span data-stu-id="bbeec-319">Sets the language of the CLI UI using a locale value such as `en-us`.</span></span> <span data-ttu-id="bbeec-320">Podporované hodnoty jsou stejné jako pro Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bbeec-320">The supported values are the same as for Visual Studio.</span></span> <span data-ttu-id="bbeec-321">Další informace naleznete v části o změně jazyka instalačního programu v [dokumentaci k instalaci sady Visual Studio](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019).</span><span class="sxs-lookup"><span data-stu-id="bbeec-321">For more information, see the section on changing the installer language in the [Visual Studio installation documentation](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019).</span></span> <span data-ttu-id="bbeec-322">Platí pravidla správce prostředků .NET, takže nemusíte vybírat přesnou shodu,&mdash; `CultureInfo` můžete také vybrat potomky ve stromu.</span><span class="sxs-lookup"><span data-stu-id="bbeec-322">The .NET resource manager rules apply, so you don't have to pick an exact match&mdash;you can also pick descendants in the `CultureInfo` tree.</span></span> <span data-ttu-id="bbeec-323">Pokud ji například nastavíte na `fr-CA`, vykázané nastavení matné a konstatování překlady vyhledá a použije. `fr`</span><span class="sxs-lookup"><span data-stu-id="bbeec-323">For example, if you set it to `fr-CA`, the CLI will find and use the `fr` translations.</span></span> <span data-ttu-id="bbeec-324">Pokud jej nastavíte na jazyk, který není podporován, rozhraní se konkretním rozhraním SE vrátí zpět do angličtiny.</span><span class="sxs-lookup"><span data-stu-id="bbeec-324">If you set it to a language that is not supported, the CLI falls back to English.</span></span>

- `DOTNET_DISABLE_GUI_ERRORS`

  <span data-ttu-id="bbeec-325">Pro gui-umožnil generované spustitelné soubory - zakáže dialogové okno, které obvykle ukazuje pro určité třídy chyb.</span><span class="sxs-lookup"><span data-stu-id="bbeec-325">For GUI-enabled generated executables - disables dialog popup, which normally shows for certain classes of errors.</span></span> <span data-ttu-id="bbeec-326">Pouze zapisuje `stderr` a ukončí v těchto případech.</span><span class="sxs-lookup"><span data-stu-id="bbeec-326">It only writes to `stderr` and exits in those cases.</span></span>
  
- `DOTNET_ADDITIONAL_DEPS`

  <span data-ttu-id="bbeec-327">Ekvivalentní možnost ipříkazové konzace `--additional-deps`.</span><span class="sxs-lookup"><span data-stu-id="bbeec-327">Equivalent to CLI option `--additional-deps`.</span></span>

- `DOTNET_RUNTIME_ID`

  <span data-ttu-id="bbeec-328">Přepíše zjištěný rid.</span><span class="sxs-lookup"><span data-stu-id="bbeec-328">Overrides the detected RID.</span></span>

- `DOTNET_SHARED_STORE`

  <span data-ttu-id="bbeec-329">Umístění "sdílenéúložiště", které rozlišení sestavení spadá zpět do v některých případech.</span><span class="sxs-lookup"><span data-stu-id="bbeec-329">Location of the "shared store" which assembly resolution falls back to in some cases.</span></span>

- `DOTNET_STARTUP_HOOKS`

  <span data-ttu-id="bbeec-330">Seznam sestavení pro načtení a spuštění spouštěcích háků z.</span><span class="sxs-lookup"><span data-stu-id="bbeec-330">List of assemblies to load and execute startup hooks from.</span></span>

- <span data-ttu-id="bbeec-331">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span><span class="sxs-lookup"><span data-stu-id="bbeec-331">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span></span>

  <span data-ttu-id="bbeec-332">Řídí diagnostiku trasování z hostitelských `dotnet.exe`součástí, například , `hostfxr`a `hostpolicy`.</span><span class="sxs-lookup"><span data-stu-id="bbeec-332">Controls diagnostics tracing from the hosting components, such as `dotnet.exe`, `hostfxr`, and `hostpolicy`.</span></span>

## <a name="see-also"></a><span data-ttu-id="bbeec-333">Viz také</span><span class="sxs-lookup"><span data-stu-id="bbeec-333">See also</span></span>

- [<span data-ttu-id="bbeec-334">Konfigurační soubory runtime</span><span class="sxs-lookup"><span data-stu-id="bbeec-334">Runtime Configuration Files</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [<span data-ttu-id="bbeec-335">Nastavení konfigurace jádra .NET</span><span class="sxs-lookup"><span data-stu-id="bbeec-335">.NET Core run-time configuration settings</span></span>](../run-time-config/index.md)
