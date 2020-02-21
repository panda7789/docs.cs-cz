---
title: Události
description: Zjistěte, F# jak události umožňují přidružit volání funkcí k akcím uživatele, které jsou důležité při programování v grafickém uživatelském rozhraní.
ms.date: 05/16/2016
ms.openlocfilehash: ad60aff318832ab3ba5e9f7c43928898e171cea8
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543622"
---
# <a name="events"></a><span data-ttu-id="df74d-103">Události</span><span class="sxs-lookup"><span data-stu-id="df74d-103">Events</span></span>

> [!NOTE]
> <span data-ttu-id="df74d-104">Odkazy na reference k rozhraní API v tomto článku vás převezmou na MSDN.</span><span class="sxs-lookup"><span data-stu-id="df74d-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="df74d-105">Reference k rozhraní docs.microsoft.com API není dokončená.</span><span class="sxs-lookup"><span data-stu-id="df74d-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="df74d-106">Události umožňují přiřadit funkce volání a akce uživatele a jsou důležité pro programování grafického uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="df74d-106">Events enable you to associate function calls with user actions and are important in GUI programming.</span></span> <span data-ttu-id="df74d-107">Události je možné spouštět také pomocí aplikací nebo operačního systému.</span><span class="sxs-lookup"><span data-stu-id="df74d-107">Events can also be triggered by your applications or by the operating system.</span></span>

## <a name="handling-events"></a><span data-ttu-id="df74d-108">Zpracování událostí</span><span class="sxs-lookup"><span data-stu-id="df74d-108">Handling Events</span></span>

<span data-ttu-id="df74d-109">Pokud použijete knihovnu grafického uživatelského rozhraní, jako jsou formuláře Windows Forms nebo Windows Presentation Foundation (WPF), je většina kódu v aplikaci spuštěna jako odpověď na události, které byly předdefinovány knihovnou.</span><span class="sxs-lookup"><span data-stu-id="df74d-109">When you use a GUI library like Windows Forms or Windows Presentation Foundation (WPF), much of the code in your application runs in response to events that are predefined by the library.</span></span> <span data-ttu-id="df74d-110">Tyto předdefinované události jsou členy tříd grafického uživatelského rozhraní, jako jsou formuláře a ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="df74d-110">These predefined events are members of GUI classes such as forms and controls.</span></span> <span data-ttu-id="df74d-111">Můžete přidat vlastní chování k již existující události, jako je například kliknutí na tlačítko, odkazem na konkrétní pojmenovanou událost zájmu (například `Click` událost `Form` třídy) a voláním metody `Add`, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="df74d-111">You can add custom behavior to a preexisting event, such as a button click, by referencing the specific named event of interest (for example, the `Click` event of the `Form` class) and invoking the `Add` method, as shown in the following code.</span></span> <span data-ttu-id="df74d-112">Pokud spustíte tento příkaz z F# interaktivního, vynechejte volání `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)`.</span><span class="sxs-lookup"><span data-stu-id="df74d-112">If you run this from F# Interactive, omit the call to `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3601.fs)]

<span data-ttu-id="df74d-113">Typ metody `Add` je `('a -> unit) -> unit`.</span><span class="sxs-lookup"><span data-stu-id="df74d-113">The type of the `Add` method is `('a -> unit) -> unit`.</span></span> <span data-ttu-id="df74d-114">Proto metoda obslužné rutiny události přijímá jeden parametr, obvykle argumenty události a vrací `unit`.</span><span class="sxs-lookup"><span data-stu-id="df74d-114">Therefore, the event handler method takes one parameter, typically the event arguments, and returns `unit`.</span></span> <span data-ttu-id="df74d-115">Předchozí příklad znázorňuje ovladač událostí jako výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="df74d-115">The previous example shows the event handler as a lambda expression.</span></span> <span data-ttu-id="df74d-116">Ovladačem událostí může být také hodnota funkce, jako v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="df74d-116">The event handler can also be a function value, as in the following code example.</span></span> <span data-ttu-id="df74d-117">Následující příklad kódu znázorňuje také použití parametrů ovladače událostí, který poskytuje informace specifické pro daný typ události.</span><span class="sxs-lookup"><span data-stu-id="df74d-117">The following code example also shows the use of the event handler parameters, which provide information specific to the type of event.</span></span> <span data-ttu-id="df74d-118">Pro událost `MouseMove` předává systém objekt `System.Windows.Forms.MouseEventArgs`, který obsahuje `X` a `Y` pozici ukazatele.</span><span class="sxs-lookup"><span data-stu-id="df74d-118">For a `MouseMove` event, the system passes a `System.Windows.Forms.MouseEventArgs` object, which contains the `X` and `Y` position of the pointer.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3602.fs)]

