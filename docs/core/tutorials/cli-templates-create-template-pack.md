---
title: Vytvořit novou sadu šablon pro dotnet
description: Zjistěte, jak vytvořit soubor csproj, který se sestaví balíček šablon pro nový příkaz dotnet.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: df8c33856195ba7feacd32203e4a885997b50ad2
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2019
ms.locfileid: "67877183"
---
# <a name="tutorial-create-a-template-pack"></a><span data-ttu-id="3423d-103">Kurz: Vytvoření balíčku šablony</span><span class="sxs-lookup"><span data-stu-id="3423d-103">Tutorial: Create a template pack</span></span>

<span data-ttu-id="3423d-104">S .NET Core můžete vytvořit a nasadit šablon, které generují projektů, souborů, dokonce i prostředky.</span><span class="sxs-lookup"><span data-stu-id="3423d-104">With .NET Core, you can create and deploy templates that generate projects, files, even resources.</span></span> <span data-ttu-id="3423d-105">Tento kurz je třetí částí série, která vás naučí, jak vytvořit, instalaci a odinstalaci, šablony pro použití se službou `dotnet new` příkazu.</span><span class="sxs-lookup"><span data-stu-id="3423d-105">This tutorial is part three of a series that teaches you how to create, install, and uninstall, templates for use with the `dotnet new` command.</span></span>

<span data-ttu-id="3423d-106">V této části této série se dozvíte jak:</span><span class="sxs-lookup"><span data-stu-id="3423d-106">In this part of the series you'll learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="3423d-107">Vytvoření projektu _.csproj\* k vytvoření balíčku šablony</span><span class="sxs-lookup"><span data-stu-id="3423d-107">Create a _.csproj\* project to build a template pack</span></span>
> * <span data-ttu-id="3423d-108">Konfigurovat soubor projektu pro balení</span><span class="sxs-lookup"><span data-stu-id="3423d-108">Configure the project file for packing</span></span>
> * <span data-ttu-id="3423d-109">Instalace šablony ze souboru balíčku NuGet</span><span class="sxs-lookup"><span data-stu-id="3423d-109">Install a template from a NuGet package file</span></span>
> * <span data-ttu-id="3423d-110">Odinstalace šablony podle ID balíčku</span><span class="sxs-lookup"><span data-stu-id="3423d-110">Uninstall a template by package ID</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3423d-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3423d-111">Prerequisites</span></span>

* <span data-ttu-id="3423d-112">Kompletní [1. část](cli-templates-create-item-template.md) a [2. část](cli-templates-create-project-template.md) této série kurzů.</span><span class="sxs-lookup"><span data-stu-id="3423d-112">Complete [part 1](cli-templates-create-item-template.md) and [part 2](cli-templates-create-project-template.md) of this tutorial series.</span></span>

  <span data-ttu-id="3423d-113">Tento kurz používá dvě šablony vytvořené v prvních dvou částech tohoto kurzu.</span><span class="sxs-lookup"><span data-stu-id="3423d-113">This tutorial uses the two templates created in the first two parts of this tutorial.</span></span> <span data-ttu-id="3423d-114">Je možné, můžete použít jinou šablonu, za předpokladu, zkopírujte šablony jako složku do _working\templates\\_  složky.</span><span class="sxs-lookup"><span data-stu-id="3423d-114">It's possible you can use a different template as long as you copy the template as a folder into the _working\templates\\_ folder.</span></span>

* <span data-ttu-id="3423d-115">Otevřete terminál a přejděte _working\templates\\_  složky.</span><span class="sxs-lookup"><span data-stu-id="3423d-115">Open a terminal and navigate to the _working\templates\\_ folder.</span></span>

## <a name="create-a-template-pack-project"></a><span data-ttu-id="3423d-116">Vytvořte projekt balíčku šablony</span><span class="sxs-lookup"><span data-stu-id="3423d-116">Create a template pack project</span></span>

