---
title: Vytvoření šablony položky pro dotnet new - .NET Core CLI
description: Přečtěte si, jak vytvořit šablonu položky pro nový příkaz dotnet. Šablony položek mohou obsahovat libovolný počet souborů.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: 5f4038e863d9bb59df470d3516c08fd2ad29c078
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503553"
---
# <a name="tutorial-create-an-item-template"></a><span data-ttu-id="36333-104">Kurz: Vytvoření šablony položky</span><span class="sxs-lookup"><span data-stu-id="36333-104">Tutorial: Create an item template</span></span>

<span data-ttu-id="36333-105">Pomocí rozhraní .NET Core můžete vytvářet a nasazovat šablony, které generují projekty, soubory, dokonce i prostředky.</span><span class="sxs-lookup"><span data-stu-id="36333-105">With .NET Core, you can create and deploy templates that generate projects, files, even resources.</span></span> <span data-ttu-id="36333-106">Tento kurz je první částí řady, která vás naučí vytvářet, instalovat a odinstalovat šablony pro použití s příkazem. `dotnet new`</span><span class="sxs-lookup"><span data-stu-id="36333-106">This tutorial is part one of a series that teaches you how to create, install, and uninstall, templates for use with the `dotnet new` command.</span></span>

<span data-ttu-id="36333-107">V této části seriálu se dozvíte, jak:</span><span class="sxs-lookup"><span data-stu-id="36333-107">In this part of the series, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="36333-108">Vytvoření třídy pro šablonu položky</span><span class="sxs-lookup"><span data-stu-id="36333-108">Create a class for an item template</span></span>
> * <span data-ttu-id="36333-109">Vytvoření konfigurační složky a souboru šablony</span><span class="sxs-lookup"><span data-stu-id="36333-109">Create the template config folder and file</span></span>
> * <span data-ttu-id="36333-110">Instalace šablony z cesty k souboru</span><span class="sxs-lookup"><span data-stu-id="36333-110">Install a template from a file path</span></span>
> * <span data-ttu-id="36333-111">Testování šablony položky</span><span class="sxs-lookup"><span data-stu-id="36333-111">Test an item template</span></span>
> * <span data-ttu-id="36333-112">Odinstalace šablony položky</span><span class="sxs-lookup"><span data-stu-id="36333-112">Uninstall an item template</span></span>

## <a name="prerequisites"></a><span data-ttu-id="36333-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="36333-113">Prerequisites</span></span>

