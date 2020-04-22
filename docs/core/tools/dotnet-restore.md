---
title: dotnet obnovit, příkaz
description: Pomocí příkazu dotnet restore se dozvíte, jak obnovit závislosti a nástroje specifické pro projekt.
ms.date: 02/27/2020
ms.openlocfilehash: c5cc9adf1d77b0ab03a61cc315d42c2f38362ad9
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021783"
---
# <a name="dotnet-restore"></a><span data-ttu-id="0e143-103">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="0e143-103">dotnet restore</span></span>

<span data-ttu-id="0e143-104">**Tento článek se týká:** ✔️ .NET Core 2.1 SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="0e143-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="0e143-105">Název</span><span class="sxs-lookup"><span data-stu-id="0e143-105">Name</span></span>

<span data-ttu-id="0e143-106">`dotnet restore`- Obnoví závislosti a nástroje projektu.</span><span class="sxs-lookup"><span data-stu-id="0e143-106">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0e143-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="0e143-107">Synopsis</span></span>

```dotnetcli
dotnet restore [<ROOT>] [--configfile <FILE>] [--disable-parallel]
    [-f|--force] [--force-evaluate] [--ignore-failed-sources]
    [--interactive] [--lock-file-path <LOCK_FILE_PATH>] [--locked-mode]
    [--no-cache] [--no-dependencies] [--packages <PACKAGES_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-s|--source <SOURCE>]
    [--use-lockfile] [-v|--verbosity <LEVEL>]

dotnet restore -h|--help
```

## <a name="description"></a><span data-ttu-id="0e143-108">Popis</span><span class="sxs-lookup"><span data-stu-id="0e143-108">Description</span></span>

<span data-ttu-id="0e143-109">Příkaz `dotnet restore` používá NuGet k obnovení závislostí, stejně jako nástroje specifické pro projekt, které jsou zadány v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="0e143-109">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span> <span data-ttu-id="0e143-110">Ve výchozím nastavení jsou obnovení závislostí a nástrojů spouštěny paralelně.</span><span class="sxs-lookup"><span data-stu-id="0e143-110">By default, the restoration of dependencies and tools are executed in parallel.</span></span>

<span data-ttu-id="0e143-111">Chcete-li obnovit závislosti, NuGet potřebuje kanály, kde jsou umístěny balíčky.</span><span class="sxs-lookup"><span data-stu-id="0e143-111">To restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="0e143-112">Informační kanály jsou obvykle poskytovány prostřednictvím konfiguračního souboru *nuget.config.*</span><span class="sxs-lookup"><span data-stu-id="0e143-112">Feeds are usually provided via the *nuget.config* configuration file.</span></span> <span data-ttu-id="0e143-113">Při instalaci sady .NET Core SDK je k dispozici výchozí konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="0e143-113">A default configuration file is provided when the .NET Core SDK is installed.</span></span> <span data-ttu-id="0e143-114">Další informační kanály zadáte vytvořením vlastního souboru *nuget.config* v adresáři projektu.</span><span class="sxs-lookup"><span data-stu-id="0e143-114">You specify additional feeds by creating your own *nuget.config* file in the project directory.</span></span> <span data-ttu-id="0e143-115">Kanály *nuget.config* můžete přepsat pomocí `-s` možnosti - .</span><span class="sxs-lookup"><span data-stu-id="0e143-115">You can override the *nuget.config* feeds with the - `-s` option.</span></span>

<span data-ttu-id="0e143-116">U závislostí určíte, kam budou obnovené balíčky umístěny během operace obnovení pomocí argumentu. `--packages`</span><span class="sxs-lookup"><span data-stu-id="0e143-116">For dependencies, you specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="0e143-117">Pokud není zadán, je použita výchozí mezipaměť balíčku `.nuget/packages` NuGet, která se nachází v adresáři v domovském adresáři uživatele ve všech operačních systémech.</span><span class="sxs-lookup"><span data-stu-id="0e143-117">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems.</span></span> <span data-ttu-id="0e143-118">Například */home/user1* v Systému Linux nebo *C:\Users\user1* v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="0e143-118">For example, */home/user1* on Linux or *C:\Users\user1* on Windows.</span></span>

