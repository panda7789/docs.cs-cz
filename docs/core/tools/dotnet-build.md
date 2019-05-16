---
title: příkaz DotNet sestavení
description: Dotnet sestavení příkaz sestavení projektu a všechny jeho závislosti.
ms.date: 04/24/2019
ms.openlocfilehash: 6564aacbe520797b47095929cfe72c6b180b99a7
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632138"
---
# <a name="dotnet-build"></a><span data-ttu-id="cb32c-103">DotNet sestavení</span><span class="sxs-lookup"><span data-stu-id="cb32c-103">dotnet build</span></span>

<span data-ttu-id="cb32c-104">**Tento článek se týká: ✓** .NET Core 1.x sady SDK a novějších verzích</span><span class="sxs-lookup"><span data-stu-id="cb32c-104">**This article applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="cb32c-105">Name</span><span class="sxs-lookup"><span data-stu-id="cb32c-105">Name</span></span>

<span data-ttu-id="cb32c-106">`dotnet build` -Sestavení projektu a všechny jeho závislosti.</span><span class="sxs-lookup"><span data-stu-id="cb32c-106">`dotnet build` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="cb32c-107">Souhrn</span><span class="sxs-lookup"><span data-stu-id="cb32c-107">Synopsis</span></span>

```
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--force] [--interactive] [--no-dependencies]
    [--no-incremental] [--nologo] [--no-restore] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```

## <a name="description"></a><span data-ttu-id="cb32c-108">Popis</span><span class="sxs-lookup"><span data-stu-id="cb32c-108">Description</span></span>

<span data-ttu-id="cb32c-109">`dotnet build` Příkaz sestaví projekt a jeho závislosti do sady binární soubory.</span><span class="sxs-lookup"><span data-stu-id="cb32c-109">The `dotnet build` command builds the project and its dependencies into a set of binaries.</span></span> <span data-ttu-id="cb32c-110">Binární soubory zahrnují projektu kódu v souborech Intermediate Language (IL) s *.dll* rozšíření a symbol soubory používané pro ladění v sadě *PDB* rozšíření.</span><span class="sxs-lookup"><span data-stu-id="cb32c-110">The binaries include the project's code in Intermediate Language (IL) files with a *.dll* extension and symbol files used for debugging with a *.pdb* extension.</span></span> <span data-ttu-id="cb32c-111">Soubor JSON závislosti (*\*. deps.json*) je vytvořen, který obsahuje seznam závislostí aplikace.</span><span class="sxs-lookup"><span data-stu-id="cb32c-111">A dependencies JSON file (*\*.deps.json*) is produced that lists the dependencies of the application.</span></span> <span data-ttu-id="cb32c-112">A  *\*. runtimeconfig.json* je vytvořen soubor, který určuje sdílený modul runtime a jeho verze pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="cb32c-112">A *\*.runtimeconfig.json* file is produced, which specifies the shared runtime and its version for the application.</span></span>

<span data-ttu-id="cb32c-113">Obsahuje-li projekt závislostí třetích stran, jako jsou knihovny z Nugetu, že vyřešit z mezipaměti NuGet a nejsou k dispozici s sestavení výstupu projektu.</span><span class="sxs-lookup"><span data-stu-id="cb32c-113">If the project has third-party dependencies, such as libraries from NuGet, they're resolved from the NuGet cache and aren't available with the project's built output.</span></span> <span data-ttu-id="cb32c-114">Skutečností, součin `dotnet build` není připravené k převedení do jiného počítače ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="cb32c-114">With that in mind, the product of `dotnet build` isn't ready to be transferred to another machine to run.</span></span> <span data-ttu-id="cb32c-115">To se liší od chování rozhraní .NET Framework ve které vytváření spustitelného souboru projektu (aplikace) vytvoří výstup, který je spustitelný na libovolný počítač, ve kterém je nainstalováno rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cb32c-115">This is in contrast to the behavior of the .NET Framework in which building an executable project (an application) produces output that's runnable on any machine where the .NET Framework is installed.</span></span> <span data-ttu-id="cb32c-116">Pokud chcete, aby fungují na podobném principu s .NET Core, budete muset použít [dotnet publikovat](dotnet-publish.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="cb32c-116">To have a similar experience with .NET Core, you need to use the [dotnet publish](dotnet-publish.md) command.</span></span> <span data-ttu-id="cb32c-117">Další informace najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="cb32c-117">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span>

