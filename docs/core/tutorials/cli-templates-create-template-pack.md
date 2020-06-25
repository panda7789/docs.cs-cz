---
title: Vytvoření balíčku šablon pro dotnet New
description: Naučte se vytvořit soubor CSPROJ, který vytvoří balíček šablon pro příkaz dotnet New.
author: adegeo
ms.date: 12/10/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: 25264fff42c47f5bb660f68f85dbb123b5b2608c
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324338"
---
# <a name="tutorial-create-a-template-pack"></a><span data-ttu-id="06106-103">Kurz: vytvoření balíčku šablon</span><span class="sxs-lookup"><span data-stu-id="06106-103">Tutorial: Create a template pack</span></span>

<span data-ttu-id="06106-104">Pomocí .NET Core můžete vytvářet a nasazovat šablony, které generují projekty, soubory i prostředky.</span><span class="sxs-lookup"><span data-stu-id="06106-104">With .NET Core, you can create and deploy templates that generate projects, files, even resources.</span></span> <span data-ttu-id="06106-105">Tento kurz je třetí částí série, která vás seznámí s postupem vytvoření, instalace a odinstalace šablon pro použití s `dotnet new` příkazem.</span><span class="sxs-lookup"><span data-stu-id="06106-105">This tutorial is part three of a series that teaches you how to create, install, and uninstall templates for use with the `dotnet new` command.</span></span>

<span data-ttu-id="06106-106">V této části série se naučíte:</span><span class="sxs-lookup"><span data-stu-id="06106-106">In this part of the series you'll learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="06106-107">Vytvoření \* projektu. csproj pro sestavení sady šablon</span><span class="sxs-lookup"><span data-stu-id="06106-107">Create a \*.csproj project to build a template pack</span></span>
> * <span data-ttu-id="06106-108">Konfigurace souboru projektu pro balení</span><span class="sxs-lookup"><span data-stu-id="06106-108">Configure the project file for packing</span></span>
> * <span data-ttu-id="06106-109">Instalace šablony ze souboru balíčku NuGet</span><span class="sxs-lookup"><span data-stu-id="06106-109">Install a template from a NuGet package file</span></span>
> * <span data-ttu-id="06106-110">Odinstalace šablony podle ID balíčku</span><span class="sxs-lookup"><span data-stu-id="06106-110">Uninstall a template by package ID</span></span>

## <a name="prerequisites"></a><span data-ttu-id="06106-111">Požadované součásti</span><span class="sxs-lookup"><span data-stu-id="06106-111">Prerequisites</span></span>

* <span data-ttu-id="06106-112">Dokončete [část 1](cli-templates-create-item-template.md) a [část 2](cli-templates-create-project-template.md) této série kurzů.</span><span class="sxs-lookup"><span data-stu-id="06106-112">Complete [part 1](cli-templates-create-item-template.md) and [part 2](cli-templates-create-project-template.md) of this tutorial series.</span></span>

  <span data-ttu-id="06106-113">V tomto kurzu se používají dvě šablony vytvořené v první dvou částech tohoto kurzu.</span><span class="sxs-lookup"><span data-stu-id="06106-113">This tutorial uses the two templates created in the first two parts of this tutorial.</span></span> <span data-ttu-id="06106-114">Můžete použít jinou šablonu, pokud zkopírujete šablonu jako složku do složky _working\templates \\ _ .</span><span class="sxs-lookup"><span data-stu-id="06106-114">You can use a different template as long as you copy the template, as a folder, into the _working\templates\\_ folder.</span></span>

* <span data-ttu-id="06106-115">Otevřete terminál a přejděte do _pracovní \\ _ složky.</span><span class="sxs-lookup"><span data-stu-id="06106-115">Open a terminal and navigate to the _working\\_ folder.</span></span>

## <a name="create-a-template-pack-project"></a><span data-ttu-id="06106-116">Vytvoření projektu Template Pack</span><span class="sxs-lookup"><span data-stu-id="06106-116">Create a template pack project</span></span>

