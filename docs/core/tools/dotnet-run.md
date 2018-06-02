---
title: 'DotNet. Spusťte příkaz: .NET Core rozhraní příkazového řádku'
description: Dotnet, spusťte příkaz poskytuje vhodnou možnost pro spuštění aplikace ze zdrojového kódu.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 82c6e44e52aa6af7044edf72fd6e57b7614a70f3
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696309"
---
# <a name="dotnet-run"></a><span data-ttu-id="18673-103">Spustit DotNet.</span><span class="sxs-lookup"><span data-stu-id="18673-103">dotnet run</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="18673-104">Název</span><span class="sxs-lookup"><span data-stu-id="18673-104">Name</span></span>

<span data-ttu-id="18673-105">`dotnet run` -Běží zdrojový kód bez jakýchkoli explicitní kompilace nebo spusťte příkazy.</span><span class="sxs-lookup"><span data-stu-id="18673-105">`dotnet run` - Runs source code without any explicit compile or launch commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="18673-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="18673-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="18673-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="18673-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="18673-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="18673-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [[--] [application arguments]]
dotnet run [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="18673-109">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="18673-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]]
dotnet run [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="18673-110">Popis</span><span class="sxs-lookup"><span data-stu-id="18673-110">Description</span></span>

<span data-ttu-id="18673-111">`dotnet run` Příkaz poskytuje vhodnou možnost pro spuštění aplikace ze zdrojového kódu se jeden příkaz.</span><span class="sxs-lookup"><span data-stu-id="18673-111">The `dotnet run` command provides a convenient option to run your application from the source code with one command.</span></span> <span data-ttu-id="18673-112">Je vhodné pro rychlé iterativní vývoj z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="18673-112">It's useful for fast iterative development from the command line.</span></span> <span data-ttu-id="18673-113">Příkaz závisí na [ `dotnet build` ](dotnet-build.md) k vytvoření kód.</span><span class="sxs-lookup"><span data-stu-id="18673-113">The command depends on the [`dotnet build`](dotnet-build.md) command to build the code.</span></span> <span data-ttu-id="18673-114">Všechny požadavky pro sestavení, jako je například, je nutné obnovit projekt nejprve použít `dotnet run` také.</span><span class="sxs-lookup"><span data-stu-id="18673-114">Any requirements for the build, such as that the project must be restored first, apply to `dotnet run` as well.</span></span>

<span data-ttu-id="18673-115">Výstupní soubory se zapisují do výchozího umístění, což je `bin/<configuration>/<target>`.</span><span class="sxs-lookup"><span data-stu-id="18673-115">Output files are written into the default location, which is `bin/<configuration>/<target>`.</span></span> <span data-ttu-id="18673-116">Například pokud máte `netcoreapp1.0` aplikace a můžete spustit `dotnet run`, se umístí výstup v `bin/Debug/netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="18673-116">For example if you have a `netcoreapp1.0` application and you run `dotnet run`, the output is placed in `bin/Debug/netcoreapp1.0`.</span></span> <span data-ttu-id="18673-117">Soubory jsou přepsány podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="18673-117">Files are overwritten as needed.</span></span> <span data-ttu-id="18673-118">Dočasné soubory jsou umístěny v `obj` adresáře.</span><span class="sxs-lookup"><span data-stu-id="18673-118">Temporary files are placed in the `obj` directory.</span></span>

<span data-ttu-id="18673-119">Pokud projekt určuje více rozhraní, provádění `dotnet run` vede k chybě, pokud `-f|--framework <FRAMEWORK>` možnost slouží k určení rozhraní.</span><span class="sxs-lookup"><span data-stu-id="18673-119">If the project specifies multiple frameworks, executing `dotnet run` results in an error unless the `-f|--framework <FRAMEWORK>` option is used to specify the framework.</span></span>

<span data-ttu-id="18673-120">`dotnet run` Příkaz se používá v souvislosti s projekty, Nevytvořen sestavení.</span><span class="sxs-lookup"><span data-stu-id="18673-120">The `dotnet run` command is used in the context of projects, not built assemblies.</span></span> <span data-ttu-id="18673-121">Pokud se pokoušíte spustit framework závislé aplikace DLL místo, musíte použít [dotnet](dotnet.md) bez příkaz.</span><span class="sxs-lookup"><span data-stu-id="18673-121">If you're trying to run a framework-dependent application DLL instead, you must use [dotnet](dotnet.md) without a command.</span></span> <span data-ttu-id="18673-122">Chcete-li například spustit `myapp.dll`, použijte:</span><span class="sxs-lookup"><span data-stu-id="18673-122">For example, to run `myapp.dll`, use:</span></span>

```console
dotnet myapp.dll
```

<span data-ttu-id="18673-123">Další informace o `dotnet` ovladač, najdete v článku [.NET Core příkazového řádku nástroje (CLI)](index.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="18673-123">For more information on the `dotnet` driver, see the [.NET Core Command Line Tools (CLI)](index.md) topic.</span></span>

<span data-ttu-id="18673-124">Ke spuštění aplikace, `dotnet run` příkaz vyřeší závislosti aplikace, které jsou mimo sdílený modul runtime z mezipaměti NuGet.</span><span class="sxs-lookup"><span data-stu-id="18673-124">To run the application, the `dotnet run` command resolves the dependencies of the application that are outside of the shared runtime from the NuGet cache.</span></span> <span data-ttu-id="18673-125">Protože se používá v mezipaměti závislosti, nedoporučujeme používat `dotnet run` ke spouštění aplikací v provozním prostředí.</span><span class="sxs-lookup"><span data-stu-id="18673-125">Because it uses cached dependencies, it's not recommended to use `dotnet run` to run applications in production.</span></span> <span data-ttu-id="18673-126">Místo toho [vytvořit nasazení](../deploying/index.md) pomocí [ `dotnet publish` ](dotnet-publish.md) příkazů a nasadit publikované výstup.</span><span class="sxs-lookup"><span data-stu-id="18673-126">Instead, [create a deployment](../deploying/index.md) using the [`dotnet publish`](dotnet-publish.md) command and deploy the published output.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a><span data-ttu-id="18673-127">Možnosti</span><span class="sxs-lookup"><span data-stu-id="18673-127">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="18673-128">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="18673-128">.NET Core 2.1</span></span>](#tab/netcore21)

`--`

<span data-ttu-id="18673-129">Vymezuje argumenty, které mají `dotnet run` z argumentů pro aplikace spuštěna.</span><span class="sxs-lookup"><span data-stu-id="18673-129">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="18673-130">Všechny argumenty po této oddělovač jsou předány aplikace spuštěná.</span><span class="sxs-lookup"><span data-stu-id="18673-130">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="18673-131">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="18673-131">Defines the build configuration.</span></span> <span data-ttu-id="18673-132">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="18673-132">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="18673-133">Vytvoří a spustí aplikace pomocí zadané [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="18673-133">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="18673-134">Rozhraní musí být zadán v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="18673-134">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="18673-135">Vynutí všechny závislosti pro přeloženy i v případě, že poslední obnovení bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="18673-135">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="18673-136">Zadáním tohoto příznaku je stejný jako odstranění *project.assets.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="18673-136">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="18673-137">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="18673-137">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="18673-138">Název spuštění profilu (pokud existuje) pro použití při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="18673-138">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="18673-139">Spuštění profily jsou definovány v *launchSettings.json* souborů a jsou obvykle nazývá `Development`, `Staging`, a `Production`.</span><span class="sxs-lookup"><span data-stu-id="18673-139">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="18673-140">Další informace najdete v tématu [práce s několika prostředí](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="18673-140">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="18673-141">Není sestavení projektu dřív, než spustíte.</span><span class="sxs-lookup"><span data-stu-id="18673-141">Doesn't build the project before running.</span></span> <span data-ttu-id="18673-142">Také implicitní nastaví `--no-restore` příznak.</span><span class="sxs-lookup"><span data-stu-id="18673-142">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="18673-143">Při obnovování projektu s odkazy na projekt na projekt (P2P), obnoví kořenového projektu a není odkazuje.</span><span class="sxs-lookup"><span data-stu-id="18673-143">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="18673-144">Nebude pokoušet použít *launchSettings.json* konfigurace aplikace.</span><span class="sxs-lookup"><span data-stu-id="18673-144">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="18673-145">Implicitní obnovení není spustit, když spustíte příkaz.</span><span class="sxs-lookup"><span data-stu-id="18673-145">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="18673-146">Určuje cestu k souboru projektu ke spuštění (úplná cesta nebo název).</span><span class="sxs-lookup"><span data-stu-id="18673-146">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="18673-147">Pokud není zadáno, výchozí hodnoty k aktuálnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="18673-147">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="18673-148">Určuje cílový modul runtime pro obnovení balíčků pro.</span><span class="sxs-lookup"><span data-stu-id="18673-148">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="18673-149">Seznam Runtime identifikátorů (RID), najdete v článku [identifikátorů RID katalogu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="18673-149">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="18673-150">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="18673-150">Sets the verbosity level of the command.</span></span> <span data-ttu-id="18673-151">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="18673-151">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="18673-152">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="18673-152">.NET Core 2.0</span></span>](#tab/netcore20)

`--`

<span data-ttu-id="18673-153">Vymezuje argumenty, které mají `dotnet run` z argumentů pro aplikace spuštěna.</span><span class="sxs-lookup"><span data-stu-id="18673-153">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="18673-154">Všechny argumenty po této oddělovač jsou předány aplikace spuštěná.</span><span class="sxs-lookup"><span data-stu-id="18673-154">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="18673-155">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="18673-155">Defines the build configuration.</span></span> <span data-ttu-id="18673-156">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="18673-156">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="18673-157">Vytvoří a spustí aplikace pomocí zadané [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="18673-157">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="18673-158">Rozhraní musí být zadán v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="18673-158">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="18673-159">Vynutí všechny závislosti pro přeloženy i v případě, že poslední obnovení bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="18673-159">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="18673-160">Zadáním tohoto příznaku je stejný jako odstranění *project.assets.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="18673-160">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="18673-161">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="18673-161">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="18673-162">Název spuštění profilu (pokud existuje) pro použití při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="18673-162">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="18673-163">Spuštění profily jsou definovány v *launchSettings.json* souborů a jsou obvykle nazývá `Development`, `Staging`, a `Production`.</span><span class="sxs-lookup"><span data-stu-id="18673-163">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="18673-164">Další informace najdete v tématu [práce s několika prostředí](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="18673-164">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="18673-165">Není sestavení projektu dřív, než spustíte.</span><span class="sxs-lookup"><span data-stu-id="18673-165">Doesn't build the project before running.</span></span> <span data-ttu-id="18673-166">Také implicitní nastaví `--no-restore` příznak.</span><span class="sxs-lookup"><span data-stu-id="18673-166">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="18673-167">Při obnovování projektu s odkazy na projekt na projekt (P2P), obnoví kořenového projektu a není odkazuje.</span><span class="sxs-lookup"><span data-stu-id="18673-167">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="18673-168">Nebude pokoušet použít *launchSettings.json* konfigurace aplikace.</span><span class="sxs-lookup"><span data-stu-id="18673-168">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="18673-169">Implicitní obnovení není spustit, když spustíte příkaz.</span><span class="sxs-lookup"><span data-stu-id="18673-169">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="18673-170">Určuje cestu k souboru projektu ke spuštění (úplná cesta nebo název).</span><span class="sxs-lookup"><span data-stu-id="18673-170">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="18673-171">Pokud není zadáno, výchozí hodnoty k aktuálnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="18673-171">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="18673-172">Určuje cílový modul runtime pro obnovení balíčků pro.</span><span class="sxs-lookup"><span data-stu-id="18673-172">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="18673-173">Seznam Runtime identifikátorů (RID), najdete v článku [identifikátorů RID katalogu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="18673-173">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="18673-174">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="18673-174">.NET Core 1.x</span></span>](#tab/netcore1x)

`--`

<span data-ttu-id="18673-175">Vymezuje argumenty, které mají `dotnet run` z argumentů pro aplikace spuštěna.</span><span class="sxs-lookup"><span data-stu-id="18673-175">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="18673-176">Všechny argumenty po této oddělovač jsou předány aplikace spuštěná.</span><span class="sxs-lookup"><span data-stu-id="18673-176">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="18673-177">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="18673-177">Defines the build configuration.</span></span> <span data-ttu-id="18673-178">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="18673-178">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="18673-179">Vytvoří a spustí aplikace pomocí zadané [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="18673-179">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="18673-180">Rozhraní musí být zadán v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="18673-180">The framework must be specified in the project file.</span></span>

`-h|--help`

<span data-ttu-id="18673-181">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="18673-181">Prints out a short help for the command.</span></span>

`-p|--project <PATH/PROJECT.csproj>`

<span data-ttu-id="18673-182">Určuje cestu a název souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="18673-182">Specifies the path and name of the project file.</span></span> <span data-ttu-id="18673-183">(Viz poznámka.) Pokud není zadáno, výchozí hodnoty k aktuálnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="18673-183">(See the NOTE.) If not specified, it defaults to the current directory.</span></span>

> [!NOTE]
> <span data-ttu-id="18673-184">Použijte cestu a název souboru projektu s `-p|--project` možnost.</span><span class="sxs-lookup"><span data-stu-id="18673-184">Use the path and name of the project file with the `-p|--project` option.</span></span> <span data-ttu-id="18673-185">Regrese v rozhraní příkazového řádku brání poskytuje cestu ke složce s .NET Core SDK 1.x.</span><span class="sxs-lookup"><span data-stu-id="18673-185">A regression in the CLI prevents providing a folder path with .NET Core SDK 1.x.</span></span> <span data-ttu-id="18673-186">Další informace o tomto problému najdete v tématu [dotnet. Spusťte -p, nelze spustit projekt (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).</span><span class="sxs-lookup"><span data-stu-id="18673-186">For more information about this issue, see [dotnet run -p, can not start a project (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).</span></span>

---

## <a name="examples"></a><span data-ttu-id="18673-187">Příklady</span><span class="sxs-lookup"><span data-stu-id="18673-187">Examples</span></span>

<span data-ttu-id="18673-188">Spusťte projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="18673-188">Run the project in the current directory:</span></span>

`dotnet run`

<span data-ttu-id="18673-189">Spusťte zadaného projektu:</span><span class="sxs-lookup"><span data-stu-id="18673-189">Run the specified project:</span></span>

`dotnet run --project /projects/proj1/proj1.csproj`

<span data-ttu-id="18673-190">Spusťte projekt v aktuálním adresáři ( `--help` argument v tomto příkladu je předán do aplikace, protože `--` použit argument):</span><span class="sxs-lookup"><span data-stu-id="18673-190">Run the project in the current directory (the `--help` argument in this example is passed to the application, since the `--` argument is used):</span></span>

`dotnet run --configuration Release -- --help`

<span data-ttu-id="18673-191">Obnovte závislosti a nástroje pro projekt v aktuálním adresáři jen s minimální výstup a spusťte projekt: (.NET Core SDK 2.0 a novější):</span><span class="sxs-lookup"><span data-stu-id="18673-191">Restore dependencies and tools for the project in the current directory only showing minimal output and then run the project: (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet run --verbosity m`