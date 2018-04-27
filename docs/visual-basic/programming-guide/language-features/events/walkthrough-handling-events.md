---
title: Zpracování událostí (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- event handling [Visual Basic], walkthroughs
- walkthroughs [Visual Basic], event handling
- variables [Visual Basic], WithEvents
- events [Visual Basic], walkthroughs
- WithEvents keyword [Visual Basic], walkthroughs
- event handlers [Visual Basic], walkthroughs
ms.assetid: f145b3fc-5ae0-4509-a2aa-1ff6934706bd
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c1743e5f5d9dcdf83ab646407cd1fcdc77ff71cd
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-handling-events-visual-basic"></a><span data-ttu-id="0ce84-102">Návod: Zpracování událostí (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ce84-102">Walkthrough: Handling Events (Visual Basic)</span></span>
<span data-ttu-id="0ce84-103">Toto je druhý dvě témata, která ukazují, jak pracovat s událostmi.</span><span class="sxs-lookup"><span data-stu-id="0ce84-103">This is the second of two topics that demonstrate how to work with events.</span></span> <span data-ttu-id="0ce84-104">První téma [návod: deklarující a aktivaci událostí](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md), ukazuje, jak deklarace a vyvolávání událostí.</span><span class="sxs-lookup"><span data-stu-id="0ce84-104">The first topic, [Walkthrough: Declaring and Raising Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md), shows how to declare and raise events.</span></span> <span data-ttu-id="0ce84-105">Tato část používá formulář a třídy z tohoto návodu jak ke zpracování událostí při jejich provádění.</span><span class="sxs-lookup"><span data-stu-id="0ce84-105">This section uses the form and class from that walkthrough to show how to handle events when they take place.</span></span>  
  
 <span data-ttu-id="0ce84-106">`Widget` Třída příklad používá tradiční příkazy zpracování událostí.</span><span class="sxs-lookup"><span data-stu-id="0ce84-106">The `Widget` class example uses traditional event-handling statements.</span></span> <span data-ttu-id="0ce84-107">Visual Basic poskytuje další metody pro práci s událostmi.</span><span class="sxs-lookup"><span data-stu-id="0ce84-107">Visual Basic provides other techniques for working with events.</span></span> <span data-ttu-id="0ce84-108">Jako cvičení, můžete upravit tento příklad pro použití `AddHandler` a `Handles` příkazy.</span><span class="sxs-lookup"><span data-stu-id="0ce84-108">As an exercise, you can modify this example to use the `AddHandler` and `Handles` statements.</span></span>  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a><span data-ttu-id="0ce84-109">Zpracování události PercentDone třídy pomůcky</span><span class="sxs-lookup"><span data-stu-id="0ce84-109">To handle the PercentDone event of the Widget class</span></span>  
  
1.  <span data-ttu-id="0ce84-110">Vložte následující kód v `Form1`:</span><span class="sxs-lookup"><span data-stu-id="0ce84-110">Place the following code in `Form1`:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_1.vb)]  
  
     <span data-ttu-id="0ce84-111">`WithEvents` – Klíčové slovo určuje, že proměnná `mWidget` slouží ke zpracování události objektu.</span><span class="sxs-lookup"><span data-stu-id="0ce84-111">The `WithEvents` keyword specifies that the variable `mWidget` is used to handle an object's events.</span></span> <span data-ttu-id="0ce84-112">Určují druh objektu zadáním názvu třídy, ze kterého bude vytvořen objekt.</span><span class="sxs-lookup"><span data-stu-id="0ce84-112">You specify the kind of object by supplying the name of the class from which the object will be created.</span></span>  
  
     <span data-ttu-id="0ce84-113">Proměnná `mWidget` deklarovaného v souboru `Form1` protože `WithEvents` proměnných musí být na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="0ce84-113">The variable `mWidget` is declared in `Form1` because `WithEvents` variables must be class-level.</span></span> <span data-ttu-id="0ce84-114">To platí bez ohledu na typ třídy, které je v umístění.</span><span class="sxs-lookup"><span data-stu-id="0ce84-114">This is true regardless of the type of class you place them in.</span></span>  
  
     <span data-ttu-id="0ce84-115">Proměnná `mblnCancel` je sloužící ke zrušení `LongTask` metoda.</span><span class="sxs-lookup"><span data-stu-id="0ce84-115">The variable `mblnCancel` is used to cancel the `LongTask` method.</span></span>  
  
