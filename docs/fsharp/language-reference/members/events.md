---
title: Události (F#)
description: 'Zjistěte, jak F # události umožňují volání funkce přidružit uživatele akcí, které jsou důležité při programování pro grafické uživatelské rozhraní.'
ms.date: 05/16/2016
ms.openlocfilehash: e90d3abc5b5222f60c4e08539ee40bf83ac70ec7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564758"
---
# <a name="events"></a><span data-ttu-id="f2fc3-103">Události</span><span class="sxs-lookup"><span data-stu-id="f2fc3-103">Events</span></span>

> [!NOTE]
<span data-ttu-id="f2fc3-104">Referenční dokumentace rozhraní API odkazů v tomto článku se dostanete na webu MSDN.</span><span class="sxs-lookup"><span data-stu-id="f2fc3-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="f2fc3-105">Referenční dokumentace rozhraní API docs.microsoft.com není dokončena.</span><span class="sxs-lookup"><span data-stu-id="f2fc3-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="f2fc3-106">Události umožňují přiřadit funkce volání a akce uživatele a jsou důležité pro programování grafického uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f2fc3-106">Events enable you to associate function calls with user actions and are important in GUI programming.</span></span> <span data-ttu-id="f2fc3-107">Události je možné spouštět také pomocí aplikací nebo operačního systému.</span><span class="sxs-lookup"><span data-stu-id="f2fc3-107">Events can also be triggered by your applications or by the operating system.</span></span>

## <a name="handling-events"></a><span data-ttu-id="f2fc3-108">Zpracování událostí</span><span class="sxs-lookup"><span data-stu-id="f2fc3-108">Handling Events</span></span>
<span data-ttu-id="f2fc3-109">Pokud použijete knihovnu grafického uživatelského rozhraní, jako jsou formuláře Windows Forms nebo Windows Presentation Foundation (WPF), je většina kódu v aplikaci spuštěna jako odpověď na události, které byly předdefinovány knihovnou.</span><span class="sxs-lookup"><span data-stu-id="f2fc3-109">When you use a GUI library like Windows Forms or Windows Presentation Foundation (WPF), much of the code in your application runs in response to events that are predefined by the library.</span></span> <span data-ttu-id="f2fc3-110">Tyto předdefinované události jsou členy tříd grafického uživatelského rozhraní, jako jsou formuláře a ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="f2fc3-110">These predefined events are members of GUI classes such as forms and controls.</span></span> <span data-ttu-id="f2fc3-111">Můžete přidat vlastní chování na dříve existující událost, jako je například kliknutí na tlačítko pod položkou s názvem událostí, které vás zajímají konkrétní (například `Click` události `Form` třída) a vyvolání `Add` metoda, jak je znázorněno v následujícím kódu .</span><span class="sxs-lookup"><span data-stu-id="f2fc3-111">You can add custom behavior to a preexisting event, such as a button click, by referencing the specific named event of interest (for example, the `Click` event of the `Form` class) and invoking the `Add` method, as shown in the following code.</span></span> <span data-ttu-id="f2fc3-112">Pokud to z F # interaktivní, vynechejte volání `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)`.</span><span class="sxs-lookup"><span data-stu-id="f2fc3-112">If you run this from F# Interactive, omit the call to `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)`.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3601.fs)]

<span data-ttu-id="f2fc3-113">Typ `Add` je metoda `('a -> unit) -> unit`.</span><span class="sxs-lookup"><span data-stu-id="f2fc3-113">The type of the `Add` method is `('a -> unit) -> unit`.</span></span> <span data-ttu-id="f2fc3-114">Proto obslužná rutina události přijímá jeden parametr, obvykle argumenty událostí a vrátí `unit`.</span><span class="sxs-lookup"><span data-stu-id="f2fc3-114">Therefore, the event handler method takes one parameter, typically the event arguments, and returns `unit`.</span></span> <span data-ttu-id="f2fc3-115">Předchozí příklad znázorňuje ovladač událostí jako výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="f2fc3-115">The previous example shows the event handler as a lambda expression.</span></span> <span data-ttu-id="f2fc3-116">Ovladačem událostí může být také hodnota funkce, jako v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="f2fc3-116">The event handler can also be a function value, as in the following code example.</span></span> <span data-ttu-id="f2fc3-117">Následující příklad kódu znázorňuje také použití parametrů ovladače událostí, který poskytuje informace specifické pro daný typ události.</span><span class="sxs-lookup"><span data-stu-id="f2fc3-117">The following code example also shows the use of the event handler parameters, which provide information specific to the type of event.</span></span> <span data-ttu-id="f2fc3-118">Pro `MouseMove` předá systému událostí, `System.Windows.Forms.MouseEventArgs` objekt, který obsahuje `X` a `Y` pozici ukazatele.</span><span class="sxs-lookup"><span data-stu-id="f2fc3-118">For a `MouseMove` event, the system passes a `System.Windows.Forms.MouseEventArgs` object, which contains the `X` and `Y` position of the pointer.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3602.fs)]
    