<span data-ttu-id="cb32c-118">Vytváření vyžaduje *project.assets.json* soubor, který obsahuje seznam závislostí vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="cb32c-118">Building requires the *project.assets.json* file, which lists the dependencies of your application.</span></span> <span data-ttu-id="cb32c-119">Soubor je vytvořen při [ `dotnet restore` ](dotnet-restore.md) provádí.</span><span class="sxs-lookup"><span data-stu-id="cb32c-119">The file is created when [`dotnet restore`](dotnet-restore.md) is executed.</span></span> <span data-ttu-id="cb32c-120">Bez souboru prostředků v místě nelze nástrojů vyřešit referenční sestavení, což má za následek chyby.</span><span class="sxs-lookup"><span data-stu-id="cb32c-120">Without the assets file in place, the tooling can't resolve reference assemblies, which results in errors.</span></span> <span data-ttu-id="cb32c-121">S .NET Core 1.x SDK potřebné ke spuštění explicitně `dotnet restore` dřív, než spustíte `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="cb32c-121">With .NET Core 1.x SDK, you needed to explicitly run the `dotnet restore` before running `dotnet build`.</span></span> <span data-ttu-id="cb32c-122">Počínaje .NET Core 2.0 SDK `dotnet restore` se implicitně spouští při spuštění `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="cb32c-122">Starting with .NET Core 2.0 SDK, `dotnet restore` runs implicitly when you run `dotnet build`.</span></span> <span data-ttu-id="cb32c-123">Pokud chcete zakázat implicitní obnovení při spuštění příkazu k sestavení, lze předat `--no-restore` možnost.</span><span class="sxs-lookup"><span data-stu-id="cb32c-123">If you want to disable implicit restore when running the build command, you can pass the `--no-restore` option.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

<span data-ttu-id="cb32c-124">Určuje, zda je projekt spustitelné nebo ne je určeno `<OutputType>` vlastnost v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="cb32c-124">Whether the project is executable or not is determined by the `<OutputType>` property in the project file.</span></span> <span data-ttu-id="cb32c-125">Následující příklad ukazuje projekt, který vytvoří spustitelný kód:</span><span class="sxs-lookup"><span data-stu-id="cb32c-125">The following example shows a project that produces executable code:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="cb32c-126">K vytvoření knihovny vynechat, nechte `<OutputType>` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="cb32c-126">To produce a library, omit the `<OutputType>` property.</span></span> <span data-ttu-id="cb32c-127">Hlavní rozdíl v sestavení výstupu je, že knihovna DLL IL pro knihovnu neobsahuje vstupní body a nelze ho provést.</span><span class="sxs-lookup"><span data-stu-id="cb32c-127">The main difference in built output is that the IL DLL for a library doesn't contain entry points and can't be executed.</span></span>

### <a name="msbuild"></a><span data-ttu-id="cb32c-128">MSBuild</span><span class="sxs-lookup"><span data-stu-id="cb32c-128">MSBuild</span></span>

<span data-ttu-id="cb32c-129">`dotnet build` používá MSBuild k sestavení projektu, takže podporuje paralelní i přírůstkové sestavení.</span><span class="sxs-lookup"><span data-stu-id="cb32c-129">`dotnet build` uses MSBuild to build the project, so it supports both parallel and incremental builds.</span></span> <span data-ttu-id="cb32c-130">Další informace najdete v tématu [přírůstková sestavení](/visualstudio/msbuild/incremental-builds).</span><span class="sxs-lookup"><span data-stu-id="cb32c-130">For more information, see [Incremental Builds](/visualstudio/msbuild/incremental-builds).</span></span>

