---
title: Události
description: 'Přečtěte si, jak události F # umožňují přidružit volání funkcí k akcím uživatele, které jsou důležité při programování v grafickém uživatelském rozhraní.'
ms.date: 08/15/2020
ms.openlocfilehash: 42783255412d56c6ff6729694c31d0868ed99633
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559190"
---
# <a name="events"></a><span data-ttu-id="cc2e7-103">Události</span><span class="sxs-lookup"><span data-stu-id="cc2e7-103">Events</span></span>

<span data-ttu-id="cc2e7-104">Události umožňují přiřadit funkce volání a akce uživatele a jsou důležité pro programování grafického uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cc2e7-104">Events enable you to associate function calls with user actions and are important in GUI programming.</span></span> <span data-ttu-id="cc2e7-105">Události je možné spouštět také pomocí aplikací nebo operačního systému.</span><span class="sxs-lookup"><span data-stu-id="cc2e7-105">Events can also be triggered by your applications or by the operating system.</span></span>

## <a name="handling-events"></a><span data-ttu-id="cc2e7-106">Zpracování událostí</span><span class="sxs-lookup"><span data-stu-id="cc2e7-106">Handling Events</span></span>

<span data-ttu-id="cc2e7-107">Pokud použijete knihovnu grafického uživatelského rozhraní, jako jsou formuláře Windows Forms nebo Windows Presentation Foundation (WPF), je většina kódu v aplikaci spuštěna jako odpověď na události, které byly předdefinovány knihovnou.</span><span class="sxs-lookup"><span data-stu-id="cc2e7-107">When you use a GUI library like Windows Forms or Windows Presentation Foundation (WPF), much of the code in your application runs in response to events that are predefined by the library.</span></span> <span data-ttu-id="cc2e7-108">Tyto předdefinované události jsou členy tříd grafického uživatelského rozhraní, jako jsou formuláře a ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="cc2e7-108">These predefined events are members of GUI classes such as forms and controls.</span></span> <span data-ttu-id="cc2e7-109">Můžete přidat vlastní chování k již existující události, jako je například kliknutí na tlačítko, odkazem na konkrétní pojmenovanou událost zájmu (například na `Click` událost `Form` třídy) a voláním `Add` metody, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="cc2e7-109">You can add custom behavior to a preexisting event, such as a button click, by referencing the specific named event of interest (for example, the `Click` event of the `Form` class) and invoking the `Add` method, as shown in the following code.</span></span> <span data-ttu-id="cc2e7-110">Pokud spustíte tento příkaz z F# Interactive, vynechejte volání `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)` .</span><span class="sxs-lookup"><span data-stu-id="cc2e7-110">If you run this from F# Interactive, omit the call to `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3601.fs)]

<span data-ttu-id="cc2e7-111">Typ `Add` metody je `('a -> unit) -> unit` .</span><span class="sxs-lookup"><span data-stu-id="cc2e7-111">The type of the `Add` method is `('a -> unit) -> unit`.</span></span> <span data-ttu-id="cc2e7-112">Proto metoda obslužné rutiny události přijímá jeden parametr, obvykle argumenty události a vrací `unit` .</span><span class="sxs-lookup"><span data-stu-id="cc2e7-112">Therefore, the event handler method takes one parameter, typically the event arguments, and returns `unit`.</span></span> <span data-ttu-id="cc2e7-113">Předchozí příklad znázorňuje ovladač událostí jako výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="cc2e7-113">The previous example shows the event handler as a lambda expression.</span></span> <span data-ttu-id="cc2e7-114">Ovladačem událostí může být také hodnota funkce, jako v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="cc2e7-114">The event handler can also be a function value, as in the following code example.</span></span> <span data-ttu-id="cc2e7-115">Následující příklad kódu znázorňuje také použití parametrů ovladače událostí, který poskytuje informace specifické pro daný typ události.</span><span class="sxs-lookup"><span data-stu-id="cc2e7-115">The following code example also shows the use of the event handler parameters, which provide information specific to the type of event.</span></span> <span data-ttu-id="cc2e7-116">Pro `MouseMove` událost systém předává `System.Windows.Forms.MouseEventArgs` objekt, který obsahuje `X` a `Y` pozici ukazatele.</span><span class="sxs-lookup"><span data-stu-id="cc2e7-116">For a `MouseMove` event, the system passes a `System.Windows.Forms.MouseEventArgs` object, which contains the `X` and `Y` position of the pointer.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3602.fs)]

## <a name="creating-custom-events"></a><span data-ttu-id="cc2e7-117">Vytváření vlastních událostí</span><span class="sxs-lookup"><span data-stu-id="cc2e7-117">Creating Custom Events</span></span>