## <a name="creating-custom-events"></a><span data-ttu-id="f2fc3-119">Vytváření vlastních událostí</span><span class="sxs-lookup"><span data-stu-id="f2fc3-119">Creating Custom Events</span></span>
<span data-ttu-id="f2fc3-120">F # události jsou reprezentované pomocí F # [událostí](https://msdn.microsoft.com/library/f3b47c8a-4ee5-4ce8-9a72-ad305a17c4b9) třídy, které implementuje [ievent –](https://msdn.microsoft.com/library/8dbca0df-f8a1-40bd-8d50-aa26f6a8b862) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f2fc3-120">F# events are represented by the F# [Event](https://msdn.microsoft.com/library/f3b47c8a-4ee5-4ce8-9a72-ad305a17c4b9) class, which implements the [IEvent](https://msdn.microsoft.com/library/8dbca0df-f8a1-40bd-8d50-aa26f6a8b862) interface.</span></span> <span data-ttu-id="f2fc3-121">`IEvent` je sám rozhraní, které kombinuje funkce dvě jiných rozhraní `System.IObservable<'T>` a [idelegateevent –](https://msdn.microsoft.com/library/3d849465-6b8e-4fc5-b36c-2941d734268a).</span><span class="sxs-lookup"><span data-stu-id="f2fc3-121">`IEvent` is itself an interface that combines the functionality of two other interfaces, `System.IObservable<'T>` and [IDelegateEvent](https://msdn.microsoft.com/library/3d849465-6b8e-4fc5-b36c-2941d734268a).</span></span> <span data-ttu-id="f2fc3-122">Proto `Event`y mají ekvivalentní funkce Delegáti v jiných jazycích, plus další funkce `IObservable`, to znamená, že událostí F # podporu filtrování událostí a pomocí funkce prvotřídní F # a výrazy lambda jako obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="f2fc3-122">Therefore, `Event`s have the equivalent functionality of delegates in other languages, plus the additional functionality from `IObservable`, which means that F# events support event filtering and using F# first-class functions and lambda expressions as event handlers.</span></span> <span data-ttu-id="f2fc3-123">Tato funkce je součástí [událostí modulu](https://msdn.microsoft.com/library/8b883baa-a460-4840-9baa-de8260351bc7).</span><span class="sxs-lookup"><span data-stu-id="f2fc3-123">This functionality is provided in the [Event module](https://msdn.microsoft.com/library/8b883baa-a460-4840-9baa-de8260351bc7).</span></span>

