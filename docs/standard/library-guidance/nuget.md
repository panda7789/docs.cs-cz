---
title: Knihovny a rozhraní .NET NuGet
description: Doporučené osvědčené postupy pro vytváření balíčků nuget pro knihovny .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 845af3b34827e1f284bb52e040f9de09f22baf37
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49087867"
---
# <a name="nuget"></a><span data-ttu-id="fad6d-103">NuGet</span><span class="sxs-lookup"><span data-stu-id="fad6d-103">NuGet</span></span>

<span data-ttu-id="fad6d-104">NuGet je Správce balíčků pro .NET ekosystému a vývojáři hlavní způsob, jak vyhledat a získat open source knihoven .NET.</span><span class="sxs-lookup"><span data-stu-id="fad6d-104">NuGet is a package manager for the .NET eco-system and is the primary way developers discover and acquire .NET open-source libraries.</span></span> <span data-ttu-id="fad6d-105">Primární hostitele pro veřejné balíčky NuGet je NuGet.org, bezplatná služba poskytovaného společností Microsoft pro hostování balíčků NuGet, ale můžete publikovat do vlastní služby NuGet jako MyGet a Azure DevOps.</span><span class="sxs-lookup"><span data-stu-id="fad6d-105">NuGet.org, a free service provided by Microsoft for hosting NuGet packages, is the primary host for public NuGet packages but you can publish to custom NuGet services like MyGet and Azure DevOps.</span></span>

<span data-ttu-id="fad6d-106">![NuGet](./media/nuget/nuget-logo.png "NuGet")</span><span class="sxs-lookup"><span data-stu-id="fad6d-106">![NuGet](./media/nuget/nuget-logo.png "NuGet")</span></span>

## <a name="create-a-nuget-package"></a><span data-ttu-id="fad6d-107">Vytvoří balíček NuGet</span><span class="sxs-lookup"><span data-stu-id="fad6d-107">Create a NuGet package</span></span>

<span data-ttu-id="fad6d-108">Balíček NuGet (`*.nupkg`) je soubor zip, který obsahuje sestavení .NET a přidružená metadata.</span><span class="sxs-lookup"><span data-stu-id="fad6d-108">A NuGet package (`*.nupkg`) is a zip file that contains .NET assemblies and associated metadata.</span></span>

<span data-ttu-id="fad6d-109">Existují dva hlavní způsoby, jak vytvořit balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="fad6d-109">There are two main ways to create a NuGet package.</span></span> <span data-ttu-id="fad6d-110">Novější a doporučený způsob je pro vytvoření balíčku sady SDK – vizuální styl projektu (soubor projektu obsah začíná `<Project Sdk="Microsoft.NET.Sdk">`).</span><span class="sxs-lookup"><span data-stu-id="fad6d-110">The newer and recommended way is to create a package from a SDK-style project (project file the content starts with `<Project Sdk="Microsoft.NET.Sdk">`).</span></span> <span data-ttu-id="fad6d-111">Sestavení a cíle jsou automaticky přidány do balíčku a zbývající metadat se přidá do souboru MSBuild, jako je číslo název a verzi balíčku.</span><span class="sxs-lookup"><span data-stu-id="fad6d-111">Assemblies and targets are automatically added to the package and remaining metadata is added to the MSBuild file, like package name and version number.</span></span> <span data-ttu-id="fad6d-112">Kompilace s [ `dotnet pack` ](../../core/tools/dotnet-pack.md) příkaz výstupy `*.nupkg` souboru místo sestavení.</span><span class="sxs-lookup"><span data-stu-id="fad6d-112">Compiling with the [`dotnet pack`](../../core/tools/dotnet-pack.md) command outputs a `*.nupkg` file instead of assemblies.</span></span>

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

<span data-ttu-id="fad6d-113">Starší způsob vytváření balíčku NuGet se `*.nuspec` souboru a `nuget.exe` nástroj příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="fad6d-113">The older way of creating a NuGet package is with a `*.nuspec` file and the `nuget.exe` command-line tool.</span></span> <span data-ttu-id="fad6d-114">Soubor nuspec získáte skvělou kontrolu, ale musí pečlivě určit, jaké sestavení a cíle, které mají být zahrnuty do koncového balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="fad6d-114">A nuspec file gives you great control but you must carefully specify what assemblies and targets to include in the final NuGet package.</span></span> <span data-ttu-id="fad6d-115">Je snadné vytvořit chybu nebo pro uživatele nezapomeňte aktualizovat soubor nuspec při provádění změn.</span><span class="sxs-lookup"><span data-stu-id="fad6d-115">It's easy to make a mistake or for someone to forget to update the nuspec when making changes.</span></span> <span data-ttu-id="fad6d-116">Výhodou rámci souboru nuspec je můžete vytvořit balíčky NuGet pro rozhraní, které se zatím nepodporují souboru SDK – vizuální styl projektu.</span><span class="sxs-lookup"><span data-stu-id="fad6d-116">The advantage of a nuspec is you can use it create NuGet packages for frameworks that don't yet support an SDK-style project file.</span></span>

