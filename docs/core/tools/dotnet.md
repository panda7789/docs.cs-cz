---
title: dotnet – příkaz
description: Přečtěte si o příkazu dotnet (obecný ovladač pro .NET Core CLI) a jeho použití.
ms.date: 06/04/2018
ms.openlocfilehash: 7674529980623caa2291987bdeba52f50ce2fc2c
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920552"
---
# <a name="dotnet-command"></a><span data-ttu-id="49aeb-103">dotnet – příkaz</span><span class="sxs-lookup"><span data-stu-id="49aeb-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="49aeb-104">Name</span><span class="sxs-lookup"><span data-stu-id="49aeb-104">Name</span></span>

<span data-ttu-id="49aeb-105">`dotnet` – Nástroj pro správu zdrojového kódu a binárních souborů .NET.</span><span class="sxs-lookup"><span data-stu-id="49aeb-105">`dotnet` - A tool for managing .NET source code and binaries.</span></span>

## <a name="synopsis"></a><span data-ttu-id="49aeb-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="49aeb-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="49aeb-107">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="49aeb-107">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="49aeb-108">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="49aeb-108">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx]
    [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="49aeb-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="49aeb-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet [command] [arguments] [--additionalprobingpath] [--depsfile] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--runtimeconfig] [-v|--verbosity] [--version]
