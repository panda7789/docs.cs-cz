---
title: nový příkaz DotNet
description: Vytvoří nový příkaz dotnet nových projektů .NET Core založených na zadané šabloně.
ms.date: 05/06/2019
ms.openlocfilehash: f8bc8cb59ae6e421f4e9bd05925376399939056d
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65878318"
---
# <a name="dotnet-new"></a><span data-ttu-id="b05e5-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="b05e5-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="b05e5-104">Name</span><span class="sxs-lookup"><span data-stu-id="b05e5-104">Name</span></span>

<span data-ttu-id="b05e5-105">`dotnet new` -Vytvoří nový projekt, konfigurační soubor nebo řešení založené na zadané šabloně.</span><span class="sxs-lookup"><span data-stu-id="b05e5-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b05e5-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="b05e5-106">Synopsis</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="b05e5-107">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="b05e5-107">.NET Core 2.2</span></span>](#tab/netcore22)

```console
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="b05e5-108">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="b05e5-108">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="b05e5-109">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="b05e5-109">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b05e5-110">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="b05e5-110">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="b05e5-111">Popis</span><span class="sxs-lookup"><span data-stu-id="b05e5-111">Description</span></span>

<span data-ttu-id="b05e5-112">`dotnet new` Příkaz poskytuje pohodlný způsob, jak inicializovat platný projekt .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b05e5-112">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="b05e5-113">Příkaz volání [modulu šablon](https://github.com/dotnet/templating) vytvořit artefakty na disku na základě určené šablony a možnosti.</span><span class="sxs-lookup"><span data-stu-id="b05e5-113">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="b05e5-114">Arguments</span><span class="sxs-lookup"><span data-stu-id="b05e5-114">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="b05e5-115">Šablona pro vytvoření instance při vyvolání příkazu.</span><span class="sxs-lookup"><span data-stu-id="b05e5-115">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="b05e5-116">Každá šablona může mít specifické možnosti, které lze předat.</span><span class="sxs-lookup"><span data-stu-id="b05e5-116">Each template might have specific options you can pass.</span></span> <span data-ttu-id="b05e5-117">Další informace najdete v tématu [možnosti šablony](#template-options).</span><span class="sxs-lookup"><span data-stu-id="b05e5-117">For more information, see [Template options](#template-options).</span></span>

<span data-ttu-id="b05e5-118">Pokud `TEMPLATE` hodnota není přesná shoda s textem v **šablony** nebo **krátký název** sloupce odpovídají podřetězci se provádí v těchto dvou sloupců.</span><span class="sxs-lookup"><span data-stu-id="b05e5-118">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column, a substring match is performed on those two columns.</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="b05e5-119">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="b05e5-119">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="b05e5-120">Příkaz obsahuje výchozí seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="b05e5-120">The command contains a default list of templates.</span></span> <span data-ttu-id="b05e5-121">Použití `dotnet new -l` získat seznam dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="b05e5-121">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="b05e5-122">V následující tabulce jsou uvedeny šablony, které jsou předinstalovány se sadou .NET Core SDK 2.2.100.</span><span class="sxs-lookup"><span data-stu-id="b05e5-122">The following table shows the templates that come pre-installed with the .NET Core SDK 2.2.100.</span></span> <span data-ttu-id="b05e5-123">Výchozí jazyk šablony se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="b05e5-123">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="b05e5-124">Šablony</span><span class="sxs-lookup"><span data-stu-id="b05e5-124">Templates</span></span>                                    | <span data-ttu-id="b05e5-125">Krátký název</span><span class="sxs-lookup"><span data-stu-id="b05e5-125">Short Name</span></span>        | <span data-ttu-id="b05e5-126">Jazyk</span><span class="sxs-lookup"><span data-stu-id="b05e5-126">Language</span></span>     | <span data-ttu-id="b05e5-127">Značky</span><span class="sxs-lookup"><span data-stu-id="b05e5-127">Tags</span></span>                                  |
|----------------------------------------------|-------------------|--------------|---------------------------------------|
| <span data-ttu-id="b05e5-128">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="b05e5-128">Console Application</span></span>                          | `console`         | <span data-ttu-id="b05e5-129">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b05e5-129">[C#], F#, VB</span></span> | <span data-ttu-id="b05e5-130">Běžné/konzoly</span><span class="sxs-lookup"><span data-stu-id="b05e5-130">Common/Console</span></span>                        |
| <span data-ttu-id="b05e5-131">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="b05e5-131">Class library</span></span>                                | `classlib`        | <span data-ttu-id="b05e5-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b05e5-132">[C#], F#, VB</span></span> | <span data-ttu-id="b05e5-133">Běžné/knihovny</span><span class="sxs-lookup"><span data-stu-id="b05e5-133">Common/Library</span></span>                        |
| <span data-ttu-id="b05e5-134">Projekt testu jednotek</span><span class="sxs-lookup"><span data-stu-id="b05e5-134">Unit Test Project</span></span>                            | `mstest`          | <span data-ttu-id="b05e5-135">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b05e5-135">[C#], F#, VB</span></span> | <span data-ttu-id="b05e5-136">Test a MSTest</span><span class="sxs-lookup"><span data-stu-id="b05e5-136">Test/MSTest</span></span>                           |
| <span data-ttu-id="b05e5-137">NUnit 3 Test projektu</span><span class="sxs-lookup"><span data-stu-id="b05e5-137">NUnit 3 Test Project</span></span>                         | `nunit`           | <span data-ttu-id="b05e5-138">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b05e5-138">[C#], F#, VB</span></span> | <span data-ttu-id="b05e5-139">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="b05e5-139">Test/NUnit</span></span>                            |
| <span data-ttu-id="b05e5-140">NUnit 3 Test položky</span><span class="sxs-lookup"><span data-stu-id="b05e5-140">NUnit 3 Test Item</span></span>                            | `nunit-test`      | <span data-ttu-id="b05e5-141">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b05e5-141">[C#], F#, VB</span></span> | <span data-ttu-id="b05e5-142">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="b05e5-142">Test/NUnit</span></span>                            |
| <span data-ttu-id="b05e5-143">Projekt testů xUnit</span><span class="sxs-lookup"><span data-stu-id="b05e5-143">xUnit Test Project</span></span>                           | `xunit`           | <span data-ttu-id="b05e5-144">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b05e5-144">[C#], F#, VB</span></span> | <span data-ttu-id="b05e5-145">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="b05e5-145">Test/xUnit</span></span>                            |
| <span data-ttu-id="b05e5-146">Stránka Razor</span><span class="sxs-lookup"><span data-stu-id="b05e5-146">Razor Page</span></span>                                   | `page`            | <span data-ttu-id="b05e5-147">[C#]</span><span class="sxs-lookup"><span data-stu-id="b05e5-147">[C#]</span></span>         | <span data-ttu-id="b05e5-148">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b05e5-148">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="b05e5-149">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="b05e5-149">MVC ViewImports</span></span>                              | `viewimports`     | <span data-ttu-id="b05e5-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="b05e5-150">[C#]</span></span>         | <span data-ttu-id="b05e5-151">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b05e5-151">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="b05e5-152">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="b05e5-152">MVC ViewStart</span></span>                                | `viewstart`       | <span data-ttu-id="b05e5-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="b05e5-153">[C#]</span></span>         | <span data-ttu-id="b05e5-154">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b05e5-154">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="b05e5-155">ASP.NET Core (prázdné)</span><span class="sxs-lookup"><span data-stu-id="b05e5-155">ASP.NET Core Empty</span></span>                           | `web`             | <span data-ttu-id="b05e5-156">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="b05e5-156">[C#], F#</span></span>     | <span data-ttu-id="b05e5-157">Web nebo je prázdný</span><span class="sxs-lookup"><span data-stu-id="b05e5-157">Web/Empty</span></span>                             |
| <span data-ttu-id="b05e5-158">Webové aplikace ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="b05e5-158">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`             | <span data-ttu-id="b05e5-159">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="b05e5-159">[C#], F#</span></span>     | <span data-ttu-id="b05e5-160">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="b05e5-160">Web/MVC</span></span>                               |
| <span data-ttu-id="b05e5-161">Webové aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b05e5-161">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="b05e5-162">`webapp`, `razor`</span><span class="sxs-lookup"><span data-stu-id="b05e5-162">`webapp`, `razor`</span></span> | <span data-ttu-id="b05e5-163">[C#]</span><span class="sxs-lookup"><span data-stu-id="b05e5-163">[C#]</span></span>         | <span data-ttu-id="b05e5-164">Stránky MVC/web/Razor</span><span class="sxs-lookup"><span data-stu-id="b05e5-164">Web/MVC/Razor Pages</span></span>                   |
| <span data-ttu-id="b05e5-165">ASP.NET Core with Angular</span><span class="sxs-lookup"><span data-stu-id="b05e5-165">ASP.NET Core with Angular</span></span>                    | `angular`         | <span data-ttu-id="b05e5-166">[C#]</span><span class="sxs-lookup"><span data-stu-id="b05e5-166">[C#]</span></span>         | <span data-ttu-id="b05e5-167">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="b05e5-167">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="b05e5-168">ASP.NET Core pomocí React.js</span><span class="sxs-lookup"><span data-stu-id="b05e5-168">ASP.NET Core with React.js</span></span>                   | `react`           | <span data-ttu-id="b05e5-169">[C#]</span><span class="sxs-lookup"><span data-stu-id="b05e5-169">[C#]</span></span>         | <span data-ttu-id="b05e5-170">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="b05e5-170">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="b05e5-171">ASP.NET Core pomocí React.js a Redux</span><span class="sxs-lookup"><span data-stu-id="b05e5-171">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`      | <span data-ttu-id="b05e5-172">[C#]</span><span class="sxs-lookup"><span data-stu-id="b05e5-172">[C#]</span></span>         | <span data-ttu-id="b05e5-173">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="b05e5-173">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="b05e5-174">Knihovny tříd Razor</span><span class="sxs-lookup"><span data-stu-id="b05e5-174">Razor Class Library</span></span>                          | `razorclasslib`   | <span data-ttu-id="b05e5-175">[C#]</span><span class="sxs-lookup"><span data-stu-id="b05e5-175">[C#]</span></span>         | <span data-ttu-id="b05e5-176">Knihovna tříd web/Razor/Library/Razor</span><span class="sxs-lookup"><span data-stu-id="b05e5-176">Web/Razor/Library/Razor Class Library</span></span> |
| <span data-ttu-id="b05e5-177">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="b05e5-177">ASP.NET Core Web API</span></span>                         | `webapi`          | <span data-ttu-id="b05e5-178">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="b05e5-178">[C#], F#</span></span>     | <span data-ttu-id="b05e5-179">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="b05e5-179">Web/WebAPI</span></span>                            |
| <span data-ttu-id="b05e5-180">global.json file</span><span class="sxs-lookup"><span data-stu-id="b05e5-180">global.json file</span></span>                             | `globaljson`      |              | <span data-ttu-id="b05e5-181">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="b05e5-181">Config</span></span>                                |
| <span data-ttu-id="b05e5-182">NuGet Config</span><span class="sxs-lookup"><span data-stu-id="b05e5-182">NuGet Config</span></span>                                 | `nugetconfig`     |              | <span data-ttu-id="b05e5-183">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="b05e5-183">Config</span></span>                                |
| <span data-ttu-id="b05e5-184">Webové konfigurace</span><span class="sxs-lookup"><span data-stu-id="b05e5-184">Web Config</span></span>                                   | `webconfig`       |              | <span data-ttu-id="b05e5-185">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="b05e5-185">Config</span></span>                                |
| <span data-ttu-id="b05e5-186">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="b05e5-186">Solution File</span></span>                                | `sln`             |              | <span data-ttu-id="b05e5-187">Řešení</span><span class="sxs-lookup"><span data-stu-id="b05e5-187">Solution</span></span>                              |

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="b05e5-188">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="b05e5-188">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="b05e5-189">Příkaz obsahuje výchozí seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="b05e5-189">The command contains a default list of templates.</span></span> <span data-ttu-id="b05e5-190">Použití `dotnet new -l` získat seznam dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="b05e5-190">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="b05e5-191">V následující tabulce jsou uvedeny šablony, které jsou předinstalovány se sadou .NET Core SDK 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="b05e5-191">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="b05e5-192">Výchozí jazyk šablony se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="b05e5-192">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="b05e5-193">Šablony</span><span class="sxs-lookup"><span data-stu-id="b05e5-193">Templates</span></span>                                    | <span data-ttu-id="b05e5-194">Krátký název</span><span class="sxs-lookup"><span data-stu-id="b05e5-194">Short Name</span></span>      | <span data-ttu-id="b05e5-195">Jazyk</span><span class="sxs-lookup"><span data-stu-id="b05e5-195">Language</span></span>     | <span data-ttu-id="b05e5-196">Značky</span><span class="sxs-lookup"><span data-stu-id="b05e5-196">Tags</span></span>                                  |
|----------------------------------------------|-----------------|--------------|---------------------------------------|
| <span data-ttu-id="b05e5-197">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="b05e5-197">Console Application</span></span>                          | `console`       | <span data-ttu-id="b05e5-198">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b05e5-198">[C#], F#, VB</span></span> | <span data-ttu-id="b05e5-199">Běžné/konzoly</span><span class="sxs-lookup"><span data-stu-id="b05e5-199">Common/Console</span></span>                        |
| <span data-ttu-id="b05e5-200">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="b05e5-200">Class library</span></span>                                | `classlib`      | <span data-ttu-id="b05e5-201">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b05e5-201">[C#], F#, VB</span></span> | <span data-ttu-id="b05e5-202">Běžné/knihovny</span><span class="sxs-lookup"><span data-stu-id="b05e5-202">Common/Library</span></span>                        |
| <span data-ttu-id="b05e5-203">Projekt testu jednotek</span><span class="sxs-lookup"><span data-stu-id="b05e5-203">Unit Test Project</span></span>                            | `mstest`        | <span data-ttu-id="b05e5-204">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b05e5-204">[C#], F#, VB</span></span> | <span data-ttu-id="b05e5-205">Test a MSTest</span><span class="sxs-lookup"><span data-stu-id="b05e5-205">Test/MSTest</span></span>                           |
| <span data-ttu-id="b05e5-206">Projekt testů xUnit</span><span class="sxs-lookup"><span data-stu-id="b05e5-206">xUnit Test Project</span></span>                           | `xunit`         | <span data-ttu-id="b05e5-207">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b05e5-207">[C#], F#, VB</span></span> | <span data-ttu-id="b05e5-208">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="b05e5-208">Test/xUnit</span></span>                            |
| <span data-ttu-id="b05e5-209">Stránka Razor</span><span class="sxs-lookup"><span data-stu-id="b05e5-209">Razor Page</span></span>                                   | `page`          | <span data-ttu-id="b05e5-210">[C#]</span><span class="sxs-lookup"><span data-stu-id="b05e5-210">[C#]</span></span>         | <span data-ttu-id="b05e5-211">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b05e5-211">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="b05e5-212">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="b05e5-212">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="b05e5-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="b05e5-213">[C#]</span></span>         | <span data-ttu-id="b05e5-214">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b05e5-214">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="b05e5-215">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="b05e5-215">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="b05e5-216">[C#]</span><span class="sxs-lookup"><span data-stu-id="b05e5-216">[C#]</span></span>         | <span data-ttu-id="b05e5-217">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b05e5-217">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="b05e5-218">ASP.NET Core (prázdné)</span><span class="sxs-lookup"><span data-stu-id="b05e5-218">ASP.NET Core Empty</span></span>                           | `web`           | <span data-ttu-id="b05e5-219">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="b05e5-219">[C#], F#</span></span>     | <span data-ttu-id="b05e5-220">Web nebo je prázdný</span><span class="sxs-lookup"><span data-stu-id="b05e5-220">Web/Empty</span></span>                             |
| <span data-ttu-id="b05e5-221">Webové aplikace ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="b05e5-221">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="b05e5-222">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="b05e5-222">[C#], F#</span></span>     | <span data-ttu-id="b05e5-223">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="b05e5-223">Web/MVC</span></span>                               |
| <span data-ttu-id="b05e5-224">Webové aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b05e5-224">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="b05e5-225">[C#]</span><span class="sxs-lookup"><span data-stu-id="b05e5-225">[C#]</span></span>         | <span data-ttu-id="b05e5-226">Stránky MVC/web/Razor</span><span class="sxs-lookup"><span data-stu-id="b05e5-226">Web/MVC/Razor Pages</span></span>                   |
| <span data-ttu-id="b05e5-227">ASP.NET Core with Angular</span><span class="sxs-lookup"><span data-stu-id="b05e5-227">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="b05e5-228">[C#]</span><span class="sxs-lookup"><span data-stu-id="b05e5-228">[C#]</span></span>         | <span data-ttu-id="b05e5-229">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="b05e5-229">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="b05e5-230">ASP.NET Core pomocí React.js</span><span class="sxs-lookup"><span data-stu-id="b05e5-230">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="b05e5-231">[C#]</span><span class="sxs-lookup"><span data-stu-id="b05e5-231">[C#]</span></span>         | <span data-ttu-id="b05e5-232">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="b05e5-232">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="b05e5-233">ASP.NET Core pomocí React.js a Redux</span><span class="sxs-lookup"><span data-stu-id="b05e5-233">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="b05e5-234">[C#]</span><span class="sxs-lookup"><span data-stu-id="b05e5-234">[C#]</span></span>         | <span data-ttu-id="b05e5-235">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="b05e5-235">Web/MVC/SPA</span></span>                           | 
| <span data-ttu-id="b05e5-236">Knihovny tříd Razor</span><span class="sxs-lookup"><span data-stu-id="b05e5-236">Razor Class Library</span></span>                          | `razorclasslib` | <span data-ttu-id="b05e5-237">[C#]</span><span class="sxs-lookup"><span data-stu-id="b05e5-237">[C#]</span></span>         | <span data-ttu-id="b05e5-238">Knihovna tříd web/Razor/Library/Razor</span><span class="sxs-lookup"><span data-stu-id="b05e5-238">Web/Razor/Library/Razor Class Library</span></span> |
| <span data-ttu-id="b05e5-239">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="b05e5-239">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="b05e5-240">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="b05e5-240">[C#], F#</span></span>     | <span data-ttu-id="b05e5-241">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="b05e5-241">Web/WebAPI</span></span>                            |
| <span data-ttu-id="b05e5-242">global.json file</span><span class="sxs-lookup"><span data-stu-id="b05e5-242">global.json file</span></span>                             | `globaljson`    |              | <span data-ttu-id="b05e5-243">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="b05e5-243">Config</span></span>                                |
| <span data-ttu-id="b05e5-244">NuGet Config</span><span class="sxs-lookup"><span data-stu-id="b05e5-244">NuGet Config</span></span>                                 | `nugetconfig`   |              | <span data-ttu-id="b05e5-245">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="b05e5-245">Config</span></span>                                |
| <span data-ttu-id="b05e5-246">Webové konfigurace</span><span class="sxs-lookup"><span data-stu-id="b05e5-246">Web Config</span></span>                                   | `webconfig`     |              | <span data-ttu-id="b05e5-247">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="b05e5-247">Config</span></span>                                |
| <span data-ttu-id="b05e5-248">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="b05e5-248">Solution File</span></span>                                | `sln`           |              | <span data-ttu-id="b05e5-249">Řešení</span><span class="sxs-lookup"><span data-stu-id="b05e5-249">Solution</span></span>                              |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="b05e5-250">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="b05e5-250">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="b05e5-251">Příkaz obsahuje výchozí seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="b05e5-251">The command contains a default list of templates.</span></span> <span data-ttu-id="b05e5-252">Použití `dotnet new -l` získat seznam dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="b05e5-252">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="b05e5-253">V následující tabulce jsou uvedeny šablony, které jsou předem nainstalované s .NET Core SDK 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="b05e5-253">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.0.</span></span> <span data-ttu-id="b05e5-254">Výchozí jazyk šablony se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="b05e5-254">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="b05e5-255">Šablony</span><span class="sxs-lookup"><span data-stu-id="b05e5-255">Templates</span></span>                                    | <span data-ttu-id="b05e5-256">Krátký název</span><span class="sxs-lookup"><span data-stu-id="b05e5-256">Short Name</span></span>    | <span data-ttu-id="b05e5-257">Jazyk</span><span class="sxs-lookup"><span data-stu-id="b05e5-257">Language</span></span>     | <span data-ttu-id="b05e5-258">Značky</span><span class="sxs-lookup"><span data-stu-id="b05e5-258">Tags</span></span>                |
|----------------------------------------------|---------------|--------------|---------------------|
| <span data-ttu-id="b05e5-259">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="b05e5-259">Console Application</span></span>                          | `console`     | <span data-ttu-id="b05e5-260">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b05e5-260">[C#], F#, VB</span></span> | <span data-ttu-id="b05e5-261">Běžné/konzoly</span><span class="sxs-lookup"><span data-stu-id="b05e5-261">Common/Console</span></span>      |
| <span data-ttu-id="b05e5-262">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="b05e5-262">Class library</span></span>                                | `classlib`    | <span data-ttu-id="b05e5-263">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b05e5-263">[C#], F#, VB</span></span> | <span data-ttu-id="b05e5-264">Běžné/knihovny</span><span class="sxs-lookup"><span data-stu-id="b05e5-264">Common/Library</span></span>      |
| <span data-ttu-id="b05e5-265">Projekt testu jednotek</span><span class="sxs-lookup"><span data-stu-id="b05e5-265">Unit Test Project</span></span>                            | `mstest`      | <span data-ttu-id="b05e5-266">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b05e5-266">[C#], F#, VB</span></span> | <span data-ttu-id="b05e5-267">Test a MSTest</span><span class="sxs-lookup"><span data-stu-id="b05e5-267">Test/MSTest</span></span>         |
| <span data-ttu-id="b05e5-268">Projekt testů xUnit</span><span class="sxs-lookup"><span data-stu-id="b05e5-268">xUnit Test Project</span></span>                           | `xunit`       | <span data-ttu-id="b05e5-269">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="b05e5-269">[C#], F#, VB</span></span> | <span data-ttu-id="b05e5-270">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="b05e5-270">Test/xUnit</span></span>          |
| <span data-ttu-id="b05e5-271">ASP.NET Core (prázdné)</span><span class="sxs-lookup"><span data-stu-id="b05e5-271">ASP.NET Core Empty</span></span>                           | `web`         | <span data-ttu-id="b05e5-272">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="b05e5-272">[C#], F#</span></span>     | <span data-ttu-id="b05e5-273">Web nebo je prázdný</span><span class="sxs-lookup"><span data-stu-id="b05e5-273">Web/Empty</span></span>           |
| <span data-ttu-id="b05e5-274">Webové aplikace ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="b05e5-274">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="b05e5-275">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="b05e5-275">[C#], F#</span></span>     | <span data-ttu-id="b05e5-276">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="b05e5-276">Web/MVC</span></span>             |
| <span data-ttu-id="b05e5-277">Webové aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b05e5-277">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="b05e5-278">[C#]</span><span class="sxs-lookup"><span data-stu-id="b05e5-278">[C#]</span></span>         | <span data-ttu-id="b05e5-279">Stránky MVC/web/Razor</span><span class="sxs-lookup"><span data-stu-id="b05e5-279">Web/MVC/Razor Pages</span></span> |
| <span data-ttu-id="b05e5-280">ASP.NET Core with Angular</span><span class="sxs-lookup"><span data-stu-id="b05e5-280">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="b05e5-281">[C#]</span><span class="sxs-lookup"><span data-stu-id="b05e5-281">[C#]</span></span>         | <span data-ttu-id="b05e5-282">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="b05e5-282">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="b05e5-283">ASP.NET Core pomocí React.js</span><span class="sxs-lookup"><span data-stu-id="b05e5-283">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="b05e5-284">[C#]</span><span class="sxs-lookup"><span data-stu-id="b05e5-284">[C#]</span></span>         | <span data-ttu-id="b05e5-285">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="b05e5-285">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="b05e5-286">ASP.NET Core pomocí React.js a Redux</span><span class="sxs-lookup"><span data-stu-id="b05e5-286">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="b05e5-287">[C#]</span><span class="sxs-lookup"><span data-stu-id="b05e5-287">[C#]</span></span>         | <span data-ttu-id="b05e5-288">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="b05e5-288">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="b05e5-289">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="b05e5-289">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="b05e5-290">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="b05e5-290">[C#], F#</span></span>     | <span data-ttu-id="b05e5-291">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="b05e5-291">Web/WebAPI</span></span>          |
| <span data-ttu-id="b05e5-292">global.json file</span><span class="sxs-lookup"><span data-stu-id="b05e5-292">global.json file</span></span>                             | `globaljson`  |              | <span data-ttu-id="b05e5-293">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="b05e5-293">Config</span></span>              |
| <span data-ttu-id="b05e5-294">Nuget Config</span><span class="sxs-lookup"><span data-stu-id="b05e5-294">Nuget Config</span></span>                                 | `nugetconfig` |              | <span data-ttu-id="b05e5-295">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="b05e5-295">Config</span></span>              |
| <span data-ttu-id="b05e5-296">Webové konfigurace</span><span class="sxs-lookup"><span data-stu-id="b05e5-296">Web Config</span></span>                                   | `webconfig`   |              | <span data-ttu-id="b05e5-297">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="b05e5-297">Config</span></span>              |
| <span data-ttu-id="b05e5-298">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="b05e5-298">Solution File</span></span>                                | `sln`         |              | <span data-ttu-id="b05e5-299">Řešení</span><span class="sxs-lookup"><span data-stu-id="b05e5-299">Solution</span></span>            |
| <span data-ttu-id="b05e5-300">Stránka Razor</span><span class="sxs-lookup"><span data-stu-id="b05e5-300">Razor Page</span></span>                                   | `page`        |              | <span data-ttu-id="b05e5-301">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b05e5-301">Web/ASP.NET</span></span>         |
| <span data-ttu-id="b05e5-302">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="b05e5-302">MVC ViewImports</span></span>                              | `viewimports` |              | <span data-ttu-id="b05e5-303">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b05e5-303">Web/ASP.NET</span></span>         |
| <span data-ttu-id="b05e5-304">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="b05e5-304">MVC ViewStart</span></span>                                | `viewstart`   |              | <span data-ttu-id="b05e5-305">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b05e5-305">Web/ASP.NET</span></span>         |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b05e5-306">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="b05e5-306">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="b05e5-307">Příkaz obsahuje výchozí seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="b05e5-307">The command contains a default list of templates.</span></span> <span data-ttu-id="b05e5-308">Použití `dotnet new -all` získat seznam dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="b05e5-308">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="b05e5-309">V následující tabulce jsou uvedeny šablony, které jsou předinstalovány se sadou SDK .NET Core 1.0.1.</span><span class="sxs-lookup"><span data-stu-id="b05e5-309">The following table shows the templates that come pre-installed with the .NET Core SDK 1.0.1.</span></span> <span data-ttu-id="b05e5-310">Výchozí jazyk šablony se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="b05e5-310">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="b05e5-311">Šablony</span><span class="sxs-lookup"><span data-stu-id="b05e5-311">Templates</span></span>            | <span data-ttu-id="b05e5-312">Krátký název</span><span class="sxs-lookup"><span data-stu-id="b05e5-312">Short Name</span></span>    | <span data-ttu-id="b05e5-313">Jazyk</span><span class="sxs-lookup"><span data-stu-id="b05e5-313">Language</span></span> | <span data-ttu-id="b05e5-314">Značky</span><span class="sxs-lookup"><span data-stu-id="b05e5-314">Tags</span></span>           |
|----------------------|---------------|----------|----------------|
| <span data-ttu-id="b05e5-315">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="b05e5-315">Console Application</span></span>  | `console`     | <span data-ttu-id="b05e5-316">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="b05e5-316">[C#], F#</span></span> | <span data-ttu-id="b05e5-317">Běžné/konzoly</span><span class="sxs-lookup"><span data-stu-id="b05e5-317">Common/Console</span></span> |
| <span data-ttu-id="b05e5-318">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="b05e5-318">Class library</span></span>        | `classlib`    | <span data-ttu-id="b05e5-319">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="b05e5-319">[C#], F#</span></span> | <span data-ttu-id="b05e5-320">Běžné/knihovny</span><span class="sxs-lookup"><span data-stu-id="b05e5-320">Common/Library</span></span> |
| <span data-ttu-id="b05e5-321">Projekt testu jednotek</span><span class="sxs-lookup"><span data-stu-id="b05e5-321">Unit Test Project</span></span>    | `mstest`      | <span data-ttu-id="b05e5-322">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="b05e5-322">[C#], F#</span></span> | <span data-ttu-id="b05e5-323">Test a MSTest</span><span class="sxs-lookup"><span data-stu-id="b05e5-323">Test/MSTest</span></span>    |
| <span data-ttu-id="b05e5-324">Projekt testů xUnit</span><span class="sxs-lookup"><span data-stu-id="b05e5-324">xUnit Test Project</span></span>   | `xunit`       | <span data-ttu-id="b05e5-325">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="b05e5-325">[C#], F#</span></span> | <span data-ttu-id="b05e5-326">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="b05e5-326">Test/xUnit</span></span>     |
| <span data-ttu-id="b05e5-327">ASP.NET Core (prázdné)</span><span class="sxs-lookup"><span data-stu-id="b05e5-327">ASP.NET Core Empty</span></span>   | `web`         | <span data-ttu-id="b05e5-328">[C#]</span><span class="sxs-lookup"><span data-stu-id="b05e5-328">[C#]</span></span>     | <span data-ttu-id="b05e5-329">Web nebo je prázdný</span><span class="sxs-lookup"><span data-stu-id="b05e5-329">Web/Empty</span></span>      |
| <span data-ttu-id="b05e5-330">Webové aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b05e5-330">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="b05e5-331">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="b05e5-331">[C#], F#</span></span> | <span data-ttu-id="b05e5-332">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="b05e5-332">Web/MVC</span></span>        |
| <span data-ttu-id="b05e5-333">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="b05e5-333">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="b05e5-334">[C#]</span><span class="sxs-lookup"><span data-stu-id="b05e5-334">[C#]</span></span>     | <span data-ttu-id="b05e5-335">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="b05e5-335">Web/WebAPI</span></span>     |
| <span data-ttu-id="b05e5-336">Nuget Config</span><span class="sxs-lookup"><span data-stu-id="b05e5-336">Nuget Config</span></span>         | `nugetconfig` |          | <span data-ttu-id="b05e5-337">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="b05e5-337">Config</span></span>         |
| <span data-ttu-id="b05e5-338">Webové konfigurace</span><span class="sxs-lookup"><span data-stu-id="b05e5-338">Web Config</span></span>           | `webconfig`   |          | <span data-ttu-id="b05e5-339">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="b05e5-339">Config</span></span>         |
| <span data-ttu-id="b05e5-340">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="b05e5-340">Solution File</span></span>        | `sln`         |          | <span data-ttu-id="b05e5-341">Řešení</span><span class="sxs-lookup"><span data-stu-id="b05e5-341">Solution</span></span>       |

---

## <a name="options"></a><span data-ttu-id="b05e5-342">Možnosti</span><span class="sxs-lookup"><span data-stu-id="b05e5-342">Options</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="b05e5-343">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="b05e5-343">.NET Core 2.2</span></span>](#tab/netcore22)

`--dry-run`

<span data-ttu-id="b05e5-344">Zobrazí souhrn co by mohlo dojít, pokud daný příkaz byly spuštěny, pokud by výsledkem vytváření šablon.</span><span class="sxs-lookup"><span data-stu-id="b05e5-344">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span>

`--force`

<span data-ttu-id="b05e5-345">Vynutí obsahu chcete vygenerovat i v případě, že by došlo ke změně existujících souborů.</span><span class="sxs-lookup"><span data-stu-id="b05e5-345">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="b05e5-346">To je potřeba při výstupní adresář již obsahuje projekt.</span><span class="sxs-lookup"><span data-stu-id="b05e5-346">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="b05e5-347">Vytiskne nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="b05e5-347">Prints out help for the command.</span></span> <span data-ttu-id="b05e5-348">Může být vyvolána pro `dotnet new` samotný příkaz nebo pro všechny šablony, jako například `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-348">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="b05e5-349">Nainstaluje zdroj nebo šablony pack z `PATH` nebo `NUGET_ID` k dispozici.</span><span class="sxs-lookup"><span data-stu-id="b05e5-349">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="b05e5-350">Pokud chcete nainstalovat zkušební verzi balíčku šablony, je třeba zadat verzi ve formátu `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-350">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="b05e5-351">Ve výchozím nastavení `dotnet new` předá \* pro verzi, která představuje poslední stabilní balíček verze.</span><span class="sxs-lookup"><span data-stu-id="b05e5-351">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="b05e5-352">Podívejte se příklad na [příklady](#examples) oddílu.</span><span class="sxs-lookup"><span data-stu-id="b05e5-352">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="b05e5-353">Informace o vytváření vlastních šablon najdete v tématu [vlastních šablon pro dotnet nové](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="b05e5-353">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="b05e5-354">Zobrazí seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="b05e5-354">Lists templates containing the specified name.</span></span> <span data-ttu-id="b05e5-355">Pokud je vyvolána `dotnet new` příkazu, uvádí možné šablony, které jsou k dispozici pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="b05e5-355">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="b05e5-356">Například pokud adresář, projekt již obsahuje, neobsahuje všechny šablony projektů.</span><span class="sxs-lookup"><span data-stu-id="b05e5-356">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="b05e5-357">Jazyk šablony k vytvoření.</span><span class="sxs-lookup"><span data-stu-id="b05e5-357">The language of the template to create.</span></span> <span data-ttu-id="b05e5-358">Jazyk přijato, se liší podle šablony (Zobrazit výchozí hodnoty v [argumenty](#arguments) části).</span><span class="sxs-lookup"><span data-stu-id="b05e5-358">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="b05e5-359">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="b05e5-359">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="b05e5-360">Některé součásti pro interpretaci `#` jako speciální znak.</span><span class="sxs-lookup"><span data-stu-id="b05e5-360">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="b05e5-361">V takových případech bude nutné uvést hodnotu parametru jazyka, jako `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-361">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="b05e5-362">Název pro výstup vytvořený.</span><span class="sxs-lookup"><span data-stu-id="b05e5-362">The name for the created output.</span></span> <span data-ttu-id="b05e5-363">Pokud není zadán žádný název, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="b05e5-363">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="b05e5-364">Určuje zdroj NuGet, který chcete použít během instalace.</span><span class="sxs-lookup"><span data-stu-id="b05e5-364">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="b05e5-365">Umístění pro vygenerovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="b05e5-365">Location to place the generated output.</span></span> <span data-ttu-id="b05e5-366">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="b05e5-366">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="b05e5-367">Vyfiltruje šablony podle dostupných typů.</span><span class="sxs-lookup"><span data-stu-id="b05e5-367">Filters templates based on available types.</span></span> <span data-ttu-id="b05e5-368">Předdefinované hodnoty jsou "projekt", "item" nebo "jiné".</span><span class="sxs-lookup"><span data-stu-id="b05e5-368">Predefined values are "project", "item", or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="b05e5-369">Odinstaluje zdroj nebo šablony pack na `PATH` nebo `NUGET_ID` k dispozici.</span><span class="sxs-lookup"><span data-stu-id="b05e5-369">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="b05e5-370">Při vylučování `<PATH|NUGET_ID>` zobrazené hodnoty, všechny aktuálně nainstalované šablonované balíčky a jejich přidružené šablony.</span><span class="sxs-lookup"><span data-stu-id="b05e5-370">When excluding the `<PATH|NUGET_ID>` value, all currently installed template packs and their associated templates are displayed.</span></span>

> [!NOTE]
> <span data-ttu-id="b05e5-371">Chcete-li odinstalovat sadu pomocí šablony `PATH`, budete potřebovat plně kvalifikovanou cestu.</span><span class="sxs-lookup"><span data-stu-id="b05e5-371">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="b05e5-372">Například *C:/uživatele/\<uživatele > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z obsahuje složky nebudou.</span><span class="sxs-lookup"><span data-stu-id="b05e5-372">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="b05e5-373">Kromě toho nesmí být znak konečné ukončující znak lomítka adresáře na cestu k šabloně.</span><span class="sxs-lookup"><span data-stu-id="b05e5-373">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="b05e5-374">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="b05e5-374">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="b05e5-375">Vynutí obsahu chcete vygenerovat i v případě, že by došlo ke změně existujících souborů.</span><span class="sxs-lookup"><span data-stu-id="b05e5-375">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="b05e5-376">To je potřeba při výstupní adresář již obsahuje projekt.</span><span class="sxs-lookup"><span data-stu-id="b05e5-376">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="b05e5-377">Vytiskne nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="b05e5-377">Prints out help for the command.</span></span> <span data-ttu-id="b05e5-378">Může být vyvolána pro `dotnet new` samotný příkaz nebo pro všechny šablony, jako například `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-378">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="b05e5-379">Nainstaluje zdroj nebo šablony pack z `PATH` nebo `NUGET_ID` k dispozici.</span><span class="sxs-lookup"><span data-stu-id="b05e5-379">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="b05e5-380">Pokud chcete nainstalovat zkušební verzi balíčku šablony, je třeba zadat verzi ve formátu `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-380">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="b05e5-381">Ve výchozím nastavení `dotnet new` předá \* pro verzi, která představuje poslední stabilní balíček verze.</span><span class="sxs-lookup"><span data-stu-id="b05e5-381">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="b05e5-382">Podívejte se příklad na [příklady](#examples) oddílu.</span><span class="sxs-lookup"><span data-stu-id="b05e5-382">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="b05e5-383">Informace o vytváření vlastních šablon najdete v tématu [vlastních šablon pro dotnet nové](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="b05e5-383">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="b05e5-384">Zobrazí seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="b05e5-384">Lists templates containing the specified name.</span></span> <span data-ttu-id="b05e5-385">Pokud je vyvolána `dotnet new` příkazu, uvádí možné šablony, které jsou k dispozici pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="b05e5-385">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="b05e5-386">Například pokud adresář, projekt již obsahuje, neobsahuje všechny šablony projektů.</span><span class="sxs-lookup"><span data-stu-id="b05e5-386">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="b05e5-387">Jazyk šablony k vytvoření.</span><span class="sxs-lookup"><span data-stu-id="b05e5-387">The language of the template to create.</span></span> <span data-ttu-id="b05e5-388">Jazyk přijato, se liší podle šablony (Zobrazit výchozí hodnoty v [argumenty](#arguments) části).</span><span class="sxs-lookup"><span data-stu-id="b05e5-388">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="b05e5-389">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="b05e5-389">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="b05e5-390">Některé součásti pro interpretaci `#` jako speciální znak.</span><span class="sxs-lookup"><span data-stu-id="b05e5-390">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="b05e5-391">V takových případech bude nutné uvést hodnotu parametru jazyka, jako `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-391">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="b05e5-392">Název pro výstup vytvořený.</span><span class="sxs-lookup"><span data-stu-id="b05e5-392">The name for the created output.</span></span> <span data-ttu-id="b05e5-393">Pokud není zadán žádný název, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="b05e5-393">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="b05e5-394">Určuje zdroj NuGet, který chcete použít během instalace.</span><span class="sxs-lookup"><span data-stu-id="b05e5-394">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="b05e5-395">Umístění pro vygenerovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="b05e5-395">Location to place the generated output.</span></span> <span data-ttu-id="b05e5-396">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="b05e5-396">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="b05e5-397">Vyfiltruje šablony podle dostupných typů.</span><span class="sxs-lookup"><span data-stu-id="b05e5-397">Filters templates based on available types.</span></span> <span data-ttu-id="b05e5-398">Předdefinované hodnoty jsou "projekt", "item" nebo "jiné".</span><span class="sxs-lookup"><span data-stu-id="b05e5-398">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="b05e5-399">Odinstaluje zdroj nebo šablony pack na `PATH` nebo `NUGET_ID` k dispozici.</span><span class="sxs-lookup"><span data-stu-id="b05e5-399">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="b05e5-400">Chcete-li odinstalovat sadu pomocí šablony `PATH`, budete potřebovat plně kvalifikovanou cestu.</span><span class="sxs-lookup"><span data-stu-id="b05e5-400">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="b05e5-401">Například *C:/uživatele/\<uživatele > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z obsahuje složky nebudou.</span><span class="sxs-lookup"><span data-stu-id="b05e5-401">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="b05e5-402">Kromě toho nesmí být znak konečné ukončující znak lomítka adresáře na cestu k šabloně.</span><span class="sxs-lookup"><span data-stu-id="b05e5-402">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="b05e5-403">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="b05e5-403">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="b05e5-404">Vynutí obsahu chcete vygenerovat i v případě, že by došlo ke změně existujících souborů.</span><span class="sxs-lookup"><span data-stu-id="b05e5-404">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="b05e5-405">To je potřeba při výstupní adresář již obsahuje projekt.</span><span class="sxs-lookup"><span data-stu-id="b05e5-405">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="b05e5-406">Vytiskne nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="b05e5-406">Prints out help for the command.</span></span> <span data-ttu-id="b05e5-407">Může být vyvolána pro `dotnet new` samotný příkaz nebo pro všechny šablony, jako například `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-407">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="b05e5-408">Nainstaluje zdroj nebo šablony pack z `PATH` nebo `NUGET_ID` k dispozici.</span><span class="sxs-lookup"><span data-stu-id="b05e5-408">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="b05e5-409">Pokud chcete nainstalovat zkušební verzi balíčku šablony, je třeba zadat verzi ve formátu `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-409">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="b05e5-410">Ve výchozím nastavení `dotnet new` předá \* pro verzi, která představuje poslední stabilní balíček verze.</span><span class="sxs-lookup"><span data-stu-id="b05e5-410">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="b05e5-411">Podívejte se příklad na [příklady](#examples) oddílu.</span><span class="sxs-lookup"><span data-stu-id="b05e5-411">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="b05e5-412">Informace o vytváření vlastních šablon najdete v tématu [vlastních šablon pro dotnet nové](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="b05e5-412">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="b05e5-413">Zobrazí seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="b05e5-413">Lists templates containing the specified name.</span></span> <span data-ttu-id="b05e5-414">Pokud je vyvolána `dotnet new` příkazu, uvádí možné šablony, které jsou k dispozici pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="b05e5-414">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="b05e5-415">Například pokud adresář, projekt již obsahuje, neobsahuje všechny šablony projektů.</span><span class="sxs-lookup"><span data-stu-id="b05e5-415">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="b05e5-416">Jazyk šablony k vytvoření.</span><span class="sxs-lookup"><span data-stu-id="b05e5-416">The language of the template to create.</span></span> <span data-ttu-id="b05e5-417">Jazyk přijato, se liší podle šablony (Zobrazit výchozí hodnoty v [argumenty](#arguments) části).</span><span class="sxs-lookup"><span data-stu-id="b05e5-417">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="b05e5-418">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="b05e5-418">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="b05e5-419">Některé součásti pro interpretaci `#` jako speciální znak.</span><span class="sxs-lookup"><span data-stu-id="b05e5-419">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="b05e5-420">V takových případech bude nutné uvést hodnotu parametru jazyka, jako `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-420">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="b05e5-421">Název pro výstup vytvořený.</span><span class="sxs-lookup"><span data-stu-id="b05e5-421">The name for the created output.</span></span> <span data-ttu-id="b05e5-422">Pokud není zadán žádný název, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="b05e5-422">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="b05e5-423">Umístění pro vygenerovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="b05e5-423">Location to place the generated output.</span></span> <span data-ttu-id="b05e5-424">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="b05e5-424">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="b05e5-425">Vyfiltruje šablony podle dostupných typů.</span><span class="sxs-lookup"><span data-stu-id="b05e5-425">Filters templates based on available types.</span></span> <span data-ttu-id="b05e5-426">Předdefinované hodnoty jsou "projekt", "item" nebo "jiné".</span><span class="sxs-lookup"><span data-stu-id="b05e5-426">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="b05e5-427">Odinstaluje zdroj nebo šablony pack na `PATH` nebo `NUGET_ID` k dispozici.</span><span class="sxs-lookup"><span data-stu-id="b05e5-427">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="b05e5-428">Odinstalace pomocí zdroj `PATH`, budete potřebovat plně kvalifikovanou cestu.</span><span class="sxs-lookup"><span data-stu-id="b05e5-428">To uninstall a template using a source `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="b05e5-429">Například *C:/uživatele/\<uživatele > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z obsahuje složky nebudou.</span><span class="sxs-lookup"><span data-stu-id="b05e5-429">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span> <span data-ttu-id="b05e5-430">Kromě toho nesmí být znak konečné ukončující znak lomítka adresáře na cestu k šabloně.</span><span class="sxs-lookup"><span data-stu-id="b05e5-430">Additionally, do not include a final terminating directory slash on your template path.</span></span>
> 
> <span data-ttu-id="b05e5-431">Pokud se nemůžete určit `PATH` nebo `NUGET_ID` argumentů potřebných k odinstalaci šablonu s `dotnet new --uninstall` bez argumentu zobrazí seznam všech nainstalovaných šablon a argument nutné je odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="b05e5-431">If you are unable to determine the `PATH` or `NUGET_ID` argument needed to uninstall a template, running `dotnet new --uninstall` without an argument will list all installed templates and the argument required to uninstall them.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b05e5-432">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="b05e5-432">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="b05e5-433">Zobrazí všechny šablony pro konkrétní typ projektu při spuštění v kontextu `dotnet new` samotný příkaz.</span><span class="sxs-lookup"><span data-stu-id="b05e5-433">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="b05e5-434">Při spuštění v kontextu konkrétní šablony, jako například `dotnet new web -all`, `-all` je interpretován jako vytvoření příznak force.</span><span class="sxs-lookup"><span data-stu-id="b05e5-434">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="b05e5-435">To je potřeba při výstupní adresář již obsahuje projekt.</span><span class="sxs-lookup"><span data-stu-id="b05e5-435">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="b05e5-436">Vytiskne nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="b05e5-436">Prints out help for the command.</span></span> <span data-ttu-id="b05e5-437">Může být vyvolána pro `dotnet new` samotný příkaz nebo pro všechny šablony, jako například `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-437">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="b05e5-438">Zobrazí seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="b05e5-438">Lists templates containing the specified name.</span></span> <span data-ttu-id="b05e5-439">Pokud je vyvolána `dotnet new` příkazu, uvádí možné šablony, které jsou k dispozici pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="b05e5-439">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="b05e5-440">Například pokud adresář, projekt již obsahuje, neobsahuje všechny šablony projektů.</span><span class="sxs-lookup"><span data-stu-id="b05e5-440">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="b05e5-441">Jazyk šablony k vytvoření.</span><span class="sxs-lookup"><span data-stu-id="b05e5-441">The language of the template to create.</span></span> <span data-ttu-id="b05e5-442">Jazyk přijato, se liší podle šablony (Zobrazit výchozí hodnoty v [argumenty](#arguments) části).</span><span class="sxs-lookup"><span data-stu-id="b05e5-442">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="b05e5-443">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="b05e5-443">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="b05e5-444">Některé součásti pro interpretaci `#` jako speciální znak.</span><span class="sxs-lookup"><span data-stu-id="b05e5-444">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="b05e5-445">V takových případech bude nutné uvést hodnotu parametru jazyka, jako `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-445">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="b05e5-446">Název pro výstup vytvořený.</span><span class="sxs-lookup"><span data-stu-id="b05e5-446">The name for the created output.</span></span> <span data-ttu-id="b05e5-447">Pokud není zadán žádný název, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="b05e5-447">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="b05e5-448">Umístění pro vygenerovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="b05e5-448">Location to place the generated output.</span></span> <span data-ttu-id="b05e5-449">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="b05e5-449">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="b05e5-450">Nastavení šablony</span><span class="sxs-lookup"><span data-stu-id="b05e5-450">Template options</span></span>

<span data-ttu-id="b05e5-451">Každá šablona projektu může mít k dispozici další možnosti.</span><span class="sxs-lookup"><span data-stu-id="b05e5-451">Each project template may have additional options available.</span></span> <span data-ttu-id="b05e5-452">Základní šablony mají následující další možnosti:</span><span class="sxs-lookup"><span data-stu-id="b05e5-452">The core templates have the following additional options:</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="b05e5-453">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="b05e5-453">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="b05e5-454">**Konzoly**</span><span class="sxs-lookup"><span data-stu-id="b05e5-454">**console**</span></span>

<span data-ttu-id="b05e5-455">`--langVersion <VERSION_NUMBER>` -Nastaví `LangVersion` vlastností souboru vytvořeného projektu.</span><span class="sxs-lookup"><span data-stu-id="b05e5-455">`--langVersion <VERSION_NUMBER>` - Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="b05e5-456">Například použít `--langVersion 7.3` používat C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="b05e5-456">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="b05e5-457">Není podporováno pro F#.</span><span class="sxs-lookup"><span data-stu-id="b05e5-457">Not supported for F#.</span></span>

<span data-ttu-id="b05e5-458">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="b05e5-458">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b05e5-459">**angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="b05e5-459">**angular, react, reactredux**</span></span>

<span data-ttu-id="b05e5-460">`--exclude-launch-settings` -Vyloučení *launchSettings.json* z vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="b05e5-460">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="b05e5-461">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="b05e5-461">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b05e5-462">`--no-https` -Projektu nebude vyžadovat protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="b05e5-462">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="b05e5-463">Tato možnost platí, pouze pokud `IndividualAuth` nebo `OrganizationalAuth` nejsou používány.</span><span class="sxs-lookup"><span data-stu-id="b05e5-463">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="b05e5-464">**razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="b05e5-464">**razorclasslib**</span></span>

<span data-ttu-id="b05e5-465">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="b05e5-465">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b05e5-466">**classlib**</span><span class="sxs-lookup"><span data-stu-id="b05e5-466">**classlib**</span></span>

<span data-ttu-id="b05e5-467">`-f|--framework <FRAMEWORK>` : Určuje, že [framework](../../standard/frameworks.md) do cíle.</span><span class="sxs-lookup"><span data-stu-id="b05e5-467">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="b05e5-468">Hodnoty: `netcoreapp2.2` k vytvoření knihovny tříd .NET Core nebo `netstandard2.0` k vytvoření knihovny tříd .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="b05e5-468">Values: `netcoreapp2.2` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="b05e5-469">Výchozí hodnota je `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-469">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="b05e5-470">`--langVersion <VERSION_NUMBER>` -Nastaví `LangVersion` vlastností souboru vytvořeného projektu.</span><span class="sxs-lookup"><span data-stu-id="b05e5-470">`--langVersion <VERSION_NUMBER>` - Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="b05e5-471">Například použít `--langVersion 7.3` používat C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="b05e5-471">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="b05e5-472">Není podporováno pro F#.</span><span class="sxs-lookup"><span data-stu-id="b05e5-472">Not supported for F#.</span></span>

<span data-ttu-id="b05e5-473">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="b05e5-473">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b05e5-474">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="b05e5-474">**mstest, xunit**</span></span>

<span data-ttu-id="b05e5-475">`-p|--enable-pack` – Povolí balení pro projekt pomocí [balíčku dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="b05e5-475">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="b05e5-476">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="b05e5-476">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b05e5-477">**nunit**</span><span class="sxs-lookup"><span data-stu-id="b05e5-477">**nunit**</span></span>

<span data-ttu-id="b05e5-478">`-f|--framework <FRAMEWORK>` : Určuje, že [framework](../../standard/frameworks.md) do cíle.</span><span class="sxs-lookup"><span data-stu-id="b05e5-478">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="b05e5-479">Výchozí hodnota je `netcoreapp2.1`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-479">The default value is `netcoreapp2.1`.</span></span>

<span data-ttu-id="b05e5-480">`-p|--enable-pack` – Povolí balení pro projekt pomocí [balíčku dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="b05e5-480">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="b05e5-481">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="b05e5-481">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b05e5-482">**Stránka**</span><span class="sxs-lookup"><span data-stu-id="b05e5-482">**page**</span></span>

<span data-ttu-id="b05e5-483">`-na|--namespace <NAMESPACE_NAME>` -Namespace pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="b05e5-483">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="b05e5-484">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-484">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="b05e5-485">`-np|--no-pagemodel` -Vytvoří danou stránku bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="b05e5-485">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="b05e5-486">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="b05e5-486">**viewimports**</span></span>

<span data-ttu-id="b05e5-487">`-na|--namespace <NAMESPACE_NAME>` -Namespace pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="b05e5-487">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="b05e5-488">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-488">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="b05e5-489">**web**</span><span class="sxs-lookup"><span data-stu-id="b05e5-489">**web**</span></span>

<span data-ttu-id="b05e5-490">`--exclude-launch-settings` -Vyloučení *launchSettings.json* z vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="b05e5-490">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="b05e5-491">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="b05e5-491">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b05e5-492">`--no-https` -Projektu nebude vyžadovat protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="b05e5-492">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="b05e5-493">Tato možnost platí, pouze pokud `IndividualAuth` nebo `OrganizationalAuth` nejsou používány.</span><span class="sxs-lookup"><span data-stu-id="b05e5-493">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="b05e5-494">**mvc, webapp**</span><span class="sxs-lookup"><span data-stu-id="b05e5-494">**mvc, webapp**</span></span>

<span data-ttu-id="b05e5-495">`-au|--auth <AUTHENTICATION_TYPE>` -Typ ověřování, který má použít.</span><span class="sxs-lookup"><span data-stu-id="b05e5-495">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="b05e5-496">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="b05e5-496">The possible values are:</span></span>

- <span data-ttu-id="b05e5-497">`None` -Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="b05e5-497">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="b05e5-498">`Individual` -Jednotlivé ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-498">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="b05e5-499">`IndividualB2C` -Jednotlivé ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="b05e5-499">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="b05e5-500">`SingleOrg` – Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="b05e5-500">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="b05e5-501">`MultiOrg` – Ověřování organizace pro více tenantů.</span><span class="sxs-lookup"><span data-stu-id="b05e5-501">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="b05e5-502">`Windows` -Ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="b05e5-502">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="b05e5-503">`--aad-b2c-instance <INSTANCE>` -Instanci Azure Active Directory B2C pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="b05e5-503">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="b05e5-504">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-504">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="b05e5-505">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-505">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="b05e5-506">`-ssp|--susi-policy-id <ID>` – ID přihlášení a registraci zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="b05e5-506">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="b05e5-507">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-507">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b05e5-508">`-rp|--reset-password-policy-id <ID>` -Resetování hesla ID zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="b05e5-508">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="b05e5-509">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-509">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b05e5-510">`-ep|--edit-profile-policy-id <ID>` – Upravit profil zásady ID pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="b05e5-510">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="b05e5-511">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-511">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b05e5-512">`--aad-instance <INSTANCE>` – Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="b05e5-512">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="b05e5-513">Použití s `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-513">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="b05e5-514">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-514">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="b05e5-515">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="b05e5-515">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="b05e5-516">Použití s `IndividualB2C`, `SingleOrg`, nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-516">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="b05e5-517">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-517">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="b05e5-518">`--domain <DOMAIN>` -Domény tenantu Active directory.</span><span class="sxs-lookup"><span data-stu-id="b05e5-518">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="b05e5-519">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-519">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="b05e5-520">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-520">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="b05e5-521">`--tenant-id <ID>` – ID Tenanta ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="b05e5-521">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="b05e5-522">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-522">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="b05e5-523">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-523">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="b05e5-524">`--callback-path <PATH>` -Cestu požadavku v rámci základní cesty aplikace identifikátoru URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-524">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="b05e5-525">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-525">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="b05e5-526">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-526">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="b05e5-527">`-r|--org-read-access` – Povolí této aplikaci přístup pro čtení do adresáře.</span><span class="sxs-lookup"><span data-stu-id="b05e5-527">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="b05e5-528">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-528">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="b05e5-529">`--exclude-launch-settings` -Vyloučení *launchSettings.json* z vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="b05e5-529">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="b05e5-530">`--no-https` -Projektu nebude vyžadovat protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="b05e5-530">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="b05e5-531">`app.UseHsts` a `app.UseHttpsRedirection` nejsou přidány do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-531">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="b05e5-532">Tato možnost platí, pouze pokud `Individual`, `IndividualB2C`, `SingleOrg`, nebo `MultiOrg` nejsou používány.</span><span class="sxs-lookup"><span data-stu-id="b05e5-532">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="b05e5-533">`-uld|--use-local-db` : Určuje, že by měl být LocalDB použít místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="b05e5-533">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="b05e5-534">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-534">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b05e5-535">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="b05e5-535">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b05e5-536">**webapi**</span><span class="sxs-lookup"><span data-stu-id="b05e5-536">**webapi**</span></span>

<span data-ttu-id="b05e5-537">`-au|--auth <AUTHENTICATION_TYPE>` -Typ ověřování, který má použít.</span><span class="sxs-lookup"><span data-stu-id="b05e5-537">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="b05e5-538">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="b05e5-538">The possible values are:</span></span>

- <span data-ttu-id="b05e5-539">`None` -Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="b05e5-539">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="b05e5-540">`IndividualB2C` -Jednotlivé ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="b05e5-540">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="b05e5-541">`SingleOrg` – Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="b05e5-541">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="b05e5-542">`Windows` -Ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="b05e5-542">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="b05e5-543">`--aad-b2c-instance <INSTANCE>` -Instanci Azure Active Directory B2C pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="b05e5-543">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="b05e5-544">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-544">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="b05e5-545">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-545">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="b05e5-546">`-ssp|--susi-policy-id <ID>` – ID přihlášení a registraci zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="b05e5-546">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="b05e5-547">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-547">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b05e5-548">`--aad-instance <INSTANCE>` – Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="b05e5-548">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="b05e5-549">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-549">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="b05e5-550">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-550">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="b05e5-551">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="b05e5-551">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="b05e5-552">Použití s `IndividualB2C` nebo `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-552">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="b05e5-553">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-553">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="b05e5-554">`--domain <DOMAIN>` -Domény tenantu Active directory.</span><span class="sxs-lookup"><span data-stu-id="b05e5-554">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="b05e5-555">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-555">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="b05e5-556">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-556">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="b05e5-557">`--tenant-id <ID>` – ID Tenanta ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="b05e5-557">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="b05e5-558">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-558">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="b05e5-559">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-559">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="b05e5-560">`-r|--org-read-access` – Povolí této aplikaci přístup pro čtení do adresáře.</span><span class="sxs-lookup"><span data-stu-id="b05e5-560">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="b05e5-561">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-561">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="b05e5-562">`--exclude-launch-settings` -Vyloučení *launchSettings.json* z vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="b05e5-562">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="b05e5-563">`--no-https` -Projektu nebude vyžadovat protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="b05e5-563">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="b05e5-564">`app.UseHsts` a `app.UseHttpsRedirection` nejsou přidány do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-564">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="b05e5-565">Tato možnost platí, pouze pokud `Individual`, `IndividualB2C`, `SingleOrg`, nebo `MultiOrg` nejsou používány.</span><span class="sxs-lookup"><span data-stu-id="b05e5-565">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="b05e5-566">`-uld|--use-local-db` : Určuje, že by měl být LocalDB použít místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="b05e5-566">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="b05e5-567">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-567">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b05e5-568">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="b05e5-568">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b05e5-569">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="b05e5-569">**globaljson**</span></span>

<span data-ttu-id="b05e5-570">`--sdk-version <VERSION_NUMBER>` : Určuje verzi .NET Core SDK pro použití v *global.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="b05e5-570">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="b05e5-571">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="b05e5-571">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="b05e5-572">**console, angular, react, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="b05e5-572">**console, angular, react, reactredux, razorclasslib**</span></span>

<span data-ttu-id="b05e5-573">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="b05e5-573">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b05e5-574">**classlib**</span><span class="sxs-lookup"><span data-stu-id="b05e5-574">**classlib**</span></span>

<span data-ttu-id="b05e5-575">`-f|--framework <FRAMEWORK>` : Určuje, že [framework](../../standard/frameworks.md) do cíle.</span><span class="sxs-lookup"><span data-stu-id="b05e5-575">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="b05e5-576">Hodnoty: `netcoreapp2.1` k vytvoření knihovny tříd .NET Core nebo `netstandard2.0` k vytvoření knihovny tříd .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="b05e5-576">Values: `netcoreapp2.1` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="b05e5-577">Výchozí hodnota je `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-577">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="b05e5-578">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="b05e5-578">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b05e5-579">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="b05e5-579">**mstest, xunit**</span></span>

<span data-ttu-id="b05e5-580">`-p|--enable-pack` – Povolí balení pro projekt pomocí [balíčku dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="b05e5-580">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="b05e5-581">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="b05e5-581">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b05e5-582">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="b05e5-582">**globaljson**</span></span>

<span data-ttu-id="b05e5-583">`--sdk-version <VERSION_NUMBER>` : Určuje verzi .NET Core SDK pro použití v *global.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="b05e5-583">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="b05e5-584">**web**</span><span class="sxs-lookup"><span data-stu-id="b05e5-584">**web**</span></span>

<span data-ttu-id="b05e5-585">`--exclude-launch-settings` -Vyloučení *launchSettings.json* z vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="b05e5-585">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="b05e5-586">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="b05e5-586">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b05e5-587">`--no-https` -Projektu nebude vyžadovat protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="b05e5-587">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="b05e5-588">Tato možnost platí, pouze pokud `IndividualAuth` nebo `OrganizationalAuth` nejsou používány.</span><span class="sxs-lookup"><span data-stu-id="b05e5-588">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="b05e5-589">**webapi**</span><span class="sxs-lookup"><span data-stu-id="b05e5-589">**webapi**</span></span>

<span data-ttu-id="b05e5-590">`-au|--auth <AUTHENTICATION_TYPE>` -Typ ověřování, který má použít.</span><span class="sxs-lookup"><span data-stu-id="b05e5-590">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="b05e5-591">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="b05e5-591">The possible values are:</span></span>

- <span data-ttu-id="b05e5-592">`None` -Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="b05e5-592">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="b05e5-593">`IndividualB2C` -Jednotlivé ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="b05e5-593">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="b05e5-594">`SingleOrg` – Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="b05e5-594">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="b05e5-595">`Windows` -Ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="b05e5-595">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="b05e5-596">`--aad-b2c-instance <INSTANCE>` -Instanci Azure Active Directory B2C pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="b05e5-596">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="b05e5-597">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-597">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="b05e5-598">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-598">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="b05e5-599">`-ssp|--susi-policy-id <ID>` – ID přihlášení a registraci zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="b05e5-599">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="b05e5-600">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-600">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b05e5-601">`--aad-instance <INSTANCE>` – Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="b05e5-601">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="b05e5-602">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-602">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="b05e5-603">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-603">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="b05e5-604">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="b05e5-604">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="b05e5-605">Použití s `IndividualB2C` nebo `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-605">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="b05e5-606">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-606">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="b05e5-607">`--domain <DOMAIN>` -Domény tenantu Active directory.</span><span class="sxs-lookup"><span data-stu-id="b05e5-607">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="b05e5-608">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-608">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="b05e5-609">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-609">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="b05e5-610">`--tenant-id <ID>` – ID Tenanta ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="b05e5-610">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="b05e5-611">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-611">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="b05e5-612">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-612">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="b05e5-613">`-r|--org-read-access` – Povolí této aplikaci přístup pro čtení do adresáře.</span><span class="sxs-lookup"><span data-stu-id="b05e5-613">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="b05e5-614">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-614">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="b05e5-615">`--exclude-launch-settings` -Vyloučení *launchSettings.json* z vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="b05e5-615">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="b05e5-616">`-uld|--use-local-db` : Určuje, že by měl být LocalDB použít místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="b05e5-616">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="b05e5-617">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-617">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b05e5-618">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="b05e5-618">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b05e5-619">`--no-https` -Projektu nebude vyžadovat protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="b05e5-619">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="b05e5-620">`app.UseHsts` a `app.UseHttpsRedirection` nejsou přidány do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-620">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="b05e5-621">Tato možnost platí, pouze pokud `Individual`, `IndividualB2C`, `SingleOrg`, nebo `MultiOrg` nejsou používány.</span><span class="sxs-lookup"><span data-stu-id="b05e5-621">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="b05e5-622">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="b05e5-622">**mvc, razor**</span></span>

<span data-ttu-id="b05e5-623">`-au|--auth <AUTHENTICATION_TYPE>` -Typ ověřování, který má použít.</span><span class="sxs-lookup"><span data-stu-id="b05e5-623">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="b05e5-624">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="b05e5-624">The possible values are:</span></span>

- <span data-ttu-id="b05e5-625">`None` -Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="b05e5-625">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="b05e5-626">`Individual` -Jednotlivé ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-626">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="b05e5-627">`IndividualB2C` -Jednotlivé ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="b05e5-627">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="b05e5-628">`SingleOrg` – Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="b05e5-628">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="b05e5-629">`MultiOrg` – Ověřování organizace pro více tenantů.</span><span class="sxs-lookup"><span data-stu-id="b05e5-629">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="b05e5-630">`Windows` -Ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="b05e5-630">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="b05e5-631">`--aad-b2c-instance <INSTANCE>` -Instanci Azure Active Directory B2C pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="b05e5-631">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="b05e5-632">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-632">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="b05e5-633">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-633">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="b05e5-634">`-ssp|--susi-policy-id <ID>` – ID přihlášení a registraci zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="b05e5-634">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="b05e5-635">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-635">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b05e5-636">`-rp|--reset-password-policy-id <ID>` -Resetování hesla ID zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="b05e5-636">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="b05e5-637">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-637">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b05e5-638">`-ep|--edit-profile-policy-id <ID>` – Upravit profil zásady ID pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="b05e5-638">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="b05e5-639">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-639">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b05e5-640">`--aad-instance <INSTANCE>` – Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="b05e5-640">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="b05e5-641">Použití s `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-641">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="b05e5-642">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-642">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="b05e5-643">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="b05e5-643">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="b05e5-644">Použití s `IndividualB2C`, `SingleOrg`, nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-644">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="b05e5-645">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-645">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="b05e5-646">`--domain <DOMAIN>` -Domény tenantu Active directory.</span><span class="sxs-lookup"><span data-stu-id="b05e5-646">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="b05e5-647">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-647">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="b05e5-648">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-648">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="b05e5-649">`--tenant-id <ID>` – ID Tenanta ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="b05e5-649">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="b05e5-650">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-650">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="b05e5-651">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-651">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="b05e5-652">`--callback-path <PATH>` -Cestu požadavku v rámci základní cesty aplikace identifikátoru URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-652">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="b05e5-653">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-653">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="b05e5-654">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-654">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="b05e5-655">`-r|--org-read-access` – Povolí této aplikaci přístup pro čtení do adresáře.</span><span class="sxs-lookup"><span data-stu-id="b05e5-655">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="b05e5-656">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-656">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="b05e5-657">`--exclude-launch-settings` -Vyloučení *launchSettings.json* z vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="b05e5-657">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="b05e5-658">`--use-browserlink` -Obsahuje BrowserLink v projektu.</span><span class="sxs-lookup"><span data-stu-id="b05e5-658">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="b05e5-659">`-uld|--use-local-db` : Určuje, že by měl být LocalDB použít místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="b05e5-659">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="b05e5-660">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-660">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b05e5-661">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="b05e5-661">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b05e5-662">`--no-https` -Projektu nebude vyžadovat protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="b05e5-662">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="b05e5-663">`app.UseHsts` a `app.UseHttpsRedirection` nejsou přidány do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-663">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="b05e5-664">Tato možnost platí, pouze pokud `Individual`, `IndividualB2C`, `SingleOrg`, nebo `MultiOrg` nejsou používány.</span><span class="sxs-lookup"><span data-stu-id="b05e5-664">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="b05e5-665">**Stránka**</span><span class="sxs-lookup"><span data-stu-id="b05e5-665">**page**</span></span>

<span data-ttu-id="b05e5-666">`-na|--namespace <NAMESPACE_NAME>` -Namespace pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="b05e5-666">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="b05e5-667">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-667">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="b05e5-668">`-np|--no-pagemodel` -Vytvoří danou stránku bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="b05e5-668">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="b05e5-669">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="b05e5-669">**viewimports**</span></span>

<span data-ttu-id="b05e5-670">`-na|--namespace <NAMESPACE_NAME>` -Namespace pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="b05e5-670">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="b05e5-671">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-671">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="b05e5-672">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="b05e5-672">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="b05e5-673">**konzola, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="b05e5-673">**console, angular, react, reactredux**</span></span>

<span data-ttu-id="b05e5-674">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="b05e5-674">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b05e5-675">**classlib**</span><span class="sxs-lookup"><span data-stu-id="b05e5-675">**classlib**</span></span>

<span data-ttu-id="b05e5-676">`-f|--framework <FRAMEWORK>` : Určuje, že [framework](../../standard/frameworks.md) do cíle.</span><span class="sxs-lookup"><span data-stu-id="b05e5-676">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="b05e5-677">Hodnoty: `netcoreapp2.0` k vytvoření knihovny tříd .NET Core nebo `netstandard2.0` k vytvoření knihovny tříd .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="b05e5-677">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="b05e5-678">Výchozí hodnota je `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-678">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="b05e5-679">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="b05e5-679">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b05e5-680">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="b05e5-680">**mstest, xunit**</span></span>

<span data-ttu-id="b05e5-681">`-p|--enable-pack` – Povolí balení pro projekt pomocí [balíčku dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="b05e5-681">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="b05e5-682">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="b05e5-682">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b05e5-683">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="b05e5-683">**globaljson**</span></span>

<span data-ttu-id="b05e5-684">`--sdk-version <VERSION_NUMBER>` : Určuje verzi .NET Core SDK pro použití v *global.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="b05e5-684">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="b05e5-685">**web**</span><span class="sxs-lookup"><span data-stu-id="b05e5-685">**web**</span></span>

<span data-ttu-id="b05e5-686">`--use-launch-settings` -Zahrnuje *launchSettings.json* ve výstupu vygenerovanou šablonu.</span><span class="sxs-lookup"><span data-stu-id="b05e5-686">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="b05e5-687">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="b05e5-687">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b05e5-688">**webapi**</span><span class="sxs-lookup"><span data-stu-id="b05e5-688">**webapi**</span></span>

<span data-ttu-id="b05e5-689">`-au|--auth <AUTHENTICATION_TYPE>` -Typ ověřování, který má použít.</span><span class="sxs-lookup"><span data-stu-id="b05e5-689">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="b05e5-690">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="b05e5-690">The possible values are:</span></span>

- <span data-ttu-id="b05e5-691">`None` -Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="b05e5-691">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="b05e5-692">`IndividualB2C` -Jednotlivé ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="b05e5-692">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="b05e5-693">`SingleOrg` – Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="b05e5-693">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="b05e5-694">`Windows` -Ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="b05e5-694">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="b05e5-695">`--aad-b2c-instance <INSTANCE>` -Instanci Azure Active Directory B2C pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="b05e5-695">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="b05e5-696">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-696">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="b05e5-697">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-697">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="b05e5-698">`-ssp|--susi-policy-id <ID>` – ID přihlášení a registraci zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="b05e5-698">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="b05e5-699">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-699">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b05e5-700">`--aad-instance <INSTANCE>` – Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="b05e5-700">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="b05e5-701">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-701">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="b05e5-702">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-702">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="b05e5-703">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="b05e5-703">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="b05e5-704">Použití s `IndividualB2C` nebo `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-704">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="b05e5-705">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-705">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="b05e5-706">`--domain <DOMAIN>` -Domény tenantu Active directory.</span><span class="sxs-lookup"><span data-stu-id="b05e5-706">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="b05e5-707">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-707">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="b05e5-708">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-708">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="b05e5-709">`--tenant-id <ID>` – ID Tenanta ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="b05e5-709">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="b05e5-710">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-710">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="b05e5-711">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-711">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="b05e5-712">`-r|--org-read-access` – Povolí této aplikaci přístup pro čtení do adresáře.</span><span class="sxs-lookup"><span data-stu-id="b05e5-712">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="b05e5-713">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-713">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="b05e5-714">`--use-launch-settings` -Zahrnuje *launchSettings.json* ve výstupu vygenerovanou šablonu.</span><span class="sxs-lookup"><span data-stu-id="b05e5-714">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="b05e5-715">`-uld|--use-local-db` : Určuje, že by měl být LocalDB použít místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="b05e5-715">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="b05e5-716">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-716">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b05e5-717">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="b05e5-717">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b05e5-718">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="b05e5-718">**mvc, razor**</span></span>

<span data-ttu-id="b05e5-719">`-au|--auth <AUTHENTICATION_TYPE>` -Typ ověřování, který má použít.</span><span class="sxs-lookup"><span data-stu-id="b05e5-719">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="b05e5-720">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="b05e5-720">The possible values are:</span></span>

- <span data-ttu-id="b05e5-721">`None` -Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="b05e5-721">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="b05e5-722">`Individual` -Jednotlivé ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-722">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="b05e5-723">`IndividualB2C` -Jednotlivé ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="b05e5-723">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="b05e5-724">`SingleOrg` – Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="b05e5-724">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="b05e5-725">`MultiOrg` – Ověřování organizace pro více tenantů.</span><span class="sxs-lookup"><span data-stu-id="b05e5-725">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="b05e5-726">`Windows` -Ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="b05e5-726">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="b05e5-727">`--aad-b2c-instance <INSTANCE>` -Instanci Azure Active Directory B2C pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="b05e5-727">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="b05e5-728">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-728">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="b05e5-729">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-729">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="b05e5-730">`-ssp|--susi-policy-id <ID>` – ID přihlášení a registraci zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="b05e5-730">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="b05e5-731">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-731">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b05e5-732">`-rp|--reset-password-policy-id <ID>` -Resetování hesla ID zásady pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="b05e5-732">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="b05e5-733">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-733">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b05e5-734">`-ep|--edit-profile-policy-id <ID>` – Upravit profil zásady ID pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="b05e5-734">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="b05e5-735">Použití s `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-735">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b05e5-736">`--aad-instance <INSTANCE>` – Instance služby Azure Active Directory pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="b05e5-736">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="b05e5-737">Použití s `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-737">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="b05e5-738">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-738">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="b05e5-739">`--client-id <ID>` – ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="b05e5-739">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="b05e5-740">Použití s `IndividualB2C`, `SingleOrg`, nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-740">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="b05e5-741">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-741">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="b05e5-742">`--domain <DOMAIN>` -Domény tenantu Active directory.</span><span class="sxs-lookup"><span data-stu-id="b05e5-742">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="b05e5-743">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-743">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="b05e5-744">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-744">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="b05e5-745">`--tenant-id <ID>` – ID Tenanta ID adresáře pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="b05e5-745">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="b05e5-746">Použití s `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-746">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="b05e5-747">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-747">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="b05e5-748">`--callback-path <PATH>` -Cestu požadavku v rámci základní cesty aplikace identifikátoru URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-748">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="b05e5-749">Použití s `SingleOrg` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-749">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="b05e5-750">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-750">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="b05e5-751">`-r|--org-read-access` – Povolí této aplikaci přístup pro čtení do adresáře.</span><span class="sxs-lookup"><span data-stu-id="b05e5-751">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="b05e5-752">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-752">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="b05e5-753">`--use-launch-settings` -Zahrnuje *launchSettings.json* ve výstupu vygenerovanou šablonu.</span><span class="sxs-lookup"><span data-stu-id="b05e5-753">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="b05e5-754">`--use-browserlink` -Obsahuje BrowserLink v projektu.</span><span class="sxs-lookup"><span data-stu-id="b05e5-754">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="b05e5-755">`-uld|--use-local-db` : Určuje, že by měl být LocalDB použít místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="b05e5-755">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="b05e5-756">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="b05e5-756">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="b05e5-757">`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="b05e5-757">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="b05e5-758">**Stránka**</span><span class="sxs-lookup"><span data-stu-id="b05e5-758">**page**</span></span>

<span data-ttu-id="b05e5-759">`-na|--namespace <NAMESPACE_NAME>`-Namespace pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="b05e5-759">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="b05e5-760">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-760">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="b05e5-761">`-np|--no-pagemodel` -Vytvoří danou stránku bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="b05e5-761">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="b05e5-762">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="b05e5-762">**viewimports**</span></span>

<span data-ttu-id="b05e5-763">`-na|--namespace <NAMESPACE_NAME>`-Namespace pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="b05e5-763">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="b05e5-764">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-764">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b05e5-765">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="b05e5-765">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="b05e5-766">**konzola, xunit, mstest, web, webapi**</span><span class="sxs-lookup"><span data-stu-id="b05e5-766">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="b05e5-767">`-f|--framework <FRAMEWORK>` : Určuje, že [framework](../../standard/frameworks.md) do cíle.</span><span class="sxs-lookup"><span data-stu-id="b05e5-767">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="b05e5-768">Hodnoty: `netcoreapp1.0` nebo `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-768">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="b05e5-769">Výchozí hodnota je `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-769">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="b05e5-770">**classlib**</span><span class="sxs-lookup"><span data-stu-id="b05e5-770">**classlib**</span></span>

<span data-ttu-id="b05e5-771">`-f|--framework <FRAMEWORK>` : Určuje, že [framework](../../standard/frameworks.md) do cíle.</span><span class="sxs-lookup"><span data-stu-id="b05e5-771">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="b05e5-772">Hodnoty: `netcoreapp1.0`, `netcoreapp1.1`, nebo `netstandard1.0` k `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-772">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="b05e5-773">Výchozí hodnota je `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-773">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="b05e5-774">**mvc**</span><span class="sxs-lookup"><span data-stu-id="b05e5-774">**mvc**</span></span>

<span data-ttu-id="b05e5-775">`-f|--framework <FRAMEWORK>` : Určuje, že [framework](../../standard/frameworks.md) do cíle.</span><span class="sxs-lookup"><span data-stu-id="b05e5-775">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="b05e5-776">Hodnoty: `netcoreapp1.0` nebo `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-776">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="b05e5-777">Výchozí hodnota je `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-777">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="b05e5-778">`-au|--auth <AUTHENTICATION_TYPE>` -Typ ověřování, který má použít.</span><span class="sxs-lookup"><span data-stu-id="b05e5-778">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="b05e5-779">Hodnoty: `None` nebo `Individual`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-779">Values: `None` or `Individual`.</span></span> <span data-ttu-id="b05e5-780">Výchozí hodnota je `None`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-780">The default value is `None`.</span></span>

<span data-ttu-id="b05e5-781">`-uld|--use-local-db` : Určuje, jestli se mají použít databázi LocalDB místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="b05e5-781">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="b05e5-782">Hodnoty: `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-782">Values: `true` or `false`.</span></span> <span data-ttu-id="b05e5-783">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="b05e5-783">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="b05e5-784">Příklady</span><span class="sxs-lookup"><span data-stu-id="b05e5-784">Examples</span></span>

<span data-ttu-id="b05e5-785">Vytvoření C# projekt konzolové aplikace tak, že zadáte název šablony:</span><span class="sxs-lookup"><span data-stu-id="b05e5-785">Create a C# console application project by specifying the template name:</span></span>

`dotnet new "Console Application"`

<span data-ttu-id="b05e5-786">Vytvoření F# projekt konzolové aplikace v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="b05e5-786">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="b05e5-787">Vytvořte projekt knihovny tříd .NET Standard v zadaném adresáři (k dispozici pouze s .NET Core SDK 2.0 a novějšími verzemi):</span><span class="sxs-lookup"><span data-stu-id="b05e5-787">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="b05e5-788">Vytvořit nový ASP.NET Core C# projektů MVC v aktuálním adresáři bez ověřování:</span><span class="sxs-lookup"><span data-stu-id="b05e5-788">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="b05e5-789">Vytvoření nového projektu s použitím xUnit:</span><span class="sxs-lookup"><span data-stu-id="b05e5-789">Create a new xUnit project:</span></span>

`dotnet new xunit`

<span data-ttu-id="b05e5-790">Seznam všech šablon, které jsou k dispozici pro rozhraní MVC:</span><span class="sxs-lookup"><span data-stu-id="b05e5-790">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="b05e5-791">Seznam všech šablon odpovídající *jsme* dílčí řetězec.</span><span class="sxs-lookup"><span data-stu-id="b05e5-791">List all templates matching the *we* substring.</span></span> <span data-ttu-id="b05e5-792">Žádná shoda nenajde, takže odpovídající podřetězec bude možné spustit proti krátký název i název sloupce.</span><span class="sxs-lookup"><span data-stu-id="b05e5-792">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

`dotnet new we -l`

<span data-ttu-id="b05e5-793">Pokus o vyvolání šablony odpovídající *ng*.</span><span class="sxs-lookup"><span data-stu-id="b05e5-793">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="b05e5-794">Pokud nelze určit jediný výskyt shody, seznam šablon, které jsou částečné shody.</span><span class="sxs-lookup"><span data-stu-id="b05e5-794">If a single match can't be determined, list the templates that are partial matches.</span></span>

`dotnet new ng`

<span data-ttu-id="b05e5-795">Instalace verze 2.0 šablon jednostránkové aplikace ASP.NET Core (příkaz Možnosti dostupné pro .NET Core SDK 1.1 a novějších verzích pouze):</span><span class="sxs-lookup"><span data-stu-id="b05e5-795">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="b05e5-796">Vytvoření *global.json* v aktuálním adresáři nastavení sady SDK verze 2.0.0 (k dispozici pouze s .NET Core SDK 2.0 a novějšími verzemi):</span><span class="sxs-lookup"><span data-stu-id="b05e5-796">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="b05e5-797">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b05e5-797">See also</span></span>

- [<span data-ttu-id="b05e5-798">Vlastních šablon pro dotnet nové</span><span class="sxs-lookup"><span data-stu-id="b05e5-798">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="b05e5-799">Vytvoření vlastní šablony pro dotnet new</span><span class="sxs-lookup"><span data-stu-id="b05e5-799">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)
- [<span data-ttu-id="b05e5-800">úložiště GitHub DotNet/dotnet – šablony – ukázky</span><span class="sxs-lookup"><span data-stu-id="b05e5-800">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="b05e5-801">Dostupné šablony pro dotnet nové</span><span class="sxs-lookup"><span data-stu-id="b05e5-801">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
