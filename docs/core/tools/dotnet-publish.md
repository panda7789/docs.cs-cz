---
title: dotnet publish – příkaz
description: Příkaz dotnet publish publikuje projekt .NET Core do adresáře.
ms.date: 05/29/2018
ms.openlocfilehash: 8cefeae17e464e14abc54dce1feb414a72c44164
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331030"
---
# <a name="dotnet-publish"></a><span data-ttu-id="55c56-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="55c56-103">dotnet publish</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="55c56-104">Name</span><span class="sxs-lookup"><span data-stu-id="55c56-104">Name</span></span>

<span data-ttu-id="55c56-105">`dotnet publish`– Zabalí aplikaci a její závislosti do složky pro nasazení do hostitelského systému.</span><span class="sxs-lookup"><span data-stu-id="55c56-105">`dotnet publish` - Packs the application and its dependencies into a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="55c56-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="55c56-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="55c56-107">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="55c56-107">.NET Core 2.1</span></span>](#tab/netcore21)

```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="55c56-108">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="55c56-108">.NET Core 2.0</span></span>](#tab/netcore20)

```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="55c56-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="55c56-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
    [--version-suffix]
dotnet publish [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="55c56-110">Popis</span><span class="sxs-lookup"><span data-stu-id="55c56-110">Description</span></span>

<span data-ttu-id="55c56-111">`dotnet publish`zkompiluje aplikaci, přečte prostřednictvím svých závislostí zadaných v souboru projektu a publikuje výslednou sadu souborů do adresáře.</span><span class="sxs-lookup"><span data-stu-id="55c56-111">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="55c56-112">Výstup obsahuje následující prostředky:</span><span class="sxs-lookup"><span data-stu-id="55c56-112">The output includes the following assets:</span></span>

* <span data-ttu-id="55c56-113">Kód zprostředkujícího jazyka (IL) v sestavení s příponou *DLL* .</span><span class="sxs-lookup"><span data-stu-id="55c56-113">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
* <span data-ttu-id="55c56-114">soubor *. DEPS. JSON* , který obsahuje všechny závislosti projektu.</span><span class="sxs-lookup"><span data-stu-id="55c56-114">*.deps.json* file that includes all of the dependencies of the project.</span></span>
* <span data-ttu-id="55c56-115">soubor *. runtimeconfig. JSON* , který určuje sdílený modul runtime, který aplikace očekává, a další možnosti konfigurace pro modul runtime (například typ uvolňování paměti).</span><span class="sxs-lookup"><span data-stu-id="55c56-115">*.runtimeconfig.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
* <span data-ttu-id="55c56-116">Závislosti aplikace, které jsou zkopírovány z mezipaměti NuGet do výstupní složky.</span><span class="sxs-lookup"><span data-stu-id="55c56-116">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="55c56-117">Výstup `dotnet publish` příkazu je připravený k nasazení do hostitelského systému (například server, počítač, Mac, notebook) k provedení.</span><span class="sxs-lookup"><span data-stu-id="55c56-117">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="55c56-118">Jedná se o jediný oficiálně podporovaný způsob, jak připravit aplikaci pro nasazení.</span><span class="sxs-lookup"><span data-stu-id="55c56-118">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="55c56-119">V závislosti na typu nasazení, které projekt určuje, hostující systém může nebo nemusí mít nainstalovaný modul .NET Core Shared runtime.</span><span class="sxs-lookup"><span data-stu-id="55c56-119">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="55c56-120">Další informace najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="55c56-120">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span> <span data-ttu-id="55c56-121">Adresářovou strukturu publikované aplikace najdete v tématu [Struktura adresáře](/aspnet/core/hosting/directory-structure).</span><span class="sxs-lookup"><span data-stu-id="55c56-121">For the directory structure of a published application, see [Directory structure](/aspnet/core/hosting/directory-structure).</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="55c56-122">Arguments</span><span class="sxs-lookup"><span data-stu-id="55c56-122">Arguments</span></span>

`PROJECT`

<span data-ttu-id="55c56-123">Projekt, který se má publikovat</span><span class="sxs-lookup"><span data-stu-id="55c56-123">The project to publish.</span></span> <span data-ttu-id="55c56-124">Jedná se o cestu a název souboru [C#](csproj.md)projektu, F#nebo Visual Basic, nebo o cestu k adresáři, který obsahuje soubor projektu C#, F#nebo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="55c56-124">It's either the path and filename of a [C#](csproj.md), F#, or Visual Basic project file, or the path to a directory that contains a C#, F#, or Visual Basic project file.</span></span> <span data-ttu-id="55c56-125">Pokud není zadaný, použije se ve výchozím nastavení aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="55c56-125">If not specified, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="55c56-126">Možnosti</span><span class="sxs-lookup"><span data-stu-id="55c56-126">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="55c56-127">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="55c56-127">.NET Core 2.1</span></span>](#tab/netcore21)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="55c56-128">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="55c56-128">Defines the build configuration.</span></span> <span data-ttu-id="55c56-129">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="55c56-129">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="55c56-130">Publikuje aplikaci pro zadanou [cílovou architekturu](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="55c56-130">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="55c56-131">V souboru projektu je nutné zadat cílovou architekturu.</span><span class="sxs-lookup"><span data-stu-id="55c56-131">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="55c56-132">Vynutí vyřešení všech závislostí i v případě, že bylo poslední obnovení úspěšné.</span><span class="sxs-lookup"><span data-stu-id="55c56-132">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="55c56-133">Zadání tohoto příznaku je stejné jako odstranění souboru *Project. assets. JSON* .</span><span class="sxs-lookup"><span data-stu-id="55c56-133">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="55c56-134">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="55c56-134">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="55c56-135">Určuje jeden nebo několik [cílových manifestů](../deploying/runtime-store.md) , které se použijí ke zkrácení sady balíčků publikovaných s aplikací.</span><span class="sxs-lookup"><span data-stu-id="55c56-135">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="55c56-136">Soubor manifestu je součástí výstupu [ `dotnet store` příkazu](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="55c56-136">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="55c56-137">Chcete-li zadat více manifestů, `--manifest` přidejte možnost pro každý manifest.</span><span class="sxs-lookup"><span data-stu-id="55c56-137">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="55c56-138">Tato možnost je k dispozici počínaje verzí .NET Core 2,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="55c56-138">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-build`

<span data-ttu-id="55c56-139">Nevytvoří projekt před publikováním.</span><span class="sxs-lookup"><span data-stu-id="55c56-139">Doesn't build the project before publishing.</span></span> <span data-ttu-id="55c56-140">Také implicitně nastaví `--no-restore` příznak.</span><span class="sxs-lookup"><span data-stu-id="55c56-140">It also implicitly sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="55c56-141">Ignoruje odkazy z projektu na projekt a obnoví pouze kořenový projekt.</span><span class="sxs-lookup"><span data-stu-id="55c56-141">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="55c56-142">Při spuštění příkazu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="55c56-142">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="55c56-143">Určuje cestu k výstupnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="55c56-143">Specifies the path for the output directory.</span></span> <span data-ttu-id="55c56-144">Pokud není zadaný, použije se výchozí hodnota *./bin/[Configuration]/[Framework]/Publish/* pro nasazení závislé na rozhraní nebo *./bin/[Configuration]/[Framework]/[runtime]/Publish/* pro samostatně uzavřené nasazení.</span><span class="sxs-lookup"><span data-stu-id="55c56-144">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="55c56-145">Pokud je cesta relativní, vygenerovaný výstupní adresář je relativní vzhledem k umístění souboru projektu, nikoli k aktuálnímu pracovnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="55c56-145">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="55c56-146">Publikuje modul runtime .NET Core ve vaší aplikaci, takže modul runtime nemusí být na cílovém počítači nainstalován.</span><span class="sxs-lookup"><span data-stu-id="55c56-146">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="55c56-147">Je-li zadán identifikátor modulu runtime, jeho výchozí hodnota `true`je.</span><span class="sxs-lookup"><span data-stu-id="55c56-147">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="55c56-148">Další informace o různých typech nasazení naleznete v tématu [nasazení aplikace .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="55c56-148">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="55c56-149">Publikuje aplikaci pro daný modul runtime.</span><span class="sxs-lookup"><span data-stu-id="55c56-149">Publishes the application for a given runtime.</span></span> <span data-ttu-id="55c56-150">Používá se při vytváření [samostatně zahrnutého nasazení (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="55c56-150">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="55c56-151">Seznam identifikátorů modulu runtime (identifikátorů RID) najdete v [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="55c56-151">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="55c56-152">Výchozím nastavením je publikování [nasazení závislého na rozhraní (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="55c56-152">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="55c56-153">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="55c56-153">Sets the verbosity level of the command.</span></span> <span data-ttu-id="55c56-154">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]` `d[etailed]`, a .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="55c56-154">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="55c56-155">Definuje příponu verze, která nahradí hvězdičku (`*`) v poli verze souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="55c56-155">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="55c56-156">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="55c56-156">.NET Core 2.0</span></span>](#tab/netcore20)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="55c56-157">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="55c56-157">Defines the build configuration.</span></span> <span data-ttu-id="55c56-158">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="55c56-158">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="55c56-159">Publikuje aplikaci pro zadanou [cílovou architekturu](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="55c56-159">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="55c56-160">V souboru projektu je nutné zadat cílovou architekturu.</span><span class="sxs-lookup"><span data-stu-id="55c56-160">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="55c56-161">Vynutí vyřešení všech závislostí i v případě, že bylo poslední obnovení úspěšné.</span><span class="sxs-lookup"><span data-stu-id="55c56-161">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="55c56-162">Zadání tohoto příznaku je stejné jako odstranění souboru *Project. assets. JSON* .</span><span class="sxs-lookup"><span data-stu-id="55c56-162">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="55c56-163">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="55c56-163">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="55c56-164">Určuje jeden nebo několik [cílových manifestů](../deploying/runtime-store.md) , které se použijí ke zkrácení sady balíčků publikovaných s aplikací.</span><span class="sxs-lookup"><span data-stu-id="55c56-164">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="55c56-165">Soubor manifestu je součástí výstupu [ `dotnet store` příkazu](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="55c56-165">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="55c56-166">Chcete-li zadat více manifestů, `--manifest` přidejte možnost pro každý manifest.</span><span class="sxs-lookup"><span data-stu-id="55c56-166">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="55c56-167">Tato možnost je k dispozici počínaje verzí .NET Core 2,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="55c56-167">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-dependencies`

<span data-ttu-id="55c56-168">Ignoruje odkazy z projektu na projekt a obnoví pouze kořenový projekt.</span><span class="sxs-lookup"><span data-stu-id="55c56-168">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="55c56-169">Při spuštění příkazu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="55c56-169">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="55c56-170">Určuje cestu k výstupnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="55c56-170">Specifies the path for the output directory.</span></span> <span data-ttu-id="55c56-171">Pokud není zadaný, použije se výchozí hodnota *./bin/[Configuration]/[Framework]/Publish/* pro nasazení závislé na rozhraní nebo *./bin/[Configuration]/[Framework]/[runtime]/Publish/* pro samostatně uzavřené nasazení.</span><span class="sxs-lookup"><span data-stu-id="55c56-171">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="55c56-172">Pokud je cesta relativní, vygenerovaný výstupní adresář je relativní vzhledem k umístění souboru projektu, nikoli k aktuálnímu pracovnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="55c56-172">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="55c56-173">Publikuje modul runtime .NET Core ve vaší aplikaci, takže modul runtime nemusí být na cílovém počítači nainstalován.</span><span class="sxs-lookup"><span data-stu-id="55c56-173">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="55c56-174">Je-li zadán identifikátor modulu runtime, jeho výchozí hodnota `true`je.</span><span class="sxs-lookup"><span data-stu-id="55c56-174">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="55c56-175">Další informace o různých typech nasazení naleznete v tématu [nasazení aplikace .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="55c56-175">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="55c56-176">Publikuje aplikaci pro daný modul runtime.</span><span class="sxs-lookup"><span data-stu-id="55c56-176">Publishes the application for a given runtime.</span></span> <span data-ttu-id="55c56-177">Používá se při vytváření [samostatně zahrnutého nasazení (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="55c56-177">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="55c56-178">Seznam identifikátorů modulu runtime (identifikátorů RID) najdete v [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="55c56-178">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="55c56-179">Výchozím nastavením je publikování [nasazení závislého na rozhraní (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="55c56-179">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="55c56-180">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="55c56-180">Sets the verbosity level of the command.</span></span> <span data-ttu-id="55c56-181">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]` `d[etailed]`, a .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="55c56-181">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="55c56-182">Definuje příponu verze, která nahradí hvězdičku (`*`) v poli verze souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="55c56-182">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="55c56-183">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="55c56-183">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="55c56-184">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="55c56-184">Defines the build configuration.</span></span> <span data-ttu-id="55c56-185">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="55c56-185">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="55c56-186">Publikuje aplikaci pro zadanou [cílovou architekturu](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="55c56-186">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="55c56-187">V souboru projektu je nutné zadat cílovou architekturu.</span><span class="sxs-lookup"><span data-stu-id="55c56-187">You must specify the target framework in the project file.</span></span>

`-h|--help`

<span data-ttu-id="55c56-188">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="55c56-188">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="55c56-189">Určuje jeden nebo několik [cílových manifestů](../deploying/runtime-store.md) , které se použijí ke zkrácení sady balíčků publikovaných s aplikací.</span><span class="sxs-lookup"><span data-stu-id="55c56-189">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="55c56-190">Soubor manifestu je součástí výstupu [ `dotnet store` příkazu](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="55c56-190">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="55c56-191">Chcete-li zadat více manifestů, `--manifest` přidejte možnost pro každý manifest.</span><span class="sxs-lookup"><span data-stu-id="55c56-191">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="55c56-192">Tato možnost je k dispozici počínaje verzí .NET Core 2,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="55c56-192">This option is available starting with .NET Core 2.0 SDK.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="55c56-193">Určuje cestu k výstupnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="55c56-193">Specifies the path for the output directory.</span></span> <span data-ttu-id="55c56-194">Pokud není zadaný, použije se výchozí hodnota *./bin/[Configuration]/[Framework]/Publish/* pro nasazení závislé na rozhraní nebo *./bin/[Configuration]/[Framework]/[runtime]/Publish/* pro samostatně uzavřené nasazení.</span><span class="sxs-lookup"><span data-stu-id="55c56-194">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="55c56-195">Pokud je cesta relativní, vygenerovaný výstupní adresář je relativní vzhledem k umístění souboru projektu, nikoli k aktuálnímu pracovnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="55c56-195">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="55c56-196">Publikuje aplikaci pro daný modul runtime.</span><span class="sxs-lookup"><span data-stu-id="55c56-196">Publishes the application for a given runtime.</span></span> <span data-ttu-id="55c56-197">Používá se při vytváření [samostatně zahrnutého nasazení (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="55c56-197">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="55c56-198">Seznam identifikátorů modulu runtime (identifikátorů RID) najdete v [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="55c56-198">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="55c56-199">Výchozím nastavením je publikování [nasazení závislého na rozhraní (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="55c56-199">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="55c56-200">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="55c56-200">Sets the verbosity level of the command.</span></span> <span data-ttu-id="55c56-201">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]` `d[etailed]`, a .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="55c56-201">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="55c56-202">Definuje příponu verze, která nahradí hvězdičku (`*`) v poli verze souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="55c56-202">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

---

## <a name="examples"></a><span data-ttu-id="55c56-203">Příklady</span><span class="sxs-lookup"><span data-stu-id="55c56-203">Examples</span></span>

<span data-ttu-id="55c56-204">Publikovat projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="55c56-204">Publish the project in the current directory:</span></span>

`dotnet publish`

<span data-ttu-id="55c56-205">Publikovat aplikaci pomocí zadaného souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="55c56-205">Publish the application using the specified project file:</span></span>

`dotnet publish ~/projects/app1/app1.csproj`

<span data-ttu-id="55c56-206">Publikování projektu v aktuálním adresáři pomocí `netcoreapp1.1` rozhraní:</span><span class="sxs-lookup"><span data-stu-id="55c56-206">Publish the project in the current directory using the `netcoreapp1.1` framework:</span></span>

`dotnet publish --framework netcoreapp1.1`

<span data-ttu-id="55c56-207">Publikování aktuální aplikace pomocí `netcoreapp1.1` architektury a modulu runtime pro `OS X 10.10` (Tento identifikátor RID musíte uvést v souboru projektu).</span><span class="sxs-lookup"><span data-stu-id="55c56-207">Publish the current application using the `netcoreapp1.1` framework and the runtime for `OS X 10.10` (you must list this RID in the project file).</span></span>

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

<span data-ttu-id="55c56-208">Publikování aktuální aplikace, ale neobnovování odkazů na projekt na projekt (P2P), pouze kořenový projekt během operace obnovení (.NET Core SDK 2,0 a novější verze):</span><span class="sxs-lookup"><span data-stu-id="55c56-208">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet publish --no-dependencies`

## <a name="see-also"></a><span data-ttu-id="55c56-209">Viz také:</span><span class="sxs-lookup"><span data-stu-id="55c56-209">See also</span></span>

- [<span data-ttu-id="55c56-210">Cílové architektury</span><span class="sxs-lookup"><span data-stu-id="55c56-210">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="55c56-211">Katalog identifikátoru runtime (RID)</span><span class="sxs-lookup"><span data-stu-id="55c56-211">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
