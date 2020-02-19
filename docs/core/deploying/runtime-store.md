---
title: Úložiště balíčků modulu runtime
description: Naučte se používat úložiště balíčků modulu runtime pro cílení na manifesty používané .NET Core.
ms.date: 08/12/2017
ms.openlocfilehash: 7a833ed95147608c6fb403f8f0dec179d2a73833
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77448955"
---
# <a name="runtime-package-store"></a><span data-ttu-id="a6668-103">Úložiště balíčků modulu runtime</span><span class="sxs-lookup"><span data-stu-id="a6668-103">Runtime package store</span></span>

<span data-ttu-id="a6668-104">Počínaje .NET Core 2,0 je možné zabalit a nasazovat aplikace na známou sadu balíčků, které existují v cílovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="a6668-104">Starting with .NET Core 2.0, it's possible to package and deploy apps against a known set of packages that exist in the target environment.</span></span> <span data-ttu-id="a6668-105">Výhody jsou rychlejší nasazení, nižší využití místa na disku a Vylepšený výkon při spuštění v některých případech.</span><span class="sxs-lookup"><span data-stu-id="a6668-105">The benefits are faster deployments, lower disk space usage, and improved startup performance in some cases.</span></span>

<span data-ttu-id="a6668-106">Tato funkce je implementována jako *běhové úložiště balíčků*, což je adresář na disku, kde jsou uloženy balíčky (obvykle na */usr/local/share/dotnet/Store* v MacOS/Linux a *C:/Program Files/dotnet/Store* ve Windows).</span><span class="sxs-lookup"><span data-stu-id="a6668-106">This feature is implemented as a *runtime package store*, which is a directory on disk where packages are stored (typically at */usr/local/share/dotnet/store* on macOS/Linux and *C:/Program Files/dotnet/store* on Windows).</span></span> <span data-ttu-id="a6668-107">V tomto adresáři jsou podadresáře pro architektury a [cílové](../../standard/frameworks.md)architektury.</span><span class="sxs-lookup"><span data-stu-id="a6668-107">Under this directory, there are subdirectories for architectures and [target frameworks](../../standard/frameworks.md).</span></span> <span data-ttu-id="a6668-108">Rozložení souboru je podobné způsobu, jakým [jsou prostředky NuGet na disku rozloženy](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure):</span><span class="sxs-lookup"><span data-stu-id="a6668-108">The file layout is similar to the way that [NuGet assets are laid out on disk](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure):</span></span>

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

<span data-ttu-id="a6668-109">*Cílový soubor manifestu* uvádí balíčky v úložišti balíčků modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="a6668-109">A *target manifest* file lists the packages in the runtime package store.</span></span> <span data-ttu-id="a6668-110">Vývojáři můžou tento manifest cílit při publikování aplikace.</span><span class="sxs-lookup"><span data-stu-id="a6668-110">Developers can target this manifest when publishing their app.</span></span> <span data-ttu-id="a6668-111">Cílový manifest je obvykle poskytován vlastníkem cílového produkčního prostředí.</span><span class="sxs-lookup"><span data-stu-id="a6668-111">The target manifest is typically provided by the owner of the targeted production environment.</span></span>

## <a name="preparing-a-runtime-environment"></a><span data-ttu-id="a6668-112">Příprava běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="a6668-112">Preparing a runtime environment</span></span>

<span data-ttu-id="a6668-113">Správce běhového prostředí může optimalizovat aplikace pro rychlejší nasazení a snížit využití místa na disku vytvořením běhového balíčku za běhu a odpovídajícího cílového manifestu.</span><span class="sxs-lookup"><span data-stu-id="a6668-113">The administrator of a runtime environment can optimize apps for faster deployments and lower disk space use by building a runtime package store and the corresponding target manifest.</span></span>

<span data-ttu-id="a6668-114">Prvním krokem je vytvoření *manifestu balíčku pro úložiště* , který obsahuje seznam balíčků, které tvoří úložiště balíčků modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="a6668-114">The first step is to create a *package store manifest* that lists the packages that compose the runtime package store.</span></span> <span data-ttu-id="a6668-115">Tento formát souboru je kompatibilní s formátem souboru projektu (*csproj*).</span><span class="sxs-lookup"><span data-stu-id="a6668-115">This file format is compatible with the project file format (*csproj*).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="<NUGET_PACKAGE>" Version="<VERSION>" />
    <!-- Include additional packages here -->
  </ItemGroup>
