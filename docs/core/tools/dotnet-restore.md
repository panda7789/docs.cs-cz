---
title: dotnet restore – příkaz
description: Naučte se obnovit závislosti a nástroje specifické pro projekt pomocí příkazu dotnet restore.
ms.date: 02/27/2020
ms.openlocfilehash: cc8f374468ba95baccf058ac0b0a0175672cdf01
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158304"
---
# <a name="dotnet-restore"></a><span data-ttu-id="cea68-103">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="cea68-103">dotnet restore</span></span>

<span data-ttu-id="cea68-104">**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="cea68-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="cea68-105">Název</span><span class="sxs-lookup"><span data-stu-id="cea68-105">Name</span></span>

<span data-ttu-id="cea68-106">`dotnet restore`– Obnoví závislosti a nástroje projektu.</span><span class="sxs-lookup"><span data-stu-id="cea68-106">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="cea68-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="cea68-107">Synopsis</span></span>

```dotnetcli
dotnet restore [<ROOT>] [--configfile <FILE>] [--disable-parallel]
    [-f|--force] [--force-evaluate] [--ignore-failed-sources]
    [--interactive] [--lock-file-path <LOCK_FILE_PATH>] [--locked-mode]
    [--no-cache] [--no-dependencies] [--packages <PACKAGES_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-s|--source <SOURCE>]
    [--use-lockfile] [-v|--verbosity <LEVEL>]

dotnet restore -h|--help
```

## <a name="description"></a><span data-ttu-id="cea68-108">Popis</span><span class="sxs-lookup"><span data-stu-id="cea68-108">Description</span></span>

<span data-ttu-id="cea68-109">`dotnet restore` Příkaz používá NuGet k obnovení závislostí a také nástrojů specifických pro projekt, které jsou uvedeny v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="cea68-109">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span>  <span data-ttu-id="cea68-110">Ve většině případů nemusíte explicitně používat `dotnet restore` příkaz, protože obnovení NuGet se v případě potřeby spouští implicitně, když spustíte následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="cea68-110">In most cases, you don't need to explicitly use the `dotnet restore` command, since a NuGet restore is run implicitly if necessary when you run the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="cea68-111">V některých případech může být nepraktické spustit implicitní obnovení NuGet pomocí těchto příkazů.</span><span class="sxs-lookup"><span data-stu-id="cea68-111">Sometimes, it might be inconvenient to run the implicit NuGet restore with these commands.</span></span> <span data-ttu-id="cea68-112">Například některé automatizované systémy, například systémy sestavení, musí volat `dotnet restore` explicitně k řízení, když dojde k obnovení, aby bylo možné řídit využití sítě.</span><span class="sxs-lookup"><span data-stu-id="cea68-112">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="cea68-113">Chcete-li zabránit implicitnímu obnovení NuGet, můžete použít `--no-restore` příznak s některým z těchto příkazů k zakázání implicitního obnovení.</span><span class="sxs-lookup"><span data-stu-id="cea68-113">To prevent the implicit NuGet restore, you can use the `--no-restore` flag with any of these commands to disable implicit restore.</span></span>

### <a name="specify-feeds"></a><span data-ttu-id="cea68-114">Zadat informační kanály</span><span class="sxs-lookup"><span data-stu-id="cea68-114">Specify feeds</span></span>

<span data-ttu-id="cea68-115">Pro obnovení závislostí potřebuje NuGet informační kanály, ve kterých se balíčky nacházejí.</span><span class="sxs-lookup"><span data-stu-id="cea68-115">To restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="cea68-116">Informační kanály jsou obvykle poskytovány prostřednictvím konfiguračního souboru *NuGet. config* .</span><span class="sxs-lookup"><span data-stu-id="cea68-116">Feeds are usually provided via the *nuget.config* configuration file.</span></span> <span data-ttu-id="cea68-117">Výchozí konfigurační soubor se poskytne při instalaci .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="cea68-117">A default configuration file is provided when the .NET Core SDK is installed.</span></span> <span data-ttu-id="cea68-118">Chcete-li zadat další informační kanály, proveďte jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="cea68-118">To specify additional feeds, do one of the following:</span></span>

