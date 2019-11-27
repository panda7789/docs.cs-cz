---
title: 'Postupy: Vrácení hodnoty z procedury'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
ms.openlocfilehash: 1371e4ed0ff28f9caf56eabf2a1bb9290edbe75c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346029"
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a><span data-ttu-id="a01e0-102">Postupy: Vrácení hodnoty z procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a01e0-102">How to: Return a Value from a Procedure (Visual Basic)</span></span>
<span data-ttu-id="a01e0-103">Procedura `Function` vrátí hodnotu volajícímu kódu buď spuštěním příkazu `Return` nebo navoláním příkazu `Exit Function` nebo `End Function`.</span><span class="sxs-lookup"><span data-stu-id="a01e0-103">A `Function` procedure returns a value to the calling code either by executing a `Return` statement or by encountering an `Exit Function` or `End Function` statement.</span></span>  
  
### <a name="to-return-a-value-using-the-return-statement"></a><span data-ttu-id="a01e0-104">Vrácení hodnoty pomocí příkazu return</span><span class="sxs-lookup"><span data-stu-id="a01e0-104">To return a value using the Return statement</span></span>  
  
1. <span data-ttu-id="a01e0-105">Vložte příkaz `Return` v místě, kde je úkol procedury dokončen.</span><span class="sxs-lookup"><span data-stu-id="a01e0-105">Put a `Return` statement at the point where the procedure's task is completed.</span></span>  
  
2. <span data-ttu-id="a01e0-106">Použijte klíčové slovo `Return` s výrazem, který vrací hodnotu, kterou chcete vrátit na volající kód.</span><span class="sxs-lookup"><span data-stu-id="a01e0-106">Follow the `Return` keyword with an expression that yields the value you want to return to the calling code.</span></span>  
  
3. <span data-ttu-id="a01e0-107">Stejný postup může mít více než jeden `Return` příkaz.</span><span class="sxs-lookup"><span data-stu-id="a01e0-107">You can have more than one `Return` statement in the same procedure.</span></span>  
  
     <span data-ttu-id="a01e0-108">Následující `Function` postup vypočítá nejdelší stranu (nebo přepony) pravého trojúhelníku a vrátí ji do volajícího kódu.</span><span class="sxs-lookup"><span data-stu-id="a01e0-108">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, and returns it to the calling code.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     <span data-ttu-id="a01e0-109">Následující příklad ukazuje typické volání `hypotenuse`, které ukládá vrácenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a01e0-109">The following example shows a typical call to `hypotenuse`, which stores the returned value.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a><span data-ttu-id="a01e0-110">Vrácení hodnoty pomocí funkce Exit nebo funkce end</span><span class="sxs-lookup"><span data-stu-id="a01e0-110">To return a value using Exit Function or End Function</span></span>  
  
1. <span data-ttu-id="a01e0-111">Alespoň na jednom místě v `Function` proceduře přiřaďte hodnotu k názvu procedury.</span><span class="sxs-lookup"><span data-stu-id="a01e0-111">In at least one place in the `Function` procedure, assign a value to the procedure's name.</span></span>  
  
2. <span data-ttu-id="a01e0-112">Když spustíte příkaz `Exit Function` nebo `End Function`, Visual Basic vrátí hodnotu, která byla naposledy přiřazena k názvu procedury.</span><span class="sxs-lookup"><span data-stu-id="a01e0-112">When you execute an `Exit Function` or `End Function` statement, Visual Basic returns the value most recently assigned to the procedure's name.</span></span>  
  
3. <span data-ttu-id="a01e0-113">Stejný postup může mít více než jeden `Exit Function` příkaz a můžete kombinovat `Return` a `Exit Function` příkazy stejným postupem.</span><span class="sxs-lookup"><span data-stu-id="a01e0-113">You can have more than one `Exit Function` statement in the same procedure, and you can mix `Return` and `Exit Function` statements in the same procedure.</span></span>  
  
4. <span data-ttu-id="a01e0-114">V postupu `Function` může být pouze jeden příkaz `End Function`.</span><span class="sxs-lookup"><span data-stu-id="a01e0-114">You can have only one `End Function` statement in a `Function` procedure.</span></span>  
  
     <span data-ttu-id="a01e0-115">Další informace a příklad naleznete v části "návratová hodnota" v [příkazu Function](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a01e0-115">For more information and an example, see "Return Value" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a01e0-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a01e0-116">See also</span></span>

- [<span data-ttu-id="a01e0-117">Procedury</span><span class="sxs-lookup"><span data-stu-id="a01e0-117">Procedures</span></span>](./index.md)
- [<span data-ttu-id="a01e0-118">Procedury Sub</span><span class="sxs-lookup"><span data-stu-id="a01e0-118">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="a01e0-119">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a01e0-119">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="a01e0-120">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="a01e0-120">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="a01e0-121">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="a01e0-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="a01e0-122">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="a01e0-122">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="a01e0-123">Příkaz Return</span><span class="sxs-lookup"><span data-stu-id="a01e0-123">Return Statement</span></span>](../../../../visual-basic/language-reference/statements/return-statement.md)
- [<span data-ttu-id="a01e0-124">Postupy: Vytvoření procedury, která vrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="a01e0-124">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="a01e0-125">Postupy. Volání procedury, která vrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="a01e0-125">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
