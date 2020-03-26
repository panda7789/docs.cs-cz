---
title: Vytvářejte opakovaně použitelné komponenty ui s Blazorem
description: Naučte se vytvářet opakovaně použitelné komponenty uživatelského rozhraní s Blazorem a jak se porovnávají s ovládacími prvky ASP.NET webových formulářů.
author: danroth27
ms.author: daroth
ms.date: 09/18/2019
ms.openlocfilehash: 228f7aec4c7b87cb6d4127b55745f7a5ed90aaf9
ms.sourcegitcommit: b75a45f0cfe012b71b45dd9bf723adf32369d40c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80228628"
---
# <a name="build-reusable-ui-components-with-blazor"></a><span data-ttu-id="1e138-103">Vytvářejte opakovaně použitelné komponenty ui s Blazorem</span><span class="sxs-lookup"><span data-stu-id="1e138-103">Build reusable UI components with Blazor</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="1e138-104">Jednou z krásných věcí, o ASP.NET webových formulářů je, jak umožňuje zapouzdření opakovaně kusů kódu uživatelského rozhraní (UI) do opakovaně použitelných ovládacích prvků uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1e138-104">One of the beautiful things about ASP.NET Web Forms is how it enables encapsulation of reusable pieces of user interface (UI) code into reusable UI controls.</span></span> <span data-ttu-id="1e138-105">Vlastní uživatelské ovládací prvky lze definovat ve značkách pomocí souborů *ASCX.*</span><span class="sxs-lookup"><span data-stu-id="1e138-105">Custom user controls can be defined in markup using *.ascx* files.</span></span> <span data-ttu-id="1e138-106">Můžete také vytvořit komplikované serverové ovládací prvky v kódu s plnou podporou návrháře.</span><span class="sxs-lookup"><span data-stu-id="1e138-106">You can also build elaborate server controls in code with full designer support.</span></span>

<span data-ttu-id="1e138-107">Blazor také podporuje zapouzdření ui prostřednictvím *komponent*.</span><span class="sxs-lookup"><span data-stu-id="1e138-107">Blazor also supports UI encapsulation through *components*.</span></span> <span data-ttu-id="1e138-108">Součást:</span><span class="sxs-lookup"><span data-stu-id="1e138-108">A component:</span></span>

- <span data-ttu-id="1e138-109">Je samostatný kus ui.</span><span class="sxs-lookup"><span data-stu-id="1e138-109">Is a self-contained chunk of UI.</span></span>
- <span data-ttu-id="1e138-110">Udržuje svůj vlastní stav a logiku vykreslování.</span><span class="sxs-lookup"><span data-stu-id="1e138-110">Maintains its own state and rendering logic.</span></span>
- <span data-ttu-id="1e138-111">Můžete definovat obslužné rutiny událostí ui, vázat se na vstupní data a spravovat svůj vlastní životní cyklus.</span><span class="sxs-lookup"><span data-stu-id="1e138-111">Can define UI event handlers, bind to input data, and manage its own lifecycle.</span></span>
- <span data-ttu-id="1e138-112">Je obvykle definován a *.razor* soubor pomocí Razor syntaxe.</span><span class="sxs-lookup"><span data-stu-id="1e138-112">Is typically defined in a *.razor* file using Razor syntax.</span></span>

## <a name="an-introduction-to-razor"></a><span data-ttu-id="1e138-113">Úvod do Razor</span><span class="sxs-lookup"><span data-stu-id="1e138-113">An introduction to Razor</span></span>

<span data-ttu-id="1e138-114">Razor je lehký značkovací jazyk založený na HTML a C#.</span><span class="sxs-lookup"><span data-stu-id="1e138-114">Razor is a light-weight markup templating language based on HTML and C#.</span></span> <span data-ttu-id="1e138-115">S Razor můžete bez problémů přechod mezi značky a C# kód definovat logiku vykreslování komponent.</span><span class="sxs-lookup"><span data-stu-id="1e138-115">With Razor, you can seamlessly transition between markup and C# code to define your component rendering logic.</span></span> <span data-ttu-id="1e138-116">Při kompilaci souboru *.razor* je logika vykreslování ve třídě .NET zachycena strukturovaným způsobem.</span><span class="sxs-lookup"><span data-stu-id="1e138-116">When the *.razor* file is compiled, the rendering logic is captured in a structured way in a .NET class.</span></span> <span data-ttu-id="1e138-117">Název zkompilované třídy je převzat z názvu souboru *.razor.*</span><span class="sxs-lookup"><span data-stu-id="1e138-117">The name of the compiled class is taken from the *.razor* file name.</span></span> <span data-ttu-id="1e138-118">Obor názvů je převzat z výchozího oboru názvů pro projekt a cestu ke složce, nebo můžete explicitně určit obor názvů pomocí `@namespace` směrnice (více o direktivách Razor níže).</span><span class="sxs-lookup"><span data-stu-id="1e138-118">The namespace is taken from the default namespace for the project and the folder path, or you can explicitly specify the namespace using the `@namespace` directive (more on Razor directives below).</span></span>

<span data-ttu-id="1e138-119">Logika vykreslování komponenty je vytvářena pomocí běžných značek HTML s dynamickou logikou přidanou pomocí jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="1e138-119">A component's rendering logic is authored using normal HTML markup with dynamic logic added using C#.</span></span> <span data-ttu-id="1e138-120">Znak `@` se používá k přechodu na C#.</span><span class="sxs-lookup"><span data-stu-id="1e138-120">The `@` character is used to transition to C#.</span></span> <span data-ttu-id="1e138-121">Břitva je obvykle chytrý o zjišťuje, kdy jste přešel zpět na HTML.</span><span class="sxs-lookup"><span data-stu-id="1e138-121">Razor is typically smart about figuring out when you've switched back to HTML.</span></span> <span data-ttu-id="1e138-122">Například následující komponenta vykreslí `<p>` značku s aktuálním časem:</span><span class="sxs-lookup"><span data-stu-id="1e138-122">For example, the following component renders a `<p>` tag with the current time:</span></span>

```razor
<p>@DateTime.Now</p>
```

<span data-ttu-id="1e138-123">Chcete-li explicitně určit začátek a konec výrazu Jazyka C#, použijte závorky:</span><span class="sxs-lookup"><span data-stu-id="1e138-123">To explicitly specify the beginning and ending of a C# expression, use parentheses:</span></span>

```razor
<p>@(DateTime.Now)</p>
```

<span data-ttu-id="1e138-124">Razor také usnadňuje použití c# tok řízení v logice vykreslování.</span><span class="sxs-lookup"><span data-stu-id="1e138-124">Razor also makes it easy to use C# control flow in your rendering logic.</span></span> <span data-ttu-id="1e138-125">Můžete například podmíněně vykreslit některé kódy HTML takto:</span><span class="sxs-lookup"><span data-stu-id="1e138-125">For example, you can conditionally render some HTML like this:</span></span>

```razor
@if (value % 2 == 0)
{
    <p>The value was even.</p>
}
```

<span data-ttu-id="1e138-126">Nebo můžete vygenerovat seznam položek pomocí `foreach` normální smyčky Jazyka C#, jako je tato:</span><span class="sxs-lookup"><span data-stu-id="1e138-126">Or you can generate a list of items using a normal C# `foreach` loop like this:</span></span>

```razor
<ul>
@foreach (var item in items)
{
    <li>@item.Text</li>
}
</ul>
```

<span data-ttu-id="1e138-127">Razor direktivy, jako jsou direktivy v ASP.NET webových formulářů, řídí mnoho aspektů, jak je kompilován komponenty Razor.</span><span class="sxs-lookup"><span data-stu-id="1e138-127">Razor directives, like directives in ASP.NET Web Forms, control many aspects of how a Razor component is compiled.</span></span> <span data-ttu-id="1e138-128">Příklady zahrnují komponenty:</span><span class="sxs-lookup"><span data-stu-id="1e138-128">Examples include the component's:</span></span>

- <span data-ttu-id="1e138-129">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="1e138-129">Namespace</span></span>
- <span data-ttu-id="1e138-130">Základní třída</span><span class="sxs-lookup"><span data-stu-id="1e138-130">Base class</span></span>
- <span data-ttu-id="1e138-131">Implementovaná rozhraní</span><span class="sxs-lookup"><span data-stu-id="1e138-131">Implemented interfaces</span></span>
- <span data-ttu-id="1e138-132">Obecné parametry</span><span class="sxs-lookup"><span data-stu-id="1e138-132">Generic parameters</span></span>
- <span data-ttu-id="1e138-133">Importované obory názvů</span><span class="sxs-lookup"><span data-stu-id="1e138-133">Imported namespaces</span></span>
- <span data-ttu-id="1e138-134">Trasy</span><span class="sxs-lookup"><span data-stu-id="1e138-134">Routes</span></span>

