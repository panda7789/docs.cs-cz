---
title: dotnet publish – příkaz
description: Příkaz dotnet publish publikuje projekt .NET Core do adresáře.
ms.date: 05/29/2018
ms.openlocfilehash: 4612c8cd1f63550905ef7c6d94af050892b1620c
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117615"
---
# <a name="dotnet-publish"></a><span data-ttu-id="d2c3e-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="d2c3e-103">dotnet publish</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="d2c3e-104">Name</span><span class="sxs-lookup"><span data-stu-id="d2c3e-104">Name</span></span>

<span data-ttu-id="d2c3e-105">`dotnet publish`– Zabalí aplikaci a její závislosti do složky pro nasazení do hostitelského systému.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-105">`dotnet publish` - Packs the application and its dependencies into a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d2c3e-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="d2c3e-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="d2c3e-107">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="d2c3e-107">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="d2c3e-108">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="d2c3e-108">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d2c3e-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="d2c3e-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
    [--version-suffix]
dotnet publish [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="d2c3e-110">Popis</span><span class="sxs-lookup"><span data-stu-id="d2c3e-110">Description</span></span>

<span data-ttu-id="d2c3e-111">`dotnet publish`zkompiluje aplikaci, přečte prostřednictvím svých závislostí zadaných v souboru projektu a publikuje výslednou sadu souborů do adresáře.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-111">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="d2c3e-112">Výstup obsahuje následující prostředky:</span><span class="sxs-lookup"><span data-stu-id="d2c3e-112">The output includes the following assets:</span></span>

- <span data-ttu-id="d2c3e-113">Kód zprostředkujícího jazyka (IL) v sestavení s příponou *DLL* .</span><span class="sxs-lookup"><span data-stu-id="d2c3e-113">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
- <span data-ttu-id="d2c3e-114">soubor *. DEPS. JSON* , který obsahuje všechny závislosti projektu.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-114">*.deps.json* file that includes all of the dependencies of the project.</span></span>
- <span data-ttu-id="d2c3e-115">soubor *. runtimeconfig. JSON* , který určuje sdílený modul runtime, který aplikace očekává, a další možnosti konfigurace pro modul runtime (například typ uvolňování paměti).</span><span class="sxs-lookup"><span data-stu-id="d2c3e-115">*.runtimeconfig.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
- <span data-ttu-id="d2c3e-116">Závislosti aplikace, které jsou zkopírovány z mezipaměti NuGet do výstupní složky.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-116">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="d2c3e-117">Výstup `dotnet publish` příkazu je připravený k nasazení do hostitelského systému (například server, počítač, Mac, notebook) k provedení.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-117">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="d2c3e-118">Jedná se o jediný oficiálně podporovaný způsob, jak připravit aplikaci pro nasazení.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-118">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="d2c3e-119">V závislosti na typu nasazení, které projekt určuje, hostující systém může nebo nemusí mít nainstalovaný modul .NET Core Shared runtime.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-119">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="d2c3e-120">Další informace najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="d2c3e-120">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span> <span data-ttu-id="d2c3e-121">Adresářovou strukturu publikované aplikace najdete v tématu [Struktura adresáře](/aspnet/core/hosting/directory-structure).</span><span class="sxs-lookup"><span data-stu-id="d2c3e-121">For the directory structure of a published application, see [Directory structure](/aspnet/core/hosting/directory-structure).</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="d2c3e-122">Arguments</span><span class="sxs-lookup"><span data-stu-id="d2c3e-122">Arguments</span></span>

`PROJECT`

<span data-ttu-id="d2c3e-123">Projekt, který se má publikovat</span><span class="sxs-lookup"><span data-stu-id="d2c3e-123">The project to publish.</span></span> <span data-ttu-id="d2c3e-124">Jedná se o cestu a název souboru [C#](csproj.md)projektu, F#nebo Visual Basic, nebo o cestu k adresáři, který obsahuje soubor projektu C#, F#nebo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-124">It's either the path and filename of a [C#](csproj.md), F#, or Visual Basic project file, or the path to a directory that contains a C#, F#, or Visual Basic project file.</span></span> <span data-ttu-id="d2c3e-125">Pokud není zadaný, použije se ve výchozím nastavení aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-125">If not specified, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="d2c3e-126">Možnosti</span><span class="sxs-lookup"><span data-stu-id="d2c3e-126">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="d2c3e-127">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="d2c3e-127">.NET Core 2.1</span></span>](#tab/netcore21)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="d2c3e-128">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-128">Defines the build configuration.</span></span> <span data-ttu-id="d2c3e-129">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-129">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="d2c3e-130">Publikuje aplikaci pro zadanou [cílovou architekturu](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="d2c3e-130">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="d2c3e-131">V souboru projektu je nutné zadat cílovou architekturu.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-131">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="d2c3e-132">Vynutí vyřešení všech závislostí i v případě, že bylo poslední obnovení úspěšné.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-132">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="d2c3e-133">Zadání tohoto příznaku je stejné jako odstranění souboru *Project. assets. JSON* .</span><span class="sxs-lookup"><span data-stu-id="d2c3e-133">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="d2c3e-134">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-134">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="d2c3e-135">Určuje jeden nebo několik [cílových manifestů](../deploying/runtime-store.md) , které se použijí ke zkrácení sady balíčků publikovaných s aplikací.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-135">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="d2c3e-136">Soubor manifestu je součástí výstupu [ `dotnet store` příkazu](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="d2c3e-136">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="d2c3e-137">Chcete-li zadat více manifestů, `--manifest` přidejte možnost pro každý manifest.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-137">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="d2c3e-138">Tato možnost je k dispozici počínaje verzí .NET Core 2,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-138">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-build`

<span data-ttu-id="d2c3e-139">Nevytvoří projekt před publikováním.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-139">Doesn't build the project before publishing.</span></span> <span data-ttu-id="d2c3e-140">Také implicitně nastaví `--no-restore` příznak.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-140">It also implicitly sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="d2c3e-141">Ignoruje odkazy z projektu na projekt a obnoví pouze kořenový projekt.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-141">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="d2c3e-142">Při spuštění příkazu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-142">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="d2c3e-143">Určuje cestu k výstupnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-143">Specifies the path for the output directory.</span></span> <span data-ttu-id="d2c3e-144">Pokud není zadaný, použije se výchozí hodnota *./bin/[Configuration]/[Framework]/Publish/* pro nasazení závislé na rozhraní nebo *./bin/[Configuration]/[Framework]/[runtime]/Publish/* pro samostatně uzavřené nasazení.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-144">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="d2c3e-145">Pokud je cesta relativní, vygenerovaný výstupní adresář je relativní vzhledem k umístění souboru projektu, nikoli k aktuálnímu pracovnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-145">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="d2c3e-146">Publikuje modul runtime .NET Core ve vaší aplikaci, takže modul runtime nemusí být na cílovém počítači nainstalován.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-146">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="d2c3e-147">Je-li zadán identifikátor modulu runtime, jeho výchozí hodnota `true`je.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-147">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="d2c3e-148">Další informace o různých typech nasazení naleznete v tématu [nasazení aplikace .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="d2c3e-148">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="d2c3e-149">Publikuje aplikaci pro daný modul runtime.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-149">Publishes the application for a given runtime.</span></span> <span data-ttu-id="d2c3e-150">Používá se při vytváření [samostatně zahrnutého nasazení (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="d2c3e-150">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="d2c3e-151">Seznam identifikátorů modulu runtime (identifikátorů RID) najdete v [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="d2c3e-151">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="d2c3e-152">Výchozím nastavením je publikování [nasazení závislého na rozhraní (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="d2c3e-152">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="d2c3e-153">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-153">Sets the verbosity level of the command.</span></span> <span data-ttu-id="d2c3e-154">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]` `d[etailed]`, a .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="d2c3e-154">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="d2c3e-155">Definuje příponu verze, která nahradí hvězdičku (`*`) v poli verze souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-155">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="d2c3e-156">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="d2c3e-156">.NET Core 2.0</span></span>](#tab/netcore20)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="d2c3e-157">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-157">Defines the build configuration.</span></span> <span data-ttu-id="d2c3e-158">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-158">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="d2c3e-159">Publikuje aplikaci pro zadanou [cílovou architekturu](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="d2c3e-159">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="d2c3e-160">V souboru projektu je nutné zadat cílovou architekturu.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-160">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="d2c3e-161">Vynutí vyřešení všech závislostí i v případě, že bylo poslední obnovení úspěšné.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-161">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="d2c3e-162">Zadání tohoto příznaku je stejné jako odstranění souboru *Project. assets. JSON* .</span><span class="sxs-lookup"><span data-stu-id="d2c3e-162">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="d2c3e-163">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-163">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="d2c3e-164">Určuje jeden nebo několik [cílových manifestů](../deploying/runtime-store.md) , které se použijí ke zkrácení sady balíčků publikovaných s aplikací.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-164">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="d2c3e-165">Soubor manifestu je součástí výstupu [ `dotnet store` příkazu](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="d2c3e-165">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="d2c3e-166">Chcete-li zadat více manifestů, `--manifest` přidejte možnost pro každý manifest.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-166">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="d2c3e-167">Tato možnost je k dispozici počínaje verzí .NET Core 2,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-167">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-dependencies`

<span data-ttu-id="d2c3e-168">Ignoruje odkazy z projektu na projekt a obnoví pouze kořenový projekt.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-168">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="d2c3e-169">Při spuštění příkazu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-169">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="d2c3e-170">Určuje cestu k výstupnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-170">Specifies the path for the output directory.</span></span> <span data-ttu-id="d2c3e-171">Pokud není zadaný, použije se výchozí hodnota *./bin/[Configuration]/[Framework]/Publish/* pro nasazení závislé na rozhraní nebo *./bin/[Configuration]/[Framework]/[runtime]/Publish/* pro samostatně uzavřené nasazení.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-171">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="d2c3e-172">Pokud je cesta relativní, vygenerovaný výstupní adresář je relativní vzhledem k umístění souboru projektu, nikoli k aktuálnímu pracovnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-172">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="d2c3e-173">Publikuje modul runtime .NET Core ve vaší aplikaci, takže modul runtime nemusí být na cílovém počítači nainstalován.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-173">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="d2c3e-174">Je-li zadán identifikátor modulu runtime, jeho výchozí hodnota `true`je.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-174">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="d2c3e-175">Další informace o různých typech nasazení naleznete v tématu [nasazení aplikace .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="d2c3e-175">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="d2c3e-176">Publikuje aplikaci pro daný modul runtime.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-176">Publishes the application for a given runtime.</span></span> <span data-ttu-id="d2c3e-177">Používá se při vytváření [samostatně zahrnutého nasazení (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="d2c3e-177">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="d2c3e-178">Seznam identifikátorů modulu runtime (identifikátorů RID) najdete v [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="d2c3e-178">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="d2c3e-179">Výchozím nastavením je publikování [nasazení závislého na rozhraní (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="d2c3e-179">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="d2c3e-180">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-180">Sets the verbosity level of the command.</span></span> <span data-ttu-id="d2c3e-181">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]` `d[etailed]`, a .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="d2c3e-181">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="d2c3e-182">Definuje příponu verze, která nahradí hvězdičku (`*`) v poli verze souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-182">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d2c3e-183">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="d2c3e-183">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="d2c3e-184">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-184">Defines the build configuration.</span></span> <span data-ttu-id="d2c3e-185">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-185">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="d2c3e-186">Publikuje aplikaci pro zadanou [cílovou architekturu](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="d2c3e-186">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="d2c3e-187">V souboru projektu je nutné zadat cílovou architekturu.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-187">You must specify the target framework in the project file.</span></span>

`-h|--help`

<span data-ttu-id="d2c3e-188">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-188">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="d2c3e-189">Určuje jeden nebo několik [cílových manifestů](../deploying/runtime-store.md) , které se použijí ke zkrácení sady balíčků publikovaných s aplikací.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-189">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="d2c3e-190">Soubor manifestu je součástí výstupu [ `dotnet store` příkazu](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="d2c3e-190">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="d2c3e-191">Chcete-li zadat více manifestů, `--manifest` přidejte možnost pro každý manifest.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-191">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="d2c3e-192">Tato možnost je k dispozici počínaje verzí .NET Core 2,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-192">This option is available starting with .NET Core 2.0 SDK.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="d2c3e-193">Určuje cestu k výstupnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-193">Specifies the path for the output directory.</span></span> <span data-ttu-id="d2c3e-194">Pokud není zadaný, použije se výchozí hodnota *./bin/[Configuration]/[Framework]/Publish/* pro nasazení závislé na rozhraní nebo *./bin/[Configuration]/[Framework]/[runtime]/Publish/* pro samostatně uzavřené nasazení.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-194">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="d2c3e-195">Pokud je cesta relativní, vygenerovaný výstupní adresář je relativní vzhledem k umístění souboru projektu, nikoli k aktuálnímu pracovnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-195">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="d2c3e-196">Publikuje aplikaci pro daný modul runtime.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-196">Publishes the application for a given runtime.</span></span> <span data-ttu-id="d2c3e-197">Používá se při vytváření [samostatně zahrnutého nasazení (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="d2c3e-197">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="d2c3e-198">Seznam identifikátorů modulu runtime (identifikátorů RID) najdete v [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="d2c3e-198">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="d2c3e-199">Výchozím nastavením je publikování [nasazení závislého na rozhraní (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="d2c3e-199">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="d2c3e-200">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-200">Sets the verbosity level of the command.</span></span> <span data-ttu-id="d2c3e-201">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]` `d[etailed]`, a .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="d2c3e-201">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="d2c3e-202">Definuje příponu verze, která nahradí hvězdičku (`*`) v poli verze souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="d2c3e-202">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

---

## <a name="examples"></a><span data-ttu-id="d2c3e-203">Příklady</span><span class="sxs-lookup"><span data-stu-id="d2c3e-203">Examples</span></span>

<span data-ttu-id="d2c3e-204">Publikovat projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="d2c3e-204">Publish the project in the current directory:</span></span>

`dotnet publish`

<span data-ttu-id="d2c3e-205">Publikovat aplikaci pomocí zadaného souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="d2c3e-205">Publish the application using the specified project file:</span></span>

`dotnet publish ~/projects/app1/app1.csproj`

<span data-ttu-id="d2c3e-206">Publikování projektu v aktuálním adresáři pomocí `netcoreapp1.1` rozhraní:</span><span class="sxs-lookup"><span data-stu-id="d2c3e-206">Publish the project in the current directory using the `netcoreapp1.1` framework:</span></span>

`dotnet publish --framework netcoreapp1.1`

<span data-ttu-id="d2c3e-207">Publikování aktuální aplikace pomocí `netcoreapp1.1` architektury a modulu runtime pro `OS X 10.10` (Tento identifikátor RID musíte uvést v souboru projektu).</span><span class="sxs-lookup"><span data-stu-id="d2c3e-207">Publish the current application using the `netcoreapp1.1` framework and the runtime for `OS X 10.10` (you must list this RID in the project file).</span></span>

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

<span data-ttu-id="d2c3e-208">Publikování aktuální aplikace, ale neobnovování odkazů na projekt na projekt (P2P), pouze kořenový projekt během operace obnovení (.NET Core SDK 2,0 a novější verze):</span><span class="sxs-lookup"><span data-stu-id="d2c3e-208">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet publish --no-dependencies`

## <a name="see-also"></a><span data-ttu-id="d2c3e-209">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d2c3e-209">See also</span></span>

- [<span data-ttu-id="d2c3e-210">Cílové architektury</span><span class="sxs-lookup"><span data-stu-id="d2c3e-210">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="d2c3e-211">Katalog identifikátoru runtime (RID)</span><span class="sxs-lookup"><span data-stu-id="d2c3e-211">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
