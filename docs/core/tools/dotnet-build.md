---
title: dotnet – příkaz sestavení
description: Příkaz dotnet Build vytvoří projekt a všechny jeho závislosti.
ms.date: 02/14/2020
ms.openlocfilehash: 6f33b449301f40949ff5dfe4077564344a9de8ec
ms.sourcegitcommit: c8c3e1c63a00b7d27f76f5e50ee6469e6bdc8987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87251163"
---
# <a name="dotnet-build"></a><span data-ttu-id="d1d45-103">dotnet build</span><span class="sxs-lookup"><span data-stu-id="d1d45-103">dotnet build</span></span>

<span data-ttu-id="d1d45-104">**Tento článek se týká:** ✔️ .NET Core 2. x SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="d1d45-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="d1d45-105">Název</span><span class="sxs-lookup"><span data-stu-id="d1d45-105">Name</span></span>

<span data-ttu-id="d1d45-106">`dotnet build`– Sestavení projektu a všech jeho závislostí.</span><span class="sxs-lookup"><span data-stu-id="d1d45-106">`dotnet build` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d1d45-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="d1d45-107">Synopsis</span></span>

```dotnetcli
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [-f|--framework <FRAMEWORK>] [--force] [--interactive] [--no-dependencies]
    [--no-incremental] [--no-restore] [--nologo] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [--source <SOURCE>]
    [-v|--verbosity <LEVEL>] [--version-suffix <VERSION_SUFFIX>]

dotnet build -h|--help
```

## <a name="description"></a><span data-ttu-id="d1d45-108">Popis</span><span class="sxs-lookup"><span data-stu-id="d1d45-108">Description</span></span>

<span data-ttu-id="d1d45-109">`dotnet build`Příkaz vytvoří projekt a jeho závislosti do sady binárních souborů.</span><span class="sxs-lookup"><span data-stu-id="d1d45-109">The `dotnet build` command builds the project and its dependencies into a set of binaries.</span></span> <span data-ttu-id="d1d45-110">Binární soubory obsahují kód projektu v souborech IL (Intermediate Language) s příponou *. dll* .</span><span class="sxs-lookup"><span data-stu-id="d1d45-110">The binaries include the project's code in Intermediate Language (IL) files with a *.dll* extension.</span></span>  <span data-ttu-id="d1d45-111">V závislosti na typu projektu a nastavení může být zahrnutých dalších souborů, například:</span><span class="sxs-lookup"><span data-stu-id="d1d45-111">Depending on the project type and settings, other files may be included, such as:</span></span>

- <span data-ttu-id="d1d45-112">Spustitelný soubor, který lze použít ke spuštění aplikace, pokud je typ projektu spustitelný soubor cílící na rozhraní .NET Core 3,0 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="d1d45-112">An executable that can be used to run the application, if the project type is an executable targeting .NET Core 3.0 or later.</span></span>
- <span data-ttu-id="d1d45-113">Soubory symbolů používané pro ladění s příponou *. pdb* .</span><span class="sxs-lookup"><span data-stu-id="d1d45-113">Symbol files used for debugging with a *.pdb* extension.</span></span>
- <span data-ttu-id="d1d45-114">*.deps.jsv* souboru, ve kterém jsou uvedeny závislosti aplikace nebo knihovny.</span><span class="sxs-lookup"><span data-stu-id="d1d45-114">A *.deps.json* file, which lists the dependencies of the application or library.</span></span>
- <span data-ttu-id="d1d45-115">*.runtimeconfig.jsv* souboru, který určuje sdílený modul runtime a jeho verzi pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d1d45-115">A *.runtimeconfig.json* file, which specifies the shared runtime and its version for an application.</span></span>
- <span data-ttu-id="d1d45-116">Další knihovny, na kterých projekt závisí (prostřednictvím odkazů na projekt nebo odkazů na balíček NuGet).</span><span class="sxs-lookup"><span data-stu-id="d1d45-116">Other libraries that the project depends on (via project references or NuGet package references).</span></span>

