---
title: dotnet – příkaz
description: Přečtěte si o příkazu dotnet (obecný ovladač pro .NET Core CLI nástroje) a jeho využití.
ms.date: 06/04/2018
ms.openlocfilehash: 801320bf7f3527ac70f1d5b9fe3d0ce537e50e93
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969780"
---
# <a name="dotnet-command"></a><span data-ttu-id="148cd-103">dotnet – příkaz</span><span class="sxs-lookup"><span data-stu-id="148cd-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="148cd-104">Name</span><span class="sxs-lookup"><span data-stu-id="148cd-104">Name</span></span>

<span data-ttu-id="148cd-105">`dotnet`– Nástroj pro správu zdrojového kódu a binárních souborů .NET.</span><span class="sxs-lookup"><span data-stu-id="148cd-105">`dotnet` - A tool for managing .NET source code and binaries.</span></span>

## <a name="synopsis"></a><span data-ttu-id="148cd-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="148cd-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="148cd-107">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="148cd-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="148cd-108">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="148cd-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx]
    [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="148cd-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="148cd-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet [command] [arguments] [--additionalprobingpath] [--depsfile] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--runtimeconfig] [-v|--verbosity] [--version]
```

---

## <a name="description"></a><span data-ttu-id="148cd-110">Popis</span><span class="sxs-lookup"><span data-stu-id="148cd-110">Description</span></span>

<span data-ttu-id="148cd-111">`dotnet`je nástroj pro správu zdrojového kódu a binárních souborů .NET.</span><span class="sxs-lookup"><span data-stu-id="148cd-111">`dotnet` is a tool for managing .NET source code and binaries.</span></span> <span data-ttu-id="148cd-112">Zpřístupňuje příkazy, které provádějí konkrétní úkoly, [`dotnet build`](dotnet-build.md) jako například a. [`dotnet run`](dotnet-run.md)</span><span class="sxs-lookup"><span data-stu-id="148cd-112">It exposes commands that perform specific tasks, such as [`dotnet build`](dotnet-build.md) and [`dotnet run`](dotnet-run.md).</span></span> <span data-ttu-id="148cd-113">Každý příkaz definuje své vlastní argumenty.</span><span class="sxs-lookup"><span data-stu-id="148cd-113">Each command defines its own arguments.</span></span> <span data-ttu-id="148cd-114">Typ `--help` za každým příkazem pro přístup k krátké dokumentaci k nápovědě.</span><span class="sxs-lookup"><span data-stu-id="148cd-114">Type `--help` after each command to access brief help documentation.</span></span>

<span data-ttu-id="148cd-115">`dotnet`lze použít ke spouštění aplikací zadáním knihovny DLL aplikace, například `dotnet myapp.dll`.</span><span class="sxs-lookup"><span data-stu-id="148cd-115">`dotnet` can be used to run applications, by specifying an application DLL, such as `dotnet myapp.dll`.</span></span> <span data-ttu-id="148cd-116">Další informace o možnostech nasazení najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md) .</span><span class="sxs-lookup"><span data-stu-id="148cd-116">See [.NET Core application deployment](../deploying/index.md) for to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="148cd-117">Možnosti</span><span class="sxs-lookup"><span data-stu-id="148cd-117">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="148cd-118">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="148cd-118">.NET Core 2.1</span></span>](#tab/netcore21)

`--additional-deps <PATH>`

<span data-ttu-id="148cd-119">Cesta k dodatečnému souboru *. DEPS. JSON* .</span><span class="sxs-lookup"><span data-stu-id="148cd-119">Path to an additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="148cd-120">Cesta obsahující zásady a sestavení pro zjišťování k testování</span><span class="sxs-lookup"><span data-stu-id="148cd-120">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="148cd-121">Cesta k souboru *DEPS. JSON* .</span><span class="sxs-lookup"><span data-stu-id="148cd-121">Path to a *deps.json* file.</span></span>

<span data-ttu-id="148cd-122">Soubor *DEPS. JSON* obsahuje seznam závislostí, závislosti kompilace a informace o verzi používané k řešení konfliktů sestavení.</span><span class="sxs-lookup"><span data-stu-id="148cd-122">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="148cd-123">Další informace o tomto souboru najdete v tématu [běhové konfigurační soubory](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="148cd-123">For more information about this file, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

`-d|--diagnostics`

<span data-ttu-id="148cd-124">Povolí výstup diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="148cd-124">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="148cd-125">Verze modulu runtime .NET Core, která se má použít ke spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="148cd-125">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="148cd-126">Vytiskne dokumentaci pro daný příkaz, například `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="148cd-126">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="148cd-127">`dotnet --help`vytiskne seznam dostupných příkazů.</span><span class="sxs-lookup"><span data-stu-id="148cd-127">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="148cd-128">Vytiskne podrobné informace o instalaci .NET Core a počítačovém prostředí, jako je aktuální operační systém, a potvrzení SHA verze .NET Core.</span><span class="sxs-lookup"><span data-stu-id="148cd-128">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--list-runtimes`

<span data-ttu-id="148cd-129">Zobrazí nainstalované moduly runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="148cd-129">Displays the installed .NET Core runtimes.</span></span>

`--list-sdks`

<span data-ttu-id="148cd-130">Zobrazí nainstalované sady SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="148cd-130">Displays the installed .NET Core SDKs.</span></span>

`--roll-forward-on-no-candidate-fx <N>`

<span data-ttu-id="148cd-131">Definuje chování v případě, že požadovaná sdílená architektura není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="148cd-131">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="148cd-132">`N` může být:</span><span class="sxs-lookup"><span data-stu-id="148cd-132">`N` can be:</span></span>

- <span data-ttu-id="148cd-133">`0`– Zakažte u sebe i menší verzi.</span><span class="sxs-lookup"><span data-stu-id="148cd-133">`0` - Disable even minor version roll forward.</span></span>
- <span data-ttu-id="148cd-134">`1`– Navýšení se dopředá na podverzi, ale ne na hlavní verzi.</span><span class="sxs-lookup"><span data-stu-id="148cd-134">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="148cd-135">Toto je výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="148cd-135">This is the default behavior.</span></span>
- <span data-ttu-id="148cd-136">`2`– Posunutí posunu k dílčím a hlavním verzím</span><span class="sxs-lookup"><span data-stu-id="148cd-136">`2` - Roll forward on minor and major versions.</span></span>

 <span data-ttu-id="148cd-137">Další informace najdete v tématu o tom, jak [Posunout](../whats-new/dotnet-core-2-1.md#roll-forward)nahoru.</span><span class="sxs-lookup"><span data-stu-id="148cd-137">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`--runtimeconfig`

<span data-ttu-id="148cd-138">Cesta k souboru *runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="148cd-138">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="148cd-139">Soubor *runtimeconfig. JSON* je konfigurační soubor obsahující konfigurační nastavení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="148cd-139">A *runtimeconfig.json* file is a configuration file containing runtime configuration settings.</span></span> <span data-ttu-id="148cd-140">Další informace najdete v tématu [běhové konfigurační soubory](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="148cd-140">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="148cd-141">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="148cd-141">Sets the verbosity level of the command.</span></span> <span data-ttu-id="148cd-142">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]` `d[etailed]`, a .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="148cd-142">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="148cd-143">Nepodporováno v každém příkazu; Pokud chcete zjistit, zda je tato možnost k dispozici, zobrazte konkrétní příkazová stránka.</span><span class="sxs-lookup"><span data-stu-id="148cd-143">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="148cd-144">Vytiskne verzi .NET Core SDK, která se používá.</span><span class="sxs-lookup"><span data-stu-id="148cd-144">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="148cd-145">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="148cd-145">.NET Core 2.0</span></span>](#tab/netcore20)

`--additional-deps <PATH>`

<span data-ttu-id="148cd-146">Cesta k dodatečnému souboru *. DEPS. JSON* .</span><span class="sxs-lookup"><span data-stu-id="148cd-146">Path to an additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="148cd-147">Cesta obsahující zásady a sestavení pro zjišťování k testování</span><span class="sxs-lookup"><span data-stu-id="148cd-147">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="148cd-148">Cesta k souboru *DEPS. JSON* .</span><span class="sxs-lookup"><span data-stu-id="148cd-148">Path to a *deps.json* file.</span></span>

<span data-ttu-id="148cd-149">Soubor *DEPS. JSON* obsahuje seznam závislostí, závislosti kompilace a informace o verzi používané k řešení konfliktů sestavení.</span><span class="sxs-lookup"><span data-stu-id="148cd-149">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="148cd-150">Další podrobnosti o tomto souboru najdete v tématu [běhové konfigurační soubory na GitHubu](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="148cd-150">For more details on this file, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-d|--diagnostics`

<span data-ttu-id="148cd-151">Povolí výstup diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="148cd-151">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="148cd-152">Verze modulu runtime .NET Core, která se má použít ke spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="148cd-152">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="148cd-153">Vytiskne dokumentaci pro daný příkaz, například `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="148cd-153">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="148cd-154">`dotnet --help`vytiskne seznam dostupných příkazů.</span><span class="sxs-lookup"><span data-stu-id="148cd-154">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="148cd-155">Vytiskne podrobné informace o instalaci .NET Core a počítačovém prostředí, jako je aktuální operační systém, a potvrzení SHA verze .NET Core.</span><span class="sxs-lookup"><span data-stu-id="148cd-155">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="148cd-156">Zakáže posunutí dílčí verze, pokud je nastaveno `0`na.</span><span class="sxs-lookup"><span data-stu-id="148cd-156">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="148cd-157">Další informace najdete v tématu o tom, jak [Posunout](../whats-new/dotnet-core-2-1.md#roll-forward)nahoru.</span><span class="sxs-lookup"><span data-stu-id="148cd-157">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`--runtimeconfig`

<span data-ttu-id="148cd-158">Cesta k souboru *runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="148cd-158">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="148cd-159">Soubor *runtimeconfig. JSON* je konfigurační soubor obsahující konfigurační nastavení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="148cd-159">A *runtimeconfig.json* file is a configuration file containing runtime configuration settings.</span></span> <span data-ttu-id="148cd-160">Další podrobnosti najdete v tématu [běhové konfigurační soubory na GitHubu](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="148cd-160">For more details, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="148cd-161">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="148cd-161">Sets the verbosity level of the command.</span></span> <span data-ttu-id="148cd-162">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]` `d[etailed]`, a .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="148cd-162">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="148cd-163">Nepodporováno v každém příkazu; Pokud chcete zjistit, zda je tato možnost k dispozici, zobrazte konkrétní příkazová stránka.</span><span class="sxs-lookup"><span data-stu-id="148cd-163">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="148cd-164">Vytiskne verzi .NET Core SDK, která se používá.</span><span class="sxs-lookup"><span data-stu-id="148cd-164">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="148cd-165">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="148cd-165">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="148cd-166">Cesta obsahující zásady a sestavení pro zjišťování k testování</span><span class="sxs-lookup"><span data-stu-id="148cd-166">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="148cd-167">Cesta k souboru *DEPS. JSON* .</span><span class="sxs-lookup"><span data-stu-id="148cd-167">Path to a *deps.json* file.</span></span>

<span data-ttu-id="148cd-168">Soubor *DEPS. JSON* obsahuje seznam závislostí, závislosti kompilace a informace o verzi používané k řešení konfliktů sestavení.</span><span class="sxs-lookup"><span data-stu-id="148cd-168">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="148cd-169">Další podrobnosti o tomto souboru najdete v tématu [běhové konfigurační soubory na GitHubu](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="148cd-169">For more details on this file, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-d|--diagnostics`

<span data-ttu-id="148cd-170">Povolí výstup diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="148cd-170">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="148cd-171">Verze modulu runtime .NET Core, která se má použít ke spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="148cd-171">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="148cd-172">Vytiskne dokumentaci pro daný příkaz, například `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="148cd-172">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="148cd-173">`dotnet --help`vytiskne seznam dostupných příkazů.</span><span class="sxs-lookup"><span data-stu-id="148cd-173">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="148cd-174">Vytiskne podrobné informace o instalaci .NET Core a počítačovém prostředí, jako je aktuální operační systém, a potvrzení SHA verze .NET Core.</span><span class="sxs-lookup"><span data-stu-id="148cd-174">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--runtimeconfig`

<span data-ttu-id="148cd-175">Cesta k souboru *runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="148cd-175">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="148cd-176">Soubor *runtimeconfig. JSON* je konfigurační soubor obsahující konfigurační nastavení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="148cd-176">A *runtimeconfig.json* file is a configuration file containing runtime configuration settings.</span></span> <span data-ttu-id="148cd-177">Další podrobnosti najdete v tématu [běhové konfigurační soubory na GitHubu](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="148cd-177">For more details, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="148cd-178">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="148cd-178">Sets the verbosity level of the command.</span></span> <span data-ttu-id="148cd-179">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]` `d[etailed]`, a .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="148cd-179">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="148cd-180">Nepodporováno v každém příkazu; Pokud chcete zjistit, zda je tato možnost k dispozici, zobrazte konkrétní příkazová stránka.</span><span class="sxs-lookup"><span data-stu-id="148cd-180">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="148cd-181">Vytiskne verzi .NET Core SDK, která se používá.</span><span class="sxs-lookup"><span data-stu-id="148cd-181">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="148cd-182">Příkazy dotnet</span><span class="sxs-lookup"><span data-stu-id="148cd-182">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="148cd-183">Obecné</span><span class="sxs-lookup"><span data-stu-id="148cd-183">General</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="148cd-184">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="148cd-184">.NET Core 2.1</span></span>](#tab/netcore21)

| <span data-ttu-id="148cd-185">Příkaz</span><span class="sxs-lookup"><span data-stu-id="148cd-185">Command</span></span>                                       | <span data-ttu-id="148cd-186">Funkce</span><span class="sxs-lookup"><span data-stu-id="148cd-186">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="148cd-187">dotnet build</span><span class="sxs-lookup"><span data-stu-id="148cd-187">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="148cd-188">Vytvoří aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="148cd-188">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="148cd-189">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="148cd-189">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="148cd-190">Komunikuje se servery spuštěnými sestavením.</span><span class="sxs-lookup"><span data-stu-id="148cd-190">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="148cd-191">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="148cd-191">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="148cd-192">Vyčistit výstupy sestavení.</span><span class="sxs-lookup"><span data-stu-id="148cd-192">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="148cd-193">dotnet help</span><span class="sxs-lookup"><span data-stu-id="148cd-193">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="148cd-194">Zobrazí podrobnější dokumentaci pro příkaz online.</span><span class="sxs-lookup"><span data-stu-id="148cd-194">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="148cd-195">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="148cd-195">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="148cd-196">Migruje platný projekt verze Preview 2 na projekt .NET Core SDK 1,0.</span><span class="sxs-lookup"><span data-stu-id="148cd-196">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="148cd-197">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="148cd-197">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="148cd-198">Poskytuje přístup k příkazovému řádku MSBuild.</span><span class="sxs-lookup"><span data-stu-id="148cd-198">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="148cd-199">dotnet new</span><span class="sxs-lookup"><span data-stu-id="148cd-199">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="148cd-200">Inicializuje projekt C# nebo F# pro danou šablonu.</span><span class="sxs-lookup"><span data-stu-id="148cd-200">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="148cd-201">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="148cd-201">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="148cd-202">Vytvoří balíček NuGet vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="148cd-202">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="148cd-203">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="148cd-203">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="148cd-204">Publikuje aplikaci závislou na rozhraní .NET Framework nebo samostatnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="148cd-204">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="148cd-205">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="148cd-205">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="148cd-206">Obnoví závislosti pro danou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="148cd-206">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="148cd-207">dotnet run</span><span class="sxs-lookup"><span data-stu-id="148cd-207">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="148cd-208">Spustí aplikaci ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="148cd-208">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="148cd-209">dotnet run</span><span class="sxs-lookup"><span data-stu-id="148cd-209">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="148cd-210">Možnosti pro přidání, odebrání a výpis projektů v souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="148cd-210">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="148cd-211">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="148cd-211">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="148cd-212">Ukládá sestavení do úložiště balíčků modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="148cd-212">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="148cd-213">dotnet test</span><span class="sxs-lookup"><span data-stu-id="148cd-213">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="148cd-214">Spustí testy pomocí nástroje Test Runner.</span><span class="sxs-lookup"><span data-stu-id="148cd-214">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="148cd-215">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="148cd-215">.NET Core 2.0</span></span>](#tab/netcore20)

| <span data-ttu-id="148cd-216">Příkaz</span><span class="sxs-lookup"><span data-stu-id="148cd-216">Command</span></span>                             | <span data-ttu-id="148cd-217">Funkce</span><span class="sxs-lookup"><span data-stu-id="148cd-217">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="148cd-218">dotnet build</span><span class="sxs-lookup"><span data-stu-id="148cd-218">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="148cd-219">Vytvoří aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="148cd-219">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="148cd-220">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="148cd-220">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="148cd-221">Vyčistit výstupy sestavení.</span><span class="sxs-lookup"><span data-stu-id="148cd-221">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="148cd-222">dotnet help</span><span class="sxs-lookup"><span data-stu-id="148cd-222">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="148cd-223">Zobrazí podrobnější dokumentaci pro příkaz online.</span><span class="sxs-lookup"><span data-stu-id="148cd-223">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="148cd-224">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="148cd-224">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="148cd-225">Migruje platný projekt verze Preview 2 na projekt .NET Core SDK 1,0.</span><span class="sxs-lookup"><span data-stu-id="148cd-225">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="148cd-226">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="148cd-226">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="148cd-227">Poskytuje přístup k příkazovému řádku MSBuild.</span><span class="sxs-lookup"><span data-stu-id="148cd-227">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="148cd-228">dotnet new</span><span class="sxs-lookup"><span data-stu-id="148cd-228">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="148cd-229">Inicializuje projekt C# nebo F# pro danou šablonu.</span><span class="sxs-lookup"><span data-stu-id="148cd-229">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="148cd-230">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="148cd-230">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="148cd-231">Vytvoří balíček NuGet vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="148cd-231">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="148cd-232">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="148cd-232">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="148cd-233">Publikuje aplikaci závislou na rozhraní .NET Framework nebo samostatnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="148cd-233">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="148cd-234">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="148cd-234">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="148cd-235">Obnoví závislosti pro danou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="148cd-235">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="148cd-236">dotnet run</span><span class="sxs-lookup"><span data-stu-id="148cd-236">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="148cd-237">Spustí aplikaci ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="148cd-237">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="148cd-238">dotnet run</span><span class="sxs-lookup"><span data-stu-id="148cd-238">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="148cd-239">Možnosti pro přidání, odebrání a výpis projektů v souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="148cd-239">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="148cd-240">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="148cd-240">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="148cd-241">Ukládá sestavení do úložiště balíčků modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="148cd-241">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="148cd-242">dotnet test</span><span class="sxs-lookup"><span data-stu-id="148cd-242">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="148cd-243">Spustí testy pomocí nástroje Test Runner.</span><span class="sxs-lookup"><span data-stu-id="148cd-243">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="148cd-244">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="148cd-244">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="148cd-245">Příkaz</span><span class="sxs-lookup"><span data-stu-id="148cd-245">Command</span></span>                             | <span data-ttu-id="148cd-246">Funkce</span><span class="sxs-lookup"><span data-stu-id="148cd-246">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="148cd-247">dotnet build</span><span class="sxs-lookup"><span data-stu-id="148cd-247">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="148cd-248">Vytvoří aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="148cd-248">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="148cd-249">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="148cd-249">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="148cd-250">Vyčistit výstupy sestavení.</span><span class="sxs-lookup"><span data-stu-id="148cd-250">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="148cd-251">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="148cd-251">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="148cd-252">Migruje platný projekt verze Preview 2 na projekt .NET Core SDK 1,0.</span><span class="sxs-lookup"><span data-stu-id="148cd-252">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="148cd-253">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="148cd-253">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="148cd-254">Poskytuje přístup k příkazovému řádku MSBuild.</span><span class="sxs-lookup"><span data-stu-id="148cd-254">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="148cd-255">dotnet new</span><span class="sxs-lookup"><span data-stu-id="148cd-255">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="148cd-256">Inicializuje projekt C# nebo F# pro danou šablonu.</span><span class="sxs-lookup"><span data-stu-id="148cd-256">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="148cd-257">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="148cd-257">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="148cd-258">Vytvoří balíček NuGet vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="148cd-258">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="148cd-259">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="148cd-259">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="148cd-260">Publikuje aplikaci závislou na rozhraní .NET Framework nebo samostatnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="148cd-260">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="148cd-261">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="148cd-261">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="148cd-262">Obnoví závislosti pro danou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="148cd-262">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="148cd-263">dotnet run</span><span class="sxs-lookup"><span data-stu-id="148cd-263">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="148cd-264">Spustí aplikaci ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="148cd-264">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="148cd-265">dotnet run</span><span class="sxs-lookup"><span data-stu-id="148cd-265">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="148cd-266">Možnosti pro přidání, odebrání a výpis projektů v souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="148cd-266">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="148cd-267">dotnet test</span><span class="sxs-lookup"><span data-stu-id="148cd-267">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="148cd-268">Spustí testy pomocí nástroje Test Runner.</span><span class="sxs-lookup"><span data-stu-id="148cd-268">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="148cd-269">Odkazy na projekty</span><span class="sxs-lookup"><span data-stu-id="148cd-269">Project references</span></span>

<span data-ttu-id="148cd-270">Příkaz</span><span class="sxs-lookup"><span data-stu-id="148cd-270">Command</span></span> | <span data-ttu-id="148cd-271">Funkce</span><span class="sxs-lookup"><span data-stu-id="148cd-271">Function</span></span>
--- | ---
[<span data-ttu-id="148cd-272">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="148cd-272">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="148cd-273">Přidá odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="148cd-273">Adds a project reference.</span></span>
[<span data-ttu-id="148cd-274">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="148cd-274">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="148cd-275">Vypíše odkazy na projekt.</span><span class="sxs-lookup"><span data-stu-id="148cd-275">Lists project references.</span></span>
[<span data-ttu-id="148cd-276">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="148cd-276">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="148cd-277">Odebere odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="148cd-277">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="148cd-278">Balíčky NuGet</span><span class="sxs-lookup"><span data-stu-id="148cd-278">NuGet packages</span></span>

<span data-ttu-id="148cd-279">Příkaz</span><span class="sxs-lookup"><span data-stu-id="148cd-279">Command</span></span> | <span data-ttu-id="148cd-280">Funkce</span><span class="sxs-lookup"><span data-stu-id="148cd-280">Function</span></span>
--- | ---
[<span data-ttu-id="148cd-281">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="148cd-281">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="148cd-282">Přidá balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="148cd-282">Adds a NuGet package.</span></span>
[<span data-ttu-id="148cd-283">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="148cd-283">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="148cd-284">Odebere balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="148cd-284">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="148cd-285">Příkazy NuGet</span><span class="sxs-lookup"><span data-stu-id="148cd-285">NuGet commands</span></span>

<span data-ttu-id="148cd-286">Příkaz</span><span class="sxs-lookup"><span data-stu-id="148cd-286">Command</span></span> | <span data-ttu-id="148cd-287">Funkce</span><span class="sxs-lookup"><span data-stu-id="148cd-287">Function</span></span>
--- | ---
[<span data-ttu-id="148cd-288">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="148cd-288">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="148cd-289">Odstraní nebo zruší výpis balíčku ze serveru.</span><span class="sxs-lookup"><span data-stu-id="148cd-289">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="148cd-290">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="148cd-290">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="148cd-291">Vymaže nebo vypíše místní prostředky NuGet, jako je mezipaměť požadavků HTTP, dočasná mezipaměť nebo složka globálních balíčků v celém počítači.</span><span class="sxs-lookup"><span data-stu-id="148cd-291">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="148cd-292">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="148cd-292">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="148cd-293">Odešle balíček na server a publikuje ho.</span><span class="sxs-lookup"><span data-stu-id="148cd-293">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tools-commands"></a><span data-ttu-id="148cd-294">Příkazy globálních nástrojů</span><span class="sxs-lookup"><span data-stu-id="148cd-294">Global Tools commands</span></span>

<span data-ttu-id="148cd-295">K dispozici jsou [globální nástroje .NET Core](global-tools.md) od .NET Core SDK 2.1.300:</span><span class="sxs-lookup"><span data-stu-id="148cd-295">[.NET Core Global Tools](global-tools.md) are available starting with .NET Core SDK 2.1.300:</span></span>

<span data-ttu-id="148cd-296">Příkaz</span><span class="sxs-lookup"><span data-stu-id="148cd-296">Command</span></span> | <span data-ttu-id="148cd-297">Funkce</span><span class="sxs-lookup"><span data-stu-id="148cd-297">Function</span></span>
--- | ---
[<span data-ttu-id="148cd-298">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="148cd-298">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="148cd-299">Nainstaluje na váš počítač globální nástroj.</span><span class="sxs-lookup"><span data-stu-id="148cd-299">Installs a Global Tool on your machine.</span></span>
[<span data-ttu-id="148cd-300">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="148cd-300">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="148cd-301">Zobrazí seznam všech globálních nástrojů, které jsou aktuálně nainstalované ve výchozím adresáři na vašem počítači nebo v zadané cestě.</span><span class="sxs-lookup"><span data-stu-id="148cd-301">Lists all Global Tools currently installed in the default directory on your machine or in the specified path.</span></span>
[<span data-ttu-id="148cd-302">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="148cd-302">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="148cd-303">Odinstaluje z počítače globální nástroj.</span><span class="sxs-lookup"><span data-stu-id="148cd-303">Uninstalls a Global Tool from your machine.</span></span>
[<span data-ttu-id="148cd-304">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="148cd-304">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="148cd-305">Aktualizuje na svém počítači globální nástroj.</span><span class="sxs-lookup"><span data-stu-id="148cd-305">Updates a Global Tool on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="148cd-306">Další nástroje</span><span class="sxs-lookup"><span data-stu-id="148cd-306">Additional tools</span></span>

<span data-ttu-id="148cd-307">Počínaje .NET Core SDK 2.1.300 je teď k dispozici několik nástrojů, které byly k dispozici pouze pro jednotlivé `DotnetCliToolReference` projekty pomocí, jako součást .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="148cd-307">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="148cd-308">Tyto nástroje jsou uvedené v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="148cd-308">These tools are listed in the following table:</span></span>

| <span data-ttu-id="148cd-309">Nástroj</span><span class="sxs-lookup"><span data-stu-id="148cd-309">Tool</span></span>                                              | <span data-ttu-id="148cd-310">Funkce</span><span class="sxs-lookup"><span data-stu-id="148cd-310">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="148cd-311">vývoj – certifikáty</span><span class="sxs-lookup"><span data-stu-id="148cd-311">dev-certs</span></span>                                         | <span data-ttu-id="148cd-312">Vytvoří a spravuje vývojové certifikáty.</span><span class="sxs-lookup"><span data-stu-id="148cd-312">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="148cd-313">EF</span><span class="sxs-lookup"><span data-stu-id="148cd-313">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="148cd-314">Entity Framework Core nástroje příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="148cd-314">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="148cd-315">sql-cache</span><span class="sxs-lookup"><span data-stu-id="148cd-315">sql-cache</span></span>                                         | <span data-ttu-id="148cd-316">Nástroje příkazového řádku pro SQL Server cache</span><span class="sxs-lookup"><span data-stu-id="148cd-316">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="148cd-317">uživatel – tajné klíče</span><span class="sxs-lookup"><span data-stu-id="148cd-317">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="148cd-318">Spravuje tajné klíče uživatele.</span><span class="sxs-lookup"><span data-stu-id="148cd-318">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="148cd-319">sledovací</span><span class="sxs-lookup"><span data-stu-id="148cd-319">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="148cd-320">Spustí sledovací proces souborů, který spustí příkaz, když se soubory změní.</span><span class="sxs-lookup"><span data-stu-id="148cd-320">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="148cd-321">Další informace o jednotlivých nástrojích získáte tak `dotnet <tool-name> --help`, že zadáte.</span><span class="sxs-lookup"><span data-stu-id="148cd-321">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="148cd-322">Příklady</span><span class="sxs-lookup"><span data-stu-id="148cd-322">Examples</span></span>

<span data-ttu-id="148cd-323">Vytvoří novou konzolovou aplikaci .NET Core:</span><span class="sxs-lookup"><span data-stu-id="148cd-323">Creates a new .NET Core console application:</span></span>

`dotnet new console`

<span data-ttu-id="148cd-324">Obnovit závislosti pro danou aplikaci:</span><span class="sxs-lookup"><span data-stu-id="148cd-324">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="148cd-325">Sestavení projektu a jeho závislostí v daném adresáři:</span><span class="sxs-lookup"><span data-stu-id="148cd-325">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="148cd-326">Spusťte knihovnu DLL aplikace, například `myapp.dll`:</span><span class="sxs-lookup"><span data-stu-id="148cd-326">Run an application DLL, such as `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="148cd-327">Proměnné prostředí</span><span class="sxs-lookup"><span data-stu-id="148cd-327">Environment variables</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="148cd-328">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="148cd-328">.NET Core 2.1</span></span>](#tab/netcore21)

`DOTNET_PACKAGES`

<span data-ttu-id="148cd-329">Složka globálních balíčků.</span><span class="sxs-lookup"><span data-stu-id="148cd-329">The global packages folder.</span></span> <span data-ttu-id="148cd-330">Pokud není nastavená, použije se `~/.nuget/packages` ve výchozím nastavení `%userprofile%\.nuget\packages` v systému UNIX nebo Windows.</span><span class="sxs-lookup"><span data-stu-id="148cd-330">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="148cd-331">Určuje umístění indexu údržby používaného sdíleným hostitelem při načítání modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="148cd-331">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="148cd-332">Určuje, jestli se data o využití nástrojů .NET Core shromažďují a odesílají do Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="148cd-332">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="148cd-333">Nastavte na `true` výslovný souhlas funkce telemetrie (hodnoty `true`, `1`nebo `yes` přijmout).</span><span class="sxs-lookup"><span data-stu-id="148cd-333">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="148cd-334">V opačném případě `false` nastavte, aby se přihlásil k funkcím `0`telemetrie ( `no` hodnoty `false`, nebo přijaty).</span><span class="sxs-lookup"><span data-stu-id="148cd-334">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="148cd-335">Pokud není nastavená, je výchozí `false` nastavení a funkce telemetrie je aktivní.</span><span class="sxs-lookup"><span data-stu-id="148cd-335">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="148cd-336">Určuje, zda je rozhraní .NET Core Runtime, sdílené rozhraní nebo sada SDK vyřešeno z globálního umístění.</span><span class="sxs-lookup"><span data-stu-id="148cd-336">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="148cd-337">Pokud není nastaven, použije se výchozí `true`hodnota.</span><span class="sxs-lookup"><span data-stu-id="148cd-337">If not set, it defaults to `true`.</span></span> <span data-ttu-id="148cd-338">Nastavte na hodnotu neřešitelné z globálního umístění a používejte izolované instalace rozhraní .NET Core ( `0` hodnoty `false` nebo jsou přijatelné). `false`</span><span class="sxs-lookup"><span data-stu-id="148cd-338">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="148cd-339">Další informace o vyhledávání na více úrovních najdete v tématu [SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="148cd-339">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

<span data-ttu-id="148cd-340">Zakáže posunutí dílčí verze, pokud je nastaveno `0`na.</span><span class="sxs-lookup"><span data-stu-id="148cd-340">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="148cd-341">Další informace najdete v tématu o tom, jak [Posunout](../whats-new/dotnet-core-2-1.md#roll-forward)nahoru.</span><span class="sxs-lookup"><span data-stu-id="148cd-341">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="148cd-342">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="148cd-342">.NET Core 2.0</span></span>](#tab/netcore20)

`DOTNET_PACKAGES`

<span data-ttu-id="148cd-343">Mezipaměť primárního balíčku.</span><span class="sxs-lookup"><span data-stu-id="148cd-343">The primary package cache.</span></span> <span data-ttu-id="148cd-344">Pokud není nastavená, použije se `$HOME/.nuget/packages` ve výchozím nastavení `%userprofile%\.nuget\packages` v systému UNIX nebo Windows.</span><span class="sxs-lookup"><span data-stu-id="148cd-344">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="148cd-345">Určuje umístění indexu údržby používaného sdíleným hostitelem při načítání modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="148cd-345">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="148cd-346">Určuje, jestli se data o využití nástrojů .NET Core shromažďují a odesílají do Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="148cd-346">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="148cd-347">Nastavte na `true` výslovný souhlas funkce telemetrie (hodnoty `true`, `1`nebo `yes` přijmout).</span><span class="sxs-lookup"><span data-stu-id="148cd-347">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="148cd-348">V opačném případě `false` nastavte, aby se přihlásil k funkcím `0`telemetrie ( `no` hodnoty `false`, nebo přijaty).</span><span class="sxs-lookup"><span data-stu-id="148cd-348">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="148cd-349">Pokud není nastavená, je výchozí `false` nastavení a funkce telemetrie je aktivní.</span><span class="sxs-lookup"><span data-stu-id="148cd-349">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="148cd-350">Určuje, zda je rozhraní .NET Core Runtime, sdílené rozhraní nebo sada SDK vyřešeno z globálního umístění.</span><span class="sxs-lookup"><span data-stu-id="148cd-350">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="148cd-351">Pokud není nastaven, použije se výchozí `true`hodnota.</span><span class="sxs-lookup"><span data-stu-id="148cd-351">If not set, it defaults to `true`.</span></span> <span data-ttu-id="148cd-352">Nastavte na hodnotu neřešitelné z globálního umístění a používejte izolované instalace rozhraní .NET Core ( `0` hodnoty `false` nebo jsou přijatelné). `false`</span><span class="sxs-lookup"><span data-stu-id="148cd-352">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="148cd-353">Další informace o vyhledávání na více úrovních najdete v tématu [SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="148cd-353">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="148cd-354">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="148cd-354">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="148cd-355">Mezipaměť primárního balíčku.</span><span class="sxs-lookup"><span data-stu-id="148cd-355">The primary package cache.</span></span> <span data-ttu-id="148cd-356">Pokud není nastavená, použije se `$HOME/.nuget/packages` ve výchozím nastavení `%userprofile%\.nuget\packages` v systému UNIX nebo Windows.</span><span class="sxs-lookup"><span data-stu-id="148cd-356">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="148cd-357">Určuje umístění indexu údržby používaného sdíleným hostitelem při načítání modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="148cd-357">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="148cd-358">Určuje, jestli se data o využití nástrojů .NET Core shromažďují a odesílají do Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="148cd-358">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="148cd-359">Nastavte na `true` výslovný souhlas funkce telemetrie (hodnoty `true`, `1`nebo `yes` přijmout).</span><span class="sxs-lookup"><span data-stu-id="148cd-359">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="148cd-360">V opačném případě `false` nastavte, aby se přihlásil k funkcím `0`telemetrie ( `no` hodnoty `false`, nebo přijaty).</span><span class="sxs-lookup"><span data-stu-id="148cd-360">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="148cd-361">Pokud není nastavená, je výchozí `false` nastavení a funkce telemetrie je aktivní.</span><span class="sxs-lookup"><span data-stu-id="148cd-361">If not set, the default is `false` and the telemetry feature is active.</span></span>

---

## <a name="see-also"></a><span data-ttu-id="148cd-362">Viz také:</span><span class="sxs-lookup"><span data-stu-id="148cd-362">See also</span></span>

- [<span data-ttu-id="148cd-363">Běhové konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="148cd-363">Runtime Configuration Files</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