## <a name="writing-code-to-handle-an-event"></a><span data-ttu-id="0ce84-116">Psaní kódu pro zpracování událostí</span><span class="sxs-lookup"><span data-stu-id="0ce84-116">Writing Code to Handle an Event</span></span>  
 <span data-ttu-id="0ce84-117">Jakmile deklarovat proměnnou pomocí `WithEvents`, název proměnné se zobrazí v levém rozevíracím seznamu třídy **Editor kódu**.</span><span class="sxs-lookup"><span data-stu-id="0ce84-117">As soon as you declare a variable using `WithEvents`, the variable name appears in the left drop-down list of the class's **Code Editor**.</span></span> <span data-ttu-id="0ce84-118">Když vyberete `mWidget`, `Widget` třídy události se zobrazí v pravém rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="0ce84-118">When you select `mWidget`, the `Widget` class's events appear in the right drop-down list.</span></span> <span data-ttu-id="0ce84-119">Výběr událost zobrazí odpovídající postup událostí s předponou `mWidget` a podtržítka.</span><span class="sxs-lookup"><span data-stu-id="0ce84-119">Selecting an event displays the corresponding event procedure, with the prefix `mWidget` and an underscore.</span></span> <span data-ttu-id="0ce84-120">Všechny postupy události související s `WithEvents` proměnná zadána název proměnné jako předponu.</span><span class="sxs-lookup"><span data-stu-id="0ce84-120">All the event procedures associated with a `WithEvents` variable are given the variable name as a prefix.</span></span>  
  
#### <a name="to-handle-an-event"></a><span data-ttu-id="0ce84-121">Zpracovat události</span><span class="sxs-lookup"><span data-stu-id="0ce84-121">To handle an event</span></span>  
  
1.  <span data-ttu-id="0ce84-122">Vyberte `mWidget` v levém rozevíracím seznamu v **Editor kódu**.</span><span class="sxs-lookup"><span data-stu-id="0ce84-122">Select `mWidget` from the left drop-down list in the **Code Editor**.</span></span>  
  
2.  <span data-ttu-id="0ce84-123">Vyberte `PercentDone` událost z pravé rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="0ce84-123">Select the `PercentDone` event from the right drop-down list.</span></span> <span data-ttu-id="0ce84-124">**Editor kódu** otevře `mWidget_PercentDone` procedury události.</span><span class="sxs-lookup"><span data-stu-id="0ce84-124">The **Code Editor** opens the `mWidget_PercentDone` event procedure.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0ce84-125">**Editor kódu** je užitečné, ale není požadováno pro vkládání nové obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="0ce84-125">The **Code Editor** is useful, but not required, for inserting new event handlers.</span></span> <span data-ttu-id="0ce84-126">V tomto návodu je více přímo do obslužné rutiny událostí jednoduše zkopírujete přímo do kódu.</span><span class="sxs-lookup"><span data-stu-id="0ce84-126">In this walkthrough, it is more direct to just copy the event handlers directly into your code.</span></span>  
  
3.  <span data-ttu-id="0ce84-127">Přidejte následující kód, který `mWidget_PercentDone` obslužné rutiny události:</span><span class="sxs-lookup"><span data-stu-id="0ce84-127">Add the following code to the `mWidget_PercentDone` event handler:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_2.vb)]  
  
     <span data-ttu-id="0ce84-128">Vždy, když `PercentDone` událost se vyvolá, postup událostí zobrazuje procento dokončení v `Label` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0ce84-128">Whenever the `PercentDone` event is raised, the event procedure displays the percent complete in a `Label` control.</span></span> <span data-ttu-id="0ce84-129">`DoEvents` Metoda umožňuje štítek, který chcete překreslit a klikněte na možnost také umožňuje uživateli **zrušit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="0ce84-129">The `DoEvents` method allows the label to repaint, and also gives the user the opportunity to click the **Cancel** button.</span></span>  
  
