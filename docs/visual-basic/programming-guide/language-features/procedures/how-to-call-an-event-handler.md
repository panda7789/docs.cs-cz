---
title: 'Postupy: Volání obslužné rutiny události v Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- event handlers [Visual Basic], calling
- event handlers
- procedures [Visual Basic], event handlers
- procedures [Visual Basic], calling
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
ms.openlocfilehash: a9e090e83b180686ccb832aa6efb314c7e0fcc9a
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216625"
---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a><span data-ttu-id="8020b-102">Postupy: Volání obslužné rutiny události v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8020b-102">How to: Call an Event Handler in Visual Basic</span></span>

<span data-ttu-id="8020b-103">*Událost* je akce nebo výskyt – například kliknutí myší nebo překročení limitu úvěru, který je rozpoznáván některými součástmi programu a pro které můžete napsat kód, který bude reagovat.</span><span class="sxs-lookup"><span data-stu-id="8020b-103">An *event* is an action or occurrence — such as a mouse click or a credit limit exceeded — that is recognized by some program component, and for which you can write code to respond.</span></span> <span data-ttu-id="8020b-104">*Obslužná rutina události* je kód, který zapisujete pro reakci na událost.</span><span class="sxs-lookup"><span data-stu-id="8020b-104">An *event handler* is the code you write to respond to an event.</span></span>

 <span data-ttu-id="8020b-105">Obslužná rutina události v Visual Basic je `Sub` procedura.</span><span class="sxs-lookup"><span data-stu-id="8020b-105">An event handler in Visual Basic is a `Sub` procedure.</span></span> <span data-ttu-id="8020b-106">Nebudete je však obvykle volat stejným způsobem jako jiné `Sub` postupy.</span><span class="sxs-lookup"><span data-stu-id="8020b-106">However, you do not normally call it the same way as other `Sub` procedures.</span></span> <span data-ttu-id="8020b-107">Místo toho identifikujete proceduru jako obslužnou rutinu pro událost.</span><span class="sxs-lookup"><span data-stu-id="8020b-107">Instead, you identify the procedure as a handler for the event.</span></span> <span data-ttu-id="8020b-108">To lze provést buď s klauzulí [Handles](../../../language-reference/statements/handles-clause.md) , a s proměnnou [WithEvents](../../../language-reference/modifiers/withevents.md) nebo s [příkazem AddHandler](../../../language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8020b-108">You can do this either with a [Handles](../../../language-reference/statements/handles-clause.md) clause and a [WithEvents](../../../language-reference/modifiers/withevents.md) variable, or with an [AddHandler Statement](../../../language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="8020b-109">`Handles` Použití klauzule je výchozí způsob, jak deklarovat obslužnou rutinu události v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8020b-109">Using a `Handles` clause is the default way to declare an event handler in Visual Basic.</span></span> <span data-ttu-id="8020b-110">Toto je způsob, jakým jsou obslužné rutiny události zapisovány návrháři při programování v integrovaném vývojovém prostředí (IDE).</span><span class="sxs-lookup"><span data-stu-id="8020b-110">This is the way the event handlers are written by the designers when you program in the integrated development environment (IDE).</span></span> <span data-ttu-id="8020b-111">`AddHandler` Příkaz je vhodný pro dynamické vyvolání událostí v době běhu.</span><span class="sxs-lookup"><span data-stu-id="8020b-111">The `AddHandler` statement is suitable for raising events dynamically at run time.</span></span>

 <span data-ttu-id="8020b-112">Když dojde k události, Visual Basic automaticky volá proceduru obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="8020b-112">When the event occurs, Visual Basic automatically calls the event handler procedure.</span></span> <span data-ttu-id="8020b-113">Jakýkoli kód, který má přístup k události, může způsobit, že dojde k provedení [příkazu RaiseEvent](../../../language-reference/statements/raiseevent-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8020b-113">Any code that has access to the event can cause it to occur by executing a [RaiseEvent Statement](../../../language-reference/statements/raiseevent-statement.md).</span></span>

 <span data-ttu-id="8020b-114">Ke stejné události můžete přidružit více než jednu obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="8020b-114">You can associate more than one event handler with the same event.</span></span> <span data-ttu-id="8020b-115">V některých případech můžete zrušit přidružení obslužné rutiny od události.</span><span class="sxs-lookup"><span data-stu-id="8020b-115">In some cases you can dissociate a handler from an event.</span></span> <span data-ttu-id="8020b-116">Další informace najdete v tématu [události](../events/index.md).</span><span class="sxs-lookup"><span data-stu-id="8020b-116">For more information, see [Events](../events/index.md).</span></span>

### <a name="to-call-an-event-handler-using-handles-and-withevents"></a><span data-ttu-id="8020b-117">Volání obslužné rutiny události pomocí obslužných rutin a WithEvents</span><span class="sxs-lookup"><span data-stu-id="8020b-117">To call an event handler using Handles and WithEvents</span></span>

1. <span data-ttu-id="8020b-118">Ujistěte se, že je událost deklarovaná pomocí [příkazu Event](../../../language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8020b-118">Make sure the event is declared with an [Event Statement](../../../language-reference/statements/event-statement.md).</span></span>

2. <span data-ttu-id="8020b-119">Deklarujte proměnnou objektu na úrovni modulu nebo třídy pomocí klíčového slova [WithEvents](../../../language-reference/modifiers/withevents.md) .</span><span class="sxs-lookup"><span data-stu-id="8020b-119">Declare an object variable at module or class level, using the [WithEvents](../../../language-reference/modifiers/withevents.md) keyword.</span></span> <span data-ttu-id="8020b-120">`As` Klauzule pro tuto proměnnou musí určovat třídu, která vyvolá událost.</span><span class="sxs-lookup"><span data-stu-id="8020b-120">The `As` clause for this variable must specify the class that raises the event.</span></span>

3. <span data-ttu-id="8020b-121">V deklaraci procedury zpracování `Sub` událostí přidejte `WithEvents` klauzuli [Handles](../../../language-reference/statements/handles-clause.md) , která určuje proměnnou a název události.</span><span class="sxs-lookup"><span data-stu-id="8020b-121">In the declaration of the event-handling `Sub` procedure, add a [Handles](../../../language-reference/statements/handles-clause.md) clause that specifies the `WithEvents` variable and the event name.</span></span>

4. <span data-ttu-id="8020b-122">Když dojde k události, Visual Basic automaticky volá `Sub` proceduru.</span><span class="sxs-lookup"><span data-stu-id="8020b-122">When the event occurs, Visual Basic automatically calls the `Sub` procedure.</span></span> <span data-ttu-id="8020b-123">Váš kód může použít `RaiseEvent` příkaz k provedení události.</span><span class="sxs-lookup"><span data-stu-id="8020b-123">Your code can use a `RaiseEvent` statement to make the event occur.</span></span>

     <span data-ttu-id="8020b-124">Následující příklad definuje událost a `WithEvents` proměnnou, která odkazuje na třídu, která vyvolá událost.</span><span class="sxs-lookup"><span data-stu-id="8020b-124">The following example defines an event and a `WithEvents` variable that refers to the class that raises the event.</span></span> <span data-ttu-id="8020b-125">Procedura zpracování `Sub` událostí `Handles` používá klauzuli k určení třídy a události, kterou zpracovává.</span><span class="sxs-lookup"><span data-stu-id="8020b-125">The event-handling `Sub` procedure uses a `Handles` clause to specify the class and event it handles.</span></span>

     [!code-vb[VbVbcnProcedures#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#4)]

### <a name="to-call-an-event-handler-using-addhandler"></a><span data-ttu-id="8020b-126">Volání obslužné rutiny události pomocí AddHandler</span><span class="sxs-lookup"><span data-stu-id="8020b-126">To call an event handler using AddHandler</span></span>

1. <span data-ttu-id="8020b-127">Ujistěte se, že je událost deklarovaná `Event` pomocí příkazu.</span><span class="sxs-lookup"><span data-stu-id="8020b-127">Make sure the event is declared with an `Event` statement.</span></span>

2. <span data-ttu-id="8020b-128">Spusťte [příkaz AddHandler](../../../language-reference/statements/addhandler-statement.md) k dynamickému propojení procedury zpracování `Sub` události s událostí.</span><span class="sxs-lookup"><span data-stu-id="8020b-128">Execute an [AddHandler Statement](../../../language-reference/statements/addhandler-statement.md) to dynamically connect the event-handling `Sub` procedure with the event.</span></span>

3. <span data-ttu-id="8020b-129">Když dojde k události, Visual Basic automaticky volá `Sub` proceduru.</span><span class="sxs-lookup"><span data-stu-id="8020b-129">When the event occurs, Visual Basic automatically calls the `Sub` procedure.</span></span> <span data-ttu-id="8020b-130">Váš kód může použít `RaiseEvent` příkaz k provedení události.</span><span class="sxs-lookup"><span data-stu-id="8020b-130">Your code can use a `RaiseEvent` statement to make the event occur.</span></span>

     <span data-ttu-id="8020b-131">Následující příklad definuje `Sub` proceduru pro <xref:System.Windows.Forms.Form.Closing> zpracování události formuláře.</span><span class="sxs-lookup"><span data-stu-id="8020b-131">The following example defines a `Sub` procedure to handle the <xref:System.Windows.Forms.Form.Closing> event of a form.</span></span> <span data-ttu-id="8020b-132">Pak použije [příkaz AddHandler](../../../language-reference/statements/addhandler-statement.md) k přidružení `catchClose` procedury jako obslužné rutiny události pro <xref:System.Windows.Forms.Form.Closing>.</span><span class="sxs-lookup"><span data-stu-id="8020b-132">It then uses the [AddHandler Statement](../../../language-reference/statements/addhandler-statement.md) to associate the `catchClose` procedure as an event handler for <xref:System.Windows.Forms.Form.Closing>.</span></span>

     [!code-vb[VbVbcnProcedures#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#5)]

     <span data-ttu-id="8020b-133">Můžete zrušit přidružení obslužné rutiny události z události spuštěním [příkazu removeHandler](../../../language-reference/statements/removehandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8020b-133">You can dissociate an event handler from an event by executing the [RemoveHandler Statement](../../../language-reference/statements/removehandler-statement.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8020b-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8020b-134">See also</span></span>

- [<span data-ttu-id="8020b-135">Procedury</span><span class="sxs-lookup"><span data-stu-id="8020b-135">Procedures</span></span>](index.md)
- [<span data-ttu-id="8020b-136">Procedury Sub</span><span class="sxs-lookup"><span data-stu-id="8020b-136">Sub Procedures</span></span>](sub-procedures.md)
- [<span data-ttu-id="8020b-137">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="8020b-137">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="8020b-138">Operátor AddressOf</span><span class="sxs-lookup"><span data-stu-id="8020b-138">AddressOf Operator</span></span>](../../../language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="8020b-139">Postupy: Vytvořit proceduru</span><span class="sxs-lookup"><span data-stu-id="8020b-139">How to: Create a Procedure</span></span>](how-to-create-a-procedure.md)
- [<span data-ttu-id="8020b-140">Postupy: Volání procedury, která nevrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="8020b-140">How to: Call a Procedure that Does Not Return a Value</span></span>](how-to-call-a-procedure-that-does-not-return-a-value.md)
