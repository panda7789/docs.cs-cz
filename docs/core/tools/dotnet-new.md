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
ms.openlocfilehash: d64881380febee08414f57a36ed92079e8d69ed6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-new"></a><span data-ttu-id="36a47-104">nové DotNet.</span><span class="sxs-lookup"><span data-stu-id="36a47-104">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="36a47-105">Název</span><span class="sxs-lookup"><span data-stu-id="36a47-105">Name</span></span>

<span data-ttu-id="36a47-106">`dotnet new`-Vytvoří nový projekt, konfigurační soubor nebo řešení v závislosti na určené šablony.</span><span class="sxs-lookup"><span data-stu-id="36a47-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="36a47-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="36a47-107">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="36a47-108">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="36a47-108">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="36a47-109">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="36a47-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="36a47-110">Popis</span><span class="sxs-lookup"><span data-stu-id="36a47-110">Description</span></span>

<span data-ttu-id="36a47-111">`dotnet new` Příkaz nabízí pohodlný způsob, jak inicializovat platný projekt .NET Core.</span><span class="sxs-lookup"><span data-stu-id="36a47-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span> 

<span data-ttu-id="36a47-112">Příkaz volání [modulu šablon](https://github.com/dotnet/templating) vytvořit artefakty na disku na základě určené šablony a možnosti.</span><span class="sxs-lookup"><span data-stu-id="36a47-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="36a47-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="36a47-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="36a47-114">Šablona pro vytvoření instance při vyvolání příkazu.</span><span class="sxs-lookup"><span data-stu-id="36a47-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="36a47-115">Každá šablona může mít specifické možnosti, které lze předat.</span><span class="sxs-lookup"><span data-stu-id="36a47-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="36a47-116">Další informace najdete v tématu [možnosti šablony](#template-options).</span><span class="sxs-lookup"><span data-stu-id="36a47-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="36a47-117">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="36a47-117">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="36a47-118">Příkaz obsahuje seznam výchozích šablon.</span><span class="sxs-lookup"><span data-stu-id="36a47-118">The command contains a default list of templates.</span></span> <span data-ttu-id="36a47-119">Použití `dotnet new -l` získat seznam dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="36a47-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="36a47-120">V následující tabulce jsou uvedeny šablony, které jsou předinstalované .NET Core 2.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="36a47-120">The following table shows the templates that come pre-installed with the .NET Core 2.0 SDK.</span></span> <span data-ttu-id="36a47-121">Výchozí jazyk pro šablonu se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="36a47-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="36a47-122">Popis šablony</span><span class="sxs-lookup"><span data-stu-id="36a47-122">Template description</span></span>                          | <span data-ttu-id="36a47-123">Název šablony</span><span class="sxs-lookup"><span data-stu-id="36a47-123">Template name</span></span>  | <span data-ttu-id="36a47-124">Jazyky</span><span class="sxs-lookup"><span data-stu-id="36a47-124">Languages</span></span>     |
|----------------------------------------------|----------------|---------------|
| <span data-ttu-id="36a47-125">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="36a47-125">Console application</span></span>                          | <span data-ttu-id="36a47-126">konzola</span><span class="sxs-lookup"><span data-stu-id="36a47-126">console</span></span>        | <span data-ttu-id="36a47-127">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="36a47-127">[C#], F#, VB</span></span>  |
| <span data-ttu-id="36a47-128">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="36a47-128">Class library</span></span>                                | <span data-ttu-id="36a47-129">classlib</span><span class="sxs-lookup"><span data-stu-id="36a47-129">classlib</span></span>       | <span data-ttu-id="36a47-130">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="36a47-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="36a47-131">Projektu testování částí</span><span class="sxs-lookup"><span data-stu-id="36a47-131">Unit test project</span></span>                            | <span data-ttu-id="36a47-132">mstestu</span><span class="sxs-lookup"><span data-stu-id="36a47-132">mstest</span></span>         | <span data-ttu-id="36a47-133">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="36a47-133">[C#], F#, VB</span></span>  |
| <span data-ttu-id="36a47-134">xUnit testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="36a47-134">xUnit test project</span></span>                           | <span data-ttu-id="36a47-135">xunit</span><span class="sxs-lookup"><span data-stu-id="36a47-135">xunit</span></span>          | <span data-ttu-id="36a47-136">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="36a47-136">[C#], F#, VB</span></span>  |
| <span data-ttu-id="36a47-137">ASP.NET Core prázdný</span><span class="sxs-lookup"><span data-stu-id="36a47-137">ASP.NET Core empty</span></span>                           | <span data-ttu-id="36a47-138">webové</span><span class="sxs-lookup"><span data-stu-id="36a47-138">web</span></span>            | <span data-ttu-id="36a47-139">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="36a47-139">[C#], F#</span></span>      |
| <span data-ttu-id="36a47-140">Webové aplikace ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="36a47-140">ASP.NET Core Web App (Model-View-Controller)</span></span> | <span data-ttu-id="36a47-141">MVC</span><span class="sxs-lookup"><span data-stu-id="36a47-141">mvc</span></span>            | <span data-ttu-id="36a47-142">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="36a47-142">[C#], F#</span></span>      |
| <span data-ttu-id="36a47-143">Webové aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="36a47-143">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="36a47-144">syntaxe Razor</span><span class="sxs-lookup"><span data-stu-id="36a47-144">razor</span></span>          | <span data-ttu-id="36a47-145">[C#]</span><span class="sxs-lookup"><span data-stu-id="36a47-145">[C#]</span></span>          |
| <span data-ttu-id="36a47-146">ASP.NET Core s úhlová</span><span class="sxs-lookup"><span data-stu-id="36a47-146">ASP.NET Core with Angular</span></span>                    | <span data-ttu-id="36a47-147">úhlová</span><span class="sxs-lookup"><span data-stu-id="36a47-147">angular</span></span>        | <span data-ttu-id="36a47-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="36a47-148">[C#]</span></span>          |
| <span data-ttu-id="36a47-149">ASP.NET Core s React.js</span><span class="sxs-lookup"><span data-stu-id="36a47-149">ASP.NET Core with React.js</span></span>                   | <span data-ttu-id="36a47-150">Reagovat</span><span class="sxs-lookup"><span data-stu-id="36a47-150">react</span></span>          | <span data-ttu-id="36a47-151">[C#]</span><span class="sxs-lookup"><span data-stu-id="36a47-151">[C#]</span></span>          |
| <span data-ttu-id="36a47-152">ASP.NET Core s React.js a – obnovení</span><span class="sxs-lookup"><span data-stu-id="36a47-152">ASP.NET Core with React.js and Redux</span></span>         | <span data-ttu-id="36a47-153">reactredux</span><span class="sxs-lookup"><span data-stu-id="36a47-153">reactredux</span></span>     | <span data-ttu-id="36a47-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="36a47-154">[C#]</span></span>          |
| <span data-ttu-id="36a47-155">Jádro ASP.NET Web API</span><span class="sxs-lookup"><span data-stu-id="36a47-155">ASP.NET Core Web API</span></span>                         | <span data-ttu-id="36a47-156">webapi</span><span class="sxs-lookup"><span data-stu-id="36a47-156">webapi</span></span>         | <span data-ttu-id="36a47-157">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="36a47-157">[C#], F#</span></span>      |
| <span data-ttu-id="36a47-158">soubor Global.JSON</span><span class="sxs-lookup"><span data-stu-id="36a47-158">global.json file</span></span>                             | <span data-ttu-id="36a47-159">globaljson</span><span class="sxs-lookup"><span data-stu-id="36a47-159">globaljson</span></span>     |               |
| <span data-ttu-id="36a47-160">Konfigurace Nuget</span><span class="sxs-lookup"><span data-stu-id="36a47-160">Nuget config</span></span>                                 | <span data-ttu-id="36a47-161">nugetconfig</span><span class="sxs-lookup"><span data-stu-id="36a47-161">nugetconfig</span></span>    |               |
| <span data-ttu-id="36a47-162">Webové konfigurace</span><span class="sxs-lookup"><span data-stu-id="36a47-162">Web config</span></span>                                   | <span data-ttu-id="36a47-163">WebConfig</span><span class="sxs-lookup"><span data-stu-id="36a47-163">webconfig</span></span>      |               |
| <span data-ttu-id="36a47-164">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="36a47-164">Solution file</span></span>                                | <span data-ttu-id="36a47-165">SLN –</span><span class="sxs-lookup"><span data-stu-id="36a47-165">sln</span></span>            |               |
| <span data-ttu-id="36a47-166">Stránky Razor</span><span class="sxs-lookup"><span data-stu-id="36a47-166">Razor page</span></span>                                   | <span data-ttu-id="36a47-167">stránka</span><span class="sxs-lookup"><span data-stu-id="36a47-167">page</span></span>           |               |
| <span data-ttu-id="36a47-168">MVC nebo ViewImports</span><span class="sxs-lookup"><span data-stu-id="36a47-168">MVC/ViewImports</span></span>                              | <span data-ttu-id="36a47-169">viewimports</span><span class="sxs-lookup"><span data-stu-id="36a47-169">viewimports</span></span>    |               |
| <span data-ttu-id="36a47-170">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="36a47-170">MVC ViewStart</span></span>                                | <span data-ttu-id="36a47-171">viewstart</span><span class="sxs-lookup"><span data-stu-id="36a47-171">viewstart</span></span>      |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="36a47-172">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="36a47-172">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="36a47-173">Příkaz obsahuje seznam výchozích šablon.</span><span class="sxs-lookup"><span data-stu-id="36a47-173">The command contains a default list of templates.</span></span> <span data-ttu-id="36a47-174">Použití `dotnet new -all` získat seznam dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="36a47-174">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="36a47-175">V následující tabulce jsou uvedeny šablony, které jsou předinstalované .NET Core 1.x SDK.</span><span class="sxs-lookup"><span data-stu-id="36a47-175">The following table shows the templates that come pre-installed with the .NET Core 1.x SDK.</span></span> <span data-ttu-id="36a47-176">Výchozí jazyk pro šablonu se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="36a47-176">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="36a47-177">Popis šablony</span><span class="sxs-lookup"><span data-stu-id="36a47-177">Template description</span></span>  | <span data-ttu-id="36a47-178">Název šablony</span><span class="sxs-lookup"><span data-stu-id="36a47-178">Template name</span></span>  | <span data-ttu-id="36a47-179">Jazyky</span><span class="sxs-lookup"><span data-stu-id="36a47-179">Languages</span></span> |
|----------------------|----------------|-----------|
| <span data-ttu-id="36a47-180">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="36a47-180">Console application</span></span>  | <span data-ttu-id="36a47-181">konzola</span><span class="sxs-lookup"><span data-stu-id="36a47-181">console</span></span>        | <span data-ttu-id="36a47-182">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="36a47-182">[C#], F#</span></span>  |
| <span data-ttu-id="36a47-183">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="36a47-183">Class library</span></span>        | <span data-ttu-id="36a47-184">classlib</span><span class="sxs-lookup"><span data-stu-id="36a47-184">classlib</span></span>       | <span data-ttu-id="36a47-185">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="36a47-185">[C#], F#</span></span>  |
| <span data-ttu-id="36a47-186">Projektu testování částí</span><span class="sxs-lookup"><span data-stu-id="36a47-186">Unit test project</span></span>    | <span data-ttu-id="36a47-187">mstestu</span><span class="sxs-lookup"><span data-stu-id="36a47-187">mstest</span></span>         | <span data-ttu-id="36a47-188">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="36a47-188">[C#], F#</span></span>  |
| <span data-ttu-id="36a47-189">xUnit testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="36a47-189">xUnit test project</span></span>   | <span data-ttu-id="36a47-190">xunit</span><span class="sxs-lookup"><span data-stu-id="36a47-190">xunit</span></span>          | <span data-ttu-id="36a47-191">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="36a47-191">[C#], F#</span></span>  |
| <span data-ttu-id="36a47-192">ASP.NET Core prázdný</span><span class="sxs-lookup"><span data-stu-id="36a47-192">ASP.NET Core empty</span></span>   | <span data-ttu-id="36a47-193">webové</span><span class="sxs-lookup"><span data-stu-id="36a47-193">web</span></span>            | <span data-ttu-id="36a47-194">[C#]</span><span class="sxs-lookup"><span data-stu-id="36a47-194">[C#]</span></span>      |
| <span data-ttu-id="36a47-195">Webové aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="36a47-195">ASP.NET Core Web App</span></span> | <span data-ttu-id="36a47-196">MVC</span><span class="sxs-lookup"><span data-stu-id="36a47-196">mvc</span></span>            | <span data-ttu-id="36a47-197">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="36a47-197">[C#], F#</span></span>  |
| <span data-ttu-id="36a47-198">Jádro ASP.NET Web API</span><span class="sxs-lookup"><span data-stu-id="36a47-198">ASP.NET Core Web API</span></span> | <span data-ttu-id="36a47-199">webapi</span><span class="sxs-lookup"><span data-stu-id="36a47-199">webapi</span></span>         | <span data-ttu-id="36a47-200">[C#]</span><span class="sxs-lookup"><span data-stu-id="36a47-200">[C#]</span></span>      |
| <span data-ttu-id="36a47-201">Konfigurace Nuget</span><span class="sxs-lookup"><span data-stu-id="36a47-201">Nuget config</span></span>         | <span data-ttu-id="36a47-202">nugetconfig</span><span class="sxs-lookup"><span data-stu-id="36a47-202">nugetconfig</span></span>    |           |
| <span data-ttu-id="36a47-203">Webové konfigurace</span><span class="sxs-lookup"><span data-stu-id="36a47-203">Web config</span></span>           | <span data-ttu-id="36a47-204">WebConfig</span><span class="sxs-lookup"><span data-stu-id="36a47-204">webconfig</span></span>      |           |
| <span data-ttu-id="36a47-205">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="36a47-205">Solution file</span></span>        | <span data-ttu-id="36a47-206">SLN –</span><span class="sxs-lookup"><span data-stu-id="36a47-206">sln</span></span>            |           |

---

## <a name="options"></a><span data-ttu-id="36a47-207">Možnosti</span><span class="sxs-lookup"><span data-stu-id="36a47-207">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="36a47-208">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="36a47-208">.NET Core 2.x</span></span>](#tab/netcore2x)

`--force`

<span data-ttu-id="36a47-209">Vynutí obsah má být vygenerován i v případě, že se změní stávající soubory.</span><span class="sxs-lookup"><span data-stu-id="36a47-209">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="36a47-210">To je potřeba, když výstupnímu adresáři již obsahuje projektu.</span><span class="sxs-lookup"><span data-stu-id="36a47-210">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="36a47-211">Vytiskne nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="36a47-211">Prints out help for the command.</span></span> <span data-ttu-id="36a47-212">Nelze vyvolat pro `dotnet new` příkaz sám sebe nebo pro všechny šablony, jako například `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="36a47-212">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="36a47-213">Nainstaluje sadu zdroje nebo šablony z `PATH` nebo `NUGET_ID` zadat.</span><span class="sxs-lookup"><span data-stu-id="36a47-213">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="36a47-214">Informace o vytváření vlastních šablon najdete v tématu [vlastních šablon pro dotnet nové](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="36a47-214">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="36a47-215">Obsahuje seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="36a47-215">Lists templates containing the specified name.</span></span> <span data-ttu-id="36a47-216">Pokud je vyvolána pro `dotnet new` příkaz, zobrazí seznam možných šablony, které jsou k dispozici pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="36a47-216">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="36a47-217">Například pokud adresář již obsahuje projekt, nepodporuje zobrazí seznam všech šablon projektu.</span><span class="sxs-lookup"><span data-stu-id="36a47-217">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="36a47-218">Jazyk šablonu, kterou chcete vytvořit.</span><span class="sxs-lookup"><span data-stu-id="36a47-218">The language of the template to create.</span></span> <span data-ttu-id="36a47-219">Jazyk přijata, se liší podle šablony (viz výchozí hodnoty v [argumenty](#arguments) části).</span><span class="sxs-lookup"><span data-stu-id="36a47-219">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="36a47-220">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="36a47-220">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="36a47-221">Název pro vytvoření výstupu.</span><span class="sxs-lookup"><span data-stu-id="36a47-221">The name for the created output.</span></span> <span data-ttu-id="36a47-222">Pokud není zadán žádný název, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="36a47-222">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="36a47-223">Umístění pro generovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="36a47-223">Location to place the generated output.</span></span> <span data-ttu-id="36a47-224">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="36a47-224">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="36a47-225">Filtry šablony vycházející z dostupných typů.</span><span class="sxs-lookup"><span data-stu-id="36a47-225">Filters templates based on available types.</span></span> <span data-ttu-id="36a47-226">Předdefinované hodnoty jsou "projektu", "položka" nebo "ostatní".</span><span class="sxs-lookup"><span data-stu-id="36a47-226">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="36a47-227">Odinstaluje sadu zdroje nebo šablony v `PATH` nebo `NUGET_ID` zadat.</span><span class="sxs-lookup"><span data-stu-id="36a47-227">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="36a47-228">Chcete-li odinstalovat šablony pomocí `PATH`, budete muset plně kvalifikovanou cestu.</span><span class="sxs-lookup"><span data-stu-id="36a47-228">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="36a47-229">Například *C: či uživatelů nebo\<uživatele > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z obsahující složka se není.</span><span class="sxs-lookup"><span data-stu-id="36a47-229">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="36a47-230">Kromě toho nezahrnují konečné ukončující lomítko adresáře na cestu k šabloně.</span><span class="sxs-lookup"><span data-stu-id="36a47-230">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="36a47-231">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="36a47-231">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="36a47-232">Při spuštění v kontextu jsou uvedeny všechny šablony pro konkrétní typ projektu `dotnet new` příkaz samostatně.</span><span class="sxs-lookup"><span data-stu-id="36a47-232">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="36a47-233">Při spuštění v rámci konkrétní šablonu, jako například `dotnet new web -all`, `-all` interpretována jako vytvoření příznak force.</span><span class="sxs-lookup"><span data-stu-id="36a47-233">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="36a47-234">To je potřeba, když výstupnímu adresáři již obsahuje projektu.</span><span class="sxs-lookup"><span data-stu-id="36a47-234">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="36a47-235">Vytiskne nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="36a47-235">Prints out help for the command.</span></span> <span data-ttu-id="36a47-236">Nelze vyvolat pro `dotnet new` příkaz sám sebe nebo pro všechny šablony, jako například `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="36a47-236">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="36a47-237">Obsahuje seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="36a47-237">Lists templates containing the specified name.</span></span> <span data-ttu-id="36a47-238">Pokud je vyvolána pro `dotnet new` příkaz, zobrazí seznam možných šablony, které jsou k dispozici pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="36a47-238">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="36a47-239">Například pokud adresář již obsahuje projekt, nepodporuje zobrazí seznam všech šablon projektu.</span><span class="sxs-lookup"><span data-stu-id="36a47-239">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="36a47-240">Jazyk šablonu, kterou chcete vytvořit.</span><span class="sxs-lookup"><span data-stu-id="36a47-240">The language of the template to create.</span></span> <span data-ttu-id="36a47-241">Jazyk přijata, se liší podle šablony (viz výchozí hodnoty v [argumenty](#arguments) části).</span><span class="sxs-lookup"><span data-stu-id="36a47-241">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="36a47-242">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="36a47-242">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="36a47-243">Název pro vytvoření výstupu.</span><span class="sxs-lookup"><span data-stu-id="36a47-243">The name for the created output.</span></span> <span data-ttu-id="36a47-244">Pokud není zadán žádný název, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="36a47-244">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="36a47-245">Umístění pro generovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="36a47-245">Location to place the generated output.</span></span> <span data-ttu-id="36a47-246">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="36a47-246">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="36a47-247">Možnosti šablony</span><span class="sxs-lookup"><span data-stu-id="36a47-247">Template options</span></span>

<span data-ttu-id="36a47-248">Každá šablona projektu může mít další možnosti, které jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="36a47-248">Each project template may have additional options available.</span></span> <span data-ttu-id="36a47-249">Základní šablony mají následující možnosti:</span><span class="sxs-lookup"><span data-stu-id="36a47-249">The core templates have the following additional options:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="36a47-250">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="36a47-250">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="36a47-251">**konzole úhlová, reagovat, reactredux**</span><span class="sxs-lookup"><span data-stu-id="36a47-251">**console, angular, react, reactredux**</span></span>

<span data-ttu-id="36a47-252">`--no-restore`-Nepodporuje provedení implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="36a47-252">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="36a47-253">**classlib**</span><span class="sxs-lookup"><span data-stu-id="36a47-253">**classlib**</span></span>

<span data-ttu-id="36a47-254">`-f|--framework <FRAMEWORK>`-Určuje [framework](../../standard/frameworks.md) k cíli.</span><span class="sxs-lookup"><span data-stu-id="36a47-254">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="36a47-255">Hodnoty: `netcoreapp2.0` pro vytvoření základní knihovny tříd rozhraní .NET nebo `netstandard2.0` vytvořit standardní knihovny tříd rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="36a47-255">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="36a47-256">Výchozí hodnota je `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="36a47-256">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="36a47-257">`--no-restore`-Nepodporuje provedení implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="36a47-257">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="36a47-258">**mstestu xunit**</span><span class="sxs-lookup"><span data-stu-id="36a47-258">**mstest, xunit**</span></span>

<span data-ttu-id="36a47-259">`-p|--enable-pack`– Umožňuje vytváření balíčků pro projekt pomocí [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="36a47-259">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="36a47-260">`--no-restore`-Nepodporuje provedení implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="36a47-260">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="36a47-261">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="36a47-261">**globaljson**</span></span>

<span data-ttu-id="36a47-262">`--sdk-version <VERSION_NUMBER>`-Určuje verzi rozhraní .NET Core SDK pro použití v *global.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="36a47-262">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="36a47-263">**webové**</span><span class="sxs-lookup"><span data-stu-id="36a47-263">**web**</span></span>

<span data-ttu-id="36a47-264">`--use-launch-settings`-Zahrnuje *launchSettings.json* ve výstupu vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="36a47-264">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="36a47-265">`--no-restore`-Nepodporuje provedení implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="36a47-265">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="36a47-266">**webapi**</span><span class="sxs-lookup"><span data-stu-id="36a47-266">**webapi**</span></span>

<span data-ttu-id="36a47-267">`-au|--auth <AUTHENTICATION_TYPE>`-Typ ověřování.</span><span class="sxs-lookup"><span data-stu-id="36a47-267">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="36a47-268">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="36a47-268">The possible values are:</span></span>

- <span data-ttu-id="36a47-269">`None`-Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="36a47-269">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="36a47-270">`IndividualB2C`-Jednotlivé ověřování s Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="36a47-270">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="36a47-271">`SingleOrg`-Organizační ověřování pro jednoho klienta.</span><span class="sxs-lookup"><span data-stu-id="36a47-271">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="36a47-272">`Windows`-Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="36a47-272">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="36a47-273">`--aad-b2c-instance <INSTANCE>`-Instance Azure Active Directory B2C se připojit k.</span><span class="sxs-lookup"><span data-stu-id="36a47-273">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="36a47-274">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="36a47-274">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="36a47-275">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="36a47-275">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="36a47-276">`-ssp|--susi-policy-id <ID>`– ID přihlášení a odhlášení zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="36a47-276">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="36a47-277">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="36a47-277">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="36a47-278">`--aad-instance <INSTANCE>`-Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="36a47-278">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="36a47-279">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="36a47-279">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="36a47-280">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="36a47-280">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="36a47-281">`--client-id <ID>`– ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="36a47-281">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="36a47-282">Použití s `IndividualB2C` nebo `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="36a47-282">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="36a47-283">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="36a47-283">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="36a47-284">`--domain <DOMAIN>`-Doména pro directory klienta.</span><span class="sxs-lookup"><span data-stu-id="36a47-284">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="36a47-285">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="36a47-285">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="36a47-286">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="36a47-286">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="36a47-287">`--tenant-id <ID>`-TenantId ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="36a47-287">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="36a47-288">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="36a47-288">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="36a47-289">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="36a47-289">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="36a47-290">`-r|--org-read-access`– Umožňuje této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="36a47-290">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="36a47-291">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="36a47-291">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="36a47-292">`--use-launch-settings`-Zahrnuje *launchSettings.json* ve výstupu vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="36a47-292">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="36a47-293">`-uld|--use-local-db`-Určuje, že místo SQLite by použít LocalDB.</span><span class="sxs-lookup"><span data-stu-id="36a47-293">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="36a47-294">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="36a47-294">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="36a47-295">`--no-restore`-Nepodporuje provedení implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="36a47-295">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="36a47-296">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="36a47-296">**mvc, razor**</span></span>

<span data-ttu-id="36a47-297">`-au|--auth <AUTHENTICATION_TYPE>`-Typ ověřování.</span><span class="sxs-lookup"><span data-stu-id="36a47-297">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="36a47-298">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="36a47-298">The possible values are:</span></span>

- <span data-ttu-id="36a47-299">`None`-Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="36a47-299">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="36a47-300">`Individual`-Jednotlivé ověřování.</span><span class="sxs-lookup"><span data-stu-id="36a47-300">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="36a47-301">`IndividualB2C`-Jednotlivé ověřování s Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="36a47-301">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="36a47-302">`SingleOrg`-Organizační ověřování pro jednoho klienta.</span><span class="sxs-lookup"><span data-stu-id="36a47-302">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="36a47-303">`MultiOrg`-Organizační ověřování pro víc klientů.</span><span class="sxs-lookup"><span data-stu-id="36a47-303">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="36a47-304">`Windows`-Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="36a47-304">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="36a47-305">`--aad-b2c-instance <INSTANCE>`-Instance Azure Active Directory B2C se připojit k.</span><span class="sxs-lookup"><span data-stu-id="36a47-305">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="36a47-306">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="36a47-306">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="36a47-307">Výchozí hodnota je `https://login.microsoftonline.com/tfp/` .</span><span class="sxs-lookup"><span data-stu-id="36a47-307">The default value is `https://login.microsoftonline.com/tfp/` .</span></span>

<span data-ttu-id="36a47-308">`-ssp|--susi-policy-id <ID>`– ID přihlášení a odhlášení zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="36a47-308">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="36a47-309">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="36a47-309">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="36a47-310">`-rp|--reset-password-policy-id <ID>`-Resetování hesla ID zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="36a47-310">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="36a47-311">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="36a47-311">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="36a47-312">`-ep|--edit-profile-policy-id <ID>`-Upravit profil ID zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="36a47-312">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="36a47-313">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="36a47-313">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="36a47-314">`--aad-instance <INSTANCE>`-Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="36a47-314">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="36a47-315">Použití s `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="36a47-315">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="36a47-316">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="36a47-316">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="36a47-317">`--client-id <ID>`– ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="36a47-317">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="36a47-318">Použití s `IndividualB2C`, `SingleOrg`, nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="36a47-318">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="36a47-319">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="36a47-319">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="36a47-320">`--domain <DOMAIN>`-Doména pro directory klienta.</span><span class="sxs-lookup"><span data-stu-id="36a47-320">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="36a47-321">Použití s `SingleOrg` nebo `IndividualB2C` ověřování...</span><span class="sxs-lookup"><span data-stu-id="36a47-321">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="36a47-322">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="36a47-322">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="36a47-323">`--tenant-id <ID>`-TenantId ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="36a47-323">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="36a47-324">Použití s `SingleOrg` ověřování...</span><span class="sxs-lookup"><span data-stu-id="36a47-324">Use with `SingleOrg` authentication..</span></span> <span data-ttu-id="36a47-325">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="36a47-325">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="36a47-326">`--callback-path <PATH>`– Cesta žádosti v rámci základní cesty aplikace identifikátor URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="36a47-326">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="36a47-327">Použití s `SingleOrg` nebo `IndividualB2C` ověřování...</span><span class="sxs-lookup"><span data-stu-id="36a47-327">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="36a47-328">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="36a47-328">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="36a47-329">`-r|--org-read-access`– Umožňuje této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="36a47-329">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="36a47-330">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="36a47-330">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="36a47-331">`--use-launch-settings`-Zahrnuje *launchSettings.json* ve výstupu vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="36a47-331">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="36a47-332">`--use-browserlink`-Zahrnuje BrowserLink v projektu.</span><span class="sxs-lookup"><span data-stu-id="36a47-332">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="36a47-333">`-uld|--use-local-db`-Určuje, že místo SQLite by použít LocalDB.</span><span class="sxs-lookup"><span data-stu-id="36a47-333">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="36a47-334">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="36a47-334">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="36a47-335">`--no-restore`-Nepodporuje provedení implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="36a47-335">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="36a47-336">**stránka**</span><span class="sxs-lookup"><span data-stu-id="36a47-336">**page**</span></span>

<span data-ttu-id="36a47-337">`-na|--namespace <NAMESPACE_NAME>`-Namespace pro generovaný kód.</span><span class="sxs-lookup"><span data-stu-id="36a47-337">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="36a47-338">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="36a47-338">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="36a47-339">`-np|--no-pagemodel`-Vytvoří danou stránku bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="36a47-339">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="36a47-340">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="36a47-340">**viewimports**</span></span>

<span data-ttu-id="36a47-341">`-na|--namespace <NAMESPACE_NAME>`-Namespace pro generovaný kód.</span><span class="sxs-lookup"><span data-stu-id="36a47-341">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="36a47-342">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="36a47-342">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="36a47-343">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="36a47-343">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="36a47-344">**konzola, xunit, mstestu, web, webapi**</span><span class="sxs-lookup"><span data-stu-id="36a47-344">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="36a47-345">`-f|--framework`-Určuje [framework](../../standard/frameworks.md) k cíli.</span><span class="sxs-lookup"><span data-stu-id="36a47-345">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="36a47-346">Hodnoty: `netcoreapp1.0` nebo `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="36a47-346">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="36a47-347">Výchozí hodnota je `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="36a47-347">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="36a47-348">**classlib**</span><span class="sxs-lookup"><span data-stu-id="36a47-348">**classlib**</span></span>

<span data-ttu-id="36a47-349">`-f|--framework`-Určuje [framework](../../standard/frameworks.md) k cíli.</span><span class="sxs-lookup"><span data-stu-id="36a47-349">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="36a47-350">Hodnoty: `netcoreapp1.0`, `netcoreapp1.1`, nebo `netstandard1.0` k `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="36a47-350">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="36a47-351">Výchozí hodnota je `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="36a47-351">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="36a47-352">**MVC**</span><span class="sxs-lookup"><span data-stu-id="36a47-352">**mvc**</span></span>

<span data-ttu-id="36a47-353">`-f|--framework`-Určuje [framework](../../standard/frameworks.md) k cíli.</span><span class="sxs-lookup"><span data-stu-id="36a47-353">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="36a47-354">Hodnoty: `netcoreapp1.0` nebo `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="36a47-354">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="36a47-355">Výchozí hodnota je `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="36a47-355">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="36a47-356">`-au|--auth`-Typ ověřování.</span><span class="sxs-lookup"><span data-stu-id="36a47-356">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="36a47-357">Hodnoty: `None` nebo `Individual`.</span><span class="sxs-lookup"><span data-stu-id="36a47-357">Values: `None` or `Individual`.</span></span> <span data-ttu-id="36a47-358">Výchozí hodnota je `None`.</span><span class="sxs-lookup"><span data-stu-id="36a47-358">The default value is `None`.</span></span>

<span data-ttu-id="36a47-359">`-uld|--use-local-db`-Určuje, zda pro použití LocalDB místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="36a47-359">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="36a47-360">Hodnoty: `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="36a47-360">Values: `true` or `false`.</span></span> <span data-ttu-id="36a47-361">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="36a47-361">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="36a47-362">Příklady</span><span class="sxs-lookup"><span data-stu-id="36a47-362">Examples</span></span>

<span data-ttu-id="36a47-363">Vytvoření projektu aplikace konzoly F # v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="36a47-363">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang f#`

<span data-ttu-id="36a47-364">Vytvořte standardní rozhraní .NET projektu knihovny tříd v zadaný adresář (dostupné pouze s .NET Core 2.0 SDK nebo novější verze):</span><span class="sxs-lookup"><span data-stu-id="36a47-364">Create a .NET Standard class library project in the specified directory (available only with .NET Core 2.0 SDK or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="36a47-365">Vytvořte nový projekt aplikace ASP.NET Core C# MVC v aktuálním adresáři bez jakéhokoli ověřování cílení na rozhraní .NET 2.0 jádra:</span><span class="sxs-lookup"><span data-stu-id="36a47-365">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication targeting .NET Core 2.0:</span></span>

`dotnet new mvc -au None -f netcoreapp2.0`

<span data-ttu-id="36a47-366">Vytvoření nové aplikace xUnit cílení na rozhraní .NET 2.0 jádra:</span><span class="sxs-lookup"><span data-stu-id="36a47-366">Create a new xUnit application targeting .NET Core 2.0:</span></span>

`dotnet new xunit --framework netcoreapp2.0`

<span data-ttu-id="36a47-367">Seznam všech šablon, které jsou k dispozici pro MVC:</span><span class="sxs-lookup"><span data-stu-id="36a47-367">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

## <a name="see-also"></a><span data-ttu-id="36a47-368">Viz také</span><span class="sxs-lookup"><span data-stu-id="36a47-368">See also</span></span>

[<span data-ttu-id="36a47-369">Vlastní šablony pro nové dotnet.</span><span class="sxs-lookup"><span data-stu-id="36a47-369">Custom templates for dotnet new</span></span>](custom-templates.md)  
[<span data-ttu-id="36a47-370">Vytvoření nové vlastní šablony pro dotnet.</span><span class="sxs-lookup"><span data-stu-id="36a47-370">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
[<span data-ttu-id="36a47-371">úložiště GitHub DotNet/dotnet šablony – ukázky</span><span class="sxs-lookup"><span data-stu-id="36a47-371">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
[<span data-ttu-id="36a47-372">Dostupné šablony pro nové dotnet.</span><span class="sxs-lookup"><span data-stu-id="36a47-372">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
