---
title: Sestavení opakovaně použitelných součástí uživatelského rozhraní s Blazor
description: Naučte se sestavovat opakovaně použitelné součásti uživatelského rozhraní Blazor a jak se porovnávají s ovládacími prvky webových formulářů ASP.NET.
author: danroth27
ms.author: daroth
no-loc:
- Blazor
ms.date: 09/18/2019
ms.openlocfilehash: 4fdf062fb719e62b53e47f79db1e93d0bf079350
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267682"
---
# <a name="build-reusable-ui-components-with-no-locblazor"></a>Sestavení opakovaně použitelných součástí uživatelského rozhraní s Blazor

Jednou ze skvělých věcí o webových formulářích ASP.NET je to, jak umožňuje zapouzdření opakovaně použitelných částí kódu uživatelského rozhraní (UI) do opakovaně použitelných ovládacích prvků uživatelského rozhraní. Vlastní uživatelské ovládací prvky lze definovat v označení pomocí souborů *. ascx* . Můžete také vytvořit podrobné serverové ovládací prvky v kódu s podporou plného návrháře.

Blazor podporuje také zapouzdření uživatelského rozhraní prostřednictvím *komponent*. Součást:

- Je samostatně obsažený blok uživatelského rozhraní.
- Udržuje vlastní logiku stavu a vykreslování.
- Může definovat obslužné rutiny událostí uživatelského rozhraní, vytvořit vazby na vstupní data a spravovat svůj životní cyklus.
- Je obvykle definováno v souboru *. Razor* pomocí syntaxe Razor.

## <a name="an-introduction-to-razor"></a>Úvod do Razor

Razor je šablonování jazyk založený na jazyce HTML a jazyce C#. Pomocí Razor můžete hladce přejít mezi značkami a kódem jazyka C# a definovat logiku vykreslování komponent. Když je soubor *. Razor* zkompilován, je logika vykreslování zachycena strukturovaným způsobem ve třídě .NET. Název zkompilované třídy je pořízen z názvu souboru *. Razor* . Obor názvů je pořízen z výchozího oboru názvů pro projekt a cestu ke složce, nebo můžete explicitně zadat obor názvů pomocí `@namespace` direktivy (Další informace o direktivách Razor níže).

Logika vykreslování komponenty je vytvořena pomocí normální značky HTML s dynamickou logikou přidanou pomocí jazyka C#. `@`Znak slouží k přechodu do jazyka C#. Základní informace o tom, jak se přepnul zpátky na HTML, je obvykle inteligentní. Například následující komponenta vykreslí `<p>` značku s aktuálním časem:

```razor
<p>@DateTime.Now</p>
```

Chcete-li explicitně zadat začátek a konec výrazu jazyka C#, použijte závorky:

```razor
<p>@(DateTime.Now)</p>
```

Razor také usnadňuje použití toku řízení jazyka C# ve vaší logice vykreslování. Například můžete podmíněně vykreslit nějaký HTML podobný:

```razor
@if (value % 2 == 0)
{
    <p>The value was even.</p>
}
```

Nebo můžete vygenerovat seznam položek pomocí normální smyčky jazyka C#, `foreach` jako je tato:

```razor
<ul>
@foreach (var item in items)
{
    <li>@item.Text</li>
}
</ul>
```

Direktivy Razor, například direktivy ve webových formulářích ASP.NET, řídí mnoho aspektů, jak je kompilována komponenta Razor. Příklady zahrnují komponentu:

- Obor názvů
- Základní třída
- Implementovaná rozhraní
- Obecné parametry
- Importované obory názvů
- Trasy

Direktivy Razor začínají `@` znakem a jsou obvykle použity na začátku nového řádku na začátku souboru. Například `@namespace` direktiva definuje obor názvů komponenty:

```razor
@namespace MyComponentNamespace
```

Následující tabulka shrnuje různé direktivy Razor používané v Blazor a jejich ekvivalenty webových formulářů ASP.NET, pokud existují.

