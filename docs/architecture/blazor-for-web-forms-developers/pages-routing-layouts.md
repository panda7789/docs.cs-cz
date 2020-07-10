---
title: Stránky, směrování a rozložení
description: Naučte se vytvářet stránky v Blazor , pracovat s směrováním na straně klienta a spravovat rozložení stránek.
author: danroth27
ms.author: daroth
no-loc:
- Blazor
ms.date: 09/19/2019
ms.openlocfilehash: fc1f6f9420c7149b6e67123f2f68bef75667aa0c
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173104"
---
# <a name="pages-routing-and-layouts"></a><span data-ttu-id="eaf32-103">Stránky, směrování a rozložení</span><span class="sxs-lookup"><span data-stu-id="eaf32-103">Pages, routing, and layouts</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="eaf32-104">Aplikace webových formulářů ASP.NET se skládají ze stránek definovaných v souborech *. aspx* .</span><span class="sxs-lookup"><span data-stu-id="eaf32-104">ASP.NET Web Forms apps are composed of pages defined in *.aspx* files.</span></span> <span data-ttu-id="eaf32-105">Adresa každé stránky je založena na své fyzické cestě k souboru v projektu.</span><span class="sxs-lookup"><span data-stu-id="eaf32-105">Each page's address is based on its physical file path in the project.</span></span> <span data-ttu-id="eaf32-106">Když prohlížeč odešle požadavek na stránku, obsah stránky se dynamicky vykresluje na serveru.</span><span class="sxs-lookup"><span data-stu-id="eaf32-106">When a browser makes a request to the page, the contents of the page are dynamically rendered on the server.</span></span> <span data-ttu-id="eaf32-107">Účty vykreslování pro značky HTML stránky a její serverové ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="eaf32-107">The rendering accounts for both the page's HTML markup and its server controls.</span></span>

<span data-ttu-id="eaf32-108">BlazorKaždá stránka v aplikaci je součástí, která je obvykle definovaná v souboru *. Razor* s jednou nebo více zadanými trasami.</span><span class="sxs-lookup"><span data-stu-id="eaf32-108">In Blazor, each page in the app is a component, typically defined in a *.razor* file, with one or more specified routes.</span></span> <span data-ttu-id="eaf32-109">Směrování většinou probíhá na straně klienta bez nutnosti zahrnutí konkrétního požadavku serveru.</span><span class="sxs-lookup"><span data-stu-id="eaf32-109">Routing mostly happens client-side without involving a specific server request.</span></span> <span data-ttu-id="eaf32-110">Prohlížeč nejprve vytvoří požadavek na kořenovou adresu aplikace.</span><span class="sxs-lookup"><span data-stu-id="eaf32-110">The browser first makes a request to the root address of the app.</span></span> <span data-ttu-id="eaf32-111">Kořenová `Router` komponenta v Blazor aplikaci pak zpracovává zachycení požadavků na navigaci a jejich správné součásti.</span><span class="sxs-lookup"><span data-stu-id="eaf32-111">A root `Router` component in the Blazor app then handles intercepting navigation requests and them to the correct component.</span></span>

Blazor<span data-ttu-id="eaf32-112">podporuje také *přímý odkazování*.</span><span class="sxs-lookup"><span data-stu-id="eaf32-112"> also supports *deep linking*.</span></span> <span data-ttu-id="eaf32-113">K přímému propojení dojde, když prohlížeč odešle požadavek na konkrétní trasu jinou než na kořen aplikace.</span><span class="sxs-lookup"><span data-stu-id="eaf32-113">Deep linking occurs when the browser makes a request to a specific route other than the root of the app.</span></span> <span data-ttu-id="eaf32-114">Požadavky na přímé odkazy odeslané na server jsou směrovány do Blazor aplikace, která pak směruje požadavek na správnou součást klienta.</span><span class="sxs-lookup"><span data-stu-id="eaf32-114">Requests for deep links sent to the server are routed to the Blazor app, which then routes the request client-side to the correct component.</span></span>