<span data-ttu-id="fad6d-117">**✔️ ZVAŽTE** pomocí souboru SDK – vizuální styl projektu k vytvoření balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="fad6d-117">**✔️ CONSIDER** using an SDK-style project file to create the NuGet package.</span></span>

<span data-ttu-id="fad6d-118">**✔️ ZVAŽTE** nastavení SourceLink přidat metadata ovládací prvek zdroje k sestavení a balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="fad6d-118">**✔️ CONSIDER** setting up SourceLink to add source control metadata to your assemblies and NuGet package.</span></span>

## <a name="package-dependencies"></a><span data-ttu-id="fad6d-119">Závislosti balíčků</span><span class="sxs-lookup"><span data-stu-id="fad6d-119">Package dependencies</span></span>

<span data-ttu-id="fad6d-120">Závislosti balíčků NuGet je podrobně popsána v [závislosti](./dependencies.md) článku.</span><span class="sxs-lookup"><span data-stu-id="fad6d-120">NuGet package dependencies are covered in detail in the [Dependencies](./dependencies.md) article.</span></span>

## <a name="important-nuget-package-metadata"></a><span data-ttu-id="fad6d-121">Důležitá metadata balíčku NuGet</span><span class="sxs-lookup"><span data-stu-id="fad6d-121">Important NuGet package metadata</span></span>

<span data-ttu-id="fad6d-122">Balíček NuGet podporuje mnoho [vlastnosti metadat](/nuget/reference/nuspec).</span><span class="sxs-lookup"><span data-stu-id="fad6d-122">A NuGet package supports many [metadata properties](/nuget/reference/nuspec).</span></span> <span data-ttu-id="fad6d-123">Následující tabulka obsahuje základní metadata, která by měla poskytnout každý projekt open source:</span><span class="sxs-lookup"><span data-stu-id="fad6d-123">The following table contains the core metadata that every open-source project should provide:</span></span>