<span data-ttu-id="cb32c-131">Kromě jeho možností `dotnet build` příkaz přijímá MSBuild možnosti, jako například `-p` pro nastavení vlastnosti nebo `-l` k definování protokolovač.</span><span class="sxs-lookup"><span data-stu-id="cb32c-131">In addition to its options, the `dotnet build` command accepts MSBuild options, such as `-p` for setting properties or `-l` to define a logger.</span></span> <span data-ttu-id="cb32c-132">Další informace o těchto možnostech najdete v tématu [MSBuild Reference k příkazovému řádku](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="cb32c-132">For more information about these options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="cb32c-133">Nebo můžete použít také [dotnet msbuild](dotnet-msbuild.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="cb32c-133">Or you can also use the [dotnet msbuild](dotnet-msbuild.md) command.</span></span>

<span data-ttu-id="cb32c-134">Spuštění `dotnet build` je ekvivalentní `dotnet msbuild -restore -target:Build`.</span><span class="sxs-lookup"><span data-stu-id="cb32c-134">Running `dotnet build` is equivalent to `dotnet msbuild -restore -target:Build`.</span></span>

## <a name="arguments"></a><span data-ttu-id="cb32c-135">Arguments</span><span class="sxs-lookup"><span data-stu-id="cb32c-135">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="cb32c-136">Soubor projektu nebo řešení pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="cb32c-136">The project or solution file to build.</span></span> <span data-ttu-id="cb32c-137">Pokud není zadán soubor projektu nebo řešení, MSBuild vyhledá aktuální pracovní adresář pro soubor, který má příponu souboru, který končí *proj* nebo *sln* a použije tento soubor.</span><span class="sxs-lookup"><span data-stu-id="cb32c-137">If a project or solution file isn't specified, MSBuild searches the current working directory for a file that has a file extension that ends in either *proj* or *sln* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="cb32c-138">Možnosti</span><span class="sxs-lookup"><span data-stu-id="cb32c-138">Options</span></span>

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="cb32c-139">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="cb32c-139">Defines the build configuration.</span></span> <span data-ttu-id="cb32c-140">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="cb32c-140">The default value is `Debug`.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="cb32c-141">Zkompiluje pro konkrétní [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="cb32c-141">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="cb32c-142">Rozhraní musí být definován v [soubor projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="cb32c-142">The framework must be defined in the [project file](csproj.md).</span></span>

* **`--force`**

  <span data-ttu-id="cb32c-143">Způsobí, že všechny závislosti vyřešit i v případě, že poslední obnovení bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="cb32c-143">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="cb32c-144">Zadání tohoto příznaku je stejný jako odstranění *project.assets.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="cb32c-144">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span> <span data-ttu-id="cb32c-145">Tato možnost je k dispozici, protože .NET Core 2.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="cb32c-145">Available since .NET Core 2.0 SDK.</span></span>

* **`-h|--help`**

  <span data-ttu-id="cb32c-146">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="cb32c-146">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="cb32c-147">Povoluje příkazu zastavit a počkat na vstup uživatele nebo akce.</span><span class="sxs-lookup"><span data-stu-id="cb32c-147">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="cb32c-148">Například k dokončení ověřování.</span><span class="sxs-lookup"><span data-stu-id="cb32c-148">For example, to complete authentication.</span></span> <span data-ttu-id="cb32c-149">Tato možnost je k dispozici, protože .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="cb32c-149">Available since .NET Core 3.0 SDK.</span></span>

* **`--no-dependencies`**

  <span data-ttu-id="cb32c-150">Pouze sestavení projektu zadaný kořenový a ignoruje odkazy typu projekt projekt (P2P).</span><span class="sxs-lookup"><span data-stu-id="cb32c-150">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

* **`--no-incremental`**

  <span data-ttu-id="cb32c-151">Označí sestavení jako problematické pro přírůstkové sestavení.</span><span class="sxs-lookup"><span data-stu-id="cb32c-151">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="cb32c-152">Tento příznak vypne přírůstková kompilace a vynutí opětovné čisté sestavení grafu závislostí projektu.</span><span class="sxs-lookup"><span data-stu-id="cb32c-152">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

* **`--no-logo`**

  <span data-ttu-id="cb32c-153">Nezobrazí úvodní nápis a zprávu o autorských právech.</span><span class="sxs-lookup"><span data-stu-id="cb32c-153">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="cb32c-154">Tato možnost je k dispozici, protože .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="cb32c-154">Available since .NET Core 3.0 SDK.</span></span>

* **`--no-restore`**

  <span data-ttu-id="cb32c-155">Neprovede implicitní obnovení během sestavování.</span><span class="sxs-lookup"><span data-stu-id="cb32c-155">Doesn't execute an implicit restore during build.</span></span> <span data-ttu-id="cb32c-156">Tato možnost je k dispozici, protože .NET Core 2.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="cb32c-156">Available since .NET Core 2.0 SDK.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="cb32c-157">Adresář, do kterého chcete sestavené binární soubory.</span><span class="sxs-lookup"><span data-stu-id="cb32c-157">Directory in which to place the built binaries.</span></span> <span data-ttu-id="cb32c-158">Budete také muset definovat `--framework` při zadání této možnosti.</span><span class="sxs-lookup"><span data-stu-id="cb32c-158">You also need to define `--framework` when you specify this option.</span></span> <span data-ttu-id="cb32c-159">Pokud není zadán, výchozí cesta je `./bin/<configuration>/<framework>/`.</span><span class="sxs-lookup"><span data-stu-id="cb32c-159">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="cb32c-160">Určuje cílový modul runtime.</span><span class="sxs-lookup"><span data-stu-id="cb32c-160">Specifies the target runtime.</span></span> <span data-ttu-id="cb32c-161">Seznam identifikátorů modulů Runtime (RID), najdete v článku [katalog identifikátorů RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="cb32c-161">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="cb32c-162">Nastaví úroveň podrobností MSBuild.</span><span class="sxs-lookup"><span data-stu-id="cb32c-162">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="cb32c-163">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="cb32c-163">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="cb32c-164">Výchozí hodnota je `minimal`.</span><span class="sxs-lookup"><span data-stu-id="cb32c-164">The default is `minimal`.</span></span>

* **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="cb32c-165">Nastaví hodnotu vlastnosti `$(VersionSuffix)` vlastnost použít při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="cb32c-165">Sets the value of the `$(VersionSuffix)` property to use when building the project.</span></span> <span data-ttu-id="cb32c-166">Toto funguje, pouze pokud `$(Version)` není nastavena vlastnost.</span><span class="sxs-lookup"><span data-stu-id="cb32c-166">This only works if the `$(Version)` property isn't set.</span></span> <span data-ttu-id="cb32c-167">Potom `$(Version)` je nastavena na `$(VersionPrefix)` v kombinaci s `$(VersionSuffix)`, oddělená spojovníkem.</span><span class="sxs-lookup"><span data-stu-id="cb32c-167">Then, `$(Version)` is set to the `$(VersionPrefix)` combined with the `$(VersionSuffix)`, separated by a dash.</span></span>

## <a name="examples"></a><span data-ttu-id="cb32c-168">Příklady</span><span class="sxs-lookup"><span data-stu-id="cb32c-168">Examples</span></span>

* <span data-ttu-id="cb32c-169">Sestavení projektu a jeho závislosti:</span><span class="sxs-lookup"><span data-stu-id="cb32c-169">Build a project and its dependencies:</span></span>

  ```console
  dotnet build
  ```

* <span data-ttu-id="cb32c-170">Sestavení projektu a jeho závislosti pomocí konfigurace vydané verze:</span><span class="sxs-lookup"><span data-stu-id="cb32c-170">Build a project and its dependencies using Release configuration:</span></span>

  ```console
  dotnet build --configuration Release
  ```

* <span data-ttu-id="cb32c-171">Sestavení projektu a jeho závislosti pro konkrétní prostředí runtime (v tomto příkladu Ubuntu 18.04):</span><span class="sxs-lookup"><span data-stu-id="cb32c-171">Build a project and its dependencies for a specific runtime (in this example, Ubuntu 18.04):</span></span>

  ```console
  dotnet build --runtime ubuntu.18.04-x64
  ```

* <span data-ttu-id="cb32c-172">Sestavte projekt a použít zadaný zdroj balíčku NuGet během operace obnovení (.NET Core 2.0 SDK a novější):</span><span class="sxs-lookup"><span data-stu-id="cb32c-172">Build the project and use the specified NuGet package source during the restore operation (.NET Core 2.0 SDK and later versions):</span></span>

  ```console
  dotnet build --source c:\packages\mypackages
  ```

* <span data-ttu-id="cb32c-173">Sestavte projekt a nastavte 1.2.3.4 verzi jako parametr sestavení:</span><span class="sxs-lookup"><span data-stu-id="cb32c-173">Build the project and set 1.2.3.4 version as a build parameter:</span></span>

  ```console
  dotnet build -p:Version=1.2.3.4
  ```