<span data-ttu-id="1e138-135">Razor direktivy začínají znakem `@` a obvykle se používají na začátku nového řádku na začátku souboru.</span><span class="sxs-lookup"><span data-stu-id="1e138-135">Razor directives start with the `@` character and are typically used at the start of a new line at the start of the file.</span></span> <span data-ttu-id="1e138-136">Například `@namespace` směrnice definuje obor názvů komponenty:</span><span class="sxs-lookup"><span data-stu-id="1e138-136">For example, the `@namespace` directive defines the component's namespace:</span></span>

```razor
@namespace MyComponentNamespace
```

<span data-ttu-id="1e138-137">Následující tabulka shrnuje různé direktivy Razor používané v Blazoru a jejich ASP.NET ekvivalenty webových formulářů, pokud existují.</span><span class="sxs-lookup"><span data-stu-id="1e138-137">The following table summarizes the various Razor directives used in Blazor and their ASP.NET Web Forms equivalents, if they exist.</span></span>

|<span data-ttu-id="1e138-138">Směrnice</span><span class="sxs-lookup"><span data-stu-id="1e138-138">Directive</span></span>    |<span data-ttu-id="1e138-139">Popis</span><span class="sxs-lookup"><span data-stu-id="1e138-139">Description</span></span>|<span data-ttu-id="1e138-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="1e138-140">Example</span></span>|<span data-ttu-id="1e138-141">Ekvivalent webových formulářů</span><span class="sxs-lookup"><span data-stu-id="1e138-141">Web Forms equivalent</span></span>|
|-------------|-----------|-------|--------------------|
|`@attribute` |<span data-ttu-id="1e138-142">Přidá k komponentě atribut na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="1e138-142">Adds a class-level attribute to the component</span></span>|`@attribute [Authorize]`|<span data-ttu-id="1e138-143">Žádný</span><span class="sxs-lookup"><span data-stu-id="1e138-143">None</span></span>|
|`@code`      |<span data-ttu-id="1e138-144">Přidá členy třídy do komponenty.</span><span class="sxs-lookup"><span data-stu-id="1e138-144">Adds class members to the component</span></span>|`@code { ... }`|`<script runat="server">...</script>`|
|`@implements`|<span data-ttu-id="1e138-145">Implementuje zadané rozhraní</span><span class="sxs-lookup"><span data-stu-id="1e138-145">Implements the specified interface</span></span>|`@implements IDisposable`|<span data-ttu-id="1e138-146">Použití kódu na pozadí</span><span class="sxs-lookup"><span data-stu-id="1e138-146">Use code-behind</span></span>|
|`@inherits`  |<span data-ttu-id="1e138-147">Dědí ze zadané základní třídy</span><span class="sxs-lookup"><span data-stu-id="1e138-147">Inherits from the specified base class</span></span>|`@inherits MyComponentBase`|`<%@ Control Inherits="MyUserControlBase" %>`|
|`@inject`    |<span data-ttu-id="1e138-148">Vstřikuje službu do součásti</span><span class="sxs-lookup"><span data-stu-id="1e138-148">Injects a service into the component</span></span>|`@inject IJSRuntime JS`|<span data-ttu-id="1e138-149">Žádný</span><span class="sxs-lookup"><span data-stu-id="1e138-149">None</span></span>|
|`@layout`    |<span data-ttu-id="1e138-150">Určuje komponentu rozvržení pro komponentu.</span><span class="sxs-lookup"><span data-stu-id="1e138-150">Specifies a layout component for the component</span></span>|`@layout MainLayout`|`<%@ Page MasterPageFile="~/Site.Master" %>`|
|`@namespace` |<span data-ttu-id="1e138-151">Nastaví obor názvů pro komponentu.</span><span class="sxs-lookup"><span data-stu-id="1e138-151">Sets the namespace for the component</span></span>|`@namespace MyNamespace`|<span data-ttu-id="1e138-152">Žádný</span><span class="sxs-lookup"><span data-stu-id="1e138-152">None</span></span>|
|`@page`      |<span data-ttu-id="1e138-153">Určuje postup pro komponentu.</span><span class="sxs-lookup"><span data-stu-id="1e138-153">Specifies the route for the component</span></span>|`@page "/product/{id}"`|`<%@ Page %>`|
|`@typeparam` |<span data-ttu-id="1e138-154">Určuje parametr obecného typu pro komponentu.</span><span class="sxs-lookup"><span data-stu-id="1e138-154">Specifies a generic type parameter for the component</span></span>|`@typeparam TItem`|<span data-ttu-id="1e138-155">Použití kódu na pozadí</span><span class="sxs-lookup"><span data-stu-id="1e138-155">Use code-behind</span></span>|
|`@using`     |<span data-ttu-id="1e138-156">Určuje obor názvů, který má být převeden do oboru.</span><span class="sxs-lookup"><span data-stu-id="1e138-156">Specifies a namespace to bring into scope</span></span>|`@using MyComponentNamespace`|<span data-ttu-id="1e138-157">Přidání oboru názvů v *souboru web.config*</span><span class="sxs-lookup"><span data-stu-id="1e138-157">Add namespace in *web.config*</span></span>|

<span data-ttu-id="1e138-158">Razor komponenty také rozsáhlé použití *atributy směrnice* na prvky řídit různé aspekty, jak se kompilují součásti (zpracování událostí, datové vazby, odkazy na element komponenty & a tak dále).</span><span class="sxs-lookup"><span data-stu-id="1e138-158">Razor components also make extensive use of *directive attributes* on elements to control various aspects of how components get compiled (event handling, data binding, component & element references, and so on).</span></span> <span data-ttu-id="1e138-159">Direktivy všechny postupujte podle běžné obecné syntaxe, kde jsou hodnoty v závorce volitelné:</span><span class="sxs-lookup"><span data-stu-id="1e138-159">Directive attributes all follow a common generic syntax where the values in parenthesis are optional:</span></span>

```razor
@directive(-suffix(:name))(="value")
```

<span data-ttu-id="1e138-160">Následující tabulka shrnuje různé atributy direktiv Razor používaných v Blazoru.</span><span class="sxs-lookup"><span data-stu-id="1e138-160">The following table summarizes the various attributes for Razor directives used in Blazor.</span></span>

|<span data-ttu-id="1e138-161">Atribut</span><span class="sxs-lookup"><span data-stu-id="1e138-161">Attribute</span></span>    |<span data-ttu-id="1e138-162">Popis</span><span class="sxs-lookup"><span data-stu-id="1e138-162">Description</span></span>|<span data-ttu-id="1e138-163">Příklad</span><span class="sxs-lookup"><span data-stu-id="1e138-163">Example</span></span>|
|-------------|-----------|-------|
|`@attributes`|<span data-ttu-id="1e138-164">Vykreslí slovník atributů</span><span class="sxs-lookup"><span data-stu-id="1e138-164">Renders a dictionary of attributes</span></span>|`<input @attributes="ExtraAttributes" />`|
|`@bind`      |<span data-ttu-id="1e138-165">Vytvoří obousměrnou datovou vazbu.</span><span class="sxs-lookup"><span data-stu-id="1e138-165">Creates a two-way data binding</span></span>    |`<input @bind="username" @bind:event="oninput" />`|
|`@on{event}` |<span data-ttu-id="1e138-166">Přidá obslužnou rutinu události pro zadanou událost.</span><span class="sxs-lookup"><span data-stu-id="1e138-166">Adds an event handler for the specified event</span></span>|`<button @onclick="IncrementCount">Click me!</button>`|
|`@key`       |<span data-ttu-id="1e138-167">Určuje klíč, který má být použit algoritmus diffing pro zachování prvků v kolekci.</span><span class="sxs-lookup"><span data-stu-id="1e138-167">Specifies a key to be used by the diffing algorithm for preserving elements in a collection</span></span>|`<DetailsEditor @key="person" Details="person.Details" />`|
|`@ref`       |<span data-ttu-id="1e138-168">Zachytí odkaz na komponentu nebo element HTML.</span><span class="sxs-lookup"><span data-stu-id="1e138-168">Captures a reference to the component or HTML element</span></span>|`<MyDialog @ref="myDialog" />`|

<span data-ttu-id="1e138-169">Různé atributy směrnice používané Blazorem (`@onclick`, `@bind`, `@ref`, a tak dále) jsou uvedeny v následujících oddílech a v pozdějších kapitolách.</span><span class="sxs-lookup"><span data-stu-id="1e138-169">The various directive attributes used by Blazor (`@onclick`, `@bind`, `@ref`, and so on) are covered in the sections below and later chapters.</span></span>

