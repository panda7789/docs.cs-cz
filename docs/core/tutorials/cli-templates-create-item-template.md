---
title: Vytvořit šablonu položky pro dotnet new - rozhraní příkazového řádku .NET Core
description: Zjistěte, jak vytvořit šablonu položky pro nový příkaz dotnet. Šablony položek může obsahovat libovolný počet souborů.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: c50aaf413f08c2e4cbe3f8ce8c057e5841067c92
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2019
ms.locfileid: "67877177"
---
# <a name="tutorial-create-an-item-template"></a><span data-ttu-id="f8697-104">Kurz: Vytvořit šablonu položky</span><span class="sxs-lookup"><span data-stu-id="f8697-104">Tutorial: Create an item template</span></span>

<span data-ttu-id="f8697-105">S .NET Core můžete vytvořit a nasadit šablon, které generují projektů, souborů, dokonce i prostředky.</span><span class="sxs-lookup"><span data-stu-id="f8697-105">With .NET Core, you can create and deploy templates that generate projects, files, even resources.</span></span> <span data-ttu-id="f8697-106">Tento kurz je druhou částí série, která vás naučí, jak vytvořit, instalaci a odinstalaci, šablony pro použití se službou `dotnet new` příkazu.</span><span class="sxs-lookup"><span data-stu-id="f8697-106">This tutorial is part one of a series that teaches you how to create, install, and uninstall, templates for use with the `dotnet new` command.</span></span>

<span data-ttu-id="f8697-107">V této části této série se dozvíte, jak:</span><span class="sxs-lookup"><span data-stu-id="f8697-107">In this part of the series, you'll learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="f8697-108">Vytvořte třídu pro šablonu položky</span><span class="sxs-lookup"><span data-stu-id="f8697-108">Create a class for an item template</span></span>
> * <span data-ttu-id="f8697-109">Vytvoření šablony konfigurace složky a souboru</span><span class="sxs-lookup"><span data-stu-id="f8697-109">Create the template config folder and file</span></span>
> * <span data-ttu-id="f8697-110">Instalovat z cesty k souboru šablony</span><span class="sxs-lookup"><span data-stu-id="f8697-110">Install a template from a file path</span></span>
> * <span data-ttu-id="f8697-111">Test šablony položky</span><span class="sxs-lookup"><span data-stu-id="f8697-111">Test an item template</span></span>
> * <span data-ttu-id="f8697-112">Odinstalace šablonu položky</span><span class="sxs-lookup"><span data-stu-id="f8697-112">Uninstall an item template</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f8697-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f8697-113">Prerequisites</span></span>

