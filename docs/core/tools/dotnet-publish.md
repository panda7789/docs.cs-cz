---
title: dotnet publish – příkaz
description: Příkaz dotnet publish publikuje projekt nebo řešení .NET Core do adresáře.
ms.date: 02/24/2020
ms.openlocfilehash: 64a68c97e01bbf962616b31210889eb23d3734f1
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608286"
---
# <a name="dotnet-publish"></a><span data-ttu-id="82160-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="82160-103">dotnet publish</span></span>

<span data-ttu-id="82160-104">**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="82160-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="82160-105">Name</span><span class="sxs-lookup"><span data-stu-id="82160-105">Name</span></span>

<span data-ttu-id="82160-106">`dotnet publish` -Publikuje aplikaci a její závislosti do složky pro nasazení do hostitelského systému.</span><span class="sxs-lookup"><span data-stu-id="82160-106">`dotnet publish` - Publishes the application and its dependencies to a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="82160-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="82160-107">Synopsis</span></span>

```dotnetcli
dotnet publish [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [-f|--framework <FRAMEWORK>] [--force] [--interactive]
    [--manifest <PATH_TO_MANIFEST_FILE>] [--no-build] [--no-dependencies]
    [--no-restore] [--nologo] [-o|--output <OUTPUT_DIRECTORY>]
    [-p:PublishReadyToRun=true] [-p:PublishSingleFile=true] [-p:PublishTrimmed=true]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [--self-contained [true|false]]
    [--no-self-contained] [-v|--verbosity <LEVEL>]
    [--version-suffix <VERSION_SUFFIX>]

dotnet publish -h|--help
```

## <a name="description"></a><span data-ttu-id="82160-108">Popis</span><span class="sxs-lookup"><span data-stu-id="82160-108">Description</span></span>

<span data-ttu-id="82160-109">`dotnet publish` zkompiluje aplikaci, přečte prostřednictvím svých závislostí zadaných v souboru projektu a publikuje výslednou sadu souborů do adresáře.</span><span class="sxs-lookup"><span data-stu-id="82160-109">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="82160-110">Výstup obsahuje následující prostředky:</span><span class="sxs-lookup"><span data-stu-id="82160-110">The output includes the following assets:</span></span>

