---
title: Vytvoření šablony položky pro dotnet New-.NET Core CLI
description: Naučte se vytvořit šablonu položky pro příkaz dotnet New. Šablony položek mohou obsahovat libovolný počet souborů.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: 5183781d6a131aa395cf7c1fd8a09e05ed0bd71d
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926155"
---
# <a name="tutorial-create-an-item-template"></a><span data-ttu-id="d8be6-104">Kurz: Vytvoření šablony položky</span><span class="sxs-lookup"><span data-stu-id="d8be6-104">Tutorial: Create an item template</span></span>

<span data-ttu-id="d8be6-105">Pomocí .NET Core můžete vytvářet a nasazovat šablony, které generují projekty, soubory i prostředky.</span><span class="sxs-lookup"><span data-stu-id="d8be6-105">With .NET Core, you can create and deploy templates that generate projects, files, even resources.</span></span> <span data-ttu-id="d8be6-106">Tento kurz je první částí série, která vás seznámí s postupem vytvoření, instalace a odinstalace šablon pro použití s `dotnet new` příkazem.</span><span class="sxs-lookup"><span data-stu-id="d8be6-106">This tutorial is part one of a series that teaches you how to create, install, and uninstall, templates for use with the `dotnet new` command.</span></span>

<span data-ttu-id="d8be6-107">V této části série se naučíte:</span><span class="sxs-lookup"><span data-stu-id="d8be6-107">In this part of the series, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="d8be6-108">Vytvoření třídy pro šablonu položky</span><span class="sxs-lookup"><span data-stu-id="d8be6-108">Create a class for an item template</span></span>
> * <span data-ttu-id="d8be6-109">Vytvoření konfigurační složky a souboru šablony</span><span class="sxs-lookup"><span data-stu-id="d8be6-109">Create the template config folder and file</span></span>
> * <span data-ttu-id="d8be6-110">Nainstalovat šablonu z cesty k souboru</span><span class="sxs-lookup"><span data-stu-id="d8be6-110">Install a template from a file path</span></span>
> * <span data-ttu-id="d8be6-111">Testování šablony položky</span><span class="sxs-lookup"><span data-stu-id="d8be6-111">Test an item template</span></span>
> * <span data-ttu-id="d8be6-112">Odinstalace šablony položky</span><span class="sxs-lookup"><span data-stu-id="d8be6-112">Uninstall an item template</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d8be6-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d8be6-113">Prerequisites</span></span>

