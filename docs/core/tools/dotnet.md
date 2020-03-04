---
title: dotnet – příkaz
description: Přečtěte si o příkazu dotnet (obecný ovladač pro .NET Core CLI) a jeho použití.
ms.date: 02/13/2020
ms.openlocfilehash: da37c5cc3b019851e245fa3f65ae9dfb8a3fef54
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240867"
---
# <a name="dotnet-command"></a><span data-ttu-id="3039b-103">dotnet – příkaz</span><span class="sxs-lookup"><span data-stu-id="3039b-103">dotnet command</span></span>

<span data-ttu-id="3039b-104">**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="3039b-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="3039b-105">Název</span><span class="sxs-lookup"><span data-stu-id="3039b-105">Name</span></span>

<span data-ttu-id="3039b-106">`dotnet` – obecný ovladač pro .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="3039b-106">`dotnet` - The generic driver for the .NET Core CLI.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3039b-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="3039b-107">Synopsis</span></span>

<span data-ttu-id="3039b-108">Chcete-li získat informace o dostupných příkazech a prostředí:</span><span class="sxs-lookup"><span data-stu-id="3039b-108">To get information about the available commands and the environment:</span></span>

```dotnetcli
dotnet [-h|--help] [--version] [--info]
    [--list-runtimes] [--list-sdks]
```

<span data-ttu-id="3039b-109">Spuštění příkazu (vyžaduje instalaci sady SDK):</span><span class="sxs-lookup"><span data-stu-id="3039b-109">To run a command (requires SDK installation):</span></span>

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity]
    [command-options] [arguments]
```

<span data-ttu-id="3039b-110">Spuštění aplikace:</span><span class="sxs-lookup"><span data-stu-id="3039b-110">To run an application:</span></span>

```dotnetcli
dotnet [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]
```

<span data-ttu-id="3039b-111">`--roll-forward` je k dispozici od verze .NET Core 3. x.</span><span class="sxs-lookup"><span data-stu-id="3039b-111">`--roll-forward` is available since .NET Core 3.x.</span></span> <span data-ttu-id="3039b-112">Použijte `--roll-forward-on-no-candidate-fx` pro .NET Core 2. x.</span><span class="sxs-lookup"><span data-stu-id="3039b-112">Use `--roll-forward-on-no-candidate-fx` for .NET Core 2.x.</span></span>

## <a name="description"></a><span data-ttu-id="3039b-113">Popis</span><span class="sxs-lookup"><span data-stu-id="3039b-113">Description</span></span>

<span data-ttu-id="3039b-114">Příkaz `dotnet` má dvě funkce:</span><span class="sxs-lookup"><span data-stu-id="3039b-114">The `dotnet` command has two functions:</span></span>

- <span data-ttu-id="3039b-115">Poskytuje příkazy pro práci s projekty .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3039b-115">It provides commands for working with .NET Core projects.</span></span>

  <span data-ttu-id="3039b-116">Například [`dotnet build`](dotnet-build.md) sestavit projekt.</span><span class="sxs-lookup"><span data-stu-id="3039b-116">For example, [`dotnet build`](dotnet-build.md) builds a project.</span></span> <span data-ttu-id="3039b-117">Každý příkaz definuje vlastní parametry a argumenty.</span><span class="sxs-lookup"><span data-stu-id="3039b-117">Each command defines its own options and arguments.</span></span> <span data-ttu-id="3039b-118">Všechny příkazy podporují možnost `--help` pro tisk stručné dokumentace k použití příkazu.</span><span class="sxs-lookup"><span data-stu-id="3039b-118">All commands support the `--help` option for printing out brief documentation about how to use the command.</span></span>

- <span data-ttu-id="3039b-119">Spouští aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3039b-119">It runs .NET Core applications.</span></span>

  <span data-ttu-id="3039b-120">Zadejte cestu k souboru aplikace `.dll` pro spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="3039b-120">You specify the path to an application `.dll` file to run the application.</span></span> <span data-ttu-id="3039b-121">Například `dotnet myapp.dll` spouští aplikaci `myapp`.</span><span class="sxs-lookup"><span data-stu-id="3039b-121">For example, `dotnet myapp.dll` runs the `myapp` application.</span></span> <span data-ttu-id="3039b-122">Další informace o možnostech nasazení najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md) .</span><span class="sxs-lookup"><span data-stu-id="3039b-122">See [.NET Core application deployment](../deploying/index.md) to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="3039b-123">Možnosti</span><span class="sxs-lookup"><span data-stu-id="3039b-123">Options</span></span>

<span data-ttu-id="3039b-124">K dispozici jsou různé možnosti `dotnet` samostatně, pro spuštění příkazu a pro spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="3039b-124">Different options are available for `dotnet` by itself, for running a command, and for running an application.</span></span>

### <a name="options-for-dotnet-by-itself"></a><span data-ttu-id="3039b-125">Možnosti pro dotnet samotné</span><span class="sxs-lookup"><span data-stu-id="3039b-125">Options for dotnet by itself</span></span>

<span data-ttu-id="3039b-126">Následující možnosti jsou `dotnet` samotné.</span><span class="sxs-lookup"><span data-stu-id="3039b-126">The following options are for `dotnet` by itself.</span></span> <span data-ttu-id="3039b-127">například `dotnet --info`.</span><span class="sxs-lookup"><span data-stu-id="3039b-127">For example, `dotnet --info`.</span></span> <span data-ttu-id="3039b-128">Tisknou informace o daném prostředí.</span><span class="sxs-lookup"><span data-stu-id="3039b-128">They print out information about the environment.</span></span>

- **`--info`**

  <span data-ttu-id="3039b-129">Vytiskne podrobné informace o instalaci .NET Core a počítačovém prostředí, jako je aktuální operační systém, a potvrzení SHA verze .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3039b-129">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

- **`--version`**

  <span data-ttu-id="3039b-130">Vytiskne verzi .NET Core SDK, která se používá.</span><span class="sxs-lookup"><span data-stu-id="3039b-130">Prints out the version of the .NET Core SDK in use.</span></span>

- **`--list-runtimes`**

  <span data-ttu-id="3039b-131">Vytiskne seznam nainstalovaných modulů runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3039b-131">Prints out a list of the installed .NET Core runtimes.</span></span>

- **`--list-sdks`**

  <span data-ttu-id="3039b-132">Vytiskne seznam nainstalovaných sad SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3039b-132">Prints out a list of the installed .NET Core SDKs.</span></span>

- **`-h|--help`**

  <span data-ttu-id="3039b-133">Vytiskne seznam dostupných příkazů.</span><span class="sxs-lookup"><span data-stu-id="3039b-133">Prints out a list of available commands.</span></span>

### <a name="sdk-options-for-running-a-command"></a><span data-ttu-id="3039b-134">Možnosti sady SDK pro spuštění příkazu</span><span class="sxs-lookup"><span data-stu-id="3039b-134">SDK options for running a command</span></span>

<span data-ttu-id="3039b-135">Následující možnosti jsou pro `dotnet` s příkazem.</span><span class="sxs-lookup"><span data-stu-id="3039b-135">The following options are for `dotnet` with a command.</span></span> <span data-ttu-id="3039b-136">například `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="3039b-136">For example, `dotnet build --help`.</span></span>

