---
title: Sestavení opakovaně použitelných součástí uživatelského rozhraní pomocí Blazor
description: Naučte se sestavovat znovu použitelné součásti uživatelského rozhraní pomocí Blazor a jak se porovnávají s ovládacími prvky webových formulářů ASP.NET.
author: danroth27
ms.author: daroth
ms.date: 09/18/2019
ms.openlocfilehash: 1a5f6b63143c4fd7a276219b9c4877e9e355c996
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378324"
---
# <a name="build-reusable-ui-components-with-blazor"></a><span data-ttu-id="38eb6-103">Sestavení opakovaně použitelných součástí uživatelského rozhraní pomocí Blazor</span><span class="sxs-lookup"><span data-stu-id="38eb6-103">Build reusable UI components with Blazor</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="38eb6-104">Jednou ze skvělých věcí o webových formulářích ASP.NET je to, jak umožňuje zapouzdření opakovaně použitelných částí kódu uživatelského rozhraní (UI) do opakovaně použitelných ovládacích prvků uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="38eb6-104">One of the beautiful things about ASP.NET Web Forms is how it enables encapsulation of reusable pieces of user interface (UI) code into reusable UI controls.</span></span> <span data-ttu-id="38eb6-105">Vlastní uživatelské ovládací prvky lze definovat v označení pomocí souborů *. ascx* .</span><span class="sxs-lookup"><span data-stu-id="38eb6-105">Custom user controls can be defined in markup using *.ascx* files.</span></span> <span data-ttu-id="38eb6-106">Můžete také vytvořit podrobné serverové ovládací prvky v kódu s podporou plného návrháře.</span><span class="sxs-lookup"><span data-stu-id="38eb6-106">You can also build elaborate server controls in code with full designer support.</span></span>

<span data-ttu-id="38eb6-107">Blazor také podporuje zapouzdření uživatelského rozhraní prostřednictvím *komponent*.</span><span class="sxs-lookup"><span data-stu-id="38eb6-107">Blazor also supports UI encapsulation through *components*.</span></span> <span data-ttu-id="38eb6-108">Součást:</span><span class="sxs-lookup"><span data-stu-id="38eb6-108">A component:</span></span>

- <span data-ttu-id="38eb6-109">Je samostatně obsažený blok uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="38eb6-109">Is a self-contained chunk of UI.</span></span>
- <span data-ttu-id="38eb6-110">Udržuje vlastní logiku stavu a vykreslování.</span><span class="sxs-lookup"><span data-stu-id="38eb6-110">Maintains its own state and rendering logic.</span></span>
- <span data-ttu-id="38eb6-111">Může definovat obslužné rutiny událostí uživatelského rozhraní, vytvořit vazby na vstupní data a spravovat svůj životní cyklus.</span><span class="sxs-lookup"><span data-stu-id="38eb6-111">Can define UI event handlers, bind to input data, and manage its own lifecycle.</span></span>
- <span data-ttu-id="38eb6-112">Je obvykle definováno v souboru *. Razor* pomocí syntaxe Razor.</span><span class="sxs-lookup"><span data-stu-id="38eb6-112">Is typically defined in a *.razor* file using Razor syntax.</span></span>

## <a name="an-introduction-to-razor"></a><span data-ttu-id="38eb6-113">Úvod do Razor</span><span class="sxs-lookup"><span data-stu-id="38eb6-113">An introduction to Razor</span></span>

<span data-ttu-id="38eb6-114">Razor je šablonování jazyk založený na jazyce HTML a jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="38eb6-114">Razor is a light-weight markup templating language based on HTML and C#.</span></span> <span data-ttu-id="38eb6-115">Pomocí Razor můžete hladce přejít mezi značkami a kódem jazyka C# a definovat logiku vykreslování komponent.</span><span class="sxs-lookup"><span data-stu-id="38eb6-115">With Razor, you can seamlessly transition between markup and C# code to define your component rendering logic.</span></span> <span data-ttu-id="38eb6-116">Když je soubor *. Razor* zkompilován, je logika vykreslování zachycena strukturovaným způsobem ve třídě .NET.</span><span class="sxs-lookup"><span data-stu-id="38eb6-116">When the *.razor* file is compiled, the rendering logic is captured in a structured way in a .NET class.</span></span> <span data-ttu-id="38eb6-117">Název zkompilované třídy je pořízen z názvu souboru *. Razor* .</span><span class="sxs-lookup"><span data-stu-id="38eb6-117">The name of the compiled class is taken from the *.razor* file name.</span></span> <span data-ttu-id="38eb6-118">Obor názvů je pořízen z výchozího oboru názvů pro projekt a cestu ke složce, nebo můžete explicitně zadat obor názvů pomocí `@namespace` direktivy (Další informace o direktivách Razor níže).</span><span class="sxs-lookup"><span data-stu-id="38eb6-118">The namespace is taken from the default namespace for the project and the folder path, or you can explicitly specify the namespace using the `@namespace` directive (more on Razor directives below).</span></span>

<span data-ttu-id="38eb6-119">Logika vykreslování komponenty je vytvořena pomocí normální značky HTML s dynamickou logikou přidanou pomocí jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="38eb6-119">A component's rendering logic is authored using normal HTML markup with dynamic logic added using C#.</span></span> <span data-ttu-id="38eb6-120">`@`Znak slouží k přechodu do jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="38eb6-120">The `@` character is used to transition to C#.</span></span> <span data-ttu-id="38eb6-121">Základní informace o tom, jak se přepnul zpátky na HTML, je obvykle inteligentní.</span><span class="sxs-lookup"><span data-stu-id="38eb6-121">Razor is typically smart about figuring out when you've switched back to HTML.</span></span> <span data-ttu-id="38eb6-122">Například následující komponenta vykreslí `<p>` značku s aktuálním časem:</span><span class="sxs-lookup"><span data-stu-id="38eb6-122">For example, the following component renders a `<p>` tag with the current time:</span></span>

```razor
<p>@DateTime.Now</p>
```

<span data-ttu-id="38eb6-123">Chcete-li explicitně zadat začátek a konec výrazu jazyka C#, použijte závorky:</span><span class="sxs-lookup"><span data-stu-id="38eb6-123">To explicitly specify the beginning and ending of a C# expression, use parentheses:</span></span>

```razor
<p>@(DateTime.Now)</p>
```

<span data-ttu-id="38eb6-124">Razor také usnadňuje použití toku řízení jazyka C# ve vaší logice vykreslování.</span><span class="sxs-lookup"><span data-stu-id="38eb6-124">Razor also makes it easy to use C# control flow in your rendering logic.</span></span> <span data-ttu-id="38eb6-125">Například můžete podmíněně vykreslit nějaký HTML podobný:</span><span class="sxs-lookup"><span data-stu-id="38eb6-125">For example, you can conditionally render some HTML like this:</span></span>

```razor
@if (value % 2 == 0)
{
    <p>The value was even.</p>
}
```

<span data-ttu-id="38eb6-126">Nebo můžete vygenerovat seznam položek pomocí normální smyčky jazyka C#, `foreach` jako je tato:</span><span class="sxs-lookup"><span data-stu-id="38eb6-126">Or you can generate a list of items using a normal C# `foreach` loop like this:</span></span>

```razor
<ul>
@foreach (var item in items)
{
    <li>@item.Text</li>
}
</ul>
```

<span data-ttu-id="38eb6-127">Direktivy Razor, například direktivy ve webových formulářích ASP.NET, řídí mnoho aspektů, jak je kompilována komponenta Razor.</span><span class="sxs-lookup"><span data-stu-id="38eb6-127">Razor directives, like directives in ASP.NET Web Forms, control many aspects of how a Razor component is compiled.</span></span> <span data-ttu-id="38eb6-128">Příklady zahrnují komponentu:</span><span class="sxs-lookup"><span data-stu-id="38eb6-128">Examples include the component's:</span></span>

- <span data-ttu-id="38eb6-129">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="38eb6-129">Namespace</span></span>
- <span data-ttu-id="38eb6-130">Základní třída</span><span class="sxs-lookup"><span data-stu-id="38eb6-130">Base class</span></span>
- <span data-ttu-id="38eb6-131">Implementovaná rozhraní</span><span class="sxs-lookup"><span data-stu-id="38eb6-131">Implemented interfaces</span></span>
- <span data-ttu-id="38eb6-132">Obecné parametry</span><span class="sxs-lookup"><span data-stu-id="38eb6-132">Generic parameters</span></span>
- <span data-ttu-id="38eb6-133">Importované obory názvů</span><span class="sxs-lookup"><span data-stu-id="38eb6-133">Imported namespaces</span></span>
- <span data-ttu-id="38eb6-134">Trasy</span><span class="sxs-lookup"><span data-stu-id="38eb6-134">Routes</span></span>

