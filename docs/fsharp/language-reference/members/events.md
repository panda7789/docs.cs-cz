---
title: Události
description: Zjistěte, jak F# události umožňují přiřadit funkce volání akce uživatelů, které jsou důležité pro programování grafického uživatelského rozhraní.
ms.date: 05/16/2016
ms.openlocfilehash: 8972d9ab358ff9ff903e8bbbe42b74beea683233
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59226999"
---
# <a name="events"></a>Události

> [!NOTE]
> Rozhraní API referenčních odkazů v tomto článku se dostanete na webu MSDN.  Reference k rozhraní API webu docs.microsoft.com není dokončena.

Události umožňují přiřadit funkce volání a akce uživatele a jsou důležité pro programování grafického uživatelského rozhraní. Události je možné spouštět také pomocí aplikací nebo operačního systému.

## <a name="handling-events"></a>Zpracování událostí

Pokud použijete knihovnu grafického uživatelského rozhraní, jako jsou formuláře Windows Forms nebo Windows Presentation Foundation (WPF), je většina kódu v aplikaci spuštěna jako odpověď na události, které byly předdefinovány knihovnou. Tyto předdefinované události jsou členy tříd grafického uživatelského rozhraní, jako jsou formuláře a ovládací prvky. Můžete přidat vlastní chování k dříve existující události, jako je kliknutí na tlačítko, odkaz na konkrétní pojmenované události zájmu (například `Click` událost `Form` třídy) a vyvolání `Add` způsob, jak je znázorněno v následujícím kódu . Při spuštění z F# Interactive vynechejte volání `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)`.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3601.fs)]

Typ `Add` je metoda `('a -> unit) -> unit`. Proto se metody obslužné rutiny události přijímá jeden parametr, většinou s argumenty události a vrátí `unit`. Předchozí příklad znázorňuje ovladač událostí jako výraz lambda. Ovladačem událostí může být také hodnota funkce, jako v následujícím příkladu kódu. Následující příklad kódu znázorňuje také použití parametrů ovladače událostí, který poskytuje informace specifické pro daný typ události. Pro `MouseMove` předává systém událostí, `System.Windows.Forms.MouseEventArgs` objektu, který obsahuje `X` a `Y` pozici ukazatele.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3602.fs)]

## <a name="creating-custom-events"></a>Vytváření vlastních událostí

F#události jsou reprezentovány F# [události](https://msdn.microsoft.com/library/f3b47c8a-4ee5-4ce8-9a72-ad305a17c4b9) třídy, která implementuje [IEvent](https://msdn.microsoft.com/library/8dbca0df-f8a1-40bd-8d50-aa26f6a8b862) rozhraní. `IEvent` je sama o sobě rozhraní, které kombinuje funkce dvou dalších rozhraní `System.IObservable<'T>` a [IDelegateEvent](https://msdn.microsoft.com/library/3d849465-6b8e-4fc5-b36c-2941d734268a). Proto `Event`y mají obdobné funkce delegátů v jiných jazycích a navíc další funkce `IObservable`, což znamená, že F# události podporují filtrování událostí a používání F# funkce první třídy a výrazy lambda jako ovladačů událostí. Tato funkce je součástí [modul událostí](https://msdn.microsoft.com/library/8b883baa-a460-4840-9baa-de8260351bc7).

Vytvořit událost třídy, která funguje stejně jako ostatní události rozhraní .NET Framework, přidejte do třídy `let` vazbu, která definuje `Event` jako pole v třídě. Můžete zadat požadovaný typ argumentu události jako typ argumentu, nebo jej ponechat prázdný a odvodit odpovídající typ pomocí kompilátoru. Musíte také definovat člen události, který zpřístupňuje událost jako událost typu CLI. Tento člen by měl mít [CLIEvent](https://msdn.microsoft.com/library/d359f1dd-ffa5-42fb-8808-b4c8131a0333) atribut. Je deklarován jako vlastnost a příslušnou implementací je pouhé volání [publikovat](https://msdn.microsoft.com/library/b0fdaad5-25e5-43d0-9c0c-ce37c4aeb68e) vlastnosti události. Uživatelé třídy mohou používat `Add` metoda publikované události pro přidání obslužné rutiny. Argument pro `Add` metoda může být výraz lambda. Můžete použít `Trigger` vlastnosti události, aby se vyvolala událost a předáte argumenty funkci ovladače. Následující příklad kódu to dokládá. V tomto příkladu je odvozeným argumentem typu události řazená kolekce, která představuje argumenty pro výraz lambda.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3605.fs)]

Výstup je následující.

```
Event1 occurred! Object data: Hello World!
```

Další funkce poskytovaná modulem `Event` je znázorněna zde. Následující příklad kódu ukazuje základní použití `Event.create` vytvoření události a aktivaci metody, přidání dvou ovladačů událostí ve formě výrazu lambda a poté aktivovat události a obou výrazů lambda.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3603.fs)]

Výstup předchozího kódu vypadá takto.

```
Event occurred.
Given a value: Event occurred.
```

## <a name="processing-event-streams"></a>Zpracování datových proudů události

Namísto pouhého přidání obslužné rutiny události pro událost pomocí [Event.add](https://msdn.microsoft.com/library/10670d3b-8d47-4f6e-b8df-ebc6f64ef4fd) funkce, je možné použít funkce v `Event` modul pro zpracování datových proudů událostí velmi individuálním způsobem. Chcete-li to provést, použijte svislou (`|>`) spolu s událostí jako první hodnotu v řadě volání funkcí a `Event` funkce modulu jako následující volání funkce.

Následující příklad kódu ukazuje, jak lze nastavit událost, pro kterou je ovladač událostí volán pouze za určitých podmínek.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3604.fs)]

[Observable – modul](https://msdn.microsoft.com/library/16b8610b-b30a-4df7-aa99-d9d352276227) obsahuje obdobné funkce, které obsluhují Pozorovatelný objekt. Pozorovatelné objekty jsou podobné událostem, aktivně se však k událostem přihlašují pouze tehdy, jsou-li samy přihlašovány.

## <a name="implementing-an-interface-event"></a>Implementace události rozhraní

Při vývoji součástí uživatelského rozhraní začínáte často tak, že vytvoříte nový formulář nebo nový ovládací prvek, který se dědí z existujícího formuláře nebo ovládacího prvku. Události jsou často definovány v rozhraní. V takovém případě pak musíte implementovat rozhraní za účelem implementace události. `System.ComponentModel.INotifyPropertyChanged` Rozhraní definuje jedinou `System.ComponentModel.INotifyPropertyChanged.PropertyChanged` událostí. Následující kód znázorňuje způsob implementace události, kterou toto zděděné rozhraní definuje:

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
        this.Click |> Event.add(fun evArgs -> this.Property1 <- "text2"
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

Pokud se chcete připojit událost v konstruktoru, kód je o něco složitější, protože spojení události musí být v `then` blokovat dodatečném konstruktoru, jako v následujícím příkladu:

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
        this.Click |> Event.add(fun evArgs -> this.Property1 <- "text2"
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

## <a name="see-also"></a>Viz také:

- [Členové](index.md)
- [Zpracování a generování událostí](../../../../docs/standard/events/index.md)
- [Výrazy lambda: Klíčové slovo `fun`](../functions/lambda-expressions-the-fun-keyword.md)
- [Control.Event – modul](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event-module-%5bfsharp%5d)
- [Control.Event&#60;'T&#62; třídy](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27t%5d-class-%5bfsharp%5d)
- [Control.Event&#60;"Delegáta," Args&#62; třídy](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27delegate%2c%27args%5d-class-%5bfsharp%5d)