<span data-ttu-id="06106-117">Template Pack je jeden nebo více šablon zabalených do souboru.</span><span class="sxs-lookup"><span data-stu-id="06106-117">A template pack is one or more templates packaged into a file.</span></span> <span data-ttu-id="06106-118">Při instalaci nebo odinstalaci balíčku se všechny šablony obsažené v balíčku přidají nebo odeberou v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="06106-118">When you install or uninstall a pack, all templates contained in the pack are added or removed, respectively.</span></span> <span data-ttu-id="06106-119">Předchozí části této série kurzů se pracovaly jenom s jednotlivými šablonami.</span><span class="sxs-lookup"><span data-stu-id="06106-119">The previous parts of this tutorial series only worked with individual templates.</span></span> <span data-ttu-id="06106-120">Chcete-li sdílet nesbalenou šablonu, je nutné zkopírovat složku šablony a nainstalovat ji prostřednictvím této složky.</span><span class="sxs-lookup"><span data-stu-id="06106-120">To share a non-packed template, you have to copy the template folder and install via that folder.</span></span> <span data-ttu-id="06106-121">Vzhledem k tomu, že balíček šablon může obsahovat více než jednu šablonu a je jedním souborem, sdílení je snazší.</span><span class="sxs-lookup"><span data-stu-id="06106-121">Because a template pack can have more than one template in it, and is a single file, sharing is easier.</span></span>

<span data-ttu-id="06106-122">Balíčky šablon jsou reprezentovány souborem balíčku NuGet (_. nupkg_).</span><span class="sxs-lookup"><span data-stu-id="06106-122">Template packs are represented by a NuGet package (_.nupkg_) file.</span></span> <span data-ttu-id="06106-123">A podobně jako jakýkoli balíček NuGet můžete nahrát balíček šablony do informačního kanálu NuGet.</span><span class="sxs-lookup"><span data-stu-id="06106-123">And, like any NuGet package, you can upload the template pack to a NuGet feed.</span></span> <span data-ttu-id="06106-124">`dotnet new -i`Příkaz podporuje instalaci balíčku šablon z informačního kanálu balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="06106-124">The `dotnet new -i` command supports installing template pack from a NuGet package feed.</span></span> <span data-ttu-id="06106-125">Kromě toho můžete nainstalovat sadu šablon přímo ze souboru _. nupkg_ .</span><span class="sxs-lookup"><span data-stu-id="06106-125">Additionally, you can install a template pack from a _.nupkg_ file directly.</span></span>

<span data-ttu-id="06106-126">Normálně používáte soubor projektu C# ke kompilaci kódu a vytvoření binárního souboru.</span><span class="sxs-lookup"><span data-stu-id="06106-126">Normally you use a C# project file to compile code and produce a binary.</span></span> <span data-ttu-id="06106-127">Projekt však lze použít také k vygenerování balíčku šablon.</span><span class="sxs-lookup"><span data-stu-id="06106-127">However, the project can also be used to generate a template pack.</span></span> <span data-ttu-id="06106-128">Změnou nastavení v _. csproj_můžete zabránit tomu, aby se v kompilování kódu a místo toho zahrnuly všechny prostředky vašich šablon jako prostředky.</span><span class="sxs-lookup"><span data-stu-id="06106-128">By changing the settings of the _.csproj_, you can prevent it from compiling any code and instead include all the assets of your templates as resources.</span></span> <span data-ttu-id="06106-129">Při sestavení tohoto projektu vytvoří balíček NuGet sady Template Pack.</span><span class="sxs-lookup"><span data-stu-id="06106-129">When this project is built, it produces a template pack NuGet package.</span></span>

<span data-ttu-id="06106-130">Balíček, který vytvoříte, bude obsahovat [šablonu položky](cli-templates-create-item-template.md) a [šablonu balíčku](cli-templates-create-project-template.md) , která byla dříve vytvořena.</span><span class="sxs-lookup"><span data-stu-id="06106-130">The pack you'll create will include the [item template](cli-templates-create-item-template.md) and [package template](cli-templates-create-project-template.md) previously created.</span></span> <span data-ttu-id="06106-131">Vzhledem k tomu, že jsme tyto dvě šablony seskupili do složky _working\templates \\ _ , můžeme použít _pracovní_ složku pro soubor _. csproj_ .</span><span class="sxs-lookup"><span data-stu-id="06106-131">Because we grouped the two templates into the _working\templates\\_ folder, we can use the _working_ folder for the _.csproj_ file.</span></span>

<span data-ttu-id="06106-132">V terminálu přejděte do _pracovní_ složky.</span><span class="sxs-lookup"><span data-stu-id="06106-132">In your terminal, navigate to the _working_ folder.</span></span> <span data-ttu-id="06106-133">Vytvořte nový projekt a nastavte jeho název na `templatepack` výstupní složku na aktuální.</span><span class="sxs-lookup"><span data-stu-id="06106-133">Create a new project and set the name to `templatepack` and the output folder to the current folder.</span></span>

```dotnetcli
dotnet new console -n templatepack -o .
```

