---
title: nový příkaz DotNet – rozhraní příkazového řádku .NET Core
description: Vytvoří nový příkaz dotnet nových projektů .NET Core založených na zadané šabloně.
author: mairaw
ms.author: mairaw
ms.date: 10/24/2018
ms.openlocfilehash: 56d76f1dd54097f9cf20129d74057235290c273c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188196"
---
# <a name="dotnet-new"></a><span data-ttu-id="3b8dc-103">nový příkaz DotNet</span><span class="sxs-lookup"><span data-stu-id="3b8dc-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="3b8dc-104">Název</span><span class="sxs-lookup"><span data-stu-id="3b8dc-104">Name</span></span>

<span data-ttu-id="3b8dc-105">`dotnet new` -Vytvoří nový projekt, konfigurační soubor nebo řešení založené na zadané šabloně.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3b8dc-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="3b8dc-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="3b8dc-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="3b8dc-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output]
    [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="3b8dc-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="3b8dc-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="3b8dc-109">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="3b8dc-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="3b8dc-110">Popis</span><span class="sxs-lookup"><span data-stu-id="3b8dc-110">Description</span></span>

<span data-ttu-id="3b8dc-111">`dotnet new` Příkaz poskytuje pohodlný způsob, jak inicializovat platný projekt .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="3b8dc-112">Příkaz volání [modulu šablon](https://github.com/dotnet/templating) vytvořit artefakty na disku na základě určené šablony a možnosti.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="3b8dc-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="3b8dc-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="3b8dc-114">Šablona pro vytvoření instance při vyvolání příkazu.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="3b8dc-115">Každá šablona může mít specifické možnosti, které lze předat.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="3b8dc-116">Další informace najdete v tématu [možnosti šablony](#template-options).</span><span class="sxs-lookup"><span data-stu-id="3b8dc-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="3b8dc-117">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="3b8dc-117">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="3b8dc-118">Příkaz obsahuje výchozí seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-118">The command contains a default list of templates.</span></span> <span data-ttu-id="3b8dc-119">Použití `dotnet new -l` získat seznam dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="3b8dc-120">V následující tabulce jsou uvedeny šablony, které jsou předinstalovány se sadou .NET Core SDK 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-120">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="3b8dc-121">Výchozí jazyk šablony se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="3b8dc-122">Popis šablony</span><span class="sxs-lookup"><span data-stu-id="3b8dc-122">Template description</span></span>                          | <span data-ttu-id="3b8dc-123">Název šablony</span><span class="sxs-lookup"><span data-stu-id="3b8dc-123">Template name</span></span>    | <span data-ttu-id="3b8dc-124">Jazyky</span><span class="sxs-lookup"><span data-stu-id="3b8dc-124">Languages</span></span>     |
|----------------------------------------------|------------------|---------------|
| <span data-ttu-id="3b8dc-125">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="3b8dc-125">Console application</span></span>                          | `console`        | <span data-ttu-id="3b8dc-126">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="3b8dc-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="3b8dc-127">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="3b8dc-127">Class library</span></span>                                | `classlib`       | <span data-ttu-id="3b8dc-128">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="3b8dc-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="3b8dc-129">Projekt testu jednotek</span><span class="sxs-lookup"><span data-stu-id="3b8dc-129">Unit test project</span></span>                            | `mstest`         | <span data-ttu-id="3b8dc-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="3b8dc-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="3b8dc-131">Projekt testů xUnit</span><span class="sxs-lookup"><span data-stu-id="3b8dc-131">xUnit test project</span></span>                           | `xunit`          | <span data-ttu-id="3b8dc-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="3b8dc-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="3b8dc-133">Stránka Razor</span><span class="sxs-lookup"><span data-stu-id="3b8dc-133">Razor page</span></span>                                   | `page`           | <span data-ttu-id="3b8dc-134">[C#]</span><span class="sxs-lookup"><span data-stu-id="3b8dc-134">[C#]</span></span>          |
| <span data-ttu-id="3b8dc-135">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="3b8dc-135">MVC ViewImports</span></span>                              | `viewimports`    | <span data-ttu-id="3b8dc-136">[C#]</span><span class="sxs-lookup"><span data-stu-id="3b8dc-136">[C#]</span></span>          |
| <span data-ttu-id="3b8dc-137">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="3b8dc-137">MVC ViewStart</span></span>                                | `viewstart`      | <span data-ttu-id="3b8dc-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="3b8dc-138">[C#]</span></span>          |
| <span data-ttu-id="3b8dc-139">ASP.NET Core je prázdný</span><span class="sxs-lookup"><span data-stu-id="3b8dc-139">ASP.NET Core empty</span></span>                           | `web`            | <span data-ttu-id="3b8dc-140">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="3b8dc-140">[C#], F#</span></span>      |
| <span data-ttu-id="3b8dc-141">Webové aplikace ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="3b8dc-141">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`            | <span data-ttu-id="3b8dc-142">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="3b8dc-142">[C#], F#</span></span>      |
| <span data-ttu-id="3b8dc-143">Webové aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3b8dc-143">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="3b8dc-144">`razor`, `webapp`</span><span class="sxs-lookup"><span data-stu-id="3b8dc-144">`razor`, `webapp`</span></span>| <span data-ttu-id="3b8dc-145">[C#]</span><span class="sxs-lookup"><span data-stu-id="3b8dc-145">[C#]</span></span>          |
| <span data-ttu-id="3b8dc-146">ASP.NET Core pomocí Angular</span><span class="sxs-lookup"><span data-stu-id="3b8dc-146">ASP.NET Core with Angular</span></span>                    | `angular`        | <span data-ttu-id="3b8dc-147">[C#]</span><span class="sxs-lookup"><span data-stu-id="3b8dc-147">[C#]</span></span>          |
| <span data-ttu-id="3b8dc-148">ASP.NET Core pomocí React.js</span><span class="sxs-lookup"><span data-stu-id="3b8dc-148">ASP.NET Core with React.js</span></span>                   | `react`          | <span data-ttu-id="3b8dc-149">[C#]</span><span class="sxs-lookup"><span data-stu-id="3b8dc-149">[C#]</span></span>          |
| <span data-ttu-id="3b8dc-150">ASP.NET Core pomocí React.js a Redux</span><span class="sxs-lookup"><span data-stu-id="3b8dc-150">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`     | <span data-ttu-id="3b8dc-151">[C#]</span><span class="sxs-lookup"><span data-stu-id="3b8dc-151">[C#]</span></span>          |
| <span data-ttu-id="3b8dc-152">Webové rozhraní API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3b8dc-152">ASP.NET Core Web API</span></span>                         | `webapi`         | <span data-ttu-id="3b8dc-153">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="3b8dc-153">[C#], F#</span></span>      |
| <span data-ttu-id="3b8dc-154">Knihovny tříd Razor</span><span class="sxs-lookup"><span data-stu-id="3b8dc-154">Razor class library</span></span>                          | `razorclasslib`  | <span data-ttu-id="3b8dc-155">[C#]</span><span class="sxs-lookup"><span data-stu-id="3b8dc-155">[C#]</span></span>          |
| <span data-ttu-id="3b8dc-156">soubor Global.JSON</span><span class="sxs-lookup"><span data-stu-id="3b8dc-156">global.json file</span></span>                             | `globaljson`     |               |
| <span data-ttu-id="3b8dc-157">NuGet config</span><span class="sxs-lookup"><span data-stu-id="3b8dc-157">NuGet config</span></span>                                 | `nugetconfig`    |               |
| <span data-ttu-id="3b8dc-158">Webové konfigurace</span><span class="sxs-lookup"><span data-stu-id="3b8dc-158">Web config</span></span>                                   | `webconfig`      |               |
| <span data-ttu-id="3b8dc-159">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="3b8dc-159">Solution file</span></span>                                | `sln`            |               |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="3b8dc-160">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="3b8dc-160">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="3b8dc-161">Příkaz obsahuje výchozí seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-161">The command contains a default list of templates.</span></span> <span data-ttu-id="3b8dc-162">Použití `dotnet new -l` získat seznam dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-162">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="3b8dc-163">V následující tabulce jsou uvedeny šablony, které jsou předem nainstalované s .NET Core SDK 2.0.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-163">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.</span></span> <span data-ttu-id="3b8dc-164">Výchozí jazyk šablony se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-164">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="3b8dc-165">Popis šablony</span><span class="sxs-lookup"><span data-stu-id="3b8dc-165">Template description</span></span>                          | <span data-ttu-id="3b8dc-166">Název šablony</span><span class="sxs-lookup"><span data-stu-id="3b8dc-166">Template name</span></span> | <span data-ttu-id="3b8dc-167">Jazyky</span><span class="sxs-lookup"><span data-stu-id="3b8dc-167">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="3b8dc-168">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="3b8dc-168">Console application</span></span>                          | `console`     | <span data-ttu-id="3b8dc-169">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="3b8dc-169">[C#], F#, VB</span></span>  |
| <span data-ttu-id="3b8dc-170">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="3b8dc-170">Class library</span></span>                                | `classlib`    | <span data-ttu-id="3b8dc-171">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="3b8dc-171">[C#], F#, VB</span></span>  |
| <span data-ttu-id="3b8dc-172">Projekt testu jednotek</span><span class="sxs-lookup"><span data-stu-id="3b8dc-172">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="3b8dc-173">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="3b8dc-173">[C#], F#, VB</span></span>  |
| <span data-ttu-id="3b8dc-174">Projekt testů xUnit</span><span class="sxs-lookup"><span data-stu-id="3b8dc-174">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="3b8dc-175">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="3b8dc-175">[C#], F#, VB</span></span>  |
| <span data-ttu-id="3b8dc-176">ASP.NET Core je prázdný</span><span class="sxs-lookup"><span data-stu-id="3b8dc-176">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="3b8dc-177">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="3b8dc-177">[C#], F#</span></span>      |
| <span data-ttu-id="3b8dc-178">Webové aplikace ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="3b8dc-178">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="3b8dc-179">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="3b8dc-179">[C#], F#</span></span>      |
| <span data-ttu-id="3b8dc-180">Webové aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3b8dc-180">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="3b8dc-181">[C#]</span><span class="sxs-lookup"><span data-stu-id="3b8dc-181">[C#]</span></span>          |
| <span data-ttu-id="3b8dc-182">ASP.NET Core pomocí Angular</span><span class="sxs-lookup"><span data-stu-id="3b8dc-182">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="3b8dc-183">[C#]</span><span class="sxs-lookup"><span data-stu-id="3b8dc-183">[C#]</span></span>          |
| <span data-ttu-id="3b8dc-184">ASP.NET Core pomocí React.js</span><span class="sxs-lookup"><span data-stu-id="3b8dc-184">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="3b8dc-185">[C#]</span><span class="sxs-lookup"><span data-stu-id="3b8dc-185">[C#]</span></span>          |
| <span data-ttu-id="3b8dc-186">ASP.NET Core pomocí React.js a Redux</span><span class="sxs-lookup"><span data-stu-id="3b8dc-186">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="3b8dc-187">[C#]</span><span class="sxs-lookup"><span data-stu-id="3b8dc-187">[C#]</span></span>          |
| <span data-ttu-id="3b8dc-188">Webové rozhraní API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3b8dc-188">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="3b8dc-189">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="3b8dc-189">[C#], F#</span></span>      |
| <span data-ttu-id="3b8dc-190">soubor Global.JSON</span><span class="sxs-lookup"><span data-stu-id="3b8dc-190">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="3b8dc-191">NuGet config</span><span class="sxs-lookup"><span data-stu-id="3b8dc-191">NuGet config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="3b8dc-192">Webové konfigurace</span><span class="sxs-lookup"><span data-stu-id="3b8dc-192">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="3b8dc-193">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="3b8dc-193">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="3b8dc-194">Stránka Razor</span><span class="sxs-lookup"><span data-stu-id="3b8dc-194">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="3b8dc-195">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="3b8dc-195">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="3b8dc-196">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="3b8dc-196">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="3b8dc-197">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="3b8dc-197">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="3b8dc-198">Příkaz obsahuje výchozí seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-198">The command contains a default list of templates.</span></span> <span data-ttu-id="3b8dc-199">Použití `dotnet new -all` získat seznam dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-199">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="3b8dc-200">V následující tabulce jsou uvedeny šablony, které jsou předinstalovány se sadou SDK .NET Core 1.x.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-200">The following table shows the templates that come pre-installed with the .NET Core SDK 1.x.</span></span> <span data-ttu-id="3b8dc-201">Výchozí jazyk šablony se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-201">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="3b8dc-202">Popis šablony</span><span class="sxs-lookup"><span data-stu-id="3b8dc-202">Template description</span></span>  | <span data-ttu-id="3b8dc-203">Název šablony</span><span class="sxs-lookup"><span data-stu-id="3b8dc-203">Template name</span></span> | <span data-ttu-id="3b8dc-204">Jazyky</span><span class="sxs-lookup"><span data-stu-id="3b8dc-204">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="3b8dc-205">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="3b8dc-205">Console application</span></span>  | `console`     | <span data-ttu-id="3b8dc-206">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="3b8dc-206">[C#], F#</span></span>  |
| <span data-ttu-id="3b8dc-207">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="3b8dc-207">Class library</span></span>        | `classlib`    | <span data-ttu-id="3b8dc-208">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="3b8dc-208">[C#], F#</span></span>  |
| <span data-ttu-id="3b8dc-209">Projekt testu jednotek</span><span class="sxs-lookup"><span data-stu-id="3b8dc-209">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="3b8dc-210">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="3b8dc-210">[C#], F#</span></span>  |
| <span data-ttu-id="3b8dc-211">Projekt testů xUnit</span><span class="sxs-lookup"><span data-stu-id="3b8dc-211">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="3b8dc-212">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="3b8dc-212">[C#], F#</span></span>  |
| <span data-ttu-id="3b8dc-213">ASP.NET Core je prázdný</span><span class="sxs-lookup"><span data-stu-id="3b8dc-213">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="3b8dc-214">[C#]</span><span class="sxs-lookup"><span data-stu-id="3b8dc-214">[C#]</span></span>      |
| <span data-ttu-id="3b8dc-215">Webové aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3b8dc-215">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="3b8dc-216">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="3b8dc-216">[C#], F#</span></span>  |
| <span data-ttu-id="3b8dc-217">Webové rozhraní API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3b8dc-217">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="3b8dc-218">[C#]</span><span class="sxs-lookup"><span data-stu-id="3b8dc-218">[C#]</span></span>      |
| <span data-ttu-id="3b8dc-219">NuGet config</span><span class="sxs-lookup"><span data-stu-id="3b8dc-219">NuGet config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="3b8dc-220">Webové konfigurace</span><span class="sxs-lookup"><span data-stu-id="3b8dc-220">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="3b8dc-221">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="3b8dc-221">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="3b8dc-222">Možnosti</span><span class="sxs-lookup"><span data-stu-id="3b8dc-222">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="3b8dc-223">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="3b8dc-223">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="3b8dc-224">Vynutí obsahu chcete vygenerovat i v případě, že by došlo ke změně existujících souborů.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-224">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="3b8dc-225">To je potřeba při výstupní adresář již obsahuje projekt.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-225">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="3b8dc-226">Vytiskne nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-226">Prints out help for the command.</span></span> <span data-ttu-id="3b8dc-227">Může být vyvolána pro `dotnet new` samotný příkaz nebo pro všechny šablony, jako například `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-227">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="3b8dc-228">Nainstaluje zdroj nebo šablony pack z `PATH` nebo `NUGET_ID` k dispozici.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-228">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="3b8dc-229">Pokud chcete nainstalovat zkušební verzi balíčku šablony, je třeba zadat verzi ve formátu `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-229">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="3b8dc-230">Ve výchozím nastavení `dotnet new` předá \* pro verzi, která představuje poslední stabilní balíček verze.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-230">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="3b8dc-231">Podívejte se příklad na [příklady](#examples) oddílu.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-231">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="3b8dc-232">Informace o vytváření vlastních šablon najdete v tématu [vlastních šablon pro dotnet nové](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="3b8dc-232">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="3b8dc-233">Zobrazí seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-233">Lists templates containing the specified name.</span></span> <span data-ttu-id="3b8dc-234">Pokud je vyvolána `dotnet new` příkazu, uvádí možné šablony, které jsou k dispozici pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-234">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="3b8dc-235">Například pokud adresář, projekt již obsahuje, neobsahuje všechny šablony projektů.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-235">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="3b8dc-236">Jazyk šablony k vytvoření.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-236">The language of the template to create.</span></span> <span data-ttu-id="3b8dc-237">Jazyk přijato, se liší podle šablony (Zobrazit výchozí hodnoty v [argumenty](#arguments) části).</span><span class="sxs-lookup"><span data-stu-id="3b8dc-237">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="3b8dc-238">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-238">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="3b8dc-239">Některé součásti pro interpretaci `#` jako speciální znak.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-239">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="3b8dc-240">V takových případech bude nutné uvést hodnotu parametru jazyka, jako `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-240">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="3b8dc-241">Název pro výstup vytvořený.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-241">The name for the created output.</span></span> <span data-ttu-id="3b8dc-242">Pokud není zadán žádný název, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-242">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="3b8dc-243">Určuje zdroj NuGet, který chcete použít během instalace.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-243">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="3b8dc-244">Umístění pro vygenerovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-244">Location to place the generated output.</span></span> <span data-ttu-id="3b8dc-245">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-245">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="3b8dc-246">Vyfiltruje šablony podle dostupných typů.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-246">Filters templates based on available types.</span></span> <span data-ttu-id="3b8dc-247">Předdefinované hodnoty jsou "projekt", "item" nebo "jiné".</span><span class="sxs-lookup"><span data-stu-id="3b8dc-247">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="3b8dc-248">Odinstaluje zdroj nebo šablony pack na `PATH` nebo `NUGET_ID` k dispozici.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-248">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="3b8dc-249">Chcete-li odinstalovat sadu pomocí šablony `PATH`, budete potřebovat plně kvalifikovanou cestu.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-249">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="3b8dc-250">Například *C:/uživatele/\<uživatele > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z obsahuje složky nebudou.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-250">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="3b8dc-251">Kromě toho nesmí být znak konečné ukončující znak lomítka adresáře na cestu k šabloně.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-251">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="3b8dc-252">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="3b8dc-252">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="3b8dc-253">Vynutí obsahu chcete vygenerovat i v případě, že by došlo ke změně existujících souborů.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-253">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="3b8dc-254">To je potřeba při výstupní adresář již obsahuje projekt.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-254">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="3b8dc-255">Vytiskne nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-255">Prints out help for the command.</span></span> <span data-ttu-id="3b8dc-256">Může být vyvolána pro `dotnet new` samotný příkaz nebo pro všechny šablony, jako například `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-256">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="3b8dc-257">Nainstaluje zdroj nebo šablony pack z `PATH` nebo `NUGET_ID` k dispozici.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-257">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="3b8dc-258">Pokud chcete nainstalovat zkušební verzi balíčku šablony, je třeba zadat verzi ve formátu `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-258">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="3b8dc-259">Ve výchozím nastavení `dotnet new` předá \* pro verzi, která představuje poslední stabilní balíček verze.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-259">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="3b8dc-260">Podívejte se příklad na [příklady](#examples) oddílu.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-260">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="3b8dc-261">Informace o vytváření vlastních šablon najdete v tématu [vlastních šablon pro dotnet nové](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="3b8dc-261">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="3b8dc-262">Zobrazí seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-262">Lists templates containing the specified name.</span></span> <span data-ttu-id="3b8dc-263">Pokud je vyvolána `dotnet new` příkazu, uvádí možné šablony, které jsou k dispozici pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-263">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="3b8dc-264">Například pokud adresář, projekt již obsahuje, neobsahuje všechny šablony projektů.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-264">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="3b8dc-265">Jazyk šablony k vytvoření.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-265">The language of the template to create.</span></span> <span data-ttu-id="3b8dc-266">Jazyk přijato, se liší podle šablony (Zobrazit výchozí hodnoty v [argumenty](#arguments) části).</span><span class="sxs-lookup"><span data-stu-id="3b8dc-266">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="3b8dc-267">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-267">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="3b8dc-268">Některé součásti pro interpretaci `#` jako speciální znak.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-268">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="3b8dc-269">V takových případech bude nutné uvést hodnotu parametru jazyka, jako `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-269">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="3b8dc-270">Název pro výstup vytvořený.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-270">The name for the created output.</span></span> <span data-ttu-id="3b8dc-271">Pokud není zadán žádný název, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-271">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="3b8dc-272">Umístění pro vygenerovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-272">Location to place the generated output.</span></span> <span data-ttu-id="3b8dc-273">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-273">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="3b8dc-274">Vyfiltruje šablony podle dostupných typů.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-274">Filters templates based on available types.</span></span> <span data-ttu-id="3b8dc-275">Předdefinované hodnoty jsou "projekt", "item" nebo "jiné".</span><span class="sxs-lookup"><span data-stu-id="3b8dc-275">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="3b8dc-276">Odinstaluje zdroj nebo šablony pack na `PATH` nebo `NUGET_ID` k dispozici.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-276">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="3b8dc-277">Odinstalace pomocí zdroj `PATH`, budete potřebovat plně kvalifikovanou cestu.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-277">To uninstall a template using a source `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="3b8dc-278">Například *C:/uživatele/\<uživatele > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z obsahuje složky nebudou.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-278">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span> <span data-ttu-id="3b8dc-279">Kromě toho nesmí být znak konečné ukončující znak lomítka adresáře na cestu k šabloně.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-279">Additionally, do not include a final terminating directory slash on your template path.</span></span>
> 
> <span data-ttu-id="3b8dc-280">Pokud se nemůžete určit `PATH` nebo `NUGET_ID` argumentů potřebných k odinstalaci šablonu s `dotnet new --uninstall` bez argumentu zobrazí seznam všech nainstalovaných šablon a argument nutné je odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-280">If you are unable to determine the `PATH` or `NUGET_ID` argument needed to uninstall a template, running `dotnet new --uninstall` without an argument will list all installed templates and the argument required to uninstall them.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="3b8dc-281">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="3b8dc-281">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="3b8dc-282">Zobrazí všechny šablony pro konkrétní typ projektu při spuštění v kontextu `dotnet new` samotný příkaz.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-282">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="3b8dc-283">Při spuštění v kontextu konkrétní šablony, jako například `dotnet new web -all`, `-all` je interpretován jako vytvoření příznak force.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-283">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="3b8dc-284">To je potřeba při výstupní adresář již obsahuje projekt.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-284">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="3b8dc-285">Vytiskne nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-285">Prints out help for the command.</span></span> <span data-ttu-id="3b8dc-286">Může být vyvolána pro `dotnet new` samotný příkaz nebo pro všechny šablony, jako například `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-286">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="3b8dc-287">Zobrazí seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-287">Lists templates containing the specified name.</span></span> <span data-ttu-id="3b8dc-288">Pokud je vyvolána `dotnet new` příkazu, uvádí možné šablony, které jsou k dispozici pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-288">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="3b8dc-289">Například pokud adresář, projekt již obsahuje, neobsahuje všechny šablony projektů.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-289">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="3b8dc-290">Jazyk šablony k vytvoření.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-290">The language of the template to create.</span></span> <span data-ttu-id="3b8dc-291">Jazyk přijato, se liší podle šablony (Zobrazit výchozí hodnoty v [argumenty](#arguments) části).</span><span class="sxs-lookup"><span data-stu-id="3b8dc-291">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="3b8dc-292">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-292">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="3b8dc-293">Některé součásti pro interpretaci `#` jako speciální znak.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-293">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="3b8dc-294">V takových případech bude nutné uvést hodnotu parametru jazyka, jako `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-294">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="3b8dc-295">Název pro výstup vytvořený.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-295">The name for the created output.</span></span> <span data-ttu-id="3b8dc-296">Pokud není zadán žádný název, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-296">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="3b8dc-297">Umístění pro vygenerovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-297">Location to place the generated output.</span></span> <span data-ttu-id="3b8dc-298">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-298">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="3b8dc-299">Nastavení šablony</span><span class="sxs-lookup"><span data-stu-id="3b8dc-299">Template options</span></span>

<span data-ttu-id="3b8dc-300">Každá šablona projektu může mít k dispozici další možnosti.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-300">Each project template may have additional options available.</span></span> <span data-ttu-id="3b8dc-301">Základní šablony mají následující další možnosti:</span><span class="sxs-lookup"><span data-stu-id="3b8dc-301">The core templates have the following additional options:</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="3b8dc-302">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="3b8dc-302">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="3b8dc-303">**konzola, angular, react, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="3b8dc-303">**console, angular, react, reactredux, razorclasslib**</span></span>

  <span data-ttu-id="3b8dc-304">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-304">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="3b8dc-305">**classlib**</span><span class="sxs-lookup"><span data-stu-id="3b8dc-305">**classlib**</span></span>

<span data-ttu-id="3b8dc-306">`-f|--framework <FRAMEWORK>` : Určuje, že [framework](../../standard/frameworks.md) do cíle.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-306">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="3b8dc-307">Hodnoty: `netcoreapp2.0` k vytvoření knihovny tříd .NET Core nebo `netstandard2.0` k vytvoření knihovny tříd .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-307">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="3b8dc-308">Výchozí hodnota je `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-308">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="3b8dc-309">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-309">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="3b8dc-310">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="3b8dc-310">**mstest, xunit**</span></span>

<span data-ttu-id="3b8dc-311">`-p|--enable-pack` – Povolí balení pro projekt pomocí [balíčku dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="3b8dc-311">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="3b8dc-312">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-312">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="3b8dc-313">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="3b8dc-313">**globaljson**</span></span>

<span data-ttu-id="3b8dc-314">`--sdk-version <VERSION_NUMBER>` : Určuje verzi .NET Core SDK pro použití v *global.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-314">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="3b8dc-315">**web**</span><span class="sxs-lookup"><span data-stu-id="3b8dc-315">**web**</span></span>

<span data-ttu-id="3b8dc-316">`--exclude-launch-settings` -Vyloučení *launchSettings.json* z vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-316">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="3b8dc-317">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-317">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="3b8dc-318">`--no-https` -Projektu nebude vyžadovat protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-318">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="3b8dc-319">Tato možnost platí, pouze pokud `IndividualAuth` nebo `OrganizationalAuth` nejsou používány.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-319">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="3b8dc-320">**webapi**</span><span class="sxs-lookup"><span data-stu-id="3b8dc-320">**webapi**</span></span>

<span data-ttu-id="3b8dc-321">`-au|--auth <AUTHENTICATION_TYPE>` -Typ ověřování, který má použít.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-321">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="3b8dc-322">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="3b8dc-322">The possible values are:</span></span>

- <span data-ttu-id="3b8dc-323">`None` -Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="3b8dc-323">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="3b8dc-324">`IndividualB2C` -Jednotlivé ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-324">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="3b8dc-325">`SingleOrg` – Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-325">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="3b8dc-326">`Windows` -Ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-326">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="3b8dc-327">`--aad-b2c-instance <INSTANCE>` -Instanci Azure Active Directory B2C pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-327">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="3b8dc-328">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-328">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="3b8dc-329">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-329">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="3b8dc-330">`-ssp|--susi-policy-id <ID>` – ID přihlášení a registraci zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-330">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="3b8dc-331">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-331">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="3b8dc-332">`--aad-instance <INSTANCE>` – Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-332">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="3b8dc-333">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-333">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="3b8dc-334">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-334">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="3b8dc-335">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-335">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="3b8dc-336">Použití s `IndividualB2C` nebo `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-336">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="3b8dc-337">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-337">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="3b8dc-338">`--domain <DOMAIN>` -Domény tenantu Active directory.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-338">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="3b8dc-339">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-339">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="3b8dc-340">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-340">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="3b8dc-341">`--tenant-id <ID>` – ID Tenanta ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-341">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="3b8dc-342">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-342">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="3b8dc-343">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-343">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="3b8dc-344">`-r|--org-read-access` – Povolí této aplikaci přístup pro čtení do adresáře.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-344">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="3b8dc-345">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-345">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="3b8dc-346">`--exclude-launch-settings` -Vyloučení *launchSettings.json* z vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-346">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="3b8dc-347">`-uld|--use-local-db` : Určuje, že by měl být LocalDB použít místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-347">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="3b8dc-348">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-348">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="3b8dc-349">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-349">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="3b8dc-350">`--no-https` -Projektu nebude vyžadovat protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-350">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="3b8dc-351">`app.UseHsts` a `app.UseHttpsRedirection` nejsou přidány do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-351">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="3b8dc-352">Tato možnost platí, pouze pokud `Individual`, `IndividualB2C`, `SingleOrg`, nebo `MultiOrg` nejsou používány.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-352">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="3b8dc-353">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="3b8dc-353">**mvc, razor**</span></span>

<span data-ttu-id="3b8dc-354">`-au|--auth <AUTHENTICATION_TYPE>` -Typ ověřování, který má použít.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-354">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="3b8dc-355">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="3b8dc-355">The possible values are:</span></span>

- <span data-ttu-id="3b8dc-356">`None` -Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="3b8dc-356">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="3b8dc-357">`Individual` -Jednotlivé ověřování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-357">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="3b8dc-358">`IndividualB2C` -Jednotlivé ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-358">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="3b8dc-359">`SingleOrg` – Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-359">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="3b8dc-360">`MultiOrg` – Ověřování organizace pro více tenantů.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-360">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="3b8dc-361">`Windows` -Ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-361">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="3b8dc-362">`--aad-b2c-instance <INSTANCE>` -Instanci Azure Active Directory B2C pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-362">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="3b8dc-363">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-363">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="3b8dc-364">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-364">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="3b8dc-365">`-ssp|--susi-policy-id <ID>` – ID přihlášení a registraci zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-365">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="3b8dc-366">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-366">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="3b8dc-367">`-rp|--reset-password-policy-id <ID>` -Resetování hesla ID zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-367">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="3b8dc-368">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-368">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="3b8dc-369">`-ep|--edit-profile-policy-id <ID>` – Upravit profil zásady ID pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-369">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="3b8dc-370">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-370">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="3b8dc-371">`--aad-instance <INSTANCE>` – Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-371">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="3b8dc-372">Použití s `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-372">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="3b8dc-373">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-373">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="3b8dc-374">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-374">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="3b8dc-375">Použití s `IndividualB2C`, `SingleOrg`, nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-375">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="3b8dc-376">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-376">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="3b8dc-377">`--domain <DOMAIN>` -Domény tenantu Active directory.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-377">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="3b8dc-378">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-378">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="3b8dc-379">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-379">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="3b8dc-380">`--tenant-id <ID>` – ID Tenanta ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-380">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="3b8dc-381">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-381">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="3b8dc-382">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-382">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="3b8dc-383">`--callback-path <PATH>` -Cestu požadavku v rámci základní cesty aplikace identifikátoru URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-383">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="3b8dc-384">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-384">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="3b8dc-385">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-385">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="3b8dc-386">`-r|--org-read-access` – Povolí této aplikaci přístup pro čtení do adresáře.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-386">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="3b8dc-387">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-387">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="3b8dc-388">`--exclude-launch-settings` -Vyloučení *launchSettings.json* z vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-388">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="3b8dc-389">`--use-browserlink` -Obsahuje BrowserLink v projektu.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-389">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="3b8dc-390">`-uld|--use-local-db` : Určuje, že by měl být LocalDB použít místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-390">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="3b8dc-391">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-391">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="3b8dc-392">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-392">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="3b8dc-393">`--no-https` -Projektu nebude vyžadovat protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-393">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="3b8dc-394">`app.UseHsts` a `app.UseHttpsRedirection` nejsou přidány do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-394">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="3b8dc-395">Tato možnost platí, pouze pokud `Individual`, `IndividualB2C`, `SingleOrg`, nebo `MultiOrg` nejsou používány.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-395">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="3b8dc-396">**Stránka**</span><span class="sxs-lookup"><span data-stu-id="3b8dc-396">**page**</span></span>

<span data-ttu-id="3b8dc-397">`-na|--namespace <NAMESPACE_NAME>`-Namespace pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-397">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="3b8dc-398">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-398">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="3b8dc-399">`-np|--no-pagemodel` -Vytvoří danou stránku bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-399">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="3b8dc-400">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="3b8dc-400">**viewimports**</span></span>

<span data-ttu-id="3b8dc-401">`-na|--namespace <NAMESPACE_NAME>`-Namespace pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-401">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="3b8dc-402">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-402">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="3b8dc-403">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="3b8dc-403">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="3b8dc-404">**konzola, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="3b8dc-404">**console, angular, react, reactredux**</span></span>

  <span data-ttu-id="3b8dc-405">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-405">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="3b8dc-406">**classlib**</span><span class="sxs-lookup"><span data-stu-id="3b8dc-406">**classlib**</span></span>

<span data-ttu-id="3b8dc-407">`-f|--framework <FRAMEWORK>` : Určuje, že [framework](../../standard/frameworks.md) do cíle.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-407">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="3b8dc-408">Hodnoty: `netcoreapp2.0` k vytvoření knihovny tříd .NET Core nebo `netstandard2.0` k vytvoření knihovny tříd .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-408">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="3b8dc-409">Výchozí hodnota je `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-409">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="3b8dc-410">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-410">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="3b8dc-411">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="3b8dc-411">**mstest, xunit**</span></span>

<span data-ttu-id="3b8dc-412">`-p|--enable-pack` – Povolí balení pro projekt pomocí [balíčku dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="3b8dc-412">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="3b8dc-413">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-413">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="3b8dc-414">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="3b8dc-414">**globaljson**</span></span>

<span data-ttu-id="3b8dc-415">`--sdk-version <VERSION_NUMBER>` : Určuje verzi .NET Core SDK pro použití v *global.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-415">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="3b8dc-416">**web**</span><span class="sxs-lookup"><span data-stu-id="3b8dc-416">**web**</span></span>

<span data-ttu-id="3b8dc-417">`--use-launch-settings` -Zahrnuje *launchSettings.json* ve výstupu vygenerovanou šablonu.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-417">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="3b8dc-418">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-418">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="3b8dc-419">**webapi**</span><span class="sxs-lookup"><span data-stu-id="3b8dc-419">**webapi**</span></span>

<span data-ttu-id="3b8dc-420">`-au|--auth <AUTHENTICATION_TYPE>` -Typ ověřování, který má použít.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-420">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="3b8dc-421">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="3b8dc-421">The possible values are:</span></span>

- <span data-ttu-id="3b8dc-422">`None` -Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="3b8dc-422">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="3b8dc-423">`IndividualB2C` -Jednotlivé ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-423">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="3b8dc-424">`SingleOrg` – Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-424">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="3b8dc-425">`Windows` -Ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-425">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="3b8dc-426">`--aad-b2c-instance <INSTANCE>` -Instanci Azure Active Directory B2C pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-426">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="3b8dc-427">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-427">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="3b8dc-428">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-428">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="3b8dc-429">`-ssp|--susi-policy-id <ID>` – ID přihlášení a registraci zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-429">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="3b8dc-430">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-430">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="3b8dc-431">`--aad-instance <INSTANCE>` – Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-431">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="3b8dc-432">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-432">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="3b8dc-433">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-433">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="3b8dc-434">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-434">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="3b8dc-435">Použití s `IndividualB2C` nebo `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-435">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="3b8dc-436">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-436">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="3b8dc-437">`--domain <DOMAIN>` -Domény tenantu Active directory.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-437">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="3b8dc-438">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-438">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="3b8dc-439">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-439">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="3b8dc-440">`--tenant-id <ID>` – ID Tenanta ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-440">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="3b8dc-441">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-441">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="3b8dc-442">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-442">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="3b8dc-443">`-r|--org-read-access` – Povolí této aplikaci přístup pro čtení do adresáře.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-443">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="3b8dc-444">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-444">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="3b8dc-445">`--use-launch-settings` -Zahrnuje *launchSettings.json* ve výstupu vygenerovanou šablonu.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-445">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="3b8dc-446">`-uld|--use-local-db` : Určuje, že by měl být LocalDB použít místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-446">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="3b8dc-447">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-447">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="3b8dc-448">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-448">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="3b8dc-449">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="3b8dc-449">**mvc, razor**</span></span>

<span data-ttu-id="3b8dc-450">`-au|--auth <AUTHENTICATION_TYPE>` -Typ ověřování, který má použít.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-450">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="3b8dc-451">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="3b8dc-451">The possible values are:</span></span>

- <span data-ttu-id="3b8dc-452">`None` -Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="3b8dc-452">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="3b8dc-453">`Individual` -Jednotlivé ověřování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-453">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="3b8dc-454">`IndividualB2C` -Jednotlivé ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-454">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="3b8dc-455">`SingleOrg` – Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-455">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="3b8dc-456">`MultiOrg` – Ověřování organizace pro více tenantů.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-456">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="3b8dc-457">`Windows` -Ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-457">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="3b8dc-458">`--aad-b2c-instance <INSTANCE>` -Instanci Azure Active Directory B2C pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-458">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="3b8dc-459">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-459">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="3b8dc-460">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-460">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="3b8dc-461">`-ssp|--susi-policy-id <ID>` – ID přihlášení a registraci zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-461">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="3b8dc-462">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-462">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="3b8dc-463">`-rp|--reset-password-policy-id <ID>` -Resetování hesla ID zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-463">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="3b8dc-464">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-464">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="3b8dc-465">`-ep|--edit-profile-policy-id <ID>` – Upravit profil zásady ID pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-465">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="3b8dc-466">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-466">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="3b8dc-467">`--aad-instance <INSTANCE>` – Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-467">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="3b8dc-468">Použití s `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-468">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="3b8dc-469">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-469">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="3b8dc-470">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-470">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="3b8dc-471">Použití s `IndividualB2C`, `SingleOrg`, nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-471">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="3b8dc-472">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-472">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="3b8dc-473">`--domain <DOMAIN>` -Domény tenantu Active directory.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-473">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="3b8dc-474">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-474">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="3b8dc-475">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-475">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="3b8dc-476">`--tenant-id <ID>` – ID Tenanta ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-476">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="3b8dc-477">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-477">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="3b8dc-478">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-478">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="3b8dc-479">`--callback-path <PATH>` -Cestu požadavku v rámci základní cesty aplikace identifikátoru URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-479">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="3b8dc-480">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-480">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="3b8dc-481">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-481">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="3b8dc-482">`-r|--org-read-access` – Povolí této aplikaci přístup pro čtení do adresáře.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-482">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="3b8dc-483">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-483">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="3b8dc-484">`--use-launch-settings` -Zahrnuje *launchSettings.json* ve výstupu vygenerovanou šablonu.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-484">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="3b8dc-485">`--use-browserlink` -Obsahuje BrowserLink v projektu.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-485">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="3b8dc-486">`-uld|--use-local-db` : Určuje, že by měl být LocalDB použít místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-486">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="3b8dc-487">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-487">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="3b8dc-488">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-488">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="3b8dc-489">**Stránka**</span><span class="sxs-lookup"><span data-stu-id="3b8dc-489">**page**</span></span>

<span data-ttu-id="3b8dc-490">`-na|--namespace <NAMESPACE_NAME>`-Namespace pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-490">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="3b8dc-491">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-491">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="3b8dc-492">`-np|--no-pagemodel` -Vytvoří danou stránku bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-492">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="3b8dc-493">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="3b8dc-493">**viewimports**</span></span>

<span data-ttu-id="3b8dc-494">`-na|--namespace <NAMESPACE_NAME>`-Namespace pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-494">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="3b8dc-495">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-495">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="3b8dc-496">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="3b8dc-496">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="3b8dc-497">**konzola, xunit, mstest, web, webapi**</span><span class="sxs-lookup"><span data-stu-id="3b8dc-497">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="3b8dc-498">`-f|--framework` : Určuje, že [framework](../../standard/frameworks.md) do cíle.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-498">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="3b8dc-499">Hodnoty: `netcoreapp1.0` nebo `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-499">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="3b8dc-500">Výchozí hodnota je `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-500">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="3b8dc-501">**classlib**</span><span class="sxs-lookup"><span data-stu-id="3b8dc-501">**classlib**</span></span>

<span data-ttu-id="3b8dc-502">`-f|--framework` : Určuje, že [framework](../../standard/frameworks.md) do cíle.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-502">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="3b8dc-503">Hodnoty: `netcoreapp1.0`, `netcoreapp1.1`, nebo `netstandard1.0` k `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-503">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="3b8dc-504">Výchozí hodnota je `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-504">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="3b8dc-505">**mvc**</span><span class="sxs-lookup"><span data-stu-id="3b8dc-505">**mvc**</span></span>

<span data-ttu-id="3b8dc-506">`-f|--framework` : Určuje, že [framework](../../standard/frameworks.md) do cíle.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-506">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="3b8dc-507">Hodnoty: `netcoreapp1.0` nebo `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-507">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="3b8dc-508">Výchozí hodnota je `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-508">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="3b8dc-509">`-au|--auth` -Typ ověřování, který má použít.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-509">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="3b8dc-510">Hodnoty: `None` nebo `Individual`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-510">Values: `None` or `Individual`.</span></span> <span data-ttu-id="3b8dc-511">Výchozí hodnota je `None`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-511">The default value is `None`.</span></span>

<span data-ttu-id="3b8dc-512">`-uld|--use-local-db` : Určuje, jestli se mají použít databázi LocalDB místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-512">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="3b8dc-513">Hodnoty: `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-513">Values: `true` or `false`.</span></span> <span data-ttu-id="3b8dc-514">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="3b8dc-514">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="3b8dc-515">Příklady</span><span class="sxs-lookup"><span data-stu-id="3b8dc-515">Examples</span></span>

<span data-ttu-id="3b8dc-516">Vytvoření projektu aplikace konzoly F # v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="3b8dc-516">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="3b8dc-517">Vytvořte projekt knihovny tříd .NET Standard v zadaném adresáři (k dispozici pouze s .NET Core SDK 2.0 a novějšími verzemi):</span><span class="sxs-lookup"><span data-stu-id="3b8dc-517">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="3b8dc-518">Vytvoření nového projektu aplikace ASP.NET Core C# MVC v aktuálním adresáři bez ověřování:</span><span class="sxs-lookup"><span data-stu-id="3b8dc-518">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="3b8dc-519">Vytvořte novou aplikaci xUnit:</span><span class="sxs-lookup"><span data-stu-id="3b8dc-519">Create a new xUnit application:</span></span>

`dotnet new xunit`

<span data-ttu-id="3b8dc-520">Seznam všech šablon, které jsou k dispozici pro rozhraní MVC:</span><span class="sxs-lookup"><span data-stu-id="3b8dc-520">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="3b8dc-521">Instalace verze 2.0 šablon jednostránkové aplikace ASP.NET Core (příkaz Možnosti dostupné pro .NET Core SDK 1.1 a novějších verzích pouze):</span><span class="sxs-lookup"><span data-stu-id="3b8dc-521">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="3b8dc-522">Vytvoření *global.json* v aktuálním adresáři nastavení sady SDK verze 2.0.0 (k dispozici pouze s .NET Core SDK 2.0 a novějšími verzemi):</span><span class="sxs-lookup"><span data-stu-id="3b8dc-522">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="3b8dc-523">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3b8dc-523">See also</span></span>

* [<span data-ttu-id="3b8dc-524">Vlastních šablon pro dotnet nové</span><span class="sxs-lookup"><span data-stu-id="3b8dc-524">Custom templates for dotnet new</span></span>](custom-templates.md)  
* [<span data-ttu-id="3b8dc-525">Vytvoření vlastní šablony pro dotnet new</span><span class="sxs-lookup"><span data-stu-id="3b8dc-525">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
* [<span data-ttu-id="3b8dc-526">úložiště GitHub DotNet/dotnet – šablony – ukázky</span><span class="sxs-lookup"><span data-stu-id="3b8dc-526">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
* [<span data-ttu-id="3b8dc-527">Dostupné šablony pro dotnet nové</span><span class="sxs-lookup"><span data-stu-id="3b8dc-527">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
