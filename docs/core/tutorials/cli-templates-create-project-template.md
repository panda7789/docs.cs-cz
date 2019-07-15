---
title: Vytvoření nové šablony projektu pro dotnet
description: Zjistěte, jak vytvořit šablonu projektu pro nový příkaz dotnet.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: 31a6189c0126d6dff000bb84978c1527dbe4e2ae
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2019
ms.locfileid: "67877180"
---
# <a name="tutorial-create-a-project-template"></a><span data-ttu-id="7246a-103">Kurz: Vytvoření šablony projektu</span><span class="sxs-lookup"><span data-stu-id="7246a-103">Tutorial: Create a project template</span></span>

<span data-ttu-id="7246a-104">S .NET Core můžete vytvořit a nasadit šablon, které generují projektů, souborů, dokonce i prostředky.</span><span class="sxs-lookup"><span data-stu-id="7246a-104">With .NET Core, you can create and deploy templates that generate projects, files, even resources.</span></span> <span data-ttu-id="7246a-105">Tento kurz je druhá část série, která vás naučí, jak vytvořit, instalaci a odinstalaci, šablony pro použití se službou `dotnet new` příkazu.</span><span class="sxs-lookup"><span data-stu-id="7246a-105">This tutorial is part two of a series that teaches you how to create, install, and uninstall, templates for use with the `dotnet new` command.</span></span>

<span data-ttu-id="7246a-106">V této části této série se dozvíte jak:</span><span class="sxs-lookup"><span data-stu-id="7246a-106">In this part of the series you'll learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="7246a-107">Vytvoření prostředků šablony projektu</span><span class="sxs-lookup"><span data-stu-id="7246a-107">Create the resources of a project template</span></span>
> * <span data-ttu-id="7246a-108">Vytvoření šablony konfigurace složky a souboru</span><span class="sxs-lookup"><span data-stu-id="7246a-108">Create the template config folder and file</span></span>
> * <span data-ttu-id="7246a-109">Instalovat z cesty k souboru šablony</span><span class="sxs-lookup"><span data-stu-id="7246a-109">Install a template from a file path</span></span>
> * <span data-ttu-id="7246a-110">Test šablony položky</span><span class="sxs-lookup"><span data-stu-id="7246a-110">Test an item template</span></span>
> * <span data-ttu-id="7246a-111">Odinstalace šablonu položky</span><span class="sxs-lookup"><span data-stu-id="7246a-111">Uninstall an item template</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7246a-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7246a-112">Prerequisites</span></span>

* <span data-ttu-id="7246a-113">Kompletní [1. část](cli-templates-create-item-template.md) této série kurzů.</span><span class="sxs-lookup"><span data-stu-id="7246a-113">Complete [part 1](cli-templates-create-item-template.md) of this tutorial series.</span></span>
* <span data-ttu-id="7246a-114">Otevřete terminál a přejděte _working\templates\\_  složky.</span><span class="sxs-lookup"><span data-stu-id="7246a-114">Open a terminal and navigate to the _working\templates\\_ folder.</span></span>

## <a name="create-a-project-template"></a><span data-ttu-id="7246a-115">Vytvoření šablony projektu</span><span class="sxs-lookup"><span data-stu-id="7246a-115">Create a project template</span></span>

<span data-ttu-id="7246a-116">Projekt šablony vytvořit připravené ke spuštění projektů, které usnadňují uživatelům začít s funkční sadu kódu.</span><span class="sxs-lookup"><span data-stu-id="7246a-116">Project templates produce ready-to-run projects that make it easy for users to start with a working set of code.</span></span> <span data-ttu-id="7246a-117">.NET core obsahuje několik šablon projektů například konzolové aplikace nebo knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="7246a-117">.NET Core includes a few project templates such as a console application or a class library.</span></span> <span data-ttu-id="7246a-118">V tomto příkladu vytvoříte nový projekt konzoly, která umožňuje C# 8.0 a vytváří `async main` vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="7246a-118">In this example, you'll create a new console project that enables C# 8.0 and produces an `async main` entry point.</span></span>

