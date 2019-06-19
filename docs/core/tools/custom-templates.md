---
title: Vlastních šablon pro dotnet nové
description: Další informace o vlastních šablon pro jakýkoli druh projektu .NET nebo soubory.
author: thraka
ms.date: 06/14/2019
ms.openlocfilehash: d7e9c549ff132deb4682ba81ab5ff354d6cc1522
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2019
ms.locfileid: "67169634"
---
# <a name="custom-templates-for-dotnet-new"></a><span data-ttu-id="c7c50-103">Vlastních šablon pro dotnet nové</span><span class="sxs-lookup"><span data-stu-id="c7c50-103">Custom templates for dotnet new</span></span>

<span data-ttu-id="c7c50-104">[.NET Core SDK](https://www.microsoft.com/net/download/core) se dodává s mnoha šablony už nainstalované a připravené k použití.</span><span class="sxs-lookup"><span data-stu-id="c7c50-104">The [.NET Core SDK](https://www.microsoft.com/net/download/core) comes with many templates already installed and ready for you to use.</span></span> <span data-ttu-id="c7c50-105">[ `dotnet new` Příkaz](dotnet-new.md) není pouze způsob, jak používat šablony, ale také jak nainstalovat a odinstalovat šablony.</span><span class="sxs-lookup"><span data-stu-id="c7c50-105">The [`dotnet new` command](dotnet-new.md) isn't only the way to use a template, but also how to install and uninstall templates.</span></span> <span data-ttu-id="c7c50-106">Od verze rozhraní .NET Core 2.0, můžete vytvořit vlastní šablony pro každý typ projektu, například aplikace, služby, nástroje nebo knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="c7c50-106">Starting with .NET Core 2.0, you can create your own custom templates for any type of project, such as an app, service, tool, or class library.</span></span> <span data-ttu-id="c7c50-107">Můžete dokonce vytvořit šablonu, jejichž výstupem jsou jeden nebo více nezávislých souborech, jako je konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="c7c50-107">You can even create a template that outputs one or more independent files, such as a configuration file.</span></span>

<span data-ttu-id="c7c50-108">Vlastní šablony můžete nainstalovat z balíčku NuGet na jakékoli NuGet kanálu pomocí odkazu na NuGet *.nupkg* souboru přímo, nebo zadáním systémový adresář souboru, který obsahuje šablonu.</span><span class="sxs-lookup"><span data-stu-id="c7c50-108">You can install custom templates from a NuGet package on any NuGet feed, by referencing a NuGet *.nupkg* file directly, or by specifying a file system directory that contains the template.</span></span> <span data-ttu-id="c7c50-109">Modul šablon nabízí funkce, které umožňují nahraďte hodnotami, zahrnutí a vyloučení souborů a provádění vlastního zpracování operací při použití šablony.</span><span class="sxs-lookup"><span data-stu-id="c7c50-109">The template engine offers features that allow you to replace values, include and exclude files, and execute custom processing operations when your template is used.</span></span>

<span data-ttu-id="c7c50-110">Modul šablon je typu open source a úložiště online kódu je na [dotnet/šablonování](https://github.com/dotnet/templating/) na Githubu.</span><span class="sxs-lookup"><span data-stu-id="c7c50-110">The template engine is open source, and the online code repository is at [dotnet/templating](https://github.com/dotnet/templating/) on GitHub.</span></span> <span data-ttu-id="c7c50-111">Přejděte [dotnet/dotnet – šablony – ukázky](https://github.com/dotnet/dotnet-template-samples) úložiště pro ukázky šablon.</span><span class="sxs-lookup"><span data-stu-id="c7c50-111">Visit the [dotnet/dotnet-template-samples](https://github.com/dotnet/dotnet-template-samples) repo for samples of templates.</span></span> <span data-ttu-id="c7c50-112">Další šablony, včetně šablon od třetích stran, se nacházejí v [dostupných šablon pro dotnet nové](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) na Githubu.</span><span class="sxs-lookup"><span data-stu-id="c7c50-112">More templates, including templates from third parties, are found at [Available templates for dotnet new](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) on GitHub.</span></span> <span data-ttu-id="c7c50-113">Další informace o vytváření a používání vlastních šablon najdete v tématu [tom, jak vytvořit nové vlastní šablony pro dotnet](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/) a [úložiště GitHub dotnet/šablonování Wiki](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="c7c50-113">For more information about creating and using custom templates, see [How to create your own templates for dotnet new](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/) and the [dotnet/templating GitHub repo Wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="c7c50-114">Postupujte podle průvodce a vytvoření šablony najdete v tématu [vytvořit nové vlastní šablony pro dotnet](~/docs/core/tutorials/create-custom-template.md) kurzu.</span><span class="sxs-lookup"><span data-stu-id="c7c50-114">To follow a walkthrough and create a template, see the [Create a custom template for dotnet new](~/docs/core/tutorials/create-custom-template.md) tutorial.</span></span>

### <a name="net-default-templates"></a><span data-ttu-id="c7c50-115">Výchozí šablony .NET</span><span class="sxs-lookup"><span data-stu-id="c7c50-115">.NET default templates</span></span>

<span data-ttu-id="c7c50-116">Při instalaci [.NET Core SDK](https://www.microsoft.com/net/download/core), obdržíte více než tucet předdefinovaných šablon pro vytváření projektů a souborů, včetně konzolové aplikace, knihovny tříd, jednotky testování projektů, aplikace ASP.NET Core (včetně [Angular](https://angular.io/) a [React](https://facebook.github.io/react/) projekty) a konfigurační soubory.</span><span class="sxs-lookup"><span data-stu-id="c7c50-116">When you install the [.NET Core SDK](https://www.microsoft.com/net/download/core), you receive over a dozen built-in templates for creating projects and files, including console apps, class libraries, unit test projects, ASP.NET Core apps (including [Angular](https://angular.io/) and [React](https://facebook.github.io/react/) projects), and configuration files.</span></span> <span data-ttu-id="c7c50-117">Chcete-li seznam integrovaných šablon, spusťte `dotnet new` příkaz `-l|--list` možnost:</span><span class="sxs-lookup"><span data-stu-id="c7c50-117">To list the built-in templates, run the `dotnet new` command with the `-l|--list` option:</span></span>

```console
dotnet new --list
```

## <a name="configuration"></a><span data-ttu-id="c7c50-118">Konfiguraci</span><span class="sxs-lookup"><span data-stu-id="c7c50-118">Configuration</span></span>

<span data-ttu-id="c7c50-119">Šablona se skládá z následujících částí:</span><span class="sxs-lookup"><span data-stu-id="c7c50-119">A template is composed of the following parts:</span></span>

- <span data-ttu-id="c7c50-120">Zdrojové soubory a složky.</span><span class="sxs-lookup"><span data-stu-id="c7c50-120">Source files and folders.</span></span>
- <span data-ttu-id="c7c50-121">Konfigurační soubor (*template.json*).</span><span class="sxs-lookup"><span data-stu-id="c7c50-121">A configuration file (*template.json*).</span></span>

### <a name="source-files-and-folders"></a><span data-ttu-id="c7c50-122">Zdrojové soubory a složky</span><span class="sxs-lookup"><span data-stu-id="c7c50-122">Source files and folders</span></span>

<span data-ttu-id="c7c50-123">Zdrojové soubory a složky patří libovolné soubory a složky šablona modul mají použít, když `dotnet new <TEMPLATE>` příkaz spustit.</span><span class="sxs-lookup"><span data-stu-id="c7c50-123">The source files and folders include whatever files and folders you want the template engine to use when the `dotnet new <TEMPLATE>` command is run.</span></span> <span data-ttu-id="c7c50-124">Modul šablon je navržen pro použití *spustitelné projekty* jako zdrojový kód k vytvoření projektů.</span><span class="sxs-lookup"><span data-stu-id="c7c50-124">The template engine is designed to use *runnable projects* as source code to produce projects.</span></span> <span data-ttu-id="c7c50-125">To má několik výhod:</span><span class="sxs-lookup"><span data-stu-id="c7c50-125">This has several benefits:</span></span>

- <span data-ttu-id="c7c50-126">Modul šablon nevyžaduje vložit speciální tokeny do zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="c7c50-126">The template engine doesn't require you to inject special tokens into your project's source code.</span></span>
- <span data-ttu-id="c7c50-127">Soubory kódu nejsou speciální soubory nebo pro práci s modulem šablony žádným způsobem upravit.</span><span class="sxs-lookup"><span data-stu-id="c7c50-127">The code files aren't special files or modified in any way to work with the template engine.</span></span> <span data-ttu-id="c7c50-128">Nástroje, které standardně používáte při práci s projekty tedy také pracovat obsah šablony.</span><span class="sxs-lookup"><span data-stu-id="c7c50-128">So, the tools you normally use when working with projects also work with template content.</span></span>
- <span data-ttu-id="c7c50-129">Sestavení, spouštět a ladit vaše projekty ze šablony, stejně, jako je tomu u vašich projektů.</span><span class="sxs-lookup"><span data-stu-id="c7c50-129">You build, run, and debug your template projects just like you do for any of your other projects.</span></span>
- <span data-ttu-id="c7c50-130">Můžete rychle vytvořit šablonu z existujícího projektu pouhým přidáním *./.template.config/template.json* konfigurační soubor do projektu.</span><span class="sxs-lookup"><span data-stu-id="c7c50-130">You can quickly create a template from an existing project just by adding a *./.template.config/template.json* configuration file to the project.</span></span>

<span data-ttu-id="c7c50-131">Soubory a složky uložené v šabloně nejsou omezené na formální typy projektů .NET.</span><span class="sxs-lookup"><span data-stu-id="c7c50-131">Files and folders stored in the template aren't limited to formal .NET project types.</span></span> <span data-ttu-id="c7c50-132">Zdrojové soubory a složky může obsahovat veškerý obsah, který chcete vytvořit při použití této šablony i v případě, že modul šablony vytvoří jenom jeden soubor jako výstup.</span><span class="sxs-lookup"><span data-stu-id="c7c50-132">Source files and folders may consist of any content that you wish to create when the template is used, even if the template engine produces just one file as its output.</span></span>

<span data-ttu-id="c7c50-133">Soubory generované záznamem šablony lze upravit na základě logiky a jste zadali v nastavení *template.json* konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="c7c50-133">Files generated by the template can be modified based on logic and settings you've provided in the *template.json* configuration file.</span></span> <span data-ttu-id="c7c50-134">Uživatel může přepsat tato nastavení pomocí předání možností `dotnet new <TEMPLATE>` příkazu.</span><span class="sxs-lookup"><span data-stu-id="c7c50-134">The user can override these settings by passing options to the `dotnet new <TEMPLATE>` command.</span></span> <span data-ttu-id="c7c50-135">Běžným příkladem vlastní logiku poskytuje název pro třídu nebo proměnné ve zdrojovém souboru, který je nasazený v šabloně.</span><span class="sxs-lookup"><span data-stu-id="c7c50-135">A common example of custom logic is providing a name for a class or variable in the code file that's deployed by a template.</span></span>

### <a name="templatejson"></a><span data-ttu-id="c7c50-136">template.json</span><span class="sxs-lookup"><span data-stu-id="c7c50-136">template.json</span></span>

<span data-ttu-id="c7c50-137">*Template.json* soubor umístěn v *. template.config* složku v kořenovém adresáři šablony.</span><span class="sxs-lookup"><span data-stu-id="c7c50-137">The *template.json* file is placed in a *.template.config* folder in the root directory of the template.</span></span> <span data-ttu-id="c7c50-138">Soubor obsahuje informace o konfiguraci pro modul šablony.</span><span class="sxs-lookup"><span data-stu-id="c7c50-138">The file provides configuration information to the template engine.</span></span> <span data-ttu-id="c7c50-139">Minimální požadavky na konfiguraci vyžaduje členů je znázorněno v následující tabulce, což je dostatečná pro vytvoření funkční šablony.</span><span class="sxs-lookup"><span data-stu-id="c7c50-139">The minimum configuration requires the members shown in the following table, which is sufficient to create a functional template.</span></span>

| <span data-ttu-id="c7c50-140">Člen</span><span class="sxs-lookup"><span data-stu-id="c7c50-140">Member</span></span>            | <span data-ttu-id="c7c50-141">Type</span><span class="sxs-lookup"><span data-stu-id="c7c50-141">Type</span></span>          | <span data-ttu-id="c7c50-142">Popis</span><span class="sxs-lookup"><span data-stu-id="c7c50-142">Description</span></span> |
| ----------------- | ------------- | ----------- |
| `$schema`         | <span data-ttu-id="c7c50-143">Identifikátor URI</span><span class="sxs-lookup"><span data-stu-id="c7c50-143">URI</span></span>           | <span data-ttu-id="c7c50-144">Schéma JSON pro *template.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="c7c50-144">The JSON schema for the *template.json* file.</span></span> <span data-ttu-id="c7c50-145">Editory, které podporují schémat JSON povolte úpravy v editoru JSON funkce-li zadána schématu.</span><span class="sxs-lookup"><span data-stu-id="c7c50-145">Editors that support JSON schemas enable JSON-editing features when the schema is specified.</span></span> <span data-ttu-id="c7c50-146">Například [Visual Studio Code](https://code.visualstudio.com/) vyžaduje tento člen pro povolení technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="c7c50-146">For example, [Visual Studio Code](https://code.visualstudio.com/) requires this member to enable IntelliSense.</span></span> <span data-ttu-id="c7c50-147">Použijte hodnotu `http://json.schemastore.org/template`.</span><span class="sxs-lookup"><span data-stu-id="c7c50-147">Use a value of `http://json.schemastore.org/template`.</span></span> |
| `author`          | <span data-ttu-id="c7c50-148">odkazy řetězců</span><span class="sxs-lookup"><span data-stu-id="c7c50-148">string</span></span>        | <span data-ttu-id="c7c50-149">Autor šablony.</span><span class="sxs-lookup"><span data-stu-id="c7c50-149">The author of the template.</span></span> |
| `classifications` | <span data-ttu-id="c7c50-150">Array(String)</span><span class="sxs-lookup"><span data-stu-id="c7c50-150">array(string)</span></span> | <span data-ttu-id="c7c50-151">Nula nebo více vlastností šablony, která uživatel může použít k vyhledávání pro něj najít šablonu.</span><span class="sxs-lookup"><span data-stu-id="c7c50-151">Zero or more characteristics of the template that a user might use to find the template when searching for it.</span></span> <span data-ttu-id="c7c50-152">Klasifikace se také zobrazují v *značky* sloupce, když se objeví v seznamu šablon vytvořený pomocí `dotnet new -l|--list` příkazu.</span><span class="sxs-lookup"><span data-stu-id="c7c50-152">The classifications also appear in the *Tags* column when it appears in a list of templates produced by using the `dotnet new -l|--list` command.</span></span> |
| `identity`        | <span data-ttu-id="c7c50-153">odkazy řetězců</span><span class="sxs-lookup"><span data-stu-id="c7c50-153">string</span></span>        | <span data-ttu-id="c7c50-154">Jedinečný název pro tuto šablonu.</span><span class="sxs-lookup"><span data-stu-id="c7c50-154">A unique name for this template.</span></span> |
| `name`            | <span data-ttu-id="c7c50-155">odkazy řetězců</span><span class="sxs-lookup"><span data-stu-id="c7c50-155">string</span></span>        | <span data-ttu-id="c7c50-156">Název pro šablonu, kterou uživatelé měli vidět.</span><span class="sxs-lookup"><span data-stu-id="c7c50-156">The name for the template that users should see.</span></span> |
| `shortName`       | <span data-ttu-id="c7c50-157">odkazy řetězců</span><span class="sxs-lookup"><span data-stu-id="c7c50-157">string</span></span>        | <span data-ttu-id="c7c50-158">Výchozí název Zkrácený tvar vlastností pro výběr šablonu, která se vztahuje na prostředí, kde název šablony je uživatel zadá, není vybrána přes grafické uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c7c50-158">A default shorthand name for selecting the template that applies to environments where the template name is specified by the user, not selected via a GUI.</span></span> <span data-ttu-id="c7c50-159">Krátký název například je užitečné při použití šablony z příkazového řádku pomocí příkazů rozhraní příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="c7c50-159">For example, the short name is useful when using templates from a command prompt with CLI commands.</span></span> |

<span data-ttu-id="c7c50-160">Úplného schématu pro *template.json* soubor se nachází v umístění [Store schématu JSON](http://json.schemastore.org/template).</span><span class="sxs-lookup"><span data-stu-id="c7c50-160">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="c7c50-161">Další informace o *template.json* souboru, najdete v článku [dotnet šablonování wiki](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="c7c50-161">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

#### <a name="example"></a><span data-ttu-id="c7c50-162">Příklad</span><span class="sxs-lookup"><span data-stu-id="c7c50-162">Example</span></span>

<span data-ttu-id="c7c50-163">Například tady je složka šablony, která obsahuje dva soubory obsahu: *console.cs* a *readme.txt*.</span><span class="sxs-lookup"><span data-stu-id="c7c50-163">For example, here is a template folder that contains two content files: *console.cs* and *readme.txt*.</span></span> <span data-ttu-id="c7c50-164">Všimněte si, že je k požadované složce s názvem trvat *. template.config* obsahující *template.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="c7c50-164">Take notice that there is the required folder named *.template.config* that contains the *template.json* file.</span></span>

```text
└───mytemplate
    │   console.cs
    │   readme.txt
    │
    └───.template.config
            template.json
```

<span data-ttu-id="c7c50-165">*Template.json* soubor bude vypadat nějak takto:</span><span class="sxs-lookup"><span data-stu-id="c7c50-165">The *template.json* file looks like the following:</span></span>

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

<span data-ttu-id="c7c50-166">*Moje_šablona* Instalovatelné šablonovaný balíček je složka.</span><span class="sxs-lookup"><span data-stu-id="c7c50-166">The *mytemplate* folder is an installable template pack.</span></span> <span data-ttu-id="c7c50-167">Po instalaci této sady `shortName` jde použít s `dotnet new` příkazu.</span><span class="sxs-lookup"><span data-stu-id="c7c50-167">Once the pack is installed, the `shortName` can be used with the `dotnet new` command.</span></span> <span data-ttu-id="c7c50-168">Například `dotnet new adatumconsole` by výstup `console.cs` a `readme.txt` soubory do aktuální složky.</span><span class="sxs-lookup"><span data-stu-id="c7c50-168">For example, `dotnet new adatumconsole` would output the `console.cs` and `readme.txt` files to the current folder.</span></span>

## <a name="packing-a-template-into-a-nuget-package-nupkg-file"></a><span data-ttu-id="c7c50-169">Balení šablonu do balíčku NuGet (soubor nupkg)</span><span class="sxs-lookup"><span data-stu-id="c7c50-169">Packing a template into a NuGet package (nupkg file)</span></span>

<span data-ttu-id="c7c50-170">Vlastní šablony, jsou vybavené [balíčku dotnet](dotnet-pack.md) příkazu a *.csproj* souboru.</span><span class="sxs-lookup"><span data-stu-id="c7c50-170">A custom template is packed with the [dotnet pack](dotnet-pack.md) command and a *.csproj* file.</span></span> <span data-ttu-id="c7c50-171">Alternativně [NuGet](https://docs.microsoft.com/nuget/tools/nuget-exe-cli-reference) jde použít s [balíčku nuget](https://docs.microsoft.com/nuget/tools/cli-ref-pack) příkaz spolu s *souboru .nuspec* souboru.</span><span class="sxs-lookup"><span data-stu-id="c7c50-171">Alternatively, [NuGet](https://docs.microsoft.com/nuget/tools/nuget-exe-cli-reference) can be used with the [nuget pack](https://docs.microsoft.com/nuget/tools/cli-ref-pack) command along with a *.nuspec* file.</span></span> <span data-ttu-id="c7c50-172">Ale NuGet vyžaduje rozhraní .NET Framework na Windows a [Mono](https://www.mono-project.com/) v Linuxu a MacOS.</span><span class="sxs-lookup"><span data-stu-id="c7c50-172">However, NuGet requires the .NET Framework on Windows and [Mono](https://www.mono-project.com/) on Linux and MacOS.</span></span>

<span data-ttu-id="c7c50-173">*.Csproj* souboru se mírně liší od tradiční projekt kódu *.csproj* souboru.</span><span class="sxs-lookup"><span data-stu-id="c7c50-173">The *.csproj* file is slightly different from a traditional code-project *.csproj* file.</span></span> <span data-ttu-id="c7c50-174">Mějte na paměti následující nastavení:</span><span class="sxs-lookup"><span data-stu-id="c7c50-174">Note the following settings:</span></span>

01. <span data-ttu-id="c7c50-175">`<PackageType>` Nastavení přidán a nastavit na `Template`.</span><span class="sxs-lookup"><span data-stu-id="c7c50-175">The `<PackageType>` setting is added and set to `Template`.</span></span>
01. <span data-ttu-id="c7c50-176">`<PackageVersion>` Přidán a nastaven na platné nastavení [číslo verze NuGet](/nuget/reference/package-versioning).</span><span class="sxs-lookup"><span data-stu-id="c7c50-176">The `<PackageVersion>` setting is added and set to a valid [NuGet version number](/nuget/reference/package-versioning).</span></span>
01. <span data-ttu-id="c7c50-177">`<PackageId>` Nastavení přidán a nastavit na jedinečný identifikátor.</span><span class="sxs-lookup"><span data-stu-id="c7c50-177">The `<PackageId>` setting is added and set to a unique identifier.</span></span> <span data-ttu-id="c7c50-178">Tento identifikátor slouží k odinstalaci šablonovaný balíček a používá NuGet informační kanály k registraci šablonovaný balíček.</span><span class="sxs-lookup"><span data-stu-id="c7c50-178">This identifier is used to uninstall the template pack and is used by NuGet feeds to register your template pack.</span></span>
01. <span data-ttu-id="c7c50-179">Nastavení obecných metadat by měla být nastavena: `<Title>`, `<Authors>`, `<Description>`, a `<Tags>`.</span><span class="sxs-lookup"><span data-stu-id="c7c50-179">Generic metadata settings should be set: `<Title>`, `<Authors>`, `<Description>`, and `<Tags>`.</span></span>
01. <span data-ttu-id="c7c50-180">`<TargetFramework>` Nastavení musí být nastaveno, i když se nepoužije binární soubor vytvořený pomocí šablony procesu.</span><span class="sxs-lookup"><span data-stu-id="c7c50-180">The `<TargetFramework>` setting must be set, even though the binary produced by the template process isn't used.</span></span> <span data-ttu-id="c7c50-181">V následujícím příkladu je nastavena `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="c7c50-181">In the example below it's set to `netstandard2.0`.</span></span>

<span data-ttu-id="c7c50-182">Šablonovaný balíček ve formě *.nupkg* balíčku NuGet, vyžaduje uložení všechny šablony v *obsah* složky v rámci balíčku.</span><span class="sxs-lookup"><span data-stu-id="c7c50-182">A template pack, in the form of a *.nupkg* NuGet package, requires that all templates be stored in the *content* folder within the package.</span></span> <span data-ttu-id="c7c50-183">Existuje několik dalších nastavení pro přidání do *.csproj* soubor a zkontrolujte, že generované *.nupkg* je možné nainstalovat jako šablonovaný balíček:</span><span class="sxs-lookup"><span data-stu-id="c7c50-183">There are a few more settings to add to a *.csproj* file to ensure that the generated *.nupkg* can be installed as a template pack:</span></span>

01. <span data-ttu-id="c7c50-184">`<IncludeContentInPack>` Nastavená na `true` zahrnout všechny soubory projektu se nastaví jako **obsah** v balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="c7c50-184">The `<IncludeContentInPack>` setting is set to `true` to include any file the project sets as **content** in the NuGet package.</span></span>
01. <span data-ttu-id="c7c50-185">`<IncludeBuildOutput>` Nastavená na `false` vyloučit všechny binární soubory generované kompilátorem z balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="c7c50-185">The `<IncludeBuildOutput>` setting is set to `false` to exclude all binaries generated by the compiler from the NuGet package.</span></span>
01. <span data-ttu-id="c7c50-186">`<ContentTargetFolders>` Nastavená na `content`.</span><span class="sxs-lookup"><span data-stu-id="c7c50-186">The `<ContentTargetFolders>` setting is set to `content`.</span></span> <span data-ttu-id="c7c50-187">Tím je zajištěno, že soubory nastavit jako **obsah** jsou uloženy v *obsah* složky v balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="c7c50-187">This makes sure that the files set as **content** are stored in the *content* folder in the NuGet package.</span></span> <span data-ttu-id="c7c50-188">Tato složka v balíčku NuGet je analyzován systémem šablony pro dotnet.</span><span class="sxs-lookup"><span data-stu-id="c7c50-188">This folder in the NuGet package is parsed by the dotnet template system.</span></span>

<span data-ttu-id="c7c50-189">Snadný způsob, jak vyloučit všechny soubory kódu z kompilovaná pomocí šablony projektu je pomocí `<Compile Remove="**\*" />` uvnitř položky v souboru projektu `<ItemGroup>` elementu.</span><span class="sxs-lookup"><span data-stu-id="c7c50-189">An easy way to exclude all code files from being compiled by your template project is by using the `<Compile Remove="**\*" />` item in your project file, inside an `<ItemGroup>` element.</span></span>

<span data-ttu-id="c7c50-190">Snadný způsob, jak strukturovat váš balíček šablony je umístit všechny šablony do jednotlivé složky a potom každé šablony složky uvnitř *šablony* složku, která se nachází ve stejném adresáři jako vaše *.csproj* soubor.</span><span class="sxs-lookup"><span data-stu-id="c7c50-190">An easy way to structure your template pack is to put all templates in individual folders, and then each template folder inside of a *templates* folder that is located in the same directory as your *.csproj* file.</span></span> <span data-ttu-id="c7c50-191">Tímto způsobem můžete pomocí jednoho projektu položky zahrnout všechny soubory a složky v *šablony* jako **obsah**.</span><span class="sxs-lookup"><span data-stu-id="c7c50-191">This way, you can use a single project item to include all files and folders in the *templates* as **content**.</span></span> <span data-ttu-id="c7c50-192">Uvnitř `<ItemGroup>` elementu, vytvořit `<Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />` položky.</span><span class="sxs-lookup"><span data-stu-id="c7c50-192">Inside of an `<ItemGroup>` element, create a `<Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />` item.</span></span>

<span data-ttu-id="c7c50-193">Tady je příklad *.csproj* souboru, který následuje všechny výše uvedené pokyny.</span><span class="sxs-lookup"><span data-stu-id="c7c50-193">Here is an example *.csproj* file that follows all of the guidelines above.</span></span> <span data-ttu-id="c7c50-194">Jeho balíčky *šablony* podřízené složky do *obsah* balíček složky a vyloučí všechny soubory kódu z kompilován.</span><span class="sxs-lookup"><span data-stu-id="c7c50-194">It packs the *templates* child folder to the *content* package folder and excludes any code file from being compiled.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <PackageType>Template</PackageType>
    <PackageVersion>1.0</PackageVersion>
    <PackageId>AdatumCorporation.Utility.Templates</PackageId>
    <Title>AdatumCorporation Templates</Title>
    <Authors>Me</Authors>
    <Description>Templates to use when creating an application for Adatum Corporation.</Description>
    <Tags>dotnet-new;templates;contoso</Tags>
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

<span data-ttu-id="c7c50-195">Následující příklad ukazuje strukturu souborů a složek pomocí *.csproj* vytvořit balíček šablon.</span><span class="sxs-lookup"><span data-stu-id="c7c50-195">The example below demonstrates the file and folder structure of using a *.csproj* to create a template pack.</span></span> <span data-ttu-id="c7c50-196">*MyDotnetTemplates.csproj* souboru a *šablony* složky jsou umístěné v kořenovém adresáři s názvem *project_folder*.</span><span class="sxs-lookup"><span data-stu-id="c7c50-196">The *MyDotnetTemplates.csproj* file and *templates* folder are both located at the root of a directory named *project_folder*.</span></span> <span data-ttu-id="c7c50-197">*Šablony* složka obsahuje dvě šablony *mytemplate1* a *mytemplate2*.</span><span class="sxs-lookup"><span data-stu-id="c7c50-197">The *templates* folder contains two templates, *mytemplate1* and *mytemplate2*.</span></span> <span data-ttu-id="c7c50-198">Každá šablona má soubory obsahu a *. template.config* složka s *template.json* konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="c7c50-198">Each template has content files and a *.template.config* folder with a *template.json* config file.</span></span>

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

## <a name="installing-a-template"></a><span data-ttu-id="c7c50-199">Instalace šablony</span><span class="sxs-lookup"><span data-stu-id="c7c50-199">Installing a template</span></span>

<span data-ttu-id="c7c50-200">Použití [dotnet nové -i |--nainstalovat](dotnet-new.md) příkaz k instalaci balíčku.</span><span class="sxs-lookup"><span data-stu-id="c7c50-200">Use the [dotnet new -i|--install](dotnet-new.md) command to install a package.</span></span>

### <a name="to-install-a-template-from-a-nuget-package-stored-at-nugetorg"></a><span data-ttu-id="c7c50-201">Chcete-li nainstalovat šablony z balíčku NuGet uloženou v nuget.org</span><span class="sxs-lookup"><span data-stu-id="c7c50-201">To install a template from a NuGet package stored at nuget.org</span></span>

<span data-ttu-id="c7c50-202">Použijte identifikátor balíčku NuGet k instalaci balíčku šablony.</span><span class="sxs-lookup"><span data-stu-id="c7c50-202">Use the NuGet package identifier to install a template package.</span></span>

```console
dotnet new -i <NUGET_PACKAGE_ID>
```

### <a name="to-install-a-template-from-a-local-nupkg-file"></a><span data-ttu-id="c7c50-203">Chcete-li nainstalovat šablony ze souboru místní nupkg</span><span class="sxs-lookup"><span data-stu-id="c7c50-203">To install a template from a local nupkg file</span></span>

<span data-ttu-id="c7c50-204">Zadejte cestu k *.nupkg* soubor balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="c7c50-204">Provide the path to a *.nupkg* NuGet package file.</span></span>

```console
dotnet new -i <PATH_TO_NUPKG_FILE>
```

### <a name="to-install-a-template-from-a-file-system-directory"></a><span data-ttu-id="c7c50-205">Chcete-li nainstalovat šablony z adresáře systému souborů</span><span class="sxs-lookup"><span data-stu-id="c7c50-205">To install a template from a file system directory</span></span>

<span data-ttu-id="c7c50-206">Šablony si můžete nainstalovat pomocí složky šablony, jako *mytemplate1* složky jako v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="c7c50-206">Templates can be installed from a template folder, such as the *mytemplate1* folder from the example above.</span></span> <span data-ttu-id="c7c50-207">Zadejte cestu ke složce aplikace *. template.config* složky.</span><span class="sxs-lookup"><span data-stu-id="c7c50-207">Specify the folder path of the *.template.config* folder.</span></span> <span data-ttu-id="c7c50-208">Cesta k adresáři šablony nemusí být absolutní.</span><span class="sxs-lookup"><span data-stu-id="c7c50-208">The path to the template directory does not need to be absolute.</span></span> <span data-ttu-id="c7c50-209">Absolutní cesta je však nutné odinstalovat šablonu, která je nainstalovaná ze složky.</span><span class="sxs-lookup"><span data-stu-id="c7c50-209">However, an absolute path is required to uninstall a template that is installed from a folder.</span></span>

```console
dotnet new -i <FILE_SYSTEM_DIRECTORY>
```

## <a name="get-a-list-of-installed-templates"></a><span data-ttu-id="c7c50-210">Získání seznamu nainstalovaných šablon</span><span class="sxs-lookup"><span data-stu-id="c7c50-210">Get a list of installed templates</span></span>

<span data-ttu-id="c7c50-211">Příkaz odinstalace, bez jakékoli další parametry, zobrazí se seznam všech nainstalovaných šablon.</span><span class="sxs-lookup"><span data-stu-id="c7c50-211">The uninstall command, without any other parameters, will list all installed templates.</span></span>

```console
dotnet new -u
```

<span data-ttu-id="c7c50-212">Tento příkaz vrátí podobně jako následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c7c50-212">That command returns something similar to the following output:</span></span>

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

<span data-ttu-id="c7c50-213">První úroveň položky po `Currently installed items:` jsou identifikátory použitými v odinstalaci šablony.</span><span class="sxs-lookup"><span data-stu-id="c7c50-213">The first level of items after `Currently installed items:` are the identifiers used in uninstalling a template.</span></span> <span data-ttu-id="c7c50-214">A v příkladu výše `Microsoft.DotNet.Common.ItemTemplates` a `Microsoft.DotNet.Common.ProjectTemplates.3.0` jsou uvedeny.</span><span class="sxs-lookup"><span data-stu-id="c7c50-214">And in the example above, `Microsoft.DotNet.Common.ItemTemplates` and `Microsoft.DotNet.Common.ProjectTemplates.3.0` are listed.</span></span> <span data-ttu-id="c7c50-215">Pokud šablona byla nainstalována pomocí cestu systému souborů, bude tento identifikátor cesta ke složce *. template.config* složky.</span><span class="sxs-lookup"><span data-stu-id="c7c50-215">If the template was installed by using a file system path, this identifier will the folder path of the *.template.config* folder.</span></span>

## <a name="uninstalling-a-template"></a><span data-ttu-id="c7c50-216">Odinstalace šablony</span><span class="sxs-lookup"><span data-stu-id="c7c50-216">Uninstalling a template</span></span>

<span data-ttu-id="c7c50-217">Použití [dotnet nové -u |--odinstalovat](dotnet-new.md) příkaz pro odinstalaci balíčku.</span><span class="sxs-lookup"><span data-stu-id="c7c50-217">Use the [dotnet new -u|--uninstall](dotnet-new.md) command to uninstall a package.</span></span>

<span data-ttu-id="c7c50-218">Pokud balíček nainstaloval kanál NuGet nebo parametrem *.nupkg* přímo soubor, zadejte identifikátor.</span><span class="sxs-lookup"><span data-stu-id="c7c50-218">If the package was installed by either a NuGet feed or by a *.nupkg* file directly, provide the identifier.</span></span>

```console
dotnet new -u <NUGET_PACKAGE_ID>
```

<span data-ttu-id="c7c50-219">Pokud zadáte cestu k byl nainstalován balíček *. template.config* složky, použít **absolutní** cestu k odinstalaci balíčku.</span><span class="sxs-lookup"><span data-stu-id="c7c50-219">If the package was installed by specifying a path to the *.template.config* folder, use that **absolute** path to uninstall the package.</span></span> <span data-ttu-id="c7c50-220">Zobrazí se absolutní cesta šablony v výstup poskytovaný `dotnet new -u` příkazu.</span><span class="sxs-lookup"><span data-stu-id="c7c50-220">You can see the absolute path of the template in the output provided by the `dotnet new -u` command.</span></span> <span data-ttu-id="c7c50-221">Další informace najdete v tématu [získání seznamu nainstalovaných šablon](#get-a-list-of-installed-templates) výše uvedené části.</span><span class="sxs-lookup"><span data-stu-id="c7c50-221">For more information, see the [Get a list of installed templates](#get-a-list-of-installed-templates) section above.</span></span>

```console
dotnet new -u <ABSOLUTE_FILE_SYSTEM_DIRECTORY>
```

## <a name="create-a-project-using-a-custom-template"></a><span data-ttu-id="c7c50-222">Vytvořte projekt pomocí vlastní šablony</span><span class="sxs-lookup"><span data-stu-id="c7c50-222">Create a project using a custom template</span></span>

<span data-ttu-id="c7c50-223">Po instalaci šablony, použijte šablonu pomocí provádí `dotnet new <TEMPLATE>` příkaz stejně jako u jiných předem nainstalovaných šablon.</span><span class="sxs-lookup"><span data-stu-id="c7c50-223">After a template is installed, use the template by executing the `dotnet new <TEMPLATE>` command as you would with any other pre-installed template.</span></span> <span data-ttu-id="c7c50-224">Můžete také určit [možnosti](dotnet-new.md#options) k `dotnet new` příkazu, včetně možnosti specifické pro šablony jste nakonfigurovali v nastavení šablony.</span><span class="sxs-lookup"><span data-stu-id="c7c50-224">You can also specify [options](dotnet-new.md#options) to the `dotnet new` command, including template-specific options you configured in the template settings.</span></span> <span data-ttu-id="c7c50-225">Zadejte krátký název šablony přímo k příkazu:</span><span class="sxs-lookup"><span data-stu-id="c7c50-225">Supply the template's short name directly to the command:</span></span>

```console
dotnet new <TEMPLATE>
```

## <a name="see-also"></a><span data-ttu-id="c7c50-226">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c7c50-226">See also</span></span>

- [<span data-ttu-id="c7c50-227">Vytvoření vlastní šablony pro dotnet new (kurz)</span><span class="sxs-lookup"><span data-stu-id="c7c50-227">Create a custom template for dotnet new (tutorial)</span></span>](../tutorials/create-custom-template.md)
- [<span data-ttu-id="c7c50-228">úložiště GitHub DotNet/šablonování Wiki</span><span class="sxs-lookup"><span data-stu-id="c7c50-228">dotnet/templating GitHub repo Wiki</span></span>](https://github.com/dotnet/templating/wiki)
- [<span data-ttu-id="c7c50-229">úložiště GitHub DotNet/dotnet – šablony – ukázky</span><span class="sxs-lookup"><span data-stu-id="c7c50-229">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="c7c50-230">Jak vytvořit nové vlastní šablony pro dotnet</span><span class="sxs-lookup"><span data-stu-id="c7c50-230">How to create your own templates for dotnet new</span></span>](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/)
- [<span data-ttu-id="c7c50-231">*Template.JSON* schématu na Store schématu JSON</span><span class="sxs-lookup"><span data-stu-id="c7c50-231">*template.json* schema at the JSON Schema Store</span></span>](http://json.schemastore.org/template)
