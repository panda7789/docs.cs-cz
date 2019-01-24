---
title: nový příkaz DotNet
description: Vytvoří nový příkaz dotnet nových projektů .NET Core založených na zadané šabloně.
ms.date: 10/24/2018
ms.openlocfilehash: 5177c920fee6fa946d2bf5d96644f26309ed0a99
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54516145"
---
# <a name="dotnet-new"></a><span data-ttu-id="a76f0-103">nový příkaz DotNet</span><span class="sxs-lookup"><span data-stu-id="a76f0-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="a76f0-104">Název</span><span class="sxs-lookup"><span data-stu-id="a76f0-104">Name</span></span>

<span data-ttu-id="a76f0-105">`dotnet new` -Vytvoří nový projekt, konfigurační soubor nebo řešení založené na zadané šabloně.</span><span class="sxs-lookup"><span data-stu-id="a76f0-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a76f0-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="a76f0-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="a76f0-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="a76f0-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output]
    [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="a76f0-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="a76f0-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a76f0-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="a76f0-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="a76f0-110">Popis</span><span class="sxs-lookup"><span data-stu-id="a76f0-110">Description</span></span>

<span data-ttu-id="a76f0-111">`dotnet new` Příkaz poskytuje pohodlný způsob, jak inicializovat platný projekt .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a76f0-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="a76f0-112">Příkaz volání [modulu šablon](https://github.com/dotnet/templating) vytvořit artefakty na disku na základě určené šablony a možnosti.</span><span class="sxs-lookup"><span data-stu-id="a76f0-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="a76f0-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="a76f0-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="a76f0-114">Šablona pro vytvoření instance při vyvolání příkazu.</span><span class="sxs-lookup"><span data-stu-id="a76f0-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="a76f0-115">Každá šablona může mít specifické možnosti, které lze předat.</span><span class="sxs-lookup"><span data-stu-id="a76f0-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="a76f0-116">Další informace najdete v tématu [možnosti šablony](#template-options).</span><span class="sxs-lookup"><span data-stu-id="a76f0-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="a76f0-117">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="a76f0-117">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="a76f0-118">Příkaz obsahuje výchozí seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="a76f0-118">The command contains a default list of templates.</span></span> <span data-ttu-id="a76f0-119">Použití `dotnet new -l` získat seznam dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="a76f0-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="a76f0-120">V následující tabulce jsou uvedeny šablony, které jsou předinstalovány se sadou .NET Core SDK 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="a76f0-120">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="a76f0-121">Výchozí jazyk šablony se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="a76f0-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="a76f0-122">Popis šablony</span><span class="sxs-lookup"><span data-stu-id="a76f0-122">Template description</span></span>                          | <span data-ttu-id="a76f0-123">Název šablony</span><span class="sxs-lookup"><span data-stu-id="a76f0-123">Template name</span></span>    | <span data-ttu-id="a76f0-124">Jazyky</span><span class="sxs-lookup"><span data-stu-id="a76f0-124">Languages</span></span>     |
|----------------------------------------------|------------------|---------------|
| <span data-ttu-id="a76f0-125">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="a76f0-125">Console application</span></span>                          | `console`        | <span data-ttu-id="a76f0-126">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="a76f0-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="a76f0-127">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="a76f0-127">Class library</span></span>                                | `classlib`       | <span data-ttu-id="a76f0-128">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="a76f0-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="a76f0-129">Projekt testu jednotek</span><span class="sxs-lookup"><span data-stu-id="a76f0-129">Unit test project</span></span>                            | `mstest`         | <span data-ttu-id="a76f0-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="a76f0-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="a76f0-131">Projekt testů xUnit</span><span class="sxs-lookup"><span data-stu-id="a76f0-131">xUnit test project</span></span>                           | `xunit`          | <span data-ttu-id="a76f0-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="a76f0-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="a76f0-133">NUnit testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="a76f0-133">NUnit test project</span></span>                           | `nunit`          | <span data-ttu-id="a76f0-134">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="a76f0-134">[C#], F#, VB</span></span>  |
| <span data-ttu-id="a76f0-135">Stránka Razor</span><span class="sxs-lookup"><span data-stu-id="a76f0-135">Razor page</span></span>                                   | `page`           | <span data-ttu-id="a76f0-136">[C#]</span><span class="sxs-lookup"><span data-stu-id="a76f0-136">[C#]</span></span>          |
| <span data-ttu-id="a76f0-137">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="a76f0-137">MVC ViewImports</span></span>                              | `viewimports`    | <span data-ttu-id="a76f0-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="a76f0-138">[C#]</span></span>          |
| <span data-ttu-id="a76f0-139">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="a76f0-139">MVC ViewStart</span></span>                                | `viewstart`      | <span data-ttu-id="a76f0-140">[C#]</span><span class="sxs-lookup"><span data-stu-id="a76f0-140">[C#]</span></span>          |
| <span data-ttu-id="a76f0-141">ASP.NET Core je prázdný</span><span class="sxs-lookup"><span data-stu-id="a76f0-141">ASP.NET Core empty</span></span>                           | `web`            | <span data-ttu-id="a76f0-142">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="a76f0-142">[C#], F#</span></span>      |
| <span data-ttu-id="a76f0-143">Webové aplikace ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="a76f0-143">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`            | <span data-ttu-id="a76f0-144">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="a76f0-144">[C#], F#</span></span>      |
| <span data-ttu-id="a76f0-145">Webové aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a76f0-145">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="a76f0-146">`razor`, `webapp`</span><span class="sxs-lookup"><span data-stu-id="a76f0-146">`razor`, `webapp`</span></span>| <span data-ttu-id="a76f0-147">[C#]</span><span class="sxs-lookup"><span data-stu-id="a76f0-147">[C#]</span></span>          |
| <span data-ttu-id="a76f0-148">ASP.NET Core with Angular</span><span class="sxs-lookup"><span data-stu-id="a76f0-148">ASP.NET Core with Angular</span></span>                    | `angular`        | <span data-ttu-id="a76f0-149">[C#]</span><span class="sxs-lookup"><span data-stu-id="a76f0-149">[C#]</span></span>          |
| <span data-ttu-id="a76f0-150">ASP.NET Core pomocí React.js</span><span class="sxs-lookup"><span data-stu-id="a76f0-150">ASP.NET Core with React.js</span></span>                   | `react`          | <span data-ttu-id="a76f0-151">[C#]</span><span class="sxs-lookup"><span data-stu-id="a76f0-151">[C#]</span></span>          |
| <span data-ttu-id="a76f0-152">ASP.NET Core pomocí React.js a Redux</span><span class="sxs-lookup"><span data-stu-id="a76f0-152">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`     | <span data-ttu-id="a76f0-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="a76f0-153">[C#]</span></span>          |
| <span data-ttu-id="a76f0-154">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="a76f0-154">ASP.NET Core Web API</span></span>                         | `webapi`         | <span data-ttu-id="a76f0-155">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="a76f0-155">[C#], F#</span></span>      |
| <span data-ttu-id="a76f0-156">Knihovny tříd Razor</span><span class="sxs-lookup"><span data-stu-id="a76f0-156">Razor class library</span></span>                          | `razorclasslib`  | <span data-ttu-id="a76f0-157">[C#]</span><span class="sxs-lookup"><span data-stu-id="a76f0-157">[C#]</span></span>          |
| <span data-ttu-id="a76f0-158">global.json file</span><span class="sxs-lookup"><span data-stu-id="a76f0-158">global.json file</span></span>                             | `globaljson`     |               |
| <span data-ttu-id="a76f0-159">NuGet config</span><span class="sxs-lookup"><span data-stu-id="a76f0-159">NuGet config</span></span>                                 | `nugetconfig`    |               |
| <span data-ttu-id="a76f0-160">Webové konfigurace</span><span class="sxs-lookup"><span data-stu-id="a76f0-160">Web config</span></span>                                   | `webconfig`      |               |
| <span data-ttu-id="a76f0-161">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="a76f0-161">Solution file</span></span>                                | `sln`            |               |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="a76f0-162">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="a76f0-162">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="a76f0-163">Příkaz obsahuje výchozí seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="a76f0-163">The command contains a default list of templates.</span></span> <span data-ttu-id="a76f0-164">Použití `dotnet new -l` získat seznam dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="a76f0-164">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="a76f0-165">V následující tabulce jsou uvedeny šablony, které jsou předem nainstalované s .NET Core SDK 2.0.</span><span class="sxs-lookup"><span data-stu-id="a76f0-165">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.</span></span> <span data-ttu-id="a76f0-166">Výchozí jazyk šablony se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="a76f0-166">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="a76f0-167">Popis šablony</span><span class="sxs-lookup"><span data-stu-id="a76f0-167">Template description</span></span>                          | <span data-ttu-id="a76f0-168">Název šablony</span><span class="sxs-lookup"><span data-stu-id="a76f0-168">Template name</span></span> | <span data-ttu-id="a76f0-169">Jazyky</span><span class="sxs-lookup"><span data-stu-id="a76f0-169">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="a76f0-170">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="a76f0-170">Console application</span></span>                          | `console`     | <span data-ttu-id="a76f0-171">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="a76f0-171">[C#], F#, VB</span></span>  |
| <span data-ttu-id="a76f0-172">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="a76f0-172">Class library</span></span>                                | `classlib`    | <span data-ttu-id="a76f0-173">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="a76f0-173">[C#], F#, VB</span></span>  |
| <span data-ttu-id="a76f0-174">Projekt testu jednotek</span><span class="sxs-lookup"><span data-stu-id="a76f0-174">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="a76f0-175">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="a76f0-175">[C#], F#, VB</span></span>  |
| <span data-ttu-id="a76f0-176">Projekt testů xUnit</span><span class="sxs-lookup"><span data-stu-id="a76f0-176">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="a76f0-177">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="a76f0-177">[C#], F#, VB</span></span>  |
| <span data-ttu-id="a76f0-178">ASP.NET Core je prázdný</span><span class="sxs-lookup"><span data-stu-id="a76f0-178">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="a76f0-179">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="a76f0-179">[C#], F#</span></span>      |
| <span data-ttu-id="a76f0-180">Webové aplikace ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="a76f0-180">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="a76f0-181">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="a76f0-181">[C#], F#</span></span>      |
| <span data-ttu-id="a76f0-182">Webové aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a76f0-182">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="a76f0-183">[C#]</span><span class="sxs-lookup"><span data-stu-id="a76f0-183">[C#]</span></span>          |
| <span data-ttu-id="a76f0-184">ASP.NET Core with Angular</span><span class="sxs-lookup"><span data-stu-id="a76f0-184">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="a76f0-185">[C#]</span><span class="sxs-lookup"><span data-stu-id="a76f0-185">[C#]</span></span>          |
| <span data-ttu-id="a76f0-186">ASP.NET Core pomocí React.js</span><span class="sxs-lookup"><span data-stu-id="a76f0-186">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="a76f0-187">[C#]</span><span class="sxs-lookup"><span data-stu-id="a76f0-187">[C#]</span></span>          |
| <span data-ttu-id="a76f0-188">ASP.NET Core pomocí React.js a Redux</span><span class="sxs-lookup"><span data-stu-id="a76f0-188">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="a76f0-189">[C#]</span><span class="sxs-lookup"><span data-stu-id="a76f0-189">[C#]</span></span>          |
| <span data-ttu-id="a76f0-190">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="a76f0-190">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="a76f0-191">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="a76f0-191">[C#], F#</span></span>      |
| <span data-ttu-id="a76f0-192">global.json file</span><span class="sxs-lookup"><span data-stu-id="a76f0-192">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="a76f0-193">NuGet config</span><span class="sxs-lookup"><span data-stu-id="a76f0-193">NuGet config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="a76f0-194">Webové konfigurace</span><span class="sxs-lookup"><span data-stu-id="a76f0-194">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="a76f0-195">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="a76f0-195">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="a76f0-196">Stránka Razor</span><span class="sxs-lookup"><span data-stu-id="a76f0-196">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="a76f0-197">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="a76f0-197">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="a76f0-198">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="a76f0-198">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a76f0-199">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="a76f0-199">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="a76f0-200">Příkaz obsahuje výchozí seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="a76f0-200">The command contains a default list of templates.</span></span> <span data-ttu-id="a76f0-201">Použití `dotnet new -all` získat seznam dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="a76f0-201">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="a76f0-202">V následující tabulce jsou uvedeny šablony, které jsou předinstalovány se sadou SDK .NET Core 1.x.</span><span class="sxs-lookup"><span data-stu-id="a76f0-202">The following table shows the templates that come pre-installed with the .NET Core SDK 1.x.</span></span> <span data-ttu-id="a76f0-203">Výchozí jazyk šablony se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="a76f0-203">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="a76f0-204">Popis šablony</span><span class="sxs-lookup"><span data-stu-id="a76f0-204">Template description</span></span>  | <span data-ttu-id="a76f0-205">Název šablony</span><span class="sxs-lookup"><span data-stu-id="a76f0-205">Template name</span></span> | <span data-ttu-id="a76f0-206">Jazyky</span><span class="sxs-lookup"><span data-stu-id="a76f0-206">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="a76f0-207">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="a76f0-207">Console application</span></span>  | `console`     | <span data-ttu-id="a76f0-208">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="a76f0-208">[C#], F#</span></span>  |
| <span data-ttu-id="a76f0-209">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="a76f0-209">Class library</span></span>        | `classlib`    | <span data-ttu-id="a76f0-210">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="a76f0-210">[C#], F#</span></span>  |
| <span data-ttu-id="a76f0-211">Projekt testu jednotek</span><span class="sxs-lookup"><span data-stu-id="a76f0-211">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="a76f0-212">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="a76f0-212">[C#], F#</span></span>  |
| <span data-ttu-id="a76f0-213">Projekt testů xUnit</span><span class="sxs-lookup"><span data-stu-id="a76f0-213">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="a76f0-214">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="a76f0-214">[C#], F#</span></span>  |
| <span data-ttu-id="a76f0-215">ASP.NET Core je prázdný</span><span class="sxs-lookup"><span data-stu-id="a76f0-215">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="a76f0-216">[C#]</span><span class="sxs-lookup"><span data-stu-id="a76f0-216">[C#]</span></span>      |
| <span data-ttu-id="a76f0-217">Webové aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a76f0-217">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="a76f0-218">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="a76f0-218">[C#], F#</span></span>  |
| <span data-ttu-id="a76f0-219">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="a76f0-219">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="a76f0-220">[C#]</span><span class="sxs-lookup"><span data-stu-id="a76f0-220">[C#]</span></span>      |
| <span data-ttu-id="a76f0-221">NuGet config</span><span class="sxs-lookup"><span data-stu-id="a76f0-221">NuGet config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="a76f0-222">Webové konfigurace</span><span class="sxs-lookup"><span data-stu-id="a76f0-222">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="a76f0-223">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="a76f0-223">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="a76f0-224">Možnosti</span><span class="sxs-lookup"><span data-stu-id="a76f0-224">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="a76f0-225">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="a76f0-225">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="a76f0-226">Vynutí obsahu chcete vygenerovat i v případě, že by došlo ke změně existujících souborů.</span><span class="sxs-lookup"><span data-stu-id="a76f0-226">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="a76f0-227">To je potřeba při výstupní adresář již obsahuje projekt.</span><span class="sxs-lookup"><span data-stu-id="a76f0-227">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="a76f0-228">Vytiskne nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="a76f0-228">Prints out help for the command.</span></span> <span data-ttu-id="a76f0-229">Může být vyvolána pro `dotnet new` samotný příkaz nebo pro všechny šablony, jako například `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-229">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="a76f0-230">Nainstaluje zdroj nebo šablony pack z `PATH` nebo `NUGET_ID` k dispozici.</span><span class="sxs-lookup"><span data-stu-id="a76f0-230">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="a76f0-231">Pokud chcete nainstalovat zkušební verzi balíčku šablony, je třeba zadat verzi ve formátu `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-231">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="a76f0-232">Ve výchozím nastavení `dotnet new` předá \* pro verzi, která představuje poslední stabilní balíček verze.</span><span class="sxs-lookup"><span data-stu-id="a76f0-232">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="a76f0-233">Podívejte se příklad na [příklady](#examples) oddílu.</span><span class="sxs-lookup"><span data-stu-id="a76f0-233">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="a76f0-234">Informace o vytváření vlastních šablon najdete v tématu [vlastních šablon pro dotnet nové](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="a76f0-234">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="a76f0-235">Zobrazí seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="a76f0-235">Lists templates containing the specified name.</span></span> <span data-ttu-id="a76f0-236">Pokud je vyvolána `dotnet new` příkazu, uvádí možné šablony, které jsou k dispozici pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="a76f0-236">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="a76f0-237">Například pokud adresář, projekt již obsahuje, neobsahuje všechny šablony projektů.</span><span class="sxs-lookup"><span data-stu-id="a76f0-237">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="a76f0-238">Jazyk šablony k vytvoření.</span><span class="sxs-lookup"><span data-stu-id="a76f0-238">The language of the template to create.</span></span> <span data-ttu-id="a76f0-239">Jazyk přijato, se liší podle šablony (Zobrazit výchozí hodnoty v [argumenty](#arguments) části).</span><span class="sxs-lookup"><span data-stu-id="a76f0-239">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="a76f0-240">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="a76f0-240">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="a76f0-241">Některé součásti pro interpretaci `#` jako speciální znak.</span><span class="sxs-lookup"><span data-stu-id="a76f0-241">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="a76f0-242">V takových případech bude nutné uvést hodnotu parametru jazyka, jako `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-242">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="a76f0-243">Název pro výstup vytvořený.</span><span class="sxs-lookup"><span data-stu-id="a76f0-243">The name for the created output.</span></span> <span data-ttu-id="a76f0-244">Pokud není zadán žádný název, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="a76f0-244">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="a76f0-245">Určuje zdroj NuGet, který chcete použít během instalace.</span><span class="sxs-lookup"><span data-stu-id="a76f0-245">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="a76f0-246">Umístění pro vygenerovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="a76f0-246">Location to place the generated output.</span></span> <span data-ttu-id="a76f0-247">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="a76f0-247">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="a76f0-248">Vyfiltruje šablony podle dostupných typů.</span><span class="sxs-lookup"><span data-stu-id="a76f0-248">Filters templates based on available types.</span></span> <span data-ttu-id="a76f0-249">Předdefinované hodnoty jsou "projekt", "item" nebo "jiné".</span><span class="sxs-lookup"><span data-stu-id="a76f0-249">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="a76f0-250">Odinstaluje zdroj nebo šablony pack na `PATH` nebo `NUGET_ID` k dispozici.</span><span class="sxs-lookup"><span data-stu-id="a76f0-250">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="a76f0-251">Chcete-li odinstalovat sadu pomocí šablony `PATH`, budete potřebovat plně kvalifikovanou cestu.</span><span class="sxs-lookup"><span data-stu-id="a76f0-251">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="a76f0-252">Například *C:/uživatele/\<uživatele > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z obsahuje složky nebudou.</span><span class="sxs-lookup"><span data-stu-id="a76f0-252">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="a76f0-253">Kromě toho nesmí být znak konečné ukončující znak lomítka adresáře na cestu k šabloně.</span><span class="sxs-lookup"><span data-stu-id="a76f0-253">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="a76f0-254">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="a76f0-254">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="a76f0-255">Vynutí obsahu chcete vygenerovat i v případě, že by došlo ke změně existujících souborů.</span><span class="sxs-lookup"><span data-stu-id="a76f0-255">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="a76f0-256">To je potřeba při výstupní adresář již obsahuje projekt.</span><span class="sxs-lookup"><span data-stu-id="a76f0-256">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="a76f0-257">Vytiskne nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="a76f0-257">Prints out help for the command.</span></span> <span data-ttu-id="a76f0-258">Může být vyvolána pro `dotnet new` samotný příkaz nebo pro všechny šablony, jako například `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-258">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="a76f0-259">Nainstaluje zdroj nebo šablony pack z `PATH` nebo `NUGET_ID` k dispozici.</span><span class="sxs-lookup"><span data-stu-id="a76f0-259">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="a76f0-260">Pokud chcete nainstalovat zkušební verzi balíčku šablony, je třeba zadat verzi ve formátu `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-260">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="a76f0-261">Ve výchozím nastavení `dotnet new` předá \* pro verzi, která představuje poslední stabilní balíček verze.</span><span class="sxs-lookup"><span data-stu-id="a76f0-261">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="a76f0-262">Podívejte se příklad na [příklady](#examples) oddílu.</span><span class="sxs-lookup"><span data-stu-id="a76f0-262">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="a76f0-263">Informace o vytváření vlastních šablon najdete v tématu [vlastních šablon pro dotnet nové](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="a76f0-263">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="a76f0-264">Zobrazí seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="a76f0-264">Lists templates containing the specified name.</span></span> <span data-ttu-id="a76f0-265">Pokud je vyvolána `dotnet new` příkazu, uvádí možné šablony, které jsou k dispozici pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="a76f0-265">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="a76f0-266">Například pokud adresář, projekt již obsahuje, neobsahuje všechny šablony projektů.</span><span class="sxs-lookup"><span data-stu-id="a76f0-266">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="a76f0-267">Jazyk šablony k vytvoření.</span><span class="sxs-lookup"><span data-stu-id="a76f0-267">The language of the template to create.</span></span> <span data-ttu-id="a76f0-268">Jazyk přijato, se liší podle šablony (Zobrazit výchozí hodnoty v [argumenty](#arguments) části).</span><span class="sxs-lookup"><span data-stu-id="a76f0-268">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="a76f0-269">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="a76f0-269">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="a76f0-270">Některé součásti pro interpretaci `#` jako speciální znak.</span><span class="sxs-lookup"><span data-stu-id="a76f0-270">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="a76f0-271">V takových případech bude nutné uvést hodnotu parametru jazyka, jako `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-271">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="a76f0-272">Název pro výstup vytvořený.</span><span class="sxs-lookup"><span data-stu-id="a76f0-272">The name for the created output.</span></span> <span data-ttu-id="a76f0-273">Pokud není zadán žádný název, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="a76f0-273">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="a76f0-274">Umístění pro vygenerovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="a76f0-274">Location to place the generated output.</span></span> <span data-ttu-id="a76f0-275">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="a76f0-275">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="a76f0-276">Vyfiltruje šablony podle dostupných typů.</span><span class="sxs-lookup"><span data-stu-id="a76f0-276">Filters templates based on available types.</span></span> <span data-ttu-id="a76f0-277">Předdefinované hodnoty jsou "projekt", "item" nebo "jiné".</span><span class="sxs-lookup"><span data-stu-id="a76f0-277">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="a76f0-278">Odinstaluje zdroj nebo šablony pack na `PATH` nebo `NUGET_ID` k dispozici.</span><span class="sxs-lookup"><span data-stu-id="a76f0-278">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="a76f0-279">Odinstalace pomocí zdroj `PATH`, budete potřebovat plně kvalifikovanou cestu.</span><span class="sxs-lookup"><span data-stu-id="a76f0-279">To uninstall a template using a source `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="a76f0-280">Například *C:/uživatele/\<uživatele > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z obsahuje složky nebudou.</span><span class="sxs-lookup"><span data-stu-id="a76f0-280">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span> <span data-ttu-id="a76f0-281">Kromě toho nesmí být znak konečné ukončující znak lomítka adresáře na cestu k šabloně.</span><span class="sxs-lookup"><span data-stu-id="a76f0-281">Additionally, do not include a final terminating directory slash on your template path.</span></span>
> 
> <span data-ttu-id="a76f0-282">Pokud se nemůžete určit `PATH` nebo `NUGET_ID` argumentů potřebných k odinstalaci šablonu s `dotnet new --uninstall` bez argumentu zobrazí seznam všech nainstalovaných šablon a argument nutné je odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="a76f0-282">If you are unable to determine the `PATH` or `NUGET_ID` argument needed to uninstall a template, running `dotnet new --uninstall` without an argument will list all installed templates and the argument required to uninstall them.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a76f0-283">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="a76f0-283">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="a76f0-284">Zobrazí všechny šablony pro konkrétní typ projektu při spuštění v kontextu `dotnet new` samotný příkaz.</span><span class="sxs-lookup"><span data-stu-id="a76f0-284">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="a76f0-285">Při spuštění v kontextu konkrétní šablony, jako například `dotnet new web -all`, `-all` je interpretován jako vytvoření příznak force.</span><span class="sxs-lookup"><span data-stu-id="a76f0-285">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="a76f0-286">To je potřeba při výstupní adresář již obsahuje projekt.</span><span class="sxs-lookup"><span data-stu-id="a76f0-286">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="a76f0-287">Vytiskne nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="a76f0-287">Prints out help for the command.</span></span> <span data-ttu-id="a76f0-288">Může být vyvolána pro `dotnet new` samotný příkaz nebo pro všechny šablony, jako například `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-288">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="a76f0-289">Zobrazí seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="a76f0-289">Lists templates containing the specified name.</span></span> <span data-ttu-id="a76f0-290">Pokud je vyvolána `dotnet new` příkazu, uvádí možné šablony, které jsou k dispozici pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="a76f0-290">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="a76f0-291">Například pokud adresář, projekt již obsahuje, neobsahuje všechny šablony projektů.</span><span class="sxs-lookup"><span data-stu-id="a76f0-291">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="a76f0-292">Jazyk šablony k vytvoření.</span><span class="sxs-lookup"><span data-stu-id="a76f0-292">The language of the template to create.</span></span> <span data-ttu-id="a76f0-293">Jazyk přijato, se liší podle šablony (Zobrazit výchozí hodnoty v [argumenty](#arguments) části).</span><span class="sxs-lookup"><span data-stu-id="a76f0-293">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="a76f0-294">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="a76f0-294">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="a76f0-295">Některé součásti pro interpretaci `#` jako speciální znak.</span><span class="sxs-lookup"><span data-stu-id="a76f0-295">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="a76f0-296">V takových případech bude nutné uvést hodnotu parametru jazyka, jako `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-296">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="a76f0-297">Název pro výstup vytvořený.</span><span class="sxs-lookup"><span data-stu-id="a76f0-297">The name for the created output.</span></span> <span data-ttu-id="a76f0-298">Pokud není zadán žádný název, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="a76f0-298">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="a76f0-299">Umístění pro vygenerovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="a76f0-299">Location to place the generated output.</span></span> <span data-ttu-id="a76f0-300">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="a76f0-300">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="a76f0-301">Nastavení šablony</span><span class="sxs-lookup"><span data-stu-id="a76f0-301">Template options</span></span>

<span data-ttu-id="a76f0-302">Každá šablona projektu může mít k dispozici další možnosti.</span><span class="sxs-lookup"><span data-stu-id="a76f0-302">Each project template may have additional options available.</span></span> <span data-ttu-id="a76f0-303">Základní šablony mají následující další možnosti:</span><span class="sxs-lookup"><span data-stu-id="a76f0-303">The core templates have the following additional options:</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="a76f0-304">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="a76f0-304">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="a76f0-305">**console, angular, react, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="a76f0-305">**console, angular, react, reactredux, razorclasslib**</span></span>

  <span data-ttu-id="a76f0-306">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="a76f0-306">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="a76f0-307">**classlib**</span><span class="sxs-lookup"><span data-stu-id="a76f0-307">**classlib**</span></span>

<span data-ttu-id="a76f0-308">`-f|--framework <FRAMEWORK>` : Určuje, že [framework](../../standard/frameworks.md) do cíle.</span><span class="sxs-lookup"><span data-stu-id="a76f0-308">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="a76f0-309">Hodnoty: `netcoreapp2.0` k vytvoření knihovny tříd .NET Core nebo `netstandard2.0` k vytvoření knihovny tříd .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="a76f0-309">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="a76f0-310">Výchozí hodnota je `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-310">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="a76f0-311">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="a76f0-311">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="a76f0-312">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="a76f0-312">**mstest, xunit**</span></span>

<span data-ttu-id="a76f0-313">`-p|--enable-pack` – Povolí balení pro projekt pomocí [balíčku dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="a76f0-313">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="a76f0-314">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="a76f0-314">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="a76f0-315">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="a76f0-315">**globaljson**</span></span>

<span data-ttu-id="a76f0-316">`--sdk-version <VERSION_NUMBER>` : Určuje verzi .NET Core SDK pro použití v *global.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="a76f0-316">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="a76f0-317">**web**</span><span class="sxs-lookup"><span data-stu-id="a76f0-317">**web**</span></span>

<span data-ttu-id="a76f0-318">`--exclude-launch-settings` -Vyloučení *launchSettings.json* z vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="a76f0-318">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="a76f0-319">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="a76f0-319">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="a76f0-320">`--no-https` -Projektu nebude vyžadovat protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a76f0-320">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="a76f0-321">Tato možnost platí, pouze pokud `IndividualAuth` nebo `OrganizationalAuth` nejsou používány.</span><span class="sxs-lookup"><span data-stu-id="a76f0-321">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="a76f0-322">**webapi**</span><span class="sxs-lookup"><span data-stu-id="a76f0-322">**webapi**</span></span>

<span data-ttu-id="a76f0-323">`-au|--auth <AUTHENTICATION_TYPE>` -Typ ověřování, který má použít.</span><span class="sxs-lookup"><span data-stu-id="a76f0-323">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="a76f0-324">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="a76f0-324">The possible values are:</span></span>

- <span data-ttu-id="a76f0-325">`None` -Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="a76f0-325">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="a76f0-326">`IndividualB2C` -Jednotlivé ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="a76f0-326">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="a76f0-327">`SingleOrg` – Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="a76f0-327">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="a76f0-328">`Windows` -Ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="a76f0-328">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="a76f0-329">`--aad-b2c-instance <INSTANCE>` -Instanci Azure Active Directory B2C pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="a76f0-329">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="a76f0-330">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-330">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="a76f0-331">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-331">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="a76f0-332">`-ssp|--susi-policy-id <ID>` – ID přihlášení a registraci zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="a76f0-332">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="a76f0-333">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-333">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="a76f0-334">`--aad-instance <INSTANCE>` – Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="a76f0-334">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="a76f0-335">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-335">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="a76f0-336">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-336">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="a76f0-337">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="a76f0-337">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="a76f0-338">Použití s `IndividualB2C` nebo `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-338">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="a76f0-339">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-339">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="a76f0-340">`--domain <DOMAIN>` -Domény tenantu Active directory.</span><span class="sxs-lookup"><span data-stu-id="a76f0-340">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="a76f0-341">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-341">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="a76f0-342">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-342">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="a76f0-343">`--tenant-id <ID>` – ID Tenanta ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="a76f0-343">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="a76f0-344">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-344">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="a76f0-345">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-345">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="a76f0-346">`-r|--org-read-access` – Povolí této aplikaci přístup pro čtení do adresáře.</span><span class="sxs-lookup"><span data-stu-id="a76f0-346">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="a76f0-347">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-347">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="a76f0-348">`--exclude-launch-settings` -Vyloučení *launchSettings.json* z vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="a76f0-348">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="a76f0-349">`-uld|--use-local-db` : Určuje, že by měl být LocalDB použít místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="a76f0-349">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="a76f0-350">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-350">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="a76f0-351">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="a76f0-351">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="a76f0-352">`--no-https` -Projektu nebude vyžadovat protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a76f0-352">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="a76f0-353">`app.UseHsts` a `app.UseHttpsRedirection` nejsou přidány do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-353">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="a76f0-354">Tato možnost platí, pouze pokud `Individual`, `IndividualB2C`, `SingleOrg`, nebo `MultiOrg` nejsou používány.</span><span class="sxs-lookup"><span data-stu-id="a76f0-354">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="a76f0-355">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="a76f0-355">**mvc, razor**</span></span>

<span data-ttu-id="a76f0-356">`-au|--auth <AUTHENTICATION_TYPE>` -Typ ověřování, který má použít.</span><span class="sxs-lookup"><span data-stu-id="a76f0-356">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="a76f0-357">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="a76f0-357">The possible values are:</span></span>

- <span data-ttu-id="a76f0-358">`None` -Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="a76f0-358">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="a76f0-359">`Individual` -Jednotlivé ověřování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-359">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="a76f0-360">`IndividualB2C` -Jednotlivé ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="a76f0-360">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="a76f0-361">`SingleOrg` – Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="a76f0-361">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="a76f0-362">`MultiOrg` – Ověřování organizace pro více tenantů.</span><span class="sxs-lookup"><span data-stu-id="a76f0-362">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="a76f0-363">`Windows` -Ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="a76f0-363">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="a76f0-364">`--aad-b2c-instance <INSTANCE>` -Instanci Azure Active Directory B2C pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="a76f0-364">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="a76f0-365">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-365">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="a76f0-366">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-366">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="a76f0-367">`-ssp|--susi-policy-id <ID>` – ID přihlášení a registraci zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="a76f0-367">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="a76f0-368">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-368">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="a76f0-369">`-rp|--reset-password-policy-id <ID>` -Resetování hesla ID zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="a76f0-369">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="a76f0-370">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-370">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="a76f0-371">`-ep|--edit-profile-policy-id <ID>` – Upravit profil zásady ID pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="a76f0-371">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="a76f0-372">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-372">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="a76f0-373">`--aad-instance <INSTANCE>` – Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="a76f0-373">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="a76f0-374">Použití s `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-374">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="a76f0-375">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-375">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="a76f0-376">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="a76f0-376">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="a76f0-377">Použití s `IndividualB2C`, `SingleOrg`, nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-377">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="a76f0-378">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-378">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="a76f0-379">`--domain <DOMAIN>` -Domény tenantu Active directory.</span><span class="sxs-lookup"><span data-stu-id="a76f0-379">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="a76f0-380">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-380">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="a76f0-381">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-381">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="a76f0-382">`--tenant-id <ID>` – ID Tenanta ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="a76f0-382">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="a76f0-383">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-383">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="a76f0-384">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-384">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="a76f0-385">`--callback-path <PATH>` -Cestu požadavku v rámci základní cesty aplikace identifikátoru URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-385">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="a76f0-386">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-386">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="a76f0-387">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-387">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="a76f0-388">`-r|--org-read-access` – Povolí této aplikaci přístup pro čtení do adresáře.</span><span class="sxs-lookup"><span data-stu-id="a76f0-388">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="a76f0-389">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-389">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="a76f0-390">`--exclude-launch-settings` -Vyloučení *launchSettings.json* z vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="a76f0-390">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="a76f0-391">`--use-browserlink` -Obsahuje BrowserLink v projektu.</span><span class="sxs-lookup"><span data-stu-id="a76f0-391">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="a76f0-392">`-uld|--use-local-db` : Určuje, že by měl být LocalDB použít místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="a76f0-392">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="a76f0-393">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-393">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="a76f0-394">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="a76f0-394">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="a76f0-395">`--no-https` -Projektu nebude vyžadovat protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a76f0-395">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="a76f0-396">`app.UseHsts` a `app.UseHttpsRedirection` nejsou přidány do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-396">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="a76f0-397">Tato možnost platí, pouze pokud `Individual`, `IndividualB2C`, `SingleOrg`, nebo `MultiOrg` nejsou používány.</span><span class="sxs-lookup"><span data-stu-id="a76f0-397">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="a76f0-398">**Stránka**</span><span class="sxs-lookup"><span data-stu-id="a76f0-398">**page**</span></span>

<span data-ttu-id="a76f0-399">`-na|--namespace <NAMESPACE_NAME>`-Namespace pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="a76f0-399">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="a76f0-400">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-400">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="a76f0-401">`-np|--no-pagemodel` -Vytvoří danou stránku bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="a76f0-401">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="a76f0-402">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="a76f0-402">**viewimports**</span></span>

<span data-ttu-id="a76f0-403">`-na|--namespace <NAMESPACE_NAME>`-Namespace pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="a76f0-403">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="a76f0-404">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-404">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="a76f0-405">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="a76f0-405">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="a76f0-406">**konzola, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="a76f0-406">**console, angular, react, reactredux**</span></span>

  <span data-ttu-id="a76f0-407">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="a76f0-407">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="a76f0-408">**classlib**</span><span class="sxs-lookup"><span data-stu-id="a76f0-408">**classlib**</span></span>

<span data-ttu-id="a76f0-409">`-f|--framework <FRAMEWORK>` : Určuje, že [framework](../../standard/frameworks.md) do cíle.</span><span class="sxs-lookup"><span data-stu-id="a76f0-409">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="a76f0-410">Hodnoty: `netcoreapp2.0` k vytvoření knihovny tříd .NET Core nebo `netstandard2.0` k vytvoření knihovny tříd .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="a76f0-410">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="a76f0-411">Výchozí hodnota je `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-411">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="a76f0-412">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="a76f0-412">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="a76f0-413">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="a76f0-413">**mstest, xunit**</span></span>

<span data-ttu-id="a76f0-414">`-p|--enable-pack` – Povolí balení pro projekt pomocí [balíčku dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="a76f0-414">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="a76f0-415">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="a76f0-415">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="a76f0-416">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="a76f0-416">**globaljson**</span></span>

<span data-ttu-id="a76f0-417">`--sdk-version <VERSION_NUMBER>` : Určuje verzi .NET Core SDK pro použití v *global.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="a76f0-417">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="a76f0-418">**web**</span><span class="sxs-lookup"><span data-stu-id="a76f0-418">**web**</span></span>

<span data-ttu-id="a76f0-419">`--use-launch-settings` -Zahrnuje *launchSettings.json* ve výstupu vygenerovanou šablonu.</span><span class="sxs-lookup"><span data-stu-id="a76f0-419">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="a76f0-420">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="a76f0-420">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="a76f0-421">**webapi**</span><span class="sxs-lookup"><span data-stu-id="a76f0-421">**webapi**</span></span>

<span data-ttu-id="a76f0-422">`-au|--auth <AUTHENTICATION_TYPE>` -Typ ověřování, který má použít.</span><span class="sxs-lookup"><span data-stu-id="a76f0-422">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="a76f0-423">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="a76f0-423">The possible values are:</span></span>

- <span data-ttu-id="a76f0-424">`None` -Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="a76f0-424">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="a76f0-425">`IndividualB2C` -Jednotlivé ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="a76f0-425">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="a76f0-426">`SingleOrg` – Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="a76f0-426">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="a76f0-427">`Windows` -Ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="a76f0-427">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="a76f0-428">`--aad-b2c-instance <INSTANCE>` -Instanci Azure Active Directory B2C pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="a76f0-428">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="a76f0-429">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-429">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="a76f0-430">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-430">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="a76f0-431">`-ssp|--susi-policy-id <ID>` – ID přihlášení a registraci zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="a76f0-431">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="a76f0-432">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-432">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="a76f0-433">`--aad-instance <INSTANCE>` – Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="a76f0-433">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="a76f0-434">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-434">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="a76f0-435">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-435">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="a76f0-436">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="a76f0-436">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="a76f0-437">Použití s `IndividualB2C` nebo `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-437">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="a76f0-438">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-438">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="a76f0-439">`--domain <DOMAIN>` -Domény tenantu Active directory.</span><span class="sxs-lookup"><span data-stu-id="a76f0-439">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="a76f0-440">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-440">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="a76f0-441">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-441">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="a76f0-442">`--tenant-id <ID>` – ID Tenanta ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="a76f0-442">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="a76f0-443">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-443">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="a76f0-444">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-444">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="a76f0-445">`-r|--org-read-access` – Povolí této aplikaci přístup pro čtení do adresáře.</span><span class="sxs-lookup"><span data-stu-id="a76f0-445">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="a76f0-446">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-446">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="a76f0-447">`--use-launch-settings` -Zahrnuje *launchSettings.json* ve výstupu vygenerovanou šablonu.</span><span class="sxs-lookup"><span data-stu-id="a76f0-447">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="a76f0-448">`-uld|--use-local-db` : Určuje, že by měl být LocalDB použít místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="a76f0-448">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="a76f0-449">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-449">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="a76f0-450">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="a76f0-450">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="a76f0-451">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="a76f0-451">**mvc, razor**</span></span>

<span data-ttu-id="a76f0-452">`-au|--auth <AUTHENTICATION_TYPE>` -Typ ověřování, který má použít.</span><span class="sxs-lookup"><span data-stu-id="a76f0-452">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="a76f0-453">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="a76f0-453">The possible values are:</span></span>

- <span data-ttu-id="a76f0-454">`None` -Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="a76f0-454">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="a76f0-455">`Individual` -Jednotlivé ověřování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-455">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="a76f0-456">`IndividualB2C` -Jednotlivé ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="a76f0-456">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="a76f0-457">`SingleOrg` – Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="a76f0-457">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="a76f0-458">`MultiOrg` – Ověřování organizace pro více tenantů.</span><span class="sxs-lookup"><span data-stu-id="a76f0-458">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="a76f0-459">`Windows` -Ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="a76f0-459">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="a76f0-460">`--aad-b2c-instance <INSTANCE>` -Instanci Azure Active Directory B2C pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="a76f0-460">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="a76f0-461">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-461">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="a76f0-462">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-462">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="a76f0-463">`-ssp|--susi-policy-id <ID>` – ID přihlášení a registraci zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="a76f0-463">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="a76f0-464">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-464">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="a76f0-465">`-rp|--reset-password-policy-id <ID>` -Resetování hesla ID zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="a76f0-465">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="a76f0-466">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-466">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="a76f0-467">`-ep|--edit-profile-policy-id <ID>` – Upravit profil zásady ID pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="a76f0-467">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="a76f0-468">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-468">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="a76f0-469">`--aad-instance <INSTANCE>` – Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="a76f0-469">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="a76f0-470">Použití s `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-470">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="a76f0-471">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-471">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="a76f0-472">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="a76f0-472">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="a76f0-473">Použití s `IndividualB2C`, `SingleOrg`, nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-473">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="a76f0-474">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-474">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="a76f0-475">`--domain <DOMAIN>` -Domény tenantu Active directory.</span><span class="sxs-lookup"><span data-stu-id="a76f0-475">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="a76f0-476">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-476">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="a76f0-477">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-477">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="a76f0-478">`--tenant-id <ID>` – ID Tenanta ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="a76f0-478">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="a76f0-479">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-479">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="a76f0-480">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-480">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="a76f0-481">`--callback-path <PATH>` -Cestu požadavku v rámci základní cesty aplikace identifikátoru URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-481">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="a76f0-482">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-482">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="a76f0-483">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-483">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="a76f0-484">`-r|--org-read-access` – Povolí této aplikaci přístup pro čtení do adresáře.</span><span class="sxs-lookup"><span data-stu-id="a76f0-484">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="a76f0-485">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-485">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="a76f0-486">`--use-launch-settings` -Zahrnuje *launchSettings.json* ve výstupu vygenerovanou šablonu.</span><span class="sxs-lookup"><span data-stu-id="a76f0-486">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="a76f0-487">`--use-browserlink` -Obsahuje BrowserLink v projektu.</span><span class="sxs-lookup"><span data-stu-id="a76f0-487">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="a76f0-488">`-uld|--use-local-db` : Určuje, že by měl být LocalDB použít místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="a76f0-488">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="a76f0-489">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="a76f0-489">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="a76f0-490">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="a76f0-490">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="a76f0-491">**Stránka**</span><span class="sxs-lookup"><span data-stu-id="a76f0-491">**page**</span></span>

<span data-ttu-id="a76f0-492">`-na|--namespace <NAMESPACE_NAME>`-Namespace pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="a76f0-492">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="a76f0-493">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-493">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="a76f0-494">`-np|--no-pagemodel` -Vytvoří danou stránku bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="a76f0-494">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="a76f0-495">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="a76f0-495">**viewimports**</span></span>

<span data-ttu-id="a76f0-496">`-na|--namespace <NAMESPACE_NAME>`-Namespace pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="a76f0-496">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="a76f0-497">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-497">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a76f0-498">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="a76f0-498">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="a76f0-499">**konzola, xunit, mstest, web, webapi**</span><span class="sxs-lookup"><span data-stu-id="a76f0-499">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="a76f0-500">`-f|--framework` : Určuje, že [framework](../../standard/frameworks.md) do cíle.</span><span class="sxs-lookup"><span data-stu-id="a76f0-500">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="a76f0-501">Hodnoty: `netcoreapp1.0` nebo `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-501">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="a76f0-502">Výchozí hodnota je `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-502">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="a76f0-503">**classlib**</span><span class="sxs-lookup"><span data-stu-id="a76f0-503">**classlib**</span></span>

<span data-ttu-id="a76f0-504">`-f|--framework` : Určuje, že [framework](../../standard/frameworks.md) do cíle.</span><span class="sxs-lookup"><span data-stu-id="a76f0-504">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="a76f0-505">Hodnoty: `netcoreapp1.0`, `netcoreapp1.1`, nebo `netstandard1.0` k `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-505">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="a76f0-506">Výchozí hodnota je `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-506">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="a76f0-507">**mvc**</span><span class="sxs-lookup"><span data-stu-id="a76f0-507">**mvc**</span></span>

<span data-ttu-id="a76f0-508">`-f|--framework` : Určuje, že [framework](../../standard/frameworks.md) do cíle.</span><span class="sxs-lookup"><span data-stu-id="a76f0-508">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="a76f0-509">Hodnoty: `netcoreapp1.0` nebo `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-509">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="a76f0-510">Výchozí hodnota je `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-510">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="a76f0-511">`-au|--auth` -Typ ověřování, který má použít.</span><span class="sxs-lookup"><span data-stu-id="a76f0-511">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="a76f0-512">Hodnoty: `None` nebo `Individual`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-512">Values: `None` or `Individual`.</span></span> <span data-ttu-id="a76f0-513">Výchozí hodnota je `None`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-513">The default value is `None`.</span></span>

<span data-ttu-id="a76f0-514">`-uld|--use-local-db` : Určuje, jestli se mají použít databázi LocalDB místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="a76f0-514">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="a76f0-515">Hodnoty: `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-515">Values: `true` or `false`.</span></span> <span data-ttu-id="a76f0-516">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="a76f0-516">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="a76f0-517">Příklady</span><span class="sxs-lookup"><span data-stu-id="a76f0-517">Examples</span></span>

<span data-ttu-id="a76f0-518">Vytvoření F# projekt konzolové aplikace v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="a76f0-518">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="a76f0-519">Vytvořte projekt knihovny tříd .NET Standard v zadaném adresáři (k dispozici pouze s .NET Core SDK 2.0 a novějšími verzemi):</span><span class="sxs-lookup"><span data-stu-id="a76f0-519">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="a76f0-520">Vytvoření nového projektu aplikace ASP.NET Core C# MVC v aktuálním adresáři bez ověřování:</span><span class="sxs-lookup"><span data-stu-id="a76f0-520">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="a76f0-521">Vytvořte novou aplikaci xUnit:</span><span class="sxs-lookup"><span data-stu-id="a76f0-521">Create a new xUnit application:</span></span>

`dotnet new xunit`

<span data-ttu-id="a76f0-522">Seznam všech šablon, které jsou k dispozici pro rozhraní MVC:</span><span class="sxs-lookup"><span data-stu-id="a76f0-522">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="a76f0-523">Instalace verze 2.0 šablon jednostránkové aplikace ASP.NET Core (příkaz Možnosti dostupné pro .NET Core SDK 1.1 a novějších verzích pouze):</span><span class="sxs-lookup"><span data-stu-id="a76f0-523">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="a76f0-524">Vytvoření *global.json* v aktuálním adresáři nastavení sady SDK verze 2.0.0 (k dispozici pouze s .NET Core SDK 2.0 a novějšími verzemi):</span><span class="sxs-lookup"><span data-stu-id="a76f0-524">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="a76f0-525">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a76f0-525">See also</span></span>

- [<span data-ttu-id="a76f0-526">Vlastních šablon pro dotnet nové</span><span class="sxs-lookup"><span data-stu-id="a76f0-526">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="a76f0-527">Vytvoření vlastní šablony pro dotnet new</span><span class="sxs-lookup"><span data-stu-id="a76f0-527">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)
- [<span data-ttu-id="a76f0-528">úložiště GitHub DotNet/dotnet – šablony – ukázky</span><span class="sxs-lookup"><span data-stu-id="a76f0-528">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="a76f0-529">Dostupné šablony pro dotnet nové</span><span class="sxs-lookup"><span data-stu-id="a76f0-529">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
