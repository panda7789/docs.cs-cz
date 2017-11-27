---
title: "Postupy: Volání obslužné rutiny události (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- event handlers [Visual Basic], calling
- event handlers
- procedures [Visual Basic], event handlers
- procedures [Visual Basic], calling
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 52b4b6ca8b03d8301535d6aeedc3bd0190d8527f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a><span data-ttu-id="9f778-102">Postupy: Volání obslužné rutiny události (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f778-102">How to: Call an Event Handler in Visual Basic</span></span>
<span data-ttu-id="9f778-103">*Událostí* je akce nebo výskyt – například myši klikněte na tlačítko nebo platební limit překročen – některých součástí programu, a který můžete napsat kód je rozpoznán reagovat.</span><span class="sxs-lookup"><span data-stu-id="9f778-103">An *event* is an action or occurrence — such as a mouse click or a credit limit exceeded — that is recognized by some program component, and for which you can write code to respond.</span></span> <span data-ttu-id="9f778-104">*Obslužné rutiny události* je kód, který vytváříte reagovat na událost.</span><span class="sxs-lookup"><span data-stu-id="9f778-104">An *event handler* is the code you write to respond to an event.</span></span>  
  
 <span data-ttu-id="9f778-105">Obslužné rutiny události v [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] je `Sub` postupu.</span><span class="sxs-lookup"><span data-stu-id="9f778-105">An event handler in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] is a `Sub` procedure.</span></span> <span data-ttu-id="9f778-106">Však můžete normálně ho nevolají stejný způsobem jako ostatní `Sub` postupy.</span><span class="sxs-lookup"><span data-stu-id="9f778-106">However, you do not normally call it the same way as other `Sub` procedures.</span></span> <span data-ttu-id="9f778-107">Místo toho identifikujete postupu jako obslužná rutina události.</span><span class="sxs-lookup"><span data-stu-id="9f778-107">Instead, you identify the procedure as a handler for the event.</span></span> <span data-ttu-id="9f778-108">To provedete buď pomocí [zpracovává](../../../../visual-basic/language-reference/statements/handles-clause.md) klauzule a [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) proměnnou, nebo se [AddHandler – příkaz](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9f778-108">You can do this either with a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause and a [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) variable, or with an [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="9f778-109">Použití `Handles` klauzule je způsob výchozí deklarace obslužné rutiny události v [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9f778-109">Using a `Handles` clause is the default way to declare an event handler in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span> <span data-ttu-id="9f778-110">Toto je způsob, jakým obslužné rutiny událostí se zapisují návrháři, když budete programu v integrované vývojové prostředí (IDE).</span><span class="sxs-lookup"><span data-stu-id="9f778-110">This is the way the event handlers are written by the designers when you program in the integrated development environment (IDE).</span></span> <span data-ttu-id="9f778-111">`AddHandler` Příkaz je vhodný pro vyvolávání událostí dynamicky za běhu.</span><span class="sxs-lookup"><span data-stu-id="9f778-111">The `AddHandler` statement is suitable for raising events dynamically at run time.</span></span>  
  
 <span data-ttu-id="9f778-112">Když dojde k události, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] automaticky volá proceduru obslužná rutina události.</span><span class="sxs-lookup"><span data-stu-id="9f778-112">When the event occurs, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] automatically calls the event handler procedure.</span></span> <span data-ttu-id="9f778-113">Kód, který má přístup k události může způsobit tak, aby spuštěním [RaiseEvent – příkaz](../../../../visual-basic/language-reference/statements/raiseevent-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9f778-113">Any code that has access to the event can cause it to occur by executing a [RaiseEvent Statement](../../../../visual-basic/language-reference/statements/raiseevent-statement.md).</span></span>  
  
 <span data-ttu-id="9f778-114">Více než jeden obslužné rutiny události můžete přidružit jednu událost.</span><span class="sxs-lookup"><span data-stu-id="9f778-114">You can associate more than one event handler with the same event.</span></span> <span data-ttu-id="9f778-115">V některých případech můžete zrušit přidružení obslužnou rutinu z události.</span><span class="sxs-lookup"><span data-stu-id="9f778-115">In some cases you can dissociate a handler from an event.</span></span> <span data-ttu-id="9f778-116">Další informace najdete v tématu [události](../../../../visual-basic/programming-guide/language-features/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="9f778-116">For more information, see [Events](../../../../visual-basic/programming-guide/language-features/events/index.md).</span></span>  
  
### <a name="to-call-an-event-handler-using-handles-and-withevents"></a><span data-ttu-id="9f778-117">K volání obslužné rutiny události pomocí obslužných rutin a WithEvents</span><span class="sxs-lookup"><span data-stu-id="9f778-117">To call an event handler using Handles and WithEvents</span></span>  
  
1.  <span data-ttu-id="9f778-118">Ujistěte se, že událost je deklarovaný s [Event – příkaz](../../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9f778-118">Make sure the event is declared with an [Event Statement](../../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
2.  <span data-ttu-id="9f778-119">Deklarace proměnné objektu v modulu nebo třída úrovně, pomocí [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="9f778-119">Declare an object variable at module or class level, using the [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) keyword.</span></span> <span data-ttu-id="9f778-120">`As` Klauzuli pro tato proměnná musí být zadána třída, která vyvolá událost.</span><span class="sxs-lookup"><span data-stu-id="9f778-120">The `As` clause for this variable must specify the class that raises the event.</span></span>  
  
3.  <span data-ttu-id="9f778-121">V deklaraci zpracování událostí `Sub` postupu přidat [zpracovává](../../../../visual-basic/language-reference/statements/handles-clause.md) klauzuli, která určuje, `WithEvents` proměnné a z názvu události.</span><span class="sxs-lookup"><span data-stu-id="9f778-121">In the declaration of the event-handling `Sub` procedure, add a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause that specifies the `WithEvents` variable and the event name.</span></span>  
  
4.  <span data-ttu-id="9f778-122">Když dojde k události, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] automaticky zavolá `Sub` postupu.</span><span class="sxs-lookup"><span data-stu-id="9f778-122">When the event occurs, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] automatically calls the `Sub` procedure.</span></span> <span data-ttu-id="9f778-123">Váš kód můžete použít `RaiseEvent` příkaz a ujistěte se, dojde k události.</span><span class="sxs-lookup"><span data-stu-id="9f778-123">Your code can use a `RaiseEvent` statement to make the event occur.</span></span>  
  
     <span data-ttu-id="9f778-124">V následujícím příkladu definuje události a `WithEvents` proměnné, která odkazuje na třídu, která vyvolává událost.</span><span class="sxs-lookup"><span data-stu-id="9f778-124">The following example defines an event and a `WithEvents` variable that refers to the class that raises the event.</span></span> <span data-ttu-id="9f778-125">Zpracování událostí `Sub` postup používá `Handles` klauzule zadat třídu a zpracovává události.</span><span class="sxs-lookup"><span data-stu-id="9f778-125">The event-handling `Sub` procedure uses a `Handles` clause to specify the class and event it handles.</span></span>  
  
     [!code-vb[VbVbcnProcedures#4](./codesnippet/VisualBasic/how-to-call-an-event-handler_1.vb)]  
  
### <a name="to-call-an-event-handler-using-addhandler"></a><span data-ttu-id="9f778-126">K volání obslužné rutiny události pomocí AddHandler</span><span class="sxs-lookup"><span data-stu-id="9f778-126">To call an event handler using AddHandler</span></span>  
  
1.  <span data-ttu-id="9f778-127">Ujistěte se, že událost je deklarovaný s `Event` příkaz.</span><span class="sxs-lookup"><span data-stu-id="9f778-127">Make sure the event is declared with an `Event` statement.</span></span>  
  
2.  <span data-ttu-id="9f778-128">Spuštění [AddHandler – příkaz](../../../../visual-basic/language-reference/statements/addhandler-statement.md) dynamicky připojit zpracování událostí `Sub` postup k události.</span><span class="sxs-lookup"><span data-stu-id="9f778-128">Execute an [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) to dynamically connect the event-handling `Sub` procedure with the event.</span></span>  
  
3.  <span data-ttu-id="9f778-129">Když dojde k události, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] automaticky zavolá `Sub` postupu.</span><span class="sxs-lookup"><span data-stu-id="9f778-129">When the event occurs, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] automatically calls the `Sub` procedure.</span></span> <span data-ttu-id="9f778-130">Váš kód můžete použít `RaiseEvent` příkaz a ujistěte se, dojde k události.</span><span class="sxs-lookup"><span data-stu-id="9f778-130">Your code can use a `RaiseEvent` statement to make the event occur.</span></span>  
  
     <span data-ttu-id="9f778-131">V následujícím příkladu definuje `Sub` postup zpracování <xref:System.Windows.Forms.Form.Closing> událost formuláře.</span><span class="sxs-lookup"><span data-stu-id="9f778-131">The following example defines a `Sub` procedure to handle the <xref:System.Windows.Forms.Form.Closing> event of a form.</span></span> <span data-ttu-id="9f778-132">Poté použije [AddHandler – příkaz](../../../../visual-basic/language-reference/statements/addhandler-statement.md) přidružit `catchClose` postupu jako obslužné rutiny události pro <xref:System.Windows.Forms.Form.Closing>.</span><span class="sxs-lookup"><span data-stu-id="9f778-132">It then uses the [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) to associate the `catchClose` procedure as an event handler for <xref:System.Windows.Forms.Form.Closing>.</span></span>  
  
     [!code-vb[VbVbcnProcedures#5](./codesnippet/VisualBasic/how-to-call-an-event-handler_2.vb)]  
  
     <span data-ttu-id="9f778-133">Obslužné rutiny události z události můžete zrušit přidružení spuštěním [RemoveHandler – příkaz](../../../../visual-basic/language-reference/statements/removehandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9f778-133">You can dissociate an event handler from an event by executing the [RemoveHandler Statement](../../../../visual-basic/language-reference/statements/removehandler-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f778-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="9f778-134">See Also</span></span>  
 [<span data-ttu-id="9f778-135">Postupy</span><span class="sxs-lookup"><span data-stu-id="9f778-135">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="9f778-136">Sub – procedury</span><span class="sxs-lookup"><span data-stu-id="9f778-136">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="9f778-137">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="9f778-137">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="9f778-138">AddressOf – operátor</span><span class="sxs-lookup"><span data-stu-id="9f778-138">AddressOf Operator</span></span>](../../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="9f778-139">Postupy: vytvoření procedury</span><span class="sxs-lookup"><span data-stu-id="9f778-139">How to: Create a Procedure</span></span>](./how-to-create-a-procedure.md)  
 [<span data-ttu-id="9f778-140">Postupy: volání procedury, která nevrátí hodnotu</span><span class="sxs-lookup"><span data-stu-id="9f778-140">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)
