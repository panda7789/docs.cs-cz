---
title: "Úložiště balíčku modulu runtime"
description: "Toto téma vysvětluje runtime balíček úložiště a cílový manifesty používané .NET Core."
keywords: "Rozhraní .NET, .NET core dotnet úložiště, úložiště balíček modulu runtime"
author: bleroy
ms.author: mairaw
ms.date: 08/12/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 9521d8b4-25fc-412b-a65b-4c975ebf6bfd
ms.openlocfilehash: 607f8259fa6d8488a7fccf3c7d90b6cf40d5f237
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="runtime-package-store"></a><span data-ttu-id="79491-104">Úložiště balíčku modulu runtime</span><span class="sxs-lookup"><span data-stu-id="79491-104">Runtime package store</span></span>

<span data-ttu-id="79491-105">Od verze rozhraní .NET Core 2.0, je možné balíček a nasazení aplikací proti se známou sadou balíčky, které existují v cílovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="79491-105">Starting with .NET Core 2.0, it's possible to package and deploy apps against a known set of packages that exist in the target environment.</span></span> <span data-ttu-id="79491-106">Výhody jsou rychlejší nasazení, nižší využití místa na disku a spuštění lepší výkon v některých případech.</span><span class="sxs-lookup"><span data-stu-id="79491-106">The benefits are faster deployments, lower disk space use, and improved startup performance in some cases.</span></span>