<span data-ttu-id="0e143-119">Pro nástroje specifické pro `dotnet restore` projekt nejprve obnoví balíček, ve kterém je nástroj zabalen a potom pokračuje obnovit závislosti nástroje, jak je uvedeno v jeho souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="0e143-119">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

### <a name="nugetconfig-differences"></a><span data-ttu-id="0e143-120">nuget.config rozdíly</span><span class="sxs-lookup"><span data-stu-id="0e143-120">nuget.config differences</span></span>

<span data-ttu-id="0e143-121">Chování příkazu `dotnet restore` je ovlivněno nastavením v souboru *nuget.config,* pokud je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="0e143-121">The behavior of the `dotnet restore` command is affected by the settings in the *nuget.config* file, if present.</span></span> <span data-ttu-id="0e143-122">Například nastavení `globalPackagesFolder` v *nuget.config* umístí obnovené balíčky NuGet do zadané složky.</span><span class="sxs-lookup"><span data-stu-id="0e143-122">For example, setting the `globalPackagesFolder` in *nuget.config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="0e143-123">Toto je alternativa `--packages` k určení `dotnet restore` možnosti v příkazu.</span><span class="sxs-lookup"><span data-stu-id="0e143-123">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="0e143-124">Další informace naleznete v [odkazu nuget.config](/nuget/schema/nuget-config-file).</span><span class="sxs-lookup"><span data-stu-id="0e143-124">For more information, see the [nuget.config reference](/nuget/schema/nuget-config-file).</span></span>

<span data-ttu-id="0e143-125">Existují tři konkrétní `dotnet restore` nastavení, která ignorují:</span><span class="sxs-lookup"><span data-stu-id="0e143-125">There are three specific settings that `dotnet restore` ignores:</span></span>

