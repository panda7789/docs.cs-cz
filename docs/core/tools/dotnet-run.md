---
title: příkaz dotnet run
description: Příkaz dotnet Run poskytuje pohodlný způsob, jak spustit aplikaci ze zdrojového kódu.
ms.date: 02/19/2020
ms.openlocfilehash: 415d7079db6a3da80c4fcf2074307ea760e84982
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503605"
---
# <a name="dotnet-run"></a><span data-ttu-id="f912c-103">dotnet run</span><span class="sxs-lookup"><span data-stu-id="f912c-103">dotnet run</span></span>

<span data-ttu-id="f912c-104">**Tento článek se týká:** ✔️ .NET Core 2. x SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="f912c-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="f912c-105">Název</span><span class="sxs-lookup"><span data-stu-id="f912c-105">Name</span></span>

<span data-ttu-id="f912c-106">`dotnet run` – spustí zdrojový kód bez explicitních příkazů Compile nebo Launch.</span><span class="sxs-lookup"><span data-stu-id="f912c-106">`dotnet run` - Runs source code without any explicit compile or launch commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f912c-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="f912c-107">Synopsis</span></span>

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--interactive] [--launch-profile] 
    [--no-build] [--no-dependencies] [--no-launch-profile] [--no-restore] [-p|--project] 
    [-r|--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

## <a name="description"></a><span data-ttu-id="f912c-108">Popis</span><span class="sxs-lookup"><span data-stu-id="f912c-108">Description</span></span>

<span data-ttu-id="f912c-109">Příkaz `dotnet run` poskytuje pohodlný způsob, jak spustit aplikaci ze zdrojového kódu pomocí jednoho příkazu.</span><span class="sxs-lookup"><span data-stu-id="f912c-109">The `dotnet run` command provides a convenient option to run your application from the source code with one command.</span></span> <span data-ttu-id="f912c-110">Je vhodný pro rychlý iterativní vývoj z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="f912c-110">It's useful for fast iterative development from the command line.</span></span> <span data-ttu-id="f912c-111">Příkaz závisí na příkazu [`dotnet build`](dotnet-build.md) pro sestavení kódu.</span><span class="sxs-lookup"><span data-stu-id="f912c-111">The command depends on the [`dotnet build`](dotnet-build.md) command to build the code.</span></span> <span data-ttu-id="f912c-112">Všechny požadavky na sestavení, například, že je nutné nejprve obnovit projekt, platí pro `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="f912c-112">Any requirements for the build, such as that the project must be restored first, apply to `dotnet run` as well.</span></span>

<span data-ttu-id="f912c-113">Výstupní soubory jsou zapsány do výchozího umístění, které je `bin/<configuration>/<target>`.</span><span class="sxs-lookup"><span data-stu-id="f912c-113">Output files are written into the default location, which is `bin/<configuration>/<target>`.</span></span> <span data-ttu-id="f912c-114">Pokud máte například aplikaci `netcoreapp2.1` a spustíte `dotnet run`, výstup je umístěný v `bin/Debug/netcoreapp2.1`.</span><span class="sxs-lookup"><span data-stu-id="f912c-114">For example if you have a `netcoreapp2.1` application and you run `dotnet run`, the output is placed in `bin/Debug/netcoreapp2.1`.</span></span> <span data-ttu-id="f912c-115">Soubory jsou v případě potřeby přepsány.</span><span class="sxs-lookup"><span data-stu-id="f912c-115">Files are overwritten as needed.</span></span> <span data-ttu-id="f912c-116">Dočasné soubory jsou umístěny v adresáři `obj`.</span><span class="sxs-lookup"><span data-stu-id="f912c-116">Temporary files are placed in the `obj` directory.</span></span>

<span data-ttu-id="f912c-117">Pokud projekt určuje více rozhraní, spuštění `dotnet run` způsobí chybu, pokud není použita možnost `-f|--framework <FRAMEWORK>` k určení architektury.</span><span class="sxs-lookup"><span data-stu-id="f912c-117">If the project specifies multiple frameworks, executing `dotnet run` results in an error unless the `-f|--framework <FRAMEWORK>` option is used to specify the framework.</span></span>

<span data-ttu-id="f912c-118">Příkaz `dotnet run` se používá v kontextu projektů, nikoli ve vytvořených sestaveních.</span><span class="sxs-lookup"><span data-stu-id="f912c-118">The `dotnet run` command is used in the context of projects, not built assemblies.</span></span> <span data-ttu-id="f912c-119">Pokud se pokoušíte spustit knihovnu DLL aplikace závislou na rozhraní, je nutné použít příkaz [dotnet](dotnet.md) bez příkazu.</span><span class="sxs-lookup"><span data-stu-id="f912c-119">If you're trying to run a framework-dependent application DLL instead, you must use [dotnet](dotnet.md) without a command.</span></span> <span data-ttu-id="f912c-120">Pokud například chcete spustit `myapp.dll`, použijte:</span><span class="sxs-lookup"><span data-stu-id="f912c-120">For example, to run `myapp.dll`, use:</span></span>

```dotnetcli
dotnet myapp.dll
```

<span data-ttu-id="f912c-121">Další informace o ovladači `dotnet` naleznete v tématu [.NET Core Command line Tools (CLI)](index.md) .</span><span class="sxs-lookup"><span data-stu-id="f912c-121">For more information on the `dotnet` driver, see the [.NET Core Command Line Tools (CLI)](index.md) topic.</span></span>

<span data-ttu-id="f912c-122">Chcete-li spustit aplikaci, příkaz `dotnet run` vyřeší závislosti aplikace, které jsou mimo sdílený modul runtime z mezipaměti NuGet.</span><span class="sxs-lookup"><span data-stu-id="f912c-122">To run the application, the `dotnet run` command resolves the dependencies of the application that are outside of the shared runtime from the NuGet cache.</span></span> <span data-ttu-id="f912c-123">Protože používá závislosti v mezipaměti, nedoporučuje se používat `dotnet run` ke spouštění aplikací v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="f912c-123">Because it uses cached dependencies, it's not recommended to use `dotnet run` to run applications in production.</span></span> <span data-ttu-id="f912c-124">Místo toho [vytvořte nasazení](../deploying/index.md) pomocí příkazu [`dotnet publish`](dotnet-publish.md) a nasaďte publikovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="f912c-124">Instead, [create a deployment](../deploying/index.md) using the [`dotnet publish`](dotnet-publish.md) command and deploy the published output.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a><span data-ttu-id="f912c-125">Možnosti</span><span class="sxs-lookup"><span data-stu-id="f912c-125">Options</span></span>

- **`--`**

  <span data-ttu-id="f912c-126">Odděluje argumenty pro `dotnet run` z argumentů pro spouštěnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f912c-126">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="f912c-127">Všechny argumenty po tomto oddělovači jsou předány spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="f912c-127">All arguments after this delimiter are passed to the application run.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="f912c-128">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="f912c-128">Defines the build configuration.</span></span> <span data-ttu-id="f912c-129">Výchozí hodnota pro většinu projektů je `Debug`, ale můžete přepsat nastavení konfigurace sestavení v projektu.</span><span class="sxs-lookup"><span data-stu-id="f912c-129">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f912c-130">Vytvoří a spustí aplikaci pomocí zadaného [rozhraní](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="f912c-130">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="f912c-131">Rozhraní musí být určeno v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="f912c-131">The framework must be specified in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="f912c-132">Vynutí vyřešení všech závislostí i v případě, že bylo poslední obnovení úspěšné.</span><span class="sxs-lookup"><span data-stu-id="f912c-132">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="f912c-133">Zadání tohoto příznaku je stejné jako odstranění souboru *Project. assets. JSON* .</span><span class="sxs-lookup"><span data-stu-id="f912c-133">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="f912c-134">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="f912c-134">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="f912c-135">Umožňuje příkazu zastavit a počkat na vstup nebo akci uživatele (například k dokončení ověřování).</span><span class="sxs-lookup"><span data-stu-id="f912c-135">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="f912c-136">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="f912c-136">Available since .NET Core 3.0 SDK.</span></span>

- **`--launch-profile <NAME>`**

  <span data-ttu-id="f912c-137">Název spouštěcího profilu (pokud existuje), který se má použít při spouštění aplikace</span><span class="sxs-lookup"><span data-stu-id="f912c-137">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="f912c-138">Spouštěcí profily jsou definované v souboru *launchSettings. JSON* a obvykle se nazývají `Development`, `Staging`a `Production`.</span><span class="sxs-lookup"><span data-stu-id="f912c-138">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="f912c-139">Další informace najdete v tématu [práce s více prostředími](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="f912c-139">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

- **`--no-build`**

  <span data-ttu-id="f912c-140">Před spuštěním nevytvoří projekt.</span><span class="sxs-lookup"><span data-stu-id="f912c-140">Doesn't build the project before running.</span></span> <span data-ttu-id="f912c-141">Také implicitně nastaví příznak `--no-restore`.</span><span class="sxs-lookup"><span data-stu-id="f912c-141">It also implicit sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="f912c-142">Při obnovení projektu s odkazy z projektu na projekt (P2P) obnoví kořenový projekt a nikoli odkazy.</span><span class="sxs-lookup"><span data-stu-id="f912c-142">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

- **`--no-launch-profile`**

  <span data-ttu-id="f912c-143">Nepokusí se nakonfigurovat aplikaci pomocí *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="f912c-143">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

- **`--no-restore`**

  <span data-ttu-id="f912c-144">Při spuštění příkazu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="f912c-144">Doesn't execute an implicit restore when running the command.</span></span>

- **`-p|--project <PATH>`**

  <span data-ttu-id="f912c-145">Určuje cestu k souboru projektu, který se má spustit (název složky nebo úplná cesta).</span><span class="sxs-lookup"><span data-stu-id="f912c-145">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="f912c-146">Pokud není zadaný, použije se ve výchozím nastavení aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="f912c-146">If not specified, it defaults to the current directory.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="f912c-147">Určuje cílový modul runtime pro obnovení balíčků pro.</span><span class="sxs-lookup"><span data-stu-id="f912c-147">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="f912c-148">Seznam identifikátorů modulu runtime (identifikátorů RID) najdete v [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="f912c-148">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="f912c-149">pro sadu .NET Core 3,0 SDK je `-r` k dispozici krátká možnost.</span><span class="sxs-lookup"><span data-stu-id="f912c-149">`-r` short option available since .NET Core 3.0 SDK.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="f912c-150">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="f912c-150">Sets the verbosity level of the command.</span></span> <span data-ttu-id="f912c-151">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="f912c-151">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="f912c-152">Výchozí hodnota je `m`.</span><span class="sxs-lookup"><span data-stu-id="f912c-152">The default value is `m`.</span></span> <span data-ttu-id="f912c-153">K dispozici od verze .NET Core 2,1 SDK.</span><span class="sxs-lookup"><span data-stu-id="f912c-153">Available since .NET Core 2.1 SDK.</span></span> 

## <a name="examples"></a><span data-ttu-id="f912c-154">Příklady</span><span class="sxs-lookup"><span data-stu-id="f912c-154">Examples</span></span>

- <span data-ttu-id="f912c-155">Spustit projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="f912c-155">Run the project in the current directory:</span></span>

  ```dotnetcli
  dotnet run
  ```

- <span data-ttu-id="f912c-156">Spustit zadaný projekt:</span><span class="sxs-lookup"><span data-stu-id="f912c-156">Run the specified project:</span></span>

  ```dotnetcli
  dotnet run --project ./projects/proj1/proj1.csproj
  ```

- <span data-ttu-id="f912c-157">Spustí projekt v aktuálním adresáři (`--help` argument v tomto příkladu je předán do aplikace, protože je použita možnost prázdné `--`):</span><span class="sxs-lookup"><span data-stu-id="f912c-157">Run the project in the current directory (the `--help` argument in this example is passed to the application, since the blank `--` option is used):</span></span>

  ```dotnetcli
  dotnet run --configuration Release -- --help
  ```

- <span data-ttu-id="f912c-158">Obnovte závislosti a nástroje pro projekt v aktuálním adresáři pouze s minimálním výstupem a potom spusťte projekt: (.NET Core SDK 2,0 a novější verze):</span><span class="sxs-lookup"><span data-stu-id="f912c-158">Restore dependencies and tools for the project in the current directory only showing minimal output and then run the project: (.NET Core SDK 2.0 and later versions):</span></span>

  ```dotnetcli
  dotnet run --verbosity m
  ```