<span data-ttu-id="38eb6-135">Direktivy Razor začínají `@` znakem a jsou obvykle použity na začátku nového řádku na začátku souboru.</span><span class="sxs-lookup"><span data-stu-id="38eb6-135">Razor directives start with the `@` character and are typically used at the start of a new line at the start of the file.</span></span> <span data-ttu-id="38eb6-136">Například `@namespace` direktiva definuje obor názvů komponenty:</span><span class="sxs-lookup"><span data-stu-id="38eb6-136">For example, the `@namespace` directive defines the component's namespace:</span></span>

```razor
@namespace MyComponentNamespace
```

<span data-ttu-id="38eb6-137">Následující tabulka shrnuje různé direktivy Razor používané v Blazor a jejich ekvivalenty webových formulářů ASP.NET, pokud existují.</span><span class="sxs-lookup"><span data-stu-id="38eb6-137">The following table summarizes the various Razor directives used in Blazor and their ASP.NET Web Forms equivalents, if they exist.</span></span>

|<span data-ttu-id="38eb6-138">Směrnici</span><span class="sxs-lookup"><span data-stu-id="38eb6-138">Directive</span></span>    |<span data-ttu-id="38eb6-139">Popis</span><span class="sxs-lookup"><span data-stu-id="38eb6-139">Description</span></span>|<span data-ttu-id="38eb6-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="38eb6-140">Example</span></span>|<span data-ttu-id="38eb6-141">Ekvivalentní webové formuláře</span><span class="sxs-lookup"><span data-stu-id="38eb6-141">Web Forms equivalent</span></span>|
|-------------|-----------|-------|--------------------|
|`@attribute` |<span data-ttu-id="38eb6-142">Přidá do komponenty atribut na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="38eb6-142">Adds a class-level attribute to the component</span></span>|`@attribute [Authorize]`|<span data-ttu-id="38eb6-143">Žádné</span><span class="sxs-lookup"><span data-stu-id="38eb6-143">None</span></span>|
|`@code`      |<span data-ttu-id="38eb6-144">Přidá do komponenty členy třídy.</span><span class="sxs-lookup"><span data-stu-id="38eb6-144">Adds class members to the component</span></span>|`@code { ... }`|`<script runat="server">...</script>`|
|`@implements`|<span data-ttu-id="38eb6-145">Implementuje zadané rozhraní.</span><span class="sxs-lookup"><span data-stu-id="38eb6-145">Implements the specified interface</span></span>|`@implements IDisposable`|<span data-ttu-id="38eb6-146">Použití kódu na pozadí</span><span class="sxs-lookup"><span data-stu-id="38eb6-146">Use code-behind</span></span>|
|`@inherits`  |<span data-ttu-id="38eb6-147">Dědí ze zadané základní třídy.</span><span class="sxs-lookup"><span data-stu-id="38eb6-147">Inherits from the specified base class</span></span>|`@inherits MyComponentBase`|`<%@ Control Inherits="MyUserControlBase" %>`|
|`@inject`    |<span data-ttu-id="38eb6-148">Vloží službu do komponenty.</span><span class="sxs-lookup"><span data-stu-id="38eb6-148">Injects a service into the component</span></span>|`@inject IJSRuntime JS`|<span data-ttu-id="38eb6-149">Žádné</span><span class="sxs-lookup"><span data-stu-id="38eb6-149">None</span></span>|
|`@layout`    |<span data-ttu-id="38eb6-150">Určuje komponentu rozložení pro komponentu.</span><span class="sxs-lookup"><span data-stu-id="38eb6-150">Specifies a layout component for the component</span></span>|`@layout MainLayout`|`<%@ Page MasterPageFile="~/Site.Master" %>`|
|`@namespace` |<span data-ttu-id="38eb6-151">Nastaví obor názvů pro komponentu.</span><span class="sxs-lookup"><span data-stu-id="38eb6-151">Sets the namespace for the component</span></span>|`@namespace MyNamespace`|<span data-ttu-id="38eb6-152">Žádné</span><span class="sxs-lookup"><span data-stu-id="38eb6-152">None</span></span>|
|`@page`      |<span data-ttu-id="38eb6-153">Určuje trasu pro komponentu.</span><span class="sxs-lookup"><span data-stu-id="38eb6-153">Specifies the route for the component</span></span>|`@page "/product/{id}"`|`<%@ Page %>`|
|`@typeparam` |<span data-ttu-id="38eb6-154">Určuje parametr obecného typu pro komponentu.</span><span class="sxs-lookup"><span data-stu-id="38eb6-154">Specifies a generic type parameter for the component</span></span>|`@typeparam TItem`|<span data-ttu-id="38eb6-155">Použití kódu na pozadí</span><span class="sxs-lookup"><span data-stu-id="38eb6-155">Use code-behind</span></span>|
|`@using`     |<span data-ttu-id="38eb6-156">Určuje obor názvů, který se má uvést do oboru.</span><span class="sxs-lookup"><span data-stu-id="38eb6-156">Specifies a namespace to bring into scope</span></span>|`@using MyComponentNamespace`|<span data-ttu-id="38eb6-157">Přidat obor názvů do *souboru Web. config*</span><span class="sxs-lookup"><span data-stu-id="38eb6-157">Add namespace in *web.config*</span></span>|

<span data-ttu-id="38eb6-158">Komponenty Razor také usnadňují rozsáhlé použití *atributů direktiv* u elementů pro řízení různých aspektů, jak se komponenty dostanou kompilovat (zpracování událostí, vázání dat, komponenta & odkazů na prvky a tak dále).</span><span class="sxs-lookup"><span data-stu-id="38eb6-158">Razor components also make extensive use of *directive attributes* on elements to control various aspects of how components get compiled (event handling, data binding, component & element references, and so on).</span></span> <span data-ttu-id="38eb6-159">Atribut direktivy All se řídí společnou obecnou syntaxí, kde jsou hodnoty v závorkách volitelné:</span><span class="sxs-lookup"><span data-stu-id="38eb6-159">Directive attributes all follow a common generic syntax where the values in parenthesis are optional:</span></span>

```razor
@directive(-suffix(:name))(="value")
```

<span data-ttu-id="38eb6-160">Následující tabulka shrnuje různé atributy pro direktivy Razor používané v Blazor.</span><span class="sxs-lookup"><span data-stu-id="38eb6-160">The following table summarizes the various attributes for Razor directives used in Blazor.</span></span>

|<span data-ttu-id="38eb6-161">Atribut</span><span class="sxs-lookup"><span data-stu-id="38eb6-161">Attribute</span></span>    |<span data-ttu-id="38eb6-162">Popis</span><span class="sxs-lookup"><span data-stu-id="38eb6-162">Description</span></span>|<span data-ttu-id="38eb6-163">Příklad</span><span class="sxs-lookup"><span data-stu-id="38eb6-163">Example</span></span>|
|-------------|-----------|-------|
|`@attributes`|<span data-ttu-id="38eb6-164">Vykreslí slovník atributů.</span><span class="sxs-lookup"><span data-stu-id="38eb6-164">Renders a dictionary of attributes</span></span>|`<input @attributes="ExtraAttributes" />`|
|`@bind`      |<span data-ttu-id="38eb6-165">Vytvoří obousměrnou datovou vazbu</span><span class="sxs-lookup"><span data-stu-id="38eb6-165">Creates a two-way data binding</span></span>    |`<input @bind="username" @bind:event="oninput" />`|
|`@on{event}` |<span data-ttu-id="38eb6-166">Přidá obslužnou rutinu události pro určenou událost.</span><span class="sxs-lookup"><span data-stu-id="38eb6-166">Adds an event handler for the specified event</span></span>|`<button @onclick="IncrementCount">Click me!</button>`|
|`@key`       |<span data-ttu-id="38eb6-167">Určuje klíč, který má být použit rozdílovým algoritmem pro zachování prvků v kolekci.</span><span class="sxs-lookup"><span data-stu-id="38eb6-167">Specifies a key to be used by the diffing algorithm for preserving elements in a collection</span></span>|`<DetailsEditor @key="person" Details="person.Details" />`|
|`@ref`       |<span data-ttu-id="38eb6-168">Zachycuje odkaz na komponentu nebo HTML element.</span><span class="sxs-lookup"><span data-stu-id="38eb6-168">Captures a reference to the component or HTML element</span></span>|`<MyDialog @ref="myDialog" />`|

