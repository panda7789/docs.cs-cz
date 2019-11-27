---
title: RaiseEvent – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.RaiseEventMethod
- vb.RaiseEvent
- RaiseEvent
helpviewer_keywords:
- raising events [Visual Basic], RaiseEvent statement
- RaiseEvent statement [Visual Basic]
- event handlers, connecting events to
ms.assetid: f82e380a-1e6b-4047-bea8-c853f4d2c742
ms.openlocfilehash: e04f2bbaf57789f0bdaa07c1ebd68b22e3ae6178
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333049"
---
# <a name="raiseevent-statement"></a><span data-ttu-id="29a84-102">RaiseEvent – příkaz</span><span class="sxs-lookup"><span data-stu-id="29a84-102">RaiseEvent Statement</span></span>
<span data-ttu-id="29a84-103">Aktivuje událost deklarovanou na úrovni modulu v rámci třídy, formuláře nebo dokumentu.</span><span class="sxs-lookup"><span data-stu-id="29a84-103">Triggers an event declared at module level within a class, form, or document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29a84-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29a84-104">Syntax</span></span>  
  
```vb  
RaiseEvent eventname[( argumentlist )]  
```  
  
## <a name="parts"></a><span data-ttu-id="29a84-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="29a84-105">Parts</span></span>  
 `eventname`  
 <span data-ttu-id="29a84-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="29a84-106">Required.</span></span> <span data-ttu-id="29a84-107">Název události, která se má aktivovat</span><span class="sxs-lookup"><span data-stu-id="29a84-107">Name of the event to trigger.</span></span>  
  
 `argumentlist`  
 <span data-ttu-id="29a84-108">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="29a84-108">Optional.</span></span> <span data-ttu-id="29a84-109">Seznam proměnných, polí nebo výrazů oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="29a84-109">Comma-delimited list of variables, arrays, or expressions.</span></span> <span data-ttu-id="29a84-110">Argument `argumentlist` musí být uzavřený v závorkách.</span><span class="sxs-lookup"><span data-stu-id="29a84-110">The `argumentlist` argument must be enclosed by parentheses.</span></span> <span data-ttu-id="29a84-111">Pokud neexistují žádné argumenty, musí být uvozovky vynechány.</span><span class="sxs-lookup"><span data-stu-id="29a84-111">If there are no arguments, the parentheses must be omitted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29a84-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="29a84-112">Remarks</span></span>  
 <span data-ttu-id="29a84-113">Požadovaná `eventname` je název události deklarované v rámci modulu.</span><span class="sxs-lookup"><span data-stu-id="29a84-113">The required `eventname` is the name of an event declared within the module.</span></span> <span data-ttu-id="29a84-114">Postupuje podle Visual Basic konvence pojmenovávání proměnných.</span><span class="sxs-lookup"><span data-stu-id="29a84-114">It follows Visual Basic variable naming conventions.</span></span>  
  
 <span data-ttu-id="29a84-115">Pokud událost nebyla deklarována v modulu, ve kterém je vyvolána, dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="29a84-115">If the event has not been declared within the module in which it is raised, an error occurs.</span></span> <span data-ttu-id="29a84-116">Následující fragment kódu ukazuje deklaraci události a proceduru, ve které je událost vyvolána.</span><span class="sxs-lookup"><span data-stu-id="29a84-116">The following code fragment illustrates an event declaration and a procedure in which the event is raised.</span></span>  
  
 [!code-vb[VbVbalrEvents#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#37)]  
  
 <span data-ttu-id="29a84-117">Pomocí `RaiseEvent` nelze vyvolat události, které nejsou explicitně deklarovány v modulu.</span><span class="sxs-lookup"><span data-stu-id="29a84-117">You cannot use `RaiseEvent` to raise events that are not explicitly declared in the module.</span></span> <span data-ttu-id="29a84-118">Například všechny formuláře dědí událost <xref:System.Windows.Forms.Control.Click> z <xref:System.Windows.Forms.Form?displayProperty=nameWithType>, nelze ji vyvolat pomocí `RaiseEvent` v odvozené formě.</span><span class="sxs-lookup"><span data-stu-id="29a84-118">For example, all forms inherit a <xref:System.Windows.Forms.Control.Click> event from <xref:System.Windows.Forms.Form?displayProperty=nameWithType>, it cannot be raised using `RaiseEvent` in a derived form.</span></span> <span data-ttu-id="29a84-119">Pokud deklarujete událost `Click` v modulu formuláře, vystínuje se událost vlastní <xref:System.Windows.Forms.Control.Click> formuláře.</span><span class="sxs-lookup"><span data-stu-id="29a84-119">If you declare a `Click` event in the form module, it shadows the form's own <xref:System.Windows.Forms.Control.Click> event.</span></span> <span data-ttu-id="29a84-120">Můžete přesto vyvolat událost <xref:System.Windows.Forms.Control.Click> formuláře voláním metody <xref:System.Windows.Forms.Control.OnClick%2A>.</span><span class="sxs-lookup"><span data-stu-id="29a84-120">You can still invoke the form's <xref:System.Windows.Forms.Control.Click> event by calling the <xref:System.Windows.Forms.Control.OnClick%2A> method.</span></span>  
  
 <span data-ttu-id="29a84-121">Ve výchozím nastavení událost definovaná v Visual Basic vyvolává obslužné rutiny událostí v pořadí, ve kterém jsou navázána připojení.</span><span class="sxs-lookup"><span data-stu-id="29a84-121">By default, an event defined in Visual Basic raises its event handlers in the order that the connections are established.</span></span> <span data-ttu-id="29a84-122">Vzhledem k tomu, že události mohou mít parametry `ByRef`, proces, který spojuje pozdě, může přijímat parametry, které byly změněny předchozí obslužnou rutinou události.</span><span class="sxs-lookup"><span data-stu-id="29a84-122">Because events can have `ByRef` parameters, a process that connects late may receive parameters that have been changed by an earlier event handler.</span></span> <span data-ttu-id="29a84-123">Po provedení obslužné rutiny události je ovládací prvek vrácen do subrutiny, která událost vyvolala.</span><span class="sxs-lookup"><span data-stu-id="29a84-123">After the event handlers execute, control is returned to the subroutine that raised the event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="29a84-124">Nesdílené události by neměly být vyvolány v rámci konstruktoru třídy, ve které jsou deklarovány.</span><span class="sxs-lookup"><span data-stu-id="29a84-124">Non-shared events should not be raised within the constructor of the class in which they are declared.</span></span> <span data-ttu-id="29a84-125">I když takové události nezpůsobí chyby v době běhu, nemusí se podařit zachytit pomocí přidružených obslužných rutin událostí.</span><span class="sxs-lookup"><span data-stu-id="29a84-125">Although such events do not cause run-time errors, they may fail to be caught by associated event handlers.</span></span> <span data-ttu-id="29a84-126">Pomocí modifikátoru `Shared` vytvořte sdílenou událost, pokud potřebujete vyvolat událost z konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="29a84-126">Use the `Shared` modifier to create a shared event if you need to raise an event from a constructor.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="29a84-127">Můžete změnit výchozí chování událostí definováním vlastní události.</span><span class="sxs-lookup"><span data-stu-id="29a84-127">You can change the default behavior of events by defining a custom event.</span></span> <span data-ttu-id="29a84-128">Pro vlastní události příkaz `RaiseEvent` vyvolá přistupující objekt `RaiseEvent` události.</span><span class="sxs-lookup"><span data-stu-id="29a84-128">For custom events, the `RaiseEvent` statement invokes the event's `RaiseEvent` accessor.</span></span> <span data-ttu-id="29a84-129">Další informace o vlastních událostech naleznete v tématu [příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29a84-129">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="29a84-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="29a84-130">Example</span></span>  
 <span data-ttu-id="29a84-131">Následující příklad používá události pro počítání sekund od 10 do 0.</span><span class="sxs-lookup"><span data-stu-id="29a84-131">The following example uses events to count down seconds from 10 to 0.</span></span> <span data-ttu-id="29a84-132">Kód ilustruje několik metod, vlastností a příkazů souvisejících s událostmi, včetně příkazu `RaiseEvent`.</span><span class="sxs-lookup"><span data-stu-id="29a84-132">The code illustrates several of the event-related methods, properties, and statements, including the `RaiseEvent` statement.</span></span>  
  
 <span data-ttu-id="29a84-133">Třída, která vyvolá událost, je zdrojem události a metody, které zpracovávají události, jsou obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="29a84-133">The class that raises an event is the event source, and the methods that process the event are the event handlers.</span></span> <span data-ttu-id="29a84-134">Zdroj události může mít několik obslužných rutin pro události, které generuje.</span><span class="sxs-lookup"><span data-stu-id="29a84-134">An event source can have multiple handlers for the events it generates.</span></span> <span data-ttu-id="29a84-135">Když třída vyvolá událost, tato událost je vyvolána na každé třídě, která se rozhodla zpracovávat události pro tuto instanci objektu.</span><span class="sxs-lookup"><span data-stu-id="29a84-135">When the class raises the event, that event is raised on every class that has elected to handle events for that instance of the object.</span></span>  
  
 <span data-ttu-id="29a84-136">Příklad také používá formulář (`Form1`) s tlačítkem (`Button1`) a textovým polem (`TextBox1`).</span><span class="sxs-lookup"><span data-stu-id="29a84-136">The example also uses a form (`Form1`) with a button (`Button1`) and a text box (`TextBox1`).</span></span> <span data-ttu-id="29a84-137">Když kliknete na tlačítko, zobrazí se v prvním textovém poli odpočítávání od 10 do 0 sekund.</span><span class="sxs-lookup"><span data-stu-id="29a84-137">When you click the button, the first text box displays a countdown from 10 to 0 seconds.</span></span> <span data-ttu-id="29a84-138">Když uplyne celý čas (10 sekund), zobrazí se v prvním textovém poli "Hotovo".</span><span class="sxs-lookup"><span data-stu-id="29a84-138">When the full time (10 seconds) has elapsed, the first text box displays "Done".</span></span>  
  
 <span data-ttu-id="29a84-139">Kód pro `Form1` Určuje počáteční a koncovou stavy formuláře.</span><span class="sxs-lookup"><span data-stu-id="29a84-139">The code for `Form1` specifies the initial and terminal states of the form.</span></span> <span data-ttu-id="29a84-140">Obsahuje také kód spuštěný při vyvolání události.</span><span class="sxs-lookup"><span data-stu-id="29a84-140">It also contains the code executed when events are raised.</span></span>  
  
 <span data-ttu-id="29a84-141">Chcete-li použít tento příklad, otevřete nový projekt aplikace pro systém Windows, přidejte tlačítko s názvem `Button1` a textové pole s názvem `TextBox1` do hlavního formuláře s názvem `Form1`.</span><span class="sxs-lookup"><span data-stu-id="29a84-141">To use this example, open a new Windows Application project, add a button named `Button1` and a text box named `TextBox1` to the main form, named `Form1`.</span></span> <span data-ttu-id="29a84-142">Potom klikněte pravým tlačítkem myši na formulář a kliknutím na **Zobrazit kód** otevřete Editor kódu.</span><span class="sxs-lookup"><span data-stu-id="29a84-142">Then right-click the form and click **View Code** to open the Code Editor.</span></span>  
  
 <span data-ttu-id="29a84-143">Přidejte `WithEvents` proměnnou do oddílu deklarace `Form1` třídy.</span><span class="sxs-lookup"><span data-stu-id="29a84-143">Add a `WithEvents` variable to the declarations section of the `Form1` class.</span></span>  
  
 [!code-vb[VbVbalrEvents#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="29a84-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="29a84-144">Example</span></span>  
 <span data-ttu-id="29a84-145">Do kódu pro `Form1`přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="29a84-145">Add the following code to the code for `Form1`.</span></span> <span data-ttu-id="29a84-146">Nahraďte všechny duplicitní procedury, které mohou existovat, například `Form_Load`nebo `Button_Click`.</span><span class="sxs-lookup"><span data-stu-id="29a84-146">Replace any duplicate procedures that may exist, such as `Form_Load`, or `Button_Click`.</span></span>  
  
 [!code-vb[VbVbalrEvents#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#15)]  
  
 <span data-ttu-id="29a84-147">Stisknutím klávesy F5 spusťte předchozí příklad a klikněte na tlačítko s názvem **Spustit**.</span><span class="sxs-lookup"><span data-stu-id="29a84-147">Press F5 to run the preceding example, and click the button labeled **Start**.</span></span> <span data-ttu-id="29a84-148">V prvním textovém poli se začne počítat sekundy.</span><span class="sxs-lookup"><span data-stu-id="29a84-148">The first text box starts to count down the seconds.</span></span> <span data-ttu-id="29a84-149">Když uplyne celý čas (10 sekund), zobrazí se v prvním textovém poli "Hotovo".</span><span class="sxs-lookup"><span data-stu-id="29a84-149">When the full time (10 seconds) has elapsed, the first text box displays "Done".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="29a84-150">Metoda `My.Application.DoEvents` nezpracovává události přesně stejným způsobem jako formulář.</span><span class="sxs-lookup"><span data-stu-id="29a84-150">The `My.Application.DoEvents` method does not process events in exactly the same way as the form does.</span></span> <span data-ttu-id="29a84-151">Chcete-li, aby formulář mohl zpracovávat události přímo, můžete použít multithreading.</span><span class="sxs-lookup"><span data-stu-id="29a84-151">To allow the form to handle the events directly, you can use multithreading.</span></span> <span data-ttu-id="29a84-152">Další informace najdete v tématu [spravovaná vlákna](../../../standard/threading/index.md).</span><span class="sxs-lookup"><span data-stu-id="29a84-152">For more information, see [Managed Threading](../../../standard/threading/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29a84-153">Viz také:</span><span class="sxs-lookup"><span data-stu-id="29a84-153">See also</span></span>

- [<span data-ttu-id="29a84-154">Události</span><span class="sxs-lookup"><span data-stu-id="29a84-154">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
- [<span data-ttu-id="29a84-155">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="29a84-155">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="29a84-156">Příkaz AddHandler</span><span class="sxs-lookup"><span data-stu-id="29a84-156">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [<span data-ttu-id="29a84-157">Příkaz RemoveHandler</span><span class="sxs-lookup"><span data-stu-id="29a84-157">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [<span data-ttu-id="29a84-158">Řeší</span><span class="sxs-lookup"><span data-stu-id="29a84-158">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