```

---

## <a name="description"></a><span data-ttu-id="49aeb-110">Popis</span><span class="sxs-lookup"><span data-stu-id="49aeb-110">Description</span></span>

<span data-ttu-id="49aeb-111">`dotnet` je nástroj pro správu zdrojového kódu a binárních souborů .NET.</span><span class="sxs-lookup"><span data-stu-id="49aeb-111">`dotnet` is a tool for managing .NET source code and binaries.</span></span> <span data-ttu-id="49aeb-112">Zpřístupňuje příkazy, které provádějí konkrétní úkoly, například [`dotnet build`](dotnet-build.md) a [`dotnet run`](dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="49aeb-112">It exposes commands that perform specific tasks, such as [`dotnet build`](dotnet-build.md) and [`dotnet run`](dotnet-run.md).</span></span> <span data-ttu-id="49aeb-113">Každý příkaz definuje své vlastní argumenty.</span><span class="sxs-lookup"><span data-stu-id="49aeb-113">Each command defines its own arguments.</span></span> <span data-ttu-id="49aeb-114">Zadejte `--help` za každým příkazem pro přístup k krátké dokumentaci k nápovědě.</span><span class="sxs-lookup"><span data-stu-id="49aeb-114">Type `--help` after each command to access brief help documentation.</span></span>

<span data-ttu-id="49aeb-115">`dotnet` lze použít ke spouštění aplikací zadáním knihovny DLL aplikace, jako je například `dotnet myapp.dll`.</span><span class="sxs-lookup"><span data-stu-id="49aeb-115">`dotnet` can be used to run applications, by specifying an application DLL, such as `dotnet myapp.dll`.</span></span> <span data-ttu-id="49aeb-116">Další informace o možnostech nasazení najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md) .</span><span class="sxs-lookup"><span data-stu-id="49aeb-116">See [.NET Core application deployment](../deploying/index.md) for to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="49aeb-117">Možnosti</span><span class="sxs-lookup"><span data-stu-id="49aeb-117">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="49aeb-118">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="49aeb-118">.NET Core 2.1</span></span>](#tab/netcore21)

`--additional-deps <PATH>`

<span data-ttu-id="49aeb-119">Cesta k dodatečnému souboru *. DEPS. JSON* .</span><span class="sxs-lookup"><span data-stu-id="49aeb-119">Path to an additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="49aeb-120">Cesta obsahující zásady a sestavení pro zjišťování k testování</span><span class="sxs-lookup"><span data-stu-id="49aeb-120">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="49aeb-121">Cesta k souboru *DEPS. JSON* .</span><span class="sxs-lookup"><span data-stu-id="49aeb-121">Path to a *deps.json* file.</span></span>

<span data-ttu-id="49aeb-122">Soubor *DEPS. JSON* obsahuje seznam závislostí, závislosti kompilace a informace o verzi používané k řešení konfliktů sestavení.</span><span class="sxs-lookup"><span data-stu-id="49aeb-122">A *deps.json* file contains a list of dependencies, compilation dependencies, and version information used to address assembly conflicts.</span></span> <span data-ttu-id="49aeb-123">Další informace o tomto souboru najdete v tématu [běhové konfigurační soubory](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="49aeb-123">For more information about this file, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

`-d|--diagnostics`

<span data-ttu-id="49aeb-124">Povolí výstup diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="49aeb-124">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="49aeb-125">Verze modulu runtime .NET Core, která se má použít ke spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="49aeb-125">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="49aeb-126">Vytiskne dokumentaci pro daný příkaz, například `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="49aeb-126">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="49aeb-127">`dotnet --help` vytiskne seznam dostupných příkazů.</span><span class="sxs-lookup"><span data-stu-id="49aeb-127">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="49aeb-128">Vytiskne podrobné informace o instalaci .NET Core a počítačovém prostředí, jako je aktuální operační systém, a potvrzení SHA verze .NET Core.</span><span class="sxs-lookup"><span data-stu-id="49aeb-128">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--list-runtimes`

<span data-ttu-id="49aeb-129">Zobrazí nainstalované moduly runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="49aeb-129">Displays the installed .NET Core runtimes.</span></span>

`--list-sdks`

<span data-ttu-id="49aeb-130">Zobrazí nainstalované sady SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="49aeb-130">Displays the installed .NET Core SDKs.</span></span>

`--roll-forward-on-no-candidate-fx <N>`

<span data-ttu-id="49aeb-131">Definuje chování v případě, že požadovaná sdílená architektura není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="49aeb-131">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="49aeb-132">`N` může být:</span><span class="sxs-lookup"><span data-stu-id="49aeb-132">`N` can be:</span></span>

- <span data-ttu-id="49aeb-133">`0` – zakažte u sebe i menší verzi.</span><span class="sxs-lookup"><span data-stu-id="49aeb-133">`0` - Disable even minor version roll forward.</span></span>
- <span data-ttu-id="49aeb-134">`1` – předejte se k dílčí verzi, ale ne k hlavní verzi.</span><span class="sxs-lookup"><span data-stu-id="49aeb-134">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="49aeb-135">Toto je výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="49aeb-135">This is the default behavior.</span></span>
- <span data-ttu-id="49aeb-136">`2` – předejte se do menších a hlavních verzí.</span><span class="sxs-lookup"><span data-stu-id="49aeb-136">`2` - Roll forward on minor and major versions.</span></span>

 <span data-ttu-id="49aeb-137">Další informace najdete v tématu o tom, jak [Posunout](../whats-new/dotnet-core-2-1.md#roll-forward)nahoru.</span><span class="sxs-lookup"><span data-stu-id="49aeb-137">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`--runtimeconfig`

<span data-ttu-id="49aeb-138">Cesta k souboru *runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="49aeb-138">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="49aeb-139">Soubor *runtimeconfig. JSON* je konfigurační soubor, který obsahuje nastavení runtime.</span><span class="sxs-lookup"><span data-stu-id="49aeb-139">A *runtimeconfig.json* file is a configuration file containing run-time settings.</span></span> <span data-ttu-id="49aeb-140">Další informace najdete v tématu [nastavení konfigurace runtime .NET Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="49aeb-140">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="49aeb-141">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="49aeb-141">Sets the verbosity level of the command.</span></span> <span data-ttu-id="49aeb-142">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="49aeb-142">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="49aeb-143">Nepodporováno v každém příkazu; Pokud chcete zjistit, zda je tato možnost k dispozici, zobrazte konkrétní příkazová stránka.</span><span class="sxs-lookup"><span data-stu-id="49aeb-143">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="49aeb-144">Vytiskne verzi .NET Core SDK, která se používá.</span><span class="sxs-lookup"><span data-stu-id="49aeb-144">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="49aeb-145">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="49aeb-145">.NET Core 2.0</span></span>](#tab/netcore20)

`--additional-deps <PATH>`

<span data-ttu-id="49aeb-146">Cesta k dodatečnému souboru *. DEPS. JSON* .</span><span class="sxs-lookup"><span data-stu-id="49aeb-146">Path to an additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="49aeb-147">Cesta obsahující zásady a sestavení pro zjišťování k testování</span><span class="sxs-lookup"><span data-stu-id="49aeb-147">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="49aeb-148">Cesta k souboru *DEPS. JSON* .</span><span class="sxs-lookup"><span data-stu-id="49aeb-148">Path to a *deps.json* file.</span></span>

<span data-ttu-id="49aeb-149">Soubor *DEPS. JSON* obsahuje seznam závislostí, závislosti kompilace a informace o verzi používané k řešení konfliktů sestavení.</span><span class="sxs-lookup"><span data-stu-id="49aeb-149">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="49aeb-150">Další podrobnosti o tomto souboru najdete v tématu [běhové konfigurační soubory na GitHubu](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="49aeb-150">For more details on this file, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-d|--diagnostics`

