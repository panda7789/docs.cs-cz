---
title: dotnet – příkaz sestavení
description: Příkaz dotnet Build vytvoří projekt a všechny jeho závislosti.
ms.date: 10/07/2019
ms.openlocfilehash: 0a3e2c0e441cfdd1cb8266bc77dc1aba08af84d6
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522779"
---
# <a name="dotnet-build"></a><span data-ttu-id="e9ae6-103">dotnet build</span><span class="sxs-lookup"><span data-stu-id="e9ae6-103">dotnet build</span></span>

<span data-ttu-id="e9ae6-104">**Tento článek se týká: ✓** .NET Core 1. x SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="e9ae6-104">**This article applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="e9ae6-105">Name</span><span class="sxs-lookup"><span data-stu-id="e9ae6-105">Name</span></span>

<span data-ttu-id="e9ae6-106">`dotnet build` – sestavení projektu a všech jeho závislostí.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-106">`dotnet build` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e9ae6-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="e9ae6-107">Synopsis</span></span>

```dotnetcli
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--force] [--interactive] [--no-dependencies]
    [--no-incremental] [--no-restore] [--nologo] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```

## <a name="description"></a><span data-ttu-id="e9ae6-108">Popis</span><span class="sxs-lookup"><span data-stu-id="e9ae6-108">Description</span></span>

<span data-ttu-id="e9ae6-109">Příkaz `dotnet build` sestaví projekt a jeho závislosti do sady binárních souborů.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-109">The `dotnet build` command builds the project and its dependencies into a set of binaries.</span></span> <span data-ttu-id="e9ae6-110">Binární soubory obsahují kód projektu v souborech IL (Intermediate Language) s příponou *. dll* a soubory symbolů používané pro ladění s příponou *. pdb* .</span><span class="sxs-lookup"><span data-stu-id="e9ae6-110">The binaries include the project's code in Intermediate Language (IL) files with a *.dll* extension and symbol files used for debugging with a *.pdb* extension.</span></span> <span data-ttu-id="e9ae6-111">Vytvoří se soubor JSON závislosti ( *. DEPS. JSON*), který obsahuje seznam závislostí aplikace.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-111">A dependencies JSON file (*.deps.json*) is produced that lists the dependencies of the application.</span></span> <span data-ttu-id="e9ae6-112">Je vytvořen soubor *. runtimeconfig. JSON* , který určuje sdílený modul runtime a jeho verzi aplikace.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-112">A *.runtimeconfig.json* file is produced, which specifies the shared runtime and its version for the application.</span></span>

<span data-ttu-id="e9ae6-113">Pokud má projekt závislosti třetích stran, jako jsou knihovny z NuGet, jsou vyřešeny z mezipaměti NuGet a nejsou k dispozici s vytvořeným výstupem projektu.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-113">If the project has third-party dependencies, such as libraries from NuGet, they're resolved from the NuGet cache and aren't available with the project's built output.</span></span> <span data-ttu-id="e9ae6-114">V takovém případě produkt `dotnet build` není připraven k přenosu do jiného počítače ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-114">With that in mind, the product of `dotnet build` isn't ready to be transferred to another machine to run.</span></span> <span data-ttu-id="e9ae6-115">To je v kontrastu s chováním .NET Framework, při které sestavení spustitelného projektu (aplikace) vytvoří výstup, který je spustitelný na jakémkoli počítači, kde je nainstalován .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-115">This is in contrast to the behavior of the .NET Framework in which building an executable project (an application) produces output that's runnable on any machine where the .NET Framework is installed.</span></span> <span data-ttu-id="e9ae6-116">Chcete-li mít rozhraní .NET Core podobné prostředí, je nutné použít příkaz [dotnet Publish](dotnet-publish.md) .</span><span class="sxs-lookup"><span data-stu-id="e9ae6-116">To have a similar experience with .NET Core, you need to use the [dotnet publish](dotnet-publish.md) command.</span></span> <span data-ttu-id="e9ae6-117">Další informace najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="e9ae6-117">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span>

