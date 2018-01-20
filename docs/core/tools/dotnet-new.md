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
ms.openlocfilehash: cf65dc80f135badcb1580726a12a9ae9d94ae3d7
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/20/2018
---
# <a name="dotnet-new"></a><span data-ttu-id="2798f-104">nové DotNet.</span><span class="sxs-lookup"><span data-stu-id="2798f-104">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="2798f-105">Název</span><span class="sxs-lookup"><span data-stu-id="2798f-105">Name</span></span>

<span data-ttu-id="2798f-106">`dotnet new`-Vytvoří nový projekt, konfigurační soubor nebo řešení v závislosti na určené šablony.</span><span class="sxs-lookup"><span data-stu-id="2798f-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2798f-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="2798f-107">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="2798f-108">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="2798f-108">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="2798f-109">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="2798f-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="2798f-110">Popis</span><span class="sxs-lookup"><span data-stu-id="2798f-110">Description</span></span>

<span data-ttu-id="2798f-111">`dotnet new` Příkaz nabízí pohodlný způsob, jak inicializovat platný projekt .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2798f-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span> 

<span data-ttu-id="2798f-112">Příkaz volání [modulu šablon](https://github.com/dotnet/templating) vytvořit artefakty na disku na základě určené šablony a možnosti.</span><span class="sxs-lookup"><span data-stu-id="2798f-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="2798f-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="2798f-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="2798f-114">Šablona pro vytvoření instance při vyvolání příkazu.</span><span class="sxs-lookup"><span data-stu-id="2798f-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="2798f-115">Každá šablona může mít specifické možnosti, které lze předat.</span><span class="sxs-lookup"><span data-stu-id="2798f-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="2798f-116">Další informace najdete v tématu [možnosti šablony](#template-options).</span><span class="sxs-lookup"><span data-stu-id="2798f-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="2798f-117">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="2798f-117">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="2798f-118">Příkaz obsahuje seznam výchozích šablon.</span><span class="sxs-lookup"><span data-stu-id="2798f-118">The command contains a default list of templates.</span></span> <span data-ttu-id="2798f-119">Použití `dotnet new -l` získat seznam dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="2798f-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="2798f-120">V následující tabulce jsou uvedeny šablony, které jsou předinstalované .NET Core 2.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="2798f-120">The following table shows the templates that come pre-installed with the .NET Core 2.0 SDK.</span></span> <span data-ttu-id="2798f-121">Výchozí jazyk pro šablonu se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="2798f-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="2798f-122">Popis šablony</span><span class="sxs-lookup"><span data-stu-id="2798f-122">Template description</span></span>                          | <span data-ttu-id="2798f-123">Název šablony</span><span class="sxs-lookup"><span data-stu-id="2798f-123">Template name</span></span> | <span data-ttu-id="2798f-124">Jazyky</span><span class="sxs-lookup"><span data-stu-id="2798f-124">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="2798f-125">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="2798f-125">Console application</span></span>                          | `console`     | <span data-ttu-id="2798f-126">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="2798f-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="2798f-127">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="2798f-127">Class library</span></span>                                | `classlib`    | <span data-ttu-id="2798f-128">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="2798f-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="2798f-129">Projektu testování částí</span><span class="sxs-lookup"><span data-stu-id="2798f-129">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="2798f-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="2798f-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="2798f-131">xUnit testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="2798f-131">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="2798f-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="2798f-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="2798f-133">ASP.NET Core prázdný</span><span class="sxs-lookup"><span data-stu-id="2798f-133">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="2798f-134">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="2798f-134">[C#], F#</span></span>      |
| <span data-ttu-id="2798f-135">Webové aplikace ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="2798f-135">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="2798f-136">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="2798f-136">[C#], F#</span></span>      |
| <span data-ttu-id="2798f-137">Webové aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2798f-137">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="2798f-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="2798f-138">[C#]</span></span>          |
| <span data-ttu-id="2798f-139">ASP.NET Core s úhlová</span><span class="sxs-lookup"><span data-stu-id="2798f-139">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="2798f-140">[C#]</span><span class="sxs-lookup"><span data-stu-id="2798f-140">[C#]</span></span>          |
| <span data-ttu-id="2798f-141">ASP.NET Core s React.js</span><span class="sxs-lookup"><span data-stu-id="2798f-141">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="2798f-142">[C#]</span><span class="sxs-lookup"><span data-stu-id="2798f-142">[C#]</span></span>          |
| <span data-ttu-id="2798f-143">ASP.NET Core s React.js a – obnovení</span><span class="sxs-lookup"><span data-stu-id="2798f-143">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="2798f-144">[C#]</span><span class="sxs-lookup"><span data-stu-id="2798f-144">[C#]</span></span>          |
| <span data-ttu-id="2798f-145">Jádro ASP.NET Web API</span><span class="sxs-lookup"><span data-stu-id="2798f-145">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="2798f-146">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="2798f-146">[C#], F#</span></span>      |
| <span data-ttu-id="2798f-147">global.json file</span><span class="sxs-lookup"><span data-stu-id="2798f-147">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="2798f-148">Konfigurace Nuget</span><span class="sxs-lookup"><span data-stu-id="2798f-148">Nuget config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="2798f-149">Webové konfigurace</span><span class="sxs-lookup"><span data-stu-id="2798f-149">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="2798f-150">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="2798f-150">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="2798f-151">Stránky Razor</span><span class="sxs-lookup"><span data-stu-id="2798f-151">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="2798f-152">MVC/ViewImports</span><span class="sxs-lookup"><span data-stu-id="2798f-152">MVC/ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="2798f-153">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="2798f-153">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="2798f-154">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="2798f-154">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="2798f-155">Příkaz obsahuje seznam výchozích šablon.</span><span class="sxs-lookup"><span data-stu-id="2798f-155">The command contains a default list of templates.</span></span> <span data-ttu-id="2798f-156">Použití `dotnet new -all` získat seznam dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="2798f-156">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="2798f-157">V následující tabulce jsou uvedeny šablony, které jsou předinstalované .NET Core 1.x SDK.</span><span class="sxs-lookup"><span data-stu-id="2798f-157">The following table shows the templates that come pre-installed with the .NET Core 1.x SDK.</span></span> <span data-ttu-id="2798f-158">Výchozí jazyk pro šablonu se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="2798f-158">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="2798f-159">Popis šablony</span><span class="sxs-lookup"><span data-stu-id="2798f-159">Template description</span></span>  | <span data-ttu-id="2798f-160">Název šablony</span><span class="sxs-lookup"><span data-stu-id="2798f-160">Template name</span></span> | <span data-ttu-id="2798f-161">Jazyky</span><span class="sxs-lookup"><span data-stu-id="2798f-161">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="2798f-162">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="2798f-162">Console application</span></span>  | `console`     | <span data-ttu-id="2798f-163">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="2798f-163">[C#], F#</span></span>  |
| <span data-ttu-id="2798f-164">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="2798f-164">Class library</span></span>        | `classlib`    | <span data-ttu-id="2798f-165">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="2798f-165">[C#], F#</span></span>  |
| <span data-ttu-id="2798f-166">Projektu testování částí</span><span class="sxs-lookup"><span data-stu-id="2798f-166">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="2798f-167">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="2798f-167">[C#], F#</span></span>  |
| <span data-ttu-id="2798f-168">xUnit testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="2798f-168">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="2798f-169">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="2798f-169">[C#], F#</span></span>  |
| <span data-ttu-id="2798f-170">ASP.NET Core prázdný</span><span class="sxs-lookup"><span data-stu-id="2798f-170">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="2798f-171">[C#]</span><span class="sxs-lookup"><span data-stu-id="2798f-171">[C#]</span></span>      |
| <span data-ttu-id="2798f-172">Webové aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2798f-172">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="2798f-173">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="2798f-173">[C#], F#</span></span>  |
| <span data-ttu-id="2798f-174">Jádro ASP.NET Web API</span><span class="sxs-lookup"><span data-stu-id="2798f-174">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="2798f-175">[C#]</span><span class="sxs-lookup"><span data-stu-id="2798f-175">[C#]</span></span>      |
| <span data-ttu-id="2798f-176">Konfigurace Nuget</span><span class="sxs-lookup"><span data-stu-id="2798f-176">Nuget config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="2798f-177">Webové konfigurace</span><span class="sxs-lookup"><span data-stu-id="2798f-177">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="2798f-178">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="2798f-178">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="2798f-179">Možnosti</span><span class="sxs-lookup"><span data-stu-id="2798f-179">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="2798f-180">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="2798f-180">.NET Core 2.x</span></span>](#tab/netcore2x)

`--force`

<span data-ttu-id="2798f-181">Vynutí obsah má být vygenerován i v případě, že se změní stávající soubory.</span><span class="sxs-lookup"><span data-stu-id="2798f-181">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="2798f-182">To je potřeba, když výstupnímu adresáři již obsahuje projektu.</span><span class="sxs-lookup"><span data-stu-id="2798f-182">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="2798f-183">Vytiskne nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="2798f-183">Prints out help for the command.</span></span> <span data-ttu-id="2798f-184">Nelze vyvolat pro `dotnet new` příkaz sám sebe nebo pro všechny šablony, jako například `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="2798f-184">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="2798f-185">Nainstaluje sadu zdroje nebo šablony z `PATH` nebo `NUGET_ID` zadat.</span><span class="sxs-lookup"><span data-stu-id="2798f-185">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="2798f-186">Informace o vytváření vlastních šablon najdete v tématu [vlastních šablon pro dotnet nové](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="2798f-186">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="2798f-187">Obsahuje seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="2798f-187">Lists templates containing the specified name.</span></span> <span data-ttu-id="2798f-188">Pokud je vyvolána pro `dotnet new` příkaz, zobrazí seznam možných šablony, které jsou k dispozici pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="2798f-188">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="2798f-189">Například pokud adresář již obsahuje projekt, nepodporuje zobrazí seznam všech šablon projektu.</span><span class="sxs-lookup"><span data-stu-id="2798f-189">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="2798f-190">Jazyk šablonu, kterou chcete vytvořit.</span><span class="sxs-lookup"><span data-stu-id="2798f-190">The language of the template to create.</span></span> <span data-ttu-id="2798f-191">Jazyk přijata, se liší podle šablony (viz výchozí hodnoty v [argumenty](#arguments) části).</span><span class="sxs-lookup"><span data-stu-id="2798f-191">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="2798f-192">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="2798f-192">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="2798f-193">Název pro vytvoření výstupu.</span><span class="sxs-lookup"><span data-stu-id="2798f-193">The name for the created output.</span></span> <span data-ttu-id="2798f-194">Pokud není zadán žádný název, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="2798f-194">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="2798f-195">Umístění pro generovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="2798f-195">Location to place the generated output.</span></span> <span data-ttu-id="2798f-196">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="2798f-196">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="2798f-197">Filtry šablony vycházející z dostupných typů.</span><span class="sxs-lookup"><span data-stu-id="2798f-197">Filters templates based on available types.</span></span> <span data-ttu-id="2798f-198">Předdefinované hodnoty jsou "projektu", "položka" nebo "ostatní".</span><span class="sxs-lookup"><span data-stu-id="2798f-198">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="2798f-199">Odinstaluje sadu zdroje nebo šablony v `PATH` nebo `NUGET_ID` zadat.</span><span class="sxs-lookup"><span data-stu-id="2798f-199">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="2798f-200">Chcete-li odinstalovat šablony pomocí `PATH`, budete muset plně kvalifikovanou cestu.</span><span class="sxs-lookup"><span data-stu-id="2798f-200">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="2798f-201">Například *C: či uživatelů nebo\<uživatele > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z obsahující složka se není.</span><span class="sxs-lookup"><span data-stu-id="2798f-201">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="2798f-202">Kromě toho nezahrnují konečné ukončující lomítko adresáře na cestu k šabloně.</span><span class="sxs-lookup"><span data-stu-id="2798f-202">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="2798f-203">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="2798f-203">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="2798f-204">Při spuštění v kontextu jsou uvedeny všechny šablony pro konkrétní typ projektu `dotnet new` příkaz samostatně.</span><span class="sxs-lookup"><span data-stu-id="2798f-204">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="2798f-205">Při spuštění v rámci konkrétní šablonu, jako například `dotnet new web -all`, `-all` interpretována jako vytvoření příznak force.</span><span class="sxs-lookup"><span data-stu-id="2798f-205">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="2798f-206">To je potřeba, když výstupnímu adresáři již obsahuje projektu.</span><span class="sxs-lookup"><span data-stu-id="2798f-206">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="2798f-207">Vytiskne nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="2798f-207">Prints out help for the command.</span></span> <span data-ttu-id="2798f-208">Nelze vyvolat pro `dotnet new` příkaz sám sebe nebo pro všechny šablony, jako například `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="2798f-208">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="2798f-209">Obsahuje seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="2798f-209">Lists templates containing the specified name.</span></span> <span data-ttu-id="2798f-210">Pokud je vyvolána pro `dotnet new` příkaz, zobrazí seznam možných šablony, které jsou k dispozici pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="2798f-210">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="2798f-211">Například pokud adresář již obsahuje projekt, nepodporuje zobrazí seznam všech šablon projektu.</span><span class="sxs-lookup"><span data-stu-id="2798f-211">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="2798f-212">Jazyk šablonu, kterou chcete vytvořit.</span><span class="sxs-lookup"><span data-stu-id="2798f-212">The language of the template to create.</span></span> <span data-ttu-id="2798f-213">Jazyk přijata, se liší podle šablony (viz výchozí hodnoty v [argumenty](#arguments) části).</span><span class="sxs-lookup"><span data-stu-id="2798f-213">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="2798f-214">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="2798f-214">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="2798f-215">Název pro vytvoření výstupu.</span><span class="sxs-lookup"><span data-stu-id="2798f-215">The name for the created output.</span></span> <span data-ttu-id="2798f-216">Pokud není zadán žádný název, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="2798f-216">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="2798f-217">Umístění pro generovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="2798f-217">Location to place the generated output.</span></span> <span data-ttu-id="2798f-218">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="2798f-218">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="2798f-219">Možnosti šablony</span><span class="sxs-lookup"><span data-stu-id="2798f-219">Template options</span></span>

<span data-ttu-id="2798f-220">Každá šablona projektu může mít další možnosti, které jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="2798f-220">Each project template may have additional options available.</span></span> <span data-ttu-id="2798f-221">Základní šablony mají následující možnosti:</span><span class="sxs-lookup"><span data-stu-id="2798f-221">The core templates have the following additional options:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="2798f-222">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="2798f-222">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="2798f-223">**konzole úhlová, reagovat, reactredux**</span><span class="sxs-lookup"><span data-stu-id="2798f-223">**console, angular, react, reactredux**</span></span>

<span data-ttu-id="2798f-224">`--no-restore`-Nepodporuje provedení implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="2798f-224">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="2798f-225">**classlib**</span><span class="sxs-lookup"><span data-stu-id="2798f-225">**classlib**</span></span>

<span data-ttu-id="2798f-226">`-f|--framework <FRAMEWORK>`-Určuje [framework](../../standard/frameworks.md) k cíli.</span><span class="sxs-lookup"><span data-stu-id="2798f-226">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="2798f-227">Hodnoty: `netcoreapp2.0` pro vytvoření základní knihovny tříd rozhraní .NET nebo `netstandard2.0` vytvořit standardní knihovny tříd rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="2798f-227">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="2798f-228">Výchozí hodnota je `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="2798f-228">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="2798f-229">`--no-restore`-Nepodporuje provedení implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="2798f-229">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="2798f-230">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="2798f-230">**mstest, xunit**</span></span>

<span data-ttu-id="2798f-231">`-p|--enable-pack`– Umožňuje vytváření balíčků pro projekt pomocí [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="2798f-231">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="2798f-232">`--no-restore`-Nepodporuje provedení implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="2798f-232">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="2798f-233">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="2798f-233">**globaljson**</span></span>

<span data-ttu-id="2798f-234">`--sdk-version <VERSION_NUMBER>`-Určuje verzi rozhraní .NET Core SDK pro použití v *global.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="2798f-234">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="2798f-235">**web**</span><span class="sxs-lookup"><span data-stu-id="2798f-235">**web**</span></span>

<span data-ttu-id="2798f-236">`--use-launch-settings`-Zahrnuje *launchSettings.json* ve výstupu vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="2798f-236">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="2798f-237">`--no-restore`-Nepodporuje provedení implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="2798f-237">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="2798f-238">**webapi**</span><span class="sxs-lookup"><span data-stu-id="2798f-238">**webapi**</span></span>

<span data-ttu-id="2798f-239">`-au|--auth <AUTHENTICATION_TYPE>`-Typ ověřování.</span><span class="sxs-lookup"><span data-stu-id="2798f-239">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="2798f-240">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="2798f-240">The possible values are:</span></span>

- <span data-ttu-id="2798f-241">`None`-Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="2798f-241">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="2798f-242">`IndividualB2C`-Jednotlivé ověřování s Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="2798f-242">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="2798f-243">`SingleOrg`-Organizační ověřování pro jednoho klienta.</span><span class="sxs-lookup"><span data-stu-id="2798f-243">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="2798f-244">`Windows`-Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="2798f-244">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="2798f-245">`--aad-b2c-instance <INSTANCE>`-Instance Azure Active Directory B2C se připojit k.</span><span class="sxs-lookup"><span data-stu-id="2798f-245">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="2798f-246">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="2798f-246">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="2798f-247">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="2798f-247">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="2798f-248">`-ssp|--susi-policy-id <ID>`– ID přihlášení a odhlášení zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="2798f-248">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="2798f-249">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="2798f-249">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="2798f-250">`--aad-instance <INSTANCE>`-Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="2798f-250">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="2798f-251">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="2798f-251">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="2798f-252">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="2798f-252">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="2798f-253">`--client-id <ID>`– ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="2798f-253">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="2798f-254">Použití s `IndividualB2C` nebo `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="2798f-254">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="2798f-255">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="2798f-255">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="2798f-256">`--domain <DOMAIN>`-Doména pro directory klienta.</span><span class="sxs-lookup"><span data-stu-id="2798f-256">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="2798f-257">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="2798f-257">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="2798f-258">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="2798f-258">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="2798f-259">`--tenant-id <ID>`-TenantId ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="2798f-259">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="2798f-260">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="2798f-260">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="2798f-261">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="2798f-261">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="2798f-262">`-r|--org-read-access`– Umožňuje této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="2798f-262">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="2798f-263">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="2798f-263">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="2798f-264">`--use-launch-settings`-Zahrnuje *launchSettings.json* ve výstupu vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="2798f-264">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="2798f-265">`-uld|--use-local-db`-Určuje, že místo SQLite by použít LocalDB.</span><span class="sxs-lookup"><span data-stu-id="2798f-265">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="2798f-266">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="2798f-266">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="2798f-267">`--no-restore`-Nepodporuje provedení implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="2798f-267">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="2798f-268">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="2798f-268">**mvc, razor**</span></span>

<span data-ttu-id="2798f-269">`-au|--auth <AUTHENTICATION_TYPE>`-Typ ověřování.</span><span class="sxs-lookup"><span data-stu-id="2798f-269">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="2798f-270">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="2798f-270">The possible values are:</span></span>

- <span data-ttu-id="2798f-271">`None`-Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="2798f-271">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="2798f-272">`Individual`-Jednotlivé ověřování.</span><span class="sxs-lookup"><span data-stu-id="2798f-272">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="2798f-273">`IndividualB2C`-Jednotlivé ověřování s Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="2798f-273">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="2798f-274">`SingleOrg`-Organizační ověřování pro jednoho klienta.</span><span class="sxs-lookup"><span data-stu-id="2798f-274">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="2798f-275">`MultiOrg`-Organizační ověřování pro víc klientů.</span><span class="sxs-lookup"><span data-stu-id="2798f-275">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="2798f-276">`Windows`-Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="2798f-276">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="2798f-277">`--aad-b2c-instance <INSTANCE>`-Instance Azure Active Directory B2C se připojit k.</span><span class="sxs-lookup"><span data-stu-id="2798f-277">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="2798f-278">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="2798f-278">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="2798f-279">Výchozí hodnota je `https://login.microsoftonline.com/tfp/` .</span><span class="sxs-lookup"><span data-stu-id="2798f-279">The default value is `https://login.microsoftonline.com/tfp/` .</span></span>

<span data-ttu-id="2798f-280">`-ssp|--susi-policy-id <ID>`– ID přihlášení a odhlášení zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="2798f-280">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="2798f-281">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="2798f-281">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="2798f-282">`-rp|--reset-password-policy-id <ID>`-Resetování hesla ID zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="2798f-282">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="2798f-283">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="2798f-283">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="2798f-284">`-ep|--edit-profile-policy-id <ID>`-Upravit profil ID zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="2798f-284">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="2798f-285">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="2798f-285">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="2798f-286">`--aad-instance <INSTANCE>`-Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="2798f-286">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="2798f-287">Použití s `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="2798f-287">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="2798f-288">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="2798f-288">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="2798f-289">`--client-id <ID>`– ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="2798f-289">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="2798f-290">Použití s `IndividualB2C`, `SingleOrg`, nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="2798f-290">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="2798f-291">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="2798f-291">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="2798f-292">`--domain <DOMAIN>`-Doména pro directory klienta.</span><span class="sxs-lookup"><span data-stu-id="2798f-292">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="2798f-293">Použití s `SingleOrg` nebo `IndividualB2C` ověřování...</span><span class="sxs-lookup"><span data-stu-id="2798f-293">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="2798f-294">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="2798f-294">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="2798f-295">`--tenant-id <ID>`-TenantId ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="2798f-295">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="2798f-296">Použití s `SingleOrg` ověřování...</span><span class="sxs-lookup"><span data-stu-id="2798f-296">Use with `SingleOrg` authentication..</span></span> <span data-ttu-id="2798f-297">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="2798f-297">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="2798f-298">`--callback-path <PATH>`– Cesta žádosti v rámci základní cesty aplikace identifikátor URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="2798f-298">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="2798f-299">Použití s `SingleOrg` nebo `IndividualB2C` ověřování...</span><span class="sxs-lookup"><span data-stu-id="2798f-299">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="2798f-300">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="2798f-300">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="2798f-301">`-r|--org-read-access`– Umožňuje této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="2798f-301">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="2798f-302">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="2798f-302">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="2798f-303">`--use-launch-settings`-Zahrnuje *launchSettings.json* ve výstupu vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="2798f-303">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="2798f-304">`--use-browserlink`-Zahrnuje BrowserLink v projektu.</span><span class="sxs-lookup"><span data-stu-id="2798f-304">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="2798f-305">`-uld|--use-local-db`-Určuje, že místo SQLite by použít LocalDB.</span><span class="sxs-lookup"><span data-stu-id="2798f-305">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="2798f-306">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="2798f-306">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="2798f-307">`--no-restore`-Nepodporuje provedení implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="2798f-307">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="2798f-308">**stránka**</span><span class="sxs-lookup"><span data-stu-id="2798f-308">**page**</span></span>

<span data-ttu-id="2798f-309">`-na|--namespace <NAMESPACE_NAME>`-Namespace pro generovaný kód.</span><span class="sxs-lookup"><span data-stu-id="2798f-309">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="2798f-310">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="2798f-310">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="2798f-311">`-np|--no-pagemodel`-Vytvoří danou stránku bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="2798f-311">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="2798f-312">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="2798f-312">**viewimports**</span></span>

<span data-ttu-id="2798f-313">`-na|--namespace <NAMESPACE_NAME>`-Namespace pro generovaný kód.</span><span class="sxs-lookup"><span data-stu-id="2798f-313">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="2798f-314">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="2798f-314">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="2798f-315">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="2798f-315">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="2798f-316">**console, xunit, mstest, web, webapi**</span><span class="sxs-lookup"><span data-stu-id="2798f-316">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="2798f-317">`-f|--framework`-Určuje [framework](../../standard/frameworks.md) k cíli.</span><span class="sxs-lookup"><span data-stu-id="2798f-317">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="2798f-318">Hodnoty: `netcoreapp1.0` nebo `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="2798f-318">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="2798f-319">Výchozí hodnota je `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="2798f-319">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="2798f-320">**classlib**</span><span class="sxs-lookup"><span data-stu-id="2798f-320">**classlib**</span></span>

<span data-ttu-id="2798f-321">`-f|--framework`-Určuje [framework](../../standard/frameworks.md) k cíli.</span><span class="sxs-lookup"><span data-stu-id="2798f-321">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="2798f-322">Hodnoty: `netcoreapp1.0`, `netcoreapp1.1`, nebo `netstandard1.0` k `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="2798f-322">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="2798f-323">Výchozí hodnota je `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="2798f-323">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="2798f-324">**mvc**</span><span class="sxs-lookup"><span data-stu-id="2798f-324">**mvc**</span></span>

<span data-ttu-id="2798f-325">`-f|--framework`-Určuje [framework](../../standard/frameworks.md) k cíli.</span><span class="sxs-lookup"><span data-stu-id="2798f-325">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="2798f-326">Hodnoty: `netcoreapp1.0` nebo `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="2798f-326">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="2798f-327">Výchozí hodnota je `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="2798f-327">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="2798f-328">`-au|--auth`-Typ ověřování.</span><span class="sxs-lookup"><span data-stu-id="2798f-328">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="2798f-329">Hodnoty: `None` nebo `Individual`.</span><span class="sxs-lookup"><span data-stu-id="2798f-329">Values: `None` or `Individual`.</span></span> <span data-ttu-id="2798f-330">Výchozí hodnota je `None`.</span><span class="sxs-lookup"><span data-stu-id="2798f-330">The default value is `None`.</span></span>

<span data-ttu-id="2798f-331">`-uld|--use-local-db`-Určuje, zda pro použití LocalDB místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="2798f-331">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="2798f-332">Hodnoty: `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="2798f-332">Values: `true` or `false`.</span></span> <span data-ttu-id="2798f-333">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="2798f-333">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="2798f-334">Příklady</span><span class="sxs-lookup"><span data-stu-id="2798f-334">Examples</span></span>

<span data-ttu-id="2798f-335">Vytvoření projektu aplikace konzoly F # v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="2798f-335">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang f#`

<span data-ttu-id="2798f-336">Vytvořte standardní rozhraní .NET projektu knihovny tříd v zadaný adresář (dostupné pouze s .NET Core 2.0 SDK nebo novější verze):</span><span class="sxs-lookup"><span data-stu-id="2798f-336">Create a .NET Standard class library project in the specified directory (available only with .NET Core 2.0 SDK or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="2798f-337">Vytvořte nový projekt aplikace ASP.NET Core C# MVC v aktuálním adresáři bez jakéhokoli ověřování cílení na rozhraní .NET 2.0 jádra:</span><span class="sxs-lookup"><span data-stu-id="2798f-337">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication targeting .NET Core 2.0:</span></span>

`dotnet new mvc -au None -f netcoreapp2.0`

<span data-ttu-id="2798f-338">Vytvoření nové aplikace xUnit cílení na rozhraní .NET 2.0 jádra:</span><span class="sxs-lookup"><span data-stu-id="2798f-338">Create a new xUnit application targeting .NET Core 2.0:</span></span>

`dotnet new xunit --framework netcoreapp2.0`

<span data-ttu-id="2798f-339">Seznam všech šablon, které jsou k dispozici pro MVC:</span><span class="sxs-lookup"><span data-stu-id="2798f-339">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

## <a name="see-also"></a><span data-ttu-id="2798f-340">Viz také</span><span class="sxs-lookup"><span data-stu-id="2798f-340">See also</span></span>

[<span data-ttu-id="2798f-341">Vlastní šablony pro nové dotnet.</span><span class="sxs-lookup"><span data-stu-id="2798f-341">Custom templates for dotnet new</span></span>](custom-templates.md)  
[<span data-ttu-id="2798f-342">Vytvoření vlastní šablony pro dotnet new</span><span class="sxs-lookup"><span data-stu-id="2798f-342">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
[<span data-ttu-id="2798f-343">dotnet/dotnet-template-samples GitHub repo</span><span class="sxs-lookup"><span data-stu-id="2798f-343">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
[<span data-ttu-id="2798f-344">Dostupné šablony pro nové dotnet.</span><span class="sxs-lookup"><span data-stu-id="2798f-344">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