| <span data-ttu-id="fad6d-124">Název vlastnosti nástroje MSBuild</span><span class="sxs-lookup"><span data-stu-id="fad6d-124">MSBuild Property name</span></span>              | <span data-ttu-id="fad6d-125">Název souboru Nuspec</span><span class="sxs-lookup"><span data-stu-id="fad6d-125">Nuspec name</span></span>              | <span data-ttu-id="fad6d-126">Popis</span><span class="sxs-lookup"><span data-stu-id="fad6d-126">Description</span></span>  |
| ---------------------------------- | ------------------------ | ------------ |
| `PackageId`                        | `id`                       | <span data-ttu-id="fad6d-127">Identifikátor balíčku.</span><span class="sxs-lookup"><span data-stu-id="fad6d-127">The package identifier.</span></span> <span data-ttu-id="fad6d-128">Je možné vyhradit předpony z identifikátoru, pokud splňuje [kritéria](/nuget/reference/id-prefix-reservation).</span><span class="sxs-lookup"><span data-stu-id="fad6d-128">A prefix from the identifier can be reserved if it meets the [criteria](/nuget/reference/id-prefix-reservation).</span></span> |
| `PackageVersion`                   | `version`                  | <span data-ttu-id="fad6d-129">Verze balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="fad6d-129">NuGet package version.</span></span> <span data-ttu-id="fad6d-130">Další informace najdete v tématu [verze balíčku NuGet](./versioning.md#nuget-package-version).</span><span class="sxs-lookup"><span data-stu-id="fad6d-130">For more information, see [NuGet package version](./versioning.md#nuget-package-version).</span></span>             |
| `Title`                            | `title`                    | <span data-ttu-id="fad6d-131">Lidské popisný název balíčku.</span><span class="sxs-lookup"><span data-stu-id="fad6d-131">A human-friendly title of the package.</span></span> <span data-ttu-id="fad6d-132">Výchozí hodnota `PackageId`.</span><span class="sxs-lookup"><span data-stu-id="fad6d-132">It defaults to the `PackageId`.</span></span>             |
| `Description`                      | `description`              | <span data-ttu-id="fad6d-133">Dlouhý popis balíčku zobrazeného v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fad6d-133">A long description of the package displayed in UI.</span></span>             |
| `Authors`                          | `authors`                  | <span data-ttu-id="fad6d-134">Čárkou oddělený seznam autorů balíčků, odpovídající názvy profilů na nuget.org.</span><span class="sxs-lookup"><span data-stu-id="fad6d-134">A comma-separated list of package authors, matching the profile names on nuget.org.</span></span>             |
| `PackageTags`                      | `tags`                     | <span data-ttu-id="fad6d-135">Mezerami oddělený seznam značek a klíčových slov, které popisují balíček.</span><span class="sxs-lookup"><span data-stu-id="fad6d-135">A space-delimited list of tags and keywords that describe the package.</span></span> <span data-ttu-id="fad6d-136">Značky se používají při vyhledávání balíčků.</span><span class="sxs-lookup"><span data-stu-id="fad6d-136">Tags are used when searching for packages.</span></span>             |
| `PackageIconUrl`                   | `iconUrl`                  | <span data-ttu-id="fad6d-137">Adresa URL obrázku má použít jako ikona pro balíček.</span><span class="sxs-lookup"><span data-stu-id="fad6d-137">A URL for an image to use as the icon for the package.</span></span> <span data-ttu-id="fad6d-138">Adresa URL by měla být HTTPS a bitové kopie by měl být 64 x 64 a průhledné pozadí.</span><span class="sxs-lookup"><span data-stu-id="fad6d-138">URL should be HTTPS and the image should be 64x64 and have a transparent background.</span></span>             |
| `PackageProjectUrl`                | `projectUrl`               | <span data-ttu-id="fad6d-139">Adresa URL pro projekt domovskou stránku a zdrojového úložiště.</span><span class="sxs-lookup"><span data-stu-id="fad6d-139">A URL for the project homepage or source repository.</span></span>             |
| `PackageLicenseUrl`                | `licenseUrl`               | <span data-ttu-id="fad6d-140">Adresa URL licence projektu.</span><span class="sxs-lookup"><span data-stu-id="fad6d-140">A URL to the project license.</span></span> <span data-ttu-id="fad6d-141">Může být adresa URL `LICENSE` soubor ve správě zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="fad6d-141">Can be the URL to the `LICENSE` file in source control.</span></span>             |

<span data-ttu-id="fad6d-142">**✔️ ZVAŽTE** zvolíte název balíčku NuGet s předponou, který splňuje rezervace předpony Nugetu [kritéria](/nuget/reference/id-prefix-reservation).</span><span class="sxs-lookup"><span data-stu-id="fad6d-142">**✔️ CONSIDER** choosing a NuGet package name with a prefix that meets NuGet's prefix reservation [criteria](/nuget/reference/id-prefix-reservation).</span></span>

<span data-ttu-id="fad6d-143">**✔️ ZVAŽTE** pomocí `LICENSE` soubor ve správě zdrojového kódu, jako `LicenseUrl`.</span><span class="sxs-lookup"><span data-stu-id="fad6d-143">**✔️ CONSIDER** using the `LICENSE` file in source control as the `LicenseUrl`.</span></span> <span data-ttu-id="fad6d-144">Třeba https://github.com/JamesNK/Newtonsoft.Json/blob/master/LICENSE.md.</span><span class="sxs-lookup"><span data-stu-id="fad6d-144">For example, https://github.com/JamesNK/Newtonsoft.Json/blob/master/LICENSE.md</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fad6d-145">Projekt bez licence výchozí hodnota je [exkluzivní copyright](https://choosealicense.com/no-permission/), může znemožnit ostatním uživatelům.</span><span class="sxs-lookup"><span data-stu-id="fad6d-145">A project without a license defaults to [exclusive copyright](https://choosealicense.com/no-permission/), making it impossible for other people to use.</span></span>

<span data-ttu-id="fad6d-146">**PROVEĎTE ✔️** použít href HTTPS na ikonu vašeho balíčku.</span><span class="sxs-lookup"><span data-stu-id="fad6d-146">**✔️ DO** use an HTTPS href to your package icon.</span></span>

> <span data-ttu-id="fad6d-147">NuGet.org, jako jsou spuštění pomocí protokolu HTTPS povolené a zobrazování obrázků bez HTTPS vytvoří smíšený obsah upozornění.</span><span class="sxs-lookup"><span data-stu-id="fad6d-147">Sites like NuGet.org run with HTTPS enabled and displaying a non-HTTPS image will create a mixed content warning.</span></span>

<span data-ttu-id="fad6d-148">**PROVEĎTE ✔️** použít bitovou kopii balíčku ikonu, která je 64 x 64 a má průhledné pozadí nejlepšího zobrazení výsledků.</span><span class="sxs-lookup"><span data-stu-id="fad6d-148">**✔️ DO** use a package icon image that is 64x64 and has a transparent background for best viewing results.</span></span>

## <a name="pre-release-packages"></a><span data-ttu-id="fad6d-149">Balíčky v předběžné verzi</span><span class="sxs-lookup"><span data-stu-id="fad6d-149">Pre-release packages</span></span>

<span data-ttu-id="fad6d-150">Balíčky NuGet s příponou verze jsou považovány za [předběžné verze](/nuget/create-packages/prerelease-packages).</span><span class="sxs-lookup"><span data-stu-id="fad6d-150">NuGet packages with a version suffix are considered [pre-release](/nuget/create-packages/prerelease-packages).</span></span> <span data-ttu-id="fad6d-151">Ve výchozím nastavení uživatelského rozhraní Správce balíčků NuGet zobrazuje stabilní verze, pokud uživatel požádá o výslovný souhlas a předběžné verze balíčků, díky tomu balíčky v předběžné verzi ideální pro testování uživatel s omezenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="fad6d-151">By default, the NuGet Package Manager UI shows stable releases unless a user opts-in to pre-release packages, making pre-release packages ideal for limited user testing.</span></span>

```xml
<PackageVersion>1.0.1-beta1</PackageVersion>
```

> [!NOTE]
> <span data-ttu-id="fad6d-152">Stabilní balíček nemohou záviset na předběžnou verzi balíčku.</span><span class="sxs-lookup"><span data-stu-id="fad6d-152">A stable package cannot depend on a pre-release package.</span></span> <span data-ttu-id="fad6d-153">Musíte vytvořit vlastní balíček předběžné verze nebo závisí na starší stabilní verzi.</span><span class="sxs-lookup"><span data-stu-id="fad6d-153">You must either make your own package pre-release or depend on an older stable version.</span></span>

<span data-ttu-id="fad6d-154">![Závislost předběžné verze balíčku NuGet](./media/nuget/nuget-prerelease-package.png "závislost předběžné verze balíčku NuGet")</span><span class="sxs-lookup"><span data-stu-id="fad6d-154">![NuGet pre-release package dependency](./media/nuget/nuget-prerelease-package.png "NuGet pre-release package dependency")</span></span>

<span data-ttu-id="fad6d-155">**PROVEĎTE ✔️** publikovat předběžné verze balíčků při testování, náhled nebo experimentování.</span><span class="sxs-lookup"><span data-stu-id="fad6d-155">**✔️ DO** publish a pre-release package when testing, previewing, or experimenting.</span></span>

<span data-ttu-id="fad6d-156">**PROVEĎTE ✔️** publikovat stabilní balíček, když je připraven tak další stabilní balíčky na něj mohli odkazovat.</span><span class="sxs-lookup"><span data-stu-id="fad6d-156">**✔️ DO** publish a stable package when its ready so other stable packages can reference it.</span></span>

## <a name="symbol-packages"></a><span data-ttu-id="fad6d-157">Balíčky symbolů</span><span class="sxs-lookup"><span data-stu-id="fad6d-157">Symbol packages</span></span>

<span data-ttu-id="fad6d-158">Podporuje NuGet [generování balíčku samostatný symbol](/nuget/create-packages/symbol-packages) obsahující ladit soubory PDB souběžně s hlavní balíček, který obsahuje sestavení .NET.</span><span class="sxs-lookup"><span data-stu-id="fad6d-158">NuGet supports [generating a separate symbol package](/nuget/create-packages/symbol-packages) containing debug PDB files alongside the main package containing .NET assemblies.</span></span> <span data-ttu-id="fad6d-159">Představu o balíčky symbolů je už hostovaný na serveru symbolů a stáhnou jenom nástroje, jako je Visual Studio na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="fad6d-159">The idea of symbol packages is they're hosted on a symbol server and are only downloaded by a tool like Visual Studio on demand.</span></span>

<span data-ttu-id="fad6d-160">Aktuálně hlavní veřejný hostitel pro symboly – [SymbolSource](http://www.symbolsource.org/) -nepodporuje souborům portable PDB vytvořené pomocí sady SDK – vizuální styl není užitečné projekty a balíčky symbolů.</span><span class="sxs-lookup"><span data-stu-id="fad6d-160">Currently the main public host for symbols - [SymbolSource](http://www.symbolsource.org/) - doesn't support the portable PDBs created by SDK-style projects and symbol packages aren't useful.</span></span>

<span data-ttu-id="fad6d-161">**✔️ ZVAŽTE** vkládání PDB do hlavního balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="fad6d-161">**✔️ CONSIDER** embedding PDBs in the main NuGet package.</span></span>

<span data-ttu-id="fad6d-162">**❌ Nepoužívejte** vytváří se balíček symbolů, který obsahuje soubory PDB.</span><span class="sxs-lookup"><span data-stu-id="fad6d-162">**❌ AVOID** creating a symbols package containing PDBs.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="fad6d-163">[Předchozí](./strong-naming.md)
[další](./dependencies.md)</span><span class="sxs-lookup"><span data-stu-id="fad6d-163">[Previous](./strong-naming.md)
[Next](./dependencies.md)</span></span>
