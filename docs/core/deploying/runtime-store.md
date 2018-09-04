---
title: Úložiště balíčků modulu runtime
description: Toto téma vysvětluje úložiště balíčků modulu runtime a cíl manifestů, které používá .NET Core.
author: bleroy
ms.author: mairaw
ms.date: 08/12/2017
ms.openlocfilehash: df2776ac2e4a2eed7f54b3031f13ab41fc714aae
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43511581"
---
# <a name="runtime-package-store"></a><span data-ttu-id="a6d60-103">Úložiště balíčků modulu runtime</span><span class="sxs-lookup"><span data-stu-id="a6d60-103">Runtime package store</span></span>

<span data-ttu-id="a6d60-104">Počínaje .NET Core 2.0, je možné k zabalení a nasazení aplikace před známými sadu balíčků, které existují v cílovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="a6d60-104">Starting with .NET Core 2.0, it's possible to package and deploy apps against a known set of packages that exist in the target environment.</span></span> <span data-ttu-id="a6d60-105">Výhody jsou rychlejší nasazení, nižší využití místa na disku a vylepšené spouštění výkonu v některých případech.</span><span class="sxs-lookup"><span data-stu-id="a6d60-105">The benefits are faster deployments, lower disk space use, and improved startup performance in some cases.</span></span>