4.  <span data-ttu-id="0ce84-130">Přidejte následující kód pro `Button2_Click` obslužné rutiny události:</span><span class="sxs-lookup"><span data-stu-id="0ce84-130">Add the following code for the `Button2_Click` event handler:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_3.vb)]  
  
 <span data-ttu-id="0ce84-131">Pokud uživatel klikne **zrušit** tlačítko při `LongTask` běží, `Button2_Click` událost se spustí co nejrychleji `DoEvents` příkaz umožňuje zpracování událostí proběhnout.</span><span class="sxs-lookup"><span data-stu-id="0ce84-131">If the user clicks the **Cancel** button while `LongTask` is running, the `Button2_Click` event is executed as soon as the `DoEvents` statement allows event processing to occur.</span></span> <span data-ttu-id="0ce84-132">Proměnná úrovni třídy `mblnCancel` je nastaven na `True`a `mWidget_PercentDone` událostí pak ho testuje a nastaví `ByRef Cancel` argument `True`.</span><span class="sxs-lookup"><span data-stu-id="0ce84-132">The class-level variable `mblnCancel` is set to `True`, and the `mWidget_PercentDone` event then tests it and sets the `ByRef Cancel` argument to `True`.</span></span>  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a><span data-ttu-id="0ce84-133">Připojení proměnnou WithEvents k objektu</span><span class="sxs-lookup"><span data-stu-id="0ce84-133">Connecting a WithEvents Variable to an Object</span></span>  
 <span data-ttu-id="0ce84-134">`Form1` je teď nastavená pro zpracování `Widget` události objektu.</span><span class="sxs-lookup"><span data-stu-id="0ce84-134">`Form1` is now set up to handle a `Widget` object's events.</span></span> <span data-ttu-id="0ce84-135">Zbývá k vyhledání `Widget` místo.</span><span class="sxs-lookup"><span data-stu-id="0ce84-135">All that remains is to find a `Widget` somewhere.</span></span>  
  
 <span data-ttu-id="0ce84-136">Když je deklarovat proměnnou `WithEvents` žádný objekt v době návrhu, je k ní přidružena.</span><span class="sxs-lookup"><span data-stu-id="0ce84-136">When you declare a variable `WithEvents` at design time, no object is associated with it.</span></span> <span data-ttu-id="0ce84-137">A `WithEvents` proměnná je stejně jako jakoukoli jinou proměnnou objektu.</span><span class="sxs-lookup"><span data-stu-id="0ce84-137">A `WithEvents` variable is just like any other object variable.</span></span> <span data-ttu-id="0ce84-138">Máte-li vytvořit objekt a přiřadit odkaz na její `WithEvents` proměnné.</span><span class="sxs-lookup"><span data-stu-id="0ce84-138">You have to create an object and assign a reference to it with the `WithEvents` variable.</span></span>  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a><span data-ttu-id="0ce84-139">K vytvoření objektu a odkaz na jeho přiřazení</span><span class="sxs-lookup"><span data-stu-id="0ce84-139">To create an object and assign a reference to it</span></span>  
  
1.  <span data-ttu-id="0ce84-140">Vyberte **(Form1 událostí)** v levém rozevíracím seznamu v **Editor kódu**.</span><span class="sxs-lookup"><span data-stu-id="0ce84-140">Select **(Form1 Events)** from the left drop-down list in the **Code Editor**.</span></span>  
  
2.  <span data-ttu-id="0ce84-141">Vyberte `Load` událost z pravé rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="0ce84-141">Select the `Load` event from the right drop-down list.</span></span> <span data-ttu-id="0ce84-142">**Editor kódu** otevře `Form1_Load` procedury události.</span><span class="sxs-lookup"><span data-stu-id="0ce84-142">The **Code Editor** opens the `Form1_Load` event procedure.</span></span>  
  
