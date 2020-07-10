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
# <a name="pages-routing-and-layouts"></a>Stránky, směrování a rozložení

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Aplikace webových formulářů ASP.NET se skládají ze stránek definovaných v souborech *. aspx* . Adresa každé stránky je založena na své fyzické cestě k souboru v projektu. Když prohlížeč odešle požadavek na stránku, obsah stránky se dynamicky vykresluje na serveru. Účty vykreslování pro značky HTML stránky a její serverové ovládací prvky.

BlazorKaždá stránka v aplikaci je součástí, která je obvykle definovaná v souboru *. Razor* s jednou nebo více zadanými trasami. Směrování většinou probíhá na straně klienta bez nutnosti zahrnutí konkrétního požadavku serveru. Prohlížeč nejprve vytvoří požadavek na kořenovou adresu aplikace. Kořenová `Router` komponenta v Blazor aplikaci pak zpracovává zachycení požadavků na navigaci a jejich správné součásti.

Blazorpodporuje také *přímý odkazování*. K přímému propojení dojde, když prohlížeč odešle požadavek na konkrétní trasu jinou než na kořen aplikace. Požadavky na přímé odkazy odeslané na server jsou směrovány do Blazor aplikace, která pak směruje požadavek na správnou součást klienta.

Jednoduchá stránka ve webových formulářích ASP.NET může obsahovat následující kód:

*Název. aspx*

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

*Name.aspx.cs*

```csharp
public partial class Name : System.Web.UI.Page
{
    protected void Button1_Click1(object sender, EventArgs e)
    {
        Literal1.Text = "Hello " + TextBox1.Text;
    }
}
```

Ekvivalentní stránka v Blazor aplikaci by vypadala takto:

*Název. Razor*

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

## <a name="create-pages"></a>Vytvořit stránky

Chcete-li vytvořit stránku v Blazor , vytvořte komponentu a přidejte `@page` direktivu Razor pro určení trasy pro komponentu. `@page`Direktiva přijímá jeden parametr, který je šablonou směrování, která se má přidat do této součásti.

```razor
@page "/counter"
```

Parametr šablony trasy je povinný. Na rozdíl od webových formulářů ASP.NET Blazor *není* trasa k součásti odvozená od umístění souboru (i když to může být funkce přidaná v budoucnu).

Syntaxe šablony směrování je stejná základní syntaxe, která se používá pro směrování ve webových formulářích ASP.NET. Parametry směrování jsou zadány v šabloně pomocí složených závorek. Blazorvytvoří vazby hodnot směrování k parametrům komponenty se stejným názvem (bez rozlišení velkých a malých písmen).

```razor
@page "/product/{id}"

<h1>Product @Id</h1>

@code {
    [Parameter]
    public string Id { get; set; }
}
```

Můžete také zadat omezení hodnoty parametru Route. Chcete-li například omezit ID produktu na `int` :

```razor
@page "/product/{id:int}"

<h1>Product @Id</h1>

@code {
    [Parameter]
    public int Id { get; set; }
}
```