<span data-ttu-id="38eb6-169">Různé atributy direktiv používané Blazor ( `@onclick` , `@bind` , `@ref` a tak dále) jsou popsány v následujících částech a v pozdějších kapitolách.</span><span class="sxs-lookup"><span data-stu-id="38eb6-169">The various directive attributes used by Blazor (`@onclick`, `@bind`, `@ref`, and so on) are covered in the sections below and later chapters.</span></span>

<span data-ttu-id="38eb6-170">Mnohé z syntaxí používaných v souborech *. aspx* a *. ascx* mají paralelní syntaxe v Razor.</span><span class="sxs-lookup"><span data-stu-id="38eb6-170">Many of the syntaxes used in *.aspx* and *.ascx* files have parallel syntaxes in Razor.</span></span> <span data-ttu-id="38eb6-171">Níže je jednoduché porovnání syntaxí pro webové formuláře ASP.NET a Razor.</span><span class="sxs-lookup"><span data-stu-id="38eb6-171">Below is a simple comparison of the syntaxes for ASP.NET Web Forms and Razor.</span></span>

|<span data-ttu-id="38eb6-172">Funkce</span><span class="sxs-lookup"><span data-stu-id="38eb6-172">Feature</span></span>                      |<span data-ttu-id="38eb6-173">webové formuláře</span><span class="sxs-lookup"><span data-stu-id="38eb6-173">Web Forms</span></span>           |<span data-ttu-id="38eb6-174">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38eb6-174">Syntax</span></span>               |<span data-ttu-id="38eb6-175">Razor</span><span class="sxs-lookup"><span data-stu-id="38eb6-175">Razor</span></span>         |<span data-ttu-id="38eb6-176">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38eb6-176">Syntax</span></span> |
|-----------------------------|--------------------|---------------------|--------------|-------|
|<span data-ttu-id="38eb6-177">Direktivy</span><span class="sxs-lookup"><span data-stu-id="38eb6-177">Directives</span></span>                   |`<%@ [directive] %>`|`<%@ Page %>`        |`@[directive]`|`@page`|
|<span data-ttu-id="38eb6-178">Bloky kódu</span><span class="sxs-lookup"><span data-stu-id="38eb6-178">Code blocks</span></span>                  |`<% %>`             |`<% int x = 123; %>` |`@{ }`        |`@{ int x = 123; }`|
|<span data-ttu-id="38eb6-179">Výrazy</span><span class="sxs-lookup"><span data-stu-id="38eb6-179">Expressions</span></span><br><span data-ttu-id="38eb6-180">(Kódovaný v HTML)</span><span class="sxs-lookup"><span data-stu-id="38eb6-180">(HTML-encoded)</span></span>|`<%: %>`            |`<%:DateTime.Now %>` |<span data-ttu-id="38eb6-181">Nepřímo`@`</span><span class="sxs-lookup"><span data-stu-id="38eb6-181">Implicit: `@`</span></span><br><span data-ttu-id="38eb6-182">Explicitně`@()`</span><span class="sxs-lookup"><span data-stu-id="38eb6-182">Explicit: `@()`</span></span>|`@DateTime.Now`<br>`@(DateTime.Now)`|
|<span data-ttu-id="38eb6-183">Komentáře</span><span class="sxs-lookup"><span data-stu-id="38eb6-183">Comments</span></span>                     |`<%-- --%>`         |`<%-- Commented --%>`|`@* *@`       |`@* Commented *@`|
|<span data-ttu-id="38eb6-184">Datová vazba</span><span class="sxs-lookup"><span data-stu-id="38eb6-184">Data binding</span></span>                 |`<%# %>`            |`<%# Bind("Name") %>`|`@bind`       |`<input @bind="username" />`|

<span data-ttu-id="38eb6-185">Chcete-li přidat členy do třídy komponenty Razor, použijte `@code` direktivu.</span><span class="sxs-lookup"><span data-stu-id="38eb6-185">To add members to the Razor component class, use the `@code` directive.</span></span> <span data-ttu-id="38eb6-186">Tato technika je podobná použití `<script runat="server">...</script>` bloku v uživatelském ovládacím prvku nebo stránce webových formulářů ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="38eb6-186">This technique is similar to using a `<script runat="server">...</script>` block in an ASP.NET Web Forms user control or page.</span></span>

```razor
@code {
    int count = 0;

    void IncrementCount()
    {
        count++;
    }
}
```

<span data-ttu-id="38eb6-187">Vzhledem k tomu, že je Razor založen na jazyce C#, musí být zkompilován z projektu jazyka C# (*. csproj*).</span><span class="sxs-lookup"><span data-stu-id="38eb6-187">Because Razor is based on C#, it must be compiled from within a C# project (*.csproj*).</span></span> <span data-ttu-id="38eb6-188">Soubory *. Razor* nemůžete kompilovat z Visual Basicho projektu (*. vbproj*).</span><span class="sxs-lookup"><span data-stu-id="38eb6-188">You can't compile *.razor* files from a Visual Basic project (*.vbproj*).</span></span> <span data-ttu-id="38eb6-189">Stále můžete odkazovat na Visual Basic projekty z projektu Blazor.</span><span class="sxs-lookup"><span data-stu-id="38eb6-189">You can still reference Visual Basic projects from your Blazor project.</span></span> <span data-ttu-id="38eb6-190">Opak je pravda.</span><span class="sxs-lookup"><span data-stu-id="38eb6-190">The opposite is true too.</span></span>

<span data-ttu-id="38eb6-191">Úplný odkaz na syntaxe Razor naleznete v tématu [syntaxe Razor reference for ASP.NET Core](/aspnet/core/mvc/views/razor).</span><span class="sxs-lookup"><span data-stu-id="38eb6-191">For a full Razor syntax reference, see [Razor syntax reference for ASP.NET Core](/aspnet/core/mvc/views/razor).</span></span>

## <a name="use-components"></a><span data-ttu-id="38eb6-192">Použití komponent</span><span class="sxs-lookup"><span data-stu-id="38eb6-192">Use components</span></span>

<span data-ttu-id="38eb6-193">Kromě normálního formátu HTML mohou komponenty také použít jiné komponenty jako součást logiky vykreslování.</span><span class="sxs-lookup"><span data-stu-id="38eb6-193">Aside from normal HTML, components can also use other components as part of their rendering logic.</span></span> <span data-ttu-id="38eb6-194">Syntaxe pro použití komponenty v Razor je podobná použití uživatelského ovládacího prvku v aplikaci webových formulářů ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="38eb6-194">The syntax for using a component in Razor is similar to using a user control in an ASP.NET Web Forms app.</span></span> <span data-ttu-id="38eb6-195">Komponenty jsou určeny pomocí značky elementu, který odpovídá názvu typu komponenty.</span><span class="sxs-lookup"><span data-stu-id="38eb6-195">Components are specified using an element tag that matches the type name of the component.</span></span> <span data-ttu-id="38eb6-196">Například můžete přidat `Counter` komponentu podobné této:</span><span class="sxs-lookup"><span data-stu-id="38eb6-196">For example, you can add a `Counter` component like this:</span></span>

```razor
<Counter />
```

<span data-ttu-id="38eb6-197">Na rozdíl od webových formulářů ASP.NET, komponent v Blazor:</span><span class="sxs-lookup"><span data-stu-id="38eb6-197">Unlike ASP.NET Web Forms, components in Blazor:</span></span>

- <span data-ttu-id="38eb6-198">Nepoužívejte předponu elementu (například `asp:` ).</span><span class="sxs-lookup"><span data-stu-id="38eb6-198">Don't use an element prefix (for example, `asp:`).</span></span>
- <span data-ttu-id="38eb6-199">Nevyžaduje registraci na stránce nebo v *souboru Web. config*.</span><span class="sxs-lookup"><span data-stu-id="38eb6-199">Don't require registration on the page or in the *web.config*.</span></span>