<span data-ttu-id="cc2e7-118">Události f # jsou reprezentovány typem [události](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpevent-1.html) jazyka f #, který implementuje rozhraní [IEvent](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-ievent-1.html) .</span><span class="sxs-lookup"><span data-stu-id="cc2e7-118">F# events are represented by the F# [Event](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpevent-1.html) type, which implements the [IEvent](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-ievent-1.html) interface.</span></span> <span data-ttu-id="cc2e7-119">`IEvent` je to rozhraní, které kombinuje funkce dvou dalších rozhraní `System.IObservable<'T>` a [IDelegateEvent](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-idelegateevent-1.html).</span><span class="sxs-lookup"><span data-stu-id="cc2e7-119">`IEvent` is itself an interface that combines the functionality of two other interfaces, `System.IObservable<'T>` and [IDelegateEvent](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-idelegateevent-1.html).</span></span> <span data-ttu-id="cc2e7-120">Proto `Event` mají ekvivalentní funkce delegátů v jiných jazycích a další funkce z `IObservable` , což znamená, že události jazyka f # podporují filtrování událostí a používají funkce první třídy jazyka f # a lambda výrazy jako obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="cc2e7-120">Therefore, `Event`s have the equivalent functionality of delegates in other languages, plus the additional functionality from `IObservable`, which means that F# events support event filtering and using F# first-class functions and lambda expressions as event handlers.</span></span> <span data-ttu-id="cc2e7-121">Tato funkce je k dispozici v [modulu Event](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-eventmodule.html).</span><span class="sxs-lookup"><span data-stu-id="cc2e7-121">This functionality is provided in the [Event module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-eventmodule.html).</span></span>

<span data-ttu-id="cc2e7-122">Chcete-li vytvořit událost pro třídu, která funguje stejně jako jakákoli jiná událost .NET Framework, přidejte do třídy `let` vazbu, která definuje `Event` jako pole ve třídě.</span><span class="sxs-lookup"><span data-stu-id="cc2e7-122">To create an event on a class that acts just like any other .NET Framework event, add to the class a `let` binding that defines an `Event` as a field in a class.</span></span> <span data-ttu-id="cc2e7-123">Můžete zadat požadovaný typ argumentu události jako typ argumentu, nebo jej ponechat prázdný a odvodit odpovídající typ pomocí kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="cc2e7-123">You can specify the desired event argument type as the type argument, or leave it blank and have the compiler infer the appropriate type.</span></span> <span data-ttu-id="cc2e7-124">Musíte také definovat člen události, který zpřístupňuje událost jako událost typu CLI.</span><span class="sxs-lookup"><span data-stu-id="cc2e7-124">You also must define an event member that exposes the event as a CLI event.</span></span> <span data-ttu-id="cc2e7-125">Tento člen by měl mít atribut [CLIEvent](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-clieventattribute.html) .</span><span class="sxs-lookup"><span data-stu-id="cc2e7-125">This member should have the [CLIEvent](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-clieventattribute.html) attribute.</span></span> <span data-ttu-id="cc2e7-126">Je deklarován jako vlastnost a její implementace je pouze voláním vlastnosti [publikovat](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpevent-1.html#Publish) události.</span><span class="sxs-lookup"><span data-stu-id="cc2e7-126">It is declared like a property and its implementation is just a call to the [Publish](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpevent-1.html#Publish) property of the event.</span></span> <span data-ttu-id="cc2e7-127">Uživatelé vaší třídy mohou použít `Add` metodu publikované události pro přidání obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="cc2e7-127">Users of your class can use the `Add` method of the published event to add a handler.</span></span> <span data-ttu-id="cc2e7-128">Argumentem `Add` metody může být výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="cc2e7-128">The argument for the `Add` method can be a lambda expression.</span></span> <span data-ttu-id="cc2e7-129">Můžete použít `Trigger` vlastnost události k vyvolání události a předání argumentů funkci obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="cc2e7-129">You can use the `Trigger` property of the event to raise the event, passing the arguments to the handler function.</span></span> <span data-ttu-id="cc2e7-130">Následující příklad kódu to dokládá.</span><span class="sxs-lookup"><span data-stu-id="cc2e7-130">The following code example illustrates this.</span></span> <span data-ttu-id="cc2e7-131">V tomto příkladu je odvozeným argumentem typu události řazená kolekce, která představuje argumenty pro výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="cc2e7-131">In this example, the inferred type argument for the event is a tuple, which represents the arguments for the lambda expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3605.fs)]

<span data-ttu-id="cc2e7-132">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="cc2e7-132">The output is as follows.</span></span>

```console
Event1 occurred! Object data: Hello World!
```

<span data-ttu-id="cc2e7-133">Další funkce poskytované `Event` modulem jsou znázorněny zde.</span><span class="sxs-lookup"><span data-stu-id="cc2e7-133">The additional functionality provided by the `Event` module is illustrated here.</span></span> <span data-ttu-id="cc2e7-134">Následující příklad kódu ukazuje základní použití `Event.create` pro vytvoření události a metody triggeru, přidání dvou obslužných rutin událostí ve formě výrazů lambda a následnou aktivací události pro provedení obou výrazů lambda.</span><span class="sxs-lookup"><span data-stu-id="cc2e7-134">The following code example illustrates the basic use of `Event.create` to create an event and a trigger method, add two event handlers in the form of lambda expressions, and then trigger the event to execute both lambda expressions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3603.fs)]

