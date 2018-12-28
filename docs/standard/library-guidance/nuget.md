---
title: Knihovny a rozhraní .NET NuGet
description: Doporučené osvědčené postupy pro vytváření balíčků nuget pro knihovny .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 4f33c9993d8eef4b18823d5c16f9f51c06afae88
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53614542"
---
# <a name="nuget"></a><span data-ttu-id="98170-103">NuGet</span><span class="sxs-lookup"><span data-stu-id="98170-103">NuGet</span></span>

<span data-ttu-id="98170-104">NuGet je Správce balíčků pro .NET ekosystému a vývojáři hlavní způsob, jak vyhledat a získat open source knihoven .NET.</span><span class="sxs-lookup"><span data-stu-id="98170-104">NuGet is a package manager for the .NET ecosystem and is the primary way developers discover and acquire .NET open-source libraries.</span></span> <span data-ttu-id="98170-105">[NuGet.org](https://www.nuget.org/), je bezplatná služba poskytovaného společností Microsoft pro balíčky NuGet hostují primární hostitele pro veřejné balíčky NuGet, ale můžete publikovat vlastní služeb NuGet, třeba [MyGet](https://www.myget.org/) a [artefakty Azure ](https://azure.microsoft.com/services/devops/artifacts/).</span><span class="sxs-lookup"><span data-stu-id="98170-105">[NuGet.org](https://www.nuget.org/), a free service provided by Microsoft for hosting NuGet packages, is the primary host for public NuGet packages, but you can publish to custom NuGet services like [MyGet](https://www.myget.org/) and [Azure Artifacts](https://azure.microsoft.com/services/devops/artifacts/).</span></span>

<span data-ttu-id="98170-106">![NuGet](./media/nuget/nuget-logo.png "NuGet")</span><span class="sxs-lookup"><span data-stu-id="98170-106">![NuGet](./media/nuget/nuget-logo.png "NuGet")</span></span>

## <a name="create-a-nuget-package"></a><span data-ttu-id="98170-107">Vytvoří balíček NuGet</span><span class="sxs-lookup"><span data-stu-id="98170-107">Create a NuGet package</span></span>

<span data-ttu-id="98170-108">Balíček NuGet (`*.nupkg`) je soubor zip, který obsahuje sestavení .NET a přidružená metadata.</span><span class="sxs-lookup"><span data-stu-id="98170-108">A NuGet package (`*.nupkg`) is a zip file that contains .NET assemblies and associated metadata.</span></span>

<span data-ttu-id="98170-109">Existují dva hlavní způsoby, jak vytvořit balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="98170-109">There are two main ways to create a NuGet package.</span></span> <span data-ttu-id="98170-110">Novější a doporučený způsob je pro vytvoření balíčku sady SDK – vizuální styl projektu (soubor projektu, jehož obsah začíná `<Project Sdk="Microsoft.NET.Sdk">`).</span><span class="sxs-lookup"><span data-stu-id="98170-110">The newer and recommended way is to create a package from a SDK-style project (project file whose content starts with `<Project Sdk="Microsoft.NET.Sdk">`).</span></span> <span data-ttu-id="98170-111">Sestavení a cíle jsou automaticky přidány do balíčku a zbývající metadat se přidá do souboru MSBuild, jako je číslo název a verzi balíčku.</span><span class="sxs-lookup"><span data-stu-id="98170-111">Assemblies and targets are automatically added to the package and remaining metadata is added to the MSBuild file, like package name and version number.</span></span> <span data-ttu-id="98170-112">Kompilace s [ `dotnet pack` ](../../core/tools/dotnet-pack.md) příkaz výstupy `*.nupkg` souboru místo sestavení.</span><span class="sxs-lookup"><span data-stu-id="98170-112">Compiling with the [`dotnet pack`](../../core/tools/dotnet-pack.md) command outputs a `*.nupkg` file instead of assemblies.</span></span>

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

<span data-ttu-id="98170-113">Starší způsob vytváření balíčku NuGet se `*.nuspec` souboru a `nuget.exe` nástroj příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="98170-113">The older way of creating a NuGet package is with a `*.nuspec` file and the `nuget.exe` command-line tool.</span></span> <span data-ttu-id="98170-114">Soubor nuspec získáte skvělou kontrolu, ale musí pečlivě určit, jaké sestavení a cíle, které mají být zahrnuty do koncového balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="98170-114">A nuspec file gives you great control but you must carefully specify what assemblies and targets to include in the final NuGet package.</span></span> <span data-ttu-id="98170-115">Je snadné vytvořit chybu nebo pro uživatele nezapomeňte aktualizovat soubor nuspec při provádění změn.</span><span class="sxs-lookup"><span data-stu-id="98170-115">It's easy to make a mistake or for someone to forget to update the nuspec when making changes.</span></span> <span data-ttu-id="98170-116">Výhodou rámci souboru nuspec je můžete vytvořit balíčky NuGet pro rozhraní, které se zatím nepodporují souboru SDK – vizuální styl projektu.</span><span class="sxs-lookup"><span data-stu-id="98170-116">The advantage of a nuspec is you can use it create NuGet packages for frameworks that don't yet support an SDK-style project file.</span></span>

<span data-ttu-id="98170-117">**✔️ ZVAŽTE** pomocí souboru SDK – vizuální styl projektu k vytvoření balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="98170-117">**✔️ CONSIDER** using an SDK-style project file to create the NuGet package.</span></span>

## <a name="package-dependencies"></a><span data-ttu-id="98170-118">Závislosti balíčků</span><span class="sxs-lookup"><span data-stu-id="98170-118">Package dependencies</span></span>

<span data-ttu-id="98170-119">Závislosti balíčků NuGet je podrobně popsána v [závislosti](./dependencies.md) článku.</span><span class="sxs-lookup"><span data-stu-id="98170-119">NuGet package dependencies are covered in detail in the [Dependencies](./dependencies.md) article.</span></span>

## <a name="important-nuget-package-metadata"></a><span data-ttu-id="98170-120">Důležitá metadata balíčku NuGet</span><span class="sxs-lookup"><span data-stu-id="98170-120">Important NuGet package metadata</span></span>

<span data-ttu-id="98170-121">Balíček NuGet podporuje mnoho [vlastnosti metadat](/nuget/reference/nuspec).</span><span class="sxs-lookup"><span data-stu-id="98170-121">A NuGet package supports many [metadata properties](/nuget/reference/nuspec).</span></span> <span data-ttu-id="98170-122">Následující tabulka obsahuje základní metadata, která by měla poskytnout všech balíčků na NuGet.org:</span><span class="sxs-lookup"><span data-stu-id="98170-122">The following table contains the core metadata that every package on NuGet.org should provide:</span></span>

| <span data-ttu-id="98170-123">Název vlastnosti nástroje MSBuild</span><span class="sxs-lookup"><span data-stu-id="98170-123">MSBuild Property name</span></span>              | <span data-ttu-id="98170-124">Název souboru Nuspec</span><span class="sxs-lookup"><span data-stu-id="98170-124">Nuspec name</span></span>              | <span data-ttu-id="98170-125">Popis</span><span class="sxs-lookup"><span data-stu-id="98170-125">Description</span></span>  |
| ---------------------------------- | ------------------------ | ------------ |
| `PackageId`                        | `id`                       | <span data-ttu-id="98170-126">Identifikátor balíčku.</span><span class="sxs-lookup"><span data-stu-id="98170-126">The package identifier.</span></span> <span data-ttu-id="98170-127">Je možné vyhradit předpony z identifikátoru, pokud splňuje [kritéria](/nuget/reference/id-prefix-reservation).</span><span class="sxs-lookup"><span data-stu-id="98170-127">A prefix from the identifier can be reserved if it meets the [criteria](/nuget/reference/id-prefix-reservation).</span></span> |
| `PackageVersion`                   | `version`                  | <span data-ttu-id="98170-128">Verze balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="98170-128">NuGet package version.</span></span> <span data-ttu-id="98170-129">Další informace najdete v tématu [verze balíčku NuGet](./versioning.md#nuget-package-version).</span><span class="sxs-lookup"><span data-stu-id="98170-129">For more information, see [NuGet package version](./versioning.md#nuget-package-version).</span></span>             |
| `Title`                            | `title`                    | <span data-ttu-id="98170-130">Lidské popisný název balíčku.</span><span class="sxs-lookup"><span data-stu-id="98170-130">A human-friendly title of the package.</span></span> <span data-ttu-id="98170-131">Výchozí hodnota `PackageId`.</span><span class="sxs-lookup"><span data-stu-id="98170-131">It defaults to the `PackageId`.</span></span>             |
| `Description`                      | `description`              | <span data-ttu-id="98170-132">Dlouhý popis balíčku zobrazeného v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="98170-132">A long description of the package displayed in UI.</span></span>             |
| `Authors`                          | `authors`                  | <span data-ttu-id="98170-133">Čárkou oddělený seznam autorů balíčků, odpovídající názvy profilů na nuget.org.</span><span class="sxs-lookup"><span data-stu-id="98170-133">A comma-separated list of package authors, matching the profile names on nuget.org.</span></span>             |
| `PackageTags`                      | `tags`                     | <span data-ttu-id="98170-134">Mezerami oddělený seznam značek a klíčových slov, které popisují balíček.</span><span class="sxs-lookup"><span data-stu-id="98170-134">A space-delimited list of tags and keywords that describe the package.</span></span> <span data-ttu-id="98170-135">Značky se používají při vyhledávání balíčků.</span><span class="sxs-lookup"><span data-stu-id="98170-135">Tags are used when searching for packages.</span></span>             |
| `PackageIconUrl`                   | `iconUrl`                  | <span data-ttu-id="98170-136">Adresa URL obrázku má použít jako ikona pro balíček.</span><span class="sxs-lookup"><span data-stu-id="98170-136">A URL for an image to use as the icon for the package.</span></span> <span data-ttu-id="98170-137">Adresa URL by měla být HTTPS a bitové kopie by měl být 64 x 64 a průhledné pozadí.</span><span class="sxs-lookup"><span data-stu-id="98170-137">URL should be HTTPS and the image should be 64x64 and have a transparent background.</span></span>             |
| `PackageProjectUrl`                | `projectUrl`               | <span data-ttu-id="98170-138">Adresa URL pro projekt domovskou stránku a zdrojového úložiště.</span><span class="sxs-lookup"><span data-stu-id="98170-138">A URL for the project homepage or source repository.</span></span>             |
| `PackageLicenseExpression`         | `license`                  | <span data-ttu-id="98170-139">Licence projektu [SPDX identifikátor](https://spdx.org/licenses/).</span><span class="sxs-lookup"><span data-stu-id="98170-139">The project license's [SPDX identifier](https://spdx.org/licenses/).</span></span> <span data-ttu-id="98170-140">Pouze OSI a FSF schválené licencí můžete použít identifikátor.</span><span class="sxs-lookup"><span data-stu-id="98170-140">Only OSI and FSF approved licenses can use an identifier.</span></span> <span data-ttu-id="98170-141">Licence na ostatní používejte `PackageLicenseFile`.</span><span class="sxs-lookup"><span data-stu-id="98170-141">Other licenses should use `PackageLicenseFile`.</span></span> <span data-ttu-id="98170-142">Další informace o [ `license` metadat](/nuget/reference/nuspec#license).</span><span class="sxs-lookup"><span data-stu-id="98170-142">Read more about [`license` metadata](/nuget/reference/nuspec#license).</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="98170-143">Projekt bez licence výchozí hodnota je [exkluzivní copyright](https://choosealicense.com/no-permission/), může znemožnit právně pro používání jiným lidem.</span><span class="sxs-lookup"><span data-stu-id="98170-143">A project without a license defaults to [exclusive copyright](https://choosealicense.com/no-permission/), making it legally impossible for other people to use.</span></span>

<span data-ttu-id="98170-144">**✔️ ZVAŽTE** zvolíte název balíčku NuGet s předponou, který splňuje rezervace předpony Nugetu [kritéria](/nuget/reference/id-prefix-reservation).</span><span class="sxs-lookup"><span data-stu-id="98170-144">**✔️ CONSIDER** choosing a NuGet package name with a prefix that meets NuGet's prefix reservation [criteria](/nuget/reference/id-prefix-reservation).</span></span>

<span data-ttu-id="98170-145">**PROVEĎTE ✔️** použít href HTTPS na ikonu vašeho balíčku.</span><span class="sxs-lookup"><span data-stu-id="98170-145">**✔️ DO** use an HTTPS href to your package icon.</span></span>

> <span data-ttu-id="98170-146">NuGet.org, jako jsou spuštění pomocí protokolu HTTPS povolené a zobrazování obrázků bez HTTPS vytvoří smíšený obsah upozornění.</span><span class="sxs-lookup"><span data-stu-id="98170-146">Sites like NuGet.org run with HTTPS enabled and displaying a non-HTTPS image will create a mixed content warning.</span></span>

<span data-ttu-id="98170-147">**PROVEĎTE ✔️** použít bitovou kopii balíčku ikonu, která je 64 x 64 a má průhledné pozadí nejlepšího zobrazení výsledků.</span><span class="sxs-lookup"><span data-stu-id="98170-147">**✔️ DO** use a package icon image that is 64x64 and has a transparent background for best viewing results.</span></span>

<span data-ttu-id="98170-148">**✔️ ZVAŽTE** nastavení [SourceLink](./sourcelink.md) přidat metadata ovládací prvek zdroje k sestavení a balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="98170-148">**✔️ CONSIDER** setting up [SourceLink](./sourcelink.md) to add source control metadata to your assemblies and NuGet package.</span></span>

> <span data-ttu-id="98170-149">Automaticky přidá SourceLink `RepositoryUrl` a `RepositoryType` metadata balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="98170-149">SourceLink automatically adds `RepositoryUrl` and `RepositoryType` metadata to the NuGet package.</span></span> <span data-ttu-id="98170-150">SourceLink přidá také informace o kódu konkrétním použitém zdroji balíčku byla vytvořena z.</span><span class="sxs-lookup"><span data-stu-id="98170-150">SourceLink also adds information about the exact source code the package was built from.</span></span> <span data-ttu-id="98170-151">Hodnota hash zápisu přidán jako metadata bude mít například balíček vytvořen z úložiště Git.</span><span class="sxs-lookup"><span data-stu-id="98170-151">For example, a package created from a Git repository will have the commit hash added as metadata.</span></span>

## <a name="pre-release-packages"></a><span data-ttu-id="98170-152">Balíčky v předběžné verzi</span><span class="sxs-lookup"><span data-stu-id="98170-152">Pre-release packages</span></span>

<span data-ttu-id="98170-153">Balíčky NuGet s příponou verze jsou považovány za [předběžné verze](/nuget/create-packages/prerelease-packages).</span><span class="sxs-lookup"><span data-stu-id="98170-153">NuGet packages with a version suffix are considered [pre-release](/nuget/create-packages/prerelease-packages).</span></span> <span data-ttu-id="98170-154">Ve výchozím nastavení uživatelského rozhraní Správce balíčků NuGet zobrazuje stabilní verze, pokud uživatel požádá o výslovný souhlas a předběžné verze balíčků, díky tomu balíčky v předběžné verzi ideální pro testování uživatel s omezenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="98170-154">By default, the NuGet Package Manager UI shows stable releases unless a user opts-in to pre-release packages, making pre-release packages ideal for limited user testing.</span></span>

```xml
<PackageVersion>1.0.1-beta1</PackageVersion>
```

> [!NOTE]
> <span data-ttu-id="98170-155">Stabilní balíček nemohou záviset na předběžnou verzi balíčku.</span><span class="sxs-lookup"><span data-stu-id="98170-155">A stable package cannot depend on a pre-release package.</span></span> <span data-ttu-id="98170-156">Musíte vytvořit vlastní balíček předběžné verze nebo závisí na starší stabilní verzi.</span><span class="sxs-lookup"><span data-stu-id="98170-156">You must either make your own package pre-release or depend on an older stable version.</span></span>

<span data-ttu-id="98170-157">![Závislost předběžné verze balíčku NuGet](./media/nuget/nuget-prerelease-package.png "závislost předběžné verze balíčku NuGet")</span><span class="sxs-lookup"><span data-stu-id="98170-157">![NuGet pre-release package dependency](./media/nuget/nuget-prerelease-package.png "NuGet pre-release package dependency")</span></span>

<span data-ttu-id="98170-158">**PROVEĎTE ✔️** publikovat předběžné verze balíčků při testování, náhled nebo experimentování.</span><span class="sxs-lookup"><span data-stu-id="98170-158">**✔️ DO** publish a pre-release package when testing, previewing, or experimenting.</span></span>

<span data-ttu-id="98170-159">**PROVEĎTE ✔️** publikovat stabilní balíček, když je připraven tak další stabilní balíčky na něj mohli odkazovat.</span><span class="sxs-lookup"><span data-stu-id="98170-159">**✔️ DO** publish a stable package when its ready so other stable packages can reference it.</span></span>

## <a name="symbol-packages"></a><span data-ttu-id="98170-160">Balíčky symbolů</span><span class="sxs-lookup"><span data-stu-id="98170-160">Symbol packages</span></span>

<span data-ttu-id="98170-161">Soubory symbolů (`*.pdb`) jsou produkované kompilátorem .NET spolu s sestavení.</span><span class="sxs-lookup"><span data-stu-id="98170-161">Symbol files (`*.pdb`) are produced by the .NET compiler alongside assemblies.</span></span> <span data-ttu-id="98170-162">Umístění se symboly mapy provádění soubory do původního zdrojového kódu, můžete procházet zdrojový kód, protože je spuštěn pomocí ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="98170-162">Symbol files map execution locations to the original source code so you can step through source code as it is running using a debugger.</span></span> <span data-ttu-id="98170-163">Podporuje NuGet [generování balíčku samostatný symbol (`*.snupkg`)](/nuget/create-packages/symbol-packages-snupkg) obsahující soubory symbolů souběžně s hlavní balíček, který obsahuje sestavení .NET.</span><span class="sxs-lookup"><span data-stu-id="98170-163">NuGet supports [generating a separate symbol package (`*.snupkg`)](/nuget/create-packages/symbol-packages-snupkg) containing symbol files alongside the main package containing .NET assemblies.</span></span> <span data-ttu-id="98170-164">Představu o balíčky symbolů je už hostovaný na serveru symbolů a stáhnou jenom nástroje, jako je Visual Studio na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="98170-164">The idea of symbol packages is they're hosted on a symbol server and are only downloaded by a tool like Visual Studio on demand.</span></span>

<span data-ttu-id="98170-165">NuGet.org hostuje vlastní [úložiště serveru symbolů](/nuget/create-packages/symbol-packages-snupkg#nugetorg-symbol-server).</span><span class="sxs-lookup"><span data-stu-id="98170-165">NuGet.org hosts its own [symbols server repository](/nuget/create-packages/symbol-packages-snupkg#nugetorg-symbol-server).</span></span> <span data-ttu-id="98170-166">Vývojáři mohou použít symboly publikované na NuGet.org symbol server tak, že přidáte `https://symbols.nuget.org/download/symbols` k jejich [symbol zdroje v sadě Visual Studio](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger).</span><span class="sxs-lookup"><span data-stu-id="98170-166">Developers can use the symbols published to the NuGet.org symbol server by adding `https://symbols.nuget.org/download/symbols` to their [symbol sources in Visual Studio](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="98170-167">Server symbolů NuGet.org podporuje pouze nové [soubory portable symbolů](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) (`*.pdb`) vytvořené projekty založenými na sadě SDK.</span><span class="sxs-lookup"><span data-stu-id="98170-167">The NuGet.org symbol server only supports the new [portable symbol files](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) (`*.pdb`) created by SDK-style projects.</span></span>

<span data-ttu-id="98170-168">Alternativa k vytvoření balíčku symbolů je vložení soubory symbolů do hlavního balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="98170-168">An alternative to creating a symbol package is embedding symbol files in the main NuGet package.</span></span> <span data-ttu-id="98170-169">Hlavní balíček NuGet bude větší, ale symbol vložené soubory znamená, že vývojáři nevyžaduje konfiguraci serveru symbolů NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="98170-169">The main NuGet package will be larger, but the embedded symbol files means developers don't need to configure the NuGet.org symbol server.</span></span> <span data-ttu-id="98170-170">Pokud vytváříte balíček NuGet pomocí sady SDK styl projektu a pak můžete vložit soubory symbolů tak, že nastavíte `AllowedOutputExtensionsInPackageBuildOutputFolder` vlastnost:</span><span class="sxs-lookup"><span data-stu-id="98170-170">If you're building your NuGet package using an SDK-style project, then you can embed symbol files by setting the `AllowedOutputExtensionsInPackageBuildOutputFolder` property:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
 <PropertyGroup>
    <!-- Include symbol files (*.pdb) in the built .nupkg -->
    <AllowedOutputExtensionsInPackageBuildOutputFolder>$(AllowedOutputExtensionsInPackageBuildOutputFolder);.pdb</AllowedOutputExtensionsInPackageBuildOutputFolder>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="98170-171">**✔️ ZVAŽTE** vložení soubory symbolů do hlavního balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="98170-171">**✔️ CONSIDER** embedding symbol files in the main NuGet package.</span></span>

> <span data-ttu-id="98170-172">Vložení souborů symbolů do hlavního balíčku NuGet vývojářům poskytuje lepší možnosti ladění ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="98170-172">Embedding symbol files in the main NuGet package gives developers a better debugging experience by default.</span></span> <span data-ttu-id="98170-173">Nepotřebují najít a nakonfigurujte server symbolů NuGet v jejich prostředí IDE se má získat soubory symbolů.</span><span class="sxs-lookup"><span data-stu-id="98170-173">They don't need to find and configure the NuGet symbol server in their IDE to get symbol files.</span></span>
>
> <span data-ttu-id="98170-174">Nevýhodou souborů vložený symbolů je že velikost balíčku zvyšují o 30 % knihovnám .NET kompilováno s použitím projekty založenými na sadě SDK.</span><span class="sxs-lookup"><span data-stu-id="98170-174">The downside to embedded symbol files is they increase the package size by about 30% for .NET libraries compiled using SDK-style projects.</span></span> <span data-ttu-id="98170-175">Pokud velikost balíčku je problém, jste měli publikovat symboly místo toho v balíčku symbolů.</span><span class="sxs-lookup"><span data-stu-id="98170-175">If package size is a concern, you should publish symbols in a symbol package instead.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="98170-176">[Předchozí](strong-naming.md)
>[další](dependencies.md)</span><span class="sxs-lookup"><span data-stu-id="98170-176">[Previous](strong-naming.md)
[Next](dependencies.md)</span></span>