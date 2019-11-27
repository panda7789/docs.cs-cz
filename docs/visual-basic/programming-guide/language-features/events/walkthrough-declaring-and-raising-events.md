---
title: Deklarace a vyvolávání událostí
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], events
- events [Visual Basic], walkthroughs
- declaring events [Visual Basic], walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events [Visual Basic], walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
ms.openlocfilehash: 6f4c303604f9cf55b4ecd500636e0d2772b6234c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345090"
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a><span data-ttu-id="51899-102">Návod: Deklarace a vyvolávání událostí (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="51899-102">Walkthrough: Declaring and Raising Events (Visual Basic)</span></span>
<span data-ttu-id="51899-103">Tento návod ukazuje, jak deklarovat a vyvolat události pro třídu s názvem `Widget`.</span><span class="sxs-lookup"><span data-stu-id="51899-103">This walkthrough demonstrates how to declare and raise events for a class named `Widget`.</span></span> <span data-ttu-id="51899-104">Po dokončení kroků si můžete přečíst doprovodné téma, [Návod: zpracování událostí](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), které ukazuje, jak používat události z `Widget` objektů k poskytnutí informací o stavu v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="51899-104">After you complete the steps, you might want to read the companion topic, [Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), which shows how to use events from `Widget` objects to provide status information in an application.</span></span>  
  
## <a name="the-widget-class"></a><span data-ttu-id="51899-105">Widget – třída</span><span class="sxs-lookup"><span data-stu-id="51899-105">The Widget Class</span></span>  
 <span data-ttu-id="51899-106">Předpokládejme, kdy máte `Widget` třídu.</span><span class="sxs-lookup"><span data-stu-id="51899-106">Assume for the moment that you have a `Widget` class.</span></span> <span data-ttu-id="51899-107">Vaše třída `Widget` má metodu, která může trvat dlouhou dobu, a chcete, aby aplikace mohla sestavit nějaký typ indikátoru dokončení.</span><span class="sxs-lookup"><span data-stu-id="51899-107">Your `Widget` class has a method that can take a long time to execute, and you want your application to be able to put up some kind of completion indicator.</span></span>  
  
 <span data-ttu-id="51899-108">Samozřejmě můžete nastavit, aby objekt `Widget` zobrazoval dialogové okno procento dokončení, ale pak byste zablokovali toto dialogové okno v každém projektu, ve kterém jste použili třídu `Widget`.</span><span class="sxs-lookup"><span data-stu-id="51899-108">Of course, you could make the `Widget` object show a percent-complete dialog box, but then you would be stuck with that dialog box in every project in which you used the `Widget` class.</span></span> <span data-ttu-id="51899-109">Dobrým principem návrhu objektu je umožnit aplikaci, která používá objekt, zpracovat uživatelské rozhraní – Pokud celý účel objektu není spravovat formulář nebo dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="51899-109">A good principle of object design is to let the application that uses an object handle the user interface—unless the whole purpose of the object is to manage a form or dialog box.</span></span>  
  
 <span data-ttu-id="51899-110">Účelem `Widget` je provést jiné úkoly, takže je lepší přidat událost `PercentDone` a nechat proceduru, která volá metody `Widget`, zpracovávat tyto události a zobrazovat aktualizace stavu.</span><span class="sxs-lookup"><span data-stu-id="51899-110">The purpose of `Widget` is to perform other tasks, so it is better to add a `PercentDone` event and let the procedure that calls `Widget`'s methods handle that event and display status updates.</span></span> <span data-ttu-id="51899-111">Událost `PercentDone` může také poskytovat mechanismus pro zrušení úlohy.</span><span class="sxs-lookup"><span data-stu-id="51899-111">The `PercentDone` event can also provide a mechanism for canceling the task.</span></span>  
  
#### <a name="to-build-the-code-example-for-this-topic"></a><span data-ttu-id="51899-112">Postup sestavení příkladu kódu pro toto téma</span><span class="sxs-lookup"><span data-stu-id="51899-112">To build the code example for this topic</span></span>  
  
1. <span data-ttu-id="51899-113">Otevřete nový Visual Basic projekt aplikace pro Windows a vytvořte formulář s názvem `Form1`.</span><span class="sxs-lookup"><span data-stu-id="51899-113">Open a new Visual Basic Windows Application project and create a form named `Form1`.</span></span>  
  
2. <span data-ttu-id="51899-114">Přidejte dvě tlačítka a popisek pro `Form1`.</span><span class="sxs-lookup"><span data-stu-id="51899-114">Add two buttons and a label to `Form1`.</span></span>  
  
3. <span data-ttu-id="51899-115">Pojmenujte objekty, jak je uvedeno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="51899-115">Name the objects as shown in the following table.</span></span>  
  
    |<span data-ttu-id="51899-116">Objekt</span><span class="sxs-lookup"><span data-stu-id="51899-116">Object</span></span>|<span data-ttu-id="51899-117">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="51899-117">Property</span></span>|<span data-ttu-id="51899-118">Nastavení</span><span class="sxs-lookup"><span data-stu-id="51899-118">Setting</span></span>|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|<span data-ttu-id="51899-119">Spustit úkol</span><span class="sxs-lookup"><span data-stu-id="51899-119">Start Task</span></span>|  
    |`Button2`|`Text`|<span data-ttu-id="51899-120">Zrušit</span><span class="sxs-lookup"><span data-stu-id="51899-120">Cancel</span></span>|  
    |`Label`|<span data-ttu-id="51899-121">`(Name)``Text`</span><span class="sxs-lookup"><span data-stu-id="51899-121">`(Name)`, `Text`</span></span>|<span data-ttu-id="51899-122">lblPercentDone, 0</span><span class="sxs-lookup"><span data-stu-id="51899-122">lblPercentDone, 0</span></span>|  
  
4. <span data-ttu-id="51899-123">V nabídce **projekt** vyberte možnost **Přidat třídu** a přidejte do projektu třídu s názvem `Widget.vb`.</span><span class="sxs-lookup"><span data-stu-id="51899-123">On the **Project** menu, choose **Add Class** to add a class named `Widget.vb` to the project.</span></span>  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a><span data-ttu-id="51899-124">Deklarace události pro třídu widgetu</span><span class="sxs-lookup"><span data-stu-id="51899-124">To declare an event for the Widget class</span></span>  
  
- <span data-ttu-id="51899-125">Použijte klíčové slovo `Event` k deklaraci události ve třídě `Widget`.</span><span class="sxs-lookup"><span data-stu-id="51899-125">Use the `Event` keyword to declare an event in the `Widget` class.</span></span> <span data-ttu-id="51899-126">Všimněte si, že událost může mít argumenty `ByVal` a `ByRef`, jak demonstruje `Widget``PercentDone` událost:</span><span class="sxs-lookup"><span data-stu-id="51899-126">Note that an event can have `ByVal` and `ByRef` arguments, as `Widget`'s `PercentDone` event demonstrates:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#1)]  
  
 <span data-ttu-id="51899-127">Když volající objekt obdrží událost `PercentDone`, argument `Percent` obsahuje procento dokončeného úkolu.</span><span class="sxs-lookup"><span data-stu-id="51899-127">When the calling object receives a `PercentDone` event, the `Percent` argument contains the percentage of the task that is complete.</span></span> <span data-ttu-id="51899-128">Argument `Cancel` lze nastavit na hodnotu `True`, aby bylo možné zrušit metodu, která událost vyvolala.</span><span class="sxs-lookup"><span data-stu-id="51899-128">The `Cancel` argument can be set to `True` to cancel the method that raised the event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="51899-129">Argumenty události lze deklarovat stejně jako argumenty procedur, s následujícími výjimkami: události nemohou mít `Optional` ani `ParamArray` argumenty a události nemají návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="51899-129">You can declare event arguments just as you do arguments of procedures, with the following exceptions: Events cannot have `Optional` or `ParamArray` arguments, and events do not have return values.</span></span>  
  
 <span data-ttu-id="51899-130">Událost `PercentDone` je vyvolána metodou `LongTask` třídy `Widget`.</span><span class="sxs-lookup"><span data-stu-id="51899-130">The `PercentDone` event is raised by the `LongTask` method of the `Widget` class.</span></span> <span data-ttu-id="51899-131">`LongTask` přebírá dva argumenty: dobu, po kterou metoda zamýšlí pracovat, a minimální časový interval před tím, než `LongTask` pozastavení vyvolá událost `PercentDone`.</span><span class="sxs-lookup"><span data-stu-id="51899-131">`LongTask` takes two arguments: the length of time the method pretends to be doing work, and the minimum time interval before `LongTask` pauses to raise the `PercentDone` event.</span></span>  
  
#### <a name="to-raise-the-percentdone-event"></a><span data-ttu-id="51899-132">Vyvolání události PercentDone</span><span class="sxs-lookup"><span data-stu-id="51899-132">To raise the PercentDone event</span></span>  
  
1. <span data-ttu-id="51899-133">Chcete-li zjednodušit přístup k vlastnosti `Timer` používané touto třídou, přidejte příkaz `Imports` na začátek oddílu deklarace v rámci vašeho modulu třídy, nad příkaz `Class Widget`.</span><span class="sxs-lookup"><span data-stu-id="51899-133">To simplify access to the `Timer` property used by this class, add an `Imports` statement to the top of the declarations section of your class module, above the `Class Widget` statement.</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#2)]  
  
2. <span data-ttu-id="51899-134">Do `Widget` třídy přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="51899-134">Add the following code to the `Widget` class:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#3)]  
  
 <span data-ttu-id="51899-135">Když vaše aplikace volá metodu `LongTask`, třída `Widget` vyvolá událost `PercentDone` každých `MinimumInterval` sekund.</span><span class="sxs-lookup"><span data-stu-id="51899-135">When your application calls the `LongTask` method, the `Widget` class raises the `PercentDone` event every `MinimumInterval` seconds.</span></span> <span data-ttu-id="51899-136">Po návratu události `LongTask` zkontroluje, zda byl argument `Cancel` nastaven na hodnotu `True`.</span><span class="sxs-lookup"><span data-stu-id="51899-136">When the event returns, `LongTask` checks to see if the `Cancel` argument was set to `True`.</span></span>  
  
 <span data-ttu-id="51899-137">Tady je potřeba pár omezení.</span><span class="sxs-lookup"><span data-stu-id="51899-137">A few disclaimers are necessary here.</span></span> <span data-ttu-id="51899-138">Pro zjednodušení `LongTask`ý postup předpokládá, že jste předem věděli, jak dlouho bude úkol trvat.</span><span class="sxs-lookup"><span data-stu-id="51899-138">For simplicity, the `LongTask` procedure assumes you know in advance how long the task will take.</span></span> <span data-ttu-id="51899-139">To téměř nikdy neplatí.</span><span class="sxs-lookup"><span data-stu-id="51899-139">This is almost never the case.</span></span> <span data-ttu-id="51899-140">Rozdělování úkolů do bloků rovnoměrné velikosti může být obtížné a často se jedná o většinu uživatelů, což je jednoduše doba, která se předá před tím, než získá indikaci, že se něco děje.</span><span class="sxs-lookup"><span data-stu-id="51899-140">Dividing tasks into chunks of even size can be difficult, and often what matters most to users is simply the amount of time that passes before they get an indication that something is happening.</span></span>  
  
 <span data-ttu-id="51899-141">V této ukázce jste pravděpodobně spottedi jinou chybu.</span><span class="sxs-lookup"><span data-stu-id="51899-141">You may have spotted another flaw in this sample.</span></span> <span data-ttu-id="51899-142">Vlastnost `Timer` vrátí počet sekund, které uplynuly od půlnoci; Proto se aplikace zablokuje, pokud je spuštěná těsně před půlnocí.</span><span class="sxs-lookup"><span data-stu-id="51899-142">The `Timer` property returns the number of seconds that have passed since midnight; therefore, the application gets stuck if it is started just before midnight.</span></span> <span data-ttu-id="51899-143">Opatrnější přístup k měření času by vyžadoval podmínky hranice, jako je to v úvahu, nebo jejich zcela neřešitelné pomocí vlastností, jako je `Now`.</span><span class="sxs-lookup"><span data-stu-id="51899-143">A more careful approach to measuring time would take boundary conditions such as this into consideration, or avoid them altogether, using properties such as `Now`.</span></span>  
  
 <span data-ttu-id="51899-144">Teď, když `Widget` třída může vyvolávat události, můžete přejít k dalšímu návodu.</span><span class="sxs-lookup"><span data-stu-id="51899-144">Now that the `Widget` class can raise events, you can move to the next walkthrough.</span></span> <span data-ttu-id="51899-145">[Návod: zpracování událostí](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) ukazuje, jak použít `WithEvents` k přidružení obslužné rutiny události `PercentDone` události.</span><span class="sxs-lookup"><span data-stu-id="51899-145">[Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) demonstrates how to use `WithEvents` to associate an event handler with the `PercentDone` event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51899-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="51899-146">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>
- <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>
- [<span data-ttu-id="51899-147">Návod: Zpracování událostí</span><span class="sxs-lookup"><span data-stu-id="51899-147">Walkthrough: Handling Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)
- [<span data-ttu-id="51899-148">Události</span><span class="sxs-lookup"><span data-stu-id="51899-148">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
