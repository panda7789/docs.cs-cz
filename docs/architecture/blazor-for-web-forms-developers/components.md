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
# <a name="build-reusable-ui-components-with-blazor"></a>Vytvářejte opakovaně použitelné komponenty ui s Blazorem

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Jednou z krásných věcí, o ASP.NET webových formulářů je, jak umožňuje zapouzdření opakovaně kusů kódu uživatelského rozhraní (UI) do opakovaně použitelných ovládacích prvků uživatelského rozhraní. Vlastní uživatelské ovládací prvky lze definovat ve značkách pomocí souborů *ASCX.* Můžete také vytvořit komplikované serverové ovládací prvky v kódu s plnou podporou návrháře.

Blazor také podporuje zapouzdření ui prostřednictvím *komponent*. Součást:

- Je samostatný kus ui.
- Udržuje svůj vlastní stav a logiku vykreslování.
- Můžete definovat obslužné rutiny událostí ui, vázat se na vstupní data a spravovat svůj vlastní životní cyklus.
- Je obvykle definován a *.razor* soubor pomocí Razor syntaxe.

## <a name="an-introduction-to-razor"></a>Úvod do Razor

Razor je lehký značkovací jazyk založený na HTML a C#. S Razor můžete bez problémů přechod mezi značky a C# kód definovat logiku vykreslování komponent. Při kompilaci souboru *.razor* je logika vykreslování ve třídě .NET zachycena strukturovaným způsobem. Název zkompilované třídy je převzat z názvu souboru *.razor.* Obor názvů je převzat z výchozího oboru názvů pro projekt a cestu ke složce, nebo můžete explicitně určit obor názvů pomocí `@namespace` směrnice (více o direktivách Razor níže).

Logika vykreslování komponenty je vytvářena pomocí běžných značek HTML s dynamickou logikou přidanou pomocí jazyka C#. Znak `@` se používá k přechodu na C#. Břitva je obvykle chytrý o zjišťuje, kdy jste přešel zpět na HTML. Například následující komponenta vykreslí `<p>` značku s aktuálním časem:

```razor
<p>@DateTime.Now</p>
```

Chcete-li explicitně určit začátek a konec výrazu Jazyka C#, použijte závorky:

```razor
<p>@(DateTime.Now)</p>
```

Razor také usnadňuje použití c# tok řízení v logice vykreslování. Můžete například podmíněně vykreslit některé kódy HTML takto:

```razor
@if (value % 2 == 0)
{
    <p>The value was even.</p>
}
```

Nebo můžete vygenerovat seznam položek pomocí `foreach` normální smyčky Jazyka C#, jako je tato:

```razor
<ul>
@foreach (var item in items)
{
    <li>@item.Text</li>
}
</ul>
```

Razor direktivy, jako jsou direktivy v ASP.NET webových formulářů, řídí mnoho aspektů, jak je kompilován komponenty Razor. Příklady zahrnují komponenty:

- Obor názvů
- Základní třída
- Implementovaná rozhraní
- Obecné parametry
- Importované obory názvů
- Trasy

Razor direktivy začínají znakem `@` a obvykle se používají na začátku nového řádku na začátku souboru. Například `@namespace` směrnice definuje obor názvů komponenty:

```razor
@namespace MyComponentNamespace
```

Následující tabulka shrnuje různé direktivy Razor používané v Blazoru a jejich ASP.NET ekvivalenty webových formulářů, pokud existují.

|Směrnice    |Popis|Příklad|Ekvivalent webových formulářů|
|-------------|-----------|-------|--------------------|
|`@attribute` |Přidá k komponentě atribut na úrovni třídy.|`@attribute [Authorize]`|Žádný|
|`@code`      |Přidá členy třídy do komponenty.|`@code { ... }`|`<script runat="server">...</script>`|
|`@implements`|Implementuje zadané rozhraní|`@implements IDisposable`|Použití kódu na pozadí|
|`@inherits`  |Dědí ze zadané základní třídy|`@inherits MyComponentBase`|`<%@ Control Inherits="MyUserControlBase" %>`|
|`@inject`    |Vstřikuje službu do součásti|`@inject IJSRuntime JS`|Žádný|
|`@layout`    |Určuje komponentu rozvržení pro komponentu.|`@layout MainLayout`|`<%@ Page MasterPageFile="~/Site.Master" %>`|
|`@namespace` |Nastaví obor názvů pro komponentu.|`@namespace MyNamespace`|Žádný|
|`@page`      |Určuje postup pro komponentu.|`@page "/product/{id}"`|`<%@ Page %>`|
|`@typeparam` |Určuje parametr obecného typu pro komponentu.|`@typeparam TItem`|Použití kódu na pozadí|
|`@using`     |Určuje obor názvů, který má být převeden do oboru.|`@using MyComponentNamespace`|Přidání oboru názvů v *souboru web.config*|

