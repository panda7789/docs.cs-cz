---
title: příkaz dotnet run
description: Příkaz dotnet Run poskytuje pohodlný způsob, jak spustit aplikaci ze zdrojového kódu.
ms.date: 10/31/2019
ms.openlocfilehash: 5920f0d1f04204b286fdf6f51f5fd13644846390
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734100"
---
# <a name="dotnet-run"></a><span data-ttu-id="9f572-103">dotnet run</span><span class="sxs-lookup"><span data-stu-id="9f572-103">dotnet run</span></span>

<span data-ttu-id="9f572-104">**Tento článek se týká:** ✔️ .NET Core 1. x SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="9f572-104">**This article applies to:** ✔️ .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="9f572-105">Name</span><span class="sxs-lookup"><span data-stu-id="9f572-105">Name</span></span>

<span data-ttu-id="9f572-106">`dotnet run` – spustí zdrojový kód bez explicitních příkazů Compile nebo Launch.</span><span class="sxs-lookup"><span data-stu-id="9f572-106">`dotnet run` - Runs source code without any explicit compile or launch commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9f572-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="9f572-107">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="9f572-108">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="9f572-108">.NET Core 3.0</span></span>](#tab/netcore30)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--interactive] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [-r|--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="9f572-109">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="9f572-109">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="9f572-110">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="9f572-110">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="9f572-111">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="9f572-111">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]]
dotnet run [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="9f572-112">Popis</span><span class="sxs-lookup"><span data-stu-id="9f572-112">Description</span></span>

<span data-ttu-id="9f572-113">Příkaz `dotnet run` poskytuje pohodlný způsob, jak spustit aplikaci ze zdrojového kódu pomocí jednoho příkazu.</span><span class="sxs-lookup"><span data-stu-id="9f572-113">The `dotnet run` command provides a convenient option to run your application from the source code with one command.</span></span> <span data-ttu-id="9f572-114">Je vhodný pro rychlý iterativní vývoj z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="9f572-114">It's useful for fast iterative development from the command line.</span></span> <span data-ttu-id="9f572-115">Příkaz závisí na příkazu [`dotnet build`](dotnet-build.md) pro sestavení kódu.</span><span class="sxs-lookup"><span data-stu-id="9f572-115">The command depends on the [`dotnet build`](dotnet-build.md) command to build the code.</span></span> <span data-ttu-id="9f572-116">Všechny požadavky na sestavení, například, že je nutné nejprve obnovit projekt, platí pro `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="9f572-116">Any requirements for the build, such as that the project must be restored first, apply to `dotnet run` as well.</span></span>

<span data-ttu-id="9f572-117">Výstupní soubory jsou zapsány do výchozího umístění, které je `bin/<configuration>/<target>`.</span><span class="sxs-lookup"><span data-stu-id="9f572-117">Output files are written into the default location, which is `bin/<configuration>/<target>`.</span></span> <span data-ttu-id="9f572-118">Pokud máte například aplikaci `netcoreapp2.1` a spustíte `dotnet run`, výstup je umístěný v `bin/Debug/netcoreapp2.1`.</span><span class="sxs-lookup"><span data-stu-id="9f572-118">For example if you have a `netcoreapp2.1` application and you run `dotnet run`, the output is placed in `bin/Debug/netcoreapp2.1`.</span></span> <span data-ttu-id="9f572-119">Soubory jsou v případě potřeby přepsány.</span><span class="sxs-lookup"><span data-stu-id="9f572-119">Files are overwritten as needed.</span></span> <span data-ttu-id="9f572-120">Dočasné soubory jsou umístěny v adresáři `obj`.</span><span class="sxs-lookup"><span data-stu-id="9f572-120">Temporary files are placed in the `obj` directory.</span></span>

<span data-ttu-id="9f572-121">Pokud projekt určuje více rozhraní, spuštění `dotnet run` způsobí chybu, pokud není použita možnost `-f|--framework <FRAMEWORK>` k určení architektury.</span><span class="sxs-lookup"><span data-stu-id="9f572-121">If the project specifies multiple frameworks, executing `dotnet run` results in an error unless the `-f|--framework <FRAMEWORK>` option is used to specify the framework.</span></span>

<span data-ttu-id="9f572-122">Příkaz `dotnet run` se používá v kontextu projektů, nikoli ve vytvořených sestaveních.</span><span class="sxs-lookup"><span data-stu-id="9f572-122">The `dotnet run` command is used in the context of projects, not built assemblies.</span></span> <span data-ttu-id="9f572-123">Pokud se pokoušíte spustit knihovnu DLL aplikace závislou na rozhraní, je nutné použít příkaz [dotnet](dotnet.md) bez příkazu.</span><span class="sxs-lookup"><span data-stu-id="9f572-123">If you're trying to run a framework-dependent application DLL instead, you must use [dotnet](dotnet.md) without a command.</span></span> <span data-ttu-id="9f572-124">Pokud například chcete spustit `myapp.dll`, použijte:</span><span class="sxs-lookup"><span data-stu-id="9f572-124">For example, to run `myapp.dll`, use:</span></span>

```dotnetcli
dotnet myapp.dll
```

<span data-ttu-id="9f572-125">Další informace o ovladači `dotnet` naleznete v tématu [.NET Core Command line Tools (CLI)](index.md) .</span><span class="sxs-lookup"><span data-stu-id="9f572-125">For more information on the `dotnet` driver, see the [.NET Core Command Line Tools (CLI)](index.md) topic.</span></span>

<span data-ttu-id="9f572-126">Chcete-li spustit aplikaci, příkaz `dotnet run` vyřeší závislosti aplikace, které jsou mimo sdílený modul runtime z mezipaměti NuGet.</span><span class="sxs-lookup"><span data-stu-id="9f572-126">To run the application, the `dotnet run` command resolves the dependencies of the application that are outside of the shared runtime from the NuGet cache.</span></span> <span data-ttu-id="9f572-127">Protože používá závislosti v mezipaměti, nedoporučuje se používat `dotnet run` ke spouštění aplikací v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="9f572-127">Because it uses cached dependencies, it's not recommended to use `dotnet run` to run applications in production.</span></span> <span data-ttu-id="9f572-128">Místo toho [vytvořte nasazení](../deploying/index.md) pomocí příkazu [`dotnet publish`](dotnet-publish.md) a nasaďte publikovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="9f572-128">Instead, [create a deployment](../deploying/index.md) using the [`dotnet publish`](dotnet-publish.md) command and deploy the published output.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a><span data-ttu-id="9f572-129">Možnosti</span><span class="sxs-lookup"><span data-stu-id="9f572-129">Options</span></span>

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="9f572-130">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="9f572-130">.NET Core 3.0</span></span>](#tab/netcore30)

`--`

<span data-ttu-id="9f572-131">Odděluje argumenty pro `dotnet run` z argumentů pro spouštěnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9f572-131">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="9f572-132">Všechny argumenty po tomto oddělovači jsou předány spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="9f572-132">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="9f572-133">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="9f572-133">Defines the build configuration.</span></span> <span data-ttu-id="9f572-134">Výchozí hodnota pro většinu projektů je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="9f572-134">The default value for most projects is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="9f572-135">Vytvoří a spustí aplikaci pomocí zadaného [rozhraní](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="9f572-135">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="9f572-136">Rozhraní musí být určeno v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="9f572-136">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="9f572-137">Vynutí vyřešení všech závislostí i v případě, že bylo poslední obnovení úspěšné.</span><span class="sxs-lookup"><span data-stu-id="9f572-137">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="9f572-138">Zadání tohoto příznaku je stejné jako odstranění souboru *Project. assets. JSON* .</span><span class="sxs-lookup"><span data-stu-id="9f572-138">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="9f572-139">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="9f572-139">Prints out a short help for the command.</span></span>

`--interactive`

<span data-ttu-id="9f572-140">Umožňuje příkazu zastavit a počkat na vstup nebo akci uživatele (například k dokončení ověřování).</span><span class="sxs-lookup"><span data-stu-id="9f572-140">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="9f572-141">Název spouštěcího profilu (pokud existuje), který se má použít při spouštění aplikace</span><span class="sxs-lookup"><span data-stu-id="9f572-141">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="9f572-142">Spouštěcí profily jsou definované v souboru *launchSettings. JSON* a obvykle se nazývají `Development`, `Staging`a `Production`.</span><span class="sxs-lookup"><span data-stu-id="9f572-142">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="9f572-143">Další informace najdete v tématu [práce s více prostředími](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="9f572-143">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="9f572-144">Před spuštěním nevytvoří projekt.</span><span class="sxs-lookup"><span data-stu-id="9f572-144">Doesn't build the project before running.</span></span> <span data-ttu-id="9f572-145">Také implicitně nastaví příznak `--no-restore`.</span><span class="sxs-lookup"><span data-stu-id="9f572-145">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="9f572-146">Při obnovení projektu s odkazy z projektu na projekt (P2P) obnoví kořenový projekt a nikoli odkazy.</span><span class="sxs-lookup"><span data-stu-id="9f572-146">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="9f572-147">Nepokusí se nakonfigurovat aplikaci pomocí *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="9f572-147">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="9f572-148">Při spuštění příkazu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="9f572-148">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="9f572-149">Určuje cestu k souboru projektu, který se má spustit (název složky nebo úplná cesta).</span><span class="sxs-lookup"><span data-stu-id="9f572-149">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="9f572-150">Pokud není zadaný, použije se ve výchozím nastavení aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="9f572-150">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="9f572-151">Určuje cílový modul runtime pro obnovení balíčků pro.</span><span class="sxs-lookup"><span data-stu-id="9f572-151">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="9f572-152">Seznam identifikátorů modulu runtime (identifikátorů RID) najdete v [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="9f572-152">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="9f572-153">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="9f572-153">Sets the verbosity level of the command.</span></span> <span data-ttu-id="9f572-154">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="9f572-154">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="9f572-155">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="9f572-155">.NET Core 2.1</span></span>](#tab/netcore21)

`--`

<span data-ttu-id="9f572-156">Odděluje argumenty pro `dotnet run` z argumentů pro spouštěnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9f572-156">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="9f572-157">Všechny argumenty po tomto oddělovači jsou předány spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="9f572-157">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="9f572-158">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="9f572-158">Defines the build configuration.</span></span> <span data-ttu-id="9f572-159">Výchozí hodnota pro většinu projektů je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="9f572-159">The default value for most projects is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="9f572-160">Vytvoří a spustí aplikaci pomocí zadaného [rozhraní](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="9f572-160">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="9f572-161">Rozhraní musí být určeno v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="9f572-161">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="9f572-162">Vynutí vyřešení všech závislostí i v případě, že bylo poslední obnovení úspěšné.</span><span class="sxs-lookup"><span data-stu-id="9f572-162">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="9f572-163">Zadání tohoto příznaku je stejné jako odstranění souboru *Project. assets. JSON* .</span><span class="sxs-lookup"><span data-stu-id="9f572-163">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="9f572-164">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="9f572-164">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="9f572-165">Název spouštěcího profilu (pokud existuje), který se má použít při spouštění aplikace</span><span class="sxs-lookup"><span data-stu-id="9f572-165">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="9f572-166">Spouštěcí profily jsou definované v souboru *launchSettings. JSON* a obvykle se nazývají `Development`, `Staging`a `Production`.</span><span class="sxs-lookup"><span data-stu-id="9f572-166">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="9f572-167">Další informace najdete v tématu [práce s více prostředími](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="9f572-167">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="9f572-168">Před spuštěním nevytvoří projekt.</span><span class="sxs-lookup"><span data-stu-id="9f572-168">Doesn't build the project before running.</span></span> <span data-ttu-id="9f572-169">Také implicitně nastaví příznak `--no-restore`.</span><span class="sxs-lookup"><span data-stu-id="9f572-169">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="9f572-170">Při obnovení projektu s odkazy z projektu na projekt (P2P) obnoví kořenový projekt a nikoli odkazy.</span><span class="sxs-lookup"><span data-stu-id="9f572-170">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="9f572-171">Nepokusí se nakonfigurovat aplikaci pomocí *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="9f572-171">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="9f572-172">Při spuštění příkazu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="9f572-172">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="9f572-173">Určuje cestu k souboru projektu, který se má spustit (název složky nebo úplná cesta).</span><span class="sxs-lookup"><span data-stu-id="9f572-173">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="9f572-174">Pokud není zadaný, použije se ve výchozím nastavení aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="9f572-174">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="9f572-175">Určuje cílový modul runtime pro obnovení balíčků pro.</span><span class="sxs-lookup"><span data-stu-id="9f572-175">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="9f572-176">Seznam identifikátorů modulu runtime (identifikátorů RID) najdete v [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="9f572-176">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="9f572-177">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="9f572-177">Sets the verbosity level of the command.</span></span> <span data-ttu-id="9f572-178">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="9f572-178">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="9f572-179">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="9f572-179">.NET Core 2.0</span></span>](#tab/netcore20)

`--`

<span data-ttu-id="9f572-180">Odděluje argumenty pro `dotnet run` z argumentů pro spouštěnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9f572-180">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="9f572-181">Všechny argumenty po tomto oddělovači jsou předány spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="9f572-181">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="9f572-182">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="9f572-182">Defines the build configuration.</span></span> <span data-ttu-id="9f572-183">Výchozí hodnota pro většinu projektů je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="9f572-183">The default for most projects value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="9f572-184">Vytvoří a spustí aplikaci pomocí zadaného [rozhraní](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="9f572-184">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="9f572-185">Rozhraní musí být určeno v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="9f572-185">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="9f572-186">Vynutí vyřešení všech závislostí i v případě, že bylo poslední obnovení úspěšné.</span><span class="sxs-lookup"><span data-stu-id="9f572-186">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="9f572-187">Zadání tohoto příznaku je stejné jako odstranění souboru *Project. assets. JSON* .</span><span class="sxs-lookup"><span data-stu-id="9f572-187">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="9f572-188">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="9f572-188">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="9f572-189">Název spouštěcího profilu (pokud existuje), který se má použít při spouštění aplikace</span><span class="sxs-lookup"><span data-stu-id="9f572-189">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="9f572-190">Spouštěcí profily jsou definované v souboru *launchSettings. JSON* a obvykle se nazývají `Development`, `Staging`a `Production`.</span><span class="sxs-lookup"><span data-stu-id="9f572-190">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="9f572-191">Další informace najdete v tématu [práce s více prostředími](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="9f572-191">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="9f572-192">Před spuštěním nevytvoří projekt.</span><span class="sxs-lookup"><span data-stu-id="9f572-192">Doesn't build the project before running.</span></span> <span data-ttu-id="9f572-193">Také implicitně nastaví příznak `--no-restore`.</span><span class="sxs-lookup"><span data-stu-id="9f572-193">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="9f572-194">Při obnovení projektu s odkazy z projektu na projekt (P2P) obnoví kořenový projekt a nikoli odkazy.</span><span class="sxs-lookup"><span data-stu-id="9f572-194">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="9f572-195">Nepokusí se nakonfigurovat aplikaci pomocí *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="9f572-195">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="9f572-196">Při spuštění příkazu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="9f572-196">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="9f572-197">Určuje cestu k souboru projektu, který se má spustit (název složky nebo úplná cesta).</span><span class="sxs-lookup"><span data-stu-id="9f572-197">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="9f572-198">Pokud není zadaný, použije se ve výchozím nastavení aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="9f572-198">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="9f572-199">Určuje cílový modul runtime pro obnovení balíčků pro.</span><span class="sxs-lookup"><span data-stu-id="9f572-199">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="9f572-200">Seznam identifikátorů modulu runtime (identifikátorů RID) najdete v [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="9f572-200">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="9f572-201">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="9f572-201">.NET Core 1.x</span></span>](#tab/netcore1x)

`--`

<span data-ttu-id="9f572-202">Odděluje argumenty pro `dotnet run` z argumentů pro spouštěnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9f572-202">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="9f572-203">Všechny argumenty po tomto oddělovači jsou předány spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="9f572-203">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="9f572-204">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="9f572-204">Defines the build configuration.</span></span> <span data-ttu-id="9f572-205">Výchozí hodnota pro většinu projektů je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="9f572-205">The default value for most projects is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="9f572-206">Vytvoří a spustí aplikaci pomocí zadaného [rozhraní](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="9f572-206">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="9f572-207">Rozhraní musí být určeno v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="9f572-207">The framework must be specified in the project file.</span></span>

`-h|--help`

<span data-ttu-id="9f572-208">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="9f572-208">Prints out a short help for the command.</span></span>

`-p|--project <PATH/PROJECT.csproj>`

<span data-ttu-id="9f572-209">Určuje cestu a název souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="9f572-209">Specifies the path and name of the project file.</span></span> <span data-ttu-id="9f572-210">(Podívejte se na poznámku.) Pokud není zadaný, použije se ve výchozím nastavení aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="9f572-210">(See the NOTE.) If not specified, it defaults to the current directory.</span></span>

> [!NOTE]
> <span data-ttu-id="9f572-211">Použijte cestu a název souboru projektu s možností `-p|--project`.</span><span class="sxs-lookup"><span data-stu-id="9f572-211">Use the path and name of the project file with the `-p|--project` option.</span></span> <span data-ttu-id="9f572-212">Regrese v rozhraní příkazového řádku zabraňuje tomu, aby poskytovala cestu ke složce .NET Core SDK 1. x.</span><span class="sxs-lookup"><span data-stu-id="9f572-212">A regression in the CLI prevents providing a folder path with .NET Core SDK 1.x.</span></span> <span data-ttu-id="9f572-213">Další informace o tomto problému naleznete v tématu [dotnet Run-p. nelze spustit projekt (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).</span><span class="sxs-lookup"><span data-stu-id="9f572-213">For more information about this issue, see [dotnet run -p, can not start a project (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).</span></span>

---

## <a name="examples"></a><span data-ttu-id="9f572-214">Příklady</span><span class="sxs-lookup"><span data-stu-id="9f572-214">Examples</span></span>

<span data-ttu-id="9f572-215">Spustit projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="9f572-215">Run the project in the current directory:</span></span>

`dotnet run`

<span data-ttu-id="9f572-216">Spustit zadaný projekt:</span><span class="sxs-lookup"><span data-stu-id="9f572-216">Run the specified project:</span></span>

`dotnet run --project ./projects/proj1/proj1.csproj`

<span data-ttu-id="9f572-217">Spustí projekt v aktuálním adresáři (`--help` argument v tomto příkladu je předán do aplikace, protože je použita možnost prázdné `--`):</span><span class="sxs-lookup"><span data-stu-id="9f572-217">Run the project in the current directory (the `--help` argument in this example is passed to the application, since the blank `--` option is used):</span></span>

`dotnet run --configuration Release -- --help`

<span data-ttu-id="9f572-218">Obnovte závislosti a nástroje pro projekt v aktuálním adresáři pouze s minimálním výstupem a potom spusťte projekt: (.NET Core SDK 2,0 a novější verze):</span><span class="sxs-lookup"><span data-stu-id="9f572-218">Restore dependencies and tools for the project in the current directory only showing minimal output and then run the project: (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet run --verbosity m`
