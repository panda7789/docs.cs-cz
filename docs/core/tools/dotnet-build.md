---
title: DotNet sestavení příkaz – rozhraní příkazového řádku .NET Core
description: Dotnet sestavení příkaz sestavení projektu a všechny jeho závislosti.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: c9d1478e3d3e298b01e707242cc7ad5cd924a9b3
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50200547"
---
# <a name="dotnet-build"></a><span data-ttu-id="d65d7-103">DotNet sestavení</span><span class="sxs-lookup"><span data-stu-id="d65d7-103">dotnet build</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="d65d7-104">Název</span><span class="sxs-lookup"><span data-stu-id="d65d7-104">Name</span></span>

<span data-ttu-id="d65d7-105">`dotnet build` -Sestavení projektu a všechny jeho závislosti.</span><span class="sxs-lookup"><span data-stu-id="d65d7-105">`dotnet build` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d65d7-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="d65d7-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="d65d7-107">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="d65d7-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--force] [--no-dependencies] [--no-incremental]
    [--no-restore] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d65d7-108">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="d65d7-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--no-dependencies] [--no-incremental] [-o|--output]
    [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="d65d7-109">Popis</span><span class="sxs-lookup"><span data-stu-id="d65d7-109">Description</span></span>

<span data-ttu-id="d65d7-110">`dotnet build` Příkaz sestaví projekt a jeho závislosti do sady binární soubory.</span><span class="sxs-lookup"><span data-stu-id="d65d7-110">The `dotnet build` command builds the project and its dependencies into a set of binaries.</span></span> <span data-ttu-id="d65d7-111">Binární soubory zahrnují projektu kódu v souborech Intermediate Language (IL) s *.dll* rozšíření a symbol soubory používané pro ladění v sadě *PDB* rozšíření.</span><span class="sxs-lookup"><span data-stu-id="d65d7-111">The binaries include the project's code in Intermediate Language (IL) files with a *.dll* extension and symbol files used for debugging with a *.pdb* extension.</span></span> <span data-ttu-id="d65d7-112">Soubor JSON závislosti (*\*. deps.json*) je vytvořen, který obsahuje seznam závislostí aplikace.</span><span class="sxs-lookup"><span data-stu-id="d65d7-112">A dependencies JSON file (*\*.deps.json*) is produced that lists the dependencies of the application.</span></span> <span data-ttu-id="d65d7-113">A  *\*. runtimeconfig.json* je vytvořen soubor, který určuje sdílený modul runtime a jeho verze pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d65d7-113">A *\*.runtimeconfig.json* file is produced, which specifies the shared runtime and its version for the application.</span></span>

<span data-ttu-id="d65d7-114">Obsahuje-li projekt závislostí třetích stran, jako jsou knihovny z Nugetu, že vyřešit z mezipaměti NuGet a nejsou k dispozici s sestavení výstupu projektu.</span><span class="sxs-lookup"><span data-stu-id="d65d7-114">If the project has third-party dependencies, such as libraries from NuGet, they're resolved from the NuGet cache and aren't available with the project's built output.</span></span> <span data-ttu-id="d65d7-115">Skutečností, součin `dotnet build` není připravené k převedení do jiného počítače ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="d65d7-115">With that in mind, the product of `dotnet build` isn't ready to be transferred to another machine to run.</span></span> <span data-ttu-id="d65d7-116">To se liší od chování rozhraní .NET Framework ve které vytváření spustitelného souboru projektu (aplikace) vytvoří výstup, který je spustitelný na libovolný počítač, ve kterém je nainstalováno rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d65d7-116">This is in contrast to the behavior of the .NET Framework in which building an executable project (an application) produces output that's runnable on any machine where the .NET Framework is installed.</span></span> <span data-ttu-id="d65d7-117">Pokud chcete, aby fungují na podobném principu s .NET Core, budete muset použít [dotnet publikovat](dotnet-publish.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="d65d7-117">To have a similar experience with .NET Core, you need to use the [dotnet publish](dotnet-publish.md) command.</span></span> <span data-ttu-id="d65d7-118">Další informace najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="d65d7-118">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span>

<span data-ttu-id="d65d7-119">Vytváření vyžaduje *project.assets.json* soubor, který obsahuje seznam závislostí vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="d65d7-119">Building requires the *project.assets.json* file, which lists the dependencies of your application.</span></span> <span data-ttu-id="d65d7-120">Soubor je vytvořen při [ `dotnet restore` ](dotnet-restore.md) provádí.</span><span class="sxs-lookup"><span data-stu-id="d65d7-120">The file is created when [`dotnet restore`](dotnet-restore.md) is executed.</span></span> <span data-ttu-id="d65d7-121">Bez souboru prostředků v místě nelze nástrojů vyřešit referenční sestavení, což má za následek chyby.</span><span class="sxs-lookup"><span data-stu-id="d65d7-121">Without the assets file in place, the tooling cannot resolve reference assemblies, which results in errors.</span></span> <span data-ttu-id="d65d7-122">S .NET Core 1.x SDK potřebné ke spuštění explicitně `dotnet restore` dřív, než spustíte `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="d65d7-122">With .NET Core 1.x SDK, you needed to explicitly run the `dotnet restore` before running `dotnet build`.</span></span> <span data-ttu-id="d65d7-123">Počínaje .NET Core 2.0 SDK `dotnet restore` se implicitně spouští při spuštění `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="d65d7-123">Starting with .NET Core 2.0 SDK, `dotnet restore` runs implicitly when you run `dotnet build`.</span></span> <span data-ttu-id="d65d7-124">Pokud chcete zakázat implicitní obnovení při spuštění příkazu k sestavení, lze předat `--no-restore` možnost.</span><span class="sxs-lookup"><span data-stu-id="d65d7-124">If you want to disable implicit restore when running the build command, you can pass the `--no-restore` option.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

<span data-ttu-id="d65d7-125">`dotnet build` používá MSBuild k sestavení projektu, takže podporuje paralelní i přírůstkové sestavení.</span><span class="sxs-lookup"><span data-stu-id="d65d7-125">`dotnet build` uses MSBuild to build the project, so it supports both parallel and incremental builds.</span></span> <span data-ttu-id="d65d7-126">Další informace najdete v tématu [přírůstková sestavení](/visualstudio/msbuild/incremental-builds).</span><span class="sxs-lookup"><span data-stu-id="d65d7-126">For more information, see [Incremental Builds](/visualstudio/msbuild/incremental-builds).</span></span>

<span data-ttu-id="d65d7-127">Kromě jeho možností `dotnet build` příkaz přijímá MSBuild možnosti, jako například `-p` pro nastavení vlastnosti nebo `-l` k definování protokolovač.</span><span class="sxs-lookup"><span data-stu-id="d65d7-127">In addition to its options, the `dotnet build` command accepts MSBuild options, such as `-p` for setting properties or `-l` to define a logger.</span></span> <span data-ttu-id="d65d7-128">Další informace o těchto možnostech najdete v tématu [MSBuild Reference k příkazovému řádku](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="d65d7-128">For more information about these options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="d65d7-129">Určuje, zda je projekt spustitelné nebo ne je určeno `<OutputType>` vlastnost v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="d65d7-129">Whether the project is executable or not is determined by the `<OutputType>` property in the project file.</span></span> <span data-ttu-id="d65d7-130">Následující příklad ukazuje projekt, který vytvoří spustitelný kód:</span><span class="sxs-lookup"><span data-stu-id="d65d7-130">The following example shows a project that produces executable code:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="d65d7-131">Pokud chcete vytvořit knihovnu, vynechejte `<OutputType>` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d65d7-131">In order to produce a library, omit the `<OutputType>` property.</span></span> <span data-ttu-id="d65d7-132">Hlavní rozdíl v sestavení výstupu je, že knihovna DLL IL pro knihovnu neobsahuje vstupní body a nelze ho provést.</span><span class="sxs-lookup"><span data-stu-id="d65d7-132">The main difference in built output is that the IL DLL for a library doesn't contain entry points and can't be executed.</span></span>

## <a name="arguments"></a><span data-ttu-id="d65d7-133">Arguments</span><span class="sxs-lookup"><span data-stu-id="d65d7-133">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="d65d7-134">Soubor projektu nebo řešení pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="d65d7-134">The project or solution file to build.</span></span> <span data-ttu-id="d65d7-135">Pokud není zadán soubor projektu nebo řešení, MSBuild vyhledá aktuální pracovní adresář pro soubor, který má příponu souboru, který končí *proj* nebo *sln* a použije tento soubor.</span><span class="sxs-lookup"><span data-stu-id="d65d7-135">If a project or solution file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in either *proj* or *sln* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="d65d7-136">Možnosti</span><span class="sxs-lookup"><span data-stu-id="d65d7-136">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="d65d7-137">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="d65d7-137">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="d65d7-138">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="d65d7-138">Defines the build configuration.</span></span> <span data-ttu-id="d65d7-139">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="d65d7-139">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="d65d7-140">Zkompiluje pro konkrétní [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="d65d7-140">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="d65d7-141">Rozhraní musí být definován v [soubor projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="d65d7-141">The framework must be defined in the [project file](csproj.md).</span></span>

`--force`

<span data-ttu-id="d65d7-142">Způsobí, že všechny závislosti vyřešit i v případě, že poslední obnovení bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="d65d7-142">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="d65d7-143">Zadání tohoto příznaku je stejný jako odstranění *project.assets.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="d65d7-143">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="d65d7-144">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="d65d7-144">Prints out a short help for the command.</span></span>

`--no-dependencies`

<span data-ttu-id="d65d7-145">Pouze sestavení projektu zadaný kořenový a ignoruje odkazy typu projekt projekt (P2P).</span><span class="sxs-lookup"><span data-stu-id="d65d7-145">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

`--no-incremental`

<span data-ttu-id="d65d7-146">Označí sestavení jako problematické pro přírůstkové sestavení.</span><span class="sxs-lookup"><span data-stu-id="d65d7-146">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="d65d7-147">Tento příznak vypne přírůstková kompilace a vynutí opětovné čisté sestavení grafu závislostí projektu.</span><span class="sxs-lookup"><span data-stu-id="d65d7-147">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

`--no-restore`

<span data-ttu-id="d65d7-148">Neprovede implicitní obnovení během sestavování.</span><span class="sxs-lookup"><span data-stu-id="d65d7-148">Doesn't execute an implicit restore during build.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="d65d7-149">Adresář, do kterého chcete sestavené binární soubory.</span><span class="sxs-lookup"><span data-stu-id="d65d7-149">Directory in which to place the built binaries.</span></span> <span data-ttu-id="d65d7-150">Budete také muset definovat `--framework` při zadání této možnosti.</span><span class="sxs-lookup"><span data-stu-id="d65d7-150">You also need to define `--framework` when you specify this option.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="d65d7-151">Určuje cílový modul runtime.</span><span class="sxs-lookup"><span data-stu-id="d65d7-151">Specifies the target runtime.</span></span> <span data-ttu-id="d65d7-152">Seznam identifikátorů modulů Runtime (RID), najdete v článku [katalog identifikátorů RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="d65d7-152">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="d65d7-153">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="d65d7-153">Sets the verbosity level of the command.</span></span> <span data-ttu-id="d65d7-154">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d65d7-154">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="d65d7-155">Definuje, verze přípona hvězdičku (`*`) v poli verze souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="d65d7-155">Defines the version suffix for an asterisk (`*`) in the version field of the project file.</span></span> <span data-ttu-id="d65d7-156">Formát řídí pokyny verze Nugetu.</span><span class="sxs-lookup"><span data-stu-id="d65d7-156">The format follows NuGet's version guidelines.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d65d7-157">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="d65d7-157">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="d65d7-158">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="d65d7-158">Defines the build configuration.</span></span> <span data-ttu-id="d65d7-159">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="d65d7-159">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="d65d7-160">Zkompiluje pro konkrétní [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="d65d7-160">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="d65d7-161">Rozhraní musí být definován v [soubor projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="d65d7-161">The framework must be defined in the [project file](csproj.md).</span></span>

`-h|--help`

<span data-ttu-id="d65d7-162">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="d65d7-162">Prints out a short help for the command.</span></span>

`--no-dependencies`

<span data-ttu-id="d65d7-163">Pouze sestavení projektu zadaný kořenový a ignoruje odkazy typu projekt projekt (P2P).</span><span class="sxs-lookup"><span data-stu-id="d65d7-163">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

`--no-incremental`

<span data-ttu-id="d65d7-164">Označí sestavení jako problematické pro přírůstkové sestavení.</span><span class="sxs-lookup"><span data-stu-id="d65d7-164">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="d65d7-165">Tento příznak vypne přírůstková kompilace a vynutí opětovné čisté sestavení grafu závislostí projektu.</span><span class="sxs-lookup"><span data-stu-id="d65d7-165">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="d65d7-166">Adresář, do kterého chcete sestavené binární soubory.</span><span class="sxs-lookup"><span data-stu-id="d65d7-166">Directory in which to place the built binaries.</span></span> <span data-ttu-id="d65d7-167">Budete také muset definovat `--framework` při zadání této možnosti.</span><span class="sxs-lookup"><span data-stu-id="d65d7-167">You also need to define `--framework` when you specify this option.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="d65d7-168">Určuje cílový modul runtime.</span><span class="sxs-lookup"><span data-stu-id="d65d7-168">Specifies the target runtime.</span></span> <span data-ttu-id="d65d7-169">Seznam identifikátorů modulů Runtime (RID), najdete v článku [katalog identifikátorů RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="d65d7-169">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="d65d7-170">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="d65d7-170">Sets the verbosity level of the command.</span></span> <span data-ttu-id="d65d7-171">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d65d7-171">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="d65d7-172">Definuje, verze přípona hvězdičku (`*`) v poli verze souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="d65d7-172">Defines the version suffix for an asterisk (`*`) in the version field of the project file.</span></span> <span data-ttu-id="d65d7-173">Formát řídí pokyny verze Nugetu.</span><span class="sxs-lookup"><span data-stu-id="d65d7-173">The format follows NuGet's version guidelines.</span></span>

---

## <a name="examples"></a><span data-ttu-id="d65d7-174">Příklady</span><span class="sxs-lookup"><span data-stu-id="d65d7-174">Examples</span></span>

<span data-ttu-id="d65d7-175">Sestavení projektu a jeho závislosti:</span><span class="sxs-lookup"><span data-stu-id="d65d7-175">Build a project and its dependencies:</span></span>

`dotnet build`

<span data-ttu-id="d65d7-176">Sestavení projektu a jeho závislosti pomocí konfigurace vydané verze:</span><span class="sxs-lookup"><span data-stu-id="d65d7-176">Build a project and its dependencies using Release configuration:</span></span>

`dotnet build --configuration Release`

<span data-ttu-id="d65d7-177">Sestavení projektu a jeho závislosti pro konkrétní prostředí runtime (v tomto příkladu se systémem Ubuntu 16.04):</span><span class="sxs-lookup"><span data-stu-id="d65d7-177">Build a project and its dependencies for a specific runtime (in this example, Ubuntu 16.04):</span></span>

`dotnet build --runtime ubuntu.16.04-x64`

<span data-ttu-id="d65d7-178">Sestavte projekt a použít zadaný zdroj balíčku NuGet během operace obnovení (.NET Core SDK 2.0 a novější):</span><span class="sxs-lookup"><span data-stu-id="d65d7-178">Build the project and use the specified NuGet package source during the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet build --source c:\packages\mypackages`