<span data-ttu-id="38eb6-200">Komponenty Razor si můžete představit jako typy .NET, protože jsou přesně to, co jsou.</span><span class="sxs-lookup"><span data-stu-id="38eb6-200">Think of Razor components like you would .NET types, because that's exactly what they are.</span></span> <span data-ttu-id="38eb6-201">Pokud je odkazováno na sestavení obsahující komponentu, je součást k dispozici pro použití.</span><span class="sxs-lookup"><span data-stu-id="38eb6-201">If the assembly containing the component is referenced, then the component is available for use.</span></span> <span data-ttu-id="38eb6-202">Chcete-li převést obor názvů komponenty do oboru, použijte `@using` direktivu:</span><span class="sxs-lookup"><span data-stu-id="38eb6-202">To bring the component's namespace into scope, apply the `@using` directive:</span></span>

```razor
@using MyComponentLib

<Counter />
```

<span data-ttu-id="38eb6-203">Jak je vidět ve výchozích projektech Blazor, je běžné umístit `@using` direktivy do souboru *_Imports. Razor* tak, aby byly importovány do všech souborů *. Razor* ve stejném adresáři a v podřízených adresářích.</span><span class="sxs-lookup"><span data-stu-id="38eb6-203">As seen in the default Blazor projects, it's common to put `@using` directives into a *_Imports.razor* file so that they're imported into all *.razor* files in the same directory and in child directories.</span></span>

<span data-ttu-id="38eb6-204">Pokud obor názvů pro komponentu není v oboru, můžete určit komponentu pomocí jejího úplného názvu typu, jak je možné v jazyce C#:</span><span class="sxs-lookup"><span data-stu-id="38eb6-204">If the namespace for a component isn't in scope, you can specify a component using its full type name, as you can in C#:</span></span>

```razor
<MyComponentLib.Counter />
```

## <a name="component-parameters"></a><span data-ttu-id="38eb6-205">Parametry součásti</span><span class="sxs-lookup"><span data-stu-id="38eb6-205">Component parameters</span></span>

<span data-ttu-id="38eb6-206">Ve webových formulářích ASP.NET můžete Flow parametry a data do ovládacích prvků pomocí veřejných vlastností.</span><span class="sxs-lookup"><span data-stu-id="38eb6-206">In ASP.NET Web Forms, you can flow parameters and data to controls using public properties.</span></span> <span data-ttu-id="38eb6-207">Tyto vlastnosti lze nastavit v kódu pomocí atributů nebo nastavit přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="38eb6-207">These properties can be set in markup using attributes or set directly in code.</span></span> <span data-ttu-id="38eb6-208">Komponenty Blazor fungují podobným způsobem, i když vlastnosti komponenty musí být označeny také `[Parameter]` atributem, který má být považován za parametr komponenty.</span><span class="sxs-lookup"><span data-stu-id="38eb6-208">Blazor components work in a similar fashion, although the component properties must also be marked with the `[Parameter]` attribute to be considered component parameters.</span></span>

<span data-ttu-id="38eb6-209">Následující `Counter` Komponenta definuje parametr komponenty s názvem `IncrementAmount` , který lze použít k určení množství, které se má `Counter` zvýšit při každém kliknutí na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="38eb6-209">The following `Counter` component defines a component parameter called `IncrementAmount` that can be used to specify the amount that the `Counter` should be incremented each time the button is clicked.</span></span>

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

<span data-ttu-id="38eb6-210">Chcete-li určit parametr komponenty v Blazor, použijte atribut jako ve webových formulářích ASP.NET:</span><span class="sxs-lookup"><span data-stu-id="38eb6-210">To specify a component parameter in Blazor, use an attribute as you would in ASP.NET Web Forms:</span></span>

```razor
<Counter IncrementAmount="10" />
```

## <a name="event-handlers"></a><span data-ttu-id="38eb6-211">Obslužné rutiny událostí</span><span class="sxs-lookup"><span data-stu-id="38eb6-211">Event handlers</span></span>

<span data-ttu-id="38eb6-212">Webové formuláře ASP.NET a Blazor poskytují programovací model založený na událostech pro zpracování událostí uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="38eb6-212">Both ASP.NET Web Forms and Blazor provide an event-based programming model for handling UI events.</span></span> <span data-ttu-id="38eb6-213">Příklady takových událostí zahrnují kliknutí na tlačítko a textové zadání.</span><span class="sxs-lookup"><span data-stu-id="38eb6-213">Examples of such events include button clicks and text input.</span></span> <span data-ttu-id="38eb6-214">Ve webových formulářích ASP.NET používáte ovládací prvky HTML serveru pro zpracování událostí uživatelského rozhraní vystavených modelem DOM, nebo můžete zpracovávat události vystavené ovládacími prvky webového serveru.</span><span class="sxs-lookup"><span data-stu-id="38eb6-214">In ASP.NET Web Forms, you use HTML server controls to handle UI events exposed by the DOM, or you can handle events exposed by web server controls.</span></span> <span data-ttu-id="38eb6-215">Události jsou na serveru umístěny prostřednictvím požadavků po návratu do formuláře.</span><span class="sxs-lookup"><span data-stu-id="38eb6-215">The events are surfaced on the server through form post-back requests.</span></span> <span data-ttu-id="38eb6-216">Vezměte v úvahu následující tlačítko Web Forms klikněte na příklad:</span><span class="sxs-lookup"><span data-stu-id="38eb6-216">Consider the following Web Forms button click example:</span></span>

<span data-ttu-id="38eb6-217">*Čítač. ascx*</span><span class="sxs-lookup"><span data-stu-id="38eb6-217">*Counter.ascx*</span></span>

```aspx-csharp
<asp:Button ID="ClickMeButton" runat="server" Text="Click me!" OnClick="ClickMeButton_Click" />
```

<span data-ttu-id="38eb6-218">*Counter.ascx.cs*</span><span class="sxs-lookup"><span data-stu-id="38eb6-218">*Counter.ascx.cs*</span></span>

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void ClickMeButton_Click(object sender, EventArgs e)
    {
        Console.WriteLine("The button was clicked!");
    }
}
```

<span data-ttu-id="38eb6-219">V Blazor můžete zaregistrovat obslužné rutiny pro události uživatelského rozhraní modelu DOM přímo pomocí atributů direktiv formuláře `@on{event}` .</span><span class="sxs-lookup"><span data-stu-id="38eb6-219">In Blazor, you can register handlers for DOM UI events directly using directive attributes of the form `@on{event}`.</span></span> <span data-ttu-id="38eb6-220">`{event}`Zástupný symbol představuje název události.</span><span class="sxs-lookup"><span data-stu-id="38eb6-220">The `{event}` placeholder represents the name of the event.</span></span> <span data-ttu-id="38eb6-221">Například můžete naslouchat tomu, že kliknete na tlačítko takto:</span><span class="sxs-lookup"><span data-stu-id="38eb6-221">For example, you can listen for button clicks like this:</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick()
    {
        Console.WriteLine("The button was clicked!);
    }
}
```

<span data-ttu-id="38eb6-222">Obslužné rutiny událostí mohou pro poskytnutí dalších informací o události přijmout volitelný argument specifický pro událost.</span><span class="sxs-lookup"><span data-stu-id="38eb6-222">Event handlers can accept an optional, event-specific argument to provide more information about the event.</span></span> <span data-ttu-id="38eb6-223">Například události myši mohou mít `MouseEventArgs` argument, ale není to vyžadováno.</span><span class="sxs-lookup"><span data-stu-id="38eb6-223">For example, mouse events can take a `MouseEventArgs` argument, but it isn't required.</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick(MouseEventArgs e)
    {
        Console.WriteLine($"Mouse clicked at {e.ScreenX}, {e.ScreenY}.");
    }
}
```

<span data-ttu-id="38eb6-224">Namísto odkazování na skupinu metod pro obslužnou rutinu události lze použít výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="38eb6-224">Instead of referring to a method group for an event handler, you can use a lambda expression.</span></span> <span data-ttu-id="38eb6-225">Výraz lambda umožňuje zavřít jiné hodnoty v oboru.</span><span class="sxs-lookup"><span data-stu-id="38eb6-225">A lambda expression allows you to close over other in-scope values.</span></span>

```razor
@foreach (var buttonLabel in buttonLabels)
{
    <button @onclick="() => Console.WriteLine($"The {buttonLabel} button was clicked!")">@buttonLabel</button>
}
```

<span data-ttu-id="38eb6-226">Obslužné rutiny událostí lze provádět synchronně nebo asynchronně.</span><span class="sxs-lookup"><span data-stu-id="38eb6-226">Event handlers can execute synchronously or asynchronously.</span></span> <span data-ttu-id="38eb6-227">Například následující `OnClick` obslužná rutina události se provádí asynchronně:</span><span class="sxs-lookup"><span data-stu-id="38eb6-227">For example, the following `OnClick` event handler executes asynchronously:</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    async Task OnClick()
    {
        var result = await Http.GetAsync("api/values");
    }
}
```