<span data-ttu-id="d1d45-117">U spustitelných projektů, které cílí na verze starší než .NET Core 3,0, se obvykle nekopírují závislosti knihoven z NuGet do výstupní složky.</span><span class="sxs-lookup"><span data-stu-id="d1d45-117">For executable projects targeting versions earlier than .NET Core 3.0, library dependencies from NuGet are typically NOT copied to the output folder.</span></span>  <span data-ttu-id="d1d45-118">Jsou vyřešeny ze složky globálních balíčků NuGet v době běhu.</span><span class="sxs-lookup"><span data-stu-id="d1d45-118">They're resolved from the NuGet global packages folder at run time.</span></span> <span data-ttu-id="d1d45-119">V takovém případě produkt `dotnet build` není připravený k přenosu na jiný počítač ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="d1d45-119">With that in mind, the product of `dotnet build` isn't ready to be transferred to another machine to run.</span></span> <span data-ttu-id="d1d45-120">Chcete-li vytvořit verzi aplikace, kterou lze nasadit, je nutné ji publikovat (například pomocí příkazu [dotnet Publish](dotnet-publish.md) ).</span><span class="sxs-lookup"><span data-stu-id="d1d45-120">To create a version of the application that can be deployed, you need to publish it (for example, with the [dotnet publish](dotnet-publish.md) command).</span></span> <span data-ttu-id="d1d45-121">Další informace najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="d1d45-121">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span>

<span data-ttu-id="d1d45-122">Pro spustitelné projekty cílené na .NET Core 3,0 a novější se závislosti knihoven zkopírují do výstupní složky.</span><span class="sxs-lookup"><span data-stu-id="d1d45-122">For executable projects targeting .NET Core 3.0 and later, library dependencies are copied to the output folder.</span></span> <span data-ttu-id="d1d45-123">To znamená, že pokud neexistují žádné jiné logiky specifické pro publikování (například webové projekty), měl by být výstup sestavení nasazený.</span><span class="sxs-lookup"><span data-stu-id="d1d45-123">This means that if there isn't any other publish-specific logic (such as Web projects have), the build output should be deployable.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="d1d45-124">Implicitní obnovení</span><span class="sxs-lookup"><span data-stu-id="d1d45-124">Implicit restore</span></span>

<span data-ttu-id="d1d45-125">Sestavování vyžaduje *project.assets.jsv* souboru, který obsahuje závislosti vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="d1d45-125">Building requires the *project.assets.json* file, which lists the dependencies of your application.</span></span> <span data-ttu-id="d1d45-126">Soubor se vytvoří při [`dotnet restore`](dotnet-restore.md) spuštění.</span><span class="sxs-lookup"><span data-stu-id="d1d45-126">The file is created when [`dotnet restore`](dotnet-restore.md) is executed.</span></span> <span data-ttu-id="d1d45-127">Bez zavedeného souboru prostředků nemůže nástroj překládat referenční sestavení, což má za následek chyby.</span><span class="sxs-lookup"><span data-stu-id="d1d45-127">Without the assets file in place, the tooling can't resolve reference assemblies, which results in errors.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

### <a name="executable-or-library-output"></a><span data-ttu-id="d1d45-128">Výstup spustitelného souboru nebo knihovny</span><span class="sxs-lookup"><span data-stu-id="d1d45-128">Executable or library output</span></span>

<span data-ttu-id="d1d45-129">Zda je projekt spustitelný nebo není určen `<OutputType>` vlastností v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="d1d45-129">Whether the project is executable or not is determined by the `<OutputType>` property in the project file.</span></span> <span data-ttu-id="d1d45-130">Následující příklad ukazuje projekt, který vytváří spustitelný kód:</span><span class="sxs-lookup"><span data-stu-id="d1d45-130">The following example shows a project that produces executable code:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="d1d45-131">Chcete-li vytvořit knihovnu, vynechejte `<OutputType>` vlastnost nebo změňte její hodnotu na `Library` .</span><span class="sxs-lookup"><span data-stu-id="d1d45-131">To produce a library, omit the `<OutputType>` property or change its value to `Library`.</span></span> <span data-ttu-id="d1d45-132">Knihovna DLL IL pro knihovnu neobsahuje vstupní body a nelze ji spustit.</span><span class="sxs-lookup"><span data-stu-id="d1d45-132">The IL DLL for a library doesn't contain entry points and can't be executed.</span></span>

### <a name="msbuild"></a><span data-ttu-id="d1d45-133">MSBuild</span><span class="sxs-lookup"><span data-stu-id="d1d45-133">MSBuild</span></span>

<span data-ttu-id="d1d45-134">`dotnet build`pomocí nástroje MSBuild sestaví projekt, takže podporuje paralelní i přírůstkové sestavení.</span><span class="sxs-lookup"><span data-stu-id="d1d45-134">`dotnet build` uses MSBuild to build the project, so it supports both parallel and incremental builds.</span></span> <span data-ttu-id="d1d45-135">Další informace naleznete v tématu [přírůstkové sestavení](/visualstudio/msbuild/incremental-builds).</span><span class="sxs-lookup"><span data-stu-id="d1d45-135">For more information, see [Incremental Builds](/visualstudio/msbuild/incremental-builds).</span></span>