<span data-ttu-id="e9ae6-118">Sestavování vyžaduje soubor *Project. assets. JSON* , který obsahuje závislosti vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-118">Building requires the *project.assets.json* file, which lists the dependencies of your application.</span></span> <span data-ttu-id="e9ae6-119">Soubor se vytvoří při spuštění [`dotnet restore`](dotnet-restore.md) .</span><span class="sxs-lookup"><span data-stu-id="e9ae6-119">The file is created when [`dotnet restore`](dotnet-restore.md) is executed.</span></span> <span data-ttu-id="e9ae6-120">Bez zavedeného souboru prostředků nemůže nástroj překládat referenční sestavení, což má za následek chyby.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-120">Without the assets file in place, the tooling can't resolve reference assemblies, which results in errors.</span></span> <span data-ttu-id="e9ae6-121">Pomocí sady .NET Core 1. x SDK jste před spuštěním `dotnet build` museli explicitně spustit `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-121">With .NET Core 1.x SDK, you needed to explicitly run `dotnet restore` before running `dotnet build`.</span></span> <span data-ttu-id="e9ae6-122">Počínaje verzí .NET Core 2,0 SDK se `dotnet restore` spouští implicitně při spuštění `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-122">Starting with .NET Core 2.0 SDK, `dotnet restore` runs implicitly when you run `dotnet build`.</span></span> <span data-ttu-id="e9ae6-123">Pokud chcete zakázat implicitní obnovení při spuštění příkazu Build, můžete předat možnost `--no-restore`.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-123">If you want to disable implicit restore when running the build command, you can pass the `--no-restore` option.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

<span data-ttu-id="e9ae6-124">Zda je projekt spustitelný nebo není určen vlastností `<OutputType>` v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-124">Whether the project is executable or not is determined by the `<OutputType>` property in the project file.</span></span> <span data-ttu-id="e9ae6-125">Následující příklad ukazuje projekt, který vytváří spustitelný kód:</span><span class="sxs-lookup"><span data-stu-id="e9ae6-125">The following example shows a project that produces executable code:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="e9ae6-126">Chcete-li vytvořit knihovnu, vynechejte vlastnost `<OutputType>`.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-126">To produce a library, omit the `<OutputType>` property.</span></span> <span data-ttu-id="e9ae6-127">Hlavním rozdílem v sestavení výstupu je, že knihovna DLL IL pro knihovnu neobsahuje vstupní body a nemůže být provedena.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-127">The main difference in built output is that the IL DLL for a library doesn't contain entry points and can't be executed.</span></span>

### <a name="msbuild"></a><span data-ttu-id="e9ae6-128">MSBuild</span><span class="sxs-lookup"><span data-stu-id="e9ae6-128">MSBuild</span></span>

<span data-ttu-id="e9ae6-129">`dotnet build` používá nástroj MSBuild k sestavení projektu, takže podporuje paralelní i přírůstkové sestavení.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-129">`dotnet build` uses MSBuild to build the project, so it supports both parallel and incremental builds.</span></span> <span data-ttu-id="e9ae6-130">Další informace naleznete v tématu [přírůstkové sestavení](/visualstudio/msbuild/incremental-builds).</span><span class="sxs-lookup"><span data-stu-id="e9ae6-130">For more information, see [Incremental Builds](/visualstudio/msbuild/incremental-builds).</span></span>

