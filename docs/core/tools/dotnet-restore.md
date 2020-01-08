---
title: dotnet restore – příkaz
description: Naučte se obnovit závislosti a nástroje specifické pro projekt pomocí příkazu dotnet restore.
ms.date: 05/29/2018
ms.openlocfilehash: 82dd85e340a4cb520f781d977b0798b0f532a088
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75340439"
---
# <a name="dotnet-restore"></a><span data-ttu-id="218ed-103">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="218ed-103">dotnet restore</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="218ed-104">Name</span><span class="sxs-lookup"><span data-stu-id="218ed-104">Name</span></span>

<span data-ttu-id="218ed-105">`dotnet restore` – obnoví závislosti a nástroje projektu.</span><span class="sxs-lookup"><span data-stu-id="218ed-105">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="218ed-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="218ed-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="218ed-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="218ed-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```dotnetcli
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--force] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity] [--interactive]
dotnet restore [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="218ed-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="218ed-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="218ed-109">Popis</span><span class="sxs-lookup"><span data-stu-id="218ed-109">Description</span></span>

<span data-ttu-id="218ed-110">Příkaz `dotnet restore` používá NuGet pro obnovení závislostí a také nástrojů specifických pro projekt, které jsou uvedeny v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="218ed-110">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span> <span data-ttu-id="218ed-111">Ve výchozím nastavení jsou obnovení závislostí a nástrojů spouštěny paralelně.</span><span class="sxs-lookup"><span data-stu-id="218ed-111">By default, the restoration of dependencies and tools are executed in parallel.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="218ed-112">Pro obnovení závislostí potřebuje NuGet informační kanály, ve kterých se balíčky nacházejí.</span><span class="sxs-lookup"><span data-stu-id="218ed-112">To restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="218ed-113">Informační kanály jsou obvykle poskytovány prostřednictvím konfiguračního souboru *NuGet. config* .</span><span class="sxs-lookup"><span data-stu-id="218ed-113">Feeds are usually provided via the *nuget.config* configuration file.</span></span> <span data-ttu-id="218ed-114">Výchozí konfigurační soubor se poskytne při instalaci nástrojů rozhraní příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="218ed-114">A default configuration file is provided when the CLI tools are installed.</span></span> <span data-ttu-id="218ed-115">Další kanály určíte tak, že vytvoříte vlastní soubor *NuGet. config* v adresáři projektu.</span><span class="sxs-lookup"><span data-stu-id="218ed-115">You specify additional feeds by creating your own *nuget.config* file in the project directory.</span></span> <span data-ttu-id="218ed-116">Informační kanály *NuGet. config* můžete přepsat pomocí možnosti `-s`.</span><span class="sxs-lookup"><span data-stu-id="218ed-116">You can override the *nuget.config* feeds with the `-s` option.</span></span>

<span data-ttu-id="218ed-117">U závislostí určíte, kde se obnovené balíčky umístí během operace obnovení pomocí argumentu `--packages`.</span><span class="sxs-lookup"><span data-stu-id="218ed-117">For dependencies, you specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="218ed-118">Pokud není zadaný, použije se výchozí mezipaměť balíčků NuGet, která se nachází v adresáři `.nuget/packages` v domovském adresáři uživatele ve všech operačních systémech.</span><span class="sxs-lookup"><span data-stu-id="218ed-118">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems.</span></span> <span data-ttu-id="218ed-119">Například */Home/user1* v systému Linux nebo *C:\Users\user1* ve Windows.</span><span class="sxs-lookup"><span data-stu-id="218ed-119">For example, */home/user1* on Linux or *C:\Users\user1* on Windows.</span></span>

<span data-ttu-id="218ed-120">U nástrojů specifických pro projekt `dotnet restore` nejprve obnovte balíček, ve kterém je nástroj zabalený, a pak pokračuje v obnovování závislostí nástroje, jak je uvedeno v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="218ed-120">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

### <a name="nugetconfig-differences"></a><span data-ttu-id="218ed-121">rozdíly v NuGet. config</span><span class="sxs-lookup"><span data-stu-id="218ed-121">nuget.config differences</span></span>

<span data-ttu-id="218ed-122">Chování `dotnet restore` příkazu je ovlivněno nastavením v souboru *NuGet. config* , pokud je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="218ed-122">The behavior of the `dotnet restore` command is affected by the settings in the *nuget.config* file, if present.</span></span> <span data-ttu-id="218ed-123">Například nastavení `globalPackagesFolder` v *souboru NuGet. config* umístí obnovené balíčky NuGet do zadané složky.</span><span class="sxs-lookup"><span data-stu-id="218ed-123">For example, setting the `globalPackagesFolder` in *nuget.config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="218ed-124">Toto je alternativa k zadání možnosti `--packages` v příkazu `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="218ed-124">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="218ed-125">Další informace najdete v referenčních informacích k [NuGet. config](/nuget/schema/nuget-config-file).</span><span class="sxs-lookup"><span data-stu-id="218ed-125">For more information, see the [nuget.config reference](/nuget/schema/nuget-config-file).</span></span>

