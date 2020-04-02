---
title: dotnet publikovat, příkaz
description: Příkaz publikování dotnet publikuje projekt nebo řešení .NET Core do adresáře.
ms.date: 02/24/2020
ms.openlocfilehash: 0e18220443f3713c86c257fcf401b98ddd716ebc
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588272"
---
# <a name="dotnet-publish"></a><span data-ttu-id="18dd0-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="18dd0-103">dotnet publish</span></span>

<span data-ttu-id="18dd0-104">**Tento článek se týká:** ✔️ .NET Core 2.1 SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="18dd0-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="18dd0-105">Name (Název)</span><span class="sxs-lookup"><span data-stu-id="18dd0-105">Name</span></span>

<span data-ttu-id="18dd0-106">`dotnet publish`- Publikuje aplikaci a její závislosti do složky pro nasazení do hostitelského systému.</span><span class="sxs-lookup"><span data-stu-id="18dd0-106">`dotnet publish` - Publishes the application and its dependencies to a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="18dd0-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="18dd0-107">Synopsis</span></span>

```dotnetcli
dotnet publish [<PROJECT>|<SOLUTION>] [-c|--configuration]
    [-f|--framework] [--force] [--interactive] [--manifest]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo]
    [-o|--output] [-r|--runtime] [--self-contained]
    [--no-self-contained] [-v|--verbosity] [--version-suffix]

dotnet publish [-h|--help]
```

## <a name="description"></a><span data-ttu-id="18dd0-108">Popis</span><span class="sxs-lookup"><span data-stu-id="18dd0-108">Description</span></span>

<span data-ttu-id="18dd0-109">`dotnet publish`zkompiluje aplikaci, pročte její závislosti zadané v souboru projektu a publikuje výslednou sadu souborů do adresáře.</span><span class="sxs-lookup"><span data-stu-id="18dd0-109">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="18dd0-110">Výstup zahrnuje následující aktiva:</span><span class="sxs-lookup"><span data-stu-id="18dd0-110">The output includes the following assets:</span></span>