- **`-d|--diagnostics`**

  <span data-ttu-id="3039b-137">Povolí výstup diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="3039b-137">Enables diagnostic output.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="3039b-138">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="3039b-138">Sets the verbosity level of the command.</span></span> <span data-ttu-id="3039b-139">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="3039b-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="3039b-140">Nepodporováno v každém příkazu.</span><span class="sxs-lookup"><span data-stu-id="3039b-140">Not supported in every command.</span></span> <span data-ttu-id="3039b-141">Pokud chcete zjistit, zda je tato možnost k dispozici, zobrazte konkrétní příkazová stránka.</span><span class="sxs-lookup"><span data-stu-id="3039b-141">See specific command page to determine if this option is available.</span></span>

- **`-h|--help`**

  <span data-ttu-id="3039b-142">Vytiskne dokumentaci pro daný příkaz, například `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="3039b-142">Prints out documentation for a given command, such as `dotnet build --help`.</span></span>

- **`command options`**

  <span data-ttu-id="3039b-143">Každý příkaz definuje možnosti specifické pro tento příkaz.</span><span class="sxs-lookup"><span data-stu-id="3039b-143">Each command defines options specific to that command.</span></span> <span data-ttu-id="3039b-144">Seznam dostupných možností najdete v tématu konkrétní příkazová stránka.</span><span class="sxs-lookup"><span data-stu-id="3039b-144">See specific command page for a list of available options.</span></span>

### <a name="runtime-options"></a><span data-ttu-id="3039b-145">Možnosti modulu runtime</span><span class="sxs-lookup"><span data-stu-id="3039b-145">Runtime options</span></span>

<span data-ttu-id="3039b-146">Když `dotnet` spouští aplikaci, jsou k dispozici následující možnosti.</span><span class="sxs-lookup"><span data-stu-id="3039b-146">The following options are available when `dotnet` runs an application.</span></span> <span data-ttu-id="3039b-147">například `dotnet myapp.dll --fx-version 3.1.1`.</span><span class="sxs-lookup"><span data-stu-id="3039b-147">For example, `dotnet myapp.dll --fx-version 3.1.1`.</span></span>

- **`--additionalprobingpath <PATH>`**

  <span data-ttu-id="3039b-148">Cesta obsahující zásady a sestavení pro zjišťování k testování</span><span class="sxs-lookup"><span data-stu-id="3039b-148">Path containing probing policy and assemblies to probe.</span></span>

- **`--additional-deps <PATH>`**

  <span data-ttu-id="3039b-149">Cesta k dodatečnému souboru *. DEPS. JSON* .</span><span class="sxs-lookup"><span data-stu-id="3039b-149">Path to an additional *.deps.json* file.</span></span> <span data-ttu-id="3039b-150">Soubor *DEPS. JSON* obsahuje seznam závislostí, závislosti kompilace a informace o verzi používané k řešení konfliktů sestavení.</span><span class="sxs-lookup"><span data-stu-id="3039b-150">A *deps.json* file contains a list of dependencies, compilation dependencies, and version information used to address assembly conflicts.</span></span> <span data-ttu-id="3039b-151">Další informace najdete v tématu [běhové konfigurační soubory](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="3039b-151">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

- **`--fx-version <VERSION>`**

  <span data-ttu-id="3039b-152">Verze modulu runtime .NET Core, která se má použít ke spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="3039b-152">Version of the .NET Core runtime to use to run the application.</span></span>

- **`--runtimeconfig`**

  <span data-ttu-id="3039b-153">Cesta k souboru *runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="3039b-153">Path to a *runtimeconfig.json* file.</span></span> <span data-ttu-id="3039b-154">Soubor *runtimeconfig. JSON* je konfigurační soubor, který obsahuje nastavení běhu.</span><span class="sxs-lookup"><span data-stu-id="3039b-154">A *runtimeconfig.json* file is a configuration file that contains run-time settings.</span></span> <span data-ttu-id="3039b-155">Další informace najdete v tématu [nastavení konfigurace runtime .NET Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="3039b-155">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

- <span data-ttu-id="3039b-156">**`--roll-forward-on-no-candidate-fx <N>`** **k dispozici v sadě .NET Core 2. x SDK.**</span><span class="sxs-lookup"><span data-stu-id="3039b-156">**`--roll-forward-on-no-candidate-fx <N>`** **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="3039b-157">Definuje chování v případě, že požadovaná sdílená architektura není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="3039b-157">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="3039b-158">`N` může být:</span><span class="sxs-lookup"><span data-stu-id="3039b-158">`N` can be:</span></span>

  - <span data-ttu-id="3039b-159">`0` – zakažte u sebe i menší verzi.</span><span class="sxs-lookup"><span data-stu-id="3039b-159">`0` - Disable even minor version roll forward.</span></span>
  - <span data-ttu-id="3039b-160">`1` – předejte se k dílčí verzi, ale ne k hlavní verzi.</span><span class="sxs-lookup"><span data-stu-id="3039b-160">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="3039b-161">Toto je výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="3039b-161">This is the default behavior.</span></span>
  - <span data-ttu-id="3039b-162">`2` – předejte se do menších a hlavních verzí.</span><span class="sxs-lookup"><span data-stu-id="3039b-162">`2` - Roll forward on minor and major versions.</span></span>

   <span data-ttu-id="3039b-163">Další informace najdete v tématu o tom, jak [Posunout](../whats-new/dotnet-core-2-1.md#roll-forward)nahoru.</span><span class="sxs-lookup"><span data-stu-id="3039b-163">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

- <span data-ttu-id="3039b-164">**`--roll-forward <SETTING>`** **k dispozici od .NET Core SDK 3,0.**</span><span class="sxs-lookup"><span data-stu-id="3039b-164">**`--roll-forward <SETTING>`** **Available starting with .NET Core SDK 3.0.**</span></span>

  <span data-ttu-id="3039b-165">Určuje, jak se v aplikaci aplikuje posunutí.</span><span class="sxs-lookup"><span data-stu-id="3039b-165">Controls how roll forward is applied to the app.</span></span> <span data-ttu-id="3039b-166">`SETTING` může být jedna z následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="3039b-166">The `SETTING` can be one of the following values.</span></span> <span data-ttu-id="3039b-167">Pokud není zadaný, `Minor` je výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="3039b-167">If not specified, `Minor` is the default.</span></span>

  - <span data-ttu-id="3039b-168">`LatestPatch` – vraťte se k nejvyšší verzi opravy.</span><span class="sxs-lookup"><span data-stu-id="3039b-168">`LatestPatch` - Roll forward to the highest patch version.</span></span> <span data-ttu-id="3039b-169">Tím se zakáže dílčí verze s posunem.</span><span class="sxs-lookup"><span data-stu-id="3039b-169">This disables minor version roll forward.</span></span>
  - <span data-ttu-id="3039b-170">v případě, že chybí požadovaná podverze, `Minor` – převeďte na nejnižší nižší verzi.</span><span class="sxs-lookup"><span data-stu-id="3039b-170">`Minor` - Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="3039b-171">Pokud je k dispozici požadovaná dílčí verze, použije se zásada LatestPatch.</span><span class="sxs-lookup"><span data-stu-id="3039b-171">If the requested minor version is present, then the LatestPatch policy is used.</span></span>
  - <span data-ttu-id="3039b-172">Pokud chybí požadovaná hlavní verze, `Major` – převeďte na nejnižší vyšší hlavní verzi a nejnižší podverzi.</span><span class="sxs-lookup"><span data-stu-id="3039b-172">`Major` - Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="3039b-173">Pokud je k dispozici požadovaná hlavní verze, použije se vedlejší zásada.</span><span class="sxs-lookup"><span data-stu-id="3039b-173">If the requested major version is present, then the Minor policy is used.</span></span>
  - <span data-ttu-id="3039b-174">`LatestMinor` – převeďte do nejvyšší dílčí verze, i když je k dispozici požadovaná dílčí verze.</span><span class="sxs-lookup"><span data-stu-id="3039b-174">`LatestMinor` - Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="3039b-175">Určeno pro scénáře hostování součástí.</span><span class="sxs-lookup"><span data-stu-id="3039b-175">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="3039b-176">`LatestMajor` – převeďte do nejvyšší hlavní a nejvyšší dílčí verze, a to i v případě, že je k dispozici požadovaná hlavní verze.</span><span class="sxs-lookup"><span data-stu-id="3039b-176">`LatestMajor` - Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="3039b-177">Určeno pro scénáře hostování součástí.</span><span class="sxs-lookup"><span data-stu-id="3039b-177">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="3039b-178">`Disable` – nezavádět do popředí.</span><span class="sxs-lookup"><span data-stu-id="3039b-178">`Disable` - Don't roll forward.</span></span> <span data-ttu-id="3039b-179">Vytvoří se jenom vazba na určenou verzi.</span><span class="sxs-lookup"><span data-stu-id="3039b-179">Only bind to specified version.</span></span> <span data-ttu-id="3039b-180">Tyto zásady se nedoporučují pro obecné použití, protože zakazují možnost navrátit se k nejnovějším opravám.</span><span class="sxs-lookup"><span data-stu-id="3039b-180">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="3039b-181">Tato hodnota se doporučuje jenom pro testování.</span><span class="sxs-lookup"><span data-stu-id="3039b-181">This value is only recommended for testing.</span></span>

<span data-ttu-id="3039b-182">S výjimkou `Disable`budou všechna nastavení využívat nejvyšší dostupnou verzi opravy.</span><span class="sxs-lookup"><span data-stu-id="3039b-182">With the exception of `Disable`, all settings will use the highest available patch version.</span></span>

<span data-ttu-id="3039b-183">Chování při posunutí nahoru lze také nakonfigurovat v vlastnost souboru projektu, vlastnosti konfiguračního souboru modulu runtime a proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="3039b-183">Roll forward behavior can also be configured in a project file property, a run-time configuration file property, and an environment variable.</span></span> <span data-ttu-id="3039b-184">Další informace najdete v tématu o [zavedení modulu runtime hlavní verze – posunutí](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span><span class="sxs-lookup"><span data-stu-id="3039b-184">For more information, see [Major-version runtime roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span></span>

## <a name="dotnet-commands"></a><span data-ttu-id="3039b-185">Příkazy dotnet</span><span class="sxs-lookup"><span data-stu-id="3039b-185">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="3039b-186">Obecné</span><span class="sxs-lookup"><span data-stu-id="3039b-186">General</span></span>

| <span data-ttu-id="3039b-187">Příkaz</span><span class="sxs-lookup"><span data-stu-id="3039b-187">Command</span></span>                                       | <span data-ttu-id="3039b-188">Funkce</span><span class="sxs-lookup"><span data-stu-id="3039b-188">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="3039b-189">dotnet build</span><span class="sxs-lookup"><span data-stu-id="3039b-189">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="3039b-190">Vytvoří aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3039b-190">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="3039b-191">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="3039b-191">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="3039b-192">Komunikuje se servery spuštěnými sestavením.</span><span class="sxs-lookup"><span data-stu-id="3039b-192">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="3039b-193">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="3039b-193">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="3039b-194">Vyčistit výstupy sestavení.</span><span class="sxs-lookup"><span data-stu-id="3039b-194">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="3039b-195">dotnet help</span><span class="sxs-lookup"><span data-stu-id="3039b-195">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="3039b-196">Zobrazí podrobnější dokumentaci pro příkaz online.</span><span class="sxs-lookup"><span data-stu-id="3039b-196">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="3039b-197">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="3039b-197">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="3039b-198">Migruje platný projekt verze Preview 2 na projekt .NET Core SDK 1,0.</span><span class="sxs-lookup"><span data-stu-id="3039b-198">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="3039b-199">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="3039b-199">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="3039b-200">Poskytuje přístup k příkazovému řádku MSBuild.</span><span class="sxs-lookup"><span data-stu-id="3039b-200">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="3039b-201">dotnet new</span><span class="sxs-lookup"><span data-stu-id="3039b-201">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="3039b-202">Inicializuje projekt C# nebo F# pro danou šablonu.</span><span class="sxs-lookup"><span data-stu-id="3039b-202">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="3039b-203">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="3039b-203">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="3039b-204">Vytvoří balíček NuGet vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="3039b-204">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="3039b-205">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="3039b-205">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="3039b-206">Publikuje aplikaci závislou na rozhraní .NET Framework nebo samostatnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3039b-206">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="3039b-207">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="3039b-207">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="3039b-208">Obnoví závislosti pro danou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3039b-208">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="3039b-209">dotnet run</span><span class="sxs-lookup"><span data-stu-id="3039b-209">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="3039b-210">Spustí aplikaci ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="3039b-210">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="3039b-211">dotnet run</span><span class="sxs-lookup"><span data-stu-id="3039b-211">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="3039b-212">Možnosti pro přidání, odebrání a výpis projektů v souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="3039b-212">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="3039b-213">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="3039b-213">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="3039b-214">Ukládá sestavení do úložiště balíčků modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="3039b-214">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="3039b-215">dotnet test</span><span class="sxs-lookup"><span data-stu-id="3039b-215">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="3039b-216">Spustí testy pomocí nástroje Test Runner.</span><span class="sxs-lookup"><span data-stu-id="3039b-216">Runs tests using a test runner.</span></span>                                     |

### <a name="project-references"></a><span data-ttu-id="3039b-217">Odkazy na projekty</span><span class="sxs-lookup"><span data-stu-id="3039b-217">Project references</span></span>

<span data-ttu-id="3039b-218">Příkaz</span><span class="sxs-lookup"><span data-stu-id="3039b-218">Command</span></span> | <span data-ttu-id="3039b-219">Funkce</span><span class="sxs-lookup"><span data-stu-id="3039b-219">Function</span></span>
--- | ---
[<span data-ttu-id="3039b-220">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="3039b-220">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="3039b-221">Přidá odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="3039b-221">Adds a project reference.</span></span>
[<span data-ttu-id="3039b-222">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="3039b-222">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="3039b-223">Vypíše odkazy na projekt.</span><span class="sxs-lookup"><span data-stu-id="3039b-223">Lists project references.</span></span>
[<span data-ttu-id="3039b-224">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="3039b-224">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="3039b-225">Odebere odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="3039b-225">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="3039b-226">Balíčky NuGet</span><span class="sxs-lookup"><span data-stu-id="3039b-226">NuGet packages</span></span>

<span data-ttu-id="3039b-227">Příkaz</span><span class="sxs-lookup"><span data-stu-id="3039b-227">Command</span></span> | <span data-ttu-id="3039b-228">Funkce</span><span class="sxs-lookup"><span data-stu-id="3039b-228">Function</span></span>
--- | ---
[<span data-ttu-id="3039b-229">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="3039b-229">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="3039b-230">Přidá balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="3039b-230">Adds a NuGet package.</span></span>
[<span data-ttu-id="3039b-231">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="3039b-231">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="3039b-232">Odebere balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="3039b-232">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="3039b-233">Příkazy NuGet</span><span class="sxs-lookup"><span data-stu-id="3039b-233">NuGet commands</span></span>

<span data-ttu-id="3039b-234">Příkaz</span><span class="sxs-lookup"><span data-stu-id="3039b-234">Command</span></span> | <span data-ttu-id="3039b-235">Funkce</span><span class="sxs-lookup"><span data-stu-id="3039b-235">Function</span></span>
--- | ---
[<span data-ttu-id="3039b-236">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="3039b-236">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="3039b-237">Odstraní nebo zruší výpis balíčku ze serveru.</span><span class="sxs-lookup"><span data-stu-id="3039b-237">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="3039b-238">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="3039b-238">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="3039b-239">Vymaže nebo vypíše místní prostředky NuGet, jako je mezipaměť požadavků HTTP, dočasná mezipaměť nebo složka globálních balíčků v celém počítači.</span><span class="sxs-lookup"><span data-stu-id="3039b-239">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="3039b-240">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="3039b-240">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="3039b-241">Odešle balíček na server a publikuje ho.</span><span class="sxs-lookup"><span data-stu-id="3039b-241">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tool-path-and-local-tools-commands"></a><span data-ttu-id="3039b-242">Příkazy globálních nástrojů, nástrojů a cest a místních nástrojů</span><span class="sxs-lookup"><span data-stu-id="3039b-242">Global, tool-path, and local tools commands</span></span>

<span data-ttu-id="3039b-243">Nástroje jsou konzolové aplikace, které jsou nainstalovány z balíčků NuGet a jsou vyvolány z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="3039b-243">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="3039b-244">Můžete psát nástroje sami nebo instalovat nástroje napsané třetí stranou.</span><span class="sxs-lookup"><span data-stu-id="3039b-244">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="3039b-245">Nástroje jsou také známé jako globální nástroje, nástroje pro cestu nástrojů a místní nástroje.</span><span class="sxs-lookup"><span data-stu-id="3039b-245">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="3039b-246">Další informace najdete v tématu [Přehled nástrojů .NET Core](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="3039b-246">For more information, see [.NET Core tools overview](global-tools.md).</span></span> <span data-ttu-id="3039b-247">Nástroje pro globální a cestu nástrojů jsou k dispozici od .NET Core SDK 2,1.</span><span class="sxs-lookup"><span data-stu-id="3039b-247">Global and tool-path tools are available starting with .NET Core SDK 2.1.</span></span> <span data-ttu-id="3039b-248">K dispozici jsou místní nástroje od .NET Core SDK 3,0.</span><span class="sxs-lookup"><span data-stu-id="3039b-248">Local tools are available starting with .NET Core SDK 3.0.</span></span>

<span data-ttu-id="3039b-249">Příkaz</span><span class="sxs-lookup"><span data-stu-id="3039b-249">Command</span></span> | <span data-ttu-id="3039b-250">Funkce</span><span class="sxs-lookup"><span data-stu-id="3039b-250">Function</span></span>
--- | ---
[<span data-ttu-id="3039b-251">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="3039b-251">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="3039b-252">Nainstaluje nástroj na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="3039b-252">Installs a tool on your machine.</span></span>
[<span data-ttu-id="3039b-253">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="3039b-253">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="3039b-254">Zobrazí seznam všech nástrojů, které jsou aktuálně nainstalované na vašem počítači, na základě globálních nástrojů, nástrojů a cest.</span><span class="sxs-lookup"><span data-stu-id="3039b-254">Lists all global, tool-path, or local tools currently installed on your machine.</span></span>
[<span data-ttu-id="3039b-255">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="3039b-255">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="3039b-256">Odinstaluje nástroj z počítače.</span><span class="sxs-lookup"><span data-stu-id="3039b-256">Uninstalls a tool from your machine.</span></span>
[<span data-ttu-id="3039b-257">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="3039b-257">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="3039b-258">Aktualizuje nástroj, který je nainstalovaný na vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="3039b-258">Updates a tool that is installed on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="3039b-259">Další nástroje</span><span class="sxs-lookup"><span data-stu-id="3039b-259">Additional tools</span></span>

<span data-ttu-id="3039b-260">Počínaje .NET Core SDK 2.1.300 je teď k dispozici několik nástrojů, které byly k dispozici pouze pro jednotlivé projekty pomocí `DotnetCliToolReference` jsou nyní k dispozici jako součást .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="3039b-260">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="3039b-261">Tyto nástroje jsou uvedené v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="3039b-261">These tools are listed in the following table:</span></span>

| <span data-ttu-id="3039b-262">Nástroj</span><span class="sxs-lookup"><span data-stu-id="3039b-262">Tool</span></span>                                              | <span data-ttu-id="3039b-263">Funkce</span><span class="sxs-lookup"><span data-stu-id="3039b-263">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="3039b-264">vývoj – certifikáty</span><span class="sxs-lookup"><span data-stu-id="3039b-264">dev-certs</span></span>                                         | <span data-ttu-id="3039b-265">Vytvoří a spravuje vývojové certifikáty.</span><span class="sxs-lookup"><span data-stu-id="3039b-265">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="3039b-266">EF</span><span class="sxs-lookup"><span data-stu-id="3039b-266">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="3039b-267">Entity Framework Core nástroje příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="3039b-267">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="3039b-268">sql-cache</span><span class="sxs-lookup"><span data-stu-id="3039b-268">sql-cache</span></span>                                         | <span data-ttu-id="3039b-269">Nástroje příkazového řádku pro SQL Server cache</span><span class="sxs-lookup"><span data-stu-id="3039b-269">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="3039b-270">uživatel – tajné klíče</span><span class="sxs-lookup"><span data-stu-id="3039b-270">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="3039b-271">Spravuje tajné klíče uživatele.</span><span class="sxs-lookup"><span data-stu-id="3039b-271">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="3039b-272">sledovací</span><span class="sxs-lookup"><span data-stu-id="3039b-272">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="3039b-273">Spustí sledovací proces souborů, který spustí příkaz, když se soubory změní.</span><span class="sxs-lookup"><span data-stu-id="3039b-273">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="3039b-274">Další informace o jednotlivých nástrojích získáte, když zadáte `dotnet <tool-name> --help`.</span><span class="sxs-lookup"><span data-stu-id="3039b-274">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="3039b-275">Příklady</span><span class="sxs-lookup"><span data-stu-id="3039b-275">Examples</span></span>

<span data-ttu-id="3039b-276">Vytvořte novou konzolovou aplikaci .NET Core:</span><span class="sxs-lookup"><span data-stu-id="3039b-276">Create a new .NET Core console application:</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="3039b-277">Sestavení projektu a jeho závislostí v daném adresáři:</span><span class="sxs-lookup"><span data-stu-id="3039b-277">Build a project and its dependencies in a given directory:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="3039b-278">Spuštění aplikace:</span><span class="sxs-lookup"><span data-stu-id="3039b-278">Run an application:</span></span>

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a><span data-ttu-id="3039b-279">Proměnné prostředí</span><span class="sxs-lookup"><span data-stu-id="3039b-279">Environment variables</span></span>

- <span data-ttu-id="3039b-280">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span><span class="sxs-lookup"><span data-stu-id="3039b-280">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span></span>

  <span data-ttu-id="3039b-281">Určuje umístění modulů runtime .NET Core, pokud nejsou nainstalovány ve výchozím umístění.</span><span class="sxs-lookup"><span data-stu-id="3039b-281">Specifies the location of the .NET Core runtimes, if they are not installed in the default location.</span></span> <span data-ttu-id="3039b-282">Výchozí umístění ve Windows je `C:\Program Files\dotnet`.</span><span class="sxs-lookup"><span data-stu-id="3039b-282">The default location on Windows is `C:\Program Files\dotnet`.</span></span> <span data-ttu-id="3039b-283">Výchozí umístění v systému Linux a macOS je `/usr/share/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="3039b-283">The default location on Linux and macOS is `/usr/share/dotnet`.</span></span> <span data-ttu-id="3039b-284">Tato proměnná prostředí se používá jenom při spouštění aplikací prostřednictvím generovaných spustitelných souborů (apphosts).</span><span class="sxs-lookup"><span data-stu-id="3039b-284">This environment variable is used only when running apps via generated executables (apphosts).</span></span> <span data-ttu-id="3039b-285">místo toho se používá `DOTNET_ROOT(x86)`, když se na 64 operačním systému spouští 32 spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="3039b-285">`DOTNET_ROOT(x86)` is used instead when running a 32-bit executable on a 64-bit OS.</span></span>

