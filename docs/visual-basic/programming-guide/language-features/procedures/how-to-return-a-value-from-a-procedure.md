---
title: 'Postupy: Vrácení hodnoty z procedury (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
ms.openlocfilehash: 45f175de647887a406f8ae87dae492a5fe58cca9
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976730"
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a><span data-ttu-id="078d7-102">Postupy: Vrácení hodnoty z procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="078d7-102">How to: Return a Value from a Procedure (Visual Basic)</span></span>
<span data-ttu-id="078d7-103">A `Function` postup vrací hodnotu volajícímu kódu, buď pomocí provádí `Return` příkaz nebo zjištění `Exit Function` nebo `End Function` příkazu.</span><span class="sxs-lookup"><span data-stu-id="078d7-103">A `Function` procedure returns a value to the calling code either by executing a `Return` statement or by encountering an `Exit Function` or `End Function` statement.</span></span>  
  
### <a name="to-return-a-value-using-the-return-statement"></a><span data-ttu-id="078d7-104">Pro navrácení hodnoty návratový příkaz using</span><span class="sxs-lookup"><span data-stu-id="078d7-104">To return a value using the Return statement</span></span>  
  
1.  <span data-ttu-id="078d7-105">Vložit `Return` příkaz v místě, kde se dokončí úkol podle postupu.</span><span class="sxs-lookup"><span data-stu-id="078d7-105">Put a `Return` statement at the point where the procedure's task is completed.</span></span>  
  
2.  <span data-ttu-id="078d7-106">Postupujte podle `Return` – klíčové slovo výrazem, který vrací hodnotu, kterou chcete vrátit na volajícím kódu.</span><span class="sxs-lookup"><span data-stu-id="078d7-106">Follow the `Return` keyword with an expression that yields the value you want to return to the calling code.</span></span>  
  
3.  <span data-ttu-id="078d7-107">Můžete mít více než jeden `Return` příkaz ve stejné proceduře.</span><span class="sxs-lookup"><span data-stu-id="078d7-107">You can have more than one `Return` statement in the same procedure.</span></span>  
  
     <span data-ttu-id="078d7-108">Následující `Function` postup vypočítá nejdelší strana nebo přepony pravoúhlého trojúhelníku a vrátí volajícímu kódu.</span><span class="sxs-lookup"><span data-stu-id="078d7-108">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, and returns it to the calling code.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     <span data-ttu-id="078d7-109">Následující příklad ukazuje typické volání `hypotenuse`, která ukládá vrácené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="078d7-109">The following example shows a typical call to `hypotenuse`, which stores the returned value.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a><span data-ttu-id="078d7-110">Vrátit hodnotu pomocí Exit Function nebo End Function</span><span class="sxs-lookup"><span data-stu-id="078d7-110">To return a value using Exit Function or End Function</span></span>  
  
1.  <span data-ttu-id="078d7-111">V nejméně jednom místě `Function` postupu přiřadit hodnotu pro název procedury.</span><span class="sxs-lookup"><span data-stu-id="078d7-111">In at least one place in the `Function` procedure, assign a value to the procedure's name.</span></span>  
  
2.  <span data-ttu-id="078d7-112">Při spuštění `Exit Function` nebo `End Function` příkazu jazyka Visual Basic vrátí hodnotu naposledy přiřazeno název procedury.</span><span class="sxs-lookup"><span data-stu-id="078d7-112">When you execute an `Exit Function` or `End Function` statement, Visual Basic returns the value most recently assigned to the procedure's name.</span></span>  
  
3.  <span data-ttu-id="078d7-113">Můžete mít více než jeden `Exit Function` příkaz v stejným způsobem a můžete kombinovat `Return` a `Exit Function` příkazy ve stejné proceduře.</span><span class="sxs-lookup"><span data-stu-id="078d7-113">You can have more than one `Exit Function` statement in the same procedure, and you can mix `Return` and `Exit Function` statements in the same procedure.</span></span>  
  
4.  <span data-ttu-id="078d7-114">Může mít pouze jeden `End Function` výroky `Function` postup.</span><span class="sxs-lookup"><span data-stu-id="078d7-114">You can have only one `End Function` statement in a `Function` procedure.</span></span>  
  
     <span data-ttu-id="078d7-115">Další informace a příklad naleznete v části "Vrácení hodnoty" v [Function – příkaz](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="078d7-115">For more information and an example, see "Return Value" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="078d7-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="078d7-116">See also</span></span>
- [<span data-ttu-id="078d7-117">Procedury</span><span class="sxs-lookup"><span data-stu-id="078d7-117">Procedures</span></span>](./index.md)
- [<span data-ttu-id="078d7-118">Procedury Sub</span><span class="sxs-lookup"><span data-stu-id="078d7-118">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="078d7-119">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="078d7-119">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="078d7-120">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="078d7-120">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="078d7-121">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="078d7-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="078d7-122">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="078d7-122">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="078d7-123">Příkaz Return</span><span class="sxs-lookup"><span data-stu-id="078d7-123">Return Statement</span></span>](../../../../visual-basic/language-reference/statements/return-statement.md)
- [<span data-ttu-id="078d7-124">Postupy: Vytvořit proceduru, která vrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="078d7-124">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="078d7-125">Postupy: Volání procedury, která vrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="078d7-125">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
