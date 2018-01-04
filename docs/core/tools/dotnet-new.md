---
title: "nový příkaz DotNet - .NET Core rozhraní příkazového řádku"
description: "Nový příkaz dotnet vytvoří nové projekty .NET Core na základě zadané šablony."
keywords: "DotNet nové rozhraní příkazového řádku, rozhraní příkazového řádku příkaz .NET Core"
author: mairaw
ms.author: mairaw
ms.date: 08/13/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: fcc3ed2e-9265-4d50-b59e-dc2e5c190b34
ms.workload: dotnetcore
ms.openlocfilehash: f5815e1ad2a36a8ef3279f6ff83465dba9ec5d50
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-new"></a><span data-ttu-id="729dd-104">nové DotNet.</span><span class="sxs-lookup"><span data-stu-id="729dd-104">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="729dd-105">Název</span><span class="sxs-lookup"><span data-stu-id="729dd-105">Name</span></span>

<span data-ttu-id="729dd-106">`dotnet new`-Vytvoří nový projekt, konfigurační soubor nebo řešení v závislosti na určené šablony.</span><span class="sxs-lookup"><span data-stu-id="729dd-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="729dd-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="729dd-107">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="729dd-108">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="729dd-108">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="729dd-109">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="729dd-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="729dd-110">Popis</span><span class="sxs-lookup"><span data-stu-id="729dd-110">Description</span></span>

<span data-ttu-id="729dd-111">`dotnet new` Příkaz nabízí pohodlný způsob, jak inicializovat platný projekt .NET Core.</span><span class="sxs-lookup"><span data-stu-id="729dd-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span> 

