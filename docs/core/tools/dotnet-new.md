---
title: dotnet – nový příkaz
description: Příkaz dotnet New vytvoří nové projekty .NET Core založené na zadané šabloně.
ms.date: 05/06/2019
ms.openlocfilehash: c9529e135f48c80f445c91038294a3e7266486f1
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73420479"
---
# <a name="dotnet-new"></a><span data-ttu-id="c6775-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="c6775-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="c6775-104">Name</span><span class="sxs-lookup"><span data-stu-id="c6775-104">Name</span></span>

<span data-ttu-id="c6775-105">`dotnet new` – vytvoří nový projekt, konfigurační soubor nebo řešení na základě zadané šablony.</span><span class="sxs-lookup"><span data-stu-id="c6775-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c6775-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="c6775-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="c6775-107">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="c6775-107">.NET Core 2.2</span></span>](#tab/netcore22)

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="c6775-108">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="c6775-108">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="c6775-109">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="c6775-109">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c6775-110">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="c6775-110">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="c6775-111">Popis</span><span class="sxs-lookup"><span data-stu-id="c6775-111">Description</span></span>

<span data-ttu-id="c6775-112">Příkaz `dotnet new` poskytuje pohodlný způsob, jak inicializovat platný projekt .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c6775-112">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="c6775-113">Příkaz volá [modul šablony](https://github.com/dotnet/templating) a vytvoří artefakty na disku na základě zadané šablony a možností.</span><span class="sxs-lookup"><span data-stu-id="c6775-113">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="c6775-114">Arguments</span><span class="sxs-lookup"><span data-stu-id="c6775-114">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="c6775-115">Šablona, která se má vytvořit při vyvolání příkazu</span><span class="sxs-lookup"><span data-stu-id="c6775-115">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="c6775-116">Každá šablona může mít konkrétní možnosti, které můžete předat.</span><span class="sxs-lookup"><span data-stu-id="c6775-116">Each template might have specific options you can pass.</span></span> <span data-ttu-id="c6775-117">Další informace najdete v tématu [Možnosti šablony](#template-options).</span><span class="sxs-lookup"><span data-stu-id="c6775-117">For more information, see [Template options](#template-options).</span></span>

<span data-ttu-id="c6775-118">Pokud hodnota `TEMPLATE` není přesná shoda na textu v **šablonách** nebo ve sloupci **short name** , je v těchto dvou sloupcích provedena shoda s podřetězcem.</span><span class="sxs-lookup"><span data-stu-id="c6775-118">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column, a substring match is performed on those two columns.</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="c6775-119">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="c6775-119">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="c6775-120">Příkaz obsahuje výchozí seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="c6775-120">The command contains a default list of templates.</span></span> <span data-ttu-id="c6775-121">Seznam dostupných šablon můžete získat pomocí `dotnet new -l`.</span><span class="sxs-lookup"><span data-stu-id="c6775-121">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="c6775-122">Následující tabulka obsahuje šablony, které jsou předinstalované s .NET Core SDK 2.2.100.</span><span class="sxs-lookup"><span data-stu-id="c6775-122">The following table shows the templates that come pre-installed with the .NET Core SDK 2.2.100.</span></span> <span data-ttu-id="c6775-123">Výchozí jazyk pro šablonu se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="c6775-123">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="c6775-124">Šablony</span><span class="sxs-lookup"><span data-stu-id="c6775-124">Templates</span></span>                                    | <span data-ttu-id="c6775-125">Krátký název</span><span class="sxs-lookup"><span data-stu-id="c6775-125">Short Name</span></span>        | <span data-ttu-id="c6775-126">Jazyk</span><span class="sxs-lookup"><span data-stu-id="c6775-126">Language</span></span>     | <span data-ttu-id="c6775-127">Značky</span><span class="sxs-lookup"><span data-stu-id="c6775-127">Tags</span></span>                                  |
|----------------------------------------------|-------------------|--------------|---------------------------------------|
| <span data-ttu-id="c6775-128">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="c6775-128">Console Application</span></span>                          | `console`         | <span data-ttu-id="c6775-129">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c6775-129">[C#], F#, VB</span></span> | <span data-ttu-id="c6775-130">Společná/konzola</span><span class="sxs-lookup"><span data-stu-id="c6775-130">Common/Console</span></span>                        |
| <span data-ttu-id="c6775-131">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="c6775-131">Class library</span></span>                                | `classlib`        | <span data-ttu-id="c6775-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c6775-132">[C#], F#, VB</span></span> | <span data-ttu-id="c6775-133">Společné/knihovny</span><span class="sxs-lookup"><span data-stu-id="c6775-133">Common/Library</span></span>                        |
| <span data-ttu-id="c6775-134">Projekt testu jednotek</span><span class="sxs-lookup"><span data-stu-id="c6775-134">Unit Test Project</span></span>                            | `mstest`          | <span data-ttu-id="c6775-135">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c6775-135">[C#], F#, VB</span></span> | <span data-ttu-id="c6775-136">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="c6775-136">Test/MSTest</span></span>                           |
| <span data-ttu-id="c6775-137">Projekt testů NUnit 3</span><span class="sxs-lookup"><span data-stu-id="c6775-137">NUnit 3 Test Project</span></span>                         | `nunit`           | <span data-ttu-id="c6775-138">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c6775-138">[C#], F#, VB</span></span> | <span data-ttu-id="c6775-139">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="c6775-139">Test/NUnit</span></span>                            |
| <span data-ttu-id="c6775-140">NUnit 3 položka testu</span><span class="sxs-lookup"><span data-stu-id="c6775-140">NUnit 3 Test Item</span></span>                            | `nunit-test`      | <span data-ttu-id="c6775-141">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c6775-141">[C#], F#, VB</span></span> | <span data-ttu-id="c6775-142">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="c6775-142">Test/NUnit</span></span>                            |
| <span data-ttu-id="c6775-143">Projekt testů xUnit</span><span class="sxs-lookup"><span data-stu-id="c6775-143">xUnit Test Project</span></span>                           | `xunit`           | <span data-ttu-id="c6775-144">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c6775-144">[C#], F#, VB</span></span> | <span data-ttu-id="c6775-145">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="c6775-145">Test/xUnit</span></span>                            |
| <span data-ttu-id="c6775-146">Stránka Razor</span><span class="sxs-lookup"><span data-stu-id="c6775-146">Razor Page</span></span>                                   | `page`            | <span data-ttu-id="c6775-147">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6775-147">[C#]</span></span>         | <span data-ttu-id="c6775-148">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="c6775-148">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="c6775-149">ViewImports MVC</span><span class="sxs-lookup"><span data-stu-id="c6775-149">MVC ViewImports</span></span>                              | `viewimports`     | <span data-ttu-id="c6775-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6775-150">[C#]</span></span>         | <span data-ttu-id="c6775-151">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="c6775-151">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="c6775-152">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="c6775-152">MVC ViewStart</span></span>                                | `viewstart`       | <span data-ttu-id="c6775-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6775-153">[C#]</span></span>         | <span data-ttu-id="c6775-154">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="c6775-154">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="c6775-155">ASP.NET Core prázdné</span><span class="sxs-lookup"><span data-stu-id="c6775-155">ASP.NET Core Empty</span></span>                           | `web`             | <span data-ttu-id="c6775-156">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="c6775-156">[C#], F#</span></span>     | <span data-ttu-id="c6775-157">Web/prázdné</span><span class="sxs-lookup"><span data-stu-id="c6775-157">Web/Empty</span></span>                             |
| <span data-ttu-id="c6775-158">ASP.NET Core webová aplikace (model-zobrazení-kontroler)</span><span class="sxs-lookup"><span data-stu-id="c6775-158">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`             | <span data-ttu-id="c6775-159">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="c6775-159">[C#], F#</span></span>     | <span data-ttu-id="c6775-160">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="c6775-160">Web/MVC</span></span>                               |
| <span data-ttu-id="c6775-161">ASP.NET Core webové aplikace</span><span class="sxs-lookup"><span data-stu-id="c6775-161">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="c6775-162">`webapp``razor`</span><span class="sxs-lookup"><span data-stu-id="c6775-162">`webapp`, `razor`</span></span> | <span data-ttu-id="c6775-163">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6775-163">[C#]</span></span>         | <span data-ttu-id="c6775-164">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="c6775-164">Web/MVC/Razor Pages</span></span>                   |
| <span data-ttu-id="c6775-165">ASP.NET Core s úhlovým</span><span class="sxs-lookup"><span data-stu-id="c6775-165">ASP.NET Core with Angular</span></span>                    | `angular`         | <span data-ttu-id="c6775-166">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6775-166">[C#]</span></span>         | <span data-ttu-id="c6775-167">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="c6775-167">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="c6775-168">ASP.NET Core s reagují. js</span><span class="sxs-lookup"><span data-stu-id="c6775-168">ASP.NET Core with React.js</span></span>                   | `react`           | <span data-ttu-id="c6775-169">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6775-169">[C#]</span></span>         | <span data-ttu-id="c6775-170">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="c6775-170">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="c6775-171">ASP.NET Core s využitím reagují. js a Redux</span><span class="sxs-lookup"><span data-stu-id="c6775-171">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`      | <span data-ttu-id="c6775-172">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6775-172">[C#]</span></span>         | <span data-ttu-id="c6775-173">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="c6775-173">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="c6775-174">Knihovna tříd Razor</span><span class="sxs-lookup"><span data-stu-id="c6775-174">Razor Class Library</span></span>                          | `razorclasslib`   | <span data-ttu-id="c6775-175">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6775-175">[C#]</span></span>         | <span data-ttu-id="c6775-176">Knihovna tříd web/Razor/Library/Razor</span><span class="sxs-lookup"><span data-stu-id="c6775-176">Web/Razor/Library/Razor Class Library</span></span> |
| <span data-ttu-id="c6775-177">ASP.NET Core webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="c6775-177">ASP.NET Core Web API</span></span>                         | `webapi`          | <span data-ttu-id="c6775-178">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="c6775-178">[C#], F#</span></span>     | <span data-ttu-id="c6775-179">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="c6775-179">Web/WebAPI</span></span>                            |
| <span data-ttu-id="c6775-180">soubor Global. JSON</span><span class="sxs-lookup"><span data-stu-id="c6775-180">global.json file</span></span>                             | `globaljson`      |              | <span data-ttu-id="c6775-181">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="c6775-181">Config</span></span>                                |
| <span data-ttu-id="c6775-182">Konfigurace NuGet</span><span class="sxs-lookup"><span data-stu-id="c6775-182">NuGet Config</span></span>                                 | `nugetconfig`     |              | <span data-ttu-id="c6775-183">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="c6775-183">Config</span></span>                                |
| <span data-ttu-id="c6775-184">Webová konfigurace</span><span class="sxs-lookup"><span data-stu-id="c6775-184">Web Config</span></span>                                   | `webconfig`       |              | <span data-ttu-id="c6775-185">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="c6775-185">Config</span></span>                                |
| <span data-ttu-id="c6775-186">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="c6775-186">Solution File</span></span>                                | `sln`             |              | <span data-ttu-id="c6775-187">Řešení</span><span class="sxs-lookup"><span data-stu-id="c6775-187">Solution</span></span>                              |

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="c6775-188">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="c6775-188">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="c6775-189">Příkaz obsahuje výchozí seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="c6775-189">The command contains a default list of templates.</span></span> <span data-ttu-id="c6775-190">Seznam dostupných šablon můžete získat pomocí `dotnet new -l`.</span><span class="sxs-lookup"><span data-stu-id="c6775-190">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="c6775-191">Následující tabulka obsahuje šablony, které jsou předinstalované s .NET Core SDK 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="c6775-191">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="c6775-192">Výchozí jazyk pro šablonu se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="c6775-192">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="c6775-193">Šablony</span><span class="sxs-lookup"><span data-stu-id="c6775-193">Templates</span></span>                                    | <span data-ttu-id="c6775-194">Krátký název</span><span class="sxs-lookup"><span data-stu-id="c6775-194">Short Name</span></span>      | <span data-ttu-id="c6775-195">Jazyk</span><span class="sxs-lookup"><span data-stu-id="c6775-195">Language</span></span>     | <span data-ttu-id="c6775-196">Značky</span><span class="sxs-lookup"><span data-stu-id="c6775-196">Tags</span></span>                                  |
|----------------------------------------------|-----------------|--------------|---------------------------------------|
| <span data-ttu-id="c6775-197">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="c6775-197">Console Application</span></span>                          | `console`       | <span data-ttu-id="c6775-198">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c6775-198">[C#], F#, VB</span></span> | <span data-ttu-id="c6775-199">Společná/konzola</span><span class="sxs-lookup"><span data-stu-id="c6775-199">Common/Console</span></span>                        |
| <span data-ttu-id="c6775-200">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="c6775-200">Class library</span></span>                                | `classlib`      | <span data-ttu-id="c6775-201">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c6775-201">[C#], F#, VB</span></span> | <span data-ttu-id="c6775-202">Společné/knihovny</span><span class="sxs-lookup"><span data-stu-id="c6775-202">Common/Library</span></span>                        |
| <span data-ttu-id="c6775-203">Projekt testu jednotek</span><span class="sxs-lookup"><span data-stu-id="c6775-203">Unit Test Project</span></span>                            | `mstest`        | <span data-ttu-id="c6775-204">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c6775-204">[C#], F#, VB</span></span> | <span data-ttu-id="c6775-205">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="c6775-205">Test/MSTest</span></span>                           |
| <span data-ttu-id="c6775-206">Projekt testů xUnit</span><span class="sxs-lookup"><span data-stu-id="c6775-206">xUnit Test Project</span></span>                           | `xunit`         | <span data-ttu-id="c6775-207">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c6775-207">[C#], F#, VB</span></span> | <span data-ttu-id="c6775-208">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="c6775-208">Test/xUnit</span></span>                            |
| <span data-ttu-id="c6775-209">Stránka Razor</span><span class="sxs-lookup"><span data-stu-id="c6775-209">Razor Page</span></span>                                   | `page`          | <span data-ttu-id="c6775-210">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6775-210">[C#]</span></span>         | <span data-ttu-id="c6775-211">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="c6775-211">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="c6775-212">ViewImports MVC</span><span class="sxs-lookup"><span data-stu-id="c6775-212">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="c6775-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6775-213">[C#]</span></span>         | <span data-ttu-id="c6775-214">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="c6775-214">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="c6775-215">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="c6775-215">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="c6775-216">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6775-216">[C#]</span></span>         | <span data-ttu-id="c6775-217">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="c6775-217">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="c6775-218">ASP.NET Core prázdné</span><span class="sxs-lookup"><span data-stu-id="c6775-218">ASP.NET Core Empty</span></span>                           | `web`           | <span data-ttu-id="c6775-219">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="c6775-219">[C#], F#</span></span>     | <span data-ttu-id="c6775-220">Web/prázdné</span><span class="sxs-lookup"><span data-stu-id="c6775-220">Web/Empty</span></span>                             |
| <span data-ttu-id="c6775-221">ASP.NET Core webová aplikace (model-zobrazení-kontroler)</span><span class="sxs-lookup"><span data-stu-id="c6775-221">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="c6775-222">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="c6775-222">[C#], F#</span></span>     | <span data-ttu-id="c6775-223">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="c6775-223">Web/MVC</span></span>                               |
| <span data-ttu-id="c6775-224">ASP.NET Core webové aplikace</span><span class="sxs-lookup"><span data-stu-id="c6775-224">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="c6775-225">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6775-225">[C#]</span></span>         | <span data-ttu-id="c6775-226">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="c6775-226">Web/MVC/Razor Pages</span></span>                   |
| <span data-ttu-id="c6775-227">ASP.NET Core s úhlovým</span><span class="sxs-lookup"><span data-stu-id="c6775-227">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="c6775-228">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6775-228">[C#]</span></span>         | <span data-ttu-id="c6775-229">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="c6775-229">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="c6775-230">ASP.NET Core s reagují. js</span><span class="sxs-lookup"><span data-stu-id="c6775-230">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="c6775-231">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6775-231">[C#]</span></span>         | <span data-ttu-id="c6775-232">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="c6775-232">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="c6775-233">ASP.NET Core s využitím reagují. js a Redux</span><span class="sxs-lookup"><span data-stu-id="c6775-233">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="c6775-234">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6775-234">[C#]</span></span>         | <span data-ttu-id="c6775-235">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="c6775-235">Web/MVC/SPA</span></span>                           | 
| <span data-ttu-id="c6775-236">Knihovna tříd Razor</span><span class="sxs-lookup"><span data-stu-id="c6775-236">Razor Class Library</span></span>                          | `razorclasslib` | <span data-ttu-id="c6775-237">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6775-237">[C#]</span></span>         | <span data-ttu-id="c6775-238">Knihovna tříd web/Razor/Library/Razor</span><span class="sxs-lookup"><span data-stu-id="c6775-238">Web/Razor/Library/Razor Class Library</span></span> |
| <span data-ttu-id="c6775-239">ASP.NET Core webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="c6775-239">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="c6775-240">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="c6775-240">[C#], F#</span></span>     | <span data-ttu-id="c6775-241">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="c6775-241">Web/WebAPI</span></span>                            |
| <span data-ttu-id="c6775-242">soubor Global. JSON</span><span class="sxs-lookup"><span data-stu-id="c6775-242">global.json file</span></span>                             | `globaljson`    |              | <span data-ttu-id="c6775-243">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="c6775-243">Config</span></span>                                |
| <span data-ttu-id="c6775-244">Konfigurace NuGet</span><span class="sxs-lookup"><span data-stu-id="c6775-244">NuGet Config</span></span>                                 | `nugetconfig`   |              | <span data-ttu-id="c6775-245">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="c6775-245">Config</span></span>                                |
| <span data-ttu-id="c6775-246">Webová konfigurace</span><span class="sxs-lookup"><span data-stu-id="c6775-246">Web Config</span></span>                                   | `webconfig`     |              | <span data-ttu-id="c6775-247">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="c6775-247">Config</span></span>                                |
| <span data-ttu-id="c6775-248">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="c6775-248">Solution File</span></span>                                | `sln`           |              | <span data-ttu-id="c6775-249">Řešení</span><span class="sxs-lookup"><span data-stu-id="c6775-249">Solution</span></span>                              |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="c6775-250">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="c6775-250">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="c6775-251">Příkaz obsahuje výchozí seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="c6775-251">The command contains a default list of templates.</span></span> <span data-ttu-id="c6775-252">Seznam dostupných šablon můžete získat pomocí `dotnet new -l`.</span><span class="sxs-lookup"><span data-stu-id="c6775-252">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="c6775-253">Následující tabulka obsahuje šablony, které jsou předinstalované s .NET Core SDK 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="c6775-253">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.0.</span></span> <span data-ttu-id="c6775-254">Výchozí jazyk pro šablonu se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="c6775-254">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="c6775-255">Šablony</span><span class="sxs-lookup"><span data-stu-id="c6775-255">Templates</span></span>                                    | <span data-ttu-id="c6775-256">Krátký název</span><span class="sxs-lookup"><span data-stu-id="c6775-256">Short Name</span></span>    | <span data-ttu-id="c6775-257">Jazyk</span><span class="sxs-lookup"><span data-stu-id="c6775-257">Language</span></span>     | <span data-ttu-id="c6775-258">Značky</span><span class="sxs-lookup"><span data-stu-id="c6775-258">Tags</span></span>                |
|----------------------------------------------|---------------|--------------|---------------------|
| <span data-ttu-id="c6775-259">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="c6775-259">Console Application</span></span>                          | `console`     | <span data-ttu-id="c6775-260">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c6775-260">[C#], F#, VB</span></span> | <span data-ttu-id="c6775-261">Společná/konzola</span><span class="sxs-lookup"><span data-stu-id="c6775-261">Common/Console</span></span>      |
| <span data-ttu-id="c6775-262">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="c6775-262">Class library</span></span>                                | `classlib`    | <span data-ttu-id="c6775-263">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c6775-263">[C#], F#, VB</span></span> | <span data-ttu-id="c6775-264">Společné/knihovny</span><span class="sxs-lookup"><span data-stu-id="c6775-264">Common/Library</span></span>      |
| <span data-ttu-id="c6775-265">Projekt testu jednotek</span><span class="sxs-lookup"><span data-stu-id="c6775-265">Unit Test Project</span></span>                            | `mstest`      | <span data-ttu-id="c6775-266">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c6775-266">[C#], F#, VB</span></span> | <span data-ttu-id="c6775-267">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="c6775-267">Test/MSTest</span></span>         |
| <span data-ttu-id="c6775-268">Projekt testů xUnit</span><span class="sxs-lookup"><span data-stu-id="c6775-268">xUnit Test Project</span></span>                           | `xunit`       | <span data-ttu-id="c6775-269">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c6775-269">[C#], F#, VB</span></span> | <span data-ttu-id="c6775-270">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="c6775-270">Test/xUnit</span></span>          |
| <span data-ttu-id="c6775-271">ASP.NET Core prázdné</span><span class="sxs-lookup"><span data-stu-id="c6775-271">ASP.NET Core Empty</span></span>                           | `web`         | <span data-ttu-id="c6775-272">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="c6775-272">[C#], F#</span></span>     | <span data-ttu-id="c6775-273">Web/prázdné</span><span class="sxs-lookup"><span data-stu-id="c6775-273">Web/Empty</span></span>           |
| <span data-ttu-id="c6775-274">ASP.NET Core webová aplikace (model-zobrazení-kontroler)</span><span class="sxs-lookup"><span data-stu-id="c6775-274">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="c6775-275">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="c6775-275">[C#], F#</span></span>     | <span data-ttu-id="c6775-276">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="c6775-276">Web/MVC</span></span>             |
| <span data-ttu-id="c6775-277">ASP.NET Core webové aplikace</span><span class="sxs-lookup"><span data-stu-id="c6775-277">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="c6775-278">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6775-278">[C#]</span></span>         | <span data-ttu-id="c6775-279">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="c6775-279">Web/MVC/Razor Pages</span></span> |
| <span data-ttu-id="c6775-280">ASP.NET Core s úhlovým</span><span class="sxs-lookup"><span data-stu-id="c6775-280">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="c6775-281">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6775-281">[C#]</span></span>         | <span data-ttu-id="c6775-282">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="c6775-282">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="c6775-283">ASP.NET Core s reagují. js</span><span class="sxs-lookup"><span data-stu-id="c6775-283">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="c6775-284">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6775-284">[C#]</span></span>         | <span data-ttu-id="c6775-285">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="c6775-285">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="c6775-286">ASP.NET Core s využitím reagují. js a Redux</span><span class="sxs-lookup"><span data-stu-id="c6775-286">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="c6775-287">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6775-287">[C#]</span></span>         | <span data-ttu-id="c6775-288">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="c6775-288">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="c6775-289">ASP.NET Core webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="c6775-289">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="c6775-290">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="c6775-290">[C#], F#</span></span>     | <span data-ttu-id="c6775-291">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="c6775-291">Web/WebAPI</span></span>          |
| <span data-ttu-id="c6775-292">soubor Global. JSON</span><span class="sxs-lookup"><span data-stu-id="c6775-292">global.json file</span></span>                             | `globaljson`  |              | <span data-ttu-id="c6775-293">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="c6775-293">Config</span></span>              |
| <span data-ttu-id="c6775-294">Konfigurace NuGet</span><span class="sxs-lookup"><span data-stu-id="c6775-294">Nuget Config</span></span>                                 | `nugetconfig` |              | <span data-ttu-id="c6775-295">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="c6775-295">Config</span></span>              |
| <span data-ttu-id="c6775-296">Webová konfigurace</span><span class="sxs-lookup"><span data-stu-id="c6775-296">Web Config</span></span>                                   | `webconfig`   |              | <span data-ttu-id="c6775-297">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="c6775-297">Config</span></span>              |
| <span data-ttu-id="c6775-298">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="c6775-298">Solution File</span></span>                                | `sln`         |              | <span data-ttu-id="c6775-299">Řešení</span><span class="sxs-lookup"><span data-stu-id="c6775-299">Solution</span></span>            |
| <span data-ttu-id="c6775-300">Stránka Razor</span><span class="sxs-lookup"><span data-stu-id="c6775-300">Razor Page</span></span>                                   | `page`        |              | <span data-ttu-id="c6775-301">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="c6775-301">Web/ASP.NET</span></span>         |
| <span data-ttu-id="c6775-302">ViewImports MVC</span><span class="sxs-lookup"><span data-stu-id="c6775-302">MVC ViewImports</span></span>                              | `viewimports` |              | <span data-ttu-id="c6775-303">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="c6775-303">Web/ASP.NET</span></span>         |
| <span data-ttu-id="c6775-304">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="c6775-304">MVC ViewStart</span></span>                                | `viewstart`   |              | <span data-ttu-id="c6775-305">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="c6775-305">Web/ASP.NET</span></span>         |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c6775-306">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="c6775-306">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="c6775-307">Příkaz obsahuje výchozí seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="c6775-307">The command contains a default list of templates.</span></span> <span data-ttu-id="c6775-308">Seznam dostupných šablon můžete získat pomocí `dotnet new -all`.</span><span class="sxs-lookup"><span data-stu-id="c6775-308">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="c6775-309">Následující tabulka obsahuje šablony, které jsou předinstalované s .NET Core SDK 1.0.1.</span><span class="sxs-lookup"><span data-stu-id="c6775-309">The following table shows the templates that come pre-installed with the .NET Core SDK 1.0.1.</span></span> <span data-ttu-id="c6775-310">Výchozí jazyk pro šablonu se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="c6775-310">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="c6775-311">Šablony</span><span class="sxs-lookup"><span data-stu-id="c6775-311">Templates</span></span>            | <span data-ttu-id="c6775-312">Krátký název</span><span class="sxs-lookup"><span data-stu-id="c6775-312">Short Name</span></span>    | <span data-ttu-id="c6775-313">Jazyk</span><span class="sxs-lookup"><span data-stu-id="c6775-313">Language</span></span> | <span data-ttu-id="c6775-314">Značky</span><span class="sxs-lookup"><span data-stu-id="c6775-314">Tags</span></span>           |
|----------------------|---------------|----------|----------------|
| <span data-ttu-id="c6775-315">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="c6775-315">Console Application</span></span>  | `console`     | <span data-ttu-id="c6775-316">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="c6775-316">[C#], F#</span></span> | <span data-ttu-id="c6775-317">Společná/konzola</span><span class="sxs-lookup"><span data-stu-id="c6775-317">Common/Console</span></span> |
| <span data-ttu-id="c6775-318">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="c6775-318">Class library</span></span>        | `classlib`    | <span data-ttu-id="c6775-319">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="c6775-319">[C#], F#</span></span> | <span data-ttu-id="c6775-320">Společné/knihovny</span><span class="sxs-lookup"><span data-stu-id="c6775-320">Common/Library</span></span> |
| <span data-ttu-id="c6775-321">Projekt testu jednotek</span><span class="sxs-lookup"><span data-stu-id="c6775-321">Unit Test Project</span></span>    | `mstest`      | <span data-ttu-id="c6775-322">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="c6775-322">[C#], F#</span></span> | <span data-ttu-id="c6775-323">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="c6775-323">Test/MSTest</span></span>    |
| <span data-ttu-id="c6775-324">Projekt testů xUnit</span><span class="sxs-lookup"><span data-stu-id="c6775-324">xUnit Test Project</span></span>   | `xunit`       | <span data-ttu-id="c6775-325">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="c6775-325">[C#], F#</span></span> | <span data-ttu-id="c6775-326">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="c6775-326">Test/xUnit</span></span>     |
| <span data-ttu-id="c6775-327">ASP.NET Core prázdné</span><span class="sxs-lookup"><span data-stu-id="c6775-327">ASP.NET Core Empty</span></span>   | `web`         | <span data-ttu-id="c6775-328">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6775-328">[C#]</span></span>     | <span data-ttu-id="c6775-329">Web/prázdné</span><span class="sxs-lookup"><span data-stu-id="c6775-329">Web/Empty</span></span>      |
| <span data-ttu-id="c6775-330">ASP.NET Core webové aplikace</span><span class="sxs-lookup"><span data-stu-id="c6775-330">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="c6775-331">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="c6775-331">[C#], F#</span></span> | <span data-ttu-id="c6775-332">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="c6775-332">Web/MVC</span></span>        |
| <span data-ttu-id="c6775-333">ASP.NET Core webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="c6775-333">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="c6775-334">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6775-334">[C#]</span></span>     | <span data-ttu-id="c6775-335">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="c6775-335">Web/WebAPI</span></span>     |
| <span data-ttu-id="c6775-336">Konfigurace NuGet</span><span class="sxs-lookup"><span data-stu-id="c6775-336">Nuget Config</span></span>         | `nugetconfig` |          | <span data-ttu-id="c6775-337">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="c6775-337">Config</span></span>         |
| <span data-ttu-id="c6775-338">Webová konfigurace</span><span class="sxs-lookup"><span data-stu-id="c6775-338">Web Config</span></span>           | `webconfig`   |          | <span data-ttu-id="c6775-339">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="c6775-339">Config</span></span>         |
| <span data-ttu-id="c6775-340">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="c6775-340">Solution File</span></span>        | `sln`         |          | <span data-ttu-id="c6775-341">Řešení</span><span class="sxs-lookup"><span data-stu-id="c6775-341">Solution</span></span>       |

---

## <a name="options"></a><span data-ttu-id="c6775-342">Možnosti</span><span class="sxs-lookup"><span data-stu-id="c6775-342">Options</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="c6775-343">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="c6775-343">.NET Core 2.2</span></span>](#tab/netcore22)

`--dry-run`

<span data-ttu-id="c6775-344">Zobrazí souhrnné informace o tom, co se stane, pokud by došlo ke spuštění daného příkazu, pokud by to vedlo k vytvoření šablony.</span><span class="sxs-lookup"><span data-stu-id="c6775-344">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span>

`--force`

<span data-ttu-id="c6775-345">Vynutí vygenerování obsahu i v případě, že změní existující soubory.</span><span class="sxs-lookup"><span data-stu-id="c6775-345">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="c6775-346">To je nutné v případě, že výstupní adresář již obsahuje projekt.</span><span class="sxs-lookup"><span data-stu-id="c6775-346">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="c6775-347">Vytiskne nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="c6775-347">Prints out help for the command.</span></span> <span data-ttu-id="c6775-348">Dá se vyvolat pro samotný příkaz `dotnet new` nebo pro libovolnou šablonu, jako je například `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="c6775-348">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="c6775-349">Nainstaluje zdroj nebo balíček šablon z `PATH` nebo `NUGET_ID` poskytnutý.</span><span class="sxs-lookup"><span data-stu-id="c6775-349">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="c6775-350">Pokud chcete nainstalovat předprodejní verzi balíčku šablony, je nutné zadat verzi ve formátu `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="c6775-350">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="c6775-351">Ve výchozím nastavení `dotnet new` předá \* verze, která představuje poslední stabilní verzi balíčku.</span><span class="sxs-lookup"><span data-stu-id="c6775-351">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="c6775-352">Podívejte se na příklad v části [Příklady](#examples) .</span><span class="sxs-lookup"><span data-stu-id="c6775-352">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="c6775-353">Informace o vytváření vlastních šablon najdete v tématu [vlastní šablony pro dotnet New](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="c6775-353">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="c6775-354">Vypíše seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="c6775-354">Lists templates containing the specified name.</span></span> <span data-ttu-id="c6775-355">Pokud je vyvolána pro příkaz `dotnet new`, zobrazí seznam možných šablon dostupných pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="c6775-355">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="c6775-356">Například Pokud adresář již obsahuje projekt, nezobrazuje seznam všech šablon projektu.</span><span class="sxs-lookup"><span data-stu-id="c6775-356">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="c6775-357">Jazyk šablony, která se má vytvořit</span><span class="sxs-lookup"><span data-stu-id="c6775-357">The language of the template to create.</span></span> <span data-ttu-id="c6775-358">Přijatý jazyk se liší podle šablony (viz výchozí hodnoty v oddílu [argumenty](#arguments) ).</span><span class="sxs-lookup"><span data-stu-id="c6775-358">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="c6775-359">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="c6775-359">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="c6775-360">Některá prostředí interpretují `#` jako speciální znak.</span><span class="sxs-lookup"><span data-stu-id="c6775-360">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="c6775-361">V těchto případech je třeba uvést hodnotu parametru Language, například `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="c6775-361">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="c6775-362">Název vytvořeného výstupu.</span><span class="sxs-lookup"><span data-stu-id="c6775-362">The name for the created output.</span></span> <span data-ttu-id="c6775-363">Pokud název nezadáte, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="c6775-363">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="c6775-364">Určuje zdroj NuGet, který se použije při instalaci.</span><span class="sxs-lookup"><span data-stu-id="c6775-364">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="c6775-365">Umístění, do kterého se má vygenerovaný výstup umístit.</span><span class="sxs-lookup"><span data-stu-id="c6775-365">Location to place the generated output.</span></span> <span data-ttu-id="c6775-366">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="c6775-366">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="c6775-367">Filtruje šablony založené na dostupných typech.</span><span class="sxs-lookup"><span data-stu-id="c6775-367">Filters templates based on available types.</span></span> <span data-ttu-id="c6775-368">Předdefinované hodnoty jsou "projekt", "položka" nebo "jiné".</span><span class="sxs-lookup"><span data-stu-id="c6775-368">Predefined values are "project", "item", or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="c6775-369">Odinstaluje zdroj nebo balíček šablony na `PATH` nebo `NUGET_ID` poskytnutých.</span><span class="sxs-lookup"><span data-stu-id="c6775-369">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="c6775-370">Pokud se vyloučí hodnota `<PATH|NUGET_ID>`, zobrazí se všechny aktuálně nainstalované sady šablon a jejich přidružené šablony.</span><span class="sxs-lookup"><span data-stu-id="c6775-370">When excluding the `<PATH|NUGET_ID>` value, all currently installed template packs and their associated templates are displayed.</span></span>

> [!NOTE]
> <span data-ttu-id="c6775-371">Chcete-li odinstalovat šablonu pomocí `PATH`, je nutné cestu plně kvalifikovat.</span><span class="sxs-lookup"><span data-stu-id="c6775-371">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="c6775-372">Například *C:/uživatelé/\<USER >/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* budou fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z nadřazené složky to nebude.</span><span class="sxs-lookup"><span data-stu-id="c6775-372">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="c6775-373">Kromě toho Nezahrnovat koncové koncové lomítko adresáře na cestu k šabloně.</span><span class="sxs-lookup"><span data-stu-id="c6775-373">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="c6775-374">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="c6775-374">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="c6775-375">Vynutí vygenerování obsahu i v případě, že změní existující soubory.</span><span class="sxs-lookup"><span data-stu-id="c6775-375">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="c6775-376">To je nutné v případě, že výstupní adresář již obsahuje projekt.</span><span class="sxs-lookup"><span data-stu-id="c6775-376">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="c6775-377">Vytiskne nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="c6775-377">Prints out help for the command.</span></span> <span data-ttu-id="c6775-378">Dá se vyvolat pro samotný příkaz `dotnet new` nebo pro libovolnou šablonu, jako je například `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="c6775-378">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="c6775-379">Nainstaluje zdroj nebo balíček šablon z `PATH` nebo `NUGET_ID` poskytnutý.</span><span class="sxs-lookup"><span data-stu-id="c6775-379">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="c6775-380">Pokud chcete nainstalovat předprodejní verzi balíčku šablony, je nutné zadat verzi ve formátu `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="c6775-380">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="c6775-381">Ve výchozím nastavení `dotnet new` předá \* verze, která představuje poslední stabilní verzi balíčku.</span><span class="sxs-lookup"><span data-stu-id="c6775-381">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="c6775-382">Podívejte se na příklad v části [Příklady](#examples) .</span><span class="sxs-lookup"><span data-stu-id="c6775-382">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="c6775-383">Informace o vytváření vlastních šablon najdete v tématu [vlastní šablony pro dotnet New](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="c6775-383">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="c6775-384">Vypíše seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="c6775-384">Lists templates containing the specified name.</span></span> <span data-ttu-id="c6775-385">Pokud je vyvolána pro příkaz `dotnet new`, zobrazí seznam možných šablon dostupných pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="c6775-385">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="c6775-386">Například Pokud adresář již obsahuje projekt, nezobrazuje seznam všech šablon projektu.</span><span class="sxs-lookup"><span data-stu-id="c6775-386">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="c6775-387">Jazyk šablony, která se má vytvořit</span><span class="sxs-lookup"><span data-stu-id="c6775-387">The language of the template to create.</span></span> <span data-ttu-id="c6775-388">Přijatý jazyk se liší podle šablony (viz výchozí hodnoty v oddílu [argumenty](#arguments) ).</span><span class="sxs-lookup"><span data-stu-id="c6775-388">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="c6775-389">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="c6775-389">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="c6775-390">Některá prostředí interpretují `#` jako speciální znak.</span><span class="sxs-lookup"><span data-stu-id="c6775-390">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="c6775-391">V těchto případech je třeba uvést hodnotu parametru Language, například `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="c6775-391">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="c6775-392">Název vytvořeného výstupu.</span><span class="sxs-lookup"><span data-stu-id="c6775-392">The name for the created output.</span></span> <span data-ttu-id="c6775-393">Pokud název nezadáte, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="c6775-393">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="c6775-394">Určuje zdroj NuGet, který se použije při instalaci.</span><span class="sxs-lookup"><span data-stu-id="c6775-394">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="c6775-395">Umístění, do kterého se má vygenerovaný výstup umístit.</span><span class="sxs-lookup"><span data-stu-id="c6775-395">Location to place the generated output.</span></span> <span data-ttu-id="c6775-396">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="c6775-396">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="c6775-397">Filtruje šablony založené na dostupných typech.</span><span class="sxs-lookup"><span data-stu-id="c6775-397">Filters templates based on available types.</span></span> <span data-ttu-id="c6775-398">Předdefinované hodnoty jsou "projekt", "položka" nebo "jiné".</span><span class="sxs-lookup"><span data-stu-id="c6775-398">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="c6775-399">Odinstaluje zdroj nebo balíček šablony na `PATH` nebo `NUGET_ID` poskytnutých.</span><span class="sxs-lookup"><span data-stu-id="c6775-399">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="c6775-400">Chcete-li odinstalovat šablonu pomocí `PATH`, je nutné cestu plně kvalifikovat.</span><span class="sxs-lookup"><span data-stu-id="c6775-400">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="c6775-401">Například *C:/uživatelé/\<USER >/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* budou fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z nadřazené složky to nebude.</span><span class="sxs-lookup"><span data-stu-id="c6775-401">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="c6775-402">Kromě toho Nezahrnovat koncové koncové lomítko adresáře na cestu k šabloně.</span><span class="sxs-lookup"><span data-stu-id="c6775-402">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="c6775-403">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="c6775-403">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="c6775-404">Vynutí vygenerování obsahu i v případě, že změní existující soubory.</span><span class="sxs-lookup"><span data-stu-id="c6775-404">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="c6775-405">To je nutné v případě, že výstupní adresář již obsahuje projekt.</span><span class="sxs-lookup"><span data-stu-id="c6775-405">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="c6775-406">Vytiskne nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="c6775-406">Prints out help for the command.</span></span> <span data-ttu-id="c6775-407">Dá se vyvolat pro samotný příkaz `dotnet new` nebo pro libovolnou šablonu, jako je například `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="c6775-407">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="c6775-408">Nainstaluje zdroj nebo balíček šablon z `PATH` nebo `NUGET_ID` poskytnutý.</span><span class="sxs-lookup"><span data-stu-id="c6775-408">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="c6775-409">Pokud chcete nainstalovat předprodejní verzi balíčku šablony, je nutné zadat verzi ve formátu `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="c6775-409">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="c6775-410">Ve výchozím nastavení `dotnet new` předá \* verze, která představuje poslední stabilní verzi balíčku.</span><span class="sxs-lookup"><span data-stu-id="c6775-410">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="c6775-411">Podívejte se na příklad v části [Příklady](#examples) .</span><span class="sxs-lookup"><span data-stu-id="c6775-411">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="c6775-412">Informace o vytváření vlastních šablon najdete v tématu [vlastní šablony pro dotnet New](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="c6775-412">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="c6775-413">Vypíše seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="c6775-413">Lists templates containing the specified name.</span></span> <span data-ttu-id="c6775-414">Pokud je vyvolána pro příkaz `dotnet new`, zobrazí seznam možných šablon dostupných pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="c6775-414">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="c6775-415">Například Pokud adresář již obsahuje projekt, nezobrazuje seznam všech šablon projektu.</span><span class="sxs-lookup"><span data-stu-id="c6775-415">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="c6775-416">Jazyk šablony, která se má vytvořit</span><span class="sxs-lookup"><span data-stu-id="c6775-416">The language of the template to create.</span></span> <span data-ttu-id="c6775-417">Přijatý jazyk se liší podle šablony (viz výchozí hodnoty v oddílu [argumenty](#arguments) ).</span><span class="sxs-lookup"><span data-stu-id="c6775-417">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="c6775-418">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="c6775-418">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="c6775-419">Některá prostředí interpretují `#` jako speciální znak.</span><span class="sxs-lookup"><span data-stu-id="c6775-419">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="c6775-420">V těchto případech je třeba uvést hodnotu parametru Language, například `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="c6775-420">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="c6775-421">Název vytvořeného výstupu.</span><span class="sxs-lookup"><span data-stu-id="c6775-421">The name for the created output.</span></span> <span data-ttu-id="c6775-422">Pokud název nezadáte, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="c6775-422">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="c6775-423">Umístění, do kterého se má vygenerovaný výstup umístit.</span><span class="sxs-lookup"><span data-stu-id="c6775-423">Location to place the generated output.</span></span> <span data-ttu-id="c6775-424">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="c6775-424">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="c6775-425">Filtruje šablony založené na dostupných typech.</span><span class="sxs-lookup"><span data-stu-id="c6775-425">Filters templates based on available types.</span></span> <span data-ttu-id="c6775-426">Předdefinované hodnoty jsou "projekt", "položka" nebo "jiné".</span><span class="sxs-lookup"><span data-stu-id="c6775-426">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="c6775-427">Odinstaluje zdroj nebo balíček šablony na `PATH` nebo `NUGET_ID` poskytnutých.</span><span class="sxs-lookup"><span data-stu-id="c6775-427">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="c6775-428">Chcete-li odinstalovat šablonu pomocí zdrojové `PATH`, je nutné cestu plně kvalifikovat.</span><span class="sxs-lookup"><span data-stu-id="c6775-428">To uninstall a template using a source `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="c6775-429">Například *C:/uživatelé/\<USER >/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* budou fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z nadřazené složky to nebude.</span><span class="sxs-lookup"><span data-stu-id="c6775-429">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span> <span data-ttu-id="c6775-430">Kromě toho Nezahrnovat koncové koncové lomítko adresáře na cestu k šabloně.</span><span class="sxs-lookup"><span data-stu-id="c6775-430">Additionally, do not include a final terminating directory slash on your template path.</span></span>
> 
> <span data-ttu-id="c6775-431">Pokud nemůžete určit `PATH` nebo `NUGET_ID` argument potřebný k odinstalaci šablony, spuštěním `dotnet new --uninstall` bez argumentu se zobrazí seznam všech nainstalovaných šablon a argument potřebný k jejich odinstalování.</span><span class="sxs-lookup"><span data-stu-id="c6775-431">If you are unable to determine the `PATH` or `NUGET_ID` argument needed to uninstall a template, running `dotnet new --uninstall` without an argument will list all installed templates and the argument required to uninstall them.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c6775-432">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="c6775-432">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="c6775-433">Zobrazí všechny šablony pro konkrétní typ projektu při spuštění v kontextu samostatného příkazu `dotnet new`.</span><span class="sxs-lookup"><span data-stu-id="c6775-433">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="c6775-434">Při spuštění v souvislosti se specifickou šablonou, jako je například `dotnet new web -all`, `-all` je interpretován jako příznak vytvoření síly.</span><span class="sxs-lookup"><span data-stu-id="c6775-434">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="c6775-435">To je nutné v případě, že výstupní adresář již obsahuje projekt.</span><span class="sxs-lookup"><span data-stu-id="c6775-435">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="c6775-436">Vytiskne nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="c6775-436">Prints out help for the command.</span></span> <span data-ttu-id="c6775-437">Dá se vyvolat pro samotný příkaz `dotnet new` nebo pro libovolnou šablonu, jako je například `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="c6775-437">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="c6775-438">Vypíše seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="c6775-438">Lists templates containing the specified name.</span></span> <span data-ttu-id="c6775-439">Pokud je vyvolána pro příkaz `dotnet new`, zobrazí seznam možných šablon dostupných pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="c6775-439">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="c6775-440">Například Pokud adresář již obsahuje projekt, nezobrazuje seznam všech šablon projektu.</span><span class="sxs-lookup"><span data-stu-id="c6775-440">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="c6775-441">Jazyk šablony, která se má vytvořit</span><span class="sxs-lookup"><span data-stu-id="c6775-441">The language of the template to create.</span></span> <span data-ttu-id="c6775-442">Přijatý jazyk se liší podle šablony (viz výchozí hodnoty v oddílu [argumenty](#arguments) ).</span><span class="sxs-lookup"><span data-stu-id="c6775-442">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="c6775-443">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="c6775-443">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="c6775-444">Některá prostředí interpretují `#` jako speciální znak.</span><span class="sxs-lookup"><span data-stu-id="c6775-444">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="c6775-445">V těchto případech je třeba uvést hodnotu parametru Language, například `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="c6775-445">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="c6775-446">Název vytvořeného výstupu.</span><span class="sxs-lookup"><span data-stu-id="c6775-446">The name for the created output.</span></span> <span data-ttu-id="c6775-447">Pokud název nezadáte, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="c6775-447">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="c6775-448">Umístění, do kterého se má vygenerovaný výstup umístit.</span><span class="sxs-lookup"><span data-stu-id="c6775-448">Location to place the generated output.</span></span> <span data-ttu-id="c6775-449">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="c6775-449">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="c6775-450">Možnosti šablony</span><span class="sxs-lookup"><span data-stu-id="c6775-450">Template options</span></span>

<span data-ttu-id="c6775-451">Každá šablona projektu může mít k dispozici další možnosti.</span><span class="sxs-lookup"><span data-stu-id="c6775-451">Each project template may have additional options available.</span></span> <span data-ttu-id="c6775-452">Základní šablony mají následující další možnosti:</span><span class="sxs-lookup"><span data-stu-id="c6775-452">The core templates have the following additional options:</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="c6775-453">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="c6775-453">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="c6775-454">**stromu**</span><span class="sxs-lookup"><span data-stu-id="c6775-454">**console**</span></span>

<span data-ttu-id="c6775-455">`--langVersion <VERSION_NUMBER>` – nastaví vlastnost `LangVersion` v souboru vytvořeného projektu.</span><span class="sxs-lookup"><span data-stu-id="c6775-455">`--langVersion <VERSION_NUMBER>` - Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="c6775-456">Například použijte `--langVersion 7.3` k použití C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="c6775-456">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="c6775-457">Nepodporuje se pro F#.</span><span class="sxs-lookup"><span data-stu-id="c6775-457">Not supported for F#.</span></span>

<span data-ttu-id="c6775-458">`--no-restore` – při vytváření projektu nespustí implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="c6775-458">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c6775-459">**Úhlová, reakce, reactredux**</span><span class="sxs-lookup"><span data-stu-id="c6775-459">**angular, react, reactredux**</span></span>

<span data-ttu-id="c6775-460">`--exclude-launch-settings` – vylučte z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="c6775-460">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="c6775-461">`--no-restore` – při vytváření projektu nespustí implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="c6775-461">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c6775-462">`--no-https` – projekt nevyžaduje protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c6775-462">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="c6775-463">Tato možnost se vztahuje jenom v případě, že se nepoužívají `IndividualAuth` nebo `OrganizationalAuth`.</span><span class="sxs-lookup"><span data-stu-id="c6775-463">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="c6775-464">**razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="c6775-464">**razorclasslib**</span></span>

<span data-ttu-id="c6775-465">`--no-restore` – při vytváření projektu nespustí implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="c6775-465">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c6775-466">**že knihovna tříd**</span><span class="sxs-lookup"><span data-stu-id="c6775-466">**classlib**</span></span>

<span data-ttu-id="c6775-467">`-f|--framework <FRAMEWORK>` – Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="c6775-467">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c6775-468">Hodnoty: `netcoreapp2.2` pro vytvoření knihovny tříd .NET Core nebo `netstandard2.0` k vytvoření knihovny tříd .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="c6775-468">Values: `netcoreapp2.2` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="c6775-469">Výchozí hodnota je `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="c6775-469">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="c6775-470">`--langVersion <VERSION_NUMBER>` – nastaví vlastnost `LangVersion` v souboru vytvořeného projektu.</span><span class="sxs-lookup"><span data-stu-id="c6775-470">`--langVersion <VERSION_NUMBER>` - Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="c6775-471">Například použijte `--langVersion 7.3` k použití C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="c6775-471">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="c6775-472">Nepodporuje se pro F#.</span><span class="sxs-lookup"><span data-stu-id="c6775-472">Not supported for F#.</span></span>

<span data-ttu-id="c6775-473">`--no-restore` – při vytváření projektu nespustí implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="c6775-473">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c6775-474">**MSTest, xUnit**</span><span class="sxs-lookup"><span data-stu-id="c6775-474">**mstest, xunit**</span></span>

<span data-ttu-id="c6775-475">`-p|--enable-pack` – povolí balení pro projekt pomocí [sady dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="c6775-475">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="c6775-476">`--no-restore` – při vytváření projektu nespustí implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="c6775-476">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c6775-477">**nunit**</span><span class="sxs-lookup"><span data-stu-id="c6775-477">**nunit**</span></span>

<span data-ttu-id="c6775-478">`-f|--framework <FRAMEWORK>` – Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="c6775-478">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c6775-479">Výchozí hodnota je `netcoreapp2.1`.</span><span class="sxs-lookup"><span data-stu-id="c6775-479">The default value is `netcoreapp2.1`.</span></span>

<span data-ttu-id="c6775-480">`-p|--enable-pack` – povolí balení pro projekt pomocí [sady dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="c6775-480">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="c6775-481">`--no-restore` – při vytváření projektu nespustí implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="c6775-481">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c6775-482">**Page**</span><span class="sxs-lookup"><span data-stu-id="c6775-482">**page**</span></span>

<span data-ttu-id="c6775-483">`-na|--namespace <NAMESPACE_NAME>` – obor názvů pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="c6775-483">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="c6775-484">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="c6775-484">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="c6775-485">`-np|--no-pagemodel` – vytvoří stránku bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="c6775-485">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="c6775-486">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="c6775-486">**viewimports**</span></span>

<span data-ttu-id="c6775-487">`-na|--namespace <NAMESPACE_NAME>` – obor názvů pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="c6775-487">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="c6775-488">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="c6775-488">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="c6775-489">**webovém**</span><span class="sxs-lookup"><span data-stu-id="c6775-489">**web**</span></span>

<span data-ttu-id="c6775-490">`--exclude-launch-settings` – vylučte z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="c6775-490">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="c6775-491">`--no-restore` – při vytváření projektu nespustí implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="c6775-491">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c6775-492">`--no-https` – projekt nevyžaduje protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c6775-492">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="c6775-493">Tato možnost se vztahuje jenom v případě, že se nepoužívají `IndividualAuth` nebo `OrganizationalAuth`.</span><span class="sxs-lookup"><span data-stu-id="c6775-493">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="c6775-494">**MVC, WebApp**</span><span class="sxs-lookup"><span data-stu-id="c6775-494">**mvc, webapp**</span></span>

<span data-ttu-id="c6775-495">`-au|--auth <AUTHENTICATION_TYPE>` – typ ověřování, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="c6775-495">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="c6775-496">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="c6775-496">The possible values are:</span></span>

- <span data-ttu-id="c6775-497">`None` – bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="c6775-497">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="c6775-498">`Individual` – individuální ověřování.</span><span class="sxs-lookup"><span data-stu-id="c6775-498">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="c6775-499">`IndividualB2C` – individuální ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="c6775-499">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="c6775-500">`SingleOrg` – ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="c6775-500">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="c6775-501">`MultiOrg` – ověřování organizace pro více tenantů.</span><span class="sxs-lookup"><span data-stu-id="c6775-501">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="c6775-502">`Windows` – ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="c6775-502">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="c6775-503">`--aad-b2c-instance <INSTANCE>` – instance Azure Active Directory B2C, ke které se chcete připojit</span><span class="sxs-lookup"><span data-stu-id="c6775-503">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="c6775-504">Použijte s ověřováním `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6775-504">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="c6775-505">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="c6775-505">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="c6775-506">`-ssp|--susi-policy-id <ID>` – ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="c6775-506">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="c6775-507">Použijte s ověřováním `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6775-507">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c6775-508">`-rp|--reset-password-policy-id <ID>` – ID zásad pro resetování hesla pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="c6775-508">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="c6775-509">Použijte s ověřováním `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6775-509">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c6775-510">`-ep|--edit-profile-policy-id <ID>` – ID zásad úprav profilu pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="c6775-510">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="c6775-511">Použijte s ověřováním `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6775-511">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c6775-512">`--aad-instance <INSTANCE>` – instance Azure Active Directory, ke které se chcete připojit</span><span class="sxs-lookup"><span data-stu-id="c6775-512">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="c6775-513">Použijte s ověřováním `SingleOrg` nebo `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6775-513">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="c6775-514">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="c6775-514">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="c6775-515">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="c6775-515">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="c6775-516">Použijte s ověřováním `IndividualB2C`, `SingleOrg`nebo `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6775-516">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="c6775-517">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="c6775-517">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="c6775-518">`--domain <DOMAIN>` – doména pro tenanta adresáře.</span><span class="sxs-lookup"><span data-stu-id="c6775-518">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="c6775-519">Použijte s ověřováním `SingleOrg` nebo `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6775-519">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c6775-520">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="c6775-520">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="c6775-521">`--tenant-id <ID>` – ID TenantId adresáře, ke kterému se má připojit.</span><span class="sxs-lookup"><span data-stu-id="c6775-521">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="c6775-522">Použijte s ověřováním `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6775-522">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c6775-523">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="c6775-523">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="c6775-524">`--callback-path <PATH>` – cesta požadavku v základní cestě identifikátoru URI pro přesměrování.</span><span class="sxs-lookup"><span data-stu-id="c6775-524">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="c6775-525">Použijte s ověřováním `SingleOrg` nebo `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6775-525">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c6775-526">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="c6775-526">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="c6775-527">`-r|--org-read-access` – povolí této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="c6775-527">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="c6775-528">Platí jenom pro ověřování `SingleOrg` nebo `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6775-528">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="c6775-529">`--exclude-launch-settings` – vylučte z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="c6775-529">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="c6775-530">`--no-https` – projekt nevyžaduje protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c6775-530">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="c6775-531">`app.UseHsts` a `app.UseHttpsRedirection` nejsou přidány do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="c6775-531">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="c6775-532">Tato možnost se vztahuje jenom v případě, že se nepoužívají `Individual`, `IndividualB2C`, `SingleOrg`nebo `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6775-532">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="c6775-533">`-uld|--use-local-db` – určuje, že se má místo SQLite použít LocalDB.</span><span class="sxs-lookup"><span data-stu-id="c6775-533">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c6775-534">Platí jenom pro ověřování `Individual` nebo `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6775-534">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c6775-535">`--no-restore` – při vytváření projektu nespustí implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="c6775-535">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c6775-536">**WebApi**</span><span class="sxs-lookup"><span data-stu-id="c6775-536">**webapi**</span></span>

<span data-ttu-id="c6775-537">`-au|--auth <AUTHENTICATION_TYPE>` – typ ověřování, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="c6775-537">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="c6775-538">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="c6775-538">The possible values are:</span></span>

- <span data-ttu-id="c6775-539">`None` – bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="c6775-539">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="c6775-540">`IndividualB2C` – individuální ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="c6775-540">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="c6775-541">`SingleOrg` – ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="c6775-541">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="c6775-542">`Windows` – ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="c6775-542">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="c6775-543">`--aad-b2c-instance <INSTANCE>` – instance Azure Active Directory B2C, ke které se chcete připojit</span><span class="sxs-lookup"><span data-stu-id="c6775-543">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="c6775-544">Použijte s ověřováním `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6775-544">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="c6775-545">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="c6775-545">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="c6775-546">`-ssp|--susi-policy-id <ID>` – ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="c6775-546">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="c6775-547">Použijte s ověřováním `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6775-547">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c6775-548">`--aad-instance <INSTANCE>` – instance Azure Active Directory, ke které se chcete připojit</span><span class="sxs-lookup"><span data-stu-id="c6775-548">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="c6775-549">Použijte s ověřováním `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6775-549">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c6775-550">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="c6775-550">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="c6775-551">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="c6775-551">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="c6775-552">Použijte s ověřováním `IndividualB2C` nebo `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6775-552">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="c6775-553">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="c6775-553">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="c6775-554">`--domain <DOMAIN>` – doména pro tenanta adresáře.</span><span class="sxs-lookup"><span data-stu-id="c6775-554">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="c6775-555">Použijte s ověřováním `SingleOrg` nebo `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6775-555">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c6775-556">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="c6775-556">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="c6775-557">`--tenant-id <ID>` – ID TenantId adresáře, ke kterému se má připojit.</span><span class="sxs-lookup"><span data-stu-id="c6775-557">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="c6775-558">Použijte s ověřováním `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6775-558">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c6775-559">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="c6775-559">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="c6775-560">`-r|--org-read-access` – povolí této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="c6775-560">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="c6775-561">Platí jenom pro ověřování `SingleOrg` nebo `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6775-561">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="c6775-562">`--exclude-launch-settings` – vylučte z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="c6775-562">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="c6775-563">`--no-https` – projekt nevyžaduje protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c6775-563">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="c6775-564">`app.UseHsts` a `app.UseHttpsRedirection` nejsou přidány do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="c6775-564">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="c6775-565">Tato možnost se vztahuje jenom v případě, že se nepoužívají `Individual`, `IndividualB2C`, `SingleOrg`nebo `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6775-565">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="c6775-566">`-uld|--use-local-db` – určuje, že se má místo SQLite použít LocalDB.</span><span class="sxs-lookup"><span data-stu-id="c6775-566">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c6775-567">Platí jenom pro ověřování `Individual` nebo `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6775-567">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c6775-568">`--no-restore` – při vytváření projektu nespustí implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="c6775-568">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c6775-569">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="c6775-569">**globaljson**</span></span>

<span data-ttu-id="c6775-570">`--sdk-version <VERSION_NUMBER>` – určuje verzi .NET Core SDK, která se má použít v souboru *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="c6775-570">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="c6775-571">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="c6775-571">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="c6775-572">**Konzola, úhlová, reakce, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="c6775-572">**console, angular, react, reactredux, razorclasslib**</span></span>

<span data-ttu-id="c6775-573">`--no-restore` – při vytváření projektu nespustí implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="c6775-573">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c6775-574">**že knihovna tříd**</span><span class="sxs-lookup"><span data-stu-id="c6775-574">**classlib**</span></span>

<span data-ttu-id="c6775-575">`-f|--framework <FRAMEWORK>` – Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="c6775-575">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c6775-576">Hodnoty: `netcoreapp2.1` pro vytvoření knihovny tříd .NET Core nebo `netstandard2.0` k vytvoření knihovny tříd .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="c6775-576">Values: `netcoreapp2.1` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="c6775-577">Výchozí hodnota je `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="c6775-577">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="c6775-578">`--no-restore` – při vytváření projektu nespustí implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="c6775-578">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c6775-579">**MSTest, xUnit**</span><span class="sxs-lookup"><span data-stu-id="c6775-579">**mstest, xunit**</span></span>

<span data-ttu-id="c6775-580">`-p|--enable-pack` – povolí balení pro projekt pomocí [sady dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="c6775-580">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="c6775-581">`--no-restore` – při vytváření projektu nespustí implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="c6775-581">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c6775-582">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="c6775-582">**globaljson**</span></span>

<span data-ttu-id="c6775-583">`--sdk-version <VERSION_NUMBER>` – určuje verzi .NET Core SDK, která se má použít v souboru *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="c6775-583">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="c6775-584">**webovém**</span><span class="sxs-lookup"><span data-stu-id="c6775-584">**web**</span></span>

<span data-ttu-id="c6775-585">`--exclude-launch-settings` – vylučte z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="c6775-585">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="c6775-586">`--no-restore` – při vytváření projektu nespustí implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="c6775-586">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c6775-587">`--no-https` – projekt nevyžaduje protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c6775-587">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="c6775-588">Tato možnost se vztahuje jenom v případě, že se nepoužívají `IndividualAuth` nebo `OrganizationalAuth`.</span><span class="sxs-lookup"><span data-stu-id="c6775-588">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="c6775-589">**WebApi**</span><span class="sxs-lookup"><span data-stu-id="c6775-589">**webapi**</span></span>

<span data-ttu-id="c6775-590">`-au|--auth <AUTHENTICATION_TYPE>` – typ ověřování, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="c6775-590">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="c6775-591">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="c6775-591">The possible values are:</span></span>

- <span data-ttu-id="c6775-592">`None` – bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="c6775-592">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="c6775-593">`IndividualB2C` – individuální ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="c6775-593">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="c6775-594">`SingleOrg` – ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="c6775-594">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="c6775-595">`Windows` – ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="c6775-595">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="c6775-596">`--aad-b2c-instance <INSTANCE>` – instance Azure Active Directory B2C, ke které se chcete připojit</span><span class="sxs-lookup"><span data-stu-id="c6775-596">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="c6775-597">Použijte s ověřováním `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6775-597">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="c6775-598">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="c6775-598">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="c6775-599">`-ssp|--susi-policy-id <ID>` – ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="c6775-599">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="c6775-600">Použijte s ověřováním `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6775-600">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c6775-601">`--aad-instance <INSTANCE>` – instance Azure Active Directory, ke které se chcete připojit</span><span class="sxs-lookup"><span data-stu-id="c6775-601">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="c6775-602">Použijte s ověřováním `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6775-602">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c6775-603">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="c6775-603">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="c6775-604">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="c6775-604">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="c6775-605">Použijte s ověřováním `IndividualB2C` nebo `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6775-605">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="c6775-606">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="c6775-606">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="c6775-607">`--domain <DOMAIN>` – doména pro tenanta adresáře.</span><span class="sxs-lookup"><span data-stu-id="c6775-607">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="c6775-608">Použijte s ověřováním `SingleOrg` nebo `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6775-608">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c6775-609">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="c6775-609">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="c6775-610">`--tenant-id <ID>` – ID TenantId adresáře, ke kterému se má připojit.</span><span class="sxs-lookup"><span data-stu-id="c6775-610">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="c6775-611">Použijte s ověřováním `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6775-611">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c6775-612">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="c6775-612">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="c6775-613">`-r|--org-read-access` – povolí této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="c6775-613">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="c6775-614">Platí jenom pro ověřování `SingleOrg` nebo `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6775-614">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="c6775-615">`--exclude-launch-settings` – vylučte z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="c6775-615">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="c6775-616">`-uld|--use-local-db` – určuje, že se má místo SQLite použít LocalDB.</span><span class="sxs-lookup"><span data-stu-id="c6775-616">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c6775-617">Platí jenom pro ověřování `Individual` nebo `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6775-617">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c6775-618">`--no-restore` – při vytváření projektu nespustí implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="c6775-618">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c6775-619">`--no-https` – projekt nevyžaduje protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c6775-619">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="c6775-620">`app.UseHsts` a `app.UseHttpsRedirection` nejsou přidány do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="c6775-620">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="c6775-621">Tato možnost se vztahuje jenom v případě, že se nepoužívají `Individual`, `IndividualB2C`, `SingleOrg`nebo `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6775-621">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="c6775-622">**MVC, Razor**</span><span class="sxs-lookup"><span data-stu-id="c6775-622">**mvc, razor**</span></span>

<span data-ttu-id="c6775-623">`-au|--auth <AUTHENTICATION_TYPE>` – typ ověřování, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="c6775-623">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="c6775-624">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="c6775-624">The possible values are:</span></span>

- <span data-ttu-id="c6775-625">`None` – bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="c6775-625">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="c6775-626">`Individual` – individuální ověřování.</span><span class="sxs-lookup"><span data-stu-id="c6775-626">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="c6775-627">`IndividualB2C` – individuální ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="c6775-627">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="c6775-628">`SingleOrg` – ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="c6775-628">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="c6775-629">`MultiOrg` – ověřování organizace pro více tenantů.</span><span class="sxs-lookup"><span data-stu-id="c6775-629">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="c6775-630">`Windows` – ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="c6775-630">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="c6775-631">`--aad-b2c-instance <INSTANCE>` – instance Azure Active Directory B2C, ke které se chcete připojit</span><span class="sxs-lookup"><span data-stu-id="c6775-631">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="c6775-632">Použijte s ověřováním `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6775-632">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="c6775-633">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="c6775-633">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="c6775-634">`-ssp|--susi-policy-id <ID>` – ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="c6775-634">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="c6775-635">Použijte s ověřováním `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6775-635">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c6775-636">`-rp|--reset-password-policy-id <ID>` – ID zásad pro resetování hesla pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="c6775-636">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="c6775-637">Použijte s ověřováním `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6775-637">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c6775-638">`-ep|--edit-profile-policy-id <ID>` – ID zásad úprav profilu pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="c6775-638">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="c6775-639">Použijte s ověřováním `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6775-639">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c6775-640">`--aad-instance <INSTANCE>` – instance Azure Active Directory, ke které se chcete připojit</span><span class="sxs-lookup"><span data-stu-id="c6775-640">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="c6775-641">Použijte s ověřováním `SingleOrg` nebo `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6775-641">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="c6775-642">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="c6775-642">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="c6775-643">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="c6775-643">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="c6775-644">Použijte s ověřováním `IndividualB2C`, `SingleOrg`nebo `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6775-644">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="c6775-645">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="c6775-645">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="c6775-646">`--domain <DOMAIN>` – doména pro tenanta adresáře.</span><span class="sxs-lookup"><span data-stu-id="c6775-646">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="c6775-647">Použijte s ověřováním `SingleOrg` nebo `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6775-647">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c6775-648">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="c6775-648">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="c6775-649">`--tenant-id <ID>` – ID TenantId adresáře, ke kterému se má připojit.</span><span class="sxs-lookup"><span data-stu-id="c6775-649">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="c6775-650">Použijte s ověřováním `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6775-650">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c6775-651">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="c6775-651">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="c6775-652">`--callback-path <PATH>` – cesta požadavku v základní cestě identifikátoru URI pro přesměrování.</span><span class="sxs-lookup"><span data-stu-id="c6775-652">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="c6775-653">Použijte s ověřováním `SingleOrg` nebo `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6775-653">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c6775-654">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="c6775-654">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="c6775-655">`-r|--org-read-access` – povolí této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="c6775-655">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="c6775-656">Platí jenom pro ověřování `SingleOrg` nebo `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6775-656">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="c6775-657">`--exclude-launch-settings` – vylučte z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="c6775-657">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="c6775-658">`--use-browserlink` – zahrnuje BrowserLink do projektu.</span><span class="sxs-lookup"><span data-stu-id="c6775-658">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="c6775-659">`-uld|--use-local-db` – určuje, že se má místo SQLite použít LocalDB.</span><span class="sxs-lookup"><span data-stu-id="c6775-659">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c6775-660">Platí jenom pro ověřování `Individual` nebo `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6775-660">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c6775-661">`--no-restore` – při vytváření projektu nespustí implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="c6775-661">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c6775-662">`--no-https` – projekt nevyžaduje protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c6775-662">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="c6775-663">`app.UseHsts` a `app.UseHttpsRedirection` nejsou přidány do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="c6775-663">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="c6775-664">Tato možnost se vztahuje jenom v případě, že se nepoužívají `Individual`, `IndividualB2C`, `SingleOrg`nebo `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6775-664">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="c6775-665">**Page**</span><span class="sxs-lookup"><span data-stu-id="c6775-665">**page**</span></span>

<span data-ttu-id="c6775-666">`-na|--namespace <NAMESPACE_NAME>` – obor názvů pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="c6775-666">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="c6775-667">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="c6775-667">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="c6775-668">`-np|--no-pagemodel` – vytvoří stránku bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="c6775-668">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="c6775-669">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="c6775-669">**viewimports**</span></span>

<span data-ttu-id="c6775-670">`-na|--namespace <NAMESPACE_NAME>` – obor názvů pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="c6775-670">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="c6775-671">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="c6775-671">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="c6775-672">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="c6775-672">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="c6775-673">**Konzola, úhlová, reakce, reactredux**</span><span class="sxs-lookup"><span data-stu-id="c6775-673">**console, angular, react, reactredux**</span></span>

<span data-ttu-id="c6775-674">`--no-restore` – při vytváření projektu nespustí implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="c6775-674">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c6775-675">**že knihovna tříd**</span><span class="sxs-lookup"><span data-stu-id="c6775-675">**classlib**</span></span>

<span data-ttu-id="c6775-676">`-f|--framework <FRAMEWORK>` – Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="c6775-676">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c6775-677">Hodnoty: `netcoreapp2.0` pro vytvoření knihovny tříd .NET Core nebo `netstandard2.0` k vytvoření knihovny tříd .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="c6775-677">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="c6775-678">Výchozí hodnota je `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="c6775-678">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="c6775-679">`--no-restore` – při vytváření projektu nespustí implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="c6775-679">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c6775-680">**MSTest, xUnit**</span><span class="sxs-lookup"><span data-stu-id="c6775-680">**mstest, xunit**</span></span>

<span data-ttu-id="c6775-681">`-p|--enable-pack` – povolí balení pro projekt pomocí [sady dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="c6775-681">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="c6775-682">`--no-restore` – při vytváření projektu nespustí implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="c6775-682">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c6775-683">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="c6775-683">**globaljson**</span></span>

<span data-ttu-id="c6775-684">`--sdk-version <VERSION_NUMBER>` – určuje verzi .NET Core SDK, která se má použít v souboru *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="c6775-684">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="c6775-685">**webovém**</span><span class="sxs-lookup"><span data-stu-id="c6775-685">**web**</span></span>

<span data-ttu-id="c6775-686">`--use-launch-settings` – obsahuje ve výstupu vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="c6775-686">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="c6775-687">`--no-restore` – při vytváření projektu nespustí implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="c6775-687">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c6775-688">**WebApi**</span><span class="sxs-lookup"><span data-stu-id="c6775-688">**webapi**</span></span>

<span data-ttu-id="c6775-689">`-au|--auth <AUTHENTICATION_TYPE>` – typ ověřování, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="c6775-689">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="c6775-690">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="c6775-690">The possible values are:</span></span>

- <span data-ttu-id="c6775-691">`None` – bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="c6775-691">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="c6775-692">`IndividualB2C` – individuální ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="c6775-692">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="c6775-693">`SingleOrg` – ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="c6775-693">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="c6775-694">`Windows` – ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="c6775-694">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="c6775-695">`--aad-b2c-instance <INSTANCE>` – instance Azure Active Directory B2C, ke které se chcete připojit</span><span class="sxs-lookup"><span data-stu-id="c6775-695">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="c6775-696">Použijte s ověřováním `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6775-696">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="c6775-697">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="c6775-697">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="c6775-698">`-ssp|--susi-policy-id <ID>` – ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="c6775-698">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="c6775-699">Použijte s ověřováním `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6775-699">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c6775-700">`--aad-instance <INSTANCE>` – instance Azure Active Directory, ke které se chcete připojit</span><span class="sxs-lookup"><span data-stu-id="c6775-700">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="c6775-701">Použijte s ověřováním `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6775-701">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c6775-702">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="c6775-702">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="c6775-703">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="c6775-703">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="c6775-704">Použijte s ověřováním `IndividualB2C` nebo `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6775-704">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="c6775-705">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="c6775-705">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="c6775-706">`--domain <DOMAIN>` – doména pro tenanta adresáře.</span><span class="sxs-lookup"><span data-stu-id="c6775-706">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="c6775-707">Použijte s ověřováním `SingleOrg` nebo `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6775-707">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c6775-708">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="c6775-708">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="c6775-709">`--tenant-id <ID>` – ID TenantId adresáře, ke kterému se má připojit.</span><span class="sxs-lookup"><span data-stu-id="c6775-709">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="c6775-710">Použijte s ověřováním `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6775-710">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c6775-711">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="c6775-711">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="c6775-712">`-r|--org-read-access` – povolí této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="c6775-712">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="c6775-713">Platí jenom pro ověřování `SingleOrg` nebo `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6775-713">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="c6775-714">`--use-launch-settings` – obsahuje ve výstupu vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="c6775-714">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="c6775-715">`-uld|--use-local-db` – určuje, že se má místo SQLite použít LocalDB.</span><span class="sxs-lookup"><span data-stu-id="c6775-715">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c6775-716">Platí jenom pro ověřování `Individual` nebo `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6775-716">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c6775-717">`--no-restore` – při vytváření projektu nespustí implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="c6775-717">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c6775-718">**MVC, Razor**</span><span class="sxs-lookup"><span data-stu-id="c6775-718">**mvc, razor**</span></span>

<span data-ttu-id="c6775-719">`-au|--auth <AUTHENTICATION_TYPE>` – typ ověřování, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="c6775-719">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="c6775-720">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="c6775-720">The possible values are:</span></span>

- <span data-ttu-id="c6775-721">`None` – bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="c6775-721">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="c6775-722">`Individual` – individuální ověřování.</span><span class="sxs-lookup"><span data-stu-id="c6775-722">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="c6775-723">`IndividualB2C` – individuální ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="c6775-723">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="c6775-724">`SingleOrg` – ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="c6775-724">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="c6775-725">`MultiOrg` – ověřování organizace pro více tenantů.</span><span class="sxs-lookup"><span data-stu-id="c6775-725">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="c6775-726">`Windows` – ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="c6775-726">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="c6775-727">`--aad-b2c-instance <INSTANCE>` – instance Azure Active Directory B2C, ke které se chcete připojit</span><span class="sxs-lookup"><span data-stu-id="c6775-727">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="c6775-728">Použijte s ověřováním `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6775-728">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="c6775-729">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="c6775-729">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="c6775-730">`-ssp|--susi-policy-id <ID>` – ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="c6775-730">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="c6775-731">Použijte s ověřováním `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6775-731">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c6775-732">`-rp|--reset-password-policy-id <ID>` – ID zásad pro resetování hesla pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="c6775-732">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="c6775-733">Použijte s ověřováním `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6775-733">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c6775-734">`-ep|--edit-profile-policy-id <ID>` – ID zásad úprav profilu pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="c6775-734">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="c6775-735">Použijte s ověřováním `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6775-735">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c6775-736">`--aad-instance <INSTANCE>` – instance Azure Active Directory, ke které se chcete připojit</span><span class="sxs-lookup"><span data-stu-id="c6775-736">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="c6775-737">Použijte s ověřováním `SingleOrg` nebo `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6775-737">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="c6775-738">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="c6775-738">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="c6775-739">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="c6775-739">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="c6775-740">Použijte s ověřováním `IndividualB2C`, `SingleOrg`nebo `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6775-740">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="c6775-741">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="c6775-741">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="c6775-742">`--domain <DOMAIN>` – doména pro tenanta adresáře.</span><span class="sxs-lookup"><span data-stu-id="c6775-742">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="c6775-743">Použijte s ověřováním `SingleOrg` nebo `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6775-743">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c6775-744">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="c6775-744">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="c6775-745">`--tenant-id <ID>` – ID TenantId adresáře, ke kterému se má připojit.</span><span class="sxs-lookup"><span data-stu-id="c6775-745">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="c6775-746">Použijte s ověřováním `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6775-746">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c6775-747">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="c6775-747">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="c6775-748">`--callback-path <PATH>` – cesta požadavku v základní cestě identifikátoru URI pro přesměrování.</span><span class="sxs-lookup"><span data-stu-id="c6775-748">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="c6775-749">Použijte s ověřováním `SingleOrg` nebo `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6775-749">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c6775-750">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="c6775-750">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="c6775-751">`-r|--org-read-access` – povolí této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="c6775-751">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="c6775-752">Platí jenom pro ověřování `SingleOrg` nebo `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6775-752">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="c6775-753">`--use-launch-settings` – obsahuje ve výstupu vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="c6775-753">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="c6775-754">`--use-browserlink` – zahrnuje BrowserLink do projektu.</span><span class="sxs-lookup"><span data-stu-id="c6775-754">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="c6775-755">`-uld|--use-local-db` – určuje, že se má místo SQLite použít LocalDB.</span><span class="sxs-lookup"><span data-stu-id="c6775-755">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c6775-756">Platí jenom pro ověřování `Individual` nebo `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6775-756">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c6775-757">`--no-restore` – při vytváření projektu nespustí implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="c6775-757">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c6775-758">**Page**</span><span class="sxs-lookup"><span data-stu-id="c6775-758">**page**</span></span>

<span data-ttu-id="c6775-759">`-na|--namespace <NAMESPACE_NAME>`– obor názvů pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="c6775-759">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="c6775-760">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="c6775-760">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="c6775-761">`-np|--no-pagemodel` – vytvoří stránku bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="c6775-761">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="c6775-762">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="c6775-762">**viewimports**</span></span>

<span data-ttu-id="c6775-763">`-na|--namespace <NAMESPACE_NAME>`– obor názvů pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="c6775-763">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="c6775-764">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="c6775-764">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c6775-765">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="c6775-765">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="c6775-766">**Konzola, xUnit, MSTest, web, WebApi**</span><span class="sxs-lookup"><span data-stu-id="c6775-766">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="c6775-767">`-f|--framework <FRAMEWORK>` – Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="c6775-767">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c6775-768">Hodnoty: `netcoreapp1.0` nebo `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="c6775-768">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="c6775-769">Výchozí hodnota je `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="c6775-769">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="c6775-770">**že knihovna tříd**</span><span class="sxs-lookup"><span data-stu-id="c6775-770">**classlib**</span></span>

<span data-ttu-id="c6775-771">`-f|--framework <FRAMEWORK>` – Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="c6775-771">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c6775-772">Hodnoty: `netcoreapp1.0`, `netcoreapp1.1`nebo `netstandard1.0` do `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="c6775-772">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="c6775-773">Výchozí hodnota je `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="c6775-773">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="c6775-774">**Návrhový**</span><span class="sxs-lookup"><span data-stu-id="c6775-774">**mvc**</span></span>

<span data-ttu-id="c6775-775">`-f|--framework <FRAMEWORK>` – Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="c6775-775">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c6775-776">Hodnoty: `netcoreapp1.0` nebo `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="c6775-776">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="c6775-777">Výchozí hodnota je `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="c6775-777">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="c6775-778">`-au|--auth <AUTHENTICATION_TYPE>` – typ ověřování, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="c6775-778">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="c6775-779">Hodnoty: `None` nebo `Individual`.</span><span class="sxs-lookup"><span data-stu-id="c6775-779">Values: `None` or `Individual`.</span></span> <span data-ttu-id="c6775-780">Výchozí hodnota je `None`.</span><span class="sxs-lookup"><span data-stu-id="c6775-780">The default value is `None`.</span></span>

<span data-ttu-id="c6775-781">`-uld|--use-local-db` – určuje, jestli se místo SQLite použije LocalDB.</span><span class="sxs-lookup"><span data-stu-id="c6775-781">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="c6775-782">Hodnoty: `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="c6775-782">Values: `true` or `false`.</span></span> <span data-ttu-id="c6775-783">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="c6775-783">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="c6775-784">Příklady</span><span class="sxs-lookup"><span data-stu-id="c6775-784">Examples</span></span>

<span data-ttu-id="c6775-785">Vytvořte projekt C# konzolové aplikace zadáním názvu šablony:</span><span class="sxs-lookup"><span data-stu-id="c6775-785">Create a C# console application project by specifying the template name:</span></span>

`dotnet new "Console Application"`

<span data-ttu-id="c6775-786">Vytvořte projekt F# konzolové aplikace v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="c6775-786">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="c6775-787">Vytvořit projekt knihovny tříd .NET Standard v zadaném adresáři (k dispozici pouze s .NET Core SDK 2,0 nebo novějšími verzemi):</span><span class="sxs-lookup"><span data-stu-id="c6775-787">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="c6775-788">Vytvoří nový projekt ASP.NET Core C# MVC v aktuálním adresáři bez ověřování:</span><span class="sxs-lookup"><span data-stu-id="c6775-788">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="c6775-789">Vytvořit nový projekt xUnit:</span><span class="sxs-lookup"><span data-stu-id="c6775-789">Create a new xUnit project:</span></span>

`dotnet new xunit`

<span data-ttu-id="c6775-790">Vypíše všechny šablony, které jsou k dispozici pro MVC:</span><span class="sxs-lookup"><span data-stu-id="c6775-790">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="c6775-791">Vypíše všechny šablony, které odpovídají podřetězci *My* .</span><span class="sxs-lookup"><span data-stu-id="c6775-791">List all templates matching the *we* substring.</span></span> <span data-ttu-id="c6775-792">Nebyla nalezena žádná přesná shoda, takže porovnávání dílčích řetězců se shoduje se sloupci krátkého názvu a názvu.</span><span class="sxs-lookup"><span data-stu-id="c6775-792">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

`dotnet new we -l`

<span data-ttu-id="c6775-793">Došlo k pokusu o vyvolání šablony, která odpovídá *NG*.</span><span class="sxs-lookup"><span data-stu-id="c6775-793">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="c6775-794">Pokud nelze určit jednu shodu, Seznamte se se šablonami, které jsou částečné shody.</span><span class="sxs-lookup"><span data-stu-id="c6775-794">If a single match can't be determined, list the templates that are partial matches.</span></span>

`dotnet new ng`

<span data-ttu-id="c6775-795">2,0 nainstalujte šablony aplikace s jednou stránkou pro ASP.NET Core (možnost příkazového řádku, která je dostupná jenom pro .NET Core SDK 1,1 a novější verze):</span><span class="sxs-lookup"><span data-stu-id="c6775-795">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="c6775-796">Vytvoří *Global. JSON* v aktuálním adresáři nastavení verze sady SDK na 2.0.0 (k dispozici pouze s .NET Core SDK 2,0 nebo novějšími verzemi):</span><span class="sxs-lookup"><span data-stu-id="c6775-796">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="c6775-797">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c6775-797">See also</span></span>

- [<span data-ttu-id="c6775-798">Vlastní šablony pro dotnet New</span><span class="sxs-lookup"><span data-stu-id="c6775-798">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="c6775-799">Vytvoření vlastní šablony pro dotnet new</span><span class="sxs-lookup"><span data-stu-id="c6775-799">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="c6775-800">dotnet/dotnet-Template-Samples – úložiště GitHub</span><span class="sxs-lookup"><span data-stu-id="c6775-800">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="c6775-801">Dostupné šablony pro dotnet New</span><span class="sxs-lookup"><span data-stu-id="c6775-801">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
