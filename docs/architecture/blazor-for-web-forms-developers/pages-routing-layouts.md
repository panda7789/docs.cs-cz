---
title: Stránky, směrování a rozložení
description: Naučte se vytvářet stránky v Blazor, pracovat s směrováním na straně klienta a spravovat rozložení stránek.
author: danroth27
ms.author: daroth
ms.date: 09/19/2019
ms.openlocfilehash: 693eee270a46ccb56ed5fef8fced1d4a1cf1974f
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72520230"
---
# <a name="pages-routing-and-layouts"></a>Stránky, směrování a rozložení

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Aplikace webových formulářů ASP.NET se skládají ze stránek definovaných v souborech *. aspx* . Adresa každé stránky je založena na své fyzické cestě k souboru v projektu. Když prohlížeč odešle požadavek na stránku, obsah stránky se dynamicky vykresluje na serveru. Účty vykreslování pro značky HTML stránky a její serverové ovládací prvky.

V Blazor každá stránka aplikace je komponentou, která je obvykle definovaná v souboru *. Razor* s jednou nebo více zadanými trasami. Směrování většinou probíhá na straně klienta bez nutnosti zahrnutí konkrétního požadavku serveru. Prohlížeč nejprve vytvoří požadavek na kořenovou adresu aplikace. Kořenová komponenta `Router` v aplikaci Blazor zpracovává zachycené požadavky navigace a jejich správné součásti.

Blazor také podporuje *přímý odkazování*. K přímému propojení dojde, když prohlížeč odešle požadavek na konkrétní trasu jinou než na kořen aplikace. Požadavky na přímé odkazy odeslané na server jsou směrovány do aplikace Blazor, která pak směruje požadavek na správnou součást klienta.

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

Ekvivalentní stránka v aplikaci Blazor by vypadala takto:

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

Chcete-li vytvořit stránku v Blazor, vytvořte komponentu a přidejte direktivu `@page` Razor k určení trasy pro komponentu. Direktiva `@page` přijímá jeden parametr, který je šablonou směrování, která se má přidat do této součásti.

```razor
@page "/counter"
```

Parametr šablony trasy je povinný. Na rozdíl od webových formulářů ASP.NET *není* trasa k součásti Blazor odvozena z umístění souboru (i když to může být funkce přidaná v budoucnu).

Syntaxe šablony směrování je stejná základní syntaxe, která se používá pro směrování ve webových formulářích ASP.NET. Parametry směrování jsou zadány v šabloně pomocí složených závorek. Blazor vytvoří vazby hodnot trasy k parametrům komponenty se stejným názvem (bez rozlišení velkých a malých písmen).

```razor
@page "/product/{id}"

<h1>Product @Id</h1>

@code {
    [Parameter]
    public string Id { get; set; }
}
```

Můžete také zadat omezení hodnoty parametru Route. Pokud například chcete omezit ID produktu na `int`:

```razor
@page "/product/{id:int}"

<h1>Product @Id</h1>

@code {
    [Parameter]
    public int Id { get; set; }
}
```