Razor komponenty také rozsáhlé použití *atributy směrnice* na prvky řídit různé aspekty, jak se kompilují součásti (zpracování událostí, datové vazby, odkazy na element komponenty & a tak dále). Direktivy všechny postupujte podle běžné obecné syntaxe, kde jsou hodnoty v závorce volitelné:

```razor
@directive(-suffix(:name))(="value")
```

Následující tabulka shrnuje různé atributy direktiv Razor používaných v Blazoru.

|Atribut    |Popis|Příklad|
|-------------|-----------|-------|
|`@attributes`|Vykreslí slovník atributů|`<input @attributes="ExtraAttributes" />`|
|`@bind`      |Vytvoří obousměrnou datovou vazbu.    |`<input @bind="username" @bind:event="oninput" />`|
|`@on{event}` |Přidá obslužnou rutinu události pro zadanou událost.|`<button @onclick="IncrementCount">Click me!</button>`|
|`@key`       |Určuje klíč, který má být použit algoritmus diffing pro zachování prvků v kolekci.|`<DetailsEditor @key="person" Details="person.Details" />`|
|`@ref`       |Zachytí odkaz na komponentu nebo element HTML.|`<MyDialog @ref="myDialog" />`|

Různé atributy směrnice používané Blazorem (`@onclick`, `@bind`, `@ref`, a tak dále) jsou uvedeny v následujících oddílech a v pozdějších kapitolách.

Mnoho syntaxí používaných v *souborech ASPX* a *ASCX* má paralelní syntaxe v Razor. Níže je jednoduché srovnání syntaxí pro ASP.NET webových formulářů a břitva.

|Funkce                      |webové formuláře           |Syntaxe               |Razor         |Syntaxe |
|-----------------------------|--------------------|---------------------|--------------|-------|
|Direktivy                   |`<%@ [directive] %>`|`<%@ Page %>`        |`@[directive]`|`@page`|
|Bloky kódu                  |`<% %>`             |`<% int x = 123; %>` |`@{ }`        |`@{ int x = 123; }`|
|Výrazy<br>(html kódované)|`<%: %>`            |`<%:DateTime.Now %>` |Implicitní:`@`<br>Explicitní:`@()`|`@DateTime.Now`<br>`@(DateTime.Now)`|
|Komentáře                     |`<%-- --%>`         |`<%-- Commented --%>`|`@* *@`       |`@* Commented *@`|
|Datová vazba                 |`<%# %>`            |`<%# Bind("Name") %>`|`@bind`       |`<input @bind="username" />`|

Chcete-li přidat členy do třídy komponenty Razor, použijte direktivu. `@code` Tato technika je podobná `<script runat="server">...</script>` použití bloku v uživatelském ovládacím prvku ASP.NET webových formulářů nebo stránce.

```razor
@code {
    int count = 0;

    void IncrementCount()
    {
        count++;
    }
}
```

Protože Razor je založen na C#, musí být zkompilován z projektu C# (*.csproj).* Soubory *.razor* nelze zkompilovat z projektu jazyka Visual Basic (*.vbproj*). Stále můžete odkazovat na projekty jazyka Visual Basic z projektu Blazor. Opak je také pravdou.

Úplný odkaz na syntaxi Razor najdete v [tématu Razor syntaxe reference for ASP.NET Core](/aspnet/core/mvc/views/razor).

## <a name="use-components"></a>Použití součástí

Kromě normálního kódu HTML mohou komponenty používat také jiné součásti jako součást jejich logiky vykreslování. Syntaxe pro použití komponenty v holicí strojek je podobná použití uživatelského ovládacího prvku v aplikaci ASP.NET Web Forms. Součásti jsou určeny pomocí značky elementu, která odpovídá názvu typu komponenty. Můžete například přidat `Counter` komponentu, jako je tato:

