---
title: dotnet obnovit, příkaz
description: Pomocí příkazu dotnet restore se dozvíte, jak obnovit závislosti a nástroje specifické pro projekt.
ms.date: 02/27/2020
ms.openlocfilehash: 3deef68a9bcee389a52291c72e7e1a1019a739fd
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102785"
---
# <a name="dotnet-restore"></a><span data-ttu-id="7faba-103">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="7faba-103">dotnet restore</span></span>

<span data-ttu-id="7faba-104">**Tento článek se týká:** ✔️ .NET Core 2.1 SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="7faba-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="7faba-105">Název</span><span class="sxs-lookup"><span data-stu-id="7faba-105">Name</span></span>

<span data-ttu-id="7faba-106">`dotnet restore`- Obnoví závislosti a nástroje projektu.</span><span class="sxs-lookup"><span data-stu-id="7faba-106">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="7faba-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="7faba-107">Synopsis</span></span>

```dotnetcli
dotnet restore [<ROOT>] [--configfile <FILE>] [--disable-parallel]
    [-f|--force] [--force-evaluate] [--ignore-failed-sources]
    [--interactive] [--lock-file-path <LOCK_FILE_PATH>] [--locked-mode]
    [--no-cache] [--no-dependencies] [--packages <PACKAGES_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-s|--source <SOURCE>]
    [--use-lockfile] [-v|--verbosity <LEVEL>]

dotnet restore -h|--help
```

## <a name="description"></a><span data-ttu-id="7faba-108">Popis</span><span class="sxs-lookup"><span data-stu-id="7faba-108">Description</span></span>

<span data-ttu-id="7faba-109">Příkaz `dotnet restore` používá NuGet k obnovení závislostí, stejně jako nástroje specifické pro projekt, které jsou zadány v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="7faba-109">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span> <span data-ttu-id="7faba-110">Ve výchozím nastavení jsou obnovení závislostí a nástrojů spouštěny paralelně.</span><span class="sxs-lookup"><span data-stu-id="7faba-110">By default, the restoration of dependencies and tools are executed in parallel.</span></span>

### <a name="specify-feeds"></a><span data-ttu-id="7faba-111">Určení informačních kanálů</span><span class="sxs-lookup"><span data-stu-id="7faba-111">Specify feeds</span></span>

<span data-ttu-id="7faba-112">Chcete-li obnovit závislosti, NuGet potřebuje kanály, kde jsou umístěny balíčky.</span><span class="sxs-lookup"><span data-stu-id="7faba-112">To restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="7faba-113">Informační kanály jsou obvykle poskytovány prostřednictvím konfiguračního souboru *nuget.config.*</span><span class="sxs-lookup"><span data-stu-id="7faba-113">Feeds are usually provided via the *nuget.config* configuration file.</span></span> <span data-ttu-id="7faba-114">Při instalaci sady .NET Core SDK je k dispozici výchozí konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="7faba-114">A default configuration file is provided when the .NET Core SDK is installed.</span></span> <span data-ttu-id="7faba-115">Chcete-li zadat další informační kanály, proveďte jeden z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="7faba-115">To specify additional feeds, do one of the following:</span></span>

