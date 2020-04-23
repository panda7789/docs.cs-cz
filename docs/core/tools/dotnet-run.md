---
title: dotnet spustit, příkaz
description: Příkaz dotnet run poskytuje vhodnou možnost spuštění aplikace ze zdrojového kódu.
ms.date: 02/19/2020
ms.openlocfilehash: 77282fd8615ef01b7867c1bf0f741c834b6ddb30
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102762"
---
# <a name="dotnet-run"></a><span data-ttu-id="ee65f-103">dotnet run</span><span class="sxs-lookup"><span data-stu-id="ee65f-103">dotnet run</span></span>

<span data-ttu-id="ee65f-104">**Tento článek se týká:** ✔️ .NET Core 2.x SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="ee65f-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="ee65f-105">Název</span><span class="sxs-lookup"><span data-stu-id="ee65f-105">Name</span></span>

<span data-ttu-id="ee65f-106">`dotnet run`- Spustí zdrojový kód bez explicitních příkazů kompilace nebo spuštění.</span><span class="sxs-lookup"><span data-stu-id="ee65f-106">`dotnet run` - Runs source code without any explicit compile or launch commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ee65f-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="ee65f-107">Synopsis</span></span>

```dotnetcli
dotnet run [-c|--configuration <CONFIGURATION>] [-f|--framework <FRAMEWORK>]
    [--force] [--interactive] [--launch-profile <NAME>] [--no-build]
    [--no-dependencies] [--no-launch-profile] [--no-restore]
    [-p|--project <PATH>] [-r|--runtime <RUNTIME_IDENTIFIER>]
    [-v|--verbosity <LEVEL>] [[--] [application arguments]]

dotnet run -h|--help
```

## <a name="description"></a><span data-ttu-id="ee65f-108">Popis</span><span class="sxs-lookup"><span data-stu-id="ee65f-108">Description</span></span>

<span data-ttu-id="ee65f-109">Příkaz `dotnet run` poskytuje vhodnou možnost spuštění aplikace ze zdrojového kódu pomocí jednoho příkazu.</span><span class="sxs-lookup"><span data-stu-id="ee65f-109">The `dotnet run` command provides a convenient option to run your application from the source code with one command.</span></span> <span data-ttu-id="ee65f-110">Je to užitečné pro rychlý iterativní vývoj z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="ee65f-110">It's useful for fast iterative development from the command line.</span></span> <span data-ttu-id="ee65f-111">Příkaz závisí na [`dotnet build`](dotnet-build.md) příkaz u vytvoření kódu.</span><span class="sxs-lookup"><span data-stu-id="ee65f-111">The command depends on the [`dotnet build`](dotnet-build.md) command to build the code.</span></span> <span data-ttu-id="ee65f-112">Všechny požadavky na sestavení, například že projekt musí být `dotnet run` obnovena jako první, platí také.</span><span class="sxs-lookup"><span data-stu-id="ee65f-112">Any requirements for the build, such as that the project must be restored first, apply to `dotnet run` as well.</span></span>

<span data-ttu-id="ee65f-113">Výstupní soubory jsou zapsány do `bin/<configuration>/<target>`výchozího umístění, což je .</span><span class="sxs-lookup"><span data-stu-id="ee65f-113">Output files are written into the default location, which is `bin/<configuration>/<target>`.</span></span> <span data-ttu-id="ee65f-114">Například pokud máte `netcoreapp2.1` aplikaci `dotnet run`a spustit , `bin/Debug/netcoreapp2.1`výstup je umístěn v .</span><span class="sxs-lookup"><span data-stu-id="ee65f-114">For example if you have a `netcoreapp2.1` application and you run `dotnet run`, the output is placed in `bin/Debug/netcoreapp2.1`.</span></span> <span data-ttu-id="ee65f-115">Soubory jsou přepsány podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="ee65f-115">Files are overwritten as needed.</span></span> <span data-ttu-id="ee65f-116">Dočasné soubory jsou `obj` umístěny v adresáři.</span><span class="sxs-lookup"><span data-stu-id="ee65f-116">Temporary files are placed in the `obj` directory.</span></span>

<span data-ttu-id="ee65f-117">Pokud projekt určuje více rozhraní, `dotnet run` provádění výsledků v `-f|--framework <FRAMEWORK>` chybě, pokud je použita možnost k určení rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ee65f-117">If the project specifies multiple frameworks, executing `dotnet run` results in an error unless the `-f|--framework <FRAMEWORK>` option is used to specify the framework.</span></span>

