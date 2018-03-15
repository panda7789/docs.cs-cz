---
title: "DotNet. Spusťte příkaz: .NET Core rozhraní příkazového řádku"
description: "Dotnet, spusťte příkaz poskytuje vhodnou možnost pro spuštění aplikace ze zdrojového kódu."
author: mairaw
ms.author: mairaw
ms.date: 03/10/2018
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 251aca6dcd3edb17fe86dc03ea8f5c6d7d699d48
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2018
---
# <a name="dotnet-run"></a><span data-ttu-id="d235e-103">Spustit DotNet.</span><span class="sxs-lookup"><span data-stu-id="d235e-103">dotnet run</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="d235e-104">Název</span><span class="sxs-lookup"><span data-stu-id="d235e-104">Name</span></span>

<span data-ttu-id="d235e-105">`dotnet run` -Běží zdrojový kód bez jakýchkoli explicitní kompilace nebo spusťte příkazy.</span><span class="sxs-lookup"><span data-stu-id="d235e-105">`dotnet run` - Runs source code without any explicit compile or launch commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d235e-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="d235e-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="d235e-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="d235e-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies] [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d235e-108">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="d235e-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]]
dotnet run [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="d235e-109">Popis</span><span class="sxs-lookup"><span data-stu-id="d235e-109">Description</span></span>

<span data-ttu-id="d235e-110">`dotnet run` Příkaz poskytuje vhodnou možnost pro spuštění aplikace ze zdrojového kódu se jeden příkaz.</span><span class="sxs-lookup"><span data-stu-id="d235e-110">The `dotnet run` command provides a convenient option to run your application from the source code with one command.</span></span> <span data-ttu-id="d235e-111">Je vhodné pro rychlé iterativní vývoj z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="d235e-111">It's useful for fast iterative development from the command line.</span></span> <span data-ttu-id="d235e-112">Příkaz závisí na [ `dotnet build` ](dotnet-build.md) k vytvoření kód.</span><span class="sxs-lookup"><span data-stu-id="d235e-112">The command depends on the [`dotnet build`](dotnet-build.md) command to build the code.</span></span> <span data-ttu-id="d235e-113">Všechny požadavky pro sestavení, jako je například, je nutné obnovit projekt nejprve použít `dotnet run` také.</span><span class="sxs-lookup"><span data-stu-id="d235e-113">Any requirements for the build, such as that the project must be restored first, apply to `dotnet run` as well.</span></span>

<span data-ttu-id="d235e-114">Výstupní soubory se zapisují do výchozího umístění, což je `bin/<configuration>/<target>`.</span><span class="sxs-lookup"><span data-stu-id="d235e-114">Output files are written into the default location, which is `bin/<configuration>/<target>`.</span></span> <span data-ttu-id="d235e-115">Například pokud máte `netcoreapp1.0` aplikace a můžete spustit `dotnet run`, se umístí výstup v `bin/Debug/netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="d235e-115">For example if you have a `netcoreapp1.0` application and you run `dotnet run`, the output is placed in `bin/Debug/netcoreapp1.0`.</span></span> <span data-ttu-id="d235e-116">Soubory jsou přepsány podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="d235e-116">Files are overwritten as needed.</span></span> <span data-ttu-id="d235e-117">Dočasné soubory jsou umístěny v `obj` adresáře.</span><span class="sxs-lookup"><span data-stu-id="d235e-117">Temporary files are placed in the `obj` directory.</span></span>

<span data-ttu-id="d235e-118">Pokud projekt určuje více rozhraní, provádění `dotnet run` vede k chybě, pokud `-f|--framework <FRAMEWORK>` možnost slouží k určení rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d235e-118">If the project specifies multiple frameworks, executing `dotnet run` results in an error unless the `-f|--framework <FRAMEWORK>` option is used to specify the framework.</span></span>

<span data-ttu-id="d235e-119">`dotnet run` Příkaz se používá v souvislosti s projekty, Nevytvořen sestavení.</span><span class="sxs-lookup"><span data-stu-id="d235e-119">The `dotnet run` command is used in the context of projects, not built assemblies.</span></span> <span data-ttu-id="d235e-120">Pokud se pokoušíte spustit framework závislé aplikace DLL místo, musíte použít [dotnet](dotnet.md) bez příkaz.</span><span class="sxs-lookup"><span data-stu-id="d235e-120">If you're trying to run a framework-dependent application DLL instead, you must use [dotnet](dotnet.md) without a command.</span></span> <span data-ttu-id="d235e-121">Chcete-li například spustit `myapp.dll`, použijte:</span><span class="sxs-lookup"><span data-stu-id="d235e-121">For example, to run `myapp.dll`, use:</span></span>

```
dotnet myapp.dll
```

<span data-ttu-id="d235e-122">Další informace o `dotnet` ovladač, najdete v článku [.NET Core příkazového řádku nástroje (CLI)](index.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="d235e-122">For more information on the `dotnet` driver, see the [.NET Core Command Line Tools (CLI)](index.md) topic.</span></span>

<span data-ttu-id="d235e-123">Aby bylo možné spustit aplikaci `dotnet run` příkaz vyřeší závislosti aplikace, které jsou mimo sdílený modul runtime z mezipaměti NuGet.</span><span class="sxs-lookup"><span data-stu-id="d235e-123">In order to run the application, the `dotnet run` command resolves the dependencies of the application that are outside of the shared runtime from the NuGet cache.</span></span> <span data-ttu-id="d235e-124">Protože se používá v mezipaměti závislosti, nedoporučujeme používat `dotnet run` ke spouštění aplikací v provozním prostředí.</span><span class="sxs-lookup"><span data-stu-id="d235e-124">Because it uses cached dependencies, it's not recommended to use `dotnet run` to run applications in production.</span></span> <span data-ttu-id="d235e-125">Místo toho [vytvořit nasazení](../deploying/index.md) pomocí [ `dotnet publish` ](dotnet-publish.md) příkazů a nasadit publikované výstup.</span><span class="sxs-lookup"><span data-stu-id="d235e-125">Instead, [create a deployment](../deploying/index.md) using the [`dotnet publish`](dotnet-publish.md) command and deploy the published output.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a><span data-ttu-id="d235e-126">Možnosti</span><span class="sxs-lookup"><span data-stu-id="d235e-126">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="d235e-127">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="d235e-127">.NET Core 2.x</span></span>](#tab/netcore2x)

`--`

<span data-ttu-id="d235e-128">Vymezuje argumenty, které mají `dotnet run` z argumentů pro aplikace spuštěna.</span><span class="sxs-lookup"><span data-stu-id="d235e-128">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="d235e-129">Všechny argumenty po touto jsou předány aplikace spuštěná.</span><span class="sxs-lookup"><span data-stu-id="d235e-129">All arguments after this one are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="d235e-130">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="d235e-130">Defines the build configuration.</span></span> <span data-ttu-id="d235e-131">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="d235e-131">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="d235e-132">Vytvoří a spustí aplikace pomocí zadané [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="d235e-132">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="d235e-133">Rozhraní musí být zadán v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="d235e-133">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="d235e-134">Vynutí všechny závislosti pro přeloženy i v případě, že poslední obnovení bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="d235e-134">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="d235e-135">Jde o ekvivalent odstraňování *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="d235e-135">This is equivalent to deleting *project.assets.json*.</span></span>

`-h|--help`

<span data-ttu-id="d235e-136">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="d235e-136">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="d235e-137">Název spuštění profilu (pokud existuje) pro použití při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="d235e-137">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="d235e-138">Spuštění profily jsou definovány v *launchSettings.json* souborů a jsou obvykle nazývá `Development`, `Staging` a `Production`.</span><span class="sxs-lookup"><span data-stu-id="d235e-138">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging` and `Production`.</span></span> <span data-ttu-id="d235e-139">Další informace najdete v tématu [práce s několika prostředí](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="d235e-139">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="d235e-140">Není sestavení projektu dřív, než spustíte.</span><span class="sxs-lookup"><span data-stu-id="d235e-140">Doesn't build the project before running.</span></span>

`--no-dependencies`

<span data-ttu-id="d235e-141">Při obnovování projektu s odkazy na projekt na projekt (P2P), obnoví kořenového projektu a není odkazuje.</span><span class="sxs-lookup"><span data-stu-id="d235e-141">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="d235e-142">Není pokus o použití *launchSettings.json* konfigurace aplikace.</span><span class="sxs-lookup"><span data-stu-id="d235e-142">Doesn't attempt to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="d235e-143">Neprovede implicitní obnovení, při spuštění příkazu.</span><span class="sxs-lookup"><span data-stu-id="d235e-143">Doesn't perform an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="d235e-144">Určuje cestu k souboru projektu ke spuštění (úplná cesta nebo název).</span><span class="sxs-lookup"><span data-stu-id="d235e-144">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="d235e-145">Pokud není zadaný, výchozí se k aktuálnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="d235e-145">It defaults to the current directory if not specified.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="d235e-146">Určuje cílový modul runtime pro obnovení balíčků pro.</span><span class="sxs-lookup"><span data-stu-id="d235e-146">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="d235e-147">Seznam Runtime identifikátorů (RID), najdete v článku [identifikátorů RID katalogu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="d235e-147">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d235e-148">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="d235e-148">.NET Core 1.x</span></span>](#tab/netcore1x)

`--`

<span data-ttu-id="d235e-149">Vymezuje argumenty, které mají `dotnet run` z argumentů pro aplikace spuštěna.</span><span class="sxs-lookup"><span data-stu-id="d235e-149">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="d235e-150">Všechny argumenty po touto jsou předány aplikace spuštěná.</span><span class="sxs-lookup"><span data-stu-id="d235e-150">All arguments after this one are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="d235e-151">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="d235e-151">Defines the build configuration.</span></span> <span data-ttu-id="d235e-152">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="d235e-152">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="d235e-153">Vytvoří a spustí aplikace pomocí zadané [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="d235e-153">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="d235e-154">Rozhraní musí být zadán v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="d235e-154">The framework must be specified in the project file.</span></span>

`-h|--help`

<span data-ttu-id="d235e-155">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="d235e-155">Prints out a short help for the command.</span></span>

`-p|--project <PATH/PROJECT.csproj>`

<span data-ttu-id="d235e-156">Určuje cestu a název souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="d235e-156">Specifies the path and name of the project file.</span></span> <span data-ttu-id="d235e-157">(Viz poznámka.) Pokud není zadaný, výchozí se k aktuálnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="d235e-157">(See the NOTE.) It defaults to the current directory if not specified.</span></span>

> [!NOTE]
> <span data-ttu-id="d235e-158">Použijte cestu a název souboru projektu s `-p|--project` možnost.</span><span class="sxs-lookup"><span data-stu-id="d235e-158">Use the path and name of the project file with the `-p|--project` option.</span></span> <span data-ttu-id="d235e-159">Regrese v rozhraní příkazového řádku brání poskytuje cestu ke složce s .NET Core SDK 1.x.</span><span class="sxs-lookup"><span data-stu-id="d235e-159">A regression in the CLI prevents providing a folder path with .NET Core SDK 1.x.</span></span> <span data-ttu-id="d235e-160">Další informace o tomto problému najdete v tématu [dotnet. Spusťte -p, nelze spustit projekt (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).</span><span class="sxs-lookup"><span data-stu-id="d235e-160">For more information about this issue, see [dotnet run -p, can not start a project (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).</span></span>

---

## <a name="examples"></a><span data-ttu-id="d235e-161">Příklady</span><span class="sxs-lookup"><span data-stu-id="d235e-161">Examples</span></span>

<span data-ttu-id="d235e-162">Spusťte projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="d235e-162">Run the project in the current directory:</span></span>

`dotnet run`

<span data-ttu-id="d235e-163">Spusťte zadaného projektu:</span><span class="sxs-lookup"><span data-stu-id="d235e-163">Run the specified project:</span></span>

`dotnet run --project /projects/proj1/proj1.csproj`

<span data-ttu-id="d235e-164">Spusťte projekt v aktuálním adresáři ( `--help` argument v tomto příkladu je předán do aplikace, protože `--` použit argument):</span><span class="sxs-lookup"><span data-stu-id="d235e-164">Run the project in the current directory (the `--help` argument in this example is passed to the application, since the `--` argument is used):</span></span>

`dotnet run --configuration Release -- --help`

<span data-ttu-id="d235e-165">Obnovte závislosti a nástroje pro projekt v aktuálním adresáři jen s minimální výstup a spusťte projekt: (.NET Core SDK 2.0 a novější):</span><span class="sxs-lookup"><span data-stu-id="d235e-165">Restore dependencies and tools for the project in the current directory only showing minimal output and then run the project: (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet run --verbosity m`