<span data-ttu-id="1e138-170">Mnoho syntaxí používaných v *souborech ASPX* a *ASCX* má paralelní syntaxe v Razor.</span><span class="sxs-lookup"><span data-stu-id="1e138-170">Many of the syntaxes used in *.aspx* and *.ascx* files have parallel syntaxes in Razor.</span></span> <span data-ttu-id="1e138-171">Níže je jednoduché srovnání syntaxí pro ASP.NET webových formulářů a břitva.</span><span class="sxs-lookup"><span data-stu-id="1e138-171">Below is a simple comparison of the syntaxes for ASP.NET Web Forms and Razor.</span></span>

|<span data-ttu-id="1e138-172">Funkce</span><span class="sxs-lookup"><span data-stu-id="1e138-172">Feature</span></span>                      |<span data-ttu-id="1e138-173">webové formuláře</span><span class="sxs-lookup"><span data-stu-id="1e138-173">Web Forms</span></span>           |<span data-ttu-id="1e138-174">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e138-174">Syntax</span></span>               |<span data-ttu-id="1e138-175">Razor</span><span class="sxs-lookup"><span data-stu-id="1e138-175">Razor</span></span>         |<span data-ttu-id="1e138-176">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e138-176">Syntax</span></span> |
|-----------------------------|--------------------|---------------------|--------------|-------|
|<span data-ttu-id="1e138-177">Direktivy</span><span class="sxs-lookup"><span data-stu-id="1e138-177">Directives</span></span>                   |`<%@ [directive] %>`|`<%@ Page %>`        |`@[directive]`|`@page`|
|<span data-ttu-id="1e138-178">Bloky kódu</span><span class="sxs-lookup"><span data-stu-id="1e138-178">Code blocks</span></span>                  |`<% %>`             |`<% int x = 123; %>` |`@{ }`        |`@{ int x = 123; }`|
|<span data-ttu-id="1e138-179">Výrazy</span><span class="sxs-lookup"><span data-stu-id="1e138-179">Expressions</span></span><br><span data-ttu-id="1e138-180">(html kódované)</span><span class="sxs-lookup"><span data-stu-id="1e138-180">(HTML-encoded)</span></span>|`<%: %>`            |`<%:DateTime.Now %>` |<span data-ttu-id="1e138-181">Implicitní:`@`</span><span class="sxs-lookup"><span data-stu-id="1e138-181">Implicit: `@`</span></span><br><span data-ttu-id="1e138-182">Explicitní:`@()`</span><span class="sxs-lookup"><span data-stu-id="1e138-182">Explicit: `@()`</span></span>|`@DateTime.Now`<br>`@(DateTime.Now)`|
|<span data-ttu-id="1e138-183">Komentáře</span><span class="sxs-lookup"><span data-stu-id="1e138-183">Comments</span></span>                     |`<%-- --%>`         |`<%-- Commented --%>`|`@* *@`       |`@* Commented *@`|
|<span data-ttu-id="1e138-184">Datová vazba</span><span class="sxs-lookup"><span data-stu-id="1e138-184">Data binding</span></span>                 |`<%# %>`            |`<%# Bind("Name") %>`|`@bind`       |`<input @bind="username" />`|

<span data-ttu-id="1e138-185">Chcete-li přidat členy do třídy komponenty Razor, použijte direktivu. `@code`</span><span class="sxs-lookup"><span data-stu-id="1e138-185">To add members to the Razor component class, use the `@code` directive.</span></span> <span data-ttu-id="1e138-186">Tato technika je podobná `<script runat="server">...</script>` použití bloku v uživatelském ovládacím prvku ASP.NET webových formulářů nebo stránce.</span><span class="sxs-lookup"><span data-stu-id="1e138-186">This technique is similar to using a `<script runat="server">...</script>` block in an ASP.NET Web Forms user control or page.</span></span>

```razor
@code {
    int count = 0;

    void IncrementCount()
    {
        count++;
    }
}
```

<span data-ttu-id="1e138-187">Protože Razor je založen na C#, musí být zkompilován z projektu C# (*.csproj).*</span><span class="sxs-lookup"><span data-stu-id="1e138-187">Because Razor is based on C#, it must be compiled from within a C# project (*.csproj*).</span></span> <span data-ttu-id="1e138-188">Soubory *.razor* nelze zkompilovat z projektu jazyka Visual Basic (*.vbproj*).</span><span class="sxs-lookup"><span data-stu-id="1e138-188">You can't compile *.razor* files from a Visual Basic project (*.vbproj*).</span></span> <span data-ttu-id="1e138-189">Stále můžete odkazovat na projekty jazyka Visual Basic z projektu Blazor.</span><span class="sxs-lookup"><span data-stu-id="1e138-189">You can still reference Visual Basic projects from your Blazor project.</span></span> <span data-ttu-id="1e138-190">Opak je také pravdou.</span><span class="sxs-lookup"><span data-stu-id="1e138-190">The opposite is true too.</span></span>

<span data-ttu-id="1e138-191">Úplný odkaz na syntaxi Razor najdete v [tématu Razor syntaxe reference for ASP.NET Core](/aspnet/core/mvc/views/razor).</span><span class="sxs-lookup"><span data-stu-id="1e138-191">For a full Razor syntax reference, see [Razor syntax reference for ASP.NET Core](/aspnet/core/mvc/views/razor).</span></span>

## <a name="use-components"></a><span data-ttu-id="1e138-192">Použití součástí</span><span class="sxs-lookup"><span data-stu-id="1e138-192">Use components</span></span>

<span data-ttu-id="1e138-193">Kromě normálního kódu HTML mohou komponenty používat také jiné součásti jako součást jejich logiky vykreslování.</span><span class="sxs-lookup"><span data-stu-id="1e138-193">Aside from normal HTML, components can also use other components as part of their rendering logic.</span></span> <span data-ttu-id="1e138-194">Syntaxe pro použití komponenty v holicí strojek je podobná použití uživatelského ovládacího prvku v aplikaci ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="1e138-194">The syntax for using a component in Razor is similar to using a user control in an ASP.NET Web Forms app.</span></span> <span data-ttu-id="1e138-195">Součásti jsou určeny pomocí značky elementu, která odpovídá názvu typu komponenty.</span><span class="sxs-lookup"><span data-stu-id="1e138-195">Components are specified using an element tag that matches the type name of the component.</span></span> <span data-ttu-id="1e138-196">Můžete například přidat `Counter` komponentu, jako je tato:</span><span class="sxs-lookup"><span data-stu-id="1e138-196">For example, you can add a `Counter` component like this:</span></span>

```razor
<Counter />
```

<span data-ttu-id="1e138-197">Na rozdíl od ASP.NET webových formulářů, komponenty v Blazor:</span><span class="sxs-lookup"><span data-stu-id="1e138-197">Unlike ASP.NET Web Forms, components in Blazor:</span></span>

- <span data-ttu-id="1e138-198">Nepoužívejte předponu prvku `asp:`(například).</span><span class="sxs-lookup"><span data-stu-id="1e138-198">Don't use an element prefix (for example, `asp:`).</span></span>
- <span data-ttu-id="1e138-199">Nevyžadují registraci na stránce nebo na *web.config*.</span><span class="sxs-lookup"><span data-stu-id="1e138-199">Don't require registration on the page or in the *web.config*.</span></span>

<span data-ttu-id="1e138-200">Myslete na komponenty Razor, jako byste .NET typy, protože to je přesně to, co jsou.</span><span class="sxs-lookup"><span data-stu-id="1e138-200">Think of Razor components like you would .NET types, because that's exactly what they are.</span></span> <span data-ttu-id="1e138-201">Pokud je odkazována sestava obsahující součást, je komponenta k dispozici pro použití.</span><span class="sxs-lookup"><span data-stu-id="1e138-201">If the assembly containing the component is referenced, then the component is available for use.</span></span> <span data-ttu-id="1e138-202">Chcete-li přenést obor názvů komponenty `@using` do oboru, použijte direktivu:</span><span class="sxs-lookup"><span data-stu-id="1e138-202">To bring the component's namespace into scope, apply the `@using` directive:</span></span>

```razor
@using MyComponentLib

<Counter />
```

