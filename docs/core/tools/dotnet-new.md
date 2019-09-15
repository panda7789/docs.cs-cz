---
title: dotnet – nový příkaz
description: Příkaz dotnet New vytvoří nové projekty .NET Core založené na zadané šabloně.
ms.date: 05/06/2019
ms.openlocfilehash: 57b198d13984fb4585e1df6303afe481e7e0552d
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969741"
---
# <a name="dotnet-new"></a><span data-ttu-id="9a92c-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="9a92c-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="9a92c-104">Name</span><span class="sxs-lookup"><span data-stu-id="9a92c-104">Name</span></span>

<span data-ttu-id="9a92c-105">`dotnet new`– Vytvoří nový projekt, konfigurační soubor nebo řešení na základě zadané šablony.</span><span class="sxs-lookup"><span data-stu-id="9a92c-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9a92c-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="9a92c-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="9a92c-107">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="9a92c-107">.NET Core 2.2</span></span>](#tab/netcore22)

```console
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="9a92c-108">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="9a92c-108">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="9a92c-109">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="9a92c-109">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="9a92c-110">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="9a92c-110">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="9a92c-111">Popis</span><span class="sxs-lookup"><span data-stu-id="9a92c-111">Description</span></span>

<span data-ttu-id="9a92c-112">`dotnet new` Příkaz nabízí pohodlný způsob, jak inicializovat platný projekt .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9a92c-112">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="9a92c-113">Příkaz volá [modul šablony](https://github.com/dotnet/templating) a vytvoří artefakty na disku na základě zadané šablony a možností.</span><span class="sxs-lookup"><span data-stu-id="9a92c-113">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="9a92c-114">Arguments</span><span class="sxs-lookup"><span data-stu-id="9a92c-114">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="9a92c-115">Šablona, která se má vytvořit při vyvolání příkazu</span><span class="sxs-lookup"><span data-stu-id="9a92c-115">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="9a92c-116">Každá šablona může mít konkrétní možnosti, které můžete předat.</span><span class="sxs-lookup"><span data-stu-id="9a92c-116">Each template might have specific options you can pass.</span></span> <span data-ttu-id="9a92c-117">Další informace najdete v tématu [Možnosti šablony](#template-options).</span><span class="sxs-lookup"><span data-stu-id="9a92c-117">For more information, see [Template options](#template-options).</span></span>

<span data-ttu-id="9a92c-118">Pokud hodnota není přesná shoda na textu v **šablonách** nebo ve sloupci **short name** , je v těchto dvou sloupcích provedena shoda podřetězce. `TEMPLATE`</span><span class="sxs-lookup"><span data-stu-id="9a92c-118">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column, a substring match is performed on those two columns.</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="9a92c-119">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="9a92c-119">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="9a92c-120">Příkaz obsahuje výchozí seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="9a92c-120">The command contains a default list of templates.</span></span> <span data-ttu-id="9a92c-121">Použijte `dotnet new -l` k získání seznamu dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="9a92c-121">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="9a92c-122">Následující tabulka obsahuje šablony, které jsou předinstalované s .NET Core SDK 2.2.100.</span><span class="sxs-lookup"><span data-stu-id="9a92c-122">The following table shows the templates that come pre-installed with the .NET Core SDK 2.2.100.</span></span> <span data-ttu-id="9a92c-123">Výchozí jazyk pro šablonu se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="9a92c-123">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="9a92c-124">Šablony</span><span class="sxs-lookup"><span data-stu-id="9a92c-124">Templates</span></span>                                    | <span data-ttu-id="9a92c-125">Krátký název</span><span class="sxs-lookup"><span data-stu-id="9a92c-125">Short Name</span></span>        | <span data-ttu-id="9a92c-126">Jazyk</span><span class="sxs-lookup"><span data-stu-id="9a92c-126">Language</span></span>     | <span data-ttu-id="9a92c-127">Značky</span><span class="sxs-lookup"><span data-stu-id="9a92c-127">Tags</span></span>                                  |
|----------------------------------------------|-------------------|--------------|---------------------------------------|
| <span data-ttu-id="9a92c-128">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="9a92c-128">Console Application</span></span>                          | `console`         | <span data-ttu-id="9a92c-129">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="9a92c-129">[C#], F#, VB</span></span> | <span data-ttu-id="9a92c-130">Společná/konzola</span><span class="sxs-lookup"><span data-stu-id="9a92c-130">Common/Console</span></span>                        |
| <span data-ttu-id="9a92c-131">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="9a92c-131">Class library</span></span>                                | `classlib`        | <span data-ttu-id="9a92c-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="9a92c-132">[C#], F#, VB</span></span> | <span data-ttu-id="9a92c-133">Společné/knihovny</span><span class="sxs-lookup"><span data-stu-id="9a92c-133">Common/Library</span></span>                        |
| <span data-ttu-id="9a92c-134">Projekt testu jednotek</span><span class="sxs-lookup"><span data-stu-id="9a92c-134">Unit Test Project</span></span>                            | `mstest`          | <span data-ttu-id="9a92c-135">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="9a92c-135">[C#], F#, VB</span></span> | <span data-ttu-id="9a92c-136">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="9a92c-136">Test/MSTest</span></span>                           |
| <span data-ttu-id="9a92c-137">Projekt testů NUnit 3</span><span class="sxs-lookup"><span data-stu-id="9a92c-137">NUnit 3 Test Project</span></span>                         | `nunit`           | <span data-ttu-id="9a92c-138">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="9a92c-138">[C#], F#, VB</span></span> | <span data-ttu-id="9a92c-139">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="9a92c-139">Test/NUnit</span></span>                            |
| <span data-ttu-id="9a92c-140">NUnit 3 položka testu</span><span class="sxs-lookup"><span data-stu-id="9a92c-140">NUnit 3 Test Item</span></span>                            | `nunit-test`      | <span data-ttu-id="9a92c-141">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="9a92c-141">[C#], F#, VB</span></span> | <span data-ttu-id="9a92c-142">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="9a92c-142">Test/NUnit</span></span>                            |
| <span data-ttu-id="9a92c-143">Projekt testů xUnit</span><span class="sxs-lookup"><span data-stu-id="9a92c-143">xUnit Test Project</span></span>                           | `xunit`           | <span data-ttu-id="9a92c-144">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="9a92c-144">[C#], F#, VB</span></span> | <span data-ttu-id="9a92c-145">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="9a92c-145">Test/xUnit</span></span>                            |
| <span data-ttu-id="9a92c-146">Stránka Razor</span><span class="sxs-lookup"><span data-stu-id="9a92c-146">Razor Page</span></span>                                   | `page`            | <span data-ttu-id="9a92c-147">[C#]</span><span class="sxs-lookup"><span data-stu-id="9a92c-147">[C#]</span></span>         | <span data-ttu-id="9a92c-148">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="9a92c-148">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="9a92c-149">ViewImports MVC</span><span class="sxs-lookup"><span data-stu-id="9a92c-149">MVC ViewImports</span></span>                              | `viewimports`     | <span data-ttu-id="9a92c-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="9a92c-150">[C#]</span></span>         | <span data-ttu-id="9a92c-151">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="9a92c-151">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="9a92c-152">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="9a92c-152">MVC ViewStart</span></span>                                | `viewstart`       | <span data-ttu-id="9a92c-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="9a92c-153">[C#]</span></span>         | <span data-ttu-id="9a92c-154">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="9a92c-154">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="9a92c-155">ASP.NET Core prázdné</span><span class="sxs-lookup"><span data-stu-id="9a92c-155">ASP.NET Core Empty</span></span>                           | `web`             | <span data-ttu-id="9a92c-156">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="9a92c-156">[C#], F#</span></span>     | <span data-ttu-id="9a92c-157">Web/prázdné</span><span class="sxs-lookup"><span data-stu-id="9a92c-157">Web/Empty</span></span>                             |
| <span data-ttu-id="9a92c-158">ASP.NET Core webová aplikace (model-zobrazení-kontroler)</span><span class="sxs-lookup"><span data-stu-id="9a92c-158">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`             | <span data-ttu-id="9a92c-159">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="9a92c-159">[C#], F#</span></span>     | <span data-ttu-id="9a92c-160">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="9a92c-160">Web/MVC</span></span>                               |
| <span data-ttu-id="9a92c-161">ASP.NET Core webové aplikace</span><span class="sxs-lookup"><span data-stu-id="9a92c-161">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="9a92c-162">`webapp`, `razor`</span><span class="sxs-lookup"><span data-stu-id="9a92c-162">`webapp`, `razor`</span></span> | <span data-ttu-id="9a92c-163">[C#]</span><span class="sxs-lookup"><span data-stu-id="9a92c-163">[C#]</span></span>         | <span data-ttu-id="9a92c-164">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="9a92c-164">Web/MVC/Razor Pages</span></span>                   |
| <span data-ttu-id="9a92c-165">ASP.NET Core s úhlovým</span><span class="sxs-lookup"><span data-stu-id="9a92c-165">ASP.NET Core with Angular</span></span>                    | `angular`         | <span data-ttu-id="9a92c-166">[C#]</span><span class="sxs-lookup"><span data-stu-id="9a92c-166">[C#]</span></span>         | <span data-ttu-id="9a92c-167">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="9a92c-167">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="9a92c-168">ASP.NET Core s reagují. js</span><span class="sxs-lookup"><span data-stu-id="9a92c-168">ASP.NET Core with React.js</span></span>                   | `react`           | <span data-ttu-id="9a92c-169">[C#]</span><span class="sxs-lookup"><span data-stu-id="9a92c-169">[C#]</span></span>         | <span data-ttu-id="9a92c-170">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="9a92c-170">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="9a92c-171">ASP.NET Core s využitím reagují. js a Redux</span><span class="sxs-lookup"><span data-stu-id="9a92c-171">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`      | <span data-ttu-id="9a92c-172">[C#]</span><span class="sxs-lookup"><span data-stu-id="9a92c-172">[C#]</span></span>         | <span data-ttu-id="9a92c-173">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="9a92c-173">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="9a92c-174">Knihovna tříd Razor</span><span class="sxs-lookup"><span data-stu-id="9a92c-174">Razor Class Library</span></span>                          | `razorclasslib`   | <span data-ttu-id="9a92c-175">[C#]</span><span class="sxs-lookup"><span data-stu-id="9a92c-175">[C#]</span></span>         | <span data-ttu-id="9a92c-176">Knihovna tříd web/Razor/Library/Razor</span><span class="sxs-lookup"><span data-stu-id="9a92c-176">Web/Razor/Library/Razor Class Library</span></span> |
| <span data-ttu-id="9a92c-177">ASP.NET Core webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="9a92c-177">ASP.NET Core Web API</span></span>                         | `webapi`          | <span data-ttu-id="9a92c-178">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="9a92c-178">[C#], F#</span></span>     | <span data-ttu-id="9a92c-179">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="9a92c-179">Web/WebAPI</span></span>                            |
| <span data-ttu-id="9a92c-180">global.json file</span><span class="sxs-lookup"><span data-stu-id="9a92c-180">global.json file</span></span>                             | `globaljson`      |              | <span data-ttu-id="9a92c-181">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="9a92c-181">Config</span></span>                                |
| <span data-ttu-id="9a92c-182">Konfigurace NuGet</span><span class="sxs-lookup"><span data-stu-id="9a92c-182">NuGet Config</span></span>                                 | `nugetconfig`     |              | <span data-ttu-id="9a92c-183">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="9a92c-183">Config</span></span>                                |
| <span data-ttu-id="9a92c-184">Webová konfigurace</span><span class="sxs-lookup"><span data-stu-id="9a92c-184">Web Config</span></span>                                   | `webconfig`       |              | <span data-ttu-id="9a92c-185">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="9a92c-185">Config</span></span>                                |
| <span data-ttu-id="9a92c-186">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="9a92c-186">Solution File</span></span>                                | `sln`             |              | <span data-ttu-id="9a92c-187">Řešení</span><span class="sxs-lookup"><span data-stu-id="9a92c-187">Solution</span></span>                              |

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="9a92c-188">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="9a92c-188">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="9a92c-189">Příkaz obsahuje výchozí seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="9a92c-189">The command contains a default list of templates.</span></span> <span data-ttu-id="9a92c-190">Použijte `dotnet new -l` k získání seznamu dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="9a92c-190">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="9a92c-191">Následující tabulka obsahuje šablony, které jsou předinstalované s .NET Core SDK 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="9a92c-191">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="9a92c-192">Výchozí jazyk pro šablonu se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="9a92c-192">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="9a92c-193">Šablony</span><span class="sxs-lookup"><span data-stu-id="9a92c-193">Templates</span></span>                                    | <span data-ttu-id="9a92c-194">Krátký název</span><span class="sxs-lookup"><span data-stu-id="9a92c-194">Short Name</span></span>      | <span data-ttu-id="9a92c-195">Jazyk</span><span class="sxs-lookup"><span data-stu-id="9a92c-195">Language</span></span>     | <span data-ttu-id="9a92c-196">Značky</span><span class="sxs-lookup"><span data-stu-id="9a92c-196">Tags</span></span>                                  |
|----------------------------------------------|-----------------|--------------|---------------------------------------|
| <span data-ttu-id="9a92c-197">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="9a92c-197">Console Application</span></span>                          | `console`       | <span data-ttu-id="9a92c-198">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="9a92c-198">[C#], F#, VB</span></span> | <span data-ttu-id="9a92c-199">Společná/konzola</span><span class="sxs-lookup"><span data-stu-id="9a92c-199">Common/Console</span></span>                        |
| <span data-ttu-id="9a92c-200">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="9a92c-200">Class library</span></span>                                | `classlib`      | <span data-ttu-id="9a92c-201">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="9a92c-201">[C#], F#, VB</span></span> | <span data-ttu-id="9a92c-202">Společné/knihovny</span><span class="sxs-lookup"><span data-stu-id="9a92c-202">Common/Library</span></span>                        |
| <span data-ttu-id="9a92c-203">Projekt testu jednotek</span><span class="sxs-lookup"><span data-stu-id="9a92c-203">Unit Test Project</span></span>                            | `mstest`        | <span data-ttu-id="9a92c-204">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="9a92c-204">[C#], F#, VB</span></span> | <span data-ttu-id="9a92c-205">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="9a92c-205">Test/MSTest</span></span>                           |
| <span data-ttu-id="9a92c-206">Projekt testů xUnit</span><span class="sxs-lookup"><span data-stu-id="9a92c-206">xUnit Test Project</span></span>                           | `xunit`         | <span data-ttu-id="9a92c-207">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="9a92c-207">[C#], F#, VB</span></span> | <span data-ttu-id="9a92c-208">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="9a92c-208">Test/xUnit</span></span>                            |
| <span data-ttu-id="9a92c-209">Stránka Razor</span><span class="sxs-lookup"><span data-stu-id="9a92c-209">Razor Page</span></span>                                   | `page`          | <span data-ttu-id="9a92c-210">[C#]</span><span class="sxs-lookup"><span data-stu-id="9a92c-210">[C#]</span></span>         | <span data-ttu-id="9a92c-211">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="9a92c-211">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="9a92c-212">ViewImports MVC</span><span class="sxs-lookup"><span data-stu-id="9a92c-212">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="9a92c-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="9a92c-213">[C#]</span></span>         | <span data-ttu-id="9a92c-214">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="9a92c-214">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="9a92c-215">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="9a92c-215">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="9a92c-216">[C#]</span><span class="sxs-lookup"><span data-stu-id="9a92c-216">[C#]</span></span>         | <span data-ttu-id="9a92c-217">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="9a92c-217">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="9a92c-218">ASP.NET Core prázdné</span><span class="sxs-lookup"><span data-stu-id="9a92c-218">ASP.NET Core Empty</span></span>                           | `web`           | <span data-ttu-id="9a92c-219">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="9a92c-219">[C#], F#</span></span>     | <span data-ttu-id="9a92c-220">Web/prázdné</span><span class="sxs-lookup"><span data-stu-id="9a92c-220">Web/Empty</span></span>                             |
| <span data-ttu-id="9a92c-221">ASP.NET Core webová aplikace (model-zobrazení-kontroler)</span><span class="sxs-lookup"><span data-stu-id="9a92c-221">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="9a92c-222">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="9a92c-222">[C#], F#</span></span>     | <span data-ttu-id="9a92c-223">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="9a92c-223">Web/MVC</span></span>                               |
| <span data-ttu-id="9a92c-224">ASP.NET Core webové aplikace</span><span class="sxs-lookup"><span data-stu-id="9a92c-224">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="9a92c-225">[C#]</span><span class="sxs-lookup"><span data-stu-id="9a92c-225">[C#]</span></span>         | <span data-ttu-id="9a92c-226">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="9a92c-226">Web/MVC/Razor Pages</span></span>                   |
| <span data-ttu-id="9a92c-227">ASP.NET Core s úhlovým</span><span class="sxs-lookup"><span data-stu-id="9a92c-227">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="9a92c-228">[C#]</span><span class="sxs-lookup"><span data-stu-id="9a92c-228">[C#]</span></span>         | <span data-ttu-id="9a92c-229">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="9a92c-229">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="9a92c-230">ASP.NET Core s reagují. js</span><span class="sxs-lookup"><span data-stu-id="9a92c-230">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="9a92c-231">[C#]</span><span class="sxs-lookup"><span data-stu-id="9a92c-231">[C#]</span></span>         | <span data-ttu-id="9a92c-232">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="9a92c-232">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="9a92c-233">ASP.NET Core s využitím reagují. js a Redux</span><span class="sxs-lookup"><span data-stu-id="9a92c-233">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="9a92c-234">[C#]</span><span class="sxs-lookup"><span data-stu-id="9a92c-234">[C#]</span></span>         | <span data-ttu-id="9a92c-235">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="9a92c-235">Web/MVC/SPA</span></span>                           | 
| <span data-ttu-id="9a92c-236">Knihovna tříd Razor</span><span class="sxs-lookup"><span data-stu-id="9a92c-236">Razor Class Library</span></span>                          | `razorclasslib` | <span data-ttu-id="9a92c-237">[C#]</span><span class="sxs-lookup"><span data-stu-id="9a92c-237">[C#]</span></span>         | <span data-ttu-id="9a92c-238">Knihovna tříd web/Razor/Library/Razor</span><span class="sxs-lookup"><span data-stu-id="9a92c-238">Web/Razor/Library/Razor Class Library</span></span> |
| <span data-ttu-id="9a92c-239">ASP.NET Core webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="9a92c-239">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="9a92c-240">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="9a92c-240">[C#], F#</span></span>     | <span data-ttu-id="9a92c-241">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="9a92c-241">Web/WebAPI</span></span>                            |
| <span data-ttu-id="9a92c-242">global.json file</span><span class="sxs-lookup"><span data-stu-id="9a92c-242">global.json file</span></span>                             | `globaljson`    |              | <span data-ttu-id="9a92c-243">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="9a92c-243">Config</span></span>                                |
| <span data-ttu-id="9a92c-244">Konfigurace NuGet</span><span class="sxs-lookup"><span data-stu-id="9a92c-244">NuGet Config</span></span>                                 | `nugetconfig`   |              | <span data-ttu-id="9a92c-245">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="9a92c-245">Config</span></span>                                |
| <span data-ttu-id="9a92c-246">Webová konfigurace</span><span class="sxs-lookup"><span data-stu-id="9a92c-246">Web Config</span></span>                                   | `webconfig`     |              | <span data-ttu-id="9a92c-247">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="9a92c-247">Config</span></span>                                |
| <span data-ttu-id="9a92c-248">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="9a92c-248">Solution File</span></span>                                | `sln`           |              | <span data-ttu-id="9a92c-249">Řešení</span><span class="sxs-lookup"><span data-stu-id="9a92c-249">Solution</span></span>                              |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="9a92c-250">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="9a92c-250">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="9a92c-251">Příkaz obsahuje výchozí seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="9a92c-251">The command contains a default list of templates.</span></span> <span data-ttu-id="9a92c-252">Použijte `dotnet new -l` k získání seznamu dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="9a92c-252">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="9a92c-253">Následující tabulka obsahuje šablony, které jsou předinstalované s .NET Core SDK 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="9a92c-253">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.0.</span></span> <span data-ttu-id="9a92c-254">Výchozí jazyk pro šablonu se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="9a92c-254">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="9a92c-255">Šablony</span><span class="sxs-lookup"><span data-stu-id="9a92c-255">Templates</span></span>                                    | <span data-ttu-id="9a92c-256">Krátký název</span><span class="sxs-lookup"><span data-stu-id="9a92c-256">Short Name</span></span>    | <span data-ttu-id="9a92c-257">Jazyk</span><span class="sxs-lookup"><span data-stu-id="9a92c-257">Language</span></span>     | <span data-ttu-id="9a92c-258">Značky</span><span class="sxs-lookup"><span data-stu-id="9a92c-258">Tags</span></span>                |
|----------------------------------------------|---------------|--------------|---------------------|
| <span data-ttu-id="9a92c-259">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="9a92c-259">Console Application</span></span>                          | `console`     | <span data-ttu-id="9a92c-260">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="9a92c-260">[C#], F#, VB</span></span> | <span data-ttu-id="9a92c-261">Společná/konzola</span><span class="sxs-lookup"><span data-stu-id="9a92c-261">Common/Console</span></span>      |
| <span data-ttu-id="9a92c-262">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="9a92c-262">Class library</span></span>                                | `classlib`    | <span data-ttu-id="9a92c-263">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="9a92c-263">[C#], F#, VB</span></span> | <span data-ttu-id="9a92c-264">Společné/knihovny</span><span class="sxs-lookup"><span data-stu-id="9a92c-264">Common/Library</span></span>      |
| <span data-ttu-id="9a92c-265">Projekt testu jednotek</span><span class="sxs-lookup"><span data-stu-id="9a92c-265">Unit Test Project</span></span>                            | `mstest`      | <span data-ttu-id="9a92c-266">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="9a92c-266">[C#], F#, VB</span></span> | <span data-ttu-id="9a92c-267">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="9a92c-267">Test/MSTest</span></span>         |
| <span data-ttu-id="9a92c-268">Projekt testů xUnit</span><span class="sxs-lookup"><span data-stu-id="9a92c-268">xUnit Test Project</span></span>                           | `xunit`       | <span data-ttu-id="9a92c-269">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="9a92c-269">[C#], F#, VB</span></span> | <span data-ttu-id="9a92c-270">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="9a92c-270">Test/xUnit</span></span>          |
| <span data-ttu-id="9a92c-271">ASP.NET Core prázdné</span><span class="sxs-lookup"><span data-stu-id="9a92c-271">ASP.NET Core Empty</span></span>                           | `web`         | <span data-ttu-id="9a92c-272">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="9a92c-272">[C#], F#</span></span>     | <span data-ttu-id="9a92c-273">Web/prázdné</span><span class="sxs-lookup"><span data-stu-id="9a92c-273">Web/Empty</span></span>           |
| <span data-ttu-id="9a92c-274">ASP.NET Core webová aplikace (model-zobrazení-kontroler)</span><span class="sxs-lookup"><span data-stu-id="9a92c-274">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="9a92c-275">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="9a92c-275">[C#], F#</span></span>     | <span data-ttu-id="9a92c-276">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="9a92c-276">Web/MVC</span></span>             |
| <span data-ttu-id="9a92c-277">ASP.NET Core webové aplikace</span><span class="sxs-lookup"><span data-stu-id="9a92c-277">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="9a92c-278">[C#]</span><span class="sxs-lookup"><span data-stu-id="9a92c-278">[C#]</span></span>         | <span data-ttu-id="9a92c-279">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="9a92c-279">Web/MVC/Razor Pages</span></span> |
| <span data-ttu-id="9a92c-280">ASP.NET Core s úhlovým</span><span class="sxs-lookup"><span data-stu-id="9a92c-280">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="9a92c-281">[C#]</span><span class="sxs-lookup"><span data-stu-id="9a92c-281">[C#]</span></span>         | <span data-ttu-id="9a92c-282">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="9a92c-282">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="9a92c-283">ASP.NET Core s reagují. js</span><span class="sxs-lookup"><span data-stu-id="9a92c-283">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="9a92c-284">[C#]</span><span class="sxs-lookup"><span data-stu-id="9a92c-284">[C#]</span></span>         | <span data-ttu-id="9a92c-285">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="9a92c-285">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="9a92c-286">ASP.NET Core s využitím reagují. js a Redux</span><span class="sxs-lookup"><span data-stu-id="9a92c-286">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="9a92c-287">[C#]</span><span class="sxs-lookup"><span data-stu-id="9a92c-287">[C#]</span></span>         | <span data-ttu-id="9a92c-288">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="9a92c-288">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="9a92c-289">ASP.NET Core webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="9a92c-289">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="9a92c-290">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="9a92c-290">[C#], F#</span></span>     | <span data-ttu-id="9a92c-291">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="9a92c-291">Web/WebAPI</span></span>          |
| <span data-ttu-id="9a92c-292">global.json file</span><span class="sxs-lookup"><span data-stu-id="9a92c-292">global.json file</span></span>                             | `globaljson`  |              | <span data-ttu-id="9a92c-293">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="9a92c-293">Config</span></span>              |
| <span data-ttu-id="9a92c-294">Konfigurace NuGet</span><span class="sxs-lookup"><span data-stu-id="9a92c-294">Nuget Config</span></span>                                 | `nugetconfig` |              | <span data-ttu-id="9a92c-295">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="9a92c-295">Config</span></span>              |
| <span data-ttu-id="9a92c-296">Webová konfigurace</span><span class="sxs-lookup"><span data-stu-id="9a92c-296">Web Config</span></span>                                   | `webconfig`   |              | <span data-ttu-id="9a92c-297">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="9a92c-297">Config</span></span>              |
| <span data-ttu-id="9a92c-298">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="9a92c-298">Solution File</span></span>                                | `sln`         |              | <span data-ttu-id="9a92c-299">Řešení</span><span class="sxs-lookup"><span data-stu-id="9a92c-299">Solution</span></span>            |
| <span data-ttu-id="9a92c-300">Stránka Razor</span><span class="sxs-lookup"><span data-stu-id="9a92c-300">Razor Page</span></span>                                   | `page`        |              | <span data-ttu-id="9a92c-301">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="9a92c-301">Web/ASP.NET</span></span>         |
| <span data-ttu-id="9a92c-302">ViewImports MVC</span><span class="sxs-lookup"><span data-stu-id="9a92c-302">MVC ViewImports</span></span>                              | `viewimports` |              | <span data-ttu-id="9a92c-303">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="9a92c-303">Web/ASP.NET</span></span>         |
| <span data-ttu-id="9a92c-304">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="9a92c-304">MVC ViewStart</span></span>                                | `viewstart`   |              | <span data-ttu-id="9a92c-305">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="9a92c-305">Web/ASP.NET</span></span>         |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="9a92c-306">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="9a92c-306">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="9a92c-307">Příkaz obsahuje výchozí seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="9a92c-307">The command contains a default list of templates.</span></span> <span data-ttu-id="9a92c-308">Použijte `dotnet new -all` k získání seznamu dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="9a92c-308">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="9a92c-309">Následující tabulka obsahuje šablony, které jsou předinstalované s .NET Core SDK 1.0.1.</span><span class="sxs-lookup"><span data-stu-id="9a92c-309">The following table shows the templates that come pre-installed with the .NET Core SDK 1.0.1.</span></span> <span data-ttu-id="9a92c-310">Výchozí jazyk pro šablonu se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="9a92c-310">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="9a92c-311">Šablony</span><span class="sxs-lookup"><span data-stu-id="9a92c-311">Templates</span></span>            | <span data-ttu-id="9a92c-312">Krátký název</span><span class="sxs-lookup"><span data-stu-id="9a92c-312">Short Name</span></span>    | <span data-ttu-id="9a92c-313">Jazyk</span><span class="sxs-lookup"><span data-stu-id="9a92c-313">Language</span></span> | <span data-ttu-id="9a92c-314">Značky</span><span class="sxs-lookup"><span data-stu-id="9a92c-314">Tags</span></span>           |
|----------------------|---------------|----------|----------------|
| <span data-ttu-id="9a92c-315">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="9a92c-315">Console Application</span></span>  | `console`     | <span data-ttu-id="9a92c-316">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="9a92c-316">[C#], F#</span></span> | <span data-ttu-id="9a92c-317">Společná/konzola</span><span class="sxs-lookup"><span data-stu-id="9a92c-317">Common/Console</span></span> |
| <span data-ttu-id="9a92c-318">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="9a92c-318">Class library</span></span>        | `classlib`    | <span data-ttu-id="9a92c-319">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="9a92c-319">[C#], F#</span></span> | <span data-ttu-id="9a92c-320">Společné/knihovny</span><span class="sxs-lookup"><span data-stu-id="9a92c-320">Common/Library</span></span> |
| <span data-ttu-id="9a92c-321">Projekt testu jednotek</span><span class="sxs-lookup"><span data-stu-id="9a92c-321">Unit Test Project</span></span>    | `mstest`      | <span data-ttu-id="9a92c-322">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="9a92c-322">[C#], F#</span></span> | <span data-ttu-id="9a92c-323">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="9a92c-323">Test/MSTest</span></span>    |
| <span data-ttu-id="9a92c-324">Projekt testů xUnit</span><span class="sxs-lookup"><span data-stu-id="9a92c-324">xUnit Test Project</span></span>   | `xunit`       | <span data-ttu-id="9a92c-325">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="9a92c-325">[C#], F#</span></span> | <span data-ttu-id="9a92c-326">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="9a92c-326">Test/xUnit</span></span>     |
| <span data-ttu-id="9a92c-327">ASP.NET Core prázdné</span><span class="sxs-lookup"><span data-stu-id="9a92c-327">ASP.NET Core Empty</span></span>   | `web`         | <span data-ttu-id="9a92c-328">[C#]</span><span class="sxs-lookup"><span data-stu-id="9a92c-328">[C#]</span></span>     | <span data-ttu-id="9a92c-329">Web/prázdné</span><span class="sxs-lookup"><span data-stu-id="9a92c-329">Web/Empty</span></span>      |
| <span data-ttu-id="9a92c-330">ASP.NET Core webové aplikace</span><span class="sxs-lookup"><span data-stu-id="9a92c-330">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="9a92c-331">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="9a92c-331">[C#], F#</span></span> | <span data-ttu-id="9a92c-332">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="9a92c-332">Web/MVC</span></span>        |
| <span data-ttu-id="9a92c-333">ASP.NET Core webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="9a92c-333">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="9a92c-334">[C#]</span><span class="sxs-lookup"><span data-stu-id="9a92c-334">[C#]</span></span>     | <span data-ttu-id="9a92c-335">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="9a92c-335">Web/WebAPI</span></span>     |
| <span data-ttu-id="9a92c-336">Konfigurace NuGet</span><span class="sxs-lookup"><span data-stu-id="9a92c-336">Nuget Config</span></span>         | `nugetconfig` |          | <span data-ttu-id="9a92c-337">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="9a92c-337">Config</span></span>         |
| <span data-ttu-id="9a92c-338">Webová konfigurace</span><span class="sxs-lookup"><span data-stu-id="9a92c-338">Web Config</span></span>           | `webconfig`   |          | <span data-ttu-id="9a92c-339">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="9a92c-339">Config</span></span>         |
| <span data-ttu-id="9a92c-340">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="9a92c-340">Solution File</span></span>        | `sln`         |          | <span data-ttu-id="9a92c-341">Řešení</span><span class="sxs-lookup"><span data-stu-id="9a92c-341">Solution</span></span>       |

---

## <a name="options"></a><span data-ttu-id="9a92c-342">Možnosti</span><span class="sxs-lookup"><span data-stu-id="9a92c-342">Options</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="9a92c-343">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="9a92c-343">.NET Core 2.2</span></span>](#tab/netcore22)

`--dry-run`

<span data-ttu-id="9a92c-344">Zobrazí souhrnné informace o tom, co se stane, pokud by došlo ke spuštění daného příkazu, pokud by to vedlo k vytvoření šablony.</span><span class="sxs-lookup"><span data-stu-id="9a92c-344">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span>

`--force`

<span data-ttu-id="9a92c-345">Vynutí vygenerování obsahu i v případě, že změní existující soubory.</span><span class="sxs-lookup"><span data-stu-id="9a92c-345">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="9a92c-346">To je nutné v případě, že výstupní adresář již obsahuje projekt.</span><span class="sxs-lookup"><span data-stu-id="9a92c-346">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="9a92c-347">Vytiskne nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="9a92c-347">Prints out help for the command.</span></span> <span data-ttu-id="9a92c-348">Dá se vyvolat pro `dotnet new` samotný příkaz nebo pro libovolnou šablonu, `dotnet new mvc --help`jako je například.</span><span class="sxs-lookup"><span data-stu-id="9a92c-348">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="9a92c-349">Nainstaluje zdroj nebo balíček šablony z `PATH` nebo `NUGET_ID` poskytnutého.</span><span class="sxs-lookup"><span data-stu-id="9a92c-349">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="9a92c-350">Pokud chcete nainstalovat předprodejní verzi balíčku šablony, je nutné zadat verzi ve formátu `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-350">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="9a92c-351">Ve výchozím nastavení `dotnet new` se \* předá verze, která představuje poslední stabilní verzi balíčku.</span><span class="sxs-lookup"><span data-stu-id="9a92c-351">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="9a92c-352">Podívejte se na příklad v části [Příklady](#examples) .</span><span class="sxs-lookup"><span data-stu-id="9a92c-352">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="9a92c-353">Informace o vytváření vlastních šablon najdete v tématu [vlastní šablony pro dotnet New](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="9a92c-353">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="9a92c-354">Vypíše seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="9a92c-354">Lists templates containing the specified name.</span></span> <span data-ttu-id="9a92c-355">Pokud je vyvoláno pro `dotnet new` příkaz, zobrazí seznam možných šablon dostupných pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="9a92c-355">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="9a92c-356">Například Pokud adresář již obsahuje projekt, nezobrazuje seznam všech šablon projektu.</span><span class="sxs-lookup"><span data-stu-id="9a92c-356">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="9a92c-357">Jazyk šablony, která se má vytvořit</span><span class="sxs-lookup"><span data-stu-id="9a92c-357">The language of the template to create.</span></span> <span data-ttu-id="9a92c-358">Přijatý jazyk se liší podle šablony (viz výchozí hodnoty v oddílu [argumenty](#arguments) ).</span><span class="sxs-lookup"><span data-stu-id="9a92c-358">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="9a92c-359">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="9a92c-359">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="9a92c-360">Některá prostředí jsou interpretována `#` jako speciální znak.</span><span class="sxs-lookup"><span data-stu-id="9a92c-360">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="9a92c-361">V těchto případech je nutné uvést hodnotu parametru jazyka, například `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-361">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="9a92c-362">Název vytvořeného výstupu.</span><span class="sxs-lookup"><span data-stu-id="9a92c-362">The name for the created output.</span></span> <span data-ttu-id="9a92c-363">Pokud název nezadáte, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="9a92c-363">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="9a92c-364">Určuje zdroj NuGet, který se použije při instalaci.</span><span class="sxs-lookup"><span data-stu-id="9a92c-364">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="9a92c-365">Umístění, do kterého se má vygenerovaný výstup umístit.</span><span class="sxs-lookup"><span data-stu-id="9a92c-365">Location to place the generated output.</span></span> <span data-ttu-id="9a92c-366">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="9a92c-366">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="9a92c-367">Filtruje šablony založené na dostupných typech.</span><span class="sxs-lookup"><span data-stu-id="9a92c-367">Filters templates based on available types.</span></span> <span data-ttu-id="9a92c-368">Předdefinované hodnoty jsou "projekt", "položka" nebo "jiné".</span><span class="sxs-lookup"><span data-stu-id="9a92c-368">Predefined values are "project", "item", or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="9a92c-369">Odinstaluje zdrojový nebo Template Pack na `PATH` nebo `NUGET_ID` poskytnutý.</span><span class="sxs-lookup"><span data-stu-id="9a92c-369">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="9a92c-370">Při vyloučení `<PATH|NUGET_ID>` hodnoty se zobrazí všechny aktuálně nainstalované sady šablon a jejich přidružené šablony.</span><span class="sxs-lookup"><span data-stu-id="9a92c-370">When excluding the `<PATH|NUGET_ID>` value, all currently installed template packs and their associated templates are displayed.</span></span>

> [!NOTE]
> <span data-ttu-id="9a92c-371">Chcete-li odinstalovat šablonu pomocí `PATH`nástroje, je nutné plně kvalifikovat cestu.</span><span class="sxs-lookup"><span data-stu-id="9a92c-371">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="9a92c-372">Například *C:/Users/\<User >/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z nadřazené složky to nebude.</span><span class="sxs-lookup"><span data-stu-id="9a92c-372">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="9a92c-373">Kromě toho Nezahrnovat koncové koncové lomítko adresáře na cestu k šabloně.</span><span class="sxs-lookup"><span data-stu-id="9a92c-373">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="9a92c-374">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="9a92c-374">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="9a92c-375">Vynutí vygenerování obsahu i v případě, že změní existující soubory.</span><span class="sxs-lookup"><span data-stu-id="9a92c-375">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="9a92c-376">To je nutné v případě, že výstupní adresář již obsahuje projekt.</span><span class="sxs-lookup"><span data-stu-id="9a92c-376">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="9a92c-377">Vytiskne nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="9a92c-377">Prints out help for the command.</span></span> <span data-ttu-id="9a92c-378">Dá se vyvolat pro `dotnet new` samotný příkaz nebo pro libovolnou šablonu, `dotnet new mvc --help`jako je například.</span><span class="sxs-lookup"><span data-stu-id="9a92c-378">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="9a92c-379">Nainstaluje zdroj nebo balíček šablony z `PATH` nebo `NUGET_ID` poskytnutého.</span><span class="sxs-lookup"><span data-stu-id="9a92c-379">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="9a92c-380">Pokud chcete nainstalovat předprodejní verzi balíčku šablony, je nutné zadat verzi ve formátu `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-380">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="9a92c-381">Ve výchozím nastavení `dotnet new` se \* předá verze, která představuje poslední stabilní verzi balíčku.</span><span class="sxs-lookup"><span data-stu-id="9a92c-381">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="9a92c-382">Podívejte se na příklad v části [Příklady](#examples) .</span><span class="sxs-lookup"><span data-stu-id="9a92c-382">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="9a92c-383">Informace o vytváření vlastních šablon najdete v tématu [vlastní šablony pro dotnet New](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="9a92c-383">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="9a92c-384">Vypíše seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="9a92c-384">Lists templates containing the specified name.</span></span> <span data-ttu-id="9a92c-385">Pokud je vyvoláno pro `dotnet new` příkaz, zobrazí seznam možných šablon dostupných pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="9a92c-385">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="9a92c-386">Například Pokud adresář již obsahuje projekt, nezobrazuje seznam všech šablon projektu.</span><span class="sxs-lookup"><span data-stu-id="9a92c-386">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="9a92c-387">Jazyk šablony, která se má vytvořit</span><span class="sxs-lookup"><span data-stu-id="9a92c-387">The language of the template to create.</span></span> <span data-ttu-id="9a92c-388">Přijatý jazyk se liší podle šablony (viz výchozí hodnoty v oddílu [argumenty](#arguments) ).</span><span class="sxs-lookup"><span data-stu-id="9a92c-388">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="9a92c-389">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="9a92c-389">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="9a92c-390">Některá prostředí jsou interpretována `#` jako speciální znak.</span><span class="sxs-lookup"><span data-stu-id="9a92c-390">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="9a92c-391">V těchto případech je nutné uvést hodnotu parametru jazyka, například `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-391">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="9a92c-392">Název vytvořeného výstupu.</span><span class="sxs-lookup"><span data-stu-id="9a92c-392">The name for the created output.</span></span> <span data-ttu-id="9a92c-393">Pokud název nezadáte, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="9a92c-393">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="9a92c-394">Určuje zdroj NuGet, který se použije při instalaci.</span><span class="sxs-lookup"><span data-stu-id="9a92c-394">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="9a92c-395">Umístění, do kterého se má vygenerovaný výstup umístit.</span><span class="sxs-lookup"><span data-stu-id="9a92c-395">Location to place the generated output.</span></span> <span data-ttu-id="9a92c-396">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="9a92c-396">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="9a92c-397">Filtruje šablony založené na dostupných typech.</span><span class="sxs-lookup"><span data-stu-id="9a92c-397">Filters templates based on available types.</span></span> <span data-ttu-id="9a92c-398">Předdefinované hodnoty jsou "projekt", "položka" nebo "jiné".</span><span class="sxs-lookup"><span data-stu-id="9a92c-398">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="9a92c-399">Odinstaluje zdrojový nebo Template Pack na `PATH` nebo `NUGET_ID` poskytnutý.</span><span class="sxs-lookup"><span data-stu-id="9a92c-399">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="9a92c-400">Chcete-li odinstalovat šablonu pomocí `PATH`nástroje, je nutné plně kvalifikovat cestu.</span><span class="sxs-lookup"><span data-stu-id="9a92c-400">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="9a92c-401">Například *C:/Users/\<User >/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z nadřazené složky to nebude.</span><span class="sxs-lookup"><span data-stu-id="9a92c-401">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="9a92c-402">Kromě toho Nezahrnovat koncové koncové lomítko adresáře na cestu k šabloně.</span><span class="sxs-lookup"><span data-stu-id="9a92c-402">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="9a92c-403">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="9a92c-403">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="9a92c-404">Vynutí vygenerování obsahu i v případě, že změní existující soubory.</span><span class="sxs-lookup"><span data-stu-id="9a92c-404">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="9a92c-405">To je nutné v případě, že výstupní adresář již obsahuje projekt.</span><span class="sxs-lookup"><span data-stu-id="9a92c-405">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="9a92c-406">Vytiskne nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="9a92c-406">Prints out help for the command.</span></span> <span data-ttu-id="9a92c-407">Dá se vyvolat pro `dotnet new` samotný příkaz nebo pro libovolnou šablonu, `dotnet new mvc --help`jako je například.</span><span class="sxs-lookup"><span data-stu-id="9a92c-407">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="9a92c-408">Nainstaluje zdroj nebo balíček šablony z `PATH` nebo `NUGET_ID` poskytnutého.</span><span class="sxs-lookup"><span data-stu-id="9a92c-408">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="9a92c-409">Pokud chcete nainstalovat předprodejní verzi balíčku šablony, je nutné zadat verzi ve formátu `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-409">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="9a92c-410">Ve výchozím nastavení `dotnet new` se \* předá verze, která představuje poslední stabilní verzi balíčku.</span><span class="sxs-lookup"><span data-stu-id="9a92c-410">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="9a92c-411">Podívejte se na příklad v části [Příklady](#examples) .</span><span class="sxs-lookup"><span data-stu-id="9a92c-411">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="9a92c-412">Informace o vytváření vlastních šablon najdete v tématu [vlastní šablony pro dotnet New](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="9a92c-412">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="9a92c-413">Vypíše seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="9a92c-413">Lists templates containing the specified name.</span></span> <span data-ttu-id="9a92c-414">Pokud je vyvoláno pro `dotnet new` příkaz, zobrazí seznam možných šablon dostupných pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="9a92c-414">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="9a92c-415">Například Pokud adresář již obsahuje projekt, nezobrazuje seznam všech šablon projektu.</span><span class="sxs-lookup"><span data-stu-id="9a92c-415">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="9a92c-416">Jazyk šablony, která se má vytvořit</span><span class="sxs-lookup"><span data-stu-id="9a92c-416">The language of the template to create.</span></span> <span data-ttu-id="9a92c-417">Přijatý jazyk se liší podle šablony (viz výchozí hodnoty v oddílu [argumenty](#arguments) ).</span><span class="sxs-lookup"><span data-stu-id="9a92c-417">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="9a92c-418">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="9a92c-418">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="9a92c-419">Některá prostředí jsou interpretována `#` jako speciální znak.</span><span class="sxs-lookup"><span data-stu-id="9a92c-419">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="9a92c-420">V těchto případech je nutné uvést hodnotu parametru jazyka, například `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-420">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="9a92c-421">Název vytvořeného výstupu.</span><span class="sxs-lookup"><span data-stu-id="9a92c-421">The name for the created output.</span></span> <span data-ttu-id="9a92c-422">Pokud název nezadáte, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="9a92c-422">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="9a92c-423">Umístění, do kterého se má vygenerovaný výstup umístit.</span><span class="sxs-lookup"><span data-stu-id="9a92c-423">Location to place the generated output.</span></span> <span data-ttu-id="9a92c-424">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="9a92c-424">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="9a92c-425">Filtruje šablony založené na dostupných typech.</span><span class="sxs-lookup"><span data-stu-id="9a92c-425">Filters templates based on available types.</span></span> <span data-ttu-id="9a92c-426">Předdefinované hodnoty jsou "projekt", "položka" nebo "jiné".</span><span class="sxs-lookup"><span data-stu-id="9a92c-426">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="9a92c-427">Odinstaluje zdrojový nebo Template Pack na `PATH` nebo `NUGET_ID` poskytnutý.</span><span class="sxs-lookup"><span data-stu-id="9a92c-427">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="9a92c-428">Chcete-li odinstalovat šablonu pomocí zdroje `PATH`, je nutné cestu plně kvalifikovat.</span><span class="sxs-lookup"><span data-stu-id="9a92c-428">To uninstall a template using a source `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="9a92c-429">Například *C:/Users/\<User >/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z nadřazené složky to nebude.</span><span class="sxs-lookup"><span data-stu-id="9a92c-429">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span> <span data-ttu-id="9a92c-430">Kromě toho Nezahrnovat koncové koncové lomítko adresáře na cestu k šabloně.</span><span class="sxs-lookup"><span data-stu-id="9a92c-430">Additionally, do not include a final terminating directory slash on your template path.</span></span>
> 
> <span data-ttu-id="9a92c-431">Pokud nemůžete určit `PATH` argument nebo `NUGET_ID` , který je potřeba k odinstalaci šablony, `dotnet new --uninstall` při spuštění bez argumentu se zobrazí seznam všech nainstalovaných šablon a argument, který je potřeba k jejich odinstalování.</span><span class="sxs-lookup"><span data-stu-id="9a92c-431">If you are unable to determine the `PATH` or `NUGET_ID` argument needed to uninstall a template, running `dotnet new --uninstall` without an argument will list all installed templates and the argument required to uninstall them.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="9a92c-432">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="9a92c-432">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="9a92c-433">Zobrazí všechny šablony pro konkrétní typ projektu při spuštění v kontextu `dotnet new` samotného příkazu.</span><span class="sxs-lookup"><span data-stu-id="9a92c-433">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="9a92c-434">Při spuštění v souvislosti s konkrétní šablonou, `dotnet new web -all`jako je například, `-all` je interpretován jako příznak vytvoření vynucení.</span><span class="sxs-lookup"><span data-stu-id="9a92c-434">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="9a92c-435">To je nutné v případě, že výstupní adresář již obsahuje projekt.</span><span class="sxs-lookup"><span data-stu-id="9a92c-435">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="9a92c-436">Vytiskne nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="9a92c-436">Prints out help for the command.</span></span> <span data-ttu-id="9a92c-437">Dá se vyvolat pro `dotnet new` samotný příkaz nebo pro libovolnou šablonu, `dotnet new mvc --help`jako je například.</span><span class="sxs-lookup"><span data-stu-id="9a92c-437">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="9a92c-438">Vypíše seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="9a92c-438">Lists templates containing the specified name.</span></span> <span data-ttu-id="9a92c-439">Pokud je vyvoláno pro `dotnet new` příkaz, zobrazí seznam možných šablon dostupných pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="9a92c-439">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="9a92c-440">Například Pokud adresář již obsahuje projekt, nezobrazuje seznam všech šablon projektu.</span><span class="sxs-lookup"><span data-stu-id="9a92c-440">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="9a92c-441">Jazyk šablony, která se má vytvořit</span><span class="sxs-lookup"><span data-stu-id="9a92c-441">The language of the template to create.</span></span> <span data-ttu-id="9a92c-442">Přijatý jazyk se liší podle šablony (viz výchozí hodnoty v oddílu [argumenty](#arguments) ).</span><span class="sxs-lookup"><span data-stu-id="9a92c-442">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="9a92c-443">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="9a92c-443">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="9a92c-444">Některá prostředí jsou interpretována `#` jako speciální znak.</span><span class="sxs-lookup"><span data-stu-id="9a92c-444">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="9a92c-445">V těchto případech je nutné uvést hodnotu parametru jazyka, například `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-445">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="9a92c-446">Název vytvořeného výstupu.</span><span class="sxs-lookup"><span data-stu-id="9a92c-446">The name for the created output.</span></span> <span data-ttu-id="9a92c-447">Pokud název nezadáte, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="9a92c-447">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="9a92c-448">Umístění, do kterého se má vygenerovaný výstup umístit.</span><span class="sxs-lookup"><span data-stu-id="9a92c-448">Location to place the generated output.</span></span> <span data-ttu-id="9a92c-449">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="9a92c-449">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="9a92c-450">Možnosti šablony</span><span class="sxs-lookup"><span data-stu-id="9a92c-450">Template options</span></span>

<span data-ttu-id="9a92c-451">Každá šablona projektu může mít k dispozici další možnosti.</span><span class="sxs-lookup"><span data-stu-id="9a92c-451">Each project template may have additional options available.</span></span> <span data-ttu-id="9a92c-452">Základní šablony mají následující další možnosti:</span><span class="sxs-lookup"><span data-stu-id="9a92c-452">The core templates have the following additional options:</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="9a92c-453">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="9a92c-453">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="9a92c-454">**stromu**</span><span class="sxs-lookup"><span data-stu-id="9a92c-454">**console**</span></span>

<span data-ttu-id="9a92c-455">`--langVersion <VERSION_NUMBER>`-Nastaví `LangVersion` vlastnost v souboru vytvořeného projektu.</span><span class="sxs-lookup"><span data-stu-id="9a92c-455">`--langVersion <VERSION_NUMBER>` - Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="9a92c-456">Použijte `--langVersion 7.3` například k použití C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="9a92c-456">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="9a92c-457">Nepodporuje se pro F#.</span><span class="sxs-lookup"><span data-stu-id="9a92c-457">Not supported for F#.</span></span>

<span data-ttu-id="9a92c-458">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="9a92c-458">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="9a92c-459">**Úhlová, reakce, reactredux**</span><span class="sxs-lookup"><span data-stu-id="9a92c-459">**angular, react, reactredux**</span></span>

<span data-ttu-id="9a92c-460">`--exclude-launch-settings`– Vylučte z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="9a92c-460">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="9a92c-461">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="9a92c-461">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="9a92c-462">`--no-https`-Projekt nevyžaduje protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="9a92c-462">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="9a92c-463">Tato možnost se vztahuje jenom `IndividualAuth` na `OrganizationalAuth` to, jestli se nepoužívají.</span><span class="sxs-lookup"><span data-stu-id="9a92c-463">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="9a92c-464">**razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="9a92c-464">**razorclasslib**</span></span>

<span data-ttu-id="9a92c-465">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="9a92c-465">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="9a92c-466">**classlib**</span><span class="sxs-lookup"><span data-stu-id="9a92c-466">**classlib**</span></span>

<span data-ttu-id="9a92c-467">`-f|--framework <FRAMEWORK>`-Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="9a92c-467">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="9a92c-468">Hodnoty: `netcoreapp2.2` pro vytvoření knihovny tříd .NET Core nebo `netstandard2.0` pro vytvoření knihovny tříd .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="9a92c-468">Values: `netcoreapp2.2` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="9a92c-469">Výchozí hodnota je `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-469">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="9a92c-470">`--langVersion <VERSION_NUMBER>`-Nastaví `LangVersion` vlastnost v souboru vytvořeného projektu.</span><span class="sxs-lookup"><span data-stu-id="9a92c-470">`--langVersion <VERSION_NUMBER>` - Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="9a92c-471">Použijte `--langVersion 7.3` například k použití C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="9a92c-471">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="9a92c-472">Nepodporuje se pro F#.</span><span class="sxs-lookup"><span data-stu-id="9a92c-472">Not supported for F#.</span></span>

<span data-ttu-id="9a92c-473">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="9a92c-473">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="9a92c-474">**MSTest, xUnit**</span><span class="sxs-lookup"><span data-stu-id="9a92c-474">**mstest, xunit**</span></span>

<span data-ttu-id="9a92c-475">`-p|--enable-pack`– Povolí balení pro projekt pomocí [sady dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="9a92c-475">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="9a92c-476">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="9a92c-476">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="9a92c-477">**nunit**</span><span class="sxs-lookup"><span data-stu-id="9a92c-477">**nunit**</span></span>

<span data-ttu-id="9a92c-478">`-f|--framework <FRAMEWORK>`-Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="9a92c-478">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="9a92c-479">Výchozí hodnota je `netcoreapp2.1`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-479">The default value is `netcoreapp2.1`.</span></span>

<span data-ttu-id="9a92c-480">`-p|--enable-pack`– Povolí balení pro projekt pomocí [sady dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="9a92c-480">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="9a92c-481">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="9a92c-481">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="9a92c-482">**Page**</span><span class="sxs-lookup"><span data-stu-id="9a92c-482">**page**</span></span>

<span data-ttu-id="9a92c-483">`-na|--namespace <NAMESPACE_NAME>`– Obor názvů pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="9a92c-483">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="9a92c-484">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-484">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="9a92c-485">`-np|--no-pagemodel`-Vytvoří stránku bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="9a92c-485">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="9a92c-486">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="9a92c-486">**viewimports**</span></span>

<span data-ttu-id="9a92c-487">`-na|--namespace <NAMESPACE_NAME>`– Obor názvů pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="9a92c-487">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="9a92c-488">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-488">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="9a92c-489">**web**</span><span class="sxs-lookup"><span data-stu-id="9a92c-489">**web**</span></span>

<span data-ttu-id="9a92c-490">`--exclude-launch-settings`– Vylučte z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="9a92c-490">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="9a92c-491">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="9a92c-491">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="9a92c-492">`--no-https`-Projekt nevyžaduje protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="9a92c-492">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="9a92c-493">Tato možnost se vztahuje jenom `IndividualAuth` na `OrganizationalAuth` to, jestli se nepoužívají.</span><span class="sxs-lookup"><span data-stu-id="9a92c-493">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="9a92c-494">**mvc, webapp**</span><span class="sxs-lookup"><span data-stu-id="9a92c-494">**mvc, webapp**</span></span>

<span data-ttu-id="9a92c-495">`-au|--auth <AUTHENTICATION_TYPE>`– Typ ověřování, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="9a92c-495">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="9a92c-496">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="9a92c-496">The possible values are:</span></span>

- <span data-ttu-id="9a92c-497">`None`-Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="9a92c-497">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="9a92c-498">`Individual`-Individuální ověřování.</span><span class="sxs-lookup"><span data-stu-id="9a92c-498">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="9a92c-499">`IndividualB2C`-Jednotlivá ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="9a92c-499">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="9a92c-500">`SingleOrg`– Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="9a92c-500">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="9a92c-501">`MultiOrg`– Ověřování organizace pro více tenantů.</span><span class="sxs-lookup"><span data-stu-id="9a92c-501">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="9a92c-502">`Windows`– Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="9a92c-502">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="9a92c-503">`--aad-b2c-instance <INSTANCE>`– Instance Azure Active Directory B2C pro připojení.</span><span class="sxs-lookup"><span data-stu-id="9a92c-503">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="9a92c-504">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="9a92c-504">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="9a92c-505">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-505">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="9a92c-506">`-ssp|--susi-policy-id <ID>`– ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="9a92c-506">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="9a92c-507">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="9a92c-507">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="9a92c-508">`-rp|--reset-password-policy-id <ID>`– Resetování ID zásad hesla pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="9a92c-508">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="9a92c-509">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="9a92c-509">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="9a92c-510">`-ep|--edit-profile-policy-id <ID>`– Upravte ID zásad profilu pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="9a92c-510">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="9a92c-511">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="9a92c-511">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="9a92c-512">`--aad-instance <INSTANCE>`– Instance Azure Active Directory pro připojení.</span><span class="sxs-lookup"><span data-stu-id="9a92c-512">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="9a92c-513">Použijte s `SingleOrg` ověřováním nebo `MultiOrg` .</span><span class="sxs-lookup"><span data-stu-id="9a92c-513">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="9a92c-514">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-514">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="9a92c-515">`--client-id <ID>`– ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="9a92c-515">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="9a92c-516">Použijte s `IndividualB2C`ověřováním, `MultiOrg` `SingleOrg`nebo.</span><span class="sxs-lookup"><span data-stu-id="9a92c-516">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="9a92c-517">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-517">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="9a92c-518">`--domain <DOMAIN>`– Doména pro tenanta adresáře.</span><span class="sxs-lookup"><span data-stu-id="9a92c-518">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="9a92c-519">Použijte s `SingleOrg` ověřováním nebo `IndividualB2C` .</span><span class="sxs-lookup"><span data-stu-id="9a92c-519">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="9a92c-520">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-520">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="9a92c-521">`--tenant-id <ID>`– ID TenantId adresáře, ke kterému se má připojit.</span><span class="sxs-lookup"><span data-stu-id="9a92c-521">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="9a92c-522">Použijte s `SingleOrg` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="9a92c-522">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="9a92c-523">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-523">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="9a92c-524">`--callback-path <PATH>`– Cesta požadavku v základní cestě identifikátoru URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="9a92c-524">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="9a92c-525">Použijte s `SingleOrg` ověřováním nebo `IndividualB2C` .</span><span class="sxs-lookup"><span data-stu-id="9a92c-525">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="9a92c-526">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-526">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="9a92c-527">`-r|--org-read-access`– Povolí této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="9a92c-527">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="9a92c-528">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="9a92c-528">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="9a92c-529">`--exclude-launch-settings`– Vylučte z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="9a92c-529">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="9a92c-530">`--no-https`-Projekt nevyžaduje protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="9a92c-530">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="9a92c-531">`app.UseHsts`a `app.UseHttpsRedirection` nejsou přidány do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-531">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="9a92c-532">`Individual`Tato možnost platí pouze `IndividualB2C` `MultiOrg` v případě, že se nepoužívají, nebo.`SingleOrg`</span><span class="sxs-lookup"><span data-stu-id="9a92c-532">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="9a92c-533">`-uld|--use-local-db`-Určuje LocalDB by měl být použit místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="9a92c-533">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="9a92c-534">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="9a92c-534">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="9a92c-535">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="9a92c-535">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="9a92c-536">**webapi**</span><span class="sxs-lookup"><span data-stu-id="9a92c-536">**webapi**</span></span>

<span data-ttu-id="9a92c-537">`-au|--auth <AUTHENTICATION_TYPE>`– Typ ověřování, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="9a92c-537">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="9a92c-538">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="9a92c-538">The possible values are:</span></span>

- <span data-ttu-id="9a92c-539">`None`-Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="9a92c-539">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="9a92c-540">`IndividualB2C`-Jednotlivá ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="9a92c-540">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="9a92c-541">`SingleOrg`– Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="9a92c-541">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="9a92c-542">`Windows`– Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="9a92c-542">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="9a92c-543">`--aad-b2c-instance <INSTANCE>`– Instance Azure Active Directory B2C pro připojení.</span><span class="sxs-lookup"><span data-stu-id="9a92c-543">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="9a92c-544">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="9a92c-544">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="9a92c-545">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-545">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="9a92c-546">`-ssp|--susi-policy-id <ID>`– ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="9a92c-546">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="9a92c-547">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="9a92c-547">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="9a92c-548">`--aad-instance <INSTANCE>`– Instance Azure Active Directory pro připojení.</span><span class="sxs-lookup"><span data-stu-id="9a92c-548">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="9a92c-549">Použijte s `SingleOrg` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="9a92c-549">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="9a92c-550">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-550">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="9a92c-551">`--client-id <ID>`– ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="9a92c-551">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="9a92c-552">Použijte s `IndividualB2C` ověřováním nebo `SingleOrg` .</span><span class="sxs-lookup"><span data-stu-id="9a92c-552">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="9a92c-553">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-553">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="9a92c-554">`--domain <DOMAIN>`– Doména pro tenanta adresáře.</span><span class="sxs-lookup"><span data-stu-id="9a92c-554">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="9a92c-555">Použijte s `SingleOrg` ověřováním nebo `IndividualB2C` .</span><span class="sxs-lookup"><span data-stu-id="9a92c-555">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="9a92c-556">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-556">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="9a92c-557">`--tenant-id <ID>`– ID TenantId adresáře, ke kterému se má připojit.</span><span class="sxs-lookup"><span data-stu-id="9a92c-557">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="9a92c-558">Použijte s `SingleOrg` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="9a92c-558">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="9a92c-559">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-559">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="9a92c-560">`-r|--org-read-access`– Povolí této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="9a92c-560">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="9a92c-561">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="9a92c-561">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="9a92c-562">`--exclude-launch-settings`– Vylučte z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="9a92c-562">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="9a92c-563">`--no-https`-Projekt nevyžaduje protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="9a92c-563">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="9a92c-564">`app.UseHsts`a `app.UseHttpsRedirection` nejsou přidány do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-564">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="9a92c-565">`Individual`Tato možnost platí pouze `IndividualB2C` `MultiOrg` v případě, že se nepoužívají, nebo.`SingleOrg`</span><span class="sxs-lookup"><span data-stu-id="9a92c-565">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="9a92c-566">`-uld|--use-local-db`-Určuje LocalDB by měl být použit místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="9a92c-566">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="9a92c-567">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="9a92c-567">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="9a92c-568">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="9a92c-568">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="9a92c-569">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="9a92c-569">**globaljson**</span></span>

<span data-ttu-id="9a92c-570">`--sdk-version <VERSION_NUMBER>`-Určuje verzi .NET Core SDK, která se má použít v souboru *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="9a92c-570">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="9a92c-571">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="9a92c-571">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="9a92c-572">**Konzola, úhlová, reakce, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="9a92c-572">**console, angular, react, reactredux, razorclasslib**</span></span>

<span data-ttu-id="9a92c-573">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="9a92c-573">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="9a92c-574">**classlib**</span><span class="sxs-lookup"><span data-stu-id="9a92c-574">**classlib**</span></span>

<span data-ttu-id="9a92c-575">`-f|--framework <FRAMEWORK>`-Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="9a92c-575">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="9a92c-576">Hodnoty: `netcoreapp2.1` pro vytvoření knihovny tříd .NET Core nebo `netstandard2.0` pro vytvoření knihovny tříd .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="9a92c-576">Values: `netcoreapp2.1` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="9a92c-577">Výchozí hodnota je `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-577">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="9a92c-578">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="9a92c-578">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="9a92c-579">**MSTest, xUnit**</span><span class="sxs-lookup"><span data-stu-id="9a92c-579">**mstest, xunit**</span></span>

<span data-ttu-id="9a92c-580">`-p|--enable-pack`– Povolí balení pro projekt pomocí [sady dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="9a92c-580">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="9a92c-581">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="9a92c-581">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="9a92c-582">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="9a92c-582">**globaljson**</span></span>

<span data-ttu-id="9a92c-583">`--sdk-version <VERSION_NUMBER>`-Určuje verzi .NET Core SDK, která se má použít v souboru *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="9a92c-583">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="9a92c-584">**web**</span><span class="sxs-lookup"><span data-stu-id="9a92c-584">**web**</span></span>

<span data-ttu-id="9a92c-585">`--exclude-launch-settings`– Vylučte z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="9a92c-585">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="9a92c-586">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="9a92c-586">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="9a92c-587">`--no-https`-Projekt nevyžaduje protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="9a92c-587">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="9a92c-588">Tato možnost se vztahuje jenom `IndividualAuth` na `OrganizationalAuth` to, jestli se nepoužívají.</span><span class="sxs-lookup"><span data-stu-id="9a92c-588">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="9a92c-589">**webapi**</span><span class="sxs-lookup"><span data-stu-id="9a92c-589">**webapi**</span></span>

<span data-ttu-id="9a92c-590">`-au|--auth <AUTHENTICATION_TYPE>`– Typ ověřování, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="9a92c-590">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="9a92c-591">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="9a92c-591">The possible values are:</span></span>

- <span data-ttu-id="9a92c-592">`None`-Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="9a92c-592">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="9a92c-593">`IndividualB2C`-Jednotlivá ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="9a92c-593">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="9a92c-594">`SingleOrg`– Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="9a92c-594">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="9a92c-595">`Windows`– Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="9a92c-595">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="9a92c-596">`--aad-b2c-instance <INSTANCE>`– Instance Azure Active Directory B2C pro připojení.</span><span class="sxs-lookup"><span data-stu-id="9a92c-596">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="9a92c-597">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="9a92c-597">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="9a92c-598">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-598">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="9a92c-599">`-ssp|--susi-policy-id <ID>`– ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="9a92c-599">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="9a92c-600">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="9a92c-600">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="9a92c-601">`--aad-instance <INSTANCE>`– Instance Azure Active Directory pro připojení.</span><span class="sxs-lookup"><span data-stu-id="9a92c-601">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="9a92c-602">Použijte s `SingleOrg` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="9a92c-602">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="9a92c-603">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-603">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="9a92c-604">`--client-id <ID>`– ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="9a92c-604">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="9a92c-605">Použijte s `IndividualB2C` ověřováním nebo `SingleOrg` .</span><span class="sxs-lookup"><span data-stu-id="9a92c-605">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="9a92c-606">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-606">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="9a92c-607">`--domain <DOMAIN>`– Doména pro tenanta adresáře.</span><span class="sxs-lookup"><span data-stu-id="9a92c-607">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="9a92c-608">Použijte s `SingleOrg` ověřováním nebo `IndividualB2C` .</span><span class="sxs-lookup"><span data-stu-id="9a92c-608">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="9a92c-609">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-609">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="9a92c-610">`--tenant-id <ID>`– ID TenantId adresáře, ke kterému se má připojit.</span><span class="sxs-lookup"><span data-stu-id="9a92c-610">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="9a92c-611">Použijte s `SingleOrg` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="9a92c-611">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="9a92c-612">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-612">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="9a92c-613">`-r|--org-read-access`– Povolí této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="9a92c-613">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="9a92c-614">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="9a92c-614">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="9a92c-615">`--exclude-launch-settings`– Vylučte z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="9a92c-615">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="9a92c-616">`-uld|--use-local-db`-Určuje LocalDB by měl být použit místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="9a92c-616">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="9a92c-617">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="9a92c-617">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="9a92c-618">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="9a92c-618">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="9a92c-619">`--no-https`-Projekt nevyžaduje protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="9a92c-619">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="9a92c-620">`app.UseHsts`a `app.UseHttpsRedirection` nejsou přidány do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-620">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="9a92c-621">`Individual`Tato možnost platí pouze `IndividualB2C` `MultiOrg` v případě, že se nepoužívají, nebo.`SingleOrg`</span><span class="sxs-lookup"><span data-stu-id="9a92c-621">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="9a92c-622">**MVC, Razor**</span><span class="sxs-lookup"><span data-stu-id="9a92c-622">**mvc, razor**</span></span>

<span data-ttu-id="9a92c-623">`-au|--auth <AUTHENTICATION_TYPE>`– Typ ověřování, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="9a92c-623">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="9a92c-624">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="9a92c-624">The possible values are:</span></span>

- <span data-ttu-id="9a92c-625">`None`-Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="9a92c-625">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="9a92c-626">`Individual`-Individuální ověřování.</span><span class="sxs-lookup"><span data-stu-id="9a92c-626">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="9a92c-627">`IndividualB2C`-Jednotlivá ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="9a92c-627">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="9a92c-628">`SingleOrg`– Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="9a92c-628">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="9a92c-629">`MultiOrg`– Ověřování organizace pro více tenantů.</span><span class="sxs-lookup"><span data-stu-id="9a92c-629">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="9a92c-630">`Windows`– Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="9a92c-630">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="9a92c-631">`--aad-b2c-instance <INSTANCE>`– Instance Azure Active Directory B2C pro připojení.</span><span class="sxs-lookup"><span data-stu-id="9a92c-631">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="9a92c-632">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="9a92c-632">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="9a92c-633">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-633">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="9a92c-634">`-ssp|--susi-policy-id <ID>`– ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="9a92c-634">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="9a92c-635">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="9a92c-635">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="9a92c-636">`-rp|--reset-password-policy-id <ID>`– Resetování ID zásad hesla pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="9a92c-636">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="9a92c-637">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="9a92c-637">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="9a92c-638">`-ep|--edit-profile-policy-id <ID>`– Upravte ID zásad profilu pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="9a92c-638">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="9a92c-639">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="9a92c-639">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="9a92c-640">`--aad-instance <INSTANCE>`– Instance Azure Active Directory pro připojení.</span><span class="sxs-lookup"><span data-stu-id="9a92c-640">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="9a92c-641">Použijte s `SingleOrg` ověřováním nebo `MultiOrg` .</span><span class="sxs-lookup"><span data-stu-id="9a92c-641">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="9a92c-642">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-642">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="9a92c-643">`--client-id <ID>`– ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="9a92c-643">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="9a92c-644">Použijte s `IndividualB2C`ověřováním, `MultiOrg` `SingleOrg`nebo.</span><span class="sxs-lookup"><span data-stu-id="9a92c-644">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="9a92c-645">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-645">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="9a92c-646">`--domain <DOMAIN>`– Doména pro tenanta adresáře.</span><span class="sxs-lookup"><span data-stu-id="9a92c-646">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="9a92c-647">Použijte s `SingleOrg` ověřováním nebo `IndividualB2C` .</span><span class="sxs-lookup"><span data-stu-id="9a92c-647">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="9a92c-648">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-648">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="9a92c-649">`--tenant-id <ID>`– ID TenantId adresáře, ke kterému se má připojit.</span><span class="sxs-lookup"><span data-stu-id="9a92c-649">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="9a92c-650">Použijte s `SingleOrg` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="9a92c-650">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="9a92c-651">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-651">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="9a92c-652">`--callback-path <PATH>`– Cesta požadavku v základní cestě identifikátoru URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="9a92c-652">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="9a92c-653">Použijte s `SingleOrg` ověřováním nebo `IndividualB2C` .</span><span class="sxs-lookup"><span data-stu-id="9a92c-653">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="9a92c-654">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-654">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="9a92c-655">`-r|--org-read-access`– Povolí této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="9a92c-655">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="9a92c-656">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="9a92c-656">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="9a92c-657">`--exclude-launch-settings`– Vylučte z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="9a92c-657">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="9a92c-658">`--use-browserlink`-Zahrnuje BrowserLink do projektu.</span><span class="sxs-lookup"><span data-stu-id="9a92c-658">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="9a92c-659">`-uld|--use-local-db`-Určuje LocalDB by měl být použit místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="9a92c-659">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="9a92c-660">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="9a92c-660">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="9a92c-661">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="9a92c-661">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="9a92c-662">`--no-https`-Projekt nevyžaduje protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="9a92c-662">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="9a92c-663">`app.UseHsts`a `app.UseHttpsRedirection` nejsou přidány do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-663">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="9a92c-664">`Individual`Tato možnost platí pouze `IndividualB2C` `MultiOrg` v případě, že se nepoužívají, nebo.`SingleOrg`</span><span class="sxs-lookup"><span data-stu-id="9a92c-664">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="9a92c-665">**Page**</span><span class="sxs-lookup"><span data-stu-id="9a92c-665">**page**</span></span>

<span data-ttu-id="9a92c-666">`-na|--namespace <NAMESPACE_NAME>`– Obor názvů pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="9a92c-666">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="9a92c-667">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-667">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="9a92c-668">`-np|--no-pagemodel`-Vytvoří stránku bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="9a92c-668">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="9a92c-669">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="9a92c-669">**viewimports**</span></span>

<span data-ttu-id="9a92c-670">`-na|--namespace <NAMESPACE_NAME>`– Obor názvů pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="9a92c-670">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="9a92c-671">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-671">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="9a92c-672">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="9a92c-672">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="9a92c-673">**Konzola, úhlová, reakce, reactredux**</span><span class="sxs-lookup"><span data-stu-id="9a92c-673">**console, angular, react, reactredux**</span></span>

<span data-ttu-id="9a92c-674">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="9a92c-674">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="9a92c-675">**classlib**</span><span class="sxs-lookup"><span data-stu-id="9a92c-675">**classlib**</span></span>

<span data-ttu-id="9a92c-676">`-f|--framework <FRAMEWORK>`-Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="9a92c-676">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="9a92c-677">Hodnoty: `netcoreapp2.0` pro vytvoření knihovny tříd .NET Core nebo `netstandard2.0` pro vytvoření knihovny tříd .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="9a92c-677">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="9a92c-678">Výchozí hodnota je `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-678">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="9a92c-679">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="9a92c-679">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="9a92c-680">**MSTest, xUnit**</span><span class="sxs-lookup"><span data-stu-id="9a92c-680">**mstest, xunit**</span></span>

<span data-ttu-id="9a92c-681">`-p|--enable-pack`– Povolí balení pro projekt pomocí [sady dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="9a92c-681">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="9a92c-682">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="9a92c-682">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="9a92c-683">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="9a92c-683">**globaljson**</span></span>

<span data-ttu-id="9a92c-684">`--sdk-version <VERSION_NUMBER>`-Určuje verzi .NET Core SDK, která se má použít v souboru *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="9a92c-684">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="9a92c-685">**web**</span><span class="sxs-lookup"><span data-stu-id="9a92c-685">**web**</span></span>

<span data-ttu-id="9a92c-686">`--use-launch-settings`-Zahrnuje *launchSettings. JSON* ve výstupu vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="9a92c-686">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="9a92c-687">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="9a92c-687">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="9a92c-688">**webapi**</span><span class="sxs-lookup"><span data-stu-id="9a92c-688">**webapi**</span></span>

<span data-ttu-id="9a92c-689">`-au|--auth <AUTHENTICATION_TYPE>`– Typ ověřování, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="9a92c-689">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="9a92c-690">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="9a92c-690">The possible values are:</span></span>

- <span data-ttu-id="9a92c-691">`None`-Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="9a92c-691">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="9a92c-692">`IndividualB2C`-Jednotlivá ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="9a92c-692">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="9a92c-693">`SingleOrg`– Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="9a92c-693">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="9a92c-694">`Windows`– Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="9a92c-694">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="9a92c-695">`--aad-b2c-instance <INSTANCE>`– Instance Azure Active Directory B2C pro připojení.</span><span class="sxs-lookup"><span data-stu-id="9a92c-695">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="9a92c-696">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="9a92c-696">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="9a92c-697">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-697">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="9a92c-698">`-ssp|--susi-policy-id <ID>`– ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="9a92c-698">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="9a92c-699">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="9a92c-699">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="9a92c-700">`--aad-instance <INSTANCE>`– Instance Azure Active Directory pro připojení.</span><span class="sxs-lookup"><span data-stu-id="9a92c-700">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="9a92c-701">Použijte s `SingleOrg` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="9a92c-701">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="9a92c-702">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-702">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="9a92c-703">`--client-id <ID>`– ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="9a92c-703">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="9a92c-704">Použijte s `IndividualB2C` ověřováním nebo `SingleOrg` .</span><span class="sxs-lookup"><span data-stu-id="9a92c-704">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="9a92c-705">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-705">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="9a92c-706">`--domain <DOMAIN>`– Doména pro tenanta adresáře.</span><span class="sxs-lookup"><span data-stu-id="9a92c-706">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="9a92c-707">Použijte s `SingleOrg` ověřováním nebo `IndividualB2C` .</span><span class="sxs-lookup"><span data-stu-id="9a92c-707">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="9a92c-708">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-708">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="9a92c-709">`--tenant-id <ID>`– ID TenantId adresáře, ke kterému se má připojit.</span><span class="sxs-lookup"><span data-stu-id="9a92c-709">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="9a92c-710">Použijte s `SingleOrg` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="9a92c-710">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="9a92c-711">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-711">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="9a92c-712">`-r|--org-read-access`– Povolí této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="9a92c-712">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="9a92c-713">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="9a92c-713">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="9a92c-714">`--use-launch-settings`-Zahrnuje *launchSettings. JSON* ve výstupu vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="9a92c-714">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="9a92c-715">`-uld|--use-local-db`-Určuje LocalDB by měl být použit místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="9a92c-715">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="9a92c-716">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="9a92c-716">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="9a92c-717">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="9a92c-717">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="9a92c-718">**MVC, Razor**</span><span class="sxs-lookup"><span data-stu-id="9a92c-718">**mvc, razor**</span></span>

<span data-ttu-id="9a92c-719">`-au|--auth <AUTHENTICATION_TYPE>`– Typ ověřování, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="9a92c-719">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="9a92c-720">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="9a92c-720">The possible values are:</span></span>

- <span data-ttu-id="9a92c-721">`None`-Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="9a92c-721">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="9a92c-722">`Individual`-Individuální ověřování.</span><span class="sxs-lookup"><span data-stu-id="9a92c-722">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="9a92c-723">`IndividualB2C`-Jednotlivá ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="9a92c-723">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="9a92c-724">`SingleOrg`– Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="9a92c-724">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="9a92c-725">`MultiOrg`– Ověřování organizace pro více tenantů.</span><span class="sxs-lookup"><span data-stu-id="9a92c-725">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="9a92c-726">`Windows`– Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="9a92c-726">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="9a92c-727">`--aad-b2c-instance <INSTANCE>`– Instance Azure Active Directory B2C pro připojení.</span><span class="sxs-lookup"><span data-stu-id="9a92c-727">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="9a92c-728">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="9a92c-728">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="9a92c-729">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-729">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="9a92c-730">`-ssp|--susi-policy-id <ID>`– ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="9a92c-730">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="9a92c-731">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="9a92c-731">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="9a92c-732">`-rp|--reset-password-policy-id <ID>`– Resetování ID zásad hesla pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="9a92c-732">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="9a92c-733">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="9a92c-733">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="9a92c-734">`-ep|--edit-profile-policy-id <ID>`– Upravte ID zásad profilu pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="9a92c-734">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="9a92c-735">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="9a92c-735">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="9a92c-736">`--aad-instance <INSTANCE>`– Instance Azure Active Directory pro připojení.</span><span class="sxs-lookup"><span data-stu-id="9a92c-736">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="9a92c-737">Použijte s `SingleOrg` ověřováním nebo `MultiOrg` .</span><span class="sxs-lookup"><span data-stu-id="9a92c-737">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="9a92c-738">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-738">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="9a92c-739">`--client-id <ID>`– ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="9a92c-739">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="9a92c-740">Použijte s `IndividualB2C`ověřováním, `MultiOrg` `SingleOrg`nebo.</span><span class="sxs-lookup"><span data-stu-id="9a92c-740">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="9a92c-741">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-741">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="9a92c-742">`--domain <DOMAIN>`– Doména pro tenanta adresáře.</span><span class="sxs-lookup"><span data-stu-id="9a92c-742">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="9a92c-743">Použijte s `SingleOrg` ověřováním nebo `IndividualB2C` .</span><span class="sxs-lookup"><span data-stu-id="9a92c-743">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="9a92c-744">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-744">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="9a92c-745">`--tenant-id <ID>`– ID TenantId adresáře, ke kterému se má připojit.</span><span class="sxs-lookup"><span data-stu-id="9a92c-745">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="9a92c-746">Použijte s `SingleOrg` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="9a92c-746">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="9a92c-747">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-747">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="9a92c-748">`--callback-path <PATH>`– Cesta požadavku v základní cestě identifikátoru URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="9a92c-748">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="9a92c-749">Použijte s `SingleOrg` ověřováním nebo `IndividualB2C` .</span><span class="sxs-lookup"><span data-stu-id="9a92c-749">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="9a92c-750">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-750">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="9a92c-751">`-r|--org-read-access`– Povolí této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="9a92c-751">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="9a92c-752">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="9a92c-752">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="9a92c-753">`--use-launch-settings`-Zahrnuje *launchSettings. JSON* ve výstupu vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="9a92c-753">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="9a92c-754">`--use-browserlink`-Zahrnuje BrowserLink do projektu.</span><span class="sxs-lookup"><span data-stu-id="9a92c-754">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="9a92c-755">`-uld|--use-local-db`-Určuje LocalDB by měl být použit místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="9a92c-755">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="9a92c-756">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="9a92c-756">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="9a92c-757">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="9a92c-757">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="9a92c-758">**Page**</span><span class="sxs-lookup"><span data-stu-id="9a92c-758">**page**</span></span>

<span data-ttu-id="9a92c-759">`-na|--namespace <NAMESPACE_NAME>`– Obor názvů pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="9a92c-759">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="9a92c-760">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-760">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="9a92c-761">`-np|--no-pagemodel`-Vytvoří stránku bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="9a92c-761">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="9a92c-762">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="9a92c-762">**viewimports**</span></span>

<span data-ttu-id="9a92c-763">`-na|--namespace <NAMESPACE_NAME>`– Obor názvů pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="9a92c-763">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="9a92c-764">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-764">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="9a92c-765">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="9a92c-765">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="9a92c-766">**Konzola, xUnit, MSTest, web, WebApi**</span><span class="sxs-lookup"><span data-stu-id="9a92c-766">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="9a92c-767">`-f|--framework <FRAMEWORK>`-Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="9a92c-767">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="9a92c-768">Hodnoty: `netcoreapp1.0` nebo `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-768">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="9a92c-769">Výchozí hodnota je `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-769">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="9a92c-770">**classlib**</span><span class="sxs-lookup"><span data-stu-id="9a92c-770">**classlib**</span></span>

<span data-ttu-id="9a92c-771">`-f|--framework <FRAMEWORK>`-Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="9a92c-771">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="9a92c-772">Hodnoty: `netcoreapp1.0`, `netcoreapp1.1`, nebo `netstandard1.0` na `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-772">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="9a92c-773">Výchozí hodnota je `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-773">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="9a92c-774">**mvc**</span><span class="sxs-lookup"><span data-stu-id="9a92c-774">**mvc**</span></span>

<span data-ttu-id="9a92c-775">`-f|--framework <FRAMEWORK>`-Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="9a92c-775">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="9a92c-776">Hodnoty: `netcoreapp1.0` nebo `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-776">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="9a92c-777">Výchozí hodnota je `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-777">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="9a92c-778">`-au|--auth <AUTHENTICATION_TYPE>`– Typ ověřování, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="9a92c-778">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="9a92c-779">Hodnoty: `None` nebo `Individual`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-779">Values: `None` or `Individual`.</span></span> <span data-ttu-id="9a92c-780">Výchozí hodnota je `None`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-780">The default value is `None`.</span></span>

<span data-ttu-id="9a92c-781">`-uld|--use-local-db`– Určuje, jestli se místo SQLite použije LocalDB.</span><span class="sxs-lookup"><span data-stu-id="9a92c-781">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="9a92c-782">Hodnoty: `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-782">Values: `true` or `false`.</span></span> <span data-ttu-id="9a92c-783">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="9a92c-783">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="9a92c-784">Příklady</span><span class="sxs-lookup"><span data-stu-id="9a92c-784">Examples</span></span>

<span data-ttu-id="9a92c-785">Vytvořte projekt C# konzolové aplikace zadáním názvu šablony:</span><span class="sxs-lookup"><span data-stu-id="9a92c-785">Create a C# console application project by specifying the template name:</span></span>

`dotnet new "Console Application"`

<span data-ttu-id="9a92c-786">Vytvořte projekt F# konzolové aplikace v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="9a92c-786">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="9a92c-787">Vytvořit projekt knihovny tříd .NET Standard v zadaném adresáři (k dispozici pouze s .NET Core SDK 2,0 nebo novějšími verzemi):</span><span class="sxs-lookup"><span data-stu-id="9a92c-787">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="9a92c-788">Vytvoří nový projekt ASP.NET Core C# MVC v aktuálním adresáři bez ověřování:</span><span class="sxs-lookup"><span data-stu-id="9a92c-788">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="9a92c-789">Vytvořit nový projekt xUnit:</span><span class="sxs-lookup"><span data-stu-id="9a92c-789">Create a new xUnit project:</span></span>

`dotnet new xunit`

<span data-ttu-id="9a92c-790">Vypíše všechny šablony, které jsou k dispozici pro MVC:</span><span class="sxs-lookup"><span data-stu-id="9a92c-790">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="9a92c-791">Vypíše všechny šablony, které odpovídají podřetězci *My* .</span><span class="sxs-lookup"><span data-stu-id="9a92c-791">List all templates matching the *we* substring.</span></span> <span data-ttu-id="9a92c-792">Nebyla nalezena žádná přesná shoda, takže porovnávání dílčích řetězců se shoduje se sloupci krátkého názvu a názvu.</span><span class="sxs-lookup"><span data-stu-id="9a92c-792">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

`dotnet new we -l`

<span data-ttu-id="9a92c-793">Došlo k pokusu o vyvolání šablony, která odpovídá *NG*.</span><span class="sxs-lookup"><span data-stu-id="9a92c-793">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="9a92c-794">Pokud nelze určit jednu shodu, Seznamte se se šablonami, které jsou částečné shody.</span><span class="sxs-lookup"><span data-stu-id="9a92c-794">If a single match can't be determined, list the templates that are partial matches.</span></span>

`dotnet new ng`

<span data-ttu-id="9a92c-795">2,0 nainstalujte šablony aplikace s jednou stránkou pro ASP.NET Core (možnost příkazového řádku, která je dostupná jenom pro .NET Core SDK 1,1 a novější verze):</span><span class="sxs-lookup"><span data-stu-id="9a92c-795">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="9a92c-796">Vytvoří *Global. JSON* v aktuálním adresáři nastavení verze sady SDK na 2.0.0 (k dispozici pouze s .NET Core SDK 2,0 nebo novějšími verzemi):</span><span class="sxs-lookup"><span data-stu-id="9a92c-796">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="9a92c-797">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9a92c-797">See also</span></span>

- [<span data-ttu-id="9a92c-798">Vlastní šablony pro dotnet New</span><span class="sxs-lookup"><span data-stu-id="9a92c-798">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="9a92c-799">Vytvoření vlastní šablony pro dotnet new</span><span class="sxs-lookup"><span data-stu-id="9a92c-799">Create a custom template for dotnet new</span></span>](../tutorials/create-custom-template.md)
- [<span data-ttu-id="9a92c-800">dotnet/dotnet-Template-Samples – úložiště GitHub</span><span class="sxs-lookup"><span data-stu-id="9a92c-800">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="9a92c-801">Dostupné šablony pro dotnet New</span><span class="sxs-lookup"><span data-stu-id="9a92c-801">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