<span data-ttu-id="3423d-117">Balíček šablony je jedna nebo více šablon zabalené do souboru.</span><span class="sxs-lookup"><span data-stu-id="3423d-117">A template pack is one or more templates packaged into a file.</span></span> <span data-ttu-id="3423d-118">Při instalaci nebo odinstalaci aktualizací Service pack, jsou všechny šablony, které jsou součástí této sady přidaly nebo odebraly v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="3423d-118">When you install or uninstall a pack, all templates contained in the pack are added or removed, respectively.</span></span> <span data-ttu-id="3423d-119">Předchozí části této série kurzů pouze pracovali jednotlivé šablony.</span><span class="sxs-lookup"><span data-stu-id="3423d-119">The previous parts of this tutorial series only worked with individual templates.</span></span> <span data-ttu-id="3423d-120">Sdílení šablony nezabalených, budete muset zkopírovat do složky šablony a nainstalovat prostřednictvím této složky.</span><span class="sxs-lookup"><span data-stu-id="3423d-120">To share a non-packed template, you have to copy the template folder and install via that folder.</span></span> <span data-ttu-id="3423d-121">Protože šablonovaný balíček může mít více než jedna šablona v něm a je jeden soubor, sdílení je jednodušší.</span><span class="sxs-lookup"><span data-stu-id="3423d-121">Because a template pack can have more than one template in it, and is a single file, sharing is easier.</span></span>

<span data-ttu-id="3423d-122">Šablonované balíčky jsou reprezentované prostřednictvím balíčku NuGet ( _.nupkg_) soubor.</span><span class="sxs-lookup"><span data-stu-id="3423d-122">Template packs are represented by a NuGet package (_.nupkg_) file.</span></span> <span data-ttu-id="3423d-123">A stejně jako libovolný balíček NuGet můžete nahrát šablonovaný balíček NuGet informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="3423d-123">And, like any NuGet package, you can upload the template pack to a NuGet feed.</span></span> <span data-ttu-id="3423d-124">`dotnet new -i` Příkaz podporuje instalaci šablonovaný balíček z informačního kanálu balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="3423d-124">The `dotnet new -i` command supports installing template pack from a NuGet package feed.</span></span> <span data-ttu-id="3423d-125">Kromě toho můžete nainstalovat balíček ze šablon _.nupkg_ přímo soubor.</span><span class="sxs-lookup"><span data-stu-id="3423d-125">Additionally, you can install a template pack from a _.nupkg_ file directly.</span></span>

<span data-ttu-id="3423d-126">Obvykle použijete C# soubor projektu a kompilaci kódu a vytvoří binární soubor.</span><span class="sxs-lookup"><span data-stu-id="3423d-126">Normally you use a C# project file to compile code and produce a binary.</span></span> <span data-ttu-id="3423d-127">Ale projektu lze také generovat balíček šablon.</span><span class="sxs-lookup"><span data-stu-id="3423d-127">However, the project can also be used to generate a template pack.</span></span> <span data-ttu-id="3423d-128">Změnou nastavení _.csproj_, můžete zabránit kompilaci libovolný kód a místo toho zahrnout všechny prostředky k šablonám jako prostředky.</span><span class="sxs-lookup"><span data-stu-id="3423d-128">By changing the settings of the _.csproj_, you can prevent it from compiling any code and instead include all the assets of your templates as resources.</span></span> <span data-ttu-id="3423d-129">Když tento projekt se vytvořil, vytvoří šablonovaný balíček balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="3423d-129">When this project is built, it produces a template pack NuGet package.</span></span>

<span data-ttu-id="3423d-130">Bude obsahovat pack, kterou vytvoříte [šablony položky](cli-templates-create-item-template.md) a [balíček šablony](cli-templates-create-project-template.md) předtím vytvořili.</span><span class="sxs-lookup"><span data-stu-id="3423d-130">The pack you'll create will include the [item template](cli-templates-create-item-template.md) and [package template](cli-templates-create-project-template.md) previously created.</span></span> <span data-ttu-id="3423d-131">Protože jsme seskupit dvou šablon do _working\templates\\_  složky, můžeme použít _práce_ složku pro _.csproj_ souboru.</span><span class="sxs-lookup"><span data-stu-id="3423d-131">Because we grouped the two templates into the _working\templates\\_ folder, we can use the _working_ folder for the _.csproj_ file.</span></span>