<span data-ttu-id="1e138-203">Jak je vidět ve výchozích projektech Blazor, je běžné umístit `@using` direktivy do souboru *_Imports.razor* tak, aby byly importovány do všech souborů *.razor* ve stejném adresáři a v podřízených adresářích.</span><span class="sxs-lookup"><span data-stu-id="1e138-203">As seen in the default Blazor projects, it's common to put `@using` directives into a *_Imports.razor* file so that they're imported into all *.razor* files in the same directory and in child directories.</span></span>

<span data-ttu-id="1e138-204">Pokud obor názvů pro komponentu není v oboru, můžete určit komponentu pomocí jejího úplného názvu typu, jak je možné v C#:</span><span class="sxs-lookup"><span data-stu-id="1e138-204">If the namespace for a component isn't in scope, you can specify a component using its full type name, as you can in C#:</span></span>

```razor
<MyComponentLib.Counter />
```

## <a name="component-parameters"></a><span data-ttu-id="1e138-205">Parametry komponenty</span><span class="sxs-lookup"><span data-stu-id="1e138-205">Component parameters</span></span>

<span data-ttu-id="1e138-206">V ASP.NET webových formulářů můžete navést parametry a data do ovládacích prvků pomocí veřejných vlastností.</span><span class="sxs-lookup"><span data-stu-id="1e138-206">In ASP.NET Web Forms, you can flow parameters and data to controls using public properties.</span></span> <span data-ttu-id="1e138-207">Tyto vlastnosti lze nastavit ve značkách pomocí atributů nebo nastavit přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="1e138-207">These properties can be set in markup using attributes or set directly in code.</span></span> <span data-ttu-id="1e138-208">Komponenty Blazor pracují podobným způsobem, i když vlastnosti `[Parameter]` komponenty musí být také označeny atributem, který má být považován za parametry komponenty.</span><span class="sxs-lookup"><span data-stu-id="1e138-208">Blazor components work in a similar fashion, although the component properties must also be marked with the `[Parameter]` attribute to be considered component parameters.</span></span>

<span data-ttu-id="1e138-209">Následující `Counter` komponenta definuje volaný `IncrementAmount` parametr komponenty, který `Counter` lze použít k určení částky, kterou by mělo být při každém klepnutí na tlačítko přírůst.</span><span class="sxs-lookup"><span data-stu-id="1e138-209">The following `Counter` component defines a component parameter called `IncrementAmount` that can be used to specify the amount that the `Counter` should be incremented each time the button is clicked.</span></span>

```razor
<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button class="btn btn-primary" @onclick="IncrementCount">Click me</button>

@code {
    int currentCount = 0;

    [Parameter]
    public int IncrementAmount { get; set; } = 1;

    void IncrementCount()
    {
        currentCount+=IncrementAmount;
    }
}
```

<span data-ttu-id="1e138-210">Chcete-li zadat parametr komponenty v Blazoru, použijte atribut jako v ASP.NET webových formulářů:</span><span class="sxs-lookup"><span data-stu-id="1e138-210">To specify a component parameter in Blazor, use an attribute as you would in ASP.NET Web Forms:</span></span>

```razor
<Counter IncrementAmount="10" />
```

## <a name="event-handlers"></a><span data-ttu-id="1e138-211">Obslužné rutiny událostí</span><span class="sxs-lookup"><span data-stu-id="1e138-211">Event handlers</span></span>

<span data-ttu-id="1e138-212">Oba ASP.NET Web Forms a Blazor poskytují programovací model založený na událostech pro zpracování událostí uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1e138-212">Both ASP.NET Web Forms and Blazor provide an event-based programming model for handling UI events.</span></span> <span data-ttu-id="1e138-213">Příklady takových událostí zahrnují kliknutí na tlačítko a zadávání textu.</span><span class="sxs-lookup"><span data-stu-id="1e138-213">Examples of such events include button clicks and text input.</span></span> <span data-ttu-id="1e138-214">V ASP.NET webových formulářů používáte serverové ovládací prvky HTML ke zpracování událostí uživatelského rozhraní vystavených dom nebo můžete zpracovávat události vystavené ovládacími prvky webového serveru.</span><span class="sxs-lookup"><span data-stu-id="1e138-214">In ASP.NET Web Forms, you use HTML server controls to handle UI events exposed by the DOM, or you can handle events exposed by web server controls.</span></span> <span data-ttu-id="1e138-215">Události jsou na serveru vystavovány prostřednictvím požadavků formuláře po vrácení.</span><span class="sxs-lookup"><span data-stu-id="1e138-215">The events are surfaced on the server through form post-back requests.</span></span> <span data-ttu-id="1e138-216">Zvažte následující tlačítko Webové formuláře, klepněte na příklad:</span><span class="sxs-lookup"><span data-stu-id="1e138-216">Consider the following Web Forms button click example:</span></span>

<span data-ttu-id="1e138-217">*Čítač.ascx*</span><span class="sxs-lookup"><span data-stu-id="1e138-217">*Counter.ascx*</span></span>

```aspx-csharp
<asp:Button ID="ClickMeButton" runat="server" Text="Click me!" OnClick="ClickMeButton_Click" />
```

<span data-ttu-id="1e138-218">*Counter.ascx.cs*</span><span class="sxs-lookup"><span data-stu-id="1e138-218">*Counter.ascx.cs*</span></span>

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void ClickMeButton_Click(object sender, EventArgs e)
    {
        Console.WriteLine("The button was clicked!");
    }
}
```

<span data-ttu-id="1e138-219">V Blazoru můžete registrovat obslužné rutiny pro události `@on{event}`uzlení DOM přímo pomocí atributů směrnice formuláře .</span><span class="sxs-lookup"><span data-stu-id="1e138-219">In Blazor, you can register handlers for DOM UI events directly using directive attributes of the form `@on{event}`.</span></span> <span data-ttu-id="1e138-220">Zástupný `{event}` symbol představuje název události.</span><span class="sxs-lookup"><span data-stu-id="1e138-220">The `{event}` placeholder represents the name of the event.</span></span> <span data-ttu-id="1e138-221">Můžete například poslouchat kliknutí na tlačítka, jako je tento:</span><span class="sxs-lookup"><span data-stu-id="1e138-221">For example, you can listen for button clicks like this:</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick()
    {
        Console.WriteLine("The button was clicked!);
    }
}
```

<span data-ttu-id="1e138-222">Obslužné rutiny událostí mohou přijmout volitelný argument specifický pro událost, který poskytuje další informace o události.</span><span class="sxs-lookup"><span data-stu-id="1e138-222">Event handlers can accept an optional, event-specific argument to provide more information about the event.</span></span> <span data-ttu-id="1e138-223">Například události myši může `MouseEventArgs` mít argument, ale není vyžadováno.</span><span class="sxs-lookup"><span data-stu-id="1e138-223">For example, mouse events can take a `MouseEventArgs` argument, but it isn't required.</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick(MouseEventArgs e)
    {
        Console.WriteLine($"Mouse clicked at {e.ScreenX}, {e.ScreenY}.");
    }
}
```

<span data-ttu-id="1e138-224">Místo odkazování na skupinu metod pro obslužnou rutinu události můžete použít výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="1e138-224">Instead of referring to a method group for an event handler, you can use a lambda expression.</span></span> <span data-ttu-id="1e138-225">Výraz lambda umožňuje zavřít přes jiné hodnoty v oboru.</span><span class="sxs-lookup"><span data-stu-id="1e138-225">A lambda expression allows you to close over other in-scope values.</span></span>

```razor
@foreach (var buttonLabel in buttonLabels)
{
    <button @onclick="() => Console.WriteLine($"The {buttonLabel} button was clicked!")">@buttonLabel</button>
}
```

<span data-ttu-id="1e138-226">Obslužné rutiny událostí lze spustit synchronně nebo asynchronně.</span><span class="sxs-lookup"><span data-stu-id="1e138-226">Event handlers can execute synchronously or asynchronously.</span></span> <span data-ttu-id="1e138-227">Například následující `OnClick` obslužná rutina události se spouští asynchronně:</span><span class="sxs-lookup"><span data-stu-id="1e138-227">For example, the following `OnClick` event handler executes asynchronously:</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    async Task OnClick()
    {
        var result = await Http.GetAsync("api/values");
    }
}
```