Úplný seznam omezení trasy, které podporuje Blazor , najdete v tématu věnovaném [omezením trasy](/aspnet/core/blazor/routing#route-constraints).

## <a name="router-component"></a>Součást směrovače

Směrování v nástroji Blazor je zpracováván `Router` komponentou. `Router`Komponenta se obvykle používá v kořenové komponentě aplikace (*App. Razor*).

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

`Router`Komponenta vyhledá směrovatelný komponenty v určeném `AppAssembly` a volitelně zadaném `AdditionalAssemblies` . Když prohlížeč přejde, `Router` zachytí navigaci a vykreslí obsah svého `Found` parametru s extrakcí, `RouteData` Pokud trasa odpovídá adrese, jinak `Router` vykreslí svůj `NotFound` parametr.

`RouteView`Komponenta zpracovává vykreslování odpovídající komponenty určené pomocí `RouteData` jejího rozložení, pokud má jednu z nich. Pokud odpovídající součást nemá rozložení, `DefaultLayout` je použita volitelně zadaná.

`LayoutView`Komponenta vykreslí svůj podřízený obsah v rámci zadaného rozložení. Podrobněji se podíváme na rozložení podrobněji v této kapitole.

## <a name="navigation"></a>Navigace

Ve webových formulářích ASP.NET můžete aktivovat navigaci na jinou stránku tak, že v prohlížeči vrátíte odezvu přesměrování. Zde je příklad:

```csharp
protected void NavigateButton_Click(object sender, EventArgs e)
{
    Response.Redirect("Counter");
}
```

Vrácení odpovědi přesměrování není obvykle možné v Blazor . Blazornepoužívá model požadavek-odpověď. Pomocí JavaScriptu můžete ale aktivovat navigace v prohlížeči přímo.

Blazorposkytuje `NavigationManager` službu, která se dá použít k těmto akcím:

- Získat aktuální adresu prohlížeče
- Získat základní adresu
- Aktivovat navigační panel
- Dostávat oznámení, když se změní adresa

Chcete-li přejít na jinou adresu, použijte `NavigateTo` metodu:

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

Popis všech `NavigationManager` členů naleznete v tématu věnovaném [identifikátorům URI a nápovědě pro stav navigace](/aspnet/core/blazor/routing#uri-and-navigation-state-helpers).

## <a name="base-urls"></a>Základní adresy URL

Pokud Blazor je vaše aplikace nasazena v základní cestě, je nutné zadat základní adresu URL v metadatech stránky pomocí `<base>` značky vlastnosti směrování na práci. Pokud je stránka hostitele aplikace vykreslena serverem pomocí syntaxe Razor, můžete použít `~/` syntaxi k určení základní adresy aplikace. Pokud je stránka hostitele statická HTML, je nutné explicitně zadat základní adresu URL.

```html
<base href="~/" />
```

## <a name="page-layout"></a>Rozložení stránky

Rozložení stránky ve webových formulářích ASP.NET je zpracováváno pomocí stránek předlohy. Stránky předlohy definují šablonu s jedním nebo více zástupnými symboly obsahu, které lze poté zadat na jednotlivé stránky. Stránky předlohy jsou definovány v souborech *. Master* a začínají `<%@ Master %>` direktivou. Obsah souborů *. Master* je kódován jako stránka *. aspx* , ale s přidáním `<asp:ContentPlaceHolder>` ovládacích prvků k označení místa, kde mohou stránky dodávají obsah.

*Site.master*

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

V aplikaci Blazor můžete zpracovávat rozložení stránky pomocí komponent rozložení. Komponenty rozložení dědí z `LayoutComponentBase` , který definuje jednu `Body` vlastnost typu `RenderFragment` , která se dá použít k vykreslení obsahu stránky.

*MainLayout. Razor*

```razor
@inherits LayoutComponentBase
<h1>Main layout</h1>
<div>
    @Body
</div>
```

Při vykreslení stránky s rozložením se stránka vykreslí v rámci obsahu zadaného rozložení v umístění, kde rozložení vykreslí svou `Body` vlastnost.

Chcete-li použít rozložení na stránku, použijte `@layout` direktivu:

```razor
@layout MainLayout
```

Můžete určit rozložení pro všechny součásti ve složce a podsložkách pomocí souboru *_Imports. Razor* . Můžete také zadat výchozí rozložení pro všechny stránky pomocí [součásti směrovače](#router-component).

Stránky předlohy mohou definovat více zástupných symbolů obsahu, ale rozložení Blazor mají pouze jednu `Body` vlastnost. Toto omezení Blazor součástí rozložení bude snad v budoucí verzi.

Stránky předlohy ve webových formulářích ASP.NET můžou být vnořené. To znamená, že stránka předlohy může také používat hlavní stránku. Komponenty rozložení v Blazor můžou být vnořené také. Komponentu rozložení můžete použít pro komponentu rozložení. Obsah vnitřního rozložení se vygeneruje v rámci vnějšího rozložení.

*ChildLayout. Razor*

```razor
@layout MainLayout
<h2>Child layout</h2>
<div>
    @Body
</div>
```

*Index. Razor*

```razor
@page "/"
@layout ChildLayout
<p>I'm in a nested layout!</p>
```

Vykreslený výstup pro stránku by pak byl:

```html
<h1>Main layout</h1>
<div>
    <h2>Child layout</h2>
    <div>
        <p>I'm in a nested layout!</p>
    </div>
</div>
```

Rozložení v Blazor neobvykle definují kořenové prvky HTML stránky ( `<html>` ,, `<body>` `<head>` atd.). Kořenové prvky HTML jsou místo toho definovány na Blazor stránce hostitele aplikace, která se používá k vykreslení počátečního obsahu HTML pro aplikaci (viz [bootstrap Blazor ](project-structure.md#bootstrap-blazor)). Stránka hostitel může vykreslit několik kořenových součástí pro aplikaci s okolním kódem.

Komponenty v Blazor , včetně stránek, nemůžou vykreslovat `<script>` značky. Toto omezení vykreslování existuje `<script>` , protože značky se načítají jednou a pak se nedají změnit. Pokud se pokusíte vykreslit značky dynamicky pomocí syntaxe Razor, může dojít k neočekávanému chování. Místo toho `<script>` by měly být všechny značky přidány na stránku hostitele aplikace.

>[!div class="step-by-step"]
>[Předchozí](components.md) 
> [Další](state-management.md)
