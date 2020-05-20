---
title: dotnet – nový příkaz
description: Příkaz dotnet New vytvoří nové projekty .NET Core založené na zadané šabloně.
ms.date: 04/10/2020
ms.openlocfilehash: 1544f519f2a5f6a1a6e042c1db720eff45f5d98c
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442238"
---
# <a name="dotnet-new"></a><span data-ttu-id="ffc31-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="ffc31-103">dotnet new</span></span>

<span data-ttu-id="ffc31-104">**Tento článek se týká:** ✔️ .net Core 2,0 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="ffc31-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="ffc31-105">Name</span><span class="sxs-lookup"><span data-stu-id="ffc31-105">Name</span></span>

<span data-ttu-id="ffc31-106">`dotnet new`– Vytvoří nový projekt, konfigurační soubor nebo řešení na základě zadané šablony.</span><span class="sxs-lookup"><span data-stu-id="ffc31-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ffc31-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="ffc31-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {"C#"|"F#"|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="ffc31-108">Popis</span><span class="sxs-lookup"><span data-stu-id="ffc31-108">Description</span></span>

<span data-ttu-id="ffc31-109">`dotnet new`Příkaz vytvoří projekt .NET Core nebo jiné artefakty založené na šabloně.</span><span class="sxs-lookup"><span data-stu-id="ffc31-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="ffc31-110">Příkaz volá [modul šablony](https://github.com/dotnet/templating) a vytvoří artefakty na disku na základě zadané šablony a možností.</span><span class="sxs-lookup"><span data-stu-id="ffc31-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="ffc31-111">Implicitní obnovení</span><span class="sxs-lookup"><span data-stu-id="ffc31-111">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="ffc31-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="ffc31-112">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="ffc31-113">Šablona, která se má vytvořit při vyvolání příkazu</span><span class="sxs-lookup"><span data-stu-id="ffc31-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="ffc31-114">Každá šablona může mít konkrétní možnosti, které můžete předat.</span><span class="sxs-lookup"><span data-stu-id="ffc31-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="ffc31-115">Další informace najdete v tématu [Možnosti šablony](#template-options).</span><span class="sxs-lookup"><span data-stu-id="ffc31-115">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="ffc31-116">Můžete spustit `dotnet new --list` nebo `dotnet new -l` a zobrazit seznam všech nainstalovaných šablon.</span><span class="sxs-lookup"><span data-stu-id="ffc31-116">You can run `dotnet new --list` or `dotnet new -l` to see a list of all installed templates.</span></span> <span data-ttu-id="ffc31-117">Pokud `TEMPLATE` hodnota není přesná shoda na textu v **šablonách** nebo ve sloupci **krátký název** z vrácené tabulky, provede se shoda podřetězce na těchto dvou sloupcích.</span><span class="sxs-lookup"><span data-stu-id="ffc31-117">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="ffc31-118">Počínaje verzí .NET Core 3,0 SDK vyhledává CLI šablony v NuGet.org při vyvolání `dotnet new` příkazu v následujících podmínkách:</span><span class="sxs-lookup"><span data-stu-id="ffc31-118">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="ffc31-119">Pokud rozhraní příkazového řádku nenalezne při vyvolání odpovídající šablonu `dotnet new` , která není ani částečná.</span><span class="sxs-lookup"><span data-stu-id="ffc31-119">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="ffc31-120">Pokud je k dispozici novější verze šablony.</span><span class="sxs-lookup"><span data-stu-id="ffc31-120">If there's a newer version of the template available.</span></span> <span data-ttu-id="ffc31-121">V tomto případě se vytvoří projekt nebo artefakt, ale rozhraní příkazového řádku vás upozorní na aktualizovanou verzi šablony.</span><span class="sxs-lookup"><span data-stu-id="ffc31-121">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="ffc31-122">Následující tabulka obsahuje šablony, které jsou předinstalované s .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="ffc31-122">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="ffc31-123">Výchozí jazyk pro šablonu se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="ffc31-123">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="ffc31-124">Kliknutím na odkaz krátké jméno zobrazíte konkrétní možnosti šablony.</span><span class="sxs-lookup"><span data-stu-id="ffc31-124">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="ffc31-125">Šablony</span><span class="sxs-lookup"><span data-stu-id="ffc31-125">Templates</span></span>                                    | <span data-ttu-id="ffc31-126">Krátký název</span><span class="sxs-lookup"><span data-stu-id="ffc31-126">Short name</span></span>                      | <span data-ttu-id="ffc31-127">Jazyk</span><span class="sxs-lookup"><span data-stu-id="ffc31-127">Language</span></span>     | <span data-ttu-id="ffc31-128">Značky</span><span class="sxs-lookup"><span data-stu-id="ffc31-128">Tags</span></span>                                  | <span data-ttu-id="ffc31-129">Vedou</span><span class="sxs-lookup"><span data-stu-id="ffc31-129">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="ffc31-130">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="ffc31-130">Console Application</span></span>                          | [<span data-ttu-id="ffc31-131">stromu</span><span class="sxs-lookup"><span data-stu-id="ffc31-131">console</span></span>](#console)             | <span data-ttu-id="ffc31-132">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="ffc31-132">[C#], F#, VB</span></span> | <span data-ttu-id="ffc31-133">Společná/konzola</span><span class="sxs-lookup"><span data-stu-id="ffc31-133">Common/Console</span></span>                        | <span data-ttu-id="ffc31-134">1.0</span><span class="sxs-lookup"><span data-stu-id="ffc31-134">1.0</span></span>        |
| <span data-ttu-id="ffc31-135">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="ffc31-135">Class library</span></span>                                | [<span data-ttu-id="ffc31-136">že knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="ffc31-136">classlib</span></span>](#classlib)           | <span data-ttu-id="ffc31-137">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="ffc31-137">[C#], F#, VB</span></span> | <span data-ttu-id="ffc31-138">Společné/knihovny</span><span class="sxs-lookup"><span data-stu-id="ffc31-138">Common/Library</span></span>                        | <span data-ttu-id="ffc31-139">1.0</span><span class="sxs-lookup"><span data-stu-id="ffc31-139">1.0</span></span>        |
| <span data-ttu-id="ffc31-140">Aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="ffc31-140">WPF Application</span></span>                              | [<span data-ttu-id="ffc31-141">subsystém</span><span class="sxs-lookup"><span data-stu-id="ffc31-141">wpf</span></span>](#wpf)                     | <span data-ttu-id="ffc31-142">Jazyk</span><span class="sxs-lookup"><span data-stu-id="ffc31-142">[C#]</span></span>         | <span data-ttu-id="ffc31-143">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="ffc31-143">Common/WPF</span></span>                            | <span data-ttu-id="ffc31-144">3.0</span><span class="sxs-lookup"><span data-stu-id="ffc31-144">3.0</span></span>        |
| <span data-ttu-id="ffc31-145">WPF – knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="ffc31-145">WPF Class library</span></span>                            | [<span data-ttu-id="ffc31-146">wpflib</span><span class="sxs-lookup"><span data-stu-id="ffc31-146">wpflib</span></span>](#wpf)                  | <span data-ttu-id="ffc31-147">Jazyk</span><span class="sxs-lookup"><span data-stu-id="ffc31-147">[C#]</span></span>         | <span data-ttu-id="ffc31-148">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="ffc31-148">Common/WPF</span></span>                            | <span data-ttu-id="ffc31-149">3.0</span><span class="sxs-lookup"><span data-stu-id="ffc31-149">3.0</span></span>        |
| <span data-ttu-id="ffc31-150">Knihovna vlastních ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="ffc31-150">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="ffc31-151">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="ffc31-151">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="ffc31-152">Jazyk</span><span class="sxs-lookup"><span data-stu-id="ffc31-152">[C#]</span></span>         | <span data-ttu-id="ffc31-153">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="ffc31-153">Common/WPF</span></span>                            | <span data-ttu-id="ffc31-154">3.0</span><span class="sxs-lookup"><span data-stu-id="ffc31-154">3.0</span></span>        |
| <span data-ttu-id="ffc31-155">Knihovna uživatelských ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="ffc31-155">WPF User Control Library</span></span>                     | [<span data-ttu-id="ffc31-156">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="ffc31-156">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="ffc31-157">Jazyk</span><span class="sxs-lookup"><span data-stu-id="ffc31-157">[C#]</span></span>         | <span data-ttu-id="ffc31-158">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="ffc31-158">Common/WPF</span></span>                            | <span data-ttu-id="ffc31-159">3.0</span><span class="sxs-lookup"><span data-stu-id="ffc31-159">3.0</span></span>        |
| <span data-ttu-id="ffc31-160">Aplikace model Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="ffc31-160">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="ffc31-161">WinForms</span><span class="sxs-lookup"><span data-stu-id="ffc31-161">winforms</span></span>](#winforms)           | <span data-ttu-id="ffc31-162">Jazyk</span><span class="sxs-lookup"><span data-stu-id="ffc31-162">[C#]</span></span>         | <span data-ttu-id="ffc31-163">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="ffc31-163">Common/WinForms</span></span>                       | <span data-ttu-id="ffc31-164">3.0</span><span class="sxs-lookup"><span data-stu-id="ffc31-164">3.0</span></span>        |
| <span data-ttu-id="ffc31-165">Knihovna tříd model Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="ffc31-165">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="ffc31-166">winformslib</span><span class="sxs-lookup"><span data-stu-id="ffc31-166">winformslib</span></span>](#winforms)        | <span data-ttu-id="ffc31-167">Jazyk</span><span class="sxs-lookup"><span data-stu-id="ffc31-167">[C#]</span></span>         | <span data-ttu-id="ffc31-168">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="ffc31-168">Common/WinForms</span></span>                       | <span data-ttu-id="ffc31-169">3.0</span><span class="sxs-lookup"><span data-stu-id="ffc31-169">3.0</span></span>        |
| <span data-ttu-id="ffc31-170">Služba pracovního procesu</span><span class="sxs-lookup"><span data-stu-id="ffc31-170">Worker Service</span></span>                               | [<span data-ttu-id="ffc31-171">zaměstnanec</span><span class="sxs-lookup"><span data-stu-id="ffc31-171">worker</span></span>](#web-others)           | <span data-ttu-id="ffc31-172">Jazyk</span><span class="sxs-lookup"><span data-stu-id="ffc31-172">[C#]</span></span>         | <span data-ttu-id="ffc31-173">Common/Work/Web</span><span class="sxs-lookup"><span data-stu-id="ffc31-173">Common/Worker/Web</span></span>                     | <span data-ttu-id="ffc31-174">3.0</span><span class="sxs-lookup"><span data-stu-id="ffc31-174">3.0</span></span>        |
| <span data-ttu-id="ffc31-175">Projekt testu jednotek</span><span class="sxs-lookup"><span data-stu-id="ffc31-175">Unit Test Project</span></span>                            | [<span data-ttu-id="ffc31-176">MSTest</span><span class="sxs-lookup"><span data-stu-id="ffc31-176">mstest</span></span>](#test)                 | <span data-ttu-id="ffc31-177">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="ffc31-177">[C#], F#, VB</span></span> | <span data-ttu-id="ffc31-178">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="ffc31-178">Test/MSTest</span></span>                           | <span data-ttu-id="ffc31-179">1.0</span><span class="sxs-lookup"><span data-stu-id="ffc31-179">1.0</span></span>        |
| <span data-ttu-id="ffc31-180">Projekt testů NUnit 3</span><span class="sxs-lookup"><span data-stu-id="ffc31-180">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="ffc31-181">nunit</span><span class="sxs-lookup"><span data-stu-id="ffc31-181">nunit</span></span>](#nunit)                  | <span data-ttu-id="ffc31-182">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="ffc31-182">[C#], F#, VB</span></span> | <span data-ttu-id="ffc31-183">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="ffc31-183">Test/NUnit</span></span>                            | <span data-ttu-id="ffc31-184">2.1.400</span><span class="sxs-lookup"><span data-stu-id="ffc31-184">2.1.400</span></span>    |
| <span data-ttu-id="ffc31-185">NUnit 3 položka testu</span><span class="sxs-lookup"><span data-stu-id="ffc31-185">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="ffc31-186">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="ffc31-186">[C#], F#, VB</span></span> | <span data-ttu-id="ffc31-187">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="ffc31-187">Test/NUnit</span></span>                            | <span data-ttu-id="ffc31-188">2,2</span><span class="sxs-lookup"><span data-stu-id="ffc31-188">2.2</span></span>        |
| <span data-ttu-id="ffc31-189">Projekt testů xUnit</span><span class="sxs-lookup"><span data-stu-id="ffc31-189">xUnit Test Project</span></span>                           | [<span data-ttu-id="ffc31-190">xUnit</span><span class="sxs-lookup"><span data-stu-id="ffc31-190">xunit</span></span>](#test)                  | <span data-ttu-id="ffc31-191">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="ffc31-191">[C#], F#, VB</span></span> | <span data-ttu-id="ffc31-192">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="ffc31-192">Test/xUnit</span></span>                            | <span data-ttu-id="ffc31-193">1.0</span><span class="sxs-lookup"><span data-stu-id="ffc31-193">1.0</span></span>        |
| <span data-ttu-id="ffc31-194">Komponenta Razor</span><span class="sxs-lookup"><span data-stu-id="ffc31-194">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="ffc31-195">Jazyk</span><span class="sxs-lookup"><span data-stu-id="ffc31-195">[C#]</span></span>         | <span data-ttu-id="ffc31-196">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="ffc31-196">Web/ASP.NET</span></span>                           | <span data-ttu-id="ffc31-197">3.0</span><span class="sxs-lookup"><span data-stu-id="ffc31-197">3.0</span></span>        |
| <span data-ttu-id="ffc31-198">Stránka Razor</span><span class="sxs-lookup"><span data-stu-id="ffc31-198">Razor Page</span></span>                                   | [<span data-ttu-id="ffc31-199">Page</span><span class="sxs-lookup"><span data-stu-id="ffc31-199">page</span></span>](#page)                   | <span data-ttu-id="ffc31-200">Jazyk</span><span class="sxs-lookup"><span data-stu-id="ffc31-200">[C#]</span></span>         | <span data-ttu-id="ffc31-201">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="ffc31-201">Web/ASP.NET</span></span>                           | <span data-ttu-id="ffc31-202">2.0</span><span class="sxs-lookup"><span data-stu-id="ffc31-202">2.0</span></span>        |
| <span data-ttu-id="ffc31-203">ViewImports MVC</span><span class="sxs-lookup"><span data-stu-id="ffc31-203">MVC ViewImports</span></span>                              | [<span data-ttu-id="ffc31-204">viewimports</span><span class="sxs-lookup"><span data-stu-id="ffc31-204">viewimports</span></span>](#namespace)       | <span data-ttu-id="ffc31-205">Jazyk</span><span class="sxs-lookup"><span data-stu-id="ffc31-205">[C#]</span></span>         | <span data-ttu-id="ffc31-206">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="ffc31-206">Web/ASP.NET</span></span>                           | <span data-ttu-id="ffc31-207">2.0</span><span class="sxs-lookup"><span data-stu-id="ffc31-207">2.0</span></span>        |
| <span data-ttu-id="ffc31-208">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="ffc31-208">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="ffc31-209">Jazyk</span><span class="sxs-lookup"><span data-stu-id="ffc31-209">[C#]</span></span>         | <span data-ttu-id="ffc31-210">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="ffc31-210">Web/ASP.NET</span></span>                           | <span data-ttu-id="ffc31-211">2.0</span><span class="sxs-lookup"><span data-stu-id="ffc31-211">2.0</span></span>        |
| <span data-ttu-id="ffc31-212">Aplikace serveru Blazor</span><span class="sxs-lookup"><span data-stu-id="ffc31-212">Blazor Server App</span></span>                            | [<span data-ttu-id="ffc31-213">blazorserver</span><span class="sxs-lookup"><span data-stu-id="ffc31-213">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="ffc31-214">Jazyk</span><span class="sxs-lookup"><span data-stu-id="ffc31-214">[C#]</span></span>         | <span data-ttu-id="ffc31-215">Web/Blazor</span><span class="sxs-lookup"><span data-stu-id="ffc31-215">Web/Blazor</span></span>                            | <span data-ttu-id="ffc31-216">3.0</span><span class="sxs-lookup"><span data-stu-id="ffc31-216">3.0</span></span>        |
| <span data-ttu-id="ffc31-217">ASP.NET Core prázdné</span><span class="sxs-lookup"><span data-stu-id="ffc31-217">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="ffc31-218">webovém</span><span class="sxs-lookup"><span data-stu-id="ffc31-218">web</span></span>](#web)                     | <span data-ttu-id="ffc31-219">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="ffc31-219">[C#], F#</span></span>     | <span data-ttu-id="ffc31-220">Web/prázdné</span><span class="sxs-lookup"><span data-stu-id="ffc31-220">Web/Empty</span></span>                             | <span data-ttu-id="ffc31-221">1.0</span><span class="sxs-lookup"><span data-stu-id="ffc31-221">1.0</span></span>        |
| <span data-ttu-id="ffc31-222">ASP.NET Core webová aplikace (model-zobrazení-kontroler)</span><span class="sxs-lookup"><span data-stu-id="ffc31-222">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="ffc31-223">Návrhový</span><span class="sxs-lookup"><span data-stu-id="ffc31-223">mvc</span></span>](#web-options)             | <span data-ttu-id="ffc31-224">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="ffc31-224">[C#], F#</span></span>     | <span data-ttu-id="ffc31-225">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="ffc31-225">Web/MVC</span></span>                               | <span data-ttu-id="ffc31-226">1.0</span><span class="sxs-lookup"><span data-stu-id="ffc31-226">1.0</span></span>        |
| <span data-ttu-id="ffc31-227">ASP.NET Core webové aplikace</span><span class="sxs-lookup"><span data-stu-id="ffc31-227">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="ffc31-228">WebApp, Razor</span><span class="sxs-lookup"><span data-stu-id="ffc31-228">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="ffc31-229">Jazyk</span><span class="sxs-lookup"><span data-stu-id="ffc31-229">[C#]</span></span>         | <span data-ttu-id="ffc31-230">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="ffc31-230">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="ffc31-231">2,2, 2,0</span><span class="sxs-lookup"><span data-stu-id="ffc31-231">2.2, 2.0</span></span>   |
| <span data-ttu-id="ffc31-232">ASP.NET Core s úhlovým</span><span class="sxs-lookup"><span data-stu-id="ffc31-232">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="ffc31-233">Angular</span><span class="sxs-lookup"><span data-stu-id="ffc31-233">angular</span></span>](#spa)                 | <span data-ttu-id="ffc31-234">Jazyk</span><span class="sxs-lookup"><span data-stu-id="ffc31-234">[C#]</span></span>         | <span data-ttu-id="ffc31-235">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="ffc31-235">Web/MVC/SPA</span></span>                           | <span data-ttu-id="ffc31-236">2.0</span><span class="sxs-lookup"><span data-stu-id="ffc31-236">2.0</span></span>        |
| <span data-ttu-id="ffc31-237">ASP.NET Core s reagují. js</span><span class="sxs-lookup"><span data-stu-id="ffc31-237">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="ffc31-238">reaguje</span><span class="sxs-lookup"><span data-stu-id="ffc31-238">react</span></span>](#spa)                   | <span data-ttu-id="ffc31-239">Jazyk</span><span class="sxs-lookup"><span data-stu-id="ffc31-239">[C#]</span></span>         | <span data-ttu-id="ffc31-240">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="ffc31-240">Web/MVC/SPA</span></span>                           | <span data-ttu-id="ffc31-241">2.0</span><span class="sxs-lookup"><span data-stu-id="ffc31-241">2.0</span></span>        |
| <span data-ttu-id="ffc31-242">ASP.NET Core s využitím reagují. js a Redux</span><span class="sxs-lookup"><span data-stu-id="ffc31-242">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="ffc31-243">reactredux</span><span class="sxs-lookup"><span data-stu-id="ffc31-243">reactredux</span></span>](#reactredux)       | <span data-ttu-id="ffc31-244">Jazyk</span><span class="sxs-lookup"><span data-stu-id="ffc31-244">[C#]</span></span>         | <span data-ttu-id="ffc31-245">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="ffc31-245">Web/MVC/SPA</span></span>                           | <span data-ttu-id="ffc31-246">2.0</span><span class="sxs-lookup"><span data-stu-id="ffc31-246">2.0</span></span>        |
| <span data-ttu-id="ffc31-247">Knihovna tříd Razor</span><span class="sxs-lookup"><span data-stu-id="ffc31-247">Razor Class Library</span></span>                          | [<span data-ttu-id="ffc31-248">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="ffc31-248">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="ffc31-249">Jazyk</span><span class="sxs-lookup"><span data-stu-id="ffc31-249">[C#]</span></span>         | <span data-ttu-id="ffc31-250">Knihovna tříd web/Razor/Library/Razor</span><span class="sxs-lookup"><span data-stu-id="ffc31-250">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="ffc31-251">2.1</span><span class="sxs-lookup"><span data-stu-id="ffc31-251">2.1</span></span>        |
| <span data-ttu-id="ffc31-252">Webové rozhraní API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ffc31-252">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="ffc31-253">WebApi</span><span class="sxs-lookup"><span data-stu-id="ffc31-253">webapi</span></span>](#webapi)               | <span data-ttu-id="ffc31-254">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="ffc31-254">[C#], F#</span></span>     | <span data-ttu-id="ffc31-255">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="ffc31-255">Web/WebAPI</span></span>                            | <span data-ttu-id="ffc31-256">1.0</span><span class="sxs-lookup"><span data-stu-id="ffc31-256">1.0</span></span>        |
| <span data-ttu-id="ffc31-257">Služba ASP.NET Core gRPC</span><span class="sxs-lookup"><span data-stu-id="ffc31-257">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="ffc31-258">grpc</span><span class="sxs-lookup"><span data-stu-id="ffc31-258">grpc</span></span>](#web-others)             | <span data-ttu-id="ffc31-259">Jazyk</span><span class="sxs-lookup"><span data-stu-id="ffc31-259">[C#]</span></span>         | <span data-ttu-id="ffc31-260">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="ffc31-260">Web/gRPC</span></span>                              | <span data-ttu-id="ffc31-261">3.0</span><span class="sxs-lookup"><span data-stu-id="ffc31-261">3.0</span></span>        |
| <span data-ttu-id="ffc31-262">soubor dotnet gitignore</span><span class="sxs-lookup"><span data-stu-id="ffc31-262">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="ffc31-263">Config</span><span class="sxs-lookup"><span data-stu-id="ffc31-263">Config</span></span>                                | <span data-ttu-id="ffc31-264">3.0</span><span class="sxs-lookup"><span data-stu-id="ffc31-264">3.0</span></span>        |
| <span data-ttu-id="ffc31-265">soubor Global. JSON</span><span class="sxs-lookup"><span data-stu-id="ffc31-265">global.json file</span></span>                             | [<span data-ttu-id="ffc31-266">globaljson</span><span class="sxs-lookup"><span data-stu-id="ffc31-266">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="ffc31-267">Config</span><span class="sxs-lookup"><span data-stu-id="ffc31-267">Config</span></span>                                | <span data-ttu-id="ffc31-268">2.0</span><span class="sxs-lookup"><span data-stu-id="ffc31-268">2.0</span></span>        |
| <span data-ttu-id="ffc31-269">Konfigurace NuGet</span><span class="sxs-lookup"><span data-stu-id="ffc31-269">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="ffc31-270">Config</span><span class="sxs-lookup"><span data-stu-id="ffc31-270">Config</span></span>                                | <span data-ttu-id="ffc31-271">1.0</span><span class="sxs-lookup"><span data-stu-id="ffc31-271">1.0</span></span>        |
| <span data-ttu-id="ffc31-272">Dotnet – místní nástroj soubor manifestu</span><span class="sxs-lookup"><span data-stu-id="ffc31-272">Dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="ffc31-273">Config</span><span class="sxs-lookup"><span data-stu-id="ffc31-273">Config</span></span>                                | <span data-ttu-id="ffc31-274">3.0</span><span class="sxs-lookup"><span data-stu-id="ffc31-274">3.0</span></span>        |
| <span data-ttu-id="ffc31-275">Webová konfigurace</span><span class="sxs-lookup"><span data-stu-id="ffc31-275">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="ffc31-276">Config</span><span class="sxs-lookup"><span data-stu-id="ffc31-276">Config</span></span>                                | <span data-ttu-id="ffc31-277">1.0</span><span class="sxs-lookup"><span data-stu-id="ffc31-277">1.0</span></span>        |
| <span data-ttu-id="ffc31-278">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="ffc31-278">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="ffc31-279">Řešení</span><span class="sxs-lookup"><span data-stu-id="ffc31-279">Solution</span></span>                              | <span data-ttu-id="ffc31-280">1.0</span><span class="sxs-lookup"><span data-stu-id="ffc31-280">1.0</span></span>        |
| <span data-ttu-id="ffc31-281">Soubor vyrovnávací paměti protokolu</span><span class="sxs-lookup"><span data-stu-id="ffc31-281">Protocol Buffer File</span></span>                         | [<span data-ttu-id="ffc31-282">proto</span><span class="sxs-lookup"><span data-stu-id="ffc31-282">proto</span></span>](#namespace)             |              | <span data-ttu-id="ffc31-283">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="ffc31-283">Web/gRPC</span></span>                              | <span data-ttu-id="ffc31-284">3.0</span><span class="sxs-lookup"><span data-stu-id="ffc31-284">3.0</span></span>        |

## <a name="options"></a><span data-ttu-id="ffc31-285">Možnosti</span><span class="sxs-lookup"><span data-stu-id="ffc31-285">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="ffc31-286">Zobrazí souhrnné informace o tom, co se stane, pokud by došlo ke spuštění daného příkazu, pokud by to vedlo k vytvoření šablony.</span><span class="sxs-lookup"><span data-stu-id="ffc31-286">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span> <span data-ttu-id="ffc31-287">K dispozici od verze .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="ffc31-287">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="ffc31-288">Vynutí vygenerování obsahu i v případě, že změní existující soubory.</span><span class="sxs-lookup"><span data-stu-id="ffc31-288">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="ffc31-289">Tato možnost je vyžadována, pokud by vybraná šablona přepsala existující soubory ve výstupním adresáři.</span><span class="sxs-lookup"><span data-stu-id="ffc31-289">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="ffc31-290">Vytiskne nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="ffc31-290">Prints out help for the command.</span></span> <span data-ttu-id="ffc31-291">Dá se vyvolat pro `dotnet new` samotný příkaz nebo pro libovolnou šablonu.</span><span class="sxs-lookup"><span data-stu-id="ffc31-291">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="ffc31-292">Například, `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="ffc31-292">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="ffc31-293">Nainstaluje sadu šablon z `PATH` nebo `NUGET_ID` poskytnuté.</span><span class="sxs-lookup"><span data-stu-id="ffc31-293">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="ffc31-294">Pokud chcete nainstalovat předprodejní verzi balíčku šablony, je nutné zadat verzi ve formátu `<package-name>::<package-version>` .</span><span class="sxs-lookup"><span data-stu-id="ffc31-294">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="ffc31-295">Ve výchozím nastavení se `dotnet new` předá \* verze, která představuje nejnovější stabilní verzi balíčku.</span><span class="sxs-lookup"><span data-stu-id="ffc31-295">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="ffc31-296">Podívejte se na příklad v části [Příklady](#examples) .</span><span class="sxs-lookup"><span data-stu-id="ffc31-296">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="ffc31-297">Pokud byla verze šablony již nainstalována při spuštění tohoto příkazu, šablona bude aktualizována na určenou verzi nebo na nejnovější stabilní verzi, pokud nebyla zadána žádná verze.</span><span class="sxs-lookup"><span data-stu-id="ffc31-297">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="ffc31-298">Informace o vytváření vlastních šablon najdete v tématu [vlastní šablony pro dotnet New](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="ffc31-298">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="ffc31-299">Vypíše seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="ffc31-299">Lists templates containing the specified name.</span></span> <span data-ttu-id="ffc31-300">Pokud není zadán žádný název, vypíše všechny šablony.</span><span class="sxs-lookup"><span data-stu-id="ffc31-300">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="ffc31-301">Jazyk šablony, která se má vytvořit</span><span class="sxs-lookup"><span data-stu-id="ffc31-301">The language of the template to create.</span></span> <span data-ttu-id="ffc31-302">Přijatý jazyk se liší podle šablony (viz výchozí hodnoty v oddílu [argumenty](#arguments) ).</span><span class="sxs-lookup"><span data-stu-id="ffc31-302">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="ffc31-303">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="ffc31-303">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="ffc31-304">Některá prostředí jsou interpretována `#` jako speciální znak.</span><span class="sxs-lookup"><span data-stu-id="ffc31-304">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="ffc31-305">V těchto případech uveďte hodnotu parametru Language v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="ffc31-305">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="ffc31-306">Například, `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="ffc31-306">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="ffc31-307">Název vytvořeného výstupu.</span><span class="sxs-lookup"><span data-stu-id="ffc31-307">The name for the created output.</span></span> <span data-ttu-id="ffc31-308">Pokud název nezadáte, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="ffc31-308">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="ffc31-309">Určuje zdroj NuGet, který se použije při instalaci.</span><span class="sxs-lookup"><span data-stu-id="ffc31-309">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="ffc31-310">K dispozici od verze .NET Core 2,1 SDK.</span><span class="sxs-lookup"><span data-stu-id="ffc31-310">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="ffc31-311">Umístění, do kterého se má vygenerovaný výstup umístit.</span><span class="sxs-lookup"><span data-stu-id="ffc31-311">Location to place the generated output.</span></span> <span data-ttu-id="ffc31-312">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="ffc31-312">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="ffc31-313">Filtruje šablony založené na dostupných typech.</span><span class="sxs-lookup"><span data-stu-id="ffc31-313">Filters templates based on available types.</span></span> <span data-ttu-id="ffc31-314">Předdefinované hodnoty jsou `project` , `item` a `other` .</span><span class="sxs-lookup"><span data-stu-id="ffc31-314">Predefined values are `project`, `item`, and `other`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="ffc31-315">Odinstaluje sadu šablon na `PATH` nebo `NUGET_ID` poskytnutou.</span><span class="sxs-lookup"><span data-stu-id="ffc31-315">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="ffc31-316">Pokud `<PATH|NUGET_ID>` hodnota není zadaná, zobrazí se všechny aktuálně nainstalované sady šablon a jejich přidružené šablony.</span><span class="sxs-lookup"><span data-stu-id="ffc31-316">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="ffc31-317">Při zadávání nezahrnujte `NUGET_ID` číslo verze.</span><span class="sxs-lookup"><span data-stu-id="ffc31-317">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="ffc31-318">Pokud neurčíte parametr této možnosti, příkaz zobrazí seznam nainstalovaných šablon a podrobností.</span><span class="sxs-lookup"><span data-stu-id="ffc31-318">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="ffc31-319">Chcete-li odinstalovat šablonu pomocí nástroje `PATH` , je nutné plně kvalifikovat cestu.</span><span class="sxs-lookup"><span data-stu-id="ffc31-319">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="ffc31-320">Například *C:/Users/ \< User>/Documents/Templates/garciasoftware.consoletemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z nadřazené složky to nebude.</span><span class="sxs-lookup"><span data-stu-id="ffc31-320">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="ffc31-321">Do cesty k šabloně nezahrnujte konečné koncové lomítko adresáře.</span><span class="sxs-lookup"><span data-stu-id="ffc31-321">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="ffc31-322">Kontroluje, zda jsou k dispozici aktualizace pro sady šablon, které jsou aktuálně nainstalovány a instalovány.</span><span class="sxs-lookup"><span data-stu-id="ffc31-322">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="ffc31-323">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ffc31-323">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="ffc31-324">Kontroluje, zda jsou k dispozici aktualizace pro sady šablon, které jsou aktuálně nainstalovány.</span><span class="sxs-lookup"><span data-stu-id="ffc31-324">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="ffc31-325">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ffc31-325">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="ffc31-326">Možnosti šablon</span><span class="sxs-lookup"><span data-stu-id="ffc31-326">Template options</span></span>

<span data-ttu-id="ffc31-327">Každá šablona projektu může mít k dispozici další možnosti.</span><span class="sxs-lookup"><span data-stu-id="ffc31-327">Each project template may have additional options available.</span></span> <span data-ttu-id="ffc31-328">Základní šablony mají následující další možnosti:</span><span class="sxs-lookup"><span data-stu-id="ffc31-328">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="ffc31-329">konzola</span><span class="sxs-lookup"><span data-stu-id="ffc31-329">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ffc31-330">Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="ffc31-330">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ffc31-331">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ffc31-331">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="ffc31-332">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, který používáte:</span><span class="sxs-lookup"><span data-stu-id="ffc31-332">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ffc31-333">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="ffc31-333">SDK version</span></span> | <span data-ttu-id="ffc31-334">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="ffc31-334">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ffc31-335">3.1</span><span class="sxs-lookup"><span data-stu-id="ffc31-335">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ffc31-336">3.0</span><span class="sxs-lookup"><span data-stu-id="ffc31-336">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="ffc31-337">Nastaví `LangVersion` vlastnost v souboru vytvořeného projektu.</span><span class="sxs-lookup"><span data-stu-id="ffc31-337">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="ffc31-338">Například použijte `--langVersion 7.3` k použití jazyka C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="ffc31-338">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="ffc31-339">Nepodporováno v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="ffc31-339">Not supported for F#.</span></span> <span data-ttu-id="ffc31-340">K dispozici od verze .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="ffc31-340">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="ffc31-341">Seznam výchozích verzí jazyka C# naleznete v tématu [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="ffc31-341">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="ffc31-342">Je-li tento parametr zadán, nespustí při vytváření projektu implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="ffc31-342">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="ffc31-343">K dispozici od verze .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="ffc31-343">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="ffc31-344">že knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="ffc31-344">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ffc31-345">Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="ffc31-345">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ffc31-346">Hodnoty: `netcoreapp<version>` pro vytvoření knihovny tříd .NET Core nebo `netstandard<version>` pro vytvoření knihovny tříd .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="ffc31-346">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="ffc31-347">Výchozí hodnota je `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="ffc31-347">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="ffc31-348">Nastaví `LangVersion` vlastnost v souboru vytvořeného projektu.</span><span class="sxs-lookup"><span data-stu-id="ffc31-348">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="ffc31-349">Například použijte `--langVersion 7.3` k použití jazyka C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="ffc31-349">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="ffc31-350">Nepodporováno v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="ffc31-350">Not supported for F#.</span></span> <span data-ttu-id="ffc31-351">K dispozici od verze .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="ffc31-351">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="ffc31-352">Seznam výchozích verzí jazyka C# naleznete v tématu [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="ffc31-352">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="ffc31-353">Při vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="ffc31-353">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a><span data-ttu-id="ffc31-354">WPF, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="ffc31-354">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ffc31-355">Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="ffc31-355">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ffc31-356">Výchozí hodnota je `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="ffc31-356">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="ffc31-357">K dispozici od verze .NET Core 3,1 SDK.</span><span class="sxs-lookup"><span data-stu-id="ffc31-357">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="ffc31-358">Nastaví `LangVersion` vlastnost v souboru vytvořeného projektu.</span><span class="sxs-lookup"><span data-stu-id="ffc31-358">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="ffc31-359">Například použijte `--langVersion 7.3` k použití jazyka C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="ffc31-359">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="ffc31-360">Seznam výchozích verzí jazyka C# naleznete v tématu [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="ffc31-360">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="ffc31-361">Při vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="ffc31-361">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms-winformslib"></a><a name="winforms"></a><span data-ttu-id="ffc31-362">WinForms, winformslib</span><span class="sxs-lookup"><span data-stu-id="ffc31-362">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="ffc31-363">Nastaví `LangVersion` vlastnost v souboru vytvořeného projektu.</span><span class="sxs-lookup"><span data-stu-id="ffc31-363">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="ffc31-364">Například použijte `--langVersion 7.3` k použití jazyka C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="ffc31-364">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="ffc31-365">Seznam výchozích verzí jazyka C# naleznete v tématu [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="ffc31-365">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="ffc31-366">Při vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="ffc31-366">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="worker-grpc"></a><a name="web-others"></a><span data-ttu-id="ffc31-367">pracovní proces, grpc</span><span class="sxs-lookup"><span data-stu-id="ffc31-367">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ffc31-368">Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="ffc31-368">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ffc31-369">Výchozí hodnota je `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="ffc31-369">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="ffc31-370">K dispozici od verze .NET Core 3,1 SDK.</span><span class="sxs-lookup"><span data-stu-id="ffc31-370">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="ffc31-371">Vyloučí z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="ffc31-371">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="ffc31-372">Při vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="ffc31-372">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="mstest-xunit"></a><a name="test"></a><span data-ttu-id="ffc31-373">MSTest, xUnit</span><span class="sxs-lookup"><span data-stu-id="ffc31-373">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ffc31-374">Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="ffc31-374">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ffc31-375">Možnost je k dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ffc31-375">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="ffc31-376">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, který používáte:</span><span class="sxs-lookup"><span data-stu-id="ffc31-376">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ffc31-377">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="ffc31-377">SDK version</span></span> | <span data-ttu-id="ffc31-378">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="ffc31-378">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ffc31-379">3.1</span><span class="sxs-lookup"><span data-stu-id="ffc31-379">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ffc31-380">3.0</span><span class="sxs-lookup"><span data-stu-id="ffc31-380">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="ffc31-381">Umožňuje sbalení pro projekt pomocí [sady dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="ffc31-381">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="ffc31-382">Při vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="ffc31-382">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="ffc31-383">nunit</span><span class="sxs-lookup"><span data-stu-id="ffc31-383">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ffc31-384">Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="ffc31-384">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="ffc31-385">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, který používáte:</span><span class="sxs-lookup"><span data-stu-id="ffc31-385">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ffc31-386">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="ffc31-386">SDK version</span></span> | <span data-ttu-id="ffc31-387">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="ffc31-387">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ffc31-388">3.1</span><span class="sxs-lookup"><span data-stu-id="ffc31-388">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ffc31-389">3.0</span><span class="sxs-lookup"><span data-stu-id="ffc31-389">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="ffc31-390">2,2</span><span class="sxs-lookup"><span data-stu-id="ffc31-390">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="ffc31-391">2.1</span><span class="sxs-lookup"><span data-stu-id="ffc31-391">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="ffc31-392">Umožňuje sbalení pro projekt pomocí [sady dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="ffc31-392">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="ffc31-393">Při vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="ffc31-393">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="ffc31-394">Page</span><span class="sxs-lookup"><span data-stu-id="ffc31-394">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="ffc31-395">Obor názvů pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="ffc31-395">Namespace for the generated code.</span></span> <span data-ttu-id="ffc31-396">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="ffc31-396">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="ffc31-397">Vytvoří stránku bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="ffc31-397">Creates the page without a PageModel.</span></span>

***

### <a name="viewimports-proto"></a><a name="namespace"></a><span data-ttu-id="ffc31-398">viewimports, a proto</span><span class="sxs-lookup"><span data-stu-id="ffc31-398">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="ffc31-399">Obor názvů pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="ffc31-399">Namespace for the generated code.</span></span> <span data-ttu-id="ffc31-400">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="ffc31-400">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="ffc31-401">blazorserver</span><span class="sxs-lookup"><span data-stu-id="ffc31-401">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="ffc31-402">Typ ověřování, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="ffc31-402">The type of authentication to use.</span></span> <span data-ttu-id="ffc31-403">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="ffc31-403">The possible values are:</span></span>

  - <span data-ttu-id="ffc31-404">`None`-Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="ffc31-404">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="ffc31-405">`Individual`-Individuální ověřování.</span><span class="sxs-lookup"><span data-stu-id="ffc31-405">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="ffc31-406">`IndividualB2C`-Jednotlivá ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="ffc31-406">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="ffc31-407">`SingleOrg`– Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="ffc31-407">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="ffc31-408">`MultiOrg`– Ověřování organizace pro více tenantů.</span><span class="sxs-lookup"><span data-stu-id="ffc31-408">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="ffc31-409">`Windows`– Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="ffc31-409">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="ffc31-410">Instance Azure Active Directory B2C pro připojení.</span><span class="sxs-lookup"><span data-stu-id="ffc31-410">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ffc31-411">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="ffc31-411">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ffc31-412">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="ffc31-412">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="ffc31-413">ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="ffc31-413">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ffc31-414">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="ffc31-414">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="ffc31-415">ID zásad pro resetování hesla pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="ffc31-415">The reset password policy ID for this project.</span></span> <span data-ttu-id="ffc31-416">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="ffc31-416">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="ffc31-417">Upravit ID zásad profilu pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="ffc31-417">The edit profile policy ID for this project.</span></span> <span data-ttu-id="ffc31-418">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="ffc31-418">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="ffc31-419">Instance Azure Active Directory pro připojení.</span><span class="sxs-lookup"><span data-stu-id="ffc31-419">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ffc31-420">Použijte s `SingleOrg` `MultiOrg` ověřováním nebo.</span><span class="sxs-lookup"><span data-stu-id="ffc31-420">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="ffc31-421">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="ffc31-421">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="ffc31-422">ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="ffc31-422">The Client ID for this project.</span></span> <span data-ttu-id="ffc31-423">Použijte s `IndividualB2C` `SingleOrg` `MultiOrg` ověřováním, nebo.</span><span class="sxs-lookup"><span data-stu-id="ffc31-423">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="ffc31-424">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="ffc31-424">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="ffc31-425">Doména pro tenanta adresáře.</span><span class="sxs-lookup"><span data-stu-id="ffc31-425">The domain for the directory tenant.</span></span> <span data-ttu-id="ffc31-426">Použijte s `SingleOrg` `IndividualB2C` ověřováním nebo.</span><span class="sxs-lookup"><span data-stu-id="ffc31-426">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ffc31-427">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="ffc31-427">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="ffc31-428">ID TenantId adresáře, ke kterému se má připojit.</span><span class="sxs-lookup"><span data-stu-id="ffc31-428">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ffc31-429">Použijte s `SingleOrg` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="ffc31-429">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ffc31-430">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="ffc31-430">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="ffc31-431">Cesta požadavku v základní cestě identifikátoru URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="ffc31-431">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="ffc31-432">Použijte s `SingleOrg` `IndividualB2C` ověřováním nebo.</span><span class="sxs-lookup"><span data-stu-id="ffc31-432">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ffc31-433">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="ffc31-433">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="ffc31-434">Povolí této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="ffc31-434">Allows this application read-access to the directory.</span></span> <span data-ttu-id="ffc31-435">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ffc31-435">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="ffc31-436">Vyloučí z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="ffc31-436">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="ffc31-437">Vypne protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ffc31-437">Turns off HTTPS.</span></span> <span data-ttu-id="ffc31-438">Tato možnost platí pouze v případě, že se `Individual` `IndividualB2C` `SingleOrg` `MultiOrg` nepoužívá pro `--auth` .</span><span class="sxs-lookup"><span data-stu-id="ffc31-438">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="ffc31-439">Určuje, že se má místo SQLite použít LocalDB.</span><span class="sxs-lookup"><span data-stu-id="ffc31-439">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ffc31-440">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ffc31-440">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="ffc31-441">Při vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="ffc31-441">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="ffc31-442">web</span><span class="sxs-lookup"><span data-stu-id="ffc31-442">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="ffc31-443">Vyloučí z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="ffc31-443">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ffc31-444">Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="ffc31-444">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ffc31-445">Možnost není dostupná v sadě .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="ffc31-445">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="ffc31-446">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, který používáte:</span><span class="sxs-lookup"><span data-stu-id="ffc31-446">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ffc31-447">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="ffc31-447">SDK version</span></span> | <span data-ttu-id="ffc31-448">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="ffc31-448">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ffc31-449">3.1</span><span class="sxs-lookup"><span data-stu-id="ffc31-449">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ffc31-450">3.0</span><span class="sxs-lookup"><span data-stu-id="ffc31-450">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="ffc31-451">2.1</span><span class="sxs-lookup"><span data-stu-id="ffc31-451">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="ffc31-452">Při vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="ffc31-452">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="ffc31-453">Vypne protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ffc31-453">Turns off HTTPS.</span></span>

***

### <a name="mvc-webapp"></a><a name="web-options"></a><span data-ttu-id="ffc31-454">MVC, WebApp</span><span class="sxs-lookup"><span data-stu-id="ffc31-454">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="ffc31-455">Typ ověřování, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="ffc31-455">The type of authentication to use.</span></span> <span data-ttu-id="ffc31-456">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="ffc31-456">The possible values are:</span></span>

  - <span data-ttu-id="ffc31-457">`None`-Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="ffc31-457">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="ffc31-458">`Individual`-Individuální ověřování.</span><span class="sxs-lookup"><span data-stu-id="ffc31-458">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="ffc31-459">`IndividualB2C`-Jednotlivá ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="ffc31-459">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="ffc31-460">`SingleOrg`– Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="ffc31-460">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="ffc31-461">`MultiOrg`– Ověřování organizace pro více tenantů.</span><span class="sxs-lookup"><span data-stu-id="ffc31-461">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="ffc31-462">`Windows`– Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="ffc31-462">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="ffc31-463">Instance Azure Active Directory B2C pro připojení.</span><span class="sxs-lookup"><span data-stu-id="ffc31-463">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ffc31-464">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="ffc31-464">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ffc31-465">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="ffc31-465">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="ffc31-466">ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="ffc31-466">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ffc31-467">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="ffc31-467">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="ffc31-468">ID zásad pro resetování hesla pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="ffc31-468">The reset password policy ID for this project.</span></span> <span data-ttu-id="ffc31-469">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="ffc31-469">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="ffc31-470">Upravit ID zásad profilu pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="ffc31-470">The edit profile policy ID for this project.</span></span> <span data-ttu-id="ffc31-471">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="ffc31-471">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="ffc31-472">Instance Azure Active Directory pro připojení.</span><span class="sxs-lookup"><span data-stu-id="ffc31-472">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ffc31-473">Použijte s `SingleOrg` `MultiOrg` ověřováním nebo.</span><span class="sxs-lookup"><span data-stu-id="ffc31-473">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="ffc31-474">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="ffc31-474">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="ffc31-475">ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="ffc31-475">The Client ID for this project.</span></span> <span data-ttu-id="ffc31-476">Použijte s `IndividualB2C` `SingleOrg` `MultiOrg` ověřováním, nebo.</span><span class="sxs-lookup"><span data-stu-id="ffc31-476">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="ffc31-477">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="ffc31-477">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="ffc31-478">Doména pro tenanta adresáře.</span><span class="sxs-lookup"><span data-stu-id="ffc31-478">The domain for the directory tenant.</span></span> <span data-ttu-id="ffc31-479">Použijte s `SingleOrg` `IndividualB2C` ověřováním nebo.</span><span class="sxs-lookup"><span data-stu-id="ffc31-479">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ffc31-480">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="ffc31-480">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="ffc31-481">ID TenantId adresáře, ke kterému se má připojit.</span><span class="sxs-lookup"><span data-stu-id="ffc31-481">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ffc31-482">Použijte s `SingleOrg` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="ffc31-482">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ffc31-483">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="ffc31-483">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="ffc31-484">Cesta požadavku v základní cestě identifikátoru URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="ffc31-484">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="ffc31-485">Použijte s `SingleOrg` `IndividualB2C` ověřováním nebo.</span><span class="sxs-lookup"><span data-stu-id="ffc31-485">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ffc31-486">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="ffc31-486">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="ffc31-487">Povolí této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="ffc31-487">Allows this application read-access to the directory.</span></span> <span data-ttu-id="ffc31-488">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ffc31-488">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="ffc31-489">Vyloučí z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="ffc31-489">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="ffc31-490">Vypne protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ffc31-490">Turns off HTTPS.</span></span> <span data-ttu-id="ffc31-491">Tato možnost platí pouze v případě, že se `Individual` `IndividualB2C` `SingleOrg` `MultiOrg` nepoužívají, nebo.</span><span class="sxs-lookup"><span data-stu-id="ffc31-491">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="ffc31-492">Určuje, že se má místo SQLite použít LocalDB.</span><span class="sxs-lookup"><span data-stu-id="ffc31-492">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ffc31-493">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ffc31-493">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ffc31-494">Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="ffc31-494">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ffc31-495">Možnost je k dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ffc31-495">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="ffc31-496">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, který používáte:</span><span class="sxs-lookup"><span data-stu-id="ffc31-496">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ffc31-497">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="ffc31-497">SDK version</span></span> | <span data-ttu-id="ffc31-498">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="ffc31-498">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ffc31-499">3.1</span><span class="sxs-lookup"><span data-stu-id="ffc31-499">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ffc31-500">3.0</span><span class="sxs-lookup"><span data-stu-id="ffc31-500">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="ffc31-501">Při vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="ffc31-501">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="ffc31-502">Zahrnuje BrowserLink do projektu.</span><span class="sxs-lookup"><span data-stu-id="ffc31-502">Includes BrowserLink in the project.</span></span> <span data-ttu-id="ffc31-503">V rozhraní .NET Core 2,2 a 3,1 SDK není dostupná možnost.</span><span class="sxs-lookup"><span data-stu-id="ffc31-503">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="ffc31-504">Určuje, jestli je projekt nakonfigurovaný tak, aby používal [kompilaci za běhu Razor](/aspnet/core/mvc/views/view-compilation#runtime-compilation) v sestaveních ladění.</span><span class="sxs-lookup"><span data-stu-id="ffc31-504">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="ffc31-505">Možnost je k dispozici od 3.1.201 sady .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="ffc31-505">Option available since .NET Core 3.1.201 SDK.</span></span>

***

### <a name="angular-react"></a><a name="spa"></a><span data-ttu-id="ffc31-506">Úhlová, reakce</span><span class="sxs-lookup"><span data-stu-id="ffc31-506">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="ffc31-507">Typ ověřování, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="ffc31-507">The type of authentication to use.</span></span> <span data-ttu-id="ffc31-508">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ffc31-508">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="ffc31-509">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="ffc31-509">The possible values are:</span></span>

  - <span data-ttu-id="ffc31-510">`None`-Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="ffc31-510">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="ffc31-511">`Individual`-Individuální ověřování.</span><span class="sxs-lookup"><span data-stu-id="ffc31-511">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="ffc31-512">Vyloučí z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="ffc31-512">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="ffc31-513">Při vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="ffc31-513">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="ffc31-514">Vypne protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ffc31-514">Turns off HTTPS.</span></span> <span data-ttu-id="ffc31-515">Tato možnost platí pouze v případě, že je ověřování `None` .</span><span class="sxs-lookup"><span data-stu-id="ffc31-515">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="ffc31-516">Určuje, že se má místo SQLite použít LocalDB.</span><span class="sxs-lookup"><span data-stu-id="ffc31-516">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ffc31-517">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ffc31-517">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ffc31-518">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ffc31-518">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ffc31-519">Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="ffc31-519">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ffc31-520">Možnost není dostupná v sadě .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="ffc31-520">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="ffc31-521">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, který používáte:</span><span class="sxs-lookup"><span data-stu-id="ffc31-521">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ffc31-522">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="ffc31-522">SDK version</span></span> | <span data-ttu-id="ffc31-523">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="ffc31-523">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ffc31-524">3.1</span><span class="sxs-lookup"><span data-stu-id="ffc31-524">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ffc31-525">3.0</span><span class="sxs-lookup"><span data-stu-id="ffc31-525">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="ffc31-526">2.1</span><span class="sxs-lookup"><span data-stu-id="ffc31-526">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="ffc31-527">reactredux</span><span class="sxs-lookup"><span data-stu-id="ffc31-527">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="ffc31-528">Vyloučí z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="ffc31-528">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ffc31-529">Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="ffc31-529">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ffc31-530">Možnost není dostupná v sadě .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="ffc31-530">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="ffc31-531">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, který používáte:</span><span class="sxs-lookup"><span data-stu-id="ffc31-531">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ffc31-532">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="ffc31-532">SDK version</span></span> | <span data-ttu-id="ffc31-533">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="ffc31-533">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ffc31-534">3.1</span><span class="sxs-lookup"><span data-stu-id="ffc31-534">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ffc31-535">3.0</span><span class="sxs-lookup"><span data-stu-id="ffc31-535">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="ffc31-536">2.1</span><span class="sxs-lookup"><span data-stu-id="ffc31-536">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="ffc31-537">Při vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="ffc31-537">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="ffc31-538">Vypne protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ffc31-538">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="ffc31-539">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="ffc31-539">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="ffc31-540">Při vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="ffc31-540">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="ffc31-541">Podporuje kromě součástí do této knihovny i tradiční zobrazení a stránky Razor.</span><span class="sxs-lookup"><span data-stu-id="ffc31-541">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="ffc31-542">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ffc31-542">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="ffc31-543">WebApi</span><span class="sxs-lookup"><span data-stu-id="ffc31-543">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="ffc31-544">Typ ověřování, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="ffc31-544">The type of authentication to use.</span></span> <span data-ttu-id="ffc31-545">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="ffc31-545">The possible values are:</span></span>

  - <span data-ttu-id="ffc31-546">`None`-Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="ffc31-546">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="ffc31-547">`IndividualB2C`-Jednotlivá ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="ffc31-547">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="ffc31-548">`SingleOrg`– Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="ffc31-548">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="ffc31-549">`Windows`– Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="ffc31-549">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="ffc31-550">Instance Azure Active Directory B2C pro připojení.</span><span class="sxs-lookup"><span data-stu-id="ffc31-550">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ffc31-551">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="ffc31-551">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ffc31-552">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="ffc31-552">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="ffc31-553">ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="ffc31-553">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ffc31-554">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="ffc31-554">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="ffc31-555">Instance Azure Active Directory pro připojení.</span><span class="sxs-lookup"><span data-stu-id="ffc31-555">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ffc31-556">Použijte s `SingleOrg` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="ffc31-556">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ffc31-557">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="ffc31-557">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="ffc31-558">ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="ffc31-558">The Client ID for this project.</span></span> <span data-ttu-id="ffc31-559">Použijte s `IndividualB2C` `SingleOrg` ověřováním nebo.</span><span class="sxs-lookup"><span data-stu-id="ffc31-559">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="ffc31-560">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="ffc31-560">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="ffc31-561">Doména pro tenanta adresáře.</span><span class="sxs-lookup"><span data-stu-id="ffc31-561">The domain for the directory tenant.</span></span> <span data-ttu-id="ffc31-562">Použijte s `IndividualB2C` `SingleOrg` ověřováním nebo.</span><span class="sxs-lookup"><span data-stu-id="ffc31-562">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="ffc31-563">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="ffc31-563">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="ffc31-564">ID TenantId adresáře, ke kterému se má připojit.</span><span class="sxs-lookup"><span data-stu-id="ffc31-564">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ffc31-565">Použijte s `SingleOrg` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="ffc31-565">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ffc31-566">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="ffc31-566">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="ffc31-567">Povolí této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="ffc31-567">Allows this application read-access to the directory.</span></span> <span data-ttu-id="ffc31-568">Platí jenom pro `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ffc31-568">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="ffc31-569">Vyloučí z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="ffc31-569">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="ffc31-570">Vypne protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ffc31-570">Turns off HTTPS.</span></span> <span data-ttu-id="ffc31-571">`app.UseHsts`a `app.UseHttpsRedirection` nejsou přidány do `Startup.Configure` .</span><span class="sxs-lookup"><span data-stu-id="ffc31-571">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="ffc31-572">Tato možnost se vztahuje jenom `IndividualB2C` na to, jestli `SingleOrg` se nepoužívají pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="ffc31-572">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="ffc31-573">Určuje, že se má místo SQLite použít LocalDB.</span><span class="sxs-lookup"><span data-stu-id="ffc31-573">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ffc31-574">Platí jenom pro `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ffc31-574">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ffc31-575">Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="ffc31-575">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ffc31-576">Možnost není dostupná v sadě .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="ffc31-576">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="ffc31-577">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, který používáte:</span><span class="sxs-lookup"><span data-stu-id="ffc31-577">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ffc31-578">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="ffc31-578">SDK version</span></span> | <span data-ttu-id="ffc31-579">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="ffc31-579">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ffc31-580">3.1</span><span class="sxs-lookup"><span data-stu-id="ffc31-580">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ffc31-581">3.0</span><span class="sxs-lookup"><span data-stu-id="ffc31-581">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="ffc31-582">2.1</span><span class="sxs-lookup"><span data-stu-id="ffc31-582">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="ffc31-583">Při vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="ffc31-583">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="ffc31-584">globaljson</span><span class="sxs-lookup"><span data-stu-id="ffc31-584">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="ffc31-585">Určuje verzi .NET Core SDK, která se má použít v souboru *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="ffc31-585">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="ffc31-586">Příklady</span><span class="sxs-lookup"><span data-stu-id="ffc31-586">Examples</span></span>

- <span data-ttu-id="ffc31-587">Vytvořte projekt konzolové aplikace v jazyce C# zadáním názvu šablony:</span><span class="sxs-lookup"><span data-stu-id="ffc31-587">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="ffc31-588">Vytvořte projekt konzolové aplikace F # v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="ffc31-588">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang "F#"
  ```

- <span data-ttu-id="ffc31-589">Vytvořte .NET Standard projekt knihovny tříd v zadaném adresáři:</span><span class="sxs-lookup"><span data-stu-id="ffc31-589">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="ffc31-590">Vytvoří nový projekt ASP.NET Core C# MVC v aktuálním adresáři bez ověřování:</span><span class="sxs-lookup"><span data-stu-id="ffc31-590">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="ffc31-591">Vytvořit nový projekt xUnit:</span><span class="sxs-lookup"><span data-stu-id="ffc31-591">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="ffc31-592">Vypíše všechny šablony, které jsou k dispozici pro šablony jednostránkové aplikace (SPA):</span><span class="sxs-lookup"><span data-stu-id="ffc31-592">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="ffc31-593">Vypíše všechny šablony, které odpovídají podřetězci *My* .</span><span class="sxs-lookup"><span data-stu-id="ffc31-593">List all templates matching the *we* substring.</span></span> <span data-ttu-id="ffc31-594">Nebyla nalezena žádná přesná shoda, takže porovnávání dílčích řetězců se shoduje se sloupci krátkého názvu a názvu.</span><span class="sxs-lookup"><span data-stu-id="ffc31-594">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="ffc31-595">Došlo k pokusu o vyvolání šablony, která odpovídá *NG*.</span><span class="sxs-lookup"><span data-stu-id="ffc31-595">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="ffc31-596">Pokud nelze určit jednu shodu, Seznamte se se šablonami, které jsou částečné shody.</span><span class="sxs-lookup"><span data-stu-id="ffc31-596">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="ffc31-597">Nainstalujte verzi 2,0 šablon SPA pro ASP.NET Core:</span><span class="sxs-lookup"><span data-stu-id="ffc31-597">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="ffc31-598">Seznam nainstalovaných šablon a podrobností, včetně jejich odinstalace:</span><span class="sxs-lookup"><span data-stu-id="ffc31-598">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="ffc31-599">V aktuálním adresáři vytvořte *Global. JSON* s nastavením verze sady SDK na 3.1.101:</span><span class="sxs-lookup"><span data-stu-id="ffc31-599">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="ffc31-600">Viz také</span><span class="sxs-lookup"><span data-stu-id="ffc31-600">See also</span></span>

- [<span data-ttu-id="ffc31-601">Vlastní šablony pro dotnet New</span><span class="sxs-lookup"><span data-stu-id="ffc31-601">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="ffc31-602">Vytvoření vlastní šablony pro dotnet new</span><span class="sxs-lookup"><span data-stu-id="ffc31-602">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="ffc31-603">dotnet/dotnet-Template-Samples – úložiště GitHub</span><span class="sxs-lookup"><span data-stu-id="ffc31-603">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="ffc31-604">Dostupné šablony pro dotnet New</span><span class="sxs-lookup"><span data-stu-id="ffc31-604">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
