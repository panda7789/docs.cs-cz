---
title: Vytvoření nové vlastní šablony pro dotnet.
description: Naučte se vytvořit vlastní šablonu pro nový příkaz dotnet. v této fun kurzu.
author: guardrex
ms.author: mairaw
ms.date: 08/12/2017
ms.openlocfilehash: fee2709f54395b9926dae904a448cb92aafb5172
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218079"
---
# <a name="create-a-custom-template-for-dotnet-new"></a><span data-ttu-id="4bae1-103">Vytvoření nové vlastní šablony pro dotnet.</span><span class="sxs-lookup"><span data-stu-id="4bae1-103">Create a custom template for dotnet new</span></span>

<span data-ttu-id="4bae1-104">Tento kurz ukazuje, jak na:</span><span class="sxs-lookup"><span data-stu-id="4bae1-104">This tutorial shows you how to:</span></span>

- <span data-ttu-id="4bae1-105">Vytvořte šablonu základní z existujícího projektu nebo nový projekt konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="4bae1-105">Create a basic template from an existing project or a new console app project.</span></span>
- <span data-ttu-id="4bae1-106">Pack šablony pro distribuci v nuget.org nebo z místního *nupkg* souboru.</span><span class="sxs-lookup"><span data-stu-id="4bae1-106">Pack the template for distribution at nuget.org or from a local *nupkg* file.</span></span>
- <span data-ttu-id="4bae1-107">Instalace šablony z nuget.org, místní *nupkg* soubor nebo místního systému souborů.</span><span class="sxs-lookup"><span data-stu-id="4bae1-107">Install the template from nuget.org, a local *nupkg* file, or the local file system.</span></span>
- <span data-ttu-id="4bae1-108">Odinstalujte šablony.</span><span class="sxs-lookup"><span data-stu-id="4bae1-108">Uninstall the template.</span></span>