<span data-ttu-id="1e138-228">Po zpracování události je komponenta vykreslena tak, aby odpovídala všem změnám stavu součásti.</span><span class="sxs-lookup"><span data-stu-id="1e138-228">After an event is handled, the component is rendered to account for any component state changes.</span></span> <span data-ttu-id="1e138-229">U obslužných rutin asynchronní události je komponenta vykreslena ihned po dokončení spuštění obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="1e138-229">With asynchronous event handlers, the component is rendered immediately after the handler execution completes.</span></span> <span data-ttu-id="1e138-230">Součást je *vykreslen znovu* po dokončení `Task` asynchronní.</span><span class="sxs-lookup"><span data-stu-id="1e138-230">The component is rendered *again* after the asynchronous `Task` completes.</span></span> <span data-ttu-id="1e138-231">Tento režim asynchronního spuštění poskytuje příležitost k vykreslení některé `Task` vhodné uI, zatímco asynchronní je stále probíhá.</span><span class="sxs-lookup"><span data-stu-id="1e138-231">This asynchronous execution mode provides an opportunity to render some appropriate UI while the asynchronous `Task` is still in progress.</span></span>

```razor
<button @onclick="ShowMessage">Get message</button>

@if (showMessage)
{
    @if (message == null)
    {
        <p><em>Loading...</em></p>
    }
    else
    {
        <p>The message is: @message</p>
    }
}

@code
{
    bool showMessage = false;
    string message;

    public async Task ShowMessage()
    {
        showMessage = true;
        message = await MessageService.GetMessageAsync();
    }
}
```

<span data-ttu-id="1e138-232">Komponenty mohou také definovat své vlastní události definováním parametru komponenty typu `EventCallback<TValue>`.</span><span class="sxs-lookup"><span data-stu-id="1e138-232">Components can also define their own events by defining a component parameter of type `EventCallback<TValue>`.</span></span> <span data-ttu-id="1e138-233">Zpětná volání událostí podporují všechny varianty obslužných rutin událostí um DOM: volitelné argumenty, synchronní nebo asynchronní, skupiny metod nebo výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="1e138-233">Event callbacks support all the variations of DOM UI event handlers: optional arguments, synchronous or asynchronous, method groups, or lambda expressions.</span></span>

```razor
<button class="btn btn-primary" @onclick="OnClick">Click me!</button>

@code {
    [Parameter]
    public EventCallback<MouseEventArgs> OnClick { get; set; }
}
```

## <a name="data-binding"></a><span data-ttu-id="1e138-234">Datová vazba</span><span class="sxs-lookup"><span data-stu-id="1e138-234">Data binding</span></span>

<span data-ttu-id="1e138-235">Blazor poskytuje jednoduchý mechanismus pro vazbu dat z komponenty ui do stavu komponenty.</span><span class="sxs-lookup"><span data-stu-id="1e138-235">Blazor provides a simple mechanism to bind data from a UI component to the component's state.</span></span> <span data-ttu-id="1e138-236">Tento přístup se liší od funkcí v ASP.NET webových formulářů pro vazby dat ze zdrojů dat na ovládací prvky uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1e138-236">This approach differs from the features in ASP.NET Web Forms for binding data from data sources to UI controls.</span></span> <span data-ttu-id="1e138-237">Zpracování dat z různých zdrojů dat se budeme zabývat v části [Nakládání s údaji.](data.md)</span><span class="sxs-lookup"><span data-stu-id="1e138-237">We'll cover handling data from different data sources in the [Dealing with data](data.md) section.</span></span>

<span data-ttu-id="1e138-238">Chcete-li vytvořit obousměrnou datovou vazbu z komponenty ui `@bind` do stavu komponenty, použijte atribut direktivy.</span><span class="sxs-lookup"><span data-stu-id="1e138-238">To create a two-way data binding from a UI component to the component's state, use the `@bind` directive attribute.</span></span> <span data-ttu-id="1e138-239">V následujícím příkladu je hodnota zaškrtávacího políčka vázána na `isChecked` pole.</span><span class="sxs-lookup"><span data-stu-id="1e138-239">In the following example, the value of the check box is bound to the `isChecked` field.</span></span>

```razor
<input type="checkbox" @bind="isChecked" />

@code {
    bool isChecked;
}
```

<span data-ttu-id="1e138-240">Při vykreslení komponenty je hodnota zaškrtávacího políčka nastavena na hodnotu `isChecked` pole.</span><span class="sxs-lookup"><span data-stu-id="1e138-240">When the component is rendered, the value of the checkbox is set to the value of the `isChecked` field.</span></span> <span data-ttu-id="1e138-241">Když uživatel přepne zaškrtávací políčko, `onchange` událost je aktivována a `isChecked` pole je nastavena na novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1e138-241">When the user toggles the checkbox, the `onchange` event is fired and the `isChecked` field is set to the new value.</span></span> <span data-ttu-id="1e138-242">Syntaxe `@bind` v tomto případě je ekvivalentní následující značky:</span><span class="sxs-lookup"><span data-stu-id="1e138-242">The `@bind` syntax in this case is equivalent to the following markup:</span></span>

```razor
<input value="@isChecked" @onchange="(UIChangeEventArgs e) => isChecked = e.Value" />
```

<span data-ttu-id="1e138-243">Chcete-li změnit událost použitou `@bind:event` pro vazbu, použijte atribut.</span><span class="sxs-lookup"><span data-stu-id="1e138-243">To change the event used for the bind, use the `@bind:event` attribute.</span></span>

```razor
<input @bind="text" @bind:event="oninput" />
<p>@text</p>

@code {
    string text;
}
```

<span data-ttu-id="1e138-244">Komponenty mohou také podporovat datové vazby na jejich parametry.</span><span class="sxs-lookup"><span data-stu-id="1e138-244">Components can also support data binding to their parameters.</span></span> <span data-ttu-id="1e138-245">Chcete-li vytvořit vazbu dat, definujte parametr zpětného volání události se stejným názvem jako parametr s povážit.</span><span class="sxs-lookup"><span data-stu-id="1e138-245">To data bind, define an event callback parameter with the same name as the bindable parameter.</span></span> <span data-ttu-id="1e138-246">K názvu je přidána přípona "Změněno".</span><span class="sxs-lookup"><span data-stu-id="1e138-246">The "Changed" suffix is added to the name.</span></span>

<span data-ttu-id="1e138-247">*PasswordBox.holicí strojek*</span><span class="sxs-lookup"><span data-stu-id="1e138-247">*PasswordBox.razor*</span></span>

```razor
Password: <input
    value="@Password"
    @oninput="OnPasswordChanged"
    type="@(showPassword ? "text" : "password")" />

<label><input type="checkbox" @bind="showPassword" />Show password</label>

@code {
    private bool showPassword;

    [Parameter]
    public string Password { get; set; }

    [Parameter]
    public EventCallback<string> PasswordChanged { get; set; }

    private Task OnPasswordChanged(ChangeEventArgs e)
    {
        Password = e.Value.ToString();
        return PasswordChanged.InvokeAsync(Password);
    }
}
```

<span data-ttu-id="1e138-248">Chcete-li zřetězit datovou vazbu na základní prvek rozhraní, nastavte hodnotu a `@bind` zpracovat událost přímo v prvku ui namísto použití atributu.</span><span class="sxs-lookup"><span data-stu-id="1e138-248">To chain a data binding to an underlying UI element, set the value and handle the event directly on the UI element instead of using the `@bind` attribute.</span></span>

<span data-ttu-id="1e138-249">Chcete-li vytvořit vazbu `@bind-{Parameter}` na parametr komponenty, použijte atribut k určení parametru, ke kterému chcete vazbu.</span><span class="sxs-lookup"><span data-stu-id="1e138-249">To bind to a component parameter, use a `@bind-{Parameter}` attribute to specify the parameter to which you want to bind.</span></span>

```razor
<PasswordBox @bind-Password="password" />

@code {
    string password;
}
```

## <a name="state-changes"></a><span data-ttu-id="1e138-250">Změny stavu</span><span class="sxs-lookup"><span data-stu-id="1e138-250">State changes</span></span>

<span data-ttu-id="1e138-251">Pokud se stav komponenty změnil mimo normální událost uI nebo zpětné volání události, musí komponenta ručně signalizovat, že je třeba ji znovu vykreslit.</span><span class="sxs-lookup"><span data-stu-id="1e138-251">If the component's state has changed outside of a normal UI event or event callback, then the component must manually signal that it needs to be rendered again.</span></span> <span data-ttu-id="1e138-252">Chcete-li signalizovat, že se stav `StateHasChanged` komponenty změnil, zavolejte metodu komponenty.</span><span class="sxs-lookup"><span data-stu-id="1e138-252">To signal that a component's state has changed, call the `StateHasChanged` method on the component.</span></span>