<span data-ttu-id="3423d-132">V terminálu přejděte _práce_ složky.</span><span class="sxs-lookup"><span data-stu-id="3423d-132">In your terminal, navigate to the _working_ folder.</span></span> <span data-ttu-id="3423d-133">Vytvořte nový projekt a nastavte její název na `templatepack` a složku výstupu do aktuální složky.</span><span class="sxs-lookup"><span data-stu-id="3423d-133">Create a new project and set the name to `templatepack` and the output folder to the current folder.</span></span>

```console
dotnet new console -n templatepack -o .
```

<span data-ttu-id="3423d-134">`-n` Sady parametrů _.csproj_ název souboru k _templatepack.csproj_ a `-o` parametry vytvoří soubory v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="3423d-134">The `-n` parameter sets the _.csproj_ filename to _templatepack.csproj_ and the `-o` parameters creates the files in the current directory.</span></span> <span data-ttu-id="3423d-135">Zobrazí se výsledek podobný následující výstup.</span><span class="sxs-lookup"><span data-stu-id="3423d-135">You should see a result similar to the following output.</span></span>

```console
C:\working> dotnet new console -n templatepack -o .
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on .\templatepack.csproj...
  Restore completed in 52.38 ms for C:\working\templatepack.csproj.

Restore succeeded.
```

<span data-ttu-id="3423d-136">Dále otevřete _templatepack.csproj_ souboru ve svém oblíbeném editoru a nahraďte obsah následujícím XML:</span><span class="sxs-lookup"><span data-stu-id="3423d-136">Next, open the _templatepack.csproj_ file in your favorite editor and replace the content with the following XML:</span></span>

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

<span data-ttu-id="3423d-137">`<PropertyGroup>` Nastavení v souboru XML výše je rozdělená do tří skupin.</span><span class="sxs-lookup"><span data-stu-id="3423d-137">The `<PropertyGroup>` settings in the XML above is broken into three groups.</span></span> <span data-ttu-id="3423d-138">První skupina se zabývá vlastnosti požadované pro balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="3423d-138">The first group deals with properties required for a NuGet package.</span></span> <span data-ttu-id="3423d-139">Tři `<Package` nastavení muset s NuGet vlastnosti balíčku k identifikaci vašeho balíčku na informačního kanálu NuGet.</span><span class="sxs-lookup"><span data-stu-id="3423d-139">The three `<Package` settings have to do with the NuGet package properties to identify your package on a NuGet feed.</span></span> <span data-ttu-id="3423d-140">Konkrétně `<PacakgeId>` hodnota slouží k odinstalaci šablonovaný balíček s jedním názvem, ne cestu k adresáři.</span><span class="sxs-lookup"><span data-stu-id="3423d-140">Specifically the `<PacakgeId>` value is used to uninstall the template pack with a single name instead of a directory path.</span></span> <span data-ttu-id="3423d-141">To lze také nainstalovat šablonovaný balíček z informačního kanálu NuGet.</span><span class="sxs-lookup"><span data-stu-id="3423d-141">It can also be used to install the template pack from a NuGet feed.</span></span> <span data-ttu-id="3423d-142">Zbývající nastavení, jako `<Title>` a `<Tags>` muset s metadaty zobrazené na NuGet informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="3423d-142">The remaining settings such as `<Title>` and `<Tags>` have to do with metadata displayed on the NuGet feed.</span></span> <span data-ttu-id="3423d-143">Další informace o nastavení NuGet naleznete v tématu [vlastnosti nástroje MSBuild a NuGet](/nuget/reference/msbuild-targets).</span><span class="sxs-lookup"><span data-stu-id="3423d-143">For more information about NuGet settings, see [NuGet and MSBuild properties](/nuget/reference/msbuild-targets).</span></span>

