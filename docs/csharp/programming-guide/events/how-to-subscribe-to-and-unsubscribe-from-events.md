---
title: Jak se přihlásit k odběru a zrušit odběr událostí – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- event handlers [C#], creating
- Code Editor, event handlers
- events [C#], creating using the IDE
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
ms.openlocfilehash: 3df357cb15f7f77cefbf360dd9615ce246afe2ea
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705324"
---
# <a name="how-to-subscribe-to-and-unsubscribe-from-events-c-programming-guide"></a><span data-ttu-id="5e80a-102">Přihlášení a odhlášení odběru událostí (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="5e80a-102">How to subscribe to and unsubscribe from events (C# Programming Guide)</span></span>
<span data-ttu-id="5e80a-103">Přihlásíte se k odběru události, která je publikována jinou třídou, pokud chcete napsat vlastní kód, který je volán při vyvolání události.</span><span class="sxs-lookup"><span data-stu-id="5e80a-103">You subscribe to an event that is published by another class when you want to write custom code that is called when that event is raised.</span></span> <span data-ttu-id="5e80a-104">Například se můžete přihlásit k odběru události `click` tlačítka, aby se vaše aplikace vytvářely co nejužitečnější, když uživatel klikne na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="5e80a-104">For example, you might subscribe to a button's `click` event in order to make your application do something useful when the user clicks the button.</span></span>  
  
### <a name="to-subscribe-to-events-by-using-the-visual-studio-ide"></a><span data-ttu-id="5e80a-105">Přihlášení k odběru událostí pomocí integrovaného vývojového prostředí (IDE) sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5e80a-105">To subscribe to events by using the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="5e80a-106">Pokud se okno **vlastnosti** nezobrazí, klikněte v **návrhovém** zobrazení pravým tlačítkem myši na formulář nebo ovládací prvek, pro který chcete vytvořit obslužnou rutinu události, a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="5e80a-106">If you cannot see the **Properties** window, in **Design** view, right-click the form or control for which you want to create an event handler, and select **Properties**.</span></span>  
  
2. <span data-ttu-id="5e80a-107">V horní části okna **vlastnosti** klikněte na ikonu **události** .</span><span class="sxs-lookup"><span data-stu-id="5e80a-107">On top of the **Properties** window, click the **Events** icon.</span></span>  
  
3. <span data-ttu-id="5e80a-108">Dvakrát klikněte na událost, kterou chcete vytvořit, například na událost `Load`.</span><span class="sxs-lookup"><span data-stu-id="5e80a-108">Double-click the event that you want to create, for example the `Load` event.</span></span>  
  
     <span data-ttu-id="5e80a-109">Vizuál C# vytvoří prázdnou metodu obslužné rutiny události a přidá ji do kódu.</span><span class="sxs-lookup"><span data-stu-id="5e80a-109">Visual C# creates an empty event handler method and adds it to your code.</span></span> <span data-ttu-id="5e80a-110">Případně můžete kód přidat ručně v zobrazení **kódu** .</span><span class="sxs-lookup"><span data-stu-id="5e80a-110">Alternatively you can add the code manually in **Code** view.</span></span> <span data-ttu-id="5e80a-111">Například následující řádky kódu deklaruje metodu obslužné rutiny události, která bude volána, když třída `Form` vyvolá událost `Load`.</span><span class="sxs-lookup"><span data-stu-id="5e80a-111">For example, the following lines of code declare an event handler method that will be called when the `Form` class raises the `Load` event.</span></span>  
  
     [!code-csharp[csProgGuideEvents#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#11)]  
  
     <span data-ttu-id="5e80a-112">Řádek kódu, který je požadován k přihlášení k odběru události, je také automaticky vygenerován v metodě `InitializeComponent` v souboru Form1.Designer.cs v projektu.</span><span class="sxs-lookup"><span data-stu-id="5e80a-112">The line of code that is required to subscribe to the event is also automatically generated in the `InitializeComponent` method in the Form1.Designer.cs file in your project.</span></span> <span data-ttu-id="5e80a-113">Vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="5e80a-113">It resembles this:</span></span>  
  
    ```csharp
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### <a name="to-subscribe-to-events-programmatically"></a><span data-ttu-id="5e80a-114">Programové přihlášení k odběru událostí</span><span class="sxs-lookup"><span data-stu-id="5e80a-114">To subscribe to events programmatically</span></span>  
  
1. <span data-ttu-id="5e80a-115">Definujte metodu obslužné rutiny události, jejíž signatura odpovídá signatuře delegáta události.</span><span class="sxs-lookup"><span data-stu-id="5e80a-115">Define an event handler method whose signature matches the delegate signature for the event.</span></span> <span data-ttu-id="5e80a-116">Například pokud je událost založená na typu delegáta <xref:System.EventHandler>, následující kód představuje zástupnou proceduru metody:</span><span class="sxs-lookup"><span data-stu-id="5e80a-116">For example, if the event is based on the <xref:System.EventHandler> delegate type, the following code represents the method stub:</span></span>  
  
    ```csharp
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2. <span data-ttu-id="5e80a-117">Pomocí operátoru přiřazení sčítání (`+=`) připojte k události obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="5e80a-117">Use the addition assignment operator (`+=`) to attach an event handler to the event.</span></span> <span data-ttu-id="5e80a-118">V následujícím příkladu Předpokládejme, že objekt s názvem `publisher` má událost s názvem `RaiseCustomEvent`.</span><span class="sxs-lookup"><span data-stu-id="5e80a-118">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent`.</span></span> <span data-ttu-id="5e80a-119">Všimněte si, že třída odběratele potřebuje odkaz na třídu vydavatele, aby se přihlásil k odběru jeho událostí.</span><span class="sxs-lookup"><span data-stu-id="5e80a-119">Note that the subscriber class needs a reference to the publisher class in order to subscribe to its events.</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="5e80a-120">Všimněte si, že předchozí syntaxe je v C# 2,0 nová.</span><span class="sxs-lookup"><span data-stu-id="5e80a-120">Note that the previous syntax is new in C# 2.0.</span></span> <span data-ttu-id="5e80a-121">Je přesně stejný jako syntaxe C# 1,0, ve které musí být delegát zapouzdření explicitně vytvořen pomocí klíčového slova `new`:</span><span class="sxs-lookup"><span data-stu-id="5e80a-121">It is exactly equivalent to the C# 1.0 syntax in which the encapsulating delegate must be explicitly created by using the `new` keyword:</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += new CustomEventHandler(HandleCustomEvent);  
    ```  
  
     <span data-ttu-id="5e80a-122">[Výraz lambda](../statements-expressions-operators/lambda-expressions.md) lze také použít k určení obslužné rutiny události:</span><span class="sxs-lookup"><span data-stu-id="5e80a-122">You also can use a [lambda expression](../statements-expressions-operators/lambda-expressions.md) to specify an event handler:</span></span>
  
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
  
### <a name="to-subscribe-to-events-by-using-an-anonymous-method"></a><span data-ttu-id="5e80a-123">Přihlášení k odběru událostí pomocí anonymní metody</span><span class="sxs-lookup"><span data-stu-id="5e80a-123">To subscribe to events by using an anonymous method</span></span>  
  
- <span data-ttu-id="5e80a-124">Pokud nebudete muset odhlásit odběr události později, můžete k události připojit anonymní metodu pomocí operátoru přiřazení sčítání (`+=`).</span><span class="sxs-lookup"><span data-stu-id="5e80a-124">If you will not have to unsubscribe to an event later, you can use the addition assignment operator (`+=`) to attach an anonymous method to the event.</span></span> <span data-ttu-id="5e80a-125">V následujícím příkladu Předpokládejme, že objekt s názvem `publisher` má událost s názvem `RaiseCustomEvent` a že třída `CustomEventArgs` byla také definována tak, aby převedla určitý druh informací o zvláštních událostech.</span><span class="sxs-lookup"><span data-stu-id="5e80a-125">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent` and that a `CustomEventArgs` class has also been defined to carry some kind of specialized event information.</span></span> <span data-ttu-id="5e80a-126">Všimněte si, že třída odběratele potřebuje odkaz na `publisher`, aby se přihlásil k odběru jeho událostí.</span><span class="sxs-lookup"><span data-stu-id="5e80a-126">Note that the subscriber class needs a reference to `publisher` in order to subscribe to its events.</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     <span data-ttu-id="5e80a-127">Je důležité si všimnout, že pokud jste k přihlášení k odběru použili anonymní funkci, nemůžete se k odběru události snadno odhlásit.</span><span class="sxs-lookup"><span data-stu-id="5e80a-127">It is important to notice that you cannot easily unsubscribe from an event if you used an anonymous function to subscribe to it.</span></span> <span data-ttu-id="5e80a-128">Chcete-li zrušit odběr v tomto scénáři, je nutné přejít zpět na kód, kde jste přihlášeni k odběru události, uložit anonymní metodu do proměnné delegáta a poté přidat delegáta události.</span><span class="sxs-lookup"><span data-stu-id="5e80a-128">To unsubscribe in this scenario, it is necessary to go back to the code where you subscribe to the event, store the anonymous method in a delegate variable, and then add the delegate to the event.</span></span> <span data-ttu-id="5e80a-129">Obecně doporučujeme, abyste nepoužívali anonymní funkce pro přihlášení k odběru událostí, pokud budete muset zrušit odběr události v pozdější fázi kódu.</span><span class="sxs-lookup"><span data-stu-id="5e80a-129">In general, we recommend that you do not use anonymous functions to subscribe to events if you will have to unsubscribe from the event at some later point in your code.</span></span> <span data-ttu-id="5e80a-130">Další informace o anonymních funkcích naleznete v tématu [Anonymous Functions](../statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="5e80a-130">For more information about anonymous functions, see [Anonymous Functions](../statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="unsubscribing"></a><span data-ttu-id="5e80a-131">Odhlašování odběru</span><span class="sxs-lookup"><span data-stu-id="5e80a-131">Unsubscribing</span></span>  
 <span data-ttu-id="5e80a-132">Chcete-li zabránit vyvolání obslužné rutiny události při vyvolání události, odhlaste se od události.</span><span class="sxs-lookup"><span data-stu-id="5e80a-132">To prevent your event handler from being invoked when the event is raised, unsubscribe from the event.</span></span> <span data-ttu-id="5e80a-133">Aby nedošlo k nevracení prostředků, měli byste zrušit odběr událostí předtím, než vyřadíte objekt předplatitele.</span><span class="sxs-lookup"><span data-stu-id="5e80a-133">In order to prevent resource leaks, you should unsubscribe from events before you dispose of a subscriber object.</span></span> <span data-ttu-id="5e80a-134">Dokud neprovedete zrušení odběru události, delegát vícesměrového vysílání, který je na události v objektu publikování, odkazuje na delegáta, který zapouzdřuje obslužnou rutinu události odběratele.</span><span class="sxs-lookup"><span data-stu-id="5e80a-134">Until you unsubscribe from an event, the multicast delegate that underlies the event in the publishing object has a reference to the delegate that encapsulates the subscriber's event handler.</span></span> <span data-ttu-id="5e80a-135">Pokud objekt publikování obsahuje tento odkaz, uvolňování paměti neodstraní váš objekt předplatitele.</span><span class="sxs-lookup"><span data-stu-id="5e80a-135">As long as the publishing object holds that reference, garbage collection will not delete your subscriber object.</span></span>  
  
#### <a name="to-unsubscribe-from-an-event"></a><span data-ttu-id="5e80a-136">Zrušení odběru události</span><span class="sxs-lookup"><span data-stu-id="5e80a-136">To unsubscribe from an event</span></span>  
  
- <span data-ttu-id="5e80a-137">K odhlášení odběru události použijte operátor přiřazení odčítání (`-=`):</span><span class="sxs-lookup"><span data-stu-id="5e80a-137">Use the subtraction assignment operator (`-=`) to unsubscribe from an event:</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="5e80a-138">Když se zruší odběr všech předplatitelů z nějaké události, instance události ve třídě vydavatele je nastavená na `null`.</span><span class="sxs-lookup"><span data-stu-id="5e80a-138">When all subscribers have unsubscribed from an event, the event instance in the publisher class is set to `null`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e80a-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5e80a-139">See also</span></span>

- [<span data-ttu-id="5e80a-140">Události</span><span class="sxs-lookup"><span data-stu-id="5e80a-140">Events</span></span>](./index.md)
- [<span data-ttu-id="5e80a-141">event</span><span class="sxs-lookup"><span data-stu-id="5e80a-141">event</span></span>](../../language-reference/keywords/event.md)
- [<span data-ttu-id="5e80a-142">Jak publikovat události, které jsou v souladu s pokyny pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5e80a-142">How to publish events that conform to .NET Framework Guidelines</span></span>](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)
- [<span data-ttu-id="5e80a-143">-a-= – operátory</span><span class="sxs-lookup"><span data-stu-id="5e80a-143">- and -= operators</span></span>](../../language-reference/operators/subtraction-operator.md)
- [<span data-ttu-id="5e80a-144">+ a + = – operátory</span><span class="sxs-lookup"><span data-stu-id="5e80a-144">+ and += operators</span></span>](../../language-reference/operators/addition-operator.md)
