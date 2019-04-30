---
title: 'Postupy: Vytvořit proceduru, která vrací hodnotu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: 115c1df4bd49d5848d72c4cbd0242a49a12740c7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61863724"
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="87871-102">Postupy: Vytvořit proceduru, která vrací hodnotu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87871-102">How to: Create a Procedure that Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="87871-103">Můžete použít `Function` postup, který vrací hodnotu volajícímu kódu.</span><span class="sxs-lookup"><span data-stu-id="87871-103">You use a `Function` procedure to return a value to the calling code.</span></span>  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="87871-104">Chcete-li vytvořit proceduru, která vrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="87871-104">To create a procedure that returns a value</span></span>  
  
1. <span data-ttu-id="87871-105">Mimo všechny procedury, použijte `Function` příkazu, za nímž následuje `End Function` příkazu.</span><span class="sxs-lookup"><span data-stu-id="87871-105">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>  
  
2. <span data-ttu-id="87871-106">V `Function` prohlášení, postupujte `Function` – klíčové slovo s názvem podle postupu a seznam parametrů v závorkách.</span><span class="sxs-lookup"><span data-stu-id="87871-106">In the `Function` statement, follow the `Function` keyword with the name of the procedure, and then the parameter list in parentheses.</span></span>  
  
3. <span data-ttu-id="87871-107">Postupujte podle závorek s `As` klauzule zadejte datový typ vrácené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="87871-107">Follow the parentheses with an `As` clause to specify the data type of the returned value.</span></span>  
  
4. <span data-ttu-id="87871-108">Umístit příkazy kódu podle postupu mezi `Function` a `End Function` příkazy.</span><span class="sxs-lookup"><span data-stu-id="87871-108">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>  
  
5. <span data-ttu-id="87871-109">Použití `Return` příkazu vrátí hodnotu volajícímu kódu.</span><span class="sxs-lookup"><span data-stu-id="87871-109">Use a `Return` statement to return the value to the calling code.</span></span>  
  
     <span data-ttu-id="87871-110">Následující `Function` postup vypočítá nejdelší strana nebo přepony pravoúhlého trojúhelníku, pro obě strany zadané hodnoty.</span><span class="sxs-lookup"><span data-stu-id="87871-110">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     <span data-ttu-id="87871-111">Následující příklad ukazuje typické volání `hypotenuse`.</span><span class="sxs-lookup"><span data-stu-id="87871-111">The following example shows a typical call to `hypotenuse`.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="87871-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="87871-112">See also</span></span>

- [<span data-ttu-id="87871-113">Procedury</span><span class="sxs-lookup"><span data-stu-id="87871-113">Procedures</span></span>](./index.md)
- [<span data-ttu-id="87871-114">Procedury Sub</span><span class="sxs-lookup"><span data-stu-id="87871-114">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="87871-115">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="87871-115">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="87871-116">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="87871-116">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="87871-117">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="87871-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="87871-118">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="87871-118">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="87871-119">Postupy: Vrácení hodnoty z procedury</span><span class="sxs-lookup"><span data-stu-id="87871-119">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="87871-120">Postupy: Volání procedury, která vrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="87871-120">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
