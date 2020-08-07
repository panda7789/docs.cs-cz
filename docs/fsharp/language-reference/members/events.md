---
title: Události
description: 'Přečtěte si, jak události F # umožňují přidružit volání funkcí k akcím uživatele, které jsou důležité při programování v grafickém uživatelském rozhraní.'
ms.date: 05/16/2016
ms.openlocfilehash: 682686ba58d0f7a56e7da2585e6507ccd0156a44
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2020
ms.locfileid: "87854929"
---
# <a name="events"></a>Události

Události umožňují přiřadit funkce volání a akce uživatele a jsou důležité pro programování grafického uživatelského rozhraní. Události je možné spouštět také pomocí aplikací nebo operačního systému.

> [!NOTE]
> Reference k rozhraní docs.microsoft.com API pro F # není dokončená. Pokud narazíte na nefunkční odkazy, místo toho použijte [dokumentaci základní knihovny F #](https://fsharp.github.io/fsharp-core-docs/) .

## <a name="handling-events"></a>Zpracování událostí

Pokud použijete knihovnu grafického uživatelského rozhraní, jako jsou formuláře Windows Forms nebo Windows Presentation Foundation (WPF), je většina kódu v aplikaci spuštěna jako odpověď na události, které byly předdefinovány knihovnou. Tyto předdefinované události jsou členy tříd grafického uživatelského rozhraní, jako jsou formuláře a ovládací prvky. Můžete přidat vlastní chování k již existující události, jako je například kliknutí na tlačítko, odkazem na konkrétní pojmenovanou událost zájmu (například na `Click` událost `Form` třídy) a voláním `Add` metody, jak je znázorněno v následujícím kódu. Pokud spustíte tento příkaz z F# Interactive, vynechejte volání `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3601.fs)]

Typ `Add` metody je `('a -> unit) -> unit` . Proto metoda obslužné rutiny události přijímá jeden parametr, obvykle argumenty události a vrací `unit` . Předchozí příklad znázorňuje ovladač událostí jako výraz lambda. Ovladačem událostí může být také hodnota funkce, jako v následujícím příkladu kódu. Následující příklad kódu znázorňuje také použití parametrů ovladače událostí, který poskytuje informace specifické pro daný typ události. Pro `MouseMove` událost systém předává `System.Windows.Forms.MouseEventArgs` objekt, který obsahuje `X` a `Y` pozici ukazatele.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3602.fs)]

## <a name="creating-custom-events"></a>Vytváření vlastních událostí

Události f # jsou reprezentovány třídou [Event](https://msdn.microsoft.com/library/f3b47c8a-4ee5-4ce8-9a72-ad305a17c4b9) jazyka f #, která implementuje rozhraní [IEvent](https://msdn.microsoft.com/library/8dbca0df-f8a1-40bd-8d50-aa26f6a8b862) . `IEvent`je to rozhraní, které kombinuje funkce dvou dalších rozhraní `System.IObservable<'T>` a [IDelegateEvent](https://msdn.microsoft.com/library/3d849465-6b8e-4fc5-b36c-2941d734268a). Proto `Event` mají ekvivalentní funkce delegátů v jiných jazycích a další funkce z `IObservable` , což znamená, že události jazyka f # podporují filtrování událostí a používají funkce první třídy jazyka f # a lambda výrazy jako obslužné rutiny událostí. Tato funkce je k dispozici v [modulu Event](https://msdn.microsoft.com/library/8b883baa-a460-4840-9baa-de8260351bc7).

Chcete-li vytvořit událost pro třídu, která funguje stejně jako jakákoli jiná událost .NET Framework, přidejte do třídy `let` vazbu, která definuje `Event` jako pole ve třídě. Můžete zadat požadovaný typ argumentu události jako typ argumentu, nebo jej ponechat prázdný a odvodit odpovídající typ pomocí kompilátoru. Musíte také definovat člen události, který zpřístupňuje událost jako událost typu CLI. Tento člen by měl mít atribut [CLIEvent](https://msdn.microsoft.com/library/d359f1dd-ffa5-42fb-8808-b4c8131a0333) . Je deklarován jako vlastnost a její implementace je pouze voláním vlastnosti [publikovat](https://msdn.microsoft.com/library/b0fdaad5-25e5-43d0-9c0c-ce37c4aeb68e) události. Uživatelé vaší třídy mohou použít `Add` metodu publikované události pro přidání obslužné rutiny. Argumentem `Add` metody může být výraz lambda. Můžete použít `Trigger` vlastnost události k vyvolání události a předání argumentů funkci obslužné rutiny. Následující příklad kódu to dokládá. V tomto příkladu je odvozeným argumentem typu události řazená kolekce, která představuje argumenty pro výraz lambda.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3605.fs)]

Výstup je následující.

```console
Event1 occurred! Object data: Hello World!
```

Další funkce poskytované `Event` modulem jsou znázorněny zde. Následující příklad kódu ukazuje základní použití `Event.create` pro vytvoření události a metody triggeru, přidání dvou obslužných rutin událostí ve formě výrazů lambda a následnou aktivací události pro provedení obou výrazů lambda.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3603.fs)]

Výstup předchozího kódu vypadá takto.

```console
Event occurred.
Given a value: Event occurred.
```

## <a name="processing-event-streams"></a>Zpracování datových proudů události

Místo pouhého přidání obslužné rutiny události pro událost pomocí funkce [Event. Add](https://msdn.microsoft.com/library/10670d3b-8d47-4f6e-b8df-ebc6f64ef4fd) můžete použít funkce v `Event` modulu ke zpracování datových proudů událostí v vysoce přizpůsobených způsobech. K tomu je třeba použít přesměrování přesměrování ( `|>` ) spolu s událostí jako první hodnotu v řadě volání funkce a `Event` modul funguje jako následné volání funkce.

Následující příklad kódu ukazuje, jak lze nastavit událost, pro kterou je ovladač událostí volán pouze za určitých podmínek.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3604.fs)]

