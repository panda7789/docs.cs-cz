---
title: dotnet, příkaz
description: Další informace o příkazu dotnet (obecný ovladač pro rozhraní příkazu .NET Core CLI) a jeho použití.
ms.date: 02/13/2020
ms.openlocfilehash: 6a08297499d955db44e342dc82fed25b7b9b8171
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739069"
---
# <a name="dotnet-command"></a><span data-ttu-id="53996-103">dotnet, příkaz</span><span class="sxs-lookup"><span data-stu-id="53996-103">dotnet command</span></span>

<span data-ttu-id="53996-104">**Tento článek se týká:** ✔️ .NET Core 2.1 SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="53996-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="53996-105">Název</span><span class="sxs-lookup"><span data-stu-id="53996-105">Name</span></span>

<span data-ttu-id="53996-106">`dotnet`- Obecný ovladač pro rozhraní CLI jádra .NET.</span><span class="sxs-lookup"><span data-stu-id="53996-106">`dotnet` - The generic driver for the .NET Core CLI.</span></span>

## <a name="synopsis"></a><span data-ttu-id="53996-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="53996-107">Synopsis</span></span>

<span data-ttu-id="53996-108">Získání informací o dostupných příkazech a prostředí:</span><span class="sxs-lookup"><span data-stu-id="53996-108">To get information about the available commands and the environment:</span></span>

```dotnetcli
dotnet [--version] [--info] [--list-runtimes] [--list-sdks]

dotnet -h|--help
```

<span data-ttu-id="53996-109">Spuštění příkazu (vyžaduje instalaci sady SDK):</span><span class="sxs-lookup"><span data-stu-id="53996-109">To run a command (requires SDK installation):</span></span>

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity <LEVEL>]
    [command-options] [arguments]
```

<span data-ttu-id="53996-110">Spuštění aplikace:</span><span class="sxs-lookup"><span data-stu-id="53996-110">To run an application:</span></span>

```dotnetcli
dotnet [--additionalprobingpath <PATH>] [--additional-deps <PATH>]
    [--fx-version <VERSION>]  [--roll-forward <SETTING>]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps <PATH>]
    [--fx-version <VERSION>]  [--roll-forward <SETTING>]
    <PATH_TO_APPLICATION> [arguments]
```

<span data-ttu-id="53996-111">`--roll-forward`je k dispozici od rozhraní .NET Core 3.x.</span><span class="sxs-lookup"><span data-stu-id="53996-111">`--roll-forward` is available since .NET Core 3.x.</span></span> <span data-ttu-id="53996-112">Slouží `--roll-forward-on-no-candidate-fx` pro rozhraní .NET Core 2.x.</span><span class="sxs-lookup"><span data-stu-id="53996-112">Use `--roll-forward-on-no-candidate-fx` for .NET Core 2.x.</span></span>

## <a name="description"></a><span data-ttu-id="53996-113">Popis</span><span class="sxs-lookup"><span data-stu-id="53996-113">Description</span></span>

<span data-ttu-id="53996-114">Příkaz `dotnet` má dvě funkce:</span><span class="sxs-lookup"><span data-stu-id="53996-114">The `dotnet` command has two functions:</span></span>

- <span data-ttu-id="53996-115">Poskytuje příkazy pro práci s projekty .NET Core.</span><span class="sxs-lookup"><span data-stu-id="53996-115">It provides commands for working with .NET Core projects.</span></span>

  <span data-ttu-id="53996-116">Například [`dotnet build`](dotnet-build.md) vytvoří projekt.</span><span class="sxs-lookup"><span data-stu-id="53996-116">For example, [`dotnet build`](dotnet-build.md) builds a project.</span></span> <span data-ttu-id="53996-117">Každý příkaz definuje své vlastní možnosti a argumenty.</span><span class="sxs-lookup"><span data-stu-id="53996-117">Each command defines its own options and arguments.</span></span> <span data-ttu-id="53996-118">Všechny příkazy `--help` podporují možnost tisku stručné dokumentace o použití příkazu.</span><span class="sxs-lookup"><span data-stu-id="53996-118">All commands support the `--help` option for printing out brief documentation about how to use the command.</span></span>

- <span data-ttu-id="53996-119">Spouští aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="53996-119">It runs .NET Core applications.</span></span>

  <span data-ttu-id="53996-120">Určíte cestu k `.dll` souboru aplikace pro spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="53996-120">You specify the path to an application `.dll` file to run the application.</span></span>  <span data-ttu-id="53996-121">Spuštění aplikace znamená najít a spustit vstupní bod, což je v `Main` případě konzolových aplikací metoda.</span><span class="sxs-lookup"><span data-stu-id="53996-121">To run the application means to find and execute the entry point, which in the case of console apps is the `Main` method.</span></span> <span data-ttu-id="53996-122">Například `dotnet myapp.dll` spustí `myapp` aplikaci.</span><span class="sxs-lookup"><span data-stu-id="53996-122">For example, `dotnet myapp.dll` runs the `myapp` application.</span></span> <span data-ttu-id="53996-123">Informace o možnostech nasazení najdete v tématu [Nasazení aplikace .NET Core.](../deploying/index.md)</span><span class="sxs-lookup"><span data-stu-id="53996-123">See [.NET Core application deployment](../deploying/index.md) to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="53996-124">Možnosti</span><span class="sxs-lookup"><span data-stu-id="53996-124">Options</span></span>

<span data-ttu-id="53996-125">Různé možnosti `dotnet` jsou k dispozici samostatně, pro spuštění příkazu a pro spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="53996-125">Different options are available for `dotnet` by itself, for running a command, and for running an application.</span></span>

### <a name="options-for-dotnet-by-itself"></a><span data-ttu-id="53996-126">Možnosti pro dotnet sám o sobě</span><span class="sxs-lookup"><span data-stu-id="53996-126">Options for dotnet by itself</span></span>

<span data-ttu-id="53996-127">Následující možnosti `dotnet` jsou samy o sobě.</span><span class="sxs-lookup"><span data-stu-id="53996-127">The following options are for `dotnet` by itself.</span></span> <span data-ttu-id="53996-128">Například, `dotnet --info`.</span><span class="sxs-lookup"><span data-stu-id="53996-128">For example, `dotnet --info`.</span></span> <span data-ttu-id="53996-129">Tisknou informace o životním prostředí.</span><span class="sxs-lookup"><span data-stu-id="53996-129">They print out information about the environment.</span></span>

- **`--info`**

  <span data-ttu-id="53996-130">Vytiskne podrobné informace o instalaci jádra .NET a prostředí počítače, jako je například aktuální operační systém, a potvrdí sha verze .NET Core.</span><span class="sxs-lookup"><span data-stu-id="53996-130">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

- **`--version`**

  <span data-ttu-id="53996-131">Vytiskne verzi sady .NET Core SDK, která se používá.</span><span class="sxs-lookup"><span data-stu-id="53996-131">Prints out the version of the .NET Core SDK in use.</span></span>

- **`--list-runtimes`**

  <span data-ttu-id="53996-132">Vytiskne seznam nainstalovaných runčasů jádra .NET.</span><span class="sxs-lookup"><span data-stu-id="53996-132">Prints out a list of the installed .NET Core runtimes.</span></span> <span data-ttu-id="53996-133">Verze sady X86 sady SDK obsahuje pouze za běhu x86 a verze sady SDK x64 uvádí pouze za běhu x64.</span><span class="sxs-lookup"><span data-stu-id="53996-133">An x86 version of the SDK lists only x86 runtimes, and an x64 version of the SDK lists only x64 runtimes.</span></span>

- **`--list-sdks`**

  <span data-ttu-id="53996-134">Vytiskne seznam nainstalovaných sad SDK jádra .NET.</span><span class="sxs-lookup"><span data-stu-id="53996-134">Prints out a list of the installed .NET Core SDKs.</span></span>

- **`-h|--help`**

  <span data-ttu-id="53996-135">Vytiskne seznam dostupných příkazů.</span><span class="sxs-lookup"><span data-stu-id="53996-135">Prints out a list of available commands.</span></span>

### <a name="sdk-options-for-running-a-command"></a><span data-ttu-id="53996-136">Možnosti sady SDK pro spuštění příkazu</span><span class="sxs-lookup"><span data-stu-id="53996-136">SDK options for running a command</span></span>

<span data-ttu-id="53996-137">Následující možnosti `dotnet` jsou pro s příkazem.</span><span class="sxs-lookup"><span data-stu-id="53996-137">The following options are for `dotnet` with a command.</span></span> <span data-ttu-id="53996-138">Například, `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="53996-138">For example, `dotnet build --help`.</span></span>