- <span data-ttu-id="7faba-116">Vytvořte si vlastní soubor *nuget.config* v adresáři projektu.</span><span class="sxs-lookup"><span data-stu-id="7faba-116">Create your own *nuget.config* file in the project directory.</span></span> <span data-ttu-id="7faba-117">Další informace naleznete [v tématu Běžné konfigurace NuGet](/nuget/consume-packages/configuring-nuget-behavior) a [nuget.config rozdíly](#nugetconfig-differences) dále v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="7faba-117">For more information, see [Common NuGet configurations](/nuget/consume-packages/configuring-nuget-behavior) and [nuget.config differences](#nugetconfig-differences) later in this article.</span></span>
- <span data-ttu-id="7faba-118">Používejte `dotnet nuget` příkazy, [`dotnet nuget add source`](dotnet-nuget-add-source.md)například .</span><span class="sxs-lookup"><span data-stu-id="7faba-118">Use `dotnet nuget` commands such as [`dotnet nuget add source`](dotnet-nuget-add-source.md).</span></span>

<span data-ttu-id="7faba-119">Kanály *nuget.config* můžete přepsat pomocí `-s` možnosti.</span><span class="sxs-lookup"><span data-stu-id="7faba-119">You can override the *nuget.config* feeds with the `-s` option.</span></span>

<span data-ttu-id="7faba-120">Informace o použití ověřených informačních kanálů naleznete v [tématu Náročné balíčky z ověřených informačních kanálů](/nuget/consume-packages/consuming-packages-authenticated-feeds).</span><span class="sxs-lookup"><span data-stu-id="7faba-120">For information about how to use authenticated feeds, see [Consuming packages from authenticated feeds](/nuget/consume-packages/consuming-packages-authenticated-feeds).</span></span>

### <a name="package-cache"></a><span data-ttu-id="7faba-121">Mezipaměť balíčků</span><span class="sxs-lookup"><span data-stu-id="7faba-121">Package cache</span></span>

<span data-ttu-id="7faba-122">U závislostí určíte, kam budou obnovené balíčky umístěny během operace obnovení pomocí argumentu. `--packages`</span><span class="sxs-lookup"><span data-stu-id="7faba-122">For dependencies, you specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="7faba-123">Pokud není zadán, je použita výchozí mezipaměť balíčku `.nuget/packages` NuGet, která se nachází v adresáři v domovském adresáři uživatele ve všech operačních systémech.</span><span class="sxs-lookup"><span data-stu-id="7faba-123">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems.</span></span> <span data-ttu-id="7faba-124">Například */home/user1* v Systému Linux nebo *C:\Users\user1* v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="7faba-124">For example, */home/user1* on Linux or *C:\Users\user1* on Windows.</span></span>

### <a name="project-specific-tooling"></a><span data-ttu-id="7faba-125">Nástroje specifické pro projekt</span><span class="sxs-lookup"><span data-stu-id="7faba-125">Project-specific tooling</span></span>

<span data-ttu-id="7faba-126">Pro nástroje specifické pro `dotnet restore` projekt nejprve obnoví balíček, ve kterém je nástroj zabalen a potom pokračuje obnovit závislosti nástroje, jak je uvedeno v jeho souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="7faba-126">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

### <a name="nugetconfig-differences"></a><span data-ttu-id="7faba-127">nuget.config rozdíly</span><span class="sxs-lookup"><span data-stu-id="7faba-127">nuget.config differences</span></span>

<span data-ttu-id="7faba-128">Chování příkazu `dotnet restore` je ovlivněno nastavením v souboru *nuget.config,* pokud je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="7faba-128">The behavior of the `dotnet restore` command is affected by the settings in the *nuget.config* file, if present.</span></span> <span data-ttu-id="7faba-129">Například nastavení `globalPackagesFolder` v *nuget.config* umístí obnovené balíčky NuGet do zadané složky.</span><span class="sxs-lookup"><span data-stu-id="7faba-129">For example, setting the `globalPackagesFolder` in *nuget.config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="7faba-130">Toto je alternativa `--packages` k určení `dotnet restore` možnosti v příkazu.</span><span class="sxs-lookup"><span data-stu-id="7faba-130">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="7faba-131">Další informace naleznete v [odkazu nuget.config](/nuget/schema/nuget-config-file).</span><span class="sxs-lookup"><span data-stu-id="7faba-131">For more information, see the [nuget.config reference](/nuget/schema/nuget-config-file).</span></span>

<span data-ttu-id="7faba-132">Existují tři konkrétní `dotnet restore` nastavení, která ignorují:</span><span class="sxs-lookup"><span data-stu-id="7faba-132">There are three specific settings that `dotnet restore` ignores:</span></span>

- [<span data-ttu-id="7faba-133">vazbyPřesměrování</span><span class="sxs-lookup"><span data-stu-id="7faba-133">bindingRedirects</span></span>](/nuget/schema/nuget-config-file#bindingredirects-section)

  <span data-ttu-id="7faba-134">Přesměrování vazby nefungují s `<PackageReference>` prvky a .NET Core podporuje `<PackageReference>` pouze prvky pro balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="7faba-134">Binding redirects don't work with `<PackageReference>` elements and .NET Core only supports `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="7faba-135">Řešení</span><span class="sxs-lookup"><span data-stu-id="7faba-135">solution</span></span>](/nuget/schema/nuget-config-file#solution-section)

  <span data-ttu-id="7faba-136">Toto nastavení je specifické pro visual studio a nevztahuje se na jádro .NET.</span><span class="sxs-lookup"><span data-stu-id="7faba-136">This setting is Visual Studio specific and doesn't apply to .NET Core.</span></span> <span data-ttu-id="7faba-137">.NET Core nepoužívá `packages.config` soubor a místo `<PackageReference>` toho používá prvky pro balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="7faba-137">.NET Core doesn't use a `packages.config` file and instead uses `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="7faba-138">důvěryhodní podepisující</span><span class="sxs-lookup"><span data-stu-id="7faba-138">trustedSigners</span></span>](/nuget/schema/nuget-config-file#trustedsigners-section)

  <span data-ttu-id="7faba-139">Toto nastavení není použitelné, protože [NuGet ještě nepodporuje ověřování](https://github.com/NuGet/Home/issues/7939) důvěryhodných balíčků napříč platformami.</span><span class="sxs-lookup"><span data-stu-id="7faba-139">This setting isn't applicable as [NuGet doesn't yet support cross-platform verification](https://github.com/NuGet/Home/issues/7939) of trusted packages.</span></span>

## <a name="implicit-restore"></a><span data-ttu-id="7faba-140">Implicitní obnovení</span><span class="sxs-lookup"><span data-stu-id="7faba-140">Implicit restore</span></span>

<span data-ttu-id="7faba-141">Příkaz `dotnet restore` je spuštěn implicitně v případě potřeby při spuštění následujících příkazů:</span><span class="sxs-lookup"><span data-stu-id="7faba-141">The `dotnet restore` command is run implicitly if necessary when you run the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="7faba-142">Ve většině případů není nutné explicitně `dotnet restore` použít příkaz.</span><span class="sxs-lookup"><span data-stu-id="7faba-142">In most cases, you don't need to explicitly use the `dotnet restore` command.</span></span>

<span data-ttu-id="7faba-143">Někdy může být nepohodlné `dotnet restore` spustit implicitně.</span><span class="sxs-lookup"><span data-stu-id="7faba-143">Sometimes, it might be inconvenient to run `dotnet restore` implicitly.</span></span> <span data-ttu-id="7faba-144">Například některé automatizované systémy, jako jsou systémy `dotnet restore` sestavení, musí explicitně volat, aby řídily, kdy dojde k obnovení, aby mohly řídit využití sítě.</span><span class="sxs-lookup"><span data-stu-id="7faba-144">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="7faba-145">Chcete-li zabránit `dotnet restore` spuštění implicitně, `--no-restore` můžete použít příznak s některou z těchto příkazů zakázat implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="7faba-145">To prevent `dotnet restore` from running implicitly, you can use the `--no-restore` flag with any of these commands to disable implicit restore.</span></span>

## <a name="arguments"></a><span data-ttu-id="7faba-146">Argumenty</span><span class="sxs-lookup"><span data-stu-id="7faba-146">Arguments</span></span>

- **`ROOT`**

  <span data-ttu-id="7faba-147">Volitelná cesta k souboru projektu k obnovení.</span><span class="sxs-lookup"><span data-stu-id="7faba-147">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="7faba-148">Možnosti</span><span class="sxs-lookup"><span data-stu-id="7faba-148">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="7faba-149">Konfigurační soubor NuGet *(nuget.config),* který se má použít pro operaci obnovení.</span><span class="sxs-lookup"><span data-stu-id="7faba-149">The NuGet configuration file (*nuget.config*) to use for the restore operation.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="7faba-150">Zakáže obnovení více projektů paralelně.</span><span class="sxs-lookup"><span data-stu-id="7faba-150">Disables restoring multiple projects in parallel.</span></span>

- **`--force`**

  <span data-ttu-id="7faba-151">Vynutí vyřešení všech závislostí, i když bylo poslední obnovení úspěšné.</span><span class="sxs-lookup"><span data-stu-id="7faba-151">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="7faba-152">Zadání tohoto příznaku je stejné jako odstranění souboru *project.assets.json.*</span><span class="sxs-lookup"><span data-stu-id="7faba-152">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`--force-evaluate`**

  <span data-ttu-id="7faba-153">Vynutí obnovení přehodnotit všechny závislosti i v případě, že soubor zámku již existuje.</span><span class="sxs-lookup"><span data-stu-id="7faba-153">Forces restore to reevaluate all dependencies even if a lock file already exists.</span></span>

- **`-h|--help`**

  <span data-ttu-id="7faba-154">Vytiskne krátkou nápovědu pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="7faba-154">Prints out a short help for the command.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="7faba-155">Pouze upozornit na zdroje selhání, pokud existují balíčky splňující požadavek na verzi.</span><span class="sxs-lookup"><span data-stu-id="7faba-155">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

- **`--interactive`**

  <span data-ttu-id="7faba-156">Umožňuje příkazu zastavit a čekat na vstup uživatele nebo akci (například k dokončení ověřování).</span><span class="sxs-lookup"><span data-stu-id="7faba-156">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span> <span data-ttu-id="7faba-157">Od .NET Core 2.1.400.</span><span class="sxs-lookup"><span data-stu-id="7faba-157">Since .NET Core 2.1.400.</span></span>

- **`--lock-file-path <LOCK_FILE_PATH>`**

  <span data-ttu-id="7faba-158">Výstupní umístění, kde je zapsán soubor zámku projektu.</span><span class="sxs-lookup"><span data-stu-id="7faba-158">Output location where project lock file is written.</span></span> <span data-ttu-id="7faba-159">Ve výchozím nastavení se jedná *o soubor PROJECT_ROOT\packages.lock.json*.</span><span class="sxs-lookup"><span data-stu-id="7faba-159">By default, this is *PROJECT_ROOT\packages.lock.json*.</span></span>

- **`--locked-mode`**

  <span data-ttu-id="7faba-160">Nepovoluj aktualizaci souboru zámku projektu.</span><span class="sxs-lookup"><span data-stu-id="7faba-160">Don't allow updating project lock file.</span></span>

- **`--no-cache`**

  <span data-ttu-id="7faba-161">Určuje, že se nemají ukládat do mezipaměti požadavky HTTP.</span><span class="sxs-lookup"><span data-stu-id="7faba-161">Specifies to not cache HTTP requests.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="7faba-162">Při obnovení projektu s odkazy projekt-projekt (P2P) obnoví kořenový projekt a nikoli odkazy.</span><span class="sxs-lookup"><span data-stu-id="7faba-162">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

- **`--packages <PACKAGES_DIRECTORY>`**

  <span data-ttu-id="7faba-163">Určuje adresář pro obnovené balíčky.</span><span class="sxs-lookup"><span data-stu-id="7faba-163">Specifies the directory for restored packages.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="7faba-164">Určuje dobu runtime pro obnovení balíčku.</span><span class="sxs-lookup"><span data-stu-id="7faba-164">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="7faba-165">Používá se k obnovení balíčků pro runtimes, které nejsou výslovně uvedeny ve značce `<RuntimeIdentifiers>` v souboru *.csproj.*</span><span class="sxs-lookup"><span data-stu-id="7faba-165">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="7faba-166">Seznam identifikátorů modulu Runtime (RID) naleznete v [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="7faba-166">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="7faba-167">Zadejte více ridů zadáním této možnosti vícekrát.</span><span class="sxs-lookup"><span data-stu-id="7faba-167">Provide multiple RIDs by specifying this option multiple times.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="7faba-168">Určuje zdroj balíčku NuGet, který se má použít během operace obnovení.</span><span class="sxs-lookup"><span data-stu-id="7faba-168">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="7faba-169">Toto nastavení přepíše všechny zdroje zadané v souborech *nuget.config.*</span><span class="sxs-lookup"><span data-stu-id="7faba-169">This setting overrides all of the sources specified in the *nuget.config* files.</span></span> <span data-ttu-id="7faba-170">Zadáním této možnosti vícekrát lze poskytnout více zdrojů.</span><span class="sxs-lookup"><span data-stu-id="7faba-170">Multiple sources can be provided by specifying this option multiple times.</span></span>

- **`--use-lockfile`**

  <span data-ttu-id="7faba-171">Umožňuje generovat a používat soubor zámku projektu s obnovením.</span><span class="sxs-lookup"><span data-stu-id="7faba-171">Enables project lock file to be generated and used with restore.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="7faba-172">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="7faba-172">Sets the verbosity level of the command.</span></span> <span data-ttu-id="7faba-173">Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a .</span><span class="sxs-lookup"><span data-stu-id="7faba-173">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="7faba-174">Výchozí hodnota `minimal`je .</span><span class="sxs-lookup"><span data-stu-id="7faba-174">Default value is `minimal`.</span></span>

## <a name="examples"></a><span data-ttu-id="7faba-175">Příklady</span><span class="sxs-lookup"><span data-stu-id="7faba-175">Examples</span></span>

- <span data-ttu-id="7faba-176">Obnovení závislostí a nástrojů pro projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="7faba-176">Restore dependencies and tools for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet restore
  ```

- <span data-ttu-id="7faba-177">Obnovit závislosti a nástroje `app1` pro projekt nalezený v dané cestě:</span><span class="sxs-lookup"><span data-stu-id="7faba-177">Restore dependencies and tools for the `app1` project found in the   given path:</span></span>

  ```dotnetcli
  dotnet restore ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="7faba-178">Obnovte závislosti a nástroje pro projekt v aktuálním adresáři pomocí cesty k souboru, která je k dispozici jako zdroj:</span><span class="sxs-lookup"><span data-stu-id="7faba-178">Restore the dependencies and tools for the project in the current   directory using the file path provided as the source:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages
  ```

- <span data-ttu-id="7faba-179">Obnovte závislosti a nástroje pro projekt v aktuálním adresáři pomocí dvou cest k souborům, které jsou k dispozici jako zdroje:</span><span class="sxs-lookup"><span data-stu-id="7faba-179">Restore the dependencies and tools for the project in the current   directory using the two file paths provided as sources:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages
  ```

- <span data-ttu-id="7faba-180">Obnovení závislostí a nástrojů pro projekt v aktuálním adresáři zobrazujícího podrobný výstup:</span><span class="sxs-lookup"><span data-stu-id="7faba-180">Restore dependencies and tools for the project in the current directory   showing detailed output:</span></span>

  ```dotnetcli
  dotnet restore --verbosity detailed
  ```