<span data-ttu-id="06106-134">`-n`Parametr nastaví název souboru _. csproj_ na _templatepack. csproj_.</span><span class="sxs-lookup"><span data-stu-id="06106-134">The `-n` parameter sets the _.csproj_ filename to _templatepack.csproj_.</span></span> <span data-ttu-id="06106-135">`-o`Parametr vytvoří soubory v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="06106-135">The `-o` parameter creates the files in the current directory.</span></span> <span data-ttu-id="06106-136">Měl by se zobrazit výsledek podobný následujícímu výstupu.</span><span class="sxs-lookup"><span data-stu-id="06106-136">You should see a result similar to the following output.</span></span>

```dotnetcli
dotnet new console -n templatepack -o .
```

```console
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on .\templatepack.csproj...
  Restore completed in 52.38 ms for C:\working\templatepack.csproj.

Restore succeeded.
```

<span data-ttu-id="06106-137">Potom v oblíbeném editoru otevřete soubor _templatepack. csproj_ a nahraďte jeho obsah následujícím kódem XML:</span><span class="sxs-lookup"><span data-stu-id="06106-137">Next, open the _templatepack.csproj_ file in your favorite editor and replace the content with the following XML:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <PackageType>Template</PackageType>
    <PackageVersion>1.0</PackageVersion>
    <PackageId>AdatumCorporation.Utility.Templates</PackageId>
    <Title>AdatumCorporation Templates</Title>
    <Authors>Me</Authors>
    <Description>Templates to use when creating an application for Adatum Corporation.</Description>
    <PackageTags>dotnet-new;templates;contoso</PackageTags>

    <TargetFramework>netstandard2.0</TargetFramework>

    <IncludeContentInPack>true</IncludeContentInPack>
    <IncludeBuildOutput>false</IncludeBuildOutput>
    <ContentTargetFolders>content</ContentTargetFolders>
  </PropertyGroup>

  <ItemGroup>
    <Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />
    <Compile Remove="**\*" />
  </ItemGroup>

