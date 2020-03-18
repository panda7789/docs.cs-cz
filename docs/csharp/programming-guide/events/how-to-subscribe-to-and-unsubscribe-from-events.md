---
title: Jak se přihlásit k odběru a odhlásit se z událostí - C# Programming Guide
ms.date: 07/20/2015
helpviewer_keywords:
- event handlers [C#], creating
- Code Editor, event handlers
- events [C#], creating using the IDE
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
ms.openlocfilehash: 3df357cb15f7f77cefbf360dd9615ce246afe2ea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705324"
---
# <a name="how-to-subscribe-to-and-unsubscribe-from-events-c-programming-guide"></a><span data-ttu-id="392bd-102">Jak se přihlásit k odběru a odhlásit se z událostí (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="392bd-102">How to subscribe to and unsubscribe from events (C# Programming Guide)</span></span>
<span data-ttu-id="392bd-103">Přihlášení k odběru události, která je publikována jinou třídou, pokud chcete napsat vlastní kód, který je volán při vyvolání této události.</span><span class="sxs-lookup"><span data-stu-id="392bd-103">You subscribe to an event that is published by another class when you want to write custom code that is called when that event is raised.</span></span> <span data-ttu-id="392bd-104">Můžete se například přihlásit k `click` odběru události tlačítka, aby vaše aplikace udělala něco užitečného, když uživatel klikne na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="392bd-104">For example, you might subscribe to a button's `click` event in order to make your application do something useful when the user clicks the button.</span></span>  
  
### <a name="to-subscribe-to-events-by-using-the-visual-studio-ide"></a><span data-ttu-id="392bd-105">Přihlášení k odběru událostí pomocí ide sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="392bd-105">To subscribe to events by using the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="392bd-106">Pokud se v návrhovém **zobrazení** nezobrazí okno **Vlastnosti,** klepněte pravým tlačítkem myši na formulář nebo ovládací prvek, pro který chcete vytvořit obslužnou rutinu události, a vyberte **příkaz Vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="392bd-106">If you cannot see the **Properties** window, in **Design** view, right-click the form or control for which you want to create an event handler, and select **Properties**.</span></span>  
  
2. <span data-ttu-id="392bd-107">V horní části okna **Vlastnosti** klikněte na ikonu **Události.**</span><span class="sxs-lookup"><span data-stu-id="392bd-107">On top of the **Properties** window, click the **Events** icon.</span></span>  
  
3. <span data-ttu-id="392bd-108">Poklepejte na událost, kterou chcete vytvořit, například na `Load` událost.</span><span class="sxs-lookup"><span data-stu-id="392bd-108">Double-click the event that you want to create, for example the `Load` event.</span></span>  
  
     <span data-ttu-id="392bd-109">Visual C# vytvoří metodu obslužné rutiny prázdné události a přidá ji do kódu.</span><span class="sxs-lookup"><span data-stu-id="392bd-109">Visual C# creates an empty event handler method and adds it to your code.</span></span> <span data-ttu-id="392bd-110">Případně můžete přidat kód ručně v zobrazení **kódu.**</span><span class="sxs-lookup"><span data-stu-id="392bd-110">Alternatively you can add the code manually in **Code** view.</span></span> <span data-ttu-id="392bd-111">Například následující řádky kódu deklarují metodu obslužné rutiny události, která bude volána, `Form` když třída vyvolá `Load` událost.</span><span class="sxs-lookup"><span data-stu-id="392bd-111">For example, the following lines of code declare an event handler method that will be called when the `Form` class raises the `Load` event.</span></span>  
  
     [!code-csharp[csProgGuideEvents#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#11)]  
  
     <span data-ttu-id="392bd-112">Řádek kódu, který je nutný k přihlášení k odběru `InitializeComponent` události, je také automaticky generován v metodě v souboru Form1.Designer.cs v projektu.</span><span class="sxs-lookup"><span data-stu-id="392bd-112">The line of code that is required to subscribe to the event is also automatically generated in the `InitializeComponent` method in the Form1.Designer.cs file in your project.</span></span> <span data-ttu-id="392bd-113">Podobá se toto:</span><span class="sxs-lookup"><span data-stu-id="392bd-113">It resembles this:</span></span>  
  
    ```csharp
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### <a name="to-subscribe-to-events-programmatically"></a><span data-ttu-id="392bd-114">Chcete-li se přihlásit k odběru událostí programově</span><span class="sxs-lookup"><span data-stu-id="392bd-114">To subscribe to events programmatically</span></span>  
  
1. <span data-ttu-id="392bd-115">Definujte metodu obslužné rutiny události, jejíž podpis odpovídá podpisu delegáta pro událost.</span><span class="sxs-lookup"><span data-stu-id="392bd-115">Define an event handler method whose signature matches the delegate signature for the event.</span></span> <span data-ttu-id="392bd-116">Například pokud je událost založena <xref:System.EventHandler> na typu delegáta, následující kód představuje zástupný kód metody:</span><span class="sxs-lookup"><span data-stu-id="392bd-116">For example, if the event is based on the <xref:System.EventHandler> delegate type, the following code represents the method stub:</span></span>  
  
    ```csharp
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2. <span data-ttu-id="392bd-117">Pomocí operátoru přiřazení`+=`sčítání ( ) připojte k události obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="392bd-117">Use the addition assignment operator (`+=`) to attach an event handler to the event.</span></span> <span data-ttu-id="392bd-118">V následujícím příkladu předpokládejme, `publisher` že objekt `RaiseCustomEvent`s názvem má událost s názvem .</span><span class="sxs-lookup"><span data-stu-id="392bd-118">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent`.</span></span> <span data-ttu-id="392bd-119">Všimněte si, že třída odběratele potřebuje odkaz na třídu vydavatele, aby se mohla přihlásit k odběru svých událostí.</span><span class="sxs-lookup"><span data-stu-id="392bd-119">Note that the subscriber class needs a reference to the publisher class in order to subscribe to its events.</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="392bd-120">Všimněte si, že předchozí syntaxe je nová v C# 2.0.</span><span class="sxs-lookup"><span data-stu-id="392bd-120">Note that the previous syntax is new in C# 2.0.</span></span> <span data-ttu-id="392bd-121">Je přesně ekvivalentní syntaxi jazyka C# 1.0, ve které musí být encapsulating delegate explicitně vytvořen pomocí klíčového `new` slova:</span><span class="sxs-lookup"><span data-stu-id="392bd-121">It is exactly equivalent to the C# 1.0 syntax in which the encapsulating delegate must be explicitly created by using the `new` keyword:</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += new CustomEventHandler(HandleCustomEvent);  
    ```  
  
     <span data-ttu-id="392bd-122">Výraz [lambda](../statements-expressions-operators/lambda-expressions.md) můžete také použít k určení obslužné rutiny události:</span><span class="sxs-lookup"><span data-stu-id="392bd-122">You also can use a [lambda expression](../statements-expressions-operators/lambda-expressions.md) to specify an event handler:</span></span>
  
    ```csharp
    public Form1()  
    {  
        InitializeComponent();  
        this.Click += (s,e) =>
            {
                MessageBox.Show(((MouseEventArgs)e).Location.ToString());
            };
    }  
    ```  
  
### <a name="to-subscribe-to-events-by-using-an-anonymous-method"></a><span data-ttu-id="392bd-123">Přihlášení k odběru událostí pomocí anonymní metody</span><span class="sxs-lookup"><span data-stu-id="392bd-123">To subscribe to events by using an anonymous method</span></span>  
  
- <span data-ttu-id="392bd-124">Pokud se nebudete muset odhlásit z odběru události později,`+=`můžete k události připojit anonymní metodu pomocí operátoru přiřazení sčítání ( ).</span><span class="sxs-lookup"><span data-stu-id="392bd-124">If you will not have to unsubscribe to an event later, you can use the addition assignment operator (`+=`) to attach an anonymous method to the event.</span></span> <span data-ttu-id="392bd-125">V následujícím příkladu předpokládejme, `publisher` že objekt `RaiseCustomEvent` s `CustomEventArgs` názvem má událost s názvem a že třída byla také definována tak, aby nesla nějaký druh specializovaných informací o událostech.</span><span class="sxs-lookup"><span data-stu-id="392bd-125">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent` and that a `CustomEventArgs` class has also been defined to carry some kind of specialized event information.</span></span> <span data-ttu-id="392bd-126">Všimněte si, že třída `publisher` odběratele potřebuje odkaz na k přihlášení k odběru své události.</span><span class="sxs-lookup"><span data-stu-id="392bd-126">Note that the subscriber class needs a reference to `publisher` in order to subscribe to its events.</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     <span data-ttu-id="392bd-127">Je důležité si uvědomit, že nemůžete snadno odhlásit z události, pokud jste použili anonymní funkci k odběru.</span><span class="sxs-lookup"><span data-stu-id="392bd-127">It is important to notice that you cannot easily unsubscribe from an event if you used an anonymous function to subscribe to it.</span></span> <span data-ttu-id="392bd-128">Chcete-li odhlásit v tomto scénáři, je nutné se vrátit ke kódu, kde se přihlásíte k odběru události, uložte anonymní metodu v proměnné delegáta a pak přidejte delegáta k události.</span><span class="sxs-lookup"><span data-stu-id="392bd-128">To unsubscribe in this scenario, it is necessary to go back to the code where you subscribe to the event, store the anonymous method in a delegate variable, and then add the delegate to the event.</span></span> <span data-ttu-id="392bd-129">Obecně doporučujeme, abyste nepoužívali anonymní funkce k přihlášení k odběru událostí, pokud budete muset odhlásit z události v určitém pozdějším okamžiku vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="392bd-129">In general, we recommend that you do not use anonymous functions to subscribe to events if you will have to unsubscribe from the event at some later point in your code.</span></span> <span data-ttu-id="392bd-130">Další informace o anonymních funkcích naleznete [v tématu Anonymní funkce](../statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="392bd-130">For more information about anonymous functions, see [Anonymous Functions](../statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="unsubscribing"></a><span data-ttu-id="392bd-131">Odhlášení</span><span class="sxs-lookup"><span data-stu-id="392bd-131">Unsubscribing</span></span>  
 <span data-ttu-id="392bd-132">Chcete-li zabránit vyvolání obslužné rutiny události při vyvolání události, odhlaste se od události.</span><span class="sxs-lookup"><span data-stu-id="392bd-132">To prevent your event handler from being invoked when the event is raised, unsubscribe from the event.</span></span> <span data-ttu-id="392bd-133">Chcete-li zabránit úniku prostředků, měli byste zrušit odběr z událostí před vyřazením objektu odběratele.</span><span class="sxs-lookup"><span data-stu-id="392bd-133">In order to prevent resource leaks, you should unsubscribe from events before you dispose of a subscriber object.</span></span> <span data-ttu-id="392bd-134">Dokud se neodhlásíte z události, delegát vícesměrového vysílání, který je základem události v objektu publikování, má odkaz na delegáta, který zapouzdřuje obslužnou rutinu události odběratele.</span><span class="sxs-lookup"><span data-stu-id="392bd-134">Until you unsubscribe from an event, the multicast delegate that underlies the event in the publishing object has a reference to the delegate that encapsulates the subscriber's event handler.</span></span> <span data-ttu-id="392bd-135">Tak dlouho, dokud objekt publikování obsahuje tento odkaz, uvolňování paměti neodstraní objekt odběratele.</span><span class="sxs-lookup"><span data-stu-id="392bd-135">As long as the publishing object holds that reference, garbage collection will not delete your subscriber object.</span></span>  
  
#### <a name="to-unsubscribe-from-an-event"></a><span data-ttu-id="392bd-136">Odhlášení z odběru události</span><span class="sxs-lookup"><span data-stu-id="392bd-136">To unsubscribe from an event</span></span>  
  
- <span data-ttu-id="392bd-137">K odhlášení z`-=`události použijte operátor přiřazení odčítání ( ).</span><span class="sxs-lookup"><span data-stu-id="392bd-137">Use the subtraction assignment operator (`-=`) to unsubscribe from an event:</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="392bd-138">Pokud se všichni odběratelé odhlásili z události, instance události ve `null`třídě vydavatele je nastavena na .</span><span class="sxs-lookup"><span data-stu-id="392bd-138">When all subscribers have unsubscribed from an event, the event instance in the publisher class is set to `null`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="392bd-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="392bd-139">See also</span></span>

- [<span data-ttu-id="392bd-140">Akce</span><span class="sxs-lookup"><span data-stu-id="392bd-140">Events</span></span>](./index.md)
- [<span data-ttu-id="392bd-141">Událost</span><span class="sxs-lookup"><span data-stu-id="392bd-141">event</span></span>](../../language-reference/keywords/event.md)
- [<span data-ttu-id="392bd-142">Jak publikovat události vyhovující pravidlům rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="392bd-142">How to publish events that conform to .NET Framework Guidelines</span></span>](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)
- [<span data-ttu-id="392bd-143">- a -= operátoři</span><span class="sxs-lookup"><span data-stu-id="392bd-143">- and -= operators</span></span>](../../language-reference/operators/subtraction-operator.md)
- [<span data-ttu-id="392bd-144">+ a += operátory</span><span class="sxs-lookup"><span data-stu-id="392bd-144">+ and += operators</span></span>](../../language-reference/operators/addition-operator.md)