<span data-ttu-id="1e138-253">V níže uvedeném příkladu se `AppState` zobrazí zpráva ze služby, kterou lze aktualizovat v jiných částech aplikace.</span><span class="sxs-lookup"><span data-stu-id="1e138-253">In the example below, a component displays a message from an `AppState` service that can be updated by other parts of the app.</span></span> <span data-ttu-id="1e138-254">Komponenta zaregistruje `StateHasChanged` svou `AppState.OnChange` metodu s událostí tak, aby komponenta je vykreslen a vždy, když zpráva získá aktualizován.</span><span class="sxs-lookup"><span data-stu-id="1e138-254">The component registers its `StateHasChanged` method with the `AppState.OnChange` event so that the component is rendered whenever the message gets updated.</span></span>

```csharp
public class AppState
{
    public string Message { get; }

    // Lets components receive change notifications
    public event Action OnChange;

    public void UpdateMessage(string message)
    {
        shortlist.Add(itinerary);
        NotifyStateChanged();
    }

    private void NotifyStateChanged() => OnChange?.Invoke();
}
```

```razor
@inject AppState AppState

<p>App message: @AppState.Message</p>

@code {
    protected override void OnInitialized()
    {
        AppState.OnChange += StateHasChanged
    }
}
```

## <a name="component-lifecycle"></a><span data-ttu-id="1e138-255">Životní cyklus komponenty</span><span class="sxs-lookup"><span data-stu-id="1e138-255">Component lifecycle</span></span>

<span data-ttu-id="1e138-256">Rozhraní ASP.NET webových formulářů obsahuje dobře definované metody životního cyklu pro moduly, stránky a ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="1e138-256">The ASP.NET Web Forms framework has well-defined lifecycle methods for modules, pages, and controls.</span></span> <span data-ttu-id="1e138-257">Například následující ovládací prvek implementuje `Init`obslužné rutiny událostí pro události , `Load`a `UnLoad` životního cyklu:</span><span class="sxs-lookup"><span data-stu-id="1e138-257">For example, the following control implements event handlers for the `Init`, `Load`, and `UnLoad` lifecycle events:</span></span>

<span data-ttu-id="1e138-258">*Counter.ascx.cs*</span><span class="sxs-lookup"><span data-stu-id="1e138-258">*Counter.ascx.cs*</span></span>

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void Page_Init(object sender, EventArgs e) { ... }
    protected void Page_Load(object sender, EventArgs e) { ... }
    protected void Page_UnLoad(object sender, EventArgs e) { ... }
}
```

<span data-ttu-id="1e138-259">Komponenty Blazor mají také dobře definovaný životní cyklus.</span><span class="sxs-lookup"><span data-stu-id="1e138-259">Blazor components also have a well-defined lifecycle.</span></span> <span data-ttu-id="1e138-260">Životní cyklus komponenty lze použít k inicializaci stavu komponenty a implementaci rozšířeného chování součástí.</span><span class="sxs-lookup"><span data-stu-id="1e138-260">A component's lifecycle can be used to initialize component state and implement advanced component behaviors.</span></span>

<span data-ttu-id="1e138-261">Všechny metody životního cyklu komponent Blazor mají synchronní i asynchronní verze.</span><span class="sxs-lookup"><span data-stu-id="1e138-261">All of Blazor's component lifecycle methods have both synchronous and asynchronous versions.</span></span> <span data-ttu-id="1e138-262">Vykreslování komponent je synchronní.</span><span class="sxs-lookup"><span data-stu-id="1e138-262">Component rendering is synchronous.</span></span> <span data-ttu-id="1e138-263">Asynchronní logiku nelze spustit jako součást vykreslování komponenty.</span><span class="sxs-lookup"><span data-stu-id="1e138-263">You can't run asynchronous logic as part of the component rendering.</span></span> <span data-ttu-id="1e138-264">Všechny asynchronní logiky musí spustit `async` jako součást metody životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="1e138-264">All asynchronous logic must execute as part of an `async` lifecycle method.</span></span>

### <a name="oninitialized"></a><span data-ttu-id="1e138-265">Přiicializováno</span><span class="sxs-lookup"><span data-stu-id="1e138-265">OnInitialized</span></span>

<span data-ttu-id="1e138-266">Metody `OnInitialized` `OnInitializedAsync` a se používají k inicializaci komponenty.</span><span class="sxs-lookup"><span data-stu-id="1e138-266">The `OnInitialized` and `OnInitializedAsync` methods are used to initialize the component.</span></span> <span data-ttu-id="1e138-267">Komponenta je obvykle inicializována po prvním vykreslení.</span><span class="sxs-lookup"><span data-stu-id="1e138-267">A component is typically initialized after it's first rendered.</span></span> <span data-ttu-id="1e138-268">Po inicializování součásti může být vykreslena vícekrát před tím, než je nakonec uvolněna.</span><span class="sxs-lookup"><span data-stu-id="1e138-268">After a component is initialized, it may be rendered multiple times before it's eventually disposed.</span></span> <span data-ttu-id="1e138-269">Metoda `OnInitialized` je podobná `Page_Load` události na stránkách a ovládacích prvcích webových formulářů ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="1e138-269">The `OnInitialized` method is similar to the `Page_Load` event in ASP.NET Web Forms pages and controls.</span></span>

```csharp
protected override void OnInitialized() { ... }
protected override async Task OnInitializedAsync() { await ... }
```

### <a name="onparametersset"></a><span data-ttu-id="1e138-270">OnParametersSet</span><span class="sxs-lookup"><span data-stu-id="1e138-270">OnParametersSet</span></span>

<span data-ttu-id="1e138-271">Metody `OnParametersSet` `OnParametersSetAsync` a jsou volány, když komponenta obdržela parametry od nadřazeného a hodnota je přiřazena vlastnostem.</span><span class="sxs-lookup"><span data-stu-id="1e138-271">The `OnParametersSet` and `OnParametersSetAsync` methods are called when a component has received parameters from its parent and the value are assigned to properties.</span></span> <span data-ttu-id="1e138-272">Tyto metody jsou prováděny po inicializaci komponenty a *při každém vykreslení komponenty*.</span><span class="sxs-lookup"><span data-stu-id="1e138-272">These methods are executed after component initialization and *each time the component is rendered*.</span></span>

```csharp
protected override void OnParametersSet() { ... }
protected override async Task OnParametersSetAsync() { await ... }
```

### <a name="onafterrender"></a><span data-ttu-id="1e138-273">OnAfterRender</span><span class="sxs-lookup"><span data-stu-id="1e138-273">OnAfterRender</span></span>

<span data-ttu-id="1e138-274">Metody `OnAfterRender` `OnAfterRenderAsync` a jsou volány po dokončení vykreslování komponenty.</span><span class="sxs-lookup"><span data-stu-id="1e138-274">The `OnAfterRender` and `OnAfterRenderAsync` methods are called after a component has finished rendering.</span></span> <span data-ttu-id="1e138-275">Odkazy na elementy a komponenty jsou vyplněny v tomto okamžiku (více o těchto konceptech níže).</span><span class="sxs-lookup"><span data-stu-id="1e138-275">Element and component references are populated at this point (more on these concepts below).</span></span> <span data-ttu-id="1e138-276">Interaktivita s prohlížečem je v tomto okamžiku povolena.</span><span class="sxs-lookup"><span data-stu-id="1e138-276">Interactivity with the browser is enabled at this point.</span></span> <span data-ttu-id="1e138-277">Interakce s dom a JavaScript provedení může bezpečně probíhat.</span><span class="sxs-lookup"><span data-stu-id="1e138-277">Interactions with the DOM and JavaScript execution can safely take place.</span></span>

```csharp
protected override void OnAfterRender(bool firstRender)
{
    if (firstRender)
    {
        ...
    }
}
protected override async Task OnAfterRenderAsync(bool firstRender)
{
    if (firstRender)
    {
        await ...
    }
}
```

<span data-ttu-id="1e138-278">`OnAfterRender`a `OnAfterRenderAsync` *nejsou volány při předběžném vykreslování na serveru*.</span><span class="sxs-lookup"><span data-stu-id="1e138-278">`OnAfterRender` and `OnAfterRenderAsync` *aren't called when prerendering on the server*.</span></span>

<span data-ttu-id="1e138-279">Parametr `firstRender` je `true` poprvé, kdy je komponenta vykreslena; jinak je `false`jeho hodnota .</span><span class="sxs-lookup"><span data-stu-id="1e138-279">The `firstRender` parameter is `true` the first time the component is rendered; otherwise, its value is `false`.</span></span>

### <a name="idisposable"></a><span data-ttu-id="1e138-280">Idisposable</span><span class="sxs-lookup"><span data-stu-id="1e138-280">IDisposable</span></span>

<span data-ttu-id="1e138-281">Komponenty Blazor `IDisposable` lze implementovat k vyřazení prostředků při odebrání komponenty z unového nástroje.</span><span class="sxs-lookup"><span data-stu-id="1e138-281">Blazor components can implement `IDisposable` to dispose of resources when the component is removed from the UI.</span></span> <span data-ttu-id="1e138-282">Razor komponenta `IDispose` lze implementovat pomocí `@implements` směrnice:</span><span class="sxs-lookup"><span data-stu-id="1e138-282">A Razor component can implement `IDispose` by using the `@implements` directive:</span></span>

```razor
@using System
@implements IDisposable