</Project>
```

<span data-ttu-id="06106-138">`<PropertyGroup>`Nastavení v souboru XML výše je rozděleno do tří skupin.</span><span class="sxs-lookup"><span data-stu-id="06106-138">The `<PropertyGroup>` settings in the XML above is broken into three groups.</span></span> <span data-ttu-id="06106-139">První skupina se zabývá vlastnostmi vyžadovanými pro balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="06106-139">The first group deals with properties required for a NuGet package.</span></span> <span data-ttu-id="06106-140">Aby `<Package` bylo možné balíček v informačním kanálu NuGet identifikovat, musí se tato tři nastavení udělat s vlastnostmi balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="06106-140">The three `<Package` settings have to do with the NuGet package properties to identify your package on a NuGet feed.</span></span> <span data-ttu-id="06106-141">Konkrétně se `<PackageId>` používá k odinstalování sady šablon s jedním názvem, nikoli cestou k adresáři.</span><span class="sxs-lookup"><span data-stu-id="06106-141">Specifically the `<PackageId>` value is used to uninstall the template pack with a single name instead of a directory path.</span></span> <span data-ttu-id="06106-142">Dá se použít taky k instalaci balíčku šablon z informačního kanálu NuGet.</span><span class="sxs-lookup"><span data-stu-id="06106-142">It can also be used to install the template pack from a NuGet feed.</span></span> <span data-ttu-id="06106-143">Zbývající nastavení, jako je `<Title>` `<PackageTags>` třeba a musí dělat s metadaty zobrazenými v informačním kanálu NuGet.</span><span class="sxs-lookup"><span data-stu-id="06106-143">The remaining settings such as `<Title>` and `<PackageTags>` have to do with metadata displayed on the NuGet feed.</span></span> <span data-ttu-id="06106-144">Další informace o nastaveních NuGet naleznete v tématu [vlastnosti NuGet a MSBuild](/nuget/reference/msbuild-targets).</span><span class="sxs-lookup"><span data-stu-id="06106-144">For more information about NuGet settings, see [NuGet and MSBuild properties](/nuget/reference/msbuild-targets).</span></span>

<span data-ttu-id="06106-145">`<TargetFramework>`Nastavení musí být nastavené tak, aby nástroj MSBuild běžel správně při spuštění příkazu Pack pro zkompilování a sbalení projektu.</span><span class="sxs-lookup"><span data-stu-id="06106-145">The `<TargetFramework>` setting must be set so that MSBuild will run properly when you run the pack command to compile and pack the project.</span></span>

<span data-ttu-id="06106-146">Poslední tři nastavení musí udělat s tím, že správně nakonfigurujete projekt tak, aby zahrnoval šablony do příslušné složky v balíčku NuGet, když se vytvoří.</span><span class="sxs-lookup"><span data-stu-id="06106-146">The last three settings have to do with configuring the project correctly to include the templates in the appropriate folder in the NuGet pack when it's created.</span></span>

<span data-ttu-id="06106-147">`<ItemGroup>`Obsahuje dvě nastavení.</span><span class="sxs-lookup"><span data-stu-id="06106-147">The `<ItemGroup>` contains two settings.</span></span> <span data-ttu-id="06106-148">Nejprve `<Content>` nastavení zahrnuje vše ve složce _šablony_ jako obsah.</span><span class="sxs-lookup"><span data-stu-id="06106-148">First, the `<Content>` setting includes everything in the _templates_ folder as content.</span></span> <span data-ttu-id="06106-149">Také je nastavené pro vyloučení složky _bin_ nebo složky _obj_ , aby se zabránilo zahrnutí zkompilovaného kódu (Pokud jste otestovali a nakompilováni šablony).</span><span class="sxs-lookup"><span data-stu-id="06106-149">It's also set to exclude any _bin_ folder or _obj_ folder to prevent any compiled code (if you tested and compiled your templates) from being included.</span></span> <span data-ttu-id="06106-150">Za druhé `<Compile>` Nastavení vyloučí všechny soubory kódu z kompilace bez ohledu na to, kde se nacházejí.</span><span class="sxs-lookup"><span data-stu-id="06106-150">Second, the `<Compile>` setting excludes all code files from compiling no matter where they're located.</span></span> <span data-ttu-id="06106-151">Toto nastavení brání projektu, který se používá k vytvoření sady šablon z pokusu o zkompilování kódu v hierarchii složek _šablon_ .</span><span class="sxs-lookup"><span data-stu-id="06106-151">This setting prevents the project being used to create a template pack from trying to compile the code in the _templates_ folder hierarchy.</span></span>

## <a name="build-and-install"></a><span data-ttu-id="06106-152">Sestavení a instalace</span><span class="sxs-lookup"><span data-stu-id="06106-152">Build and install</span></span>

<span data-ttu-id="06106-153">Uložte tento soubor a potom spusťte příkaz Pack.</span><span class="sxs-lookup"><span data-stu-id="06106-153">Save this file and then run the pack command</span></span>

```dotnetcli
dotnet pack
```

<span data-ttu-id="06106-154">Tento příkaz sestaví projekt a vytvoří balíček NuGet v tomto umístění by měl být složka _working\bin\Debug_ .</span><span class="sxs-lookup"><span data-stu-id="06106-154">This command will build your project and create a NuGet package in This should be the _working\bin\Debug_ folder.</span></span>

```dotnetcli
dotnet pack
```

```console
Microsoft (R) Build Engine version 16.2.0-preview-19278-01+d635043bd for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 123.86 ms for C:\working\templatepack.csproj.

  templatepack -> C:\working\bin\Debug\netstandard2.0\templatepack.dll
  Successfully created package 'C:\working\bin\Debug\AdatumCorporation.Utility.Templates.1.0.0.nupkg'.
```

<span data-ttu-id="06106-155">Dále nainstalujte soubor Template Pack pomocí `dotnet new -i PATH_TO_NUPKG_FILE` příkazu.</span><span class="sxs-lookup"><span data-stu-id="06106-155">Next, install the template pack file with the `dotnet new -i PATH_TO_NUPKG_FILE` command.</span></span>

```console
C:\working> dotnet new -i C:\working\bin\Debug\AdatumCorporation.Utility.Templates.1.0.0.nupkg
Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.

... cut to save space ...