- **`-d|--diagnostics`**

  <span data-ttu-id="53996-139">Umožňuje diagnostický výstup.</span><span class="sxs-lookup"><span data-stu-id="53996-139">Enables diagnostic output.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="53996-140">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="53996-140">Sets the verbosity level of the command.</span></span> <span data-ttu-id="53996-141">Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a .</span><span class="sxs-lookup"><span data-stu-id="53996-141">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="53996-142">Není podporováno v každém příkazu.</span><span class="sxs-lookup"><span data-stu-id="53996-142">Not supported in every command.</span></span> <span data-ttu-id="53996-143">Chcete-li zjistit, zda je tato možnost k dispozici, podívejte se na konkrétní příkazovou stránku.</span><span class="sxs-lookup"><span data-stu-id="53996-143">See specific command page to determine if this option is available.</span></span>

- **`-h|--help`**

  <span data-ttu-id="53996-144">Vytiskne dokumentaci pro daný `dotnet build --help`příkaz, například .</span><span class="sxs-lookup"><span data-stu-id="53996-144">Prints out documentation for a given command, such as `dotnet build --help`.</span></span>

- **`command options`**

  <span data-ttu-id="53996-145">Každý příkaz definuje možnosti specifické pro tento příkaz.</span><span class="sxs-lookup"><span data-stu-id="53996-145">Each command defines options specific to that command.</span></span> <span data-ttu-id="53996-146">Seznam dostupných možností naleznete na konkrétní stránce příkazů.</span><span class="sxs-lookup"><span data-stu-id="53996-146">See specific command page for a list of available options.</span></span>

### <a name="runtime-options"></a><span data-ttu-id="53996-147">Možnosti běhu</span><span class="sxs-lookup"><span data-stu-id="53996-147">Runtime options</span></span>

<span data-ttu-id="53996-148">Následující možnosti jsou `dotnet` k dispozici při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="53996-148">The following options are available when `dotnet` runs an application.</span></span> <span data-ttu-id="53996-149">Například, `dotnet myapp.dll --fx-version 3.1.1`.</span><span class="sxs-lookup"><span data-stu-id="53996-149">For example, `dotnet myapp.dll --fx-version 3.1.1`.</span></span>

- **`--additionalprobingpath <PATH>`**

  <span data-ttu-id="53996-150">Cesta obsahující sondování zásady a sestavení pro sondu.</span><span class="sxs-lookup"><span data-stu-id="53996-150">Path containing probing policy and assemblies to probe.</span></span>