* <span data-ttu-id="f8697-114">[Sada .NET core 2.2 SDK](https://www.microsoft.com/net/core) nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="f8697-114">[.NET Core 2.2 SDK](https://www.microsoft.com/net/core) or later versions.</span></span>
* <span data-ttu-id="f8697-115">Přečtěte si článek odkaz [vlastních šablon pro dotnet nové](../tools/custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="f8697-115">Read the reference article [Custom templates for dotnet new](../tools/custom-templates.md).</span></span>

  <span data-ttu-id="f8697-116">Odkaz na článek vysvětluje základní informace o šablonách a že jste čeho.</span><span class="sxs-lookup"><span data-stu-id="f8697-116">The reference article explains the basics about templates and how they're put together.</span></span> <span data-ttu-id="f8697-117">Některé z těchto informací se opakoval tady.</span><span class="sxs-lookup"><span data-stu-id="f8697-117">Some of this information will be reiterated here.</span></span>

* <span data-ttu-id="f8697-118">Otevřete terminál a přejděte _working\templates\\_  složky.</span><span class="sxs-lookup"><span data-stu-id="f8697-118">Open a terminal and navigate to the _working\templates\\_ folder.</span></span>

## <a name="create-the-required-folders"></a><span data-ttu-id="f8697-119">Vytvořit požadované složky</span><span class="sxs-lookup"><span data-stu-id="f8697-119">Create the required folders</span></span>

<span data-ttu-id="f8697-120">Tato série používá "pracovní složku" kde je obsažen zdroje šablony a "testování složku" použily k testování vašich šablon.</span><span class="sxs-lookup"><span data-stu-id="f8697-120">This series uses a "working folder" where your template source is contained and a "testing folder" used to test your templates.</span></span> <span data-ttu-id="f8697-121">Pracovní složky a složky testování musí být ve stejné nadřazené složky.</span><span class="sxs-lookup"><span data-stu-id="f8697-121">The working folder and testing folder should be under the same parent folder.</span></span>

<span data-ttu-id="f8697-122">Nejprve vytvořte nadřazené složky, název, nezáleží.</span><span class="sxs-lookup"><span data-stu-id="f8697-122">First, create the parent folder, the name does not matter.</span></span> <span data-ttu-id="f8697-123">Potom vytvořte podsložku s názvem _práce_.</span><span class="sxs-lookup"><span data-stu-id="f8697-123">Then, create a subfolder named _working_.</span></span> <span data-ttu-id="f8697-124">Uvnitř _práce_ složce vytvořte podsložku s názvem _šablony_.</span><span class="sxs-lookup"><span data-stu-id="f8697-124">Inside of the _working_ folder, create a subfolder named _templates_.</span></span>

<span data-ttu-id="f8697-125">V dalším kroku vytvořte složku s nadřazenou složku s názvem _testování_.</span><span class="sxs-lookup"><span data-stu-id="f8697-125">Next, create a folder under the parent folder named _test_.</span></span> <span data-ttu-id="f8697-126">Struktura složek by měl vypadat nějak takto:</span><span class="sxs-lookup"><span data-stu-id="f8697-126">The folder structure should look like the following:</span></span>

```console
parent_folder
├───test
└───working
    └───templates
```

## <a name="create-an-item-template"></a><span data-ttu-id="f8697-127">Vytvořit šablonu položky</span><span class="sxs-lookup"><span data-stu-id="f8697-127">Create an item template</span></span>

<span data-ttu-id="f8697-128">Šablony položky je určitý typ šablony, která obsahuje jeden nebo více souborů.</span><span class="sxs-lookup"><span data-stu-id="f8697-128">An item template is a specific type of template that contains one or more files.</span></span> <span data-ttu-id="f8697-129">Tyto typy šablon jsou užitečné, pokud chcete vygenerovat něco jako config, kód nebo soubor řešení.</span><span class="sxs-lookup"><span data-stu-id="f8697-129">These types of templates are useful when you want to generate something like a config, code, or solution file.</span></span> <span data-ttu-id="f8697-130">V tomto příkladu vytvoříte třídu, která přidá metodu rozšíření k tomuto typu řetězec.</span><span class="sxs-lookup"><span data-stu-id="f8697-130">In this example, you'll create a class that adds an extension method to the string type.</span></span>

<span data-ttu-id="f8697-131">V terminálu přejděte _working\templates\\_  složky a vytvořit novou podsložku s názvem _rozšíření_.</span><span class="sxs-lookup"><span data-stu-id="f8697-131">In your terminal, navigate to the _working\templates\\_ folder and create a new subfolder named _extensions_.</span></span> <span data-ttu-id="f8697-132">Zadejte složku.</span><span class="sxs-lookup"><span data-stu-id="f8697-132">Enter the folder.</span></span>

```console
working
└───templates
    └───extensions
```

<span data-ttu-id="f8697-133">Vytvořte nový soubor s názvem _CommonExtensions.cs_ a otevřete jej pomocí oblíbeného textového editoru.</span><span class="sxs-lookup"><span data-stu-id="f8697-133">Create a new file named _CommonExtensions.cs_ and open it with your favorite text editor.</span></span> <span data-ttu-id="f8697-134">Tato třída bude poskytovat rozšiřující metodu s názvem `Reverse` , který vrátí obsah řetězce.</span><span class="sxs-lookup"><span data-stu-id="f8697-134">This class will provide an extension method named `Reverse` that reverses the contents of a string.</span></span> <span data-ttu-id="f8697-135">Vložte následující kód a soubor uložte:</span><span class="sxs-lookup"><span data-stu-id="f8697-135">Paste in the following code and save the file:</span></span>

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

<span data-ttu-id="f8697-136">Teď, když máte obsah šablony, vytvořili, je potřeba vytvořit šablonu config v kořenové složce šablony.</span><span class="sxs-lookup"><span data-stu-id="f8697-136">Now that you have the content of the template created, you need to create the template config at the root folder of the template.</span></span>

## <a name="create-the-template-config"></a><span data-ttu-id="f8697-137">Vytvoření šablony konfigurace</span><span class="sxs-lookup"><span data-stu-id="f8697-137">Create the template config</span></span>

<span data-ttu-id="f8697-138">Šablony jsou rozpoznány v .NET Core ve zvláštní složce a konfiguračním souboru, který existuje v kořenovém adresáři šablony.</span><span class="sxs-lookup"><span data-stu-id="f8697-138">Templates are recognized in .NET Core by a special folder and config file that exist at the root of your template.</span></span> <span data-ttu-id="f8697-139">V tomto kurzu se nachází na složky šablony _working\templates\extensions\\_ .</span><span class="sxs-lookup"><span data-stu-id="f8697-139">In this tutorial, your template folder is located at _working\templates\extensions\\_.</span></span>

<span data-ttu-id="f8697-140">Když vytvoříte šablonu, všechny soubory a složky ve složce Šablony jsou zahrnuty jako součást šablony s výjimkou složky zvláštní konfigurace.</span><span class="sxs-lookup"><span data-stu-id="f8697-140">When you create a template, all files and folders in the template folder are included as part of the template except for the special config folder.</span></span> <span data-ttu-id="f8697-141">Tato složka config jmenuje _. template.config_.</span><span class="sxs-lookup"><span data-stu-id="f8697-141">This config folder is named _.template.config_.</span></span>

<span data-ttu-id="f8697-142">Nejprve vytvořte novou podsložku s názvem _. template.config_, zadejte ji.</span><span class="sxs-lookup"><span data-stu-id="f8697-142">First, create a new subfolder named _.template.config_, enter it.</span></span> <span data-ttu-id="f8697-143">Vytvořte nový soubor s názvem _template.json_.</span><span class="sxs-lookup"><span data-stu-id="f8697-143">Then, create a new file named _template.json_.</span></span> <span data-ttu-id="f8697-144">Vaše struktura složky by měl vypadat nějak takto:</span><span class="sxs-lookup"><span data-stu-id="f8697-144">Your folder structure should look like this:</span></span>

```console
working
└───templates
    └───extensions
        └───.template.config
                template.json
```

<span data-ttu-id="f8697-145">Otevřít _template.json_ pomocí oblíbeného textového editoru a vložte následující kód JSON kód a uložte ho:</span><span class="sxs-lookup"><span data-stu-id="f8697-145">Open the _template.json_ with your favorite text editor and paste in the following JSON code and save it:</span></span>

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

<span data-ttu-id="f8697-146">Tento konfigurační soubor obsahuje všechna nastavení pro šablonu.</span><span class="sxs-lookup"><span data-stu-id="f8697-146">This config file contains all the settings for your template.</span></span> <span data-ttu-id="f8697-147">Vidíte základní nastavení, jako například `name` a `shortName`, ale k dispozici je také `tags/type` hodnotu, která je nastavena na `item`.</span><span class="sxs-lookup"><span data-stu-id="f8697-147">You can see the basic settings, such as `name` and `shortName`, but there's also a `tags/type` value that is set to `item`.</span></span> <span data-ttu-id="f8697-148">To slouží ke kategorizaci do šablony jako šablonu položky.</span><span class="sxs-lookup"><span data-stu-id="f8697-148">This categorizes your template as an item template.</span></span> <span data-ttu-id="f8697-149">Neexistuje žádné omezení typu šablony, které vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="f8697-149">There's no restriction on the type of template you create.</span></span> <span data-ttu-id="f8697-150">`item` a `project` hodnoty jsou běžné názvy, které doporučuje .NET Core tak, aby uživatelé mohou snadno filtrovat typ šablony, které hledají.</span><span class="sxs-lookup"><span data-stu-id="f8697-150">The `item` and `project` values are common names that .NET Core recommends so that users can easily filter the type of template they're searching for.</span></span>

<span data-ttu-id="f8697-151">`classifications` Položka představuje **značky** sloupce se zobrazí při spuštění `dotnet new` a získat seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="f8697-151">The `classifications` item represents the **tags** column you see when you run `dotnet new` and get a list of templates.</span></span> <span data-ttu-id="f8697-152">Můžete také vyhledat uživatele podle klasifikační značky.</span><span class="sxs-lookup"><span data-stu-id="f8697-152">Users can also search based on classification tags.</span></span> <span data-ttu-id="f8697-153">Nepleťte si `tags` vlastnost \*soubor .json s `classifications` seznam značek.</span><span class="sxs-lookup"><span data-stu-id="f8697-153">Don't confuse the `tags` property in the \*.json file with the `classifications` tags list.</span></span> <span data-ttu-id="f8697-154">Jsou to dvě různé věci bohužel s názvem podobně.</span><span class="sxs-lookup"><span data-stu-id="f8697-154">They're two different things unfortunately named similarly.</span></span> <span data-ttu-id="f8697-155">Úplného schématu pro *template.json* soubor se nachází v umístění [Store schématu JSON](http://json.schemastore.org/template).</span><span class="sxs-lookup"><span data-stu-id="f8697-155">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="f8697-156">Další informace o *template.json* souboru, najdete v článku [dotnet šablonování wiki](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="f8697-156">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="f8697-157">Teď, když máte platný _.template.config/template.json_ souboru je šablona připravena k instalaci.</span><span class="sxs-lookup"><span data-stu-id="f8697-157">Now that you have a valid _.template.config/template.json_ file, your template is ready to be installed.</span></span> <span data-ttu-id="f8697-158">V terminálu přejděte _rozšíření_ složky a spusťte následující příkaz k instalaci šabloně nachází v aktuální složce:</span><span class="sxs-lookup"><span data-stu-id="f8697-158">In your terminal, navigate to the  _extensions_ folder and run the following command to install the template located at the current folder:</span></span>

* <span data-ttu-id="f8697-159">**Na Windows**: `dotnet new -i .\`</span><span class="sxs-lookup"><span data-stu-id="f8697-159">**On Windows**: `dotnet new -i .\`</span></span>
* <span data-ttu-id="f8697-160">**V systému Linux nebo macOS**: `dotnet new -i ./`</span><span class="sxs-lookup"><span data-stu-id="f8697-160">**On Linux or macOS**: `dotnet new -i ./`</span></span>

<span data-ttu-id="f8697-161">Tento příkaz vypíše seznam nainstalované, šablony, které by měl obsahovat vaše.</span><span class="sxs-lookup"><span data-stu-id="f8697-161">This command outputs the list of templates installed, which should include yours.</span></span>

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

## <a name="test-the-item-template"></a><span data-ttu-id="f8697-162">Test šablony položky</span><span class="sxs-lookup"><span data-stu-id="f8697-162">Test the item template</span></span>

<span data-ttu-id="f8697-163">Teď, když máte nainstalované šablony položky, otestujte ji.</span><span class="sxs-lookup"><span data-stu-id="f8697-163">Now that you have an item template installed, test it.</span></span> <span data-ttu-id="f8697-164">Přejděte _testování /_ složky a vytvořte novou konzolovou aplikaci s `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="f8697-164">Navigate to the _test/_ folder and create a new console application with `dotnet new console`.</span></span> <span data-ttu-id="f8697-165">Tím se vytvoří projekt práci snadno můžete otestovat s `dotnet run` příkazu.</span><span class="sxs-lookup"><span data-stu-id="f8697-165">This generates a working project you can easily test with the `dotnet run` command.</span></span>

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

<span data-ttu-id="f8697-166">Potom spusťte `dotnet new stringext` ke generování _CommonExtensions.cs_ ze šablony.</span><span class="sxs-lookup"><span data-stu-id="f8697-166">Next, run `dotnet new stringext` to generate the _CommonExtensions.cs_ from the template.</span></span>

```console
C:\test> dotnet new stringext
The template "Example templates: string extensions" was created successfully.
```

<span data-ttu-id="f8697-167">Změňte kód v _Program.cs_ vrátit `"Hello World"` řetězec pomocí metody rozšíření poskytované šablony.</span><span class="sxs-lookup"><span data-stu-id="f8697-167">Change the code in _Program.cs_ to reverse the `"Hello World"` string with the extension method provided by the template.</span></span>

```csharp
Console.WriteLine("Hello World!".Reverse());
```

<span data-ttu-id="f8697-168">Znovu spusťte program a zobrazí se vám, že výsledek je obrácený.</span><span class="sxs-lookup"><span data-stu-id="f8697-168">Run the program again and you'll see that the result is reversed.</span></span>

```console
C:\test> dotnet run
!dlroW olleH
```

<span data-ttu-id="f8697-169">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="f8697-169">Congratulations!</span></span> <span data-ttu-id="f8697-170">Vytvoření a nasazení šablony položky s .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f8697-170">You created and deployed an item template with .NET Core.</span></span> <span data-ttu-id="f8697-171">Během přípravy na další části této série kurzů je nutné odinstalovat šablona, kterou jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="f8697-171">In preparation for the next part of this tutorial series, you must uninstall the template you created.</span></span> <span data-ttu-id="f8697-172">Ujistěte se, že chcete odstranit všechny soubory z _testování_ složky příliš.</span><span class="sxs-lookup"><span data-stu-id="f8697-172">Make sure to delete all files from the _test_ folder too.</span></span> <span data-ttu-id="f8697-173">Získáte zpět do čistého stavu Připraveno pro další hlavní části tohoto kurzu.</span><span class="sxs-lookup"><span data-stu-id="f8697-173">This will get you back to a clean state ready for the next major section of this tutorial.</span></span>

## <a name="uninstall-the-template"></a><span data-ttu-id="f8697-174">Odinstalace šablony</span><span class="sxs-lookup"><span data-stu-id="f8697-174">Uninstall the template</span></span>

<span data-ttu-id="f8697-175">Vzhledem k tomu, že jste nainstalovali pomocí cesta k souboru šablony, je nutné odinstalovat ji **absolutní** cesta k souboru.</span><span class="sxs-lookup"><span data-stu-id="f8697-175">Because you installed the template by file path, you must uninstall it with the **absolute** file path.</span></span> <span data-ttu-id="f8697-176">Zobrazí se seznam šablon instalaci spuštěním `dotnet new -u` příkazu.</span><span class="sxs-lookup"><span data-stu-id="f8697-176">You can see a list of templates installed by running the `dotnet new -u` command.</span></span> <span data-ttu-id="f8697-177">Vaše šablona by měla být uvedená jako poslední.</span><span class="sxs-lookup"><span data-stu-id="f8697-177">Your template should be listed last.</span></span> <span data-ttu-id="f8697-178">Použití cesty uvedené odinstalace svou šablonu pomocí `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` příkazu.</span><span class="sxs-lookup"><span data-stu-id="f8697-178">Use the path listed to uninstall your template with the `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` command.</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="f8697-179">Další kroky</span><span class="sxs-lookup"><span data-stu-id="f8697-179">Next steps</span></span>

<span data-ttu-id="f8697-180">V tomto kurzu jste vytvořili šablonu položky.</span><span class="sxs-lookup"><span data-stu-id="f8697-180">In this tutorial, you created an item template.</span></span> <span data-ttu-id="f8697-181">Chcete-li zjistěte, jak vytvořit šablonu projektu, pokračujte v této sérii kurzů.</span><span class="sxs-lookup"><span data-stu-id="f8697-181">To learn how to create a project template, continue this tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f8697-182">Vytvoření šablony projektu</span><span class="sxs-lookup"><span data-stu-id="f8697-182">Create a project template</span></span>](cli-templates-create-project-template.md)
