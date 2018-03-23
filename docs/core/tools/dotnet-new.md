---
title: nový příkaz DotNet - .NET Core rozhraní příkazového řádku
description: Nový příkaz dotnet vytvoří nové projekty .NET Core na základě zadané šablony.
author: mairaw
ms.author: mairaw
ms.date: 03/21/2018
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 2cbd42195d0ec713d2ccb4af823075ece950ceff
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/23/2018
---
# <a name="dotnet-new"></a><span data-ttu-id="cfdd0-103">nové DotNet.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="cfdd0-104">Název</span><span class="sxs-lookup"><span data-stu-id="cfdd0-104">Name</span></span>

<span data-ttu-id="cfdd0-105">`dotnet new` -Vytvoří nový projekt, konfigurační soubor nebo řešení v závislosti na určené šablony.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="cfdd0-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="cfdd0-106">Synopsis</span></span>

# <a name="net-core-20tabnetcore2x"></a>[<span data-ttu-id="cfdd0-107">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="cfdd0-107">.NET Core 2.0</span></span>](#tab/netcore2x)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="cfdd0-108">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="cfdd0-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="cfdd0-109">Popis</span><span class="sxs-lookup"><span data-stu-id="cfdd0-109">Description</span></span>

<span data-ttu-id="cfdd0-110">`dotnet new` Příkaz nabízí pohodlný způsob, jak inicializovat platný projekt .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-110">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span> 