- `DOTNET_PACKAGES`

  <span data-ttu-id="3039b-286">Složka globálních balíčků.</span><span class="sxs-lookup"><span data-stu-id="3039b-286">The global packages folder.</span></span> <span data-ttu-id="3039b-287">Pokud není nastavené, použije se výchozí nastavení `~/.nuget/packages` v systému UNIX nebo `%userprofile%\.nuget\packages` ve Windows.</span><span class="sxs-lookup"><span data-stu-id="3039b-287">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

- `DOTNET_SERVICING`

  <span data-ttu-id="3039b-288">Určuje umístění indexu údržby používaného sdíleným hostitelem při načítání modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="3039b-288">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  <span data-ttu-id="3039b-289">Určuje, jestli se data o využití nástrojů .NET Core shromažďují a odesílají do Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="3039b-289">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="3039b-290">Nastavte na `true` pro výslovný souhlas funkce telemetrie (hodnoty `true`, `1`nebo `yes` přijaté).</span><span class="sxs-lookup"><span data-stu-id="3039b-290">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="3039b-291">Jinak nastavte `false` tak, aby se přihlásil k funkcím telemetrie (hodnoty `false`, `0`nebo přijaté `no`).</span><span class="sxs-lookup"><span data-stu-id="3039b-291">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="3039b-292">Pokud není nastavená, výchozí hodnota je `false` a funkce telemetrie je aktivní.</span><span class="sxs-lookup"><span data-stu-id="3039b-292">If not set, the default is `false` and the telemetry feature is active.</span></span>

