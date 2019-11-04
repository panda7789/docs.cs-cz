---
title: Vlastní šablony pro dotnet New
description: Seznamte se s vlastními šablonami pro jakýkoli typ projektu nebo souborů .NET.
author: thraka
ms.date: 06/14/2019
ms.openlocfilehash: 8e1ac4ca21a8a90ad0f7c9bd3dd11281eb4a6e02
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73420881"
---
# <a name="custom-templates-for-dotnet-new"></a><span data-ttu-id="dc024-103">Vlastní šablony pro dotnet New</span><span class="sxs-lookup"><span data-stu-id="dc024-103">Custom templates for dotnet new</span></span>

<span data-ttu-id="dc024-104">[.NET Core SDK](https://dotnet.microsoft.com/download) obsahuje mnoho šablon, které jsou už nainstalované a připravené k použití.</span><span class="sxs-lookup"><span data-stu-id="dc024-104">The [.NET Core SDK](https://dotnet.microsoft.com/download) comes with many templates already installed and ready for you to use.</span></span> <span data-ttu-id="dc024-105">[Příkaz`dotnet new`](dotnet-new.md) nepoužívá pouze způsob, jak šablonu používat, ale také postup instalace a odinstalace šablon.</span><span class="sxs-lookup"><span data-stu-id="dc024-105">The [`dotnet new` command](dotnet-new.md) isn't only the way to use a template, but also how to install and uninstall templates.</span></span> <span data-ttu-id="dc024-106">Počínaje rozhraním .NET Core 2,0 můžete vytvořit vlastní šablony pro jakýkoli typ projektu, například aplikace, služby, nástroje nebo knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="dc024-106">Starting with .NET Core 2.0, you can create your own custom templates for any type of project, such as an app, service, tool, or class library.</span></span> <span data-ttu-id="dc024-107">Můžete dokonce vytvořit šablonu, která bude vytvářet výstup jednoho nebo více nezávislých souborů, například konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="dc024-107">You can even create a template that outputs one or more independent files, such as a configuration file.</span></span>

<span data-ttu-id="dc024-108">Vlastní šablony můžete nainstalovat z balíčku NuGet v jakémkoli kanálu NuGet, odkazování na soubor NuGet *. nupkg* nebo zadáním adresáře systému souborů, který šablonu obsahuje.</span><span class="sxs-lookup"><span data-stu-id="dc024-108">You can install custom templates from a NuGet package on any NuGet feed, by referencing a NuGet *.nupkg* file directly, or by specifying a file system directory that contains the template.</span></span> <span data-ttu-id="dc024-109">Modul šablon nabízí funkce, které umožňují nahradit hodnoty, zahrnout a vyloučit soubory a provádět vlastní operace zpracování při použití šablony.</span><span class="sxs-lookup"><span data-stu-id="dc024-109">The template engine offers features that allow you to replace values, include and exclude files, and execute custom processing operations when your template is used.</span></span>

<span data-ttu-id="dc024-110">Modul šablon je open source a online úložiště kódu je v [dotnet/šablonování](https://github.com/dotnet/templating/) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="dc024-110">The template engine is open source, and the online code repository is at [dotnet/templating](https://github.com/dotnet/templating/) on GitHub.</span></span> <span data-ttu-id="dc024-111">Ukázky šablon najdete v úložišti [dotnet/dotnet-Template-Samples](https://github.com/dotnet/dotnet-template-samples) .</span><span class="sxs-lookup"><span data-stu-id="dc024-111">Visit the [dotnet/dotnet-template-samples](https://github.com/dotnet/dotnet-template-samples) repo for samples of templates.</span></span> <span data-ttu-id="dc024-112">Další šablony, včetně šablon od třetích stran, najdete v [dostupných šablonách pro dotnet New](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="dc024-112">More templates, including templates from third parties, are found at [Available templates for dotnet new](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) on GitHub.</span></span> <span data-ttu-id="dc024-113">Další informace o vytváření a používání vlastních šablon najdete v tématu [jak vytvořit vlastní šablony pro dotnet New](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/) a [wiki pro úložiště GitHubu a šablonování](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="dc024-113">For more information about creating and using custom templates, see [How to create your own templates for dotnet new](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/) and the [dotnet/templating GitHub repo Wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="dc024-114">Pokud chcete postupovat podle návodu a vytvořit šablonu, přečtěte si článek [Vytvoření vlastní šablony pro dotnet nový](../tutorials/cli-templates-create-item-template.md) kurz.</span><span class="sxs-lookup"><span data-stu-id="dc024-114">To follow a walkthrough and create a template, see the [Create a custom template for dotnet new](../tutorials/cli-templates-create-item-template.md) tutorial.</span></span>

### <a name="net-default-templates"></a><span data-ttu-id="dc024-115">Výchozí šablony rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="dc024-115">.NET default templates</span></span>

<span data-ttu-id="dc024-116">Při instalaci [.NET Core SDK](https://dotnet.microsoft.com/download)obdržíte spoustu předdefinovaných šablon pro vytváření projektů a souborů, včetně konzolových aplikací, knihoven tříd, projektů testování částí, ASP.NET Corech aplikací (včetně [úhlů](https://angular.io/) a [reagujících](https://facebook.github.io/react/) projektů). a konfigurační soubory.</span><span class="sxs-lookup"><span data-stu-id="dc024-116">When you install the [.NET Core SDK](https://dotnet.microsoft.com/download), you receive over a dozen built-in templates for creating projects and files, including console apps, class libraries, unit test projects, ASP.NET Core apps (including [Angular](https://angular.io/) and [React](https://facebook.github.io/react/) projects), and configuration files.</span></span> <span data-ttu-id="dc024-117">Pokud chcete zobrazit seznam předdefinovaných šablon, spusťte příkaz `dotnet new` s možností `-l|--list`:</span><span class="sxs-lookup"><span data-stu-id="dc024-117">To list the built-in templates, run the `dotnet new` command with the `-l|--list` option:</span></span>

```dotnetcli
dotnet new --list
```

## <a name="configuration"></a><span data-ttu-id="dc024-118">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="dc024-118">Configuration</span></span>

<span data-ttu-id="dc024-119">Šablona se skládá z následujících částí:</span><span class="sxs-lookup"><span data-stu-id="dc024-119">A template is composed of the following parts:</span></span>

- <span data-ttu-id="dc024-120">Zdrojové soubory a složky.</span><span class="sxs-lookup"><span data-stu-id="dc024-120">Source files and folders.</span></span>
- <span data-ttu-id="dc024-121">Konfigurační soubor (*template. JSON*).</span><span class="sxs-lookup"><span data-stu-id="dc024-121">A configuration file (*template.json*).</span></span>

### <a name="source-files-and-folders"></a><span data-ttu-id="dc024-122">Zdrojové soubory a složky</span><span class="sxs-lookup"><span data-stu-id="dc024-122">Source files and folders</span></span>

<span data-ttu-id="dc024-123">Zdrojové soubory a složky zahrnují libovolné soubory a složky, které má modul šablon použít při spuštění příkazu `dotnet new <TEMPLATE>`.</span><span class="sxs-lookup"><span data-stu-id="dc024-123">The source files and folders include whatever files and folders you want the template engine to use when the `dotnet new <TEMPLATE>` command is run.</span></span> <span data-ttu-id="dc024-124">Modul šablon je navržen tak, aby používal *projekty spustitelný* jako zdrojový kód k výrobě projektů.</span><span class="sxs-lookup"><span data-stu-id="dc024-124">The template engine is designed to use *runnable projects* as source code to produce projects.</span></span> <span data-ttu-id="dc024-125">Má několik výhod:</span><span class="sxs-lookup"><span data-stu-id="dc024-125">This has several benefits:</span></span>

- <span data-ttu-id="dc024-126">Modul šablon nevyžaduje vložení speciálních tokenů do zdrojového kódu vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="dc024-126">The template engine doesn't require you to inject special tokens into your project's source code.</span></span>
- <span data-ttu-id="dc024-127">Soubory s kódem nejsou speciální soubory ani upravovány jakýmkoli způsobem pro práci s modulem šablon.</span><span class="sxs-lookup"><span data-stu-id="dc024-127">The code files aren't special files or modified in any way to work with the template engine.</span></span> <span data-ttu-id="dc024-128">Proto nástroje, které běžně používáte při práci s projekty, fungují také s obsahem šablony.</span><span class="sxs-lookup"><span data-stu-id="dc024-128">So, the tools you normally use when working with projects also work with template content.</span></span>
- <span data-ttu-id="dc024-129">Projekty šablon můžete sestavovat, spouštět a ladit stejně jako u všech ostatních projektů.</span><span class="sxs-lookup"><span data-stu-id="dc024-129">You build, run, and debug your template projects just like you do for any of your other projects.</span></span>
- <span data-ttu-id="dc024-130">Můžete rychle vytvořit šablonu z existujícího projektu pouhým přidáním konfiguračního souboru *./.template.config/Template.JSON* do projektu.</span><span class="sxs-lookup"><span data-stu-id="dc024-130">You can quickly create a template from an existing project just by adding a *./.template.config/template.json* configuration file to the project.</span></span>

<span data-ttu-id="dc024-131">Soubory a složky uložené v šabloně nejsou omezeny na formální typy projektů .NET.</span><span class="sxs-lookup"><span data-stu-id="dc024-131">Files and folders stored in the template aren't limited to formal .NET project types.</span></span> <span data-ttu-id="dc024-132">Zdrojové soubory a složky mohou být tvořeny jakýmkoli obsahem, který chcete vytvořit při použití šablony, a to i v případě, že modul šablon vytvoří jako výstup pouze jeden soubor.</span><span class="sxs-lookup"><span data-stu-id="dc024-132">Source files and folders may consist of any content that you wish to create when the template is used, even if the template engine produces just one file as its output.</span></span>

<span data-ttu-id="dc024-133">Soubory vygenerované šablonou lze upravit na základě logiky a nastavení, které jste zadali v konfiguračním souboru *template. JSON* .</span><span class="sxs-lookup"><span data-stu-id="dc024-133">Files generated by the template can be modified based on logic and settings you've provided in the *template.json* configuration file.</span></span> <span data-ttu-id="dc024-134">Uživatel může tato nastavení přepsat předáním možností `dotnet new <TEMPLATE>` příkazu.</span><span class="sxs-lookup"><span data-stu-id="dc024-134">The user can override these settings by passing options to the `dotnet new <TEMPLATE>` command.</span></span> <span data-ttu-id="dc024-135">Běžným příkladem vlastní logiky je poskytnutí názvu pro třídu nebo proměnnou v souboru kódu, který je nasazen šablonou.</span><span class="sxs-lookup"><span data-stu-id="dc024-135">A common example of custom logic is providing a name for a class or variable in the code file that's deployed by a template.</span></span>

### <a name="templatejson"></a><span data-ttu-id="dc024-136">Template. JSON</span><span class="sxs-lookup"><span data-stu-id="dc024-136">template.json</span></span>

<span data-ttu-id="dc024-137">Soubor *template. JSON* je umístěný ve složce *. template. config* v kořenovém adresáři šablony.</span><span class="sxs-lookup"><span data-stu-id="dc024-137">The *template.json* file is placed in a *.template.config* folder in the root directory of the template.</span></span> <span data-ttu-id="dc024-138">Soubor poskytuje konfigurační informace modulu šablony.</span><span class="sxs-lookup"><span data-stu-id="dc024-138">The file provides configuration information to the template engine.</span></span> <span data-ttu-id="dc024-139">Minimální konfigurace vyžaduje, aby členové byli uvedeni v následující tabulce, která je dostačující k vytvoření funkční šablony.</span><span class="sxs-lookup"><span data-stu-id="dc024-139">The minimum configuration requires the members shown in the following table, which is sufficient to create a functional template.</span></span>

| <span data-ttu-id="dc024-140">Člen</span><span class="sxs-lookup"><span data-stu-id="dc024-140">Member</span></span>            | <span data-ttu-id="dc024-141">Typ</span><span class="sxs-lookup"><span data-stu-id="dc024-141">Type</span></span>          | <span data-ttu-id="dc024-142">Popis</span><span class="sxs-lookup"><span data-stu-id="dc024-142">Description</span></span> |
| ----------------- | ------------- | ----------- |
| `$schema`         | <span data-ttu-id="dc024-143">Identifikátor URI</span><span class="sxs-lookup"><span data-stu-id="dc024-143">URI</span></span>           | <span data-ttu-id="dc024-144">Schéma JSON pro soubor *template. JSON* .</span><span class="sxs-lookup"><span data-stu-id="dc024-144">The JSON schema for the *template.json* file.</span></span> <span data-ttu-id="dc024-145">Editory podporující schémata JSON povolují funkce úprav JSON při určení schématu.</span><span class="sxs-lookup"><span data-stu-id="dc024-145">Editors that support JSON schemas enable JSON-editing features when the schema is specified.</span></span> <span data-ttu-id="dc024-146">Například [Visual Studio Code](https://code.visualstudio.com/) vyžaduje, aby tento člen povoloval technologii IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="dc024-146">For example, [Visual Studio Code](https://code.visualstudio.com/) requires this member to enable IntelliSense.</span></span> <span data-ttu-id="dc024-147">Použijte hodnotu `http://json.schemastore.org/template`.</span><span class="sxs-lookup"><span data-stu-id="dc024-147">Use a value of `http://json.schemastore.org/template`.</span></span> |
| `author`          | <span data-ttu-id="dc024-148">odkazy řetězců</span><span class="sxs-lookup"><span data-stu-id="dc024-148">string</span></span>        | <span data-ttu-id="dc024-149">Autor šablony</span><span class="sxs-lookup"><span data-stu-id="dc024-149">The author of the template.</span></span> |
| `classifications` | <span data-ttu-id="dc024-150">Array (řetězec)</span><span class="sxs-lookup"><span data-stu-id="dc024-150">array(string)</span></span> | <span data-ttu-id="dc024-151">Nula nebo více vlastností šablony, kterou může uživatel použít k vyhledání šablony při jejím hledání.</span><span class="sxs-lookup"><span data-stu-id="dc024-151">Zero or more characteristics of the template that a user might use to find the template when searching for it.</span></span> <span data-ttu-id="dc024-152">Klasifikace se také zobrazí ve sloupci *značky* , když se objeví v seznamu šablon vytvořených pomocí příkazu `dotnet new -l|--list`.</span><span class="sxs-lookup"><span data-stu-id="dc024-152">The classifications also appear in the *Tags* column when it appears in a list of templates produced by using the `dotnet new -l|--list` command.</span></span> |
| `identity`        | <span data-ttu-id="dc024-153">odkazy řetězců</span><span class="sxs-lookup"><span data-stu-id="dc024-153">string</span></span>        | <span data-ttu-id="dc024-154">Jedinečný název pro tuto šablonu.</span><span class="sxs-lookup"><span data-stu-id="dc024-154">A unique name for this template.</span></span> |
| `name`            | <span data-ttu-id="dc024-155">odkazy řetězců</span><span class="sxs-lookup"><span data-stu-id="dc024-155">string</span></span>        | <span data-ttu-id="dc024-156">Název šablony, kterou by uživatelé měli vidět.</span><span class="sxs-lookup"><span data-stu-id="dc024-156">The name for the template that users should see.</span></span> |
| `shortName`       | <span data-ttu-id="dc024-157">odkazy řetězců</span><span class="sxs-lookup"><span data-stu-id="dc024-157">string</span></span>        | <span data-ttu-id="dc024-158">Výchozí zkrácený název pro výběr šablony, která se vztahuje na prostředí, kde je název šablony určený uživatelem, který není vybraný prostřednictvím grafického uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="dc024-158">A default shorthand name for selecting the template that applies to environments where the template name is specified by the user, not selected via a GUI.</span></span> <span data-ttu-id="dc024-159">Krátký název je například užitečný při použití šablon z příkazového řádku s příkazy CLI.</span><span class="sxs-lookup"><span data-stu-id="dc024-159">For example, the short name is useful when using templates from a command prompt with CLI commands.</span></span> |

<span data-ttu-id="dc024-160">Úplné schéma pro soubor *template. JSON* najdete v [úložišti schémat JSON](http://json.schemastore.org/template).</span><span class="sxs-lookup"><span data-stu-id="dc024-160">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="dc024-161">Další informace o souboru *template. JSON* najdete v tématu [dotnet šablonování wiki](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="dc024-161">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

#### <a name="example"></a><span data-ttu-id="dc024-162">Příklad</span><span class="sxs-lookup"><span data-stu-id="dc024-162">Example</span></span>

<span data-ttu-id="dc024-163">Tady je například složka šablony, která obsahuje dva soubory obsahu: *Console.cs* a *Readme. txt*.</span><span class="sxs-lookup"><span data-stu-id="dc024-163">For example, here is a template folder that contains two content files: *console.cs* and *readme.txt*.</span></span> <span data-ttu-id="dc024-164">Všimněte si, že existuje požadovaná složka s názvem *. template. config* , která obsahuje soubor *template. JSON* .</span><span class="sxs-lookup"><span data-stu-id="dc024-164">Take notice that there is the required folder named *.template.config* that contains the *template.json* file.</span></span>

```text
└───mytemplate
    │   console.cs
    │   readme.txt
    │
    └───.template.config
            template.json
```

<span data-ttu-id="dc024-165">Soubor *template. JSON* vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="dc024-165">The *template.json* file looks like the following:</span></span>

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Travis Chau",
  "classifications": [ "Common", "Console" ],
  "identity": "AdatumCorporation.ConsoleTemplate.CSharp",
  "name": "Adatum Corporation Console Application",
  "shortName": "adatumconsole"
}
```

<span data-ttu-id="dc024-166">Složka *MyTemplate* je instalovatelný balíček šablon.</span><span class="sxs-lookup"><span data-stu-id="dc024-166">The *mytemplate* folder is an installable template pack.</span></span> <span data-ttu-id="dc024-167">Po instalaci balíčku se `shortName` dá použít s příkazem `dotnet new`.</span><span class="sxs-lookup"><span data-stu-id="dc024-167">Once the pack is installed, the `shortName` can be used with the `dotnet new` command.</span></span> <span data-ttu-id="dc024-168">Například `dotnet new adatumconsole` by měl výstup `console.cs` a `readme.txt` souborů do aktuální složky.</span><span class="sxs-lookup"><span data-stu-id="dc024-168">For example, `dotnet new adatumconsole` would output the `console.cs` and `readme.txt` files to the current folder.</span></span>

## <a name="packing-a-template-into-a-nuget-package-nupkg-file"></a><span data-ttu-id="dc024-169">Balení šablony do balíčku NuGet (soubor nupkg)</span><span class="sxs-lookup"><span data-stu-id="dc024-169">Packing a template into a NuGet package (nupkg file)</span></span>

<span data-ttu-id="dc024-170">Vlastní šablona je zabalena pomocí příkazu [dotnet Pack](dotnet-pack.md) a souboru *. csproj* .</span><span class="sxs-lookup"><span data-stu-id="dc024-170">A custom template is packed with the [dotnet pack](dotnet-pack.md) command and a *.csproj* file.</span></span> <span data-ttu-id="dc024-171">Případně lze [NuGet](https://docs.microsoft.com/nuget/tools/nuget-exe-cli-reference) použít společně s příkazem [balíčku NuGet](https://docs.microsoft.com/nuget/tools/cli-ref-pack) spolu se souborem *. nuspec* .</span><span class="sxs-lookup"><span data-stu-id="dc024-171">Alternatively, [NuGet](https://docs.microsoft.com/nuget/tools/nuget-exe-cli-reference) can be used with the [nuget pack](https://docs.microsoft.com/nuget/tools/cli-ref-pack) command along with a *.nuspec* file.</span></span> <span data-ttu-id="dc024-172">NuGet ale vyžaduje .NET Framework ve Windows a [mono](https://www.mono-project.com/) v systémech Linux a MacOS.</span><span class="sxs-lookup"><span data-stu-id="dc024-172">However, NuGet requires the .NET Framework on Windows and [Mono](https://www.mono-project.com/) on Linux and MacOS.</span></span>

<span data-ttu-id="dc024-173">Soubor *. csproj* se mírně liší od tradičního souboru Code-Project *. csproj* .</span><span class="sxs-lookup"><span data-stu-id="dc024-173">The *.csproj* file is slightly different from a traditional code-project *.csproj* file.</span></span> <span data-ttu-id="dc024-174">Všimněte si následujícího nastavení:</span><span class="sxs-lookup"><span data-stu-id="dc024-174">Note the following settings:</span></span>

01. <span data-ttu-id="dc024-175">Nastavení `<PackageType>` se přidá a nastaví na `Template`.</span><span class="sxs-lookup"><span data-stu-id="dc024-175">The `<PackageType>` setting is added and set to `Template`.</span></span>
01. <span data-ttu-id="dc024-176">Nastavení `<PackageVersion>` se přidá a nastaví na platné [číslo verze NuGet](/nuget/reference/package-versioning).</span><span class="sxs-lookup"><span data-stu-id="dc024-176">The `<PackageVersion>` setting is added and set to a valid [NuGet version number](/nuget/reference/package-versioning).</span></span>
01. <span data-ttu-id="dc024-177">Nastavení `<PackageId>` se přidá a nastaví na jedinečný identifikátor.</span><span class="sxs-lookup"><span data-stu-id="dc024-177">The `<PackageId>` setting is added and set to a unique identifier.</span></span> <span data-ttu-id="dc024-178">Tento identifikátor se používá k odinstalaci balíčku šablon a používá se v kanálech NuGet k registraci balíčku šablon.</span><span class="sxs-lookup"><span data-stu-id="dc024-178">This identifier is used to uninstall the template pack and is used by NuGet feeds to register your template pack.</span></span>
01. <span data-ttu-id="dc024-179">Měla by být nastavena obecná nastavení metadat: `<Title>`, `<Authors>`, `<Description>`a `<PackageTags>`.</span><span class="sxs-lookup"><span data-stu-id="dc024-179">Generic metadata settings should be set: `<Title>`, `<Authors>`, `<Description>`, and `<PackageTags>`.</span></span>
01. <span data-ttu-id="dc024-180">Nastavení `<TargetFramework>` musí být nastavené, i když se binární soubor vytvořený procesem šablony nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="dc024-180">The `<TargetFramework>` setting must be set, even though the binary produced by the template process isn't used.</span></span> <span data-ttu-id="dc024-181">V následujícím příkladu je nastaveno na `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="dc024-181">In the example below it's set to `netstandard2.0`.</span></span>

<span data-ttu-id="dc024-182">Sada šablon, ve formě balíčku NuGet *. nupkg* , vyžaduje, aby všechny šablony byly uloženy ve složce *obsahu* v rámci balíčku.</span><span class="sxs-lookup"><span data-stu-id="dc024-182">A template pack, in the form of a *.nupkg* NuGet package, requires that all templates be stored in the *content* folder within the package.</span></span> <span data-ttu-id="dc024-183">Je k dispozici několik dalších nastavení pro přidání do souboru *. csproj* , aby bylo zajištěno, že vygenerovaný soubor *. nupkg* může být nainstalován jako balíček šablony:</span><span class="sxs-lookup"><span data-stu-id="dc024-183">There are a few more settings to add to a *.csproj* file to ensure that the generated *.nupkg* can be installed as a template pack:</span></span>

01. <span data-ttu-id="dc024-184">Nastavení `<IncludeContentInPack>` je nastaveno na `true`, aby obsahovalo všechny soubory, které projekt nastaví jako **obsah** v balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="dc024-184">The `<IncludeContentInPack>` setting is set to `true` to include any file the project sets as **content** in the NuGet package.</span></span>
01. <span data-ttu-id="dc024-185">Nastavení `<IncludeBuildOutput>` je nastavené na hodnotu `false`, aby se vyloučily všechny binární soubory vygenerované kompilátorem z balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="dc024-185">The `<IncludeBuildOutput>` setting is set to `false` to exclude all binaries generated by the compiler from the NuGet package.</span></span>
01. <span data-ttu-id="dc024-186">Nastavení `<ContentTargetFolders>` je nastaveno na hodnotu `content`.</span><span class="sxs-lookup"><span data-stu-id="dc024-186">The `<ContentTargetFolders>` setting is set to `content`.</span></span> <span data-ttu-id="dc024-187">Tím se zajistí, že soubory nastavené jako **obsah** budou uloženy ve složce *obsahu* v balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="dc024-187">This makes sure that the files set as **content** are stored in the *content* folder in the NuGet package.</span></span> <span data-ttu-id="dc024-188">Tato složka v balíčku NuGet je analyzována systémem šablony dotnet.</span><span class="sxs-lookup"><span data-stu-id="dc024-188">This folder in the NuGet package is parsed by the dotnet template system.</span></span>

<span data-ttu-id="dc024-189">Snadný způsob, jak vyloučit všechny soubory kódu z kompilace pomocí projektu šablony, je použití položky `<Compile Remove="**\*" />` v souboru projektu v rámci `<ItemGroup>` elementu.</span><span class="sxs-lookup"><span data-stu-id="dc024-189">An easy way to exclude all code files from being compiled by your template project is by using the `<Compile Remove="**\*" />` item in your project file, inside an `<ItemGroup>` element.</span></span>

<span data-ttu-id="dc024-190">Snadný způsob, jak strukturovat balíček šablon, je umístit všechny šablony do jednotlivých složek a následně každou složku šablony do složky *šablony* , která je umístěna ve stejném adresáři jako soubor *. csproj* .</span><span class="sxs-lookup"><span data-stu-id="dc024-190">An easy way to structure your template pack is to put all templates in individual folders, and then each template folder inside of a *templates* folder that is located in the same directory as your *.csproj* file.</span></span> <span data-ttu-id="dc024-191">Tímto způsobem můžete použít jednu položku projektu pro zahrnutí všech souborů a složek v *šablonách* jako **obsah**.</span><span class="sxs-lookup"><span data-stu-id="dc024-191">This way, you can use a single project item to include all files and folders in the *templates* as **content**.</span></span> <span data-ttu-id="dc024-192">V prvku `<ItemGroup>` vytvořte položku `<Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />`.</span><span class="sxs-lookup"><span data-stu-id="dc024-192">Inside of an `<ItemGroup>` element, create a `<Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />` item.</span></span>

<span data-ttu-id="dc024-193">Zde je příklad souboru *. csproj* , který následuje za všemi výše uvedenými pokyny.</span><span class="sxs-lookup"><span data-stu-id="dc024-193">Here is an example *.csproj* file that follows all of the guidelines above.</span></span> <span data-ttu-id="dc024-194">Sbalí podřízenou složku *šablony* do složky balíčku *obsahu* a vyloučí všechny soubory kódu, které se mají kompilovat.</span><span class="sxs-lookup"><span data-stu-id="dc024-194">It packs the *templates* child folder to the *content* package folder and excludes any code file from being compiled.</span></span>

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

<span data-ttu-id="dc024-195">Následující příklad ukazuje strukturu souborů a složek použití souboru *. csproj* k vytvoření sady šablon.</span><span class="sxs-lookup"><span data-stu-id="dc024-195">The example below demonstrates the file and folder structure of using a *.csproj* to create a template pack.</span></span> <span data-ttu-id="dc024-196">Soubor *MyDotnetTemplates. csproj* a složky *šablon* jsou umístěny v kořenu adresáře s názvem *project_folder*.</span><span class="sxs-lookup"><span data-stu-id="dc024-196">The *MyDotnetTemplates.csproj* file and *templates* folder are both located at the root of a directory named *project_folder*.</span></span> <span data-ttu-id="dc024-197">Složka *Templates* obsahuje dvě šablony, *mytemplate1* a *mytemplate2*.</span><span class="sxs-lookup"><span data-stu-id="dc024-197">The *templates* folder contains two templates, *mytemplate1* and *mytemplate2*.</span></span> <span data-ttu-id="dc024-198">Každá šablona má soubory obsahu a složku *. template. config* pomocí konfiguračního souboru *template. JSON* .</span><span class="sxs-lookup"><span data-stu-id="dc024-198">Each template has content files and a *.template.config* folder with a *template.json* config file.</span></span>

```text
project_folder
│   MyDotnetTemplates.csproj
│
└───templates
    ├───mytemplate1
    │   │   console.cs
    │   │   readme.txt
    │   │
    │   └───.template.config
    │           template.json
    │
    └───mytemplate2
        │   otherfile.cs
        │
        └───.template.config
                template.json
```

## <a name="installing-a-template"></a><span data-ttu-id="dc024-199">Instalace šablony</span><span class="sxs-lookup"><span data-stu-id="dc024-199">Installing a template</span></span>

<span data-ttu-id="dc024-200">K instalaci balíčku použijte příkaz [dotnet New-i |--Install](dotnet-new.md) .</span><span class="sxs-lookup"><span data-stu-id="dc024-200">Use the [dotnet new -i|--install](dotnet-new.md) command to install a package.</span></span>

### <a name="to-install-a-template-from-a-nuget-package-stored-at-nugetorg"></a><span data-ttu-id="dc024-201">Instalace šablony z balíčku NuGet uloženého na nuget.org</span><span class="sxs-lookup"><span data-stu-id="dc024-201">To install a template from a NuGet package stored at nuget.org</span></span>

<span data-ttu-id="dc024-202">K instalaci balíčku šablony použijte identifikátor balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="dc024-202">Use the NuGet package identifier to install a template package.</span></span>

```dotnetcli
dotnet new -i <NUGET_PACKAGE_ID>
```

### <a name="to-install-a-template-from-a-local-nupkg-file"></a><span data-ttu-id="dc024-203">Instalace šablony z místního souboru nupkg</span><span class="sxs-lookup"><span data-stu-id="dc024-203">To install a template from a local nupkg file</span></span>

<span data-ttu-id="dc024-204">Zadejte cestu k souboru balíčku NuGet *. nupkg* .</span><span class="sxs-lookup"><span data-stu-id="dc024-204">Provide the path to a *.nupkg* NuGet package file.</span></span>

```dotnetcli
dotnet new -i <PATH_TO_NUPKG_FILE>
```

### <a name="to-install-a-template-from-a-file-system-directory"></a><span data-ttu-id="dc024-205">Instalace šablony z adresáře systému souborů</span><span class="sxs-lookup"><span data-stu-id="dc024-205">To install a template from a file system directory</span></span>

<span data-ttu-id="dc024-206">Šablony lze nainstalovat ze složky šablony, jako je například složka *mytemplate1* z výše uvedeného příkladu.</span><span class="sxs-lookup"><span data-stu-id="dc024-206">Templates can be installed from a template folder, such as the *mytemplate1* folder from the example above.</span></span> <span data-ttu-id="dc024-207">Zadejte cestu ke složce ve složce *. template. config* .</span><span class="sxs-lookup"><span data-stu-id="dc024-207">Specify the folder path of the *.template.config* folder.</span></span> <span data-ttu-id="dc024-208">Cesta k adresáři šablon nemusí být absolutní.</span><span class="sxs-lookup"><span data-stu-id="dc024-208">The path to the template directory does not need to be absolute.</span></span> <span data-ttu-id="dc024-209">K odinstalaci šablony, která je nainstalovaná ze složky, je ale nutná absolutní cesta.</span><span class="sxs-lookup"><span data-stu-id="dc024-209">However, an absolute path is required to uninstall a template that is installed from a folder.</span></span>

```dotnetcli
dotnet new -i <FILE_SYSTEM_DIRECTORY>
```

## <a name="get-a-list-of-installed-templates"></a><span data-ttu-id="dc024-210">Získání seznamu nainstalovaných šablon</span><span class="sxs-lookup"><span data-stu-id="dc024-210">Get a list of installed templates</span></span>

<span data-ttu-id="dc024-211">Příkaz uninstall bez dalších parametrů zobrazí seznam všech nainstalovaných šablon.</span><span class="sxs-lookup"><span data-stu-id="dc024-211">The uninstall command, without any other parameters, will list all installed templates.</span></span>

```dotnetcli
dotnet new -u
```

<span data-ttu-id="dc024-212">Tento příkaz vrátí něco podobného následujícímu výstupu:</span><span class="sxs-lookup"><span data-stu-id="dc024-212">That command returns something similar to the following output:</span></span>

```console
Template Instantiation Commands for .NET Core CLI

Currently installed items:
  Microsoft.DotNet.Common.ItemTemplates
    Templates:
      global.json file (globaljson)
      NuGet Config (nugetconfig)
      Solution File (sln)
      Dotnet local tool manifest file (tool-manifest)
      Web Config (webconfig)
  Microsoft.DotNet.Common.ProjectTemplates.3.0
    Templates:
      Class library (classlib) C#
      Class library (classlib) F#
      Class library (classlib) VB
      Console Application (console) C#
      Console Application (console) F#
      Console Application (console) VB
...
```

<span data-ttu-id="dc024-213">První úroveň položek po `Currently installed items:` jsou identifikátory používané při odinstalaci šablony.</span><span class="sxs-lookup"><span data-stu-id="dc024-213">The first level of items after `Currently installed items:` are the identifiers used in uninstalling a template.</span></span> <span data-ttu-id="dc024-214">A v příkladu výše jsou uvedeny `Microsoft.DotNet.Common.ItemTemplates` a `Microsoft.DotNet.Common.ProjectTemplates.3.0`.</span><span class="sxs-lookup"><span data-stu-id="dc024-214">And in the example above, `Microsoft.DotNet.Common.ItemTemplates` and `Microsoft.DotNet.Common.ProjectTemplates.3.0` are listed.</span></span> <span data-ttu-id="dc024-215">Pokud byla šablona nainstalována pomocí cesty systému souborů, tento identifikátor bude cestou složky složky *. template. config* .</span><span class="sxs-lookup"><span data-stu-id="dc024-215">If the template was installed by using a file system path, this identifier will the folder path of the *.template.config* folder.</span></span>

## <a name="uninstalling-a-template"></a><span data-ttu-id="dc024-216">Odinstalace šablony</span><span class="sxs-lookup"><span data-stu-id="dc024-216">Uninstalling a template</span></span>

<span data-ttu-id="dc024-217">K odinstalaci balíčku použijte příkaz [dotnet New-u |--Uninstall](dotnet-new.md) .</span><span class="sxs-lookup"><span data-stu-id="dc024-217">Use the [dotnet new -u|--uninstall](dotnet-new.md) command to uninstall a package.</span></span>

<span data-ttu-id="dc024-218">Pokud byl balíček nainstalován buď pomocí kanálu NuGet, nebo přímo v souboru *. nupkg* , zadejte identifikátor.</span><span class="sxs-lookup"><span data-stu-id="dc024-218">If the package was installed by either a NuGet feed or by a *.nupkg* file directly, provide the identifier.</span></span>

```dotnetcli
dotnet new -u <NUGET_PACKAGE_ID>
```

<span data-ttu-id="dc024-219">Pokud byl balíček nainstalovaný zadáním cesty ke složce *. template. config* , použijte k odinstalaci balíčku tuto **absolutní** cestu.</span><span class="sxs-lookup"><span data-stu-id="dc024-219">If the package was installed by specifying a path to the *.template.config* folder, use that **absolute** path to uninstall the package.</span></span> <span data-ttu-id="dc024-220">Ve výstupu poskytnutém příkazem `dotnet new -u` lze zobrazit absolutní cestu šablony.</span><span class="sxs-lookup"><span data-stu-id="dc024-220">You can see the absolute path of the template in the output provided by the `dotnet new -u` command.</span></span> <span data-ttu-id="dc024-221">Další informace najdete v části [získání seznamu nainstalovaných šablon](#get-a-list-of-installed-templates) výše.</span><span class="sxs-lookup"><span data-stu-id="dc024-221">For more information, see the [Get a list of installed templates](#get-a-list-of-installed-templates) section above.</span></span>

```dotnetcli
dotnet new -u <ABSOLUTE_FILE_SYSTEM_DIRECTORY>
```

## <a name="create-a-project-using-a-custom-template"></a><span data-ttu-id="dc024-222">Vytvoření projektu pomocí vlastní šablony</span><span class="sxs-lookup"><span data-stu-id="dc024-222">Create a project using a custom template</span></span>

<span data-ttu-id="dc024-223">Po instalaci šablony použijte příkaz `dotnet new <TEMPLATE>` stejným způsobem jako u jakékoli jiné předem instalované šablony.</span><span class="sxs-lookup"><span data-stu-id="dc024-223">After a template is installed, use the template by executing the `dotnet new <TEMPLATE>` command as you would with any other pre-installed template.</span></span> <span data-ttu-id="dc024-224">Můžete také zadat [Možnosti](dotnet-new.md#options) příkazu `dotnet new`, včetně možností specifických pro šablonu, které jste nakonfigurovali v nastavení šablony.</span><span class="sxs-lookup"><span data-stu-id="dc024-224">You can also specify [options](dotnet-new.md#options) to the `dotnet new` command, including template-specific options you configured in the template settings.</span></span> <span data-ttu-id="dc024-225">Zadejte krátký název šablony přímo do příkazu:</span><span class="sxs-lookup"><span data-stu-id="dc024-225">Supply the template's short name directly to the command:</span></span>

```dotnetcli
dotnet new <TEMPLATE>
```

## <a name="see-also"></a><span data-ttu-id="dc024-226">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dc024-226">See also</span></span>

- [<span data-ttu-id="dc024-227">Vytvoření vlastní šablony pro dotnet New (kurz)</span><span class="sxs-lookup"><span data-stu-id="dc024-227">Create a custom template for dotnet new (tutorial)</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="dc024-228">dotnet/šablonování wiki úložiště GitHub</span><span class="sxs-lookup"><span data-stu-id="dc024-228">dotnet/templating GitHub repo Wiki</span></span>](https://github.com/dotnet/templating/wiki)
- [<span data-ttu-id="dc024-229">dotnet/dotnet-Template-Samples – úložiště GitHub</span><span class="sxs-lookup"><span data-stu-id="dc024-229">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="dc024-230">Jak vytvořit vlastní šablony pro dotnet New</span><span class="sxs-lookup"><span data-stu-id="dc024-230">How to create your own templates for dotnet new</span></span>](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/)
- [<span data-ttu-id="dc024-231">*template. JSON* – schéma v ÚLOŽIŠTI schémat JSON</span><span class="sxs-lookup"><span data-stu-id="dc024-231">*template.json* schema at the JSON Schema Store</span></span>](http://json.schemastore.org/template)
