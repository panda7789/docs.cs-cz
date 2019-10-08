---
title: Sestavení opakovaně použitelných součástí uživatelského rozhraní pomocí Blazor
description: Naučte se sestavovat znovu použitelné součásti uživatelského rozhraní pomocí Blazor a jak se porovnávají s ovládacími prvky webových formulářů ASP.NET.
author: danroth27
ms.author: daroth
ms.date: 09/18/2019
ms.openlocfilehash: c9fb9b3ff59986ebaf64ecb19277ffbbc8696fed
ms.sourcegitcommit: 10db6551ea3c971470cf5d2cc21ba1cbcefe5c55
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/08/2019
ms.locfileid: "72031795"
---
# <a name="build-reusable-ui-components-with-blazor"></a>Sestavení opakovaně použitelných součástí uživatelského rozhraní pomocí Blazor

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Jednou ze skvělých věcí o webových formulářích ASP.NET je to, jak umožňuje zapouzdření opakovaně použitelných částí kódu uživatelského rozhraní (UI) do opakovaně použitelných ovládacích prvků uživatelského rozhraní. Vlastní uživatelské ovládací prvky lze definovat v označení pomocí souborů *. ascx* . Můžete také vytvořit podrobné serverové ovládací prvky v kódu s podporou plného návrháře.

Blazor také podporuje zapouzdření uživatelského rozhraní prostřednictvím *komponent*. Součást:

* Je samostatně obsažený blok uživatelského rozhraní.
* Udržuje vlastní logiku stavu a vykreslování.
* Může definovat obslužné rutiny událostí uživatelského rozhraní, vytvořit vazby na vstupní data a spravovat svůj životní cyklus.
* Je obvykle definováno v souboru *. Razor* pomocí syntaxe Razor.

## <a name="an-introduction-to-razor"></a>Úvod do Razor

Razor je šablonování jazyk založený na jazyce HTML a C#na základě značky. Pomocí Razor můžete hladce přejít mezi značkou a C# kódem pro definování logiky vykreslování komponent. Když je soubor *. Razor* zkompilován, je logika vykreslování zachycena strukturovaným způsobem ve třídě .NET. Název zkompilované třídy je pořízen z názvu souboru *. Razor* . Obor názvů je pořízen z výchozího oboru názvů pro projekt a cestu ke složce, nebo můžete explicitně zadat obor názvů pomocí direktivy `@namespace` (Další informace o direktivách Razor níže).

Logika vykreslování komponenty je vytvořena pomocí normální značky HTML s dynamickou logikou přidanou pomocí C#. Znak `@` se používá k přechodu na C#. Základní informace o tom, jak se přepnul zpátky na HTML, je obvykle inteligentní. Například následující komponenta vykreslí značku `<p>` s aktuálním časem:

```razor
<p>@DateTime.Now</p>
```

Chcete-li explicitně zadat začátek a konec C# výrazu, použijte závorky:

```razor
<p>@(DateTime.Now)</p>
```

Razor také usnadňuje používání C# toku řízení ve vaší logice vykreslování. Například můžete podmíněně vykreslit nějaký HTML podobný:

```razor
@if (value % 2 == 0)
{
    <p>The value was even.</p>
}
```

Nebo můžete vygenerovat seznam položek pomocí normální C# smyčky `foreach`, například takto:

```razor
<ul>
@foreach (var item in items)
{
    <li>item.Text</li>
}
</ul>
```

Direktivy Razor, například direktivy ve webových formulářích ASP.NET, řídí mnoho aspektů, jak je kompilována komponenta Razor. Příklady zahrnují komponentu:

* Obor názvů
* Základní třída
* Implementovaná rozhraní
* Obecné parametry
* Importované obory názvů
* Tras

Direktivy Razor začínají znakem `@` a obvykle se používají na začátku nového řádku na začátku souboru. Například Direktiva `@namespace` definuje obor názvů komponenty:

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
|`@using`     |Určuje obor názvů, který se má uvést do oboru.|`@using MyComponentNamespace`|Přidat obor názvů do *souboru Web. config*|

Komponenty Razor také usnadňují rozsáhlé použití *atributů direktiv* u elementů pro řízení různých aspektů, jak se komponenty dostanou kompilovat (zpracování událostí, vázání dat, komponenta & odkazů na prvky a tak dále). Atribut direktivy All se řídí společnou obecnou syntaxí, kde jsou hodnoty v závorkách volitelné:

```razor
@directive(-suffix(:name))(="value")
```