```razor
<Counter />
```

Na rozdíl od ASP.NET webových formulářů, komponenty v Blazor:

- Nepoužívejte předponu prvku `asp:`(například).
- Nevyžadují registraci na stránce nebo na *web.config*.

Myslete na komponenty Razor, jako byste .NET typy, protože to je přesně to, co jsou. Pokud je odkazována sestava obsahující součást, je komponenta k dispozici pro použití. Chcete-li přenést obor názvů komponenty `@using` do oboru, použijte direktivu:

```razor
@using MyComponentLib

<Counter />
```

Jak je vidět ve výchozích projektech Blazor, je běžné umístit `@using` direktivy do souboru *_Imports.razor* tak, aby byly importovány do všech souborů *.razor* ve stejném adresáři a v podřízených adresářích.

Pokud obor názvů pro komponentu není v oboru, můžete určit komponentu pomocí jejího úplného názvu typu, jak je možné v C#:

```razor
<MyComponentLib.Counter />
```

## <a name="component-parameters"></a>Parametry komponenty

V ASP.NET webových formulářů můžete navést parametry a data do ovládacích prvků pomocí veřejných vlastností. Tyto vlastnosti lze nastavit ve značkách pomocí atributů nebo nastavit přímo v kódu. Komponenty Blazor pracují podobným způsobem, i když vlastnosti `[Parameter]` komponenty musí být také označeny atributem, který má být považován za parametry komponenty.

Následující `Counter` komponenta definuje volaný `IncrementAmount` parametr komponenty, který `Counter` lze použít k určení částky, kterou by mělo být při každém klepnutí na tlačítko přírůst.

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

Chcete-li zadat parametr komponenty v Blazoru, použijte atribut jako v ASP.NET webových formulářů:

```razor
<Counter IncrementAmount="10" />
```

## <a name="event-handlers"></a>Obslužné rutiny událostí

Oba ASP.NET Web Forms a Blazor poskytují programovací model založený na událostech pro zpracování událostí uživatelského rozhraní. Příklady takových událostí zahrnují kliknutí na tlačítko a zadávání textu. V ASP.NET webových formulářů používáte serverové ovládací prvky HTML ke zpracování událostí uživatelského rozhraní vystavených dom nebo můžete zpracovávat události vystavené ovládacími prvky webového serveru. Události jsou na serveru vystavovány prostřednictvím požadavků formuláře po vrácení. Zvažte následující tlačítko Webové formuláře, klepněte na příklad:

*Čítač.ascx*

```aspx-csharp
<asp:Button ID="ClickMeButton" runat="server" Text="Click me!" OnClick="ClickMeButton_Click" />
```

*Counter.ascx.cs*

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void ClickMeButton_Click(object sender, EventArgs e)
    {
        Console.WriteLine("The button was clicked!");
    }
}
```

V Blazoru můžete registrovat obslužné rutiny pro události `@on{event}`uzlení DOM přímo pomocí atributů směrnice formuláře . Zástupný `{event}` symbol představuje název události. Můžete například poslouchat kliknutí na tlačítka, jako je tento:

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick()
    {
        Console.WriteLine("The button was clicked!);
    }
}
```

Obslužné rutiny událostí mohou přijmout volitelný argument specifický pro událost, který poskytuje další informace o události. Například události myši může `MouseEventArgs` mít argument, ale není vyžadováno.

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick(MouseEventArgs e)
    {
        Console.WriteLine($"Mouse clicked at {e.ScreenX}, {e.ScreenY}.");
    }
}
```

Místo odkazování na skupinu metod pro obslužnou rutinu události můžete použít výraz lambda. Výraz lambda umožňuje zavřít přes jiné hodnoty v oboru.

```razor
@foreach (var buttonLabel in buttonLabels)
{
    <button @onclick="() => Console.WriteLine($"The {buttonLabel} button was clicked!")">@buttonLabel</button>
}
```

Obslužné rutiny událostí lze spustit synchronně nebo asynchronně. Například následující `OnClick` obslužná rutina události se spouští asynchronně:

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    async Task OnClick()
    {
        var result = await Http.GetAsync("api/values");
    }
}
```