<span data-ttu-id="49aeb-151">Povolí výstup diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="49aeb-151">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="49aeb-152">Verze modulu runtime .NET Core, která se má použít ke spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="49aeb-152">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="49aeb-153">Vytiskne dokumentaci pro daný příkaz, například `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="49aeb-153">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="49aeb-154">`dotnet --help` vytiskne seznam dostupných příkazů.</span><span class="sxs-lookup"><span data-stu-id="49aeb-154">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="49aeb-155">Vytiskne podrobné informace o instalaci .NET Core a počítačovém prostředí, jako je aktuální operační systém, a potvrzení SHA verze .NET Core.</span><span class="sxs-lookup"><span data-stu-id="49aeb-155">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="49aeb-156">Zakáže posunutí dílčí verze, pokud je nastaveno na `0`.</span><span class="sxs-lookup"><span data-stu-id="49aeb-156">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="49aeb-157">Další informace najdete v tématu o tom, jak [Posunout](../whats-new/dotnet-core-2-1.md#roll-forward)nahoru.</span><span class="sxs-lookup"><span data-stu-id="49aeb-157">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`--runtimeconfig`

<span data-ttu-id="49aeb-158">Cesta k souboru *runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="49aeb-158">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="49aeb-159">Soubor *runtimeconfig. JSON* je konfigurační soubor, který obsahuje nastavení runtime.</span><span class="sxs-lookup"><span data-stu-id="49aeb-159">A *runtimeconfig.json* file is a configuration file containing run-time settings.</span></span> <span data-ttu-id="49aeb-160">Další informace najdete v tématu [nastavení konfigurace runtime .NET Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="49aeb-160">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="49aeb-161">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="49aeb-161">Sets the verbosity level of the command.</span></span> <span data-ttu-id="49aeb-162">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="49aeb-162">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="49aeb-163">Nepodporováno v každém příkazu; Pokud chcete zjistit, zda je tato možnost k dispozici, zobrazte konkrétní příkazová stránka.</span><span class="sxs-lookup"><span data-stu-id="49aeb-163">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="49aeb-164">Vytiskne verzi .NET Core SDK, která se používá.</span><span class="sxs-lookup"><span data-stu-id="49aeb-164">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="49aeb-165">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="49aeb-165">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="49aeb-166">Cesta obsahující zásady a sestavení pro zjišťování k testování</span><span class="sxs-lookup"><span data-stu-id="49aeb-166">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="49aeb-167">Cesta k souboru *DEPS. JSON* .</span><span class="sxs-lookup"><span data-stu-id="49aeb-167">Path to a *deps.json* file.</span></span>

<span data-ttu-id="49aeb-168">Soubor *DEPS. JSON* obsahuje seznam závislostí, závislosti kompilace a informace o verzi používané k řešení konfliktů sestavení.</span><span class="sxs-lookup"><span data-stu-id="49aeb-168">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="49aeb-169">Další podrobnosti o tomto souboru najdete v tématu [běhové konfigurační soubory na GitHubu](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="49aeb-169">For more details on this file, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-d|--diagnostics`

<span data-ttu-id="49aeb-170">Povolí výstup diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="49aeb-170">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="49aeb-171">Verze modulu runtime .NET Core, která se má použít ke spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="49aeb-171">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="49aeb-172">Vytiskne dokumentaci pro daný příkaz, například `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="49aeb-172">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="49aeb-173">`dotnet --help` vytiskne seznam dostupných příkazů.</span><span class="sxs-lookup"><span data-stu-id="49aeb-173">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="49aeb-174">Vytiskne podrobné informace o instalaci .NET Core a počítačovém prostředí, jako je aktuální operační systém, a potvrzení SHA verze .NET Core.</span><span class="sxs-lookup"><span data-stu-id="49aeb-174">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--runtimeconfig`