<span data-ttu-id="38eb6-228">Po zpracování události se komponenta vykreslí do účtu pro všechny změny stavu součásti.</span><span class="sxs-lookup"><span data-stu-id="38eb6-228">After an event is handled, the component is rendered to account for any component state changes.</span></span> <span data-ttu-id="38eb6-229">Pomocí asynchronních obslužných rutin událostí je komponenta vykreslena ihned po dokončení provádění obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="38eb6-229">With asynchronous event handlers, the component is rendered immediately after the handler execution completes.</span></span> <span data-ttu-id="38eb6-230">Komponenta se po dokončení asynchronního vykreslí *znovu* `Task` .</span><span class="sxs-lookup"><span data-stu-id="38eb6-230">The component is rendered *again* after the asynchronous `Task` completes.</span></span> <span data-ttu-id="38eb6-231">Tento režim asynchronního spuštění nabízí možnost vykreslit některé vhodné uživatelské rozhraní, když `Task` je asynchronní operace stále probíhá.</span><span class="sxs-lookup"><span data-stu-id="38eb6-231">This asynchronous execution mode provides an opportunity to render some appropriate UI while the asynchronous `Task` is still in progress.</span></span>

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

<span data-ttu-id="38eb6-232">Komponenty mohou také definovat vlastní události definováním parametru součásti typu `EventCallback<TValue>` .</span><span class="sxs-lookup"><span data-stu-id="38eb6-232">Components can also define their own events by defining a component parameter of type `EventCallback<TValue>`.</span></span> <span data-ttu-id="38eb6-233">Zpětná volání událostí podporují všechny variace obslužných rutin událostí rozhraní modelu DOM: nepovinné argumenty, synchronní nebo asynchronní, skupiny metod nebo výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="38eb6-233">Event callbacks support all the variations of DOM UI event handlers: optional arguments, synchronous or asynchronous, method groups, or lambda expressions.</span></span>

```razor
<button class="btn btn-primary" @onclick="OnClick">Click me!</button>

@code {
    [Parameter]
    public EventCallback<MouseEventArgs> OnClick { get; set; }
}
```

## <a name="data-binding"></a><span data-ttu-id="38eb6-234">Datová vazba</span><span class="sxs-lookup"><span data-stu-id="38eb6-234">Data binding</span></span>

<span data-ttu-id="38eb6-235">Blazor poskytuje jednoduchý mechanismus pro svázání dat z komponenty uživatelského rozhraní do stavu komponenty.</span><span class="sxs-lookup"><span data-stu-id="38eb6-235">Blazor provides a simple mechanism to bind data from a UI component to the component's state.</span></span> <span data-ttu-id="38eb6-236">Tento přístup se liší od funkcí ve webových formulářích ASP.NET pro svázání dat ze zdrojů dat až po ovládací prvky uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="38eb6-236">This approach differs from the features in ASP.NET Web Forms for binding data from data sources to UI controls.</span></span> <span data-ttu-id="38eb6-237">Zpracováváme data z různých zdrojů dat v části řešení problémů [s daty](data.md) .</span><span class="sxs-lookup"><span data-stu-id="38eb6-237">We'll cover handling data from different data sources in the [Dealing with data](data.md) section.</span></span>

<span data-ttu-id="38eb6-238">Chcete-li vytvořit obousměrnou datovou vazbu z komponenty uživatelského rozhraní do stavu komponenty, použijte `@bind` atribut direktiva.</span><span class="sxs-lookup"><span data-stu-id="38eb6-238">To create a two-way data binding from a UI component to the component's state, use the `@bind` directive attribute.</span></span> <span data-ttu-id="38eb6-239">V následujícím příkladu je hodnota zaškrtávacího políčka svázána s `isChecked` polem.</span><span class="sxs-lookup"><span data-stu-id="38eb6-239">In the following example, the value of the check box is bound to the `isChecked` field.</span></span>

```razor
<input type="checkbox" @bind="isChecked" />

@code {
    bool isChecked;
}
```

<span data-ttu-id="38eb6-240">Při vykreslení komponenty je hodnota zaškrtávacího políčka nastavena na hodnotu `isChecked` pole.</span><span class="sxs-lookup"><span data-stu-id="38eb6-240">When the component is rendered, the value of the checkbox is set to the value of the `isChecked` field.</span></span> <span data-ttu-id="38eb6-241">Když uživatel přepíná zaškrtávací políčko, `onchange` událost je aktivována a `isChecked` pole je nastaveno na novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="38eb6-241">When the user toggles the checkbox, the `onchange` event is fired and the `isChecked` field is set to the new value.</span></span> <span data-ttu-id="38eb6-242">`@bind`Syntaxe v tomto případě je ekvivalentní následujícímu kódu:</span><span class="sxs-lookup"><span data-stu-id="38eb6-242">The `@bind` syntax in this case is equivalent to the following markup:</span></span>

```razor
<input value="@isChecked" @onchange="(UIChangeEventArgs e) => isChecked = e.Value" />
```

<span data-ttu-id="38eb6-243">Chcete-li změnit událost použitou pro BIND, použijte `@bind:event` atribut.</span><span class="sxs-lookup"><span data-stu-id="38eb6-243">To change the event used for the bind, use the `@bind:event` attribute.</span></span>

```razor
<input @bind="text" @bind:event="oninput" />
<p>@text</p>

@code {
    string text;
}
```

<span data-ttu-id="38eb6-244">Komponenty mohou také podporovat datovou vazbu k jejich parametrům.</span><span class="sxs-lookup"><span data-stu-id="38eb6-244">Components can also support data binding to their parameters.</span></span> <span data-ttu-id="38eb6-245">Pro vázání dat definujte parametr zpětného volání události se stejným názvem, jako má parametr s možností vazby.</span><span class="sxs-lookup"><span data-stu-id="38eb6-245">To data bind, define an event callback parameter with the same name as the bindable parameter.</span></span> <span data-ttu-id="38eb6-246">Do názvu se přidá přípona "změněná".</span><span class="sxs-lookup"><span data-stu-id="38eb6-246">The "Changed" suffix is added to the name.</span></span>

<span data-ttu-id="38eb6-247">*PasswordBox. Razor*</span><span class="sxs-lookup"><span data-stu-id="38eb6-247">*PasswordBox.razor*</span></span>

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

<span data-ttu-id="38eb6-248">Chcete-li zřetězit datovou vazbu k základnímu prvku uživatelského rozhraní, nastavte hodnotu a zpracujte událost přímo na prvku uživatelského rozhraní namísto použití `@bind` atributu.</span><span class="sxs-lookup"><span data-stu-id="38eb6-248">To chain a data binding to an underlying UI element, set the value and handle the event directly on the UI element instead of using the `@bind` attribute.</span></span>

<span data-ttu-id="38eb6-249">Chcete-li vytvořit propojení s parametrem komponenty, použijte `@bind-{Parameter}` atribut k určení parametru, do kterého chcete vytvořit vazby.</span><span class="sxs-lookup"><span data-stu-id="38eb6-249">To bind to a component parameter, use a `@bind-{Parameter}` attribute to specify the parameter to which you want to bind.</span></span>

```razor
<PasswordBox @bind-Password="password" />

@code {
    string password;
}
```

## <a name="state-changes"></a><span data-ttu-id="38eb6-250">Změny stavu</span><span class="sxs-lookup"><span data-stu-id="38eb6-250">State changes</span></span>

<span data-ttu-id="38eb6-251">Pokud se stav součásti změnil mimo normální událost uživatelského rozhraní nebo zpětného volání události, musí komponenta ručně signalizovat, že je nutné ji znovu vykreslit.</span><span class="sxs-lookup"><span data-stu-id="38eb6-251">If the component's state has changed outside of a normal UI event or event callback, then the component must manually signal that it needs to be rendered again.</span></span> <span data-ttu-id="38eb6-252">Chcete-li signalizovat, že došlo ke změně stavu komponenty, zavolejte `StateHasChanged` metodu pro komponentu.</span><span class="sxs-lookup"><span data-stu-id="38eb6-252">To signal that a component's state has changed, call the `StateHasChanged` method on the component.</span></span>

