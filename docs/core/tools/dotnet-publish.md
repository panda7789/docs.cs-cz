---
title: DotNet publikovat příkaz – rozhraní příkazového řádku .NET Core
description: Dotnet publikovat příkaz publikuje do adresáře projektu .NET Core.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 38224aa8472f99df107e523667e18892384a20b0
ms.sourcegitcommit: f6343b070f3c66877338a05c8bfb0be9985255e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2018
ms.locfileid: "39220669"
---
# <a name="dotnet-publish"></a><span data-ttu-id="70b9a-103">publikování DotNet</span><span class="sxs-lookup"><span data-stu-id="70b9a-103">dotnet publish</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="70b9a-104">Název</span><span class="sxs-lookup"><span data-stu-id="70b9a-104">Name</span></span>

<span data-ttu-id="70b9a-105">`dotnet publish` – Balíčky aplikace a jeho závislosti do složky pro nasazení do hostujícího systému.</span><span class="sxs-lookup"><span data-stu-id="70b9a-105">`dotnet publish` - Packs the application and its dependencies into a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="70b9a-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="70b9a-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="70b9a-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="70b9a-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="70b9a-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="70b9a-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="70b9a-109">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="70b9a-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
    [--version-suffix]
dotnet publish [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="70b9a-110">Popis</span><span class="sxs-lookup"><span data-stu-id="70b9a-110">Description</span></span>

<span data-ttu-id="70b9a-111">`dotnet publish` zkompiluje aplikaci, přečte závislých zadané v souboru projektu a publikuje výslednou sadu souborů do adresáře.</span><span class="sxs-lookup"><span data-stu-id="70b9a-111">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="70b9a-112">Výstup zahrnuje následující prostředky:</span><span class="sxs-lookup"><span data-stu-id="70b9a-112">The output includes the following assets:</span></span>

* <span data-ttu-id="70b9a-113">Zprostředkující jazyk (IL) kódu v sestavení *dll* rozšíření.</span><span class="sxs-lookup"><span data-stu-id="70b9a-113">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
* <span data-ttu-id="70b9a-114">*. deps.json* soubor, který zahrnuje všechny závislosti projektu.</span><span class="sxs-lookup"><span data-stu-id="70b9a-114">*.deps.json* file that includes all of the dependencies of the project.</span></span>
* <span data-ttu-id="70b9a-115">*. runtime.config.json* soubor, který určuje sdílený modul runtime, který aplikace očekává, a také další možnosti konfigurace pro modul runtime (například typ kolekce uvolnění paměti).</span><span class="sxs-lookup"><span data-stu-id="70b9a-115">*.runtime.config.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
* <span data-ttu-id="70b9a-116">Závislosti aplikace, které se kopírují z mezipaměti NuGet do výstupní složky.</span><span class="sxs-lookup"><span data-stu-id="70b9a-116">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="70b9a-117">`dotnet publish` Výstupu příkazu je připravená k nasazení do hostujícího systému (třeba server, PC, Mac, přenosných počítačů) pro spuštění.</span><span class="sxs-lookup"><span data-stu-id="70b9a-117">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="70b9a-118">Je oficiálně podporované jedině Příprava aplikace pro nasazení.</span><span class="sxs-lookup"><span data-stu-id="70b9a-118">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="70b9a-119">V závislosti na typu nasazení, které určuje projekt hostitelském systému může nebo nemusí mít .NET Core sdílený modul runtime na něm nainstalován.</span><span class="sxs-lookup"><span data-stu-id="70b9a-119">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="70b9a-120">Další informace najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="70b9a-120">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span> <span data-ttu-id="70b9a-121">Struktura adresářů je publikovaná aplikace, najdete v části [adresářovou strukturu](/aspnet/core/hosting/directory-structure).</span><span class="sxs-lookup"><span data-stu-id="70b9a-121">For the directory structure of a published application, see [Directory structure](/aspnet/core/hosting/directory-structure).</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="70b9a-122">Arguments</span><span class="sxs-lookup"><span data-stu-id="70b9a-122">Arguments</span></span>

`PROJECT`

<span data-ttu-id="70b9a-123">Projekt pro publikování.</span><span class="sxs-lookup"><span data-stu-id="70b9a-123">The project to publish.</span></span> <span data-ttu-id="70b9a-124">Pokud není zadán, použije se výchozí do aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="70b9a-124">If not specified, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="70b9a-125">Možnosti</span><span class="sxs-lookup"><span data-stu-id="70b9a-125">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="70b9a-126">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="70b9a-126">.NET Core 2.1</span></span>](#tab/netcore21)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="70b9a-127">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="70b9a-127">Defines the build configuration.</span></span> <span data-ttu-id="70b9a-128">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="70b9a-128">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="70b9a-129">Publikuje aplikace pro danou [Cílová architektura](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="70b9a-129">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="70b9a-130">V souboru projektu je nutné zadat cílovou architekturu.</span><span class="sxs-lookup"><span data-stu-id="70b9a-130">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="70b9a-131">Způsobí, že všechny závislosti vyřešit i v případě, že poslední obnovení bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="70b9a-131">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="70b9a-132">Zadání tohoto příznaku je stejný jako odstranění *project.assets.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="70b9a-132">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="70b9a-133">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="70b9a-133">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="70b9a-134">Určuje jeden nebo několik [cílit manifesty](../deploying/runtime-store.md) oříznout sadu balíčků, které jsou publikované v aplikaci používat.</span><span class="sxs-lookup"><span data-stu-id="70b9a-134">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="70b9a-135">Soubor manifestu je část výstupu [ `dotnet store` příkaz](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="70b9a-135">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="70b9a-136">Chcete-li zadat více manifesty, přidejte `--manifest` možnost pro každý manifest.</span><span class="sxs-lookup"><span data-stu-id="70b9a-136">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="70b9a-137">Tato možnost je k dispozici od verze rozhraní .NET Core 2.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="70b9a-137">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-build`

<span data-ttu-id="70b9a-138">Nedaří sestavit projekt před publikováním.</span><span class="sxs-lookup"><span data-stu-id="70b9a-138">Doesn't build the project before publishing.</span></span> <span data-ttu-id="70b9a-139">Také implicitní nastaví `--no-restore` příznak.</span><span class="sxs-lookup"><span data-stu-id="70b9a-139">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="70b9a-140">Ignoruje odkazy typu projekt projekt a obnoví pouze zadané kořenového projektu.</span><span class="sxs-lookup"><span data-stu-id="70b9a-140">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="70b9a-141">Při spuštění příkazu se nebude spouštět implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="70b9a-141">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="70b9a-142">Určuje cestu k výstupnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="70b9a-142">Specifies the path for the output directory.</span></span> <span data-ttu-id="70b9a-143">Pokud není zadán, použije se výchozí *./bin/[configuration]/[framework]/publish/* nasazení závisí na architektuře nebo *./bin/[configuration]/[framework]/[runtime]/publish/* pro samostatná nasazení.</span><span class="sxs-lookup"><span data-stu-id="70b9a-143">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="70b9a-144">Pokud je relativní cesta, vygeneruje výstupní adresář je relativní vzhledem k umístění souboru projektu, ne do aktuálního pracovního adresáře.</span><span class="sxs-lookup"><span data-stu-id="70b9a-144">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="70b9a-145">Publikuje modulu runtime .NET Core s vaší aplikací, modul runtime nemusí být nainstalovaný na cílovém počítači.</span><span class="sxs-lookup"><span data-stu-id="70b9a-145">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="70b9a-146">Pokud je zadaný identifikátor modulu runtime, výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="70b9a-146">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="70b9a-147">Další informace o různých typů najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="70b9a-147">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="70b9a-148">Publikuje aplikace pro daný modul runtime.</span><span class="sxs-lookup"><span data-stu-id="70b9a-148">Publishes the application for a given runtime.</span></span> <span data-ttu-id="70b9a-149">Používá se při vytváření [samostatná nasazení (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="70b9a-149">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="70b9a-150">Seznam identifikátorů modulů Runtime (RID), najdete v článku [katalog identifikátorů RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="70b9a-150">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="70b9a-151">Výchozí hodnota je publikovat [nasazení závisí na architektuře (chyba)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="70b9a-151">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="70b9a-152">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="70b9a-152">Sets the verbosity level of the command.</span></span> <span data-ttu-id="70b9a-153">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="70b9a-153">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="70b9a-154">Definuje verze příponu, která má nahradit hvězdičku (`*`) v poli verze souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="70b9a-154">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="70b9a-155">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="70b9a-155">.NET Core 2.0</span></span>](#tab/netcore20)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="70b9a-156">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="70b9a-156">Defines the build configuration.</span></span> <span data-ttu-id="70b9a-157">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="70b9a-157">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="70b9a-158">Publikuje aplikace pro danou [Cílová architektura](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="70b9a-158">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="70b9a-159">V souboru projektu je nutné zadat cílovou architekturu.</span><span class="sxs-lookup"><span data-stu-id="70b9a-159">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="70b9a-160">Způsobí, že všechny závislosti vyřešit i v případě, že poslední obnovení bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="70b9a-160">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="70b9a-161">Zadání tohoto příznaku je stejný jako odstranění *project.assets.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="70b9a-161">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="70b9a-162">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="70b9a-162">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="70b9a-163">Určuje jeden nebo několik [cílit manifesty](../deploying/runtime-store.md) oříznout sadu balíčků, které jsou publikované v aplikaci používat.</span><span class="sxs-lookup"><span data-stu-id="70b9a-163">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="70b9a-164">Soubor manifestu je část výstupu [ `dotnet store` příkaz](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="70b9a-164">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="70b9a-165">Chcete-li zadat více manifesty, přidejte `--manifest` možnost pro každý manifest.</span><span class="sxs-lookup"><span data-stu-id="70b9a-165">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="70b9a-166">Tato možnost je k dispozici od verze rozhraní .NET Core 2.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="70b9a-166">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-dependencies`

<span data-ttu-id="70b9a-167">Ignoruje odkazy typu projekt projekt a obnoví pouze zadané kořenového projektu.</span><span class="sxs-lookup"><span data-stu-id="70b9a-167">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="70b9a-168">Při spuštění příkazu se nebude spouštět implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="70b9a-168">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="70b9a-169">Určuje cestu k výstupnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="70b9a-169">Specifies the path for the output directory.</span></span> <span data-ttu-id="70b9a-170">Pokud není zadán, použije se výchozí *./bin/[configuration]/[framework]/publish/* nasazení závisí na architektuře nebo *./bin/[configuration]/[framework]/[runtime]/publish/* pro samostatná nasazení.</span><span class="sxs-lookup"><span data-stu-id="70b9a-170">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="70b9a-171">Pokud je relativní cesta, vygeneruje výstupní adresář je relativní vzhledem k umístění souboru projektu, ne do aktuálního pracovního adresáře.</span><span class="sxs-lookup"><span data-stu-id="70b9a-171">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="70b9a-172">Publikuje modulu runtime .NET Core s vaší aplikací, modul runtime nemusí být nainstalovaný na cílovém počítači.</span><span class="sxs-lookup"><span data-stu-id="70b9a-172">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="70b9a-173">Pokud je zadaný identifikátor modulu runtime, výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="70b9a-173">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="70b9a-174">Další informace o různých typů najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="70b9a-174">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="70b9a-175">Publikuje aplikace pro daný modul runtime.</span><span class="sxs-lookup"><span data-stu-id="70b9a-175">Publishes the application for a given runtime.</span></span> <span data-ttu-id="70b9a-176">Používá se při vytváření [samostatná nasazení (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="70b9a-176">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="70b9a-177">Seznam identifikátorů modulů Runtime (RID), najdete v článku [katalog identifikátorů RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="70b9a-177">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="70b9a-178">Výchozí hodnota je publikovat [nasazení závisí na architektuře (chyba)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="70b9a-178">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="70b9a-179">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="70b9a-179">Sets the verbosity level of the command.</span></span> <span data-ttu-id="70b9a-180">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="70b9a-180">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="70b9a-181">Definuje verze příponu, která má nahradit hvězdičku (`*`) v poli verze souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="70b9a-181">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="70b9a-182">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="70b9a-182">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="70b9a-183">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="70b9a-183">Defines the build configuration.</span></span> <span data-ttu-id="70b9a-184">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="70b9a-184">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="70b9a-185">Publikuje aplikace pro danou [Cílová architektura](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="70b9a-185">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="70b9a-186">V souboru projektu je nutné zadat cílovou architekturu.</span><span class="sxs-lookup"><span data-stu-id="70b9a-186">You must specify the target framework in the project file.</span></span>

`-h|--help`

<span data-ttu-id="70b9a-187">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="70b9a-187">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="70b9a-188">Určuje jeden nebo několik [cílit manifesty](../deploying/runtime-store.md) oříznout sadu balíčků, které jsou publikované v aplikaci používat.</span><span class="sxs-lookup"><span data-stu-id="70b9a-188">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="70b9a-189">Soubor manifestu je část výstupu [ `dotnet store` příkaz](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="70b9a-189">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="70b9a-190">Chcete-li zadat více manifesty, přidejte `--manifest` možnost pro každý manifest.</span><span class="sxs-lookup"><span data-stu-id="70b9a-190">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="70b9a-191">Tato možnost je k dispozici od verze rozhraní .NET Core 2.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="70b9a-191">This option is available starting with .NET Core 2.0 SDK.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="70b9a-192">Určuje cestu k výstupnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="70b9a-192">Specifies the path for the output directory.</span></span> <span data-ttu-id="70b9a-193">Pokud není zadán, použije se výchozí *./bin/[configuration]/[framework]/publish/* nasazení závisí na architektuře nebo *./bin/[configuration]/[framework]/[runtime]/publish/* pro samostatná nasazení.</span><span class="sxs-lookup"><span data-stu-id="70b9a-193">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="70b9a-194">Pokud je relativní cesta, vygeneruje výstupní adresář je relativní vzhledem k umístění souboru projektu, ne do aktuálního pracovního adresáře.</span><span class="sxs-lookup"><span data-stu-id="70b9a-194">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="70b9a-195">Publikuje aplikace pro daný modul runtime.</span><span class="sxs-lookup"><span data-stu-id="70b9a-195">Publishes the application for a given runtime.</span></span> <span data-ttu-id="70b9a-196">Používá se při vytváření [samostatná nasazení (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="70b9a-196">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="70b9a-197">Seznam identifikátorů modulů Runtime (RID), najdete v článku [katalog identifikátorů RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="70b9a-197">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="70b9a-198">Výchozí hodnota je publikovat [nasazení závisí na architektuře (chyba)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="70b9a-198">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="70b9a-199">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="70b9a-199">Sets the verbosity level of the command.</span></span> <span data-ttu-id="70b9a-200">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="70b9a-200">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="70b9a-201">Definuje verze příponu, která má nahradit hvězdičku (`*`) v poli verze souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="70b9a-201">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

---

## <a name="examples"></a><span data-ttu-id="70b9a-202">Příklady</span><span class="sxs-lookup"><span data-stu-id="70b9a-202">Examples</span></span>

<span data-ttu-id="70b9a-203">Publikujte projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="70b9a-203">Publish the project in the current directory:</span></span>

`dotnet publish`

<span data-ttu-id="70b9a-204">Publikování aplikace pomocí zadaný soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="70b9a-204">Publish the application using the specified project file:</span></span>

`dotnet publish ~/projects/app1/app1.csproj`

<span data-ttu-id="70b9a-205">Publikujte projekt v aktuálním adresáři pomocí `netcoreapp1.1` framework:</span><span class="sxs-lookup"><span data-stu-id="70b9a-205">Publish the project in the current directory using the `netcoreapp1.1` framework:</span></span>

`dotnet publish --framework netcoreapp1.1`

<span data-ttu-id="70b9a-206">Publikujte aktuální aplikace pomocí `netcoreapp1.1` rozhraní framework a modulu runtime pro `OS X 10.10` (musí uvést tento identifikátorů RID v souboru projektu).</span><span class="sxs-lookup"><span data-stu-id="70b9a-206">Publish the current application using the `netcoreapp1.1` framework and the runtime for `OS X 10.10` (you must list this RID in the project file).</span></span>

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

<span data-ttu-id="70b9a-207">Aktuální aplikaci publikovat, ale nechcete obnovit odkazy na projekt na projekt (P2P), jenom kořenový projektu během operace obnovení (.NET Core SDK 2.0 a novější):</span><span class="sxs-lookup"><span data-stu-id="70b9a-207">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet publish --no-dependencies`

## <a name="see-also"></a><span data-ttu-id="70b9a-208">Viz také:</span><span class="sxs-lookup"><span data-stu-id="70b9a-208">See also</span></span>

* [<span data-ttu-id="70b9a-209">Cílové verze rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="70b9a-209">Target frameworks</span></span>](../../standard/frameworks.md)
* [<span data-ttu-id="70b9a-210">Identifikátor modulu runtime (RID) katalogu</span><span class="sxs-lookup"><span data-stu-id="70b9a-210">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