<span data-ttu-id="7246a-119">V terminálu přejděte _working\templates\\_  složky a vytvořit novou podsložku s názvem _consoleasync_.</span><span class="sxs-lookup"><span data-stu-id="7246a-119">In your terminal, navigate to the _working\templates\\_ folder and create a new subfolder named _consoleasync_.</span></span> <span data-ttu-id="7246a-120">Zadejte název podsložky a spusťte `dotnet new console` ke generování standardní konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="7246a-120">Enter the subfolder and run `dotnet new console` to generate the standard console application.</span></span> <span data-ttu-id="7246a-121">Budete upravovat soubory vytvořené pomocí této šablony můžete vytvořit novou šablonu.</span><span class="sxs-lookup"><span data-stu-id="7246a-121">You'll be editing the files produced by this template to create a new template.</span></span>

```console
working
└───templates
    └───consoleasync
            consoleasync.csproj
            Program.cs
```

## <a name="modify-programcs"></a><span data-ttu-id="7246a-122">Úprava souboru Program.cs</span><span class="sxs-lookup"><span data-stu-id="7246a-122">Modify Program.cs</span></span>

<span data-ttu-id="7246a-123">Otevřete _program.cs_ souboru.</span><span class="sxs-lookup"><span data-stu-id="7246a-123">Open up the _program.cs_ file.</span></span> <span data-ttu-id="7246a-124">Projekt konzolové není použít asynchronní vstupní bod, Pojďme přidat.</span><span class="sxs-lookup"><span data-stu-id="7246a-124">The console project doesn't use an asynchronous entry point, so let's add that.</span></span> <span data-ttu-id="7246a-125">Změňte následující kód a soubor uložte:</span><span class="sxs-lookup"><span data-stu-id="7246a-125">Change your code to the following and save the file:</span></span>

```csharp
using System;
using System.Threading.Tasks;

namespace consoleasync
{
    class Program
    {
        static async Task Main(string[] args)
        {
            await Console.Out.WriteAsync("Hello World with C# 8.0!");
        }
    }
}
```

## <a name="modify-consoleasynccsproj"></a><span data-ttu-id="7246a-126">Upravit consoleasync.csproj</span><span class="sxs-lookup"><span data-stu-id="7246a-126">Modify consoleasync.csproj</span></span>

<span data-ttu-id="7246a-127">Aktualizaci Pojďme C# jazykovou verzi, že projekt používá verzi 8.0.</span><span class="sxs-lookup"><span data-stu-id="7246a-127">Let's update the C# language version the project uses to version 8.0.</span></span> <span data-ttu-id="7246a-128">Upravit _consoleasync.csproj_ a přidejte `<LangVersion>` nastavení na hodnotu `<PropertyGroup>` uzlu.</span><span class="sxs-lookup"><span data-stu-id="7246a-128">Edit the _consoleasync.csproj_ file and add the `<LangVersion>` setting to a `<PropertyGroup>` node.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.2</TargetFramework>

    <LangVersion>8.0</LangVersion>

  </PropertyGroup>
  
</Project>
```

## <a name="build-the-project"></a><span data-ttu-id="7246a-129">Sestavení projektu</span><span class="sxs-lookup"><span data-stu-id="7246a-129">Build the project</span></span>

<span data-ttu-id="7246a-130">Před dokončením šablonu projektu, měli byste otestovat a ujistit se, že se správně zkompiluje a spustí.</span><span class="sxs-lookup"><span data-stu-id="7246a-130">Before you complete a project template, you should test it to make sure it compiles and runs correctly.</span></span> <span data-ttu-id="7246a-131">V terminálu spusťte `dotnet run` příkazu by se měla zobrazit následující výstup:</span><span class="sxs-lookup"><span data-stu-id="7246a-131">In your terminal, run the `dotnet run` command and you should see the following output:</span></span>

```console
C:\working\templates\consoleasync> dotnet run
Hello World with C# 8.0!
```

<span data-ttu-id="7246a-132">Můžete odstranit _obj_ a _bin_ složky vytvořené využitím `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="7246a-132">You can delete the _obj_ and _bin_ folders created by using `dotnet run`.</span></span> <span data-ttu-id="7246a-133">Odstranění těchto souborů zajišťuje, že šablony obsahuje jenom soubory související s vaší šablony a ne všechny soubory tento výsledek akce sestavení.</span><span class="sxs-lookup"><span data-stu-id="7246a-133">Deleting these files ensures your template only includes the files related to your template and not any files that result of a build action.</span></span>

