---
title: Vytvořit šablonu projektu pro dotnet New
description: Naučte se vytvořit šablonu projektu pro příkaz dotnet New.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: 3455720d729f813d9b6f32e433adffa4dc40dce4
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926136"
---
# <a name="tutorial-create-a-project-template"></a><span data-ttu-id="12475-103">Kurz: Vytvoření šablony projektu</span><span class="sxs-lookup"><span data-stu-id="12475-103">Tutorial: Create a project template</span></span>

<span data-ttu-id="12475-104">Pomocí .NET Core můžete vytvářet a nasazovat šablony, které generují projekty, soubory i prostředky.</span><span class="sxs-lookup"><span data-stu-id="12475-104">With .NET Core, you can create and deploy templates that generate projects, files, even resources.</span></span> <span data-ttu-id="12475-105">Tento kurz je druhou částí série, která vás seznámí s postupem vytvoření, instalace a odinstalace šablon pro použití s `dotnet new` příkazem.</span><span class="sxs-lookup"><span data-stu-id="12475-105">This tutorial is part two of a series that teaches you how to create, install, and uninstall, templates for use with the `dotnet new` command.</span></span>

<span data-ttu-id="12475-106">V této části série se naučíte:</span><span class="sxs-lookup"><span data-stu-id="12475-106">In this part of the series you'll learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="12475-107">Vytvoření prostředků šablony projektu</span><span class="sxs-lookup"><span data-stu-id="12475-107">Create the resources of a project template</span></span>
> * <span data-ttu-id="12475-108">Vytvoření konfigurační složky a souboru šablony</span><span class="sxs-lookup"><span data-stu-id="12475-108">Create the template config folder and file</span></span>
> * <span data-ttu-id="12475-109">Nainstalovat šablonu z cesty k souboru</span><span class="sxs-lookup"><span data-stu-id="12475-109">Install a template from a file path</span></span>
> * <span data-ttu-id="12475-110">Testování šablony položky</span><span class="sxs-lookup"><span data-stu-id="12475-110">Test an item template</span></span>
> * <span data-ttu-id="12475-111">Odinstalace šablony položky</span><span class="sxs-lookup"><span data-stu-id="12475-111">Uninstall an item template</span></span>

## <a name="prerequisites"></a><span data-ttu-id="12475-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="12475-112">Prerequisites</span></span>

* <span data-ttu-id="12475-113">Vyplňte [část 1](cli-templates-create-item-template.md) této série kurzů.</span><span class="sxs-lookup"><span data-stu-id="12475-113">Complete [part 1](cli-templates-create-item-template.md) of this tutorial series.</span></span>
* <span data-ttu-id="12475-114">Otevřete terminál a přejděte do složky _working\templates\\_  .</span><span class="sxs-lookup"><span data-stu-id="12475-114">Open a terminal and navigate to the _working\templates\\_ folder.</span></span>

## <a name="create-a-project-template"></a><span data-ttu-id="12475-115">Vytvoření šablony projektu</span><span class="sxs-lookup"><span data-stu-id="12475-115">Create a project template</span></span>

<span data-ttu-id="12475-116">Projektové šablony vytvářejí projekty připravené k spuštění, které uživatelům usnadňují spuštění pracovní sady kódu.</span><span class="sxs-lookup"><span data-stu-id="12475-116">Project templates produce ready-to-run projects that make it easy for users to start with a working set of code.</span></span> <span data-ttu-id="12475-117">.NET Core obsahuje několik šablon projektů, jako je například Konzolová aplikace nebo knihovna tříd.</span><span class="sxs-lookup"><span data-stu-id="12475-117">.NET Core includes a few project templates such as a console application or a class library.</span></span> <span data-ttu-id="12475-118">V tomto příkladu vytvoříte nový projekt konzoly, který povolí C# 8,0 a vytvoří `async main` vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="12475-118">In this example, you'll create a new console project that enables C# 8.0 and produces an `async main` entry point.</span></span>

