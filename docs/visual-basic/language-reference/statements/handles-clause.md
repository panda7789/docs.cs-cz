---
title: "Handles – Klauzule (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- Handles
- vb.Handles
helpviewer_keywords:
- Handles keyword [Visual Basic]
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a23b3d96052ad179ea25150bb570461a9e764977
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="handles-clause-visual-basic"></a><span data-ttu-id="922ac-102">Handles – Klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="922ac-102">Handles Clause (Visual Basic)</span></span>
<span data-ttu-id="922ac-103">Deklaruje, že procedury zpracovává zadané události.</span><span class="sxs-lookup"><span data-stu-id="922ac-103">Declares that a procedure handles a specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="922ac-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="922ac-104">Syntax</span></span>  
  
```  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a><span data-ttu-id="922ac-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="922ac-105">Parts</span></span>  
 `proceduredeclaration`  
 <span data-ttu-id="922ac-106">`Sub` Postup deklarace pro proceduru, která zpracovává událost.</span><span class="sxs-lookup"><span data-stu-id="922ac-106">The `Sub` procedure declaration for the procedure that will handle the event.</span></span>  
  
 `eventlist`  
 <span data-ttu-id="922ac-107">Seznam událostí pro `proceduredeclaration` pro zpracování, oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="922ac-107">List of the events for `proceduredeclaration` to handle, separated by commas.</span></span> <span data-ttu-id="922ac-108">Události musí být vyvolány buď základní třída pro aktuální třídu nebo objektem deklarováno s použitím `WithEvents` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="922ac-108">The events must be raised by either the base class for the current class, or by an object declared using the `WithEvents` keyword.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="922ac-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="922ac-109">Remarks</span></span>  
 <span data-ttu-id="922ac-110">Použití `Handles` – klíčové slovo na konci tohoto postupu deklarace způsobí zpracovávat události vyvolané službou proměnné objektu deklarováno s použitím `WithEvents` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="922ac-110">Use the `Handles` keyword at the end of a procedure declaration to cause it to handle events raised by an object variable declared using the `WithEvents` keyword.</span></span> <span data-ttu-id="922ac-111">`Handles` – Klíčové slovo lze použít také v odvozené třídě zpracování událostí ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="922ac-111">The `Handles` keyword can also be used in a derived class to handle events from a base class.</span></span>  
  
 <span data-ttu-id="922ac-112">`Handles` – Klíčové slovo a `AddHandler` příkaz oba umožňují určit, že konkrétní postupy zpracování konkrétní události, ale jsou rozdíly.</span><span class="sxs-lookup"><span data-stu-id="922ac-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="922ac-113">Použití `Handles` – klíčové slovo při definování postup, chcete-li určit, která byla zjištěna určitá událost.</span><span class="sxs-lookup"><span data-stu-id="922ac-113">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="922ac-114">`AddHandler` Příkaz připojí postupy pro události za běhu.</span><span class="sxs-lookup"><span data-stu-id="922ac-114">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="922ac-115">Další informace najdete v tématu [AddHandler – příkaz](../../../visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="922ac-115">For more information, see [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span>  
  
 <span data-ttu-id="922ac-116">Pro vlastní události aplikace spustí události `AddHandler` přistupujícího objektu, když přidá postupu jako obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="922ac-116">For custom events, the application invokes the event's `AddHandler` accessor when it adds the procedure as an event handler.</span></span> <span data-ttu-id="922ac-117">Další informace o vlastních událostí najdete v tématu [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="922ac-117">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="922ac-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="922ac-118">Example</span></span>  
 [!code-vb[VbVbalrEvents#2](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_1.vb)]  
  
 <span data-ttu-id="922ac-119">Následující příklad ukazuje, jak můžete použít třídu odvozenou `Handles` příkaz zpracovat události ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="922ac-119">The following example demonstrates how a derived class can use the `Handles` statement to handle an event from a base class.</span></span>  
  
 [!code-vb[VbVbalrEvents#3](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="922ac-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="922ac-120">Example</span></span>  
 <span data-ttu-id="922ac-121">Následující příklad obsahuje dvě obslužné rutiny tlačítko událostí pro **aplikaci WPF** projektu.</span><span class="sxs-lookup"><span data-stu-id="922ac-121">The following example contains two button event handlers for a **WPF Application** project.</span></span>  
  
 [!code-vb[VbVbalrEvents#41](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="922ac-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="922ac-122">Example</span></span>  
 <span data-ttu-id="922ac-123">Následující příklad je ekvivalentní předchozí příklad.</span><span class="sxs-lookup"><span data-stu-id="922ac-123">The following example is equivalent to the previous example.</span></span> <span data-ttu-id="922ac-124">`eventlist` v `Handles` klauzule WHERE obsahuje události pro obě tlačítka.</span><span class="sxs-lookup"><span data-stu-id="922ac-124">The `eventlist` in the `Handles` clause contains the events for both buttons.</span></span>  
  
 [!code-vb[VbVbalrEvents#42](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="922ac-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="922ac-125">See Also</span></span>  
 [<span data-ttu-id="922ac-126">WithEvents</span><span class="sxs-lookup"><span data-stu-id="922ac-126">WithEvents</span></span>](../../../visual-basic/language-reference/modifiers/withevents.md)  
 [<span data-ttu-id="922ac-127">AddHandler – příkaz</span><span class="sxs-lookup"><span data-stu-id="922ac-127">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)  
 [<span data-ttu-id="922ac-128">RemoveHandler – příkaz</span><span class="sxs-lookup"><span data-stu-id="922ac-128">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [<span data-ttu-id="922ac-129">Event – příkaz</span><span class="sxs-lookup"><span data-stu-id="922ac-129">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="922ac-130">RaiseEvent – příkaz</span><span class="sxs-lookup"><span data-stu-id="922ac-130">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)  
 [<span data-ttu-id="922ac-131">Události</span><span class="sxs-lookup"><span data-stu-id="922ac-131">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
