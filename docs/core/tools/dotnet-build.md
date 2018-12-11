---
title: příkaz DotNet sestavení
description: Dotnet sestavení příkaz sestavení projektu a všechny jeho závislosti.
ms.date: 12/04/2018
ms.openlocfilehash: 1e5e05d51f98394b2b77e3a8fc645cf9712b0a0f
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169689"
---
# <a name="dotnet-build"></a><span data-ttu-id="639be-103">DotNet sestavení</span><span class="sxs-lookup"><span data-stu-id="639be-103">dotnet build</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="639be-104">Název</span><span class="sxs-lookup"><span data-stu-id="639be-104">Name</span></span>

<span data-ttu-id="639be-105">`dotnet build` -Sestavení projektu a všechny jeho závislosti.</span><span class="sxs-lookup"><span data-stu-id="639be-105">`dotnet build` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="639be-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="639be-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="639be-107">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="639be-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--force] [--no-dependencies] [--no-incremental]
    [--no-restore] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="639be-108">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="639be-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--no-dependencies] [--no-incremental] [-o|--output]
    [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="639be-109">Popis</span><span class="sxs-lookup"><span data-stu-id="639be-109">Description</span></span>

<span data-ttu-id="639be-110">`dotnet build` Příkaz sestaví projekt a jeho závislosti do sady binární soubory.</span><span class="sxs-lookup"><span data-stu-id="639be-110">The `dotnet build` command builds the project and its dependencies into a set of binaries.</span></span> <span data-ttu-id="639be-111">Binární soubory zahrnují projektu kódu v souborech Intermediate Language (IL) s *.dll* rozšíření a symbol soubory používané pro ladění v sadě *PDB* rozšíření.</span><span class="sxs-lookup"><span data-stu-id="639be-111">The binaries include the project's code in Intermediate Language (IL) files with a *.dll* extension and symbol files used for debugging with a *.pdb* extension.</span></span> <span data-ttu-id="639be-112">Soubor JSON závislosti (*\*. deps.json*) je vytvořen, který obsahuje seznam závislostí aplikace.</span><span class="sxs-lookup"><span data-stu-id="639be-112">A dependencies JSON file (*\*.deps.json*) is produced that lists the dependencies of the application.</span></span> <span data-ttu-id="639be-113">A  *\*. runtimeconfig.json* je vytvořen soubor, který určuje sdílený modul runtime a jeho verze pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="639be-113">A *\*.runtimeconfig.json* file is produced, which specifies the shared runtime and its version for the application.</span></span>

<span data-ttu-id="639be-114">Obsahuje-li projekt závislostí třetích stran, jako jsou knihovny z Nugetu, že vyřešit z mezipaměti NuGet a nejsou k dispozici s sestavení výstupu projektu.</span><span class="sxs-lookup"><span data-stu-id="639be-114">If the project has third-party dependencies, such as libraries from NuGet, they're resolved from the NuGet cache and aren't available with the project's built output.</span></span> <span data-ttu-id="639be-115">Skutečností, součin `dotnet build` není připravené k převedení do jiného počítače ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="639be-115">With that in mind, the product of `dotnet build` isn't ready to be transferred to another machine to run.</span></span> <span data-ttu-id="639be-116">To se liší od chování rozhraní .NET Framework ve které vytváření spustitelného souboru projektu (aplikace) vytvoří výstup, který je spustitelný na libovolný počítač, ve kterém je nainstalováno rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="639be-116">This is in contrast to the behavior of the .NET Framework in which building an executable project (an application) produces output that's runnable on any machine where the .NET Framework is installed.</span></span> <span data-ttu-id="639be-117">Pokud chcete, aby fungují na podobném principu s .NET Core, budete muset použít [dotnet publikovat](dotnet-publish.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="639be-117">To have a similar experience with .NET Core, you need to use the [dotnet publish](dotnet-publish.md) command.</span></span> <span data-ttu-id="639be-118">Další informace najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="639be-118">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span>

<span data-ttu-id="639be-119">Vytváření vyžaduje *project.assets.json* soubor, který obsahuje seznam závislostí vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="639be-119">Building requires the *project.assets.json* file, which lists the dependencies of your application.</span></span> <span data-ttu-id="639be-120">Soubor je vytvořen při [ `dotnet restore` ](dotnet-restore.md) provádí.</span><span class="sxs-lookup"><span data-stu-id="639be-120">The file is created when [`dotnet restore`](dotnet-restore.md) is executed.</span></span> <span data-ttu-id="639be-121">Bez souboru prostředků v místě nelze nástrojů vyřešit referenční sestavení, což má za následek chyby.</span><span class="sxs-lookup"><span data-stu-id="639be-121">Without the assets file in place, the tooling cannot resolve reference assemblies, which results in errors.</span></span> <span data-ttu-id="639be-122">S .NET Core 1.x SDK potřebné ke spuštění explicitně `dotnet restore` dřív, než spustíte `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="639be-122">With .NET Core 1.x SDK, you needed to explicitly run the `dotnet restore` before running `dotnet build`.</span></span> <span data-ttu-id="639be-123">Počínaje .NET Core 2.0 SDK `dotnet restore` se implicitně spouští při spuštění `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="639be-123">Starting with .NET Core 2.0 SDK, `dotnet restore` runs implicitly when you run `dotnet build`.</span></span> <span data-ttu-id="639be-124">Pokud chcete zakázat implicitní obnovení při spuštění příkazu k sestavení, lze předat `--no-restore` možnost.</span><span class="sxs-lookup"><span data-stu-id="639be-124">If you want to disable implicit restore when running the build command, you can pass the `--no-restore` option.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

<span data-ttu-id="639be-125">Určuje, zda je projekt spustitelné nebo ne je určeno `<OutputType>` vlastnost v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="639be-125">Whether the project is executable or not is determined by the `<OutputType>` property in the project file.</span></span> <span data-ttu-id="639be-126">Následující příklad ukazuje projekt, který vytvoří spustitelný kód:</span><span class="sxs-lookup"><span data-stu-id="639be-126">The following example shows a project that produces executable code:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="639be-127">Pokud chcete vytvořit knihovnu, vynechejte `<OutputType>` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="639be-127">In order to produce a library, omit the `<OutputType>` property.</span></span> <span data-ttu-id="639be-128">Hlavní rozdíl v sestavení výstupu je, že knihovna DLL IL pro knihovnu neobsahuje vstupní body a nelze ho provést.</span><span class="sxs-lookup"><span data-stu-id="639be-128">The main difference in built output is that the IL DLL for a library doesn't contain entry points and can't be executed.</span></span>

### <a name="msbuild"></a><span data-ttu-id="639be-129">MSBuild</span><span class="sxs-lookup"><span data-stu-id="639be-129">MSBuild</span></span>

<span data-ttu-id="639be-130">`dotnet build` používá MSBuild k sestavení projektu, takže podporuje paralelní i přírůstkové sestavení.</span><span class="sxs-lookup"><span data-stu-id="639be-130">`dotnet build` uses MSBuild to build the project, so it supports both parallel and incremental builds.</span></span> <span data-ttu-id="639be-131">Další informace najdete v tématu [přírůstková sestavení](/visualstudio/msbuild/incremental-builds).</span><span class="sxs-lookup"><span data-stu-id="639be-131">For more information, see [Incremental Builds](/visualstudio/msbuild/incremental-builds).</span></span>

<span data-ttu-id="639be-132">Kromě jeho možností `dotnet build` příkaz přijímá MSBuild možnosti, jako například `-p` pro nastavení vlastnosti nebo `-l` k definování protokolovač.</span><span class="sxs-lookup"><span data-stu-id="639be-132">In addition to its options, the `dotnet build` command accepts MSBuild options, such as `-p` for setting properties or `-l` to define a logger.</span></span> <span data-ttu-id="639be-133">Další informace o těchto možnostech najdete v tématu [MSBuild Reference k příkazovému řádku](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="639be-133">For more information about these options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="639be-134">Nebo můžete použít také [dotnet msbuild](dotnet-msbuild.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="639be-134">Or you can also use the [dotnet msbuild](dotnet-msbuild.md) command.</span></span>

<span data-ttu-id="639be-135">Spuštění `dotnet build` je ekvivalentní `dotnet msbuild -restore -target:Build`.</span><span class="sxs-lookup"><span data-stu-id="639be-135">Running `dotnet build` is equivalent to `dotnet msbuild -restore -target:Build`.</span></span>

## <a name="arguments"></a><span data-ttu-id="639be-136">Arguments</span><span class="sxs-lookup"><span data-stu-id="639be-136">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="639be-137">Soubor projektu nebo řešení pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="639be-137">The project or solution file to build.</span></span> <span data-ttu-id="639be-138">Pokud není zadán soubor projektu nebo řešení, MSBuild vyhledá aktuální pracovní adresář pro soubor, který má příponu souboru, který končí *proj* nebo *sln* a použije tento soubor.</span><span class="sxs-lookup"><span data-stu-id="639be-138">If a project or solution file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in either *proj* or *sln* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="639be-139">Možnosti</span><span class="sxs-lookup"><span data-stu-id="639be-139">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="639be-140">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="639be-140">.NET Core 2.x</span></span>](#tab/netcore2x)

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="639be-141">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="639be-141">Defines the build configuration.</span></span> <span data-ttu-id="639be-142">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="639be-142">The default value is `Debug`.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="639be-143">Zkompiluje pro konkrétní [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="639be-143">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="639be-144">Rozhraní musí být definován v [soubor projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="639be-144">The framework must be defined in the [project file](csproj.md).</span></span>

* **`--force`**

  <span data-ttu-id="639be-145">Způsobí, že všechny závislosti vyřešit i v případě, že poslední obnovení bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="639be-145">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="639be-146">Zadání tohoto příznaku je stejný jako odstranění *project.assets.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="639be-146">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

* **`-h|--help`**

  <span data-ttu-id="639be-147">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="639be-147">Prints out a short help for the command.</span></span>

* **`--no-dependencies`**

  <span data-ttu-id="639be-148">Pouze sestavení projektu zadaný kořenový a ignoruje odkazy typu projekt projekt (P2P).</span><span class="sxs-lookup"><span data-stu-id="639be-148">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

* **`--no-incremental`**

  <span data-ttu-id="639be-149">Označí sestavení jako problematické pro přírůstkové sestavení.</span><span class="sxs-lookup"><span data-stu-id="639be-149">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="639be-150">Tento příznak vypne přírůstková kompilace a vynutí opětovné čisté sestavení grafu závislostí projektu.</span><span class="sxs-lookup"><span data-stu-id="639be-150">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

* **`--no-restore`**

  <span data-ttu-id="639be-151">Neprovede implicitní obnovení během sestavování.</span><span class="sxs-lookup"><span data-stu-id="639be-151">Doesn't execute an implicit restore during build.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="639be-152">Adresář, do kterého chcete sestavené binární soubory.</span><span class="sxs-lookup"><span data-stu-id="639be-152">Directory in which to place the built binaries.</span></span> <span data-ttu-id="639be-153">Budete také muset definovat `--framework` při zadání této možnosti.</span><span class="sxs-lookup"><span data-stu-id="639be-153">You also need to define `--framework` when you specify this option.</span></span> <span data-ttu-id="639be-154">Pokud není zadán, výchozí cesta je `./bin/<configuration>/<framework>/`.</span><span class="sxs-lookup"><span data-stu-id="639be-154">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="639be-155">Určuje cílový modul runtime.</span><span class="sxs-lookup"><span data-stu-id="639be-155">Specifies the target runtime.</span></span> <span data-ttu-id="639be-156">Seznam identifikátorů modulů Runtime (RID), najdete v článku [katalog identifikátorů RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="639be-156">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="639be-157">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="639be-157">Sets the verbosity level of the command.</span></span> <span data-ttu-id="639be-158">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="639be-158">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

* **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="639be-159">Definuje, verze přípona hvězdičku (`*`) v poli verze souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="639be-159">Defines the version suffix for an asterisk (`*`) in the version field of the project file.</span></span> <span data-ttu-id="639be-160">Formát řídí pokyny verze Nugetu.</span><span class="sxs-lookup"><span data-stu-id="639be-160">The format follows NuGet's version guidelines.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="639be-161">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="639be-161">.NET Core 1.x</span></span>](#tab/netcore1x)

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="639be-162">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="639be-162">Defines the build configuration.</span></span> <span data-ttu-id="639be-163">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="639be-163">The default value is `Debug`.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="639be-164">Zkompiluje pro konkrétní [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="639be-164">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="639be-165">Rozhraní musí být definován v [soubor projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="639be-165">The framework must be defined in the [project file](csproj.md).</span></span>

* **`-h|--help`**

  <span data-ttu-id="639be-166">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="639be-166">Prints out a short help for the command.</span></span>

* **`--no-dependencies`**

  <span data-ttu-id="639be-167">Pouze sestavení projektu zadaný kořenový a ignoruje odkazy typu projekt projekt (P2P).</span><span class="sxs-lookup"><span data-stu-id="639be-167">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

* **`--no-incremental`**

  <span data-ttu-id="639be-168">Označí sestavení jako problematické pro přírůstkové sestavení.</span><span class="sxs-lookup"><span data-stu-id="639be-168">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="639be-169">Tento příznak vypne přírůstková kompilace a vynutí opětovné čisté sestavení grafu závislostí projektu.</span><span class="sxs-lookup"><span data-stu-id="639be-169">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="639be-170">Adresář, do kterého chcete sestavené binární soubory.</span><span class="sxs-lookup"><span data-stu-id="639be-170">Directory in which to place the built binaries.</span></span> <span data-ttu-id="639be-171">Budete také muset definovat `--framework` při zadání této možnosti.</span><span class="sxs-lookup"><span data-stu-id="639be-171">You also need to define `--framework` when you specify this option.</span></span>

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="639be-172">Určuje cílový modul runtime.</span><span class="sxs-lookup"><span data-stu-id="639be-172">Specifies the target runtime.</span></span> <span data-ttu-id="639be-173">Seznam identifikátorů modulů Runtime (RID), najdete v článku [katalog identifikátorů RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="639be-173">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="639be-174">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="639be-174">Sets the verbosity level of the command.</span></span> <span data-ttu-id="639be-175">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="639be-175">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

* **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="639be-176">Definuje, verze přípona hvězdičku (`*`) v poli verze souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="639be-176">Defines the version suffix for an asterisk (`*`) in the version field of the project file.</span></span> <span data-ttu-id="639be-177">Formát řídí pokyny verze Nugetu.</span><span class="sxs-lookup"><span data-stu-id="639be-177">The format follows NuGet's version guidelines.</span></span>

---

## <a name="examples"></a><span data-ttu-id="639be-178">Příklady</span><span class="sxs-lookup"><span data-stu-id="639be-178">Examples</span></span>

* <span data-ttu-id="639be-179">Sestavení projektu a jeho závislosti:</span><span class="sxs-lookup"><span data-stu-id="639be-179">Build a project and its dependencies:</span></span>

  ```console
  dotnet build
  ```

* <span data-ttu-id="639be-180">Sestavení projektu a jeho závislosti pomocí konfigurace vydané verze:</span><span class="sxs-lookup"><span data-stu-id="639be-180">Build a project and its dependencies using Release configuration:</span></span>

  ```console
  dotnet build --configuration Release
  ```

* <span data-ttu-id="639be-181">Sestavení projektu a jeho závislosti pro konkrétní prostředí runtime (v tomto příkladu se systémem Ubuntu 16.04):</span><span class="sxs-lookup"><span data-stu-id="639be-181">Build a project and its dependencies for a specific runtime (in this example, Ubuntu 16.04):</span></span>

  ```console
  dotnet build --runtime ubuntu.16.04-x64
  ```

* <span data-ttu-id="639be-182">Sestavte projekt a použít zadaný zdroj balíčku NuGet během operace obnovení (.NET Core 2.0 SDK a novější):</span><span class="sxs-lookup"><span data-stu-id="639be-182">Build the project and use the specified NuGet package source during the restore operation (.NET Core 2.0 SDK and later versions):</span></span>

  ```console
  dotnet build --source c:\packages\mypackages
  ```

* <span data-ttu-id="639be-183">Sestavte projekt a nastavte 1.2.3.4 verzi jako parametr sestavení:</span><span class="sxs-lookup"><span data-stu-id="639be-183">Build the project and set 1.2.3.4 version as a build parameter:</span></span>

  ```console
  dotnet build -p:Version=1.2.3.4
  ```