<span data-ttu-id="e9ae6-131">Kromě možností příkaz `dotnet build` přijímá možnosti nástroje MSBuild, jako je například `-p` pro nastavení vlastností nebo `-l` pro definování protokolovacího nástroje.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-131">In addition to its options, the `dotnet build` command accepts MSBuild options, such as `-p` for setting properties or `-l` to define a logger.</span></span> <span data-ttu-id="e9ae6-132">Další informace o těchto možnostech naleznete v tématu Referenční dokumentace k [příkazovému řádku MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="e9ae6-132">For more information about these options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="e9ae6-133">Případně můžete použít také příkaz [dotnet MSBuild](dotnet-msbuild.md) .</span><span class="sxs-lookup"><span data-stu-id="e9ae6-133">Or you can also use the [dotnet msbuild](dotnet-msbuild.md) command.</span></span>

<span data-ttu-id="e9ae6-134">Spuštění `dotnet build` je ekvivalentem `dotnet msbuild -restore -target:Build`.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-134">Running `dotnet build` is equivalent to `dotnet msbuild -restore -target:Build`.</span></span>

## <a name="arguments"></a><span data-ttu-id="e9ae6-135">Arguments</span><span class="sxs-lookup"><span data-stu-id="e9ae6-135">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="e9ae6-136">Soubor projektu nebo řešení, který se má sestavit</span><span class="sxs-lookup"><span data-stu-id="e9ae6-136">The project or solution file to build.</span></span> <span data-ttu-id="e9ae6-137">Pokud není zadán soubor projektu nebo řešení, nástroj MSBuild vyhledá v aktuálním pracovním adresáři soubor s příponou souboru, který končí buď *proj* nebo *sln* , a použije tento soubor.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-137">If a project or solution file isn't specified, MSBuild searches the current working directory for a file that has a file extension that ends in either *proj* or *sln* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="e9ae6-138">Možnosti</span><span class="sxs-lookup"><span data-stu-id="e9ae6-138">Options</span></span>

- **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="e9ae6-139">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-139">Defines the build configuration.</span></span> <span data-ttu-id="e9ae6-140">Výchozí hodnota pro většinu projektů je `Debug`, ale můžete přepsat nastavení konfigurace sestavení v projektu.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-140">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e9ae6-141">Zkompiluje pro konkrétní [rozhraní](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="e9ae6-141">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="e9ae6-142">Rozhraní musí být definováno v [souboru projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="e9ae6-142">The framework must be defined in the [project file](csproj.md).</span></span>

- **`--force`**

  <span data-ttu-id="e9ae6-143">Vynutí vyřešení všech závislostí i v případě, že bylo poslední obnovení úspěšné.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-143">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="e9ae6-144">Zadání tohoto příznaku je stejné jako odstranění souboru *Project. assets. JSON* .</span><span class="sxs-lookup"><span data-stu-id="e9ae6-144">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span> <span data-ttu-id="e9ae6-145">K dispozici od verze .NET Core 2,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-145">Available since .NET Core 2.0 SDK.</span></span>

- **`-h|--help`**

  <span data-ttu-id="e9ae6-146">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-146">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="e9ae6-147">Umožňuje zastavení příkazu zastavit a počkat na vstup nebo akci uživatele.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-147">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="e9ae6-148">Například k dokončení ověřování.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-148">For example, to complete authentication.</span></span> <span data-ttu-id="e9ae6-149">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-149">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="e9ae6-150">Ignoruje odkazy z projektu na projekt (P2P) a sestavuje pouze zadaný kořenový projekt.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-150">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

- **`--no-incremental`**

  <span data-ttu-id="e9ae6-151">Označí sestavení jako nebezpečná pro přírůstkové sestavení.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-151">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="e9ae6-152">Tento příznak vypne přírůstkovou kompilaci a vynutí čisté opětovné sestavení grafu závislostí projektu.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-152">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

- **`--no-restore`**

  <span data-ttu-id="e9ae6-153">Během sestavování neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-153">Doesn't execute an implicit restore during build.</span></span> <span data-ttu-id="e9ae6-154">K dispozici od verze .NET Core 2,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-154">Available since .NET Core 2.0 SDK.</span></span>

