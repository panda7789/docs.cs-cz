---
title: 'Postupy: Přihlaste se k odběru a zrušit její odběr události – C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- event handlers [C#], creating
- Code Editor, event handlers
- events [C#], creating using the IDE
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
ms.openlocfilehash: d1442e02d651cd283e5ff63d28f3cfe80e99cc7d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59306596"
---
# <a name="how-to-subscribe-to-and-unsubscribe-from-events-c-programming-guide"></a><span data-ttu-id="c7c06-102">Postupy: Přihlaste se k odběru a zrušit její odběr událostí (C# Průvodce programováním v)</span><span class="sxs-lookup"><span data-stu-id="c7c06-102">How to: Subscribe to and Unsubscribe from Events (C# Programming Guide)</span></span>
<span data-ttu-id="c7c06-103">Se přihlásíte k odběru události, která se publikuje jinou třídou, když chcete napsat vlastní kód, který se volá, když se vyvolá tuto událost.</span><span class="sxs-lookup"><span data-stu-id="c7c06-103">You subscribe to an event that is published by another class when you want to write custom code that is called when that event is raised.</span></span> <span data-ttu-id="c7c06-104">Například může přihlásit tlačítko `click` událostí, aby vaše aplikace dělat něco užitečné, když uživatel klikne na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="c7c06-104">For example, you might subscribe to a button's `click` event in order to make your application do something useful when the user clicks the button.</span></span>  
  
### <a name="to-subscribe-to-events-by-using-the-visual-studio-ide"></a><span data-ttu-id="c7c06-105">Přihlásit k odběru události pomocí rozhraní IDE sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c7c06-105">To subscribe to events by using the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="c7c06-106">Pokud nevidíte **vlastnosti** okno v **návrhu** zobrazení, klikněte pravým tlačítkem na formulář nebo ovládací prvek, pro kterou chcete vytvořit obslužnou rutinu události a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="c7c06-106">If you cannot see the **Properties** window, in **Design** view, right-click the form or control for which you want to create an event handler, and select **Properties**.</span></span>  
  
2. <span data-ttu-id="c7c06-107">Nahoře **vlastnosti** okna, klikněte na tlačítko **události** ikonu.</span><span class="sxs-lookup"><span data-stu-id="c7c06-107">On top of the **Properties** window, click the **Events** icon.</span></span>  
  
3. <span data-ttu-id="c7c06-108">Poklikáním na událost, kterou chcete vytvořit, například `Load` událostí.</span><span class="sxs-lookup"><span data-stu-id="c7c06-108">Double-click the event that you want to create, for example the `Load` event.</span></span>  
  
     <span data-ttu-id="c7c06-109">Visual C# vytvoří metodu obslužné rutiny události prázdný a přidá ji do vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="c7c06-109">Visual C# creates an empty event handler method and adds it to your code.</span></span> <span data-ttu-id="c7c06-110">Případně můžete přidat ručně v kódu **kód** zobrazení.</span><span class="sxs-lookup"><span data-stu-id="c7c06-110">Alternatively you can add the code manually in **Code** view.</span></span> <span data-ttu-id="c7c06-111">Například následující řádky kódu deklarovat metodu obslužné rutiny události, která bude volána při `Form` třídy vyvolá `Load` událostí.</span><span class="sxs-lookup"><span data-stu-id="c7c06-111">For example, the following lines of code declare an event handler method that will be called when the `Form` class raises the `Load` event.</span></span>  
  
     [!code-csharp[csProgGuideEvents#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#11)]  
  
     <span data-ttu-id="c7c06-112">Řádek kódu, který je potřeba k události registrovat také automaticky generován `InitializeComponent` metody v souboru Form1.Designer.cs ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="c7c06-112">The line of code that is required to subscribe to the event is also automatically generated in the `InitializeComponent` method in the Form1.Designer.cs file in your project.</span></span> <span data-ttu-id="c7c06-113">Vypadal takto:</span><span class="sxs-lookup"><span data-stu-id="c7c06-113">It resembles this:</span></span>  
  
    ```csharp
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### <a name="to-subscribe-to-events-programmatically"></a><span data-ttu-id="c7c06-114">Přihlaste se k odběru událostí prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="c7c06-114">To subscribe to events programmatically</span></span>  
  
1. <span data-ttu-id="c7c06-115">Definujte metodu obslužné rutiny události, jejíž podpis odpovídá delegáta pro událost.</span><span class="sxs-lookup"><span data-stu-id="c7c06-115">Define an event handler method whose signature matches the delegate signature for the event.</span></span> <span data-ttu-id="c7c06-116">Například, pokud je na základě události <xref:System.EventHandler> typu delegátu, následující kód představuje pahýl metody:</span><span class="sxs-lookup"><span data-stu-id="c7c06-116">For example, if the event is based on the <xref:System.EventHandler> delegate type, the following code represents the method stub:</span></span>  
  
    ```csharp
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2. <span data-ttu-id="c7c06-117">Operátor přiřazení sčítání (`+=`) připojit vaše obslužná rutina události pro událost.</span><span class="sxs-lookup"><span data-stu-id="c7c06-117">Use the addition assignment operator (`+=`) to attach your event handler to the event.</span></span> <span data-ttu-id="c7c06-118">V následujícím příkladu se předpokládá, že objekt s názvem `publisher` má událost s názvem `RaiseCustomEvent`.</span><span class="sxs-lookup"><span data-stu-id="c7c06-118">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent`.</span></span> <span data-ttu-id="c7c06-119">Všimněte si, že třída odběratele musí odkaz na třídu vydavatele k přihlášení k odběru jeho událostí.</span><span class="sxs-lookup"><span data-stu-id="c7c06-119">Note that the subscriber class needs a reference to the publisher class in order to subscribe to its events.</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="c7c06-120">Všimněte si, že předchozí syntaxi je nového v jazyce C# 2.0.</span><span class="sxs-lookup"><span data-stu-id="c7c06-120">Note that the previous syntax is new in C# 2.0.</span></span> <span data-ttu-id="c7c06-121">Je přesně odpovídá syntaxe jazyka C# 1.0 ve kterém musí být explicitně vytvořeny zapouzdřující delegáta s použitím `new` – klíčové slovo:</span><span class="sxs-lookup"><span data-stu-id="c7c06-121">It is exactly equivalent to the C# 1.0 syntax in which the encapsulating delegate must be explicitly created by using the `new` keyword:</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += new CustomEventHandler(HandleCustomEvent);  
    ```  
  
     <span data-ttu-id="c7c06-122">Pomocí výrazu lambda lze také přidat obslužné rutiny události:</span><span class="sxs-lookup"><span data-stu-id="c7c06-122">An event handler can also be added by using a lambda expression:</span></span>  
  
    ```csharp
    public Form1()  
    {  
        InitializeComponent();  
        // Use a lambda expression to define an event handler.  
        this.Click += (s,e) => { MessageBox.Show(  
           ((MouseEventArgs)e).Location.ToString());};  
    }  
    ```  
  
     <span data-ttu-id="c7c06-123">Další informace najdete v tématu [jak: Použití výrazů Lambda mimo LINQ](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md).</span><span class="sxs-lookup"><span data-stu-id="c7c06-123">For more information, see [How to: Use Lambda Expressions Outside LINQ](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md).</span></span>  
  
### <a name="to-subscribe-to-events-by-using-an-anonymous-method"></a><span data-ttu-id="c7c06-124">Přihlásit k odběru událostí s využitím anonymní metoda</span><span class="sxs-lookup"><span data-stu-id="c7c06-124">To subscribe to events by using an anonymous method</span></span>  
  
-   <span data-ttu-id="c7c06-125">Pokud nebudete mít k odhlášení odběru události později, můžete použít operátor přiřazení sčítání (`+=`) na anonymní metodu připojte k této události.</span><span class="sxs-lookup"><span data-stu-id="c7c06-125">If you will not have to unsubscribe to an event later, you can use the addition assignment operator (`+=`) to attach an anonymous method to the event.</span></span> <span data-ttu-id="c7c06-126">V následujícím příkladu se předpokládá, že objekt s názvem `publisher` má událost s názvem `RaiseCustomEvent` a že `CustomEventArgs` třída definována také provádět nějaký druh informací o specializované události.</span><span class="sxs-lookup"><span data-stu-id="c7c06-126">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent` and that a `CustomEventArgs` class has also been defined to carry some kind of specialized event information.</span></span> <span data-ttu-id="c7c06-127">Všimněte si, že třída odběratele musí odkaz na `publisher` k přihlášení k odběru jeho událostí.</span><span class="sxs-lookup"><span data-stu-id="c7c06-127">Note that the subscriber class needs a reference to `publisher` in order to subscribe to its events.</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     <span data-ttu-id="c7c06-128">Je důležité si všimněte, že je nelze zrušit snadno odběr události byste používali anonymní funkce pro si ji předplatit.</span><span class="sxs-lookup"><span data-stu-id="c7c06-128">It is important to notice that you cannot easily unsubscribe from an event if you used an anonymous function to subscribe to it.</span></span> <span data-ttu-id="c7c06-129">Zrušení odběru v tomto scénáři, je nutné přejít zpět do kódu, kde se přihlásíte k odběru události, uložte anonymní metody delegáta proměnné a pak přidat delegáta pro událost.</span><span class="sxs-lookup"><span data-stu-id="c7c06-129">To unsubscribe in this scenario, it is necessary to go back to the code where you subscribe to the event, store the anonymous method in a delegate variable, and then add the delegate to the event.</span></span> <span data-ttu-id="c7c06-130">Obecně doporučujeme, abyste je velmi riskantní používat anonymní funkce přihlásit k odběru události v případě, že budete muset zrušit odběr události někdy později ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="c7c06-130">In general, we recommend that you do not use anonymous functions to subscribe to events if you will have to unsubscribe from the event at some later point in your code.</span></span> <span data-ttu-id="c7c06-131">Další informace o anonymní funkce, najdete v části [anonymní funkce](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="c7c06-131">For more information about anonymous functions, see [Anonymous Functions](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="unsubscribing"></a><span data-ttu-id="c7c06-132">Ruší se předplatné</span><span class="sxs-lookup"><span data-stu-id="c7c06-132">Unsubscribing</span></span>  
 <span data-ttu-id="c7c06-133">Abyste zabránili vaše obslužná rutina události volaná při vyvolání události, zrušit odběr události.</span><span class="sxs-lookup"><span data-stu-id="c7c06-133">To prevent your event handler from being invoked when the event is raised, unsubscribe from the event.</span></span> <span data-ttu-id="c7c06-134">Pokud chcete zabránit nedostatku prostředků by měl zrušit odběr událostí před vyřazení objektu odběratele.</span><span class="sxs-lookup"><span data-stu-id="c7c06-134">In order to prevent resource leaks, you should unsubscribe from events before you dispose of a subscriber object.</span></span> <span data-ttu-id="c7c06-135">Dokud odběr události vícesměrového vysílání delegáta, které je základem událost v objektu publikování obsahuje odkaz na delegáta, který zapouzdřuje obslužná rutina události odběratele.</span><span class="sxs-lookup"><span data-stu-id="c7c06-135">Until you unsubscribe from an event, the multicast delegate that underlies the event in the publishing object has a reference to the delegate that encapsulates the subscriber's event handler.</span></span> <span data-ttu-id="c7c06-136">Tak dlouho, dokud publikování objekt obsahuje tento odkaz, nedojde k odstranění objektu odběratele uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="c7c06-136">As long as the publishing object holds that reference, garbage collection will not delete your subscriber object.</span></span>  
  
#### <a name="to-unsubscribe-from-an-event"></a><span data-ttu-id="c7c06-137">Chcete-li zrušit odběr události</span><span class="sxs-lookup"><span data-stu-id="c7c06-137">To unsubscribe from an event</span></span>  
  
-   <span data-ttu-id="c7c06-138">Operátor přiřazení odčítání (`-=`) Chcete-li zrušit odběr události:</span><span class="sxs-lookup"><span data-stu-id="c7c06-138">Use the subtraction assignment operator (`-=`) to unsubscribe from an event:</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="c7c06-139">Když všichni předplatitelé odhlásili odběr události, instanci události ve třídě vydavatele se nastaví na `null`.</span><span class="sxs-lookup"><span data-stu-id="c7c06-139">When all subscribers have unsubscribed from an event, the event instance in the publisher class is set to `null`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7c06-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c7c06-140">See also</span></span>

- [<span data-ttu-id="c7c06-141">Události</span><span class="sxs-lookup"><span data-stu-id="c7c06-141">Events</span></span>](../../../csharp/programming-guide/events/index.md)
- [<span data-ttu-id="c7c06-142">event</span><span class="sxs-lookup"><span data-stu-id="c7c06-142">event</span></span>](../../../csharp/language-reference/keywords/event.md)
- [<span data-ttu-id="c7c06-143">Postupy: Publikování událostí odpovídajících směrnicím rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c7c06-143">How to: Publish Events that Conform to .NET Framework Guidelines</span></span>](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)
- [<span data-ttu-id="c7c06-144">-= – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="c7c06-144">-= Operator (C# Reference)</span></span>](../../language-reference/operators/subtraction-assignment-operator.md)
- [<span data-ttu-id="c7c06-145">+= – operátor</span><span class="sxs-lookup"><span data-stu-id="c7c06-145">+= Operator</span></span>](../../../csharp/language-reference/operators/addition-assignment-operator.md)