<span data-ttu-id="12475-119">V terminálu přejděte do složky _working\templates\\_  a vytvořte novou podsložku s názvem _consoleasync_.</span><span class="sxs-lookup"><span data-stu-id="12475-119">In your terminal, navigate to the _working\templates\\_ folder and create a new subfolder named _consoleasync_.</span></span> <span data-ttu-id="12475-120">Zadejte podsložku a spusťte `dotnet new console` příkaz pro vygenerování standardní konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="12475-120">Enter the subfolder and run `dotnet new console` to generate the standard console application.</span></span> <span data-ttu-id="12475-121">Pokud chcete vytvořit novou šablonu, budete upravovat soubory vytvořené touto šablonou.</span><span class="sxs-lookup"><span data-stu-id="12475-121">You'll be editing the files produced by this template to create a new template.</span></span>

```console
working
└───templates
    └───consoleasync
            consoleasync.csproj
            Program.cs
```

## <a name="modify-programcs"></a><span data-ttu-id="12475-122">Upravit Program.cs</span><span class="sxs-lookup"><span data-stu-id="12475-122">Modify Program.cs</span></span>

<span data-ttu-id="12475-123">Otevřete soubor _program.cs_ .</span><span class="sxs-lookup"><span data-stu-id="12475-123">Open up the _program.cs_ file.</span></span> <span data-ttu-id="12475-124">Projekt konzoly nepoužívá asynchronní vstupní bod, takže ho přidáváme.</span><span class="sxs-lookup"><span data-stu-id="12475-124">The console project doesn't use an asynchronous entry point, so let's add that.</span></span> <span data-ttu-id="12475-125">Změňte kód na následující a uložte soubor:</span><span class="sxs-lookup"><span data-stu-id="12475-125">Change your code to the following and save the file:</span></span>

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

## <a name="modify-consoleasynccsproj"></a><span data-ttu-id="12475-126">Upravit consoleasync. csproj</span><span class="sxs-lookup"><span data-stu-id="12475-126">Modify consoleasync.csproj</span></span>

<span data-ttu-id="12475-127">Pojďme aktualizovat C# jazykovou verzi, kterou projekt používá, na verzi 8,0.</span><span class="sxs-lookup"><span data-stu-id="12475-127">Let's update the C# language version the project uses to version 8.0.</span></span> <span data-ttu-id="12475-128">Upravte soubor _consoleasync. csproj_ a přidejte `<LangVersion>` nastavení do `<PropertyGroup>` uzlu.</span><span class="sxs-lookup"><span data-stu-id="12475-128">Edit the _consoleasync.csproj_ file and add the `<LangVersion>` setting to a `<PropertyGroup>` node.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.2</TargetFramework>

    <LangVersion>8.0</LangVersion>

  </PropertyGroup>
  
</Project>
```

## <a name="build-the-project"></a><span data-ttu-id="12475-129">Sestavení projektu</span><span class="sxs-lookup"><span data-stu-id="12475-129">Build the project</span></span>

<span data-ttu-id="12475-130">Před dokončením šablony projektu byste ji měli otestovat, abyste se ujistili, že kompiluje a běží správně.</span><span class="sxs-lookup"><span data-stu-id="12475-130">Before you complete a project template, you should test it to make sure it compiles and runs correctly.</span></span> <span data-ttu-id="12475-131">V terminálu spusťte `dotnet run` příkaz a měl by se zobrazit následující výstup:</span><span class="sxs-lookup"><span data-stu-id="12475-131">In your terminal, run the `dotnet run` command and you should see the following output:</span></span>

```console
C:\working\templates\consoleasync> dotnet run
Hello World with C# 8.0!
```

<span data-ttu-id="12475-132">Můžete odstranit složky _obj_ a _bin_ vytvořené pomocí `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="12475-132">You can delete the _obj_ and _bin_ folders created by using `dotnet run`.</span></span> <span data-ttu-id="12475-133">Odstranění těchto souborů zajistí, že šablona obsahuje jenom soubory, které souvisejí s vaší šablonou, a ne žádné soubory, které mají za následek akci sestavení.</span><span class="sxs-lookup"><span data-stu-id="12475-133">Deleting these files ensures your template only includes the files related to your template and not any files that result of a build action.</span></span>

