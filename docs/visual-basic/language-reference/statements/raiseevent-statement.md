---
title: RaiseEvent – příkaz (Visual Basic)
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
ms.openlocfilehash: ef4dce290a7a7f6340b15aa4083cd40518e37d0d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43388404"
---
# <a name="raiseevent-statement"></a><span data-ttu-id="01628-102">RaiseEvent – příkaz</span><span class="sxs-lookup"><span data-stu-id="01628-102">RaiseEvent Statement</span></span>
<span data-ttu-id="01628-103">Spustí událost deklarovanou na úrovni modulu uvnitř třídy, formuláře nebo dokumentu.</span><span class="sxs-lookup"><span data-stu-id="01628-103">Triggers an event declared at module level within a class, form, or document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01628-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01628-104">Syntax</span></span>  
  
```  
RaiseEvent eventname[( argumentlist )]  
```  
  
## <a name="parts"></a><span data-ttu-id="01628-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="01628-105">Parts</span></span>  
 `eventname`  
 <span data-ttu-id="01628-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="01628-106">Required.</span></span> <span data-ttu-id="01628-107">Název události k aktivaci.</span><span class="sxs-lookup"><span data-stu-id="01628-107">Name of the event to trigger.</span></span>  
  
 `argumentlist`  
 <span data-ttu-id="01628-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="01628-108">Optional.</span></span> <span data-ttu-id="01628-109">Čárkami oddělený seznam proměnných, pole nebo výrazy.</span><span class="sxs-lookup"><span data-stu-id="01628-109">Comma-delimited list of variables, arrays, or expressions.</span></span> <span data-ttu-id="01628-110">`argumentlist` Argument musí být uzavřen v závorkách.</span><span class="sxs-lookup"><span data-stu-id="01628-110">The `argumentlist` argument must be enclosed by parentheses.</span></span> <span data-ttu-id="01628-111">Pokud neexistují žádné argumenty, musí být vynechána závorky.</span><span class="sxs-lookup"><span data-stu-id="01628-111">If there are no arguments, the parentheses must be omitted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01628-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="01628-112">Remarks</span></span>  
 <span data-ttu-id="01628-113">Požadované `eventname` je název události deklarované v rámci modulu.</span><span class="sxs-lookup"><span data-stu-id="01628-113">The required `eventname` is the name of an event declared within the module.</span></span> <span data-ttu-id="01628-114">Splňuje zásady vytváření názvů proměnných jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="01628-114">It follows Visual Basic variable naming conventions.</span></span>  
  
 <span data-ttu-id="01628-115">Pokud událost nebyla deklarována v rámci modulu, ve kterém se vyvolá, dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="01628-115">If the event has not been declared within the module in which it is raised, an error occurs.</span></span> <span data-ttu-id="01628-116">Následující fragment kódu ukazuje deklaraci události a postup vyvolání události.</span><span class="sxs-lookup"><span data-stu-id="01628-116">The following code fragment illustrates an event declaration and a procedure in which the event is raised.</span></span>  
  
 [!code-vb[VbVbalrEvents#37](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_1.vb)]  
  
 <span data-ttu-id="01628-117">Nemůžete použít `RaiseEvent` vyvolávat události, které nejsou explicitně deklarovány v modulu.</span><span class="sxs-lookup"><span data-stu-id="01628-117">You cannot use `RaiseEvent` to raise events that are not explicitly declared in the module.</span></span> <span data-ttu-id="01628-118">Například zdědí všechny formuláře <xref:System.Windows.Forms.Control.Click> událost z <xref:System.Windows.Forms.Form?displayProperty=nameWithType>, nelze vyvolat, pomocí `RaiseEvent` ve formě odvozené.</span><span class="sxs-lookup"><span data-stu-id="01628-118">For example, all forms inherit a <xref:System.Windows.Forms.Control.Click> event from <xref:System.Windows.Forms.Form?displayProperty=nameWithType>, it cannot be raised using `RaiseEvent` in a derived form.</span></span> <span data-ttu-id="01628-119">Pokud deklarujete `Click` událostí v modulu formuláře je zastiňuje formuláře vlastní <xref:System.Windows.Forms.Control.Click> událostí.</span><span class="sxs-lookup"><span data-stu-id="01628-119">If you declare a `Click` event in the form module, it shadows the form's own <xref:System.Windows.Forms.Control.Click> event.</span></span> <span data-ttu-id="01628-120">Stále můžete vyvolat formuláře <xref:System.Windows.Forms.Control.Click> události voláním <xref:System.Windows.Forms.Control.OnClick%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="01628-120">You can still invoke the form's <xref:System.Windows.Forms.Control.Click> event by calling the <xref:System.Windows.Forms.Control.OnClick%2A> method.</span></span>  
  
 <span data-ttu-id="01628-121">Ve výchozím nastavení události definované v jazyce Visual Basic vyvolá jeho obslužné rutiny událostí v pořadí, že se vytvoří připojení.</span><span class="sxs-lookup"><span data-stu-id="01628-121">By default, an event defined in Visual Basic raises its event handlers in the order that the connections are established.</span></span> <span data-ttu-id="01628-122">Vzhledem k tomu, že události můžou mít `ByRef` parametry, proces, který se připojuje pozdní mohou přijímat parametry, které se změnily předchozí obslužnou rutinou události.</span><span class="sxs-lookup"><span data-stu-id="01628-122">Because events can have `ByRef` parameters, a process that connects late may receive parameters that have been changed by an earlier event handler.</span></span> <span data-ttu-id="01628-123">Po spuštění obslužné rutiny událostí, ovládací prvek se vrátí do podprogram, který vyvolal událost.</span><span class="sxs-lookup"><span data-stu-id="01628-123">After the event handlers execute, control is returned to the subroutine that raised the event.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="01628-124">Pro nesdílené události by neměla být vyvolána v rámci konstruktoru třídy, ve kterém jsou deklarovány.</span><span class="sxs-lookup"><span data-stu-id="01628-124">Non-shared events should not be raised within the constructor of the class in which they are declared.</span></span> <span data-ttu-id="01628-125">I když tyto události nezpůsobí chyby za běhu, se nemusí podařit ji zachytit obslužnými rutinami související události.</span><span class="sxs-lookup"><span data-stu-id="01628-125">Although such events do not cause run-time errors, they may fail to be caught by associated event handlers.</span></span> <span data-ttu-id="01628-126">Použití `Shared` modifikátor vytvořit sdílené událost, pokud je potřeba vyvolat událost v konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="01628-126">Use the `Shared` modifier to create a shared event if you need to raise an event from a constructor.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="01628-127">Výchozí chování událostí můžete změnit tak, že definujete vlastní událost.</span><span class="sxs-lookup"><span data-stu-id="01628-127">You can change the default behavior of events by defining a custom event.</span></span> <span data-ttu-id="01628-128">Pro vlastní události `RaiseEvent` příkaz volá události `RaiseEvent` přistupujícího objektu.</span><span class="sxs-lookup"><span data-stu-id="01628-128">For custom events, the `RaiseEvent` statement invokes the event's `RaiseEvent` accessor.</span></span> <span data-ttu-id="01628-129">Další informace o vlastních událostech najdete v tématu [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="01628-129">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="01628-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="01628-130">Example</span></span>  
 <span data-ttu-id="01628-131">Následující příklad používá události k počet sekund od 10 do 0.</span><span class="sxs-lookup"><span data-stu-id="01628-131">The following example uses events to count down seconds from 10 to 0.</span></span> <span data-ttu-id="01628-132">Kód ukazuje několik událostí související metody, vlastnosti a příkazy, včetně `RaiseEvent` příkazu.</span><span class="sxs-lookup"><span data-stu-id="01628-132">The code illustrates several of the event-related methods, properties, and statements, including the `RaiseEvent` statement.</span></span>  
  
 <span data-ttu-id="01628-133">Třída, která vyvolá událost, je zdroj události a metody, které zpracovávají události jsou obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="01628-133">The class that raises an event is the event source, and the methods that process the event are the event handlers.</span></span> <span data-ttu-id="01628-134">Zdroj událostí může mít více obslužných rutin událostí, který generuje.</span><span class="sxs-lookup"><span data-stu-id="01628-134">An event source can have multiple handlers for the events it generates.</span></span> <span data-ttu-id="01628-135">Pokud třída vyvolá událost, této události je vyvoláno na každé třídy, která je se rozhodli zpracovávat události pro tuto instanci objektu.</span><span class="sxs-lookup"><span data-stu-id="01628-135">When the class raises the event, that event is raised on every class that has elected to handle events for that instance of the object.</span></span>  
  
 <span data-ttu-id="01628-136">V příkladu se také používá formuláře (`Form1`) s tlačítkem (`Button1`) a textové pole (`TextBox1`).</span><span class="sxs-lookup"><span data-stu-id="01628-136">The example also uses a form (`Form1`) with a button (`Button1`) and a text box (`TextBox1`).</span></span> <span data-ttu-id="01628-137">Když kliknete na tlačítko, prvního textového pole zobrazuje odpočítávání z 10 na 0 sekund.</span><span class="sxs-lookup"><span data-stu-id="01628-137">When you click the button, the first text box displays a countdown from 10 to 0 seconds.</span></span> <span data-ttu-id="01628-138">Po uplynutí doby úplné (10 sekund), se zobrazí "Hotovo" prvního textového pole.</span><span class="sxs-lookup"><span data-stu-id="01628-138">When the full time (10 seconds) has elapsed, the first text box displays "Done".</span></span>  
  
 <span data-ttu-id="01628-139">Kód pro `Form1` Určuje počáteční a terminálu stavy formuláře.</span><span class="sxs-lookup"><span data-stu-id="01628-139">The code for `Form1` specifies the initial and terminal states of the form.</span></span> <span data-ttu-id="01628-140">Také obsahuje kód, spustí se, když jsou vyvolány události.</span><span class="sxs-lookup"><span data-stu-id="01628-140">It also contains the code executed when events are raised.</span></span>  
  
 <span data-ttu-id="01628-141">Pokud chcete použít tento příklad, otevřete nový projekt aplikace Windows, přidejte tlačítko s názvem `Button1` a textové pole s názvem `TextBox1` hlavní formulář s názvem `Form1`.</span><span class="sxs-lookup"><span data-stu-id="01628-141">To use this example, open a new Windows Application project, add a button named `Button1` and a text box named `TextBox1` to the main form, named `Form1`.</span></span> <span data-ttu-id="01628-142">Klikněte pravým tlačítkem myši na formuláři a klikněte na tlačítko **zobrazit kód** otevřete Editor kódu.</span><span class="sxs-lookup"><span data-stu-id="01628-142">Then right-click the form and click **View Code** to open the Code Editor.</span></span>  
  
 <span data-ttu-id="01628-143">Přidat `WithEvents` do části deklarace proměnných `Form1` třídy.</span><span class="sxs-lookup"><span data-stu-id="01628-143">Add a `WithEvents` variable to the declarations section of the `Form1` class.</span></span>  
  
 [!code-vb[VbVbalrEvents#14](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="01628-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="01628-144">Example</span></span>  
 <span data-ttu-id="01628-145">Následující kód přidejte kód pro `Form1`.</span><span class="sxs-lookup"><span data-stu-id="01628-145">Add the following code to the code for `Form1`.</span></span> <span data-ttu-id="01628-146">Nahraďte všechny duplicitní postupy, které mohou existovat, jako například `Form_Load`, nebo `Button_Click`.</span><span class="sxs-lookup"><span data-stu-id="01628-146">Replace any duplicate procedures that may exist, such as `Form_Load`, or `Button_Click`.</span></span>  
  
 [!code-vb[VbVbalrEvents#15](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_3.vb)]  
  
 <span data-ttu-id="01628-147">Stisknutím klávesy F5 spusťte v předchozím příkladu a klikněte na tlačítko s popiskem **Start**.</span><span class="sxs-lookup"><span data-stu-id="01628-147">Press F5 to run the preceding example, and click the button labeled **Start**.</span></span> <span data-ttu-id="01628-148">Prvního textového pole spustí odpočet sekundy.</span><span class="sxs-lookup"><span data-stu-id="01628-148">The first text box starts to count down the seconds.</span></span> <span data-ttu-id="01628-149">Po uplynutí doby úplné (10 sekund), se zobrazí "Hotovo" prvního textového pole.</span><span class="sxs-lookup"><span data-stu-id="01628-149">When the full time (10 seconds) has elapsed, the first text box displays "Done".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="01628-150">`My.Application.DoEvents` Metoda nezpracovává události stejným způsobem, stejně jako formulář.</span><span class="sxs-lookup"><span data-stu-id="01628-150">The `My.Application.DoEvents` method does not process events in exactly the same way as the form does.</span></span> <span data-ttu-id="01628-151">Povolit formulář pro zpracování událostí přímo, můžete použít multithreadingu.</span><span class="sxs-lookup"><span data-stu-id="01628-151">To allow the form to handle the events directly, you can use multithreading.</span></span> <span data-ttu-id="01628-152">Další informace najdete v tématu [zřetězení](../../programming-guide/concepts/threading/index.md).</span><span class="sxs-lookup"><span data-stu-id="01628-152">For more information, see [Threading](../../programming-guide/concepts/threading/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01628-153">Viz také</span><span class="sxs-lookup"><span data-stu-id="01628-153">See Also</span></span>  
 [<span data-ttu-id="01628-154">Události</span><span class="sxs-lookup"><span data-stu-id="01628-154">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)  
 [<span data-ttu-id="01628-155">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="01628-155">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="01628-156">Příkaz AddHandler</span><span class="sxs-lookup"><span data-stu-id="01628-156">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)  
 [<span data-ttu-id="01628-157">Příkaz RemoveHandler</span><span class="sxs-lookup"><span data-stu-id="01628-157">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [<span data-ttu-id="01628-158">Obslužné rutiny</span><span class="sxs-lookup"><span data-stu-id="01628-158">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