...

@code {
    public void Dispose()
    {
        ...
    }
}
```

## <a name="capture-component-references"></a><span data-ttu-id="1e138-283">Zachycení odkazů na součásti</span><span class="sxs-lookup"><span data-stu-id="1e138-283">Capture component references</span></span>

<span data-ttu-id="1e138-284">V ASP.NET webových formulářů je běžné manipulovat s instanci ovládacího prvku přímo v kódu odkazem na jeho ID.</span><span class="sxs-lookup"><span data-stu-id="1e138-284">In ASP.NET Web Forms, it's common to manipulate a control instance directly in code by referring to its ID.</span></span> <span data-ttu-id="1e138-285">V Blazoru je také možné zachytit a manipulovat s odkazem na komponentu, i když je mnohem méně častá.</span><span class="sxs-lookup"><span data-stu-id="1e138-285">In Blazor, it's also possible to capture and manipulate a reference to a component, although it's much less common.</span></span>

<span data-ttu-id="1e138-286">Chcete-li zachytit odkaz na komponentu `@ref` v Blazoru, použijte atribut direktivy.</span><span class="sxs-lookup"><span data-stu-id="1e138-286">To capture a component reference in Blazor, use the `@ref` directive attribute.</span></span> <span data-ttu-id="1e138-287">Hodnota atributu by měla odpovídat názvu tištěného pole se stejným typem jako odkazovaná komponenta.</span><span class="sxs-lookup"><span data-stu-id="1e138-287">The value of the attribute should match the name of a settable field with the same type as the referenced component.</span></span>

```razor
<MyLoginDialog @ref="loginDialog" ... />

@code {
    MyLoginDialog loginDialog;

    void OnSomething()
    {
        loginDialog.Show();
    }
}
```

<span data-ttu-id="1e138-288">Při vykreslení nadřazené součásti je pole naplněno podřízenou instancí komponenty.</span><span class="sxs-lookup"><span data-stu-id="1e138-288">When the parent component is rendered, the field is populated with the child component instance.</span></span> <span data-ttu-id="1e138-289">Potom můžete volat metody na nebo jinak manipulovat s instancí komponenty.</span><span class="sxs-lookup"><span data-stu-id="1e138-289">You can then call methods on, or otherwise manipulate, the component instance.</span></span>

<span data-ttu-id="1e138-290">Manipulace se stavem komponenty přímo pomocí odkazů na komponenty se nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="1e138-290">Manipulating component state directly using component references isn't recommended.</span></span> <span data-ttu-id="1e138-291">Tím zabráníte automatickému vykreslení součásti ve správný čas.</span><span class="sxs-lookup"><span data-stu-id="1e138-291">Doing so prevents the component from being rendered automatically at the correct times.</span></span>

## <a name="capture-element-references"></a><span data-ttu-id="1e138-292">Zachycení odkazů na elementy</span><span class="sxs-lookup"><span data-stu-id="1e138-292">Capture element references</span></span>

<span data-ttu-id="1e138-293">Komponenty Blazor umějí zachytit odkazy na prvek.</span><span class="sxs-lookup"><span data-stu-id="1e138-293">Blazor components can capture references to an element.</span></span> <span data-ttu-id="1e138-294">Na rozdíl od serverových ovládacích prvků HTML v ASP.NET webových formulářů nelze s dom přímo manipulovat pomocí odkazu na element v Blazoru.</span><span class="sxs-lookup"><span data-stu-id="1e138-294">Unlike HTML server controls in ASP.NET Web Forms, you can't manipulate the DOM directly using an element reference in Blazor.</span></span> <span data-ttu-id="1e138-295">Blazor zpracovává většinu dom interakcí pro vás pomocí jeho DOM diffing algoritmus.</span><span class="sxs-lookup"><span data-stu-id="1e138-295">Blazor handles most DOM interactions for you using its DOM diffing algorithm.</span></span> <span data-ttu-id="1e138-296">Zachycené odkazy na elementy v Blazoru jsou neprůhledné.</span><span class="sxs-lookup"><span data-stu-id="1e138-296">Captured element references in Blazor are opaque.</span></span> <span data-ttu-id="1e138-297">Používají se však k předání odkazu na určitý prvek v volání interop javascriptu.</span><span class="sxs-lookup"><span data-stu-id="1e138-297">However, they're used to pass a specific element reference in a JavaScript interop call.</span></span> <span data-ttu-id="1e138-298">Další informace o javascriptovém interopu najdete [v tématu ASP.NET Core Blazor JavaScript interop](/aspnet/core/blazor/javascript-interop).</span><span class="sxs-lookup"><span data-stu-id="1e138-298">For more information about JavaScript interop, see [ASP.NET Core Blazor JavaScript interop](/aspnet/core/blazor/javascript-interop).</span></span>

## <a name="templated-components"></a><span data-ttu-id="1e138-299">Komponenty bez vizuálního vzhledu</span><span class="sxs-lookup"><span data-stu-id="1e138-299">Templated components</span></span>

<span data-ttu-id="1e138-300">Ve ASP.NET webových formulářů můžete vytvářet *šablony ovládacích prvků*.</span><span class="sxs-lookup"><span data-stu-id="1e138-300">In ASP.NET Web Forms, you can create *templated controls*.</span></span> <span data-ttu-id="1e138-301">Šablony ovládací prvky umožňují vývojáři určit část HTML, která slouží k vykreslení ovládacího prvku kontejneru.</span><span class="sxs-lookup"><span data-stu-id="1e138-301">Templated controls enable the developer to specify a portion of the HTML used to render a container control.</span></span> <span data-ttu-id="1e138-302">Mechanika vytváření šablonových serverových ovládacích prvků je složitá, ale umožňují výkonné scénáře pro vykreslování dat uživatelsky přizpůsobitelným způsobem.</span><span class="sxs-lookup"><span data-stu-id="1e138-302">The mechanics of building templated server controls are complex, but they enable powerful scenarios for rendering data in a user customizable way.</span></span> <span data-ttu-id="1e138-303">Příklady šablonovaných ovládacích prvků zahrnují `Repeater` a `DataList`.</span><span class="sxs-lookup"><span data-stu-id="1e138-303">Examples of templated controls include `Repeater` and `DataList`.</span></span>

<span data-ttu-id="1e138-304">Komponenty Blazor lze také šablonovat definováním parametrů `RenderFragment` `RenderFragment<T>`komponent typu nebo .</span><span class="sxs-lookup"><span data-stu-id="1e138-304">Blazor components can also be templated by defining component parameters of type `RenderFragment` or `RenderFragment<T>`.</span></span> <span data-ttu-id="1e138-305">A `RenderFragment` představuje blok razor značky, které pak mohou být vykresleny komponenty.</span><span class="sxs-lookup"><span data-stu-id="1e138-305">A `RenderFragment` represents a chunk of Razor markup that can then be rendered by the component.</span></span> <span data-ttu-id="1e138-306">A `RenderFragment<T>` je blok značky Razor, který přebírá parametr, který lze zadat při vykreslení fragmentu vykreslení.</span><span class="sxs-lookup"><span data-stu-id="1e138-306">A `RenderFragment<T>` is a chunk of Razor markup that takes a parameter that can be specified when the render fragment is rendered.</span></span>

### <a name="child-content"></a><span data-ttu-id="1e138-307">Podřízený obsah</span><span class="sxs-lookup"><span data-stu-id="1e138-307">Child content</span></span>

<span data-ttu-id="1e138-308">Komponenty Blazor mohou zachytit svůj `RenderFragment` podřízený obsah jako a vykreslit tento obsah jako součást vykreslování komponent.</span><span class="sxs-lookup"><span data-stu-id="1e138-308">Blazor components can capture their child content as a `RenderFragment` and render that content as part of the component rendering.</span></span> <span data-ttu-id="1e138-309">Chcete-li zachytit podřízený obsah, `RenderFragment` definujte `ChildContent`parametr komponenty typu a pojmenujte jej .</span><span class="sxs-lookup"><span data-stu-id="1e138-309">To capture child content, define a component parameter of type `RenderFragment` and name it `ChildContent`.</span></span>

<span data-ttu-id="1e138-310">*ChildContentComponent.razor*</span><span class="sxs-lookup"><span data-stu-id="1e138-310">*ChildContentComponent.razor*</span></span>

```razor
<h1>Component with child content</h1>

