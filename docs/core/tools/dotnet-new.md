---
title: nový příkaz DotNet - .NET Core rozhraní příkazového řádku
description: Nový příkaz dotnet vytvoří nové projekty .NET Core na základě zadané šablony.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: ae24c4145cc67ca863c07e4d22af8a1c2c2dd732
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34570460"
---
# <a name="dotnet-new"></a><span data-ttu-id="59b78-103">nové DotNet.</span><span class="sxs-lookup"><span data-stu-id="59b78-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="59b78-104">Název</span><span class="sxs-lookup"><span data-stu-id="59b78-104">Name</span></span>

<span data-ttu-id="59b78-105">`dotnet new` -Vytvoří nový projekt, konfigurační soubor nebo řešení v závislosti na určené šablony.</span><span class="sxs-lookup"><span data-stu-id="59b78-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="59b78-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="59b78-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="59b78-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="59b78-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output]
    [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="59b78-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="59b78-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="59b78-109">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="59b78-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="59b78-110">Popis</span><span class="sxs-lookup"><span data-stu-id="59b78-110">Description</span></span>

<span data-ttu-id="59b78-111">`dotnet new` Příkaz nabízí pohodlný způsob, jak inicializovat platný projekt .NET Core.</span><span class="sxs-lookup"><span data-stu-id="59b78-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="59b78-112">Příkaz volání [modulu šablon](https://github.com/dotnet/templating) vytvořit artefakty na disku na základě určené šablony a možnosti.</span><span class="sxs-lookup"><span data-stu-id="59b78-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="59b78-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="59b78-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="59b78-114">Šablona pro vytvoření instance při vyvolání příkazu.</span><span class="sxs-lookup"><span data-stu-id="59b78-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="59b78-115">Každá šablona může mít specifické možnosti, které lze předat.</span><span class="sxs-lookup"><span data-stu-id="59b78-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="59b78-116">Další informace najdete v tématu [možnosti šablony](#template-options).</span><span class="sxs-lookup"><span data-stu-id="59b78-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="59b78-117">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="59b78-117">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="59b78-118">Příkaz obsahuje seznam výchozích šablon.</span><span class="sxs-lookup"><span data-stu-id="59b78-118">The command contains a default list of templates.</span></span> <span data-ttu-id="59b78-119">Použití `dotnet new -l` získat seznam dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="59b78-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="59b78-120">V následující tabulce jsou uvedeny šablony, které jsou předinstalované .NET Core SDK 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="59b78-120">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="59b78-121">Výchozí jazyk pro šablonu se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="59b78-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="59b78-122">Popis šablony</span><span class="sxs-lookup"><span data-stu-id="59b78-122">Template description</span></span>                          | <span data-ttu-id="59b78-123">Název šablony</span><span class="sxs-lookup"><span data-stu-id="59b78-123">Template name</span></span>   | <span data-ttu-id="59b78-124">Jazyky</span><span class="sxs-lookup"><span data-stu-id="59b78-124">Languages</span></span>     |
|----------------------------------------------|-----------------|---------------|
| <span data-ttu-id="59b78-125">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="59b78-125">Console application</span></span>                          | `console`       | <span data-ttu-id="59b78-126">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="59b78-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="59b78-127">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="59b78-127">Class library</span></span>                                | `classlib`      | <span data-ttu-id="59b78-128">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="59b78-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="59b78-129">Projektu testování částí</span><span class="sxs-lookup"><span data-stu-id="59b78-129">Unit test project</span></span>                            | `mstest`        | <span data-ttu-id="59b78-130">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="59b78-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="59b78-131">xUnit testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="59b78-131">xUnit test project</span></span>                           | `xunit`         | <span data-ttu-id="59b78-132">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="59b78-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="59b78-133">Stránky Razor</span><span class="sxs-lookup"><span data-stu-id="59b78-133">Razor page</span></span>                                   | `page`          | <span data-ttu-id="59b78-134">[C#]</span><span class="sxs-lookup"><span data-stu-id="59b78-134">[C#]</span></span>          |
| <span data-ttu-id="59b78-135">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="59b78-135">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="59b78-136">[C#]</span><span class="sxs-lookup"><span data-stu-id="59b78-136">[C#]</span></span>          |
| <span data-ttu-id="59b78-137">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="59b78-137">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="59b78-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="59b78-138">[C#]</span></span>          |
| <span data-ttu-id="59b78-139">ASP.NET Core prázdný</span><span class="sxs-lookup"><span data-stu-id="59b78-139">ASP.NET Core empty</span></span>                           | `web`           | <span data-ttu-id="59b78-140">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="59b78-140">[C#], F#</span></span>      |
| <span data-ttu-id="59b78-141">Webové aplikace ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="59b78-141">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="59b78-142">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="59b78-142">[C#], F#</span></span>      |
| <span data-ttu-id="59b78-143">Webové aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="59b78-143">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="59b78-144">[C#]</span><span class="sxs-lookup"><span data-stu-id="59b78-144">[C#]</span></span>          |
| <span data-ttu-id="59b78-145">ASP.NET Core s úhlová</span><span class="sxs-lookup"><span data-stu-id="59b78-145">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="59b78-146">[C#]</span><span class="sxs-lookup"><span data-stu-id="59b78-146">[C#]</span></span>          |
| <span data-ttu-id="59b78-147">ASP.NET Core s React.js</span><span class="sxs-lookup"><span data-stu-id="59b78-147">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="59b78-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="59b78-148">[C#]</span></span>          |
| <span data-ttu-id="59b78-149">ASP.NET Core s React.js a – obnovení</span><span class="sxs-lookup"><span data-stu-id="59b78-149">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="59b78-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="59b78-150">[C#]</span></span>          |
| <span data-ttu-id="59b78-151">Jádro ASP.NET Web API</span><span class="sxs-lookup"><span data-stu-id="59b78-151">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="59b78-152">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="59b78-152">[C#], F#</span></span>      |
| <span data-ttu-id="59b78-153">Knihovna tříd Razor</span><span class="sxs-lookup"><span data-stu-id="59b78-153">Razor class library</span></span>                          | `razorclasslib` | <span data-ttu-id="59b78-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="59b78-154">[C#]</span></span>          |
| <span data-ttu-id="59b78-155">soubor Global.JSON</span><span class="sxs-lookup"><span data-stu-id="59b78-155">global.json file</span></span>                             | `globaljson`    |               |
| <span data-ttu-id="59b78-156">Konfigurace NuGet</span><span class="sxs-lookup"><span data-stu-id="59b78-156">NuGet config</span></span>                                 | `nugetconfig`   |               |
| <span data-ttu-id="59b78-157">Webové konfigurace</span><span class="sxs-lookup"><span data-stu-id="59b78-157">Web config</span></span>                                   | `webconfig`     |               |
| <span data-ttu-id="59b78-158">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="59b78-158">Solution file</span></span>                                | `sln`           |               |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="59b78-159">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="59b78-159">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="59b78-160">Příkaz obsahuje seznam výchozích šablon.</span><span class="sxs-lookup"><span data-stu-id="59b78-160">The command contains a default list of templates.</span></span> <span data-ttu-id="59b78-161">Použití `dotnet new -l` získat seznam dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="59b78-161">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="59b78-162">V následující tabulce jsou uvedeny šablony, které jsou předinstalované .NET Core SDK 2.0.</span><span class="sxs-lookup"><span data-stu-id="59b78-162">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.</span></span> <span data-ttu-id="59b78-163">Výchozí jazyk pro šablonu se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="59b78-163">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="59b78-164">Popis šablony</span><span class="sxs-lookup"><span data-stu-id="59b78-164">Template description</span></span>                          | <span data-ttu-id="59b78-165">Název šablony</span><span class="sxs-lookup"><span data-stu-id="59b78-165">Template name</span></span> | <span data-ttu-id="59b78-166">Jazyky</span><span class="sxs-lookup"><span data-stu-id="59b78-166">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="59b78-167">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="59b78-167">Console application</span></span>                          | `console`     | <span data-ttu-id="59b78-168">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="59b78-168">[C#], F#, VB</span></span>  |
| <span data-ttu-id="59b78-169">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="59b78-169">Class library</span></span>                                | `classlib`    | <span data-ttu-id="59b78-170">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="59b78-170">[C#], F#, VB</span></span>  |
| <span data-ttu-id="59b78-171">Projektu testování částí</span><span class="sxs-lookup"><span data-stu-id="59b78-171">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="59b78-172">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="59b78-172">[C#], F#, VB</span></span>  |
| <span data-ttu-id="59b78-173">xUnit testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="59b78-173">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="59b78-174">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="59b78-174">[C#], F#, VB</span></span>  |
| <span data-ttu-id="59b78-175">ASP.NET Core prázdný</span><span class="sxs-lookup"><span data-stu-id="59b78-175">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="59b78-176">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="59b78-176">[C#], F#</span></span>      |
| <span data-ttu-id="59b78-177">Webové aplikace ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="59b78-177">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="59b78-178">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="59b78-178">[C#], F#</span></span>      |
| <span data-ttu-id="59b78-179">Webové aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="59b78-179">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="59b78-180">[C#]</span><span class="sxs-lookup"><span data-stu-id="59b78-180">[C#]</span></span>          |
| <span data-ttu-id="59b78-181">ASP.NET Core s úhlová</span><span class="sxs-lookup"><span data-stu-id="59b78-181">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="59b78-182">[C#]</span><span class="sxs-lookup"><span data-stu-id="59b78-182">[C#]</span></span>          |
| <span data-ttu-id="59b78-183">ASP.NET Core s React.js</span><span class="sxs-lookup"><span data-stu-id="59b78-183">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="59b78-184">[C#]</span><span class="sxs-lookup"><span data-stu-id="59b78-184">[C#]</span></span>          |
| <span data-ttu-id="59b78-185">ASP.NET Core s React.js a – obnovení</span><span class="sxs-lookup"><span data-stu-id="59b78-185">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="59b78-186">[C#]</span><span class="sxs-lookup"><span data-stu-id="59b78-186">[C#]</span></span>          |
| <span data-ttu-id="59b78-187">Jádro ASP.NET Web API</span><span class="sxs-lookup"><span data-stu-id="59b78-187">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="59b78-188">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="59b78-188">[C#], F#</span></span>      |
| <span data-ttu-id="59b78-189">soubor Global.JSON</span><span class="sxs-lookup"><span data-stu-id="59b78-189">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="59b78-190">Konfigurace NuGet</span><span class="sxs-lookup"><span data-stu-id="59b78-190">NuGet config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="59b78-191">Webové konfigurace</span><span class="sxs-lookup"><span data-stu-id="59b78-191">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="59b78-192">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="59b78-192">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="59b78-193">Stránky Razor</span><span class="sxs-lookup"><span data-stu-id="59b78-193">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="59b78-194">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="59b78-194">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="59b78-195">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="59b78-195">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="59b78-196">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="59b78-196">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="59b78-197">Příkaz obsahuje seznam výchozích šablon.</span><span class="sxs-lookup"><span data-stu-id="59b78-197">The command contains a default list of templates.</span></span> <span data-ttu-id="59b78-198">Použití `dotnet new -all` získat seznam dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="59b78-198">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="59b78-199">V následující tabulce jsou uvedeny šablony, které jsou předinstalované .NET Core SDK 1.x.</span><span class="sxs-lookup"><span data-stu-id="59b78-199">The following table shows the templates that come pre-installed with the .NET Core SDK 1.x.</span></span> <span data-ttu-id="59b78-200">Výchozí jazyk pro šablonu se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="59b78-200">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="59b78-201">Popis šablony</span><span class="sxs-lookup"><span data-stu-id="59b78-201">Template description</span></span>  | <span data-ttu-id="59b78-202">Název šablony</span><span class="sxs-lookup"><span data-stu-id="59b78-202">Template name</span></span> | <span data-ttu-id="59b78-203">Jazyky</span><span class="sxs-lookup"><span data-stu-id="59b78-203">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="59b78-204">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="59b78-204">Console application</span></span>  | `console`     | <span data-ttu-id="59b78-205">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="59b78-205">[C#], F#</span></span>  |
| <span data-ttu-id="59b78-206">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="59b78-206">Class library</span></span>        | `classlib`    | <span data-ttu-id="59b78-207">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="59b78-207">[C#], F#</span></span>  |
| <span data-ttu-id="59b78-208">Projektu testování částí</span><span class="sxs-lookup"><span data-stu-id="59b78-208">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="59b78-209">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="59b78-209">[C#], F#</span></span>  |
| <span data-ttu-id="59b78-210">xUnit testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="59b78-210">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="59b78-211">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="59b78-211">[C#], F#</span></span>  |
| <span data-ttu-id="59b78-212">ASP.NET Core prázdný</span><span class="sxs-lookup"><span data-stu-id="59b78-212">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="59b78-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="59b78-213">[C#]</span></span>      |
| <span data-ttu-id="59b78-214">Webové aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="59b78-214">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="59b78-215">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="59b78-215">[C#], F#</span></span>  |
| <span data-ttu-id="59b78-216">Jádro ASP.NET Web API</span><span class="sxs-lookup"><span data-stu-id="59b78-216">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="59b78-217">[C#]</span><span class="sxs-lookup"><span data-stu-id="59b78-217">[C#]</span></span>      |
| <span data-ttu-id="59b78-218">Konfigurace NuGet</span><span class="sxs-lookup"><span data-stu-id="59b78-218">NuGet config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="59b78-219">Webové konfigurace</span><span class="sxs-lookup"><span data-stu-id="59b78-219">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="59b78-220">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="59b78-220">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="59b78-221">Možnosti</span><span class="sxs-lookup"><span data-stu-id="59b78-221">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="59b78-222">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="59b78-222">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="59b78-223">Vynutí obsah má být vygenerován i v případě, že se změní stávající soubory.</span><span class="sxs-lookup"><span data-stu-id="59b78-223">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="59b78-224">To je potřeba, když výstupnímu adresáři již obsahuje projektu.</span><span class="sxs-lookup"><span data-stu-id="59b78-224">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="59b78-225">Vytiskne nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="59b78-225">Prints out help for the command.</span></span> <span data-ttu-id="59b78-226">Nelze vyvolat pro `dotnet new` příkaz sám sebe nebo pro všechny šablony, jako například `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="59b78-226">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="59b78-227">Nainstaluje sadu zdroje nebo šablony z `PATH` nebo `NUGET_ID` zadat.</span><span class="sxs-lookup"><span data-stu-id="59b78-227">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="59b78-228">Pokud chcete nainstalovat zkušební verzi balíčku šablony, je třeba zadat ve formátu verze `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="59b78-228">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="59b78-229">Ve výchozím nastavení `dotnet new` předá \* pro verzi, která představuje poslední stabilní balíčku verze.</span><span class="sxs-lookup"><span data-stu-id="59b78-229">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="59b78-230">Prohlédněte si příklad na [příklady](#examples) části.</span><span class="sxs-lookup"><span data-stu-id="59b78-230">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="59b78-231">Informace o vytváření vlastních šablon najdete v tématu [vlastních šablon pro dotnet nové](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="59b78-231">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="59b78-232">Obsahuje seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="59b78-232">Lists templates containing the specified name.</span></span> <span data-ttu-id="59b78-233">Pokud je vyvolána pro `dotnet new` příkaz, zobrazí seznam možných šablony, které jsou k dispozici pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="59b78-233">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="59b78-234">Například pokud adresář již obsahuje projekt, nepodporuje zobrazí seznam všech šablon projektu.</span><span class="sxs-lookup"><span data-stu-id="59b78-234">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="59b78-235">Jazyk šablonu, kterou chcete vytvořit.</span><span class="sxs-lookup"><span data-stu-id="59b78-235">The language of the template to create.</span></span> <span data-ttu-id="59b78-236">Jazyk přijata, se liší podle šablony (viz výchozí hodnoty v [argumenty](#arguments) části).</span><span class="sxs-lookup"><span data-stu-id="59b78-236">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="59b78-237">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="59b78-237">Not valid for some templates.</span></span>

    > [!NOTE]
    > Some shells interpret `#` as a special character. In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="59b78-238">Název pro vytvoření výstupu.</span><span class="sxs-lookup"><span data-stu-id="59b78-238">The name for the created output.</span></span> <span data-ttu-id="59b78-239">Pokud není zadán žádný název, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="59b78-239">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="59b78-240">Určuje zdroj NuGet, který chcete použít během instalace.</span><span class="sxs-lookup"><span data-stu-id="59b78-240">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="59b78-241">Umístění pro generovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="59b78-241">Location to place the generated output.</span></span> <span data-ttu-id="59b78-242">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="59b78-242">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="59b78-243">Filtry šablony vycházející z dostupných typů.</span><span class="sxs-lookup"><span data-stu-id="59b78-243">Filters templates based on available types.</span></span> <span data-ttu-id="59b78-244">Předdefinované hodnoty jsou "projektu", "položka" nebo "ostatní".</span><span class="sxs-lookup"><span data-stu-id="59b78-244">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="59b78-245">Odinstaluje sadu zdroje nebo šablony v `PATH` nebo `NUGET_ID` zadat.</span><span class="sxs-lookup"><span data-stu-id="59b78-245">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="59b78-246">Chcete-li odinstalovat šablony pomocí `PATH`, budete muset plně kvalifikovanou cestu.</span><span class="sxs-lookup"><span data-stu-id="59b78-246">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="59b78-247">Například *C: či uživatelů nebo\<uživatele > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z obsahující složka se není.</span><span class="sxs-lookup"><span data-stu-id="59b78-247">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="59b78-248">Kromě toho nezahrnují konečné ukončující lomítko adresáře na cestu k šabloně.</span><span class="sxs-lookup"><span data-stu-id="59b78-248">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="59b78-249">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="59b78-249">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="59b78-250">Vynutí obsah má být vygenerován i v případě, že se změní stávající soubory.</span><span class="sxs-lookup"><span data-stu-id="59b78-250">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="59b78-251">To je potřeba, když výstupnímu adresáři již obsahuje projektu.</span><span class="sxs-lookup"><span data-stu-id="59b78-251">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="59b78-252">Vytiskne nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="59b78-252">Prints out help for the command.</span></span> <span data-ttu-id="59b78-253">Nelze vyvolat pro `dotnet new` příkaz sám sebe nebo pro všechny šablony, jako například `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="59b78-253">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="59b78-254">Nainstaluje sadu zdroje nebo šablony z `PATH` nebo `NUGET_ID` zadat.</span><span class="sxs-lookup"><span data-stu-id="59b78-254">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="59b78-255">Pokud chcete nainstalovat zkušební verzi balíčku šablony, je třeba zadat ve formátu verze `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="59b78-255">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="59b78-256">Ve výchozím nastavení `dotnet new` předá \* pro verzi, která představuje poslední stabilní balíčku verze.</span><span class="sxs-lookup"><span data-stu-id="59b78-256">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="59b78-257">Prohlédněte si příklad na [příklady](#examples) části.</span><span class="sxs-lookup"><span data-stu-id="59b78-257">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="59b78-258">Informace o vytváření vlastních šablon najdete v tématu [vlastních šablon pro dotnet nové](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="59b78-258">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="59b78-259">Obsahuje seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="59b78-259">Lists templates containing the specified name.</span></span> <span data-ttu-id="59b78-260">Pokud je vyvolána pro `dotnet new` příkaz, zobrazí seznam možných šablony, které jsou k dispozici pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="59b78-260">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="59b78-261">Například pokud adresář již obsahuje projekt, nepodporuje zobrazí seznam všech šablon projektu.</span><span class="sxs-lookup"><span data-stu-id="59b78-261">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="59b78-262">Jazyk šablonu, kterou chcete vytvořit.</span><span class="sxs-lookup"><span data-stu-id="59b78-262">The language of the template to create.</span></span> <span data-ttu-id="59b78-263">Jazyk přijata, se liší podle šablony (viz výchozí hodnoty v [argumenty](#arguments) části).</span><span class="sxs-lookup"><span data-stu-id="59b78-263">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="59b78-264">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="59b78-264">Not valid for some templates.</span></span>

    > [!NOTE]
    > Some shells interpret `#` as a special character. In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="59b78-265">Název pro vytvoření výstupu.</span><span class="sxs-lookup"><span data-stu-id="59b78-265">The name for the created output.</span></span> <span data-ttu-id="59b78-266">Pokud není zadán žádný název, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="59b78-266">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="59b78-267">Umístění pro generovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="59b78-267">Location to place the generated output.</span></span> <span data-ttu-id="59b78-268">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="59b78-268">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="59b78-269">Filtry šablony vycházející z dostupných typů.</span><span class="sxs-lookup"><span data-stu-id="59b78-269">Filters templates based on available types.</span></span> <span data-ttu-id="59b78-270">Předdefinované hodnoty jsou "projektu", "položka" nebo "ostatní".</span><span class="sxs-lookup"><span data-stu-id="59b78-270">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="59b78-271">Odinstaluje sadu zdroje nebo šablony v `PATH` nebo `NUGET_ID` zadat.</span><span class="sxs-lookup"><span data-stu-id="59b78-271">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="59b78-272">Chcete-li odinstalovat šablony pomocí `PATH`, budete muset plně kvalifikovanou cestu.</span><span class="sxs-lookup"><span data-stu-id="59b78-272">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="59b78-273">Například *C: či uživatelů nebo\<uživatele > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z obsahující složka se není.</span><span class="sxs-lookup"><span data-stu-id="59b78-273">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="59b78-274">Kromě toho nezahrnují konečné ukončující lomítko adresáře na cestu k šabloně.</span><span class="sxs-lookup"><span data-stu-id="59b78-274">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="59b78-275">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="59b78-275">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="59b78-276">Při spuštění v kontextu jsou uvedeny všechny šablony pro konkrétní typ projektu `dotnet new` příkaz samostatně.</span><span class="sxs-lookup"><span data-stu-id="59b78-276">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="59b78-277">Při spuštění v rámci konkrétní šablonu, jako například `dotnet new web -all`, `-all` interpretována jako vytvoření příznak force.</span><span class="sxs-lookup"><span data-stu-id="59b78-277">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="59b78-278">To je potřeba, když výstupnímu adresáři již obsahuje projektu.</span><span class="sxs-lookup"><span data-stu-id="59b78-278">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="59b78-279">Vytiskne nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="59b78-279">Prints out help for the command.</span></span> <span data-ttu-id="59b78-280">Nelze vyvolat pro `dotnet new` příkaz sám sebe nebo pro všechny šablony, jako například `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="59b78-280">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="59b78-281">Obsahuje seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="59b78-281">Lists templates containing the specified name.</span></span> <span data-ttu-id="59b78-282">Pokud je vyvolána pro `dotnet new` příkaz, zobrazí seznam možných šablony, které jsou k dispozici pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="59b78-282">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="59b78-283">Například pokud adresář již obsahuje projekt, nepodporuje zobrazí seznam všech šablon projektu.</span><span class="sxs-lookup"><span data-stu-id="59b78-283">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="59b78-284">Jazyk šablonu, kterou chcete vytvořit.</span><span class="sxs-lookup"><span data-stu-id="59b78-284">The language of the template to create.</span></span> <span data-ttu-id="59b78-285">Jazyk přijata, se liší podle šablony (viz výchozí hodnoty v [argumenty](#arguments) části).</span><span class="sxs-lookup"><span data-stu-id="59b78-285">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="59b78-286">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="59b78-286">Not valid for some templates.</span></span>

    > [!NOTE]
    > Some shells interpret `#` as a special character. In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="59b78-287">Název pro vytvoření výstupu.</span><span class="sxs-lookup"><span data-stu-id="59b78-287">The name for the created output.</span></span> <span data-ttu-id="59b78-288">Pokud není zadán žádný název, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="59b78-288">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="59b78-289">Umístění pro generovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="59b78-289">Location to place the generated output.</span></span> <span data-ttu-id="59b78-290">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="59b78-290">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="59b78-291">Možnosti šablony</span><span class="sxs-lookup"><span data-stu-id="59b78-291">Template options</span></span>

<span data-ttu-id="59b78-292">Každá šablona projektu může mít další možnosti, které jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="59b78-292">Each project template may have additional options available.</span></span> <span data-ttu-id="59b78-293">Základní šablony mají následující možnosti:</span><span class="sxs-lookup"><span data-stu-id="59b78-293">The core templates have the following additional options:</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="59b78-294">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="59b78-294">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="59b78-295">**konzole úhlová, reagují, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="59b78-295">**console, angular, react, reactredux, razorclasslib**</span></span>

  <span data-ttu-id="59b78-296">`--no-restore` -Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="59b78-296">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="59b78-297">**classlib**</span><span class="sxs-lookup"><span data-stu-id="59b78-297">**classlib**</span></span>

<span data-ttu-id="59b78-298">`-f|--framework <FRAMEWORK>` -Určuje [framework](../../standard/frameworks.md) k cíli.</span><span class="sxs-lookup"><span data-stu-id="59b78-298">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="59b78-299">Hodnoty: `netcoreapp2.0` pro vytvoření základní knihovny tříd rozhraní .NET nebo `netstandard2.0` vytvořit standardní knihovny tříd rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="59b78-299">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="59b78-300">Výchozí hodnota je `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="59b78-300">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="59b78-301">`--no-restore` -Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="59b78-301">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="59b78-302">**mstestu xunit**</span><span class="sxs-lookup"><span data-stu-id="59b78-302">**mstest, xunit**</span></span>

<span data-ttu-id="59b78-303">`-p|--enable-pack` – Umožňuje vytváření balíčků pro projekt pomocí [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="59b78-303">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="59b78-304">`--no-restore` -Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="59b78-304">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="59b78-305">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="59b78-305">**globaljson**</span></span>

<span data-ttu-id="59b78-306">`--sdk-version <VERSION_NUMBER>` -Určuje verzi rozhraní .NET Core SDK pro použití v *global.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="59b78-306">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="59b78-307">**web**</span><span class="sxs-lookup"><span data-stu-id="59b78-307">**web**</span></span>

<span data-ttu-id="59b78-308">`--use-launch-settings` -Zahrnuje *launchSettings.json* ve výstupu vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="59b78-308">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="59b78-309">`--no-restore` -Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="59b78-309">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="59b78-310">**webapi**</span><span class="sxs-lookup"><span data-stu-id="59b78-310">**webapi**</span></span>

<span data-ttu-id="59b78-311">`-au|--auth <AUTHENTICATION_TYPE>` -Typ ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-311">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="59b78-312">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="59b78-312">The possible values are:</span></span>

- <span data-ttu-id="59b78-313">`None` -Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="59b78-313">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="59b78-314">`IndividualB2C` -Jednotlivé ověřování s Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="59b78-314">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="59b78-315">`SingleOrg` -Organizační ověřování pro jednoho klienta.</span><span class="sxs-lookup"><span data-stu-id="59b78-315">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="59b78-316">`Windows` -Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="59b78-316">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="59b78-317">`--aad-b2c-instance <INSTANCE>` -Instance Azure Active Directory B2C se připojit k.</span><span class="sxs-lookup"><span data-stu-id="59b78-317">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="59b78-318">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-318">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="59b78-319">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="59b78-319">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="59b78-320">`-ssp|--susi-policy-id <ID>` – ID přihlášení a odhlášení zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="59b78-320">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="59b78-321">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-321">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="59b78-322">`--aad-instance <INSTANCE>` -Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="59b78-322">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="59b78-323">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-323">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="59b78-324">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="59b78-324">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="59b78-325">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="59b78-325">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="59b78-326">Použití s `IndividualB2C` nebo `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-326">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="59b78-327">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="59b78-327">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="59b78-328">`--domain <DOMAIN>` -Doména pro directory klienta.</span><span class="sxs-lookup"><span data-stu-id="59b78-328">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="59b78-329">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-329">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="59b78-330">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="59b78-330">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="59b78-331">`--tenant-id <ID>` -TenantId ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="59b78-331">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="59b78-332">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-332">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="59b78-333">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="59b78-333">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="59b78-334">`-r|--org-read-access` – Umožňuje této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="59b78-334">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="59b78-335">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-335">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="59b78-336">`--use-launch-settings` -Zahrnuje *launchSettings.json* ve výstupu vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="59b78-336">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="59b78-337">`-uld|--use-local-db` -Určuje, že místo SQLite by použít LocalDB.</span><span class="sxs-lookup"><span data-stu-id="59b78-337">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="59b78-338">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-338">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="59b78-339">`--no-restore` -Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="59b78-339">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="59b78-340">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="59b78-340">**mvc, razor**</span></span>

<span data-ttu-id="59b78-341">`-au|--auth <AUTHENTICATION_TYPE>` -Typ ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-341">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="59b78-342">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="59b78-342">The possible values are:</span></span>

- <span data-ttu-id="59b78-343">`None` -Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="59b78-343">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="59b78-344">`Individual` -Jednotlivé ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-344">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="59b78-345">`IndividualB2C` -Jednotlivé ověřování s Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="59b78-345">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="59b78-346">`SingleOrg` -Organizační ověřování pro jednoho klienta.</span><span class="sxs-lookup"><span data-stu-id="59b78-346">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="59b78-347">`MultiOrg` -Organizační ověřování pro víc klientů.</span><span class="sxs-lookup"><span data-stu-id="59b78-347">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="59b78-348">`Windows` -Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="59b78-348">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="59b78-349">`--aad-b2c-instance <INSTANCE>` -Instance Azure Active Directory B2C se připojit k.</span><span class="sxs-lookup"><span data-stu-id="59b78-349">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="59b78-350">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-350">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="59b78-351">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="59b78-351">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="59b78-352">`-ssp|--susi-policy-id <ID>` – ID přihlášení a odhlášení zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="59b78-352">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="59b78-353">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-353">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="59b78-354">`-rp|--reset-password-policy-id <ID>` -Resetování hesla ID zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="59b78-354">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="59b78-355">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-355">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="59b78-356">`-ep|--edit-profile-policy-id <ID>` -Upravit profil ID zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="59b78-356">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="59b78-357">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-357">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="59b78-358">`--aad-instance <INSTANCE>` -Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="59b78-358">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="59b78-359">Použití s `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-359">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="59b78-360">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="59b78-360">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="59b78-361">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="59b78-361">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="59b78-362">Použití s `IndividualB2C`, `SingleOrg`, nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-362">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="59b78-363">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="59b78-363">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="59b78-364">`--domain <DOMAIN>` -Doména pro directory klienta.</span><span class="sxs-lookup"><span data-stu-id="59b78-364">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="59b78-365">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-365">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="59b78-366">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="59b78-366">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="59b78-367">`--tenant-id <ID>` -TenantId ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="59b78-367">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="59b78-368">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-368">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="59b78-369">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="59b78-369">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="59b78-370">`--callback-path <PATH>` – Cesta žádosti v rámci základní cesty aplikace identifikátor URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="59b78-370">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="59b78-371">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-371">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="59b78-372">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="59b78-372">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="59b78-373">`-r|--org-read-access` – Umožňuje této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="59b78-373">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="59b78-374">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-374">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="59b78-375">`--use-launch-settings` -Zahrnuje *launchSettings.json* ve výstupu vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="59b78-375">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="59b78-376">`--use-browserlink` -Zahrnuje BrowserLink v projektu.</span><span class="sxs-lookup"><span data-stu-id="59b78-376">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="59b78-377">`-uld|--use-local-db` -Určuje, že místo SQLite by použít LocalDB.</span><span class="sxs-lookup"><span data-stu-id="59b78-377">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="59b78-378">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-378">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="59b78-379">`--no-restore` -Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="59b78-379">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="59b78-380">**Stránka**</span><span class="sxs-lookup"><span data-stu-id="59b78-380">**page**</span></span>

<span data-ttu-id="59b78-381">`-na|--namespace <NAMESPACE_NAME>`-Namespace pro generovaný kód.</span><span class="sxs-lookup"><span data-stu-id="59b78-381">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="59b78-382">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="59b78-382">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="59b78-383">`-np|--no-pagemodel` -Vytvoří danou stránku bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="59b78-383">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="59b78-384">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="59b78-384">**viewimports**</span></span>

<span data-ttu-id="59b78-385">`-na|--namespace <NAMESPACE_NAME>`-Namespace pro generovaný kód.</span><span class="sxs-lookup"><span data-stu-id="59b78-385">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="59b78-386">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="59b78-386">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="59b78-387">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="59b78-387">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="59b78-388">**konzole úhlová, reagovat, reactredux**</span><span class="sxs-lookup"><span data-stu-id="59b78-388">**console, angular, react, reactredux**</span></span>

  <span data-ttu-id="59b78-389">`--no-restore` -Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="59b78-389">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="59b78-390">**classlib**</span><span class="sxs-lookup"><span data-stu-id="59b78-390">**classlib**</span></span>

<span data-ttu-id="59b78-391">`-f|--framework <FRAMEWORK>` -Určuje [framework](../../standard/frameworks.md) k cíli.</span><span class="sxs-lookup"><span data-stu-id="59b78-391">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="59b78-392">Hodnoty: `netcoreapp2.0` pro vytvoření základní knihovny tříd rozhraní .NET nebo `netstandard2.0` vytvořit standardní knihovny tříd rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="59b78-392">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="59b78-393">Výchozí hodnota je `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="59b78-393">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="59b78-394">`--no-restore` -Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="59b78-394">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="59b78-395">**mstestu xunit**</span><span class="sxs-lookup"><span data-stu-id="59b78-395">**mstest, xunit**</span></span>

<span data-ttu-id="59b78-396">`-p|--enable-pack` – Umožňuje vytváření balíčků pro projekt pomocí [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="59b78-396">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="59b78-397">`--no-restore` -Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="59b78-397">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="59b78-398">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="59b78-398">**globaljson**</span></span>

<span data-ttu-id="59b78-399">`--sdk-version <VERSION_NUMBER>` -Určuje verzi rozhraní .NET Core SDK pro použití v *global.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="59b78-399">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="59b78-400">**web**</span><span class="sxs-lookup"><span data-stu-id="59b78-400">**web**</span></span>

<span data-ttu-id="59b78-401">`--use-launch-settings` -Zahrnuje *launchSettings.json* ve výstupu vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="59b78-401">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="59b78-402">`--no-restore` -Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="59b78-402">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="59b78-403">**webapi**</span><span class="sxs-lookup"><span data-stu-id="59b78-403">**webapi**</span></span>

<span data-ttu-id="59b78-404">`-au|--auth <AUTHENTICATION_TYPE>` -Typ ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-404">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="59b78-405">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="59b78-405">The possible values are:</span></span>

- <span data-ttu-id="59b78-406">`None` -Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="59b78-406">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="59b78-407">`IndividualB2C` -Jednotlivé ověřování s Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="59b78-407">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="59b78-408">`SingleOrg` -Organizační ověřování pro jednoho klienta.</span><span class="sxs-lookup"><span data-stu-id="59b78-408">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="59b78-409">`Windows` -Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="59b78-409">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="59b78-410">`--aad-b2c-instance <INSTANCE>` -Instance Azure Active Directory B2C se připojit k.</span><span class="sxs-lookup"><span data-stu-id="59b78-410">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="59b78-411">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-411">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="59b78-412">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="59b78-412">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="59b78-413">`-ssp|--susi-policy-id <ID>` – ID přihlášení a odhlášení zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="59b78-413">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="59b78-414">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-414">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="59b78-415">`--aad-instance <INSTANCE>` -Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="59b78-415">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="59b78-416">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-416">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="59b78-417">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="59b78-417">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="59b78-418">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="59b78-418">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="59b78-419">Použití s `IndividualB2C` nebo `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-419">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="59b78-420">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="59b78-420">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="59b78-421">`--domain <DOMAIN>` -Doména pro directory klienta.</span><span class="sxs-lookup"><span data-stu-id="59b78-421">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="59b78-422">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-422">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="59b78-423">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="59b78-423">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="59b78-424">`--tenant-id <ID>` -TenantId ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="59b78-424">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="59b78-425">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-425">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="59b78-426">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="59b78-426">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="59b78-427">`-r|--org-read-access` – Umožňuje této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="59b78-427">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="59b78-428">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-428">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="59b78-429">`--use-launch-settings` -Zahrnuje *launchSettings.json* ve výstupu vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="59b78-429">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="59b78-430">`-uld|--use-local-db` -Určuje, že místo SQLite by použít LocalDB.</span><span class="sxs-lookup"><span data-stu-id="59b78-430">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="59b78-431">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-431">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="59b78-432">`--no-restore` -Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="59b78-432">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="59b78-433">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="59b78-433">**mvc, razor**</span></span>

<span data-ttu-id="59b78-434">`-au|--auth <AUTHENTICATION_TYPE>` -Typ ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-434">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="59b78-435">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="59b78-435">The possible values are:</span></span>

- <span data-ttu-id="59b78-436">`None` -Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="59b78-436">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="59b78-437">`Individual` -Jednotlivé ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-437">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="59b78-438">`IndividualB2C` -Jednotlivé ověřování s Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="59b78-438">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="59b78-439">`SingleOrg` -Organizační ověřování pro jednoho klienta.</span><span class="sxs-lookup"><span data-stu-id="59b78-439">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="59b78-440">`MultiOrg` -Organizační ověřování pro víc klientů.</span><span class="sxs-lookup"><span data-stu-id="59b78-440">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="59b78-441">`Windows` -Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="59b78-441">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="59b78-442">`--aad-b2c-instance <INSTANCE>` -Instance Azure Active Directory B2C se připojit k.</span><span class="sxs-lookup"><span data-stu-id="59b78-442">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="59b78-443">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-443">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="59b78-444">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="59b78-444">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="59b78-445">`-ssp|--susi-policy-id <ID>` – ID přihlášení a odhlášení zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="59b78-445">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="59b78-446">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-446">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="59b78-447">`-rp|--reset-password-policy-id <ID>` -Resetování hesla ID zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="59b78-447">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="59b78-448">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-448">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="59b78-449">`-ep|--edit-profile-policy-id <ID>` -Upravit profil ID zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="59b78-449">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="59b78-450">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-450">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="59b78-451">`--aad-instance <INSTANCE>` -Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="59b78-451">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="59b78-452">Použití s `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-452">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="59b78-453">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="59b78-453">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="59b78-454">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="59b78-454">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="59b78-455">Použití s `IndividualB2C`, `SingleOrg`, nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-455">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="59b78-456">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="59b78-456">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="59b78-457">`--domain <DOMAIN>` -Doména pro directory klienta.</span><span class="sxs-lookup"><span data-stu-id="59b78-457">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="59b78-458">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-458">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="59b78-459">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="59b78-459">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="59b78-460">`--tenant-id <ID>` -TenantId ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="59b78-460">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="59b78-461">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-461">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="59b78-462">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="59b78-462">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="59b78-463">`--callback-path <PATH>` – Cesta žádosti v rámci základní cesty aplikace identifikátor URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="59b78-463">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="59b78-464">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-464">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="59b78-465">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="59b78-465">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="59b78-466">`-r|--org-read-access` – Umožňuje této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="59b78-466">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="59b78-467">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-467">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="59b78-468">`--use-launch-settings` -Zahrnuje *launchSettings.json* ve výstupu vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="59b78-468">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="59b78-469">`--use-browserlink` -Zahrnuje BrowserLink v projektu.</span><span class="sxs-lookup"><span data-stu-id="59b78-469">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="59b78-470">`-uld|--use-local-db` -Určuje, že místo SQLite by použít LocalDB.</span><span class="sxs-lookup"><span data-stu-id="59b78-470">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="59b78-471">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-471">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="59b78-472">`--no-restore` -Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="59b78-472">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="59b78-473">**Stránka**</span><span class="sxs-lookup"><span data-stu-id="59b78-473">**page**</span></span>

<span data-ttu-id="59b78-474">`-na|--namespace <NAMESPACE_NAME>`-Namespace pro generovaný kód.</span><span class="sxs-lookup"><span data-stu-id="59b78-474">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="59b78-475">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="59b78-475">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="59b78-476">`-np|--no-pagemodel` -Vytvoří danou stránku bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="59b78-476">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="59b78-477">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="59b78-477">**viewimports**</span></span>

<span data-ttu-id="59b78-478">`-na|--namespace <NAMESPACE_NAME>`-Namespace pro generovaný kód.</span><span class="sxs-lookup"><span data-stu-id="59b78-478">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="59b78-479">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="59b78-479">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="59b78-480">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="59b78-480">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="59b78-481">**konzola, xunit, mstestu, web, webapi**</span><span class="sxs-lookup"><span data-stu-id="59b78-481">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="59b78-482">`-f|--framework` -Určuje [framework](../../standard/frameworks.md) k cíli.</span><span class="sxs-lookup"><span data-stu-id="59b78-482">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="59b78-483">Hodnoty: `netcoreapp1.0` nebo `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="59b78-483">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="59b78-484">Výchozí hodnota je `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="59b78-484">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="59b78-485">**classlib**</span><span class="sxs-lookup"><span data-stu-id="59b78-485">**classlib**</span></span>

<span data-ttu-id="59b78-486">`-f|--framework` -Určuje [framework](../../standard/frameworks.md) k cíli.</span><span class="sxs-lookup"><span data-stu-id="59b78-486">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="59b78-487">Hodnoty: `netcoreapp1.0`, `netcoreapp1.1`, nebo `netstandard1.0` k `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="59b78-487">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="59b78-488">Výchozí hodnota je `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="59b78-488">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="59b78-489">**mvc**</span><span class="sxs-lookup"><span data-stu-id="59b78-489">**mvc**</span></span>

<span data-ttu-id="59b78-490">`-f|--framework` -Určuje [framework](../../standard/frameworks.md) k cíli.</span><span class="sxs-lookup"><span data-stu-id="59b78-490">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="59b78-491">Hodnoty: `netcoreapp1.0` nebo `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="59b78-491">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="59b78-492">Výchozí hodnota je `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="59b78-492">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="59b78-493">`-au|--auth` -Typ ověřování.</span><span class="sxs-lookup"><span data-stu-id="59b78-493">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="59b78-494">Hodnoty: `None` nebo `Individual`.</span><span class="sxs-lookup"><span data-stu-id="59b78-494">Values: `None` or `Individual`.</span></span> <span data-ttu-id="59b78-495">Výchozí hodnota je `None`.</span><span class="sxs-lookup"><span data-stu-id="59b78-495">The default value is `None`.</span></span>

<span data-ttu-id="59b78-496">`-uld|--use-local-db` -Určuje, zda pro použití LocalDB místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="59b78-496">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="59b78-497">Hodnoty: `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="59b78-497">Values: `true` or `false`.</span></span> <span data-ttu-id="59b78-498">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="59b78-498">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="59b78-499">Příklady</span><span class="sxs-lookup"><span data-stu-id="59b78-499">Examples</span></span>

<span data-ttu-id="59b78-500">Vytvoření projektu aplikace konzoly F # v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="59b78-500">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="59b78-501">Vytvořte standardní rozhraní .NET projektu knihovny tříd v zadaný adresář (dostupné pouze s .NET Core SDK 2.0 nebo novější verze):</span><span class="sxs-lookup"><span data-stu-id="59b78-501">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="59b78-502">Vytvořte nový projekt aplikace ASP.NET Core C# MVC v aktuálním adresáři bez jakéhokoli ověřování cílení na rozhraní .NET 2.0 jádra:</span><span class="sxs-lookup"><span data-stu-id="59b78-502">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication targeting .NET Core 2.0:</span></span>

`dotnet new mvc -au None -f netcoreapp2.0`

<span data-ttu-id="59b78-503">Vytvoření nové aplikace xUnit cílení na rozhraní .NET 2.0 jádra:</span><span class="sxs-lookup"><span data-stu-id="59b78-503">Create a new xUnit application targeting .NET Core 2.0:</span></span>

`dotnet new xunit --framework netcoreapp2.0`

<span data-ttu-id="59b78-504">Seznam všech šablon, které jsou k dispozici pro MVC:</span><span class="sxs-lookup"><span data-stu-id="59b78-504">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="59b78-505">Instalace verze 2.0 šablon jedné stránky aplikace ASP.NET Core (příkaz možnost k dispozici pro .NET Core SDK 1.1 a pouze novější verze):</span><span class="sxs-lookup"><span data-stu-id="59b78-505">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="59b78-506">Vytvoření *global.json* v aktuálním adresáři nastavení verze sady SDK na 2.0.0 (dostupné pouze s .NET Core SDK 2.0 nebo novější verze):</span><span class="sxs-lookup"><span data-stu-id="59b78-506">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="59b78-507">Viz také:</span><span class="sxs-lookup"><span data-stu-id="59b78-507">See also</span></span>

[<span data-ttu-id="59b78-508">Vlastní šablony pro nové dotnet.</span><span class="sxs-lookup"><span data-stu-id="59b78-508">Custom templates for dotnet new</span></span>](custom-templates.md)  
[<span data-ttu-id="59b78-509">Vytvoření vlastní šablony pro dotnet new</span><span class="sxs-lookup"><span data-stu-id="59b78-509">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
[<span data-ttu-id="59b78-510">úložiště GitHub DotNet/dotnet šablony – ukázky</span><span class="sxs-lookup"><span data-stu-id="59b78-510">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
[<span data-ttu-id="59b78-511">Dostupné šablony pro nové dotnet.</span><span class="sxs-lookup"><span data-stu-id="59b78-511">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)