Po zpracování události je komponenta vykreslena tak, aby odpovídala všem změnám stavu součásti. U obslužných rutin asynchronní události je komponenta vykreslena ihned po dokončení spuštění obslužné rutiny. Součást je *vykreslen znovu* po dokončení `Task` asynchronní. Tento režim asynchronního spuštění poskytuje příležitost k vykreslení některé `Task` vhodné uI, zatímco asynchronní je stále probíhá.

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

Komponenty mohou také definovat své vlastní události definováním parametru komponenty typu `EventCallback<TValue>`. Zpětná volání událostí podporují všechny varianty obslužných rutin událostí um DOM: volitelné argumenty, synchronní nebo asynchronní, skupiny metod nebo výrazy lambda.

```razor
<button class="btn btn-primary" @onclick="OnClick">Click me!</button>

@code {
    [Parameter]
    public EventCallback<MouseEventArgs> OnClick { get; set; }
}
```

## <a name="data-binding"></a>Datová vazba

Blazor poskytuje jednoduchý mechanismus pro vazbu dat z komponenty ui do stavu komponenty. Tento přístup se liší od funkcí v ASP.NET webových formulářů pro vazby dat ze zdrojů dat na ovládací prvky uživatelského rozhraní. Zpracování dat z různých zdrojů dat se budeme zabývat v části [Nakládání s údaji.](data.md)

Chcete-li vytvořit obousměrnou datovou vazbu z komponenty ui `@bind` do stavu komponenty, použijte atribut direktivy. V následujícím příkladu je hodnota zaškrtávacího políčka vázána na `isChecked` pole.

```razor
<input type="checkbox" @bind="isChecked" />

@code {
    bool isChecked;
}
```

Při vykreslení komponenty je hodnota zaškrtávacího políčka nastavena na hodnotu `isChecked` pole. Když uživatel přepne zaškrtávací políčko, `onchange` událost je aktivována a `isChecked` pole je nastavena na novou hodnotu. Syntaxe `@bind` v tomto případě je ekvivalentní následující značky:

```razor
<input value="@isChecked" @onchange="(UIChangeEventArgs e) => isChecked = e.Value" />
```

Chcete-li změnit událost použitou `@bind:event` pro vazbu, použijte atribut.

```razor
<input @bind="text" @bind:event="oninput" />
<p>@text</p>

@code {
    string text;
}
```

Komponenty mohou také podporovat datové vazby na jejich parametry. Chcete-li vytvořit vazbu dat, definujte parametr zpětného volání události se stejným názvem jako parametr s povážit. K názvu je přidána přípona "Změněno".

*PasswordBox.holicí strojek*

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

Chcete-li zřetězit datovou vazbu na základní prvek rozhraní, nastavte hodnotu a `@bind` zpracovat událost přímo v prvku ui namísto použití atributu.

Chcete-li vytvořit vazbu `@bind-{Parameter}` na parametr komponenty, použijte atribut k určení parametru, ke kterému chcete vazbu.

```razor
<PasswordBox @bind-Password="password" />

@code {
    string password;
}
```

## <a name="state-changes"></a>Změny stavu

Pokud se stav komponenty změnil mimo normální událost uI nebo zpětné volání události, musí komponenta ručně signalizovat, že je třeba ji znovu vykreslit. Chcete-li signalizovat, že se stav `StateHasChanged` komponenty změnil, zavolejte metodu komponenty.

V níže uvedeném příkladu se `AppState` zobrazí zpráva ze služby, kterou lze aktualizovat v jiných částech aplikace. Komponenta zaregistruje `StateHasChanged` svou `AppState.OnChange` metodu s událostí tak, aby komponenta je vykreslen a vždy, když zpráva získá aktualizován.

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

## <a name="component-lifecycle"></a>Životní cyklus komponenty

Rozhraní ASP.NET webových formulářů obsahuje dobře definované metody životního cyklu pro moduly, stránky a ovládací prvky. Například následující ovládací prvek implementuje `Init`obslužné rutiny událostí pro události , `Load`a `UnLoad` životního cyklu:

