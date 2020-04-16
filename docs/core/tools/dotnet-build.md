---
title: dotnet sestavení, příkaz
description: Příkaz sestavení dotnet vytvoří projekt a všechny jeho závislosti.
ms.date: 02/14/2020
ms.openlocfilehash: 27deca4ab1c12314db5214c73660862a8a57a398
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463712"
---
# <a name="dotnet-build"></a><span data-ttu-id="23695-103">dotnet build</span><span class="sxs-lookup"><span data-stu-id="23695-103">dotnet build</span></span>

<span data-ttu-id="23695-104">**Tento článek se týká:** ✔️ .NET Core 2.x SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="23695-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="23695-105">Název</span><span class="sxs-lookup"><span data-stu-id="23695-105">Name</span></span>

<span data-ttu-id="23695-106">`dotnet build`- Vytvoří projekt a všechny jeho závislosti.</span><span class="sxs-lookup"><span data-stu-id="23695-106">`dotnet build` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="23695-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="23695-107">Synopsis</span></span>

```dotnetcli
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [-f|--framework <FRAMEWORK>] [--force] [--interactive] [--no-dependencies]
    [--no-incremental] [--no-restore] [--nologo] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-v|--verbosity <LEVEL>]
    [--version-suffix <VERSION_SUFFIX>]

dotnet build -h|--help
```

## <a name="description"></a><span data-ttu-id="23695-108">Popis</span><span class="sxs-lookup"><span data-stu-id="23695-108">Description</span></span>

<span data-ttu-id="23695-109">Příkaz `dotnet build` vytvoří projekt a jeho závislosti do sady binárních souborů.</span><span class="sxs-lookup"><span data-stu-id="23695-109">The `dotnet build` command builds the project and its dependencies into a set of binaries.</span></span> <span data-ttu-id="23695-110">Binární soubory zahrnují kód projektu v souborech zprostředkujícíjazyk (IL) s příponou *DLL.*</span><span class="sxs-lookup"><span data-stu-id="23695-110">The binaries include the project's code in Intermediate Language (IL) files with a *.dll* extension.</span></span>  <span data-ttu-id="23695-111">V závislosti na typu a nastavení projektu mohou být zahrnuty další soubory, například:</span><span class="sxs-lookup"><span data-stu-id="23695-111">Depending on the project type and settings, other files may be included, such as:</span></span>

- <span data-ttu-id="23695-112">Spustitelný soubor, který lze použít ke spuštění aplikace, pokud je typ projektu spustitelným cílením .NET Core 3.0 nebo novějším.</span><span class="sxs-lookup"><span data-stu-id="23695-112">An executable that can be used to run the application, if the project type is an executable targeting .NET Core 3.0 or later.</span></span>
- <span data-ttu-id="23695-113">Soubory symbolů používané pro ladění s příponou *PDB.*</span><span class="sxs-lookup"><span data-stu-id="23695-113">Symbol files used for debugging with a *.pdb* extension.</span></span>
- <span data-ttu-id="23695-114">Soubor *.deps.json,* který obsahuje seznam závislostí aplikace nebo knihovny.</span><span class="sxs-lookup"><span data-stu-id="23695-114">A *.deps.json* file, which lists the dependencies of the application or library.</span></span>
- <span data-ttu-id="23695-115">Soubor *.runtimeconfig.json,* který určuje sdílený čas runtime a jeho verzi pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="23695-115">A *.runtimeconfig.json* file, which specifies the shared runtime and its version for an application.</span></span>
- <span data-ttu-id="23695-116">Další knihovny, na kterých projekt závisí (prostřednictvím odkazů na projekt nebo odkazů na balíček NuGet).</span><span class="sxs-lookup"><span data-stu-id="23695-116">Other libraries that the project depends on (via project references or NuGet package references).</span></span>