Následující tabulka shrnuje různé atributy pro direktivy Razor používané v Blazor.

|Atribut    |Popis|Příklad|
|-------------|-----------|-------|
|`@attributes`|Vykreslí slovník atributů.|`<input @attributes="ExtraAttributes" />`|
|`@bind`      |Vytvoří obousměrnou datovou vazbu    |`<input @bind="username" @bind:event="oninput" />`|
|`@on{event}` |Přidá obslužnou rutinu události pro určenou událost.|`<button @onclick="IncrementCount">Click me!</button>`|
|`@key`       |Určuje klíč, který má být použit rozdílovým algoritmem pro zachování prvků v kolekci.|`<DetailsEditor @key="person" Details="person.Details" />`|
|`@ref`       |Zachycuje odkaz na komponentu nebo HTML element.|`<MyDialog @ref="myDialog" />`|

Různé atributy direktiv používané Blazor (`@onclick`, `@bind`, `@ref` atd.) jsou popsány v následujících částech a v pozdějších kapitolách.

Mnohé z syntaxí používaných v souborech *. aspx* a *. ascx* mají paralelní syntaxe v Razor. Níže je jednoduché porovnání syntaxí pro webové formuláře ASP.NET a Razor.

|Funkce                      |webové formuláře           |Syntaxe               |Razor         |Syntaxe |
|-----------------------------|--------------------|---------------------|--------------|-------|
|Direktivy                   |`<%@ [directive] %>`|`<%@ Page %>`        |`@[directive]`|`@page`|
|Bloky kódu                  |`<% %>`             |`<% int x = 123; %>` |`@{ }`        |`@{ int x = 123; }`|
|Výrazy<br>(Kódovaný v HTML)|`<%: %>`            |`<%:DateTime.Now %>` |Implicitní: `@`<br>Explicitní: `@()`|`@DateTime.Now`<br>`@(DateTime.Now)`|
|Komentáře                     |`<%-- --%>`         |`<%-- Commented --%>`|`@* *@`       |`@* Commented *@`|
|Datová vazba                 |`<%# %>`            |`<%# Bind("Name") %>`|`@bind`       |`<input @bind="username" />`|

Chcete-li přidat členy do třídy komponenty Razor, použijte direktivu `@code`. Tato technika je podobná použití bloku `<script runat="server">...</script>` v uživatelském ovládacím prvku nebo stránce webových formulářů ASP.NET.

```razor
@code {
    int count = 0;

    void IncrementCount()
    {
        count++;
    }
}
```

Vzhledem k tomu, že C#je Razor založen na, musí být zkompilován C# z projektu ( *. csproj*). Nemůžete kompilovat soubory *. Razor* z projektu VB ( *. vbproj*). Stále můžete odkazovat na projekty VB z projektu Blazor. Opak je pravda.

Úplný odkaz na syntaxe Razor naleznete v tématu [syntaxe Razor reference for ASP.NET Core](/aspnet/core/mvc/views/razor).

## <a name="use-components"></a>Použití komponent

Kromě normálního formátu HTML mohou komponenty také použít jiné komponenty jako součást logiky vykreslování. Syntaxe pro použití komponenty v Razor je podobná použití uživatelského ovládacího prvku v aplikaci webových formulářů ASP.NET. Komponenty jsou určeny pomocí značky elementu, který odpovídá názvu typu komponenty. Například můžete přidat komponentu `Counter`, například:

```razor
<Counter />
```

Na rozdíl od webových formulářů ASP.NET, komponent v Blazor:

* Nepoužívejte předponu elementu (například `asp:`).
* Nevyžaduje registraci na stránce nebo v *souboru Web. config*.

Komponenty Razor si můžete představit jako typy .NET, protože jsou přesně to, co jsou. Pokud je odkazováno na sestavení obsahující komponentu, je součást k dispozici pro použití. Chcete-li převést obor názvů komponenty do oboru, použijte direktivu `@using`:

```razor
@using MyComponentLib

<Counter />
```

Jak je vidět ve výchozích projektech Blazor, je běžné umístit direktivy `@using` do souboru *_Imports. Razor* tak, aby byly naimportovány do všech souborů *. Razor* ve stejném adresáři a v podřízených adresářích.

Pokud obor názvů pro komponentu není v oboru, můžete určit komponentu pomocí jejího úplného názvu typu, jak můžete v C#:

```razor
<MyComponentLib.Counter />
```

