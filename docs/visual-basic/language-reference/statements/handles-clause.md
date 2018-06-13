---
title: Handles – Klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Handles
- vb.Handles
helpviewer_keywords:
- Handles keyword [Visual Basic]
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
ms.openlocfilehash: 15ce6a25aa5f403a2e55beb57b3693095743e52f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603714"
---
# <a name="handles-clause-visual-basic"></a><span data-ttu-id="394aa-102">Handles – Klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="394aa-102">Handles Clause (Visual Basic)</span></span>
<span data-ttu-id="394aa-103">Deklaruje, že procedury zpracovává zadané události.</span><span class="sxs-lookup"><span data-stu-id="394aa-103">Declares that a procedure handles a specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="394aa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="394aa-104">Syntax</span></span>  
  
```  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a><span data-ttu-id="394aa-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="394aa-105">Parts</span></span>  
 `proceduredeclaration`  
 <span data-ttu-id="394aa-106">`Sub` Postup deklarace pro proceduru, která zpracovává událost.</span><span class="sxs-lookup"><span data-stu-id="394aa-106">The `Sub` procedure declaration for the procedure that will handle the event.</span></span>  
  
 `eventlist`  
 <span data-ttu-id="394aa-107">Seznam událostí pro `proceduredeclaration` pro zpracování, oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="394aa-107">List of the events for `proceduredeclaration` to handle, separated by commas.</span></span> <span data-ttu-id="394aa-108">Události musí být vyvolány buď základní třída pro aktuální třídu nebo objektem deklarováno s použitím `WithEvents` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="394aa-108">The events must be raised by either the base class for the current class, or by an object declared using the `WithEvents` keyword.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="394aa-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="394aa-109">Remarks</span></span>  
 <span data-ttu-id="394aa-110">Použití `Handles` – klíčové slovo na konci tohoto postupu deklarace způsobí zpracovávat události vyvolané službou proměnné objektu deklarováno s použitím `WithEvents` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="394aa-110">Use the `Handles` keyword at the end of a procedure declaration to cause it to handle events raised by an object variable declared using the `WithEvents` keyword.</span></span> <span data-ttu-id="394aa-111">`Handles` – Klíčové slovo lze použít také v odvozené třídě zpracování událostí ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="394aa-111">The `Handles` keyword can also be used in a derived class to handle events from a base class.</span></span>  
  
 <span data-ttu-id="394aa-112">`Handles` – Klíčové slovo a `AddHandler` příkaz oba umožňují určit, že konkrétní postupy zpracování konkrétní události, ale jsou rozdíly.</span><span class="sxs-lookup"><span data-stu-id="394aa-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="394aa-113">Použití `Handles` – klíčové slovo při definování postup, chcete-li určit, která byla zjištěna určitá událost.</span><span class="sxs-lookup"><span data-stu-id="394aa-113">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="394aa-114">`AddHandler` Příkaz připojí postupy pro události za běhu.</span><span class="sxs-lookup"><span data-stu-id="394aa-114">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="394aa-115">Další informace najdete v tématu [AddHandler – příkaz](../../../visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="394aa-115">For more information, see [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span>  
  
 <span data-ttu-id="394aa-116">Pro vlastní události aplikace spustí události `AddHandler` přistupujícího objektu, když přidá postupu jako obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="394aa-116">For custom events, the application invokes the event's `AddHandler` accessor when it adds the procedure as an event handler.</span></span> <span data-ttu-id="394aa-117">Další informace o vlastních událostí najdete v tématu [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="394aa-117">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="394aa-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="394aa-118">Example</span></span>  
 [!code-vb[VbVbalrEvents#2](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_1.vb)]  
  
 <span data-ttu-id="394aa-119">Následující příklad ukazuje, jak můžete použít třídu odvozenou `Handles` příkaz zpracovat události ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="394aa-119">The following example demonstrates how a derived class can use the `Handles` statement to handle an event from a base class.</span></span>  
  
 [!code-vb[VbVbalrEvents#3](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="394aa-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="394aa-120">Example</span></span>  
 <span data-ttu-id="394aa-121">Následující příklad obsahuje dvě obslužné rutiny tlačítko událostí pro **aplikaci WPF** projektu.</span><span class="sxs-lookup"><span data-stu-id="394aa-121">The following example contains two button event handlers for a **WPF Application** project.</span></span>  
  
 [!code-vb[VbVbalrEvents#41](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="394aa-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="394aa-122">Example</span></span>  
 <span data-ttu-id="394aa-123">Následující příklad je ekvivalentní předchozí příklad.</span><span class="sxs-lookup"><span data-stu-id="394aa-123">The following example is equivalent to the previous example.</span></span> <span data-ttu-id="394aa-124">`eventlist` v `Handles` klauzule WHERE obsahuje události pro obě tlačítka.</span><span class="sxs-lookup"><span data-stu-id="394aa-124">The `eventlist` in the `Handles` clause contains the events for both buttons.</span></span>  
  
 [!code-vb[VbVbalrEvents#42](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="394aa-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="394aa-125">See Also</span></span>  
 [<span data-ttu-id="394aa-126">WithEvents</span><span class="sxs-lookup"><span data-stu-id="394aa-126">WithEvents</span></span>](../../../visual-basic/language-reference/modifiers/withevents.md)  
 [<span data-ttu-id="394aa-127">Příkaz AddHandler</span><span class="sxs-lookup"><span data-stu-id="394aa-127">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)  
 [<span data-ttu-id="394aa-128">Příkaz RemoveHandler</span><span class="sxs-lookup"><span data-stu-id="394aa-128">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [<span data-ttu-id="394aa-129">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="394aa-129">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="394aa-130">Příkaz RaiseEvent</span><span class="sxs-lookup"><span data-stu-id="394aa-130">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)  
 [<span data-ttu-id="394aa-131">Události</span><span class="sxs-lookup"><span data-stu-id="394aa-131">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