<span data-ttu-id="d1d45-136">Kromě možností `dotnet build` příkaz akceptuje možnosti nástroje MSBuild, například `-p` pro nastavení vlastností nebo pro `-l` Definování protokolovacího nástroje.</span><span class="sxs-lookup"><span data-stu-id="d1d45-136">In addition to its options, the `dotnet build` command accepts MSBuild options, such as `-p` for setting properties or `-l` to define a logger.</span></span> <span data-ttu-id="d1d45-137">Další informace o těchto možnostech naleznete v tématu Referenční dokumentace k [příkazovému řádku MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="d1d45-137">For more information about these options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="d1d45-138">Případně můžete použít také příkaz [dotnet MSBuild](dotnet-msbuild.md) .</span><span class="sxs-lookup"><span data-stu-id="d1d45-138">Or you can also use the [dotnet msbuild](dotnet-msbuild.md) command.</span></span>

<span data-ttu-id="d1d45-139">Spuštění `dotnet build` je ekvivalentní se spuštěným `dotnet msbuild -restore` . výchozí podrobností výstupu se však liší.</span><span class="sxs-lookup"><span data-stu-id="d1d45-139">Running `dotnet build` is equivalent to running `dotnet msbuild -restore`; however, the default verbosity of the output is different.</span></span>

## <a name="arguments"></a><span data-ttu-id="d1d45-140">Arguments</span><span class="sxs-lookup"><span data-stu-id="d1d45-140">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="d1d45-141">Soubor projektu nebo řešení, který se má sestavit</span><span class="sxs-lookup"><span data-stu-id="d1d45-141">The project or solution file to build.</span></span> <span data-ttu-id="d1d45-142">Pokud není zadán soubor projektu nebo řešení, nástroj MSBuild vyhledá v aktuálním pracovním adresáři soubor s příponou souboru, který končí buď *proj* nebo *sln* , a použije tento soubor.</span><span class="sxs-lookup"><span data-stu-id="d1d45-142">If a project or solution file isn't specified, MSBuild searches the current working directory for a file that has a file extension that ends in either *proj* or *sln* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="d1d45-143">Možnosti</span><span class="sxs-lookup"><span data-stu-id="d1d45-143">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="d1d45-144">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="d1d45-144">Defines the build configuration.</span></span> <span data-ttu-id="d1d45-145">Výchozí hodnota pro většinu projektů je `Debug` , ale můžete přepsat nastavení konfigurace sestavení v projektu.</span><span class="sxs-lookup"><span data-stu-id="d1d45-145">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d1d45-146">Zkompiluje pro konkrétní [rozhraní](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="d1d45-146">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="d1d45-147">Rozhraní musí být definováno v [souboru projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="d1d45-147">The framework must be defined in the [project file](csproj.md).</span></span>

- **`--force`**

  <span data-ttu-id="d1d45-148">Vynutí vyřešení všech závislostí i v případě, že bylo poslední obnovení úspěšné.</span><span class="sxs-lookup"><span data-stu-id="d1d45-148">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="d1d45-149">Zadání tohoto příznaku je stejné jako odstranění *project.assets.jsv* souboru.</span><span class="sxs-lookup"><span data-stu-id="d1d45-149">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="d1d45-150">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="d1d45-150">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="d1d45-151">Umožňuje zastavení příkazu zastavit a počkat na vstup nebo akci uživatele.</span><span class="sxs-lookup"><span data-stu-id="d1d45-151">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="d1d45-152">Například k dokončení ověřování.</span><span class="sxs-lookup"><span data-stu-id="d1d45-152">For example, to complete authentication.</span></span> <span data-ttu-id="d1d45-153">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="d1d45-153">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="d1d45-154">Ignoruje odkazy z projektu na projekt (P2P) a sestavuje pouze zadaný kořenový projekt.</span><span class="sxs-lookup"><span data-stu-id="d1d45-154">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

- **`--no-incremental`**

  <span data-ttu-id="d1d45-155">Označí sestavení jako nebezpečná pro přírůstkové sestavení.</span><span class="sxs-lookup"><span data-stu-id="d1d45-155">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="d1d45-156">Tento příznak vypne přírůstkovou kompilaci a vynutí čisté opětovné sestavení grafu závislostí projektu.</span><span class="sxs-lookup"><span data-stu-id="d1d45-156">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

- **`--no-restore`**

  <span data-ttu-id="d1d45-157">Během sestavování neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="d1d45-157">Doesn't execute an implicit restore during build.</span></span>

- **`--nologo`**

  <span data-ttu-id="d1d45-158">Nezobrazuje úvodní nápis nebo zprávu o autorských právech.</span><span class="sxs-lookup"><span data-stu-id="d1d45-158">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="d1d45-159">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="d1d45-159">Available since .NET Core 3.0 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="d1d45-160">Adresář, do kterého se umístí sestavené binární soubory.</span><span class="sxs-lookup"><span data-stu-id="d1d45-160">Directory in which to place the built binaries.</span></span> <span data-ttu-id="d1d45-161">Pokud není zadaný, použije se výchozí cesta `./bin/<configuration>/<framework>/` .</span><span class="sxs-lookup"><span data-stu-id="d1d45-161">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="d1d45-162">Pro projekty s více cílovými rozhraními (prostřednictvím `TargetFrameworks` Vlastnosti) musíte definovat i `--framework` při zadání této možnosti.</span><span class="sxs-lookup"><span data-stu-id="d1d45-162">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="d1d45-163">Určuje cílový modul runtime.</span><span class="sxs-lookup"><span data-stu-id="d1d45-163">Specifies the target runtime.</span></span> <span data-ttu-id="d1d45-164">Seznam identifikátorů modulu runtime (identifikátorů RID) najdete v [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="d1d45-164">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

- **`--source <SOURCE>`**

  <span data-ttu-id="d1d45-165">Identifikátor URI zdroje balíčku NuGet, který má být použit během operace obnovení.</span><span class="sxs-lookup"><span data-stu-id="d1d45-165">The URI of the NuGet package source to use during the restore operation.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="d1d45-166">Nastaví úroveň podrobností MSBuild.</span><span class="sxs-lookup"><span data-stu-id="d1d45-166">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="d1d45-167">Povolené hodnoty jsou `q[uiet]` , `m[inimal]` ,, a `n[ormal]` `d[etailed]` `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="d1d45-167">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="d1d45-168">Výchozí formát je `minimal`.</span><span class="sxs-lookup"><span data-stu-id="d1d45-168">The default is `minimal`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="d1d45-169">Nastaví hodnotu `$(VersionSuffix)` vlastnosti, která má být použita při sestavování projektu.</span><span class="sxs-lookup"><span data-stu-id="d1d45-169">Sets the value of the `$(VersionSuffix)` property to use when building the project.</span></span> <span data-ttu-id="d1d45-170">To funguje pouze v případě, že `$(Version)` vlastnost není nastavena.</span><span class="sxs-lookup"><span data-stu-id="d1d45-170">This only works if the `$(Version)` property isn't set.</span></span> <span data-ttu-id="d1d45-171">Pak `$(Version)` je nastaven na `$(VersionPrefix)` kombinaci s `$(VersionSuffix)` oddělovačem odděleným pomlčkou.</span><span class="sxs-lookup"><span data-stu-id="d1d45-171">Then, `$(Version)` is set to the `$(VersionPrefix)` combined with the `$(VersionSuffix)`, separated by a dash.</span></span>

## <a name="examples"></a><span data-ttu-id="d1d45-172">Příklady</span><span class="sxs-lookup"><span data-stu-id="d1d45-172">Examples</span></span>

- <span data-ttu-id="d1d45-173">Sestavení projektu a jeho závislostí:</span><span class="sxs-lookup"><span data-stu-id="d1d45-173">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet build
  ```

- <span data-ttu-id="d1d45-174">Sestavení projektu a jeho závislostí pomocí konfigurace vydané verze:</span><span class="sxs-lookup"><span data-stu-id="d1d45-174">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet build --configuration Release
  ```

- <span data-ttu-id="d1d45-175">Sestavení projektu a jeho závislostí pro určitý modul runtime (v tomto příkladu Ubuntu 18,04):</span><span class="sxs-lookup"><span data-stu-id="d1d45-175">Build a project and its dependencies for a specific runtime (in this example, Ubuntu 18.04):</span></span>

  ```dotnetcli
  dotnet build --runtime ubuntu.18.04-x64
  ```

- <span data-ttu-id="d1d45-176">Sestavit projekt a použít zadaný zdroj balíčku NuGet během operace obnovení (.NET Core 2,0 SDK a novější verze):</span><span class="sxs-lookup"><span data-stu-id="d1d45-176">Build the project and use the specified NuGet package source during the restore operation (.NET Core 2.0 SDK and later versions):</span></span>

  ```dotnetcli
  dotnet build --source c:\packages\mypackages
  ```

- <span data-ttu-id="d1d45-177">Sestavte projekt a nastavte parametr Version 1.2.3.4 jako parametr sestavení pomocí `-p` [Možnosti MSBuild](#msbuild):</span><span class="sxs-lookup"><span data-stu-id="d1d45-177">Build the project and set version 1.2.3.4 as a build parameter using the `-p` [MSBuild option](#msbuild):</span></span>

  ```dotnetcli
  dotnet build -p:Version=1.2.3.4
  ```