|Směrnici    |Popis|Příklad|Ekvivalentní webové formuláře|
|-------------|-----------|-------|--------------------|
|`@attribute` |Přidá do komponenty atribut na úrovni třídy.|`@attribute [Authorize]`|Žádné|
|`@code`      |Přidá do komponenty členy třídy.|`@code { ... }`|`<script runat="server">...</script>`|
|`@implements`|Implementuje zadané rozhraní.|`@implements IDisposable`|Použití kódu na pozadí|
|`@inherits`  |Dědí ze zadané základní třídy.|`@inherits MyComponentBase`|`<%@ Control Inherits="MyUserControlBase" %>`|
|`@inject`    |Vloží službu do komponenty.|`@inject IJSRuntime JS`|Žádné|
|`@layout`    |Určuje komponentu rozložení pro komponentu.|`@layout MainLayout`|`<%@ Page MasterPageFile="~/Site.Master" %>`|
|`@namespace` |Nastaví obor názvů pro komponentu.|`@namespace MyNamespace`|Žádné|
|`@page`      |Určuje trasu pro komponentu.|`@page "/product/{id}"`|`<%@ Page %>`|
|`@typeparam` |Určuje parametr obecného typu pro komponentu.|`@typeparam TItem`|Použití kódu na pozadí|
|`@using`     |Určuje obor názvů, který se má uvést do oboru.|`@using MyComponentNamespace`|Přidat obor názvů v *web.config*|

Komponenty Razor také usnadňují rozsáhlé použití *atributů direktiv* u elementů pro řízení různých aspektů, jak se komponenty dostanou kompilovat (zpracování událostí, vázání dat, komponenta & odkazů na prvky a tak dále). Atribut direktivy All se řídí společnou obecnou syntaxí, kde jsou hodnoty v závorkách volitelné:

```razor
@directive(-suffix(:name))(="value")
```

Následující tabulka shrnuje různé atributy pro direktivy Razor používané v Blazor .

|Atribut    |Popis|Příklad|
|-------------|-----------|-------|
|`@attributes`|Vykreslí slovník atributů.|`<input @attributes="ExtraAttributes" />`|
|`@bind`      |Vytvoří obousměrnou datovou vazbu    |`<input @bind="username" @bind:event="oninput" />`|
|`@on{event}` |Přidá obslužnou rutinu události pro určenou událost.|`<button @onclick="IncrementCount">Click me!</button>`|
|`@key`       |Určuje klíč, který má být použit rozdílovým algoritmem pro zachování prvků v kolekci.|`<DetailsEditor @key="person" Details="person.Details" />`|
|`@ref`       |Zachycuje odkaz na komponentu nebo HTML element.|`<MyDialog @ref="myDialog" />`|

Různé atributy direktiv používané pomocí Blazor ( `@onclick` , `@bind` , `@ref` a tak dále) jsou popsány v následujících částech a v pozdějších kapitolách.

Mnohé z syntaxí používaných v souborech *. aspx* a *. ascx* mají paralelní syntaxe v Razor. Níže je jednoduché porovnání syntaxí pro webové formuláře ASP.NET a Razor.

|Příznak                      |webové formuláře           |Syntaxe               |Razor         |Syntaxe |
|-----------------------------|--------------------|---------------------|--------------|-------|
|Direktivy                   |`<%@ [directive] %>`|`<%@ Page %>`        |`@[directive]`|`@page`|
|Bloky kódu                  |`<% %>`             |`<% int x = 123; %>` |`@{ }`        |`@{ int x = 123; }`|
|Výrazy<br>(Kódovaný v HTML)|`<%: %>`            |`<%:DateTime.Now %>` |Nepřímo `@`<br>Explicitně `@()`|`@DateTime.Now`<br>`@(DateTime.Now)`|
|Komentáře                     |`<%-- --%>`         |`<%-- Commented --%>`|`@* *@`       |`@* Commented *@`|
|Datová vazba                 |`<%# %>`            |`<%# Bind("Name") %>`|`@bind`       |`<input @bind="username" />`|

Chcete-li přidat členy do třídy komponenty Razor, použijte `@code` direktivu. Tato technika je podobná použití `<script runat="server">...</script>` bloku v uživatelském ovládacím prvku nebo stránce webových formulářů ASP.NET.

```razor
@code {
    int count = 0;

    void IncrementCount()
    {
        count++;
    }
}
```

Vzhledem k tomu, že je Razor založen na jazyce C#, musí být zkompilován z projektu jazyka C# (*. csproj*). Soubory *. Razor* nemůžete kompilovat z Visual Basicho projektu (*. vbproj*). Stále můžete odkazovat na Visual Basic projekty z Blazor projektu. Opak je pravda.

