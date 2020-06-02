---
title: dotnet – nový příkaz
description: Příkaz dotnet New vytvoří nové projekty .NET Core založené na zadané šabloně.
ms.date: 04/10/2020
ms.openlocfilehash: 39301ad95761848b60b45cb5c18ede937f70c32c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84283972"
---
# <a name="dotnet-new"></a><span data-ttu-id="ab919-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="ab919-103">dotnet new</span></span>

<span data-ttu-id="ab919-104">**Tento článek se týká:** ✔️ .net Core 2,0 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="ab919-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="ab919-105">Name</span><span class="sxs-lookup"><span data-stu-id="ab919-105">Name</span></span>

<span data-ttu-id="ab919-106">`dotnet new`– Vytvoří nový projekt, konfigurační soubor nebo řešení na základě zadané šablony.</span><span class="sxs-lookup"><span data-stu-id="ab919-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ab919-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="ab919-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {"C#"|"F#"|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="ab919-108">Popis</span><span class="sxs-lookup"><span data-stu-id="ab919-108">Description</span></span>

<span data-ttu-id="ab919-109">`dotnet new`Příkaz vytvoří projekt .NET Core nebo jiné artefakty založené na šabloně.</span><span class="sxs-lookup"><span data-stu-id="ab919-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="ab919-110">Příkaz volá [modul šablony](https://github.com/dotnet/templating) a vytvoří artefakty na disku na základě zadané šablony a možností.</span><span class="sxs-lookup"><span data-stu-id="ab919-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="ab919-111">Implicitní obnovení</span><span class="sxs-lookup"><span data-stu-id="ab919-111">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="ab919-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="ab919-112">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="ab919-113">Šablona, která se má vytvořit při vyvolání příkazu</span><span class="sxs-lookup"><span data-stu-id="ab919-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="ab919-114">Každá šablona může mít konkrétní možnosti, které můžete předat.</span><span class="sxs-lookup"><span data-stu-id="ab919-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="ab919-115">Další informace najdete v tématu [Možnosti šablony](#template-options).</span><span class="sxs-lookup"><span data-stu-id="ab919-115">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="ab919-116">Můžete spustit `dotnet new --list` nebo `dotnet new -l` a zobrazit seznam všech nainstalovaných šablon.</span><span class="sxs-lookup"><span data-stu-id="ab919-116">You can run `dotnet new --list` or `dotnet new -l` to see a list of all installed templates.</span></span> <span data-ttu-id="ab919-117">Pokud `TEMPLATE` hodnota není přesná shoda na textu v **šablonách** nebo ve sloupci **krátký název** z vrácené tabulky, provede se shoda podřetězce na těchto dvou sloupcích.</span><span class="sxs-lookup"><span data-stu-id="ab919-117">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="ab919-118">Počínaje verzí .NET Core 3,0 SDK vyhledává CLI šablony v NuGet.org při vyvolání `dotnet new` příkazu v následujících podmínkách:</span><span class="sxs-lookup"><span data-stu-id="ab919-118">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="ab919-119">Pokud rozhraní příkazového řádku nenalezne při vyvolání odpovídající šablonu `dotnet new` , která není ani částečná.</span><span class="sxs-lookup"><span data-stu-id="ab919-119">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="ab919-120">Pokud je k dispozici novější verze šablony.</span><span class="sxs-lookup"><span data-stu-id="ab919-120">If there's a newer version of the template available.</span></span> <span data-ttu-id="ab919-121">V tomto případě se vytvoří projekt nebo artefakt, ale rozhraní příkazového řádku vás upozorní na aktualizovanou verzi šablony.</span><span class="sxs-lookup"><span data-stu-id="ab919-121">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="ab919-122">Následující tabulka obsahuje šablony, které jsou předinstalované s .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="ab919-122">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="ab919-123">Výchozí jazyk pro šablonu se zobrazí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="ab919-123">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="ab919-124">Kliknutím na odkaz krátké jméno zobrazíte konkrétní možnosti šablony.</span><span class="sxs-lookup"><span data-stu-id="ab919-124">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="ab919-125">Šablony</span><span class="sxs-lookup"><span data-stu-id="ab919-125">Templates</span></span>                                    | <span data-ttu-id="ab919-126">Krátký název</span><span class="sxs-lookup"><span data-stu-id="ab919-126">Short name</span></span>                      | <span data-ttu-id="ab919-127">Jazyk</span><span class="sxs-lookup"><span data-stu-id="ab919-127">Language</span></span>     | <span data-ttu-id="ab919-128">Značky</span><span class="sxs-lookup"><span data-stu-id="ab919-128">Tags</span></span>                                  | <span data-ttu-id="ab919-129">Vedou</span><span class="sxs-lookup"><span data-stu-id="ab919-129">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="ab919-130">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="ab919-130">Console Application</span></span>                          | [<span data-ttu-id="ab919-131">stromu</span><span class="sxs-lookup"><span data-stu-id="ab919-131">console</span></span>](#console)             | <span data-ttu-id="ab919-132">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="ab919-132">[C#], F#, VB</span></span> | <span data-ttu-id="ab919-133">Společná/konzola</span><span class="sxs-lookup"><span data-stu-id="ab919-133">Common/Console</span></span>                        | <span data-ttu-id="ab919-134">1.0</span><span class="sxs-lookup"><span data-stu-id="ab919-134">1.0</span></span>        |
| <span data-ttu-id="ab919-135">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="ab919-135">Class library</span></span>                                | [<span data-ttu-id="ab919-136">že knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="ab919-136">classlib</span></span>](#classlib)           | <span data-ttu-id="ab919-137">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="ab919-137">[C#], F#, VB</span></span> | <span data-ttu-id="ab919-138">Společné/knihovny</span><span class="sxs-lookup"><span data-stu-id="ab919-138">Common/Library</span></span>                        | <span data-ttu-id="ab919-139">1.0</span><span class="sxs-lookup"><span data-stu-id="ab919-139">1.0</span></span>        |
| <span data-ttu-id="ab919-140">Aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="ab919-140">WPF Application</span></span>                              | [<span data-ttu-id="ab919-141">subsystém</span><span class="sxs-lookup"><span data-stu-id="ab919-141">wpf</span></span>](#wpf)                     | <span data-ttu-id="ab919-142">Jazyk</span><span class="sxs-lookup"><span data-stu-id="ab919-142">[C#]</span></span>         | <span data-ttu-id="ab919-143">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="ab919-143">Common/WPF</span></span>                            | <span data-ttu-id="ab919-144">3.0</span><span class="sxs-lookup"><span data-stu-id="ab919-144">3.0</span></span>        |
| <span data-ttu-id="ab919-145">WPF – knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="ab919-145">WPF Class library</span></span>                            | [<span data-ttu-id="ab919-146">wpflib</span><span class="sxs-lookup"><span data-stu-id="ab919-146">wpflib</span></span>](#wpf)                  | <span data-ttu-id="ab919-147">Jazyk</span><span class="sxs-lookup"><span data-stu-id="ab919-147">[C#]</span></span>         | <span data-ttu-id="ab919-148">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="ab919-148">Common/WPF</span></span>                            | <span data-ttu-id="ab919-149">3.0</span><span class="sxs-lookup"><span data-stu-id="ab919-149">3.0</span></span>        |
| <span data-ttu-id="ab919-150">Knihovna vlastních ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="ab919-150">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="ab919-151">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="ab919-151">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="ab919-152">Jazyk</span><span class="sxs-lookup"><span data-stu-id="ab919-152">[C#]</span></span>         | <span data-ttu-id="ab919-153">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="ab919-153">Common/WPF</span></span>                            | <span data-ttu-id="ab919-154">3.0</span><span class="sxs-lookup"><span data-stu-id="ab919-154">3.0</span></span>        |
| <span data-ttu-id="ab919-155">Knihovna uživatelských ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="ab919-155">WPF User Control Library</span></span>                     | [<span data-ttu-id="ab919-156">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="ab919-156">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="ab919-157">Jazyk</span><span class="sxs-lookup"><span data-stu-id="ab919-157">[C#]</span></span>         | <span data-ttu-id="ab919-158">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="ab919-158">Common/WPF</span></span>                            | <span data-ttu-id="ab919-159">3.0</span><span class="sxs-lookup"><span data-stu-id="ab919-159">3.0</span></span>        |
| <span data-ttu-id="ab919-160">Aplikace model Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="ab919-160">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="ab919-161">WinForms</span><span class="sxs-lookup"><span data-stu-id="ab919-161">winforms</span></span>](#winforms)           | <span data-ttu-id="ab919-162">Jazyk</span><span class="sxs-lookup"><span data-stu-id="ab919-162">[C#]</span></span>         | <span data-ttu-id="ab919-163">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="ab919-163">Common/WinForms</span></span>                       | <span data-ttu-id="ab919-164">3.0</span><span class="sxs-lookup"><span data-stu-id="ab919-164">3.0</span></span>        |
| <span data-ttu-id="ab919-165">Knihovna tříd model Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="ab919-165">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="ab919-166">winformslib</span><span class="sxs-lookup"><span data-stu-id="ab919-166">winformslib</span></span>](#winforms)        | <span data-ttu-id="ab919-167">Jazyk</span><span class="sxs-lookup"><span data-stu-id="ab919-167">[C#]</span></span>         | <span data-ttu-id="ab919-168">Common/WinForms</span><span class="sxs-lookup"><span data-stu-id="ab919-168">Common/WinForms</span></span>                       | <span data-ttu-id="ab919-169">3.0</span><span class="sxs-lookup"><span data-stu-id="ab919-169">3.0</span></span>        |
| <span data-ttu-id="ab919-170">Služba pracovního procesu</span><span class="sxs-lookup"><span data-stu-id="ab919-170">Worker Service</span></span>                               | [<span data-ttu-id="ab919-171">zaměstnanec</span><span class="sxs-lookup"><span data-stu-id="ab919-171">worker</span></span>](#web-others)           | <span data-ttu-id="ab919-172">Jazyk</span><span class="sxs-lookup"><span data-stu-id="ab919-172">[C#]</span></span>         | <span data-ttu-id="ab919-173">Common/Work/Web</span><span class="sxs-lookup"><span data-stu-id="ab919-173">Common/Worker/Web</span></span>                     | <span data-ttu-id="ab919-174">3.0</span><span class="sxs-lookup"><span data-stu-id="ab919-174">3.0</span></span>        |
| <span data-ttu-id="ab919-175">Projekt testu jednotek</span><span class="sxs-lookup"><span data-stu-id="ab919-175">Unit Test Project</span></span>                            | [<span data-ttu-id="ab919-176">MSTest</span><span class="sxs-lookup"><span data-stu-id="ab919-176">mstest</span></span>](#test)                 | <span data-ttu-id="ab919-177">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="ab919-177">[C#], F#, VB</span></span> | <span data-ttu-id="ab919-178">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="ab919-178">Test/MSTest</span></span>                           | <span data-ttu-id="ab919-179">1.0</span><span class="sxs-lookup"><span data-stu-id="ab919-179">1.0</span></span>        |
| <span data-ttu-id="ab919-180">Projekt testů NUnit 3</span><span class="sxs-lookup"><span data-stu-id="ab919-180">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="ab919-181">nunit</span><span class="sxs-lookup"><span data-stu-id="ab919-181">nunit</span></span>](#nunit)                  | <span data-ttu-id="ab919-182">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="ab919-182">[C#], F#, VB</span></span> | <span data-ttu-id="ab919-183">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="ab919-183">Test/NUnit</span></span>                            | <span data-ttu-id="ab919-184">2.1.400</span><span class="sxs-lookup"><span data-stu-id="ab919-184">2.1.400</span></span>    |
| <span data-ttu-id="ab919-185">NUnit 3 položka testu</span><span class="sxs-lookup"><span data-stu-id="ab919-185">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="ab919-186">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="ab919-186">[C#], F#, VB</span></span> | <span data-ttu-id="ab919-187">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="ab919-187">Test/NUnit</span></span>                            | <span data-ttu-id="ab919-188">2,2</span><span class="sxs-lookup"><span data-stu-id="ab919-188">2.2</span></span>        |
| <span data-ttu-id="ab919-189">Projekt testů xUnit</span><span class="sxs-lookup"><span data-stu-id="ab919-189">xUnit Test Project</span></span>                           | [<span data-ttu-id="ab919-190">xUnit</span><span class="sxs-lookup"><span data-stu-id="ab919-190">xunit</span></span>](#test)                  | <span data-ttu-id="ab919-191">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="ab919-191">[C#], F#, VB</span></span> | <span data-ttu-id="ab919-192">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="ab919-192">Test/xUnit</span></span>                            | <span data-ttu-id="ab919-193">1.0</span><span class="sxs-lookup"><span data-stu-id="ab919-193">1.0</span></span>        |
| <span data-ttu-id="ab919-194">Komponenta Razor</span><span class="sxs-lookup"><span data-stu-id="ab919-194">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="ab919-195">Jazyk</span><span class="sxs-lookup"><span data-stu-id="ab919-195">[C#]</span></span>         | <span data-ttu-id="ab919-196">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="ab919-196">Web/ASP.NET</span></span>                           | <span data-ttu-id="ab919-197">3.0</span><span class="sxs-lookup"><span data-stu-id="ab919-197">3.0</span></span>        |
| <span data-ttu-id="ab919-198">Stránka Razor</span><span class="sxs-lookup"><span data-stu-id="ab919-198">Razor Page</span></span>                                   | [<span data-ttu-id="ab919-199">Page</span><span class="sxs-lookup"><span data-stu-id="ab919-199">page</span></span>](#page)                   | <span data-ttu-id="ab919-200">Jazyk</span><span class="sxs-lookup"><span data-stu-id="ab919-200">[C#]</span></span>         | <span data-ttu-id="ab919-201">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="ab919-201">Web/ASP.NET</span></span>                           | <span data-ttu-id="ab919-202">2.0</span><span class="sxs-lookup"><span data-stu-id="ab919-202">2.0</span></span>        |
| <span data-ttu-id="ab919-203">ViewImports MVC</span><span class="sxs-lookup"><span data-stu-id="ab919-203">MVC ViewImports</span></span>                              | [<span data-ttu-id="ab919-204">viewimports</span><span class="sxs-lookup"><span data-stu-id="ab919-204">viewimports</span></span>](#namespace)       | <span data-ttu-id="ab919-205">Jazyk</span><span class="sxs-lookup"><span data-stu-id="ab919-205">[C#]</span></span>         | <span data-ttu-id="ab919-206">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="ab919-206">Web/ASP.NET</span></span>                           | <span data-ttu-id="ab919-207">2.0</span><span class="sxs-lookup"><span data-stu-id="ab919-207">2.0</span></span>        |
| <span data-ttu-id="ab919-208">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="ab919-208">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="ab919-209">Jazyk</span><span class="sxs-lookup"><span data-stu-id="ab919-209">[C#]</span></span>         | <span data-ttu-id="ab919-210">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="ab919-210">Web/ASP.NET</span></span>                           | <span data-ttu-id="ab919-211">2.0</span><span class="sxs-lookup"><span data-stu-id="ab919-211">2.0</span></span>        |
| <span data-ttu-id="ab919-212">Aplikace serveru Blazor</span><span class="sxs-lookup"><span data-stu-id="ab919-212">Blazor Server App</span></span>                            | [<span data-ttu-id="ab919-213">blazorserver</span><span class="sxs-lookup"><span data-stu-id="ab919-213">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="ab919-214">Jazyk</span><span class="sxs-lookup"><span data-stu-id="ab919-214">[C#]</span></span>         | <span data-ttu-id="ab919-215">Web/Blazor</span><span class="sxs-lookup"><span data-stu-id="ab919-215">Web/Blazor</span></span>                            | <span data-ttu-id="ab919-216">3.0</span><span class="sxs-lookup"><span data-stu-id="ab919-216">3.0</span></span>        |
| <span data-ttu-id="ab919-217">Aplikace WebAssembly v Blazor</span><span class="sxs-lookup"><span data-stu-id="ab919-217">Blazor WebAssembly App</span></span>                       | `blazorwasm`                    | <span data-ttu-id="ab919-218">Jazyk</span><span class="sxs-lookup"><span data-stu-id="ab919-218">[C#]</span></span>         | <span data-ttu-id="ab919-219">Web/Blazor/WebAssembly</span><span class="sxs-lookup"><span data-stu-id="ab919-219">Web/Blazor/WebAssembly</span></span>                            | <span data-ttu-id="ab919-220">3.1.300</span><span class="sxs-lookup"><span data-stu-id="ab919-220">3.1.300</span></span>    |
| <span data-ttu-id="ab919-221">ASP.NET Core prázdné</span><span class="sxs-lookup"><span data-stu-id="ab919-221">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="ab919-222">webovém</span><span class="sxs-lookup"><span data-stu-id="ab919-222">web</span></span>](#web)                     | <span data-ttu-id="ab919-223">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="ab919-223">[C#], F#</span></span>     | <span data-ttu-id="ab919-224">Web/prázdné</span><span class="sxs-lookup"><span data-stu-id="ab919-224">Web/Empty</span></span>                             | <span data-ttu-id="ab919-225">1.0</span><span class="sxs-lookup"><span data-stu-id="ab919-225">1.0</span></span>        |
| <span data-ttu-id="ab919-226">ASP.NET Core webová aplikace (model-zobrazení-kontroler)</span><span class="sxs-lookup"><span data-stu-id="ab919-226">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="ab919-227">Návrhový</span><span class="sxs-lookup"><span data-stu-id="ab919-227">mvc</span></span>](#web-options)             | <span data-ttu-id="ab919-228">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="ab919-228">[C#], F#</span></span>     | <span data-ttu-id="ab919-229">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="ab919-229">Web/MVC</span></span>                               | <span data-ttu-id="ab919-230">1.0</span><span class="sxs-lookup"><span data-stu-id="ab919-230">1.0</span></span>        |
| <span data-ttu-id="ab919-231">ASP.NET Core webové aplikace</span><span class="sxs-lookup"><span data-stu-id="ab919-231">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="ab919-232">WebApp, Razor</span><span class="sxs-lookup"><span data-stu-id="ab919-232">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="ab919-233">Jazyk</span><span class="sxs-lookup"><span data-stu-id="ab919-233">[C#]</span></span>         | <span data-ttu-id="ab919-234">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="ab919-234">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="ab919-235">2,2, 2,0</span><span class="sxs-lookup"><span data-stu-id="ab919-235">2.2, 2.0</span></span>   |
| <span data-ttu-id="ab919-236">ASP.NET Core s úhlovým</span><span class="sxs-lookup"><span data-stu-id="ab919-236">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="ab919-237">Angular</span><span class="sxs-lookup"><span data-stu-id="ab919-237">angular</span></span>](#spa)                 | <span data-ttu-id="ab919-238">Jazyk</span><span class="sxs-lookup"><span data-stu-id="ab919-238">[C#]</span></span>         | <span data-ttu-id="ab919-239">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="ab919-239">Web/MVC/SPA</span></span>                           | <span data-ttu-id="ab919-240">2.0</span><span class="sxs-lookup"><span data-stu-id="ab919-240">2.0</span></span>        |
| <span data-ttu-id="ab919-241">ASP.NET Core s reagují. js</span><span class="sxs-lookup"><span data-stu-id="ab919-241">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="ab919-242">reaguje</span><span class="sxs-lookup"><span data-stu-id="ab919-242">react</span></span>](#spa)                   | <span data-ttu-id="ab919-243">Jazyk</span><span class="sxs-lookup"><span data-stu-id="ab919-243">[C#]</span></span>         | <span data-ttu-id="ab919-244">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="ab919-244">Web/MVC/SPA</span></span>                           | <span data-ttu-id="ab919-245">2.0</span><span class="sxs-lookup"><span data-stu-id="ab919-245">2.0</span></span>        |
| <span data-ttu-id="ab919-246">ASP.NET Core s využitím reagují. js a Redux</span><span class="sxs-lookup"><span data-stu-id="ab919-246">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="ab919-247">reactredux</span><span class="sxs-lookup"><span data-stu-id="ab919-247">reactredux</span></span>](#reactredux)       | <span data-ttu-id="ab919-248">Jazyk</span><span class="sxs-lookup"><span data-stu-id="ab919-248">[C#]</span></span>         | <span data-ttu-id="ab919-249">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="ab919-249">Web/MVC/SPA</span></span>                           | <span data-ttu-id="ab919-250">2.0</span><span class="sxs-lookup"><span data-stu-id="ab919-250">2.0</span></span>        |
| <span data-ttu-id="ab919-251">Knihovna tříd Razor</span><span class="sxs-lookup"><span data-stu-id="ab919-251">Razor Class Library</span></span>                          | [<span data-ttu-id="ab919-252">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="ab919-252">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="ab919-253">Jazyk</span><span class="sxs-lookup"><span data-stu-id="ab919-253">[C#]</span></span>         | <span data-ttu-id="ab919-254">Knihovna tříd web/Razor/Library/Razor</span><span class="sxs-lookup"><span data-stu-id="ab919-254">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="ab919-255">2.1</span><span class="sxs-lookup"><span data-stu-id="ab919-255">2.1</span></span>        |
| <span data-ttu-id="ab919-256">Webové rozhraní API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ab919-256">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="ab919-257">WebApi</span><span class="sxs-lookup"><span data-stu-id="ab919-257">webapi</span></span>](#webapi)               | <span data-ttu-id="ab919-258">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="ab919-258">[C#], F#</span></span>     | <span data-ttu-id="ab919-259">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="ab919-259">Web/WebAPI</span></span>                            | <span data-ttu-id="ab919-260">1.0</span><span class="sxs-lookup"><span data-stu-id="ab919-260">1.0</span></span>        |
| <span data-ttu-id="ab919-261">Služba ASP.NET Core gRPC</span><span class="sxs-lookup"><span data-stu-id="ab919-261">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="ab919-262">grpc</span><span class="sxs-lookup"><span data-stu-id="ab919-262">grpc</span></span>](#web-others)             | <span data-ttu-id="ab919-263">Jazyk</span><span class="sxs-lookup"><span data-stu-id="ab919-263">[C#]</span></span>         | <span data-ttu-id="ab919-264">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="ab919-264">Web/gRPC</span></span>                              | <span data-ttu-id="ab919-265">3.0</span><span class="sxs-lookup"><span data-stu-id="ab919-265">3.0</span></span>        |
| <span data-ttu-id="ab919-266">soubor dotnet gitignore</span><span class="sxs-lookup"><span data-stu-id="ab919-266">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="ab919-267">Config</span><span class="sxs-lookup"><span data-stu-id="ab919-267">Config</span></span>                                | <span data-ttu-id="ab919-268">3.0</span><span class="sxs-lookup"><span data-stu-id="ab919-268">3.0</span></span>        |
| <span data-ttu-id="ab919-269">soubor Global. JSON</span><span class="sxs-lookup"><span data-stu-id="ab919-269">global.json file</span></span>                             | [<span data-ttu-id="ab919-270">globaljson</span><span class="sxs-lookup"><span data-stu-id="ab919-270">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="ab919-271">Config</span><span class="sxs-lookup"><span data-stu-id="ab919-271">Config</span></span>                                | <span data-ttu-id="ab919-272">2.0</span><span class="sxs-lookup"><span data-stu-id="ab919-272">2.0</span></span>        |
| <span data-ttu-id="ab919-273">Konfigurace NuGet</span><span class="sxs-lookup"><span data-stu-id="ab919-273">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="ab919-274">Config</span><span class="sxs-lookup"><span data-stu-id="ab919-274">Config</span></span>                                | <span data-ttu-id="ab919-275">1.0</span><span class="sxs-lookup"><span data-stu-id="ab919-275">1.0</span></span>        |
| <span data-ttu-id="ab919-276">Dotnet – místní nástroj soubor manifestu</span><span class="sxs-lookup"><span data-stu-id="ab919-276">Dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="ab919-277">Config</span><span class="sxs-lookup"><span data-stu-id="ab919-277">Config</span></span>                                | <span data-ttu-id="ab919-278">3.0</span><span class="sxs-lookup"><span data-stu-id="ab919-278">3.0</span></span>        |
| <span data-ttu-id="ab919-279">Webová konfigurace</span><span class="sxs-lookup"><span data-stu-id="ab919-279">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="ab919-280">Config</span><span class="sxs-lookup"><span data-stu-id="ab919-280">Config</span></span>                                | <span data-ttu-id="ab919-281">1.0</span><span class="sxs-lookup"><span data-stu-id="ab919-281">1.0</span></span>        |
| <span data-ttu-id="ab919-282">Soubor řešení</span><span class="sxs-lookup"><span data-stu-id="ab919-282">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="ab919-283">Řešení</span><span class="sxs-lookup"><span data-stu-id="ab919-283">Solution</span></span>                              | <span data-ttu-id="ab919-284">1.0</span><span class="sxs-lookup"><span data-stu-id="ab919-284">1.0</span></span>        |
| <span data-ttu-id="ab919-285">Soubor vyrovnávací paměti protokolu</span><span class="sxs-lookup"><span data-stu-id="ab919-285">Protocol Buffer File</span></span>                         | [<span data-ttu-id="ab919-286">proto</span><span class="sxs-lookup"><span data-stu-id="ab919-286">proto</span></span>](#namespace)             |              | <span data-ttu-id="ab919-287">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="ab919-287">Web/gRPC</span></span>                              | <span data-ttu-id="ab919-288">3.0</span><span class="sxs-lookup"><span data-stu-id="ab919-288">3.0</span></span>        |

## <a name="options"></a><span data-ttu-id="ab919-289">Možnosti</span><span class="sxs-lookup"><span data-stu-id="ab919-289">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="ab919-290">Zobrazí souhrnné informace o tom, co se stane, pokud by došlo ke spuštění daného příkazu, pokud by to vedlo k vytvoření šablony.</span><span class="sxs-lookup"><span data-stu-id="ab919-290">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span> <span data-ttu-id="ab919-291">K dispozici od verze .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="ab919-291">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="ab919-292">Vynutí vygenerování obsahu i v případě, že změní existující soubory.</span><span class="sxs-lookup"><span data-stu-id="ab919-292">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="ab919-293">Tato možnost je vyžadována, pokud by vybraná šablona přepsala existující soubory ve výstupním adresáři.</span><span class="sxs-lookup"><span data-stu-id="ab919-293">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="ab919-294">Vytiskne nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="ab919-294">Prints out help for the command.</span></span> <span data-ttu-id="ab919-295">Dá se vyvolat pro `dotnet new` samotný příkaz nebo pro libovolnou šablonu.</span><span class="sxs-lookup"><span data-stu-id="ab919-295">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="ab919-296">Například, `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="ab919-296">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="ab919-297">Nainstaluje sadu šablon z `PATH` nebo `NUGET_ID` poskytnuté.</span><span class="sxs-lookup"><span data-stu-id="ab919-297">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="ab919-298">Pokud chcete nainstalovat předprodejní verzi balíčku šablony, je nutné zadat verzi ve formátu `<package-name>::<package-version>` .</span><span class="sxs-lookup"><span data-stu-id="ab919-298">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="ab919-299">Ve výchozím nastavení se `dotnet new` předá \* verze, která představuje nejnovější stabilní verzi balíčku.</span><span class="sxs-lookup"><span data-stu-id="ab919-299">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="ab919-300">Podívejte se na příklad v části [Příklady](#examples) .</span><span class="sxs-lookup"><span data-stu-id="ab919-300">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="ab919-301">Pokud byla verze šablony již nainstalována při spuštění tohoto příkazu, šablona bude aktualizována na určenou verzi nebo na nejnovější stabilní verzi, pokud nebyla zadána žádná verze.</span><span class="sxs-lookup"><span data-stu-id="ab919-301">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="ab919-302">Informace o vytváření vlastních šablon najdete v tématu [vlastní šablony pro dotnet New](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="ab919-302">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="ab919-303">Vypíše seznam šablon, které obsahují zadaný název.</span><span class="sxs-lookup"><span data-stu-id="ab919-303">Lists templates containing the specified name.</span></span> <span data-ttu-id="ab919-304">Pokud není zadán žádný název, vypíše všechny šablony.</span><span class="sxs-lookup"><span data-stu-id="ab919-304">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="ab919-305">Jazyk šablony, která se má vytvořit</span><span class="sxs-lookup"><span data-stu-id="ab919-305">The language of the template to create.</span></span> <span data-ttu-id="ab919-306">Přijatý jazyk se liší podle šablony (viz výchozí hodnoty v oddílu [argumenty](#arguments) ).</span><span class="sxs-lookup"><span data-stu-id="ab919-306">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="ab919-307">Pro některé šablony není platná.</span><span class="sxs-lookup"><span data-stu-id="ab919-307">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="ab919-308">Některá prostředí jsou interpretována `#` jako speciální znak.</span><span class="sxs-lookup"><span data-stu-id="ab919-308">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="ab919-309">V těchto případech uveďte hodnotu parametru Language v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="ab919-309">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="ab919-310">Například, `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="ab919-310">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="ab919-311">Název vytvořeného výstupu.</span><span class="sxs-lookup"><span data-stu-id="ab919-311">The name for the created output.</span></span> <span data-ttu-id="ab919-312">Pokud název nezadáte, použije se název aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="ab919-312">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="ab919-313">Určuje zdroj NuGet, který se použije při instalaci.</span><span class="sxs-lookup"><span data-stu-id="ab919-313">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="ab919-314">K dispozici od verze .NET Core 2,1 SDK.</span><span class="sxs-lookup"><span data-stu-id="ab919-314">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="ab919-315">Umístění, do kterého se má vygenerovaný výstup umístit.</span><span class="sxs-lookup"><span data-stu-id="ab919-315">Location to place the generated output.</span></span> <span data-ttu-id="ab919-316">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="ab919-316">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="ab919-317">Filtruje šablony založené na dostupných typech.</span><span class="sxs-lookup"><span data-stu-id="ab919-317">Filters templates based on available types.</span></span> <span data-ttu-id="ab919-318">Předdefinované hodnoty jsou `project` , `item` a `other` .</span><span class="sxs-lookup"><span data-stu-id="ab919-318">Predefined values are `project`, `item`, and `other`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="ab919-319">Odinstaluje sadu šablon na `PATH` nebo `NUGET_ID` poskytnutou.</span><span class="sxs-lookup"><span data-stu-id="ab919-319">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="ab919-320">Pokud `<PATH|NUGET_ID>` hodnota není zadaná, zobrazí se všechny aktuálně nainstalované sady šablon a jejich přidružené šablony.</span><span class="sxs-lookup"><span data-stu-id="ab919-320">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="ab919-321">Při zadávání nezahrnujte `NUGET_ID` číslo verze.</span><span class="sxs-lookup"><span data-stu-id="ab919-321">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="ab919-322">Pokud neurčíte parametr této možnosti, příkaz zobrazí seznam nainstalovaných šablon a podrobností.</span><span class="sxs-lookup"><span data-stu-id="ab919-322">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="ab919-323">Chcete-li odinstalovat šablonu pomocí nástroje `PATH` , je nutné plně kvalifikovat cestu.</span><span class="sxs-lookup"><span data-stu-id="ab919-323">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="ab919-324">Například *C:/Users/ \<USER> /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z nadřazené složky to nebude.</span><span class="sxs-lookup"><span data-stu-id="ab919-324">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="ab919-325">Do cesty k šabloně nezahrnujte konečné koncové lomítko adresáře.</span><span class="sxs-lookup"><span data-stu-id="ab919-325">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="ab919-326">Kontroluje, zda jsou k dispozici aktualizace pro sady šablon, které jsou aktuálně nainstalovány a instalovány.</span><span class="sxs-lookup"><span data-stu-id="ab919-326">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="ab919-327">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ab919-327">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="ab919-328">Kontroluje, zda jsou k dispozici aktualizace pro sady šablon, které jsou aktuálně nainstalovány.</span><span class="sxs-lookup"><span data-stu-id="ab919-328">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="ab919-329">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ab919-329">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="ab919-330">Možnosti šablon</span><span class="sxs-lookup"><span data-stu-id="ab919-330">Template options</span></span>

<span data-ttu-id="ab919-331">Každá šablona projektu může mít k dispozici další možnosti.</span><span class="sxs-lookup"><span data-stu-id="ab919-331">Each project template may have additional options available.</span></span> <span data-ttu-id="ab919-332">Základní šablony mají následující další možnosti:</span><span class="sxs-lookup"><span data-stu-id="ab919-332">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="ab919-333">konzola</span><span class="sxs-lookup"><span data-stu-id="ab919-333">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ab919-334">Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="ab919-334">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ab919-335">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ab919-335">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="ab919-336">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, který používáte:</span><span class="sxs-lookup"><span data-stu-id="ab919-336">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ab919-337">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="ab919-337">SDK version</span></span> | <span data-ttu-id="ab919-338">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="ab919-338">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ab919-339">3.1</span><span class="sxs-lookup"><span data-stu-id="ab919-339">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ab919-340">3.0</span><span class="sxs-lookup"><span data-stu-id="ab919-340">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="ab919-341">Nastaví `LangVersion` vlastnost v souboru vytvořeného projektu.</span><span class="sxs-lookup"><span data-stu-id="ab919-341">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="ab919-342">Například použijte `--langVersion 7.3` k použití jazyka C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="ab919-342">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="ab919-343">Nepodporováno v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="ab919-343">Not supported for F#.</span></span> <span data-ttu-id="ab919-344">K dispozici od verze .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="ab919-344">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="ab919-345">Seznam výchozích verzí jazyka C# naleznete v tématu [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="ab919-345">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="ab919-346">Je-li tento parametr zadán, nespustí při vytváření projektu implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="ab919-346">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="ab919-347">K dispozici od verze .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="ab919-347">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="ab919-348">že knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="ab919-348">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ab919-349">Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="ab919-349">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ab919-350">Hodnoty: `netcoreapp<version>` pro vytvoření knihovny tříd .NET Core nebo `netstandard<version>` pro vytvoření knihovny tříd .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="ab919-350">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="ab919-351">Výchozí hodnota je `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="ab919-351">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="ab919-352">Nastaví `LangVersion` vlastnost v souboru vytvořeného projektu.</span><span class="sxs-lookup"><span data-stu-id="ab919-352">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="ab919-353">Například použijte `--langVersion 7.3` k použití jazyka C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="ab919-353">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="ab919-354">Nepodporováno v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="ab919-354">Not supported for F#.</span></span> <span data-ttu-id="ab919-355">K dispozici od verze .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="ab919-355">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="ab919-356">Seznam výchozích verzí jazyka C# naleznete v tématu [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="ab919-356">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="ab919-357">Při vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="ab919-357">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a><span data-ttu-id="ab919-358">WPF, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="ab919-358">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ab919-359">Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="ab919-359">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ab919-360">Výchozí hodnota je `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="ab919-360">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="ab919-361">K dispozici od verze .NET Core 3,1 SDK.</span><span class="sxs-lookup"><span data-stu-id="ab919-361">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="ab919-362">Nastaví `LangVersion` vlastnost v souboru vytvořeného projektu.</span><span class="sxs-lookup"><span data-stu-id="ab919-362">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="ab919-363">Například použijte `--langVersion 7.3` k použití jazyka C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="ab919-363">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="ab919-364">Seznam výchozích verzí jazyka C# naleznete v tématu [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="ab919-364">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="ab919-365">Při vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="ab919-365">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms-winformslib"></a><a name="winforms"></a><span data-ttu-id="ab919-366">WinForms, winformslib</span><span class="sxs-lookup"><span data-stu-id="ab919-366">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="ab919-367">Nastaví `LangVersion` vlastnost v souboru vytvořeného projektu.</span><span class="sxs-lookup"><span data-stu-id="ab919-367">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="ab919-368">Například použijte `--langVersion 7.3` k použití jazyka C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="ab919-368">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="ab919-369">Seznam výchozích verzí jazyka C# naleznete v tématu [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="ab919-369">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="ab919-370">Při vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="ab919-370">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="worker-grpc"></a><a name="web-others"></a><span data-ttu-id="ab919-371">pracovní proces, grpc</span><span class="sxs-lookup"><span data-stu-id="ab919-371">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ab919-372">Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="ab919-372">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ab919-373">Výchozí hodnota je `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="ab919-373">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="ab919-374">K dispozici od verze .NET Core 3,1 SDK.</span><span class="sxs-lookup"><span data-stu-id="ab919-374">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="ab919-375">Vyloučí z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="ab919-375">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="ab919-376">Při vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="ab919-376">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="mstest-xunit"></a><a name="test"></a><span data-ttu-id="ab919-377">MSTest, xUnit</span><span class="sxs-lookup"><span data-stu-id="ab919-377">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ab919-378">Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="ab919-378">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ab919-379">Možnost je k dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ab919-379">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="ab919-380">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, který používáte:</span><span class="sxs-lookup"><span data-stu-id="ab919-380">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ab919-381">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="ab919-381">SDK version</span></span> | <span data-ttu-id="ab919-382">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="ab919-382">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ab919-383">3.1</span><span class="sxs-lookup"><span data-stu-id="ab919-383">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ab919-384">3.0</span><span class="sxs-lookup"><span data-stu-id="ab919-384">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="ab919-385">Umožňuje sbalení pro projekt pomocí [sady dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="ab919-385">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="ab919-386">Při vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="ab919-386">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="ab919-387">nunit</span><span class="sxs-lookup"><span data-stu-id="ab919-387">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ab919-388">Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="ab919-388">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="ab919-389">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, který používáte:</span><span class="sxs-lookup"><span data-stu-id="ab919-389">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ab919-390">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="ab919-390">SDK version</span></span> | <span data-ttu-id="ab919-391">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="ab919-391">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ab919-392">3.1</span><span class="sxs-lookup"><span data-stu-id="ab919-392">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ab919-393">3.0</span><span class="sxs-lookup"><span data-stu-id="ab919-393">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="ab919-394">2,2</span><span class="sxs-lookup"><span data-stu-id="ab919-394">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="ab919-395">2.1</span><span class="sxs-lookup"><span data-stu-id="ab919-395">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="ab919-396">Umožňuje sbalení pro projekt pomocí [sady dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="ab919-396">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="ab919-397">Při vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="ab919-397">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="ab919-398">Page</span><span class="sxs-lookup"><span data-stu-id="ab919-398">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="ab919-399">Obor názvů pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="ab919-399">Namespace for the generated code.</span></span> <span data-ttu-id="ab919-400">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="ab919-400">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="ab919-401">Vytvoří stránku bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="ab919-401">Creates the page without a PageModel.</span></span>

***

### <a name="viewimports-proto"></a><a name="namespace"></a><span data-ttu-id="ab919-402">viewimports, a proto</span><span class="sxs-lookup"><span data-stu-id="ab919-402">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="ab919-403">Obor názvů pro vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="ab919-403">Namespace for the generated code.</span></span> <span data-ttu-id="ab919-404">Výchozí hodnota je `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="ab919-404">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="ab919-405">blazorserver</span><span class="sxs-lookup"><span data-stu-id="ab919-405">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="ab919-406">Typ ověřování, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="ab919-406">The type of authentication to use.</span></span> <span data-ttu-id="ab919-407">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="ab919-407">The possible values are:</span></span>

  - <span data-ttu-id="ab919-408">`None`-Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="ab919-408">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="ab919-409">`Individual`-Individuální ověřování.</span><span class="sxs-lookup"><span data-stu-id="ab919-409">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="ab919-410">`IndividualB2C`-Jednotlivá ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="ab919-410">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="ab919-411">`SingleOrg`– Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="ab919-411">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="ab919-412">`MultiOrg`– Ověřování organizace pro více tenantů.</span><span class="sxs-lookup"><span data-stu-id="ab919-412">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="ab919-413">`Windows`– Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="ab919-413">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="ab919-414">Instance Azure Active Directory B2C pro připojení.</span><span class="sxs-lookup"><span data-stu-id="ab919-414">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ab919-415">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="ab919-415">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ab919-416">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="ab919-416">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="ab919-417">ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="ab919-417">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ab919-418">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="ab919-418">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="ab919-419">ID zásad pro resetování hesla pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="ab919-419">The reset password policy ID for this project.</span></span> <span data-ttu-id="ab919-420">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="ab919-420">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="ab919-421">Upravit ID zásad profilu pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="ab919-421">The edit profile policy ID for this project.</span></span> <span data-ttu-id="ab919-422">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="ab919-422">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="ab919-423">Instance Azure Active Directory pro připojení.</span><span class="sxs-lookup"><span data-stu-id="ab919-423">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ab919-424">Použijte s `SingleOrg` `MultiOrg` ověřováním nebo.</span><span class="sxs-lookup"><span data-stu-id="ab919-424">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="ab919-425">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="ab919-425">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="ab919-426">ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="ab919-426">The Client ID for this project.</span></span> <span data-ttu-id="ab919-427">Použijte s `IndividualB2C` `SingleOrg` `MultiOrg` ověřováním, nebo.</span><span class="sxs-lookup"><span data-stu-id="ab919-427">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="ab919-428">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="ab919-428">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="ab919-429">Doména pro tenanta adresáře.</span><span class="sxs-lookup"><span data-stu-id="ab919-429">The domain for the directory tenant.</span></span> <span data-ttu-id="ab919-430">Použijte s `SingleOrg` `IndividualB2C` ověřováním nebo.</span><span class="sxs-lookup"><span data-stu-id="ab919-430">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ab919-431">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="ab919-431">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="ab919-432">ID TenantId adresáře, ke kterému se má připojit.</span><span class="sxs-lookup"><span data-stu-id="ab919-432">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ab919-433">Použijte s `SingleOrg` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="ab919-433">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ab919-434">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="ab919-434">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="ab919-435">Cesta požadavku v základní cestě identifikátoru URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="ab919-435">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="ab919-436">Použijte s `SingleOrg` `IndividualB2C` ověřováním nebo.</span><span class="sxs-lookup"><span data-stu-id="ab919-436">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ab919-437">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="ab919-437">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="ab919-438">Povolí této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="ab919-438">Allows this application read-access to the directory.</span></span> <span data-ttu-id="ab919-439">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ab919-439">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="ab919-440">Vyloučí z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="ab919-440">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="ab919-441">Vypne protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ab919-441">Turns off HTTPS.</span></span> <span data-ttu-id="ab919-442">Tato možnost platí pouze v případě, že se `Individual` `IndividualB2C` `SingleOrg` `MultiOrg` nepoužívá pro `--auth` .</span><span class="sxs-lookup"><span data-stu-id="ab919-442">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="ab919-443">Určuje, že se má místo SQLite použít LocalDB.</span><span class="sxs-lookup"><span data-stu-id="ab919-443">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ab919-444">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ab919-444">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="ab919-445">Při vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="ab919-445">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="ab919-446">web</span><span class="sxs-lookup"><span data-stu-id="ab919-446">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="ab919-447">Vyloučí z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="ab919-447">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ab919-448">Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="ab919-448">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ab919-449">Možnost není dostupná v sadě .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="ab919-449">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="ab919-450">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, který používáte:</span><span class="sxs-lookup"><span data-stu-id="ab919-450">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ab919-451">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="ab919-451">SDK version</span></span> | <span data-ttu-id="ab919-452">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="ab919-452">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ab919-453">3.1</span><span class="sxs-lookup"><span data-stu-id="ab919-453">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ab919-454">3.0</span><span class="sxs-lookup"><span data-stu-id="ab919-454">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="ab919-455">2.1</span><span class="sxs-lookup"><span data-stu-id="ab919-455">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="ab919-456">Při vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="ab919-456">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="ab919-457">Vypne protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ab919-457">Turns off HTTPS.</span></span>

***

### <a name="mvc-webapp"></a><a name="web-options"></a><span data-ttu-id="ab919-458">MVC, WebApp</span><span class="sxs-lookup"><span data-stu-id="ab919-458">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="ab919-459">Typ ověřování, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="ab919-459">The type of authentication to use.</span></span> <span data-ttu-id="ab919-460">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="ab919-460">The possible values are:</span></span>

  - <span data-ttu-id="ab919-461">`None`-Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="ab919-461">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="ab919-462">`Individual`-Individuální ověřování.</span><span class="sxs-lookup"><span data-stu-id="ab919-462">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="ab919-463">`IndividualB2C`-Jednotlivá ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="ab919-463">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="ab919-464">`SingleOrg`– Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="ab919-464">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="ab919-465">`MultiOrg`– Ověřování organizace pro více tenantů.</span><span class="sxs-lookup"><span data-stu-id="ab919-465">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="ab919-466">`Windows`– Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="ab919-466">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="ab919-467">Instance Azure Active Directory B2C pro připojení.</span><span class="sxs-lookup"><span data-stu-id="ab919-467">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ab919-468">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="ab919-468">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ab919-469">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="ab919-469">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="ab919-470">ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="ab919-470">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ab919-471">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="ab919-471">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="ab919-472">ID zásad pro resetování hesla pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="ab919-472">The reset password policy ID for this project.</span></span> <span data-ttu-id="ab919-473">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="ab919-473">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="ab919-474">Upravit ID zásad profilu pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="ab919-474">The edit profile policy ID for this project.</span></span> <span data-ttu-id="ab919-475">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="ab919-475">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="ab919-476">Instance Azure Active Directory pro připojení.</span><span class="sxs-lookup"><span data-stu-id="ab919-476">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ab919-477">Použijte s `SingleOrg` `MultiOrg` ověřováním nebo.</span><span class="sxs-lookup"><span data-stu-id="ab919-477">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="ab919-478">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="ab919-478">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="ab919-479">ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="ab919-479">The Client ID for this project.</span></span> <span data-ttu-id="ab919-480">Použijte s `IndividualB2C` `SingleOrg` `MultiOrg` ověřováním, nebo.</span><span class="sxs-lookup"><span data-stu-id="ab919-480">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="ab919-481">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="ab919-481">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="ab919-482">Doména pro tenanta adresáře.</span><span class="sxs-lookup"><span data-stu-id="ab919-482">The domain for the directory tenant.</span></span> <span data-ttu-id="ab919-483">Použijte s `SingleOrg` `IndividualB2C` ověřováním nebo.</span><span class="sxs-lookup"><span data-stu-id="ab919-483">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ab919-484">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="ab919-484">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="ab919-485">ID TenantId adresáře, ke kterému se má připojit.</span><span class="sxs-lookup"><span data-stu-id="ab919-485">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ab919-486">Použijte s `SingleOrg` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="ab919-486">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ab919-487">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="ab919-487">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="ab919-488">Cesta požadavku v základní cestě identifikátoru URI přesměrování.</span><span class="sxs-lookup"><span data-stu-id="ab919-488">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="ab919-489">Použijte s `SingleOrg` `IndividualB2C` ověřováním nebo.</span><span class="sxs-lookup"><span data-stu-id="ab919-489">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ab919-490">Výchozí hodnota je `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="ab919-490">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="ab919-491">Povolí této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="ab919-491">Allows this application read-access to the directory.</span></span> <span data-ttu-id="ab919-492">Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ab919-492">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="ab919-493">Vyloučí z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="ab919-493">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="ab919-494">Vypne protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ab919-494">Turns off HTTPS.</span></span> <span data-ttu-id="ab919-495">Tato možnost platí pouze v případě, že se `Individual` `IndividualB2C` `SingleOrg` `MultiOrg` nepoužívají, nebo.</span><span class="sxs-lookup"><span data-stu-id="ab919-495">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="ab919-496">Určuje, že se má místo SQLite použít LocalDB.</span><span class="sxs-lookup"><span data-stu-id="ab919-496">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ab919-497">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ab919-497">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ab919-498">Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="ab919-498">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ab919-499">Možnost je k dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ab919-499">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="ab919-500">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, který používáte:</span><span class="sxs-lookup"><span data-stu-id="ab919-500">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ab919-501">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="ab919-501">SDK version</span></span> | <span data-ttu-id="ab919-502">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="ab919-502">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ab919-503">3.1</span><span class="sxs-lookup"><span data-stu-id="ab919-503">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ab919-504">3.0</span><span class="sxs-lookup"><span data-stu-id="ab919-504">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="ab919-505">Při vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="ab919-505">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="ab919-506">Zahrnuje BrowserLink do projektu.</span><span class="sxs-lookup"><span data-stu-id="ab919-506">Includes BrowserLink in the project.</span></span> <span data-ttu-id="ab919-507">V rozhraní .NET Core 2,2 a 3,1 SDK není dostupná možnost.</span><span class="sxs-lookup"><span data-stu-id="ab919-507">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="ab919-508">Určuje, jestli je projekt nakonfigurovaný tak, aby používal [kompilaci za běhu Razor](/aspnet/core/mvc/views/view-compilation#runtime-compilation) v sestaveních ladění.</span><span class="sxs-lookup"><span data-stu-id="ab919-508">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="ab919-509">Možnost je k dispozici od 3.1.201 sady .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="ab919-509">Option available since .NET Core 3.1.201 SDK.</span></span>

***

### <a name="angular-react"></a><a name="spa"></a><span data-ttu-id="ab919-510">Úhlová, reakce</span><span class="sxs-lookup"><span data-stu-id="ab919-510">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="ab919-511">Typ ověřování, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="ab919-511">The type of authentication to use.</span></span> <span data-ttu-id="ab919-512">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ab919-512">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="ab919-513">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="ab919-513">The possible values are:</span></span>

  - <span data-ttu-id="ab919-514">`None`-Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="ab919-514">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="ab919-515">`Individual`-Individuální ověřování.</span><span class="sxs-lookup"><span data-stu-id="ab919-515">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="ab919-516">Vyloučí z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="ab919-516">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="ab919-517">Při vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="ab919-517">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="ab919-518">Vypne protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ab919-518">Turns off HTTPS.</span></span> <span data-ttu-id="ab919-519">Tato možnost platí pouze v případě, že je ověřování `None` .</span><span class="sxs-lookup"><span data-stu-id="ab919-519">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="ab919-520">Určuje, že se má místo SQLite použít LocalDB.</span><span class="sxs-lookup"><span data-stu-id="ab919-520">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ab919-521">Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ab919-521">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ab919-522">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ab919-522">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ab919-523">Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="ab919-523">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ab919-524">Možnost není dostupná v sadě .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="ab919-524">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="ab919-525">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, který používáte:</span><span class="sxs-lookup"><span data-stu-id="ab919-525">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ab919-526">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="ab919-526">SDK version</span></span> | <span data-ttu-id="ab919-527">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="ab919-527">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ab919-528">3.1</span><span class="sxs-lookup"><span data-stu-id="ab919-528">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ab919-529">3.0</span><span class="sxs-lookup"><span data-stu-id="ab919-529">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="ab919-530">2.1</span><span class="sxs-lookup"><span data-stu-id="ab919-530">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="ab919-531">reactredux</span><span class="sxs-lookup"><span data-stu-id="ab919-531">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="ab919-532">Vyloučí z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="ab919-532">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ab919-533">Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="ab919-533">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ab919-534">Možnost není dostupná v sadě .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="ab919-534">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="ab919-535">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, který používáte:</span><span class="sxs-lookup"><span data-stu-id="ab919-535">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ab919-536">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="ab919-536">SDK version</span></span> | <span data-ttu-id="ab919-537">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="ab919-537">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ab919-538">3.1</span><span class="sxs-lookup"><span data-stu-id="ab919-538">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ab919-539">3.0</span><span class="sxs-lookup"><span data-stu-id="ab919-539">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="ab919-540">2.1</span><span class="sxs-lookup"><span data-stu-id="ab919-540">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="ab919-541">Při vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="ab919-541">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="ab919-542">Vypne protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ab919-542">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="ab919-543">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="ab919-543">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="ab919-544">Při vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="ab919-544">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="ab919-545">Podporuje kromě součástí do této knihovny i tradiční zobrazení a stránky Razor.</span><span class="sxs-lookup"><span data-stu-id="ab919-545">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="ab919-546">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ab919-546">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="ab919-547">WebApi</span><span class="sxs-lookup"><span data-stu-id="ab919-547">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="ab919-548">Typ ověřování, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="ab919-548">The type of authentication to use.</span></span> <span data-ttu-id="ab919-549">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="ab919-549">The possible values are:</span></span>

  - <span data-ttu-id="ab919-550">`None`-Bez ověřování (výchozí).</span><span class="sxs-lookup"><span data-stu-id="ab919-550">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="ab919-551">`IndividualB2C`-Jednotlivá ověřování pomocí Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="ab919-551">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="ab919-552">`SingleOrg`– Ověřování organizace pro jednoho tenanta.</span><span class="sxs-lookup"><span data-stu-id="ab919-552">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="ab919-553">`Windows`– Ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="ab919-553">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="ab919-554">Instance Azure Active Directory B2C pro připojení.</span><span class="sxs-lookup"><span data-stu-id="ab919-554">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ab919-555">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="ab919-555">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ab919-556">Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="ab919-556">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="ab919-557">ID zásad přihlášení a registrace pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="ab919-557">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ab919-558">Použijte s `IndividualB2C` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="ab919-558">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="ab919-559">Instance Azure Active Directory pro připojení.</span><span class="sxs-lookup"><span data-stu-id="ab919-559">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ab919-560">Použijte s `SingleOrg` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="ab919-560">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ab919-561">Výchozí hodnota je `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="ab919-561">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="ab919-562">ID klienta pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="ab919-562">The Client ID for this project.</span></span> <span data-ttu-id="ab919-563">Použijte s `IndividualB2C` `SingleOrg` ověřováním nebo.</span><span class="sxs-lookup"><span data-stu-id="ab919-563">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="ab919-564">Výchozí hodnota je `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="ab919-564">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="ab919-565">Doména pro tenanta adresáře.</span><span class="sxs-lookup"><span data-stu-id="ab919-565">The domain for the directory tenant.</span></span> <span data-ttu-id="ab919-566">Použijte s `IndividualB2C` `SingleOrg` ověřováním nebo.</span><span class="sxs-lookup"><span data-stu-id="ab919-566">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="ab919-567">Výchozí hodnota je `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="ab919-567">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="ab919-568">ID TenantId adresáře, ke kterému se má připojit.</span><span class="sxs-lookup"><span data-stu-id="ab919-568">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ab919-569">Použijte s `SingleOrg` ověřováním.</span><span class="sxs-lookup"><span data-stu-id="ab919-569">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ab919-570">Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="ab919-570">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="ab919-571">Povolí této aplikaci přístup pro čtení k adresáři.</span><span class="sxs-lookup"><span data-stu-id="ab919-571">Allows this application read-access to the directory.</span></span> <span data-ttu-id="ab919-572">Platí jenom pro `SingleOrg` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ab919-572">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="ab919-573">Vyloučí z vygenerované šablony *launchSettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="ab919-573">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="ab919-574">Vypne protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ab919-574">Turns off HTTPS.</span></span> <span data-ttu-id="ab919-575">`app.UseHsts`a `app.UseHttpsRedirection` nejsou přidány do `Startup.Configure` .</span><span class="sxs-lookup"><span data-stu-id="ab919-575">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="ab919-576">Tato možnost se vztahuje jenom `IndividualB2C` na to, jestli `SingleOrg` se nepoužívají pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="ab919-576">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="ab919-577">Určuje, že se má místo SQLite použít LocalDB.</span><span class="sxs-lookup"><span data-stu-id="ab919-577">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ab919-578">Platí jenom pro `IndividualB2C` ověřování.</span><span class="sxs-lookup"><span data-stu-id="ab919-578">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ab919-579">Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.</span><span class="sxs-lookup"><span data-stu-id="ab919-579">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ab919-580">Možnost není dostupná v sadě .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="ab919-580">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="ab919-581">V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, který používáte:</span><span class="sxs-lookup"><span data-stu-id="ab919-581">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ab919-582">SDK version (Verze sady SDK)</span><span class="sxs-lookup"><span data-stu-id="ab919-582">SDK version</span></span> | <span data-ttu-id="ab919-583">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="ab919-583">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ab919-584">3.1</span><span class="sxs-lookup"><span data-stu-id="ab919-584">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ab919-585">3.0</span><span class="sxs-lookup"><span data-stu-id="ab919-585">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="ab919-586">2.1</span><span class="sxs-lookup"><span data-stu-id="ab919-586">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="ab919-587">Při vytváření projektu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="ab919-587">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="ab919-588">globaljson</span><span class="sxs-lookup"><span data-stu-id="ab919-588">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="ab919-589">Určuje verzi .NET Core SDK, která se má použít v souboru *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="ab919-589">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="ab919-590">Příklady</span><span class="sxs-lookup"><span data-stu-id="ab919-590">Examples</span></span>

- <span data-ttu-id="ab919-591">Vytvořte projekt konzolové aplikace v jazyce C# zadáním názvu šablony:</span><span class="sxs-lookup"><span data-stu-id="ab919-591">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="ab919-592">Vytvořte projekt konzolové aplikace F # v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="ab919-592">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang "F#"
  ```

- <span data-ttu-id="ab919-593">Vytvořte .NET Standard projekt knihovny tříd v zadaném adresáři:</span><span class="sxs-lookup"><span data-stu-id="ab919-593">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="ab919-594">Vytvoří nový projekt ASP.NET Core C# MVC v aktuálním adresáři bez ověřování:</span><span class="sxs-lookup"><span data-stu-id="ab919-594">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="ab919-595">Vytvořit nový projekt xUnit:</span><span class="sxs-lookup"><span data-stu-id="ab919-595">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="ab919-596">Vypíše všechny šablony, které jsou k dispozici pro šablony jednostránkové aplikace (SPA):</span><span class="sxs-lookup"><span data-stu-id="ab919-596">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="ab919-597">Vypíše všechny šablony, které odpovídají podřetězci *My* .</span><span class="sxs-lookup"><span data-stu-id="ab919-597">List all templates matching the *we* substring.</span></span> <span data-ttu-id="ab919-598">Nebyla nalezena žádná přesná shoda, takže porovnávání dílčích řetězců se shoduje se sloupci krátkého názvu a názvu.</span><span class="sxs-lookup"><span data-stu-id="ab919-598">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="ab919-599">Došlo k pokusu o vyvolání šablony, která odpovídá *NG*.</span><span class="sxs-lookup"><span data-stu-id="ab919-599">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="ab919-600">Pokud nelze určit jednu shodu, Seznamte se se šablonami, které jsou částečné shody.</span><span class="sxs-lookup"><span data-stu-id="ab919-600">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="ab919-601">Nainstalujte verzi 2,0 šablon SPA pro ASP.NET Core:</span><span class="sxs-lookup"><span data-stu-id="ab919-601">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="ab919-602">Seznam nainstalovaných šablon a podrobností, včetně jejich odinstalace:</span><span class="sxs-lookup"><span data-stu-id="ab919-602">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="ab919-603">V aktuálním adresáři vytvořte *Global. JSON* s nastavením verze sady SDK na 3.1.101:</span><span class="sxs-lookup"><span data-stu-id="ab919-603">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="ab919-604">Viz také</span><span class="sxs-lookup"><span data-stu-id="ab919-604">See also</span></span>

- [<span data-ttu-id="ab919-605">Vlastní šablony pro dotnet New</span><span class="sxs-lookup"><span data-stu-id="ab919-605">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="ab919-606">Vytvoření vlastní šablony pro dotnet new</span><span class="sxs-lookup"><span data-stu-id="ab919-606">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="ab919-607">dotnet/dotnet-Template-Samples – úložiště GitHub</span><span class="sxs-lookup"><span data-stu-id="ab919-607">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="ab919-608">Dostupné šablony pro dotnet New</span><span class="sxs-lookup"><span data-stu-id="ab919-608">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