<span data-ttu-id="49aeb-175">Cesta k souboru *runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="49aeb-175">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="49aeb-176">Soubor *runtimeconfig. JSON* je konfigurační soubor, který obsahuje nastavení runtime.</span><span class="sxs-lookup"><span data-stu-id="49aeb-176">A *runtimeconfig.json* file is a configuration file containing run-time settings.</span></span> <span data-ttu-id="49aeb-177">Další informace najdete v tématu [nastavení konfigurace runtime .NET Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="49aeb-177">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="49aeb-178">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="49aeb-178">Sets the verbosity level of the command.</span></span> <span data-ttu-id="49aeb-179">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="49aeb-179">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="49aeb-180">Nepodporováno v každém příkazu; Pokud chcete zjistit, zda je tato možnost k dispozici, zobrazte konkrétní příkazová stránka.</span><span class="sxs-lookup"><span data-stu-id="49aeb-180">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="49aeb-181">Vytiskne verzi .NET Core SDK, která se používá.</span><span class="sxs-lookup"><span data-stu-id="49aeb-181">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="49aeb-182">Příkazy dotnet</span><span class="sxs-lookup"><span data-stu-id="49aeb-182">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="49aeb-183">Obecné</span><span class="sxs-lookup"><span data-stu-id="49aeb-183">General</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="49aeb-184">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="49aeb-184">.NET Core 2.1</span></span>](#tab/netcore21)

| <span data-ttu-id="49aeb-185">Příkaz</span><span class="sxs-lookup"><span data-stu-id="49aeb-185">Command</span></span>                                       | <span data-ttu-id="49aeb-186">Funkce</span><span class="sxs-lookup"><span data-stu-id="49aeb-186">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="49aeb-187">dotnet build</span><span class="sxs-lookup"><span data-stu-id="49aeb-187">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="49aeb-188">Vytvoří aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="49aeb-188">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="49aeb-189">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="49aeb-189">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="49aeb-190">Komunikuje se servery spuštěnými sestavením.</span><span class="sxs-lookup"><span data-stu-id="49aeb-190">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="49aeb-191">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="49aeb-191">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="49aeb-192">Vyčistit výstupy sestavení.</span><span class="sxs-lookup"><span data-stu-id="49aeb-192">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="49aeb-193">dotnet help</span><span class="sxs-lookup"><span data-stu-id="49aeb-193">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="49aeb-194">Zobrazí podrobnější dokumentaci pro příkaz online.</span><span class="sxs-lookup"><span data-stu-id="49aeb-194">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="49aeb-195">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="49aeb-195">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="49aeb-196">Migruje platný projekt verze Preview 2 na projekt .NET Core SDK 1,0.</span><span class="sxs-lookup"><span data-stu-id="49aeb-196">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="49aeb-197">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="49aeb-197">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="49aeb-198">Poskytuje přístup k příkazovému řádku MSBuild.</span><span class="sxs-lookup"><span data-stu-id="49aeb-198">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="49aeb-199">dotnet new</span><span class="sxs-lookup"><span data-stu-id="49aeb-199">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="49aeb-200">Inicializuje projekt C# nebo F# pro danou šablonu.</span><span class="sxs-lookup"><span data-stu-id="49aeb-200">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="49aeb-201">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="49aeb-201">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="49aeb-202">Vytvoří balíček NuGet vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="49aeb-202">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="49aeb-203">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="49aeb-203">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="49aeb-204">Publikuje aplikaci závislou na rozhraní .NET Framework nebo samostatnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="49aeb-204">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="49aeb-205">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="49aeb-205">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="49aeb-206">Obnoví závislosti pro danou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="49aeb-206">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="49aeb-207">dotnet run</span><span class="sxs-lookup"><span data-stu-id="49aeb-207">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="49aeb-208">Spustí aplikaci ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="49aeb-208">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="49aeb-209">dotnet run</span><span class="sxs-lookup"><span data-stu-id="49aeb-209">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="49aeb-210">Možnosti pro přidání, odebrání a výpis projektů v souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="49aeb-210">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="49aeb-211">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="49aeb-211">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="49aeb-212">Ukládá sestavení do úložiště balíčků modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="49aeb-212">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="49aeb-213">dotnet test</span><span class="sxs-lookup"><span data-stu-id="49aeb-213">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="49aeb-214">Spustí testy pomocí nástroje Test Runner.</span><span class="sxs-lookup"><span data-stu-id="49aeb-214">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="49aeb-215">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="49aeb-215">.NET Core 2.0</span></span>](#tab/netcore20)

| <span data-ttu-id="49aeb-216">Příkaz</span><span class="sxs-lookup"><span data-stu-id="49aeb-216">Command</span></span>                             | <span data-ttu-id="49aeb-217">Funkce</span><span class="sxs-lookup"><span data-stu-id="49aeb-217">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="49aeb-218">dotnet build</span><span class="sxs-lookup"><span data-stu-id="49aeb-218">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="49aeb-219">Vytvoří aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="49aeb-219">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="49aeb-220">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="49aeb-220">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="49aeb-221">Vyčistit výstupy sestavení.</span><span class="sxs-lookup"><span data-stu-id="49aeb-221">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="49aeb-222">dotnet help</span><span class="sxs-lookup"><span data-stu-id="49aeb-222">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="49aeb-223">Zobrazí podrobnější dokumentaci pro příkaz online.</span><span class="sxs-lookup"><span data-stu-id="49aeb-223">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="49aeb-224">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="49aeb-224">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="49aeb-225">Migruje platný projekt verze Preview 2 na projekt .NET Core SDK 1,0.</span><span class="sxs-lookup"><span data-stu-id="49aeb-225">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="49aeb-226">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="49aeb-226">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="49aeb-227">Poskytuje přístup k příkazovému řádku MSBuild.</span><span class="sxs-lookup"><span data-stu-id="49aeb-227">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="49aeb-228">dotnet new</span><span class="sxs-lookup"><span data-stu-id="49aeb-228">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="49aeb-229">Inicializuje projekt C# nebo F# pro danou šablonu.</span><span class="sxs-lookup"><span data-stu-id="49aeb-229">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="49aeb-230">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="49aeb-230">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="49aeb-231">Vytvoří balíček NuGet vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="49aeb-231">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="49aeb-232">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="49aeb-232">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="49aeb-233">Publikuje aplikaci závislou na rozhraní .NET Framework nebo samostatnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="49aeb-233">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="49aeb-234">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="49aeb-234">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="49aeb-235">Obnoví závislosti pro danou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="49aeb-235">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="49aeb-236">dotnet run</span><span class="sxs-lookup"><span data-stu-id="49aeb-236">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="49aeb-237">Spustí aplikaci ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="49aeb-237">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="49aeb-238">dotnet run</span><span class="sxs-lookup"><span data-stu-id="49aeb-238">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="49aeb-239">Možnosti pro přidání, odebrání a výpis projektů v souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="49aeb-239">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="49aeb-240">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="49aeb-240">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="49aeb-241">Ukládá sestavení do úložiště balíčků modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="49aeb-241">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="49aeb-242">dotnet test</span><span class="sxs-lookup"><span data-stu-id="49aeb-242">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="49aeb-243">Spustí testy pomocí nástroje Test Runner.</span><span class="sxs-lookup"><span data-stu-id="49aeb-243">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="49aeb-244">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="49aeb-244">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="49aeb-245">Příkaz</span><span class="sxs-lookup"><span data-stu-id="49aeb-245">Command</span></span>                             | <span data-ttu-id="49aeb-246">Funkce</span><span class="sxs-lookup"><span data-stu-id="49aeb-246">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="49aeb-247">dotnet build</span><span class="sxs-lookup"><span data-stu-id="49aeb-247">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="49aeb-248">Vytvoří aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="49aeb-248">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="49aeb-249">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="49aeb-249">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="49aeb-250">Vyčistit výstupy sestavení.</span><span class="sxs-lookup"><span data-stu-id="49aeb-250">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="49aeb-251">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="49aeb-251">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="49aeb-252">Migruje platný projekt verze Preview 2 na projekt .NET Core SDK 1,0.</span><span class="sxs-lookup"><span data-stu-id="49aeb-252">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="49aeb-253">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="49aeb-253">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="49aeb-254">Poskytuje přístup k příkazovému řádku MSBuild.</span><span class="sxs-lookup"><span data-stu-id="49aeb-254">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="49aeb-255">dotnet new</span><span class="sxs-lookup"><span data-stu-id="49aeb-255">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="49aeb-256">Inicializuje projekt C# nebo F# pro danou šablonu.</span><span class="sxs-lookup"><span data-stu-id="49aeb-256">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="49aeb-257">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="49aeb-257">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="49aeb-258">Vytvoří balíček NuGet vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="49aeb-258">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="49aeb-259">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="49aeb-259">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="49aeb-260">Publikuje aplikaci závislou na rozhraní .NET Framework nebo samostatnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="49aeb-260">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="49aeb-261">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="49aeb-261">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="49aeb-262">Obnoví závislosti pro danou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="49aeb-262">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="49aeb-263">dotnet run</span><span class="sxs-lookup"><span data-stu-id="49aeb-263">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="49aeb-264">Spustí aplikaci ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="49aeb-264">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="49aeb-265">dotnet run</span><span class="sxs-lookup"><span data-stu-id="49aeb-265">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="49aeb-266">Možnosti pro přidání, odebrání a výpis projektů v souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="49aeb-266">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="49aeb-267">dotnet test</span><span class="sxs-lookup"><span data-stu-id="49aeb-267">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="49aeb-268">Spustí testy pomocí nástroje Test Runner.</span><span class="sxs-lookup"><span data-stu-id="49aeb-268">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="49aeb-269">Odkazy na projekty</span><span class="sxs-lookup"><span data-stu-id="49aeb-269">Project references</span></span>

<span data-ttu-id="49aeb-270">Příkaz</span><span class="sxs-lookup"><span data-stu-id="49aeb-270">Command</span></span> | <span data-ttu-id="49aeb-271">Funkce</span><span class="sxs-lookup"><span data-stu-id="49aeb-271">Function</span></span>
--- | ---
[<span data-ttu-id="49aeb-272">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="49aeb-272">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="49aeb-273">Přidá odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="49aeb-273">Adds a project reference.</span></span>
[<span data-ttu-id="49aeb-274">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="49aeb-274">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="49aeb-275">Vypíše odkazy na projekt.</span><span class="sxs-lookup"><span data-stu-id="49aeb-275">Lists project references.</span></span>
[<span data-ttu-id="49aeb-276">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="49aeb-276">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="49aeb-277">Odebere odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="49aeb-277">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="49aeb-278">Balíčky NuGet</span><span class="sxs-lookup"><span data-stu-id="49aeb-278">NuGet packages</span></span>

<span data-ttu-id="49aeb-279">Příkaz</span><span class="sxs-lookup"><span data-stu-id="49aeb-279">Command</span></span> | <span data-ttu-id="49aeb-280">Funkce</span><span class="sxs-lookup"><span data-stu-id="49aeb-280">Function</span></span>
--- | ---
[<span data-ttu-id="49aeb-281">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="49aeb-281">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="49aeb-282">Přidá balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="49aeb-282">Adds a NuGet package.</span></span>
[<span data-ttu-id="49aeb-283">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="49aeb-283">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="49aeb-284">Odebere balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="49aeb-284">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="49aeb-285">Příkazy NuGet</span><span class="sxs-lookup"><span data-stu-id="49aeb-285">NuGet commands</span></span>

<span data-ttu-id="49aeb-286">Příkaz</span><span class="sxs-lookup"><span data-stu-id="49aeb-286">Command</span></span> | <span data-ttu-id="49aeb-287">Funkce</span><span class="sxs-lookup"><span data-stu-id="49aeb-287">Function</span></span>
--- | ---
[<span data-ttu-id="49aeb-288">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="49aeb-288">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="49aeb-289">Odstraní nebo zruší výpis balíčku ze serveru.</span><span class="sxs-lookup"><span data-stu-id="49aeb-289">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="49aeb-290">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="49aeb-290">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="49aeb-291">Vymaže nebo vypíše místní prostředky NuGet, jako je mezipaměť požadavků HTTP, dočasná mezipaměť nebo složka globálních balíčků v celém počítači.</span><span class="sxs-lookup"><span data-stu-id="49aeb-291">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="49aeb-292">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="49aeb-292">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="49aeb-293">Odešle balíček na server a publikuje ho.</span><span class="sxs-lookup"><span data-stu-id="49aeb-293">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tools-commands"></a><span data-ttu-id="49aeb-294">Příkazy globálních nástrojů</span><span class="sxs-lookup"><span data-stu-id="49aeb-294">Global Tools commands</span></span>

<span data-ttu-id="49aeb-295">K dispozici jsou [globální nástroje .NET Core](global-tools.md) od .NET Core SDK 2.1.300:</span><span class="sxs-lookup"><span data-stu-id="49aeb-295">[.NET Core Global Tools](global-tools.md) are available starting with .NET Core SDK 2.1.300:</span></span>

<span data-ttu-id="49aeb-296">Příkaz</span><span class="sxs-lookup"><span data-stu-id="49aeb-296">Command</span></span> | <span data-ttu-id="49aeb-297">Funkce</span><span class="sxs-lookup"><span data-stu-id="49aeb-297">Function</span></span>
--- | ---
[<span data-ttu-id="49aeb-298">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="49aeb-298">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="49aeb-299">Nainstaluje na váš počítač globální nástroj.</span><span class="sxs-lookup"><span data-stu-id="49aeb-299">Installs a Global Tool on your machine.</span></span>
[<span data-ttu-id="49aeb-300">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="49aeb-300">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="49aeb-301">Zobrazí seznam všech globálních nástrojů, které jsou aktuálně nainstalované ve výchozím adresáři na vašem počítači nebo v zadané cestě.</span><span class="sxs-lookup"><span data-stu-id="49aeb-301">Lists all Global Tools currently installed in the default directory on your machine or in the specified path.</span></span>
[<span data-ttu-id="49aeb-302">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="49aeb-302">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="49aeb-303">Odinstaluje z počítače globální nástroj.</span><span class="sxs-lookup"><span data-stu-id="49aeb-303">Uninstalls a Global Tool from your machine.</span></span>
[<span data-ttu-id="49aeb-304">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="49aeb-304">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="49aeb-305">Aktualizuje na svém počítači globální nástroj.</span><span class="sxs-lookup"><span data-stu-id="49aeb-305">Updates a Global Tool on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="49aeb-306">Další nástroje</span><span class="sxs-lookup"><span data-stu-id="49aeb-306">Additional tools</span></span>

<span data-ttu-id="49aeb-307">Počínaje .NET Core SDK 2.1.300 je teď k dispozici několik nástrojů, které byly k dispozici pouze pro jednotlivé projekty pomocí `DotnetCliToolReference` jsou nyní k dispozici jako součást .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="49aeb-307">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="49aeb-308">Tyto nástroje jsou uvedené v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="49aeb-308">These tools are listed in the following table:</span></span>

| <span data-ttu-id="49aeb-309">Nástroj</span><span class="sxs-lookup"><span data-stu-id="49aeb-309">Tool</span></span>                                              | <span data-ttu-id="49aeb-310">Funkce</span><span class="sxs-lookup"><span data-stu-id="49aeb-310">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="49aeb-311">vývoj – certifikáty</span><span class="sxs-lookup"><span data-stu-id="49aeb-311">dev-certs</span></span>                                         | <span data-ttu-id="49aeb-312">Vytvoří a spravuje vývojové certifikáty.</span><span class="sxs-lookup"><span data-stu-id="49aeb-312">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="49aeb-313">EF</span><span class="sxs-lookup"><span data-stu-id="49aeb-313">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="49aeb-314">Entity Framework Core nástroje příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="49aeb-314">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="49aeb-315">sql-cache</span><span class="sxs-lookup"><span data-stu-id="49aeb-315">sql-cache</span></span>                                         | <span data-ttu-id="49aeb-316">Nástroje příkazového řádku pro SQL Server cache</span><span class="sxs-lookup"><span data-stu-id="49aeb-316">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="49aeb-317">uživatel – tajné klíče</span><span class="sxs-lookup"><span data-stu-id="49aeb-317">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="49aeb-318">Spravuje tajné klíče uživatele.</span><span class="sxs-lookup"><span data-stu-id="49aeb-318">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="49aeb-319">sledovací</span><span class="sxs-lookup"><span data-stu-id="49aeb-319">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="49aeb-320">Spustí sledovací proces souborů, který spustí příkaz, když se soubory změní.</span><span class="sxs-lookup"><span data-stu-id="49aeb-320">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="49aeb-321">Další informace o jednotlivých nástrojích získáte, když zadáte `dotnet <tool-name> --help`.</span><span class="sxs-lookup"><span data-stu-id="49aeb-321">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="49aeb-322">Příklady</span><span class="sxs-lookup"><span data-stu-id="49aeb-322">Examples</span></span>

<span data-ttu-id="49aeb-323">Vytvoří novou konzolovou aplikaci .NET Core:</span><span class="sxs-lookup"><span data-stu-id="49aeb-323">Creates a new .NET Core console application:</span></span>

`dotnet new console`

<span data-ttu-id="49aeb-324">Obnovit závislosti pro danou aplikaci:</span><span class="sxs-lookup"><span data-stu-id="49aeb-324">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="49aeb-325">Sestavení projektu a jeho závislostí v daném adresáři:</span><span class="sxs-lookup"><span data-stu-id="49aeb-325">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="49aeb-326">Spusťte knihovnu DLL aplikace, například `myapp.dll`:</span><span class="sxs-lookup"><span data-stu-id="49aeb-326">Run an application DLL, such as `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="49aeb-327">Proměnné prostředí</span><span class="sxs-lookup"><span data-stu-id="49aeb-327">Environment variables</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="49aeb-328">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="49aeb-328">.NET Core 2.1</span></span>](#tab/netcore21)

`DOTNET_PACKAGES`

<span data-ttu-id="49aeb-329">Složka globálních balíčků.</span><span class="sxs-lookup"><span data-stu-id="49aeb-329">The global packages folder.</span></span> <span data-ttu-id="49aeb-330">Pokud není nastavené, použije se výchozí nastavení `~/.nuget/packages` v systému UNIX nebo `%userprofile%\.nuget\packages` ve Windows.</span><span class="sxs-lookup"><span data-stu-id="49aeb-330">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="49aeb-331">Určuje umístění indexu údržby používaného sdíleným hostitelem při načítání modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="49aeb-331">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="49aeb-332">Určuje, jestli se data o využití nástrojů .NET Core shromažďují a odesílají do Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="49aeb-332">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="49aeb-333">Nastavte na `true` pro výslovný souhlas funkce telemetrie (hodnoty `true`, `1`nebo `yes` přijaté).</span><span class="sxs-lookup"><span data-stu-id="49aeb-333">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="49aeb-334">Jinak nastavte `false` tak, aby se přihlásil k funkcím telemetrie (hodnoty `false`, `0`nebo přijaté `no`).</span><span class="sxs-lookup"><span data-stu-id="49aeb-334">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="49aeb-335">Pokud není nastavená, výchozí hodnota je `false` a funkce telemetrie je aktivní.</span><span class="sxs-lookup"><span data-stu-id="49aeb-335">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="49aeb-336">Určuje, zda je rozhraní .NET Core Runtime, sdílené rozhraní nebo sada SDK vyřešeno z globálního umístění.</span><span class="sxs-lookup"><span data-stu-id="49aeb-336">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="49aeb-337">Pokud není nastavená, použije se výchozí hodnota `true`.</span><span class="sxs-lookup"><span data-stu-id="49aeb-337">If not set, it defaults to `true`.</span></span> <span data-ttu-id="49aeb-338">Nastavte na `false`, aby se nepřeložily z globálního umístění a měly izolované instalace .NET Core (hodnoty `0` nebo `false` jsou přijaté).</span><span class="sxs-lookup"><span data-stu-id="49aeb-338">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="49aeb-339">Další informace o vyhledávání na více úrovních najdete v tématu [SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="49aeb-339">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

<span data-ttu-id="49aeb-340">Zakáže posunutí dílčí verze, pokud je nastaveno na `0`.</span><span class="sxs-lookup"><span data-stu-id="49aeb-340">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="49aeb-341">Další informace najdete v tématu o tom, jak [Posunout](../whats-new/dotnet-core-2-1.md#roll-forward)nahoru.</span><span class="sxs-lookup"><span data-stu-id="49aeb-341">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="49aeb-342">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="49aeb-342">.NET Core 2.0</span></span>](#tab/netcore20)

`DOTNET_PACKAGES`

<span data-ttu-id="49aeb-343">Mezipaměť primárního balíčku.</span><span class="sxs-lookup"><span data-stu-id="49aeb-343">The primary package cache.</span></span> <span data-ttu-id="49aeb-344">Pokud není nastavené, použije se výchozí nastavení `$HOME/.nuget/packages` v systému UNIX nebo `%userprofile%\.nuget\packages` ve Windows.</span><span class="sxs-lookup"><span data-stu-id="49aeb-344">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="49aeb-345">Určuje umístění indexu údržby používaného sdíleným hostitelem při načítání modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="49aeb-345">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="49aeb-346">Určuje, jestli se data o využití nástrojů .NET Core shromažďují a odesílají do Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="49aeb-346">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="49aeb-347">Nastavte na `true` pro výslovný souhlas funkce telemetrie (hodnoty `true`, `1`nebo `yes` přijaté).</span><span class="sxs-lookup"><span data-stu-id="49aeb-347">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="49aeb-348">Jinak nastavte `false` tak, aby se přihlásil k funkcím telemetrie (hodnoty `false`, `0`nebo přijaté `no`).</span><span class="sxs-lookup"><span data-stu-id="49aeb-348">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="49aeb-349">Pokud není nastavená, výchozí hodnota je `false` a funkce telemetrie je aktivní.</span><span class="sxs-lookup"><span data-stu-id="49aeb-349">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="49aeb-350">Určuje, zda je rozhraní .NET Core Runtime, sdílené rozhraní nebo sada SDK vyřešeno z globálního umístění.</span><span class="sxs-lookup"><span data-stu-id="49aeb-350">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="49aeb-351">Pokud není nastavená, použije se výchozí hodnota `true`.</span><span class="sxs-lookup"><span data-stu-id="49aeb-351">If not set, it defaults to `true`.</span></span> <span data-ttu-id="49aeb-352">Nastavte na `false`, aby se nepřeložily z globálního umístění a měly izolované instalace .NET Core (hodnoty `0` nebo `false` jsou přijaté).</span><span class="sxs-lookup"><span data-stu-id="49aeb-352">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="49aeb-353">Další informace o vyhledávání na více úrovních najdete v tématu [SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="49aeb-353">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="49aeb-354">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="49aeb-354">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="49aeb-355">Mezipaměť primárního balíčku.</span><span class="sxs-lookup"><span data-stu-id="49aeb-355">The primary package cache.</span></span> <span data-ttu-id="49aeb-356">Pokud není nastavené, použije se výchozí nastavení `$HOME/.nuget/packages` v systému UNIX nebo `%userprofile%\.nuget\packages` ve Windows.</span><span class="sxs-lookup"><span data-stu-id="49aeb-356">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="49aeb-357">Určuje umístění indexu údržby používaného sdíleným hostitelem při načítání modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="49aeb-357">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="49aeb-358">Určuje, jestli se data o využití nástrojů .NET Core shromažďují a odesílají do Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="49aeb-358">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="49aeb-359">Nastavte na `true` pro výslovný souhlas funkce telemetrie (hodnoty `true`, `1`nebo `yes` přijaté).</span><span class="sxs-lookup"><span data-stu-id="49aeb-359">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="49aeb-360">Jinak nastavte `false` tak, aby se přihlásil k funkcím telemetrie (hodnoty `false`, `0`nebo přijaté `no`).</span><span class="sxs-lookup"><span data-stu-id="49aeb-360">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="49aeb-361">Pokud není nastavená, výchozí hodnota je `false` a funkce telemetrie je aktivní.</span><span class="sxs-lookup"><span data-stu-id="49aeb-361">If not set, the default is `false` and the telemetry feature is active.</span></span>

---

## <a name="see-also"></a><span data-ttu-id="49aeb-362">Viz také:</span><span class="sxs-lookup"><span data-stu-id="49aeb-362">See also</span></span>

- [<span data-ttu-id="49aeb-363">Běhové konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="49aeb-363">Runtime Configuration Files</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [<span data-ttu-id="49aeb-364">Nastavení konfigurace runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="49aeb-364">.NET Core run-time configuration settings</span></span>](../run-time-config/index.md)