<span data-ttu-id="218ed-126">Existují tři specifická nastavení, která `dotnet restore` ignorují:</span><span class="sxs-lookup"><span data-stu-id="218ed-126">There are three specific settings that `dotnet restore` ignores:</span></span>

- [<span data-ttu-id="218ed-127">bindingRedirects</span><span class="sxs-lookup"><span data-stu-id="218ed-127">bindingRedirects</span></span>](/nuget/schema/nuget-config-file#bindingredirects-section)

  <span data-ttu-id="218ed-128">Přesměrování vazby nefungují s prvky `<PackageReference>` a .NET Core podporuje pouze `<PackageReference>` prvky pro balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="218ed-128">Binding redirects don't work with `<PackageReference>` elements and .NET Core only supports `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="218ed-129">řešení</span><span class="sxs-lookup"><span data-stu-id="218ed-129">solution</span></span>](/nuget/schema/nuget-config-file#solution-section)

  <span data-ttu-id="218ed-130">Toto nastavení je specifické pro Visual Studio a neplatí pro .NET Core.</span><span class="sxs-lookup"><span data-stu-id="218ed-130">This setting is Visual Studio specific and doesn't apply to .NET Core.</span></span> <span data-ttu-id="218ed-131">.NET Core nepoužívá soubor `packages.config` a místo toho používá `<PackageReference>` prvky pro balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="218ed-131">.NET Core doesn't use a `packages.config` file and instead uses `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="218ed-132">trustedSigners</span><span class="sxs-lookup"><span data-stu-id="218ed-132">trustedSigners</span></span>](/nuget/schema/nuget-config-file#trustedsigners-section)

  <span data-ttu-id="218ed-133">Toto nastavení se nedá použít, protože [NuGet zatím nepodporuje ověřování](https://github.com/NuGet/Home/issues/7939) pro důvěryhodné balíčky v různých platformách.</span><span class="sxs-lookup"><span data-stu-id="218ed-133">This setting isn't applicable as [NuGet doesn't yet support cross-platform verification](https://github.com/NuGet/Home/issues/7939) of trusted packages.</span></span>

## <a name="implicit-dotnet-restore"></a><span data-ttu-id="218ed-134">Implicitní `dotnet restore`</span><span class="sxs-lookup"><span data-stu-id="218ed-134">Implicit `dotnet restore`</span></span>

<span data-ttu-id="218ed-135">Počínaje rozhraním .NET Core 2,0 se `dotnet restore` v případě potřeby spouští implicitně, když vydáte následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="218ed-135">Starting with .NET Core 2.0, `dotnet restore` is run implicitly if necessary when you issue the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="218ed-136">Ve většině případů už nemusíte explicitně používat příkaz `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="218ed-136">In most cases, you no longer need to explicitly use the `dotnet restore` command.</span></span>

<span data-ttu-id="218ed-137">V některých případech může být nepraktické spustit `dotnet restore` implicitně.</span><span class="sxs-lookup"><span data-stu-id="218ed-137">Sometimes, it might be inconvenient to run `dotnet restore` implicitly.</span></span> <span data-ttu-id="218ed-138">Například některé automatizované systémy, například systémy sestavení, musí volat `dotnet restore` explicitně pro řízení, když dojde k obnovení, aby bylo možné řídit využití sítě.</span><span class="sxs-lookup"><span data-stu-id="218ed-138">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="218ed-139">Chcete-li zabránit spuštění `dotnet restore` implicitně, můžete použít příznak `--no-restore` s některým z těchto příkazů k zakázání implicitního obnovení.</span><span class="sxs-lookup"><span data-stu-id="218ed-139">To prevent `dotnet restore` from running implicitly, you can use the `--no-restore` flag with any of these commands to disable implicit restore.</span></span>

## <a name="arguments"></a><span data-ttu-id="218ed-140">Arguments</span><span class="sxs-lookup"><span data-stu-id="218ed-140">Arguments</span></span>

`ROOT`

<span data-ttu-id="218ed-141">Volitelná cesta k souboru projektu, který má být obnoven.</span><span class="sxs-lookup"><span data-stu-id="218ed-141">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="218ed-142">Možnosti</span><span class="sxs-lookup"><span data-stu-id="218ed-142">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="218ed-143">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="218ed-143">.NET Core 2.x</span></span>](#tab/netcore2x)

`--configfile <FILE>`

<span data-ttu-id="218ed-144">Konfigurační soubor NuGet (*NuGet. config*), který se má použít pro operaci obnovení.</span><span class="sxs-lookup"><span data-stu-id="218ed-144">The NuGet configuration file (*nuget.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="218ed-145">Zakáže obnovení více projektů paralelně.</span><span class="sxs-lookup"><span data-stu-id="218ed-145">Disables restoring multiple projects in parallel.</span></span>

`--force`

<span data-ttu-id="218ed-146">Vynutí vyřešení všech závislostí i v případě, že bylo poslední obnovení úspěšné.</span><span class="sxs-lookup"><span data-stu-id="218ed-146">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="218ed-147">Zadání tohoto příznaku je stejné jako odstranění souboru *Project. assets. JSON* .</span><span class="sxs-lookup"><span data-stu-id="218ed-147">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="218ed-148">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="218ed-148">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="218ed-149">Pouze upozornit na zdroje, které selhaly, pokud existují balíčky, které splňují požadavky na verzi.</span><span class="sxs-lookup"><span data-stu-id="218ed-149">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="218ed-150">Určuje, že nejsou balíčky mezipaměti a požadavky HTTP.</span><span class="sxs-lookup"><span data-stu-id="218ed-150">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="218ed-151">Při obnovení projektu s odkazy z projektu na projekt (P2P) obnoví kořenový projekt a nikoli odkazy.</span><span class="sxs-lookup"><span data-stu-id="218ed-151">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="218ed-152">Určuje adresář pro obnovené balíčky.</span><span class="sxs-lookup"><span data-stu-id="218ed-152">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="218ed-153">Určuje modul runtime pro obnovení balíčku.</span><span class="sxs-lookup"><span data-stu-id="218ed-153">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="218ed-154">Slouží k obnovení balíčků pro moduly runtime, které nejsou explicitně uvedeny v značce `<RuntimeIdentifiers>` v souboru *. csproj* .</span><span class="sxs-lookup"><span data-stu-id="218ed-154">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="218ed-155">Seznam identifikátorů modulu runtime (identifikátorů RID) najdete v [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="218ed-155">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="218ed-156">Zadáním této možnosti několikrát zadejte víc identifikátorů RID.</span><span class="sxs-lookup"><span data-stu-id="218ed-156">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="218ed-157">Určuje zdroj balíčku NuGet, který se použije během operace obnovení.</span><span class="sxs-lookup"><span data-stu-id="218ed-157">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="218ed-158">Toto nastavení přepíše všechny zdroje zadané v souborech *NuGet. config* .</span><span class="sxs-lookup"><span data-stu-id="218ed-158">This setting overrides all of the sources specified in the *nuget.config* files.</span></span> <span data-ttu-id="218ed-159">Více zdrojů lze zadat zadáním této možnosti několikrát.</span><span class="sxs-lookup"><span data-stu-id="218ed-159">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="218ed-160">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="218ed-160">Sets the verbosity level of the command.</span></span> <span data-ttu-id="218ed-161">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="218ed-161">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="218ed-162">Výchozí hodnota je `minimal`.</span><span class="sxs-lookup"><span data-stu-id="218ed-162">Default value is `minimal`.</span></span>

`--interactive`

<span data-ttu-id="218ed-163">Umožňuje příkazu zastavit a počkat na vstup nebo akci uživatele (například k dokončení ověřování).</span><span class="sxs-lookup"><span data-stu-id="218ed-163">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span> <span data-ttu-id="218ed-164">Vzhledem k tomu, že .NET Core 2.1.400.</span><span class="sxs-lookup"><span data-stu-id="218ed-164">Since .NET Core 2.1.400.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="218ed-165">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="218ed-165">.NET Core 1.x</span></span>](#tab/netcore1x)

`--configfile <FILE>`

<span data-ttu-id="218ed-166">Konfigurační soubor NuGet (*NuGet. config*), který se má použít pro operaci obnovení.</span><span class="sxs-lookup"><span data-stu-id="218ed-166">The NuGet configuration file (*nuget.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="218ed-167">Zakáže obnovení více projektů paralelně.</span><span class="sxs-lookup"><span data-stu-id="218ed-167">Disables restoring multiple projects in parallel.</span></span>

`-h|--help`

<span data-ttu-id="218ed-168">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="218ed-168">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="218ed-169">Pouze upozornit na zdroje, které selhaly, pokud existují balíčky, které splňují požadavky na verzi.</span><span class="sxs-lookup"><span data-stu-id="218ed-169">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="218ed-170">Určuje, že nejsou balíčky mezipaměti a požadavky HTTP.</span><span class="sxs-lookup"><span data-stu-id="218ed-170">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="218ed-171">Při obnovení projektu s odkazy z projektu na projekt (P2P) obnoví kořenový projekt a nikoli odkazy.</span><span class="sxs-lookup"><span data-stu-id="218ed-171">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="218ed-172">Určuje adresář pro obnovené balíčky.</span><span class="sxs-lookup"><span data-stu-id="218ed-172">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="218ed-173">Určuje modul runtime pro obnovení balíčku.</span><span class="sxs-lookup"><span data-stu-id="218ed-173">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="218ed-174">Slouží k obnovení balíčků pro moduly runtime, které nejsou explicitně uvedeny v značce `<RuntimeIdentifiers>` v souboru *. csproj* .</span><span class="sxs-lookup"><span data-stu-id="218ed-174">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="218ed-175">Seznam identifikátorů modulu runtime (identifikátorů RID) najdete v [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="218ed-175">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="218ed-176">Zadáním této možnosti několikrát zadejte víc identifikátorů RID.</span><span class="sxs-lookup"><span data-stu-id="218ed-176">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="218ed-177">Určuje zdroj balíčku NuGet, který se použije během operace obnovení.</span><span class="sxs-lookup"><span data-stu-id="218ed-177">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="218ed-178">Tím dojde k přepsání všech zdrojů zadaných v souborech *NuGet. config* a efektivně si přečtete soubor *NuGet. config* , jako kdyby `<packageSource>` element nebyl nalezen.</span><span class="sxs-lookup"><span data-stu-id="218ed-178">This overrides all of the sources specified in the *nuget.config* files, effectively reading the *nuget.config* file as if the `<packageSource>` element was not there.</span></span> <span data-ttu-id="218ed-179">Více zdrojů lze zadat zadáním této možnosti několikrát.</span><span class="sxs-lookup"><span data-stu-id="218ed-179">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="218ed-180">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="218ed-180">Sets the verbosity level of the command.</span></span> <span data-ttu-id="218ed-181">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="218ed-181">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="218ed-182">Výchozí hodnota je `minimal`.</span><span class="sxs-lookup"><span data-stu-id="218ed-182">The default is `minimal`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="218ed-183">Příklady</span><span class="sxs-lookup"><span data-stu-id="218ed-183">Examples</span></span>

<span data-ttu-id="218ed-184">Obnovit závislosti a nástroje pro projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="218ed-184">Restore dependencies and tools for the project in the current directory:</span></span>

`dotnet restore`

<span data-ttu-id="218ed-185">V dané cestě se našly závislosti a nástroje pro `app1` projekt:</span><span class="sxs-lookup"><span data-stu-id="218ed-185">Restore dependencies and tools for the `app1` project found in the given path:</span></span>

`dotnet restore ~/projects/app1/app1.csproj`

<span data-ttu-id="218ed-186">Obnovte závislosti a nástroje pro projekt v aktuálním adresáři pomocí cesty k souboru, který jste zadali jako zdroj:</span><span class="sxs-lookup"><span data-stu-id="218ed-186">Restore the dependencies and tools for the project in the current directory using the file path provided as the source:</span></span>

`dotnet restore -s c:\packages\mypackages`

<span data-ttu-id="218ed-187">Obnovte závislosti a nástroje pro projekt v aktuálním adresáři pomocí dvou cest k souborům, které jsou k dispozici jako zdroje:</span><span class="sxs-lookup"><span data-stu-id="218ed-187">Restore the dependencies and tools for the project in the current directory using the two file paths provided as sources:</span></span>

`dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages`

<span data-ttu-id="218ed-188">Obnoví závislosti a nástroje pro projekt v aktuálním adresáři se zobrazeným podrobným výstupem:</span><span class="sxs-lookup"><span data-stu-id="218ed-188">Restore dependencies and tools for the project in the current directory showing detailed output:</span></span>

`dotnet restore --verbosity detailed`
