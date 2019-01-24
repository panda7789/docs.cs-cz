---
title: 'Postupy: Vytvořit proceduru, která vrací hodnotu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: 18becfe05da27e538c5c294b26e0bb7aa19cad2b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506417"
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="eaeea-102">Postupy: Vytvořit proceduru, která vrací hodnotu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eaeea-102">How to: Create a Procedure that Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="eaeea-103">Můžete použít `Function` postup, který vrací hodnotu volajícímu kódu.</span><span class="sxs-lookup"><span data-stu-id="eaeea-103">You use a `Function` procedure to return a value to the calling code.</span></span>  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="eaeea-104">Chcete-li vytvořit proceduru, která vrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="eaeea-104">To create a procedure that returns a value</span></span>  
  
1.  <span data-ttu-id="eaeea-105">Mimo všechny procedury, použijte `Function` příkazu, za nímž následuje `End Function` příkazu.</span><span class="sxs-lookup"><span data-stu-id="eaeea-105">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>  
  
2.  <span data-ttu-id="eaeea-106">V `Function` prohlášení, postupujte `Function` – klíčové slovo s názvem podle postupu a seznam parametrů v závorkách.</span><span class="sxs-lookup"><span data-stu-id="eaeea-106">In the `Function` statement, follow the `Function` keyword with the name of the procedure, and then the parameter list in parentheses.</span></span>  
  
3.  <span data-ttu-id="eaeea-107">Postupujte podle závorek s `As` klauzule zadejte datový typ vrácené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="eaeea-107">Follow the parentheses with an `As` clause to specify the data type of the returned value.</span></span>  
  
4.  <span data-ttu-id="eaeea-108">Umístit příkazy kódu podle postupu mezi `Function` a `End Function` příkazy.</span><span class="sxs-lookup"><span data-stu-id="eaeea-108">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>  
  
5.  <span data-ttu-id="eaeea-109">Použití `Return` příkazu vrátí hodnotu volajícímu kódu.</span><span class="sxs-lookup"><span data-stu-id="eaeea-109">Use a `Return` statement to return the value to the calling code.</span></span>  
  
     <span data-ttu-id="eaeea-110">Následující `Function` postup vypočítá nejdelší strana nebo přepony pravoúhlého trojúhelníku, pro obě strany zadané hodnoty.</span><span class="sxs-lookup"><span data-stu-id="eaeea-110">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_1.vb)]  
  
     <span data-ttu-id="eaeea-111">Následující příklad ukazuje typické volání `hypotenuse`.</span><span class="sxs-lookup"><span data-stu-id="eaeea-111">The following example shows a typical call to `hypotenuse`.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="eaeea-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eaeea-112">See also</span></span>
- [<span data-ttu-id="eaeea-113">Procedury</span><span class="sxs-lookup"><span data-stu-id="eaeea-113">Procedures</span></span>](./index.md)
- [<span data-ttu-id="eaeea-114">Procedury Sub</span><span class="sxs-lookup"><span data-stu-id="eaeea-114">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="eaeea-115">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="eaeea-115">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="eaeea-116">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="eaeea-116">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="eaeea-117">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="eaeea-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="eaeea-118">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="eaeea-118">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="eaeea-119">Postupy: Vrácení hodnoty z procedury</span><span class="sxs-lookup"><span data-stu-id="eaeea-119">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="eaeea-120">Postupy: Volání procedury, která vrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="eaeea-120">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
