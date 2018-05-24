---
title: příkaz - .NET Core rozhraní příkazového řádku publikování DotNet.
description: Příkaz Publikovat dotnet publikuje do adresáře projektu .NET Core.
author: mairaw
ms.author: mairaw
ms.date: 03/10/2018
ms.openlocfilehash: 8509f1a721c0b4b4c05d68e0f98f9b856bcc5a8e
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2018
---
# <a name="dotnet-publish"></a><span data-ttu-id="ab398-103">publikování DotNet.</span><span class="sxs-lookup"><span data-stu-id="ab398-103">dotnet publish</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="ab398-104">Název</span><span class="sxs-lookup"><span data-stu-id="ab398-104">Name</span></span>

<span data-ttu-id="ab398-105">`dotnet publish` -Pack aplikace a jeho závislosti do složky pro nasazení k hostování systému.</span><span class="sxs-lookup"><span data-stu-id="ab398-105">`dotnet publish` - Packs the application and its dependencies into a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ab398-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="ab398-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="ab398-107">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="ab398-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-dependencies] [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ab398-108">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="ab398-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="ab398-109">Popis</span><span class="sxs-lookup"><span data-stu-id="ab398-109">Description</span></span>

<span data-ttu-id="ab398-110">`dotnet publish` zkompiluje aplikace, čte prostřednictvím jeho závislé součásti, zadaný v souboru projektu a publikuje výslednou sadu soubory do adresáře.</span><span class="sxs-lookup"><span data-stu-id="ab398-110">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="ab398-111">Výstup bude obsahovat následující:</span><span class="sxs-lookup"><span data-stu-id="ab398-111">The output will contain the following:</span></span>

* <span data-ttu-id="ab398-112">Kód jazyka (IL) v sestavení s mezilehlé *dll* rozšíření.</span><span class="sxs-lookup"><span data-stu-id="ab398-112">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
* <span data-ttu-id="ab398-113">*. deps.json* soubor, který obsahuje všechny závislosti projektu.</span><span class="sxs-lookup"><span data-stu-id="ab398-113">*.deps.json* file that contains all of the dependencies of the project.</span></span>
* <span data-ttu-id="ab398-114">*. runtime.config.json* soubor, který určuje sdílený modul runtime, který aplikace očekává a také další možnosti konfigurace pro modul runtime (například uvolňování paměti – typ kolekce).</span><span class="sxs-lookup"><span data-stu-id="ab398-114">*.runtime.config.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
* <span data-ttu-id="ab398-115">Závislosti aplikace.</span><span class="sxs-lookup"><span data-stu-id="ab398-115">The application's dependencies.</span></span> <span data-ttu-id="ab398-116">Tyto jsou kopírovány z mezipaměti NuGet do výstupní složky.</span><span class="sxs-lookup"><span data-stu-id="ab398-116">These are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="ab398-117">`dotnet publish` Výstup příkazu je připraven k nasazení k hostování systému (například server, PC, Mac, přenosných počítačů) pro spuštění a je jediným oficiálně podporované způsob, jak připravit aplikaci pro nasazení.</span><span class="sxs-lookup"><span data-stu-id="ab398-117">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution and is the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="ab398-118">V závislosti na typu nasazení, který určuje projekt hostitelský systém může nebo nemusí mít .NET Core sdílené na něm nainstalován modul runtime.</span><span class="sxs-lookup"><span data-stu-id="ab398-118">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="ab398-119">Další informace najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="ab398-119">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span> <span data-ttu-id="ab398-120">Struktura adresářů publikované aplikace, najdete v části [adresářovou strukturu](/aspnet/core/hosting/directory-structure).</span><span class="sxs-lookup"><span data-stu-id="ab398-120">For the directory structure of a published application, see [Directory structure](/aspnet/core/hosting/directory-structure).</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="ab398-121">Arguments</span><span class="sxs-lookup"><span data-stu-id="ab398-121">Arguments</span></span>

`PROJECT`

<span data-ttu-id="ab398-122">Projekt k publikování, výchozí nastavení k aktuálnímu adresáři, není-li zadána.</span><span class="sxs-lookup"><span data-stu-id="ab398-122">The project to publish, which defaults to the current directory if not specified.</span></span>

## <a name="options"></a><span data-ttu-id="ab398-123">Možnosti</span><span class="sxs-lookup"><span data-stu-id="ab398-123">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="ab398-124">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="ab398-124">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="ab398-125">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="ab398-125">Defines the build configuration.</span></span> <span data-ttu-id="ab398-126">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="ab398-126">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="ab398-127">Publikuje aplikace pro zadaný [cílové rozhraní](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="ab398-127">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="ab398-128">Musíte zadat cílové rozhraní v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="ab398-128">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="ab398-129">Vynutí všechny závislosti pro přeloženy i v případě, že poslední obnovení bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="ab398-129">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="ab398-130">Jde o ekvivalent odstraňování *project.assets.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="ab398-130">This is equivalent to deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="ab398-131">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="ab398-131">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="ab398-132">Určuje jeden nebo několik [cíle manifesty](../deploying/runtime-store.md) sloužící k uvolnění dočasné paměti sadu balíčků, které jsou publikovány v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ab398-132">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="ab398-133">Soubor manifestu je součástí výstup [ `dotnet store` příkaz](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="ab398-133">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="ab398-134">Chcete-li zadat více manifesty, přidejte `--manifest` možnost pro každý manifest.</span><span class="sxs-lookup"><span data-stu-id="ab398-134">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="ab398-135">Tato možnost je dostupná od verze rozhraní .NET Core 2.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ab398-135">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-dependencies`

<span data-ttu-id="ab398-136">Ignoruje odkazy na projekt na projekt a obnoví pouze kořenové projektu.</span><span class="sxs-lookup"><span data-stu-id="ab398-136">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="ab398-137">Neprovede implicitní obnovení, při spuštění příkazu.</span><span class="sxs-lookup"><span data-stu-id="ab398-137">Doesn't perform an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="ab398-138">Určuje cestu k výstupnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="ab398-138">Specifies the path for the output directory.</span></span> <span data-ttu-id="ab398-139">Pokud není zadáno, je standardně *./bin/[configuration]/[framework]/publish/* pro nasazení závislé na framework nebo *./bin/[configuration]/[framework]/[runtime]/publish/* pro samostatná nasazení.</span><span class="sxs-lookup"><span data-stu-id="ab398-139">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="ab398-140">Pokud je zadaný na relativní cestu, výstupní adresář generované je relativní k umístění souboru projektu, není pro aktuální pracovní adresář.</span><span class="sxs-lookup"><span data-stu-id="ab398-140">If a relative path is provided, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="ab398-141">Publikuje na .NET Core runtime s vaší aplikací, takže modul runtime nemusí být nainstalován v cílovém počítači.</span><span class="sxs-lookup"><span data-stu-id="ab398-141">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="ab398-142">Pokud je zadán identifikátor runtime, výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="ab398-142">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="ab398-143">Další informace o různých typů najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="ab398-143">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="ab398-144">Publikuje aplikace pro daný modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="ab398-144">Publishes the application for a given runtime.</span></span> <span data-ttu-id="ab398-145">Používá se při vytváření [samostatná nasazení (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="ab398-145">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="ab398-146">Seznam Runtime identifikátorů (RID), najdete v článku [identifikátorů RID katalogu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="ab398-146">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="ab398-147">Výchozí hodnota je publikování [nasazení závislé na framework (disketové jednotky)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="ab398-147">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="ab398-148">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="ab398-148">Sets the verbosity level of the command.</span></span> <span data-ttu-id="ab398-149">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="ab398-149">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="ab398-150">Definuje příponu verze, která má nahradit hvězdičku (`*`) v poli verze souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="ab398-150">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ab398-151">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="ab398-151">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="ab398-152">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="ab398-152">Defines the build configuration.</span></span> <span data-ttu-id="ab398-153">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="ab398-153">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="ab398-154">Publikuje aplikace pro zadaný [cílové rozhraní](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="ab398-154">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="ab398-155">Musíte zadat cílové rozhraní v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="ab398-155">You must specify the target framework in the project file.</span></span>

`-h|--help`

<span data-ttu-id="ab398-156">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="ab398-156">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="ab398-157">Určuje jeden nebo několik [cíle manifesty](../deploying/runtime-store.md) sloužící k uvolnění dočasné paměti sadu balíčků, které jsou publikovány v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ab398-157">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="ab398-158">Soubor manifestu je součástí výstup [ `dotnet store` příkaz](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="ab398-158">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="ab398-159">Chcete-li zadat více manifesty, přidejte `--manifest` možnost pro každý manifest.</span><span class="sxs-lookup"><span data-stu-id="ab398-159">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="ab398-160">Tato možnost je dostupná od verze rozhraní .NET Core 2.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ab398-160">This option is available starting with .NET Core 2.0 SDK.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="ab398-161">Určuje cestu k výstupnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="ab398-161">Specifies the path for the output directory.</span></span> <span data-ttu-id="ab398-162">Pokud není zadáno, je standardně *./bin/[configuration]/[framework]/publish/* pro nasazení závislé na framework nebo *./bin/[configuration]/[framework]/[runtime]/publish/* pro samostatná nasazení.</span><span class="sxs-lookup"><span data-stu-id="ab398-162">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="ab398-163">Pokud je zadaný na relativní cestu, výstupní adresář generované je relativní k umístění souboru projektu, není pro aktuální pracovní adresář.</span><span class="sxs-lookup"><span data-stu-id="ab398-163">If a relative path is provided, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="ab398-164">Publikuje aplikace pro daný modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="ab398-164">Publishes the application for a given runtime.</span></span> <span data-ttu-id="ab398-165">Používá se při vytváření [samostatná nasazení (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="ab398-165">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="ab398-166">Seznam Runtime identifikátorů (RID), najdete v článku [identifikátorů RID katalogu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="ab398-166">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="ab398-167">Výchozí hodnota je publikování [nasazení závislé na framework (disketové jednotky)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="ab398-167">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="ab398-168">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="ab398-168">Sets the verbosity level of the command.</span></span> <span data-ttu-id="ab398-169">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="ab398-169">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="ab398-170">Definuje příponu verze, která má nahradit hvězdičku (`*`) v poli verze souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="ab398-170">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

---

## <a name="examples"></a><span data-ttu-id="ab398-171">Příklady</span><span class="sxs-lookup"><span data-stu-id="ab398-171">Examples</span></span>

<span data-ttu-id="ab398-172">Publikování tohoto projektu v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="ab398-172">Publish the project in the current directory:</span></span>

`dotnet publish`

<span data-ttu-id="ab398-173">Publikování aplikace pomocí souboru zadaného projektu:</span><span class="sxs-lookup"><span data-stu-id="ab398-173">Publish the application using the specified project file:</span></span>

`dotnet publish ~/projects/app1/app1.csproj`

<span data-ttu-id="ab398-174">Publikování tohoto projektu v aktuálním adresáři pomocí `netcoreapp1.1` framework:</span><span class="sxs-lookup"><span data-stu-id="ab398-174">Publish the project in the current directory using the `netcoreapp1.1` framework:</span></span>

`dotnet publish --framework netcoreapp1.1`

<span data-ttu-id="ab398-175">Publikování aktuální aplikace pomocí `netcoreapp1.1` framework a prostředí runtime pro `OS X 10.10` (musí seznam tento identifikátorů RID v souboru projektu).</span><span class="sxs-lookup"><span data-stu-id="ab398-175">Publish the current application using the `netcoreapp1.1` framework and the runtime for `OS X 10.10` (you must list this RID in the project file).</span></span>

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

<span data-ttu-id="ab398-176">Publikování aktuální aplikace ale neobnoví odkazů na projekt na projekt (P2P), pouze v kořenové projektu během operace obnovení (.NET Core SDK 2.0 a novější):</span><span class="sxs-lookup"><span data-stu-id="ab398-176">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet publish --no-dependencies`

## <a name="see-also"></a><span data-ttu-id="ab398-177">Viz také</span><span class="sxs-lookup"><span data-stu-id="ab398-177">See also</span></span>

* [<span data-ttu-id="ab398-178">Cílové verze rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ab398-178">Target frameworks</span></span>](../../standard/frameworks.md)
* [<span data-ttu-id="ab398-179">Katalog identifikátor runtime (RID)</span><span class="sxs-lookup"><span data-stu-id="ab398-179">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
