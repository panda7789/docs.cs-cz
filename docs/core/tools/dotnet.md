---
title: dotnet – příkaz
description: Přečtěte si o příkazu dotnet (obecný ovladač pro .NET Core CLI) a jeho použití.
ms.date: 02/13/2020
ms.openlocfilehash: 88e92b3ff5e8f68b980015a817434dd2d67df93a
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378844"
---
# <a name="dotnet-command"></a><span data-ttu-id="0f3ff-103">dotnet – příkaz</span><span class="sxs-lookup"><span data-stu-id="0f3ff-103">dotnet command</span></span>

<span data-ttu-id="0f3ff-104">**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="0f3ff-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="0f3ff-105">Name</span><span class="sxs-lookup"><span data-stu-id="0f3ff-105">Name</span></span>

<span data-ttu-id="0f3ff-106">`dotnet`– Obecný ovladač pro .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-106">`dotnet` - The generic driver for the .NET Core CLI.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0f3ff-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="0f3ff-107">Synopsis</span></span>

<span data-ttu-id="0f3ff-108">Chcete-li získat informace o dostupných příkazech a prostředí:</span><span class="sxs-lookup"><span data-stu-id="0f3ff-108">To get information about the available commands and the environment:</span></span>

```dotnetcli
dotnet [--version] [--info] [--list-runtimes] [--list-sdks]

dotnet -h|--help
```

<span data-ttu-id="0f3ff-109">Spuštění příkazu (vyžaduje instalaci sady SDK):</span><span class="sxs-lookup"><span data-stu-id="0f3ff-109">To run a command (requires SDK installation):</span></span>

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity <LEVEL>]
    [command-options] [arguments]
```

<span data-ttu-id="0f3ff-110">Spuštění aplikace:</span><span class="sxs-lookup"><span data-stu-id="0f3ff-110">To run an application:</span></span>

```dotnetcli
dotnet [--additionalprobingpath <PATH>] [--additional-deps <PATH>]
    [--fx-version <VERSION>]  [--roll-forward <SETTING>]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps <PATH>]
    [--fx-version <VERSION>]  [--roll-forward <SETTING>]
    <PATH_TO_APPLICATION> [arguments]
```

<span data-ttu-id="0f3ff-111">`--roll-forward`je k dispozici od verze .NET Core 3. x.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-111">`--roll-forward` is available since .NET Core 3.x.</span></span> <span data-ttu-id="0f3ff-112">Používá se `--roll-forward-on-no-candidate-fx` pro .NET Core 2. x.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-112">Use `--roll-forward-on-no-candidate-fx` for .NET Core 2.x.</span></span>

## <a name="description"></a><span data-ttu-id="0f3ff-113">Popis</span><span class="sxs-lookup"><span data-stu-id="0f3ff-113">Description</span></span>

<span data-ttu-id="0f3ff-114">`dotnet`Příkaz má dvě funkce:</span><span class="sxs-lookup"><span data-stu-id="0f3ff-114">The `dotnet` command has two functions:</span></span>

- <span data-ttu-id="0f3ff-115">Poskytuje příkazy pro práci s projekty .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-115">It provides commands for working with .NET Core projects.</span></span>

  <span data-ttu-id="0f3ff-116">Například [`dotnet build`](dotnet-build.md) sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-116">For example, [`dotnet build`](dotnet-build.md) builds a project.</span></span> <span data-ttu-id="0f3ff-117">Každý příkaz definuje vlastní parametry a argumenty.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-117">Each command defines its own options and arguments.</span></span> <span data-ttu-id="0f3ff-118">Všechny příkazy podporují `--help` možnost tisku stručné dokumentace k použití příkazu.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-118">All commands support the `--help` option for printing out brief documentation about how to use the command.</span></span>

- <span data-ttu-id="0f3ff-119">Spouští aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-119">It runs .NET Core applications.</span></span>

  <span data-ttu-id="0f3ff-120">Zadejte cestu k `.dll` souboru aplikace pro spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-120">You specify the path to an application `.dll` file to run the application.</span></span>  <span data-ttu-id="0f3ff-121">Pro spuštění aplikace znamená, že se má vyhledat a spustit vstupní bod, který je v případě konzolových aplikací `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-121">To run the application means to find and execute the entry point, which in the case of console apps is the `Main` method.</span></span> <span data-ttu-id="0f3ff-122">Například `dotnet myapp.dll` spustí `myapp` aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-122">For example, `dotnet myapp.dll` runs the `myapp` application.</span></span> <span data-ttu-id="0f3ff-123">Další informace o možnostech nasazení najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md) .</span><span class="sxs-lookup"><span data-stu-id="0f3ff-123">See [.NET Core application deployment](../deploying/index.md) to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="0f3ff-124">Možnosti</span><span class="sxs-lookup"><span data-stu-id="0f3ff-124">Options</span></span>

<span data-ttu-id="0f3ff-125">K dispozici jsou různé možnosti pro `dotnet` spuštění příkazu a pro spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-125">Different options are available for `dotnet` by itself, for running a command, and for running an application.</span></span>

### <a name="options-for-dotnet-by-itself"></a><span data-ttu-id="0f3ff-126">Možnosti pro dotnet samotné</span><span class="sxs-lookup"><span data-stu-id="0f3ff-126">Options for dotnet by itself</span></span>

<span data-ttu-id="0f3ff-127">Následující možnosti jsou samotné pro `dotnet` sebe sama.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-127">The following options are for `dotnet` by itself.</span></span> <span data-ttu-id="0f3ff-128">Například, `dotnet --info`.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-128">For example, `dotnet --info`.</span></span> <span data-ttu-id="0f3ff-129">Tisknou informace o daném prostředí.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-129">They print out information about the environment.</span></span>

- **`--info`**

  <span data-ttu-id="0f3ff-130">Vytiskne podrobné informace o instalaci .NET Core a počítačovém prostředí, jako je aktuální operační systém, a potvrzení SHA verze .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-130">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

- **`--version`**

  <span data-ttu-id="0f3ff-131">Vytiskne verzi .NET Core SDK, která se používá.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-131">Prints out the version of the .NET Core SDK in use.</span></span>

