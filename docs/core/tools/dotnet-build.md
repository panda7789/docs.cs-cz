---
title: dotnet – příkaz sestavení
description: Příkaz dotnet Build vytvoří projekt a všechny jeho závislosti.
ms.date: 10/14/2019
ms.openlocfilehash: ec37d82c9e22a59acf7617f80a7491c0bcab89c9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734311"
---
# <a name="dotnet-build"></a><span data-ttu-id="9b216-103">dotnet build</span><span class="sxs-lookup"><span data-stu-id="9b216-103">dotnet build</span></span>

<span data-ttu-id="9b216-104">**Tento článek se týká:** ✔️ .NET Core 1. x SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="9b216-104">**This article applies to:** ✔️ .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="9b216-105">Name</span><span class="sxs-lookup"><span data-stu-id="9b216-105">Name</span></span>

<span data-ttu-id="9b216-106">`dotnet build` – sestavení projektu a všech jeho závislostí.</span><span class="sxs-lookup"><span data-stu-id="9b216-106">`dotnet build` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9b216-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="9b216-107">Synopsis</span></span>

```dotnetcli
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--force]
    [--interactive] [--no-dependencies] [--no-incremental] [--no-restore] [--nologo]
    [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```

## <a name="description"></a><span data-ttu-id="9b216-108">Popis</span><span class="sxs-lookup"><span data-stu-id="9b216-108">Description</span></span>

<span data-ttu-id="9b216-109">Příkaz `dotnet build` vytvoří projekt a jeho závislosti do sady binárních souborů.</span><span class="sxs-lookup"><span data-stu-id="9b216-109">The `dotnet build` command builds the project and its dependencies into a set of binaries.</span></span> <span data-ttu-id="9b216-110">Binární soubory obsahují kód projektu v souborech IL (Intermediate Language) s příponou *. dll* .</span><span class="sxs-lookup"><span data-stu-id="9b216-110">The binaries include the project's code in Intermediate Language (IL) files with a *.dll* extension.</span></span>  <span data-ttu-id="9b216-111">V závislosti na typu projektu a nastavení může být zahrnutých dalších souborů, například:</span><span class="sxs-lookup"><span data-stu-id="9b216-111">Depending on the project type and settings, other files may be included, such as:</span></span>

- <span data-ttu-id="9b216-112">Spustitelný soubor, který lze použít ke spuštění aplikace, pokud je typ projektu spustitelný soubor cílící na rozhraní .NET Core 3,0 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="9b216-112">An executable that can be used to run the application, if the project type is an executable targeting .NET Core 3.0 or later.</span></span>
- <span data-ttu-id="9b216-113">Soubory symbolů používané pro ladění s příponou *. pdb* .</span><span class="sxs-lookup"><span data-stu-id="9b216-113">Symbol files used for debugging with a *.pdb* extension.</span></span>
- <span data-ttu-id="9b216-114">Soubor *. DEPS. JSON* , který obsahuje závislosti aplikace nebo knihovny.</span><span class="sxs-lookup"><span data-stu-id="9b216-114">A *.deps.json* file, which lists the dependencies of the application or library.</span></span>
- <span data-ttu-id="9b216-115">Soubor *. runtimeconfig. JSON* , který určuje sdílený modul runtime a jeho verzi pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9b216-115">A *.runtimeconfig.json* file, which specifies the shared runtime and its version for an application.</span></span>
- <span data-ttu-id="9b216-116">Další knihovny, na kterých projekt závisí (prostřednictvím odkazů na projekt nebo odkazů na balíček NuGet).</span><span class="sxs-lookup"><span data-stu-id="9b216-116">Other libraries that the project depends on (via project references or NuGet package references).</span></span>

<span data-ttu-id="9b216-117">U spustitelných projektů, které cílí na verze starší než .NET Core 3,0, se obvykle nekopírují závislosti knihoven z NuGet do výstupní složky.</span><span class="sxs-lookup"><span data-stu-id="9b216-117">For executable projects targeting versions earlier than .NET Core 3.0, library dependencies from NuGet are typically NOT copied to the output folder.</span></span>  <span data-ttu-id="9b216-118">Jsou vyřešeny ze složky globálních balíčků NuGet v době běhu.</span><span class="sxs-lookup"><span data-stu-id="9b216-118">They're resolved from the NuGet global packages folder at run time.</span></span> <span data-ttu-id="9b216-119">V takovém případě produkt `dotnet build` není připravený k přenosu na jiný počítač ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="9b216-119">With that in mind, the product of `dotnet build` isn't ready to be transferred to another machine to run.</span></span> <span data-ttu-id="9b216-120">Chcete-li vytvořit verzi aplikace, kterou lze nasadit, je nutné ji publikovat (například pomocí příkazu [dotnet Publish](dotnet-publish.md) ).</span><span class="sxs-lookup"><span data-stu-id="9b216-120">To create a version of the application that can be deployed, you need to publish it (for example, with the [dotnet publish](dotnet-publish.md) command).</span></span> <span data-ttu-id="9b216-121">Další informace najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="9b216-121">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span>

