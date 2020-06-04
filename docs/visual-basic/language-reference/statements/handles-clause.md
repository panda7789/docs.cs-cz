---
title: Handles – klauzule
ms.date: 07/20/2015
f1_keywords:
- Handles
- vb.Handles
helpviewer_keywords:
- Handles keyword [Visual Basic]
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
ms.openlocfilehash: df786e4b0f0ab3795592ea57f7af17695b086cfa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404573"
---
# <a name="handles-clause-visual-basic"></a><span data-ttu-id="6d152-102">Handles – Klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6d152-102">Handles Clause (Visual Basic)</span></span>
<span data-ttu-id="6d152-103">Deklaruje, že procedura zpracovává určenou událost.</span><span class="sxs-lookup"><span data-stu-id="6d152-103">Declares that a procedure handles a specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d152-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d152-104">Syntax</span></span>  
  
```vb  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a><span data-ttu-id="6d152-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="6d152-105">Parts</span></span>  
 `proceduredeclaration`  
 <span data-ttu-id="6d152-106">`Sub`Deklarace procedury pro proceduru, která zpracuje událost.</span><span class="sxs-lookup"><span data-stu-id="6d152-106">The `Sub` procedure declaration for the procedure that will handle the event.</span></span>  
  
 `eventlist`  
 <span data-ttu-id="6d152-107">Seznam událostí `proceduredeclaration` , které se mají zpracovat, oddělené čárkami</span><span class="sxs-lookup"><span data-stu-id="6d152-107">List of the events for `proceduredeclaration` to handle, separated by commas.</span></span> <span data-ttu-id="6d152-108">Události musí být vyvolány buď základní třídou pro aktuální třídu, nebo objektem deklarovaným pomocí `WithEvents` klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="6d152-108">The events must be raised by either the base class for the current class, or by an object declared using the `WithEvents` keyword.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d152-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6d152-109">Remarks</span></span>  
 <span data-ttu-id="6d152-110">Použijte `Handles` klíčové slovo na konci deklarace procedury k tomu, aby zpracovával události vyvolané proměnnou objektu deklarované pomocí `WithEvents` klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="6d152-110">Use the `Handles` keyword at the end of a procedure declaration to cause it to handle events raised by an object variable declared using the `WithEvents` keyword.</span></span> <span data-ttu-id="6d152-111">`Handles`Klíčové slovo lze také použít v odvozené třídě pro zpracování událostí ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="6d152-111">The `Handles` keyword can also be used in a derived class to handle events from a base class.</span></span>  
  
 <span data-ttu-id="6d152-112">`Handles`Klíčové slovo a `AddHandler` příkaz umožňují určit, že konkrétní procedury budou zpracovávat konkrétní události, ale existují rozdíly.</span><span class="sxs-lookup"><span data-stu-id="6d152-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="6d152-113">`Handles`Při definování procedury použijte klíčové slovo, které určuje, že zpracuje konkrétní událost.</span><span class="sxs-lookup"><span data-stu-id="6d152-113">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="6d152-114">`AddHandler`Příkaz propojuje procedury s událostmi v době běhu.</span><span class="sxs-lookup"><span data-stu-id="6d152-114">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="6d152-115">Další informace naleznete v tématu [addHandler – příkaz](addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6d152-115">For more information, see [AddHandler Statement](addhandler-statement.md).</span></span>  
  
 <span data-ttu-id="6d152-116">Pro vlastní události aplikace vyvolá `AddHandler` přistupující objekt události při přidání procedury jako obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="6d152-116">For custom events, the application invokes the event's `AddHandler` accessor when it adds the procedure as an event handler.</span></span> <span data-ttu-id="6d152-117">Další informace o vlastních událostech naleznete v tématu [příkaz Event](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6d152-117">For more information on custom events, see [Event Statement](event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d152-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="6d152-118">Example</span></span>  
 [!code-vb[VbVbalrEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#2)]  
  
 <span data-ttu-id="6d152-119">Následující příklad ukazuje, jak může odvozená třída použít `Handles` příkaz ke zpracování události ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="6d152-119">The following example demonstrates how a derived class can use the `Handles` statement to handle an event from a base class.</span></span>  
  
 [!code-vb[VbVbalrEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="6d152-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="6d152-120">Example</span></span>  
 <span data-ttu-id="6d152-121">Následující příklad obsahuje dvě obslužné rutiny událostí tlačítek pro projekt **aplikace WPF** .</span><span class="sxs-lookup"><span data-stu-id="6d152-121">The following example contains two button event handlers for a **WPF Application** project.</span></span>  
  
 [!code-vb[VbVbalrEvents#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#41)]  
  
## <a name="example"></a><span data-ttu-id="6d152-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="6d152-122">Example</span></span>  
 <span data-ttu-id="6d152-123">Následující příklad je ekvivalentní k předchozímu příkladu.</span><span class="sxs-lookup"><span data-stu-id="6d152-123">The following example is equivalent to the previous example.</span></span> <span data-ttu-id="6d152-124">`eventlist` `Handles` Klauzule in obsahuje události pro obě tlačítka.</span><span class="sxs-lookup"><span data-stu-id="6d152-124">The `eventlist` in the `Handles` clause contains the events for both buttons.</span></span>  
  
 [!code-vb[VbVbalrEvents#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#42)]  
  
## <a name="see-also"></a><span data-ttu-id="6d152-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="6d152-125">See also</span></span>

- [<span data-ttu-id="6d152-126">WithEvents</span><span class="sxs-lookup"><span data-stu-id="6d152-126">WithEvents</span></span>](../modifiers/withevents.md)
- [<span data-ttu-id="6d152-127">AddHandler – příkaz</span><span class="sxs-lookup"><span data-stu-id="6d152-127">AddHandler Statement</span></span>](addhandler-statement.md)
- [<span data-ttu-id="6d152-128">RemoveHandler – příkaz</span><span class="sxs-lookup"><span data-stu-id="6d152-128">RemoveHandler Statement</span></span>](removehandler-statement.md)
- [<span data-ttu-id="6d152-129">Event – příkaz</span><span class="sxs-lookup"><span data-stu-id="6d152-129">Event Statement</span></span>](event-statement.md)
- [<span data-ttu-id="6d152-130">RaiseEvent – příkaz</span><span class="sxs-lookup"><span data-stu-id="6d152-130">RaiseEvent Statement</span></span>](raiseevent-statement.md)
- [<span data-ttu-id="6d152-131">Události</span><span class="sxs-lookup"><span data-stu-id="6d152-131">Events</span></span>](../../programming-guide/language-features/events/index.md)
