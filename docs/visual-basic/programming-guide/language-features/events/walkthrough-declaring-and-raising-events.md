---
title: Deklarace a vyvolávání událostí (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], events
- events [Visual Basic], walkthroughs
- declaring events [Visual Basic], walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events [Visual Basic], walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
ms.openlocfilehash: cab6c90947eae8abeb9387535eadb2f89e71454a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59320688"
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a><span data-ttu-id="70bb4-102">Návod: Deklarace a vyvolávání událostí (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70bb4-102">Walkthrough: Declaring and Raising Events (Visual Basic)</span></span>
<span data-ttu-id="70bb4-103">Tento návod ukazuje, jak deklarovat a vyvolávání událostí pro třídu s názvem `Widget`.</span><span class="sxs-lookup"><span data-stu-id="70bb4-103">This walkthrough demonstrates how to declare and raise events for a class named `Widget`.</span></span> <span data-ttu-id="70bb4-104">Po dokončení kroků se můžete chtít přečíst téma doprovodná [názorný postup: Zpracování událostí](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), který ukazuje, jak používat události z `Widget` objekty poskytnout informace o stavu v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="70bb4-104">After you complete the steps, you might want to read the companion topic, [Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), which shows how to use events from `Widget` objects to provide status information in an application.</span></span>  
  
## <a name="the-widget-class"></a><span data-ttu-id="70bb4-105">Třída widgetu</span><span class="sxs-lookup"><span data-stu-id="70bb4-105">The Widget Class</span></span>  
 <span data-ttu-id="70bb4-106">Předpokládejme, že máte nyní `Widget` třídy.</span><span class="sxs-lookup"><span data-stu-id="70bb4-106">Assume for the moment that you have a `Widget` class.</span></span> <span data-ttu-id="70bb4-107">Vaše `Widget` třída nemá metodu, která může trvat dlouhou dobu spuštění, a chcete, aby vaše aplikace bude moct vyvěste určitého druhu dokončení indikátoru.</span><span class="sxs-lookup"><span data-stu-id="70bb4-107">Your `Widget` class has a method that can take a long time to execute, and you want your application to be able to put up some kind of completion indicator.</span></span>  
  
 <span data-ttu-id="70bb4-108">Samozřejmě můžete provést `Widget` objekt zobrazit dokončeno % dialogovému oknu, ale pak jste by zablokuje se tohoto dialogového okna v každém projektu, ve které jste použili `Widget` třídy.</span><span class="sxs-lookup"><span data-stu-id="70bb4-108">Of course, you could make the `Widget` object show a percent-complete dialog box, but then you would be stuck with that dialog box in every project in which you used the `Widget` class.</span></span> <span data-ttu-id="70bb4-109">Dobré zásady navrhování objektu je umožnit aplikaci, která používá popisovač objektu uživatelského rozhraní – Pokud je účelem objektu ke správě pole formuláře nebo dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="70bb4-109">A good principle of object design is to let the application that uses an object handle the user interface—unless the whole purpose of the object is to manage a form or dialog box.</span></span>  
  
 <span data-ttu-id="70bb4-110">Účelem `Widget` je a provádět další úlohy, tak, aby byl lepší přidat `PercentDone` událostí a umožňují proceduru, která volá `Widget`uživatele metody zpracovávají, události a zobrazení stavu aktualizace.</span><span class="sxs-lookup"><span data-stu-id="70bb4-110">The purpose of `Widget` is to perform other tasks, so it is better to add a `PercentDone` event and let the procedure that calls `Widget`'s methods handle that event and display status updates.</span></span> <span data-ttu-id="70bb4-111">`PercentDone` Události můžete taky mělo poskytovat mechanismus pro zrušení úkolu.</span><span class="sxs-lookup"><span data-stu-id="70bb4-111">The `PercentDone` event can also provide a mechanism for canceling the task.</span></span>  
  
#### <a name="to-build-the-code-example-for-this-topic"></a><span data-ttu-id="70bb4-112">Chcete-li vytvořit příklad kódu pro toto téma</span><span class="sxs-lookup"><span data-stu-id="70bb4-112">To build the code example for this topic</span></span>  
  
1. <span data-ttu-id="70bb4-113">Otevřete nový projekt aplikace Windows jazyka Visual Basic a vytvořte formulář s názvem `Form1`.</span><span class="sxs-lookup"><span data-stu-id="70bb4-113">Open a new Visual Basic Windows Application project and create a form named `Form1`.</span></span>  
  
2. <span data-ttu-id="70bb4-114">Přidání dvou tlačítek a popisek pro `Form1`.</span><span class="sxs-lookup"><span data-stu-id="70bb4-114">Add two buttons and a label to `Form1`.</span></span>  
  
3. <span data-ttu-id="70bb4-115">Jak je znázorněno v následující tabulce, pojmenujte objekty.</span><span class="sxs-lookup"><span data-stu-id="70bb4-115">Name the objects as shown in the following table.</span></span>  
  
    |<span data-ttu-id="70bb4-116">Objekt</span><span class="sxs-lookup"><span data-stu-id="70bb4-116">Object</span></span>|<span data-ttu-id="70bb4-117">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="70bb4-117">Property</span></span>|<span data-ttu-id="70bb4-118">Nastavení</span><span class="sxs-lookup"><span data-stu-id="70bb4-118">Setting</span></span>|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|<span data-ttu-id="70bb4-119">Spouštěcí úkol</span><span class="sxs-lookup"><span data-stu-id="70bb4-119">Start Task</span></span>|  
    |`Button2`|`Text`|<span data-ttu-id="70bb4-120">Zrušit</span><span class="sxs-lookup"><span data-stu-id="70bb4-120">Cancel</span></span>|  
    |`Label`|<span data-ttu-id="70bb4-121">`(Name)`, `Text`</span><span class="sxs-lookup"><span data-stu-id="70bb4-121">`(Name)`, `Text`</span></span>|<span data-ttu-id="70bb4-122">lblPercentDone, 0</span><span class="sxs-lookup"><span data-stu-id="70bb4-122">lblPercentDone, 0</span></span>|  
  
4. <span data-ttu-id="70bb4-123">Na **projektu** nabídce zvolte **přidat třídu** přidat třídu s názvem `Widget.vb` do projektu.</span><span class="sxs-lookup"><span data-stu-id="70bb4-123">On the **Project** menu, choose **Add Class** to add a class named `Widget.vb` to the project.</span></span>  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a><span data-ttu-id="70bb4-124">Chcete-li deklarovat události pro třídu widgetu</span><span class="sxs-lookup"><span data-stu-id="70bb4-124">To declare an event for the Widget class</span></span>  
  
-   <span data-ttu-id="70bb4-125">Použití `Event` – klíčové slovo pro deklaraci události v `Widget` třídy.</span><span class="sxs-lookup"><span data-stu-id="70bb4-125">Use the `Event` keyword to declare an event in the `Widget` class.</span></span> <span data-ttu-id="70bb4-126">Všimněte si, že událost může mít `ByVal` a `ByRef` argumenty, jako `Widget`společnosti `PercentDone` ukazuje událostí:</span><span class="sxs-lookup"><span data-stu-id="70bb4-126">Note that an event can have `ByVal` and `ByRef` arguments, as `Widget`'s `PercentDone` event demonstrates:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#1)]  
  
 <span data-ttu-id="70bb4-127">Když se obdrží objektem neúčastnícím se volání `PercentDone` událostí, `Percent` argument obsahuje procento dokončení úkolu.</span><span class="sxs-lookup"><span data-stu-id="70bb4-127">When the calling object receives a `PercentDone` event, the `Percent` argument contains the percentage of the task that is complete.</span></span> <span data-ttu-id="70bb4-128">`Cancel` Argument může být nastaven na `True` zrušit metodu, která vyvolala událost.</span><span class="sxs-lookup"><span data-stu-id="70bb4-128">The `Cancel` argument can be set to `True` to cancel the method that raised the event.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="70bb4-129">Je možné deklarovat argumenty události, stejně jako argumenty procedur, s následujícími výjimkami: Události nemohou mít `Optional` nebo `ParamArray` argumenty a události nemají návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="70bb4-129">You can declare event arguments just as you do arguments of procedures, with the following exceptions: Events cannot have `Optional` or `ParamArray` arguments, and events do not have return values.</span></span>  
  
 <span data-ttu-id="70bb4-130">`PercentDone` Vyvolá událost `LongTask` metodu `Widget` třídy.</span><span class="sxs-lookup"><span data-stu-id="70bb4-130">The `PercentDone` event is raised by the `LongTask` method of the `Widget` class.</span></span> <span data-ttu-id="70bb4-131">`LongTask` přebírá dva argumenty: doba metodu předstírá, že se to práci a minimální časový interval před `LongTask` možné zvýšit `PercentDone` událostí.</span><span class="sxs-lookup"><span data-stu-id="70bb4-131">`LongTask` takes two arguments: the length of time the method pretends to be doing work, and the minimum time interval before `LongTask` pauses to raise the `PercentDone` event.</span></span>  
  
#### <a name="to-raise-the-percentdone-event"></a><span data-ttu-id="70bb4-132">Aby se vyvolala událost PercentDone</span><span class="sxs-lookup"><span data-stu-id="70bb4-132">To raise the PercentDone event</span></span>  
  
1. <span data-ttu-id="70bb4-133">Pro zjednodušení přístupu k `Timer` přidat vlastnost použitou touto třídou `Imports` příkaz do horní části deklarace třídy modulu, výše `Class Widget` příkazu.</span><span class="sxs-lookup"><span data-stu-id="70bb4-133">To simplify access to the `Timer` property used by this class, add an `Imports` statement to the top of the declarations section of your class module, above the `Class Widget` statement.</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#2)]  
  
2. <span data-ttu-id="70bb4-134">Přidejte následující kód, který `Widget` třídy:</span><span class="sxs-lookup"><span data-stu-id="70bb4-134">Add the following code to the `Widget` class:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#3)]  
  
 <span data-ttu-id="70bb4-135">Když vaše aplikace volá `LongTask` metody `Widget` třídy vyvolá `PercentDone` událost každých `MinimumInterval` sekund.</span><span class="sxs-lookup"><span data-stu-id="70bb4-135">When your application calls the `LongTask` method, the `Widget` class raises the `PercentDone` event every `MinimumInterval` seconds.</span></span> <span data-ttu-id="70bb4-136">Po návratu události `LongTask` kontroluje, jestli `Cancel` argument byl nastaven na `True`.</span><span class="sxs-lookup"><span data-stu-id="70bb4-136">When the event returns, `LongTask` checks to see if the `Cancel` argument was set to `True`.</span></span>  
  
 <span data-ttu-id="70bb4-137">Zde je potřeba několik omezení.</span><span class="sxs-lookup"><span data-stu-id="70bb4-137">A few disclaimers are necessary here.</span></span> <span data-ttu-id="70bb4-138">Pro zjednodušení `LongTask` postupu se předpokládá můžete předem vědět, jak dlouho bude trvat úkolu.</span><span class="sxs-lookup"><span data-stu-id="70bb4-138">For simplicity, the `LongTask` procedure assumes you know in advance how long the task will take.</span></span> <span data-ttu-id="70bb4-139">To platí téměř nikdy.</span><span class="sxs-lookup"><span data-stu-id="70bb4-139">This is almost never the case.</span></span> <span data-ttu-id="70bb4-140">Dělení do bloků velikosti i úlohy může být složité a často to nejdůležitější uživatelů je jednoduše množství času, který uplyne, než se jim zobrazí jako ukazatel toho, že se něco děje.</span><span class="sxs-lookup"><span data-stu-id="70bb4-140">Dividing tasks into chunks of even size can be difficult, and often what matters most to users is simply the amount of time that passes before they get an indication that something is happening.</span></span>  
  
 <span data-ttu-id="70bb4-141">Může mít další vadou nanese v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="70bb4-141">You may have spotted another flaw in this sample.</span></span> <span data-ttu-id="70bb4-142">`Timer` Vlastnost vrátí počet sekund, které uplynuly od půlnoci; proto aplikace zasekne, pokud je spuštěna těsně před půlnocí.</span><span class="sxs-lookup"><span data-stu-id="70bb4-142">The `Timer` property returns the number of seconds that have passed since midnight; therefore, the application gets stuck if it is started just before midnight.</span></span> <span data-ttu-id="70bb4-143">Více opatrní přístup k měření doby by přijmout podmínky hranice takovou situaci v úvahu, nebo jim zabránit zcela, například pomocí vlastnosti `Now`.</span><span class="sxs-lookup"><span data-stu-id="70bb4-143">A more careful approach to measuring time would take boundary conditions such as this into consideration, or avoid them altogether, using properties such as `Now`.</span></span>  
  
 <span data-ttu-id="70bb4-144">Teď, když `Widget` třída může vyvolat události, můžete přesunout do dalšího názorného postupu.</span><span class="sxs-lookup"><span data-stu-id="70bb4-144">Now that the `Widget` class can raise events, you can move to the next walkthrough.</span></span> <span data-ttu-id="70bb4-145">[Návod: Zpracování událostí](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) ukazuje, jak používat `WithEvents` přidružení obslužné rutiny události s `PercentDone` událostí.</span><span class="sxs-lookup"><span data-stu-id="70bb4-145">[Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) demonstrates how to use `WithEvents` to associate an event handler with the `PercentDone` event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70bb4-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="70bb4-146">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>
- <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>
- [<span data-ttu-id="70bb4-147">Návod: Zpracování událostí</span><span class="sxs-lookup"><span data-stu-id="70bb4-147">Walkthrough: Handling Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)
- [<span data-ttu-id="70bb4-148">Události</span><span class="sxs-lookup"><span data-stu-id="70bb4-148">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