<span data-ttu-id="7246a-134">Teď, když máte obsah šablony, vytvořili, je potřeba vytvořit šablonu config v kořenové složce šablony.</span><span class="sxs-lookup"><span data-stu-id="7246a-134">Now that you have the content of the template created, you need to create the template config at the root folder of the template.</span></span>

## <a name="create-the-template-config"></a><span data-ttu-id="7246a-135">Vytvoření šablony konfigurace</span><span class="sxs-lookup"><span data-stu-id="7246a-135">Create the template config</span></span>

<span data-ttu-id="7246a-136">Šablony jsou rozpoznány v .NET Core ve zvláštní složce a konfiguračním souboru, který existuje v kořenovém adresáři šablony.</span><span class="sxs-lookup"><span data-stu-id="7246a-136">Templates are recognized in .NET Core by a special folder and config file that exist at the root of your template.</span></span> <span data-ttu-id="7246a-137">V tomto kurzu se nachází na složky šablony _working\templates\consoleasync\\_ .</span><span class="sxs-lookup"><span data-stu-id="7246a-137">In this tutorial, your template folder is located at _working\templates\consoleasync\\_.</span></span>

<span data-ttu-id="7246a-138">Když vytvoříte šablonu, všechny soubory a složky ve složce Šablony jsou zahrnuty jako součást šablony s výjimkou složky zvláštní konfigurace.</span><span class="sxs-lookup"><span data-stu-id="7246a-138">When you create a template, all files and folders in the template folder are included as part of the template except for the special config folder.</span></span> <span data-ttu-id="7246a-139">Tato složka config jmenuje _. template.config_.</span><span class="sxs-lookup"><span data-stu-id="7246a-139">This config folder is named _.template.config_.</span></span>

<span data-ttu-id="7246a-140">Nejprve vytvořte novou podsložku s názvem _. template.config_, zadejte ji.</span><span class="sxs-lookup"><span data-stu-id="7246a-140">First, create a new subfolder named _.template.config_, enter it.</span></span> <span data-ttu-id="7246a-141">Vytvořte nový soubor s názvem _template.json_.</span><span class="sxs-lookup"><span data-stu-id="7246a-141">Then, create a new file named _template.json_.</span></span> <span data-ttu-id="7246a-142">Vaše struktura složky by měl vypadat nějak takto:</span><span class="sxs-lookup"><span data-stu-id="7246a-142">Your folder structure should look like this:</span></span>

```console
working
└───templates
    └───consoleasync
        └───.template.config
                template.json
```