<span data-ttu-id="12475-134">Teď, když máte vytvořený obsah šablony, je nutné vytvořit šablonu config v kořenové složce šablony.</span><span class="sxs-lookup"><span data-stu-id="12475-134">Now that you have the content of the template created, you need to create the template config at the root folder of the template.</span></span>

## <a name="create-the-template-config"></a><span data-ttu-id="12475-135">Vytvoření šablony konfigurace</span><span class="sxs-lookup"><span data-stu-id="12475-135">Create the template config</span></span>

<span data-ttu-id="12475-136">Šablony jsou v rozhraní .NET Core rozpoznány pomocí speciální složky a konfiguračního souboru, který se nachází v kořenovém adresáři šablony.</span><span class="sxs-lookup"><span data-stu-id="12475-136">Templates are recognized in .NET Core by a special folder and config file that exist at the root of your template.</span></span> <span data-ttu-id="12475-137">V tomto kurzu se složka šablony nachází na adrese _working\templates\consoleasync\\_ .</span><span class="sxs-lookup"><span data-stu-id="12475-137">In this tutorial, your template folder is located at _working\templates\consoleasync\\_.</span></span>

<span data-ttu-id="12475-138">Když vytvoříte šablonu, všechny soubory a složky ve složce šablon budou zahrnuty jako součást šablony kromě speciální konfigurační složky.</span><span class="sxs-lookup"><span data-stu-id="12475-138">When you create a template, all files and folders in the template folder are included as part of the template except for the special config folder.</span></span> <span data-ttu-id="12475-139">Tato konfigurační složka má název _. template. config_.</span><span class="sxs-lookup"><span data-stu-id="12475-139">This config folder is named _.template.config_.</span></span>

<span data-ttu-id="12475-140">Nejprve vytvořte novou podsložku s názvem _. template. config_a zadejte ji.</span><span class="sxs-lookup"><span data-stu-id="12475-140">First, create a new subfolder named _.template.config_, enter it.</span></span> <span data-ttu-id="12475-141">Pak vytvořte nový soubor s názvem _template. JSON_.</span><span class="sxs-lookup"><span data-stu-id="12475-141">Then, create a new file named _template.json_.</span></span> <span data-ttu-id="12475-142">Struktura vaší složky by měla vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="12475-142">Your folder structure should look like this:</span></span>

```console
working
└───templates
    └───consoleasync
        └───.template.config
                template.json
```

<span data-ttu-id="12475-143">Otevřete _template. JSON_ s oblíbeným textovým editorem a vložte následující kód JSON a uložte ho:</span><span class="sxs-lookup"><span data-stu-id="12475-143">Open the _template.json_ with your favorite text editor and paste in the following json code and save it:</span></span>

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

<span data-ttu-id="12475-144">Tento konfigurační soubor obsahuje všechna nastavení pro šablonu.</span><span class="sxs-lookup"><span data-stu-id="12475-144">This config file contains all of the settings for your template.</span></span> <span data-ttu-id="12475-145">Můžete zobrazit základní nastavení, `name` například a `shortName` , `tags/type` ale také existuje hodnota, která je nastavena na `project`.</span><span class="sxs-lookup"><span data-stu-id="12475-145">You can see the basic settings such as `name` and `shortName` but also there's a `tags/type` value that's set to `project`.</span></span> <span data-ttu-id="12475-146">Tím označíte šablonu jako šablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="12475-146">This designates your template as a project template.</span></span> <span data-ttu-id="12475-147">Typ šablony, kterou jste vytvořili, není nijak omezen.</span><span class="sxs-lookup"><span data-stu-id="12475-147">There's no restriction on the type of template you create.</span></span> <span data-ttu-id="12475-148">Hodnoty `item` a`project` jsou běžné názvy, které doporučuje .NET Core, aby uživatelé mohli snadno filtrovat typ šablony, kterou hledají.</span><span class="sxs-lookup"><span data-stu-id="12475-148">The `item` and `project` values are common names that .NET Core recommends so that users can easily filter the type of template they're searching for.</span></span>