<span data-ttu-id="729dd-112">Příkaz volání [modulu šablon](https://github.com/dotnet/templating) vytvořit artefakty na disku na základě určené šablony a možnosti.</span><span class="sxs-lookup"><span data-stu-id="729dd-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="729dd-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="729dd-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="729dd-114">Šablona pro vytvoření instance při vyvolání příkazu.</span><span class="sxs-lookup"><span data-stu-id="729dd-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="729dd-115">Každá šablona může mít specifické možnosti, které lze předat.</span><span class="sxs-lookup"><span data-stu-id="729dd-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="729dd-116">Další informace najdete v tématu [možnosti šablony](#template-options).</span><span class="sxs-lookup"><span data-stu-id="729dd-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="729dd-117">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="729dd-117">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="729dd-118">Příkaz obsahuje seznam výchozích šablon.</span><span class="sxs-lookup"><span data-stu-id="729dd-118">The command contains a default list of templates.</span></span> <span data-ttu-id="729dd-119">Použití `dotnet new -l` získat seznam dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="729dd-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="729dd-120">V následující tabulce jsou uvedeny šablony, které jsou předinstalované .NET Core 2.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="729dd-120">The following table shows the templates that come pre-installed with the .NET Core 2.0 SDK.</span></span> <span data-ttu-id="729dd-121">Výchozí jazyk pro šablonu se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="729dd-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="729dd-122">Popis šablony</span><span class="sxs-lookup"><span data-stu-id="729dd-122">Template description</span></span>                          | <span data-ttu-id="729dd-123">Název šablony</span><span class="sxs-lookup"><span data-stu-id="729dd-123">Template name</span></span>  | <span data-ttu-id="729dd-124">Jazyky</span><span class="sxs-lookup"><span data-stu-id="729dd-124">Languages</span></span>     |
|----------------------------------------------|----------------|---------------|
| <span data-ttu-id="729dd-125">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="729dd-125">Console application</span></span>                          | <span data-ttu-id="729dd-126">konzola</span><span class="sxs-lookup"><span data-stu-id="729dd-126">console</span></span>        | <span data-ttu-id="729dd-127">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="729dd-127">[C#], F#, VB</span></span>  |
| <span data-ttu-id="729dd-128">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="729dd-128">Class library</span></span>                                | <span data-ttu-id="729dd-129">classlib</span><span class="sxs-lookup"><span data-stu-id="729dd-129">classlib</span></span>       | <span data-ttu-id="729dd-130">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="729dd-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="729dd-131">Projektu testování částí</span><span class="sxs-lookup"><span data-stu-id="729dd-131">Unit test project</span></span>                            | <span data-ttu-id="729dd-132">mstestu</span><span class="sxs-lookup"><span data-stu-id="729dd-132">mstest</span></span>         | <span data-ttu-id="729dd-133">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="729dd-133">[C#], F#, VB</span></span>  |
| <span data-ttu-id="729dd-134">xUnit testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="729dd-134">xUnit test project</span></span>                           | <span data-ttu-id="729dd-135">xunit</span><span class="sxs-lookup"><span data-stu-id="729dd-135">xunit</span></span>          | <span data-ttu-id="729dd-136">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="729dd-136">[C#], F#, VB</span></span>  |
| <span data-ttu-id="729dd-137">ASP.NET Core prázdný</span><span class="sxs-lookup"><span data-stu-id="729dd-137">ASP.NET Core empty</span></span>                           | <span data-ttu-id="729dd-138">webové</span><span class="sxs-lookup"><span data-stu-id="729dd-138">web</span></span>            | <span data-ttu-id="729dd-139">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="729dd-139">[C#], F#</span></span>      |
| <span data-ttu-id="729dd-140">Webové aplikace ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="729dd-140">ASP.NET Core Web App (Model-View-Controller)</span></span> | <span data-ttu-id="729dd-141">MVC</span><span class="sxs-lookup"><span data-stu-id="729dd-141">mvc</span></span>            | <span data-ttu-id="729dd-142">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="729dd-142">[C#], F#</span></span>      |
| <span data-ttu-id="729dd-143">Webové aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="729dd-143">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="729dd-144">syntaxe Razor</span><span class="sxs-lookup"><span data-stu-id="729dd-144">razor</span></span>          | <span data-ttu-id="729dd-145">[C#]</span><span class="sxs-lookup"><span data-stu-id="729dd-145">[C#]</span></span>          |
| <span data-ttu-id="729dd-146">ASP.NET Core s úhlová</span><span class="sxs-lookup"><span data-stu-id="729dd-146">ASP.NET Core with Angular</span></span>                    | <span data-ttu-id="729dd-147">úhlová</span><span class="sxs-lookup"><span data-stu-id="729dd-147">angular</span></span>        | <span data-ttu-id="729dd-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="729dd-148">[C#]</span></span>          |
| <span data-ttu-id="729dd-149">ASP.NET Core s React.js</span><span class="sxs-lookup"><span data-stu-id="729dd-149">ASP.NET Core with React.js</span></span>                   | <span data-ttu-id="729dd-150">Reagovat</span><span class="sxs-lookup"><span data-stu-id="729dd-150">react</span></span>          | <span data-ttu-id="729dd-151">[C#]</span><span class="sxs-lookup"><span data-stu-id="729dd-151">[C#]</span></span>          |
| <span data-ttu-id="729dd-152">ASP.NET Core s React.js a – obnovení</span><span class="sxs-lookup"><span data-stu-id="729dd-152">ASP.NET Core with React.js and Redux</span></span>         | <span data-ttu-id="729dd-153">reactredux</span><span class="sxs-lookup"><span data-stu-id="729dd-153">reactredux</span></span>     | <span data-ttu-id="729dd-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="729dd-154">[C#]</span></span>          |
| <span data-ttu-id="729dd-155">Jádro ASP.NET Web API</span><span class="sxs-lookup"><span data-stu-id="729dd-155">ASP.NET Core Web API</span></span>                         | <span data-ttu-id="729dd-156">webapi</span><span class="sxs-lookup"><span data-stu-id="729dd-156">webapi</span></span>         | <span data-ttu-id="729dd-157">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="729dd-157">[C#], F#</span></span>      |
| <span data-ttu-id="729dd-158">soubor Global.JSON</span><span class="sxs-lookup"><span data-stu-id="729dd-158">global.json file</span></span>                             | <span data-ttu-id="729dd-159">globaljson</span><span class="sxs-lookup"><span data-stu-id="729dd-159">globaljson</span></span>     |               |
| <span data-ttu-id="729dd-160">Konfigurace Nuget</span><span class="sxs-lookup"><span data-stu-id="729dd-160">Nuget config</span></span>                                 | <span data-ttu-id="729dd-161">nugetconfig</span><span class="sxs-lookup"><span data-stu-id="729dd-161">nugetconfig</span></span>    |               |
| <span data-ttu-id="729dd-162">Webové konfigurace</span><span class="sxs-lookup"><span data-stu-id="729dd-162">Web config</span></span>                                   | <span data-ttu-id="729dd-163">WebConfig</span><span class="sxs-lookup"><span data-stu-id="729dd-163">webconfig</span></span>      |               |
| <span data-ttu-id="729dd-164">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="729dd-164">Solution file</span></span>                                | <span data-ttu-id="729dd-165">SLN –</span><span class="sxs-lookup"><span data-stu-id="729dd-165">sln</span></span>            |               |
| <span data-ttu-id="729dd-166">Stránky Razor</span><span class="sxs-lookup"><span data-stu-id="729dd-166">Razor page</span></span>                                   | <span data-ttu-id="729dd-167">stránka</span><span class="sxs-lookup"><span data-stu-id="729dd-167">page</span></span>           |               |
| <span data-ttu-id="729dd-168">MVC nebo ViewImports</span><span class="sxs-lookup"><span data-stu-id="729dd-168">MVC/ViewImports</span></span>                              | <span data-ttu-id="729dd-169">viewimports</span><span class="sxs-lookup"><span data-stu-id="729dd-169">viewimports</span></span>    |               |
| <span data-ttu-id="729dd-170">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="729dd-170">MVC ViewStart</span></span>                                | <span data-ttu-id="729dd-171">viewstart</span><span class="sxs-lookup"><span data-stu-id="729dd-171">viewstart</span></span>      |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="729dd-172">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="729dd-172">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="729dd-173">Příkaz obsahuje seznam výchozích šablon.</span><span class="sxs-lookup"><span data-stu-id="729dd-173">The command contains a default list of templates.</span></span> <span data-ttu-id="729dd-174">Použití `dotnet new -all` získat seznam dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="729dd-174">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="729dd-175">V následující tabulce jsou uvedeny šablony, které jsou předinstalované .NET Core 1.x SDK.</span><span class="sxs-lookup"><span data-stu-id="729dd-175">The following table shows the templates that come pre-installed with the .NET Core 1.x SDK.</span></span> <span data-ttu-id="729dd-176">Výchozí jazyk pro šablonu se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="729dd-176">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="729dd-177">Popis šablony</span><span class="sxs-lookup"><span data-stu-id="729dd-177">Template description</span></span>  | <span data-ttu-id="729dd-178">Název šablony</span><span class="sxs-lookup"><span data-stu-id="729dd-178">Template name</span></span>  | <span data-ttu-id="729dd-179">Jazyky</span><span class="sxs-lookup"><span data-stu-id="729dd-179">Languages</span></span> |
|----------------------|----------------|-----------|
| <span data-ttu-id="729dd-180">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="729dd-180">Console application</span></span>  | <span data-ttu-id="729dd-181">konzola</span><span class="sxs-lookup"><span data-stu-id="729dd-181">console</span></span>        | <span data-ttu-id="729dd-182">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="729dd-182">[C#], F#</span></span>  |
| <span data-ttu-id="729dd-183">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="729dd-183">Class library</span></span>        | <span data-ttu-id="729dd-184">classlib</span><span class="sxs-lookup"><span data-stu-id="729dd-184">classlib</span></span>       | <span data-ttu-id="729dd-185">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="729dd-185">[C#], F#</span></span>  |
| <span data-ttu-id="729dd-186">Projektu testování částí</span><span class="sxs-lookup"><span data-stu-id="729dd-186">Unit test project</span></span>    | <span data-ttu-id="729dd-187">mstestu</span><span class="sxs-lookup"><span data-stu-id="729dd-187">mstest</span></span>         | <span data-ttu-id="729dd-188">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="729dd-188">[C#], F#</span></span>  |
| <span data-ttu-id="729dd-189">xUnit testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="729dd-189">xUnit test project</span></span>   | <span data-ttu-id="729dd-190">xunit</span><span class="sxs-lookup"><span data-stu-id="729dd-190">xunit</span></span>          | <span data-ttu-id="729dd-191">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="729dd-191">[C#], F#</span></span>  |
| <span data-ttu-id="729dd-192">ASP.NET Core prázdný</span><span class="sxs-lookup"><span data-stu-id="729dd-192">ASP.NET Core empty</span></span>   | <span data-ttu-id="729dd-193">webové</span><span class="sxs-lookup"><span data-stu-id="729dd-193">web</span></span>            | <span data-ttu-id="729dd-194">[C#]</span><span class="sxs-lookup"><span data-stu-id="729dd-194">[C#]</span></span>      |
| <span data-ttu-id="729dd-195">Webové aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="729dd-195">ASP.NET Core Web App</span></span> | <span data-ttu-id="729dd-196">MVC</span><span class="sxs-lookup"><span data-stu-id="729dd-196">mvc</span></span>            | <span data-ttu-id="729dd-197">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="729dd-197">[C#], F#</span></span>  |
| <span data-ttu-id="729dd-198">Jádro ASP.NET Web API</span><span class="sxs-lookup"><span data-stu-id="729dd-198">ASP.NET Core Web API</span></span> | <span data-ttu-id="729dd-199">webapi</span><span class="sxs-lookup"><span data-stu-id="729dd-199">webapi</span></span>         | <span data-ttu-id="729dd-200">[C#]</span><span class="sxs-lookup"><span data-stu-id="729dd-200">[C#]</span></span>      |
| <span data-ttu-id="729dd-201">Konfigurace Nuget</span><span class="sxs-lookup"><span data-stu-id="729dd-201">Nuget config</span></span>         | <span data-ttu-id="729dd-202">nugetconfig</span><span class="sxs-lookup"><span data-stu-id="729dd-202">nugetconfig</span></span>    |           |
| <span data-ttu-id="729dd-203">Webové konfigurace</span><span class="sxs-lookup"><span data-stu-id="729dd-203">Web config</span></span>           | <span data-ttu-id="729dd-204">WebConfig</span><span class="sxs-lookup"><span data-stu-id="729dd-204">webconfig</span></span>      |           |
| <span data-ttu-id="729dd-205">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="729dd-205">Solution file</span></span>        | <span data-ttu-id="729dd-206">SLN –</span><span class="sxs-lookup"><span data-stu-id="729dd-206">sln</span></span>            |           |

---

## <a name="options"></a><span data-ttu-id="729dd-207">Možnosti</span><span class="sxs-lookup"><span data-stu-id="729dd-207">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="729dd-208">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="729dd-208">.NET Core 2.x</span></span>](#tab/netcore2x)

`--force`

<span data-ttu-id="729dd-209">Vynutí obsah má být vygenerován i v případě, že se změní stávající soubory.</span><span class="sxs-lookup"><span data-stu-id="729dd-209">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="729dd-210">To je potřeba, když výstupnímu adresáři již obsahuje projektu.</span><span class="sxs-lookup"><span data-stu-id="729dd-210">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="729dd-211">Vytiskne nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="729dd-211">Prints out help for the command.</span></span> <span data-ttu-id="729dd-212">Nelze vyvolat pro `dotnet new` příkaz sám sebe nebo pro všechny šablony, jako například `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="729dd-212">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="729dd-213">Nainstaluje sadu zdroje nebo šablony z `PATH` nebo `NUGET_ID` zadat.</span><span class="sxs-lookup"><span data-stu-id="729dd-213">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="729dd-214">Informace o vytváření vlastních šablon najdete v tématu [vlastních šablon pro dotnet nové](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="729dd-214">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="729dd-215">Obsahuje seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="729dd-215">Lists templates containing the specified name.</span></span> <span data-ttu-id="729dd-216">Pokud je vyvolána pro `dotnet new` příkaz, zobrazí seznam možných šablony, které jsou k dispozici pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="729dd-216">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="729dd-217">Například pokud adresář již obsahuje projekt, nepodporuje zobrazí seznam všech šablon projektu.</span><span class="sxs-lookup"><span data-stu-id="729dd-217">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="729dd-218">Jazyk šablonu, kterou chcete vytvořit.</span><span class="sxs-lookup"><span data-stu-id="729dd-218">The language of the template to create.</span></span> <span data-ttu-id="729dd-219">Jazyk přijata, se liší podle šablony (viz výchozí hodnoty v [argumenty](#arguments) části).</span><span class="sxs-lookup"><span data-stu-id="729dd-219">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="729dd-220">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="729dd-220">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="729dd-221">Název pro vytvoření výstupu.</span><span class="sxs-lookup"><span data-stu-id="729dd-221">The name for the created output.</span></span> <span data-ttu-id="729dd-222">Pokud není zadán žádný název, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="729dd-222">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="729dd-223">Umístění pro generovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="729dd-223">Location to place the generated output.</span></span> <span data-ttu-id="729dd-224">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="729dd-224">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="729dd-225">Filtry šablony vycházející z dostupných typů.</span><span class="sxs-lookup"><span data-stu-id="729dd-225">Filters templates based on available types.</span></span> <span data-ttu-id="729dd-226">Předdefinované hodnoty jsou "projektu", "položka" nebo "ostatní".</span><span class="sxs-lookup"><span data-stu-id="729dd-226">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="729dd-227">Odinstaluje sadu zdroje nebo šablony v `PATH` nebo `NUGET_ID` zadat.</span><span class="sxs-lookup"><span data-stu-id="729dd-227">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="729dd-228">Chcete-li odinstalovat šablony pomocí `PATH`, budete muset plně kvalifikovanou cestu.</span><span class="sxs-lookup"><span data-stu-id="729dd-228">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="729dd-229">Například *C: či uživatelů nebo\<uživatele > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z obsahující složka se není.</span><span class="sxs-lookup"><span data-stu-id="729dd-229">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="729dd-230">Kromě toho nezahrnují konečné ukončující lomítko adresáře na cestu k šabloně.</span><span class="sxs-lookup"><span data-stu-id="729dd-230">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="729dd-231">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="729dd-231">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="729dd-232">Při spuštění v kontextu jsou uvedeny všechny šablony pro konkrétní typ projektu `dotnet new` příkaz samostatně.</span><span class="sxs-lookup"><span data-stu-id="729dd-232">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="729dd-233">Při spuštění v rámci konkrétní šablonu, jako například `dotnet new web -all`, `-all` interpretována jako vytvoření příznak force.</span><span class="sxs-lookup"><span data-stu-id="729dd-233">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="729dd-234">To je potřeba, když výstupnímu adresáři již obsahuje projektu.</span><span class="sxs-lookup"><span data-stu-id="729dd-234">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="729dd-235">Vytiskne nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="729dd-235">Prints out help for the command.</span></span> <span data-ttu-id="729dd-236">Nelze vyvolat pro `dotnet new` příkaz sám sebe nebo pro všechny šablony, jako například `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="729dd-236">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="729dd-237">Obsahuje seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="729dd-237">Lists templates containing the specified name.</span></span> <span data-ttu-id="729dd-238">Pokud je vyvolána pro `dotnet new` příkaz, zobrazí seznam možných šablony, které jsou k dispozici pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="729dd-238">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="729dd-239">Například pokud adresář již obsahuje projekt, nepodporuje zobrazí seznam všech šablon projektu.</span><span class="sxs-lookup"><span data-stu-id="729dd-239">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="729dd-240">Jazyk šablonu, kterou chcete vytvořit.</span><span class="sxs-lookup"><span data-stu-id="729dd-240">The language of the template to create.</span></span> <span data-ttu-id="729dd-241">Jazyk přijata, se liší podle šablony (viz výchozí hodnoty v [argumenty](#arguments) části).</span><span class="sxs-lookup"><span data-stu-id="729dd-241">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="729dd-242">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="729dd-242">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="729dd-243">Název pro vytvoření výstupu.</span><span class="sxs-lookup"><span data-stu-id="729dd-243">The name for the created output.</span></span> <span data-ttu-id="729dd-244">Pokud není zadán žádný název, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="729dd-244">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="729dd-245">Umístění pro generovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="729dd-245">Location to place the generated output.</span></span> <span data-ttu-id="729dd-246">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="729dd-246">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="729dd-247">Možnosti šablony</span><span class="sxs-lookup"><span data-stu-id="729dd-247">Template options</span></span>

<span data-ttu-id="729dd-248">Každá šablona projektu může mít další možnosti, které jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="729dd-248">Each project template may have additional options available.</span></span> <span data-ttu-id="729dd-249">Základní šablony mají následující možnosti:</span><span class="sxs-lookup"><span data-stu-id="729dd-249">The core templates have the following additional options:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="729dd-250">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="729dd-250">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="729dd-251">**konzole úhlová, reagovat, reactredux**</span><span class="sxs-lookup"><span data-stu-id="729dd-251">**console, angular, react, reactredux**</span></span>

<span data-ttu-id="729dd-252">`--no-restore`-Nepodporuje provedení implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="729dd-252">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="729dd-253">**classlib**</span><span class="sxs-lookup"><span data-stu-id="729dd-253">**classlib**</span></span>

<span data-ttu-id="729dd-254">`-f|--framework <FRAMEWORK>`-Určuje [framework](../../standard/frameworks.md) k cíli.</span><span class="sxs-lookup"><span data-stu-id="729dd-254">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="729dd-255">Hodnoty: `netcoreapp2.0` pro vytvoření základní knihovny tříd rozhraní .NET nebo `netstandard2.0` vytvořit standardní knihovny tříd rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="729dd-255">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="729dd-256">Výchozí hodnota je `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="729dd-256">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="729dd-257">`--no-restore`-Nepodporuje provedení implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="729dd-257">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="729dd-258">**mstestu xunit**</span><span class="sxs-lookup"><span data-stu-id="729dd-258">**mstest, xunit**</span></span>

<span data-ttu-id="729dd-259">`-p|--enable-pack`– Umožňuje vytváření balíčků pro projekt pomocí [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="729dd-259">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="729dd-260">`--no-restore`-Nepodporuje provedení implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="729dd-260">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="729dd-261">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="729dd-261">**globaljson**</span></span>

<span data-ttu-id="729dd-262">`--sdk-version <VERSION_NUMBER>`-Určuje verzi rozhraní .NET Core SDK pro použití v *global.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="729dd-262">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="729dd-263">**webové**</span><span class="sxs-lookup"><span data-stu-id="729dd-263">**web**</span></span>

<span data-ttu-id="729dd-264">`--use-launch-settings`-Zahrnuje *launchSettings.json* ve výstupu vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="729dd-264">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="729dd-265">`--no-restore`-Nepodporuje provedení implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="729dd-265">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="729dd-266">**webapi**</span><span class="sxs-lookup"><span data-stu-id="729dd-266">**webapi**</span></span>

<span data-ttu-id="729dd-267">`-au|--auth <AUTHENTICATION_TYPE>`-Typ ověřování.</span><span class="sxs-lookup"><span data-stu-id="729dd-267">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="729dd-268">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="729dd-268">The possible values are:</span></span>

- <span data-ttu-id="729dd-269">`None`-Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="729dd-269">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="729dd-270">`IndividualB2C`-Jednotlivé ověřování s Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="729dd-270">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="729dd-271">`SingleOrg`-Organizační ověřování pro jednoho klienta.</span><span class="sxs-lookup"><span data-stu-id="729dd-271">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="729dd-272">`Windows`-Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="729dd-272">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="729dd-273">`--aad-b2c-instance <INSTANCE>`-Instance Azure Active Directory B2C se připojit k.</span><span class="sxs-lookup"><span data-stu-id="729dd-273">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="729dd-274">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="729dd-274">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="729dd-275">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="729dd-275">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="729dd-276">`-ssp|--susi-policy-id <ID>`– ID přihlášení a odhlášení zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="729dd-276">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="729dd-277">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="729dd-277">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="729dd-278">`--aad-instance <INSTANCE>`-Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="729dd-278">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="729dd-279">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="729dd-279">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="729dd-280">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="729dd-280">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="729dd-281">`--client-id <ID>`– ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="729dd-281">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="729dd-282">Použití s `IndividualB2C` nebo `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="729dd-282">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="729dd-283">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="729dd-283">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="729dd-284">`--domain <DOMAIN>`-Doména pro directory klienta.</span><span class="sxs-lookup"><span data-stu-id="729dd-284">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="729dd-285">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="729dd-285">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="729dd-286">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="729dd-286">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="729dd-287">`--tenant-id <ID>`-TenantId ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="729dd-287">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="729dd-288">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="729dd-288">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="729dd-289">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="729dd-289">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="729dd-290">`-r|--org-read-access`– Umožňuje této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="729dd-290">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="729dd-291">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="729dd-291">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="729dd-292">`--use-launch-settings`-Zahrnuje *launchSettings.json* ve výstupu vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="729dd-292">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="729dd-293">`-uld|--use-local-db`-Určuje, že místo SQLite by použít LocalDB.</span><span class="sxs-lookup"><span data-stu-id="729dd-293">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="729dd-294">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="729dd-294">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="729dd-295">`--no-restore`-Nepodporuje provedení implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="729dd-295">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="729dd-296">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="729dd-296">**mvc, razor**</span></span>

<span data-ttu-id="729dd-297">`-au|--auth <AUTHENTICATION_TYPE>`-Typ ověřování.</span><span class="sxs-lookup"><span data-stu-id="729dd-297">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="729dd-298">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="729dd-298">The possible values are:</span></span>

- <span data-ttu-id="729dd-299">`None`-Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="729dd-299">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="729dd-300">`Individual`-Jednotlivé ověřování.</span><span class="sxs-lookup"><span data-stu-id="729dd-300">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="729dd-301">`IndividualB2C`-Jednotlivé ověřování s Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="729dd-301">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="729dd-302">`SingleOrg`-Organizační ověřování pro jednoho klienta.</span><span class="sxs-lookup"><span data-stu-id="729dd-302">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="729dd-303">`MultiOrg`-Organizační ověřování pro víc klientů.</span><span class="sxs-lookup"><span data-stu-id="729dd-303">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="729dd-304">`Windows`-Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="729dd-304">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="729dd-305">`--aad-b2c-instance <INSTANCE>`-Instance Azure Active Directory B2C se připojit k.</span><span class="sxs-lookup"><span data-stu-id="729dd-305">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="729dd-306">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="729dd-306">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="729dd-307">Výchozí hodnota je `https://login.microsoftonline.com/tfp/` .</span><span class="sxs-lookup"><span data-stu-id="729dd-307">The default value is `https://login.microsoftonline.com/tfp/` .</span></span>

<span data-ttu-id="729dd-308">`-ssp|--susi-policy-id <ID>`– ID přihlášení a odhlášení zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="729dd-308">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="729dd-309">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="729dd-309">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="729dd-310">`-rp|--reset-password-policy-id <ID>`-Resetování hesla ID zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="729dd-310">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="729dd-311">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="729dd-311">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="729dd-312">`-ep|--edit-profile-policy-id <ID>`-Upravit profil ID zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="729dd-312">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="729dd-313">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="729dd-313">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="729dd-314">`--aad-instance <INSTANCE>`-Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="729dd-314">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="729dd-315">Použití s `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="729dd-315">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="729dd-316">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="729dd-316">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="729dd-317">`--client-id <ID>`– ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="729dd-317">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="729dd-318">Použití s `IndividualB2C`, `SingleOrg`, nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="729dd-318">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="729dd-319">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="729dd-319">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="729dd-320">`--domain <DOMAIN>`-Doména pro directory klienta.</span><span class="sxs-lookup"><span data-stu-id="729dd-320">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="729dd-321">Použití s `SingleOrg` nebo `IndividualB2C` ověřování...</span><span class="sxs-lookup"><span data-stu-id="729dd-321">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="729dd-322">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="729dd-322">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="729dd-323">`--tenant-id <ID>`-TenantId ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="729dd-323">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="729dd-324">Použití s `SingleOrg` ověřování...</span><span class="sxs-lookup"><span data-stu-id="729dd-324">Use with `SingleOrg` authentication..</span></span> <span data-ttu-id="729dd-325">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="729dd-325">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="729dd-326">`--callback-path <PATH>`– Cesta žádosti v rámci základní cesty aplikace identifikátor URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="729dd-326">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="729dd-327">Použití s `SingleOrg` nebo `IndividualB2C` ověřování...</span><span class="sxs-lookup"><span data-stu-id="729dd-327">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="729dd-328">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="729dd-328">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="729dd-329">`-r|--org-read-access`– Umožňuje této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="729dd-329">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="729dd-330">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="729dd-330">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="729dd-331">`--use-launch-settings`-Zahrnuje *launchSettings.json* ve výstupu vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="729dd-331">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="729dd-332">`--use-browserlink`-Zahrnuje BrowserLink v projektu.</span><span class="sxs-lookup"><span data-stu-id="729dd-332">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="729dd-333">`-uld|--use-local-db`-Určuje, že místo SQLite by použít LocalDB.</span><span class="sxs-lookup"><span data-stu-id="729dd-333">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="729dd-334">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="729dd-334">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="729dd-335">`--no-restore`-Nepodporuje provedení implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="729dd-335">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="729dd-336">**stránka**</span><span class="sxs-lookup"><span data-stu-id="729dd-336">**page**</span></span>

<span data-ttu-id="729dd-337">`-na|--namespace <NAMESPACE_NAME>`-Namespace pro generovaný kód.</span><span class="sxs-lookup"><span data-stu-id="729dd-337">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="729dd-338">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="729dd-338">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="729dd-339">`-np|--no-pagemodel`-Vytvoří danou stránku bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="729dd-339">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="729dd-340">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="729dd-340">**viewimports**</span></span>

<span data-ttu-id="729dd-341">`-na|--namespace <NAMESPACE_NAME>`-Namespace pro generovaný kód.</span><span class="sxs-lookup"><span data-stu-id="729dd-341">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="729dd-342">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="729dd-342">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="729dd-343">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="729dd-343">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="729dd-344">**konzola, xunit, mstestu, web, webapi**</span><span class="sxs-lookup"><span data-stu-id="729dd-344">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="729dd-345">`-f|--framework`-Určuje [framework](../../standard/frameworks.md) k cíli.</span><span class="sxs-lookup"><span data-stu-id="729dd-345">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="729dd-346">Hodnoty: `netcoreapp1.0` nebo `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="729dd-346">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="729dd-347">Výchozí hodnota je `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="729dd-347">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="729dd-348">**classlib**</span><span class="sxs-lookup"><span data-stu-id="729dd-348">**classlib**</span></span>

<span data-ttu-id="729dd-349">`-f|--framework`-Určuje [framework](../../standard/frameworks.md) k cíli.</span><span class="sxs-lookup"><span data-stu-id="729dd-349">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="729dd-350">Hodnoty: `netcoreapp1.0`, `netcoreapp1.1`, nebo `netstandard1.0` k `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="729dd-350">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="729dd-351">Výchozí hodnota je `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="729dd-351">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="729dd-352">**MVC**</span><span class="sxs-lookup"><span data-stu-id="729dd-352">**mvc**</span></span>

<span data-ttu-id="729dd-353">`-f|--framework`-Určuje [framework](../../standard/frameworks.md) k cíli.</span><span class="sxs-lookup"><span data-stu-id="729dd-353">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="729dd-354">Hodnoty: `netcoreapp1.0` nebo `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="729dd-354">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="729dd-355">Výchozí hodnota je `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="729dd-355">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="729dd-356">`-au|--auth`-Typ ověřování.</span><span class="sxs-lookup"><span data-stu-id="729dd-356">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="729dd-357">Hodnoty: `None` nebo `Individual`.</span><span class="sxs-lookup"><span data-stu-id="729dd-357">Values: `None` or `Individual`.</span></span> <span data-ttu-id="729dd-358">Výchozí hodnota je `None`.</span><span class="sxs-lookup"><span data-stu-id="729dd-358">The default value is `None`.</span></span>

<span data-ttu-id="729dd-359">`-uld|--use-local-db`-Určuje, zda pro použití LocalDB místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="729dd-359">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="729dd-360">Hodnoty: `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="729dd-360">Values: `true` or `false`.</span></span> <span data-ttu-id="729dd-361">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="729dd-361">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="729dd-362">Příklady</span><span class="sxs-lookup"><span data-stu-id="729dd-362">Examples</span></span>

<span data-ttu-id="729dd-363">Vytvoření projektu aplikace konzoly F # v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="729dd-363">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang f#`

<span data-ttu-id="729dd-364">Vytvořte standardní rozhraní .NET projektu knihovny tříd v zadaný adresář (dostupné pouze s .NET Core 2.0 SDK nebo novější verze):</span><span class="sxs-lookup"><span data-stu-id="729dd-364">Create a .NET Standard class library project in the specified directory (available only with .NET Core 2.0 SDK or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="729dd-365">Vytvořte nový projekt aplikace ASP.NET Core C# MVC v aktuálním adresáři bez jakéhokoli ověřování cílení na rozhraní .NET 2.0 jádra:</span><span class="sxs-lookup"><span data-stu-id="729dd-365">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication targeting .NET Core 2.0:</span></span>

`dotnet new mvc -au None -f netcoreapp2.0`

<span data-ttu-id="729dd-366">Vytvoření nové aplikace xUnit cílení na rozhraní .NET 2.0 jádra:</span><span class="sxs-lookup"><span data-stu-id="729dd-366">Create a new xUnit application targeting .NET Core 2.0:</span></span>

`dotnet new xunit --framework netcoreapp2.0`

<span data-ttu-id="729dd-367">Seznam všech šablon, které jsou k dispozici pro MVC:</span><span class="sxs-lookup"><span data-stu-id="729dd-367">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

## <a name="see-also"></a><span data-ttu-id="729dd-368">Viz také</span><span class="sxs-lookup"><span data-stu-id="729dd-368">See also</span></span>

[<span data-ttu-id="729dd-369">Vlastní šablony pro nové dotnet.</span><span class="sxs-lookup"><span data-stu-id="729dd-369">Custom templates for dotnet new</span></span>](custom-templates.md)  
[<span data-ttu-id="729dd-370">Vytvoření vlastní šablony pro dotnet new</span><span class="sxs-lookup"><span data-stu-id="729dd-370">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
[<span data-ttu-id="729dd-371">úložiště GitHub DotNet/dotnet šablony – ukázky</span><span class="sxs-lookup"><span data-stu-id="729dd-371">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
[<span data-ttu-id="729dd-372">Dostupné šablony pro nové dotnet.</span><span class="sxs-lookup"><span data-stu-id="729dd-372">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
