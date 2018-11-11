---
title: DotNet publikovat příkaz – rozhraní příkazového řádku .NET Core
description: Dotnet publikovat příkaz publikuje do adresáře projektu .NET Core.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 17bacc92eea90072b95b2d42a87cb57e9fa0be67
ms.sourcegitcommit: 3b1cb8467bd73dee854b604e306c0e7e3882d91a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2018
ms.locfileid: "43511421"
---
# <a name="dotnet-publish"></a><span data-ttu-id="efc00-103">publikování DotNet</span><span class="sxs-lookup"><span data-stu-id="efc00-103">dotnet publish</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="efc00-104">Název</span><span class="sxs-lookup"><span data-stu-id="efc00-104">Name</span></span>

<span data-ttu-id="efc00-105">`dotnet publish` – Balíčky aplikace a jeho závislosti do složky pro nasazení do hostujícího systému.</span><span class="sxs-lookup"><span data-stu-id="efc00-105">`dotnet publish` - Packs the application and its dependencies into a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="efc00-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="efc00-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="efc00-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="efc00-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="efc00-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="efc00-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="efc00-109">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="efc00-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
    [--version-suffix]
dotnet publish [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="efc00-110">Popis</span><span class="sxs-lookup"><span data-stu-id="efc00-110">Description</span></span>

<span data-ttu-id="efc00-111">`dotnet publish` zkompiluje aplikaci, přečte závislých zadané v souboru projektu a publikuje výslednou sadu souborů do adresáře.</span><span class="sxs-lookup"><span data-stu-id="efc00-111">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="efc00-112">Výstup zahrnuje následující prostředky:</span><span class="sxs-lookup"><span data-stu-id="efc00-112">The output includes the following assets:</span></span>

* <span data-ttu-id="efc00-113">Zprostředkující jazyk (IL) kódu v sestavení *dll* rozšíření.</span><span class="sxs-lookup"><span data-stu-id="efc00-113">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
* <span data-ttu-id="efc00-114">*. deps.json* soubor, který zahrnuje všechny závislosti projektu.</span><span class="sxs-lookup"><span data-stu-id="efc00-114">*.deps.json* file that includes all of the dependencies of the project.</span></span>
* <span data-ttu-id="efc00-115">*. runtime.config.json* soubor, který určuje sdílený modul runtime, který aplikace očekává, a také další možnosti konfigurace pro modul runtime (například typ kolekce uvolnění paměti).</span><span class="sxs-lookup"><span data-stu-id="efc00-115">*.runtime.config.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
* <span data-ttu-id="efc00-116">Závislosti aplikace, které se kopírují z mezipaměti NuGet do výstupní složky.</span><span class="sxs-lookup"><span data-stu-id="efc00-116">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="efc00-117">`dotnet publish` Výstupu příkazu je připravená k nasazení do hostujícího systému (třeba server, PC, Mac, přenosných počítačů) pro spuštění.</span><span class="sxs-lookup"><span data-stu-id="efc00-117">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="efc00-118">Je oficiálně podporované jedině Příprava aplikace pro nasazení.</span><span class="sxs-lookup"><span data-stu-id="efc00-118">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="efc00-119">V závislosti na typu nasazení, které určuje projekt hostitelském systému může nebo nemusí mít .NET Core sdílený modul runtime na něm nainstalován.</span><span class="sxs-lookup"><span data-stu-id="efc00-119">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="efc00-120">Další informace najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="efc00-120">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span> <span data-ttu-id="efc00-121">Struktura adresářů je publikovaná aplikace, najdete v části [adresářovou strukturu](/aspnet/core/hosting/directory-structure).</span><span class="sxs-lookup"><span data-stu-id="efc00-121">For the directory structure of a published application, see [Directory structure](/aspnet/core/hosting/directory-structure).</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="efc00-122">Arguments</span><span class="sxs-lookup"><span data-stu-id="efc00-122">Arguments</span></span>

`PROJECT`

<span data-ttu-id="efc00-123">Projekt pro publikování.</span><span class="sxs-lookup"><span data-stu-id="efc00-123">The project to publish.</span></span> <span data-ttu-id="efc00-124">Je cestu a název souboru [ C# ](csproj.md), F#, nebo soubor projektu jazyka Visual Basic, nebo cestu k adresáři, který obsahuje C#, F#, nebo soubor projektu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="efc00-124">It's either the path and filename of a [C#](csproj.md), F#, or Visual Basic project file, or the path to a directory that contains a C#, F#, or Visual Basic project file.</span></span> <span data-ttu-id="efc00-125">Pokud není zadán, použije se výchozí do aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="efc00-125">If not specified, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="efc00-126">Možnosti</span><span class="sxs-lookup"><span data-stu-id="efc00-126">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="efc00-127">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="efc00-127">.NET Core 2.1</span></span>](#tab/netcore21)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="efc00-128">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="efc00-128">Defines the build configuration.</span></span> <span data-ttu-id="efc00-129">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="efc00-129">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="efc00-130">Publikuje aplikace pro danou [Cílová architektura](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="efc00-130">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="efc00-131">V souboru projektu je nutné zadat cílovou architekturu.</span><span class="sxs-lookup"><span data-stu-id="efc00-131">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="efc00-132">Způsobí, že všechny závislosti vyřešit i v případě, že poslední obnovení bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="efc00-132">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="efc00-133">Zadání tohoto příznaku je stejný jako odstranění *project.assets.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="efc00-133">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="efc00-134">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="efc00-134">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="efc00-135">Určuje jeden nebo několik [cílit manifesty](../deploying/runtime-store.md) oříznout sadu balíčků, které jsou publikované v aplikaci používat.</span><span class="sxs-lookup"><span data-stu-id="efc00-135">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="efc00-136">Soubor manifestu je část výstupu [ `dotnet store` příkaz](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="efc00-136">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="efc00-137">Chcete-li zadat více manifesty, přidejte `--manifest` možnost pro každý manifest.</span><span class="sxs-lookup"><span data-stu-id="efc00-137">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="efc00-138">Tato možnost je k dispozici od verze rozhraní .NET Core 2.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="efc00-138">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-build`

<span data-ttu-id="efc00-139">Nedaří sestavit projekt před publikováním.</span><span class="sxs-lookup"><span data-stu-id="efc00-139">Doesn't build the project before publishing.</span></span> <span data-ttu-id="efc00-140">Také implicitně nastaví `--no-restore` příznak.</span><span class="sxs-lookup"><span data-stu-id="efc00-140">It also implicitly sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="efc00-141">Ignoruje odkazy typu projekt projekt a obnoví pouze zadané kořenového projektu.</span><span class="sxs-lookup"><span data-stu-id="efc00-141">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="efc00-142">Při spuštění příkazu se nebude spouštět implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="efc00-142">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="efc00-143">Určuje cestu k výstupnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="efc00-143">Specifies the path for the output directory.</span></span> <span data-ttu-id="efc00-144">Pokud není zadán, použije se výchozí *./bin/[configuration]/[framework]/publish/* nasazení závisí na architektuře nebo *./bin/[configuration]/[framework]/[runtime]/publish/* pro samostatná nasazení.</span><span class="sxs-lookup"><span data-stu-id="efc00-144">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="efc00-145">Pokud je relativní cesta, vygeneruje výstupní adresář je relativní vzhledem k umístění souboru projektu, ne do aktuálního pracovního adresáře.</span><span class="sxs-lookup"><span data-stu-id="efc00-145">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="efc00-146">Publikuje modulu runtime .NET Core s vaší aplikací, modul runtime nemusí být nainstalovaný na cílovém počítači.</span><span class="sxs-lookup"><span data-stu-id="efc00-146">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="efc00-147">Pokud je zadaný identifikátor modulu runtime, výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="efc00-147">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="efc00-148">Další informace o různých typů najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="efc00-148">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="efc00-149">Publikuje aplikace pro daný modul runtime.</span><span class="sxs-lookup"><span data-stu-id="efc00-149">Publishes the application for a given runtime.</span></span> <span data-ttu-id="efc00-150">Používá se při vytváření [samostatná nasazení (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="efc00-150">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="efc00-151">Seznam identifikátorů modulů Runtime (RID), najdete v článku [katalog identifikátorů RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="efc00-151">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="efc00-152">Výchozí hodnota je publikovat [nasazení závisí na architektuře (chyba)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="efc00-152">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="efc00-153">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="efc00-153">Sets the verbosity level of the command.</span></span> <span data-ttu-id="efc00-154">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="efc00-154">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="efc00-155">Definuje verze příponu, která má nahradit hvězdičku (`*`) v poli verze souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="efc00-155">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="efc00-156">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="efc00-156">.NET Core 2.0</span></span>](#tab/netcore20)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="efc00-157">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="efc00-157">Defines the build configuration.</span></span> <span data-ttu-id="efc00-158">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="efc00-158">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="efc00-159">Publikuje aplikace pro danou [Cílová architektura](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="efc00-159">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="efc00-160">V souboru projektu je nutné zadat cílovou architekturu.</span><span class="sxs-lookup"><span data-stu-id="efc00-160">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="efc00-161">Způsobí, že všechny závislosti vyřešit i v případě, že poslední obnovení bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="efc00-161">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="efc00-162">Zadání tohoto příznaku je stejný jako odstranění *project.assets.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="efc00-162">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="efc00-163">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="efc00-163">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="efc00-164">Určuje jeden nebo několik [cílit manifesty](../deploying/runtime-store.md) oříznout sadu balíčků, které jsou publikované v aplikaci používat.</span><span class="sxs-lookup"><span data-stu-id="efc00-164">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="efc00-165">Soubor manifestu je část výstupu [ `dotnet store` příkaz](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="efc00-165">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="efc00-166">Chcete-li zadat více manifesty, přidejte `--manifest` možnost pro každý manifest.</span><span class="sxs-lookup"><span data-stu-id="efc00-166">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="efc00-167">Tato možnost je k dispozici od verze rozhraní .NET Core 2.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="efc00-167">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-dependencies`

<span data-ttu-id="efc00-168">Ignoruje odkazy typu projekt projekt a obnoví pouze zadané kořenového projektu.</span><span class="sxs-lookup"><span data-stu-id="efc00-168">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="efc00-169">Při spuštění příkazu se nebude spouštět implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="efc00-169">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="efc00-170">Určuje cestu k výstupnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="efc00-170">Specifies the path for the output directory.</span></span> <span data-ttu-id="efc00-171">Pokud není zadán, použije se výchozí *./bin/[configuration]/[framework]/publish/* nasazení závisí na architektuře nebo *./bin/[configuration]/[framework]/[runtime]/publish/* pro samostatná nasazení.</span><span class="sxs-lookup"><span data-stu-id="efc00-171">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="efc00-172">Pokud je relativní cesta, vygeneruje výstupní adresář je relativní vzhledem k umístění souboru projektu, ne do aktuálního pracovního adresáře.</span><span class="sxs-lookup"><span data-stu-id="efc00-172">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="efc00-173">Publikuje modulu runtime .NET Core s vaší aplikací, modul runtime nemusí být nainstalovaný na cílovém počítači.</span><span class="sxs-lookup"><span data-stu-id="efc00-173">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="efc00-174">Pokud je zadaný identifikátor modulu runtime, výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="efc00-174">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="efc00-175">Další informace o různých typů najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="efc00-175">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="efc00-176">Publikuje aplikace pro daný modul runtime.</span><span class="sxs-lookup"><span data-stu-id="efc00-176">Publishes the application for a given runtime.</span></span> <span data-ttu-id="efc00-177">Používá se při vytváření [samostatná nasazení (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="efc00-177">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="efc00-178">Seznam identifikátorů modulů Runtime (RID), najdete v článku [katalog identifikátorů RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="efc00-178">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="efc00-179">Výchozí hodnota je publikovat [nasazení závisí na architektuře (chyba)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="efc00-179">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="efc00-180">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="efc00-180">Sets the verbosity level of the command.</span></span> <span data-ttu-id="efc00-181">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="efc00-181">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="efc00-182">Definuje verze příponu, která má nahradit hvězdičku (`*`) v poli verze souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="efc00-182">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="efc00-183">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="efc00-183">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="efc00-184">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="efc00-184">Defines the build configuration.</span></span> <span data-ttu-id="efc00-185">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="efc00-185">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="efc00-186">Publikuje aplikace pro danou [Cílová architektura](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="efc00-186">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="efc00-187">V souboru projektu je nutné zadat cílovou architekturu.</span><span class="sxs-lookup"><span data-stu-id="efc00-187">You must specify the target framework in the project file.</span></span>

`-h|--help`

<span data-ttu-id="efc00-188">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="efc00-188">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="efc00-189">Určuje jeden nebo několik [cílit manifesty](../deploying/runtime-store.md) oříznout sadu balíčků, které jsou publikované v aplikaci používat.</span><span class="sxs-lookup"><span data-stu-id="efc00-189">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="efc00-190">Soubor manifestu je část výstupu [ `dotnet store` příkaz](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="efc00-190">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="efc00-191">Chcete-li zadat více manifesty, přidejte `--manifest` možnost pro každý manifest.</span><span class="sxs-lookup"><span data-stu-id="efc00-191">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="efc00-192">Tato možnost je k dispozici od verze rozhraní .NET Core 2.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="efc00-192">This option is available starting with .NET Core 2.0 SDK.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="efc00-193">Určuje cestu k výstupnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="efc00-193">Specifies the path for the output directory.</span></span> <span data-ttu-id="efc00-194">Pokud není zadán, použije se výchozí *./bin/[configuration]/[framework]/publish/* nasazení závisí na architektuře nebo *./bin/[configuration]/[framework]/[runtime]/publish/* pro samostatná nasazení.</span><span class="sxs-lookup"><span data-stu-id="efc00-194">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="efc00-195">Pokud je relativní cesta, vygeneruje výstupní adresář je relativní vzhledem k umístění souboru projektu, ne do aktuálního pracovního adresáře.</span><span class="sxs-lookup"><span data-stu-id="efc00-195">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="efc00-196">Publikuje aplikace pro daný modul runtime.</span><span class="sxs-lookup"><span data-stu-id="efc00-196">Publishes the application for a given runtime.</span></span> <span data-ttu-id="efc00-197">Používá se při vytváření [samostatná nasazení (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="efc00-197">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="efc00-198">Seznam identifikátorů modulů Runtime (RID), najdete v článku [katalog identifikátorů RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="efc00-198">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="efc00-199">Výchozí hodnota je publikovat [nasazení závisí na architektuře (chyba)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="efc00-199">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="efc00-200">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="efc00-200">Sets the verbosity level of the command.</span></span> <span data-ttu-id="efc00-201">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="efc00-201">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="efc00-202">Definuje verze příponu, která má nahradit hvězdičku (`*`) v poli verze souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="efc00-202">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

---

## <a name="examples"></a><span data-ttu-id="efc00-203">Příklady</span><span class="sxs-lookup"><span data-stu-id="efc00-203">Examples</span></span>

<span data-ttu-id="efc00-204">Publikujte projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="efc00-204">Publish the project in the current directory:</span></span>

`dotnet publish`

<span data-ttu-id="efc00-205">Publikování aplikace pomocí zadaný soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="efc00-205">Publish the application using the specified project file:</span></span>

`dotnet publish ~/projects/app1/app1.csproj`

<span data-ttu-id="efc00-206">Publikujte projekt v aktuálním adresáři pomocí `netcoreapp1.1` framework:</span><span class="sxs-lookup"><span data-stu-id="efc00-206">Publish the project in the current directory using the `netcoreapp1.1` framework:</span></span>

`dotnet publish --framework netcoreapp1.1`

<span data-ttu-id="efc00-207">Publikujte aktuální aplikace pomocí `netcoreapp1.1` rozhraní framework a modulu runtime pro `OS X 10.10` (musí uvést tento identifikátorů RID v souboru projektu).</span><span class="sxs-lookup"><span data-stu-id="efc00-207">Publish the current application using the `netcoreapp1.1` framework and the runtime for `OS X 10.10` (you must list this RID in the project file).</span></span>

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

<span data-ttu-id="efc00-208">Aktuální aplikaci publikovat, ale nechcete obnovit odkazy na projekt na projekt (P2P), jenom kořenový projektu během operace obnovení (.NET Core SDK 2.0 a novější):</span><span class="sxs-lookup"><span data-stu-id="efc00-208">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet publish --no-dependencies`

## <a name="see-also"></a><span data-ttu-id="efc00-209">Viz také:</span><span class="sxs-lookup"><span data-stu-id="efc00-209">See also</span></span>

* [<span data-ttu-id="efc00-210">Cílové verze rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="efc00-210">Target frameworks</span></span>](../../standard/frameworks.md)
* [<span data-ttu-id="efc00-211">Identifikátor modulu runtime (RID) katalogu</span><span class="sxs-lookup"><span data-stu-id="efc00-211">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