<span data-ttu-id="f2fc3-124">Pokud chcete vytvořit událost na třídu, která funguje stejně jako všechny ostatní události rozhraní .NET Framework, přidejte do třídy `let` vazby, která definuje `Event` jako pole v třídě.</span><span class="sxs-lookup"><span data-stu-id="f2fc3-124">To create an event on a class that acts just like any other .NET Framework event, add to the class a `let` binding that defines an `Event` as a field in a class.</span></span> <span data-ttu-id="f2fc3-125">Můžete zadat požadovaný typ argumentu události jako typ argumentu, nebo jej ponechat prázdný a odvodit odpovídající typ pomocí kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="f2fc3-125">You can specify the desired event argument type as the type argument, or leave it blank and have the compiler infer the appropriate type.</span></span> <span data-ttu-id="f2fc3-126">Musíte také definovat člen události, který zpřístupňuje událost jako událost typu CLI.</span><span class="sxs-lookup"><span data-stu-id="f2fc3-126">You also must define an event member that exposes the event as a CLI event.</span></span> <span data-ttu-id="f2fc3-127">Tento člen musí mít [clievent –](https://msdn.microsoft.com/library/d359f1dd-ffa5-42fb-8808-b4c8131a0333) atribut.</span><span class="sxs-lookup"><span data-stu-id="f2fc3-127">This member should have the [CLIEvent](https://msdn.microsoft.com/library/d359f1dd-ffa5-42fb-8808-b4c8131a0333) attribute.</span></span> <span data-ttu-id="f2fc3-128">Je deklarován jako vlastnost a její implementace je právě volání [publikovat](https://msdn.microsoft.com/library/b0fdaad5-25e5-43d0-9c0c-ce37c4aeb68e) vlastnosti události.</span><span class="sxs-lookup"><span data-stu-id="f2fc3-128">It is declared like a property and its implementation is just a call to the [Publish](https://msdn.microsoft.com/library/b0fdaad5-25e5-43d0-9c0c-ce37c4aeb68e) property of the event.</span></span> <span data-ttu-id="f2fc3-129">Uživatelé vaší třídy mohou používat `Add` metody publikovanou události pro přidání obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="f2fc3-129">Users of your class can use the `Add` method of the published event to add a handler.</span></span> <span data-ttu-id="f2fc3-130">Argument pro `Add` metoda může být výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="f2fc3-130">The argument for the `Add` method can be a lambda expression.</span></span> <span data-ttu-id="f2fc3-131">Můžete použít `Trigger` vlastnost události k vyvolání události, předání argumentů obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="f2fc3-131">You can use the `Trigger` property of the event to raise the event, passing the arguments to the handler function.</span></span> <span data-ttu-id="f2fc3-132">Následující příklad kódu to dokládá.</span><span class="sxs-lookup"><span data-stu-id="f2fc3-132">The following code example illustrates this.</span></span> <span data-ttu-id="f2fc3-133">V tomto příkladu je odvozeným argumentem typu události řazená kolekce, která představuje argumenty pro výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="f2fc3-133">In this example, the inferred type argument for the event is a tuple, which represents the arguments for the lambda expression.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3605.fs)]

<span data-ttu-id="f2fc3-134">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="f2fc3-134">The output is as follows.</span></span>

```
Event1 occurred! Object data: Hello World!
```

<span data-ttu-id="f2fc3-135">Další funkce poskytované službou `Event` je zde znázorněný modulu.</span><span class="sxs-lookup"><span data-stu-id="f2fc3-135">The additional functionality provided by the `Event` module is illustrated here.</span></span> <span data-ttu-id="f2fc3-136">Následující příklad kódu ukazuje základní použití `Event.create` Chcete-li vytvořit událost a metoda aktivační událost, přidejte dvě obslužné rutiny událostí ve formě lambda – výrazy a poté aktivuje událost provést oba výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="f2fc3-136">The following code example illustrates the basic use of `Event.create` to create an event and a trigger method, add two event handlers in the form of lambda expressions, and then trigger the event to execute both lambda expressions.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3603.fs)]

<span data-ttu-id="f2fc3-137">Výstup předchozího kódu vypadá takto.</span><span class="sxs-lookup"><span data-stu-id="f2fc3-137">The output of the previous code is as follows.</span></span>

```
Event occurred.
Given a value: Event occurred.
```

## <a name="processing-event-streams"></a><span data-ttu-id="f2fc3-138">Zpracování datových proudů události</span><span class="sxs-lookup"><span data-stu-id="f2fc3-138">Processing Event Streams</span></span>
<span data-ttu-id="f2fc3-139">Místo právě přidání obslužné rutiny události pro událost pomocí [Event.add](https://msdn.microsoft.com/library/10670d3b-8d47-4f6e-b8df-ebc6f64ef4fd) funkce, můžete použít funkce v `Event` modulu do procesu datových proudů událostí vysokou přizpůsobené způsoby.</span><span class="sxs-lookup"><span data-stu-id="f2fc3-139">Instead of just adding an event handler for an event by using the [Event.add](https://msdn.microsoft.com/library/10670d3b-8d47-4f6e-b8df-ebc6f64ef4fd) function, you can use the functions in the `Event` module to process streams of events in highly customized ways.</span></span> <span data-ttu-id="f2fc3-140">K tomuto účelu použijete dopředného kanálu (`|>`) společně s událostí jako první hodnotu v řadě volání funkce a `Event` modul funguje jako volání dalších funkcí.</span><span class="sxs-lookup"><span data-stu-id="f2fc3-140">To do this, you use the forward pipe (`|>`) together with the event as the first value in a series of function calls, and the `Event` module functions as subsequent function calls.</span></span>

<span data-ttu-id="f2fc3-141">Následující příklad kódu ukazuje, jak lze nastavit událost, pro kterou je ovladač událostí volán pouze za určitých podmínek.</span><span class="sxs-lookup"><span data-stu-id="f2fc3-141">The following code example shows how to set up an event for which the handler is only called under certain conditions.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3604.fs)]