<span data-ttu-id="38eb6-253">V následujícím příkladu komponenta zobrazuje zprávu ze `AppState` služby, kterou lze aktualizovat jinými částmi aplikace.</span><span class="sxs-lookup"><span data-stu-id="38eb6-253">In the example below, a component displays a message from an `AppState` service that can be updated by other parts of the app.</span></span> <span data-ttu-id="38eb6-254">Komponenta registruje svou `StateHasChanged` metodu s `AppState.OnChange` událostí tak, aby se komponenta vykreslila pokaždé, když se zpráva aktualizuje.</span><span class="sxs-lookup"><span data-stu-id="38eb6-254">The component registers its `StateHasChanged` method with the `AppState.OnChange` event so that the component is rendered whenever the message gets updated.</span></span>

```csharp
public class AppState
{
    public string Message { get; }

    // Lets components receive change notifications
    public event Action OnChange;

    public void UpdateMessage(string message)
    {
        Message = message;
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

## <a name="component-lifecycle"></a><span data-ttu-id="38eb6-255">Životní cyklus komponent</span><span class="sxs-lookup"><span data-stu-id="38eb6-255">Component lifecycle</span></span>

<span data-ttu-id="38eb6-256">Rozhraní webových formulářů ASP.NET má dobře definované metody životního cyklu pro moduly, stránky a ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="38eb6-256">The ASP.NET Web Forms framework has well-defined lifecycle methods for modules, pages, and controls.</span></span> <span data-ttu-id="38eb6-257">Například následující ovládací prvek implementuje obslužné rutiny událostí pro `Init` `Load` `UnLoad` události životního cyklu, a:</span><span class="sxs-lookup"><span data-stu-id="38eb6-257">For example, the following control implements event handlers for the `Init`, `Load`, and `UnLoad` lifecycle events:</span></span>

<span data-ttu-id="38eb6-258">*Counter.ascx.cs*</span><span class="sxs-lookup"><span data-stu-id="38eb6-258">*Counter.ascx.cs*</span></span>

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void Page_Init(object sender, EventArgs e) { ... }
    protected void Page_Load(object sender, EventArgs e) { ... }
    protected void Page_UnLoad(object sender, EventArgs e) { ... }
}
```

<span data-ttu-id="38eb6-259">Komponenty Blazor mají také dobře definovaný životní cyklus.</span><span class="sxs-lookup"><span data-stu-id="38eb6-259">Blazor components also have a well-defined lifecycle.</span></span> <span data-ttu-id="38eb6-260">Životní cyklus komponenty lze použít k inicializaci stavu součásti a implementaci pokročilého chování komponent.</span><span class="sxs-lookup"><span data-stu-id="38eb6-260">A component's lifecycle can be used to initialize component state and implement advanced component behaviors.</span></span>

<span data-ttu-id="38eb6-261">Všechny metody životního cyklu komponenty Blazor mají synchronní i asynchronní verzi.</span><span class="sxs-lookup"><span data-stu-id="38eb6-261">All of Blazor's component lifecycle methods have both synchronous and asynchronous versions.</span></span> <span data-ttu-id="38eb6-262">Vykreslování součásti je synchronní.</span><span class="sxs-lookup"><span data-stu-id="38eb6-262">Component rendering is synchronous.</span></span> <span data-ttu-id="38eb6-263">Asynchronní logiku nelze spustit jako součást vykreslování komponenty.</span><span class="sxs-lookup"><span data-stu-id="38eb6-263">You can't run asynchronous logic as part of the component rendering.</span></span> <span data-ttu-id="38eb6-264">Veškerá asynchronní logika musí být spuštěna jako součást `async` metody životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="38eb6-264">All asynchronous logic must execute as part of an `async` lifecycle method.</span></span>

### <a name="oninitialized"></a><span data-ttu-id="38eb6-265">Inicializováno</span><span class="sxs-lookup"><span data-stu-id="38eb6-265">OnInitialized</span></span>

<span data-ttu-id="38eb6-266">`OnInitialized`Metody a `OnInitializedAsync` se používají k inicializaci komponenty.</span><span class="sxs-lookup"><span data-stu-id="38eb6-266">The `OnInitialized` and `OnInitializedAsync` methods are used to initialize the component.</span></span> <span data-ttu-id="38eb6-267">Komponenta je obvykle inicializována po jejím prvním vykreslení.</span><span class="sxs-lookup"><span data-stu-id="38eb6-267">A component is typically initialized after it's first rendered.</span></span> <span data-ttu-id="38eb6-268">Po inicializaci komponenty může být vygenerována několikrát, než bude nakonec uvolněna.</span><span class="sxs-lookup"><span data-stu-id="38eb6-268">After a component is initialized, it may be rendered multiple times before it's eventually disposed.</span></span> <span data-ttu-id="38eb6-269">`OnInitialized`Metoda je podobná události na `Page_Load` stránkách a ovládacích prvcích webových formulářů ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="38eb6-269">The `OnInitialized` method is similar to the `Page_Load` event in ASP.NET Web Forms pages and controls.</span></span>

```csharp
protected override void OnInitialized() { ... }
protected override async Task OnInitializedAsync() { await ... }
```

### <a name="onparametersset"></a><span data-ttu-id="38eb6-270">OnParametersSet</span><span class="sxs-lookup"><span data-stu-id="38eb6-270">OnParametersSet</span></span>

<span data-ttu-id="38eb6-271">`OnParametersSet`Metody a `OnParametersSetAsync` jsou volány, když komponenta obdrží parametry z nadřazené položky a hodnota je přiřazena k vlastnostem.</span><span class="sxs-lookup"><span data-stu-id="38eb6-271">The `OnParametersSet` and `OnParametersSetAsync` methods are called when a component has received parameters from its parent and the value are assigned to properties.</span></span> <span data-ttu-id="38eb6-272">Tyto metody jsou spouštěny po inicializaci komponenty a *pokaždé, když je komponenta vykreslena*.</span><span class="sxs-lookup"><span data-stu-id="38eb6-272">These methods are executed after component initialization and *each time the component is rendered*.</span></span>

```csharp
protected override void OnParametersSet() { ... }
protected override async Task OnParametersSetAsync() { await ... }
```

### <a name="onafterrender"></a><span data-ttu-id="38eb6-273">OnAfterRender</span><span class="sxs-lookup"><span data-stu-id="38eb6-273">OnAfterRender</span></span>

<span data-ttu-id="38eb6-274">`OnAfterRender`Metody a `OnAfterRenderAsync` jsou volány po dokončení vykreslování součásti.</span><span class="sxs-lookup"><span data-stu-id="38eb6-274">The `OnAfterRender` and `OnAfterRenderAsync` methods are called after a component has finished rendering.</span></span> <span data-ttu-id="38eb6-275">V tomto bodě jsou zaplněny odkazy na elementy a součásti (Další informace o těchto konceptech).</span><span class="sxs-lookup"><span data-stu-id="38eb6-275">Element and component references are populated at this point (more on these concepts below).</span></span> <span data-ttu-id="38eb6-276">V tuto chvíli je povolená interaktivita v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="38eb6-276">Interactivity with the browser is enabled at this point.</span></span> <span data-ttu-id="38eb6-277">Interakce s modelem DOM a prováděním JavaScriptu můžou bezpečně probíhat.</span><span class="sxs-lookup"><span data-stu-id="38eb6-277">Interactions with the DOM and JavaScript execution can safely take place.</span></span>

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

<span data-ttu-id="38eb6-278">`OnAfterRender`a `OnAfterRenderAsync` *nejsou volány při předvykreslování na serveru*.</span><span class="sxs-lookup"><span data-stu-id="38eb6-278">`OnAfterRender` and `OnAfterRenderAsync` *aren't called when prerendering on the server*.</span></span>

<span data-ttu-id="38eb6-279">`firstRender`Parametr je při `true` prvním vykreslení komponenty, v opačném případě jeho hodnota je `false` .</span><span class="sxs-lookup"><span data-stu-id="38eb6-279">The `firstRender` parameter is `true` the first time the component is rendered; otherwise, its value is `false`.</span></span>

### <a name="idisposable"></a><span data-ttu-id="38eb6-280">IDisposable</span><span class="sxs-lookup"><span data-stu-id="38eb6-280">IDisposable</span></span>