<span data-ttu-id="4bae1-109">Pokud dáváte přednost pokračujte kurzu s ucelenou ukázku, stáhněte si [šablona projektu vzorku](https://github.com/dotnet/dotnet-template-samples/tree/master/16-nuget-package).</span><span class="sxs-lookup"><span data-stu-id="4bae1-109">If you prefer to proceed through the tutorial with a complete sample, download the [sample project template](https://github.com/dotnet/dotnet-template-samples/tree/master/16-nuget-package).</span></span> <span data-ttu-id="4bae1-110">Ukázka šablony je nakonfigurován pro distribuci NuGet.</span><span class="sxs-lookup"><span data-stu-id="4bae1-110">The sample template is configured for NuGet distribution.</span></span>

<span data-ttu-id="4bae1-111">Pokud chcete stažený ukázku použít s distribučním systému souborů, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="4bae1-111">If you wish to use the downloaded sample with file system distribution, do the following:</span></span>

- <span data-ttu-id="4bae1-112">Přesunout obsah *obsah* vzorku jednu úroveň do složky *GarciaSoftware.ConsoleTemplate.CSharp* složky.</span><span class="sxs-lookup"><span data-stu-id="4bae1-112">Move the contents of the *content* folder of the sample up one level into the *GarciaSoftware.ConsoleTemplate.CSharp* folder.</span></span>
- <span data-ttu-id="4bae1-113">Odstranit prázdné *obsah* složky.</span><span class="sxs-lookup"><span data-stu-id="4bae1-113">Delete the empty *content* folder.</span></span>
- <span data-ttu-id="4bae1-114">Odstranit *nuspec* souboru.</span><span class="sxs-lookup"><span data-stu-id="4bae1-114">Delete the *nuspec* file.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4bae1-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4bae1-115">Prerequisites</span></span>

- <span data-ttu-id="4bae1-116">Nainstalujte [.NET Core 2.0 SDK](https://www.microsoft.com/net/core) nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="4bae1-116">Install the [.NET Core 2.0 SDK](https://www.microsoft.com/net/core) or later versions.</span></span>
- <span data-ttu-id="4bae1-117">Přečtěte si téma odkaz [vlastních šablon pro dotnet nové](../tools/custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="4bae1-117">Read the reference topic [Custom templates for dotnet new](../tools/custom-templates.md).</span></span>

## <a name="create-a-template-from-a-project"></a><span data-ttu-id="4bae1-118">Vytvoření šablony z projektu</span><span class="sxs-lookup"><span data-stu-id="4bae1-118">Create a template from a project</span></span>

<span data-ttu-id="4bae1-119">Použít existující projekt, který jste potvrzen zkompiluje a spustí nebo vytvořit nový projekt konzolové aplikace do složky na pevném disku.</span><span class="sxs-lookup"><span data-stu-id="4bae1-119">Use an existing project that you've confirmed compiles and runs, or create a new console app project in a folder on your hard drive.</span></span> <span data-ttu-id="4bae1-120">Tento kurz předpokládá, že je název složky projektu *GarciaSoftware.ConsoleTemplate.CSharp* uložené v *Documents\Templates* v profilu uživatele.</span><span class="sxs-lookup"><span data-stu-id="4bae1-120">This tutorial assumes that the name of the project folder is *GarciaSoftware.ConsoleTemplate.CSharp* stored at *Documents\Templates* in the user's profile.</span></span> <span data-ttu-id="4bae1-121">Název šablony kurz projektu je ve formátu  *\<název společnosti >.\< Typ šablony >. \<Programovací jazyk >*, však můžete název projektu a šablony nic nechcete.</span><span class="sxs-lookup"><span data-stu-id="4bae1-121">The tutorial project template name is in the format *\<Company Name>.\<Template Type>.\<Programming Language>*, but you're free to name your project and template anything you wish.</span></span>

1. <span data-ttu-id="4bae1-122">Přidat složku do kořenového adresáře projektu s názvem *. template.config*.</span><span class="sxs-lookup"><span data-stu-id="4bae1-122">Add a folder to the root of the project named *.template.config*.</span></span>
1. <span data-ttu-id="4bae1-123">Uvnitř *. template.config* složky, vytvoření *template.json* souboru konfigurace šablony.</span><span class="sxs-lookup"><span data-stu-id="4bae1-123">Inside the *.template.config* folder, create a *template.json* file to configure your template.</span></span> <span data-ttu-id="4bae1-124">Další informace a člen definice pro *template.json* souborů najdete v tématu [vlastních šablon pro dotnet nové](../tools/custom-templates.md#templatejson) tématu a [ *template.json* schéma na úložiště schématu JSON](http://json.schemastore.org/template).</span><span class="sxs-lookup"><span data-stu-id="4bae1-124">For more information and member definitions for the *template.json* file, see the [Custom templates for dotnet new](../tools/custom-templates.md#templatejson) topic and the [*template.json* schema at the JSON Schema Store](http://json.schemastore.org/template).</span></span>

```json
{
    "$schema": "http://json.schemastore.org/template",
    "author": "Catalina Garcia",
    "classifications": [ "Common", "Console" ],
    "identity": "GarciaSoftware.ConsoleTemplate.CSharp",
    "name": "Garcia Software Console Application",
    "shortName": "garciaconsole"
}
```

<span data-ttu-id="4bae1-125">Šablona je dokončena.</span><span class="sxs-lookup"><span data-stu-id="4bae1-125">The template is finished.</span></span> <span data-ttu-id="4bae1-126">V tuto chvíli máte dvě možnosti pro distribuci šablony.</span><span class="sxs-lookup"><span data-stu-id="4bae1-126">At this point, you have two options for template distribution.</span></span> <span data-ttu-id="4bae1-127">Chcete-li pokračovat v tomto kurzu, vyberte jednu cestu nebo dalších:</span><span class="sxs-lookup"><span data-stu-id="4bae1-127">To continue this tutorial, choose one path or the other:</span></span>

1. <span data-ttu-id="4bae1-128">[Distribuce NuGet](#use-nuget-distribution): nainstalovat šablonu z NuGet nebo místní *nupkg* souboru a používat nainstalované šablony.</span><span class="sxs-lookup"><span data-stu-id="4bae1-128">[NuGet distribution](#use-nuget-distribution): install the template from NuGet or from the local *nupkg* file, and use the installed template.</span></span>
2. <span data-ttu-id="4bae1-129">[Soubor distribuční systému](#use-file-system-distribution).</span><span class="sxs-lookup"><span data-stu-id="4bae1-129">[File system distribution](#use-file-system-distribution).</span></span>

## <a name="use-nuget-distribution"></a><span data-ttu-id="4bae1-130">Použití distribučních NuGet</span><span class="sxs-lookup"><span data-stu-id="4bae1-130">Use NuGet Distribution</span></span>

### <a name="pack-the-template-into-a-nuget-package"></a><span data-ttu-id="4bae1-131">Pack šablony do balíčku NuGet</span><span class="sxs-lookup"><span data-stu-id="4bae1-131">Pack the template into a NuGet package</span></span>

1. <span data-ttu-id="4bae1-132">Vytvořte složku pro balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="4bae1-132">Create a folder for the NuGet package.</span></span> <span data-ttu-id="4bae1-133">Pro tento kurz, název složky *GarciaSoftware.ConsoleTemplate.CSharp* se používá, a je vytvořena uvnitř *Documents\NuGetTemplates* složky v profilu uživatele.</span><span class="sxs-lookup"><span data-stu-id="4bae1-133">For the tutorial, the folder name *GarciaSoftware.ConsoleTemplate.CSharp* is used, and the folder is created inside a *Documents\NuGetTemplates* folder in the user's profile.</span></span> <span data-ttu-id="4bae1-134">Vytvořte složku s názvem *obsah* uvnitř do nové složky pro uložení souborů projektu šablony.</span><span class="sxs-lookup"><span data-stu-id="4bae1-134">Create a folder named *content* inside of the new template folder to hold the project files.</span></span>
1. <span data-ttu-id="4bae1-135">Zkopírujte obsah složky projektu, společně s jeho *.template.config/template.json* souboru do *obsah* složky, které jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="4bae1-135">Copy the contents of your project folder, together with its *.template.config/template.json* file, into the *content* folder you created.</span></span>
1. <span data-ttu-id="4bae1-136">Vedle položky *obsah* složky, přidejte [ *nuspec* soubor](/nuget/create-packages/creating-a-package).</span><span class="sxs-lookup"><span data-stu-id="4bae1-136">Next to the *content* folder, add a [*nuspec* file](/nuget/create-packages/creating-a-package).</span></span> <span data-ttu-id="4bae1-137">Soubor nuspec je soubor XML manifestu, který popisuje obsah balíčku a disky proces vytvoření balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="4bae1-137">The nuspec file is an XML manifest file that describes a package's contents and drives the process of creating the NuGet package.</span></span>
   
   ![Struktura adresářů znázorňující rozložení balíček NuGet](./media/create-custom-template/nugetdirectorylayout.png)

1. <span data-ttu-id="4bae1-139">Uvnitř  **\<packageTypes >** element v *nuspec* souboru, zahrnout  **\<packageType >** element s `name` Hodnota atributu `Template`.</span><span class="sxs-lookup"><span data-stu-id="4bae1-139">Inside of a **\<packageTypes>** element in the *nuspec* file, include a **\<packageType>** element with a `name` attribute value of `Template`.</span></span> <span data-ttu-id="4bae1-140">Obě *obsah* složky a *nuspec* soubor by měl být uložený ve stejném adresáři.</span><span class="sxs-lookup"><span data-stu-id="4bae1-140">Both the *content* folder and the *nuspec* file should reside in the same directory.</span></span> <span data-ttu-id="4bae1-141">V tabulce jsou uvedeny minimální *nuspec* souboru elementy, které jsou potřebné k vytvoření šablony jako balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="4bae1-141">The table shows the minimum *nuspec* file elements required to produce a template as a NuGet package.</span></span>

   | <span data-ttu-id="4bae1-142">Prvek</span><span class="sxs-lookup"><span data-stu-id="4bae1-142">Element</span></span>            | <span data-ttu-id="4bae1-143">Typ</span><span class="sxs-lookup"><span data-stu-id="4bae1-143">Type</span></span>   | <span data-ttu-id="4bae1-144">Popis</span><span class="sxs-lookup"><span data-stu-id="4bae1-144">Description</span></span> |
   | ------------------ | ------ | ----------- |
   | <span data-ttu-id="4bae1-145">**\<Autoři >**</span><span class="sxs-lookup"><span data-stu-id="4bae1-145">**\<authors>**</span></span>     | <span data-ttu-id="4bae1-146">odkazy řetězců</span><span class="sxs-lookup"><span data-stu-id="4bae1-146">string</span></span> | <span data-ttu-id="4bae1-147">Seznam balíčků autoři, odpovídající profil názvy v nuget.org oddělených čárkami. Autoři jsou zobrazeny v galerii NuGet v nuget.org a jsou používané pro křížovou balíčky autory stejné.</span><span class="sxs-lookup"><span data-stu-id="4bae1-147">A comma-separated list of packages authors, matching the profile names on nuget.org. Authors are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span> |
   | <span data-ttu-id="4bae1-148">**\<Popis >**</span><span class="sxs-lookup"><span data-stu-id="4bae1-148">**\<description>**</span></span> | <span data-ttu-id="4bae1-149">odkazy řetězců</span><span class="sxs-lookup"><span data-stu-id="4bae1-149">string</span></span> | <span data-ttu-id="4bae1-150">Dlouhý popis balíčku pro zobrazení uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4bae1-150">A long description of the package for UI display.</span></span> |
   | <span data-ttu-id="4bae1-151">**\<id>**</span><span class="sxs-lookup"><span data-stu-id="4bae1-151">**\<id>**</span></span>          | <span data-ttu-id="4bae1-152">odkazy řetězců</span><span class="sxs-lookup"><span data-stu-id="4bae1-152">string</span></span> | <span data-ttu-id="4bae1-153">Identifikátor balíčku velká a malá písmena, která musí být jedinečný v rámci nuget.org nebo jiná bude balíček nacházet v galerii.</span><span class="sxs-lookup"><span data-stu-id="4bae1-153">The case-insensitive package identifier, which must be unique across nuget.org or whatever gallery the package will reside in.</span></span> <span data-ttu-id="4bae1-154">ID nesmí obsahovat mezery ani znaky, které nejsou platné pro adresu URL a obecně se řídí pravidly obor názvů .NET.</span><span class="sxs-lookup"><span data-stu-id="4bae1-154">IDs may not contain spaces or characters that are not valid for a URL and generally follow .NET namespace rules.</span></span> <span data-ttu-id="4bae1-155">V tématu [výběr balíčku jedinečný identifikátor a nastavení číslo verze](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number) pokyny.</span><span class="sxs-lookup"><span data-stu-id="4bae1-155">See [Choosing a unique package identifier and setting the version number](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number) for guidance.</span></span> |
   | <span data-ttu-id="4bae1-156">**\<packageType>**</span><span class="sxs-lookup"><span data-stu-id="4bae1-156">**\<packageType>**</span></span> | <span data-ttu-id="4bae1-157">odkazy řetězců</span><span class="sxs-lookup"><span data-stu-id="4bae1-157">string</span></span> | <span data-ttu-id="4bae1-158">Umístěte tento element uvnitř  **\<packageTypes >** element mezi  **\<metadata >** elementy.</span><span class="sxs-lookup"><span data-stu-id="4bae1-158">Place this element inside a **\<packageTypes>** element among the **\<metadata>** elements.</span></span> <span data-ttu-id="4bae1-159">Nastavte `name` atribut  **\<packageType >** element `Template`.</span><span class="sxs-lookup"><span data-stu-id="4bae1-159">Set the `name` attribute of the **\<packageType>** element to `Template`.</span></span> |
   | <span data-ttu-id="4bae1-160">**\<verze >**</span><span class="sxs-lookup"><span data-stu-id="4bae1-160">**\<version>**</span></span>     | <span data-ttu-id="4bae1-161">odkazy řetězců</span><span class="sxs-lookup"><span data-stu-id="4bae1-161">string</span></span> | <span data-ttu-id="4bae1-162">Verze balíčku, následující vzoru major.minor.patch.</span><span class="sxs-lookup"><span data-stu-id="4bae1-162">The version of the package, following the major.minor.patch pattern.</span></span> <span data-ttu-id="4bae1-163">Čísla verzí může zahrnovat příponu předběžné verze, jak je popsáno v [předprodejní verze](/nuget/create-packages/prerelease-packages#semantic-versioning).</span><span class="sxs-lookup"><span data-stu-id="4bae1-163">Version numbers may include a pre-release suffix as described in [Pre-release versions](/nuget/create-packages/prerelease-packages#semantic-versioning).</span></span> |

   <span data-ttu-id="4bae1-164">Najdete v článku [odkaz příponou .nuspec](/nuget/schema/nuspec) pro kompletní *nuspec* schéma souboru.</span><span class="sxs-lookup"><span data-stu-id="4bae1-164">See the [.nuspec reference](/nuget/schema/nuspec) for the complete *nuspec* file schema.</span></span>

   <span data-ttu-id="4bae1-165">*Nuspec* souborů pro tento kurz je s názvem *GarciaSoftware.ConsoleTemplate.CSharp.nuspec* a obsahuje následující obsah:</span><span class="sxs-lookup"><span data-stu-id="4bae1-165">The *nuspec* file for the tutorial is named *GarciaSoftware.ConsoleTemplate.CSharp.nuspec* and contains the following content:</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <package xmlns="http://schemas.microsoft.com/packaging/2012/06/nuspec.xsd">
     <metadata>
       <id>GarciaSoftware.ConsoleTemplate.CSharp</id>
       <version>1.0.0</version>
       <description>
         Creates the Garcia Software console app.
       </description>
       <authors>Catalina Garcia</authors>
       <packageTypes>
         <packageType name="Template" />
       </packageTypes>
     </metadata>
   </package>
   ```

1. <span data-ttu-id="4bae1-166">[Vytvoření balíčku](/nuget/create-packages/creating-a-package#creating-the-package) pomocí `nuget pack <PATH_TO_NUSPEC_FILE>` příkaz.</span><span class="sxs-lookup"><span data-stu-id="4bae1-166">[Create the package](/nuget/create-packages/creating-a-package#creating-the-package) using the `nuget pack <PATH_TO_NUSPEC_FILE>` command.</span></span> <span data-ttu-id="4bae1-167">Následující příkaz předpokládá, že složka, která obsahuje prostředky NuGet je v *C:\Users\\\<uživatele > \Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp*.</span><span class="sxs-lookup"><span data-stu-id="4bae1-167">The following command assumes that the folder that holds the NuGet assets is at *C:\Users\\\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp*.</span></span> <span data-ttu-id="4bae1-168">Ale kdekoli umístit složku v systému, `nuget pack` v příkazu zadat cestu k *nuspec* souboru:</span><span class="sxs-lookup"><span data-stu-id="4bae1-168">But wherever you place the folder on your system, the `nuget pack` command accepts the path to the *nuspec* file:</span></span>

   ```console
   nuget pack C:\Users\<USER>\Documents\NuGetTemplates\GarciaSoftware.ConsoleTemplate.CSharp\GarciaSoftware.ConsoleTemplate.CSharp.nuspec
   ```

### <a name="publishing-the-package-to-nugetorg"></a><span data-ttu-id="4bae1-169">Publikování balíčku nuget.org</span><span class="sxs-lookup"><span data-stu-id="4bae1-169">Publishing the package to nuget.org</span></span>

<span data-ttu-id="4bae1-170">K publikování balíčku NuGet, postupujte podle pokynů v [vytvoření a publikování balíčku](/nuget/quickstart/create-and-publish-a-package#publish-the-package) tématu.</span><span class="sxs-lookup"><span data-stu-id="4bae1-170">To publish a NuGet package, follow the instructions in the [Create and publish a package](/nuget/quickstart/create-and-publish-a-package#publish-the-package) topic.</span></span> <span data-ttu-id="4bae1-171">Doporučujeme však není publikovat kurz šablony NuGet jako nikdy odstraněním po publikování, pouze delisted.</span><span class="sxs-lookup"><span data-stu-id="4bae1-171">However, we recommend that you don't publish the tutorial template to NuGet as it can never be deleted once published, only delisted.</span></span> <span data-ttu-id="4bae1-172">Teď, když máte balíček NuGet ve formě *nupkg* souborů, doporučujeme postupujte podle pokynů k instalaci šablony přímo z místní *nupkg* souboru.</span><span class="sxs-lookup"><span data-stu-id="4bae1-172">Now that you have the NuGet package in the form of a *nupkg* file, we suggest that you follow the instructions below to install the template directly from the local *nupkg* file.</span></span>

### <a name="install-the-template-from-a-nuget-package"></a><span data-ttu-id="4bae1-173">Instalace šablony z balíčku NuGet</span><span class="sxs-lookup"><span data-stu-id="4bae1-173">Install the template from a NuGet package</span></span>

#### <a name="install-the-template-from-the-local-nupkg-file"></a><span data-ttu-id="4bae1-174">Instalace šablony z místní *nupkg* souboru</span><span class="sxs-lookup"><span data-stu-id="4bae1-174">Install the template from the local *nupkg* file</span></span>

<span data-ttu-id="4bae1-175">Instalace šablony *nupkg* soubor, který je vytvořil, použijte `dotnet new` s `-i|--install` možnost a zadejte cestu k *nupkg* souboru:</span><span class="sxs-lookup"><span data-stu-id="4bae1-175">To install the template from the *nupkg* file that you produced, use the `dotnet new` command with the `-i|--install` option and provide the path to the *nupkg* file:</span></span>

```console
dotnet new -i C:\Users\<USER>\GarciaSoftware.ConsoleTemplate.CSharp.1.0.0.nupkg
```

#### <a name="install-the-template-from-a-nuget-package-stored-at-nugetorg"></a><span data-ttu-id="4bae1-176">Instalace šablony z balíčku NuGet uložené v nuget.org</span><span class="sxs-lookup"><span data-stu-id="4bae1-176">Install the template from a NuGet package stored at nuget.org</span></span>

<span data-ttu-id="4bae1-177">Pokud chcete nainstalovat z balíčku NuGet uložené v nuget.org, použijte šablonu `dotnet new` s `-i|--install` možnost a zadejte název balíčku NuGet:</span><span class="sxs-lookup"><span data-stu-id="4bae1-177">If you wish to install a template from a NuGet package stored at nuget.org, use the `dotnet new` command with the `-i|--install` option and supply the name of the NuGet package:</span></span>

```console
dotnet new -i GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> <span data-ttu-id="4bae1-178">Příkladem je pouze pro demonstrační účely.</span><span class="sxs-lookup"><span data-stu-id="4bae1-178">The example is for demonstration purposes only.</span></span> <span data-ttu-id="4bae1-179">Není k dispozici `GarciaSoftware.ConsoleTemplate.CSharp` balíček NuGet v nuget.org, a není doporučeno, publikovat a využívat testovací šablon z NuGet.</span><span class="sxs-lookup"><span data-stu-id="4bae1-179">There isn't a `GarciaSoftware.ConsoleTemplate.CSharp` NuGet package at nuget.org, and we don't recommend that you publish and consume test templates from NuGet.</span></span> <span data-ttu-id="4bae1-180">Pokud příkaz spouštíte, je nainstalována žádná šablona.</span><span class="sxs-lookup"><span data-stu-id="4bae1-180">If you run the command, no template is installed.</span></span> <span data-ttu-id="4bae1-181">Však můžete nainstalovat šablonu, která nebyla publikována na nuget.org odkazem *nupkg* souboru přímo na místní systém souborů, jak je uvedeno v předchozí části [nainstalujte šablonu z místní nupkg soubor](#install-the-template-from-the-local-nupkg-file).</span><span class="sxs-lookup"><span data-stu-id="4bae1-181">However, you can install a template that hasn't been published to nuget.org by referencing the *nupkg* file directly on your local file system as shown in the previous section [Install the template from the local nupkg file](#install-the-template-from-the-local-nupkg-file).</span></span>

<span data-ttu-id="4bae1-182">Pokud chcete za provozu příklad instalace šablonu z balíčku v nuget.org, můžete použít [NUnit 3 šablonu pro nové dotnet](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/).</span><span class="sxs-lookup"><span data-stu-id="4bae1-182">If you'd like a live example of how to install a template from a package at nuget.org, you can use the [NUnit 3 template for dotnet-new](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/).</span></span> <span data-ttu-id="4bae1-183">Tato šablona nastaví projekt tak, aby pomocí testování částí NUnit.</span><span class="sxs-lookup"><span data-stu-id="4bae1-183">This template sets up a project to use NUnit unit testing.</span></span> <span data-ttu-id="4bae1-184">Použijte následující příkaz k její instalaci:</span><span class="sxs-lookup"><span data-stu-id="4bae1-184">Use the following command to install it:</span></span>

```console
dotnet new -i NUnit3.DotNetNew.Template
```

<span data-ttu-id="4bae1-185">Pokud uvedete šablon s `dotnet new -l`, uvidíte *NUnit 3 testovacího projektu* s krátký název *nunit* v seznamu šablon.</span><span class="sxs-lookup"><span data-stu-id="4bae1-185">When you list the templates with `dotnet new -l`, you see the *NUnit 3 Test Project* with a short name of *nunit* in the template list.</span></span> <span data-ttu-id="4bae1-186">Jste připravení použít šablonu v další části.</span><span class="sxs-lookup"><span data-stu-id="4bae1-186">You're ready to use the template in the next section.</span></span>

![Okno konzoly zobrazující šabloně NUnit označené Další nainstalované šablony](./media/create-custom-template/nunit1.png)

### <a name="create-a-project-from-the-template"></a><span data-ttu-id="4bae1-188">Vytvoření projektu ze šablony</span><span class="sxs-lookup"><span data-stu-id="4bae1-188">Create a project from the template</span></span>

<span data-ttu-id="4bae1-189">Po instalaci šablony z NuGet použít šablonu spuštěním `dotnet new <TEMPLATE>` příkaz z adresáře, kam chcete modulu šablon výstupu umístit (Pokud používáte `-o|--output` možnost určení konkrétního adresáře).</span><span class="sxs-lookup"><span data-stu-id="4bae1-189">After the template is installed from NuGet, use the template by executing the `dotnet new <TEMPLATE>` command from the directory where you want to the template engine's output placed (unless you're using the `-o|--output` option to specify a specific directory).</span></span> <span data-ttu-id="4bae1-190">Další informace najdete v tématu [ `dotnet new` možnosti](~/docs/core/tools/dotnet-new.md#options).</span><span class="sxs-lookup"><span data-stu-id="4bae1-190">For more information, see [`dotnet new` Options](~/docs/core/tools/dotnet-new.md#options).</span></span> <span data-ttu-id="4bae1-191">Zadejte krátký název šablony přímo na `dotnet new` příkaz.</span><span class="sxs-lookup"><span data-stu-id="4bae1-191">Supply the template's short name directly to the `dotnet new` command.</span></span> <span data-ttu-id="4bae1-192">Pokud chcete vytvořit projekt ze šablony NUnit, spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="4bae1-192">To create a project from the NUnit template, run the following command:</span></span>

```console
dotnet new nunit
```

<span data-ttu-id="4bae1-193">Konzole ukazuje vytvoření projektu a obnovení projektu balíčky.</span><span class="sxs-lookup"><span data-stu-id="4bae1-193">The console shows that the project is created and that the project's packages are restored.</span></span> <span data-ttu-id="4bae1-194">Po spuštění příkazu projekt je připravený k použití.</span><span class="sxs-lookup"><span data-stu-id="4bae1-194">After the command is run, the project is ready for use.</span></span>

![Okno konzoly zobrazující výstup příkazu nové dotnet jak vytvoří NUnit projekt a obnoví závislosti projektu](./media/create-custom-template/nunit2.png)

### <a name="to-uninstall-a-template-from-a-nuget-package-stored-at-nugetorg"></a><span data-ttu-id="4bae1-196">Chcete-li odinstalovat šablonu z balíčku NuGet uložené v nuget.org</span><span class="sxs-lookup"><span data-stu-id="4bae1-196">To uninstall a template from a NuGet package stored at nuget.org</span></span>

```console
dotnet new -u GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> <span data-ttu-id="4bae1-197">Příkladem je pouze pro demonstrační účely.</span><span class="sxs-lookup"><span data-stu-id="4bae1-197">The example is for demonstration purposes only.</span></span> <span data-ttu-id="4bae1-198">Není k dispozici `GarciaSoftware.ConsoleTemplate.CSharp` NuGet balíčku v nuget.org nebo nainstalovat s .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="4bae1-198">There isn't a `GarciaSoftware.ConsoleTemplate.CSharp` NuGet package at nuget.org or installed with the .NET Core SDK.</span></span> <span data-ttu-id="4bae1-199">Pokud příkaz spouštíte, se Odinstaluje balíček či šablonu a zobrazí se následující výjimky:</span><span class="sxs-lookup"><span data-stu-id="4bae1-199">If you run the command, no package/template is uninstalled and you receive the following exception:</span></span>
> 
> > <span data-ttu-id="4bae1-200">Nelze najít něco odinstalace volat 'GarciaSoftware.ConsoleTemplate.CSharp'.</span><span class="sxs-lookup"><span data-stu-id="4bae1-200">Could not find something to uninstall called 'GarciaSoftware.ConsoleTemplate.CSharp'.</span></span>

<span data-ttu-id="4bae1-201">Pokud jste nainstalovali [NUnit 3 šablonu pro nové dotnet](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/) a chcete ji odinstalovat, použijte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="4bae1-201">If you installed the [NUnit 3 template for dotnet-new](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/) and wish to uninstall it, use the following command:</span></span>

```console
dotnet new -u NUnit3.DotNetNew.Template
```

### <a name="uninstall-the-template-from-a-local-nupkg-file"></a><span data-ttu-id="4bae1-202">Odinstalujte šablony ze souboru místní nupkg</span><span class="sxs-lookup"><span data-stu-id="4bae1-202">Uninstall the template from a local nupkg file</span></span>

<span data-ttu-id="4bae1-203">Pokud chcete odinstalovat šablony, nemusíte pokus o použití cesty k *nupkg* souboru.</span><span class="sxs-lookup"><span data-stu-id="4bae1-203">When you wish to uninstall the template, don't attempt to use the path to the *nupkg* file.</span></span> <span data-ttu-id="4bae1-204">*Probíhá pokus o odinstalaci šablony pomocí `dotnet new -u <PATH_TO_NUPKG_FILE>` selže.*</span><span class="sxs-lookup"><span data-stu-id="4bae1-204">*Attempting to uninstall a template using `dotnet new -u <PATH_TO_NUPKG_FILE>` fails.*</span></span> <span data-ttu-id="4bae1-205">Odkazují na balíček podle jeho `id`:</span><span class="sxs-lookup"><span data-stu-id="4bae1-205">Reference the package by its `id`:</span></span>

```console
dotnet new -u GarciaSoftware.ConsoleTemplate.CSharp.1.0.0
```

## <a name="use-file-system-distribution"></a><span data-ttu-id="4bae1-206">Použít distribuci systému souborů</span><span class="sxs-lookup"><span data-stu-id="4bae1-206">Use file system distribution</span></span>

<span data-ttu-id="4bae1-207">K distribuci šablony, umístíte složce projektu šablony v umístění dostupné pro uživatele ve vaší síti.</span><span class="sxs-lookup"><span data-stu-id="4bae1-207">To distribute the template, place the project template folder in a location accessible to users on your network.</span></span> <span data-ttu-id="4bae1-208">Použití `dotnet new` s `-i|--install` možnost a zadejte cestu ke složce šablony (složku projekt obsahující projekt a *. template.config* složku).</span><span class="sxs-lookup"><span data-stu-id="4bae1-208">Use the `dotnet new` command with the `-i|--install` option and specify the path to the template folder (the project folder containing the project and the *.template.config* folder).</span></span>

<span data-ttu-id="4bae1-209">Kurz předpokládá, že v šabloně projektů je uložen v *dokumentů, šablon* složku profilu uživatele.</span><span class="sxs-lookup"><span data-stu-id="4bae1-209">The tutorial assumes the project template is stored in the *Documents/Templates* folder of the user's profile.</span></span> <span data-ttu-id="4bae1-210">Z tohoto umístění instalovat šablony s následujícím příkazu nahraďte \<uživatele > s názvem profilu uživatele:</span><span class="sxs-lookup"><span data-stu-id="4bae1-210">From that location, install the template with the following command replacing \<USER> with the user's profile name:</span></span>

```console
dotnet new -i C:\Users\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp
```

### <a name="create-a-project-from-the-template"></a><span data-ttu-id="4bae1-211">Vytvoření projektu ze šablony</span><span class="sxs-lookup"><span data-stu-id="4bae1-211">Create a project from the template</span></span>

<span data-ttu-id="4bae1-212">Po instalaci šablony ze systému souborů, použijte šablonu spuštěním `dotnet new <TEMPLATE>` příkaz z adresáře, kam chcete modulu šablon výstupu umístit (Pokud používáte `-o|--output` možnost určení konkrétního adresáře).</span><span class="sxs-lookup"><span data-stu-id="4bae1-212">After the template is installed from the file system, use the template by executing the `dotnet new <TEMPLATE>` command from the directory where you want to the template engine's output placed (unless you're using the `-o|--output` option to specify a specific directory).</span></span> <span data-ttu-id="4bae1-213">Další informace najdete v tématu [ `dotnet new` možnosti](~/docs/core/tools/dotnet-new.md#options).</span><span class="sxs-lookup"><span data-stu-id="4bae1-213">For more information, see [`dotnet new` Options](~/docs/core/tools/dotnet-new.md#options).</span></span> <span data-ttu-id="4bae1-214">Zadejte krátký název šablony přímo na `dotnet new` příkaz.</span><span class="sxs-lookup"><span data-stu-id="4bae1-214">Supply the template's short name directly to the `dotnet new` command.</span></span>

<span data-ttu-id="4bae1-215">Ze složky nový projekt vytvořený v *C:\Users\\\<uživatele > \Documents\Projects\MyConsoleApp*, vytvoření projektu z `garciaconsole` šablony:</span><span class="sxs-lookup"><span data-stu-id="4bae1-215">From a new project folder created at *C:\Users\\\<USER>\Documents\Projects\MyConsoleApp*, create a project from the `garciaconsole` template:</span></span>

```console
dotnet new garciaconsole
```

### <a name="uninstall-the-template"></a><span data-ttu-id="4bae1-216">Odinstalujte šablony</span><span class="sxs-lookup"><span data-stu-id="4bae1-216">Uninstall the template</span></span>

<span data-ttu-id="4bae1-217">Pokud jste vytvořili šablonu v místním systému souborů na *C:\Users\\\<uživatele > \Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp*, odinstalujte jej pomocí `-u|--uninstall` přepínače a cestu ke složce šablony:</span><span class="sxs-lookup"><span data-stu-id="4bae1-217">If you created the template on your local file system at *C:\Users\\\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp*, uninstall it with the `-u|--uninstall` switch and the path to the template folder:</span></span>

```console
dotnet new -u C:\Users\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> <span data-ttu-id="4bae1-218">Chcete-li odinstalovat šablony z vašeho místního systému souborů, je potřeba plně kvalifikovanou cestu.</span><span class="sxs-lookup"><span data-stu-id="4bae1-218">To uninstall the template from your local file system, you need to fully qualify the path.</span></span> <span data-ttu-id="4bae1-219">Například *C:\Users\\\<uživatele > \Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* ve složce obsahující není.</span><span class="sxs-lookup"><span data-stu-id="4bae1-219">For example, *C:\Users\\\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="4bae1-220">Kromě toho nezahrnují konečné ukončující lomítko adresáře na cestu k šabloně.</span><span class="sxs-lookup"><span data-stu-id="4bae1-220">Additionally, do not include a final terminating directory slash on your template path.</span></span>

## <a name="see-also"></a><span data-ttu-id="4bae1-221">Viz také</span><span class="sxs-lookup"><span data-stu-id="4bae1-221">See also</span></span>

[<span data-ttu-id="4bae1-222">úložiště GitHub DotNet/ukázka Wiki</span><span class="sxs-lookup"><span data-stu-id="4bae1-222">dotnet/templating GitHub repo Wiki</span></span>](https://github.com/dotnet/templating/wiki)  
[<span data-ttu-id="4bae1-223">úložiště GitHub DotNet/dotnet šablony – ukázky</span><span class="sxs-lookup"><span data-stu-id="4bae1-223">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
[<span data-ttu-id="4bae1-224">Jak vytvořit nové vlastní šablony pro dotnet.</span><span class="sxs-lookup"><span data-stu-id="4bae1-224">How to create your own templates for dotnet new</span></span>](https://blogs.msdn.microsoft.com/dotnet/2017/04/02/how-to-create-your-own-templates-for-dotnet-new/)  
[<span data-ttu-id="4bae1-225">*Template.JSON* schématu na úložiště schématu JSON</span><span class="sxs-lookup"><span data-stu-id="4bae1-225">*template.json* schema at the JSON Schema Store</span></span>](http://json.schemastore.org/template)  
