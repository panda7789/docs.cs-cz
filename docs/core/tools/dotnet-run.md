---
title: příkaz dotnet run
description: Příkaz dotnet Run poskytuje pohodlný způsob, jak spustit aplikaci ze zdrojového kódu.
ms.date: 05/29/2018
ms.openlocfilehash: ec2a24b78f435dd1905ec67b6f3f4a4ec3f7e7fa
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117480"
---
# <a name="dotnet-run"></a><span data-ttu-id="0c943-103">dotnet run</span><span class="sxs-lookup"><span data-stu-id="0c943-103">dotnet run</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="0c943-104">Name</span><span class="sxs-lookup"><span data-stu-id="0c943-104">Name</span></span>

<span data-ttu-id="0c943-105">`dotnet run`-Spustí zdrojový kód bez explicitních příkazů Compile nebo Launch.</span><span class="sxs-lookup"><span data-stu-id="0c943-105">`dotnet run` - Runs source code without any explicit compile or launch commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0c943-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="0c943-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="0c943-107">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="0c943-107">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="0c943-108">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="0c943-108">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0c943-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="0c943-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]]
dotnet run [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="0c943-110">Popis</span><span class="sxs-lookup"><span data-stu-id="0c943-110">Description</span></span>

<span data-ttu-id="0c943-111">`dotnet run` Příkaz nabízí pohodlný způsob, jak spustit aplikaci ze zdrojového kódu pomocí jednoho příkazu.</span><span class="sxs-lookup"><span data-stu-id="0c943-111">The `dotnet run` command provides a convenient option to run your application from the source code with one command.</span></span> <span data-ttu-id="0c943-112">Je vhodný pro rychlý iterativní vývoj z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="0c943-112">It's useful for fast iterative development from the command line.</span></span> <span data-ttu-id="0c943-113">Příkaz závisí na [`dotnet build`](dotnet-build.md) příkazu pro sestavení kódu.</span><span class="sxs-lookup"><span data-stu-id="0c943-113">The command depends on the [`dotnet build`](dotnet-build.md) command to build the code.</span></span> <span data-ttu-id="0c943-114">Všechny požadavky na sestavení, jako je třeba projekt, musí být nejprve obnoveny, platí také `dotnet run` pro něj.</span><span class="sxs-lookup"><span data-stu-id="0c943-114">Any requirements for the build, such as that the project must be restored first, apply to `dotnet run` as well.</span></span>

<span data-ttu-id="0c943-115">Výstupní soubory jsou zapsány do výchozího umístění, což `bin/<configuration>/<target>`je.</span><span class="sxs-lookup"><span data-stu-id="0c943-115">Output files are written into the default location, which is `bin/<configuration>/<target>`.</span></span> <span data-ttu-id="0c943-116">Například pokud `netcoreapp2.1` máte aplikaci a spustíte `dotnet run`, výstup je umístěný v `bin/Debug/netcoreapp2.1`.</span><span class="sxs-lookup"><span data-stu-id="0c943-116">For example if you have a `netcoreapp2.1` application and you run `dotnet run`, the output is placed in `bin/Debug/netcoreapp2.1`.</span></span> <span data-ttu-id="0c943-117">Soubory jsou v případě potřeby přepsány.</span><span class="sxs-lookup"><span data-stu-id="0c943-117">Files are overwritten as needed.</span></span> <span data-ttu-id="0c943-118">Dočasné soubory jsou umístěny v `obj` adresáři.</span><span class="sxs-lookup"><span data-stu-id="0c943-118">Temporary files are placed in the `obj` directory.</span></span>

<span data-ttu-id="0c943-119">Pokud projekt určuje více rozhraní, spuštění `dotnet run` způsobí chybu, `-f|--framework <FRAMEWORK>` Pokud není použita možnost pro určení rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0c943-119">If the project specifies multiple frameworks, executing `dotnet run` results in an error unless the `-f|--framework <FRAMEWORK>` option is used to specify the framework.</span></span>

<span data-ttu-id="0c943-120">`dotnet run` Příkaz se používá v kontextu projektů, nesestavených sestavení.</span><span class="sxs-lookup"><span data-stu-id="0c943-120">The `dotnet run` command is used in the context of projects, not built assemblies.</span></span> <span data-ttu-id="0c943-121">Pokud se pokoušíte spustit knihovnu DLL aplikace závislou na rozhraní, je nutné použít příkaz [dotnet](dotnet.md) bez příkazu.</span><span class="sxs-lookup"><span data-stu-id="0c943-121">If you're trying to run a framework-dependent application DLL instead, you must use [dotnet](dotnet.md) without a command.</span></span> <span data-ttu-id="0c943-122">Pokud například chcete spustit `myapp.dll`, použijte:</span><span class="sxs-lookup"><span data-stu-id="0c943-122">For example, to run `myapp.dll`, use:</span></span>

```dotnetcli
dotnet myapp.dll
```

<span data-ttu-id="0c943-123">Další informace o `dotnet` ovladači naleznete v tématu [.NET Core Command line Tools (CLI)](index.md) .</span><span class="sxs-lookup"><span data-stu-id="0c943-123">For more information on the `dotnet` driver, see the [.NET Core Command Line Tools (CLI)](index.md) topic.</span></span>

<span data-ttu-id="0c943-124">Pro spuštění aplikace `dotnet run` příkaz vyřeší závislosti aplikace, které jsou mimo sdílený modul runtime z mezipaměti NuGet.</span><span class="sxs-lookup"><span data-stu-id="0c943-124">To run the application, the `dotnet run` command resolves the dependencies of the application that are outside of the shared runtime from the NuGet cache.</span></span> <span data-ttu-id="0c943-125">Protože používá závislosti v mezipaměti, nedoporučuje se používat `dotnet run` ke spouštění aplikací v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="0c943-125">Because it uses cached dependencies, it's not recommended to use `dotnet run` to run applications in production.</span></span> <span data-ttu-id="0c943-126">Místo toho [vytvořte nasazení](../deploying/index.md) pomocí [`dotnet publish`](dotnet-publish.md) příkazu a nasaďte publikovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="0c943-126">Instead, [create a deployment](../deploying/index.md) using the [`dotnet publish`](dotnet-publish.md) command and deploy the published output.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a><span data-ttu-id="0c943-127">Možnosti</span><span class="sxs-lookup"><span data-stu-id="0c943-127">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="0c943-128">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="0c943-128">.NET Core 2.1</span></span>](#tab/netcore21)

`--`

<span data-ttu-id="0c943-129">Odděluje argumenty `dotnet run` z argumentů pro spouštěnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0c943-129">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="0c943-130">Všechny argumenty po tomto oddělovači jsou předány spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="0c943-130">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="0c943-131">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="0c943-131">Defines the build configuration.</span></span> <span data-ttu-id="0c943-132">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="0c943-132">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="0c943-133">Vytvoří a spustí aplikaci pomocí zadaného [rozhraní](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="0c943-133">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="0c943-134">Rozhraní musí být určeno v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="0c943-134">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="0c943-135">Vynutí vyřešení všech závislostí i v případě, že bylo poslední obnovení úspěšné.</span><span class="sxs-lookup"><span data-stu-id="0c943-135">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="0c943-136">Zadání tohoto příznaku je stejné jako odstranění souboru *Project. assets. JSON* .</span><span class="sxs-lookup"><span data-stu-id="0c943-136">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="0c943-137">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="0c943-137">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="0c943-138">Název spouštěcího profilu (pokud existuje), který se má použít při spouštění aplikace</span><span class="sxs-lookup"><span data-stu-id="0c943-138">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="0c943-139">Spouštěcí profily jsou definované v souboru *launchSettings. JSON* a obvykle se nazývají `Development`, `Staging`a `Production`.</span><span class="sxs-lookup"><span data-stu-id="0c943-139">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="0c943-140">Další informace najdete v tématu [práce s více prostředími](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="0c943-140">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="0c943-141">Před spuštěním nevytvoří projekt.</span><span class="sxs-lookup"><span data-stu-id="0c943-141">Doesn't build the project before running.</span></span> <span data-ttu-id="0c943-142">Také implicitně nastaví `--no-restore` příznak.</span><span class="sxs-lookup"><span data-stu-id="0c943-142">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="0c943-143">Při obnovení projektu s odkazy z projektu na projekt (P2P) obnoví kořenový projekt a nikoli odkazy.</span><span class="sxs-lookup"><span data-stu-id="0c943-143">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="0c943-144">Nepokusí se nakonfigurovat aplikaci pomocí *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="0c943-144">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="0c943-145">Při spuštění příkazu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="0c943-145">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="0c943-146">Určuje cestu k souboru projektu, který se má spustit (název složky nebo úplná cesta).</span><span class="sxs-lookup"><span data-stu-id="0c943-146">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="0c943-147">Pokud není zadaný, použije se ve výchozím nastavení aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="0c943-147">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="0c943-148">Určuje cílový modul runtime pro obnovení balíčků pro.</span><span class="sxs-lookup"><span data-stu-id="0c943-148">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="0c943-149">Seznam identifikátorů modulu runtime (identifikátorů RID) najdete v [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="0c943-149">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="0c943-150">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="0c943-150">Sets the verbosity level of the command.</span></span> <span data-ttu-id="0c943-151">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]` `d[etailed]`, a .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="0c943-151">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="0c943-152">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="0c943-152">.NET Core 2.0</span></span>](#tab/netcore20)

`--`

<span data-ttu-id="0c943-153">Odděluje argumenty `dotnet run` z argumentů pro spouštěnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0c943-153">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="0c943-154">Všechny argumenty po tomto oddělovači jsou předány spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="0c943-154">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="0c943-155">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="0c943-155">Defines the build configuration.</span></span> <span data-ttu-id="0c943-156">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="0c943-156">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="0c943-157">Vytvoří a spustí aplikaci pomocí zadaného [rozhraní](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="0c943-157">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="0c943-158">Rozhraní musí být určeno v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="0c943-158">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="0c943-159">Vynutí vyřešení všech závislostí i v případě, že bylo poslední obnovení úspěšné.</span><span class="sxs-lookup"><span data-stu-id="0c943-159">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="0c943-160">Zadání tohoto příznaku je stejné jako odstranění souboru *Project. assets. JSON* .</span><span class="sxs-lookup"><span data-stu-id="0c943-160">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="0c943-161">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="0c943-161">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="0c943-162">Název spouštěcího profilu (pokud existuje), který se má použít při spouštění aplikace</span><span class="sxs-lookup"><span data-stu-id="0c943-162">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="0c943-163">Spouštěcí profily jsou definované v souboru *launchSettings. JSON* a obvykle se nazývají `Development`, `Staging`a `Production`.</span><span class="sxs-lookup"><span data-stu-id="0c943-163">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="0c943-164">Další informace najdete v tématu [práce s více prostředími](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="0c943-164">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="0c943-165">Před spuštěním nevytvoří projekt.</span><span class="sxs-lookup"><span data-stu-id="0c943-165">Doesn't build the project before running.</span></span> <span data-ttu-id="0c943-166">Také implicitně nastaví `--no-restore` příznak.</span><span class="sxs-lookup"><span data-stu-id="0c943-166">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="0c943-167">Při obnovení projektu s odkazy z projektu na projekt (P2P) obnoví kořenový projekt a nikoli odkazy.</span><span class="sxs-lookup"><span data-stu-id="0c943-167">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="0c943-168">Nepokusí se nakonfigurovat aplikaci pomocí *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="0c943-168">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="0c943-169">Při spuštění příkazu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="0c943-169">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="0c943-170">Určuje cestu k souboru projektu, který se má spustit (název složky nebo úplná cesta).</span><span class="sxs-lookup"><span data-stu-id="0c943-170">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="0c943-171">Pokud není zadaný, použije se ve výchozím nastavení aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="0c943-171">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="0c943-172">Určuje cílový modul runtime pro obnovení balíčků pro.</span><span class="sxs-lookup"><span data-stu-id="0c943-172">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="0c943-173">Seznam identifikátorů modulu runtime (identifikátorů RID) najdete v [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="0c943-173">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0c943-174">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="0c943-174">.NET Core 1.x</span></span>](#tab/netcore1x)

`--`

<span data-ttu-id="0c943-175">Odděluje argumenty `dotnet run` z argumentů pro spouštěnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0c943-175">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="0c943-176">Všechny argumenty po tomto oddělovači jsou předány spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="0c943-176">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="0c943-177">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="0c943-177">Defines the build configuration.</span></span> <span data-ttu-id="0c943-178">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="0c943-178">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="0c943-179">Vytvoří a spustí aplikaci pomocí zadaného [rozhraní](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="0c943-179">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="0c943-180">Rozhraní musí být určeno v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="0c943-180">The framework must be specified in the project file.</span></span>

`-h|--help`

<span data-ttu-id="0c943-181">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="0c943-181">Prints out a short help for the command.</span></span>

`-p|--project <PATH/PROJECT.csproj>`

<span data-ttu-id="0c943-182">Určuje cestu a název souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="0c943-182">Specifies the path and name of the project file.</span></span> <span data-ttu-id="0c943-183">(Podívejte se na poznámku.) Pokud není zadaný, použije se ve výchozím nastavení aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="0c943-183">(See the NOTE.) If not specified, it defaults to the current directory.</span></span>

> [!NOTE]
> <span data-ttu-id="0c943-184">Použijte cestu a název souboru projektu s `-p|--project` možností.</span><span class="sxs-lookup"><span data-stu-id="0c943-184">Use the path and name of the project file with the `-p|--project` option.</span></span> <span data-ttu-id="0c943-185">Regrese v rozhraní příkazového řádku zabraňuje tomu, aby poskytovala cestu ke složce .NET Core SDK 1. x.</span><span class="sxs-lookup"><span data-stu-id="0c943-185">A regression in the CLI prevents providing a folder path with .NET Core SDK 1.x.</span></span> <span data-ttu-id="0c943-186">Další informace o tomto problému naleznete v tématu [dotnet Run-p. nelze spustit projekt (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).</span><span class="sxs-lookup"><span data-stu-id="0c943-186">For more information about this issue, see [dotnet run -p, can not start a project (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).</span></span>

---

## <a name="examples"></a><span data-ttu-id="0c943-187">Příklady</span><span class="sxs-lookup"><span data-stu-id="0c943-187">Examples</span></span>

<span data-ttu-id="0c943-188">Spustit projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="0c943-188">Run the project in the current directory:</span></span>

`dotnet run`

<span data-ttu-id="0c943-189">Spustit zadaný projekt:</span><span class="sxs-lookup"><span data-stu-id="0c943-189">Run the specified project:</span></span>

`dotnet run --project ./projects/proj1/proj1.csproj`

<span data-ttu-id="0c943-190">Spustí projekt v aktuálním adresáři ( `--help` argument v tomto příkladu je předán do aplikace, protože je použita prázdná `--` možnost):</span><span class="sxs-lookup"><span data-stu-id="0c943-190">Run the project in the current directory (the `--help` argument in this example is passed to the application, since the blank `--` option is used):</span></span>

`dotnet run --configuration Release -- --help`

<span data-ttu-id="0c943-191">Obnovte závislosti a nástroje pro projekt v aktuálním adresáři pouze s minimálním výstupem a potom spusťte projekt: (.NET Core SDK 2,0 a novější verze):</span><span class="sxs-lookup"><span data-stu-id="0c943-191">Restore dependencies and tools for the project in the current directory only showing minimal output and then run the project: (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet run --verbosity m`