*Counter.ascx.cs*

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void Page_Init(object sender, EventArgs e) { ... }
    protected void Page_Load(object sender, EventArgs e) { ... }
    protected void Page_UnLoad(object sender, EventArgs e) { ... }
}
```

Komponenty Blazor mají také dobře definovaný životní cyklus. Životní cyklus komponenty lze použít k inicializaci stavu komponenty a implementaci rozšířeného chování součástí.

Všechny metody životního cyklu komponent Blazor mají synchronní i asynchronní verze. Vykreslování komponent je synchronní. Asynchronní logiku nelze spustit jako součást vykreslování komponenty. Všechny asynchronní logiky musí spustit `async` jako součást metody životního cyklu.

### <a name="oninitialized"></a>Přiicializováno

Metody `OnInitialized` `OnInitializedAsync` a se používají k inicializaci komponenty. Komponenta je obvykle inicializována po prvním vykreslení. Po inicializování součásti může být vykreslena vícekrát před tím, než je nakonec uvolněna. Metoda `OnInitialized` je podobná `Page_Load` události na stránkách a ovládacích prvcích webových formulářů ASP.NET.

```csharp
protected override void OnInitialized() { ... }
protected override async Task OnInitializedAsync() { await ... }
```

### <a name="onparametersset"></a>OnParametersSet

Metody `OnParametersSet` `OnParametersSetAsync` a jsou volány, když komponenta obdržela parametry od nadřazeného a hodnota je přiřazena vlastnostem. Tyto metody jsou prováděny po inicializaci komponenty a *při každém vykreslení komponenty*.

```csharp
protected override void OnParametersSet() { ... }
protected override async Task OnParametersSetAsync() { await ... }
```

### <a name="onafterrender"></a>OnAfterRender

Metody `OnAfterRender` `OnAfterRenderAsync` a jsou volány po dokončení vykreslování komponenty. Odkazy na elementy a komponenty jsou vyplněny v tomto okamžiku (více o těchto konceptech níže). Interaktivita s prohlížečem je v tomto okamžiku povolena. Interakce s dom a JavaScript provedení může bezpečně probíhat.

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

`OnAfterRender`a `OnAfterRenderAsync` *nejsou volány při předběžném vykreslování na serveru*.

Parametr `firstRender` je `true` poprvé, kdy je komponenta vykreslena; jinak je `false`jeho hodnota .

### <a name="idisposable"></a>Idisposable

Komponenty Blazor `IDisposable` lze implementovat k vyřazení prostředků při odebrání komponenty z unového nástroje. Razor komponenta `IDispose` lze implementovat pomocí `@implements` směrnice:

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

## <a name="capture-component-references"></a>Zachycení odkazů na součásti

V ASP.NET webových formulářů je běžné manipulovat s instanci ovládacího prvku přímo v kódu odkazem na jeho ID. V Blazoru je také možné zachytit a manipulovat s odkazem na komponentu, i když je mnohem méně častá.

Chcete-li zachytit odkaz na komponentu `@ref` v Blazoru, použijte atribut direktivy. Hodnota atributu by měla odpovídat názvu tištěného pole se stejným typem jako odkazovaná komponenta.

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

Při vykreslení nadřazené součásti je pole naplněno podřízenou instancí komponenty. Potom můžete volat metody na nebo jinak manipulovat s instancí komponenty.

Manipulace se stavem komponenty přímo pomocí odkazů na komponenty se nedoporučuje. Tím zabráníte automatickému vykreslení součásti ve správný čas.

## <a name="capture-element-references"></a>Zachycení odkazů na elementy

Komponenty Blazor umějí zachytit odkazy na prvek. Na rozdíl od serverových ovládacích prvků HTML v ASP.NET webových formulářů nelze s dom přímo manipulovat pomocí odkazu na element v Blazoru. Blazor zpracovává většinu dom interakcí pro vás pomocí jeho DOM diffing algoritmus. Zachycené odkazy na elementy v Blazoru jsou neprůhledné. Používají se však k předání odkazu na určitý prvek v volání interop javascriptu. Další informace o javascriptovém interopu najdete [v tématu ASP.NET Core Blazor JavaScript interop](/aspnet/core/blazor/javascript-interop).

## <a name="templated-components"></a>Komponenty bez vizuálního vzhledu

Ve ASP.NET webových formulářů můžete vytvářet *šablony ovládacích prvků*. Šablony ovládací prvky umožňují vývojáři určit část HTML, která slouží k vykreslení ovládacího prvku kontejneru. Mechanika vytváření šablonových serverových ovládacích prvků je složitá, ale umožňují výkonné scénáře pro vykreslování dat uživatelsky přizpůsobitelným způsobem. Příklady šablonovaných ovládacích prvků zahrnují `Repeater` a `DataList`.

Komponenty Blazor lze také šablonovat definováním parametrů `RenderFragment` `RenderFragment<T>`komponent typu nebo . A `RenderFragment` představuje blok razor značky, které pak mohou být vykresleny komponenty. A `RenderFragment<T>` je blok značky Razor, který přebírá parametr, který lze zadat při vykreslení fragmentu vykreslení.

### <a name="child-content"></a>Podřízený obsah

Komponenty Blazor mohou zachytit svůj `RenderFragment` podřízený obsah jako a vykreslit tento obsah jako součást vykreslování komponent. Chcete-li zachytit podřízený obsah, `RenderFragment` definujte `ChildContent`parametr komponenty typu a pojmenujte jej .

*ChildContentComponent.razor*

```razor
<h1>Component with child content</h1>