Úplný odkaz na syntaxe Razor naleznete v tématu [syntaxe Razor reference for ASP.NET Core](/aspnet/core/mvc/views/razor).

## <a name="use-components"></a>Použití komponent

Kromě normálního formátu HTML mohou komponenty také použít jiné komponenty jako součást logiky vykreslování. Syntaxe pro použití komponenty v Razor je podobná použití uživatelského ovládacího prvku v aplikaci webových formulářů ASP.NET. Komponenty jsou určeny pomocí značky elementu, který odpovídá názvu typu komponenty. Například můžete přidat `Counter` komponentu podobné této:

```razor
<Counter />
```

Na rozdíl od webových formulářů ASP.NET, součástí v Blazor :

- Nepoužívejte předponu elementu (například `asp:` ).
- Pro stránku nebo *web.config*Nevyžadovat registraci.

Komponenty Razor si můžete představit jako typy .NET, protože jsou přesně to, co jsou. Pokud je odkazováno na sestavení obsahující komponentu, je součást k dispozici pro použití. Chcete-li převést obor názvů komponenty do oboru, použijte `@using` direktivu:

```razor
@using MyComponentLib

<Counter />
```

Jak je vidět ve výchozích Blazor projektech, je běžné umístit `@using` direktivy do souboru *_Imports. Razor* tak, aby byly importovány do všech souborů *. Razor* ve stejném adresáři a v podřízených adresářích.

Pokud obor názvů pro komponentu není v oboru, můžete určit komponentu pomocí jejího úplného názvu typu, jak je možné v jazyce C#:

```razor
<MyComponentLib.Counter />
```

## <a name="component-parameters"></a>Parametry součásti

Ve webových formulářích ASP.NET můžete Flow parametry a data do ovládacích prvků pomocí veřejných vlastností. Tyto vlastnosti lze nastavit v kódu pomocí atributů nebo nastavit přímo v kódu. Blazor komponenty fungují podobným způsobem, i když vlastnosti komponent musí být označeny `[Parameter]` atributem, který má být považován za parametrem součásti.

Následující `Counter` Komponenta definuje parametr komponenty s názvem `IncrementAmount` , který lze použít k určení množství, které se má `Counter` zvýšit při každém kliknutí na tlačítko.

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

Chcete-li určit parametr komponenty v Blazor , použijte atribut jako ve webových formulářích ASP.NET:

```razor
<Counter IncrementAmount="10" />
```

## <a name="event-handlers"></a>Obslužné rutiny událostí

Jak webové formuláře ASP.NET, tak Blazor poskytují programovací model založený na událostech pro zpracování událostí uživatelského rozhraní. Příklady takových událostí zahrnují kliknutí na tlačítko a textové zadání. Ve webových formulářích ASP.NET používáte ovládací prvky HTML serveru pro zpracování událostí uživatelského rozhraní vystavených modelem DOM, nebo můžete zpracovávat události vystavené ovládacími prvky webového serveru. Události jsou na serveru umístěny prostřednictvím požadavků po návratu do formuláře. Vezměte v úvahu následující tlačítko Web Forms klikněte na příklad:

*Čítač. ascx*

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

V Blazor nástroji můžete zaregistrovat obslužné rutiny pro události uživatelského rozhraní modelu DOM přímo pomocí atributů direktiv formuláře `@on{event}` . `{event}`Zástupný symbol představuje název události. Například můžete naslouchat tomu, že kliknete na tlačítko takto:

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick()
    {
        Console.WriteLine("The button was clicked!);
    }
}
```

Obslužné rutiny událostí mohou pro poskytnutí dalších informací o události přijmout volitelný argument specifický pro událost. Například události myši mohou mít `MouseEventArgs` argument, ale není to vyžadováno.

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick(MouseEventArgs e)
    {
        Console.WriteLine($"Mouse clicked at {e.ScreenX}, {e.ScreenY}.");
    }
}
```

Namísto odkazování na skupinu metod pro obslužnou rutinu události lze použít výraz lambda. Výraz lambda umožňuje zavřít jiné hodnoty v oboru.