Úplný seznam omezení trasy, které podporuje Blazor, najdete v tématu věnovaném [omezením tras](/aspnet/core/blazor/routing#route-constraints).

## <a name="router-component"></a>Součást směrovače

Směrování v Blazor se zpracovává komponentou `Router`. Komponenta `Router` se obvykle používá v kořenové komponentě aplikace (*App. Razor*).

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

Komponenta `Router` zjišťuje směrovatelné komponenty v zadaném `AppAssembly` a volitelně zadaném `AdditionalAssemblies`. Když prohlížeč přejde, `Router` zachytí navigaci a vykreslí obsah svého `Found` parametru s extrahovanou `RouteData`, pokud trasa odpovídá adrese, jinak `Router` vykreslí svůj parametr `NotFound`.

Komponenta `RouteView` zpracovává vykreslování odpovídající komponenty určené `RouteData` s jeho rozložením, pokud má jednu z nich. Pokud odpovídající součást nemá rozložení, použije se volitelně zadaný `DefaultLayout`.

Komponenta `LayoutView` vykreslí svůj podřízený obsah v rámci zadaného rozložení. Podrobněji se podíváme na rozložení podrobněji v této kapitole.

## <a name="navigation"></a>Navigace

Ve webových formulářích ASP.NET můžete aktivovat navigaci na jinou stránku tak, že v prohlížeči vrátíte odezvu přesměrování. Příklad:

```csharp
protected void NavigateButton_Click(object sender, EventArgs e)
{
    Response.Redirect("Counter");
}
```

Vrácení odpovědi přesměrování není obvykle možné v Blazor. Blazor nepoužívá model požadavek-odpověď. Pomocí JavaScriptu můžete ale aktivovat navigace v prohlížeči přímo.

Blazor poskytuje službu `NavigationManager`, kterou lze použít k těmto akcím:

- Získat aktuální adresu prohlížeče
- Získat základní adresu
- Aktivovat navigační panel
- Dostávat oznámení, když se změní adresa

Chcete-li přejít na jinou adresu, použijte metodu `NavigateTo`:

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

Popis všech členů `NavigationManager` naleznete v tématu věnovaném [identifikátorům URI a pomocníkům pro stav navigace](/aspnet/core/blazor/routing#uri-and-navigation-state-helpers).

## <a name="base-urls"></a>Základní adresy URL

Pokud je vaše aplikace Blazor nasazená v základní cestě, musíte v metadatech stránky zadat základní adresu URL s použitím značky `<base>` pro směrování do pracovní vlastnosti. Pokud je stránka hostitele aplikace vykreslena serverem pomocí Razor, můžete pomocí syntaxe `~/` zadat základní adresu aplikace. Pokud je stránka hostitele statická HTML, je nutné explicitně zadat základní adresu URL.

```html
<base href="~/" />
```

## <a name="page-layout"></a>Rozložení stránky

Rozložení stránky ve webových formulářích ASP.NET je zpracováváno pomocí stránek předlohy. Stránky předlohy definují šablonu s jedním nebo více zástupnými symboly obsahu, které lze poté zadat na jednotlivé stránky. Stránky předlohy jsou definovány v souborech *. Master* a začínají direktivou `<%@ Master %>`. Obsah souborů *. Master* je kódován jako stránka *. aspx* , ale s přidáním ovládacích prvků `<asp:ContentPlaceHolder>` k označení místa, kde mohou stránky dodávají obsah.

*Lokalita. Master*

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

V Blazor můžete zpracovávat rozložení stránky pomocí komponent rozložení. Komponenty rozložení dědí z `LayoutComponentBase`, což definuje jednu vlastnost `Body` typu `RenderFragment`, kterou lze použít k vykreslení obsahu stránky.

*MainLayout. Razor*

```razor
@inherits LayoutComponentBase
<h1>Main layout</h1>
<div>
    @Body
</div>
```

Při vykreslení stránky s rozložením se stránka vykreslí v rámci obsahu zadaného rozložení v umístění, kde rozložení vykresluje jeho vlastnost `Body`.

Chcete-li použít rozložení na stránku, použijte direktivu `@layout`:

```razor
@layout MainLayout
```

Můžete určit rozložení pro všechny součásti ve složce a podsložkách pomocí souboru *_Imports. Razor* . Můžete také zadat výchozí rozložení pro všechny stránky pomocí [součásti směrovače](#router-component).

Stránky předlohy mohou definovat více zástupných symbolů obsahu, ale rozložení v Blazor mají pouze jednu vlastnost `Body`. Toto omezení součástí rozložení Blazor bude snad být řešeno v budoucí verzi.

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

Rozložení v Blazor obvykle nedefinují kořenové prvky HTML stránky (`<html>`, `<body>`, `<head>` atd.). Kořenové prvky HTML jsou místo toho definovány na stránce hostitele aplikace v Blazor, která se používá k vykreslení počátečního obsahu HTML pro aplikaci (viz [bootstrap Blazor](project-structure.md#bootstrap-blazor)). Stránka hostitel může vykreslit několik kořenových součástí pro aplikaci s okolním kódem.

Komponenty v Blazor, včetně stránek, nemůžou vykreslovat značky `<script>`. Toto omezení vykreslování existuje, protože značky `<script>` se načítají jednou a pak se nedají změnit. Pokud se pokusíte vykreslit značky dynamicky pomocí syntaxe Razor, může dojít k neočekávanému chování. Místo toho by se měly na stránku hostitele aplikace přidat všechny značky `<script>`.

>[!div class="step-by-step"]
>[Předchozí](components.md)
>[Další](state-management.md)
