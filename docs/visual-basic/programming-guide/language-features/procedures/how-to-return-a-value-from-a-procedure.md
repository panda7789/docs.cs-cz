---
title: 'Postupy: Vrácení hodnoty z procedury'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
ms.openlocfilehash: 917e52b711645fbf94a132216a3fa90b0dfc15b3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414321"
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a><span data-ttu-id="ef272-102">Postupy: Vrácení hodnoty z procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ef272-102">How to: Return a Value from a Procedure (Visual Basic)</span></span>
<span data-ttu-id="ef272-103">`Function`Procedura vrátí hodnotu volajícímu kódu buď spuštěním `Return` příkazu, nebo zjištěním `Exit Function` `End Function` příkazu or.</span><span class="sxs-lookup"><span data-stu-id="ef272-103">A `Function` procedure returns a value to the calling code either by executing a `Return` statement or by encountering an `Exit Function` or `End Function` statement.</span></span>  
  
### <a name="to-return-a-value-using-the-return-statement"></a><span data-ttu-id="ef272-104">Vrácení hodnoty pomocí příkazu return</span><span class="sxs-lookup"><span data-stu-id="ef272-104">To return a value using the Return statement</span></span>  
  
1. <span data-ttu-id="ef272-105">Vložte `Return` příkaz do místa, kde je úkol procedury dokončen.</span><span class="sxs-lookup"><span data-stu-id="ef272-105">Put a `Return` statement at the point where the procedure's task is completed.</span></span>  
  
2. <span data-ttu-id="ef272-106">Sledujte `Return` klíčové slovo s výrazem, který vrací hodnotu, kterou chcete vrátit na volající kód.</span><span class="sxs-lookup"><span data-stu-id="ef272-106">Follow the `Return` keyword with an expression that yields the value you want to return to the calling code.</span></span>  
  
3. <span data-ttu-id="ef272-107">Stejný postup může mít více než jeden `Return` příkaz.</span><span class="sxs-lookup"><span data-stu-id="ef272-107">You can have more than one `Return` statement in the same procedure.</span></span>  
  
     <span data-ttu-id="ef272-108">Následující `Function` postup vypočítá nejdelší stranu (nebo přepony) pravého trojúhelníku a vrátí ji do volajícího kódu.</span><span class="sxs-lookup"><span data-stu-id="ef272-108">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, and returns it to the calling code.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     <span data-ttu-id="ef272-109">Následující příklad ukazuje typické volání metody `hypotenuse` , které ukládá vrácenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ef272-109">The following example shows a typical call to `hypotenuse`, which stores the returned value.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a><span data-ttu-id="ef272-110">Vrácení hodnoty pomocí funkce Exit nebo funkce end</span><span class="sxs-lookup"><span data-stu-id="ef272-110">To return a value using Exit Function or End Function</span></span>  
  
1. <span data-ttu-id="ef272-111">V alespoň jednom místě v `Function` proceduře přiřaďte hodnotu k názvu procedury.</span><span class="sxs-lookup"><span data-stu-id="ef272-111">In at least one place in the `Function` procedure, assign a value to the procedure's name.</span></span>  
  
2. <span data-ttu-id="ef272-112">Když spustíte `Exit Function` `End Function` příkaz nebo, Visual Basic vrátí hodnotu, která byla naposledy přiřazena k názvu procedury.</span><span class="sxs-lookup"><span data-stu-id="ef272-112">When you execute an `Exit Function` or `End Function` statement, Visual Basic returns the value most recently assigned to the procedure's name.</span></span>  
  
3. <span data-ttu-id="ef272-113">Stejným postupem můžete mít více než jeden `Exit Function` příkaz a můžete kombinovat `Return` a `Exit Function` příkazy stejným postupem.</span><span class="sxs-lookup"><span data-stu-id="ef272-113">You can have more than one `Exit Function` statement in the same procedure, and you can mix `Return` and `Exit Function` statements in the same procedure.</span></span>  
  
4. <span data-ttu-id="ef272-114">Procedura může obsahovat jenom jeden `End Function` příkaz `Function` .</span><span class="sxs-lookup"><span data-stu-id="ef272-114">You can have only one `End Function` statement in a `Function` procedure.</span></span>  
  
     <span data-ttu-id="ef272-115">Další informace a příklad naleznete v části "návratová hodnota" v [příkazu Function](../../../language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ef272-115">For more information and an example, see "Return Value" in [Function Statement](../../../language-reference/statements/function-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef272-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="ef272-116">See also</span></span>

- [<span data-ttu-id="ef272-117">Procedury</span><span class="sxs-lookup"><span data-stu-id="ef272-117">Procedures</span></span>](./index.md)
- [<span data-ttu-id="ef272-118">Procedury Sub</span><span class="sxs-lookup"><span data-stu-id="ef272-118">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="ef272-119">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ef272-119">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="ef272-120">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="ef272-120">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="ef272-121">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="ef272-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="ef272-122">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="ef272-122">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="ef272-123">Return – příkaz</span><span class="sxs-lookup"><span data-stu-id="ef272-123">Return Statement</span></span>](../../../language-reference/statements/return-statement.md)
- [<span data-ttu-id="ef272-124">Postupy: Vytvoření procedury, která vrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="ef272-124">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="ef272-125">Postupy. Volání procedury, která vrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="ef272-125">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