- **`--additional-deps <PATH>`**

  <span data-ttu-id="53996-151">Cesta k dalšímu souboru *.deps.json.*</span><span class="sxs-lookup"><span data-stu-id="53996-151">Path to an additional *.deps.json* file.</span></span> <span data-ttu-id="53996-152">Soubor *deps.json* obsahuje seznam závislostí, závislostí kompilace a informací o verzi, které se používají k řešení konfliktů sestavení.</span><span class="sxs-lookup"><span data-stu-id="53996-152">A *deps.json* file contains a list of dependencies, compilation dependencies, and version information used to address assembly conflicts.</span></span> <span data-ttu-id="53996-153">Další informace najdete [v tématu Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="53996-153">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

- **`--fx-version <VERSION>`**

  <span data-ttu-id="53996-154">Verze runtime .NET Core, která se má použít ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="53996-154">Version of the .NET Core runtime to use to run the application.</span></span>

- **`--runtimeconfig`**

  <span data-ttu-id="53996-155">Cesta k souboru *runtimeconfig.json.*</span><span class="sxs-lookup"><span data-stu-id="53996-155">Path to a *runtimeconfig.json* file.</span></span> <span data-ttu-id="53996-156">Soubor *runtimeconfig.json* je konfigurační soubor, který obsahuje nastavení běhu.</span><span class="sxs-lookup"><span data-stu-id="53996-156">A *runtimeconfig.json* file is a configuration file that contains run-time settings.</span></span> <span data-ttu-id="53996-157">Další informace naleznete v [tématu Nastavení konfigurace rozhraní .NET Core run-time](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="53996-157">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

- <span data-ttu-id="53996-158">**`--roll-forward-on-no-candidate-fx <N>`\*\*\*\*K dispozici v sdk .NET Core 2.x.**</span><span class="sxs-lookup"><span data-stu-id="53996-158">**`--roll-forward-on-no-candidate-fx <N>`** **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="53996-159">Definuje chování, když není k dispozici požadovaná sdílená architektura.</span><span class="sxs-lookup"><span data-stu-id="53996-159">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="53996-160">`N`může být:</span><span class="sxs-lookup"><span data-stu-id="53996-160">`N` can be:</span></span>

  - <span data-ttu-id="53996-161">`0`- Zakázat i menší verze roll vpřed.</span><span class="sxs-lookup"><span data-stu-id="53996-161">`0` - Disable even minor version roll forward.</span></span>
  - <span data-ttu-id="53996-162">`1`- Roll vpřed na dílčí verzi, ale ne na hlavní verzi.</span><span class="sxs-lookup"><span data-stu-id="53996-162">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="53996-163">Toto je výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="53996-163">This is the default behavior.</span></span>
  - <span data-ttu-id="53996-164">`2`- Roll vpřed na menší a hlavní verze.</span><span class="sxs-lookup"><span data-stu-id="53996-164">`2` - Roll forward on minor and major versions.</span></span>

   <span data-ttu-id="53996-165">Další informace naleznete v [tématu Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="53996-165">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

- <span data-ttu-id="53996-166">**`--roll-forward <SETTING>`\*\*\*\*K dispozici počínaje sadou .NET Core SDK 3.0.**</span><span class="sxs-lookup"><span data-stu-id="53996-166">**`--roll-forward <SETTING>`** **Available starting with .NET Core SDK 3.0.**</span></span>

  <span data-ttu-id="53996-167">Určuje, jak se v aplikaci použije posun vpřed.</span><span class="sxs-lookup"><span data-stu-id="53996-167">Controls how roll forward is applied to the app.</span></span> <span data-ttu-id="53996-168">Může `SETTING` být jedna z následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="53996-168">The `SETTING` can be one of the following values.</span></span> <span data-ttu-id="53996-169">Pokud není `Minor` zadán, je výchozí.</span><span class="sxs-lookup"><span data-stu-id="53996-169">If not specified, `Minor` is the default.</span></span>

  - <span data-ttu-id="53996-170">`LatestPatch`- Přetočte se dopředu na nejvyšší verzi opravy.</span><span class="sxs-lookup"><span data-stu-id="53996-170">`LatestPatch` - Roll forward to the highest patch version.</span></span> <span data-ttu-id="53996-171">Tím se zakáže dílčí verze posunout vpřed.</span><span class="sxs-lookup"><span data-stu-id="53996-171">This disables minor version roll forward.</span></span>
  - <span data-ttu-id="53996-172">`Minor`- Převrátit na nejnižší vyšší dílčí verze, pokud je požadována dílčí verze chybí.</span><span class="sxs-lookup"><span data-stu-id="53996-172">`Minor` - Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="53996-173">Pokud je k dispozici požadovaná dílčí verze, použije se zásada LatestPatch.</span><span class="sxs-lookup"><span data-stu-id="53996-173">If the requested minor version is present, then the LatestPatch policy is used.</span></span>
  - <span data-ttu-id="53996-174">`Major`- Roll vpřed na nejnižší vyšší hlavní verze, a nejnižší dílčí verze, pokud požadované hlavní verze chybí.</span><span class="sxs-lookup"><span data-stu-id="53996-174">`Major` - Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="53996-175">Pokud je k dispozici požadovaná hlavní verze, použije se zásada Vedlejší.</span><span class="sxs-lookup"><span data-stu-id="53996-175">If the requested major version is present, then the Minor policy is used.</span></span>
  - <span data-ttu-id="53996-176">`LatestMinor`- Převrátit na nejvyšší dílčí verzi, a to i v případě, že je požadována dílčí verze je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="53996-176">`LatestMinor` - Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="53996-177">Určeno pro scénáře hostování komponent.</span><span class="sxs-lookup"><span data-stu-id="53996-177">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="53996-178">`LatestMajor`- Převrátit na nejvyšší hlavní a nejvyšší dílčí verze, i když požadované hlavní je přítomen.</span><span class="sxs-lookup"><span data-stu-id="53996-178">`LatestMajor` - Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="53996-179">Určeno pro scénáře hostování komponent.</span><span class="sxs-lookup"><span data-stu-id="53996-179">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="53996-180">`Disable`- Neotáčejte se dopředu.</span><span class="sxs-lookup"><span data-stu-id="53996-180">`Disable` - Don't roll forward.</span></span> <span data-ttu-id="53996-181">Spojte se pouze se zadanou verzí.</span><span class="sxs-lookup"><span data-stu-id="53996-181">Only bind to specified version.</span></span> <span data-ttu-id="53996-182">Tato zásada se nedoporučuje pro obecné použití, protože zakáže možnost převést na nejnovější opravy.</span><span class="sxs-lookup"><span data-stu-id="53996-182">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="53996-183">Tato hodnota je doporučena pouze pro testování.</span><span class="sxs-lookup"><span data-stu-id="53996-183">This value is only recommended for testing.</span></span>

<span data-ttu-id="53996-184">S výjimkou `Disable`aplikace budou všechna nastavení používat nejvyšší dostupnou verzi opravy.</span><span class="sxs-lookup"><span data-stu-id="53996-184">With the exception of `Disable`, all settings will use the highest available patch version.</span></span>

<span data-ttu-id="53996-185">Chování posunout vpřed lze také nakonfigurovat ve vlastnosti souboru projektu, vlastnosti konfiguračního souboru za běhu a proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="53996-185">Roll forward behavior can also be configured in a project file property, a run-time configuration file property, and an environment variable.</span></span> <span data-ttu-id="53996-186">Další informace naleznete v [tématu Hlavní verze runtime posun vpřed](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span><span class="sxs-lookup"><span data-stu-id="53996-186">For more information, see [Major-version runtime roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span></span>

## <a name="dotnet-commands"></a><span data-ttu-id="53996-187">Příkazy dotnet</span><span class="sxs-lookup"><span data-stu-id="53996-187">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="53996-188">Obecné</span><span class="sxs-lookup"><span data-stu-id="53996-188">General</span></span>

| <span data-ttu-id="53996-189">Příkaz</span><span class="sxs-lookup"><span data-stu-id="53996-189">Command</span></span>                                       | <span data-ttu-id="53996-190">Funkce</span><span class="sxs-lookup"><span data-stu-id="53996-190">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="53996-191">dotnet build</span><span class="sxs-lookup"><span data-stu-id="53996-191">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="53996-192">Vytvoří aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="53996-192">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="53996-193">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="53996-193">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="53996-194">Spolupracuje se servery spuštěnými sestavením.</span><span class="sxs-lookup"><span data-stu-id="53996-194">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="53996-195">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="53996-195">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="53996-196">Čisté výstupy sestavení.</span><span class="sxs-lookup"><span data-stu-id="53996-196">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="53996-197">dotnet help</span><span class="sxs-lookup"><span data-stu-id="53996-197">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="53996-198">Zobrazuje podrobnější dokumentaci online pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="53996-198">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="53996-199">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="53996-199">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="53996-200">Přenese platný projekt Preview 2 do projektu .NET Core SDK 1.0.</span><span class="sxs-lookup"><span data-stu-id="53996-200">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="53996-201">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="53996-201">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="53996-202">Poskytuje přístup k příkazovému řádku MSBuild.</span><span class="sxs-lookup"><span data-stu-id="53996-202">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="53996-203">dotnet new</span><span class="sxs-lookup"><span data-stu-id="53996-203">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="53996-204">Inicializuje projekt C# nebo F# pro danou šablonu.</span><span class="sxs-lookup"><span data-stu-id="53996-204">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="53996-205">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="53996-205">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="53996-206">Vytvoří balíček NuGet vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="53996-206">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="53996-207">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="53996-207">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="53996-208">Publikuje aplikaci závislou na rozhraní .NET nebo samostatnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="53996-208">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="53996-209">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="53996-209">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="53996-210">Obnoví závislosti pro danou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="53996-210">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="53996-211">dotnet run</span><span class="sxs-lookup"><span data-stu-id="53996-211">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="53996-212">Spustí aplikaci ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="53996-212">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="53996-213">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="53996-213">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="53996-214">Možnosti pro přidání, odebrání a seznam projektů v souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="53996-214">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="53996-215">dotnet store</span><span class="sxs-lookup"><span data-stu-id="53996-215">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="53996-216">Ukládá sestavení v runtime balíček úložiště.</span><span class="sxs-lookup"><span data-stu-id="53996-216">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="53996-217">dotnet test</span><span class="sxs-lookup"><span data-stu-id="53996-217">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="53996-218">Spustí testy pomocí testovacího běhu.</span><span class="sxs-lookup"><span data-stu-id="53996-218">Runs tests using a test runner.</span></span>                                     |

### <a name="project-references"></a><span data-ttu-id="53996-219">Odkazy na projekty</span><span class="sxs-lookup"><span data-stu-id="53996-219">Project references</span></span>

<span data-ttu-id="53996-220">Příkaz</span><span class="sxs-lookup"><span data-stu-id="53996-220">Command</span></span> | <span data-ttu-id="53996-221">Funkce</span><span class="sxs-lookup"><span data-stu-id="53996-221">Function</span></span>
--- | ---
[<span data-ttu-id="53996-222">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="53996-222">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="53996-223">Přidá odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="53996-223">Adds a project reference.</span></span>
[<span data-ttu-id="53996-224">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="53996-224">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="53996-225">Zobrazí seznam odkazů na projekt.</span><span class="sxs-lookup"><span data-stu-id="53996-225">Lists project references.</span></span>
[<span data-ttu-id="53996-226">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="53996-226">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="53996-227">Odebere odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="53996-227">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="53996-228">Balíčky NuGet</span><span class="sxs-lookup"><span data-stu-id="53996-228">NuGet packages</span></span>

<span data-ttu-id="53996-229">Příkaz</span><span class="sxs-lookup"><span data-stu-id="53996-229">Command</span></span> | <span data-ttu-id="53996-230">Funkce</span><span class="sxs-lookup"><span data-stu-id="53996-230">Function</span></span>
--- | ---
[<span data-ttu-id="53996-231">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="53996-231">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="53996-232">Přidá balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="53996-232">Adds a NuGet package.</span></span>
[<span data-ttu-id="53996-233">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="53996-233">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="53996-234">Odebere balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="53996-234">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="53996-235">Příkazy NuGet</span><span class="sxs-lookup"><span data-stu-id="53996-235">NuGet commands</span></span>

<span data-ttu-id="53996-236">Příkaz</span><span class="sxs-lookup"><span data-stu-id="53996-236">Command</span></span> | <span data-ttu-id="53996-237">Funkce</span><span class="sxs-lookup"><span data-stu-id="53996-237">Function</span></span>
--- | ---
[<span data-ttu-id="53996-238">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="53996-238">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="53996-239">Odstraní nebo odřadí seznam balíčku ze serveru.</span><span class="sxs-lookup"><span data-stu-id="53996-239">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="53996-240">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="53996-240">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="53996-241">Odešle balíček na server a publikuje jej.</span><span class="sxs-lookup"><span data-stu-id="53996-241">Pushes a package to the server and publishes it.</span></span>
[<span data-ttu-id="53996-242">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="53996-242">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="53996-243">Vymaže nebo zobrazí seznam místních prostředků NuGet, jako je například mezipaměť http-request, dočasná mezipaměť nebo globální balíček pro celý počítač.</span><span class="sxs-lookup"><span data-stu-id="53996-243">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="53996-244">dotnet nuget add source</span><span class="sxs-lookup"><span data-stu-id="53996-244">dotnet nuget add source</span></span>](dotnet-nuget-add-source.md) | <span data-ttu-id="53996-245">Přidá zdroj NuGet.</span><span class="sxs-lookup"><span data-stu-id="53996-245">Adds a NuGet source.</span></span>
[<span data-ttu-id="53996-246">dotnet nuget disable source</span><span class="sxs-lookup"><span data-stu-id="53996-246">dotnet nuget disable source</span></span>](dotnet-nuget-disable-source.md) | <span data-ttu-id="53996-247">Zakáže zdroj NuGet.</span><span class="sxs-lookup"><span data-stu-id="53996-247">Disables a NuGet source.</span></span>
[<span data-ttu-id="53996-248">dotnet nuget enable source</span><span class="sxs-lookup"><span data-stu-id="53996-248">dotnet nuget enable source</span></span>](dotnet-nuget-enable-source.md) | <span data-ttu-id="53996-249">Povolí zdroj NuGet.</span><span class="sxs-lookup"><span data-stu-id="53996-249">Enables a NuGet source.</span></span>
[<span data-ttu-id="53996-250">dotnet nuget list source</span><span class="sxs-lookup"><span data-stu-id="53996-250">dotnet nuget list source</span></span>](dotnet-nuget-list-source.md) | <span data-ttu-id="53996-251">Zobrazí seznam všech nakonfigurovaných zdrojů NuGet.</span><span class="sxs-lookup"><span data-stu-id="53996-251">Lists all configured NuGet sources.</span></span>
[<span data-ttu-id="53996-252">dotnet nuget remove source</span><span class="sxs-lookup"><span data-stu-id="53996-252">dotnet nuget remove source</span></span>](dotnet-nuget-remove-source.md) | <span data-ttu-id="53996-253">Odebere zdroj NuGet.</span><span class="sxs-lookup"><span data-stu-id="53996-253">Removes a NuGet source.</span></span>
[<span data-ttu-id="53996-254">dotnet nuget update source</span><span class="sxs-lookup"><span data-stu-id="53996-254">dotnet nuget update source</span></span>](dotnet-nuget-update-source.md) | <span data-ttu-id="53996-255">Aktualizuje zdroj NuGet.</span><span class="sxs-lookup"><span data-stu-id="53996-255">Updates a NuGet source.</span></span>

### <a name="global-tool-path-and-local-tools-commands"></a><span data-ttu-id="53996-256">Příkazy globálních nástrojů, cest nástrojů a místních nástrojů</span><span class="sxs-lookup"><span data-stu-id="53996-256">Global, tool-path, and local tools commands</span></span>

<span data-ttu-id="53996-257">Nástroje jsou konzolové aplikace, které jsou nainstalovány z balíčků NuGet a jsou vyvolány z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="53996-257">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="53996-258">Můžete psát nástroje sami nebo instalovat nástroje napsané třetími stranami.</span><span class="sxs-lookup"><span data-stu-id="53996-258">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="53996-259">Nástroje jsou také známé jako globální nástroje, nástroje pro cestu nástrojů a místní nástroje.</span><span class="sxs-lookup"><span data-stu-id="53996-259">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="53996-260">Další informace naleznete v tématu [Přehled nástrojů .NET Core](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="53996-260">For more information, see [.NET Core tools overview](global-tools.md).</span></span> <span data-ttu-id="53996-261">Globální nástroje a nástroje cesta jsou k dispozici počínaje .NET Core SDK 2.1.</span><span class="sxs-lookup"><span data-stu-id="53996-261">Global and tool-path tools are available starting with .NET Core SDK 2.1.</span></span> <span data-ttu-id="53996-262">Místní nástroje jsou k dispozici počínaje .NET Core SDK 3.0.</span><span class="sxs-lookup"><span data-stu-id="53996-262">Local tools are available starting with .NET Core SDK 3.0.</span></span>

<span data-ttu-id="53996-263">Příkaz</span><span class="sxs-lookup"><span data-stu-id="53996-263">Command</span></span> | <span data-ttu-id="53996-264">Funkce</span><span class="sxs-lookup"><span data-stu-id="53996-264">Function</span></span>
--- | ---
[<span data-ttu-id="53996-265">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="53996-265">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="53996-266">Nainstaluje do počítače nástroj.</span><span class="sxs-lookup"><span data-stu-id="53996-266">Installs a tool on your machine.</span></span>
[<span data-ttu-id="53996-267">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="53996-267">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="53996-268">Zobrazí seznam všech globálních, nástrojových cest nebo místních nástrojů, které jsou v počítači aktuálně nainstalovány.</span><span class="sxs-lookup"><span data-stu-id="53996-268">Lists all global, tool-path, or local tools currently installed on your machine.</span></span>
[<span data-ttu-id="53996-269">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="53996-269">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="53996-270">Odinstaluje nástroj ze zařízení.</span><span class="sxs-lookup"><span data-stu-id="53996-270">Uninstalls a tool from your machine.</span></span>
[<span data-ttu-id="53996-271">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="53996-271">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="53996-272">Aktualizuje nástroj, který je nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="53996-272">Updates a tool that is installed on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="53996-273">Další nástroje</span><span class="sxs-lookup"><span data-stu-id="53996-273">Additional tools</span></span>

<span data-ttu-id="53996-274">Počínaje .NET Core SDK 2.1.300, počet nástrojů, které byly k `DotnetCliToolReference` dispozici pouze na základě projektu pomocí jsou nyní k dispozici jako součást .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="53996-274">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="53996-275">Tyto nástroje jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="53996-275">These tools are listed in the following table:</span></span>

| <span data-ttu-id="53996-276">Nástroj</span><span class="sxs-lookup"><span data-stu-id="53996-276">Tool</span></span>                                              | <span data-ttu-id="53996-277">Funkce</span><span class="sxs-lookup"><span data-stu-id="53996-277">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="53996-278">dev-certs</span><span class="sxs-lookup"><span data-stu-id="53996-278">dev-certs</span></span>                                         | <span data-ttu-id="53996-279">Vytváří a spravuje vývojové certifikáty.</span><span class="sxs-lookup"><span data-stu-id="53996-279">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="53996-280">Ef</span><span class="sxs-lookup"><span data-stu-id="53996-280">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="53996-281">Nástroje příkazového řádku Core entity Framework.</span><span class="sxs-lookup"><span data-stu-id="53996-281">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="53996-282">sql-cache</span><span class="sxs-lookup"><span data-stu-id="53996-282">sql-cache</span></span>                                         | <span data-ttu-id="53996-283">Nástroje příkazového řádku mezipaměti serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="53996-283">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="53996-284">uživatelské tajemství</span><span class="sxs-lookup"><span data-stu-id="53996-284">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="53996-285">Spravuje tajné kódy uživatelů vývoje.</span><span class="sxs-lookup"><span data-stu-id="53996-285">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="53996-286">Sledovat</span><span class="sxs-lookup"><span data-stu-id="53996-286">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="53996-287">Spustí sledovací proces souboru, který spustí příkaz při změně souborů.</span><span class="sxs-lookup"><span data-stu-id="53996-287">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="53996-288">Další informace o jednotlivých `dotnet <tool-name> --help`nástrojích získáte zadáním příkazu .</span><span class="sxs-lookup"><span data-stu-id="53996-288">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="53996-289">Příklady</span><span class="sxs-lookup"><span data-stu-id="53996-289">Examples</span></span>

<span data-ttu-id="53996-290">Vytvořte novou aplikaci konzoly .NET Core:</span><span class="sxs-lookup"><span data-stu-id="53996-290">Create a new .NET Core console application:</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="53996-291">Sestavení projektu a jeho závislostí v daném adresáři:</span><span class="sxs-lookup"><span data-stu-id="53996-291">Build a project and its dependencies in a given directory:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="53996-292">Spuštění aplikace:</span><span class="sxs-lookup"><span data-stu-id="53996-292">Run an application:</span></span>

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a><span data-ttu-id="53996-293">Proměnné prostředí</span><span class="sxs-lookup"><span data-stu-id="53996-293">Environment variables</span></span>

- <span data-ttu-id="53996-294">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span><span class="sxs-lookup"><span data-stu-id="53996-294">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span></span>

  <span data-ttu-id="53996-295">Určuje umístění runčasů jádra .NET, pokud nejsou nainstalovány ve výchozím umístění.</span><span class="sxs-lookup"><span data-stu-id="53996-295">Specifies the location of the .NET Core runtimes, if they are not installed in the default location.</span></span> <span data-ttu-id="53996-296">Výchozí umístění v `C:\Program Files\dotnet`systému Windows je .</span><span class="sxs-lookup"><span data-stu-id="53996-296">The default location on Windows is `C:\Program Files\dotnet`.</span></span> <span data-ttu-id="53996-297">Výchozí umístění na Linuxu a `/usr/share/dotnet`macOS je .</span><span class="sxs-lookup"><span data-stu-id="53996-297">The default location on Linux and macOS is `/usr/share/dotnet`.</span></span> <span data-ttu-id="53996-298">Tato proměnná prostředí se používá pouze při spouštění aplikací prostřednictvím generovaných spustitelných souborů (apphosts).</span><span class="sxs-lookup"><span data-stu-id="53996-298">This environment variable is used only when running apps via generated executables (apphosts).</span></span> <span data-ttu-id="53996-299">`DOTNET_ROOT(x86)`se používá místo toho při spuštění 32bitového spustitelného souboru v 64bitovém osu.</span><span class="sxs-lookup"><span data-stu-id="53996-299">`DOTNET_ROOT(x86)` is used instead when running a 32-bit executable on a 64-bit OS.</span></span>

- `DOTNET_PACKAGES`

  <span data-ttu-id="53996-300">Složka globálních balíčků.</span><span class="sxs-lookup"><span data-stu-id="53996-300">The global packages folder.</span></span> <span data-ttu-id="53996-301">Pokud není nastavena, `~/.nuget/packages` je výchozí `%userprofile%\.nuget\packages` na Unix nebo na Windows.</span><span class="sxs-lookup"><span data-stu-id="53996-301">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

- `DOTNET_SERVICING`

  <span data-ttu-id="53996-302">Určuje umístění indexu obsluhy, který má sdílený hostitel použít při načítání za běhu.</span><span class="sxs-lookup"><span data-stu-id="53996-302">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

- `DOTNET_NOLOGO`

  <span data-ttu-id="53996-303">Určuje, zda se při prvním spuštění zobrazí uvítání a telemetrické zprávy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="53996-303">Specifies whether .NET Core welcome and telemetry messages are displayed on first run.</span></span> <span data-ttu-id="53996-304">Nastaví `true` ztlumení těchto zpráv `true` `1`(hodnoty `yes` , nebo `false` přijaté) nebo `false` `0`na `no` povolit (hodnoty , nebo přijaté).</span><span class="sxs-lookup"><span data-stu-id="53996-304">Set to `true` to mute these messages (values `true`, `1`, or `yes` accepted) or set to `false` to allow (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="53996-305">Pokud není nastavena, `false` výchozí je a zprávy se zobrazí při prvním spuštění.</span><span class="sxs-lookup"><span data-stu-id="53996-305">If not set, the default is `false` and the messages will be displayed on first run.</span></span> <span data-ttu-id="53996-306">Tento příznak nemá žádný vliv `DOTNET_CLI_TELEMETRY_OPTOUT` na telemetrii (viz pro odhlášení odesílání telemetrie).</span><span class="sxs-lookup"><span data-stu-id="53996-306">This flag has no effect on telemetry (see `DOTNET_CLI_TELEMETRY_OPTOUT` for opting out of sending telemetry).</span></span>

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  <span data-ttu-id="53996-307">Určuje, zda jsou data o použití nástrojů .NET Core shromažďována a odesílána společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="53996-307">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="53996-308">Nastavte `true` na odhlášení z funkce telemetrie (hodnoty `true`, `1`nebo `yes` přijaté).</span><span class="sxs-lookup"><span data-stu-id="53996-308">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="53996-309">V opačném `false` případě nastavte na opt-li `false` `0`do `no` funkce telemetrie (hodnoty , nebo přijat).</span><span class="sxs-lookup"><span data-stu-id="53996-309">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="53996-310">Pokud není nastavena, `false` výchozí je a funkce telemetrie je aktivní.</span><span class="sxs-lookup"><span data-stu-id="53996-310">If not set, the default is `false` and the telemetry feature is active.</span></span>

- `DOTNET_MULTILEVEL_LOOKUP`

  <span data-ttu-id="53996-311">Určuje, zda jsou z globálního umístění vyřešeny zaběhu .NET Core, sdílené ho frameworku nebo sdk.</span><span class="sxs-lookup"><span data-stu-id="53996-311">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="53996-312">Pokud není nastavena, je výchozí `true`hodnota 1 (logické).</span><span class="sxs-lookup"><span data-stu-id="53996-312">If not set, it defaults to 1 (logical `true`).</span></span> <span data-ttu-id="53996-313">Nastavte 0 (logické) `false`není vyřešit z globálního umístění a mají izolované instalace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="53996-313">Set to 0 (logical `false`) to not resolve from the global location and have isolated .NET Core installations.</span></span> <span data-ttu-id="53996-314">Další informace o víceúrovňovém vyhledávání naleznete v [tématu Vyhledávání SharedFX na více úrovních](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="53996-314">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

- <span data-ttu-id="53996-315">`DOTNET_ROLL_FORWARD`**K dispozici počínaje sadou .NET Core 3.x SDK.**</span><span class="sxs-lookup"><span data-stu-id="53996-315">`DOTNET_ROLL_FORWARD` **Available starting with .NET Core 3.x SDK.**</span></span>

  <span data-ttu-id="53996-316">Určuje chování posunout vpřed.</span><span class="sxs-lookup"><span data-stu-id="53996-316">Determines roll forward behavior.</span></span> <span data-ttu-id="53996-317">Další informace naleznete `--roll-forward` v této možnosti dříve v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="53996-317">For more information, see the `--roll-forward` option earlier in this article.</span></span>

- <span data-ttu-id="53996-318">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`**K dispozici v sdk .NET Core 2.x.**</span><span class="sxs-lookup"><span data-stu-id="53996-318">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="53996-319">Zakáže dílčí verze posunout `0`vpřed, pokud je nastavena na .</span><span class="sxs-lookup"><span data-stu-id="53996-319">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="53996-320">Další informace naleznete v [tématu Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="53996-320">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

- `DOTNET_CLI_UI_LANGUAGE`

  <span data-ttu-id="53996-321">Nastaví jazyk rozhraní rozhraní rozhraní SEkatelu `en-us`pomocí hodnoty národního prostředí, například .</span><span class="sxs-lookup"><span data-stu-id="53996-321">Sets the language of the CLI UI using a locale value such as `en-us`.</span></span> <span data-ttu-id="53996-322">Podporované hodnoty jsou stejné jako pro Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="53996-322">The supported values are the same as for Visual Studio.</span></span> <span data-ttu-id="53996-323">Další informace naleznete v části o změně jazyka instalačního programu v [dokumentaci k instalaci sady Visual Studio](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019).</span><span class="sxs-lookup"><span data-stu-id="53996-323">For more information, see the section on changing the installer language in the [Visual Studio installation documentation](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019).</span></span> <span data-ttu-id="53996-324">Platí pravidla správce prostředků .NET, takže nemusíte vybírat přesnou shodu,&mdash; `CultureInfo` můžete také vybrat potomky ve stromu.</span><span class="sxs-lookup"><span data-stu-id="53996-324">The .NET resource manager rules apply, so you don't have to pick an exact match&mdash;you can also pick descendants in the `CultureInfo` tree.</span></span> <span data-ttu-id="53996-325">Pokud ji například nastavíte na `fr-CA`, vykázané nastavení matné a konstatování překlady vyhledá a použije. `fr`</span><span class="sxs-lookup"><span data-stu-id="53996-325">For example, if you set it to `fr-CA`, the CLI will find and use the `fr` translations.</span></span> <span data-ttu-id="53996-326">Pokud jej nastavíte na jazyk, který není podporován, rozhraní se konkretním rozhraním SE vrátí zpět do angličtiny.</span><span class="sxs-lookup"><span data-stu-id="53996-326">If you set it to a language that is not supported, the CLI falls back to English.</span></span>

- `DOTNET_DISABLE_GUI_ERRORS`

  <span data-ttu-id="53996-327">Pro gui-umožnil generované spustitelné soubory - zakáže dialogové okno, které obvykle ukazuje pro určité třídy chyb.</span><span class="sxs-lookup"><span data-stu-id="53996-327">For GUI-enabled generated executables - disables dialog popup, which normally shows for certain classes of errors.</span></span> <span data-ttu-id="53996-328">Pouze zapisuje `stderr` a ukončí v těchto případech.</span><span class="sxs-lookup"><span data-stu-id="53996-328">It only writes to `stderr` and exits in those cases.</span></span>
  
- `DOTNET_ADDITIONAL_DEPS`

  <span data-ttu-id="53996-329">Ekvivalentní možnost ipříkazové konzace `--additional-deps`.</span><span class="sxs-lookup"><span data-stu-id="53996-329">Equivalent to CLI option `--additional-deps`.</span></span>

- `DOTNET_RUNTIME_ID`

  <span data-ttu-id="53996-330">Přepíše zjištěný rid.</span><span class="sxs-lookup"><span data-stu-id="53996-330">Overrides the detected RID.</span></span>

- `DOTNET_SHARED_STORE`

  <span data-ttu-id="53996-331">Umístění "sdílenéúložiště", které rozlišení sestavení spadá zpět do v některých případech.</span><span class="sxs-lookup"><span data-stu-id="53996-331">Location of the "shared store" which assembly resolution falls back to in some cases.</span></span>

- `DOTNET_STARTUP_HOOKS`

  <span data-ttu-id="53996-332">Seznam sestavení pro načtení a spuštění spouštěcích háků z.</span><span class="sxs-lookup"><span data-stu-id="53996-332">List of assemblies to load and execute startup hooks from.</span></span>

- <span data-ttu-id="53996-333">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span><span class="sxs-lookup"><span data-stu-id="53996-333">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span></span>

  <span data-ttu-id="53996-334">Řídí diagnostiku trasování z hostitelských `dotnet.exe`součástí, například , `hostfxr`a `hostpolicy`.</span><span class="sxs-lookup"><span data-stu-id="53996-334">Controls diagnostics tracing from the hosting components, such as `dotnet.exe`, `hostfxr`, and `hostpolicy`.</span></span>

## <a name="see-also"></a><span data-ttu-id="53996-335">Viz také</span><span class="sxs-lookup"><span data-stu-id="53996-335">See also</span></span>

- [<span data-ttu-id="53996-336">Konfigurační soubory runtime</span><span class="sxs-lookup"><span data-stu-id="53996-336">Runtime Configuration Files</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [<span data-ttu-id="53996-337">Nastavení konfigurace jádra .NET</span><span class="sxs-lookup"><span data-stu-id="53996-337">.NET Core run-time configuration settings</span></span>](../run-time-config/index.md)
