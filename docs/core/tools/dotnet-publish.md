---
title: příkaz - .NET Core rozhraní příkazového řádku publikování DotNet.
description: Příkaz Publikovat dotnet publikuje do adresáře projektu .NET Core.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 38224aa8472f99df107e523667e18892384a20b0
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696657"
---
# <a name="dotnet-publish"></a><span data-ttu-id="8e73d-103">publikování DotNet.</span><span class="sxs-lookup"><span data-stu-id="8e73d-103">dotnet publish</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="8e73d-104">Název</span><span class="sxs-lookup"><span data-stu-id="8e73d-104">Name</span></span>

<span data-ttu-id="8e73d-105">`dotnet publish` -Pack aplikace a jeho závislosti do složky pro nasazení k hostování systému.</span><span class="sxs-lookup"><span data-stu-id="8e73d-105">`dotnet publish` - Packs the application and its dependencies into a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="8e73d-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="8e73d-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="8e73d-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="8e73d-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="8e73d-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="8e73d-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="8e73d-109">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="8e73d-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
    [--version-suffix]
dotnet publish [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="8e73d-110">Popis</span><span class="sxs-lookup"><span data-stu-id="8e73d-110">Description</span></span>

<span data-ttu-id="8e73d-111">`dotnet publish` zkompiluje aplikace, čte prostřednictvím jeho závislé součásti, zadaný v souboru projektu a publikuje výslednou sadu soubory do adresáře.</span><span class="sxs-lookup"><span data-stu-id="8e73d-111">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="8e73d-112">Výstup obsahuje následující prostředky:</span><span class="sxs-lookup"><span data-stu-id="8e73d-112">The output includes the following assets:</span></span>

* <span data-ttu-id="8e73d-113">Kód jazyka (IL) v sestavení s mezilehlé *dll* rozšíření.</span><span class="sxs-lookup"><span data-stu-id="8e73d-113">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
* <span data-ttu-id="8e73d-114">*. deps.json* soubor, který zahrnuje všechny závislosti projektu.</span><span class="sxs-lookup"><span data-stu-id="8e73d-114">*.deps.json* file that includes all of the dependencies of the project.</span></span>
* <span data-ttu-id="8e73d-115">*. runtime.config.json* soubor, který určuje sdílený modul runtime, který aplikace očekává a také další možnosti konfigurace pro modul runtime (například uvolňování paměti – typ kolekce).</span><span class="sxs-lookup"><span data-stu-id="8e73d-115">*.runtime.config.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
* <span data-ttu-id="8e73d-116">Závislosti aplikace, které se zkopírují z mezipaměti NuGet do výstupní složky.</span><span class="sxs-lookup"><span data-stu-id="8e73d-116">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="8e73d-117">`dotnet publish` Výstup příkazu je připraven k nasazení k hostování systému (například server, PC, Mac, přenosných počítačů) pro provedení.</span><span class="sxs-lookup"><span data-stu-id="8e73d-117">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="8e73d-118">Je oficiálně podporované jedině Příprava aplikací pro nasazení.</span><span class="sxs-lookup"><span data-stu-id="8e73d-118">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="8e73d-119">V závislosti na typu nasazení, který určuje projekt hostitelský systém může nebo nemusí mít .NET Core sdílené na něm nainstalován modul runtime.</span><span class="sxs-lookup"><span data-stu-id="8e73d-119">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="8e73d-120">Další informace najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="8e73d-120">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span> <span data-ttu-id="8e73d-121">Struktura adresářů publikované aplikace, najdete v části [adresářovou strukturu](/aspnet/core/hosting/directory-structure).</span><span class="sxs-lookup"><span data-stu-id="8e73d-121">For the directory structure of a published application, see [Directory structure](/aspnet/core/hosting/directory-structure).</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="8e73d-122">Arguments</span><span class="sxs-lookup"><span data-stu-id="8e73d-122">Arguments</span></span>

`PROJECT`

<span data-ttu-id="8e73d-123">Projekt k publikování.</span><span class="sxs-lookup"><span data-stu-id="8e73d-123">The project to publish.</span></span> <span data-ttu-id="8e73d-124">Pokud není zadáno, výchozí hodnoty k aktuálnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="8e73d-124">If not specified, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="8e73d-125">Možnosti</span><span class="sxs-lookup"><span data-stu-id="8e73d-125">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="8e73d-126">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="8e73d-126">.NET Core 2.1</span></span>](#tab/netcore21)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="8e73d-127">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="8e73d-127">Defines the build configuration.</span></span> <span data-ttu-id="8e73d-128">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="8e73d-128">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="8e73d-129">Publikuje aplikace pro zadaný [cílové rozhraní](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="8e73d-129">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="8e73d-130">Musíte zadat cílové rozhraní v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="8e73d-130">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="8e73d-131">Vynutí všechny závislosti pro přeloženy i v případě, že poslední obnovení bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="8e73d-131">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="8e73d-132">Zadáním tohoto příznaku je stejný jako odstranění *project.assets.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="8e73d-132">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="8e73d-133">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="8e73d-133">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="8e73d-134">Určuje jeden nebo několik [cíle manifesty](../deploying/runtime-store.md) sloužící k uvolnění dočasné paměti sadu balíčků, které jsou publikovány v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8e73d-134">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="8e73d-135">Soubor manifestu je součástí výstup [ `dotnet store` příkaz](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="8e73d-135">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="8e73d-136">Chcete-li zadat více manifesty, přidejte `--manifest` možnost pro každý manifest.</span><span class="sxs-lookup"><span data-stu-id="8e73d-136">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="8e73d-137">Tato možnost je dostupná od verze rozhraní .NET Core 2.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="8e73d-137">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-build`

<span data-ttu-id="8e73d-138">Není sestavení projektu před publikováním.</span><span class="sxs-lookup"><span data-stu-id="8e73d-138">Doesn't build the project before publishing.</span></span> <span data-ttu-id="8e73d-139">Také implicitní nastaví `--no-restore` příznak.</span><span class="sxs-lookup"><span data-stu-id="8e73d-139">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="8e73d-140">Ignoruje odkazy na projekt na projekt a obnoví pouze kořenové projektu.</span><span class="sxs-lookup"><span data-stu-id="8e73d-140">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="8e73d-141">Implicitní obnovení není spustit, když spustíte příkaz.</span><span class="sxs-lookup"><span data-stu-id="8e73d-141">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="8e73d-142">Určuje cestu k výstupnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="8e73d-142">Specifies the path for the output directory.</span></span> <span data-ttu-id="8e73d-143">Pokud není zadáno, je standardně *./bin/[configuration]/[framework]/publish/* pro nasazení závislé na framework nebo *./bin/[configuration]/[framework]/[runtime]/publish/* pro samostatná nasazení.</span><span class="sxs-lookup"><span data-stu-id="8e73d-143">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="8e73d-144">Pokud je relativní cesta, výstupní adresář generované je relativní k umístění souboru projektu, není pro aktuální pracovní adresář.</span><span class="sxs-lookup"><span data-stu-id="8e73d-144">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="8e73d-145">Publikuje na .NET Core runtime s vaší aplikací, takže modul runtime nemusí být nainstalován v cílovém počítači.</span><span class="sxs-lookup"><span data-stu-id="8e73d-145">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="8e73d-146">Pokud je zadán identifikátor runtime, výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="8e73d-146">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="8e73d-147">Další informace o různých typů najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="8e73d-147">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="8e73d-148">Publikuje aplikace pro daný modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="8e73d-148">Publishes the application for a given runtime.</span></span> <span data-ttu-id="8e73d-149">Používá se při vytváření [samostatná nasazení (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="8e73d-149">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="8e73d-150">Seznam Runtime identifikátorů (RID), najdete v článku [identifikátorů RID katalogu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="8e73d-150">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="8e73d-151">Výchozí hodnota je publikování [nasazení závislé na framework (disketové jednotky)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="8e73d-151">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="8e73d-152">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="8e73d-152">Sets the verbosity level of the command.</span></span> <span data-ttu-id="8e73d-153">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="8e73d-153">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="8e73d-154">Definuje příponu verze, která má nahradit hvězdičku (`*`) v poli verze souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="8e73d-154">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="8e73d-155">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="8e73d-155">.NET Core 2.0</span></span>](#tab/netcore20)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="8e73d-156">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="8e73d-156">Defines the build configuration.</span></span> <span data-ttu-id="8e73d-157">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="8e73d-157">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="8e73d-158">Publikuje aplikace pro zadaný [cílové rozhraní](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="8e73d-158">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="8e73d-159">Musíte zadat cílové rozhraní v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="8e73d-159">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="8e73d-160">Vynutí všechny závislosti pro přeloženy i v případě, že poslední obnovení bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="8e73d-160">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="8e73d-161">Zadáním tohoto příznaku je stejný jako odstranění *project.assets.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="8e73d-161">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="8e73d-162">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="8e73d-162">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="8e73d-163">Určuje jeden nebo několik [cíle manifesty](../deploying/runtime-store.md) sloužící k uvolnění dočasné paměti sadu balíčků, které jsou publikovány v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8e73d-163">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="8e73d-164">Soubor manifestu je součástí výstup [ `dotnet store` příkaz](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="8e73d-164">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="8e73d-165">Chcete-li zadat více manifesty, přidejte `--manifest` možnost pro každý manifest.</span><span class="sxs-lookup"><span data-stu-id="8e73d-165">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="8e73d-166">Tato možnost je dostupná od verze rozhraní .NET Core 2.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="8e73d-166">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-dependencies`

<span data-ttu-id="8e73d-167">Ignoruje odkazy na projekt na projekt a obnoví pouze kořenové projektu.</span><span class="sxs-lookup"><span data-stu-id="8e73d-167">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="8e73d-168">Implicitní obnovení není spustit, když spustíte příkaz.</span><span class="sxs-lookup"><span data-stu-id="8e73d-168">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="8e73d-169">Určuje cestu k výstupnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="8e73d-169">Specifies the path for the output directory.</span></span> <span data-ttu-id="8e73d-170">Pokud není zadáno, je standardně *./bin/[configuration]/[framework]/publish/* pro nasazení závislé na framework nebo *./bin/[configuration]/[framework]/[runtime]/publish/* pro samostatná nasazení.</span><span class="sxs-lookup"><span data-stu-id="8e73d-170">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="8e73d-171">Pokud je relativní cesta, výstupní adresář generované je relativní k umístění souboru projektu, není pro aktuální pracovní adresář.</span><span class="sxs-lookup"><span data-stu-id="8e73d-171">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="8e73d-172">Publikuje na .NET Core runtime s vaší aplikací, takže modul runtime nemusí být nainstalován v cílovém počítači.</span><span class="sxs-lookup"><span data-stu-id="8e73d-172">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="8e73d-173">Pokud je zadán identifikátor runtime, výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="8e73d-173">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="8e73d-174">Další informace o různých typů najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="8e73d-174">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="8e73d-175">Publikuje aplikace pro daný modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="8e73d-175">Publishes the application for a given runtime.</span></span> <span data-ttu-id="8e73d-176">Používá se při vytváření [samostatná nasazení (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="8e73d-176">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="8e73d-177">Seznam Runtime identifikátorů (RID), najdete v článku [identifikátorů RID katalogu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="8e73d-177">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="8e73d-178">Výchozí hodnota je publikování [nasazení závislé na framework (disketové jednotky)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="8e73d-178">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="8e73d-179">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="8e73d-179">Sets the verbosity level of the command.</span></span> <span data-ttu-id="8e73d-180">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="8e73d-180">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="8e73d-181">Definuje příponu verze, která má nahradit hvězdičku (`*`) v poli verze souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="8e73d-181">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="8e73d-182">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="8e73d-182">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="8e73d-183">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="8e73d-183">Defines the build configuration.</span></span> <span data-ttu-id="8e73d-184">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="8e73d-184">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="8e73d-185">Publikuje aplikace pro zadaný [cílové rozhraní](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="8e73d-185">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="8e73d-186">Musíte zadat cílové rozhraní v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="8e73d-186">You must specify the target framework in the project file.</span></span>

`-h|--help`

<span data-ttu-id="8e73d-187">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="8e73d-187">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="8e73d-188">Určuje jeden nebo několik [cíle manifesty](../deploying/runtime-store.md) sloužící k uvolnění dočasné paměti sadu balíčků, které jsou publikovány v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8e73d-188">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="8e73d-189">Soubor manifestu je součástí výstup [ `dotnet store` příkaz](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="8e73d-189">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="8e73d-190">Chcete-li zadat více manifesty, přidejte `--manifest` možnost pro každý manifest.</span><span class="sxs-lookup"><span data-stu-id="8e73d-190">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="8e73d-191">Tato možnost je dostupná od verze rozhraní .NET Core 2.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="8e73d-191">This option is available starting with .NET Core 2.0 SDK.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="8e73d-192">Určuje cestu k výstupnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="8e73d-192">Specifies the path for the output directory.</span></span> <span data-ttu-id="8e73d-193">Pokud není zadáno, je standardně *./bin/[configuration]/[framework]/publish/* pro nasazení závislé na framework nebo *./bin/[configuration]/[framework]/[runtime]/publish/* pro samostatná nasazení.</span><span class="sxs-lookup"><span data-stu-id="8e73d-193">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="8e73d-194">Pokud je relativní cesta, výstupní adresář generované je relativní k umístění souboru projektu, není pro aktuální pracovní adresář.</span><span class="sxs-lookup"><span data-stu-id="8e73d-194">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="8e73d-195">Publikuje aplikace pro daný modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="8e73d-195">Publishes the application for a given runtime.</span></span> <span data-ttu-id="8e73d-196">Používá se při vytváření [samostatná nasazení (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="8e73d-196">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="8e73d-197">Seznam Runtime identifikátorů (RID), najdete v článku [identifikátorů RID katalogu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="8e73d-197">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="8e73d-198">Výchozí hodnota je publikování [nasazení závislé na framework (disketové jednotky)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="8e73d-198">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="8e73d-199">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="8e73d-199">Sets the verbosity level of the command.</span></span> <span data-ttu-id="8e73d-200">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="8e73d-200">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="8e73d-201">Definuje příponu verze, která má nahradit hvězdičku (`*`) v poli verze souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="8e73d-201">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

---

## <a name="examples"></a><span data-ttu-id="8e73d-202">Příklady</span><span class="sxs-lookup"><span data-stu-id="8e73d-202">Examples</span></span>

<span data-ttu-id="8e73d-203">Publikování tohoto projektu v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="8e73d-203">Publish the project in the current directory:</span></span>

`dotnet publish`

<span data-ttu-id="8e73d-204">Publikování aplikace pomocí souboru zadaného projektu:</span><span class="sxs-lookup"><span data-stu-id="8e73d-204">Publish the application using the specified project file:</span></span>

`dotnet publish ~/projects/app1/app1.csproj`

<span data-ttu-id="8e73d-205">Publikování tohoto projektu v aktuálním adresáři pomocí `netcoreapp1.1` framework:</span><span class="sxs-lookup"><span data-stu-id="8e73d-205">Publish the project in the current directory using the `netcoreapp1.1` framework:</span></span>

`dotnet publish --framework netcoreapp1.1`

<span data-ttu-id="8e73d-206">Publikování aktuální aplikace pomocí `netcoreapp1.1` framework a prostředí runtime pro `OS X 10.10` (musí seznam tento identifikátorů RID v souboru projektu).</span><span class="sxs-lookup"><span data-stu-id="8e73d-206">Publish the current application using the `netcoreapp1.1` framework and the runtime for `OS X 10.10` (you must list this RID in the project file).</span></span>

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

<span data-ttu-id="8e73d-207">Publikování aktuální aplikace ale neobnoví odkazů na projekt na projekt (P2P), pouze v kořenové projektu během operace obnovení (.NET Core SDK 2.0 a novější):</span><span class="sxs-lookup"><span data-stu-id="8e73d-207">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet publish --no-dependencies`

## <a name="see-also"></a><span data-ttu-id="8e73d-208">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8e73d-208">See also</span></span>

* [<span data-ttu-id="8e73d-209">Cílové verze rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8e73d-209">Target frameworks</span></span>](../../standard/frameworks.md)
* [<span data-ttu-id="8e73d-210">Katalog identifikátor runtime (RID)</span><span class="sxs-lookup"><span data-stu-id="8e73d-210">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
