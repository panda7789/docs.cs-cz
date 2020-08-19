---
title: Úložiště balíčků modulu runtime
description: Naučte se používat úložiště balíčků modulu runtime pro cílení na manifesty používané .NET Core.
ms.date: 08/12/2017
ms.openlocfilehash: e9e27ef535dbd9e7197c323f7e49a9960aeff0f9
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608359"
---
# <a name="runtime-package-store"></a><span data-ttu-id="c6722-103">Úložiště balíčků modulu runtime</span><span class="sxs-lookup"><span data-stu-id="c6722-103">Runtime package store</span></span>

<span data-ttu-id="c6722-104">Počínaje .NET Core 2,0 je možné zabalit a nasazovat aplikace na známou sadu balíčků, které existují v cílovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="c6722-104">Starting with .NET Core 2.0, it's possible to package and deploy apps against a known set of packages that exist in the target environment.</span></span> <span data-ttu-id="c6722-105">Výhody jsou rychlejší nasazení, nižší využití místa na disku a Vylepšený výkon při spuštění v některých případech.</span><span class="sxs-lookup"><span data-stu-id="c6722-105">The benefits are faster deployments, lower disk space usage, and improved startup performance in some cases.</span></span>

<span data-ttu-id="c6722-106">Tato funkce je implementována jako *běhové úložiště balíčků*, což je adresář na disku, kde jsou uloženy balíčky (obvykle na */usr/local/share/dotnet/Store* v MacOS/Linux a *C:/Program Files/dotnet/Store* ve Windows).</span><span class="sxs-lookup"><span data-stu-id="c6722-106">This feature is implemented as a *runtime package store*, which is a directory on disk where packages are stored (typically at */usr/local/share/dotnet/store* on macOS/Linux and *C:/Program Files/dotnet/store* on Windows).</span></span> <span data-ttu-id="c6722-107">V tomto adresáři jsou podadresáře pro architektury a [cílové](../../standard/frameworks.md)architektury.</span><span class="sxs-lookup"><span data-stu-id="c6722-107">Under this directory, there are subdirectories for architectures and [target frameworks](../../standard/frameworks.md).</span></span> <span data-ttu-id="c6722-108">Rozložení souboru je podobné způsobu, jakým [jsou prostředky NuGet na disku rozloženy](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure):</span><span class="sxs-lookup"><span data-stu-id="c6722-108">The file layout is similar to the way that [NuGet assets are laid out on disk](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure):</span></span>

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

<span data-ttu-id="c6722-109">*Cílový soubor manifestu* uvádí balíčky v úložišti balíčků modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="c6722-109">A *target manifest* file lists the packages in the runtime package store.</span></span> <span data-ttu-id="c6722-110">Vývojáři můžou tento manifest cílit při publikování aplikace.</span><span class="sxs-lookup"><span data-stu-id="c6722-110">Developers can target this manifest when publishing their app.</span></span> <span data-ttu-id="c6722-111">Cílový manifest je obvykle poskytován vlastníkem cílového produkčního prostředí.</span><span class="sxs-lookup"><span data-stu-id="c6722-111">The target manifest is typically provided by the owner of the targeted production environment.</span></span>

## <a name="preparing-a-runtime-environment"></a><span data-ttu-id="c6722-112">Příprava běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="c6722-112">Preparing a runtime environment</span></span>

<span data-ttu-id="c6722-113">Správce běhového prostředí může optimalizovat aplikace pro rychlejší nasazení a snížit využití místa na disku vytvořením běhového balíčku za běhu a odpovídajícího cílového manifestu.</span><span class="sxs-lookup"><span data-stu-id="c6722-113">The administrator of a runtime environment can optimize apps for faster deployments and lower disk space use by building a runtime package store and the corresponding target manifest.</span></span>

<span data-ttu-id="c6722-114">Prvním krokem je vytvoření *manifestu balíčku pro úložiště* , který obsahuje seznam balíčků, které tvoří úložiště balíčků modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="c6722-114">The first step is to create a *package store manifest* that lists the packages that compose the runtime package store.</span></span> <span data-ttu-id="c6722-115">Tento formát souboru je kompatibilní s formátem souboru projektu (*csproj*).</span><span class="sxs-lookup"><span data-stu-id="c6722-115">This file format is compatible with the project file format (*csproj*).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="NUGET_PACKAGE" Version="VERSION" />
    <!-- Include additional packages here -->
  </ItemGroup>
