---
title: nový příkaz DotNet – rozhraní příkazového řádku .NET Core
description: Vytvoří nový příkaz dotnet nových projektů .NET Core založených na zadané šabloně.
author: mairaw
ms.author: mairaw
ms.date: 07/31/2018
ms.openlocfilehash: 396c4ddf09854fa4582226bdb1422f8c929e459b
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48036127"
---
# <a name="dotnet-new"></a><span data-ttu-id="6ce38-103">nový příkaz DotNet</span><span class="sxs-lookup"><span data-stu-id="6ce38-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="6ce38-104">Název</span><span class="sxs-lookup"><span data-stu-id="6ce38-104">Name</span></span>

<span data-ttu-id="6ce38-105">`dotnet new` -Vytvoří nový projekt, konfigurační soubor nebo řešení založené na zadané šabloně.</span><span class="sxs-lookup"><span data-stu-id="6ce38-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="6ce38-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="6ce38-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="6ce38-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="6ce38-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output]
    [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="6ce38-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="6ce38-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6ce38-109">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="6ce38-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="6ce38-110">Popis</span><span class="sxs-lookup"><span data-stu-id="6ce38-110">Description</span></span>

<span data-ttu-id="6ce38-111">`dotnet new` Příkaz poskytuje pohodlný způsob, jak inicializovat platný projekt .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6ce38-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="6ce38-112">Příkaz volání [modulu šablon](https://github.com/dotnet/templating) vytvořit artefakty na disku na základě určené šablony a možnosti.</span><span class="sxs-lookup"><span data-stu-id="6ce38-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="6ce38-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="6ce38-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="6ce38-114">Šablona pro vytvoření instance při vyvolání příkazu.</span><span class="sxs-lookup"><span data-stu-id="6ce38-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="6ce38-115">Každá šablona může mít specifické možnosti, které lze předat.</span><span class="sxs-lookup"><span data-stu-id="6ce38-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="6ce38-116">Další informace najdete v tématu [možnosti šablony](#template-options).</span><span class="sxs-lookup"><span data-stu-id="6ce38-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="6ce38-117">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="6ce38-117">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="6ce38-118">Příkaz obsahuje výchozí seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="6ce38-118">The command contains a default list of templates.</span></span> <span data-ttu-id="6ce38-119">Použití `dotnet new -l` získat seznam dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="6ce38-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="6ce38-120">V následující tabulce jsou uvedeny šablony, které jsou předinstalovány se sadou .NET Core SDK 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="6ce38-120">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="6ce38-121">Výchozí jazyk šablony se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="6ce38-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="6ce38-122">Popis šablony</span><span class="sxs-lookup"><span data-stu-id="6ce38-122">Template description</span></span>                          | <span data-ttu-id="6ce38-123">Název šablony</span><span class="sxs-lookup"><span data-stu-id="6ce38-123">Template name</span></span>   | <span data-ttu-id="6ce38-124">Jazyky</span><span class="sxs-lookup"><span data-stu-id="6ce38-124">Languages</span></span>     |
|----------------------------------------------|-----------------|---------------|
| <span data-ttu-id="6ce38-125">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="6ce38-125">Console application</span></span>                          | `console`       | <span data-ttu-id="6ce38-126">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="6ce38-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="6ce38-127">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="6ce38-127">Class library</span></span>                                | `classlib`      | <span data-ttu-id="6ce38-128">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="6ce38-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="6ce38-129">Projekt testu jednotek</span><span class="sxs-lookup"><span data-stu-id="6ce38-129">Unit test project</span></span>                            | `mstest`        | <span data-ttu-id="6ce38-130">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="6ce38-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="6ce38-131">Projekt testů xUnit</span><span class="sxs-lookup"><span data-stu-id="6ce38-131">xUnit test project</span></span>                           | `xunit`         | <span data-ttu-id="6ce38-132">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="6ce38-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="6ce38-133">Stránka Razor</span><span class="sxs-lookup"><span data-stu-id="6ce38-133">Razor page</span></span>                                   | `page`          | <span data-ttu-id="6ce38-134">[C#]</span><span class="sxs-lookup"><span data-stu-id="6ce38-134">[C#]</span></span>          |
| <span data-ttu-id="6ce38-135">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="6ce38-135">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="6ce38-136">[C#]</span><span class="sxs-lookup"><span data-stu-id="6ce38-136">[C#]</span></span>          |
| <span data-ttu-id="6ce38-137">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="6ce38-137">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="6ce38-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="6ce38-138">[C#]</span></span>          |
| <span data-ttu-id="6ce38-139">ASP.NET Core je prázdný</span><span class="sxs-lookup"><span data-stu-id="6ce38-139">ASP.NET Core empty</span></span>                           | `web`           | <span data-ttu-id="6ce38-140">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="6ce38-140">[C#], F#</span></span>      |
| <span data-ttu-id="6ce38-141">Webové aplikace ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="6ce38-141">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="6ce38-142">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="6ce38-142">[C#], F#</span></span>      |
| <span data-ttu-id="6ce38-143">Webové aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6ce38-143">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="6ce38-144">[C#]</span><span class="sxs-lookup"><span data-stu-id="6ce38-144">[C#]</span></span>          |
| <span data-ttu-id="6ce38-145">ASP.NET Core pomocí Angular</span><span class="sxs-lookup"><span data-stu-id="6ce38-145">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="6ce38-146">[C#]</span><span class="sxs-lookup"><span data-stu-id="6ce38-146">[C#]</span></span>          |
| <span data-ttu-id="6ce38-147">ASP.NET Core pomocí React.js</span><span class="sxs-lookup"><span data-stu-id="6ce38-147">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="6ce38-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="6ce38-148">[C#]</span></span>          |
| <span data-ttu-id="6ce38-149">ASP.NET Core pomocí React.js a Redux</span><span class="sxs-lookup"><span data-stu-id="6ce38-149">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="6ce38-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="6ce38-150">[C#]</span></span>          |
| <span data-ttu-id="6ce38-151">Webové rozhraní API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6ce38-151">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="6ce38-152">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="6ce38-152">[C#], F#</span></span>      |
| <span data-ttu-id="6ce38-153">Knihovny tříd Razor</span><span class="sxs-lookup"><span data-stu-id="6ce38-153">Razor class library</span></span>                          | `razorclasslib` | <span data-ttu-id="6ce38-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="6ce38-154">[C#]</span></span>          |
| <span data-ttu-id="6ce38-155">soubor Global.JSON</span><span class="sxs-lookup"><span data-stu-id="6ce38-155">global.json file</span></span>                             | `globaljson`    |               |
| <span data-ttu-id="6ce38-156">NuGet config</span><span class="sxs-lookup"><span data-stu-id="6ce38-156">NuGet config</span></span>                                 | `nugetconfig`   |               |
| <span data-ttu-id="6ce38-157">Webové konfigurace</span><span class="sxs-lookup"><span data-stu-id="6ce38-157">Web config</span></span>                                   | `webconfig`     |               |
| <span data-ttu-id="6ce38-158">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="6ce38-158">Solution file</span></span>                                | `sln`           |               |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="6ce38-159">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="6ce38-159">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="6ce38-160">Příkaz obsahuje výchozí seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="6ce38-160">The command contains a default list of templates.</span></span> <span data-ttu-id="6ce38-161">Použití `dotnet new -l` získat seznam dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="6ce38-161">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="6ce38-162">V následující tabulce jsou uvedeny šablony, které jsou předem nainstalované s .NET Core SDK 2.0.</span><span class="sxs-lookup"><span data-stu-id="6ce38-162">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.</span></span> <span data-ttu-id="6ce38-163">Výchozí jazyk šablony se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="6ce38-163">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="6ce38-164">Popis šablony</span><span class="sxs-lookup"><span data-stu-id="6ce38-164">Template description</span></span>                          | <span data-ttu-id="6ce38-165">Název šablony</span><span class="sxs-lookup"><span data-stu-id="6ce38-165">Template name</span></span> | <span data-ttu-id="6ce38-166">Jazyky</span><span class="sxs-lookup"><span data-stu-id="6ce38-166">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="6ce38-167">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="6ce38-167">Console application</span></span>                          | `console`     | <span data-ttu-id="6ce38-168">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="6ce38-168">[C#], F#, VB</span></span>  |
| <span data-ttu-id="6ce38-169">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="6ce38-169">Class library</span></span>                                | `classlib`    | <span data-ttu-id="6ce38-170">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="6ce38-170">[C#], F#, VB</span></span>  |
| <span data-ttu-id="6ce38-171">Projekt testu jednotek</span><span class="sxs-lookup"><span data-stu-id="6ce38-171">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="6ce38-172">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="6ce38-172">[C#], F#, VB</span></span>  |
| <span data-ttu-id="6ce38-173">Projekt testů xUnit</span><span class="sxs-lookup"><span data-stu-id="6ce38-173">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="6ce38-174">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="6ce38-174">[C#], F#, VB</span></span>  |
| <span data-ttu-id="6ce38-175">ASP.NET Core je prázdný</span><span class="sxs-lookup"><span data-stu-id="6ce38-175">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="6ce38-176">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="6ce38-176">[C#], F#</span></span>      |
| <span data-ttu-id="6ce38-177">Webové aplikace ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="6ce38-177">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="6ce38-178">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="6ce38-178">[C#], F#</span></span>      |
| <span data-ttu-id="6ce38-179">Webové aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6ce38-179">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="6ce38-180">[C#]</span><span class="sxs-lookup"><span data-stu-id="6ce38-180">[C#]</span></span>          |
| <span data-ttu-id="6ce38-181">ASP.NET Core pomocí Angular</span><span class="sxs-lookup"><span data-stu-id="6ce38-181">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="6ce38-182">[C#]</span><span class="sxs-lookup"><span data-stu-id="6ce38-182">[C#]</span></span>          |
| <span data-ttu-id="6ce38-183">ASP.NET Core pomocí React.js</span><span class="sxs-lookup"><span data-stu-id="6ce38-183">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="6ce38-184">[C#]</span><span class="sxs-lookup"><span data-stu-id="6ce38-184">[C#]</span></span>          |
| <span data-ttu-id="6ce38-185">ASP.NET Core pomocí React.js a Redux</span><span class="sxs-lookup"><span data-stu-id="6ce38-185">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="6ce38-186">[C#]</span><span class="sxs-lookup"><span data-stu-id="6ce38-186">[C#]</span></span>          |
| <span data-ttu-id="6ce38-187">Webové rozhraní API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6ce38-187">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="6ce38-188">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="6ce38-188">[C#], F#</span></span>      |
| <span data-ttu-id="6ce38-189">soubor Global.JSON</span><span class="sxs-lookup"><span data-stu-id="6ce38-189">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="6ce38-190">NuGet config</span><span class="sxs-lookup"><span data-stu-id="6ce38-190">NuGet config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="6ce38-191">Webové konfigurace</span><span class="sxs-lookup"><span data-stu-id="6ce38-191">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="6ce38-192">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="6ce38-192">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="6ce38-193">Stránka Razor</span><span class="sxs-lookup"><span data-stu-id="6ce38-193">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="6ce38-194">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="6ce38-194">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="6ce38-195">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="6ce38-195">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6ce38-196">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="6ce38-196">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="6ce38-197">Příkaz obsahuje výchozí seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="6ce38-197">The command contains a default list of templates.</span></span> <span data-ttu-id="6ce38-198">Použití `dotnet new -all` získat seznam dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="6ce38-198">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="6ce38-199">V následující tabulce jsou uvedeny šablony, které jsou předinstalovány se sadou SDK .NET Core 1.x.</span><span class="sxs-lookup"><span data-stu-id="6ce38-199">The following table shows the templates that come pre-installed with the .NET Core SDK 1.x.</span></span> <span data-ttu-id="6ce38-200">Výchozí jazyk šablony se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="6ce38-200">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="6ce38-201">Popis šablony</span><span class="sxs-lookup"><span data-stu-id="6ce38-201">Template description</span></span>  | <span data-ttu-id="6ce38-202">Název šablony</span><span class="sxs-lookup"><span data-stu-id="6ce38-202">Template name</span></span> | <span data-ttu-id="6ce38-203">Jazyky</span><span class="sxs-lookup"><span data-stu-id="6ce38-203">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="6ce38-204">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="6ce38-204">Console application</span></span>  | `console`     | <span data-ttu-id="6ce38-205">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="6ce38-205">[C#], F#</span></span>  |
| <span data-ttu-id="6ce38-206">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="6ce38-206">Class library</span></span>        | `classlib`    | <span data-ttu-id="6ce38-207">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="6ce38-207">[C#], F#</span></span>  |
| <span data-ttu-id="6ce38-208">Projekt testu jednotek</span><span class="sxs-lookup"><span data-stu-id="6ce38-208">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="6ce38-209">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="6ce38-209">[C#], F#</span></span>  |
| <span data-ttu-id="6ce38-210">Projekt testů xUnit</span><span class="sxs-lookup"><span data-stu-id="6ce38-210">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="6ce38-211">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="6ce38-211">[C#], F#</span></span>  |
| <span data-ttu-id="6ce38-212">ASP.NET Core je prázdný</span><span class="sxs-lookup"><span data-stu-id="6ce38-212">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="6ce38-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="6ce38-213">[C#]</span></span>      |
| <span data-ttu-id="6ce38-214">Webové aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6ce38-214">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="6ce38-215">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="6ce38-215">[C#], F#</span></span>  |
| <span data-ttu-id="6ce38-216">Webové rozhraní API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6ce38-216">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="6ce38-217">[C#]</span><span class="sxs-lookup"><span data-stu-id="6ce38-217">[C#]</span></span>      |
| <span data-ttu-id="6ce38-218">NuGet config</span><span class="sxs-lookup"><span data-stu-id="6ce38-218">NuGet config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="6ce38-219">Webové konfigurace</span><span class="sxs-lookup"><span data-stu-id="6ce38-219">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="6ce38-220">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="6ce38-220">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="6ce38-221">Možnosti</span><span class="sxs-lookup"><span data-stu-id="6ce38-221">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="6ce38-222">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="6ce38-222">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="6ce38-223">Vynutí obsahu chcete vygenerovat i v případě, že by došlo ke změně existujících souborů.</span><span class="sxs-lookup"><span data-stu-id="6ce38-223">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="6ce38-224">To je potřeba při výstupní adresář již obsahuje projekt.</span><span class="sxs-lookup"><span data-stu-id="6ce38-224">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="6ce38-225">Vytiskne nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="6ce38-225">Prints out help for the command.</span></span> <span data-ttu-id="6ce38-226">Může být vyvolána pro `dotnet new` samotný příkaz nebo pro všechny šablony, jako například `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-226">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="6ce38-227">Nainstaluje zdroj nebo šablony pack z `PATH` nebo `NUGET_ID` k dispozici.</span><span class="sxs-lookup"><span data-stu-id="6ce38-227">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="6ce38-228">Pokud chcete nainstalovat zkušební verzi balíčku šablony, je třeba zadat verzi ve formátu `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-228">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="6ce38-229">Ve výchozím nastavení `dotnet new` předá \* pro verzi, která představuje poslední stabilní balíček verze.</span><span class="sxs-lookup"><span data-stu-id="6ce38-229">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="6ce38-230">Podívejte se příklad na [příklady](#examples) oddílu.</span><span class="sxs-lookup"><span data-stu-id="6ce38-230">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="6ce38-231">Informace o vytváření vlastních šablon najdete v tématu [vlastních šablon pro dotnet nové](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="6ce38-231">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="6ce38-232">Zobrazí seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="6ce38-232">Lists templates containing the specified name.</span></span> <span data-ttu-id="6ce38-233">Pokud je vyvolána `dotnet new` příkazu, uvádí možné šablony, které jsou k dispozici pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="6ce38-233">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="6ce38-234">Například pokud adresář, projekt již obsahuje, neobsahuje všechny šablony projektů.</span><span class="sxs-lookup"><span data-stu-id="6ce38-234">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="6ce38-235">Jazyk šablony k vytvoření.</span><span class="sxs-lookup"><span data-stu-id="6ce38-235">The language of the template to create.</span></span> <span data-ttu-id="6ce38-236">Jazyk přijato, se liší podle šablony (Zobrazit výchozí hodnoty v [argumenty](#arguments) části).</span><span class="sxs-lookup"><span data-stu-id="6ce38-236">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="6ce38-237">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="6ce38-237">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="6ce38-238">Některé součásti pro interpretaci `#` jako speciální znak.</span><span class="sxs-lookup"><span data-stu-id="6ce38-238">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="6ce38-239">V takových případech bude nutné uvést hodnotu parametru jazyka, jako `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-239">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="6ce38-240">Název pro výstup vytvořený.</span><span class="sxs-lookup"><span data-stu-id="6ce38-240">The name for the created output.</span></span> <span data-ttu-id="6ce38-241">Pokud není zadán žádný název, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="6ce38-241">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="6ce38-242">Určuje zdroj NuGet, který chcete použít během instalace.</span><span class="sxs-lookup"><span data-stu-id="6ce38-242">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="6ce38-243">Umístění pro vygenerovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="6ce38-243">Location to place the generated output.</span></span> <span data-ttu-id="6ce38-244">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="6ce38-244">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="6ce38-245">Vyfiltruje šablony podle dostupných typů.</span><span class="sxs-lookup"><span data-stu-id="6ce38-245">Filters templates based on available types.</span></span> <span data-ttu-id="6ce38-246">Předdefinované hodnoty jsou "projekt", "item" nebo "jiné".</span><span class="sxs-lookup"><span data-stu-id="6ce38-246">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="6ce38-247">Odinstaluje zdroj nebo šablony pack na `PATH` nebo `NUGET_ID` k dispozici.</span><span class="sxs-lookup"><span data-stu-id="6ce38-247">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="6ce38-248">Chcete-li odinstalovat sadu pomocí šablony `PATH`, budete potřebovat plně kvalifikovanou cestu.</span><span class="sxs-lookup"><span data-stu-id="6ce38-248">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="6ce38-249">Například *C:/uživatele/\<uživatele > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z obsahuje složky nebudou.</span><span class="sxs-lookup"><span data-stu-id="6ce38-249">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="6ce38-250">Kromě toho nesmí být znak konečné ukončující znak lomítka adresáře na cestu k šabloně.</span><span class="sxs-lookup"><span data-stu-id="6ce38-250">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="6ce38-251">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="6ce38-251">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="6ce38-252">Vynutí obsahu chcete vygenerovat i v případě, že by došlo ke změně existujících souborů.</span><span class="sxs-lookup"><span data-stu-id="6ce38-252">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="6ce38-253">To je potřeba při výstupní adresář již obsahuje projekt.</span><span class="sxs-lookup"><span data-stu-id="6ce38-253">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="6ce38-254">Vytiskne nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="6ce38-254">Prints out help for the command.</span></span> <span data-ttu-id="6ce38-255">Může být vyvolána pro `dotnet new` samotný příkaz nebo pro všechny šablony, jako například `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-255">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="6ce38-256">Nainstaluje zdroj nebo šablony pack z `PATH` nebo `NUGET_ID` k dispozici.</span><span class="sxs-lookup"><span data-stu-id="6ce38-256">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="6ce38-257">Pokud chcete nainstalovat zkušební verzi balíčku šablony, je třeba zadat verzi ve formátu `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-257">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="6ce38-258">Ve výchozím nastavení `dotnet new` předá \* pro verzi, která představuje poslední stabilní balíček verze.</span><span class="sxs-lookup"><span data-stu-id="6ce38-258">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="6ce38-259">Podívejte se příklad na [příklady](#examples) oddílu.</span><span class="sxs-lookup"><span data-stu-id="6ce38-259">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="6ce38-260">Informace o vytváření vlastních šablon najdete v tématu [vlastních šablon pro dotnet nové](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="6ce38-260">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="6ce38-261">Zobrazí seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="6ce38-261">Lists templates containing the specified name.</span></span> <span data-ttu-id="6ce38-262">Pokud je vyvolána `dotnet new` příkazu, uvádí možné šablony, které jsou k dispozici pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="6ce38-262">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="6ce38-263">Například pokud adresář, projekt již obsahuje, neobsahuje všechny šablony projektů.</span><span class="sxs-lookup"><span data-stu-id="6ce38-263">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="6ce38-264">Jazyk šablony k vytvoření.</span><span class="sxs-lookup"><span data-stu-id="6ce38-264">The language of the template to create.</span></span> <span data-ttu-id="6ce38-265">Jazyk přijato, se liší podle šablony (Zobrazit výchozí hodnoty v [argumenty](#arguments) části).</span><span class="sxs-lookup"><span data-stu-id="6ce38-265">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="6ce38-266">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="6ce38-266">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="6ce38-267">Některé součásti pro interpretaci `#` jako speciální znak.</span><span class="sxs-lookup"><span data-stu-id="6ce38-267">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="6ce38-268">V takových případech bude nutné uvést hodnotu parametru jazyka, jako `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-268">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="6ce38-269">Název pro výstup vytvořený.</span><span class="sxs-lookup"><span data-stu-id="6ce38-269">The name for the created output.</span></span> <span data-ttu-id="6ce38-270">Pokud není zadán žádný název, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="6ce38-270">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="6ce38-271">Umístění pro vygenerovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="6ce38-271">Location to place the generated output.</span></span> <span data-ttu-id="6ce38-272">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="6ce38-272">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="6ce38-273">Vyfiltruje šablony podle dostupných typů.</span><span class="sxs-lookup"><span data-stu-id="6ce38-273">Filters templates based on available types.</span></span> <span data-ttu-id="6ce38-274">Předdefinované hodnoty jsou "projekt", "item" nebo "jiné".</span><span class="sxs-lookup"><span data-stu-id="6ce38-274">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="6ce38-275">Odinstaluje zdroj nebo šablony pack na `PATH` nebo `NUGET_ID` k dispozici.</span><span class="sxs-lookup"><span data-stu-id="6ce38-275">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="6ce38-276">Odinstalace pomocí zdroj `PATH`, budete potřebovat plně kvalifikovanou cestu.</span><span class="sxs-lookup"><span data-stu-id="6ce38-276">To uninstall a template using a source `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="6ce38-277">Například *C:/uživatele/\<uživatele > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z obsahuje složky nebudou.</span><span class="sxs-lookup"><span data-stu-id="6ce38-277">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span> <span data-ttu-id="6ce38-278">Kromě toho nesmí být znak konečné ukončující znak lomítka adresáře na cestu k šabloně.</span><span class="sxs-lookup"><span data-stu-id="6ce38-278">Additionally, do not include a final terminating directory slash on your template path.</span></span>
> 
> <span data-ttu-id="6ce38-279">Pokud se nemůžete určit `PATH` nebo `NUGET_ID` argumentů potřebných k odinstalaci šablonu s `dotnet new --uninstall` bez argumentu zobrazí seznam všech nainstalovaných šablon a argument nutné je odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="6ce38-279">If you are unable to determine the `PATH` or `NUGET_ID` argument needed to uninstall a template, running `dotnet new --uninstall` without an argument will list all installed templates and the argument required to uninstall them.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6ce38-280">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="6ce38-280">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="6ce38-281">Zobrazí všechny šablony pro konkrétní typ projektu při spuštění v kontextu `dotnet new` samotný příkaz.</span><span class="sxs-lookup"><span data-stu-id="6ce38-281">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="6ce38-282">Při spuštění v kontextu konkrétní šablony, jako například `dotnet new web -all`, `-all` je interpretován jako vytvoření příznak force.</span><span class="sxs-lookup"><span data-stu-id="6ce38-282">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="6ce38-283">To je potřeba při výstupní adresář již obsahuje projekt.</span><span class="sxs-lookup"><span data-stu-id="6ce38-283">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="6ce38-284">Vytiskne nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="6ce38-284">Prints out help for the command.</span></span> <span data-ttu-id="6ce38-285">Může být vyvolána pro `dotnet new` samotný příkaz nebo pro všechny šablony, jako například `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-285">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="6ce38-286">Zobrazí seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="6ce38-286">Lists templates containing the specified name.</span></span> <span data-ttu-id="6ce38-287">Pokud je vyvolána `dotnet new` příkazu, uvádí možné šablony, které jsou k dispozici pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="6ce38-287">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="6ce38-288">Například pokud adresář, projekt již obsahuje, neobsahuje všechny šablony projektů.</span><span class="sxs-lookup"><span data-stu-id="6ce38-288">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="6ce38-289">Jazyk šablony k vytvoření.</span><span class="sxs-lookup"><span data-stu-id="6ce38-289">The language of the template to create.</span></span> <span data-ttu-id="6ce38-290">Jazyk přijato, se liší podle šablony (Zobrazit výchozí hodnoty v [argumenty](#arguments) části).</span><span class="sxs-lookup"><span data-stu-id="6ce38-290">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="6ce38-291">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="6ce38-291">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="6ce38-292">Některé součásti pro interpretaci `#` jako speciální znak.</span><span class="sxs-lookup"><span data-stu-id="6ce38-292">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="6ce38-293">V takových případech bude nutné uvést hodnotu parametru jazyka, jako `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-293">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="6ce38-294">Název pro výstup vytvořený.</span><span class="sxs-lookup"><span data-stu-id="6ce38-294">The name for the created output.</span></span> <span data-ttu-id="6ce38-295">Pokud není zadán žádný název, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="6ce38-295">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="6ce38-296">Umístění pro vygenerovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="6ce38-296">Location to place the generated output.</span></span> <span data-ttu-id="6ce38-297">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="6ce38-297">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="6ce38-298">Nastavení šablony</span><span class="sxs-lookup"><span data-stu-id="6ce38-298">Template options</span></span>

<span data-ttu-id="6ce38-299">Každá šablona projektu může mít k dispozici další možnosti.</span><span class="sxs-lookup"><span data-stu-id="6ce38-299">Each project template may have additional options available.</span></span> <span data-ttu-id="6ce38-300">Základní šablony mají následující další možnosti:</span><span class="sxs-lookup"><span data-stu-id="6ce38-300">The core templates have the following additional options:</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="6ce38-301">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="6ce38-301">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="6ce38-302">**konzola, angular, react, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="6ce38-302">**console, angular, react, reactredux, razorclasslib**</span></span>

  <span data-ttu-id="6ce38-303">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="6ce38-303">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6ce38-304">**classlib**</span><span class="sxs-lookup"><span data-stu-id="6ce38-304">**classlib**</span></span>

<span data-ttu-id="6ce38-305">`-f|--framework <FRAMEWORK>` : Určuje, že [framework](../../standard/frameworks.md) do cíle.</span><span class="sxs-lookup"><span data-stu-id="6ce38-305">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6ce38-306">Hodnoty: `netcoreapp2.0` k vytvoření knihovny tříd .NET Core nebo `netstandard2.0` k vytvoření knihovny tříd .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="6ce38-306">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="6ce38-307">Výchozí hodnota je `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-307">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="6ce38-308">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="6ce38-308">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6ce38-309">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="6ce38-309">**mstest, xunit**</span></span>

<span data-ttu-id="6ce38-310">`-p|--enable-pack` – Povolí balení pro projekt pomocí [balíčku dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="6ce38-310">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="6ce38-311">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="6ce38-311">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6ce38-312">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="6ce38-312">**globaljson**</span></span>

<span data-ttu-id="6ce38-313">`--sdk-version <VERSION_NUMBER>` : Určuje verzi .NET Core SDK pro použití v *global.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="6ce38-313">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="6ce38-314">**web**</span><span class="sxs-lookup"><span data-stu-id="6ce38-314">**web**</span></span>

<span data-ttu-id="6ce38-315">`--exclude-launch-settings` -Vyloučení *launchSettings.json* z vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="6ce38-315">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="6ce38-316">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="6ce38-316">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6ce38-317">`--no-https` -Projektu nebude vyžadovat protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6ce38-317">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="6ce38-318">Tato možnost platí, pouze pokud `IndividualAuth` nebo `OrganizationalAuth` nejsou používány.</span><span class="sxs-lookup"><span data-stu-id="6ce38-318">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="6ce38-319">**webapi**</span><span class="sxs-lookup"><span data-stu-id="6ce38-319">**webapi**</span></span>

<span data-ttu-id="6ce38-320">`-au|--auth <AUTHENTICATION_TYPE>` -Typ ověřování, který má použít.</span><span class="sxs-lookup"><span data-stu-id="6ce38-320">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="6ce38-321">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="6ce38-321">The possible values are:</span></span>

- <span data-ttu-id="6ce38-322">`None` -Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="6ce38-322">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="6ce38-323">`IndividualB2C` -Jednotlivé ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="6ce38-323">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="6ce38-324">`SingleOrg` – Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="6ce38-324">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="6ce38-325">`Windows` -Ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="6ce38-325">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="6ce38-326">`--aad-b2c-instance <INSTANCE>` -Instanci Azure Active Directory B2C pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="6ce38-326">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="6ce38-327">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-327">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="6ce38-328">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-328">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="6ce38-329">`-ssp|--susi-policy-id <ID>` – ID přihlášení a registraci zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="6ce38-329">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="6ce38-330">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-330">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6ce38-331">`--aad-instance <INSTANCE>` – Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="6ce38-331">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="6ce38-332">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-332">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="6ce38-333">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-333">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="6ce38-334">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="6ce38-334">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="6ce38-335">Použití s `IndividualB2C` nebo `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-335">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="6ce38-336">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-336">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="6ce38-337">`--domain <DOMAIN>` -Domény tenantu Active directory.</span><span class="sxs-lookup"><span data-stu-id="6ce38-337">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="6ce38-338">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-338">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="6ce38-339">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-339">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="6ce38-340">`--tenant-id <ID>` – ID Tenanta ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="6ce38-340">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="6ce38-341">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-341">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="6ce38-342">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-342">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="6ce38-343">`-r|--org-read-access` – Povolí této aplikaci přístup pro čtení do adresáře.</span><span class="sxs-lookup"><span data-stu-id="6ce38-343">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="6ce38-344">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-344">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="6ce38-345">`--exclude-launch-settings` -Vyloučení *launchSettings.json* z vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="6ce38-345">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="6ce38-346">`-uld|--use-local-db` : Určuje, že by měl být LocalDB použít místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="6ce38-346">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="6ce38-347">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-347">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6ce38-348">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="6ce38-348">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6ce38-349">`--no-https` -Projektu nebude vyžadovat protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6ce38-349">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="6ce38-350">`app.UseHsts` a `app.UseHttpsRedirection` nejsou přidány do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-350">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="6ce38-351">Tato možnost platí, pouze pokud `Individual`, `IndividualB2C`, `SingleOrg`, nebo `MultiOrg` nejsou používány.</span><span class="sxs-lookup"><span data-stu-id="6ce38-351">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="6ce38-352">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="6ce38-352">**mvc, razor**</span></span>

<span data-ttu-id="6ce38-353">`-au|--auth <AUTHENTICATION_TYPE>` -Typ ověřování, který má použít.</span><span class="sxs-lookup"><span data-stu-id="6ce38-353">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="6ce38-354">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="6ce38-354">The possible values are:</span></span>

- <span data-ttu-id="6ce38-355">`None` -Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="6ce38-355">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="6ce38-356">`Individual` -Jednotlivé ověřování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-356">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="6ce38-357">`IndividualB2C` -Jednotlivé ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="6ce38-357">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="6ce38-358">`SingleOrg` – Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="6ce38-358">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="6ce38-359">`MultiOrg` – Ověřování organizace pro více tenantů.</span><span class="sxs-lookup"><span data-stu-id="6ce38-359">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="6ce38-360">`Windows` -Ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="6ce38-360">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="6ce38-361">`--aad-b2c-instance <INSTANCE>` -Instanci Azure Active Directory B2C pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="6ce38-361">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="6ce38-362">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-362">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="6ce38-363">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-363">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="6ce38-364">`-ssp|--susi-policy-id <ID>` – ID přihlášení a registraci zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="6ce38-364">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="6ce38-365">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-365">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6ce38-366">`-rp|--reset-password-policy-id <ID>` -Resetování hesla ID zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="6ce38-366">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="6ce38-367">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-367">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6ce38-368">`-ep|--edit-profile-policy-id <ID>` – Upravit profil zásady ID pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="6ce38-368">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="6ce38-369">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-369">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6ce38-370">`--aad-instance <INSTANCE>` – Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="6ce38-370">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="6ce38-371">Použití s `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-371">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="6ce38-372">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-372">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="6ce38-373">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="6ce38-373">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="6ce38-374">Použití s `IndividualB2C`, `SingleOrg`, nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-374">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="6ce38-375">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-375">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="6ce38-376">`--domain <DOMAIN>` -Domény tenantu Active directory.</span><span class="sxs-lookup"><span data-stu-id="6ce38-376">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="6ce38-377">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-377">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="6ce38-378">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-378">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="6ce38-379">`--tenant-id <ID>` – ID Tenanta ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="6ce38-379">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="6ce38-380">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-380">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="6ce38-381">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-381">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="6ce38-382">`--callback-path <PATH>` -Cestu požadavku v rámci základní cesty aplikace identifikátoru URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-382">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="6ce38-383">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-383">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="6ce38-384">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-384">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="6ce38-385">`-r|--org-read-access` – Povolí této aplikaci přístup pro čtení do adresáře.</span><span class="sxs-lookup"><span data-stu-id="6ce38-385">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="6ce38-386">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-386">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="6ce38-387">`--exclude-launch-settings` -Vyloučení *launchSettings.json* z vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="6ce38-387">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="6ce38-388">`--use-browserlink` -Obsahuje BrowserLink v projektu.</span><span class="sxs-lookup"><span data-stu-id="6ce38-388">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="6ce38-389">`-uld|--use-local-db` : Určuje, že by měl být LocalDB použít místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="6ce38-389">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="6ce38-390">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-390">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6ce38-391">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="6ce38-391">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6ce38-392">`--no-https` -Projektu nebude vyžadovat protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6ce38-392">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="6ce38-393">`app.UseHsts` a `app.UseHttpsRedirection` nejsou přidány do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-393">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="6ce38-394">Tato možnost platí, pouze pokud `Individual`, `IndividualB2C`, `SingleOrg`, nebo `MultiOrg` nejsou používány.</span><span class="sxs-lookup"><span data-stu-id="6ce38-394">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="6ce38-395">**Stránka**</span><span class="sxs-lookup"><span data-stu-id="6ce38-395">**page**</span></span>

<span data-ttu-id="6ce38-396">`-na|--namespace <NAMESPACE_NAME>`-Namespace pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="6ce38-396">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="6ce38-397">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-397">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="6ce38-398">`-np|--no-pagemodel` -Vytvoří danou stránku bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="6ce38-398">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="6ce38-399">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="6ce38-399">**viewimports**</span></span>

<span data-ttu-id="6ce38-400">`-na|--namespace <NAMESPACE_NAME>`-Namespace pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="6ce38-400">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="6ce38-401">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-401">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="6ce38-402">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="6ce38-402">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="6ce38-403">**konzola, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="6ce38-403">**console, angular, react, reactredux**</span></span>

  <span data-ttu-id="6ce38-404">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="6ce38-404">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6ce38-405">**classlib**</span><span class="sxs-lookup"><span data-stu-id="6ce38-405">**classlib**</span></span>

<span data-ttu-id="6ce38-406">`-f|--framework <FRAMEWORK>` : Určuje, že [framework](../../standard/frameworks.md) do cíle.</span><span class="sxs-lookup"><span data-stu-id="6ce38-406">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6ce38-407">Hodnoty: `netcoreapp2.0` k vytvoření knihovny tříd .NET Core nebo `netstandard2.0` k vytvoření knihovny tříd .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="6ce38-407">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="6ce38-408">Výchozí hodnota je `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-408">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="6ce38-409">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="6ce38-409">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6ce38-410">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="6ce38-410">**mstest, xunit**</span></span>

<span data-ttu-id="6ce38-411">`-p|--enable-pack` – Povolí balení pro projekt pomocí [balíčku dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="6ce38-411">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="6ce38-412">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="6ce38-412">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6ce38-413">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="6ce38-413">**globaljson**</span></span>

<span data-ttu-id="6ce38-414">`--sdk-version <VERSION_NUMBER>` : Určuje verzi .NET Core SDK pro použití v *global.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="6ce38-414">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="6ce38-415">**web**</span><span class="sxs-lookup"><span data-stu-id="6ce38-415">**web**</span></span>

<span data-ttu-id="6ce38-416">`--use-launch-settings` -Zahrnuje *launchSettings.json* ve výstupu vygenerovanou šablonu.</span><span class="sxs-lookup"><span data-stu-id="6ce38-416">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="6ce38-417">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="6ce38-417">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6ce38-418">**webapi**</span><span class="sxs-lookup"><span data-stu-id="6ce38-418">**webapi**</span></span>

<span data-ttu-id="6ce38-419">`-au|--auth <AUTHENTICATION_TYPE>` -Typ ověřování, který má použít.</span><span class="sxs-lookup"><span data-stu-id="6ce38-419">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="6ce38-420">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="6ce38-420">The possible values are:</span></span>

- <span data-ttu-id="6ce38-421">`None` -Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="6ce38-421">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="6ce38-422">`IndividualB2C` -Jednotlivé ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="6ce38-422">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="6ce38-423">`SingleOrg` – Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="6ce38-423">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="6ce38-424">`Windows` -Ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="6ce38-424">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="6ce38-425">`--aad-b2c-instance <INSTANCE>` -Instanci Azure Active Directory B2C pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="6ce38-425">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="6ce38-426">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-426">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="6ce38-427">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-427">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="6ce38-428">`-ssp|--susi-policy-id <ID>` – ID přihlášení a registraci zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="6ce38-428">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="6ce38-429">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-429">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6ce38-430">`--aad-instance <INSTANCE>` – Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="6ce38-430">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="6ce38-431">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-431">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="6ce38-432">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-432">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="6ce38-433">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="6ce38-433">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="6ce38-434">Použití s `IndividualB2C` nebo `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-434">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="6ce38-435">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-435">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="6ce38-436">`--domain <DOMAIN>` -Domény tenantu Active directory.</span><span class="sxs-lookup"><span data-stu-id="6ce38-436">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="6ce38-437">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-437">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="6ce38-438">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-438">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="6ce38-439">`--tenant-id <ID>` – ID Tenanta ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="6ce38-439">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="6ce38-440">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-440">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="6ce38-441">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-441">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="6ce38-442">`-r|--org-read-access` – Povolí této aplikaci přístup pro čtení do adresáře.</span><span class="sxs-lookup"><span data-stu-id="6ce38-442">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="6ce38-443">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-443">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="6ce38-444">`--use-launch-settings` -Zahrnuje *launchSettings.json* ve výstupu vygenerovanou šablonu.</span><span class="sxs-lookup"><span data-stu-id="6ce38-444">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="6ce38-445">`-uld|--use-local-db` : Určuje, že by měl být LocalDB použít místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="6ce38-445">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="6ce38-446">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-446">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6ce38-447">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="6ce38-447">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6ce38-448">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="6ce38-448">**mvc, razor**</span></span>

<span data-ttu-id="6ce38-449">`-au|--auth <AUTHENTICATION_TYPE>` -Typ ověřování, který má použít.</span><span class="sxs-lookup"><span data-stu-id="6ce38-449">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="6ce38-450">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="6ce38-450">The possible values are:</span></span>

- <span data-ttu-id="6ce38-451">`None` -Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="6ce38-451">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="6ce38-452">`Individual` -Jednotlivé ověřování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-452">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="6ce38-453">`IndividualB2C` -Jednotlivé ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="6ce38-453">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="6ce38-454">`SingleOrg` – Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="6ce38-454">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="6ce38-455">`MultiOrg` – Ověřování organizace pro více tenantů.</span><span class="sxs-lookup"><span data-stu-id="6ce38-455">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="6ce38-456">`Windows` -Ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="6ce38-456">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="6ce38-457">`--aad-b2c-instance <INSTANCE>` -Instanci Azure Active Directory B2C pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="6ce38-457">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="6ce38-458">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-458">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="6ce38-459">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-459">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="6ce38-460">`-ssp|--susi-policy-id <ID>` – ID přihlášení a registraci zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="6ce38-460">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="6ce38-461">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-461">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6ce38-462">`-rp|--reset-password-policy-id <ID>` -Resetování hesla ID zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="6ce38-462">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="6ce38-463">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-463">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6ce38-464">`-ep|--edit-profile-policy-id <ID>` – Upravit profil zásady ID pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="6ce38-464">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="6ce38-465">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-465">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6ce38-466">`--aad-instance <INSTANCE>` – Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="6ce38-466">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="6ce38-467">Použití s `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-467">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="6ce38-468">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-468">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="6ce38-469">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="6ce38-469">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="6ce38-470">Použití s `IndividualB2C`, `SingleOrg`, nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-470">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="6ce38-471">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-471">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="6ce38-472">`--domain <DOMAIN>` -Domény tenantu Active directory.</span><span class="sxs-lookup"><span data-stu-id="6ce38-472">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="6ce38-473">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-473">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="6ce38-474">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-474">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="6ce38-475">`--tenant-id <ID>` – ID Tenanta ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="6ce38-475">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="6ce38-476">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-476">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="6ce38-477">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-477">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="6ce38-478">`--callback-path <PATH>` -Cestu požadavku v rámci základní cesty aplikace identifikátoru URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-478">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="6ce38-479">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-479">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="6ce38-480">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-480">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="6ce38-481">`-r|--org-read-access` – Povolí této aplikaci přístup pro čtení do adresáře.</span><span class="sxs-lookup"><span data-stu-id="6ce38-481">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="6ce38-482">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-482">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="6ce38-483">`--use-launch-settings` -Zahrnuje *launchSettings.json* ve výstupu vygenerovanou šablonu.</span><span class="sxs-lookup"><span data-stu-id="6ce38-483">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="6ce38-484">`--use-browserlink` -Obsahuje BrowserLink v projektu.</span><span class="sxs-lookup"><span data-stu-id="6ce38-484">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="6ce38-485">`-uld|--use-local-db` : Určuje, že by měl být LocalDB použít místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="6ce38-485">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="6ce38-486">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6ce38-486">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6ce38-487">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="6ce38-487">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6ce38-488">**Stránka**</span><span class="sxs-lookup"><span data-stu-id="6ce38-488">**page**</span></span>

<span data-ttu-id="6ce38-489">`-na|--namespace <NAMESPACE_NAME>`-Namespace pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="6ce38-489">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="6ce38-490">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-490">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="6ce38-491">`-np|--no-pagemodel` -Vytvoří danou stránku bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="6ce38-491">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="6ce38-492">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="6ce38-492">**viewimports**</span></span>

<span data-ttu-id="6ce38-493">`-na|--namespace <NAMESPACE_NAME>`-Namespace pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="6ce38-493">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="6ce38-494">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-494">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6ce38-495">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="6ce38-495">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="6ce38-496">**konzola, xunit, mstest, web, webapi**</span><span class="sxs-lookup"><span data-stu-id="6ce38-496">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="6ce38-497">`-f|--framework` : Určuje, že [framework](../../standard/frameworks.md) do cíle.</span><span class="sxs-lookup"><span data-stu-id="6ce38-497">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6ce38-498">Hodnoty: `netcoreapp1.0` nebo `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-498">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="6ce38-499">Výchozí hodnota je `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-499">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="6ce38-500">**classlib**</span><span class="sxs-lookup"><span data-stu-id="6ce38-500">**classlib**</span></span>

<span data-ttu-id="6ce38-501">`-f|--framework` : Určuje, že [framework](../../standard/frameworks.md) do cíle.</span><span class="sxs-lookup"><span data-stu-id="6ce38-501">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6ce38-502">Hodnoty: `netcoreapp1.0`, `netcoreapp1.1`, nebo `netstandard1.0` k `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-502">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="6ce38-503">Výchozí hodnota je `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-503">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="6ce38-504">**mvc**</span><span class="sxs-lookup"><span data-stu-id="6ce38-504">**mvc**</span></span>

<span data-ttu-id="6ce38-505">`-f|--framework` : Určuje, že [framework](../../standard/frameworks.md) do cíle.</span><span class="sxs-lookup"><span data-stu-id="6ce38-505">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6ce38-506">Hodnoty: `netcoreapp1.0` nebo `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-506">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="6ce38-507">Výchozí hodnota je `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-507">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="6ce38-508">`-au|--auth` -Typ ověřování, který má použít.</span><span class="sxs-lookup"><span data-stu-id="6ce38-508">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="6ce38-509">Hodnoty: `None` nebo `Individual`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-509">Values: `None` or `Individual`.</span></span> <span data-ttu-id="6ce38-510">Výchozí hodnota je `None`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-510">The default value is `None`.</span></span>

<span data-ttu-id="6ce38-511">`-uld|--use-local-db` : Určuje, jestli se mají použít databázi LocalDB místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="6ce38-511">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="6ce38-512">Hodnoty: `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-512">Values: `true` or `false`.</span></span> <span data-ttu-id="6ce38-513">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="6ce38-513">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="6ce38-514">Příklady</span><span class="sxs-lookup"><span data-stu-id="6ce38-514">Examples</span></span>

<span data-ttu-id="6ce38-515">Vytvoření projektu aplikace konzoly F # v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="6ce38-515">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="6ce38-516">Vytvořte projekt knihovny tříd .NET Standard v zadaném adresáři (k dispozici pouze s .NET Core SDK 2.0 a novějšími verzemi):</span><span class="sxs-lookup"><span data-stu-id="6ce38-516">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="6ce38-517">Vytvoření nového projektu aplikace ASP.NET Core C# MVC v aktuálním adresáři bez ověřování:</span><span class="sxs-lookup"><span data-stu-id="6ce38-517">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="6ce38-518">Vytvořte novou aplikaci xUnit:</span><span class="sxs-lookup"><span data-stu-id="6ce38-518">Create a new xUnit application:</span></span>

`dotnet new xunit`

<span data-ttu-id="6ce38-519">Seznam všech šablon, které jsou k dispozici pro rozhraní MVC:</span><span class="sxs-lookup"><span data-stu-id="6ce38-519">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="6ce38-520">Instalace verze 2.0 šablon jednostránkové aplikace ASP.NET Core (příkaz Možnosti dostupné pro .NET Core SDK 1.1 a novějších verzích pouze):</span><span class="sxs-lookup"><span data-stu-id="6ce38-520">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="6ce38-521">Vytvoření *global.json* v aktuálním adresáři nastavení sady SDK verze 2.0.0 (k dispozici pouze s .NET Core SDK 2.0 a novějšími verzemi):</span><span class="sxs-lookup"><span data-stu-id="6ce38-521">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="6ce38-522">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6ce38-522">See also</span></span>

* [<span data-ttu-id="6ce38-523">Vlastních šablon pro dotnet nové</span><span class="sxs-lookup"><span data-stu-id="6ce38-523">Custom templates for dotnet new</span></span>](custom-templates.md)  
* [<span data-ttu-id="6ce38-524">Vytvoření vlastní šablony pro dotnet new</span><span class="sxs-lookup"><span data-stu-id="6ce38-524">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
* [<span data-ttu-id="6ce38-525">úložiště GitHub DotNet/dotnet – šablony – ukázky</span><span class="sxs-lookup"><span data-stu-id="6ce38-525">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
* [<span data-ttu-id="6ce38-526">Dostupné šablony pro dotnet nové</span><span class="sxs-lookup"><span data-stu-id="6ce38-526">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