<span data-ttu-id="cfdd0-111">Příkaz volání [modulu šablon](https://github.com/dotnet/templating) vytvořit artefakty na disku na základě určené šablony a možnosti.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-111">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="cfdd0-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="cfdd0-112">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="cfdd0-113">Šablona pro vytvoření instance při vyvolání příkazu.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="cfdd0-114">Každá šablona může mít specifické možnosti, které lze předat.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="cfdd0-115">Další informace najdete v tématu [možnosti šablony](#template-options).</span><span class="sxs-lookup"><span data-stu-id="cfdd0-115">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-20tabnetcore2x"></a>[<span data-ttu-id="cfdd0-116">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="cfdd0-116">.NET Core 2.0</span></span>](#tab/netcore2x)

<span data-ttu-id="cfdd0-117">Příkaz obsahuje seznam výchozích šablon.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-117">The command contains a default list of templates.</span></span> <span data-ttu-id="cfdd0-118">Použití `dotnet new -l` získat seznam dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-118">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="cfdd0-119">V následující tabulce jsou uvedeny šablony, které jsou předinstalované .NET Core 2.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-119">The following table shows the templates that come pre-installed with the .NET Core 2.0 SDK.</span></span> <span data-ttu-id="cfdd0-120">Výchozí jazyk pro šablonu se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-120">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="cfdd0-121">Popis šablony</span><span class="sxs-lookup"><span data-stu-id="cfdd0-121">Template description</span></span>                          | <span data-ttu-id="cfdd0-122">Název šablony</span><span class="sxs-lookup"><span data-stu-id="cfdd0-122">Template name</span></span> | <span data-ttu-id="cfdd0-123">Jazyky</span><span class="sxs-lookup"><span data-stu-id="cfdd0-123">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="cfdd0-124">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="cfdd0-124">Console application</span></span>                          | `console`     | <span data-ttu-id="cfdd0-125">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="cfdd0-125">[C#], F#, VB</span></span>  |
| <span data-ttu-id="cfdd0-126">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="cfdd0-126">Class library</span></span>                                | `classlib`    | <span data-ttu-id="cfdd0-127">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="cfdd0-127">[C#], F#, VB</span></span>  |
| <span data-ttu-id="cfdd0-128">Projektu testování částí</span><span class="sxs-lookup"><span data-stu-id="cfdd0-128">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="cfdd0-129">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="cfdd0-129">[C#], F#, VB</span></span>  |
| <span data-ttu-id="cfdd0-130">xUnit testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="cfdd0-130">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="cfdd0-131">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="cfdd0-131">[C#], F#, VB</span></span>  |
| <span data-ttu-id="cfdd0-132">ASP.NET Core prázdný</span><span class="sxs-lookup"><span data-stu-id="cfdd0-132">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="cfdd0-133">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="cfdd0-133">[C#], F#</span></span>      |
| <span data-ttu-id="cfdd0-134">Webové aplikace ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="cfdd0-134">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="cfdd0-135">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="cfdd0-135">[C#], F#</span></span>      |
| <span data-ttu-id="cfdd0-136">Webové aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="cfdd0-136">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="cfdd0-137">[C#]</span><span class="sxs-lookup"><span data-stu-id="cfdd0-137">[C#]</span></span>          |
| <span data-ttu-id="cfdd0-138">ASP.NET Core s úhlová</span><span class="sxs-lookup"><span data-stu-id="cfdd0-138">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="cfdd0-139">[C#]</span><span class="sxs-lookup"><span data-stu-id="cfdd0-139">[C#]</span></span>          |
| <span data-ttu-id="cfdd0-140">ASP.NET Core s React.js</span><span class="sxs-lookup"><span data-stu-id="cfdd0-140">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="cfdd0-141">[C#]</span><span class="sxs-lookup"><span data-stu-id="cfdd0-141">[C#]</span></span>          |
| <span data-ttu-id="cfdd0-142">ASP.NET Core s React.js a – obnovení</span><span class="sxs-lookup"><span data-stu-id="cfdd0-142">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="cfdd0-143">[C#]</span><span class="sxs-lookup"><span data-stu-id="cfdd0-143">[C#]</span></span>          |
| <span data-ttu-id="cfdd0-144">Jádro ASP.NET Web API</span><span class="sxs-lookup"><span data-stu-id="cfdd0-144">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="cfdd0-145">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="cfdd0-145">[C#], F#</span></span>      |
| <span data-ttu-id="cfdd0-146">global.json file</span><span class="sxs-lookup"><span data-stu-id="cfdd0-146">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="cfdd0-147">Konfigurace Nuget</span><span class="sxs-lookup"><span data-stu-id="cfdd0-147">Nuget config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="cfdd0-148">Webové konfigurace</span><span class="sxs-lookup"><span data-stu-id="cfdd0-148">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="cfdd0-149">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="cfdd0-149">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="cfdd0-150">Stránky Razor</span><span class="sxs-lookup"><span data-stu-id="cfdd0-150">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="cfdd0-151">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="cfdd0-151">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="cfdd0-152">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="cfdd0-152">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="cfdd0-153">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="cfdd0-153">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="cfdd0-154">Příkaz obsahuje seznam výchozích šablon.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-154">The command contains a default list of templates.</span></span> <span data-ttu-id="cfdd0-155">Použití `dotnet new -all` získat seznam dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-155">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="cfdd0-156">V následující tabulce jsou uvedeny šablony, které jsou předinstalované .NET Core 1.x SDK.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-156">The following table shows the templates that come pre-installed with the .NET Core 1.x SDK.</span></span> <span data-ttu-id="cfdd0-157">Výchozí jazyk pro šablonu se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-157">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="cfdd0-158">Popis šablony</span><span class="sxs-lookup"><span data-stu-id="cfdd0-158">Template description</span></span>  | <span data-ttu-id="cfdd0-159">Název šablony</span><span class="sxs-lookup"><span data-stu-id="cfdd0-159">Template name</span></span> | <span data-ttu-id="cfdd0-160">Jazyky</span><span class="sxs-lookup"><span data-stu-id="cfdd0-160">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="cfdd0-161">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="cfdd0-161">Console application</span></span>  | `console`     | <span data-ttu-id="cfdd0-162">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="cfdd0-162">[C#], F#</span></span>  |
| <span data-ttu-id="cfdd0-163">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="cfdd0-163">Class library</span></span>        | `classlib`    | <span data-ttu-id="cfdd0-164">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="cfdd0-164">[C#], F#</span></span>  |
| <span data-ttu-id="cfdd0-165">Projektu testování částí</span><span class="sxs-lookup"><span data-stu-id="cfdd0-165">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="cfdd0-166">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="cfdd0-166">[C#], F#</span></span>  |
| <span data-ttu-id="cfdd0-167">xUnit testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="cfdd0-167">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="cfdd0-168">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="cfdd0-168">[C#], F#</span></span>  |
| <span data-ttu-id="cfdd0-169">ASP.NET Core prázdný</span><span class="sxs-lookup"><span data-stu-id="cfdd0-169">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="cfdd0-170">[C#]</span><span class="sxs-lookup"><span data-stu-id="cfdd0-170">[C#]</span></span>      |
| <span data-ttu-id="cfdd0-171">Webové aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="cfdd0-171">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="cfdd0-172">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="cfdd0-172">[C#], F#</span></span>  |
| <span data-ttu-id="cfdd0-173">Jádro ASP.NET Web API</span><span class="sxs-lookup"><span data-stu-id="cfdd0-173">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="cfdd0-174">[C#]</span><span class="sxs-lookup"><span data-stu-id="cfdd0-174">[C#]</span></span>      |
| <span data-ttu-id="cfdd0-175">Konfigurace Nuget</span><span class="sxs-lookup"><span data-stu-id="cfdd0-175">Nuget config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="cfdd0-176">Webové konfigurace</span><span class="sxs-lookup"><span data-stu-id="cfdd0-176">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="cfdd0-177">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="cfdd0-177">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="cfdd0-178">Možnosti</span><span class="sxs-lookup"><span data-stu-id="cfdd0-178">Options</span></span>

# <a name="net-core-20tabnetcore2x"></a>[<span data-ttu-id="cfdd0-179">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="cfdd0-179">.NET Core 2.0</span></span>](#tab/netcore2x)

`--force`

<span data-ttu-id="cfdd0-180">Vynutí obsah má být vygenerován i v případě, že se změní stávající soubory.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-180">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="cfdd0-181">To je potřeba, když výstupnímu adresáři již obsahuje projektu.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-181">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="cfdd0-182">Vytiskne nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-182">Prints out help for the command.</span></span> <span data-ttu-id="cfdd0-183">Nelze vyvolat pro `dotnet new` příkaz sám sebe nebo pro všechny šablony, jako například `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-183">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="cfdd0-184">Nainstaluje sadu zdroje nebo šablony z `PATH` nebo `NUGET_ID` zadat.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-184">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="cfdd0-185">Pokud chcete nainstalovat zkušební verzi balíčku šablony, je třeba zadat ve formátu verze `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-185">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="cfdd0-186">Ve výchozím nastavení `dotnet new` předá \* pro verzi, která představuje poslední stabilní balíčku verze.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-186">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="cfdd0-187">Prohlédněte si příklad na [příklady](#examples) části.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-187">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="cfdd0-188">Informace o vytváření vlastních šablon najdete v tématu [vlastních šablon pro dotnet nové](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="cfdd0-188">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="cfdd0-189">Obsahuje seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-189">Lists templates containing the specified name.</span></span> <span data-ttu-id="cfdd0-190">Pokud je vyvolána pro `dotnet new` příkaz, zobrazí seznam možných šablony, které jsou k dispozici pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-190">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="cfdd0-191">Například pokud adresář již obsahuje projekt, nepodporuje zobrazí seznam všech šablon projektu.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-191">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="cfdd0-192">Jazyk šablonu, kterou chcete vytvořit.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-192">The language of the template to create.</span></span> <span data-ttu-id="cfdd0-193">Jazyk přijata, se liší podle šablony (viz výchozí hodnoty v [argumenty](#arguments) části).</span><span class="sxs-lookup"><span data-stu-id="cfdd0-193">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="cfdd0-194">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-194">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="cfdd0-195">Název pro vytvoření výstupu.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-195">The name for the created output.</span></span> <span data-ttu-id="cfdd0-196">Pokud není zadán žádný název, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-196">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="cfdd0-197">Umístění pro generovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-197">Location to place the generated output.</span></span> <span data-ttu-id="cfdd0-198">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-198">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="cfdd0-199">Filtry šablony vycházející z dostupných typů.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-199">Filters templates based on available types.</span></span> <span data-ttu-id="cfdd0-200">Předdefinované hodnoty jsou "projektu", "položka" nebo "ostatní".</span><span class="sxs-lookup"><span data-stu-id="cfdd0-200">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="cfdd0-201">Odinstaluje sadu zdroje nebo šablony v `PATH` nebo `NUGET_ID` zadat.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-201">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="cfdd0-202">Chcete-li odinstalovat šablony pomocí `PATH`, budete muset plně kvalifikovanou cestu.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-202">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="cfdd0-203">Například *C: či uživatelů nebo\<uživatele > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z obsahující složka se není.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-203">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="cfdd0-204">Kromě toho nezahrnují konečné ukončující lomítko adresáře na cestu k šabloně.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-204">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="cfdd0-205">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="cfdd0-205">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="cfdd0-206">Při spuštění v kontextu jsou uvedeny všechny šablony pro konkrétní typ projektu `dotnet new` příkaz samostatně.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-206">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="cfdd0-207">Při spuštění v rámci konkrétní šablonu, jako například `dotnet new web -all`, `-all` interpretována jako vytvoření příznak force.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-207">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="cfdd0-208">To je potřeba, když výstupnímu adresáři již obsahuje projektu.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-208">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="cfdd0-209">Vytiskne nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-209">Prints out help for the command.</span></span> <span data-ttu-id="cfdd0-210">Nelze vyvolat pro `dotnet new` příkaz sám sebe nebo pro všechny šablony, jako například `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-210">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="cfdd0-211">Obsahuje seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-211">Lists templates containing the specified name.</span></span> <span data-ttu-id="cfdd0-212">Pokud je vyvolána pro `dotnet new` příkaz, zobrazí seznam možných šablony, které jsou k dispozici pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-212">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="cfdd0-213">Například pokud adresář již obsahuje projekt, nepodporuje zobrazí seznam všech šablon projektu.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-213">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="cfdd0-214">Jazyk šablonu, kterou chcete vytvořit.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-214">The language of the template to create.</span></span> <span data-ttu-id="cfdd0-215">Jazyk přijata, se liší podle šablony (viz výchozí hodnoty v [argumenty](#arguments) části).</span><span class="sxs-lookup"><span data-stu-id="cfdd0-215">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="cfdd0-216">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-216">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="cfdd0-217">Název pro vytvoření výstupu.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-217">The name for the created output.</span></span> <span data-ttu-id="cfdd0-218">Pokud není zadán žádný název, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-218">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="cfdd0-219">Umístění pro generovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-219">Location to place the generated output.</span></span> <span data-ttu-id="cfdd0-220">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-220">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="cfdd0-221">Možnosti šablony</span><span class="sxs-lookup"><span data-stu-id="cfdd0-221">Template options</span></span>

<span data-ttu-id="cfdd0-222">Každá šablona projektu může mít další možnosti, které jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-222">Each project template may have additional options available.</span></span> <span data-ttu-id="cfdd0-223">Základní šablony mají následující možnosti:</span><span class="sxs-lookup"><span data-stu-id="cfdd0-223">The core templates have the following additional options:</span></span>

# <a name="net-core-20tabnetcore2x"></a>[<span data-ttu-id="cfdd0-224">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="cfdd0-224">.NET Core 2.0</span></span>](#tab/netcore2x)

<span data-ttu-id="cfdd0-225">**konzole úhlová, reagovat, reactredux**</span><span class="sxs-lookup"><span data-stu-id="cfdd0-225">**console, angular, react, reactredux**</span></span>

  <span data-ttu-id="cfdd0-226">`--no-restore` -Nepodporuje provedení implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-226">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="cfdd0-227">**classlib**</span><span class="sxs-lookup"><span data-stu-id="cfdd0-227">**classlib**</span></span>

<span data-ttu-id="cfdd0-228">`-f|--framework <FRAMEWORK>` -Určuje [framework](../../standard/frameworks.md) k cíli.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-228">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="cfdd0-229">Hodnoty: `netcoreapp2.0` pro vytvoření základní knihovny tříd rozhraní .NET nebo `netstandard2.0` vytvořit standardní knihovny tříd rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-229">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="cfdd0-230">Výchozí hodnota je `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-230">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="cfdd0-231">`--no-restore` -Nepodporuje provedení implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-231">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="cfdd0-232">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="cfdd0-232">**mstest, xunit**</span></span>

<span data-ttu-id="cfdd0-233">`-p|--enable-pack` – Umožňuje vytváření balíčků pro projekt pomocí [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="cfdd0-233">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="cfdd0-234">`--no-restore` -Nepodporuje provedení implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-234">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="cfdd0-235">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="cfdd0-235">**globaljson**</span></span>

<span data-ttu-id="cfdd0-236">`--sdk-version <VERSION_NUMBER>` -Určuje verzi rozhraní .NET Core SDK pro použití v *global.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-236">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="cfdd0-237">**web**</span><span class="sxs-lookup"><span data-stu-id="cfdd0-237">**web**</span></span>

<span data-ttu-id="cfdd0-238">`--use-launch-settings` -Zahrnuje *launchSettings.json* ve výstupu vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-238">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="cfdd0-239">`--no-restore` -Nepodporuje provedení implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-239">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="cfdd0-240">**webapi**</span><span class="sxs-lookup"><span data-stu-id="cfdd0-240">**webapi**</span></span>

<span data-ttu-id="cfdd0-241">`-au|--auth <AUTHENTICATION_TYPE>` -Typ ověřování.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-241">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="cfdd0-242">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="cfdd0-242">The possible values are:</span></span>

- <span data-ttu-id="cfdd0-243">`None` -Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="cfdd0-243">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="cfdd0-244">`IndividualB2C` -Jednotlivé ověřování s Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-244">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="cfdd0-245">`SingleOrg` -Organizační ověřování pro jednoho klienta.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-245">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="cfdd0-246">`Windows` -Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-246">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="cfdd0-247">`--aad-b2c-instance <INSTANCE>` -Instance Azure Active Directory B2C se připojit k.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-247">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="cfdd0-248">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-248">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="cfdd0-249">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-249">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="cfdd0-250">`-ssp|--susi-policy-id <ID>` – ID přihlášení a odhlášení zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-250">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="cfdd0-251">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-251">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="cfdd0-252">`--aad-instance <INSTANCE>` -Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-252">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="cfdd0-253">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-253">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="cfdd0-254">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-254">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="cfdd0-255">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-255">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="cfdd0-256">Použití s `IndividualB2C` nebo `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-256">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="cfdd0-257">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-257">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="cfdd0-258">`--domain <DOMAIN>` -Doména pro directory klienta.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-258">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="cfdd0-259">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-259">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="cfdd0-260">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-260">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="cfdd0-261">`--tenant-id <ID>` -TenantId ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-261">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="cfdd0-262">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-262">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="cfdd0-263">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-263">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="cfdd0-264">`-r|--org-read-access` – Umožňuje této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-264">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="cfdd0-265">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-265">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="cfdd0-266">`--use-launch-settings` -Zahrnuje *launchSettings.json* ve výstupu vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-266">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="cfdd0-267">`-uld|--use-local-db` -Určuje, že místo SQLite by použít LocalDB.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-267">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="cfdd0-268">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-268">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="cfdd0-269">`--no-restore` -Nepodporuje provedení implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-269">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="cfdd0-270">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="cfdd0-270">**mvc, razor**</span></span>

<span data-ttu-id="cfdd0-271">`-au|--auth <AUTHENTICATION_TYPE>` -Typ ověřování.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-271">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="cfdd0-272">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="cfdd0-272">The possible values are:</span></span>

- <span data-ttu-id="cfdd0-273">`None` -Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="cfdd0-273">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="cfdd0-274">`Individual` -Jednotlivé ověřování.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-274">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="cfdd0-275">`IndividualB2C` -Jednotlivé ověřování s Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-275">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="cfdd0-276">`SingleOrg` -Organizační ověřování pro jednoho klienta.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-276">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="cfdd0-277">`MultiOrg` -Organizační ověřování pro víc klientů.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-277">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="cfdd0-278">`Windows` -Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-278">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="cfdd0-279">`--aad-b2c-instance <INSTANCE>` -Instance Azure Active Directory B2C se připojit k.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-279">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="cfdd0-280">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-280">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="cfdd0-281">Výchozí hodnota je `https://login.microsoftonline.com/tfp/` .</span><span class="sxs-lookup"><span data-stu-id="cfdd0-281">The default value is `https://login.microsoftonline.com/tfp/` .</span></span>

<span data-ttu-id="cfdd0-282">`-ssp|--susi-policy-id <ID>` – ID přihlášení a odhlášení zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-282">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="cfdd0-283">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-283">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="cfdd0-284">`-rp|--reset-password-policy-id <ID>` -Resetování hesla ID zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-284">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="cfdd0-285">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-285">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="cfdd0-286">`-ep|--edit-profile-policy-id <ID>` -Upravit profil ID zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-286">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="cfdd0-287">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-287">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="cfdd0-288">`--aad-instance <INSTANCE>` -Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-288">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="cfdd0-289">Použití s `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-289">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="cfdd0-290">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-290">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="cfdd0-291">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-291">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="cfdd0-292">Použití s `IndividualB2C`, `SingleOrg`, nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-292">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="cfdd0-293">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-293">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="cfdd0-294">`--domain <DOMAIN>` -Doména pro directory klienta.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-294">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="cfdd0-295">Použití s `SingleOrg` nebo `IndividualB2C` ověřování...</span><span class="sxs-lookup"><span data-stu-id="cfdd0-295">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="cfdd0-296">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-296">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="cfdd0-297">`--tenant-id <ID>` -TenantId ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-297">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="cfdd0-298">Použití s `SingleOrg` ověřování...</span><span class="sxs-lookup"><span data-stu-id="cfdd0-298">Use with `SingleOrg` authentication..</span></span> <span data-ttu-id="cfdd0-299">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-299">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="cfdd0-300">`--callback-path <PATH>` – Cesta žádosti v rámci základní cesty aplikace identifikátor URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-300">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="cfdd0-301">Použití s `SingleOrg` nebo `IndividualB2C` ověřování...</span><span class="sxs-lookup"><span data-stu-id="cfdd0-301">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="cfdd0-302">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-302">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="cfdd0-303">`-r|--org-read-access` – Umožňuje této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-303">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="cfdd0-304">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-304">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="cfdd0-305">`--use-launch-settings` -Zahrnuje *launchSettings.json* ve výstupu vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-305">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="cfdd0-306">`--use-browserlink` -Zahrnuje BrowserLink v projektu.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-306">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="cfdd0-307">`-uld|--use-local-db` -Určuje, že místo SQLite by použít LocalDB.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-307">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="cfdd0-308">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-308">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="cfdd0-309">`--no-restore` -Nepodporuje provedení implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-309">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="cfdd0-310">**Stránka**</span><span class="sxs-lookup"><span data-stu-id="cfdd0-310">**page**</span></span>

<span data-ttu-id="cfdd0-311">`-na|--namespace <NAMESPACE_NAME>`-Namespace pro generovaný kód.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-311">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="cfdd0-312">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-312">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="cfdd0-313">`-np|--no-pagemodel` -Vytvoří danou stránku bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-313">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="cfdd0-314">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="cfdd0-314">**viewimports**</span></span>

<span data-ttu-id="cfdd0-315">`-na|--namespace <NAMESPACE_NAME>`-Namespace pro generovaný kód.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-315">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="cfdd0-316">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-316">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="cfdd0-317">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="cfdd0-317">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="cfdd0-318">**console, xunit, mstest, web, webapi**</span><span class="sxs-lookup"><span data-stu-id="cfdd0-318">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="cfdd0-319">`-f|--framework` -Určuje [framework](../../standard/frameworks.md) k cíli.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-319">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="cfdd0-320">Hodnoty: `netcoreapp1.0` nebo `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-320">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="cfdd0-321">Výchozí hodnota je `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-321">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="cfdd0-322">**classlib**</span><span class="sxs-lookup"><span data-stu-id="cfdd0-322">**classlib**</span></span>

<span data-ttu-id="cfdd0-323">`-f|--framework` -Určuje [framework](../../standard/frameworks.md) k cíli.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-323">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="cfdd0-324">Hodnoty: `netcoreapp1.0`, `netcoreapp1.1`, nebo `netstandard1.0` k `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-324">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="cfdd0-325">Výchozí hodnota je `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-325">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="cfdd0-326">**mvc**</span><span class="sxs-lookup"><span data-stu-id="cfdd0-326">**mvc**</span></span>

<span data-ttu-id="cfdd0-327">`-f|--framework` -Určuje [framework](../../standard/frameworks.md) k cíli.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-327">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="cfdd0-328">Hodnoty: `netcoreapp1.0` nebo `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-328">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="cfdd0-329">Výchozí hodnota je `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-329">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="cfdd0-330">`-au|--auth` -Typ ověřování.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-330">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="cfdd0-331">Hodnoty: `None` nebo `Individual`.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-331">Values: `None` or `Individual`.</span></span> <span data-ttu-id="cfdd0-332">Výchozí hodnota je `None`.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-332">The default value is `None`.</span></span>

<span data-ttu-id="cfdd0-333">`-uld|--use-local-db` -Určuje, zda pro použití LocalDB místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-333">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="cfdd0-334">Hodnoty: `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-334">Values: `true` or `false`.</span></span> <span data-ttu-id="cfdd0-335">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-335">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="cfdd0-336">Příklady</span><span class="sxs-lookup"><span data-stu-id="cfdd0-336">Examples</span></span>

<span data-ttu-id="cfdd0-337">Vytvoření projektu aplikace konzoly F # v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="cfdd0-337">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang f#`

<span data-ttu-id="cfdd0-338">Vytvořte standardní rozhraní .NET projektu knihovny tříd v zadaný adresář (dostupné pouze s .NET Core 2.0 SDK nebo novější verze):</span><span class="sxs-lookup"><span data-stu-id="cfdd0-338">Create a .NET Standard class library project in the specified directory (available only with .NET Core 2.0 SDK or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="cfdd0-339">Vytvořte nový projekt aplikace ASP.NET Core C# MVC v aktuálním adresáři bez jakéhokoli ověřování cílení na rozhraní .NET 2.0 jádra:</span><span class="sxs-lookup"><span data-stu-id="cfdd0-339">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication targeting .NET Core 2.0:</span></span>

`dotnet new mvc -au None -f netcoreapp2.0`

<span data-ttu-id="cfdd0-340">Vytvoření nové aplikace xUnit cílení na rozhraní .NET 2.0 jádra:</span><span class="sxs-lookup"><span data-stu-id="cfdd0-340">Create a new xUnit application targeting .NET Core 2.0:</span></span>

`dotnet new xunit --framework netcoreapp2.0`

<span data-ttu-id="cfdd0-341">Seznam všech šablon, které jsou k dispozici pro MVC:</span><span class="sxs-lookup"><span data-stu-id="cfdd0-341">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="cfdd0-342">Instalace verze 2.0 šablon jedné stránky aplikace ASP.NET Core (příkaz možnost k dispozici pro .NET Core SDK 1.1 a pouze novější verze):</span><span class="sxs-lookup"><span data-stu-id="cfdd0-342">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

## <a name="see-also"></a><span data-ttu-id="cfdd0-343">Viz také</span><span class="sxs-lookup"><span data-stu-id="cfdd0-343">See also</span></span>

[<span data-ttu-id="cfdd0-344">Vlastní šablony pro nové dotnet.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-344">Custom templates for dotnet new</span></span>](custom-templates.md)  
[<span data-ttu-id="cfdd0-345">Vytvoření vlastní šablony pro dotnet new</span><span class="sxs-lookup"><span data-stu-id="cfdd0-345">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
[<span data-ttu-id="cfdd0-346">dotnet/dotnet-template-samples GitHub repo</span><span class="sxs-lookup"><span data-stu-id="cfdd0-346">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
[<span data-ttu-id="cfdd0-347">Dostupné šablony pro nové dotnet.</span><span class="sxs-lookup"><span data-stu-id="cfdd0-347">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
