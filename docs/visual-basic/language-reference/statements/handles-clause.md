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
# <a name="handles-clause-visual-basic"></a><span data-ttu-id="a2b48-102">Handles – Klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2b48-102">Handles Clause (Visual Basic)</span></span>
<span data-ttu-id="a2b48-103">Deklaruje, že procedura zpracovává určenou událost.</span><span class="sxs-lookup"><span data-stu-id="a2b48-103">Declares that a procedure handles a specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2b48-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a2b48-104">Syntax</span></span>  
  
```vb  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a><span data-ttu-id="a2b48-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="a2b48-105">Parts</span></span>  
 `proceduredeclaration`  
 <span data-ttu-id="a2b48-106">Deklarace procedury `Sub` pro proceduru, která zpracuje událost.</span><span class="sxs-lookup"><span data-stu-id="a2b48-106">The `Sub` procedure declaration for the procedure that will handle the event.</span></span>  
  
 `eventlist`  
 <span data-ttu-id="a2b48-107">Seznam událostí pro `proceduredeclaration`, které se mají zpracovat, oddělené čárkami</span><span class="sxs-lookup"><span data-stu-id="a2b48-107">List of the events for `proceduredeclaration` to handle, separated by commas.</span></span> <span data-ttu-id="a2b48-108">Události musí být vyvolány buď základní třídou pro aktuální třídu, nebo objektem deklarovaným pomocí klíčového slova `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="a2b48-108">The events must be raised by either the base class for the current class, or by an object declared using the `WithEvents` keyword.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2b48-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a2b48-109">Remarks</span></span>  
 <span data-ttu-id="a2b48-110">Použijte klíčové slovo `Handles` na konci deklarace procedury k tomu, aby zpracovával události vyvolané proměnnou objektu deklarované pomocí klíčového slova `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="a2b48-110">Use the `Handles` keyword at the end of a procedure declaration to cause it to handle events raised by an object variable declared using the `WithEvents` keyword.</span></span> <span data-ttu-id="a2b48-111">Klíčové slovo `Handles` lze také použít v odvozené třídě pro zpracování událostí ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="a2b48-111">The `Handles` keyword can also be used in a derived class to handle events from a base class.</span></span>  
  
 <span data-ttu-id="a2b48-112">Klíčové slovo `Handles` a příkaz `AddHandler` umožňují určit, že konkrétní procedury budou zpracovávat konkrétní události, ale existují rozdíly.</span><span class="sxs-lookup"><span data-stu-id="a2b48-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="a2b48-113">Při definování procedury použijte klíčové slovo `Handles`, které určuje, že zpracuje konkrétní událost.</span><span class="sxs-lookup"><span data-stu-id="a2b48-113">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="a2b48-114">Příkaz `AddHandler` propojuje procedury s událostmi v době běhu.</span><span class="sxs-lookup"><span data-stu-id="a2b48-114">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="a2b48-115">Další informace naleznete v tématu [addHandler – příkaz](../../../visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a2b48-115">For more information, see [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span>  
  
 <span data-ttu-id="a2b48-116">Pro vlastní události aplikace vyvolá přistupující objekt `AddHandler` události při přidání procedury jako obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="a2b48-116">For custom events, the application invokes the event's `AddHandler` accessor when it adds the procedure as an event handler.</span></span> <span data-ttu-id="a2b48-117">Další informace o vlastních událostech naleznete v tématu [příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a2b48-117">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2b48-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="a2b48-118">Example</span></span>  
 [!code-vb[VbVbalrEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#2)]  
  
 <span data-ttu-id="a2b48-119">Následující příklad ukazuje, jak může odvozená třída použít příkaz `Handles` ke zpracování události ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="a2b48-119">The following example demonstrates how a derived class can use the `Handles` statement to handle an event from a base class.</span></span>  
  
 [!code-vb[VbVbalrEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="a2b48-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="a2b48-120">Example</span></span>  
 <span data-ttu-id="a2b48-121">Následující příklad obsahuje dvě obslužné rutiny událostí tlačítek pro projekt **aplikace WPF** .</span><span class="sxs-lookup"><span data-stu-id="a2b48-121">The following example contains two button event handlers for a **WPF Application** project.</span></span>  
  
 [!code-vb[VbVbalrEvents#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#41)]  
  
## <a name="example"></a><span data-ttu-id="a2b48-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="a2b48-122">Example</span></span>  
 <span data-ttu-id="a2b48-123">Následující příklad je ekvivalentní k předchozímu příkladu.</span><span class="sxs-lookup"><span data-stu-id="a2b48-123">The following example is equivalent to the previous example.</span></span> <span data-ttu-id="a2b48-124">`eventlist` v klauzuli `Handles` obsahuje události pro obě tlačítka.</span><span class="sxs-lookup"><span data-stu-id="a2b48-124">The `eventlist` in the `Handles` clause contains the events for both buttons.</span></span>  
  
 [!code-vb[VbVbalrEvents#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#42)]  
  
## <a name="see-also"></a><span data-ttu-id="a2b48-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a2b48-125">See also</span></span>

- [<span data-ttu-id="a2b48-126">WithEvents</span><span class="sxs-lookup"><span data-stu-id="a2b48-126">WithEvents</span></span>](../../../visual-basic/language-reference/modifiers/withevents.md)
- [<span data-ttu-id="a2b48-127">Příkaz AddHandler</span><span class="sxs-lookup"><span data-stu-id="a2b48-127">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [<span data-ttu-id="a2b48-128">Příkaz RemoveHandler</span><span class="sxs-lookup"><span data-stu-id="a2b48-128">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [<span data-ttu-id="a2b48-129">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="a2b48-129">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="a2b48-130">Příkaz RaiseEvent</span><span class="sxs-lookup"><span data-stu-id="a2b48-130">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
- [<span data-ttu-id="a2b48-131">Události</span><span class="sxs-lookup"><span data-stu-id="a2b48-131">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
