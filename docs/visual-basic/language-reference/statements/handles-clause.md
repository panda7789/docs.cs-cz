---
title: Handles – klauzule
ms.date: 07/20/2015
f1_keywords:
- Handles
- vb.Handles
helpviewer_keywords:
- Handles keyword [Visual Basic]
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
ms.openlocfilehash: 2fecad919722f3da25c48f133a9c92b5e683d5e4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345913"
---
# <a name="handles-clause-visual-basic"></a><span data-ttu-id="176ee-102">Handles – Klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="176ee-102">Handles Clause (Visual Basic)</span></span>
<span data-ttu-id="176ee-103">Declares that a procedure handles a specified event.</span><span class="sxs-lookup"><span data-stu-id="176ee-103">Declares that a procedure handles a specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="176ee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="176ee-104">Syntax</span></span>  
  
```vb  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a><span data-ttu-id="176ee-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="176ee-105">Parts</span></span>  
 `proceduredeclaration`  
 <span data-ttu-id="176ee-106">The `Sub` procedure declaration for the procedure that will handle the event.</span><span class="sxs-lookup"><span data-stu-id="176ee-106">The `Sub` procedure declaration for the procedure that will handle the event.</span></span>  
  
 `eventlist`  
 <span data-ttu-id="176ee-107">List of the events for `proceduredeclaration` to handle, separated by commas.</span><span class="sxs-lookup"><span data-stu-id="176ee-107">List of the events for `proceduredeclaration` to handle, separated by commas.</span></span> <span data-ttu-id="176ee-108">The events must be raised by either the base class for the current class, or by an object declared using the `WithEvents` keyword.</span><span class="sxs-lookup"><span data-stu-id="176ee-108">The events must be raised by either the base class for the current class, or by an object declared using the `WithEvents` keyword.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="176ee-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="176ee-109">Remarks</span></span>  
 <span data-ttu-id="176ee-110">Use the `Handles` keyword at the end of a procedure declaration to cause it to handle events raised by an object variable declared using the `WithEvents` keyword.</span><span class="sxs-lookup"><span data-stu-id="176ee-110">Use the `Handles` keyword at the end of a procedure declaration to cause it to handle events raised by an object variable declared using the `WithEvents` keyword.</span></span> <span data-ttu-id="176ee-111">The `Handles` keyword can also be used in a derived class to handle events from a base class.</span><span class="sxs-lookup"><span data-stu-id="176ee-111">The `Handles` keyword can also be used in a derived class to handle events from a base class.</span></span>  
  
 <span data-ttu-id="176ee-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span><span class="sxs-lookup"><span data-stu-id="176ee-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="176ee-113">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span><span class="sxs-lookup"><span data-stu-id="176ee-113">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="176ee-114">The `AddHandler` statement connects procedures to events at run time.</span><span class="sxs-lookup"><span data-stu-id="176ee-114">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="176ee-115">For more information, see [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="176ee-115">For more information, see [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span>  
  
 <span data-ttu-id="176ee-116">For custom events, the application invokes the event's `AddHandler` accessor when it adds the procedure as an event handler.</span><span class="sxs-lookup"><span data-stu-id="176ee-116">For custom events, the application invokes the event's `AddHandler` accessor when it adds the procedure as an event handler.</span></span> <span data-ttu-id="176ee-117">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="176ee-117">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="176ee-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="176ee-118">Example</span></span>  
 [!code-vb[VbVbalrEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#2)]  
  
 <span data-ttu-id="176ee-119">The following example demonstrates how a derived class can use the `Handles` statement to handle an event from a base class.</span><span class="sxs-lookup"><span data-stu-id="176ee-119">The following example demonstrates how a derived class can use the `Handles` statement to handle an event from a base class.</span></span>  
  
 [!code-vb[VbVbalrEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="176ee-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="176ee-120">Example</span></span>  
 <span data-ttu-id="176ee-121">The following example contains two button event handlers for a **WPF Application** project.</span><span class="sxs-lookup"><span data-stu-id="176ee-121">The following example contains two button event handlers for a **WPF Application** project.</span></span>  
  
 [!code-vb[VbVbalrEvents#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#41)]  
  
## <a name="example"></a><span data-ttu-id="176ee-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="176ee-122">Example</span></span>  
 <span data-ttu-id="176ee-123">The following example is equivalent to the previous example.</span><span class="sxs-lookup"><span data-stu-id="176ee-123">The following example is equivalent to the previous example.</span></span> <span data-ttu-id="176ee-124">The `eventlist` in the `Handles` clause contains the events for both buttons.</span><span class="sxs-lookup"><span data-stu-id="176ee-124">The `eventlist` in the `Handles` clause contains the events for both buttons.</span></span>  
  
 [!code-vb[VbVbalrEvents#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#42)]  
  
## <a name="see-also"></a><span data-ttu-id="176ee-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="176ee-125">See also</span></span>

- [<span data-ttu-id="176ee-126">WithEvents</span><span class="sxs-lookup"><span data-stu-id="176ee-126">WithEvents</span></span>](../../../visual-basic/language-reference/modifiers/withevents.md)
- [<span data-ttu-id="176ee-127">Příkaz AddHandler</span><span class="sxs-lookup"><span data-stu-id="176ee-127">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [<span data-ttu-id="176ee-128">Příkaz RemoveHandler</span><span class="sxs-lookup"><span data-stu-id="176ee-128">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [<span data-ttu-id="176ee-129">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="176ee-129">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="176ee-130">Příkaz RaiseEvent</span><span class="sxs-lookup"><span data-stu-id="176ee-130">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
- [<span data-ttu-id="176ee-131">Události</span><span class="sxs-lookup"><span data-stu-id="176ee-131">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