- `DOTNET_MULTILEVEL_LOOKUP`

  <span data-ttu-id="3039b-293">Určuje, zda je rozhraní .NET Core Runtime, sdílené rozhraní nebo sada SDK vyřešeno z globálního umístění.</span><span class="sxs-lookup"><span data-stu-id="3039b-293">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="3039b-294">Pokud není nastavené, použije se výchozí hodnota 1 (logická `true`).</span><span class="sxs-lookup"><span data-stu-id="3039b-294">If not set, it defaults to 1 (logical `true`).</span></span> <span data-ttu-id="3039b-295">Nastavte na 0 (logický `false`), aby se nepřeložily z globálního umístění a měly izolované instalace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3039b-295">Set to 0 (logical `false`) to not resolve from the global location and have isolated .NET Core installations.</span></span> <span data-ttu-id="3039b-296">Další informace o vyhledávání na více úrovních najdete v tématu [SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="3039b-296">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

- <span data-ttu-id="3039b-297">`DOTNET_ROLL_FORWARD` **k dispozici počínaje verzí .NET Core 3. x SDK.**</span><span class="sxs-lookup"><span data-stu-id="3039b-297">`DOTNET_ROLL_FORWARD` **Available starting with .NET Core 3.x SDK.**</span></span>

  <span data-ttu-id="3039b-298">Určuje chování při posunu nahoru.</span><span class="sxs-lookup"><span data-stu-id="3039b-298">Determines roll forward behavior.</span></span> <span data-ttu-id="3039b-299">Další informace najdete v části `--roll-forward` možnosti výše v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="3039b-299">For more information, see the `--roll-forward` option earlier in this article.</span></span>