<span data-ttu-id="a6d60-106">Tato funkce je implementovaná jako *úložiště balíčků modulu runtime*, což je adresář na disku, kde jsou uloženy balíčky (obvykle v */usr/local/share/dotnet/store* v systému macOS nebo Linuxu a *C: / Program soubory/dotnet/store* na Windows).</span><span class="sxs-lookup"><span data-stu-id="a6d60-106">This feature is implemented as a *runtime package store*, which is a directory on disk where packages are stored (typically at */usr/local/share/dotnet/store* on macOS/Linux and *C:/Program Files/dotnet/store* on Windows).</span></span> <span data-ttu-id="a6d60-107">V tomto adresáři neexistují podadresáře pro architektury a [platforem](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="a6d60-107">Under this directory, there are subdirectories for architectures and [target frameworks](../../standard/frameworks.md).</span></span> <span data-ttu-id="a6d60-108">Soubor rozložení je podobným způsobem, který [NuGet prostředky jsou rozloženy na disku](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure):</span><span class="sxs-lookup"><span data-stu-id="a6d60-108">The file layout is similar to the way that [NuGet assets are laid out on disk](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure):</span></span>

```
\dotnet
    \store
        \x64
            \netcoreapp2.0
                \microsoft.applicationinsights
                \microsoft.aspnetcore
                ...
        \x86
            \netcoreapp2.0
                \microsoft.applicationinsights
                \microsoft.aspnetcore
                ...
```

<span data-ttu-id="a6d60-109">A *cíl manifestu* soubor obsahuje seznam balíčků v úložiště balíčků modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="a6d60-109">A *target manifest* file lists the packages in the runtime package store.</span></span> <span data-ttu-id="a6d60-110">Vývojáři mohou cílit manifestu, při publikování své aplikace.</span><span class="sxs-lookup"><span data-stu-id="a6d60-110">Developers can target this manifest when publishing their app.</span></span> <span data-ttu-id="a6d60-111">Cíl manifestu se většinou poskytuje vlastník cílové produkčního prostředí.</span><span class="sxs-lookup"><span data-stu-id="a6d60-111">The target manifest is typically provided by the owner of the targeted production environment.</span></span>

## <a name="preparing-a-runtime-environment"></a><span data-ttu-id="a6d60-112">Příprava prostředí runtime</span><span class="sxs-lookup"><span data-stu-id="a6d60-112">Preparing a runtime environment</span></span>

<span data-ttu-id="a6d60-113">Správce prostředí modulu runtime může optimalizovat aplikace pro rychlejší nasazení a nižší využití místa na disku vytvořením úložiště balíčků modulu runtime a odpovídající cíl manifestu.</span><span class="sxs-lookup"><span data-stu-id="a6d60-113">The administrator of a runtime environment can optimize apps for faster deployments and lower disk space use by building a runtime package store and the corresponding target manifest.</span></span>

<span data-ttu-id="a6d60-114">Prvním krokem je vytvoření *manifest balíčku úložiště* , který obsahuje seznam balíčků, které tvoří úložiště balíčků modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="a6d60-114">The first step is to create a *package store manifest* that lists the packages that compose the runtime package store.</span></span> <span data-ttu-id="a6d60-115">Tento formát souboru je kompatibilní s formátem souboru projektu (*csproj*).</span><span class="sxs-lookup"><span data-stu-id="a6d60-115">This file format is compatible with the project file format (*csproj*).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="<NUGET_PACKAGE>" Version="<VERSION>" />
    <!-- Include additional packages here -->
  </ItemGroup>
</Project>
```

<span data-ttu-id="a6d60-116">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="a6d60-116">**Example**</span></span>

<span data-ttu-id="a6d60-117">Následující příklad manifestu úložiště balíčků (*packages.csproj*) se používá k přidání [ `Newtonsoft.Json` ](https://www.nuget.org/packages/Newtonsoft.Json/) a [ `Moq` ](https://www.nuget.org/packages/moq/) do úložiště balíčků modulu runtime:</span><span class="sxs-lookup"><span data-stu-id="a6d60-117">The following example package store manifest (*packages.csproj*) is used to add [`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) and [`Moq`](https://www.nuget.org/packages/moq/) to a runtime package store:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.3" />
    <PackageReference Include="Moq" Version="4.7.63" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="a6d60-118">Zřídit úložiště balíčků modulu runtime pomocí provádí `dotnet store` manifest balíčku úložiště, modul runtime a framework:</span><span class="sxs-lookup"><span data-stu-id="a6d60-118">Provision the runtime package store by executing `dotnet store` with the package store manifest, runtime, and framework:</span></span>

```console
dotnet store --manifest <PATH_TO_MANIFEST_FILE> --runtime <RUNTIME_IDENTIFIER> --framework <FRAMEWORK>
```

<span data-ttu-id="a6d60-119">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="a6d60-119">**Example**</span></span>

```console
dotnet store --manifest packages.csproj --runtime win10-x64 --framework netcoreapp2.0 --framework-version 2.0.0
```

<span data-ttu-id="a6d60-120">Můžete předat více cílové úložiště balíčků cesty k manifestu do jediné [ `dotnet store` ](../tools/dotnet-store.md) příkaz opakováním možnost a cestu v příkazu.</span><span class="sxs-lookup"><span data-stu-id="a6d60-120">You can pass multiple target package store manifest paths to a single [`dotnet store`](../tools/dotnet-store.md) command by repeating the option and path in the command.</span></span>

<span data-ttu-id="a6d60-121">Výchozí výstup příkazu je balíček úložiště v nabídce *.dotnet/store* podadresář tím profil daného uživatele.</span><span class="sxs-lookup"><span data-stu-id="a6d60-121">By default, the output of the command is a package store under the *.dotnet/store* subdirectory of the user's profile.</span></span> <span data-ttu-id="a6d60-122">Můžete zadat jiné umístění pomocí `--output <OUTPUT_DIRECTORY>` možnost.</span><span class="sxs-lookup"><span data-stu-id="a6d60-122">You can specify a different location using the `--output <OUTPUT_DIRECTORY>` option.</span></span> <span data-ttu-id="a6d60-123">Kořenový adresář úložiště obsahuje cíl manifestu *artifact.xml* souboru.</span><span class="sxs-lookup"><span data-stu-id="a6d60-123">The root directory of the store contains a target manifest *artifact.xml* file.</span></span> <span data-ttu-id="a6d60-124">Tento soubor může být k dispozici ke stažení a používá aplikace autory, kteří chtějí cílí toto úložiště při publikování.</span><span class="sxs-lookup"><span data-stu-id="a6d60-124">This file can be made available for download and be used by app authors who want to target this store when publishing.</span></span>

<span data-ttu-id="a6d60-125">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="a6d60-125">**Example**</span></span>

<span data-ttu-id="a6d60-126">Následující *artifact.xml* po spuštění předchozího příkladu je vytvořen soubor.</span><span class="sxs-lookup"><span data-stu-id="a6d60-126">The following *artifact.xml* file is produced after running the previous example.</span></span> <span data-ttu-id="a6d60-127">Všimněte si, že [ `Castle.Core` ](https://www.nuget.org/packages/Castle.Core/) je závislost `Moq`, takže ji vložila automaticky a zobrazí se v *artifacts.xml* soubor manifestu.</span><span class="sxs-lookup"><span data-stu-id="a6d60-127">Note that [`Castle.Core`](https://www.nuget.org/packages/Castle.Core/) is a dependency of `Moq`, so it's included automatically and appears in the *artifacts.xml* manifest file.</span></span>

```xml
<StoreArtifacts>
  <Package Id="Newtonsoft.Json" Version="10.0.3" />
  <Package Id="Castle.Core" Version="4.1.0" />
  <Package Id="Moq" Version="4.7.63" />
</StoreArtifacts>
```

## <a name="publishing-an-app-against-a-target-manifest"></a><span data-ttu-id="a6d60-128">Publikování aplikace proti cílové manifestu</span><span class="sxs-lookup"><span data-stu-id="a6d60-128">Publishing an app against a target manifest</span></span>

<span data-ttu-id="a6d60-129">Pokud máte soubor manifestu cíl na disku, je při publikování aplikace s využitím zadat cestu k souboru [ `dotnet publish` ](../tools/dotnet-publish.md) příkaz:</span><span class="sxs-lookup"><span data-stu-id="a6d60-129">If you have a target manifest file on disk, you specify the path to the file when publishing your app with the [`dotnet publish`](../tools/dotnet-publish.md) command:</span></span>

```console
dotnet publish --manifest <PATH_TO_MANIFEST_FILE>
```

<span data-ttu-id="a6d60-130">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="a6d60-130">**Example**</span></span>

```console
dotnet publish --manifest manifest.xml
```

<span data-ttu-id="a6d60-131">Nasazení výsledné publikované aplikace do prostředí, který má balíčky, které je popsáno v manifestu cíl.</span><span class="sxs-lookup"><span data-stu-id="a6d60-131">You deploy the resulting published app to an environment that has the packages described in the target manifest.</span></span> <span data-ttu-id="a6d60-132">Pokud tak neučiníte za následek selhání spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="a6d60-132">Failing to do so results in the app failing to start.</span></span>

<span data-ttu-id="a6d60-133">Určení více manifestů cílové při publikování aplikace opakováním možnost a cestu (například `--manifest manifest1.xml --manifest manifest2.xml`).</span><span class="sxs-lookup"><span data-stu-id="a6d60-133">Specify multiple target manifests when publishing an app by repeating the option and path (for example, `--manifest manifest1.xml --manifest manifest2.xml`).</span></span> <span data-ttu-id="a6d60-134">Pokud tak učiníte, aplikace je oříznut pro sjednocení balíčky zadané v cílové soubory manifestu k příkazu k dispozici.</span><span class="sxs-lookup"><span data-stu-id="a6d60-134">When you do so, the app is trimmed for the union of packages specified in the target manifest files provided to the command.</span></span>

## <a name="specifying-target-manifests-in-the-project-file"></a><span data-ttu-id="a6d60-135">Zadání cílové manifesty v souboru projektu</span><span class="sxs-lookup"><span data-stu-id="a6d60-135">Specifying target manifests in the project file</span></span>

<span data-ttu-id="a6d60-136">Alternativa k určení cílového manifesty s [ `dotnet publish` ](../tools/dotnet-publish.md) příkaz je se zadávají v souboru projektu jako středníkem oddělený seznam cest v rámci  **\<TargetManifestFiles >** značky.</span><span class="sxs-lookup"><span data-stu-id="a6d60-136">An alternative to specifying target manifests with the [`dotnet publish`](../tools/dotnet-publish.md) command is to specify them in the project file as a semicolon-separated list of paths under a **\<TargetManifestFiles>** tag.</span></span>

```xml
<PropertyGroup>
  <TargetManifestFiles>manifest1.xml;manifest2.xml</TargetManifestFiles>
</PropertyGroup>
```

<span data-ttu-id="a6d60-137">Určení manifestů cíl v souboru projektu, pouze v případě cílového prostředí pro aplikaci je dobře známé, například pro projekty .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a6d60-137">Specify the target manifests in the project file only when the target environment for the app is well-known, such as for .NET Core projects.</span></span> <span data-ttu-id="a6d60-138">To není případ open-source projektů.</span><span class="sxs-lookup"><span data-stu-id="a6d60-138">This isn't the case for open-source projects.</span></span> <span data-ttu-id="a6d60-139">Uživatelé open source projektu je obvykle nasazení do různých produkční prostředí.</span><span class="sxs-lookup"><span data-stu-id="a6d60-139">The users of an open-source project typically deploy it to different production environments.</span></span> <span data-ttu-id="a6d60-140">Tyto produkční prostředí obvykle mají různé sady předem nainstalované balíčky.</span><span class="sxs-lookup"><span data-stu-id="a6d60-140">These production environments generally have different sets of packages pre-installed.</span></span> <span data-ttu-id="a6d60-141">Předpoklady o cíl manifestu nemůže provádět v těchto prostředích, proto byste měli použít `--manifest` možnost [ `dotnet publish` ](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="a6d60-141">You can't make assumptions about the target manifest in such environments, so you should use the `--manifest` option of [`dotnet publish`](../tools/dotnet-publish.md).</span></span>

## <a name="aspnet-core-implicit-store"></a><span data-ttu-id="a6d60-142">Implicitní úložiště ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a6d60-142">ASP.NET Core implicit store</span></span>

<span data-ttu-id="a6d60-143">ASP.NET Core implicitní úložiště platí jenom pro ASP.NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="a6d60-143">The ASP.NET Core implicit store applies only to ASP.NET Core 2.0.</span></span> <span data-ttu-id="a6d60-144">Důrazně doporučujeme aplikace pomocí ASP.NET Core 2.1 nebo novější, která zajišťuje **není** použít implicitní úložiště.</span><span class="sxs-lookup"><span data-stu-id="a6d60-144">We strongly recommend applications use ASP.NET Core 2.1 and later, which does **not** use the implicit store.</span></span> <span data-ttu-id="a6d60-145">ASP.NET Core 2.1 a pozdější použití sdílené architektuře.</span><span class="sxs-lookup"><span data-stu-id="a6d60-145">ASP.NET Core 2.1 and later use the shared framework.</span></span>

<span data-ttu-id="a6d60-146">Funkce úložiště balíčků modulu runtime používá implicitně aplikace ASP.NET Core při nasazení aplikace jako [nasazení závisí na architektuře (chyba)](index.md#framework-dependent-deployments-fdd) aplikace.</span><span class="sxs-lookup"><span data-stu-id="a6d60-146">The runtime package store feature is used implicitly by an ASP.NET Core app when the app is deployed as a [framework-dependent deployment (FDD)](index.md#framework-dependent-deployments-fdd) app.</span></span> <span data-ttu-id="a6d60-147">Cíle v [ `Microsoft.NET.Sdk.Web` ](https://github.com/aspnet/websdk) zahrnují manifesty odkazující na implicitní úložiště balíček v cílovém systému.</span><span class="sxs-lookup"><span data-stu-id="a6d60-147">The targets in [`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk) include manifests referencing the implicit package store on the target system.</span></span> <span data-ttu-id="a6d60-148">Kromě toho libovolnou aplikaci disketové jednotky, na kterém závisí `Microsoft.AspNetCore.All` balíček výsledky v publikované aplikaci, která obsahuje jenom aplikace a její prostředky a není balíčky uvedené v `Microsoft.AspNetCore.All` Microsoft.aspnetcore.all.</span><span class="sxs-lookup"><span data-stu-id="a6d60-148">Additionally, any FDD app that depends on the `Microsoft.AspNetCore.All` package results in a published app that contains only the app and its assets and not the packages listed in the `Microsoft.AspNetCore.All` metapackage.</span></span> <span data-ttu-id="a6d60-149">Předpokládá se, že tyto balíčky jsou k dispozici v cílovém systému.</span><span class="sxs-lookup"><span data-stu-id="a6d60-149">It's assumed that those packages are present on the target system.</span></span>

<span data-ttu-id="a6d60-150">Úložiště balíčků modulu runtime je nainstalován na hostiteli, když je nainstalovaná sada .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="a6d60-150">The runtime package store is installed on the host when the .NET Core SDK is installed.</span></span> <span data-ttu-id="a6d60-151">Další instalační programy může poskytovat úložiště balíčků modulu runtime, včetně Zip/tarballu instalace sady .NET Core SDK `apt-get`, Red Hat Yumu, sady .NET Core Windows serveru, který hostuje a ruční runtime úložiště balíčků zařízení.</span><span class="sxs-lookup"><span data-stu-id="a6d60-151">Other installers may provide the runtime package store, including Zip/tarball installations of the .NET Core SDK, `apt-get`, Red Hat Yum, the .NET Core Windows Server Hosting bundle, and manual runtime package store installations.</span></span>

<span data-ttu-id="a6d60-152">Při nasazování [nasazení závisí na architektuře (chyba)](index.md#framework-dependent-deployments-fdd) aplikace, ujistěte se, že cílové prostředí má nainstalovaná sada .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="a6d60-152">When deploying a [framework-dependent deployment (FDD)](index.md#framework-dependent-deployments-fdd) app, make sure that the target environment has the .NET Core SDK installed.</span></span> <span data-ttu-id="a6d60-153">Pokud je aplikace nasazena do prostředí, který neobsahuje ASP.NET Core, můžete zrušit implicitní úložiště tak, že zadáte  **\<PublishWithAspNetCoreTargetManifest >** nastavena na `false` v souboru projektu jako v v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="a6d60-153">If the app is deployed to an environment that doesn't include ASP.NET Core, you can opt out of the implicit store by specifying  **\<PublishWithAspNetCoreTargetManifest>** set to `false` in the project file as in the following example:</span></span>

```xml
<PropertyGroup>
  <PublishWithAspNetCoreTargetManifest>false</PublishWithAspNetCoreTargetManifest>
</PropertyGroup>
```

> [!NOTE]
> <span data-ttu-id="a6d60-154">Pro [samostatná nasazení (SCD)](index.md#self-contained-deployments-scd) aplikací, se předpokládá, že cílový systém nutně neobsahuje požadované balíčky manifestu.</span><span class="sxs-lookup"><span data-stu-id="a6d60-154">For [self-contained deployment (SCD)](index.md#self-contained-deployments-scd) apps, it's assumed that the target system doesn't necessarily contain the required manifest packages.</span></span> <span data-ttu-id="a6d60-155">Proto  **\<PublishWithAspNetCoreTargetManifest >** nelze nastavit na `true` SCD aplikace.</span><span class="sxs-lookup"><span data-stu-id="a6d60-155">Therefore, **\<PublishWithAspNetCoreTargetManifest>** cannot be set to `true` for an SCD app.</span></span>

<span data-ttu-id="a6d60-156">Pokud nasazujete aplikaci se závislostí manifestu, který je k dispozici v nasazení (je k dispozici v sestavení *bin* složky), úložiště balíčků modulu runtime *nepoužívá* na hostiteli pro toto sestavení.</span><span class="sxs-lookup"><span data-stu-id="a6d60-156">If you deploy an application with a manifest dependency that's present in the deployment (the assembly is present in the *bin* folder), the runtime package store *isn't used* on the host for that assembly.</span></span> <span data-ttu-id="a6d60-157">*Bin* sestavení složky se používá bez ohledu na jejich přítomnosti v úložiště balíčků modulu runtime na hostiteli.</span><span class="sxs-lookup"><span data-stu-id="a6d60-157">The *bin* folder assembly is used regardless of its presence in the runtime package store on the host.</span></span>

<span data-ttu-id="a6d60-158">Verze závislosti uvedené v manifestu musí odpovídat verzi závislosti v úložiště balíčků modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="a6d60-158">The version of the dependency indicated in the manifest must match the version of the dependency in the runtime package store.</span></span> <span data-ttu-id="a6d60-159">Pokud máte Neshoda verzí mezi závislosti v manifestu cíl a verze, která existuje v úložiště balíčků modulu runtime a aplikace neobsahuje požadovanou verzi balíčku v jeho nasazení, aplikace se nespustí.</span><span class="sxs-lookup"><span data-stu-id="a6d60-159">If you have a version mismatch between the dependency in the target manifest and the version that exists in the runtime package store and the app doesn't include the required version of the package in its deployment, the app fails to start.</span></span> <span data-ttu-id="a6d60-160">Výjimka obsahuje název cílového manifestu, který volá se pro sestavení úložiště balíčků modulu runtime, které vám pomohou s řešením neshoda.</span><span class="sxs-lookup"><span data-stu-id="a6d60-160">The exception includes the name of the target manifest that called for the runtime package store assembly, which helps you troubleshoot the mismatch.</span></span>

<span data-ttu-id="a6d60-161">Pokud je nasazení *oříznut* při publikování, jsou pouze konkrétní verze manifestu balíčky určujete sražených z publikovaných výstupu.</span><span class="sxs-lookup"><span data-stu-id="a6d60-161">When the deployment is *trimmed* on publish, only the specific versions of the manifest packages you indicate are withheld from the published output.</span></span> <span data-ttu-id="a6d60-162">Balíčky na uvedené verze musí být k dispozici na na spuštění hostitele pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a6d60-162">The packages at the versions indicated must be present on the host for the app to start.</span></span>

## <a name="see-also"></a><span data-ttu-id="a6d60-163">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a6d60-163">See also</span></span>

* [<span data-ttu-id="a6d60-164">DotNet – publikování</span><span class="sxs-lookup"><span data-stu-id="a6d60-164">dotnet-publish</span></span>](../tools/dotnet-publish.md)  
* [<span data-ttu-id="a6d60-165">DotNet Restore</span><span class="sxs-lookup"><span data-stu-id="a6d60-165">dotnet-store</span></span>](../tools/dotnet-store.md)  
