---
title: nový příkaz DotNet - .NET Core rozhraní příkazového řádku
description: Nový příkaz dotnet vytvoří nové projekty .NET Core na základě zadané šablony.
author: mairaw
ms.author: mairaw
ms.date: 06/12/2018
ms.openlocfilehash: f0ef91361dfbc2c2ba5532fbd607786289e98c69
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208313"
---
# <a name="dotnet-new"></a><span data-ttu-id="0988f-103">nové DotNet.</span><span class="sxs-lookup"><span data-stu-id="0988f-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="0988f-104">Název</span><span class="sxs-lookup"><span data-stu-id="0988f-104">Name</span></span>

<span data-ttu-id="0988f-105">`dotnet new` -Vytvoří nový projekt, konfigurační soubor nebo řešení v závislosti na určené šablony.</span><span class="sxs-lookup"><span data-stu-id="0988f-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0988f-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="0988f-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="0988f-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="0988f-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output]
    [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="0988f-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="0988f-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0988f-109">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="0988f-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="0988f-110">Popis</span><span class="sxs-lookup"><span data-stu-id="0988f-110">Description</span></span>

<span data-ttu-id="0988f-111">`dotnet new` Příkaz nabízí pohodlný způsob, jak inicializovat platný projekt .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0988f-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="0988f-112">Příkaz volání [modulu šablon](https://github.com/dotnet/templating) vytvořit artefakty na disku na základě určené šablony a možnosti.</span><span class="sxs-lookup"><span data-stu-id="0988f-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="0988f-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="0988f-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="0988f-114">Šablona pro vytvoření instance při vyvolání příkazu.</span><span class="sxs-lookup"><span data-stu-id="0988f-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="0988f-115">Každá šablona může mít specifické možnosti, které lze předat.</span><span class="sxs-lookup"><span data-stu-id="0988f-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="0988f-116">Další informace najdete v tématu [možnosti šablony](#template-options).</span><span class="sxs-lookup"><span data-stu-id="0988f-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="0988f-117">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="0988f-117">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="0988f-118">Příkaz obsahuje seznam výchozích šablon.</span><span class="sxs-lookup"><span data-stu-id="0988f-118">The command contains a default list of templates.</span></span> <span data-ttu-id="0988f-119">Použití `dotnet new -l` získat seznam dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="0988f-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="0988f-120">V následující tabulce jsou uvedeny šablony, které jsou předinstalované .NET Core SDK 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="0988f-120">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="0988f-121">Výchozí jazyk pro šablonu se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="0988f-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="0988f-122">Popis šablony</span><span class="sxs-lookup"><span data-stu-id="0988f-122">Template description</span></span>                          | <span data-ttu-id="0988f-123">Název šablony</span><span class="sxs-lookup"><span data-stu-id="0988f-123">Template name</span></span>   | <span data-ttu-id="0988f-124">Jazyky</span><span class="sxs-lookup"><span data-stu-id="0988f-124">Languages</span></span>     |
|----------------------------------------------|-----------------|---------------|
| <span data-ttu-id="0988f-125">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="0988f-125">Console application</span></span>                          | `console`       | <span data-ttu-id="0988f-126">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="0988f-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="0988f-127">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="0988f-127">Class library</span></span>                                | `classlib`      | <span data-ttu-id="0988f-128">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="0988f-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="0988f-129">Projektu testování částí</span><span class="sxs-lookup"><span data-stu-id="0988f-129">Unit test project</span></span>                            | `mstest`        | <span data-ttu-id="0988f-130">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="0988f-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="0988f-131">xUnit testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="0988f-131">xUnit test project</span></span>                           | `xunit`         | <span data-ttu-id="0988f-132">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="0988f-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="0988f-133">Stránky Razor</span><span class="sxs-lookup"><span data-stu-id="0988f-133">Razor page</span></span>                                   | `page`          | <span data-ttu-id="0988f-134">[C#]</span><span class="sxs-lookup"><span data-stu-id="0988f-134">[C#]</span></span>          |
| <span data-ttu-id="0988f-135">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="0988f-135">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="0988f-136">[C#]</span><span class="sxs-lookup"><span data-stu-id="0988f-136">[C#]</span></span>          |
| <span data-ttu-id="0988f-137">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="0988f-137">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="0988f-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="0988f-138">[C#]</span></span>          |
| <span data-ttu-id="0988f-139">ASP.NET Core prázdný</span><span class="sxs-lookup"><span data-stu-id="0988f-139">ASP.NET Core empty</span></span>                           | `web`           | <span data-ttu-id="0988f-140">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="0988f-140">[C#], F#</span></span>      |
| <span data-ttu-id="0988f-141">Webové aplikace ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="0988f-141">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="0988f-142">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="0988f-142">[C#], F#</span></span>      |
| <span data-ttu-id="0988f-143">Webové aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0988f-143">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="0988f-144">[C#]</span><span class="sxs-lookup"><span data-stu-id="0988f-144">[C#]</span></span>          |
| <span data-ttu-id="0988f-145">ASP.NET Core s úhlová</span><span class="sxs-lookup"><span data-stu-id="0988f-145">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="0988f-146">[C#]</span><span class="sxs-lookup"><span data-stu-id="0988f-146">[C#]</span></span>          |
| <span data-ttu-id="0988f-147">ASP.NET Core s React.js</span><span class="sxs-lookup"><span data-stu-id="0988f-147">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="0988f-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="0988f-148">[C#]</span></span>          |
| <span data-ttu-id="0988f-149">ASP.NET Core s React.js a – obnovení</span><span class="sxs-lookup"><span data-stu-id="0988f-149">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="0988f-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="0988f-150">[C#]</span></span>          |
| <span data-ttu-id="0988f-151">Jádro ASP.NET Web API</span><span class="sxs-lookup"><span data-stu-id="0988f-151">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="0988f-152">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="0988f-152">[C#], F#</span></span>      |
| <span data-ttu-id="0988f-153">Knihovna tříd Razor</span><span class="sxs-lookup"><span data-stu-id="0988f-153">Razor class library</span></span>                          | `razorclasslib` | <span data-ttu-id="0988f-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="0988f-154">[C#]</span></span>          |
| <span data-ttu-id="0988f-155">soubor Global.JSON</span><span class="sxs-lookup"><span data-stu-id="0988f-155">global.json file</span></span>                             | `globaljson`    |               |
| <span data-ttu-id="0988f-156">Konfigurace NuGet</span><span class="sxs-lookup"><span data-stu-id="0988f-156">NuGet config</span></span>                                 | `nugetconfig`   |               |
| <span data-ttu-id="0988f-157">Webové konfigurace</span><span class="sxs-lookup"><span data-stu-id="0988f-157">Web config</span></span>                                   | `webconfig`     |               |
| <span data-ttu-id="0988f-158">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="0988f-158">Solution file</span></span>                                | `sln`           |               |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="0988f-159">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="0988f-159">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="0988f-160">Příkaz obsahuje seznam výchozích šablon.</span><span class="sxs-lookup"><span data-stu-id="0988f-160">The command contains a default list of templates.</span></span> <span data-ttu-id="0988f-161">Použití `dotnet new -l` získat seznam dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="0988f-161">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="0988f-162">V následující tabulce jsou uvedeny šablony, které jsou předinstalované .NET Core SDK 2.0.</span><span class="sxs-lookup"><span data-stu-id="0988f-162">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.</span></span> <span data-ttu-id="0988f-163">Výchozí jazyk pro šablonu se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="0988f-163">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="0988f-164">Popis šablony</span><span class="sxs-lookup"><span data-stu-id="0988f-164">Template description</span></span>                          | <span data-ttu-id="0988f-165">Název šablony</span><span class="sxs-lookup"><span data-stu-id="0988f-165">Template name</span></span> | <span data-ttu-id="0988f-166">Jazyky</span><span class="sxs-lookup"><span data-stu-id="0988f-166">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="0988f-167">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="0988f-167">Console application</span></span>                          | `console`     | <span data-ttu-id="0988f-168">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="0988f-168">[C#], F#, VB</span></span>  |
| <span data-ttu-id="0988f-169">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="0988f-169">Class library</span></span>                                | `classlib`    | <span data-ttu-id="0988f-170">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="0988f-170">[C#], F#, VB</span></span>  |
| <span data-ttu-id="0988f-171">Projektu testování částí</span><span class="sxs-lookup"><span data-stu-id="0988f-171">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="0988f-172">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="0988f-172">[C#], F#, VB</span></span>  |
| <span data-ttu-id="0988f-173">xUnit testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="0988f-173">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="0988f-174">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="0988f-174">[C#], F#, VB</span></span>  |
| <span data-ttu-id="0988f-175">ASP.NET Core prázdný</span><span class="sxs-lookup"><span data-stu-id="0988f-175">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="0988f-176">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="0988f-176">[C#], F#</span></span>      |
| <span data-ttu-id="0988f-177">Webové aplikace ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="0988f-177">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="0988f-178">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="0988f-178">[C#], F#</span></span>      |
| <span data-ttu-id="0988f-179">Webové aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0988f-179">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="0988f-180">[C#]</span><span class="sxs-lookup"><span data-stu-id="0988f-180">[C#]</span></span>          |
| <span data-ttu-id="0988f-181">ASP.NET Core s úhlová</span><span class="sxs-lookup"><span data-stu-id="0988f-181">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="0988f-182">[C#]</span><span class="sxs-lookup"><span data-stu-id="0988f-182">[C#]</span></span>          |
| <span data-ttu-id="0988f-183">ASP.NET Core s React.js</span><span class="sxs-lookup"><span data-stu-id="0988f-183">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="0988f-184">[C#]</span><span class="sxs-lookup"><span data-stu-id="0988f-184">[C#]</span></span>          |
| <span data-ttu-id="0988f-185">ASP.NET Core s React.js a – obnovení</span><span class="sxs-lookup"><span data-stu-id="0988f-185">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="0988f-186">[C#]</span><span class="sxs-lookup"><span data-stu-id="0988f-186">[C#]</span></span>          |
| <span data-ttu-id="0988f-187">Jádro ASP.NET Web API</span><span class="sxs-lookup"><span data-stu-id="0988f-187">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="0988f-188">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="0988f-188">[C#], F#</span></span>      |
| <span data-ttu-id="0988f-189">soubor Global.JSON</span><span class="sxs-lookup"><span data-stu-id="0988f-189">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="0988f-190">Konfigurace NuGet</span><span class="sxs-lookup"><span data-stu-id="0988f-190">NuGet config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="0988f-191">Webové konfigurace</span><span class="sxs-lookup"><span data-stu-id="0988f-191">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="0988f-192">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="0988f-192">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="0988f-193">Stránky Razor</span><span class="sxs-lookup"><span data-stu-id="0988f-193">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="0988f-194">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="0988f-194">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="0988f-195">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="0988f-195">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0988f-196">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="0988f-196">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="0988f-197">Příkaz obsahuje seznam výchozích šablon.</span><span class="sxs-lookup"><span data-stu-id="0988f-197">The command contains a default list of templates.</span></span> <span data-ttu-id="0988f-198">Použití `dotnet new -all` získat seznam dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="0988f-198">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="0988f-199">V následující tabulce jsou uvedeny šablony, které jsou předinstalované .NET Core SDK 1.x.</span><span class="sxs-lookup"><span data-stu-id="0988f-199">The following table shows the templates that come pre-installed with the .NET Core SDK 1.x.</span></span> <span data-ttu-id="0988f-200">Výchozí jazyk pro šablonu se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="0988f-200">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="0988f-201">Popis šablony</span><span class="sxs-lookup"><span data-stu-id="0988f-201">Template description</span></span>  | <span data-ttu-id="0988f-202">Název šablony</span><span class="sxs-lookup"><span data-stu-id="0988f-202">Template name</span></span> | <span data-ttu-id="0988f-203">Jazyky</span><span class="sxs-lookup"><span data-stu-id="0988f-203">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="0988f-204">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="0988f-204">Console application</span></span>  | `console`     | <span data-ttu-id="0988f-205">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="0988f-205">[C#], F#</span></span>  |
| <span data-ttu-id="0988f-206">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="0988f-206">Class library</span></span>        | `classlib`    | <span data-ttu-id="0988f-207">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="0988f-207">[C#], F#</span></span>  |
| <span data-ttu-id="0988f-208">Projektu testování částí</span><span class="sxs-lookup"><span data-stu-id="0988f-208">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="0988f-209">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="0988f-209">[C#], F#</span></span>  |
| <span data-ttu-id="0988f-210">xUnit testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="0988f-210">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="0988f-211">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="0988f-211">[C#], F#</span></span>  |
| <span data-ttu-id="0988f-212">ASP.NET Core prázdný</span><span class="sxs-lookup"><span data-stu-id="0988f-212">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="0988f-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="0988f-213">[C#]</span></span>      |
| <span data-ttu-id="0988f-214">Webové aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0988f-214">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="0988f-215">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="0988f-215">[C#], F#</span></span>  |
| <span data-ttu-id="0988f-216">Jádro ASP.NET Web API</span><span class="sxs-lookup"><span data-stu-id="0988f-216">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="0988f-217">[C#]</span><span class="sxs-lookup"><span data-stu-id="0988f-217">[C#]</span></span>      |
| <span data-ttu-id="0988f-218">Konfigurace NuGet</span><span class="sxs-lookup"><span data-stu-id="0988f-218">NuGet config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="0988f-219">Webové konfigurace</span><span class="sxs-lookup"><span data-stu-id="0988f-219">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="0988f-220">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="0988f-220">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="0988f-221">Možnosti</span><span class="sxs-lookup"><span data-stu-id="0988f-221">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="0988f-222">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="0988f-222">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="0988f-223">Vynutí obsah má být vygenerován i v případě, že se změní stávající soubory.</span><span class="sxs-lookup"><span data-stu-id="0988f-223">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="0988f-224">To je potřeba, když výstupnímu adresáři již obsahuje projektu.</span><span class="sxs-lookup"><span data-stu-id="0988f-224">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="0988f-225">Vytiskne nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="0988f-225">Prints out help for the command.</span></span> <span data-ttu-id="0988f-226">Nelze vyvolat pro `dotnet new` příkaz sám sebe nebo pro všechny šablony, jako například `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="0988f-226">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="0988f-227">Nainstaluje sadu zdroje nebo šablony z `PATH` nebo `NUGET_ID` zadat.</span><span class="sxs-lookup"><span data-stu-id="0988f-227">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="0988f-228">Pokud chcete nainstalovat zkušební verzi balíčku šablony, je třeba zadat ve formátu verze `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="0988f-228">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="0988f-229">Ve výchozím nastavení `dotnet new` předá \* pro verzi, která představuje poslední stabilní balíčku verze.</span><span class="sxs-lookup"><span data-stu-id="0988f-229">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="0988f-230">Prohlédněte si příklad na [příklady](#examples) části.</span><span class="sxs-lookup"><span data-stu-id="0988f-230">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="0988f-231">Informace o vytváření vlastních šablon najdete v tématu [vlastních šablon pro dotnet nové](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="0988f-231">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="0988f-232">Obsahuje seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="0988f-232">Lists templates containing the specified name.</span></span> <span data-ttu-id="0988f-233">Pokud je vyvolána pro `dotnet new` příkaz, zobrazí seznam možných šablony, které jsou k dispozici pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="0988f-233">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="0988f-234">Například pokud adresář již obsahuje projekt, nepodporuje zobrazí seznam všech šablon projektu.</span><span class="sxs-lookup"><span data-stu-id="0988f-234">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="0988f-235">Jazyk šablonu, kterou chcete vytvořit.</span><span class="sxs-lookup"><span data-stu-id="0988f-235">The language of the template to create.</span></span> <span data-ttu-id="0988f-236">Jazyk přijata, se liší podle šablony (viz výchozí hodnoty v [argumenty](#arguments) části).</span><span class="sxs-lookup"><span data-stu-id="0988f-236">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="0988f-237">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="0988f-237">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="0988f-238">Některé součásti pro interpretovat `#` za zvláštní znak.</span><span class="sxs-lookup"><span data-stu-id="0988f-238">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="0988f-239">V takových případech je potřeba uzavřít hodnotu parametru jazyka, například `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="0988f-239">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="0988f-240">Název pro vytvoření výstupu.</span><span class="sxs-lookup"><span data-stu-id="0988f-240">The name for the created output.</span></span> <span data-ttu-id="0988f-241">Pokud není zadán žádný název, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="0988f-241">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="0988f-242">Určuje zdroj NuGet, který chcete použít během instalace.</span><span class="sxs-lookup"><span data-stu-id="0988f-242">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="0988f-243">Umístění pro generovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="0988f-243">Location to place the generated output.</span></span> <span data-ttu-id="0988f-244">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="0988f-244">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="0988f-245">Filtry šablony vycházející z dostupných typů.</span><span class="sxs-lookup"><span data-stu-id="0988f-245">Filters templates based on available types.</span></span> <span data-ttu-id="0988f-246">Předdefinované hodnoty jsou "projektu", "položka" nebo "ostatní".</span><span class="sxs-lookup"><span data-stu-id="0988f-246">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="0988f-247">Odinstaluje sadu zdroje nebo šablony v `PATH` nebo `NUGET_ID` zadat.</span><span class="sxs-lookup"><span data-stu-id="0988f-247">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="0988f-248">Chcete-li odinstalovat šablony pomocí `PATH`, budete muset plně kvalifikovanou cestu.</span><span class="sxs-lookup"><span data-stu-id="0988f-248">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="0988f-249">Například *C: či uživatelů nebo\<uživatele > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z obsahující složka se není.</span><span class="sxs-lookup"><span data-stu-id="0988f-249">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="0988f-250">Kromě toho nezahrnují konečné ukončující lomítko adresáře na cestu k šabloně.</span><span class="sxs-lookup"><span data-stu-id="0988f-250">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="0988f-251">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="0988f-251">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="0988f-252">Vynutí obsah má být vygenerován i v případě, že se změní stávající soubory.</span><span class="sxs-lookup"><span data-stu-id="0988f-252">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="0988f-253">To je potřeba, když výstupnímu adresáři již obsahuje projektu.</span><span class="sxs-lookup"><span data-stu-id="0988f-253">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="0988f-254">Vytiskne nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="0988f-254">Prints out help for the command.</span></span> <span data-ttu-id="0988f-255">Nelze vyvolat pro `dotnet new` příkaz sám sebe nebo pro všechny šablony, jako například `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="0988f-255">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="0988f-256">Nainstaluje sadu zdroje nebo šablony z `PATH` nebo `NUGET_ID` zadat.</span><span class="sxs-lookup"><span data-stu-id="0988f-256">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="0988f-257">Pokud chcete nainstalovat zkušební verzi balíčku šablony, je třeba zadat ve formátu verze `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="0988f-257">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="0988f-258">Ve výchozím nastavení `dotnet new` předá \* pro verzi, která představuje poslední stabilní balíčku verze.</span><span class="sxs-lookup"><span data-stu-id="0988f-258">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="0988f-259">Prohlédněte si příklad na [příklady](#examples) části.</span><span class="sxs-lookup"><span data-stu-id="0988f-259">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="0988f-260">Informace o vytváření vlastních šablon najdete v tématu [vlastních šablon pro dotnet nové](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="0988f-260">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="0988f-261">Obsahuje seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="0988f-261">Lists templates containing the specified name.</span></span> <span data-ttu-id="0988f-262">Pokud je vyvolána pro `dotnet new` příkaz, zobrazí seznam možných šablony, které jsou k dispozici pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="0988f-262">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="0988f-263">Například pokud adresář již obsahuje projekt, nepodporuje zobrazí seznam všech šablon projektu.</span><span class="sxs-lookup"><span data-stu-id="0988f-263">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="0988f-264">Jazyk šablonu, kterou chcete vytvořit.</span><span class="sxs-lookup"><span data-stu-id="0988f-264">The language of the template to create.</span></span> <span data-ttu-id="0988f-265">Jazyk přijata, se liší podle šablony (viz výchozí hodnoty v [argumenty](#arguments) části).</span><span class="sxs-lookup"><span data-stu-id="0988f-265">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="0988f-266">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="0988f-266">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="0988f-267">Některé součásti pro interpretovat `#` za zvláštní znak.</span><span class="sxs-lookup"><span data-stu-id="0988f-267">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="0988f-268">V takových případech je potřeba uzavřít hodnotu parametru jazyka, například `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="0988f-268">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="0988f-269">Název pro vytvoření výstupu.</span><span class="sxs-lookup"><span data-stu-id="0988f-269">The name for the created output.</span></span> <span data-ttu-id="0988f-270">Pokud není zadán žádný název, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="0988f-270">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="0988f-271">Umístění pro generovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="0988f-271">Location to place the generated output.</span></span> <span data-ttu-id="0988f-272">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="0988f-272">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="0988f-273">Filtry šablony vycházející z dostupných typů.</span><span class="sxs-lookup"><span data-stu-id="0988f-273">Filters templates based on available types.</span></span> <span data-ttu-id="0988f-274">Předdefinované hodnoty jsou "projektu", "položka" nebo "ostatní".</span><span class="sxs-lookup"><span data-stu-id="0988f-274">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="0988f-275">Odinstaluje sadu zdroje nebo šablony v `PATH` nebo `NUGET_ID` zadat.</span><span class="sxs-lookup"><span data-stu-id="0988f-275">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="0988f-276">Chcete-li odinstalovat šablony pomocí `PATH`, budete muset plně kvalifikovanou cestu.</span><span class="sxs-lookup"><span data-stu-id="0988f-276">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="0988f-277">Například *C: či uživatelů nebo\<uživatele > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z obsahující složka se není.</span><span class="sxs-lookup"><span data-stu-id="0988f-277">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="0988f-278">Kromě toho nezahrnují konečné ukončující lomítko adresáře na cestu k šabloně.</span><span class="sxs-lookup"><span data-stu-id="0988f-278">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0988f-279">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="0988f-279">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="0988f-280">Při spuštění v kontextu jsou uvedeny všechny šablony pro konkrétní typ projektu `dotnet new` příkaz samostatně.</span><span class="sxs-lookup"><span data-stu-id="0988f-280">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="0988f-281">Při spuštění v rámci konkrétní šablonu, jako například `dotnet new web -all`, `-all` interpretována jako vytvoření příznak force.</span><span class="sxs-lookup"><span data-stu-id="0988f-281">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="0988f-282">To je potřeba, když výstupnímu adresáři již obsahuje projektu.</span><span class="sxs-lookup"><span data-stu-id="0988f-282">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="0988f-283">Vytiskne nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="0988f-283">Prints out help for the command.</span></span> <span data-ttu-id="0988f-284">Nelze vyvolat pro `dotnet new` příkaz sám sebe nebo pro všechny šablony, jako například `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="0988f-284">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="0988f-285">Obsahuje seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="0988f-285">Lists templates containing the specified name.</span></span> <span data-ttu-id="0988f-286">Pokud je vyvolána pro `dotnet new` příkaz, zobrazí seznam možných šablony, které jsou k dispozici pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="0988f-286">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="0988f-287">Například pokud adresář již obsahuje projekt, nepodporuje zobrazí seznam všech šablon projektu.</span><span class="sxs-lookup"><span data-stu-id="0988f-287">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="0988f-288">Jazyk šablonu, kterou chcete vytvořit.</span><span class="sxs-lookup"><span data-stu-id="0988f-288">The language of the template to create.</span></span> <span data-ttu-id="0988f-289">Jazyk přijata, se liší podle šablony (viz výchozí hodnoty v [argumenty](#arguments) části).</span><span class="sxs-lookup"><span data-stu-id="0988f-289">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="0988f-290">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="0988f-290">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="0988f-291">Některé součásti pro interpretovat `#` za zvláštní znak.</span><span class="sxs-lookup"><span data-stu-id="0988f-291">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="0988f-292">V takových případech je potřeba uzavřít hodnotu parametru jazyka, například `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="0988f-292">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="0988f-293">Název pro vytvoření výstupu.</span><span class="sxs-lookup"><span data-stu-id="0988f-293">The name for the created output.</span></span> <span data-ttu-id="0988f-294">Pokud není zadán žádný název, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="0988f-294">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="0988f-295">Umístění pro generovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="0988f-295">Location to place the generated output.</span></span> <span data-ttu-id="0988f-296">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="0988f-296">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="0988f-297">Možnosti šablony</span><span class="sxs-lookup"><span data-stu-id="0988f-297">Template options</span></span>

<span data-ttu-id="0988f-298">Každá šablona projektu může mít další možnosti, které jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="0988f-298">Each project template may have additional options available.</span></span> <span data-ttu-id="0988f-299">Základní šablony mají následující možnosti:</span><span class="sxs-lookup"><span data-stu-id="0988f-299">The core templates have the following additional options:</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="0988f-300">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="0988f-300">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="0988f-301">**konzole úhlová, reagují, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="0988f-301">**console, angular, react, reactredux, razorclasslib**</span></span>

  <span data-ttu-id="0988f-302">`--no-restore` -Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="0988f-302">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="0988f-303">**classlib**</span><span class="sxs-lookup"><span data-stu-id="0988f-303">**classlib**</span></span>

<span data-ttu-id="0988f-304">`-f|--framework <FRAMEWORK>` -Určuje [framework](../../standard/frameworks.md) k cíli.</span><span class="sxs-lookup"><span data-stu-id="0988f-304">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="0988f-305">Hodnoty: `netcoreapp2.0` pro vytvoření základní knihovny tříd rozhraní .NET nebo `netstandard2.0` vytvořit standardní knihovny tříd rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="0988f-305">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="0988f-306">Výchozí hodnota je `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="0988f-306">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="0988f-307">`--no-restore` -Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="0988f-307">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="0988f-308">**mstestu xunit**</span><span class="sxs-lookup"><span data-stu-id="0988f-308">**mstest, xunit**</span></span>

<span data-ttu-id="0988f-309">`-p|--enable-pack` – Umožňuje vytváření balíčků pro projekt pomocí [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="0988f-309">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="0988f-310">`--no-restore` -Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="0988f-310">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="0988f-311">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="0988f-311">**globaljson**</span></span>

<span data-ttu-id="0988f-312">`--sdk-version <VERSION_NUMBER>` -Určuje verzi rozhraní .NET Core SDK pro použití v *global.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="0988f-312">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="0988f-313">**web**</span><span class="sxs-lookup"><span data-stu-id="0988f-313">**web**</span></span>

<span data-ttu-id="0988f-314">`--use-launch-settings` -Zahrnuje *launchSettings.json* ve výstupu vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="0988f-314">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="0988f-315">`--no-restore` -Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="0988f-315">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="0988f-316">**webapi**</span><span class="sxs-lookup"><span data-stu-id="0988f-316">**webapi**</span></span>

<span data-ttu-id="0988f-317">`-au|--auth <AUTHENTICATION_TYPE>` -Typ ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-317">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="0988f-318">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="0988f-318">The possible values are:</span></span>

- <span data-ttu-id="0988f-319">`None` -Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="0988f-319">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="0988f-320">`IndividualB2C` -Jednotlivé ověřování s Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="0988f-320">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="0988f-321">`SingleOrg` -Organizační ověřování pro jednoho klienta.</span><span class="sxs-lookup"><span data-stu-id="0988f-321">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="0988f-322">`Windows` -Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="0988f-322">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="0988f-323">`--aad-b2c-instance <INSTANCE>` -Instance Azure Active Directory B2C se připojit k.</span><span class="sxs-lookup"><span data-stu-id="0988f-323">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="0988f-324">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-324">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="0988f-325">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="0988f-325">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="0988f-326">`-ssp|--susi-policy-id <ID>` – ID přihlášení a odhlášení zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="0988f-326">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="0988f-327">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-327">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="0988f-328">`--aad-instance <INSTANCE>` -Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="0988f-328">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="0988f-329">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-329">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="0988f-330">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="0988f-330">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="0988f-331">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="0988f-331">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="0988f-332">Použití s `IndividualB2C` nebo `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-332">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="0988f-333">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="0988f-333">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="0988f-334">`--domain <DOMAIN>` -Doména pro directory klienta.</span><span class="sxs-lookup"><span data-stu-id="0988f-334">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="0988f-335">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-335">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="0988f-336">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="0988f-336">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="0988f-337">`--tenant-id <ID>` -TenantId ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="0988f-337">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="0988f-338">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-338">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="0988f-339">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="0988f-339">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="0988f-340">`-r|--org-read-access` – Umožňuje této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="0988f-340">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="0988f-341">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-341">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="0988f-342">`--use-launch-settings` -Zahrnuje *launchSettings.json* ve výstupu vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="0988f-342">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="0988f-343">`-uld|--use-local-db` -Určuje, že místo SQLite by použít LocalDB.</span><span class="sxs-lookup"><span data-stu-id="0988f-343">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="0988f-344">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-344">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="0988f-345">`--no-restore` -Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="0988f-345">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="0988f-346">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="0988f-346">**mvc, razor**</span></span>

<span data-ttu-id="0988f-347">`-au|--auth <AUTHENTICATION_TYPE>` -Typ ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-347">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="0988f-348">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="0988f-348">The possible values are:</span></span>

- <span data-ttu-id="0988f-349">`None` -Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="0988f-349">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="0988f-350">`Individual` -Jednotlivé ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-350">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="0988f-351">`IndividualB2C` -Jednotlivé ověřování s Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="0988f-351">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="0988f-352">`SingleOrg` -Organizační ověřování pro jednoho klienta.</span><span class="sxs-lookup"><span data-stu-id="0988f-352">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="0988f-353">`MultiOrg` -Organizační ověřování pro víc klientů.</span><span class="sxs-lookup"><span data-stu-id="0988f-353">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="0988f-354">`Windows` -Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="0988f-354">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="0988f-355">`--aad-b2c-instance <INSTANCE>` -Instance Azure Active Directory B2C se připojit k.</span><span class="sxs-lookup"><span data-stu-id="0988f-355">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="0988f-356">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-356">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="0988f-357">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="0988f-357">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="0988f-358">`-ssp|--susi-policy-id <ID>` – ID přihlášení a odhlášení zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="0988f-358">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="0988f-359">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-359">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="0988f-360">`-rp|--reset-password-policy-id <ID>` -Resetování hesla ID zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="0988f-360">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="0988f-361">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-361">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="0988f-362">`-ep|--edit-profile-policy-id <ID>` -Upravit profil ID zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="0988f-362">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="0988f-363">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-363">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="0988f-364">`--aad-instance <INSTANCE>` -Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="0988f-364">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="0988f-365">Použití s `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-365">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="0988f-366">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="0988f-366">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="0988f-367">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="0988f-367">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="0988f-368">Použití s `IndividualB2C`, `SingleOrg`, nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-368">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="0988f-369">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="0988f-369">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="0988f-370">`--domain <DOMAIN>` -Doména pro directory klienta.</span><span class="sxs-lookup"><span data-stu-id="0988f-370">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="0988f-371">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-371">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="0988f-372">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="0988f-372">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="0988f-373">`--tenant-id <ID>` -TenantId ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="0988f-373">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="0988f-374">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-374">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="0988f-375">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="0988f-375">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="0988f-376">`--callback-path <PATH>` – Cesta žádosti v rámci základní cesty aplikace identifikátor URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="0988f-376">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="0988f-377">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-377">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="0988f-378">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="0988f-378">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="0988f-379">`-r|--org-read-access` – Umožňuje této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="0988f-379">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="0988f-380">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-380">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="0988f-381">`--use-launch-settings` -Zahrnuje *launchSettings.json* ve výstupu vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="0988f-381">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="0988f-382">`--use-browserlink` -Zahrnuje BrowserLink v projektu.</span><span class="sxs-lookup"><span data-stu-id="0988f-382">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="0988f-383">`-uld|--use-local-db` -Určuje, že místo SQLite by použít LocalDB.</span><span class="sxs-lookup"><span data-stu-id="0988f-383">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="0988f-384">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-384">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="0988f-385">`--no-restore` -Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="0988f-385">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="0988f-386">**Stránka**</span><span class="sxs-lookup"><span data-stu-id="0988f-386">**page**</span></span>

<span data-ttu-id="0988f-387">`-na|--namespace <NAMESPACE_NAME>`-Namespace pro generovaný kód.</span><span class="sxs-lookup"><span data-stu-id="0988f-387">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="0988f-388">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="0988f-388">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="0988f-389">`-np|--no-pagemodel` -Vytvoří danou stránku bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="0988f-389">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="0988f-390">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="0988f-390">**viewimports**</span></span>

<span data-ttu-id="0988f-391">`-na|--namespace <NAMESPACE_NAME>`-Namespace pro generovaný kód.</span><span class="sxs-lookup"><span data-stu-id="0988f-391">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="0988f-392">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="0988f-392">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="0988f-393">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="0988f-393">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="0988f-394">**konzole úhlová, reagovat, reactredux**</span><span class="sxs-lookup"><span data-stu-id="0988f-394">**console, angular, react, reactredux**</span></span>

  <span data-ttu-id="0988f-395">`--no-restore` -Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="0988f-395">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="0988f-396">**classlib**</span><span class="sxs-lookup"><span data-stu-id="0988f-396">**classlib**</span></span>

<span data-ttu-id="0988f-397">`-f|--framework <FRAMEWORK>` -Určuje [framework](../../standard/frameworks.md) k cíli.</span><span class="sxs-lookup"><span data-stu-id="0988f-397">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="0988f-398">Hodnoty: `netcoreapp2.0` pro vytvoření základní knihovny tříd rozhraní .NET nebo `netstandard2.0` vytvořit standardní knihovny tříd rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="0988f-398">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="0988f-399">Výchozí hodnota je `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="0988f-399">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="0988f-400">`--no-restore` -Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="0988f-400">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="0988f-401">**mstestu xunit**</span><span class="sxs-lookup"><span data-stu-id="0988f-401">**mstest, xunit**</span></span>

<span data-ttu-id="0988f-402">`-p|--enable-pack` – Umožňuje vytváření balíčků pro projekt pomocí [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="0988f-402">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="0988f-403">`--no-restore` -Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="0988f-403">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="0988f-404">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="0988f-404">**globaljson**</span></span>

<span data-ttu-id="0988f-405">`--sdk-version <VERSION_NUMBER>` -Určuje verzi rozhraní .NET Core SDK pro použití v *global.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="0988f-405">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="0988f-406">**web**</span><span class="sxs-lookup"><span data-stu-id="0988f-406">**web**</span></span>

<span data-ttu-id="0988f-407">`--use-launch-settings` -Zahrnuje *launchSettings.json* ve výstupu vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="0988f-407">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="0988f-408">`--no-restore` -Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="0988f-408">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="0988f-409">**webapi**</span><span class="sxs-lookup"><span data-stu-id="0988f-409">**webapi**</span></span>

<span data-ttu-id="0988f-410">`-au|--auth <AUTHENTICATION_TYPE>` -Typ ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-410">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="0988f-411">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="0988f-411">The possible values are:</span></span>

- <span data-ttu-id="0988f-412">`None` -Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="0988f-412">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="0988f-413">`IndividualB2C` -Jednotlivé ověřování s Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="0988f-413">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="0988f-414">`SingleOrg` -Organizační ověřování pro jednoho klienta.</span><span class="sxs-lookup"><span data-stu-id="0988f-414">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="0988f-415">`Windows` -Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="0988f-415">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="0988f-416">`--aad-b2c-instance <INSTANCE>` -Instance Azure Active Directory B2C se připojit k.</span><span class="sxs-lookup"><span data-stu-id="0988f-416">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="0988f-417">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-417">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="0988f-418">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="0988f-418">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="0988f-419">`-ssp|--susi-policy-id <ID>` – ID přihlášení a odhlášení zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="0988f-419">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="0988f-420">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-420">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="0988f-421">`--aad-instance <INSTANCE>` -Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="0988f-421">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="0988f-422">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-422">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="0988f-423">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="0988f-423">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="0988f-424">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="0988f-424">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="0988f-425">Použití s `IndividualB2C` nebo `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-425">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="0988f-426">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="0988f-426">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="0988f-427">`--domain <DOMAIN>` -Doména pro directory klienta.</span><span class="sxs-lookup"><span data-stu-id="0988f-427">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="0988f-428">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-428">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="0988f-429">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="0988f-429">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="0988f-430">`--tenant-id <ID>` -TenantId ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="0988f-430">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="0988f-431">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-431">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="0988f-432">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="0988f-432">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="0988f-433">`-r|--org-read-access` – Umožňuje této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="0988f-433">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="0988f-434">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-434">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="0988f-435">`--use-launch-settings` -Zahrnuje *launchSettings.json* ve výstupu vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="0988f-435">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="0988f-436">`-uld|--use-local-db` -Určuje, že místo SQLite by použít LocalDB.</span><span class="sxs-lookup"><span data-stu-id="0988f-436">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="0988f-437">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-437">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="0988f-438">`--no-restore` -Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="0988f-438">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="0988f-439">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="0988f-439">**mvc, razor**</span></span>

<span data-ttu-id="0988f-440">`-au|--auth <AUTHENTICATION_TYPE>` -Typ ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-440">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="0988f-441">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="0988f-441">The possible values are:</span></span>

- <span data-ttu-id="0988f-442">`None` -Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="0988f-442">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="0988f-443">`Individual` -Jednotlivé ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-443">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="0988f-444">`IndividualB2C` -Jednotlivé ověřování s Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="0988f-444">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="0988f-445">`SingleOrg` -Organizační ověřování pro jednoho klienta.</span><span class="sxs-lookup"><span data-stu-id="0988f-445">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="0988f-446">`MultiOrg` -Organizační ověřování pro víc klientů.</span><span class="sxs-lookup"><span data-stu-id="0988f-446">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="0988f-447">`Windows` -Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="0988f-447">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="0988f-448">`--aad-b2c-instance <INSTANCE>` -Instance Azure Active Directory B2C se připojit k.</span><span class="sxs-lookup"><span data-stu-id="0988f-448">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="0988f-449">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-449">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="0988f-450">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="0988f-450">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="0988f-451">`-ssp|--susi-policy-id <ID>` – ID přihlášení a odhlášení zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="0988f-451">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="0988f-452">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-452">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="0988f-453">`-rp|--reset-password-policy-id <ID>` -Resetování hesla ID zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="0988f-453">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="0988f-454">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-454">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="0988f-455">`-ep|--edit-profile-policy-id <ID>` -Upravit profil ID zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="0988f-455">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="0988f-456">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-456">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="0988f-457">`--aad-instance <INSTANCE>` -Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="0988f-457">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="0988f-458">Použití s `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-458">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="0988f-459">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="0988f-459">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="0988f-460">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="0988f-460">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="0988f-461">Použití s `IndividualB2C`, `SingleOrg`, nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-461">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="0988f-462">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="0988f-462">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="0988f-463">`--domain <DOMAIN>` -Doména pro directory klienta.</span><span class="sxs-lookup"><span data-stu-id="0988f-463">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="0988f-464">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-464">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="0988f-465">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="0988f-465">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="0988f-466">`--tenant-id <ID>` -TenantId ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="0988f-466">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="0988f-467">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-467">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="0988f-468">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="0988f-468">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="0988f-469">`--callback-path <PATH>` – Cesta žádosti v rámci základní cesty aplikace identifikátor URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="0988f-469">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="0988f-470">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-470">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="0988f-471">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="0988f-471">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="0988f-472">`-r|--org-read-access` – Umožňuje této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="0988f-472">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="0988f-473">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-473">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="0988f-474">`--use-launch-settings` -Zahrnuje *launchSettings.json* ve výstupu vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="0988f-474">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="0988f-475">`--use-browserlink` -Zahrnuje BrowserLink v projektu.</span><span class="sxs-lookup"><span data-stu-id="0988f-475">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="0988f-476">`-uld|--use-local-db` -Určuje, že místo SQLite by použít LocalDB.</span><span class="sxs-lookup"><span data-stu-id="0988f-476">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="0988f-477">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-477">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="0988f-478">`--no-restore` -Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="0988f-478">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="0988f-479">**Stránka**</span><span class="sxs-lookup"><span data-stu-id="0988f-479">**page**</span></span>

<span data-ttu-id="0988f-480">`-na|--namespace <NAMESPACE_NAME>`-Namespace pro generovaný kód.</span><span class="sxs-lookup"><span data-stu-id="0988f-480">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="0988f-481">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="0988f-481">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="0988f-482">`-np|--no-pagemodel` -Vytvoří danou stránku bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="0988f-482">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="0988f-483">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="0988f-483">**viewimports**</span></span>

<span data-ttu-id="0988f-484">`-na|--namespace <NAMESPACE_NAME>`-Namespace pro generovaný kód.</span><span class="sxs-lookup"><span data-stu-id="0988f-484">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="0988f-485">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="0988f-485">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0988f-486">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="0988f-486">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="0988f-487">**konzola, xunit, mstestu, web, webapi**</span><span class="sxs-lookup"><span data-stu-id="0988f-487">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="0988f-488">`-f|--framework` -Určuje [framework](../../standard/frameworks.md) k cíli.</span><span class="sxs-lookup"><span data-stu-id="0988f-488">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="0988f-489">Hodnoty: `netcoreapp1.0` nebo `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="0988f-489">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="0988f-490">Výchozí hodnota je `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="0988f-490">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="0988f-491">**classlib**</span><span class="sxs-lookup"><span data-stu-id="0988f-491">**classlib**</span></span>

<span data-ttu-id="0988f-492">`-f|--framework` -Určuje [framework](../../standard/frameworks.md) k cíli.</span><span class="sxs-lookup"><span data-stu-id="0988f-492">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="0988f-493">Hodnoty: `netcoreapp1.0`, `netcoreapp1.1`, nebo `netstandard1.0` k `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="0988f-493">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="0988f-494">Výchozí hodnota je `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="0988f-494">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="0988f-495">**mvc**</span><span class="sxs-lookup"><span data-stu-id="0988f-495">**mvc**</span></span>

<span data-ttu-id="0988f-496">`-f|--framework` -Určuje [framework](../../standard/frameworks.md) k cíli.</span><span class="sxs-lookup"><span data-stu-id="0988f-496">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="0988f-497">Hodnoty: `netcoreapp1.0` nebo `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="0988f-497">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="0988f-498">Výchozí hodnota je `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="0988f-498">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="0988f-499">`-au|--auth` -Typ ověřování.</span><span class="sxs-lookup"><span data-stu-id="0988f-499">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="0988f-500">Hodnoty: `None` nebo `Individual`.</span><span class="sxs-lookup"><span data-stu-id="0988f-500">Values: `None` or `Individual`.</span></span> <span data-ttu-id="0988f-501">Výchozí hodnota je `None`.</span><span class="sxs-lookup"><span data-stu-id="0988f-501">The default value is `None`.</span></span>

<span data-ttu-id="0988f-502">`-uld|--use-local-db` -Určuje, zda pro použití LocalDB místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="0988f-502">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="0988f-503">Hodnoty: `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="0988f-503">Values: `true` or `false`.</span></span> <span data-ttu-id="0988f-504">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="0988f-504">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="0988f-505">Příklady</span><span class="sxs-lookup"><span data-stu-id="0988f-505">Examples</span></span>

<span data-ttu-id="0988f-506">Vytvoření projektu aplikace konzoly F # v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="0988f-506">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="0988f-507">Vytvořte standardní rozhraní .NET projektu knihovny tříd v zadaný adresář (dostupné pouze s .NET Core SDK 2.0 nebo novější verze):</span><span class="sxs-lookup"><span data-stu-id="0988f-507">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="0988f-508">Vytvořte nový projekt aplikace ASP.NET Core C# MVC v aktuálním adresáři bez jakéhokoli ověřování:</span><span class="sxs-lookup"><span data-stu-id="0988f-508">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="0988f-509">Vytvoření nové aplikace xUnit:</span><span class="sxs-lookup"><span data-stu-id="0988f-509">Create a new xUnit application:</span></span>

`dotnet new xunit`

<span data-ttu-id="0988f-510">Seznam všech šablon, které jsou k dispozici pro MVC:</span><span class="sxs-lookup"><span data-stu-id="0988f-510">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="0988f-511">Instalace verze 2.0 šablon jedné stránky aplikace ASP.NET Core (příkaz možnost k dispozici pro .NET Core SDK 1.1 a pouze novější verze):</span><span class="sxs-lookup"><span data-stu-id="0988f-511">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="0988f-512">Vytvoření *global.json* v aktuálním adresáři nastavení verze sady SDK na 2.0.0 (dostupné pouze s .NET Core SDK 2.0 nebo novější verze):</span><span class="sxs-lookup"><span data-stu-id="0988f-512">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="0988f-513">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0988f-513">See also</span></span>

[<span data-ttu-id="0988f-514">Vlastní šablony pro nové dotnet.</span><span class="sxs-lookup"><span data-stu-id="0988f-514">Custom templates for dotnet new</span></span>](custom-templates.md)  
[<span data-ttu-id="0988f-515">Vytvoření vlastní šablony pro dotnet new</span><span class="sxs-lookup"><span data-stu-id="0988f-515">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
[<span data-ttu-id="0988f-516">úložiště GitHub DotNet/dotnet šablony – ukázky</span><span class="sxs-lookup"><span data-stu-id="0988f-516">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
[<span data-ttu-id="0988f-517">Dostupné šablony pro nové dotnet.</span><span class="sxs-lookup"><span data-stu-id="0988f-517">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