3.  <span data-ttu-id="0ce84-143">Přidejte následující kód pro `Form1_Load` události postupu vytvořte `Widget`:</span><span class="sxs-lookup"><span data-stu-id="0ce84-143">Add the following code for the `Form1_Load` event procedure to create the `Widget`:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_4.vb)]  
  
 <span data-ttu-id="0ce84-144">Když tento kód provede, vytvoří jazyka Visual Basic `Widget` objektu a události se připojí k události postupy související s `mWidget`.</span><span class="sxs-lookup"><span data-stu-id="0ce84-144">When this code executes, Visual Basic creates a `Widget` object and connects its events to the event procedures associated with `mWidget`.</span></span> <span data-ttu-id="0ce84-145">Od této chvíle, vždy, když `Widget` vyvolá jeho `PercentDone` událostí, `mWidget_PercentDone` procedury událostí.</span><span class="sxs-lookup"><span data-stu-id="0ce84-145">From that point on, whenever the `Widget` raises its `PercentDone` event, the `mWidget_PercentDone` event procedure is executed.</span></span>  
  
#### <a name="to-call-the-longtask-method"></a><span data-ttu-id="0ce84-146">K volání metody LongTask</span><span class="sxs-lookup"><span data-stu-id="0ce84-146">To call the LongTask method</span></span>  
  
-   <span data-ttu-id="0ce84-147">Přidejte následující kód, který `Button1_Click` obslužné rutiny události:</span><span class="sxs-lookup"><span data-stu-id="0ce84-147">Add the following code to the `Button1_Click` event handler:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_5.vb)]  
  
 <span data-ttu-id="0ce84-148">Před `LongTask` metoda je volána, štítky, musí být inicializován zobrazí procento dokončení a úrovni třídy `Boolean` příznak pro zrušení metodu, musí být nastavené na `False`.</span><span class="sxs-lookup"><span data-stu-id="0ce84-148">Before the `LongTask` method is called, the label that displays the percent complete must be initialized, and the class-level `Boolean` flag for canceling the method must be set to `False`.</span></span>  
  
 <span data-ttu-id="0ce84-149">`LongTask` je volána s určitou dobou trvání úloh 12.2 sekund.</span><span class="sxs-lookup"><span data-stu-id="0ce84-149">`LongTask` is called with a task duration of 12.2 seconds.</span></span> <span data-ttu-id="0ce84-150">`PercentDone` Událost se vyvolá po každé třetinu sekundy.</span><span class="sxs-lookup"><span data-stu-id="0ce84-150">The `PercentDone` event is raised once every one-third of a second.</span></span> <span data-ttu-id="0ce84-151">Pokaždé, když událost se vyvolá, `mWidget_PercentDone` procedury událostí.</span><span class="sxs-lookup"><span data-stu-id="0ce84-151">Each time the event is raised, the `mWidget_PercentDone` event procedure is executed.</span></span>  
  
 <span data-ttu-id="0ce84-152">Když `LongTask` probíhá, `mblnCancel` je testován pro případ, `LongTask` skončila normálně, nebo pokud je zastavena, protože `mblnCancel` byla nastavena na `True`.</span><span class="sxs-lookup"><span data-stu-id="0ce84-152">When `LongTask` is done, `mblnCancel` is tested to see if `LongTask` ended normally, or if it stopped because `mblnCancel` was set to `True`.</span></span> <span data-ttu-id="0ce84-153">Procento dokončení je aktualizovat jenom v prvním případě.</span><span class="sxs-lookup"><span data-stu-id="0ce84-153">The percent complete is updated only in the former case.</span></span>  
  
#### <a name="to-run-the-program"></a><span data-ttu-id="0ce84-154">Ke spuštění programu</span><span class="sxs-lookup"><span data-stu-id="0ce84-154">To run the program</span></span>  
  