```razor
@foreach (var buttonLabel in buttonLabels)
{
    <button @onclick="() => Console.WriteLine($"The {buttonLabel} button was clicked!")">@buttonLabel</button>
}
```

Obslužné rutiny událostí lze provádět synchronně nebo asynchronně. Například následující `OnClick` obslužná rutina události se provádí asynchronně:

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    async Task OnClick()
    {
        var result = await Http.GetAsync("api/values");
    }
}
```

Po zpracování události se komponenta vykreslí do účtu pro všechny změny stavu součásti. Pomocí asynchronních obslužných rutin událostí je komponenta vykreslena ihned po dokončení provádění obslužné rutiny. Komponenta se po dokončení asynchronního vykreslí *znovu* `Task` . Tento režim asynchronního spuštění nabízí možnost vykreslit některé vhodné uživatelské rozhraní, když `Task` je asynchronní operace stále probíhá.

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

Komponenty mohou také definovat vlastní události definováním parametru součásti typu `EventCallback<TValue>` . Zpětná volání událostí podporují všechny variace obslužných rutin událostí rozhraní modelu DOM: nepovinné argumenty, synchronní nebo asynchronní, skupiny metod nebo výrazy lambda.

```razor
<button class="btn btn-primary" @onclick="OnClick">Click me!</button>

@code {
    [Parameter]
    public EventCallback<MouseEventArgs> OnClick { get; set; }
}
```

## <a name="data-binding"></a>Datová vazba

Blazor poskytuje jednoduchý mechanismus pro svázání dat z komponenty uživatelského rozhraní do stavu komponenty. Tento přístup se liší od funkcí ve webových formulářích ASP.NET pro svázání dat ze zdrojů dat až po ovládací prvky uživatelského rozhraní. Zpracováváme data z různých zdrojů dat v části řešení problémů [s daty](data.md) .

Chcete-li vytvořit obousměrnou datovou vazbu z komponenty uživatelského rozhraní do stavu komponenty, použijte `@bind` atribut direktiva. V následujícím příkladu je hodnota zaškrtávacího políčka svázána s `isChecked` polem.

```razor
<input type="checkbox" @bind="isChecked" />

@code {
    bool isChecked;
}
```

Při vykreslení komponenty je hodnota zaškrtávacího políčka nastavena na hodnotu `isChecked` pole. Když uživatel přepíná zaškrtávací políčko, `onchange` událost je aktivována a `isChecked` pole je nastaveno na novou hodnotu. `@bind`Syntaxe v tomto případě je ekvivalentní následujícímu kódu:

```razor
<input value="@isChecked" @onchange="(UIChangeEventArgs e) => isChecked = e.Value" />
```

Chcete-li změnit událost použitou pro BIND, použijte `@bind:event` atribut.

```razor
<input @bind="text" @bind:event="oninput" />
<p>@text</p>

@code {
    string text;
}
```

Komponenty mohou také podporovat datovou vazbu k jejich parametrům. Pro vázání dat definujte parametr zpětného volání události se stejným názvem, jako má parametr s možností vazby. Do názvu se přidá přípona "změněná".

*PasswordBox. Razor*

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

Chcete-li zřetězit datovou vazbu k základnímu prvku uživatelského rozhraní, nastavte hodnotu a zpracujte událost přímo na prvku uživatelského rozhraní namísto použití `@bind` atributu.

Chcete-li vytvořit propojení s parametrem komponenty, použijte `@bind-{Parameter}` atribut k určení parametru, do kterého chcete vytvořit vazby.

```razor
<PasswordBox @bind-Password="password" />

@code {
    string password;
}
```

## <a name="state-changes"></a>Změny stavu

Pokud se stav součásti změnil mimo normální událost uživatelského rozhraní nebo zpětného volání události, musí komponenta ručně signalizovat, že je nutné ji znovu vykreslit. Chcete-li signalizovat, že došlo ke změně stavu komponenty, zavolejte `StateHasChanged` metodu pro komponentu.

V následujícím příkladu komponenta zobrazuje zprávu ze `AppState` služby, kterou lze aktualizovat jinými částmi aplikace. Komponenta registruje svou `StateHasChanged` metodu s `AppState.OnChange` událostí tak, aby se komponenta vykreslila pokaždé, když se zpráva aktualizuje.

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

## <a name="component-lifecycle"></a>Životní cyklus komponent

Rozhraní webových formulářů ASP.NET má dobře definované metody životního cyklu pro moduly, stránky a ovládací prvky. Například následující ovládací prvek implementuje obslužné rutiny událostí pro `Init` `Load` `UnLoad` události životního cyklu, a:

*Counter.ascx.cs*

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void Page_Init(object sender, EventArgs e) { ... }
    protected void Page_Load(object sender, EventArgs e) { ... }
    protected void Page_UnLoad(object sender, EventArgs e) { ... }
}
```