<span data-ttu-id="9b216-122">Pro spustitelné projekty cílené na .NET Core 3,0 a novější se závislosti knihoven zkopírují do výstupní složky.</span><span class="sxs-lookup"><span data-stu-id="9b216-122">For executable projects targeting .NET Core 3.0 and later, library dependencies are copied to the output folder.</span></span> <span data-ttu-id="9b216-123">To znamená, že pokud neexistují žádné jiné logiky specifické pro publikování (například webové projekty), měl by být výstup sestavení nasazený.</span><span class="sxs-lookup"><span data-stu-id="9b216-123">This means that if there isn't any other publish-specific logic (such as Web projects have), the build output should be deployable.</span></span>

<span data-ttu-id="9b216-124">Sestavování vyžaduje soubor *Project. assets. JSON* , který obsahuje závislosti vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="9b216-124">Building requires the *project.assets.json* file, which lists the dependencies of your application.</span></span> <span data-ttu-id="9b216-125">Soubor se vytvoří, když se spustí [`dotnet restore`](dotnet-restore.md) .</span><span class="sxs-lookup"><span data-stu-id="9b216-125">The file is created when [`dotnet restore`](dotnet-restore.md) is executed.</span></span> <span data-ttu-id="9b216-126">Bez zavedeného souboru prostředků nemůže nástroj překládat referenční sestavení, což má za následek chyby.</span><span class="sxs-lookup"><span data-stu-id="9b216-126">Without the assets file in place, the tooling can't resolve reference assemblies, which results in errors.</span></span> <span data-ttu-id="9b216-127">Pomocí sady .NET Core 1. x SDK jste před spuštěním `dotnet build`museli explicitně spustit `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="9b216-127">With .NET Core 1.x SDK, you needed to explicitly run `dotnet restore` before running `dotnet build`.</span></span> <span data-ttu-id="9b216-128">Počínaje rozhraním .NET Core 2,0 SDK se `dotnet restore` spouští implicitně při spuštění `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="9b216-128">Starting with .NET Core 2.0 SDK, `dotnet restore` runs implicitly when you run `dotnet build`.</span></span> <span data-ttu-id="9b216-129">Pokud chcete zakázat implicitní obnovení při spuštění příkazu sestavení, můžete předat možnost `--no-restore`.</span><span class="sxs-lookup"><span data-stu-id="9b216-129">If you want to disable implicit restore when running the build command, you can pass the `--no-restore` option.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

<span data-ttu-id="9b216-130">Zda je projekt spustitelný nebo není určen vlastností `<OutputType>` v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="9b216-130">Whether the project is executable or not is determined by the `<OutputType>` property in the project file.</span></span> <span data-ttu-id="9b216-131">Následující příklad ukazuje projekt, který vytváří spustitelný kód:</span><span class="sxs-lookup"><span data-stu-id="9b216-131">The following example shows a project that produces executable code:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="9b216-132">Chcete-li vytvořit knihovnu, vynechejte vlastnost `<OutputType>` nebo změňte její hodnotu na `Library`.</span><span class="sxs-lookup"><span data-stu-id="9b216-132">To produce a library, omit the `<OutputType>` property or change its value to `Library`.</span></span> <span data-ttu-id="9b216-133">Knihovna DLL IL pro knihovnu neobsahuje vstupní body a nelze ji spustit.</span><span class="sxs-lookup"><span data-stu-id="9b216-133">The IL DLL for a library doesn't contain entry points and can't be executed.</span></span>

### <a name="msbuild"></a><span data-ttu-id="9b216-134">MSBuild</span><span class="sxs-lookup"><span data-stu-id="9b216-134">MSBuild</span></span>

<span data-ttu-id="9b216-135">`dotnet build` používá nástroj MSBuild k sestavení projektu, takže podporuje paralelní i přírůstkové sestavení.</span><span class="sxs-lookup"><span data-stu-id="9b216-135">`dotnet build` uses MSBuild to build the project, so it supports both parallel and incremental builds.</span></span> <span data-ttu-id="9b216-136">Další informace naleznete v tématu [přírůstkové sestavení](/visualstudio/msbuild/incremental-builds).</span><span class="sxs-lookup"><span data-stu-id="9b216-136">For more information, see [Incremental Builds](/visualstudio/msbuild/incremental-builds).</span></span>

