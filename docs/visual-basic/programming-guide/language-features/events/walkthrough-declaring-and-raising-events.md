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
ms.openlocfilehash: 20e2b0efbf40597049c515134f408927f18d5603
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956337"
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a><span data-ttu-id="c26dc-102">Návod: Deklarace a vyvolávání událostí (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c26dc-102">Walkthrough: Declaring and Raising Events (Visual Basic)</span></span>
<span data-ttu-id="c26dc-103">Tento návod ukazuje, jak deklarovat a vyvolat události pro třídu s názvem `Widget`.</span><span class="sxs-lookup"><span data-stu-id="c26dc-103">This walkthrough demonstrates how to declare and raise events for a class named `Widget`.</span></span> <span data-ttu-id="c26dc-104">Po dokončení tohoto postupu si můžete přečíst doprovodný článek, [Návod: Zpracování událostí](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), které ukazují, jak používat události z `Widget` objektů k poskytnutí informací o stavu v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c26dc-104">After you complete the steps, you might want to read the companion topic, [Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), which shows how to use events from `Widget` objects to provide status information in an application.</span></span>  
  
## <a name="the-widget-class"></a><span data-ttu-id="c26dc-105">Widget – třída</span><span class="sxs-lookup"><span data-stu-id="c26dc-105">The Widget Class</span></span>  
 <span data-ttu-id="c26dc-106">Předpokládejme, kdy máte `Widget` třídu.</span><span class="sxs-lookup"><span data-stu-id="c26dc-106">Assume for the moment that you have a `Widget` class.</span></span> <span data-ttu-id="c26dc-107">Vaše `Widget` třída má metodu, která může trvat dlouhou dobu, a chcete, aby aplikace mohla sestavit nějaký typ indikátoru dokončení.</span><span class="sxs-lookup"><span data-stu-id="c26dc-107">Your `Widget` class has a method that can take a long time to execute, and you want your application to be able to put up some kind of completion indicator.</span></span>  
  
 <span data-ttu-id="c26dc-108">Samozřejmě je možné nastavit, aby se `Widget` v objektu zobrazilo dialogové okno procento dokončení, ale pak byste zablokovali toto dialogové okno v každém projektu, ve kterém jste `Widget` použili třídu.</span><span class="sxs-lookup"><span data-stu-id="c26dc-108">Of course, you could make the `Widget` object show a percent-complete dialog box, but then you would be stuck with that dialog box in every project in which you used the `Widget` class.</span></span> <span data-ttu-id="c26dc-109">Dobrým principem návrhu objektu je umožnit aplikaci, která používá objekt, zpracovat uživatelské rozhraní – Pokud celý účel objektu není spravovat formulář nebo dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="c26dc-109">A good principle of object design is to let the application that uses an object handle the user interface—unless the whole purpose of the object is to manage a form or dialog box.</span></span>  
  
 <span data-ttu-id="c26dc-110">Účelem `Widget` je provést jiné úkoly, takže je lepší `PercentDone` přidat událost a nechat proceduru, která volá `Widget`metody, zpracovávat tuto událost a zobrazovat aktualizace stavu.</span><span class="sxs-lookup"><span data-stu-id="c26dc-110">The purpose of `Widget` is to perform other tasks, so it is better to add a `PercentDone` event and let the procedure that calls `Widget`'s methods handle that event and display status updates.</span></span> <span data-ttu-id="c26dc-111">`PercentDone` Událost může také poskytovat mechanismus pro zrušení úlohy.</span><span class="sxs-lookup"><span data-stu-id="c26dc-111">The `PercentDone` event can also provide a mechanism for canceling the task.</span></span>  
  
#### <a name="to-build-the-code-example-for-this-topic"></a><span data-ttu-id="c26dc-112">Postup sestavení příkladu kódu pro toto téma</span><span class="sxs-lookup"><span data-stu-id="c26dc-112">To build the code example for this topic</span></span>  
  
1. <span data-ttu-id="c26dc-113">Otevřete nový Visual Basic projekt aplikace pro Windows a vytvořte formulář s názvem `Form1`.</span><span class="sxs-lookup"><span data-stu-id="c26dc-113">Open a new Visual Basic Windows Application project and create a form named `Form1`.</span></span>  
  
2. <span data-ttu-id="c26dc-114">Přidejte dvě tlačítka a popisky do `Form1`.</span><span class="sxs-lookup"><span data-stu-id="c26dc-114">Add two buttons and a label to `Form1`.</span></span>  
  
3. <span data-ttu-id="c26dc-115">Pojmenujte objekty, jak je uvedeno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="c26dc-115">Name the objects as shown in the following table.</span></span>  
  
    |<span data-ttu-id="c26dc-116">Objekt</span><span class="sxs-lookup"><span data-stu-id="c26dc-116">Object</span></span>|<span data-ttu-id="c26dc-117">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="c26dc-117">Property</span></span>|<span data-ttu-id="c26dc-118">Nastavení</span><span class="sxs-lookup"><span data-stu-id="c26dc-118">Setting</span></span>|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|<span data-ttu-id="c26dc-119">Spustit úkol</span><span class="sxs-lookup"><span data-stu-id="c26dc-119">Start Task</span></span>|  
    |`Button2`|`Text`|<span data-ttu-id="c26dc-120">Zrušit</span><span class="sxs-lookup"><span data-stu-id="c26dc-120">Cancel</span></span>|  
    |`Label`|<span data-ttu-id="c26dc-121">`(Name)`, `Text`</span><span class="sxs-lookup"><span data-stu-id="c26dc-121">`(Name)`, `Text`</span></span>|<span data-ttu-id="c26dc-122">lblPercentDone, 0</span><span class="sxs-lookup"><span data-stu-id="c26dc-122">lblPercentDone, 0</span></span>|  
  
4. <span data-ttu-id="c26dc-123">V nabídce **projekt** vyberte možnost **Přidat třídu** a přidejte do projektu třídu s `Widget.vb` názvem.</span><span class="sxs-lookup"><span data-stu-id="c26dc-123">On the **Project** menu, choose **Add Class** to add a class named `Widget.vb` to the project.</span></span>  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a><span data-ttu-id="c26dc-124">Deklarace události pro třídu widgetu</span><span class="sxs-lookup"><span data-stu-id="c26dc-124">To declare an event for the Widget class</span></span>  
  
- <span data-ttu-id="c26dc-125">Použijte klíčové slovo k deklaraci události `Widget` ve třídě. `Event`</span><span class="sxs-lookup"><span data-stu-id="c26dc-125">Use the `Event` keyword to declare an event in the `Widget` class.</span></span> <span data-ttu-id="c26dc-126">Všimněte si, že událost může `ByVal` mít `ByRef` argumenty a a `Widget`jako `PercentDone` událost ukazuje:</span><span class="sxs-lookup"><span data-stu-id="c26dc-126">Note that an event can have `ByVal` and `ByRef` arguments, as `Widget`'s `PercentDone` event demonstrates:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#1)]  
  
 <span data-ttu-id="c26dc-127">Když volající objekt obdrží `PercentDone` událost `Percent` , argument obsahuje procento dokončeného úkolu.</span><span class="sxs-lookup"><span data-stu-id="c26dc-127">When the calling object receives a `PercentDone` event, the `Percent` argument contains the percentage of the task that is complete.</span></span> <span data-ttu-id="c26dc-128">Argument lze nastavit na `True` hodnotu, chcete-li zrušit metodu, která událost vyvolala. `Cancel`</span><span class="sxs-lookup"><span data-stu-id="c26dc-128">The `Cancel` argument can be set to `True` to cancel the method that raised the event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c26dc-129">Argumenty události lze deklarovat stejně jako argumenty procedur, s následujícími výjimkami: Události nemohou mít `Optional` argumenty `ParamArray` nebo a události neobsahují návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c26dc-129">You can declare event arguments just as you do arguments of procedures, with the following exceptions: Events cannot have `Optional` or `ParamArray` arguments, and events do not have return values.</span></span>  
  
 <span data-ttu-id="c26dc-130">Událost je vyvolána `LongTask` metodou`Widget`třídy. `PercentDone`</span><span class="sxs-lookup"><span data-stu-id="c26dc-130">The `PercentDone` event is raised by the `LongTask` method of the `Widget` class.</span></span> <span data-ttu-id="c26dc-131">`LongTask`přebírá dva argumenty: dobu, po kterou metoda zamýšlí pracovat, a minimální časový interval před `LongTask` pauzou pro `PercentDone` vyvolání události.</span><span class="sxs-lookup"><span data-stu-id="c26dc-131">`LongTask` takes two arguments: the length of time the method pretends to be doing work, and the minimum time interval before `LongTask` pauses to raise the `PercentDone` event.</span></span>  
  
#### <a name="to-raise-the-percentdone-event"></a><span data-ttu-id="c26dc-132">Vyvolání události PercentDone</span><span class="sxs-lookup"><span data-stu-id="c26dc-132">To raise the PercentDone event</span></span>  
  
1. <span data-ttu-id="c26dc-133">Chcete-li zjednodušit `Timer` přístup k vlastnosti, kterou používá tato třída `Imports` , přidejte příkaz na začátek oddílu deklarace v modulu `Class Widget` třídy nad rámec příkazu.</span><span class="sxs-lookup"><span data-stu-id="c26dc-133">To simplify access to the `Timer` property used by this class, add an `Imports` statement to the top of the declarations section of your class module, above the `Class Widget` statement.</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#2)]  
  
2. <span data-ttu-id="c26dc-134">Do `Widget` třídy přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="c26dc-134">Add the following code to the `Widget` class:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#3)]  
  
 <span data-ttu-id="c26dc-135">Když vaše aplikace `LongTask` volá metodu `Widget` , třída vyvolá `PercentDone` událost každou `MinimumInterval` sekundou.</span><span class="sxs-lookup"><span data-stu-id="c26dc-135">When your application calls the `LongTask` method, the `Widget` class raises the `PercentDone` event every `MinimumInterval` seconds.</span></span> <span data-ttu-id="c26dc-136">Jakmile se událost vrátí, `LongTask` zkontroluje, `Cancel` zda byl argument nastaven na `True`hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c26dc-136">When the event returns, `LongTask` checks to see if the `Cancel` argument was set to `True`.</span></span>  
  
 <span data-ttu-id="c26dc-137">Tady je potřeba pár omezení.</span><span class="sxs-lookup"><span data-stu-id="c26dc-137">A few disclaimers are necessary here.</span></span> <span data-ttu-id="c26dc-138">V zájmu jednoduchosti `LongTask` postup předpokládá, že jste předem věděli, jak dlouho bude úkol trvat.</span><span class="sxs-lookup"><span data-stu-id="c26dc-138">For simplicity, the `LongTask` procedure assumes you know in advance how long the task will take.</span></span> <span data-ttu-id="c26dc-139">To téměř nikdy neplatí.</span><span class="sxs-lookup"><span data-stu-id="c26dc-139">This is almost never the case.</span></span> <span data-ttu-id="c26dc-140">Rozdělování úkolů do bloků rovnoměrné velikosti může být obtížné a často se jedná o většinu uživatelů, což je jednoduše doba, která se předá před tím, než získá indikaci, že se něco děje.</span><span class="sxs-lookup"><span data-stu-id="c26dc-140">Dividing tasks into chunks of even size can be difficult, and often what matters most to users is simply the amount of time that passes before they get an indication that something is happening.</span></span>  
  
 <span data-ttu-id="c26dc-141">V této ukázce jste pravděpodobně spottedi jinou chybu.</span><span class="sxs-lookup"><span data-stu-id="c26dc-141">You may have spotted another flaw in this sample.</span></span> <span data-ttu-id="c26dc-142">`Timer` Vlastnost vrátí počet sekund, které byly předány od půlnoci. proto je aplikace zablokovaná, pokud je spuštěna těsně před půlnocí.</span><span class="sxs-lookup"><span data-stu-id="c26dc-142">The `Timer` property returns the number of seconds that have passed since midnight; therefore, the application gets stuck if it is started just before midnight.</span></span> <span data-ttu-id="c26dc-143">Lepším přístupem k měření času by došlo k tomu, že se jedná o podmínky pro hranici, jako je to vhodné, nebo se `Now`jim vyhnete úplně, a to pomocí vlastností jako.</span><span class="sxs-lookup"><span data-stu-id="c26dc-143">A more careful approach to measuring time would take boundary conditions such as this into consideration, or avoid them altogether, using properties such as `Now`.</span></span>  
  
 <span data-ttu-id="c26dc-144">Teď, `Widget` když třída může vyvolávat události, můžete přejít k dalšímu návodu.</span><span class="sxs-lookup"><span data-stu-id="c26dc-144">Now that the `Widget` class can raise events, you can move to the next walkthrough.</span></span> <span data-ttu-id="c26dc-145">[Návod: Zpracování událostí](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) ukazuje, jak použít `WithEvents` k přidružení obslužné rutiny `PercentDone` události k události.</span><span class="sxs-lookup"><span data-stu-id="c26dc-145">[Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) demonstrates how to use `WithEvents` to associate an event handler with the `PercentDone` event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c26dc-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c26dc-146">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>
- <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>
- [<span data-ttu-id="c26dc-147">Návod: Zpracování událostí</span><span class="sxs-lookup"><span data-stu-id="c26dc-147">Walkthrough: Handling Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)
- [<span data-ttu-id="c26dc-148">Události</span><span class="sxs-lookup"><span data-stu-id="c26dc-148">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
