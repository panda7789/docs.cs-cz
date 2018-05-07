---
title: Události (F#)
description: 'Zjistěte, jak F # události umožňují volání funkce přidružit uživatele akcí, které jsou důležité při programování pro grafické uživatelské rozhraní.'
ms.date: 05/16/2016
ms.openlocfilehash: e90d3abc5b5222f60c4e08539ee40bf83ac70ec7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="events"></a>Události

> [!NOTE]
Referenční dokumentace rozhraní API odkazů v tomto článku se dostanete na webu MSDN.  Referenční dokumentace rozhraní API docs.microsoft.com není dokončena.

Události umožňují přiřadit funkce volání a akce uživatele a jsou důležité pro programování grafického uživatelského rozhraní. Události je možné spouštět také pomocí aplikací nebo operačního systému.

## <a name="handling-events"></a>Zpracování událostí
Pokud použijete knihovnu grafického uživatelského rozhraní, jako jsou formuláře Windows Forms nebo Windows Presentation Foundation (WPF), je většina kódu v aplikaci spuštěna jako odpověď na události, které byly předdefinovány knihovnou. Tyto předdefinované události jsou členy tříd grafického uživatelského rozhraní, jako jsou formuláře a ovládací prvky. Můžete přidat vlastní chování na dříve existující událost, jako je například kliknutí na tlačítko pod položkou s názvem událostí, které vás zajímají konkrétní (například `Click` události `Form` třída) a vyvolání `Add` metoda, jak je znázorněno v následujícím kódu . Pokud to z F # interaktivní, vynechejte volání `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)`.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3601.fs)]

Typ `Add` je metoda `('a -> unit) -> unit`. Proto obslužná rutina události přijímá jeden parametr, obvykle argumenty událostí a vrátí `unit`. Předchozí příklad znázorňuje ovladač událostí jako výraz lambda. Ovladačem událostí může být také hodnota funkce, jako v následujícím příkladu kódu. Následující příklad kódu znázorňuje také použití parametrů ovladače událostí, který poskytuje informace specifické pro daný typ události. Pro `MouseMove` předá systému událostí, `System.Windows.Forms.MouseEventArgs` objekt, který obsahuje `X` a `Y` pozici ukazatele.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3602.fs)]
    
## <a name="creating-custom-events"></a>Vytváření vlastních událostí
F # události jsou reprezentované pomocí F # [událostí](https://msdn.microsoft.com/library/f3b47c8a-4ee5-4ce8-9a72-ad305a17c4b9) třídy, které implementuje [ievent –](https://msdn.microsoft.com/library/8dbca0df-f8a1-40bd-8d50-aa26f6a8b862) rozhraní. `IEvent` je sám rozhraní, které kombinuje funkce dvě jiných rozhraní `System.IObservable<'T>` a [idelegateevent –](https://msdn.microsoft.com/library/3d849465-6b8e-4fc5-b36c-2941d734268a). Proto `Event`y mají ekvivalentní funkce Delegáti v jiných jazycích, plus další funkce `IObservable`, to znamená, že událostí F # podporu filtrování událostí a pomocí funkce prvotřídní F # a výrazy lambda jako obslužné rutiny událostí. Tato funkce je součástí [událostí modulu](https://msdn.microsoft.com/library/8b883baa-a460-4840-9baa-de8260351bc7).

Pokud chcete vytvořit událost na třídu, která funguje stejně jako všechny ostatní události rozhraní .NET Framework, přidejte do třídy `let` vazby, která definuje `Event` jako pole v třídě. Můžete zadat požadovaný typ argumentu události jako typ argumentu, nebo jej ponechat prázdný a odvodit odpovídající typ pomocí kompilátoru. Musíte také definovat člen události, který zpřístupňuje událost jako událost typu CLI. Tento člen musí mít [clievent –](https://msdn.microsoft.com/library/d359f1dd-ffa5-42fb-8808-b4c8131a0333) atribut. Je deklarován jako vlastnost a její implementace je právě volání [publikovat](https://msdn.microsoft.com/library/b0fdaad5-25e5-43d0-9c0c-ce37c4aeb68e) vlastnosti události. Uživatelé vaší třídy mohou používat `Add` metody publikovanou události pro přidání obslužné rutiny. Argument pro `Add` metoda může být výraz lambda. Můžete použít `Trigger` vlastnost události k vyvolání události, předání argumentů obslužné rutiny. Následující příklad kódu to dokládá. V tomto příkladu je odvozeným argumentem typu události řazená kolekce, která představuje argumenty pro výraz lambda.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3605.fs)]

Výstup je následující.

```
Event1 occurred! Object data: Hello World!
```

Další funkce poskytované službou `Event` je zde znázorněný modulu. Následující příklad kódu ukazuje základní použití `Event.create` Chcete-li vytvořit událost a metoda aktivační událost, přidejte dvě obslužné rutiny událostí ve formě lambda – výrazy a poté aktivuje událost provést oba výrazy lambda.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3603.fs)]

Výstup předchozího kódu vypadá takto.

```
Event occurred.
Given a value: Event occurred.
```

## <a name="processing-event-streams"></a>Zpracování datových proudů události
Místo právě přidání obslužné rutiny události pro událost pomocí [Event.add](https://msdn.microsoft.com/library/10670d3b-8d47-4f6e-b8df-ebc6f64ef4fd) funkce, můžete použít funkce v `Event` modulu do procesu datových proudů událostí vysokou přizpůsobené způsoby. K tomuto účelu použijete dopředného kanálu (`|>`) společně s událostí jako první hodnotu v řadě volání funkce a `Event` modul funguje jako volání dalších funkcí.

Následující příklad kódu ukazuje, jak lze nastavit událost, pro kterou je ovladač událostí volán pouze za určitých podmínek.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3604.fs)]

[Observable – modul](https://msdn.microsoft.com/library/16b8610b-b30a-4df7-aa99-d9d352276227) obsahuje podobné funkce, které působí na pozorovatelné objekty. Pozorovatelné objekty jsou podobné událostem, aktivně se však k událostem přihlašují pouze tehdy, jsou-li samy přihlašovány.


## <a name="implementing-an-interface-event"></a>Implementace události rozhraní
Při vývoji součástí uživatelského rozhraní začínáte často tak, že vytvoříte nový formulář nebo nový ovládací prvek, který se dědí z existujícího formuláře nebo ovládacího prvku. Události jsou často definovány v rozhraní. V takovém případě pak musíte implementovat rozhraní za účelem implementace události. `System.ComponentModel.INotifyPropertyChanged` Rozhraní definuje jeden `System.ComponentModel.INotifyPropertyChanged.PropertyChanged` událostí. Následující kód znázorňuje způsob implementace události, kterou toto zděděné rozhraní definuje:

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

Pokud chcete spojit události v konstruktoru, kód je trochu složitější, protože spojení události musí být v `then` blokovat v další konstruktoru, jako v následujícím příkladu:

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

## <a name="see-also"></a>Viz také
[Členové](index.md)

[Zpracování a generování událostí](../../../../docs/standard/events/index.md)

[Výrazy lambda: `fun` – klíčové slovo](../functions/lambda-expressions-the-fun-keyword.md)

[Control.Event – modul](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event-module-%5bfsharp%5d)

[Control.Event –&#60;'T&#62; – třída](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27t%5d-class-%5bfsharp%5d)

[Control.Event –&#60;'Delegáta,' argumentů&#62; – třída](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27delegate%2c%27args%5d-class-%5bfsharp%5d)
