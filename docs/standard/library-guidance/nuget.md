---
title: Knihovny a rozhraní .NET NuGet
description: Doporučené osvědčené postupy pro vytváření balíčků nuget pro knihovny .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 479d1786c232ef1f843877169954e847453681c9
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185616"
---
# <a name="nuget"></a><span data-ttu-id="f77e9-103">NuGet</span><span class="sxs-lookup"><span data-stu-id="f77e9-103">NuGet</span></span>

<span data-ttu-id="f77e9-104">NuGet je Správce balíčků pro .NET ekosystému a vývojáři hlavní způsob, jak vyhledat a získat open source knihoven .NET.</span><span class="sxs-lookup"><span data-stu-id="f77e9-104">NuGet is a package manager for the .NET ecosystem and is the primary way developers discover and acquire .NET open-source libraries.</span></span> <span data-ttu-id="f77e9-105">[NuGet.org](https://www.nuget.org/), je bezplatná služba poskytovaného společností Microsoft pro balíčky NuGet hostují primární hostitele pro veřejné balíčky NuGet, ale můžete publikovat vlastní služeb NuGet, třeba [MyGet](https://www.myget.org/) a [artefakty Azure ](https://azure.microsoft.com/services/devops/artifacts/).</span><span class="sxs-lookup"><span data-stu-id="f77e9-105">[NuGet.org](https://www.nuget.org/), a free service provided by Microsoft for hosting NuGet packages, is the primary host for public NuGet packages, but you can publish to custom NuGet services like [MyGet](https://www.myget.org/) and [Azure Artifacts](https://azure.microsoft.com/services/devops/artifacts/).</span></span>

<span data-ttu-id="f77e9-106">![NuGet](./media/nuget/nuget-logo.png "NuGet")</span><span class="sxs-lookup"><span data-stu-id="f77e9-106">![NuGet](./media/nuget/nuget-logo.png "NuGet")</span></span>

## <a name="create-a-nuget-package"></a><span data-ttu-id="f77e9-107">Vytvoří balíček NuGet</span><span class="sxs-lookup"><span data-stu-id="f77e9-107">Create a NuGet package</span></span>

<span data-ttu-id="f77e9-108">Balíček NuGet (`*.nupkg`) je soubor zip, který obsahuje sestavení .NET a přidružená metadata.</span><span class="sxs-lookup"><span data-stu-id="f77e9-108">A NuGet package (`*.nupkg`) is a zip file that contains .NET assemblies and associated metadata.</span></span>

<span data-ttu-id="f77e9-109">Existují dva hlavní způsoby, jak vytvořit balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="f77e9-109">There are two main ways to create a NuGet package.</span></span> <span data-ttu-id="f77e9-110">Novější a doporučený způsob je pro vytvoření balíčku sady SDK – vizuální styl projektu (soubor projektu, jehož obsah začíná `<Project Sdk="Microsoft.NET.Sdk">`).</span><span class="sxs-lookup"><span data-stu-id="f77e9-110">The newer and recommended way is to create a package from a SDK-style project (project file whose content starts with `<Project Sdk="Microsoft.NET.Sdk">`).</span></span> <span data-ttu-id="f77e9-111">Sestavení a cíle jsou automaticky přidány do balíčku a zbývající metadat se přidá do souboru MSBuild, jako je číslo název a verzi balíčku.</span><span class="sxs-lookup"><span data-stu-id="f77e9-111">Assemblies and targets are automatically added to the package and remaining metadata is added to the MSBuild file, like package name and version number.</span></span> <span data-ttu-id="f77e9-112">Kompilace s [ `dotnet pack` ](../../core/tools/dotnet-pack.md) příkaz výstupy `*.nupkg` souboru místo sestavení.</span><span class="sxs-lookup"><span data-stu-id="f77e9-112">Compiling with the [`dotnet pack`](../../core/tools/dotnet-pack.md) command outputs a `*.nupkg` file instead of assemblies.</span></span>

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

<span data-ttu-id="f77e9-113">Starší způsob vytváření balíčku NuGet se `*.nuspec` souboru a `nuget.exe` nástroj příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="f77e9-113">The older way of creating a NuGet package is with a `*.nuspec` file and the `nuget.exe` command-line tool.</span></span> <span data-ttu-id="f77e9-114">Soubor nuspec získáte skvělou kontrolu, ale musí pečlivě určit, jaké sestavení a cíle, které mají být zahrnuty do koncového balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="f77e9-114">A nuspec file gives you great control but you must carefully specify what assemblies and targets to include in the final NuGet package.</span></span> <span data-ttu-id="f77e9-115">Je snadné vytvořit chybu nebo pro uživatele nezapomeňte aktualizovat soubor nuspec při provádění změn.</span><span class="sxs-lookup"><span data-stu-id="f77e9-115">It's easy to make a mistake or for someone to forget to update the nuspec when making changes.</span></span> <span data-ttu-id="f77e9-116">Výhodou rámci souboru nuspec je můžete vytvořit balíčky NuGet pro rozhraní, které se zatím nepodporují souboru SDK – vizuální styl projektu.</span><span class="sxs-lookup"><span data-stu-id="f77e9-116">The advantage of a nuspec is you can use it create NuGet packages for frameworks that don't yet support an SDK-style project file.</span></span>

<span data-ttu-id="f77e9-117">**✔️ ZVAŽTE** pomocí souboru SDK – vizuální styl projektu k vytvoření balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="f77e9-117">**✔️ CONSIDER** using an SDK-style project file to create the NuGet package.</span></span>

<span data-ttu-id="f77e9-118">**✔️ ZVAŽTE** nastavení SourceLink přidat metadata ovládací prvek zdroje k sestavení a balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="f77e9-118">**✔️ CONSIDER** setting up SourceLink to add source control metadata to your assemblies and NuGet package.</span></span>

## <a name="package-dependencies"></a><span data-ttu-id="f77e9-119">Závislosti balíčků</span><span class="sxs-lookup"><span data-stu-id="f77e9-119">Package dependencies</span></span>

<span data-ttu-id="f77e9-120">Závislosti balíčků NuGet je podrobně popsána v [závislosti](./dependencies.md) článku.</span><span class="sxs-lookup"><span data-stu-id="f77e9-120">NuGet package dependencies are covered in detail in the [Dependencies](./dependencies.md) article.</span></span>

## <a name="important-nuget-package-metadata"></a><span data-ttu-id="f77e9-121">Důležitá metadata balíčku NuGet</span><span class="sxs-lookup"><span data-stu-id="f77e9-121">Important NuGet package metadata</span></span>

<span data-ttu-id="f77e9-122">Balíček NuGet podporuje mnoho [vlastnosti metadat](/nuget/reference/nuspec).</span><span class="sxs-lookup"><span data-stu-id="f77e9-122">A NuGet package supports many [metadata properties](/nuget/reference/nuspec).</span></span> <span data-ttu-id="f77e9-123">Následující tabulka obsahuje základní metadata, která by měla poskytnout každý projekt open source:</span><span class="sxs-lookup"><span data-stu-id="f77e9-123">The following table contains the core metadata that every open-source project should provide:</span></span>

| <span data-ttu-id="f77e9-124">Název vlastnosti nástroje MSBuild</span><span class="sxs-lookup"><span data-stu-id="f77e9-124">MSBuild Property name</span></span>              | <span data-ttu-id="f77e9-125">Název souboru Nuspec</span><span class="sxs-lookup"><span data-stu-id="f77e9-125">Nuspec name</span></span>              | <span data-ttu-id="f77e9-126">Popis</span><span class="sxs-lookup"><span data-stu-id="f77e9-126">Description</span></span>  |
| ---------------------------------- | ------------------------ | ------------ |
| `PackageId`                        | `id`                       | <span data-ttu-id="f77e9-127">Identifikátor balíčku.</span><span class="sxs-lookup"><span data-stu-id="f77e9-127">The package identifier.</span></span> <span data-ttu-id="f77e9-128">Je možné vyhradit předpony z identifikátoru, pokud splňuje [kritéria](/nuget/reference/id-prefix-reservation).</span><span class="sxs-lookup"><span data-stu-id="f77e9-128">A prefix from the identifier can be reserved if it meets the [criteria](/nuget/reference/id-prefix-reservation).</span></span> |
| `PackageVersion`                   | `version`                  | <span data-ttu-id="f77e9-129">Verze balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="f77e9-129">NuGet package version.</span></span> <span data-ttu-id="f77e9-130">Další informace najdete v tématu [verze balíčku NuGet](./versioning.md#nuget-package-version).</span><span class="sxs-lookup"><span data-stu-id="f77e9-130">For more information, see [NuGet package version](./versioning.md#nuget-package-version).</span></span>             |
| `Title`                            | `title`                    | <span data-ttu-id="f77e9-131">Lidské popisný název balíčku.</span><span class="sxs-lookup"><span data-stu-id="f77e9-131">A human-friendly title of the package.</span></span> <span data-ttu-id="f77e9-132">Výchozí hodnota `PackageId`.</span><span class="sxs-lookup"><span data-stu-id="f77e9-132">It defaults to the `PackageId`.</span></span>             |
| `Description`                      | `description`              | <span data-ttu-id="f77e9-133">Dlouhý popis balíčku zobrazeného v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f77e9-133">A long description of the package displayed in UI.</span></span>             |
| `Authors`                          | `authors`                  | <span data-ttu-id="f77e9-134">Čárkou oddělený seznam autorů balíčků, odpovídající názvy profilů na nuget.org.</span><span class="sxs-lookup"><span data-stu-id="f77e9-134">A comma-separated list of package authors, matching the profile names on nuget.org.</span></span>             |
| `PackageTags`                      | `tags`                     | <span data-ttu-id="f77e9-135">Mezerami oddělený seznam značek a klíčových slov, které popisují balíček.</span><span class="sxs-lookup"><span data-stu-id="f77e9-135">A space-delimited list of tags and keywords that describe the package.</span></span> <span data-ttu-id="f77e9-136">Značky se používají při vyhledávání balíčků.</span><span class="sxs-lookup"><span data-stu-id="f77e9-136">Tags are used when searching for packages.</span></span>             |
| `PackageIconUrl`                   | `iconUrl`                  | <span data-ttu-id="f77e9-137">Adresa URL obrázku má použít jako ikona pro balíček.</span><span class="sxs-lookup"><span data-stu-id="f77e9-137">A URL for an image to use as the icon for the package.</span></span> <span data-ttu-id="f77e9-138">Adresa URL by měla být HTTPS a bitové kopie by měl být 64 x 64 a průhledné pozadí.</span><span class="sxs-lookup"><span data-stu-id="f77e9-138">URL should be HTTPS and the image should be 64x64 and have a transparent background.</span></span>             |
| `PackageProjectUrl`                | `projectUrl`               | <span data-ttu-id="f77e9-139">Adresa URL pro projekt domovskou stránku a zdrojového úložiště.</span><span class="sxs-lookup"><span data-stu-id="f77e9-139">A URL for the project homepage or source repository.</span></span>             |
| `PackageLicenseUrl`                | `licenseUrl`               | <span data-ttu-id="f77e9-140">Adresa URL licence projektu.</span><span class="sxs-lookup"><span data-stu-id="f77e9-140">A URL to the project license.</span></span> <span data-ttu-id="f77e9-141">Může být adresa URL `LICENSE` soubor ve správě zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="f77e9-141">Can be the URL to the `LICENSE` file in source control.</span></span>             |

<span data-ttu-id="f77e9-142">**✔️ ZVAŽTE** zvolíte název balíčku NuGet s předponou, který splňuje rezervace předpony Nugetu [kritéria](/nuget/reference/id-prefix-reservation).</span><span class="sxs-lookup"><span data-stu-id="f77e9-142">**✔️ CONSIDER** choosing a NuGet package name with a prefix that meets NuGet's prefix reservation [criteria](/nuget/reference/id-prefix-reservation).</span></span>

<span data-ttu-id="f77e9-143">**✔️ ZVAŽTE** pomocí `LICENSE` soubor ve správě zdrojového kódu, jako `LicenseUrl`.</span><span class="sxs-lookup"><span data-stu-id="f77e9-143">**✔️ CONSIDER** using the `LICENSE` file in source control as the `LicenseUrl`.</span></span> <span data-ttu-id="f77e9-144">Například [LICENSE.md](https://github.com/JamesNK/Newtonsoft.Json/blob/c4af75c8e91ca0d75aa6c335e8c106780c4f7712/LICENSE.md).</span><span class="sxs-lookup"><span data-stu-id="f77e9-144">For example, [LICENSE.md](https://github.com/JamesNK/Newtonsoft.Json/blob/c4af75c8e91ca0d75aa6c335e8c106780c4f7712/LICENSE.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f77e9-145">Projekt bez licence výchozí hodnota je [exkluzivní copyright](https://choosealicense.com/no-permission/), může znemožnit ostatním uživatelům.</span><span class="sxs-lookup"><span data-stu-id="f77e9-145">A project without a license defaults to [exclusive copyright](https://choosealicense.com/no-permission/), making it impossible for other people to use.</span></span>

<span data-ttu-id="f77e9-146">**PROVEĎTE ✔️** použít href HTTPS na ikonu vašeho balíčku.</span><span class="sxs-lookup"><span data-stu-id="f77e9-146">**✔️ DO** use an HTTPS href to your package icon.</span></span>

> <span data-ttu-id="f77e9-147">NuGet.org, jako jsou spuštění pomocí protokolu HTTPS povolené a zobrazování obrázků bez HTTPS vytvoří smíšený obsah upozornění.</span><span class="sxs-lookup"><span data-stu-id="f77e9-147">Sites like NuGet.org run with HTTPS enabled and displaying a non-HTTPS image will create a mixed content warning.</span></span>

<span data-ttu-id="f77e9-148">**PROVEĎTE ✔️** použít bitovou kopii balíčku ikonu, která je 64 x 64 a má průhledné pozadí nejlepšího zobrazení výsledků.</span><span class="sxs-lookup"><span data-stu-id="f77e9-148">**✔️ DO** use a package icon image that is 64x64 and has a transparent background for best viewing results.</span></span>

## <a name="pre-release-packages"></a><span data-ttu-id="f77e9-149">Balíčky v předběžné verzi</span><span class="sxs-lookup"><span data-stu-id="f77e9-149">Pre-release packages</span></span>

<span data-ttu-id="f77e9-150">Balíčky NuGet s příponou verze jsou považovány za [předběžné verze](/nuget/create-packages/prerelease-packages).</span><span class="sxs-lookup"><span data-stu-id="f77e9-150">NuGet packages with a version suffix are considered [pre-release](/nuget/create-packages/prerelease-packages).</span></span> <span data-ttu-id="f77e9-151">Ve výchozím nastavení uživatelského rozhraní Správce balíčků NuGet zobrazuje stabilní verze, pokud uživatel požádá o výslovný souhlas a předběžné verze balíčků, díky tomu balíčky v předběžné verzi ideální pro testování uživatel s omezenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="f77e9-151">By default, the NuGet Package Manager UI shows stable releases unless a user opts-in to pre-release packages, making pre-release packages ideal for limited user testing.</span></span>

```xml
<PackageVersion>1.0.1-beta1</PackageVersion>
```

> [!NOTE]
> <span data-ttu-id="f77e9-152">Stabilní balíček nemohou záviset na předběžnou verzi balíčku.</span><span class="sxs-lookup"><span data-stu-id="f77e9-152">A stable package cannot depend on a pre-release package.</span></span> <span data-ttu-id="f77e9-153">Musíte vytvořit vlastní balíček předběžné verze nebo závisí na starší stabilní verzi.</span><span class="sxs-lookup"><span data-stu-id="f77e9-153">You must either make your own package pre-release or depend on an older stable version.</span></span>

<span data-ttu-id="f77e9-154">![Závislost předběžné verze balíčku NuGet](./media/nuget/nuget-prerelease-package.png "závislost předběžné verze balíčku NuGet")</span><span class="sxs-lookup"><span data-stu-id="f77e9-154">![NuGet pre-release package dependency](./media/nuget/nuget-prerelease-package.png "NuGet pre-release package dependency")</span></span>

<span data-ttu-id="f77e9-155">**PROVEĎTE ✔️** publikovat předběžné verze balíčků při testování, náhled nebo experimentování.</span><span class="sxs-lookup"><span data-stu-id="f77e9-155">**✔️ DO** publish a pre-release package when testing, previewing, or experimenting.</span></span>

<span data-ttu-id="f77e9-156">**PROVEĎTE ✔️** publikovat stabilní balíček, když je připraven tak další stabilní balíčky na něj mohli odkazovat.</span><span class="sxs-lookup"><span data-stu-id="f77e9-156">**✔️ DO** publish a stable package when its ready so other stable packages can reference it.</span></span>

## <a name="symbol-packages"></a><span data-ttu-id="f77e9-157">Balíčky symbolů</span><span class="sxs-lookup"><span data-stu-id="f77e9-157">Symbol packages</span></span>

<span data-ttu-id="f77e9-158">Soubory symbolů (`*.pdb`) jsou produkované kompilátorem .NET spolu s sestavení.</span><span class="sxs-lookup"><span data-stu-id="f77e9-158">Symbol files (`*.pdb`) are produced by the .NET compiler alongside assemblies.</span></span> <span data-ttu-id="f77e9-159">Umístění se symboly mapy provádění soubory do původního zdrojového kódu, můžete procházet zdrojový kód, protože je spuštěn pomocí ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="f77e9-159">Symbol files map execution locations to the original source code so you can step through source code as it is running using a debugger.</span></span> <span data-ttu-id="f77e9-160">Podporuje NuGet [generování balíčku samostatný symbol](/nuget/create-packages/symbol-packages) obsahující soubory symbolů souběžně s hlavní balíček, který obsahuje sestavení .NET.</span><span class="sxs-lookup"><span data-stu-id="f77e9-160">NuGet supports [generating a separate symbol package](/nuget/create-packages/symbol-packages) containing symbol files alongside the main package containing .NET assemblies.</span></span> <span data-ttu-id="f77e9-161">Představu o balíčky symbolů je už hostovaný na serveru symbolů a stáhnou jenom nástroje, jako je Visual Studio na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="f77e9-161">The idea of symbol packages is they're hosted on a symbol server and are only downloaded by a tool like Visual Studio on demand.</span></span>

<span data-ttu-id="f77e9-162">Aktuálně hlavní veřejný hostitel pro symboly – [SymbolSource](http://www.symbolsource.org/) -nepodporuje novou [soubory portable symbolů](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) (`*.pdb`) vytvořené projekty založenými na sadě SDK a symbol balíčky nejsou uloženy užitečné.</span><span class="sxs-lookup"><span data-stu-id="f77e9-162">Currently the main public host for symbols - [SymbolSource](http://www.symbolsource.org/) - doesn't support the new [portable symbol files](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) (`*.pdb`) created by SDK-style projects, and symbol packages aren't useful.</span></span> <span data-ttu-id="f77e9-163">Dokud nedojde k doporučený hostitel pro balíčky symbolů, soubory symbolů může být vložen do hlavního balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="f77e9-163">Until there is a recommended host for symbol packages, symbol files can be embedded in the main NuGet package.</span></span> <span data-ttu-id="f77e9-164">Pokud vytváříte balíček NuGet použití sady SDK – vizuální styl projektu můžete vložit soubory symbolů tak, že nastavíte `AllowedOutputExtensionsInPackageBuildOutputFolder` vlastnost:</span><span class="sxs-lookup"><span data-stu-id="f77e9-164">If you are building your NuGet package using an SDK-style project you can embed symbol files by setting the `AllowedOutputExtensionsInPackageBuildOutputFolder` property:</span></span> 

```xml
<Project Sdk="Microsoft.NET.Sdk">
 <PropertyGroup>
    <!-- Include symbol files (*.pdb) in the built .nupkg -->
    <AllowedOutputExtensionsInPackageBuildOutputFolder>$(AllowedOutputExtensionsInPackageBuildOutputFolder);.pdb</AllowedOutputExtensionsInPackageBuildOutputFolder>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="f77e9-165">**✔️ ZVAŽTE** vložení soubory symbolů do hlavního balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="f77e9-165">**✔️ CONSIDER** embedding symbol files in the main NuGet package.</span></span>

<span data-ttu-id="f77e9-166">**❌ Nepoužívejte** vytváří se balíček symbolů, který obsahuje soubory symbolů.</span><span class="sxs-lookup"><span data-stu-id="f77e9-166">**❌ AVOID** creating a symbols package containing symbol files.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="f77e9-167">[Předchozí](./strong-naming.md)
[další](./dependencies.md)</span><span class="sxs-lookup"><span data-stu-id="f77e9-167">[Previous](./strong-naming.md)
[Next](./dependencies.md)</span></span>