<span data-ttu-id="79491-107">Tato funkce je implementovaná jako *úložiště balíčku runtime*, tedy adresáře na disku, kde jsou uloženy balíčky (obvykle na */usr/local/share/dotnet/store* v systému macOS/Linux a *C: / Program soubory nebo dotnet/úložiště* v systému Windows).</span><span class="sxs-lookup"><span data-stu-id="79491-107">This feature is implemented as a *runtime package store*, which is a directory on disk where packages are stored (typically at */usr/local/share/dotnet/store* on macOS/Linux and *C:/Program Files/dotnet/store* on Windows).</span></span> <span data-ttu-id="79491-108">V tomto adresáři neexistují podadresáře pro architektury a [cílové rozhraní](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="79491-108">Under this directory, there are subdirectories for architectures and [target frameworks](../../standard/frameworks.md).</span></span> <span data-ttu-id="79491-109">Rozložení souboru je podobným způsobem, který [NuGet prostředky jsou nastíněny na disku](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure):</span><span class="sxs-lookup"><span data-stu-id="79491-109">The file layout is similar to the way that [NuGet assets are laid out on disk](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure):</span></span>

<span data-ttu-id="79491-110">\dotnet</span><span class="sxs-lookup"><span data-stu-id="79491-110">\dotnet</span></span>   
<span data-ttu-id="79491-111">&nbsp;&nbsp;\store</span><span class="sxs-lookup"><span data-stu-id="79491-111">&nbsp;&nbsp;\store</span></span>   
<span data-ttu-id="79491-112">&nbsp;&nbsp;&nbsp;&nbsp;\x64</span><span class="sxs-lookup"><span data-stu-id="79491-112">&nbsp;&nbsp;&nbsp;&nbsp;\x64</span></span>   
<span data-ttu-id="79491-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\netcoreapp2.0</span><span class="sxs-lookup"><span data-stu-id="79491-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\netcoreapp2.0</span></span>   
<span data-ttu-id="79491-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\Microsoft.applicationinsights</span><span class="sxs-lookup"><span data-stu-id="79491-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.applicationinsights</span></span>   
<span data-ttu-id="79491-115">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\Microsoft.aspnetcore</span><span class="sxs-lookup"><span data-stu-id="79491-115">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.aspnetcore</span></span>   
<span data-ttu-id="79491-116">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...</span><span class="sxs-lookup"><span data-stu-id="79491-116">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...</span></span>   
<span data-ttu-id="79491-117">&nbsp;&nbsp;&nbsp;&nbsp;\x86</span><span class="sxs-lookup"><span data-stu-id="79491-117">&nbsp;&nbsp;&nbsp;&nbsp;\x86</span></span>   
<span data-ttu-id="79491-118">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\netcoreapp2.0</span><span class="sxs-lookup"><span data-stu-id="79491-118">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\netcoreapp2.0</span></span>   
<span data-ttu-id="79491-119">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\Microsoft.applicationinsights</span><span class="sxs-lookup"><span data-stu-id="79491-119">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.applicationinsights</span></span>   
<span data-ttu-id="79491-120">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\Microsoft.aspnetcore</span><span class="sxs-lookup"><span data-stu-id="79491-120">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.aspnetcore</span></span>   
<span data-ttu-id="79491-121">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...</span><span class="sxs-lookup"><span data-stu-id="79491-121">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...</span></span>   

<span data-ttu-id="79491-122">A *cíl manifest* soubor obsahuje seznam balíčků v úložišti balíček modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="79491-122">A *target manifest* file lists the packages in the runtime package store.</span></span> <span data-ttu-id="79491-123">Vývojáři mohou být určeny tento manifest při publikování své aplikace.</span><span class="sxs-lookup"><span data-stu-id="79491-123">Developers can target this manifest when publishing their app.</span></span> <span data-ttu-id="79491-124">Cíl manifest se většinou poskytuje vlastníkem cílové produkčního prostředí.</span><span class="sxs-lookup"><span data-stu-id="79491-124">The target manifest is typically provided by the owner of the targeted production environment.</span></span>

## <a name="preparing-a-runtime-environment"></a><span data-ttu-id="79491-125">Příprava prostředí runtime</span><span class="sxs-lookup"><span data-stu-id="79491-125">Preparing a runtime environment</span></span>

<span data-ttu-id="79491-126">Správce běhového prostředí můžete optimalizovat aplikace pro rychlejší nasazení a nižší využití místa na disku podle budovy úložiště balíčku runtime a odpovídající manifest cíl.</span><span class="sxs-lookup"><span data-stu-id="79491-126">The administrator of a runtime environment can optimize apps for faster deployments and lower disk space use by building a runtime package store and the corresponding target manifest.</span></span>

<span data-ttu-id="79491-127">Prvním krokem je vytvoření *manifestu balíčku úložiště* , obsahuje seznam balíčků, které tvoří úložišti balíček modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="79491-127">The first step is to create a *package store manifest* that lists the packages that compose the runtime package store.</span></span> <span data-ttu-id="79491-128">Tento formát souboru není kompatibilní s formátem souboru projektu (*csproj*).</span><span class="sxs-lookup"><span data-stu-id="79491-128">This file format is compatible with the project file format (*csproj*).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="<NUGET_PACKAGE>" Version="<VERSION>" />
    <!-- Include additional packages here -->
  </ItemGroup>
</Project>
```

<span data-ttu-id="79491-129">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="79491-129">**Example**</span></span>

<span data-ttu-id="79491-130">Následující příklad manifest balíčku úložiště (*packages.csproj*) se používá k přidání [ `Newtonsoft.Json` ](https://www.nuget.org/packages/Newtonsoft.Json/) a [ `Moq` ](https://www.nuget.org/packages/moq/) k úložišti balíček modulu runtime:</span><span class="sxs-lookup"><span data-stu-id="79491-130">The following example package store manifest (*packages.csproj*) is used to add [`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) and [`Moq`](https://www.nuget.org/packages/moq/) to a runtime package store:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.3" />
    <PackageReference Include="Moq" Version="4.7.63" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="79491-131">Zřízení úložiště balíčku runtime spuštěním `dotnet store` s manifestu balíčku úložiště, modulu runtime a framework:</span><span class="sxs-lookup"><span data-stu-id="79491-131">Provision the runtime package store by executing `dotnet store` with the package store manifest, runtime, and framework:</span></span>

```console
dotnet store --manifest <PATH_TO_MANIFEST_FILE> --runtime <RUNTIME_IDENTIFIER> --framework <FRAMEWORK>
```

<span data-ttu-id="79491-132">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="79491-132">**Example**</span></span>

```console
dotnet store --manifest packages.csproj --runtime win10-x64 --framework netcoreapp2.0 --framework-version 2.0.0
```

<span data-ttu-id="79491-133">Můžete předat více cest manifestu cílové úložiště balíčku do jednoho [ `dotnet store` ](../tools/dotnet-store.md) příkaz opakováním možnost a cestu v příkazu.</span><span class="sxs-lookup"><span data-stu-id="79491-133">You can pass multiple target package store manifest paths to a single [`dotnet store`](../tools/dotnet-store.md) command by repeating the option and path in the command.</span></span>

<span data-ttu-id="79491-134">Ve výchozím nastavení, je výstup příkazu balíček úložiště v nabídce *.dotnet/úložiště* podadresáři profilu uživatele.</span><span class="sxs-lookup"><span data-stu-id="79491-134">By default, the output of the command is a package store under the *.dotnet/store* subdirectory of the user's profile.</span></span> <span data-ttu-id="79491-135">Můžete zadat jiné umístění pomocí `--output <OUTPUT_DIRECTORY>` možnost.</span><span class="sxs-lookup"><span data-stu-id="79491-135">You can specify a different location using the `--output <OUTPUT_DIRECTORY>` option.</span></span> <span data-ttu-id="79491-136">Kořenový adresář úložiště obsahuje cílový manifestu *artifact.xml* souboru.</span><span class="sxs-lookup"><span data-stu-id="79491-136">The root directory of the store contains a target manifest *artifact.xml* file.</span></span> <span data-ttu-id="79491-137">Tento soubor může být k dispozici ke stažení a použije autory aplikace, které chcete cílit toto úložiště při publikování.</span><span class="sxs-lookup"><span data-stu-id="79491-137">This file can be made available for download and be used by app authors who want to target this store when publishing.</span></span>

<span data-ttu-id="79491-138">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="79491-138">**Example**</span></span>

<span data-ttu-id="79491-139">Následující *artifact.xml* soubor je vytvořen po spuštění předchozí příklad.</span><span class="sxs-lookup"><span data-stu-id="79491-139">The following *artifact.xml* file is produced after running the previous example.</span></span> <span data-ttu-id="79491-140">Všimněte si, že [ `Castle.Core` ](https://www.nuget.org/packages/Castle.Core/) je závislost `Moq`, takže se má automaticky zahrnuty a zobrazí se v *artifacts.xml* souboru manifestu.</span><span class="sxs-lookup"><span data-stu-id="79491-140">Note that [`Castle.Core`](https://www.nuget.org/packages/Castle.Core/) is a dependency of `Moq`, so it's included automatically and appears in the *artifacts.xml* manifest file.</span></span>

```xml
<StoreArtifacts>
  <Package Id="Newtonsoft.Json" Version="10.0.3" />
  <Package Id="Castle.Core" Version="4.1.0" />
  <Package Id="Moq" Version="4.7.63" />
</StoreArtifacts>
```

## <a name="publishing-an-app-against-a-target-manifest"></a><span data-ttu-id="79491-141">Publikování aplikace proti cílové manifestu</span><span class="sxs-lookup"><span data-stu-id="79491-141">Publishing an app against a target manifest</span></span>

<span data-ttu-id="79491-142">Pokud máte soubor manifestu cíl na disku, musíte zadat cestu k souboru, při publikování aplikace pomocí [ `dotnet publish` ](../tools/dotnet-publish.md) příkaz:</span><span class="sxs-lookup"><span data-stu-id="79491-142">If you have a target manifest file on disk, you specify the path to the file when publishing your app with the [`dotnet publish`](../tools/dotnet-publish.md) command:</span></span>

```console
dotnet publish --manifest <PATH_TO_MANIFEST_FILE>
```

<span data-ttu-id="79491-143">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="79491-143">**Example**</span></span>

```console
dotnet publish --manifest manifest.xml
```

<span data-ttu-id="79491-144">Výsledný publikované aplikace můžete nasadit pro prostředí, které má balíčky, které jsou popsané v manifestu cíl.</span><span class="sxs-lookup"><span data-stu-id="79491-144">You deploy the resulting published app to an environment that has the packages described in the target manifest.</span></span> <span data-ttu-id="79491-145">Tak neučiníte způsobuje selhání spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="79491-145">Failing to do so results in the app failing to start.</span></span>

<span data-ttu-id="79491-146">Zadejte více manifesty cíl při publikování aplikace opakováním možnost a cestu (například `--manifest manifest1.xml --manifest manifest2.xml`).</span><span class="sxs-lookup"><span data-stu-id="79491-146">Specify multiple target manifests when publishing an app by repeating the option and path (for example, `--manifest manifest1.xml --manifest manifest2.xml`).</span></span> <span data-ttu-id="79491-147">Pokud tak učiníte, aplikace je oříznut pro sjednocení balíčky zadané v manifestu soubory cíl zadaný pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="79491-147">When you do so, the app is trimmed for the union of packages specified in the target manifest files provided to the command.</span></span>

## <a name="specifying-target-manifests-in-the-project-file"></a><span data-ttu-id="79491-148">Zadání manifesty cíl v souboru projektu</span><span class="sxs-lookup"><span data-stu-id="79491-148">Specifying target manifests in the project file</span></span>

<span data-ttu-id="79491-149">Alternativu k určení cílového manifesty s [ `dotnet publish` ](../tools/dotnet-publish.md) příkaz je zadávat v souboru projektu jako středníky oddělený seznam cest v rámci  **\<TargetManifestFiles >** značky.</span><span class="sxs-lookup"><span data-stu-id="79491-149">An alternative to specifying target manifests with the [`dotnet publish`](../tools/dotnet-publish.md) command is to specify them in the project file as a semicolon-separated list of paths under a **\<TargetManifestFiles>** tag.</span></span>

```xml
<PropertyGroup>
  <TargetManifestFiles>manifest1.xml;manifest2.xml</TargetManifestFiles>
</PropertyGroup>
```

<span data-ttu-id="79491-150">Zadejte cíl manifesty v souboru projektu pouze v případě, že cílové prostředí pro aplikaci je dobře známé, například pro projekty .NET Core.</span><span class="sxs-lookup"><span data-stu-id="79491-150">Specify the target manifests in the project file only when the target environment for the app is well-known, such as for .NET Core projects.</span></span> <span data-ttu-id="79491-151">Tato akce není případ projekty open source.</span><span class="sxs-lookup"><span data-stu-id="79491-151">This isn't the case for open-source projects.</span></span> <span data-ttu-id="79491-152">Uživatelé open-source projekt je obvykle nasadit do různých produkčního prostředí.</span><span class="sxs-lookup"><span data-stu-id="79491-152">The users of an open-source project typically deploy it to different production environments.</span></span> <span data-ttu-id="79491-153">Tyto provozní prostředí obvykle mají různé sady balíčky předem nainstalované.</span><span class="sxs-lookup"><span data-stu-id="79491-153">These production environments generally have different sets of packages pre-installed.</span></span> <span data-ttu-id="79491-154">Nelze provádět předpoklady o manifest cíl v těchto prostředích, měli byste použít `--manifest` možnost [ `dotnet publish` ](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="79491-154">You can't make assumptions about the target manifest in such environments, so you should use the `--manifest` option of [`dotnet publish`](../tools/dotnet-publish.md).</span></span>

## <a name="aspnet-core-implicit-store"></a><span data-ttu-id="79491-155">Implicitní úložiště ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="79491-155">ASP.NET Core implicit store</span></span>

<span data-ttu-id="79491-156">Funkce úložiště balíčku runtime používají implicitně aplikace ASP.NET Core při nasazení aplikace jako [nasazení závislé na framework (disketové jednotky)](index.md#framework-dependent-deployments-fdd) aplikace.</span><span class="sxs-lookup"><span data-stu-id="79491-156">The runtime package store feature is used implicitly by an ASP.NET Core app when the app is deployed as a [framework-dependent deployment (FDD)](index.md#framework-dependent-deployments-fdd) app.</span></span> <span data-ttu-id="79491-157">Cíle v [ `Microsoft.NET.Sdk.Web` ](https://github.com/aspnet/websdk) zahrnují manifesty odkazující na úložišti implicitní balíček v cílovém systému.</span><span class="sxs-lookup"><span data-stu-id="79491-157">The targets in [`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk) include manifests referencing the implicit package store on the target system.</span></span> <span data-ttu-id="79491-158">Kromě toho jakékoli aplikaci disketové jednotky, která závisí na `Microsoft.AspNetCore.All` výsledky v publikované aplikaci, která obsahuje jenom aplikace a její prostředky a není balíčky uvedené v balíčku `Microsoft.AspNetCore.All` metapackage.</span><span class="sxs-lookup"><span data-stu-id="79491-158">Additionally, any FDD app that depends on the `Microsoft.AspNetCore.All` package results in a published app that contains only the app and its assets and not the packages listed in the `Microsoft.AspNetCore.All` metapackage.</span></span> <span data-ttu-id="79491-159">Předpokládá se, zda tyto balíčky jsou k dispozici v cílovém systému.</span><span class="sxs-lookup"><span data-stu-id="79491-159">It's assumed that those packages are present on the target system.</span></span>

<span data-ttu-id="79491-160">Úložiště balíčku runtime je nainstalován na hostiteli, při instalaci .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="79491-160">The runtime package store is installed on the host when the .NET Core SDK is installed.</span></span> <span data-ttu-id="79491-161">Další instalační programy může poskytnout úložišti balíček modulu runtime, včetně Zip nebo tarball instalace rozhraní .NET Core SDK, `apt-get`, Red Hat Yum, sady hostování v rozhraní .NET Core systému Windows Server a instalací balíčku úložiště ruční runtime.</span><span class="sxs-lookup"><span data-stu-id="79491-161">Other installers may provide the runtime package store, including Zip/tarball installations of the .NET Core SDK, `apt-get`, Red Hat Yum, the .NET Core Windows Server Hosting bundle, and manual runtime package store installations.</span></span>

<span data-ttu-id="79491-162">Při nasazování [nasazení závislé na framework (disketové jednotky)](index.md#framework-dependent-deployments-fdd) aplikace, ujistěte se, že cílové prostředí má .NET Core SDK nainstalovat.</span><span class="sxs-lookup"><span data-stu-id="79491-162">When deploying a [framework-dependent deployment (FDD)](index.md#framework-dependent-deployments-fdd) app, make sure that the target environment has the .NET Core SDK installed.</span></span> <span data-ttu-id="79491-163">Pokud je aplikace nasazená na prostředí, které neobsahuje ASP.NET Core, můžete zamítnutí úložišti implicitní zadáním  **\<PublishWithAspNetCoreTargetManifest >** nastavena na `false` v souboru projektu jako v v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="79491-163">If the app is deployed to an environment that doesn't include ASP.NET Core, you can opt out of the implicit store by specifying  **\<PublishWithAspNetCoreTargetManifest>** set to `false` in the project file as in the following example:</span></span>

```xml
<PropertyGroup>
  <PublishWithAspNetCoreTargetManifest>false</PublishWithAspNetCoreTargetManifest>
</PropertyGroup>
```

> [!NOTE] 
> <span data-ttu-id="79491-164">Pro [samostatná nasazení (SCD)](index.md#self-contained-deployments-scd) aplikace, se předpokládá, že cílový systém neobsahuje nutně požadované balíčky manifestu.</span><span class="sxs-lookup"><span data-stu-id="79491-164">For [self-contained deployment (SCD)](index.md#self-contained-deployments-scd) apps, it's assumed that the target system doesn't necessarily contain the required manifest packages.</span></span> <span data-ttu-id="79491-165">Proto  **\<PublishWithAspNetCoreTargetManifest >** nelze nastavit na `true` SCD aplikace.</span><span class="sxs-lookup"><span data-stu-id="79491-165">Therefore, **\<PublishWithAspNetCoreTargetManifest>** cannot be set to `true` for an SCD app.</span></span>

<span data-ttu-id="79491-166">Pokud nasazujete aplikaci s manifestu závislost, která je k dispozici v nasazení (sestavení se nachází ve *bin* složky), úložiště balíčku runtime *nepoužívá* na hostiteli pro toto sestavení.</span><span class="sxs-lookup"><span data-stu-id="79491-166">If you deploy an application with a manifest dependency that's present in the deployment (the assembly is present in the *bin* folder), the runtime package store *isn't used* on the host for that assembly.</span></span> <span data-ttu-id="79491-167">*Bin* sestavení složky se používá bez ohledu na jeho přítomnosti v úložišti runtime balíčku na hostiteli.</span><span class="sxs-lookup"><span data-stu-id="79491-167">The *bin* folder assembly is used regardless of its presence in the runtime package store on the host.</span></span>

<span data-ttu-id="79491-168">Verze závislosti uvedené v manifestu musí shodovat s verzí závislosti v úložišti balíček modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="79491-168">The version of the dependency indicated in the manifest must match the version of the dependency in the runtime package store.</span></span> <span data-ttu-id="79491-169">Pokud máte Neshoda verzí mezi závislostí v manifestu cíl a verzi, která existuje v úložišti balíček modulu runtime a aplikaci neobsahuje požadovaná verze balíčku v jeho nasazení, aplikace se nespustí.</span><span class="sxs-lookup"><span data-stu-id="79491-169">If you have a version mismatch between the dependency in the target manifest and the version that exists in the runtime package store and the app doesn't include the required version of the package in its deployment, the app fails to start.</span></span> <span data-ttu-id="79491-170">Výjimka obsahuje název cílové manifestu, který volá úložiště balíčku sestavení modulu runtime, který vám pomůže vyřešit neshody.</span><span class="sxs-lookup"><span data-stu-id="79491-170">The exception includes the name of the target manifest that called for the runtime package store assembly, which helps you troubleshoot the mismatch.</span></span>

<span data-ttu-id="79491-171">Po nasazení *oříznut* při publikování, jsou pouze konkrétní verze manifestu balíčky, které jste uvedli vyřazeno z publikovaných výstup.</span><span class="sxs-lookup"><span data-stu-id="79491-171">When the deployment is *trimmed* on publish, only the specific versions of the manifest packages you indicate are withheld from the published output.</span></span> <span data-ttu-id="79491-172">Balíčky na uvedené verze musí být přítomen na hostiteli aplikace spustit.</span><span class="sxs-lookup"><span data-stu-id="79491-172">The packages at the versions indicated must be present on the host for the app to start.</span></span>

## <a name="see-also"></a><span data-ttu-id="79491-173">Viz také</span><span class="sxs-lookup"><span data-stu-id="79491-173">See also</span></span>
 [<span data-ttu-id="79491-174">DotNet-publikování</span><span class="sxs-lookup"><span data-stu-id="79491-174">dotnet-publish</span></span>](../tools/dotnet-publish.md)  
 [<span data-ttu-id="79491-175">úložiště DotNet.</span><span class="sxs-lookup"><span data-stu-id="79491-175">dotnet-store</span></span>](../tools/dotnet-store.md)  
