---
title: nový příkaz DotNet – rozhraní příkazového řádku .NET Core
description: Vytvoří nový příkaz dotnet nových projektů .NET Core založených na zadané šabloně.
author: mairaw
ms.author: mairaw
ms.date: 07/31/2018
ms.openlocfilehash: 2c82dda2d93225edb360316637e22964135cd5e4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43512552"
---
# <a name="dotnet-new"></a><span data-ttu-id="0f6ea-103">nový příkaz DotNet</span><span class="sxs-lookup"><span data-stu-id="0f6ea-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="0f6ea-104">Název</span><span class="sxs-lookup"><span data-stu-id="0f6ea-104">Name</span></span>

<span data-ttu-id="0f6ea-105">`dotnet new` -Vytvoří nový projekt, konfigurační soubor nebo řešení založené na zadané šabloně.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0f6ea-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="0f6ea-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="0f6ea-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="0f6ea-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output]
    [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="0f6ea-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="0f6ea-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0f6ea-109">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="0f6ea-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="0f6ea-110">Popis</span><span class="sxs-lookup"><span data-stu-id="0f6ea-110">Description</span></span>

<span data-ttu-id="0f6ea-111">`dotnet new` Příkaz poskytuje pohodlný způsob, jak inicializovat platný projekt .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="0f6ea-112">Příkaz volání [modulu šablon](https://github.com/dotnet/templating) vytvořit artefakty na disku na základě určené šablony a možnosti.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="0f6ea-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="0f6ea-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="0f6ea-114">Šablona pro vytvoření instance při vyvolání příkazu.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="0f6ea-115">Každá šablona může mít specifické možnosti, které lze předat.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="0f6ea-116">Další informace najdete v tématu [možnosti šablony](#template-options).</span><span class="sxs-lookup"><span data-stu-id="0f6ea-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="0f6ea-117">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="0f6ea-117">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="0f6ea-118">Příkaz obsahuje výchozí seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-118">The command contains a default list of templates.</span></span> <span data-ttu-id="0f6ea-119">Použití `dotnet new -l` získat seznam dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="0f6ea-120">V následující tabulce jsou uvedeny šablony, které jsou předinstalovány se sadou .NET Core SDK 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-120">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="0f6ea-121">Výchozí jazyk šablony se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="0f6ea-122">Popis šablony</span><span class="sxs-lookup"><span data-stu-id="0f6ea-122">Template description</span></span>                          | <span data-ttu-id="0f6ea-123">Název šablony</span><span class="sxs-lookup"><span data-stu-id="0f6ea-123">Template name</span></span>   | <span data-ttu-id="0f6ea-124">Jazyky</span><span class="sxs-lookup"><span data-stu-id="0f6ea-124">Languages</span></span>     |
|----------------------------------------------|-----------------|---------------|
| <span data-ttu-id="0f6ea-125">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="0f6ea-125">Console application</span></span>                          | `console`       | <span data-ttu-id="0f6ea-126">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="0f6ea-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="0f6ea-127">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="0f6ea-127">Class library</span></span>                                | `classlib`      | <span data-ttu-id="0f6ea-128">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="0f6ea-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="0f6ea-129">Projekt testu jednotek</span><span class="sxs-lookup"><span data-stu-id="0f6ea-129">Unit test project</span></span>                            | `mstest`        | <span data-ttu-id="0f6ea-130">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="0f6ea-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="0f6ea-131">Projekt testů xUnit</span><span class="sxs-lookup"><span data-stu-id="0f6ea-131">xUnit test project</span></span>                           | `xunit`         | <span data-ttu-id="0f6ea-132">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="0f6ea-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="0f6ea-133">Stránka Razor</span><span class="sxs-lookup"><span data-stu-id="0f6ea-133">Razor page</span></span>                                   | `page`          | <span data-ttu-id="0f6ea-134">[C#]</span><span class="sxs-lookup"><span data-stu-id="0f6ea-134">[C#]</span></span>          |
| <span data-ttu-id="0f6ea-135">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="0f6ea-135">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="0f6ea-136">[C#]</span><span class="sxs-lookup"><span data-stu-id="0f6ea-136">[C#]</span></span>          |
| <span data-ttu-id="0f6ea-137">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="0f6ea-137">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="0f6ea-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="0f6ea-138">[C#]</span></span>          |
| <span data-ttu-id="0f6ea-139">ASP.NET Core je prázdný</span><span class="sxs-lookup"><span data-stu-id="0f6ea-139">ASP.NET Core empty</span></span>                           | `web`           | <span data-ttu-id="0f6ea-140">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="0f6ea-140">[C#], F#</span></span>      |
| <span data-ttu-id="0f6ea-141">Webové aplikace ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="0f6ea-141">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="0f6ea-142">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="0f6ea-142">[C#], F#</span></span>      |
| <span data-ttu-id="0f6ea-143">Webové aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0f6ea-143">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="0f6ea-144">[C#]</span><span class="sxs-lookup"><span data-stu-id="0f6ea-144">[C#]</span></span>          |
| <span data-ttu-id="0f6ea-145">ASP.NET Core pomocí Angular</span><span class="sxs-lookup"><span data-stu-id="0f6ea-145">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="0f6ea-146">[C#]</span><span class="sxs-lookup"><span data-stu-id="0f6ea-146">[C#]</span></span>          |
| <span data-ttu-id="0f6ea-147">ASP.NET Core pomocí React.js</span><span class="sxs-lookup"><span data-stu-id="0f6ea-147">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="0f6ea-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="0f6ea-148">[C#]</span></span>          |
| <span data-ttu-id="0f6ea-149">ASP.NET Core pomocí React.js a Redux</span><span class="sxs-lookup"><span data-stu-id="0f6ea-149">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="0f6ea-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="0f6ea-150">[C#]</span></span>          |
| <span data-ttu-id="0f6ea-151">Webové rozhraní API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0f6ea-151">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="0f6ea-152">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="0f6ea-152">[C#], F#</span></span>      |
| <span data-ttu-id="0f6ea-153">Knihovny tříd Razor</span><span class="sxs-lookup"><span data-stu-id="0f6ea-153">Razor class library</span></span>                          | `razorclasslib` | <span data-ttu-id="0f6ea-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="0f6ea-154">[C#]</span></span>          |
| <span data-ttu-id="0f6ea-155">soubor Global.JSON</span><span class="sxs-lookup"><span data-stu-id="0f6ea-155">global.json file</span></span>                             | `globaljson`    |               |
| <span data-ttu-id="0f6ea-156">NuGet config</span><span class="sxs-lookup"><span data-stu-id="0f6ea-156">NuGet config</span></span>                                 | `nugetconfig`   |               |
| <span data-ttu-id="0f6ea-157">Webové konfigurace</span><span class="sxs-lookup"><span data-stu-id="0f6ea-157">Web config</span></span>                                   | `webconfig`     |               |
| <span data-ttu-id="0f6ea-158">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="0f6ea-158">Solution file</span></span>                                | `sln`           |               |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="0f6ea-159">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="0f6ea-159">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="0f6ea-160">Příkaz obsahuje výchozí seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-160">The command contains a default list of templates.</span></span> <span data-ttu-id="0f6ea-161">Použití `dotnet new -l` získat seznam dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-161">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="0f6ea-162">V následující tabulce jsou uvedeny šablony, které jsou předem nainstalované s .NET Core SDK 2.0.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-162">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.</span></span> <span data-ttu-id="0f6ea-163">Výchozí jazyk šablony se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-163">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="0f6ea-164">Popis šablony</span><span class="sxs-lookup"><span data-stu-id="0f6ea-164">Template description</span></span>                          | <span data-ttu-id="0f6ea-165">Název šablony</span><span class="sxs-lookup"><span data-stu-id="0f6ea-165">Template name</span></span> | <span data-ttu-id="0f6ea-166">Jazyky</span><span class="sxs-lookup"><span data-stu-id="0f6ea-166">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="0f6ea-167">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="0f6ea-167">Console application</span></span>                          | `console`     | <span data-ttu-id="0f6ea-168">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="0f6ea-168">[C#], F#, VB</span></span>  |
| <span data-ttu-id="0f6ea-169">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="0f6ea-169">Class library</span></span>                                | `classlib`    | <span data-ttu-id="0f6ea-170">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="0f6ea-170">[C#], F#, VB</span></span>  |
| <span data-ttu-id="0f6ea-171">Projekt testu jednotek</span><span class="sxs-lookup"><span data-stu-id="0f6ea-171">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="0f6ea-172">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="0f6ea-172">[C#], F#, VB</span></span>  |
| <span data-ttu-id="0f6ea-173">Projekt testů xUnit</span><span class="sxs-lookup"><span data-stu-id="0f6ea-173">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="0f6ea-174">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="0f6ea-174">[C#], F#, VB</span></span>  |
| <span data-ttu-id="0f6ea-175">ASP.NET Core je prázdný</span><span class="sxs-lookup"><span data-stu-id="0f6ea-175">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="0f6ea-176">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="0f6ea-176">[C#], F#</span></span>      |
| <span data-ttu-id="0f6ea-177">Webové aplikace ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="0f6ea-177">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="0f6ea-178">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="0f6ea-178">[C#], F#</span></span>      |
| <span data-ttu-id="0f6ea-179">Webové aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0f6ea-179">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="0f6ea-180">[C#]</span><span class="sxs-lookup"><span data-stu-id="0f6ea-180">[C#]</span></span>          |
| <span data-ttu-id="0f6ea-181">ASP.NET Core pomocí Angular</span><span class="sxs-lookup"><span data-stu-id="0f6ea-181">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="0f6ea-182">[C#]</span><span class="sxs-lookup"><span data-stu-id="0f6ea-182">[C#]</span></span>          |
| <span data-ttu-id="0f6ea-183">ASP.NET Core pomocí React.js</span><span class="sxs-lookup"><span data-stu-id="0f6ea-183">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="0f6ea-184">[C#]</span><span class="sxs-lookup"><span data-stu-id="0f6ea-184">[C#]</span></span>          |
| <span data-ttu-id="0f6ea-185">ASP.NET Core pomocí React.js a Redux</span><span class="sxs-lookup"><span data-stu-id="0f6ea-185">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="0f6ea-186">[C#]</span><span class="sxs-lookup"><span data-stu-id="0f6ea-186">[C#]</span></span>          |
| <span data-ttu-id="0f6ea-187">Webové rozhraní API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0f6ea-187">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="0f6ea-188">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="0f6ea-188">[C#], F#</span></span>      |
| <span data-ttu-id="0f6ea-189">soubor Global.JSON</span><span class="sxs-lookup"><span data-stu-id="0f6ea-189">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="0f6ea-190">NuGet config</span><span class="sxs-lookup"><span data-stu-id="0f6ea-190">NuGet config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="0f6ea-191">Webové konfigurace</span><span class="sxs-lookup"><span data-stu-id="0f6ea-191">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="0f6ea-192">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="0f6ea-192">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="0f6ea-193">Stránka Razor</span><span class="sxs-lookup"><span data-stu-id="0f6ea-193">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="0f6ea-194">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="0f6ea-194">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="0f6ea-195">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="0f6ea-195">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0f6ea-196">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="0f6ea-196">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="0f6ea-197">Příkaz obsahuje výchozí seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-197">The command contains a default list of templates.</span></span> <span data-ttu-id="0f6ea-198">Použití `dotnet new -all` získat seznam dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-198">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="0f6ea-199">V následující tabulce jsou uvedeny šablony, které jsou předinstalovány se sadou SDK .NET Core 1.x.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-199">The following table shows the templates that come pre-installed with the .NET Core SDK 1.x.</span></span> <span data-ttu-id="0f6ea-200">Výchozí jazyk šablony se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-200">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="0f6ea-201">Popis šablony</span><span class="sxs-lookup"><span data-stu-id="0f6ea-201">Template description</span></span>  | <span data-ttu-id="0f6ea-202">Název šablony</span><span class="sxs-lookup"><span data-stu-id="0f6ea-202">Template name</span></span> | <span data-ttu-id="0f6ea-203">Jazyky</span><span class="sxs-lookup"><span data-stu-id="0f6ea-203">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="0f6ea-204">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="0f6ea-204">Console application</span></span>  | `console`     | <span data-ttu-id="0f6ea-205">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="0f6ea-205">[C#], F#</span></span>  |
| <span data-ttu-id="0f6ea-206">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="0f6ea-206">Class library</span></span>        | `classlib`    | <span data-ttu-id="0f6ea-207">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="0f6ea-207">[C#], F#</span></span>  |
| <span data-ttu-id="0f6ea-208">Projekt testu jednotek</span><span class="sxs-lookup"><span data-stu-id="0f6ea-208">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="0f6ea-209">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="0f6ea-209">[C#], F#</span></span>  |
| <span data-ttu-id="0f6ea-210">Projekt testů xUnit</span><span class="sxs-lookup"><span data-stu-id="0f6ea-210">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="0f6ea-211">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="0f6ea-211">[C#], F#</span></span>  |
| <span data-ttu-id="0f6ea-212">ASP.NET Core je prázdný</span><span class="sxs-lookup"><span data-stu-id="0f6ea-212">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="0f6ea-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="0f6ea-213">[C#]</span></span>      |
| <span data-ttu-id="0f6ea-214">Webové aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0f6ea-214">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="0f6ea-215">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="0f6ea-215">[C#], F#</span></span>  |
| <span data-ttu-id="0f6ea-216">Webové rozhraní API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0f6ea-216">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="0f6ea-217">[C#]</span><span class="sxs-lookup"><span data-stu-id="0f6ea-217">[C#]</span></span>      |
| <span data-ttu-id="0f6ea-218">NuGet config</span><span class="sxs-lookup"><span data-stu-id="0f6ea-218">NuGet config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="0f6ea-219">Webové konfigurace</span><span class="sxs-lookup"><span data-stu-id="0f6ea-219">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="0f6ea-220">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="0f6ea-220">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="0f6ea-221">Možnosti</span><span class="sxs-lookup"><span data-stu-id="0f6ea-221">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="0f6ea-222">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="0f6ea-222">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="0f6ea-223">Vynutí obsahu chcete vygenerovat i v případě, že by došlo ke změně existujících souborů.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-223">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="0f6ea-224">To je potřeba při výstupní adresář již obsahuje projekt.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-224">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="0f6ea-225">Vytiskne nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-225">Prints out help for the command.</span></span> <span data-ttu-id="0f6ea-226">Může být vyvolána pro `dotnet new` samotný příkaz nebo pro všechny šablony, jako například `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-226">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="0f6ea-227">Nainstaluje zdroj nebo šablony pack z `PATH` nebo `NUGET_ID` k dispozici.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-227">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="0f6ea-228">Pokud chcete nainstalovat zkušební verzi balíčku šablony, je třeba zadat verzi ve formátu `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-228">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="0f6ea-229">Ve výchozím nastavení `dotnet new` předá \* pro verzi, která představuje poslední stabilní balíček verze.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-229">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="0f6ea-230">Podívejte se příklad na [příklady](#examples) oddílu.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-230">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="0f6ea-231">Informace o vytváření vlastních šablon najdete v tématu [vlastních šablon pro dotnet nové](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="0f6ea-231">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="0f6ea-232">Zobrazí seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-232">Lists templates containing the specified name.</span></span> <span data-ttu-id="0f6ea-233">Pokud je vyvolána `dotnet new` příkazu, uvádí možné šablony, které jsou k dispozici pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-233">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="0f6ea-234">Například pokud adresář, projekt již obsahuje, neobsahuje všechny šablony projektů.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-234">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="0f6ea-235">Jazyk šablony k vytvoření.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-235">The language of the template to create.</span></span> <span data-ttu-id="0f6ea-236">Jazyk přijato, se liší podle šablony (Zobrazit výchozí hodnoty v [argumenty](#arguments) části).</span><span class="sxs-lookup"><span data-stu-id="0f6ea-236">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="0f6ea-237">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-237">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="0f6ea-238">Některé součásti pro interpretaci `#` jako speciální znak.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-238">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="0f6ea-239">V takových případech bude nutné uvést hodnotu parametru jazyka, jako `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-239">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="0f6ea-240">Název pro výstup vytvořený.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-240">The name for the created output.</span></span> <span data-ttu-id="0f6ea-241">Pokud není zadán žádný název, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-241">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="0f6ea-242">Určuje zdroj NuGet, který chcete použít během instalace.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-242">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="0f6ea-243">Umístění pro vygenerovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-243">Location to place the generated output.</span></span> <span data-ttu-id="0f6ea-244">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-244">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="0f6ea-245">Vyfiltruje šablony podle dostupných typů.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-245">Filters templates based on available types.</span></span> <span data-ttu-id="0f6ea-246">Předdefinované hodnoty jsou "projekt", "item" nebo "jiné".</span><span class="sxs-lookup"><span data-stu-id="0f6ea-246">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="0f6ea-247">Odinstaluje zdroj nebo šablony pack na `PATH` nebo `NUGET_ID` k dispozici.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-247">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="0f6ea-248">Chcete-li odinstalovat sadu pomocí šablony `PATH`, budete potřebovat plně kvalifikovanou cestu.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-248">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="0f6ea-249">Například *C:/uživatele/\<uživatele > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z obsahuje složky nebudou.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-249">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="0f6ea-250">Kromě toho nesmí být znak konečné ukončující znak lomítka adresáře na cestu k šabloně.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-250">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="0f6ea-251">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="0f6ea-251">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="0f6ea-252">Vynutí obsahu chcete vygenerovat i v případě, že by došlo ke změně existujících souborů.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-252">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="0f6ea-253">To je potřeba při výstupní adresář již obsahuje projekt.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-253">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="0f6ea-254">Vytiskne nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-254">Prints out help for the command.</span></span> <span data-ttu-id="0f6ea-255">Může být vyvolána pro `dotnet new` samotný příkaz nebo pro všechny šablony, jako například `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-255">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="0f6ea-256">Nainstaluje zdroj nebo šablony pack z `PATH` nebo `NUGET_ID` k dispozici.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-256">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="0f6ea-257">Pokud chcete nainstalovat zkušební verzi balíčku šablony, je třeba zadat verzi ve formátu `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-257">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="0f6ea-258">Ve výchozím nastavení `dotnet new` předá \* pro verzi, která představuje poslední stabilní balíček verze.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-258">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="0f6ea-259">Podívejte se příklad na [příklady](#examples) oddílu.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-259">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="0f6ea-260">Informace o vytváření vlastních šablon najdete v tématu [vlastních šablon pro dotnet nové](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="0f6ea-260">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="0f6ea-261">Zobrazí seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-261">Lists templates containing the specified name.</span></span> <span data-ttu-id="0f6ea-262">Pokud je vyvolána `dotnet new` příkazu, uvádí možné šablony, které jsou k dispozici pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-262">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="0f6ea-263">Například pokud adresář, projekt již obsahuje, neobsahuje všechny šablony projektů.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-263">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="0f6ea-264">Jazyk šablony k vytvoření.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-264">The language of the template to create.</span></span> <span data-ttu-id="0f6ea-265">Jazyk přijato, se liší podle šablony (Zobrazit výchozí hodnoty v [argumenty](#arguments) části).</span><span class="sxs-lookup"><span data-stu-id="0f6ea-265">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="0f6ea-266">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-266">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="0f6ea-267">Některé součásti pro interpretaci `#` jako speciální znak.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-267">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="0f6ea-268">V takových případech bude nutné uvést hodnotu parametru jazyka, jako `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-268">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="0f6ea-269">Název pro výstup vytvořený.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-269">The name for the created output.</span></span> <span data-ttu-id="0f6ea-270">Pokud není zadán žádný název, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-270">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="0f6ea-271">Umístění pro vygenerovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-271">Location to place the generated output.</span></span> <span data-ttu-id="0f6ea-272">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-272">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="0f6ea-273">Vyfiltruje šablony podle dostupných typů.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-273">Filters templates based on available types.</span></span> <span data-ttu-id="0f6ea-274">Předdefinované hodnoty jsou "projekt", "item" nebo "jiné".</span><span class="sxs-lookup"><span data-stu-id="0f6ea-274">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="0f6ea-275">Odinstaluje zdroj nebo šablony pack na `PATH` nebo `NUGET_ID` k dispozici.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-275">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="0f6ea-276">Chcete-li odinstalovat sadu pomocí šablony `PATH`, budete potřebovat plně kvalifikovanou cestu.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-276">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="0f6ea-277">Například *C:/uživatele/\<uživatele > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z obsahuje složky nebudou.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-277">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="0f6ea-278">Kromě toho nesmí být znak konečné ukončující znak lomítka adresáře na cestu k šabloně.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-278">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0f6ea-279">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="0f6ea-279">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="0f6ea-280">Zobrazí všechny šablony pro konkrétní typ projektu při spuštění v kontextu `dotnet new` samotný příkaz.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-280">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="0f6ea-281">Při spuštění v kontextu konkrétní šablony, jako například `dotnet new web -all`, `-all` je interpretován jako vytvoření příznak force.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-281">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="0f6ea-282">To je potřeba při výstupní adresář již obsahuje projekt.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-282">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="0f6ea-283">Vytiskne nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-283">Prints out help for the command.</span></span> <span data-ttu-id="0f6ea-284">Může být vyvolána pro `dotnet new` samotný příkaz nebo pro všechny šablony, jako například `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-284">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="0f6ea-285">Zobrazí seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-285">Lists templates containing the specified name.</span></span> <span data-ttu-id="0f6ea-286">Pokud je vyvolána `dotnet new` příkazu, uvádí možné šablony, které jsou k dispozici pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-286">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="0f6ea-287">Například pokud adresář, projekt již obsahuje, neobsahuje všechny šablony projektů.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-287">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="0f6ea-288">Jazyk šablony k vytvoření.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-288">The language of the template to create.</span></span> <span data-ttu-id="0f6ea-289">Jazyk přijato, se liší podle šablony (Zobrazit výchozí hodnoty v [argumenty](#arguments) části).</span><span class="sxs-lookup"><span data-stu-id="0f6ea-289">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="0f6ea-290">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-290">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="0f6ea-291">Některé součásti pro interpretaci `#` jako speciální znak.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-291">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="0f6ea-292">V takových případech bude nutné uvést hodnotu parametru jazyka, jako `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-292">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="0f6ea-293">Název pro výstup vytvořený.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-293">The name for the created output.</span></span> <span data-ttu-id="0f6ea-294">Pokud není zadán žádný název, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-294">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="0f6ea-295">Umístění pro vygenerovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-295">Location to place the generated output.</span></span> <span data-ttu-id="0f6ea-296">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-296">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="0f6ea-297">Nastavení šablony</span><span class="sxs-lookup"><span data-stu-id="0f6ea-297">Template options</span></span>

<span data-ttu-id="0f6ea-298">Každá šablona projektu může mít k dispozici další možnosti.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-298">Each project template may have additional options available.</span></span> <span data-ttu-id="0f6ea-299">Základní šablony mají následující další možnosti:</span><span class="sxs-lookup"><span data-stu-id="0f6ea-299">The core templates have the following additional options:</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="0f6ea-300">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="0f6ea-300">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="0f6ea-301">**konzola, angular, react, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="0f6ea-301">**console, angular, react, reactredux, razorclasslib**</span></span>

  <span data-ttu-id="0f6ea-302">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-302">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="0f6ea-303">**classlib**</span><span class="sxs-lookup"><span data-stu-id="0f6ea-303">**classlib**</span></span>

<span data-ttu-id="0f6ea-304">`-f|--framework <FRAMEWORK>` : Určuje, že [framework](../../standard/frameworks.md) do cíle.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-304">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="0f6ea-305">Hodnoty: `netcoreapp2.0` k vytvoření knihovny tříd .NET Core nebo `netstandard2.0` k vytvoření knihovny tříd .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-305">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="0f6ea-306">Výchozí hodnota je `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-306">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="0f6ea-307">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-307">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="0f6ea-308">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="0f6ea-308">**mstest, xunit**</span></span>

<span data-ttu-id="0f6ea-309">`-p|--enable-pack` – Povolí balení pro projekt pomocí [balíčku dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="0f6ea-309">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="0f6ea-310">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-310">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="0f6ea-311">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="0f6ea-311">**globaljson**</span></span>

<span data-ttu-id="0f6ea-312">`--sdk-version <VERSION_NUMBER>` : Určuje verzi .NET Core SDK pro použití v *global.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-312">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="0f6ea-313">**web**</span><span class="sxs-lookup"><span data-stu-id="0f6ea-313">**web**</span></span>

<span data-ttu-id="0f6ea-314">`--exclude-launch-settings` -Vyloučení *launchSettings.json* z vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-314">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="0f6ea-315">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-315">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="0f6ea-316">`--no-https` -Projektu nebude vyžadovat protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-316">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="0f6ea-317">Tato možnost platí, pouze pokud `IndividualAuth` nebo `OrganizationalAuth` nejsou používány.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-317">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="0f6ea-318">**webapi**</span><span class="sxs-lookup"><span data-stu-id="0f6ea-318">**webapi**</span></span>

<span data-ttu-id="0f6ea-319">`-au|--auth <AUTHENTICATION_TYPE>` -Typ ověřování, který má použít.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-319">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="0f6ea-320">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="0f6ea-320">The possible values are:</span></span>

- <span data-ttu-id="0f6ea-321">`None` -Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="0f6ea-321">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="0f6ea-322">`IndividualB2C` -Jednotlivé ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-322">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="0f6ea-323">`SingleOrg` – Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-323">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="0f6ea-324">`Windows` -Ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-324">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="0f6ea-325">`--aad-b2c-instance <INSTANCE>` -Instanci Azure Active Directory B2C pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-325">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="0f6ea-326">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-326">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="0f6ea-327">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-327">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="0f6ea-328">`-ssp|--susi-policy-id <ID>` – ID přihlášení a registraci zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-328">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="0f6ea-329">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-329">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="0f6ea-330">`--aad-instance <INSTANCE>` – Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-330">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="0f6ea-331">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-331">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="0f6ea-332">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-332">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="0f6ea-333">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-333">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="0f6ea-334">Použití s `IndividualB2C` nebo `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-334">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="0f6ea-335">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-335">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="0f6ea-336">`--domain <DOMAIN>` -Domény tenantu Active directory.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-336">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="0f6ea-337">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-337">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="0f6ea-338">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-338">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="0f6ea-339">`--tenant-id <ID>` – ID Tenanta ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-339">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="0f6ea-340">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-340">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="0f6ea-341">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-341">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="0f6ea-342">`-r|--org-read-access` – Povolí této aplikaci přístup pro čtení do adresáře.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-342">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="0f6ea-343">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-343">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="0f6ea-344">`--exclude-launch-settings` -Vyloučení *launchSettings.json* z vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-344">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="0f6ea-345">`-uld|--use-local-db` : Určuje, že by měl být LocalDB použít místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-345">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="0f6ea-346">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-346">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="0f6ea-347">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-347">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="0f6ea-348">`--no-https` -Projektu nebude vyžadovat protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-348">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="0f6ea-349">`app.UseHsts` a `app.UseHttpsRedirection` nejsou přidány do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-349">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="0f6ea-350">Tato možnost platí, pouze pokud `Individual`, `IndividualB2C`, `SingleOrg`, nebo `MultiOrg` nejsou používány.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-350">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="0f6ea-351">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="0f6ea-351">**mvc, razor**</span></span>

<span data-ttu-id="0f6ea-352">`-au|--auth <AUTHENTICATION_TYPE>` -Typ ověřování, který má použít.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-352">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="0f6ea-353">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="0f6ea-353">The possible values are:</span></span>

- <span data-ttu-id="0f6ea-354">`None` -Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="0f6ea-354">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="0f6ea-355">`Individual` -Jednotlivé ověřování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-355">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="0f6ea-356">`IndividualB2C` -Jednotlivé ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-356">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="0f6ea-357">`SingleOrg` – Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-357">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="0f6ea-358">`MultiOrg` – Ověřování organizace pro více tenantů.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-358">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="0f6ea-359">`Windows` -Ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-359">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="0f6ea-360">`--aad-b2c-instance <INSTANCE>` -Instanci Azure Active Directory B2C pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-360">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="0f6ea-361">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-361">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="0f6ea-362">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-362">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="0f6ea-363">`-ssp|--susi-policy-id <ID>` – ID přihlášení a registraci zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-363">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="0f6ea-364">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-364">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="0f6ea-365">`-rp|--reset-password-policy-id <ID>` -Resetování hesla ID zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-365">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="0f6ea-366">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-366">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="0f6ea-367">`-ep|--edit-profile-policy-id <ID>` – Upravit profil zásady ID pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-367">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="0f6ea-368">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-368">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="0f6ea-369">`--aad-instance <INSTANCE>` – Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-369">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="0f6ea-370">Použití s `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-370">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="0f6ea-371">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-371">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="0f6ea-372">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-372">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="0f6ea-373">Použití s `IndividualB2C`, `SingleOrg`, nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-373">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="0f6ea-374">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-374">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="0f6ea-375">`--domain <DOMAIN>` -Domény tenantu Active directory.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-375">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="0f6ea-376">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-376">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="0f6ea-377">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-377">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="0f6ea-378">`--tenant-id <ID>` – ID Tenanta ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-378">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="0f6ea-379">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-379">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="0f6ea-380">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-380">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="0f6ea-381">`--callback-path <PATH>` -Cestu požadavku v rámci základní cesty aplikace identifikátoru URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-381">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="0f6ea-382">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-382">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="0f6ea-383">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-383">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="0f6ea-384">`-r|--org-read-access` – Povolí této aplikaci přístup pro čtení do adresáře.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-384">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="0f6ea-385">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-385">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="0f6ea-386">`--exclude-launch-settings` -Vyloučení *launchSettings.json* z vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-386">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="0f6ea-387">`--use-browserlink` -Obsahuje BrowserLink v projektu.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-387">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="0f6ea-388">`-uld|--use-local-db` : Určuje, že by měl být LocalDB použít místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-388">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="0f6ea-389">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-389">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="0f6ea-390">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-390">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="0f6ea-391">`--no-https` -Projektu nebude vyžadovat protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-391">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="0f6ea-392">`app.UseHsts` a `app.UseHttpsRedirection` nejsou přidány do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-392">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="0f6ea-393">Tato možnost platí, pouze pokud `Individual`, `IndividualB2C`, `SingleOrg`, nebo `MultiOrg` nejsou používány.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-393">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="0f6ea-394">**Stránka**</span><span class="sxs-lookup"><span data-stu-id="0f6ea-394">**page**</span></span>

<span data-ttu-id="0f6ea-395">`-na|--namespace <NAMESPACE_NAME>`-Namespace pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-395">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="0f6ea-396">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-396">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="0f6ea-397">`-np|--no-pagemodel` -Vytvoří danou stránku bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-397">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="0f6ea-398">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="0f6ea-398">**viewimports**</span></span>

<span data-ttu-id="0f6ea-399">`-na|--namespace <NAMESPACE_NAME>`-Namespace pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-399">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="0f6ea-400">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-400">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="0f6ea-401">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="0f6ea-401">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="0f6ea-402">**konzola, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="0f6ea-402">**console, angular, react, reactredux**</span></span>

  <span data-ttu-id="0f6ea-403">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-403">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="0f6ea-404">**classlib**</span><span class="sxs-lookup"><span data-stu-id="0f6ea-404">**classlib**</span></span>

<span data-ttu-id="0f6ea-405">`-f|--framework <FRAMEWORK>` : Určuje, že [framework](../../standard/frameworks.md) do cíle.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-405">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="0f6ea-406">Hodnoty: `netcoreapp2.0` k vytvoření knihovny tříd .NET Core nebo `netstandard2.0` k vytvoření knihovny tříd .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-406">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="0f6ea-407">Výchozí hodnota je `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-407">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="0f6ea-408">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-408">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="0f6ea-409">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="0f6ea-409">**mstest, xunit**</span></span>

<span data-ttu-id="0f6ea-410">`-p|--enable-pack` – Povolí balení pro projekt pomocí [balíčku dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="0f6ea-410">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="0f6ea-411">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-411">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="0f6ea-412">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="0f6ea-412">**globaljson**</span></span>

<span data-ttu-id="0f6ea-413">`--sdk-version <VERSION_NUMBER>` : Určuje verzi .NET Core SDK pro použití v *global.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-413">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="0f6ea-414">**web**</span><span class="sxs-lookup"><span data-stu-id="0f6ea-414">**web**</span></span>

<span data-ttu-id="0f6ea-415">`--use-launch-settings` -Zahrnuje *launchSettings.json* ve výstupu vygenerovanou šablonu.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-415">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="0f6ea-416">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-416">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="0f6ea-417">**webapi**</span><span class="sxs-lookup"><span data-stu-id="0f6ea-417">**webapi**</span></span>

<span data-ttu-id="0f6ea-418">`-au|--auth <AUTHENTICATION_TYPE>` -Typ ověřování, který má použít.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-418">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="0f6ea-419">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="0f6ea-419">The possible values are:</span></span>

- <span data-ttu-id="0f6ea-420">`None` -Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="0f6ea-420">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="0f6ea-421">`IndividualB2C` -Jednotlivé ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-421">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="0f6ea-422">`SingleOrg` – Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-422">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="0f6ea-423">`Windows` -Ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-423">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="0f6ea-424">`--aad-b2c-instance <INSTANCE>` -Instanci Azure Active Directory B2C pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-424">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="0f6ea-425">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-425">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="0f6ea-426">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-426">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="0f6ea-427">`-ssp|--susi-policy-id <ID>` – ID přihlášení a registraci zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-427">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="0f6ea-428">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-428">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="0f6ea-429">`--aad-instance <INSTANCE>` – Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-429">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="0f6ea-430">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-430">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="0f6ea-431">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-431">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="0f6ea-432">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-432">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="0f6ea-433">Použití s `IndividualB2C` nebo `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-433">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="0f6ea-434">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-434">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="0f6ea-435">`--domain <DOMAIN>` -Domény tenantu Active directory.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-435">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="0f6ea-436">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-436">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="0f6ea-437">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-437">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="0f6ea-438">`--tenant-id <ID>` – ID Tenanta ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-438">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="0f6ea-439">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-439">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="0f6ea-440">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-440">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="0f6ea-441">`-r|--org-read-access` – Povolí této aplikaci přístup pro čtení do adresáře.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-441">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="0f6ea-442">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-442">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="0f6ea-443">`--use-launch-settings` -Zahrnuje *launchSettings.json* ve výstupu vygenerovanou šablonu.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-443">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="0f6ea-444">`-uld|--use-local-db` : Určuje, že by měl být LocalDB použít místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-444">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="0f6ea-445">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-445">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="0f6ea-446">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-446">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="0f6ea-447">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="0f6ea-447">**mvc, razor**</span></span>

<span data-ttu-id="0f6ea-448">`-au|--auth <AUTHENTICATION_TYPE>` -Typ ověřování, který má použít.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-448">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="0f6ea-449">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="0f6ea-449">The possible values are:</span></span>

- <span data-ttu-id="0f6ea-450">`None` -Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="0f6ea-450">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="0f6ea-451">`Individual` -Jednotlivé ověřování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-451">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="0f6ea-452">`IndividualB2C` -Jednotlivé ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-452">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="0f6ea-453">`SingleOrg` – Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-453">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="0f6ea-454">`MultiOrg` – Ověřování organizace pro více tenantů.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-454">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="0f6ea-455">`Windows` -Ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-455">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="0f6ea-456">`--aad-b2c-instance <INSTANCE>` -Instanci Azure Active Directory B2C pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-456">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="0f6ea-457">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-457">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="0f6ea-458">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-458">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="0f6ea-459">`-ssp|--susi-policy-id <ID>` – ID přihlášení a registraci zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-459">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="0f6ea-460">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-460">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="0f6ea-461">`-rp|--reset-password-policy-id <ID>` -Resetování hesla ID zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-461">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="0f6ea-462">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-462">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="0f6ea-463">`-ep|--edit-profile-policy-id <ID>` – Upravit profil zásady ID pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-463">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="0f6ea-464">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-464">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="0f6ea-465">`--aad-instance <INSTANCE>` – Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-465">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="0f6ea-466">Použití s `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-466">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="0f6ea-467">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-467">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="0f6ea-468">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-468">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="0f6ea-469">Použití s `IndividualB2C`, `SingleOrg`, nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-469">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="0f6ea-470">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-470">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="0f6ea-471">`--domain <DOMAIN>` -Domény tenantu Active directory.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-471">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="0f6ea-472">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-472">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="0f6ea-473">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-473">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="0f6ea-474">`--tenant-id <ID>` – ID Tenanta ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-474">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="0f6ea-475">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-475">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="0f6ea-476">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-476">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="0f6ea-477">`--callback-path <PATH>` -Cestu požadavku v rámci základní cesty aplikace identifikátoru URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-477">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="0f6ea-478">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-478">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="0f6ea-479">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-479">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="0f6ea-480">`-r|--org-read-access` – Povolí této aplikaci přístup pro čtení do adresáře.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-480">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="0f6ea-481">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-481">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="0f6ea-482">`--use-launch-settings` -Zahrnuje *launchSettings.json* ve výstupu vygenerovanou šablonu.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-482">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="0f6ea-483">`--use-browserlink` -Obsahuje BrowserLink v projektu.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-483">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="0f6ea-484">`-uld|--use-local-db` : Určuje, že by měl být LocalDB použít místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-484">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="0f6ea-485">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-485">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="0f6ea-486">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-486">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="0f6ea-487">**Stránka**</span><span class="sxs-lookup"><span data-stu-id="0f6ea-487">**page**</span></span>

<span data-ttu-id="0f6ea-488">`-na|--namespace <NAMESPACE_NAME>`-Namespace pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-488">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="0f6ea-489">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-489">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="0f6ea-490">`-np|--no-pagemodel` -Vytvoří danou stránku bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-490">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="0f6ea-491">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="0f6ea-491">**viewimports**</span></span>

<span data-ttu-id="0f6ea-492">`-na|--namespace <NAMESPACE_NAME>`-Namespace pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-492">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="0f6ea-493">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-493">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0f6ea-494">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="0f6ea-494">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="0f6ea-495">**konzola, xunit, mstest, web, webapi**</span><span class="sxs-lookup"><span data-stu-id="0f6ea-495">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="0f6ea-496">`-f|--framework` : Určuje, že [framework](../../standard/frameworks.md) do cíle.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-496">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="0f6ea-497">Hodnoty: `netcoreapp1.0` nebo `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-497">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="0f6ea-498">Výchozí hodnota je `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-498">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="0f6ea-499">**classlib**</span><span class="sxs-lookup"><span data-stu-id="0f6ea-499">**classlib**</span></span>

<span data-ttu-id="0f6ea-500">`-f|--framework` : Určuje, že [framework](../../standard/frameworks.md) do cíle.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-500">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="0f6ea-501">Hodnoty: `netcoreapp1.0`, `netcoreapp1.1`, nebo `netstandard1.0` k `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-501">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="0f6ea-502">Výchozí hodnota je `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-502">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="0f6ea-503">**mvc**</span><span class="sxs-lookup"><span data-stu-id="0f6ea-503">**mvc**</span></span>

<span data-ttu-id="0f6ea-504">`-f|--framework` : Určuje, že [framework](../../standard/frameworks.md) do cíle.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-504">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="0f6ea-505">Hodnoty: `netcoreapp1.0` nebo `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-505">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="0f6ea-506">Výchozí hodnota je `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-506">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="0f6ea-507">`-au|--auth` -Typ ověřování, který má použít.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-507">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="0f6ea-508">Hodnoty: `None` nebo `Individual`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-508">Values: `None` or `Individual`.</span></span> <span data-ttu-id="0f6ea-509">Výchozí hodnota je `None`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-509">The default value is `None`.</span></span>

<span data-ttu-id="0f6ea-510">`-uld|--use-local-db` : Určuje, jestli se mají použít databázi LocalDB místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-510">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="0f6ea-511">Hodnoty: `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-511">Values: `true` or `false`.</span></span> <span data-ttu-id="0f6ea-512">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="0f6ea-512">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="0f6ea-513">Příklady</span><span class="sxs-lookup"><span data-stu-id="0f6ea-513">Examples</span></span>

<span data-ttu-id="0f6ea-514">Vytvoření projektu aplikace konzoly F # v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="0f6ea-514">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="0f6ea-515">Vytvořte projekt knihovny tříd .NET Standard v zadaném adresáři (k dispozici pouze s .NET Core SDK 2.0 a novějšími verzemi):</span><span class="sxs-lookup"><span data-stu-id="0f6ea-515">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="0f6ea-516">Vytvoření nového projektu aplikace ASP.NET Core C# MVC v aktuálním adresáři bez ověřování:</span><span class="sxs-lookup"><span data-stu-id="0f6ea-516">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="0f6ea-517">Vytvořte novou aplikaci xUnit:</span><span class="sxs-lookup"><span data-stu-id="0f6ea-517">Create a new xUnit application:</span></span>

`dotnet new xunit`

<span data-ttu-id="0f6ea-518">Seznam všech šablon, které jsou k dispozici pro rozhraní MVC:</span><span class="sxs-lookup"><span data-stu-id="0f6ea-518">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="0f6ea-519">Instalace verze 2.0 šablon jednostránkové aplikace ASP.NET Core (příkaz Možnosti dostupné pro .NET Core SDK 1.1 a novějších verzích pouze):</span><span class="sxs-lookup"><span data-stu-id="0f6ea-519">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="0f6ea-520">Vytvoření *global.json* v aktuálním adresáři nastavení sady SDK verze 2.0.0 (k dispozici pouze s .NET Core SDK 2.0 a novějšími verzemi):</span><span class="sxs-lookup"><span data-stu-id="0f6ea-520">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="0f6ea-521">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0f6ea-521">See also</span></span>

* [<span data-ttu-id="0f6ea-522">Vlastních šablon pro dotnet nové</span><span class="sxs-lookup"><span data-stu-id="0f6ea-522">Custom templates for dotnet new</span></span>](custom-templates.md)  
* [<span data-ttu-id="0f6ea-523">Vytvoření vlastní šablony pro dotnet new</span><span class="sxs-lookup"><span data-stu-id="0f6ea-523">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
* [<span data-ttu-id="0f6ea-524">úložiště GitHub DotNet/dotnet – šablony – ukázky</span><span class="sxs-lookup"><span data-stu-id="0f6ea-524">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
* [<span data-ttu-id="0f6ea-525">Dostupné šablony pro dotnet nové</span><span class="sxs-lookup"><span data-stu-id="0f6ea-525">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