[Pozorovatelný modul](https://msdn.microsoft.com/library/16b8610b-b30a-4df7-aa99-d9d352276227) obsahuje podobné funkce, které fungují na pozorovatelných objektech. Pozorovatelné objekty jsou podobné událostem, aktivně se však k událostem přihlašují pouze tehdy, jsou-li samy přihlašovány.

## <a name="implementing-an-interface-event"></a>Implementace události rozhraní

Při vývoji součástí uživatelského rozhraní začínáte často tak, že vytvoříte nový formulář nebo nový ovládací prvek, který se dědí z existujícího formuláře nebo ovládacího prvku. Události jsou často definovány v rozhraní. V takovém případě pak musíte implementovat rozhraní za účelem implementace události. `System.ComponentModel.INotifyPropertyChanged`Rozhraní definuje jednu `System.ComponentModel.INotifyPropertyChanged.PropertyChanged` událost. Následující kód znázorňuje způsob implementace události, kterou toto zděděné rozhraní definuje:

```fsharp
module CustomForm

open System.Windows.Forms
open System.ComponentModel

type AppForm() as this =
    inherit Form()

    // Define the propertyChanged event.
    let propertyChanged = Event<PropertyChangedEventHandler, PropertyChangedEventArgs>()
    let mutable underlyingValue = "text0"

    // Set up a click event to change the properties.
    do
        this.Click |> Event.add(fun evArgs ->
            this.Property1 <- "text2"
            this.Property2 <- "text3")

    // This property does not have the property-changed event set.
    member val Property1 : string = "text" with get, set

    // This property has the property-changed event set.
    member this.Property2
        with get() = underlyingValue
        and set(newValue) =
            underlyingValue <- newValue
            propertyChanged.Trigger(this, new PropertyChangedEventArgs("Property2"))

    // Expose the PropertyChanged event as a first class .NET event.
    [<CLIEvent>]
    member this.PropertyChanged = propertyChanged.Publish

    // Define the add and remove methods to implement this interface.
    interface INotifyPropertyChanged with
        member this.add_PropertyChanged(handler) = propertyChanged.Publish.AddHandler(handler)
        member this.remove_PropertyChanged(handler) = propertyChanged.Publish.RemoveHandler(handler)

    // This is the event-handler method.
    member this.OnPropertyChanged(args : PropertyChangedEventArgs) =
        let newProperty = this.GetType().GetProperty(args.PropertyName)
        let newValue = newProperty.GetValue(this :> obj) :?> string
        printfn "Property %s changed its value to %s" args.PropertyName newValue

// Create a form, hook up the event handler, and start the application.
let appForm = new AppForm()
let inpc = appForm :> INotifyPropertyChanged
inpc.PropertyChanged.Add(appForm.OnPropertyChanged)
Application.Run(appForm)
```

Pokud chcete událost v konstruktoru připojit, je kód trochu složitější, protože Event propojení musí být v `then` bloku v dalším konstruktoru, jako v následujícím příkladu:

```fsharp
module CustomForm

open System.Windows.Forms
open System.ComponentModel

// Create a private constructor with a dummy argument so that the public
// constructor can have no arguments.
type AppForm private (dummy) as this =
    inherit Form()

    // Define the propertyChanged event.
    let propertyChanged = Event<PropertyChangedEventHandler, PropertyChangedEventArgs>()
    let mutable underlyingValue = "text0"

    // Set up a click event to change the properties.
    do
        this.Click |> Event.add(fun evArgs ->
            this.Property1 <- "text2"
            this.Property2 <- "text3")

    // This property does not have the property changed event set.
    member val Property1 : string = "text" with get, set

    // This property has the property changed event set.
    member this.Property2
        with get() = underlyingValue
        and set(newValue) =
            underlyingValue <- newValue
            propertyChanged.Trigger(this, new PropertyChangedEventArgs("Property2"))

    [<CLIEvent>]
    member this.PropertyChanged = propertyChanged.Publish

    // Define the add and remove methods to implement this interface.
    interface INotifyPropertyChanged with
        member this.add_PropertyChanged(handler) = this.PropertyChanged.AddHandler(handler)
        member this.remove_PropertyChanged(handler) = this.PropertyChanged.RemoveHandler(handler)

    // This is the event handler method.
    member this.OnPropertyChanged(args : PropertyChangedEventArgs) =
        let newProperty = this.GetType().GetProperty(args.PropertyName)
        let newValue = newProperty.GetValue(this :> obj) :?> string
        printfn "Property %s changed its value to %s" args.PropertyName newValue

    new() as this =
        new AppForm(0)
        then
            let inpc = this :> INotifyPropertyChanged
            inpc.PropertyChanged.Add(this.OnPropertyChanged)

// Create a form, hook up the event handler, and start the application.
let appForm = new AppForm()
Application.Run(appForm)
```

## <a name="see-also"></a>Viz také

- [Členové](index.md)
- [Zpracování a generování událostí](../../../standard/events/index.md)
- [Výrazy lambda: `fun` klíčové slovo](../functions/lambda-expressions-the-fun-keyword.md)
- [Control. Event – modul](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event-module-%5bfsharp%5d)
- [Control. Event&#60; ne&#62; třídy](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27t%5d-class-%5bfsharp%5d)
- [Control. Event&#60; Delegate, args&#62; class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27delegate%2c%27args%5d-class-%5bfsharp%5d)
