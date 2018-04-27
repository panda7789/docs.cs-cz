---
title: 'Postupy: Přihlášení a odhlášení odběru událostí (Průvodce programováním v C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- event handlers [C#], creating
- Code Editor, event handlers
- events [C#], creating using the IDE
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ecb65a2156f83d9da722329ff6159bb08e464eaa
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-subscribe-to-and-unsubscribe-from-events-c-programming-guide"></a><span data-ttu-id="1cf48-102">Postupy: Přihlášení a odhlášení odběru událostí (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="1cf48-102">How to: Subscribe to and Unsubscribe from Events (C# Programming Guide)</span></span>
<span data-ttu-id="1cf48-103">Přihlášení k odběru na událost, která se publikuje jinou třídou, když chcete napsat vlastní kód, který je volána, když se vyvolá tuto událost.</span><span class="sxs-lookup"><span data-stu-id="1cf48-103">You subscribe to an event that is published by another class when you want to write custom code that is called when that event is raised.</span></span> <span data-ttu-id="1cf48-104">Například může přihlásíte k odběru na tlačítko `click` událostí, aby bylo možné aplikaci dělat něco užitečné, když uživatel klikne na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="1cf48-104">For example, you might subscribe to a button's `click` event in order to make your application do something useful when the user clicks the button.</span></span>  
  
### <a name="to-subscribe-to-events-by-using-the-visual-studio-ide"></a><span data-ttu-id="1cf48-105">Přihlásit k odběru událostí pomocí prostředí Visual Studio IDE</span><span class="sxs-lookup"><span data-stu-id="1cf48-105">To subscribe to events by using the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="1cf48-106">Pokud nevidíte **vlastnosti** okno v **návrhu** zobrazit, klikněte pravým tlačítkem na formulář nebo ovládací prvek, pro který chcete vytvořit obslužnou rutinu a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="1cf48-106">If you cannot see the **Properties** window, in **Design** view, right-click the form or control for which you want to create an event handler, and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="1cf48-107">Na **vlastnosti** okně klikněte na tlačítko **události** ikonu.</span><span class="sxs-lookup"><span data-stu-id="1cf48-107">On top of the **Properties** window, click the **Events** icon.</span></span>  
  
3.  <span data-ttu-id="1cf48-108">Dvakrát klikněte na událost, kterou chcete vytvořit, například `Load` událostí.</span><span class="sxs-lookup"><span data-stu-id="1cf48-108">Double-click the event that you want to create, for example the `Load` event.</span></span>  
  
     <span data-ttu-id="1cf48-109">Visual C# vytvoří metodu obslužné rutiny události prázdný a přidá ji do vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="1cf48-109">Visual C# creates an empty event handler method and adds it to your code.</span></span> <span data-ttu-id="1cf48-110">Případně můžete přidat kód ručně v **kód** zobrazení.</span><span class="sxs-lookup"><span data-stu-id="1cf48-110">Alternatively you can add the code manually in **Code** view.</span></span> <span data-ttu-id="1cf48-111">Například následující řádky kódu deklarovat metodu obslužné rutiny události, který bude volán při `Form` třídy vyvolá `Load` událostí.</span><span class="sxs-lookup"><span data-stu-id="1cf48-111">For example, the following lines of code declare an event handler method that will be called when the `Form` class raises the `Load` event.</span></span>  
  
     [!code-csharp[csProgGuideEvents#11](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-subscribe-to-and-unsubscribe-from-events_1.cs)]  
  
     <span data-ttu-id="1cf48-112">Řádek kódu, který je požadován k odběru události je také automaticky generovány v `InitializeComponent` metoda v souboru Form1.Designer.cs ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="1cf48-112">The line of code that is required to subscribe to the event is also automatically generated in the `InitializeComponent` method in the Form1.Designer.cs file in your project.</span></span> <span data-ttu-id="1cf48-113">Vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="1cf48-113">It resembles this:</span></span>  
  
    ```csharp
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### <a name="to-subscribe-to-events-programmatically"></a><span data-ttu-id="1cf48-114">Přihlásit k odběru událostí prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="1cf48-114">To subscribe to events programmatically</span></span>  
  
1.  <span data-ttu-id="1cf48-115">Definujte metodu obslužné rutiny události, jejichž podpis odpovídá delegáta pro událost.</span><span class="sxs-lookup"><span data-stu-id="1cf48-115">Define an event handler method whose signature matches the delegate signature for the event.</span></span> <span data-ttu-id="1cf48-116">Například, pokud je na základě události <xref:System.EventHandler> se zakázaným inzerováním metoda představuje typ delegáta, následující kód:</span><span class="sxs-lookup"><span data-stu-id="1cf48-116">For example, if the event is based on the <xref:System.EventHandler> delegate type, the following code represents the method stub:</span></span>  
  
    ```csharp
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2.  <span data-ttu-id="1cf48-117">Použít operátor přiřazení sčítání (`+=`) připojit vaší obslužné rutiny události pro událost.</span><span class="sxs-lookup"><span data-stu-id="1cf48-117">Use the addition assignment operator (`+=`) to attach your event handler to the event.</span></span> <span data-ttu-id="1cf48-118">V následujícím příkladu se předpokládá, že objekt s názvem `publisher` má událost s názvem `RaiseCustomEvent`.</span><span class="sxs-lookup"><span data-stu-id="1cf48-118">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent`.</span></span> <span data-ttu-id="1cf48-119">Všimněte si, že třídě odběratele potřebuje odkaz na třídě vydavatele Chcete-li se přihlásit k jeho události odběru.</span><span class="sxs-lookup"><span data-stu-id="1cf48-119">Note that the subscriber class needs a reference to the publisher class in order to subscribe to its events.</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="1cf48-120">Všimněte si, že předchozí syntaxe jazyka C# 2.0 nové.</span><span class="sxs-lookup"><span data-stu-id="1cf48-120">Note that the previous syntax is new in C# 2.0.</span></span> <span data-ttu-id="1cf48-121">Je přesně odpovídá syntaxe jazyka C# 1.0, ve kterém musí být explicitně vytvořen zapouzdřením delegát pomocí `new` – klíčové slovo:</span><span class="sxs-lookup"><span data-stu-id="1cf48-121">It is exactly equivalent to the C# 1.0 syntax in which the encapsulating delegate must be explicitly created by using the `new` keyword:</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += new CustomEventHandler(HandleCustomEvent);  
    ```  
  
     <span data-ttu-id="1cf48-122">Obslužné rutiny události lze také přidat pomocí výrazu lambda:</span><span class="sxs-lookup"><span data-stu-id="1cf48-122">An event handler can also be added by using a lambda expression:</span></span>  
  
    ```csharp
    public Form1()  
    {  
        InitializeComponent();  
        // Use a lambda expression to define an event handler.  
        this.Click += (s,e) => { MessageBox.Show(  
           ((MouseEventArgs)e).Location.ToString());};  
    }  
    ```  
  
     <span data-ttu-id="1cf48-123">Další informace najdete v tématu [postupy: použití Lambda výrazy mimo LINQ](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md).</span><span class="sxs-lookup"><span data-stu-id="1cf48-123">For more information, see [How to: Use Lambda Expressions Outside LINQ](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md).</span></span>  
  
### <a name="to-subscribe-to-events-by-using-an-anonymous-method"></a><span data-ttu-id="1cf48-124">Přihlásit k odběru událostí pomocí anonymní metody</span><span class="sxs-lookup"><span data-stu-id="1cf48-124">To subscribe to events by using an anonymous method</span></span>  
  
-   <span data-ttu-id="1cf48-125">Pokud nebudete mít k odhlášení odběru událostí později, můžete použít operátor přiřazení sčítání (`+=`) pro připojení anonymní metody k události.</span><span class="sxs-lookup"><span data-stu-id="1cf48-125">If you will not have to unsubscribe to an event later, you can use the addition assignment operator (`+=`) to attach an anonymous method to the event.</span></span> <span data-ttu-id="1cf48-126">V následujícím příkladu se předpokládá, že objekt s názvem `publisher` má událost s názvem `RaiseCustomEvent` a že `CustomEventArgs` třída definována také k provedení nějaký druh informací o specializované události.</span><span class="sxs-lookup"><span data-stu-id="1cf48-126">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent` and that a `CustomEventArgs` class has also been defined to carry some kind of specialized event information.</span></span> <span data-ttu-id="1cf48-127">Všimněte si, že třída odběratele musí odkaz na `publisher` Chcete-li se přihlásit k jeho události odběru.</span><span class="sxs-lookup"><span data-stu-id="1cf48-127">Note that the subscriber class needs a reference to `publisher` in order to subscribe to its events.</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     <span data-ttu-id="1cf48-128">Je důležité si všimněte si, že nelze zrušíte snadno událost Pokud použijete anonymní funkce si ji předplatili.</span><span class="sxs-lookup"><span data-stu-id="1cf48-128">It is important to notice that you cannot easily unsubscribe from an event if you used an anonymous function to subscribe to it.</span></span> <span data-ttu-id="1cf48-129">Chcete-li odhlásit v tomto scénáři, je potřeba přejděte zpět na kód, kde se přihlásíte k odběru události, uložit jako proměnnou delegáta anonymní metody a pak přidejte delegát pro událost.</span><span class="sxs-lookup"><span data-stu-id="1cf48-129">To unsubscribe in this scenario, it is necessary to go back to the code where you subscribe to the event, store the anonymous method in a delegate variable, and then add the delegate to the event.</span></span> <span data-ttu-id="1cf48-130">Obecně doporučujeme anonymní funkce nepoužívejte k odběru událostí, pokud bude mít k odhlášení odběru událostí novější někde v kódu.</span><span class="sxs-lookup"><span data-stu-id="1cf48-130">In general, we recommend that you do not use anonymous functions to subscribe to events if you will have to unsubscribe from the event at some later point in your code.</span></span> <span data-ttu-id="1cf48-131">Další informace o anonymní funkce najdete v tématu [anonymní funkce](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="1cf48-131">For more information about anonymous functions, see [Anonymous Functions](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="unsubscribing"></a><span data-ttu-id="1cf48-132">Odhlášení</span><span class="sxs-lookup"><span data-stu-id="1cf48-132">Unsubscribing</span></span>  
 <span data-ttu-id="1cf48-133">Abyste zabránili vaší obslužné rutiny událostí je volána, když událost se vyvolá, odhlášení odběru událostí.</span><span class="sxs-lookup"><span data-stu-id="1cf48-133">To prevent your event handler from being invoked when the event is raised, unsubscribe from the event.</span></span> <span data-ttu-id="1cf48-134">Prevence úniků prostředků by měl odhlášení odběru událostí před vyřazení objekt odběratele.</span><span class="sxs-lookup"><span data-stu-id="1cf48-134">In order to prevent resource leaks, you should unsubscribe from events before you dispose of a subscriber object.</span></span> <span data-ttu-id="1cf48-135">Dokud zrušíte událost, vícesměrového vysílání delegát podkladovou události v objektu, publikování obsahuje odkaz na delegáta, který zapouzdřuje obslužné rutiny události odběratele.</span><span class="sxs-lookup"><span data-stu-id="1cf48-135">Until you unsubscribe from an event, the multicast delegate that underlies the event in the publishing object has a reference to the delegate that encapsulates the subscriber's event handler.</span></span> <span data-ttu-id="1cf48-136">Tak dlouho, dokud objekt publikování obsahuje tento odkaz, neodstraní uvolňování objektu odběratele.</span><span class="sxs-lookup"><span data-stu-id="1cf48-136">As long as the publishing object holds that reference, garbage collection will not delete your subscriber object.</span></span>  
  
#### <a name="to-unsubscribe-from-an-event"></a><span data-ttu-id="1cf48-137">Chcete-li odhlásit z události</span><span class="sxs-lookup"><span data-stu-id="1cf48-137">To unsubscribe from an event</span></span>  
  
-   <span data-ttu-id="1cf48-138">Operátor přiřazení odčítání (`-=`) k odhlášení odběru událostí:</span><span class="sxs-lookup"><span data-stu-id="1cf48-138">Use the subtraction assignment operator (`-=`) to unsubscribe from an event:</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="1cf48-139">Pokud všechny Odběratelé, kteří mají odhlásil z události, instanci události ve třídě vydavatele je nastavena na `null`.</span><span class="sxs-lookup"><span data-stu-id="1cf48-139">When all subscribers have unsubscribed from an event, the event instance in the publisher class is set to `null`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cf48-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="1cf48-140">See Also</span></span>  
 [<span data-ttu-id="1cf48-141">Události</span><span class="sxs-lookup"><span data-stu-id="1cf48-141">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
 [<span data-ttu-id="1cf48-142">event</span><span class="sxs-lookup"><span data-stu-id="1cf48-142">event</span></span>](../../../csharp/language-reference/keywords/event.md)  
 [<span data-ttu-id="1cf48-143">Postupy: Publikování událostí odpovídajících směrnicím rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1cf48-143">How to: Publish Events that Conform to .NET Framework Guidelines</span></span>](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
 [<span data-ttu-id="1cf48-144">-= – Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="1cf48-144">-= Operator (C# Reference)</span></span>](../../language-reference/operators/subtraction-assignment-operator.md)  
 [<span data-ttu-id="1cf48-145">+= – operátor</span><span class="sxs-lookup"><span data-stu-id="1cf48-145">+= Operator</span></span>](../../../csharp/language-reference/operators/addition-assignment-operator.md)