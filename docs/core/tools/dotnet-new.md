---
title: dotnet – nový příkaz
description: Příkaz dotnet New vytvoří nové projekty .NET Core založené na zadané šabloně.
ms.date: 02/13/2020
ms.openlocfilehash: d3c609419596b123f5bfb3ca85cf292a61154a70
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157216"
---
# <a name="dotnet-new"></a><span data-ttu-id="739d1-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="739d1-103">dotnet new</span></span>

<span data-ttu-id="739d1-104">**Tento článek se týká:** ✔️ .net Core 2,0 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="739d1-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="739d1-105">Název</span><span class="sxs-lookup"><span data-stu-id="739d1-105">Name</span></span>

<span data-ttu-id="739d1-106">`dotnet new` – vytvoří nový projekt, konfigurační soubor nebo řešení na základě zadané šablony.</span><span class="sxs-lookup"><span data-stu-id="739d1-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="739d1-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="739d1-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name]
    [--nuget-source] [-o|--output] [-u|--uninstall] [--update-apply] [--update-check] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

## <a name="description"></a><span data-ttu-id="739d1-108">Popis</span><span class="sxs-lookup"><span data-stu-id="739d1-108">Description</span></span>

<span data-ttu-id="739d1-109">Příkaz `dotnet new` vytvoří projekt .NET Core nebo jiné artefakty založené na šabloně.</span><span class="sxs-lookup"><span data-stu-id="739d1-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="739d1-110">Příkaz volá [modul šablony](https://github.com/dotnet/templating) a vytvoří artefakty na disku na základě zadané šablony a možností.</span><span class="sxs-lookup"><span data-stu-id="739d1-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="739d1-111">Argumenty</span><span class="sxs-lookup"><span data-stu-id="739d1-111">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="739d1-112">Šablona, která se má vytvořit při vyvolání příkazu</span><span class="sxs-lookup"><span data-stu-id="739d1-112">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="739d1-113">Každá šablona může mít konkrétní možnosti, které můžete předat.</span><span class="sxs-lookup"><span data-stu-id="739d1-113">Each template might have specific options you can pass.</span></span> <span data-ttu-id="739d1-114">Další informace najdete v tématu [Možnosti šablony](#template-options).</span><span class="sxs-lookup"><span data-stu-id="739d1-114">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="739d1-115">Můžete spustit `dotnet new --list`, abyste zobrazili seznam všech nainstalovaných šablon.</span><span class="sxs-lookup"><span data-stu-id="739d1-115">You can run `dotnet new --list` to see a list of all installed templates.</span></span> <span data-ttu-id="739d1-116">Pokud hodnota `TEMPLATE` není přesná shoda na textu v **šablonách** nebo ve sloupci **krátký název** z vrácené tabulky, provede se shoda podřetězce na těchto dvou sloupcích.</span><span class="sxs-lookup"><span data-stu-id="739d1-116">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="739d1-117">Počínaje verzí .NET Core 3,0 SDK vyhledává CLI šablony v NuGet.org při vyvolání příkazu `dotnet new` v následujících podmínkách:</span><span class="sxs-lookup"><span data-stu-id="739d1-117">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="739d1-118">Pokud rozhraní příkazového řádku nemůže najít shodu šablony při vyvolání `dotnet new`, a ne i částečně.</span><span class="sxs-lookup"><span data-stu-id="739d1-118">If the CLI can’t find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="739d1-119">Pokud je k dispozici novější verze šablony.</span><span class="sxs-lookup"><span data-stu-id="739d1-119">If there’s a newer version of the template available.</span></span> <span data-ttu-id="739d1-120">V tomto případě se vytvoří projekt nebo artefakt, ale rozhraní příkazového řádku vás upozorní na aktualizovanou verzi šablony.</span><span class="sxs-lookup"><span data-stu-id="739d1-120">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="739d1-121">Příkaz obsahuje výchozí seznam šablon.</span><span class="sxs-lookup"><span data-stu-id="739d1-121">The command contains a default list of templates.</span></span> <span data-ttu-id="739d1-122">Seznam dostupných šablon můžete získat pomocí `dotnet new -l`.</span><span class="sxs-lookup"><span data-stu-id="739d1-122">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="739d1-123">Následující tabulka obsahuje šablony, které jsou předinstalované s .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="739d1-123">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="739d1-124">Výchozí jazyk pro šablonu se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="739d1-124">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="739d1-125">Kliknutím na odkaz krátké jméno zobrazíte konkrétní možnosti šablony.</span><span class="sxs-lookup"><span data-stu-id="739d1-125">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="739d1-126">Šablony</span><span class="sxs-lookup"><span data-stu-id="739d1-126">Templates</span></span>                                    | <span data-ttu-id="739d1-127">Krátký název</span><span class="sxs-lookup"><span data-stu-id="739d1-127">Short name</span></span>                      | <span data-ttu-id="739d1-128">Jazyk</span><span class="sxs-lookup"><span data-stu-id="739d1-128">Language</span></span>     | <span data-ttu-id="739d1-129">Značky</span><span class="sxs-lookup"><span data-stu-id="739d1-129">Tags</span></span>                                  | <span data-ttu-id="739d1-130">Vedou</span><span class="sxs-lookup"><span data-stu-id="739d1-130">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="739d1-131">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="739d1-131">Console Application</span></span>                          | [<span data-ttu-id="739d1-132">stromu</span><span class="sxs-lookup"><span data-stu-id="739d1-132">console</span></span>](#console)             | <span data-ttu-id="739d1-133">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="739d1-133">[C#], F#, VB</span></span> | <span data-ttu-id="739d1-134">Společná/konzola</span><span class="sxs-lookup"><span data-stu-id="739d1-134">Common/Console</span></span>                        | <span data-ttu-id="739d1-135">1.0</span><span class="sxs-lookup"><span data-stu-id="739d1-135">1.0</span></span>        |
| <span data-ttu-id="739d1-136">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="739d1-136">Class library</span></span>                                | [<span data-ttu-id="739d1-137">že knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="739d1-137">classlib</span></span>](#classlib)           | <span data-ttu-id="739d1-138">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="739d1-138">[C#], F#, VB</span></span> | <span data-ttu-id="739d1-139">Společné/knihovny</span><span class="sxs-lookup"><span data-stu-id="739d1-139">Common/Library</span></span>                        | <span data-ttu-id="739d1-140">1.0</span><span class="sxs-lookup"><span data-stu-id="739d1-140">1.0</span></span>        |
| <span data-ttu-id="739d1-141">Aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="739d1-141">WPF Application</span></span>                              | [<span data-ttu-id="739d1-142">subsystém</span><span class="sxs-lookup"><span data-stu-id="739d1-142">wpf</span></span>](#wpf)                     | <span data-ttu-id="739d1-143">[C#]</span><span class="sxs-lookup"><span data-stu-id="739d1-143">[C#]</span></span>         | <span data-ttu-id="739d1-144">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="739d1-144">Common/WPF</span></span>                            | <span data-ttu-id="739d1-145">3.0</span><span class="sxs-lookup"><span data-stu-id="739d1-145">3.0</span></span>        |
| <span data-ttu-id="739d1-146">WPF – knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="739d1-146">WPF Class library</span></span>                            | [<span data-ttu-id="739d1-147">wpflib</span><span class="sxs-lookup"><span data-stu-id="739d1-147">wpflib</span></span>](#wpf)                  | <span data-ttu-id="739d1-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="739d1-148">[C#]</span></span>         | <span data-ttu-id="739d1-149">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="739d1-149">Common/WPF</span></span>                            | <span data-ttu-id="739d1-150">3.0</span><span class="sxs-lookup"><span data-stu-id="739d1-150">3.0</span></span>        |
| <span data-ttu-id="739d1-151">Knihovna vlastních ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="739d1-151">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="739d1-152">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="739d1-152">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="739d1-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="739d1-153">[C#]</span></span>         | <span data-ttu-id="739d1-154">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="739d1-154">Common/WPF</span></span>                            | <span data-ttu-id="739d1-155">3.0</span><span class="sxs-lookup"><span data-stu-id="739d1-155">3.0</span></span>        |
| <span data-ttu-id="739d1-156">Knihovna uživatelských ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="739d1-156">WPF User Control Library</span></span>                     | [<span data-ttu-id="739d1-157">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="739d1-157">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="739d1-158">[C#]</span><span class="sxs-lookup"><span data-stu-id="739d1-158">[C#]</span></span>         | <span data-ttu-id="739d1-159">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="739d1-159">Common/WPF</span></span>                            | <span data-ttu-id="739d1-160">3.0</span><span class="sxs-lookup"><span data-stu-id="739d1-160">3.0</span></span>        |
| <span data-ttu-id="739d1-161">Aplikace model Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="739d1-161">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="739d1-162">WinForms</span><span class="sxs-lookup"><span data-stu-id="739d1-162">winforms</span></span>](#winforms)           | <span data-ttu-id="739d1-163">[C#]</span><span class="sxs-lookup"><span data-stu-id="739d1-163">[C#]</span></span>         | <span data-ttu-id="739d1-164">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="739d1-164">Common/WinForms</span></span>                       | <span data-ttu-id="739d1-165">3.0</span><span class="sxs-lookup"><span data-stu-id="739d1-165">3.0</span></span>        |
| <span data-ttu-id="739d1-166">Knihovna tříd model Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="739d1-166">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="739d1-167">winformslib</span><span class="sxs-lookup"><span data-stu-id="739d1-167">winformslib</span></span>](#winforms)        | <span data-ttu-id="739d1-168">[C#]</span><span class="sxs-lookup"><span data-stu-id="739d1-168">[C#]</span></span>         | <span data-ttu-id="739d1-169">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="739d1-169">Common/WinForms</span></span>                       | <span data-ttu-id="739d1-170">3.0</span><span class="sxs-lookup"><span data-stu-id="739d1-170">3.0</span></span>        |
| <span data-ttu-id="739d1-171">Služba pracovního procesu</span><span class="sxs-lookup"><span data-stu-id="739d1-171">Worker Service</span></span>                               | [<span data-ttu-id="739d1-172">zaměstnanec</span><span class="sxs-lookup"><span data-stu-id="739d1-172">worker</span></span>](#web-others)           | <span data-ttu-id="739d1-173">[C#]</span><span class="sxs-lookup"><span data-stu-id="739d1-173">[C#]</span></span>         | <span data-ttu-id="739d1-174">Common/Work/Web</span><span class="sxs-lookup"><span data-stu-id="739d1-174">Common/Worker/Web</span></span>                     | <span data-ttu-id="739d1-175">3.0</span><span class="sxs-lookup"><span data-stu-id="739d1-175">3.0</span></span>        |
| <span data-ttu-id="739d1-176">Projekt testu jednotek</span><span class="sxs-lookup"><span data-stu-id="739d1-176">Unit Test Project</span></span>                            | [<span data-ttu-id="739d1-177">MSTest</span><span class="sxs-lookup"><span data-stu-id="739d1-177">mstest</span></span>](#test)                 | <span data-ttu-id="739d1-178">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="739d1-178">[C#], F#, VB</span></span> | <span data-ttu-id="739d1-179">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="739d1-179">Test/MSTest</span></span>                           | <span data-ttu-id="739d1-180">1.0</span><span class="sxs-lookup"><span data-stu-id="739d1-180">1.0</span></span>        |
| <span data-ttu-id="739d1-181">Projekt testů NUnit 3</span><span class="sxs-lookup"><span data-stu-id="739d1-181">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="739d1-182">nunit</span><span class="sxs-lookup"><span data-stu-id="739d1-182">nunit</span></span>](#nunit)                  | <span data-ttu-id="739d1-183">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="739d1-183">[C#], F#, VB</span></span> | <span data-ttu-id="739d1-184">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="739d1-184">Test/NUnit</span></span>                            | <span data-ttu-id="739d1-185">2.1.400</span><span class="sxs-lookup"><span data-stu-id="739d1-185">2.1.400</span></span>    |
| <span data-ttu-id="739d1-186">NUnit 3 položka testu</span><span class="sxs-lookup"><span data-stu-id="739d1-186">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="739d1-187">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="739d1-187">[C#], F#, VB</span></span> | <span data-ttu-id="739d1-188">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="739d1-188">Test/NUnit</span></span>                            | <span data-ttu-id="739d1-189">2.2</span><span class="sxs-lookup"><span data-stu-id="739d1-189">2.2</span></span>        |
| <span data-ttu-id="739d1-190">Projekt testů xUnit</span><span class="sxs-lookup"><span data-stu-id="739d1-190">xUnit Test Project</span></span>                           | [<span data-ttu-id="739d1-191">xUnit</span><span class="sxs-lookup"><span data-stu-id="739d1-191">xunit</span></span>](#test)                  | <span data-ttu-id="739d1-192">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="739d1-192">[C#], F#, VB</span></span> | <span data-ttu-id="739d1-193">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="739d1-193">Test/xUnit</span></span>                            | <span data-ttu-id="739d1-194">1.0</span><span class="sxs-lookup"><span data-stu-id="739d1-194">1.0</span></span>        |
| <span data-ttu-id="739d1-195">Komponenta Razor</span><span class="sxs-lookup"><span data-stu-id="739d1-195">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="739d1-196">[C#]</span><span class="sxs-lookup"><span data-stu-id="739d1-196">[C#]</span></span>         | <span data-ttu-id="739d1-197">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="739d1-197">Web/ASP.NET</span></span>                           | <span data-ttu-id="739d1-198">3.0</span><span class="sxs-lookup"><span data-stu-id="739d1-198">3.0</span></span>        |
| <span data-ttu-id="739d1-199">Stránka Razor</span><span class="sxs-lookup"><span data-stu-id="739d1-199">Razor Page</span></span>                                   | [<span data-ttu-id="739d1-200">Page</span><span class="sxs-lookup"><span data-stu-id="739d1-200">page</span></span>](#page)                   | <span data-ttu-id="739d1-201">[C#]</span><span class="sxs-lookup"><span data-stu-id="739d1-201">[C#]</span></span>         | <span data-ttu-id="739d1-202">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="739d1-202">Web/ASP.NET</span></span>                           | <span data-ttu-id="739d1-203">2.0</span><span class="sxs-lookup"><span data-stu-id="739d1-203">2.0</span></span>        |
| <span data-ttu-id="739d1-204">ViewImports MVC</span><span class="sxs-lookup"><span data-stu-id="739d1-204">MVC ViewImports</span></span>                              | [<span data-ttu-id="739d1-205">viewimports</span><span class="sxs-lookup"><span data-stu-id="739d1-205">viewimports</span></span>](#namespace)       | <span data-ttu-id="739d1-206">[C#]</span><span class="sxs-lookup"><span data-stu-id="739d1-206">[C#]</span></span>         | <span data-ttu-id="739d1-207">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="739d1-207">Web/ASP.NET</span></span>                           | <span data-ttu-id="739d1-208">2.0</span><span class="sxs-lookup"><span data-stu-id="739d1-208">2.0</span></span>        |
| <span data-ttu-id="739d1-209">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="739d1-209">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="739d1-210">[C#]</span><span class="sxs-lookup"><span data-stu-id="739d1-210">[C#]</span></span>         | <span data-ttu-id="739d1-211">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="739d1-211">Web/ASP.NET</span></span>                           | <span data-ttu-id="739d1-212">2.0</span><span class="sxs-lookup"><span data-stu-id="739d1-212">2.0</span></span>        |
| <span data-ttu-id="739d1-213">Aplikace serveru Blazor</span><span class="sxs-lookup"><span data-stu-id="739d1-213">Blazor Server App</span></span>                            | [<span data-ttu-id="739d1-214">blazorserver</span><span class="sxs-lookup"><span data-stu-id="739d1-214">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="739d1-215">[C#]</span><span class="sxs-lookup"><span data-stu-id="739d1-215">[C#]</span></span>         | <span data-ttu-id="739d1-216">Web/Blazor</span><span class="sxs-lookup"><span data-stu-id="739d1-216">Web/Blazor</span></span>                            | <span data-ttu-id="739d1-217">3.0</span><span class="sxs-lookup"><span data-stu-id="739d1-217">3.0</span></span>        |
| <span data-ttu-id="739d1-218">ASP.NET Core prázdné</span><span class="sxs-lookup"><span data-stu-id="739d1-218">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="739d1-219">webovém</span><span class="sxs-lookup"><span data-stu-id="739d1-219">web</span></span>](#web)                     | <span data-ttu-id="739d1-220">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="739d1-220">[C#], F#</span></span>     | <span data-ttu-id="739d1-221">Web/prázdné</span><span class="sxs-lookup"><span data-stu-id="739d1-221">Web/Empty</span></span>                             | <span data-ttu-id="739d1-222">1.0</span><span class="sxs-lookup"><span data-stu-id="739d1-222">1.0</span></span>        |
| <span data-ttu-id="739d1-223">ASP.NET Core webová aplikace (model-zobrazení-kontroler)</span><span class="sxs-lookup"><span data-stu-id="739d1-223">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="739d1-224">Návrhový</span><span class="sxs-lookup"><span data-stu-id="739d1-224">mvc</span></span>](#web-options)             | <span data-ttu-id="739d1-225">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="739d1-225">[C#], F#</span></span>     | <span data-ttu-id="739d1-226">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="739d1-226">Web/MVC</span></span>                               | <span data-ttu-id="739d1-227">1.0</span><span class="sxs-lookup"><span data-stu-id="739d1-227">1.0</span></span>        |
| <span data-ttu-id="739d1-228">ASP.NET Core webové aplikace</span><span class="sxs-lookup"><span data-stu-id="739d1-228">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="739d1-229">WebApp, Razor</span><span class="sxs-lookup"><span data-stu-id="739d1-229">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="739d1-230">[C#]</span><span class="sxs-lookup"><span data-stu-id="739d1-230">[C#]</span></span>         | <span data-ttu-id="739d1-231">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="739d1-231">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="739d1-232">2,2, 2,0</span><span class="sxs-lookup"><span data-stu-id="739d1-232">2.2, 2.0</span></span>   |
| <span data-ttu-id="739d1-233">ASP.NET Core s úhlovým</span><span class="sxs-lookup"><span data-stu-id="739d1-233">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="739d1-234">Angular</span><span class="sxs-lookup"><span data-stu-id="739d1-234">angular</span></span>](#spa)                 | <span data-ttu-id="739d1-235">[C#]</span><span class="sxs-lookup"><span data-stu-id="739d1-235">[C#]</span></span>         | <span data-ttu-id="739d1-236">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="739d1-236">Web/MVC/SPA</span></span>                           | <span data-ttu-id="739d1-237">2.0</span><span class="sxs-lookup"><span data-stu-id="739d1-237">2.0</span></span>        |
| <span data-ttu-id="739d1-238">ASP.NET Core s reagují. js</span><span class="sxs-lookup"><span data-stu-id="739d1-238">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="739d1-239">reaguje</span><span class="sxs-lookup"><span data-stu-id="739d1-239">react</span></span>](#spa)                   | <span data-ttu-id="739d1-240">[C#]</span><span class="sxs-lookup"><span data-stu-id="739d1-240">[C#]</span></span>         | <span data-ttu-id="739d1-241">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="739d1-241">Web/MVC/SPA</span></span>                           | <span data-ttu-id="739d1-242">2.0</span><span class="sxs-lookup"><span data-stu-id="739d1-242">2.0</span></span>        |
| <span data-ttu-id="739d1-243">ASP.NET Core s využitím reagují. js a Redux</span><span class="sxs-lookup"><span data-stu-id="739d1-243">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="739d1-244">reactredux</span><span class="sxs-lookup"><span data-stu-id="739d1-244">reactredux</span></span>](#reactredux)       | <span data-ttu-id="739d1-245">[C#]</span><span class="sxs-lookup"><span data-stu-id="739d1-245">[C#]</span></span>         | <span data-ttu-id="739d1-246">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="739d1-246">Web/MVC/SPA</span></span>                           | <span data-ttu-id="739d1-247">2.0</span><span class="sxs-lookup"><span data-stu-id="739d1-247">2.0</span></span>        |
| <span data-ttu-id="739d1-248">Knihovna tříd Razor</span><span class="sxs-lookup"><span data-stu-id="739d1-248">Razor Class Library</span></span>                          | [<span data-ttu-id="739d1-249">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="739d1-249">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="739d1-250">[C#]</span><span class="sxs-lookup"><span data-stu-id="739d1-250">[C#]</span></span>         | <span data-ttu-id="739d1-251">Knihovna tříd web/Razor/Library/Razor</span><span class="sxs-lookup"><span data-stu-id="739d1-251">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="739d1-252">2.1</span><span class="sxs-lookup"><span data-stu-id="739d1-252">2.1</span></span>        |
| <span data-ttu-id="739d1-253">Webové rozhraní API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="739d1-253">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="739d1-254">WebApi</span><span class="sxs-lookup"><span data-stu-id="739d1-254">webapi</span></span>](#webapi)               | <span data-ttu-id="739d1-255">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="739d1-255">[C#], F#</span></span>     | <span data-ttu-id="739d1-256">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="739d1-256">Web/WebAPI</span></span>                            | <span data-ttu-id="739d1-257">1.0</span><span class="sxs-lookup"><span data-stu-id="739d1-257">1.0</span></span>        |
| <span data-ttu-id="739d1-258">Služba ASP.NET Core gRPC</span><span class="sxs-lookup"><span data-stu-id="739d1-258">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="739d1-259">grpc</span><span class="sxs-lookup"><span data-stu-id="739d1-259">grpc</span></span>](#web-others)             | <span data-ttu-id="739d1-260">[C#]</span><span class="sxs-lookup"><span data-stu-id="739d1-260">[C#]</span></span>         | <span data-ttu-id="739d1-261">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="739d1-261">Web/gRPC</span></span>                              | <span data-ttu-id="739d1-262">3.0</span><span class="sxs-lookup"><span data-stu-id="739d1-262">3.0</span></span>        |
| <span data-ttu-id="739d1-263">Soubor vyrovnávací paměti protokolu</span><span class="sxs-lookup"><span data-stu-id="739d1-263">Protocol Buffer File</span></span>                         | [<span data-ttu-id="739d1-264">Proto</span><span class="sxs-lookup"><span data-stu-id="739d1-264">proto</span></span>](#namespace)             |              | <span data-ttu-id="739d1-265">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="739d1-265">Web/gRPC</span></span>                              | <span data-ttu-id="739d1-266">3.0</span><span class="sxs-lookup"><span data-stu-id="739d1-266">3.0</span></span>        |
| <span data-ttu-id="739d1-267">soubor dotnet gitignore</span><span class="sxs-lookup"><span data-stu-id="739d1-267">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="739d1-268">Config</span><span class="sxs-lookup"><span data-stu-id="739d1-268">Config</span></span>                                | <span data-ttu-id="739d1-269">3.0</span><span class="sxs-lookup"><span data-stu-id="739d1-269">3.0</span></span>        |
| <span data-ttu-id="739d1-270">global.json file</span><span class="sxs-lookup"><span data-stu-id="739d1-270">global.json file</span></span>                             | [<span data-ttu-id="739d1-271">globaljson</span><span class="sxs-lookup"><span data-stu-id="739d1-271">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="739d1-272">Config</span><span class="sxs-lookup"><span data-stu-id="739d1-272">Config</span></span>                                | <span data-ttu-id="739d1-273">2.0</span><span class="sxs-lookup"><span data-stu-id="739d1-273">2.0</span></span>        |
| <span data-ttu-id="739d1-274">Konfigurace NuGet</span><span class="sxs-lookup"><span data-stu-id="739d1-274">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="739d1-275">Config</span><span class="sxs-lookup"><span data-stu-id="739d1-275">Config</span></span>                                | <span data-ttu-id="739d1-276">1.0</span><span class="sxs-lookup"><span data-stu-id="739d1-276">1.0</span></span>        |
| <span data-ttu-id="739d1-277">dotnet – místní nástroj soubor manifestu</span><span class="sxs-lookup"><span data-stu-id="739d1-277">dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="739d1-278">Config</span><span class="sxs-lookup"><span data-stu-id="739d1-278">Config</span></span>                                | <span data-ttu-id="739d1-279">3.0</span><span class="sxs-lookup"><span data-stu-id="739d1-279">3.0</span></span>        |
| <span data-ttu-id="739d1-280">Webová konfigurace</span><span class="sxs-lookup"><span data-stu-id="739d1-280">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="739d1-281">Config</span><span class="sxs-lookup"><span data-stu-id="739d1-281">Config</span></span>                                | <span data-ttu-id="739d1-282">1.0</span><span class="sxs-lookup"><span data-stu-id="739d1-282">1.0</span></span>        |
| <span data-ttu-id="739d1-283">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="739d1-283">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="739d1-284">Řešení</span><span class="sxs-lookup"><span data-stu-id="739d1-284">Solution</span></span>                              | <span data-ttu-id="739d1-285">1.0</span><span class="sxs-lookup"><span data-stu-id="739d1-285">1.0</span></span>        |

## <a name="options"></a><span data-ttu-id="739d1-286">Možnosti</span><span class="sxs-lookup"><span data-stu-id="739d1-286">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="739d1-287">Zobrazí souhrn toho, co se stane, když se spustí daný příkaz.</span><span class="sxs-lookup"><span data-stu-id="739d1-287">Displays a summary of what would happen if the given command were run.</span></span> <span data-ttu-id="739d1-288">K dispozici od verze .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="739d1-288">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="739d1-289">Vynutí vygenerování obsahu i v případě, že změní existující soubory.</span><span class="sxs-lookup"><span data-stu-id="739d1-289">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="739d1-290">Tato možnost je vyžadována, pokud by vybraná šablona přepsala existující soubory ve výstupním adresáři.</span><span class="sxs-lookup"><span data-stu-id="739d1-290">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="739d1-291">Vytiskne nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="739d1-291">Prints out help for the command.</span></span> <span data-ttu-id="739d1-292">Dá se vyvolat pro samotný příkaz `dotnet new` nebo pro libovolnou šablonu.</span><span class="sxs-lookup"><span data-stu-id="739d1-292">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="739d1-293">například `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="739d1-293">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="739d1-294">Nainstaluje balíček šablon z `PATH` nebo `NUGET_ID` poskytnutý.</span><span class="sxs-lookup"><span data-stu-id="739d1-294">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="739d1-295">Pokud chcete nainstalovat předprodejní verzi balíčku šablony, je nutné zadat verzi ve formátu `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="739d1-295">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="739d1-296">Ve výchozím nastavení `dotnet new` předá verze \*, která představuje nejnovější stabilní verzi balíčku.</span><span class="sxs-lookup"><span data-stu-id="739d1-296">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="739d1-297">Podívejte se na příklad v části [Příklady](#examples) .</span><span class="sxs-lookup"><span data-stu-id="739d1-297">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="739d1-298">Pokud byla verze šablony již nainstalována při spuštění tohoto příkazu, šablona bude aktualizována na určenou verzi nebo na nejnovější stabilní verzi, pokud nebyla zadána žádná verze.</span><span class="sxs-lookup"><span data-stu-id="739d1-298">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="739d1-299">Informace o vytváření vlastních šablon najdete v tématu [vlastní šablony pro dotnet New](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="739d1-299">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="739d1-300">Vypíše seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="739d1-300">Lists templates containing the specified name.</span></span> <span data-ttu-id="739d1-301">Pokud není zadán žádný název, vypíše všechny šablony.</span><span class="sxs-lookup"><span data-stu-id="739d1-301">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="739d1-302">Jazyk šablony, která se má vytvořit</span><span class="sxs-lookup"><span data-stu-id="739d1-302">The language of the template to create.</span></span> <span data-ttu-id="739d1-303">Přijatý jazyk se liší podle šablony (viz výchozí hodnoty v oddílu [argumenty](#arguments) ).</span><span class="sxs-lookup"><span data-stu-id="739d1-303">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="739d1-304">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="739d1-304">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="739d1-305">Některá prostředí interpretují `#` jako speciální znak.</span><span class="sxs-lookup"><span data-stu-id="739d1-305">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="739d1-306">V těchto případech uveďte hodnotu parametru Language v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="739d1-306">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="739d1-307">například `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="739d1-307">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="739d1-308">Název vytvořeného výstupu.</span><span class="sxs-lookup"><span data-stu-id="739d1-308">The name for the created output.</span></span> <span data-ttu-id="739d1-309">Pokud název nezadáte, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="739d1-309">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source`**

  <span data-ttu-id="739d1-310">Určuje zdroj NuGet, který se použije při instalaci.</span><span class="sxs-lookup"><span data-stu-id="739d1-310">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="739d1-311">K dispozici od verze .NET Core 2,1 SDK.</span><span class="sxs-lookup"><span data-stu-id="739d1-311">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="739d1-312">Umístění, do kterého se má vygenerovaný výstup umístit.</span><span class="sxs-lookup"><span data-stu-id="739d1-312">Location to place the generated output.</span></span> <span data-ttu-id="739d1-313">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="739d1-313">The default is the current directory.</span></span>

- **`--type`**

  <span data-ttu-id="739d1-314">Filtruje šablony založené na dostupných typech.</span><span class="sxs-lookup"><span data-stu-id="739d1-314">Filters templates based on available types.</span></span> <span data-ttu-id="739d1-315">Předdefinované hodnoty jsou "projekt", "položka" nebo "jiné".</span><span class="sxs-lookup"><span data-stu-id="739d1-315">Predefined values are "project", "item", or "other".</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="739d1-316">Odinstaluje balíček šablon na `PATH` nebo `NUGET_ID` poskytnutý.</span><span class="sxs-lookup"><span data-stu-id="739d1-316">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="739d1-317">Pokud není zadána hodnota `<PATH|NUGET_ID>`, zobrazí se všechny aktuálně nainstalované sady šablon a jejich přidružené šablony.</span><span class="sxs-lookup"><span data-stu-id="739d1-317">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="739d1-318">Při zadávání `NUGET_ID`nezahrnujte číslo verze.</span><span class="sxs-lookup"><span data-stu-id="739d1-318">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="739d1-319">Pokud neurčíte parametr této možnosti, příkaz zobrazí seznam nainstalovaných šablon a podrobností.</span><span class="sxs-lookup"><span data-stu-id="739d1-319">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="739d1-320">Chcete-li odinstalovat šablonu pomocí `PATH`, je nutné cestu plně kvalifikovat.</span><span class="sxs-lookup"><span data-stu-id="739d1-320">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="739d1-321">Například *C:/uživatelé/\<USER >/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* budou fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z nadřazené složky to nebude.</span><span class="sxs-lookup"><span data-stu-id="739d1-321">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="739d1-322">Do cesty k šabloně nezahrnujte konečné koncové lomítko adresáře.</span><span class="sxs-lookup"><span data-stu-id="739d1-322">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="739d1-323">Kontroluje, zda jsou k dispozici aktualizace pro sady šablon, které jsou aktuálně nainstalovány a instalovány.</span><span class="sxs-lookup"><span data-stu-id="739d1-323">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="739d1-324">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="739d1-324">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="739d1-325">Kontroluje, zda jsou k dispozici aktualizace pro sady šablon, které jsou aktuálně nainstalovány.</span><span class="sxs-lookup"><span data-stu-id="739d1-325">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="739d1-326">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="739d1-326">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="739d1-327">Možnosti šablony</span><span class="sxs-lookup"><span data-stu-id="739d1-327">Template options</span></span>

<span data-ttu-id="739d1-328">Každá šablona projektu může mít k dispozici další možnosti.</span><span class="sxs-lookup"><span data-stu-id="739d1-328">Each project template may have additional options available.</span></span> <span data-ttu-id="739d1-329">Základní šablony mají následující další možnosti:</span><span class="sxs-lookup"><span data-stu-id="739d1-329">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="739d1-330">konzola</span><span class="sxs-lookup"><span data-stu-id="739d1-330">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="739d1-331">Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="739d1-331">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="739d1-332">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="739d1-332">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="739d1-333">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, který používáte:</span><span class="sxs-lookup"><span data-stu-id="739d1-333">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="739d1-334">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="739d1-334">SDK version</span></span> | <span data-ttu-id="739d1-335">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="739d1-335">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="739d1-336">3.1</span><span class="sxs-lookup"><span data-stu-id="739d1-336">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="739d1-337">3.0</span><span class="sxs-lookup"><span data-stu-id="739d1-337">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="739d1-338">Nastaví vlastnost `LangVersion` v souboru vytvořeného projektu.</span><span class="sxs-lookup"><span data-stu-id="739d1-338">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="739d1-339">Například použijte `--langVersion 7.3` k použití C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="739d1-339">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="739d1-340">Nepodporuje se pro F#.</span><span class="sxs-lookup"><span data-stu-id="739d1-340">Not supported for F#.</span></span> <span data-ttu-id="739d1-341">K dispozici od verze .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="739d1-341">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="739d1-342">Seznam výchozích C# verzí najdete v tématu [výchozí](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="739d1-342">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="739d1-343">Je-li tento parametr zadán, nespustí při vytváření projektu implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="739d1-343">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="739d1-344">K dispozici od verze .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="739d1-344">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="739d1-345">že knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="739d1-345">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="739d1-346">Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="739d1-346">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="739d1-347">Hodnoty: `netcoreapp<version>` pro vytvoření knihovny tříd .NET Core nebo `netstandard<version>` k vytvoření knihovny tříd .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="739d1-347">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="739d1-348">Výchozí hodnota je `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="739d1-348">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="739d1-349">Nastaví vlastnost `LangVersion` v souboru vytvořeného projektu.</span><span class="sxs-lookup"><span data-stu-id="739d1-349">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="739d1-350">Například použijte `--langVersion 7.3` k použití C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="739d1-350">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="739d1-351">Nepodporuje se pro F#.</span><span class="sxs-lookup"><span data-stu-id="739d1-351">Not supported for F#.</span></span> <span data-ttu-id="739d1-352">K dispozici od verze .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="739d1-352">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="739d1-353">Seznam výchozích C# verzí najdete v tématu [výchozí](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="739d1-353">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="739d1-354">Při vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="739d1-354">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf"></a><span data-ttu-id="739d1-355">WPF, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="739d1-355">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="739d1-356">Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="739d1-356">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="739d1-357">Výchozí hodnota je `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="739d1-357">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="739d1-358">K dispozici od verze .NET Core 3,1 SDK.</span><span class="sxs-lookup"><span data-stu-id="739d1-358">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="739d1-359">Nastaví vlastnost `LangVersion` v souboru vytvořeného projektu.</span><span class="sxs-lookup"><span data-stu-id="739d1-359">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="739d1-360">Například použijte `--langVersion 7.3` k použití C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="739d1-360">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="739d1-361">Seznam výchozích C# verzí najdete v tématu [výchozí](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="739d1-361">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="739d1-362">Při vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="739d1-362">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms"></a><span data-ttu-id="739d1-363">WinForms, winformslib</span><span class="sxs-lookup"><span data-stu-id="739d1-363">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="739d1-364">Nastaví vlastnost `LangVersion` v souboru vytvořeného projektu.</span><span class="sxs-lookup"><span data-stu-id="739d1-364">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="739d1-365">Například použijte `--langVersion 7.3` k použití C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="739d1-365">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="739d1-366">Seznam výchozích C# verzí najdete v tématu [výchozí](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="739d1-366">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="739d1-367">Při vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="739d1-367">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web-others"></a><span data-ttu-id="739d1-368">pracovní proces, grpc</span><span class="sxs-lookup"><span data-stu-id="739d1-368">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="739d1-369">Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="739d1-369">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="739d1-370">Výchozí hodnota je `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="739d1-370">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="739d1-371">K dispozici od verze .NET Core 3,1 SDK.</span><span class="sxs-lookup"><span data-stu-id="739d1-371">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="739d1-372">Vyloučí z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="739d1-372">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="739d1-373">Při vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="739d1-373">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="test"></a><span data-ttu-id="739d1-374">MSTest, xUnit</span><span class="sxs-lookup"><span data-stu-id="739d1-374">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="739d1-375">Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="739d1-375">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="739d1-376">Možnost je k dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="739d1-376">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="739d1-377">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, který používáte:</span><span class="sxs-lookup"><span data-stu-id="739d1-377">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="739d1-378">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="739d1-378">SDK version</span></span> | <span data-ttu-id="739d1-379">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="739d1-379">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="739d1-380">3.1</span><span class="sxs-lookup"><span data-stu-id="739d1-380">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="739d1-381">3.0</span><span class="sxs-lookup"><span data-stu-id="739d1-381">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="739d1-382">Umožňuje sbalení pro projekt pomocí [sady dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="739d1-382">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="739d1-383">Při vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="739d1-383">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="739d1-384">nunit</span><span class="sxs-lookup"><span data-stu-id="739d1-384">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="739d1-385">Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="739d1-385">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="739d1-386">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, který používáte:</span><span class="sxs-lookup"><span data-stu-id="739d1-386">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="739d1-387">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="739d1-387">SDK version</span></span> | <span data-ttu-id="739d1-388">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="739d1-388">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="739d1-389">3.1</span><span class="sxs-lookup"><span data-stu-id="739d1-389">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="739d1-390">3.0</span><span class="sxs-lookup"><span data-stu-id="739d1-390">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="739d1-391">2.2</span><span class="sxs-lookup"><span data-stu-id="739d1-391">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="739d1-392">2.1</span><span class="sxs-lookup"><span data-stu-id="739d1-392">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="739d1-393">Umožňuje sbalení pro projekt pomocí [sady dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="739d1-393">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="739d1-394">Při vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="739d1-394">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="739d1-395">stránka</span><span class="sxs-lookup"><span data-stu-id="739d1-395">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="739d1-396">Obor názvů pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="739d1-396">Namespace for the generated code.</span></span> <span data-ttu-id="739d1-397">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="739d1-397">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="739d1-398">Vytvoří stránku bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="739d1-398">Creates the page without a PageModel.</span></span>

***

### <a name="namespace"></a><span data-ttu-id="739d1-399">viewimports, a proto</span><span class="sxs-lookup"><span data-stu-id="739d1-399">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="739d1-400">Obor názvů pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="739d1-400">Namespace for the generated code.</span></span> <span data-ttu-id="739d1-401">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="739d1-401">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="739d1-402">blazorserver</span><span class="sxs-lookup"><span data-stu-id="739d1-402">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="739d1-403">Typ ověřování, který má být použit.</span><span class="sxs-lookup"><span data-stu-id="739d1-403">The type of authentication to use.</span></span> <span data-ttu-id="739d1-404">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="739d1-404">The possible values are:</span></span>

  - <span data-ttu-id="739d1-405">`None` – bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="739d1-405">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="739d1-406">`Individual` – individuální ověřování.</span><span class="sxs-lookup"><span data-stu-id="739d1-406">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="739d1-407">`IndividualB2C` – individuální ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="739d1-407">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="739d1-408">`SingleOrg` – ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="739d1-408">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="739d1-409">`MultiOrg` – ověřování organizace pro více tenantů.</span><span class="sxs-lookup"><span data-stu-id="739d1-409">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="739d1-410">`Windows` – ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="739d1-410">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="739d1-411">Instance Azure Active Directory B2C pro připojení.</span><span class="sxs-lookup"><span data-stu-id="739d1-411">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="739d1-412">Použijte s ověřováním `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="739d1-412">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="739d1-413">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="739d1-413">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="739d1-414">ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="739d1-414">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="739d1-415">Použijte s ověřováním `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="739d1-415">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="739d1-416">ID zásad pro resetování hesla pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="739d1-416">The reset password policy ID for this project.</span></span> <span data-ttu-id="739d1-417">Použijte s ověřováním `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="739d1-417">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="739d1-418">Upravit ID zásad profilu pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="739d1-418">The edit profile policy ID for this project.</span></span> <span data-ttu-id="739d1-419">Použijte s ověřováním `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="739d1-419">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="739d1-420">Instance Azure Active Directory pro připojení.</span><span class="sxs-lookup"><span data-stu-id="739d1-420">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="739d1-421">Použijte s ověřováním `SingleOrg` nebo `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="739d1-421">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="739d1-422">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="739d1-422">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="739d1-423">ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="739d1-423">The Client ID for this project.</span></span> <span data-ttu-id="739d1-424">Použijte s ověřováním `IndividualB2C`, `SingleOrg`nebo `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="739d1-424">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="739d1-425">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="739d1-425">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="739d1-426">Doména pro tenanta adresáře.</span><span class="sxs-lookup"><span data-stu-id="739d1-426">The domain for the directory tenant.</span></span> <span data-ttu-id="739d1-427">Použijte s ověřováním `SingleOrg` nebo `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="739d1-427">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="739d1-428">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="739d1-428">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="739d1-429">ID TenantId adresáře, ke kterému se má připojit.</span><span class="sxs-lookup"><span data-stu-id="739d1-429">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="739d1-430">Použijte s ověřováním `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="739d1-430">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="739d1-431">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="739d1-431">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="739d1-432">Cesta požadavku v základní cestě identifikátoru URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="739d1-432">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="739d1-433">Použijte s ověřováním `SingleOrg` nebo `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="739d1-433">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="739d1-434">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="739d1-434">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="739d1-435">Povolí této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="739d1-435">Allows this application read-access to the directory.</span></span> <span data-ttu-id="739d1-436">Platí jenom pro ověřování `SingleOrg` nebo `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="739d1-436">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="739d1-437">Vyloučí z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="739d1-437">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="739d1-438">Vypne protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="739d1-438">Turns off HTTPS.</span></span> <span data-ttu-id="739d1-439">Tato možnost se použije jenom v případě, že se pro `--auth`nepoužívají `Individual`, `IndividualB2C`, `SingleOrg`nebo `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="739d1-439">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="739d1-440">Určuje, že se má místo SQLite použít LocalDB.</span><span class="sxs-lookup"><span data-stu-id="739d1-440">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="739d1-441">Platí jenom pro ověřování `Individual` nebo `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="739d1-441">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="739d1-442">Při vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="739d1-442">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="739d1-443">web</span><span class="sxs-lookup"><span data-stu-id="739d1-443">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="739d1-444">Vyloučí z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="739d1-444">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="739d1-445">Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="739d1-445">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="739d1-446">Možnost není dostupná v sadě .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="739d1-446">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="739d1-447">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, který používáte:</span><span class="sxs-lookup"><span data-stu-id="739d1-447">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="739d1-448">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="739d1-448">SDK version</span></span> | <span data-ttu-id="739d1-449">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="739d1-449">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="739d1-450">3.1</span><span class="sxs-lookup"><span data-stu-id="739d1-450">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="739d1-451">3.0</span><span class="sxs-lookup"><span data-stu-id="739d1-451">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="739d1-452">2.1</span><span class="sxs-lookup"><span data-stu-id="739d1-452">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="739d1-453">Při vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="739d1-453">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="739d1-454">Vypne protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="739d1-454">Turns off HTTPS.</span></span>

***

### <a name="web-options"></a><span data-ttu-id="739d1-455">MVC, WebApp</span><span class="sxs-lookup"><span data-stu-id="739d1-455">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="739d1-456">Typ ověřování, který má být použit.</span><span class="sxs-lookup"><span data-stu-id="739d1-456">The type of authentication to use.</span></span> <span data-ttu-id="739d1-457">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="739d1-457">The possible values are:</span></span>

  - <span data-ttu-id="739d1-458">`None` – bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="739d1-458">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="739d1-459">`Individual` – individuální ověřování.</span><span class="sxs-lookup"><span data-stu-id="739d1-459">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="739d1-460">`IndividualB2C` – individuální ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="739d1-460">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="739d1-461">`SingleOrg` – ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="739d1-461">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="739d1-462">`MultiOrg` – ověřování organizace pro více tenantů.</span><span class="sxs-lookup"><span data-stu-id="739d1-462">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="739d1-463">`Windows` – ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="739d1-463">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="739d1-464">Instance Azure Active Directory B2C pro připojení.</span><span class="sxs-lookup"><span data-stu-id="739d1-464">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="739d1-465">Použijte s ověřováním `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="739d1-465">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="739d1-466">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="739d1-466">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="739d1-467">ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="739d1-467">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="739d1-468">Použijte s ověřováním `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="739d1-468">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="739d1-469">ID zásad pro resetování hesla pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="739d1-469">The reset password policy ID for this project.</span></span> <span data-ttu-id="739d1-470">Použijte s ověřováním `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="739d1-470">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="739d1-471">Upravit ID zásad profilu pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="739d1-471">The edit profile policy ID for this project.</span></span> <span data-ttu-id="739d1-472">Použijte s ověřováním `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="739d1-472">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="739d1-473">Instance Azure Active Directory pro připojení.</span><span class="sxs-lookup"><span data-stu-id="739d1-473">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="739d1-474">Použijte s ověřováním `SingleOrg` nebo `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="739d1-474">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="739d1-475">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="739d1-475">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="739d1-476">ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="739d1-476">The Client ID for this project.</span></span> <span data-ttu-id="739d1-477">Použijte s ověřováním `IndividualB2C`, `SingleOrg`nebo `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="739d1-477">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="739d1-478">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="739d1-478">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="739d1-479">Doména pro tenanta adresáře.</span><span class="sxs-lookup"><span data-stu-id="739d1-479">The domain for the directory tenant.</span></span> <span data-ttu-id="739d1-480">Použijte s ověřováním `SingleOrg` nebo `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="739d1-480">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="739d1-481">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="739d1-481">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="739d1-482">ID TenantId adresáře, ke kterému se má připojit.</span><span class="sxs-lookup"><span data-stu-id="739d1-482">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="739d1-483">Použijte s ověřováním `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="739d1-483">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="739d1-484">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="739d1-484">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="739d1-485">Cesta požadavku v základní cestě identifikátoru URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="739d1-485">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="739d1-486">Použijte s ověřováním `SingleOrg` nebo `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="739d1-486">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="739d1-487">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="739d1-487">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="739d1-488">Povolí této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="739d1-488">Allows this application read-access to the directory.</span></span> <span data-ttu-id="739d1-489">Platí jenom pro ověřování `SingleOrg` nebo `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="739d1-489">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="739d1-490">Vyloučí z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="739d1-490">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="739d1-491">Vypne protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="739d1-491">Turns off HTTPS.</span></span> <span data-ttu-id="739d1-492">Tato možnost se vztahuje jenom v případě, že se nepoužívají `Individual`, `IndividualB2C`, `SingleOrg`nebo `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="739d1-492">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="739d1-493">Určuje, že se má místo SQLite použít LocalDB.</span><span class="sxs-lookup"><span data-stu-id="739d1-493">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="739d1-494">Platí jenom pro ověřování `Individual` nebo `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="739d1-494">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="739d1-495">Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="739d1-495">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="739d1-496">Možnost je k dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="739d1-496">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="739d1-497">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, který používáte:</span><span class="sxs-lookup"><span data-stu-id="739d1-497">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="739d1-498">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="739d1-498">SDK version</span></span> | <span data-ttu-id="739d1-499">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="739d1-499">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="739d1-500">3.1</span><span class="sxs-lookup"><span data-stu-id="739d1-500">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="739d1-501">3.0</span><span class="sxs-lookup"><span data-stu-id="739d1-501">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="739d1-502">Při vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="739d1-502">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="739d1-503">Zahrnuje BrowserLink do projektu.</span><span class="sxs-lookup"><span data-stu-id="739d1-503">Includes BrowserLink in the project.</span></span> <span data-ttu-id="739d1-504">V rozhraní .NET Core 2,2 a 3,1 SDK není dostupná možnost.</span><span class="sxs-lookup"><span data-stu-id="739d1-504">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

***

### <a name="spa"></a><span data-ttu-id="739d1-505">Úhlová, reakce</span><span class="sxs-lookup"><span data-stu-id="739d1-505">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="739d1-506">Typ ověřování, který má být použit.</span><span class="sxs-lookup"><span data-stu-id="739d1-506">The type of authentication to use.</span></span> <span data-ttu-id="739d1-507">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="739d1-507">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="739d1-508">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="739d1-508">The possible values are:</span></span>

  - <span data-ttu-id="739d1-509">`None` – bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="739d1-509">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="739d1-510">`Individual` – individuální ověřování.</span><span class="sxs-lookup"><span data-stu-id="739d1-510">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="739d1-511">Vyloučí z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="739d1-511">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="739d1-512">Při vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="739d1-512">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="739d1-513">Vypne protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="739d1-513">Turns off HTTPS.</span></span> <span data-ttu-id="739d1-514">Tato možnost se vztahuje pouze v případě, že je ověřování `None`.</span><span class="sxs-lookup"><span data-stu-id="739d1-514">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="739d1-515">Určuje, že se má místo SQLite použít LocalDB.</span><span class="sxs-lookup"><span data-stu-id="739d1-515">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="739d1-516">Platí jenom pro ověřování `Individual` nebo `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="739d1-516">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="739d1-517">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="739d1-517">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="739d1-518">Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="739d1-518">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="739d1-519">Možnost není dostupná v sadě .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="739d1-519">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="739d1-520">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, který používáte:</span><span class="sxs-lookup"><span data-stu-id="739d1-520">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="739d1-521">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="739d1-521">SDK version</span></span> | <span data-ttu-id="739d1-522">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="739d1-522">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="739d1-523">3.1</span><span class="sxs-lookup"><span data-stu-id="739d1-523">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="739d1-524">3.0</span><span class="sxs-lookup"><span data-stu-id="739d1-524">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="739d1-525">2.1</span><span class="sxs-lookup"><span data-stu-id="739d1-525">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="739d1-526">reactredux</span><span class="sxs-lookup"><span data-stu-id="739d1-526">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="739d1-527">Vyloučí z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="739d1-527">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="739d1-528">Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="739d1-528">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="739d1-529">Možnost není dostupná v sadě .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="739d1-529">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="739d1-530">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, který používáte:</span><span class="sxs-lookup"><span data-stu-id="739d1-530">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="739d1-531">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="739d1-531">SDK version</span></span> | <span data-ttu-id="739d1-532">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="739d1-532">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="739d1-533">3.1</span><span class="sxs-lookup"><span data-stu-id="739d1-533">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="739d1-534">3.0</span><span class="sxs-lookup"><span data-stu-id="739d1-534">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="739d1-535">2.1</span><span class="sxs-lookup"><span data-stu-id="739d1-535">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="739d1-536">Při vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="739d1-536">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="739d1-537">Vypne protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="739d1-537">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="739d1-538">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="739d1-538">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="739d1-539">Při vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="739d1-539">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="739d1-540">Podporuje kromě součástí do této knihovny i tradiční zobrazení a stránky Razor.</span><span class="sxs-lookup"><span data-stu-id="739d1-540">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="739d1-541">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="739d1-541">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="739d1-542">WebApi</span><span class="sxs-lookup"><span data-stu-id="739d1-542">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="739d1-543">Typ ověřování, který má být použit.</span><span class="sxs-lookup"><span data-stu-id="739d1-543">The type of authentication to use.</span></span> <span data-ttu-id="739d1-544">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="739d1-544">The possible values are:</span></span>

  - <span data-ttu-id="739d1-545">`None` – bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="739d1-545">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="739d1-546">`IndividualB2C` – individuální ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="739d1-546">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="739d1-547">`SingleOrg` – ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="739d1-547">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="739d1-548">`Windows` – ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="739d1-548">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="739d1-549">Instance Azure Active Directory B2C pro připojení.</span><span class="sxs-lookup"><span data-stu-id="739d1-549">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="739d1-550">Použijte s ověřováním `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="739d1-550">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="739d1-551">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="739d1-551">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="739d1-552">ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="739d1-552">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="739d1-553">Použijte s ověřováním `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="739d1-553">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="739d1-554">Instance Azure Active Directory pro připojení.</span><span class="sxs-lookup"><span data-stu-id="739d1-554">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="739d1-555">Použijte s ověřováním `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="739d1-555">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="739d1-556">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="739d1-556">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="739d1-557">ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="739d1-557">The Client ID for this project.</span></span> <span data-ttu-id="739d1-558">Použijte s ověřováním `IndividualB2C` nebo `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="739d1-558">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="739d1-559">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="739d1-559">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="739d1-560">Doména pro tenanta adresáře.</span><span class="sxs-lookup"><span data-stu-id="739d1-560">The domain for the directory tenant.</span></span> <span data-ttu-id="739d1-561">Použijte s ověřováním `IndividualB2C` nebo `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="739d1-561">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="739d1-562">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="739d1-562">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="739d1-563">ID TenantId adresáře, ke kterému se má připojit.</span><span class="sxs-lookup"><span data-stu-id="739d1-563">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="739d1-564">Použijte s ověřováním `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="739d1-564">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="739d1-565">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="739d1-565">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="739d1-566">Povolí této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="739d1-566">Allows this application read-access to the directory.</span></span> <span data-ttu-id="739d1-567">Platí jenom pro ověřování `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="739d1-567">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="739d1-568">Vyloučí z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="739d1-568">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="739d1-569">Vypne protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="739d1-569">Turns off HTTPS.</span></span> <span data-ttu-id="739d1-570">`app.UseHsts` a `app.UseHttpsRedirection` nejsou přidány do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="739d1-570">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="739d1-571">Tato možnost platí pouze v případě, že se pro ověřování nepoužívá `IndividualB2C` nebo `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="739d1-571">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="739d1-572">Určuje, že se má místo SQLite použít LocalDB.</span><span class="sxs-lookup"><span data-stu-id="739d1-572">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="739d1-573">Platí jenom pro ověřování `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="739d1-573">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="739d1-574">Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="739d1-574">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="739d1-575">Možnost není dostupná v sadě .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="739d1-575">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="739d1-576">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, který používáte:</span><span class="sxs-lookup"><span data-stu-id="739d1-576">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="739d1-577">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="739d1-577">SDK version</span></span> | <span data-ttu-id="739d1-578">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="739d1-578">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="739d1-579">3.1</span><span class="sxs-lookup"><span data-stu-id="739d1-579">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="739d1-580">3.0</span><span class="sxs-lookup"><span data-stu-id="739d1-580">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="739d1-581">2.1</span><span class="sxs-lookup"><span data-stu-id="739d1-581">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="739d1-582">Při vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="739d1-582">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="739d1-583">globaljson</span><span class="sxs-lookup"><span data-stu-id="739d1-583">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="739d1-584">Určuje verzi .NET Core SDK, která se má použít v souboru *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="739d1-584">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="739d1-585">Příklady</span><span class="sxs-lookup"><span data-stu-id="739d1-585">Examples</span></span>

- <span data-ttu-id="739d1-586">Vytvořte projekt C# konzolové aplikace zadáním názvu šablony:</span><span class="sxs-lookup"><span data-stu-id="739d1-586">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="739d1-587">Vytvořte projekt F# konzolové aplikace v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="739d1-587">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang F#
  ```

- <span data-ttu-id="739d1-588">Vytvořte .NET Standard projekt knihovny tříd v zadaném adresáři:</span><span class="sxs-lookup"><span data-stu-id="739d1-588">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="739d1-589">Vytvoří nový projekt ASP.NET Core C# MVC v aktuálním adresáři bez ověřování:</span><span class="sxs-lookup"><span data-stu-id="739d1-589">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="739d1-590">Vytvořit nový projekt xUnit:</span><span class="sxs-lookup"><span data-stu-id="739d1-590">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="739d1-591">Vypíše všechny šablony, které jsou k dispozici pro šablony jednostránkové aplikace (SPA):</span><span class="sxs-lookup"><span data-stu-id="739d1-591">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="739d1-592">Vypíše všechny šablony, které odpovídají podřetězci *My* .</span><span class="sxs-lookup"><span data-stu-id="739d1-592">List all templates matching the *we* substring.</span></span> <span data-ttu-id="739d1-593">Nebyla nalezena žádná přesná shoda, takže porovnávání dílčích řetězců se shoduje se sloupci krátkého názvu a názvu.</span><span class="sxs-lookup"><span data-stu-id="739d1-593">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="739d1-594">Došlo k pokusu o vyvolání šablony, která odpovídá *NG*.</span><span class="sxs-lookup"><span data-stu-id="739d1-594">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="739d1-595">Pokud nelze určit jednu shodu, Seznamte se se šablonami, které jsou částečné shody.</span><span class="sxs-lookup"><span data-stu-id="739d1-595">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="739d1-596">Nainstalujte verzi 2,0 šablon SPA pro ASP.NET Core:</span><span class="sxs-lookup"><span data-stu-id="739d1-596">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="739d1-597">Seznam nainstalovaných šablon a podrobností, včetně jejich odinstalace:</span><span class="sxs-lookup"><span data-stu-id="739d1-597">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="739d1-598">V aktuálním adresáři vytvořte *Global. JSON* s nastavením verze sady SDK na 3.1.101:</span><span class="sxs-lookup"><span data-stu-id="739d1-598">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="739d1-599">Viz také</span><span class="sxs-lookup"><span data-stu-id="739d1-599">See also</span></span>

- [<span data-ttu-id="739d1-600">Vlastní šablony pro dotnet New</span><span class="sxs-lookup"><span data-stu-id="739d1-600">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="739d1-601">Vytvoření vlastní šablony pro dotnet new</span><span class="sxs-lookup"><span data-stu-id="739d1-601">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="739d1-602">dotnet/dotnet-Template-Samples – úložiště GitHub</span><span class="sxs-lookup"><span data-stu-id="739d1-602">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="739d1-603">Dostupné šablony pro dotnet New</span><span class="sxs-lookup"><span data-stu-id="739d1-603">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
