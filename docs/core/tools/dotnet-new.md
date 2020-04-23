---
title: dotnet nový příkaz
description: Nový příkaz dotnet vytvoří nové projekty .NET Core založené na zadané šabloně.
ms.date: 04/10/2020
ms.openlocfilehash: 1979f98a6005a414acc64c5eaa086a88aca9f033
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102824"
---
# <a name="dotnet-new"></a><span data-ttu-id="4b7ac-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="4b7ac-103">dotnet new</span></span>

<span data-ttu-id="4b7ac-104">**Tento článek se týká:** ✔️ .NET Core 2.0 SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="4b7ac-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="4b7ac-105">Název</span><span class="sxs-lookup"><span data-stu-id="4b7ac-105">Name</span></span>

<span data-ttu-id="4b7ac-106">`dotnet new`- Vytvoří nový projekt, konfigurační soubor nebo řešení založené na zadané šabloně.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="4b7ac-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="4b7ac-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {C#|F#|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="4b7ac-108">Popis</span><span class="sxs-lookup"><span data-stu-id="4b7ac-108">Description</span></span>

<span data-ttu-id="4b7ac-109">Příkaz `dotnet new` vytvoří projekt .NET Core nebo jiné artefakty založené na šabloně.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="4b7ac-110">Příkaz volá [modul šablony](https://github.com/dotnet/templating) k vytvoření artefaktů na disku na základě zadané šablony a možností.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="4b7ac-111">Implicitní obnovení</span><span class="sxs-lookup"><span data-stu-id="4b7ac-111">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="4b7ac-112">Argumenty</span><span class="sxs-lookup"><span data-stu-id="4b7ac-112">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="4b7ac-113">Šablona k vytvoření instance při vyvolání příkazu.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="4b7ac-114">Každá šablona může mít konkrétní možnosti, které můžete předat.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="4b7ac-115">Další informace naleznete v [tématu Možnosti šablony](#template-options).</span><span class="sxs-lookup"><span data-stu-id="4b7ac-115">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="4b7ac-116">Seznam všech `dotnet new --list` nainstalovaných šablon můžete spustit.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-116">You can run `dotnet new --list` to see a list of all installed templates.</span></span> <span data-ttu-id="4b7ac-117">Pokud `TEMPLATE` hodnota není přesná shoda na text ve **sloupci Šablony** nebo **krátký název** z vrácené tabulky, podřetězec shoda se provádí na tyto dva sloupce.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-117">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="4b7ac-118">Počínaje sadou .NET Core 3.0 SDK hledá rozhraní příkazového příkazu šablony v NuGet.org při vyvolání příkazu `dotnet new` za následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="4b7ac-118">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="4b7ac-119">Pokud clI nemůže najít šablonu zápas při `dotnet new`vyvolání , ani částečné.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-119">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="4b7ac-120">Pokud je k dispozici novější verze šablony.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-120">If there's a newer version of the template available.</span></span> <span data-ttu-id="4b7ac-121">V tomto případě je vytvořen projekt nebo artefakt, ale CLI vás upozorní na aktualizovanou verzi šablony.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-121">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="4b7ac-122">Příkaz obsahuje výchozí seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-122">The command contains a default list of templates.</span></span> <span data-ttu-id="4b7ac-123">Slouží `dotnet new -l` k získání seznamu dostupných šablon.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-123">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="4b7ac-124">V následující tabulce jsou uvedeny šablony, které jsou předinstalovány se sadou .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-124">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="4b7ac-125">Výchozí jazyk šablony je zobrazen uvnitř závorek.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-125">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="4b7ac-126">Kliknutím na odkaz krátký název zobrazíte konkrétní možnosti šablony.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-126">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="4b7ac-127">Šablony</span><span class="sxs-lookup"><span data-stu-id="4b7ac-127">Templates</span></span>                                    | <span data-ttu-id="4b7ac-128">Krátký název</span><span class="sxs-lookup"><span data-stu-id="4b7ac-128">Short name</span></span>                      | <span data-ttu-id="4b7ac-129">Jazyk</span><span class="sxs-lookup"><span data-stu-id="4b7ac-129">Language</span></span>     | <span data-ttu-id="4b7ac-130">Značky</span><span class="sxs-lookup"><span data-stu-id="4b7ac-130">Tags</span></span>                                  | <span data-ttu-id="4b7ac-131">Zavedena</span><span class="sxs-lookup"><span data-stu-id="4b7ac-131">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="4b7ac-132">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="4b7ac-132">Console Application</span></span>                          | [<span data-ttu-id="4b7ac-133">Konzoly</span><span class="sxs-lookup"><span data-stu-id="4b7ac-133">console</span></span>](#console)             | <span data-ttu-id="4b7ac-134">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="4b7ac-134">[C#], F#, VB</span></span> | <span data-ttu-id="4b7ac-135">Běžné/konzolové</span><span class="sxs-lookup"><span data-stu-id="4b7ac-135">Common/Console</span></span>                        | <span data-ttu-id="4b7ac-136">1.0</span><span class="sxs-lookup"><span data-stu-id="4b7ac-136">1.0</span></span>        |
| <span data-ttu-id="4b7ac-137">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="4b7ac-137">Class library</span></span>                                | [<span data-ttu-id="4b7ac-138">classlib</span><span class="sxs-lookup"><span data-stu-id="4b7ac-138">classlib</span></span>](#classlib)           | <span data-ttu-id="4b7ac-139">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="4b7ac-139">[C#], F#, VB</span></span> | <span data-ttu-id="4b7ac-140">Společné/Knihovna</span><span class="sxs-lookup"><span data-stu-id="4b7ac-140">Common/Library</span></span>                        | <span data-ttu-id="4b7ac-141">1.0</span><span class="sxs-lookup"><span data-stu-id="4b7ac-141">1.0</span></span>        |
| <span data-ttu-id="4b7ac-142">Aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="4b7ac-142">WPF Application</span></span>                              | [<span data-ttu-id="4b7ac-143">Wpf</span><span class="sxs-lookup"><span data-stu-id="4b7ac-143">wpf</span></span>](#wpf)                     | <span data-ttu-id="4b7ac-144">[C#]</span><span class="sxs-lookup"><span data-stu-id="4b7ac-144">[C#]</span></span>         | <span data-ttu-id="4b7ac-145">Časté/WPF</span><span class="sxs-lookup"><span data-stu-id="4b7ac-145">Common/WPF</span></span>                            | <span data-ttu-id="4b7ac-146">3.0</span><span class="sxs-lookup"><span data-stu-id="4b7ac-146">3.0</span></span>        |
| <span data-ttu-id="4b7ac-147">Knihovna tříd WPF</span><span class="sxs-lookup"><span data-stu-id="4b7ac-147">WPF Class library</span></span>                            | [<span data-ttu-id="4b7ac-148">wpflib</span><span class="sxs-lookup"><span data-stu-id="4b7ac-148">wpflib</span></span>](#wpf)                  | <span data-ttu-id="4b7ac-149">[C#]</span><span class="sxs-lookup"><span data-stu-id="4b7ac-149">[C#]</span></span>         | <span data-ttu-id="4b7ac-150">Časté/WPF</span><span class="sxs-lookup"><span data-stu-id="4b7ac-150">Common/WPF</span></span>                            | <span data-ttu-id="4b7ac-151">3.0</span><span class="sxs-lookup"><span data-stu-id="4b7ac-151">3.0</span></span>        |
| <span data-ttu-id="4b7ac-152">Knihovna vlastních ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="4b7ac-152">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="4b7ac-153">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="4b7ac-153">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="4b7ac-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="4b7ac-154">[C#]</span></span>         | <span data-ttu-id="4b7ac-155">Časté/WPF</span><span class="sxs-lookup"><span data-stu-id="4b7ac-155">Common/WPF</span></span>                            | <span data-ttu-id="4b7ac-156">3.0</span><span class="sxs-lookup"><span data-stu-id="4b7ac-156">3.0</span></span>        |
| <span data-ttu-id="4b7ac-157">Knihovna uživatelských ovládacích prveků WPF</span><span class="sxs-lookup"><span data-stu-id="4b7ac-157">WPF User Control Library</span></span>                     | [<span data-ttu-id="4b7ac-158">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="4b7ac-158">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="4b7ac-159">[C#]</span><span class="sxs-lookup"><span data-stu-id="4b7ac-159">[C#]</span></span>         | <span data-ttu-id="4b7ac-160">Časté/WPF</span><span class="sxs-lookup"><span data-stu-id="4b7ac-160">Common/WPF</span></span>                            | <span data-ttu-id="4b7ac-161">3.0</span><span class="sxs-lookup"><span data-stu-id="4b7ac-161">3.0</span></span>        |
| <span data-ttu-id="4b7ac-162">Aplikace Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="4b7ac-162">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="4b7ac-163">Winforms</span><span class="sxs-lookup"><span data-stu-id="4b7ac-163">winforms</span></span>](#winforms)           | <span data-ttu-id="4b7ac-164">[C#]</span><span class="sxs-lookup"><span data-stu-id="4b7ac-164">[C#]</span></span>         | <span data-ttu-id="4b7ac-165">Běžné/WinForms</span><span class="sxs-lookup"><span data-stu-id="4b7ac-165">Common/WinForms</span></span>                       | <span data-ttu-id="4b7ac-166">3.0</span><span class="sxs-lookup"><span data-stu-id="4b7ac-166">3.0</span></span>        |
| <span data-ttu-id="4b7ac-167">Knihovna tříd Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="4b7ac-167">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="4b7ac-168">winformslib</span><span class="sxs-lookup"><span data-stu-id="4b7ac-168">winformslib</span></span>](#winforms)        | <span data-ttu-id="4b7ac-169">[C#]</span><span class="sxs-lookup"><span data-stu-id="4b7ac-169">[C#]</span></span>         | <span data-ttu-id="4b7ac-170">Běžné/WinForms</span><span class="sxs-lookup"><span data-stu-id="4b7ac-170">Common/WinForms</span></span>                       | <span data-ttu-id="4b7ac-171">3.0</span><span class="sxs-lookup"><span data-stu-id="4b7ac-171">3.0</span></span>        |
| <span data-ttu-id="4b7ac-172">Pracovní služba</span><span class="sxs-lookup"><span data-stu-id="4b7ac-172">Worker Service</span></span>                               | [<span data-ttu-id="4b7ac-173">Pracovník</span><span class="sxs-lookup"><span data-stu-id="4b7ac-173">worker</span></span>](#web-others)           | <span data-ttu-id="4b7ac-174">[C#]</span><span class="sxs-lookup"><span data-stu-id="4b7ac-174">[C#]</span></span>         | <span data-ttu-id="4b7ac-175">Běžné/Pracovník/Web</span><span class="sxs-lookup"><span data-stu-id="4b7ac-175">Common/Worker/Web</span></span>                     | <span data-ttu-id="4b7ac-176">3.0</span><span class="sxs-lookup"><span data-stu-id="4b7ac-176">3.0</span></span>        |
| <span data-ttu-id="4b7ac-177">Projekt testování částí</span><span class="sxs-lookup"><span data-stu-id="4b7ac-177">Unit Test Project</span></span>                            | [<span data-ttu-id="4b7ac-178">mstest</span><span class="sxs-lookup"><span data-stu-id="4b7ac-178">mstest</span></span>](#test)                 | <span data-ttu-id="4b7ac-179">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="4b7ac-179">[C#], F#, VB</span></span> | <span data-ttu-id="4b7ac-180">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="4b7ac-180">Test/MSTest</span></span>                           | <span data-ttu-id="4b7ac-181">1.0</span><span class="sxs-lookup"><span data-stu-id="4b7ac-181">1.0</span></span>        |
| <span data-ttu-id="4b7ac-182">Testovací projekt NUnit 3</span><span class="sxs-lookup"><span data-stu-id="4b7ac-182">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="4b7ac-183">nunit</span><span class="sxs-lookup"><span data-stu-id="4b7ac-183">nunit</span></span>](#nunit)                  | <span data-ttu-id="4b7ac-184">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="4b7ac-184">[C#], F#, VB</span></span> | <span data-ttu-id="4b7ac-185">Testovací/NUnit</span><span class="sxs-lookup"><span data-stu-id="4b7ac-185">Test/NUnit</span></span>                            | <span data-ttu-id="4b7ac-186">2.1.400</span><span class="sxs-lookup"><span data-stu-id="4b7ac-186">2.1.400</span></span>    |
| <span data-ttu-id="4b7ac-187">Testovací položka NUnit 3</span><span class="sxs-lookup"><span data-stu-id="4b7ac-187">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="4b7ac-188">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="4b7ac-188">[C#], F#, VB</span></span> | <span data-ttu-id="4b7ac-189">Testovací/NUnit</span><span class="sxs-lookup"><span data-stu-id="4b7ac-189">Test/NUnit</span></span>                            | <span data-ttu-id="4b7ac-190">2,2</span><span class="sxs-lookup"><span data-stu-id="4b7ac-190">2.2</span></span>        |
| <span data-ttu-id="4b7ac-191">XUnit testovací projekt</span><span class="sxs-lookup"><span data-stu-id="4b7ac-191">xUnit Test Project</span></span>                           | [<span data-ttu-id="4b7ac-192">jednotka x</span><span class="sxs-lookup"><span data-stu-id="4b7ac-192">xunit</span></span>](#test)                  | <span data-ttu-id="4b7ac-193">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="4b7ac-193">[C#], F#, VB</span></span> | <span data-ttu-id="4b7ac-194">Testovací/xJednotka</span><span class="sxs-lookup"><span data-stu-id="4b7ac-194">Test/xUnit</span></span>                            | <span data-ttu-id="4b7ac-195">1.0</span><span class="sxs-lookup"><span data-stu-id="4b7ac-195">1.0</span></span>        |
| <span data-ttu-id="4b7ac-196">Komponenta razor</span><span class="sxs-lookup"><span data-stu-id="4b7ac-196">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="4b7ac-197">[C#]</span><span class="sxs-lookup"><span data-stu-id="4b7ac-197">[C#]</span></span>         | <span data-ttu-id="4b7ac-198">Web/Technologie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4b7ac-198">Web/ASP.NET</span></span>                           | <span data-ttu-id="4b7ac-199">3.0</span><span class="sxs-lookup"><span data-stu-id="4b7ac-199">3.0</span></span>        |
| <span data-ttu-id="4b7ac-200">Holicí strojek stránka</span><span class="sxs-lookup"><span data-stu-id="4b7ac-200">Razor Page</span></span>                                   | [<span data-ttu-id="4b7ac-201">Stránka</span><span class="sxs-lookup"><span data-stu-id="4b7ac-201">page</span></span>](#page)                   | <span data-ttu-id="4b7ac-202">[C#]</span><span class="sxs-lookup"><span data-stu-id="4b7ac-202">[C#]</span></span>         | <span data-ttu-id="4b7ac-203">Web/Technologie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4b7ac-203">Web/ASP.NET</span></span>                           | <span data-ttu-id="4b7ac-204">2.0</span><span class="sxs-lookup"><span data-stu-id="4b7ac-204">2.0</span></span>        |
| <span data-ttu-id="4b7ac-205">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="4b7ac-205">MVC ViewImports</span></span>                              | [<span data-ttu-id="4b7ac-206">viewimports</span><span class="sxs-lookup"><span data-stu-id="4b7ac-206">viewimports</span></span>](#namespace)       | <span data-ttu-id="4b7ac-207">[C#]</span><span class="sxs-lookup"><span data-stu-id="4b7ac-207">[C#]</span></span>         | <span data-ttu-id="4b7ac-208">Web/Technologie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4b7ac-208">Web/ASP.NET</span></span>                           | <span data-ttu-id="4b7ac-209">2.0</span><span class="sxs-lookup"><span data-stu-id="4b7ac-209">2.0</span></span>        |
| <span data-ttu-id="4b7ac-210">Spuštění zobrazení MVC</span><span class="sxs-lookup"><span data-stu-id="4b7ac-210">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="4b7ac-211">[C#]</span><span class="sxs-lookup"><span data-stu-id="4b7ac-211">[C#]</span></span>         | <span data-ttu-id="4b7ac-212">Web/Technologie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4b7ac-212">Web/ASP.NET</span></span>                           | <span data-ttu-id="4b7ac-213">2.0</span><span class="sxs-lookup"><span data-stu-id="4b7ac-213">2.0</span></span>        |
| <span data-ttu-id="4b7ac-214">Aplikace Blazor Server</span><span class="sxs-lookup"><span data-stu-id="4b7ac-214">Blazor Server App</span></span>                            | [<span data-ttu-id="4b7ac-215">blazorserver</span><span class="sxs-lookup"><span data-stu-id="4b7ac-215">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="4b7ac-216">[C#]</span><span class="sxs-lookup"><span data-stu-id="4b7ac-216">[C#]</span></span>         | <span data-ttu-id="4b7ac-217">Web/Blazor</span><span class="sxs-lookup"><span data-stu-id="4b7ac-217">Web/Blazor</span></span>                            | <span data-ttu-id="4b7ac-218">3.0</span><span class="sxs-lookup"><span data-stu-id="4b7ac-218">3.0</span></span>        |
| <span data-ttu-id="4b7ac-219">ASP.NET jádro prázdné</span><span class="sxs-lookup"><span data-stu-id="4b7ac-219">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="4b7ac-220">Webové</span><span class="sxs-lookup"><span data-stu-id="4b7ac-220">web</span></span>](#web)                     | <span data-ttu-id="4b7ac-221">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="4b7ac-221">[C#], F#</span></span>     | <span data-ttu-id="4b7ac-222">Web/Prázdný</span><span class="sxs-lookup"><span data-stu-id="4b7ac-222">Web/Empty</span></span>                             | <span data-ttu-id="4b7ac-223">1.0</span><span class="sxs-lookup"><span data-stu-id="4b7ac-223">1.0</span></span>        |
| <span data-ttu-id="4b7ac-224">ASP.NET základní webová aplikace (model-view-controller)</span><span class="sxs-lookup"><span data-stu-id="4b7ac-224">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="4b7ac-225">Mvc</span><span class="sxs-lookup"><span data-stu-id="4b7ac-225">mvc</span></span>](#web-options)             | <span data-ttu-id="4b7ac-226">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="4b7ac-226">[C#], F#</span></span>     | <span data-ttu-id="4b7ac-227">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="4b7ac-227">Web/MVC</span></span>                               | <span data-ttu-id="4b7ac-228">1.0</span><span class="sxs-lookup"><span data-stu-id="4b7ac-228">1.0</span></span>        |
| <span data-ttu-id="4b7ac-229">ASP.NET základní webová aplikace</span><span class="sxs-lookup"><span data-stu-id="4b7ac-229">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="4b7ac-230">webapp, holicí strojek</span><span class="sxs-lookup"><span data-stu-id="4b7ac-230">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="4b7ac-231">[C#]</span><span class="sxs-lookup"><span data-stu-id="4b7ac-231">[C#]</span></span>         | <span data-ttu-id="4b7ac-232">Webové/MVC/Razor stránky</span><span class="sxs-lookup"><span data-stu-id="4b7ac-232">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="4b7ac-233">2.2, 2.0</span><span class="sxs-lookup"><span data-stu-id="4b7ac-233">2.2, 2.0</span></span>   |
| <span data-ttu-id="4b7ac-234">ASP.NET jádro s úhlovým</span><span class="sxs-lookup"><span data-stu-id="4b7ac-234">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="4b7ac-235">Úhlové</span><span class="sxs-lookup"><span data-stu-id="4b7ac-235">angular</span></span>](#spa)                 | <span data-ttu-id="4b7ac-236">[C#]</span><span class="sxs-lookup"><span data-stu-id="4b7ac-236">[C#]</span></span>         | <span data-ttu-id="4b7ac-237">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="4b7ac-237">Web/MVC/SPA</span></span>                           | <span data-ttu-id="4b7ac-238">2.0</span><span class="sxs-lookup"><span data-stu-id="4b7ac-238">2.0</span></span>        |
| <span data-ttu-id="4b7ac-239">ASP.NET jádro s React.js</span><span class="sxs-lookup"><span data-stu-id="4b7ac-239">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="4b7ac-240">Reagovat</span><span class="sxs-lookup"><span data-stu-id="4b7ac-240">react</span></span>](#spa)                   | <span data-ttu-id="4b7ac-241">[C#]</span><span class="sxs-lookup"><span data-stu-id="4b7ac-241">[C#]</span></span>         | <span data-ttu-id="4b7ac-242">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="4b7ac-242">Web/MVC/SPA</span></span>                           | <span data-ttu-id="4b7ac-243">2.0</span><span class="sxs-lookup"><span data-stu-id="4b7ac-243">2.0</span></span>        |
| <span data-ttu-id="4b7ac-244">ASP.NET jádro s React.js a Redux</span><span class="sxs-lookup"><span data-stu-id="4b7ac-244">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="4b7ac-245">reactredux</span><span class="sxs-lookup"><span data-stu-id="4b7ac-245">reactredux</span></span>](#reactredux)       | <span data-ttu-id="4b7ac-246">[C#]</span><span class="sxs-lookup"><span data-stu-id="4b7ac-246">[C#]</span></span>         | <span data-ttu-id="4b7ac-247">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="4b7ac-247">Web/MVC/SPA</span></span>                           | <span data-ttu-id="4b7ac-248">2.0</span><span class="sxs-lookup"><span data-stu-id="4b7ac-248">2.0</span></span>        |
| <span data-ttu-id="4b7ac-249">Knihovna třídy Holicí strojek</span><span class="sxs-lookup"><span data-stu-id="4b7ac-249">Razor Class Library</span></span>                          | [<span data-ttu-id="4b7ac-250">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="4b7ac-250">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="4b7ac-251">[C#]</span><span class="sxs-lookup"><span data-stu-id="4b7ac-251">[C#]</span></span>         | <span data-ttu-id="4b7ac-252">Web/Břitva/knihovna/knihovna</span><span class="sxs-lookup"><span data-stu-id="4b7ac-252">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="4b7ac-253">2.1</span><span class="sxs-lookup"><span data-stu-id="4b7ac-253">2.1</span></span>        |
| <span data-ttu-id="4b7ac-254">Webové rozhraní API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4b7ac-254">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="4b7ac-255">webapi</span><span class="sxs-lookup"><span data-stu-id="4b7ac-255">webapi</span></span>](#webapi)               | <span data-ttu-id="4b7ac-256">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="4b7ac-256">[C#], F#</span></span>     | <span data-ttu-id="4b7ac-257">Webové rozhraní API</span><span class="sxs-lookup"><span data-stu-id="4b7ac-257">Web/WebAPI</span></span>                            | <span data-ttu-id="4b7ac-258">1.0</span><span class="sxs-lookup"><span data-stu-id="4b7ac-258">1.0</span></span>        |
| <span data-ttu-id="4b7ac-259">ASP.NET Core gRPC Service</span><span class="sxs-lookup"><span data-stu-id="4b7ac-259">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="4b7ac-260">grpc</span><span class="sxs-lookup"><span data-stu-id="4b7ac-260">grpc</span></span>](#web-others)             | <span data-ttu-id="4b7ac-261">[C#]</span><span class="sxs-lookup"><span data-stu-id="4b7ac-261">[C#]</span></span>         | <span data-ttu-id="4b7ac-262">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="4b7ac-262">Web/gRPC</span></span>                              | <span data-ttu-id="4b7ac-263">3.0</span><span class="sxs-lookup"><span data-stu-id="4b7ac-263">3.0</span></span>        |
| <span data-ttu-id="4b7ac-264">Soubor vyrovnávací paměti protokolu</span><span class="sxs-lookup"><span data-stu-id="4b7ac-264">Protocol Buffer File</span></span>                         | [<span data-ttu-id="4b7ac-265">proto</span><span class="sxs-lookup"><span data-stu-id="4b7ac-265">proto</span></span>](#namespace)             |              | <span data-ttu-id="4b7ac-266">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="4b7ac-266">Web/gRPC</span></span>                              | <span data-ttu-id="4b7ac-267">3.0</span><span class="sxs-lookup"><span data-stu-id="4b7ac-267">3.0</span></span>        |
| <span data-ttu-id="4b7ac-268">dotnet gitignore soubor</span><span class="sxs-lookup"><span data-stu-id="4b7ac-268">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="4b7ac-269">Config</span><span class="sxs-lookup"><span data-stu-id="4b7ac-269">Config</span></span>                                | <span data-ttu-id="4b7ac-270">3.0</span><span class="sxs-lookup"><span data-stu-id="4b7ac-270">3.0</span></span>        |
| <span data-ttu-id="4b7ac-271">soubor global.json</span><span class="sxs-lookup"><span data-stu-id="4b7ac-271">global.json file</span></span>                             | [<span data-ttu-id="4b7ac-272">globaljson</span><span class="sxs-lookup"><span data-stu-id="4b7ac-272">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="4b7ac-273">Config</span><span class="sxs-lookup"><span data-stu-id="4b7ac-273">Config</span></span>                                | <span data-ttu-id="4b7ac-274">2.0</span><span class="sxs-lookup"><span data-stu-id="4b7ac-274">2.0</span></span>        |
| <span data-ttu-id="4b7ac-275">Konfigurace nugetu</span><span class="sxs-lookup"><span data-stu-id="4b7ac-275">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="4b7ac-276">Config</span><span class="sxs-lookup"><span data-stu-id="4b7ac-276">Config</span></span>                                | <span data-ttu-id="4b7ac-277">1.0</span><span class="sxs-lookup"><span data-stu-id="4b7ac-277">1.0</span></span>        |
| <span data-ttu-id="4b7ac-278">Dotnet místní nástroj manifest soubor</span><span class="sxs-lookup"><span data-stu-id="4b7ac-278">dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="4b7ac-279">Config</span><span class="sxs-lookup"><span data-stu-id="4b7ac-279">Config</span></span>                                | <span data-ttu-id="4b7ac-280">3.0</span><span class="sxs-lookup"><span data-stu-id="4b7ac-280">3.0</span></span>        |
| <span data-ttu-id="4b7ac-281">Konfigurace webu</span><span class="sxs-lookup"><span data-stu-id="4b7ac-281">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="4b7ac-282">Config</span><span class="sxs-lookup"><span data-stu-id="4b7ac-282">Config</span></span>                                | <span data-ttu-id="4b7ac-283">1.0</span><span class="sxs-lookup"><span data-stu-id="4b7ac-283">1.0</span></span>        |
| <span data-ttu-id="4b7ac-284">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="4b7ac-284">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="4b7ac-285">Řešení</span><span class="sxs-lookup"><span data-stu-id="4b7ac-285">Solution</span></span>                              | <span data-ttu-id="4b7ac-286">1.0</span><span class="sxs-lookup"><span data-stu-id="4b7ac-286">1.0</span></span>        |

## <a name="options"></a><span data-ttu-id="4b7ac-287">Možnosti</span><span class="sxs-lookup"><span data-stu-id="4b7ac-287">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="4b7ac-288">Zobrazí souhrn toho, co by se stalo, kdyby byl daný příkaz spuštěn.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-288">Displays a summary of what would happen if the given command were run.</span></span> <span data-ttu-id="4b7ac-289">K dispozici od .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-289">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="4b7ac-290">Vynutí vygenerování obsahu, i když by změnil existující soubory.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-290">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="4b7ac-291">To je nutné, pokud vybraná šablona přepíše existující soubory ve výstupním adresáři.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-291">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="4b7ac-292">Vytiskne nápovědu pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-292">Prints out help for the command.</span></span> <span data-ttu-id="4b7ac-293">Může být vyvolána `dotnet new` pro samotný příkaz nebo pro libovolnou šablonu.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-293">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="4b7ac-294">Například, `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-294">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="4b7ac-295">Nainstaluje sadu šablon `PATH` z `NUGET_ID` nebo poskytované.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-295">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="4b7ac-296">Chcete-li nainstalovat předběžnou verzi balíčku šablony, je třeba zadat verzi `<package-name>::<package-version>`ve formátu .</span><span class="sxs-lookup"><span data-stu-id="4b7ac-296">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="4b7ac-297">Ve výchozím `dotnet new` \* nastavení přechází pro verzi, která představuje nejnovější stabilní verzi balíčku.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-297">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="4b7ac-298">Viz příklad v části [Příklady.](#examples)</span><span class="sxs-lookup"><span data-stu-id="4b7ac-298">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="4b7ac-299">Pokud byla verze šablony již nainstalována při spuštění tohoto příkazu, bude šablona aktualizována na zadanou verzi nebo na nejnovější stabilní verzi, pokud nebyla zadána žádná verze.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-299">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="4b7ac-300">Informace o vytváření vlastních šablon naleznete v [tématu Vlastní šablony pro dotnet new](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="4b7ac-300">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="4b7ac-301">Zobrazí seznam šablon obsahujících zadaný název.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-301">Lists templates containing the specified name.</span></span> <span data-ttu-id="4b7ac-302">Pokud není zadán žádný název, zobrazí seznam všech šablon.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-302">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="4b7ac-303">Jazyk šablony, kterou chcete vytvořit.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-303">The language of the template to create.</span></span> <span data-ttu-id="4b7ac-304">Přijatý jazyk se liší podle šablony (viz výchozí hodnoty v části [argumenty).](#arguments)</span><span class="sxs-lookup"><span data-stu-id="4b7ac-304">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="4b7ac-305">Neplatí pro některé šablony.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-305">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="4b7ac-306">Některé skořepiny interpretují `#` jako speciální znak.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-306">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="4b7ac-307">V těchto případech uzavřete hodnotu parametru jazyka do uvozovek.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-307">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="4b7ac-308">Například, `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-308">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="4b7ac-309">Název vytvořeného výstupu.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-309">The name for the created output.</span></span> <span data-ttu-id="4b7ac-310">Pokud není zadán žádný název, bude použit název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-310">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="4b7ac-311">Určuje zdroj NuGet, který se má použít během instalace.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-311">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="4b7ac-312">K dispozici od .NET Core 2.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-312">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="4b7ac-313">Umístění pro umístění generovaného výstupu.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-313">Location to place the generated output.</span></span> <span data-ttu-id="4b7ac-314">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-314">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="4b7ac-315">Filtruje šablony založené na dostupných typech.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-315">Filters templates based on available types.</span></span> <span data-ttu-id="4b7ac-316">Předdefinované hodnoty `project` `item`jsou `other`, , nebo .</span><span class="sxs-lookup"><span data-stu-id="4b7ac-316">Predefined values are `project`, `item`, or `other`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="4b7ac-317">Odinstaluje sadu `PATH` šablon `NUGET_ID` v aplikaci nebo v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-317">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="4b7ac-318">Pokud `<PATH|NUGET_ID>` není zadána hodnota, zobrazí se všechny aktuálně nainstalované balíčky šablon a jejich přidružené šablony.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-318">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="4b7ac-319">Při zadávání `NUGET_ID`aplikace neuvádějte číslo verze.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-319">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="4b7ac-320">Pokud nezadáte parametr této možnosti, příkaz zobrazí seznam nainstalovaných šablon a podrobnosti o nich.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-320">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="4b7ac-321">Chcete-li odinstalovat `PATH`šablonu pomocí aplikace , je třeba cestu plně kvalifikovat.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-321">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="4b7ac-322">Například *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z obsahující složky nebude.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-322">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="4b7ac-323">Nezahrnujte konečné ukončující lomítko adresáře na cestě šablony.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-323">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="4b7ac-324">Zkontroluje, zda jsou k dispozici aktualizace pro aktuálně nainstalované balíčky šablon, a nainstaluje je.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-324">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="4b7ac-325">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-325">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="4b7ac-326">Zkontroluje, zda jsou k dispozici aktualizace pro aktuálně nainstalované balíčky šablon.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-326">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="4b7ac-327">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-327">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="4b7ac-328">Možnosti šablon</span><span class="sxs-lookup"><span data-stu-id="4b7ac-328">Template options</span></span>

<span data-ttu-id="4b7ac-329">Každá šablona projektu může mít k dispozici další možnosti.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-329">Each project template may have additional options available.</span></span> <span data-ttu-id="4b7ac-330">Základní šablony mají následující další možnosti:</span><span class="sxs-lookup"><span data-stu-id="4b7ac-330">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="4b7ac-331">konzola</span><span class="sxs-lookup"><span data-stu-id="4b7ac-331">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="4b7ac-332">Určuje [rámec,](../../standard/frameworks.md) na který má být cílit.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-332">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="4b7ac-333">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-333">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="4b7ac-334">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, které používáte:</span><span class="sxs-lookup"><span data-stu-id="4b7ac-334">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="4b7ac-335">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="4b7ac-335">SDK version</span></span> | <span data-ttu-id="4b7ac-336">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="4b7ac-336">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="4b7ac-337">3.1</span><span class="sxs-lookup"><span data-stu-id="4b7ac-337">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="4b7ac-338">3.0</span><span class="sxs-lookup"><span data-stu-id="4b7ac-338">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="4b7ac-339">Nastaví `LangVersion` vlastnost v vytvořeném souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-339">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="4b7ac-340">Například použijte `--langVersion 7.3` použít C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-340">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="4b7ac-341">Není podporováno pro F#.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-341">Not supported for F#.</span></span> <span data-ttu-id="4b7ac-342">K dispozici od .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-342">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="4b7ac-343">Seznam výchozích verzí jazyka C# naleznete [v tématu Výchozí verze](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="4b7ac-343">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="4b7ac-344">Pokud je zadán, neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-344">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="4b7ac-345">K dispozici od .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-345">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="4b7ac-346">classlib</span><span class="sxs-lookup"><span data-stu-id="4b7ac-346">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="4b7ac-347">Určuje [rámec,](../../standard/frameworks.md) na který má být cílit.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-347">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="4b7ac-348">Hodnoty: `netcoreapp<version>` chcete-li vytvořit knihovnu `netstandard<version>` tříd .NET Core nebo vytvořit knihovnu standardních tříd .NET.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-348">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="4b7ac-349">Výchozí hodnota je `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-349">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="4b7ac-350">Nastaví `LangVersion` vlastnost v vytvořeném souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-350">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="4b7ac-351">Například použijte `--langVersion 7.3` použít C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-351">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="4b7ac-352">Není podporováno pro F#.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-352">Not supported for F#.</span></span> <span data-ttu-id="4b7ac-353">K dispozici od .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-353">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="4b7ac-354">Seznam výchozích verzí jazyka C# naleznete [v tématu Výchozí verze](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="4b7ac-354">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="4b7ac-355">Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-355">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a><span data-ttu-id="4b7ac-356">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="4b7ac-356">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="4b7ac-357">Určuje [rámec,](../../standard/frameworks.md) na který má být cílit.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-357">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="4b7ac-358">Výchozí hodnota je `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-358">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="4b7ac-359">K dispozici od .NET Core 3.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-359">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="4b7ac-360">Nastaví `LangVersion` vlastnost v vytvořeném souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-360">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="4b7ac-361">Například použijte `--langVersion 7.3` použít C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-361">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="4b7ac-362">Seznam výchozích verzí jazyka C# naleznete [v tématu Výchozí verze](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="4b7ac-362">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="4b7ac-363">Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-363">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms-winformslib"></a><a name="winforms"></a><span data-ttu-id="4b7ac-364">winforms, winformslib</span><span class="sxs-lookup"><span data-stu-id="4b7ac-364">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="4b7ac-365">Nastaví `LangVersion` vlastnost v vytvořeném souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-365">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="4b7ac-366">Například použijte `--langVersion 7.3` použít C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-366">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="4b7ac-367">Seznam výchozích verzí jazyka C# naleznete [v tématu Výchozí verze](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="4b7ac-367">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="4b7ac-368">Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-368">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="worker-grpc"></a><a name="web-others"></a><span data-ttu-id="4b7ac-369">pracovník, grpc</span><span class="sxs-lookup"><span data-stu-id="4b7ac-369">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="4b7ac-370">Určuje [rámec,](../../standard/frameworks.md) na který má být cílit.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-370">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="4b7ac-371">Výchozí hodnota je `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-371">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="4b7ac-372">K dispozici od .NET Core 3.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-372">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="4b7ac-373">Nezahrnuje *launchSettings.json* z generované šablony.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-373">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="4b7ac-374">Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-374">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="mstest-xunit"></a><a name="test"></a><span data-ttu-id="4b7ac-375">mstest, xunit</span><span class="sxs-lookup"><span data-stu-id="4b7ac-375">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="4b7ac-376">Určuje [rámec,](../../standard/frameworks.md) na který má být cílit.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-376">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="4b7ac-377">Možnost je k dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-377">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="4b7ac-378">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, které používáte:</span><span class="sxs-lookup"><span data-stu-id="4b7ac-378">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="4b7ac-379">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="4b7ac-379">SDK version</span></span> | <span data-ttu-id="4b7ac-380">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="4b7ac-380">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="4b7ac-381">3.1</span><span class="sxs-lookup"><span data-stu-id="4b7ac-381">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="4b7ac-382">3.0</span><span class="sxs-lookup"><span data-stu-id="4b7ac-382">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="4b7ac-383">Umožňuje balení pro projekt pomocí [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="4b7ac-383">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="4b7ac-384">Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-384">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="4b7ac-385">nunit</span><span class="sxs-lookup"><span data-stu-id="4b7ac-385">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="4b7ac-386">Určuje [rámec,](../../standard/frameworks.md) na který má být cílit.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-386">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="4b7ac-387">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, které používáte:</span><span class="sxs-lookup"><span data-stu-id="4b7ac-387">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="4b7ac-388">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="4b7ac-388">SDK version</span></span> | <span data-ttu-id="4b7ac-389">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="4b7ac-389">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="4b7ac-390">3.1</span><span class="sxs-lookup"><span data-stu-id="4b7ac-390">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="4b7ac-391">3.0</span><span class="sxs-lookup"><span data-stu-id="4b7ac-391">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="4b7ac-392">2,2</span><span class="sxs-lookup"><span data-stu-id="4b7ac-392">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="4b7ac-393">2.1</span><span class="sxs-lookup"><span data-stu-id="4b7ac-393">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="4b7ac-394">Umožňuje balení pro projekt pomocí [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="4b7ac-394">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="4b7ac-395">Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-395">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="4b7ac-396">Stránka</span><span class="sxs-lookup"><span data-stu-id="4b7ac-396">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="4b7ac-397">Obor názvů pro generovaný kód.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-397">Namespace for the generated code.</span></span> <span data-ttu-id="4b7ac-398">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-398">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="4b7ac-399">Vytvoří stránku bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-399">Creates the page without a PageModel.</span></span>

***

### <a name="viewimports-proto"></a><a name="namespace"></a><span data-ttu-id="4b7ac-400">viewimports, proto</span><span class="sxs-lookup"><span data-stu-id="4b7ac-400">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="4b7ac-401">Obor názvů pro generovaný kód.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-401">Namespace for the generated code.</span></span> <span data-ttu-id="4b7ac-402">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-402">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="4b7ac-403">blazorserver</span><span class="sxs-lookup"><span data-stu-id="4b7ac-403">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="4b7ac-404">Typ ověřování, které chcete použít.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-404">The type of authentication to use.</span></span> <span data-ttu-id="4b7ac-405">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="4b7ac-405">The possible values are:</span></span>

  - <span data-ttu-id="4b7ac-406">`None`- Žádné ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="4b7ac-406">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="4b7ac-407">`Individual`- Individuální autentizace.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-407">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="4b7ac-408">`IndividualB2C`- Individuální ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-408">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="4b7ac-409">`SingleOrg`- Organizační ověřování pro jednoho klienta.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-409">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="4b7ac-410">`MultiOrg`- Organizační ověřování pro více klientů.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-410">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="4b7ac-411">`Windows`- Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-411">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="4b7ac-412">Instance Azure Active Directory B2C, ke které se chcete připojit.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-412">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="4b7ac-413">Použití `IndividualB2C` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-413">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="4b7ac-414">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-414">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="4b7ac-415">ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-415">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="4b7ac-416">Použití `IndividualB2C` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-416">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="4b7ac-417">ID zásady obnovení hesla pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-417">The reset password policy ID for this project.</span></span> <span data-ttu-id="4b7ac-418">Použití `IndividualB2C` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-418">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="4b7ac-419">ID zásady úpravy profilu pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-419">The edit profile policy ID for this project.</span></span> <span data-ttu-id="4b7ac-420">Použití `IndividualB2C` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-420">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="4b7ac-421">Instance služby Azure Active Directory, ke které se chcete připojit.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-421">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="4b7ac-422">Použití `SingleOrg` s `MultiOrg` ověřováním nebo ověřování.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-422">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="4b7ac-423">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-423">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="4b7ac-424">ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-424">The Client ID for this project.</span></span> <span data-ttu-id="4b7ac-425">Použití `IndividualB2C`s `SingleOrg`protokolem , nebo `MultiOrg` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-425">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="4b7ac-426">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-426">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="4b7ac-427">Doména klienta adresáře.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-427">The domain for the directory tenant.</span></span> <span data-ttu-id="4b7ac-428">Použití `SingleOrg` s `IndividualB2C` ověřováním nebo ověřování.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-428">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="4b7ac-429">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-429">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="4b7ac-430">ID ID ID tenantid adresáře, ke kterému se chcete připojit.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-430">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="4b7ac-431">Použití `SingleOrg` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-431">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="4b7ac-432">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-432">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="4b7ac-433">Cesta požadavku v rámci základní cesty aplikace identifikátoru URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-433">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="4b7ac-434">Použití `SingleOrg` s `IndividualB2C` ověřováním nebo ověřování.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-434">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="4b7ac-435">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-435">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="4b7ac-436">Umožňuje této aplikaci přístup pro čtení do adresáře.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-436">Allows this application read-access to the directory.</span></span> <span data-ttu-id="4b7ac-437">Platí pouze `SingleOrg` pro `MultiOrg` nebo ověřování.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-437">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="4b7ac-438">Nezahrnuje *launchSettings.json* z generované šablony.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-438">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="4b7ac-439">Vypne protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-439">Turns off HTTPS.</span></span> <span data-ttu-id="4b7ac-440">Tato možnost platí `Individual`pouze `IndividualB2C` `SingleOrg`v `MultiOrg` případě, že se `--auth`pro .</span><span class="sxs-lookup"><span data-stu-id="4b7ac-440">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="4b7ac-441">Určuje LocalDB by měl být použit místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-441">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="4b7ac-442">Platí pouze `Individual` pro `IndividualB2C` nebo ověřování.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-442">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="4b7ac-443">Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-443">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="4b7ac-444">web</span><span class="sxs-lookup"><span data-stu-id="4b7ac-444">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="4b7ac-445">Nezahrnuje *launchSettings.json* z generované šablony.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-445">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="4b7ac-446">Určuje [rámec,](../../standard/frameworks.md) na který má být cílit.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-446">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="4b7ac-447">Možnost není k dispozici v sada .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-447">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="4b7ac-448">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, které používáte:</span><span class="sxs-lookup"><span data-stu-id="4b7ac-448">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="4b7ac-449">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="4b7ac-449">SDK version</span></span> | <span data-ttu-id="4b7ac-450">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="4b7ac-450">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="4b7ac-451">3.1</span><span class="sxs-lookup"><span data-stu-id="4b7ac-451">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="4b7ac-452">3.0</span><span class="sxs-lookup"><span data-stu-id="4b7ac-452">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="4b7ac-453">2.1</span><span class="sxs-lookup"><span data-stu-id="4b7ac-453">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="4b7ac-454">Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-454">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="4b7ac-455">Vypne protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-455">Turns off HTTPS.</span></span>

***

### <a name="mvc-webapp"></a><a name="web-options"></a><span data-ttu-id="4b7ac-456">mvc, webapp</span><span class="sxs-lookup"><span data-stu-id="4b7ac-456">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="4b7ac-457">Typ ověřování, které chcete použít.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-457">The type of authentication to use.</span></span> <span data-ttu-id="4b7ac-458">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="4b7ac-458">The possible values are:</span></span>

  - <span data-ttu-id="4b7ac-459">`None`- Žádné ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="4b7ac-459">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="4b7ac-460">`Individual`- Individuální autentizace.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-460">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="4b7ac-461">`IndividualB2C`- Individuální ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-461">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="4b7ac-462">`SingleOrg`- Organizační ověřování pro jednoho klienta.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-462">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="4b7ac-463">`MultiOrg`- Organizační ověřování pro více klientů.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-463">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="4b7ac-464">`Windows`- Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-464">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="4b7ac-465">Instance Azure Active Directory B2C, ke které se chcete připojit.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-465">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="4b7ac-466">Použití `IndividualB2C` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-466">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="4b7ac-467">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-467">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="4b7ac-468">ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-468">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="4b7ac-469">Použití `IndividualB2C` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-469">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="4b7ac-470">ID zásady obnovení hesla pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-470">The reset password policy ID for this project.</span></span> <span data-ttu-id="4b7ac-471">Použití `IndividualB2C` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-471">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="4b7ac-472">ID zásady úpravy profilu pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-472">The edit profile policy ID for this project.</span></span> <span data-ttu-id="4b7ac-473">Použití `IndividualB2C` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-473">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="4b7ac-474">Instance služby Azure Active Directory, ke které se chcete připojit.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-474">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="4b7ac-475">Použití `SingleOrg` s `MultiOrg` ověřováním nebo ověřování.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-475">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="4b7ac-476">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-476">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="4b7ac-477">ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-477">The Client ID for this project.</span></span> <span data-ttu-id="4b7ac-478">Použití `IndividualB2C`s `SingleOrg`protokolem , nebo `MultiOrg` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-478">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="4b7ac-479">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-479">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="4b7ac-480">Doména klienta adresáře.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-480">The domain for the directory tenant.</span></span> <span data-ttu-id="4b7ac-481">Použití `SingleOrg` s `IndividualB2C` ověřováním nebo ověřování.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-481">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="4b7ac-482">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-482">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="4b7ac-483">ID ID ID tenantid adresáře, ke kterému se chcete připojit.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-483">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="4b7ac-484">Použití `SingleOrg` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-484">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="4b7ac-485">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-485">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="4b7ac-486">Cesta požadavku v rámci základní cesty aplikace identifikátoru URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-486">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="4b7ac-487">Použití `SingleOrg` s `IndividualB2C` ověřováním nebo ověřování.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-487">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="4b7ac-488">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-488">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="4b7ac-489">Umožňuje této aplikaci přístup pro čtení do adresáře.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-489">Allows this application read-access to the directory.</span></span> <span data-ttu-id="4b7ac-490">Platí pouze `SingleOrg` pro `MultiOrg` nebo ověřování.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-490">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="4b7ac-491">Nezahrnuje *launchSettings.json* z generované šablony.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-491">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="4b7ac-492">Vypne protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-492">Turns off HTTPS.</span></span> <span data-ttu-id="4b7ac-493">Tato možnost platí `Individual`pouze `IndividualB2C` `SingleOrg`v `MultiOrg` případě, , , , nebo nejsou používány.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-493">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="4b7ac-494">Určuje LocalDB by měl být použit místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-494">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="4b7ac-495">Platí pouze `Individual` pro `IndividualB2C` nebo ověřování.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-495">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="4b7ac-496">Určuje [rámec,](../../standard/frameworks.md) na který má být cílit.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-496">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="4b7ac-497">Možnost je k dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-497">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="4b7ac-498">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, které používáte:</span><span class="sxs-lookup"><span data-stu-id="4b7ac-498">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="4b7ac-499">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="4b7ac-499">SDK version</span></span> | <span data-ttu-id="4b7ac-500">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="4b7ac-500">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="4b7ac-501">3.1</span><span class="sxs-lookup"><span data-stu-id="4b7ac-501">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="4b7ac-502">3.0</span><span class="sxs-lookup"><span data-stu-id="4b7ac-502">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="4b7ac-503">Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-503">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="4b7ac-504">Zahrnuje BrowserLink v projektu.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-504">Includes BrowserLink in the project.</span></span> <span data-ttu-id="4b7ac-505">Možnost není k dispozici v .NET Core 2.2 a 3.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-505">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="4b7ac-506">Určuje, zda je projekt nakonfigurován pro použití [kompilace razor runtime](/aspnet/core/mvc/views/view-compilation#runtime-compilation) v sestaveních ladění.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-506">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="4b7ac-507">Možnost je k dispozici od .NET Core 3.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-507">Option available since .NET Core 3.1 SDK.</span></span>

***

### <a name="angular-react"></a><a name="spa"></a><span data-ttu-id="4b7ac-508">úhlové, reagovat</span><span class="sxs-lookup"><span data-stu-id="4b7ac-508">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="4b7ac-509">Typ ověřování, které chcete použít.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-509">The type of authentication to use.</span></span> <span data-ttu-id="4b7ac-510">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-510">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="4b7ac-511">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="4b7ac-511">The possible values are:</span></span>

  - <span data-ttu-id="4b7ac-512">`None`- Žádné ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="4b7ac-512">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="4b7ac-513">`Individual`- Individuální autentizace.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-513">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="4b7ac-514">Nezahrnuje *launchSettings.json* z generované šablony.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-514">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="4b7ac-515">Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-515">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="4b7ac-516">Vypne protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-516">Turns off HTTPS.</span></span> <span data-ttu-id="4b7ac-517">Tato možnost platí pouze `None`v případě, že ověřování je .</span><span class="sxs-lookup"><span data-stu-id="4b7ac-517">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="4b7ac-518">Určuje LocalDB by měl být použit místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-518">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="4b7ac-519">Platí pouze `Individual` pro `IndividualB2C` nebo ověřování.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-519">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="4b7ac-520">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-520">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="4b7ac-521">Určuje [rámec,](../../standard/frameworks.md) na který má být cílit.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-521">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="4b7ac-522">Možnost není k dispozici v sada .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-522">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="4b7ac-523">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, které používáte:</span><span class="sxs-lookup"><span data-stu-id="4b7ac-523">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="4b7ac-524">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="4b7ac-524">SDK version</span></span> | <span data-ttu-id="4b7ac-525">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="4b7ac-525">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="4b7ac-526">3.1</span><span class="sxs-lookup"><span data-stu-id="4b7ac-526">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="4b7ac-527">3.0</span><span class="sxs-lookup"><span data-stu-id="4b7ac-527">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="4b7ac-528">2.1</span><span class="sxs-lookup"><span data-stu-id="4b7ac-528">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="4b7ac-529">reactredux</span><span class="sxs-lookup"><span data-stu-id="4b7ac-529">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="4b7ac-530">Nezahrnuje *launchSettings.json* z generované šablony.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-530">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="4b7ac-531">Určuje [rámec,](../../standard/frameworks.md) na který má být cílit.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-531">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="4b7ac-532">Možnost není k dispozici v sada .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-532">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="4b7ac-533">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, které používáte:</span><span class="sxs-lookup"><span data-stu-id="4b7ac-533">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="4b7ac-534">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="4b7ac-534">SDK version</span></span> | <span data-ttu-id="4b7ac-535">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="4b7ac-535">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="4b7ac-536">3.1</span><span class="sxs-lookup"><span data-stu-id="4b7ac-536">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="4b7ac-537">3.0</span><span class="sxs-lookup"><span data-stu-id="4b7ac-537">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="4b7ac-538">2.1</span><span class="sxs-lookup"><span data-stu-id="4b7ac-538">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="4b7ac-539">Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-539">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="4b7ac-540">Vypne protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-540">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="4b7ac-541">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="4b7ac-541">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="4b7ac-542">Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-542">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="4b7ac-543">Podporuje přidávání tradičních stránek Razor a zobrazení kromě komponent do této knihovny.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-543">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="4b7ac-544">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-544">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="4b7ac-545">webapi</span><span class="sxs-lookup"><span data-stu-id="4b7ac-545">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="4b7ac-546">Typ ověřování, které chcete použít.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-546">The type of authentication to use.</span></span> <span data-ttu-id="4b7ac-547">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="4b7ac-547">The possible values are:</span></span>

  - <span data-ttu-id="4b7ac-548">`None`- Žádné ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="4b7ac-548">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="4b7ac-549">`IndividualB2C`- Individuální ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-549">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="4b7ac-550">`SingleOrg`- Organizační ověřování pro jednoho klienta.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-550">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="4b7ac-551">`Windows`- Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-551">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="4b7ac-552">Instance Azure Active Directory B2C, ke které se chcete připojit.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-552">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="4b7ac-553">Použití `IndividualB2C` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-553">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="4b7ac-554">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-554">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="4b7ac-555">ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-555">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="4b7ac-556">Použití `IndividualB2C` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-556">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="4b7ac-557">Instance služby Azure Active Directory, ke které se chcete připojit.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-557">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="4b7ac-558">Použití `SingleOrg` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-558">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="4b7ac-559">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-559">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="4b7ac-560">ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-560">The Client ID for this project.</span></span> <span data-ttu-id="4b7ac-561">Použití `IndividualB2C` s `SingleOrg` ověřováním nebo ověřování.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-561">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="4b7ac-562">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-562">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="4b7ac-563">Doména klienta adresáře.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-563">The domain for the directory tenant.</span></span> <span data-ttu-id="4b7ac-564">Použití `IndividualB2C` s `SingleOrg` ověřováním nebo ověřování.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-564">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="4b7ac-565">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-565">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="4b7ac-566">ID ID ID tenantid adresáře, ke kterému se chcete připojit.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-566">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="4b7ac-567">Použití `SingleOrg` s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-567">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="4b7ac-568">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-568">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="4b7ac-569">Umožňuje této aplikaci přístup pro čtení do adresáře.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-569">Allows this application read-access to the directory.</span></span> <span data-ttu-id="4b7ac-570">Platí pouze `SingleOrg` pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-570">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="4b7ac-571">Nezahrnuje *launchSettings.json* z generované šablony.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-571">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="4b7ac-572">Vypne protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-572">Turns off HTTPS.</span></span> <span data-ttu-id="4b7ac-573">`app.UseHsts`a `app.UseHttpsRedirection` nejsou přidány `Startup.Configure`do .</span><span class="sxs-lookup"><span data-stu-id="4b7ac-573">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="4b7ac-574">Tato možnost platí `IndividualB2C` pouze `SingleOrg` v případě, že se k ověřování používá nebo nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-574">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="4b7ac-575">Určuje LocalDB by měl být použit místo SQLite.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-575">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="4b7ac-576">Platí pouze `IndividualB2C` pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-576">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="4b7ac-577">Určuje [rámec,](../../standard/frameworks.md) na který má být cílit.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-577">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="4b7ac-578">Možnost není k dispozici v sada .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-578">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="4b7ac-579">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, které používáte:</span><span class="sxs-lookup"><span data-stu-id="4b7ac-579">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="4b7ac-580">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="4b7ac-580">SDK version</span></span> | <span data-ttu-id="4b7ac-581">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="4b7ac-581">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="4b7ac-582">3.1</span><span class="sxs-lookup"><span data-stu-id="4b7ac-582">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="4b7ac-583">3.0</span><span class="sxs-lookup"><span data-stu-id="4b7ac-583">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="4b7ac-584">2.1</span><span class="sxs-lookup"><span data-stu-id="4b7ac-584">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="4b7ac-585">Neprovede implicitní obnovení během vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-585">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="4b7ac-586">globaljson</span><span class="sxs-lookup"><span data-stu-id="4b7ac-586">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="4b7ac-587">Určuje verzi sady .NET Core SDK, která má být používána v souboru *global.json.*</span><span class="sxs-lookup"><span data-stu-id="4b7ac-587">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="4b7ac-588">Příklady</span><span class="sxs-lookup"><span data-stu-id="4b7ac-588">Examples</span></span>

- <span data-ttu-id="4b7ac-589">Vytvořte projekt aplikace konzoly Jazyka C# zadáním názvu šablony:</span><span class="sxs-lookup"><span data-stu-id="4b7ac-589">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="4b7ac-590">Vytvořte projekt aplikace konzoly F# v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="4b7ac-590">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang F#
  ```

- <span data-ttu-id="4b7ac-591">Vytvořte projekt knihovny tříd .NET Standard v zadaném adresáři:</span><span class="sxs-lookup"><span data-stu-id="4b7ac-591">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="4b7ac-592">Vytvořte nový ASP.NET projektu Core C# MVC v aktuálním adresáři bez ověřování:</span><span class="sxs-lookup"><span data-stu-id="4b7ac-592">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="4b7ac-593">Vytvořte nový projekt xUnit:</span><span class="sxs-lookup"><span data-stu-id="4b7ac-593">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="4b7ac-594">Seznam všech šablon dostupných pro jednostránkové aplikace (SPA) šablony:</span><span class="sxs-lookup"><span data-stu-id="4b7ac-594">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="4b7ac-595">Seznam všech šablon odpovídajících podřetězci *we.*</span><span class="sxs-lookup"><span data-stu-id="4b7ac-595">List all templates matching the *we* substring.</span></span> <span data-ttu-id="4b7ac-596">Nebyla nalezena žádná přesná shoda, takže porovnávání podřetězců se spustí proti sloupcům krátkého názvu i názvu.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-596">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="4b7ac-597">Pokus o vyvolání šablony odpovídající *ng*.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-597">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="4b7ac-598">Pokud nelze určit jednu shodu, uveďte šablony, které se částečně shodují.</span><span class="sxs-lookup"><span data-stu-id="4b7ac-598">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="4b7ac-599">Nainstalujte verzi 2.0 šablon SPA pro ASP.NET Core:</span><span class="sxs-lookup"><span data-stu-id="4b7ac-599">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="4b7ac-600">Seznam nainstalovaných šablon a podrobnosti o nich, včetně toho, jak je odinstalovat:</span><span class="sxs-lookup"><span data-stu-id="4b7ac-600">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="4b7ac-601">Vytvořte *soubor global.json* v aktuálním adresáři, který nastavuje verzi sady SDK na 3.1.101:</span><span class="sxs-lookup"><span data-stu-id="4b7ac-601">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="4b7ac-602">Viz také</span><span class="sxs-lookup"><span data-stu-id="4b7ac-602">See also</span></span>

- [<span data-ttu-id="4b7ac-603">Vlastní šablony pro dotnet nové</span><span class="sxs-lookup"><span data-stu-id="4b7ac-603">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="4b7ac-604">Vytvoření vlastní šablony pro dotnet new</span><span class="sxs-lookup"><span data-stu-id="4b7ac-604">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="4b7ac-605">úložiště GitHub u dotnet/dotnet-template-samples GitHub</span><span class="sxs-lookup"><span data-stu-id="4b7ac-605">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="4b7ac-606">Dostupné šablony pro dotnet nové</span><span class="sxs-lookup"><span data-stu-id="4b7ac-606">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