<span data-ttu-id="38eb6-281">Komponenty Blazor mohou implementovat `IDisposable` pro uvolnění prostředků, pokud je komponenta odebrána z uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="38eb6-281">Blazor components can implement `IDisposable` to dispose of resources when the component is removed from the UI.</span></span> <span data-ttu-id="38eb6-282">Komponenta Razor může implementovat `IDispose` pomocí `@implements` direktivy:</span><span class="sxs-lookup"><span data-stu-id="38eb6-282">A Razor component can implement `IDispose` by using the `@implements` directive:</span></span>

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

## <a name="capture-component-references"></a><span data-ttu-id="38eb6-283">Zachytit odkazy na komponenty</span><span class="sxs-lookup"><span data-stu-id="38eb6-283">Capture component references</span></span>

<span data-ttu-id="38eb6-284">Ve webových formulářích ASP.NET je běžné manipulovat s instancí ovládacího prvku přímo v kódu odkazem na jeho ID.</span><span class="sxs-lookup"><span data-stu-id="38eb6-284">In ASP.NET Web Forms, it's common to manipulate a control instance directly in code by referring to its ID.</span></span> <span data-ttu-id="38eb6-285">V Blazor je také možné zachytit odkaz na komponentu a manipulovat s nimi, i když je to mnohem méně běžné.</span><span class="sxs-lookup"><span data-stu-id="38eb6-285">In Blazor, it's also possible to capture and manipulate a reference to a component, although it's much less common.</span></span>

<span data-ttu-id="38eb6-286">Chcete-li zachytit odkaz na komponentu v Blazor, použijte `@ref` atribut direktiva.</span><span class="sxs-lookup"><span data-stu-id="38eb6-286">To capture a component reference in Blazor, use the `@ref` directive attribute.</span></span> <span data-ttu-id="38eb6-287">Hodnota atributu by měla odpovídat názvu nastavitelné pole se stejným typem, jako má Odkazovaná komponenta.</span><span class="sxs-lookup"><span data-stu-id="38eb6-287">The value of the attribute should match the name of a settable field with the same type as the referenced component.</span></span>

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

<span data-ttu-id="38eb6-288">Při vykreslení nadřazené komponenty je pole vyplněno instancí podřízené součásti.</span><span class="sxs-lookup"><span data-stu-id="38eb6-288">When the parent component is rendered, the field is populated with the child component instance.</span></span> <span data-ttu-id="38eb6-289">Pak můžete zavolat metody do nebo jinak manipulovat s instancí součásti.</span><span class="sxs-lookup"><span data-stu-id="38eb6-289">You can then call methods on, or otherwise manipulate, the component instance.</span></span>

<span data-ttu-id="38eb6-290">Manipulace se stavem součásti přímo pomocí odkazů na součásti se nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="38eb6-290">Manipulating component state directly using component references isn't recommended.</span></span> <span data-ttu-id="38eb6-291">Zabráníte tak automatickému vykreslování komponenty ve správných časech.</span><span class="sxs-lookup"><span data-stu-id="38eb6-291">Doing so prevents the component from being rendered automatically at the correct times.</span></span>

## <a name="capture-element-references"></a><span data-ttu-id="38eb6-292">Zachytit odkazy elementu</span><span class="sxs-lookup"><span data-stu-id="38eb6-292">Capture element references</span></span>

<span data-ttu-id="38eb6-293">Komponenty Blazor mohou zachytit odkazy na prvek.</span><span class="sxs-lookup"><span data-stu-id="38eb6-293">Blazor components can capture references to an element.</span></span> <span data-ttu-id="38eb6-294">Na rozdíl od serverových ovládacích prvků HTML ve webových formulářích ASP.NET nemůžete manipulovat s DOM přímo pomocí odkazu elementu v Blazor.</span><span class="sxs-lookup"><span data-stu-id="38eb6-294">Unlike HTML server controls in ASP.NET Web Forms, you can't manipulate the DOM directly using an element reference in Blazor.</span></span> <span data-ttu-id="38eb6-295">Blazor zpracovává většinu interakcí DOM za použití jejich rozdílového algoritmu modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="38eb6-295">Blazor handles most DOM interactions for you using its DOM diffing algorithm.</span></span> <span data-ttu-id="38eb6-296">Zachycené odkazy na prvky v Blazor jsou neprůhledné.</span><span class="sxs-lookup"><span data-stu-id="38eb6-296">Captured element references in Blazor are opaque.</span></span> <span data-ttu-id="38eb6-297">Používají se však k předání konkrétního odkazu na element ve volání interoperability JavaScriptu.</span><span class="sxs-lookup"><span data-stu-id="38eb6-297">However, they're used to pass a specific element reference in a JavaScript interop call.</span></span> <span data-ttu-id="38eb6-298">Další informace o zprostředkovateli komunikace s JavaScriptem naleznete v tématu [ASP.NET Core Blazor JavaScript](/aspnet/core/blazor/javascript-interop).</span><span class="sxs-lookup"><span data-stu-id="38eb6-298">For more information about JavaScript interop, see [ASP.NET Core Blazor JavaScript interop](/aspnet/core/blazor/javascript-interop).</span></span>

## <a name="templated-components"></a><span data-ttu-id="38eb6-299">Komponenty bez vizuálního vzhledu</span><span class="sxs-lookup"><span data-stu-id="38eb6-299">Templated components</span></span>

<span data-ttu-id="38eb6-300">Ve webových formulářích ASP.NET můžete vytvořit *ovládací prvky s šablonami*.</span><span class="sxs-lookup"><span data-stu-id="38eb6-300">In ASP.NET Web Forms, you can create *templated controls*.</span></span> <span data-ttu-id="38eb6-301">Ovládací prvky s šablonou umožňují vývojáři zadat část kódu HTML použitou k vykreslení ovládacího prvku kontejneru.</span><span class="sxs-lookup"><span data-stu-id="38eb6-301">Templated controls enable the developer to specify a portion of the HTML used to render a container control.</span></span> <span data-ttu-id="38eb6-302">Mechanismus sestavování serverových ovládacích prvků na základě šablon je složitý, ale umožňuje výkonné scénáře pro vykreslování dat uživatelsky přizpůsobitelným způsobem.</span><span class="sxs-lookup"><span data-stu-id="38eb6-302">The mechanics of building templated server controls are complex, but they enable powerful scenarios for rendering data in a user customizable way.</span></span> <span data-ttu-id="38eb6-303">Příklady ovládacích prvků s šablonami jsou `Repeater` a `DataList` .</span><span class="sxs-lookup"><span data-stu-id="38eb6-303">Examples of templated controls include `Repeater` and `DataList`.</span></span>

<span data-ttu-id="38eb6-304">Komponenty Blazor lze také šablonou definovat definováním parametrů součásti typu `RenderFragment` nebo `RenderFragment<T>` .</span><span class="sxs-lookup"><span data-stu-id="38eb6-304">Blazor components can also be templated by defining component parameters of type `RenderFragment` or `RenderFragment<T>`.</span></span> <span data-ttu-id="38eb6-305">`RenderFragment`Představuje blok značek Razor, který lze následně vykreslit komponentou.</span><span class="sxs-lookup"><span data-stu-id="38eb6-305">A `RenderFragment` represents a chunk of Razor markup that can then be rendered by the component.</span></span> <span data-ttu-id="38eb6-306">`RenderFragment<T>`Je blok značek Razor, který přebírá parametr, který lze zadat při vykreslení fragmentu vykreslování.</span><span class="sxs-lookup"><span data-stu-id="38eb6-306">A `RenderFragment<T>` is a chunk of Razor markup that takes a parameter that can be specified when the render fragment is rendered.</span></span>

### <a name="child-content"></a><span data-ttu-id="38eb6-307">Podřízený obsah</span><span class="sxs-lookup"><span data-stu-id="38eb6-307">Child content</span></span>

<span data-ttu-id="38eb6-308">Komponenty Blazor můžou zachytit svůj podřízený obsah `RenderFragment` a vykreslovat ho jako součást vykreslování komponent.</span><span class="sxs-lookup"><span data-stu-id="38eb6-308">Blazor components can capture their child content as a `RenderFragment` and render that content as part of the component rendering.</span></span> <span data-ttu-id="38eb6-309">Chcete-li zachytit podřízený obsah, definujte parametr součásti typu `RenderFragment` a pojmenujte jej `ChildContent` .</span><span class="sxs-lookup"><span data-stu-id="38eb6-309">To capture child content, define a component parameter of type `RenderFragment` and name it `ChildContent`.</span></span>