## <a name="component-parameters"></a>Parametry součásti

Ve webových formulářích ASP.NET můžete Flow parametry a data do ovládacích prvků pomocí veřejných vlastností. Tyto vlastnosti lze nastavit v kódu pomocí atributů nebo nastavit přímo v kódu. Komponenty Blazor fungují podobným způsobem, i když vlastnosti komponenty musí být označeny také atributem `[Parameter]`, který se má považovat za parametry součásti.

Následující součást `Counter` definuje parametr komponenty s názvem `IncrementAmount`, který lze použít k určení množství, které by mělo být při každém kliknutí na tlačítko zvýšeno na hodnotu `Counter`.

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

Chcete-li určit parametr komponenty v Blazor, použijte atribut jako ve webových formulářích ASP.NET:

```razor
<Counter IncrementAmount="10" />
```

## <a name="event-handlers"></a>Obslužné rutiny událostí

Webové formuláře ASP.NET a Blazor poskytují programovací model založený na událostech pro zpracování událostí uživatelského rozhraní. Příklady takových událostí zahrnují kliknutí na tlačítko a textové zadání. Ve webových formulářích ASP.NET používáte ovládací prvky HTML serveru pro zpracování událostí uživatelského rozhraní vystavených modelem DOM, nebo můžete zpracovávat události vystavené ovládacími prvky webového serveru. Události jsou na serveru umístěny prostřednictvím požadavků po návratu do formuláře. Vezměte v úvahu následující tlačítko Web Forms klikněte na příklad:

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

V Blazor můžete zaregistrovat obslužné rutiny pro události uživatelského rozhraní modelu DOM přímo pomocí atributů direktiv ve formátu `@on{event}`. Zástupný symbol `{event}` představuje název události. Například můžete naslouchat tomu, že kliknete na tlačítko takto:

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick()
    {
        Console.WriteLine("The button was clicked!);
    }
}
```

Obslužné rutiny událostí mohou pro poskytnutí dalších informací o události přijmout volitelný argument specifický pro událost. Události myši mohou například přebírat @no__t argument-0, ale není vyžadováno.

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

Obslužné rutiny událostí lze provádět synchronně nebo asynchronně. Například následující obslužná rutina události `OnClick` se spouští asynchronně:

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    async Task OnClick() 
    {
        var result = await Http.GetAsync("api/values");
    }
}
```

Po zpracování události se komponenta vykreslí do účtu pro všechny změny stavu součásti. Pomocí asynchronních obslužných rutin událostí je komponenta vykreslena ihned po dokončení provádění obslužné rutiny. Komponenta se po dokončení asynchronního `Task` *znovu* vykreslí. Tento režim asynchronního spuštění nabízí možnost vykreslit některé vhodné uživatelské rozhraní, když asynchronní `Task` stále probíhá.

```razor
<button @onclick="Get message">Get message</button>

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

Komponenty mohou také definovat vlastní události definováním parametru součásti typu `EventCallback<TValue>`. Zpětná volání událostí podporují všechny variace obslužných rutin událostí rozhraní modelu DOM: nepovinné argumenty, synchronní nebo asynchronní, skupiny metod nebo výrazy lambda.

```razor
<button class="btn btn-primary" @onclick="OnClick">Click me!</button>

@code {
    [Parameter]
    public EventCallback<MouseEventArgs> OnClick { get; set; }
}
```

## <a name="data-binding"></a>Datová vazba

Blazor poskytuje jednoduchý mechanismus pro svázání dat z komponenty uživatelského rozhraní do stavu komponenty. Tento přístup se liší od funkcí ve webových formulářích ASP.NET pro svázání dat ze zdrojů dat až po ovládací prvky uživatelského rozhraní. Zpracováváme data z různých zdrojů dat v části řešení problémů [s daty](data.md) .

Chcete-li vytvořit obousměrnou datovou vazbu z komponenty uživatelského rozhraní do stavu komponenty, použijte atribut direktivy `@bind`. V následujícím příkladu je hodnota zaškrtávacího políčka svázána s polem `isChecked`.

```razor
<input type="checkbox" @bind="isChecked" />

