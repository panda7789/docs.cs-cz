---
title: Handles – Klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Handles
- vb.Handles
helpviewer_keywords:
- Handles keyword [Visual Basic]
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
ms.openlocfilehash: ae05e77515e4e2b50cdf5f9a1908375fa311c3a3
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581802"
---
# <a name="handles-clause-visual-basic"></a><span data-ttu-id="aa05e-102">Handles – Klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aa05e-102">Handles Clause (Visual Basic)</span></span>
<span data-ttu-id="aa05e-103">Deklaruje, že procedura zpracovává určenou událost.</span><span class="sxs-lookup"><span data-stu-id="aa05e-103">Declares that a procedure handles a specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa05e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aa05e-104">Syntax</span></span>  
  
```vb  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a><span data-ttu-id="aa05e-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="aa05e-105">Parts</span></span>  
 `proceduredeclaration`  
 <span data-ttu-id="aa05e-106">Deklarace procedury `Sub` pro proceduru, která zpracuje událost.</span><span class="sxs-lookup"><span data-stu-id="aa05e-106">The `Sub` procedure declaration for the procedure that will handle the event.</span></span>  
  
 `eventlist`  
 <span data-ttu-id="aa05e-107">Seznam událostí pro `proceduredeclaration`, které se mají zpracovat, oddělené čárkami</span><span class="sxs-lookup"><span data-stu-id="aa05e-107">List of the events for `proceduredeclaration` to handle, separated by commas.</span></span> <span data-ttu-id="aa05e-108">Události musí být vyvolány buď základní třídou pro aktuální třídu, nebo objektem deklarovaným pomocí klíčového slova `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="aa05e-108">The events must be raised by either the base class for the current class, or by an object declared using the `WithEvents` keyword.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa05e-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aa05e-109">Remarks</span></span>  
 <span data-ttu-id="aa05e-110">Použijte klíčové slovo `Handles` na konci deklarace procedury k tomu, aby zpracovával události vyvolané proměnnou objektu deklarované pomocí klíčového slova `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="aa05e-110">Use the `Handles` keyword at the end of a procedure declaration to cause it to handle events raised by an object variable declared using the `WithEvents` keyword.</span></span> <span data-ttu-id="aa05e-111">Klíčové slovo `Handles` lze také použít v odvozené třídě pro zpracování událostí ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="aa05e-111">The `Handles` keyword can also be used in a derived class to handle events from a base class.</span></span>  
  
 <span data-ttu-id="aa05e-112">Klíčové slovo `Handles` a příkaz `AddHandler` umožňují určit, že konkrétní procedury budou zpracovávat konkrétní události, ale existují rozdíly.</span><span class="sxs-lookup"><span data-stu-id="aa05e-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="aa05e-113">Při definování procedury použijte klíčové slovo `Handles`, které určuje, že zpracuje konkrétní událost.</span><span class="sxs-lookup"><span data-stu-id="aa05e-113">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="aa05e-114">Příkaz `AddHandler` spojuje procedury s událostmi v době běhu.</span><span class="sxs-lookup"><span data-stu-id="aa05e-114">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="aa05e-115">Další informace naleznete v tématu [addHandler – příkaz](../../../visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="aa05e-115">For more information, see [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span>  
  
 <span data-ttu-id="aa05e-116">Pro vlastní události aplikace vyvolá přistupující objekt `AddHandler` události při přidání procedury jako obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="aa05e-116">For custom events, the application invokes the event's `AddHandler` accessor when it adds the procedure as an event handler.</span></span> <span data-ttu-id="aa05e-117">Další informace o vlastních událostech naleznete v tématu [příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="aa05e-117">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa05e-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="aa05e-118">Example</span></span>  
 [!code-vb[VbVbalrEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#2)]  
  
 <span data-ttu-id="aa05e-119">Následující příklad ukazuje, jak může odvozená třída použít příkaz `Handles` ke zpracování události ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="aa05e-119">The following example demonstrates how a derived class can use the `Handles` statement to handle an event from a base class.</span></span>  
  
 [!code-vb[VbVbalrEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="aa05e-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="aa05e-120">Example</span></span>  
 <span data-ttu-id="aa05e-121">Následující příklad obsahuje dvě obslužné rutiny událostí tlačítek pro projekt **aplikace WPF** .</span><span class="sxs-lookup"><span data-stu-id="aa05e-121">The following example contains two button event handlers for a **WPF Application** project.</span></span>  
  
 [!code-vb[VbVbalrEvents#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#41)]  
  
## <a name="example"></a><span data-ttu-id="aa05e-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="aa05e-122">Example</span></span>  
 <span data-ttu-id="aa05e-123">Následující příklad je ekvivalentní k předchozímu příkladu.</span><span class="sxs-lookup"><span data-stu-id="aa05e-123">The following example is equivalent to the previous example.</span></span> <span data-ttu-id="aa05e-124">@No__t_0 v klauzuli `Handles` obsahuje události pro obě tlačítka.</span><span class="sxs-lookup"><span data-stu-id="aa05e-124">The `eventlist` in the `Handles` clause contains the events for both buttons.</span></span>  
  
 [!code-vb[VbVbalrEvents#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#42)]  
  
## <a name="see-also"></a><span data-ttu-id="aa05e-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aa05e-125">See also</span></span>

- [<span data-ttu-id="aa05e-126">WithEvents</span><span class="sxs-lookup"><span data-stu-id="aa05e-126">WithEvents</span></span>](../../../visual-basic/language-reference/modifiers/withevents.md)
- [<span data-ttu-id="aa05e-127">Příkaz AddHandler</span><span class="sxs-lookup"><span data-stu-id="aa05e-127">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [<span data-ttu-id="aa05e-128">Příkaz RemoveHandler</span><span class="sxs-lookup"><span data-stu-id="aa05e-128">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [<span data-ttu-id="aa05e-129">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="aa05e-129">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="aa05e-130">Příkaz RaiseEvent</span><span class="sxs-lookup"><span data-stu-id="aa05e-130">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
- [<span data-ttu-id="aa05e-131">Události</span><span class="sxs-lookup"><span data-stu-id="aa05e-131">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
