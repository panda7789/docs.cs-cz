---
title: dotnet – příkaz
description: Přečtěte si o příkazu dotnet (obecný ovladač pro .NET Core CLI nástroje) a jeho využití.
ms.date: 06/04/2018
ms.openlocfilehash: 8de6a6f7e584dc472dc23d60f113b03610abb3ef
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926229"
---
# <a name="dotnet-command"></a><span data-ttu-id="2f88e-103">dotnet – příkaz</span><span class="sxs-lookup"><span data-stu-id="2f88e-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="2f88e-104">Name</span><span class="sxs-lookup"><span data-stu-id="2f88e-104">Name</span></span>

<span data-ttu-id="2f88e-105">`dotnet`– Nástroj pro správu zdrojového kódu a binárních souborů .NET.</span><span class="sxs-lookup"><span data-stu-id="2f88e-105">`dotnet` - A tool for managing .NET source code and binaries.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2f88e-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="2f88e-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="2f88e-107">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="2f88e-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="2f88e-108">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="2f88e-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx]
    [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="2f88e-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="2f88e-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet [command] [arguments] [--additionalprobingpath] [--depsfile] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--runtimeconfig] [-v|--verbosity] [--version]
```

---

## <a name="description"></a><span data-ttu-id="2f88e-110">Popis</span><span class="sxs-lookup"><span data-stu-id="2f88e-110">Description</span></span>

<span data-ttu-id="2f88e-111">`dotnet`je nástroj pro správu zdrojového kódu a binárních souborů .NET.</span><span class="sxs-lookup"><span data-stu-id="2f88e-111">`dotnet` is a tool for managing .NET source code and binaries.</span></span> <span data-ttu-id="2f88e-112">Zpřístupňuje příkazy, které provádějí konkrétní úkoly, [`dotnet build`](dotnet-build.md) jako například a. [`dotnet run`](dotnet-run.md)</span><span class="sxs-lookup"><span data-stu-id="2f88e-112">It exposes commands that perform specific tasks, such as [`dotnet build`](dotnet-build.md) and [`dotnet run`](dotnet-run.md).</span></span> <span data-ttu-id="2f88e-113">Každý příkaz definuje své vlastní argumenty.</span><span class="sxs-lookup"><span data-stu-id="2f88e-113">Each command defines its own arguments.</span></span> <span data-ttu-id="2f88e-114">Typ `--help` za každým příkazem pro přístup k krátké dokumentaci k nápovědě.</span><span class="sxs-lookup"><span data-stu-id="2f88e-114">Type `--help` after each command to access brief help documentation.</span></span>

<span data-ttu-id="2f88e-115">`dotnet`lze použít ke spouštění aplikací zadáním knihovny DLL aplikace, například `dotnet myapp.dll`.</span><span class="sxs-lookup"><span data-stu-id="2f88e-115">`dotnet` can be used to run applications, by specifying an application DLL, such as `dotnet myapp.dll`.</span></span> <span data-ttu-id="2f88e-116">Další informace o možnostech nasazení najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md) .</span><span class="sxs-lookup"><span data-stu-id="2f88e-116">See [.NET Core application deployment](../deploying/index.md) for to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="2f88e-117">Možnosti</span><span class="sxs-lookup"><span data-stu-id="2f88e-117">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="2f88e-118">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="2f88e-118">.NET Core 2.1</span></span>](#tab/netcore21)

`--additional-deps <PATH>`

<span data-ttu-id="2f88e-119">Cesta k dodatečnému souboru *. DEPS. JSON* .</span><span class="sxs-lookup"><span data-stu-id="2f88e-119">Path to an additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="2f88e-120">Cesta obsahující zásady a sestavení pro zjišťování k testování</span><span class="sxs-lookup"><span data-stu-id="2f88e-120">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="2f88e-121">Cesta k souboru *DEPS. JSON* .</span><span class="sxs-lookup"><span data-stu-id="2f88e-121">Path to a *deps.json* file.</span></span>

<span data-ttu-id="2f88e-122">Soubor *DEPS. JSON* obsahuje seznam závislostí, závislosti kompilace a informace o verzi používané k řešení konfliktů sestavení.</span><span class="sxs-lookup"><span data-stu-id="2f88e-122">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="2f88e-123">Další informace o tomto souboru najdete v tématu [běhové konfigurační soubory](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="2f88e-123">For more information about this file, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

`-d|--diagnostics`

<span data-ttu-id="2f88e-124">Povolí výstup diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="2f88e-124">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="2f88e-125">Verze modulu runtime .NET Core, která se má použít ke spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="2f88e-125">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="2f88e-126">Vytiskne dokumentaci pro daný příkaz, například `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="2f88e-126">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="2f88e-127">`dotnet --help`vytiskne seznam dostupných příkazů.</span><span class="sxs-lookup"><span data-stu-id="2f88e-127">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="2f88e-128">Vytiskne podrobné informace o instalaci .NET Core a počítačovém prostředí, jako je aktuální operační systém, a potvrzení SHA verze .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2f88e-128">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--list-runtimes`

