---
title: dotnet – nový příkaz
description: Příkaz dotnet New vytvoří nové projekty .NET Core založené na zadané šabloně.
ms.date: 05/06/2019
ms.openlocfilehash: b61b5fd53f470c30b636026fa19ebfad834d6354
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117658"
---
# <a name="dotnet-new"></a><span data-ttu-id="5b84b-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="5b84b-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="5b84b-104">Name</span><span class="sxs-lookup"><span data-stu-id="5b84b-104">Name</span></span>

<span data-ttu-id="5b84b-105">`dotnet new`– Vytvoří nový projekt, konfigurační soubor nebo řešení na základě zadané šablony.</span><span class="sxs-lookup"><span data-stu-id="5b84b-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5b84b-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="5b84b-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="5b84b-107">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="5b84b-107">.NET Core 2.2</span></span>](#tab/netcore22)

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="5b84b-108">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="5b84b-108">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="5b84b-109">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="5b84b-109">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5b84b-110">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="5b84b-110">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="5b84b-111">Popis</span><span class="sxs-lookup"><span data-stu-id="5b84b-111">Description</span></span>

<span data-ttu-id="5b84b-112">`dotnet new` Příkaz nabízí pohodlný způsob, jak inicializovat platný projekt .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5b84b-112">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="5b84b-113">Příkaz volá [modul šablony](https://github.com/dotnet/templating) a vytvoří artefakty na disku na základě zadané šablony a možností.</span><span class="sxs-lookup"><span data-stu-id="5b84b-113">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="5b84b-114">Arguments</span><span class="sxs-lookup"><span data-stu-id="5b84b-114">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="5b84b-115">Šablona, která se má vytvořit při vyvolání příkazu</span><span class="sxs-lookup"><span data-stu-id="5b84b-115">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="5b84b-116">Každá šablona může mít konkrétní možnosti, které můžete předat.</span><span class="sxs-lookup"><span data-stu-id="5b84b-116">Each template might have specific options you can pass.</span></span> <span data-ttu-id="5b84b-117">Další informace najdete v tématu [Možnosti šablony](#template-options).</span><span class="sxs-lookup"><span data-stu-id="5b84b-117">For more information, see [Template options](#template-options).</span></span>

<span data-ttu-id="5b84b-118">Pokud hodnota není přesná shoda na textu v **šablonách** nebo ve sloupci **short name** , je v těchto dvou sloupcích provedena shoda podřetězce. `TEMPLATE`</span><span class="sxs-lookup"><span data-stu-id="5b84b-118">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column, a substring match is performed on those two columns.</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="5b84b-119">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="5b84b-119">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="5b84b-120">Příkaz obsahuje výchozí seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="5b84b-120">The command contains a default list of templates.</span></span> <span data-ttu-id="5b84b-121">Použijte `dotnet new -l` k získání seznamu dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="5b84b-121">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="5b84b-122">Následující tabulka obsahuje šablony, které jsou předinstalované s .NET Core SDK 2.2.100.</span><span class="sxs-lookup"><span data-stu-id="5b84b-122">The following table shows the templates that come pre-installed with the .NET Core SDK 2.2.100.</span></span> <span data-ttu-id="5b84b-123">Výchozí jazyk pro šablonu se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="5b84b-123">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="5b84b-124">Šablony</span><span class="sxs-lookup"><span data-stu-id="5b84b-124">Templates</span></span>                                    | <span data-ttu-id="5b84b-125">Krátký název</span><span class="sxs-lookup"><span data-stu-id="5b84b-125">Short Name</span></span>        | <span data-ttu-id="5b84b-126">Jazyk</span><span class="sxs-lookup"><span data-stu-id="5b84b-126">Language</span></span>     | <span data-ttu-id="5b84b-127">Značky</span><span class="sxs-lookup"><span data-stu-id="5b84b-127">Tags</span></span>                                  |
|----------------------------------------------|-------------------|--------------|---------------------------------------|
| <span data-ttu-id="5b84b-128">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="5b84b-128">Console Application</span></span>                          | `console`         | <span data-ttu-id="5b84b-129">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5b84b-129">[C#], F#, VB</span></span> | <span data-ttu-id="5b84b-130">Společná/konzola</span><span class="sxs-lookup"><span data-stu-id="5b84b-130">Common/Console</span></span>                        |
| <span data-ttu-id="5b84b-131">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="5b84b-131">Class library</span></span>                                | `classlib`        | <span data-ttu-id="5b84b-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5b84b-132">[C#], F#, VB</span></span> | <span data-ttu-id="5b84b-133">Společné/knihovny</span><span class="sxs-lookup"><span data-stu-id="5b84b-133">Common/Library</span></span>                        |
| <span data-ttu-id="5b84b-134">Projekt testu jednotek</span><span class="sxs-lookup"><span data-stu-id="5b84b-134">Unit Test Project</span></span>                            | `mstest`          | <span data-ttu-id="5b84b-135">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5b84b-135">[C#], F#, VB</span></span> | <span data-ttu-id="5b84b-136">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="5b84b-136">Test/MSTest</span></span>                           |
| <span data-ttu-id="5b84b-137">Projekt testů NUnit 3</span><span class="sxs-lookup"><span data-stu-id="5b84b-137">NUnit 3 Test Project</span></span>                         | `nunit`           | <span data-ttu-id="5b84b-138">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5b84b-138">[C#], F#, VB</span></span> | <span data-ttu-id="5b84b-139">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="5b84b-139">Test/NUnit</span></span>                            |
| <span data-ttu-id="5b84b-140">NUnit 3 položka testu</span><span class="sxs-lookup"><span data-stu-id="5b84b-140">NUnit 3 Test Item</span></span>                            | `nunit-test`      | <span data-ttu-id="5b84b-141">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5b84b-141">[C#], F#, VB</span></span> | <span data-ttu-id="5b84b-142">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="5b84b-142">Test/NUnit</span></span>                            |
| <span data-ttu-id="5b84b-143">Projekt testů xUnit</span><span class="sxs-lookup"><span data-stu-id="5b84b-143">xUnit Test Project</span></span>                           | `xunit`           | <span data-ttu-id="5b84b-144">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5b84b-144">[C#], F#, VB</span></span> | <span data-ttu-id="5b84b-145">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="5b84b-145">Test/xUnit</span></span>                            |
| <span data-ttu-id="5b84b-146">Stránka Razor</span><span class="sxs-lookup"><span data-stu-id="5b84b-146">Razor Page</span></span>                                   | `page`            | <span data-ttu-id="5b84b-147">[C#]</span><span class="sxs-lookup"><span data-stu-id="5b84b-147">[C#]</span></span>         | <span data-ttu-id="5b84b-148">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5b84b-148">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="5b84b-149">ViewImports MVC</span><span class="sxs-lookup"><span data-stu-id="5b84b-149">MVC ViewImports</span></span>                              | `viewimports`     | <span data-ttu-id="5b84b-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="5b84b-150">[C#]</span></span>         | <span data-ttu-id="5b84b-151">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5b84b-151">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="5b84b-152">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="5b84b-152">MVC ViewStart</span></span>                                | `viewstart`       | <span data-ttu-id="5b84b-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="5b84b-153">[C#]</span></span>         | <span data-ttu-id="5b84b-154">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5b84b-154">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="5b84b-155">ASP.NET Core prázdné</span><span class="sxs-lookup"><span data-stu-id="5b84b-155">ASP.NET Core Empty</span></span>                           | `web`             | <span data-ttu-id="5b84b-156">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="5b84b-156">[C#], F#</span></span>     | <span data-ttu-id="5b84b-157">Web/prázdné</span><span class="sxs-lookup"><span data-stu-id="5b84b-157">Web/Empty</span></span>                             |
| <span data-ttu-id="5b84b-158">ASP.NET Core webová aplikace (model-zobrazení-kontroler)</span><span class="sxs-lookup"><span data-stu-id="5b84b-158">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`             | <span data-ttu-id="5b84b-159">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="5b84b-159">[C#], F#</span></span>     | <span data-ttu-id="5b84b-160">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="5b84b-160">Web/MVC</span></span>                               |
| <span data-ttu-id="5b84b-161">ASP.NET Core webové aplikace</span><span class="sxs-lookup"><span data-stu-id="5b84b-161">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="5b84b-162">`webapp`, `razor`</span><span class="sxs-lookup"><span data-stu-id="5b84b-162">`webapp`, `razor`</span></span> | <span data-ttu-id="5b84b-163">[C#]</span><span class="sxs-lookup"><span data-stu-id="5b84b-163">[C#]</span></span>         | <span data-ttu-id="5b84b-164">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="5b84b-164">Web/MVC/Razor Pages</span></span>                   |
| <span data-ttu-id="5b84b-165">ASP.NET Core s úhlovým</span><span class="sxs-lookup"><span data-stu-id="5b84b-165">ASP.NET Core with Angular</span></span>                    | `angular`         | <span data-ttu-id="5b84b-166">[C#]</span><span class="sxs-lookup"><span data-stu-id="5b84b-166">[C#]</span></span>         | <span data-ttu-id="5b84b-167">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="5b84b-167">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="5b84b-168">ASP.NET Core s reagují. js</span><span class="sxs-lookup"><span data-stu-id="5b84b-168">ASP.NET Core with React.js</span></span>                   | `react`           | <span data-ttu-id="5b84b-169">[C#]</span><span class="sxs-lookup"><span data-stu-id="5b84b-169">[C#]</span></span>         | <span data-ttu-id="5b84b-170">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="5b84b-170">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="5b84b-171">ASP.NET Core s využitím reagují. js a Redux</span><span class="sxs-lookup"><span data-stu-id="5b84b-171">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`      | <span data-ttu-id="5b84b-172">[C#]</span><span class="sxs-lookup"><span data-stu-id="5b84b-172">[C#]</span></span>         | <span data-ttu-id="5b84b-173">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="5b84b-173">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="5b84b-174">Knihovna tříd Razor</span><span class="sxs-lookup"><span data-stu-id="5b84b-174">Razor Class Library</span></span>                          | `razorclasslib`   | <span data-ttu-id="5b84b-175">[C#]</span><span class="sxs-lookup"><span data-stu-id="5b84b-175">[C#]</span></span>         | <span data-ttu-id="5b84b-176">Knihovna tříd web/Razor/Library/Razor</span><span class="sxs-lookup"><span data-stu-id="5b84b-176">Web/Razor/Library/Razor Class Library</span></span> |
| <span data-ttu-id="5b84b-177">ASP.NET Core webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="5b84b-177">ASP.NET Core Web API</span></span>                         | `webapi`          | <span data-ttu-id="5b84b-178">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="5b84b-178">[C#], F#</span></span>     | <span data-ttu-id="5b84b-179">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="5b84b-179">Web/WebAPI</span></span>                            |
| <span data-ttu-id="5b84b-180">global.json file</span><span class="sxs-lookup"><span data-stu-id="5b84b-180">global.json file</span></span>                             | `globaljson`      |              | <span data-ttu-id="5b84b-181">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="5b84b-181">Config</span></span>                                |
| <span data-ttu-id="5b84b-182">Konfigurace NuGet</span><span class="sxs-lookup"><span data-stu-id="5b84b-182">NuGet Config</span></span>                                 | `nugetconfig`     |              | <span data-ttu-id="5b84b-183">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="5b84b-183">Config</span></span>                                |
| <span data-ttu-id="5b84b-184">Webová konfigurace</span><span class="sxs-lookup"><span data-stu-id="5b84b-184">Web Config</span></span>                                   | `webconfig`       |              | <span data-ttu-id="5b84b-185">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="5b84b-185">Config</span></span>                                |
| <span data-ttu-id="5b84b-186">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="5b84b-186">Solution File</span></span>                                | `sln`             |              | <span data-ttu-id="5b84b-187">Řešení</span><span class="sxs-lookup"><span data-stu-id="5b84b-187">Solution</span></span>                              |

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="5b84b-188">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="5b84b-188">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="5b84b-189">Příkaz obsahuje výchozí seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="5b84b-189">The command contains a default list of templates.</span></span> <span data-ttu-id="5b84b-190">Použijte `dotnet new -l` k získání seznamu dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="5b84b-190">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="5b84b-191">Následující tabulka obsahuje šablony, které jsou předinstalované s .NET Core SDK 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="5b84b-191">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="5b84b-192">Výchozí jazyk pro šablonu se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="5b84b-192">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="5b84b-193">Šablony</span><span class="sxs-lookup"><span data-stu-id="5b84b-193">Templates</span></span>                                    | <span data-ttu-id="5b84b-194">Krátký název</span><span class="sxs-lookup"><span data-stu-id="5b84b-194">Short Name</span></span>      | <span data-ttu-id="5b84b-195">Jazyk</span><span class="sxs-lookup"><span data-stu-id="5b84b-195">Language</span></span>     | <span data-ttu-id="5b84b-196">Značky</span><span class="sxs-lookup"><span data-stu-id="5b84b-196">Tags</span></span>                                  |
|----------------------------------------------|-----------------|--------------|---------------------------------------|
| <span data-ttu-id="5b84b-197">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="5b84b-197">Console Application</span></span>                          | `console`       | <span data-ttu-id="5b84b-198">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5b84b-198">[C#], F#, VB</span></span> | <span data-ttu-id="5b84b-199">Společná/konzola</span><span class="sxs-lookup"><span data-stu-id="5b84b-199">Common/Console</span></span>                        |
| <span data-ttu-id="5b84b-200">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="5b84b-200">Class library</span></span>                                | `classlib`      | <span data-ttu-id="5b84b-201">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5b84b-201">[C#], F#, VB</span></span> | <span data-ttu-id="5b84b-202">Společné/knihovny</span><span class="sxs-lookup"><span data-stu-id="5b84b-202">Common/Library</span></span>                        |
| <span data-ttu-id="5b84b-203">Projekt testu jednotek</span><span class="sxs-lookup"><span data-stu-id="5b84b-203">Unit Test Project</span></span>                            | `mstest`        | <span data-ttu-id="5b84b-204">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5b84b-204">[C#], F#, VB</span></span> | <span data-ttu-id="5b84b-205">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="5b84b-205">Test/MSTest</span></span>                           |
| <span data-ttu-id="5b84b-206">Projekt testů xUnit</span><span class="sxs-lookup"><span data-stu-id="5b84b-206">xUnit Test Project</span></span>                           | `xunit`         | <span data-ttu-id="5b84b-207">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5b84b-207">[C#], F#, VB</span></span> | <span data-ttu-id="5b84b-208">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="5b84b-208">Test/xUnit</span></span>                            |
| <span data-ttu-id="5b84b-209">Stránka Razor</span><span class="sxs-lookup"><span data-stu-id="5b84b-209">Razor Page</span></span>                                   | `page`          | <span data-ttu-id="5b84b-210">[C#]</span><span class="sxs-lookup"><span data-stu-id="5b84b-210">[C#]</span></span>         | <span data-ttu-id="5b84b-211">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5b84b-211">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="5b84b-212">ViewImports MVC</span><span class="sxs-lookup"><span data-stu-id="5b84b-212">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="5b84b-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="5b84b-213">[C#]</span></span>         | <span data-ttu-id="5b84b-214">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5b84b-214">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="5b84b-215">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="5b84b-215">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="5b84b-216">[C#]</span><span class="sxs-lookup"><span data-stu-id="5b84b-216">[C#]</span></span>         | <span data-ttu-id="5b84b-217">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5b84b-217">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="5b84b-218">ASP.NET Core prázdné</span><span class="sxs-lookup"><span data-stu-id="5b84b-218">ASP.NET Core Empty</span></span>                           | `web`           | <span data-ttu-id="5b84b-219">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="5b84b-219">[C#], F#</span></span>     | <span data-ttu-id="5b84b-220">Web/prázdné</span><span class="sxs-lookup"><span data-stu-id="5b84b-220">Web/Empty</span></span>                             |
| <span data-ttu-id="5b84b-221">ASP.NET Core webová aplikace (model-zobrazení-kontroler)</span><span class="sxs-lookup"><span data-stu-id="5b84b-221">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="5b84b-222">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="5b84b-222">[C#], F#</span></span>     | <span data-ttu-id="5b84b-223">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="5b84b-223">Web/MVC</span></span>                               |
| <span data-ttu-id="5b84b-224">ASP.NET Core webové aplikace</span><span class="sxs-lookup"><span data-stu-id="5b84b-224">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="5b84b-225">[C#]</span><span class="sxs-lookup"><span data-stu-id="5b84b-225">[C#]</span></span>         | <span data-ttu-id="5b84b-226">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="5b84b-226">Web/MVC/Razor Pages</span></span>                   |
| <span data-ttu-id="5b84b-227">ASP.NET Core s úhlovým</span><span class="sxs-lookup"><span data-stu-id="5b84b-227">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="5b84b-228">[C#]</span><span class="sxs-lookup"><span data-stu-id="5b84b-228">[C#]</span></span>         | <span data-ttu-id="5b84b-229">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="5b84b-229">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="5b84b-230">ASP.NET Core s reagují. js</span><span class="sxs-lookup"><span data-stu-id="5b84b-230">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="5b84b-231">[C#]</span><span class="sxs-lookup"><span data-stu-id="5b84b-231">[C#]</span></span>         | <span data-ttu-id="5b84b-232">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="5b84b-232">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="5b84b-233">ASP.NET Core s využitím reagují. js a Redux</span><span class="sxs-lookup"><span data-stu-id="5b84b-233">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="5b84b-234">[C#]</span><span class="sxs-lookup"><span data-stu-id="5b84b-234">[C#]</span></span>         | <span data-ttu-id="5b84b-235">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="5b84b-235">Web/MVC/SPA</span></span>                           | 
| <span data-ttu-id="5b84b-236">Knihovna tříd Razor</span><span class="sxs-lookup"><span data-stu-id="5b84b-236">Razor Class Library</span></span>                          | `razorclasslib` | <span data-ttu-id="5b84b-237">[C#]</span><span class="sxs-lookup"><span data-stu-id="5b84b-237">[C#]</span></span>         | <span data-ttu-id="5b84b-238">Knihovna tříd web/Razor/Library/Razor</span><span class="sxs-lookup"><span data-stu-id="5b84b-238">Web/Razor/Library/Razor Class Library</span></span> |
| <span data-ttu-id="5b84b-239">ASP.NET Core webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="5b84b-239">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="5b84b-240">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="5b84b-240">[C#], F#</span></span>     | <span data-ttu-id="5b84b-241">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="5b84b-241">Web/WebAPI</span></span>                            |
| <span data-ttu-id="5b84b-242">global.json file</span><span class="sxs-lookup"><span data-stu-id="5b84b-242">global.json file</span></span>                             | `globaljson`    |              | <span data-ttu-id="5b84b-243">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="5b84b-243">Config</span></span>                                |
| <span data-ttu-id="5b84b-244">Konfigurace NuGet</span><span class="sxs-lookup"><span data-stu-id="5b84b-244">NuGet Config</span></span>                                 | `nugetconfig`   |              | <span data-ttu-id="5b84b-245">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="5b84b-245">Config</span></span>                                |
| <span data-ttu-id="5b84b-246">Webová konfigurace</span><span class="sxs-lookup"><span data-stu-id="5b84b-246">Web Config</span></span>                                   | `webconfig`     |              | <span data-ttu-id="5b84b-247">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="5b84b-247">Config</span></span>                                |
| <span data-ttu-id="5b84b-248">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="5b84b-248">Solution File</span></span>                                | `sln`           |              | <span data-ttu-id="5b84b-249">Řešení</span><span class="sxs-lookup"><span data-stu-id="5b84b-249">Solution</span></span>                              |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="5b84b-250">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="5b84b-250">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="5b84b-251">Příkaz obsahuje výchozí seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="5b84b-251">The command contains a default list of templates.</span></span> <span data-ttu-id="5b84b-252">Použijte `dotnet new -l` k získání seznamu dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="5b84b-252">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="5b84b-253">Následující tabulka obsahuje šablony, které jsou předinstalované s .NET Core SDK 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="5b84b-253">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.0.</span></span> <span data-ttu-id="5b84b-254">Výchozí jazyk pro šablonu se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="5b84b-254">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="5b84b-255">Šablony</span><span class="sxs-lookup"><span data-stu-id="5b84b-255">Templates</span></span>                                    | <span data-ttu-id="5b84b-256">Krátký název</span><span class="sxs-lookup"><span data-stu-id="5b84b-256">Short Name</span></span>    | <span data-ttu-id="5b84b-257">Jazyk</span><span class="sxs-lookup"><span data-stu-id="5b84b-257">Language</span></span>     | <span data-ttu-id="5b84b-258">Značky</span><span class="sxs-lookup"><span data-stu-id="5b84b-258">Tags</span></span>                |
|----------------------------------------------|---------------|--------------|---------------------|
| <span data-ttu-id="5b84b-259">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="5b84b-259">Console Application</span></span>                          | `console`     | <span data-ttu-id="5b84b-260">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5b84b-260">[C#], F#, VB</span></span> | <span data-ttu-id="5b84b-261">Společná/konzola</span><span class="sxs-lookup"><span data-stu-id="5b84b-261">Common/Console</span></span>      |
| <span data-ttu-id="5b84b-262">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="5b84b-262">Class library</span></span>                                | `classlib`    | <span data-ttu-id="5b84b-263">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5b84b-263">[C#], F#, VB</span></span> | <span data-ttu-id="5b84b-264">Společné/knihovny</span><span class="sxs-lookup"><span data-stu-id="5b84b-264">Common/Library</span></span>      |
| <span data-ttu-id="5b84b-265">Projekt testu jednotek</span><span class="sxs-lookup"><span data-stu-id="5b84b-265">Unit Test Project</span></span>                            | `mstest`      | <span data-ttu-id="5b84b-266">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5b84b-266">[C#], F#, VB</span></span> | <span data-ttu-id="5b84b-267">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="5b84b-267">Test/MSTest</span></span>         |
| <span data-ttu-id="5b84b-268">Projekt testů xUnit</span><span class="sxs-lookup"><span data-stu-id="5b84b-268">xUnit Test Project</span></span>                           | `xunit`       | <span data-ttu-id="5b84b-269">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5b84b-269">[C#], F#, VB</span></span> | <span data-ttu-id="5b84b-270">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="5b84b-270">Test/xUnit</span></span>          |
| <span data-ttu-id="5b84b-271">ASP.NET Core prázdné</span><span class="sxs-lookup"><span data-stu-id="5b84b-271">ASP.NET Core Empty</span></span>                           | `web`         | <span data-ttu-id="5b84b-272">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="5b84b-272">[C#], F#</span></span>     | <span data-ttu-id="5b84b-273">Web/prázdné</span><span class="sxs-lookup"><span data-stu-id="5b84b-273">Web/Empty</span></span>           |
| <span data-ttu-id="5b84b-274">ASP.NET Core webová aplikace (model-zobrazení-kontroler)</span><span class="sxs-lookup"><span data-stu-id="5b84b-274">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="5b84b-275">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="5b84b-275">[C#], F#</span></span>     | <span data-ttu-id="5b84b-276">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="5b84b-276">Web/MVC</span></span>             |
| <span data-ttu-id="5b84b-277">ASP.NET Core webové aplikace</span><span class="sxs-lookup"><span data-stu-id="5b84b-277">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="5b84b-278">[C#]</span><span class="sxs-lookup"><span data-stu-id="5b84b-278">[C#]</span></span>         | <span data-ttu-id="5b84b-279">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="5b84b-279">Web/MVC/Razor Pages</span></span> |
| <span data-ttu-id="5b84b-280">ASP.NET Core s úhlovým</span><span class="sxs-lookup"><span data-stu-id="5b84b-280">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="5b84b-281">[C#]</span><span class="sxs-lookup"><span data-stu-id="5b84b-281">[C#]</span></span>         | <span data-ttu-id="5b84b-282">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="5b84b-282">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="5b84b-283">ASP.NET Core s reagují. js</span><span class="sxs-lookup"><span data-stu-id="5b84b-283">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="5b84b-284">[C#]</span><span class="sxs-lookup"><span data-stu-id="5b84b-284">[C#]</span></span>         | <span data-ttu-id="5b84b-285">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="5b84b-285">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="5b84b-286">ASP.NET Core s využitím reagují. js a Redux</span><span class="sxs-lookup"><span data-stu-id="5b84b-286">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="5b84b-287">[C#]</span><span class="sxs-lookup"><span data-stu-id="5b84b-287">[C#]</span></span>         | <span data-ttu-id="5b84b-288">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="5b84b-288">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="5b84b-289">ASP.NET Core webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="5b84b-289">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="5b84b-290">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="5b84b-290">[C#], F#</span></span>     | <span data-ttu-id="5b84b-291">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="5b84b-291">Web/WebAPI</span></span>          |
| <span data-ttu-id="5b84b-292">global.json file</span><span class="sxs-lookup"><span data-stu-id="5b84b-292">global.json file</span></span>                             | `globaljson`  |              | <span data-ttu-id="5b84b-293">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="5b84b-293">Config</span></span>              |
| <span data-ttu-id="5b84b-294">Konfigurace NuGet</span><span class="sxs-lookup"><span data-stu-id="5b84b-294">Nuget Config</span></span>                                 | `nugetconfig` |              | <span data-ttu-id="5b84b-295">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="5b84b-295">Config</span></span>              |
| <span data-ttu-id="5b84b-296">Webová konfigurace</span><span class="sxs-lookup"><span data-stu-id="5b84b-296">Web Config</span></span>                                   | `webconfig`   |              | <span data-ttu-id="5b84b-297">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="5b84b-297">Config</span></span>              |
| <span data-ttu-id="5b84b-298">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="5b84b-298">Solution File</span></span>                                | `sln`         |              | <span data-ttu-id="5b84b-299">Řešení</span><span class="sxs-lookup"><span data-stu-id="5b84b-299">Solution</span></span>            |
| <span data-ttu-id="5b84b-300">Stránka Razor</span><span class="sxs-lookup"><span data-stu-id="5b84b-300">Razor Page</span></span>                                   | `page`        |              | <span data-ttu-id="5b84b-301">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5b84b-301">Web/ASP.NET</span></span>         |
| <span data-ttu-id="5b84b-302">ViewImports MVC</span><span class="sxs-lookup"><span data-stu-id="5b84b-302">MVC ViewImports</span></span>                              | `viewimports` |              | <span data-ttu-id="5b84b-303">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5b84b-303">Web/ASP.NET</span></span>         |
| <span data-ttu-id="5b84b-304">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="5b84b-304">MVC ViewStart</span></span>                                | `viewstart`   |              | <span data-ttu-id="5b84b-305">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5b84b-305">Web/ASP.NET</span></span>         |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5b84b-306">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="5b84b-306">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="5b84b-307">Příkaz obsahuje výchozí seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="5b84b-307">The command contains a default list of templates.</span></span> <span data-ttu-id="5b84b-308">Použijte `dotnet new -all` k získání seznamu dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="5b84b-308">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="5b84b-309">Následující tabulka obsahuje šablony, které jsou předinstalované s .NET Core SDK 1.0.1.</span><span class="sxs-lookup"><span data-stu-id="5b84b-309">The following table shows the templates that come pre-installed with the .NET Core SDK 1.0.1.</span></span> <span data-ttu-id="5b84b-310">Výchozí jazyk pro šablonu se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="5b84b-310">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="5b84b-311">Šablony</span><span class="sxs-lookup"><span data-stu-id="5b84b-311">Templates</span></span>            | <span data-ttu-id="5b84b-312">Krátký název</span><span class="sxs-lookup"><span data-stu-id="5b84b-312">Short Name</span></span>    | <span data-ttu-id="5b84b-313">Jazyk</span><span class="sxs-lookup"><span data-stu-id="5b84b-313">Language</span></span> | <span data-ttu-id="5b84b-314">Značky</span><span class="sxs-lookup"><span data-stu-id="5b84b-314">Tags</span></span>           |
|----------------------|---------------|----------|----------------|
| <span data-ttu-id="5b84b-315">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="5b84b-315">Console Application</span></span>  | `console`     | <span data-ttu-id="5b84b-316">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="5b84b-316">[C#], F#</span></span> | <span data-ttu-id="5b84b-317">Společná/konzola</span><span class="sxs-lookup"><span data-stu-id="5b84b-317">Common/Console</span></span> |
| <span data-ttu-id="5b84b-318">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="5b84b-318">Class library</span></span>        | `classlib`    | <span data-ttu-id="5b84b-319">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="5b84b-319">[C#], F#</span></span> | <span data-ttu-id="5b84b-320">Společné/knihovny</span><span class="sxs-lookup"><span data-stu-id="5b84b-320">Common/Library</span></span> |
| <span data-ttu-id="5b84b-321">Projekt testu jednotek</span><span class="sxs-lookup"><span data-stu-id="5b84b-321">Unit Test Project</span></span>    | `mstest`      | <span data-ttu-id="5b84b-322">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="5b84b-322">[C#], F#</span></span> | <span data-ttu-id="5b84b-323">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="5b84b-323">Test/MSTest</span></span>    |
| <span data-ttu-id="5b84b-324">Projekt testů xUnit</span><span class="sxs-lookup"><span data-stu-id="5b84b-324">xUnit Test Project</span></span>   | `xunit`       | <span data-ttu-id="5b84b-325">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="5b84b-325">[C#], F#</span></span> | <span data-ttu-id="5b84b-326">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="5b84b-326">Test/xUnit</span></span>     |
| <span data-ttu-id="5b84b-327">ASP.NET Core prázdné</span><span class="sxs-lookup"><span data-stu-id="5b84b-327">ASP.NET Core Empty</span></span>   | `web`         | <span data-ttu-id="5b84b-328">[C#]</span><span class="sxs-lookup"><span data-stu-id="5b84b-328">[C#]</span></span>     | <span data-ttu-id="5b84b-329">Web/prázdné</span><span class="sxs-lookup"><span data-stu-id="5b84b-329">Web/Empty</span></span>      |
| <span data-ttu-id="5b84b-330">ASP.NET Core webové aplikace</span><span class="sxs-lookup"><span data-stu-id="5b84b-330">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="5b84b-331">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="5b84b-331">[C#], F#</span></span> | <span data-ttu-id="5b84b-332">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="5b84b-332">Web/MVC</span></span>        |
| <span data-ttu-id="5b84b-333">ASP.NET Core webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="5b84b-333">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="5b84b-334">[C#]</span><span class="sxs-lookup"><span data-stu-id="5b84b-334">[C#]</span></span>     | <span data-ttu-id="5b84b-335">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="5b84b-335">Web/WebAPI</span></span>     |
| <span data-ttu-id="5b84b-336">Konfigurace NuGet</span><span class="sxs-lookup"><span data-stu-id="5b84b-336">Nuget Config</span></span>         | `nugetconfig` |          | <span data-ttu-id="5b84b-337">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="5b84b-337">Config</span></span>         |
| <span data-ttu-id="5b84b-338">Webová konfigurace</span><span class="sxs-lookup"><span data-stu-id="5b84b-338">Web Config</span></span>           | `webconfig`   |          | <span data-ttu-id="5b84b-339">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="5b84b-339">Config</span></span>         |
| <span data-ttu-id="5b84b-340">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="5b84b-340">Solution File</span></span>        | `sln`         |          | <span data-ttu-id="5b84b-341">Řešení</span><span class="sxs-lookup"><span data-stu-id="5b84b-341">Solution</span></span>       |

---

## <a name="options"></a><span data-ttu-id="5b84b-342">Možnosti</span><span class="sxs-lookup"><span data-stu-id="5b84b-342">Options</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="5b84b-343">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="5b84b-343">.NET Core 2.2</span></span>](#tab/netcore22)

`--dry-run`

<span data-ttu-id="5b84b-344">Zobrazí souhrnné informace o tom, co se stane, pokud by došlo ke spuštění daného příkazu, pokud by to vedlo k vytvoření šablony.</span><span class="sxs-lookup"><span data-stu-id="5b84b-344">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span>

`--force`

<span data-ttu-id="5b84b-345">Vynutí vygenerování obsahu i v případě, že změní existující soubory.</span><span class="sxs-lookup"><span data-stu-id="5b84b-345">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="5b84b-346">To je nutné v případě, že výstupní adresář již obsahuje projekt.</span><span class="sxs-lookup"><span data-stu-id="5b84b-346">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="5b84b-347">Vytiskne nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="5b84b-347">Prints out help for the command.</span></span> <span data-ttu-id="5b84b-348">Dá se vyvolat pro `dotnet new` samotný příkaz nebo pro libovolnou šablonu, `dotnet new mvc --help`jako je například.</span><span class="sxs-lookup"><span data-stu-id="5b84b-348">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="5b84b-349">Nainstaluje zdroj nebo balíček šablony z `PATH` nebo `NUGET_ID` poskytnutého.</span><span class="sxs-lookup"><span data-stu-id="5b84b-349">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="5b84b-350">Pokud chcete nainstalovat předprodejní verzi balíčku šablony, je nutné zadat verzi ve formátu `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-350">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="5b84b-351">Ve výchozím nastavení `dotnet new` se \* předá verze, která představuje poslední stabilní verzi balíčku.</span><span class="sxs-lookup"><span data-stu-id="5b84b-351">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="5b84b-352">Podívejte se na příklad v části [Příklady](#examples) .</span><span class="sxs-lookup"><span data-stu-id="5b84b-352">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="5b84b-353">Informace o vytváření vlastních šablon najdete v tématu [vlastní šablony pro dotnet New](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="5b84b-353">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="5b84b-354">Vypíše seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="5b84b-354">Lists templates containing the specified name.</span></span> <span data-ttu-id="5b84b-355">Pokud je vyvoláno pro `dotnet new` příkaz, zobrazí seznam možných šablon dostupných pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="5b84b-355">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="5b84b-356">Například Pokud adresář již obsahuje projekt, nezobrazuje seznam všech šablon projektu.</span><span class="sxs-lookup"><span data-stu-id="5b84b-356">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="5b84b-357">Jazyk šablony, která se má vytvořit</span><span class="sxs-lookup"><span data-stu-id="5b84b-357">The language of the template to create.</span></span> <span data-ttu-id="5b84b-358">Přijatý jazyk se liší podle šablony (viz výchozí hodnoty v oddílu [argumenty](#arguments) ).</span><span class="sxs-lookup"><span data-stu-id="5b84b-358">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="5b84b-359">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="5b84b-359">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="5b84b-360">Některá prostředí jsou interpretována `#` jako speciální znak.</span><span class="sxs-lookup"><span data-stu-id="5b84b-360">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="5b84b-361">V těchto případech je nutné uvést hodnotu parametru jazyka, například `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-361">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="5b84b-362">Název vytvořeného výstupu.</span><span class="sxs-lookup"><span data-stu-id="5b84b-362">The name for the created output.</span></span> <span data-ttu-id="5b84b-363">Pokud název nezadáte, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="5b84b-363">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="5b84b-364">Určuje zdroj NuGet, který se použije při instalaci.</span><span class="sxs-lookup"><span data-stu-id="5b84b-364">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="5b84b-365">Umístění, do kterého se má vygenerovaný výstup umístit.</span><span class="sxs-lookup"><span data-stu-id="5b84b-365">Location to place the generated output.</span></span> <span data-ttu-id="5b84b-366">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="5b84b-366">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="5b84b-367">Filtruje šablony založené na dostupných typech.</span><span class="sxs-lookup"><span data-stu-id="5b84b-367">Filters templates based on available types.</span></span> <span data-ttu-id="5b84b-368">Předdefinované hodnoty jsou "projekt", "položka" nebo "jiné".</span><span class="sxs-lookup"><span data-stu-id="5b84b-368">Predefined values are "project", "item", or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="5b84b-369">Odinstaluje zdrojový nebo Template Pack na `PATH` nebo `NUGET_ID` poskytnutý.</span><span class="sxs-lookup"><span data-stu-id="5b84b-369">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="5b84b-370">Při vyloučení `<PATH|NUGET_ID>` hodnoty se zobrazí všechny aktuálně nainstalované sady šablon a jejich přidružené šablony.</span><span class="sxs-lookup"><span data-stu-id="5b84b-370">When excluding the `<PATH|NUGET_ID>` value, all currently installed template packs and their associated templates are displayed.</span></span>

> [!NOTE]
> <span data-ttu-id="5b84b-371">Chcete-li odinstalovat šablonu pomocí `PATH`nástroje, je nutné plně kvalifikovat cestu.</span><span class="sxs-lookup"><span data-stu-id="5b84b-371">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="5b84b-372">Například *C:/Users/\<User >/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z nadřazené složky to nebude.</span><span class="sxs-lookup"><span data-stu-id="5b84b-372">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="5b84b-373">Kromě toho Nezahrnovat koncové koncové lomítko adresáře na cestu k šabloně.</span><span class="sxs-lookup"><span data-stu-id="5b84b-373">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="5b84b-374">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="5b84b-374">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="5b84b-375">Vynutí vygenerování obsahu i v případě, že změní existující soubory.</span><span class="sxs-lookup"><span data-stu-id="5b84b-375">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="5b84b-376">To je nutné v případě, že výstupní adresář již obsahuje projekt.</span><span class="sxs-lookup"><span data-stu-id="5b84b-376">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="5b84b-377">Vytiskne nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="5b84b-377">Prints out help for the command.</span></span> <span data-ttu-id="5b84b-378">Dá se vyvolat pro `dotnet new` samotný příkaz nebo pro libovolnou šablonu, `dotnet new mvc --help`jako je například.</span><span class="sxs-lookup"><span data-stu-id="5b84b-378">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="5b84b-379">Nainstaluje zdroj nebo balíček šablony z `PATH` nebo `NUGET_ID` poskytnutého.</span><span class="sxs-lookup"><span data-stu-id="5b84b-379">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="5b84b-380">Pokud chcete nainstalovat předprodejní verzi balíčku šablony, je nutné zadat verzi ve formátu `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-380">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="5b84b-381">Ve výchozím nastavení `dotnet new` se \* předá verze, která představuje poslední stabilní verzi balíčku.</span><span class="sxs-lookup"><span data-stu-id="5b84b-381">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="5b84b-382">Podívejte se na příklad v části [Příklady](#examples) .</span><span class="sxs-lookup"><span data-stu-id="5b84b-382">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="5b84b-383">Informace o vytváření vlastních šablon najdete v tématu [vlastní šablony pro dotnet New](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="5b84b-383">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="5b84b-384">Vypíše seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="5b84b-384">Lists templates containing the specified name.</span></span> <span data-ttu-id="5b84b-385">Pokud je vyvoláno pro `dotnet new` příkaz, zobrazí seznam možných šablon dostupných pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="5b84b-385">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="5b84b-386">Například Pokud adresář již obsahuje projekt, nezobrazuje seznam všech šablon projektu.</span><span class="sxs-lookup"><span data-stu-id="5b84b-386">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="5b84b-387">Jazyk šablony, která se má vytvořit</span><span class="sxs-lookup"><span data-stu-id="5b84b-387">The language of the template to create.</span></span> <span data-ttu-id="5b84b-388">Přijatý jazyk se liší podle šablony (viz výchozí hodnoty v oddílu [argumenty](#arguments) ).</span><span class="sxs-lookup"><span data-stu-id="5b84b-388">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="5b84b-389">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="5b84b-389">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="5b84b-390">Některá prostředí jsou interpretována `#` jako speciální znak.</span><span class="sxs-lookup"><span data-stu-id="5b84b-390">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="5b84b-391">V těchto případech je nutné uvést hodnotu parametru jazyka, například `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-391">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="5b84b-392">Název vytvořeného výstupu.</span><span class="sxs-lookup"><span data-stu-id="5b84b-392">The name for the created output.</span></span> <span data-ttu-id="5b84b-393">Pokud název nezadáte, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="5b84b-393">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="5b84b-394">Určuje zdroj NuGet, který se použije při instalaci.</span><span class="sxs-lookup"><span data-stu-id="5b84b-394">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="5b84b-395">Umístění, do kterého se má vygenerovaný výstup umístit.</span><span class="sxs-lookup"><span data-stu-id="5b84b-395">Location to place the generated output.</span></span> <span data-ttu-id="5b84b-396">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="5b84b-396">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="5b84b-397">Filtruje šablony založené na dostupných typech.</span><span class="sxs-lookup"><span data-stu-id="5b84b-397">Filters templates based on available types.</span></span> <span data-ttu-id="5b84b-398">Předdefinované hodnoty jsou "projekt", "položka" nebo "jiné".</span><span class="sxs-lookup"><span data-stu-id="5b84b-398">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="5b84b-399">Odinstaluje zdrojový nebo Template Pack na `PATH` nebo `NUGET_ID` poskytnutý.</span><span class="sxs-lookup"><span data-stu-id="5b84b-399">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="5b84b-400">Chcete-li odinstalovat šablonu pomocí `PATH`nástroje, je nutné plně kvalifikovat cestu.</span><span class="sxs-lookup"><span data-stu-id="5b84b-400">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="5b84b-401">Například *C:/Users/\<User >/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z nadřazené složky to nebude.</span><span class="sxs-lookup"><span data-stu-id="5b84b-401">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="5b84b-402">Kromě toho Nezahrnovat koncové koncové lomítko adresáře na cestu k šabloně.</span><span class="sxs-lookup"><span data-stu-id="5b84b-402">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="5b84b-403">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="5b84b-403">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="5b84b-404">Vynutí vygenerování obsahu i v případě, že změní existující soubory.</span><span class="sxs-lookup"><span data-stu-id="5b84b-404">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="5b84b-405">To je nutné v případě, že výstupní adresář již obsahuje projekt.</span><span class="sxs-lookup"><span data-stu-id="5b84b-405">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="5b84b-406">Vytiskne nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="5b84b-406">Prints out help for the command.</span></span> <span data-ttu-id="5b84b-407">Dá se vyvolat pro `dotnet new` samotný příkaz nebo pro libovolnou šablonu, `dotnet new mvc --help`jako je například.</span><span class="sxs-lookup"><span data-stu-id="5b84b-407">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="5b84b-408">Nainstaluje zdroj nebo balíček šablony z `PATH` nebo `NUGET_ID` poskytnutého.</span><span class="sxs-lookup"><span data-stu-id="5b84b-408">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="5b84b-409">Pokud chcete nainstalovat předprodejní verzi balíčku šablony, je nutné zadat verzi ve formátu `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-409">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="5b84b-410">Ve výchozím nastavení `dotnet new` se \* předá verze, která představuje poslední stabilní verzi balíčku.</span><span class="sxs-lookup"><span data-stu-id="5b84b-410">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="5b84b-411">Podívejte se na příklad v části [Příklady](#examples) .</span><span class="sxs-lookup"><span data-stu-id="5b84b-411">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="5b84b-412">Informace o vytváření vlastních šablon najdete v tématu [vlastní šablony pro dotnet New](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="5b84b-412">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="5b84b-413">Vypíše seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="5b84b-413">Lists templates containing the specified name.</span></span> <span data-ttu-id="5b84b-414">Pokud je vyvoláno pro `dotnet new` příkaz, zobrazí seznam možných šablon dostupných pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="5b84b-414">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="5b84b-415">Například Pokud adresář již obsahuje projekt, nezobrazuje seznam všech šablon projektu.</span><span class="sxs-lookup"><span data-stu-id="5b84b-415">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="5b84b-416">Jazyk šablony, která se má vytvořit</span><span class="sxs-lookup"><span data-stu-id="5b84b-416">The language of the template to create.</span></span> <span data-ttu-id="5b84b-417">Přijatý jazyk se liší podle šablony (viz výchozí hodnoty v oddílu [argumenty](#arguments) ).</span><span class="sxs-lookup"><span data-stu-id="5b84b-417">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="5b84b-418">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="5b84b-418">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="5b84b-419">Některá prostředí jsou interpretována `#` jako speciální znak.</span><span class="sxs-lookup"><span data-stu-id="5b84b-419">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="5b84b-420">V těchto případech je nutné uvést hodnotu parametru jazyka, například `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-420">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="5b84b-421">Název vytvořeného výstupu.</span><span class="sxs-lookup"><span data-stu-id="5b84b-421">The name for the created output.</span></span> <span data-ttu-id="5b84b-422">Pokud název nezadáte, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="5b84b-422">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="5b84b-423">Umístění, do kterého se má vygenerovaný výstup umístit.</span><span class="sxs-lookup"><span data-stu-id="5b84b-423">Location to place the generated output.</span></span> <span data-ttu-id="5b84b-424">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="5b84b-424">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="5b84b-425">Filtruje šablony založené na dostupných typech.</span><span class="sxs-lookup"><span data-stu-id="5b84b-425">Filters templates based on available types.</span></span> <span data-ttu-id="5b84b-426">Předdefinované hodnoty jsou "projekt", "položka" nebo "jiné".</span><span class="sxs-lookup"><span data-stu-id="5b84b-426">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="5b84b-427">Odinstaluje zdrojový nebo Template Pack na `PATH` nebo `NUGET_ID` poskytnutý.</span><span class="sxs-lookup"><span data-stu-id="5b84b-427">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="5b84b-428">Chcete-li odinstalovat šablonu pomocí zdroje `PATH`, je nutné cestu plně kvalifikovat.</span><span class="sxs-lookup"><span data-stu-id="5b84b-428">To uninstall a template using a source `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="5b84b-429">Například *C:/Users/\<User >/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z nadřazené složky to nebude.</span><span class="sxs-lookup"><span data-stu-id="5b84b-429">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span> <span data-ttu-id="5b84b-430">Kromě toho Nezahrnovat koncové koncové lomítko adresáře na cestu k šabloně.</span><span class="sxs-lookup"><span data-stu-id="5b84b-430">Additionally, do not include a final terminating directory slash on your template path.</span></span>
> 
> <span data-ttu-id="5b84b-431">Pokud nemůžete určit `PATH` argument nebo `NUGET_ID` , který je potřeba k odinstalaci šablony, `dotnet new --uninstall` při spuštění bez argumentu se zobrazí seznam všech nainstalovaných šablon a argument, který je potřeba k jejich odinstalování.</span><span class="sxs-lookup"><span data-stu-id="5b84b-431">If you are unable to determine the `PATH` or `NUGET_ID` argument needed to uninstall a template, running `dotnet new --uninstall` without an argument will list all installed templates and the argument required to uninstall them.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5b84b-432">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="5b84b-432">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="5b84b-433">Zobrazí všechny šablony pro konkrétní typ projektu při spuštění v kontextu `dotnet new` samotného příkazu.</span><span class="sxs-lookup"><span data-stu-id="5b84b-433">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="5b84b-434">Při spuštění v souvislosti s konkrétní šablonou, `dotnet new web -all`jako je například, `-all` je interpretován jako příznak vytvoření vynucení.</span><span class="sxs-lookup"><span data-stu-id="5b84b-434">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="5b84b-435">To je nutné v případě, že výstupní adresář již obsahuje projekt.</span><span class="sxs-lookup"><span data-stu-id="5b84b-435">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="5b84b-436">Vytiskne nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="5b84b-436">Prints out help for the command.</span></span> <span data-ttu-id="5b84b-437">Dá se vyvolat pro `dotnet new` samotný příkaz nebo pro libovolnou šablonu, `dotnet new mvc --help`jako je například.</span><span class="sxs-lookup"><span data-stu-id="5b84b-437">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="5b84b-438">Vypíše seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="5b84b-438">Lists templates containing the specified name.</span></span> <span data-ttu-id="5b84b-439">Pokud je vyvoláno pro `dotnet new` příkaz, zobrazí seznam možných šablon dostupných pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="5b84b-439">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="5b84b-440">Například Pokud adresář již obsahuje projekt, nezobrazuje seznam všech šablon projektu.</span><span class="sxs-lookup"><span data-stu-id="5b84b-440">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="5b84b-441">Jazyk šablony, která se má vytvořit</span><span class="sxs-lookup"><span data-stu-id="5b84b-441">The language of the template to create.</span></span> <span data-ttu-id="5b84b-442">Přijatý jazyk se liší podle šablony (viz výchozí hodnoty v oddílu [argumenty](#arguments) ).</span><span class="sxs-lookup"><span data-stu-id="5b84b-442">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="5b84b-443">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="5b84b-443">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="5b84b-444">Některá prostředí jsou interpretována `#` jako speciální znak.</span><span class="sxs-lookup"><span data-stu-id="5b84b-444">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="5b84b-445">V těchto případech je nutné uvést hodnotu parametru jazyka, například `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-445">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="5b84b-446">Název vytvořeného výstupu.</span><span class="sxs-lookup"><span data-stu-id="5b84b-446">The name for the created output.</span></span> <span data-ttu-id="5b84b-447">Pokud název nezadáte, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="5b84b-447">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="5b84b-448">Umístění, do kterého se má vygenerovaný výstup umístit.</span><span class="sxs-lookup"><span data-stu-id="5b84b-448">Location to place the generated output.</span></span> <span data-ttu-id="5b84b-449">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="5b84b-449">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="5b84b-450">Možnosti šablony</span><span class="sxs-lookup"><span data-stu-id="5b84b-450">Template options</span></span>

<span data-ttu-id="5b84b-451">Každá šablona projektu může mít k dispozici další možnosti.</span><span class="sxs-lookup"><span data-stu-id="5b84b-451">Each project template may have additional options available.</span></span> <span data-ttu-id="5b84b-452">Základní šablony mají následující další možnosti:</span><span class="sxs-lookup"><span data-stu-id="5b84b-452">The core templates have the following additional options:</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="5b84b-453">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="5b84b-453">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="5b84b-454">**stromu**</span><span class="sxs-lookup"><span data-stu-id="5b84b-454">**console**</span></span>

<span data-ttu-id="5b84b-455">`--langVersion <VERSION_NUMBER>`-Nastaví `LangVersion` vlastnost v souboru vytvořeného projektu.</span><span class="sxs-lookup"><span data-stu-id="5b84b-455">`--langVersion <VERSION_NUMBER>` - Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="5b84b-456">Použijte `--langVersion 7.3` například k použití C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="5b84b-456">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="5b84b-457">Nepodporuje se pro F#.</span><span class="sxs-lookup"><span data-stu-id="5b84b-457">Not supported for F#.</span></span>

<span data-ttu-id="5b84b-458">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="5b84b-458">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5b84b-459">**Úhlová, reakce, reactredux**</span><span class="sxs-lookup"><span data-stu-id="5b84b-459">**angular, react, reactredux**</span></span>

<span data-ttu-id="5b84b-460">`--exclude-launch-settings`– Vylučte z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="5b84b-460">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="5b84b-461">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="5b84b-461">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5b84b-462">`--no-https`-Projekt nevyžaduje protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5b84b-462">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="5b84b-463">Tato možnost se vztahuje jenom `IndividualAuth` na `OrganizationalAuth` to, jestli se nepoužívají.</span><span class="sxs-lookup"><span data-stu-id="5b84b-463">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="5b84b-464">**razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="5b84b-464">**razorclasslib**</span></span>

<span data-ttu-id="5b84b-465">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="5b84b-465">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5b84b-466">**classlib**</span><span class="sxs-lookup"><span data-stu-id="5b84b-466">**classlib**</span></span>

<span data-ttu-id="5b84b-467">`-f|--framework <FRAMEWORK>`-Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="5b84b-467">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="5b84b-468">Hodnoty: `netcoreapp2.2` pro vytvoření knihovny tříd .NET Core nebo `netstandard2.0` pro vytvoření knihovny tříd .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="5b84b-468">Values: `netcoreapp2.2` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="5b84b-469">Výchozí hodnota je `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-469">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="5b84b-470">`--langVersion <VERSION_NUMBER>`-Nastaví `LangVersion` vlastnost v souboru vytvořeného projektu.</span><span class="sxs-lookup"><span data-stu-id="5b84b-470">`--langVersion <VERSION_NUMBER>` - Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="5b84b-471">Použijte `--langVersion 7.3` například k použití C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="5b84b-471">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="5b84b-472">Nepodporuje se pro F#.</span><span class="sxs-lookup"><span data-stu-id="5b84b-472">Not supported for F#.</span></span>

<span data-ttu-id="5b84b-473">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="5b84b-473">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5b84b-474">**MSTest, xUnit**</span><span class="sxs-lookup"><span data-stu-id="5b84b-474">**mstest, xunit**</span></span>

<span data-ttu-id="5b84b-475">`-p|--enable-pack`– Povolí balení pro projekt pomocí [sady dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="5b84b-475">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="5b84b-476">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="5b84b-476">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5b84b-477">**nunit**</span><span class="sxs-lookup"><span data-stu-id="5b84b-477">**nunit**</span></span>

<span data-ttu-id="5b84b-478">`-f|--framework <FRAMEWORK>`-Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="5b84b-478">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="5b84b-479">Výchozí hodnota je `netcoreapp2.1`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-479">The default value is `netcoreapp2.1`.</span></span>

<span data-ttu-id="5b84b-480">`-p|--enable-pack`– Povolí balení pro projekt pomocí [sady dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="5b84b-480">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="5b84b-481">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="5b84b-481">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5b84b-482">**Page**</span><span class="sxs-lookup"><span data-stu-id="5b84b-482">**page**</span></span>

<span data-ttu-id="5b84b-483">`-na|--namespace <NAMESPACE_NAME>`– Obor názvů pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="5b84b-483">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="5b84b-484">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-484">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="5b84b-485">`-np|--no-pagemodel`-Vytvoří stránku bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="5b84b-485">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="5b84b-486">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="5b84b-486">**viewimports**</span></span>

<span data-ttu-id="5b84b-487">`-na|--namespace <NAMESPACE_NAME>`– Obor názvů pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="5b84b-487">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="5b84b-488">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-488">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="5b84b-489">**web**</span><span class="sxs-lookup"><span data-stu-id="5b84b-489">**web**</span></span>

<span data-ttu-id="5b84b-490">`--exclude-launch-settings`– Vylučte z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="5b84b-490">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="5b84b-491">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="5b84b-491">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5b84b-492">`--no-https`-Projekt nevyžaduje protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5b84b-492">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="5b84b-493">Tato možnost se vztahuje jenom `IndividualAuth` na `OrganizationalAuth` to, jestli se nepoužívají.</span><span class="sxs-lookup"><span data-stu-id="5b84b-493">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="5b84b-494">**mvc, webapp**</span><span class="sxs-lookup"><span data-stu-id="5b84b-494">**mvc, webapp**</span></span>

<span data-ttu-id="5b84b-495">`-au|--auth <AUTHENTICATION_TYPE>`– Typ ověřování, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="5b84b-495">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="5b84b-496">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="5b84b-496">The possible values are:</span></span>

- <span data-ttu-id="5b84b-497">`None`-Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="5b84b-497">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="5b84b-498">`Individual`-Individuální ověřování.</span><span class="sxs-lookup"><span data-stu-id="5b84b-498">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="5b84b-499">`IndividualB2C`-Jednotlivá ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="5b84b-499">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="5b84b-500">`SingleOrg`– Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="5b84b-500">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="5b84b-501">`MultiOrg`– Ověřování organizace pro více tenantů.</span><span class="sxs-lookup"><span data-stu-id="5b84b-501">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="5b84b-502">`Windows`– Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5b84b-502">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="5b84b-503">`--aad-b2c-instance <INSTANCE>`– Instance Azure Active Directory B2C pro připojení.</span><span class="sxs-lookup"><span data-stu-id="5b84b-503">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="5b84b-504">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="5b84b-504">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="5b84b-505">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-505">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="5b84b-506">`-ssp|--susi-policy-id <ID>`– ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="5b84b-506">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="5b84b-507">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="5b84b-507">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5b84b-508">`-rp|--reset-password-policy-id <ID>`– Resetování ID zásad hesla pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="5b84b-508">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="5b84b-509">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="5b84b-509">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5b84b-510">`-ep|--edit-profile-policy-id <ID>`– Upravte ID zásad profilu pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="5b84b-510">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="5b84b-511">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="5b84b-511">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5b84b-512">`--aad-instance <INSTANCE>`– Instance Azure Active Directory pro připojení.</span><span class="sxs-lookup"><span data-stu-id="5b84b-512">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="5b84b-513">Použijte s `SingleOrg` ověřováním nebo `MultiOrg` .</span><span class="sxs-lookup"><span data-stu-id="5b84b-513">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="5b84b-514">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-514">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="5b84b-515">`--client-id <ID>`– ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="5b84b-515">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="5b84b-516">Použijte s `IndividualB2C`ověřováním, `MultiOrg` `SingleOrg`nebo.</span><span class="sxs-lookup"><span data-stu-id="5b84b-516">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="5b84b-517">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-517">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="5b84b-518">`--domain <DOMAIN>`– Doména pro tenanta adresáře.</span><span class="sxs-lookup"><span data-stu-id="5b84b-518">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="5b84b-519">Použijte s `SingleOrg` ověřováním nebo `IndividualB2C` .</span><span class="sxs-lookup"><span data-stu-id="5b84b-519">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="5b84b-520">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-520">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="5b84b-521">`--tenant-id <ID>`– ID TenantId adresáře, ke kterému se má připojit.</span><span class="sxs-lookup"><span data-stu-id="5b84b-521">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="5b84b-522">Použijte s `SingleOrg` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="5b84b-522">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="5b84b-523">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-523">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="5b84b-524">`--callback-path <PATH>`– Cesta požadavku v základní cestě identifikátoru URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="5b84b-524">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="5b84b-525">Použijte s `SingleOrg` ověřováním nebo `IndividualB2C` .</span><span class="sxs-lookup"><span data-stu-id="5b84b-525">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="5b84b-526">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-526">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="5b84b-527">`-r|--org-read-access`– Povolí této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="5b84b-527">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="5b84b-528">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="5b84b-528">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="5b84b-529">`--exclude-launch-settings`– Vylučte z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="5b84b-529">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="5b84b-530">`--no-https`-Projekt nevyžaduje protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5b84b-530">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="5b84b-531">`app.UseHsts`a `app.UseHttpsRedirection` nejsou přidány do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-531">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="5b84b-532">`Individual`Tato možnost platí pouze `IndividualB2C` `MultiOrg` v případě, že se nepoužívají, nebo.`SingleOrg`</span><span class="sxs-lookup"><span data-stu-id="5b84b-532">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="5b84b-533">`-uld|--use-local-db`-Určuje LocalDB by měl být použit místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="5b84b-533">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="5b84b-534">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="5b84b-534">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5b84b-535">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="5b84b-535">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5b84b-536">**webapi**</span><span class="sxs-lookup"><span data-stu-id="5b84b-536">**webapi**</span></span>

<span data-ttu-id="5b84b-537">`-au|--auth <AUTHENTICATION_TYPE>`– Typ ověřování, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="5b84b-537">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="5b84b-538">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="5b84b-538">The possible values are:</span></span>

- <span data-ttu-id="5b84b-539">`None`-Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="5b84b-539">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="5b84b-540">`IndividualB2C`-Jednotlivá ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="5b84b-540">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="5b84b-541">`SingleOrg`– Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="5b84b-541">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="5b84b-542">`Windows`– Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5b84b-542">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="5b84b-543">`--aad-b2c-instance <INSTANCE>`– Instance Azure Active Directory B2C pro připojení.</span><span class="sxs-lookup"><span data-stu-id="5b84b-543">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="5b84b-544">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="5b84b-544">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="5b84b-545">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-545">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="5b84b-546">`-ssp|--susi-policy-id <ID>`– ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="5b84b-546">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="5b84b-547">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="5b84b-547">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5b84b-548">`--aad-instance <INSTANCE>`– Instance Azure Active Directory pro připojení.</span><span class="sxs-lookup"><span data-stu-id="5b84b-548">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="5b84b-549">Použijte s `SingleOrg` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="5b84b-549">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="5b84b-550">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-550">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="5b84b-551">`--client-id <ID>`– ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="5b84b-551">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="5b84b-552">Použijte s `IndividualB2C` ověřováním nebo `SingleOrg` .</span><span class="sxs-lookup"><span data-stu-id="5b84b-552">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="5b84b-553">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-553">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="5b84b-554">`--domain <DOMAIN>`– Doména pro tenanta adresáře.</span><span class="sxs-lookup"><span data-stu-id="5b84b-554">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="5b84b-555">Použijte s `SingleOrg` ověřováním nebo `IndividualB2C` .</span><span class="sxs-lookup"><span data-stu-id="5b84b-555">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="5b84b-556">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-556">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="5b84b-557">`--tenant-id <ID>`– ID TenantId adresáře, ke kterému se má připojit.</span><span class="sxs-lookup"><span data-stu-id="5b84b-557">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="5b84b-558">Použijte s `SingleOrg` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="5b84b-558">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="5b84b-559">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-559">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="5b84b-560">`-r|--org-read-access`– Povolí této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="5b84b-560">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="5b84b-561">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="5b84b-561">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="5b84b-562">`--exclude-launch-settings`– Vylučte z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="5b84b-562">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="5b84b-563">`--no-https`-Projekt nevyžaduje protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5b84b-563">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="5b84b-564">`app.UseHsts`a `app.UseHttpsRedirection` nejsou přidány do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-564">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="5b84b-565">`Individual`Tato možnost platí pouze `IndividualB2C` `MultiOrg` v případě, že se nepoužívají, nebo.`SingleOrg`</span><span class="sxs-lookup"><span data-stu-id="5b84b-565">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="5b84b-566">`-uld|--use-local-db`-Určuje LocalDB by měl být použit místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="5b84b-566">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="5b84b-567">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="5b84b-567">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5b84b-568">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="5b84b-568">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5b84b-569">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="5b84b-569">**globaljson**</span></span>

<span data-ttu-id="5b84b-570">`--sdk-version <VERSION_NUMBER>`-Určuje verzi .NET Core SDK, která se má použít v souboru *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="5b84b-570">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="5b84b-571">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="5b84b-571">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="5b84b-572">**Konzola, úhlová, reakce, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="5b84b-572">**console, angular, react, reactredux, razorclasslib**</span></span>

<span data-ttu-id="5b84b-573">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="5b84b-573">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5b84b-574">**classlib**</span><span class="sxs-lookup"><span data-stu-id="5b84b-574">**classlib**</span></span>

<span data-ttu-id="5b84b-575">`-f|--framework <FRAMEWORK>`-Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="5b84b-575">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="5b84b-576">Hodnoty: `netcoreapp2.1` pro vytvoření knihovny tříd .NET Core nebo `netstandard2.0` pro vytvoření knihovny tříd .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="5b84b-576">Values: `netcoreapp2.1` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="5b84b-577">Výchozí hodnota je `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-577">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="5b84b-578">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="5b84b-578">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5b84b-579">**MSTest, xUnit**</span><span class="sxs-lookup"><span data-stu-id="5b84b-579">**mstest, xunit**</span></span>

<span data-ttu-id="5b84b-580">`-p|--enable-pack`– Povolí balení pro projekt pomocí [sady dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="5b84b-580">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="5b84b-581">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="5b84b-581">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5b84b-582">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="5b84b-582">**globaljson**</span></span>

<span data-ttu-id="5b84b-583">`--sdk-version <VERSION_NUMBER>`-Určuje verzi .NET Core SDK, která se má použít v souboru *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="5b84b-583">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="5b84b-584">**web**</span><span class="sxs-lookup"><span data-stu-id="5b84b-584">**web**</span></span>

<span data-ttu-id="5b84b-585">`--exclude-launch-settings`– Vylučte z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="5b84b-585">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="5b84b-586">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="5b84b-586">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5b84b-587">`--no-https`-Projekt nevyžaduje protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5b84b-587">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="5b84b-588">Tato možnost se vztahuje jenom `IndividualAuth` na `OrganizationalAuth` to, jestli se nepoužívají.</span><span class="sxs-lookup"><span data-stu-id="5b84b-588">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="5b84b-589">**webapi**</span><span class="sxs-lookup"><span data-stu-id="5b84b-589">**webapi**</span></span>

<span data-ttu-id="5b84b-590">`-au|--auth <AUTHENTICATION_TYPE>`– Typ ověřování, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="5b84b-590">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="5b84b-591">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="5b84b-591">The possible values are:</span></span>

- <span data-ttu-id="5b84b-592">`None`-Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="5b84b-592">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="5b84b-593">`IndividualB2C`-Jednotlivá ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="5b84b-593">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="5b84b-594">`SingleOrg`– Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="5b84b-594">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="5b84b-595">`Windows`– Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5b84b-595">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="5b84b-596">`--aad-b2c-instance <INSTANCE>`– Instance Azure Active Directory B2C pro připojení.</span><span class="sxs-lookup"><span data-stu-id="5b84b-596">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="5b84b-597">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="5b84b-597">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="5b84b-598">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-598">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="5b84b-599">`-ssp|--susi-policy-id <ID>`– ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="5b84b-599">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="5b84b-600">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="5b84b-600">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5b84b-601">`--aad-instance <INSTANCE>`– Instance Azure Active Directory pro připojení.</span><span class="sxs-lookup"><span data-stu-id="5b84b-601">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="5b84b-602">Použijte s `SingleOrg` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="5b84b-602">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="5b84b-603">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-603">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="5b84b-604">`--client-id <ID>`– ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="5b84b-604">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="5b84b-605">Použijte s `IndividualB2C` ověřováním nebo `SingleOrg` .</span><span class="sxs-lookup"><span data-stu-id="5b84b-605">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="5b84b-606">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-606">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="5b84b-607">`--domain <DOMAIN>`– Doména pro tenanta adresáře.</span><span class="sxs-lookup"><span data-stu-id="5b84b-607">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="5b84b-608">Použijte s `SingleOrg` ověřováním nebo `IndividualB2C` .</span><span class="sxs-lookup"><span data-stu-id="5b84b-608">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="5b84b-609">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-609">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="5b84b-610">`--tenant-id <ID>`– ID TenantId adresáře, ke kterému se má připojit.</span><span class="sxs-lookup"><span data-stu-id="5b84b-610">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="5b84b-611">Použijte s `SingleOrg` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="5b84b-611">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="5b84b-612">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-612">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="5b84b-613">`-r|--org-read-access`– Povolí této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="5b84b-613">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="5b84b-614">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="5b84b-614">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="5b84b-615">`--exclude-launch-settings`– Vylučte z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="5b84b-615">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="5b84b-616">`-uld|--use-local-db`-Určuje LocalDB by měl být použit místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="5b84b-616">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="5b84b-617">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="5b84b-617">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5b84b-618">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="5b84b-618">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5b84b-619">`--no-https`-Projekt nevyžaduje protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5b84b-619">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="5b84b-620">`app.UseHsts`a `app.UseHttpsRedirection` nejsou přidány do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-620">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="5b84b-621">`Individual`Tato možnost platí pouze `IndividualB2C` `MultiOrg` v případě, že se nepoužívají, nebo.`SingleOrg`</span><span class="sxs-lookup"><span data-stu-id="5b84b-621">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="5b84b-622">**MVC, Razor**</span><span class="sxs-lookup"><span data-stu-id="5b84b-622">**mvc, razor**</span></span>

<span data-ttu-id="5b84b-623">`-au|--auth <AUTHENTICATION_TYPE>`– Typ ověřování, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="5b84b-623">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="5b84b-624">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="5b84b-624">The possible values are:</span></span>

- <span data-ttu-id="5b84b-625">`None`-Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="5b84b-625">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="5b84b-626">`Individual`-Individuální ověřování.</span><span class="sxs-lookup"><span data-stu-id="5b84b-626">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="5b84b-627">`IndividualB2C`-Jednotlivá ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="5b84b-627">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="5b84b-628">`SingleOrg`– Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="5b84b-628">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="5b84b-629">`MultiOrg`– Ověřování organizace pro více tenantů.</span><span class="sxs-lookup"><span data-stu-id="5b84b-629">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="5b84b-630">`Windows`– Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5b84b-630">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="5b84b-631">`--aad-b2c-instance <INSTANCE>`– Instance Azure Active Directory B2C pro připojení.</span><span class="sxs-lookup"><span data-stu-id="5b84b-631">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="5b84b-632">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="5b84b-632">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="5b84b-633">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-633">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="5b84b-634">`-ssp|--susi-policy-id <ID>`– ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="5b84b-634">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="5b84b-635">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="5b84b-635">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5b84b-636">`-rp|--reset-password-policy-id <ID>`– Resetování ID zásad hesla pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="5b84b-636">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="5b84b-637">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="5b84b-637">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5b84b-638">`-ep|--edit-profile-policy-id <ID>`– Upravte ID zásad profilu pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="5b84b-638">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="5b84b-639">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="5b84b-639">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5b84b-640">`--aad-instance <INSTANCE>`– Instance Azure Active Directory pro připojení.</span><span class="sxs-lookup"><span data-stu-id="5b84b-640">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="5b84b-641">Použijte s `SingleOrg` ověřováním nebo `MultiOrg` .</span><span class="sxs-lookup"><span data-stu-id="5b84b-641">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="5b84b-642">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-642">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="5b84b-643">`--client-id <ID>`– ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="5b84b-643">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="5b84b-644">Použijte s `IndividualB2C`ověřováním, `MultiOrg` `SingleOrg`nebo.</span><span class="sxs-lookup"><span data-stu-id="5b84b-644">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="5b84b-645">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-645">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="5b84b-646">`--domain <DOMAIN>`– Doména pro tenanta adresáře.</span><span class="sxs-lookup"><span data-stu-id="5b84b-646">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="5b84b-647">Použijte s `SingleOrg` ověřováním nebo `IndividualB2C` .</span><span class="sxs-lookup"><span data-stu-id="5b84b-647">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="5b84b-648">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-648">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="5b84b-649">`--tenant-id <ID>`– ID TenantId adresáře, ke kterému se má připojit.</span><span class="sxs-lookup"><span data-stu-id="5b84b-649">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="5b84b-650">Použijte s `SingleOrg` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="5b84b-650">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="5b84b-651">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-651">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="5b84b-652">`--callback-path <PATH>`– Cesta požadavku v základní cestě identifikátoru URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="5b84b-652">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="5b84b-653">Použijte s `SingleOrg` ověřováním nebo `IndividualB2C` .</span><span class="sxs-lookup"><span data-stu-id="5b84b-653">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="5b84b-654">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-654">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="5b84b-655">`-r|--org-read-access`– Povolí této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="5b84b-655">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="5b84b-656">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="5b84b-656">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="5b84b-657">`--exclude-launch-settings`– Vylučte z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="5b84b-657">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="5b84b-658">`--use-browserlink`-Zahrnuje BrowserLink do projektu.</span><span class="sxs-lookup"><span data-stu-id="5b84b-658">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="5b84b-659">`-uld|--use-local-db`-Určuje LocalDB by měl být použit místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="5b84b-659">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="5b84b-660">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="5b84b-660">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5b84b-661">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="5b84b-661">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5b84b-662">`--no-https`-Projekt nevyžaduje protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5b84b-662">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="5b84b-663">`app.UseHsts`a `app.UseHttpsRedirection` nejsou přidány do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-663">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="5b84b-664">`Individual`Tato možnost platí pouze `IndividualB2C` `MultiOrg` v případě, že se nepoužívají, nebo.`SingleOrg`</span><span class="sxs-lookup"><span data-stu-id="5b84b-664">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="5b84b-665">**Page**</span><span class="sxs-lookup"><span data-stu-id="5b84b-665">**page**</span></span>

<span data-ttu-id="5b84b-666">`-na|--namespace <NAMESPACE_NAME>`– Obor názvů pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="5b84b-666">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="5b84b-667">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-667">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="5b84b-668">`-np|--no-pagemodel`-Vytvoří stránku bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="5b84b-668">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="5b84b-669">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="5b84b-669">**viewimports**</span></span>

<span data-ttu-id="5b84b-670">`-na|--namespace <NAMESPACE_NAME>`– Obor názvů pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="5b84b-670">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="5b84b-671">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-671">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="5b84b-672">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="5b84b-672">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="5b84b-673">**Konzola, úhlová, reakce, reactredux**</span><span class="sxs-lookup"><span data-stu-id="5b84b-673">**console, angular, react, reactredux**</span></span>

<span data-ttu-id="5b84b-674">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="5b84b-674">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5b84b-675">**classlib**</span><span class="sxs-lookup"><span data-stu-id="5b84b-675">**classlib**</span></span>

<span data-ttu-id="5b84b-676">`-f|--framework <FRAMEWORK>`-Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="5b84b-676">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="5b84b-677">Hodnoty: `netcoreapp2.0` pro vytvoření knihovny tříd .NET Core nebo `netstandard2.0` pro vytvoření knihovny tříd .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="5b84b-677">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="5b84b-678">Výchozí hodnota je `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-678">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="5b84b-679">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="5b84b-679">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5b84b-680">**MSTest, xUnit**</span><span class="sxs-lookup"><span data-stu-id="5b84b-680">**mstest, xunit**</span></span>

<span data-ttu-id="5b84b-681">`-p|--enable-pack`– Povolí balení pro projekt pomocí [sady dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="5b84b-681">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="5b84b-682">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="5b84b-682">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5b84b-683">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="5b84b-683">**globaljson**</span></span>

<span data-ttu-id="5b84b-684">`--sdk-version <VERSION_NUMBER>`-Určuje verzi .NET Core SDK, která se má použít v souboru *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="5b84b-684">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="5b84b-685">**web**</span><span class="sxs-lookup"><span data-stu-id="5b84b-685">**web**</span></span>

<span data-ttu-id="5b84b-686">`--use-launch-settings`-Zahrnuje *launchSettings. JSON* ve výstupu vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="5b84b-686">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="5b84b-687">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="5b84b-687">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5b84b-688">**webapi**</span><span class="sxs-lookup"><span data-stu-id="5b84b-688">**webapi**</span></span>

<span data-ttu-id="5b84b-689">`-au|--auth <AUTHENTICATION_TYPE>`– Typ ověřování, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="5b84b-689">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="5b84b-690">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="5b84b-690">The possible values are:</span></span>

- <span data-ttu-id="5b84b-691">`None`-Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="5b84b-691">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="5b84b-692">`IndividualB2C`-Jednotlivá ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="5b84b-692">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="5b84b-693">`SingleOrg`– Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="5b84b-693">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="5b84b-694">`Windows`– Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5b84b-694">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="5b84b-695">`--aad-b2c-instance <INSTANCE>`– Instance Azure Active Directory B2C pro připojení.</span><span class="sxs-lookup"><span data-stu-id="5b84b-695">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="5b84b-696">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="5b84b-696">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="5b84b-697">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-697">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="5b84b-698">`-ssp|--susi-policy-id <ID>`– ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="5b84b-698">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="5b84b-699">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="5b84b-699">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5b84b-700">`--aad-instance <INSTANCE>`– Instance Azure Active Directory pro připojení.</span><span class="sxs-lookup"><span data-stu-id="5b84b-700">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="5b84b-701">Použijte s `SingleOrg` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="5b84b-701">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="5b84b-702">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-702">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="5b84b-703">`--client-id <ID>`– ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="5b84b-703">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="5b84b-704">Použijte s `IndividualB2C` ověřováním nebo `SingleOrg` .</span><span class="sxs-lookup"><span data-stu-id="5b84b-704">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="5b84b-705">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-705">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="5b84b-706">`--domain <DOMAIN>`– Doména pro tenanta adresáře.</span><span class="sxs-lookup"><span data-stu-id="5b84b-706">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="5b84b-707">Použijte s `SingleOrg` ověřováním nebo `IndividualB2C` .</span><span class="sxs-lookup"><span data-stu-id="5b84b-707">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="5b84b-708">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-708">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="5b84b-709">`--tenant-id <ID>`– ID TenantId adresáře, ke kterému se má připojit.</span><span class="sxs-lookup"><span data-stu-id="5b84b-709">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="5b84b-710">Použijte s `SingleOrg` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="5b84b-710">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="5b84b-711">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-711">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="5b84b-712">`-r|--org-read-access`– Povolí této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="5b84b-712">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="5b84b-713">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="5b84b-713">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="5b84b-714">`--use-launch-settings`-Zahrnuje *launchSettings. JSON* ve výstupu vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="5b84b-714">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="5b84b-715">`-uld|--use-local-db`-Určuje LocalDB by měl být použit místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="5b84b-715">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="5b84b-716">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="5b84b-716">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5b84b-717">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="5b84b-717">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5b84b-718">**MVC, Razor**</span><span class="sxs-lookup"><span data-stu-id="5b84b-718">**mvc, razor**</span></span>

<span data-ttu-id="5b84b-719">`-au|--auth <AUTHENTICATION_TYPE>`– Typ ověřování, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="5b84b-719">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="5b84b-720">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="5b84b-720">The possible values are:</span></span>

- <span data-ttu-id="5b84b-721">`None`-Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="5b84b-721">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="5b84b-722">`Individual`-Individuální ověřování.</span><span class="sxs-lookup"><span data-stu-id="5b84b-722">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="5b84b-723">`IndividualB2C`-Jednotlivá ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="5b84b-723">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="5b84b-724">`SingleOrg`– Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="5b84b-724">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="5b84b-725">`MultiOrg`– Ověřování organizace pro více tenantů.</span><span class="sxs-lookup"><span data-stu-id="5b84b-725">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="5b84b-726">`Windows`– Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5b84b-726">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="5b84b-727">`--aad-b2c-instance <INSTANCE>`– Instance Azure Active Directory B2C pro připojení.</span><span class="sxs-lookup"><span data-stu-id="5b84b-727">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="5b84b-728">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="5b84b-728">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="5b84b-729">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-729">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="5b84b-730">`-ssp|--susi-policy-id <ID>`– ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="5b84b-730">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="5b84b-731">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="5b84b-731">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5b84b-732">`-rp|--reset-password-policy-id <ID>`– Resetování ID zásad hesla pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="5b84b-732">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="5b84b-733">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="5b84b-733">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5b84b-734">`-ep|--edit-profile-policy-id <ID>`– Upravte ID zásad profilu pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="5b84b-734">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="5b84b-735">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="5b84b-735">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5b84b-736">`--aad-instance <INSTANCE>`– Instance Azure Active Directory pro připojení.</span><span class="sxs-lookup"><span data-stu-id="5b84b-736">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="5b84b-737">Použijte s `SingleOrg` ověřováním nebo `MultiOrg` .</span><span class="sxs-lookup"><span data-stu-id="5b84b-737">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="5b84b-738">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-738">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="5b84b-739">`--client-id <ID>`– ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="5b84b-739">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="5b84b-740">Použijte s `IndividualB2C`ověřováním, `MultiOrg` `SingleOrg`nebo.</span><span class="sxs-lookup"><span data-stu-id="5b84b-740">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="5b84b-741">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-741">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="5b84b-742">`--domain <DOMAIN>`– Doména pro tenanta adresáře.</span><span class="sxs-lookup"><span data-stu-id="5b84b-742">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="5b84b-743">Použijte s `SingleOrg` ověřováním nebo `IndividualB2C` .</span><span class="sxs-lookup"><span data-stu-id="5b84b-743">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="5b84b-744">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-744">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="5b84b-745">`--tenant-id <ID>`– ID TenantId adresáře, ke kterému se má připojit.</span><span class="sxs-lookup"><span data-stu-id="5b84b-745">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="5b84b-746">Použijte s `SingleOrg` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="5b84b-746">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="5b84b-747">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-747">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="5b84b-748">`--callback-path <PATH>`– Cesta požadavku v základní cestě identifikátoru URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="5b84b-748">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="5b84b-749">Použijte s `SingleOrg` ověřováním nebo `IndividualB2C` .</span><span class="sxs-lookup"><span data-stu-id="5b84b-749">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="5b84b-750">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-750">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="5b84b-751">`-r|--org-read-access`– Povolí této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="5b84b-751">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="5b84b-752">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="5b84b-752">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="5b84b-753">`--use-launch-settings`-Zahrnuje *launchSettings. JSON* ve výstupu vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="5b84b-753">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="5b84b-754">`--use-browserlink`-Zahrnuje BrowserLink do projektu.</span><span class="sxs-lookup"><span data-stu-id="5b84b-754">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="5b84b-755">`-uld|--use-local-db`-Určuje LocalDB by měl být použit místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="5b84b-755">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="5b84b-756">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="5b84b-756">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5b84b-757">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="5b84b-757">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5b84b-758">**Page**</span><span class="sxs-lookup"><span data-stu-id="5b84b-758">**page**</span></span>

<span data-ttu-id="5b84b-759">`-na|--namespace <NAMESPACE_NAME>`– Obor názvů pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="5b84b-759">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="5b84b-760">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-760">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="5b84b-761">`-np|--no-pagemodel`-Vytvoří stránku bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="5b84b-761">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="5b84b-762">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="5b84b-762">**viewimports**</span></span>

<span data-ttu-id="5b84b-763">`-na|--namespace <NAMESPACE_NAME>`– Obor názvů pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="5b84b-763">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="5b84b-764">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-764">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5b84b-765">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="5b84b-765">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="5b84b-766">**Konzola, xUnit, MSTest, web, WebApi**</span><span class="sxs-lookup"><span data-stu-id="5b84b-766">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="5b84b-767">`-f|--framework <FRAMEWORK>`-Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="5b84b-767">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="5b84b-768">Hodnoty: `netcoreapp1.0` nebo `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-768">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="5b84b-769">Výchozí hodnota je `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-769">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="5b84b-770">**classlib**</span><span class="sxs-lookup"><span data-stu-id="5b84b-770">**classlib**</span></span>

<span data-ttu-id="5b84b-771">`-f|--framework <FRAMEWORK>`-Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="5b84b-771">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="5b84b-772">Hodnoty: `netcoreapp1.0`, `netcoreapp1.1`, nebo `netstandard1.0` na `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-772">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="5b84b-773">Výchozí hodnota je `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-773">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="5b84b-774">**mvc**</span><span class="sxs-lookup"><span data-stu-id="5b84b-774">**mvc**</span></span>

<span data-ttu-id="5b84b-775">`-f|--framework <FRAMEWORK>`-Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="5b84b-775">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="5b84b-776">Hodnoty: `netcoreapp1.0` nebo `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-776">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="5b84b-777">Výchozí hodnota je `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-777">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="5b84b-778">`-au|--auth <AUTHENTICATION_TYPE>`– Typ ověřování, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="5b84b-778">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="5b84b-779">Hodnoty: `None` nebo `Individual`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-779">Values: `None` or `Individual`.</span></span> <span data-ttu-id="5b84b-780">Výchozí hodnota je `None`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-780">The default value is `None`.</span></span>

<span data-ttu-id="5b84b-781">`-uld|--use-local-db`– Určuje, jestli se místo SQLite použije LocalDB.</span><span class="sxs-lookup"><span data-stu-id="5b84b-781">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="5b84b-782">Hodnoty: `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-782">Values: `true` or `false`.</span></span> <span data-ttu-id="5b84b-783">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="5b84b-783">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="5b84b-784">Příklady</span><span class="sxs-lookup"><span data-stu-id="5b84b-784">Examples</span></span>

<span data-ttu-id="5b84b-785">Vytvořte projekt C# konzolové aplikace zadáním názvu šablony:</span><span class="sxs-lookup"><span data-stu-id="5b84b-785">Create a C# console application project by specifying the template name:</span></span>

`dotnet new "Console Application"`

<span data-ttu-id="5b84b-786">Vytvořte projekt F# konzolové aplikace v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="5b84b-786">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="5b84b-787">Vytvořit projekt knihovny tříd .NET Standard v zadaném adresáři (k dispozici pouze s .NET Core SDK 2,0 nebo novějšími verzemi):</span><span class="sxs-lookup"><span data-stu-id="5b84b-787">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="5b84b-788">Vytvoří nový projekt ASP.NET Core C# MVC v aktuálním adresáři bez ověřování:</span><span class="sxs-lookup"><span data-stu-id="5b84b-788">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="5b84b-789">Vytvořit nový projekt xUnit:</span><span class="sxs-lookup"><span data-stu-id="5b84b-789">Create a new xUnit project:</span></span>

`dotnet new xunit`

<span data-ttu-id="5b84b-790">Vypíše všechny šablony, které jsou k dispozici pro MVC:</span><span class="sxs-lookup"><span data-stu-id="5b84b-790">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="5b84b-791">Vypíše všechny šablony, které odpovídají podřetězci *My* .</span><span class="sxs-lookup"><span data-stu-id="5b84b-791">List all templates matching the *we* substring.</span></span> <span data-ttu-id="5b84b-792">Nebyla nalezena žádná přesná shoda, takže porovnávání dílčích řetězců se shoduje se sloupci krátkého názvu a názvu.</span><span class="sxs-lookup"><span data-stu-id="5b84b-792">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

`dotnet new we -l`

<span data-ttu-id="5b84b-793">Došlo k pokusu o vyvolání šablony, která odpovídá *NG*.</span><span class="sxs-lookup"><span data-stu-id="5b84b-793">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="5b84b-794">Pokud nelze určit jednu shodu, Seznamte se se šablonami, které jsou částečné shody.</span><span class="sxs-lookup"><span data-stu-id="5b84b-794">If a single match can't be determined, list the templates that are partial matches.</span></span>

`dotnet new ng`

<span data-ttu-id="5b84b-795">2,0 nainstalujte šablony aplikace s jednou stránkou pro ASP.NET Core (možnost příkazového řádku, která je dostupná jenom pro .NET Core SDK 1,1 a novější verze):</span><span class="sxs-lookup"><span data-stu-id="5b84b-795">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="5b84b-796">Vytvoří *Global. JSON* v aktuálním adresáři nastavení verze sady SDK na 2.0.0 (k dispozici pouze s .NET Core SDK 2,0 nebo novějšími verzemi):</span><span class="sxs-lookup"><span data-stu-id="5b84b-796">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="5b84b-797">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5b84b-797">See also</span></span>

- [<span data-ttu-id="5b84b-798">Vlastní šablony pro dotnet New</span><span class="sxs-lookup"><span data-stu-id="5b84b-798">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="5b84b-799">Vytvoření vlastní šablony pro dotnet new</span><span class="sxs-lookup"><span data-stu-id="5b84b-799">Create a custom template for dotnet new</span></span>](../tutorials/create-custom-template.md)
- [<span data-ttu-id="5b84b-800">dotnet/dotnet-Template-Samples – úložiště GitHub</span><span class="sxs-lookup"><span data-stu-id="5b84b-800">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="5b84b-801">Dostupné šablony pro dotnet New</span><span class="sxs-lookup"><span data-stu-id="5b84b-801">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