Templates                                         Short Name            Language          Tags
-------------------------------------------------------------------------------------------------------------------------------
Example templates: string extensions              stringext             [C#]              Common/Code
Console Application                               console               [C#], F#, VB      Common/Console
Example templates: async project                  consoleasync          [C#]              Common/Console/C#8
Class library                                     classlib              [C#], F#, VB      Common/Library
```

<span data-ttu-id="06106-156">Pokud jste nahráli balíček NuGet do kanálu NuGet, můžete použít příkaz, který `dotnet new -i PACKAGEID` `PACKAGEID` je stejný jako `<PackageId>` nastavení ze souboru _. csproj_ .</span><span class="sxs-lookup"><span data-stu-id="06106-156">If you uploaded the NuGet package to a NuGet feed, you can use the `dotnet new -i PACKAGEID` command where `PACKAGEID` is the same as the `<PackageId>` setting from the _.csproj_ file.</span></span> <span data-ttu-id="06106-157">ID tohoto balíčku je stejné jako identifikátor balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="06106-157">This package ID is the same as the NuGet package identifier.</span></span>

## <a name="uninstall-the-template-pack"></a><span data-ttu-id="06106-158">Odinstalace balíčku šablon</span><span class="sxs-lookup"><span data-stu-id="06106-158">Uninstall the template pack</span></span>

<span data-ttu-id="06106-159">Bez ohledu na to, jakým způsobem jste balíček šablon nainstalovali, buď pomocí souboru _. nupkg_ přímo nebo pomocí kanálu NuGet, je odebrání balíčku šablon stejné.</span><span class="sxs-lookup"><span data-stu-id="06106-159">No matter how you installed the template pack, either with the _.nupkg_ file directly or by NuGet feed, removing a template pack is the same.</span></span> <span data-ttu-id="06106-160">Použijte `<PackageId>` šablonu, kterou chcete odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="06106-160">Use the `<PackageId>` of the template you want to uninstall.</span></span> <span data-ttu-id="06106-161">Seznam šablon, které jsou nainstalovány, můžete získat spuštěním `dotnet new -u` příkazu.</span><span class="sxs-lookup"><span data-stu-id="06106-161">You can get a list of templates that are installed by running the `dotnet new -u` command.</span></span>

```dotnetcli
dotnet new -u
```

```console
Template Instantiation Commands for .NET Core CLI

Currently installed items:
  Microsoft.DotNet.Common.ItemTemplates
    Templates:
      dotnet gitignore file (gitignore)
      global.json file (globaljson)
      NuGet Config (nugetconfig)
      Solution File (sln)
      Dotnet local tool manifest file (tool-manifest)
      Web Config (webconfig)

... cut to save space ...

  NUnit3.DotNetNew.Template
    Templates:
      NUnit 3 Test Project (nunit) C#
      NUnit 3 Test Item (nunit-test) C#
      NUnit 3 Test Project (nunit) F#
      NUnit 3 Test Item (nunit-test) F#
      NUnit 3 Test Project (nunit) VB
      NUnit 3 Test Item (nunit-test) VB
  AdatumCorporation.Utility.Templates
    Templates:
      Example templates: async project (consoleasync) C#
      Example templates: string extensions (stringext) C#
```

<span data-ttu-id="06106-162">Spusťte `dotnet new -u AdatumCorporation.Utility.Templates` pro odinstalaci šablony.</span><span class="sxs-lookup"><span data-stu-id="06106-162">Run `dotnet new -u AdatumCorporation.Utility.Templates` to uninstall the template.</span></span> <span data-ttu-id="06106-163">`dotnet new`Příkaz zobrazí výstup informací o nápovědě, které by měly vynechat šablony, které jste předtím nainstalovali.</span><span class="sxs-lookup"><span data-stu-id="06106-163">The `dotnet new` command will output help information that should omit the templates you previously installed.</span></span>

<span data-ttu-id="06106-164">Gratulujeme!</span><span class="sxs-lookup"><span data-stu-id="06106-164">Congratulations!</span></span> <span data-ttu-id="06106-165">nainstalovali jste a odinstalovali balíček šablon.</span><span class="sxs-lookup"><span data-stu-id="06106-165">you've installed and uninstalled a template pack.</span></span>

## <a name="next-steps"></a><span data-ttu-id="06106-166">Další kroky</span><span class="sxs-lookup"><span data-stu-id="06106-166">Next steps</span></span>

<span data-ttu-id="06106-167">Další informace o šablonách, ze kterých už jste se seznámili, najdete v článku [vlastní šablony pro dotnet nový](../tools/custom-templates.md) článek.</span><span class="sxs-lookup"><span data-stu-id="06106-167">To learn more about templates, most of which you've already learned, see the [Custom templates for dotnet new](../tools/custom-templates.md) article.</span></span>

* [<span data-ttu-id="06106-168">dotnet/šablonování wiki úložiště GitHub</span><span class="sxs-lookup"><span data-stu-id="06106-168">dotnet/templating GitHub repo Wiki</span></span>](https://github.com/dotnet/templating/wiki)
* [<span data-ttu-id="06106-169">dotnet/dotnet-Template-Samples – úložiště GitHub</span><span class="sxs-lookup"><span data-stu-id="06106-169">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
* [<span data-ttu-id="06106-170">*template.js* schématu v ÚLOŽIŠTI schémat JSON</span><span class="sxs-lookup"><span data-stu-id="06106-170">*template.json* schema at the JSON Schema Store</span></span>](http://json.schemastore.org/template)