- <span data-ttu-id="cea68-119">Vytvořte vlastní soubor *NuGet. config* v adresáři projektu.</span><span class="sxs-lookup"><span data-stu-id="cea68-119">Create your own *nuget.config* file in the project directory.</span></span> <span data-ttu-id="cea68-120">Další informace najdete v tématu [běžné konfigurace NuGet](/nuget/consume-packages/configuring-nuget-behavior) a [rozdíly v souboru NuGet. config](#nugetconfig-differences) dále v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="cea68-120">For more information, see [Common NuGet configurations](/nuget/consume-packages/configuring-nuget-behavior) and [nuget.config differences](#nugetconfig-differences) later in this article.</span></span>
- <span data-ttu-id="cea68-121">Použijte `dotnet nuget` příkazy, jako [`dotnet nuget add source`](dotnet-nuget-add-source.md)je.</span><span class="sxs-lookup"><span data-stu-id="cea68-121">Use `dotnet nuget` commands such as [`dotnet nuget add source`](dotnet-nuget-add-source.md).</span></span>

<span data-ttu-id="cea68-122">Informační kanály *NuGet. config* můžete přepsat `-s` možností.</span><span class="sxs-lookup"><span data-stu-id="cea68-122">You can override the *nuget.config* feeds with the `-s` option.</span></span>

<span data-ttu-id="cea68-123">Informace o tom, jak používat ověřené informační kanály, najdete v tématu [využívání balíčků ze ověřených informačních kanálů](/nuget/consume-packages/consuming-packages-authenticated-feeds).</span><span class="sxs-lookup"><span data-stu-id="cea68-123">For information about how to use authenticated feeds, see [Consuming packages from authenticated feeds](/nuget/consume-packages/consuming-packages-authenticated-feeds).</span></span>

### <a name="global-packages-folder"></a><span data-ttu-id="cea68-124">Složka globálních balíčků</span><span class="sxs-lookup"><span data-stu-id="cea68-124">Global packages folder</span></span>

<span data-ttu-id="cea68-125">U závislostí můžete určit, kde se obnovené balíčky umístí během operace obnovení pomocí `--packages` argumentu.</span><span class="sxs-lookup"><span data-stu-id="cea68-125">For dependencies, you can specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="cea68-126">Pokud není zadaný, použije se výchozí mezipaměť balíčků NuGet, která se nachází v `.nuget/packages` adresáři domovského adresáře uživatele ve všech operačních systémech.</span><span class="sxs-lookup"><span data-stu-id="cea68-126">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems.</span></span> <span data-ttu-id="cea68-127">Například */Home/user1* v systému Linux nebo *C:\Users\user1* ve Windows.</span><span class="sxs-lookup"><span data-stu-id="cea68-127">For example, */home/user1* on Linux or *C:\Users\user1* on Windows.</span></span>

### <a name="project-specific-tooling"></a><span data-ttu-id="cea68-128">Nástroje specifické pro projekt</span><span class="sxs-lookup"><span data-stu-id="cea68-128">Project-specific tooling</span></span>

<span data-ttu-id="cea68-129">U nástrojů specifických pro projekt `dotnet restore` nejprve obnovte balíček, ve kterém je nástroj zabalen, a poté pokračuje v obnovování závislostí nástroje, jak je uvedeno v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="cea68-129">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

### <a name="nugetconfig-differences"></a><span data-ttu-id="cea68-130">rozdíly v NuGet. config</span><span class="sxs-lookup"><span data-stu-id="cea68-130">nuget.config differences</span></span>

<span data-ttu-id="cea68-131">Chování `dotnet restore` příkazu je ovlivněno nastavením v souboru *NuGet. config* , pokud je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="cea68-131">The behavior of the `dotnet restore` command is affected by the settings in the *nuget.config* file, if present.</span></span> <span data-ttu-id="cea68-132">Například nastavení `globalPackagesFolder` v *souboru NuGet. config* umístí obnovené balíčky NuGet do zadané složky.</span><span class="sxs-lookup"><span data-stu-id="cea68-132">For example, setting the `globalPackagesFolder` in *nuget.config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="cea68-133">Toto je alternativa k zadání `--packages` možnosti `dotnet restore` příkazu.</span><span class="sxs-lookup"><span data-stu-id="cea68-133">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="cea68-134">Další informace najdete v referenčních informacích k [NuGet. config](/nuget/schema/nuget-config-file).</span><span class="sxs-lookup"><span data-stu-id="cea68-134">For more information, see the [nuget.config reference](/nuget/schema/nuget-config-file).</span></span>

<span data-ttu-id="cea68-135">Existují tři specifická nastavení, která `dotnet restore` ignorují:</span><span class="sxs-lookup"><span data-stu-id="cea68-135">There are three specific settings that `dotnet restore` ignores:</span></span>

- [<span data-ttu-id="cea68-136">bindingRedirects</span><span class="sxs-lookup"><span data-stu-id="cea68-136">bindingRedirects</span></span>](/nuget/schema/nuget-config-file#bindingredirects-section)

  <span data-ttu-id="cea68-137">Přesměrování vazby nefungují s `<PackageReference>` prvky a .NET Core podporuje `<PackageReference>` pouze prvky pro balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="cea68-137">Binding redirects don't work with `<PackageReference>` elements and .NET Core only supports `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="cea68-138">řešení</span><span class="sxs-lookup"><span data-stu-id="cea68-138">solution</span></span>](/nuget/schema/nuget-config-file#solution-section)

  <span data-ttu-id="cea68-139">Toto nastavení je specifické pro Visual Studio a neplatí pro .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cea68-139">This setting is Visual Studio specific and doesn't apply to .NET Core.</span></span> <span data-ttu-id="cea68-140">.NET Core nepoužívá `packages.config` soubor a místo toho používá `<PackageReference>` elementy pro balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="cea68-140">.NET Core doesn't use a `packages.config` file and instead uses `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="cea68-141">trustedSigners</span><span class="sxs-lookup"><span data-stu-id="cea68-141">trustedSigners</span></span>](/nuget/schema/nuget-config-file#trustedsigners-section)

  <span data-ttu-id="cea68-142">Toto nastavení se nedá použít, protože [NuGet zatím nepodporuje ověřování](https://github.com/NuGet/Home/issues/7939) pro důvěryhodné balíčky v různých platformách.</span><span class="sxs-lookup"><span data-stu-id="cea68-142">This setting isn't applicable as [NuGet doesn't yet support cross-platform verification](https://github.com/NuGet/Home/issues/7939) of trusted packages.</span></span>

## <a name="arguments"></a><span data-ttu-id="cea68-143">Argumenty</span><span class="sxs-lookup"><span data-stu-id="cea68-143">Arguments</span></span>

- **`ROOT`**

  <span data-ttu-id="cea68-144">Volitelná cesta k souboru projektu, který má být obnoven.</span><span class="sxs-lookup"><span data-stu-id="cea68-144">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="cea68-145">Možnosti</span><span class="sxs-lookup"><span data-stu-id="cea68-145">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="cea68-146">Konfigurační soubor NuGet (*NuGet. config*), který se má použít pro operaci obnovení.</span><span class="sxs-lookup"><span data-stu-id="cea68-146">The NuGet configuration file (*nuget.config*) to use for the restore operation.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="cea68-147">Zakáže obnovení více projektů paralelně.</span><span class="sxs-lookup"><span data-stu-id="cea68-147">Disables restoring multiple projects in parallel.</span></span>

- **`--force`**

  <span data-ttu-id="cea68-148">Vynutí vyřešení všech závislostí i v případě, že bylo poslední obnovení úspěšné.</span><span class="sxs-lookup"><span data-stu-id="cea68-148">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="cea68-149">Zadání tohoto příznaku je stejné jako odstranění souboru *Project. assets. JSON* .</span><span class="sxs-lookup"><span data-stu-id="cea68-149">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`--force-evaluate`**

  <span data-ttu-id="cea68-150">Vynutí obnovení, aby se znovu vyhodnotily všechny závislosti i v případě, že soubor zámku již existuje.</span><span class="sxs-lookup"><span data-stu-id="cea68-150">Forces restore to reevaluate all dependencies even if a lock file already exists.</span></span>

- **`-h|--help`**

  <span data-ttu-id="cea68-151">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="cea68-151">Prints out a short help for the command.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="cea68-152">Pouze upozornit na zdroje, které selhaly, pokud existují balíčky, které splňují požadavky na verzi.</span><span class="sxs-lookup"><span data-stu-id="cea68-152">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

- **`--interactive`**

  <span data-ttu-id="cea68-153">Umožňuje příkazu zastavit a počkat na vstup nebo akci uživatele (například k dokončení ověřování).</span><span class="sxs-lookup"><span data-stu-id="cea68-153">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span> <span data-ttu-id="cea68-154">Vzhledem k tomu, že .NET Core 2.1.400.</span><span class="sxs-lookup"><span data-stu-id="cea68-154">Since .NET Core 2.1.400.</span></span>

- **`--lock-file-path <LOCK_FILE_PATH>`**

  <span data-ttu-id="cea68-155">Výstupní umístění, kde je zapsán soubor zámku projektu.</span><span class="sxs-lookup"><span data-stu-id="cea68-155">Output location where project lock file is written.</span></span> <span data-ttu-id="cea68-156">Ve výchozím nastavení je to *PROJECT_ROOT \Packages.Lock.JSON*.</span><span class="sxs-lookup"><span data-stu-id="cea68-156">By default, this is *PROJECT_ROOT\packages.lock.json*.</span></span>

- **`--locked-mode`**

  <span data-ttu-id="cea68-157">Nepovolujte aktualizaci souboru zámku projektu.</span><span class="sxs-lookup"><span data-stu-id="cea68-157">Don't allow updating project lock file.</span></span>

- **`--no-cache`**

  <span data-ttu-id="cea68-158">Určuje, že nejsou požadavky HTTP cache.</span><span class="sxs-lookup"><span data-stu-id="cea68-158">Specifies to not cache HTTP requests.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="cea68-159">Při obnovení projektu s odkazy z projektu na projekt (P2P) obnoví kořenový projekt a nikoli odkazy.</span><span class="sxs-lookup"><span data-stu-id="cea68-159">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

- **`--packages <PACKAGES_DIRECTORY>`**

  <span data-ttu-id="cea68-160">Určuje adresář pro obnovené balíčky.</span><span class="sxs-lookup"><span data-stu-id="cea68-160">Specifies the directory for restored packages.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="cea68-161">Určuje modul runtime pro obnovení balíčku.</span><span class="sxs-lookup"><span data-stu-id="cea68-161">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="cea68-162">Slouží k obnovení balíčků pro moduly runtime, které nejsou explicitně uvedeny v `<RuntimeIdentifiers>` značce v souboru *. csproj* .</span><span class="sxs-lookup"><span data-stu-id="cea68-162">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="cea68-163">Seznam identifikátorů modulu runtime (identifikátorů RID) najdete v [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="cea68-163">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="cea68-164">Zadáním této možnosti několikrát zadejte víc identifikátorů RID.</span><span class="sxs-lookup"><span data-stu-id="cea68-164">Provide multiple RIDs by specifying this option multiple times.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="cea68-165">Určuje zdroj balíčku NuGet, který se použije během operace obnovení.</span><span class="sxs-lookup"><span data-stu-id="cea68-165">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="cea68-166">Toto nastavení přepíše všechny zdroje zadané v souborech *NuGet. config* .</span><span class="sxs-lookup"><span data-stu-id="cea68-166">This setting overrides all of the sources specified in the *nuget.config* files.</span></span> <span data-ttu-id="cea68-167">Více zdrojů lze zadat zadáním této možnosti několikrát.</span><span class="sxs-lookup"><span data-stu-id="cea68-167">Multiple sources can be provided by specifying this option multiple times.</span></span>

- **`--use-lockfile`**

  <span data-ttu-id="cea68-168">Povoluje vygenerování souboru zámku projektu a jeho použití s obnovením.</span><span class="sxs-lookup"><span data-stu-id="cea68-168">Enables project lock file to be generated and used with restore.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="cea68-169">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="cea68-169">Sets the verbosity level of the command.</span></span> <span data-ttu-id="cea68-170">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]` `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="cea68-170">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="cea68-171">Výchozí hodnota je `minimal`.</span><span class="sxs-lookup"><span data-stu-id="cea68-171">Default value is `minimal`.</span></span>

## <a name="examples"></a><span data-ttu-id="cea68-172">Příklady</span><span class="sxs-lookup"><span data-stu-id="cea68-172">Examples</span></span>

- <span data-ttu-id="cea68-173">Obnovit závislosti a nástroje pro projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="cea68-173">Restore dependencies and tools for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet restore
  ```

- <span data-ttu-id="cea68-174">Obnovit závislosti a nástroje pro `app1` projekt nalezené v dané cestě:</span><span class="sxs-lookup"><span data-stu-id="cea68-174">Restore dependencies and tools for the `app1` project found in the   given path:</span></span>

  ```dotnetcli
  dotnet restore ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="cea68-175">Obnovte závislosti a nástroje pro projekt v aktuálním adresáři pomocí cesty k souboru, který jste zadali jako zdroj:</span><span class="sxs-lookup"><span data-stu-id="cea68-175">Restore the dependencies and tools for the project in the current   directory using the file path provided as the source:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages
  ```

- <span data-ttu-id="cea68-176">Obnovte závislosti a nástroje pro projekt v aktuálním adresáři pomocí dvou cest k souborům, které jsou k dispozici jako zdroje:</span><span class="sxs-lookup"><span data-stu-id="cea68-176">Restore the dependencies and tools for the project in the current   directory using the two file paths provided as sources:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages
  ```

- <span data-ttu-id="cea68-177">Obnoví závislosti a nástroje pro projekt v aktuálním adresáři se zobrazeným podrobným výstupem:</span><span class="sxs-lookup"><span data-stu-id="cea68-177">Restore dependencies and tools for the project in the current directory   showing detailed output:</span></span>

  ```dotnetcli
  dotnet restore --verbosity detailed
  ```