## <a name="creating-custom-events"></a><span data-ttu-id="df74d-119">Vytváření vlastních událostí</span><span class="sxs-lookup"><span data-stu-id="df74d-119">Creating Custom Events</span></span>

<span data-ttu-id="df74d-120">F#události jsou reprezentovány F# třídou [Event](https://msdn.microsoft.com/library/f3b47c8a-4ee5-4ce8-9a72-ad305a17c4b9) , která implementuje rozhraní [IEvent](https://msdn.microsoft.com/library/8dbca0df-f8a1-40bd-8d50-aa26f6a8b862) .</span><span class="sxs-lookup"><span data-stu-id="df74d-120">F# events are represented by the F# [Event](https://msdn.microsoft.com/library/f3b47c8a-4ee5-4ce8-9a72-ad305a17c4b9) class, which implements the [IEvent](https://msdn.microsoft.com/library/8dbca0df-f8a1-40bd-8d50-aa26f6a8b862) interface.</span></span> <span data-ttu-id="df74d-121">`IEvent` je toto rozhraní, které kombinuje funkce dvou dalších rozhraní, `System.IObservable<'T>` a [IDelegateEvent](https://msdn.microsoft.com/library/3d849465-6b8e-4fc5-b36c-2941d734268a).</span><span class="sxs-lookup"><span data-stu-id="df74d-121">`IEvent` is itself an interface that combines the functionality of two other interfaces, `System.IObservable<'T>` and [IDelegateEvent](https://msdn.microsoft.com/library/3d849465-6b8e-4fc5-b36c-2941d734268a).</span></span> <span data-ttu-id="df74d-122">Proto `Event`s mají ekvivalentní funkce delegátů v jiných jazycích a další funkce z `IObservable`, což znamená, že F# události podporují filtrování událostí a používají F# funkce první třídy a lambda výrazy jako obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="df74d-122">Therefore, `Event`s have the equivalent functionality of delegates in other languages, plus the additional functionality from `IObservable`, which means that F# events support event filtering and using F# first-class functions and lambda expressions as event handlers.</span></span> <span data-ttu-id="df74d-123">Tato funkce je k dispozici v [modulu Event](https://msdn.microsoft.com/library/8b883baa-a460-4840-9baa-de8260351bc7).</span><span class="sxs-lookup"><span data-stu-id="df74d-123">This functionality is provided in the [Event module](https://msdn.microsoft.com/library/8b883baa-a460-4840-9baa-de8260351bc7).</span></span>