<span data-ttu-id="38eb6-310">*ChildContentComponent. Razor*</span><span class="sxs-lookup"><span data-stu-id="38eb6-310">*ChildContentComponent.razor*</span></span>

```razor
<h1>Component with child content</h1>

<div>@ChildContent</div>

@code {
    [Parameter]
    public RenderFragment ChildContent { get; set; }
}
```

<span data-ttu-id="38eb6-311">Nadřazená komponenta pak může poskytovat podřízený obsah pomocí normální syntaxe Razor.</span><span class="sxs-lookup"><span data-stu-id="38eb6-311">A parent component can then supply child content using normal Razor syntax.</span></span>

```razor
<ChildContentComponent>
    <p>The time is @DateTime.Now</p>
</ChildContentComponent>
```

### <a name="template-parameters"></a><span data-ttu-id="38eb6-312">Parametry šablony</span><span class="sxs-lookup"><span data-stu-id="38eb6-312">Template parameters</span></span>

<span data-ttu-id="38eb6-313">Komponenta Blazor šablon může také definovat více parametrů součásti typu `RenderFragment` nebo `RenderFragment<T>` .</span><span class="sxs-lookup"><span data-stu-id="38eb6-313">A templated Blazor component can also define multiple component parameters of type `RenderFragment` or `RenderFragment<T>`.</span></span> <span data-ttu-id="38eb6-314">Parametr pro `RenderFragment<T>` lze zadat při jeho vyvolání.</span><span class="sxs-lookup"><span data-stu-id="38eb6-314">The parameter for a `RenderFragment<T>` can be specified when it's invoked.</span></span> <span data-ttu-id="38eb6-315">Chcete-li zadat parametr obecného typu pro komponentu, použijte `@typeparam` direktivu Razor.</span><span class="sxs-lookup"><span data-stu-id="38eb6-315">To specify a generic type parameter for a component, use the `@typeparam` Razor directive.</span></span>

<span data-ttu-id="38eb6-316">*SimpleListView. Razor*</span><span class="sxs-lookup"><span data-stu-id="38eb6-316">*SimpleListView.razor*</span></span>

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

<span data-ttu-id="38eb6-317">Při použití komponenty se šablonou lze parametry šablony zadat pomocí podřízených prvků, které odpovídají názvům parametrů.</span><span class="sxs-lookup"><span data-stu-id="38eb6-317">When using a templated component, the template parameters can be specified using child elements that match the names of the parameters.</span></span> <span data-ttu-id="38eb6-318">Argumenty součásti typu `RenderFragment<T>` předané jako elementy mají implicitní parametr s názvem `context` .</span><span class="sxs-lookup"><span data-stu-id="38eb6-318">Component arguments of type `RenderFragment<T>` passed as elements have an implicit parameter named `context`.</span></span> <span data-ttu-id="38eb6-319">Můžete změnit název tohoto parametru implementace pomocí `Context` atributu u podřízeného elementu.</span><span class="sxs-lookup"><span data-stu-id="38eb6-319">You can change the name of this implement parameter using the `Context` attribute on the child element.</span></span> <span data-ttu-id="38eb6-320">Parametry obecného typu lze zadat pomocí atributu, který odpovídá názvu parametru typu.</span><span class="sxs-lookup"><span data-stu-id="38eb6-320">Any generic type parameters can be specified using an attribute that matches the name of the type parameter.</span></span> <span data-ttu-id="38eb6-321">Parametr typu bude odvozený, pokud je to možné:</span><span class="sxs-lookup"><span data-stu-id="38eb6-321">The type parameter will be inferred if possible:</span></span>

```razor
<SimpleListView Items="messages" TItem="string">
    <Heading>
        <h1>My list</h1>
    </Heading>
    <ItemTemplate Context="message">
        <p>The message is: @message</p>
    </ItemTemplate>
</SimpleListView>
```

<span data-ttu-id="38eb6-322">Výstup této součásti vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="38eb6-322">The output of this component looks like this:</span></span>

```html
<h1>My list</h1>
<ul>
    <li>The message is: message1</li>
    <li>The message is: message2</li>
<ul>
```

## <a name="code-behind"></a><span data-ttu-id="38eb6-323">Kód na pozadí</span><span class="sxs-lookup"><span data-stu-id="38eb6-323">Code-behind</span></span>

<span data-ttu-id="38eb6-324">Komponenta Blazor je obvykle vytvořená v jednom souboru *. Razor* .</span><span class="sxs-lookup"><span data-stu-id="38eb6-324">A Blazor component is typically authored in a single *.razor* file.</span></span> <span data-ttu-id="38eb6-325">Je však také možné oddělit kód a značky pomocí souboru kódu na pozadí.</span><span class="sxs-lookup"><span data-stu-id="38eb6-325">However, it's also possible to separate the code and markup using a code-behind file.</span></span> <span data-ttu-id="38eb6-326">Chcete-li použít soubor komponenty, přidejte soubor C#, který se shoduje s názvem souboru komponenty, ale s přidaným rozšířením *. cs* (*Counter.Razor.cs*).</span><span class="sxs-lookup"><span data-stu-id="38eb6-326">To use a component file, add a C# file that matches the file name of the component file but with a *.cs* extension added (*Counter.razor.cs*).</span></span> <span data-ttu-id="38eb6-327">Použijte soubor C# k definování základní třídy pro komponentu.</span><span class="sxs-lookup"><span data-stu-id="38eb6-327">Use the C# file to define a base class for the component.</span></span> <span data-ttu-id="38eb6-328">Základní třídu můžete pojmenovat cokoli, co byste chtěli, ale je běžné pojmenovat třídu stejně jako třídu komponenty, ale s `Base` rozšířením ( `CounterBase` ).</span><span class="sxs-lookup"><span data-stu-id="38eb6-328">You can name the base class anything you'd like, but it's common to name the class the same as the component class, but with a `Base` extension added (`CounterBase`).</span></span> <span data-ttu-id="38eb6-329">Třída založená na komponentě musí také odvozovat z `ComponentBase` .</span><span class="sxs-lookup"><span data-stu-id="38eb6-329">The component-based class must also derive from `ComponentBase`.</span></span> <span data-ttu-id="38eb6-330">Poté v souboru komponenty Razor přidejte `@inherits` direktivu pro určení základní třídy pro komponentu ( `@inherits CounterBase` ).</span><span class="sxs-lookup"><span data-stu-id="38eb6-330">Then, in the Razor component file, add the `@inherits` directive to specify the base class for the component (`@inherits CounterBase`).</span></span>

<span data-ttu-id="38eb6-331">*Čítač. Razor*</span><span class="sxs-lookup"><span data-stu-id="38eb6-331">*Counter.razor*</span></span>

```razor
@inherits CounterBase

<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button @onclick="IncrementCount">Click me</button>
```

<span data-ttu-id="38eb6-332">*Counter.razor.cs*</span><span class="sxs-lookup"><span data-stu-id="38eb6-332">*Counter.razor.cs*</span></span>

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

<span data-ttu-id="38eb6-333">Viditelnost členů komponenty v základní třídě musí být `protected` nebo `public` viditelná pro třídu součásti.</span><span class="sxs-lookup"><span data-stu-id="38eb6-333">The visibility of the component's members in the base class must be `protected` or `public` to be visible to the component class.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="38eb6-334">Další materiály a zdroje informací</span><span class="sxs-lookup"><span data-stu-id="38eb6-334">Additional resources</span></span>

<span data-ttu-id="38eb6-335">Předchozí není vyčerpávajícím způsobem všech aspektů Blazor komponent.</span><span class="sxs-lookup"><span data-stu-id="38eb6-335">The preceding isn't an exhaustive treatment of all aspects of Blazor components.</span></span> <span data-ttu-id="38eb6-336">Další informace o tom, jak [vytvořit a používat ASP.NET Core komponenty Razor](/aspnet/core/blazor/components), najdete v dokumentaci k Blazor.</span><span class="sxs-lookup"><span data-stu-id="38eb6-336">For more information on how to [Create and use ASP.NET Core Razor components](/aspnet/core/blazor/components), see the Blazor documentation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="38eb6-337">[Předchozí](app-startup.md) 
> [Další](pages-routing-layouts.md)</span><span class="sxs-lookup"><span data-stu-id="38eb6-337">[Previous](app-startup.md)
[Next](pages-routing-layouts.md)</span></span>