- **`--nologo`**

  <span data-ttu-id="e9ae6-155">Nezobrazuje úvodní nápis nebo zprávu o autorských právech.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-155">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="e9ae6-156">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-156">Available since .NET Core 3.0 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="e9ae6-157">Adresář, do kterého se umístí sestavené binární soubory.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-157">Directory in which to place the built binaries.</span></span> <span data-ttu-id="e9ae6-158">I když zadáte tuto možnost, musíte definovat `--framework`.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-158">You also need to define `--framework` when you specify this option.</span></span> <span data-ttu-id="e9ae6-159">Pokud není zadán, výchozí cesta je `./bin/<configuration>/<framework>/`.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-159">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="e9ae6-160">Určuje cílový modul runtime.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-160">Specifies the target runtime.</span></span> <span data-ttu-id="e9ae6-161">Seznam identifikátorů modulu runtime (identifikátorů RID) najdete v [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="e9ae6-161">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="e9ae6-162">Nastaví úroveň podrobností MSBuild.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-162">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="e9ae6-163">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-163">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="e9ae6-164">Výchozí hodnota je `minimal`.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-164">The default is `minimal`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="e9ae6-165">Nastaví hodnotu vlastnosti `$(VersionSuffix)`, která se má použít při sestavování projektu.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-165">Sets the value of the `$(VersionSuffix)` property to use when building the project.</span></span> <span data-ttu-id="e9ae6-166">To funguje pouze v případě, že vlastnost `$(Version)` není nastavena.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-166">This only works if the `$(Version)` property isn't set.</span></span> <span data-ttu-id="e9ae6-167">Pak `$(Version)` se nastaví na `$(VersionPrefix)` kombinované s `$(VersionSuffix)` oddělené pomlčkou.</span><span class="sxs-lookup"><span data-stu-id="e9ae6-167">Then, `$(Version)` is set to the `$(VersionPrefix)` combined with the `$(VersionSuffix)`, separated by a dash.</span></span>

## <a name="examples"></a><span data-ttu-id="e9ae6-168">Příklady</span><span class="sxs-lookup"><span data-stu-id="e9ae6-168">Examples</span></span>

- <span data-ttu-id="e9ae6-169">Sestavení projektu a jeho závislostí:</span><span class="sxs-lookup"><span data-stu-id="e9ae6-169">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet build
  ```

- <span data-ttu-id="e9ae6-170">Sestavení projektu a jeho závislostí pomocí konfigurace vydané verze:</span><span class="sxs-lookup"><span data-stu-id="e9ae6-170">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet build --configuration Release
  ```

- <span data-ttu-id="e9ae6-171">Sestavení projektu a jeho závislostí pro určitý modul runtime (v tomto příkladu Ubuntu 18,04):</span><span class="sxs-lookup"><span data-stu-id="e9ae6-171">Build a project and its dependencies for a specific runtime (in this example, Ubuntu 18.04):</span></span>

  ```dotnetcli
  dotnet build --runtime ubuntu.18.04-x64
  ```

- <span data-ttu-id="e9ae6-172">Sestavit projekt a použít zadaný zdroj balíčku NuGet během operace obnovení (.NET Core 2,0 SDK a novější verze):</span><span class="sxs-lookup"><span data-stu-id="e9ae6-172">Build the project and use the specified NuGet package source during the restore operation (.NET Core 2.0 SDK and later versions):</span></span>

  ```dotnetcli
  dotnet build --source c:\packages\mypackages
  ```

- <span data-ttu-id="e9ae6-173">Sestavte projekt a nastavte parametr Version 1.2.3.4 jako parametr sestavení pomocí možnosti `-p` [MSBuild](#msbuild):</span><span class="sxs-lookup"><span data-stu-id="e9ae6-173">Build the project and set version 1.2.3.4 as a build parameter using the `-p` [MSBuild option](#msbuild):</span></span>

  ```dotnetcli
  dotnet build -p:Version=1.2.3.4
  ```