<span data-ttu-id="eaf32-115">Jednoduchá stránka ve webových formulářích ASP.NET může obsahovat následující kód:</span><span class="sxs-lookup"><span data-stu-id="eaf32-115">A simple page in ASP.NET Web Forms might contain the following markup:</span></span>

<span data-ttu-id="eaf32-116">*Název. aspx*</span><span class="sxs-lookup"><span data-stu-id="eaf32-116">*Name.aspx*</span></span>

```aspx-csharp
<%@ Page Title="Name" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true" CodeBehind="Name.aspx.cs" Inherits="WebApplication1.Name" %>

<asp:Content ID="BodyContent" ContentPlaceHolderID="MainContent" runat="server">
    <div>
        What is your name?<br />
        <asp:TextBox ID="TextBox1" runat="server"></asp:TextBox>
        <asp:Button ID="Button1" runat="server" Text="Submit" OnClick="Button1_Click" />
    </div>
    <div>
        <asp:Literal ID="Literal1" runat="server" />
    </div>
</asp:Content>
```

<span data-ttu-id="eaf32-117">*Name.aspx.cs*</span><span class="sxs-lookup"><span data-stu-id="eaf32-117">*Name.aspx.cs*</span></span>

```csharp
public partial class Name : System.Web.UI.Page
{
    protected void Button1_Click1(object sender, EventArgs e)
    {
        Literal1.Text = "Hello " + TextBox1.Text;
    }
}
```

<span data-ttu-id="eaf32-118">Ekvivalentní stránka v Blazor aplikaci by vypadala takto:</span><span class="sxs-lookup"><span data-stu-id="eaf32-118">The equivalent page in a Blazor app would look like this:</span></span>

<span data-ttu-id="eaf32-119">*Název. Razor*</span><span class="sxs-lookup"><span data-stu-id="eaf32-119">*Name.razor*</span></span>

```razor
@page "/Name"
@layout MainLayout

<div>
    What is your name?<br />
    <input @bind="text" />
    <button @onclick="OnClick">Submit</button>
</div>
<div>
    @if (name != null)
    {
        @:Hello @name
    }
</div>

@code {
    string text;
    string name;

    void OnClick() {
        name = text;
    }
}
```

## <a name="create-pages"></a><span data-ttu-id="eaf32-120">Vytvořit stránky</span><span class="sxs-lookup"><span data-stu-id="eaf32-120">Create pages</span></span>

<span data-ttu-id="eaf32-121">Chcete-li vytvořit stránku v Blazor , vytvořte komponentu a přidejte `@page` direktivu Razor pro určení trasy pro komponentu.</span><span class="sxs-lookup"><span data-stu-id="eaf32-121">To create a page in Blazor, create a component and add the `@page` Razor directive to specify the route for the component.</span></span> <span data-ttu-id="eaf32-122">`@page`Direktiva přijímá jeden parametr, který je šablonou směrování, která se má přidat do této součásti.</span><span class="sxs-lookup"><span data-stu-id="eaf32-122">The `@page` directive takes a single parameter, which is the route template to add to that component.</span></span>

```razor
@page "/counter"
```

<span data-ttu-id="eaf32-123">Parametr šablony trasy je povinný.</span><span class="sxs-lookup"><span data-stu-id="eaf32-123">The route template parameter is required.</span></span> <span data-ttu-id="eaf32-124">Na rozdíl od webových formulářů ASP.NET Blazor *není* trasa k součásti odvozená od umístění souboru (i když to může být funkce přidaná v budoucnu).</span><span class="sxs-lookup"><span data-stu-id="eaf32-124">Unlike ASP.NET Web Forms, the route to a Blazor component *isn't* inferred from its file location (although that may be a feature added in the future).</span></span>