1.  <span data-ttu-id="0ce84-155">Stisknutím klávesy F5 projekt uvést do režimu spuštění.</span><span class="sxs-lookup"><span data-stu-id="0ce84-155">Press F5 to put the project in run mode.</span></span>  
  
2.  <span data-ttu-id="0ce84-156">Klikněte **spustit úlohu** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="0ce84-156">Click the **Start Task** button.</span></span> <span data-ttu-id="0ce84-157">Pokaždé, když `PercentDone` událost se vyvolá, aktualizuje popisek s procento dokončení úkolu.</span><span class="sxs-lookup"><span data-stu-id="0ce84-157">Each time the `PercentDone` event is raised, the label is updated with the percentage of the task that is complete.</span></span>  
  
3.  <span data-ttu-id="0ce84-158">Klikněte **zrušit** tlačítko Ukončit úlohu.</span><span class="sxs-lookup"><span data-stu-id="0ce84-158">Click the **Cancel** button to stop the task.</span></span> <span data-ttu-id="0ce84-159">Všimněte si, že vzhled **zrušit** tlačítko nezmění okamžitě po kliknutí.</span><span class="sxs-lookup"><span data-stu-id="0ce84-159">Notice that the appearance of the **Cancel** button does not change immediately when you click it.</span></span> <span data-ttu-id="0ce84-160">`Click` Událostí je skutečnost, dokud `My.Application.DoEvents` příkaz umožňuje zpracování událostí.</span><span class="sxs-lookup"><span data-stu-id="0ce84-160">The `Click` event cannot happen until the `My.Application.DoEvents` statement allows event processing.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0ce84-161">`My.Application.DoEvents` Metoda nezpracovává události stejným způsobem, jak to dělá formuláře.</span><span class="sxs-lookup"><span data-stu-id="0ce84-161">The `My.Application.DoEvents` method does not process events in exactly the same way as the form does.</span></span> <span data-ttu-id="0ce84-162">Například v tomto návodu, musíte kliknout na **zrušit** tlačítko dvakrát.</span><span class="sxs-lookup"><span data-stu-id="0ce84-162">For example, in this walkthrough, you must click the **Cancel** button twice.</span></span> <span data-ttu-id="0ce84-163">Chcete-li povolit formuláře pro zpracování událostí přímo, můžete použít více vláken.</span><span class="sxs-lookup"><span data-stu-id="0ce84-163">To allow the form to handle the events directly, you can use multithreading.</span></span> <span data-ttu-id="0ce84-164">Další informace najdete v tématu [zřetězení](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c).</span><span class="sxs-lookup"><span data-stu-id="0ce84-164">For more information, see [Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c).</span></span>  
  
 <span data-ttu-id="0ce84-165">Možná bude významné lze spustit program s F11 a procházet kód řádku najednou.</span><span class="sxs-lookup"><span data-stu-id="0ce84-165">You may find it instructive to run the program with F11 and step through the code a line at a time.</span></span> <span data-ttu-id="0ce84-166">Jasně uvidíte, jak provádění zadá `LongTask`a pak stručně znovu zadá `Form1` pokaždé, když `PercentDone` událost se vyvolá.</span><span class="sxs-lookup"><span data-stu-id="0ce84-166">You can clearly see how execution enters `LongTask`, and then briefly re-enters `Form1` each time the `PercentDone` event is raised.</span></span>  
  
 <span data-ttu-id="0ce84-167">Co by mohlo dojít v případě, při spuštění zpět v kódu `Form1`, `LongTask` byla volána metoda znovu?</span><span class="sxs-lookup"><span data-stu-id="0ce84-167">What would happen if, while execution was back in the code of `Form1`, the `LongTask` method were called again?</span></span> <span data-ttu-id="0ce84-168">V nejhorším případě může dojít k přetečení zásobníku, pokud `LongTask` měla volat pokaždé, když byla vyvolána událost.</span><span class="sxs-lookup"><span data-stu-id="0ce84-168">At worst, a stack overflow might occur if `LongTask` were called every time the event was raised.</span></span>  
  
 <span data-ttu-id="0ce84-169">Proměnná může způsobit `mWidget` zpracovat události pro jiné `Widget` objekt přiřazením odkaz na nové `Widget` k `mWidget`.</span><span class="sxs-lookup"><span data-stu-id="0ce84-169">You can cause the variable `mWidget` to handle events for a different `Widget` object by assigning a reference to the new `Widget` to `mWidget`.</span></span> <span data-ttu-id="0ce84-170">Ve skutečnosti můžete použít kód v `Button1_Click` tomu pokaždé, když kliknete na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="0ce84-170">In fact, you can make the code in `Button1_Click` do this every time you click the button.</span></span>  
  
