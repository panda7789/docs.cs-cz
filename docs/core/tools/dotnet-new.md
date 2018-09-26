---
title: nový příkaz DotNet – rozhraní příkazového řádku .NET Core
description: Vytvoří nový příkaz dotnet nových projektů .NET Core založených na zadané šabloně.
author: mairaw
ms.author: mairaw
ms.date: 07/31/2018
ms.openlocfilehash: 396c4ddf09854fa4582226bdb1422f8c929e459b
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47083049"
---
# <a name="dotnet-new"></a><span data-ttu-id="ad1a2-103">nový příkaz DotNet</span><span class="sxs-lookup"><span data-stu-id="ad1a2-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="ad1a2-104">Název</span><span class="sxs-lookup"><span data-stu-id="ad1a2-104">Name</span></span>

<span data-ttu-id="ad1a2-105">`dotnet new` -Vytvoří nový projekt, konfigurační soubor nebo řešení založené na zadané šabloně.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ad1a2-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="ad1a2-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="ad1a2-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="ad1a2-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output]
    [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="ad1a2-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="ad1a2-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ad1a2-109">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="ad1a2-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="ad1a2-110">Popis</span><span class="sxs-lookup"><span data-stu-id="ad1a2-110">Description</span></span>

<span data-ttu-id="ad1a2-111">`dotnet new` Příkaz poskytuje pohodlný způsob, jak inicializovat platný projekt .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="ad1a2-112">Příkaz volání [modulu šablon](https://github.com/dotnet/templating) vytvořit artefakty na disku na základě určené šablony a možnosti.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="ad1a2-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="ad1a2-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="ad1a2-114">Šablona pro vytvoření instance při vyvolání příkazu.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="ad1a2-115">Každá šablona může mít specifické možnosti, které lze předat.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="ad1a2-116">Další informace najdete v tématu [možnosti šablony](#template-options).</span><span class="sxs-lookup"><span data-stu-id="ad1a2-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="ad1a2-117">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="ad1a2-117">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="ad1a2-118">Příkaz obsahuje výchozí seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-118">The command contains a default list of templates.</span></span> <span data-ttu-id="ad1a2-119">Použití `dotnet new -l` získat seznam dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="ad1a2-120">V následující tabulce jsou uvedeny šablony, které jsou předinstalovány se sadou .NET Core SDK 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-120">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="ad1a2-121">Výchozí jazyk šablony se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="ad1a2-122">Popis šablony</span><span class="sxs-lookup"><span data-stu-id="ad1a2-122">Template description</span></span>                          | <span data-ttu-id="ad1a2-123">Název šablony</span><span class="sxs-lookup"><span data-stu-id="ad1a2-123">Template name</span></span>   | <span data-ttu-id="ad1a2-124">Jazyky</span><span class="sxs-lookup"><span data-stu-id="ad1a2-124">Languages</span></span>     |
|----------------------------------------------|-----------------|---------------|
| <span data-ttu-id="ad1a2-125">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="ad1a2-125">Console application</span></span>                          | `console`       | <span data-ttu-id="ad1a2-126">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="ad1a2-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="ad1a2-127">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="ad1a2-127">Class library</span></span>                                | `classlib`      | <span data-ttu-id="ad1a2-128">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="ad1a2-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="ad1a2-129">Projekt testu jednotek</span><span class="sxs-lookup"><span data-stu-id="ad1a2-129">Unit test project</span></span>                            | `mstest`        | <span data-ttu-id="ad1a2-130">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="ad1a2-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="ad1a2-131">Projekt testů xUnit</span><span class="sxs-lookup"><span data-stu-id="ad1a2-131">xUnit test project</span></span>                           | `xunit`         | <span data-ttu-id="ad1a2-132">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="ad1a2-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="ad1a2-133">Stránka Razor</span><span class="sxs-lookup"><span data-stu-id="ad1a2-133">Razor page</span></span>                                   | `page`          | <span data-ttu-id="ad1a2-134">[C#]</span><span class="sxs-lookup"><span data-stu-id="ad1a2-134">[C#]</span></span>          |
| <span data-ttu-id="ad1a2-135">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="ad1a2-135">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="ad1a2-136">[C#]</span><span class="sxs-lookup"><span data-stu-id="ad1a2-136">[C#]</span></span>          |
| <span data-ttu-id="ad1a2-137">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="ad1a2-137">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="ad1a2-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="ad1a2-138">[C#]</span></span>          |
| <span data-ttu-id="ad1a2-139">ASP.NET Core je prázdný</span><span class="sxs-lookup"><span data-stu-id="ad1a2-139">ASP.NET Core empty</span></span>                           | `web`           | <span data-ttu-id="ad1a2-140">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="ad1a2-140">[C#], F#</span></span>      |
| <span data-ttu-id="ad1a2-141">Webové aplikace ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="ad1a2-141">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="ad1a2-142">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="ad1a2-142">[C#], F#</span></span>      |
| <span data-ttu-id="ad1a2-143">Webové aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ad1a2-143">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="ad1a2-144">[C#]</span><span class="sxs-lookup"><span data-stu-id="ad1a2-144">[C#]</span></span>          |
| <span data-ttu-id="ad1a2-145">ASP.NET Core pomocí Angular</span><span class="sxs-lookup"><span data-stu-id="ad1a2-145">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="ad1a2-146">[C#]</span><span class="sxs-lookup"><span data-stu-id="ad1a2-146">[C#]</span></span>          |
| <span data-ttu-id="ad1a2-147">ASP.NET Core pomocí React.js</span><span class="sxs-lookup"><span data-stu-id="ad1a2-147">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="ad1a2-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="ad1a2-148">[C#]</span></span>          |
| <span data-ttu-id="ad1a2-149">ASP.NET Core pomocí React.js a Redux</span><span class="sxs-lookup"><span data-stu-id="ad1a2-149">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="ad1a2-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="ad1a2-150">[C#]</span></span>          |
| <span data-ttu-id="ad1a2-151">Webové rozhraní API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ad1a2-151">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="ad1a2-152">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="ad1a2-152">[C#], F#</span></span>      |
| <span data-ttu-id="ad1a2-153">Knihovny tříd Razor</span><span class="sxs-lookup"><span data-stu-id="ad1a2-153">Razor class library</span></span>                          | `razorclasslib` | <span data-ttu-id="ad1a2-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="ad1a2-154">[C#]</span></span>          |
| <span data-ttu-id="ad1a2-155">soubor Global.JSON</span><span class="sxs-lookup"><span data-stu-id="ad1a2-155">global.json file</span></span>                             | `globaljson`    |               |
| <span data-ttu-id="ad1a2-156">NuGet config</span><span class="sxs-lookup"><span data-stu-id="ad1a2-156">NuGet config</span></span>                                 | `nugetconfig`   |               |
| <span data-ttu-id="ad1a2-157">Webové konfigurace</span><span class="sxs-lookup"><span data-stu-id="ad1a2-157">Web config</span></span>                                   | `webconfig`     |               |
| <span data-ttu-id="ad1a2-158">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="ad1a2-158">Solution file</span></span>                                | `sln`           |               |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="ad1a2-159">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="ad1a2-159">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="ad1a2-160">Příkaz obsahuje výchozí seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-160">The command contains a default list of templates.</span></span> <span data-ttu-id="ad1a2-161">Použití `dotnet new -l` získat seznam dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-161">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="ad1a2-162">V následující tabulce jsou uvedeny šablony, které jsou předem nainstalované s .NET Core SDK 2.0.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-162">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.</span></span> <span data-ttu-id="ad1a2-163">Výchozí jazyk šablony se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-163">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="ad1a2-164">Popis šablony</span><span class="sxs-lookup"><span data-stu-id="ad1a2-164">Template description</span></span>                          | <span data-ttu-id="ad1a2-165">Název šablony</span><span class="sxs-lookup"><span data-stu-id="ad1a2-165">Template name</span></span> | <span data-ttu-id="ad1a2-166">Jazyky</span><span class="sxs-lookup"><span data-stu-id="ad1a2-166">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="ad1a2-167">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="ad1a2-167">Console application</span></span>                          | `console`     | <span data-ttu-id="ad1a2-168">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="ad1a2-168">[C#], F#, VB</span></span>  |
| <span data-ttu-id="ad1a2-169">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="ad1a2-169">Class library</span></span>                                | `classlib`    | <span data-ttu-id="ad1a2-170">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="ad1a2-170">[C#], F#, VB</span></span>  |
| <span data-ttu-id="ad1a2-171">Projekt testu jednotek</span><span class="sxs-lookup"><span data-stu-id="ad1a2-171">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="ad1a2-172">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="ad1a2-172">[C#], F#, VB</span></span>  |
| <span data-ttu-id="ad1a2-173">Projekt testů xUnit</span><span class="sxs-lookup"><span data-stu-id="ad1a2-173">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="ad1a2-174">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="ad1a2-174">[C#], F#, VB</span></span>  |
| <span data-ttu-id="ad1a2-175">ASP.NET Core je prázdný</span><span class="sxs-lookup"><span data-stu-id="ad1a2-175">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="ad1a2-176">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="ad1a2-176">[C#], F#</span></span>      |
| <span data-ttu-id="ad1a2-177">Webové aplikace ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="ad1a2-177">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="ad1a2-178">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="ad1a2-178">[C#], F#</span></span>      |
| <span data-ttu-id="ad1a2-179">Webové aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ad1a2-179">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="ad1a2-180">[C#]</span><span class="sxs-lookup"><span data-stu-id="ad1a2-180">[C#]</span></span>          |
| <span data-ttu-id="ad1a2-181">ASP.NET Core pomocí Angular</span><span class="sxs-lookup"><span data-stu-id="ad1a2-181">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="ad1a2-182">[C#]</span><span class="sxs-lookup"><span data-stu-id="ad1a2-182">[C#]</span></span>          |
| <span data-ttu-id="ad1a2-183">ASP.NET Core pomocí React.js</span><span class="sxs-lookup"><span data-stu-id="ad1a2-183">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="ad1a2-184">[C#]</span><span class="sxs-lookup"><span data-stu-id="ad1a2-184">[C#]</span></span>          |
| <span data-ttu-id="ad1a2-185">ASP.NET Core pomocí React.js a Redux</span><span class="sxs-lookup"><span data-stu-id="ad1a2-185">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="ad1a2-186">[C#]</span><span class="sxs-lookup"><span data-stu-id="ad1a2-186">[C#]</span></span>          |
| <span data-ttu-id="ad1a2-187">Webové rozhraní API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ad1a2-187">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="ad1a2-188">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="ad1a2-188">[C#], F#</span></span>      |
| <span data-ttu-id="ad1a2-189">soubor Global.JSON</span><span class="sxs-lookup"><span data-stu-id="ad1a2-189">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="ad1a2-190">NuGet config</span><span class="sxs-lookup"><span data-stu-id="ad1a2-190">NuGet config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="ad1a2-191">Webové konfigurace</span><span class="sxs-lookup"><span data-stu-id="ad1a2-191">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="ad1a2-192">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="ad1a2-192">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="ad1a2-193">Stránka Razor</span><span class="sxs-lookup"><span data-stu-id="ad1a2-193">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="ad1a2-194">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="ad1a2-194">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="ad1a2-195">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="ad1a2-195">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ad1a2-196">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="ad1a2-196">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="ad1a2-197">Příkaz obsahuje výchozí seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-197">The command contains a default list of templates.</span></span> <span data-ttu-id="ad1a2-198">Použití `dotnet new -all` získat seznam dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-198">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="ad1a2-199">V následující tabulce jsou uvedeny šablony, které jsou předinstalovány se sadou SDK .NET Core 1.x.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-199">The following table shows the templates that come pre-installed with the .NET Core SDK 1.x.</span></span> <span data-ttu-id="ad1a2-200">Výchozí jazyk šablony se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-200">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="ad1a2-201">Popis šablony</span><span class="sxs-lookup"><span data-stu-id="ad1a2-201">Template description</span></span>  | <span data-ttu-id="ad1a2-202">Název šablony</span><span class="sxs-lookup"><span data-stu-id="ad1a2-202">Template name</span></span> | <span data-ttu-id="ad1a2-203">Jazyky</span><span class="sxs-lookup"><span data-stu-id="ad1a2-203">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="ad1a2-204">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="ad1a2-204">Console application</span></span>  | `console`     | <span data-ttu-id="ad1a2-205">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="ad1a2-205">[C#], F#</span></span>  |
| <span data-ttu-id="ad1a2-206">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="ad1a2-206">Class library</span></span>        | `classlib`    | <span data-ttu-id="ad1a2-207">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="ad1a2-207">[C#], F#</span></span>  |
| <span data-ttu-id="ad1a2-208">Projekt testu jednotek</span><span class="sxs-lookup"><span data-stu-id="ad1a2-208">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="ad1a2-209">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="ad1a2-209">[C#], F#</span></span>  |
| <span data-ttu-id="ad1a2-210">Projekt testů xUnit</span><span class="sxs-lookup"><span data-stu-id="ad1a2-210">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="ad1a2-211">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="ad1a2-211">[C#], F#</span></span>  |
| <span data-ttu-id="ad1a2-212">ASP.NET Core je prázdný</span><span class="sxs-lookup"><span data-stu-id="ad1a2-212">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="ad1a2-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="ad1a2-213">[C#]</span></span>      |
| <span data-ttu-id="ad1a2-214">Webové aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ad1a2-214">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="ad1a2-215">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="ad1a2-215">[C#], F#</span></span>  |
| <span data-ttu-id="ad1a2-216">Webové rozhraní API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ad1a2-216">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="ad1a2-217">[C#]</span><span class="sxs-lookup"><span data-stu-id="ad1a2-217">[C#]</span></span>      |
| <span data-ttu-id="ad1a2-218">NuGet config</span><span class="sxs-lookup"><span data-stu-id="ad1a2-218">NuGet config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="ad1a2-219">Webové konfigurace</span><span class="sxs-lookup"><span data-stu-id="ad1a2-219">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="ad1a2-220">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="ad1a2-220">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="ad1a2-221">Možnosti</span><span class="sxs-lookup"><span data-stu-id="ad1a2-221">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="ad1a2-222">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="ad1a2-222">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="ad1a2-223">Vynutí obsahu chcete vygenerovat i v případě, že by došlo ke změně existujících souborů.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-223">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="ad1a2-224">To je potřeba při výstupní adresář již obsahuje projekt.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-224">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="ad1a2-225">Vytiskne nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-225">Prints out help for the command.</span></span> <span data-ttu-id="ad1a2-226">Může být vyvolána pro `dotnet new` samotný příkaz nebo pro všechny šablony, jako například `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-226">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="ad1a2-227">Nainstaluje zdroj nebo šablony pack z `PATH` nebo `NUGET_ID` k dispozici.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-227">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="ad1a2-228">Pokud chcete nainstalovat zkušební verzi balíčku šablony, je třeba zadat verzi ve formátu `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-228">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="ad1a2-229">Ve výchozím nastavení `dotnet new` předá \* pro verzi, která představuje poslední stabilní balíček verze.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-229">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="ad1a2-230">Podívejte se příklad na [příklady](#examples) oddílu.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-230">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="ad1a2-231">Informace o vytváření vlastních šablon najdete v tématu [vlastních šablon pro dotnet nové](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="ad1a2-231">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="ad1a2-232">Zobrazí seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-232">Lists templates containing the specified name.</span></span> <span data-ttu-id="ad1a2-233">Pokud je vyvolána `dotnet new` příkazu, uvádí možné šablony, které jsou k dispozici pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-233">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="ad1a2-234">Například pokud adresář, projekt již obsahuje, neobsahuje všechny šablony projektů.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-234">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="ad1a2-235">Jazyk šablony k vytvoření.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-235">The language of the template to create.</span></span> <span data-ttu-id="ad1a2-236">Jazyk přijato, se liší podle šablony (Zobrazit výchozí hodnoty v [argumenty](#arguments) části).</span><span class="sxs-lookup"><span data-stu-id="ad1a2-236">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="ad1a2-237">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-237">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="ad1a2-238">Některé součásti pro interpretaci `#` jako speciální znak.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-238">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="ad1a2-239">V takových případech bude nutné uvést hodnotu parametru jazyka, jako `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-239">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="ad1a2-240">Název pro výstup vytvořený.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-240">The name for the created output.</span></span> <span data-ttu-id="ad1a2-241">Pokud není zadán žádný název, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-241">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="ad1a2-242">Určuje zdroj NuGet, který chcete použít během instalace.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-242">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="ad1a2-243">Umístění pro vygenerovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-243">Location to place the generated output.</span></span> <span data-ttu-id="ad1a2-244">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-244">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="ad1a2-245">Vyfiltruje šablony podle dostupných typů.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-245">Filters templates based on available types.</span></span> <span data-ttu-id="ad1a2-246">Předdefinované hodnoty jsou "projekt", "item" nebo "jiné".</span><span class="sxs-lookup"><span data-stu-id="ad1a2-246">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="ad1a2-247">Odinstaluje zdroj nebo šablony pack na `PATH` nebo `NUGET_ID` k dispozici.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-247">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="ad1a2-248">Chcete-li odinstalovat sadu pomocí šablony `PATH`, budete potřebovat plně kvalifikovanou cestu.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-248">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="ad1a2-249">Například *C:/uživatele/\<uživatele > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z obsahuje složky nebudou.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-249">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="ad1a2-250">Kromě toho nesmí být znak konečné ukončující znak lomítka adresáře na cestu k šabloně.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-250">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="ad1a2-251">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="ad1a2-251">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="ad1a2-252">Vynutí obsahu chcete vygenerovat i v případě, že by došlo ke změně existujících souborů.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-252">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="ad1a2-253">To je potřeba při výstupní adresář již obsahuje projekt.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-253">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="ad1a2-254">Vytiskne nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-254">Prints out help for the command.</span></span> <span data-ttu-id="ad1a2-255">Může být vyvolána pro `dotnet new` samotný příkaz nebo pro všechny šablony, jako například `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-255">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="ad1a2-256">Nainstaluje zdroj nebo šablony pack z `PATH` nebo `NUGET_ID` k dispozici.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-256">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="ad1a2-257">Pokud chcete nainstalovat zkušební verzi balíčku šablony, je třeba zadat verzi ve formátu `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-257">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="ad1a2-258">Ve výchozím nastavení `dotnet new` předá \* pro verzi, která představuje poslední stabilní balíček verze.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-258">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="ad1a2-259">Podívejte se příklad na [příklady](#examples) oddílu.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-259">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="ad1a2-260">Informace o vytváření vlastních šablon najdete v tématu [vlastních šablon pro dotnet nové](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="ad1a2-260">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="ad1a2-261">Zobrazí seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-261">Lists templates containing the specified name.</span></span> <span data-ttu-id="ad1a2-262">Pokud je vyvolána `dotnet new` příkazu, uvádí možné šablony, které jsou k dispozici pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-262">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="ad1a2-263">Například pokud adresář, projekt již obsahuje, neobsahuje všechny šablony projektů.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-263">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="ad1a2-264">Jazyk šablony k vytvoření.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-264">The language of the template to create.</span></span> <span data-ttu-id="ad1a2-265">Jazyk přijato, se liší podle šablony (Zobrazit výchozí hodnoty v [argumenty](#arguments) části).</span><span class="sxs-lookup"><span data-stu-id="ad1a2-265">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="ad1a2-266">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-266">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="ad1a2-267">Některé součásti pro interpretaci `#` jako speciální znak.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-267">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="ad1a2-268">V takových případech bude nutné uvést hodnotu parametru jazyka, jako `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-268">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="ad1a2-269">Název pro výstup vytvořený.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-269">The name for the created output.</span></span> <span data-ttu-id="ad1a2-270">Pokud není zadán žádný název, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-270">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="ad1a2-271">Umístění pro vygenerovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-271">Location to place the generated output.</span></span> <span data-ttu-id="ad1a2-272">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-272">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="ad1a2-273">Vyfiltruje šablony podle dostupných typů.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-273">Filters templates based on available types.</span></span> <span data-ttu-id="ad1a2-274">Předdefinované hodnoty jsou "projekt", "item" nebo "jiné".</span><span class="sxs-lookup"><span data-stu-id="ad1a2-274">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="ad1a2-275">Odinstaluje zdroj nebo šablony pack na `PATH` nebo `NUGET_ID` k dispozici.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-275">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="ad1a2-276">Odinstalace pomocí zdroj `PATH`, budete potřebovat plně kvalifikovanou cestu.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-276">To uninstall a template using a source `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="ad1a2-277">Například *C:/uživatele/\<uživatele > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z obsahuje složky nebudou.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-277">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span> <span data-ttu-id="ad1a2-278">Kromě toho nesmí být znak konečné ukončující znak lomítka adresáře na cestu k šabloně.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-278">Additionally, do not include a final terminating directory slash on your template path.</span></span>
> 
> <span data-ttu-id="ad1a2-279">Pokud se nemůžete určit `PATH` nebo `NUGET_ID` argumentů potřebných k odinstalaci šablonu s `dotnet new --uninstall` bez argumentu zobrazí seznam všech nainstalovaných šablon a argument nutné je odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-279">If you are unable to determine the `PATH` or `NUGET_ID` argument needed to uninstall a template, running `dotnet new --uninstall` without an argument will list all installed templates and the argument required to uninstall them.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ad1a2-280">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="ad1a2-280">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="ad1a2-281">Zobrazí všechny šablony pro konkrétní typ projektu při spuštění v kontextu `dotnet new` samotný příkaz.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-281">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="ad1a2-282">Při spuštění v kontextu konkrétní šablony, jako například `dotnet new web -all`, `-all` je interpretován jako vytvoření příznak force.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-282">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="ad1a2-283">To je potřeba při výstupní adresář již obsahuje projekt.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-283">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="ad1a2-284">Vytiskne nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-284">Prints out help for the command.</span></span> <span data-ttu-id="ad1a2-285">Může být vyvolána pro `dotnet new` samotný příkaz nebo pro všechny šablony, jako například `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-285">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="ad1a2-286">Zobrazí seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-286">Lists templates containing the specified name.</span></span> <span data-ttu-id="ad1a2-287">Pokud je vyvolána `dotnet new` příkazu, uvádí možné šablony, které jsou k dispozici pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-287">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="ad1a2-288">Například pokud adresář, projekt již obsahuje, neobsahuje všechny šablony projektů.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-288">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="ad1a2-289">Jazyk šablony k vytvoření.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-289">The language of the template to create.</span></span> <span data-ttu-id="ad1a2-290">Jazyk přijato, se liší podle šablony (Zobrazit výchozí hodnoty v [argumenty](#arguments) části).</span><span class="sxs-lookup"><span data-stu-id="ad1a2-290">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="ad1a2-291">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-291">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="ad1a2-292">Některé součásti pro interpretaci `#` jako speciální znak.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-292">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="ad1a2-293">V takových případech bude nutné uvést hodnotu parametru jazyka, jako `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-293">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="ad1a2-294">Název pro výstup vytvořený.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-294">The name for the created output.</span></span> <span data-ttu-id="ad1a2-295">Pokud není zadán žádný název, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-295">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="ad1a2-296">Umístění pro vygenerovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-296">Location to place the generated output.</span></span> <span data-ttu-id="ad1a2-297">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-297">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="ad1a2-298">Nastavení šablony</span><span class="sxs-lookup"><span data-stu-id="ad1a2-298">Template options</span></span>

<span data-ttu-id="ad1a2-299">Každá šablona projektu může mít k dispozici další možnosti.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-299">Each project template may have additional options available.</span></span> <span data-ttu-id="ad1a2-300">Základní šablony mají následující další možnosti:</span><span class="sxs-lookup"><span data-stu-id="ad1a2-300">The core templates have the following additional options:</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="ad1a2-301">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="ad1a2-301">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="ad1a2-302">**konzola, angular, react, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="ad1a2-302">**console, angular, react, reactredux, razorclasslib**</span></span>

  <span data-ttu-id="ad1a2-303">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-303">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ad1a2-304">**classlib**</span><span class="sxs-lookup"><span data-stu-id="ad1a2-304">**classlib**</span></span>

<span data-ttu-id="ad1a2-305">`-f|--framework <FRAMEWORK>` : Určuje, že [framework](../../standard/frameworks.md) do cíle.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-305">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ad1a2-306">Hodnoty: `netcoreapp2.0` k vytvoření knihovny tříd .NET Core nebo `netstandard2.0` k vytvoření knihovny tříd .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-306">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="ad1a2-307">Výchozí hodnota je `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-307">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="ad1a2-308">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-308">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ad1a2-309">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="ad1a2-309">**mstest, xunit**</span></span>

<span data-ttu-id="ad1a2-310">`-p|--enable-pack` – Povolí balení pro projekt pomocí [balíčku dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="ad1a2-310">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="ad1a2-311">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-311">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ad1a2-312">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="ad1a2-312">**globaljson**</span></span>

<span data-ttu-id="ad1a2-313">`--sdk-version <VERSION_NUMBER>` : Určuje verzi .NET Core SDK pro použití v *global.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-313">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="ad1a2-314">**web**</span><span class="sxs-lookup"><span data-stu-id="ad1a2-314">**web**</span></span>

<span data-ttu-id="ad1a2-315">`--exclude-launch-settings` -Vyloučení *launchSettings.json* z vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-315">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="ad1a2-316">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-316">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ad1a2-317">`--no-https` -Projektu nebude vyžadovat protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-317">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="ad1a2-318">Tato možnost platí, pouze pokud `IndividualAuth` nebo `OrganizationalAuth` nejsou používány.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-318">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="ad1a2-319">**webapi**</span><span class="sxs-lookup"><span data-stu-id="ad1a2-319">**webapi**</span></span>

<span data-ttu-id="ad1a2-320">`-au|--auth <AUTHENTICATION_TYPE>` -Typ ověřování, který má použít.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-320">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="ad1a2-321">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="ad1a2-321">The possible values are:</span></span>

- <span data-ttu-id="ad1a2-322">`None` -Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="ad1a2-322">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="ad1a2-323">`IndividualB2C` -Jednotlivé ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-323">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="ad1a2-324">`SingleOrg` – Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-324">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="ad1a2-325">`Windows` -Ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-325">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="ad1a2-326">`--aad-b2c-instance <INSTANCE>` -Instanci Azure Active Directory B2C pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-326">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ad1a2-327">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-327">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ad1a2-328">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-328">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="ad1a2-329">`-ssp|--susi-policy-id <ID>` – ID přihlášení a registraci zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-329">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ad1a2-330">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-330">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ad1a2-331">`--aad-instance <INSTANCE>` – Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-331">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ad1a2-332">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-332">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ad1a2-333">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-333">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="ad1a2-334">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-334">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="ad1a2-335">Použití s `IndividualB2C` nebo `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-335">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="ad1a2-336">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-336">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="ad1a2-337">`--domain <DOMAIN>` -Domény tenantu Active directory.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-337">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="ad1a2-338">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-338">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ad1a2-339">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-339">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="ad1a2-340">`--tenant-id <ID>` – ID Tenanta ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-340">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ad1a2-341">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-341">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ad1a2-342">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-342">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="ad1a2-343">`-r|--org-read-access` – Povolí této aplikaci přístup pro čtení do adresáře.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-343">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="ad1a2-344">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-344">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="ad1a2-345">`--exclude-launch-settings` -Vyloučení *launchSettings.json* z vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-345">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="ad1a2-346">`-uld|--use-local-db` : Určuje, že by měl být LocalDB použít místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-346">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ad1a2-347">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-347">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ad1a2-348">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-348">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ad1a2-349">`--no-https` -Projektu nebude vyžadovat protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-349">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="ad1a2-350">`app.UseHsts` a `app.UseHttpsRedirection` nejsou přidány do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-350">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="ad1a2-351">Tato možnost platí, pouze pokud `Individual`, `IndividualB2C`, `SingleOrg`, nebo `MultiOrg` nejsou používány.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-351">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="ad1a2-352">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="ad1a2-352">**mvc, razor**</span></span>

<span data-ttu-id="ad1a2-353">`-au|--auth <AUTHENTICATION_TYPE>` -Typ ověřování, který má použít.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-353">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="ad1a2-354">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="ad1a2-354">The possible values are:</span></span>

- <span data-ttu-id="ad1a2-355">`None` -Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="ad1a2-355">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="ad1a2-356">`Individual` -Jednotlivé ověřování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-356">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="ad1a2-357">`IndividualB2C` -Jednotlivé ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-357">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="ad1a2-358">`SingleOrg` – Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-358">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="ad1a2-359">`MultiOrg` – Ověřování organizace pro více tenantů.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-359">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="ad1a2-360">`Windows` -Ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-360">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="ad1a2-361">`--aad-b2c-instance <INSTANCE>` -Instanci Azure Active Directory B2C pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-361">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ad1a2-362">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-362">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ad1a2-363">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-363">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="ad1a2-364">`-ssp|--susi-policy-id <ID>` – ID přihlášení a registraci zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-364">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ad1a2-365">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-365">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ad1a2-366">`-rp|--reset-password-policy-id <ID>` -Resetování hesla ID zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-366">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="ad1a2-367">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-367">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ad1a2-368">`-ep|--edit-profile-policy-id <ID>` – Upravit profil zásady ID pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-368">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="ad1a2-369">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-369">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ad1a2-370">`--aad-instance <INSTANCE>` – Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-370">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ad1a2-371">Použití s `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-371">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="ad1a2-372">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-372">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="ad1a2-373">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-373">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="ad1a2-374">Použití s `IndividualB2C`, `SingleOrg`, nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-374">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="ad1a2-375">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-375">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="ad1a2-376">`--domain <DOMAIN>` -Domény tenantu Active directory.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-376">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="ad1a2-377">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-377">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ad1a2-378">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-378">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="ad1a2-379">`--tenant-id <ID>` – ID Tenanta ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-379">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ad1a2-380">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-380">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ad1a2-381">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-381">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="ad1a2-382">`--callback-path <PATH>` -Cestu požadavku v rámci základní cesty aplikace identifikátoru URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-382">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="ad1a2-383">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-383">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ad1a2-384">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-384">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="ad1a2-385">`-r|--org-read-access` – Povolí této aplikaci přístup pro čtení do adresáře.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-385">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="ad1a2-386">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-386">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="ad1a2-387">`--exclude-launch-settings` -Vyloučení *launchSettings.json* z vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-387">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="ad1a2-388">`--use-browserlink` -Obsahuje BrowserLink v projektu.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-388">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="ad1a2-389">`-uld|--use-local-db` : Určuje, že by měl být LocalDB použít místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-389">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ad1a2-390">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-390">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ad1a2-391">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-391">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ad1a2-392">`--no-https` -Projektu nebude vyžadovat protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-392">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="ad1a2-393">`app.UseHsts` a `app.UseHttpsRedirection` nejsou přidány do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-393">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="ad1a2-394">Tato možnost platí, pouze pokud `Individual`, `IndividualB2C`, `SingleOrg`, nebo `MultiOrg` nejsou používány.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-394">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="ad1a2-395">**Stránka**</span><span class="sxs-lookup"><span data-stu-id="ad1a2-395">**page**</span></span>

<span data-ttu-id="ad1a2-396">`-na|--namespace <NAMESPACE_NAME>`-Namespace pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-396">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="ad1a2-397">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-397">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="ad1a2-398">`-np|--no-pagemodel` -Vytvoří danou stránku bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-398">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="ad1a2-399">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="ad1a2-399">**viewimports**</span></span>

<span data-ttu-id="ad1a2-400">`-na|--namespace <NAMESPACE_NAME>`-Namespace pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-400">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="ad1a2-401">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-401">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="ad1a2-402">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="ad1a2-402">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="ad1a2-403">**konzola, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="ad1a2-403">**console, angular, react, reactredux**</span></span>

  <span data-ttu-id="ad1a2-404">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-404">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ad1a2-405">**classlib**</span><span class="sxs-lookup"><span data-stu-id="ad1a2-405">**classlib**</span></span>

<span data-ttu-id="ad1a2-406">`-f|--framework <FRAMEWORK>` : Určuje, že [framework](../../standard/frameworks.md) do cíle.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-406">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ad1a2-407">Hodnoty: `netcoreapp2.0` k vytvoření knihovny tříd .NET Core nebo `netstandard2.0` k vytvoření knihovny tříd .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-407">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="ad1a2-408">Výchozí hodnota je `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-408">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="ad1a2-409">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-409">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ad1a2-410">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="ad1a2-410">**mstest, xunit**</span></span>

<span data-ttu-id="ad1a2-411">`-p|--enable-pack` – Povolí balení pro projekt pomocí [balíčku dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="ad1a2-411">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="ad1a2-412">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-412">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ad1a2-413">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="ad1a2-413">**globaljson**</span></span>

<span data-ttu-id="ad1a2-414">`--sdk-version <VERSION_NUMBER>` : Určuje verzi .NET Core SDK pro použití v *global.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-414">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="ad1a2-415">**web**</span><span class="sxs-lookup"><span data-stu-id="ad1a2-415">**web**</span></span>

<span data-ttu-id="ad1a2-416">`--use-launch-settings` -Zahrnuje *launchSettings.json* ve výstupu vygenerovanou šablonu.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-416">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="ad1a2-417">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-417">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ad1a2-418">**webapi**</span><span class="sxs-lookup"><span data-stu-id="ad1a2-418">**webapi**</span></span>

<span data-ttu-id="ad1a2-419">`-au|--auth <AUTHENTICATION_TYPE>` -Typ ověřování, který má použít.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-419">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="ad1a2-420">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="ad1a2-420">The possible values are:</span></span>

- <span data-ttu-id="ad1a2-421">`None` -Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="ad1a2-421">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="ad1a2-422">`IndividualB2C` -Jednotlivé ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-422">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="ad1a2-423">`SingleOrg` – Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-423">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="ad1a2-424">`Windows` -Ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-424">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="ad1a2-425">`--aad-b2c-instance <INSTANCE>` -Instanci Azure Active Directory B2C pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-425">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ad1a2-426">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-426">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ad1a2-427">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-427">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="ad1a2-428">`-ssp|--susi-policy-id <ID>` – ID přihlášení a registraci zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-428">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ad1a2-429">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-429">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ad1a2-430">`--aad-instance <INSTANCE>` – Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-430">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ad1a2-431">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-431">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ad1a2-432">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-432">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="ad1a2-433">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-433">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="ad1a2-434">Použití s `IndividualB2C` nebo `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-434">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="ad1a2-435">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-435">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="ad1a2-436">`--domain <DOMAIN>` -Domény tenantu Active directory.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-436">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="ad1a2-437">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-437">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ad1a2-438">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-438">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="ad1a2-439">`--tenant-id <ID>` – ID Tenanta ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-439">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ad1a2-440">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-440">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ad1a2-441">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-441">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="ad1a2-442">`-r|--org-read-access` – Povolí této aplikaci přístup pro čtení do adresáře.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-442">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="ad1a2-443">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-443">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="ad1a2-444">`--use-launch-settings` -Zahrnuje *launchSettings.json* ve výstupu vygenerovanou šablonu.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-444">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="ad1a2-445">`-uld|--use-local-db` : Určuje, že by měl být LocalDB použít místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-445">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ad1a2-446">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-446">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ad1a2-447">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-447">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ad1a2-448">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="ad1a2-448">**mvc, razor**</span></span>

<span data-ttu-id="ad1a2-449">`-au|--auth <AUTHENTICATION_TYPE>` -Typ ověřování, který má použít.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-449">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="ad1a2-450">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="ad1a2-450">The possible values are:</span></span>

- <span data-ttu-id="ad1a2-451">`None` -Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="ad1a2-451">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="ad1a2-452">`Individual` -Jednotlivé ověřování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-452">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="ad1a2-453">`IndividualB2C` -Jednotlivé ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-453">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="ad1a2-454">`SingleOrg` – Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-454">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="ad1a2-455">`MultiOrg` – Ověřování organizace pro více tenantů.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-455">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="ad1a2-456">`Windows` -Ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-456">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="ad1a2-457">`--aad-b2c-instance <INSTANCE>` -Instanci Azure Active Directory B2C pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-457">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ad1a2-458">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-458">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ad1a2-459">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-459">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="ad1a2-460">`-ssp|--susi-policy-id <ID>` – ID přihlášení a registraci zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-460">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ad1a2-461">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-461">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ad1a2-462">`-rp|--reset-password-policy-id <ID>` -Resetování hesla ID zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-462">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="ad1a2-463">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-463">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ad1a2-464">`-ep|--edit-profile-policy-id <ID>` – Upravit profil zásady ID pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-464">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="ad1a2-465">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-465">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ad1a2-466">`--aad-instance <INSTANCE>` – Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-466">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ad1a2-467">Použití s `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-467">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="ad1a2-468">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-468">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="ad1a2-469">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-469">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="ad1a2-470">Použití s `IndividualB2C`, `SingleOrg`, nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-470">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="ad1a2-471">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-471">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="ad1a2-472">`--domain <DOMAIN>` -Domény tenantu Active directory.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-472">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="ad1a2-473">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-473">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ad1a2-474">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-474">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="ad1a2-475">`--tenant-id <ID>` – ID Tenanta ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-475">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ad1a2-476">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-476">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ad1a2-477">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-477">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="ad1a2-478">`--callback-path <PATH>` -Cestu požadavku v rámci základní cesty aplikace identifikátoru URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-478">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="ad1a2-479">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-479">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ad1a2-480">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-480">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="ad1a2-481">`-r|--org-read-access` – Povolí této aplikaci přístup pro čtení do adresáře.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-481">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="ad1a2-482">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-482">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="ad1a2-483">`--use-launch-settings` -Zahrnuje *launchSettings.json* ve výstupu vygenerovanou šablonu.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-483">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="ad1a2-484">`--use-browserlink` -Obsahuje BrowserLink v projektu.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-484">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="ad1a2-485">`-uld|--use-local-db` : Určuje, že by měl být LocalDB použít místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-485">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ad1a2-486">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-486">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ad1a2-487">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-487">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ad1a2-488">**Stránka**</span><span class="sxs-lookup"><span data-stu-id="ad1a2-488">**page**</span></span>

<span data-ttu-id="ad1a2-489">`-na|--namespace <NAMESPACE_NAME>`-Namespace pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-489">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="ad1a2-490">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-490">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="ad1a2-491">`-np|--no-pagemodel` -Vytvoří danou stránku bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-491">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="ad1a2-492">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="ad1a2-492">**viewimports**</span></span>

<span data-ttu-id="ad1a2-493">`-na|--namespace <NAMESPACE_NAME>`-Namespace pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-493">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="ad1a2-494">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-494">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ad1a2-495">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="ad1a2-495">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="ad1a2-496">**konzola, xunit, mstest, web, webapi**</span><span class="sxs-lookup"><span data-stu-id="ad1a2-496">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="ad1a2-497">`-f|--framework` : Určuje, že [framework](../../standard/frameworks.md) do cíle.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-497">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ad1a2-498">Hodnoty: `netcoreapp1.0` nebo `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-498">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="ad1a2-499">Výchozí hodnota je `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-499">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="ad1a2-500">**classlib**</span><span class="sxs-lookup"><span data-stu-id="ad1a2-500">**classlib**</span></span>

<span data-ttu-id="ad1a2-501">`-f|--framework` : Určuje, že [framework](../../standard/frameworks.md) do cíle.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-501">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ad1a2-502">Hodnoty: `netcoreapp1.0`, `netcoreapp1.1`, nebo `netstandard1.0` k `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-502">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="ad1a2-503">Výchozí hodnota je `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-503">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="ad1a2-504">**mvc**</span><span class="sxs-lookup"><span data-stu-id="ad1a2-504">**mvc**</span></span>

<span data-ttu-id="ad1a2-505">`-f|--framework` : Určuje, že [framework](../../standard/frameworks.md) do cíle.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-505">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ad1a2-506">Hodnoty: `netcoreapp1.0` nebo `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-506">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="ad1a2-507">Výchozí hodnota je `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-507">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="ad1a2-508">`-au|--auth` -Typ ověřování, který má použít.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-508">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="ad1a2-509">Hodnoty: `None` nebo `Individual`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-509">Values: `None` or `Individual`.</span></span> <span data-ttu-id="ad1a2-510">Výchozí hodnota je `None`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-510">The default value is `None`.</span></span>

<span data-ttu-id="ad1a2-511">`-uld|--use-local-db` : Určuje, jestli se mají použít databázi LocalDB místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-511">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="ad1a2-512">Hodnoty: `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-512">Values: `true` or `false`.</span></span> <span data-ttu-id="ad1a2-513">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="ad1a2-513">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="ad1a2-514">Příklady</span><span class="sxs-lookup"><span data-stu-id="ad1a2-514">Examples</span></span>

<span data-ttu-id="ad1a2-515">Vytvoření projektu aplikace konzoly F # v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="ad1a2-515">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="ad1a2-516">Vytvořte projekt knihovny tříd .NET Standard v zadaném adresáři (k dispozici pouze s .NET Core SDK 2.0 a novějšími verzemi):</span><span class="sxs-lookup"><span data-stu-id="ad1a2-516">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="ad1a2-517">Vytvoření nového projektu aplikace ASP.NET Core C# MVC v aktuálním adresáři bez ověřování:</span><span class="sxs-lookup"><span data-stu-id="ad1a2-517">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="ad1a2-518">Vytvořte novou aplikaci xUnit:</span><span class="sxs-lookup"><span data-stu-id="ad1a2-518">Create a new xUnit application:</span></span>

`dotnet new xunit`

<span data-ttu-id="ad1a2-519">Seznam všech šablon, které jsou k dispozici pro rozhraní MVC:</span><span class="sxs-lookup"><span data-stu-id="ad1a2-519">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="ad1a2-520">Instalace verze 2.0 šablon jednostránkové aplikace ASP.NET Core (příkaz Možnosti dostupné pro .NET Core SDK 1.1 a novějších verzích pouze):</span><span class="sxs-lookup"><span data-stu-id="ad1a2-520">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="ad1a2-521">Vytvoření *global.json* v aktuálním adresáři nastavení sady SDK verze 2.0.0 (k dispozici pouze s .NET Core SDK 2.0 a novějšími verzemi):</span><span class="sxs-lookup"><span data-stu-id="ad1a2-521">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="ad1a2-522">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ad1a2-522">See also</span></span>

* [<span data-ttu-id="ad1a2-523">Vlastních šablon pro dotnet nové</span><span class="sxs-lookup"><span data-stu-id="ad1a2-523">Custom templates for dotnet new</span></span>](custom-templates.md)  
* [<span data-ttu-id="ad1a2-524">Vytvoření vlastní šablony pro dotnet new</span><span class="sxs-lookup"><span data-stu-id="ad1a2-524">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
* [<span data-ttu-id="ad1a2-525">úložiště GitHub DotNet/dotnet – šablony – ukázky</span><span class="sxs-lookup"><span data-stu-id="ad1a2-525">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
* [<span data-ttu-id="ad1a2-526">Dostupné šablony pro dotnet nové</span><span class="sxs-lookup"><span data-stu-id="ad1a2-526">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