- **`--list-runtimes`**

  <span data-ttu-id="0f3ff-132">Vytiskne seznam nainstalovaných modulů runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-132">Prints out a list of the installed .NET Core runtimes.</span></span> <span data-ttu-id="0f3ff-133">Verze x86 sady SDK obsahuje jenom modul runtime x86 a verze x64 sady SDK obsahuje jenom technologie runtime x64.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-133">An x86 version of the SDK lists only x86 runtimes, and an x64 version of the SDK lists only x64 runtimes.</span></span>

- **`--list-sdks`**

  <span data-ttu-id="0f3ff-134">Vytiskne seznam nainstalovaných sad SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-134">Prints out a list of the installed .NET Core SDKs.</span></span>

- **`-h|--help`**

  <span data-ttu-id="0f3ff-135">Vytiskne seznam dostupných příkazů.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-135">Prints out a list of available commands.</span></span>

### <a name="sdk-options-for-running-a-command"></a><span data-ttu-id="0f3ff-136">Možnosti sady SDK pro spuštění příkazu</span><span class="sxs-lookup"><span data-stu-id="0f3ff-136">SDK options for running a command</span></span>

<span data-ttu-id="0f3ff-137">Následující možnosti jsou pro `dotnet` s příkazem.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-137">The following options are for `dotnet` with a command.</span></span> <span data-ttu-id="0f3ff-138">Například, `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-138">For example, `dotnet build --help`.</span></span>