* <span data-ttu-id="d8be6-114">[.NET Core 2,2 SDK](https://dotnet.microsoft.com/download) nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="d8be6-114">[.NET Core 2.2 SDK](https://dotnet.microsoft.com/download) or later versions.</span></span>
* <span data-ttu-id="d8be6-115">Přečtěte si referenční článek [vlastní šablony pro dotnet New](../tools/custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="d8be6-115">Read the reference article [Custom templates for dotnet new](../tools/custom-templates.md).</span></span>

  <span data-ttu-id="d8be6-116">Referenční článek vysvětluje základní informace o šablonách a způsobu jejich spojování.</span><span class="sxs-lookup"><span data-stu-id="d8be6-116">The reference article explains the basics about templates and how they're put together.</span></span> <span data-ttu-id="d8be6-117">Některé z těchto informací se tady opakují.</span><span class="sxs-lookup"><span data-stu-id="d8be6-117">Some of this information will be reiterated here.</span></span>

* <span data-ttu-id="d8be6-118">Otevřete terminál a přejděte do složky _working\templates\\_  .</span><span class="sxs-lookup"><span data-stu-id="d8be6-118">Open a terminal and navigate to the _working\templates\\_ folder.</span></span>

## <a name="create-the-required-folders"></a><span data-ttu-id="d8be6-119">Vytvoření požadovaných složek</span><span class="sxs-lookup"><span data-stu-id="d8be6-119">Create the required folders</span></span>

<span data-ttu-id="d8be6-120">Tato série používá pracovní složku, ve které je zdroj šablony obsažený, a "testovací složka" sloužící k testování vašich šablon.</span><span class="sxs-lookup"><span data-stu-id="d8be6-120">This series uses a "working folder" where your template source is contained and a "testing folder" used to test your templates.</span></span> <span data-ttu-id="d8be6-121">Pracovní složka a složka pro testování by měly být ve stejné nadřazené složce.</span><span class="sxs-lookup"><span data-stu-id="d8be6-121">The working folder and testing folder should be under the same parent folder.</span></span>

<span data-ttu-id="d8be6-122">Nejprve vytvořte nadřazenou složku, na které název nezáleží.</span><span class="sxs-lookup"><span data-stu-id="d8be6-122">First, create the parent folder, the name does not matter.</span></span> <span data-ttu-id="d8be6-123">Pak vytvořte podsložku s názvem _Work_.</span><span class="sxs-lookup"><span data-stu-id="d8be6-123">Then, create a subfolder named _working_.</span></span> <span data-ttu-id="d8be6-124">V _pracovní_ složce vytvořte podsložku s názvem _Templates_.</span><span class="sxs-lookup"><span data-stu-id="d8be6-124">Inside of the _working_ folder, create a subfolder named _templates_.</span></span>

<span data-ttu-id="d8be6-125">Dále v nadřazené složce vytvořte složku s názvem _test_.</span><span class="sxs-lookup"><span data-stu-id="d8be6-125">Next, create a folder under the parent folder named _test_.</span></span> <span data-ttu-id="d8be6-126">Struktura složky by měla vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="d8be6-126">The folder structure should look like the following:</span></span>

```console
parent_folder
├───test
└───working
    └───templates
```

## <a name="create-an-item-template"></a><span data-ttu-id="d8be6-127">Vytvoření šablony položky</span><span class="sxs-lookup"><span data-stu-id="d8be6-127">Create an item template</span></span>

<span data-ttu-id="d8be6-128">Šablona položky je konkrétní typ šablony, která obsahuje jeden nebo více souborů.</span><span class="sxs-lookup"><span data-stu-id="d8be6-128">An item template is a specific type of template that contains one or more files.</span></span> <span data-ttu-id="d8be6-129">Tyto typy šablon jsou užitečné, pokud chcete vygenerovat něco jako soubor s konfigurací, kódem nebo souborem řešení.</span><span class="sxs-lookup"><span data-stu-id="d8be6-129">These types of templates are useful when you want to generate something like a config, code, or solution file.</span></span> <span data-ttu-id="d8be6-130">V tomto příkladu vytvoříte třídu, která přidá metodu rozšíření k typu řetězce.</span><span class="sxs-lookup"><span data-stu-id="d8be6-130">In this example, you'll create a class that adds an extension method to the string type.</span></span>

<span data-ttu-id="d8be6-131">V terminálu přejděte do složky _working\templates\\_  a vytvořte novou podsložku s názvem _rozšíření_.</span><span class="sxs-lookup"><span data-stu-id="d8be6-131">In your terminal, navigate to the _working\templates\\_ folder and create a new subfolder named _extensions_.</span></span> <span data-ttu-id="d8be6-132">Zadejte složku.</span><span class="sxs-lookup"><span data-stu-id="d8be6-132">Enter the folder.</span></span>

```console
working
└───templates
    └───extensions
```

<span data-ttu-id="d8be6-133">Vytvořte nový soubor s názvem _CommonExtensions.cs_ a otevřete ho ve svém oblíbeném textovém editoru.</span><span class="sxs-lookup"><span data-stu-id="d8be6-133">Create a new file named _CommonExtensions.cs_ and open it with your favorite text editor.</span></span> <span data-ttu-id="d8be6-134">Tato třída poskytne metodu rozšíření s názvem `Reverse` , která bude měnit obsah řetězce.</span><span class="sxs-lookup"><span data-stu-id="d8be6-134">This class will provide an extension method named `Reverse` that reverses the contents of a string.</span></span> <span data-ttu-id="d8be6-135">Vložte následující kód a soubor uložte:</span><span class="sxs-lookup"><span data-stu-id="d8be6-135">Paste in the following code and save the file:</span></span>

```csharp
using System;

namespace System
{
    public static class StringExtensions
    {
        public static string Reverse(this string value)
        {
            var tempArray = value.ToCharArray();
            Array.Reverse(tempArray);
            return new string(tempArray);
        }
    }
}
```

<span data-ttu-id="d8be6-136">Teď, když máte vytvořený obsah šablony, je nutné vytvořit šablonu config v kořenové složce šablony.</span><span class="sxs-lookup"><span data-stu-id="d8be6-136">Now that you have the content of the template created, you need to create the template config at the root folder of the template.</span></span>

## <a name="create-the-template-config"></a><span data-ttu-id="d8be6-137">Vytvoření šablony konfigurace</span><span class="sxs-lookup"><span data-stu-id="d8be6-137">Create the template config</span></span>

<span data-ttu-id="d8be6-138">Šablony jsou v rozhraní .NET Core rozpoznány pomocí speciální složky a konfiguračního souboru, který se nachází v kořenovém adresáři šablony.</span><span class="sxs-lookup"><span data-stu-id="d8be6-138">Templates are recognized in .NET Core by a special folder and config file that exist at the root of your template.</span></span> <span data-ttu-id="d8be6-139">V tomto kurzu se složka šablony nachází na adrese _working\templates\extensions\\_ .</span><span class="sxs-lookup"><span data-stu-id="d8be6-139">In this tutorial, your template folder is located at _working\templates\extensions\\_.</span></span>

<span data-ttu-id="d8be6-140">Když vytvoříte šablonu, všechny soubory a složky ve složce šablon budou zahrnuty jako součást šablony kromě speciální konfigurační složky.</span><span class="sxs-lookup"><span data-stu-id="d8be6-140">When you create a template, all files and folders in the template folder are included as part of the template except for the special config folder.</span></span> <span data-ttu-id="d8be6-141">Tato konfigurační složka má název _. template. config_.</span><span class="sxs-lookup"><span data-stu-id="d8be6-141">This config folder is named _.template.config_.</span></span>

<span data-ttu-id="d8be6-142">Nejprve vytvořte novou podsložku s názvem _. template. config_a zadejte ji.</span><span class="sxs-lookup"><span data-stu-id="d8be6-142">First, create a new subfolder named _.template.config_, enter it.</span></span> <span data-ttu-id="d8be6-143">Pak vytvořte nový soubor s názvem _template. JSON_.</span><span class="sxs-lookup"><span data-stu-id="d8be6-143">Then, create a new file named _template.json_.</span></span> <span data-ttu-id="d8be6-144">Struktura vaší složky by měla vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="d8be6-144">Your folder structure should look like this:</span></span>

```console
working
└───templates
    └───extensions
        └───.template.config
                template.json
```

<span data-ttu-id="d8be6-145">Otevřete _template. JSON_ s oblíbeným textovým editorem a vložte následující kód JSON a uložte ho:</span><span class="sxs-lookup"><span data-stu-id="d8be6-145">Open the _template.json_ with your favorite text editor and paste in the following JSON code and save it:</span></span>

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Me",
  "classifications": [ "Common", "Code" ],
  "identity": "ExampleTemplate.StringExtensions",
  "name": "Example templates: string extensions",
  "shortName": "stringext",
  "tags": {
    "language": "C#",
    "type": "item"
  }
}
```

<span data-ttu-id="d8be6-146">Tento konfigurační soubor obsahuje všechna nastavení pro šablonu.</span><span class="sxs-lookup"><span data-stu-id="d8be6-146">This config file contains all the settings for your template.</span></span> <span data-ttu-id="d8be6-147">Můžete zobrazit základní nastavení, `name` například a `shortName`, `tags/type` ale existuje také hodnota nastavená na `item`.</span><span class="sxs-lookup"><span data-stu-id="d8be6-147">You can see the basic settings, such as `name` and `shortName`, but there's also a `tags/type` value that is set to `item`.</span></span> <span data-ttu-id="d8be6-148">Tato šablona kategorizuje šablonu jako šablonu položky.</span><span class="sxs-lookup"><span data-stu-id="d8be6-148">This categorizes your template as an item template.</span></span> <span data-ttu-id="d8be6-149">Typ šablony, kterou jste vytvořili, není nijak omezen.</span><span class="sxs-lookup"><span data-stu-id="d8be6-149">There's no restriction on the type of template you create.</span></span> <span data-ttu-id="d8be6-150">Hodnoty `item` a`project` jsou běžné názvy, které doporučuje .NET Core, aby uživatelé mohli snadno filtrovat typ šablony, kterou hledají.</span><span class="sxs-lookup"><span data-stu-id="d8be6-150">The `item` and `project` values are common names that .NET Core recommends so that users can easily filter the type of template they're searching for.</span></span>

<span data-ttu-id="d8be6-151">Položka představuje sloupec **značky** , který se zobrazí při spuštění `dotnet new` a získání seznamu šablon. `classifications`</span><span class="sxs-lookup"><span data-stu-id="d8be6-151">The `classifications` item represents the **tags** column you see when you run `dotnet new` and get a list of templates.</span></span> <span data-ttu-id="d8be6-152">Uživatelé můžou vyhledávat i na základě klasifikačních značek.</span><span class="sxs-lookup"><span data-stu-id="d8be6-152">Users can also search based on classification tags.</span></span> <span data-ttu-id="d8be6-153">Nepleťte `tags` si vlastnost \*v souboru `classifications` . JSON se seznamem značek.</span><span class="sxs-lookup"><span data-stu-id="d8be6-153">Don't confuse the `tags` property in the \*.json file with the `classifications` tags list.</span></span> <span data-ttu-id="d8be6-154">Existují dvě různé věci, které se nazývají podobně.</span><span class="sxs-lookup"><span data-stu-id="d8be6-154">They're two different things unfortunately named similarly.</span></span> <span data-ttu-id="d8be6-155">Úplné schéma pro soubor *template. JSON* najdete v [úložišti schémat JSON](http://json.schemastore.org/template).</span><span class="sxs-lookup"><span data-stu-id="d8be6-155">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="d8be6-156">Další informace o souboru *template. JSON* najdete v tématu [dotnet šablonování wiki](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="d8be6-156">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="d8be6-157">Teď, když máte platný soubor _. template. config/Template. JSON_ , je vaše šablona připravená k instalaci.</span><span class="sxs-lookup"><span data-stu-id="d8be6-157">Now that you have a valid _.template.config/template.json_ file, your template is ready to be installed.</span></span> <span data-ttu-id="d8be6-158">V terminálu přejděte do složky _rozšíření_ a spusťte následující příkaz, který nainstaluje šablonu umístěnou v aktuální složce:</span><span class="sxs-lookup"><span data-stu-id="d8be6-158">In your terminal, navigate to the  _extensions_ folder and run the following command to install the template located at the current folder:</span></span>

* <span data-ttu-id="d8be6-159">**Ve Windows**:`dotnet new -i .\`</span><span class="sxs-lookup"><span data-stu-id="d8be6-159">**On Windows**: `dotnet new -i .\`</span></span>
* <span data-ttu-id="d8be6-160">**V systému Linux nebo MacOS**:`dotnet new -i ./`</span><span class="sxs-lookup"><span data-stu-id="d8be6-160">**On Linux or macOS**: `dotnet new -i ./`</span></span>

<span data-ttu-id="d8be6-161">Tento příkaz vypíše seznam nainstalovaných šablon, které by měly obsahovat vaše.</span><span class="sxs-lookup"><span data-stu-id="d8be6-161">This command outputs the list of templates installed, which should include yours.</span></span>

```console
C:\working\templates\extensions> dotnet new -i .\
Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.

... cut to save space ...

Templates                                         Short Name            Language          Tags
-------------------------------------------------------------------------------------------------------------------------------
Example templates: string extensions              stringext             [C#]              Common/Code
Console Application                               console               [C#], F#, VB      Common/Console
Class library                                     classlib              [C#], F#, VB      Common/Library
WPF Application                                   wpf                   [C#], VB          Common/WPF
Windows Forms (WinForms) Application              winforms              [C#], VB          Common/WinForms
Worker Service                                    worker                [C#]              Common/Worker/Web
```

## <a name="test-the-item-template"></a><span data-ttu-id="d8be6-162">Testování šablony položky</span><span class="sxs-lookup"><span data-stu-id="d8be6-162">Test the item template</span></span>

<span data-ttu-id="d8be6-163">Teď, když máte nainstalovanou šablonu položky, otestujte ji.</span><span class="sxs-lookup"><span data-stu-id="d8be6-163">Now that you have an item template installed, test it.</span></span> <span data-ttu-id="d8be6-164">Přejděte do složky _test/_ Folder a vytvořte novou konzolovou aplikaci pomocí `dotnet new console`nástroje.</span><span class="sxs-lookup"><span data-stu-id="d8be6-164">Navigate to the _test/_ folder and create a new console application with `dotnet new console`.</span></span> <span data-ttu-id="d8be6-165">Tím se vygeneruje pracovní projekt, který lze snadno otestovat `dotnet run` pomocí příkazu.</span><span class="sxs-lookup"><span data-stu-id="d8be6-165">This generates a working project you can easily test with the `dotnet run` command.</span></span>

```console
C:\test> dotnet new console
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\test\test.csproj...
  Restore completed in 54.82 ms for C:\test\test.csproj.

Restore succeeded.
```

```console
C:\test> dotnet run
Hello World!
```

<span data-ttu-id="d8be6-166">Dále spusťte příkaz `dotnet new stringext` , který vygeneruje _CommonExtensions.cs_ ze šablony.</span><span class="sxs-lookup"><span data-stu-id="d8be6-166">Next, run `dotnet new stringext` to generate the _CommonExtensions.cs_ from the template.</span></span>

```console
C:\test> dotnet new stringext
The template "Example templates: string extensions" was created successfully.
```

<span data-ttu-id="d8be6-167">Změňte kód v _program.cs_ a převratte `"Hello World"` řetězec s metodou rozšíření poskytnutou šablonou.</span><span class="sxs-lookup"><span data-stu-id="d8be6-167">Change the code in _Program.cs_ to reverse the `"Hello World"` string with the extension method provided by the template.</span></span>

```csharp
Console.WriteLine("Hello World!".Reverse());
```

<span data-ttu-id="d8be6-168">Spusťte program znovu a uvidíte, že výsledek je obrácený.</span><span class="sxs-lookup"><span data-stu-id="d8be6-168">Run the program again and you'll see that the result is reversed.</span></span>

```console
C:\test> dotnet run
!dlroW olleH
```

<span data-ttu-id="d8be6-169">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="d8be6-169">Congratulations!</span></span> <span data-ttu-id="d8be6-170">Vytvořili jste a nasadili šablonu položky pomocí .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d8be6-170">You created and deployed an item template with .NET Core.</span></span> <span data-ttu-id="d8be6-171">Při přípravě na další část této série kurzů musíte odinstalovat šablonu, kterou jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="d8be6-171">In preparation for the next part of this tutorial series, you must uninstall the template you created.</span></span> <span data-ttu-id="d8be6-172">Přesvědčte se, zda jsou všechny soubory odstraněny také z _testovací_ složky.</span><span class="sxs-lookup"><span data-stu-id="d8be6-172">Make sure to delete all files from the _test_ folder too.</span></span> <span data-ttu-id="d8be6-173">Tím se vrátíte zpět do připraveného stavu pro další hlavní část tohoto kurzu.</span><span class="sxs-lookup"><span data-stu-id="d8be6-173">This will get you back to a clean state ready for the next major section of this tutorial.</span></span>

## <a name="uninstall-the-template"></a><span data-ttu-id="d8be6-174">Odinstalace šablony</span><span class="sxs-lookup"><span data-stu-id="d8be6-174">Uninstall the template</span></span>

<span data-ttu-id="d8be6-175">Vzhledem k tomu, že jste nainstalovali šablonu podle cesty k souboru, je nutné ji odinstalovat s **absolutní** cestou k souboru.</span><span class="sxs-lookup"><span data-stu-id="d8be6-175">Because you installed the template by file path, you must uninstall it with the **absolute** file path.</span></span> <span data-ttu-id="d8be6-176">Seznam nainstalovaných šablon můžete zobrazit spuštěním `dotnet new -u` příkazu.</span><span class="sxs-lookup"><span data-stu-id="d8be6-176">You can see a list of templates installed by running the `dotnet new -u` command.</span></span> <span data-ttu-id="d8be6-177">Vaše šablona by měla být uvedena jako poslední.</span><span class="sxs-lookup"><span data-stu-id="d8be6-177">Your template should be listed last.</span></span> <span data-ttu-id="d8be6-178">Použijte cestu uvedenou k odinstalaci šablony pomocí `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` příkazu.</span><span class="sxs-lookup"><span data-stu-id="d8be6-178">Use the path listed to uninstall your template with the `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` command.</span></span>

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
  C:\working\templates\extensions
    Templates:
      Example templates: string extensions (stringext) C#
```

```console
C:\working> dotnet new -u C:\working\templates\extensions
```

## <a name="next-steps"></a><span data-ttu-id="d8be6-179">Další postup</span><span class="sxs-lookup"><span data-stu-id="d8be6-179">Next steps</span></span>

<span data-ttu-id="d8be6-180">V tomto kurzu jste vytvořili šablonu položky.</span><span class="sxs-lookup"><span data-stu-id="d8be6-180">In this tutorial, you created an item template.</span></span> <span data-ttu-id="d8be6-181">Pokud se chcete dozvědět, jak vytvořit šablonu projektu, pokračujte v této sérii kurzů.</span><span class="sxs-lookup"><span data-stu-id="d8be6-181">To learn how to create a project template, continue this tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d8be6-182">Vytvoření šablony projektu</span><span class="sxs-lookup"><span data-stu-id="d8be6-182">Create a project template</span></span>](cli-templates-create-project-template.md)
