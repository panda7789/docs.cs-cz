---
title: dotnet nový příkaz
description: Nový příkaz dotnet vytvoří nové projekty .NET Core založené na zadané šabloně.
ms.date: 04/10/2020
ms.openlocfilehash: 4ad0d7e54f93582237ed9457b562957018916d36
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463616"
---
# <a name="dotnet-new"></a><span data-ttu-id="a0028-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="a0028-103">dotnet new</span></span>

<span data-ttu-id="a0028-104">**Tento článek se týká:** ✔️ .NET Core 2.0 SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="a0028-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="a0028-105">Název</span><span class="sxs-lookup"><span data-stu-id="a0028-105">Name</span></span>

<span data-ttu-id="a0028-106">`dotnet new`- Vytvoří nový projekt, konfigurační soubor nebo řešení založené na zadané šabloně.</span><span class="sxs-lookup"><span data-stu-id="a0028-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a0028-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="a0028-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {C#|F#|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="a0028-108">Popis</span><span class="sxs-lookup"><span data-stu-id="a0028-108">Description</span></span>

<span data-ttu-id="a0028-109">Příkaz `dotnet new` vytvoří projekt .NET Core nebo jiné artefakty založené na šabloně.</span><span class="sxs-lookup"><span data-stu-id="a0028-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="a0028-110">Příkaz volá [modul šablony](https://github.com/dotnet/templating) k vytvoření artefaktů na disku na základě zadané šablony a možností.</span><span class="sxs-lookup"><span data-stu-id="a0028-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="a0028-111">Argumenty</span><span class="sxs-lookup"><span data-stu-id="a0028-111">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="a0028-112">Šablona k vytvoření instance při vyvolání příkazu.</span><span class="sxs-lookup"><span data-stu-id="a0028-112">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="a0028-113">Každá šablona může mít konkrétní možnosti, které můžete předat.</span><span class="sxs-lookup"><span data-stu-id="a0028-113">Each template might have specific options you can pass.</span></span> <span data-ttu-id="a0028-114">Další informace naleznete v [tématu Možnosti šablony](#template-options).</span><span class="sxs-lookup"><span data-stu-id="a0028-114">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="a0028-115">Seznam všech `dotnet new --list` nainstalovaných šablon můžete spustit.</span><span class="sxs-lookup"><span data-stu-id="a0028-115">You can run `dotnet new --list` to see a list of all installed templates.</span></span> <span data-ttu-id="a0028-116">Pokud `TEMPLATE` hodnota není přesná shoda na text ve **sloupci Šablony** nebo **krátký název** z vrácené tabulky, podřetězec shoda se provádí na tyto dva sloupce.</span><span class="sxs-lookup"><span data-stu-id="a0028-116">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="a0028-117">Počínaje sadou .NET Core 3.0 SDK hledá rozhraní příkazového příkazu šablony v NuGet.org při vyvolání příkazu `dotnet new` za následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="a0028-117">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="a0028-118">Pokud clI nemůže najít šablonu zápas při `dotnet new`vyvolání , ani částečné.</span><span class="sxs-lookup"><span data-stu-id="a0028-118">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="a0028-119">Pokud je k dispozici novější verze šablony.</span><span class="sxs-lookup"><span data-stu-id="a0028-119">If there's a newer version of the template available.</span></span> <span data-ttu-id="a0028-120">V tomto případě je vytvořen projekt nebo artefakt, ale CLI vás upozorní na aktualizovanou verzi šablony.</span><span class="sxs-lookup"><span data-stu-id="a0028-120">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="a0028-121">Příkaz obsahuje výchozí seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="a0028-121">The command contains a default list of templates.</span></span> <span data-ttu-id="a0028-122">Slouží `dotnet new -l` k získání seznamu dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="a0028-122">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="a0028-123">V následující tabulce jsou uvedeny šablony, které jsou předinstalovány se sadou .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="a0028-123">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="a0028-124">Výchozí jazyk šablony je zobrazen uvnitř závorek.</span><span class="sxs-lookup"><span data-stu-id="a0028-124">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="a0028-125">Kliknutím na odkaz krátký název zobrazíte konkrétní možnosti šablony.</span><span class="sxs-lookup"><span data-stu-id="a0028-125">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="a0028-126">Šablony</span><span class="sxs-lookup"><span data-stu-id="a0028-126">Templates</span></span>                                    | <span data-ttu-id="a0028-127">Krátký název</span><span class="sxs-lookup"><span data-stu-id="a0028-127">Short name</span></span>                      | <span data-ttu-id="a0028-128">Jazyk</span><span class="sxs-lookup"><span data-stu-id="a0028-128">Language</span></span>     | <span data-ttu-id="a0028-129">Značky</span><span class="sxs-lookup"><span data-stu-id="a0028-129">Tags</span></span>                                  | <span data-ttu-id="a0028-130">Zavedena</span><span class="sxs-lookup"><span data-stu-id="a0028-130">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="a0028-131">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="a0028-131">Console Application</span></span>                          | [<span data-ttu-id="a0028-132">Konzoly</span><span class="sxs-lookup"><span data-stu-id="a0028-132">console</span></span>](#console)             | <span data-ttu-id="a0028-133">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="a0028-133">[C#], F#, VB</span></span> | <span data-ttu-id="a0028-134">Běžné/konzolové</span><span class="sxs-lookup"><span data-stu-id="a0028-134">Common/Console</span></span>                        | <span data-ttu-id="a0028-135">1.0</span><span class="sxs-lookup"><span data-stu-id="a0028-135">1.0</span></span>        |
| <span data-ttu-id="a0028-136">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="a0028-136">Class library</span></span>                                | [<span data-ttu-id="a0028-137">classlib</span><span class="sxs-lookup"><span data-stu-id="a0028-137">classlib</span></span>](#classlib)           | <span data-ttu-id="a0028-138">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="a0028-138">[C#], F#, VB</span></span> | <span data-ttu-id="a0028-139">Společné/Knihovna</span><span class="sxs-lookup"><span data-stu-id="a0028-139">Common/Library</span></span>                        | <span data-ttu-id="a0028-140">1.0</span><span class="sxs-lookup"><span data-stu-id="a0028-140">1.0</span></span>        |
| <span data-ttu-id="a0028-141">Aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="a0028-141">WPF Application</span></span>                              | [<span data-ttu-id="a0028-142">Wpf</span><span class="sxs-lookup"><span data-stu-id="a0028-142">wpf</span></span>](#wpf)                     | <span data-ttu-id="a0028-143">[C#]</span><span class="sxs-lookup"><span data-stu-id="a0028-143">[C#]</span></span>         | <span data-ttu-id="a0028-144">Časté/WPF</span><span class="sxs-lookup"><span data-stu-id="a0028-144">Common/WPF</span></span>                            | <span data-ttu-id="a0028-145">3.0</span><span class="sxs-lookup"><span data-stu-id="a0028-145">3.0</span></span>        |
| <span data-ttu-id="a0028-146">Knihovna tříd WPF</span><span class="sxs-lookup"><span data-stu-id="a0028-146">WPF Class library</span></span>                            | [<span data-ttu-id="a0028-147">wpflib</span><span class="sxs-lookup"><span data-stu-id="a0028-147">wpflib</span></span>](#wpf)                  | <span data-ttu-id="a0028-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="a0028-148">[C#]</span></span>         | <span data-ttu-id="a0028-149">Časté/WPF</span><span class="sxs-lookup"><span data-stu-id="a0028-149">Common/WPF</span></span>                            | <span data-ttu-id="a0028-150">3.0</span><span class="sxs-lookup"><span data-stu-id="a0028-150">3.0</span></span>        |
| <span data-ttu-id="a0028-151">Knihovna vlastních ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="a0028-151">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="a0028-152">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="a0028-152">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="a0028-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="a0028-153">[C#]</span></span>         | <span data-ttu-id="a0028-154">Časté/WPF</span><span class="sxs-lookup"><span data-stu-id="a0028-154">Common/WPF</span></span>                            | <span data-ttu-id="a0028-155">3.0</span><span class="sxs-lookup"><span data-stu-id="a0028-155">3.0</span></span>        |
| <span data-ttu-id="a0028-156">Knihovna uživatelských ovládacích prveků WPF</span><span class="sxs-lookup"><span data-stu-id="a0028-156">WPF User Control Library</span></span>                     | [<span data-ttu-id="a0028-157">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="a0028-157">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="a0028-158">[C#]</span><span class="sxs-lookup"><span data-stu-id="a0028-158">[C#]</span></span>         | <span data-ttu-id="a0028-159">Časté/WPF</span><span class="sxs-lookup"><span data-stu-id="a0028-159">Common/WPF</span></span>                            | <span data-ttu-id="a0028-160">3.0</span><span class="sxs-lookup"><span data-stu-id="a0028-160">3.0</span></span>        |
| <span data-ttu-id="a0028-161">Aplikace Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="a0028-161">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="a0028-162">Winforms</span><span class="sxs-lookup"><span data-stu-id="a0028-162">winforms</span></span>](#winforms)           | <span data-ttu-id="a0028-163">[C#]</span><span class="sxs-lookup"><span data-stu-id="a0028-163">[C#]</span></span>         | <span data-ttu-id="a0028-164">Běžné/WinForms</span><span class="sxs-lookup"><span data-stu-id="a0028-164">Common/WinForms</span></span>                       | <span data-ttu-id="a0028-165">3.0</span><span class="sxs-lookup"><span data-stu-id="a0028-165">3.0</span></span>        |
| <span data-ttu-id="a0028-166">Knihovna tříd Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="a0028-166">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="a0028-167">winformslib</span><span class="sxs-lookup"><span data-stu-id="a0028-167">winformslib</span></span>](#winforms)        | <span data-ttu-id="a0028-168">[C#]</span><span class="sxs-lookup"><span data-stu-id="a0028-168">[C#]</span></span>         | <span data-ttu-id="a0028-169">Běžné/WinForms</span><span class="sxs-lookup"><span data-stu-id="a0028-169">Common/WinForms</span></span>                       | <span data-ttu-id="a0028-170">3.0</span><span class="sxs-lookup"><span data-stu-id="a0028-170">3.0</span></span>        |
| <span data-ttu-id="a0028-171">Pracovní služba</span><span class="sxs-lookup"><span data-stu-id="a0028-171">Worker Service</span></span>                               | [<span data-ttu-id="a0028-172">Pracovník</span><span class="sxs-lookup"><span data-stu-id="a0028-172">worker</span></span>](#web-others)           | <span data-ttu-id="a0028-173">[C#]</span><span class="sxs-lookup"><span data-stu-id="a0028-173">[C#]</span></span>         | <span data-ttu-id="a0028-174">Běžné/Pracovník/Web</span><span class="sxs-lookup"><span data-stu-id="a0028-174">Common/Worker/Web</span></span>                     | <span data-ttu-id="a0028-175">3.0</span><span class="sxs-lookup"><span data-stu-id="a0028-175">3.0</span></span>        |
| <span data-ttu-id="a0028-176">Projekt testování částí</span><span class="sxs-lookup"><span data-stu-id="a0028-176">Unit Test Project</span></span>                            | [<span data-ttu-id="a0028-177">mstest</span><span class="sxs-lookup"><span data-stu-id="a0028-177">mstest</span></span>](#test)                 | <span data-ttu-id="a0028-178">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="a0028-178">[C#], F#, VB</span></span> | <span data-ttu-id="a0028-179">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="a0028-179">Test/MSTest</span></span>                           | <span data-ttu-id="a0028-180">1.0</span><span class="sxs-lookup"><span data-stu-id="a0028-180">1.0</span></span>        |
| <span data-ttu-id="a0028-181">Testovací projekt NUnit 3</span><span class="sxs-lookup"><span data-stu-id="a0028-181">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="a0028-182">nunit</span><span class="sxs-lookup"><span data-stu-id="a0028-182">nunit</span></span>](#nunit)                  | <span data-ttu-id="a0028-183">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="a0028-183">[C#], F#, VB</span></span> | <span data-ttu-id="a0028-184">Testovací/NUnit</span><span class="sxs-lookup"><span data-stu-id="a0028-184">Test/NUnit</span></span>                            | <span data-ttu-id="a0028-185">2.1.400</span><span class="sxs-lookup"><span data-stu-id="a0028-185">2.1.400</span></span>    |
| <span data-ttu-id="a0028-186">Testovací položka NUnit 3</span><span class="sxs-lookup"><span data-stu-id="a0028-186">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="a0028-187">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="a0028-187">[C#], F#, VB</span></span> | <span data-ttu-id="a0028-188">Testovací/NUnit</span><span class="sxs-lookup"><span data-stu-id="a0028-188">Test/NUnit</span></span>                            | <span data-ttu-id="a0028-189">2,2</span><span class="sxs-lookup"><span data-stu-id="a0028-189">2.2</span></span>        |
| <span data-ttu-id="a0028-190">XUnit testovací projekt</span><span class="sxs-lookup"><span data-stu-id="a0028-190">xUnit Test Project</span></span>                           | [<span data-ttu-id="a0028-191">jednotka x</span><span class="sxs-lookup"><span data-stu-id="a0028-191">xunit</span></span>](#test)                  | <span data-ttu-id="a0028-192">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="a0028-192">[C#], F#, VB</span></span> | <span data-ttu-id="a0028-193">Testovací/xJednotka</span><span class="sxs-lookup"><span data-stu-id="a0028-193">Test/xUnit</span></span>                            | <span data-ttu-id="a0028-194">1.0</span><span class="sxs-lookup"><span data-stu-id="a0028-194">1.0</span></span>        |
| <span data-ttu-id="a0028-195">Komponenta razor</span><span class="sxs-lookup"><span data-stu-id="a0028-195">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="a0028-196">[C#]</span><span class="sxs-lookup"><span data-stu-id="a0028-196">[C#]</span></span>         | <span data-ttu-id="a0028-197">Web/Technologie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="a0028-197">Web/ASP.NET</span></span>                           | <span data-ttu-id="a0028-198">3.0</span><span class="sxs-lookup"><span data-stu-id="a0028-198">3.0</span></span>        |
| <span data-ttu-id="a0028-199">Holicí strojek stránka</span><span class="sxs-lookup"><span data-stu-id="a0028-199">Razor Page</span></span>                                   | [<span data-ttu-id="a0028-200">Stránka</span><span class="sxs-lookup"><span data-stu-id="a0028-200">page</span></span>](#page)                   | <span data-ttu-id="a0028-201">[C#]</span><span class="sxs-lookup"><span data-stu-id="a0028-201">[C#]</span></span>         | <span data-ttu-id="a0028-202">Web/Technologie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="a0028-202">Web/ASP.NET</span></span>                           | <span data-ttu-id="a0028-203">2.0</span><span class="sxs-lookup"><span data-stu-id="a0028-203">2.0</span></span>        |
| <span data-ttu-id="a0028-204">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="a0028-204">MVC ViewImports</span></span>                              | [<span data-ttu-id="a0028-205">viewimports</span><span class="sxs-lookup"><span data-stu-id="a0028-205">viewimports</span></span>](#namespace)       | <span data-ttu-id="a0028-206">[C#]</span><span class="sxs-lookup"><span data-stu-id="a0028-206">[C#]</span></span>         | <span data-ttu-id="a0028-207">Web/Technologie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="a0028-207">Web/ASP.NET</span></span>                           | <span data-ttu-id="a0028-208">2.0</span><span class="sxs-lookup"><span data-stu-id="a0028-208">2.0</span></span>        |
| <span data-ttu-id="a0028-209">Spuštění zobrazení MVC</span><span class="sxs-lookup"><span data-stu-id="a0028-209">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="a0028-210">[C#]</span><span class="sxs-lookup"><span data-stu-id="a0028-210">[C#]</span></span>         | <span data-ttu-id="a0028-211">Web/Technologie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="a0028-211">Web/ASP.NET</span></span>                           | <span data-ttu-id="a0028-212">2.0</span><span class="sxs-lookup"><span data-stu-id="a0028-212">2.0</span></span>        |
| <span data-ttu-id="a0028-213">Aplikace Blazor Server</span><span class="sxs-lookup"><span data-stu-id="a0028-213">Blazor Server App</span></span>                            | [<span data-ttu-id="a0028-214">blazorserver</span><span class="sxs-lookup"><span data-stu-id="a0028-214">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="a0028-215">[C#]</span><span class="sxs-lookup"><span data-stu-id="a0028-215">[C#]</span></span>         | <span data-ttu-id="a0028-216">Web/Blazor</span><span class="sxs-lookup"><span data-stu-id="a0028-216">Web/Blazor</span></span>                            | <span data-ttu-id="a0028-217">3.0</span><span class="sxs-lookup"><span data-stu-id="a0028-217">3.0</span></span>        |
| <span data-ttu-id="a0028-218">ASP.NET jádro prázdné</span><span class="sxs-lookup"><span data-stu-id="a0028-218">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="a0028-219">Webové</span><span class="sxs-lookup"><span data-stu-id="a0028-219">web</span></span>](#web)                     | <span data-ttu-id="a0028-220">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="a0028-220">[C#], F#</span></span>     | <span data-ttu-id="a0028-221">Web/Prázdný</span><span class="sxs-lookup"><span data-stu-id="a0028-221">Web/Empty</span></span>                             | <span data-ttu-id="a0028-222">1.0</span><span class="sxs-lookup"><span data-stu-id="a0028-222">1.0</span></span>        |
| <span data-ttu-id="a0028-223">ASP.NET základní webová aplikace (model-view-controller)</span><span class="sxs-lookup"><span data-stu-id="a0028-223">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="a0028-224">Mvc</span><span class="sxs-lookup"><span data-stu-id="a0028-224">mvc</span></span>](#web-options)             | <span data-ttu-id="a0028-225">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="a0028-225">[C#], F#</span></span>     | <span data-ttu-id="a0028-226">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="a0028-226">Web/MVC</span></span>                               | <span data-ttu-id="a0028-227">1.0</span><span class="sxs-lookup"><span data-stu-id="a0028-227">1.0</span></span>        |
| <span data-ttu-id="a0028-228">ASP.NET základní webová aplikace</span><span class="sxs-lookup"><span data-stu-id="a0028-228">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="a0028-229">webapp, holicí strojek</span><span class="sxs-lookup"><span data-stu-id="a0028-229">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="a0028-230">[C#]</span><span class="sxs-lookup"><span data-stu-id="a0028-230">[C#]</span></span>         | <span data-ttu-id="a0028-231">Webové/MVC/Razor stránky</span><span class="sxs-lookup"><span data-stu-id="a0028-231">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="a0028-232">2.2, 2.0</span><span class="sxs-lookup"><span data-stu-id="a0028-232">2.2, 2.0</span></span>   |
| <span data-ttu-id="a0028-233">ASP.NET jádro s úhlovým</span><span class="sxs-lookup"><span data-stu-id="a0028-233">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="a0028-234">Úhlové</span><span class="sxs-lookup"><span data-stu-id="a0028-234">angular</span></span>](#spa)                 | <span data-ttu-id="a0028-235">[C#]</span><span class="sxs-lookup"><span data-stu-id="a0028-235">[C#]</span></span>         | <span data-ttu-id="a0028-236">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="a0028-236">Web/MVC/SPA</span></span>                           | <span data-ttu-id="a0028-237">2.0</span><span class="sxs-lookup"><span data-stu-id="a0028-237">2.0</span></span>        |
| <span data-ttu-id="a0028-238">ASP.NET jádro s React.js</span><span class="sxs-lookup"><span data-stu-id="a0028-238">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="a0028-239">Reagovat</span><span class="sxs-lookup"><span data-stu-id="a0028-239">react</span></span>](#spa)                   | <span data-ttu-id="a0028-240">[C#]</span><span class="sxs-lookup"><span data-stu-id="a0028-240">[C#]</span></span>         | <span data-ttu-id="a0028-241">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="a0028-241">Web/MVC/SPA</span></span>                           | <span data-ttu-id="a0028-242">2.0</span><span class="sxs-lookup"><span data-stu-id="a0028-242">2.0</span></span>        |
| <span data-ttu-id="a0028-243">ASP.NET jádro s React.js a Redux</span><span class="sxs-lookup"><span data-stu-id="a0028-243">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="a0028-244">reactredux</span><span class="sxs-lookup"><span data-stu-id="a0028-244">reactredux</span></span>](#reactredux)       | <span data-ttu-id="a0028-245">[C#]</span><span class="sxs-lookup"><span data-stu-id="a0028-245">[C#]</span></span>         | <span data-ttu-id="a0028-246">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="a0028-246">Web/MVC/SPA</span></span>                           | <span data-ttu-id="a0028-247">2.0</span><span class="sxs-lookup"><span data-stu-id="a0028-247">2.0</span></span>        |
| <span data-ttu-id="a0028-248">Knihovna třídy Holicí strojek</span><span class="sxs-lookup"><span data-stu-id="a0028-248">Razor Class Library</span></span>                          | [<span data-ttu-id="a0028-249">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="a0028-249">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="a0028-250">[C#]</span><span class="sxs-lookup"><span data-stu-id="a0028-250">[C#]</span></span>         | <span data-ttu-id="a0028-251">Web/Břitva/knihovna/knihovna</span><span class="sxs-lookup"><span data-stu-id="a0028-251">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="a0028-252">2.1</span><span class="sxs-lookup"><span data-stu-id="a0028-252">2.1</span></span>        |
| <span data-ttu-id="a0028-253">Webové rozhraní API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a0028-253">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="a0028-254">webapi</span><span class="sxs-lookup"><span data-stu-id="a0028-254">webapi</span></span>](#webapi)               | <span data-ttu-id="a0028-255">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="a0028-255">[C#], F#</span></span>     | <span data-ttu-id="a0028-256">Webové rozhraní API</span><span class="sxs-lookup"><span data-stu-id="a0028-256">Web/WebAPI</span></span>                            | <span data-ttu-id="a0028-257">1.0</span><span class="sxs-lookup"><span data-stu-id="a0028-257">1.0</span></span>        |
| <span data-ttu-id="a0028-258">ASP.NET Core gRPC Service</span><span class="sxs-lookup"><span data-stu-id="a0028-258">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="a0028-259">grpc</span><span class="sxs-lookup"><span data-stu-id="a0028-259">grpc</span></span>](#web-others)             | <span data-ttu-id="a0028-260">[C#]</span><span class="sxs-lookup"><span data-stu-id="a0028-260">[C#]</span></span>         | <span data-ttu-id="a0028-261">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="a0028-261">Web/gRPC</span></span>                              | <span data-ttu-id="a0028-262">3.0</span><span class="sxs-lookup"><span data-stu-id="a0028-262">3.0</span></span>        |
| <span data-ttu-id="a0028-263">Soubor vyrovnávací paměti protokolu</span><span class="sxs-lookup"><span data-stu-id="a0028-263">Protocol Buffer File</span></span>                         | [<span data-ttu-id="a0028-264">proto</span><span class="sxs-lookup"><span data-stu-id="a0028-264">proto</span></span>](#namespace)             |              | <span data-ttu-id="a0028-265">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="a0028-265">Web/gRPC</span></span>                              | <span data-ttu-id="a0028-266">3.0</span><span class="sxs-lookup"><span data-stu-id="a0028-266">3.0</span></span>        |
| <span data-ttu-id="a0028-267">dotnet gitignore soubor</span><span class="sxs-lookup"><span data-stu-id="a0028-267">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="a0028-268">Config</span><span class="sxs-lookup"><span data-stu-id="a0028-268">Config</span></span>                                | <span data-ttu-id="a0028-269">3.0</span><span class="sxs-lookup"><span data-stu-id="a0028-269">3.0</span></span>        |
| <span data-ttu-id="a0028-270">soubor global.json</span><span class="sxs-lookup"><span data-stu-id="a0028-270">global.json file</span></span>                             | [<span data-ttu-id="a0028-271">globaljson</span><span class="sxs-lookup"><span data-stu-id="a0028-271">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="a0028-272">Config</span><span class="sxs-lookup"><span data-stu-id="a0028-272">Config</span></span>                                | <span data-ttu-id="a0028-273">2.0</span><span class="sxs-lookup"><span data-stu-id="a0028-273">2.0</span></span>        |
| <span data-ttu-id="a0028-274">Konfigurace nugetu</span><span class="sxs-lookup"><span data-stu-id="a0028-274">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="a0028-275">Config</span><span class="sxs-lookup"><span data-stu-id="a0028-275">Config</span></span>                                | <span data-ttu-id="a0028-276">1.0</span><span class="sxs-lookup"><span data-stu-id="a0028-276">1.0</span></span>        |
| <span data-ttu-id="a0028-277">Dotnet místní nástroj manifest soubor</span><span class="sxs-lookup"><span data-stu-id="a0028-277">dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="a0028-278">Config</span><span class="sxs-lookup"><span data-stu-id="a0028-278">Config</span></span>                                | <span data-ttu-id="a0028-279">3.0</span><span class="sxs-lookup"><span data-stu-id="a0028-279">3.0</span></span>        |
| <span data-ttu-id="a0028-280">Konfigurace webu</span><span class="sxs-lookup"><span data-stu-id="a0028-280">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="a0028-281">Config</span><span class="sxs-lookup"><span data-stu-id="a0028-281">Config</span></span>                                | <span data-ttu-id="a0028-282">1.0</span><span class="sxs-lookup"><span data-stu-id="a0028-282">1.0</span></span>        |
| <span data-ttu-id="a0028-283">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="a0028-283">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="a0028-284">Řešení</span><span class="sxs-lookup"><span data-stu-id="a0028-284">Solution</span></span>                              | <span data-ttu-id="a0028-285">1.0</span><span class="sxs-lookup"><span data-stu-id="a0028-285">1.0</span></span>        |

## <a name="options"></a><span data-ttu-id="a0028-286">Možnosti</span><span class="sxs-lookup"><span data-stu-id="a0028-286">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="a0028-287">Zobrazí souhrn toho, co by se stalo, kdyby byl daný příkaz spuštěn.</span><span class="sxs-lookup"><span data-stu-id="a0028-287">Displays a summary of what would happen if the given command were run.</span></span> <span data-ttu-id="a0028-288">K dispozici od .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="a0028-288">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="a0028-289">Vynutí vygenerování obsahu, i když by změnil existující soubory.</span><span class="sxs-lookup"><span data-stu-id="a0028-289">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="a0028-290">To je nutné, pokud vybraná šablona přepíše existující soubory ve výstupním adresáři.</span><span class="sxs-lookup"><span data-stu-id="a0028-290">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="a0028-291">Vytiskne nápovědu pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="a0028-291">Prints out help for the command.</span></span> <span data-ttu-id="a0028-292">Může být vyvolána `dotnet new` pro samotný příkaz nebo pro libovolnou šablonu.</span><span class="sxs-lookup"><span data-stu-id="a0028-292">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="a0028-293">Například, `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="a0028-293">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="a0028-294">Nainstaluje sadu šablon `PATH` z `NUGET_ID` nebo poskytované.</span><span class="sxs-lookup"><span data-stu-id="a0028-294">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="a0028-295">Chcete-li nainstalovat předběžnou verzi balíčku šablony, je třeba zadat verzi `<package-name>::<package-version>`ve formátu .</span><span class="sxs-lookup"><span data-stu-id="a0028-295">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="a0028-296">Ve výchozím `dotnet new` \* nastavení přechází pro verzi, která představuje nejnovější stabilní verzi balíčku.</span><span class="sxs-lookup"><span data-stu-id="a0028-296">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="a0028-297">Viz příklad v části [Příklady.](#examples)</span><span class="sxs-lookup"><span data-stu-id="a0028-297">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="a0028-298">Pokud byla verze šablony již nainstalována při spuštění tohoto příkazu, bude šablona aktualizována na zadanou verzi nebo na nejnovější stabilní verzi, pokud nebyla zadána žádná verze.</span><span class="sxs-lookup"><span data-stu-id="a0028-298">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="a0028-299">Informace o vytváření vlastních šablon naleznete v [tématu Vlastní šablony pro dotnet new](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="a0028-299">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="a0028-300">Zobrazí seznam šablon obsahujících zadaný název.</span><span class="sxs-lookup"><span data-stu-id="a0028-300">Lists templates containing the specified name.</span></span> <span data-ttu-id="a0028-301">Pokud není zadán žádný název, zobrazí seznam všech šablon.</span><span class="sxs-lookup"><span data-stu-id="a0028-301">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="a0028-302">Jazyk šablony, kterou chcete vytvořit.</span><span class="sxs-lookup"><span data-stu-id="a0028-302">The language of the template to create.</span></span> <span data-ttu-id="a0028-303">Přijatý jazyk se liší podle šablony (viz výchozí hodnoty v části [argumenty).](#arguments)</span><span class="sxs-lookup"><span data-stu-id="a0028-303">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="a0028-304">Neplatí pro některé šablony.</span><span class="sxs-lookup"><span data-stu-id="a0028-304">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="a0028-305">Některé skořepiny interpretují `#` jako speciální znak.</span><span class="sxs-lookup"><span data-stu-id="a0028-305">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="a0028-306">V těchto případech uzavřete hodnotu parametru jazyka do uvozovek.</span><span class="sxs-lookup"><span data-stu-id="a0028-306">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="a0028-307">Například, `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="a0028-307">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="a0028-308">Název vytvořeného výstupu.</span><span class="sxs-lookup"><span data-stu-id="a0028-308">The name for the created output.</span></span> <span data-ttu-id="a0028-309">Pokud není zadán žádný název, bude použit název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="a0028-309">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="a0028-310">Určuje zdroj NuGet, který se má použít během instalace.</span><span class="sxs-lookup"><span data-stu-id="a0028-310">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="a0028-311">K dispozici od .NET Core 2.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="a0028-311">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="a0028-312">Umístění pro umístění generovaného výstupu.</span><span class="sxs-lookup"><span data-stu-id="a0028-312">Location to place the generated output.</span></span> <span data-ttu-id="a0028-313">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="a0028-313">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="a0028-314">Filtruje šablony založené na dostupných typech.</span><span class="sxs-lookup"><span data-stu-id="a0028-314">Filters templates based on available types.</span></span> <span data-ttu-id="a0028-315">Předdefinované hodnoty `project` `item`jsou `other`, , nebo .</span><span class="sxs-lookup"><span data-stu-id="a0028-315">Predefined values are `project`, `item`, or `other`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="a0028-316">Odinstaluje sadu `PATH` šablon `NUGET_ID` v aplikaci nebo v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a0028-316">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="a0028-317">Pokud `<PATH|NUGET_ID>` není zadána hodnota, zobrazí se všechny aktuálně nainstalované balíčky šablon a jejich přidružené šablony.</span><span class="sxs-lookup"><span data-stu-id="a0028-317">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="a0028-318">Při zadávání `NUGET_ID`aplikace neuvádějte číslo verze.</span><span class="sxs-lookup"><span data-stu-id="a0028-318">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="a0028-319">Pokud nezadáte parametr této možnosti, příkaz zobrazí seznam nainstalovaných šablon a podrobnosti o nich.</span><span class="sxs-lookup"><span data-stu-id="a0028-319">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="a0028-320">Chcete-li odinstalovat `PATH`šablonu pomocí aplikace , je třeba cestu plně kvalifikovat.</span><span class="sxs-lookup"><span data-stu-id="a0028-320">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="a0028-321">Například *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z obsahující složky nebude.</span><span class="sxs-lookup"><span data-stu-id="a0028-321">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="a0028-322">Nezahrnujte konečné ukončující lomítko adresáře na cestě šablony.</span><span class="sxs-lookup"><span data-stu-id="a0028-322">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="a0028-323">Zkontroluje, zda jsou k dispozici aktualizace pro aktuálně nainstalované balíčky šablon, a nainstaluje je.</span><span class="sxs-lookup"><span data-stu-id="a0028-323">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="a0028-324">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="a0028-324">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="a0028-325">Zkontroluje, zda jsou k dispozici aktualizace pro aktuálně nainstalované balíčky šablon.</span><span class="sxs-lookup"><span data-stu-id="a0028-325">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="a0028-326">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="a0028-326">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="a0028-327">Možnosti šablon</span><span class="sxs-lookup"><span data-stu-id="a0028-327">Template options</span></span>

<span data-ttu-id="a0028-328">Každá šablona projektu může mít k dispozici další možnosti.</span><span class="sxs-lookup"><span data-stu-id="a0028-328">Each project template may have additional options available.</span></span> <span data-ttu-id="a0028-329">Základní šablony mají následující další možnosti:</span><span class="sxs-lookup"><span data-stu-id="a0028-329">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="a0028-330">konzola</span><span class="sxs-lookup"><span data-stu-id="a0028-330">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="a0028-331">Určuje [rámec,](../../standard/frameworks.md) na který má být cílit.</span><span class="sxs-lookup"><span data-stu-id="a0028-331">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="a0028-332">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="a0028-332">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="a0028-333">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, které používáte:</span><span class="sxs-lookup"><span data-stu-id="a0028-333">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="a0028-334">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="a0028-334">SDK version</span></span> | <span data-ttu-id="a0028-335">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="a0028-335">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="a0028-336">3.1</span><span class="sxs-lookup"><span data-stu-id="a0028-336">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="a0028-337">3.0</span><span class="sxs-lookup"><span data-stu-id="a0028-337">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="a0028-338">Nastaví `LangVersion` vlastnost v vytvořeném souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="a0028-338">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="a0028-339">Například použijte `--langVersion 7.3` použít C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="a0028-339">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="a0028-340">Není podporováno pro F#.</span><span class="sxs-lookup"><span data-stu-id="a0028-340">Not supported for F#.</span></span> <span data-ttu-id="a0028-341">K dispozici od .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="a0028-341">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="a0028-342">Seznam výchozích verzí jazyka C# naleznete [v tématu Výchozí verze](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="a0028-342">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="a0028-343">Pokud je zadán, neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="a0028-343">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="a0028-344">K dispozici od .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="a0028-344">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="a0028-345">classlib</span><span class="sxs-lookup"><span data-stu-id="a0028-345">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="a0028-346">Určuje [rámec,](../../standard/frameworks.md) na který má být cílit.</span><span class="sxs-lookup"><span data-stu-id="a0028-346">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="a0028-347">Hodnoty: `netcoreapp<version>` chcete-li vytvořit knihovnu `netstandard<version>` tříd .NET Core nebo vytvořit knihovnu standardních tříd .NET.</span><span class="sxs-lookup"><span data-stu-id="a0028-347">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="a0028-348">Výchozí hodnota je `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="a0028-348">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="a0028-349">Nastaví `LangVersion` vlastnost v vytvořeném souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="a0028-349">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="a0028-350">Například použijte `--langVersion 7.3` použít C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="a0028-350">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="a0028-351">Není podporováno pro F#.</span><span class="sxs-lookup"><span data-stu-id="a0028-351">Not supported for F#.</span></span> <span data-ttu-id="a0028-352">K dispozici od .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="a0028-352">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="a0028-353">Seznam výchozích verzí jazyka C# naleznete [v tématu Výchozí verze](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="a0028-353">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="a0028-354">Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="a0028-354">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a><span data-ttu-id="a0028-355">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="a0028-355">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="a0028-356">Určuje [rámec,](../../standard/frameworks.md) na který má být cílit.</span><span class="sxs-lookup"><span data-stu-id="a0028-356">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="a0028-357">Výchozí hodnota je `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="a0028-357">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="a0028-358">K dispozici od .NET Core 3.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="a0028-358">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="a0028-359">Nastaví `LangVersion` vlastnost v vytvořeném souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="a0028-359">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="a0028-360">Například použijte `--langVersion 7.3` použít C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="a0028-360">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="a0028-361">Seznam výchozích verzí jazyka C# naleznete [v tématu Výchozí verze](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="a0028-361">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="a0028-362">Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="a0028-362">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms-winformslib"></a><a name="winforms"></a><span data-ttu-id="a0028-363">winforms, winformslib</span><span class="sxs-lookup"><span data-stu-id="a0028-363">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="a0028-364">Nastaví `LangVersion` vlastnost v vytvořeném souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="a0028-364">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="a0028-365">Například použijte `--langVersion 7.3` použít C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="a0028-365">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="a0028-366">Seznam výchozích verzí jazyka C# naleznete [v tématu Výchozí verze](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="a0028-366">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="a0028-367">Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="a0028-367">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="worker-grpc"></a><a name="web-others"></a><span data-ttu-id="a0028-368">pracovník, grpc</span><span class="sxs-lookup"><span data-stu-id="a0028-368">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="a0028-369">Určuje [rámec,](../../standard/frameworks.md) na který má být cílit.</span><span class="sxs-lookup"><span data-stu-id="a0028-369">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="a0028-370">Výchozí hodnota je `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="a0028-370">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="a0028-371">K dispozici od .NET Core 3.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="a0028-371">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="a0028-372">Nezahrnuje *launchSettings.json* z generované šablony.</span><span class="sxs-lookup"><span data-stu-id="a0028-372">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="a0028-373">Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="a0028-373">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="mstest-xunit"></a><a name="test"></a><span data-ttu-id="a0028-374">mstest, xunit</span><span class="sxs-lookup"><span data-stu-id="a0028-374">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="a0028-375">Určuje [rámec,](../../standard/frameworks.md) na který má být cílit.</span><span class="sxs-lookup"><span data-stu-id="a0028-375">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="a0028-376">Možnost je k dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="a0028-376">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="a0028-377">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, které používáte:</span><span class="sxs-lookup"><span data-stu-id="a0028-377">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="a0028-378">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="a0028-378">SDK version</span></span> | <span data-ttu-id="a0028-379">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="a0028-379">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="a0028-380">3.1</span><span class="sxs-lookup"><span data-stu-id="a0028-380">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="a0028-381">3.0</span><span class="sxs-lookup"><span data-stu-id="a0028-381">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="a0028-382">Umožňuje balení pro projekt pomocí [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="a0028-382">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="a0028-383">Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="a0028-383">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="a0028-384">nunit</span><span class="sxs-lookup"><span data-stu-id="a0028-384">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="a0028-385">Určuje [rámec,](../../standard/frameworks.md) na který má být cílit.</span><span class="sxs-lookup"><span data-stu-id="a0028-385">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="a0028-386">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, které používáte:</span><span class="sxs-lookup"><span data-stu-id="a0028-386">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="a0028-387">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="a0028-387">SDK version</span></span> | <span data-ttu-id="a0028-388">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="a0028-388">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="a0028-389">3.1</span><span class="sxs-lookup"><span data-stu-id="a0028-389">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="a0028-390">3.0</span><span class="sxs-lookup"><span data-stu-id="a0028-390">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="a0028-391">2,2</span><span class="sxs-lookup"><span data-stu-id="a0028-391">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="a0028-392">2.1</span><span class="sxs-lookup"><span data-stu-id="a0028-392">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="a0028-393">Umožňuje balení pro projekt pomocí [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="a0028-393">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="a0028-394">Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="a0028-394">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="a0028-395">Stránka</span><span class="sxs-lookup"><span data-stu-id="a0028-395">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="a0028-396">Obor názvů pro generovaný kód.</span><span class="sxs-lookup"><span data-stu-id="a0028-396">Namespace for the generated code.</span></span> <span data-ttu-id="a0028-397">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="a0028-397">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="a0028-398">Vytvoří stránku bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="a0028-398">Creates the page without a PageModel.</span></span>

***

### <a name="viewimports-proto"></a><a name="namespace"></a><span data-ttu-id="a0028-399">viewimports, proto</span><span class="sxs-lookup"><span data-stu-id="a0028-399">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="a0028-400">Obor názvů pro generovaný kód.</span><span class="sxs-lookup"><span data-stu-id="a0028-400">Namespace for the generated code.</span></span> <span data-ttu-id="a0028-401">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="a0028-401">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="a0028-402">blazorserver</span><span class="sxs-lookup"><span data-stu-id="a0028-402">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="a0028-403">Typ ověřování, které chcete použít.</span><span class="sxs-lookup"><span data-stu-id="a0028-403">The type of authentication to use.</span></span> <span data-ttu-id="a0028-404">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="a0028-404">The possible values are:</span></span>

  - <span data-ttu-id="a0028-405">`None`- Žádné ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="a0028-405">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="a0028-406">`Individual`- Individuální autentizace.</span><span class="sxs-lookup"><span data-stu-id="a0028-406">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="a0028-407">`IndividualB2C`- Individuální ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="a0028-407">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="a0028-408">`SingleOrg`- Organizační ověřování pro jednoho klienta.</span><span class="sxs-lookup"><span data-stu-id="a0028-408">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="a0028-409">`MultiOrg`- Organizační ověřování pro více klientů.</span><span class="sxs-lookup"><span data-stu-id="a0028-409">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="a0028-410">`Windows`- Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="a0028-410">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="a0028-411">Instance Azure Active Directory B2C, ke které se chcete připojit.</span><span class="sxs-lookup"><span data-stu-id="a0028-411">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="a0028-412">Použití `IndividualB2C` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="a0028-412">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="a0028-413">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="a0028-413">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="a0028-414">ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="a0028-414">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="a0028-415">Použití `IndividualB2C` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="a0028-415">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="a0028-416">ID zásady obnovení hesla pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="a0028-416">The reset password policy ID for this project.</span></span> <span data-ttu-id="a0028-417">Použití `IndividualB2C` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="a0028-417">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="a0028-418">ID zásady úpravy profilu pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="a0028-418">The edit profile policy ID for this project.</span></span> <span data-ttu-id="a0028-419">Použití `IndividualB2C` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="a0028-419">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="a0028-420">Instance služby Azure Active Directory, ke které se chcete připojit.</span><span class="sxs-lookup"><span data-stu-id="a0028-420">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="a0028-421">Použití `SingleOrg` s `MultiOrg` ověřováním nebo ověřování.</span><span class="sxs-lookup"><span data-stu-id="a0028-421">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="a0028-422">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="a0028-422">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="a0028-423">ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="a0028-423">The Client ID for this project.</span></span> <span data-ttu-id="a0028-424">Použití `IndividualB2C`s `SingleOrg`protokolem , nebo `MultiOrg` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="a0028-424">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="a0028-425">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="a0028-425">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="a0028-426">Doména klienta adresáře.</span><span class="sxs-lookup"><span data-stu-id="a0028-426">The domain for the directory tenant.</span></span> <span data-ttu-id="a0028-427">Použití `SingleOrg` s `IndividualB2C` ověřováním nebo ověřování.</span><span class="sxs-lookup"><span data-stu-id="a0028-427">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="a0028-428">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="a0028-428">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="a0028-429">ID ID ID tenantid adresáře, ke kterému se chcete připojit.</span><span class="sxs-lookup"><span data-stu-id="a0028-429">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="a0028-430">Použití `SingleOrg` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="a0028-430">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="a0028-431">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="a0028-431">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="a0028-432">Cesta požadavku v rámci základní cesty aplikace identifikátoru URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="a0028-432">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="a0028-433">Použití `SingleOrg` s `IndividualB2C` ověřováním nebo ověřování.</span><span class="sxs-lookup"><span data-stu-id="a0028-433">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="a0028-434">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="a0028-434">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="a0028-435">Umožňuje této aplikaci přístup pro čtení do adresáře.</span><span class="sxs-lookup"><span data-stu-id="a0028-435">Allows this application read-access to the directory.</span></span> <span data-ttu-id="a0028-436">Platí pouze `SingleOrg` pro `MultiOrg` nebo ověřování.</span><span class="sxs-lookup"><span data-stu-id="a0028-436">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="a0028-437">Nezahrnuje *launchSettings.json* z generované šablony.</span><span class="sxs-lookup"><span data-stu-id="a0028-437">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="a0028-438">Vypne protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a0028-438">Turns off HTTPS.</span></span> <span data-ttu-id="a0028-439">Tato možnost platí `Individual`pouze `IndividualB2C` `SingleOrg`v `MultiOrg` případě, že se `--auth`pro .</span><span class="sxs-lookup"><span data-stu-id="a0028-439">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="a0028-440">Určuje LocalDB by měl být použit místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="a0028-440">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="a0028-441">Platí pouze `Individual` pro `IndividualB2C` nebo ověřování.</span><span class="sxs-lookup"><span data-stu-id="a0028-441">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="a0028-442">Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="a0028-442">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="a0028-443">web</span><span class="sxs-lookup"><span data-stu-id="a0028-443">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="a0028-444">Nezahrnuje *launchSettings.json* z generované šablony.</span><span class="sxs-lookup"><span data-stu-id="a0028-444">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="a0028-445">Určuje [rámec,](../../standard/frameworks.md) na který má být cílit.</span><span class="sxs-lookup"><span data-stu-id="a0028-445">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="a0028-446">Možnost není k dispozici v sada .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="a0028-446">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="a0028-447">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, které používáte:</span><span class="sxs-lookup"><span data-stu-id="a0028-447">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="a0028-448">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="a0028-448">SDK version</span></span> | <span data-ttu-id="a0028-449">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="a0028-449">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="a0028-450">3.1</span><span class="sxs-lookup"><span data-stu-id="a0028-450">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="a0028-451">3.0</span><span class="sxs-lookup"><span data-stu-id="a0028-451">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="a0028-452">2.1</span><span class="sxs-lookup"><span data-stu-id="a0028-452">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="a0028-453">Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="a0028-453">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="a0028-454">Vypne protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a0028-454">Turns off HTTPS.</span></span>

***

### <a name="mvc-webapp"></a><a name="web-options"></a><span data-ttu-id="a0028-455">mvc, webapp</span><span class="sxs-lookup"><span data-stu-id="a0028-455">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="a0028-456">Typ ověřování, které chcete použít.</span><span class="sxs-lookup"><span data-stu-id="a0028-456">The type of authentication to use.</span></span> <span data-ttu-id="a0028-457">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="a0028-457">The possible values are:</span></span>

  - <span data-ttu-id="a0028-458">`None`- Žádné ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="a0028-458">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="a0028-459">`Individual`- Individuální autentizace.</span><span class="sxs-lookup"><span data-stu-id="a0028-459">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="a0028-460">`IndividualB2C`- Individuální ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="a0028-460">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="a0028-461">`SingleOrg`- Organizační ověřování pro jednoho klienta.</span><span class="sxs-lookup"><span data-stu-id="a0028-461">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="a0028-462">`MultiOrg`- Organizační ověřování pro více klientů.</span><span class="sxs-lookup"><span data-stu-id="a0028-462">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="a0028-463">`Windows`- Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="a0028-463">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="a0028-464">Instance Azure Active Directory B2C, ke které se chcete připojit.</span><span class="sxs-lookup"><span data-stu-id="a0028-464">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="a0028-465">Použití `IndividualB2C` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="a0028-465">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="a0028-466">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="a0028-466">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="a0028-467">ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="a0028-467">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="a0028-468">Použití `IndividualB2C` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="a0028-468">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="a0028-469">ID zásady obnovení hesla pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="a0028-469">The reset password policy ID for this project.</span></span> <span data-ttu-id="a0028-470">Použití `IndividualB2C` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="a0028-470">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="a0028-471">ID zásady úpravy profilu pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="a0028-471">The edit profile policy ID for this project.</span></span> <span data-ttu-id="a0028-472">Použití `IndividualB2C` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="a0028-472">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="a0028-473">Instance služby Azure Active Directory, ke které se chcete připojit.</span><span class="sxs-lookup"><span data-stu-id="a0028-473">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="a0028-474">Použití `SingleOrg` s `MultiOrg` ověřováním nebo ověřování.</span><span class="sxs-lookup"><span data-stu-id="a0028-474">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="a0028-475">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="a0028-475">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="a0028-476">ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="a0028-476">The Client ID for this project.</span></span> <span data-ttu-id="a0028-477">Použití `IndividualB2C`s `SingleOrg`protokolem , nebo `MultiOrg` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="a0028-477">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="a0028-478">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="a0028-478">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="a0028-479">Doména klienta adresáře.</span><span class="sxs-lookup"><span data-stu-id="a0028-479">The domain for the directory tenant.</span></span> <span data-ttu-id="a0028-480">Použití `SingleOrg` s `IndividualB2C` ověřováním nebo ověřování.</span><span class="sxs-lookup"><span data-stu-id="a0028-480">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="a0028-481">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="a0028-481">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="a0028-482">ID ID ID tenantid adresáře, ke kterému se chcete připojit.</span><span class="sxs-lookup"><span data-stu-id="a0028-482">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="a0028-483">Použití `SingleOrg` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="a0028-483">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="a0028-484">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="a0028-484">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="a0028-485">Cesta požadavku v rámci základní cesty aplikace identifikátoru URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="a0028-485">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="a0028-486">Použití `SingleOrg` s `IndividualB2C` ověřováním nebo ověřování.</span><span class="sxs-lookup"><span data-stu-id="a0028-486">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="a0028-487">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="a0028-487">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="a0028-488">Umožňuje této aplikaci přístup pro čtení do adresáře.</span><span class="sxs-lookup"><span data-stu-id="a0028-488">Allows this application read-access to the directory.</span></span> <span data-ttu-id="a0028-489">Platí pouze `SingleOrg` pro `MultiOrg` nebo ověřování.</span><span class="sxs-lookup"><span data-stu-id="a0028-489">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="a0028-490">Nezahrnuje *launchSettings.json* z generované šablony.</span><span class="sxs-lookup"><span data-stu-id="a0028-490">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="a0028-491">Vypne protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a0028-491">Turns off HTTPS.</span></span> <span data-ttu-id="a0028-492">Tato možnost platí `Individual`pouze `IndividualB2C` `SingleOrg`v `MultiOrg` případě, , , , nebo nejsou používány.</span><span class="sxs-lookup"><span data-stu-id="a0028-492">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="a0028-493">Určuje LocalDB by měl být použit místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="a0028-493">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="a0028-494">Platí pouze `Individual` pro `IndividualB2C` nebo ověřování.</span><span class="sxs-lookup"><span data-stu-id="a0028-494">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="a0028-495">Určuje [rámec,](../../standard/frameworks.md) na který má být cílit.</span><span class="sxs-lookup"><span data-stu-id="a0028-495">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="a0028-496">Možnost je k dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="a0028-496">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="a0028-497">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, které používáte:</span><span class="sxs-lookup"><span data-stu-id="a0028-497">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="a0028-498">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="a0028-498">SDK version</span></span> | <span data-ttu-id="a0028-499">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="a0028-499">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="a0028-500">3.1</span><span class="sxs-lookup"><span data-stu-id="a0028-500">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="a0028-501">3.0</span><span class="sxs-lookup"><span data-stu-id="a0028-501">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="a0028-502">Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="a0028-502">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="a0028-503">Zahrnuje BrowserLink v projektu.</span><span class="sxs-lookup"><span data-stu-id="a0028-503">Includes BrowserLink in the project.</span></span> <span data-ttu-id="a0028-504">Možnost není k dispozici v .NET Core 2.2 a 3.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="a0028-504">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="a0028-505">Určuje, zda je projekt nakonfigurován pro použití [kompilace razor runtime](/aspnet/core/mvc/views/view-compilation#runtime-compilation) v sestaveních ladění.</span><span class="sxs-lookup"><span data-stu-id="a0028-505">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="a0028-506">Možnost je k dispozici od .NET Core 3.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="a0028-506">Option available since .NET Core 3.1 SDK.</span></span>

***

### <a name="angular-react"></a><a name="spa"></a><span data-ttu-id="a0028-507">úhlové, reagovat</span><span class="sxs-lookup"><span data-stu-id="a0028-507">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="a0028-508">Typ ověřování, které chcete použít.</span><span class="sxs-lookup"><span data-stu-id="a0028-508">The type of authentication to use.</span></span> <span data-ttu-id="a0028-509">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="a0028-509">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="a0028-510">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="a0028-510">The possible values are:</span></span>

  - <span data-ttu-id="a0028-511">`None`- Žádné ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="a0028-511">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="a0028-512">`Individual`- Individuální autentizace.</span><span class="sxs-lookup"><span data-stu-id="a0028-512">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="a0028-513">Nezahrnuje *launchSettings.json* z generované šablony.</span><span class="sxs-lookup"><span data-stu-id="a0028-513">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="a0028-514">Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="a0028-514">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="a0028-515">Vypne protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a0028-515">Turns off HTTPS.</span></span> <span data-ttu-id="a0028-516">Tato možnost platí pouze `None`v případě, že ověřování je .</span><span class="sxs-lookup"><span data-stu-id="a0028-516">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="a0028-517">Určuje LocalDB by měl být použit místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="a0028-517">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="a0028-518">Platí pouze `Individual` pro `IndividualB2C` nebo ověřování.</span><span class="sxs-lookup"><span data-stu-id="a0028-518">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="a0028-519">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="a0028-519">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="a0028-520">Určuje [rámec,](../../standard/frameworks.md) na který má být cílit.</span><span class="sxs-lookup"><span data-stu-id="a0028-520">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="a0028-521">Možnost není k dispozici v sada .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="a0028-521">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="a0028-522">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, které používáte:</span><span class="sxs-lookup"><span data-stu-id="a0028-522">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="a0028-523">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="a0028-523">SDK version</span></span> | <span data-ttu-id="a0028-524">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="a0028-524">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="a0028-525">3.1</span><span class="sxs-lookup"><span data-stu-id="a0028-525">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="a0028-526">3.0</span><span class="sxs-lookup"><span data-stu-id="a0028-526">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="a0028-527">2.1</span><span class="sxs-lookup"><span data-stu-id="a0028-527">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="a0028-528">reactredux</span><span class="sxs-lookup"><span data-stu-id="a0028-528">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="a0028-529">Nezahrnuje *launchSettings.json* z generované šablony.</span><span class="sxs-lookup"><span data-stu-id="a0028-529">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="a0028-530">Určuje [rámec,](../../standard/frameworks.md) na který má být cílit.</span><span class="sxs-lookup"><span data-stu-id="a0028-530">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="a0028-531">Možnost není k dispozici v sada .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="a0028-531">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="a0028-532">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, které používáte:</span><span class="sxs-lookup"><span data-stu-id="a0028-532">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="a0028-533">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="a0028-533">SDK version</span></span> | <span data-ttu-id="a0028-534">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="a0028-534">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="a0028-535">3.1</span><span class="sxs-lookup"><span data-stu-id="a0028-535">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="a0028-536">3.0</span><span class="sxs-lookup"><span data-stu-id="a0028-536">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="a0028-537">2.1</span><span class="sxs-lookup"><span data-stu-id="a0028-537">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="a0028-538">Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="a0028-538">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="a0028-539">Vypne protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a0028-539">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="a0028-540">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="a0028-540">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="a0028-541">Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="a0028-541">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="a0028-542">Podporuje přidávání tradičních stránek Razor a zobrazení kromě komponent do této knihovny.</span><span class="sxs-lookup"><span data-stu-id="a0028-542">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="a0028-543">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="a0028-543">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="a0028-544">webapi</span><span class="sxs-lookup"><span data-stu-id="a0028-544">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="a0028-545">Typ ověřování, které chcete použít.</span><span class="sxs-lookup"><span data-stu-id="a0028-545">The type of authentication to use.</span></span> <span data-ttu-id="a0028-546">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="a0028-546">The possible values are:</span></span>

  - <span data-ttu-id="a0028-547">`None`- Žádné ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="a0028-547">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="a0028-548">`IndividualB2C`- Individuální ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="a0028-548">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="a0028-549">`SingleOrg`- Organizační ověřování pro jednoho klienta.</span><span class="sxs-lookup"><span data-stu-id="a0028-549">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="a0028-550">`Windows`- Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="a0028-550">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="a0028-551">Instance Azure Active Directory B2C, ke které se chcete připojit.</span><span class="sxs-lookup"><span data-stu-id="a0028-551">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="a0028-552">Použití `IndividualB2C` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="a0028-552">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="a0028-553">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="a0028-553">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="a0028-554">ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="a0028-554">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="a0028-555">Použití `IndividualB2C` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="a0028-555">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="a0028-556">Instance služby Azure Active Directory, ke které se chcete připojit.</span><span class="sxs-lookup"><span data-stu-id="a0028-556">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="a0028-557">Použití `SingleOrg` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="a0028-557">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="a0028-558">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="a0028-558">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="a0028-559">ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="a0028-559">The Client ID for this project.</span></span> <span data-ttu-id="a0028-560">Použití `IndividualB2C` s `SingleOrg` ověřováním nebo ověřování.</span><span class="sxs-lookup"><span data-stu-id="a0028-560">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="a0028-561">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="a0028-561">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="a0028-562">Doména klienta adresáře.</span><span class="sxs-lookup"><span data-stu-id="a0028-562">The domain for the directory tenant.</span></span> <span data-ttu-id="a0028-563">Použití `IndividualB2C` s `SingleOrg` ověřováním nebo ověřování.</span><span class="sxs-lookup"><span data-stu-id="a0028-563">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="a0028-564">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="a0028-564">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="a0028-565">ID ID ID tenantid adresáře, ke kterému se chcete připojit.</span><span class="sxs-lookup"><span data-stu-id="a0028-565">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="a0028-566">Použití `SingleOrg` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="a0028-566">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="a0028-567">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="a0028-567">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="a0028-568">Umožňuje této aplikaci přístup pro čtení do adresáře.</span><span class="sxs-lookup"><span data-stu-id="a0028-568">Allows this application read-access to the directory.</span></span> <span data-ttu-id="a0028-569">Platí pouze `SingleOrg` pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="a0028-569">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="a0028-570">Nezahrnuje *launchSettings.json* z generované šablony.</span><span class="sxs-lookup"><span data-stu-id="a0028-570">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="a0028-571">Vypne protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a0028-571">Turns off HTTPS.</span></span> <span data-ttu-id="a0028-572">`app.UseHsts`a `app.UseHttpsRedirection` nejsou přidány `Startup.Configure`do .</span><span class="sxs-lookup"><span data-stu-id="a0028-572">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="a0028-573">Tato možnost platí `IndividualB2C` pouze `SingleOrg` v případě, že se k ověřování používá nebo nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="a0028-573">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="a0028-574">Určuje LocalDB by měl být použit místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="a0028-574">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="a0028-575">Platí pouze `IndividualB2C` pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="a0028-575">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="a0028-576">Určuje [rámec,](../../standard/frameworks.md) na který má být cílit.</span><span class="sxs-lookup"><span data-stu-id="a0028-576">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="a0028-577">Možnost není k dispozici v sada .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="a0028-577">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="a0028-578">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, které používáte:</span><span class="sxs-lookup"><span data-stu-id="a0028-578">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="a0028-579">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="a0028-579">SDK version</span></span> | <span data-ttu-id="a0028-580">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="a0028-580">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="a0028-581">3.1</span><span class="sxs-lookup"><span data-stu-id="a0028-581">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="a0028-582">3.0</span><span class="sxs-lookup"><span data-stu-id="a0028-582">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="a0028-583">2.1</span><span class="sxs-lookup"><span data-stu-id="a0028-583">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="a0028-584">Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="a0028-584">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="a0028-585">globaljson</span><span class="sxs-lookup"><span data-stu-id="a0028-585">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="a0028-586">Určuje verzi sady .NET Core SDK, která má být používána v souboru *global.json.*</span><span class="sxs-lookup"><span data-stu-id="a0028-586">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="a0028-587">Příklady</span><span class="sxs-lookup"><span data-stu-id="a0028-587">Examples</span></span>

- <span data-ttu-id="a0028-588">Vytvořte projekt aplikace konzoly Jazyka C# zadáním názvu šablony:</span><span class="sxs-lookup"><span data-stu-id="a0028-588">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="a0028-589">Vytvořte projekt aplikace konzoly F# v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="a0028-589">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang F#
  ```

- <span data-ttu-id="a0028-590">Vytvořte projekt knihovny tříd .NET Standard v zadaném adresáři:</span><span class="sxs-lookup"><span data-stu-id="a0028-590">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="a0028-591">Vytvořte nový ASP.NET projektu Core C# MVC v aktuálním adresáři bez ověřování:</span><span class="sxs-lookup"><span data-stu-id="a0028-591">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="a0028-592">Vytvořte nový projekt xUnit:</span><span class="sxs-lookup"><span data-stu-id="a0028-592">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="a0028-593">Seznam všech šablon dostupných pro jednostránkové aplikace (SPA) šablony:</span><span class="sxs-lookup"><span data-stu-id="a0028-593">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="a0028-594">Seznam všech šablon odpovídajících podřetězci *we.*</span><span class="sxs-lookup"><span data-stu-id="a0028-594">List all templates matching the *we* substring.</span></span> <span data-ttu-id="a0028-595">Nebyla nalezena žádná přesná shoda, takže porovnávání podřetězců se spustí proti sloupcům krátkého názvu i názvu.</span><span class="sxs-lookup"><span data-stu-id="a0028-595">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="a0028-596">Pokus o vyvolání šablony odpovídající *ng*.</span><span class="sxs-lookup"><span data-stu-id="a0028-596">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="a0028-597">Pokud nelze určit jednu shodu, uveďte šablony, které se částečně shodují.</span><span class="sxs-lookup"><span data-stu-id="a0028-597">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="a0028-598">Nainstalujte verzi 2.0 šablon SPA pro ASP.NET Core:</span><span class="sxs-lookup"><span data-stu-id="a0028-598">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="a0028-599">Seznam nainstalovaných šablon a podrobnosti o nich, včetně toho, jak je odinstalovat:</span><span class="sxs-lookup"><span data-stu-id="a0028-599">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="a0028-600">Vytvořte *soubor global.json* v aktuálním adresáři, který nastavuje verzi sady SDK na 3.1.101:</span><span class="sxs-lookup"><span data-stu-id="a0028-600">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="a0028-601">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0028-601">See also</span></span>

- [<span data-ttu-id="a0028-602">Vlastní šablony pro dotnet nové</span><span class="sxs-lookup"><span data-stu-id="a0028-602">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="a0028-603">Vytvoření vlastní šablony pro dotnet new</span><span class="sxs-lookup"><span data-stu-id="a0028-603">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="a0028-604">úložiště GitHub u dotnet/dotnet-template-samples GitHub</span><span class="sxs-lookup"><span data-stu-id="a0028-604">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="a0028-605">Dostupné šablony pro dotnet nové</span><span class="sxs-lookup"><span data-stu-id="a0028-605">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