- <span data-ttu-id="82160-111">Kód zprostředkujícího jazyka (IL) v sestavení s příponou *DLL* .</span><span class="sxs-lookup"><span data-stu-id="82160-111">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
- <span data-ttu-id="82160-112">*.deps.jsv* souboru, který obsahuje všechny závislosti projektu.</span><span class="sxs-lookup"><span data-stu-id="82160-112">A *.deps.json* file that includes all of the dependencies of the project.</span></span>
- <span data-ttu-id="82160-113">*.runtimeconfig.jsv* souboru, který určuje sdílený modul runtime, který aplikace očekává, a další možnosti konfigurace pro modul runtime (například typ uvolňování paměti).</span><span class="sxs-lookup"><span data-stu-id="82160-113">A *.runtimeconfig.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
- <span data-ttu-id="82160-114">Závislosti aplikace, které jsou zkopírovány z mezipaměti NuGet do výstupní složky.</span><span class="sxs-lookup"><span data-stu-id="82160-114">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="82160-115">`dotnet publish`Výstup příkazu je připravený k nasazení do hostitelského systému (například server, počítač, Mac, notebook) k provedení.</span><span class="sxs-lookup"><span data-stu-id="82160-115">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="82160-116">Jedná se o jediný oficiálně podporovaný způsob, jak připravit aplikaci pro nasazení.</span><span class="sxs-lookup"><span data-stu-id="82160-116">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="82160-117">V závislosti na typu nasazení, které projekt určuje, hostující systém může nebo nemusí mít nainstalovaný modul .NET Core Shared runtime.</span><span class="sxs-lookup"><span data-stu-id="82160-117">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="82160-118">Další informace najdete v tématu [publikování aplikací .NET Core pomocí .NET Core CLI](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="82160-118">For more information, see [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="82160-119">Implicitní obnovení</span><span class="sxs-lookup"><span data-stu-id="82160-119">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

### <a name="msbuild"></a><span data-ttu-id="82160-120">MSBuild</span><span class="sxs-lookup"><span data-stu-id="82160-120">MSBuild</span></span>

<span data-ttu-id="82160-121">`dotnet publish`Příkaz volá MSBuild, který vyvolá `Publish` cíl.</span><span class="sxs-lookup"><span data-stu-id="82160-121">The `dotnet publish` command calls MSBuild, which invokes the `Publish` target.</span></span> <span data-ttu-id="82160-122">Všechny parametry předané do `dotnet publish` jsou předány do nástroje MSBuild.</span><span class="sxs-lookup"><span data-stu-id="82160-122">Any parameters passed to `dotnet publish` are passed to MSBuild.</span></span> <span data-ttu-id="82160-123">`-c`Parametry a se `-o` mapují do `Configuration` vlastností a v `PublishDir` uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="82160-123">The `-c` and `-o` parameters map to MSBuild's `Configuration` and `PublishDir` properties, respectively.</span></span>

<span data-ttu-id="82160-124">`dotnet publish`Příkaz přijímá možnosti nástroje MSBuild, jako je například `-p` pro nastavení vlastností a `-l` k definování protokolovacího nástroje.</span><span class="sxs-lookup"><span data-stu-id="82160-124">The `dotnet publish` command accepts MSBuild options, such as `-p` for setting properties and `-l` to define a logger.</span></span> <span data-ttu-id="82160-125">Můžete například nastavit vlastnost MSBuild pomocí formátu: `-p:<NAME>=<VALUE>` .</span><span class="sxs-lookup"><span data-stu-id="82160-125">For example, you can set an MSBuild property by using the format: `-p:<NAME>=<VALUE>`.</span></span>

<span data-ttu-id="82160-126">Vlastnosti související s publikováním můžete také nastavit tak, že odkazujete na soubor *. pubxml* (k dispozici od verze .net Core 3,1 SDK).</span><span class="sxs-lookup"><span data-stu-id="82160-126">You can also set publish-related properties by referring to a *.pubxml* file (available since .NET Core 3.1 SDK).</span></span> <span data-ttu-id="82160-127">Příklad:</span><span class="sxs-lookup"><span data-stu-id="82160-127">For example:</span></span>

```dotnetcli
dotnet publish -p:PublishProfile=FolderProfile
```

<span data-ttu-id="82160-128">Předchozí příklad používá soubor *FolderProfile. pubxml* , který se nachází ve složce \* \<project_folder> /Properties/PublishProfiles\* .</span><span class="sxs-lookup"><span data-stu-id="82160-128">The preceding example uses the *FolderProfile.pubxml* file that is found in the *\<project_folder>/Properties/PublishProfiles* folder.</span></span> <span data-ttu-id="82160-129">Pokud při nastavování vlastnosti určíte cestu a příponu souboru `PublishProfile` , budou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="82160-129">If you specify a path and file extension when setting the `PublishProfile` property, they are ignored.</span></span> <span data-ttu-id="82160-130">Nástroj MSBuild ve výchozím nastavení vyhledává ve složce *Properties/PublishProfiles* a předpokládá příponu souboru *pubxml* .</span><span class="sxs-lookup"><span data-stu-id="82160-130">MSBuild by default looks in the *Properties/PublishProfiles* folder and assumes the *pubxml* file extension.</span></span> <span data-ttu-id="82160-131">Chcete-li zadat cestu a název souboru včetně přípony, nastavte `PublishProfileFullPath` vlastnost namísto `PublishProfile` Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="82160-131">To specify the path and filename including extension, set the `PublishProfileFullPath` property instead of the `PublishProfile` property.</span></span>

<span data-ttu-id="82160-132">Další informace naleznete v následujících zdrojích:</span><span class="sxs-lookup"><span data-stu-id="82160-132">For more information, see the following resources:</span></span>

- [<span data-ttu-id="82160-133">Referenční dokumentace pro použití nástroje MSBuild v příkazovém řádku</span><span class="sxs-lookup"><span data-stu-id="82160-133">MSBuild command-line reference</span></span>](/visualstudio/msbuild/msbuild-command-line-reference)
- [<span data-ttu-id="82160-134">Publikační profily sady Visual Studio (. pubxml) pro nasazení aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="82160-134">Visual Studio publish profiles (.pubxml) for ASP.NET Core app deployment</span></span>](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [<span data-ttu-id="82160-135">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="82160-135">dotnet msbuild</span></span>](dotnet-msbuild.md)

## <a name="arguments"></a><span data-ttu-id="82160-136">Arguments</span><span class="sxs-lookup"><span data-stu-id="82160-136">Arguments</span></span>

- **`PROJECT|SOLUTION`**

  <span data-ttu-id="82160-137">Projekt nebo řešení, které se má publikovat</span><span class="sxs-lookup"><span data-stu-id="82160-137">The project or solution to publish.</span></span>
  
  * <span data-ttu-id="82160-138">`PROJECT` je cesta a název souboru projektu [jazyka c#](csproj.md), f # nebo Visual Basic nebo cesta k adresáři, který obsahuje soubor projektu jazyka C#, f # nebo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="82160-138">`PROJECT` is the path and filename of a [C#](csproj.md), F#, or Visual Basic project file, or the path to a directory that contains a C#, F#, or Visual Basic project file.</span></span> <span data-ttu-id="82160-139">Pokud adresář není zadaný, použije se ve výchozím nastavení aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="82160-139">If the directory is not specified, it defaults to the current directory.</span></span>

  * <span data-ttu-id="82160-140">`SOLUTION` je cesta a název souboru řešení (*. sln* rozšíření) nebo cesta k adresáři, který obsahuje soubor řešení.</span><span class="sxs-lookup"><span data-stu-id="82160-140">`SOLUTION` is the path and filename of a solution file (*.sln* extension), or the path to a directory that contains a solution file.</span></span> <span data-ttu-id="82160-141">Pokud adresář není zadaný, použije se ve výchozím nastavení aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="82160-141">If the directory is not specified, it defaults to the current directory.</span></span> <span data-ttu-id="82160-142">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="82160-142">Available since .NET Core 3.0 SDK.</span></span>

## <a name="options"></a><span data-ttu-id="82160-143">Možnosti</span><span class="sxs-lookup"><span data-stu-id="82160-143">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="82160-144">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="82160-144">Defines the build configuration.</span></span> <span data-ttu-id="82160-145">Výchozí hodnota pro většinu projektů je `Debug` , ale můžete přepsat nastavení konfigurace sestavení v projektu.</span><span class="sxs-lookup"><span data-stu-id="82160-145">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="82160-146">Publikuje aplikaci pro zadanou [cílovou architekturu](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="82160-146">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="82160-147">V souboru projektu je nutné zadat cílovou architekturu.</span><span class="sxs-lookup"><span data-stu-id="82160-147">You must specify the target framework in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="82160-148">Vynutí vyřešení všech závislostí i v případě, že bylo poslední obnovení úspěšné.</span><span class="sxs-lookup"><span data-stu-id="82160-148">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="82160-149">Zadání tohoto příznaku je stejné jako odstranění *project.assets.jsv* souboru.</span><span class="sxs-lookup"><span data-stu-id="82160-149">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="82160-150">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="82160-150">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="82160-151">Umožňuje zastavení příkazu zastavit a počkat na vstup nebo akci uživatele.</span><span class="sxs-lookup"><span data-stu-id="82160-151">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="82160-152">Například k dokončení ověřování.</span><span class="sxs-lookup"><span data-stu-id="82160-152">For example, to complete authentication.</span></span> <span data-ttu-id="82160-153">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="82160-153">Available since .NET Core 3.0 SDK.</span></span>

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  <span data-ttu-id="82160-154">Určuje jeden nebo několik [cílových manifestů](../deploying/runtime-store.md) , které se použijí ke zkrácení sady balíčků publikovaných s aplikací.</span><span class="sxs-lookup"><span data-stu-id="82160-154">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="82160-155">Soubor manifestu je součástí výstupu [ `dotnet store` příkazu](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="82160-155">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="82160-156">Chcete-li zadat více manifestů, přidejte `--manifest` možnost pro každý manifest.</span><span class="sxs-lookup"><span data-stu-id="82160-156">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span>

- **`--no-build`**

  <span data-ttu-id="82160-157">Nevytvoří projekt před publikováním.</span><span class="sxs-lookup"><span data-stu-id="82160-157">Doesn't build the project before publishing.</span></span> <span data-ttu-id="82160-158">Také implicitně nastaví `--no-restore` příznak.</span><span class="sxs-lookup"><span data-stu-id="82160-158">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="82160-159">Ignoruje odkazy z projektu na projekt a obnoví pouze kořenový projekt.</span><span class="sxs-lookup"><span data-stu-id="82160-159">Ignores project-to-project references and only restores the root project.</span></span>

- **`--nologo`**

  <span data-ttu-id="82160-160">Nezobrazuje úvodní nápis nebo zprávu o autorských právech.</span><span class="sxs-lookup"><span data-stu-id="82160-160">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="82160-161">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="82160-161">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="82160-162">Při spuštění příkazu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="82160-162">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="82160-163">Určuje cestu k výstupnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="82160-163">Specifies the path for the output directory.</span></span>
  
  <span data-ttu-id="82160-164">Pokud není zadaný, použije se výchozí hodnota *[project_file_folder]./bin/[Configuration]/[Framework]/Publish/* pro spustitelný soubor závislý na rozhraní a binární soubory pro více platforem.</span><span class="sxs-lookup"><span data-stu-id="82160-164">If not specified, it defaults to *[project_file_folder]./bin/[configuration]/[framework]/publish/* for a framework-dependent executable and cross-platform binaries.</span></span> <span data-ttu-id="82160-165">Pro samostatně uložený spustitelný soubor má výchozí nastavení *[project_file_folder]/bin/[Configuration]/[Framework]/[runtime]/Publish/* .</span><span class="sxs-lookup"><span data-stu-id="82160-165">It defaults to *[project_file_folder]/bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained executable.</span></span>

  <span data-ttu-id="82160-166">Je-li výstupní složka ve webovém projektu ve složce projektu, `dotnet publish` výsledkem úspěchu příkazů jsou vnořené výstupní složky.</span><span class="sxs-lookup"><span data-stu-id="82160-166">In a web project, if the output folder is in the project folder, successive `dotnet publish` commands result in nested output folders.</span></span> <span data-ttu-id="82160-167">Pokud je například složka projektu *MyProject*a výstupní složka pro publikování je *MyProject/Published*a `dotnet publish` dvakrát spustíte, druhý příkaz spustí do *MyProject/Publish/* Publish a Publishing soubory obsahu, jako jsou soubory *. config* a *. JSON* .</span><span class="sxs-lookup"><span data-stu-id="82160-167">For example, if the project folder is *myproject*, and the publish output folder is *myproject/publish*, and you run `dotnet publish` twice, the second run puts content files such as *.config* and *.json* files in *myproject/publish/publish*.</span></span> <span data-ttu-id="82160-168">Chcete-li se vyhnout vnořování publikačních složek, zadejte složku pro publikování, která není **přímo** ve složce projektu, nebo vylučte složku pro publikování z projektu.</span><span class="sxs-lookup"><span data-stu-id="82160-168">To avoid nesting publish folders, specify a publish folder that is not **directly** under the project folder, or exclude the publish folder from the project.</span></span> <span data-ttu-id="82160-169">Chcete-li vyloučit složku pro publikování s názvem *publishoutput*, přidejte následující element do `PropertyGroup` elementu v souboru *. csproj* :</span><span class="sxs-lookup"><span data-stu-id="82160-169">To exclude a publish folder named *publishoutput*, add the following element to a `PropertyGroup` element in the *.csproj* file:</span></span>

  ```xml
  <DefaultItemExcludes>$(DefaultItemExcludes);publishoutput**</DefaultItemExcludes>
  ```

  - <span data-ttu-id="82160-170">.NET Core 3. x SDK a novější</span><span class="sxs-lookup"><span data-stu-id="82160-170">.NET Core 3.x SDK and later</span></span>
  
    <span data-ttu-id="82160-171">Pokud je při publikování projektu zadána relativní cesta, vygenerovaný výstupní adresář je relativní vzhledem k aktuálnímu pracovnímu adresáři, nikoli k umístění souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="82160-171">If a relative path is specified when publishing a project, the output directory generated is relative to the current working directory, not to the project file location.</span></span>

    <span data-ttu-id="82160-172">Pokud je při publikování řešení zadána relativní cesta, veškerý výstup pro všechny projekty přejde do zadané složky vzhledem k aktuálnímu pracovnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="82160-172">If a relative path is specified when publishing a solution, all output for all projects goes into the specified folder relative to the current working directory.</span></span> <span data-ttu-id="82160-173">Chcete-li, aby výstup pro publikování přešel do samostatných složek pro každý projekt, zadejte relativní cestu pomocí `PublishDir` vlastnosti MSBuild namísto `--output` Možnosti.</span><span class="sxs-lookup"><span data-stu-id="82160-173">To make publish output go to separate folders for each project, specify a relative path by using the msbuild `PublishDir` property instead of the `--output` option.</span></span> <span data-ttu-id="82160-174">Například `dotnet publish -p:PublishDir=.\publish` odesílá výstup publikování pro každý projekt do `publish` složky ve složce, která obsahuje soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="82160-174">For example, `dotnet publish -p:PublishDir=.\publish` sends publish output for each project to a `publish` folder under the folder that contains the project file.</span></span>

  - <span data-ttu-id="82160-175">Sada .NET Core 2. x SDK</span><span class="sxs-lookup"><span data-stu-id="82160-175">.NET Core 2.x SDK</span></span>
  
    <span data-ttu-id="82160-176">Pokud je při publikování projektu zadána relativní cesta, vygenerovaný výstupní adresář je relativní vzhledem k umístění souboru projektu, nikoli k aktuálnímu pracovnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="82160-176">If a relative path is specified when publishing a project, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

    <span data-ttu-id="82160-177">Pokud je při publikování řešení zadána relativní cesta, výstup každého projektu přejde do samostatné složky vzhledem k umístění souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="82160-177">If a relative path is specified when publishing a solution, each project's output goes into a separate folder relative to the project file location.</span></span> <span data-ttu-id="82160-178">Pokud je při publikování řešení zadána absolutní cesta, veškerý výstup publikování pro všechny projekty přejde do zadané složky.</span><span class="sxs-lookup"><span data-stu-id="82160-178">If an absolute path is specified when publishing a solution, all publish output for all projects goes into the specified folder.</span></span>

- **`-p:PublishReadyToRun=true`**

  <span data-ttu-id="82160-179">Zkompiluje sestavení aplikace jako formát ReadyToRun (R2R).</span><span class="sxs-lookup"><span data-stu-id="82160-179">Compiles application assemblies as ReadyToRun (R2R) format.</span></span> <span data-ttu-id="82160-180">R2R je forma kompilace v čase před zahájením (AOT).</span><span class="sxs-lookup"><span data-stu-id="82160-180">R2R is a form of ahead-of-time (AOT) compilation.</span></span> <span data-ttu-id="82160-181">Další informace najdete v tématu [ReadyToRun images](../whats-new/dotnet-core-3-0.md#readytorun-images).</span><span class="sxs-lookup"><span data-stu-id="82160-181">For more information, see [ReadyToRun images](../whats-new/dotnet-core-3-0.md#readytorun-images).</span></span> <span data-ttu-id="82160-182">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="82160-182">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="82160-183">Tuto možnost doporučujeme zadat v profilu publikování, nikoli na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="82160-183">We recommend that you specify this option in a publish profile rather than on the command line.</span></span> <span data-ttu-id="82160-184">Další informace najdete v tématu [MSBuild](#msbuild).</span><span class="sxs-lookup"><span data-stu-id="82160-184">For more information, see [MSBuild](#msbuild).</span></span>

- **`-p:PublishSingleFile=true`**

  <span data-ttu-id="82160-185">Zabalí aplikaci do spustitelného souboru s jedním souborem konkrétní platformy.</span><span class="sxs-lookup"><span data-stu-id="82160-185">Packages the app into a platform-specific single-file executable.</span></span> <span data-ttu-id="82160-186">Spustitelný soubor je samorozbalovací a obsahuje všechny závislosti (včetně nativních), které jsou nutné ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="82160-186">The executable is self-extracting and contains all dependencies (including native) that are required to run the app.</span></span> <span data-ttu-id="82160-187">Při prvním spuštění aplikace se aplikace extrahuje do adresáře na základě názvu aplikace a identifikátoru buildu.</span><span class="sxs-lookup"><span data-stu-id="82160-187">When the app is first run, the application is extracted to a directory based on the app name and build identifier.</span></span> <span data-ttu-id="82160-188">Spuštění je rychlejší, když aplikaci znovu spustíte.</span><span class="sxs-lookup"><span data-stu-id="82160-188">Startup is faster when the application is run again.</span></span> <span data-ttu-id="82160-189">Pokud se nepoužije nová verze, aplikace se už nebude muset extrahovat druhou dobu.</span><span class="sxs-lookup"><span data-stu-id="82160-189">The application doesn't need to extract itself a second time unless a new version is used.</span></span> <span data-ttu-id="82160-190">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="82160-190">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="82160-191">Další informace o publikování v jednom souboru najdete v [dokumentu návrhu sady prostředků s jedním souborem](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md).</span><span class="sxs-lookup"><span data-stu-id="82160-191">For more information about single-file publishing, see the [single-file bundler design document](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md).</span></span>

  <span data-ttu-id="82160-192">Tuto možnost doporučujeme zadat v profilu publikování, nikoli na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="82160-192">We recommend that you specify this option in a publish profile rather than on the command line.</span></span> <span data-ttu-id="82160-193">Další informace najdete v tématu [MSBuild](#msbuild).</span><span class="sxs-lookup"><span data-stu-id="82160-193">For more information, see [MSBuild](#msbuild).</span></span>

- **`-p:PublishTrimmed=true`**

  <span data-ttu-id="82160-194">Ořízne nepoužívané knihovny, aby se snížila velikost nasazení aplikace při publikování samostatného spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="82160-194">Trims unused libraries to reduce the deployment size of an app when publishing a self-contained executable.</span></span> <span data-ttu-id="82160-195">Další informace najdete v tématu [stříhání samostatných nasazení a spustitelných souborů](../deploying/trim-self-contained.md).</span><span class="sxs-lookup"><span data-stu-id="82160-195">For more information, see [Trim self-contained deployments and executables](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="82160-196">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="82160-196">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="82160-197">Tuto možnost doporučujeme zadat v profilu publikování, nikoli na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="82160-197">We recommend that you specify this option in a publish profile rather than on the command line.</span></span> <span data-ttu-id="82160-198">Další informace najdete v tématu [MSBuild](#msbuild).</span><span class="sxs-lookup"><span data-stu-id="82160-198">For more information, see [MSBuild](#msbuild).</span></span>

- **`--self-contained [true|false]`**

  <span data-ttu-id="82160-199">Publikuje modul runtime .NET Core ve vaší aplikaci, takže modul runtime nemusí být na cílovém počítači nainstalován.</span><span class="sxs-lookup"><span data-stu-id="82160-199">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="82160-200">Výchozí hodnota je `true` , pokud je zadán identifikátor modulu runtime a projekt je spustitelný projekt (ne projekt knihovny).</span><span class="sxs-lookup"><span data-stu-id="82160-200">Default is `true` if a runtime identifier is specified and the project is an executable project (not a library project).</span></span> <span data-ttu-id="82160-201">Další informace najdete v tématu [aplikace .NET Core – publikování](../deploying/index.md) a [publikování aplikací .net Core pomocí .NET Core CLI](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="82160-201">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

  <span data-ttu-id="82160-202">Pokud je tato možnost použita bez zadání `true` nebo `false` , je výchozí hodnota `true` .</span><span class="sxs-lookup"><span data-stu-id="82160-202">If this option is used without specifying `true` or `false`, the default is `true`.</span></span> <span data-ttu-id="82160-203">V takovém případě neumísťujte argument řešení nebo projektu hned po `--self-contained` , protože `true` nebo `false` se na této pozici očekává.</span><span class="sxs-lookup"><span data-stu-id="82160-203">In that case, don't put the solution or project argument immediately after `--self-contained`, because `true` or `false` is expected in that position.</span></span>

- **`--no-self-contained`**

  <span data-ttu-id="82160-204">Ekvivalent `--self-contained false` .</span><span class="sxs-lookup"><span data-stu-id="82160-204">Equivalent to `--self-contained false`.</span></span> <span data-ttu-id="82160-205">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="82160-205">Available since .NET Core 3.0 SDK.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="82160-206">Publikuje aplikaci pro daný modul runtime.</span><span class="sxs-lookup"><span data-stu-id="82160-206">Publishes the application for a given runtime.</span></span> <span data-ttu-id="82160-207">Seznam identifikátorů modulu runtime (identifikátorů RID) najdete v [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="82160-207">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="82160-208">Další informace najdete v tématu [aplikace .NET Core – publikování](../deploying/index.md) a [publikování aplikací .net Core pomocí .NET Core CLI](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="82160-208">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="82160-209">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="82160-209">Sets the verbosity level of the command.</span></span> <span data-ttu-id="82160-210">Povolené hodnoty jsou `q[uiet]` , `m[inimal]` ,, a `n[ormal]` `d[etailed]` `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="82160-210">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="82160-211">Výchozí hodnota je `minimal` .</span><span class="sxs-lookup"><span data-stu-id="82160-211">Default value is `minimal`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="82160-212">Definuje příponu verze, která nahradí hvězdičku ( `*` ) v poli verze souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="82160-212">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

## <a name="examples"></a><span data-ttu-id="82160-213">Příklady</span><span class="sxs-lookup"><span data-stu-id="82160-213">Examples</span></span>

- <span data-ttu-id="82160-214">Vytvořte [binární soubor pro více platforem závislý na rozhraní](../deploying/index.md#produce-a-cross-platform-binary) pro projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="82160-214">Create a [framework-dependent cross-platform binary](../deploying/index.md#produce-a-cross-platform-binary) for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet publish
  ```

  <span data-ttu-id="82160-215">Počínaje verzí .NET Core 3,0 SDK tento příklad také vytvoří [spustitelný soubor závislý na rozhraní](../deploying/index.md#publish-framework-dependent) pro aktuální platformu.</span><span class="sxs-lookup"><span data-stu-id="82160-215">Starting with .NET Core 3.0 SDK, this example also creates a [framework-dependent executable](../deploying/index.md#publish-framework-dependent) for the current platform.</span></span>

- <span data-ttu-id="82160-216">Vytvoření [samostatného spustitelného souboru](../deploying/index.md#publish-self-contained) pro projekt v aktuálním adresáři pro konkrétní modul runtime:</span><span class="sxs-lookup"><span data-stu-id="82160-216">Create a [self-contained executable](../deploying/index.md#publish-self-contained) for the project in the current directory, for a specific runtime:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  <span data-ttu-id="82160-217">Identifikátor RID musí být v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="82160-217">The RID must be in the project file.</span></span>

- <span data-ttu-id="82160-218">Vytvořte [spustitelný soubor závislý na rozhraní](../deploying/index.md#publish-framework-dependent) pro projekt v aktuálním adresáři pro konkrétní platformu:</span><span class="sxs-lookup"><span data-stu-id="82160-218">Create a [framework-dependent executable](../deploying/index.md#publish-framework-dependent) for the project in the current directory, for a specific platform:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  <span data-ttu-id="82160-219">Identifikátor RID musí být v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="82160-219">The RID must be in the project file.</span></span> <span data-ttu-id="82160-220">Tento příklad platí pro .NET Core 3,0 SDK a novější verze.</span><span class="sxs-lookup"><span data-stu-id="82160-220">This example applies to .NET Core 3.0 SDK and later versions.</span></span>

- <span data-ttu-id="82160-221">Publikování projektu v aktuálním adresáři pro konkrétní modul runtime a cílové rozhraní:</span><span class="sxs-lookup"><span data-stu-id="82160-221">Publish the project in the current directory, for a specific runtime and target framework:</span></span>

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- <span data-ttu-id="82160-222">Publikovat zadaný soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="82160-222">Publish the specified project file:</span></span>

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="82160-223">Publikování aktuální aplikace, ale neobnovujte odkazy na projekt na projekt (P2P), pouze kořenový projekt během operace obnovení:</span><span class="sxs-lookup"><span data-stu-id="82160-223">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation:</span></span>

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a><span data-ttu-id="82160-224">Viz také</span><span class="sxs-lookup"><span data-stu-id="82160-224">See also</span></span>

- [<span data-ttu-id="82160-225">Přehled publikování aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="82160-225">.NET Core application publishing overview</span></span>](../deploying/index.md)
- [<span data-ttu-id="82160-226">Publikování aplikací .NET Core pomocí .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="82160-226">Publish .NET Core apps with the .NET Core CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="82160-227">Cílové architektury</span><span class="sxs-lookup"><span data-stu-id="82160-227">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="82160-228">Katalog identifikátoru runtime (RID)</span><span class="sxs-lookup"><span data-stu-id="82160-228">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="82160-229">Práce s macOS Catalina notarization</span><span class="sxs-lookup"><span data-stu-id="82160-229">Working with macOS Catalina Notarization</span></span>](../install/macos-notarization-issues.md)
- [<span data-ttu-id="82160-230">Adresářová struktura publikované aplikace</span><span class="sxs-lookup"><span data-stu-id="82160-230">Directory structure of a published application</span></span>](/aspnet/core/hosting/directory-structure)
- [<span data-ttu-id="82160-231">Referenční dokumentace pro použití nástroje MSBuild v příkazovém řádku</span><span class="sxs-lookup"><span data-stu-id="82160-231">MSBuild command-line reference</span></span>](/visualstudio/msbuild/msbuild-command-line-reference)
- [<span data-ttu-id="82160-232">Publikační profily sady Visual Studio (. pubxml) pro nasazení aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="82160-232">Visual Studio publish profiles (.pubxml) for ASP.NET Core app deployment</span></span>](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [<span data-ttu-id="82160-233">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="82160-233">dotnet msbuild</span></span>](dotnet-msbuild.md)
- [<span data-ttu-id="82160-234">ILLInk. Tasks</span><span class="sxs-lookup"><span data-stu-id="82160-234">ILLInk.Tasks</span></span>](https://aka.ms/dotnet-illink)
