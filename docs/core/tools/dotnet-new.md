---
title: dotnet nový příkaz
description: Nový příkaz dotnet vytvoří nové projekty .NET Core založené na zadané šabloně.
ms.date: 02/13/2020
ms.openlocfilehash: d3c609419596b123f5bfb3ca85cf292a61154a70
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399124"
---
# <a name="dotnet-new"></a><span data-ttu-id="c1105-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="c1105-103">dotnet new</span></span>

<span data-ttu-id="c1105-104">**Tento článek se týká:** ✔️ .NET Core 2.0 SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="c1105-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="c1105-105">Name (Název)</span><span class="sxs-lookup"><span data-stu-id="c1105-105">Name</span></span>

<span data-ttu-id="c1105-106">`dotnet new`- Vytvoří nový projekt, konfigurační soubor nebo řešení založené na zadané šabloně.</span><span class="sxs-lookup"><span data-stu-id="c1105-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c1105-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="c1105-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name]
    [--nuget-source] [-o|--output] [-u|--uninstall] [--update-apply] [--update-check] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

## <a name="description"></a><span data-ttu-id="c1105-108">Popis</span><span class="sxs-lookup"><span data-stu-id="c1105-108">Description</span></span>

<span data-ttu-id="c1105-109">Příkaz `dotnet new` vytvoří projekt .NET Core nebo jiné artefakty založené na šabloně.</span><span class="sxs-lookup"><span data-stu-id="c1105-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="c1105-110">Příkaz volá [modul šablony](https://github.com/dotnet/templating) k vytvoření artefaktů na disku na základě zadané šablony a možností.</span><span class="sxs-lookup"><span data-stu-id="c1105-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="c1105-111">Argumenty</span><span class="sxs-lookup"><span data-stu-id="c1105-111">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="c1105-112">Šablona k vytvoření instance při vyvolání příkazu.</span><span class="sxs-lookup"><span data-stu-id="c1105-112">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="c1105-113">Každá šablona může mít konkrétní možnosti, které můžete předat.</span><span class="sxs-lookup"><span data-stu-id="c1105-113">Each template might have specific options you can pass.</span></span> <span data-ttu-id="c1105-114">Další informace naleznete v [tématu Možnosti šablony](#template-options).</span><span class="sxs-lookup"><span data-stu-id="c1105-114">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="c1105-115">Seznam všech `dotnet new --list` nainstalovaných šablon můžete spustit.</span><span class="sxs-lookup"><span data-stu-id="c1105-115">You can run `dotnet new --list` to see a list of all installed templates.</span></span> <span data-ttu-id="c1105-116">Pokud `TEMPLATE` hodnota není přesná shoda na text ve **sloupci Šablony** nebo **krátký název** z vrácené tabulky, podřetězec shoda se provádí na tyto dva sloupce.</span><span class="sxs-lookup"><span data-stu-id="c1105-116">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="c1105-117">Počínaje sadou .NET Core 3.0 SDK hledá rozhraní příkazového příkazu šablony v NuGet.org při vyvolání příkazu `dotnet new` za následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="c1105-117">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="c1105-118">Pokud clI nemůže najít šablonu zápas při `dotnet new`vyvolání , ani částečné.</span><span class="sxs-lookup"><span data-stu-id="c1105-118">If the CLI can’t find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="c1105-119">Pokud je k dispozici novější verze šablony.</span><span class="sxs-lookup"><span data-stu-id="c1105-119">If there’s a newer version of the template available.</span></span> <span data-ttu-id="c1105-120">V tomto případě je vytvořen projekt nebo artefakt, ale CLI vás upozorní na aktualizovanou verzi šablony.</span><span class="sxs-lookup"><span data-stu-id="c1105-120">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="c1105-121">Příkaz obsahuje výchozí seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="c1105-121">The command contains a default list of templates.</span></span> <span data-ttu-id="c1105-122">Slouží `dotnet new -l` k získání seznamu dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="c1105-122">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="c1105-123">V následující tabulce jsou uvedeny šablony, které jsou předinstalovány se sadou .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="c1105-123">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="c1105-124">Výchozí jazyk šablony je zobrazen uvnitř závorek.</span><span class="sxs-lookup"><span data-stu-id="c1105-124">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="c1105-125">Kliknutím na odkaz krátký název zobrazíte konkrétní možnosti šablony.</span><span class="sxs-lookup"><span data-stu-id="c1105-125">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="c1105-126">Šablony</span><span class="sxs-lookup"><span data-stu-id="c1105-126">Templates</span></span>                                    | <span data-ttu-id="c1105-127">Krátký název</span><span class="sxs-lookup"><span data-stu-id="c1105-127">Short name</span></span>                      | <span data-ttu-id="c1105-128">Jazyk</span><span class="sxs-lookup"><span data-stu-id="c1105-128">Language</span></span>     | <span data-ttu-id="c1105-129">Značky</span><span class="sxs-lookup"><span data-stu-id="c1105-129">Tags</span></span>                                  | <span data-ttu-id="c1105-130">Zavedena</span><span class="sxs-lookup"><span data-stu-id="c1105-130">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="c1105-131">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="c1105-131">Console Application</span></span>                          | [<span data-ttu-id="c1105-132">Konzoly</span><span class="sxs-lookup"><span data-stu-id="c1105-132">console</span></span>](#console)             | <span data-ttu-id="c1105-133">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c1105-133">[C#], F#, VB</span></span> | <span data-ttu-id="c1105-134">Běžné/konzolové</span><span class="sxs-lookup"><span data-stu-id="c1105-134">Common/Console</span></span>                        | <span data-ttu-id="c1105-135">1.0</span><span class="sxs-lookup"><span data-stu-id="c1105-135">1.0</span></span>        |
| <span data-ttu-id="c1105-136">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="c1105-136">Class library</span></span>                                | [<span data-ttu-id="c1105-137">classlib</span><span class="sxs-lookup"><span data-stu-id="c1105-137">classlib</span></span>](#classlib)           | <span data-ttu-id="c1105-138">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c1105-138">[C#], F#, VB</span></span> | <span data-ttu-id="c1105-139">Společné/Knihovna</span><span class="sxs-lookup"><span data-stu-id="c1105-139">Common/Library</span></span>                        | <span data-ttu-id="c1105-140">1.0</span><span class="sxs-lookup"><span data-stu-id="c1105-140">1.0</span></span>        |
| <span data-ttu-id="c1105-141">Aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="c1105-141">WPF Application</span></span>                              | [<span data-ttu-id="c1105-142">Wpf</span><span class="sxs-lookup"><span data-stu-id="c1105-142">wpf</span></span>](#wpf)                     | <span data-ttu-id="c1105-143">[C#]</span><span class="sxs-lookup"><span data-stu-id="c1105-143">[C#]</span></span>         | <span data-ttu-id="c1105-144">Časté/WPF</span><span class="sxs-lookup"><span data-stu-id="c1105-144">Common/WPF</span></span>                            | <span data-ttu-id="c1105-145">3.0</span><span class="sxs-lookup"><span data-stu-id="c1105-145">3.0</span></span>        |
| <span data-ttu-id="c1105-146">Knihovna tříd WPF</span><span class="sxs-lookup"><span data-stu-id="c1105-146">WPF Class library</span></span>                            | [<span data-ttu-id="c1105-147">wpflib</span><span class="sxs-lookup"><span data-stu-id="c1105-147">wpflib</span></span>](#wpf)                  | <span data-ttu-id="c1105-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="c1105-148">[C#]</span></span>         | <span data-ttu-id="c1105-149">Časté/WPF</span><span class="sxs-lookup"><span data-stu-id="c1105-149">Common/WPF</span></span>                            | <span data-ttu-id="c1105-150">3.0</span><span class="sxs-lookup"><span data-stu-id="c1105-150">3.0</span></span>        |
| <span data-ttu-id="c1105-151">Knihovna vlastních ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="c1105-151">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="c1105-152">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="c1105-152">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="c1105-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="c1105-153">[C#]</span></span>         | <span data-ttu-id="c1105-154">Časté/WPF</span><span class="sxs-lookup"><span data-stu-id="c1105-154">Common/WPF</span></span>                            | <span data-ttu-id="c1105-155">3.0</span><span class="sxs-lookup"><span data-stu-id="c1105-155">3.0</span></span>        |
| <span data-ttu-id="c1105-156">Knihovna uživatelských ovládacích prveků WPF</span><span class="sxs-lookup"><span data-stu-id="c1105-156">WPF User Control Library</span></span>                     | [<span data-ttu-id="c1105-157">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="c1105-157">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="c1105-158">[C#]</span><span class="sxs-lookup"><span data-stu-id="c1105-158">[C#]</span></span>         | <span data-ttu-id="c1105-159">Časté/WPF</span><span class="sxs-lookup"><span data-stu-id="c1105-159">Common/WPF</span></span>                            | <span data-ttu-id="c1105-160">3.0</span><span class="sxs-lookup"><span data-stu-id="c1105-160">3.0</span></span>        |
| <span data-ttu-id="c1105-161">Aplikace Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="c1105-161">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="c1105-162">Winforms</span><span class="sxs-lookup"><span data-stu-id="c1105-162">winforms</span></span>](#winforms)           | <span data-ttu-id="c1105-163">[C#]</span><span class="sxs-lookup"><span data-stu-id="c1105-163">[C#]</span></span>         | <span data-ttu-id="c1105-164">Běžné/WinForms</span><span class="sxs-lookup"><span data-stu-id="c1105-164">Common/WinForms</span></span>                       | <span data-ttu-id="c1105-165">3.0</span><span class="sxs-lookup"><span data-stu-id="c1105-165">3.0</span></span>        |
| <span data-ttu-id="c1105-166">Knihovna tříd Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="c1105-166">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="c1105-167">winformslib</span><span class="sxs-lookup"><span data-stu-id="c1105-167">winformslib</span></span>](#winforms)        | <span data-ttu-id="c1105-168">[C#]</span><span class="sxs-lookup"><span data-stu-id="c1105-168">[C#]</span></span>         | <span data-ttu-id="c1105-169">Běžné/WinForms</span><span class="sxs-lookup"><span data-stu-id="c1105-169">Common/WinForms</span></span>                       | <span data-ttu-id="c1105-170">3.0</span><span class="sxs-lookup"><span data-stu-id="c1105-170">3.0</span></span>        |
| <span data-ttu-id="c1105-171">Pracovní služba</span><span class="sxs-lookup"><span data-stu-id="c1105-171">Worker Service</span></span>                               | [<span data-ttu-id="c1105-172">Pracovník</span><span class="sxs-lookup"><span data-stu-id="c1105-172">worker</span></span>](#web-others)           | <span data-ttu-id="c1105-173">[C#]</span><span class="sxs-lookup"><span data-stu-id="c1105-173">[C#]</span></span>         | <span data-ttu-id="c1105-174">Běžné/Pracovník/Web</span><span class="sxs-lookup"><span data-stu-id="c1105-174">Common/Worker/Web</span></span>                     | <span data-ttu-id="c1105-175">3.0</span><span class="sxs-lookup"><span data-stu-id="c1105-175">3.0</span></span>        |
| <span data-ttu-id="c1105-176">Projekt testování částí</span><span class="sxs-lookup"><span data-stu-id="c1105-176">Unit Test Project</span></span>                            | [<span data-ttu-id="c1105-177">mstest</span><span class="sxs-lookup"><span data-stu-id="c1105-177">mstest</span></span>](#test)                 | <span data-ttu-id="c1105-178">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c1105-178">[C#], F#, VB</span></span> | <span data-ttu-id="c1105-179">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="c1105-179">Test/MSTest</span></span>                           | <span data-ttu-id="c1105-180">1.0</span><span class="sxs-lookup"><span data-stu-id="c1105-180">1.0</span></span>        |
| <span data-ttu-id="c1105-181">Testovací projekt NUnit 3</span><span class="sxs-lookup"><span data-stu-id="c1105-181">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="c1105-182">nunit</span><span class="sxs-lookup"><span data-stu-id="c1105-182">nunit</span></span>](#nunit)                  | <span data-ttu-id="c1105-183">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c1105-183">[C#], F#, VB</span></span> | <span data-ttu-id="c1105-184">Testovací/NUnit</span><span class="sxs-lookup"><span data-stu-id="c1105-184">Test/NUnit</span></span>                            | <span data-ttu-id="c1105-185">2.1.400</span><span class="sxs-lookup"><span data-stu-id="c1105-185">2.1.400</span></span>    |
| <span data-ttu-id="c1105-186">Testovací položka NUnit 3</span><span class="sxs-lookup"><span data-stu-id="c1105-186">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="c1105-187">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c1105-187">[C#], F#, VB</span></span> | <span data-ttu-id="c1105-188">Testovací/NUnit</span><span class="sxs-lookup"><span data-stu-id="c1105-188">Test/NUnit</span></span>                            | <span data-ttu-id="c1105-189">2,2</span><span class="sxs-lookup"><span data-stu-id="c1105-189">2.2</span></span>        |
| <span data-ttu-id="c1105-190">XUnit testovací projekt</span><span class="sxs-lookup"><span data-stu-id="c1105-190">xUnit Test Project</span></span>                           | [<span data-ttu-id="c1105-191">jednotka x</span><span class="sxs-lookup"><span data-stu-id="c1105-191">xunit</span></span>](#test)                  | <span data-ttu-id="c1105-192">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c1105-192">[C#], F#, VB</span></span> | <span data-ttu-id="c1105-193">Testovací/xJednotka</span><span class="sxs-lookup"><span data-stu-id="c1105-193">Test/xUnit</span></span>                            | <span data-ttu-id="c1105-194">1.0</span><span class="sxs-lookup"><span data-stu-id="c1105-194">1.0</span></span>        |
| <span data-ttu-id="c1105-195">Komponenta razor</span><span class="sxs-lookup"><span data-stu-id="c1105-195">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="c1105-196">[C#]</span><span class="sxs-lookup"><span data-stu-id="c1105-196">[C#]</span></span>         | <span data-ttu-id="c1105-197">Web/Technologie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c1105-197">Web/ASP.NET</span></span>                           | <span data-ttu-id="c1105-198">3.0</span><span class="sxs-lookup"><span data-stu-id="c1105-198">3.0</span></span>        |
| <span data-ttu-id="c1105-199">Holicí strojek stránka</span><span class="sxs-lookup"><span data-stu-id="c1105-199">Razor Page</span></span>                                   | [<span data-ttu-id="c1105-200">Stránka</span><span class="sxs-lookup"><span data-stu-id="c1105-200">page</span></span>](#page)                   | <span data-ttu-id="c1105-201">[C#]</span><span class="sxs-lookup"><span data-stu-id="c1105-201">[C#]</span></span>         | <span data-ttu-id="c1105-202">Web/Technologie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c1105-202">Web/ASP.NET</span></span>                           | <span data-ttu-id="c1105-203">2.0</span><span class="sxs-lookup"><span data-stu-id="c1105-203">2.0</span></span>        |
| <span data-ttu-id="c1105-204">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="c1105-204">MVC ViewImports</span></span>                              | [<span data-ttu-id="c1105-205">viewimports</span><span class="sxs-lookup"><span data-stu-id="c1105-205">viewimports</span></span>](#namespace)       | <span data-ttu-id="c1105-206">[C#]</span><span class="sxs-lookup"><span data-stu-id="c1105-206">[C#]</span></span>         | <span data-ttu-id="c1105-207">Web/Technologie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c1105-207">Web/ASP.NET</span></span>                           | <span data-ttu-id="c1105-208">2.0</span><span class="sxs-lookup"><span data-stu-id="c1105-208">2.0</span></span>        |
| <span data-ttu-id="c1105-209">Spuštění zobrazení MVC</span><span class="sxs-lookup"><span data-stu-id="c1105-209">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="c1105-210">[C#]</span><span class="sxs-lookup"><span data-stu-id="c1105-210">[C#]</span></span>         | <span data-ttu-id="c1105-211">Web/Technologie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c1105-211">Web/ASP.NET</span></span>                           | <span data-ttu-id="c1105-212">2.0</span><span class="sxs-lookup"><span data-stu-id="c1105-212">2.0</span></span>        |
| <span data-ttu-id="c1105-213">Aplikace Blazor Server</span><span class="sxs-lookup"><span data-stu-id="c1105-213">Blazor Server App</span></span>                            | [<span data-ttu-id="c1105-214">blazorserver</span><span class="sxs-lookup"><span data-stu-id="c1105-214">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="c1105-215">[C#]</span><span class="sxs-lookup"><span data-stu-id="c1105-215">[C#]</span></span>         | <span data-ttu-id="c1105-216">Web/Blazor</span><span class="sxs-lookup"><span data-stu-id="c1105-216">Web/Blazor</span></span>                            | <span data-ttu-id="c1105-217">3.0</span><span class="sxs-lookup"><span data-stu-id="c1105-217">3.0</span></span>        |
| <span data-ttu-id="c1105-218">ASP.NET jádro prázdné</span><span class="sxs-lookup"><span data-stu-id="c1105-218">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="c1105-219">Webové</span><span class="sxs-lookup"><span data-stu-id="c1105-219">web</span></span>](#web)                     | <span data-ttu-id="c1105-220">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="c1105-220">[C#], F#</span></span>     | <span data-ttu-id="c1105-221">Web/Prázdný</span><span class="sxs-lookup"><span data-stu-id="c1105-221">Web/Empty</span></span>                             | <span data-ttu-id="c1105-222">1.0</span><span class="sxs-lookup"><span data-stu-id="c1105-222">1.0</span></span>        |
| <span data-ttu-id="c1105-223">ASP.NET základní webová aplikace (model-view-controller)</span><span class="sxs-lookup"><span data-stu-id="c1105-223">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="c1105-224">Mvc</span><span class="sxs-lookup"><span data-stu-id="c1105-224">mvc</span></span>](#web-options)             | <span data-ttu-id="c1105-225">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="c1105-225">[C#], F#</span></span>     | <span data-ttu-id="c1105-226">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="c1105-226">Web/MVC</span></span>                               | <span data-ttu-id="c1105-227">1.0</span><span class="sxs-lookup"><span data-stu-id="c1105-227">1.0</span></span>        |
| <span data-ttu-id="c1105-228">ASP.NET základní webová aplikace</span><span class="sxs-lookup"><span data-stu-id="c1105-228">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="c1105-229">webapp, holicí strojek</span><span class="sxs-lookup"><span data-stu-id="c1105-229">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="c1105-230">[C#]</span><span class="sxs-lookup"><span data-stu-id="c1105-230">[C#]</span></span>         | <span data-ttu-id="c1105-231">Webové/MVC/Razor stránky</span><span class="sxs-lookup"><span data-stu-id="c1105-231">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="c1105-232">2.2, 2.0</span><span class="sxs-lookup"><span data-stu-id="c1105-232">2.2, 2.0</span></span>   |
| <span data-ttu-id="c1105-233">ASP.NET jádro s úhlovým</span><span class="sxs-lookup"><span data-stu-id="c1105-233">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="c1105-234">Úhlové</span><span class="sxs-lookup"><span data-stu-id="c1105-234">angular</span></span>](#spa)                 | <span data-ttu-id="c1105-235">[C#]</span><span class="sxs-lookup"><span data-stu-id="c1105-235">[C#]</span></span>         | <span data-ttu-id="c1105-236">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="c1105-236">Web/MVC/SPA</span></span>                           | <span data-ttu-id="c1105-237">2.0</span><span class="sxs-lookup"><span data-stu-id="c1105-237">2.0</span></span>        |
| <span data-ttu-id="c1105-238">ASP.NET jádro s React.js</span><span class="sxs-lookup"><span data-stu-id="c1105-238">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="c1105-239">Reagovat</span><span class="sxs-lookup"><span data-stu-id="c1105-239">react</span></span>](#spa)                   | <span data-ttu-id="c1105-240">[C#]</span><span class="sxs-lookup"><span data-stu-id="c1105-240">[C#]</span></span>         | <span data-ttu-id="c1105-241">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="c1105-241">Web/MVC/SPA</span></span>                           | <span data-ttu-id="c1105-242">2.0</span><span class="sxs-lookup"><span data-stu-id="c1105-242">2.0</span></span>        |
| <span data-ttu-id="c1105-243">ASP.NET jádro s React.js a Redux</span><span class="sxs-lookup"><span data-stu-id="c1105-243">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="c1105-244">reactredux</span><span class="sxs-lookup"><span data-stu-id="c1105-244">reactredux</span></span>](#reactredux)       | <span data-ttu-id="c1105-245">[C#]</span><span class="sxs-lookup"><span data-stu-id="c1105-245">[C#]</span></span>         | <span data-ttu-id="c1105-246">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="c1105-246">Web/MVC/SPA</span></span>                           | <span data-ttu-id="c1105-247">2.0</span><span class="sxs-lookup"><span data-stu-id="c1105-247">2.0</span></span>        |
| <span data-ttu-id="c1105-248">Knihovna třídy Holicí strojek</span><span class="sxs-lookup"><span data-stu-id="c1105-248">Razor Class Library</span></span>                          | [<span data-ttu-id="c1105-249">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="c1105-249">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="c1105-250">[C#]</span><span class="sxs-lookup"><span data-stu-id="c1105-250">[C#]</span></span>         | <span data-ttu-id="c1105-251">Web/Břitva/knihovna/knihovna</span><span class="sxs-lookup"><span data-stu-id="c1105-251">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="c1105-252">2.1</span><span class="sxs-lookup"><span data-stu-id="c1105-252">2.1</span></span>        |
| <span data-ttu-id="c1105-253">Webové rozhraní API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c1105-253">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="c1105-254">webapi</span><span class="sxs-lookup"><span data-stu-id="c1105-254">webapi</span></span>](#webapi)               | <span data-ttu-id="c1105-255">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="c1105-255">[C#], F#</span></span>     | <span data-ttu-id="c1105-256">Webové rozhraní API</span><span class="sxs-lookup"><span data-stu-id="c1105-256">Web/WebAPI</span></span>                            | <span data-ttu-id="c1105-257">1.0</span><span class="sxs-lookup"><span data-stu-id="c1105-257">1.0</span></span>        |
| <span data-ttu-id="c1105-258">ASP.NET Core gRPC Service</span><span class="sxs-lookup"><span data-stu-id="c1105-258">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="c1105-259">grpc</span><span class="sxs-lookup"><span data-stu-id="c1105-259">grpc</span></span>](#web-others)             | <span data-ttu-id="c1105-260">[C#]</span><span class="sxs-lookup"><span data-stu-id="c1105-260">[C#]</span></span>         | <span data-ttu-id="c1105-261">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="c1105-261">Web/gRPC</span></span>                              | <span data-ttu-id="c1105-262">3.0</span><span class="sxs-lookup"><span data-stu-id="c1105-262">3.0</span></span>        |
| <span data-ttu-id="c1105-263">Soubor vyrovnávací paměti protokolu</span><span class="sxs-lookup"><span data-stu-id="c1105-263">Protocol Buffer File</span></span>                         | [<span data-ttu-id="c1105-264">proto</span><span class="sxs-lookup"><span data-stu-id="c1105-264">proto</span></span>](#namespace)             |              | <span data-ttu-id="c1105-265">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="c1105-265">Web/gRPC</span></span>                              | <span data-ttu-id="c1105-266">3.0</span><span class="sxs-lookup"><span data-stu-id="c1105-266">3.0</span></span>        |
| <span data-ttu-id="c1105-267">dotnet gitignore soubor</span><span class="sxs-lookup"><span data-stu-id="c1105-267">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="c1105-268">Config</span><span class="sxs-lookup"><span data-stu-id="c1105-268">Config</span></span>                                | <span data-ttu-id="c1105-269">3.0</span><span class="sxs-lookup"><span data-stu-id="c1105-269">3.0</span></span>        |
| <span data-ttu-id="c1105-270">soubor global.json</span><span class="sxs-lookup"><span data-stu-id="c1105-270">global.json file</span></span>                             | [<span data-ttu-id="c1105-271">globaljson</span><span class="sxs-lookup"><span data-stu-id="c1105-271">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="c1105-272">Config</span><span class="sxs-lookup"><span data-stu-id="c1105-272">Config</span></span>                                | <span data-ttu-id="c1105-273">2.0</span><span class="sxs-lookup"><span data-stu-id="c1105-273">2.0</span></span>        |
| <span data-ttu-id="c1105-274">Konfigurace nugetu</span><span class="sxs-lookup"><span data-stu-id="c1105-274">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="c1105-275">Config</span><span class="sxs-lookup"><span data-stu-id="c1105-275">Config</span></span>                                | <span data-ttu-id="c1105-276">1.0</span><span class="sxs-lookup"><span data-stu-id="c1105-276">1.0</span></span>        |
| <span data-ttu-id="c1105-277">Dotnet místní nástroj manifest soubor</span><span class="sxs-lookup"><span data-stu-id="c1105-277">dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="c1105-278">Config</span><span class="sxs-lookup"><span data-stu-id="c1105-278">Config</span></span>                                | <span data-ttu-id="c1105-279">3.0</span><span class="sxs-lookup"><span data-stu-id="c1105-279">3.0</span></span>        |
| <span data-ttu-id="c1105-280">Konfigurace webu</span><span class="sxs-lookup"><span data-stu-id="c1105-280">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="c1105-281">Config</span><span class="sxs-lookup"><span data-stu-id="c1105-281">Config</span></span>                                | <span data-ttu-id="c1105-282">1.0</span><span class="sxs-lookup"><span data-stu-id="c1105-282">1.0</span></span>        |
| <span data-ttu-id="c1105-283">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="c1105-283">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="c1105-284">Řešení</span><span class="sxs-lookup"><span data-stu-id="c1105-284">Solution</span></span>                              | <span data-ttu-id="c1105-285">1.0</span><span class="sxs-lookup"><span data-stu-id="c1105-285">1.0</span></span>        |

## <a name="options"></a><span data-ttu-id="c1105-286">Možnosti</span><span class="sxs-lookup"><span data-stu-id="c1105-286">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="c1105-287">Zobrazí souhrn toho, co by se stalo, kdyby byl daný příkaz spuštěn.</span><span class="sxs-lookup"><span data-stu-id="c1105-287">Displays a summary of what would happen if the given command were run.</span></span> <span data-ttu-id="c1105-288">K dispozici od .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="c1105-288">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="c1105-289">Vynutí vygenerování obsahu, i když by změnil existující soubory.</span><span class="sxs-lookup"><span data-stu-id="c1105-289">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="c1105-290">To je nutné, pokud vybraná šablona přepíše existující soubory ve výstupním adresáři.</span><span class="sxs-lookup"><span data-stu-id="c1105-290">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="c1105-291">Vytiskne nápovědu pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="c1105-291">Prints out help for the command.</span></span> <span data-ttu-id="c1105-292">Může být vyvolána `dotnet new` pro samotný příkaz nebo pro libovolnou šablonu.</span><span class="sxs-lookup"><span data-stu-id="c1105-292">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="c1105-293">Například, `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="c1105-293">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="c1105-294">Nainstaluje sadu šablon `PATH` z `NUGET_ID` nebo poskytované.</span><span class="sxs-lookup"><span data-stu-id="c1105-294">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="c1105-295">Chcete-li nainstalovat předběžnou verzi balíčku šablony, je třeba zadat verzi `<package-name>::<package-version>`ve formátu .</span><span class="sxs-lookup"><span data-stu-id="c1105-295">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="c1105-296">Ve výchozím `dotnet new` \* nastavení přechází pro verzi, která představuje nejnovější stabilní verzi balíčku.</span><span class="sxs-lookup"><span data-stu-id="c1105-296">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="c1105-297">Viz příklad v části [Příklady.](#examples)</span><span class="sxs-lookup"><span data-stu-id="c1105-297">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="c1105-298">Pokud byla verze šablony již nainstalována při spuštění tohoto příkazu, bude šablona aktualizována na zadanou verzi nebo na nejnovější stabilní verzi, pokud nebyla zadána žádná verze.</span><span class="sxs-lookup"><span data-stu-id="c1105-298">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="c1105-299">Informace o vytváření vlastních šablon naleznete v [tématu Vlastní šablony pro dotnet new](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="c1105-299">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="c1105-300">Zobrazí seznam šablon obsahujících zadaný název.</span><span class="sxs-lookup"><span data-stu-id="c1105-300">Lists templates containing the specified name.</span></span> <span data-ttu-id="c1105-301">Pokud není zadán žádný název, zobrazí seznam všech šablon.</span><span class="sxs-lookup"><span data-stu-id="c1105-301">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="c1105-302">Jazyk šablony, kterou chcete vytvořit.</span><span class="sxs-lookup"><span data-stu-id="c1105-302">The language of the template to create.</span></span> <span data-ttu-id="c1105-303">Přijatý jazyk se liší podle šablony (viz výchozí hodnoty v části [argumenty).](#arguments)</span><span class="sxs-lookup"><span data-stu-id="c1105-303">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="c1105-304">Neplatí pro některé šablony.</span><span class="sxs-lookup"><span data-stu-id="c1105-304">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="c1105-305">Některé skořepiny interpretují `#` jako speciální znak.</span><span class="sxs-lookup"><span data-stu-id="c1105-305">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="c1105-306">V těchto případech uzavřete hodnotu parametru jazyka do uvozovek.</span><span class="sxs-lookup"><span data-stu-id="c1105-306">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="c1105-307">Například, `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="c1105-307">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="c1105-308">Název vytvořeného výstupu.</span><span class="sxs-lookup"><span data-stu-id="c1105-308">The name for the created output.</span></span> <span data-ttu-id="c1105-309">Pokud není zadán žádný název, bude použit název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="c1105-309">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source`**

  <span data-ttu-id="c1105-310">Určuje zdroj NuGet, který se má použít během instalace.</span><span class="sxs-lookup"><span data-stu-id="c1105-310">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="c1105-311">K dispozici od .NET Core 2.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="c1105-311">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="c1105-312">Umístění pro umístění generovaného výstupu.</span><span class="sxs-lookup"><span data-stu-id="c1105-312">Location to place the generated output.</span></span> <span data-ttu-id="c1105-313">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="c1105-313">The default is the current directory.</span></span>

- **`--type`**

  <span data-ttu-id="c1105-314">Filtruje šablony založené na dostupných typech.</span><span class="sxs-lookup"><span data-stu-id="c1105-314">Filters templates based on available types.</span></span> <span data-ttu-id="c1105-315">Předdefinované hodnoty jsou "projekt", "položka" nebo "jiné".</span><span class="sxs-lookup"><span data-stu-id="c1105-315">Predefined values are "project", "item", or "other".</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="c1105-316">Odinstaluje sadu `PATH` šablon `NUGET_ID` v aplikaci nebo v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c1105-316">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="c1105-317">Pokud `<PATH|NUGET_ID>` není zadána hodnota, zobrazí se všechny aktuálně nainstalované balíčky šablon a jejich přidružené šablony.</span><span class="sxs-lookup"><span data-stu-id="c1105-317">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="c1105-318">Při zadávání `NUGET_ID`aplikace neuvádějte číslo verze.</span><span class="sxs-lookup"><span data-stu-id="c1105-318">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="c1105-319">Pokud nezadáte parametr této možnosti, příkaz zobrazí seznam nainstalovaných šablon a podrobnosti o nich.</span><span class="sxs-lookup"><span data-stu-id="c1105-319">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="c1105-320">Chcete-li odinstalovat `PATH`šablonu pomocí aplikace , je třeba cestu plně kvalifikovat.</span><span class="sxs-lookup"><span data-stu-id="c1105-320">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="c1105-321">Například *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z obsahující složky nebude.</span><span class="sxs-lookup"><span data-stu-id="c1105-321">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="c1105-322">Nezahrnujte konečné ukončující lomítko adresáře na cestě šablony.</span><span class="sxs-lookup"><span data-stu-id="c1105-322">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="c1105-323">Zkontroluje, zda jsou k dispozici aktualizace pro aktuálně nainstalované balíčky šablon, a nainstaluje je.</span><span class="sxs-lookup"><span data-stu-id="c1105-323">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="c1105-324">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="c1105-324">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="c1105-325">Zkontroluje, zda jsou k dispozici aktualizace pro aktuálně nainstalované balíčky šablon.</span><span class="sxs-lookup"><span data-stu-id="c1105-325">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="c1105-326">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="c1105-326">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="c1105-327">Možnosti šablon</span><span class="sxs-lookup"><span data-stu-id="c1105-327">Template options</span></span>

<span data-ttu-id="c1105-328">Každá šablona projektu může mít k dispozici další možnosti.</span><span class="sxs-lookup"><span data-stu-id="c1105-328">Each project template may have additional options available.</span></span> <span data-ttu-id="c1105-329">Základní šablony mají následující další možnosti:</span><span class="sxs-lookup"><span data-stu-id="c1105-329">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="c1105-330">konzola</span><span class="sxs-lookup"><span data-stu-id="c1105-330">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c1105-331">Určuje [rámec,](../../standard/frameworks.md) na který má být cílit.</span><span class="sxs-lookup"><span data-stu-id="c1105-331">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c1105-332">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="c1105-332">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="c1105-333">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, které používáte:</span><span class="sxs-lookup"><span data-stu-id="c1105-333">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="c1105-334">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="c1105-334">SDK version</span></span> | <span data-ttu-id="c1105-335">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="c1105-335">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="c1105-336">3.1</span><span class="sxs-lookup"><span data-stu-id="c1105-336">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="c1105-337">3.0</span><span class="sxs-lookup"><span data-stu-id="c1105-337">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="c1105-338">Nastaví `LangVersion` vlastnost v vytvořeném souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="c1105-338">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="c1105-339">Například použijte `--langVersion 7.3` použít C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="c1105-339">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="c1105-340">Není podporováno pro F#.</span><span class="sxs-lookup"><span data-stu-id="c1105-340">Not supported for F#.</span></span> <span data-ttu-id="c1105-341">K dispozici od .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="c1105-341">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="c1105-342">Seznam výchozích verzí jazyka C# naleznete [v tématu Výchozí verze](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="c1105-342">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="c1105-343">Pokud je zadán, neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="c1105-343">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="c1105-344">K dispozici od .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="c1105-344">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="c1105-345">classlib</span><span class="sxs-lookup"><span data-stu-id="c1105-345">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c1105-346">Určuje [rámec,](../../standard/frameworks.md) na který má být cílit.</span><span class="sxs-lookup"><span data-stu-id="c1105-346">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c1105-347">Hodnoty: `netcoreapp<version>` chcete-li vytvořit knihovnu `netstandard<version>` tříd .NET Core nebo vytvořit knihovnu standardních tříd .NET.</span><span class="sxs-lookup"><span data-stu-id="c1105-347">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="c1105-348">Výchozí hodnota je `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="c1105-348">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="c1105-349">Nastaví `LangVersion` vlastnost v vytvořeném souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="c1105-349">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="c1105-350">Například použijte `--langVersion 7.3` použít C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="c1105-350">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="c1105-351">Není podporováno pro F#.</span><span class="sxs-lookup"><span data-stu-id="c1105-351">Not supported for F#.</span></span> <span data-ttu-id="c1105-352">K dispozici od .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="c1105-352">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="c1105-353">Seznam výchozích verzí jazyka C# naleznete [v tématu Výchozí verze](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="c1105-353">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="c1105-354">Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="c1105-354">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf"></a><span data-ttu-id="c1105-355">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="c1105-355">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c1105-356">Určuje [rámec,](../../standard/frameworks.md) na který má být cílit.</span><span class="sxs-lookup"><span data-stu-id="c1105-356">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c1105-357">Výchozí hodnota je `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="c1105-357">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="c1105-358">K dispozici od .NET Core 3.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="c1105-358">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="c1105-359">Nastaví `LangVersion` vlastnost v vytvořeném souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="c1105-359">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="c1105-360">Například použijte `--langVersion 7.3` použít C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="c1105-360">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="c1105-361">Seznam výchozích verzí jazyka C# naleznete [v tématu Výchozí verze](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="c1105-361">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="c1105-362">Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="c1105-362">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms"></a><span data-ttu-id="c1105-363">winforms, winformslib</span><span class="sxs-lookup"><span data-stu-id="c1105-363">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="c1105-364">Nastaví `LangVersion` vlastnost v vytvořeném souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="c1105-364">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="c1105-365">Například použijte `--langVersion 7.3` použít C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="c1105-365">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="c1105-366">Seznam výchozích verzí jazyka C# naleznete [v tématu Výchozí verze](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="c1105-366">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="c1105-367">Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="c1105-367">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web-others"></a><span data-ttu-id="c1105-368">pracovník, grpc</span><span class="sxs-lookup"><span data-stu-id="c1105-368">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c1105-369">Určuje [rámec,](../../standard/frameworks.md) na který má být cílit.</span><span class="sxs-lookup"><span data-stu-id="c1105-369">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c1105-370">Výchozí hodnota je `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="c1105-370">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="c1105-371">K dispozici od .NET Core 3.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="c1105-371">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="c1105-372">Nezahrnuje *launchSettings.json* z generované šablony.</span><span class="sxs-lookup"><span data-stu-id="c1105-372">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="c1105-373">Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="c1105-373">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="test"></a><span data-ttu-id="c1105-374">mstest, xunit</span><span class="sxs-lookup"><span data-stu-id="c1105-374">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c1105-375">Určuje [rámec,](../../standard/frameworks.md) na který má být cílit.</span><span class="sxs-lookup"><span data-stu-id="c1105-375">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c1105-376">Možnost je k dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="c1105-376">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="c1105-377">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, které používáte:</span><span class="sxs-lookup"><span data-stu-id="c1105-377">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="c1105-378">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="c1105-378">SDK version</span></span> | <span data-ttu-id="c1105-379">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="c1105-379">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="c1105-380">3.1</span><span class="sxs-lookup"><span data-stu-id="c1105-380">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="c1105-381">3.0</span><span class="sxs-lookup"><span data-stu-id="c1105-381">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="c1105-382">Umožňuje balení pro projekt pomocí [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="c1105-382">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="c1105-383">Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="c1105-383">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="c1105-384">nunit</span><span class="sxs-lookup"><span data-stu-id="c1105-384">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c1105-385">Určuje [rámec,](../../standard/frameworks.md) na který má být cílit.</span><span class="sxs-lookup"><span data-stu-id="c1105-385">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="c1105-386">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, které používáte:</span><span class="sxs-lookup"><span data-stu-id="c1105-386">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="c1105-387">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="c1105-387">SDK version</span></span> | <span data-ttu-id="c1105-388">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="c1105-388">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="c1105-389">3.1</span><span class="sxs-lookup"><span data-stu-id="c1105-389">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="c1105-390">3.0</span><span class="sxs-lookup"><span data-stu-id="c1105-390">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="c1105-391">2,2</span><span class="sxs-lookup"><span data-stu-id="c1105-391">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="c1105-392">2.1</span><span class="sxs-lookup"><span data-stu-id="c1105-392">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="c1105-393">Umožňuje balení pro projekt pomocí [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="c1105-393">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="c1105-394">Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="c1105-394">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="c1105-395">Stránka</span><span class="sxs-lookup"><span data-stu-id="c1105-395">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="c1105-396">Obor názvů pro generovaný kód.</span><span class="sxs-lookup"><span data-stu-id="c1105-396">Namespace for the generated code.</span></span> <span data-ttu-id="c1105-397">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="c1105-397">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="c1105-398">Vytvoří stránku bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="c1105-398">Creates the page without a PageModel.</span></span>

***

### <a name="namespace"></a><span data-ttu-id="c1105-399">viewimports, proto</span><span class="sxs-lookup"><span data-stu-id="c1105-399">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="c1105-400">Obor názvů pro generovaný kód.</span><span class="sxs-lookup"><span data-stu-id="c1105-400">Namespace for the generated code.</span></span> <span data-ttu-id="c1105-401">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="c1105-401">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="c1105-402">blazorserver</span><span class="sxs-lookup"><span data-stu-id="c1105-402">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="c1105-403">Typ ověřování, které chcete použít.</span><span class="sxs-lookup"><span data-stu-id="c1105-403">The type of authentication to use.</span></span> <span data-ttu-id="c1105-404">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="c1105-404">The possible values are:</span></span>

  - <span data-ttu-id="c1105-405">`None`- Žádné ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="c1105-405">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="c1105-406">`Individual`- Individuální autentizace.</span><span class="sxs-lookup"><span data-stu-id="c1105-406">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="c1105-407">`IndividualB2C`- Individuální ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="c1105-407">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="c1105-408">`SingleOrg`- Organizační ověřování pro jednoho klienta.</span><span class="sxs-lookup"><span data-stu-id="c1105-408">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="c1105-409">`MultiOrg`- Organizační ověřování pro více klientů.</span><span class="sxs-lookup"><span data-stu-id="c1105-409">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="c1105-410">`Windows`- Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="c1105-410">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="c1105-411">Instance Azure Active Directory B2C, ke které se chcete připojit.</span><span class="sxs-lookup"><span data-stu-id="c1105-411">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="c1105-412">Použití `IndividualB2C` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="c1105-412">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="c1105-413">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="c1105-413">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="c1105-414">ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="c1105-414">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="c1105-415">Použití `IndividualB2C` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="c1105-415">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="c1105-416">ID zásady obnovení hesla pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="c1105-416">The reset password policy ID for this project.</span></span> <span data-ttu-id="c1105-417">Použití `IndividualB2C` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="c1105-417">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="c1105-418">ID zásady úpravy profilu pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="c1105-418">The edit profile policy ID for this project.</span></span> <span data-ttu-id="c1105-419">Použití `IndividualB2C` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="c1105-419">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="c1105-420">Instance služby Azure Active Directory, ke které se chcete připojit.</span><span class="sxs-lookup"><span data-stu-id="c1105-420">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="c1105-421">Použití `SingleOrg` s `MultiOrg` ověřováním nebo ověřování.</span><span class="sxs-lookup"><span data-stu-id="c1105-421">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="c1105-422">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="c1105-422">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="c1105-423">ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="c1105-423">The Client ID for this project.</span></span> <span data-ttu-id="c1105-424">Použití `IndividualB2C`s `SingleOrg`protokolem , nebo `MultiOrg` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="c1105-424">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="c1105-425">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="c1105-425">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="c1105-426">Doména klienta adresáře.</span><span class="sxs-lookup"><span data-stu-id="c1105-426">The domain for the directory tenant.</span></span> <span data-ttu-id="c1105-427">Použití `SingleOrg` s `IndividualB2C` ověřováním nebo ověřování.</span><span class="sxs-lookup"><span data-stu-id="c1105-427">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c1105-428">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="c1105-428">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="c1105-429">ID ID ID tenantid adresáře, ke kterému se chcete připojit.</span><span class="sxs-lookup"><span data-stu-id="c1105-429">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="c1105-430">Použití `SingleOrg` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="c1105-430">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c1105-431">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="c1105-431">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="c1105-432">Cesta požadavku v rámci základní cesty aplikace identifikátoru URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="c1105-432">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="c1105-433">Použití `SingleOrg` s `IndividualB2C` ověřováním nebo ověřování.</span><span class="sxs-lookup"><span data-stu-id="c1105-433">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c1105-434">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="c1105-434">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="c1105-435">Umožňuje této aplikaci přístup pro čtení do adresáře.</span><span class="sxs-lookup"><span data-stu-id="c1105-435">Allows this application read-access to the directory.</span></span> <span data-ttu-id="c1105-436">Platí pouze `SingleOrg` pro `MultiOrg` nebo ověřování.</span><span class="sxs-lookup"><span data-stu-id="c1105-436">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="c1105-437">Nezahrnuje *launchSettings.json* z generované šablony.</span><span class="sxs-lookup"><span data-stu-id="c1105-437">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="c1105-438">Vypne protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c1105-438">Turns off HTTPS.</span></span> <span data-ttu-id="c1105-439">Tato možnost platí `Individual`pouze `IndividualB2C` `SingleOrg`v `MultiOrg` případě, že se `--auth`pro .</span><span class="sxs-lookup"><span data-stu-id="c1105-439">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="c1105-440">Určuje LocalDB by měl být použit místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="c1105-440">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c1105-441">Platí pouze `Individual` pro `IndividualB2C` nebo ověřování.</span><span class="sxs-lookup"><span data-stu-id="c1105-441">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="c1105-442">Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="c1105-442">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="c1105-443">web</span><span class="sxs-lookup"><span data-stu-id="c1105-443">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="c1105-444">Nezahrnuje *launchSettings.json* z generované šablony.</span><span class="sxs-lookup"><span data-stu-id="c1105-444">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c1105-445">Určuje [rámec,](../../standard/frameworks.md) na který má být cílit.</span><span class="sxs-lookup"><span data-stu-id="c1105-445">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c1105-446">Možnost není k dispozici v sada .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="c1105-446">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="c1105-447">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, které používáte:</span><span class="sxs-lookup"><span data-stu-id="c1105-447">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="c1105-448">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="c1105-448">SDK version</span></span> | <span data-ttu-id="c1105-449">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="c1105-449">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="c1105-450">3.1</span><span class="sxs-lookup"><span data-stu-id="c1105-450">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="c1105-451">3.0</span><span class="sxs-lookup"><span data-stu-id="c1105-451">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="c1105-452">2.1</span><span class="sxs-lookup"><span data-stu-id="c1105-452">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="c1105-453">Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="c1105-453">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="c1105-454">Vypne protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c1105-454">Turns off HTTPS.</span></span>

***

### <a name="web-options"></a><span data-ttu-id="c1105-455">mvc, webapp</span><span class="sxs-lookup"><span data-stu-id="c1105-455">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="c1105-456">Typ ověřování, které chcete použít.</span><span class="sxs-lookup"><span data-stu-id="c1105-456">The type of authentication to use.</span></span> <span data-ttu-id="c1105-457">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="c1105-457">The possible values are:</span></span>

  - <span data-ttu-id="c1105-458">`None`- Žádné ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="c1105-458">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="c1105-459">`Individual`- Individuální autentizace.</span><span class="sxs-lookup"><span data-stu-id="c1105-459">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="c1105-460">`IndividualB2C`- Individuální ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="c1105-460">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="c1105-461">`SingleOrg`- Organizační ověřování pro jednoho klienta.</span><span class="sxs-lookup"><span data-stu-id="c1105-461">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="c1105-462">`MultiOrg`- Organizační ověřování pro více klientů.</span><span class="sxs-lookup"><span data-stu-id="c1105-462">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="c1105-463">`Windows`- Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="c1105-463">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="c1105-464">Instance Azure Active Directory B2C, ke které se chcete připojit.</span><span class="sxs-lookup"><span data-stu-id="c1105-464">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="c1105-465">Použití `IndividualB2C` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="c1105-465">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="c1105-466">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="c1105-466">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="c1105-467">ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="c1105-467">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="c1105-468">Použití `IndividualB2C` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="c1105-468">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="c1105-469">ID zásady obnovení hesla pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="c1105-469">The reset password policy ID for this project.</span></span> <span data-ttu-id="c1105-470">Použití `IndividualB2C` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="c1105-470">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="c1105-471">ID zásady úpravy profilu pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="c1105-471">The edit profile policy ID for this project.</span></span> <span data-ttu-id="c1105-472">Použití `IndividualB2C` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="c1105-472">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="c1105-473">Instance služby Azure Active Directory, ke které se chcete připojit.</span><span class="sxs-lookup"><span data-stu-id="c1105-473">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="c1105-474">Použití `SingleOrg` s `MultiOrg` ověřováním nebo ověřování.</span><span class="sxs-lookup"><span data-stu-id="c1105-474">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="c1105-475">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="c1105-475">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="c1105-476">ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="c1105-476">The Client ID for this project.</span></span> <span data-ttu-id="c1105-477">Použití `IndividualB2C`s `SingleOrg`protokolem , nebo `MultiOrg` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="c1105-477">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="c1105-478">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="c1105-478">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="c1105-479">Doména klienta adresáře.</span><span class="sxs-lookup"><span data-stu-id="c1105-479">The domain for the directory tenant.</span></span> <span data-ttu-id="c1105-480">Použití `SingleOrg` s `IndividualB2C` ověřováním nebo ověřování.</span><span class="sxs-lookup"><span data-stu-id="c1105-480">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c1105-481">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="c1105-481">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="c1105-482">ID ID ID tenantid adresáře, ke kterému se chcete připojit.</span><span class="sxs-lookup"><span data-stu-id="c1105-482">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="c1105-483">Použití `SingleOrg` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="c1105-483">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c1105-484">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="c1105-484">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="c1105-485">Cesta požadavku v rámci základní cesty aplikace identifikátoru URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="c1105-485">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="c1105-486">Použití `SingleOrg` s `IndividualB2C` ověřováním nebo ověřování.</span><span class="sxs-lookup"><span data-stu-id="c1105-486">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c1105-487">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="c1105-487">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="c1105-488">Umožňuje této aplikaci přístup pro čtení do adresáře.</span><span class="sxs-lookup"><span data-stu-id="c1105-488">Allows this application read-access to the directory.</span></span> <span data-ttu-id="c1105-489">Platí pouze `SingleOrg` pro `MultiOrg` nebo ověřování.</span><span class="sxs-lookup"><span data-stu-id="c1105-489">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="c1105-490">Nezahrnuje *launchSettings.json* z generované šablony.</span><span class="sxs-lookup"><span data-stu-id="c1105-490">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="c1105-491">Vypne protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c1105-491">Turns off HTTPS.</span></span> <span data-ttu-id="c1105-492">Tato možnost platí `Individual`pouze `IndividualB2C` `SingleOrg`v `MultiOrg` případě, , , , nebo nejsou používány.</span><span class="sxs-lookup"><span data-stu-id="c1105-492">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="c1105-493">Určuje LocalDB by měl být použit místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="c1105-493">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c1105-494">Platí pouze `Individual` pro `IndividualB2C` nebo ověřování.</span><span class="sxs-lookup"><span data-stu-id="c1105-494">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c1105-495">Určuje [rámec,](../../standard/frameworks.md) na který má být cílit.</span><span class="sxs-lookup"><span data-stu-id="c1105-495">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c1105-496">Možnost je k dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="c1105-496">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="c1105-497">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, které používáte:</span><span class="sxs-lookup"><span data-stu-id="c1105-497">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="c1105-498">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="c1105-498">SDK version</span></span> | <span data-ttu-id="c1105-499">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="c1105-499">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="c1105-500">3.1</span><span class="sxs-lookup"><span data-stu-id="c1105-500">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="c1105-501">3.0</span><span class="sxs-lookup"><span data-stu-id="c1105-501">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="c1105-502">Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="c1105-502">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="c1105-503">Zahrnuje BrowserLink v projektu.</span><span class="sxs-lookup"><span data-stu-id="c1105-503">Includes BrowserLink in the project.</span></span> <span data-ttu-id="c1105-504">Možnost není k dispozici v .NET Core 2.2 a 3.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="c1105-504">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

***

### <a name="spa"></a><span data-ttu-id="c1105-505">úhlové, reagovat</span><span class="sxs-lookup"><span data-stu-id="c1105-505">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="c1105-506">Typ ověřování, které chcete použít.</span><span class="sxs-lookup"><span data-stu-id="c1105-506">The type of authentication to use.</span></span> <span data-ttu-id="c1105-507">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="c1105-507">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="c1105-508">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="c1105-508">The possible values are:</span></span>

  - <span data-ttu-id="c1105-509">`None`- Žádné ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="c1105-509">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="c1105-510">`Individual`- Individuální autentizace.</span><span class="sxs-lookup"><span data-stu-id="c1105-510">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="c1105-511">Nezahrnuje *launchSettings.json* z generované šablony.</span><span class="sxs-lookup"><span data-stu-id="c1105-511">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="c1105-512">Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="c1105-512">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="c1105-513">Vypne protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c1105-513">Turns off HTTPS.</span></span> <span data-ttu-id="c1105-514">Tato možnost platí pouze `None`v případě, že ověřování je .</span><span class="sxs-lookup"><span data-stu-id="c1105-514">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="c1105-515">Určuje LocalDB by měl být použit místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="c1105-515">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c1105-516">Platí pouze `Individual` pro `IndividualB2C` nebo ověřování.</span><span class="sxs-lookup"><span data-stu-id="c1105-516">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c1105-517">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="c1105-517">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c1105-518">Určuje [rámec,](../../standard/frameworks.md) na který má být cílit.</span><span class="sxs-lookup"><span data-stu-id="c1105-518">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c1105-519">Možnost není k dispozici v sada .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="c1105-519">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="c1105-520">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, které používáte:</span><span class="sxs-lookup"><span data-stu-id="c1105-520">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="c1105-521">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="c1105-521">SDK version</span></span> | <span data-ttu-id="c1105-522">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="c1105-522">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="c1105-523">3.1</span><span class="sxs-lookup"><span data-stu-id="c1105-523">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="c1105-524">3.0</span><span class="sxs-lookup"><span data-stu-id="c1105-524">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="c1105-525">2.1</span><span class="sxs-lookup"><span data-stu-id="c1105-525">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="c1105-526">reactredux</span><span class="sxs-lookup"><span data-stu-id="c1105-526">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="c1105-527">Nezahrnuje *launchSettings.json* z generované šablony.</span><span class="sxs-lookup"><span data-stu-id="c1105-527">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c1105-528">Určuje [rámec,](../../standard/frameworks.md) na který má být cílit.</span><span class="sxs-lookup"><span data-stu-id="c1105-528">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c1105-529">Možnost není k dispozici v sada .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="c1105-529">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="c1105-530">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, které používáte:</span><span class="sxs-lookup"><span data-stu-id="c1105-530">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="c1105-531">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="c1105-531">SDK version</span></span> | <span data-ttu-id="c1105-532">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="c1105-532">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="c1105-533">3.1</span><span class="sxs-lookup"><span data-stu-id="c1105-533">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="c1105-534">3.0</span><span class="sxs-lookup"><span data-stu-id="c1105-534">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="c1105-535">2.1</span><span class="sxs-lookup"><span data-stu-id="c1105-535">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="c1105-536">Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="c1105-536">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="c1105-537">Vypne protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c1105-537">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="c1105-538">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="c1105-538">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="c1105-539">Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="c1105-539">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="c1105-540">Podporuje přidávání tradičních stránek Razor a zobrazení kromě komponent do této knihovny.</span><span class="sxs-lookup"><span data-stu-id="c1105-540">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="c1105-541">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="c1105-541">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="c1105-542">webapi</span><span class="sxs-lookup"><span data-stu-id="c1105-542">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="c1105-543">Typ ověřování, které chcete použít.</span><span class="sxs-lookup"><span data-stu-id="c1105-543">The type of authentication to use.</span></span> <span data-ttu-id="c1105-544">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="c1105-544">The possible values are:</span></span>

  - <span data-ttu-id="c1105-545">`None`- Žádné ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="c1105-545">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="c1105-546">`IndividualB2C`- Individuální ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="c1105-546">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="c1105-547">`SingleOrg`- Organizační ověřování pro jednoho klienta.</span><span class="sxs-lookup"><span data-stu-id="c1105-547">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="c1105-548">`Windows`- Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="c1105-548">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="c1105-549">Instance Azure Active Directory B2C, ke které se chcete připojit.</span><span class="sxs-lookup"><span data-stu-id="c1105-549">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="c1105-550">Použití `IndividualB2C` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="c1105-550">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="c1105-551">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="c1105-551">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="c1105-552">ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="c1105-552">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="c1105-553">Použití `IndividualB2C` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="c1105-553">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="c1105-554">Instance služby Azure Active Directory, ke které se chcete připojit.</span><span class="sxs-lookup"><span data-stu-id="c1105-554">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="c1105-555">Použití `SingleOrg` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="c1105-555">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c1105-556">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="c1105-556">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="c1105-557">ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="c1105-557">The Client ID for this project.</span></span> <span data-ttu-id="c1105-558">Použití `IndividualB2C` s `SingleOrg` ověřováním nebo ověřování.</span><span class="sxs-lookup"><span data-stu-id="c1105-558">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="c1105-559">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="c1105-559">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="c1105-560">Doména klienta adresáře.</span><span class="sxs-lookup"><span data-stu-id="c1105-560">The domain for the directory tenant.</span></span> <span data-ttu-id="c1105-561">Použití `IndividualB2C` s `SingleOrg` ověřováním nebo ověřování.</span><span class="sxs-lookup"><span data-stu-id="c1105-561">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="c1105-562">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="c1105-562">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="c1105-563">ID ID ID tenantid adresáře, ke kterému se chcete připojit.</span><span class="sxs-lookup"><span data-stu-id="c1105-563">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="c1105-564">Použití `SingleOrg` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="c1105-564">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c1105-565">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="c1105-565">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="c1105-566">Umožňuje této aplikaci přístup pro čtení do adresáře.</span><span class="sxs-lookup"><span data-stu-id="c1105-566">Allows this application read-access to the directory.</span></span> <span data-ttu-id="c1105-567">Platí pouze `SingleOrg` pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="c1105-567">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="c1105-568">Nezahrnuje *launchSettings.json* z generované šablony.</span><span class="sxs-lookup"><span data-stu-id="c1105-568">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="c1105-569">Vypne protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c1105-569">Turns off HTTPS.</span></span> <span data-ttu-id="c1105-570">`app.UseHsts`a `app.UseHttpsRedirection` nejsou přidány `Startup.Configure`do .</span><span class="sxs-lookup"><span data-stu-id="c1105-570">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="c1105-571">Tato možnost platí `IndividualB2C` pouze `SingleOrg` v případě, že se k ověřování používá nebo nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="c1105-571">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="c1105-572">Určuje LocalDB by měl být použit místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="c1105-572">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c1105-573">Platí pouze `IndividualB2C` pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="c1105-573">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c1105-574">Určuje [rámec,](../../standard/frameworks.md) na který má být cílit.</span><span class="sxs-lookup"><span data-stu-id="c1105-574">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c1105-575">Možnost není k dispozici v sada .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="c1105-575">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="c1105-576">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, které používáte:</span><span class="sxs-lookup"><span data-stu-id="c1105-576">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="c1105-577">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="c1105-577">SDK version</span></span> | <span data-ttu-id="c1105-578">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="c1105-578">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="c1105-579">3.1</span><span class="sxs-lookup"><span data-stu-id="c1105-579">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="c1105-580">3.0</span><span class="sxs-lookup"><span data-stu-id="c1105-580">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="c1105-581">2.1</span><span class="sxs-lookup"><span data-stu-id="c1105-581">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="c1105-582">Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="c1105-582">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="c1105-583">globaljson</span><span class="sxs-lookup"><span data-stu-id="c1105-583">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="c1105-584">Určuje verzi sady .NET Core SDK, která má být používána v souboru *global.json.*</span><span class="sxs-lookup"><span data-stu-id="c1105-584">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="c1105-585">Příklady</span><span class="sxs-lookup"><span data-stu-id="c1105-585">Examples</span></span>

- <span data-ttu-id="c1105-586">Vytvořte projekt aplikace konzoly Jazyka C# zadáním názvu šablony:</span><span class="sxs-lookup"><span data-stu-id="c1105-586">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="c1105-587">Vytvořte projekt aplikace konzoly F# v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="c1105-587">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang F#
  ```

- <span data-ttu-id="c1105-588">Vytvořte projekt knihovny tříd .NET Standard v zadaném adresáři:</span><span class="sxs-lookup"><span data-stu-id="c1105-588">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="c1105-589">Vytvořte nový ASP.NET projektu Core C# MVC v aktuálním adresáři bez ověřování:</span><span class="sxs-lookup"><span data-stu-id="c1105-589">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="c1105-590">Vytvořte nový projekt xUnit:</span><span class="sxs-lookup"><span data-stu-id="c1105-590">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="c1105-591">Seznam všech šablon dostupných pro jednostránkové aplikace (SPA) šablony:</span><span class="sxs-lookup"><span data-stu-id="c1105-591">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="c1105-592">Seznam všech šablon odpovídajících podřetězci *we.*</span><span class="sxs-lookup"><span data-stu-id="c1105-592">List all templates matching the *we* substring.</span></span> <span data-ttu-id="c1105-593">Nebyla nalezena žádná přesná shoda, takže porovnávání podřetězců se spustí proti sloupcům krátkého názvu i názvu.</span><span class="sxs-lookup"><span data-stu-id="c1105-593">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="c1105-594">Pokus o vyvolání šablony odpovídající *ng*.</span><span class="sxs-lookup"><span data-stu-id="c1105-594">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="c1105-595">Pokud nelze určit jednu shodu, uveďte šablony, které se částečně shodují.</span><span class="sxs-lookup"><span data-stu-id="c1105-595">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="c1105-596">Nainstalujte verzi 2.0 šablon SPA pro ASP.NET Core:</span><span class="sxs-lookup"><span data-stu-id="c1105-596">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="c1105-597">Seznam nainstalovaných šablon a podrobnosti o nich, včetně toho, jak je odinstalovat:</span><span class="sxs-lookup"><span data-stu-id="c1105-597">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="c1105-598">Vytvořte *soubor global.json* v aktuálním adresáři, který nastavuje verzi sady SDK na 3.1.101:</span><span class="sxs-lookup"><span data-stu-id="c1105-598">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="c1105-599">Viz také</span><span class="sxs-lookup"><span data-stu-id="c1105-599">See also</span></span>

- [<span data-ttu-id="c1105-600">Vlastní šablony pro dotnet nové</span><span class="sxs-lookup"><span data-stu-id="c1105-600">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="c1105-601">Vytvoření vlastní šablony pro dotnet new</span><span class="sxs-lookup"><span data-stu-id="c1105-601">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="c1105-602">úložiště GitHub u dotnet/dotnet-template-samples GitHub</span><span class="sxs-lookup"><span data-stu-id="c1105-602">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="c1105-603">Dostupné šablony pro dotnet nové</span><span class="sxs-lookup"><span data-stu-id="c1105-603">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