<span data-ttu-id="ee65f-118">Příkaz `dotnet run` se používá v kontextu projektů, nikoli sestavení.</span><span class="sxs-lookup"><span data-stu-id="ee65f-118">The `dotnet run` command is used in the context of projects, not built assemblies.</span></span> <span data-ttu-id="ee65f-119">Pokud se místo toho pokoušíte spustit dll aplikace závislé na rozhraní, musíte použít [dotnet](dotnet.md) bez příkazu.</span><span class="sxs-lookup"><span data-stu-id="ee65f-119">If you're trying to run a framework-dependent application DLL instead, you must use [dotnet](dotnet.md) without a command.</span></span> <span data-ttu-id="ee65f-120">Chcete-li například spustit `myapp.dll`, použijte:</span><span class="sxs-lookup"><span data-stu-id="ee65f-120">For example, to run `myapp.dll`, use:</span></span>

```dotnetcli
dotnet myapp.dll
```

<span data-ttu-id="ee65f-121">Další informace o `dotnet` ovladači naleznete v tématu [nástroje CLI (.NET Core Command Line Tools).](index.md)</span><span class="sxs-lookup"><span data-stu-id="ee65f-121">For more information on the `dotnet` driver, see the [.NET Core Command Line Tools (CLI)](index.md) topic.</span></span>

<span data-ttu-id="ee65f-122">Chcete-li spustit `dotnet run` aplikaci, příkaz řeší závislosti aplikace, které jsou mimo sdílené hodu runtime z mezipaměti NuGet.</span><span class="sxs-lookup"><span data-stu-id="ee65f-122">To run the application, the `dotnet run` command resolves the dependencies of the application that are outside of the shared runtime from the NuGet cache.</span></span> <span data-ttu-id="ee65f-123">Vzhledem k tomu, že používá závislosti uložené `dotnet run` v mezipaměti, nedoporučuje se používat ke spouštění aplikací v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="ee65f-123">Because it uses cached dependencies, it's not recommended to use `dotnet run` to run applications in production.</span></span> <span data-ttu-id="ee65f-124">Místo toho [vytvořte](../deploying/index.md) [`dotnet publish`](dotnet-publish.md) nasazení pomocí příkazu a nasadit publikovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="ee65f-124">Instead, [create a deployment](../deploying/index.md) using the [`dotnet publish`](dotnet-publish.md) command and deploy the published output.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="ee65f-125">Implicitní obnovení</span><span class="sxs-lookup"><span data-stu-id="ee65f-125">Implicit restore</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a><span data-ttu-id="ee65f-126">Možnosti</span><span class="sxs-lookup"><span data-stu-id="ee65f-126">Options</span></span>

