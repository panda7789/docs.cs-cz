---
title: Úložiště balíčků modulu runtime
description: Zjistěte, jak pomocí úložiště balíčků runtime cílit manifesty používané jádrem .NET Core.
ms.date: 08/12/2017
ms.openlocfilehash: 7a833ed95147608c6fb403f8f0dec179d2a73833
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77448955"
---
# <a name="runtime-package-store"></a><span data-ttu-id="22df3-103">Úložiště balíčků modulu runtime</span><span class="sxs-lookup"><span data-stu-id="22df3-103">Runtime package store</span></span>

<span data-ttu-id="22df3-104">Počínaje rozhraním .NET Core 2.0 je možné balit a nasazovat aplikace proti známé sadě balíčků, které existují v cílovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="22df3-104">Starting with .NET Core 2.0, it's possible to package and deploy apps against a known set of packages that exist in the target environment.</span></span> <span data-ttu-id="22df3-105">Výhodou jsou rychlejší nasazení, nižší využití místa na disku a v některých případech lepší výkon při spuštění.</span><span class="sxs-lookup"><span data-stu-id="22df3-105">The benefits are faster deployments, lower disk space usage, and improved startup performance in some cases.</span></span>

<span data-ttu-id="22df3-106">Tato funkce je implementována jako *runtime package store*, což je adresář na disku, kde jsou uloženy balíčky (obvykle na */usr/local/share/dotnet/store* na macOS/Linux a *C:/Program Files/dotnet/store* v systému Windows).</span><span class="sxs-lookup"><span data-stu-id="22df3-106">This feature is implemented as a *runtime package store*, which is a directory on disk where packages are stored (typically at */usr/local/share/dotnet/store* on macOS/Linux and *C:/Program Files/dotnet/store* on Windows).</span></span> <span data-ttu-id="22df3-107">Pod tímto adresářem jsou podadresáře pro architektury a [cílové architektury](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="22df3-107">Under this directory, there are subdirectories for architectures and [target frameworks](../../standard/frameworks.md).</span></span> <span data-ttu-id="22df3-108">Rozložení souboru je podobné způsobu, jakým [jsou prostředky NuGet rozloženy na disku](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure):</span><span class="sxs-lookup"><span data-stu-id="22df3-108">The file layout is similar to the way that [NuGet assets are laid out on disk](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure):</span></span>

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

<span data-ttu-id="22df3-109">*Cílový soubor manifestu* uvádí balíčky v úložišti balíčků runtime.</span><span class="sxs-lookup"><span data-stu-id="22df3-109">A *target manifest* file lists the packages in the runtime package store.</span></span> <span data-ttu-id="22df3-110">Vývojáři mohou cílit na tento manifest při publikování své aplikace.</span><span class="sxs-lookup"><span data-stu-id="22df3-110">Developers can target this manifest when publishing their app.</span></span> <span data-ttu-id="22df3-111">Cílový manifest je obvykle poskytován vlastníkem cílového produkčního prostředí.</span><span class="sxs-lookup"><span data-stu-id="22df3-111">The target manifest is typically provided by the owner of the targeted production environment.</span></span>

## <a name="preparing-a-runtime-environment"></a><span data-ttu-id="22df3-112">Příprava runtime prostředí</span><span class="sxs-lookup"><span data-stu-id="22df3-112">Preparing a runtime environment</span></span>

<span data-ttu-id="22df3-113">Správce prostředí runtime můžete optimalizovat aplikace pro rychlejší nasazení a nižší využití místa na disku vytvořením úložiště balíčků runtime a odpovídající cílový manifest.</span><span class="sxs-lookup"><span data-stu-id="22df3-113">The administrator of a runtime environment can optimize apps for faster deployments and lower disk space use by building a runtime package store and the corresponding target manifest.</span></span>

<span data-ttu-id="22df3-114">Prvním krokem je vytvoření *manifestu úložiště balíčků,* který obsahuje seznam balíčků, které tvoří úložiště balíčků runtime.</span><span class="sxs-lookup"><span data-stu-id="22df3-114">The first step is to create a *package store manifest* that lists the packages that compose the runtime package store.</span></span> <span data-ttu-id="22df3-115">Tento formát souboru je kompatibilní s formátem souboru projektu (*csproj*).</span><span class="sxs-lookup"><span data-stu-id="22df3-115">This file format is compatible with the project file format (*csproj*).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="<NUGET_PACKAGE>" Version="<VERSION>" />
    <!-- Include additional packages here -->
  </ItemGroup>
</Project>
```

<span data-ttu-id="22df3-116">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="22df3-116">**Example**</span></span>

<span data-ttu-id="22df3-117">Následující ukázkový manifest úložiště balíčků *(packages.csproj*) se používá k přidání [`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) a [`Moq`](https://www.nuget.org/packages/moq/) do runtime úložiště balíčků:</span><span class="sxs-lookup"><span data-stu-id="22df3-117">The following example package store manifest (*packages.csproj*) is used to add [`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) and [`Moq`](https://www.nuget.org/packages/moq/) to a runtime package store:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.3" />
    <PackageReference Include="Moq" Version="4.7.63" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="22df3-118">Zřízení úložiště balíčků runtime `dotnet store` spuštěním s manifestem úložiště balíčků, runtime a framework:</span><span class="sxs-lookup"><span data-stu-id="22df3-118">Provision the runtime package store by executing `dotnet store` with the package store manifest, runtime, and framework:</span></span>

```dotnetcli
dotnet store --manifest <PATH_TO_MANIFEST_FILE> --runtime <RUNTIME_IDENTIFIER> --framework <FRAMEWORK>
```

<span data-ttu-id="22df3-119">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="22df3-119">**Example**</span></span>

```dotnetcli
dotnet store --manifest packages.csproj --runtime win10-x64 --framework netcoreapp2.0 --framework-version 2.0.0
```

<span data-ttu-id="22df3-120">Můžete předat více cest manifestu úložiště [`dotnet store`](../tools/dotnet-store.md) cílového balíčku k jednomu příkazu opakováním možnosti a cesty v příkazu.</span><span class="sxs-lookup"><span data-stu-id="22df3-120">You can pass multiple target package store manifest paths to a single [`dotnet store`](../tools/dotnet-store.md) command by repeating the option and path in the command.</span></span>

<span data-ttu-id="22df3-121">Ve výchozím nastavení je výstupem příkazu úložiště balíčků pod podadresářem *.dotnet/store* profilu uživatele.</span><span class="sxs-lookup"><span data-stu-id="22df3-121">By default, the output of the command is a package store under the *.dotnet/store* subdirectory of the user's profile.</span></span> <span data-ttu-id="22df3-122">Pomocí možnosti `--output <OUTPUT_DIRECTORY>` můžete určit jiné umístění.</span><span class="sxs-lookup"><span data-stu-id="22df3-122">You can specify a different location using the `--output <OUTPUT_DIRECTORY>` option.</span></span> <span data-ttu-id="22df3-123">Kořenový adresář úložiště obsahuje cílový soubor *manifestu artefakt.xml.*</span><span class="sxs-lookup"><span data-stu-id="22df3-123">The root directory of the store contains a target manifest *artifact.xml* file.</span></span> <span data-ttu-id="22df3-124">Tento soubor může být k dispozici ke stažení a může být použit autory aplikací, kteří chtějí cílit na tento obchod při publikování.</span><span class="sxs-lookup"><span data-stu-id="22df3-124">This file can be made available for download and be used by app authors who want to target this store when publishing.</span></span>

<span data-ttu-id="22df3-125">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="22df3-125">**Example**</span></span>

<span data-ttu-id="22df3-126">Následující soubor *artifact.xml* je vytvořen po spuštění předchozího příkladu.</span><span class="sxs-lookup"><span data-stu-id="22df3-126">The following *artifact.xml* file is produced after running the previous example.</span></span> <span data-ttu-id="22df3-127">Všimněte [`Castle.Core`](https://www.nuget.org/packages/Castle.Core/) si, že `Moq`je závislost , takže je součástí automaticky a zobrazí se v souboru manifestu *artifacts.xml.*</span><span class="sxs-lookup"><span data-stu-id="22df3-127">Note that [`Castle.Core`](https://www.nuget.org/packages/Castle.Core/) is a dependency of `Moq`, so it's included automatically and appears in the *artifacts.xml* manifest file.</span></span>

```xml
<StoreArtifacts>
  <Package Id="Newtonsoft.Json" Version="10.0.3" />
  <Package Id="Castle.Core" Version="4.1.0" />
  <Package Id="Moq" Version="4.7.63" />
</StoreArtifacts>
```

## <a name="publishing-an-app-against-a-target-manifest"></a><span data-ttu-id="22df3-128">Publikování aplikace proti cílovému manifestu</span><span class="sxs-lookup"><span data-stu-id="22df3-128">Publishing an app against a target manifest</span></span>

<span data-ttu-id="22df3-129">Pokud máte na disku cílový soubor manifestu, zadejte cestu k [`dotnet publish`](../tools/dotnet-publish.md) souboru při publikování aplikace pomocí příkazu:</span><span class="sxs-lookup"><span data-stu-id="22df3-129">If you have a target manifest file on disk, you specify the path to the file when publishing your app with the [`dotnet publish`](../tools/dotnet-publish.md) command:</span></span>

```dotnetcli
dotnet publish --manifest <PATH_TO_MANIFEST_FILE>
```

<span data-ttu-id="22df3-130">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="22df3-130">**Example**</span></span>

```dotnetcli
dotnet publish --manifest manifest.xml
```

<span data-ttu-id="22df3-131">Nasadíte výsledné publikované aplikace do prostředí, které má balíčky popsané v cílovémanifestu.</span><span class="sxs-lookup"><span data-stu-id="22df3-131">You deploy the resulting published app to an environment that has the packages described in the target manifest.</span></span> <span data-ttu-id="22df3-132">Pokud tak neučiníte, nepodaří se spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="22df3-132">Failing to do so results in the app failing to start.</span></span>

<span data-ttu-id="22df3-133">Při publikování aplikace zadejte více cílových manifestů opakováním `--manifest manifest1.xml --manifest manifest2.xml`možnosti a cesty (například ).</span><span class="sxs-lookup"><span data-stu-id="22df3-133">Specify multiple target manifests when publishing an app by repeating the option and path (for example, `--manifest manifest1.xml --manifest manifest2.xml`).</span></span> <span data-ttu-id="22df3-134">Pokud tak učiníte, aplikace je oříznuta pro sjednocení balíčků zadaných v cílových souborech manifestu, které jsou k dispozici příkazu.</span><span class="sxs-lookup"><span data-stu-id="22df3-134">When you do so, the app is trimmed for the union of packages specified in the target manifest files provided to the command.</span></span>

## <a name="specifying-target-manifests-in-the-project-file"></a><span data-ttu-id="22df3-135">Určení cílových manifestů v souboru projektu</span><span class="sxs-lookup"><span data-stu-id="22df3-135">Specifying target manifests in the project file</span></span>

<span data-ttu-id="22df3-136">Alternativou k určení cílových [`dotnet publish`](../tools/dotnet-publish.md) manifestů pomocí příkazu je zadat je v souboru projektu jako seznam cest oddělených středníkem pod značkou \*\* \<TargetManifestFiles>.\*\*</span><span class="sxs-lookup"><span data-stu-id="22df3-136">An alternative to specifying target manifests with the [`dotnet publish`](../tools/dotnet-publish.md) command is to specify them in the project file as a semicolon-separated list of paths under a **\<TargetManifestFiles>** tag.</span></span>

```xml
<PropertyGroup>
  <TargetManifestFiles>manifest1.xml;manifest2.xml</TargetManifestFiles>
</PropertyGroup>
```

<span data-ttu-id="22df3-137">Zadejte cílové manifesty v souboru projektu pouze v případě, že cílové prostředí pro aplikaci je dobře známé, například pro projekty .NET Core.</span><span class="sxs-lookup"><span data-stu-id="22df3-137">Specify the target manifests in the project file only when the target environment for the app is well-known, such as for .NET Core projects.</span></span> <span data-ttu-id="22df3-138">To není případ open-source projektů.</span><span class="sxs-lookup"><span data-stu-id="22df3-138">This isn't the case for open-source projects.</span></span> <span data-ttu-id="22df3-139">Uživatelé projektu s otevřeným zdrojovým kódem obvykle nasazují do různých produkčních prostředí.</span><span class="sxs-lookup"><span data-stu-id="22df3-139">The users of an open-source project typically deploy it to different production environments.</span></span> <span data-ttu-id="22df3-140">Tato produkční prostředí mají obvykle různé sady balíčků předinstalovaných.</span><span class="sxs-lookup"><span data-stu-id="22df3-140">These production environments generally have different sets of packages pre-installed.</span></span> <span data-ttu-id="22df3-141">V takových prostředích nelze provádět předpoklady o cílovém manifestu, takže byste měli použít `--manifest` možnost [`dotnet publish`](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="22df3-141">You can't make assumptions about the target manifest in such environments, so you should use the `--manifest` option of [`dotnet publish`](../tools/dotnet-publish.md).</span></span>

## <a name="aspnet-core-implicit-store"></a><span data-ttu-id="22df3-142">ASP.NET implicitní úložiště Core</span><span class="sxs-lookup"><span data-stu-id="22df3-142">ASP.NET Core implicit store</span></span>

<span data-ttu-id="22df3-143">Implicitní úložiště ASP.NET Core se vztahuje pouze na ASP.NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="22df3-143">The ASP.NET Core implicit store applies only to ASP.NET Core 2.0.</span></span> <span data-ttu-id="22df3-144">Důrazně doporučujeme, aby aplikace používaly ASP.NET Core 2.1 a novějším, který **nepoužívá** implicitní úložiště.</span><span class="sxs-lookup"><span data-stu-id="22df3-144">We strongly recommend applications use ASP.NET Core 2.1 and later, which does **not** use the implicit store.</span></span> <span data-ttu-id="22df3-145">ASP.NET Core 2.1 a později používat sdílený rámec.</span><span class="sxs-lookup"><span data-stu-id="22df3-145">ASP.NET Core 2.1 and later use the shared framework.</span></span>

<span data-ttu-id="22df3-146">Funkce runtime package store se implicitně používá aplikace ASP.NET Core, když je aplikace nasazená jako aplikace [pro nasazení (FDD) závislá na rámci.](index.md#publish-runtime-dependent)</span><span class="sxs-lookup"><span data-stu-id="22df3-146">The runtime package store feature is used implicitly by an ASP.NET Core app when the app is deployed as a [framework-dependent deployment (FDD)](index.md#publish-runtime-dependent) app.</span></span> <span data-ttu-id="22df3-147">Cíle v [`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk) zahrnují manifesty odkazující na implicitní úložiště balíčků v cílovém systému.</span><span class="sxs-lookup"><span data-stu-id="22df3-147">The targets in [`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk) include manifests referencing the implicit package store on the target system.</span></span> <span data-ttu-id="22df3-148">Kromě toho všechny FDD aplikace, `Microsoft.AspNetCore.All` která závisí na balíčku výsledky v publikované aplikaci, která `Microsoft.AspNetCore.All` obsahuje pouze aplikaci a její prostředky a ne balíčky uvedené v metabalíčku.</span><span class="sxs-lookup"><span data-stu-id="22df3-148">Additionally, any FDD app that depends on the `Microsoft.AspNetCore.All` package results in a published app that contains only the app and its assets and not the packages listed in the `Microsoft.AspNetCore.All` metapackage.</span></span> <span data-ttu-id="22df3-149">Předpokládá se, že tyto balíčky jsou přítomny v cílovém systému.</span><span class="sxs-lookup"><span data-stu-id="22df3-149">It's assumed that those packages are present on the target system.</span></span>

<span data-ttu-id="22df3-150">Úložiště runtime balíčků je nainstalováno na hostiteli při instalaci sady .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="22df3-150">The runtime package store is installed on the host when the .NET Core SDK is installed.</span></span> <span data-ttu-id="22df3-151">Ostatní instalační programy mohou poskytovat runtime package store, včetně zip/tarball ových `apt-get`instalací sady .NET Core SDK, , Red Hat Yum, balíčku .NET Core Windows Server Hosting a ručních instalací úložiště runtime balíčků.</span><span class="sxs-lookup"><span data-stu-id="22df3-151">Other installers may provide the runtime package store, including Zip/tarball installations of the .NET Core SDK, `apt-get`, Red Hat Yum, the .NET Core Windows Server Hosting bundle, and manual runtime package store installations.</span></span>

<span data-ttu-id="22df3-152">Při nasazování aplikace [pro nasazení v rámci (FDD)](index.md#publish-runtime-dependent) se ujistěte, že cílové prostředí má nainstalovanou sadu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="22df3-152">When deploying a [framework-dependent deployment (FDD)](index.md#publish-runtime-dependent) app, make sure that the target environment has the .NET Core SDK installed.</span></span> <span data-ttu-id="22df3-153">Pokud je aplikace nasazená do prostředí, které neobsahuje ASP.NET Core, můžete se odhlásit z implicitního úložiště `false` zadáním \*\* \<>PublishWithAspNetCoreTargetManifest\*\* nastavena v souboru projektu jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="22df3-153">If the app is deployed to an environment that doesn't include ASP.NET Core, you can opt out of the implicit store by specifying  **\<PublishWithAspNetCoreTargetManifest>** set to `false` in the project file as in the following example:</span></span>

```xml
<PropertyGroup>
  <PublishWithAspNetCoreTargetManifest>false</PublishWithAspNetCoreTargetManifest>
</PropertyGroup>
```

> [!NOTE]
> <span data-ttu-id="22df3-154">Pro [samostatné nasazení (SCD)](index.md#publish-self-contained) aplikace se předpokládá, že cílový systém nemusí nutně obsahovat požadované balíčky manifestu.</span><span class="sxs-lookup"><span data-stu-id="22df3-154">For [self-contained deployment (SCD)](index.md#publish-self-contained) apps, it's assumed that the target system doesn't necessarily contain the required manifest packages.</span></span> <span data-ttu-id="22df3-155">Proto \*\* \<PublishWithAspNetCoreTargetManifest>\*\* nelze `true` nastavit pro aplikaci SCD.</span><span class="sxs-lookup"><span data-stu-id="22df3-155">Therefore, **\<PublishWithAspNetCoreTargetManifest>** cannot be set to `true` for an SCD app.</span></span>

<span data-ttu-id="22df3-156">Pokud nasadíte aplikaci se závislostí na manifestu, která je přítomna v nasazení (sestavení je k dispozici ve složce *přihrádky),* úložiště balíčků runtime *se nepoužívá* na hostiteli pro toto sestavení.</span><span class="sxs-lookup"><span data-stu-id="22df3-156">If you deploy an application with a manifest dependency that's present in the deployment (the assembly is present in the *bin* folder), the runtime package store *isn't used* on the host for that assembly.</span></span> <span data-ttu-id="22df3-157">Sestavení složky *přihrádky* se používá bez ohledu na jeho přítomnost v úložišti balíčků runtime na hostiteli.</span><span class="sxs-lookup"><span data-stu-id="22df3-157">The *bin* folder assembly is used regardless of its presence in the runtime package store on the host.</span></span>

<span data-ttu-id="22df3-158">Verze závislosti uvedená v manifestu musí odpovídat verzi závislosti v runtime package store.</span><span class="sxs-lookup"><span data-stu-id="22df3-158">The version of the dependency indicated in the manifest must match the version of the dependency in the runtime package store.</span></span> <span data-ttu-id="22df3-159">Pokud máte neshodu verzí mezi závislostí v cílovém manifestu a verzí, která existuje v obchodě s balíčky runtime a aplikace neobsahuje požadovanou verzi balíčku v jeho nasazení, aplikace se nepodaří spustit.</span><span class="sxs-lookup"><span data-stu-id="22df3-159">If you have a version mismatch between the dependency in the target manifest and the version that exists in the runtime package store and the app doesn't include the required version of the package in its deployment, the app fails to start.</span></span> <span data-ttu-id="22df3-160">Výjimka zahrnuje název cílového manifestu, který volal pro sestavení úložiště balíčků runtime, který vám pomůže vyřešit neshodu.</span><span class="sxs-lookup"><span data-stu-id="22df3-160">The exception includes the name of the target manifest that called for the runtime package store assembly, which helps you troubleshoot the mismatch.</span></span>

<span data-ttu-id="22df3-161">Při *oříznutí* nasazení při publikování jsou z publikovaného výstupu odepřeny pouze konkrétní verze balíčků manifestu, které označujete.</span><span class="sxs-lookup"><span data-stu-id="22df3-161">When the deployment is *trimmed* on publish, only the specific versions of the manifest packages you indicate are withheld from the published output.</span></span> <span data-ttu-id="22df3-162">Balíčky v uvedených verzích musí být k dispozici na hostiteli, aby aplikace začala.</span><span class="sxs-lookup"><span data-stu-id="22df3-162">The packages at the versions indicated must be present on the host for the app to start.</span></span>

## <a name="see-also"></a><span data-ttu-id="22df3-163">Viz také</span><span class="sxs-lookup"><span data-stu-id="22df3-163">See also</span></span>

- [<span data-ttu-id="22df3-164">dotnet-publikovat</span><span class="sxs-lookup"><span data-stu-id="22df3-164">dotnet-publish</span></span>](../tools/dotnet-publish.md)
- [<span data-ttu-id="22df3-165">dotnet-store</span><span class="sxs-lookup"><span data-stu-id="22df3-165">dotnet-store</span></span>](../tools/dotnet-store.md)
