---
title: Knihovny NuGet a .NET
description: Doporučení osvědčených postupů pro balení s NuGet pro knihovny .NET
author: jamesnk
ms.author: mairaw
ms.date: 01/15/2019
ms.openlocfilehash: 9288bf440692302c3a0b1954236540af6363f367
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775316"
---
# <a name="nuget"></a><span data-ttu-id="2b88f-103">NuGet</span><span class="sxs-lookup"><span data-stu-id="2b88f-103">NuGet</span></span>

<span data-ttu-id="2b88f-104">NuGet je správce balíčků pro ekosystém .NET a je primárním způsobem, jak vývojáři zjišťují a získávají knihovny .NET open source.</span><span class="sxs-lookup"><span data-stu-id="2b88f-104">NuGet is a package manager for the .NET ecosystem and is the primary way developers discover and acquire .NET open-source libraries.</span></span> <span data-ttu-id="2b88f-105">[NuGet.org](https://www.nuget.org/)je bezplatná služba poskytovaná Microsoftem pro hostování balíčků NuGet, je primárním hostitelem pro veřejné balíčky NuGet, ale můžete publikovat ve vlastních službách NuGet, jako je [MyGet](https://www.myget.org/) a [Azure Artifacts](https://azure.microsoft.com/services/devops/artifacts/).</span><span class="sxs-lookup"><span data-stu-id="2b88f-105">[NuGet.org](https://www.nuget.org/), a free service provided by Microsoft for hosting NuGet packages, is the primary host for public NuGet packages, but you can publish to custom NuGet services like [MyGet](https://www.myget.org/) and [Azure Artifacts](https://azure.microsoft.com/services/devops/artifacts/).</span></span>

<span data-ttu-id="2b88f-106">![NuGet](./media/nuget/nuget-logo.png "NuGet")</span><span class="sxs-lookup"><span data-stu-id="2b88f-106">![NuGet](./media/nuget/nuget-logo.png "NuGet")</span></span>

## <a name="create-a-nuget-package"></a><span data-ttu-id="2b88f-107">Vytvoření balíčku NuGet</span><span class="sxs-lookup"><span data-stu-id="2b88f-107">Create a NuGet package</span></span>

<span data-ttu-id="2b88f-108">Balíček NuGet (`*.nupkg`) je soubor zip, který obsahuje sestavení .NET a přidružená metadata.</span><span class="sxs-lookup"><span data-stu-id="2b88f-108">A NuGet package (`*.nupkg`) is a zip file that contains .NET assemblies and associated metadata.</span></span>

<span data-ttu-id="2b88f-109">Existují dva hlavní způsoby, jak vytvořit balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="2b88f-109">There are two main ways to create a NuGet package.</span></span> <span data-ttu-id="2b88f-110">Novější a doporučený způsob je vytvořit balíček z projektu ve stylu sady SDK (soubor projektu, jehož obsah začíná `<Project Sdk="Microsoft.NET.Sdk">`).</span><span class="sxs-lookup"><span data-stu-id="2b88f-110">The newer and recommended way is to create a package from a SDK-style project (project file whose content starts with `<Project Sdk="Microsoft.NET.Sdk">`).</span></span> <span data-ttu-id="2b88f-111">Sestavení a cíle jsou automaticky přidány do balíčku a zbývající metadata jsou přidána do souboru MSBuild, jako je název balíčku a číslo verze.</span><span class="sxs-lookup"><span data-stu-id="2b88f-111">Assemblies and targets are automatically added to the package and remaining metadata is added to the MSBuild file, like package name and version number.</span></span> <span data-ttu-id="2b88f-112">Kompilace s příkazem [`dotnet pack`](../../core/tools/dotnet-pack.md) vypisuje místo sestavení `*.nupkg` soubor.</span><span class="sxs-lookup"><span data-stu-id="2b88f-112">Compiling with the [`dotnet pack`](../../core/tools/dotnet-pack.md) command outputs a `*.nupkg` file instead of assemblies.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
    <AssemblyName>Contoso.Api</AssemblyName>
    <PackageVersion>1.1.0</PackageVersion>
    <Authors>John Doe</Authors>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="2b88f-113">Starší způsob vytváření balíčku NuGet je soubor `*.nuspec` a nástroj `nuget.exe` příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="2b88f-113">The older way of creating a NuGet package is with a `*.nuspec` file and the `nuget.exe` command-line tool.</span></span> <span data-ttu-id="2b88f-114">Soubor nuspec vám dává Skvělé řízení, ale musíte pečlivě určit, jaká sestavení a cíle se mají zahrnout do finálního balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="2b88f-114">A nuspec file gives you great control but you must carefully specify what assemblies and targets to include in the final NuGet package.</span></span> <span data-ttu-id="2b88f-115">Je snadné vytvořit chybu nebo někoho, aby se při provádění změn aktualizoval nuspec.</span><span class="sxs-lookup"><span data-stu-id="2b88f-115">It's easy to make a mistake or for someone to forget to update the nuspec when making changes.</span></span> <span data-ttu-id="2b88f-116">Výhodou nuspec je, že můžete použít vytvoření balíčků NuGet pro architektury, které ještě nepodporují soubor projektu ve stylu sady SDK.</span><span class="sxs-lookup"><span data-stu-id="2b88f-116">The advantage of a nuspec is you can use it create NuGet packages for frameworks that don't yet support an SDK-style project file.</span></span>

<span data-ttu-id="2b88f-117">**✔️ zvažte** použití souboru projektu ve stylu sady SDK k vytvoření balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="2b88f-117">**✔️ CONSIDER** using an SDK-style project file to create the NuGet package.</span></span>

## <a name="package-dependencies"></a><span data-ttu-id="2b88f-118">Závislosti balíčků</span><span class="sxs-lookup"><span data-stu-id="2b88f-118">Package dependencies</span></span>

<span data-ttu-id="2b88f-119">Závislosti balíčků NuGet jsou podrobně popsané v článku [závislosti](./dependencies.md) .</span><span class="sxs-lookup"><span data-stu-id="2b88f-119">NuGet package dependencies are covered in detail in the [Dependencies](./dependencies.md) article.</span></span>

## <a name="important-nuget-package-metadata"></a><span data-ttu-id="2b88f-120">Důležitá metadata balíčku NuGet</span><span class="sxs-lookup"><span data-stu-id="2b88f-120">Important NuGet package metadata</span></span>

<span data-ttu-id="2b88f-121">Balíček NuGet podporuje mnoho [vlastností metadat](/nuget/reference/nuspec).</span><span class="sxs-lookup"><span data-stu-id="2b88f-121">A NuGet package supports many [metadata properties](/nuget/reference/nuspec).</span></span> <span data-ttu-id="2b88f-122">Následující tabulka obsahuje základní metadata, která by měl každý balíček v NuGet.org poskytnout:</span><span class="sxs-lookup"><span data-stu-id="2b88f-122">The following table contains the core metadata that every package on NuGet.org should provide:</span></span>

| <span data-ttu-id="2b88f-123">Název vlastnosti MSBuild</span><span class="sxs-lookup"><span data-stu-id="2b88f-123">MSBuild Property name</span></span>              | <span data-ttu-id="2b88f-124">Název nuspec</span><span class="sxs-lookup"><span data-stu-id="2b88f-124">Nuspec name</span></span>              | <span data-ttu-id="2b88f-125">Popis</span><span class="sxs-lookup"><span data-stu-id="2b88f-125">Description</span></span>  |
| ---------------------------------- | ------------------------ | ------------ |
| `PackageId`                        | `id`                       | <span data-ttu-id="2b88f-126">Identifikátor balíčku.</span><span class="sxs-lookup"><span data-stu-id="2b88f-126">The package identifier.</span></span> <span data-ttu-id="2b88f-127">Předpona z identifikátoru může být vyhrazena, pokud splňuje [kritéria](/nuget/reference/id-prefix-reservation).</span><span class="sxs-lookup"><span data-stu-id="2b88f-127">A prefix from the identifier can be reserved if it meets the [criteria](/nuget/reference/id-prefix-reservation).</span></span> |
| `PackageVersion`                   | `version`                  | <span data-ttu-id="2b88f-128">Verze balíčku NuGet</span><span class="sxs-lookup"><span data-stu-id="2b88f-128">NuGet package version.</span></span> <span data-ttu-id="2b88f-129">Další informace najdete v tématu [verze balíčku NuGet](./versioning.md#nuget-package-version).</span><span class="sxs-lookup"><span data-stu-id="2b88f-129">For more information, see [NuGet package version](./versioning.md#nuget-package-version).</span></span>             |
| `Title`                            | `title`                    | <span data-ttu-id="2b88f-130">Popisný název balíčku.</span><span class="sxs-lookup"><span data-stu-id="2b88f-130">A human-friendly title of the package.</span></span> <span data-ttu-id="2b88f-131">Výchozím nastavením je `PackageId`.</span><span class="sxs-lookup"><span data-stu-id="2b88f-131">It defaults to the `PackageId`.</span></span>             |
| `Description`                      | `description`              | <span data-ttu-id="2b88f-132">Dlouhý popis balíčku zobrazeného v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2b88f-132">A long description of the package displayed in UI.</span></span>             |
| `Authors`                          | `authors`                  | <span data-ttu-id="2b88f-133">Čárkami oddělený seznam autorů balíčků, které odpovídají názvům profilů v nuget.org.</span><span class="sxs-lookup"><span data-stu-id="2b88f-133">A comma-separated list of package authors, matching the profile names on nuget.org.</span></span>             |
| `PackageTags`                      | `tags`                     | <span data-ttu-id="2b88f-134">Mezerou oddělený seznam značek a klíčových slov, které popisují balíček.</span><span class="sxs-lookup"><span data-stu-id="2b88f-134">A space-delimited list of tags and keywords that describe the package.</span></span> <span data-ttu-id="2b88f-135">Značky se používají při hledání balíčků.</span><span class="sxs-lookup"><span data-stu-id="2b88f-135">Tags are used when searching for packages.</span></span>             |
| `PackageIconUrl`                   | `iconUrl`                  | <span data-ttu-id="2b88f-136">Adresa URL obrázku, který má být použit jako ikona balíčku.</span><span class="sxs-lookup"><span data-stu-id="2b88f-136">A URL for an image to use as the icon for the package.</span></span> <span data-ttu-id="2b88f-137">Adresa URL by měla být HTTPS a Image by měla být 64 × 64 a měla by mít transparentní pozadí.</span><span class="sxs-lookup"><span data-stu-id="2b88f-137">URL should be HTTPS and the image should be 64x64 and have a transparent background.</span></span>             |
| `PackageProjectUrl`                | `projectUrl`               | <span data-ttu-id="2b88f-138">Adresa URL domovské stránky projektu nebo zdrojového úložiště.</span><span class="sxs-lookup"><span data-stu-id="2b88f-138">A URL for the project homepage or source repository.</span></span>             |
| `PackageLicenseExpression`         | `license`                  | <span data-ttu-id="2b88f-139">[Identifikátor SPDX](https://spdx.org/licenses/)licence projektu.</span><span class="sxs-lookup"><span data-stu-id="2b88f-139">The project license's [SPDX identifier](https://spdx.org/licenses/).</span></span> <span data-ttu-id="2b88f-140">Identifikátor můžou používat jenom licence OSI a FSF schválené.</span><span class="sxs-lookup"><span data-stu-id="2b88f-140">Only OSI and FSF approved licenses can use an identifier.</span></span> <span data-ttu-id="2b88f-141">Jiné licence by se měly používat `PackageLicenseFile`.</span><span class="sxs-lookup"><span data-stu-id="2b88f-141">Other licenses should use `PackageLicenseFile`.</span></span> <span data-ttu-id="2b88f-142">Přečtěte si další informace o [`license` metadatech](/nuget/reference/nuspec#license).</span><span class="sxs-lookup"><span data-stu-id="2b88f-142">Read more about [`license` metadata](/nuget/reference/nuspec#license).</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="2b88f-143">Projekt bez licence se standardně [vylučuje na výhradní Copyright](https://choosealicense.com/no-permission/), což umožňuje, aby ho jiní uživatelé mohli používat.</span><span class="sxs-lookup"><span data-stu-id="2b88f-143">A project without a license defaults to [exclusive copyright](https://choosealicense.com/no-permission/), making it legally impossible for other people to use.</span></span>

<span data-ttu-id="2b88f-144">**✔️ zvažte** možnost zvolit název balíčku NuGet s předponou, která splňuje [kritéria](/nuget/reference/id-prefix-reservation)rezervace předpon NuGet.</span><span class="sxs-lookup"><span data-stu-id="2b88f-144">**✔️ CONSIDER** choosing a NuGet package name with a prefix that meets NuGet's prefix reservation [criteria](/nuget/reference/id-prefix-reservation).</span></span>

<span data-ttu-id="2b88f-145">**✔️** použijte odkaz HTTPS href na ikonu balíčku.</span><span class="sxs-lookup"><span data-stu-id="2b88f-145">**✔️ DO** use an HTTPS href to your package icon.</span></span>

> <span data-ttu-id="2b88f-146">Weby, jako je NuGet.org spuštěná s povoleným protokolem HTTPS a zobrazením image bez HTTPS, vytvoří upozornění na smíšený obsah.</span><span class="sxs-lookup"><span data-stu-id="2b88f-146">Sites like NuGet.org run with HTTPS enabled and displaying a non-HTTPS image will create a mixed content warning.</span></span>

<span data-ttu-id="2b88f-147">**✔️** použít obrázek ikony balíčku, který je 64 × 64 a má transparentní pozadí pro nejlepší výsledky zobrazení.</span><span class="sxs-lookup"><span data-stu-id="2b88f-147">**✔️ DO** use a package icon image that is 64x64 and has a transparent background for best viewing results.</span></span>

<span data-ttu-id="2b88f-148">**✔️ zvažte** nastavení [zdrojového odkazu](./sourcelink.md) pro přidání metadat správy zdrojů do sestavení a balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="2b88f-148">**✔️ CONSIDER** setting up [Source Link](./sourcelink.md) to add source control metadata to your assemblies and NuGet package.</span></span>

> <span data-ttu-id="2b88f-149">Odkaz na zdroj automaticky přidá do balíčku NuGet metadata `RepositoryUrl` a `RepositoryType`.</span><span class="sxs-lookup"><span data-stu-id="2b88f-149">Source Link automatically adds `RepositoryUrl` and `RepositoryType` metadata to the NuGet package.</span></span> <span data-ttu-id="2b88f-150">Odkaz na zdroj také přidá informace o přesném zdrojovém kódu, ze kterého byl balíček sestaven.</span><span class="sxs-lookup"><span data-stu-id="2b88f-150">Source Link also adds information about the exact source code the package was built from.</span></span> <span data-ttu-id="2b88f-151">Například balíček vytvořený z úložiště Git bude obsahovat hodnotu hash potvrzení přidané jako metadata.</span><span class="sxs-lookup"><span data-stu-id="2b88f-151">For example, a package created from a Git repository will have the commit hash added as metadata.</span></span>

## <a name="pre-release-packages"></a><span data-ttu-id="2b88f-152">Předběžné verze balíčků</span><span class="sxs-lookup"><span data-stu-id="2b88f-152">Pre-release packages</span></span>

<span data-ttu-id="2b88f-153">Balíčky NuGet s příponou verze se považují za [předběžné verze](/nuget/create-packages/prerelease-packages).</span><span class="sxs-lookup"><span data-stu-id="2b88f-153">NuGet packages with a version suffix are considered [pre-release](/nuget/create-packages/prerelease-packages).</span></span> <span data-ttu-id="2b88f-154">Ve výchozím nastavení uživatelské rozhraní Správce balíčků NuGet zobrazuje stabilní verze, pokud se uživatel výslovný k předběžným balíčkům, takže předběžné verze balíčků jsou ideální pro omezené testování uživatelů.</span><span class="sxs-lookup"><span data-stu-id="2b88f-154">By default, the NuGet Package Manager UI shows stable releases unless a user opts-in to pre-release packages, making pre-release packages ideal for limited user testing.</span></span>

```xml
<PackageVersion>1.0.1-beta1</PackageVersion>
```

> [!NOTE]
> <span data-ttu-id="2b88f-155">Stabilní balíček nemůže záviset na předběžné verzi balíčku.</span><span class="sxs-lookup"><span data-stu-id="2b88f-155">A stable package cannot depend on a pre-release package.</span></span> <span data-ttu-id="2b88f-156">Musíte buď udělat předběžnou verzi balíčku, nebo závisí na starší verzi stabilní verze.</span><span class="sxs-lookup"><span data-stu-id="2b88f-156">You must either make your own package pre-release or depend on an older stable version.</span></span>

<span data-ttu-id="2b88f-157">![Závislost předběžné verze balíčku NuGet](./media/nuget/nuget-prerelease-package.png "Závislost předběžné verze balíčku NuGet")</span><span class="sxs-lookup"><span data-stu-id="2b88f-157">![NuGet pre-release package dependency](./media/nuget/nuget-prerelease-package.png "NuGet pre-release package dependency")</span></span>

<span data-ttu-id="2b88f-158">**✔️** publikovat předběžnou verzi balíčku při testování, náhledu nebo experimentování.</span><span class="sxs-lookup"><span data-stu-id="2b88f-158">**✔️ DO** publish a pre-release package when testing, previewing, or experimenting.</span></span>

<span data-ttu-id="2b88f-159">**✔️** po jeho přípravě publikovat stabilní balíček, aby na něj mohli odkazovat další stabilní balíčky.</span><span class="sxs-lookup"><span data-stu-id="2b88f-159">**✔️ DO** publish a stable package when its ready so other stable packages can reference it.</span></span>

## <a name="symbol-packages"></a><span data-ttu-id="2b88f-160">Balíčky symbolů</span><span class="sxs-lookup"><span data-stu-id="2b88f-160">Symbol packages</span></span>

<span data-ttu-id="2b88f-161">Soubory symbolů (`*.pdb`) jsou vytvářeny kompilátorem rozhraní .NET spolu se sestaveními.</span><span class="sxs-lookup"><span data-stu-id="2b88f-161">Symbol files (`*.pdb`) are produced by the .NET compiler alongside assemblies.</span></span> <span data-ttu-id="2b88f-162">Soubory symbolů mapují umístění spuštění na původní zdrojový kód, takže můžete procházet zdrojový kód tak, jak je spuštěn pomocí ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="2b88f-162">Symbol files map execution locations to the original source code so you can step through source code as it is running using a debugger.</span></span> <span data-ttu-id="2b88f-163">NuGet podporuje [vygenerování samostatného balíčku symbolů (`*.snupkg`)](/nuget/create-packages/symbol-packages-snupkg) obsahujícího soubory symbolů společně s hlavním balíčkem obsahujícím sestavení .NET.</span><span class="sxs-lookup"><span data-stu-id="2b88f-163">NuGet supports [generating a separate symbol package (`*.snupkg`)](/nuget/create-packages/symbol-packages-snupkg) containing symbol files alongside the main package containing .NET assemblies.</span></span> <span data-ttu-id="2b88f-164">Nápad balíčků symbolů je hostovaný na serveru symbolů a stahuje se jenom nástrojem, jako je Visual Studio na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="2b88f-164">The idea of symbol packages is they're hosted on a symbol server and are only downloaded by a tool like Visual Studio on demand.</span></span>

<span data-ttu-id="2b88f-165">NuGet.org hostuje své vlastní [úložiště symbolů serveru](/nuget/create-packages/symbol-packages-snupkg#nugetorg-symbol-server).</span><span class="sxs-lookup"><span data-stu-id="2b88f-165">NuGet.org hosts its own [symbols server repository](/nuget/create-packages/symbol-packages-snupkg#nugetorg-symbol-server).</span></span> <span data-ttu-id="2b88f-166">Vývojáři mohou používat symboly publikované na serveru symbolů NuGet.org přidáním `https://symbols.nuget.org/download/symbols` do jejich [zdrojů symbolů v aplikaci Visual Studio](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger).</span><span class="sxs-lookup"><span data-stu-id="2b88f-166">Developers can use the symbols published to the NuGet.org symbol server by adding `https://symbols.nuget.org/download/symbols` to their [symbol sources in Visual Studio](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2b88f-167">Server symbolů NuGet.org podporuje pouze nové [přenositelné soubory symbolů](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) (`*.pdb`) vytvořené projekty ve stylu sady SDK.</span><span class="sxs-lookup"><span data-stu-id="2b88f-167">The NuGet.org symbol server only supports the new [portable symbol files](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) (`*.pdb`) created by SDK-style projects.</span></span>
>
> <span data-ttu-id="2b88f-168">Chcete-li použít server symbolů NuGet.org při ladění knihovny .NET, musí mít vývojáři Visual Studio 2017 verze 15,9 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="2b88f-168">To use the NuGet.org symbol server when debugging a .NET library, developers must have Visual Studio 2017 version 15.9 or later.</span></span>

<span data-ttu-id="2b88f-169">Alternativou k vytvoření balíčku symbolů je vkládání souborů symbolů do hlavního balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="2b88f-169">An alternative to creating a symbol package is embedding symbol files in the main NuGet package.</span></span> <span data-ttu-id="2b88f-170">Hlavní balíček NuGet bude větší, ale vložené soubory symbolů znamená, že vývojáři nepotřebují konfigurovat server symbolů NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="2b88f-170">The main NuGet package will be larger, but the embedded symbol files means developers don't need to configure the NuGet.org symbol server.</span></span> <span data-ttu-id="2b88f-171">Pokud vytváříte balíček NuGet pomocí projektu ve stylu sady SDK, můžete vložit soubory symbolů nastavením vlastnosti `AllowedOutputExtensionsInPackageBuildOutputFolder`:</span><span class="sxs-lookup"><span data-stu-id="2b88f-171">If you're building your NuGet package using an SDK-style project, then you can embed symbol files by setting the `AllowedOutputExtensionsInPackageBuildOutputFolder` property:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
 <PropertyGroup>
    <!-- Include symbol files (*.pdb) in the built .nupkg -->
    <AllowedOutputExtensionsInPackageBuildOutputFolder>$(AllowedOutputExtensionsInPackageBuildOutputFolder);.pdb</AllowedOutputExtensionsInPackageBuildOutputFolder>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="2b88f-172">Nevýhodou soubory symbolů vkládání je to, že zvyšují velikost balíčku o přibližně 30% pro knihovny .NET zkompilované pomocí projektů ve stylu sady SDK.</span><span class="sxs-lookup"><span data-stu-id="2b88f-172">The downside of embedding symbol files is that they increase the package size by about 30% for .NET libraries compiled using SDK-style projects.</span></span> <span data-ttu-id="2b88f-173">Pokud je velikost balíčku obavou, místo toho byste měli publikovat symboly v balíčku symbolů.</span><span class="sxs-lookup"><span data-stu-id="2b88f-173">If package size is a concern, you should publish symbols in a symbol package instead.</span></span>

<span data-ttu-id="2b88f-174">**✔️ zvažte** publikování symbolů jako balíčku symbolů (`*.snupkg`) do NuGet.org</span><span class="sxs-lookup"><span data-stu-id="2b88f-174">**✔️ CONSIDER** publishing symbols as a symbol package (`*.snupkg`) to NuGet.org</span></span>

> <span data-ttu-id="2b88f-175">Balíčky symbolů (`*.snupkg`) poskytují vývojářům kvalitní možnosti ladění na vyžádání, aniž by bloating hlavní velikost balíčku a ovlivnily výkon obnovení pro uživatele, kteří nemají v úmyslu ladit balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="2b88f-175">Symbol packages (`*.snupkg`) provide developers a good on-demand debugging experience without bloating the main package size and impacting restore performance for those who don't intend to debug the NuGet package.</span></span>
>
> <span data-ttu-id="2b88f-176">Upozornění je, že uživatelé mohou potřebovat vyhledat a nakonfigurovat server symbolů NuGet v integrovaném vývojovém prostředí (jako jednorázovou instalaci) a získat tak soubory symbolů.</span><span class="sxs-lookup"><span data-stu-id="2b88f-176">The caveat is that users may need to find and configure the NuGet symbol server in their IDE (as a one-time setup) to get symbol files.</span></span> <span data-ttu-id="2b88f-177">Visual Studio 2019 verze 16,1 přidala server symbolů NuGet. org do seznamu výchozích symbolových serverů.</span><span class="sxs-lookup"><span data-stu-id="2b88f-177">Visual Studio 2019 version 16.1 added NuGet.org's symbol server to the list of default symbol servers.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="2b88f-178">[Předchozí](strong-naming.md)
>[Další](dependencies.md)</span><span class="sxs-lookup"><span data-stu-id="2b88f-178">[Previous](strong-naming.md)
[Next](dependencies.md)</span></span>