- **`--`**

  <span data-ttu-id="ee65f-127">Vymezuje `dotnet run` argumenty z argumentů pro spuštěnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ee65f-127">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="ee65f-128">Všechny argumenty po tomto oddělovači jsou předány spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="ee65f-128">All arguments after this delimiter are passed to the application run.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="ee65f-129">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="ee65f-129">Defines the build configuration.</span></span> <span data-ttu-id="ee65f-130">Výchozí hodnota pro `Debug`většinu projektů je , ale můžete přepsat nastavení konfigurace sestavení v projektu.</span><span class="sxs-lookup"><span data-stu-id="ee65f-130">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ee65f-131">Vytvoří a spustí aplikaci pomocí zadaného [rozhraní](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="ee65f-131">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="ee65f-132">Rámec musí být zadán v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="ee65f-132">The framework must be specified in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="ee65f-133">Vynutí vyřešení všech závislostí, i když bylo poslední obnovení úspěšné.</span><span class="sxs-lookup"><span data-stu-id="ee65f-133">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="ee65f-134">Zadání tohoto příznaku je stejné jako odstranění souboru *project.assets.json.*</span><span class="sxs-lookup"><span data-stu-id="ee65f-134">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="ee65f-135">Vytiskne krátkou nápovědu pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="ee65f-135">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="ee65f-136">Umožňuje příkazu zastavit a čekat na vstup nebo akci uživatele (například k dokončení ověřování).</span><span class="sxs-lookup"><span data-stu-id="ee65f-136">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="ee65f-137">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ee65f-137">Available since .NET Core 3.0 SDK.</span></span>

- **`--launch-profile <NAME>`**

  <span data-ttu-id="ee65f-138">Název profilu spuštění (pokud existuje) použít při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="ee65f-138">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="ee65f-139">Profily spuštění jsou definovány v souboru *launchSettings.json* a obvykle se nazývají `Development`, `Staging`, a `Production`.</span><span class="sxs-lookup"><span data-stu-id="ee65f-139">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="ee65f-140">Další informace naleznete v [tématu Práce s více prostředími](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="ee65f-140">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

- **`--no-build`**

  <span data-ttu-id="ee65f-141">Nesestavuje projekt před spuštěním.</span><span class="sxs-lookup"><span data-stu-id="ee65f-141">Doesn't build the project before running.</span></span> <span data-ttu-id="ee65f-142">Také implicitní `--no-restore` nastaví příznak.</span><span class="sxs-lookup"><span data-stu-id="ee65f-142">It also implicit sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="ee65f-143">Při obnovení projektu s odkazy projekt-projekt (P2P) obnoví kořenový projekt a nikoli odkazy.</span><span class="sxs-lookup"><span data-stu-id="ee65f-143">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

- **`--no-launch-profile`**

  <span data-ttu-id="ee65f-144">Nepokouší se použít *launchSettings.json* ke konfiguraci aplikace.</span><span class="sxs-lookup"><span data-stu-id="ee65f-144">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

- **`--no-restore`**

  <span data-ttu-id="ee65f-145">Nespustí implicitní obnovení při spuštění příkazu.</span><span class="sxs-lookup"><span data-stu-id="ee65f-145">Doesn't execute an implicit restore when running the command.</span></span>

- **`-p|--project <PATH>`**

  <span data-ttu-id="ee65f-146">Určuje cestu ke spuštění souboru projektu (název složky nebo úplná cesta).</span><span class="sxs-lookup"><span data-stu-id="ee65f-146">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="ee65f-147">Pokud není zadán, je výchozí aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="ee65f-147">If not specified, it defaults to the current directory.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="ee65f-148">Určuje cílový čas běhu, pro který má být obnoveny balíčky.</span><span class="sxs-lookup"><span data-stu-id="ee65f-148">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="ee65f-149">Seznam identifikátorů modulu Runtime (RID) naleznete v [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="ee65f-149">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="ee65f-150">`-r`krátká možnost k dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ee65f-150">`-r` short option available since .NET Core 3.0 SDK.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="ee65f-151">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="ee65f-151">Sets the verbosity level of the command.</span></span> <span data-ttu-id="ee65f-152">Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a .</span><span class="sxs-lookup"><span data-stu-id="ee65f-152">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="ee65f-153">Výchozí hodnota je `m`.</span><span class="sxs-lookup"><span data-stu-id="ee65f-153">The default value is `m`.</span></span> <span data-ttu-id="ee65f-154">K dispozici od .NET Core 2.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="ee65f-154">Available since .NET Core 2.1 SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="ee65f-155">Příklady</span><span class="sxs-lookup"><span data-stu-id="ee65f-155">Examples</span></span>

- <span data-ttu-id="ee65f-156">Spusťte projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="ee65f-156">Run the project in the current directory:</span></span>

  ```dotnetcli
  dotnet run
  ```

- <span data-ttu-id="ee65f-157">Spusťte zadaný projekt:</span><span class="sxs-lookup"><span data-stu-id="ee65f-157">Run the specified project:</span></span>

  ```dotnetcli
  dotnet run --project ./projects/proj1/proj1.csproj
  ```

- <span data-ttu-id="ee65f-158">Spusťte projekt v aktuálním adresáři (argument v tomto příkladu `--help` je předán aplikaci, protože se používá prázdná `--` možnost):</span><span class="sxs-lookup"><span data-stu-id="ee65f-158">Run the project in the current directory (the `--help` argument in this example is passed to the application, since the blank `--` option is used):</span></span>

  ```dotnetcli
  dotnet run --configuration Release -- --help
  ```

- <span data-ttu-id="ee65f-159">Obnovení závislostí a nástrojů pro projekt v aktuálním adresáři zobrazující pouze minimální výstup a potom spustit projekt: (.NET Core SDK 2.0 a novější verze):</span><span class="sxs-lookup"><span data-stu-id="ee65f-159">Restore dependencies and tools for the project in the current directory only showing minimal output and then run the project: (.NET Core SDK 2.0 and later versions):</span></span>

  ```dotnetcli
  dotnet run --verbosity m
  ```