- [<span data-ttu-id="0e143-126">vazbyPřesměrování</span><span class="sxs-lookup"><span data-stu-id="0e143-126">bindingRedirects</span></span>](/nuget/schema/nuget-config-file#bindingredirects-section)

  <span data-ttu-id="0e143-127">Přesměrování vazby nefungují s `<PackageReference>` prvky a .NET Core podporuje `<PackageReference>` pouze prvky pro balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="0e143-127">Binding redirects don't work with `<PackageReference>` elements and .NET Core only supports `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="0e143-128">Řešení</span><span class="sxs-lookup"><span data-stu-id="0e143-128">solution</span></span>](/nuget/schema/nuget-config-file#solution-section)

  <span data-ttu-id="0e143-129">Toto nastavení je specifické pro visual studio a nevztahuje se na jádro .NET.</span><span class="sxs-lookup"><span data-stu-id="0e143-129">This setting is Visual Studio specific and doesn't apply to .NET Core.</span></span> <span data-ttu-id="0e143-130">.NET Core nepoužívá `packages.config` soubor a místo `<PackageReference>` toho používá prvky pro balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="0e143-130">.NET Core doesn't use a `packages.config` file and instead uses `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="0e143-131">důvěryhodní podepisující</span><span class="sxs-lookup"><span data-stu-id="0e143-131">trustedSigners</span></span>](/nuget/schema/nuget-config-file#trustedsigners-section)

  <span data-ttu-id="0e143-132">Toto nastavení není použitelné, protože [NuGet ještě nepodporuje ověřování](https://github.com/NuGet/Home/issues/7939) důvěryhodných balíčků napříč platformami.</span><span class="sxs-lookup"><span data-stu-id="0e143-132">This setting isn't applicable as [NuGet doesn't yet support cross-platform verification](https://github.com/NuGet/Home/issues/7939) of trusted packages.</span></span>

## <a name="implicit-restore"></a><span data-ttu-id="0e143-133">Implicitní obnovení</span><span class="sxs-lookup"><span data-stu-id="0e143-133">Implicit restore</span></span>

<span data-ttu-id="0e143-134">Příkaz `dotnet restore` je spuštěn implicitně v případě potřeby při spuštění následujících příkazů:</span><span class="sxs-lookup"><span data-stu-id="0e143-134">The `dotnet restore` command is run implicitly if necessary when you run the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="0e143-135">Ve většině případů není nutné explicitně `dotnet restore` použít příkaz.</span><span class="sxs-lookup"><span data-stu-id="0e143-135">In most cases, you don't need to explicitly use the `dotnet restore` command.</span></span>

<span data-ttu-id="0e143-136">Někdy může být nepohodlné `dotnet restore` spustit implicitně.</span><span class="sxs-lookup"><span data-stu-id="0e143-136">Sometimes, it might be inconvenient to run `dotnet restore` implicitly.</span></span> <span data-ttu-id="0e143-137">Například některé automatizované systémy, jako jsou systémy `dotnet restore` sestavení, musí explicitně volat, aby řídily, kdy dojde k obnovení, aby mohly řídit využití sítě.</span><span class="sxs-lookup"><span data-stu-id="0e143-137">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="0e143-138">Chcete-li zabránit `dotnet restore` spuštění implicitně, `--no-restore` můžete použít příznak s některou z těchto příkazů zakázat implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="0e143-138">To prevent `dotnet restore` from running implicitly, you can use the `--no-restore` flag with any of these commands to disable implicit restore.</span></span>

## <a name="arguments"></a><span data-ttu-id="0e143-139">Argumenty</span><span class="sxs-lookup"><span data-stu-id="0e143-139">Arguments</span></span>

- **`ROOT`**

  <span data-ttu-id="0e143-140">Volitelná cesta k souboru projektu k obnovení.</span><span class="sxs-lookup"><span data-stu-id="0e143-140">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="0e143-141">Možnosti</span><span class="sxs-lookup"><span data-stu-id="0e143-141">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="0e143-142">Konfigurační soubor NuGet *(nuget.config),* který se má použít pro operaci obnovení.</span><span class="sxs-lookup"><span data-stu-id="0e143-142">The NuGet configuration file (*nuget.config*) to use for the restore operation.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="0e143-143">Zakáže obnovení více projektů paralelně.</span><span class="sxs-lookup"><span data-stu-id="0e143-143">Disables restoring multiple projects in parallel.</span></span>

- **`--force`**

  <span data-ttu-id="0e143-144">Vynutí vyřešení všech závislostí, i když bylo poslední obnovení úspěšné.</span><span class="sxs-lookup"><span data-stu-id="0e143-144">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="0e143-145">Zadání tohoto příznaku je stejné jako odstranění souboru *project.assets.json.*</span><span class="sxs-lookup"><span data-stu-id="0e143-145">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`--force-evaluate`**

  <span data-ttu-id="0e143-146">Vynutí obnovení přehodnotit všechny závislosti i v případě, že soubor zámku již existuje.</span><span class="sxs-lookup"><span data-stu-id="0e143-146">Forces restore to reevaluate all dependencies even if a lock file already exists.</span></span>

- **`-h|--help`**

  <span data-ttu-id="0e143-147">Vytiskne krátkou nápovědu pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="0e143-147">Prints out a short help for the command.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="0e143-148">Pouze upozornit na zdroje selhání, pokud existují balíčky splňující požadavek na verzi.</span><span class="sxs-lookup"><span data-stu-id="0e143-148">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

- **`--interactive`**

  <span data-ttu-id="0e143-149">Umožňuje příkazu zastavit a čekat na vstup uživatele nebo akci (například k dokončení ověřování).</span><span class="sxs-lookup"><span data-stu-id="0e143-149">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span> <span data-ttu-id="0e143-150">Od .NET Core 2.1.400.</span><span class="sxs-lookup"><span data-stu-id="0e143-150">Since .NET Core 2.1.400.</span></span>

- **`--lock-file-path <LOCK_FILE_PATH>`**

  <span data-ttu-id="0e143-151">Výstupní umístění, kde je zapsán soubor zámku projektu.</span><span class="sxs-lookup"><span data-stu-id="0e143-151">Output location where project lock file is written.</span></span> <span data-ttu-id="0e143-152">Ve výchozím nastavení se jedná *o soubor PROJECT_ROOT\packages.lock.json*.</span><span class="sxs-lookup"><span data-stu-id="0e143-152">By default, this is *PROJECT_ROOT\packages.lock.json*.</span></span>

- **`--locked-mode`**

  <span data-ttu-id="0e143-153">Nepovoluj aktualizaci souboru zámku projektu.</span><span class="sxs-lookup"><span data-stu-id="0e143-153">Don't allow updating project lock file.</span></span>

- **`--no-cache`**

  <span data-ttu-id="0e143-154">Určuje, že se nemají ukládat do mezipaměti požadavky HTTP.</span><span class="sxs-lookup"><span data-stu-id="0e143-154">Specifies to not cache HTTP requests.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="0e143-155">Při obnovení projektu s odkazy projekt-projekt (P2P) obnoví kořenový projekt a nikoli odkazy.</span><span class="sxs-lookup"><span data-stu-id="0e143-155">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

- **`--packages <PACKAGES_DIRECTORY>`**

  <span data-ttu-id="0e143-156">Určuje adresář pro obnovené balíčky.</span><span class="sxs-lookup"><span data-stu-id="0e143-156">Specifies the directory for restored packages.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="0e143-157">Určuje dobu runtime pro obnovení balíčku.</span><span class="sxs-lookup"><span data-stu-id="0e143-157">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="0e143-158">Používá se k obnovení balíčků pro runtimes, které nejsou výslovně uvedeny ve značce `<RuntimeIdentifiers>` v souboru *.csproj.*</span><span class="sxs-lookup"><span data-stu-id="0e143-158">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="0e143-159">Seznam identifikátorů modulu Runtime (RID) naleznete v [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="0e143-159">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="0e143-160">Zadejte více ridů zadáním této možnosti vícekrát.</span><span class="sxs-lookup"><span data-stu-id="0e143-160">Provide multiple RIDs by specifying this option multiple times.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="0e143-161">Určuje zdroj balíčku NuGet, který se má použít během operace obnovení.</span><span class="sxs-lookup"><span data-stu-id="0e143-161">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="0e143-162">Toto nastavení přepíše všechny zdroje zadané v souborech *nuget.config.*</span><span class="sxs-lookup"><span data-stu-id="0e143-162">This setting overrides all of the sources specified in the *nuget.config* files.</span></span> <span data-ttu-id="0e143-163">Zadáním této možnosti vícekrát lze poskytnout více zdrojů.</span><span class="sxs-lookup"><span data-stu-id="0e143-163">Multiple sources can be provided by specifying this option multiple times.</span></span>

- **`--use-lockfile`**

  <span data-ttu-id="0e143-164">Umožňuje generovat a používat soubor zámku projektu s obnovením.</span><span class="sxs-lookup"><span data-stu-id="0e143-164">Enables project lock file to be generated and used with restore.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="0e143-165">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="0e143-165">Sets the verbosity level of the command.</span></span> <span data-ttu-id="0e143-166">Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a .</span><span class="sxs-lookup"><span data-stu-id="0e143-166">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="0e143-167">Výchozí hodnota `minimal`je .</span><span class="sxs-lookup"><span data-stu-id="0e143-167">Default value is `minimal`.</span></span>

## <a name="examples"></a><span data-ttu-id="0e143-168">Příklady</span><span class="sxs-lookup"><span data-stu-id="0e143-168">Examples</span></span>

- <span data-ttu-id="0e143-169">Obnovení závislostí a nástrojů pro projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="0e143-169">Restore dependencies and tools for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet restore
  ```

- <span data-ttu-id="0e143-170">Obnovit závislosti a nástroje `app1` pro projekt nalezený v dané cestě:</span><span class="sxs-lookup"><span data-stu-id="0e143-170">Restore dependencies and tools for the `app1` project found in the   given path:</span></span>

  ```dotnetcli
  dotnet restore ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="0e143-171">Obnovte závislosti a nástroje pro projekt v aktuálním adresáři pomocí cesty k souboru, která je k dispozici jako zdroj:</span><span class="sxs-lookup"><span data-stu-id="0e143-171">Restore the dependencies and tools for the project in the current   directory using the file path provided as the source:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages
  ```

- <span data-ttu-id="0e143-172">Obnovte závislosti a nástroje pro projekt v aktuálním adresáři pomocí dvou cest k souborům, které jsou k dispozici jako zdroje:</span><span class="sxs-lookup"><span data-stu-id="0e143-172">Restore the dependencies and tools for the project in the current   directory using the two file paths provided as sources:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages
  ```

- <span data-ttu-id="0e143-173">Obnovení závislostí a nástrojů pro projekt v aktuálním adresáři zobrazujícího podrobný výstup:</span><span class="sxs-lookup"><span data-stu-id="0e143-173">Restore dependencies and tools for the project in the current directory   showing detailed output:</span></span>

  ```dotnetcli
  dotnet restore --verbosity detailed
  ```