<span data-ttu-id="23695-117">U spustitelných projektů zaměřených na verze starší než .NET Core 3.0 se závislosti knihovny z NuGet obvykle nezkopírují do výstupní složky.</span><span class="sxs-lookup"><span data-stu-id="23695-117">For executable projects targeting versions earlier than .NET Core 3.0, library dependencies from NuGet are typically NOT copied to the output folder.</span></span>  <span data-ttu-id="23695-118">Jsou vyřešeny ze složky globálních balíčků NuGet za běhu.</span><span class="sxs-lookup"><span data-stu-id="23695-118">They're resolved from the NuGet global packages folder at run time.</span></span> <span data-ttu-id="23695-119">S ohledem na to `dotnet build` není produkt připraven k přenosu do jiného stroje ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="23695-119">With that in mind, the product of `dotnet build` isn't ready to be transferred to another machine to run.</span></span> <span data-ttu-id="23695-120">Chcete-li vytvořit verzi aplikace, kterou lze nasadit, musíte ji publikovat (například pomocí příkazu [dotnet publish).](dotnet-publish.md)</span><span class="sxs-lookup"><span data-stu-id="23695-120">To create a version of the application that can be deployed, you need to publish it (for example, with the [dotnet publish](dotnet-publish.md) command).</span></span> <span data-ttu-id="23695-121">Další informace naleznete v tématu [.NET Core Application Deployment](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="23695-121">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span>

<span data-ttu-id="23695-122">U spustitelných projektů zaměřených na rozhraní .NET Core 3.0 a novější jsou závislosti knihovny zkopírovány do výstupní složky.</span><span class="sxs-lookup"><span data-stu-id="23695-122">For executable projects targeting .NET Core 3.0 and later, library dependencies are copied to the output folder.</span></span> <span data-ttu-id="23695-123">To znamená, že pokud neexistuje žádná jiná logika specifická pro publikování (například webové projekty mají), výstup sestavení by měl být nasaditelný.</span><span class="sxs-lookup"><span data-stu-id="23695-123">This means that if there isn't any other publish-specific logic (such as Web projects have), the build output should be deployable.</span></span>

<span data-ttu-id="23695-124">Sestavení vyžaduje soubor *project.assets.json,* který obsahuje seznam závislostí vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="23695-124">Building requires the *project.assets.json* file, which lists the dependencies of your application.</span></span> <span data-ttu-id="23695-125">Soubor je vytvořen [`dotnet restore`](dotnet-restore.md) při spuštění.</span><span class="sxs-lookup"><span data-stu-id="23695-125">The file is created when [`dotnet restore`](dotnet-restore.md) is executed.</span></span> <span data-ttu-id="23695-126">Bez souboru datových zdrojů na místě nástroje nelze vyřešit referenční sestavení, což má za následek chyby.</span><span class="sxs-lookup"><span data-stu-id="23695-126">Without the assets file in place, the tooling can't resolve reference assemblies, which results in errors.</span></span> <span data-ttu-id="23695-127">Pomocí sady .NET Core 1.x SDK `dotnet restore` bylo `dotnet build`nutné před spuštěním explicitně spustit .</span><span class="sxs-lookup"><span data-stu-id="23695-127">With .NET Core 1.x SDK, you needed to explicitly run `dotnet restore` before running `dotnet build`.</span></span> <span data-ttu-id="23695-128">Počínaje sadou .NET Core 2.0 `dotnet restore` SDK, `dotnet build`běží implicitně při spuštění .</span><span class="sxs-lookup"><span data-stu-id="23695-128">Starting with .NET Core 2.0 SDK, `dotnet restore` runs implicitly when you run `dotnet build`.</span></span> <span data-ttu-id="23695-129">Pokud chcete zakázat implicitní obnovení při spuštění příkazu sestavení, můžete předat `--no-restore` možnost.</span><span class="sxs-lookup"><span data-stu-id="23695-129">If you want to disable implicit restore when running the build command, you can pass the `--no-restore` option.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

<span data-ttu-id="23695-130">Zda je projekt spustitelný nebo není, je určena `<OutputType>` vlastností v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="23695-130">Whether the project is executable or not is determined by the `<OutputType>` property in the project file.</span></span> <span data-ttu-id="23695-131">Následující příklad ukazuje projekt, který vytváří spustitelný kód:</span><span class="sxs-lookup"><span data-stu-id="23695-131">The following example shows a project that produces executable code:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="23695-132">Chcete-li vytvořit knihovnu, `<OutputType>` vynechte `Library`vlastnost nebo změňte její hodnotu na .</span><span class="sxs-lookup"><span data-stu-id="23695-132">To produce a library, omit the `<OutputType>` property or change its value to `Library`.</span></span> <span data-ttu-id="23695-133">Knihovna IL DLL pro knihovnu neobsahuje vstupní body a nelze ji spustit.</span><span class="sxs-lookup"><span data-stu-id="23695-133">The IL DLL for a library doesn't contain entry points and can't be executed.</span></span>

### <a name="msbuild"></a><span data-ttu-id="23695-134">MSBuild</span><span class="sxs-lookup"><span data-stu-id="23695-134">MSBuild</span></span>

<span data-ttu-id="23695-135">`dotnet build`používá MSBuild k sestavení projektu, takže podporuje paralelní i přírůstkové sestavení.</span><span class="sxs-lookup"><span data-stu-id="23695-135">`dotnet build` uses MSBuild to build the project, so it supports both parallel and incremental builds.</span></span> <span data-ttu-id="23695-136">Další informace naleznete [v tématu Přírůstková sestavení](/visualstudio/msbuild/incremental-builds).</span><span class="sxs-lookup"><span data-stu-id="23695-136">For more information, see [Incremental Builds](/visualstudio/msbuild/incremental-builds).</span></span>

<span data-ttu-id="23695-137">Kromě jeho možnosti `dotnet build` příkaz přijímá MSBuild možnosti, `-p` například `-l` pro nastavení vlastností nebo definovat protokolování.</span><span class="sxs-lookup"><span data-stu-id="23695-137">In addition to its options, the `dotnet build` command accepts MSBuild options, such as `-p` for setting properties or `-l` to define a logger.</span></span> <span data-ttu-id="23695-138">Další informace o těchto možnostech naleznete v [odkazu na příkazový řádek msbuildu](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="23695-138">For more information about these options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="23695-139">Nebo můžete také použít příkaz [dotnet msbuild.](dotnet-msbuild.md)</span><span class="sxs-lookup"><span data-stu-id="23695-139">Or you can also use the [dotnet msbuild](dotnet-msbuild.md) command.</span></span>

<span data-ttu-id="23695-140">Běh `dotnet build` je ekvivalentní `dotnet msbuild -restore`běhu ; výchozí podrobnost výstupu se však liší.</span><span class="sxs-lookup"><span data-stu-id="23695-140">Running `dotnet build` is equivalent to running `dotnet msbuild -restore`; however, the default verbosity of the output is different.</span></span>

## <a name="arguments"></a><span data-ttu-id="23695-141">Argumenty</span><span class="sxs-lookup"><span data-stu-id="23695-141">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="23695-142">Soubor projektu nebo řešení k sestavení.</span><span class="sxs-lookup"><span data-stu-id="23695-142">The project or solution file to build.</span></span> <span data-ttu-id="23695-143">Pokud není zadán soubor projektu nebo řešení, MSBuild vyhledá aktuální pracovní adresář pro soubor, který má příponu souboru, který končí *buď proj* nebo *sln* a používá tento soubor.</span><span class="sxs-lookup"><span data-stu-id="23695-143">If a project or solution file isn't specified, MSBuild searches the current working directory for a file that has a file extension that ends in either *proj* or *sln* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="23695-144">Možnosti</span><span class="sxs-lookup"><span data-stu-id="23695-144">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="23695-145">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="23695-145">Defines the build configuration.</span></span> <span data-ttu-id="23695-146">Výchozí hodnota pro `Debug`většinu projektů je , ale můžete přepsat nastavení konfigurace sestavení v projektu.</span><span class="sxs-lookup"><span data-stu-id="23695-146">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="23695-147">Zkompiluje pro konkrétní [rámec](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="23695-147">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="23695-148">Rámec musí být definován v [souboru projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="23695-148">The framework must be defined in the [project file](csproj.md).</span></span>

- **`--force`**

  <span data-ttu-id="23695-149">Vynutí vyřešení všech závislostí, i když bylo poslední obnovení úspěšné.</span><span class="sxs-lookup"><span data-stu-id="23695-149">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="23695-150">Zadání tohoto příznaku je stejné jako odstranění souboru *project.assets.json.*</span><span class="sxs-lookup"><span data-stu-id="23695-150">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="23695-151">Vytiskne krátkou nápovědu pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="23695-151">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="23695-152">Umožňuje příkazu zastavit a čekat na vstup uživatele nebo akci.</span><span class="sxs-lookup"><span data-stu-id="23695-152">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="23695-153">Například k dokončení ověřování.</span><span class="sxs-lookup"><span data-stu-id="23695-153">For example, to complete authentication.</span></span> <span data-ttu-id="23695-154">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="23695-154">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="23695-155">Ignoruje odkazy projekt-projekt (P2P) a pouze vytvoří zadaný kořenový projekt.</span><span class="sxs-lookup"><span data-stu-id="23695-155">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

- **`--no-incremental`**

  <span data-ttu-id="23695-156">Označí sestavení jako nebezpečné pro přírůstkové sestavení.</span><span class="sxs-lookup"><span data-stu-id="23695-156">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="23695-157">Tento příznak vypne přírůstkovou kompilaci a vynutí čisté opětovné sestavení grafu závislostí projektu.</span><span class="sxs-lookup"><span data-stu-id="23695-157">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

- **`--no-restore`**

  <span data-ttu-id="23695-158">Neprovede implicitní obnovení během sestavení.</span><span class="sxs-lookup"><span data-stu-id="23695-158">Doesn't execute an implicit restore during build.</span></span>

- **`--nologo`**

  <span data-ttu-id="23695-159">Nezobrazuje spouštěcí banner ani zprávu o autorských právech.</span><span class="sxs-lookup"><span data-stu-id="23695-159">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="23695-160">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="23695-160">Available since .NET Core 3.0 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="23695-161">Adresář, do kterého chcete umístit vytvořené binární soubory.</span><span class="sxs-lookup"><span data-stu-id="23695-161">Directory in which to place the built binaries.</span></span> <span data-ttu-id="23695-162">Pokud není zadán, výchozí `./bin/<configuration>/<framework>/`cesta je .</span><span class="sxs-lookup"><span data-stu-id="23695-162">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="23695-163">Pro projekty s více cílových rozhraní (prostřednictvím vlastnosti) `TargetFrameworks` je také nutné definovat, `--framework` když zadáte tuto možnost.</span><span class="sxs-lookup"><span data-stu-id="23695-163">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="23695-164">Určuje cílový čas běhu.</span><span class="sxs-lookup"><span data-stu-id="23695-164">Specifies the target runtime.</span></span> <span data-ttu-id="23695-165">Seznam identifikátorů modulu Runtime (RID) naleznete v [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="23695-165">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="23695-166">Nastaví úroveň podrobností MSBuild.</span><span class="sxs-lookup"><span data-stu-id="23695-166">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="23695-167">Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a .</span><span class="sxs-lookup"><span data-stu-id="23695-167">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="23695-168">Výchozí formát je `minimal`.</span><span class="sxs-lookup"><span data-stu-id="23695-168">The default is `minimal`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="23695-169">Nastaví hodnotu `$(VersionSuffix)` vlastnosti, která má být používána při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="23695-169">Sets the value of the `$(VersionSuffix)` property to use when building the project.</span></span> <span data-ttu-id="23695-170">To funguje pouze `$(Version)` v případě, že vlastnost není nastavena.</span><span class="sxs-lookup"><span data-stu-id="23695-170">This only works if the `$(Version)` property isn't set.</span></span> <span data-ttu-id="23695-171">Potom `$(Version)` je nastavena `$(VersionPrefix)` na kombinaci `$(VersionSuffix)`s , oddělenou pomlčkou.</span><span class="sxs-lookup"><span data-stu-id="23695-171">Then, `$(Version)` is set to the `$(VersionPrefix)` combined with the `$(VersionSuffix)`, separated by a dash.</span></span>

## <a name="examples"></a><span data-ttu-id="23695-172">Příklady</span><span class="sxs-lookup"><span data-stu-id="23695-172">Examples</span></span>

- <span data-ttu-id="23695-173">Sestavení projektu a jeho závislostí:</span><span class="sxs-lookup"><span data-stu-id="23695-173">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet build
  ```

- <span data-ttu-id="23695-174">Sestavení projektu a jeho závislostí pomocí konfigurace verze:</span><span class="sxs-lookup"><span data-stu-id="23695-174">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet build --configuration Release
  ```

- <span data-ttu-id="23695-175">Sestavení projektu a jeho závislostí pro konkrétní běhový čas (v tomto příkladu Ubuntu 18.04):</span><span class="sxs-lookup"><span data-stu-id="23695-175">Build a project and its dependencies for a specific runtime (in this example, Ubuntu 18.04):</span></span>

  ```dotnetcli
  dotnet build --runtime ubuntu.18.04-x64
  ```

- <span data-ttu-id="23695-176">Vytvořte projekt a použijte zadaný zdroj balíčku NuGet během operace obnovení (sada SDK.NET Core 2.0 a novější verze):</span><span class="sxs-lookup"><span data-stu-id="23695-176">Build the project and use the specified NuGet package source during the restore operation (.NET Core 2.0 SDK and later versions):</span></span>

  ```dotnetcli
  dotnet build --source c:\packages\mypackages
  ```

- <span data-ttu-id="23695-177">Vytvořte projekt a nastavte verzi 1.2.3.4 `-p` jako parametr sestavení pomocí [možnosti MSBuild](#msbuild):</span><span class="sxs-lookup"><span data-stu-id="23695-177">Build the project and set version 1.2.3.4 as a build parameter using the `-p` [MSBuild option](#msbuild):</span></span>

  ```dotnetcli
  dotnet build -p:Version=1.2.3.4
  ```