@code {
    bool isChecked;
}
```

Při vykreslení komponenty je hodnota CheckBox nastavena na hodnotu pole `isChecked`. Když uživatel přepíná zaškrtávací políčko, aktivuje se událost `onchange` a pole `isChecked` bude nastaveno na novou hodnotu. Syntaxe `@bind` v tomto případě je ekvivalentní následujícímu kódu:

```razor
<input value="@isChecked" @onchange="(UIChangeEventArgs e) => isChecked = e.Value" />
```

Pokud chcete změnit událost, která se používá pro BIND, použijte atribut `@bind:event`.

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

Chcete-li zřetězit datovou vazbu k základnímu prvku uživatelského rozhraní, nastavte hodnotu a zpracujte událost přímo na prvku uživatelského rozhraní místo použití atributu `@bind`.

Chcete-li vytvořit propojení s parametrem komponenty, použijte atribut `@bind-{Parameter}` k určení parametru, do kterého chcete vytvořit vazby.

```razor
<PasswordBox @bind-Password="password" />

@code {
    string password;
}
```

## <a name="state-changes"></a>Změny stavu

Pokud se stav součásti změnil mimo normální událost uživatelského rozhraní nebo zpětného volání události, musí komponenta ručně signalizovat, že je nutné ji znovu vykreslit. Chcete-li signalizovat, že došlo ke změně stavu komponenty, zavolejte na komponentu metodu `StateHasChanged`.

V následujícím příkladu se součástí zobrazí zpráva od @no__t 0, kterou je možné aktualizovat jinými částmi aplikace. Komponenta zaregistruje svou metodu `StateHasChanged` s událostí `AppState.OnChange` tak, aby se komponenta vykreslila pokaždé, když se zpráva aktualizuje.

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

## <a name="component-lifecycle"></a>Životní cyklus komponent

Rozhraní webových formulářů ASP.NET má dobře definované metody životního cyklu pro moduly, stránky a ovládací prvky. Například následující ovládací prvek implementuje obslužné rutiny událostí pro události životního cyklu `Init`, `Load` a `UnLoad`:

*Counter.ascx.cs*

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void Page_Init(object sender, EventArgs e) { ... }
    protected void Page_Load(object sender, EventArgs e) { ... }
    protected void Page_UnLoad(object sender, EventArgs e) { ... }
}
```

Komponenty Blazor mají také dobře definovaný životní cyklus. Životní cyklus komponenty lze použít k inicializaci stavu součásti a implementaci pokročilého chování komponent. 

Všechny metody životního cyklu komponenty Blazor mají synchronní i asynchronní verzi. Vykreslování součásti je synchronní. Asynchronní logiku nelze spustit jako součást vykreslování komponenty. Veškerá asynchronní logika musí být spuštěna jako součást metody životního cyklu `async`.

### <a name="oninitialized"></a>Inicializováno

Metody `OnInitialized` a `OnInitializedAsync` slouží k inicializaci komponenty. Komponenta je obvykle inicializována po jejím prvním vykreslení. Po inicializaci komponenty může být vygenerována několikrát, než bude nakonec uvolněna. Metoda `OnInitialized` se podobá události `Page_Load` na stránkách a ovládacích prvcích webových formulářů ASP.NET.

```csharp
protected override void OnInitialized() { ... }
protected override async Task OnInitializedAsync() { await ... }
```

### <a name="onparametersset"></a>OnParametersSet

Metody `OnParametersSet` a `OnParametersSetAsync` jsou volány, když komponenta obdrží parametry z jejího nadřazeného objektu a hodnota je přiřazena k vlastnostem. Tyto metody jsou spouštěny po inicializaci komponenty a *pokaždé, když je komponenta vykreslena*.

```csharp
protected override void OnParametersSet() { ... }
protected override async Task OnParametersSetAsync() { await ... }
```

### <a name="onafterrender"></a>OnAfterRender

Metody `OnAfterRender` a `OnAfterRenderAsync` jsou volány po dokončení vykreslování součásti. V tomto bodě jsou zaplněny odkazy na elementy a součásti (Další informace o těchto konceptech). V tuto chvíli je povolená interaktivita v prohlížeči. Interakce s modelem DOM a prováděním JavaScriptu můžou bezpečně probíhat. 

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

Parametr `firstRender` je při prvním vykreslení komponenty `true`. v opačném případě je jeho hodnota `false`.

### <a name="idisposable"></a>IDisposable

Komponenty Blazor můžou implementovat `IDisposable` k Dispose prostředků, když se komponenta z uživatelského rozhraní odebere. Komponenta Razor může implementovat `IDispose` pomocí direktivy `@implements`:

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

Ve webových formulářích ASP.NET je běžné manipulovat s instancí ovládacího prvku přímo v kódu odkazem na jeho ID. V Blazor je také možné zachytit odkaz na komponentu a manipulovat s nimi, i když je to mnohem méně běžné.