<span data-ttu-id="12475-149">Položka představuje sloupec **značky** , který se zobrazí při spuštění `dotnet new` a získání seznamu šablon. `classifications`</span><span class="sxs-lookup"><span data-stu-id="12475-149">The `classifications` item represents the **tags** column you see when you run `dotnet new` and get a list of templates.</span></span> <span data-ttu-id="12475-150">Uživatelé můžou vyhledávat i na základě klasifikačních značek.</span><span class="sxs-lookup"><span data-stu-id="12475-150">Users can also search based on classification tags.</span></span> <span data-ttu-id="12475-151">Nepleťte `tags` si vlastnost v souboru JSON `classifications` se seznamem značek.</span><span class="sxs-lookup"><span data-stu-id="12475-151">Don't confuse the `tags` property in the json file with the `classifications` tags list.</span></span> <span data-ttu-id="12475-152">Existují dvě různé věci, které se nazývají podobně.</span><span class="sxs-lookup"><span data-stu-id="12475-152">They're two different things unfortunately named similarly.</span></span> <span data-ttu-id="12475-153">Úplné schéma pro soubor *template. JSON* najdete v [úložišti schémat JSON](http://json.schemastore.org/template).</span><span class="sxs-lookup"><span data-stu-id="12475-153">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="12475-154">Další informace o souboru *template. JSON* najdete v tématu [dotnet šablonování wiki](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="12475-154">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="12475-155">Teď, když máte platný soubor _. template. config/Template. JSON_ , je vaše šablona připravená k instalaci.</span><span class="sxs-lookup"><span data-stu-id="12475-155">Now that you have a valid _.template.config/template.json_ file, your template is ready to be installed.</span></span> <span data-ttu-id="12475-156">Před instalací šablony nezapomeňte odstranit všechny složky a soubory s dalšími soubory, které nechcete zahrnout do šablony, jako jsou složky _bin_ nebo _obj_ .</span><span class="sxs-lookup"><span data-stu-id="12475-156">Before you install the template, make sure that you delete any extra files folders and files you don't want included in your template, like the _bin_ or _obj_ folders.</span></span> <span data-ttu-id="12475-157">V terminálu přejděte do složky _consoleasync_ a spusťte `dotnet new -i .\` instalaci šablony umístěné v aktuální složce.</span><span class="sxs-lookup"><span data-stu-id="12475-157">In your terminal, navigate to the _consoleasync_ folder and run `dotnet new -i .\` to install the template located at the current folder.</span></span> <span data-ttu-id="12475-158">Pokud používáte operační systém Linux nebo MacOS, použijte lomítko: `dotnet new -i ./`.</span><span class="sxs-lookup"><span data-stu-id="12475-158">If you're using a Linux or MacOS operating system, use a forward slash: `dotnet new -i ./`.</span></span>

<span data-ttu-id="12475-159">Tento příkaz vypíše seznam nainstalovaných šablon, které by měly obsahovat vaše.</span><span class="sxs-lookup"><span data-stu-id="12475-159">This command outputs the list of templates installed, which should include yours.</span></span>

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

### <a name="test-the-project-template"></a><span data-ttu-id="12475-160">Testování šablony projektu</span><span class="sxs-lookup"><span data-stu-id="12475-160">Test the project template</span></span>

<span data-ttu-id="12475-161">Teď, když máte nainstalovanou šablonu položky, otestujte ji.</span><span class="sxs-lookup"><span data-stu-id="12475-161">Now that you have an item template installed, test it.</span></span> <span data-ttu-id="12475-162">Přejděte do složky _test_ a vytvořte novou konzolovou aplikaci pomocí `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="12475-162">Navigate to the _test_ folder and create a new console application with `dotnet new console`.</span></span> <span data-ttu-id="12475-163">Tím se vygeneruje pracovní projekt, který lze snadno otestovat `dotnet run` pomocí příkazu.</span><span class="sxs-lookup"><span data-stu-id="12475-163">This generates a working project you can easily test with the `dotnet run` command.</span></span>

```console
C:\test> dotnet new consoleasync
The template "Example templates: async project" was created successfully.
```

```console
C:\test> dotnet run
Hello World with C# 8.0!
```

<span data-ttu-id="12475-164">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="12475-164">Congratulations!</span></span> <span data-ttu-id="12475-165">Vytvořili jste a nasadili šablonu projektu pomocí .NET Core.</span><span class="sxs-lookup"><span data-stu-id="12475-165">You created and deployed a project template with .NET Core.</span></span> <span data-ttu-id="12475-166">Při přípravě na další část této série kurzů musíte odinstalovat šablonu, kterou jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="12475-166">In preparation for the next part of this tutorial series, you must uninstall the template you created.</span></span> <span data-ttu-id="12475-167">Přesvědčte se, zda jsou všechny soubory odstraněny také z _testovací_ složky.</span><span class="sxs-lookup"><span data-stu-id="12475-167">Make sure to delete all files from the _test_ folder too.</span></span> <span data-ttu-id="12475-168">Tím se vrátíte zpět do připraveného stavu pro další hlavní část tohoto kurzu.</span><span class="sxs-lookup"><span data-stu-id="12475-168">This will get you back to a clean state ready for the next major section of this tutorial.</span></span>

### <a name="uninstall-the-template"></a><span data-ttu-id="12475-169">Odinstalace šablony</span><span class="sxs-lookup"><span data-stu-id="12475-169">Uninstall the template</span></span>

<span data-ttu-id="12475-170">Vzhledem k tomu, že jste šablonu nainstalovali pomocí cesty k souboru, je nutné ji odinstalovat s **absolutní** cestou k souboru.</span><span class="sxs-lookup"><span data-stu-id="12475-170">Because you installed the template by using a file path, you must uninstall it with the **absolute** file path.</span></span> <span data-ttu-id="12475-171">Seznam nainstalovaných šablon můžete zobrazit spuštěním `dotnet new -u` příkazu.</span><span class="sxs-lookup"><span data-stu-id="12475-171">You can see a list of templates installed by running the `dotnet new -u` command.</span></span> <span data-ttu-id="12475-172">Vaše šablona by měla být uvedena jako poslední.</span><span class="sxs-lookup"><span data-stu-id="12475-172">Your template should be listed last.</span></span> <span data-ttu-id="12475-173">Použijte cestu uvedenou k odinstalaci šablony pomocí `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` příkazu.</span><span class="sxs-lookup"><span data-stu-id="12475-173">Use the path listed to uninstall your template with the `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` command.</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="12475-174">Další kroky</span><span class="sxs-lookup"><span data-stu-id="12475-174">Next steps</span></span>

<span data-ttu-id="12475-175">V tomto kurzu jste vytvořili šablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="12475-175">In this tutorial, you created a project template.</span></span> <span data-ttu-id="12475-176">Chcete-li se dozvědět, jak zabalit šablony položek a projektů do snadno použitelného souboru, pokračujte v této sérii kurzů.</span><span class="sxs-lookup"><span data-stu-id="12475-176">To learn how to package both the item and project templates into an easy-to-use file, continue this tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="12475-177">Vytvoření sady šablon</span><span class="sxs-lookup"><span data-stu-id="12475-177">Create a template pack</span></span>](cli-templates-create-template-pack.md)
