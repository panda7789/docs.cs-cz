---
title: 'Postupy: Vytvoření procedury, která vrátí hodnotu.'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: 2655aba6ce37be831d8dd4202ffd484cfd3fd5ef
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388346"
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="9723d-102">Postupy: Vytvoření procedury, která vrátí hodnotu (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="9723d-102">How to: Create a Procedure that Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="9723d-103">Použijte `Function` proceduru, která vrátí hodnotu volajícímu kódu.</span><span class="sxs-lookup"><span data-stu-id="9723d-103">You use a `Function` procedure to return a value to the calling code.</span></span>  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="9723d-104">Vytvoření procedury, která vrátí hodnotu</span><span class="sxs-lookup"><span data-stu-id="9723d-104">To create a procedure that returns a value</span></span>  
  
1. <span data-ttu-id="9723d-105">Mimo jakýkoli jiný postup použijte `Function` příkaz následovaný `End Function` příkazem.</span><span class="sxs-lookup"><span data-stu-id="9723d-105">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>  
  
2. <span data-ttu-id="9723d-106">V `Function` příkazu použijte `Function` klíčové slovo s názvem procedury a pak seznam parametrů v závorkách.</span><span class="sxs-lookup"><span data-stu-id="9723d-106">In the `Function` statement, follow the `Function` keyword with the name of the procedure, and then the parameter list in parentheses.</span></span>  
  
3. <span data-ttu-id="9723d-107">Pomocí závorek s `As` klauzulí určete datový typ vrácené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9723d-107">Follow the parentheses with an `As` clause to specify the data type of the returned value.</span></span>  
  
4. <span data-ttu-id="9723d-108">Umístěte příkazy kódu procedury mezi `Function` `End Function` příkazy a.</span><span class="sxs-lookup"><span data-stu-id="9723d-108">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>  
  
5. <span data-ttu-id="9723d-109">Pomocí `Return` příkazu vraťte hodnotu volajícímu kódu.</span><span class="sxs-lookup"><span data-stu-id="9723d-109">Use a `Return` statement to return the value to the calling code.</span></span>  
  
     <span data-ttu-id="9723d-110">Následující `Function` postup vypočítá nejdelší stranu (neboli přepony) pravého trojúhelníku s ohledem na hodnoty ostatních dvou stran.</span><span class="sxs-lookup"><span data-stu-id="9723d-110">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     <span data-ttu-id="9723d-111">Následující příklad ukazuje typické volání metody `hypotenuse` .</span><span class="sxs-lookup"><span data-stu-id="9723d-111">The following example shows a typical call to `hypotenuse`.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="9723d-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="9723d-112">See also</span></span>

- [<span data-ttu-id="9723d-113">Procedury</span><span class="sxs-lookup"><span data-stu-id="9723d-113">Procedures</span></span>](./index.md)
- [<span data-ttu-id="9723d-114">Procedury Sub</span><span class="sxs-lookup"><span data-stu-id="9723d-114">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="9723d-115">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="9723d-115">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="9723d-116">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="9723d-116">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="9723d-117">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="9723d-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="9723d-118">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="9723d-118">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="9723d-119">Postupy: Vrácení hodnoty z procedury</span><span class="sxs-lookup"><span data-stu-id="9723d-119">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="9723d-120">Postupy. Volání procedury, která vrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="9723d-120">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