- <span data-ttu-id="3039b-300">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **k dispozici v sadě .NET Core 2. x SDK.**</span><span class="sxs-lookup"><span data-stu-id="3039b-300">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="3039b-301">Zakáže posunutí dílčí verze, pokud je nastaveno na `0`.</span><span class="sxs-lookup"><span data-stu-id="3039b-301">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="3039b-302">Další informace najdete v tématu o tom, jak [Posunout](../whats-new/dotnet-core-2-1.md#roll-forward)nahoru.</span><span class="sxs-lookup"><span data-stu-id="3039b-302">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

- `DOTNET_CLI_UI_LANGUAGE`

  <span data-ttu-id="3039b-303">Nastaví jazyk uživatelského rozhraní CLI pomocí hodnoty národního prostředí, například `en-us`.</span><span class="sxs-lookup"><span data-stu-id="3039b-303">Sets the language of the CLI UI using a locale value such as `en-us`.</span></span> <span data-ttu-id="3039b-304">Podporované hodnoty jsou stejné jako u sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3039b-304">The supported values are the same as for Visual Studio.</span></span> <span data-ttu-id="3039b-305">Další informace najdete v části o změně jazyka instalačního programu v [dokumentaci k instalaci sady Visual Studio](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019).</span><span class="sxs-lookup"><span data-stu-id="3039b-305">For more information, see the section on changing the installer language in the [Visual Studio installation documentation](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019).</span></span> <span data-ttu-id="3039b-306">Použijí se pravidla správce prostředků .NET, takže nemusíte vybírat přesnou shodu&mdash;můžete také vybrat následníky ve stromu `CultureInfo`.</span><span class="sxs-lookup"><span data-stu-id="3039b-306">The .NET resource manager rules apply, so you don't have to pick an exact match&mdash;you can also pick descendants in the `CultureInfo` tree.</span></span> <span data-ttu-id="3039b-307">Například pokud nastavíte `fr-CA`, rozhraní příkazového řádku nalezne a použije překlady `fr`.</span><span class="sxs-lookup"><span data-stu-id="3039b-307">For example, if you set it to `fr-CA`, the CLI will find and use the `fr` translations.</span></span> <span data-ttu-id="3039b-308">Pokud ho nastavíte na jazyk, který není podporován, rozhraní příkazového řádku se vrátí do angličtiny.</span><span class="sxs-lookup"><span data-stu-id="3039b-308">If you set it to a language that is not supported, the CLI falls back to English.</span></span>

- `DOTNET_DISABLE_GUI_ERRORS`

  <span data-ttu-id="3039b-309">U generovaných spustitelných souborů s povoleným grafickým uživatelským rozhraním – zakáže dialogová okna, která obvykle zobrazuje určité třídy chyb.</span><span class="sxs-lookup"><span data-stu-id="3039b-309">For GUI-enabled generated executables - disables dialog popup which normally shows for certain classes of errors.</span></span> <span data-ttu-id="3039b-310">Zapisuje pouze do `stderr` a v těchto případech skončí.</span><span class="sxs-lookup"><span data-stu-id="3039b-310">It only writes to `stderr` and exits in those cases.</span></span>
  
- `DOTNET_ADDITIONAL_DEPS`

  <span data-ttu-id="3039b-311">Ekvivalent možnosti CLI `--additional-deps`.</span><span class="sxs-lookup"><span data-stu-id="3039b-311">Equivalent to CLI option `--additional-deps`.</span></span>

- `DOTNET_RUNTIME_ID`

  <span data-ttu-id="3039b-312">Přepíše zjištěný identifikátor RID.</span><span class="sxs-lookup"><span data-stu-id="3039b-312">Overrides the detected RID.</span></span>

- `DOTNET_SHARED_STORE`

  <span data-ttu-id="3039b-313">Umístění sdíleného úložiště, na které se rozlišení sestavení vrátí v některých případech.</span><span class="sxs-lookup"><span data-stu-id="3039b-313">Location of the "shared store" which assembly resolution falls back to in some cases.</span></span>

- `DOTNET_STARTUP_HOOKS`

  <span data-ttu-id="3039b-314">Seznam sestavení pro načtení a spuštění spouštěcích háky z.</span><span class="sxs-lookup"><span data-stu-id="3039b-314">List of assemblies to load and execute startup hooks from.</span></span>

- <span data-ttu-id="3039b-315">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span><span class="sxs-lookup"><span data-stu-id="3039b-315">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span></span>

  <span data-ttu-id="3039b-316">Řídí trasování diagnostiky z komponent hostování, například `dotnet.exe`, `hostfxr`a `hostpolicy`.</span><span class="sxs-lookup"><span data-stu-id="3039b-316">Controls diagnostics tracing from the hosting components, such as `dotnet.exe`, `hostfxr`, and `hostpolicy`.</span></span>

## <a name="see-also"></a><span data-ttu-id="3039b-317">Viz také</span><span class="sxs-lookup"><span data-stu-id="3039b-317">See also</span></span>

- [<span data-ttu-id="3039b-318">Běhové konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="3039b-318">Runtime Configuration Files</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [<span data-ttu-id="3039b-319">Nastavení konfigurace runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="3039b-319">.NET Core run-time configuration settings</span></span>](../run-time-config/index.md)