<span data-ttu-id="3423d-144">`<TargetFramework>` Nastavení musí být nastavené tak, aby při spuštění příkazu pack ke kompilaci a aktualizací Service pack projekt bude správně fungovat MSBuild.</span><span class="sxs-lookup"><span data-stu-id="3423d-144">The `<TargetFramework>` setting must be set so that MSBuild will run properly when you run the pack command to compile and pack the project.</span></span>

<span data-ttu-id="3423d-145">Poslední tři nastavení muset nakonfigurovat projekt správně mají být zahrnuty šablony do odpovídající složky v balíčku NuGet pack při jeho vytváření.</span><span class="sxs-lookup"><span data-stu-id="3423d-145">The last three settings have to do with configuring the project correctly to include the templates in the appropriate folder in the NuGet pack when it's created.</span></span>

<span data-ttu-id="3423d-146">`<ItemGroup>` Obsahuje dvě nastavení.</span><span class="sxs-lookup"><span data-stu-id="3423d-146">The `<ItemGroup>` contains two settings.</span></span> <span data-ttu-id="3423d-147">Nejprve je potřeba `<Content>` nastavení zahrnuje všechno, co v _šablony_ složky jako obsah.</span><span class="sxs-lookup"><span data-stu-id="3423d-147">First, the `<Content>` setting includes everything in the _templates_ folder as content.</span></span> <span data-ttu-id="3423d-148">Má také nastavit nevylučovala žádná _bin_ složky nebo _obj_ složky zabránit zkompilovaného kódu (Pokud je testován a kompilaci šablony) nebudou zahrnuty.</span><span class="sxs-lookup"><span data-stu-id="3423d-148">It's also set to exclude any _bin_ folder or _obj_ folder to prevent any compiled code (if you tested and compiled your templates) from being included.</span></span> <span data-ttu-id="3423d-149">Druhý, `<Compile>` vyloučí všechny soubory s kódem v kompilaci bez ohledu na to, kde jsou umístěny.</span><span class="sxs-lookup"><span data-stu-id="3423d-149">Second, the `<Compile>` setting excludes all code files from compiling no matter where they're located.</span></span> <span data-ttu-id="3423d-150">Toto nastavení brání použity k vytvoření balíčku šablony v pokusu o zkompilování kódu v projektu _šablony_ hierarchii složek.</span><span class="sxs-lookup"><span data-stu-id="3423d-150">This setting prevents the project being used to create a template pack from trying to compile the code in the _templates_ folder hierarchy.</span></span>

## <a name="build-and-install"></a><span data-ttu-id="3423d-151">Sestavení a instalace</span><span class="sxs-lookup"><span data-stu-id="3423d-151">Build and install</span></span>

<span data-ttu-id="3423d-152">Uložte tento soubor a pak spusťte příkaz pack</span><span class="sxs-lookup"><span data-stu-id="3423d-152">Save this file and then run the pack command</span></span>

```console
dotnet pack
```

<span data-ttu-id="3423d-153">Tento příkaz se sestavení projektu a vytvořit by měla být v tomto balíčku NuGet _working\bin\Debug_ složky.</span><span class="sxs-lookup"><span data-stu-id="3423d-153">This command will build your project and create a NuGet package in This should be the _working\bin\Debug_ folder.</span></span>

```console
C:\working> dotnet pack
Microsoft (R) Build Engine version 16.2.0-preview-19278-01+d635043bd for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 123.86 ms for C:\working\templatepack.csproj.

  templatepack -> C:\working\bin\Debug\netstandard2.0\templatepack.dll
  Successfully created package 'C:\working\bin\Debug\AdatumCorporation.Utility.Templates.1.0.0.nupkg'.
```

<span data-ttu-id="3423d-154">V dalším kroku instalovat balíček soubor šablony s `dotnet new -i PATH_TO_NUPKG_FILE` příkazu.</span><span class="sxs-lookup"><span data-stu-id="3423d-154">Next, install the template pack file with the `dotnet new -i PATH_TO_NUPKG_FILE` command.</span></span>

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