<span data-ttu-id="7246a-143">Otevřít _template.json_ pomocí oblíbeného textového editoru a vložte následující kód json kód a uložte ho:</span><span class="sxs-lookup"><span data-stu-id="7246a-143">Open the _template.json_ with your favorite text editor and paste in the following json code and save it:</span></span>

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Me",
  "classifications": [ "Common", "Console", "C#8" ],
  "identity": "ExampleTemplate.AsyncProject",
  "name": "Example templates: async project",
  "shortName": "consoleasync",
  "tags": {
    "language": "C#",
    "type": "project"
  }
}
```

<span data-ttu-id="7246a-144">Tento konfigurační soubor obsahuje všechna nastavení pro šablonu.</span><span class="sxs-lookup"><span data-stu-id="7246a-144">This config file contains all of the settings for your template.</span></span> <span data-ttu-id="7246a-145">Vidíte základní nastavení, jako `name` a `shortName` ale také `tags/type` hodnotu, která je nastavena na `project`.</span><span class="sxs-lookup"><span data-stu-id="7246a-145">You can see the basic settings such as `name` and `shortName` but also there's a `tags/type` value that's set to `project`.</span></span> <span data-ttu-id="7246a-146">To označí jako šablona projektu šablony.</span><span class="sxs-lookup"><span data-stu-id="7246a-146">This designates your template as a project template.</span></span> <span data-ttu-id="7246a-147">Neexistuje žádné omezení typu šablony, které vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="7246a-147">There's no restriction on the type of template you create.</span></span> <span data-ttu-id="7246a-148">`item` a `project` hodnoty jsou běžné názvy, které doporučuje .NET Core tak, aby uživatelé mohou snadno filtrovat typ šablony, které hledají.</span><span class="sxs-lookup"><span data-stu-id="7246a-148">The `item` and `project` values are common names that .NET Core recommends so that users can easily filter the type of template they're searching for.</span></span>

<span data-ttu-id="7246a-149">`classifications` Položka představuje **značky** sloupce se zobrazí při spuštění `dotnet new` a získat seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="7246a-149">The `classifications` item represents the **tags** column you see when you run `dotnet new` and get a list of templates.</span></span> <span data-ttu-id="7246a-150">Můžete také vyhledat uživatele podle klasifikační značky.</span><span class="sxs-lookup"><span data-stu-id="7246a-150">Users can also search based on classification tags.</span></span> <span data-ttu-id="7246a-151">Nepleťte si `tags` vlastnost v souboru json `classifications` seznam značek.</span><span class="sxs-lookup"><span data-stu-id="7246a-151">Don't confuse the `tags` property in the json file with the `classifications` tags list.</span></span> <span data-ttu-id="7246a-152">Jsou to dvě různé věci bohužel s názvem podobně.</span><span class="sxs-lookup"><span data-stu-id="7246a-152">They're two different things unfortunately named similarly.</span></span> <span data-ttu-id="7246a-153">Úplného schématu pro *template.json* soubor se nachází v umístění [Store schématu JSON](http://json.schemastore.org/template).</span><span class="sxs-lookup"><span data-stu-id="7246a-153">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="7246a-154">Další informace o *template.json* souboru, najdete v článku [dotnet šablonování wiki](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="7246a-154">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="7246a-155">Teď, když máte platný _.template.config/template.json_ souboru je šablona připravena k instalaci.</span><span class="sxs-lookup"><span data-stu-id="7246a-155">Now that you have a valid _.template.config/template.json_ file, your template is ready to be installed.</span></span> <span data-ttu-id="7246a-156">Před instalací šablonu, ujistěte se, že jste odstranili všechny další soubory složky a soubory už nechcete součástí šablony, jako je třeba _bin_ nebo _obj_ složek.</span><span class="sxs-lookup"><span data-stu-id="7246a-156">Before you install the template, make sure that you delete any extra files folders and files you don't want included in your template, like the _bin_ or _obj_ folders.</span></span> <span data-ttu-id="7246a-157">V terminálu přejděte _consoleasync_ složky a spusťte `dotnet new -i .\` instalace umístěný ve složce aktuální šablony.</span><span class="sxs-lookup"><span data-stu-id="7246a-157">In your terminal, navigate to the _consoleasync_ folder and run `dotnet new -i .\` to install the template located at the current folder.</span></span> <span data-ttu-id="7246a-158">Pokud používáte operační systém Linux nebo MacOS, použít lomítko: `dotnet new -i ./`.</span><span class="sxs-lookup"><span data-stu-id="7246a-158">If you're using a Linux or MacOS operating system, use a forward slash: `dotnet new -i ./`.</span></span>

<span data-ttu-id="7246a-159">Tento příkaz vypíše seznam nainstalované, šablony, které by měl obsahovat vaše.</span><span class="sxs-lookup"><span data-stu-id="7246a-159">This command outputs the list of templates installed, which should include yours.</span></span>

```console
C:\working\templates\consoleasync> dotnet new -i .\
Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.

... cut to save space ...