- <span data-ttu-id="18dd0-111">Kód zprostředkujícího jazyka (IL) v sestavení s rozšířením *dll.*</span><span class="sxs-lookup"><span data-stu-id="18dd0-111">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
- <span data-ttu-id="18dd0-112">Soubor *.deps.json,* který obsahuje všechny závislosti projektu.</span><span class="sxs-lookup"><span data-stu-id="18dd0-112">A *.deps.json* file that includes all of the dependencies of the project.</span></span>
- <span data-ttu-id="18dd0-113">Soubor *.runtimeconfig.json,* který určuje sdílený runtime, který aplikace očekává, stejně jako další možnosti konfigurace pro runtime (například typ uvolňování paměti).</span><span class="sxs-lookup"><span data-stu-id="18dd0-113">A *.runtimeconfig.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
- <span data-ttu-id="18dd0-114">Závislosti aplikace, které jsou zkopírovány z mezipaměti NuGet do výstupní složky.</span><span class="sxs-lookup"><span data-stu-id="18dd0-114">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="18dd0-115">Výstup `dotnet publish` příkazu je připraven k nasazení do hostitelského systému (například server, PC, Mac, notebook) pro spuštění.</span><span class="sxs-lookup"><span data-stu-id="18dd0-115">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="18dd0-116">Je to jediný oficiálně podporovaný způsob, jak připravit aplikaci pro nasazení.</span><span class="sxs-lookup"><span data-stu-id="18dd0-116">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="18dd0-117">V závislosti na typu nasazení, který projekt určuje, může nebo nemusí mít hostitelský systém na něm nainstalovanou sdílenou runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="18dd0-117">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="18dd0-118">Další informace naleznete v [tématu Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="18dd0-118">For more information, see [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

### <a name="msbuild"></a><span data-ttu-id="18dd0-119">MSBuild</span><span class="sxs-lookup"><span data-stu-id="18dd0-119">MSBuild</span></span>

<span data-ttu-id="18dd0-120">Příkaz `dotnet publish` volá MSBuild, který `Publish` vyvolá cíl.</span><span class="sxs-lookup"><span data-stu-id="18dd0-120">The `dotnet publish` command calls MSBuild, which invokes the `Publish` target.</span></span> <span data-ttu-id="18dd0-121">Všechny parametry `dotnet publish` předané jsou předány MSBuild.</span><span class="sxs-lookup"><span data-stu-id="18dd0-121">Any parameters passed to `dotnet publish` are passed to MSBuild.</span></span> <span data-ttu-id="18dd0-122">A `-c` `-o` parametry mapovat na MSBuild `Configuration` a `OutputPath` vlastnosti, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="18dd0-122">The `-c` and `-o` parameters map to MSBuild's `Configuration` and `OutputPath` properties, respectively.</span></span>

<span data-ttu-id="18dd0-123">Příkaz `dotnet publish` přijímá možnosti MSBuild, `-p` například `-l` pro nastavení vlastností a definování protokolování.</span><span class="sxs-lookup"><span data-stu-id="18dd0-123">The `dotnet publish` command accepts MSBuild options, such as `-p` for setting properties and `-l` to define a logger.</span></span> <span data-ttu-id="18dd0-124">Vlastnost MSBuild můžete například nastavit pomocí formátu: `-p:<NAME>=<VALUE>`.</span><span class="sxs-lookup"><span data-stu-id="18dd0-124">For example, you can set an MSBuild property by using the format: `-p:<NAME>=<VALUE>`.</span></span> <span data-ttu-id="18dd0-125">Můžete také nastavit vlastnosti související s publikováním odkazem na soubor *PubXML,* například:</span><span class="sxs-lookup"><span data-stu-id="18dd0-125">You can also set publish-related properties by referring to a *.pubxml* file, for example:</span></span>

```dotnetcli
dotnet publish -p:PublishProfile=Properties\PublishProfiles\FolderProfile.pubxml
```

<span data-ttu-id="18dd0-126">Další informace najdete v následujících materiálech:</span><span class="sxs-lookup"><span data-stu-id="18dd0-126">For more information, see the following resources:</span></span>

- [<span data-ttu-id="18dd0-127">Odkaz na příkazový řádek MSBuild</span><span class="sxs-lookup"><span data-stu-id="18dd0-127">MSBuild command-line reference</span></span>](/visualstudio/msbuild/msbuild-command-line-reference)
- [<span data-ttu-id="18dd0-128">Visual Studio publikuje profily (.pubxml) pro nasazení aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="18dd0-128">Visual Studio publish profiles (.pubxml) for ASP.NET Core app deployment</span></span>](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [<span data-ttu-id="18dd0-129">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="18dd0-129">dotnet msbuild</span></span>](dotnet-msbuild.md)

## <a name="arguments"></a><span data-ttu-id="18dd0-130">Argumenty</span><span class="sxs-lookup"><span data-stu-id="18dd0-130">Arguments</span></span>

- **`PROJECT|SOLUTION`**

  <span data-ttu-id="18dd0-131">Projekt nebo řešení publikovat.</span><span class="sxs-lookup"><span data-stu-id="18dd0-131">The project or solution to publish.</span></span>
  
  * <span data-ttu-id="18dd0-132">`PROJECT`je cesta a název souboru projektu [jazyka C#](csproj.md), F# nebo Visual Basic nebo cesta k adresáři, který obsahuje soubor projektu Jazyka C#, F# nebo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="18dd0-132">`PROJECT` is the path and filename of a [C#](csproj.md), F#, or Visual Basic project file, or the path to a directory that contains a C#, F#, or Visual Basic project file.</span></span> <span data-ttu-id="18dd0-133">Pokud adresář není zadán, je výchozí pro aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="18dd0-133">If the directory is not specified, it defaults to the current directory.</span></span>

  * <span data-ttu-id="18dd0-134">`SOLUTION`je cesta a název souboru řešení (*přípona .sln)* nebo cesta k adresáři, který obsahuje soubor řešení.</span><span class="sxs-lookup"><span data-stu-id="18dd0-134">`SOLUTION` is the path and filename of a solution file (*.sln* extension), or the path to a directory that contains a solution file.</span></span> <span data-ttu-id="18dd0-135">Pokud adresář není zadán, je výchozí pro aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="18dd0-135">If the directory is not specified, it defaults to the current directory.</span></span> <span data-ttu-id="18dd0-136">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="18dd0-136">Available since .NET Core 3.0 SDK.</span></span>

## <a name="options"></a><span data-ttu-id="18dd0-137">Možnosti</span><span class="sxs-lookup"><span data-stu-id="18dd0-137">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="18dd0-138">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="18dd0-138">Defines the build configuration.</span></span> <span data-ttu-id="18dd0-139">Výchozí hodnota pro `Debug`většinu projektů je , ale můžete přepsat nastavení konfigurace sestavení v projektu.</span><span class="sxs-lookup"><span data-stu-id="18dd0-139">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="18dd0-140">Publikuje aplikaci pro zadaný [cílový rámec](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="18dd0-140">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="18dd0-141">Je nutné zadat cílovou architekturu v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="18dd0-141">You must specify the target framework in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="18dd0-142">Vynutí vyřešení všech závislostí, i když bylo poslední obnovení úspěšné.</span><span class="sxs-lookup"><span data-stu-id="18dd0-142">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="18dd0-143">Zadání tohoto příznaku je stejné jako odstranění souboru *project.assets.json.*</span><span class="sxs-lookup"><span data-stu-id="18dd0-143">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="18dd0-144">Vytiskne krátkou nápovědu pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="18dd0-144">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="18dd0-145">Umožňuje příkazu zastavit a čekat na vstup uživatele nebo akci.</span><span class="sxs-lookup"><span data-stu-id="18dd0-145">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="18dd0-146">Například k dokončení ověřování.</span><span class="sxs-lookup"><span data-stu-id="18dd0-146">For example, to complete authentication.</span></span> <span data-ttu-id="18dd0-147">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="18dd0-147">Available since .NET Core 3.0 SDK.</span></span>

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  <span data-ttu-id="18dd0-148">Určuje jeden nebo více [cílových manifestů,](../deploying/runtime-store.md) které se mají použít k oříznutí sady balíčků publikovaných s aplikací.</span><span class="sxs-lookup"><span data-stu-id="18dd0-148">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="18dd0-149">Soubor manifestu je součástí výstupu [ `dotnet store` příkazu](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="18dd0-149">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="18dd0-150">Chcete-li zadat více `--manifest` manifestů, přidejte možnost pro každý manifest.</span><span class="sxs-lookup"><span data-stu-id="18dd0-150">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span>

- **`--no-build`**

  <span data-ttu-id="18dd0-151">Nesestavuje projekt před publikováním.</span><span class="sxs-lookup"><span data-stu-id="18dd0-151">Doesn't build the project before publishing.</span></span> <span data-ttu-id="18dd0-152">Také implicitně nastaví příznak. `--no-restore`</span><span class="sxs-lookup"><span data-stu-id="18dd0-152">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="18dd0-153">Ignoruje odkazy projektu na projekt a obnoví pouze kořenový projekt.</span><span class="sxs-lookup"><span data-stu-id="18dd0-153">Ignores project-to-project references and only restores the root project.</span></span>

- **`--nologo`**

  <span data-ttu-id="18dd0-154">Nezobrazuje spouštěcí banner ani zprávu o autorských právech.</span><span class="sxs-lookup"><span data-stu-id="18dd0-154">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="18dd0-155">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="18dd0-155">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="18dd0-156">Nespustí implicitní obnovení při spuštění příkazu.</span><span class="sxs-lookup"><span data-stu-id="18dd0-156">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="18dd0-157">Určuje cestu pro výstupní adresář.</span><span class="sxs-lookup"><span data-stu-id="18dd0-157">Specifies the path for the output directory.</span></span>
  
  <span data-ttu-id="18dd0-158">Pokud není zadán, je výchozí *[project_file_folder]./bin/[konfigurace]/[framework]/publish/* pro spustitelný modul závislý na spustitelném modulu a binární soubory mezi platformami.</span><span class="sxs-lookup"><span data-stu-id="18dd0-158">If not specified, it defaults to *[project_file_folder]./bin/[configuration]/[framework]/publish/* for a runtime-dependent executable and cross-platform binaries.</span></span> <span data-ttu-id="18dd0-159">Ve výchozím nastavení je *[project_file_folder]/bin/[configuration]/[framework]/[runtime]/publish/* pro samostatný spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="18dd0-159">It defaults to *[project_file_folder]/bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained executable.</span></span>

  - <span data-ttu-id="18dd0-160">Sada .NET Core 3.x SDK a novější</span><span class="sxs-lookup"><span data-stu-id="18dd0-160">.NET Core 3.x SDK and later</span></span>
  
    <span data-ttu-id="18dd0-161">Pokud je při publikování projektu zadána relativní cesta, je vygenerovaný výstupní adresář relativní vzhledem k aktuálnímu pracovnímu adresáři, nikoli k umístění souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="18dd0-161">If a relative path is specified when publishing a project, the output directory generated is relative to the current working directory, not to the project file location.</span></span>

    <span data-ttu-id="18dd0-162">Pokud je při publikování řešení zadána relativní cesta, veškerý výstup pro všechny projekty přejde do zadané složky vzhledem k aktuálnímu pracovnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="18dd0-162">If a relative path is specified when publishing a solution, all output for all projects go into the specified folder relative to the current working directory.</span></span> <span data-ttu-id="18dd0-163">Chcete-li vytvořit výstup publikování jít do samostatných složek pro `PublishDir` každý projekt, `--output` zadejte relativní cestu pomocí msbuild vlastnost místo možnosti.</span><span class="sxs-lookup"><span data-stu-id="18dd0-163">To make publish output go to separate folders for each project, specify a relative path by using the msbuild `PublishDir` property instead of the `--output` option.</span></span> <span data-ttu-id="18dd0-164">Například `dotnet publish -p:PublishDir=.\publish` odešle výstup publikování pro `publish` každý projekt do složky ve složce, která obsahuje soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="18dd0-164">For example, `dotnet publish -p:PublishDir=.\publish` sends publish output for each project to a `publish` folder under the folder that contains the project file.</span></span>

  - <span data-ttu-id="18dd0-165">Sada SDK rozhraní .NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="18dd0-165">.NET Core 2.x SDK</span></span>
  
    <span data-ttu-id="18dd0-166">Pokud je při publikování projektu zadána relativní cesta, je vygenerovaný výstupní adresář relativní vzhledem k umístění souboru projektu, nikoli k aktuálnímu pracovnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="18dd0-166">If a relative path is specified when publishing a project, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

    <span data-ttu-id="18dd0-167">Pokud je při publikování řešení zadána relativní cesta, výstup každého projektu přejde do samostatné složky vzhledem k umístění souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="18dd0-167">If a relative path is specified when publishing a solution, each project's output goes into a separate folder relative to the project file location.</span></span> <span data-ttu-id="18dd0-168">Pokud je při publikování řešení zadána absolutní cesta, veškerý výstup publikování pro všechny projekty přejde do zadané složky.</span><span class="sxs-lookup"><span data-stu-id="18dd0-168">If an absolute path is specified when publishing a solution, all publish output for all projects goes into the specified folder.</span></span>

- **`--self-contained [true|false]`**

  <span data-ttu-id="18dd0-169">Publikuje zaběhu .NET Core s vaší aplikací, takže runtime nemusí být nainstalován v cílovém počítači.</span><span class="sxs-lookup"><span data-stu-id="18dd0-169">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="18dd0-170">Výchozí `true` hodnota je, pokud je zadán identifikátor modulu runtime a projekt je spustitelný projekt (nikoli projekt knihovny).</span><span class="sxs-lookup"><span data-stu-id="18dd0-170">Default is `true` if a runtime identifier is specified and the project is an executable project (not a library project).</span></span> <span data-ttu-id="18dd0-171">Další informace naleznete v tématu [publikování a](../deploying/index.md) publikování [aplikací .NET Core pomocí rozhraní .NET Core .](../deploying/deploy-with-cli.md)</span><span class="sxs-lookup"><span data-stu-id="18dd0-171">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

  <span data-ttu-id="18dd0-172">Pokud je tato možnost `true` použita bez zadání nebo `false`, výchozí je `true`.</span><span class="sxs-lookup"><span data-stu-id="18dd0-172">If this option is used without specifying `true` or `false`, the default is `true`.</span></span> <span data-ttu-id="18dd0-173">V takovém případě nedávejte řešení nebo argument `--self-contained`projektu `true` ihned po , protože nebo `false` se očekává v této pozici.</span><span class="sxs-lookup"><span data-stu-id="18dd0-173">In that case, don't put the solution or project argument immediately after `--self-contained`, because `true` or `false` is expected in that position.</span></span>

- **`--no-self-contained`**

  <span data-ttu-id="18dd0-174">Odpovídá `--self-contained false`.</span><span class="sxs-lookup"><span data-stu-id="18dd0-174">Equivalent to `--self-contained false`.</span></span> <span data-ttu-id="18dd0-175">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="18dd0-175">Available since .NET Core 3.0 SDK.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="18dd0-176">Publikuje aplikaci pro daný běhový čas.</span><span class="sxs-lookup"><span data-stu-id="18dd0-176">Publishes the application for a given runtime.</span></span> <span data-ttu-id="18dd0-177">Seznam identifikátorů modulu Runtime (RID) naleznete v [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="18dd0-177">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="18dd0-178">Další informace naleznete v tématu [publikování a](../deploying/index.md) publikování [aplikací .NET Core pomocí rozhraní .NET Core .](../deploying/deploy-with-cli.md)</span><span class="sxs-lookup"><span data-stu-id="18dd0-178">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="18dd0-179">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="18dd0-179">Sets the verbosity level of the command.</span></span> <span data-ttu-id="18dd0-180">Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a .</span><span class="sxs-lookup"><span data-stu-id="18dd0-180">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="18dd0-181">Výchozí hodnota `minimal`je .</span><span class="sxs-lookup"><span data-stu-id="18dd0-181">Default value is `minimal`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="18dd0-182">Definuje příponu verze, která nahradí hvězdičku (`*`) v poli verze souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="18dd0-182">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

## <a name="examples"></a><span data-ttu-id="18dd0-183">Příklady</span><span class="sxs-lookup"><span data-stu-id="18dd0-183">Examples</span></span>

- <span data-ttu-id="18dd0-184">Vytvořte [binární soubor pro běhový čas závislý na více platformách](../deploying/index.md#produce-a-cross-platform-binary) pro projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="18dd0-184">Create a [runtime-dependent cross-platform binary](../deploying/index.md#produce-a-cross-platform-binary) for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet publish
  ```

  <span data-ttu-id="18dd0-185">Počínaje .NET Core 3.0 SDK, tento příklad také vytvoří [spustitelný soubor závislý na modulu runtime](../deploying/index.md#publish-runtime-dependent) pro aktuální platformu.</span><span class="sxs-lookup"><span data-stu-id="18dd0-185">Starting with .NET Core 3.0 SDK, this example also creates a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the current platform.</span></span>

- <span data-ttu-id="18dd0-186">Vytvořte [samostatný spustitelný soubor](../deploying/index.md#publish-self-contained) pro projekt v aktuálním adresáři pro konkrétní modul runtime:</span><span class="sxs-lookup"><span data-stu-id="18dd0-186">Create a [self-contained executable](../deploying/index.md#publish-self-contained) for the project in the current directory, for a specific runtime:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  <span data-ttu-id="18dd0-187">Rid musí být v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="18dd0-187">The RID must be in the project file.</span></span>

- <span data-ttu-id="18dd0-188">Vytvořte [spustitelný soubor závislý na modulu runtime](../deploying/index.md#publish-runtime-dependent) pro projekt v aktuálním adresáři pro konkrétní platformu:</span><span class="sxs-lookup"><span data-stu-id="18dd0-188">Create a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the project in the current directory, for a specific platform:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  <span data-ttu-id="18dd0-189">Rid musí být v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="18dd0-189">The RID must be in the project file.</span></span> <span data-ttu-id="18dd0-190">Tento příklad platí pro .NET Core 3.0 SDK a novější verze.</span><span class="sxs-lookup"><span data-stu-id="18dd0-190">This example applies to .NET Core 3.0 SDK and later versions.</span></span>

- <span data-ttu-id="18dd0-191">Publikujte projekt v aktuálním adresáři pro konkrétní rozhraní runtime a cílový rámec:</span><span class="sxs-lookup"><span data-stu-id="18dd0-191">Publish the project in the current directory, for a specific runtime and target framework:</span></span>

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- <span data-ttu-id="18dd0-192">Publikování zadaného souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="18dd0-192">Publish the specified project file:</span></span>

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="18dd0-193">Publikujte aktuální aplikaci, ale neobnovte odkazy projektu na projekt (P2P), pouze kořenový projekt během operace obnovení:</span><span class="sxs-lookup"><span data-stu-id="18dd0-193">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation:</span></span>

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a><span data-ttu-id="18dd0-194">Viz také</span><span class="sxs-lookup"><span data-stu-id="18dd0-194">See also</span></span>

- [<span data-ttu-id="18dd0-195">Přehled publikování aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="18dd0-195">.NET Core application publishing overview</span></span>](../deploying/index.md)
- [<span data-ttu-id="18dd0-196">Publikování aplikací .NET Core pomocí rozhraní CLI jádra ROZHRANÍ .NET</span><span class="sxs-lookup"><span data-stu-id="18dd0-196">Publish .NET Core apps with the .NET Core CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="18dd0-197">Cílové architektury</span><span class="sxs-lookup"><span data-stu-id="18dd0-197">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="18dd0-198">Katalog IDentifier (RID) modulu runtime</span><span class="sxs-lookup"><span data-stu-id="18dd0-198">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="18dd0-199">Práce s macOS Catalina Notarization</span><span class="sxs-lookup"><span data-stu-id="18dd0-199">Working with macOS Catalina Notarization</span></span>](../install/macos-notarization-issues.md)
- [<span data-ttu-id="18dd0-200">Adresářová struktura publikované aplikace</span><span class="sxs-lookup"><span data-stu-id="18dd0-200">Directory structure of a published application</span></span>](/aspnet/core/hosting/directory-structure)
- [<span data-ttu-id="18dd0-201">Odkaz na příkazový řádek MSBuild</span><span class="sxs-lookup"><span data-stu-id="18dd0-201">MSBuild command-line reference</span></span>](/visualstudio/msbuild/msbuild-command-line-reference)
- [<span data-ttu-id="18dd0-202">Visual Studio publikuje profily (.pubxml) pro nasazení aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="18dd0-202">Visual Studio publish profiles (.pubxml) for ASP.NET Core app deployment</span></span>](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [<span data-ttu-id="18dd0-203">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="18dd0-203">dotnet msbuild</span></span>](dotnet-msbuild.md)