Chcete-li zachytit odkaz na komponentu v Blazor, použijte atribut direktivy `@ref`. Hodnota atributu by měla odpovídat názvu nastavitelné pole se stejným typem, jako má Odkazovaná komponenta.

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

Komponenty Blazor mohou zachytit odkazy na prvek. Na rozdíl od serverových ovládacích prvků HTML ve webových formulářích ASP.NET nemůžete manipulovat s DOM přímo pomocí odkazu elementu v Blazor. Blazor zpracovává většinu interakcí DOM za použití jejich rozdílového algoritmu modelu DOM. Zachycené odkazy na prvky v Blazor jsou neprůhledné. Používají se však k předání konkrétního odkazu na element ve volání interoperability JavaScriptu. Další informace o zprostředkovateli komunikace s JavaScriptem naleznete v tématu [ASP.NET Core Blazor JavaScript](/aspnet/core/blazor/javascript-interop).

## <a name="templated-components"></a>Komponenty se šablonami

Ve webových formulářích ASP.NET můžete vytvořit *ovládací prvky s šablonami*. Ovládací prvky s šablonou umožňují vývojáři zadat část kódu HTML použitou k vykreslení ovládacího prvku kontejneru. Mechanismus sestavování serverových ovládacích prvků na základě šablon je složitý, ale umožňuje výkonné scénáře pro vykreslování dat uživatelsky přizpůsobitelným způsobem. Příklady ovládacích prvků s šablonami zahrnují `Repeater` a `DataList`. 

Komponenty Blazor lze také šablonou definovat definováním parametrů součásti typu `RenderFragment` nebo `RenderFragment<T>`. @No__t-0 představuje blok značek Razor, který lze následně vykreslit komponentou. @No__t-0 je blok značek Razor, který přebírá parametr, který lze zadat při vykreslení fragmentu vykreslování.

### <a name="child-content"></a>Podřízený obsah

Komponenty Blazor můžou zachytit svůj podřízený obsah jako `RenderFragment` a tento obsah vykreslit jako součást vykreslování komponent. Chcete-li zachytit podřízený obsah, definujte parametr součásti typu `RenderFragment` a pojmenujte jej `ChildContent`.

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

Komponenta Blazor založená na šablonách může také definovat více parametrů součásti typu `RenderFragment` nebo `RenderFragment<T>`. Parametr pro `RenderFragment<T>` lze zadat při jeho vyvolání. Chcete-li určit parametr obecného typu pro komponentu, použijte direktivu `@typeparam` Razor.

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

Při použití komponenty se šablonou lze parametry šablony zadat pomocí podřízených prvků, které odpovídají názvům parametrů. Argumenty součásti typu `RenderFragment<T>` předané jako elementy mají implicitní parametr s názvem `context`. Můžete změnit název tohoto parametru implementace pomocí atributu `Context` u podřízeného elementu. Parametry obecného typu lze zadat pomocí atributu, který odpovídá názvu parametru typu. Parametr typu bude odvozený, pokud je to možné:

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

Komponenta Blazor je obvykle vytvořená v jednom souboru *. Razor* . Je však také možné oddělit kód a značky pomocí souboru kódu na pozadí. Chcete-li použít soubor komponenty, přidejte C# soubor, který se shoduje s názvem souboru komponenty, ale s přidaným rozšířením *. cs* (*Counter.Razor.cs*). Použijte C# soubor k definování základní třídy pro komponentu. Základní třídu můžete pojmenovat cokoli, co byste chtěli, ale je běžné ji pojmenovat stejně jako třídu komponenty, ale s rozšířením `Base` přidáno (`CounterBase`). Třída založená na komponentě musí být také odvozena od `ComponentBase`. Poté v souboru komponenty Razor přidejte direktivu `@inherits`, abyste určili základní třídu pro komponentu (`@inherits CounterBase`).

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

Viditelnost členů komponenty v základní třídě musí být `protected` nebo `public` pro viditelnost třídy součásti.

## <a name="additional-resources"></a>Další zdroje

Předchozí není vyčerpávajícím způsobem všech aspektů Blazor komponent. Další informace o tom, jak [vytvořit a používat ASP.NET Core komponenty Razor](/aspnet/core/blazor/components), najdete v dokumentaci k Blazor.

>[!div class="step-by-step"]
>[Předchozí](app-startup.md)
>[Další](pages-routing-layouts.md)