</Project>
```

<span data-ttu-id="a6668-116">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="a6668-116">**Example**</span></span>

<span data-ttu-id="a6668-117">Následující ukázkový manifest úložiště balíčků (*Packages. csproj*) se používá k přidání [`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) a [`Moq`](https://www.nuget.org/packages/moq/) do úložiště balíčků modulu runtime:</span><span class="sxs-lookup"><span data-stu-id="a6668-117">The following example package store manifest (*packages.csproj*) is used to add [`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) and [`Moq`](https://www.nuget.org/packages/moq/) to a runtime package store:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.3" />
    <PackageReference Include="Moq" Version="4.7.63" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="a6668-118">Zajistěte, aby se úložiště balíčků modulu runtime spustilo `dotnet store` s manifestem úložiště balíčků, modulem runtime a architekturou:</span><span class="sxs-lookup"><span data-stu-id="a6668-118">Provision the runtime package store by executing `dotnet store` with the package store manifest, runtime, and framework:</span></span>

```dotnetcli
dotnet store --manifest <PATH_TO_MANIFEST_FILE> --runtime <RUNTIME_IDENTIFIER> --framework <FRAMEWORK>
```

<span data-ttu-id="a6668-119">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="a6668-119">**Example**</span></span>

```dotnetcli
dotnet store --manifest packages.csproj --runtime win10-x64 --framework netcoreapp2.0 --framework-version 2.0.0
```

<span data-ttu-id="a6668-120">Pomocí možnosti a cesty v příkazu můžete předat několik cest k manifestu cílového úložiště balíčků do jednoho [`dotnet store`](../tools/dotnet-store.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="a6668-120">You can pass multiple target package store manifest paths to a single [`dotnet store`](../tools/dotnet-store.md) command by repeating the option and path in the command.</span></span>

<span data-ttu-id="a6668-121">Ve výchozím nastavení je výstupem příkazu úložiště balíčků v podadresáři *. dotnet/Store* profilu uživatele.</span><span class="sxs-lookup"><span data-stu-id="a6668-121">By default, the output of the command is a package store under the *.dotnet/store* subdirectory of the user's profile.</span></span> <span data-ttu-id="a6668-122">Pomocí možnosti `--output <OUTPUT_DIRECTORY>` můžete zadat jiné umístění.</span><span class="sxs-lookup"><span data-stu-id="a6668-122">You can specify a different location using the `--output <OUTPUT_DIRECTORY>` option.</span></span> <span data-ttu-id="a6668-123">Kořenový adresář úložiště obsahuje cílový soubor *. XML artefaktu* manifestu.</span><span class="sxs-lookup"><span data-stu-id="a6668-123">The root directory of the store contains a target manifest *artifact.xml* file.</span></span> <span data-ttu-id="a6668-124">Tento soubor může být zpřístupněn ke stažení a musí ho používat autoři aplikací, kteří chtějí toto úložiště cílit při publikování.</span><span class="sxs-lookup"><span data-stu-id="a6668-124">This file can be made available for download and be used by app authors who want to target this store when publishing.</span></span>

<span data-ttu-id="a6668-125">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="a6668-125">**Example**</span></span>

<span data-ttu-id="a6668-126">Následující soubor *artefakt. XML* se vytvoří po spuštění předchozího příkladu.</span><span class="sxs-lookup"><span data-stu-id="a6668-126">The following *artifact.xml* file is produced after running the previous example.</span></span> <span data-ttu-id="a6668-127">Všimněte si, že [`Castle.Core`](https://www.nuget.org/packages/Castle.Core/) je závislost `Moq`, takže je automaticky zahrnutá a zobrazí se v souboru manifestu *artefakts. XML* .</span><span class="sxs-lookup"><span data-stu-id="a6668-127">Note that [`Castle.Core`](https://www.nuget.org/packages/Castle.Core/) is a dependency of `Moq`, so it's included automatically and appears in the *artifacts.xml* manifest file.</span></span>

```xml
<StoreArtifacts>
  <Package Id="Newtonsoft.Json" Version="10.0.3" />
  <Package Id="Castle.Core" Version="4.1.0" />
  <Package Id="Moq" Version="4.7.63" />
</StoreArtifacts>
```

## <a name="publishing-an-app-against-a-target-manifest"></a><span data-ttu-id="a6668-128">Publikování aplikace proti cílovému manifestu</span><span class="sxs-lookup"><span data-stu-id="a6668-128">Publishing an app against a target manifest</span></span>

<span data-ttu-id="a6668-129">Pokud máte cílový soubor manifestu na disku, zadejte cestu k souboru při publikování aplikace pomocí příkazu [`dotnet publish`](../tools/dotnet-publish.md) :</span><span class="sxs-lookup"><span data-stu-id="a6668-129">If you have a target manifest file on disk, you specify the path to the file when publishing your app with the [`dotnet publish`](../tools/dotnet-publish.md) command:</span></span>

```dotnetcli
dotnet publish --manifest <PATH_TO_MANIFEST_FILE>
```

<span data-ttu-id="a6668-130">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="a6668-130">**Example**</span></span>

```dotnetcli
dotnet publish --manifest manifest.xml
```

<span data-ttu-id="a6668-131">Výslednou publikovanou aplikaci nasadíte do prostředí, které obsahuje balíčky popsané v cílovém manifestu.</span><span class="sxs-lookup"><span data-stu-id="a6668-131">You deploy the resulting published app to an environment that has the packages described in the target manifest.</span></span> <span data-ttu-id="a6668-132">V důsledku neúspěšného spuštění aplikace dojde k selhání.</span><span class="sxs-lookup"><span data-stu-id="a6668-132">Failing to do so results in the app failing to start.</span></span>

<span data-ttu-id="a6668-133">Zadejte více cílových manifestů při publikování aplikace opakováním možnosti a cesty (například `--manifest manifest1.xml --manifest manifest2.xml`).</span><span class="sxs-lookup"><span data-stu-id="a6668-133">Specify multiple target manifests when publishing an app by repeating the option and path (for example, `--manifest manifest1.xml --manifest manifest2.xml`).</span></span> <span data-ttu-id="a6668-134">V takovém případě se aplikace ořízne pro sjednocení balíčků zadaných v cílových souborech manifestu, které jsou k dispozici v příkazu.</span><span class="sxs-lookup"><span data-stu-id="a6668-134">When you do so, the app is trimmed for the union of packages specified in the target manifest files provided to the command.</span></span>

## <a name="specifying-target-manifests-in-the-project-file"></a><span data-ttu-id="a6668-135">Určení cílových manifestů v souboru projektu</span><span class="sxs-lookup"><span data-stu-id="a6668-135">Specifying target manifests in the project file</span></span>

<span data-ttu-id="a6668-136">Alternativou k určení cílových manifestů pomocí příkazu [`dotnet publish`](../tools/dotnet-publish.md) je zadat je do souboru projektu jako seznam cest oddělených středníkem v **\<TargetManifestFiles >** značku.</span><span class="sxs-lookup"><span data-stu-id="a6668-136">An alternative to specifying target manifests with the [`dotnet publish`](../tools/dotnet-publish.md) command is to specify them in the project file as a semicolon-separated list of paths under a **\<TargetManifestFiles>** tag.</span></span>

```xml
<PropertyGroup>
  <TargetManifestFiles>manifest1.xml;manifest2.xml</TargetManifestFiles>
</PropertyGroup>
```

<span data-ttu-id="a6668-137">Zadejte cílové manifesty v souboru projektu pouze v případě, že cílové prostředí pro aplikaci je dobře známé, například u projektů .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a6668-137">Specify the target manifests in the project file only when the target environment for the app is well-known, such as for .NET Core projects.</span></span> <span data-ttu-id="a6668-138">Nejedná se o případ open source projektů.</span><span class="sxs-lookup"><span data-stu-id="a6668-138">This isn't the case for open-source projects.</span></span> <span data-ttu-id="a6668-139">Uživatelé open source projektu ji obvykle nasadí do různých produkčních prostředí.</span><span class="sxs-lookup"><span data-stu-id="a6668-139">The users of an open-source project typically deploy it to different production environments.</span></span> <span data-ttu-id="a6668-140">Tato produkční prostředí mají většinou nainstalované různé sady balíčků.</span><span class="sxs-lookup"><span data-stu-id="a6668-140">These production environments generally have different sets of packages pre-installed.</span></span> <span data-ttu-id="a6668-141">V takových prostředích nemůžete vytvářet předpoklady pro cílový manifest, proto byste měli použít možnost `--manifest` [`dotnet publish`](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="a6668-141">You can't make assumptions about the target manifest in such environments, so you should use the `--manifest` option of [`dotnet publish`](../tools/dotnet-publish.md).</span></span>

## <a name="aspnet-core-implicit-store"></a><span data-ttu-id="a6668-142">ASP.NET Core implicitního úložiště</span><span class="sxs-lookup"><span data-stu-id="a6668-142">ASP.NET Core implicit store</span></span>

<span data-ttu-id="a6668-143">ASP.NET Core implicitní úložiště platí pouze pro ASP.NET Core 2,0.</span><span class="sxs-lookup"><span data-stu-id="a6668-143">The ASP.NET Core implicit store applies only to ASP.NET Core 2.0.</span></span> <span data-ttu-id="a6668-144">Důrazně doporučujeme, aby aplikace používaly ASP.NET Core 2,1 a novější, které **nepoužívají implicitní** úložiště.</span><span class="sxs-lookup"><span data-stu-id="a6668-144">We strongly recommend applications use ASP.NET Core 2.1 and later, which does **not** use the implicit store.</span></span> <span data-ttu-id="a6668-145">ASP.NET Core 2,1 a novější používají sdílené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a6668-145">ASP.NET Core 2.1 and later use the shared framework.</span></span>

<span data-ttu-id="a6668-146">Funkce úložiště balíčků za běhu se implicitně používá v aplikaci ASP.NET Core, když se aplikace nasadí jako aplikace [nasazení závislá na rozhraní (FDD)](index.md#publish-runtime-dependent) .</span><span class="sxs-lookup"><span data-stu-id="a6668-146">The runtime package store feature is used implicitly by an ASP.NET Core app when the app is deployed as a [framework-dependent deployment (FDD)](index.md#publish-runtime-dependent) app.</span></span> <span data-ttu-id="a6668-147">Cíle v [`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk) zahrnují manifesty odkazující na implicitní úložiště balíčků v cílovém systému.</span><span class="sxs-lookup"><span data-stu-id="a6668-147">The targets in [`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk) include manifests referencing the implicit package store on the target system.</span></span> <span data-ttu-id="a6668-148">Kromě toho jakákoli aplikace FDD, která závisí na balíčku `Microsoft.AspNetCore.All`, má za následek publikovanou aplikaci, která obsahuje jenom aplikaci a její prostředky, a ne balíčky uvedené v `Microsoft.AspNetCore.All` Metapackage.</span><span class="sxs-lookup"><span data-stu-id="a6668-148">Additionally, any FDD app that depends on the `Microsoft.AspNetCore.All` package results in a published app that contains only the app and its assets and not the packages listed in the `Microsoft.AspNetCore.All` metapackage.</span></span> <span data-ttu-id="a6668-149">Předpokládá se, že tyto balíčky jsou k dispozici v cílovém systému.</span><span class="sxs-lookup"><span data-stu-id="a6668-149">It's assumed that those packages are present on the target system.</span></span>

<span data-ttu-id="a6668-150">V případě, že je nainstalováno .NET Core SDK, je úložiště balíčků modulu runtime nainstalováno na hostiteli.</span><span class="sxs-lookup"><span data-stu-id="a6668-150">The runtime package store is installed on the host when the .NET Core SDK is installed.</span></span> <span data-ttu-id="a6668-151">Další instalační programy můžou poskytnout běhové úložiště balíčků, včetně instalace zip/tarballu .NET Core SDK, `apt-get`, Red Hat Yumu, hostitelského sady Windows serveru .NET Core a ručních instalací balíčků běhového prostředí.</span><span class="sxs-lookup"><span data-stu-id="a6668-151">Other installers may provide the runtime package store, including Zip/tarball installations of the .NET Core SDK, `apt-get`, Red Hat Yum, the .NET Core Windows Server Hosting bundle, and manual runtime package store installations.</span></span>

<span data-ttu-id="a6668-152">Při nasazování aplikace [pro nasazení závislé na rozhraní (FDD)](index.md#publish-runtime-dependent) se ujistěte, že je v cílovém prostředí nainstalovaný .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="a6668-152">When deploying a [framework-dependent deployment (FDD)](index.md#publish-runtime-dependent) app, make sure that the target environment has the .NET Core SDK installed.</span></span> <span data-ttu-id="a6668-153">Pokud je aplikace nasazená do prostředí, které neobsahuje ASP.NET Core, můžete implicitní úložiště odhlásit zadáním **\<PublishWithAspNetCoreTargetManifest >** nastaveno na `false` v souboru projektu, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="a6668-153">If the app is deployed to an environment that doesn't include ASP.NET Core, you can opt out of the implicit store by specifying  **\<PublishWithAspNetCoreTargetManifest>** set to `false` in the project file as in the following example:</span></span>

```xml
<PropertyGroup>
  <PublishWithAspNetCoreTargetManifest>false</PublishWithAspNetCoreTargetManifest>
</PropertyGroup>
```

> [!NOTE]
> <span data-ttu-id="a6668-154">Pro aplikace [s podporou nasazení (SCD)](index.md#publish-self-contained) se předpokládá, že cílový systém nutně neobsahuje požadované balíčky manifestu.</span><span class="sxs-lookup"><span data-stu-id="a6668-154">For [self-contained deployment (SCD)](index.md#publish-self-contained) apps, it's assumed that the target system doesn't necessarily contain the required manifest packages.</span></span> <span data-ttu-id="a6668-155">Proto **\<PublishWithAspNetCoreTargetManifest >** pro aplikaci SCD nelze nastavit na `true`.</span><span class="sxs-lookup"><span data-stu-id="a6668-155">Therefore, **\<PublishWithAspNetCoreTargetManifest>** cannot be set to `true` for an SCD app.</span></span>

<span data-ttu-id="a6668-156">Pokud nasadíte aplikaci se závislostí manifestu, která je přítomna v nasazení (sestavení je k dispozici ve složce *bin* ), není úložiště balíčků modulu runtime *použito* na hostiteli pro toto sestavení.</span><span class="sxs-lookup"><span data-stu-id="a6668-156">If you deploy an application with a manifest dependency that's present in the deployment (the assembly is present in the *bin* folder), the runtime package store *isn't used* on the host for that assembly.</span></span> <span data-ttu-id="a6668-157">Sestavení složky *bin* se používá bez ohledu na jeho přítomnost v úložišti balíčků modulu runtime na hostiteli.</span><span class="sxs-lookup"><span data-stu-id="a6668-157">The *bin* folder assembly is used regardless of its presence in the runtime package store on the host.</span></span>

<span data-ttu-id="a6668-158">Verze závislosti uvedená v manifestu se musí shodovat s verzí závislosti v úložišti balíčků modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="a6668-158">The version of the dependency indicated in the manifest must match the version of the dependency in the runtime package store.</span></span> <span data-ttu-id="a6668-159">Pokud se neshoduje s verzí mezi závislostí v cílovém manifestu a verzí, která existuje v úložišti balíčků modulu runtime a aplikace neobsahuje požadovanou verzi balíčku ve svém nasazení, aplikace se nepodaří spustit.</span><span class="sxs-lookup"><span data-stu-id="a6668-159">If you have a version mismatch between the dependency in the target manifest and the version that exists in the runtime package store and the app doesn't include the required version of the package in its deployment, the app fails to start.</span></span> <span data-ttu-id="a6668-160">Výjimkou je název cílového manifestu, který byl volán pro sestavení úložiště balíčků modulu runtime, což vám pomůže vyřešit neshodu.</span><span class="sxs-lookup"><span data-stu-id="a6668-160">The exception includes the name of the target manifest that called for the runtime package store assembly, which helps you troubleshoot the mismatch.</span></span>

<span data-ttu-id="a6668-161">Pokud je při publikování *oříznuto* nasazení, jsou z publikovaného výstupu zadrženy pouze konkrétní verze balíčků manifestů, které označíte.</span><span class="sxs-lookup"><span data-stu-id="a6668-161">When the deployment is *trimmed* on publish, only the specific versions of the manifest packages you indicate are withheld from the published output.</span></span> <span data-ttu-id="a6668-162">Aby bylo možné aplikaci spustit, musí být balíčky na zmíněných verzích přítomny na hostiteli.</span><span class="sxs-lookup"><span data-stu-id="a6668-162">The packages at the versions indicated must be present on the host for the app to start.</span></span>

## <a name="see-also"></a><span data-ttu-id="a6668-163">Viz také</span><span class="sxs-lookup"><span data-stu-id="a6668-163">See also</span></span>

- [<span data-ttu-id="a6668-164">dotnet – publikování</span><span class="sxs-lookup"><span data-stu-id="a6668-164">dotnet-publish</span></span>](../tools/dotnet-publish.md)
- [<span data-ttu-id="a6668-165">dotnet – úložiště</span><span class="sxs-lookup"><span data-stu-id="a6668-165">dotnet-store</span></span>](../tools/dotnet-store.md)