<span data-ttu-id="3423d-155">Pokud jste nahráli do informačního kanálu NuGet balíčku NuGet, můžete použít `dotnet new -i PACKAGEID` příkazu, kde `PACKAGEID` je stejné jako `<PackageId>` nastavení z _.csproj_ souboru.</span><span class="sxs-lookup"><span data-stu-id="3423d-155">If you uploaded the NuGet package to a NuGet feed, you can use the `dotnet new -i PACKAGEID` command where `PACKAGEID` is the same as the `<PackageId>` setting from the _.csproj_ file.</span></span> <span data-ttu-id="3423d-156">Toto ID balíčku je stejný jako identifikátor balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="3423d-156">This package ID is the same as the NuGet package identifier.</span></span>

## <a name="uninstall-the-template-pack"></a><span data-ttu-id="3423d-157">Odinstalace balíčku šablony</span><span class="sxs-lookup"><span data-stu-id="3423d-157">Uninstall the template pack</span></span>

<span data-ttu-id="3423d-158">Bez ohledu na to, jak jste nainstalovali sadu šablon, buď pomocí _.nupkg_ souboru přímo nebo pomocí NuGet informačního kanálu, odebírá se balíček šablon jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="3423d-158">No matter how you installed the template pack, either with the _.nupkg_ file directly or by NuGet feed, removing a template pack is the same.</span></span> <span data-ttu-id="3423d-159">Použití `<PackageId>` šablony, kterou chcete odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="3423d-159">Use the `<PackageId>` of the template you want to uninstall.</span></span> <span data-ttu-id="3423d-160">Můžete získat seznam šablon, které jsou nainstalovány spuštěním `dotnet new -u` příkazu.</span><span class="sxs-lookup"><span data-stu-id="3423d-160">You can get a list of templates that are installed by running the `dotnet new -u` command.</span></span>

```console
C:\working> dotnet new -u
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

<span data-ttu-id="3423d-161">Spustit `dotnet new -u AdatumCorporation.Utility.Templates` odinstalace šablony.</span><span class="sxs-lookup"><span data-stu-id="3423d-161">Run `dotnet new -u AdatumCorporation.Utility.Templates` to uninstall the template.</span></span> <span data-ttu-id="3423d-162">`dotnet new` Příkaz na výstupu informace nápovědy, která by vynechání šablony, které jste dříve nainstalovali.</span><span class="sxs-lookup"><span data-stu-id="3423d-162">The `dotnet new` command will output help information that should omit the templates you previously installed.</span></span>

<span data-ttu-id="3423d-163">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="3423d-163">Congratulations!</span></span> <span data-ttu-id="3423d-164">jste instaluje a odinstaluje balíček šablon.</span><span class="sxs-lookup"><span data-stu-id="3423d-164">you've installed and uninstalled a template pack.</span></span> 

## <a name="next-steps"></a><span data-ttu-id="3423d-165">Další kroky</span><span class="sxs-lookup"><span data-stu-id="3423d-165">Next steps</span></span>

<span data-ttu-id="3423d-166">Další informace o šablony, většina z nich jste už zjistili, najdete v článku [vlastních šablon pro dotnet nové](../tools/custom-templates.md) článku.</span><span class="sxs-lookup"><span data-stu-id="3423d-166">To learn more about templates, most of which you've already learned, see the [Custom templates for dotnet new](../tools/custom-templates.md) article.</span></span>

* [<span data-ttu-id="3423d-167">úložiště GitHub DotNet/šablonování Wiki</span><span class="sxs-lookup"><span data-stu-id="3423d-167">dotnet/templating GitHub repo Wiki</span></span>](https://github.com/dotnet/templating/wiki)
* [<span data-ttu-id="3423d-168">úložiště GitHub DotNet/dotnet – šablony – ukázky</span><span class="sxs-lookup"><span data-stu-id="3423d-168">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
* [<span data-ttu-id="3423d-169">*Template.JSON* schématu na Store schématu JSON</span><span class="sxs-lookup"><span data-stu-id="3423d-169">*template.json* schema at the JSON Schema Store</span></span>](http://json.schemastore.org/template)