- **`-d|--diagnostics`**

  <span data-ttu-id="0f3ff-139">Povolí výstup diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-139">Enables diagnostic output.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="0f3ff-140">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-140">Sets the verbosity level of the command.</span></span> <span data-ttu-id="0f3ff-141">Povolené hodnoty jsou `q[uiet]` , `m[inimal]` ,, a `n[ormal]` `d[etailed]` `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="0f3ff-141">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="0f3ff-142">Nepodporováno v každém příkazu.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-142">Not supported in every command.</span></span> <span data-ttu-id="0f3ff-143">Pokud chcete zjistit, zda je tato možnost k dispozici, zobrazte konkrétní příkazová stránka.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-143">See specific command page to determine if this option is available.</span></span>

- **`-h|--help`**

  <span data-ttu-id="0f3ff-144">Vytiskne dokumentaci pro daný příkaz, například `dotnet build --help` .</span><span class="sxs-lookup"><span data-stu-id="0f3ff-144">Prints out documentation for a given command, such as `dotnet build --help`.</span></span>

- **`command options`**

  <span data-ttu-id="0f3ff-145">Každý příkaz definuje možnosti specifické pro tento příkaz.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-145">Each command defines options specific to that command.</span></span> <span data-ttu-id="0f3ff-146">Seznam dostupných možností najdete v tématu konkrétní příkazová stránka.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-146">See specific command page for a list of available options.</span></span>

### <a name="runtime-options"></a><span data-ttu-id="0f3ff-147">Možnosti modulu runtime</span><span class="sxs-lookup"><span data-stu-id="0f3ff-147">Runtime options</span></span>

<span data-ttu-id="0f3ff-148">Při spuštění aplikace jsou k dispozici následující možnosti `dotnet` .</span><span class="sxs-lookup"><span data-stu-id="0f3ff-148">The following options are available when `dotnet` runs an application.</span></span> <span data-ttu-id="0f3ff-149">Například, `dotnet myapp.dll --roll-forward Major`.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-149">For example, `dotnet myapp.dll --roll-forward Major`.</span></span>

- **`--additionalprobingpath <PATH>`**

  <span data-ttu-id="0f3ff-150">Cesta obsahující zásady a sestavení pro zjišťování k testování</span><span class="sxs-lookup"><span data-stu-id="0f3ff-150">Path containing probing policy and assemblies to probe.</span></span>

- **`--additional-deps <PATH>`**

  <span data-ttu-id="0f3ff-151">Cesta k dodatečnému souboru *. DEPS. JSON* .</span><span class="sxs-lookup"><span data-stu-id="0f3ff-151">Path to an additional *.deps.json* file.</span></span> <span data-ttu-id="0f3ff-152">Soubor *DEPS. JSON* obsahuje seznam závislostí, závislosti kompilace a informace o verzi používané k řešení konfliktů sestavení.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-152">A *deps.json* file contains a list of dependencies, compilation dependencies, and version information used to address assembly conflicts.</span></span> <span data-ttu-id="0f3ff-153">Další informace najdete v tématu [běhové konfigurační soubory](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-153">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

- **`--depsfile <PATH_TO_DEPSFILE>`**

  <span data-ttu-id="0f3ff-154">Cesta k souboru *DEPS. JSON* .</span><span class="sxs-lookup"><span data-stu-id="0f3ff-154">Path to the *deps.json* file.</span></span> <span data-ttu-id="0f3ff-155">Soubor *DEPS. JSON* je konfigurační soubor, který obsahuje informace o závislostech nezbytných ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-155">A *deps.json* file is a configuration file that contains information about dependencies necessary to run the application.</span></span> <span data-ttu-id="0f3ff-156">Tento soubor je vygenerovaný .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-156">This file is generated by the .NET Core SDK.</span></span>

- **`--runtimeconfig`**

  <span data-ttu-id="0f3ff-157">Cesta k souboru *runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="0f3ff-157">Path to a *runtimeconfig.json* file.</span></span> <span data-ttu-id="0f3ff-158">Soubor *runtimeconfig. JSON* je konfigurační soubor, který obsahuje nastavení běhu.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-158">A *runtimeconfig.json* file is a configuration file that contains run-time settings.</span></span> <span data-ttu-id="0f3ff-159">Další informace najdete v tématu [nastavení konfigurace runtime .NET Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="0f3ff-159">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

- <span data-ttu-id="0f3ff-160">**`--roll-forward <SETTING>`\*\*\*\*K dispozici od .NET Core SDK 3,0.**</span><span class="sxs-lookup"><span data-stu-id="0f3ff-160">**`--roll-forward <SETTING>`** **Available starting with .NET Core SDK 3.0.**</span></span>

  <span data-ttu-id="0f3ff-161">Určuje, jak se v aplikaci aplikuje posunutí.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-161">Controls how roll forward is applied to the app.</span></span> <span data-ttu-id="0f3ff-162">`SETTING`Může to být jedna z následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-162">The `SETTING` can be one of the following values.</span></span> <span data-ttu-id="0f3ff-163">Pokud není zadán, `Minor` je výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-163">If not specified, `Minor` is the default.</span></span>

  - <span data-ttu-id="0f3ff-164">`LatestPatch`– Vraťte se k nejvyšší verzi opravy.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-164">`LatestPatch` - Roll forward to the highest patch version.</span></span> <span data-ttu-id="0f3ff-165">Tím se zakáže dílčí verze s posunem.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-165">This disables minor version roll forward.</span></span>
  - <span data-ttu-id="0f3ff-166">`Minor`-Posunutí nahoru na nejnižší nižší verzi, pokud chybí požadovaná dílčí verze.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-166">`Minor` - Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="0f3ff-167">Pokud je k dispozici požadovaná dílčí verze, použije se zásada LatestPatch.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-167">If the requested minor version is present, then the LatestPatch policy is used.</span></span>
  - <span data-ttu-id="0f3ff-168">`Major`-Pokud chybí požadovaná hlavní verze, převeďte nahoru na nejnižší vyšší hlavní verzi a nejnižší podverzi.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-168">`Major` - Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="0f3ff-169">Pokud je k dispozici požadovaná hlavní verze, použije se vedlejší zásada.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-169">If the requested major version is present, then the Minor policy is used.</span></span>
  - <span data-ttu-id="0f3ff-170">`LatestMinor`– Převeďte dál na nejvyšší dílčí verzi, i když je k dispozici požadovaná dílčí verze.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-170">`LatestMinor` - Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="0f3ff-171">Určeno pro scénáře hostování součástí.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-171">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="0f3ff-172">`LatestMajor`– Převeďte předem na nejvyšší hlavní a nejvyšší podverzi, i když je k dispozici požadovaná hlavní verze.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-172">`LatestMajor` - Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="0f3ff-173">Určeno pro scénáře hostování součástí.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-173">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="0f3ff-174">`Disable`– Nezavádět předem.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-174">`Disable` - Don't roll forward.</span></span> <span data-ttu-id="0f3ff-175">Vytvoří se jenom vazba na určenou verzi.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-175">Only bind to specified version.</span></span> <span data-ttu-id="0f3ff-176">Tyto zásady se nedoporučují pro obecné použití, protože zakazují možnost navrátit se k nejnovějším opravám.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-176">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="0f3ff-177">Tato hodnota se doporučuje jenom pro testování.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-177">This value is only recommended for testing.</span></span>

  <span data-ttu-id="0f3ff-178">Kromě `Disable` toho všechna nastavení použijí nejvyšší dostupnou verzi opravy.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-178">With the exception of `Disable`, all settings will use the highest available patch version.</span></span>

  <span data-ttu-id="0f3ff-179">Chování při posunutí nahoru lze také nakonfigurovat v vlastnost souboru projektu, vlastnosti konfiguračního souboru modulu runtime a proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-179">Roll forward behavior can also be configured in a project file property, a run-time configuration file property, and an environment variable.</span></span> <span data-ttu-id="0f3ff-180">Další informace najdete v tématu o [zavedení modulu runtime hlavní verze – posunutí](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span><span class="sxs-lookup"><span data-stu-id="0f3ff-180">For more information, see [Major-version runtime roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span></span>

- <span data-ttu-id="0f3ff-181">**`--roll-forward-on-no-candidate-fx <N>`\*\*\*\*K dispozici v sadě .NET Core 2. x SDK.**</span><span class="sxs-lookup"><span data-stu-id="0f3ff-181">**`--roll-forward-on-no-candidate-fx <N>`** **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="0f3ff-182">Definuje chování v případě, že požadovaná sdílená architektura není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-182">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="0f3ff-183">`N`může být:</span><span class="sxs-lookup"><span data-stu-id="0f3ff-183">`N` can be:</span></span>

  - <span data-ttu-id="0f3ff-184">`0`– Zakažte u sebe i menší verzi.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-184">`0` - Disable even minor version roll forward.</span></span>
  - <span data-ttu-id="0f3ff-185">`1`– Navýšení se dopředá na podverzi, ale ne na hlavní verzi.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-185">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="0f3ff-186">Toto je výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-186">This is the default behavior.</span></span>
  - <span data-ttu-id="0f3ff-187">`2`– Posunutí posunu k dílčím a hlavním verzím</span><span class="sxs-lookup"><span data-stu-id="0f3ff-187">`2` - Roll forward on minor and major versions.</span></span>

  <span data-ttu-id="0f3ff-188">Další informace najdete v tématu o tom, jak [Posunout](../whats-new/dotnet-core-2-1.md#roll-forward)nahoru.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-188">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

  <span data-ttu-id="0f3ff-189">Počínaje rozhraním .NET Core 3,0 je tato možnost nahrazena aplikací `--roll-forward` a tato možnost by se měla použít místo toho.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-189">Starting with .NET Core 3.0, this option is superseded by `--roll-forward`, and that option should be used instead.</span></span>

- **`--fx-version <VERSION>`**

  <span data-ttu-id="0f3ff-190">Verze modulu runtime .NET Core, která se má použít ke spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="0f3ff-190">Version of the .NET Core runtime to use to run the application.</span></span>

  <span data-ttu-id="0f3ff-191">Tato možnost přepíše verzi prvního odkazu na rozhraní v `.runtimeconfig.json` souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-191">This option overrides the version of the first framework reference in the application's `.runtimeconfig.json` file.</span></span> <span data-ttu-id="0f3ff-192">To znamená, že funguje podle očekávání pouze v případě, že existuje pouze jeden odkaz na rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-192">This means it only works as expected if there's just one framework reference.</span></span> <span data-ttu-id="0f3ff-193">Pokud má aplikace více než jeden odkaz na rozhraní, může použití této možnosti způsobit chyby.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-193">If the application has more than one framework reference, using this option may cause errors.</span></span>

## <a name="dotnet-commands"></a><span data-ttu-id="0f3ff-194">Příkazy dotnet</span><span class="sxs-lookup"><span data-stu-id="0f3ff-194">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="0f3ff-195">Obecné</span><span class="sxs-lookup"><span data-stu-id="0f3ff-195">General</span></span>

| <span data-ttu-id="0f3ff-196">Příkaz</span><span class="sxs-lookup"><span data-stu-id="0f3ff-196">Command</span></span>                                       | <span data-ttu-id="0f3ff-197">Funkce</span><span class="sxs-lookup"><span data-stu-id="0f3ff-197">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="0f3ff-198">dotnet build</span><span class="sxs-lookup"><span data-stu-id="0f3ff-198">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="0f3ff-199">Vytvoří aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-199">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="0f3ff-200">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="0f3ff-200">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="0f3ff-201">Komunikuje se servery spuštěnými sestavením.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-201">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="0f3ff-202">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="0f3ff-202">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="0f3ff-203">Vyčistit výstupy sestavení.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-203">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="0f3ff-204">dotnet help</span><span class="sxs-lookup"><span data-stu-id="0f3ff-204">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="0f3ff-205">Zobrazí podrobnější dokumentaci pro příkaz online.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-205">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="0f3ff-206">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="0f3ff-206">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="0f3ff-207">Migruje platný projekt verze Preview 2 na projekt .NET Core SDK 1,0.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-207">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="0f3ff-208">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="0f3ff-208">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="0f3ff-209">Poskytuje přístup k příkazovému řádku MSBuild.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-209">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="0f3ff-210">dotnet new</span><span class="sxs-lookup"><span data-stu-id="0f3ff-210">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="0f3ff-211">Inicializuje projekt C# nebo F # pro danou šablonu.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-211">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="0f3ff-212">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="0f3ff-212">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="0f3ff-213">Vytvoří balíček NuGet vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-213">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="0f3ff-214">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="0f3ff-214">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="0f3ff-215">Publikuje aplikaci závislou na rozhraní .NET Framework nebo samostatnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-215">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="0f3ff-216">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="0f3ff-216">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="0f3ff-217">Obnoví závislosti pro danou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-217">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="0f3ff-218">dotnet run</span><span class="sxs-lookup"><span data-stu-id="0f3ff-218">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="0f3ff-219">Spustí aplikaci ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-219">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="0f3ff-220">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="0f3ff-220">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="0f3ff-221">Možnosti pro přidání, odebrání a výpis projektů v souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-221">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="0f3ff-222">dotnet store</span><span class="sxs-lookup"><span data-stu-id="0f3ff-222">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="0f3ff-223">Ukládá sestavení do úložiště balíčků modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-223">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="0f3ff-224">dotnet test</span><span class="sxs-lookup"><span data-stu-id="0f3ff-224">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="0f3ff-225">Spustí testy pomocí nástroje Test Runner.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-225">Runs tests using a test runner.</span></span>                                     |

### <a name="project-references"></a><span data-ttu-id="0f3ff-226">Odkazy na projekty</span><span class="sxs-lookup"><span data-stu-id="0f3ff-226">Project references</span></span>

<span data-ttu-id="0f3ff-227">Příkaz</span><span class="sxs-lookup"><span data-stu-id="0f3ff-227">Command</span></span> | <span data-ttu-id="0f3ff-228">Funkce</span><span class="sxs-lookup"><span data-stu-id="0f3ff-228">Function</span></span>
--- | ---
[<span data-ttu-id="0f3ff-229">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="0f3ff-229">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="0f3ff-230">Přidá odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-230">Adds a project reference.</span></span>
[<span data-ttu-id="0f3ff-231">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="0f3ff-231">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="0f3ff-232">Vypíše odkazy na projekt.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-232">Lists project references.</span></span>
[<span data-ttu-id="0f3ff-233">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="0f3ff-233">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="0f3ff-234">Odebere odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-234">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="0f3ff-235">Balíčky NuGet</span><span class="sxs-lookup"><span data-stu-id="0f3ff-235">NuGet packages</span></span>

<span data-ttu-id="0f3ff-236">Příkaz</span><span class="sxs-lookup"><span data-stu-id="0f3ff-236">Command</span></span> | <span data-ttu-id="0f3ff-237">Funkce</span><span class="sxs-lookup"><span data-stu-id="0f3ff-237">Function</span></span>
--- | ---
[<span data-ttu-id="0f3ff-238">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="0f3ff-238">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="0f3ff-239">Přidá balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-239">Adds a NuGet package.</span></span>
[<span data-ttu-id="0f3ff-240">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="0f3ff-240">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="0f3ff-241">Odebere balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-241">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="0f3ff-242">Příkazy NuGet</span><span class="sxs-lookup"><span data-stu-id="0f3ff-242">NuGet commands</span></span>

<span data-ttu-id="0f3ff-243">Příkaz</span><span class="sxs-lookup"><span data-stu-id="0f3ff-243">Command</span></span> | <span data-ttu-id="0f3ff-244">Funkce</span><span class="sxs-lookup"><span data-stu-id="0f3ff-244">Function</span></span>
--- | ---
[<span data-ttu-id="0f3ff-245">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="0f3ff-245">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="0f3ff-246">Odstraní nebo zruší výpis balíčku ze serveru.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-246">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="0f3ff-247">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="0f3ff-247">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="0f3ff-248">Odešle balíček na server a publikuje ho.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-248">Pushes a package to the server and publishes it.</span></span>
[<span data-ttu-id="0f3ff-249">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="0f3ff-249">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="0f3ff-250">Vymaže nebo vypíše místní prostředky NuGet, jako je mezipaměť požadavků HTTP, dočasná mezipaměť nebo složka globálních balíčků v celém počítači.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-250">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="0f3ff-251">dotnet nuget add source</span><span class="sxs-lookup"><span data-stu-id="0f3ff-251">dotnet nuget add source</span></span>](dotnet-nuget-add-source.md) | <span data-ttu-id="0f3ff-252">Přidá zdroj NuGet.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-252">Adds a NuGet source.</span></span>
[<span data-ttu-id="0f3ff-253">dotnet nuget disable source</span><span class="sxs-lookup"><span data-stu-id="0f3ff-253">dotnet nuget disable source</span></span>](dotnet-nuget-disable-source.md) | <span data-ttu-id="0f3ff-254">Zakáže zdroj NuGet.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-254">Disables a NuGet source.</span></span>
[<span data-ttu-id="0f3ff-255">dotnet nuget enable source</span><span class="sxs-lookup"><span data-stu-id="0f3ff-255">dotnet nuget enable source</span></span>](dotnet-nuget-enable-source.md) | <span data-ttu-id="0f3ff-256">Povoluje zdroj NuGet.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-256">Enables a NuGet source.</span></span>
[<span data-ttu-id="0f3ff-257">dotnet nuget list source</span><span class="sxs-lookup"><span data-stu-id="0f3ff-257">dotnet nuget list source</span></span>](dotnet-nuget-list-source.md) | <span data-ttu-id="0f3ff-258">Zobrazí seznam všech nakonfigurovaných zdrojů NuGet.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-258">Lists all configured NuGet sources.</span></span>
[<span data-ttu-id="0f3ff-259">dotnet nuget remove source</span><span class="sxs-lookup"><span data-stu-id="0f3ff-259">dotnet nuget remove source</span></span>](dotnet-nuget-remove-source.md) | <span data-ttu-id="0f3ff-260">Odebere zdroj NuGet.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-260">Removes a NuGet source.</span></span>
[<span data-ttu-id="0f3ff-261">dotnet nuget update source</span><span class="sxs-lookup"><span data-stu-id="0f3ff-261">dotnet nuget update source</span></span>](dotnet-nuget-update-source.md) | <span data-ttu-id="0f3ff-262">Aktualizuje zdroj NuGet.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-262">Updates a NuGet source.</span></span>

### <a name="global-tool-path-and-local-tools-commands"></a><span data-ttu-id="0f3ff-263">Příkazy globálních nástrojů, nástrojů a cest a místních nástrojů</span><span class="sxs-lookup"><span data-stu-id="0f3ff-263">Global, tool-path, and local tools commands</span></span>

<span data-ttu-id="0f3ff-264">Nástroje jsou konzolové aplikace, které jsou nainstalovány z balíčků NuGet a jsou vyvolány z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-264">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="0f3ff-265">Můžete psát nástroje sami nebo instalovat nástroje napsané třetí stranou.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-265">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="0f3ff-266">Nástroje jsou také známé jako globální nástroje, nástroje pro cestu nástrojů a místní nástroje.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-266">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="0f3ff-267">Další informace najdete v tématu [Přehled nástrojů .NET Core](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="0f3ff-267">For more information, see [.NET Core tools overview](global-tools.md).</span></span> <span data-ttu-id="0f3ff-268">Nástroje pro globální a cestu nástrojů jsou k dispozici od .NET Core SDK 2,1.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-268">Global and tool-path tools are available starting with .NET Core SDK 2.1.</span></span> <span data-ttu-id="0f3ff-269">K dispozici jsou místní nástroje od .NET Core SDK 3,0.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-269">Local tools are available starting with .NET Core SDK 3.0.</span></span>

<span data-ttu-id="0f3ff-270">Příkaz</span><span class="sxs-lookup"><span data-stu-id="0f3ff-270">Command</span></span> | <span data-ttu-id="0f3ff-271">Funkce</span><span class="sxs-lookup"><span data-stu-id="0f3ff-271">Function</span></span>
--- | ---
[<span data-ttu-id="0f3ff-272">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="0f3ff-272">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="0f3ff-273">Nainstaluje nástroj na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-273">Installs a tool on your machine.</span></span>
[<span data-ttu-id="0f3ff-274">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="0f3ff-274">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="0f3ff-275">Zobrazí seznam všech nástrojů, které jsou aktuálně nainstalované na vašem počítači, na základě globálních nástrojů, nástrojů a cest.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-275">Lists all global, tool-path, or local tools currently installed on your machine.</span></span>
[<span data-ttu-id="0f3ff-276">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="0f3ff-276">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="0f3ff-277">Odinstaluje nástroj z počítače.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-277">Uninstalls a tool from your machine.</span></span>
[<span data-ttu-id="0f3ff-278">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="0f3ff-278">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="0f3ff-279">Aktualizuje nástroj, který je nainstalovaný na vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-279">Updates a tool that is installed on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="0f3ff-280">Další nástroje</span><span class="sxs-lookup"><span data-stu-id="0f3ff-280">Additional tools</span></span>

<span data-ttu-id="0f3ff-281">Počínaje .NET Core SDK 2.1.300 je teď k dispozici několik nástrojů, které byly k dispozici pouze pro jednotlivé projekty pomocí, `DotnetCliToolReference` jako součást .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-281">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="0f3ff-282">Tyto nástroje jsou uvedené v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="0f3ff-282">These tools are listed in the following table:</span></span>

| <span data-ttu-id="0f3ff-283">Nástroj</span><span class="sxs-lookup"><span data-stu-id="0f3ff-283">Tool</span></span>                                              | <span data-ttu-id="0f3ff-284">Funkce</span><span class="sxs-lookup"><span data-stu-id="0f3ff-284">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="0f3ff-285">vývoj – certifikáty</span><span class="sxs-lookup"><span data-stu-id="0f3ff-285">dev-certs</span></span>                                         | <span data-ttu-id="0f3ff-286">Vytvoří a spravuje vývojové certifikáty.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-286">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="0f3ff-287">EF</span><span class="sxs-lookup"><span data-stu-id="0f3ff-287">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="0f3ff-288">Entity Framework Core nástroje příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-288">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="0f3ff-289">SQL – mezipaměť</span><span class="sxs-lookup"><span data-stu-id="0f3ff-289">sql-cache</span></span>                                         | <span data-ttu-id="0f3ff-290">Nástroje příkazového řádku pro SQL Server cache</span><span class="sxs-lookup"><span data-stu-id="0f3ff-290">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="0f3ff-291">uživatel – tajné klíče</span><span class="sxs-lookup"><span data-stu-id="0f3ff-291">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="0f3ff-292">Spravuje tajné klíče uživatele.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-292">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="0f3ff-293">sledovací</span><span class="sxs-lookup"><span data-stu-id="0f3ff-293">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="0f3ff-294">Spustí sledovací proces souborů, který spustí příkaz, když se soubory změní.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-294">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="0f3ff-295">Další informace o jednotlivých nástrojích získáte tak, že zadáte `dotnet <tool-name> --help` .</span><span class="sxs-lookup"><span data-stu-id="0f3ff-295">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="0f3ff-296">Příklady</span><span class="sxs-lookup"><span data-stu-id="0f3ff-296">Examples</span></span>

<span data-ttu-id="0f3ff-297">Vytvořte novou konzolovou aplikaci .NET Core:</span><span class="sxs-lookup"><span data-stu-id="0f3ff-297">Create a new .NET Core console application:</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="0f3ff-298">Sestavení projektu a jeho závislostí v daném adresáři:</span><span class="sxs-lookup"><span data-stu-id="0f3ff-298">Build a project and its dependencies in a given directory:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="0f3ff-299">Spuštění aplikace:</span><span class="sxs-lookup"><span data-stu-id="0f3ff-299">Run an application:</span></span>

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a><span data-ttu-id="0f3ff-300">Proměnné prostředí</span><span class="sxs-lookup"><span data-stu-id="0f3ff-300">Environment variables</span></span>

- <span data-ttu-id="0f3ff-301">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span><span class="sxs-lookup"><span data-stu-id="0f3ff-301">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span></span>

  <span data-ttu-id="0f3ff-302">Určuje umístění modulů runtime .NET Core, pokud nejsou nainstalovány ve výchozím umístění.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-302">Specifies the location of the .NET Core runtimes, if they are not installed in the default location.</span></span> <span data-ttu-id="0f3ff-303">Výchozí umístění ve Windows je `C:\Program Files\dotnet` .</span><span class="sxs-lookup"><span data-stu-id="0f3ff-303">The default location on Windows is `C:\Program Files\dotnet`.</span></span> <span data-ttu-id="0f3ff-304">Výchozí umístění v systémech Linux a macOS je `/usr/share/dotnet` .</span><span class="sxs-lookup"><span data-stu-id="0f3ff-304">The default location on Linux and macOS is `/usr/share/dotnet`.</span></span> <span data-ttu-id="0f3ff-305">Tato proměnná prostředí se používá jenom při spouštění aplikací prostřednictvím generovaných spustitelných souborů (apphosts).</span><span class="sxs-lookup"><span data-stu-id="0f3ff-305">This environment variable is used only when running apps via generated executables (apphosts).</span></span> <span data-ttu-id="0f3ff-306">`DOTNET_ROOT(x86)`se používá místo toho, když je spuštěný 32 spustitelný soubor na 64 operačním systému.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-306">`DOTNET_ROOT(x86)` is used instead when running a 32-bit executable on a 64-bit OS.</span></span>

- `DOTNET_PACKAGES`

  <span data-ttu-id="0f3ff-307">Složka globálních balíčků.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-307">The global packages folder.</span></span> <span data-ttu-id="0f3ff-308">Pokud není nastavená, použije se `~/.nuget/packages` ve výchozím nastavení v systému UNIX nebo `%userprofile%\.nuget\packages` Windows.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-308">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

- `DOTNET_SERVICING`

  <span data-ttu-id="0f3ff-309">Určuje umístění indexu údržby používaného sdíleným hostitelem při načítání modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-309">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

- `DOTNET_NOLOGO`

  <span data-ttu-id="0f3ff-310">Určuje, jestli se při prvním spuštění zobrazují zprávy Welcome a telemetrie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-310">Specifies whether .NET Core welcome and telemetry messages are displayed on first run.</span></span> <span data-ttu-id="0f3ff-311">Nastavte na `true` ztlumení těchto zpráv (hodnoty `true` , `1` nebo `yes` přijmout), nebo nastavte na hodnotu `false` Povolit (hodnoty `false` , `0` nebo `no` přijmout).</span><span class="sxs-lookup"><span data-stu-id="0f3ff-311">Set to `true` to mute these messages (values `true`, `1`, or `yes` accepted) or set to `false` to allow (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="0f3ff-312">Pokud není nastavená, použije se výchozí nastavení `false` a zprávy se zobrazí při prvním spuštění.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-312">If not set, the default is `false` and the messages will be displayed on first run.</span></span> <span data-ttu-id="0f3ff-313">Tento příznak nemá žádný vliv na telemetrii (viz `DOTNET_CLI_TELEMETRY_OPTOUT` pro odsouhlasení z odesílající telemetrie).</span><span class="sxs-lookup"><span data-stu-id="0f3ff-313">This flag has no effect on telemetry (see `DOTNET_CLI_TELEMETRY_OPTOUT` for opting out of sending telemetry).</span></span>

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  <span data-ttu-id="0f3ff-314">Určuje, jestli se data o využití nástrojů .NET Core shromažďují a odesílají do Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-314">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="0f3ff-315">Nastavte na `true` výslovný souhlas funkce telemetrie (hodnoty `true` , `1` nebo `yes` přijmout).</span><span class="sxs-lookup"><span data-stu-id="0f3ff-315">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="0f3ff-316">V opačném případě nastavte, aby se `false` přihlásil k funkcím telemetrie (hodnoty `false` , `0` nebo `no` přijaty).</span><span class="sxs-lookup"><span data-stu-id="0f3ff-316">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="0f3ff-317">Pokud není nastavená, je výchozí nastavení `false` a funkce telemetrie je aktivní.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-317">If not set, the default is `false` and the telemetry feature is active.</span></span>

- `DOTNET_MULTILEVEL_LOOKUP`

  <span data-ttu-id="0f3ff-318">Určuje, zda je rozhraní .NET Core Runtime, sdílené rozhraní nebo sada SDK vyřešeno z globálního umístění.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-318">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="0f3ff-319">Pokud není nastavené, použije se výchozí hodnota 1 (logická `true` ).</span><span class="sxs-lookup"><span data-stu-id="0f3ff-319">If not set, it defaults to 1 (logical `true`).</span></span> <span data-ttu-id="0f3ff-320">Nastavte na 0 (logický `false` ), aby se nepřeložily z globálního umístění a měly izolované instalace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-320">Set to 0 (logical `false`) to not resolve from the global location and have isolated .NET Core installations.</span></span> <span data-ttu-id="0f3ff-321">Další informace o vyhledávání na více úrovních najdete v tématu [SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="0f3ff-321">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

- <span data-ttu-id="0f3ff-322">`DOTNET_ROLL_FORWARD`**K dispozici počínaje rozhraním .NET Core 3. x.**</span><span class="sxs-lookup"><span data-stu-id="0f3ff-322">`DOTNET_ROLL_FORWARD` **Available starting with .NET Core 3.x.**</span></span>

  <span data-ttu-id="0f3ff-323">Určuje chování při posunu nahoru.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-323">Determines roll forward behavior.</span></span> <span data-ttu-id="0f3ff-324">Další informace najdete v části `--roll-forward` výše v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-324">For more information, see the `--roll-forward` option earlier in this article.</span></span>

- <span data-ttu-id="0f3ff-325">`DOTNET_ROLL_FORWARD_TO_PRERELEASE`**K dispozici počínaje rozhraním .NET Core 3. x.**</span><span class="sxs-lookup"><span data-stu-id="0f3ff-325">`DOTNET_ROLL_FORWARD_TO_PRERELEASE` **Available starting with .NET Core 3.x.**</span></span>

  <span data-ttu-id="0f3ff-326">Pokud je nastaveno na `1` (povoleno), povolí návrat k předběžnému vydání verze z vydané verze.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-326">If set to `1` (enabled), enables rolling forward to a pre-release version from a release version.</span></span> <span data-ttu-id="0f3ff-327">Ve výchozím nastavení ( `0` -zakázáno) platí, že pokud je vyžadovaná vydaná verze modulu runtime .NET Core, znamená to, že je k dispozici jenom nainstalovaná verze Release.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-327">By default (`0` - disabled), when a release version of .NET Core runtime is requested, roll-forward will only consider installed release versions.</span></span>

  <span data-ttu-id="0f3ff-328">Další informace najdete v tématu o tom, jak [Posunout](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward)nahoru.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-328">For more information, see [Roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span></span>

- <span data-ttu-id="0f3ff-329">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`**K dispozici v .NET Core 2. x.**</span><span class="sxs-lookup"><span data-stu-id="0f3ff-329">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **Available in .NET Core 2.x.**</span></span>

  <span data-ttu-id="0f3ff-330">Zakáže posunutí dílčí verze, pokud je nastaveno na `0` .</span><span class="sxs-lookup"><span data-stu-id="0f3ff-330">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="0f3ff-331">Další informace najdete v tématu o tom, jak [Posunout](../whats-new/dotnet-core-2-1.md#roll-forward)nahoru.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-331">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

  <span data-ttu-id="0f3ff-332">Toto nastavení nahrazuje rozhraní .NET Core 3,0 podle `DOTNET_ROLL_FORWARD` .</span><span class="sxs-lookup"><span data-stu-id="0f3ff-332">This setting is superseded in .NET Core 3.0 by `DOTNET_ROLL_FORWARD`.</span></span> <span data-ttu-id="0f3ff-333">Místo toho by se mělo použít nové nastavení.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-333">The new settings should be used instead.</span></span>

- `DOTNET_CLI_UI_LANGUAGE`

  <span data-ttu-id="0f3ff-334">Nastaví jazyk uživatelského rozhraní CLI pomocí hodnoty národního prostředí, například `en-us` .</span><span class="sxs-lookup"><span data-stu-id="0f3ff-334">Sets the language of the CLI UI using a locale value such as `en-us`.</span></span> <span data-ttu-id="0f3ff-335">Podporované hodnoty jsou stejné jako u sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-335">The supported values are the same as for Visual Studio.</span></span> <span data-ttu-id="0f3ff-336">Další informace najdete v části o změně jazyka instalačního programu v [dokumentaci k instalaci sady Visual Studio](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019).</span><span class="sxs-lookup"><span data-stu-id="0f3ff-336">For more information, see the section on changing the installer language in the [Visual Studio installation documentation](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019).</span></span> <span data-ttu-id="0f3ff-337">Použijí se pravidla správce prostředků .NET, takže nemusíte vybírat přesnou shodu, &mdash; můžete také vybrat následníky ve `CultureInfo` stromové struktuře.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-337">The .NET resource manager rules apply, so you don't have to pick an exact match&mdash;you can also pick descendants in the `CultureInfo` tree.</span></span> <span data-ttu-id="0f3ff-338">Například pokud nastavíte na `fr-CA` , rozhraní příkazového řádku nalezne a použije `fr` překlady.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-338">For example, if you set it to `fr-CA`, the CLI will find and use the `fr` translations.</span></span> <span data-ttu-id="0f3ff-339">Pokud ho nastavíte na jazyk, který není podporován, rozhraní příkazového řádku se vrátí do angličtiny.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-339">If you set it to a language that is not supported, the CLI falls back to English.</span></span>

- `DOTNET_DISABLE_GUI_ERRORS`

  <span data-ttu-id="0f3ff-340">V případě generovaných spustitelných souborů s povoleným grafickým uživatelským rozhraním – zakáže dialogová okna, která obvykle zobrazuje určité třídy chyb.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-340">For GUI-enabled generated executables - disables dialog popup, which normally shows for certain classes of errors.</span></span> <span data-ttu-id="0f3ff-341">`stderr`V těchto případech zapisuje a ukončuje se.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-341">It only writes to `stderr` and exits in those cases.</span></span>
  
- `DOTNET_ADDITIONAL_DEPS`

  <span data-ttu-id="0f3ff-342">Ekvivalent možnosti CLI `--additional-deps` .</span><span class="sxs-lookup"><span data-stu-id="0f3ff-342">Equivalent to CLI option `--additional-deps`.</span></span>

- `DOTNET_RUNTIME_ID`

  <span data-ttu-id="0f3ff-343">Přepíše zjištěný identifikátor RID.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-343">Overrides the detected RID.</span></span>

- `DOTNET_SHARED_STORE`

  <span data-ttu-id="0f3ff-344">Umístění sdíleného úložiště, na které se rozlišení sestavení vrátí v některých případech.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-344">Location of the "shared store" which assembly resolution falls back to in some cases.</span></span>

- `DOTNET_STARTUP_HOOKS`

  <span data-ttu-id="0f3ff-345">Seznam sestavení pro načtení a spuštění spouštěcích háky z.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-345">List of assemblies to load and execute startup hooks from.</span></span>

- <span data-ttu-id="0f3ff-346">`DOTNET_BUNDLE_EXTRACT_BASE_DIR`**K dispozici počínaje rozhraním .NET Core 3. x.**</span><span class="sxs-lookup"><span data-stu-id="0f3ff-346">`DOTNET_BUNDLE_EXTRACT_BASE_DIR` **Available starting with .NET Core 3.x.**</span></span>

  <span data-ttu-id="0f3ff-347">Určuje adresář, do kterého se extrahuje aplikace s jedním souborem, než se spustí.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-347">Specifies a directory to which a single-file application is extracted before it is executed.</span></span>

  <span data-ttu-id="0f3ff-348">Další informace najdete v tématu [spustitelné soubory s jedním souborem](../whats-new/dotnet-core-3-0.md#single-file-executables).</span><span class="sxs-lookup"><span data-stu-id="0f3ff-348">For more information, see [Single-file executables](../whats-new/dotnet-core-3-0.md#single-file-executables).</span></span>

- <span data-ttu-id="0f3ff-349">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span><span class="sxs-lookup"><span data-stu-id="0f3ff-349">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span></span>

  <span data-ttu-id="0f3ff-350">Řídí trasování diagnostiky z komponent hostování, například `dotnet.exe` , `hostfxr` a `hostpolicy` .</span><span class="sxs-lookup"><span data-stu-id="0f3ff-350">Controls diagnostics tracing from the hosting components, such as `dotnet.exe`, `hostfxr`, and `hostpolicy`.</span></span>

  * <span data-ttu-id="0f3ff-351">`COREHOST_TRACE=[0/1]`-Defaulted `0` -Tracing Disabled.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-351">`COREHOST_TRACE=[0/1]` - default is `0` - tracing disabled.</span></span> <span data-ttu-id="0f3ff-352">Pokud je nastaveno na `1` , trasování diagnostiky je povoleno.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-352">If set to `1`, diagnostics tracing is enabled.</span></span>
  * <span data-ttu-id="0f3ff-353">`COREHOST_TRACEFILE=<file path>`-má vliv, pokud je povoleno trasování prostřednictvím `COREHOST_TRACE=1` .</span><span class="sxs-lookup"><span data-stu-id="0f3ff-353">`COREHOST_TRACEFILE=<file path>` - only has effect if tracing is enabled via `COREHOST_TRACE=1`.</span></span> <span data-ttu-id="0f3ff-354">Při nastavení se trasovací informace zapisují do zadaného souboru, jinak se do něj zapisují trasovací informace `stderr` .</span><span class="sxs-lookup"><span data-stu-id="0f3ff-354">When set, the tracing information is written to the specified file, otherwise the tracing information is written to `stderr`.</span></span> <span data-ttu-id="0f3ff-355">**K dispozici počínaje rozhraním .NET Core 3. x.**</span><span class="sxs-lookup"><span data-stu-id="0f3ff-355">**Available starting with .NET Core 3.x.**</span></span>
  * <span data-ttu-id="0f3ff-356">`COREHOST_TRACE_VERBOSITY=[1/2/3/4]`– Výchozí hodnota je `4` .</span><span class="sxs-lookup"><span data-stu-id="0f3ff-356">`COREHOST_TRACE_VERBOSITY=[1/2/3/4]` - default is `4`.</span></span> <span data-ttu-id="0f3ff-357">Toto nastavení se používá pouze v případě, že je povoleno trasování prostřednictvím `COREHOST_TRACE=1` .</span><span class="sxs-lookup"><span data-stu-id="0f3ff-357">The setting is used only when tracing is enabled via `COREHOST_TRACE=1`.</span></span> <span data-ttu-id="0f3ff-358">**K dispozici počínaje rozhraním .NET Core 3. x.**</span><span class="sxs-lookup"><span data-stu-id="0f3ff-358">**Available starting with .NET Core 3.x.**</span></span>
    * <span data-ttu-id="0f3ff-359">`4`– zapisují se všechny informace o trasování.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-359">`4` - all tracing information is written</span></span>
    * <span data-ttu-id="0f3ff-360">`3`– zapisují se jenom informativní, varovné a chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-360">`3` - only informational, warning and error messages are written</span></span>
    * <span data-ttu-id="0f3ff-361">`2`– zapíší se jenom upozornění a chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-361">`2` - only warning and error messages are written</span></span>
    * <span data-ttu-id="0f3ff-362">`1`-jsou zapsány pouze chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-362">`1` - only error messages are written</span></span>

  <span data-ttu-id="0f3ff-363">Typický způsob, jak získat podrobné informace o trasování o spuštění aplikace, je nastavit `COREHOST_TRACE=1` a `COREHOST_TRACEFILE=host_trace.txt` následně spustit aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-363">The typical way to get detailed trace information about application startup is to set `COREHOST_TRACE=1` and `COREHOST_TRACEFILE=host_trace.txt` and then run the application.</span></span> <span data-ttu-id="0f3ff-364">V aktuálním adresáři se vytvoří nový soubor `host_trace.txt` s podrobnými informacemi.</span><span class="sxs-lookup"><span data-stu-id="0f3ff-364">A new file `host_trace.txt` will be created in the current directory with the detailed information.</span></span>

## <a name="see-also"></a><span data-ttu-id="0f3ff-365">Viz také</span><span class="sxs-lookup"><span data-stu-id="0f3ff-365">See also</span></span>

- [<span data-ttu-id="0f3ff-366">Běhové konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="0f3ff-366">Runtime Configuration Files</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [<span data-ttu-id="0f3ff-367">Nastavení konfigurace runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="0f3ff-367">.NET Core run-time configuration settings</span></span>](../run-time-config/index.md)
