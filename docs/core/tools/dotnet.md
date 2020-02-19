---
title: dotnet – příkaz
description: Přečtěte si o příkazu dotnet (obecný ovladač pro .NET Core CLI) a jeho použití.
ms.date: 02/13/2020
ms.openlocfilehash: 364978465b63401907b46ead64dbceb2f15c8169
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451165"
---
# <a name="dotnet-command"></a><span data-ttu-id="d7013-103">dotnet – příkaz</span><span class="sxs-lookup"><span data-stu-id="d7013-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="d7013-104">Název</span><span class="sxs-lookup"><span data-stu-id="d7013-104">Name</span></span>

<span data-ttu-id="d7013-105">`dotnet` – Nástroj pro správu zdrojového kódu a binárních souborů .NET.</span><span class="sxs-lookup"><span data-stu-id="d7013-105">`dotnet` - A tool for managing .NET source code and binaries.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d7013-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="d7013-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21"></a>[<span data-ttu-id="d7013-107">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="d7013-107">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-20"></a>[<span data-ttu-id="d7013-108">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="d7013-108">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx]
    [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-1x"></a>[<span data-ttu-id="d7013-109">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="d7013-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet [command] [arguments] [--additionalprobingpath] [--depsfile] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--runtimeconfig] [-v|--verbosity] [--version]
```

---

## <a name="description"></a><span data-ttu-id="d7013-110">Popis</span><span class="sxs-lookup"><span data-stu-id="d7013-110">Description</span></span>

<span data-ttu-id="d7013-111">`dotnet` je nástroj pro správu zdrojového kódu a binárních souborů .NET.</span><span class="sxs-lookup"><span data-stu-id="d7013-111">`dotnet` is a tool for managing .NET source code and binaries.</span></span> <span data-ttu-id="d7013-112">Zpřístupňuje příkazy, které provádějí konkrétní úkoly, například [`dotnet build`](dotnet-build.md) a [`dotnet run`](dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="d7013-112">It exposes commands that perform specific tasks, such as [`dotnet build`](dotnet-build.md) and [`dotnet run`](dotnet-run.md).</span></span> <span data-ttu-id="d7013-113">Každý příkaz definuje své vlastní argumenty.</span><span class="sxs-lookup"><span data-stu-id="d7013-113">Each command defines its own arguments.</span></span> <span data-ttu-id="d7013-114">Zadejte `--help` za každým příkazem pro přístup k krátké dokumentaci k nápovědě.</span><span class="sxs-lookup"><span data-stu-id="d7013-114">Type `--help` after each command to access brief help documentation.</span></span>

<span data-ttu-id="d7013-115">`dotnet` lze použít ke spouštění aplikací zadáním knihovny DLL aplikace, jako je například `dotnet myapp.dll`.</span><span class="sxs-lookup"><span data-stu-id="d7013-115">`dotnet` can be used to run applications, by specifying an application DLL, such as `dotnet myapp.dll`.</span></span> <span data-ttu-id="d7013-116">Další informace o možnostech nasazení najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md) .</span><span class="sxs-lookup"><span data-stu-id="d7013-116">See [.NET Core application deployment](../deploying/index.md) for to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="d7013-117">Možnosti</span><span class="sxs-lookup"><span data-stu-id="d7013-117">Options</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="d7013-118">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="d7013-118">.NET Core 2.1</span></span>](#tab/netcore21)

`--additional-deps <PATH>`

<span data-ttu-id="d7013-119">Cesta k dodatečnému souboru *. DEPS. JSON* .</span><span class="sxs-lookup"><span data-stu-id="d7013-119">Path to an additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="d7013-120">Cesta obsahující zásady a sestavení pro zjišťování k testování</span><span class="sxs-lookup"><span data-stu-id="d7013-120">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="d7013-121">Cesta k souboru *DEPS. JSON* .</span><span class="sxs-lookup"><span data-stu-id="d7013-121">Path to a *deps.json* file.</span></span>

<span data-ttu-id="d7013-122">Soubor *DEPS. JSON* obsahuje seznam závislostí, závislosti kompilace a informace o verzi používané k řešení konfliktů sestavení.</span><span class="sxs-lookup"><span data-stu-id="d7013-122">A *deps.json* file contains a list of dependencies, compilation dependencies, and version information used to address assembly conflicts.</span></span> <span data-ttu-id="d7013-123">Další informace o tomto souboru najdete v tématu [běhové konfigurační soubory](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="d7013-123">For more information about this file, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

`-d|--diagnostics`

<span data-ttu-id="d7013-124">Povolí výstup diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="d7013-124">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="d7013-125">Verze modulu runtime .NET Core, která se má použít ke spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="d7013-125">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="d7013-126">Vytiskne dokumentaci pro daný příkaz, například `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="d7013-126">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="d7013-127">`dotnet --help` vytiskne seznam dostupných příkazů.</span><span class="sxs-lookup"><span data-stu-id="d7013-127">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="d7013-128">Vytiskne podrobné informace o instalaci .NET Core a počítačovém prostředí, jako je aktuální operační systém, a potvrzení SHA verze .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d7013-128">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--list-runtimes`

<span data-ttu-id="d7013-129">Zobrazí nainstalované moduly runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d7013-129">Displays the installed .NET Core runtimes.</span></span>

`--list-sdks`

<span data-ttu-id="d7013-130">Zobrazí nainstalované sady SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d7013-130">Displays the installed .NET Core SDKs.</span></span>

`--roll-forward-on-no-candidate-fx <N>`

<span data-ttu-id="d7013-131">Definuje chování v případě, že požadovaná sdílená architektura není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="d7013-131">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="d7013-132">`N` může být:</span><span class="sxs-lookup"><span data-stu-id="d7013-132">`N` can be:</span></span>

- <span data-ttu-id="d7013-133">`0` – zakažte u sebe i menší verzi.</span><span class="sxs-lookup"><span data-stu-id="d7013-133">`0` - Disable even minor version roll forward.</span></span>
- <span data-ttu-id="d7013-134">`1` – předejte se k dílčí verzi, ale ne k hlavní verzi.</span><span class="sxs-lookup"><span data-stu-id="d7013-134">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="d7013-135">Toto je výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="d7013-135">This is the default behavior.</span></span>
- <span data-ttu-id="d7013-136">`2` – předejte se do menších a hlavních verzí.</span><span class="sxs-lookup"><span data-stu-id="d7013-136">`2` - Roll forward on minor and major versions.</span></span>

 <span data-ttu-id="d7013-137">Další informace najdete v tématu o tom, jak [Posunout](../whats-new/dotnet-core-2-1.md#roll-forward)nahoru.</span><span class="sxs-lookup"><span data-stu-id="d7013-137">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`--runtimeconfig`

<span data-ttu-id="d7013-138">Cesta k souboru *runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="d7013-138">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="d7013-139">Soubor *runtimeconfig. JSON* je konfigurační soubor, který obsahuje nastavení runtime.</span><span class="sxs-lookup"><span data-stu-id="d7013-139">A *runtimeconfig.json* file is a configuration file containing run-time settings.</span></span> <span data-ttu-id="d7013-140">Další informace najdete v tématu [nastavení konfigurace runtime .NET Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="d7013-140">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="d7013-141">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="d7013-141">Sets the verbosity level of the command.</span></span> <span data-ttu-id="d7013-142">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d7013-142">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="d7013-143">Nepodporováno v každém příkazu; Pokud chcete zjistit, zda je tato možnost k dispozici, zobrazte konkrétní příkazová stránka.</span><span class="sxs-lookup"><span data-stu-id="d7013-143">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="d7013-144">Vytiskne verzi .NET Core SDK, která se používá.</span><span class="sxs-lookup"><span data-stu-id="d7013-144">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-20"></a>[<span data-ttu-id="d7013-145">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="d7013-145">.NET Core 2.0</span></span>](#tab/netcore20)

`--additional-deps <PATH>`

<span data-ttu-id="d7013-146">Cesta k dodatečnému souboru *. DEPS. JSON* .</span><span class="sxs-lookup"><span data-stu-id="d7013-146">Path to an additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="d7013-147">Cesta obsahující zásady a sestavení pro zjišťování k testování</span><span class="sxs-lookup"><span data-stu-id="d7013-147">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="d7013-148">Cesta k souboru *DEPS. JSON* .</span><span class="sxs-lookup"><span data-stu-id="d7013-148">Path to a *deps.json* file.</span></span>

<span data-ttu-id="d7013-149">Soubor *DEPS. JSON* obsahuje seznam závislostí, závislosti kompilace a informace o verzi používané k řešení konfliktů sestavení.</span><span class="sxs-lookup"><span data-stu-id="d7013-149">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="d7013-150">Další podrobnosti o tomto souboru najdete v tématu [běhové konfigurační soubory na GitHubu](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="d7013-150">For more details on this file, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-d|--diagnostics`

<span data-ttu-id="d7013-151">Povolí výstup diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="d7013-151">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="d7013-152">Verze modulu runtime .NET Core, která se má použít ke spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="d7013-152">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="d7013-153">Vytiskne dokumentaci pro daný příkaz, například `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="d7013-153">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="d7013-154">`dotnet --help` vytiskne seznam dostupných příkazů.</span><span class="sxs-lookup"><span data-stu-id="d7013-154">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="d7013-155">Vytiskne podrobné informace o instalaci .NET Core a počítačovém prostředí, jako je aktuální operační systém, a potvrzení SHA verze .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d7013-155">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="d7013-156">Zakáže posunutí dílčí verze, pokud je nastaveno na `0`.</span><span class="sxs-lookup"><span data-stu-id="d7013-156">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="d7013-157">Další informace najdete v tématu o tom, jak [Posunout](../whats-new/dotnet-core-2-1.md#roll-forward)nahoru.</span><span class="sxs-lookup"><span data-stu-id="d7013-157">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`--runtimeconfig`

<span data-ttu-id="d7013-158">Cesta k souboru *runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="d7013-158">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="d7013-159">Soubor *runtimeconfig. JSON* je konfigurační soubor, který obsahuje nastavení runtime.</span><span class="sxs-lookup"><span data-stu-id="d7013-159">A *runtimeconfig.json* file is a configuration file containing run-time settings.</span></span> <span data-ttu-id="d7013-160">Další informace najdete v tématu [nastavení konfigurace runtime .NET Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="d7013-160">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="d7013-161">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="d7013-161">Sets the verbosity level of the command.</span></span> <span data-ttu-id="d7013-162">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d7013-162">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="d7013-163">Nepodporováno v každém příkazu; Pokud chcete zjistit, zda je tato možnost k dispozici, zobrazte konkrétní příkazová stránka.</span><span class="sxs-lookup"><span data-stu-id="d7013-163">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="d7013-164">Vytiskne verzi .NET Core SDK, která se používá.</span><span class="sxs-lookup"><span data-stu-id="d7013-164">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1x"></a>[<span data-ttu-id="d7013-165">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="d7013-165">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="d7013-166">Cesta obsahující zásady a sestavení pro zjišťování k testování</span><span class="sxs-lookup"><span data-stu-id="d7013-166">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="d7013-167">Cesta k souboru *DEPS. JSON* .</span><span class="sxs-lookup"><span data-stu-id="d7013-167">Path to a *deps.json* file.</span></span>

<span data-ttu-id="d7013-168">Soubor *DEPS. JSON* obsahuje seznam závislostí, závislosti kompilace a informace o verzi používané k řešení konfliktů sestavení.</span><span class="sxs-lookup"><span data-stu-id="d7013-168">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="d7013-169">Další podrobnosti o tomto souboru najdete v tématu [běhové konfigurační soubory na GitHubu](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="d7013-169">For more details on this file, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-d|--diagnostics`

<span data-ttu-id="d7013-170">Povolí výstup diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="d7013-170">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="d7013-171">Verze modulu runtime .NET Core, která se má použít ke spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="d7013-171">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="d7013-172">Vytiskne dokumentaci pro daný příkaz, například `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="d7013-172">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="d7013-173">`dotnet --help` vytiskne seznam dostupných příkazů.</span><span class="sxs-lookup"><span data-stu-id="d7013-173">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="d7013-174">Vytiskne podrobné informace o instalaci .NET Core a počítačovém prostředí, jako je aktuální operační systém, a potvrzení SHA verze .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d7013-174">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--runtimeconfig`

<span data-ttu-id="d7013-175">Cesta k souboru *runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="d7013-175">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="d7013-176">Soubor *runtimeconfig. JSON* je konfigurační soubor, který obsahuje nastavení runtime.</span><span class="sxs-lookup"><span data-stu-id="d7013-176">A *runtimeconfig.json* file is a configuration file containing run-time settings.</span></span> <span data-ttu-id="d7013-177">Další informace najdete v tématu [nastavení konfigurace runtime .NET Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="d7013-177">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="d7013-178">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="d7013-178">Sets the verbosity level of the command.</span></span> <span data-ttu-id="d7013-179">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d7013-179">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="d7013-180">Nepodporováno v každém příkazu; Pokud chcete zjistit, zda je tato možnost k dispozici, zobrazte konkrétní příkazová stránka.</span><span class="sxs-lookup"><span data-stu-id="d7013-180">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="d7013-181">Vytiskne verzi .NET Core SDK, která se používá.</span><span class="sxs-lookup"><span data-stu-id="d7013-181">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="d7013-182">Příkazy dotnet</span><span class="sxs-lookup"><span data-stu-id="d7013-182">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="d7013-183">Obecné</span><span class="sxs-lookup"><span data-stu-id="d7013-183">General</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="d7013-184">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="d7013-184">.NET Core 2.1</span></span>](#tab/netcore21)

| <span data-ttu-id="d7013-185">Příkaz</span><span class="sxs-lookup"><span data-stu-id="d7013-185">Command</span></span>                                       | <span data-ttu-id="d7013-186">Funkce</span><span class="sxs-lookup"><span data-stu-id="d7013-186">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="d7013-187">dotnet build</span><span class="sxs-lookup"><span data-stu-id="d7013-187">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="d7013-188">Vytvoří aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d7013-188">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="d7013-189">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="d7013-189">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="d7013-190">Komunikuje se servery spuštěnými sestavením.</span><span class="sxs-lookup"><span data-stu-id="d7013-190">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="d7013-191">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="d7013-191">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="d7013-192">Vyčistit výstupy sestavení.</span><span class="sxs-lookup"><span data-stu-id="d7013-192">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="d7013-193">dotnet help</span><span class="sxs-lookup"><span data-stu-id="d7013-193">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="d7013-194">Zobrazí podrobnější dokumentaci pro příkaz online.</span><span class="sxs-lookup"><span data-stu-id="d7013-194">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="d7013-195">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="d7013-195">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="d7013-196">Migruje platný projekt verze Preview 2 na projekt .NET Core SDK 1,0.</span><span class="sxs-lookup"><span data-stu-id="d7013-196">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="d7013-197">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="d7013-197">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="d7013-198">Poskytuje přístup k příkazovému řádku MSBuild.</span><span class="sxs-lookup"><span data-stu-id="d7013-198">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="d7013-199">dotnet new</span><span class="sxs-lookup"><span data-stu-id="d7013-199">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="d7013-200">Inicializuje projekt C# nebo F# pro danou šablonu.</span><span class="sxs-lookup"><span data-stu-id="d7013-200">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="d7013-201">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="d7013-201">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="d7013-202">Vytvoří balíček NuGet vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="d7013-202">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="d7013-203">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="d7013-203">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="d7013-204">Publikuje aplikaci závislou na rozhraní .NET Framework nebo samostatnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d7013-204">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="d7013-205">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="d7013-205">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="d7013-206">Obnoví závislosti pro danou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d7013-206">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="d7013-207">dotnet run</span><span class="sxs-lookup"><span data-stu-id="d7013-207">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="d7013-208">Spustí aplikaci ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="d7013-208">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="d7013-209">dotnet run</span><span class="sxs-lookup"><span data-stu-id="d7013-209">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="d7013-210">Možnosti pro přidání, odebrání a výpis projektů v souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="d7013-210">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="d7013-211">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="d7013-211">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="d7013-212">Ukládá sestavení do úložiště balíčků modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="d7013-212">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="d7013-213">dotnet test</span><span class="sxs-lookup"><span data-stu-id="d7013-213">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="d7013-214">Spustí testy pomocí nástroje Test Runner.</span><span class="sxs-lookup"><span data-stu-id="d7013-214">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-20"></a>[<span data-ttu-id="d7013-215">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="d7013-215">.NET Core 2.0</span></span>](#tab/netcore20)

| <span data-ttu-id="d7013-216">Příkaz</span><span class="sxs-lookup"><span data-stu-id="d7013-216">Command</span></span>                             | <span data-ttu-id="d7013-217">Funkce</span><span class="sxs-lookup"><span data-stu-id="d7013-217">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="d7013-218">dotnet build</span><span class="sxs-lookup"><span data-stu-id="d7013-218">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="d7013-219">Vytvoří aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d7013-219">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="d7013-220">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="d7013-220">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="d7013-221">Vyčistit výstupy sestavení.</span><span class="sxs-lookup"><span data-stu-id="d7013-221">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="d7013-222">dotnet help</span><span class="sxs-lookup"><span data-stu-id="d7013-222">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="d7013-223">Zobrazí podrobnější dokumentaci pro příkaz online.</span><span class="sxs-lookup"><span data-stu-id="d7013-223">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="d7013-224">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="d7013-224">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="d7013-225">Migruje platný projekt verze Preview 2 na projekt .NET Core SDK 1,0.</span><span class="sxs-lookup"><span data-stu-id="d7013-225">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="d7013-226">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="d7013-226">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="d7013-227">Poskytuje přístup k příkazovému řádku MSBuild.</span><span class="sxs-lookup"><span data-stu-id="d7013-227">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="d7013-228">dotnet new</span><span class="sxs-lookup"><span data-stu-id="d7013-228">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="d7013-229">Inicializuje projekt C# nebo F# pro danou šablonu.</span><span class="sxs-lookup"><span data-stu-id="d7013-229">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="d7013-230">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="d7013-230">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="d7013-231">Vytvoří balíček NuGet vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="d7013-231">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="d7013-232">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="d7013-232">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="d7013-233">Publikuje aplikaci závislou na rozhraní .NET Framework nebo samostatnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d7013-233">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="d7013-234">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="d7013-234">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="d7013-235">Obnoví závislosti pro danou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d7013-235">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="d7013-236">dotnet run</span><span class="sxs-lookup"><span data-stu-id="d7013-236">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="d7013-237">Spustí aplikaci ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="d7013-237">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="d7013-238">dotnet run</span><span class="sxs-lookup"><span data-stu-id="d7013-238">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="d7013-239">Možnosti pro přidání, odebrání a výpis projektů v souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="d7013-239">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="d7013-240">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="d7013-240">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="d7013-241">Ukládá sestavení do úložiště balíčků modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="d7013-241">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="d7013-242">dotnet test</span><span class="sxs-lookup"><span data-stu-id="d7013-242">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="d7013-243">Spustí testy pomocí nástroje Test Runner.</span><span class="sxs-lookup"><span data-stu-id="d7013-243">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1x"></a>[<span data-ttu-id="d7013-244">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="d7013-244">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="d7013-245">Příkaz</span><span class="sxs-lookup"><span data-stu-id="d7013-245">Command</span></span>                             | <span data-ttu-id="d7013-246">Funkce</span><span class="sxs-lookup"><span data-stu-id="d7013-246">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="d7013-247">dotnet build</span><span class="sxs-lookup"><span data-stu-id="d7013-247">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="d7013-248">Vytvoří aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d7013-248">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="d7013-249">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="d7013-249">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="d7013-250">Vyčistit výstupy sestavení.</span><span class="sxs-lookup"><span data-stu-id="d7013-250">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="d7013-251">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="d7013-251">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="d7013-252">Migruje platný projekt verze Preview 2 na projekt .NET Core SDK 1,0.</span><span class="sxs-lookup"><span data-stu-id="d7013-252">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="d7013-253">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="d7013-253">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="d7013-254">Poskytuje přístup k příkazovému řádku MSBuild.</span><span class="sxs-lookup"><span data-stu-id="d7013-254">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="d7013-255">dotnet new</span><span class="sxs-lookup"><span data-stu-id="d7013-255">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="d7013-256">Inicializuje projekt C# nebo F# pro danou šablonu.</span><span class="sxs-lookup"><span data-stu-id="d7013-256">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="d7013-257">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="d7013-257">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="d7013-258">Vytvoří balíček NuGet vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="d7013-258">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="d7013-259">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="d7013-259">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="d7013-260">Publikuje aplikaci závislou na rozhraní .NET Framework nebo samostatnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d7013-260">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="d7013-261">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="d7013-261">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="d7013-262">Obnoví závislosti pro danou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d7013-262">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="d7013-263">dotnet run</span><span class="sxs-lookup"><span data-stu-id="d7013-263">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="d7013-264">Spustí aplikaci ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="d7013-264">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="d7013-265">dotnet run</span><span class="sxs-lookup"><span data-stu-id="d7013-265">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="d7013-266">Možnosti pro přidání, odebrání a výpis projektů v souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="d7013-266">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="d7013-267">dotnet test</span><span class="sxs-lookup"><span data-stu-id="d7013-267">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="d7013-268">Spustí testy pomocí nástroje Test Runner.</span><span class="sxs-lookup"><span data-stu-id="d7013-268">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="d7013-269">Odkazy na projekty</span><span class="sxs-lookup"><span data-stu-id="d7013-269">Project references</span></span>

<span data-ttu-id="d7013-270">Příkaz</span><span class="sxs-lookup"><span data-stu-id="d7013-270">Command</span></span> | <span data-ttu-id="d7013-271">Funkce</span><span class="sxs-lookup"><span data-stu-id="d7013-271">Function</span></span>
--- | ---
[<span data-ttu-id="d7013-272">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="d7013-272">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="d7013-273">Přidá odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="d7013-273">Adds a project reference.</span></span>
[<span data-ttu-id="d7013-274">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="d7013-274">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="d7013-275">Vypíše odkazy na projekt.</span><span class="sxs-lookup"><span data-stu-id="d7013-275">Lists project references.</span></span>
[<span data-ttu-id="d7013-276">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="d7013-276">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="d7013-277">Odebere odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="d7013-277">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="d7013-278">Balíčky NuGet</span><span class="sxs-lookup"><span data-stu-id="d7013-278">NuGet packages</span></span>

<span data-ttu-id="d7013-279">Příkaz</span><span class="sxs-lookup"><span data-stu-id="d7013-279">Command</span></span> | <span data-ttu-id="d7013-280">Funkce</span><span class="sxs-lookup"><span data-stu-id="d7013-280">Function</span></span>
--- | ---
[<span data-ttu-id="d7013-281">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="d7013-281">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="d7013-282">Přidá balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="d7013-282">Adds a NuGet package.</span></span>
[<span data-ttu-id="d7013-283">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="d7013-283">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="d7013-284">Odebere balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="d7013-284">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="d7013-285">Příkazy NuGet</span><span class="sxs-lookup"><span data-stu-id="d7013-285">NuGet commands</span></span>

<span data-ttu-id="d7013-286">Příkaz</span><span class="sxs-lookup"><span data-stu-id="d7013-286">Command</span></span> | <span data-ttu-id="d7013-287">Funkce</span><span class="sxs-lookup"><span data-stu-id="d7013-287">Function</span></span>
--- | ---
[<span data-ttu-id="d7013-288">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="d7013-288">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="d7013-289">Odstraní nebo zruší výpis balíčku ze serveru.</span><span class="sxs-lookup"><span data-stu-id="d7013-289">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="d7013-290">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="d7013-290">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="d7013-291">Vymaže nebo vypíše místní prostředky NuGet, jako je mezipaměť požadavků HTTP, dočasná mezipaměť nebo složka globálních balíčků v celém počítači.</span><span class="sxs-lookup"><span data-stu-id="d7013-291">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="d7013-292">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="d7013-292">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="d7013-293">Odešle balíček na server a publikuje ho.</span><span class="sxs-lookup"><span data-stu-id="d7013-293">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tool-path-and-local-tools-commands"></a><span data-ttu-id="d7013-294">Příkazy globálních nástrojů, nástrojů a cest a místních nástrojů</span><span class="sxs-lookup"><span data-stu-id="d7013-294">Global, tool-path, and local tools commands</span></span>

<span data-ttu-id="d7013-295">Nástroje jsou konzolové aplikace, které jsou nainstalovány z balíčků NuGet a jsou vyvolány z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="d7013-295">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="d7013-296">Můžete psát nástroje sami nebo instalovat nástroje napsané třetí stranou.</span><span class="sxs-lookup"><span data-stu-id="d7013-296">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="d7013-297">Nástroje jsou také známé jako globální nástroje, nástroje pro cestu nástrojů a místní nástroje.</span><span class="sxs-lookup"><span data-stu-id="d7013-297">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="d7013-298">Další informace najdete v tématu [Přehled nástrojů .NET Core](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="d7013-298">For more information, see [.NET Core tools overview](global-tools.md).</span></span> <span data-ttu-id="d7013-299">Nástroje pro globální a cestu nástrojů jsou k dispozici od .NET Core SDK 2,1.</span><span class="sxs-lookup"><span data-stu-id="d7013-299">Global and tool-path tools are available starting with .NET Core SDK 2.1.</span></span> <span data-ttu-id="d7013-300">K dispozici jsou místní nástroje od .NET Core SDK 3,0.</span><span class="sxs-lookup"><span data-stu-id="d7013-300">Local tools are available starting with .NET Core SDK 3.0.</span></span>

<span data-ttu-id="d7013-301">Příkaz</span><span class="sxs-lookup"><span data-stu-id="d7013-301">Command</span></span> | <span data-ttu-id="d7013-302">Funkce</span><span class="sxs-lookup"><span data-stu-id="d7013-302">Function</span></span>
--- | ---
[<span data-ttu-id="d7013-303">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="d7013-303">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="d7013-304">Nainstaluje nástroj na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="d7013-304">Installs a tool on your machine.</span></span>
[<span data-ttu-id="d7013-305">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="d7013-305">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="d7013-306">Zobrazí seznam všech nástrojů, které jsou aktuálně nainstalované na vašem počítači, na základě globálních nástrojů, nástrojů a cest.</span><span class="sxs-lookup"><span data-stu-id="d7013-306">Lists all global, tool-path, or local tools currently installed on your machine.</span></span>
[<span data-ttu-id="d7013-307">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="d7013-307">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="d7013-308">Odinstaluje nástroj z počítače.</span><span class="sxs-lookup"><span data-stu-id="d7013-308">Uninstalls a tool from your machine.</span></span>
[<span data-ttu-id="d7013-309">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="d7013-309">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="d7013-310">Aktualizuje nástroj, který je nainstalovaný na vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="d7013-310">Updates a tool that is installed on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="d7013-311">Další nástroje</span><span class="sxs-lookup"><span data-stu-id="d7013-311">Additional tools</span></span>

<span data-ttu-id="d7013-312">Počínaje .NET Core SDK 2.1.300 je teď k dispozici několik nástrojů, které byly k dispozici pouze pro jednotlivé projekty pomocí `DotnetCliToolReference` jsou nyní k dispozici jako součást .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="d7013-312">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="d7013-313">Tyto nástroje jsou uvedené v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="d7013-313">These tools are listed in the following table:</span></span>

| <span data-ttu-id="d7013-314">Nástroj</span><span class="sxs-lookup"><span data-stu-id="d7013-314">Tool</span></span>                                              | <span data-ttu-id="d7013-315">Funkce</span><span class="sxs-lookup"><span data-stu-id="d7013-315">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="d7013-316">vývoj – certifikáty</span><span class="sxs-lookup"><span data-stu-id="d7013-316">dev-certs</span></span>                                         | <span data-ttu-id="d7013-317">Vytvoří a spravuje vývojové certifikáty.</span><span class="sxs-lookup"><span data-stu-id="d7013-317">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="d7013-318">EF</span><span class="sxs-lookup"><span data-stu-id="d7013-318">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="d7013-319">Entity Framework Core nástroje příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="d7013-319">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="d7013-320">sql-cache</span><span class="sxs-lookup"><span data-stu-id="d7013-320">sql-cache</span></span>                                         | <span data-ttu-id="d7013-321">Nástroje příkazového řádku pro SQL Server cache</span><span class="sxs-lookup"><span data-stu-id="d7013-321">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="d7013-322">uživatel – tajné klíče</span><span class="sxs-lookup"><span data-stu-id="d7013-322">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="d7013-323">Spravuje tajné klíče uživatele.</span><span class="sxs-lookup"><span data-stu-id="d7013-323">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="d7013-324">sledovací</span><span class="sxs-lookup"><span data-stu-id="d7013-324">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="d7013-325">Spustí sledovací proces souborů, který spustí příkaz, když se soubory změní.</span><span class="sxs-lookup"><span data-stu-id="d7013-325">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="d7013-326">Další informace o jednotlivých nástrojích získáte, když zadáte `dotnet <tool-name> --help`.</span><span class="sxs-lookup"><span data-stu-id="d7013-326">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="d7013-327">Příklady</span><span class="sxs-lookup"><span data-stu-id="d7013-327">Examples</span></span>

<span data-ttu-id="d7013-328">Vytvoří novou konzolovou aplikaci .NET Core:</span><span class="sxs-lookup"><span data-stu-id="d7013-328">Creates a new .NET Core console application:</span></span>

`dotnet new console`

<span data-ttu-id="d7013-329">Obnovit závislosti pro danou aplikaci:</span><span class="sxs-lookup"><span data-stu-id="d7013-329">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="d7013-330">Sestavení projektu a jeho závislostí v daném adresáři:</span><span class="sxs-lookup"><span data-stu-id="d7013-330">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="d7013-331">Spusťte knihovnu DLL aplikace, například `myapp.dll`:</span><span class="sxs-lookup"><span data-stu-id="d7013-331">Run an application DLL, such as `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="d7013-332">Proměnné prostředí</span><span class="sxs-lookup"><span data-stu-id="d7013-332">Environment variables</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="d7013-333">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="d7013-333">.NET Core 2.1</span></span>](#tab/netcore21)

`DOTNET_PACKAGES`

<span data-ttu-id="d7013-334">Složka globálních balíčků.</span><span class="sxs-lookup"><span data-stu-id="d7013-334">The global packages folder.</span></span> <span data-ttu-id="d7013-335">Pokud není nastavené, použije se výchozí nastavení `~/.nuget/packages` v systému UNIX nebo `%userprofile%\.nuget\packages` ve Windows.</span><span class="sxs-lookup"><span data-stu-id="d7013-335">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="d7013-336">Určuje umístění indexu údržby používaného sdíleným hostitelem při načítání modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="d7013-336">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="d7013-337">Určuje, jestli se data o využití nástrojů .NET Core shromažďují a odesílají do Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="d7013-337">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="d7013-338">Nastavte na `true` pro výslovný souhlas funkce telemetrie (hodnoty `true`, `1`nebo `yes` přijaté).</span><span class="sxs-lookup"><span data-stu-id="d7013-338">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="d7013-339">Jinak nastavte `false` tak, aby se přihlásil k funkcím telemetrie (hodnoty `false`, `0`nebo přijaté `no`).</span><span class="sxs-lookup"><span data-stu-id="d7013-339">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="d7013-340">Pokud není nastavená, výchozí hodnota je `false` a funkce telemetrie je aktivní.</span><span class="sxs-lookup"><span data-stu-id="d7013-340">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="d7013-341">Určuje, zda je rozhraní .NET Core Runtime, sdílené rozhraní nebo sada SDK vyřešeno z globálního umístění.</span><span class="sxs-lookup"><span data-stu-id="d7013-341">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="d7013-342">Pokud není nastavená, použije se výchozí hodnota `true`.</span><span class="sxs-lookup"><span data-stu-id="d7013-342">If not set, it defaults to `true`.</span></span> <span data-ttu-id="d7013-343">Nastavte na `false`, aby se nepřeložily z globálního umístění a měly izolované instalace .NET Core (hodnoty `0` nebo `false` jsou přijaté).</span><span class="sxs-lookup"><span data-stu-id="d7013-343">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="d7013-344">Další informace o vyhledávání na více úrovních najdete v tématu [SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="d7013-344">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

<span data-ttu-id="d7013-345">Zakáže posunutí dílčí verze, pokud je nastaveno na `0`.</span><span class="sxs-lookup"><span data-stu-id="d7013-345">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="d7013-346">Další informace najdete v tématu o tom, jak [Posunout](../whats-new/dotnet-core-2-1.md#roll-forward)nahoru.</span><span class="sxs-lookup"><span data-stu-id="d7013-346">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

# <a name="net-core-20"></a>[<span data-ttu-id="d7013-347">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="d7013-347">.NET Core 2.0</span></span>](#tab/netcore20)

`DOTNET_PACKAGES`

<span data-ttu-id="d7013-348">Mezipaměť primárního balíčku.</span><span class="sxs-lookup"><span data-stu-id="d7013-348">The primary package cache.</span></span> <span data-ttu-id="d7013-349">Pokud není nastavené, použije se výchozí nastavení `$HOME/.nuget/packages` v systému UNIX nebo `%userprofile%\.nuget\packages` ve Windows.</span><span class="sxs-lookup"><span data-stu-id="d7013-349">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="d7013-350">Určuje umístění indexu údržby používaného sdíleným hostitelem při načítání modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="d7013-350">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="d7013-351">Určuje, jestli se data o využití nástrojů .NET Core shromažďují a odesílají do Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="d7013-351">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="d7013-352">Nastavte na `true` pro výslovný souhlas funkce telemetrie (hodnoty `true`, `1`nebo `yes` přijaté).</span><span class="sxs-lookup"><span data-stu-id="d7013-352">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="d7013-353">Jinak nastavte `false` tak, aby se přihlásil k funkcím telemetrie (hodnoty `false`, `0`nebo přijaté `no`).</span><span class="sxs-lookup"><span data-stu-id="d7013-353">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="d7013-354">Pokud není nastavená, výchozí hodnota je `false` a funkce telemetrie je aktivní.</span><span class="sxs-lookup"><span data-stu-id="d7013-354">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="d7013-355">Určuje, zda je rozhraní .NET Core Runtime, sdílené rozhraní nebo sada SDK vyřešeno z globálního umístění.</span><span class="sxs-lookup"><span data-stu-id="d7013-355">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="d7013-356">Pokud není nastavená, použije se výchozí hodnota `true`.</span><span class="sxs-lookup"><span data-stu-id="d7013-356">If not set, it defaults to `true`.</span></span> <span data-ttu-id="d7013-357">Nastavte na `false`, aby se nepřeložily z globálního umístění a měly izolované instalace .NET Core (hodnoty `0` nebo `false` jsou přijaté).</span><span class="sxs-lookup"><span data-stu-id="d7013-357">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="d7013-358">Další informace o vyhledávání na více úrovních najdete v tématu [SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="d7013-358">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1x"></a>[<span data-ttu-id="d7013-359">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="d7013-359">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="d7013-360">Mezipaměť primárního balíčku.</span><span class="sxs-lookup"><span data-stu-id="d7013-360">The primary package cache.</span></span> <span data-ttu-id="d7013-361">Pokud není nastavené, použije se výchozí nastavení `$HOME/.nuget/packages` v systému UNIX nebo `%userprofile%\.nuget\packages` ve Windows.</span><span class="sxs-lookup"><span data-stu-id="d7013-361">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="d7013-362">Určuje umístění indexu údržby používaného sdíleným hostitelem při načítání modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="d7013-362">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="d7013-363">Určuje, jestli se data o využití nástrojů .NET Core shromažďují a odesílají do Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="d7013-363">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="d7013-364">Nastavte na `true` pro výslovný souhlas funkce telemetrie (hodnoty `true`, `1`nebo `yes` přijaté).</span><span class="sxs-lookup"><span data-stu-id="d7013-364">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="d7013-365">Jinak nastavte `false` tak, aby se přihlásil k funkcím telemetrie (hodnoty `false`, `0`nebo přijaté `no`).</span><span class="sxs-lookup"><span data-stu-id="d7013-365">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="d7013-366">Pokud není nastavená, výchozí hodnota je `false` a funkce telemetrie je aktivní.</span><span class="sxs-lookup"><span data-stu-id="d7013-366">If not set, the default is `false` and the telemetry feature is active.</span></span>

---

## <a name="see-also"></a><span data-ttu-id="d7013-367">Viz také</span><span class="sxs-lookup"><span data-stu-id="d7013-367">See also</span></span>

- [<span data-ttu-id="d7013-368">Běhové konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="d7013-368">Runtime Configuration Files</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [<span data-ttu-id="d7013-369">Nastavení konfigurace runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="d7013-369">.NET Core run-time configuration settings</span></span>](../run-time-config/index.md)