<span data-ttu-id="eaf32-125">Syntaxe šablony směrování je stejná základní syntaxe, která se používá pro směrování ve webových formulářích ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="eaf32-125">The route template syntax is the same basic syntax used for routing in ASP.NET Web Forms.</span></span> <span data-ttu-id="eaf32-126">Parametry směrování jsou zadány v šabloně pomocí složených závorek.</span><span class="sxs-lookup"><span data-stu-id="eaf32-126">Route parameters are specified in the template using braces.</span></span> Blazor<span data-ttu-id="eaf32-127">vytvoří vazby hodnot směrování k parametrům komponenty se stejným názvem (bez rozlišení velkých a malých písmen).</span><span class="sxs-lookup"><span data-stu-id="eaf32-127"> will bind route values to component parameters with the same name (case-insensitive).</span></span>

```razor
@page "/product/{id}"

<h1>Product @Id</h1>

@code {
    [Parameter]
    public string Id { get; set; }
}
```

<span data-ttu-id="eaf32-128">Můžete také zadat omezení hodnoty parametru Route.</span><span class="sxs-lookup"><span data-stu-id="eaf32-128">You can also specify constraints on the value of the route parameter.</span></span> <span data-ttu-id="eaf32-129">Chcete-li například omezit ID produktu na `int` :</span><span class="sxs-lookup"><span data-stu-id="eaf32-129">For example, to constrain the product ID to be an `int`:</span></span>

```razor
@page "/product/{id:int}"

<h1>Product @Id</h1>

@code {
    [Parameter]
    public int Id { get; set; }
}
```