<span data-ttu-id="9b216-137">Kromě možností příkaz `dotnet build` přijímá možnosti nástroje MSBuild, jako je například `-p` pro nastavení vlastností nebo `-l` k definování protokolovacího nástroje.</span><span class="sxs-lookup"><span data-stu-id="9b216-137">In addition to its options, the `dotnet build` command accepts MSBuild options, such as `-p` for setting properties or `-l` to define a logger.</span></span> <span data-ttu-id="9b216-138">Další informace o těchto možnostech naleznete v tématu Referenční dokumentace k [příkazovému řádku MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="9b216-138">For more information about these options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="9b216-139">Případně můžete použít také příkaz [dotnet MSBuild](dotnet-msbuild.md) .</span><span class="sxs-lookup"><span data-stu-id="9b216-139">Or you can also use the [dotnet msbuild](dotnet-msbuild.md) command.</span></span>

<span data-ttu-id="9b216-140">Spuštění `dotnet build` je ekvivalentem spuštění `dotnet msbuild -restore`; výchozí podrobnost výstupu se ale liší.</span><span class="sxs-lookup"><span data-stu-id="9b216-140">Running `dotnet build` is equivalent to running `dotnet msbuild -restore`; however, the default verbosity of the output is different.</span></span>

## <a name="arguments"></a><span data-ttu-id="9b216-141">Arguments</span><span class="sxs-lookup"><span data-stu-id="9b216-141">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="9b216-142">Soubor projektu nebo řešení, který se má sestavit</span><span class="sxs-lookup"><span data-stu-id="9b216-142">The project or solution file to build.</span></span> <span data-ttu-id="9b216-143">Pokud není zadán soubor projektu nebo řešení, nástroj MSBuild vyhledá v aktuálním pracovním adresáři soubor s příponou souboru, který končí buď *proj* nebo *sln* , a použije tento soubor.</span><span class="sxs-lookup"><span data-stu-id="9b216-143">If a project or solution file isn't specified, MSBuild searches the current working directory for a file that has a file extension that ends in either *proj* or *sln* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="9b216-144">Možnosti</span><span class="sxs-lookup"><span data-stu-id="9b216-144">Options</span></span>

- **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="9b216-145">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="9b216-145">Defines the build configuration.</span></span> <span data-ttu-id="9b216-146">Výchozí hodnota pro většinu projektů je `Debug`, ale můžete přepsat nastavení konfigurace sestavení v projektu.</span><span class="sxs-lookup"><span data-stu-id="9b216-146">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="9b216-147">Zkompiluje pro konkrétní [rozhraní](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="9b216-147">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="9b216-148">Rozhraní musí být definováno v [souboru projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="9b216-148">The framework must be defined in the [project file](csproj.md).</span></span>

- **`--force`**

  <span data-ttu-id="9b216-149">Vynutí vyřešení všech závislostí i v případě, že bylo poslední obnovení úspěšné.</span><span class="sxs-lookup"><span data-stu-id="9b216-149">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="9b216-150">Zadání tohoto příznaku je stejné jako odstranění souboru *Project. assets. JSON* .</span><span class="sxs-lookup"><span data-stu-id="9b216-150">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span> <span data-ttu-id="9b216-151">K dispozici od verze .NET Core 2,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="9b216-151">Available since .NET Core 2.0 SDK.</span></span>

- **`-h|--help`**

  <span data-ttu-id="9b216-152">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="9b216-152">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="9b216-153">Umožňuje zastavení příkazu zastavit a počkat na vstup nebo akci uživatele.</span><span class="sxs-lookup"><span data-stu-id="9b216-153">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="9b216-154">Například k dokončení ověřování.</span><span class="sxs-lookup"><span data-stu-id="9b216-154">For example, to complete authentication.</span></span> <span data-ttu-id="9b216-155">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="9b216-155">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="9b216-156">Ignoruje odkazy z projektu na projekt (P2P) a sestavuje pouze zadaný kořenový projekt.</span><span class="sxs-lookup"><span data-stu-id="9b216-156">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

- **`--no-incremental`**

  <span data-ttu-id="9b216-157">Označí sestavení jako nebezpečná pro přírůstkové sestavení.</span><span class="sxs-lookup"><span data-stu-id="9b216-157">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="9b216-158">Tento příznak vypne přírůstkovou kompilaci a vynutí čisté opětovné sestavení grafu závislostí projektu.</span><span class="sxs-lookup"><span data-stu-id="9b216-158">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

- **`--no-restore`**

  <span data-ttu-id="9b216-159">Během sestavování neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="9b216-159">Doesn't execute an implicit restore during build.</span></span> <span data-ttu-id="9b216-160">K dispozici od verze .NET Core 2,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="9b216-160">Available since .NET Core 2.0 SDK.</span></span>

- **`--nologo`**

  <span data-ttu-id="9b216-161">Nezobrazuje úvodní nápis nebo zprávu o autorských právech.</span><span class="sxs-lookup"><span data-stu-id="9b216-161">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="9b216-162">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="9b216-162">Available since .NET Core 3.0 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="9b216-163">Adresář, do kterého se umístí sestavené binární soubory.</span><span class="sxs-lookup"><span data-stu-id="9b216-163">Directory in which to place the built binaries.</span></span> <span data-ttu-id="9b216-164">Pokud není zadaný, použije se výchozí cesta `./bin/<configuration>/<framework>/`.</span><span class="sxs-lookup"><span data-stu-id="9b216-164">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="9b216-165">Pro projekty s více cílovými rozhraními (prostřednictvím vlastnosti `TargetFrameworks`) je také potřeba definovat `--framework` při zadání této možnosti.</span><span class="sxs-lookup"><span data-stu-id="9b216-165">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="9b216-166">Určuje cílový modul runtime.</span><span class="sxs-lookup"><span data-stu-id="9b216-166">Specifies the target runtime.</span></span> <span data-ttu-id="9b216-167">Seznam identifikátorů modulu runtime (identifikátorů RID) najdete v [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="9b216-167">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="9b216-168">Nastaví úroveň podrobností MSBuild.</span><span class="sxs-lookup"><span data-stu-id="9b216-168">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="9b216-169">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="9b216-169">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="9b216-170">Výchozí hodnota je `minimal`.</span><span class="sxs-lookup"><span data-stu-id="9b216-170">The default is `minimal`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="9b216-171">Nastaví hodnotu vlastnosti `$(VersionSuffix)`, která se má použít při sestavování projektu.</span><span class="sxs-lookup"><span data-stu-id="9b216-171">Sets the value of the `$(VersionSuffix)` property to use when building the project.</span></span> <span data-ttu-id="9b216-172">To funguje pouze v případě, že vlastnost `$(Version)` není nastavena.</span><span class="sxs-lookup"><span data-stu-id="9b216-172">This only works if the `$(Version)` property isn't set.</span></span> <span data-ttu-id="9b216-173">Pak je `$(Version)` nastaveno na `$(VersionPrefix)` kombinované s `$(VersionSuffix)`, oddělené pomlčkou.</span><span class="sxs-lookup"><span data-stu-id="9b216-173">Then, `$(Version)` is set to the `$(VersionPrefix)` combined with the `$(VersionSuffix)`, separated by a dash.</span></span>

## <a name="examples"></a><span data-ttu-id="9b216-174">Příklady</span><span class="sxs-lookup"><span data-stu-id="9b216-174">Examples</span></span>

- <span data-ttu-id="9b216-175">Sestavení projektu a jeho závislostí:</span><span class="sxs-lookup"><span data-stu-id="9b216-175">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet build
  ```

- <span data-ttu-id="9b216-176">Sestavení projektu a jeho závislostí pomocí konfigurace vydané verze:</span><span class="sxs-lookup"><span data-stu-id="9b216-176">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet build --configuration Release
  ```

- <span data-ttu-id="9b216-177">Sestavení projektu a jeho závislostí pro určitý modul runtime (v tomto příkladu Ubuntu 18,04):</span><span class="sxs-lookup"><span data-stu-id="9b216-177">Build a project and its dependencies for a specific runtime (in this example, Ubuntu 18.04):</span></span>

  ```dotnetcli
  dotnet build --runtime ubuntu.18.04-x64
  ```

- <span data-ttu-id="9b216-178">Sestavit projekt a použít zadaný zdroj balíčku NuGet během operace obnovení (.NET Core 2,0 SDK a novější verze):</span><span class="sxs-lookup"><span data-stu-id="9b216-178">Build the project and use the specified NuGet package source during the restore operation (.NET Core 2.0 SDK and later versions):</span></span>

  ```dotnetcli
  dotnet build --source c:\packages\mypackages
  ```

- <span data-ttu-id="9b216-179">Sestavte projekt a nastavte parametr Version 1.2.3.4 jako parametr sestavení pomocí [možnosti `-p` MSBuild](#msbuild):</span><span class="sxs-lookup"><span data-stu-id="9b216-179">Build the project and set version 1.2.3.4 as a build parameter using the `-p` [MSBuild option](#msbuild):</span></span>

  ```dotnetcli
  dotnet build -p:Version=1.2.3.4
  ```