<div>@ChildContent</div>

@code {
    [Parameter]
    public RenderFragment ChildContent { get; set; }
}
```

Nadřazená komponenta pak může poskytovat podřízený obsah pomocí normální syntaxe Razor.

```razor
<ChildContentComponent>
    <p>The time is @DateTime.Now</p>
</ChildContentComponent>
```

### <a name="template-parameters"></a>Parametry šablony

Šablonovaná komponenta Blazor může také definovat `RenderFragment` více `RenderFragment<T>`parametrů komponent typu nebo . Parametr pro `RenderFragment<T>` lze zadat, když je vyvolána. Chcete-li zadat parametr obecného typu `@typeparam` pro komponentu, použijte direktivu Razor.

*SimpleListView.holicí strojek*

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

Při použití komponenty šablony lze parametry šablony zadat pomocí podřízených prvků, které odpovídají názvům parametrů. Komponenty argumenty `RenderFragment<T>` typu předané jako `context`prvky mají implicitní parametr s názvem . Název tohoto parametru implement můžete `Context` změnit pomocí atributu na podřízeném prvku. Všechny parametry obecného typu lze zadat pomocí atributu, který odpovídá názvu parametru typu. Parametr typu bude pokud možno odvozen:

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

Výstup této součásti vypadá takto:

```html
<h1>My list</h1>
<ul>
    <li>The message is: message1</li>
    <li>The message is: message2</li>
<ul>
```

## <a name="code-behind"></a>Kód na pozadí

Komponenta Blazor je obvykle vytvářena v jednom souboru *.razor.* Je však také možné oddělit kód a značky pomocí souboru s kódem na pozadí. Chcete-li použít soubor komponenty, přidejte soubor C#, který odpovídá názvu souboru součásti, ale s přidanou příponou *CS* (*Counter.razor.cs*). Pomocí souboru C# definujte základní třídu pro komponentu. Základní třídu můžete pojmenovat, co chcete, ale je běžné pojmenovat třídu stejně `Base` jako třída`CounterBase`komponenty, ale s přidaným rozšířením ( ). Třída založená na komponentách `ComponentBase`musí také odvozovat z . Potom v souboru komponenty `@inherits` Razor přidejte direktivu`@inherits CounterBase`k určení základní třídy pro komponentu ( ).

*Counter.břitva*

```razor
@inherits CounterBase

<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button @onclick="IncrementCount">Click me</button>
```

*Counter.razor.cs*

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

Viditelnost členů komponenty v základní třídě musí `protected` být `public` nebo musí být viditelná pro třídu komponenty.

## <a name="additional-resources"></a>Další zdroje

Předchozí není vyčerpávající zacházení se všemi aspekty komponent Blazor. Další informace o [tom,](/aspnet/core/blazor/components)jak vytvořit a používat ASP.NET komponenty Core Razor , naleznete v dokumentaci k Blazoru.

>[!div class="step-by-step"]
>[Předchozí](app-startup.md)
>[další](pages-routing-layouts.md)