<span data-ttu-id="eaf32-130">Úplný seznam omezení trasy, které podporuje Blazor , najdete v tématu věnovaném [omezením trasy](/aspnet/core/blazor/routing#route-constraints).</span><span class="sxs-lookup"><span data-stu-id="eaf32-130">For a full list of the route constraints supported by Blazor, see [Route constraints](/aspnet/core/blazor/routing#route-constraints).</span></span>

## <a name="router-component"></a><span data-ttu-id="eaf32-131">Součást směrovače</span><span class="sxs-lookup"><span data-stu-id="eaf32-131">Router component</span></span>

<span data-ttu-id="eaf32-132">Směrování v nástroji Blazor je zpracováván `Router` komponentou.</span><span class="sxs-lookup"><span data-stu-id="eaf32-132">Routing in Blazor is handled by the `Router` component.</span></span> <span data-ttu-id="eaf32-133">`Router`Komponenta se obvykle používá v kořenové komponentě aplikace (*App. Razor*).</span><span class="sxs-lookup"><span data-stu-id="eaf32-133">The `Router` component is typically used in the app's root component (*App.razor*).</span></span>

```razor
<Router AppAssembly="@typeof(Program).Assembly">
    <Found Context="routeData">
        <RouteView RouteData="@routeData" DefaultLayout="@typeof(MainLayout)" />
    </Found>
    <NotFound>
        <LayoutView Layout="@typeof(MainLayout)">
            <p>Sorry, there's nothing at this address.</p>
        </LayoutView>
    </NotFound>
</Router>
```

<span data-ttu-id="eaf32-134">`Router`Komponenta vyhledá směrovatelný komponenty v určeném `AppAssembly` a volitelně zadaném `AdditionalAssemblies` .</span><span class="sxs-lookup"><span data-stu-id="eaf32-134">The `Router` component discovers the routable components in the specified `AppAssembly` and in the optionally specified `AdditionalAssemblies`.</span></span> <span data-ttu-id="eaf32-135">Když prohlížeč přejde, `Router` zachytí navigaci a vykreslí obsah svého `Found` parametru s extrakcí, `RouteData` Pokud trasa odpovídá adrese, jinak `Router` vykreslí svůj `NotFound` parametr.</span><span class="sxs-lookup"><span data-stu-id="eaf32-135">When the browser navigates, the `Router` intercepts the navigation and renders the contents of its `Found` parameter with the extracted `RouteData` if a route matches the address, otherwise the `Router` renders its `NotFound` parameter.</span></span>

<span data-ttu-id="eaf32-136">`RouteView`Komponenta zpracovává vykreslování odpovídající komponenty určené pomocí `RouteData` jejího rozložení, pokud má jednu z nich.</span><span class="sxs-lookup"><span data-stu-id="eaf32-136">The `RouteView` component handles rendering the matched component specified by the `RouteData` with its layout if it has one.</span></span> <span data-ttu-id="eaf32-137">Pokud odpovídající součást nemá rozložení, `DefaultLayout` je použita volitelně zadaná.</span><span class="sxs-lookup"><span data-stu-id="eaf32-137">If the matched component doesn't have a layout, then the optionally specified `DefaultLayout` is used.</span></span>

<span data-ttu-id="eaf32-138">`LayoutView`Komponenta vykreslí svůj podřízený obsah v rámci zadaného rozložení.</span><span class="sxs-lookup"><span data-stu-id="eaf32-138">The `LayoutView` component renders its child content within the specified layout.</span></span> <span data-ttu-id="eaf32-139">Podrobněji se podíváme na rozložení podrobněji v této kapitole.</span><span class="sxs-lookup"><span data-stu-id="eaf32-139">We'll look at layouts more in detail later in this chapter.</span></span>

## <a name="navigation"></a><span data-ttu-id="eaf32-140">Navigace</span><span class="sxs-lookup"><span data-stu-id="eaf32-140">Navigation</span></span>

<span data-ttu-id="eaf32-141">Ve webových formulářích ASP.NET můžete aktivovat navigaci na jinou stránku tak, že v prohlížeči vrátíte odezvu přesměrování.</span><span class="sxs-lookup"><span data-stu-id="eaf32-141">In ASP.NET Web Forms, you trigger navigation to a different page by returning a redirect response to the browser.</span></span> <span data-ttu-id="eaf32-142">Zde je příklad:</span><span class="sxs-lookup"><span data-stu-id="eaf32-142">For example:</span></span>

```csharp
protected void NavigateButton_Click(object sender, EventArgs e)
{
    Response.Redirect("Counter");
}
```

<span data-ttu-id="eaf32-143">Vrácení odpovědi přesměrování není obvykle možné v Blazor .</span><span class="sxs-lookup"><span data-stu-id="eaf32-143">Returning a redirect response isn't typically possible in Blazor.</span></span> Blazor<span data-ttu-id="eaf32-144">nepoužívá model požadavek-odpověď.</span><span class="sxs-lookup"><span data-stu-id="eaf32-144"> doesn't use a request-reply model.</span></span> <span data-ttu-id="eaf32-145">Pomocí JavaScriptu můžete ale aktivovat navigace v prohlížeči přímo.</span><span class="sxs-lookup"><span data-stu-id="eaf32-145">You can, however, trigger browser navigations directly, as you can with JavaScript.</span></span>

Blazor<span data-ttu-id="eaf32-146">poskytuje `NavigationManager` službu, která se dá použít k těmto akcím:</span><span class="sxs-lookup"><span data-stu-id="eaf32-146"> provides a `NavigationManager` service that can be used to:</span></span>

- <span data-ttu-id="eaf32-147">Získat aktuální adresu prohlížeče</span><span class="sxs-lookup"><span data-stu-id="eaf32-147">Get the current browser address</span></span>
- <span data-ttu-id="eaf32-148">Získat základní adresu</span><span class="sxs-lookup"><span data-stu-id="eaf32-148">Get the base address</span></span>
- <span data-ttu-id="eaf32-149">Aktivovat navigační panel</span><span class="sxs-lookup"><span data-stu-id="eaf32-149">Trigger navigations</span></span>
- <span data-ttu-id="eaf32-150">Dostávat oznámení, když se změní adresa</span><span class="sxs-lookup"><span data-stu-id="eaf32-150">Get notified when the address changes</span></span>

<span data-ttu-id="eaf32-151">Chcete-li přejít na jinou adresu, použijte `NavigateTo` metodu:</span><span class="sxs-lookup"><span data-stu-id="eaf32-151">To navigate to a different address, use the `NavigateTo` method:</span></span>

```razor
@page "/"
@inject NavigationManager NavigationManager

<button @onclick="Navigate">Navigate</button>

@code {
    void Navigate() {
        NavigationManager.NavigateTo("counter");
    }
}
```

<span data-ttu-id="eaf32-152">Popis všech `NavigationManager` členů naleznete v tématu věnovaném [identifikátorům URI a nápovědě pro stav navigace](/aspnet/core/blazor/routing#uri-and-navigation-state-helpers).</span><span class="sxs-lookup"><span data-stu-id="eaf32-152">For a description of all `NavigationManager` members, see [URI and navigation state helpers](/aspnet/core/blazor/routing#uri-and-navigation-state-helpers).</span></span>

## <a name="base-urls"></a><span data-ttu-id="eaf32-153">Základní adresy URL</span><span class="sxs-lookup"><span data-stu-id="eaf32-153">Base URLs</span></span>

<span data-ttu-id="eaf32-154">Pokud Blazor je vaše aplikace nasazena v základní cestě, je nutné zadat základní adresu URL v metadatech stránky pomocí `<base>` značky vlastnosti směrování na práci.</span><span class="sxs-lookup"><span data-stu-id="eaf32-154">If your Blazor app is deployed under a base path, then you need to specify the base URL in the page metadata using the `<base>` tag for routing to work property.</span></span> <span data-ttu-id="eaf32-155">Pokud je stránka hostitele aplikace vykreslena serverem pomocí syntaxe Razor, můžete použít `~/` syntaxi k určení základní adresy aplikace.</span><span class="sxs-lookup"><span data-stu-id="eaf32-155">If the host page for the app is server-rendered using Razor, then you can use the `~/` syntax to specify the app's base address.</span></span> <span data-ttu-id="eaf32-156">Pokud je stránka hostitele statická HTML, je nutné explicitně zadat základní adresu URL.</span><span class="sxs-lookup"><span data-stu-id="eaf32-156">If the host page is static HTML, then you need to specify the base URL explicitly.</span></span>

```html
<base href="~/" />
```

## <a name="page-layout"></a><span data-ttu-id="eaf32-157">Rozložení stránky</span><span class="sxs-lookup"><span data-stu-id="eaf32-157">Page layout</span></span>

<span data-ttu-id="eaf32-158">Rozložení stránky ve webových formulářích ASP.NET je zpracováváno pomocí stránek předlohy.</span><span class="sxs-lookup"><span data-stu-id="eaf32-158">Page layout in ASP.NET Web Forms is handled by Master Pages.</span></span> <span data-ttu-id="eaf32-159">Stránky předlohy definují šablonu s jedním nebo více zástupnými symboly obsahu, které lze poté zadat na jednotlivé stránky.</span><span class="sxs-lookup"><span data-stu-id="eaf32-159">Master Pages define a template with one or more content placeholders that can then be supplied by individual pages.</span></span> <span data-ttu-id="eaf32-160">Stránky předlohy jsou definovány v souborech *. Master* a začínají `<%@ Master %>` direktivou.</span><span class="sxs-lookup"><span data-stu-id="eaf32-160">Master Pages are defined in *.master* files and start with the `<%@ Master %>` directive.</span></span> <span data-ttu-id="eaf32-161">Obsah souborů *. Master* je kódován jako stránka *. aspx* , ale s přidáním `<asp:ContentPlaceHolder>` ovládacích prvků k označení místa, kde mohou stránky dodávají obsah.</span><span class="sxs-lookup"><span data-stu-id="eaf32-161">The content of the *.master* files is coded as you would an *.aspx* page, but with the addition of `<asp:ContentPlaceHolder>` controls to mark where pages can supply content.</span></span>

<span data-ttu-id="eaf32-162">*Site.master*</span><span class="sxs-lookup"><span data-stu-id="eaf32-162">*Site.master*</span></span>

```aspx-csharp
<%@ Master Language="C#" AutoEventWireup="true" CodeBehind="Site.master.cs" Inherits="WebApplication1.SiteMaster" %>

<!DOCTYPE html>
<html lang="en">
<head runat="server">
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title><%: Page.Title %> - My ASP.NET Application</title>
    <link href="~/favicon.ico" rel="shortcut icon" type="image/x-icon" />
</head>
<body>
    <form runat="server">
        <div class="container body-content">
            <asp:ContentPlaceHolder ID="MainContent" runat="server">
            </asp:ContentPlaceHolder>
            <hr />
            <footer>
                <p>&copy; <%: DateTime.Now.Year %> - My ASP.NET Application</p>
            </footer>
        </div>
    </form>
</body>
</html>
```

<span data-ttu-id="eaf32-163">V aplikaci Blazor můžete zpracovávat rozložení stránky pomocí komponent rozložení.</span><span class="sxs-lookup"><span data-stu-id="eaf32-163">In Blazor, you handle page layout using layout components.</span></span> <span data-ttu-id="eaf32-164">Komponenty rozložení dědí z `LayoutComponentBase` , který definuje jednu `Body` vlastnost typu `RenderFragment` , která se dá použít k vykreslení obsahu stránky.</span><span class="sxs-lookup"><span data-stu-id="eaf32-164">Layout components inherit from `LayoutComponentBase`, which defines a single `Body` property of type `RenderFragment`, which can be used to render the contents of the page.</span></span>

<span data-ttu-id="eaf32-165">*MainLayout. Razor*</span><span class="sxs-lookup"><span data-stu-id="eaf32-165">*MainLayout.razor*</span></span>

```razor
@inherits LayoutComponentBase
<h1>Main layout</h1>
<div>
    @Body
</div>
```

<span data-ttu-id="eaf32-166">Při vykreslení stránky s rozložením se stránka vykreslí v rámci obsahu zadaného rozložení v umístění, kde rozložení vykreslí svou `Body` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="eaf32-166">When the page with a layout is rendered, the page is rendered within the contents of the specified layout at the location where the layout renders its `Body` property.</span></span>

<span data-ttu-id="eaf32-167">Chcete-li použít rozložení na stránku, použijte `@layout` direktivu:</span><span class="sxs-lookup"><span data-stu-id="eaf32-167">To apply a layout to a page, use the `@layout` directive:</span></span>

```razor
@layout MainLayout
```

<span data-ttu-id="eaf32-168">Můžete určit rozložení pro všechny součásti ve složce a podsložkách pomocí souboru *_Imports. Razor* .</span><span class="sxs-lookup"><span data-stu-id="eaf32-168">You can specify the layout for all components in a folder and subfolders using an *_Imports.razor* file.</span></span> <span data-ttu-id="eaf32-169">Můžete také zadat výchozí rozložení pro všechny stránky pomocí [součásti směrovače](#router-component).</span><span class="sxs-lookup"><span data-stu-id="eaf32-169">You can also specify a default layout for all your pages using the [Router component](#router-component).</span></span>

<span data-ttu-id="eaf32-170">Stránky předlohy mohou definovat více zástupných symbolů obsahu, ale rozložení Blazor mají pouze jednu `Body` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="eaf32-170">Master Pages can define multiple content placeholders, but layouts in Blazor only have a single `Body` property.</span></span> <span data-ttu-id="eaf32-171">Toto omezení Blazor součástí rozložení bude snad v budoucí verzi.</span><span class="sxs-lookup"><span data-stu-id="eaf32-171">This limitation of Blazor layout components will hopefully be addressed in a future release.</span></span>

<span data-ttu-id="eaf32-172">Stránky předlohy ve webových formulářích ASP.NET můžou být vnořené.</span><span class="sxs-lookup"><span data-stu-id="eaf32-172">Master Pages in ASP.NET Web Forms can be nested.</span></span> <span data-ttu-id="eaf32-173">To znamená, že stránka předlohy může také používat hlavní stránku.</span><span class="sxs-lookup"><span data-stu-id="eaf32-173">That is, a Master Page may also use a Master Page.</span></span> <span data-ttu-id="eaf32-174">Komponenty rozložení v Blazor můžou být vnořené také.</span><span class="sxs-lookup"><span data-stu-id="eaf32-174">Layout components in Blazor may be nested too.</span></span> <span data-ttu-id="eaf32-175">Komponentu rozložení můžete použít pro komponentu rozložení.</span><span class="sxs-lookup"><span data-stu-id="eaf32-175">You can apply a layout component to a layout component.</span></span> <span data-ttu-id="eaf32-176">Obsah vnitřního rozložení se vygeneruje v rámci vnějšího rozložení.</span><span class="sxs-lookup"><span data-stu-id="eaf32-176">The contents of the inner layout will be rendered within the outer layout.</span></span>

<span data-ttu-id="eaf32-177">*ChildLayout. Razor*</span><span class="sxs-lookup"><span data-stu-id="eaf32-177">*ChildLayout.razor*</span></span>

```razor
@layout MainLayout
<h2>Child layout</h2>
<div>
    @Body
</div>
```

<span data-ttu-id="eaf32-178">*Index. Razor*</span><span class="sxs-lookup"><span data-stu-id="eaf32-178">*Index.razor*</span></span>

```razor
@page "/"
@layout ChildLayout
<p>I'm in a nested layout!</p>
```

<span data-ttu-id="eaf32-179">Vykreslený výstup pro stránku by pak byl:</span><span class="sxs-lookup"><span data-stu-id="eaf32-179">The rendered output for the page would then be:</span></span>

```html
<h1>Main layout</h1>
<div>
    <h2>Child layout</h2>
    <div>
        <p>I'm in a nested layout!</p>
    </div>
</div>
```

<span data-ttu-id="eaf32-180">Rozložení v Blazor neobvykle definují kořenové prvky HTML stránky ( `<html>` ,, `<body>` `<head>` atd.).</span><span class="sxs-lookup"><span data-stu-id="eaf32-180">Layouts in Blazor don't typically define the root HTML elements for a page (`<html>`, `<body>`, `<head>`, and so on).</span></span> <span data-ttu-id="eaf32-181">Kořenové prvky HTML jsou místo toho definovány na Blazor stránce hostitele aplikace, která se používá k vykreslení počátečního obsahu HTML pro aplikaci (viz [bootstrap Blazor ](project-structure.md#bootstrap-blazor)).</span><span class="sxs-lookup"><span data-stu-id="eaf32-181">The root HTML elements are instead defined in a Blazor app's host page, which is used to render the initial HTML content for the app (see [Bootstrap Blazor](project-structure.md#bootstrap-blazor)).</span></span> <span data-ttu-id="eaf32-182">Stránka hostitel může vykreslit několik kořenových součástí pro aplikaci s okolním kódem.</span><span class="sxs-lookup"><span data-stu-id="eaf32-182">The host page can render multiple root components for the app with surrounding markup.</span></span>

<span data-ttu-id="eaf32-183">Komponenty v Blazor , včetně stránek, nemůžou vykreslovat `<script>` značky.</span><span class="sxs-lookup"><span data-stu-id="eaf32-183">Components in Blazor, including pages, can't render `<script>` tags.</span></span> <span data-ttu-id="eaf32-184">Toto omezení vykreslování existuje `<script>` , protože značky se načítají jednou a pak se nedají změnit.</span><span class="sxs-lookup"><span data-stu-id="eaf32-184">This rendering restriction exists because `<script>` tags get loaded once and then can't be changed.</span></span> <span data-ttu-id="eaf32-185">Pokud se pokusíte vykreslit značky dynamicky pomocí syntaxe Razor, může dojít k neočekávanému chování.</span><span class="sxs-lookup"><span data-stu-id="eaf32-185">Unexpected behavior may occur if you try to render the tags dynamically using Razor syntax.</span></span> <span data-ttu-id="eaf32-186">Místo toho `<script>` by měly být všechny značky přidány na stránku hostitele aplikace.</span><span class="sxs-lookup"><span data-stu-id="eaf32-186">Instead, all `<script>` tags should be added to the app's host page.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="eaf32-187">[Předchozí](components.md) 
> [Další](state-management.md)</span><span class="sxs-lookup"><span data-stu-id="eaf32-187">[Previous](components.md)
[Next](state-management.md)</span></span>