Blazor komponenty mají také dobře definovaný životní cyklus. Životní cyklus komponenty lze použít k inicializaci stavu součásti a implementaci pokročilého chování komponent.

Všechny Blazor metody životního cyklu komponenty mají synchronní i asynchronní verzi. Vykreslování součásti je synchronní. Asynchronní logiku nelze spustit jako součást vykreslování komponenty. Veškerá asynchronní logika musí být spuštěna jako součást `async` metody životního cyklu.

### <a name="oninitialized"></a>Inicializováno

`OnInitialized`Metody a `OnInitializedAsync` se používají k inicializaci komponenty. Komponenta je obvykle inicializována po jejím prvním vykreslení. Po inicializaci komponenty může být vygenerována několikrát, než bude nakonec uvolněna. `OnInitialized`Metoda je podobná události na `Page_Load` stránkách a ovládacích prvcích webových formulářů ASP.NET.

```csharp
protected override void OnInitialized() { ... }
protected override async Task OnInitializedAsync() { await ... }
```

### <a name="onparametersset"></a>OnParametersSet

`OnParametersSet`Metody a `OnParametersSetAsync` jsou volány, když komponenta obdrží parametry z nadřazené položky a hodnota je přiřazena k vlastnostem. Tyto metody jsou spouštěny po inicializaci komponenty a *pokaždé, když je komponenta vykreslena*.

```csharp
protected override void OnParametersSet() { ... }
protected override async Task OnParametersSetAsync() { await ... }
```

### <a name="onafterrender"></a>OnAfterRender

`OnAfterRender`Metody a `OnAfterRenderAsync` jsou volány po dokončení vykreslování součásti. V tomto bodě jsou zaplněny odkazy na elementy a součásti (Další informace o těchto konceptech). V tuto chvíli je povolená interaktivita v prohlížeči. Interakce s modelem DOM a prováděním JavaScriptu můžou bezpečně probíhat.

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

`OnAfterRender` a `OnAfterRenderAsync` *nejsou volány při předvykreslování na serveru*.

`firstRender`Parametr je při `true` prvním vykreslení komponenty, v opačném případě jeho hodnota je `false` .

### <a name="idisposable"></a>IDisposable

Blazor součásti mohou implementovat `IDisposable` pro uvolnění prostředků, pokud je komponenta odebrána z uživatelského rozhraní. Komponenta Razor může implementovat `IDispose` pomocí `@implements` direktivy:

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

## <a name="capture-component-references"></a>Zachytit odkazy na komponenty

Ve webových formulářích ASP.NET je běžné manipulovat s instancí ovládacího prvku přímo v kódu odkazem na jeho ID. V nástroji je Blazor také možné zachytit odkaz na komponentu a manipulovat s nimi, i když je to mnohem méně běžné.

Chcete-li zachytit odkaz na komponentu v Blazor , použijte `@ref` atribut direktiva. Hodnota atributu by měla odpovídat názvu nastavitelné pole se stejným typem, jako má Odkazovaná komponenta.

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

Při vykreslení nadřazené komponenty je pole vyplněno instancí podřízené součásti. Pak můžete zavolat metody do nebo jinak manipulovat s instancí součásti.

Manipulace se stavem součásti přímo pomocí odkazů na součásti se nedoporučuje. Zabráníte tak automatickému vykreslování komponenty ve správných časech.

## <a name="capture-element-references"></a>Zachytit odkazy elementu

