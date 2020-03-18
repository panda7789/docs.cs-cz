---
title: Vlastní šablony pro dotnet nové
description: Přečtěte si o vlastních šablonách pro jakýkoli typ projektu nebo souborů .NET.
author: thraka
ms.date: 06/14/2019
ms.openlocfilehash: 8e1ac4ca21a8a90ad0f7c9bd3dd11281eb4a6e02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73420881"
---
# <a name="custom-templates-for-dotnet-new"></a><span data-ttu-id="19af3-103">Vlastní šablony pro dotnet nové</span><span class="sxs-lookup"><span data-stu-id="19af3-103">Custom templates for dotnet new</span></span>

<span data-ttu-id="19af3-104">Sada [.NET Core SDK](https://dotnet.microsoft.com/download) je dodávána s mnoha šablonami, které jsou již nainstalovány a připraveny k použití.</span><span class="sxs-lookup"><span data-stu-id="19af3-104">The [.NET Core SDK](https://dotnet.microsoft.com/download) comes with many templates already installed and ready for you to use.</span></span> <span data-ttu-id="19af3-105">[ `dotnet new` Příkaz](dotnet-new.md) není pouze způsob použití šablony, ale také způsob instalace a odinstalace šablon.</span><span class="sxs-lookup"><span data-stu-id="19af3-105">The [`dotnet new` command](dotnet-new.md) isn't only the way to use a template, but also how to install and uninstall templates.</span></span> <span data-ttu-id="19af3-106">Počínaje rozhraním .NET Core 2.0 můžete vytvořit vlastní šablony pro libovolný typ projektu, například pro aplikaci, službu, nástroj nebo knihovnu tříd.</span><span class="sxs-lookup"><span data-stu-id="19af3-106">Starting with .NET Core 2.0, you can create your own custom templates for any type of project, such as an app, service, tool, or class library.</span></span> <span data-ttu-id="19af3-107">Můžete dokonce vytvořit šablonu, která vypíše jeden nebo více nezávislých souborů, například konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="19af3-107">You can even create a template that outputs one or more independent files, such as a configuration file.</span></span>

<span data-ttu-id="19af3-108">Vlastní šablony z balíčku NuGet můžete nainstalovat do libovolného informačního kanálu NuGet, odkazováním přímo na soubor NuGet *.nupkg* nebo zadáním adresáře systému souborů, který obsahuje šablonu.</span><span class="sxs-lookup"><span data-stu-id="19af3-108">You can install custom templates from a NuGet package on any NuGet feed, by referencing a NuGet *.nupkg* file directly, or by specifying a file system directory that contains the template.</span></span> <span data-ttu-id="19af3-109">Modul šablony nabízí funkce, které umožňují nahradit hodnoty, zahrnout a vyloučit soubory a provádět vlastní operace zpracování při použití šablony.</span><span class="sxs-lookup"><span data-stu-id="19af3-109">The template engine offers features that allow you to replace values, include and exclude files, and execute custom processing operations when your template is used.</span></span>

<span data-ttu-id="19af3-110">Modul šablony je open source a úložiště online kódu je na [dotnet/templating](https://github.com/dotnet/templating/) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="19af3-110">The template engine is open source, and the online code repository is at [dotnet/templating](https://github.com/dotnet/templating/) on GitHub.</span></span> <span data-ttu-id="19af3-111">Navštivte [dotnet/dotnet-template-samples](https://github.com/dotnet/dotnet-template-samples) repo pro ukázky šablon.</span><span class="sxs-lookup"><span data-stu-id="19af3-111">Visit the [dotnet/dotnet-template-samples](https://github.com/dotnet/dotnet-template-samples) repo for samples of templates.</span></span> <span data-ttu-id="19af3-112">Další šablony, včetně šablon od třetích stran, najdete na [dostupné šablony pro dotnet nové](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="19af3-112">More templates, including templates from third parties, are found at [Available templates for dotnet new](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) on GitHub.</span></span> <span data-ttu-id="19af3-113">Další informace o vytváření a používání vlastních šablon najdete v tématu [Jak vytvořit vlastní šablony pro dotnet new](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/) a [dotnet/templating GitHub repo Wiki](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="19af3-113">For more information about creating and using custom templates, see [How to create your own templates for dotnet new](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/) and the [dotnet/templating GitHub repo Wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="19af3-114">Pokud chcete postupovat podle návodu a vytvořit šablonu, přečtěte si viz [Vytvoření vlastní šablony pro dotnet new](../tutorials/cli-templates-create-item-template.md) tutorial.</span><span class="sxs-lookup"><span data-stu-id="19af3-114">To follow a walkthrough and create a template, see the [Create a custom template for dotnet new](../tutorials/cli-templates-create-item-template.md) tutorial.</span></span>

### <a name="net-default-templates"></a><span data-ttu-id="19af3-115">Výchozí šablony rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="19af3-115">.NET default templates</span></span>

<span data-ttu-id="19af3-116">Při instalaci [sady .NET Core SDK](https://dotnet.microsoft.com/download)získáte více než tucet předdefinovaných šablon pro vytváření projektů a souborů, včetně konzolových aplikací, knihoven tříd, projektů testování částí, aplikací ASP.NET Core (včetně [projektů Angular](https://angular.io/) a [React)](https://facebook.github.io/react/) a konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="19af3-116">When you install the [.NET Core SDK](https://dotnet.microsoft.com/download), you receive over a dozen built-in templates for creating projects and files, including console apps, class libraries, unit test projects, ASP.NET Core apps (including [Angular](https://angular.io/) and [React](https://facebook.github.io/react/) projects), and configuration files.</span></span> <span data-ttu-id="19af3-117">Chcete-li zobrazit seznam předdefinovaných `dotnet new` šablon, `-l|--list` spusťte příkaz s možností:</span><span class="sxs-lookup"><span data-stu-id="19af3-117">To list the built-in templates, run the `dotnet new` command with the `-l|--list` option:</span></span>

```dotnetcli
dotnet new --list
```

## <a name="configuration"></a><span data-ttu-id="19af3-118">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="19af3-118">Configuration</span></span>

<span data-ttu-id="19af3-119">Šablona se skládá z následujících částí:</span><span class="sxs-lookup"><span data-stu-id="19af3-119">A template is composed of the following parts:</span></span>

- <span data-ttu-id="19af3-120">Zdrojové soubory a složky.</span><span class="sxs-lookup"><span data-stu-id="19af3-120">Source files and folders.</span></span>
- <span data-ttu-id="19af3-121">Konfigurační soubor (*template.json*).</span><span class="sxs-lookup"><span data-stu-id="19af3-121">A configuration file (*template.json*).</span></span>

### <a name="source-files-and-folders"></a><span data-ttu-id="19af3-122">Zdrojové soubory a složky</span><span class="sxs-lookup"><span data-stu-id="19af3-122">Source files and folders</span></span>

<span data-ttu-id="19af3-123">Zdrojové soubory a složky obsahují libovolné soubory a složky, které chcete, aby modul šablony používal při spuštění příkazu. `dotnet new <TEMPLATE>`</span><span class="sxs-lookup"><span data-stu-id="19af3-123">The source files and folders include whatever files and folders you want the template engine to use when the `dotnet new <TEMPLATE>` command is run.</span></span> <span data-ttu-id="19af3-124">Modul šablony je navržen tak, aby používal *spustitelné projekty* jako zdrojový kód k vytváření projektů.</span><span class="sxs-lookup"><span data-stu-id="19af3-124">The template engine is designed to use *runnable projects* as source code to produce projects.</span></span> <span data-ttu-id="19af3-125">To má několik výhod:</span><span class="sxs-lookup"><span data-stu-id="19af3-125">This has several benefits:</span></span>

- <span data-ttu-id="19af3-126">Modul šablony nevyžaduje, abyste do zdrojového kódu projektu vnesli speciální tokeny.</span><span class="sxs-lookup"><span data-stu-id="19af3-126">The template engine doesn't require you to inject special tokens into your project's source code.</span></span>
- <span data-ttu-id="19af3-127">Soubory kódu nejsou speciální soubory nebo upraveny v žádném případě pracovat s šablonou motoru.</span><span class="sxs-lookup"><span data-stu-id="19af3-127">The code files aren't special files or modified in any way to work with the template engine.</span></span> <span data-ttu-id="19af3-128">Nástroje, které běžně používáte při práci s projekty, tedy pracují také s obsahem šablony.</span><span class="sxs-lookup"><span data-stu-id="19af3-128">So, the tools you normally use when working with projects also work with template content.</span></span>
- <span data-ttu-id="19af3-129">Sestavení, spuštění a ladění projektů šablony stejně jako u jiných projektů.</span><span class="sxs-lookup"><span data-stu-id="19af3-129">You build, run, and debug your template projects just like you do for any of your other projects.</span></span>
- <span data-ttu-id="19af3-130">Šablonu z existujícího projektu můžete rychle vytvořit pouhým přidáním konfiguračního souboru *./.template.config/template.json* do projektu.</span><span class="sxs-lookup"><span data-stu-id="19af3-130">You can quickly create a template from an existing project just by adding a *./.template.config/template.json* configuration file to the project.</span></span>

<span data-ttu-id="19af3-131">Soubory a složky uložené v šabloně nejsou omezeny na formální typy projektů .NET.</span><span class="sxs-lookup"><span data-stu-id="19af3-131">Files and folders stored in the template aren't limited to formal .NET project types.</span></span> <span data-ttu-id="19af3-132">Zdrojové soubory a složky se mohou skládat z libovolného obsahu, který chcete vytvořit při použití šablony, i když modul šablony vytvoří jako výstup pouze jeden soubor.</span><span class="sxs-lookup"><span data-stu-id="19af3-132">Source files and folders may consist of any content that you wish to create when the template is used, even if the template engine produces just one file as its output.</span></span>

<span data-ttu-id="19af3-133">Soubory generované šablonou lze upravit na základě logiky a nastavení, které jste zadali v konfiguračním souboru *template.json.*</span><span class="sxs-lookup"><span data-stu-id="19af3-133">Files generated by the template can be modified based on logic and settings you've provided in the *template.json* configuration file.</span></span> <span data-ttu-id="19af3-134">Uživatel může přepsat tato nastavení předáním `dotnet new <TEMPLATE>` možnosti příkazu.</span><span class="sxs-lookup"><span data-stu-id="19af3-134">The user can override these settings by passing options to the `dotnet new <TEMPLATE>` command.</span></span> <span data-ttu-id="19af3-135">Běžným příkladem vlastní logiky je poskytnutí názvu pro třídu nebo proměnnou v souboru kódu, který je nasazen šablonou.</span><span class="sxs-lookup"><span data-stu-id="19af3-135">A common example of custom logic is providing a name for a class or variable in the code file that's deployed by a template.</span></span>

### <a name="templatejson"></a><span data-ttu-id="19af3-136">šablona.json</span><span class="sxs-lookup"><span data-stu-id="19af3-136">template.json</span></span>

<span data-ttu-id="19af3-137">Soubor *template.json* je umístěn do složky *.template.config* v kořenovém adresáři šablony.</span><span class="sxs-lookup"><span data-stu-id="19af3-137">The *template.json* file is placed in a *.template.config* folder in the root directory of the template.</span></span> <span data-ttu-id="19af3-138">Soubor poskytuje informace o konfiguraci modulu šablony.</span><span class="sxs-lookup"><span data-stu-id="19af3-138">The file provides configuration information to the template engine.</span></span> <span data-ttu-id="19af3-139">Minimální konfigurace vyžaduje členy uvedené v následující tabulce, která je dostatečná k vytvoření funkční šablony.</span><span class="sxs-lookup"><span data-stu-id="19af3-139">The minimum configuration requires the members shown in the following table, which is sufficient to create a functional template.</span></span>

| <span data-ttu-id="19af3-140">Člen</span><span class="sxs-lookup"><span data-stu-id="19af3-140">Member</span></span>            | <span data-ttu-id="19af3-141">Typ</span><span class="sxs-lookup"><span data-stu-id="19af3-141">Type</span></span>          | <span data-ttu-id="19af3-142">Popis</span><span class="sxs-lookup"><span data-stu-id="19af3-142">Description</span></span> |
| ----------------- | ------------- | ----------- |
| `$schema`         | <span data-ttu-id="19af3-143">Identifikátor URI</span><span class="sxs-lookup"><span data-stu-id="19af3-143">URI</span></span>           | <span data-ttu-id="19af3-144">Schéma JSON pro soubor *template.json.*</span><span class="sxs-lookup"><span data-stu-id="19af3-144">The JSON schema for the *template.json* file.</span></span> <span data-ttu-id="19af3-145">Editory, které podporují schémata JSON, umožňují funkce úprav JSON, pokud je zadáno schéma.</span><span class="sxs-lookup"><span data-stu-id="19af3-145">Editors that support JSON schemas enable JSON-editing features when the schema is specified.</span></span> <span data-ttu-id="19af3-146">[Například Visual Studio Code](https://code.visualstudio.com/) vyžaduje tento člen povolit IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="19af3-146">For example, [Visual Studio Code](https://code.visualstudio.com/) requires this member to enable IntelliSense.</span></span> <span data-ttu-id="19af3-147">Použijte hodnotu `http://json.schemastore.org/template`.</span><span class="sxs-lookup"><span data-stu-id="19af3-147">Use a value of `http://json.schemastore.org/template`.</span></span> |
| `author`          | <span data-ttu-id="19af3-148">řetězec</span><span class="sxs-lookup"><span data-stu-id="19af3-148">string</span></span>        | <span data-ttu-id="19af3-149">Autor šablony.</span><span class="sxs-lookup"><span data-stu-id="19af3-149">The author of the template.</span></span> |
| `classifications` | <span data-ttu-id="19af3-150">array(řetězec)</span><span class="sxs-lookup"><span data-stu-id="19af3-150">array(string)</span></span> | <span data-ttu-id="19af3-151">Nula nebo více charakteristik šablony, které může uživatel použít k vyhledání šablony při hledání.</span><span class="sxs-lookup"><span data-stu-id="19af3-151">Zero or more characteristics of the template that a user might use to find the template when searching for it.</span></span> <span data-ttu-id="19af3-152">Klasifikace se také zobrazí ve sloupci *Tagy,* když se zobrazí `dotnet new -l|--list` v seznamu šablon vytvořených pomocí příkazu.</span><span class="sxs-lookup"><span data-stu-id="19af3-152">The classifications also appear in the *Tags* column when it appears in a list of templates produced by using the `dotnet new -l|--list` command.</span></span> |
| `identity`        | <span data-ttu-id="19af3-153">řetězec</span><span class="sxs-lookup"><span data-stu-id="19af3-153">string</span></span>        | <span data-ttu-id="19af3-154">Jedinečný název této šablony.</span><span class="sxs-lookup"><span data-stu-id="19af3-154">A unique name for this template.</span></span> |
| `name`            | <span data-ttu-id="19af3-155">řetězec</span><span class="sxs-lookup"><span data-stu-id="19af3-155">string</span></span>        | <span data-ttu-id="19af3-156">Název šablony, kterou by měli uživatelé vidět.</span><span class="sxs-lookup"><span data-stu-id="19af3-156">The name for the template that users should see.</span></span> |
| `shortName`       | <span data-ttu-id="19af3-157">řetězec</span><span class="sxs-lookup"><span data-stu-id="19af3-157">string</span></span>        | <span data-ttu-id="19af3-158">Výchozí zkrácený název pro výběr šablony, která se vztahuje na prostředí, kde je název šablony určen uživatelem, není vybrán pomocí grafického uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="19af3-158">A default shorthand name for selecting the template that applies to environments where the template name is specified by the user, not selected via a GUI.</span></span> <span data-ttu-id="19af3-159">Krátký název je například užitečný při použití šablon z příkazového řádku s příkazy příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="19af3-159">For example, the short name is useful when using templates from a command prompt with CLI commands.</span></span> |

<span data-ttu-id="19af3-160">Úplné schéma souboru *template.json* se nachází v [úložišti schématu JSON](http://json.schemastore.org/template).</span><span class="sxs-lookup"><span data-stu-id="19af3-160">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="19af3-161">Další informace o souboru *template.json* naleznete [na wiki dotnet templating](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="19af3-161">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

#### <a name="example"></a><span data-ttu-id="19af3-162">Příklad</span><span class="sxs-lookup"><span data-stu-id="19af3-162">Example</span></span>

<span data-ttu-id="19af3-163">Zde je například složka šablony, která obsahuje dva soubory obsahu: *console.cs* a *readme.txt*.</span><span class="sxs-lookup"><span data-stu-id="19af3-163">For example, here is a template folder that contains two content files: *console.cs* and *readme.txt*.</span></span> <span data-ttu-id="19af3-164">Všimněte si, že existuje požadovaná složka s názvem *.template.config,* která obsahuje soubor *template.json.*</span><span class="sxs-lookup"><span data-stu-id="19af3-164">Take notice that there is the required folder named *.template.config* that contains the *template.json* file.</span></span>

```text
└───mytemplate
    │   console.cs
    │   readme.txt
    │
    └───.template.config
            template.json
```

<span data-ttu-id="19af3-165">Soubor *template.json* vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="19af3-165">The *template.json* file looks like the following:</span></span>

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

<span data-ttu-id="19af3-166">Složka *mytemplate* je instalovatelná sada šablon.</span><span class="sxs-lookup"><span data-stu-id="19af3-166">The *mytemplate* folder is an installable template pack.</span></span> <span data-ttu-id="19af3-167">Jakmile je balíček `shortName` nainstalován, lze `dotnet new` jej použít pomocí příkazu.</span><span class="sxs-lookup"><span data-stu-id="19af3-167">Once the pack is installed, the `shortName` can be used with the `dotnet new` command.</span></span> <span data-ttu-id="19af3-168">Například `dotnet new adatumconsole` by výstup `console.cs` `readme.txt` a soubory do aktuální složky.</span><span class="sxs-lookup"><span data-stu-id="19af3-168">For example, `dotnet new adatumconsole` would output the `console.cs` and `readme.txt` files to the current folder.</span></span>

## <a name="packing-a-template-into-a-nuget-package-nupkg-file"></a><span data-ttu-id="19af3-169">Balení šablony do balíčku NuGet (soubor nupkg)</span><span class="sxs-lookup"><span data-stu-id="19af3-169">Packing a template into a NuGet package (nupkg file)</span></span>

<span data-ttu-id="19af3-170">Vlastní šablona je plná příkazu [dotnet pack](dotnet-pack.md) a souboru *.csproj.*</span><span class="sxs-lookup"><span data-stu-id="19af3-170">A custom template is packed with the [dotnet pack](dotnet-pack.md) command and a *.csproj* file.</span></span> <span data-ttu-id="19af3-171">Alternativně [NuGet](https://docs.microsoft.com/nuget/tools/nuget-exe-cli-reference) lze použít s [nuget pack](https://docs.microsoft.com/nuget/tools/cli-ref-pack) příkaz spolu se souborem *.nuspec.*</span><span class="sxs-lookup"><span data-stu-id="19af3-171">Alternatively, [NuGet](https://docs.microsoft.com/nuget/tools/nuget-exe-cli-reference) can be used with the [nuget pack](https://docs.microsoft.com/nuget/tools/cli-ref-pack) command along with a *.nuspec* file.</span></span> <span data-ttu-id="19af3-172">NuGet však vyžaduje rozhraní .NET Framework v systému Windows a [Mono](https://www.mono-project.com/) v systémech Linux a MacOS.</span><span class="sxs-lookup"><span data-stu-id="19af3-172">However, NuGet requires the .NET Framework on Windows and [Mono](https://www.mono-project.com/) on Linux and MacOS.</span></span>

<span data-ttu-id="19af3-173">Soubor *.csproj* se mírně liší od tradičního souboru *code-project .csproj.*</span><span class="sxs-lookup"><span data-stu-id="19af3-173">The *.csproj* file is slightly different from a traditional code-project *.csproj* file.</span></span> <span data-ttu-id="19af3-174">Všimněte si těchto nastavení:</span><span class="sxs-lookup"><span data-stu-id="19af3-174">Note the following settings:</span></span>

01. <span data-ttu-id="19af3-175">Nastavení `<PackageType>` je přidáno `Template`a nastaveno na .</span><span class="sxs-lookup"><span data-stu-id="19af3-175">The `<PackageType>` setting is added and set to `Template`.</span></span>
01. <span data-ttu-id="19af3-176">Toto `<PackageVersion>` nastavení je přidáno a nastaveno na platné [číslo verze NuGet](/nuget/reference/package-versioning).</span><span class="sxs-lookup"><span data-stu-id="19af3-176">The `<PackageVersion>` setting is added and set to a valid [NuGet version number](/nuget/reference/package-versioning).</span></span>
01. <span data-ttu-id="19af3-177">Nastavení `<PackageId>` je přidáno a nastaveno na jedinečný identifikátor.</span><span class="sxs-lookup"><span data-stu-id="19af3-177">The `<PackageId>` setting is added and set to a unique identifier.</span></span> <span data-ttu-id="19af3-178">Tento identifikátor se používá k odinstalaci balíčku šablon a používá se nugetské kanály k registraci sady šablon.</span><span class="sxs-lookup"><span data-stu-id="19af3-178">This identifier is used to uninstall the template pack and is used by NuGet feeds to register your template pack.</span></span>
01. <span data-ttu-id="19af3-179">Měla by být nastavena `<Title>` `<Authors>`obecná `<Description>`nastavení `<PackageTags>`metadat: , , a .</span><span class="sxs-lookup"><span data-stu-id="19af3-179">Generic metadata settings should be set: `<Title>`, `<Authors>`, `<Description>`, and `<PackageTags>`.</span></span>
01. <span data-ttu-id="19af3-180">Nastavení `<TargetFramework>` musí být nastaveno, i když se nepoužije binární soubor vytvořený procesem šablony.</span><span class="sxs-lookup"><span data-stu-id="19af3-180">The `<TargetFramework>` setting must be set, even though the binary produced by the template process isn't used.</span></span> <span data-ttu-id="19af3-181">V níže uvedeném příkladu `netstandard2.0`je nastavena na .</span><span class="sxs-lookup"><span data-stu-id="19af3-181">In the example below it's set to `netstandard2.0`.</span></span>

<span data-ttu-id="19af3-182">Balíček šablon ve formě balíčku *.nupkg* NuGet vyžaduje, aby všechny šablony byly uloženy ve složce *obsahu* v rámci balíčku.</span><span class="sxs-lookup"><span data-stu-id="19af3-182">A template pack, in the form of a *.nupkg* NuGet package, requires that all templates be stored in the *content* folder within the package.</span></span> <span data-ttu-id="19af3-183">Existuje několik dalších nastavení, které je třeba přidat do souboru *.csproj,* abyste zajistili, že generovaná *.nupkg* může být nainstalována jako balíček šablon:</span><span class="sxs-lookup"><span data-stu-id="19af3-183">There are a few more settings to add to a *.csproj* file to ensure that the generated *.nupkg* can be installed as a template pack:</span></span>

01. <span data-ttu-id="19af3-184">Nastavení `<IncludeContentInPack>` je nastaveno tak, aby `true` zahrnovalo všechny soubory, které projekt nastaví jako **obsah** v balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="19af3-184">The `<IncludeContentInPack>` setting is set to `true` to include any file the project sets as **content** in the NuGet package.</span></span>
01. <span data-ttu-id="19af3-185">Nastavení `<IncludeBuildOutput>` je nastaveno tak, aby `false` vyloučilo všechny binární soubory generované kompilátorem z balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="19af3-185">The `<IncludeBuildOutput>` setting is set to `false` to exclude all binaries generated by the compiler from the NuGet package.</span></span>
01. <span data-ttu-id="19af3-186">Nastavení `<ContentTargetFolders>` je nastaveno na . `content`</span><span class="sxs-lookup"><span data-stu-id="19af3-186">The `<ContentTargetFolders>` setting is set to `content`.</span></span> <span data-ttu-id="19af3-187">Tím zajistíte, že soubory nastavené jako **obsah** jsou uloženy ve složce *obsahu* v balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="19af3-187">This makes sure that the files set as **content** are stored in the *content* folder in the NuGet package.</span></span> <span data-ttu-id="19af3-188">Tato složka v balíčku NuGet je analyzována systémem šablony dotnet.</span><span class="sxs-lookup"><span data-stu-id="19af3-188">This folder in the NuGet package is parsed by the dotnet template system.</span></span>

<span data-ttu-id="19af3-189">Snadný způsob, jak vyloučit všechny soubory kódu z kompilovány `<Compile Remove="**\*" />` projektem šablony je `<ItemGroup>` pomocí položky v souboru projektu, uvnitř prvku.</span><span class="sxs-lookup"><span data-stu-id="19af3-189">An easy way to exclude all code files from being compiled by your template project is by using the `<Compile Remove="**\*" />` item in your project file, inside an `<ItemGroup>` element.</span></span>

<span data-ttu-id="19af3-190">Snadný způsob, jak strukturovat sadu šablon, je umístit všechny šablony do jednotlivých složek a potom každou složku šablony uvnitř složky *šablon,* která je umístěna ve stejném adresáři jako soubor *.csproj.*</span><span class="sxs-lookup"><span data-stu-id="19af3-190">An easy way to structure your template pack is to put all templates in individual folders, and then each template folder inside of a *templates* folder that is located in the same directory as your *.csproj* file.</span></span> <span data-ttu-id="19af3-191">Tímto způsobem můžete použít jednu položku projektu k zahrnutí všech souborů a složek do *šablon* jako **obsahu**.</span><span class="sxs-lookup"><span data-stu-id="19af3-191">This way, you can use a single project item to include all files and folders in the *templates* as **content**.</span></span> <span data-ttu-id="19af3-192">Uvnitř `<ItemGroup>` prvku vytvořte `<Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />` položku.</span><span class="sxs-lookup"><span data-stu-id="19af3-192">Inside of an `<ItemGroup>` element, create a `<Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />` item.</span></span>

<span data-ttu-id="19af3-193">Zde je příklad *souboru .csproj,* který se řídí všemi výše uvedenými pokyny.</span><span class="sxs-lookup"><span data-stu-id="19af3-193">Here is an example *.csproj* file that follows all of the guidelines above.</span></span> <span data-ttu-id="19af3-194">Zabalí *podřízenou* složku šablon do složky balíčku *obsahu* a vyloučí z kompilován libovolný soubor kódu.</span><span class="sxs-lookup"><span data-stu-id="19af3-194">It packs the *templates* child folder to the *content* package folder and excludes any code file from being compiled.</span></span>

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

<span data-ttu-id="19af3-195">Následující příklad ukazuje strukturu souborů a složek pomocí *souboru .csproj* k vytvoření balíčku šablon.</span><span class="sxs-lookup"><span data-stu-id="19af3-195">The example below demonstrates the file and folder structure of using a *.csproj* to create a template pack.</span></span> <span data-ttu-id="19af3-196">Složka *MyDotnetTemplates.csproj* souboru a šablon jsou *umístěny* v kořenovém adresáři adresáře s názvem *project_folder*.</span><span class="sxs-lookup"><span data-stu-id="19af3-196">The *MyDotnetTemplates.csproj* file and *templates* folder are both located at the root of a directory named *project_folder*.</span></span> <span data-ttu-id="19af3-197">Složka *šablony* obsahuje dvě šablony, *mytemplate1* a *mytemplate2*.</span><span class="sxs-lookup"><span data-stu-id="19af3-197">The *templates* folder contains two templates, *mytemplate1* and *mytemplate2*.</span></span> <span data-ttu-id="19af3-198">Každá šablona obsahuje soubory obsahu a složku *.template.config* s konfiguračním souborem *template.json.*</span><span class="sxs-lookup"><span data-stu-id="19af3-198">Each template has content files and a *.template.config* folder with a *template.json* config file.</span></span>

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

## <a name="installing-a-template"></a><span data-ttu-id="19af3-199">Instalace šablony</span><span class="sxs-lookup"><span data-stu-id="19af3-199">Installing a template</span></span>

<span data-ttu-id="19af3-200">K instalaci balíčku použijte příkaz [dotnet new -i|--install.](dotnet-new.md)</span><span class="sxs-lookup"><span data-stu-id="19af3-200">Use the [dotnet new -i|--install](dotnet-new.md) command to install a package.</span></span>

### <a name="to-install-a-template-from-a-nuget-package-stored-at-nugetorg"></a><span data-ttu-id="19af3-201">Instalace šablony z balíčku NuGet uloženého v nuget.org</span><span class="sxs-lookup"><span data-stu-id="19af3-201">To install a template from a NuGet package stored at nuget.org</span></span>

<span data-ttu-id="19af3-202">K instalaci balíčku šablony použijte identifikátor balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="19af3-202">Use the NuGet package identifier to install a template package.</span></span>

```dotnetcli
dotnet new -i <NUGET_PACKAGE_ID>
```

### <a name="to-install-a-template-from-a-local-nupkg-file"></a><span data-ttu-id="19af3-203">Instalace šablony z místního souboru nupkg</span><span class="sxs-lookup"><span data-stu-id="19af3-203">To install a template from a local nupkg file</span></span>

<span data-ttu-id="19af3-204">Zadejte cestu k souboru balíčku *.nupkg* NuGet.</span><span class="sxs-lookup"><span data-stu-id="19af3-204">Provide the path to a *.nupkg* NuGet package file.</span></span>

```dotnetcli
dotnet new -i <PATH_TO_NUPKG_FILE>
```

### <a name="to-install-a-template-from-a-file-system-directory"></a><span data-ttu-id="19af3-205">Instalace šablony z adresáře systému souborů</span><span class="sxs-lookup"><span data-stu-id="19af3-205">To install a template from a file system directory</span></span>

<span data-ttu-id="19af3-206">Šablony lze nainstalovat ze složky šablony, například ze složky *mytemplate1* z výše uvedeného příkladu.</span><span class="sxs-lookup"><span data-stu-id="19af3-206">Templates can be installed from a template folder, such as the *mytemplate1* folder from the example above.</span></span> <span data-ttu-id="19af3-207">Zadejte cestu ke složce *.template.config.*</span><span class="sxs-lookup"><span data-stu-id="19af3-207">Specify the folder path of the *.template.config* folder.</span></span> <span data-ttu-id="19af3-208">Cesta k adresáři šablony nemusí být absolutní.</span><span class="sxs-lookup"><span data-stu-id="19af3-208">The path to the template directory does not need to be absolute.</span></span> <span data-ttu-id="19af3-209">K odinstalaci šablony, která je nainstalována ze složky, je však vyžadována absolutní cesta.</span><span class="sxs-lookup"><span data-stu-id="19af3-209">However, an absolute path is required to uninstall a template that is installed from a folder.</span></span>

```dotnetcli
dotnet new -i <FILE_SYSTEM_DIRECTORY>
```

## <a name="get-a-list-of-installed-templates"></a><span data-ttu-id="19af3-210">Získání seznamu nainstalovaných šablon</span><span class="sxs-lookup"><span data-stu-id="19af3-210">Get a list of installed templates</span></span>

<span data-ttu-id="19af3-211">Příkaz odinstalovat bez dalších parametrů zobrazí seznam všech nainstalovaných šablon.</span><span class="sxs-lookup"><span data-stu-id="19af3-211">The uninstall command, without any other parameters, will list all installed templates.</span></span>

```dotnetcli
dotnet new -u
```

<span data-ttu-id="19af3-212">Tento příkaz vrátí něco podobného následující výstup:</span><span class="sxs-lookup"><span data-stu-id="19af3-212">That command returns something similar to the following output:</span></span>

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

<span data-ttu-id="19af3-213">První úroveň položek `Currently installed items:` po jsou identifikátory používané při odinstalaci šablony.</span><span class="sxs-lookup"><span data-stu-id="19af3-213">The first level of items after `Currently installed items:` are the identifiers used in uninstalling a template.</span></span> <span data-ttu-id="19af3-214">A ve výše `Microsoft.DotNet.Common.ItemTemplates` uvedeném příkladu, a `Microsoft.DotNet.Common.ProjectTemplates.3.0` jsou uvedeny.</span><span class="sxs-lookup"><span data-stu-id="19af3-214">And in the example above, `Microsoft.DotNet.Common.ItemTemplates` and `Microsoft.DotNet.Common.ProjectTemplates.3.0` are listed.</span></span> <span data-ttu-id="19af3-215">Pokud byla šablona nainstalována pomocí cesty k systému souborů, bude tento identifikátor cesta ke složce *.template.config.*</span><span class="sxs-lookup"><span data-stu-id="19af3-215">If the template was installed by using a file system path, this identifier will the folder path of the *.template.config* folder.</span></span>

## <a name="uninstalling-a-template"></a><span data-ttu-id="19af3-216">Odinstalace šablony</span><span class="sxs-lookup"><span data-stu-id="19af3-216">Uninstalling a template</span></span>

<span data-ttu-id="19af3-217">Chcete-li odinstalovat balíček, použijte příkaz [dotnet new -u|--uninstall.](dotnet-new.md)</span><span class="sxs-lookup"><span data-stu-id="19af3-217">Use the [dotnet new -u|--uninstall](dotnet-new.md) command to uninstall a package.</span></span>

<span data-ttu-id="19af3-218">Pokud byl balíček nainstalován zdrojem NuGet nebo přímo souborem *.nupkg,* zadejte identifikátor.</span><span class="sxs-lookup"><span data-stu-id="19af3-218">If the package was installed by either a NuGet feed or by a *.nupkg* file directly, provide the identifier.</span></span>

```dotnetcli
dotnet new -u <NUGET_PACKAGE_ID>
```

<span data-ttu-id="19af3-219">Pokud byl balíček nainstalován zadáním cesty ke složce *.template.config,* odinstalujte balíček pomocí **této absolutní** cesty.</span><span class="sxs-lookup"><span data-stu-id="19af3-219">If the package was installed by specifying a path to the *.template.config* folder, use that **absolute** path to uninstall the package.</span></span> <span data-ttu-id="19af3-220">Absolutní cesta šablony můžete vidět ve výstupu poskytnutém `dotnet new -u` příkazem.</span><span class="sxs-lookup"><span data-stu-id="19af3-220">You can see the absolute path of the template in the output provided by the `dotnet new -u` command.</span></span> <span data-ttu-id="19af3-221">Další informace naleznete v části [Získání seznamu nainstalovaných šablon](#get-a-list-of-installed-templates) výše.</span><span class="sxs-lookup"><span data-stu-id="19af3-221">For more information, see the [Get a list of installed templates](#get-a-list-of-installed-templates) section above.</span></span>

```dotnetcli
dotnet new -u <ABSOLUTE_FILE_SYSTEM_DIRECTORY>
```

## <a name="create-a-project-using-a-custom-template"></a><span data-ttu-id="19af3-222">Vytvoření projektu pomocí vlastní šablony</span><span class="sxs-lookup"><span data-stu-id="19af3-222">Create a project using a custom template</span></span>

<span data-ttu-id="19af3-223">Po instalaci šablony použijte šablonu provedením `dotnet new <TEMPLATE>` příkazu stejně jako u jakékoli jiné předinstalované šablony.</span><span class="sxs-lookup"><span data-stu-id="19af3-223">After a template is installed, use the template by executing the `dotnet new <TEMPLATE>` command as you would with any other pre-installed template.</span></span> <span data-ttu-id="19af3-224">Můžete také určit [možnosti](dotnet-new.md#options) příkazu, `dotnet new` včetně možností specifických pro šablonu, které jste nakonfigurovali v nastavení šablony.</span><span class="sxs-lookup"><span data-stu-id="19af3-224">You can also specify [options](dotnet-new.md#options) to the `dotnet new` command, including template-specific options you configured in the template settings.</span></span> <span data-ttu-id="19af3-225">Zadej krátký název šablony přímo do příkazu:</span><span class="sxs-lookup"><span data-stu-id="19af3-225">Supply the template's short name directly to the command:</span></span>

```dotnetcli
dotnet new <TEMPLATE>
```

## <a name="see-also"></a><span data-ttu-id="19af3-226">Viz také</span><span class="sxs-lookup"><span data-stu-id="19af3-226">See also</span></span>

- [<span data-ttu-id="19af3-227">Vytvoření vlastní šablony pro dotnet new (kurz)</span><span class="sxs-lookup"><span data-stu-id="19af3-227">Create a custom template for dotnet new (tutorial)</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="19af3-228">dotnet/templating GitHub repo Wiki</span><span class="sxs-lookup"><span data-stu-id="19af3-228">dotnet/templating GitHub repo Wiki</span></span>](https://github.com/dotnet/templating/wiki)
- [<span data-ttu-id="19af3-229">úložiště GitHub u dotnet/dotnet-template-samples GitHub</span><span class="sxs-lookup"><span data-stu-id="19af3-229">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="19af3-230">Jak vytvořit vlastní šablony pro dotnet nové</span><span class="sxs-lookup"><span data-stu-id="19af3-230">How to create your own templates for dotnet new</span></span>](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/)
- [<span data-ttu-id="19af3-231">*template.json* schéma v obchodě Schema JSON</span><span class="sxs-lookup"><span data-stu-id="19af3-231">*template.json* schema at the JSON Schema Store</span></span>](http://json.schemastore.org/template)