<div>@ChildContent</div>

@code {
    [Parameter]
    public RenderFragment ChildContent { get; set; }
}
```

<span data-ttu-id="1e138-311">Nadřazená komponenta pak může poskytovat podřízený obsah pomocí normální syntaxe Razor.</span><span class="sxs-lookup"><span data-stu-id="1e138-311">A parent component can then supply child content using normal Razor syntax.</span></span>

```razor
<ChildContentComponent>
    <p>The time is @DateTime.Now</p>
</ChildContentComponent>
```

### <a name="template-parameters"></a><span data-ttu-id="1e138-312">Parametry šablony</span><span class="sxs-lookup"><span data-stu-id="1e138-312">Template parameters</span></span>

<span data-ttu-id="1e138-313">Šablonovaná komponenta Blazor může také definovat `RenderFragment` více `RenderFragment<T>`parametrů komponent typu nebo .</span><span class="sxs-lookup"><span data-stu-id="1e138-313">A templated Blazor component can also define multiple component parameters of type `RenderFragment` or `RenderFragment<T>`.</span></span> <span data-ttu-id="1e138-314">Parametr pro `RenderFragment<T>` lze zadat, když je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="1e138-314">The parameter for a `RenderFragment<T>` can be specified when it's invoked.</span></span> <span data-ttu-id="1e138-315">Chcete-li zadat parametr obecného typu `@typeparam` pro komponentu, použijte direktivu Razor.</span><span class="sxs-lookup"><span data-stu-id="1e138-315">To specify a generic type parameter for a component, use the `@typeparam` Razor directive.</span></span>

<span data-ttu-id="1e138-316">*SimpleListView.holicí strojek*</span><span class="sxs-lookup"><span data-stu-id="1e138-316">*SimpleListView.razor*</span></span>

```razor
@typeparam TItem

@Heading

<ul>
@foreach (var item in Items)
{
    <li>@ItemTemplate(item)</li>
}
</ul>

@code {
    [Parameter]
    public RenderFragment Heading { get; set; }

    [Parameter]
    public RenderFragment<TItem> ItemTemplate { get; set; }

    [Parameter]
    public IEnumerable<TItem> Items { get; set; }
}
```

<span data-ttu-id="1e138-317">Při použití komponenty šablony lze parametry šablony zadat pomocí podřízených prvků, které odpovídají názvům parametrů.</span><span class="sxs-lookup"><span data-stu-id="1e138-317">When using a templated component, the template parameters can be specified using child elements that match the names of the parameters.</span></span> <span data-ttu-id="1e138-318">Komponenty argumenty `RenderFragment<T>` typu předané jako `context`prvky mají implicitní parametr s názvem .</span><span class="sxs-lookup"><span data-stu-id="1e138-318">Component arguments of type `RenderFragment<T>` passed as elements have an implicit parameter named `context`.</span></span> <span data-ttu-id="1e138-319">Název tohoto parametru implement můžete `Context` změnit pomocí atributu na podřízeném prvku.</span><span class="sxs-lookup"><span data-stu-id="1e138-319">You can change the name of this implement parameter using the `Context` attribute on the child element.</span></span> <span data-ttu-id="1e138-320">Všechny parametry obecného typu lze zadat pomocí atributu, který odpovídá názvu parametru typu.</span><span class="sxs-lookup"><span data-stu-id="1e138-320">Any generic type parameters can be specified using an attribute that matches the name of the type parameter.</span></span> <span data-ttu-id="1e138-321">Parametr typu bude pokud možno odvozen:</span><span class="sxs-lookup"><span data-stu-id="1e138-321">The type parameter will be inferred if possible:</span></span>

```razor
<SimpleListView Items="messages" TItem="string">
    <Heading>
        <h1>My list</h1>
    </Heading>
    <ItemTemplate Content="message">
        <p>The message is: @message</p>
    </ItemTemplate>
</SimpleListView>
```

<span data-ttu-id="1e138-322">Výstup této součásti vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="1e138-322">The output of this component looks like this:</span></span>

```html
<h1>My list</h1>
<ul>
    <li>The message is: message1</li>
    <li>The message is: message2</li>
<ul>
```

## <a name="code-behind"></a><span data-ttu-id="1e138-323">Kód na pozadí</span><span class="sxs-lookup"><span data-stu-id="1e138-323">Code-behind</span></span>

<span data-ttu-id="1e138-324">Komponenta Blazor je obvykle vytvářena v jednom souboru *.razor.*</span><span class="sxs-lookup"><span data-stu-id="1e138-324">A Blazor component is typically authored in a single *.razor* file.</span></span> <span data-ttu-id="1e138-325">Je však také možné oddělit kód a značky pomocí souboru s kódem na pozadí.</span><span class="sxs-lookup"><span data-stu-id="1e138-325">However, it's also possible to separate the code and markup using a code-behind file.</span></span> <span data-ttu-id="1e138-326">Chcete-li použít soubor komponenty, přidejte soubor C#, který odpovídá názvu souboru součásti, ale s přidanou příponou *CS* (*Counter.razor.cs*).</span><span class="sxs-lookup"><span data-stu-id="1e138-326">To use a component file, add a C# file that matches the file name of the component file but with a *.cs* extension added (*Counter.razor.cs*).</span></span> <span data-ttu-id="1e138-327">Pomocí souboru C# definujte základní třídu pro komponentu.</span><span class="sxs-lookup"><span data-stu-id="1e138-327">Use the C# file to define a base class for the component.</span></span> <span data-ttu-id="1e138-328">Základní třídu můžete pojmenovat, co chcete, ale je běžné pojmenovat třídu stejně `Base` jako třída`CounterBase`komponenty, ale s přidaným rozšířením ( ).</span><span class="sxs-lookup"><span data-stu-id="1e138-328">You can name the base class anything you'd like, but it's common to name the class the same as the component class, but with a `Base` extension added (`CounterBase`).</span></span> <span data-ttu-id="1e138-329">Třída založená na komponentách `ComponentBase`musí také odvozovat z .</span><span class="sxs-lookup"><span data-stu-id="1e138-329">The component-based class must also derive from `ComponentBase`.</span></span> <span data-ttu-id="1e138-330">Potom v souboru komponenty `@inherits` Razor přidejte direktivu`@inherits CounterBase`k určení základní třídy pro komponentu ( ).</span><span class="sxs-lookup"><span data-stu-id="1e138-330">Then, in the Razor component file, add the `@inherits` directive to specify the base class for the component (`@inherits CounterBase`).</span></span>

<span data-ttu-id="1e138-331">*Counter.břitva*</span><span class="sxs-lookup"><span data-stu-id="1e138-331">*Counter.razor*</span></span>

```razor
@inherits CounterBase

<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button @onclick="IncrementCount">Click me</button>
```

<span data-ttu-id="1e138-332">*Counter.razor.cs*</span><span class="sxs-lookup"><span data-stu-id="1e138-332">*Counter.razor.cs*</span></span>

```csharp
public class CounterBase : ComponentBase
{
    protected int currentCount = 0;

    protected void IncrementCount()
    {
        currentCount++;
    }
}
```

<span data-ttu-id="1e138-333">Viditelnost členů komponenty v základní třídě musí `protected` být `public` nebo musí být viditelná pro třídu komponenty.</span><span class="sxs-lookup"><span data-stu-id="1e138-333">The visibility of the component's members in the base class must be `protected` or `public` to be visible to the component class.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="1e138-334">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="1e138-334">Additional resources</span></span>

<span data-ttu-id="1e138-335">Předchozí není vyčerpávající zacházení se všemi aspekty komponent Blazor.</span><span class="sxs-lookup"><span data-stu-id="1e138-335">The preceding isn't an exhaustive treatment of all aspects of Blazor components.</span></span> <span data-ttu-id="1e138-336">Další informace o [tom,](/aspnet/core/blazor/components)jak vytvořit a používat ASP.NET komponenty Core Razor , naleznete v dokumentaci k Blazoru.</span><span class="sxs-lookup"><span data-stu-id="1e138-336">For more information on how to [Create and use ASP.NET Core Razor components](/aspnet/core/blazor/components), see the Blazor documentation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="1e138-337">[Předchozí](app-startup.md)
>[další](pages-routing-layouts.md)</span><span class="sxs-lookup"><span data-stu-id="1e138-337">[Previous](app-startup.md)
[Next](pages-routing-layouts.md)</span></span>