</Project>
```

<span data-ttu-id="c6722-116">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="c6722-116">**Example**</span></span>

<span data-ttu-id="c6722-117">Následující ukázkový manifest úložiště balíčků (*Packages. csproj*) se používá k přidání [`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) a [`Moq`](https://www.nuget.org/packages/moq/) do úložiště balíčků modulu runtime:</span><span class="sxs-lookup"><span data-stu-id="c6722-117">The following example package store manifest (*packages.csproj*) is used to add [`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) and [`Moq`](https://www.nuget.org/packages/moq/) to a runtime package store:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.3" />
    <PackageReference Include="Moq" Version="4.7.63" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="c6722-118">Zřízení úložiště balíčků modulu runtime spuštěním `dotnet store` s manifestem úložiště balíčků, modulem runtime a rozhraním:</span><span class="sxs-lookup"><span data-stu-id="c6722-118">Provision the runtime package store by executing `dotnet store` with the package store manifest, runtime, and framework:</span></span>

```dotnetcli
dotnet store --manifest <PATH_TO_MANIFEST_FILE> --runtime <RUNTIME_IDENTIFIER> --framework <FRAMEWORK>
```

<span data-ttu-id="c6722-119">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="c6722-119">**Example**</span></span>

```dotnetcli
dotnet store --manifest packages.csproj --runtime win10-x64 --framework netcoreapp2.0 --framework-version 2.0.0
```

<span data-ttu-id="c6722-120">Můžete předat několik cest k manifestu cílového úložiště balíčků do jediného [`dotnet store`](../tools/dotnet-store.md) příkazu opakováním možnosti a cesty v příkazu.</span><span class="sxs-lookup"><span data-stu-id="c6722-120">You can pass multiple target package store manifest paths to a single [`dotnet store`](../tools/dotnet-store.md) command by repeating the option and path in the command.</span></span>

<span data-ttu-id="c6722-121">Ve výchozím nastavení je výstupem příkazu úložiště balíčků v podadresáři *. dotnet/Store* profilu uživatele.</span><span class="sxs-lookup"><span data-stu-id="c6722-121">By default, the output of the command is a package store under the *.dotnet/store* subdirectory of the user's profile.</span></span> <span data-ttu-id="c6722-122">Pomocí možnosti můžete zadat jiné umístění `--output <OUTPUT_DIRECTORY>` .</span><span class="sxs-lookup"><span data-stu-id="c6722-122">You can specify a different location using the `--output <OUTPUT_DIRECTORY>` option.</span></span> <span data-ttu-id="c6722-123">Kořenový adresář úložiště obsahuje cílový soubor manifestu *artifact.xml* .</span><span class="sxs-lookup"><span data-stu-id="c6722-123">The root directory of the store contains a target manifest *artifact.xml* file.</span></span> <span data-ttu-id="c6722-124">Tento soubor může být zpřístupněn ke stažení a musí ho používat autoři aplikací, kteří chtějí toto úložiště cílit při publikování.</span><span class="sxs-lookup"><span data-stu-id="c6722-124">This file can be made available for download and be used by app authors who want to target this store when publishing.</span></span>

<span data-ttu-id="c6722-125">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="c6722-125">**Example**</span></span>

<span data-ttu-id="c6722-126">Po spuštění předchozího příkladu se vytvoří následující soubor *artifact.xml* .</span><span class="sxs-lookup"><span data-stu-id="c6722-126">The following *artifact.xml* file is produced after running the previous example.</span></span> <span data-ttu-id="c6722-127">Všimněte si, že [`Castle.Core`](https://www.nuget.org/packages/Castle.Core/) se jedná o závislost `Moq` , takže je automaticky zahrnutá a zobrazí se v souboru manifestu *artifacts.xml* .</span><span class="sxs-lookup"><span data-stu-id="c6722-127">Note that [`Castle.Core`](https://www.nuget.org/packages/Castle.Core/) is a dependency of `Moq`, so it's included automatically and appears in the *artifacts.xml* manifest file.</span></span>

```xml
<StoreArtifacts>
  <Package Id="Newtonsoft.Json" Version="10.0.3" />
  <Package Id="Castle.Core" Version="4.1.0" />
  <Package Id="Moq" Version="4.7.63" />
</StoreArtifacts>
```

## <a name="publishing-an-app-against-a-target-manifest"></a><span data-ttu-id="c6722-128">Publikování aplikace proti cílovému manifestu</span><span class="sxs-lookup"><span data-stu-id="c6722-128">Publishing an app against a target manifest</span></span>

<span data-ttu-id="c6722-129">Pokud máte cílový soubor manifestu na disku, zadejte cestu k souboru při publikování aplikace pomocí [`dotnet publish`](../tools/dotnet-publish.md) příkazu:</span><span class="sxs-lookup"><span data-stu-id="c6722-129">If you have a target manifest file on disk, you specify the path to the file when publishing your app with the [`dotnet publish`](../tools/dotnet-publish.md) command:</span></span>

```dotnetcli
dotnet publish --manifest <PATH_TO_MANIFEST_FILE>
```

<span data-ttu-id="c6722-130">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="c6722-130">**Example**</span></span>

```dotnetcli
dotnet publish --manifest manifest.xml
```

<span data-ttu-id="c6722-131">Výslednou publikovanou aplikaci nasadíte do prostředí, které obsahuje balíčky popsané v cílovém manifestu.</span><span class="sxs-lookup"><span data-stu-id="c6722-131">You deploy the resulting published app to an environment that has the packages described in the target manifest.</span></span> <span data-ttu-id="c6722-132">V důsledku neúspěšného spuštění aplikace dojde k selhání.</span><span class="sxs-lookup"><span data-stu-id="c6722-132">Failing to do so results in the app failing to start.</span></span>

<span data-ttu-id="c6722-133">Zadejte více cílových manifestů při publikování aplikace opakováním možnosti a cesty (například `--manifest manifest1.xml --manifest manifest2.xml` ).</span><span class="sxs-lookup"><span data-stu-id="c6722-133">Specify multiple target manifests when publishing an app by repeating the option and path (for example, `--manifest manifest1.xml --manifest manifest2.xml`).</span></span> <span data-ttu-id="c6722-134">V takovém případě se aplikace ořízne pro sjednocení balíčků zadaných v cílových souborech manifestu, které jsou k dispozici v příkazu.</span><span class="sxs-lookup"><span data-stu-id="c6722-134">When you do so, the app is trimmed for the union of packages specified in the target manifest files provided to the command.</span></span>

<span data-ttu-id="c6722-135">Pokud nasadíte aplikaci se závislostí manifestu, která je přítomna v nasazení (sestavení je k dispozici ve složce *bin* ), není úložiště balíčků modulu runtime *použito* na hostiteli pro toto sestavení.</span><span class="sxs-lookup"><span data-stu-id="c6722-135">If you deploy an application with a manifest dependency that's present in the deployment (the assembly is present in the *bin* folder), the runtime package store *isn't used* on the host for that assembly.</span></span> <span data-ttu-id="c6722-136">Sestavení složky *bin* se používá bez ohledu na jeho přítomnost v úložišti balíčků modulu runtime na hostiteli.</span><span class="sxs-lookup"><span data-stu-id="c6722-136">The *bin* folder assembly is used regardless of its presence in the runtime package store on the host.</span></span>

<span data-ttu-id="c6722-137">Verze závislosti uvedená v manifestu se musí shodovat s verzí závislosti v úložišti balíčků modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="c6722-137">The version of the dependency indicated in the manifest must match the version of the dependency in the runtime package store.</span></span> <span data-ttu-id="c6722-138">Pokud se neshoduje s verzí mezi závislostí v cílovém manifestu a verzí, která existuje v úložišti balíčků modulu runtime a aplikace neobsahuje požadovanou verzi balíčku ve svém nasazení, aplikace se nepodaří spustit.</span><span class="sxs-lookup"><span data-stu-id="c6722-138">If you have a version mismatch between the dependency in the target manifest and the version that exists in the runtime package store and the app doesn't include the required version of the package in its deployment, the app fails to start.</span></span> <span data-ttu-id="c6722-139">Výjimkou je název cílového manifestu, který byl volán pro sestavení úložiště balíčků modulu runtime, což vám pomůže vyřešit neshodu.</span><span class="sxs-lookup"><span data-stu-id="c6722-139">The exception includes the name of the target manifest that called for the runtime package store assembly, which helps you troubleshoot the mismatch.</span></span>

<span data-ttu-id="c6722-140">Pokud je při publikování *oříznuto* nasazení, jsou z publikovaného výstupu zadrženy pouze konkrétní verze balíčků manifestů, které označíte.</span><span class="sxs-lookup"><span data-stu-id="c6722-140">When the deployment is *trimmed* on publish, only the specific versions of the manifest packages you indicate are withheld from the published output.</span></span> <span data-ttu-id="c6722-141">Aby bylo možné aplikaci spustit, musí být balíčky na zmíněných verzích přítomny na hostiteli.</span><span class="sxs-lookup"><span data-stu-id="c6722-141">The packages at the versions indicated must be present on the host for the app to start.</span></span>

## <a name="specifying-target-manifests-in-the-project-file"></a><span data-ttu-id="c6722-142">Určení cílových manifestů v souboru projektu</span><span class="sxs-lookup"><span data-stu-id="c6722-142">Specifying target manifests in the project file</span></span>

<span data-ttu-id="c6722-143">Alternativou k určení cílových manifestů pomocí [`dotnet publish`](../tools/dotnet-publish.md) příkazu je zadat je do souboru projektu jako seznam cest oddělených středníkem v rámci **\<TargetManifestFiles>** značky.</span><span class="sxs-lookup"><span data-stu-id="c6722-143">An alternative to specifying target manifests with the [`dotnet publish`](../tools/dotnet-publish.md) command is to specify them in the project file as a semicolon-separated list of paths under a **\<TargetManifestFiles>** tag.</span></span>

```xml
<PropertyGroup>
  <TargetManifestFiles>manifest1.xml;manifest2.xml</TargetManifestFiles>
</PropertyGroup>
```

<span data-ttu-id="c6722-144">Zadejte cílové manifesty v souboru projektu pouze v případě, že cílové prostředí pro aplikaci je dobře známé, například u projektů .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c6722-144">Specify the target manifests in the project file only when the target environment for the app is well-known, such as for .NET Core projects.</span></span> <span data-ttu-id="c6722-145">Nejedná se o případ open source projektů.</span><span class="sxs-lookup"><span data-stu-id="c6722-145">This isn't the case for open-source projects.</span></span> <span data-ttu-id="c6722-146">Uživatelé open source projektu ji obvykle nasadí do různých produkčních prostředí.</span><span class="sxs-lookup"><span data-stu-id="c6722-146">The users of an open-source project typically deploy it to different production environments.</span></span> <span data-ttu-id="c6722-147">Tato produkční prostředí mají většinou nainstalované různé sady balíčků.</span><span class="sxs-lookup"><span data-stu-id="c6722-147">These production environments generally have different sets of packages pre-installed.</span></span> <span data-ttu-id="c6722-148">V takových prostředích nemůžete vytvářet předpoklady pro cílový manifest, proto byste měli použít `--manifest` možnost [`dotnet publish`](../tools/dotnet-publish.md) .</span><span class="sxs-lookup"><span data-stu-id="c6722-148">You can't make assumptions about the target manifest in such environments, so you should use the `--manifest` option of [`dotnet publish`](../tools/dotnet-publish.md).</span></span>

## <a name="aspnet-core-implicit-store-net-core-20-only"></a><span data-ttu-id="c6722-149">ASP.NET Core implicitního úložiště (jenom .NET Core 2,0)</span><span class="sxs-lookup"><span data-stu-id="c6722-149">ASP.NET Core implicit store (.NET Core 2.0 only)</span></span>

<span data-ttu-id="c6722-150">ASP.NET Core implicitní úložiště platí pouze pro ASP.NET Core 2,0.</span><span class="sxs-lookup"><span data-stu-id="c6722-150">The ASP.NET Core implicit store applies only to ASP.NET Core 2.0.</span></span> <span data-ttu-id="c6722-151">Důrazně doporučujeme, aby aplikace používaly ASP.NET Core 2,1 a novější, které **nepoužívají implicitní** úložiště.</span><span class="sxs-lookup"><span data-stu-id="c6722-151">We strongly recommend applications use ASP.NET Core 2.1 and later, which does **not** use the implicit store.</span></span> <span data-ttu-id="c6722-152">ASP.NET Core 2,1 a novější používají sdílené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c6722-152">ASP.NET Core 2.1 and later use the shared framework.</span></span>

<span data-ttu-id="c6722-153">Pro .NET Core 2,0 se funkce úložiště balíčků za běhu implicitně používá v aplikaci ASP.NET Core, když je aplikace nasazená jako aplikace [nasazení závislá na rozhraní](index.md#publish-framework-dependent) .</span><span class="sxs-lookup"><span data-stu-id="c6722-153">For .NET Core 2.0, the runtime package store feature is used implicitly by an ASP.NET Core app when the app is deployed as a [framework-dependent deployment](index.md#publish-framework-dependent) app.</span></span> <span data-ttu-id="c6722-154">Cíle v [`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk) zahrnutých manifestech odkazují na implicitní úložiště balíčků v cílovém systému.</span><span class="sxs-lookup"><span data-stu-id="c6722-154">The targets in [`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk) include manifests referencing the implicit package store on the target system.</span></span> <span data-ttu-id="c6722-155">Kromě toho jakákoli aplikace závislá na rozhraní, která závisí na `Microsoft.AspNetCore.All` balíčku, má za následek publikovanou aplikaci, která obsahuje jenom aplikaci a její prostředky, a ne balíčky uvedené v `Microsoft.AspNetCore.All` Metapackage.</span><span class="sxs-lookup"><span data-stu-id="c6722-155">Additionally, any framework-dependent app that depends on the `Microsoft.AspNetCore.All` package results in a published app that contains only the app and its assets and not the packages listed in the `Microsoft.AspNetCore.All` metapackage.</span></span> <span data-ttu-id="c6722-156">Předpokládá se, že tyto balíčky jsou k dispozici v cílovém systému.</span><span class="sxs-lookup"><span data-stu-id="c6722-156">It's assumed that those packages are present on the target system.</span></span>

<span data-ttu-id="c6722-157">V případě, že je nainstalováno .NET Core SDK, je úložiště balíčků modulu runtime nainstalováno na hostiteli.</span><span class="sxs-lookup"><span data-stu-id="c6722-157">The runtime package store is installed on the host when the .NET Core SDK is installed.</span></span> <span data-ttu-id="c6722-158">Ostatní instalační programy můžou poskytovat běhové úložiště balíčků, včetně instalací zip/tarballu .NET Core SDK, `apt-get` , Red Hat Yumu, hostování sady .NET Core Windows serveru a ručních instalací běhového balíčku.</span><span class="sxs-lookup"><span data-stu-id="c6722-158">Other installers may provide the runtime package store, including Zip/tarball installations of the .NET Core SDK, `apt-get`, Red Hat Yum, the .NET Core Windows Server Hosting bundle, and manual runtime package store installations.</span></span>

<span data-ttu-id="c6722-159">Při nasazování aplikace [pro nasazení závislé na rozhraní](index.md#publish-framework-dependent) se ujistěte, že je v cílovém prostředí nainstalovaný .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="c6722-159">When deploying a [framework-dependent deployment](index.md#publish-framework-dependent) app, make sure that the target environment has the .NET Core SDK installed.</span></span> <span data-ttu-id="c6722-160">Pokud je aplikace nasazena do prostředí, které neobsahuje ASP.NET Core, můžete z implicitního úložiště odsouhlasit zadáním parametru  **\<PublishWithAspNetCoreTargetManifest>** set to `false` v souboru projektu, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c6722-160">If the app is deployed to an environment that doesn't include ASP.NET Core, you can opt out of the implicit store by specifying  **\<PublishWithAspNetCoreTargetManifest>** set to `false` in the project file as in the following example:</span></span>

```xml
<PropertyGroup>
  <PublishWithAspNetCoreTargetManifest>false</PublishWithAspNetCoreTargetManifest>
</PropertyGroup>
```

> [!NOTE]
> <span data-ttu-id="c6722-161">U [samostatných](index.md#publish-self-contained) aplikací pro nasazení se předpokládá, že cílový systém nutně neobsahuje požadované balíčky manifestu.</span><span class="sxs-lookup"><span data-stu-id="c6722-161">For [self-contained deployment](index.md#publish-self-contained) apps, it's assumed that the target system doesn't necessarily contain the required manifest packages.</span></span> <span data-ttu-id="c6722-162">Proto **\<PublishWithAspNetCoreTargetManifest>** nejde nastavit na `true` pro aplikaci, která je samostatně obsažená.</span><span class="sxs-lookup"><span data-stu-id="c6722-162">Therefore, **\<PublishWithAspNetCoreTargetManifest>** cannot be set to `true` for an self-contained app.</span></span>

## <a name="see-also"></a><span data-ttu-id="c6722-163">Viz také</span><span class="sxs-lookup"><span data-stu-id="c6722-163">See also</span></span>

- [<span data-ttu-id="c6722-164">dotnet – publikování</span><span class="sxs-lookup"><span data-stu-id="c6722-164">dotnet-publish</span></span>](../tools/dotnet-publish.md)
- [<span data-ttu-id="c6722-165">dotnet – úložiště</span><span class="sxs-lookup"><span data-stu-id="c6722-165">dotnet-store</span></span>](../tools/dotnet-store.md)