<span data-ttu-id="f2fc3-142">[Observable – modul](https://msdn.microsoft.com/library/16b8610b-b30a-4df7-aa99-d9d352276227) obsahuje podobné funkce, které působí na pozorovatelné objekty.</span><span class="sxs-lookup"><span data-stu-id="f2fc3-142">The [Observable module](https://msdn.microsoft.com/library/16b8610b-b30a-4df7-aa99-d9d352276227) contains similar functions that operate on observable objects.</span></span> <span data-ttu-id="f2fc3-143">Pozorovatelné objekty jsou podobné událostem, aktivně se však k událostem přihlašují pouze tehdy, jsou-li samy přihlašovány.</span><span class="sxs-lookup"><span data-stu-id="f2fc3-143">Observable objects are similar to events but only actively subscribe to events if they themselves are being subscribed to.</span></span>


## <a name="implementing-an-interface-event"></a><span data-ttu-id="f2fc3-144">Implementace události rozhraní</span><span class="sxs-lookup"><span data-stu-id="f2fc3-144">Implementing an Interface Event</span></span>
<span data-ttu-id="f2fc3-145">Při vývoji součástí uživatelského rozhraní začínáte často tak, že vytvoříte nový formulář nebo nový ovládací prvek, který se dědí z existujícího formuláře nebo ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f2fc3-145">As you develop UI components, you often start by creating a new form or a new control that inherits from an existing form or control.</span></span> <span data-ttu-id="f2fc3-146">Události jsou často definovány v rozhraní. V takovém případě pak musíte implementovat rozhraní za účelem implementace události.</span><span class="sxs-lookup"><span data-stu-id="f2fc3-146">Events are frequently defined on an interface, and, in that case, you must implement the interface to implement the event.</span></span> <span data-ttu-id="f2fc3-147">`System.ComponentModel.INotifyPropertyChanged` Rozhraní definuje jeden `System.ComponentModel.INotifyPropertyChanged.PropertyChanged` událostí.</span><span class="sxs-lookup"><span data-stu-id="f2fc3-147">The `System.ComponentModel.INotifyPropertyChanged` interface defines a single `System.ComponentModel.INotifyPropertyChanged.PropertyChanged` event.</span></span> <span data-ttu-id="f2fc3-148">Následující kód znázorňuje způsob implementace události, kterou toto zděděné rozhraní definuje:</span><span class="sxs-lookup"><span data-stu-id="f2fc3-148">The following code illustrates how to implement the event that this inherited interface defined:</span></span>

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

<span data-ttu-id="f2fc3-149">Pokud chcete spojit události v konstruktoru, kód je trochu složitější, protože spojení události musí být v `then` blokovat v další konstruktoru, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f2fc3-149">If you want to hook up the event in the constructor, the code is a bit more complicated because the event hookup must be in a `then` block in an additional constructor, as in the following example:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f2fc3-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2fc3-150">See Also</span></span>
[<span data-ttu-id="f2fc3-151">Členové</span><span class="sxs-lookup"><span data-stu-id="f2fc3-151">Members</span></span>](index.md)

[<span data-ttu-id="f2fc3-152">Zpracování a generování událostí</span><span class="sxs-lookup"><span data-stu-id="f2fc3-152">Handling and Raising Events</span></span>](../../../../docs/standard/events/index.md)

[<span data-ttu-id="f2fc3-153">Výrazy lambda: `fun` – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="f2fc3-153">Lambda Expressions: The `fun` Keyword</span></span>](../functions/lambda-expressions-the-fun-keyword.md)

[<span data-ttu-id="f2fc3-154">Control.Event – modul</span><span class="sxs-lookup"><span data-stu-id="f2fc3-154">Control.Event Module</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event-module-%5bfsharp%5d)

[<span data-ttu-id="f2fc3-155">Control.Event –&#60;'T&#62; – třída</span><span class="sxs-lookup"><span data-stu-id="f2fc3-155">Control.Event&#60;'T&#62; Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27t%5d-class-%5bfsharp%5d)

[<span data-ttu-id="f2fc3-156">Control.Event –&#60;'Delegáta,' argumentů&#62; – třída</span><span class="sxs-lookup"><span data-stu-id="f2fc3-156">Control.Event&#60;'Delegate,'Args&#62; Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27delegate%2c%27args%5d-class-%5bfsharp%5d)