<span data-ttu-id="cc2e7-135">Výstup předchozího kódu vypadá takto.</span><span class="sxs-lookup"><span data-stu-id="cc2e7-135">The output of the previous code is as follows.</span></span>

```console
Event occurred.
Given a value: Event occurred.
```

## <a name="processing-event-streams"></a><span data-ttu-id="cc2e7-136">Zpracování datových proudů události</span><span class="sxs-lookup"><span data-stu-id="cc2e7-136">Processing Event Streams</span></span>

<span data-ttu-id="cc2e7-137">Místo pouhého přidání obslužné rutiny události pro událost pomocí funkce [Event. Add](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-eventmodule.html#add) můžete použít funkce v `Event` modulu ke zpracování datových proudů událostí v vysoce přizpůsobených způsobech.</span><span class="sxs-lookup"><span data-stu-id="cc2e7-137">Instead of just adding an event handler for an event by using the [Event.add](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-eventmodule.html#add) function, you can use the functions in the `Event` module to process streams of events in highly customized ways.</span></span> <span data-ttu-id="cc2e7-138">K tomu je třeba použít přesměrování přesměrování ( `|>` ) spolu s událostí jako první hodnotu v řadě volání funkce a `Event` modul funguje jako následné volání funkce.</span><span class="sxs-lookup"><span data-stu-id="cc2e7-138">To do this, you use the forward pipe (`|>`) together with the event as the first value in a series of function calls, and the `Event` module functions as subsequent function calls.</span></span>

<span data-ttu-id="cc2e7-139">Následující příklad kódu ukazuje, jak lze nastavit událost, pro kterou je ovladač událostí volán pouze za určitých podmínek.</span><span class="sxs-lookup"><span data-stu-id="cc2e7-139">The following code example shows how to set up an event for which the handler is only called under certain conditions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3604.fs)]

<span data-ttu-id="cc2e7-140">[Pozorovatelný modul](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-observablemodule.html) obsahuje podobné funkce, které fungují na pozorovatelných objektech.</span><span class="sxs-lookup"><span data-stu-id="cc2e7-140">The [Observable module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-observablemodule.html) contains similar functions that operate on observable objects.</span></span> <span data-ttu-id="cc2e7-141">Pozorovatelné objekty jsou podobné událostem, aktivně se však k událostem přihlašují pouze tehdy, jsou-li samy přihlašovány.</span><span class="sxs-lookup"><span data-stu-id="cc2e7-141">Observable objects are similar to events but only actively subscribe to events if they themselves are being subscribed to.</span></span>

## <a name="implementing-an-interface-event"></a><span data-ttu-id="cc2e7-142">Implementace události rozhraní</span><span class="sxs-lookup"><span data-stu-id="cc2e7-142">Implementing an Interface Event</span></span>

<span data-ttu-id="cc2e7-143">Při vývoji součástí uživatelského rozhraní začínáte často tak, že vytvoříte nový formulář nebo nový ovládací prvek, který se dědí z existujícího formuláře nebo ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="cc2e7-143">As you develop UI components, you often start by creating a new form or a new control that inherits from an existing form or control.</span></span> <span data-ttu-id="cc2e7-144">Události jsou často definovány v rozhraní. V takovém případě pak musíte implementovat rozhraní za účelem implementace události.</span><span class="sxs-lookup"><span data-stu-id="cc2e7-144">Events are frequently defined on an interface, and, in that case, you must implement the interface to implement the event.</span></span> <span data-ttu-id="cc2e7-145">`System.ComponentModel.INotifyPropertyChanged`Rozhraní definuje jednu `System.ComponentModel.INotifyPropertyChanged.PropertyChanged` událost.</span><span class="sxs-lookup"><span data-stu-id="cc2e7-145">The `System.ComponentModel.INotifyPropertyChanged` interface defines a single `System.ComponentModel.INotifyPropertyChanged.PropertyChanged` event.</span></span> <span data-ttu-id="cc2e7-146">Následující kód znázorňuje způsob implementace události, kterou toto zděděné rozhraní definuje:</span><span class="sxs-lookup"><span data-stu-id="cc2e7-146">The following code illustrates how to implement the event that this inherited interface defined:</span></span>

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

<span data-ttu-id="cc2e7-147">Pokud chcete událost v konstruktoru připojit, je kód trochu složitější, protože Event propojení musí být v `then` bloku v dalším konstruktoru, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="cc2e7-147">If you want to hook up the event in the constructor, the code is a bit more complicated because the event hookup must be in a `then` block in an additional constructor, as in the following example:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="cc2e7-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="cc2e7-148">See also</span></span>

- [<span data-ttu-id="cc2e7-149">Členové</span><span class="sxs-lookup"><span data-stu-id="cc2e7-149">Members</span></span>](index.md)
- [<span data-ttu-id="cc2e7-150">Zpracování a generování událostí</span><span class="sxs-lookup"><span data-stu-id="cc2e7-150">Handling and Raising Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="cc2e7-151">Výrazy lambda: `fun` klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="cc2e7-151">Lambda Expressions: The `fun` Keyword</span></span>](../functions/lambda-expressions-the-fun-keyword.md)