<span data-ttu-id="df74d-124">Chcete-li vytvořit událost pro třídu, která funguje stejně jako jakákoli jiná událost .NET Framework, přidejte do třídy `let` vazby definující `Event` jako pole ve třídě.</span><span class="sxs-lookup"><span data-stu-id="df74d-124">To create an event on a class that acts just like any other .NET Framework event, add to the class a `let` binding that defines an `Event` as a field in a class.</span></span> <span data-ttu-id="df74d-125">Můžete zadat požadovaný typ argumentu události jako typ argumentu, nebo jej ponechat prázdný a odvodit odpovídající typ pomocí kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="df74d-125">You can specify the desired event argument type as the type argument, or leave it blank and have the compiler infer the appropriate type.</span></span> <span data-ttu-id="df74d-126">Musíte také definovat člen události, který zpřístupňuje událost jako událost typu CLI.</span><span class="sxs-lookup"><span data-stu-id="df74d-126">You also must define an event member that exposes the event as a CLI event.</span></span> <span data-ttu-id="df74d-127">Tento člen by měl mít atribut [CLIEvent](https://msdn.microsoft.com/library/d359f1dd-ffa5-42fb-8808-b4c8131a0333) .</span><span class="sxs-lookup"><span data-stu-id="df74d-127">This member should have the [CLIEvent](https://msdn.microsoft.com/library/d359f1dd-ffa5-42fb-8808-b4c8131a0333) attribute.</span></span> <span data-ttu-id="df74d-128">Je deklarován jako vlastnost a její implementace je pouze voláním vlastnosti [publikovat](https://msdn.microsoft.com/library/b0fdaad5-25e5-43d0-9c0c-ce37c4aeb68e) události.</span><span class="sxs-lookup"><span data-stu-id="df74d-128">It is declared like a property and its implementation is just a call to the [Publish](https://msdn.microsoft.com/library/b0fdaad5-25e5-43d0-9c0c-ce37c4aeb68e) property of the event.</span></span> <span data-ttu-id="df74d-129">Uživatelé vaší třídy mohou použít metodu `Add` publikované události pro přidání obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="df74d-129">Users of your class can use the `Add` method of the published event to add a handler.</span></span> <span data-ttu-id="df74d-130">Argumentem metody `Add` může být výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="df74d-130">The argument for the `Add` method can be a lambda expression.</span></span> <span data-ttu-id="df74d-131">Můžete použít vlastnost `Trigger` události k vyvolání události a předání argumentů funkci obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="df74d-131">You can use the `Trigger` property of the event to raise the event, passing the arguments to the handler function.</span></span> <span data-ttu-id="df74d-132">Následující příklad kódu to dokládá.</span><span class="sxs-lookup"><span data-stu-id="df74d-132">The following code example illustrates this.</span></span> <span data-ttu-id="df74d-133">V tomto příkladu je odvozeným argumentem typu události řazená kolekce, která představuje argumenty pro výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="df74d-133">In this example, the inferred type argument for the event is a tuple, which represents the arguments for the lambda expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3605.fs)]

<span data-ttu-id="df74d-134">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="df74d-134">The output is as follows.</span></span>

```console
Event1 occurred! Object data: Hello World!
```

<span data-ttu-id="df74d-135">Další funkce, které poskytuje modul `Event`, jsou znázorněny zde.</span><span class="sxs-lookup"><span data-stu-id="df74d-135">The additional functionality provided by the `Event` module is illustrated here.</span></span> <span data-ttu-id="df74d-136">Následující příklad kódu ukazuje základní použití `Event.create` k vytvoření události a metody triggeru, přidání dvou obslužných rutin událostí ve formě výrazů lambda a následnou aktivací události pro provedení obou výrazů lambda.</span><span class="sxs-lookup"><span data-stu-id="df74d-136">The following code example illustrates the basic use of `Event.create` to create an event and a trigger method, add two event handlers in the form of lambda expressions, and then trigger the event to execute both lambda expressions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3603.fs)]

<span data-ttu-id="df74d-137">Výstup předchozího kódu vypadá takto.</span><span class="sxs-lookup"><span data-stu-id="df74d-137">The output of the previous code is as follows.</span></span>

```console
Event occurred.
Given a value: Event occurred.
```

## <a name="processing-event-streams"></a><span data-ttu-id="df74d-138">Zpracování datových proudů události</span><span class="sxs-lookup"><span data-stu-id="df74d-138">Processing Event Streams</span></span>

<span data-ttu-id="df74d-139">Místo pouhého přidání obslužné rutiny události pro událost pomocí funkce [Event. Add](https://msdn.microsoft.com/library/10670d3b-8d47-4f6e-b8df-ebc6f64ef4fd) můžete použít funkce v modulu `Event` ke zpracování proudů událostí v vysoce přizpůsobených způsobech.</span><span class="sxs-lookup"><span data-stu-id="df74d-139">Instead of just adding an event handler for an event by using the [Event.add](https://msdn.microsoft.com/library/10670d3b-8d47-4f6e-b8df-ebc6f64ef4fd) function, you can use the functions in the `Event` module to process streams of events in highly customized ways.</span></span> <span data-ttu-id="df74d-140">Chcete-li to provést, použijte přesměrování přesměrování (`|>`) spolu s událostí jako první hodnotu v řadě volání funkce a modul `Event` funguje jako následné volání funkcí.</span><span class="sxs-lookup"><span data-stu-id="df74d-140">To do this, you use the forward pipe (`|>`) together with the event as the first value in a series of function calls, and the `Event` module functions as subsequent function calls.</span></span>

<span data-ttu-id="df74d-141">Následující příklad kódu ukazuje, jak lze nastavit událost, pro kterou je ovladač událostí volán pouze za určitých podmínek.</span><span class="sxs-lookup"><span data-stu-id="df74d-141">The following code example shows how to set up an event for which the handler is only called under certain conditions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3604.fs)]