Blazor komponenty mohou zachytit odkazy na prvek. Na rozdíl od serverových ovládacích prvků HTML ve webových formulářích ASP.NET nemůžete manipulovat s DOM přímo pomocí odkazu elementu v Blazor . Blazor zpracovává většinu interakcí DOM za použití jejich rozdílového algoritmu modelu DOM. Zachycené odkazy na prvky v Blazor jsou neprůhledné. Používají se však k předání konkrétního odkazu na element ve volání interoperability JavaScriptu. Další informace o zprostředkovateli komunikace s JavaScriptem naleznete v tématu [ASP.NET Core Blazor interoperability JavaScriptu](/aspnet/core/blazor/javascript-interop).

## <a name="templated-components"></a>Komponenty bez vizuálního vzhledu

Ve webových formulářích ASP.NET můžete vytvořit *ovládací prvky s šablonami*. Ovládací prvky s šablonou umožňují vývojáři zadat část kódu HTML použitou k vykreslení ovládacího prvku kontejneru. Mechanismus sestavování serverových ovládacích prvků na základě šablon je složitý, ale umožňuje výkonné scénáře pro vykreslování dat uživatelsky přizpůsobitelným způsobem. Příklady ovládacích prvků s šablonami jsou `Repeater` a `DataList` .

Blazor komponenty lze také šablonou definovat definováním parametrů součásti typu `RenderFragment` nebo `RenderFragment<T>` . `RenderFragment`Představuje blok značek Razor, který lze následně vykreslit komponentou. `RenderFragment<T>`Je blok značek Razor, který přebírá parametr, který lze zadat při vykreslení fragmentu vykreslování.

### <a name="child-content"></a>Podřízený obsah

Blazor komponenty mohou zachytit svůj podřízený obsah jako `RenderFragment` a vykreslovat tento obsah jako součást vykreslování komponent. Chcete-li zachytit podřízený obsah, definujte parametr součásti typu `RenderFragment` a pojmenujte jej `ChildContent` .

*ChildContentComponent. Razor*

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

BlazorKomponenta šablon může také definovat více parametrů součásti typu `RenderFragment` nebo `RenderFragment<T>` . Parametr pro `RenderFragment<T>` lze zadat při jeho vyvolání. Chcete-li zadat parametr obecného typu pro komponentu, použijte `@typeparam` direktivu Razor.

*SimpleListView. Razor*

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

Při použití komponenty se šablonou lze parametry šablony zadat pomocí podřízených prvků, které odpovídají názvům parametrů. Argumenty součásti typu `RenderFragment<T>` předané jako elementy mají implicitní parametr s názvem `context` . Můžete změnit název tohoto parametru implementace pomocí `Context` atributu u podřízeného elementu. Parametry obecného typu lze zadat pomocí atributu, který odpovídá názvu parametru typu. Parametr typu bude odvozený, pokud je to možné:

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

Výstup této součásti vypadá takto:

```html
<h1>My list</h1>
<ul>
    <li><p>The message is: message1</p></li>
    <li><p>The message is: message2</p></li>
<ul>
```

## <a name="code-behind"></a>Kód na pozadí

BlazorSoučást je obvykle vytvořená v jednom souboru *. Razor* . Je však také možné oddělit kód a značky pomocí souboru kódu na pozadí. Chcete-li použít soubor komponenty, přidejte soubor C#, který se shoduje s názvem souboru komponenty, ale s přidaným rozšířením *. cs* (*Counter.Razor.cs*). Použijte soubor C# k definování základní třídy pro komponentu. Základní třídu můžete pojmenovat cokoli, co byste chtěli, ale je běžné pojmenovat třídu stejně jako třídu komponenty, ale s `Base` rozšířením ( `CounterBase` ). Třída založená na komponentě musí také odvozovat z `ComponentBase` . Poté v souboru komponenty Razor přidejte `@inherits` direktivu pro určení základní třídy pro komponentu ( `@inherits CounterBase` ).

*Čítač. Razor*

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

Viditelnost členů komponenty v základní třídě musí být `protected` nebo `public` viditelná pro třídu součásti.

## <a name="additional-resources"></a>Další zdroje

Předchozí není vyčerpávajícím způsobem všech aspektů Blazor komponent. Další informace o tom, jak [vytvořit a používat ASP.NET Core komponenty Razor](/aspnet/core/blazor/components), najdete v Blazor dokumentaci.

>[!div class="step-by-step"]
>[Předchozí](app-startup.md) 
> [Další](pages-routing-layouts.md)
