---
title: 'Postupy: Vytvoření procedury, která vrátí hodnotu (Visual Basic).'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: 472f55173a4897a23a82812a2b24bf1646c1a6ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648434"
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="3f471-102">Postupy: Vytvoření procedury, která vrátí hodnotu (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="3f471-102">How to: Create a Procedure that Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="3f471-103">Můžete použít `Function` postup vrátit hodnotu volání kódu.</span><span class="sxs-lookup"><span data-stu-id="3f471-103">You use a `Function` procedure to return a value to the calling code.</span></span>  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="3f471-104">K vytvoření procedury, která vrátí hodnotu</span><span class="sxs-lookup"><span data-stu-id="3f471-104">To create a procedure that returns a value</span></span>  
  
1.  <span data-ttu-id="3f471-105">Mimo jiné postup použijte `Function` prohlášení, za nímž následuje `End Function` příkaz.</span><span class="sxs-lookup"><span data-stu-id="3f471-105">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>  
  
2.  <span data-ttu-id="3f471-106">V `Function` prohlášení, postupujte podle `Function` – klíčové slovo s názvem postupu a seznam parametrů v závorkách.</span><span class="sxs-lookup"><span data-stu-id="3f471-106">In the `Function` statement, follow the `Function` keyword with the name of the procedure, and then the parameter list in parentheses.</span></span>  
  
3.  <span data-ttu-id="3f471-107">Postupujte podle závorkách s `As` klauzule zadat datový typ vrácené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="3f471-107">Follow the parentheses with an `As` clause to specify the data type of the returned value.</span></span>  
  
4.  <span data-ttu-id="3f471-108">Umístit postup kód příkazy mezi `Function` a `End Function` příkazy.</span><span class="sxs-lookup"><span data-stu-id="3f471-108">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>  
  
5.  <span data-ttu-id="3f471-109">Použití `Return` příkaz k vrácení hodnoty volání kódu.</span><span class="sxs-lookup"><span data-stu-id="3f471-109">Use a `Return` statement to return the value to the calling code.</span></span>  
  
     <span data-ttu-id="3f471-110">Následující `Function` postup vypočítá nejdelší straně nebo přepony trojúhelníku vpravo, pro zbývající dvě strany zadané hodnoty.</span><span class="sxs-lookup"><span data-stu-id="3f471-110">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_1.vb)]  
  
     <span data-ttu-id="3f471-111">Následující příklad ukazuje typické volání `hypotenuse`.</span><span class="sxs-lookup"><span data-stu-id="3f471-111">The following example shows a typical call to `hypotenuse`.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="3f471-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="3f471-112">See Also</span></span>  
 [<span data-ttu-id="3f471-113">Procedury</span><span class="sxs-lookup"><span data-stu-id="3f471-113">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="3f471-114">Procedury Sub</span><span class="sxs-lookup"><span data-stu-id="3f471-114">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="3f471-115">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="3f471-115">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="3f471-116">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="3f471-116">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="3f471-117">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="3f471-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="3f471-118">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="3f471-118">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="3f471-119">Postupy: Vrácení hodnoty z procedury</span><span class="sxs-lookup"><span data-stu-id="3f471-119">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)  
 [<span data-ttu-id="3f471-120">Postupy. Volání procedury, která vrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="3f471-120">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