<span data-ttu-id="2f88e-129">Zobrazí nainstalované moduly runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2f88e-129">Displays the installed .NET Core runtimes.</span></span>

`--list-sdks`

<span data-ttu-id="2f88e-130">Zobrazí nainstalované sady SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2f88e-130">Displays the installed .NET Core SDKs.</span></span>

`--roll-forward-on-no-candidate-fx <N>`

<span data-ttu-id="2f88e-131">Definuje chování v případě, že požadovaná sdílená architektura není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="2f88e-131">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="2f88e-132">`N` může být:</span><span class="sxs-lookup"><span data-stu-id="2f88e-132">`N` can be:</span></span>

- <span data-ttu-id="2f88e-133">`0`– Zakažte u sebe i menší verzi.</span><span class="sxs-lookup"><span data-stu-id="2f88e-133">`0` - Disable even minor version roll forward.</span></span>
- <span data-ttu-id="2f88e-134">`1`– Navýšení se dopředá na podverzi, ale ne na hlavní verzi.</span><span class="sxs-lookup"><span data-stu-id="2f88e-134">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="2f88e-135">Toto je výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="2f88e-135">This is the default behavior.</span></span>
- <span data-ttu-id="2f88e-136">`2`– Posunutí posunu k dílčím a hlavním verzím</span><span class="sxs-lookup"><span data-stu-id="2f88e-136">`2` - Roll forward on minor and major versions.</span></span>

 <span data-ttu-id="2f88e-137">Další informace najdete v tématu o tom, jak [Posunout](../whats-new/dotnet-core-2-1.md#roll-forward)nahoru.</span><span class="sxs-lookup"><span data-stu-id="2f88e-137">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`--runtimeconfig`

<span data-ttu-id="2f88e-138">Cesta k souboru *runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="2f88e-138">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="2f88e-139">Soubor *runtimeconfig. JSON* je konfigurační soubor obsahující konfigurační nastavení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="2f88e-139">A *runtimeconfig.json* file is a configuration file containing runtime configuration settings.</span></span> <span data-ttu-id="2f88e-140">Další informace najdete v tématu [běhové konfigurační soubory](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="2f88e-140">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="2f88e-141">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="2f88e-141">Sets the verbosity level of the command.</span></span> <span data-ttu-id="2f88e-142">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]` `d[etailed]`, a .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="2f88e-142">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="2f88e-143">Nepodporováno v každém příkazu; Pokud chcete zjistit, zda je tato možnost k dispozici, zobrazte konkrétní příkazová stránka.</span><span class="sxs-lookup"><span data-stu-id="2f88e-143">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="2f88e-144">Vytiskne verzi .NET Core SDK, která se používá.</span><span class="sxs-lookup"><span data-stu-id="2f88e-144">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="2f88e-145">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="2f88e-145">.NET Core 2.0</span></span>](#tab/netcore20)

`--additional-deps <PATH>`

<span data-ttu-id="2f88e-146">Cesta k dodatečnému souboru *. DEPS. JSON* .</span><span class="sxs-lookup"><span data-stu-id="2f88e-146">Path to an additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="2f88e-147">Cesta obsahující zásady a sestavení pro zjišťování k testování</span><span class="sxs-lookup"><span data-stu-id="2f88e-147">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="2f88e-148">Cesta k souboru *DEPS. JSON* .</span><span class="sxs-lookup"><span data-stu-id="2f88e-148">Path to a *deps.json* file.</span></span>

<span data-ttu-id="2f88e-149">Soubor *DEPS. JSON* obsahuje seznam závislostí, závislosti kompilace a informace o verzi používané k řešení konfliktů sestavení.</span><span class="sxs-lookup"><span data-stu-id="2f88e-149">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="2f88e-150">Další podrobnosti o tomto souboru najdete v tématu [běhové konfigurační soubory na GitHubu](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="2f88e-150">For more details on this file, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-d|--diagnostics`

<span data-ttu-id="2f88e-151">Povolí výstup diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="2f88e-151">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="2f88e-152">Verze modulu runtime .NET Core, která se má použít ke spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="2f88e-152">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="2f88e-153">Vytiskne dokumentaci pro daný příkaz, například `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="2f88e-153">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="2f88e-154">`dotnet --help`vytiskne seznam dostupných příkazů.</span><span class="sxs-lookup"><span data-stu-id="2f88e-154">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="2f88e-155">Vytiskne podrobné informace o instalaci .NET Core a počítačovém prostředí, jako je aktuální operační systém, a potvrzení SHA verze .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2f88e-155">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="2f88e-156">Zakáže posunutí dílčí verze, pokud je nastaveno `0`na.</span><span class="sxs-lookup"><span data-stu-id="2f88e-156">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="2f88e-157">Další informace najdete v tématu o tom, jak [Posunout](../whats-new/dotnet-core-2-1.md#roll-forward)nahoru.</span><span class="sxs-lookup"><span data-stu-id="2f88e-157">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`--runtimeconfig`

<span data-ttu-id="2f88e-158">Cesta k souboru *runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="2f88e-158">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="2f88e-159">Soubor *runtimeconfig. JSON* je konfigurační soubor obsahující konfigurační nastavení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="2f88e-159">A *runtimeconfig.json* file is a configuration file containing runtime configuration settings.</span></span> <span data-ttu-id="2f88e-160">Další podrobnosti najdete v tématu [běhové konfigurační soubory na GitHubu](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="2f88e-160">For more details, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="2f88e-161">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="2f88e-161">Sets the verbosity level of the command.</span></span> <span data-ttu-id="2f88e-162">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]` `d[etailed]`, a .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="2f88e-162">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="2f88e-163">Nepodporováno v každém příkazu; Pokud chcete zjistit, zda je tato možnost k dispozici, zobrazte konkrétní příkazová stránka.</span><span class="sxs-lookup"><span data-stu-id="2f88e-163">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="2f88e-164">Vytiskne verzi .NET Core SDK, která se používá.</span><span class="sxs-lookup"><span data-stu-id="2f88e-164">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="2f88e-165">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="2f88e-165">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="2f88e-166">Cesta obsahující zásady a sestavení pro zjišťování k testování</span><span class="sxs-lookup"><span data-stu-id="2f88e-166">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="2f88e-167">Cesta k souboru *DEPS. JSON* .</span><span class="sxs-lookup"><span data-stu-id="2f88e-167">Path to a *deps.json* file.</span></span>

<span data-ttu-id="2f88e-168">Soubor *DEPS. JSON* obsahuje seznam závislostí, závislosti kompilace a informace o verzi používané k řešení konfliktů sestavení.</span><span class="sxs-lookup"><span data-stu-id="2f88e-168">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="2f88e-169">Další podrobnosti o tomto souboru najdete v tématu [běhové konfigurační soubory na GitHubu](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="2f88e-169">For more details on this file, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-d|--diagnostics`

<span data-ttu-id="2f88e-170">Povolí výstup diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="2f88e-170">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="2f88e-171">Verze modulu runtime .NET Core, která se má použít ke spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="2f88e-171">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="2f88e-172">Vytiskne dokumentaci pro daný příkaz, například `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="2f88e-172">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="2f88e-173">`dotnet --help`vytiskne seznam dostupných příkazů.</span><span class="sxs-lookup"><span data-stu-id="2f88e-173">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="2f88e-174">Vytiskne podrobné informace o instalaci .NET Core a počítačovém prostředí, jako je aktuální operační systém, a potvrzení SHA verze .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2f88e-174">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--runtimeconfig`

<span data-ttu-id="2f88e-175">Cesta k souboru *runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="2f88e-175">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="2f88e-176">Soubor *runtimeconfig. JSON* je konfigurační soubor obsahující konfigurační nastavení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="2f88e-176">A *runtimeconfig.json* file is a configuration file containing runtime configuration settings.</span></span> <span data-ttu-id="2f88e-177">Další podrobnosti najdete v tématu [běhové konfigurační soubory na GitHubu](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="2f88e-177">For more details, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="2f88e-178">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="2f88e-178">Sets the verbosity level of the command.</span></span> <span data-ttu-id="2f88e-179">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]` `d[etailed]`, a .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="2f88e-179">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="2f88e-180">Nepodporováno v každém příkazu; Pokud chcete zjistit, zda je tato možnost k dispozici, zobrazte konkrétní příkazová stránka.</span><span class="sxs-lookup"><span data-stu-id="2f88e-180">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="2f88e-181">Vytiskne verzi .NET Core SDK, která se používá.</span><span class="sxs-lookup"><span data-stu-id="2f88e-181">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="2f88e-182">Příkazy dotnet</span><span class="sxs-lookup"><span data-stu-id="2f88e-182">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="2f88e-183">Obecné</span><span class="sxs-lookup"><span data-stu-id="2f88e-183">General</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="2f88e-184">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="2f88e-184">.NET Core 2.1</span></span>](#tab/netcore21)

| <span data-ttu-id="2f88e-185">Příkaz</span><span class="sxs-lookup"><span data-stu-id="2f88e-185">Command</span></span>                                       | <span data-ttu-id="2f88e-186">Funkce</span><span class="sxs-lookup"><span data-stu-id="2f88e-186">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="2f88e-187">dotnet build</span><span class="sxs-lookup"><span data-stu-id="2f88e-187">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="2f88e-188">Vytvoří aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2f88e-188">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="2f88e-189">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="2f88e-189">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="2f88e-190">Komunikuje se servery spuštěnými sestavením.</span><span class="sxs-lookup"><span data-stu-id="2f88e-190">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="2f88e-191">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="2f88e-191">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="2f88e-192">Vyčistit výstupy sestavení.</span><span class="sxs-lookup"><span data-stu-id="2f88e-192">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="2f88e-193">dotnet help</span><span class="sxs-lookup"><span data-stu-id="2f88e-193">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="2f88e-194">Zobrazí podrobnější dokumentaci pro příkaz online.</span><span class="sxs-lookup"><span data-stu-id="2f88e-194">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="2f88e-195">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="2f88e-195">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="2f88e-196">Migruje platný projekt verze Preview 2 na projekt .NET Core SDK 1,0.</span><span class="sxs-lookup"><span data-stu-id="2f88e-196">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="2f88e-197">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="2f88e-197">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="2f88e-198">Poskytuje přístup k příkazovému řádku MSBuild.</span><span class="sxs-lookup"><span data-stu-id="2f88e-198">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="2f88e-199">dotnet new</span><span class="sxs-lookup"><span data-stu-id="2f88e-199">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="2f88e-200">Inicializuje projekt C# nebo F# pro danou šablonu.</span><span class="sxs-lookup"><span data-stu-id="2f88e-200">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="2f88e-201">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="2f88e-201">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="2f88e-202">Vytvoří balíček NuGet vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="2f88e-202">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="2f88e-203">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="2f88e-203">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="2f88e-204">Publikuje aplikaci závislou na rozhraní .NET Framework nebo samostatnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2f88e-204">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="2f88e-205">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="2f88e-205">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="2f88e-206">Obnoví závislosti pro danou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2f88e-206">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="2f88e-207">dotnet run</span><span class="sxs-lookup"><span data-stu-id="2f88e-207">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="2f88e-208">Spustí aplikaci ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="2f88e-208">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="2f88e-209">dotnet run</span><span class="sxs-lookup"><span data-stu-id="2f88e-209">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="2f88e-210">Možnosti pro přidání, odebrání a výpis projektů v souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="2f88e-210">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="2f88e-211">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="2f88e-211">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="2f88e-212">Ukládá sestavení do úložiště balíčků modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="2f88e-212">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="2f88e-213">dotnet test</span><span class="sxs-lookup"><span data-stu-id="2f88e-213">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="2f88e-214">Spustí testy pomocí nástroje Test Runner.</span><span class="sxs-lookup"><span data-stu-id="2f88e-214">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="2f88e-215">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="2f88e-215">.NET Core 2.0</span></span>](#tab/netcore20)

| <span data-ttu-id="2f88e-216">Příkaz</span><span class="sxs-lookup"><span data-stu-id="2f88e-216">Command</span></span>                             | <span data-ttu-id="2f88e-217">Funkce</span><span class="sxs-lookup"><span data-stu-id="2f88e-217">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="2f88e-218">dotnet build</span><span class="sxs-lookup"><span data-stu-id="2f88e-218">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="2f88e-219">Vytvoří aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2f88e-219">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="2f88e-220">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="2f88e-220">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="2f88e-221">Vyčistit výstupy sestavení.</span><span class="sxs-lookup"><span data-stu-id="2f88e-221">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="2f88e-222">dotnet help</span><span class="sxs-lookup"><span data-stu-id="2f88e-222">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="2f88e-223">Zobrazí podrobnější dokumentaci pro příkaz online.</span><span class="sxs-lookup"><span data-stu-id="2f88e-223">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="2f88e-224">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="2f88e-224">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="2f88e-225">Migruje platný projekt verze Preview 2 na projekt .NET Core SDK 1,0.</span><span class="sxs-lookup"><span data-stu-id="2f88e-225">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="2f88e-226">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="2f88e-226">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="2f88e-227">Poskytuje přístup k příkazovému řádku MSBuild.</span><span class="sxs-lookup"><span data-stu-id="2f88e-227">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="2f88e-228">dotnet new</span><span class="sxs-lookup"><span data-stu-id="2f88e-228">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="2f88e-229">Inicializuje projekt C# nebo F# pro danou šablonu.</span><span class="sxs-lookup"><span data-stu-id="2f88e-229">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="2f88e-230">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="2f88e-230">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="2f88e-231">Vytvoří balíček NuGet vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="2f88e-231">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="2f88e-232">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="2f88e-232">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="2f88e-233">Publikuje aplikaci závislou na rozhraní .NET Framework nebo samostatnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2f88e-233">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="2f88e-234">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="2f88e-234">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="2f88e-235">Obnoví závislosti pro danou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2f88e-235">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="2f88e-236">dotnet run</span><span class="sxs-lookup"><span data-stu-id="2f88e-236">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="2f88e-237">Spustí aplikaci ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="2f88e-237">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="2f88e-238">dotnet run</span><span class="sxs-lookup"><span data-stu-id="2f88e-238">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="2f88e-239">Možnosti pro přidání, odebrání a výpis projektů v souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="2f88e-239">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="2f88e-240">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="2f88e-240">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="2f88e-241">Ukládá sestavení do úložiště balíčků modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="2f88e-241">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="2f88e-242">dotnet test</span><span class="sxs-lookup"><span data-stu-id="2f88e-242">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="2f88e-243">Spustí testy pomocí nástroje Test Runner.</span><span class="sxs-lookup"><span data-stu-id="2f88e-243">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="2f88e-244">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="2f88e-244">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="2f88e-245">Příkaz</span><span class="sxs-lookup"><span data-stu-id="2f88e-245">Command</span></span>                             | <span data-ttu-id="2f88e-246">Funkce</span><span class="sxs-lookup"><span data-stu-id="2f88e-246">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="2f88e-247">dotnet build</span><span class="sxs-lookup"><span data-stu-id="2f88e-247">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="2f88e-248">Vytvoří aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2f88e-248">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="2f88e-249">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="2f88e-249">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="2f88e-250">Vyčistit výstupy sestavení.</span><span class="sxs-lookup"><span data-stu-id="2f88e-250">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="2f88e-251">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="2f88e-251">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="2f88e-252">Migruje platný projekt verze Preview 2 na projekt .NET Core SDK 1,0.</span><span class="sxs-lookup"><span data-stu-id="2f88e-252">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="2f88e-253">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="2f88e-253">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="2f88e-254">Poskytuje přístup k příkazovému řádku MSBuild.</span><span class="sxs-lookup"><span data-stu-id="2f88e-254">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="2f88e-255">dotnet new</span><span class="sxs-lookup"><span data-stu-id="2f88e-255">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="2f88e-256">Inicializuje projekt C# nebo F# pro danou šablonu.</span><span class="sxs-lookup"><span data-stu-id="2f88e-256">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="2f88e-257">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="2f88e-257">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="2f88e-258">Vytvoří balíček NuGet vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="2f88e-258">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="2f88e-259">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="2f88e-259">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="2f88e-260">Publikuje aplikaci závislou na rozhraní .NET Framework nebo samostatnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2f88e-260">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="2f88e-261">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="2f88e-261">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="2f88e-262">Obnoví závislosti pro danou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2f88e-262">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="2f88e-263">dotnet run</span><span class="sxs-lookup"><span data-stu-id="2f88e-263">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="2f88e-264">Spustí aplikaci ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="2f88e-264">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="2f88e-265">dotnet run</span><span class="sxs-lookup"><span data-stu-id="2f88e-265">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="2f88e-266">Možnosti pro přidání, odebrání a výpis projektů v souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="2f88e-266">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="2f88e-267">dotnet test</span><span class="sxs-lookup"><span data-stu-id="2f88e-267">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="2f88e-268">Spustí testy pomocí nástroje Test Runner.</span><span class="sxs-lookup"><span data-stu-id="2f88e-268">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="2f88e-269">Odkazy na projekty</span><span class="sxs-lookup"><span data-stu-id="2f88e-269">Project references</span></span>

<span data-ttu-id="2f88e-270">Příkaz</span><span class="sxs-lookup"><span data-stu-id="2f88e-270">Command</span></span> | <span data-ttu-id="2f88e-271">Funkce</span><span class="sxs-lookup"><span data-stu-id="2f88e-271">Function</span></span>
--- | ---
[<span data-ttu-id="2f88e-272">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="2f88e-272">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="2f88e-273">Přidá odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="2f88e-273">Adds a project reference.</span></span>
[<span data-ttu-id="2f88e-274">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="2f88e-274">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="2f88e-275">Vypíše odkazy na projekt.</span><span class="sxs-lookup"><span data-stu-id="2f88e-275">Lists project references.</span></span>
[<span data-ttu-id="2f88e-276">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="2f88e-276">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="2f88e-277">Odebere odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="2f88e-277">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="2f88e-278">Balíčky NuGet</span><span class="sxs-lookup"><span data-stu-id="2f88e-278">NuGet packages</span></span>

<span data-ttu-id="2f88e-279">Příkaz</span><span class="sxs-lookup"><span data-stu-id="2f88e-279">Command</span></span> | <span data-ttu-id="2f88e-280">Funkce</span><span class="sxs-lookup"><span data-stu-id="2f88e-280">Function</span></span>
--- | ---
[<span data-ttu-id="2f88e-281">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="2f88e-281">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="2f88e-282">Přidá balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="2f88e-282">Adds a NuGet package.</span></span>
[<span data-ttu-id="2f88e-283">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="2f88e-283">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="2f88e-284">Odebere balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="2f88e-284">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="2f88e-285">Příkazy NuGet</span><span class="sxs-lookup"><span data-stu-id="2f88e-285">NuGet commands</span></span>

<span data-ttu-id="2f88e-286">Příkaz</span><span class="sxs-lookup"><span data-stu-id="2f88e-286">Command</span></span> | <span data-ttu-id="2f88e-287">Funkce</span><span class="sxs-lookup"><span data-stu-id="2f88e-287">Function</span></span>
--- | ---
[<span data-ttu-id="2f88e-288">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="2f88e-288">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="2f88e-289">Odstraní nebo zruší výpis balíčku ze serveru.</span><span class="sxs-lookup"><span data-stu-id="2f88e-289">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="2f88e-290">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="2f88e-290">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="2f88e-291">Vymaže nebo vypíše místní prostředky NuGet, jako je mezipaměť požadavků HTTP, dočasná mezipaměť nebo složka globálních balíčků v celém počítači.</span><span class="sxs-lookup"><span data-stu-id="2f88e-291">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="2f88e-292">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="2f88e-292">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="2f88e-293">Odešle balíček na server a publikuje ho.</span><span class="sxs-lookup"><span data-stu-id="2f88e-293">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tools-commands"></a><span data-ttu-id="2f88e-294">Příkazy globálních nástrojů</span><span class="sxs-lookup"><span data-stu-id="2f88e-294">Global Tools commands</span></span>

<span data-ttu-id="2f88e-295">K dispozici jsou [globální nástroje .NET Core](global-tools.md) od .NET Core SDK 2.1.300:</span><span class="sxs-lookup"><span data-stu-id="2f88e-295">[.NET Core Global Tools](global-tools.md) are available starting with .NET Core SDK 2.1.300:</span></span>

<span data-ttu-id="2f88e-296">Příkaz</span><span class="sxs-lookup"><span data-stu-id="2f88e-296">Command</span></span> | <span data-ttu-id="2f88e-297">Funkce</span><span class="sxs-lookup"><span data-stu-id="2f88e-297">Function</span></span>
--- | ---
[<span data-ttu-id="2f88e-298">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="2f88e-298">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="2f88e-299">Nainstaluje na váš počítač globální nástroj.</span><span class="sxs-lookup"><span data-stu-id="2f88e-299">Installs a Global Tool on your machine.</span></span>
[<span data-ttu-id="2f88e-300">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="2f88e-300">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="2f88e-301">Zobrazí seznam všech globálních nástrojů, které jsou aktuálně nainstalované ve výchozím adresáři na vašem počítači nebo v zadané cestě.</span><span class="sxs-lookup"><span data-stu-id="2f88e-301">Lists all Global Tools currently installed in the default directory on your machine or in the specified path.</span></span>
[<span data-ttu-id="2f88e-302">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="2f88e-302">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="2f88e-303">Odinstaluje z počítače globální nástroj.</span><span class="sxs-lookup"><span data-stu-id="2f88e-303">Uninstalls a Global Tool from your machine.</span></span>
[<span data-ttu-id="2f88e-304">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="2f88e-304">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="2f88e-305">Aktualizuje na svém počítači globální nástroj.</span><span class="sxs-lookup"><span data-stu-id="2f88e-305">Updates a Global Tool on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="2f88e-306">Další nástroje</span><span class="sxs-lookup"><span data-stu-id="2f88e-306">Additional tools</span></span>

<span data-ttu-id="2f88e-307">Počínaje .NET Core SDK 2.1.300 je teď k dispozici několik nástrojů, které byly k dispozici pouze pro jednotlivé `DotnetCliToolReference` projekty pomocí, jako součást .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="2f88e-307">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="2f88e-308">Tyto nástroje jsou uvedené v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="2f88e-308">These tools are listed in the following table:</span></span>

| <span data-ttu-id="2f88e-309">Nástroj</span><span class="sxs-lookup"><span data-stu-id="2f88e-309">Tool</span></span>                                              | <span data-ttu-id="2f88e-310">Funkce</span><span class="sxs-lookup"><span data-stu-id="2f88e-310">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="2f88e-311">vývoj – certifikáty</span><span class="sxs-lookup"><span data-stu-id="2f88e-311">dev-certs</span></span>                                         | <span data-ttu-id="2f88e-312">Vytvoří a spravuje vývojové certifikáty.</span><span class="sxs-lookup"><span data-stu-id="2f88e-312">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="2f88e-313">EF</span><span class="sxs-lookup"><span data-stu-id="2f88e-313">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="2f88e-314">Entity Framework Core nástroje příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="2f88e-314">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="2f88e-315">sql-cache</span><span class="sxs-lookup"><span data-stu-id="2f88e-315">sql-cache</span></span>                                         | <span data-ttu-id="2f88e-316">Nástroje příkazového řádku pro SQL Server cache</span><span class="sxs-lookup"><span data-stu-id="2f88e-316">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="2f88e-317">uživatel – tajné klíče</span><span class="sxs-lookup"><span data-stu-id="2f88e-317">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="2f88e-318">Spravuje tajné klíče uživatele.</span><span class="sxs-lookup"><span data-stu-id="2f88e-318">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="2f88e-319">sledovací</span><span class="sxs-lookup"><span data-stu-id="2f88e-319">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="2f88e-320">Spustí sledovací proces souborů, který spustí příkaz, když se soubory změní.</span><span class="sxs-lookup"><span data-stu-id="2f88e-320">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="2f88e-321">Další informace o jednotlivých nástrojích získáte tak `dotnet <tool-name> --help`, že zadáte.</span><span class="sxs-lookup"><span data-stu-id="2f88e-321">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="2f88e-322">Příklady</span><span class="sxs-lookup"><span data-stu-id="2f88e-322">Examples</span></span>

<span data-ttu-id="2f88e-323">Vytvoří novou konzolovou aplikaci .NET Core:</span><span class="sxs-lookup"><span data-stu-id="2f88e-323">Creates a new .NET Core console application:</span></span>

`dotnet new console`

<span data-ttu-id="2f88e-324">Obnovit závislosti pro danou aplikaci:</span><span class="sxs-lookup"><span data-stu-id="2f88e-324">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="2f88e-325">Sestavení projektu a jeho závislostí v daném adresáři:</span><span class="sxs-lookup"><span data-stu-id="2f88e-325">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="2f88e-326">Spusťte knihovnu DLL aplikace, například `myapp.dll`:</span><span class="sxs-lookup"><span data-stu-id="2f88e-326">Run an application DLL, such as `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="2f88e-327">Proměnné prostředí</span><span class="sxs-lookup"><span data-stu-id="2f88e-327">Environment variables</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="2f88e-328">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="2f88e-328">.NET Core 2.1</span></span>](#tab/netcore21)

`DOTNET_PACKAGES`

<span data-ttu-id="2f88e-329">Složka globálních balíčků.</span><span class="sxs-lookup"><span data-stu-id="2f88e-329">The global packages folder.</span></span> <span data-ttu-id="2f88e-330">Pokud není nastavená, použije se `~/.nuget/packages` ve výchozím nastavení `%userprofile%\.nuget\packages` v systému UNIX nebo Windows.</span><span class="sxs-lookup"><span data-stu-id="2f88e-330">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="2f88e-331">Určuje umístění indexu údržby používaného sdíleným hostitelem při načítání modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="2f88e-331">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="2f88e-332">Určuje, jestli se data o využití nástrojů .NET Core shromažďují a odesílají do Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="2f88e-332">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="2f88e-333">Nastavte na `true` výslovný souhlas funkce telemetrie (hodnoty `true`, `1`nebo `yes` přijmout).</span><span class="sxs-lookup"><span data-stu-id="2f88e-333">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="2f88e-334">V opačném případě `false` nastavte, aby se přihlásil k funkcím `0`telemetrie ( `no` hodnoty `false`, nebo přijaty).</span><span class="sxs-lookup"><span data-stu-id="2f88e-334">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="2f88e-335">Pokud není nastavená, je výchozí `false` nastavení a funkce telemetrie je aktivní.</span><span class="sxs-lookup"><span data-stu-id="2f88e-335">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="2f88e-336">Určuje, zda je rozhraní .NET Core Runtime, sdílené rozhraní nebo sada SDK vyřešeno z globálního umístění.</span><span class="sxs-lookup"><span data-stu-id="2f88e-336">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="2f88e-337">Pokud není nastaven, použije se výchozí `true`hodnota.</span><span class="sxs-lookup"><span data-stu-id="2f88e-337">If not set, it defaults to `true`.</span></span> <span data-ttu-id="2f88e-338">Nastavte na hodnotu neřešitelné z globálního umístění a používejte izolované instalace rozhraní .NET Core ( `0` hodnoty `false` nebo jsou přijatelné). `false`</span><span class="sxs-lookup"><span data-stu-id="2f88e-338">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="2f88e-339">Další informace o vyhledávání na více úrovních najdete v tématu [SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="2f88e-339">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

<span data-ttu-id="2f88e-340">Zakáže posunutí dílčí verze, pokud je nastaveno `0`na.</span><span class="sxs-lookup"><span data-stu-id="2f88e-340">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="2f88e-341">Další informace najdete v tématu o tom, jak [Posunout](../whats-new/dotnet-core-2-1.md#roll-forward)nahoru.</span><span class="sxs-lookup"><span data-stu-id="2f88e-341">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="2f88e-342">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="2f88e-342">.NET Core 2.0</span></span>](#tab/netcore20)

`DOTNET_PACKAGES`

<span data-ttu-id="2f88e-343">Mezipaměť primárního balíčku.</span><span class="sxs-lookup"><span data-stu-id="2f88e-343">The primary package cache.</span></span> <span data-ttu-id="2f88e-344">Pokud není nastavená, použije se `$HOME/.nuget/packages` ve výchozím nastavení `%userprofile%\.nuget\packages` v systému UNIX nebo Windows.</span><span class="sxs-lookup"><span data-stu-id="2f88e-344">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="2f88e-345">Určuje umístění indexu údržby používaného sdíleným hostitelem při načítání modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="2f88e-345">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="2f88e-346">Určuje, jestli se data o využití nástrojů .NET Core shromažďují a odesílají do Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="2f88e-346">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="2f88e-347">Nastavte na `true` výslovný souhlas funkce telemetrie (hodnoty `true`, `1`nebo `yes` přijmout).</span><span class="sxs-lookup"><span data-stu-id="2f88e-347">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="2f88e-348">V opačném případě `false` nastavte, aby se přihlásil k funkcím `0`telemetrie ( `no` hodnoty `false`, nebo přijaty).</span><span class="sxs-lookup"><span data-stu-id="2f88e-348">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="2f88e-349">Pokud není nastavená, je výchozí `false` nastavení a funkce telemetrie je aktivní.</span><span class="sxs-lookup"><span data-stu-id="2f88e-349">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="2f88e-350">Určuje, zda je rozhraní .NET Core Runtime, sdílené rozhraní nebo sada SDK vyřešeno z globálního umístění.</span><span class="sxs-lookup"><span data-stu-id="2f88e-350">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="2f88e-351">Pokud není nastaven, použije se výchozí `true`hodnota.</span><span class="sxs-lookup"><span data-stu-id="2f88e-351">If not set, it defaults to `true`.</span></span> <span data-ttu-id="2f88e-352">Nastavte na hodnotu neřešitelné z globálního umístění a používejte izolované instalace rozhraní .NET Core ( `0` hodnoty `false` nebo jsou přijatelné). `false`</span><span class="sxs-lookup"><span data-stu-id="2f88e-352">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="2f88e-353">Další informace o vyhledávání na více úrovních najdete v tématu [SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="2f88e-353">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="2f88e-354">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="2f88e-354">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="2f88e-355">Mezipaměť primárního balíčku.</span><span class="sxs-lookup"><span data-stu-id="2f88e-355">The primary package cache.</span></span> <span data-ttu-id="2f88e-356">Pokud není nastavená, použije se `$HOME/.nuget/packages` ve výchozím nastavení `%userprofile%\.nuget\packages` v systému UNIX nebo Windows.</span><span class="sxs-lookup"><span data-stu-id="2f88e-356">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="2f88e-357">Určuje umístění indexu údržby používaného sdíleným hostitelem při načítání modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="2f88e-357">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="2f88e-358">Určuje, jestli se data o využití nástrojů .NET Core shromažďují a odesílají do Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="2f88e-358">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="2f88e-359">Nastavte na `true` výslovný souhlas funkce telemetrie (hodnoty `true`, `1`nebo `yes` přijmout).</span><span class="sxs-lookup"><span data-stu-id="2f88e-359">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="2f88e-360">V opačném případě `false` nastavte, aby se přihlásil k funkcím `0`telemetrie ( `no` hodnoty `false`, nebo přijaty).</span><span class="sxs-lookup"><span data-stu-id="2f88e-360">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="2f88e-361">Pokud není nastavená, je výchozí `false` nastavení a funkce telemetrie je aktivní.</span><span class="sxs-lookup"><span data-stu-id="2f88e-361">If not set, the default is `false` and the telemetry feature is active.</span></span>

---

## <a name="see-also"></a><span data-ttu-id="2f88e-362">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2f88e-362">See also</span></span>

- [<span data-ttu-id="2f88e-363">Běhové konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="2f88e-363">Runtime Configuration Files</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