Templates                                         Short Name            Language          Tags
-------------------------------------------------------------------------------------------------------------------------------
Console Application                               console               [C#], F#, VB      Common/Console
Example templates: async project                  consoleasync          [C#]              Common/Console/C#8
Class library                                     classlib              [C#], F#, VB      Common/Library
WPF Application                                   wpf                   [C#], VB          Common/WPF
Windows Forms (WinForms) Application              winforms              [C#], VB          Common/WinForms
Worker Service                                    worker                [C#]              Common/Worker/Web
```

### <a name="test-the-project-template"></a><span data-ttu-id="7246a-160">Test šablony projektu</span><span class="sxs-lookup"><span data-stu-id="7246a-160">Test the project template</span></span>

<span data-ttu-id="7246a-161">Teď, když máte nainstalované šablony položky, otestujte ji.</span><span class="sxs-lookup"><span data-stu-id="7246a-161">Now that you have an item template installed, test it.</span></span> <span data-ttu-id="7246a-162">Přejděte _testování_ složky a vytvořte novou konzolovou aplikaci s `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="7246a-162">Navigate to the _test_ folder and create a new console application with `dotnet new console`.</span></span> <span data-ttu-id="7246a-163">Tím se vytvoří projekt práci snadno můžete otestovat s `dotnet run` příkazu.</span><span class="sxs-lookup"><span data-stu-id="7246a-163">This generates a working project you can easily test with the `dotnet run` command.</span></span>

```console
C:\test> dotnet new consoleasync
The template "Example templates: async project" was created successfully.
```

```console
C:\test> dotnet run
Hello World with C# 8.0!
```

<span data-ttu-id="7246a-164">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="7246a-164">Congratulations!</span></span> <span data-ttu-id="7246a-165">Vytvoření a nasazení šablonu projektu s .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7246a-165">You created and deployed a project template with .NET Core.</span></span> <span data-ttu-id="7246a-166">Během přípravy na další části této série kurzů je nutné odinstalovat šablona, kterou jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="7246a-166">In preparation for the next part of this tutorial series, you must uninstall the template you created.</span></span> <span data-ttu-id="7246a-167">Ujistěte se, že chcete odstranit všechny soubory z _testování_ složky příliš.</span><span class="sxs-lookup"><span data-stu-id="7246a-167">Make sure to delete all files from the _test_ folder too.</span></span> <span data-ttu-id="7246a-168">Získáte zpět do čistého stavu Připraveno pro další hlavní části tohoto kurzu.</span><span class="sxs-lookup"><span data-stu-id="7246a-168">This will get you back to a clean state ready for the next major section of this tutorial.</span></span>

### <a name="uninstall-the-template"></a><span data-ttu-id="7246a-169">Odinstalace šablony</span><span class="sxs-lookup"><span data-stu-id="7246a-169">Uninstall the template</span></span>

<span data-ttu-id="7246a-170">Vzhledem k tomu, že jste nainstalovali šablony pomocí cesty k souboru, je nutné odinstalovat ji **absolutní** cesta k souboru.</span><span class="sxs-lookup"><span data-stu-id="7246a-170">Because you installed the template by using a file path, you must uninstall it with the **absolute** file path.</span></span> <span data-ttu-id="7246a-171">Zobrazí se seznam šablon instalaci spuštěním `dotnet new -u` příkazu.</span><span class="sxs-lookup"><span data-stu-id="7246a-171">You can see a list of templates installed by running the `dotnet new -u` command.</span></span> <span data-ttu-id="7246a-172">Vaše šablona by měla být uvedená jako poslední.</span><span class="sxs-lookup"><span data-stu-id="7246a-172">Your template should be listed last.</span></span> <span data-ttu-id="7246a-173">Použití cesty uvedené odinstalace svou šablonu pomocí `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` příkazu.</span><span class="sxs-lookup"><span data-stu-id="7246a-173">Use the path listed to uninstall your template with the `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` command.</span></span>

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
  C:\working\templates\consoleasync
    Templates:
      Example templates: async project (consoleasync) C#
```

```console
C:\working> dotnet new -u C:\working\templates\consoleasync
```

## <a name="next-steps"></a><span data-ttu-id="7246a-174">Další postup</span><span class="sxs-lookup"><span data-stu-id="7246a-174">Next steps</span></span>

<span data-ttu-id="7246a-175">V tomto kurzu jste vytvořili šablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="7246a-175">In this tutorial, you created a project template.</span></span> <span data-ttu-id="7246a-176">Chcete-li získat informace o balíček šablon položek a projektů do souboru snadným ovládáním, pokračujte v této sérii kurzů.</span><span class="sxs-lookup"><span data-stu-id="7246a-176">To learn how to package both the item and project templates into an easy-to-use file, continue this tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7246a-177">Vytvoření balíčku šablony</span><span class="sxs-lookup"><span data-stu-id="7246a-177">Create a template pack</span></span>](cli-templates-create-template-pack.md)
