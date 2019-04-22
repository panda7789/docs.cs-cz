---
title: Handles – Klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Handles
- vb.Handles
helpviewer_keywords:
- Handles keyword [Visual Basic]
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
ms.openlocfilehash: 50a449ea8a5131c878cf703f44695cd2e2304444
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58842574"
---
# <a name="handles-clause-visual-basic"></a><span data-ttu-id="feffa-102">Handles – Klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="feffa-102">Handles Clause (Visual Basic)</span></span>
<span data-ttu-id="feffa-103">Deklaruje, že procedura zpracovává určenou událost.</span><span class="sxs-lookup"><span data-stu-id="feffa-103">Declares that a procedure handles a specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="feffa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="feffa-104">Syntax</span></span>  
  
```  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a><span data-ttu-id="feffa-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="feffa-105">Parts</span></span>  
 `proceduredeclaration`  
 <span data-ttu-id="feffa-106">`Sub` Deklarace procedury pro proces, který bude zpracovávat události.</span><span class="sxs-lookup"><span data-stu-id="feffa-106">The `Sub` procedure declaration for the procedure that will handle the event.</span></span>  
  
 `eventlist`  
 <span data-ttu-id="feffa-107">Seznam událostí pro `proceduredeclaration` pro zpracování, oddělené čárkami.</span><span class="sxs-lookup"><span data-stu-id="feffa-107">List of the events for `proceduredeclaration` to handle, separated by commas.</span></span> <span data-ttu-id="feffa-108">Události musí být vyvolány, buď základní třídou pro aktuální třídu nebo objektem deklarovány pomocí `WithEvents` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="feffa-108">The events must be raised by either the base class for the current class, or by an object declared using the `WithEvents` keyword.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="feffa-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="feffa-109">Remarks</span></span>  
 <span data-ttu-id="feffa-110">Použití `Handles` klíčového slova na konci deklaraci procedury způsobit zpracovávat události vyvolané službou objektová proměnná deklarovaná pomocí `WithEvents` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="feffa-110">Use the `Handles` keyword at the end of a procedure declaration to cause it to handle events raised by an object variable declared using the `WithEvents` keyword.</span></span> <span data-ttu-id="feffa-111">`Handles` – Klíčové slovo lze použít také v odvozené třídě pro zpracování událostí ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="feffa-111">The `Handles` keyword can also be used in a derived class to handle events from a base class.</span></span>  
  
 <span data-ttu-id="feffa-112">`Handles` – Klíčové slovo a `AddHandler` příkaz oba umožňují určit, že konkrétní postupy zpracování určité události, ale existují rozdíly.</span><span class="sxs-lookup"><span data-stu-id="feffa-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="feffa-113">Použití `Handles` – klíčové slovo při definování proceduru k určení, že zpracovává konkrétní události.</span><span class="sxs-lookup"><span data-stu-id="feffa-113">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="feffa-114">`AddHandler` Příkaz se připojí postupy k událostem v době běhu.</span><span class="sxs-lookup"><span data-stu-id="feffa-114">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="feffa-115">Další informace najdete v tématu [AddHandler – příkaz](../../../visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="feffa-115">For more information, see [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span>  
  
 <span data-ttu-id="feffa-116">Pro vlastní události aplikace vyvolává události `AddHandler` přistupujícího objektu, když přidá postup jako obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="feffa-116">For custom events, the application invokes the event's `AddHandler` accessor when it adds the procedure as an event handler.</span></span> <span data-ttu-id="feffa-117">Další informace o vlastních událostech najdete v tématu [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="feffa-117">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="feffa-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="feffa-118">Example</span></span>  
 [!code-vb[VbVbalrEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#2)]  
  
 <span data-ttu-id="feffa-119">Následující příklad ukazuje, jak můžete použít odvozenou třídu `Handles` příkaz pro zpracování události ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="feffa-119">The following example demonstrates how a derived class can use the `Handles` statement to handle an event from a base class.</span></span>  
  
 [!code-vb[VbVbalrEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="feffa-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="feffa-120">Example</span></span>  
 <span data-ttu-id="feffa-121">Následující příklad obsahuje dva tlačítko obslužné rutiny **aplikace WPF** projektu.</span><span class="sxs-lookup"><span data-stu-id="feffa-121">The following example contains two button event handlers for a **WPF Application** project.</span></span>  
  
 [!code-vb[VbVbalrEvents#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#41)]  
  
## <a name="example"></a><span data-ttu-id="feffa-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="feffa-122">Example</span></span>  
 <span data-ttu-id="feffa-123">Následující příklad je ekvivalentní předchozí příklad.</span><span class="sxs-lookup"><span data-stu-id="feffa-123">The following example is equivalent to the previous example.</span></span> <span data-ttu-id="feffa-124">`eventlist` v `Handles` klauzule WHERE obsahuje události pro obě tlačítka.</span><span class="sxs-lookup"><span data-stu-id="feffa-124">The `eventlist` in the `Handles` clause contains the events for both buttons.</span></span>  
  
 [!code-vb[VbVbalrEvents#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#42)]  
  
## <a name="see-also"></a><span data-ttu-id="feffa-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="feffa-125">See also</span></span>

- [<span data-ttu-id="feffa-126">WithEvents</span><span class="sxs-lookup"><span data-stu-id="feffa-126">WithEvents</span></span>](../../../visual-basic/language-reference/modifiers/withevents.md)
- [<span data-ttu-id="feffa-127">Příkaz AddHandler</span><span class="sxs-lookup"><span data-stu-id="feffa-127">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [<span data-ttu-id="feffa-128">Příkaz RemoveHandler</span><span class="sxs-lookup"><span data-stu-id="feffa-128">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [<span data-ttu-id="feffa-129">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="feffa-129">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="feffa-130">Příkaz RaiseEvent</span><span class="sxs-lookup"><span data-stu-id="feffa-130">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
- [<span data-ttu-id="feffa-131">Události</span><span class="sxs-lookup"><span data-stu-id="feffa-131">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
