---
title: dotnet – nový příkaz
description: Příkaz dotnet New vytvoří nové projekty .NET Core založené na zadané šabloně.
ms.date: 05/06/2019
ms.openlocfilehash: c9e960bab0e28e88b0cc8d431dad3b9f3f00c9c0
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69660544"
---
# <a name="dotnet-new"></a><span data-ttu-id="6c0c1-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="6c0c1-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="6c0c1-104">Name</span><span class="sxs-lookup"><span data-stu-id="6c0c1-104">Name</span></span>

<span data-ttu-id="6c0c1-105">`dotnet new`– Vytvoří nový projekt, konfigurační soubor nebo řešení na základě zadané šablony.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="6c0c1-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="6c0c1-106">Synopsis</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="6c0c1-107">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="6c0c1-107">.NET Core 2.2</span></span>](#tab/netcore22)

```console
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="6c0c1-108">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="6c0c1-108">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="6c0c1-109">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="6c0c1-109">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6c0c1-110">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="6c0c1-110">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="6c0c1-111">Popis</span><span class="sxs-lookup"><span data-stu-id="6c0c1-111">Description</span></span>

<span data-ttu-id="6c0c1-112">`dotnet new` Příkaz nabízí pohodlný způsob, jak inicializovat platný projekt .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-112">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="6c0c1-113">Příkaz volá [modul šablony](https://github.com/dotnet/templating) a vytvoří artefakty na disku na základě zadané šablony a možností.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-113">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="6c0c1-114">Arguments</span><span class="sxs-lookup"><span data-stu-id="6c0c1-114">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="6c0c1-115">Šablona, která se má vytvořit při vyvolání příkazu</span><span class="sxs-lookup"><span data-stu-id="6c0c1-115">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="6c0c1-116">Každá šablona může mít konkrétní možnosti, které můžete předat.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-116">Each template might have specific options you can pass.</span></span> <span data-ttu-id="6c0c1-117">Další informace najdete v tématu [Možnosti šablony](#template-options).</span><span class="sxs-lookup"><span data-stu-id="6c0c1-117">For more information, see [Template options](#template-options).</span></span>

<span data-ttu-id="6c0c1-118">Pokud hodnota není přesná shoda na textu v šablonách nebo ve sloupci **short name** , je v těchto dvou sloupcích provedena shoda podřetězce. `TEMPLATE`</span><span class="sxs-lookup"><span data-stu-id="6c0c1-118">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column, a substring match is performed on those two columns.</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="6c0c1-119">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="6c0c1-119">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="6c0c1-120">Příkaz obsahuje výchozí seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-120">The command contains a default list of templates.</span></span> <span data-ttu-id="6c0c1-121">Použijte `dotnet new -l` k získání seznamu dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-121">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="6c0c1-122">Následující tabulka obsahuje šablony, které jsou předinstalované s .NET Core SDK 2.2.100.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-122">The following table shows the templates that come pre-installed with the .NET Core SDK 2.2.100.</span></span> <span data-ttu-id="6c0c1-123">Výchozí jazyk pro šablonu se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-123">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="6c0c1-124">Šablony</span><span class="sxs-lookup"><span data-stu-id="6c0c1-124">Templates</span></span>                                    | <span data-ttu-id="6c0c1-125">Krátký název</span><span class="sxs-lookup"><span data-stu-id="6c0c1-125">Short Name</span></span>        | <span data-ttu-id="6c0c1-126">Jazyk</span><span class="sxs-lookup"><span data-stu-id="6c0c1-126">Language</span></span>     | <span data-ttu-id="6c0c1-127">Značky</span><span class="sxs-lookup"><span data-stu-id="6c0c1-127">Tags</span></span>                                  |
|----------------------------------------------|-------------------|--------------|---------------------------------------|
| <span data-ttu-id="6c0c1-128">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="6c0c1-128">Console Application</span></span>                          | `console`         | <span data-ttu-id="6c0c1-129">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6c0c1-129">[C#], F#, VB</span></span> | <span data-ttu-id="6c0c1-130">Společná/konzola</span><span class="sxs-lookup"><span data-stu-id="6c0c1-130">Common/Console</span></span>                        |
| <span data-ttu-id="6c0c1-131">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="6c0c1-131">Class library</span></span>                                | `classlib`        | <span data-ttu-id="6c0c1-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6c0c1-132">[C#], F#, VB</span></span> | <span data-ttu-id="6c0c1-133">Společné/knihovny</span><span class="sxs-lookup"><span data-stu-id="6c0c1-133">Common/Library</span></span>                        |
| <span data-ttu-id="6c0c1-134">Projekt testu jednotek</span><span class="sxs-lookup"><span data-stu-id="6c0c1-134">Unit Test Project</span></span>                            | `mstest`          | <span data-ttu-id="6c0c1-135">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6c0c1-135">[C#], F#, VB</span></span> | <span data-ttu-id="6c0c1-136">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="6c0c1-136">Test/MSTest</span></span>                           |
| <span data-ttu-id="6c0c1-137">Projekt testů NUnit 3</span><span class="sxs-lookup"><span data-stu-id="6c0c1-137">NUnit 3 Test Project</span></span>                         | `nunit`           | <span data-ttu-id="6c0c1-138">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6c0c1-138">[C#], F#, VB</span></span> | <span data-ttu-id="6c0c1-139">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="6c0c1-139">Test/NUnit</span></span>                            |
| <span data-ttu-id="6c0c1-140">NUnit 3 položka testu</span><span class="sxs-lookup"><span data-stu-id="6c0c1-140">NUnit 3 Test Item</span></span>                            | `nunit-test`      | <span data-ttu-id="6c0c1-141">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6c0c1-141">[C#], F#, VB</span></span> | <span data-ttu-id="6c0c1-142">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="6c0c1-142">Test/NUnit</span></span>                            |
| <span data-ttu-id="6c0c1-143">Projekt testů xUnit</span><span class="sxs-lookup"><span data-stu-id="6c0c1-143">xUnit Test Project</span></span>                           | `xunit`           | <span data-ttu-id="6c0c1-144">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6c0c1-144">[C#], F#, VB</span></span> | <span data-ttu-id="6c0c1-145">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="6c0c1-145">Test/xUnit</span></span>                            |
| <span data-ttu-id="6c0c1-146">Stránka Razor</span><span class="sxs-lookup"><span data-stu-id="6c0c1-146">Razor Page</span></span>                                   | `page`            | <span data-ttu-id="6c0c1-147">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c0c1-147">[C#]</span></span>         | <span data-ttu-id="6c0c1-148">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6c0c1-148">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="6c0c1-149">ViewImports MVC</span><span class="sxs-lookup"><span data-stu-id="6c0c1-149">MVC ViewImports</span></span>                              | `viewimports`     | <span data-ttu-id="6c0c1-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c0c1-150">[C#]</span></span>         | <span data-ttu-id="6c0c1-151">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6c0c1-151">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="6c0c1-152">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="6c0c1-152">MVC ViewStart</span></span>                                | `viewstart`       | <span data-ttu-id="6c0c1-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c0c1-153">[C#]</span></span>         | <span data-ttu-id="6c0c1-154">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6c0c1-154">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="6c0c1-155">ASP.NET Core prázdné</span><span class="sxs-lookup"><span data-stu-id="6c0c1-155">ASP.NET Core Empty</span></span>                           | `web`             | <span data-ttu-id="6c0c1-156">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="6c0c1-156">[C#], F#</span></span>     | <span data-ttu-id="6c0c1-157">Web/prázdné</span><span class="sxs-lookup"><span data-stu-id="6c0c1-157">Web/Empty</span></span>                             |
| <span data-ttu-id="6c0c1-158">ASP.NET Core webová aplikace (model-zobrazení-kontroler)</span><span class="sxs-lookup"><span data-stu-id="6c0c1-158">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`             | <span data-ttu-id="6c0c1-159">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="6c0c1-159">[C#], F#</span></span>     | <span data-ttu-id="6c0c1-160">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="6c0c1-160">Web/MVC</span></span>                               |
| <span data-ttu-id="6c0c1-161">ASP.NET Core webové aplikace</span><span class="sxs-lookup"><span data-stu-id="6c0c1-161">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="6c0c1-162">`webapp`, `razor`</span><span class="sxs-lookup"><span data-stu-id="6c0c1-162">`webapp`, `razor`</span></span> | <span data-ttu-id="6c0c1-163">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c0c1-163">[C#]</span></span>         | <span data-ttu-id="6c0c1-164">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="6c0c1-164">Web/MVC/Razor Pages</span></span>                   |
| <span data-ttu-id="6c0c1-165">ASP.NET Core s úhlovým</span><span class="sxs-lookup"><span data-stu-id="6c0c1-165">ASP.NET Core with Angular</span></span>                    | `angular`         | <span data-ttu-id="6c0c1-166">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c0c1-166">[C#]</span></span>         | <span data-ttu-id="6c0c1-167">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="6c0c1-167">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="6c0c1-168">ASP.NET Core s reagují. js</span><span class="sxs-lookup"><span data-stu-id="6c0c1-168">ASP.NET Core with React.js</span></span>                   | `react`           | <span data-ttu-id="6c0c1-169">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c0c1-169">[C#]</span></span>         | <span data-ttu-id="6c0c1-170">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="6c0c1-170">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="6c0c1-171">ASP.NET Core s využitím reagují. js a Redux</span><span class="sxs-lookup"><span data-stu-id="6c0c1-171">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`      | <span data-ttu-id="6c0c1-172">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c0c1-172">[C#]</span></span>         | <span data-ttu-id="6c0c1-173">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="6c0c1-173">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="6c0c1-174">Knihovna tříd Razor</span><span class="sxs-lookup"><span data-stu-id="6c0c1-174">Razor Class Library</span></span>                          | `razorclasslib`   | <span data-ttu-id="6c0c1-175">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c0c1-175">[C#]</span></span>         | <span data-ttu-id="6c0c1-176">Knihovna tříd web/Razor/Library/Razor</span><span class="sxs-lookup"><span data-stu-id="6c0c1-176">Web/Razor/Library/Razor Class Library</span></span> |
| <span data-ttu-id="6c0c1-177">ASP.NET Core webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="6c0c1-177">ASP.NET Core Web API</span></span>                         | `webapi`          | <span data-ttu-id="6c0c1-178">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="6c0c1-178">[C#], F#</span></span>     | <span data-ttu-id="6c0c1-179">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="6c0c1-179">Web/WebAPI</span></span>                            |
| <span data-ttu-id="6c0c1-180">global.json file</span><span class="sxs-lookup"><span data-stu-id="6c0c1-180">global.json file</span></span>                             | `globaljson`      |              | <span data-ttu-id="6c0c1-181">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="6c0c1-181">Config</span></span>                                |
| <span data-ttu-id="6c0c1-182">Konfigurace NuGet</span><span class="sxs-lookup"><span data-stu-id="6c0c1-182">NuGet Config</span></span>                                 | `nugetconfig`     |              | <span data-ttu-id="6c0c1-183">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="6c0c1-183">Config</span></span>                                |
| <span data-ttu-id="6c0c1-184">Webová konfigurace</span><span class="sxs-lookup"><span data-stu-id="6c0c1-184">Web Config</span></span>                                   | `webconfig`       |              | <span data-ttu-id="6c0c1-185">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="6c0c1-185">Config</span></span>                                |
| <span data-ttu-id="6c0c1-186">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="6c0c1-186">Solution File</span></span>                                | `sln`             |              | <span data-ttu-id="6c0c1-187">Řešení</span><span class="sxs-lookup"><span data-stu-id="6c0c1-187">Solution</span></span>                              |

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="6c0c1-188">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="6c0c1-188">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="6c0c1-189">Příkaz obsahuje výchozí seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-189">The command contains a default list of templates.</span></span> <span data-ttu-id="6c0c1-190">Použijte `dotnet new -l` k získání seznamu dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-190">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="6c0c1-191">Následující tabulka obsahuje šablony, které jsou předinstalované s .NET Core SDK 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-191">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="6c0c1-192">Výchozí jazyk pro šablonu se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-192">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="6c0c1-193">Šablony</span><span class="sxs-lookup"><span data-stu-id="6c0c1-193">Templates</span></span>                                    | <span data-ttu-id="6c0c1-194">Krátký název</span><span class="sxs-lookup"><span data-stu-id="6c0c1-194">Short Name</span></span>      | <span data-ttu-id="6c0c1-195">Jazyk</span><span class="sxs-lookup"><span data-stu-id="6c0c1-195">Language</span></span>     | <span data-ttu-id="6c0c1-196">Značky</span><span class="sxs-lookup"><span data-stu-id="6c0c1-196">Tags</span></span>                                  |
|----------------------------------------------|-----------------|--------------|---------------------------------------|
| <span data-ttu-id="6c0c1-197">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="6c0c1-197">Console Application</span></span>                          | `console`       | <span data-ttu-id="6c0c1-198">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6c0c1-198">[C#], F#, VB</span></span> | <span data-ttu-id="6c0c1-199">Společná/konzola</span><span class="sxs-lookup"><span data-stu-id="6c0c1-199">Common/Console</span></span>                        |
| <span data-ttu-id="6c0c1-200">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="6c0c1-200">Class library</span></span>                                | `classlib`      | <span data-ttu-id="6c0c1-201">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6c0c1-201">[C#], F#, VB</span></span> | <span data-ttu-id="6c0c1-202">Společné/knihovny</span><span class="sxs-lookup"><span data-stu-id="6c0c1-202">Common/Library</span></span>                        |
| <span data-ttu-id="6c0c1-203">Projekt testu jednotek</span><span class="sxs-lookup"><span data-stu-id="6c0c1-203">Unit Test Project</span></span>                            | `mstest`        | <span data-ttu-id="6c0c1-204">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6c0c1-204">[C#], F#, VB</span></span> | <span data-ttu-id="6c0c1-205">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="6c0c1-205">Test/MSTest</span></span>                           |
| <span data-ttu-id="6c0c1-206">Projekt testů xUnit</span><span class="sxs-lookup"><span data-stu-id="6c0c1-206">xUnit Test Project</span></span>                           | `xunit`         | <span data-ttu-id="6c0c1-207">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6c0c1-207">[C#], F#, VB</span></span> | <span data-ttu-id="6c0c1-208">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="6c0c1-208">Test/xUnit</span></span>                            |
| <span data-ttu-id="6c0c1-209">Stránka Razor</span><span class="sxs-lookup"><span data-stu-id="6c0c1-209">Razor Page</span></span>                                   | `page`          | <span data-ttu-id="6c0c1-210">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c0c1-210">[C#]</span></span>         | <span data-ttu-id="6c0c1-211">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6c0c1-211">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="6c0c1-212">ViewImports MVC</span><span class="sxs-lookup"><span data-stu-id="6c0c1-212">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="6c0c1-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c0c1-213">[C#]</span></span>         | <span data-ttu-id="6c0c1-214">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6c0c1-214">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="6c0c1-215">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="6c0c1-215">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="6c0c1-216">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c0c1-216">[C#]</span></span>         | <span data-ttu-id="6c0c1-217">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6c0c1-217">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="6c0c1-218">ASP.NET Core prázdné</span><span class="sxs-lookup"><span data-stu-id="6c0c1-218">ASP.NET Core Empty</span></span>                           | `web`           | <span data-ttu-id="6c0c1-219">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="6c0c1-219">[C#], F#</span></span>     | <span data-ttu-id="6c0c1-220">Web/prázdné</span><span class="sxs-lookup"><span data-stu-id="6c0c1-220">Web/Empty</span></span>                             |
| <span data-ttu-id="6c0c1-221">ASP.NET Core webová aplikace (model-zobrazení-kontroler)</span><span class="sxs-lookup"><span data-stu-id="6c0c1-221">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="6c0c1-222">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="6c0c1-222">[C#], F#</span></span>     | <span data-ttu-id="6c0c1-223">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="6c0c1-223">Web/MVC</span></span>                               |
| <span data-ttu-id="6c0c1-224">ASP.NET Core webové aplikace</span><span class="sxs-lookup"><span data-stu-id="6c0c1-224">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="6c0c1-225">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c0c1-225">[C#]</span></span>         | <span data-ttu-id="6c0c1-226">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="6c0c1-226">Web/MVC/Razor Pages</span></span>                   |
| <span data-ttu-id="6c0c1-227">ASP.NET Core s úhlovým</span><span class="sxs-lookup"><span data-stu-id="6c0c1-227">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="6c0c1-228">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c0c1-228">[C#]</span></span>         | <span data-ttu-id="6c0c1-229">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="6c0c1-229">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="6c0c1-230">ASP.NET Core s reagují. js</span><span class="sxs-lookup"><span data-stu-id="6c0c1-230">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="6c0c1-231">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c0c1-231">[C#]</span></span>         | <span data-ttu-id="6c0c1-232">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="6c0c1-232">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="6c0c1-233">ASP.NET Core s využitím reagují. js a Redux</span><span class="sxs-lookup"><span data-stu-id="6c0c1-233">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="6c0c1-234">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c0c1-234">[C#]</span></span>         | <span data-ttu-id="6c0c1-235">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="6c0c1-235">Web/MVC/SPA</span></span>                           | 
| <span data-ttu-id="6c0c1-236">Knihovna tříd Razor</span><span class="sxs-lookup"><span data-stu-id="6c0c1-236">Razor Class Library</span></span>                          | `razorclasslib` | <span data-ttu-id="6c0c1-237">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c0c1-237">[C#]</span></span>         | <span data-ttu-id="6c0c1-238">Knihovna tříd web/Razor/Library/Razor</span><span class="sxs-lookup"><span data-stu-id="6c0c1-238">Web/Razor/Library/Razor Class Library</span></span> |
| <span data-ttu-id="6c0c1-239">ASP.NET Core webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="6c0c1-239">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="6c0c1-240">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="6c0c1-240">[C#], F#</span></span>     | <span data-ttu-id="6c0c1-241">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="6c0c1-241">Web/WebAPI</span></span>                            |
| <span data-ttu-id="6c0c1-242">global.json file</span><span class="sxs-lookup"><span data-stu-id="6c0c1-242">global.json file</span></span>                             | `globaljson`    |              | <span data-ttu-id="6c0c1-243">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="6c0c1-243">Config</span></span>                                |
| <span data-ttu-id="6c0c1-244">Konfigurace NuGet</span><span class="sxs-lookup"><span data-stu-id="6c0c1-244">NuGet Config</span></span>                                 | `nugetconfig`   |              | <span data-ttu-id="6c0c1-245">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="6c0c1-245">Config</span></span>                                |
| <span data-ttu-id="6c0c1-246">Webová konfigurace</span><span class="sxs-lookup"><span data-stu-id="6c0c1-246">Web Config</span></span>                                   | `webconfig`     |              | <span data-ttu-id="6c0c1-247">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="6c0c1-247">Config</span></span>                                |
| <span data-ttu-id="6c0c1-248">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="6c0c1-248">Solution File</span></span>                                | `sln`           |              | <span data-ttu-id="6c0c1-249">Řešení</span><span class="sxs-lookup"><span data-stu-id="6c0c1-249">Solution</span></span>                              |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="6c0c1-250">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="6c0c1-250">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="6c0c1-251">Příkaz obsahuje výchozí seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-251">The command contains a default list of templates.</span></span> <span data-ttu-id="6c0c1-252">Použijte `dotnet new -l` k získání seznamu dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-252">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="6c0c1-253">Následující tabulka obsahuje šablony, které jsou předinstalované s .NET Core SDK 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-253">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.0.</span></span> <span data-ttu-id="6c0c1-254">Výchozí jazyk pro šablonu se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-254">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="6c0c1-255">Šablony</span><span class="sxs-lookup"><span data-stu-id="6c0c1-255">Templates</span></span>                                    | <span data-ttu-id="6c0c1-256">Krátký název</span><span class="sxs-lookup"><span data-stu-id="6c0c1-256">Short Name</span></span>    | <span data-ttu-id="6c0c1-257">Jazyk</span><span class="sxs-lookup"><span data-stu-id="6c0c1-257">Language</span></span>     | <span data-ttu-id="6c0c1-258">Značky</span><span class="sxs-lookup"><span data-stu-id="6c0c1-258">Tags</span></span>                |
|----------------------------------------------|---------------|--------------|---------------------|
| <span data-ttu-id="6c0c1-259">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="6c0c1-259">Console Application</span></span>                          | `console`     | <span data-ttu-id="6c0c1-260">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6c0c1-260">[C#], F#, VB</span></span> | <span data-ttu-id="6c0c1-261">Společná/konzola</span><span class="sxs-lookup"><span data-stu-id="6c0c1-261">Common/Console</span></span>      |
| <span data-ttu-id="6c0c1-262">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="6c0c1-262">Class library</span></span>                                | `classlib`    | <span data-ttu-id="6c0c1-263">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6c0c1-263">[C#], F#, VB</span></span> | <span data-ttu-id="6c0c1-264">Společné/knihovny</span><span class="sxs-lookup"><span data-stu-id="6c0c1-264">Common/Library</span></span>      |
| <span data-ttu-id="6c0c1-265">Projekt testu jednotek</span><span class="sxs-lookup"><span data-stu-id="6c0c1-265">Unit Test Project</span></span>                            | `mstest`      | <span data-ttu-id="6c0c1-266">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6c0c1-266">[C#], F#, VB</span></span> | <span data-ttu-id="6c0c1-267">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="6c0c1-267">Test/MSTest</span></span>         |
| <span data-ttu-id="6c0c1-268">Projekt testů xUnit</span><span class="sxs-lookup"><span data-stu-id="6c0c1-268">xUnit Test Project</span></span>                           | `xunit`       | <span data-ttu-id="6c0c1-269">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6c0c1-269">[C#], F#, VB</span></span> | <span data-ttu-id="6c0c1-270">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="6c0c1-270">Test/xUnit</span></span>          |
| <span data-ttu-id="6c0c1-271">ASP.NET Core prázdné</span><span class="sxs-lookup"><span data-stu-id="6c0c1-271">ASP.NET Core Empty</span></span>                           | `web`         | <span data-ttu-id="6c0c1-272">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="6c0c1-272">[C#], F#</span></span>     | <span data-ttu-id="6c0c1-273">Web/prázdné</span><span class="sxs-lookup"><span data-stu-id="6c0c1-273">Web/Empty</span></span>           |
| <span data-ttu-id="6c0c1-274">ASP.NET Core webová aplikace (model-zobrazení-kontroler)</span><span class="sxs-lookup"><span data-stu-id="6c0c1-274">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="6c0c1-275">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="6c0c1-275">[C#], F#</span></span>     | <span data-ttu-id="6c0c1-276">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="6c0c1-276">Web/MVC</span></span>             |
| <span data-ttu-id="6c0c1-277">ASP.NET Core webové aplikace</span><span class="sxs-lookup"><span data-stu-id="6c0c1-277">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="6c0c1-278">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c0c1-278">[C#]</span></span>         | <span data-ttu-id="6c0c1-279">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="6c0c1-279">Web/MVC/Razor Pages</span></span> |
| <span data-ttu-id="6c0c1-280">ASP.NET Core s úhlovým</span><span class="sxs-lookup"><span data-stu-id="6c0c1-280">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="6c0c1-281">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c0c1-281">[C#]</span></span>         | <span data-ttu-id="6c0c1-282">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="6c0c1-282">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="6c0c1-283">ASP.NET Core s reagují. js</span><span class="sxs-lookup"><span data-stu-id="6c0c1-283">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="6c0c1-284">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c0c1-284">[C#]</span></span>         | <span data-ttu-id="6c0c1-285">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="6c0c1-285">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="6c0c1-286">ASP.NET Core s využitím reagují. js a Redux</span><span class="sxs-lookup"><span data-stu-id="6c0c1-286">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="6c0c1-287">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c0c1-287">[C#]</span></span>         | <span data-ttu-id="6c0c1-288">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="6c0c1-288">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="6c0c1-289">ASP.NET Core webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="6c0c1-289">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="6c0c1-290">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="6c0c1-290">[C#], F#</span></span>     | <span data-ttu-id="6c0c1-291">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="6c0c1-291">Web/WebAPI</span></span>          |
| <span data-ttu-id="6c0c1-292">global.json file</span><span class="sxs-lookup"><span data-stu-id="6c0c1-292">global.json file</span></span>                             | `globaljson`  |              | <span data-ttu-id="6c0c1-293">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="6c0c1-293">Config</span></span>              |
| <span data-ttu-id="6c0c1-294">Konfigurace NuGet</span><span class="sxs-lookup"><span data-stu-id="6c0c1-294">Nuget Config</span></span>                                 | `nugetconfig` |              | <span data-ttu-id="6c0c1-295">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="6c0c1-295">Config</span></span>              |
| <span data-ttu-id="6c0c1-296">Webová konfigurace</span><span class="sxs-lookup"><span data-stu-id="6c0c1-296">Web Config</span></span>                                   | `webconfig`   |              | <span data-ttu-id="6c0c1-297">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="6c0c1-297">Config</span></span>              |
| <span data-ttu-id="6c0c1-298">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="6c0c1-298">Solution File</span></span>                                | `sln`         |              | <span data-ttu-id="6c0c1-299">Řešení</span><span class="sxs-lookup"><span data-stu-id="6c0c1-299">Solution</span></span>            |
| <span data-ttu-id="6c0c1-300">Stránka Razor</span><span class="sxs-lookup"><span data-stu-id="6c0c1-300">Razor Page</span></span>                                   | `page`        |              | <span data-ttu-id="6c0c1-301">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6c0c1-301">Web/ASP.NET</span></span>         |
| <span data-ttu-id="6c0c1-302">ViewImports MVC</span><span class="sxs-lookup"><span data-stu-id="6c0c1-302">MVC ViewImports</span></span>                              | `viewimports` |              | <span data-ttu-id="6c0c1-303">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6c0c1-303">Web/ASP.NET</span></span>         |
| <span data-ttu-id="6c0c1-304">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="6c0c1-304">MVC ViewStart</span></span>                                | `viewstart`   |              | <span data-ttu-id="6c0c1-305">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6c0c1-305">Web/ASP.NET</span></span>         |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6c0c1-306">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="6c0c1-306">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="6c0c1-307">Příkaz obsahuje výchozí seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-307">The command contains a default list of templates.</span></span> <span data-ttu-id="6c0c1-308">Použijte `dotnet new -all` k získání seznamu dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-308">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="6c0c1-309">Následující tabulka obsahuje šablony, které jsou předinstalované s .NET Core SDK 1.0.1.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-309">The following table shows the templates that come pre-installed with the .NET Core SDK 1.0.1.</span></span> <span data-ttu-id="6c0c1-310">Výchozí jazyk pro šablonu se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-310">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="6c0c1-311">Šablony</span><span class="sxs-lookup"><span data-stu-id="6c0c1-311">Templates</span></span>            | <span data-ttu-id="6c0c1-312">Krátký název</span><span class="sxs-lookup"><span data-stu-id="6c0c1-312">Short Name</span></span>    | <span data-ttu-id="6c0c1-313">Jazyk</span><span class="sxs-lookup"><span data-stu-id="6c0c1-313">Language</span></span> | <span data-ttu-id="6c0c1-314">Značky</span><span class="sxs-lookup"><span data-stu-id="6c0c1-314">Tags</span></span>           |
|----------------------|---------------|----------|----------------|
| <span data-ttu-id="6c0c1-315">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="6c0c1-315">Console Application</span></span>  | `console`     | <span data-ttu-id="6c0c1-316">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="6c0c1-316">[C#], F#</span></span> | <span data-ttu-id="6c0c1-317">Společná/konzola</span><span class="sxs-lookup"><span data-stu-id="6c0c1-317">Common/Console</span></span> |
| <span data-ttu-id="6c0c1-318">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="6c0c1-318">Class library</span></span>        | `classlib`    | <span data-ttu-id="6c0c1-319">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="6c0c1-319">[C#], F#</span></span> | <span data-ttu-id="6c0c1-320">Společné/knihovny</span><span class="sxs-lookup"><span data-stu-id="6c0c1-320">Common/Library</span></span> |
| <span data-ttu-id="6c0c1-321">Projekt testu jednotek</span><span class="sxs-lookup"><span data-stu-id="6c0c1-321">Unit Test Project</span></span>    | `mstest`      | <span data-ttu-id="6c0c1-322">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="6c0c1-322">[C#], F#</span></span> | <span data-ttu-id="6c0c1-323">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="6c0c1-323">Test/MSTest</span></span>    |
| <span data-ttu-id="6c0c1-324">Projekt testů xUnit</span><span class="sxs-lookup"><span data-stu-id="6c0c1-324">xUnit Test Project</span></span>   | `xunit`       | <span data-ttu-id="6c0c1-325">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="6c0c1-325">[C#], F#</span></span> | <span data-ttu-id="6c0c1-326">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="6c0c1-326">Test/xUnit</span></span>     |
| <span data-ttu-id="6c0c1-327">ASP.NET Core prázdné</span><span class="sxs-lookup"><span data-stu-id="6c0c1-327">ASP.NET Core Empty</span></span>   | `web`         | <span data-ttu-id="6c0c1-328">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c0c1-328">[C#]</span></span>     | <span data-ttu-id="6c0c1-329">Web/prázdné</span><span class="sxs-lookup"><span data-stu-id="6c0c1-329">Web/Empty</span></span>      |
| <span data-ttu-id="6c0c1-330">ASP.NET Core webové aplikace</span><span class="sxs-lookup"><span data-stu-id="6c0c1-330">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="6c0c1-331">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="6c0c1-331">[C#], F#</span></span> | <span data-ttu-id="6c0c1-332">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="6c0c1-332">Web/MVC</span></span>        |
| <span data-ttu-id="6c0c1-333">ASP.NET Core webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="6c0c1-333">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="6c0c1-334">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c0c1-334">[C#]</span></span>     | <span data-ttu-id="6c0c1-335">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="6c0c1-335">Web/WebAPI</span></span>     |
| <span data-ttu-id="6c0c1-336">Konfigurace NuGet</span><span class="sxs-lookup"><span data-stu-id="6c0c1-336">Nuget Config</span></span>         | `nugetconfig` |          | <span data-ttu-id="6c0c1-337">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="6c0c1-337">Config</span></span>         |
| <span data-ttu-id="6c0c1-338">Webová konfigurace</span><span class="sxs-lookup"><span data-stu-id="6c0c1-338">Web Config</span></span>           | `webconfig`   |          | <span data-ttu-id="6c0c1-339">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="6c0c1-339">Config</span></span>         |
| <span data-ttu-id="6c0c1-340">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="6c0c1-340">Solution File</span></span>        | `sln`         |          | <span data-ttu-id="6c0c1-341">Řešení</span><span class="sxs-lookup"><span data-stu-id="6c0c1-341">Solution</span></span>       |

---

## <a name="options"></a><span data-ttu-id="6c0c1-342">Možnosti</span><span class="sxs-lookup"><span data-stu-id="6c0c1-342">Options</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="6c0c1-343">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="6c0c1-343">.NET Core 2.2</span></span>](#tab/netcore22)

`--dry-run`

<span data-ttu-id="6c0c1-344">Zobrazí souhrnné informace o tom, co se stane, pokud by došlo ke spuštění daného příkazu, pokud by to vedlo k vytvoření šablony.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-344">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span>

`--force`

<span data-ttu-id="6c0c1-345">Vynutí vygenerování obsahu i v případě, že změní existující soubory.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-345">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="6c0c1-346">To je nutné v případě, že výstupní adresář již obsahuje projekt.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-346">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="6c0c1-347">Vytiskne nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-347">Prints out help for the command.</span></span> <span data-ttu-id="6c0c1-348">Dá se vyvolat pro `dotnet new` samotný příkaz nebo pro libovolnou šablonu, `dotnet new mvc --help`jako je například.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-348">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="6c0c1-349">Nainstaluje zdroj nebo balíček šablony z `PATH` nebo `NUGET_ID` poskytnutého.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-349">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="6c0c1-350">Pokud chcete nainstalovat předprodejní verzi balíčku šablony, je nutné zadat verzi ve formátu `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-350">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="6c0c1-351">Ve výchozím nastavení `dotnet new` se \* předá verze, která představuje poslední stabilní verzi balíčku.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-351">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="6c0c1-352">Podívejte se na příklad v části [Příklady](#examples) .</span><span class="sxs-lookup"><span data-stu-id="6c0c1-352">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="6c0c1-353">Informace o vytváření vlastních šablon najdete v tématu [vlastní šablony pro dotnet New](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="6c0c1-353">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="6c0c1-354">Vypíše seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-354">Lists templates containing the specified name.</span></span> <span data-ttu-id="6c0c1-355">Pokud je vyvoláno pro `dotnet new` příkaz, zobrazí seznam možných šablon dostupných pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-355">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="6c0c1-356">Například Pokud adresář již obsahuje projekt, nezobrazuje seznam všech šablon projektu.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-356">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="6c0c1-357">Jazyk šablony, která se má vytvořit</span><span class="sxs-lookup"><span data-stu-id="6c0c1-357">The language of the template to create.</span></span> <span data-ttu-id="6c0c1-358">Přijatý jazyk se liší podle šablony (viz výchozí hodnoty v oddílu [argumenty](#arguments) ).</span><span class="sxs-lookup"><span data-stu-id="6c0c1-358">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="6c0c1-359">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-359">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="6c0c1-360">Některá prostředí jsou interpretována `#` jako speciální znak.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-360">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="6c0c1-361">V těchto případech je nutné uvést hodnotu parametru jazyka, například `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-361">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="6c0c1-362">Název vytvořeného výstupu.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-362">The name for the created output.</span></span> <span data-ttu-id="6c0c1-363">Pokud název nezadáte, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-363">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="6c0c1-364">Určuje zdroj NuGet, který se použije při instalaci.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-364">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="6c0c1-365">Umístění, do kterého se má vygenerovaný výstup umístit.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-365">Location to place the generated output.</span></span> <span data-ttu-id="6c0c1-366">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-366">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="6c0c1-367">Filtruje šablony založené na dostupných typech.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-367">Filters templates based on available types.</span></span> <span data-ttu-id="6c0c1-368">Předdefinované hodnoty jsou "projekt", "položka" nebo "jiné".</span><span class="sxs-lookup"><span data-stu-id="6c0c1-368">Predefined values are "project", "item", or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="6c0c1-369">Odinstaluje zdrojový nebo Template Pack na `PATH` nebo `NUGET_ID` poskytnutý.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-369">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="6c0c1-370">Při vyloučení `<PATH|NUGET_ID>` hodnoty se zobrazí všechny aktuálně nainstalované sady šablon a jejich přidružené šablony.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-370">When excluding the `<PATH|NUGET_ID>` value, all currently installed template packs and their associated templates are displayed.</span></span>

> [!NOTE]
> <span data-ttu-id="6c0c1-371">Chcete-li odinstalovat šablonu pomocí `PATH`nástroje, je nutné plně kvalifikovat cestu.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-371">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="6c0c1-372">Například *C:/Users/\<User >/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z nadřazené složky to nebude.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-372">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="6c0c1-373">Kromě toho Nezahrnovat koncové koncové lomítko adresáře na cestu k šabloně.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-373">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="6c0c1-374">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="6c0c1-374">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="6c0c1-375">Vynutí vygenerování obsahu i v případě, že změní existující soubory.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-375">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="6c0c1-376">To je nutné v případě, že výstupní adresář již obsahuje projekt.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-376">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="6c0c1-377">Vytiskne nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-377">Prints out help for the command.</span></span> <span data-ttu-id="6c0c1-378">Dá se vyvolat pro `dotnet new` samotný příkaz nebo pro libovolnou šablonu, `dotnet new mvc --help`jako je například.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-378">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="6c0c1-379">Nainstaluje zdroj nebo balíček šablony z `PATH` nebo `NUGET_ID` poskytnutého.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-379">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="6c0c1-380">Pokud chcete nainstalovat předprodejní verzi balíčku šablony, je nutné zadat verzi ve formátu `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-380">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="6c0c1-381">Ve výchozím nastavení `dotnet new` se \* předá verze, která představuje poslední stabilní verzi balíčku.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-381">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="6c0c1-382">Podívejte se na příklad v části [Příklady](#examples) .</span><span class="sxs-lookup"><span data-stu-id="6c0c1-382">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="6c0c1-383">Informace o vytváření vlastních šablon najdete v tématu [vlastní šablony pro dotnet New](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="6c0c1-383">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="6c0c1-384">Vypíše seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-384">Lists templates containing the specified name.</span></span> <span data-ttu-id="6c0c1-385">Pokud je vyvoláno pro `dotnet new` příkaz, zobrazí seznam možných šablon dostupných pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-385">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="6c0c1-386">Například Pokud adresář již obsahuje projekt, nezobrazuje seznam všech šablon projektu.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-386">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="6c0c1-387">Jazyk šablony, která se má vytvořit</span><span class="sxs-lookup"><span data-stu-id="6c0c1-387">The language of the template to create.</span></span> <span data-ttu-id="6c0c1-388">Přijatý jazyk se liší podle šablony (viz výchozí hodnoty v oddílu [argumenty](#arguments) ).</span><span class="sxs-lookup"><span data-stu-id="6c0c1-388">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="6c0c1-389">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-389">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="6c0c1-390">Některá prostředí jsou interpretována `#` jako speciální znak.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-390">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="6c0c1-391">V těchto případech je nutné uvést hodnotu parametru jazyka, například `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-391">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="6c0c1-392">Název vytvořeného výstupu.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-392">The name for the created output.</span></span> <span data-ttu-id="6c0c1-393">Pokud název nezadáte, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-393">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="6c0c1-394">Určuje zdroj NuGet, který se použije při instalaci.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-394">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="6c0c1-395">Umístění, do kterého se má vygenerovaný výstup umístit.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-395">Location to place the generated output.</span></span> <span data-ttu-id="6c0c1-396">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-396">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="6c0c1-397">Filtruje šablony založené na dostupných typech.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-397">Filters templates based on available types.</span></span> <span data-ttu-id="6c0c1-398">Předdefinované hodnoty jsou "projekt", "položka" nebo "jiné".</span><span class="sxs-lookup"><span data-stu-id="6c0c1-398">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="6c0c1-399">Odinstaluje zdrojový nebo Template Pack na `PATH` nebo `NUGET_ID` poskytnutý.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-399">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="6c0c1-400">Chcete-li odinstalovat šablonu pomocí `PATH`nástroje, je nutné plně kvalifikovat cestu.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-400">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="6c0c1-401">Například *C:/Users/\<User >/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z nadřazené složky to nebude.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-401">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="6c0c1-402">Kromě toho Nezahrnovat koncové koncové lomítko adresáře na cestu k šabloně.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-402">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="6c0c1-403">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="6c0c1-403">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="6c0c1-404">Vynutí vygenerování obsahu i v případě, že změní existující soubory.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-404">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="6c0c1-405">To je nutné v případě, že výstupní adresář již obsahuje projekt.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-405">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="6c0c1-406">Vytiskne nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-406">Prints out help for the command.</span></span> <span data-ttu-id="6c0c1-407">Dá se vyvolat pro `dotnet new` samotný příkaz nebo pro libovolnou šablonu, `dotnet new mvc --help`jako je například.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-407">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="6c0c1-408">Nainstaluje zdroj nebo balíček šablony z `PATH` nebo `NUGET_ID` poskytnutého.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-408">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="6c0c1-409">Pokud chcete nainstalovat předprodejní verzi balíčku šablony, je nutné zadat verzi ve formátu `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-409">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="6c0c1-410">Ve výchozím nastavení `dotnet new` se \* předá verze, která představuje poslední stabilní verzi balíčku.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-410">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="6c0c1-411">Podívejte se na příklad v části [Příklady](#examples) .</span><span class="sxs-lookup"><span data-stu-id="6c0c1-411">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="6c0c1-412">Informace o vytváření vlastních šablon najdete v tématu [vlastní šablony pro dotnet New](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="6c0c1-412">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="6c0c1-413">Vypíše seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-413">Lists templates containing the specified name.</span></span> <span data-ttu-id="6c0c1-414">Pokud je vyvoláno pro `dotnet new` příkaz, zobrazí seznam možných šablon dostupných pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-414">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="6c0c1-415">Například Pokud adresář již obsahuje projekt, nezobrazuje seznam všech šablon projektu.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-415">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="6c0c1-416">Jazyk šablony, která se má vytvořit</span><span class="sxs-lookup"><span data-stu-id="6c0c1-416">The language of the template to create.</span></span> <span data-ttu-id="6c0c1-417">Přijatý jazyk se liší podle šablony (viz výchozí hodnoty v oddílu [argumenty](#arguments) ).</span><span class="sxs-lookup"><span data-stu-id="6c0c1-417">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="6c0c1-418">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-418">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="6c0c1-419">Některá prostředí jsou interpretována `#` jako speciální znak.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-419">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="6c0c1-420">V těchto případech je nutné uvést hodnotu parametru jazyka, například `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-420">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="6c0c1-421">Název vytvořeného výstupu.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-421">The name for the created output.</span></span> <span data-ttu-id="6c0c1-422">Pokud název nezadáte, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-422">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="6c0c1-423">Umístění, do kterého se má vygenerovaný výstup umístit.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-423">Location to place the generated output.</span></span> <span data-ttu-id="6c0c1-424">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-424">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="6c0c1-425">Filtruje šablony založené na dostupných typech.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-425">Filters templates based on available types.</span></span> <span data-ttu-id="6c0c1-426">Předdefinované hodnoty jsou "projekt", "položka" nebo "jiné".</span><span class="sxs-lookup"><span data-stu-id="6c0c1-426">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="6c0c1-427">Odinstaluje zdrojový nebo Template Pack na `PATH` nebo `NUGET_ID` poskytnutý.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-427">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="6c0c1-428">Chcete-li odinstalovat šablonu pomocí zdroje `PATH`, je nutné cestu plně kvalifikovat.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-428">To uninstall a template using a source `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="6c0c1-429">Například *C:/Users/\<User >/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z nadřazené složky to nebude.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-429">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span> <span data-ttu-id="6c0c1-430">Kromě toho Nezahrnovat koncové koncové lomítko adresáře na cestu k šabloně.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-430">Additionally, do not include a final terminating directory slash on your template path.</span></span>
> 
> <span data-ttu-id="6c0c1-431">Pokud nemůžete určit `PATH` argument nebo `NUGET_ID` , který je potřeba k odinstalaci šablony, `dotnet new --uninstall` při spuštění bez argumentu se zobrazí seznam všech nainstalovaných šablon a argument, který je potřeba k jejich odinstalování.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-431">If you are unable to determine the `PATH` or `NUGET_ID` argument needed to uninstall a template, running `dotnet new --uninstall` without an argument will list all installed templates and the argument required to uninstall them.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6c0c1-432">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="6c0c1-432">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="6c0c1-433">Zobrazí všechny šablony pro konkrétní typ projektu při spuštění v kontextu `dotnet new` samotného příkazu.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-433">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="6c0c1-434">Při spuštění v souvislosti s konkrétní šablonou, `dotnet new web -all`jako je například, `-all` je interpretován jako příznak vytvoření vynucení.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-434">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="6c0c1-435">To je nutné v případě, že výstupní adresář již obsahuje projekt.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-435">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="6c0c1-436">Vytiskne nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-436">Prints out help for the command.</span></span> <span data-ttu-id="6c0c1-437">Dá se vyvolat pro `dotnet new` samotný příkaz nebo pro libovolnou šablonu, `dotnet new mvc --help`jako je například.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-437">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="6c0c1-438">Vypíše seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-438">Lists templates containing the specified name.</span></span> <span data-ttu-id="6c0c1-439">Pokud je vyvoláno pro `dotnet new` příkaz, zobrazí seznam možných šablon dostupných pro daný adresář.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-439">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="6c0c1-440">Například Pokud adresář již obsahuje projekt, nezobrazuje seznam všech šablon projektu.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-440">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="6c0c1-441">Jazyk šablony, která se má vytvořit</span><span class="sxs-lookup"><span data-stu-id="6c0c1-441">The language of the template to create.</span></span> <span data-ttu-id="6c0c1-442">Přijatý jazyk se liší podle šablony (viz výchozí hodnoty v oddílu [argumenty](#arguments) ).</span><span class="sxs-lookup"><span data-stu-id="6c0c1-442">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="6c0c1-443">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-443">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="6c0c1-444">Některá prostředí jsou interpretována `#` jako speciální znak.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-444">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="6c0c1-445">V těchto případech je nutné uvést hodnotu parametru jazyka, například `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-445">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="6c0c1-446">Název vytvořeného výstupu.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-446">The name for the created output.</span></span> <span data-ttu-id="6c0c1-447">Pokud název nezadáte, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-447">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="6c0c1-448">Umístění, do kterého se má vygenerovaný výstup umístit.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-448">Location to place the generated output.</span></span> <span data-ttu-id="6c0c1-449">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-449">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="6c0c1-450">Možnosti šablony</span><span class="sxs-lookup"><span data-stu-id="6c0c1-450">Template options</span></span>

<span data-ttu-id="6c0c1-451">Každá šablona projektu může mít k dispozici další možnosti.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-451">Each project template may have additional options available.</span></span> <span data-ttu-id="6c0c1-452">Základní šablony mají následující další možnosti:</span><span class="sxs-lookup"><span data-stu-id="6c0c1-452">The core templates have the following additional options:</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="6c0c1-453">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="6c0c1-453">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="6c0c1-454">**stromu**</span><span class="sxs-lookup"><span data-stu-id="6c0c1-454">**console**</span></span>

<span data-ttu-id="6c0c1-455">`--langVersion <VERSION_NUMBER>`-Nastaví `LangVersion` vlastnost v souboru vytvořeného projektu.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-455">`--langVersion <VERSION_NUMBER>` - Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="6c0c1-456">Použijte `--langVersion 7.3` například k použití C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-456">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="6c0c1-457">Nepodporuje se pro F#.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-457">Not supported for F#.</span></span>

<span data-ttu-id="6c0c1-458">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-458">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c0c1-459">**Úhlová, reakce, reactredux**</span><span class="sxs-lookup"><span data-stu-id="6c0c1-459">**angular, react, reactredux**</span></span>

<span data-ttu-id="6c0c1-460">`--exclude-launch-settings`– Vylučte z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="6c0c1-460">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="6c0c1-461">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-461">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c0c1-462">`--no-https`-Projekt nevyžaduje protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-462">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="6c0c1-463">Tato možnost se vztahuje jenom `IndividualAuth` na `OrganizationalAuth` to, jestli se nepoužívají.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-463">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="6c0c1-464">**razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="6c0c1-464">**razorclasslib**</span></span>

<span data-ttu-id="6c0c1-465">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-465">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c0c1-466">**classlib**</span><span class="sxs-lookup"><span data-stu-id="6c0c1-466">**classlib**</span></span>

<span data-ttu-id="6c0c1-467">`-f|--framework <FRAMEWORK>`-Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-467">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6c0c1-468">Hodnoty: `netcoreapp2.2` pro vytvoření knihovny tříd .NET Core nebo `netstandard2.0` pro vytvoření knihovny tříd .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-468">Values: `netcoreapp2.2` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="6c0c1-469">Výchozí hodnota je `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-469">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="6c0c1-470">`--langVersion <VERSION_NUMBER>`-Nastaví `LangVersion` vlastnost v souboru vytvořeného projektu.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-470">`--langVersion <VERSION_NUMBER>` - Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="6c0c1-471">Použijte `--langVersion 7.3` například k použití C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-471">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="6c0c1-472">Nepodporuje se pro F#.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-472">Not supported for F#.</span></span>

<span data-ttu-id="6c0c1-473">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-473">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c0c1-474">**MSTest, xUnit**</span><span class="sxs-lookup"><span data-stu-id="6c0c1-474">**mstest, xunit**</span></span>

<span data-ttu-id="6c0c1-475">`-p|--enable-pack`– Povolí balení pro projekt pomocí [sady dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="6c0c1-475">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="6c0c1-476">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-476">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c0c1-477">**nunit**</span><span class="sxs-lookup"><span data-stu-id="6c0c1-477">**nunit**</span></span>

<span data-ttu-id="6c0c1-478">`-f|--framework <FRAMEWORK>`-Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-478">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6c0c1-479">Výchozí hodnota je `netcoreapp2.1`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-479">The default value is `netcoreapp2.1`.</span></span>

<span data-ttu-id="6c0c1-480">`-p|--enable-pack`– Povolí balení pro projekt pomocí [sady dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="6c0c1-480">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="6c0c1-481">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-481">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c0c1-482">**Page**</span><span class="sxs-lookup"><span data-stu-id="6c0c1-482">**page**</span></span>

<span data-ttu-id="6c0c1-483">`-na|--namespace <NAMESPACE_NAME>`– Obor názvů pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-483">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="6c0c1-484">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-484">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="6c0c1-485">`-np|--no-pagemodel`-Vytvoří stránku bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-485">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="6c0c1-486">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="6c0c1-486">**viewimports**</span></span>

<span data-ttu-id="6c0c1-487">`-na|--namespace <NAMESPACE_NAME>`– Obor názvů pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-487">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="6c0c1-488">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-488">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="6c0c1-489">**web**</span><span class="sxs-lookup"><span data-stu-id="6c0c1-489">**web**</span></span>

<span data-ttu-id="6c0c1-490">`--exclude-launch-settings`– Vylučte z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="6c0c1-490">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="6c0c1-491">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-491">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c0c1-492">`--no-https`-Projekt nevyžaduje protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-492">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="6c0c1-493">Tato možnost se vztahuje jenom `IndividualAuth` na `OrganizationalAuth` to, jestli se nepoužívají.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-493">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="6c0c1-494">**mvc, webapp**</span><span class="sxs-lookup"><span data-stu-id="6c0c1-494">**mvc, webapp**</span></span>

<span data-ttu-id="6c0c1-495">`-au|--auth <AUTHENTICATION_TYPE>`– Typ ověřování, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-495">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="6c0c1-496">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="6c0c1-496">The possible values are:</span></span>

- <span data-ttu-id="6c0c1-497">`None`-Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="6c0c1-497">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="6c0c1-498">`Individual`-Individuální ověřování.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-498">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="6c0c1-499">`IndividualB2C`-Jednotlivá ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-499">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="6c0c1-500">`SingleOrg`– Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-500">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="6c0c1-501">`MultiOrg`– Ověřování organizace pro více tenantů.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-501">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="6c0c1-502">`Windows`– Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-502">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="6c0c1-503">`--aad-b2c-instance <INSTANCE>`– Instance Azure Active Directory B2C pro připojení.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-503">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="6c0c1-504">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-504">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="6c0c1-505">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-505">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="6c0c1-506">`-ssp|--susi-policy-id <ID>`– ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-506">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="6c0c1-507">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-507">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c0c1-508">`-rp|--reset-password-policy-id <ID>`– Resetování ID zásad hesla pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-508">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="6c0c1-509">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-509">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c0c1-510">`-ep|--edit-profile-policy-id <ID>`– Upravte ID zásad profilu pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-510">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="6c0c1-511">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-511">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c0c1-512">`--aad-instance <INSTANCE>`– Instance Azure Active Directory pro připojení.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-512">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="6c0c1-513">Použijte s `SingleOrg` ověřováním nebo `MultiOrg` .</span><span class="sxs-lookup"><span data-stu-id="6c0c1-513">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="6c0c1-514">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-514">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="6c0c1-515">`--client-id <ID>`– ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-515">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="6c0c1-516">Použijte s `IndividualB2C`ověřováním, `MultiOrg` `SingleOrg`nebo.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-516">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="6c0c1-517">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-517">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="6c0c1-518">`--domain <DOMAIN>`– Doména pro tenanta adresáře.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-518">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="6c0c1-519">Použijte s `SingleOrg` ověřováním nebo `IndividualB2C` .</span><span class="sxs-lookup"><span data-stu-id="6c0c1-519">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="6c0c1-520">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-520">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="6c0c1-521">`--tenant-id <ID>`– ID TenantId adresáře, ke kterému se má připojit.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-521">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="6c0c1-522">Použijte s `SingleOrg` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-522">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="6c0c1-523">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-523">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="6c0c1-524">`--callback-path <PATH>`– Cesta požadavku v základní cestě identifikátoru URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-524">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="6c0c1-525">Použijte s `SingleOrg` ověřováním nebo `IndividualB2C` .</span><span class="sxs-lookup"><span data-stu-id="6c0c1-525">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="6c0c1-526">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-526">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="6c0c1-527">`-r|--org-read-access`– Povolí této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-527">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="6c0c1-528">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-528">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="6c0c1-529">`--exclude-launch-settings`– Vylučte z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="6c0c1-529">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="6c0c1-530">`--no-https`-Projekt nevyžaduje protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-530">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="6c0c1-531">`app.UseHsts`a `app.UseHttpsRedirection` nejsou přidány do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-531">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="6c0c1-532">`Individual`Tato možnost platí pouze `IndividualB2C` `MultiOrg` v případě, že se nepoužívají, nebo.`SingleOrg`</span><span class="sxs-lookup"><span data-stu-id="6c0c1-532">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="6c0c1-533">`-uld|--use-local-db`-Určuje LocalDB by měl být použit místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-533">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="6c0c1-534">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-534">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c0c1-535">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-535">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c0c1-536">**webapi**</span><span class="sxs-lookup"><span data-stu-id="6c0c1-536">**webapi**</span></span>

<span data-ttu-id="6c0c1-537">`-au|--auth <AUTHENTICATION_TYPE>`– Typ ověřování, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-537">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="6c0c1-538">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="6c0c1-538">The possible values are:</span></span>

- <span data-ttu-id="6c0c1-539">`None`-Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="6c0c1-539">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="6c0c1-540">`IndividualB2C`-Jednotlivá ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-540">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="6c0c1-541">`SingleOrg`– Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-541">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="6c0c1-542">`Windows`– Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-542">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="6c0c1-543">`--aad-b2c-instance <INSTANCE>`– Instance Azure Active Directory B2C pro připojení.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-543">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="6c0c1-544">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-544">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="6c0c1-545">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-545">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="6c0c1-546">`-ssp|--susi-policy-id <ID>`– ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-546">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="6c0c1-547">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-547">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c0c1-548">`--aad-instance <INSTANCE>`– Instance Azure Active Directory pro připojení.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-548">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="6c0c1-549">Použijte s `SingleOrg` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-549">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="6c0c1-550">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-550">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="6c0c1-551">`--client-id <ID>`– ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-551">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="6c0c1-552">Použijte s `IndividualB2C` ověřováním nebo `SingleOrg` .</span><span class="sxs-lookup"><span data-stu-id="6c0c1-552">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="6c0c1-553">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-553">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="6c0c1-554">`--domain <DOMAIN>`– Doména pro tenanta adresáře.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-554">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="6c0c1-555">Použijte s `SingleOrg` ověřováním nebo `IndividualB2C` .</span><span class="sxs-lookup"><span data-stu-id="6c0c1-555">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="6c0c1-556">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-556">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="6c0c1-557">`--tenant-id <ID>`– ID TenantId adresáře, ke kterému se má připojit.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-557">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="6c0c1-558">Použijte s `SingleOrg` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-558">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="6c0c1-559">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-559">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="6c0c1-560">`-r|--org-read-access`– Povolí této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-560">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="6c0c1-561">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-561">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="6c0c1-562">`--exclude-launch-settings`– Vylučte z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="6c0c1-562">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="6c0c1-563">`--no-https`-Projekt nevyžaduje protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-563">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="6c0c1-564">`app.UseHsts`a `app.UseHttpsRedirection` nejsou přidány do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-564">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="6c0c1-565">`Individual`Tato možnost platí pouze `IndividualB2C` `MultiOrg` v případě, že se nepoužívají, nebo.`SingleOrg`</span><span class="sxs-lookup"><span data-stu-id="6c0c1-565">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="6c0c1-566">`-uld|--use-local-db`-Určuje LocalDB by měl být použit místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-566">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="6c0c1-567">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-567">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c0c1-568">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-568">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c0c1-569">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="6c0c1-569">**globaljson**</span></span>

<span data-ttu-id="6c0c1-570">`--sdk-version <VERSION_NUMBER>`-Určuje verzi .NET Core SDK, která se má použít v souboru *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="6c0c1-570">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="6c0c1-571">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="6c0c1-571">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="6c0c1-572">**Konzola, úhlová, reakce, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="6c0c1-572">**console, angular, react, reactredux, razorclasslib**</span></span>

<span data-ttu-id="6c0c1-573">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-573">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c0c1-574">**classlib**</span><span class="sxs-lookup"><span data-stu-id="6c0c1-574">**classlib**</span></span>

<span data-ttu-id="6c0c1-575">`-f|--framework <FRAMEWORK>`-Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-575">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6c0c1-576">Hodnoty: `netcoreapp2.1` pro vytvoření knihovny tříd .NET Core nebo `netstandard2.0` pro vytvoření knihovny tříd .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-576">Values: `netcoreapp2.1` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="6c0c1-577">Výchozí hodnota je `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-577">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="6c0c1-578">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-578">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c0c1-579">**MSTest, xUnit**</span><span class="sxs-lookup"><span data-stu-id="6c0c1-579">**mstest, xunit**</span></span>

<span data-ttu-id="6c0c1-580">`-p|--enable-pack`– Povolí balení pro projekt pomocí [sady dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="6c0c1-580">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="6c0c1-581">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-581">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c0c1-582">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="6c0c1-582">**globaljson**</span></span>

<span data-ttu-id="6c0c1-583">`--sdk-version <VERSION_NUMBER>`-Určuje verzi .NET Core SDK, která se má použít v souboru *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="6c0c1-583">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="6c0c1-584">**web**</span><span class="sxs-lookup"><span data-stu-id="6c0c1-584">**web**</span></span>

<span data-ttu-id="6c0c1-585">`--exclude-launch-settings`– Vylučte z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="6c0c1-585">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="6c0c1-586">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-586">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c0c1-587">`--no-https`-Projekt nevyžaduje protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-587">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="6c0c1-588">Tato možnost se vztahuje jenom `IndividualAuth` na `OrganizationalAuth` to, jestli se nepoužívají.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-588">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="6c0c1-589">**webapi**</span><span class="sxs-lookup"><span data-stu-id="6c0c1-589">**webapi**</span></span>

<span data-ttu-id="6c0c1-590">`-au|--auth <AUTHENTICATION_TYPE>`– Typ ověřování, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-590">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="6c0c1-591">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="6c0c1-591">The possible values are:</span></span>

- <span data-ttu-id="6c0c1-592">`None`-Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="6c0c1-592">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="6c0c1-593">`IndividualB2C`-Jednotlivá ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-593">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="6c0c1-594">`SingleOrg`– Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-594">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="6c0c1-595">`Windows`– Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-595">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="6c0c1-596">`--aad-b2c-instance <INSTANCE>`– Instance Azure Active Directory B2C pro připojení.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-596">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="6c0c1-597">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-597">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="6c0c1-598">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-598">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="6c0c1-599">`-ssp|--susi-policy-id <ID>`– ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-599">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="6c0c1-600">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-600">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c0c1-601">`--aad-instance <INSTANCE>`– Instance Azure Active Directory pro připojení.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-601">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="6c0c1-602">Použijte s `SingleOrg` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-602">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="6c0c1-603">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-603">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="6c0c1-604">`--client-id <ID>`– ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-604">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="6c0c1-605">Použijte s `IndividualB2C` ověřováním nebo `SingleOrg` .</span><span class="sxs-lookup"><span data-stu-id="6c0c1-605">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="6c0c1-606">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-606">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="6c0c1-607">`--domain <DOMAIN>`– Doména pro tenanta adresáře.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-607">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="6c0c1-608">Použijte s `SingleOrg` ověřováním nebo `IndividualB2C` .</span><span class="sxs-lookup"><span data-stu-id="6c0c1-608">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="6c0c1-609">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-609">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="6c0c1-610">`--tenant-id <ID>`– ID TenantId adresáře, ke kterému se má připojit.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-610">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="6c0c1-611">Použijte s `SingleOrg` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-611">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="6c0c1-612">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-612">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="6c0c1-613">`-r|--org-read-access`– Povolí této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-613">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="6c0c1-614">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-614">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="6c0c1-615">`--exclude-launch-settings`– Vylučte z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="6c0c1-615">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="6c0c1-616">`-uld|--use-local-db`-Určuje LocalDB by měl být použit místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-616">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="6c0c1-617">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-617">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c0c1-618">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-618">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c0c1-619">`--no-https`-Projekt nevyžaduje protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-619">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="6c0c1-620">`app.UseHsts`a `app.UseHttpsRedirection` nejsou přidány do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-620">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="6c0c1-621">`Individual`Tato možnost platí pouze `IndividualB2C` `MultiOrg` v případě, že se nepoužívají, nebo.`SingleOrg`</span><span class="sxs-lookup"><span data-stu-id="6c0c1-621">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="6c0c1-622">**MVC, Razor**</span><span class="sxs-lookup"><span data-stu-id="6c0c1-622">**mvc, razor**</span></span>

<span data-ttu-id="6c0c1-623">`-au|--auth <AUTHENTICATION_TYPE>`– Typ ověřování, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-623">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="6c0c1-624">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="6c0c1-624">The possible values are:</span></span>

- <span data-ttu-id="6c0c1-625">`None`-Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="6c0c1-625">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="6c0c1-626">`Individual`-Individuální ověřování.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-626">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="6c0c1-627">`IndividualB2C`-Jednotlivá ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-627">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="6c0c1-628">`SingleOrg`– Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-628">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="6c0c1-629">`MultiOrg`– Ověřování organizace pro více tenantů.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-629">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="6c0c1-630">`Windows`– Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-630">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="6c0c1-631">`--aad-b2c-instance <INSTANCE>`– Instance Azure Active Directory B2C pro připojení.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-631">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="6c0c1-632">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-632">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="6c0c1-633">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-633">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="6c0c1-634">`-ssp|--susi-policy-id <ID>`– ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-634">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="6c0c1-635">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-635">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c0c1-636">`-rp|--reset-password-policy-id <ID>`– Resetování ID zásad hesla pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-636">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="6c0c1-637">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-637">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c0c1-638">`-ep|--edit-profile-policy-id <ID>`– Upravte ID zásad profilu pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-638">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="6c0c1-639">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-639">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c0c1-640">`--aad-instance <INSTANCE>`– Instance Azure Active Directory pro připojení.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-640">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="6c0c1-641">Použijte s `SingleOrg` ověřováním nebo `MultiOrg` .</span><span class="sxs-lookup"><span data-stu-id="6c0c1-641">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="6c0c1-642">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-642">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="6c0c1-643">`--client-id <ID>`– ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-643">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="6c0c1-644">Použijte s `IndividualB2C`ověřováním, `MultiOrg` `SingleOrg`nebo.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-644">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="6c0c1-645">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-645">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="6c0c1-646">`--domain <DOMAIN>`– Doména pro tenanta adresáře.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-646">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="6c0c1-647">Použijte s `SingleOrg` ověřováním nebo `IndividualB2C` .</span><span class="sxs-lookup"><span data-stu-id="6c0c1-647">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="6c0c1-648">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-648">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="6c0c1-649">`--tenant-id <ID>`– ID TenantId adresáře, ke kterému se má připojit.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-649">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="6c0c1-650">Použijte s `SingleOrg` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-650">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="6c0c1-651">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-651">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="6c0c1-652">`--callback-path <PATH>`– Cesta požadavku v základní cestě identifikátoru URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-652">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="6c0c1-653">Použijte s `SingleOrg` ověřováním nebo `IndividualB2C` .</span><span class="sxs-lookup"><span data-stu-id="6c0c1-653">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="6c0c1-654">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-654">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="6c0c1-655">`-r|--org-read-access`– Povolí této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-655">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="6c0c1-656">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-656">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="6c0c1-657">`--exclude-launch-settings`– Vylučte z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="6c0c1-657">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="6c0c1-658">`--use-browserlink`-Zahrnuje BrowserLink do projektu.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-658">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="6c0c1-659">`-uld|--use-local-db`-Určuje LocalDB by měl být použit místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-659">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="6c0c1-660">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-660">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c0c1-661">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-661">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c0c1-662">`--no-https`-Projekt nevyžaduje protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-662">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="6c0c1-663">`app.UseHsts`a `app.UseHttpsRedirection` nejsou přidány do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-663">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="6c0c1-664">`Individual`Tato možnost platí pouze `IndividualB2C` `MultiOrg` v případě, že se nepoužívají, nebo.`SingleOrg`</span><span class="sxs-lookup"><span data-stu-id="6c0c1-664">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="6c0c1-665">**Page**</span><span class="sxs-lookup"><span data-stu-id="6c0c1-665">**page**</span></span>

<span data-ttu-id="6c0c1-666">`-na|--namespace <NAMESPACE_NAME>`– Obor názvů pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-666">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="6c0c1-667">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-667">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="6c0c1-668">`-np|--no-pagemodel`-Vytvoří stránku bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-668">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="6c0c1-669">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="6c0c1-669">**viewimports**</span></span>

<span data-ttu-id="6c0c1-670">`-na|--namespace <NAMESPACE_NAME>`– Obor názvů pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-670">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="6c0c1-671">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-671">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="6c0c1-672">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="6c0c1-672">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="6c0c1-673">**Konzola, úhlová, reakce, reactredux**</span><span class="sxs-lookup"><span data-stu-id="6c0c1-673">**console, angular, react, reactredux**</span></span>

<span data-ttu-id="6c0c1-674">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-674">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c0c1-675">**classlib**</span><span class="sxs-lookup"><span data-stu-id="6c0c1-675">**classlib**</span></span>

<span data-ttu-id="6c0c1-676">`-f|--framework <FRAMEWORK>`-Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-676">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6c0c1-677">Hodnoty: `netcoreapp2.0` pro vytvoření knihovny tříd .NET Core nebo `netstandard2.0` pro vytvoření knihovny tříd .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-677">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="6c0c1-678">Výchozí hodnota je `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-678">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="6c0c1-679">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-679">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c0c1-680">**MSTest, xUnit**</span><span class="sxs-lookup"><span data-stu-id="6c0c1-680">**mstest, xunit**</span></span>

<span data-ttu-id="6c0c1-681">`-p|--enable-pack`– Povolí balení pro projekt pomocí [sady dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="6c0c1-681">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="6c0c1-682">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-682">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c0c1-683">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="6c0c1-683">**globaljson**</span></span>

<span data-ttu-id="6c0c1-684">`--sdk-version <VERSION_NUMBER>`-Určuje verzi .NET Core SDK, která se má použít v souboru *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="6c0c1-684">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="6c0c1-685">**web**</span><span class="sxs-lookup"><span data-stu-id="6c0c1-685">**web**</span></span>

<span data-ttu-id="6c0c1-686">`--use-launch-settings`-Zahrnuje *launchSettings. JSON* ve výstupu vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-686">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="6c0c1-687">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-687">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c0c1-688">**webapi**</span><span class="sxs-lookup"><span data-stu-id="6c0c1-688">**webapi**</span></span>

<span data-ttu-id="6c0c1-689">`-au|--auth <AUTHENTICATION_TYPE>`– Typ ověřování, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-689">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="6c0c1-690">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="6c0c1-690">The possible values are:</span></span>

- <span data-ttu-id="6c0c1-691">`None`-Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="6c0c1-691">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="6c0c1-692">`IndividualB2C`-Jednotlivá ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-692">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="6c0c1-693">`SingleOrg`– Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-693">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="6c0c1-694">`Windows`– Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-694">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="6c0c1-695">`--aad-b2c-instance <INSTANCE>`– Instance Azure Active Directory B2C pro připojení.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-695">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="6c0c1-696">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-696">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="6c0c1-697">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-697">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="6c0c1-698">`-ssp|--susi-policy-id <ID>`– ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-698">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="6c0c1-699">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-699">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c0c1-700">`--aad-instance <INSTANCE>`– Instance Azure Active Directory pro připojení.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-700">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="6c0c1-701">Použijte s `SingleOrg` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-701">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="6c0c1-702">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-702">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="6c0c1-703">`--client-id <ID>`– ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-703">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="6c0c1-704">Použijte s `IndividualB2C` ověřováním nebo `SingleOrg` .</span><span class="sxs-lookup"><span data-stu-id="6c0c1-704">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="6c0c1-705">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-705">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="6c0c1-706">`--domain <DOMAIN>`– Doména pro tenanta adresáře.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-706">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="6c0c1-707">Použijte s `SingleOrg` ověřováním nebo `IndividualB2C` .</span><span class="sxs-lookup"><span data-stu-id="6c0c1-707">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="6c0c1-708">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-708">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="6c0c1-709">`--tenant-id <ID>`– ID TenantId adresáře, ke kterému se má připojit.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-709">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="6c0c1-710">Použijte s `SingleOrg` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-710">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="6c0c1-711">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-711">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="6c0c1-712">`-r|--org-read-access`– Povolí této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-712">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="6c0c1-713">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-713">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="6c0c1-714">`--use-launch-settings`-Zahrnuje *launchSettings. JSON* ve výstupu vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-714">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="6c0c1-715">`-uld|--use-local-db`-Určuje LocalDB by měl být použit místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-715">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="6c0c1-716">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-716">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c0c1-717">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-717">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c0c1-718">**MVC, Razor**</span><span class="sxs-lookup"><span data-stu-id="6c0c1-718">**mvc, razor**</span></span>

<span data-ttu-id="6c0c1-719">`-au|--auth <AUTHENTICATION_TYPE>`– Typ ověřování, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-719">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="6c0c1-720">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="6c0c1-720">The possible values are:</span></span>

- <span data-ttu-id="6c0c1-721">`None`-Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="6c0c1-721">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="6c0c1-722">`Individual`-Individuální ověřování.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-722">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="6c0c1-723">`IndividualB2C`-Jednotlivá ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-723">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="6c0c1-724">`SingleOrg`– Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-724">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="6c0c1-725">`MultiOrg`– Ověřování organizace pro více tenantů.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-725">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="6c0c1-726">`Windows`– Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-726">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="6c0c1-727">`--aad-b2c-instance <INSTANCE>`– Instance Azure Active Directory B2C pro připojení.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-727">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="6c0c1-728">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-728">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="6c0c1-729">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-729">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="6c0c1-730">`-ssp|--susi-policy-id <ID>`– ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-730">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="6c0c1-731">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-731">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c0c1-732">`-rp|--reset-password-policy-id <ID>`– Resetování ID zásad hesla pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-732">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="6c0c1-733">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-733">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c0c1-734">`-ep|--edit-profile-policy-id <ID>`– Upravte ID zásad profilu pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-734">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="6c0c1-735">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-735">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c0c1-736">`--aad-instance <INSTANCE>`– Instance Azure Active Directory pro připojení.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-736">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="6c0c1-737">Použijte s `SingleOrg` ověřováním nebo `MultiOrg` .</span><span class="sxs-lookup"><span data-stu-id="6c0c1-737">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="6c0c1-738">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-738">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="6c0c1-739">`--client-id <ID>`– ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-739">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="6c0c1-740">Použijte s `IndividualB2C`ověřováním, `MultiOrg` `SingleOrg`nebo.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-740">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="6c0c1-741">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-741">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="6c0c1-742">`--domain <DOMAIN>`– Doména pro tenanta adresáře.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-742">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="6c0c1-743">Použijte s `SingleOrg` ověřováním nebo `IndividualB2C` .</span><span class="sxs-lookup"><span data-stu-id="6c0c1-743">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="6c0c1-744">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-744">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="6c0c1-745">`--tenant-id <ID>`– ID TenantId adresáře, ke kterému se má připojit.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-745">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="6c0c1-746">Použijte s `SingleOrg` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-746">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="6c0c1-747">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-747">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="6c0c1-748">`--callback-path <PATH>`– Cesta požadavku v základní cestě identifikátoru URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-748">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="6c0c1-749">Použijte s `SingleOrg` ověřováním nebo `IndividualB2C` .</span><span class="sxs-lookup"><span data-stu-id="6c0c1-749">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="6c0c1-750">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-750">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="6c0c1-751">`-r|--org-read-access`– Povolí této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-751">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="6c0c1-752">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-752">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="6c0c1-753">`--use-launch-settings`-Zahrnuje *launchSettings. JSON* ve výstupu vygenerované šablony.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-753">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="6c0c1-754">`--use-browserlink`-Zahrnuje BrowserLink do projektu.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-754">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="6c0c1-755">`-uld|--use-local-db`-Určuje LocalDB by měl být použit místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-755">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="6c0c1-756">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-756">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c0c1-757">`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-757">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6c0c1-758">**Page**</span><span class="sxs-lookup"><span data-stu-id="6c0c1-758">**page**</span></span>

<span data-ttu-id="6c0c1-759">`-na|--namespace <NAMESPACE_NAME>`– Obor názvů pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-759">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="6c0c1-760">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-760">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="6c0c1-761">`-np|--no-pagemodel`-Vytvoří stránku bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-761">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="6c0c1-762">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="6c0c1-762">**viewimports**</span></span>

<span data-ttu-id="6c0c1-763">`-na|--namespace <NAMESPACE_NAME>`– Obor názvů pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-763">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="6c0c1-764">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-764">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6c0c1-765">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="6c0c1-765">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="6c0c1-766">**Konzola, xUnit, MSTest, web, WebApi**</span><span class="sxs-lookup"><span data-stu-id="6c0c1-766">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="6c0c1-767">`-f|--framework <FRAMEWORK>`-Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-767">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6c0c1-768">Hodnoty: `netcoreapp1.0` nebo `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-768">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="6c0c1-769">Výchozí hodnota je `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-769">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="6c0c1-770">**classlib**</span><span class="sxs-lookup"><span data-stu-id="6c0c1-770">**classlib**</span></span>

<span data-ttu-id="6c0c1-771">`-f|--framework <FRAMEWORK>`-Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-771">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6c0c1-772">Hodnoty: `netcoreapp1.0`, `netcoreapp1.1`, nebo `netstandard1.0` na `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-772">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="6c0c1-773">Výchozí hodnota je `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-773">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="6c0c1-774">**mvc**</span><span class="sxs-lookup"><span data-stu-id="6c0c1-774">**mvc**</span></span>

<span data-ttu-id="6c0c1-775">`-f|--framework <FRAMEWORK>`-Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-775">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6c0c1-776">Hodnoty: `netcoreapp1.0` nebo `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-776">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="6c0c1-777">Výchozí hodnota je `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-777">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="6c0c1-778">`-au|--auth <AUTHENTICATION_TYPE>`– Typ ověřování, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-778">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="6c0c1-779">Hodnoty: `None` nebo `Individual`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-779">Values: `None` or `Individual`.</span></span> <span data-ttu-id="6c0c1-780">Výchozí hodnota je `None`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-780">The default value is `None`.</span></span>

<span data-ttu-id="6c0c1-781">`-uld|--use-local-db`– Určuje, jestli se místo SQLite použije LocalDB.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-781">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="6c0c1-782">Hodnoty: `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-782">Values: `true` or `false`.</span></span> <span data-ttu-id="6c0c1-783">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-783">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="6c0c1-784">Příklady</span><span class="sxs-lookup"><span data-stu-id="6c0c1-784">Examples</span></span>

<span data-ttu-id="6c0c1-785">Vytvořte projekt C# konzolové aplikace zadáním názvu šablony:</span><span class="sxs-lookup"><span data-stu-id="6c0c1-785">Create a C# console application project by specifying the template name:</span></span>

`dotnet new "Console Application"`

<span data-ttu-id="6c0c1-786">Vytvořte projekt F# konzolové aplikace v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="6c0c1-786">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="6c0c1-787">Vytvořit projekt knihovny tříd .NET Standard v zadaném adresáři (k dispozici pouze s .NET Core SDK 2,0 nebo novějšími verzemi):</span><span class="sxs-lookup"><span data-stu-id="6c0c1-787">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="6c0c1-788">Vytvoří nový projekt ASP.NET Core C# MVC v aktuálním adresáři bez ověřování:</span><span class="sxs-lookup"><span data-stu-id="6c0c1-788">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="6c0c1-789">Vytvořit nový projekt xUnit:</span><span class="sxs-lookup"><span data-stu-id="6c0c1-789">Create a new xUnit project:</span></span>

`dotnet new xunit`

<span data-ttu-id="6c0c1-790">Vypíše všechny šablony, které jsou k dispozici pro MVC:</span><span class="sxs-lookup"><span data-stu-id="6c0c1-790">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="6c0c1-791">Vypíše všechny šablony, které odpovídají podřetězci *My* .</span><span class="sxs-lookup"><span data-stu-id="6c0c1-791">List all templates matching the *we* substring.</span></span> <span data-ttu-id="6c0c1-792">Nebyla nalezena žádná přesná shoda, takže porovnávání dílčích řetězců se shoduje se sloupci krátkého názvu a názvu.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-792">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

`dotnet new we -l`

<span data-ttu-id="6c0c1-793">Došlo k pokusu o vyvolání šablony, která odpovídá *NG*.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-793">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="6c0c1-794">Pokud nelze určit jednu shodu, Seznamte se se šablonami, které jsou částečné shody.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-794">If a single match can't be determined, list the templates that are partial matches.</span></span>

`dotnet new ng`

<span data-ttu-id="6c0c1-795">2,0 nainstalujte šablony aplikace s jednou stránkou pro ASP.NET Core (možnost příkazového řádku, která je dostupná jenom pro .NET Core SDK 1,1 a novější verze):</span><span class="sxs-lookup"><span data-stu-id="6c0c1-795">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="6c0c1-796">Vytvoří *Global. JSON* v aktuálním adresáři nastavení verze sady SDK na 2.0.0 (k dispozici pouze s .NET Core SDK 2,0 nebo novějšími verzemi):</span><span class="sxs-lookup"><span data-stu-id="6c0c1-796">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="6c0c1-797">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6c0c1-797">See also</span></span>

- [<span data-ttu-id="6c0c1-798">Vlastní šablony pro dotnet New</span><span class="sxs-lookup"><span data-stu-id="6c0c1-798">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="6c0c1-799">Vytvoření vlastní šablony pro dotnet new</span><span class="sxs-lookup"><span data-stu-id="6c0c1-799">Create a custom template for dotnet new</span></span>](../tutorials/create-custom-template.md)
- [<span data-ttu-id="6c0c1-800">dotnet/dotnet-Template-Samples – úložiště GitHub</span><span class="sxs-lookup"><span data-stu-id="6c0c1-800">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="6c0c1-801">Dostupné šablony pro dotnet New</span><span class="sxs-lookup"><span data-stu-id="6c0c1-801">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