<span data-ttu-id="df74d-142">[Pozorovatelný modul](https://msdn.microsoft.com/library/16b8610b-b30a-4df7-aa99-d9d352276227) obsahuje podobné funkce, které fungují na pozorovatelných objektech.</span><span class="sxs-lookup"><span data-stu-id="df74d-142">The [Observable module](https://msdn.microsoft.com/library/16b8610b-b30a-4df7-aa99-d9d352276227) contains similar functions that operate on observable objects.</span></span> <span data-ttu-id="df74d-143">Pozorovatelné objekty jsou podobné událostem, aktivně se však k událostem přihlašují pouze tehdy, jsou-li samy přihlašovány.</span><span class="sxs-lookup"><span data-stu-id="df74d-143">Observable objects are similar to events but only actively subscribe to events if they themselves are being subscribed to.</span></span>

## <a name="implementing-an-interface-event"></a><span data-ttu-id="df74d-144">Implementace události rozhraní</span><span class="sxs-lookup"><span data-stu-id="df74d-144">Implementing an Interface Event</span></span>

<span data-ttu-id="df74d-145">Při vývoji součástí uživatelského rozhraní začínáte často tak, že vytvoříte nový formulář nebo nový ovládací prvek, který se dědí z existujícího formuláře nebo ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="df74d-145">As you develop UI components, you often start by creating a new form or a new control that inherits from an existing form or control.</span></span> <span data-ttu-id="df74d-146">Události jsou často definovány v rozhraní. V takovém případě pak musíte implementovat rozhraní za účelem implementace události.</span><span class="sxs-lookup"><span data-stu-id="df74d-146">Events are frequently defined on an interface, and, in that case, you must implement the interface to implement the event.</span></span> <span data-ttu-id="df74d-147">Rozhraní `System.ComponentModel.INotifyPropertyChanged` definuje jednu událost `System.ComponentModel.INotifyPropertyChanged.PropertyChanged`.</span><span class="sxs-lookup"><span data-stu-id="df74d-147">The `System.ComponentModel.INotifyPropertyChanged` interface defines a single `System.ComponentModel.INotifyPropertyChanged.PropertyChanged` event.</span></span> <span data-ttu-id="df74d-148">Následující kód znázorňuje způsob implementace události, kterou toto zděděné rozhraní definuje:</span><span class="sxs-lookup"><span data-stu-id="df74d-148">The following code illustrates how to implement the event that this inherited interface defined:</span></span>

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

<span data-ttu-id="df74d-149">Pokud chcete připojit událost v konstruktoru, je kód trochu složitější, protože Event propojení musí být v dalším konstruktoru `then` bloku, jak je uvedeno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="df74d-149">If you want to hook up the event in the constructor, the code is a bit more complicated because the event hookup must be in a `then` block in an additional constructor, as in the following example:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="df74d-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="df74d-150">See also</span></span>

- [<span data-ttu-id="df74d-151">Členové</span><span class="sxs-lookup"><span data-stu-id="df74d-151">Members</span></span>](index.md)
- [<span data-ttu-id="df74d-152">Zpracování a vyvolávání událostí</span><span class="sxs-lookup"><span data-stu-id="df74d-152">Handling and Raising Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="df74d-153">Výrazy lambda: klíčové slovo `fun`</span><span class="sxs-lookup"><span data-stu-id="df74d-153">Lambda Expressions: The `fun` Keyword</span></span>](../functions/lambda-expressions-the-fun-keyword.md)
- [<span data-ttu-id="df74d-154">Control. Event – modul</span><span class="sxs-lookup"><span data-stu-id="df74d-154">Control.Event Module</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event-module-%5bfsharp%5d)
- [<span data-ttu-id="df74d-155">Control. Event&#60;–&#62; třída</span><span class="sxs-lookup"><span data-stu-id="df74d-155">Control.Event&#60;'T&#62; Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27t%5d-class-%5bfsharp%5d)
- [<span data-ttu-id="df74d-156">Control. Event&#60;' Delegate; ' args&#62; Class</span><span class="sxs-lookup"><span data-stu-id="df74d-156">Control.Event&#60;'Delegate,'Args&#62; Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27delegate%2c%27args%5d-class-%5bfsharp%5d)