* <span data-ttu-id="36333-114">[Sada .NET Core 2.2 SDK](https://dotnet.microsoft.com/download) nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="36333-114">[.NET Core 2.2 SDK](https://dotnet.microsoft.com/download) or later versions.</span></span>
* <span data-ttu-id="36333-115">Přečtěte si referenční článek [Vlastní šablony pro dotnet new](../tools/custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="36333-115">Read the reference article [Custom templates for dotnet new](../tools/custom-templates.md).</span></span>

  <span data-ttu-id="36333-116">Referenční článek vysvětluje základy o šablonách a o tom, jak jsou sestaveny.</span><span class="sxs-lookup"><span data-stu-id="36333-116">The reference article explains the basics about templates and how they're put together.</span></span> <span data-ttu-id="36333-117">Některé z těchto informací budou zopakovány zde.</span><span class="sxs-lookup"><span data-stu-id="36333-117">Some of this information will be reiterated here.</span></span>

* <span data-ttu-id="36333-118">Otevřete terminál a přejděte do složky _working\templates._</span><span class="sxs-lookup"><span data-stu-id="36333-118">Open a terminal and navigate to the _working\templates_ folder.</span></span>

## <a name="create-the-required-folders"></a><span data-ttu-id="36333-119">Vytvoření požadovaných složek</span><span class="sxs-lookup"><span data-stu-id="36333-119">Create the required folders</span></span>

<span data-ttu-id="36333-120">Tato řada používá "pracovní složku", kde je zdroj šablony obsažen, a "testovací složku" používanou k testování šablon.</span><span class="sxs-lookup"><span data-stu-id="36333-120">This series uses a "working folder" where your template source is contained and a "testing folder" used to test your templates.</span></span> <span data-ttu-id="36333-121">Pracovní složka a testovací složka by měly být pod stejnou nadřazenou složkou.</span><span class="sxs-lookup"><span data-stu-id="36333-121">The working folder and testing folder should be under the same parent folder.</span></span>

<span data-ttu-id="36333-122">Nejprve vytvořte nadřazenou složku, na názvu nezáleží.</span><span class="sxs-lookup"><span data-stu-id="36333-122">First, create the parent folder, the name does not matter.</span></span> <span data-ttu-id="36333-123">Potom vytvořte podsložku s názvem _Pracovní_.</span><span class="sxs-lookup"><span data-stu-id="36333-123">Then, create a subfolder named _working_.</span></span> <span data-ttu-id="36333-124">Uvnitř _pracovní_ složky vytvořte podsložku s názvem _šablony_.</span><span class="sxs-lookup"><span data-stu-id="36333-124">Inside of the _working_ folder, create a subfolder named _templates_.</span></span>

<span data-ttu-id="36333-125">Dále vytvořte složku pod nadřazenou složku s názvem _Test_.</span><span class="sxs-lookup"><span data-stu-id="36333-125">Next, create a folder under the parent folder named _test_.</span></span> <span data-ttu-id="36333-126">Struktura složek by měla vypadat takto.</span><span class="sxs-lookup"><span data-stu-id="36333-126">The folder structure should look like the following.</span></span>

```console
parent_folder
├───test
└───working
    └───templates
```

## <a name="create-an-item-template"></a><span data-ttu-id="36333-127">Vytvoření šablony položky</span><span class="sxs-lookup"><span data-stu-id="36333-127">Create an item template</span></span>

<span data-ttu-id="36333-128">Šablona položky je specifický typ šablony, který obsahuje jeden nebo více souborů.</span><span class="sxs-lookup"><span data-stu-id="36333-128">An item template is a specific type of template that contains one or more files.</span></span> <span data-ttu-id="36333-129">Tyto typy šablon jsou užitečné, pokud chcete vygenerovat něco jako config, kód nebo soubor řešení.</span><span class="sxs-lookup"><span data-stu-id="36333-129">These types of templates are useful when you want to generate something like a config, code, or solution file.</span></span> <span data-ttu-id="36333-130">V tomto příkladu vytvoříte třídu, která přidá metodu rozšíření k typu řetězce.</span><span class="sxs-lookup"><span data-stu-id="36333-130">In this example, you'll create a class that adds an extension method to the string type.</span></span>

<span data-ttu-id="36333-131">V terminálu přejděte do složky _Working\templates_ a vytvořte novou podsložku s názvem _Extensions_.</span><span class="sxs-lookup"><span data-stu-id="36333-131">In your terminal, navigate to the _working\templates_ folder and create a new subfolder named _extensions_.</span></span> <span data-ttu-id="36333-132">Zadejte složku.</span><span class="sxs-lookup"><span data-stu-id="36333-132">Enter the folder.</span></span>

```console
working
└───templates
    └───extensions
```

<span data-ttu-id="36333-133">Vytvořte nový soubor s názvem _CommonExtensions.cs_ a otevřete jej pomocí oblíbeného textového editoru.</span><span class="sxs-lookup"><span data-stu-id="36333-133">Create a new file named _CommonExtensions.cs_ and open it with your favorite text editor.</span></span> <span data-ttu-id="36333-134">Tato třída bude poskytovat `Reverse` metodu rozšíření s názvem, která obrátí obsah řetězce.</span><span class="sxs-lookup"><span data-stu-id="36333-134">This class will provide an extension method named `Reverse` that reverses the contents of a string.</span></span> <span data-ttu-id="36333-135">Vložte do následujícího kódu a uložte soubor:</span><span class="sxs-lookup"><span data-stu-id="36333-135">Paste in the following code and save the file:</span></span>

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

<span data-ttu-id="36333-136">Nyní, když máte obsah šablony vytvořené, musíte vytvořit konfiguraci šablony v kořenové složce šablony.</span><span class="sxs-lookup"><span data-stu-id="36333-136">Now that you have the content of the template created, you need to create the template config at the root folder of the template.</span></span>

## <a name="create-the-template-config"></a><span data-ttu-id="36333-137">Vytvoření konfigurace šablony</span><span class="sxs-lookup"><span data-stu-id="36333-137">Create the template config</span></span>

<span data-ttu-id="36333-138">Šablony jsou v rozhraní .NET Core rozpoznány speciální složkou a konfiguračním souborem, které existují v kořenovém adresáři šablony.</span><span class="sxs-lookup"><span data-stu-id="36333-138">Templates are recognized in .NET Core by a special folder and config file that exist at the root of your template.</span></span> <span data-ttu-id="36333-139">V tomto kurzu je složka šablony umístěna v _working\templates\extensions_.</span><span class="sxs-lookup"><span data-stu-id="36333-139">In this tutorial, your template folder is located at _working\templates\extensions_.</span></span>

<span data-ttu-id="36333-140">Při vytváření šablony jsou všechny soubory a složky ve složce šablony zahrnuty jako součást šablony s výjimkou speciální složky konfigurace.</span><span class="sxs-lookup"><span data-stu-id="36333-140">When you create a template, all files and folders in the template folder are included as part of the template except for the special config folder.</span></span> <span data-ttu-id="36333-141">Tato složka konfigurace má název _.template.config_.</span><span class="sxs-lookup"><span data-stu-id="36333-141">This config folder is named _.template.config_.</span></span>

<span data-ttu-id="36333-142">Nejprve vytvořte novou podsložku s názvem _.template.config_, zadejte ji.</span><span class="sxs-lookup"><span data-stu-id="36333-142">First, create a new subfolder named _.template.config_, enter it.</span></span> <span data-ttu-id="36333-143">Potom vytvořte nový soubor s názvem _template.json_.</span><span class="sxs-lookup"><span data-stu-id="36333-143">Then, create a new file named _template.json_.</span></span> <span data-ttu-id="36333-144">Struktura složek by měla vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="36333-144">Your folder structure should look like this:</span></span>

```console
working
└───templates
    └───extensions
        └───.template.config
                template.json
```

<span data-ttu-id="36333-145">Otevřete _template.json_ s vaším oblíbeným textovým editorem a vložte do následujícího kódu JSON a uložte jej.</span><span class="sxs-lookup"><span data-stu-id="36333-145">Open the _template.json_ with your favorite text editor and paste in the following JSON code and save it.</span></span>

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

<span data-ttu-id="36333-146">Tento konfigurační soubor obsahuje všechna nastavení šablony.</span><span class="sxs-lookup"><span data-stu-id="36333-146">This config file contains all the settings for your template.</span></span> <span data-ttu-id="36333-147">Můžete zobrazit základní nastavení, `name` například a `shortName`, ale `tags/type` je zde `item`také hodnota, která je nastavena na .</span><span class="sxs-lookup"><span data-stu-id="36333-147">You can see the basic settings, such as `name` and `shortName`, but there's also a `tags/type` value that is set to `item`.</span></span> <span data-ttu-id="36333-148">Tím se šablona zařazuje do kategorií jako šablona položky.</span><span class="sxs-lookup"><span data-stu-id="36333-148">This categorizes your template as an item template.</span></span> <span data-ttu-id="36333-149">Neexistuje žádné omezení typu šablony, kterou vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="36333-149">There's no restriction on the type of template you create.</span></span> <span data-ttu-id="36333-150">Hodnoty `item` `project` a jsou běžné názvy, které doporučuje rozhraní .NET Core, aby uživatelé mohli snadno filtrovat typ šablony, kterou hledají.</span><span class="sxs-lookup"><span data-stu-id="36333-150">The `item` and `project` values are common names that .NET Core recommends so that users can easily filter the type of template they're searching for.</span></span>

<span data-ttu-id="36333-151">Položka `classifications` představuje sloupec **značek,** který `dotnet new` se zobrazí při spuštění a získáte seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="36333-151">The `classifications` item represents the **tags** column you see when you run `dotnet new` and get a list of templates.</span></span> <span data-ttu-id="36333-152">Uživatelé mohou také vyhledávat na základě klasifikačních značek.</span><span class="sxs-lookup"><span data-stu-id="36333-152">Users can also search based on classification tags.</span></span> <span data-ttu-id="36333-153">Nezaměňujte `tags` vlastnost v \*souboru JSON `classifications` se seznamem značek.</span><span class="sxs-lookup"><span data-stu-id="36333-153">Don't confuse the `tags` property in the \*.json file with the `classifications` tags list.</span></span> <span data-ttu-id="36333-154">Jsou to dvě různé věci, bohužel pojmenované podobně.</span><span class="sxs-lookup"><span data-stu-id="36333-154">They're two different things unfortunately named similarly.</span></span> <span data-ttu-id="36333-155">Úplné schéma souboru *template.json* se nachází v [úložišti schématu JSON](http://json.schemastore.org/template).</span><span class="sxs-lookup"><span data-stu-id="36333-155">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="36333-156">Další informace o souboru *template.json* naleznete [na wiki dotnet templating](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="36333-156">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="36333-157">Nyní, když máte platný soubor _.template.config/template.json,_ je šablona připravena k instalaci.</span><span class="sxs-lookup"><span data-stu-id="36333-157">Now that you have a valid _.template.config/template.json_ file, your template is ready to be installed.</span></span> <span data-ttu-id="36333-158">V terminálu přejděte do složky _rozšíření_ a spusťte následující příkaz pro instalaci šablony umístěné v aktuální složce:</span><span class="sxs-lookup"><span data-stu-id="36333-158">In your terminal, navigate to the  _extensions_ folder and run the following command to install the template located at the current folder:</span></span>

* <span data-ttu-id="36333-159">**Ve Windows**:`dotnet new -i .\`</span><span class="sxs-lookup"><span data-stu-id="36333-159">**On Windows**: `dotnet new -i .\`</span></span>
* <span data-ttu-id="36333-160">**Na Linuxu nebo macOS**:`dotnet new -i ./`</span><span class="sxs-lookup"><span data-stu-id="36333-160">**On Linux or macOS**: `dotnet new -i ./`</span></span>

<span data-ttu-id="36333-161">Tento příkaz vypíše seznam nainstalovaných šablon, které by měly zahrnovat vaše.</span><span class="sxs-lookup"><span data-stu-id="36333-161">This command outputs the list of templates installed, which should include yours.</span></span>

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

## <a name="test-the-item-template"></a><span data-ttu-id="36333-162">Otestovat šablonu položky</span><span class="sxs-lookup"><span data-stu-id="36333-162">Test the item template</span></span>

<span data-ttu-id="36333-163">Nyní, když máte nainstalovanou šablonu položky, otestujte ji.</span><span class="sxs-lookup"><span data-stu-id="36333-163">Now that you have an item template installed, test it.</span></span> <span data-ttu-id="36333-164">Přejděte do _složky test/_ a `dotnet new console`vytvořte novou konzolovou aplikaci s .</span><span class="sxs-lookup"><span data-stu-id="36333-164">Navigate to the _test/_ folder and create a new console application with `dotnet new console`.</span></span> <span data-ttu-id="36333-165">Tím se vygeneruje pracovní projekt, `dotnet run` který můžete snadno testovat pomocí příkazu.</span><span class="sxs-lookup"><span data-stu-id="36333-165">This generates a working project you can easily test with the `dotnet run` command.</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="36333-166">Získáte výstup podobný následující.</span><span class="sxs-lookup"><span data-stu-id="36333-166">You get output similar to the following.</span></span>

```console
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\test\test.csproj...
  Restore completed in 54.82 ms for C:\test\test.csproj.

Restore succeeded.
```

<span data-ttu-id="36333-167">Spusťte projekt s.</span><span class="sxs-lookup"><span data-stu-id="36333-167">Run the project with.</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="36333-168">Získáte následující výstup.</span><span class="sxs-lookup"><span data-stu-id="36333-168">You get the following output.</span></span>

```console
Hello World!
```

<span data-ttu-id="36333-169">Dále spusťte `dotnet new stringext` a vygenerujte _CommonExtensions.cs_ ze šablony.</span><span class="sxs-lookup"><span data-stu-id="36333-169">Next, run `dotnet new stringext` to generate the _CommonExtensions.cs_ from the template.</span></span>

```dotnetcli
dotnet new stringext
```

<span data-ttu-id="36333-170">Získáte následující výstup.</span><span class="sxs-lookup"><span data-stu-id="36333-170">You get the following output.</span></span>

```console
The template "Example templates: string extensions" was created successfully.
```

<span data-ttu-id="36333-171">Změňte kód _Program.cs_ v Program.cs `"Hello World"` stornovat řetězec s metodou rozšíření poskytované šablonou.</span><span class="sxs-lookup"><span data-stu-id="36333-171">Change the code in _Program.cs_ to reverse the `"Hello World"` string with the extension method provided by the template.</span></span>

```csharp
Console.WriteLine("Hello World!".Reverse());
```

<span data-ttu-id="36333-172">Spusťte program znovu a uvidíte, že výsledek je obrácený.</span><span class="sxs-lookup"><span data-stu-id="36333-172">Run the program again and you'll see that the result is reversed.</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="36333-173">Získáte následující výstup.</span><span class="sxs-lookup"><span data-stu-id="36333-173">You get the following output.</span></span>

```console
!dlroW olleH
```

<span data-ttu-id="36333-174">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="36333-174">Congratulations!</span></span> <span data-ttu-id="36333-175">Vytvořili jste a nasadili šablonu položky s jádrem .NET Core.</span><span class="sxs-lookup"><span data-stu-id="36333-175">You created and deployed an item template with .NET Core.</span></span> <span data-ttu-id="36333-176">Při přípravě na další část této série kurzů je nutné odinstalovat šablonu, kterou jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="36333-176">In preparation for the next part of this tutorial series, you must uninstall the template you created.</span></span> <span data-ttu-id="36333-177">Ujistěte se, že odstranit všechny soubory z _testovací_ složky příliš.</span><span class="sxs-lookup"><span data-stu-id="36333-177">Make sure to delete all files from the _test_ folder too.</span></span> <span data-ttu-id="36333-178">Tím se vrátíte do čistého stavu připraveného pro další hlavní část tohoto kurzu.</span><span class="sxs-lookup"><span data-stu-id="36333-178">This will get you back to a clean state ready for the next major section of this tutorial.</span></span>

## <a name="uninstall-the-template"></a><span data-ttu-id="36333-179">Odinstalace šablony</span><span class="sxs-lookup"><span data-stu-id="36333-179">Uninstall the template</span></span>

<span data-ttu-id="36333-180">Vzhledem k tomu, že jste šablonu nainstalovali podle cesty k souboru, je nutné ji odinstalovat s **absolutní** cestou k souboru.</span><span class="sxs-lookup"><span data-stu-id="36333-180">Because you installed the template by file path, you must uninstall it with the **absolute** file path.</span></span> <span data-ttu-id="36333-181">Seznam šablon nainstalovaných můžete zobrazit spuštěním příkazu. `dotnet new -u`</span><span class="sxs-lookup"><span data-stu-id="36333-181">You can see a list of templates installed by running the `dotnet new -u` command.</span></span> <span data-ttu-id="36333-182">Šablona by měla být uvedena jako poslední.</span><span class="sxs-lookup"><span data-stu-id="36333-182">Your template should be listed last.</span></span> <span data-ttu-id="36333-183">Pomocí uvedené cesty odinstalujte `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` šablonu pomocí příkazu.</span><span class="sxs-lookup"><span data-stu-id="36333-183">Use the path listed to uninstall your template with the `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` command.</span></span>

```dotnetcli
dotnet new -u
```

<span data-ttu-id="36333-184">Získáte výstup podobný následující.</span><span class="sxs-lookup"><span data-stu-id="36333-184">You get output similar to the following.</span></span>

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
  C:\working\templates\extensions
    Templates:
      Example templates: string extensions (stringext) C#
```

<span data-ttu-id="36333-185">Chcete-li šablonu odinstalovat, spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="36333-185">To uninstall a template, run the following command.</span></span>

```dotnetcli
dotnet new -u C:\working\templates\extensions
```

## <a name="next-steps"></a><span data-ttu-id="36333-186">Další kroky</span><span class="sxs-lookup"><span data-stu-id="36333-186">Next steps</span></span>

<span data-ttu-id="36333-187">V tomto kurzu jste vytvořili šablonu položky.</span><span class="sxs-lookup"><span data-stu-id="36333-187">In this tutorial, you created an item template.</span></span> <span data-ttu-id="36333-188">Chcete-li se dozvědět, jak vytvořit šablonu projektu, pokračujte v této sérii kurzů.</span><span class="sxs-lookup"><span data-stu-id="36333-188">To learn how to create a project template, continue this tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="36333-189">Vytvoření šablony projektu</span><span class="sxs-lookup"><span data-stu-id="36333-189">Create a project template</span></span>](cli-templates-create-project-template.md)
