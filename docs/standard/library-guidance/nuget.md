---
title: Knihovny NuGet a .NET
description: Doporučení osvědčených postupů pro balení s NuGet pro knihovny .NET.
ms.date: 01/15/2019
ms.openlocfilehash: f1e8d39fe2988f11ce7fd351a4d6bee6d322f2b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400517"
---
# <a name="nuget"></a><span data-ttu-id="3463e-103">NuGet</span><span class="sxs-lookup"><span data-stu-id="3463e-103">NuGet</span></span>

<span data-ttu-id="3463e-104">NuGet je správce balíčků pro ekosystém .NET a je primární způsob, jak vývojáři zjišťovat a získávat knihovny open source .NET.</span><span class="sxs-lookup"><span data-stu-id="3463e-104">NuGet is a package manager for the .NET ecosystem and is the primary way developers discover and acquire .NET open-source libraries.</span></span> <span data-ttu-id="3463e-105">[NuGet.org](https://www.nuget.org/), bezplatná služba poskytovaná společností Microsoft pro hostování balíčků NuGet, je primárním hostitelem pro veřejné balíčky NuGet, ale můžete publikovat na vlastních službách NuGet, jako jsou [MyGet](https://www.myget.org/) a [Azure Artifacts](https://azure.microsoft.com/services/devops/artifacts/).</span><span class="sxs-lookup"><span data-stu-id="3463e-105">[NuGet.org](https://www.nuget.org/), a free service provided by Microsoft for hosting NuGet packages, is the primary host for public NuGet packages, but you can publish to custom NuGet services like [MyGet](https://www.myget.org/) and [Azure Artifacts](https://azure.microsoft.com/services/devops/artifacts/).</span></span>

<span data-ttu-id="3463e-106">![NuGet](./media/nuget/nuget-logo.png "NuGet")</span><span class="sxs-lookup"><span data-stu-id="3463e-106">![NuGet](./media/nuget/nuget-logo.png "NuGet")</span></span>

## <a name="create-a-nuget-package"></a><span data-ttu-id="3463e-107">Vytvoření balíčku NuGet</span><span class="sxs-lookup"><span data-stu-id="3463e-107">Create a NuGet package</span></span>

<span data-ttu-id="3463e-108">Balíček NuGet`*.nupkg`( ) je soubor ZIP, který obsahuje sestavení rozhraní .NET a přidružená metadata.</span><span class="sxs-lookup"><span data-stu-id="3463e-108">A NuGet package (`*.nupkg`) is a zip file that contains .NET assemblies and associated metadata.</span></span>

<span data-ttu-id="3463e-109">Existují dva hlavní způsoby, jak vytvořit balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="3463e-109">There are two main ways to create a NuGet package.</span></span> <span data-ttu-id="3463e-110">Novější a doporučený způsob je vytvořit balíček z projektu ve stylu sady SDK (soubor projektu, jehož obsah začíná `<Project Sdk="Microsoft.NET.Sdk">`).</span><span class="sxs-lookup"><span data-stu-id="3463e-110">The newer and recommended way is to create a package from a SDK-style project (project file whose content starts with `<Project Sdk="Microsoft.NET.Sdk">`).</span></span> <span data-ttu-id="3463e-111">Sestavení a cíle jsou automaticky přidány do balíčku a zbývající metadata je přidán a soubor MSBuild, jako je název balíčku a číslo verze.</span><span class="sxs-lookup"><span data-stu-id="3463e-111">Assemblies and targets are automatically added to the package and remaining metadata is added to the MSBuild file, like package name and version number.</span></span> <span data-ttu-id="3463e-112">Kompilace s [`dotnet pack`](../../core/tools/dotnet-pack.md) příkazem výstupy souboru `*.nupkg` namísto sestavení.</span><span class="sxs-lookup"><span data-stu-id="3463e-112">Compiling with the [`dotnet pack`](../../core/tools/dotnet-pack.md) command outputs a `*.nupkg` file instead of assemblies.</span></span>

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

<span data-ttu-id="3463e-113">Starší způsob vytvoření balíčku NuGet je `*.nuspec` se `nuget.exe` souborem a nástrojem příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="3463e-113">The older way of creating a NuGet package is with a `*.nuspec` file and the `nuget.exe` command-line tool.</span></span> <span data-ttu-id="3463e-114">Soubor nuspec poskytuje skvělou kontrolu, ale musíte pečlivě určit, jaké sestavení a cíle zahrnout do konečného balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="3463e-114">A nuspec file gives you great control but you must carefully specify what assemblies and targets to include in the final NuGet package.</span></span> <span data-ttu-id="3463e-115">Je snadné udělat chybu nebo pro někoho, kdo zapomene aktualizovat nuspec při provádění změn.</span><span class="sxs-lookup"><span data-stu-id="3463e-115">It's easy to make a mistake or for someone to forget to update the nuspec when making changes.</span></span> <span data-ttu-id="3463e-116">Výhodou nuspec je můžete použít vytvořit Balíčky NuGet pro architektury, které ještě nepodporují soubor projektu ve stylu SDK.</span><span class="sxs-lookup"><span data-stu-id="3463e-116">The advantage of a nuspec is you can use it create NuGet packages for frameworks that don't yet support an SDK-style project file.</span></span>

<span data-ttu-id="3463e-117">✔️ zvažte použití souboru projektu ve stylu sady SDK k vytvoření balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="3463e-117">✔️ CONSIDER using an SDK-style project file to create the NuGet package.</span></span>

## <a name="package-dependencies"></a><span data-ttu-id="3463e-118">Závislosti balíčků</span><span class="sxs-lookup"><span data-stu-id="3463e-118">Package dependencies</span></span>

<span data-ttu-id="3463e-119">NuGet balíček závislosti jsou podrobně popsány v článku [závislosti.](./dependencies.md)</span><span class="sxs-lookup"><span data-stu-id="3463e-119">NuGet package dependencies are covered in detail in the [Dependencies](./dependencies.md) article.</span></span>

## <a name="important-nuget-package-metadata"></a><span data-ttu-id="3463e-120">Důležitá metadata balíčku NuGet</span><span class="sxs-lookup"><span data-stu-id="3463e-120">Important NuGet package metadata</span></span>

<span data-ttu-id="3463e-121">Balíček NuGet podporuje mnoho [vlastností metadat](/nuget/reference/nuspec).</span><span class="sxs-lookup"><span data-stu-id="3463e-121">A NuGet package supports many [metadata properties](/nuget/reference/nuspec).</span></span> <span data-ttu-id="3463e-122">Následující tabulka obsahuje základní metadata, která by měl každý balíček v NuGet.org poskytnout:</span><span class="sxs-lookup"><span data-stu-id="3463e-122">The following table contains the core metadata that every package on NuGet.org should provide:</span></span>

| <span data-ttu-id="3463e-123">Název vlastnosti MSBuild</span><span class="sxs-lookup"><span data-stu-id="3463e-123">MSBuild Property name</span></span>              | <span data-ttu-id="3463e-124">Název Nuspec</span><span class="sxs-lookup"><span data-stu-id="3463e-124">Nuspec name</span></span>              | <span data-ttu-id="3463e-125">Popis</span><span class="sxs-lookup"><span data-stu-id="3463e-125">Description</span></span>  |
| ---------------------------------- | ------------------------ | ------------ |
| `PackageId`                        | `id`                       | <span data-ttu-id="3463e-126">Identifikátor balíčku.</span><span class="sxs-lookup"><span data-stu-id="3463e-126">The package identifier.</span></span> <span data-ttu-id="3463e-127">Předponu z identifikátoru lze rezervovat, pokud splňuje [kritéria](/nuget/reference/id-prefix-reservation).</span><span class="sxs-lookup"><span data-stu-id="3463e-127">A prefix from the identifier can be reserved if it meets the [criteria](/nuget/reference/id-prefix-reservation).</span></span> |
| `PackageVersion`                   | `version`                  | <span data-ttu-id="3463e-128">NuGet verze balíčku.</span><span class="sxs-lookup"><span data-stu-id="3463e-128">NuGet package version.</span></span> <span data-ttu-id="3463e-129">Další informace naleznete v tématu [NuGet verze balíčku](./versioning.md#nuget-package-version).</span><span class="sxs-lookup"><span data-stu-id="3463e-129">For more information, see [NuGet package version](./versioning.md#nuget-package-version).</span></span>             |
| `Title`                            | `title`                    | <span data-ttu-id="3463e-130">Lidský název balíčku.</span><span class="sxs-lookup"><span data-stu-id="3463e-130">A human-friendly title of the package.</span></span> <span data-ttu-id="3463e-131">Je výchozí na `PackageId`.</span><span class="sxs-lookup"><span data-stu-id="3463e-131">It defaults to the `PackageId`.</span></span>             |
| `Description`                      | `description`              | <span data-ttu-id="3463e-132">Dlouhý popis balíčku zobrazeného v ui.</span><span class="sxs-lookup"><span data-stu-id="3463e-132">A long description of the package displayed in UI.</span></span>             |
| `Authors`                          | `authors`                  | <span data-ttu-id="3463e-133">Seznam autorů balíčků oddělených čárkami, který odpovídá názvům profilů na nuget.org.</span><span class="sxs-lookup"><span data-stu-id="3463e-133">A comma-separated list of package authors, matching the profile names on nuget.org.</span></span>             |
| `PackageTags`                      | `tags`                     | <span data-ttu-id="3463e-134">Mezera oddělený seznam značek a klíčových slov, které popisují balíček.</span><span class="sxs-lookup"><span data-stu-id="3463e-134">A space-delimited list of tags and keywords that describe the package.</span></span> <span data-ttu-id="3463e-135">Značky se používají při hledání balíčků.</span><span class="sxs-lookup"><span data-stu-id="3463e-135">Tags are used when searching for packages.</span></span>             |
| `PackageIconUrl`                   | `iconUrl`                  | <span data-ttu-id="3463e-136">Adresa URL obrázku, který má být používán jako ikona balíčku.</span><span class="sxs-lookup"><span data-stu-id="3463e-136">A URL for an image to use as the icon for the package.</span></span> <span data-ttu-id="3463e-137">Adresa URL by měla být HTTPS a obrázek by měl být 64x64 a měl by mít průhledné pozadí.</span><span class="sxs-lookup"><span data-stu-id="3463e-137">URL should be HTTPS and the image should be 64x64 and have a transparent background.</span></span>             |
| `PackageProjectUrl`                | `projectUrl`               | <span data-ttu-id="3463e-138">Adresa URL domovské stránky projektu nebo zdrojového úložiště.</span><span class="sxs-lookup"><span data-stu-id="3463e-138">A URL for the project homepage or source repository.</span></span>             |
| `PackageLicenseExpression`         | `license`                  | <span data-ttu-id="3463e-139">[Identifikátor SPDX](https://spdx.org/licenses/)licence projektu .</span><span class="sxs-lookup"><span data-stu-id="3463e-139">The project license's [SPDX identifier](https://spdx.org/licenses/).</span></span> <span data-ttu-id="3463e-140">Identifikátor mohou používat pouze licence schválené OSI a FSF.</span><span class="sxs-lookup"><span data-stu-id="3463e-140">Only OSI and FSF approved licenses can use an identifier.</span></span> <span data-ttu-id="3463e-141">Ostatní licence by `PackageLicenseFile`měly používat .</span><span class="sxs-lookup"><span data-stu-id="3463e-141">Other licenses should use `PackageLicenseFile`.</span></span> <span data-ttu-id="3463e-142">Přečtěte si další informace o [ `license` metadatech](/nuget/reference/nuspec#license).</span><span class="sxs-lookup"><span data-stu-id="3463e-142">Read more about [`license` metadata](/nuget/reference/nuspec#license).</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="3463e-143">Projekt bez licence výchozí [výhradní autorská práva](https://choosealicense.com/no-permission/), takže je právně nemožné pro ostatní lidi k použití.</span><span class="sxs-lookup"><span data-stu-id="3463e-143">A project without a license defaults to [exclusive copyright](https://choosealicense.com/no-permission/), making it legally impossible for other people to use.</span></span>

<span data-ttu-id="3463e-144">✔️ zvažte výběr názvu balíčku NuGet s předponou, která splňuje [kritéria](/nuget/reference/id-prefix-reservation)rezervace předpony NuGet .</span><span class="sxs-lookup"><span data-stu-id="3463e-144">✔️ CONSIDER choosing a NuGet package name with a prefix that meets NuGet's prefix reservation [criteria](/nuget/reference/id-prefix-reservation).</span></span>

<span data-ttu-id="3463e-145">✔️ do použít HTTPS href na ikonu balíčku.</span><span class="sxs-lookup"><span data-stu-id="3463e-145">✔️ DO use an HTTPS href to your package icon.</span></span>

> <span data-ttu-id="3463e-146">Weby, jako je NuGet.org spuštěna s povoleným protokolem HTTPS a zobrazení obrázku, který není https, vytvoří upozornění na smíšený obsah.</span><span class="sxs-lookup"><span data-stu-id="3463e-146">Sites like NuGet.org run with HTTPS enabled and displaying a non-HTTPS image will create a mixed content warning.</span></span>

<span data-ttu-id="3463e-147">✔️ do použít obrázek ikony balíčku, který je 64x64 a má průhledné pozadí pro nejlepší výsledky zobrazení.</span><span class="sxs-lookup"><span data-stu-id="3463e-147">✔️ DO use a package icon image that is 64x64 and has a transparent background for best viewing results.</span></span>

<span data-ttu-id="3463e-148">✔️ zvažte nastavení [zdrojového odkazu](./sourcelink.md) pro přidání metadat správy zdrojového kódu do sestavení a balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="3463e-148">✔️ CONSIDER setting up [Source Link](./sourcelink.md) to add source control metadata to your assemblies and NuGet package.</span></span>

> <span data-ttu-id="3463e-149">Zdrojový odkaz `RepositoryUrl` automaticky `RepositoryType` přidá a metadata nuget balíčku.</span><span class="sxs-lookup"><span data-stu-id="3463e-149">Source Link automatically adds `RepositoryUrl` and `RepositoryType` metadata to the NuGet package.</span></span> <span data-ttu-id="3463e-150">Zdrojový odkaz také přidává informace o přesném zdrojovém kódu, ze kterého byl balíček vytvořen.</span><span class="sxs-lookup"><span data-stu-id="3463e-150">Source Link also adds information about the exact source code the package was built from.</span></span> <span data-ttu-id="3463e-151">Například balíček vytvořený z úložiště Git bude mít hash potvrzení přidánjako metadata.</span><span class="sxs-lookup"><span data-stu-id="3463e-151">For example, a package created from a Git repository will have the commit hash added as metadata.</span></span>

## <a name="pre-release-packages"></a><span data-ttu-id="3463e-152">Předběžné verze balíčků</span><span class="sxs-lookup"><span data-stu-id="3463e-152">Pre-release packages</span></span>

<span data-ttu-id="3463e-153">Balíčky NuGet s příponou verze jsou považovány za [předběžnou verzi](/nuget/create-packages/prerelease-packages).</span><span class="sxs-lookup"><span data-stu-id="3463e-153">NuGet packages with a version suffix are considered [pre-release](/nuget/create-packages/prerelease-packages).</span></span> <span data-ttu-id="3463e-154">Ve výchozím nastavení uživatelské rozhraní NuGet Package Manager zobrazuje stabilní verze, pokud se uživatel nepřihlásí k předběžným verzím balíčků, takže předběžné verze balíčků jsou ideální pro testování uživatelů s omezenýmpřístupem.</span><span class="sxs-lookup"><span data-stu-id="3463e-154">By default, the NuGet Package Manager UI shows stable releases unless a user opts-in to pre-release packages, making pre-release packages ideal for limited user testing.</span></span>

```xml
<PackageVersion>1.0.1-beta1</PackageVersion>
```

> [!NOTE]
> <span data-ttu-id="3463e-155">Stabilní balíček nemůže záviset na předběžné verzi balíčku.</span><span class="sxs-lookup"><span data-stu-id="3463e-155">A stable package cannot depend on a pre-release package.</span></span> <span data-ttu-id="3463e-156">Musíte buď vytvořit svůj vlastní balíček pre-release, nebo závisí na starší stabilní verzi.</span><span class="sxs-lookup"><span data-stu-id="3463e-156">You must either make your own package pre-release or depend on an older stable version.</span></span>

<span data-ttu-id="3463e-157">![Závislost balíčku před vydáním nuget](./media/nuget/nuget-prerelease-package.png "Závislost balíčku před vydáním nuget")</span><span class="sxs-lookup"><span data-stu-id="3463e-157">![NuGet pre-release package dependency](./media/nuget/nuget-prerelease-package.png "NuGet pre-release package dependency")</span></span>

<span data-ttu-id="3463e-158">✔️ do publikovat předběžný balíček při testování, náhledu nebo experimentování.</span><span class="sxs-lookup"><span data-stu-id="3463e-158">✔️ DO publish a pre-release package when testing, previewing, or experimenting.</span></span>

<span data-ttu-id="3463e-159">✔️ do publikovat stabilní balíček, když jeho připraven, takže ostatní stabilní balíčky mohou odkazovat.</span><span class="sxs-lookup"><span data-stu-id="3463e-159">✔️ DO publish a stable package when its ready so other stable packages can reference it.</span></span>

## <a name="symbol-packages"></a><span data-ttu-id="3463e-160">Balíčky symbolů</span><span class="sxs-lookup"><span data-stu-id="3463e-160">Symbol packages</span></span>

<span data-ttu-id="3463e-161">Soubory symbolů (`*.pdb`) jsou vytvářeny kompilátorem .NET vedle sestavení.</span><span class="sxs-lookup"><span data-stu-id="3463e-161">Symbol files (`*.pdb`) are produced by the .NET compiler alongside assemblies.</span></span> <span data-ttu-id="3463e-162">Soubory symbolů mapují umístění spuštění na původní zdrojový kód, takže můžete krokovat zdrojový kód při spuštění pomocí ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="3463e-162">Symbol files map execution locations to the original source code so you can step through source code as it is running using a debugger.</span></span> <span data-ttu-id="3463e-163">NuGet podporuje [generování samostatného`*.snupkg`balíčku symbolů ( )](/nuget/create-packages/symbol-packages-snupkg) obsahujícísoubory symbolů vedle hlavního balíčku obsahujícího sestavení .NET.</span><span class="sxs-lookup"><span data-stu-id="3463e-163">NuGet supports [generating a separate symbol package (`*.snupkg`)](/nuget/create-packages/symbol-packages-snupkg) containing symbol files alongside the main package containing .NET assemblies.</span></span> <span data-ttu-id="3463e-164">Myšlenka symbolbalíčky je, že jsou hostovány na serveru symbolů a jsou staženy pouze nástrojem, jako je Visual Studio na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="3463e-164">The idea of symbol packages is they're hosted on a symbol server and are only downloaded by a tool like Visual Studio on demand.</span></span>

<span data-ttu-id="3463e-165">NuGet.org hostí vlastní [úložiště serverů symbolů](/nuget/create-packages/symbol-packages-snupkg#nugetorg-symbol-server).</span><span class="sxs-lookup"><span data-stu-id="3463e-165">NuGet.org hosts its own [symbols server repository](/nuget/create-packages/symbol-packages-snupkg#nugetorg-symbol-server).</span></span> <span data-ttu-id="3463e-166">Vývojáři mohou použít symboly publikované na `https://symbols.nuget.org/download/symbols` serveru symbolů NuGet.org přidáním [zdrojů symbolů v sadě Visual Studio](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger).</span><span class="sxs-lookup"><span data-stu-id="3463e-166">Developers can use the symbols published to the NuGet.org symbol server by adding `https://symbols.nuget.org/download/symbols` to their [symbol sources in Visual Studio](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3463e-167">Server symbolů NuGet.org podporuje pouze nové`*.pdb` [přenosné soubory symbolů](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) ( ) vytvořené projekty ve stylu sady SDK.</span><span class="sxs-lookup"><span data-stu-id="3463e-167">The NuGet.org symbol server only supports the new [portable symbol files](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) (`*.pdb`) created by SDK-style projects.</span></span>
>
> <span data-ttu-id="3463e-168">Chcete-li při ladění knihovny .NET používat NuGet.org server symbolů, musí mít vývojáři visual studio 2017 verze 15.9 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="3463e-168">To use the NuGet.org symbol server when debugging a .NET library, developers must have Visual Studio 2017 version 15.9 or later.</span></span>

<span data-ttu-id="3463e-169">Alternativou k vytvoření balíčku symbolje vkládání souborů symbolů v hlavním balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="3463e-169">An alternative to creating a symbol package is embedding symbol files in the main NuGet package.</span></span> <span data-ttu-id="3463e-170">Hlavní balíček NuGet bude větší, ale vložené soubory symbolů znamená, že vývojáři nemusí konfigurovat NuGet.org server symbolů.</span><span class="sxs-lookup"><span data-stu-id="3463e-170">The main NuGet package will be larger, but the embedded symbol files means developers don't need to configure the NuGet.org symbol server.</span></span> <span data-ttu-id="3463e-171">Pokud vytváříte balíček NuGet pomocí projektu ve stylu sady SDK, můžete `AllowedOutputExtensionsInPackageBuildOutputFolder` vložit soubory symbolů nastavením vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="3463e-171">If you're building your NuGet package using an SDK-style project, then you can embed symbol files by setting the `AllowedOutputExtensionsInPackageBuildOutputFolder` property:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
 <PropertyGroup>
    <!-- Include symbol files (*.pdb) in the built .nupkg -->
    <AllowedOutputExtensionsInPackageBuildOutputFolder>$(AllowedOutputExtensionsInPackageBuildOutputFolder);.pdb</AllowedOutputExtensionsInPackageBuildOutputFolder>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="3463e-172">Nevýhodou vkládání souborů symbolů je, že zvětšují velikost balíčku přibližně o 30 % pro knihovny .NET zkompilované pomocí projektů ve stylu sady SDK.</span><span class="sxs-lookup"><span data-stu-id="3463e-172">The downside of embedding symbol files is that they increase the package size by about 30% for .NET libraries compiled using SDK-style projects.</span></span> <span data-ttu-id="3463e-173">Pokud velikost balíčku je problém, měli byste publikovat symboly v balíčku symbolmísto.</span><span class="sxs-lookup"><span data-stu-id="3463e-173">If package size is a concern, you should publish symbols in a symbol package instead.</span></span>

<span data-ttu-id="3463e-174">✔️ ZVAŽTe publikování symbolů`*.snupkg`jako balíčku symbolů ( ) k NuGet.org</span><span class="sxs-lookup"><span data-stu-id="3463e-174">✔️ CONSIDER publishing symbols as a symbol package (`*.snupkg`) to NuGet.org</span></span>

> <span data-ttu-id="3463e-175">Balíčky`*.snupkg`symbolů ( ) poskytují vývojářům dobré prostředí ladění na vyžádání bez nadýmání velikosti hlavního balíčku a ovlivňující výkon obnovení pro ty, kteří nemají v úmyslu ladit balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="3463e-175">Symbol packages (`*.snupkg`) provide developers a good on-demand debugging experience without bloating the main package size and impacting restore performance for those who don't intend to debug the NuGet package.</span></span>
>
> <span data-ttu-id="3463e-176">Upozornění je, že uživatelé mohou potřebovat najít a nakonfigurovat server symbolů NuGet v jejich IDE (jako jednorázové nastavení) získat soubory symbolů.</span><span class="sxs-lookup"><span data-stu-id="3463e-176">The caveat is that users may need to find and configure the NuGet symbol server in their IDE (as a one-time setup) to get symbol files.</span></span> <span data-ttu-id="3463e-177">Visual Studio 2019 verze 16.1 přidalo symbolový server NuGet.org do seznamu výchozích serverů symbolů.</span><span class="sxs-lookup"><span data-stu-id="3463e-177">Visual Studio 2019 version 16.1 added NuGet.org's symbol server to the list of default symbol servers.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="3463e-178">[Předchozí](strong-naming.md)
>[další](dependencies.md)</span><span class="sxs-lookup"><span data-stu-id="3463e-178">[Previous](strong-naming.md)
[Next](dependencies.md)</span></span>