#### <a name="to-handle-events-for-a-different-widget"></a><span data-ttu-id="0ce84-171">Zpracování událostí pro různé pomůcky</span><span class="sxs-lookup"><span data-stu-id="0ce84-171">To handle events for a different widget</span></span>  
  
-   <span data-ttu-id="0ce84-172">Přidejte následující řádek kódu `Button1_Click` postupu přímo předchází řádku, který čte `mWidget.LongTask(12.2, 0.33)`:</span><span class="sxs-lookup"><span data-stu-id="0ce84-172">Add the following line of code to the `Button1_Click` procedure, immediately preceding the line that reads `mWidget.LongTask(12.2, 0.33)`:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_6.vb)]  
  
 <span data-ttu-id="0ce84-173">Výše uvedený kód vytvoří novou `Widget` pokaždé, když po kliknutí na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="0ce84-173">The code above creates a new `Widget` each time the button is clicked.</span></span> <span data-ttu-id="0ce84-174">Jakmile `LongTask` metoda dokončí, odkaz na `Widget` vydání a `Widget` zničena.</span><span class="sxs-lookup"><span data-stu-id="0ce84-174">As soon as the `LongTask` method completes, the reference to the `Widget` is released, and the `Widget` is destroyed.</span></span>  
  
 <span data-ttu-id="0ce84-175">A `WithEvents` proměnná může obsahovat pouze jeden objekt odkaz najednou, chcete-li přiřadit jinou `Widget` do objektu `mWidget`, předchozí `Widget` už zpracování události objektu.</span><span class="sxs-lookup"><span data-stu-id="0ce84-175">A `WithEvents` variable can contain only one object reference at a time, so if you assign a different `Widget` object to `mWidget`, the previous `Widget` object's events will no longer be handled.</span></span> <span data-ttu-id="0ce84-176">Pokud `mWidget` je proměnnou pouze objekt obsahující odkaz na starý `Widget`, objekt zničena.</span><span class="sxs-lookup"><span data-stu-id="0ce84-176">If `mWidget` is the only object variable containing a reference to the old `Widget`, the object is destroyed.</span></span> <span data-ttu-id="0ce84-177">Pokud chcete zpracovat události z několika `Widget` objekty, používají `AddHandler` příkaz zpracovat události z každý objekt odděleně.</span><span class="sxs-lookup"><span data-stu-id="0ce84-177">If you want to handle events from several `Widget` objects, use the `AddHandler` statement to process events from each object separately.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0ce84-178">Je možné deklarovat tolik `WithEvents` proměnné jako budete potřebovat, ale pole `WithEvents` proměnné nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="0ce84-178">You can declare as many `WithEvents` variables as you need, but arrays of `WithEvents` variables are not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ce84-179">Viz také</span><span class="sxs-lookup"><span data-stu-id="0ce84-179">See Also</span></span>  
 [<span data-ttu-id="0ce84-180">Návod: Deklarace a vyvolávání událostí</span><span class="sxs-lookup"><span data-stu-id="0ce84-180">Walkthrough: Declaring and Raising Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)  
 [<span data-ttu-id="0ce84-181">Události</span><span class="sxs-lookup"><span data-stu-id="0ce84-181">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
